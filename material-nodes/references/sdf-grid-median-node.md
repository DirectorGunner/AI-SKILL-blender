# Sdf Grid Median Node, Sdf Grid Offset Node, Volume To Mesh Node, Voxelize Grid Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SDF Grid Median Node; SDF Grid Offset Node; Volume to Mesh Node; Voxelize Grid Node; Cube Grid Topology Node; Volume Cube Node; Get Named Grid Node; Grid Info Node; Voxel Index Node; Advect Grid Node; Grid Curl Node; Grid Divergence Node; Grid Gradient Node; Grid Laplacian Node; Sample Grid Node; Sample Grid Index Node; Set Grid Background Node; Set Grid Transform Node.

## SDF Grid Median Node

Applies a median filter to a Signed Distance Field. Each voxel becomes the median of its neighbors—eliminating noise and small artifacts while retaining sharp features and edges. Non-linear filtering excels at impulsive noise (isolated spikes/dips) versus mean or Laplacian approaches. Retains overall structure and perimeter definition. Valuable for refining SDFs from noisy or voxelized source meshes.

Inputs:
- Grid: Signed distance field to filter
- Width: Median filter kernel radius in voxels; larger widths produce stronger smoothing via wider neighborhood
- Iterations: How many times the filter runs; more passes deepen the smoothing and knock back noise while still holding edges crisp

Outputs:
- Grid: SDF after median filtering; reduced high-frequency noise and artifacts; sharp edges and important structural details retained

## SDF Grid Offset Node

Offsets the surface of a Signed Distance Field by a specified world-space distance. Positive offset inflates (expands); negative offset shrinks (contracts). Preserves correct signed distance properties throughout the field. Core volumetric technique for wall-thickness modification, shell generation, collision-volume expansion, or blend-margin tuning.

Inputs:
- Grid: Signed distance field to offset
- Distance: Offset distance in world units; positive expands (dilation), negative contracts (erosion); applied uniformly in all directions while preserving smoothness and SDF property

Outputs:
- Grid: SDF with surface offset; preserves SDF property for subsequent booleans or mesh conversion

## Volume to Mesh Node

Builds a mesh at the volume surface. A threshold value specifies the surface boundary; voxels exceeding the threshold count as interior.

Inputs:
- Volume: Standard geometry input

Resolution Mode — Controls final mesh resolution:
- Grid: Resolution depends on converted grid resolution; higher grids yield higher-resolution meshes; often most efficient
- Voxel Amount: Specifies approximate final mesh resolution; voxel size adapts to volume size
- Voxel Size: Uses fixed resolution independent of volume changes

Voxel Amount: Approximate final mesh resolution; voxel size adapts to volume dimensions

Voxel Size: Fixed resolution unaffected by volume changes

Threshold: Voxels > threshold are inside; mesh generates on inside/outside boundary ("iso value")

Adaptivity: Reduces final face count by simplifying geometry where detail is unnecessary (similar to decimation)

Outputs:
- Mesh: Standard geometry output

## Voxelize Grid Node

Expands all active tiles in a sparse voxel grid into fully-voxelized regions. Sparse grids (SDFs, fog volumes) store inactive areas as compact tiles; this node unpacks tiles into explicit voxels, enabling direct access and modification. Preparatory for operations needing dense voxel data (sampling, filtering, arithmetic using neighboring values).

Inputs:
- Grid: Grid to voxelize (typically sparse SDF or fog volume whose active tiles should expand)

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector)

Outputs:
- Grid: Result with all active tiles converted to individual voxels; for fog volumes, interior sparse tiles expand to editable voxel values; for SDFs, produces fully dense representation suitable for precise sampling and editing

## Cube Grid Topology Node

Generates a boolean grid topology with specified bounds and resolution. Defines voxel layout and active region; usable with Field to Grid to construct volume grids. Output contains active voxels within regular, axis-aligned cube region.

Inputs:
- Bounds Min: Minimum world-space boundary; lower cube corner
- Bounds Max: Maximum world-space boundary; upper cube corner
- Resolution X/Y/Z: Voxel count along each axis; higher values increase detail and memory usage

Index space properties (Min):
- X, Y, Z: Starting voxel index for each axis

Outputs:
- Topology: Boolean grid defining grid topology and active region; active voxels correspond to bounds/resolution cube

## Volume Cube Node

Generates a volume by evaluating a density field on a 3D grid. Grid points space equally between Min/Max bounds. Density field depends only on Position node. Uses grid point extrema as volume bounds.

Inputs:
- Density: Value for new grid at each voxel
- Background: Value outside Min..Max bounds; voxels equaling background are pruned (memory efficient)
- Min: Left-most grid point; voxel volume lower bound
- Max: Right-most grid point; voxel volume upper bound
- Resolution X,Y,Z: Grid point count per axis; full voxel count = grid points - 1

Note: Resolution changes significantly impact performance (default 32 = ~33k evaluations; 100 = ~1M; 1000 = ~1B)

Outputs:
- Volume: Generated volume geometry

## Get Named Grid Node

Retrieves a specific voxel grid from a volume by name. Volumes contain multiple grids (density, color, temperature, velocity, etc.); this node accesses one for further processing.

Inputs:
- Volume: Input volume containing named grids
- Name: Grid name to retrieve (must match stored grid)
- Remove: When enabled, removes grid from volume after retrieval; useful for restructuring without duplication or memory management

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines Grid output type and usage in subsequent nodes.

Outputs:
- Volume: Resulting volume after optional grid removal
- Grid: Extracted grid for Name/Data Type; passable to Sample Grid, Grid to Mesh, or other node manipulation

## Grid Info Node

Retrieves structural and metadata information about a voxel grid. Provides spatial transform and background value details describing grid positioning and inactive-voxel storage. Useful for inspecting or reusing grid parameters in other operations (aligning transforms, matching resolutions, reconstructing fields with consistent background).

Inputs:
- Grid: Voxel grid to query

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines Grid input type and Background Value output type.

Outputs:
- Transform: Transform matrix converting grid index space to object space; defines voxel positioning, scaling, orientation in 3D; passable to Set Grid Transform or alignment operations
- Background Value: Default value for inactive voxels (as set by Set Grid Background or similar); represents empty value in outside regions

## Voxel Index Node

The Voxel Index node outputs the integer index of the voxel the field is currently being evaluated on. Unlike a position in object space, the voxel index gives the discrete cell coordinates inside a voxel grid, so you can reason about neighboring voxels directly in index space without converting through world or object space. Combine it with nodes such as Integer Math and Sample Grid Index to sample values from nearby voxels by offsetting the indices.

Inputs: this node has no inputs.

Outputs:
X, Y, Z — the integer indices of the current voxel in the grid along each axis. They identify which voxel the field is sampling at this evaluation point, and can be offset (for example, add or subtract 1 on X) and passed to Sample Grid Index to read values from neighboring voxels.
Tile:
Is Tile — whether the current evaluation is happening on a tile rather than on a single voxel. For performance, some operations evaluate fields on tiles that cover multiple voxels at once, and then the coordinates from X, Y, and Z alone don't describe the full covered region; if this is false, the extent is always 1.
Extent X, Extent Y, Extent Z — the number of voxels along each axis of the tile. For a normal voxel the extent on each axis is 1; for a tile covering multiple voxels, the extents describe how many voxels are grouped together in X, Y, and Z. Use these to detect and handle cases where an evaluation represents an aggregated region (a tile) instead of an individual voxel, so the result isn't misinterpreted as referring to just one voxel.

## Advect Grid Node

Moves voxel values through a velocity field over time via numerical integration. Advection evolves quantities (density, temperature, color) according to flow fields; used in fluid, smoke, motion simulation. Supports multiple integration schemes; trades speed, accuracy, stability. Works on scalar/vector grids with uniform voxel scale. Conceptually: trace each voxel backward through velocity field by time step, sample previous grid value, assign to current voxel.

Inputs:
- Grid: Grid to advect (uniform voxel scale required)
- Velocity: Vector grid defining flow direction/magnitude; determines value transport through space
- Time Step: Advection time step in seconds; larger values = faster motion; may reduce accuracy/stability

Integration Scheme:
- Semi-Lagrangian: First-order, fastest, most stable; introduces noticeable numerical diffusion (blurring)
- Midpoint: Second-order; balances speed/accuracy for most cases
- Runge-Kutta 3: Third-order; higher accuracy, moderate cost
- Runge-Kutta 4: Fourth-order, highest single-step accuracy; ideal for detailed simulations, slower
- MacCormack: Implicit diffusion control; reduces dissipation while maintaining stability
- BFECC: Back and Forth Error Compensation and Correction; minimizes dissipation, maintains sharp features

Limiter — Overshoot/undershoot strategy:
- None: No limiting; fastest; can introduce gradient-region artifacts
- Clamp: Constrains values to original neighborhood range; prevents over/undershooting, preserves stability
- Revert: Falls back to first-order where clamping necessary; more conservative/stable than clamping alone

Properties:
Data Type: Grid data type (Float, Integer, Vector). Determines field type being advected.

Outputs:
- Grid: Advected grid after Time Step elapsed; each voxel value transported by velocity field and integration scheme

## Grid Curl Node

Computes the curl of a vector field in a voxel grid. Curl represents local rotational motion or circulation—how much and in what direction the field "spins" around each point.

Mathematically, curl of F = (Fx, Fy, Fz):
∇ × F = ((∂Fz/∂y - ∂Fy/∂z) î + (∂Fx/∂z - ∂Fz/∂x) ĵ + (∂Fy/∂x - ∂Fx/∂y) k̂)

Result vector points along rotation axis; magnitude indicates rotation strength. Useful for generating turbulence or analyzing rotational flow behavior in simulations and procedural effects.

Inputs:
- Grid: Vector grid for curl calculation (must store 3D vectors like velocity/direction fields)

Outputs:
- Curl: Vector grid representing field curl (local rotation); output direction indicates rotation axis; magnitude represents rotational strength at each voxel

## Grid Divergence Node

Computes the divergence of a vector field in a voxel grid. Divergence measures how much a field "spreads out" or "converges"—net flow entering or leaving each voxel. Positive divergence = field expanding outward (source); negative = converging inward (sink); near-zero = locally balanced flow. Used in fluid/smoke simulations for incompressibility enforcement or flow visualization.

Mathematically, divergence of F = (Fx, Fy, Fz):
∇ · F = (∂Fx/∂x + ∂Fy/∂y + ∂Fz/∂z)

Inputs:
- Grid: Vector grid for divergence calculation (must store 3D vectors like velocity/directional fields)

Outputs:
- Divergence: Float grid representing field divergence; positive values = regions where vectors spread (sources); negative = regions where vectors converge (sinks)

## Grid Gradient Node

Calculates the gradient of a scalar voxel grid. Gradient is a vector field describing direction and rate of steepest increase at each voxel; shows how and where scalar quantity (density, temperature, distance) changes in 3D space. Gradient vector points toward increasing values; magnitude represents change rate in that direction.

Mathematically, gradient of f(x,y,z):
∇f = (∂f/∂x î + ∂f/∂y ĵ + ∂f/∂z k̂)

Used in procedural or simulation workflows deriving direction fields from scalars (surface normals from SDFs, flow direction from density/temperature).

Inputs:
- Grid: Grid for gradient computation (must contain float values like density/distance)

Outputs:
- Gradient: Vector grid representing field gradient; each vector points toward greatest value increase; length corresponds to change rate

## Grid Laplacian Node

Computes the Laplacian of a scalar voxel grid. Measures how a voxel value differs from neighbor average—how much the field "curves" or deviates locally. Defined as divergence of gradient; used in physics/geometry for diffusion, smoothing, curvature analysis, PDE solving.

Mathematically, Laplacian of f(x,y,z):
∇²f = (∂²f/∂x² + ∂²f/∂y² + ∂²f/∂z²)

Positive Laplacian = local minimum (smaller than surroundings); negative = local maximum (larger than surroundings).

Inputs:
- Grid: Scalar grid for Laplacian computation (must store float values like density, temperature, SDF)

Outputs:
- Laplacian: Float grid representing field Laplacian; each voxel contains sum of second derivatives along X/Y/Z axes; detects local peaks/valleys or drives smoothing/diffusion in procedural grids

## Sample Grid Node

Retrieves values from a voxel grid at given spatial positions. Evaluates stored data (float, integer, boolean, or vector) and returns interpolated result for each queried position. Useful for reading grids from other nodes (Mesh to SDF Grid, Field to Grid, Points to SDF Grid) and driving procedural effects, geometry deformation, shading.

Inputs:
- Grid: Grid to sample (stores scalar, vector, or color data per data type)
- Position: Spatial positions in object space; each position interpolates based on nearby voxel values

Interpolation method:
- Nearest Neighbor: Returns closest voxel value without interpolation; fastest; can appear blocky/discrete
- Trilinear: Linear interpolation across eight nearest voxels; smooth transitions; suitable for general use
- Triquadratic: Higher-order (quadratic) interpolation; even smoother gradients, more continuous; additional computation cost

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines output socket type.

Outputs:
- Value: Interpolated grid value at given positions; output type matches grid Data Type

## Sample Grid Index Node

Retrieves values directly from a voxel grid at specific integer indices rather than arbitrary spatial positions. Unlike Sample Grid (interpolates in object space), this node reads exact stored voxel values at specified coordinates. Useful for index-space work (voxel neighborhood lookups, procedural filtering, sampling from Voxel Index).

Inputs:
- Grid: Voxel grid to sample (stores scalar, vector, color, or boolean data per type)
- X, Y, Z: Integer voxel coordinates in index space; specifies voxel to retrieve along each axis

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines Grid input type and Value output type.

Outputs:
- Value: Voxel value at specified indices; output type matches grid Data Type; no interpolation—values sampled exactly as stored

## Set Grid Background Node

Defines the background value for a voxel grid—the value returned when sampling inactive regions or uninitialized tiles. By default, empty voxels evaluate to zero or an implicit value; this node customizes that behavior. Useful for procedural grid construction or multi-grid combination.

Inputs:
- Grid: Grid whose background value modifies
- Background: Value assigned to inactive/uninitialized voxels and tiles; returned when sampling outside defined region instead of zero
- Update Inactive: Override all values in inactive voxels as well

Properties:
Data Type: Grid data type (determines Background input type and grid value types: Float, Integer, Boolean, Vector)

Outputs:
- Grid: Grid with updated background value; passable to Sample Grid Index or Sample Grid for consistent out-of-region results

## Set Grid Transform Node

Establishes how a voxel grid maps from index space (voxel coordinates) into object space. Default mappings assign integer voxel indices directly to object coordinates; this node permits custom mapping matrices for grid repositioning, orientation, or scaling relative to objects/scenes.

Inputs:
- Grid: Grid whose transform changes
- Transform: New transform from grid index space to object space; typically from Transformation Matrix

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines value storage type and must match input grid.

Outputs:
- Is Valid: True if provided transform applied successfully; fails if non-invertible or extreme scaling (0, negative/positive combinations)
- Grid: Grid with updated transform; new transform affects voxel-to-object interpretation, influencing grid interactions with other geometry and sampling

## Store Named Grid Node

Stores a voxel grid in a volume geometry under a specified name. Volumes hold multiple grids (density, temperature, velocity, etc.); accessible later via Get Named Grid. Replaces existing grids with same name; enables grid updates during geometry node evaluation.

Inputs:
- Volume: Volume geometry receiving the grid
- Name: Storage name for grid (used later with Get Named Grid or Spreadsheet Volume Grids section); reuses name replaces existing
- Grid: Grid to store (must have compatible resolution/transform; data type must match node Data Type property)

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines Grid input type and storage correctness.

Outputs:
- Volume: Volume with newly stored grid; replaces same-named predecessor or adds as new entry

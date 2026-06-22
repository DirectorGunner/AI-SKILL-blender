# Texture, Render, Hair, Simulation Nodes ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Texture; Render; Hair; Simulation Nodes; Edges.

## Texture

### Texture 

Reference

Panel :

Physics ‣ Force Fields

Type :

Texture

A Texture field permits establishing intricate force distributions with directional intensity encoded by color. Red maps to the X axis, green to Y, and blue to Z (matching 3D Viewport coordinate axis coloring). A value of 0.5 signifies zero force. Values exceeding 0.5 produce acceleration along the negative axis direction (e.g., -Z), while values under 0.5 accelerate along the positive direction (e.g., +Z).

### Options 

UI for a Texture force field. 

Texture Mode

Specifies how force vectors derive from the texture.

Curl :

Derives the force vector from the curl of the 3D-RGB texture (RGB vector rotation). Functions exclusively with color textures. Example use: crafting appealing turbulence with color clouds textures incorporating Perlin noise.

Gradient :

Produces the force vector as the 3D gradient of texture intensity (grayscale). The gradient points in the increasing brightness direction.

RGB :

Applies color components directly as force vector components in the matching axis directions. Requires an RGB texture (image or color ramp), making single-color Blend textures insufficient.

Nabla

Specifies the offset for computing partial derivatives in Gradient and Curl modes.

Use Coordinates

References emitter object coordinates (plus rotation and scale) as the particle texture space. Enables force fields that move and rotate alongside an object.

Root Texture Coordinates

Valuable for hair simulations; applies the texture force calculated at the particle root to the complete hair strand.

2D

Disregards particle Z position, utilizing only X and Y for texture coordinates.

Procedural textures exhibit true three-dimensionality.

### Examples 

- A uniform texture (0.5, 0.0, 0.5) generates positive Y-axis force, aligning hair along the Y direction.

- A blend texture with color ramp establishes a force boundary. Left edge (0.5, 0.5, 0.5), right edge (1.0, 0.5, 0.5) creates a plane perpendicular to XY and parallel to Z. Object coordinate assignment lets the object reposition particles through space.

- An animated wood texture produces wave-like particle motion.

Texture

Maps a texture onto Freestyle strokes.

Line Style: Texture.

Use Nodes
In Cycles, shader Nodes define textures.

Spacing Along Stroke
Adjusts how frequently textures repeat along the stroke.

Go to Linestyle Textures
Provides quick access to texture settings in the Properties Textures panel. Ensure Use Nodes is activated beforehand.

### Nodes

### UV Along Stroke Node

UV Along Stroke Node.

This node enables texture application across strokes, allowing simulation of pencil, brush, and various artistic media effects.

Note

UV coordinates are created exclusively by Freestyle's rendering pipeline. Standard UV Map nodes are incompatible, as they work with permanent mesh UV data.

#### Inputs

This node has no inputs.

#### Properties

Use Tips
Designates the lower portion of a texture image for stroke tips (endpoints), with the upper portion spanning the main body.

#### Outputs

UV
Texture coordinates projected along the stroke path.

### Line Style Output Node

Line Style Output Node.

This node merges texture data with the base line-style coloration.

#### Inputs

Color
Incoming color from the texture.

Color Factor
Blending strength for the Color input.

Alpha
Incoming transparency from the texture.

Alpha Factor
Blending strength for the Alpha input.

#### Properties

Mix
Choose the blending method (refer to Color Blend Modes).

Clamp
Caps the output color to a maximum of 1.0.

#### Outputs

This node has no outputs.

### Example

The setup shown below demonstrates how to apply a floral image across strokes. The UV Along Stroke node extracts Freestyle-generated texture coordinates, feeding them to an Image Texture node's Vector input. Once a texture is loaded into the Image Texture node, its output connects to the Line Style Output node's Alpha input. When Alpha Factor is one, the texture replaces the line style's alpha (as shown in the Freestyle Line Style panel). The Color connection employs Mix blending with Color Factor at zero, preserving the line style's gradient overlay.

Example of Line Style Nodes
(blend-file).

The FS_floral_brush.png image featured here is a Freestyle brush texture with dual regions: a seamless tile for the stroke body (top), and tip caps for endpoints (bottom).

## Render

### Render 

Reference

Panel :

Particle System ‣ Render

The Render Panel configures rendered particle appearance.

Note

Cycles exclusively facilitates Object and Collection render modes.

### Common Settings 

Scale

Scale Randomness

Material

Determines which material property governs particle shading.

Coordinates System

Designates an alternate object's coordinate framework for particle generation point calculation.

Show Emitter

When deactivated, the emitter stays out of rendered output. Enable Emitter to incorporate mesh rendering.

### Render As 

### None 

None designation prevents particle rendering. Useful when particles drive object duplication instead.

### Halo 

Halos display as glowing spots or light concentrations. They lack genuine light emission since they don't illuminate the surrounding scene like light objects. Halos remain visible but physically insubstantial.

### Path 

The Visualization panel for Path visualization. 

Path visualization requires Hair particle systems or Keyed particles.

B-Spline

Routes hair through B-spline curves. Appropriate for lower Render settings, trading control for smoother geometry.

Steps

Sets the path subdivision depth (value represents base 2 exponent). Adjust cautiously; Render doubling quadruples memory demand. Rendering velocity increases with reduced render values (sometimes dramatically). Practical minimums depend on hair waviness. Zero steps yield one subdivision, 1→2, 2→4, 3→8, 4→16, … 𝓃 → 2 𝓃.

### Timing 

Reference

Panel :

Particle System ‣ Render ‣ Timing

Type :

Hair

Absolute Path Time

Path timing uses absolute frame numbering.

End

Terminal moment for the practical path.

Random

Applies length randomization to paths.

### Object 

Reference

Panel :

Particle System ‣ Render ‣ Object

Instance Object

Particles substitute this specified object.

Global Coordinates

References object world coordinates for instancing.

Object Rotation

Instances use object rotation.

Object Scale

Instances use object scale.

### Collection 

Reference

Panel :

Particle System ‣ Render ‣ Collection

Instance Collection

Group members get instanced consecutively at particle positions.

Whole Collection

All group members render simultaneously at each particle position rather than sequential selection.

Pick Random

Group members render in random sequence; only one appears per particle.

Global Coordinates

References object world coordinates for instancing.

Object Rotation

Instances use object rotation.

Object Scale

Instances use object scale.

#### Use Count 

Reference

Panel :

Particle System ‣ Render ‣ Collection ‣ Use Count

Allows individual objects within groups to render multiple times. The list view allows order and frequency specification.

Copy Particle Instance Object

Generates a duplicate of the list entry.

Remove Particle Instance Object

Strikes the entry from the list.

### Extra 

Reference

Panel :

Particle System ‣ Render ‣ Extra

Parents Particles

Incorporates parent particles when child particles get rendered. Children feature numerous deformation mechanisms, placing flat parent geometry behind their curved offspring. Parents hide automatically when Children activate. Refer to Children for details.

Unborn

Particles get rendered before generation.

Dead

Particles get rendered post-termination. Particularly helpful when particles expire at contact ( Die on hit ), allowing surface-based particle deposition.

## Hair

### Hair 

This material documents the deprecated hair system.
For the current hair system, see the Hair Nodes page.

## Simulation Nodes

### Simulation Nodes 

Geometry Nodes can construct custom physics simulations via Simulation Zones.
Simulation zones enable one frame's output to influence the next, allowing simple rules to produce complex behaviors over time.
Physics simulation with dedicated solvers represents the most common use case.

See also

Simulation Zones documentation

### Baking 

Playback automatically caches the simulation.
A bright yellow timeline line marks valid cache frames, enabling animators to review all previous frames rapidly.

Cached frames in the Timeline. 

Once complete, baking to disk permits non-sequential rendering.

Simulation and Physics, Geometry Nodes interface. 

Note

Baking simulations bakes all simulations in all modifiers for selected objects.

Calculate to Frame
Computes geometry node simulations from start to current frame.

Bake
Commits simulations in geometry node modifiers to disk.
The blend-file must be saved; file location determines baked-data location.
Modifier Internal Dependencies allow per-modifier baked-data directory changes.

Delete Cached Simulation
Removes cached/baked geometry node simulations.

Cache
For scenarios where current frame alone matters, disable caching to conserve memory.

### Examples 

Combined with Index of Nearest, this enables numerous sphere-based simulations.

## Edges

### Edges 

Reference

Panel :

Physics ‣ Soft Body ‣ Edges

Configure mesh edges to function as springs. See interior forces.

Springs
Designate a vertex group for spring stiffness values.

Pull
Spring stiffness for edges (stretch resistance).
Lower values mean weak springs (elastic material); higher values mean strong springs (stiff material).

0.5 resembles latex; 0.9 resembles a sweater; 0.999 resembles heavily starched fabric or leather.
Instability develops at 0.999, warranting reduction.

Push
Soft-body compression resistance, like a compression spring.
Low values suit fabric; high values suit inflated or stiff objects.

Damp
Spring friction magnitude. High values (up to 50) dampen Push / Pull and stabilize cloth.

Plasticity
Permanent post-collision deformation.
Vertices assume new positions without modifier application.

Bending
Adds virtual connections between a vertex and its neighbors' neighbors, including diagonals. Damping applies here too.

Length
Edges shrink or expand in percentage; 0 disables. 100% maintains size.

Collision

Edge
Detects soft-body mesh-edge collisions.

Face
Detects soft-body mesh-face collisions (computationally intensive).
Face-enabled collision resolves errors but lacks dampening. Soft-body regions near collision meshes "jitter" even without motion.
Edge collision includes dampening for better control, though collision-object Deflection Dampening doesn't affect face collision.

### Aerodynamics 

Surrounding-medium force.
See exterior forces for details.

Type

Simple :

Edges receive drag from surrounding medium.

Lift Force :

Edges receive lift while passing through medium.

Factor
Aerodynamic force magnitude. Begin with 30.

### Stiffness 

Quad-face diagonal edges act as springs, preventing collapse.

Shear
Virtual spring stiffness for quad-face diagonals.

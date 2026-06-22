# Repeat Zone, Align Rotation To Vector Node, Axes To Rotation Node, Axis Angle To Rotation Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Repeat Zone; Align Rotation to Vector Node; Axes to Rotation Node; Axis Angle to Rotation Node; Euler to Rotation Node; Invert Rotation Node; Mix Rotation; Quaternion to Rotation Node; Rotate Rotation Node; Rotate Vector Node; Rotation to Euler Node; Rotation to Quaternion Node; Find in String Node; Format String Node; Join Strings Node; Match String Node; Replace String Node; Slice String Node.

## Repeat Zone

Runs a set of nodes repeatedly over iterations.

The zone spans from an input node (left) to an output node (right), with an orange area in between.
On first execution, inputs are evaluated and sent into the inner nodes.
These nodes write to the output node for the next iteration's inputs and the final result.

Inner nodes can read inputs from outside the zone (same value every iteration);
they cannot send outputs outside.

**Inputs**

Iterations
How many times to execute. The Iteration socket provides the current index (starting at 0).

Geometry
Default geometry input. Extra inputs are added by connecting external outputs to the zone's blank socket,
or via the Repeat Items list in Properties.

Labels are editable via Ctrl-LMB in the zone or Repeat Items panel (double-click to rename).

**Properties**

Reference: Sidebar ‣ Node ‣ Properties

Repeat Items
List view for creating, deleting, reordering, and relabeling inputs.

Socket Type
Data type of the selected input.

Inspection Index
Which iteration to display in socket inspection and the Viewer Node.

**Example**

Builds a pyramid with adjustable levels. Each iteration creates a cube, positions it,
and merges it with the prior iteration's result.

### Repeat Zone

A Repeat Zone runs a set of nodes over and over.

Picture the zone as three parts: an input node off to one side, an output node off the other, and an orange band between for the nodes you want repeated. The first time through, it reads its inputs and passes them along to the inner nodes. Those inner nodes write back to the output node — feeding the round that follows, and, after the last round, delivering the zone's final result.

Nodes inside the zone may also draw inputs from nodes outside it — those stay the same every iteration. They cannot, though, send their outputs back out to nodes beyond the zone.

### Inputs

Iterations
How many times to run the zone. The Iteration socket reports the current iteration's index, counting from 0.

Geometry
The default geometry input. To add others, run a node's output into the zone's spare input, or use the Repeat Items list found on the node's Properties panel.

Relabel inputs by Ctrl - LMB on them, whether on the zone directly or over in the Repeat Items list — and that list responds to a double-click as well.

### Properties

Reference

Menu :

Sidebar ‣ Node ‣ Properties

Repeat Items
List View for adding, removing, reordering, and renaming the zone's inputs.

Socket Type
The data type of the selected input.

Inspection Index
The iteration surfaced during socket inspection and inside the Viewer Node.

### Cycles and EEVEE Differences

In Cycles the iteration count has to resolve to a constant, which means it cannot be driven by Input Nodes or Texture Nodes.

Error shown when Cycles is selected as the active Render Engine .

EEVEE carries no such limit, so any kind of node can drive the iteration count.

## Align Rotation to Vector Node

Rotates an Euler orientation toward a specified direction, blended by a factor.

**Inputs**

Rotation
The Euler rotation to realign. (Must be a rotation input, not a direction vector like normal.)

Factor
How much to rotate toward the vector. Zero disables the node; one aligns perfectly.

Vector
Target direction in object-local space. Zero-vector points mean no rotation.

**Properties**

Axis
Which local axis rotates toward the vector.

Pivot

Auto: Finds the optimal rotation angle, minimizing rotation magnitude.

X, Y, Z: Rotates around a specific local axis.

**Outputs**

Rotation
The rotated Euler value.

## Axes to Rotation Node

Builds a rotation from two axis directions.

Tip: Often used with mesh or curve normals and tangents.

**Inputs**

Primary Axis
The desired direction of the primary axis.

Secondary Axis
The desired direction of the secondary axis; ideally orthogonal to primary.

**Properties**

Primary Axis
Which axis (X, Y, Z) aligns exactly to the primary direction.

Secondary Axis
Which axis aligns as closely as possible to the secondary direction.

**Outputs**

Rotation
The rotation aligning both axes to their target directions.

## Axis Angle to Rotation Node

Converts an axis-angle representation to a standard rotation.

**Inputs**

Axis
Unit vector along the rotation axis.

Angle
Rotation magnitude around the axis.

**Outputs**

Rotation
Standard rotation value.

## Euler to Rotation Node

Builds a standard rotation from an Euler angle triplet.

**Inputs**

Euler
The Euler rotation triplet.

**Outputs**

Rotation
Standard rotation value.

## Invert Rotation Node

Reverses a rotation.

**Inputs**

Rotation
Standard rotation value.

**Outputs**

Rotation
The reversed rotation.

## Mix Rotation

Blends two inputs using a control factor, supporting float, vector, color, and rotation types.
Color mode adds blend modes.

**Inputs**

Factor
Strength of interpolation between A and B.

A/B
The two inputs to blend.

**Properties**

Data Type
Supported: float, vector, color, rotation.

Factor Mode (Vector only)

Uniform: Single float controls all channels.

Non-Uniform: Vector controls each XYZ channel separately.

Mix (Color only)
Choose from: Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light.
(See Color Blend Modes for details.)

Clamp Factor
Lock factor between 0.0 and 1.0, or allow Extrapolation.

Clamp Result (Color only)
Constrain output to [0.0, 1.0].

**Outputs**

Result
The blended value in the selected data type.

**Examples**

See Mix Color Node for additional examples.

## Quaternion to Rotation Node

Translates quaternion components into a standard rotation.

**Inputs**

W, X, Y, Z
Quaternion component values.

**Outputs**

Rotation
Standard rotation value.

## Rotate Rotation Node

Applies an extra rotation to an existing one.

To rotate an Euler, use Euler to Rotation first.

**Inputs**

Rotation
The initial rotation.

Rotate By
The additional rotation to apply.

**Properties**

Space

Global: Apply rotation in world space.

Local: Apply rotation in object space.

**Outputs**

Rotation
The combined rotation.

## Rotate Vector Node

Applies a rotation to a vector.

**Inputs**

Vector
The vector to rotate.

Rotation
Standard rotation value.

**Outputs**

Vector
The rotated vector.

## Rotation to Euler Node

Converts a standard rotation to an Euler angle triplet.

**Inputs**

Rotation
Standard rotation value.

**Outputs**

Euler
The Euler representation.

## Rotation to Quaternion Node

Converts a standard rotation to quaternion components.

**Inputs**

Rotation
Standard rotation value.

**Outputs**

W, X, Y, Z
Quaternion component values.

## Find in String Node

Finds how many times a substring appears and locates the first occurrence.

**Inputs**

String
The string to search within.

Search
The substring to locate.

**Outputs**

First Found
Starting position of the first match.

Count
Total occurrences of the substring.

## Format String Node

Inserts values into a string using Python-compatible or Blender format syntax.

Simplifies string assembly by formatting values inline without manual string conversion or stacked concatenation nodes.

See also: Python Format String Syntax and {fmt} Format String Syntax.

**Inputs**

Format
A string with placeholders: `Count: {}` inserts the first value; `Count: {name}` inserts a named parameter.

Additional numeric or text inputs are managed via the Format Items list in the sidebar.

**Properties**

### Format Items

List view for adding, removing, reordering, and renaming dynamic inputs.
Each entry corresponds to an insertable value.

Socket Type

Float: Floating-point number (e.g., 3.14).

Integer: Integer number (e.g., 42).

String: Text string.

**Outputs**

String
The assembled string.

**Notes**

- Supports both unnamed (`{}`) and named (`{name}`) placeholders; all unnamed must precede named.

- Supports float, integer, and string inputs only.

- Python conversions like `!r` are unsupported.

- Sub-attribute access (e.g., `{vector.x}`) is unsupported.

- Percent-style formatting (e.g., `%d`) is unsupported.

- Alternate forms using `#` (e.g., `{:#x}`) are unsupported.

- Locale formatting via `L` is unsupported.

- Grouping separators (e.g., `{:,}`, `{:_}`) are unsupported.

### Input Naming Behavior

Each input needs a unique, valid identifier for placeholders (e.g., `{value}`).
Auto-naming logic:

- If connected, uses the first character of the linked socket name.

- Otherwise defaults to letters a–z.

- Converts invalid names to valid identifiers.

- Appends a suffix (e.g., `_001`) as a fallback.

Important: Names must be valid identifiers and unique. Invalid names may cause formatting errors.

**Examples**

### Basic

Format: `Count: {}`
Inputs: Integer 5
Result: `Count: 5`

### Multiple Values

Format: `X: {}, Y: {}`
Inputs: Float 1.5, Float 2.0
Result: `X: 1.5, Y: 2.0`

### Named Inputs

Format: `Size: {width} x {height}`
Inputs: width=1920, height=1080
Result: `Size: 1920 x 1080`

### Padded Numbers

Format: `Frame_{:04}`
Inputs: Integer 12
Result: `Frame_0012`

### Number Format (Template Style)

Format: `##.00`
Input: Float 3.1415
Result: `03.14`

### Path with Frame Number

Format: `/output/image_{:04}.png`
Input: Integer 42
Result: `/output/image_0042.png`

## Join Strings Node

Combines any number of input strings into a single output, separated by an optional delimiter.
The order follows the vertical stacking of inputs in the multi-input socket.

Tip: Combine with the line break from the Special Characters Node to build a multi-line string for the String to Curves Node.

**Inputs**

Delimiter
Text placed between each concatenated string.

Strings
Multiple strings to combine in connection order.

**Outputs**

String
The concatenated result.

## Match String Node

Compares two strings using the selected operation and outputs a Boolean.
Handy for conditional logic: matching object names, filtering attribute values, etc.

**Inputs**

String
The input to evaluate.

Operation

Starts With: True if the input begins with the key.

Ends With: True if the input ends with the key.

Contains: True if the key is anywhere in the input.

Key
The comparison target.

**Outputs**

Result
Boolean result of the comparison.

## Replace String Node

Replaces occurrences of a substring with another string.

**Inputs**

String
Standard string input.

Find
The substring to locate and replace.

Replace
The replacement text.

**Outputs**

String
Standard string output.

**Examples**

Using the node to insert a newline character into a string.

## Slice String Node

Extracts a contiguous substring from a larger string.

**Inputs**

String
The source string to slice.

Position
Starting index (0-based) of the new substring.

Length
How many characters to extract.

**Outputs**

String
The extracted substring.

## Special Characters Node

Outputs non-typeable string characters (line breaks, tabs, etc.).

Tip: Combine with String to Curves Node to create multi-line text;
use with Join Strings Node or Replace String Node.

**Inputs**

This node has no inputs.

**Outputs**

Line Break
Newline character (`\n`).

Tab
Tab character for indentation.

## String Length Node

Counts how many characters are in the input string.

**Inputs**

String
The string to measure.

**Outputs**

Length
Character count as an integer.

## String to Curves Node

Converts text into curve instances. Each unique character becomes a curve once;
further uses become instances of that geometry. Instance names match their character.

Result is memory-efficient (unique characters process once) but each character instance is identical.
To process each character individually, use Realize Instances Node.

Tip: Hold the mouse over the socket to view the evaluated string value via socket inspection.

**Inputs**

String
Standard string input.

Size
Character size; all other inputs scale by this value.

Font
Typeface for curve generation.

### Alignment

Align X

Left: Left-aligned.

Center: Centered.

Right: Right-aligned.

Justify: Flush left and right.

Flush: Flush left and right with equal spacing.

Align Y

Top: Top-aligned.

Top Baseline: Baseline-aligned to top.

Middle: Vertically centered.

Bottom Baseline: Baseline-aligned to bottom.

Bottom: Bottom-aligned.

Pivot Point

Midpoint: Center of each character's bounds.

Top Left: Top-left corner.

Top Center: Midpoint of the top edge.

Top Right: Top-right corner.

Bottom Left: Bottom-left corner.

Bottom Center: Midpoint of the bottom edge.

Bottom Right: Bottom-right corner.

### Spacing

Character Spacing
X-axis kerning scale factor.

Word Spacing
X-axis whitespace scale factor between words.

Line Spacing
Distance between lines, multiplied by Size.

### Text Box

Overflow

Overflow: Wrap at Text Box Width.

Scale To Fit: Shrink text to fit both dimensions.

Truncate: Output only characters within the bounds;
move the rest to Remainder.

Text Box Width
Maximum width per line; words are not broken.

Text Box Height
Maximum height for all lines.

**Outputs**

Curve Instances
Geometry with one instance per character.

Remainder
Text that did not fit (Truncate mode only).

Line
Attribute field: line index per character (instance domain).

Word
Attribute field: word index per character (instance domain).

Pivot Point
Position of the selected Pivot Point in each instance's local space.

**Examples**

Create text boxes that overflow: unfit text from one String to Curves node
(with fixed text box) feeds into another, scaled to fit via a Scale to Fit node.

## String to Value Node

Parses a text string into a numeric value.
Useful for converting text from user input, files, or dynamic sources into numbers.

The node reads characters from the start until a number is successfully parsed.
Parsing failure returns 0.0.

**Inputs**

String
The input text to convert.

**Properties**

Data Type

Float: Parse as floating-point.

Integer: Parse as 32-bit integer.

**Outputs**

Value
The converted number.

Length
Character count successfully parsed as part of the number.
Indicates where the numeric portion ends, enabling further substring work.

**Examples**

- `"3.1415"` with Float selected: outputs 3.1415 and length 6.

- `"42abc"` with Integer selected: outputs 42 and length 2.

- `"hello"`: outputs 0 and length 0.

## Value to String Node

Generates a text representation of a numeric value.

**Inputs**

Value
The floating-point value to convert.

Decimals (Float Data Type)
Precision of the output value.

**Properties**

Data Type

Float: Convert a floating-point value to text.

Integer: Convert a 32-bit integer to text.

**Outputs**

String
Text representation of the input.

## Clip Grid Node

Restricts a voxel grid to a bounding box specified in index space. Voxels outside the min/max indices deactivate; their values reset to the grid's background. Partially clipped tiles voxelize fully so individual voxels can be isolated.

Inputs:
- Grid: Input voxel grid to clip
- Min X/Y/Z: Minimum index bounds
- Max X/Y/Z: Maximum index bounds

Properties:
Data Type: Grid data type (Float, Integer, Boolean, or Vector). Must match input grid.

Outputs:
- Grid: Clipped grid with out-of-bounds voxels deactivated and reset

## Field to Grid Node

Creates new voxel grids by sampling geometry fields on an existing grid's topology. Evaluates input fields at voxel positions, producing grids that match resolution, transform, and domain.

Inputs:
- Topology: Reference grid defining voxel layout, resolution, and transform
- Fields: Additional sockets for each field to evaluate (add by dragging into blank area)

Note: Color fields evaluate as Vector data type (color grids not yet supported)

Properties:
Configure each field individually: set data type (Float, Vector, Boolean) and evaluation order

Outputs:
- One grid per field input, each containing sampled voxel data aligned with input topology

## Grid Dilate & Erode Node

Expands or contracts the active voxel regions of a volume grid. Modifies which voxels are active without changing stored values. Common uses: grow/shrink regions, fill gaps, remove noise, adjust boundaries.

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Must match input.

Inputs:
- Grid: Volume grid to modify
- Connectivity: Determines neighboring voxel treatment:
  - Face: 6-connectivity (face-adjacent only)
  - Edge: 18-connectivity (face or edge adjacent)
  - Vertex: 26-connectivity (face, edge, or vertex adjacent)
- Tiles: Active tile handling during operation:
  - Ignore: Tiles unmodified and don't contribute
  - Expand: Convert tiles to voxels, apply operation, leave fully voxelized
  - Preserve: Keep tiles unchanged when possible; voxelize only as needed (memory efficient)
- Steps: Operation repetition count; higher values expand/contract further

Outputs:
- Grid: Result with updated active voxel regions

## Grid Mean Node

Applies a box (mean) filter to a volume grid. Each active voxel's value becomes the average of neighbors within a box-shaped kernel. Smooths data, reduces high-frequency variation. Use cases: soften density, smooth noise, prepare volume for further work.

Properties:
Data Type: Grid data type (Float, Integer, Vector). Must match input.

Inputs:
- Grid: Volume to smooth
- Width: Filter radius in voxels; larger values increase neighborhood size and smoothing strength
- Iterations: Mean filter application count; higher values progressively smooth

Outputs:
- Grid: Filtered grid with smoothed voxel values

## Grid Median Node

Applies a median (box) filter to a volume grid. Each active voxel becomes the median of neighbors within a box kernel. Median filtering preserves sharp features while removing isolated noise—more effective than mean at edge retention. Use cases: clean sparse artifacts, maintain density/level-set edges.

Properties:
Data Type: Grid data type (Float, Integer, Vector). Must match input.

Inputs:
- Grid: Volume to smooth
- Width: Filter radius in voxels; larger values increase neighborhood scope and smoothing
- Iterations: Filter application count; repeated passes progressively smooth

Outputs:
- Grid: Filtered grid with updated voxel values

## Grid to Mesh Node

Converts a voxel grid to a polygonal mesh by extracting an isosurface at a specified threshold (similar to Marching Cubes). The boundary where grid values cross the threshold becomes the mesh surface. Enables conversion of procedural volumetric data (SDFs, density grids) into geometry for rendering or further modeling.

Inputs:
- Grid: Voxel grid to convert (must contain float values from SDF or density field)
- Threshold: Value defining the surface; voxels > threshold are inside, smaller are outside. For SDF, threshold 0.0 typically marks the surface
- Adaptivity: Mesh simplification by curvature; higher values reduce polygon count by merging flat areas; 0.0 disables adaptivity for uniform density

Outputs:
- Mesh: Extracted surface where grid scalar values equal Threshold; usable for rendering or further processing

## Grid to Points Node

Transforms a voxel grid into a point cloud representation. All active voxels and tiles map to individual points. The voxel value attaches as an anonymous attribute; index-space data is available as field output. Enables custom volume visualization or downstream point manipulation.

Inputs:
- Grid: Voxel grid to convert

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Determines Value output type.

Outputs:
- Points: Point cloud (one point per active voxel or tile)
- Value: Stored grid value at each voxel; for tiles, the shared value across all voxels

Voxel Index output:
- X, Y, Z: Voxel coordinates in index space (or tile minimum for tiles)
- Is Tile: True when point represents a tile rather than single voxel
- Extent: Voxel or tile size; 1 for individual voxels; cubic dimension in voxels for tiles

## Prune Grid Node

Optimizes voxel grid storage by collapsing uniform regions into coarser tiles or inner nodes (inverse of Voxelize Grid). Detects large uniform areas and replaces them with compact representations. Especially useful after operations creating constant-value regions (filling, clipping, thresholding).

Inputs:
- Grid: Grid to optimize

Pruning methods (Mode):
- Inactive: Turns inactive voxels/tiles into inactive background tiles; basic cleanup for empty regions
- Threshold: Collapses regions where all voxels have approximately same value and active state (within tolerance) into background tiles; good for fog/scalar grids with smooth variations
- SDF: Specialized for signed distance fields; replaces inactive tiles with inactive nodes for faster, targeted pruning without threshold comparison; efficient for narrow-band SDFs with large interior/exterior regions

Threshold parameter: Regions are uniform if voxel values differ by less than this amount; higher thresholds enable aggressive simplification; lower values preserve finer detail

Properties:
Data Type: Grid data type (Float, Integer, Boolean, Vector). Must match input.

Outputs:
- Grid: Optimized grid with uniform regions collapsed into larger tiles/nodes for compact, efficient representation

## SDF Grid Boolean Node

Performs boolean operations on two or more Signed Distance Field grids. Combines, subtracts, or intersects volumetric shapes directly in grid space with smooth, continuous results. Preserves the SDF property (each voxel stores shortest distance to nearest surface).

Inputs:
- Grid Intersect: Input for intersection operations; keeps overlapping regions only
- Grid 1 (Union/Difference): Base grid for boolean combination
- Grid 2 (Union/Difference): Grid to add or subtract from Grid 1

Operations:
- Intersect: Keeps overlapping region where both grids contain interior (negative) values
- Union: Combines by taking minimum distance at each voxel; merged shape of both inputs
- Difference: Inverts Grid 2's sign then takes maximum distance; carves one SDF out of another

Outputs:
- Grid: Resulting SDF after operation; maintains valid signed distance values; usable with Grid to Mesh or further volumetric operations

## SDF Fillet Node

Smooths or rounds off concave internal corners in a Signed Distance Field grid. Modifies the field to soften transitions at sharp inward angles (similar to mesh fillet/bevel). Affects only negative-curvature regions (concave corners); preserves volume. Results in organic, continuous surfaces; useful after boolean operations.

Inputs:
- Grid: Input SDF to smooth (typically from boolean or mesh conversion)
- Iterations: Smoothing pass count; higher values produce larger, smoother fillet radius; increases computation time; single iteration = subtle rounding; multiple = progressively softer surfaces

Outputs:
- Grid: SDF with concave corners rounded; convertible to mesh via Grid to Mesh or usable in further volumetric work

## SDF Grid Laplacian Node

Applies Laplacian flow smoothing to a Signed Distance Field grid. Progressively smooths the surface by diffusing fine details across neighboring voxels. Computationally efficient alternative to mean curvature flow. Refines SDFs from meshes or booleans where sharp transitions or voxel artifacts occur. Improves surface quality before mesh conversion.

Inputs:
- Grid: Signed distance field to smooth
- Iterations: Laplacian smoothing pass count; each iteration diffuses high-frequency surface variations; higher values increase smoothness but may cause slight surface shrinkage

Outputs:
- Grid: SDF after Laplacian flow; smoother, more continuous surface while preserving major shape features

## SDF Grid Mean Node

Applies mean (box) filter smoothing to a Signed Distance Field. Averages voxel values within a local neighborhood to smooth variations and noise while preserving overall shape. Works as a fast, separable averaging operation (box filter); suited for general-purpose softening after boolean, voxelization, or other volumetric operations.

Inputs:
- Grid: Signed distance field to smooth
- Width: Smoothing kernel radius in voxels; larger values produce broader smoothing, softer less-detailed surfaces; smaller values restrict to immediate neighbors, retaining fine detail
- Iterations: Mean filter application count; each iteration increases surface smoothness; multiple passes approximate Gaussian-like blur

Outputs:
- Grid: SDF after mean filtering; smoother, more uniform surface useful for refining noisy/rough SDFs before Grid to Mesh or other operations

## SDF Grid Mean Curvature Node

Applies mean curvature flow smoothing to a Signed Distance Field. Evolves the surface based on mean curvature; high-curvature (sharp/noisy) regions smooth faster than flatter areas. Unlike simple averaging or Laplacian, mean curvature flow adapts to geometric features for natural, shape-preserving smoothing. Effective after booleans or mesh-to-SDF conversion for removing high-frequency noise.

Inputs:
- Grid: Signed distance field to smooth (typically from mesh or procedural operation)
- Iterations: Mean curvature flow pass count; each iteration progressively smooths; small values gently polish; large values significantly alter shape

Outputs:
- Grid: SDF after mean curvature smoothing; reduced high-curvature noise, smoother transitions, major structural features retained

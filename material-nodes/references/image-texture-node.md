# Image Texture Node, Musgrave Texture Node, Node Based Tools, Align Euler To Vector Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Image Texture Node; Musgrave Texture Node; Node-Based Tools; Align Euler to Vector Node; Deprecated Nodes; Rotate Euler Node; Accumulate Field Node; Evaluate at Index Node; Evaluate on Domain Node; Field Average Node; Field Min & Max Node; Field Variance Node; For Each Geometry Element Zone; Bit Math Node; Boolean Math Node; Compare Node; Float To Integer Node; Hash Value Node.

## Image Texture Node

Image Texture Node

Note: Operates differently in geometry nodes vs shader nodes. Vector defaults to implicit position.

Uses an image file as texture. Samples with Vector input, outputs Color and Alpha.

Inputs
Image: Connect to Group Input node or open/select from the node directly.
Vector: Look-up coordinate. Uses Position attribute if unconnected.
Frame: For animated images, set the frame here (keyframeable).

Properties
Interpolation: Scaling method.
  Linear: Regular quality.
  Cubic: Smoother, better for bump maps.
  Closest: No interpolation; use for pixel art.
Extension: Behavior past image bounds.
  Repeat: Tile horizontally and vertically.
  Extend: Repeat edge pixels.
  Clip: Clip to bounds, exterior = transparent black.
  Mirror: Flip horizontally and vertically repeatedly.

Outputs
Color: RGBA color from the image.
Alpha: Alpha channel from image.

Examples: Image Texture displacing a plane.

### Image Texture Node

Applies an image to a surface as a texture.

### Inputs

Vector
A 3D coordinate projected onto the 2D image through the chosen Projection method; the node then reports the colour and alpha at that projected spot.

This socket usually takes a feed from the Texture Coordinate Node. Left unconnected, the coordinate comes from the object's active UV map (with Z = 0).

### Properties

Image
Image data-block to use.

Interpolation
Method to scale images up or down for rendering.

Linear :

Regular quality interpolation.

Cubic :

Smoother, better quality interpolation. Bump maps should use this for best results.

Closest :

No interpolation (nearest neighbor). Useful for rendering pixel art.

Smart :

Cycles Only
Only for Open Shading Language. Uses cubic interpolation scaling up and linear scaling down, for better speed and sharpness.

Projection
How Vector is projected onto the image to arrive at a colour.

Flat :

Lay the image in a unit square (running from (0, 0, 0) to (1, 1, 0)) and project the Vector straight down onto it. This is the usual choice with UV maps.

Box :

Lay the image on every face of a unit cube (running from (0, 0, 0) to (1, 1, 1)) and project the Vector onto that cube along whichever axis is nearest the mesh normal. It is a common pick for architectural models, which carry plenty of box-shaped objects.

Blend
Instead of hitting a single face (which gives hard seams), project onto several faces and blend the results. Raise the value for more blending and a smoother result.

Sphere :

Wrap the image over a sphere centred at (0.5, 0.5, 0.5) and project the Vector outward from that centre onto it. This is the obvious fit for spherical objects like planets, and works well on organic shapes too.

Tube :

Wrap the image around a cylinder based at (0.5, 0.5, 0) with height 1, then project the Vector sideways from the central axis onto it. Handy for things like a bottle label, though it does not suit the top or bottom of objects.

| Flat projection | Box projection |
| Sphere projection | Tube projection |

Extension
How the image extends when Vector lands outside the usual (0, 0, 0) to (1, 1, 1) bounds:

Repeat :

Tile the image across both axes.

Extend :

Stretch the image out by repeating its edge pixels.

Clip :

Crop to the original image size and make every pixel beyond it transparent black.

Mirror :

Flip the image over and over across both axes.

Source
Type of image (Single Image, Movie…). See Image Settings.

Frames
Frame count to play from a Movie-type image (video). Beyond it the clip halts unless Cyclic is on.

For the full clip, hit Match Movie Length in the Image Editor's Sidebar and copy the resulting Frames count onto the node.

Start Frame
Which scene frame the video starts on.

Offset
How far, in frames, to drag the video back in time — equivalently, how many opening frames to skip.

Hint

Video textures run at the scene's frame rate, not the clip's own, so a mismatch leaves them fast or slow. Park a Driver on the Offset to compensate: drop the expression below into the field, with StartFrame , VideoFrameRate and SceneFrameRate swapped for your actual numbers:

#(frame - StartFrame) * (VideoFrameRate - SceneFrameRate) / SceneFrameRate

Cyclic
Loop back to the start after the final frame for a continuous cycle.

Auto Refresh
Refresh the video texture in the 3D Viewport as you scrub the timeline.

Color Space
Whichever Color Space the file was written in. See Image Settings for details.

Alpha
The way this image handles its Alpha Channel. See Image Settings for details.

### Outputs

Color
RGB colour from the image. Where the image has transparency, the colour comes out premultiplied if the Alpha output is used, and straight (non-premultiplied) otherwise.

Alpha
Alpha channel from image.

### Examples

Image texture from GoodTextures.com.

## Musgrave Texture Node

Musgrave Texture Node

Blender retired the Musgrave texture node, folding every bit of its behaviour into the Noise Texture node.

A Roughness input now stands in for the former Dimension input; the two relate by Roughness = Lacunarity^(−Dimension).

Relative to the old Musgrave Texture node, the Detail input now wants a value one lower.

## Node-Based Tools

### Node-Based Tools

Geometry node groups can become tools invoked from menus.
The Tool Context builds such tools for access via the Non-Assets menu in the 3D Viewport.
Publishing as an asset lets you move them to custom menus, reuse across blend-files, or share.

### Tool Context

Tools have different settings than modifiers, so switch the Node Tree Sub-Type to Tool in the Geometry Node Editor header.
When Tool is active, the data-block menu shows only groups with Tool Usage enabled.

- New groups created in Tool mode auto-enable Tool Usage.
- Convert an existing modifier group: manually enable Tool Usage in the Sidebar (optionally disabling Modifier Usage) before switching to Tool mode. Configure Supported Modes & Object Types.

**Note:** Inspection features are unavailable in Tool context.

### Asset

Publish a tool as an asset: right-click the node group name and choose Mark as Asset.
The group appears in the Asset Browser's Unassigned catalog.
Move it to a catalog named after a menu to place it at that menu's end.
Save the blend-file as an asset bundle and copy into an asset library for multi-file reuse.
Share the bundle with others.

### Tool Settings

Accept user input via sockets on the Group Input node.
These appear in the Adjust Last Operation panel when the tool runs.

### Supported Modes & Object Types

Specify which modes and object types a node group supports using popover menus in the editor header.

**Important:** Mesh object shape keys are unsupported and removed if you run a node tool.

### Tool-specific Nodes

Exclusive to Tool context:

- 3D Cursor Node
- Mouse Position Node
- Viewport Transform Node
- Active Element Node
- Selection Node
- Set Selection Node
- Face Set Node
- Set Face Set Node

**Note:** Self Object returns the Active object inside a Tool node group.

### Non-supported Nodes

Modifier context only:

- Simulation Zone
- Viewer Node

## Align Euler to Vector Node

### Align Euler to Vector Node

Rotate an Euler rotation toward a given direction.

**Important:** This node is deprecated; use Align Rotation to Vector instead.

### Inputs

**Rotation**
Euler rotation to align.

**Important:** Provide a rotation input. Do not connect direction vectors like normals.

**Factor**
Rotation degree: zero disables; one aligns perfectly.

**Vector**
Direction vector for rotation.
Local space to the object being modified.
Zero vector: no rotation.

### Properties

**Axis**
Local object axis to rotate toward the vector.

**Pivot**
Rotation axis.

- **Auto:** Compute best angle automatically (minimize rotation).
- **X, Y, Z:** Rotate around specified axis.

### Outputs

**Rotation**
Rotated Euler output.

## Deprecated Nodes

### Deprecated Nodes

These nodes are slated for removal and should not be used in new work.

## Rotate Euler Node

### Rotate Euler Node

Rotate an Euler rotation.

**Important:** This node is deprecated; use Rotate Rotation instead.

### Inputs

**Rotation**
Euler rotation to rotate.

**Rotate By**
Rotation amount; only shown when Rotation Type is Euler.

**Axis**
Rotation axis; only shown when Rotation Type is Axis Angle.

**Angle**
Rotation angle; only shown when Rotation Type is Axis Angle.

### Properties

**Rotation Type**

- **Axis Angle:** Separate axis and angle inputs.
- **Euler:** Euler input.

**Space**

- **Object:** Rotate in the object's space.
- **Local:** Rotate in local space.

### Outputs

**Rotation**
Rotated Euler output.

## Accumulate Field Node

### Accumulate Field Node

Sum input values sequentially, ordered by geometry indices.
Output the running total at every element, not just the final sum.

### Inputs

**Value**
Values to accumulate.

**Warning:** Integer accumulation risks overflow (~2 billion max). Large values may wrap and become negative. See Wikipedia.

**Group Index**
Index for grouping values into separate sums.
Think of it as a bin for each value.
No effect as a single value.

### Properties

**Data Type**

- **Float:** Accumulate float field.
- **Integer:** Accumulate integer field.
- **Vector:** Accumulate vector field.
- **Transform:** Accumulate matrix field.

**Domain**
Attribute domain for accumulation and Value input evaluation.

### Output

**Leading**
Running total in the group, starting at the first value.

**Trailing**
Running total in the group, starting at zero.

**Total**
Group sum.

### Examples

### Table

| Value | Group Index | Leading | Trailing | Total |
| 1 | 7 | 1 | 0 | 6 |
| 3 | 7 | 4 | 1 | 6 |
| 2 | 7 | 6 | 4 | 6 |
| 1 | 3 | 1 | 0 | 3 |
| 0 | 3 | 1 | 1 | 3 |
| 2 | 3 | 3 | 1 | 3 |

Group index values do not matter; shared values group together.

### Stacking Boxes

Paired with Random Value Node for stacked, randomly scaled boxes.
Group Index unused: all boxes in one stack.

Three separate stacks using Group Index.

## Evaluate at Index Node

### Evaluate at Index Node

Access geometry element data by index; similar to Sample Index.
Differs: uses field context geometry (no geometry input).

Also similar to Evaluate on Domain—but specifies retrieval by index instead of auto domain interpolation.

### Inputs

**Index**
Element position in the domain to fetch (e.g. "the fourth face", "the first control point").

**Value**
Field source.

### Properties

**Domain**
Evaluation domain.
Useful for domain mismatch (e.g. pick vertex per face).

### Output

**Value**
Field value at the index.

## Evaluate on Domain Node

### Evaluate on Domain Node

Evaluate a field on a different attribute domain than the field context.
Example: use face index instead of face corner index for UV Map values.

**Note:** Not required for cross-domain retrieval (automatic).
Utility: control when interpolation occurs.
Normally, inputs interpolate to the current domain on output creation.

**Tip:** Prefer over Capture Attribute—uses a specific domain without geometry socket, enabling reusable groups.

**See also:** Method similar to Evaluate at Index.

### Inputs

**Value**
Field to evaluate.

### Properties

**Domain**
Evaluation domain.

### Output

**Value**
Input evaluated on the chosen domain, then interpolated back to the field context domain.

## Field Average Node

### Field Average Node

Compute mean and median of a field.

### Inputs

**Value**
Values for averaging.

**Group ID**
Index grouping values for separate averages.
Think of bins for each value.
No effect as single value.

### Properties

**Data Type**

- **Float:** Average float field.
- **Vector:** Average vector field.

**Domain**
Attribute domain for Value evaluation.

### Output

**Mean**
Sum of group values divided by group size.

**Median**
Middle value in each group when sorted.

## Field Min & Max Node

### Field Min & Max Node

Find minimum and maximum in a field.

### Inputs

**Value**
Values to analyze.

**Group ID**
Index grouping values for separate operations.
Think of bins for each value.
No effect as single value.

### Properties

**Data Type**

- **Float:** Analyze float field.
- **Integer:** Accumulate integer field.
- **Vector:** Analyze vector field.

**Domain**
Attribute domain for Value evaluation.

### Output

**Min**
Lowest value in each group.

**Max**
Highest value in each group.

## Field Variance Node

### Field Variance Node

Compute variance and standard deviation across a domain.
Measure how much a value spreads within geometry or groups.

Analyze spread of weights, positions, or custom attributes per Group ID.

### Inputs

**Value**
Field to analyze (float or vector per Data Type).
Vector fields compute variance per component (X, Y, Z).

**Group ID**
Index grouping values for separate analyses.
Think of bins for each value.
No effect as single value.

### Properties

**Data Type**

- **Float:** Analyze float field.
- **Vector:** Analyze vector field.

**Domain**
Attribute domain for Value evaluation.

### Output

**Standard Deviation**
Square root of variance; measure of spread.

**Variance**
Average squared deviation from mean.
Higher values: more variation.

## For Each Geometry Element Zone

### For Each Geometry Element Zone

Execute nodes per element of a geometry—each face, each instance, etc.

Ideal for generating large or complex per-element geometry.
Examples: unique tree per curve, unique building per face.

Less suited for small per-element work (e.g., individual hairs); slower than bulk operations.
Design node setups to avoid tiny sub-geometry iteration for performance.

The For Each Element zone.

### Inputs

**Geometry**
Elements to iterate.

**Selection**
Subset of Domain to process.

**Index**
Element position in source geometry.
Note: same index can repeat for multi-type iteration.

**Element**
Input split per element.
Single-element geometry for current iteration.
Unavailable for Face Corner (corners need faces).

**Note:** Splitting large geometries is inefficient.
Unused outputs skip computation, improving performance.

### Properties

**Domain**
Attribute domain for iteration.

**Inspection Index**
Element index for inspection tools (Viewer Node, socket inspection).

### Outputs

Main Geometry outputs create attributes on the first output.
Every single value inside the zone becomes an attribute at the current index.

Generated panel outputs (including default Geometry) join geometry from each element.
Non-geometry below a geometry output becomes an anonymous attribute on that joined geometry.
Input geometry attributes propagate to these outputs.

## Bit Math Node

### Bit Math Node

Bitwise operations on 32-bit integers.
Low-level data manipulation and logic.

### Inputs

**A**
First integer (all operations).

**B**
Second integer (And, Or, Exclusive Or).

**Shift**
Bit count for shift/rotate (Shift and Rotate).

### Properties

**Operation**

- **And:** Bits set in both A and B.
- **Or:** Bits set in A or B.
- **Exclusive Or:** Bits set in only one (XOR).
- **Not:** Invert A bits. Equivalent to -A - 1.
- **Shift:** Displace A bits by Shift amount. Positive: left; negative: right.
- **Rotate:** Revolve A bits by Shift. Positive: left; negative: right.

### Output

**Value**
Bitwise operation result.

## Boolean Math Node

### Boolean Math Node

Logical operations on pair of boolean inputs.

### Inputs

**Boolean**
Two boolean values to combine.

### Properties

**Mode**

- **And:** True when both true (AND).
- **Or:** True when at least one true (OR).
- **Not:** Opposite of input (NOT).
- **Not And:** True when at least one false (NAND).
- **Nor:** True when both false (NOR).
- **Equal:** True when equal ("exclusive nor", XNOR).
- **Not Equal:** True when different ("exclusive or", XOR).
- **Imply:** True unless first true and second false (IMPLY).
- **Subtract:** True when first true and second false ("not imply", NIMPLY).

### Output

**Boolean**
Logical result.

## Compare Node

### Compare Node

Determine if two inputs are similar using an operation.
Works on all generic types; vector modes offer complex comparisons for cleaner, more readable trees.

### Inputs

**A, B**
Inputs of selected type.

**C**
Threshold for Dot Product mode comparison.

**Epsilon**
Threshold for Equal and Not Equal.

### Properties

**Mode**

- **Element-Wise:** Compare each axis separately; true only all axes match.
- **Length:** Compare vector magnitudes.
- **Average:** Compare vector element average (implicit Float conversion).
- **Dot Product:** Compare dot product against C; single agreement metric.
- **Direction:** Compare angle with Angle input; vector length irrelevant.

**Operation**

- **Less Than:** First < second.
- **Less Than or Equal:** First <= second.
- **Greater Than:** First > second.
- **Greater Than or Equal:** First >= second.
- **Equal:** Difference < Epsilon.
- **Not Equal:** Difference > Epsilon.
- **Brighter:** First color brighter than second.
- **Darker:** First color darker than second.

### Output

**Result**
Boolean output.

### Examples

Direction mode compares sphere face normals to cube object location direction.
Faces less than 32.9 degrees apart are selected and deleted.

## Float To Integer Node

### Float To Integer Node

Convert float to integer via choice of method.

### Inputs

**Float**
Float value.

### Properties

**Rounding Mode**

- **Round:** Nearest integer (round up or down).
- **Floor:** Nearest integer less than Float (round down).
- **Ceiling:** Nearest integer greater than Float (round up).
- **Truncate:** Nearest integer toward zero. Positive: Floor; negative: Ceiling.

### Output

**Result**
Integer output.

### Examples

| Input | Round | Floor | Ceiling | Truncate |
| -69.6574 | -70 | -70 | -69 | -69 |
| -3.14159 | -3 | -4 | -3 | -3 |
| -1.5 | -2 | -2 | -1 | -1 |
| 1.5 | 2 | 1 | 2 | 1 |
| 3.14159 | 3 | 3 | 4 | 3 |
| 69.6574 | 70 | 69 | 70 | 69 |

## Hash Value Node

### Hash Value Node

Hash a value to an integer.

**Important:** Hashes are not unique identifiers (collisions possible).
Useful for stable randomness when White Noise lacks flexibility.

### Inputs

**Value**
Value per Data Type.

**Seed**
Integer modifying hash output.

### Properties

**Data Type**
Value input type: float, integer, vector, color, boolean, rotation, matrix, string.

### Output

**Hash**
Integer output.

## Integer Math Node

### Integer Math Node

Integer arithmetic.

### Inputs

**Value**
Integer input (count varies per operation).

### Properties

**Operation**

**Functions**

- **Add:** Sum.
- **Subtract:** Difference.
- **Multiply:** Product.
- **Divide:** First ÷ second.
- **Multiply Add:** (First × second) + Addend.
- **Absolute:** Magnitude; negatives become positive.
- **Negate:** Sign flip.
- **Power:** Base ^ Exponent.

**Comparison**

- **Minimum:** Smallest input.
- **Maximum:** Largest inputs.
- **Sign:** Extract sign (+1 positive, -1 negative, 0 zero).

**Rounding**

- **Divide Round:** Divide; round toward zero.
- **Divide Floor:** Divide; round toward negative infinity.
- **Divide Ceiling:** Divide; round toward positive infinity.
- **Floored Modulo:** Positive remainder.
- **Modulo:** Remainder.
- **Greatest Common Divisor:** Largest dividing both.
- **Least Common Multiple:** Smallest divisible by both.

### Output

**Value**
Integer output.

## Combine Matrix Node

### Combine Matrix Node

Construct a 4x4 matrix from individual values.

### Inputs

Split into column panels; each has four row inputs.

### Outputs

**Matrix**
Constructed matrix.

## Combine Transform Node

### Combine Transform Node

Pack translation, rotation, and scale vectors into a transformation matrix.

### Inputs

**Translation**
Translation vector.

**Rotation**
Rotation vector.

**Scale**
Scale vector.

### Outputs

**Transform**
Transformation matrix.

## Invert Matrix Node

### Invert Matrix Node

Compute matrix inverse.

### Inputs

**Matrix**
Matrix to invert.

### Outputs

**Matrix**
Inverse matrix.

**Invertible**
False if inversion fails (e.g., scale of zero).
See Invertible matrix.

**Important:** Non-invertible matrices return the identity matrix.

## Matrix Determinant Node

### Matrix Determinant Node

Compute determinant.

### Inputs

**Matrix**
Matrix to analyze.

### Outputs

**Determinant**
Determinant value.

## Matrix SVD Node

### Matrix SVD Node

Singular Value Decomposition of the input matrix (3D component).
Describes the matrix as: M = U * S * transpose(V)

Only the 3x3 affine part is used (translation column omitted).
Non-pure transformations decompose.

U and V are rotations/reflections (±1 scaling).
Positive determinant: pure rotations.
S describes scaling via diagonal vector.

### Inputs

**Matrix**
Matrix to decompose.

### Outputs

**U**
Left transform.

**S**
Singular values.

**V**
Right transform.

## Multiply Matrices Node

### Multiply Matrices Node

Matrix multiplication.

### Inputs

**Matrix**
First multiplicand.

**Matrix**
Second multiplicand.

### Outputs

**Matrix**
Product.

## Project Point Node

### Project Point Node

Apply a projection matrix to a point.
Transform Euclidean (X, Y, Z) to homogeneous (X, Y, Z, 1),
multiply the projection matrix, and convert back by dividing by W (perspective division).

### Inputs

**Vector**
Position to project.

**Transformation**
Projection matrix.

### Outputs

**Vector**
Projected position.

## Separate Matrix Node

Splits a 4×4 matrix into scalar values.

**Inputs**

Matrix
The matrix to decompose.

**Outputs**

Organized into panels by column; each panel has four scalar outputs (one per row).

## Separate Transform Node

Decomposes a Transformation Matrix into three components: translation, rotation, and scale vectors.

**Inputs**

Transform
The transformation matrix to decompose.

**Outputs**

Translation
The translation vector.

Rotation
The rotation vector.

Scale
The scale vector.

## Transform Direction Node

Applies a Transformation Matrix to a direction vector through multiplication.

**Inputs**

Direction
The vector to transform.

Transformation
The matrix to apply.

**Outputs**

Direction
The transformed vector.

## Transform Point Node

Applies a Transformation Matrix to a position, treating it as a point in space.

**Inputs**

Vector
The point's position to transform.

Transformation
The matrix to apply.

**Outputs**

Vector
The point after transformation.

## Transpose Matrix Node

Flips a matrix across its diagonal.

See also: Transpose on Wikipedia.

**Inputs**

Matrix
The matrix to flip.

**Outputs**

Matrix
The flipped matrix.

## Random Rotation Node

Generates random rotation values within a zenith (vertical) range.
Useful for randomizing object orientation in instances, particles, or geometry.

**Inputs**

Min Zenith
Lower angle limit for vertical rotation.

Max Zenith
Upper angle limit for vertical rotation.

ID
Seed ID for the random generator. Defaults to the ID Node's value—the `id` attribute if present, otherwise the index.

Tip: By default, each element gets a unique random rotation (keyed by ID).
To use the same rotation for the entire geometry, feed a constant value (e.g., Integer Node) to ID.

Seed
Field to vary the random sequence even when ID is unchanged.

**Outputs**

Rotation
The output rotation. Can be applied directly to instances or chained into other transformations.

## Random Value Node

Outputs white-noise values as Float, Integer, Vector, or Boolean fields.

**Inputs**

Min
Lower bound for sampling (Float, Integer, Vector only).

Max
Upper bound for sampling (Float, Integer, Vector only).

Probability
True probability for Boolean output (Boolean only).

ID
Seed ID. Defaults to the ID Node's value—the `id` attribute if present, otherwise the index.

Tip: By default, a unique value is generated per index.
To get a single value for the whole geometry, connect a constant (e.g., Integer Node) to ID.

Seed
Field to produce a different sequence even for identical ID inputs.

**Properties**

Data Type

Float: Outputs a Float field.

Integer: Outputs an Integer field.

Vector: Outputs a Vector field.

Boolean: Outputs a Boolean field.

**Outputs**

Value
Random field values.

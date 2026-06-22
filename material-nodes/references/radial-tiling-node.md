# Radial Tiling Node, Separate Cylindrical Node, Separate Spherical Node, Separate Xyz Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Radial Tiling Node; Separate Cylindrical Node; Separate Spherical Node; Separate XYZ Node; Vector Curves Node; Vector Math Node; Vector Rotate Node.

## Radial Tiling Node

The Radial Tiling Node splits a 2D Cartesian input coordinate system into as many radial segments as the Sides input asks for. Each segment carries its own affinely transformed segment coordinate system, which you can use to tile textures in a radially symmetric way.

Inputs:
Vector — the input system's vector to divide into radial segments.
Sides — how many radial segments to split the input coordinate system into; a non-integer value leaves one irregular segment that is smaller than the regular ones (illustrated at Sides 5.0, 5.25, 5.5, and 6.0).
Roundness — the roundness of the segment coordinate systems (illustrated at 0.0, 0.25, 0.5, and 1.0).

Properties:
Normalize — when enabled, the Segment Coordinates output's X-coordinates are remapped into a 0.0 to 1.0 range and a constant 1.0 is added to the Y-coordinates, making the output range non-negative.

Outputs:
Segment Coordinates — segment coordinates for mapping textures within each radial segment.
Segment ID — a unique ID per radial segment, starting at 0 and increasing by 1 counterclockwise for each segment.
Segment Width — the relative width of each radial segment; can scale textures to fit each one.
Segment Rotation — the counterclockwise rotation of each segment coordinate system; can align the rotation of each segment's textures.

Examples: the Segment Coordinates output tiles textures radially, demonstrated by radially tiling a heart texture. As the segment count rises, each segment's relative width shrinks, eventually making the textures overlap and clip — visible at Sides 6.5, where the non-integer value worsens the clipping because of the smaller irregular segment; feed the Segment Width output back in to scale the textures by each segment's relative width and avoid this (the example uses an arbitrary texture scale of 0.725, tweakable to resize the textures). By default the segment coordinate systems are rotated so their Y-axes meet the origin; the Segment Rotation output can instead align them along a global direction (the example uses an arbitrary texture rotation of -1.571, tweakable to rotate the textures). For textures spanning the whole UV space, seams along segment borders usually show even when the source texture is seamless; the Normalize option removes these seams by keeping the X-coordinates spanning the full 0 to 1 range, though it adds a distortion effect you may need extra nodes to counter if it's unwanted. For some textures a more rounded look near segment borders helps, achieved by raising the Roundness input.

The Radial Tiling Node splits a 2D Cartesian input coordinate system into as many radial segments as the Sides input asks for. Each segment carries its own affinely transformed segment coordinate system, which you can use to tile textures in a radially symmetric way.

Inputs:
Vector — the input system's vector to divide into radial segments.
Sides — how many radial segments to split the input coordinate system into; a non-integer value leaves one irregular segment that is smaller than the regular ones (illustrated at Sides 5.0, 5.25, 5.5, and 6.0).
Roundness — the roundness of the segment coordinate systems (illustrated at 0.0, 0.25, 0.5, and 1.0).

Properties:
Normalize — when enabled, the Segment Coordinates output's X-coordinates are remapped into a 0.0 to 1.0 range and a constant 1.0 is added to the Y-coordinates, making the output range non-negative.

Outputs:
Segment Coordinates — segment coordinates for mapping textures within each radial segment.
Segment ID — a unique ID per radial segment, starting at 0 and increasing by 1 counterclockwise for each segment.
Segment Width — the relative width of each radial segment; can scale textures to fit each one.
Segment Rotation — the counterclockwise rotation of each segment coordinate system; can align the rotation of each segment's textures.

Examples: the Segment Coordinates output tiles textures radially, demonstrated by radially tiling a heart texture. As the segment count rises, each segment's relative width shrinks, eventually making the textures overlap and clip — visible at Sides 6.5, where the non-integer value worsens the clipping because of the smaller irregular segment; feed the Segment Width output back in to scale the textures by each segment's relative width and avoid this (the example uses an arbitrary texture scale of 0.725, tweakable to resize the textures). By default the segment coordinate systems are rotated so their Y-axes meet the origin; the Segment Rotation output can instead align them along a global direction (the example uses an arbitrary texture rotation of -1.571, tweakable to rotate the textures). For textures spanning the whole UV space, seams along segment borders usually show even when the source texture is seamless; the Normalize option removes these seams by keeping the X-coordinates spanning the full 0 to 1 range, though it adds a distortion effect you may need extra nodes to counter if it's unwanted. For some textures a more rounded look near segment borders helps, achieved by raising the Roundness input.

### Radial Tiling Node

This node segments a 2D cartesian coordinate space into radial sections based on the Sides parameter. Each section contains its own affinely transformed local coordinate system for radially symmetric texture tiling.

### Inputs

Vector
The input vector representing the coordinate system to divide.

Sides
Count of radial sections. Non-integer values create an irregular final section smaller than regular ones.

| Sides: 5.0. | Sides: 5.25. | Sides: 5.5. | Sides: 6.0. |

Roundness
Curvature of the segment coordinate systems.

| Roundness: 0.0. | Roundness: 0.25. | Roundness: 0.5. | Roundness: 1.0. |

### Properties

Normalize
When enabled, X-coordinates of Segment Coordinates are remapped to a 0.0–1.0 range and a constant 1.0 is added to Y-coordinates, ensuring non-negative output ranges.

| Normalize: Disabled. | Normalize: Enabled. |

### Outputs

Segment Coordinates
Local coordinates for texture mapping within each section.

Segment ID
Distinct identifier for each section, starting at 0 and incrementing counterclockwise.

Segment Width
Relative size of each section. Useful for scaling textures to fit segment dimensions.

Segment Rotation
Counterclockwise rotation angle of each section coordinate system. Useful for aligning texture rotation per section.

### Examples

The Segment Coordinates output enables radially symmetric texture placement, shown by the radial heart texture tiling examples below.

| Sides: 5.0. | Sides: 6.5. |

Node tree for the shader above.

As section count increases, each section narrows, potentially causing texture overlap and clipping, evident in the Sides: 6.5 example. The non-integer value introduces additional clipping due to the smaller irregular section. To prevent this overlap, use the Segment Width output to scale textures proportionally to section size.

| Sides: 5.0. | Sides: 6.5. |

Node tree for the shader above. The value 0.725 is an arbitrarily chosen texture scaling value and can be adjusted to modify texture size.

By default, segment coordinate systems orient their Y-axes toward the center. Use the Segment Rotation output to align section coordinate systems with a global direction instead.

| Sides: 5.0. | Sides: 6.5. |

Node tree for the shader above. The value -1.571 is an arbitrarily chosen texture rotation value and can be adjusted to modify texture rotation.

When working with full-coverage textures, visible boundaries often appear along section borders despite seamless source textures. Enable Normalize to remove these boundaries by ensuring X-coordinates always span the full 0–1 range. This introduces distortion, which may need correction with additional nodes depending on artistic intent.

| Normalize: Disabled. | Normalize: Enabled. |

For certain textures, a softened appearance near section borders may be desirable, achievable by adjusting the Roundness input for segment coordinate systems.

| Roundness: 0.0. | Roundness: 0.25. | Roundness: 0.5. | Roundness: 1.0. |

## Separate Cylindrical Node

The Separate Cylindrical node turns a Cartesian vector (X, Y, Z) into cylindrical coordinates (R, Φ, Z), outputting each component — the inverse of the Combine Cylindrical node — useful for analyzing geometry or making procedural effects that depend on radial distance, angular position, or height, like spiral deformations, cylindrical gradients, or radial masks. Input: Vector (the Cartesian vector to convert). Outputs: R (the radial distance from the origin in the X-Y plane), Phi (the angular position around the Z axis), and Z (the vertical component, the input's Z coordinate directly).

Converts a vector from Cartesian (X, Y, Z) to cylindrical (R, Φ, Z) coordinates.
Inverse of Combine Cylindrical.

Useful for analyzing geometry or building procedural effects based on
radial distance, angular position, or height—spirals, cylindrical gradients, radial masks, etc.

**Inputs**

Vector
The Cartesian vector to convert.

**Outputs**

R
Radial distance in the X-Y plane.

Phi
Angular position around the Z axis.

Z
Vertical component (same as input Z).

### Separate Cylindrical Node

This node converts a vector from Cartesian coordinates (X, Y, Z) to cylindrical form (R, Φ, Z), outputting each independently. It provides the inverse of the Combine Cylindrical node.

This node suits analyzing geometry or building procedural elements based on radial distance, angular position, or altitude—for instance, spiral distortions, cylindrical gradations, or radial masks.

### Inputs

Vector
The input vector to decompose from Cartesian to cylindrical form.

### Outputs

R
Radial distance from the origin in the X-Y plane.

Phi
Angular position around the Z axis.

Z
Vertical component, directly corresponding to the input Z.

## Separate Spherical Node

The Separate Spherical node turns a Cartesian vector (X, Y, Z) into spherical coordinates (R, Φ, Θ), outputting each component — the inverse of the Combine Spherical node — where spherical coordinates describe a 3D position by radius, azimuth (horizontal angle), and polar (vertical) angle, useful for procedural effects with rotational symmetry, spherical gradients, or direction-based transforms. Input: Vector (the Cartesian vector to convert). Outputs: R (the radial distance from the origin), Phi (the azimuthal angle, horizontal rotation, around the Z axis, in radians), and Theta (the polar angle, vertical inclination, from the Z axis, in radians).

Converts a vector from Cartesian (X, Y, Z) to spherical (R, Φ, Θ) coordinates.
Inverse of Combine Spherical.

Spherical representation uses radius, azimuth (horizontal angle), and polar (vertical) angle—
useful for rotational symmetry, spherical gradients, and direction-based transformations.

**Inputs**

Vector
The Cartesian vector to convert.

**Outputs**

R
Radial distance from the origin.

Phi
Azimuthal angle (horizontal rotation) around the Z axis, in radians.

Theta
Polar angle (vertical inclination) from the Z axis, in radians.

### Separate Spherical Node

This node converts a vector from Cartesian coordinates (X, Y, Z) to spherical form (R, Φ, Θ), returning each component independently. It provides the inverse of the Combine Spherical node.

Spherical representation uses radius, azimuth (horizontal angle), and polar (vertical) angle to describe a 3D position. This form facilitates procedural patterns with rotational symmetry, spherical fades, or direction-dependent effects.

### Inputs

Vector
The input Cartesian vector for conversion to spherical form.

### Outputs

R
Distance from the origin.

Phi
Azimuthal angle (horizontal rotation) around the Z axis, in radians.

Theta
Polar angle (vertical inclination) from the Z axis, in radians.

## Separate XYZ Node

The Separate XYZ node breaks a vector into its individual components. Input: Vector (standard vector input). This node has no properties. Outputs: X, Y, Z.

Splits a vector into its X, Y, Z components.

**Inputs**

Vector
Standard vector input.

**Outputs**

X, Y, Z
Component values.

### Separate XYZ Node

This node decomposes a vector into its component parts.

### Input

Vector
Standard vector input.

### Properties

This node has no properties.

### Outputs

- X

- Y

- Z

## Vector Curves Node

The Vector Curves node maps an input vector's components through a curve — use it to slow things down or speed them up from the original scene. Inputs: Factor (in the shader context, an extra property controlling how much the node influences the output vector) and Vector (standard vector input). Properties: Channel (X, Y, Z) and Curve (see the Curve widget). Output: Vector (standard vector output).

Maps input vector components to a curve. Use this curve node to slow things down or speed them up from the original scene.

Inputs:
- Factor (shader context only): Modulates influence strength on output
- Vector: Standard vector input

Properties:
Channel: X, Y, Z
Curve: See Curve widget for control details

Outputs:
- Vector: Standard vector output

### Vector Curves Node

This node applies a curve mapping to vector values, permitting fine-tuning of magnitude changes.

Apply this curve operation to decelerate or accelerate changes relative to source values.

### Inputs

In the shader context the node also has an additional Factor property.

Factor
Determines the intensity of the node's effect on the final output.

Vector
Standard vector input.

### Properties

Channel
X, Y, Z

Curve
For the curve controls see: Curve widget.

### Outputs

Vector
Standard vector output.

## Vector Math Node

The Vector Math node applies the chosen math operation to the input vectors. Inputs (dynamic — some appear only for certain operations, e.g. Scale only for the Scale operator): Vector A, Vector B, and Scale s. Properties: Operation — Add (A + B), Subtract (A - B), Multiply (the entrywise product of A and B), Divide (the entrywise division of A by B, division by zero giving zero), Multiply Add (the entrywise A × B + C), Cross Product (the cross product of A and B), Project (the projection of A onto B), Reflect (the reflection of A about the normal B, which needn't be normalized), Refract (for incident vector A, surface normal B, and an index-of-refraction ratio, the refraction vector R), Faceforward (orient A to point away from a surface B by its normal C, computing (dot(B, C) < 0) ? A : -A), Dot Product (Ax·Bx + Ay·By + Az·Bz), Distance (between A and B), Length (the length of A, √(Ax² + Ay² + Az²)), Scale (A times the scalar Scale), Normalize (A scaled to length 1 in the same direction, or (0, 0, 0) if A is (0, 0, 0)), Absolute (the entrywise absolute value of A), Power (the entrywise Base to the Exponent), Sign (1.0 for positives, -1.0 for negatives, 0.0 for zero), Minimum and Maximum (the entrywise min/max of A and B), Round (entrywise to the nearest integer, up at 0.5), Floor (entrywise down), Ceil (entrywise up), Fraction (the entrywise fractional part), Modulo (the entrywise modulo of A by B), Wrap (entrywise, a value between Min and Max from the absolute difference between the input and the nearest integer multiple of Max below it), Snap (A down to the largest integer multiple of B at most A), Sine, Cosine, and Tangent (entrywise). Outputs (dynamic — a vector or a scalar by operator, e.g. Length is scalar, Add is vector): Vector (the output vector) and Value (the output value).

Performs selected mathematical operations on two input vectors to produce the computed result.

Inputs (dynamic, available based on operation):
- Vector: A = (Ax, Ay, Az)
- Vector: B = (Bx, By, Bz)
- Scale: s

Operations:

Add: Sum of A and B.
(Ax+Bx, Ay+By, Az+Bz)

Subtract: Difference of A and B.
(Ax-Bx, Ay-By, Az-Bz)

Multiply: Element-wise product of A and B.
(Ax·Bx, Ay·By, Az·Bz)

Divide: Element-wise division of A by B. Division by zero = zero.
(Ax/Bx, Ay/By, Az/Bz)

Multiply Add: Element-wise combination of multiply and addition.
A × B + C

Cross Product: Cross product of A and B.
(Ay·Bz - Az·By, Az·Bx - Ax·Bz, Ax·By - Ay·Bx)

Project: Projection of A onto B

Reflect: A's reflection relative to normal B (B normalization not required)

Refract: Refraction vector R given incident vector A, surface normal B, and IOR ratio

Faceforward: Orients vector A to point away from surface B with normal C.
Computes (dot(B, C) < 0) ? A : -A

Dot Product: Dot product of A and B.
Ax·Bx + Ay·By + Az·Bz

Distance: Distance between A and B

Length: Magnitude of A.
√(Ax² + Ay² + Az²)

Scale: Multiply A by scalar input.
(s·Ax, s·Ay, s·Az)

Normalize: Unit vector in direction of A, with length 1. If A is (0, 0, 0), output is (0, 0, 0)

Absolute: Element-wise absolute value of A

Power: Base raised to Exponent power, element-wise

Sign: Extracts sign: positive → 1.0, negative → -1.0, zero → 0.0

Minimum: Element-wise minimum of A and B

Maximum: Element-wise maximum of A and B

Round: Rounds element-wise to nearest integer; 0.5 fractions round upward

Floor: Rounds element-wise down to nearest integer

Ceil: Rounds element-wise up to nearest integer

Fraction: Returns fractional part, element-wise

Modulo: Element-wise modulo of A by B

Wrap: Element-wise output between Min and Max based on absolute difference to nearest multiple of Max less than value

Snap: Rounds A to largest integer multiple of B that is ≤ A

Sine: Element-wise Sine of A

Cosine: Element-wise Cosine of A

Tangent: Element-wise Tangent of A

Properties:
Operation: The vector math operator to apply

Outputs (dynamic, vector or scalar depending on operator):
- Vector: Output vector
- Value: Output scalar

### Vector Math Node

This node evaluates a selected mathematical operation on the input vectors.

### Inputs

Node inputs vary depending on the selected operation; not all appear with every mode. The Scale input, for example, is visible only when the Scale operator is active.

Vector
Input vector \(A = \begin{pmatrix} A_x \\ A_y \\ A_z \end{pmatrix}\).

Vector
Input vector \(B = \begin{pmatrix} B_x \\ B_y \\ B_z \end{pmatrix}\).

Scale
Input Scale \(s\).

### Properties

Operation
The vector math operator to be applied on the input vectors.

Add :

The sum of A and B.
\(\begin{pmatrix} A_x + B_x \\ A_y + B_y \\ A_z + B_z \end{pmatrix}\)

Subtract :

The difference between A and B.
\(\begin{pmatrix} A_x - B_x \\ A_y - B_y \\ A_z - B_z \end{pmatrix}\)

Multiply :

The entrywise product of A and B.
\(\begin{pmatrix} A_x \cdot B_x \\ A_y \cdot B_y \\ A_z \cdot B_z \end{pmatrix}\)

Divide :

The entrywise division of A by B. Division by zero results in zero.
\(\begin{pmatrix} A_x / B_x \\ A_y / B_y \\ A_z / B_z \end{pmatrix}\)

Multiply Add :

The entrywise combination of the multiply and addition operations.
\(A × B + C\)

Cross Product :

The cross product of A and B.
\(\begin{pmatrix} A_y \cdot B_z - A_z \cdot B_y \\ A_z \cdot B_x - A_x \cdot B_z \\ A_x \cdot B_y - A_y \cdot B_x \end{pmatrix}\)

Project :

The projection of A onto B.

Reflect :

The reflection of A around the normal B. B need not be normalized.

Refract :

For a given incident vector A, surface normal B and ratio of indices of refraction (IOR), refract outputs the refraction vector R.

Faceforward :

Orients a vector A to point away from a surface B as defined by its normal C. Computes \((dot(B, C) < 0) ? A : -A\).

Dot Product :

The dot product of A and B.
\(A_x \cdot B_x + A_y \cdot B_y + A_z \cdot B_z\)

Distance :

The distance between A and B.

Length :

The magnitude of A.
\(\sqrt{A_x^2 + A_y^2 + A_z^2}\)

Scale :

The result of multiplying A by the scalar input Scale.
\(\begin{pmatrix} s \cdot A_x \\ s \cdot A_y \\ s \cdot A_z \end{pmatrix}\)

Normalize :

The result of normalizing A. The resulting vector points in the same direction as A with a magnitude of 1. If A is (0, 0, 0), the result is (0, 0, 0).

Absolute :

The entrywise absolute value of A.

Power :

The entrywise power operation where the Base raised to the power of Exponent.

Sign :

Extracts the sign. Positive values output 1.0, negative values output -1.0, and 0.0 outputs 0.0.

Minimum :

The entrywise minimum of A and B.

Maximum :

The entrywise maximum of A and B.

Round :

Rounds each component to the nearest integer, rounding upward when the fractional part is 0.5.

Floor :

Rounds each component downward to the nearest integer.

Ceil :

Rounds each component upward to the nearest integer.

Fraction :

Returns the fractional component of each value.

Modulo :

The entrywise remainder of A divided by B.

Wrap :

The entrywise output of a value between Min and Max based on the absolute difference between the input value and the nearest integer multiple of Max less than the value.

Snap :

The result of rounding A to the largest integer multiple of B less than or equal A.

Sine :

The entrywise sine of A.

Cosine :

The entrywise cosine of A.

Tangent :

The entrywise tangent of A.

### Outputs

The output of the node is dynamic. It is either a vector or a scalar depending on the operator. For instance, the Length operator has a scalar output while the Add operator has a vector output.

Vector
Output vector.

Value
Output value.

## Vector Rotate Node

The Vector Rotate node rotates a vector around a pivot point (Center). Inputs: Vector (the vector to rotate), Center (the point to rotate around), Axis (the axis to rotate around), Angle (the rotation amount), and Rotation (when Type is Euler, rotate by these angles around X, then Y, then Z). Properties: Type — X/Y/Z Axis (rotate around that axis by the Angle), Axis Angle (rotate around an arbitrary axis from the Axis input by the Angle), or Euler (rotate about the Center point by the per-axis Rotation vector) — plus Invert (invert the rotation angle). Output: Vector (the rotated vector).

Applies rotational transformation to a vector around a pivot (Center) using the chosen rotation method.

Inputs:
- Vector: The vector undergoing rotation
- Center: Pivot location for rotation
- Axis: Rotation axis direction
- Angle: Magnitude of rotation
- Rotation: When Type is Euler, rotation angles around X then Y then Z axes

Properties:
Type — Rotation method:

X/Y/Z Axis: Rotate around the defined axis by the amount specified in Angle

Axis Angle: Rotate around an arbitrary axis (from Axis input) by the amount in Angle

Euler: Rotate about center point (from Center input) by angles in Rotation input vector (applied in X, Y, Z order)

Invert: Inverts the rotation angle

Outputs:
- Vector: The rotated vector

### Vector Rotate Node

This node allows rotation of a vector about a pivot location (Center).

### Inputs

Vector
Vector to be rotated.

Center
Point to pivot around.

Axis
Rotation axis.

Angle
Rotation magnitude.

Rotation
When Type is set to Euler, rotate the input vector by these angles around the X, Y, then Z axes in that order.

### Properties

Type
The angle input type.

X/Y/Z Axis :

Rotates the vector around the defined axis by the amount specified in Angle.

Axis Angle :

Rotates the vector around an arbitrary axis specified by the Axis input. The rotation magnitude is defined by Angle.

Euler :

Rotates the vector about a center point specified by the Center input. Each axis rotation is defined by the Rotation input vector.

Invert
Inverts the rotation magnitude.

### Outputs

Vector
The rotated vector.

### Examples

Vector Rotate node example.

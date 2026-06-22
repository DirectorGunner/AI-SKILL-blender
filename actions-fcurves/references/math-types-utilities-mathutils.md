# Math Types Utilities Mathutils (part 1)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Math Types & Utilities (mathutils)

This module opens up a range of mathematical operations.

Note

Classes, methods and attributes that accept vectors also accept other numeric sequences,
such as tuples, lists.

The mathutils module provides the following classes:

- Color,

- Euler,

- Matrix,

- Quaternion,

- Vector,

`\text
import mathutils
from math import radians

vec = mathutils.Vector((1.0, 2.0, 3.0))

mat_rot = mathutils.Matrix.Rotation(radians(90.0), 4, 'X')
mat_trans = mathutils.Matrix.Translation(vec)

mat = mat_trans @ mat_rot
mat.invert()

mat3 = mat.to_3x3()
quat1 = mat.to_quaternion()
quat2 = mat3.to_quaternion()

quat_diff = quat1.rotation_difference(quat2)

print(quat_diff.angle)
`

class mathutils. Color ( rgb = (0.0, 0.0, 0.0) , / )

A handle onto Blender's Colors.

The colors that Blender APIs return mostly sit in scene linear color space, per the OpenColorIO configuration. The one big exception is the interface theming colors, which live in sRGB color space.

Parameters :

rgb ( Sequence [ float ] ) – (red, green, blue) color values where (0, 0, 0) is black & (1, 1, 1) is white.

`\text
import mathutils

### Color values are represented as RGB values from 0 - 1, this is blue.
col = mathutils.Color((0.0, 0.0, 1.0))

### As well as r/g/b attribute access you can adjust them by h/s/v.
col.s *= 0.5

### You can access its components by attribute or index.
print("Color R:", col.r)
print("Color G:", col[1])
print("Color B:", col[-1])
print("Color HSV: {:.2f}, {:.2f}, {:.2f}".format(*col))

### Components of an existing color can be set.
col[:] = 0.0, 0.5, 1.0

### Components of an existing color can use slice notation to get a tuple.
print("Values: {:f}, {:f}, {:f}".format(*col))

### Colors can be added and subtracted.
col += mathutils.Color((0.25, 0.0, 0.0))

### Color can be multiplied, in this example color is scaled to 0-255
### can printed as integers.
print("Color: {:d}, {:d}, {:d}".format(*(int(c) for c in (col * 255.0))))

### This example prints the color as hexadecimal.
print("Hexadecimal: {:02x}{:02x}{:02x}".format(int(col.r * 255), int(col.g * 255), int(col.b * 255)))

### Direct buffer access is supported.
print(memoryview(col).tobytes())
`

copy ( )

Returns a copy of this color.

Returns :

A copy of the color.

Return type :

Color

Note

reach for this when you need a standalone copy of a wrapped color that no longer points back at the source.

freeze ( )

Lock this object so it can no longer change.

Once locked, it becomes hashable and usable as a dictionary or set member.

Returns :

An instance of this object.

Return type :

Self

from_aces_to_scene_linear ( )

Convert from ACES2065-1 linear to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

from_acescg_to_scene_linear ( )

Convert from ACEScg linear to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

from_rec2020_linear_to_scene_linear ( )

Convert from Rec.2020 linear color space to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

from_rec709_linear_to_scene_linear ( )

Convert from Rec.709 linear color space to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

from_scene_linear_to_aces ( )

Convert from scene linear to ACES2065-1 linear color space.

Returns :

A color in ACES2065-1 linear color space.

Return type :

Color

from_scene_linear_to_acescg ( )

Convert from scene linear to ACEScg linear color space.

Returns :

A color in ACEScg linear color space.

Return type :

Color

from_scene_linear_to_rec2020_linear ( )

Convert from scene linear to Rec.2020 linear color space.

Returns :

A color in Rec.2020 linear color space.

Return type :

Color

from_scene_linear_to_rec709_linear ( )

Convert from scene linear to Rec.709 linear color space.

Returns :

A color in Rec.709 linear color space.

Return type :

Color

from_scene_linear_to_srgb ( )

Convert from scene linear to sRGB color space.

Returns :

A color in sRGB color space.

Return type :

Color

from_scene_linear_to_xyz_d65 ( )

Convert from scene linear to CIE XYZ (Illuminant D65) color space.

Returns :

A color in XYZ color space.

Return type :

Color

from_srgb_to_scene_linear ( )

Convert from sRGB to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

from_xyz_d65_to_scene_linear ( )

Convert from CIE XYZ (Illuminant D65) to scene linear color space.

Returns :

A color in scene linear color space.

Return type :

Color

b

Blue color channel.

Type :

float

g

Green color channel.

Type :

float

h

HSV Hue component in [0, 1].

Type :

float

hsv

HSV Values in [0, 1].

Type :

tuple[float, float, float]

is_frozen

Reads True once the object has been locked (read-only).

Type :

bool

is_valid

Reads True while the data's owner remains valid.

Type :

bool

is_wrapped

Reads True when the object is a wrapper around external data (read-only).

Type :

bool

owner

Whatever item this wraps, or None (read-only).

Type :

Any

r

Red color channel.

Type :

float

s

HSV Saturation component in [0, 1].

Type :

float

v

HSV Value component in [0, 1].

Type :

float

class mathutils. Euler ( angles = (0.0, 0.0, 0.0) , order = 'XYZ' , / )

A handle onto Blender's Eulers.

See also

Euler angles on Wikipedia.

Parameters :

- angles ( Sequence [ float ] ) – (X, Y, Z) angles in radians.

- order ( Literal [ 'XYZ' , 'XZY' , 'YXZ' , 'YZX' , 'ZXY' , 'ZYX' ] ) – Euler rotation order.

`\text
import mathutils
import math

### Create a new euler with default axis rotation order.
eul = mathutils.Euler((0.0, math.radians(45.0), 0.0), 'XYZ')

### Rotate the euler.
eul.rotate_axis('Z', math.radians(10.0))

### You can access its components by attribute or index.
print("Euler X", eul.x)
print("Euler Y", eul[1])
print("Euler Z", eul[-1])

### Components of an existing euler can be set.
eul[:] = 1.0, 2.0, 3.0

### Components of an existing euler can use slice notation to get a tuple.
print("Values: {:f}, {:f}, {:f}".format(*eul))

### The order can be set at any time too.
eul.order = 'ZYX'

### Eulers can be used to rotate vectors.
vec = mathutils.Vector((0.0, 0.0, 1.0))
vec.rotate(eul)

### Often its useful to convert the euler into a matrix so it can be used as
### transformations with more flexibility.
mat_rot = eul.to_matrix()
mat_loc = mathutils.Matrix.Translation((2.0, 3.0, 4.0))
mat = mat_loc @ mat_rot.to_4x4()

### Direct buffer access is supported.
print(memoryview(eul).tobytes())
`

copy ( )

Returns a copy of this euler.

Returns :

A copy of the euler.

Return type :

Euler

Note

reach for this when you need a standalone copy of a wrapped euler that no longer points back at the source.

freeze ( )

Lock this object so it can no longer change.

Once locked, it becomes hashable and usable as a dictionary or set member.

Returns :

An instance of this object.

Return type :

Self

make_compatible ( other , / )

Bring this euler into line with another so that interpolating across the two behaves the way you'd expect.

Parameters :

other (Euler) – Other euler rotation.

Note

the rotation order is not taken into account for this function.

rotate ( other , / )

Rotate the euler by some other mathutils value.

Parameters :

other (Euler | Quaternion | Matrix) – rotation component of mathutils value

rotate_axis ( axis , angle , / )

Turn the euler by a set amount, then wrap the outcome so it stays a single distinct euler rotation (no 720 degree pitches).

Parameters :

- axis ( Literal [ 'X' , 'Y' , 'Z' ] ) – An axis string.

- angle ( float ) – angle in radians.

to_matrix ( )

Give the euler back as a matrix.

Returns :

A 3x3 rotation matrix representation of the euler.

Return type :

Matrix

to_quaternion ( )

Give the euler back as a quaternion.

Returns :

Quaternion representation of the euler.

Return type :

Quaternion

zero ( )

Reset every value to zero.

is_frozen

Reads True once the object has been locked (read-only).

Type :

bool

is_valid

Reads True while the data's owner remains valid.

Type :

bool

is_wrapped

Reads True when the object is a wrapper around external data (read-only).

Type :

bool

order

Euler rotation order.

Type :

Literal[‘XYZ’, ‘XZY’, ‘YXZ’, ‘YZX’, ‘ZXY’, ‘ZYX’]

owner

Whatever item this wraps, or None (read-only).

Type :

Any

x

Euler axis angle in radians.

Type :

float

y

Euler axis angle in radians.

Type :

float

z

Euler axis angle in radians.

Type :

float

class mathutils. Matrix ( rows = Matrix.Identity(4) , / )

This object gives access to Matrices in Blender, covering both square and rectangular matrices ranging from 2x2 through 4x4.

Parameters :

rows ( Sequence [ Sequence [ float ] ] ) – Sequence of rows.

`\text
import mathutils
import math

### Create a location matrix.
mat_loc = mathutils.Matrix.Translation((2.0, 3.0, 4.0))

### Create an identity matrix.
mat_sca = mathutils.Matrix.Scale(0.5, 4, (0.0, 0.0, 1.0))

### Create a rotation matrix.
mat_rot = mathutils.Matrix.Rotation(math.radians(45.0), 4, 'X')

### Combine transformations.
mat_out = mat_loc @ mat_rot @ mat_sca
print(mat_out)

### Extract components back out of the matrix as two vectors and a quaternion.
loc, rot, sca = mat_out.decompose()
print(loc, rot, sca)

### Recombine extracted components.
mat_out2 = mathutils.Matrix.LocRotScale(loc, rot, sca)
print(mat_out2)

### It can also be useful to access components of a matrix directly.
mat = mathutils.Matrix()
mat[0][0], mat[1][0], mat[2][0] = 0.0, 1.0, 2.0

mat[0][0:3] = 0.0, 1.0, 2.0

### Each item in a matrix is a vector so vector utility functions can be used.
mat[0].xyz = 0.0, 1.0, 2.0

### Direct buffer access is supported.
print(memoryview(mat).tobytes())
`

classmethod Diagonal ( vector , / )

Build a diagonal (scaling) matrix from the vector's values.

Parameters :

vector ( Sequence [ float ] ) – The vector of values for the diagonal.

Returns :

A diagonal matrix.

Return type :

Matrix

classmethod Identity ( size , / )

Build an identity matrix.

Parameters :

size ( int ) – The size of the identity matrix to construct [2, 4].

Returns :

A new identity matrix.

Return type :

Matrix

classmethod LocRotScale ( location , rotation , scale , / )

Build one matrix that folds together translation, rotation, and scale, serving as the reverse of the decompose() method.

Any input can be swapped out for None when it isn't required.

Parameters :

- location ( Sequence [ float ] | None ) – The translation component.

- rotation (Matrix | Quaternion | Euler | None) – The rotation component as a 3x3 matrix, quaternion, euler or None for no rotation.

- scale ( Sequence [ float ] | None ) – The scale component.

Returns :

Combined transformation as a 4x4 matrix.

Return type :

Matrix

`\text
### Compute local object transformation matrix:

import bpy
import mathutils

obj = bpy.context.object
if obj.rotation_mode == 'QUATERNION':
matrix = mathutils.Matrix.LocRotScale(obj.location, obj.rotation_quaternion, obj.scale)
else:
matrix = mathutils.Matrix.LocRotScale(obj.location, obj.rotation_euler, obj.scale)
`

classmethod OrthoProjection ( axis , size , / )

Build a matrix that stands in for an orthographic projection.

Parameters :

- axis ( Literal [ 'X' , 'Y' , 'XY' , 'XZ' , 'YZ' ] | Sequence [ float ] ) – An axis string,
where a single axis is for a 2D matrix.
Or a vector for an arbitrary axis

- size ( int ) – The size of the projection matrix to construct [2, 4].

Returns :

A new projection matrix.

Return type :

Matrix

classmethod Rotation ( angle , size , axis , / )

Build a matrix that stands in for a rotation.

Parameters :

- angle ( float ) – The angle of rotation desired, in radians.

- size ( int ) – The size of the rotation matrix to construct [2, 4].

- axis ( Literal [ 'X' , 'Y' , 'Z' ] | Sequence [ float ] ) – an axis string or a 3D Vector Object
(optional when size is 2).

Returns :

A new rotation matrix.

Return type :

Matrix

classmethod Scale ( factor , size , axis , / )

Build a matrix that stands in for a scaling.

Parameters :

- factor ( float ) – The factor of scaling to apply.

- size ( int ) – The size of the scale matrix to construct [2, 4].

- axis ( Sequence [ float ] ) – Direction to influence scale. (optional).

Returns :

A new scale matrix.

Return type :

Matrix

classmethod Shear ( plane , size , factor , / )

Build a matrix that stands in for a shear transformation.

Parameters :

- plane ( Literal [ 'X' , 'Y' , 'XY' , 'XZ' , 'YZ' ] ) – An axis string,
where a single axis is for a 2D matrix only.

- size ( int ) – The size of the shear matrix to construct [2, 4].

- factor ( float | Sequence [ float ] ) – The factor of shear to apply. For a 2 size matrix use a single float. For a 3 or 4 size matrix pass a pair of floats corresponding with the plane axis.

Returns :

A new shear matrix.

Return type :

Matrix

classmethod Translation ( vector , / )

Build a matrix that stands in for a translation.

Parameters :

vector ( Sequence [ float ] ) – The translation vector.

Returns :

An identity matrix with a translation.

Return type :

Matrix

adjugate ( )

Replace the matrix with its own adjugate.

Raises :

ValueError – if the matrix cannot be adjugated.

See also

Adjugate matrix on Wikipedia.

adjugated ( )

Give back an adjugated copy of the matrix.

Returns :

the adjugated matrix.

Return type :

Matrix

Raises :

ValueError – if the matrix cannot be adjugated

copy ( )

Returns a copy of this matrix.

Returns :

A copy of the matrix.

Return type :

Matrix

decompose ( )

Pull the translation, rotation, and scale back out of this 4x4 matrix.

Returns :

Tuple of translation, rotation, and scale.

Return type :

tuple[Vector, Quaternion, Vector]

determinant ( )

Give back the matrix determinant.

Returns :

Return the determinant of a matrix.

Return type :

float

See also

Determinant on Wikipedia.

freeze ( )

Lock this object so it can no longer change.

Once locked, it becomes hashable and usable as a dictionary or set member.

Returns :

An instance of this object.

Return type :

Self

identity ( )

Turn the matrix into the identity matrix.

Note

An object with a location and rotation of zero, and a scale of one
will have an identity matrix.

See also

Identity matrix on Wikipedia.

invert ( fallback = None , / )

Replace the matrix with its inverse.

Parameters :

fallback (Matrix | None) – Set the matrix to this value when the inverse cannot be calculated
(instead of raising a ValueError exception).

See also

Inverse matrix on Wikipedia.

invert_safe ( )

Replace the matrix with its inverse, never raising an error. When the matrix is degenerate (say a zero scale on one axis), a small epsilon is added to its diagonal to make it invertible. Should the adjusted matrix still be degenerate, the identity matrix is used instead.

See also

Inverse Matrix on Wikipedia.

inverted ( fallback = None , / )

Give back an inverted copy of the matrix.

Parameters :

fallback ( Any ) – return this when the inverse can't be calculated
(instead of raising a ValueError ).

Returns :

The inverted matrix or fallback when given.

Return type :

Matrix | Any

inverted_safe ( )

Give back an inverted copy of the matrix, never raising an error. When the matrix is degenerate (say a zero scale on one axis), a small epsilon is added to its diagonal to make it invertible. Should the adjusted matrix still be degenerate, the identity matrix is returned instead.

Returns :

the inverted matrix.

Return type :

Matrix

lerp ( other , factor , / )

Give back the interpolation between two matrices. This relies on polar decomposition, per "Matrix Animation and Polar Decomposition", Shoemake and Duff, 1992.

Parameters :

- other (Matrix) – value to interpolate with.

- factor ( float ) – The interpolation value in [0.0, 1.0].

Returns :

The interpolated matrix.

Return type :

Matrix

normalize ( )

Normalize each of the matrix columns (3x3 and 4x4 only).

Note

for 4x4 matrices, the 4th column (translation) is left untouched.

normalized ( )

Give back a column-normalized matrix (3x3 and 4x4 only).

Returns :

a column normalized matrix

Return type :

Matrix

Note

for 4x4 matrices, the 4th column (translation) is left untouched.

resize_4x4 ( )

Resize the matrix to 4x4.

rotate ( other , / )

Rotate the matrix by some other mathutils value.

Note

The matrix must be 3x3.

Note

If any of the columns are not unit length this may not have desired results.

Parameters :

other (Euler | Quaternion | Matrix) – rotation component of mathutils value

to_2x2 ( )

Give back a 2x2 copy of this matrix.

Returns :

a new matrix.

Return type :

Matrix

to_3x3 ( )

Give back a 3x3 copy of this matrix.

Returns :

a new matrix.

Return type :

Matrix

to_4x4 ( )

Give back a 4x4 copy of this matrix.

Returns :

a new matrix.

Return type :

Matrix

to_euler ( order = 'XYZ' , euler_compat = None , / )

Give back an Euler form of the rotation matrix (3x3 or 4x4 matrix only).

Parameters :

- order ( Literal [ 'XYZ' , 'XZY' , 'YXZ' , 'YZX' , 'ZXY' , 'ZYX' ] ) – A rotation order string.

- euler_compat (Euler | None) – Optional euler argument the new euler will be made
compatible with (no axis flipping between them).
Useful for converting a series of matrices to animation curves.

Returns :

Euler representation of the matrix.

Return type :

Euler

to_quaternion ( )

Give back a quaternion form of the rotation matrix.

Returns :

Quaternion representation of the rotation matrix.

Return type :

Quaternion

to_scale ( )

Give back the scale portion of a 3x3 or 4x4 matrix.

Returns :

Return the scale of a matrix.

Return type :

Vector

Note

This method does not return a negative scale on any axis because it is not possible to obtain this data from the matrix alone.

to_translation ( )

Give back the translation portion of a 4x4 matrix.

Returns :

Return the translation of a matrix.

Return type :

Vector

transpose ( )

Replace the matrix with its transpose.

See also

Transpose on Wikipedia.

transposed ( )

Give back a fresh, transposed matrix.

Returns :

a transposed matrix

Return type :

Matrix

zero ( )

Set every matrix value to zero.

col

Access the matrix by columns (read-only).

Type :

MatrixAccess

is_frozen

Reads True once the object has been locked (read-only).

Type :

bool

is_identity

True if this is an identity matrix (read-only).

Type :

bool

is_negative

True if this matrix results in a negative scale, 3x3 and 4x4 only, (read-only).

Type :

bool

is_orthogonal

True if this matrix is orthogonal, 3x3 and 4x4 only, (read-only).

Type :

bool

is_orthogonal_axis_vectors

True if this matrix has orthogonal axis vectors, 3x3 and 4x4 only, (read-only).

Type :

bool

is_valid

Reads True while the data's owner remains valid.

Type :

bool

is_wrapped

Reads True when the object is a wrapper around external data (read-only).

Type :

bool

median_scale

The average scale applied to each axis (read-only).

Type :

float

owner

Whatever item this wraps, or None (read-only).

Type :

Any

row

Access the matrix by rows (default), (read-only).

Type :

MatrixAccess

translation

The translation component of the matrix.

Type :

Vector

class mathutils. MatrixAccess

An indexable type for accessing matrix rows or columns as Vector types.

class mathutils. Quaternion ( seq = (1.0, 0.0, 0.0, 0.0) , angle = 0.0 , / )

A handle onto Blender's Quaternions.

Parameters :

- seq ( Sequence [ float ] ) – A (w, x, y, z) quaternion, a 3D exponential map vector,
or a 3D axis vector (when angle is also provided).

- angle ( float ) – rotation angle, in radians

The constructor takes arguments in various forms:

(), no args
Create an identity quaternion

( wxyz )
Create a quaternion from a (w, x, y, z) vector.

( exponential_map )
Create a quaternion from a 3d exponential map vector.

See also

to_exponential_map()

( axis, angle )
Create a quaternion representing a rotation of angle radians over axis .

See also

to_axis_angle()

`\text
import mathutils
import math

### A new rotation 90 degrees about the Y axis.
quat_a = mathutils.Quaternion((0.7071068, 0.0, 0.7071068, 0.0))

### Passing values to Quaternion's directly can be confusing so axis, angle
### is supported for initializing too.
quat_b = mathutils.Quaternion((0.0, 1.0, 0.0), math.radians(90.0))

print("Check quaternions match", quat_a == quat_b)

### Like matrices, quaternions can be multiplied to accumulate rotational values.
quat_a = mathutils.Quaternion((0.0, 1.0, 0.0), math.radians(90.0))
quat_b = mathutils.Quaternion((0.0, 0.0, 1.0), math.radians(45.0))
quat_out = quat_a @ quat_b

### Print the quaternion, euler degrees for mere mortals and (axis, angle).
print("Final Rotation:")
print(quat_out)
print("{:.2f}, {:.2f}, {:.2f}".format(*(math.degrees(a) for a in quat_out.to_euler())))
print("({:.2f}, {:.2f}, {:.2f}), {:.2f}".format(*quat_out.axis, math.degrees(quat_out.angle)))

### Multiple rotations can be interpolated using the exponential map.
quat_c = mathutils.Quaternion((1.0, 0.0, 0.0), math.radians(15.0))
exp_avg = (quat_a.to_exponential_map() +
quat_b.to_exponential_map() +
quat_c.to_exponential_map()) / 3.0
quat_avg = mathutils.Quaternion(exp_avg)
print("Average rotation:")
print(quat_avg)

### Direct buffer access is supported.
print(memoryview(quat_avg).tobytes())
`

conjugate ( )

Replace the quaternion with its conjugate (negate x, y, z).

conjugated ( )

Give back a fresh conjugated quaternion.

Returns :

a new quaternion.

Return type :

Quaternion

copy ( )

Returns a copy of this quaternion.

Returns :

A copy of the quaternion.

Return type :

Quaternion

Note

reach for this when you need a standalone copy of a wrapped quaternion that no longer points back at the source.

cross ( other , / )

Give back the cross product of this quaternion with another.

Parameters :

other (Quaternion) – The other quaternion to perform the cross product with.

Returns :

The cross product.

Return type :

Quaternion

dot ( other , / )

Give back the dot product of this quaternion with another.

Parameters :

other (Quaternion) – The other quaternion to perform the dot product with.

Returns :

The dot product.

Return type :

float

freeze ( )

Lock this object so it can no longer change.

Once locked, it becomes hashable and usable as a dictionary or set member.

Returns :

An instance of this object.

Return type :

Self

identity ( )

Reset the quaternion to an identity quaternion.

invert ( )

Replace the quaternion with its inverse.

inverted ( )

Give back a fresh, inverted quaternion.

Returns :

the inverted value.

Return type :

Quaternion

make_compatible ( other , / )

Bring this quaternion into line with another so that interpolating across the two behaves the way you'd expect.

Parameters :

other (Quaternion) – The reference quaternion to make this one compatible with.

negate ( )

Replace the quaternion with its negative.

normalize ( )

Normalize the quaternion.

normalized ( )

Give back a fresh normalized quaternion.

Returns :

a normalized copy.

Return type :

Quaternion

rotate ( other , / )

Rotate the quaternion by some other mathutils value.

Parameters :

other (Euler | Quaternion | Matrix) – rotation component of mathutils value

rotation_difference ( other , / )

Give back a quaternion that captures the rotational difference.

Parameters :

other (Quaternion) – second quaternion.

Returns :

the rotational difference between the two quat rotations.

Return type :

Quaternion

slerp ( other , factor , / )

Give back the interpolation between two quaternions.

Parameters :

- other (Quaternion) – value to interpolate with.

- factor ( float ) – The interpolation value in [0.0, 1.0].

Returns :

The interpolated rotation.

Return type :

Quaternion

to_axis_angle ( )

Give back the axis-and-angle form of the quaternion.

Returns :

Axis, angle.

Return type :

tuple[Vector, float]

to_euler ( order = 'XYZ' , euler_compat = None , / )

Give back the Euler form of the quaternion.

Parameters :

- order ( Literal [ 'XYZ' , 'XZY' , 'YXZ' , 'YZX' , 'ZXY' , 'ZYX' ] ) – Rotation order.

- euler_compat (Euler | None) – Optional euler argument the new euler will be made
compatible with (no axis flipping between them).
Useful for converting a series of quaternions to animation curves.

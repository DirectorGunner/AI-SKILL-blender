# Math Types Utilities Mathutils (part 2)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Returns :

Euler representation of the quaternion.

Return type :

Euler

to_exponential_map ( ) 

Hand back the quaternion expressed as an exponential map.

The encoding holds the axis of rotation already scaled by how far the rotation turns.
Storing orientation this way makes blending across several rotations convenient.

Returns :

3D exponential map.

Return type :

Vector

Feed the result into the Quaternion constructor to recover the original quaternion.

to_matrix ( ) 

Hand back the quaternion expressed as a matrix.

Returns :

A 3x3 matrix encoding the same rotation as the quaternion.

Return type :

Matrix

to_swing_twist ( axis , / ) 

Separate the rotation into a swing part (pinned to zero about the named axis)
together with whatever twist angle is left over.

Parameters :

axis ( Literal [ 'X' , 'Y' , 'Z' ] ) – Twist axis as a string.

Returns :

Swing, twist angle.

Return type :

tuple[Quaternion, float]

angle 

Angle of the quaternion.

Type :

float

axis 

Quaternion axis as a vector.

Type :

Vector

is_frozen 

Read-only flag, set once the object has been frozen.

Type :

bool

is_valid 

Indicates the data's owner is still valid.

Type :

bool

is_wrapped 

Read-only flag marking that this object wraps outside data.

Type :

bool

magnitude 

Size of the quaternion (read-only).

Type :

float

owner 

Read-only handle to the wrapped item, or None when there is none.

Type :

Any

w 

Quaternion component value.

Type :

float

x 

Quaternion component value.

Type :

float

y 

Quaternion component value.

Type :

float

z 

Quaternion component value.

Type :

float

class mathutils. Vector ( seq = (0.0, 0.0, 0.0) , / ) 

A handle onto Blender's Vector objects.

Parameters :

seq ( Sequence [ float ] ) – The vector's entries, given as a sequence holding two or more.

`\text
import mathutils

### Zero length vector.
vec = mathutils.Vector((0.0, 0.0, 1.0))

### Unit length vector.
vec_a = vec.normalized()

vec_b = mathutils.Vector((0.0, 1.0, 2.0))

vec2d = mathutils.Vector((1.0, 2.0))
vec3d = mathutils.Vector((1.0, 0.0, 0.0))
vec4d = vec_a.to_4d()

### Other `mathutils` types.
quat = mathutils.Quaternion()
matrix = mathutils.Matrix()

### Comparison operators can be done on Vector classes:

### (In)equality operators == and != test component values, e.g. 1,2,3 != 3,2,1
vec_a == vec_b
vec_a != vec_b

### Ordering operators >, >=, > and vec_b
vec_a >= vec_b
vec_a

classmethod Fill ( size , fill = 0.0 , / ) 

Build a vector size elements long whose every entry equals fill.

Parameters :

- size ( int ) – Number of entries the new vector holds.

- fill ( float ) – Constant copied into every entry.

Returns :

A new vector.

Return type :

Vector

classmethod Linspace ( start , stop , size , / ) 

Build a vector of the given length whose entries step evenly from start through to stop.

Parameters :

- start ( float ) – Lower bound the fill values begin from.

- stop ( float ) – Upper bound the fill values run up to.

- size ( int ) – Number of entries the new vector holds.

Returns :

A new vector.

Return type :

Vector

classmethod Range ( start , stop , step = 1 , / ) 

Build a vector populated with a range of values.

Supply only one value and it counts as stop, while start falls back to 0.

Parameters :

- start ( int ) – Lower bound the fill values begin from.

- stop ( int ) – Upper bound the fill values run up to.

- step ( int ) – Increment separating one entry from the next.

Returns :

A new vector.

Return type :

Vector

classmethod Repeat ( vector , size , / ) 

Build a vector by cycling through the entries of vector until it spans the requested length.

Parameters :

- vector (Vector) – Source whose entries get repeated.

- size ( int ) – Number of entries the new vector holds.

Returns :

A new vector.

Return type :

Vector

angle ( other , fallback = None , / ) 

Give the angle separating this vector and a second one.

Note

On 4D vectors only the x, y and z parts factor in.

Parameters :

- other (Vector) – the second vector the angle is measured against

- fallback ( Any ) – handed back in place of a ValueError whenever the angle is undefined (a zero-length vector).

Returns :

the radian angle, or the supplied fallback instead

Return type :

float | Any

angle_signed ( other , fallback = None , / ) 

Give the signed angle between two 2D vectors, treating clockwise as the positive direction.

Parameters :

- other (Vector) – the second vector the angle is measured against

- fallback ( Any ) – handed back in place of a ValueError whenever the angle is undefined (a zero-length vector).

Returns :

the radian angle, or the supplied fallback instead

Return type :

float | Any

copy ( ) 

Produce a duplicate of this vector.

Returns :

A copy of the vector.

Return type :

Vector

Note

reach for this when you want a standalone copy of a wrapped vector,
detached from the source data.

cross ( other , / ) 

Give the cross product of this vector with another.

Parameters :

other (Vector) – the second operand of the cross product.

Returns :

A vector holding the cross product, or a float in the 2D case.

Return type :

Vector | float

Note

this needs both operands to be either 2D or 3D

dot ( other , / ) 

Give the dot product of this vector with another.

Parameters :

other (Vector) – the second operand of the dot product.

Returns :

The dot product.

Return type :

float

freeze ( )

Lock this object so it can no longer change.

Once frozen the object becomes hashable and may serve as a key in dictionaries and sets.

Returns :

An instance of this object.

Return type :

Self

lerp ( other , factor , / ) 

Blend between this vector and another by linear interpolation.

Parameters :

- other (Vector) – the target the blend runs toward.

- factor ( float ) – Blend weight, normally between 0.0 and 1.0.

Returns :

The interpolated vector.

Return type :

Vector

negate ( ) 

Flip the sign of every component in place.

normalize ( ) 

Rescale the vector in place so its length becomes exactly 1.0.

Warning

A vector that is all zeros stays unchanged when normalized.

Note

On 4D vectors only x, y and z get scaled; w stays as-is,
so the resulting 4D vector might not end up with unit length.

normalized ( ) 

Hand back a fresh copy scaled to unit length.

Note

On 4D vectors only x, y and z get scaled; w stays as-is,
so the resulting 4D vector might not end up with unit length.

Returns :

a unit-length duplicate of this vector

Return type :

Vector

orthogonal ( ) 

Hand back some vector at right angles to this one.

Returns :

a fresh vector turned a quarter-turn away from this one.

Return type :

Vector

Note

which perpendicular direction comes back is unspecified, so rely on it only when any will do.

project ( other , / ) 

Hand back this vector projected onto other .

Parameters :

other (Vector) – second vector.

Returns :

the component of this vector lying along other

Return type :

Vector

reflect ( mirror , / ) 

Hand back this vector bounced off the surface described by mirror .

Parameters :

mirror (Vector) – Typically the surface normal you bounce off of.

Returns :

The bounced vector, sized to match this one.

Return type :

Vector

resize ( size , / ) 

Change this vector in place so it holds size elements.

Parameters :

size ( int ) – How many elements the result should end up with.

resize_2d ( ) 

Shrink the vector in place to 2D (x, y).

resize_3d ( ) 

Shrink or grow the vector in place to 3D (x, y, z).

resize_4d ( ) 

Grow the vector in place to 4D (x, y, z, w).

resized ( size , / ) 

Hand back a copy holding size elements.

Parameters :

size ( int ) – How many elements the result should end up with.

Returns :

A new vector.

Return type :

Vector

rotate ( other , / ) 

Apply a rotation value to this vector in place.

Note

A 2D vector is special: only a 2x2 matrix can rotate it.

Parameters :

other (Euler | Quaternion | Matrix) – rotation component of mathutils value

rotation_difference ( other , / ) 

Give a quaternion describing how to turn from this vector to another.

Parameters :

other (Vector) – second vector.

Returns :

how much rotation separates the pair of vectors.

Return type :

Quaternion

Note

Calling this on 2D vectors triggers an AttributeError .

slerp ( other , factor , fallback = None , / ) 

Blend between two non-zero vectors along the sphere (spherical interpolation).

Parameters :

- other (Vector) – the target the blend runs toward.

- factor ( float ) – Blend weight, usually somewhere from 0.0 to 1.0.

- fallback ( Any ) – handed back rather than raising a ValueError when the result is undefined (a zero-length vector, or exact opposites).

Returns :

The interpolated vector.

Return type :

Vector

to_2d ( ) 

Hand back a 2d duplicate of the vector.

Returns :

a new vector

Return type :

Vector

to_3d ( ) 

Hand back a 3d duplicate of the vector.

Returns :

a new vector

Return type :

Vector

to_4d ( ) 

Hand back a 4d duplicate of the vector.

Returns :

a new vector

Return type :

Vector

to_track_quat ( track = 'Z' , up = 'Y' , / ) 

Build a quaternion orientation from this vector together with the chosen track and up axes.

Parameters :

- track ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Track axis string.

- up ( Literal [ 'X' , 'Y' , 'Z' ] ) – Up axis string.

Returns :

the orientation derived from this vector together with the track and up axes.

Return type :

Quaternion

to_tuple ( precision = -1 , / ) 

Hand back the vector as a tuple, rounded to the requested precision.

Parameters :

precision ( int ) – Decimal places to round to, spanning [-1, 21].

Returns :

this vector's entries after rounding to the chosen precision

Return type :

tuple[float, …]

zero ( ) 

Reset every component to zero.

is_frozen 

Read-only flag, set once the object has been frozen.

Type :

bool

is_valid 

Indicates the data's owner is still valid.

Type :

bool

is_wrapped 

Read-only flag marking that this object wraps outside data.

Type :

bool

length 

Vector Length.

Type :

float

length_squared 

Vector length squared (v.dot(v)).

Type :

float

magnitude 

Vector Length.

Type :

float

owner 

Read-only handle to the wrapped item, or None when there is none.

Type :

Any

w 

Vector W axis (4D Vectors only).

Type :

float

ww 

Type :

Vector

www 

Type :

Vector

wwww 

Type :

Vector

wwwx 

Type :

Vector

wwwy 

Type :

Vector

wwwz 

Type :

Vector

wwx 

Type :

Vector

wwxw 

Type :

Vector

wwxx 

Type :

Vector

wwxy 

Type :

Vector

wwxz 

Type :

Vector

wwy 

Type :

Vector

wwyw 

Type :

Vector

wwyx 

Type :

Vector

wwyy 

Type :

Vector

wwyz 

Type :

Vector

wwz 

Type :

Vector

wwzw 

Type :

Vector

wwzx 

Type :

Vector

wwzy 

Type :

Vector

wwzz 

Type :

Vector

wx 

Type :

Vector

wxw 

Type :

Vector

wxww 

Type :

Vector

wxwx 

Type :

Vector

wxwy 

Type :

Vector

wxwz 

Type :

Vector

wxx

Type :

Vector

wxxw 

Type :

Vector

wxxx 

Type :

Vector

wxxy 

Type :

Vector

wxxz 

Type :

Vector

wxy 

Type :

Vector

wxyw 

Type :

Vector

wxyx 

Type :

Vector

wxyy 

Type :

Vector

wxyz 

Type :

Vector

wxz 

Type :

Vector

wxzw 

Type :

Vector

wxzx 

Type :

Vector

wxzy 

Type :

Vector

wxzz 

Type :

Vector

wy 

Type :

Vector

wyw 

Type :

Vector

wyww 

Type :

Vector

wywx 

Type :

Vector

wywy 

Type :

Vector

wywz 

Type :

Vector

wyx 

Type :

Vector

wyxw 

Type :

Vector

wyxx 

Type :

Vector

wyxy 

Type :

Vector

wyxz 

Type :

Vector

wyy 

Type :

Vector

wyyw 

Type :

Vector

wyyx 

Type :

Vector

wyyy 

Type :

Vector

wyyz 

Type :

Vector

wyz 

Type :

Vector

wyzw 

Type :

Vector

wyzx 

Type :

Vector

wyzy 

Type :

Vector

wyzz 

Type :

Vector

wz 

Type :

Vector

wzw 

Type :

Vector

wzww 

Type :

Vector

wzwx 

Type :

Vector

wzwy 

Type :

Vector

wzwz 

Type :

Vector

wzx 

Type :

Vector

wzxw 

Type :

Vector

wzxx 

Type :

Vector

wzxy 

Type :

Vector

wzxz 

Type :

Vector

wzy 

Type :

Vector

wzyw 

Type :

Vector

wzyx 

Type :

Vector

wzyy 

Type :

Vector

wzyz 

Type :

Vector

wzz 

Type :

Vector

wzzw 

Type :

Vector

wzzx 

Type :

Vector

wzzy 

Type :

Vector

wzzz 

Type :

Vector

x 

Vector X axis.

Type :

float

xw 

Type :

Vector

xww 

Type :

Vector

xwww 

Type :

Vector

xwwx 

Type :

Vector

xwwy 

Type :

Vector

xwwz 

Type :

Vector

xwx 

Type :

Vector

xwxw 

Type :

Vector

xwxx 

Type :

Vector

xwxy 

Type :

Vector

xwxz 

Type :

Vector

xwy 

Type :

Vector

xwyw 

Type :

Vector

xwyx 

Type :

Vector

xwyy 

Type :

Vector

xwyz 

Type :

Vector

xwz 

Type :

Vector

xwzw 

Type :

Vector

xwzx 

Type :

Vector

xwzy 

Type :

Vector

xwzz 

Type :

Vector

xx 

Type :

Vector

xxw 

Type :

Vector

xxww 

Type :

Vector

xxwx 

Type :

Vector

xxwy 

Type :

Vector

xxwz 

Type :

Vector

xxx 

Type :

Vector

xxxw 

Type :

Vector

xxxx 

Type :

Vector

xxxy 

Type :

Vector

xxxz 

Type :

Vector

xxy 

Type :

Vector

xxyw 

Type :

Vector

xxyx 

Type :

Vector

xxyy 

Type :

Vector

xxyz 

Type :

Vector

xxz 

Type :

Vector

xxzw 

Type :

Vector

xxzx 

Type :

Vector

xxzy 

Type :

Vector

xxzz 

Type :

Vector

xy 

Type :

Vector

xyw 

Type :

Vector

xyww 

Type :

Vector

xywx 

Type :

Vector

xywy 

Type :

Vector

xywz 

Type :

Vector

xyx 

Type :

Vector

xyxw 

Type :

Vector

xyxx 

Type :

Vector

xyxy 

Type :

Vector

xyxz 

Type :

Vector

xyy 

Type :

Vector

xyyw 

Type :

Vector

xyyx 

Type :

Vector

xyyy 

Type :

Vector

xyyz 

Type :

Vector

xyz 

Type :

Vector

xyzw 

Type :

Vector

xyzx 

Type :

Vector

xyzy 

Type :

Vector

xyzz 

Type :

Vector

xz 

Type :

Vector

xzw 

Type :

Vector

xzww 

Type :

Vector

xzwx 

Type :

Vector

xzwy 

Type :

Vector

xzwz 

Type :

Vector

xzx 

Type :

Vector

xzxw 

Type :

Vector

xzxx 

Type :

Vector

xzxy 

Type :

Vector

xzxz 

Type :

Vector

xzy 

Type :

Vector

xzyw 

Type :

Vector

xzyx 

Type :

Vector

xzyy 

Type :

Vector

xzyz 

Type :

Vector

xzz 

Type :

Vector

xzzw 

Type :

Vector

xzzx 

Type :

Vector

xzzy 

Type :

Vector

xzzz 

Type :

Vector

y 

Vector Y axis.

Type :

float

yw 

Type :

Vector

yww 

Type :

Vector

ywww 

Type :

Vector

ywwx 

Type :

Vector

ywwy 

Type :

Vector

ywwz 

Type :

Vector

ywx 

Type :

Vector

ywxw 

Type :

Vector

ywxx 

Type :

Vector

ywxy 

Type :

Vector

ywxz 

Type :

Vector

ywy 

Type :

Vector

ywyw 

Type :

Vector

ywyx 

Type :

Vector

ywyy 

Type :

Vector

ywyz 

Type :

Vector

ywz 

Type :

Vector

ywzw 

Type :

Vector

ywzx 

Type :

Vector

ywzy 

Type :

Vector

ywzz 

Type :

Vector

yx 

Type :

Vector

yxw 

Type :

Vector

yxww 

Type :

Vector

yxwx 

Type :

Vector

yxwy 

Type :

Vector

yxwz 

Type :

Vector

yxx 

Type :

Vector

yxxw 

Type :

Vector

yxxx 

Type :

Vector

yxxy 

Type :

Vector

yxxz 

Type :

Vector

yxy 

Type :

Vector

yxyw 

Type :

Vector

yxyx 

Type :

Vector

yxyy 

Type :

Vector

yxyz 

Type :

Vector

yxz 

Type :

Vector

yxzw 

Type :

Vector

yxzx 

Type :

Vector

yxzy 

Type :

Vector

yxzz 

Type :

Vector

yy 

Type :

Vector

yyw 

Type :

Vector

yyww 

Type :

Vector

yywx 

Type :

Vector

yywy 

Type :

Vector

yywz 

Type :

Vector

yyx 

Type :

Vector

yyxw 

Type :

Vector

yyxx 

Type :

Vector

yyxy 

Type :

Vector

yyxz 

Type :

Vector

yyy 

Type :

Vector

yyyw 

Type :

Vector

yyyx 

Type :

Vector

yyyy

Type :

Vector

yyyz 

Type :

Vector

yyz 

Type :

Vector

yyzw 

Type :

Vector

yyzx 

Type :

Vector

yyzy 

Type :

Vector

yyzz 

Type :

Vector

yz 

Type :

Vector

yzw 

Type :

Vector

yzww 

Type :

Vector

yzwx 

Type :

Vector

yzwy 

Type :

Vector

yzwz 

Type :

Vector

yzx 

Type :

Vector

yzxw 

Type :

Vector

yzxx 

Type :

Vector

yzxy 

Type :

Vector

yzxz 

Type :

Vector

yzy 

Type :

Vector

yzyw 

Type :

Vector

yzyx 

Type :

Vector

yzyy 

Type :

Vector

yzyz 

Type :

Vector

yzz 

Type :

Vector

yzzw 

Type :

Vector

yzzx 

Type :

Vector

yzzy 

Type :

Vector

yzzz 

Type :

Vector

z 

Vector Z axis (3D Vectors only).

Type :

float

zw 

Type :

Vector

zww 

Type :

Vector

zwww 

Type :

Vector

zwwx 

Type :

Vector

zwwy 

Type :

Vector

zwwz 

Type :

Vector

zwx 

Type :

Vector

zwxw 

Type :

Vector

zwxx 

Type :

Vector

zwxy 

Type :

Vector

zwxz 

Type :

Vector

zwy 

Type :

Vector

zwyw 

Type :

Vector

zwyx 

Type :

Vector

zwyy 

Type :

Vector

zwyz 

Type :

Vector

zwz 

Type :

Vector

zwzw 

Type :

Vector

zwzx 

Type :

Vector

zwzy 

Type :

Vector

zwzz 

Type :

Vector

zx 

Type :

Vector

zxw 

Type :

Vector

zxww 

Type :

Vector

zxwx 

Type :

Vector

zxwy 

Type :

Vector

zxwz 

Type :

Vector

zxx 

Type :

Vector

zxxw 

Type :

Vector

zxxx 

Type :

Vector

zxxy 

Type :

Vector

zxxz 

Type :

Vector

zxy 

Type :

Vector

zxyw 

Type :

Vector

zxyx 

Type :

Vector

zxyy 

Type :

Vector

zxyz 

Type :

Vector

zxz 

Type :

Vector

zxzw 

Type :

Vector

zxzx 

Type :

Vector

zxzy 

Type :

Vector

zxzz 

Type :

Vector

zy 

Type :

Vector

zyw 

Type :

Vector

zyww 

Type :

Vector

zywx 

Type :

Vector

zywy 

Type :

Vector

zywz 

Type :

Vector

zyx 

Type :

Vector

zyxw 

Type :

Vector

zyxx 

Type :

Vector

zyxy 

Type :

Vector

zyxz 

Type :

Vector

zyy 

Type :

Vector

zyyw 

Type :

Vector

zyyx 

Type :

Vector

zyyy 

Type :

Vector

zyyz 

Type :

Vector

zyz 

Type :

Vector

zyzw 

Type :

Vector

zyzx 

Type :

Vector

zyzy 

Type :

Vector

zyzz 

Type :

Vector

zz 

Type :

Vector

zzw 

Type :

Vector

zzww 

Type :

Vector

zzwx 

Type :

Vector

zzwy 

Type :

Vector

zzwz 

Type :

Vector

zzx 

Type :

Vector

zzxw 

Type :

Vector

zzxx 

Type :

Vector

zzxy 

Type :

Vector

zzxz 

Type :

Vector

zzy 

Type :

Vector

zzyw 

Type :

Vector

zzyx 

Type :

Vector

zzyy 

Type :

Vector

zzyz 

Type :

Vector

zzz 

Type :

Vector

zzzw 

Type :

Vector

zzzx 

Type :

Vector

zzzy 

Type :

Vector

zzzz 

Type :

Vector

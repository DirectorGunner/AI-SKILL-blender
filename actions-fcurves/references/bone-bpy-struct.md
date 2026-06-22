# Bone Bpy Struct, Bonecollectionmemberships Bpy Prop Collection, Bonecollections Bpy Prop Collection, Bonecolor Bpy Struct

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Bone(bpy_struct); BoneCollectionMemberships(bpy_prop_collection); BoneCollections(bpy_prop_collection); BoneColor(bpy_struct).

## Bone(bpy_struct)

### Bone(bpy_struct)

base class — bpy_struct

class bpy.types.Bone(bpy_struct)

A single bone belonging to an Armature data-block

bbone_curveinx

Offset of the X-axis handle at the B-Bone curve's start, shaping its bend (in [-inf, inf], default 0.0)

Type:
float

bbone_curveinz

Offset of the Z-axis handle at the B-Bone curve's start, shaping its bend (in [-inf, inf], default 0.0)

Type:
float

bbone_curveoutx

Offset of the X-axis handle at the B-Bone curve's end, shaping its bend (in [-inf, inf], default 0.0)

Type:
float

bbone_curveoutz

Offset of the Z-axis handle at the B-Bone curve's end, shaping its bend (in [-inf, inf], default 0.0)

Type:
float

bbone_custom_handle_end

Bone that serves as the end handle for the B-Bone curve

Type:
Bone

bbone_custom_handle_start

Bone that serves as the start handle for the B-Bone curve

Type:
Bone

bbone_easein

Length of the first Bézier handle, applicable to B-Bones only (in [-inf, inf], default 1.0)

Type:
float

bbone_easeout

Length of the second Bézier handle, applicable to B-Bones only (in [-inf, inf], default 1.0)

Type:
float

bbone_handle_type_end

Chooses the method for deriving the B-Bone's end handle (default 'AUTO')

- AUTO
Automatic – Use connected parent and children to compute the handle.

- ABSOLUTE
Absolute – Use the position of the specified bone to compute the handle.

- RELATIVE
Relative – Use the offset of the specified bone from rest pose to compute the handle.

- TANGENT
Tangent – Use the orientation of the specified bone to compute the handle, ignoring the location.

Type:
Literal['AUTO', 'ABSOLUTE', 'RELATIVE', 'TANGENT']

bbone_handle_type_start

Chooses the method for deriving the B-Bone's start handle (default 'AUTO')

- AUTO
Automatic – Use connected parent and children to compute the handle.

- ABSOLUTE
Absolute – Use the position of the specified bone to compute the handle.

- RELATIVE
Relative – Use the offset of the specified bone from rest pose to compute the handle.

- TANGENT
Tangent – Use the orientation of the specified bone to compute the handle, ignoring the location.

Type:
Literal['AUTO', 'ABSOLUTE', 'RELATIVE', 'TANGENT']

bbone_handle_use_ease_end

Scale the B-Bone Ease Out channel by the end handle's local Y scale. This happens after, and independently of, the Scale Easing option. (default False)

Type:
bool

bbone_handle_use_ease_start

Scale the B-Bone Ease In channel by the start handle's local Y scale. This happens after, and independently of, the Scale Easing option. (default False)

Type:
bool

bbone_handle_use_scale_end

Scale the B-Bone Scale Out channels by the end handle's local scale values. This happens after, and independently of, the Scale Easing option. (array of 3 items, default (False, False, False))

Type:
bpy_prop_array[bool]

bbone_handle_use_scale_start

Scale the B-Bone Scale In channels by the start handle's local scale values. This happens after, and independently of, the Scale Easing option. (array of 3 items, default (False, False, False))

Type:
bpy_prop_array[bool]

bbone_mapping_mode

Chooses how vertices are matched to B-Bone segments according to where they sit (default 'STRAIGHT')

- STRAIGHT
Straight – Fast mapping that is good for most situations, but ignores the rest pose curvature of the B-Bone.

- CURVED
Curved – Slower mapping that gives better deformation for B-Bones that are sharply curved in rest pose.

Type:
Literal['STRAIGHT', 'CURVED']

bbone_rollin

Roll offset at the B-Bone's start, shaping its twist (in [-inf, inf], default 0.0)

Type:
float

bbone_rollout

Roll offset at the B-Bone's end, shaping its twist (in [-inf, inf], default 0.0)

Type:
float

bbone_scalein

Scale factors at the B-Bone's start, controlling thickness for tapering (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type:
mathutils.Vector

bbone_scaleout

Scale factors at the B-Bone's end, controlling thickness for tapering (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type:
mathutils.Vector

bbone_segments

Count of subdivisions along the bone, applicable to B-Bones only (in [1, 32], default 0)

Type:
int

bbone_x

B-Bone X size (in [-inf, inf], default 0.0)

Type:
float

bbone_z

B-Bone Z size (in [-inf, inf], default 0.0)

Type:
float

children

Bones which are children of this bone (default None, readonly)

Type:
bpy_prop_collection[Bone]

collections

Bone Collections that contain this bone (default None, readonly)

Type:
BoneCollectionMemberships[BoneCollection]

color

(readonly)

Type:
BoneColor

display_type

(default 'OCTAHEDRAL')

- `ARMATURE_DEFINED`
Armature Defined – Use display mode from armature (default).

- OCTAHEDRAL
Octahedral – Display bones as octahedral shape.

- STICK
Stick – Display bones as simple 2D lines with dots.

- BBONE
B-Bone – Display bones as boxes, showing subdivision and B-Splines.

- ENVELOPE
Envelope – Display bones as extruded spheres, showing deformation influence volume.

- WIRE
Wire – Display bones as thin wires, showing subdivision and B-Splines.

Type:
Literal['`ARMATURE_DEFINED`', 'OCTAHEDRAL', 'STICK', 'BBONE', 'ENVELOPE', 'WIRE']

envelope_distance

Reach of the bone's deformation, used only with Envelope deform (in [0, 1000], default 0.0)

Type:
float

envelope_weight

Strength of the bone's deformation, used only with Envelope deform (in [0, 1000], default 0.0)

Type:
float

head

Position of the bone's head end measured against its parent (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type:
mathutils.Vector

head_local

Position of the bone's head end measured against the armature (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type:
mathutils.Vector

head_radius

Radius of head of bone, used only with Envelope deform (in [-inf, inf], default 0.0)

Type:
float

hide

Bone stays hidden while in Edit Mode (default False)

Type:
bool

hide_select

Bone is able to be selected (default False)

Type:
bool

inherit_scale

Controls the manner in which scaling carries down from the parent bone (default 'FULL')

- FULL
Full – Inherit all effects of parent scaling.

- `FIX_SHEAR`
Fix Shear – Inherit scaling, but remove shearing of the child in the rest orientation.

- ALIGNED
Aligned – Rotate non-uniform parent scaling to align with the child, applying parent X scale to child X axis, and so forth.

- AVERAGE
Average – Inherit uniform scaling representing the overall change in the volume of the parent.

- NONE
None – Completely ignore parent scaling.

- `NONE_LEGACY`
None (Legacy) – Ignore parent scaling without compensating for parent shear. Replicates the effect of disabling the original Inherit Scale checkbox..

Type:
Literal['FULL', '`FIX_SHEAR`', 'ALIGNED', 'AVERAGE', 'NONE', '`NONE_LEGACY`']

length

Length of the bone (in [-inf, inf], default 0.0, readonly)

Type:
float

matrix

3×3 bone matrix (multi-dimensional array of 3 * 3 items, in [-inf, inf], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)), readonly)

Type:
mathutils.Matrix

matrix_local

4×4 bone matrix relative to armature (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type:
mathutils.Matrix

name

(default "", never None)

Type:
str

parent

Parent bone (in same Armature) (readonly)

Type:
Bone

show_wire

Keep the bone drawn as wireframe no matter the viewport shading mode, handy for unobtrusive custom bone shapes (default False)

Type:
bool

tail

Position of the bone's tail end measured against its parent (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type:
mathutils.Vector

tail_local

Position of the bone's tail end measured against the armature (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type:
mathutils.Vector

tail_radius

Radius of tail of bone, used only with Envelope deform (in [-inf, inf], default 0.0)

Type:
float

use_connect

With a parent present, the bone's head is locked to the parent's tail (default False, readonly)

Type:
bool

use_cyclic_offset

With no parent present, the bone takes on cyclic offset effects (Deprecated) (default True)

Type:
bool

use_deform

Enable Bone to deform geometry (default True)

Type:
bool

use_endroll_as_inroll

Add Roll Out of the Start Handle bone to the Roll In value (default False)

Type:
bool

use_envelope_multiply

During deformation, combine Vertex Group weights with Envelope influence by multiplication (default False)

Type:
bool

use_inherit_rotation

Bone inherits rotation or scale from parent bone (default True)

Type:
bool

use_local_location

Bone location is set in local space (default True)

Type:
bool

use_relative_parent

Object children will use relative transform, like deform (default False)

Type:
bool

use_scale_easing

Scale the final easing values by the Scale In/Out Y factors (default False)

Type:
bool

basename

The name of this bone before any . character.

(readonly)

center

The midpoint between the head and the tail.

(readonly)

children_recursive

A list of all children from this bone.

Note

Takes O(len(bones)**2) time.

(readonly)

children_recursive_basename

Returns a chain of children with the same base name as this bone.
Only direct chains are supported, forks caused by multiple children
with matching base names will terminate the function
and not be returned.

Note

Takes O(len(bones)**2) time.

(readonly)

parent_recursive

A list of parents, starting with the immediate parent.

(readonly)

vector

The direction this bone is pointing.
Utility function for (tail - head)

(readonly)

x_axis

Vector pointing down the x-axis of the bone.

(readonly)

y_axis

Vector pointing down the y-axis of the bone.

(readonly)

z_axis

Vector pointing down the z-axis of the bone.

(readonly)

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters:
do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns:
The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type:
PropertyGroup

evaluate_envelope ( point )

Calculate bone envelope at given point

Parameters:
point (mathutils.Vector) – Point, Position in 3d space to evaluate (array of 3 items, in [-inf, inf])

Returns:
Factor, Envelope factor (in [-inf, inf])

Return type:
float

convert_local_to_pose ( matrix , matrix_local , * , parent_matrix = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , parent_matrix_local = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , invert = False )

Convert a matrix between Local and Pose space (in either direction), accounting for settings such as Inherit Scale and Local Location. In contrast to Object.convert_space, this relies on rest and pose matrices that the caller supplies. When the parent matrices are left out, the bone is treated as parentless.

Parameters:
- matrix (mathutils.Matrix) – The matrix to transform (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- matrix_local (mathutils.Matrix) – The custom rest matrix of this bone (Bone.matrix_local) (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- parent_matrix (mathutils.Matrix) – The custom pose matrix of the parent bone (PoseBone.matrix) (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- parent_matrix_local (mathutils.Matrix) – The custom rest matrix of the parent bone (Bone.matrix_local) (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- invert ( bool ) – Convert from Pose to Local space (optional)

Returns:
The transformed matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type:
mathutils.Matrix

With this method you can switch bones between Local and Pose space partway through an armature update, carrying refreshed matrices through a recursive traversal yourself, so dependencies need not be recomputed after every individual change.

`text
def set_pose_matrices(obj, matrix_map):
"Assign pose space matrices of all bones at once, ignoring constraints."

def rec(pbone, parent_matrix):
if pbone.name in matrix_map:
matrix = matrix_map[pbone.name]

### # Instead of:
### pbone.matrix = matrix
### bpy.context.view_layer.update()

### Compute and assign local matrix, using the new parent matrix.
if pbone.parent:
pbone.matrix_basis = pbone.bone.convert_local_to_pose(
matrix,
pbone.bone.matrix_local,
parent_matrix=parent_matrix,
parent_matrix_local=pbone.parent.bone.matrix_local,
invert=True
)
else:
pbone.matrix_basis = pbone.bone.convert_local_to_pose(
matrix,
pbone.bone.matrix_local,
invert=True
)
else:
### Compute the updated pose matrix from local and new parent matrix.
if pbone.parent:
matrix = pbone.bone.convert_local_to_pose(
pbone.matrix_basis,
pbone.bone.matrix_local,
parent_matrix=parent_matrix,
parent_matrix_local=pbone.parent.bone.matrix_local,
)
else:
matrix = pbone.bone.convert_local_to_pose(
pbone.matrix_basis,
pbone.bone.matrix_local,
)

### Recursively process children, passing the new matrix through.
for child in pbone.children:
rec(child, matrix)

### Scan all bone trees from their roots.
for pbone in obj.pose.bones:
if not pbone.parent:
rec(pbone, None)
`

classmethod MatrixFromAxisRoll ( axis , roll )

Convert the axis + roll representation to a matrix

Parameters:
- axis (mathutils.Vector) – The main axis of the bone (tail - head) (array of 3 items, in [-inf, inf], never None)

- roll ( float ) – The roll of the bone (in [-inf, inf])

Returns:
The resulting orientation matrix (multi-dimensional array of 3 * 3 items, in [-inf, inf])

Return type:
mathutils.Matrix

classmethod AxisRollFromMatrix ( matrix , * , axis = (0.0, 0.0, 0.0) )

Convert a rotational matrix to the axis + roll representation. Note that the resulting value of the roll may not be as expected if the matrix has shear or negative determinant.

Parameters:
- matrix (mathutils.Matrix) – The orientation matrix of the bone (multi-dimensional array of 3 * 3 items, in [-inf, inf], never None)

- axis ( Sequence [ float ] ) – The optional override for the axis (finds closest approximation for the matrix) (array of 3 items, in [-inf, inf], optional)

Returns:
result_axis , The main axis of the bone, mathutils.Vector

result_roll , The roll of the bone, float

Return type:
tuple[mathutils.Vector, float]

parent_index ( parent_test )

The same as 'bone in other_bone.parent_recursive'
but saved generating a list.

translate ( vec )

Utility function to add vec to the head and tail of this bone.

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters:
- id (str) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.

Returns:
The RNA type or default when not found.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters:
- id (str) – The RNA type identifier.
- default (type | None) – The value to return when not found.

Returns:
The class or default when not found.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| bpy.context.active_bone bpy.context.bone Armature.bones ArmatureBones.active Bone.bbone_custom_handle_end | Bone.bbone_custom_handle_start Bone.children Bone.parent BoneCollection.bones PoseBone.bone |

## BoneCollectionMemberships(bpy_prop_collection)

### BoneCollectionMemberships(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BoneCollectionMemberships ( bpy_prop_collection )

The set of bone collections that this Bone belongs to.

clear ( )

Detaches this bone from every bone collection it currently sits in.

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Bone.collections | |

## BoneCollections(bpy_prop_collection)

### BoneCollections(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BoneCollections ( bpy_prop_collection )

This Armature's set of bone collections.

active

The bone collection currently active on the Armature.

Type :

BoneCollection

active_index

Index pointing at the Armature's active bone collection; a value of -1 signals that nothing is active. Keep in mind this indexes the raw backing array of collections, whose ordering can be surprising. Roots come first, and a collection's siblings always sit back-to-back, but beyond those guarantees the order is arbitrary — so stepping this index up or down may send the active collection somewhere unexpected. When you want consistent behavior, reach for active or active_name instead. (in [-inf, inf], default 0)

Type :

int

active_name

Name of whichever bone collection is active on the Armature; this comes back as an empty string (and never as None) whenever nothing is active (default "", never None)

Type :

str

is_solo_active

A read-only boolean that is set whenever one or more bone collections currently carry the 'solo' flag (default False, readonly)

Type :

bool

new ( name , * , parent = None )

Create a fresh, empty bone collection on the armature.

Parameters :

- name ( str ) – Name, The name to give the new collection. Blender guarantees uniqueness among the Armature's collections. (never None)

- parent (BoneCollection) – Parent Collection, When supplied, the freshly made collection is nested under this one as its child (optional)

Returns :

Newly created bone collection

Return type :

BoneCollection

remove ( bone_collection )

Delete the given bone collection from the armature. Any children it held are not lost — they get promoted up to the removed collection's parent, effectively stepping into the slot it left behind.

Parameters :

bone_collection (BoneCollection) – Bone Collection, The bone collection to remove

move ( from_index , to_index )

Shift a bone collection to another slot within the list. This only reorders collections among their siblings; it never alters parent-child links.

Parameters :

- from_index ( int ) – From Index, Index to move (in [-inf, inf])

- to_index ( int ) – To Index, Target index (in [-inf, inf])

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Armature.collections | |

## BoneColor(bpy_struct)

### BoneColor(bpy_struct)

base class — bpy_struct

class bpy.types. BoneColor ( bpy_struct )

A bone's color, either taken from a theme or set as a custom value.

custom

Holds the per-bone custom colors, applied only while palette is set to 'CUSTOM' (readonly, never None)

Type :

ThemeBoneColorSet

is_custom

True when the palette comes from a user-defined set rather than one supplied by the theme (default False, readonly)

Type :

bool

palette

Which color palette this bone draws from (default 'DEFAULT' )

Type :

Literal['DEFAULT', 'THEME01', 'THEME02', 'THEME03', 'THEME04', 'THEME05', 'THEME06', 'THEME07', 'THEME08', 'THEME09', 'THEME10', 'THEME11', 'THEME12', 'THEME13', 'THEME14', 'THEME15', 'THEME16', 'THEME17', 'THEME18', 'THEME19', 'THEME20', 'CUSTOM']

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Bone.color EditBone.color | PoseBone.color |

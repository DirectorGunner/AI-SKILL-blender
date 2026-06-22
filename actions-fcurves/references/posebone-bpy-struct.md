# Posebone Bpy Struct, Poseboneconstraints Bpy Prop Collection, Preferences Bpy Struct, Preferencesapps Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PoseBone(bpy_struct); PoseBoneConstraints(bpy_prop_collection); Preferences(bpy_struct); PreferencesApps(bpy_struct); PreferencesExtensions(bpy_struct).

## PoseBone(bpy_struct)

### PoseBone(bpy_struct)

base class — bpy_struct

class bpy.types. PoseBone ( bpy_struct )

A channel that holds the pose data for one bone within a Pose.

bbone_curveinx

Curvature handle offset along X at the B-Bone curve's start (in [-inf, inf], default 0.0)

Type :

float

bbone_curveinz

Curvature handle offset along Z at the B-Bone curve's start (in [-inf, inf], default 0.0)

Type :

float

bbone_curveoutx

Curvature handle offset along X at the B-Bone curve's end (in [-inf, inf], default 0.0)

Type :

float

bbone_curveoutz

Curvature handle offset along Z at the B-Bone curve's end (in [-inf, inf], default 0.0)

Type :

float

bbone_custom_handle_end

The bone acting as the end handle of the B-Bone curve (readonly)

Type :

PoseBone

bbone_custom_handle_start

The bone acting as the start handle of the B-Bone curve (readonly)

Type :

PoseBone

bbone_easein

Length of the first Bézier Handle (B-Bones only) (in [-inf, inf], default 0.0)

Type :

float

bbone_easeout

Length of the second Bézier Handle (B-Bones only) (in [-inf, inf], default 0.0)

Type :

float

bbone_rollin

Twist applied via roll offset at the B-Bone's start (in [-inf, inf], default 0.0)

Type :

float

bbone_rollout

Twist applied via roll offset at the B-Bone's end (in [-inf, inf], default 0.0)

Type :

float

bbone_scalein

Thickness scale factors at the B-Bone's start, for tapering (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

bbone_scaleout

Thickness scale factors at the B-Bone's end, for tapering (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

bone

The Bone this PoseBone belongs to (readonly, never None)

Type :

Bone

child

This pose bone's child (readonly)

Type :

PoseBone

color

(readonly)

Type :

BoneColor

constraints

Constraints applied to this pose channel (default None, readonly)

Type :

PoseBoneConstraints[Constraint]

custom_shape

Object used as the custom display shape for this bone

Type :

Object

custom_shape_rotation_euler

Tweak the rotation of the custom shape (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

custom_shape_scale_xyz

Tweak the size of the custom shape (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

custom_shape_transform

Bone whose transform drives the display of this custom shape

Type :

PoseBone

custom_shape_translation

Tweak the position of the custom shape (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

custom_shape_wire_width

Tweak how thick the wire of custom shapes appears (in [1, 16], default 0.0)

Type :

float

head

Position of the channel bone's head (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

hide

Bone stays hidden outside of Edit Mode (default False)

Type :

bool

ik_linear_weight

Strength of the IK scale constraint (in [0, 1], default 0.0)

Type :

float

ik_max_x

Upper angle bound for the IK Limit (in [0, 3.14159], default 0.0)

Type :

float

ik_max_y

Upper angle bound for the IK Limit (in [0, 3.14159], default 0.0)

Type :

float

ik_max_z

Upper angle bound for the IK Limit (in [0, 3.14159], default 0.0)

Type :

float

ik_min_x

Lower angle bound for the IK Limit (in [-3.14159, 0], default 0.0)

Type :

float

ik_min_y

Lower angle bound for the IK Limit (in [-3.14159, 0], default 0.0)

Type :

float

ik_min_z

Lower angle bound for the IK Limit (in [-3.14159, 0], default 0.0)

Type :

float

ik_rotation_weight

Strength of the IK rotation constraint (in [0, 1], default 0.0)

Type :

float

ik_stiffness_x

Resistance to IK rotation about the X axis (in [0, 0.99], default 0.0)

Type :

float

ik_stiffness_y

Resistance to IK rotation about the Y axis (in [0, 0.99], default 0.0)

Type :

float

ik_stiffness_z

Resistance to IK rotation about the Z axis (in [0, 0.99], default 0.0)

Type :

float

ik_stretch

Permit the bone to scale for IK (in [0, 1], default 0.0)

Type :

float

is_in_ik_chain

Whether this bone belongs to an IK chain (default False, readonly)

Type :

bool

length

The bone's length (in [-inf, inf], default 0.0, readonly)

Type :

float

location

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

lock_ik_x

Block rotation about the X axis (default False)

Type :

bool

lock_ik_y

Block rotation about the Y axis (default False)

Type :

bool

lock_ik_z

Block rotation about the Z axis (default False)

Type :

bool

lock_location

Prevent location from being edited while transforming (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

lock_rotation

Prevent rotation from being edited while transforming (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

lock_rotation_w

Prevent the ‘angle’ part of four-component rotations from being edited while transforming (default False)

Type :

bool

lock_rotations_4d

Edit four-component rotations component-by-component rather than as Eulers, and lock them that way (default False)

Type :

bool

lock_scale

Prevent scale from being edited while transforming (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

matrix

The final 4×4 matrix in armature object space, with constraints and drivers already applied (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_basis

A secondary way to reach location/scale/rotation relative to the parent and the bone's own rest pose (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_channel

4×4 matrix combining the bone's location/rotation/scale channels (animation and drivers included) together with the result of bone constraints (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

motion_path

The Motion Path belonging to this element (readonly)

Type :

MotionPath

name

(default “”, never None)

Type :

str

parent

This pose bone's parent (readonly)

Type :

PoseBone

rotation_axis_angle

Rotation angle for the Axis-Angle rotation form (array of 4 items, in [-inf, inf], default (0.0, 0.0, 1.0, 0.0))

Type :

bpy_prop_array[float]

rotation_euler

Euler-form rotation (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

rotation_mode

Which rotation form is active; values from the other forms stay unused (default 'QUATERNION' )

Type :

Literal[Object Rotation Mode Items]

rotation_quaternion

Quaternion-form rotation (array of 4 items, in [-inf, inf], default (1.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

scale

(array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

select

Bone is part of the Pose Mode selection (default False)

Type :

bool

tail

Position of the channel bone's tail (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

use_custom_shape_bone_size

Size the custom object relative to the bone's length (default True)

Type :

bool

use_ik_limit_x

Constrain movement about the X axis (default False)

Type :

bool

use_ik_limit_y

Constrain movement about the Y axis (default False)

Type :

bool

use_ik_limit_z

Constrain movement about the Z axis (default False)

Type :

bool

use_ik_linear_control

Feed channel size into the IK constraint when stretching is on (default False)

Type :

bool

use_ik_rotation_control

Feed channel rotation into the IK constraint (default False)

Type :

bool

use_transform_around_custom_shape

Move the bone as though parented to the Custom Shape Transform bone. Handy when blending shape-key and armature deformations. (default False)

Type :

bool

use_transform_at_custom_shape

Drive transform gizmos and other 3D Viewport transform operators from the Custom Shape Transform bone's location and orientation. With this off, the 3D Viewport keeps using the real bone transform even where the custom bone shape transform overrides it. (default False)

Type :

bool

basename

This bone's name truncated before the first . character.

(readonly)

center

The point halfway between the head and the tail.

(readonly)

children

(readonly)

children_recursive

Every descendant of this bone collected into a list.

Note

Takes O(len(bones)**2) time.

(readonly)

children_recursive_basename

Walks the descendants that share this bone's base name and returns them as a chain. Only unbroken chains work; if two or more children share a base name the fork stops the walk and nothing past it is returned.

Note

Takes O(len(bones)**2) time.

(readonly)

parent_recursive

The parents listed from the closest one outward.

(readonly)

vector

Which way the bone points.
Utility function for (tail - head)

(readonly)

x_axis

Vector aimed along the bone's x-axis.

(readonly)

y_axis

Vector aimed along the bone's y-axis.

(readonly)

z_axis

Vector aimed along the bone's z-axis.

(readonly)

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. A back door into runtime-defined RNA data storage meant only for tests and debugging. Leave it alone in normal scripting, and never count on its contents being writable

Parameters :

do_create ( bool ) – Force the system properties into existence when they are not present (optional)

Returns :

The root container holding the system properties, or None when none are stored on this data yet and creating them was not asked for

Return type :

PropertyGroup

evaluate_envelope ( point )

Compute the bone's envelope value at the supplied point

Parameters :

point (mathutils.Vector) – Point, The 3d-space location to sample (array of 3 items, in [-inf, inf])

Returns :

Factor, Envelope factor (in [-inf, inf])

Return type :

float

bbone_segment_index ( point )

From a vertex position, look up which B-Bone segment applies and how it blends

Parameters :

point (mathutils.Vector) – Point, The vertex's location in armature pose space (array of 3 items, in [-inf, inf])

Returns :

index , The index of the first segment joint affecting the point, int

blend_next , The blend factor between the given and the following joint, float

Return type :

tuple[int, float]

bbone_segment_matrix ( index , * , rest = False )

Look up the matrix at the joint between B-Bone segments, when one exists

Parameters :

- index ( int ) – The segment endpoint's index (in [0, inf])

- rest ( bool ) – Hand back the rest pose matrix (optional)

Returns :

The resulting matrix in bone local space (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type :

mathutils.Matrix

The snippet below reproduces, via B-Bone segment matrices, the deformation that the Armature modifier or constraint would apply to a given bone (Preserve Volume off). All coordinates are handled in armature Pose space:

`\text
import bpy

def bbone_deform_matrix(pose_bone, point):
index, blend_next = pose_bone.bbone_segment_index(point)

rest1 = pose_bone.bbone_segment_matrix(index, rest=True)
pose1 = pose_bone.bbone_segment_matrix(index, rest=False)
deform1 = pose1 @ rest1.inverted()

### `bbone_segment_index` ensures that index + 1 is always valid
rest2 = pose_bone.bbone_segment_matrix(index + 1, rest=True)
pose2 = pose_bone.bbone_segment_matrix(index + 1, rest=False)
deform2 = pose2 @ rest2.inverted()

deform = deform1 * (1 - blend_next) + deform2 * blend_next

return pose_bone.matrix @ deform @ pose_bone.bone.matrix_local.inverted()

### Armature modifier deforming vertices:
mesh = bpy.data.objects["Mesh"]
pose_bone = bpy.data.objects["Armature"].pose.bones["Bone"]

for vertex in mesh.data.vertices:
vertex.co = bbone_deform_matrix(pose_bone, vertex.co) @ vertex.co

### Armature constraint modifying an object transform:
empty = bpy.data.objects["Empty"]
matrix = empty.matrix_world

empty.matrix_world = bbone_deform_matrix(pose_bone, matrix.translation) @ matrix
`

compute_bbone_handles ( * , rest = False , ease = False , offsets = False )

Read back the vectors and rolls produced by the B-Bone's custom handles

Parameters :

- rest ( bool ) – Hand back the rest pose state (optional)

- ease ( bool ) – Fold in scaling taken from the ease values (optional)

- offsets ( bool ) – Fold in roll and curve offsets read from bone properties (optional)

Returns :

handle1 , The direction vector of the start handle in bone local space, mathutils.Vector

roll1 , Roll of the start handle, float

handle2 , The direction vector of the end handle in bone local space, mathutils.Vector

roll2 , Roll of the end handle, float

Return type :

tuple[mathutils.Vector, float, mathutils.Vector, float]

parent_index ( parent_test )

Equivalent to ‘bone in other_bone.parent_recursive’, but avoids building the list.

translate ( vec )

Helper that shifts both the head and tail of this bone by vec.

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

| bpy.context.active_pose_bone bpy.context.pose_bone bpy.context.selected_pose_bones bpy.context.selected_pose_bones_from_active_object bpy.context.visible_pose_bones Object.convert_space | Pose.bones PoseBone.bbone_custom_handle_end PoseBone.bbone_custom_handle_start PoseBone.child PoseBone.custom_shape_transform PoseBone.parent |

## PoseBoneConstraints(bpy_prop_collection)

### PoseBoneConstraints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. PoseBoneConstraints ( bpy_prop_collection )

The set of constraints belonging to a pose bone.

active

The currently active PoseChannel constraint

Type :

Constraint

new ( type )

Attach a new constraint to this object

Parameters :

type (Literal[Constraint Type Items]) – Which kind of constraint to add

Returns :

New constraint

Return type :

Constraint

remove ( constraint )

Detach a constraint from this object

Parameters :

constraint (Constraint) – The constraint being removed (never None)

move ( from_index , to_index )

Shift a constraint to another slot

Parameters :

- from_index ( int ) – From Index, The slot to move from (in [-inf, inf])

- to_index ( int ) – To Index, The destination slot (in [-inf, inf])

copy ( constraint )

Append a constraint that duplicates the one supplied

Parameters :

constraint (Constraint) – The constraint to duplicate - it may live on another object (never None)

Returns :

New constraint

Return type :

Constraint

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

| PoseBone.constraints | |

## Preferences(bpy_struct)

### Preferences(bpy_struct)

base class — bpy_struct

class bpy.types. Preferences ( bpy_struct )

Blender's global preference settings.

active_section

Preferences (default 'INTERFACE' )

Type :

Literal[Preference Section Items]

addons

(default None, readonly)

Type :

Addons[Addon]

app_template

(default “”, never None)

Type :

str

apps

Preferences that apply to apps only (readonly, never None)

Type :

PreferencesApps

autoexec_paths

(default None, readonly)

Type :

PathCompareCollection[PathCompare]

edit

Options governing how you interact with Blender's data (readonly, never None)

Type :

PreferencesEdit

experimental

Options for features that remain early in development (readonly, never None)

Type :

PreferencesExperimental

extensions

Options for extensions (readonly, never None)

Type :

PreferencesExtensions

filepaths

Default locations used for external files (readonly, never None)

Type :

PreferencesFilePaths

inputs

Options for input devices (readonly, never None)

Type :

PreferencesInput

is_dirty

Preferences have unsaved changes (default False)

Type :

bool

keymap

Shortcut configuration for keyboards and other input devices (readonly, never None)

Type :

PreferencesKeymap

show_hidden_ids

Reveal data-blocks whose names start with a dot in search menus (default False)

Type :

bool

studio_lights

(default None, readonly)

Type :

StudioLights[StudioLight]

system

Settings for the graphics driver and operating system (readonly, never None)

Type :

PreferencesSystem

themes

(default None, readonly)

Type :

bpy_prop_collection[Theme]

ui_styles

(default None, readonly)

Type :

bpy_prop_collection[ThemeStyle]

use_preferences_save

On exit, write preferences back if they were changed (skipped after loading factory settings) (default True)

Type :

bool

use_recent_searches

Float the most recently searched entries to the top (default True)

Type :

bool

version

The Blender version that wrote the userpref.blend (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

view

Preferences governing how data is viewed (readonly, never None)

Type :

PreferencesView

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

| Context.preferences | |

## PreferencesApps(bpy_struct)

### PreferencesApps(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesApps ( bpy_struct )

Preferences that apply to apps only

show_corner_split

Drag from a corner to split or join editors (default True)

Type :

bool

show_edge_resize

Drag along an edge to resize editors (default True)

Type :

bool

show_regions_visibility_toggle

Toggles that show or hide the header and side bars (default True)

Type :

bool

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

| Preferences.apps | |

## PreferencesExtensions(bpy_struct)

### PreferencesExtensions(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesExtensions ( bpy_struct )

Options for extensions

active_repo

Which extensions repository is currently being edited in the Preferences UI, given by index (in [-32768, 32767], default 0)

Type :

int

repos

(default None, readonly)

Type :

UserExtensionRepoCollection[UserExtensionRepo]

use_online_access_handled

Set once the user has seen the “Online Access” prompt and chosen a response (default False)

Type :

bool

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

| Preferences.extensions | |

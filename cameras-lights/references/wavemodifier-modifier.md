# Wavemodifier Modifier, Weightednormalmodifier Modifier, Weldmodifier Modifier, Worldmistsettings Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: WaveModifier(Modifier); WeightedNormalModifier(Modifier); WeldModifier(Modifier); WorldMistSettings(bpy_struct); XrNavigation(bpy_struct); XrSessionSettings(bpy_struct); bpy.utils submodule (bpy.utils.units).

## WaveModifier(Modifier)

### WaveModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. WaveModifier ( Modifier )

Wave effect modifier

damping_time

How many frames the wave takes to fade out once it dies (in [-1.04857e+06, 1.04857e+06], default 10.0)

Type :

float

falloff_radius

Distance past which the wave fades away (in [0, inf], default 0.0)

Type :

float

height

Height of the wave (in [-inf, inf], default 0.5)

Type :

float

invert_vertex_group

Flip the vertex group's influence (default False)

Type :

bool

lifetime

How long the wave lasts in frames; zero means it never ends (in [-1.04857e+06, 1.04857e+06], default 0.0)

Type :

float

narrowness

Spread between a wave's crest and its base; larger values make the wave thinner (in [0, inf], default 1.5)

Type :

float

speed

How fast the wave travels; negative values send it back toward the origin (in [-inf, inf], default 0.25)

Type :

float

start_position_object

Object that marks the wave's center

Type :

Object

start_position_x

Start position along X (in [-inf, inf], default 0.0)

Type :

float

start_position_y

Start position along Y (in [-inf, inf], default 0.0)

Type :

float

texture

Type :

Texture

texture_coords

(default 'LOCAL' )

- LOCAL
Local – Read texture coordinates from the local coordinate system.

- GLOBAL
Global – Read texture coordinates from the global coordinate system.

- OBJECT
Object – Read texture coordinates from a linked object's local coordinate system.

- UV
UV – Read texture coordinates from the UV layer.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT', 'UV']

texture_coords_bone

Bone supplying the texture coordinates (default "", never None)

Type :

str

texture_coords_object

Object supplying the texture coordinates

Type :

Object

time_offset

Acts as the start frame for positive speed or the end frame for negative speed (in [-1.04857e+06, 1.04857e+06], default 0.0)

Type :

float

use_cyclic

Make the wave effect repeat cyclically (default True)

Type :

bool

use_normal

Push geometry out along the normals (default False)

Type :

bool

use_normal_x

Allow displacement along the X normal (default True)

Type :

bool

use_normal_y

Allow displacement along the Y normal (default True)

Type :

bool

use_normal_z

Allow displacement along the Z normal (default True)

Type :

bool

use_x

Move along the X axis (default True)

Type :

bool

use_y

Move along the Y axis (default True)

Type :

bool

uv_layer

UV map name (default "", never None)

Type :

str

vertex_group

Vertex group name used to modulate the wave (default "", never None)

Type :

str

width

Gap between successive waves (in [0, inf], default 1.5)

Type :

float

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## WeightedNormalModifier(Modifier)

### WeightedNormalModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. WeightedNormalModifier ( Modifier )

invert_vertex_group

Flip the vertex group's influence (default False)

Type :

bool

keep_sharp

Preserve sharp edges as found for default custom normals, rather than assigning one weighted normal per vertex (default False)

Type :

bool

mode

Which weighted vertex-normal mode to apply (default '`FACE_AREA`' )

- `FACE_AREA`
Face Area – Weight normals by the area of each face.

- `CORNER_ANGLE`
Corner Angle – Weight normals by the angle at each corner.

- `FACE_AREA_WITH_ANGLE`
Face Area & Angle – Weight normals by face area and corner angle together.

Type :

Literal['`FACE_AREA`', '`CORNER_ANGLE`', '`FACE_AREA_WITH_ANGLE`']

thresh

How close two weights must be to count as equal (in [0, 10], default 0.01)

Type :

float

use_face_influence

Factor each face's influence into the weighting (default False)

Type :

bool

vertex_group

Vertex group name used to pick the affected areas (default "", never None)

Type :

str

weight

Correction factor applied to face weights; 50 is neutral, lower values favor weak faces and higher values favor strong faces (in [1, 100], default 50)

Type :

int

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## WeldModifier(Modifier)

### WeldModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. WeldModifier ( Modifier )

Weld modifier

invert_vertex_group

Flip the vertex group's influence (default False)

Type :

bool

loose_edges

Also collapse face-less edges such as cloth sewing edges (default False)

Type :

bool

merge_threshold

Distance under which vertices get merged (in [0, inf], default 0.001)

Type :

float

mode

Sets which rule governs the merge (default 'ALL' )

- ALL
All – Merge everything within the distance.

- CONNECTED
Connected – Restrict merging to vertices joined by edges.

Type :

Literal['ALL', 'CONNECTED']

vertex_group

Vertex group name used to pick the affected areas (default "", never None)

Type :

str

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## WorldMistSettings(bpy_struct)

### WorldMistSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. WorldMistSettings ( bpy_struct ) 

Mist settings attached to a World data-block

depth 

The range across which mist gradually reaches full strength (in [0, inf], default 25.0)

Type :

float

falloff 

Curve that governs how the mist tapers off (default 'QUADRATIC' )

- QUADRATIC
Quadratic – Use quadratic progression.

- LINEAR
Linear – Use linear progression.

- `INVERSE_QUADRATIC`
Inverse Quadratic – Use inverse quadratic progression.

Type :

Literal[‘QUADRATIC’, ‘LINEAR’, ‘`INVERSE_QUADRATIC`’]

height 

Governs how quickly mist thins out as elevation rises (in [0, 100], default 0.0)

Type :

float

intensity 

Floor on the mist effect's overall strength (in [0, 1], default 0.0)

Type :

float

start 

Where the mist begins, measured outward from the camera (in [0, inf], default 5.0)

Type :

float

use_mist 

Hide distant objects behind the environment color as distance grows (default False)

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

| World.mist_settings | |

## XrNavigation(bpy_struct)

### XrNavigation(bpy_struct) 

base class — bpy_struct

class bpy.types. XrNavigation ( bpy_struct ) 

Settings that control VR navigation

invert_rotation 

Flip which way rotation input turns the view (default False)

Type :

bool

snap_turn 

Rotate the camera in fixed steps rather than smoothly (default True)

Type :

bool

turn_amount 

How many degrees each step covers under snap turn (in [0, 6.28319], default 0.523599)

Type :

float

turn_speed 

Rotation rate in degrees per second (in [0, inf], default 1.0472)

Type :

float

vignette_intensity 

How strong the vignette grows while moving (in [0, 100], default 70.0)

Type :

float

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

| PreferencesInput.xr_navigation | |

## XrSessionSettings(bpy_struct)

### XrSessionSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. XrSessionSettings ( bpy_struct ) 

base_pose_angle 

Z-axis rotation that the VR headset's rotation deltas are applied on top of (in [-inf, inf], default 0.0)

Type :

float

base_pose_location 

Origin point that the headset's translation deltas are added to (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

base_pose_object 

Object whose location and rotation the headset's translation and rotation deltas build upon

Type :

Object

base_pose_type 

Source of the VR view's base location and rotation, onto which the headset's translation and rotation deltas are added (default '`SCENE_CAMERA`' )

- `SCENE_CAMERA`
Scene Camera – Follow the active scene camera to define the VR view’s base pose.

- OBJECT
Object – Follow the transformation of an object to define the VR view’s base pose.

- CUSTOM
Custom – Follow a custom transformation to define the VR view’s base pose.

Type :

Literal[‘`SCENE_CAMERA`’, ‘OBJECT’, ‘CUSTOM’]

base_scale 

Uniform scale of the base pose used for the VR view (in [1e-06, inf], default 1.0)

Type :

float

clip_end 

Far clip distance for the VR viewport (in [1e-06, inf], default 0.0)

Type :

float

clip_start 

Near clip distance for the VR viewport (in [1e-06, inf], default 0.0)

Type :

float

controller_draw_style 

How VR controllers are drawn (default 'DARK' )

- DARK
Dark – Draw dark controller.

- LIGHT
Light – Draw light controller.

- `DARK_RAY`
Dark + Ray – Draw dark controller with aiming axis ray.

- `LIGHT_RAY`
Light + Ray – Draw light controller with aiming axis ray.

Type :

Literal[‘DARK’, ‘LIGHT’, ‘`DARK_RAY`’, ‘`LIGHT_RAY`’]

fly_speed 

Flying speed measured in meters per second (in [1e-06, inf], default 0.0)

Type :

float

icon_from_show_object_viewport 

(in [-inf, inf], default 0, readonly)

Type :

int

shading 

(readonly, never None)

Type :

View3DShading

show_annotation 

Display annotations in this view (default False)

Type :

bool

show_controllers 

Display the VR controllers (needs VR actions supplying controller poses) (default False)

Type :

bool

show_custom_overlays 

Display custom VR overlays (default False)

Type :

bool

show_floor 

Display the ground-plane grid (default False)

Type :

bool

show_object_extras 

Display object extras such as empties, lights, and cameras (default False)

Type :

bool

show_object_select_armature 

Permit selecting armatures (default True)

Type :

bool

show_object_select_camera 

Permit selecting cameras (default True)

Type :

bool

show_object_select_curve 

Permit selecting curves (default True)

Type :

bool

show_object_select_curves 

Permit selecting hair curves (default True)

Type :

bool

show_object_select_empty 

Permit selecting empties (default True)

Type :

bool

show_object_select_font 

Permit selecting text objects (default True)

Type :

bool

show_object_select_grease_pencil 

Permit selecting Grease Pencil objects (default True)

Type :

bool

show_object_select_lattice 

Permit selecting lattices (default True)

Type :

bool

show_object_select_light 

Permit selecting lights (default True)

Type :

bool

show_object_select_light_probe 

Permit selecting light probes (default True)

Type :

bool

show_object_select_mesh 

Permit selecting mesh objects (default True)

Type :

bool

show_object_select_meta 

Permit selecting metaballs (default True)

Type :

bool

show_object_select_pointcloud 

Permit selecting point clouds (default True)

Type :

bool

show_object_select_speaker 

Permit selecting speakers (default True)

Type :

bool

show_object_select_surf 

Permit selecting surfaces (default True)

Type :

bool

show_object_select_volume 

Permit selecting volumes (default True)

Type :

bool

show_object_viewport_armature 

Display armatures (default True)

Type :

bool

show_object_viewport_camera 

Display cameras (default True)

Type :

bool

show_object_viewport_curve 

Display curves (default True)

Type :

bool

show_object_viewport_curves 

Display hair curves (default True)

Type :

bool

show_object_viewport_empty 

Display empties (default True)

Type :

bool

show_object_viewport_font 

Display text objects (default True)

Type :

bool

show_object_viewport_grease_pencil 

Display Grease Pencil objects (default True)

Type :

bool

show_object_viewport_lattice 

Display lattices (default True)

Type :

bool

show_object_viewport_light 

Display lights (default True)

Type :

bool

show_object_viewport_light_probe 

Display light probes (default True)

Type :

bool

show_object_viewport_mesh 

Display mesh objects (default True)

Type :

bool

show_object_viewport_meta 

Display metaballs (default True)

Type :

bool

show_object_viewport_pointcloud 

Display point clouds (default True)

Type :

bool

show_object_viewport_speaker 

Display speakers (default True)

Type :

bool

show_object_viewport_surf 

Display surfaces (default True)

Type :

bool

show_object_viewport_volume 

Display volumes (default True)

Type :

bool

show_passthrough 

Display the passthrough view (default False)

Type :

bool

show_selection 

Display selection outlines (default False)

Type :

bool

use_absolute_tracking 

Let the VR tracking origin be set independently from the headset's position (default False)

Type :

bool

use_positional_tracking 

Let VR headsets influence position in virtual space as well as rotation (default False)

Type :

bool

view_scale 

Fine-tuning scale factor for the VR view. Changing it leaves the viewer at the same position relative to the world. (in [1e-06, inf], default 1.0)

Type :

float

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

| WindowManager.xr_session_settings | |

## bpy.utils submodule (bpy.utils.units)

### bpy.utils submodule (bpy.utils.units) 

Some data and methods for handling units are collected in this module.

bpy.utils.units. categories 

Constant value bpy.utils.units.categories(NONE='NONE', LENGTH='LENGTH', AREA='AREA', VOLUME='VOLUME', MASS='MASS', ROTATION='ROTATION', TIME='TIME', `TIME_ABSOLUTE`='`TIME_ABSOLUTE`', VELOCITY='VELOCITY', ACCELERATION='ACCELERATION', CAMERA='CAMERA', POWER='POWER', TEMPERATURE='TEMPERATURE', WAVELENGTH='WAVELENGTH', `COLOR_TEMPERATURE`='`COLOR_TEMPERATURE`', FREQUENCY='FREQUENCY')

bpy.utils.units. systems 

Constant value bpy.utils.units.systems(NONE='NONE', METRIC='METRIC', IMPERIAL='IMPERIAL')

bpy.utils.units. to_string ( unit_system , unit_category , value , * , precision = 3 , split_unit = False , compatible_unit = False ) 

Turn a given input float value into a units string.

Parameters :

- unit_system ( str ) – The unit system, from bpy.utils.units.systems.

- unit_category ( str ) – The category of data we are converting (length, area, rotation, etc.),
from bpy.utils.units.categories.

- value ( float ) – The value to convert to a string.

- precision ( int ) – Number of digits after the decimal point.

- split_unit ( bool ) – Whether to use several units if needed (1m1cm), or always only one (1.01m).

- compatible_unit ( bool ) – Whether to use keyboard-friendly units (1m2) or nicer UTF8 ones (1m²).

Returns :

The converted string.

Return type :

str

Raises :

ValueError – if conversion fails to generate a valid Python string.

bpy.utils.units. to_value ( unit_system , unit_category , str_input , * , str_ref_unit = None ) 

Turn a given input string into a float value.

Parameters :

- unit_system ( str ) – The unit system, from bpy.utils.units.systems.

- unit_category ( str ) – The category of data we are converting (length, area, rotation, etc.),
from bpy.utils.units.categories.

- str_input ( str ) – The string to convert to a float value.

- str_ref_unit ( str | None ) – A reference string from which to extract a default unit, if none is found in str_input .

Returns :

The converted/interpreted value.

Return type :

float

Raises :

ValueError – if conversion fails to generate a valid Python float value.

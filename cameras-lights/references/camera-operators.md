# Camera Operators, Geometry Operators, Marker Operators, World Operators ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Camera Operators; Geometry Operators; Marker Operators; World Operators; AnimVizMotionPaths(bpy_struct); ArmatureModifier(Modifier); ArrayModifier(Modifier); AttributeGroupMesh(bpy_prop_collection); BlendDataCameras(bpy_prop_collection).

## Camera Operators

### Camera Operators

bpy.ops.camera. preset_add ( * , name = '' , remove_name = False , remove_active = False , use_focal_length = False )

Add or remove a Camera Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

- use_focal_length ( bool ) – Include Focal Length, Include focal length into the preset (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.camera. safe_areas_preset_add ( * , name = '' , remove_name = False , remove_active = False )

Add or remove a Safe Areas Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

## Geometry Operators

### Geometry Operators

bpy.ops.geometry.attribute_add(*, name='', domain='POINT', data_type='FLOAT')

Insert an attribute to the form

Parameters:

- name (str) – Name, Title of the new attribute (optional, never None)
- domain (Literal[Attribute Domain Items]) – Domain, Classification of component that attribute is held via (optional)
- data_type (Literal[Attribute Type Items]) – Data Type, Kind of material retained in attribute (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.attribute_convert(*, mode='GENERIC', domain='POINT', data_type='FLOAT')

Alter the storage mechanism for the attribute

Parameters:

- mode (Literal['GENERIC', '`VERTEX_GROUP`']) – Mode, (optional)
- domain (Literal[Attribute Domain Items]) – Domain, Which form component to carry the attribute towards (optional)
- data_type (Literal[Attribute Type Items]) – Data Type, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.attribute_remove()

Pull an attribute from the form

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.color_attribute_add(*, name='', domain='POINT', data_type='`FLOAT_COLOR`', color=(0.0, 0.0, 0.0, 1.0))

Insert a tint attribute to the form

Parameters:

- name (str) – Name, Title of the new tint attribute (optional, never None)
- domain (Literal[Color Attribute Domain Items]) – Domain, Classification of component that attribute is held via (optional)
- data_type (Literal[Color Attribute Type Items]) – Data Type, Kind of material retained in attribute (optional)
- color (Sequence[float]) – Color, Base fill tint (sequence of 4 items, in [0, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.color_attribute_convert(*, domain='POINT', data_type='`FLOAT_COLOR`')

Alter the storage mechanism for the tint attribute

Parameters:

- domain (Literal[Color Attribute Domain Items]) – Domain, Classification of component that attribute is held via (optional)
- data_type (Literal[Color Attribute Type Items]) – Data Type, Kind of material retained in attribute (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.color_attribute_duplicate()

Replicate tint attribute

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.color_attribute_remove()

Pull a tint attribute from the form

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.color_attribute_render_set(*, name='Color')

Fix the default tint attribute for visual output

Parameters:

name (str) – Name, Title of tint attribute (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.geometry.geometry_randomization(*, value=False)

Shuffle form organization for bug hunting use

Parameters:

value (bool) – Value, Rearrange the placement of form aspects (e.g. vertices or edges) post- certain work where sequencing has no assurance. This blocks inadvertently trusting a characteristic that may alter further on (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

## Marker Operators

### Marker Operators

bpy.ops.marker. add ( )

Add a new time marker

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. camera_bind ( )

Bind the selected camera to a marker on the current frame

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. delete ( * , confirm = True )

Delete selected time marker(s)

Parameters :

confirm ( bool ) – Confirm, Ask for confirmation first (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. duplicate ( * , frames = 0 )

Duplicate selected time marker(s)

Parameters :

frames ( int ) – Frames, (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. make_links_scene ( * , scene = '' )

Copy selected markers to another scene

Parameters :

scene ( str ) – Scene, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. move ( * , frames = 0 , tweak = False )

Move selected time marker(s)

Parameters :

- frames ( int ) – Frames, (in [-inf, inf], optional)

- tweak ( bool ) – Tweak, The operator was started with a click-drag event (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. rename ( * , name = 'RenamedMarker' )

Rename first selected time marker

Parameters :

name ( str ) – Name, New name for the marker (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. select ( * , wait_to_deselect_others = False , use_select_on_click = False , mouse_x = 0 , mouse_y = 0 , extend = False , camera = False )

Select time marker(s)

Parameters :

- wait_to_deselect_others ( bool ) – Wait to Deselect Others, (optional)

- use_select_on_click ( bool ) – Act on Click, Rather than selecting on mouse press, wait to see whether a drag follows; otherwise select on release (optional)

- mouse_x ( int ) – Mouse X, (in [-inf, inf], optional)

- mouse_y ( int ) – Mouse Y, (in [-inf, inf], optional)

- extend ( bool ) – Extend, Grow the current selection (optional)

- camera ( bool ) – Camera, Select the camera (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. select_all ( * , action = 'TOGGLE' )

Change selection of all time markers

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Which selection action to run (optional)

- TOGGLE
Toggle – Flip the selection state of every element.

- SELECT
Select – Select every element.

- DESELECT
Deselect – Deselect every element.

- INVERT
Invert – Swap which elements are selected.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' , tweak = False )

Select all time markers using box selection

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Start a fresh selection.

- ADD
Extend – Add to the current selection.

- SUB
Subtract – Remove from the current selection.

- tweak ( bool ) – Tweak, The operator was started with a click-drag event (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.marker. select_leftright ( * , mode = 'LEFT' , extend = False )

Select markers on and left/right of the current frame

Parameters :

- mode ( Literal [ 'LEFT' , 'RIGHT' ] ) – Mode, (optional)

- extend ( bool ) – Extend Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## World Operators

### World Operators 

bpy.ops.world. convert_volume_to_mesh ( ) 

Recast the area of a realm to a surface. The realm's area was previously shown by EEVEE Legacy. Alteration is necessary for it to show properly

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/world.py:26

bpy.ops.world. new ( ) 

Build a fresh realm Information-Container

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## AnimVizMotionPaths(bpy_struct)

Controls for displaying motion trails of bones and objects.

base class — bpy_struct

class bpy.types. AnimVizMotionPaths ( bpy_struct )

Settings for motion path visualization and rendering.

bake_location

When calculating Bone Paths, use Head or Tips (default 'TAILS' )

Type :

Literal[Motionpath Bake Location Items]

frame_after

Number of frames to show after the current frame (only for 'Around Frame' Onion-skinning method) (in [1, 524287], default 0)

Type :

int

frame_before

Number of frames to show before the current frame (only for 'Around Frame' Onion-skinning method) (in [1, 524287], default 0)

Type :

int

frame_end

End frame of range of paths to display/calculate (not for 'Around Frame' Onion-skinning method) (in [-inf, inf], default 0)

Type :

int

frame_start

Starting frame of range of paths to display/calculate (not for 'Around Frame' Onion-skinning method) (in [-inf, inf], default 0)

Type :

int

frame_step

Number of frames between paths shown (not for 'On Keyframes' Onion-skinning method) (in [1, 100], default 0)

Type :

int

has_motion_paths

Are there any bone paths that will need updating (read-only) (default False, readonly)

Type :

bool

range

Type of range to calculate for Motion Paths (default 'SCENE' )

Type :

Literal[Motionpath Range Items]

show_frame_numbers

Display frame numbers on Motion Paths (default False)

Type :

bool

show_keyframe_action_all

For bone motion paths, search whole Action for keyframes instead of in group with matching name only (is slower) (default False)

Type :

bool

show_keyframe_highlight

Emphasize position of keyframes on Motion Paths (default False)

Type :

bool

show_keyframe_numbers

Show frame numbers of Keyframes on Motion Paths (default False)

Type :

bool

type

Type of range to show for Motion Paths (default 'RANGE' )

Type :

Literal[Motionpath Display Type Items]

use_camera_space_bake

Motion path points will be baked into the camera space of the active camera. This means they will only look right when looking through that camera. Switching cameras using markers is not supported. (default False)

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| AnimViz.motion_path | |

## ArmatureModifier(Modifier)

Modifier for skeletal mesh deformation.

base classes — bpy_struct, Modifier

class bpy.types. ArmatureModifier ( Modifier )

Deform geometry using a bone system.

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

object

Armature object to deform with

Type :

Object

use_bone_envelopes

Bind Bone envelopes to armature modifier (default False)

Type :

bool

use_deform_preserve_volume

Deform rotation interpolation with quaternions (default False)

Type :

bool

use_multi_modifier

Use same input as previous modifier, and mix results using overall vgroup (default False)

Type :

bool

use_vertex_groups

Bind vertex groups to armature modifier (default True)

Type :

bool

vertex_group

Name of Vertex Group which determines influence of modifier per point (default "", never None)

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

## ArrayModifier(Modifier)

Modifier for creating object duplicates.

base classes — bpy_struct, Modifier

class bpy.types. ArrayModifier ( Modifier )

Copies geometry into an ordered pattern.

constant_offset_displace

Value for the distance between arrayed items (array of 3 items, in [-inf, inf], default (1.0, 0.0, 0.0))

Type :

mathutils.Vector

count

Number of duplicates to make (in [1, inf], default 2)

Type :

int

curve

Curve object to fit array length to

Type :

Object

end_cap

Mesh object to use as an end cap

Type :

Object

fit_length

Length to fit array within (in [0, inf], default 0.0)

Type :

float

fit_type

Array length calculation method (default '`FIXED_COUNT`' )

- `FIXED_COUNT`
Fixed Count – Duplicate the object a certain number of times.

- `FIT_LENGTH`
Fit Length – Duplicate the object as many times as fits in a certain length.

- `FIT_CURVE`
Fit Curve – Fit the duplicated objects to a curve.

Type :

Literal['`FIXED_COUNT`', '`FIT_LENGTH`', '`FIT_CURVE`']

merge_threshold

Limit below which to merge vertices (in [0, inf], default 0.01)

Type :

float

offset_object

Use the location and rotation of another object to determine the distance and rotational change between arrayed items

Type :

Object

offset_u

Amount to offset array UVs on the U axis (in [-1, 1], default 0.0)

Type :

float

offset_v

Amount to offset array UVs on the V axis (in [-1, 1], default 0.0)

Type :

float

relative_offset_displace

The size of the geometry will determine the distance between arrayed items (array of 3 items, in [-inf, inf], default (1.0, 0.0, 0.0))

Type :

mathutils.Vector

start_cap

Mesh object to use as a start cap

Type :

Object

use_constant_offset

Add a constant offset (default False)

Type :

bool

use_merge_vertices

Merge vertices in adjacent duplicates (default False)

Type :

bool

use_merge_vertices_cap

Merge vertices in first and last duplicates (default False)

Type :

bool

use_object_offset

Add another object's transformation to the total offset (default False)

Type :

bool

use_relative_offset

Add an offset relative to the object's bounding box (default True)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## AttributeGroupMesh(bpy_prop_collection)

Collection of geometry attributes on mesh.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AttributeGroupMesh ( bpy_prop_collection )

Container of per-element data channels.

active

Active attribute

Type :

Attribute

active_color

Active color attribute for display and editing

Type :

Attribute

active_color_index

Active color attribute index (in [-inf, inf], default 0)

Type :

int

active_color_name

The name of the active color attribute for display and editing (default "", never None)

Type :

str

active_index

Active attribute index or -1 when none are active (in [-1, inf], default 0)

Type :

int

default_color_name

The name of the default color attribute used as a fallback for rendering (default "", never None)

Type :

str

render_color_index

The index of the color attribute used as a fallback for rendering (in [-inf, inf], default 0)

Type :

int

new ( name , type , domain )

Attach an attribute to geometry.

Parameters :

- name ( str ) – Name, Name of geometry attribute (never None)

- type (Literal[Attribute Type Items]) – Type, Attribute type

- domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

New geometry attribute

Return type :

Attribute

remove ( attribute )

Detach an attribute from geometry.

Parameters :

attribute (Attribute) – Geometry Attribute (never None)

domain_size ( domain )

Get the number of elements in a domain.

Parameters :

domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

Size, Size of the domain (in [0, inf])

Return type :

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

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| Mesh.attributes | Mesh.color_attributes |

## BlendDataCameras(bpy_prop_collection)

Enumeration of object grouping containers.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataCollections ( bpy_prop_collection )

List of object group hierarchies

new ( name ) 

Register a collection in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New collection data-block

Return type :

Collection

remove ( collection , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a collection from the current file

Parameters :

- collection (Collection) – Collection to remove (never None)

- do_unlink ( bool ) – Break all references to this collection before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.collections | |

# Foreachgeometryelementzoneviewerpathelem Viewerpathelem, Function Bpy Struct, Gammacrossstrip Effectstrip, Gaussianblurstrip Effectstrip ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ForeachGeometryElementZoneViewerPathElem(ViewerPathElem); Function(bpy_struct); GammaCrossStrip(EffectStrip); GaussianBlurStrip(EffectStrip); GeometryAttributeConstraint(Constraint); Gizmo(bpy_struct).

## ForeachGeometryElementZoneViewerPathElem(ViewerPathElem)

### ForeachGeometryElementZoneViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. ForeachGeometryElementZoneViewerPathElem ( ViewerPathElem )

zone_output_node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |

## Function(bpy_struct)

### Function(bpy_struct) 

base class — bpy_struct

class bpy.types. Function ( bpy_struct ) 

The definition of an RNA function

description 

Text explaining what the function is for (default “”, readonly, never None)

Type :

str

identifier 

The unique name the function carries in code and scripting (default “”, readonly, never None)

Type :

str

is_registered 

Whether the function was registered as a callback during type registration (default False, readonly)

Type :

bool

is_registered_optional 

Whether the function was optionally registered as a callback during type registration (default False, readonly)

Type :

bool

parameters 

The arguments this function accepts (default None, readonly)

Type :

bpy_prop_collection[Property]

use_self 

The function omits itself as an argument, turning into a static method in Python (default False, readonly)

Type :

bool

use_self_type 

The function receives its own type as an argument, turning into a class method in Python when use_self is false (default False, readonly)

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

| Struct.functions | |

## GammaCrossStrip(EffectStrip)

### GammaCrossStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. GammaCrossStrip ( EffectStrip )

Gamma Crossfade Strip

input_1

The effect strip's first input (never None)

Type :

Strip

input_2

The effect strip's second input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## GaussianBlurStrip(EffectStrip)

### GaussianBlurStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. GaussianBlurStrip ( EffectStrip )

Sequence strip that applies a gaussian blur.

input_1

The effect strip's first input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

Type :

int

size_x

Extent of the blur on the X axis (in [0, inf], default 0.0)

Type :

float

size_y

Extent of the blur on the Y axis (in [0, inf], default 0.0)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## GeometryAttributeConstraint(Constraint)

### GeometryAttributeConstraint(Constraint)

base classes — bpy_struct, Constraint

class bpy.types. GeometryAttributeConstraint ( Constraint )

Sets up a constraint driven by an attribute read from geometry.

apply_target_transform

Stack the target object's world transform on top of the transform held by the attribute (default False)

Type :

bool

attribute_name

Which attribute supplies the transform (default "", never None)

Type :

str

data_type

Choose the attribute's data type (default 'VECTOR' )

- VECTOR
Vector – Vector data type, affects position.

- QUATERNION
Quaternion – Quaternion data type, affects rotation.

- FLOAT4X4
4x4 Matrix – 4x4 Matrix data type, affects transform.

Type :

Literal[‘VECTOR’, ‘QUATERNION’, ‘FLOAT4X4’]

domain

Attribute domain (default 'POINT' )

Type :

Literal[‘POINT’, ‘EDGE’, ‘FACE’, ‘`FACE_CORNER`’, ‘CURVE’, ‘INSTANCE’]

mix_loc

Mix Location (default False)

Type :

bool

mix_mode

Choose how the existing and copied transforms get blended (default 'REPLACE' )

- REPLACE
Replace – Substitute the attribute's transform in place of the original one.

- `BEFORE_FULL`
Before Original (Full) – Put the copied transform ahead of the original through plain matrix multiplication, as though the constraint target were a parent under Full Inherit Scale; rotation combined with non-uniform scale can introduce shear.

- `BEFORE_SPLIT`
Before Original (Split Channels) – Put the copied transform ahead of the original, treating location, rotation and scale on their own, much like three Copy constraints in a row.

- `AFTER_FULL`
After Original (Full) – Place the copied transform after the original through plain matrix multiplication, as though the constraint target were a child under Full Inherit Scale; rotation paired with non-uniform scale can introduce shear.

- `AFTER_SPLIT`
After Original (Split Channels) – Place the copied transform after the original, treating location, rotation and scale on their own, much like three Copy constraints in a row.

Type :

Literal[‘REPLACE’, ‘`BEFORE_FULL`’, ‘`BEFORE_SPLIT`’, ‘`AFTER_FULL`’, ‘`AFTER_SPLIT`’]

mix_rot

Mix Rotation (default False)

Type :

bool

mix_scl

Mix Scale (default False)

Type :

bool

sample_index

Sample Index (in [0, inf], default 0)

Type :

int

target

Target geometry object

Type :

Object

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

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## Gizmo(bpy_struct)

### Gizmo(bpy_struct)

base class — bpy_struct

class bpy.types. Gizmo ( bpy_struct )

Collection of gizmos

alpha

(in [0, 1], default 0.0)

Type :

float

alpha_highlight

(in [0, 1], default 0.0)

Type :

float

bl_idname

(default “”, never None)

Type :

str

color

(array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

color_highlight

(array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

group

The gizmo group that owns this gizmo (readonly)

Type :

GizmoGroup

hide

(default False)

Type :

bool

hide_keymap

Skip this gizmo’s key-map (default False)

Type :

bool

hide_select

(default False)

Type :

bool

is_highlight

(default False, readonly)

Type :

bool

is_modal

(default False, readonly)

Type :

bool

line_width

(in [0, inf], default 0.0)

Type :

float

matrix_basis

(multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_offset

(multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_space

(multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_world

(multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

properties

(readonly, never None)

Type :

GizmoProperties

scale_basis

(in [0, inf], default 0.0)

Type :

float

select

(default False)

Type :

bool

select_bias

Bias applied to depth during selection (in [-inf, inf], default 0.0)

Type :

float

use_draw_hover

(default False)

Type :

bool

use_draw_modal

Keep it visible during a drag (default False)

Type :

bool

use_draw_offset_scale

Apply scaling to the offset matrix, used for screen-space offsets (default False)

Type :

bool

use_draw_scale

Factor scale into the matrix calculation (default True)

Type :

bool

use_draw_value

While dragging, display a readout of the current value (default False)

Type :

bool

use_event_handle_all

While highlighted, hold events back so other keymaps never see them (default False)

Type :

bool

use_grab_cursor

(default False)

Type :

bool

use_operator_tool_properties

On activation, fold in the active tool’s properties without clobbering existing ones (default False)

Type :

bool

use_select_background

Leave the depth buffer untouched (default False)

Type :

bool

use_tooltip

Surface tooltips when the pointer hovers this gizmo (default True)

Type :

bool

use_undo

Record an undo step every time the gizmo is used (default False)

Type :

bool

draw ( context )

Parameters :

context (Context) – (never None)

draw_select ( context , * , select_id = 0 )

Parameters :

- context (Context) – (never None)

- select_id ( int ) – (in [0, inf], optional)

test_select ( context , location )

Parameters :

- context (Context) – (never None)

- location ( Sequence [ int ] ) – Location, Region coordinates (array of 2 items, in [-inf, inf], never None)

Returns :

Use -1 to skip this gizmo (in [-1, inf])

Return type :

int

modal ( context , event , tweak )

Parameters :

- context (Context) – (never None)

- event (Event) – (never None)

- tweak ( set [ Literal [ 'PRECISE' , 'SNAP' ] ] ) – Tweak

Returns :

result

Return type :

set[Literal[Operator Return Items]]

setup ( )

invoke ( context , event )

Parameters :

- context (Context) – (never None)

- event (Event) – (never None)

Returns :

result

Return type :

set[Literal[Operator Return Items]]

exit ( context , cancel )

Parameters :

- context (Context) – (never None)

- cancel ( bool ) – Cancel, otherwise confirm

select_refresh ( )

draw_preset_box ( matrix , * , select_id = -1 )

Draw a box

Parameters :

- matrix (mathutils.Matrix) – The transform matrix to apply (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- select_id ( int ) – The id for a selectable gizmo; pass -1 if it is not being selected., (in [-1, inf], optional)

draw_preset_arrow ( matrix , * , axis = '`POS_Z`' , select_id = -1 )

Draw a box

Parameters :

- matrix (mathutils.Matrix) – The transform matrix to apply (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- axis (Literal[Object Axis Items]) – Arrow Orientation (optional)

- select_id ( int ) – The id for a selectable gizmo; pass -1 if it is not being selected., (in [-1, inf], optional)

draw_preset_circle ( matrix , * , axis = '`POS_Z`' , select_id = -1 )

Draw a box

Parameters :

- matrix (mathutils.Matrix) – The transform matrix to apply (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- axis (Literal[Object Axis Items]) – Arrow Orientation (optional)

- select_id ( int ) – The id for a selectable gizmo; pass -1 if it is not being selected., (in [-1, inf], optional)

target_set_prop ( target , data , property , * , index = -1 )

Parameters :

- target ( str ) – Target property (never None)

- data (AnyType) – The source the property is read from (never None)

- property ( str ) – Identifier of property in data (never None)

- index ( int ) – (in [-1, inf], optional)

target_set_operator ( operator , * , index = 0 )

The operator fired when the gizmo activates; this takes priority over any property targets.

Parameters :

- operator ( str ) – Target operator (never None)

- index ( int ) – Part index, (in [0, 255], optional)

Returns :

Operator properties to fill in

Return type :

OperatorProperties

target_is_valid ( property )

Parameters :

property ( str ) – Property identifier (never None)

Return type :

bool

draw_custom_shape ( shape , * , matrix = None , select_id = None )

Renders a shape that was built by Gizmo.draw_custom_shape.

Parameters :

- shape ( Any ) – The previously cached shape that gets drawn.

- matrix (mathutils.Matrix | None) – A 4x4 matrix; if omitted, Gizmo.matrix_world stands in.

- select_id ( int | None ) – The selection id.
Only use when drawing within Gizmo.draw_select.

static new_custom_shape ( type , verts )

Builds a fresh shape suitable for handing to Gizmo.draw_custom_shape.

Parameters :

- type ( Literal [ 'POINTS' , 'LINES' , 'TRIS' , '`LINE_STRIP`' ] ) – The type of shape to create.

- verts ( Sequence [ Sequence [ float ] ] ) – Sequence of 2D or 3D coordinates.

Returns :

The freshly built shape (its return type may change later).

Return type :

Any

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

target_get_range ( target )

Reads back the allowed range for the given target property.

Parameters :

target – Target property name.

Returns :

A (min, max) pair giving the property’s range.

Return type :

tuple[float, float]

target_get_value ( target )

Reads back the current value held by the given target property.

Parameters :

target ( str ) – Target property name.

Returns :

Depending on the target type, either a single value or an array holding the property’s value.

Return type :

float | tuple[float, …]

target_set_handler ( target , get , set , range = None )

Wires up callback functions for one of a gizmo’s properties.

Parameters :

- target ( str ) – Target property name.

- get ( Callable [ [ ] , float | Sequence [ float ] ] ) – Callback yielding this property’s value, as either one number or a sequence.

- set ( Callable [ [ tuple [ float , ... ] ] , Any ] ) – Callback receiving one value argument and writing it back.

- range ( Callable [ [ ] , tuple [ float , float ] ] | None ) – Callback yielding a (min, max) pair for range-based gizmos; whatever it returns is ignored.

target_set_value ( target )

Writes a new value into the given target property.

Parameters :

target ( str ) – Target property name.

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| GizmoGroup.gizmos GizmoGroup.invoke_prepare | Gizmos.new Gizmos.remove |

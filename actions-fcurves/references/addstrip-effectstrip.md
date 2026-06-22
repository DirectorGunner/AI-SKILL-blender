# Addstrip Effectstrip, Adjustmentstrip Effectstrip, Alphaoverstrip Effectstrip, Alphaunderstrip Effectstrip ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: AddStrip(EffectStrip); AdjustmentStrip(EffectStrip); AlphaOverStrip(EffectStrip); AlphaUnderStrip(EffectStrip); AnimDataDrivers(bpy_prop_collection); AnimViz(bpy_struct); AnnotationFrame(bpy_struct); AnnotationFrames(bpy_prop_collection).

## AddStrip(EffectStrip)

### AdjustmentStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types.AdjustmentStrip(EffectStrip)

A sequence strip that applies filter adjustments to underlying layers

animation_offset_end

Animation stop offset (trim end) ([0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by '.content_trim_end'.

Type: int

animation_offset_start

Animation start offset (trim start) ([0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by '.content_trim_start'.

Type: int

content_trim_end

Number of frames to discard from the end of the underlying source. The source content is reduced, and future frames become static ([0, inf], default 0)

Type: int

content_trim_start

Number of frames to discard from the start of the underlying source. The source content is reduced, and previous frames become static ([0, inf], default 0)

Type: int

input_count

([0, inf], default 0, readonly)

Type: int

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## AdjustmentStrip(EffectStrip)

### AlphaOverStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types.AlphaOverStrip(EffectStrip)

Alpha Over Strip

input_1

The initial contribution to the effect strip (never None)

Type: Strip

input_2

The secondary contribution to the effect strip (never None)

Type: Strip

input_count

([0, inf], default 0, readonly)

Type: int

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## AlphaOverStrip(EffectStrip)

### AlphaUnderStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types.AlphaUnderStrip(EffectStrip)

Alpha Under Strip

input_1

The initial contribution to the effect strip (never None)

Type: Strip

input_2

The secondary contribution to the effect strip (never None)

Type: Strip

input_count

([0, inf], default 0, readonly)

Type: int

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## AlphaUnderStrip(EffectStrip)

### AnimData(bpy_struct)

base class — bpy_struct

class bpy.types.AnimData(bpy_struct)

Animation data associated with a data-block

action

Current Action for this data-block

Type: Action

action_blend_type

Approach for merging the Active Action's result with NLA stack output (default 'REPLACE')

- REPLACE
Replace – Stack values replace accumulated results based on influence.

- COMBINE
Combine – Stack values integrate with accumulated results using addition, multiplication, or quaternion operations per channel type.

- ADD
Add – Weighted stack result is summed with accumulated results.

- SUBTRACT
Subtract – Weighted stack result is subtracted from accumulated results.

- MULTIPLY
Multiply – Weighted stack result is multiplied into accumulated results.

Type: Literal['REPLACE', 'COMBINE', 'ADD', 'SUBTRACT', 'MULTIPLY']

action_extrapolation

Behavior past the Active Action's span (when evaluating with NLA) (default 'HOLD')

- NOTHING
Nothing – Stack has no effect outside its boundaries.

- HOLD
Hold – Maintain the first frame if no prior strips exist in the track, and always maintain the last frame.

- `HOLD_FORWARD`
Hold Forward – Maintain the last frame only.

Type: Literal['NOTHING', 'HOLD', '`HOLD_FORWARD`']

action_influence

Weight applied to the Active Action's contribution to the NLA stack result ([0, 1], default 1.0)

Type: float

action_slot

The slot that determines which subset of the Action is used by this data-block; its name locates the correct slot when a different Action is assigned

Type: ActionSlot

action_slot_handle

A number that determines which subset of the Action is used by this data-block ([-inf, inf], default 0)

Type: int

action_slot_handle_tweak_storage

A temporary holder for the main action slot during tweak mode ([-inf, inf], default 0)

Type: int

action_suitable_slots

The set of slots within this animation data-block (default None, readonly)

Type: bpy_prop_collection[ActionSlot]

action_tweak_storage

A temporary holder for the main action during tweak mode

Type: Action

drivers

The Drivers/Expressions assigned to this data-block (default None, readonly)

Type: AnimDataDrivers[FCurve]

last_slot_identifier

The identifier of the most recently assigned action slot. The slot that determines which subset of the Action is used by this data-block, and its identifier is used to locate the correct slot when a different Action is assigned. (default "", never None)

Type: str

nla_tracks

NLA Tracks (animation Layers) (default None, readonly)

Type: NlaTracks[NlaTrack]

use_nla

The NLA stack is evaluated when processing this block (default True)

Type: bool

use_pin

(default False)

Type: bool

use_tweak_mode

Whether to turn on or off tweak mode in NLA (default False)

Type: bool

nla_tweak_strip_time_to_scene(frame, *, invert=False)

Translate a time from the tweaked strip's local time to scene time, exactly like built-in key editing tools. Leaves time unchanged if not in tweak mode.

Parameters:

- frame (float) – Input time ([-1.04857e+06, 1.04857e+06])

- invert (bool) – Invert, Translate scene time to action time (optional)

Returns: Translated time ([-1.04857e+06, 1.04857e+06])

Return type: float

fix_paths_rename_all(*, prefix='', old_name='', new_name='')

Update the property paths in the animation system, since properties are animated through string paths, updates are necessary to keep them valid after properties are renamed

Parameters:

- prefix (str) – Prefix, Name prefix (optional, never None)

- old_name (str) – Old Name, Old name (optional, never None)

- new_name (str) – New Name, New name (optional, never None)

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Annotation.animation_data Armature.animation_data CacheFile.animation_data Camera.animation_data Curve.animation_data Curves.animation_data FreestyleLineStyle.animation_data GreasePencil.animation_data ID.animation_data_create Key.animation_data Lattice.animation_data Light.animation_data LightProbe.animation_data Mask.animation_data | Material.animation_data Mesh.animation_data MetaBall.animation_data MovieClip.animation_data NodeTree.animation_data Object.animation_data ParticleSettings.animation_data PointCloud.animation_data Scene.animation_data Speaker.animation_data Texture.animation_data Volume.animation_data World.animation_data |

## AnimDataDrivers(bpy_prop_collection)

Stores F-Curves that drive animation values.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AnimDataDrivers ( bpy_prop_collection )

Mechanism for storing driven animation curves.

new ( data_path , * , index = 0 )

Create a new driven F-Curve.

Parameters :

- data_path ( str ) – Data Path, F-Curve data path to use (never None)

- index ( int ) – Index, Array index (in [0, inf], optional)

Returns :

Newly Driver F-Curve

Return type :

FCurve

remove ( driver )

Delete a driven curve.

Parameters :

driver (FCurve) – (never None)

from_existing ( * , src_driver = None )

Create a new driven curve based on an existing one.

Parameters :

src_driver (FCurve) – Existing Driver F-Curve to use as template for a new one (optional)

Returns :

New Driver F-Curve

Return type :

FCurve

find ( data_path , * , index = 0 )

Locate a driven F-Curve via linear search across all driver curves.

Parameters :

- data_path ( str ) – Data Path, F-Curve data path (never None)

- index ( int ) – Index, Array index (in [0, inf], optional)

Returns :

The found F-Curve, or None if it doesn't exist

Return type :

FCurve

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

| AnimData.drivers | |

## AnimViz(bpy_struct)

Settings controlling display of moving objects.

base class — bpy_struct

class bpy.types. AnimViz ( bpy_struct )

Settings for movement visualization.

motion_path

Settings governing motion path visualization (readonly, never None)

Type :

AnimVizMotionPaths

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

| Object.animation_visualization Pose.animation_visualization |

## AnnotationFrame(bpy_struct)

A single drawn frame within an annotation layer.

base class — bpy_struct

class bpy.types. AnnotationFrame ( bpy_struct )

Set of sketches on a single frame.

frame_number

The frame on which this sketch appears (in [-1048574, 1048574], default 0)

Type :

int

select

Frame is selected for editing in the Dope Sheet (default False)

Type :

bool

strokes

Freehand curves defining the sketch on this frame (default None, readonly)

Type :

bpy_prop_collection[AnnotationStroke]

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

| AnnotationFrames.copy AnnotationFrames.copy AnnotationFrames.new | AnnotationFrames.remove AnnotationLayer.active_frame AnnotationLayer.frames |

## AnnotationFrames(bpy_prop_collection)

Container of frames within an annotation layer.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AnnotationFrames ( bpy_prop_collection )

Collection of frames in an annotation layer.

new ( frame_number , * , active = False )

Instantiate a new annotation frame.

Parameters :

- frame_number ( int ) – Frame Number, The frame on which this sketch appears (in [-1048574, 1048574])

- active ( bool ) – Active, (optional)

Returns :

The newly created frame

Return type :

AnnotationFrame

remove ( frame )

Delete an annotation frame.

Parameters :

frame (AnnotationFrame) – Frame, The frame to remove (never None)

copy ( source )

Duplicate an annotation frame.

Parameters :

source (AnnotationFrame) – Source, The source frame (never None)

Returns :

The newly copied frame

Return type :

AnnotationFrame

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

| AnnotationLayer.frames | |

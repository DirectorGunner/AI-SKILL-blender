# Metaelement Bpy Struct, Metastrip Strip, Modifierviewerpathelem Viewerpathelem, Motionpath Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MetaElement(bpy_struct); MetaStrip(Strip); ModifierViewerPathElem(ViewerPathElem); MotionPath(bpy_struct); MotionPathVert(bpy_struct); MovieClipScopes(bpy_struct); MovieClipStrip(Strip); MovieStrip(Strip).

## MetaElement(bpy_struct)

### MetaElement(bpy_struct)

base class — bpy_struct

class bpy.types. MetaElement ( bpy_struct )

One blobby component within a metaball data-block

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

hide

Hide element (default False)

Type :

bool

radius

(in [0, inf], default 0.0)

Type :

float

rotation

Normalized quaternion rotation (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

select

Select element (default False)

Type :

bool

size_x

Size of element, use of components depends on element type (in [0, 20], default 0.0)

Type :

float

size_y

Size of element, use of components depends on element type (in [0, 20], default 0.0)

Type :

float

size_z

Size of element, use of components depends on element type (in [0, 20], default 0.0)

Type :

float

stiffness

Stiffness defines how much of the element to fill (in [0, 10], default 0.0)

Type :

float

type

Metaball type (default 'BALL' )

Type :

Literal[Metaelem Type Items]

use_negative

Set metaball as negative one (default False)

Type :

bool

use_scale_stiffness

Scale stiffness instead of radius (default True)

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

| MetaBall.elements MetaBallElements.active | MetaBallElements.new MetaBallElements.remove |

## MetaStrip(Strip)

### MetaStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. MetaStrip ( Strip )

A sequence strip that bundles other strips together so they act as one

alpha_mode

How the alpha channel is encoded within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – RGB channels in transparent pixels are unaffected by the alpha channel.

- PREMUL
Premultiplied – RGB channels in transparent pixels are multiplied by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

Animation end offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Animation start offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

channels

(default None, readonly)

Type :

bpy_prop_collection[SequenceTimelineChannel]

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Adjust the intensity of the input’s color (in [0, 20], default 1.0)

Type :

float

content_trim_end

Count of frames to skip at the end of the underlying source; the source content gets trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Count of frames to skip at the start of the underlying source; the source content gets trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

multiply_alpha

Multiply alpha along with color channels (default False)

Type :

bool

proxy

(readonly)

Type :

StripProxy

strips

Strips nested in meta strip (default None, readonly)

Type :

StripsMeta[Strip]

strobe

Only display every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_deinterlace

Remove fields from video movies (default False)

Type :

bool

use_flip_x

Flip on the X axis (default False)

Type :

bool

use_flip_y

Flip on the Y axis (default False)

Type :

bool

use_float

Convert input to float data (default False)

Type :

bool

use_proxy

Use a preview proxy and/or time-code index for this strip (default False)

Type :

bool

use_reverse_frames

Reverse frame order (default False)

Type :

bool

volume

Playback volume of the sound (in [0, 100], default 1.0)

Type :

float

separate ( )

Separate meta

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## ModifierViewerPathElem(ViewerPathElem)

### ModifierViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. ModifierViewerPathElem ( ViewerPathElem )

modifier_uid

Persistent UID belonging to the modifier (in [-inf, inf], default 0)

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

## MotionPath(bpy_struct)

### MotionPath(bpy_struct)

base class — bpy_struct

class bpy.types. MotionPath ( bpy_struct )

Stored world-space locations of an element sampled across a span of frames

color

Personalized color used for the motion path on frames before the current one (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

color_post

Personalized color used for the motion path on frames after the current one (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

frame_end

Last frame of the cached span (in [-inf, inf], default 0, readonly)

Type :

int

frame_start

First frame of the cached span (in [-inf, inf], default 0, readonly)

Type :

int

is_modified

Whether the path is currently being edited (default False)

Type :

bool

length

How many frames are held in the cache (in [-inf, inf], default 0, readonly)

Type :

int

line_thickness

Thickness of the drawn motion-path line (in [1, 6], default 0)

Type :

int

lines

Draw straight segments connecting keyframe points (default False)

Type :

bool

points

Per-frame positions held in the cache (default None, readonly)

Type :

bpy_prop_collection[MotionPathVert]

use_bone_head

On PoseBone paths, base the computation on the bone's head position (default False, readonly)

Type :

bool

use_custom_color

Apply a personalized color to this motion path (default False)

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

| Object.motion_path | PoseBone.motion_path |

## MotionPathVert(bpy_struct)

### MotionPathVert(bpy_struct)

base class — bpy_struct

class bpy.types. MotionPathVert ( bpy_struct )

A single cached position along the path

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

select

Whether this path point is picked for editing (default False)

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

| MotionPath.points | |

## MovieClipScopes(bpy_struct)

### MovieClipScopes(bpy_struct)

base class — bpy_struct

class bpy.types. MovieClipScopes ( bpy_struct )

Scope displays for inspecting a movie clip statistically

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

| SpaceClipEditor.scopes | |

## MovieClipStrip(Strip)

### MovieClipStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. MovieClipStrip ( Strip )

Sequencer strip that pulls a video in from the clip editor

alpha_mode

How alpha is stored within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – RGB channels in transparent pixels are unaffected by the alpha channel.

- PREMUL
Premultiplied – RGB channels in transparent pixels are multiplied by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

End-side animation offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Start-side animation offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

clip

Movie clip that this strip draws from

Type :

MovieClip

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Tune how strong the input's color appears (in [0, 20], default 1.0)

Type :

float

content_trim_end

Count of frames discarded at the end of the underlying source; the source is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Count of frames discarded at the start of the underlying source; the source is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

fps

Frames per second (in [-inf, inf], default 0.0, readonly)

Type :

float

multiply_alpha

Scale alpha alongside the color channels (default False)

Type :

bool

stabilize2d

Draw from the 2D-stabilized variant of the clip (default False)

Type :

bool

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

undistort

Draw from the undistorted variant of the clip (default False)

Type :

bool

use_deinterlace

Strip fields out of interlaced video footage (default False)

Type :

bool

use_flip_x

Mirror across the X axis (default False)

Type :

bool

use_flip_y

Mirror across the Y axis (default False)

Type :

bool

use_float

Convert the input into float data (default False)

Type :

bool

use_reverse_frames

Play the frames back in reverse (default False)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## MovieStrip(Strip)

### MovieStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. MovieStrip ( Strip )

Sequencer strip that loads a video

alpha_mode

How alpha is stored within the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – RGB channels in transparent pixels are unaffected by the alpha channel.

- PREMUL
Premultiplied – RGB channels in transparent pixels are multiplied by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

End-side animation offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Start-side animation offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Tune how strong the input's color appears (in [0, 20], default 1.0)

Type :

float

colorspace_settings

Settings for the input color space (readonly)

Type :

ColorManagedInputColorspaceSettings

content_trim_end

Count of frames discarded at the end of the underlying source; the source is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Count of frames discarded at the start of the underlying source; the source is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

elements

(default None, readonly)

Type :

bpy_prop_collection[StripElement]

filepath

(default “”, never None, blend relative // prefix supported)

Type :

str

fps

Frames per second (in [-inf, inf], default 0.0, readonly)

Type :

float

multiply_alpha

Scale alpha alongside the color channels (default False)

Type :

bool

proxy

(readonly)

Type :

StripProxy

retiming_keys

(default None, readonly)

Type :

RetimingKeys[RetimingKey]

stereo_3d_format

Configuration for stereo 3D (readonly, never None)

Type :

Stereo3dFormat

stream_index

When a file holds multiple movie streams, pick the one at this index (in [0, 20], default 0)

Type :

int

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_deinterlace

Strip fields out of interlaced video footage (default False)

Type :

bool

use_flip_x

Mirror across the X axis (default False)

Type :

bool

use_flip_y

Mirror across the Y axis (default False)

Type :

bool

use_float

Convert the input into float data (default False)

Type :

bool

use_multiview

Use Multiple Views (when available) (default False)

Type :

bool

use_proxy

Enable a preview proxy and/or timecode index for this strip (default False)

Type :

bool

use_reverse_frames

Play the frames back in reverse (default False)

Type :

bool

views_format

How movie views get loaded (default 'INDIVIDUAL' )

Type :

Literal[Views Format Items]

reload_if_needed ( )

reload_if_needed

Returns :

True if the strip can produce frames, False otherwise

Return type :

bool

metadata ( )

Retrieve metadata of the movie file

Returns :

Dict-like object containing the metadata

Return type :

IDPropertyWrapPtr

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

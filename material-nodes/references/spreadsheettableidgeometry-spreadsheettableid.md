# Spreadsheettableidgeometry Spreadsheettableid, Stereo3Ddisplay Bpy Struct, Stereo3Dformat Bpy Struct, Strip Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpreadsheetTableIDGeometry(SpreadsheetTableID); Stereo3dDisplay(bpy_struct); Stereo3dFormat(bpy_struct); Strip(bpy_struct); StripProxy(bpy_struct).

## SpreadsheetTableIDGeometry(SpreadsheetTableID)

### SpreadsheetTableIDGeometry(SpreadsheetTableID)

base classes — bpy_struct, SpreadsheetTableID

class bpy.types. SpreadsheetTableIDGeometry ( SpreadsheetTableID )

attribute_domain

The attribute domain that is shown (default 'POINT' , readonly)

Type :

Literal[Attribute Domain Items]

geometry_component_type

Which portion of the geometry supplies the displayed data (default 'MESH' , readonly)

Type :

Literal[Geometry Component Type Items]

geometry_item_type

Item Type (default 'DOMAIN' , readonly)

- DOMAIN
Domain – Data on a domain.

- BUNDLE
Bundle – Data on a bundle.

Type :

Literal[‘DOMAIN’, ‘BUNDLE’]

layer_index

Which Grease Pencil layer this indexes (in [-inf, inf], default 0, readonly)

Type :

int

object_eval_state

(default 'EVALUATED' , readonly)

- EVALUATED
Evaluated – Pull data from an object that is fully or partially evaluated.

- ORIGINAL
Original – Pull data from the original object, with no modifiers in effect.

- `VIEWER_NODE`
Viewer Node – Pull intermediate data from the viewer node.

Type :

Literal[‘EVALUATED’, ‘ORIGINAL’, ‘`VIEWER_NODE`’]

viewer_path

Path leading to the data being shown (readonly)

Type :

ViewerPath

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | SpreadsheetTableID.type |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values SpreadsheetTableID.bl_rna_get_subclass SpreadsheetTableID.bl_rna_get_subclass_py |

## Stereo3dDisplay(bpy_struct)

### Stereo3dDisplay(bpy_struct)

base class — bpy_struct

class bpy.types. Stereo3dDisplay ( bpy_struct )

Configuration for showing stereo 3D

anaglyph_type

(default '`RED_CYAN`' )

Type :

Literal[Stereo3D Anaglyph Type Items]

display_mode

(default 'ANAGLYPH' )

Type :

Literal[Stereo3D Display Items]

interlace_type

(default '`ROW_INTERLEAVED`' )

Type :

Literal[Stereo3D Interlace Type Items]

use_interlace_swap

Exchange the left and right stereo channels (default False)

Type :

bool

use_sidebyside_crosseyed

Have the right eye view the left image and the other way around (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Window.stereo_3d_display | |

## Stereo3dFormat(bpy_struct)

### Stereo3dFormat(bpy_struct)

base class — bpy_struct

class bpy.types. Stereo3dFormat ( bpy_struct )

Configuration for stereo output

anaglyph_type

(default '`RED_CYAN`' )

Type :

Literal[Stereo3D Anaglyph Type Items]

display_mode

(default 'ANAGLYPH' )

- ANAGLYPH
Anaglyph – Output the left and right eye views as two color-filtered layers within one image (you need anaglyph glasses).

- INTERLACE
Interlace – Output the left and right eye views interlaced inside one image (you need a 3D-ready monitor).

- SIDEBYSIDE
Side-by-Side – Place the left and right eye views next to each other.

- TOPBOTTOM
Top-Bottom – Stack the left and right eye views, one above the other.

Type :

Literal[‘ANAGLYPH’, ‘INTERLACE’, ‘SIDEBYSIDE’, ‘TOPBOTTOM’]

interlace_type

(default '`ROW_INTERLEAVED`' )

Type :

Literal[Stereo3D Interlace Type Items]

use_interlace_swap

Exchange the left and right stereo channels (default False)

Type :

bool

use_sidebyside_crosseyed

Have the right eye view the left image and the other way around (default False)

Type :

bool

use_squeezed_frame

Merge the two views into one squeezed image (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Image.stereo_3d_format ImageStrip.stereo_3d_format MovieStrip.stereo_3d_format | ImageFormatSettings.stereo_3d_format UILayout.template_image_stereo_3d |

## Strip(bpy_struct)

### Strip(bpy_struct)

base class — bpy_struct

subclasses —
EffectStrip, ImageStrip, MaskStrip, MetaStrip, MovieClipStrip, MovieStrip, SceneStrip, SoundStrip

class bpy.types. Strip ( bpy_struct )

One holder for a piece of media in the Video Sequence Editor.

blend_alpha

Percentage of how much the strip’s colors affect other strips (in [0, 1], default 1.0)

Type :

float

blend_type

Determines the way this strip is mixed with the others (default '`ALPHA_OVER`' )

Type :

Literal[‘REPLACE’, ‘CROSS’, ‘DARKEN’, ‘MULTIPLY’, ‘BURN’, ‘`LINEAR_BURN`’, ‘LIGHTEN’, ‘SCREEN’, ‘DODGE’, ‘ADD’, ‘OVERLAY’, ‘`SOFT_LIGHT`’, ‘`HARD_LIGHT`’, ‘`VIVID_LIGHT`’, ‘`LINEAR_LIGHT`’, ‘`PIN_LIGHT`’, ‘DIFFERENCE’, ‘EXCLUSION’, ‘SUBTRACT’, ‘HUE’, ‘SATURATION’, ‘COLOR’, ‘VALUE’, ‘`ALPHA_OVER`’, ‘`ALPHA_UNDER`’, ‘`GAMMA_CROSS`’]

channel

Vertical position of the strip (in [1, 128], default 0)

Type :

int

color_tag

Color tag for a strip (default '`COLOR_01`' )

Type :

Literal[Strip Color Items]

content_duration

Frame count of the source behind the strip, with handles left out (in [1, 1048574], default 0, readonly)

Type :

int

content_end

Timeline frame where underlying strip source ends (in [-inf, inf], default 0, readonly)

Type :

int

content_start

Timeline frame where underlying strip source begins (in [-inf, inf], default 0.0)

Type :

float

duration

How many frames the strip spans, measured between its left and right handles (in [-inf, inf], default 0)

Type :

int

effect_fader

Custom fade value (in [0, 1], default 0.0)

Type :

float

frame_duration

How long this strip’s contents run before handles are taken into account (in [1, 1048574], default 0, readonly)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_duration’.

Type :

int

frame_final_duration

How long this strip’s contents run once the handles have been applied (in [-inf, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.duration’.

Type :

int

frame_final_end

The end frame shown in the sequence editor after offsets take effect (in [-inf, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.right_handle’.

Type :

int

frame_final_start

The start frame shown in the sequence editor once offsets are applied; assigning here is the same as nudging the handle rather than the real start frame (in [-inf, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.left_handle’.

Type :

int

frame_offset_end

Offset from the end of the strip in frames (in [-inf, inf], default 0.0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.right_handle_offset’.

Type :

float

frame_offset_start

Offset from the start of the strip in frames (in [-inf, inf], default 0.0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.left_handle_offset’.

Type :

float

frame_start

X position where the strip begins (in [-inf, inf], default 0.0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_start’.

Type :

float

left_handle

Timeline frame at the left handle, which also marks where the strip starts (in [-inf, inf], default 0)

Type :

int

left_handle_offset

How far rightward the left handle sits, in frames, from where the strip content begins (in [-inf, inf], default 0.0)

Type :

float

lock

Lock strip so that it cannot be transformed (default False)

Type :

bool

modifiers

Modifiers affecting this strip (default None, readonly)

Type :

StripModifiers[StripModifier]

mute

Disable strip so that it does not contribute any output (default False)

Type :

bool

name

(default “”, never None)

Type :

str

right_handle

Timeline frame at the right handle, the first frame on which the strip stops feeding the output (in [-inf, inf], default 0)

Type :

int

right_handle_offset

How far leftward the right handle sits, in frames, from where the strip content ends (in [-inf, inf], default 0.0)

Type :

float

select

Whether the strip is selected (default False)

Type :

bool

select_left_handle

Whether the left handle is selected (default False)

Type :

bool

select_right_handle

Whether the right handle is selected (default False)

Type :

bool

show_retiming_keys

Show retiming keys, so they can be moved (default False)

Type :

bool

type

(default 'IMAGE' , readonly)

Type :

Literal[‘IMAGE’, ‘META’, ‘SCENE’, ‘MOVIE’, ‘MOVIECLIP’, ‘MASK’, ‘SOUND’, ‘CROSS’, ‘ADD’, ‘SUBTRACT’, ‘`ALPHA_OVER`’, ‘`ALPHA_UNDER`’, ‘`GAMMA_CROSS`’, ‘MULTIPLY’, ‘WIPE’, ‘GLOW’, ‘COLOR’, ‘SPEED’, ‘MULTICAM’, ‘ADJUSTMENT’, ‘`GAUSSIAN_BLUR`’, ‘TEXT’, ‘COLORMIX’]

use_default_fade

Apply a fade with the built-in default, which generally stretches the transition to match the effect strip length (default False)

Type :

bool

use_linear_modifiers

Compute modifiers in linear space rather than the sequencer’s own space (default False)

Type :

bool

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. A back door into runtime-defined RNA storage meant only for tests and debugging. Steer clear of it in normal scripts, and never count on the data it exposes being writable

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The root container of the system properties, or None when this data holds none yet and creation was not asked for

Return type :

PropertyGroup

strip_elem_from_frame ( frame )

Return the strip element from a given frame or None

Parameters :

frame ( int ) – Frame, The frame to get the strip element from (in [-1048574, 1048574])

Returns :

strip element of the current frame

Return type :

StripElement

swap ( other )

Swap the position of this strip with another

Parameters :

other (Strip) – Other, Other strip to swap with (never None)

move_to_meta ( meta_sequence )

Move this strip into a meta Strip

Parameters :

meta_sequence (Strip) – Destination Meta Strip, Meta to move the strip into (never None)

parent_meta ( )

Returns parent meta Strip

Returns :

Parent meta strip

Return type :

Strip

invalidate_cache ( type )

Invalidate cached images for strip and all dependent strips

Parameters :

type ( Literal [ 'RAW' , 'COMPOSITE' ] ) – Type, Cache Type (never None)

split ( frame , split_method , * , ignore_connections = False )

Split Strip

Parameters :

- frame ( int ) – Frame where to split the strip (in [-inf, inf])

- split_method ( Literal [ 'SOFT' , 'HARD' ] ) – (never None)

- ignore_connections ( bool ) – Don’t propagate split to connected strips (optional)

Returns :

Right side Strip

Return type :

Strip

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

| bpy.context.active_strip bpy.context.selected_editable_strips bpy.context.selected_strips bpy.context.strip bpy.context.strips AddStrip.input_1 AddStrip.input_2 AlphaOverStrip.input_1 AlphaOverStrip.input_2 AlphaUnderStrip.input_1 AlphaUnderStrip.input_2 ColorMixStrip.input_1 ColorMixStrip.input_2 CrossStrip.input_1 CrossStrip.input_2 GammaCrossStrip.input_1 GammaCrossStrip.input_2 GaussianBlurStrip.input_1 GlowStrip.input_1 MetaStrip.strips MultiplyStrip.input_1 MultiplyStrip.input_2 SequenceEditor.active_strip SequenceEditor.display_stack SequenceEditor.meta_stack SequenceEditor.strips SequenceEditor.strips_all SpeedControlStrip.input_1 Strip.move_to_meta Strip.parent_meta | Strip.split Strip.swap StripModifier.input_mask_strip StripsMeta.new_clip StripsMeta.new_effect StripsMeta.new_effect StripsMeta.new_effect StripsMeta.new_image StripsMeta.new_mask StripsMeta.new_meta StripsMeta.new_movie StripsMeta.new_scene StripsMeta.new_sound StripsMeta.remove StripsTopLevel.new_clip StripsTopLevel.new_effect StripsTopLevel.new_effect StripsTopLevel.new_effect StripsTopLevel.new_image StripsTopLevel.new_mask StripsTopLevel.new_meta StripsTopLevel.new_movie StripsTopLevel.new_scene StripsTopLevel.new_sound StripsTopLevel.remove SubtractStrip.input_1 SubtractStrip.input_2 WipeStrip.input_1 WipeStrip.input_2 |

## StripProxy(bpy_struct)

### StripProxy(bpy_struct)

base class — bpy_struct

class bpy.types. StripProxy ( bpy_struct )

The proxy controls belonging to a sequence strip.

build_100

Build 100% proxy resolution (default False)

Type :

bool

build_25

Build 25% proxy resolution (default False)

Type :

bool

build_50

Build 50% proxy resolution (default False)

Type :

bool

build_75

Build 75% proxy resolution (default False)

Type :

bool

build_record_run

Build record run time code index (default False)

Type :

bool

directory

Location to store the proxy files (default “”, never None, blend relative // prefix supported)

Type :

str

filepath

Location of custom proxy file (default “”, never None, blend relative // prefix supported)

Type :

str

quality

Quality of proxies to build (in [0, 32767], default 0)

Type :

int

timecode

Method for reading the inputs timecode (default 'NONE' )

- NONE
None – Ignore generated timecodes, seek in movie stream based on calculated timestamp.

- `RECORD_RUN`
Record Run – Use the movie stream’s own timestamps when seeking, so scene and movie times line up as closely as possible.

- `RECORD_RUN_NO_GAPS`
Record Run No Gaps – Treat the movie as an image sequence, disregarding dropped or incomplete frames along with frame-rate shifts.

Type :

Literal[‘NONE’, ‘`RECORD_RUN`’, ‘`RECORD_RUN_NO_GAPS`’]

use_overwrite

Overwrite existing proxy files when building (default True)

Type :

bool

use_proxy_custom_directory

Use a custom directory to store data (default False)

Type :

bool

use_proxy_custom_file

Use a custom file to read proxy data from (default False)

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

| EffectStrip.proxy ImageStrip.proxy MetaStrip.proxy | MovieStrip.proxy SceneStrip.proxy |

## See also

- [Bpy Struct](bpy-struct.md)

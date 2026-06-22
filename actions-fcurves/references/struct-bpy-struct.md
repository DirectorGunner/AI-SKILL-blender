# Struct Bpy Struct, Subtractstrip Effectstrip, Textbox Bpy Struct, Textline Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Struct(bpy_struct); SubtractStrip(EffectStrip); TextBox(bpy_struct); TextLine(bpy_struct); Theme(bpy_struct); ThemeBoneColorSet(bpy_struct); ThemeClipEditor(bpy_struct); ThemeCollectionColor(bpy_struct); ThemeCommon(bpy_struct); ThemeCommonAnim(bpy_struct).

## Struct(bpy_struct)

### Struct(bpy_struct)

base class — bpy_struct

class bpy.types. Struct ( bpy_struct )

The RNA definition of a structure.

base

Struct definition this is derived from (readonly)

Type :

Struct

description

Description of the Struct’s purpose (default “”, readonly, never None)

Type :

str

functions

(default None, readonly)

Type :

bpy_prop_collection[Function]

identifier

Unique name used in the code and scripting (default “”, readonly, never None)

Type :

str

name

Human readable name (default “”, readonly, never None)

Type :

str

name_property

Property that gives the name of the struct (readonly)

Type :

StringProperty

nested

Struct in which this struct is always nested, and to which it logically belongs (readonly)

Type :

Struct

properties

Properties in the struct (default None, readonly)

Type :

bpy_prop_collection[Property]

property_tags

Tags that properties can use to influence behavior (default None, readonly)

Type :

bpy_prop_collection[EnumPropertyItem]

translation_context

Translation context of the struct’s name (default “”, readonly, never None)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlenderRNA.structs CollectionProperty.fixed_type PointerProperty.fixed_type | Property.srna Struct.base Struct.nested |

## SubtractStrip(EffectStrip)

### SubtractStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. SubtractStrip ( EffectStrip )

Subtract Strip

input_1

First input for the effect strip (never None)

Type :

Strip

input_2

Second input for the effect strip (never None)

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

## TextBox(bpy_struct)

### TextBox(bpy_struct)

base class — bpy_struct

class bpy.types. TextBox ( bpy_struct )

The bounding box used to lay out text.

height

(in [0, inf], default 0.0)

Type :

float

width

(in [0, inf], default 0.0)

Type :

float

x

(in [-inf, inf], default 0.0)

Type :

float

y

(in [-inf, inf], default 0.0)

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

| TextCurve.text_boxes | |

## TextLine(bpy_struct)

### TextLine(bpy_struct)

base class — bpy_struct

class bpy.types. TextLine ( bpy_struct )

A single line within a Text data-block.

body

The characters held on this line (default “”, never None)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Text.current_line Text.lines | Text.select_end_line |

## Theme(bpy_struct)

### Theme(bpy_struct)

base class — bpy_struct

class bpy.types. Theme ( bpy_struct )

Color and styling configuration for the user interface

bone_color_sets

(default None, readonly, never None)

Type :

bpy_prop_collection[ThemeBoneColorSet]

clip_editor

(readonly, never None)

Type :

ThemeClipEditor

collection_color

(default None, readonly, never None)

Type :

bpy_prop_collection[ThemeCollectionColor]

common

UI styling reused across the various editors (readonly, never None)

Type :

ThemeCommon

console

(readonly, never None)

Type :

ThemeConsole

dopesheet_editor

(readonly, never None)

Type :

ThemeDopeSheet

file_browser

(readonly, never None)

Type :

ThemeFileBrowser

filepath

Where the preset for this theme was loaded from, if there is one (default “”, never None)

Type :

str

graph_editor

(readonly, never None)

Type :

ThemeGraphEditor

image_editor

(readonly, never None)

Type :

ThemeImageEditor

info

(readonly, never None)

Type :

ThemeInfo

name

The theme’s name (default “”, never None)

Type :

str

nla_editor

(readonly, never None)

Type :

ThemeNLAEditor

node_editor

(readonly, never None)

Type :

ThemeNodeEditor

outliner

(readonly, never None)

Type :

ThemeOutliner

preferences

(readonly, never None)

Type :

ThemePreferences

properties

(readonly, never None)

Type :

ThemeProperties

regions

Styling shared by editor regions in common (readonly, never None)

Type :

ThemeRegions

sequence_editor

(readonly, never None)

Type :

ThemeSequenceEditor

spreadsheet

(readonly, never None)

Type :

ThemeSpreadsheet

statusbar

(readonly, never None)

Type :

ThemeStatusBar

strip_color

(default None, readonly, never None)

Type :

bpy_prop_collection[ThemeStripColor]

text_editor

(readonly, never None)

Type :

ThemeTextEditor

theme_area

(default '`USER_INTERFACE`' )

Type :

Literal[‘`USER_INTERFACE`’, ‘STYLE’, ‘REGIONS’, ‘COMMON’, ‘`VIEW_3D`’, ‘`DOPESHEET_EDITOR`’, ‘`FILE_BROWSER`’, ‘`GRAPH_EDITOR`’, ‘`IMAGE_EDITOR`’, ‘INFO’, ‘`CLIP_EDITOR`’, ‘`NODE_EDITOR`’, ‘`NLA_EDITOR`’, ‘OUTLINER’, ‘PREFERENCES’, ‘PROPERTIES’, ‘CONSOLE’, ‘SPREADSHEET’, ‘STATUSBAR’, ‘`TEXT_EDITOR`’, ‘TOPBAR’, ‘`SEQUENCE_EDITOR`’, ‘`BONE_COLOR_SETS`’]

topbar

(readonly, never None)

Type :

ThemeTopBar

user_interface

(readonly, never None)

Type :

ThemeUserInterface

view_3d

(readonly, never None)

Type :

ThemeView3D

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

| Preferences.themes | |

## ThemeBoneColorSet(bpy_struct)

### ThemeBoneColorSet(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeBoneColorSet ( bpy_struct )

Color-set styling for bones

active

Color applied to the active bone (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

normal

Color applied to a bone’s surface (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

select

Color applied to selected bones (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

show_colored_constraints

Enable color cues that signal constraint or keyed state (default False)

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

| ActionGroup.colors BoneColor.custom | Theme.bone_color_sets |

## ThemeClipEditor(bpy_struct)

### ThemeClipEditor(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeClipEditor ( bpy_struct )

Styling for the Movie Clip Editor

active_marker

Color of active marker (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

disabled_marker

Color of disabled marker (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

grid

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

locked_marker

Color of locked marker (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

marker

Color of marker (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

marker_outline

Color of marker’s outline (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

metadatabg

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

metadatatext

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

path_after

Path color drawn for frames past the current one (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

path_before

Path color drawn for frames ahead of the current one (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

path_keyframe_after

Keyframe color on the path past the current frame (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

path_keyframe_before

Keyframe color on the path before the current frame (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

selected_marker

Color of selected marker (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

space

Styling for the space (readonly, never None)

Type :

ThemeSpaceGeneric

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

| Theme.clip_editor | |

## ThemeCollectionColor(bpy_struct)

### ThemeCollectionColor(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeCollectionColor ( bpy_struct )

Styling for collection colors

color

Collection Color Tag (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

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

| Theme.collection_color | |

## ThemeCommon(bpy_struct)

### ThemeCommon(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeCommon ( bpy_struct )

UI styling reused across the various editors

anim

(readonly, never None)

Type :

ThemeCommonAnim

curves

(readonly, never None)

Type :

ThemeCommonCurves

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

| Theme.common | |

## ThemeCommonAnim(bpy_struct)

### ThemeCommonAnim(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeCommonAnim ( bpy_struct )

Animation styling shared across editors

channel

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

channel_group

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

channel_group_active

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

channel_selected

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

channels

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

channels_sub

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

keyframe

Color of regular keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_breakdown

Color of breakdown keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_breakdown_selected

Color of selected breakdown keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_extreme

Color of extreme keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_extreme_selected

Color of selected extreme keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_generated

Color of generated keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_generated_selected

Color of selected generated keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_jitter

Color of jitter keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_jitter_selected

Color of selected jitter keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_moving_hold

Color of moving hold keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_moving_hold_selected

Color of selected moving hold keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_selected

Color of selected keyframe (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

long_key

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

long_key_selected

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

playhead

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

preview_range

Overlay color marking the preview range (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

scene_strip_range

Overlay color marking the scene strip range (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

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

| ThemeCommon.anim | |

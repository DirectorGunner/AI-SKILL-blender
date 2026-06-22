# Themestyle Bpy Struct, Themetexteditor Bpy Struct, Themetopbar Bpy Struct, Themeuserinterface Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ThemeStyle(bpy_struct); ThemeTextEditor(bpy_struct); ThemeTopBar(bpy_struct); ThemeUserInterface(bpy_struct); ThemeWidgetColors(bpy_struct); ThemeWidgetStateColors(bpy_struct); TimelineMarkers(bpy_prop_collection); Timer(bpy_struct).

## ThemeStyle(bpy_struct)

### ThemeStyle(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeStyle ( bpy_struct ) 

Theming applied to style sets.

panel_title 

(readonly, never None)

Type :

ThemeFontStyle

tooltip 

(readonly, never None)

Type :

ThemeFontStyle

widget 

(readonly, never None)

Type :

ThemeFontStyle

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

| Preferences.ui_styles | |

## ThemeTextEditor(bpy_struct)

### ThemeTextEditor(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeTextEditor ( bpy_struct ) 

Color theming for the Text Editor.

cursor 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_numbers 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_numbers_background 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

selected_text 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

space 

Settings for space (readonly, never None)

Type :

ThemeSpaceGeneric

syntax_builtin 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_comment 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_numbers 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_preprocessor 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_reserved 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_special 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_string 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

syntax_symbols 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.text_editor | |

## ThemeTopBar(bpy_struct)

### ThemeTopBar(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeTopBar ( bpy_struct ) 

Color theming for the Top Bar.

space 

Settings for space (readonly, never None)

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

| Theme.topbar | |

## ThemeUserInterface(bpy_struct)

### ThemeUserInterface(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeUserInterface ( bpy_struct ) 

Color theming for user interface elements.

axis_w 

W-axis used by quaternion and axis-angle rotations (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

axis_x 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

axis_y 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

axis_z 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

editor_border 

Border color drawn between editors (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

editor_outline 

Outline color for every editor apart from the active one (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

editor_outline_active 

Outline color used for the editor that is active (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

gizmo_a 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gizmo_b 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gizmo_hi 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gizmo_primary 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gizmo_secondary 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gizmo_view_align 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

icon_alpha 

Opacity applied to interface icons so as to lower their contrast (in [0, 1], default 0.0)

Type :

float

icon_autokey 

Indicator color shown while Auto Keying is on (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_border_intensity 

Adjusts how strong the outline around theme icons appears (in [0, 1], default 0.0)

Type :

float

icon_collection 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_folder 

Tint applied to folder icons within the file browser (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_modifier 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_object 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_object_data 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_saturation 

How saturated interface icons appear (in [0, 1], default 0.0)

Type :

float

icon_scene 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

icon_shading 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

menu_shadow_fac 

How strongly shadows are blended behind panels and menus (in [0.01, 1], default 0.0)

Type :

float

menu_shadow_width 

Shadow spread behind panels and menus; a value of zero turns it off (in [0, 24], default 0)

Type :

int

panel_active 

Outline tint for active top-level panels (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

panel_back 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

panel_header 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

panel_outline 

Outline tint for top-level panels (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

panel_roundness 

How rounded the corners of panels and sub-panels look (in [0, 1], default 0.4)

Type :

float

panel_sub_back 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

panel_text 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

panel_title 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transparent_checker_primary 

First checker color marking regions that are transparent (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transparent_checker_secondary 

Second checker color marking regions that are transparent (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transparent_checker_size 

Square size of the checker pattern marking transparent regions (in [2, 48], default 0)

Type :

int

wcol_box 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_curve 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_list_item 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_menu 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_menu_back 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_menu_item 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_num 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_numslider 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_option 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_pie_menu 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_progress 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_pulldown 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_radio 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_regular 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_scroll 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_state 

(readonly, never None)

Type :

ThemeWidgetStateColors

wcol_tab 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_text 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_toggle 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_tool 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_toolbar_item 

(readonly, never None)

Type :

ThemeWidgetColors

wcol_tooltip 

(readonly, never None)

Type :

ThemeWidgetColors

widget_emboss 

Tint of the one-pixel shadow line drawn beneath widgets (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

widget_text_cursor 

Tint of the text-entry caret (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.user_interface | |

## ThemeWidgetColors(bpy_struct)

### ThemeWidgetColors(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeWidgetColors ( bpy_struct ) 

Color theming for widget color sets.

inner 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

inner_sel 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

item 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

outline 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

outline_sel 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

roundness 

How much the edges are rounded (in [0, 1], default 0.0)

Type :

float

shadedown 

(in [-100, 100], default 0)

Type :

int

shadetop 

(in [-100, 100], default 0)

Type :

int

show_shaded 

(default False)

Type :

bool

text 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

text_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| ThemeUserInterface.wcol_box ThemeUserInterface.wcol_curve ThemeUserInterface.wcol_list_item ThemeUserInterface.wcol_menu ThemeUserInterface.wcol_menu_back ThemeUserInterface.wcol_menu_item ThemeUserInterface.wcol_num ThemeUserInterface.wcol_numslider ThemeUserInterface.wcol_option ThemeUserInterface.wcol_pie_menu ThemeUserInterface.wcol_progress | ThemeUserInterface.wcol_pulldown ThemeUserInterface.wcol_radio ThemeUserInterface.wcol_regular ThemeUserInterface.wcol_scroll ThemeUserInterface.wcol_tab ThemeUserInterface.wcol_text ThemeUserInterface.wcol_toggle ThemeUserInterface.wcol_tool ThemeUserInterface.wcol_toolbar_item ThemeUserInterface.wcol_tooltip |

## ThemeWidgetStateColors(bpy_struct)

### ThemeWidgetStateColors(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeWidgetStateColors ( bpy_struct ) 

Color theming for widget state colors.

blend 

(in [0, 1], default 0.0)

Type :

float

error 

Tint applied to items in an error state (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

info 

Tint applied to informational items (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

inner_anim 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_anim_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_changed 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_changed_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_driven 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_driven_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_key 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_key_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_overridden 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

inner_overridden_sel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

success 

Tint applied to items in a success state (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

warning 

Tint applied to items in a warning state (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

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

| ThemeUserInterface.wcol_state | |

## TimelineMarkers(bpy_prop_collection)

### TimelineMarkers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. TimelineMarkers ( bpy_prop_collection ) 

A set holding the timeline markers.

new ( name , * , frame = 1 ) 

Add a timeline marker

Parameters :

- name ( str ) – New name for the marker (not unique) (never None)

- frame ( int ) – The frame for the new marker (in [-1048574, 1048574], optional)

Returns :

Newly created timeline marker

Return type :

TimelineMarker

remove ( marker ) 

Remove a timeline marker

Parameters :

marker (TimelineMarker) – Timeline marker to remove (never None)

clear ( ) 

Remove all timeline markers

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

| Scene.timeline_markers | |

## Timer(bpy_struct)

### Timer(bpy_struct) 

base class — bpy_struct

class bpy.types. Timer ( bpy_struct ) 

Timer fired by window events.

time_delta 

Seconds elapsed since the previous step (in [-inf, inf], default 0.0, readonly)

Type :

float

time_duration 

Seconds elapsed since the timer began (in [-inf, inf], default 0.0, readonly)

Type :

float

time_step 

(in [-inf, inf], default 0.0, readonly)

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

| WindowManager.event_timer_add | WindowManager.event_timer_remove |

# Themecommoncurves Bpy Struct, Themeconsole Bpy Struct, Themedopesheet Bpy Struct, Themefilebrowser Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ThemeCommonCurves(bpy_struct); ThemeConsole(bpy_struct); ThemeDopeSheet(bpy_struct); ThemeFileBrowser(bpy_struct); ThemeFontStyle(bpy_struct); ThemeGradientColors(bpy_struct); ThemeGraphEditor(bpy_struct); ThemeInfo(bpy_struct); ThemeNLAEditor(bpy_struct); ThemeOutliner(bpy_struct).

## ThemeCommonCurves(bpy_struct)

### ThemeCommonCurves(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeCommonCurves ( bpy_struct )

Curve styling shared across editors

handle_align

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_auto

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_auto_clamped

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_free

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_sel_align

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_sel_auto

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_sel_auto_clamped

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_sel_free

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_sel_vect

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_vect

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_vertex

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_vertex_select

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

handle_vertex_size

(in [1, 100], default 0)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ThemeCommon.curves | |

## ThemeConsole(bpy_struct)

### ThemeConsole(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeConsole ( bpy_struct )

Styling for the Console

cursor

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_error

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_info

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_input

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

line_output

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

select

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

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

| Theme.console | |

## ThemeDopeSheet(bpy_struct)

### ThemeDopeSheet(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeDopeSheet ( bpy_struct )

Styling for the Dope Sheet

anim_interpolation_constant

Line color shown for constant-interpolation segments (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

anim_interpolation_linear

Line color shown for linear-interpolation segments (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

anim_interpolation_other

Line color shown for easing and dynamic interpolation segments (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

grid

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_border

Color of keyframe border (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

keyframe_border_selected

Color of selected keyframe border (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

keyframe_scale_factor

Multiplier that controls how tall keyframes are drawn (in [0.8, 5], default 1.0)

Type :

float

simulated_frames

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

space

Styling for the space (readonly, never None)

Type :

ThemeSpaceGeneric

summary

Color of summary channel (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

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

| Theme.dopesheet_editor | |

## ThemeFileBrowser(bpy_struct)

### ThemeFileBrowser(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeFileBrowser ( bpy_struct )

Styling for the File Browser

row_alternate

Tint laid over alternating rows (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

selected_file

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.file_browser | |

## ThemeFontStyle(bpy_struct)

### ThemeFontStyle(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeFontStyle ( bpy_struct )

Styling for Font

character_weight

How heavy the glyphs are drawn; the 100-900 scale puts 400 at regular weight. (in [100, 900], default 400)

Type :

int

points

Size of the font, measured in points (in [6, 32], default 0.0)

Type :

float

shadow

Which shadow style to use (0 disables it, 3 and 5 blur, 6 outlines) (in [0, 6], default 0)

Type :

int

shadow_alpha

(in [0, 1], default 0.0)

Type :

float

shadow_offset_x

How far the shadow shifts, in pixels (in [-10, 10], default 0)

Type :

int

shadow_offset_y

How far the shadow shifts, in pixels (in [-10, 10], default 0)

Type :

int

shadow_value

Gray level used for the shadow color (in [0, 1], default 0.0)

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

| ThemeStyle.panel_title ThemeStyle.tooltip | ThemeStyle.widget |

## ThemeGradientColors(bpy_struct)

### ThemeGradientColors(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeGradientColors ( bpy_struct )

Styling for the background fill and its gradient

background_type

Which kind of backdrop fills the 3D viewport (default '`SINGLE_COLOR`' )

- `SINGLE_COLOR`
Single Color – Fill the viewport backdrop with one flat color.

- LINEAR
Linear Gradient – Fill the viewport backdrop with a screen-space vertical gradient.

- RADIAL
Vignette – Fill the viewport backdrop with a radial gradient.

Type :

Literal[‘`SINGLE_COLOR`’, ‘LINEAR’, ‘RADIAL’]

gradient

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

high_gradient

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

| ThemeSpaceGradient.gradients | |

## ThemeGraphEditor(bpy_struct)

### ThemeGraphEditor(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeGraphEditor ( bpy_struct )

Styling for the graph editor

grid

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

space

Styling for the space (readonly, never None)

Type :

ThemeSpaceGeneric

vertex

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_active

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_select

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_size

(in [1, 32], default 0)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Theme.graph_editor | |

## ThemeInfo(bpy_struct)

### ThemeInfo(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeInfo ( bpy_struct )

Styling for Info

info_debug

Background color of Debug icon (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

info_debug_text

Foreground color of Debug icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_error_text

Foreground color of Error icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_info_text

Foreground color of Info icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_operator

Background color of Operator icon (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

info_operator_text

Foreground color of Operator icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_property

Background color of Property icon (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

info_property_text

Foreground color of Property icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_selected

Background color of selected line (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_selected_text

Text color of selected line (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

info_warning_text

Foreground color of Warning icon (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.info | |

## ThemeNLAEditor(bpy_struct)

### ThemeNLAEditor(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeNLAEditor ( bpy_struct )

Styling for the NLA Editor

active_action

The animation data-block has an active action (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

active_action_unset

The animation data-block has no active action (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

grid

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

keyframe_border

Color of keyframe border (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

keyframe_border_selected

Color of selected keyframe border (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

meta_strips

Unselected Meta Strip (for grouping related strips) (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

meta_strips_selected

Selected Meta Strip (for grouping related strips) (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

sound_strips

Unselected Sound Strip (for timing speaker sounds) (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

sound_strips_selected

Selected Sound Strip (for timing speaker sounds) (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

space

Styling for the space (readonly, never None)

Type :

ThemeSpaceGeneric

strips

Unselected Action-Clip Strip (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

strips_selected

Selected Action-Clip Strip (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transition_strips

Unselected Transition Strip (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transition_strips_selected

Selected Transition Strip (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

tweak

Color used for the strip or action currently being tweaked (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

tweak_duplicate

Warning or error tint for strips that reference the one being tweaked (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.nla_editor | |

## ThemeOutliner(bpy_struct)

### ThemeOutliner(bpy_struct)

base class — bpy_struct

class bpy.types. ThemeOutliner ( bpy_struct )

Styling for the Outliner

active

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

active_object

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

edited_object

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

match

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

row_alternate

Tint laid over alternating rows (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

selected_highlight

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

selected_object

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

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

| Theme.outliner | |

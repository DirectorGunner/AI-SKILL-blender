# Preferencesview Bpy Struct, Propertygroup Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PreferencesView(bpy_struct); PropertyGroup(bpy_struct).

## PreferencesView(bpy_struct)

### PreferencesView(bpy_struct) 

base class — bpy_struct

class bpy.types. PreferencesView ( bpy_struct ) 

Settings that govern how data is presented on screen

border_width 

Amount of padding placed around each editor. (in [1, 10], default 2)

Type :

int

color_picker_type 

Selects which visual form the color-picker widget takes (default '`CIRCLE_HSV`' )

- `CIRCLE_HSV`
Circle (HSV) – A circular Hue/Saturation color wheel, with Value slider.

- `CIRCLE_HSL`
Circle (HSL) – A circular Hue/Saturation color wheel, with Lightness slider.

- `SQUARE_SV`
Square (SV + H) – A square showing Saturation/Value, with Hue slider.

- `SQUARE_HS`
Square (HS + V) – A square showing Hue/Saturation, with Value slider.

- `SQUARE_HV`
Square (HV + S) – A square showing Hue/Value, with Saturation slider.

Type :

Literal[‘`CIRCLE_HSV`’, ‘`CIRCLE_HSL`’, ‘`SQUARE_SV`’, ‘`SQUARE_HS`’, ‘`SQUARE_HV`’]

factor_display_type 

Chooses the presentation used for factor values (default 'FACTOR' )

- FACTOR
Factor – Display factors as values between 0 and 1.

- PERCENTAGE
Percentage – Display factors as percentages.

Type :

Literal[‘FACTOR’, ‘PERCENTAGE’]

filebrowser_display_type 

Where the File Editor opens by default (default 'WINDOW' )

- SCREEN
Maximized Area – Open the temporary editor in a maximized screen.

- WINDOW
New Window – Open the temporary editor in a new window.

Type :

Literal[‘SCREEN’, ‘WINDOW’]

font_path_ui 

Location of the font used for the interface (default “”, never None)

Type :

str

font_path_ui_mono 

Location of the monospaced font used for the interface (default “”, never None)

Type :

str

gizmo_size 

The on-screen diameter of the gizmo (in [10, 200], default 75)

Type :

int

gizmo_size_navigate_v3d 

Size given to the Navigate Gizmo (in [30, 200], default 80)

Type :

int

header_align 

Where headers sit by default for newly created space-types (default 'BOTTOM' )

- NONE
Keep Existing – Keep existing header alignment.

- TOP
Top – Top aligned on load.

- BOTTOM
Bottom – Bottom align on load (except for property editors).

Type :

Literal[‘NONE’, ‘TOP’, ‘BOTTOM’]

language 

Which language is applied for translation (default 'DEFAULT' )

- DEFAULT
Automatic – Automatically choose the system-defined language if available, or fall-back to English (US).

- ab
Abkhaz - Аԥсуа бызшәа – Locale code: ab. Translation progress: 0%.

- ar_EG
Arabic - ﺔﻴﺑﺮﻌﻟﺍ – Locale code: ar_EG. Translation progress: 23%.

- eu_EU
Basque - Euskara – Locale code: eu_EU. Translation progress: 1%.

- be
Belarusian - Беларуская – Locale code: be. Translation progress: 0%.

- bg_BG
Bulgarian - Български – Locale code: bg_BG. Translation progress: 1%.

- ca_AD
Catalan - Català – Locale code: ca_AD. Translation progress: 100%.

- zh_HANS
Chinese (Simplified) - 简体中文 – Locale code: zh_HANS. Translation progress: 100%.

- zh_HANT
Chinese (Traditional) - 繁體中文 – Locale code: zh_HANT. Translation progress: 62%.

- cs_CZ
Czech - Čeština – Locale code: cs_CZ. Translation progress: 27%.

- da
Danish - Dansk – Locale code: da. Translation progress: 3%.

- nl_NL
Dutch - Nederlands – Locale code: nl_NL. Translation progress: 8%.

- en_GB
English (UK) – Locale code: en_GB. Translation progress: 99%.

- en_US
English (US) – Locale code: en_US. Translation progress: 100%.

- eo
Esperanto - Esperanto – Locale code: eo. Translation progress: 0%.

- fi_FI
Finnish - Suomi – Locale code: fi_FI. Translation progress: 11%.

- fr_FR
French - Français – Locale code: fr_FR. Translation progress: 100%.

- ka
Georgian - ქართული – Locale code: ka. Translation progress: 100%.

- de_DE
German - Deutsch – Locale code: de_DE. Translation progress: 37%.

- el_GR
Greek - Ελληνικά – Locale code: el_GR. Translation progress: 1%.

- he_IL
Hebrew - תירִבְעִ – Locale code: he_IL. Translation progress: 2%.

- hi_IN
Hindi - हिन्दी – Locale code: hi_IN. Translation progress: 4%.

- hu_HU
Hungarian - Magyar – Locale code: hu_HU. Translation progress: 11%.

- id_ID
Indonesian - Bahasa indonesia – Locale code: id_ID. Translation progress: 21%.

- it_IT
Italian - Italiano – Locale code: it_IT. Translation progress: 44%.

- ja_JP
Japanese - 日本語 – Locale code: ja_JP. Translation progress: 100%.

- ko_KR
Korean - 한국어 – Locale code: ko_KR. Translation progress: 98%.

- ky_KG
Kyrgyz - Кыргыз тили – Locale code: ky_KG. Translation progress: 2%.

- lt
Lithuanian - Lietuviškai – Locale code: lt. Translation progress: 3%.

- ml
Malayalam - മലയാളം – Locale code: ml. Translation progress: 0%.

- nb
Norwegian (Bokmål) - Norsk bokmål – Locale code: nb. Translation progress: 4%.

- fa_IR
Persian - ﯽﺳﺭﺎﻓ – Locale code: fa_IR. Translation progress: 3%.

- pl_PL
Polish - Polski – Locale code: pl_PL. Translation progress: 100%.

- pt_BR
Portuguese (Brazil) - Português brasileiro – Locale code: pt_BR. Translation progress: 43%.

- pt_PT
Portuguese (Portugal) - Português europeu – Locale code: pt_PT. Translation progress: 78%.

- ro_RO
Romanian - Român – Locale code: ro_RO. Translation progress: 2%.

- ru_RU
Russian - Русский – Locale code: ru_RU. Translation progress: 100%.

- sr_RS
Serbian (Cyrillic) - Српски – Locale code: sr_RS. Translation progress: 16%.

- sr_RS@latin
Serbian (Latin) - Srpski latinica – Locale code: sr_RS @ latin. Translation progress: 16%.

- sk_SK
Slovak - Slovenčina – Locale code: sk_SK. Translation progress: 100%.

- sl
Slovenian - Slovenščina – Locale code: sl. Translation progress: 51%.

- es
Spanish - Español – Locale code: es. Translation progress: 100%.

- sw
Swahili - Kiswahili – Locale code: sw. Translation progress: 72%.

- sv_SE
Swedish - Svenska – Locale code: sv_SE. Translation progress: 100%.

- ta
Tamil - தமிழ் – Locale code: ta. Translation progress: 100%.

- th_TH
Thai - ภาษาไทย – Locale code: th_TH. Translation progress: 5%.

- tr_TR
Turkish - Türkçe – Locale code: tr_TR. Translation progress: 78%.

- uk_UA
Ukrainian - Українська – Locale code: uk_UA. Translation progress: 57%.

- ur
Urdu - وُدرُا – Locale code: ur. Translation progress: 86%.

- vi_VN
Vietnamese - Tiếng Việt – Locale code: vi_VN. Translation progress: 93%.

Type :

Literal[‘DEFAULT’, ‘ab’, ‘ar_EG’, ‘eu_EU’, ‘be’, ‘bg_BG’, ‘ca_AD’, ‘zh_HANS’, ‘zh_HANT’, ‘cs_CZ’, ‘da’, ‘nl_NL’, ‘en_GB’, ‘en_US’, ‘eo’, ‘fi_FI’, ‘fr_FR’, ‘ka’, ‘de_DE’, ‘el_GR’, ‘he_IL’, ‘hi_IN’, ‘hu_HU’, ‘id_ID’, ‘it_IT’, ‘ja_JP’, ‘ko_KR’, ‘ky_KG’, ‘lt’, ‘ml’, ‘nb’, ‘fa_IR’, ‘pl_PL’, ‘pt_BR’, ‘pt_PT’, ‘ro_RO’, ‘ru_RU’, ‘sr_RS’, ‘sr_RS @ latin’, ‘sk_SK’, ‘sl’, ‘es’, ‘sw’, ‘sv_SE’, ‘ta’, ‘th_TH’, ‘tr_TR’, ‘uk_UA’, ‘ur’, ‘vi_VN’]

lookdev_sphere_size 

The diameter applied to the HDRI reference spheres (in [50, 400], default 150)

Type :

int

menu_close_leave 

Dismiss menus once the pointer leaves their region. (default False)

Type :

bool

mini_axis_brightness 

How bright the icon appears (in [0, 10], default 8)

Type :

int

mini_axis_size 

Dimensions of the axes icon (in [10, 64], default 25)

Type :

int

mini_axis_type 

Display compact rotating 3D axes at the upper-right of the 3D viewport (default 'GIZMO' )

Type :

Literal[‘NONE’, ‘MINIMAL’, ‘GIZMO’]

open_sublevel_delay 

Pause, in tenths of a second, before sub level menus open by themselves (in [1, 40], default 2)

Type :

int

open_toplevel_delay 

Pause, in tenths of a second, before top level menus open by themselves (in [1, 40], default 5)

Type :

int

pie_animation_timeout 

How long it takes to animate the pie fully open (measured in hundredths of a second) (in [0, 1000], default 6)

Type :

int

pie_initial_timeout 

Span during which the pie keeps the starting mouse position as its center (measured in hundredths of a second) (in [0, 1000], default 0)

Type :

int

pie_menu_confirm 

Travel distance past which a choice is committed (set to zero to turn off) (in [0, 1000], default 0)

Type :

int

pie_menu_radius 

Size of the pie menu, in pixels (in [0, 1000], default 100)

Type :

int

pie_menu_threshold 

How far from the center the pointer must move before a choice can register (in [0, 1000], default 12)

Type :

int

pie_tap_timeout 

Holding the pie button past this duration dismisses the menu when released (measured in hundredths of a second) (in [0, 1000], default 20)

Type :

int

playback_fps_samples 

Frame count averaged when computing FPS. A value of zero lets Blender pick automatically, matching the sample count to the target FPS. (in [0, 5000], default 8)

Type :

int

preferences_display_type 

Where the Preferences window opens by default (default 'WINDOW' )

- SCREEN
Maximized Area – Open the temporary editor in a maximized screen.

- WINDOW
New Window – Open the temporary editor in a new window.

Type :

Literal[‘SCREEN’, ‘WINDOW’]

render_display_type 

Where rendered images appear by default (default 'WINDOW' )

- NONE
Keep User Interface – Images are rendered without changing the user interface.

- SCREEN
Maximized Area – Images are rendered in a maximized Image Editor.

- AREA
Image Editor – Images are rendered in an Image Editor.

- WINDOW
New Window – Images are rendered in a new window.

Type :

Literal[‘NONE’, ‘SCREEN’, ‘AREA’, ‘WINDOW’]

rotation_angle 

Increment of rotation applied by the numeric pad keys (2 4 6 8) (in [0, 90], default 15.0)

Type :

float

show_addons_enabled_only 

Restrict the list to enabled add-ons. Clear this to reveal every installed add-on. (default False)

Type :

bool

show_area_handle 

Reveal the corner handles used to adjust visible areas (default False)

Type :

bool

show_column_layout 

Arrange the toolbox using a column layout (default True)

Type :

bool

show_developer_ui 

Expose advanced developer-oriented settings and tools (default False)

Type :

bool

show_extensions_updates 

Display the count of pending Extension updates (default True)

Type :

bool

show_gizmo 

Turn on transform gizmos as the default (default True)

Type :

bool

show_navigate_ui 

Display navigation widgets in 2D and 3D views that lack scroll bars (default True)

Type :

bool

show_number_arrows 

Add arrows to numeric fields for stepping values up or down (default False)

Type :

bool

show_object_info 

Add the active object's name and the current frame to the text info overlay (default True)

Type :

bool

show_playback_fps 

Add the frames-per-second readout to the text info overlay during animation playback (default True)

Type :

bool

show_splash 

Bring up the splash screen when Blender launches (default True)

Type :

bool

show_statusbar_memory 

Report Blender's memory consumption (default False)

Type :

bool

show_statusbar_scene_duration 

Report the duration of the scene (default False)

Type :

bool

show_statusbar_stats 

Report scene statistics (default False)

Type :

bool

show_statusbar_version 

Report the Blender version string (default True)

Type :

bool

show_statusbar_vram 

Report GPU video-memory consumption (default False)

Type :

bool

show_tooltips 

Present tooltips (while turned off, hold Alt and hover to force them to appear) (default True)

Type :

bool

show_tooltips_python 

Include Python references within tooltips (default False)

Type :

bool

show_view_name 

Add the view orientation's name to the text info overlay (default True)

Type :

bool

smooth_view 

Duration, in milliseconds, of the view animation; zero turns it off (in [0, 1000], default 200)

Type :

int

text_hinting 

Technique used to keep interface text crisp (default 'AUTO' )

Type :

Literal[‘AUTO’, ‘NONE’, ‘SLIGHT’, ‘FULL’]

timecode_style 

How a timecode is shown when timing is not given as frames (default 'MINIMAL' )

- MINIMAL
Minimal Info – Most compact representation, uses ‘+’ as separator for sub-second frame numbers, with left and right truncation of the timecode as necessary.

- SMPTE
SMPTE (Full) – Full SMPTE timecode (format is HH:MM:SS:FF).

- `SMPTE_COMPACT`
SMPTE (Compact) – SMPTE timecode showing minutes, seconds, and frames only - hours are also shown if necessary, but not by default.

- MILLISECONDS
Compact with Decimals – Similar to SMPTE (Compact), except that the decimal part of the second is shown instead of frames.

- `SECONDS_ONLY`
Only Seconds – Direct conversion of frame numbers to seconds.

Type :

Literal[‘MINIMAL’, ‘SMPTE’, ‘`SMPTE_COMPACT`’, ‘MILLISECONDS’, ‘`SECONDS_ONLY`’]

ui_line_width 

Adjusts how thick widget outlines, lines, and dots appear across the interface (default 'AUTO' )

- THIN
Thin – Thinner lines than the default.

- AUTO
Default – Automatic line width based on UI scale.

- THICK
Thick – Thicker lines than the default.

Type :

Literal[‘THIN’, ‘AUTO’, ‘THICK’]

ui_scale 

Adjusts how large fonts and widgets appear across the interface (in [0.5, 6], default 1.0)

Type :

float

use_filter_brushes_by_tool 

Limit the asset shelf to brushes that suit the active tool. Held in the Preferences, which may need a manual save when Auto-Save Preferences is turned off (default False)

Type :

bool

use_fresnel_edit 

Apply a fresnel effect to edit-mesh overlays.
This aids the readability of very dense meshes, though it can tire the eyes when working on lower-poly models

(default False)

Type :

bool

use_mouse_over_open 

Have menu buttons and pull-downs open on their own while the pointer hovers them (default False)

Type :

bool

use_reduce_motion 

Suppress animations and similar motion effects throughout the interface (default False)

Type :

bool

use_save_prompt 

Prompt for confirmation before quitting while changes remain unsaved (default True)

Type :

bool

use_text_antialiasing 

Soften the jagged edges of interface text (default True)

Type :

bool

use_text_render_subpixelaa 

Lay out text for the best horizontal placement (default False)

Type :

bool

use_translate_interface 

Translate every label across menus, buttons, and panels (be aware this can complicate following tutorials or the manual) (default True)

Type :

bool

use_translate_new_dataname 

Translate the names given to new data-blocks (objects, materials…) (default True)

Type :

bool

use_translate_reports 

Translate supplementary information such as error messages (default True)

Type :

bool

use_translate_tooltips 

Translate the text shown when hovering over UI elements (recommended) (default True)

Type :

bool

use_weight_color_range 

Turn on the color range applied to weight visualization while weight painting (default False)

Type :

bool

view2d_grid_spacing_min 

Smallest pixel gap allowed between gridlines in 2D Viewports (in [1, 500], default 45)

Type :

int

view_frame_keyframes 

How many keyframes around the cursor the zoom encompasses (in [1, 500], default 0)

Type :

int

view_frame_seconds 

How many seconds around the cursor the zoom encompasses (in [0, 10000], default 0.0)

Type :

float

view_frame_type 

The way framing zoom centers on the current frame (default '`KEEP_RANGE`' )

Type :

Literal[‘`KEEP_RANGE`’, ‘SECONDS’, ‘KEYFRAMES’]

weight_color_range 

The color range applied to weight visualization while weight painting (readonly, never None)

Type :

ColorRamp

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

| Preferences.view | |

## PropertyGroup(bpy_struct)

### PropertyGroup(bpy_struct) 

### Custom Properties 

A PropertyGroup serves as the foundation class for property sets that are defined on the fly.

You can use them to attach your own custom types onto existing Blender data, and
those types stay animatable, reachable from the user interface, and reachable from Python.

Note

While the values placed on Blender data persist to disk, the class
definitions do not — so each time Blender starts the class must be
registered once more.

The recommended approach is an add-on that runs at startup and registers
your properties there.

Note

A PropertyGroup has to be registered before it can be attached to Blender data.

See also

The property types used inside class declarations all live in bpy.props

`\text
import bpy

class MyPropertyGroup(bpy.types.PropertyGroup):
custom_1: bpy.props.FloatProperty(name="My Float")
custom_2: bpy.props.IntProperty(name="My Int")

bpy.utils.register_class(MyPropertyGroup)

bpy.types.Object.my_prop_grp = bpy.props.PointerProperty(type=MyPropertyGroup)

### Test this worked.
bpy.data.objects[0].my_prop_grp.custom_1 = 22.0
`

base class — bpy_struct

subclasses —
OperatorFileListElement, OperatorMousePath, OperatorStrokeElement, SelectedUvElement

class bpy.types. PropertyGroup ( bpy_struct ) 

Group of ID properties

name 

Unique name referenced in code and scripting; Python subclasses may redefine it where needed (default “”, never None)

Type :

str

bl_system_properties_get ( * , do_create = False ) 

DEBUG ONLY. Internal entry point to runtime-defined RNA data storage, meant purely for testing and debugging. Avoid using it during normal scripting, and in particular never assume the data it returns is writable

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

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

| AddonPreferences.bl_system_properties_get Bone.bl_system_properties_get BoneCollection.bl_system_properties_get CollectionExport.export_properties EditBone.bl_system_properties_get GizmoGroupProperties.bl_system_properties_get GizmoProperties.bl_system_properties_get ID.bl_system_properties_get IDPropertyWrapPtr.bl_system_properties_get KeyConfigPreferences.bl_system_properties_get Node.bl_system_properties_get NodeSocket.bl_system_properties_get NodeTreeInterfaceSocket.bl_system_properties_get | NodesModifier.bl_system_properties_get OperatorProperties.bl_system_properties_get PoseBone.bl_system_properties_get PropertyGroup.bl_system_properties_get PropertyGroupItem.collection PropertyGroupItem.group PropertyGroupItem.idp_array Strip.bl_system_properties_get TimelineMarker.bl_system_properties_get UIList.bl_system_properties_get View3DShading.bl_system_properties_get ViewLayer.bl_system_properties_get |

## See also

- [Bpy Struct](bpy-struct.md)

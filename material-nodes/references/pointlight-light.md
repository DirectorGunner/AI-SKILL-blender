# Pointlight Light, Preferencesedit Bpy Struct, Preferencesfilepaths Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PointLight(Light); PreferencesEdit(bpy_struct); PreferencesFilePaths(bpy_struct).

## PointLight(Light)

### PointLight(Light)

base classes — bpy_struct, ID, Light

class bpy.types. PointLight ( Light )

A point Light that radiates in every direction.

energy

Radiant power (W) the light puts out across its whole surface in all directions (in [-inf, inf], default 10.0)

Type :

float

shadow_buffer_clip_start

Near limit of the shadow map; geometry nearer than this casts no shadow (in [1e-06, inf], default 0.05)

Type :

float

shadow_filter_radius

Soften shadow stair-stepping through Percentage Closer Filtering (in [0, inf], default 1.0)

Type :

float

shadow_jitter_overblur

Run shadow tracing on every jittered sample to cut down on under-sampling noise (in [0, 100], default 10.0)

Type :

float

shadow_maximum_resolution

Smallest allowed size for a shadow-map pixel. Raising it trades shadow detail for lower memory use. (in [0, inf], default 0.001)

Type :

float

shadow_soft_size

Size of the light used when sampling ray-traced shadows (Raytraced shadows) (in [0, inf], default 0.0)

Type :

float

use_absolute_resolution

Cap the resolution at one unit out from the light origin rather than scaling it with the shaded pixel (default False)

Type :

bool

use_shadow_jitter

Turn on jittered soft shadows for finer shadow precision (off in the viewport unless switched on in the render settings). Carries a heavy performance cost. (default False)

Type :

bool

use_soft_falloff

Fade the light off near contact so edges stay smooth where its geometry overlaps other objects (default True)

Type :

bool

inline_shader_nodes ( )

Return this light's shader nodes after inlining. Nested groups, repeat zones, and similar constructs are flattened out of the node tree first.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data | ID.override_library ID.preview Light.type Light.use_temperature Light.color Light.temperature Light.temperature_color Light.specular_factor Light.diffuse_factor Light.transmission_factor Light.volume_factor Light.use_custom_distance Light.cutoff_distance Light.use_shadow Light.exposure Light.normalize Light.node_tree Light.use_nodes Light.animation_data Light.cycles |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Light.area Light.inline_shader_nodes Light.bl_rna_get_subclass Light.bl_rna_get_subclass_py |

## PreferencesEdit(bpy_struct)

### PreferencesEdit(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesEdit ( bpy_struct )

Options governing how you interact with Blender's data

auto_keying_mode

How automatic keyframes get inserted for Objects and Bones (the default applied to new Scenes) (default '`ADD_REPLACE_KEYS`' )

Type :

Literal[‘`ADD_REPLACE_KEYS`’, ‘`REPLACE_KEYS`’]

collection_instance_empty_size

Size at which the empty is drawn for newly created collection instances (in [0.001, inf], default 1.0)

Type :

float

connect_strips_by_default

Automatically connect freshly added movie strips when they span several channels (default True)

Type :

bool

fcurve_new_auto_smoothing

Auto Handle Smoothing mode applied to F-Curves as they are created (default '`CONT_ACCEL`' )

Type :

Literal[Fcurve Auto Smoothing Items]

fcurve_unselected_alpha

How transparent unselected F-Curves appear over the Graph Editor background (in [0.001, 1], default 0.25)

Type :

float

grease_pencil_default_color

The color given to newly created annotation layers (array of 4 items, in [0, inf], default (0.38, 0.61, 0.78, 0.9))

Type :

bpy_prop_array[float]

grease_pencil_eraser_radius

Size of the eraser ‘brush’ (in [1, 500], default 25)

Type :

int

grease_pencil_euclidean_distance

How far the mouse must travel while drawing for a stroke point to be kept (in [0, 100], default 2)

Type :

int

grease_pencil_manhattan_distance

Per-axis mouse travel needed before a stroke point is recorded (in [0, 100], default 1)

Type :

int

key_insert_channels

Channels that receive keys when no keying set is active (default { '`CUSTOM_PROPS`' , 'LOCATION' , 'ROTATION' , 'SCALE' })

Type :

set[Literal[‘LOCATION’, ‘ROTATION’, ‘SCALE’, ‘`ROTATE_MODE`’, ‘`CUSTOM_PROPS`’]]

keyframe_new_handle_type

The handle type assigned to handles on new keyframes (default '`AUTO_CLAMPED`' )

Type :

Literal[Keyframe Handle Type Items]

keyframe_new_interpolation_type

Interpolation applied to the first keyframe of newly created F-Curves (later keyframes inherit it from the one before) (default 'BEZIER' )

Type :

Literal[Beztriple Interpolation Mode Items]

material_link

Choose whether the material attaches to the object data or to the object block (default 'OBDATA' )

- OBDATA
Object Data – Attach the material to the object data.

- OBJECT
Object – Attach the material to the object block instead.

Type :

Literal[‘OBDATA’, ‘OBJECT’]

node_margin

Smallest gap kept between nodes when Auto-offsetting them (in [0, 255], default 40)

Type :

int

node_preview_resolution

Resolution of Shader node previews (lower it for better performance) (in [50, 250], default 120)

Type :

int

node_use_insert_offset

Push neighboring nodes in a chain aside automatically when a node is inserted (default True)

Type :

bool

object_align

How objects added from a 3D viewport menu are aligned by default (default 'WORLD' )

- WORLD
World – Line new objects up with the world coordinate system.

- VIEW
View – Line new objects up with the active 3D view orientation.

- CURSOR
3D Cursor – Line new objects up with the 3D Cursor’s rotation.

Type :

Literal[‘WORLD’, ‘VIEW’, ‘CURSOR’]

sculpt_paint_overlay_color

The texture overlay's color (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

show_only_selected_curve_keyframes

Limit visible, editable keyframes to those on selected F-Curves (default False)

Type :

bool

undo_memory_limit

Cap on memory use in megabytes (0 means unlimited) (in [0, inf], default 0)

Type :

int

undo_steps

How many undo steps are kept (lower this to save memory) (in [0, 256], default 32)

Type :

int

use_anim_channel_group_colors

Color animation channel groups, typically to surface bone group colors (default False)

Type :

bool

use_auto_keyframe_insert_needed

Let Auto-Keying omit keys that would not change the animation (default True)

Type :

bool

use_auto_keying

Insert keyframes automatically for Objects and Bones (the default applied to new Scenes) (default False)

Type :

bool

use_auto_keying_warning

Flag a warning while transforming objects and bones when auto keying is on (default True)

Type :

bool

use_cursor_lock_adjust

Set the cursor without it ‘jumping’ to the new spot (when lock-to-cursor is in use) (default True)

Type :

bool

use_duplicate_action

Duplicate actions along with their data-blocks (default True)

Type :

bool

use_duplicate_armature

Duplicate armature data along with the object (default True)

Type :

bool

use_duplicate_camera

Duplicate camera data along with the object (default True)

Type :

bool

use_duplicate_curve

Duplicate curve data along with the object (default True)

Type :

bool

use_duplicate_curves

Duplicate curves data along with the object (default True)

Type :

bool

use_duplicate_grease_pencil

Duplicate Grease Pencil data along with the object (default True)

Type :

bool

use_duplicate_lattice

Duplicate lattice data along with the object (default True)

Type :

bool

use_duplicate_light

Duplicate light data along with the object (default True)

Type :

bool

use_duplicate_lightprobe

Duplicate light probe data along with the object (default True)

Type :

bool

use_duplicate_material

Duplicate material data along with the object (default False)

Type :

bool

use_duplicate_mesh

Duplicate mesh data along with the object (default True)

Type :

bool

use_duplicate_metaball

Duplicate metaball data along with the object (default True)

Type :

bool

use_duplicate_node_tree

Copy node groups when their nodes are duplicated in the node editor (default False)

Type :

bool

use_duplicate_particle

Duplicate particle systems along with the object (default False)

Type :

bool

use_duplicate_pointcloud

Duplicate point cloud data along with the object (default True)

Type :

bool

use_duplicate_speaker

Duplicate speaker data along with the object (default True)

Type :

bool

use_duplicate_surface

Duplicate surface data along with the object (default True)

Type :

bool

use_duplicate_text

Duplicate text data along with the object (default True)

Type :

bool

use_duplicate_volume

Duplicate volume data along with the object (default False)

Type :

bool

use_enter_edit_mode

Drop straight into edit mode after a new object is added (default False)

Type :

bool

use_fcurve_high_quality_drawing

Render F-Curves with Anti-Aliasing (turn off for better performance) (default True)

Type :

bool

use_global_undo

Global undo retains a full in-memory copy of the file itself, which uses extra memory (default True)

Type :

bool

use_insertkey_xyz_to_rgb

Tie the color of new transformation F-Curves (Location, Rotation, Scale) to the transform axis (default True)

Type :

bool

use_keyframe_insert_available

Only key properties that already carry animation (default False)

Type :

bool

use_keyframe_insert_needed

While keying by hand, drop keys that would not change the animation (default False)

Type :

bool

use_mouse_depth_cursor

Position the cursor using the surface depth (default True)

Type :

bool

use_negative_frames

Allow the current frame number to be set to a negative value by hand (default False)

Type :

bool

use_text_edit_auto_close

Close matching character pairs automatically while typing in the text editor (default False)

Type :

bool

use_visual_keying

Apply Visual keying automatically to constrained objects (default False)

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

| Preferences.edit | |

## PreferencesFilePaths(bpy_struct)

### PreferencesFilePaths(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesFilePaths ( bpy_struct )

Default locations used for external files

active_asset_library

Which asset library is currently being edited in the Preferences UI, given by index (in [-32768, 32767], default 0)

Type :

int

animation_player

Path to a custom player for animations or frame sequences (default “”, never None)

Type :

str

animation_player_preset

Ready-made setups for outside animation players (default 'INTERNAL' )

- INTERNAL
Internal – Blender's own animation player.

- DJV
DJV – An open-source frame player.

- FRAMECYCLER
FrameCycler – IRIDAS's frame player.

- RV
RV – Tweak Software's frame player.

- MPLAYER
MPlayer – Plays video plus PNG/JPEG/SGI image sequences.

- CUSTOM
Custom – Path to your own animation player executable.

Type :

Literal[‘INTERNAL’, ‘DJV’, ‘FRAMECYCLER’, ‘RV’, ‘MPLAYER’, ‘CUSTOM’]

asset_libraries

(default None, readonly)

Type :

AssetLibraryCollection[UserAssetLibrary]

auto_save_time

Minutes that elapse between automatic temporary saves (in [1, 60], default 2)

Type :

int

file_preview_type

Which kind of blend preview to generate (default 'AUTO' )

- NONE
None – Skip generating blend previews.

- AUTO
Auto – Pick the most suitable preview type for you.

- SCREENSHOT
Screenshot – Grab the whole window.

- CAMERA
Camera View – A Workbench render of the scene.

Type :

Literal[‘NONE’, ‘AUTO’, ‘SCREENSHOT’, ‘CAMERA’]

font_directory

Where fonts are looked for by default when loading (default “”, never None, blend relative // prefix supported)

Type :

str

i18n_branches_directory

Path to the ‘/branches’ folder of your local svn-translation checkout, enabling translation straight from the UI (default “”, never None)

Type :

str

image_editor

Path to an image editor (default “”, never None)

Type :

str

recent_files

Upper bound on how many recently opened files are remembered (in [0, 1000], default 200)

Type :

int

render_cache_directory

Location used to cache raw render results (default “”, never None, blend relative // prefix supported)

Type :

str

render_output_directory

Default render output folder used for new scenes (default “”, never None, blend relative // prefix supported)

Type :

str

save_version

How many previous versions are retained in the current directory on a manual save (in [0, 32], default 1)

Type :

int

script_directories

(default None, readonly)

Type :

ScriptDirectoryCollection[ScriptDirectory]

show_hidden_files_datablocks

Reveal files and data-blocks that are usually hidden (default True)

Type :

bool

show_recent_locations

Display the Recent locations list within the File Browser (default True)

Type :

bool

show_system_bookmarks

Display the System locations list within the File Browser (default True)

Type :

bool

sound_directory

Where sounds are looked for by default (default “”, never None, blend relative // prefix supported)

Type :

str

temporary_directory

Folder used to hold temporary save files. It must point to an existing directory, otherwise it is ignored (default “”, never None)

Type :

str

text_editor

Command that launches the text editor, given as a full path or a command on $PATH.
Leave blank to fall back to the internal editor

(default “”, never None)

Type :

str

text_editor_args

Sets the exact argument layout the text editor uses when opening files. The available expansions are:

$filepath The file's absolute path.
$line Which line to jump to (Optional).
$column Which column, counted from the line's start, to jump to (Optional).
$line0 & column0 start at zero.
Example: -f $filepath -l $line -c $column

(default “”, never None)

Type :

str

texture_directory

Where textures are looked for by default (default “”, never None, blend relative // prefix supported)

Type :

str

use_auto_save_temporary_files

Write temporary files to the temp directory on their own, tagged by process ID.
Warning: data in Sculpt and edit mode is left unsaved

(default True)

Type :

bool

use_extension_online_access_handled

Set once the user has seen the “Online Access” prompt and chosen a response (default False)

Type :

bool

use_file_compression

Compress .blend files as they are saved (default True)

Type :

bool

use_filter_files

Filter the files shown in the File Browser (default True)

Type :

bool

use_load_ui

Restore the saved interface layout when opening .blend files (default True)

Type :

bool

use_relative_paths

Default the file selector to relative paths while none has been set yet (default True)

Type :

bool

use_scripts_auto_execute

Let any .blend file run scripts on its own (risky with files from sources you don't trust) (default False)

Type :

bool

use_tabs_as_spaces

Turn every new tab into spaces for new and opened text files (default True)

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

| Preferences.filepaths | |

## See also

- [Bpy Struct](bpy-struct.md)

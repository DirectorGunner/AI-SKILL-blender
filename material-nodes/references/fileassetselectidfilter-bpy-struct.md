# Fileassetselectidfilter Bpy Struct, Fileselectidfilter Bpy Struct, Fileselectparams Bpy Struct, Foreachgeometryelementgenerationitem Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FileAssetSelectIDFilter(bpy_struct); FileSelectIDFilter(bpy_struct); FileSelectParams(bpy_struct); ForeachGeometryElementGenerationItem(bpy_struct); ForeachGeometryElementInputItem(bpy_struct); ForeachGeometryElementMainItem(bpy_struct).

## FileAssetSelectIDFilter(bpy_struct)

### FileAssetSelectIDFilter(bpy_struct)

base class — bpy_struct

class bpy.types. FileAssetSelectIDFilter ( bpy_struct )

Controls which asset types appear or stay hidden while an asset library is being browsed.

experimental_filter_annotations

Display Annotation data-blocks (default False)

Type :

bool

experimental_filter_armature

Display Armature data-blocks (default False)

Type :

bool

experimental_filter_cachefile

Display Cache File data-blocks (default False)

Type :

bool

experimental_filter_camera

Display Camera data-blocks (default False)

Type :

bool

experimental_filter_curve

Display Curve data-blocks (default False)

Type :

bool

experimental_filter_curves

Toggle Curves data-blocks (default False)

Type :

bool

experimental_filter_font

Display Font data-blocks (default False)

Type :

bool

experimental_filter_grease_pencil

Display Grease Pencil data-blocks (default False)

Type :

bool

experimental_filter_image

Display Image data-blocks (default False)

Type :

bool

experimental_filter_lattice

Display Lattice data-blocks (default False)

Type :

bool

experimental_filter_light

Display Light data-blocks (default False)

Type :

bool

experimental_filter_light_probe

Display Light Probe data-blocks (default False)

Type :

bool

experimental_filter_linestyle

Display Freestyle's Line Style data-blocks (default False)

Type :

bool

experimental_filter_mask

Display Mask data-blocks (default False)

Type :

bool

experimental_filter_mesh

Display Mesh data-blocks (default False)

Type :

bool

experimental_filter_metaball

Display Metaball data-blocks (default False)

Type :

bool

experimental_filter_movie_clip

Display Movie Clip data-blocks (default False)

Type :

bool

experimental_filter_paint_curve

Display Paint Curve data-blocks (default False)

Type :

bool

experimental_filter_palette

Display Palette data-blocks (default False)

Type :

bool

experimental_filter_particle_settings

Display Particle Settings data-blocks (default False)

Type :

bool

experimental_filter_pointcloud

Toggle Point Cloud data-blocks (default False)

Type :

bool

experimental_filter_sound

Display Sound data-blocks (default False)

Type :

bool

experimental_filter_speaker

Display Speaker data-blocks (default False)

Type :

bool

experimental_filter_text

Display Text data-blocks (default False)

Type :

bool

experimental_filter_texture

Display Texture data-blocks (default False)

Type :

bool

experimental_filter_volume

Toggle Volume data-blocks (default False)

Type :

bool

experimental_filter_work_space

Display workspace data-blocks (default False)

Type :

bool

filter_action

Display Action data-blocks (default False)

Type :

bool

filter_brush

Display Brushes data-blocks (default False)

Type :

bool

filter_group

Display Collection data-blocks (default False)

Type :

bool

filter_material

Display Material data-blocks (default False)

Type :

bool

filter_node_tree

Display Node Tree data-blocks (default False)

Type :

bool

filter_object

Display Object data-blocks (default False)

Type :

bool

filter_scene

Display Scene data-blocks (default False)

Type :

bool

filter_world

Display World data-blocks (default False)

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

| FileAssetSelectParams.filter_asset_id | |

## FileSelectIDFilter(bpy_struct)

### FileSelectIDFilter(bpy_struct)

base class — bpy_struct

class bpy.types. FileSelectIDFilter ( bpy_struct )

Controls which ID types appear or stay hidden while a library is being browsed.

category_animation

Display animation data (default False)

Type :

bool

category_environment

Display worlds, lights, cameras and speakers (default False)

Type :

bool

category_geometry

Display mesh, curve, lattice, armature and metaball data (default False)

Type :

bool

category_image

Display images, movie clips, sounds and masks (default False)

Type :

bool

category_misc

Display the remaining data types (default False)

Type :

bool

category_object

Display objects and collections (default False)

Type :

bool

category_scene

Display scenes (default False)

Type :

bool

category_shading

Display materials, node-trees, textures and Freestyle's line-styles (default False)

Type :

bool

filter_action

Display Action data-blocks (default False)

Type :

bool

filter_annotations

Display Annotation data-blocks (default False)

Type :

bool

filter_armature

Display Armature data-blocks (default False)

Type :

bool

filter_brush

Display Brushes data-blocks (default False)

Type :

bool

filter_cachefile

Display Cache File data-blocks (default False)

Type :

bool

filter_camera

Display Camera data-blocks (default False)

Type :

bool

filter_curve

Display Curve data-blocks (default False)

Type :

bool

filter_curves

Toggle Curves data-blocks (default False)

Type :

bool

filter_font

Display Font data-blocks (default False)

Type :

bool

filter_grease_pencil

Display Grease Pencil data-blocks (default False)

Type :

bool

filter_group

Display Collection data-blocks (default False)

Type :

bool

filter_image

Display Image data-blocks (default False)

Type :

bool

filter_lattice

Display Lattice data-blocks (default False)

Type :

bool

filter_light

Display Light data-blocks (default False)

Type :

bool

filter_light_probe

Display Light Probe data-blocks (default False)

Type :

bool

filter_linestyle

Display Freestyle's Line Style data-blocks (default False)

Type :

bool

filter_mask

Display Mask data-blocks (default False)

Type :

bool

filter_material

Display Material data-blocks (default False)

Type :

bool

filter_mesh

Display Mesh data-blocks (default False)

Type :

bool

filter_metaball

Display Metaball data-blocks (default False)

Type :

bool

filter_movie_clip

Display Movie Clip data-blocks (default False)

Type :

bool

filter_node_tree

Display Node Tree data-blocks (default False)

Type :

bool

filter_object

Display Object data-blocks (default False)

Type :

bool

filter_paint_curve

Display Paint Curve data-blocks (default False)

Type :

bool

filter_palette

Display Palette data-blocks (default False)

Type :

bool

filter_particle_settings

Display Particle Settings data-blocks (default False)

Type :

bool

filter_pointcloud

Toggle Point Cloud data-blocks (default False)

Type :

bool

filter_scene

Display Scene data-blocks (default False)

Type :

bool

filter_sound

Display Sound data-blocks (default False)

Type :

bool

filter_speaker

Display Speaker data-blocks (default False)

Type :

bool

filter_text

Display Text data-blocks (default False)

Type :

bool

filter_texture

Display Texture data-blocks (default False)

Type :

bool

filter_volume

Toggle Volume data-blocks (default False)

Type :

bool

filter_work_space

Display workspace data-blocks (default False)

Type :

bool

filter_world

Display World data-blocks (default False)

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

| FileSelectParams.filter_id | |

## FileSelectParams(bpy_struct)

### FileSelectParams(bpy_struct)

base class — bpy_struct

subclasses —
FileAssetSelectParams

class bpy.types. FileSelectParams ( bpy_struct )

File Select Parameters

directory

Folder shown in the file browser (default b””, never None)

Type :

bytes

display_size

Set how big the thumbnails are (in [16, 256], default 96)

Type :

int

display_size_discrete

Set thumbnail size in fixed steps (default 'TINY' )

Type :

Literal[‘TINY’, ‘SMALL’, ‘NORMAL’, ‘BIG’, ‘LARGE’]

display_type

How the file list is shown (default '`LIST_VERTICAL`' )

- `LIST_VERTICAL`
Vertical List – Lay the files out as a vertical list.

- `LIST_HORIZONTAL`
Horizontal List – Lay the files out as a horizontal list.

- THUMBNAIL
Thumbnails – Lay the files out as thumbnails.

Type :

Literal[‘`LIST_VERTICAL`’, ‘`LIST_HORIZONTAL`’, ‘THUMBNAIL’]

filename

The file currently active in the file browser (default “”, never None)

Type :

str

filter_glob

UNIX shell-style filename matching; accepts wildcards (‘*’) and a list of patterns split by ‘;’ (default “”, never None)

Type :

str

filter_id

Controls which ID types appear or stay hidden while a library is being browsed (readonly, never None)

Type :

FileSelectIDFilter

filter_search

Filter on name or tag, with ‘*’ as a wildcard (default “”, never None)

Type :

str

list_column_size

Column width used in horizontal list views (in [32, 750], default 32)

Type :

int

list_display_size

Set thumbnail size for list views (in [16, 128], default 32)

Type :

int

recursion_level

How many dirtree levels are shown at the same time (default 'NONE' )

- NONE
None – List only the current directory's contents, without recursing.

- BLEND
Blend File – List the contents of .blend files.

- `ALL_1`
One Level – List the contents of every sub-directory, recursing one level deep.

- `ALL_2`
Two Levels – List the contents of every sub-directory, recursing two levels deep.

- `ALL_3`
Three Levels – List the contents of every sub-directory, recursing three levels deep.

Type :

Literal[‘NONE’, ‘BLEND’, ‘`ALL_1`’, ‘`ALL_2`’, ‘`ALL_3`’]

show_details_datetime

Add a column showing each file's modification date and time (default False)

Type :

bool

show_details_size

Add a column showing each file's size (default False)

Type :

bool

show_hidden

Reveal hidden dot files (default True)

Type :

bool

sort_method

(default '`FILE_SORT_ALPHA`' )

Type :

Literal[Fileselect Params Sort Items]

title

The file browser's title (default “”, readonly, never None)

Type :

str

use_filter

Turn on file filtering (default False)

Type :

bool

use_filter_asset_only

Hide entries inside .blend files that are not data-blocks carrying asset metadata (default False)

Type :

bool

use_filter_backup

Reveal .blend1, .blend2, and similar files (default False)

Type :

bool

use_filter_blender

Reveal .blend files (default False)

Type :

bool

use_filter_blendid

Reveal the items inside .blend files (objects, materials, etc.) (default False)

Type :

bool

use_filter_folder

Reveal folders (default False)

Type :

bool

use_filter_font

Reveal font files (default False)

Type :

bool

use_filter_image

Reveal image files (default False)

Type :

bool

use_filter_movie

Reveal movie files (default False)

Type :

bool

use_filter_script

Reveal script files (default False)

Type :

bool

use_filter_sound

Reveal sound files (default False)

Type :

bool

use_filter_text

Reveal text files (default False)

Type :

bool

use_filter_volume

Reveal 3D volume files (default False)

Type :

bool

use_library_browsing

Whether browsing the contents of Blender files is allowed (default False, readonly)

Type :

bool

use_sort_invert

Sort entries in descending order, highest value first (default False)

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

| SpaceFileBrowser.params | UILayout.template_file_select_path |

## ForeachGeometryElementGenerationItem(bpy_struct)

### ForeachGeometryElementGenerationItem(bpy_struct)

base class — bpy_struct

class bpy.types. ForeachGeometryElementGenerationItem ( bpy_struct )

color

Color of the corresponding socket type in the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

domain

Domain that the field is evaluated on (default 'POINT' )

Type :

Literal[Attribute Domain Items]

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| GeometryNodeForeachGeometryElementOutput.generation_items NodeGeometryForeachGeometryElementGenerationItems.new | NodeGeometryForeachGeometryElementGenerationItems.remove |

## ForeachGeometryElementInputItem(bpy_struct)

### ForeachGeometryElementInputItem(bpy_struct)

base class — bpy_struct

class bpy.types. ForeachGeometryElementInputItem ( bpy_struct )

color

Color of the corresponding socket type in the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| GeometryNodeForeachGeometryElementOutput.input_items NodeGeometryForeachGeometryElementInputItems.new | NodeGeometryForeachGeometryElementInputItems.remove |

## ForeachGeometryElementMainItem(bpy_struct)

### ForeachGeometryElementMainItem(bpy_struct)

base class — bpy_struct

class bpy.types. ForeachGeometryElementMainItem ( bpy_struct )

color

Color of the corresponding socket type in the node editor (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0), readonly)

Type :

bpy_prop_array[float]

name

(default “”, never None)

Type :

str

socket_type

(default 'FLOAT' )

Type :

Literal[Node Socket Data Type Items]

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

| GeometryNodeForeachGeometryElementOutput.main_items NodeGeometryForeachGeometryElementMainItems.new | NodeGeometryForeachGeometryElementMainItems.remove |

## See also

- [Bpy Struct](bpy-struct.md)

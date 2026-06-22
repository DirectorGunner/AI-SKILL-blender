# Blenddataarmatures Bpy Prop Collection, Blenddatabrushes Bpy Prop Collection, Blenddatacachefiles Bpy Prop Collection, Blenddatacollections Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendDataArmatures(bpy_prop_collection); BlendDataBrushes(bpy_prop_collection); BlendDataCacheFiles(bpy_prop_collection); BlendDataCollections(bpy_prop_collection); BlendDataCurves(bpy_prop_collection); BlendDataFonts(bpy_prop_collection); BlendDataGreasePencilsV3(bpy_prop_collection); BlendDataHairCurves(bpy_prop_collection); BlendDataLattices(bpy_prop_collection).

## BlendDataArmatures(bpy_prop_collection)

Registry of painting and sculpting brush definitions.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataBrushes ( bpy_prop_collection )

List of paint tool configurations

new ( name , * , mode = '`TEXTURE_PAINT`' ) 

Add a brush to the database

Parameters :

- name ( str ) – New name for the data-block (never None)

- mode (Literal[Object Mode Items]) – Paint Mode for the new brush (optional)

Returns :

New brush data-block

Return type :

Brush

remove ( brush , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Delete a brush from the current file

Parameters :

- brush (Brush) – Brush to remove (never None)

- do_unlink ( bool ) – Break all references to this brush before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

create_gpencil_data ( brush ) 

Extend a brush with hand-drawn tool properties

Parameters :

brush (Brush) – Brush (never None)

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

| BlendData.brushes | |

## BlendDataBrushes(bpy_prop_collection)

Storage for imported animation cache sequences.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataCacheFiles ( bpy_prop_collection )

Library of cached animation playback streams

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.cache_files | |

## BlendDataCacheFiles(bpy_prop_collection)

Registry of viewpoint definitions.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataCameras ( bpy_prop_collection )

Collection of cameras

new ( name ) 

Register a camera in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New camera data-block

Return type :

Camera

remove ( camera , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a camera from the current file

Parameters :

- camera (Camera) – Camera to remove (never None)

- do_unlink ( bool ) – Break all references to this camera before deletion (WARNING: will also delete objects instancing that camera data) (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.cameras | |

## BlendDataCollections(bpy_prop_collection)

Registry of parametric curve objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataCurves ( bpy_prop_collection )

List of curve geometry types

new ( name , type ) 

Register a curve in the database

Parameters :

- name ( str ) – New name for the data-block (never None)

- type (Literal[Object Type Curve Items]) – Type, The type of curve to add

Returns :

New curve data-block

Return type :

Curve

remove ( curve , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a curve from the current file

Parameters :

- curve (Curve) – Curve to remove (never None)

- do_unlink ( bool ) – Break all references to this curve before deletion (WARNING: will also delete objects instancing that curve data) (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.curves | |

## BlendDataCurves(bpy_prop_collection)

Registry of scalable text font assets.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataFonts ( bpy_prop_collection )

Collection of fonts

load ( filepath , * , check_existing = False ) 

Load a font file into the database

Parameters :

- filepath ( str ) – path of the font to load (never None, blend relative // prefix supported)

- check_existing ( bool ) – Using existing data-block if this file is already loaded (optional)

Returns :

New font data-block

Return type :

VectorFont

remove ( vfont , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unload a font from the current file

Parameters :

- vfont (VectorFont) – Font to remove (never None)

- do_unlink ( bool ) – Break all references to this font before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.fonts | |

## BlendDataFonts(bpy_prop_collection)

Registry of hand-drawn sketch objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataGreasePencilsV3 ( bpy_prop_collection )

Collection of Grease Pencils

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

new ( name ) 

Insert a sketch into the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New Grease Pencil data-block

Return type :

GreasePencil

remove ( grease_pencil , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Remove a sketch from the current file

Parameters :

- grease_pencil (GreasePencil) – Grease Pencil to remove (never None)

- do_unlink ( bool ) – Break all references to this Grease Pencil before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

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

| BlendData.grease_pencils | |

## BlendDataGreasePencilsV3(bpy_prop_collection)

Registry of procedural hair objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataHairCurves ( bpy_prop_collection )

Collection of hair curves

new ( name ) 

Add a hair object to the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New curves data-block

Return type :

Curves

remove ( curves , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Erase a curves object from the current file

Parameters :

- curves (Curves) – Curves data-block to remove (never None)

- do_unlink ( bool ) – Break all references to this curves before deletion (WARNING: will also delete objects instancing that curves data) (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.hair_curves | |

## BlendDataHairCurves(bpy_prop_collection)

Registry of raster and procedural image textures.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataImages ( bpy_prop_collection )

Collection of images

new ( name , width , height , * , alpha = False , float_buffer = False , stereo3d = False , is_data = False , tiled = False ) 

Create a new image in the database

Parameters :

- name ( str ) – New name for the data-block (never None)

- width ( int ) – Width of the image (in [1, inf])

- height ( int ) – Height of the image (in [1, inf])

- alpha ( bool ) – Alpha, Use alpha channel (optional)

- float_buffer ( bool ) – Float Buffer, Create an image with floating-point color (optional)

- stereo3d ( bool ) – Stereo 3D, Create left and right views (optional)

- is_data ( bool ) – Is Data, Create image with non-color data color space (optional)

- tiled ( bool ) – Tiled, Create a tiled image (optional)

Returns :

New image data-block

Return type :

Image

load ( filepath , * , check_existing = False ) 

Import an image file into the database

Parameters :

- filepath ( str ) – Path of the file to load (never None, blend relative // prefix supported)

- check_existing ( bool ) – Using existing data-block if this file is already loaded (optional)

Returns :

New image data-block

Return type :

Image

remove ( image , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unload an image from the current file

Parameters :

- image (Image) – Image to remove (never None)

- do_unlink ( bool ) – Break all references to this image before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.images | |

## BlendDataLattices(bpy_prop_collection)

Registry of linked external blend files.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataLibraries ( bpy_prop_collection )

Collection of libraries

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

remove ( library , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Disconnect a library from the current file

Parameters :

- library (Library) – Library to remove (never None)

- do_unlink ( bool ) – Break all references to this library before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

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

load ( filepath , * , link = False , pack = False , relative = False , set_fake = False , recursive = False , reuse_local_id = False , assets_only = False , clear_asset_data = False , create_liboverrides = False , reuse_liboverrides = False , create_liboverrides_runtime = False ) 

Open a context manager that grants access to 2 library objects on entry.
Each object has properties that map to bpy.data collections; the values are lists of names to acquire.

Parameters :

- filepath ( str | bytes ) – The path to a blend file.

- link ( bool ) – When False reference to the original file is lost.

- pack ( bool ) – If True, and link is also True, embed linked data-blocks into the current blend-file.

- relative ( bool ) – When True the path is stored relative to the open blend file.

- set_fake ( bool ) – If True, set fake user on appended IDs.

- recursive ( bool ) – If True, also make indirect dependencies of appended libraries local.

- reuse_local_id ( bool ) – If True, try to re-use previously appended matching ID on new append.

- assets_only ( bool ) – If True, only list data-blocks marked as assets.

- clear_asset_data ( bool ) – If True, clear the asset data on append (it is always kept for linked data).

- create_liboverrides ( bool ) – If True and link is True, liboverrides will
be created for linked data.

- reuse_liboverrides ( bool ) – If True and create_liboverride is True,
search for existing liboverride first.

- create_liboverrides_runtime ( bool ) – If True and create_liboverride is True,
create (or search for existing) runtime liboverride.

`\text
import bpy

filepath = "//link_library.blend"

### Load a single scene we know the name of.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
data_dst.scenes = ["Scene"]

### Load all meshes.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
data_dst.meshes = data_src.meshes

### Link all objects starting with "A".
with bpy.data.libraries.load(filepath, link=True) as (data_src, data_dst):
data_dst.objects = [name for name in data_src.objects if name.startswith("A")]

### Append everything.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
for attr in dir(data_dst):
setattr(data_dst, attr, getattr(data_src, attr))

### The loaded objects can be accessed from `data_dst` outside of the context
### since loading the data replaces the strings for the data-blocks or None
### if the data-block could not be loaded.
with bpy.data.libraries.load(filepath) as (data_src, data_dst):
data_dst.meshes = data_src.meshes
### Now operate directly on the loaded data.
for mesh in data_dst.meshes:
if mesh is not None:
print(mesh.name)
`\

write ( filepath , datablocks , * , path_remap = 'NONE' , fake_user = False , compress = False ) 

Serialize a set of data-blocks into a blend file.

Note

Indirectly referenced data-blocks will be expanded and written too.

Parameters :

- filepath ( str | bytes ) – The path to write the blend-file.

- datablocks (set[bpy.types.ID]) – set of data-blocks.

- path_remap ( str ) – Optionally remap paths when writing the file:

- NONE No path manipulation (default).

- RELATIVE Remap paths that are already relative to the new location.

- `RELATIVE_ALL` Remap all paths to be relative to the new location.

- ABSOLUTE Make all paths absolute on writing.

- fake_user ( bool ) – When True, data-blocks will be written with fake-user flag enabled.

- compress ( bool ) – When True, write a compressed blend file.

`\text
import bpy

filepath = "//new_library.blend"

### Write selected objects and their data to a blend file.
data_blocks = set(bpy.context.selected_objects)
bpy.data.libraries.write(filepath, data_blocks)

### Write all meshes starting with a capital letter and
### set them with fake-user enabled so they aren't lost on re-saving.
data_blocks = {mesh for mesh in bpy.data.meshes if mesh.name[:1].isupper()}
bpy.data.libraries.write(filepath, data_blocks, fake_user=True)

### Write all materials, textures and node groups to a library.
data_blocks = {*bpy.data.materials, *bpy.data.textures, *bpy.data.node_groups}
bpy.data.libraries.write(filepath, data_blocks)
`\

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| BlendData.libraries | |

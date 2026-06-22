# Blenddata Bpy Struct, Blenddataimages Bpy Prop Collection, Blenddatamaterials Bpy Prop Collection, Blenddatanodetrees Bpy Prop Collection ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendData(bpy_struct); BlendDataImages(bpy_prop_collection); BlendDataMaterials(bpy_prop_collection); BlendDataNodeTrees(bpy_prop_collection); BlendFileColorspace(bpy_struct).

## BlendData(bpy_struct)

Root container object that provides access to all data-blocks within a .blend file.

base class — bpy_struct

class bpy.types. BlendData ( bpy_struct )

Hierarchical registry holding all data blocks and assets in a blend file

actions 

Stored motion sequences (default None, readonly)

Type :

BlendDataActions[Action]

annotations 

Deprecated sketching annotation records (default None, readonly)

Type :

BlendDataAnnotations[Annotation]

armatures 

Skeletal rig definitions (default None, readonly)

Type :

BlendDataArmatures[Armature]

brushes 

Painting and sculpting tool definitions (default None, readonly)

Type :

BlendDataBrushes[Brush]

cache_files 

Imported geometry cache sequences (default None, readonly)

Type :

BlendDataCacheFiles[CacheFile]

cameras 

Viewpoint definitions (default None, readonly)

Type :

BlendDataCameras[Camera]

collections 

Groupings of objects and hierarchies (default None, readonly)

Type :

BlendDataCollections[Collection]

colorspace 

Color management and rendering gamma profile (readonly, never None)

Type :

BlendFileColorspace

curves 

Parametric curve objects (default None, readonly)

Type :

BlendDataCurves[Curve]

filepath 

Disk path to the open .blend file (default "", readonly, never None)

Type :

str

fonts 

Loaded TrueType and OpenType font assets (default None, readonly)

Type :

BlendDataFonts[VectorFont]

grease_pencils 

Hand-drawn sketch objects (default None, readonly)

Type :

BlendDataGreasePencilsV3[GreasePencil]

hair_curves 

Procedural hair system objects (default None, readonly)

Type :

BlendDataHairCurves[Curves]

images 

Raster and procedural texture images (default None, readonly)

Type :

BlendDataImages[Image]

is_dirty 

Unsaved modifications exist (default False, readonly)

Type :

bool

is_saved 

File has been written to disk at least once (default False, readonly)

Type :

bool

lattices 

Deformation cage objects (default None, readonly)

Type :

BlendDataLattices[Lattice]

libraries 

Linked external blend files (default None, readonly)

Type :

BlendDataLibraries[Library]

lightprobes 

Precomputed radiance volumes and probes (default None, readonly)

Type :

BlendDataProbes[LightProbe]

lights 

Illumination sources (default None, readonly)

Type :

BlendDataLights[Light]

linestyles 

Non-photorealistic rendering stroke definitions (default None, readonly)

Type :

BlendDataLineStyles[FreestyleLineStyle]

masks 

Motion tracking and compositing masks (default None, readonly)

Type :

BlendDataMasks[Mask]

materials 

Surface appearance definitions (default None, readonly)

Type :

BlendDataMaterials[Material]

meshes 

Polygon geometry objects (default None, readonly)

Type :

BlendDataMeshes[Mesh]

metaballs 

Implicit surface blob objects (default None, readonly)

Type :

BlendDataMetaBalls[MetaBall]

movieclips 

Imported motion tracking footage (default None, readonly)

Type :

BlendDataMovieClips[MovieClip]

node_groups 

Reusable node setup templates (default None, readonly)

Type :

BlendDataNodeTrees[NodeTree]

objects 

Scene element instances (default None, readonly)

Type :

BlendDataObjects[Object]

paint_curves 

Stored brush stroke paths (default None, readonly)

Type :

BlendDataPaintCurves[PaintCurve]

palettes 

Color swatch collections (default None, readonly)

Type :

BlendDataPalettes[Palette]

particles 

Particle emitter and behavior definitions (default None, readonly)

Type :

BlendDataParticles[ParticleSettings]

pointclouds 

Unstructured point set objects (default None, readonly)

Type :

BlendDataPointClouds[PointCloud]

scenes 

Render and animation scene definitions (default None, readonly)

Type :

BlendDataScenes[Scene]

screens 

Workspace layout configurations (default None, readonly)

Type :

BlendDataScreens[Screen]

shape_keys 

Morph target deformation sequences (default None, readonly)

Type :

bpy_prop_collection[Key]

sounds 

Audio file references (default None, readonly)

Type :

BlendDataSounds[Sound]

speakers 

Audio playback point sources (default None, readonly)

Type :

BlendDataSpeakers[Speaker]

texts 

Stored text documents (default None, readonly)

Type :

BlendDataTexts[Text]

textures 

Texture definitions (default None, readonly)

Type :

BlendDataTextures[Texture]

use_autopack 

Automatically embed external files into the archive (default False)

Type :

bool

version 

Release version when the .blend was last saved (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

volumes 

Volumetric density field objects (default None, readonly)

Type :

BlendDataVolumes[Volume]

window_managers 

Windowing context instances (default None, readonly)

Type :

BlendDataWindowManagers[WindowManager]

workspaces 

Named interface layouts (default None, readonly)

Type :

BlendDataWorkSpaces[WorkSpace]

worlds 

Global environment and lighting definitions (default None, readonly)

Type :

BlendDataWorlds[World]

pack_linked_ids_hierarchy ( root_id ) 

Embed a linked data-block and its dependencies into the current file

Parameters :

root_id (ID) – Root linked ID to pack

Returns :

The packed ID matching the given root ID

Return type :

ID

batch_remove ( ids ) 

Erase multiple IDs in one operation.

Note that this method is faster than repeated calls to remove() (from bpy.types.BlendData
ID collections), but has lower safety/flexibility (it can destabilize Blender, e.g. by removing all scenes…).

Parameters :

ids (Sequence[bpy.types.ID]) – Sequence of IDs (types can be mixed).

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

file_path_foreach ( visit_path_fn , * , subset = None , visit_types = None , flags = {'`SKIP_PACKED`', '`SKIP_WEAK_REFERENCES`'} ) 

Invoke a callback function for all file-path references within data blocks.

For list of valid set members for visit_types, see: bpy.types.KeyingSetPath.id_type.

Parameters :

- visit_path_fn (Callable[[bpy.types.ID, str, Any], str|None]) – function that takes three parameters: the data-block, a file path, and a placeholder for future use. The function should return either None or a str . In the latter case, the visited file path will be replaced with the returned string.

- subset ( set [ str ] | None ) – When given, only these data-blocks and their used file paths will be visited.

- visit_types ( set [ str ] | None ) – When given, only visit data-blocks of these types. Ignored if subset is also given.

- flags ( set [ str ] ) – Set of flags that influence which data-blocks are visited. See File Path Foreach Flag Items.

file_path_map ( * , subset = None , key_types = None , include_libraries = False ) 

Generate a mapping of all ID data-blocks to their external file dependencies.

For list of valid set members for key_types, see: bpy.types.KeyingSetPath.id_type.

Parameters :

- subset (Sequence[bpy.types.ID] | None) – When given, only these data-blocks and their used file paths will be included as keys/values in the map.

- key_types ( set [ str ] | None ) – When given, filter the keys mapped by ID types. Ignored if subset is also given.

- include_libraries ( bool ) – Include library file paths of linked data. False by default.

Returns :

dictionary of bpy.types.ID instances, with sets of file path strings as their values.

Return type :

dict[bpy.types.ID, set[str]]

orphans_purge ( ) 

Erase all IDs that have no references.

Parameters :

- do_local_ids ( bool , optional ) – Include unused local IDs in the deletion, defaults to True

- do_linked_ids ( bool , optional ) – Include unused linked IDs in the deletion, defaults to True

- do_recursive ( bool , optional ) – Recursively check for unused IDs, ensuring no orphaned one remain after a single run of that function, defaults to False

Returns :

The number of deleted IDs.

Return type :

int

static temp_data ( * , filepath = None ) 

A context manager that temporarily creates blender file data.

Parameters :

filepath ( str | bytes | None ) – The file path for the newly temporary data. When None, the path of the currently open file is used.

Returns :

Blend file data which is freed once the context exits.

Return type :

bpy.types.BlendData

user_map ( * , subset = None , key_types = None , value_types = None ) 

Generate a mapping of all ID data-blocks to which other data-blocks reference them.

For list of valid set members for key_types & value_types, see: bpy.types.KeyingSetPath.id_type.

Parameters :

- subset (Sequence[bpy.types.ID] | None) – When passed, only these data-blocks and their users will be included as keys/values in the map.

- key_types ( set [ str ] | None ) – Filter the keys mapped by ID types.

- value_types ( set [ str ] | None ) – Filter the values in the set by ID types.

Returns :

dictionary that maps data-blocks ID's to their users.

Return type :

dict[bpy.types.ID, set[bpy.types.ID]]

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| Context.blend_data | RenderEngine.update |

Holds methods for generating new action recordings.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataActions ( bpy_prop_collection )

Enumeration of motion sequence data

new ( name ) 

Insert a new action into the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New action data-block

Return type :

Action

remove ( action , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Delete an action from the current file

Parameters :

- action (Action) – Action to remove (never None)

- do_unlink ( bool ) – Break all references to this action before deletion (optional)

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

| BlendData.actions | |

## BlendDataImages(bpy_prop_collection)

Registry of deformation cage objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataLattices ( bpy_prop_collection )

Collection of lattices

new ( name ) 

Create a lattice in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New lattice data-block

Return type :

Lattice

remove ( lattice , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unload a lattice from the current file

Parameters :

- lattice (Lattice) – Lattice to remove (never None)

- do_unlink ( bool ) – Break all references to this lattice before deletion (WARNING: will also delete objects instancing that lattice data) (optional)

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

| BlendData.lattices | |

## BlendDataMaterials(bpy_prop_collection)

Registry of polygon geometry objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataMeshes ( bpy_prop_collection )

Collection of meshes

new ( name ) 

Create a mesh in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New mesh data-block

Return type :

Mesh

new_from_object ( object , * , preserve_all_data_layers = False , depsgraph = None ) 

Add a mesh derived from a scene element (returns unevaluated geometry from original, or final evaluated geometry with all modifications applied to evaluated variant)

Parameters :

- object (Object) – Object to create mesh from (never None)

- preserve_all_data_layers ( bool ) – Preserve all data layers in the mesh, like UV maps and vertex groups. By default Blender only computes the subset of data layers needed for viewport display and rendering, for better performance. (optional)

- depsgraph (Depsgraph) – Dependency Graph, Evaluated dependency graph which is required when preserve_all_data_layers is true (optional)

Returns :

Mesh created from object, remove it if it is only used for export

Return type :

Mesh

remove ( mesh , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unload a mesh from the current file

Parameters :

- mesh (Mesh) – Mesh to remove (never None)

- do_unlink ( bool ) – Break all references to this mesh before deletion (WARNING: will also delete objects instancing that mesh data) (optional)

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

| BlendData.meshes | |

## BlendDataNodeTrees(bpy_prop_collection)

Registry of scene element instances.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataObjects ( bpy_prop_collection )

Collection of objects

new ( name , object_data ) 

Add a scene element to the database

Parameters :

- name ( str ) – New name for the data-block (never None)

- object_data (ID) – Object data or None for an empty object

Returns :

New object data-block

Return type :

Object

remove ( object , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Erase a scene element from the current file

Parameters :

- object (Object) – Object to remove (never None)

- do_unlink ( bool ) – Break all references to this object before deletion (optional)

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

| BlendData.objects | |

## BlendFileColorspace(bpy_struct)

### BlendFileColorspace(bpy_struct)

base class — bpy_struct

class bpy.types.BlendFileColorspace(bpy_struct)

Holds metadata about the color encoding system selected for stored data in a blend file.

is_missing_opencolorio_config

An OpenColorIO color scheme, display mode, or gamma profile could not be found, which signals that the OpenColorIO profile applied during file creation is unavailable (default False, readonly)

Type:
bool

working_space

The color reproduction system used for all scene-linear pixel values, as well as for node-based compositing, shader node processing, and geometry node computations (readonly)

- Linear Rec.709
Linear Rec.709 – Linear BT.709 using D65 white illumination.

- Linear Rec.2020
Linear Rec.2020 – Linear BT.2020 using D65 white illumination.

- ACEScg
ACEScg – AP1 linear with ACES reference white.

Type:
Literal['Linear Rec.709', 'Linear Rec.2020', 'ACEScg']

working_space_interop_id

Standard name assigned by the Color Interop Forum for typical color reproduction systems; may be empty when no interop mapping is defined for the selected working space. Frequently encountered assignments: lin_rec709_scene, lin_rec2020_scene, lin_ap1_scene (for ACEScg) (default "", readonly, never None)

Type:
str

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Type designation for the RNA.
- default (bpy.types.Struct | None) – Fallback to return if not located.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Type designation for the RNA.
- default (type | None) – Fallback to return if not located.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.colorspace | |

## See also

- [Bpy Struct](bpy-struct.md)

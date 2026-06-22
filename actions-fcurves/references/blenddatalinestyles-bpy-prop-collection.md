# Blenddatalinestyles Bpy Prop Collection, Blenddatamasks Bpy Prop Collection, Blenddatametaballs Bpy Prop Collection, Blenddatamovieclips Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendDataLineStyles(bpy_prop_collection); BlendDataMasks(bpy_prop_collection); BlendDataMetaBalls(bpy_prop_collection); BlendDataMovieClips(bpy_prop_collection); BlendDataObjects(bpy_prop_collection); BlendDataPaintCurves(bpy_prop_collection); BlendDataPalettes(bpy_prop_collection); BlendDataParticles(bpy_prop_collection); BlendDataPointClouds(bpy_prop_collection); BlendDataScenes(bpy_prop_collection); BlendDataScreens(bpy_prop_collection).

## BlendDataLineStyles(bpy_prop_collection)

Registry of motion tracking and compositing masks.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataMasks ( bpy_prop_collection )

Collection of masks

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

new ( name ) 

Register a mask in the database

Parameters :

name ( str ) – Mask, Name of new mask data-block (never None)

Returns :

New mask data-block

Return type :

Mask

remove ( mask , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a mask from the current file

Parameters :

- mask (Mask) – Mask to remove (never None)

- do_unlink ( bool ) – Break all references to this mask before deletion (optional)

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

| BlendData.masks | |

## BlendDataMasks(bpy_prop_collection)

Registry of surface appearance definitions.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataMaterials ( bpy_prop_collection )

Collection of materials

new ( name ) 

Create a material in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New material data-block

Return type :

Material

create_gpencil_data ( material ) 

Add hand-drawn tool properties to a material

Parameters :

material (Material) – Material (never None)

remove_gpencil_data ( material ) 

Delete hand-drawn tool properties from a material

Parameters :

material (Material) – Material (never None)

remove ( material , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Erase a material from the current file

Parameters :

- material (Material) – Material to remove (never None)

- do_unlink ( bool ) – Break all references to this material before deletion (optional)

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

| BlendData.materials | |

## BlendDataMetaBalls(bpy_prop_collection)

Registry of imported motion tracking footage.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataMovieClips ( bpy_prop_collection )

Collection of movie clips

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

remove ( clip , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Erase a movie clip from the current file.

Parameters :

- clip (MovieClip) – Movie clip to remove (never None)

- do_unlink ( bool ) – Break all references to this movie clip before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

load ( filepath , * , check_existing = False ) 

Link a movie clip into the database from a file (note: check_existing is disabled by default for consistency with other load operations, but using multiple clips with the same file path can create unwanted proxy artifacts)

Parameters :

- filepath ( str ) – path for the data-block (never None, blend relative // prefix supported)

- check_existing ( bool ) – Using existing data-block if this file is already loaded (optional)

Returns :

New movie clip data-block

Return type :

MovieClip

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

| BlendData.movieclips | |

## BlendDataMovieClips(bpy_prop_collection)

Registry of reusable node setup templates.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataNodeTrees ( bpy_prop_collection )

Collection of node trees

new ( name , type ) 

Register a node tree in the database

Parameters :

- name ( str ) – New name for the data-block (never None)

- type ( Literal [ 'GeometryNodeTree' , 'CompositorNodeTree' , 'ShaderNodeTree' , 'TextureNodeTree' ] ) – Type, The type of node_group to add

- GeometryNodeTree
Geometry Node Editor – Advanced geometry editing and tools creation using nodes.

- CompositorNodeTree
Compositor – Create effects and post-process renders, images, and the 3D Viewport.

- ShaderNodeTree
Shader Editor – Edit materials, lights, and world shading using nodes.

- TextureNodeTree
Texture Node Editor – Edit textures using nodes.

Returns :

New node tree data-block

Return type :

NodeTree

remove ( tree , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister a node tree from the current file

Parameters :

- tree (NodeTree) – Node tree to remove (never None)

- do_unlink ( bool ) – Break all references to this node tree before deletion (optional)

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

| BlendData.node_groups | |

## BlendDataObjects(bpy_prop_collection)

### BlendDataObjects(bpy_prop_collection)
base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataObjects ( bpy_prop_collection )
A collection of objects.

new ( name , object_data )
Adds a new object to the main database.
Parameters:
- name ( str ) – New name for the data-block (never None)
- object_data (ID) – Object data, or None for an empty object
Returns: New object data-block
Return type: Object

remove ( object , * , do_unlink = True , do_id_user = True , do_ui_user = True )
Removes an object from the current blendfile.
Parameters:
- object (Object) – Object to remove (never None)
- do_unlink ( bool ) – Unlink all usages of this object before deleting it (optional)
- do_id_user ( bool ) – Decrement user counter of all data-blocks used by this object (optional)
- do_ui_user ( bool ) – Make sure interface does not reference this object (optional)

tag ( value )
Tags the objects.
Parameters: value ( bool ) – Value

classmethod bl_rna_get_subclass ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.
Returns: The RNA type or default when not found.
Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default ( type | None ) – The value to return when not found.
Returns: The class or default when not found.
Return type: type

### Inherited Properties
| bpy_struct.id_data | |

### Inherited Functions
| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References
| BlendData.objects | |

## BlendDataPaintCurves(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataPaintCurves ( bpy_prop_collection )

Collection of paint curves

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

| BlendData.paint_curves | |

## BlendDataPalettes(bpy_prop_collection)

### BlendDataPalettes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataPalettes(bpy_prop_collection)

Provides access to palette collections stored within Blender's database.

new(name)

Creates and registers a fresh palette in Blender's main database.

Parameters:
- name (str) – Palette identifier (cannot be None)

Returns:
New palette data-block

Return type:
Palette

remove(palette, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Deletes a palette from the open blend file.

Parameters:
- palette (Palette) – Target palette to delete (cannot be None)
- do_unlink (bool) – Disconnect all references to this palette before removal (optional)
- do_id_user (bool) – Reduce the user count for all linked data (optional)
- do_ui_user (bool) – Ensure the interface no longer references this palette (optional)

tag(value)

Apply metadata tag.

Parameters:
- value (bool) – Tag status

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Type identifier for the RNA class.
- default (bpy.types.Struct | None) – Fallback value if not located.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Type identifier for the RNA class.
- default (type | None) – Fallback value if not located.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.palettes | |

## BlendDataParticles(bpy_prop_collection)

### BlendDataParticles(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataParticles(bpy_prop_collection)

Manages a collection of particle system configurations within the database.

new(name)

Instantiates and registers a new particle configuration in the main database.

Parameters:
- name (str) – Configuration identifier (cannot be None)

Returns:
New particle settings data-block

Return type:
ParticleSettings

remove(particle, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Purges a particle configuration from the blend file.

Parameters:
- particle (ParticleSettings) – Target configuration to remove (cannot be None)
- do_unlink (bool) – Sever all connections before deletion (optional)
- do_id_user (bool) – Decrement counters across dependent data-blocks (optional)
- do_ui_user (bool) – Clear interface references (optional)

tag(value)

Assign a metadata tag.

Parameters:
- value (bool) – Tag status

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA type identifier.
- default (bpy.types.Struct | None) – Fallback return value.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA type identifier.
- default (type | None) – Fallback return value.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.particles | |

## BlendDataPointClouds(bpy_prop_collection)

### BlendDataPointClouds(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataPointClouds(bpy_prop_collection)

Houses a collection of point cloud data structures.

new(name)

Registers a newly-created point cloud in Blender's database.

Parameters:
- name (str) – Point cloud identifier (cannot be None)

Returns:
New point cloud data-block

Return type:
PointCloud

remove(pointcloud, *, do_unlink=True, do_id_user=True, do_ui_user=True)

Eliminates a point cloud from the current blend file.

Parameters:
- pointcloud (PointCloud) – Point cloud to delete (cannot be None)
- do_unlink (bool) – Break all linkages to this cloud before deletion (WARNING: will also delete objects instancing that point cloud data) (optional)
- do_id_user (bool) – Decrement counters in all dependent data-blocks (optional)
- do_ui_user (bool) – Purge UI references (optional)

tag(value)

Tag with metadata.

Parameters:
- value (bool) – Tag state

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA class identifier.
- default (bpy.types.Struct | None) – Default response.

Returns:
The RNA type or default.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA class identifier.
- default (type | None) – Default response.

Returns:
The class or default.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.pointclouds | |

## BlendDataScenes(bpy_prop_collection)

### BlendDataScenes(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataScenes(bpy_prop_collection)

Maintains a collection of scene instances within the file.

new(name)

Constructs and stores a fresh scene in the main database.

Parameters:
- name (str) – Scene name (cannot be None)

Returns:
New scene data-block

Return type:
Scene

remove(scene, *, do_unlink=True)

Erases a scene from the blend file.

Parameters:
- scene (Scene) – Scene to erase (cannot be None)
- do_unlink (bool) – Detach all references before erasure (optional)

tag(value)

Attach a tag.

Parameters:
- value (bool) – Tag setting

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – RNA class name.
- default (bpy.types.Struct | None) – Substitute if not found.

Returns:
The RNA type or substitute.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – RNA class name.
- default (type | None) – Substitute if not found.

Returns:
The class or substitute.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.scenes | |

## BlendDataScreens(bpy_prop_collection)

### BlendDataScreens(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.BlendDataScreens(bpy_prop_collection)

Manages the collection of workspace screens.

tag(value)

Tag for metadata.

Parameters:
- value (bool) – Tag value

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – Identifier for the RNA type.
- default (bpy.types.Struct | None) – Fallback if not located.

Returns:
The RNA type or fallback.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – Identifier for the RNA type.
- default (type | None) – Fallback if not located.

Returns:
The class or fallback.

Return type:
type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| BlendData.screens | |

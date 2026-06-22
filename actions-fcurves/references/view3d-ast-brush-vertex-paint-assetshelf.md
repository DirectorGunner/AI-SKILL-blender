# View3D Ast Brush Vertex Paint Assetshelf, View3D Ast Brush Weight Paint Assetshelf, View3D Ast Pose Library Assetshelf, View3D Fh Camera Background Image Filehandler ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: `VIEW3D_AST`_brush_vertex_paint(AssetShelf); `VIEW3D_AST`_brush_weight_paint(AssetShelf); `VIEW3D_AST`_pose_library(AssetShelf); `VIEW3D_FH`_camera_background_image(FileHandler); `VIEW3D_FH`_empty_image(FileHandler); `VIEW3D_FH`_vdb_volume(FileHandler); View3DCursor(bpy_struct); ViewerNodeViewerPathElem(ViewerPathElem); ViewerPath(bpy_struct); ViewerPathElem(bpy_struct); VolumeGrid(bpy_struct).

## `VIEW3D_AST`_brush_vertex_paint(AssetShelf)

### `VIEW3D_AST`_brush_vertex_paint(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_vertex_paint ( AssetShelf ) 

classmethod brush_type_poll ( context , asset ) 

static draw_popup_selector ( layout , context , brush , show_name = True ) 

static get_shelf_name_from_context ( context ) 

classmethod has_tool_with_brush_type ( context , brush_type ) 

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

| bpy_struct.id_data AssetShelf.bl_idname AssetShelf.bl_space_type AssetShelf.bl_options AssetShelf.bl_activate_operator AssetShelf.bl_drag_operator AssetShelf.bl_default_preview_size AssetShelf.filter_action AssetShelf.filter_armature AssetShelf.filter_brush AssetShelf.filter_camera AssetShelf.filter_cachefile AssetShelf.filter_curve AssetShelf.filter_annotations AssetShelf.filter_grease_pencil AssetShelf.filter_group AssetShelf.filter_curves AssetShelf.filter_image AssetShelf.filter_light AssetShelf.filter_light_probe AssetShelf.filter_linestyle AssetShelf.filter_lattice AssetShelf.filter_material | AssetShelf.filter_metaball AssetShelf.filter_movie_clip AssetShelf.filter_mesh AssetShelf.filter_mask AssetShelf.filter_node_tree AssetShelf.filter_object AssetShelf.filter_particle_settings AssetShelf.filter_palette AssetShelf.filter_paint_curve AssetShelf.filter_pointcloud AssetShelf.filter_scene AssetShelf.filter_speaker AssetShelf.filter_sound AssetShelf.filter_texture AssetShelf.filter_text AssetShelf.filter_font AssetShelf.filter_volume AssetShelf.filter_world AssetShelf.filter_work_space AssetShelf.asset_library_reference AssetShelf.show_names AssetShelf.preview_size AssetShelf.search_filter |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values AssetShelf.poll AssetShelf.asset_poll AssetShelf.get_active_asset AssetShelf.draw_context_menu AssetShelf.bl_rna_get_subclass AssetShelf.bl_rna_get_subclass_py |

## `VIEW3D_AST`_brush_weight_paint(AssetShelf)

### `VIEW3D_AST`_brush_weight_paint(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_weight_paint ( AssetShelf ) 

classmethod brush_type_poll ( context , asset ) 

static draw_popup_selector ( layout , context , brush , show_name = True ) 

static get_shelf_name_from_context ( context ) 

classmethod has_tool_with_brush_type ( context , brush_type ) 

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

| bpy_struct.id_data AssetShelf.bl_idname AssetShelf.bl_space_type AssetShelf.bl_options AssetShelf.bl_activate_operator AssetShelf.bl_drag_operator AssetShelf.bl_default_preview_size AssetShelf.filter_action AssetShelf.filter_armature AssetShelf.filter_brush AssetShelf.filter_camera AssetShelf.filter_cachefile AssetShelf.filter_curve AssetShelf.filter_annotations AssetShelf.filter_grease_pencil AssetShelf.filter_group AssetShelf.filter_curves AssetShelf.filter_image AssetShelf.filter_light AssetShelf.filter_light_probe AssetShelf.filter_linestyle AssetShelf.filter_lattice AssetShelf.filter_material | AssetShelf.filter_metaball AssetShelf.filter_movie_clip AssetShelf.filter_mesh AssetShelf.filter_mask AssetShelf.filter_node_tree AssetShelf.filter_object AssetShelf.filter_particle_settings AssetShelf.filter_palette AssetShelf.filter_paint_curve AssetShelf.filter_pointcloud AssetShelf.filter_scene AssetShelf.filter_speaker AssetShelf.filter_sound AssetShelf.filter_texture AssetShelf.filter_text AssetShelf.filter_font AssetShelf.filter_volume AssetShelf.filter_world AssetShelf.filter_work_space AssetShelf.asset_library_reference AssetShelf.show_names AssetShelf.preview_size AssetShelf.search_filter |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values AssetShelf.poll AssetShelf.asset_poll AssetShelf.get_active_asset AssetShelf.draw_context_menu AssetShelf.bl_rna_get_subclass AssetShelf.bl_rna_get_subclass_py |

## `VIEW3D_AST`_pose_library(AssetShelf)

### `VIEW3D_AST`_pose_library(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_pose_library ( AssetShelf ) 

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

| bpy_struct.id_data AssetShelf.bl_idname AssetShelf.bl_space_type AssetShelf.bl_options AssetShelf.bl_activate_operator AssetShelf.bl_drag_operator AssetShelf.bl_default_preview_size AssetShelf.filter_action AssetShelf.filter_armature AssetShelf.filter_brush AssetShelf.filter_camera AssetShelf.filter_cachefile AssetShelf.filter_curve AssetShelf.filter_annotations AssetShelf.filter_grease_pencil AssetShelf.filter_group AssetShelf.filter_curves AssetShelf.filter_image AssetShelf.filter_light AssetShelf.filter_light_probe AssetShelf.filter_linestyle AssetShelf.filter_lattice AssetShelf.filter_material | AssetShelf.filter_metaball AssetShelf.filter_movie_clip AssetShelf.filter_mesh AssetShelf.filter_mask AssetShelf.filter_node_tree AssetShelf.filter_object AssetShelf.filter_particle_settings AssetShelf.filter_palette AssetShelf.filter_paint_curve AssetShelf.filter_pointcloud AssetShelf.filter_scene AssetShelf.filter_speaker AssetShelf.filter_sound AssetShelf.filter_texture AssetShelf.filter_text AssetShelf.filter_font AssetShelf.filter_volume AssetShelf.filter_world AssetShelf.filter_work_space AssetShelf.asset_library_reference AssetShelf.show_names AssetShelf.preview_size AssetShelf.search_filter |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys | bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values AssetShelf.poll AssetShelf.asset_poll AssetShelf.get_active_asset AssetShelf.draw_context_menu AssetShelf.bl_rna_get_subclass AssetShelf.bl_rna_get_subclass_py |

## `VIEW3D_FH`_camera_background_image(FileHandler)

### `VIEW3D_FH`_camera_background_image(FileHandler) 

base classes — bpy_struct, FileHandler

class bpy.types. `VIEW3D_FH`_camera_background_image ( FileHandler ) 

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## `VIEW3D_FH`_empty_image(FileHandler)

### `VIEW3D_FH`_empty_image(FileHandler) 

base classes — bpy_struct, FileHandler

class bpy.types. `VIEW3D_FH`_empty_image ( FileHandler ) 

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## `VIEW3D_FH`_vdb_volume(FileHandler)

### `VIEW3D_FH`_vdb_volume(FileHandler) 

base classes — bpy_struct, FileHandler

class bpy.types. `VIEW3D_FH`_vdb_volume ( FileHandler ) 

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## View3DCursor(bpy_struct)

### View3DCursor(bpy_struct) 

base class — bpy_struct

class bpy.types. View3DCursor ( bpy_struct ) 

location 

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

matrix 

A matrix that bundles together the cursor's location and rotation (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

rotation_axis_angle 

Rotation angle for the Axis-Angle rotation form (array of 4 items, in [-inf, inf], default (0.0, 0.0, 1.0, 0.0))

Type :

bpy_prop_array[float]

rotation_euler 

3D rotation (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

rotation_mode 

The rotation kind to use; values belonging to other rotation modes are ignored (default 'XYZ' )

Type :

Literal[Object Rotation Mode Items]

rotation_quaternion 

Rotation expressed as quaternions (keep normalized) (array of 4 items, in [-inf, inf], default (1.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

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

| Scene.cursor | |

## ViewerNodeViewerPathElem(ViewerPathElem)

### ViewerNodeViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. ViewerNodeViewerPathElem ( ViewerPathElem )

node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |

## ViewerPath(bpy_struct)

### ViewerPath(bpy_struct)

base class — bpy_struct

class bpy.types. ViewerPath ( bpy_struct )

Route pointing at the data being viewed.

path

(default None, readonly)

Type :

bpy_prop_collection[ViewerPathElem]

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

| SpaceSpreadsheet.viewer_path | SpreadsheetTableIDGeometry.viewer_path |

## ViewerPathElem(bpy_struct)

### ViewerPathElem(bpy_struct)

base class — bpy_struct

subclasses —
EvaluateClosureNodeViewerPathElem, ForeachGeometryElementZoneViewerPathElem, GroupNodeViewerPathElem, IDViewerPathElem, ModifierViewerPathElem, RepeatZoneViewerPathElem, SimulationZoneViewerPathElem, ViewerNodeViewerPathElem

class bpy.types. ViewerPathElem ( bpy_struct )

A single segment within a viewer path.

type

Which kind of path element this is (default 'ID' , readonly)

Type :

Literal['ID', 'MODIFIER', '`GROUP_NODE`', '`SIMULATION_ZONE`', '`VIEWER_NODE`', '`REPEAT_ZONE`', '`FOREACH_GEOMETRY_ELEMENT_ZONE`', '`EVALUATE_CLOSURE`']

ui_name

Label shown for this element in the interface (default "", readonly, never None)

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

| ViewerPath.path | |

## VolumeGrid(bpy_struct)

### VolumeGrid(bpy_struct)

base class — bpy_struct

class bpy.types. VolumeGrid ( bpy_struct )

A single 3D volume grid.

channels

How many dimensions the grid's data type has (in [0, inf], default 0, readonly)

Type :

int

data_type

The data type stored for each voxel (default 'UNKNOWN' , readonly)

Type :

Literal[Volume Grid Data Type Items]

is_loaded

Whether the grid tree currently sits in memory (default False, readonly)

Type :

bool

matrix_object

Transform that maps voxel index coordinates into object space (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

name

Volume grid name (default "", readonly, never None)

Type :

str

load ( )

Read the grid tree in from file

Returns :

True if grid tree was successfully loaded

Return type :

bool

unload ( )

Drop the grid tree and voxel data from memory, retaining only its metadata

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

| Volume.grids | |

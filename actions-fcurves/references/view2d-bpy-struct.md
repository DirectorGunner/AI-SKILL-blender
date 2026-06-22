# View2D Bpy Struct, View3D Ast Brush Gpencil Paint Assetshelf, View3D Ast Brush Gpencil Sculpt Assetshelf, View3D Ast Brush Gpencil Vertex Assetshelf ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: View2D(bpy_struct); `VIEW3D_AST`_brush_gpencil_paint(AssetShelf); `VIEW3D_AST`_brush_gpencil_sculpt(AssetShelf); `VIEW3D_AST`_brush_gpencil_vertex(AssetShelf); `VIEW3D_AST`_brush_gpencil_weight(AssetShelf); `VIEW3D_AST`_brush_sculpt(AssetShelf); `VIEW3D_AST`_brush_sculpt_curves(AssetShelf); `VIEW3D_AST`_brush_texture_paint(AssetShelf).

## View2D(bpy_struct)

### View2D(bpy_struct) 

base class — bpy_struct

class bpy.types. View2D ( bpy_struct ) 

Panning and zooming over a 2D region

region_to_view ( x , y ) 

Convert region coordinates into 2D view space

Parameters :

- x ( float ) – x, Region x coordinate (in [-inf, inf])

- y ( float ) – y, Region y coordinate (in [-inf, inf])

Returns :

Result, View coordinates (array of 2 items, in [-inf, inf])

Return type :

bpy_prop_array[float]

view_to_region ( x , y , * , clip = True ) 

Convert 2D view coordinates into region space

Parameters :

- x ( float ) – x, 2D View x coordinate (in [-inf, inf])

- y ( float ) – y, 2D View y coordinate (in [-inf, inf])

- clip ( bool ) – Clip, Clip coordinates to the visible region (optional)

Returns :

Result, Region coordinates (array of 2 items, in [-inf, inf])

Return type :

bpy_prop_array[int]

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

| Region.view2d | |

## `VIEW3D_AST`_brush_gpencil_paint(AssetShelf)

### `VIEW3D_AST`_brush_gpencil_paint(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_gpencil_paint ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_gpencil_sculpt(AssetShelf)

### `VIEW3D_AST`_brush_gpencil_sculpt(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_gpencil_sculpt ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_gpencil_vertex(AssetShelf)

### `VIEW3D_AST`_brush_gpencil_vertex(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_gpencil_vertex ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_gpencil_weight(AssetShelf)

### `VIEW3D_AST`_brush_gpencil_weight(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_gpencil_weight ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_sculpt(AssetShelf)

### `VIEW3D_AST`_brush_sculpt(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_sculpt ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_sculpt_curves(AssetShelf)

### `VIEW3D_AST`_brush_sculpt_curves(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_sculpt_curves ( AssetShelf ) 

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

## `VIEW3D_AST`_brush_texture_paint(AssetShelf)

### `VIEW3D_AST`_brush_texture_paint(AssetShelf) 

base classes — bpy_struct, AssetShelf

class bpy.types. `VIEW3D_AST`_brush_texture_paint ( AssetShelf ) 

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

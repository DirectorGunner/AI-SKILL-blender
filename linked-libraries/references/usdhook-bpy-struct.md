# Usdhook Bpy Struct, Userassetlibrary Bpy Struct, Userpref Ul Asset Libraries Uilist, Userpref Ul Extension Repos Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: USDHook(bpy_struct); UserAssetLibrary(bpy_struct); `USERPREF_UL`_asset_libraries(UIList); `USERPREF_UL`_extension_repos(UIList); `VIEWLAYER_UL`_aov(UIList); `VIEWLAYER_UL`_linesets(UIList).

## USDHook(bpy_struct)

### USDHook(bpy_struct)

### USD Hook Example

The example here demonstrates a USDHook implementation that adds to Blender’s USD export and import behaviour.

### Callback Function API

Inside a USDHook subclass you can define as many or as few of the callback functions below as you need.

#### on_export

Runs just ahead of the USD export wrapping up, giving you a chance to tweak the USD stage right before it gets written out.

Args:

- export_context (USDSceneExportContext): Provides access to the stage and dependency graph

Returns:

- True on success or False if the operation was bypassed or otherwise failed to complete

#### on_material_export

Runs once per exported material, giving you a chance to alter the USD material — for example to build shaders.

Args:

- export_context (USDMaterialExportContext): Provides access to the stage and a texture export utility function

- bl_material ( bpy.types.Material ): The source Blender material

- usd_material ( pxr.UsdShade.Material ): The target USD material to be exported

Returns:

- True on success or False if the operation was bypassed or otherwise failed to complete

Keep in mind that the destination USD material may already carry shaders wired up by the USD exporter itself or by other material-export hooks.

#### on_import

Runs once the USD import has wrapped up.

Args:

- import_context (USDSceneImportContext):
Provides access to the stage and a map associating USD prim paths and Blender IDs

Returns:

- True on success or False if the operation was bypassed or otherwise failed to complete

#### material_import_poll

Runs to decide whether this USDHook implementation is able to convert a particular USD material.

Args:

- import_context (USDMaterialImportContext): Provides access to the stage and a texture import utility function

- usd_material ( pxr.UsdShade.Material ): The source USD material to be exported

Returns:

- True if the hook can convert the material or False otherwise

Should any hook answer True to material_import_poll , the USD importer bypasses its built-in USD Preview Surface and MaterialX handling and instead calls that hook’s on_material_import method to do the conversion.

#### on_material_import

Runs once per imported material so you can turn the USD material into nodes on the Blender material. For this to be invoked, the hook also has to supply a material_import_poll() callback that answers True for the material in question.

Args:

- import_context (USDMaterialImportContext): Provides access to the stage and a texture import utility function

- bl_material ( bpy.types.Material ): The target Blender material with an empty node tree

- usd_material ( pxr.UsdShade.Material ): The source USD material to be imported

Returns:

- True on success or False if the conversion failed or otherwise did not complete

### Context Classes

The callbacks receive instances of the built-in classes listed below as their arguments.

#### USDSceneExportContext

Argument for on_export.

Methods:

- get_stage() : returns the USD stage to be saved

- get_depsgraph() : returns the Blender scene dependency graph

- get_prim_map() returns a dict where the key is an exported USD Prim path and the value a list
of the IDs associated with that prim.

#### USDMaterialExportContext

Argument for on_material_export.

Methods:

- get_stage() : returns the USD stage to be saved

- export_texture(image: bpy.types.Image) : Returns the USD asset path for the given texture image

Depending on the active USD export options, export_texture writes out in-memory images and may also duplicate texture assets. By default, for instance, a call to export_texture(/foo/bar.png) copies the file into a textures directory beside the exported USD and hands back the relative path ./textures/bar.png .

#### USDSceneImportContext

Argument for on_import.

Methods:

- get_prim_map() returns a dict where the key is an imported USD Prim path and the value a list
of the IDs created by the imported prim.

- get_stage() returns the USD stage which was imported.

#### USDMaterialImportContext

Argument for material_import_poll and on_material_import.

Methods:

- get_stage() :
returns the USD stage to be saved.

- import_texture(asset_path: str) :
for the given USD texture asset path, returns a tuple[str, bool] ,
containing the asset’s local path and a bool indicating whether the path references a temporary file.

Depending on the current USD Import Textures options, import_texture may pull the texture onto the local file system when the supplied asset path is a package-relative path inside a USDZ archive. With the Import Textures mode set to Packed , the texture lands in a temporary spot and the returned tuple’s second element is True to flag the file as temporary, which may mean you need to pack the image. If the asset path already points at a local file, or if no local copy could be made, the original path comes back unchanged.

### Errors

Any exception thrown by these functions is reported inside Blender, with the exception details echoed to the console.

### Example Code

In the example that follows, the USDHookExample class wires up these functions:

- on_export() function to add custom data to the stage’s root layer.

- on_material_export() function to create a simple MaterialX shader on the given USD material.

- on_import() function to create a text object to display the stage’s custom layer data.

- material_import_poll() returns True if the given USD material has an mtlx context.

- on_material_import() function to convert a simple MaterialX shader with a base_color input.

`text
bl_info = {
"name": "USD Hook Example",
"blender": (4, 4, 0),
}

import bpy
import bpy.types
import textwrap

### Make `pxr` module available, for running as `bpy` PIP package.
bpy.utils.expose_bundled_modules()

import pxr.Gf as Gf
import pxr.Sdf as Sdf
import pxr.Usd as Usd
import pxr.UsdShade as UsdShade

class USDHookExample(bpy.types.USDHook):
"""Example implementation of USD IO hooks"""
bl_idname = "usd_hook_example"
bl_label = "Example"

@staticmethod
def on_export(export_context):
""" Include the Blender filepath in the root layer custom data.
"""

stage = export_context.get_stage()

if stage is None:
return False
data = bpy.data
if data is None:
return False

### Set the custom data.
rootLayer = stage.GetRootLayer()
customData = rootLayer.customLayerData
customData["blenderFilepath"] = data.filepath
rootLayer.customLayerData = customData

return True

@staticmethod
def on_material_export(export_context, bl_material, usd_material):
""" Create a simple MaterialX shader on the exported material.
"""

stage = export_context.get_stage()

### Create a MaterialX standard surface shader
mtl_path = usd_material.GetPrim().GetPath()
shader = UsdShade.Shader.Define(stage, mtl_path.AppendPath("mtlxstandard_surface"))
shader.CreateIdAttr("ND_standard_surface_surfaceshader")

### Connect the shader. MaterialX materials use "mtlx" renderContext
usd_material.CreateSurfaceOutput("mtlx").ConnectToSource(shader.ConnectableAPI(), "out")

### Set the color to the Blender material's viewport display color.
col = bl_material.diffuse_color
shader.CreateInput("base_color", Sdf.ValueTypeNames.Color3f).Set(Gf.Vec3f(col[0], col[1], col[2]))

return True

@staticmethod
def on_import(import_context):
"""Inspect the imported stage & objects to set some custom data
"""

###########################################################
### Store some USD metadata on each imported data-block.
###########################################################
prim_map = import_context.get_prim_map()

### Store prim path as a string on each data-block created.
for prim_path, data_blocks in prim_map.items():

### Type hints for prim map.
prim_path: Sdf.Path
data_blocks: list[bpy.types.ID]

### Loop over mapped data-blocks to store some metadata.
for data_block in data_blocks:
data_block["prim_path"] = str(prim_path)

###########################################################
### Create a text object to display the stage's custom data.
###########################################################
stage = import_context.get_stage()

if stage is None:
return False

### Get the custom data.
rootLayer = stage.GetRootLayer()
customData = rootLayer.customLayerData

### Create a text object to display the stage path
### and custom data dictionary entries.

bpy.ops.object.text_add()
ob = bpy.context.view_layer.objects.active

if (ob is None) or (ob.data is None):
return False

ob.name = "layer_data"
ob.data.name = "layer_data"

### The stage root path is the first line.
text = rootLayer.realPath

### Append key/value strings, enforcing text wrapping.
for item in customData.items():
print(item)
text += '\n'
line = str(item[0]) + ': ' + str(item[1])
text += textwrap.fill(line, width=80)

ob.data.body = text

return True

@staticmethod
def material_import_poll(import_context, usd_material):
"""
Return True if the given USD material can be converted.
Return False otherwise.
"""
### We can convert MaterialX.
surf_output = usd_material.GetSurfaceOutput("mtlx")
return bool(surf_output)

@staticmethod
def on_material_import(import_context, bl_material, usd_material):
"""
Import a simple mtlx material. Just handle the base_color input
of a ND_standard_surface_surfaceshader.
"""

### We must confirm that we can handle this material.
surf_output = usd_material.GetSurfaceOutput("mtlx")
if not surf_output:
return False

if not surf_output.HasConnectedSource():
return False

### Get the connected surface output source.
source = surf_output.GetConnectedSource()
### Get the shader prim from the source
shader = UsdShade.Shader(source[0])
shader_id = shader.GetShaderId()
if shader_id != "ND_standard_surface_surfaceshader":
return False

color_attr = shader.GetInput("base_color")
if color_attr is None:
return False

### Create the node tree
nodes = bl_material.node_tree.nodes
output = nodes.new(type="ShaderNodeOutputMaterial")
bsdf = nodes.new(type="ShaderNodeBsdfPrincipled")
bsdf.location[0] -= 1.5 * bsdf.width
bl_material.node_tree.links.new(output.inputs["Surface"], bsdf.outputs["BSDF"])
bsdf_base_color_input = bsdf.inputs['Base Color']

### Try to set the default color value.
### Get the authored default value
color = color_attr.Get()

if color is None:
return False

bsdf_base_color_input.default_value = (color[0], color[1], color[2], 1)

return True

def register():
bpy.utils.register_class(USDHookExample)

def unregister():
bpy.utils.unregister_class(USDHookExample)

if __name__ == "__main__":
register()
`

base class — bpy_struct

class bpy.types. USDHook ( bpy_struct ) 

Callback functions that you register here let you hook into and extend USD import/export.

bl_description 

A brief note describing what the USD hook does (default "", never None)

Type :

str

bl_idname 

(default "", never None)

Type :

str

bl_label 

(default "", never None)

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

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

## UserAssetLibrary(bpy_struct)

### UserAssetLibrary(bpy_struct) 

base class — bpy_struct

class bpy.types. UserAssetLibrary ( bpy_struct ) 

Configuration for a shared library that Asset Browsers can draw from

enabled 

Turn the asset library on (default True)

Type :

bool

import_method 

Choose the way assets get brought in, unless the Asset Browser overrides it (default 'PACK' )

- LINK
Link – Import the assets as linked data-block.

- APPEND
Append – Import the assets as copied data-block, with no link to the original asset data-block.

- `APPEND_REUSE`
Append (Reuse Data) – Import the assets as copied data-block while avoiding multiple copies of nested, typically heavy data. For example the textures of a material asset, or the mesh of an object asset, don't have to be copied every time this asset is imported. The instances of the asset share the data instead..

- PACK
Pack – Import the asset as linked data-block, and pack it in the current file (ensures that it remains unchanged in case the library data is modified, is not available anymore, etc.).

Type :

Literal['LINK', 'APPEND', '`APPEND_REUSE`', 'PACK']

name 

A label for the asset library, which need not be unique (default "", never None)

Type :

str

path 

Location of a folder holding .blend files that serve as the asset library (default "", never None)

Type :

str

use_relative_path 

Store a relative path when assets from this library are linked (default True)

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

| AssetLibraryCollection.new AssetLibraryCollection.remove | PreferencesFilePaths.asset_libraries |

## `USERPREF_UL`_asset_libraries(UIList)

### `USERPREF_UL`_asset_libraries(UIList) 

base classes — bpy_struct, UIList

class bpy.types. `USERPREF_UL`_asset_libraries ( UIList ) 

draw_item ( _context , layout , _data , item , _icon , _active_data , _active_propname , _index ) 

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `USERPREF_UL`_extension_repos(UIList)

### `USERPREF_UL`_extension_repos(UIList) 

base classes — bpy_struct, UIList

class bpy.types. `USERPREF_UL`_extension_repos ( UIList ) 

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index ) 

filter_items ( _context , data , propname ) 

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `VIEWLAYER_UL`_aov(UIList)

### `VIEWLAYER_UL`_aov(UIList)

base classes — bpy_struct, UIList

class bpy.types. `VIEWLAYER_UL`_aov ( UIList )

static aov_icon ( item )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `VIEWLAYER_UL`_linesets(UIList)

### `VIEWLAYER_UL`_linesets(UIList)

base classes — bpy_struct, UIList

class bpy.types. `VIEWLAYER_UL`_linesets ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

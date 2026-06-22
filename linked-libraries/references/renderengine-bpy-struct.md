# Renderengine Bpy Struct, Scene Ul Gltf2 Filter Action Uilist, Scene Ul Keying Set Paths Uilist, Spacenodeeditorpath Bpy Prop Collection

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RenderEngine(bpy_struct); `SCENE_UL`_gltf2_filter_action(UIList); `SCENE_UL`_keying_set_paths(UIList); SpaceNodeEditorPath(bpy_prop_collection).

## RenderEngine(bpy_struct)

### RenderEngine(bpy_struct) 

### Simple Render Engine 

`\text
import bpy
import array

class CustomRenderEngine(bpy.types.RenderEngine):
### These three members are used by Blender to set up the
### RenderEngine; define its internal name, visible name and capabilities.
bl_idname = "CUSTOM"
bl_label = "Custom"
bl_use_preview = True

### Init is called whenever a new render engine instance is created. Multiple
### instances may exist at the same time, for example for a viewport and final
### render.
### Note the generic arguments signature, and the call to the parent class
### `__init__` methods, which are required for Blender to create the underlying
### `RenderEngine` data.
def __init__(self, *args, **kwargs):
super().__init__(*args, **kwargs)
self.scene_data = None
self.draw_data = None

### When the render engine instance is destroy, this is called. Clean up any
### render engine data here, for example stopping running render threads.
def __del__(self):
### Own delete code...
super().__del__()

### This is the method called by Blender for both final renders (F12) and
### small preview for materials, world and lights.
def render(self, depsgraph):
scene = depsgraph.scene
scale = scene.render.resolution_percentage / 100.0
self.size_x = int(scene.render.resolution_x * scale)
self.size_y = int(scene.render.resolution_y * scale)

### Fill the render result with a flat color. The frame-buffer is
### defined as a list of pixels, each pixel itself being a list of
### R,G,B,A values.
if self.is_preview:
color = [0.1, 0.2, 0.1, 1.0]
else:
color = [0.2, 0.1, 0.1, 1.0]

pixel_count = self.size_x * self.size_y
rect = [color] * pixel_count

### Here we write the pixel values to the RenderResult
result = self.begin_result(0, 0, self.size_x, self.size_y)
layer = result.layers[0].passes["Combined"]
layer.rect = rect
self.end_result(result)

### For viewport renders, this method gets called once at the start and
### whenever the scene or 3D viewport changes. This method is where data
### should be read from Blender in the same thread. Typically a render
### thread will be started to do the work while keeping Blender responsive.
def view_update(self, context, depsgraph):
region = context.region
view3d = context.space_data
scene = depsgraph.scene

### Get viewport dimensions
dimensions = region.width, region.height

if not self.scene_data:
### First time initialization
self.scene_data = []
first_time = True

### Loop over all datablocks used in the scene.
for datablock in depsgraph.ids:
pass
else:
first_time = False

### Test which datablocks changed
for update in depsgraph.updates:
print("Datablock updated: ", update.id.name)

### Test if any material was added, removed or changed.
if depsgraph.id_type_updated('MATERIAL'):
print("Materials updated")

### Loop over all object instances in the scene.
if first_time or depsgraph.id_type_updated('OBJECT'):
for instance in depsgraph.object_instances:
pass

### For viewport renders, this method is called whenever Blender redraws
### the 3D viewport. The renderer is expected to quickly draw the render
### with OpenGL, and not perform other expensive work.
### Blender will draw overlays for selection and editing on top of the
### rendered image automatically.
def view_draw(self, context, depsgraph):
### Lazily import GPU module, so that the render engine works in
### background mode where the GPU module can't be imported by default.
import gpu

region = context.region
scene = depsgraph.scene

### Get viewport dimensions
dimensions = region.width, region.height

### Bind shader that converts from scene linear to display space,
gpu.state.blend_set('`ALPHA_PREMULT`')
self.bind_display_space_shader(scene)

if not self.draw_data or self.draw_data.dimensions != dimensions:
self.draw_data = CustomDrawData(dimensions)

self.draw_data.draw()

self.unbind_display_space_shader()
gpu.state.blend_set('NONE')

class CustomDrawData:
def __init__(self, dimensions):
import gpu

### Generate dummy float image buffer.
self.dimensions = dimensions
width, height = dimensions

pixels = width * height * array.array('f', [0.1, 0.2, 0.1, 1.0])
pixels = gpu.types.Buffer('FLOAT', width * height * 4, pixels)

### Generate texture.
self.texture = gpu.types.GPUTexture((width, height), format='RGBA16F', data=pixels)

### Note: This is just a didactic example.
### In this case it would be more convenient to fill the texture with:
### self.texture.clear('FLOAT', value=[0.1, 0.2, 0.1, 1.0])

def __del__(self):
del self.texture

def draw(self):
from gpu_extras.presets import draw_texture_2d
draw_texture_2d(self.texture, (0, 0), self.texture.width, self.texture.height)

### RenderEngines also need to tell UI Panels that they are compatible with.
### We recommend to enable all panels marked as `BLENDER_RENDER`, and then
### exclude any panels that are replaced by custom panels registered by the
### render engine, or that are not supported.
def get_panels():
exclude_panels = {
'`VIEWLAYER_PT`_filter',
'`VIEWLAYER_PT`_layer_passes',
}

panels = []
for panel in bpy.types.Panel.__subclasses__():
if hasattr(panel, '`COMPAT_ENGINES`') and '`BLENDER_RENDER`' in panel.`COMPAT_ENGINES`:
if panel.__name__ not in exclude_panels:
panels.append(panel)

return panels

def register():
### Register the RenderEngine.
bpy.utils.register_class(CustomRenderEngine)

for panel in get_panels():
panel.`COMPAT_ENGINES`.add('CUSTOM')

def unregister():
bpy.utils.unregister_class(CustomRenderEngine)

for panel in get_panels():
if 'CUSTOM' in panel.`COMPAT_ENGINES`:
panel.`COMPAT_ENGINES`.remove('CUSTOM')

if __name__ == "__main__":
register()
`

### GPU Render Engine 

`\text
import bpy

class CustomGPURenderEngine(bpy.types.RenderEngine):
bl_idname = "`CUSTOM_GPU`"
bl_label = "Custom GPU"

### Request a GPU context to be created and activated for the render method.
### This may be used either to perform the rendering itself, or to allocate
### and fill a texture for more efficient drawing.
bl_use_gpu_context = True

def render(self, depsgraph):
### Lazily import GPU module, since GPU context is only created on demand
### for rendering and does not exist on register.
import gpu

### Perform rendering task.
pass

def register():
bpy.utils.register_class(CustomGPURenderEngine)

def unregister():
bpy.utils.unregister_class(CustomGPURenderEngine)

if __name__ == "__main__":
register()
`

base class — bpy_struct

subclasses —
HydraRenderEngine

class bpy.types. RenderEngine ( bpy_struct ) 

Render engine

bl_idname 

(default “”, never None)

Type :

str

bl_label 

(default “”, never None)

Type :

str

bl_use_custom_freestyle 

Takes care of freestyle rendering itself rather than passing it on to EEVEE (default False)

Type :

bool

bl_use_eevee_viewport 

Relies on EEVEE for viewport shading while in Material Preview mode (default False)

Type :

bool

bl_use_gpu_context 

Turn on an OpenGL context for the render method, intended for engines that render with OpenGL (default False)

Type :

bool

bl_use_image_save 

Write images/movies to disk during an animation render. Turning saving off is only allowed when bl_use_postprocess is likewise off. (default True)

Type :

bool

bl_use_materialx 

Rely on MaterialX when exporting materials to Hydra (default False)

Type :

bool

bl_use_postprocess 

Run compositing over the render results (default False)

Type :

bool

bl_use_preview 

The render engine can be used to render material, light, and world previews (default False)

Type :

bool

bl_use_shading_nodes_custom 

Keep Cycles and EEVEE shading nodes out of the node editor interface so that separate nodes can take their place (default True)

Type :

bool

bl_use_spherical_stereo 

Handle spherical stereo camera models (default False)

Type :

bool

bl_use_stereo_viewport 

Handle stereo 3D viewport rendering (default False)

Type :

bool

camera_override 

(readonly)

Type :

Object

is_animation 

(default False)

Type :

bool

is_preview 

(default False)

Type :

bool

layer_override 

(array of 20 items, default (False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False, False))

Type :

bpy_prop_array[bool]

render

(readonly)

Type :

RenderSettings

resolution_x 

(in [-inf, inf], default 0, readonly)

Type :

int

resolution_y 

(in [-inf, inf], default 0, readonly)

Type :

int

temporary_directory 

(default “”, readonly, never None)

Type :

str

use_highlight_tiles 

(default False)

Type :

bool

update ( * , data = None , depsgraph = None ) 

Export scene data for render

Parameters :

- data (BlendData) – (optional)

- depsgraph (Depsgraph) – (optional)

render ( depsgraph ) 

Render scene into an image

render_frame_finish ( ) 

Perform finishing operations after all view layers in a frame were rendered

draw ( context , depsgraph ) 

Draw render image

bake ( depsgraph , object , pass_type , pass_filter , width , height ) 

Bake passes

Parameters :

- pass_type (Literal[Bake Pass Type Items]) – Pass, Pass to bake

- pass_filter ( int ) – Pass Filter, Filter to combined, diffuse, glossy and transmission passes (in [0, inf])

- width ( int ) – Width, Image width (in [0, inf])

- height ( int ) – Height, Image height (in [0, inf])

view_update ( context , depsgraph ) 

Update on data changes for viewport render

view_draw ( context , depsgraph ) 

Draw viewport render

update_script_node ( * , node = None ) 

Compile shader script node

Parameters :

node (Node) – (optional)

update_render_passes ( * , scene = None , renderlayer = None ) 

Update the render passes that will be generated

Parameters :

- scene (Scene) – (optional)

- renderlayer (ViewLayer) – (optional)

update_custom_camera ( * , cam = None ) 

Compile custom camera

Parameters :

cam (Camera) – (optional)

tag_redraw ( ) 

Request redraw for viewport rendering

tag_update ( ) 

Request update call for viewport rendering

begin_result ( x , y , w , h , * , layer = '' , view = '' ) 

Create render result to write linear floating-point render layers and passes

Parameters :

- x ( int ) – X, (in [0, inf])

- y ( int ) – Y, (in [0, inf])

- w ( int ) – Width, (in [0, inf])

- h ( int ) – Height, (in [0, inf])

- layer ( str ) – Layer, Single layer to get render result for (optional, never None)

- view ( str ) – View, Single view to get render result for (optional, never None)

Returns :

Result

Return type :

RenderResult

update_result ( result ) 

Signal that pixels have been updated and can be redrawn in the user interface

Parameters :

result (RenderResult) – Result

end_result ( result , * , cancel = False , highlight = False , do_merge_results = False ) 

All pixels in the render result have been set and are final

Parameters :

- result (RenderResult) – Result

- cancel ( bool ) – Cancel, Don’t mark tile as done, don’t merge results unless forced (optional)

- highlight ( bool ) – Highlight, Don’t mark tile as done yet (optional)

- do_merge_results ( bool ) – Merge Results, Merge results even if cancel=true (optional)

add_pass ( name , channels , chan_id , * , layer = '' ) 

Add a pass to the render layer

Parameters :

- name ( str ) – Name, Name of the Pass, without view or channel tag (never None)

- channels ( int ) – Channels, (in [0, inf])

- chan_id ( str ) – Channel IDs, Channel names, one character per channel (never None)

- layer ( str ) – Layer, Single layer to add render pass to (optional, never None)

get_result ( ) 

Get final result for non-pixel operations

Returns :

Result

Return type :

RenderResult

test_break ( ) 

Test if the render operation should been canceled, this is a fast call that should be used regularly for responsiveness

Returns :

Break

Return type :

bool

pass_by_index_get ( layer , index ) 

pass_by_index_get

Parameters :

- layer ( str ) – Layer, Name of render layer to get pass for (never None)

- index ( int ) – Index, Index of pass to get (in [0, inf])

Returns :

Index, Index of pass to get

Return type :

RenderPass

active_view_get ( ) 

active_view_get

Returns :

View, Single view active (never None)

Return type :

str

active_view_set ( view ) 

active_view_set

Parameters :

view ( str ) – View, Single view to set as active (never None)

camera_shift_x ( camera , * , use_spherical_stereo = False ) 

camera_shift_x

Parameters :

use_spherical_stereo ( bool ) – Spherical Stereo, (optional)

Returns :

Shift X, (in [0, inf])

Return type :

float

camera_model_matrix ( camera , * , use_spherical_stereo = False ) 

camera_model_matrix

Parameters :

use_spherical_stereo ( bool ) – Spherical Stereo, (optional)

Returns :

Model Matrix, Normalized camera model matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type :

mathutils.Matrix

use_spherical_stereo ( camera ) 

use_spherical_stereo

Returns :

Spherical Stereo

Return type :

bool

update_stats ( stats , info ) 

Update and signal to redraw render status text

Parameters :

- stats ( str ) – Stats, (never None)

- info ( str ) – Info, (never None)

frame_set ( frame , subframe ) 

Evaluate scene at a different frame (for motion blur)

Parameters :

- frame ( int ) – Frame, (in [-inf, inf])

- subframe ( float ) – Subframe, (in [0, 1])

update_progress ( progress ) 

Update progress percentage of render

Parameters :

progress ( float ) – Percentage of render that’s done (in [0, 1])

update_memory_stats ( * , memory_used = 0.0 , memory_peak = 0.0 ) 

Update memory usage statistics

Parameters :

- memory_used ( float ) – Current memory usage in megabytes (in [0, inf], optional)

- memory_peak ( float ) – Peak memory usage in megabytes (in [0, inf], optional)

report ( type , message ) 

Report info, warning or error messages

Parameters :

- type (set[Literal[Wm Report Items]]) – Type

- message ( str ) – Report Message, (never None)

error_set ( message ) 

Set error message displaying after the render is finished

Parameters :

message ( str ) – Report Message, (never None)

bind_display_space_shader ( scene ) 

Bind GLSL fragment shader that converts linear colors to display space colors using scene color management settings

unbind_display_space_shader ( ) 

Unbind GLSL display space shader, must always be called after binding the shader

support_display_space_shader ( scene ) 

Test if GLSL display space shader is supported for the combination of graphics card and scene settings

Returns :

Supported

Return type :

bool

get_preview_pixel_size ( scene ) 

Get the pixel size that should be used for preview rendering

Returns :

Pixel Size, (in [1, 8])

Return type :

int

free_blender_memory ( ) 

Free Blender side memory of render engine

tile_highlight_set ( x , y , width , height , highlight ) 

Set highlighted state of the given tile

Parameters :

- x ( int ) – X, (in [0, inf])

- y ( int ) – Y, (in [0, inf])

- width ( int ) – Width, (in [0, inf])

- height ( int ) – Height, (in [0, inf])

- highlight ( bool ) – Highlight

tile_highlight_clear_all ( ) 

The temp directory used by Blender

register_pass ( scene , view_layer , name , channels , chanid , type ) 

Register a render pass that will be part of the render with the current settings

Parameters :

- name ( str ) – Name, (never None)

- channels ( int ) – Channels, (in [1, 8])

- chanid ( str ) – Channel IDs, (never None)

- type ( Literal [ 'VALUE' , 'VECTOR' , 'COLOR' ] ) – Type

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

## `SCENE_UL`_gltf2_filter_action(UIList)

### `SCENE_UL`_gltf2_filter_action(UIList)

base classes — bpy_struct, UIList

class bpy.types. `SCENE_UL`_gltf2_filter_action ( UIList )

draw_item ( context , layout , data , item , icon , active_data , active_propname , index )

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

## `SCENE_UL`_keying_set_paths(UIList)

### `SCENE_UL`_keying_set_paths(UIList)

base classes — bpy_struct, UIList

class bpy.types. `SCENE_UL`_keying_set_paths ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index )

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

## SpaceNodeEditorPath(bpy_prop_collection)

### SpaceNodeEditorPath(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. SpaceNodeEditorPath ( bpy_prop_collection )

Retrieve the node tree path as a string

to_string

(default “”, readonly, never None)

Type :

str

clear ( )

Empty the node tree path

start ( node_tree )

Define the root node tree

Parameters :

node_tree (NodeTree) – Node Tree

append ( node_tree , * , node = None )

Add a node group tree onto the path

Parameters :

- node_tree (NodeTree) – Node Tree, the node tree to tack onto the end of the node editor path

- node (Node) – Node, Group node linking to this node tree (optional)

pop ( )

Drop the last node tree off the path

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceNodeEditor.path | |

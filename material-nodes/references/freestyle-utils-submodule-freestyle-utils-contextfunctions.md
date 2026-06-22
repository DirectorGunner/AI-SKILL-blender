# Freestyle Utils Submodule Freestyle Utils Contextfunctions, Freestyle Utilities Freestyle Utils, Gpu Capabilities Utilities Gpu Capabilities, Gpu Shader Utilities Gpu Shader ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: freestyle.utils submodule (freestyle.utils.ContextFunctions); Freestyle Utilities (freestyle.utils); GPU Capabilities Utilities (gpu.capabilities); GPU Shader Utilities (gpu.shader); GPU Texture Utilities (gpu.texture).

## freestyle.utils submodule (freestyle.utils.ContextFunctions)

### freestyle.utils submodule (freestyle.utils.ContextFunctions) 

The ContextFunctions submodule that lives inside Blender's Freestyle module

freestyle.utils.ContextFunctions. get_border ( ) 

Hands back the border.

Returns :

A tuple of 4 numbers (xmin, ymin, xmax, ymax).

Return type :

tuple[int, int, int, int]

freestyle.utils.ContextFunctions. get_canvas_height ( ) 

Hands back the canvas height.

Returns :

The canvas height.

Return type :

int

freestyle.utils.ContextFunctions. get_canvas_width ( ) 

Hands back the canvas width.

Returns :

The canvas width.

Return type :

int

freestyle.utils.ContextFunctions. get_selected_fedge ( ) 

Hands back the FEdge currently selected.

Returns :

The selected FEdge.

Return type :

FEdge

freestyle.utils.ContextFunctions. get_time_stamp ( ) 

Hands back the system time stamp.

Returns :

The system time stamp.

Return type :

int

freestyle.utils.ContextFunctions. load_map ( file_name , map_name , num_levels = 4 , sigma = 1.0 ) 

Brings an image map in so it can be read later.

Parameters :

- file_name ( str ) – The name of the image file.

- map_name ( str ) – The name that will be used to access this image.

- num_levels ( int ) – How many levels the map pyramid holds
(default = 4). Passing 0 makes the full pyramid get built.

- sigma ( float ) – The sigma value of the gaussian function.

freestyle.utils.ContextFunctions. read_complete_view_map_pixel ( level , x , y ) 

Reads back one pixel out of the complete view map.

Parameters :

- level ( int ) – Which pyramid level the pixel should be read from.

- x ( int ) – Horizontal coordinate of the target pixel, measured from an
origin at the lower-left corner.

- y ( int ) – Vertical coordinate of the target pixel, measured from an
origin at the lower-left corner.

Returns :

The floating-point value stored for that pixel.

Return type :

float

freestyle.utils.ContextFunctions. read_directional_view_map_pixel ( orientation , level , x , y ) 

Reads back one pixel out of one of the oriented view map images.

Parameters :

- orientation ( int ) – A number selecting which orientation to inspect.

- level ( int ) – Which pyramid level the pixel should be read from.

- x ( int ) – Horizontal coordinate of the target pixel, measured from an
origin at the lower-left corner.

- y ( int ) – Vertical coordinate of the target pixel, measured from an
origin at the lower-left corner.

Returns :

The floating-point value stored for that pixel.

Return type :

float

freestyle.utils.ContextFunctions. read_map_pixel ( map_name , level , x , y ) 

Reads back one pixel out of a user-defined map.

Parameters :

- map_name ( str ) – The name of the map.

- level ( int ) – Which pyramid level the pixel should be read from.

- x ( int ) – Horizontal coordinate of the target pixel, measured from an
origin at the lower-left corner.

- y ( int ) – Vertical coordinate of the target pixel, measured from an
origin at the lower-left corner.

Returns :

The floating-point value stored for that pixel.

Return type :

float

## Freestyle Utilities (freestyle.utils)

### Freestyle Utilities (freestyle.utils) 

This module gathers the helper functions that support writing Freestyle style modules.

freestyle.utils. getCurrentScene ( ) 

Hands back the current scene.

Returns :

The current scene.

Return type :

bpy.types.Scene

freestyle.utils. integrate ( func , it , it_end , integration_type ) 

Collapses into one value the set of values evaluated at each 0D element of a given 1D element.

Parameters :

- func ( UnaryFunction0D ) – The UnaryFunction0D used to compute a value at each
Interface0D.

- it ( Interface0DIterator ) – The Interface0DIterator used to iterate over the 0D
elements of this 1D element. The integration will occur over
the 0D elements starting from the one pointed by it.

- it_end ( Interface0DIterator ) – The Interface0DIterator pointing the end of the 0D
elements of the 1D element.

- integration_type ( IntegrationType ) – The integration method used to compute a
single value from a set of values.

Returns :

The single value obtained for the 1D element. The return
value type is float if func is of the UnaryFunction0DDouble
or UnaryFunction0DFloat type, and int if func is of the
UnaryFunction0DUnsigned type.

Return type :

int | float

freestyle.utils. angle_x_normal ( it : Interface0DIterator ) 

the unsigned angle, in radians, separating a Point's normal from the X axis

freestyle.utils. bound ( lower , x , higher ) 

Clamps x between a lower and an upper limit. The same as: return min(max(x, lower), higher)

freestyle.utils. bounding_box ( stroke ) 

Gives back the smallest and largest coordinates spanning the stroke's vertices, i.e. its bounding box

freestyle.utils. curvature_from_stroke_vertex ( svert ) 

The 3D curvature of the geometry underneath a stroke vertex; the value is either None or somewhere in [-inf, inf]

freestyle.utils. find_matching_vertex ( id , it ) 

Locates the vertex that matches, or gives back None.

freestyle.utils. get_chain_length ( ve , orientation ) 

Gives back the 2d length of the supplied ViewEdge.

freestyle.utils. get_object_name ( stroke ) 

Gives back the name of the object on which this stroke is drawn.

freestyle.utils. get_strokes ( ) 

Fetches every stroke that is presently available

freestyle.utils. get_test_stroke ( ) 

Gives back a fixed stroke object meant for testing

freestyle.utils. is_poly_clockwise ( stroke ) 

True when the stroke runs in a clockwise direction, False if it does not

freestyle.utils. iter_distance_along_stroke ( stroke ) 

Produces, vertex by vertex, the cumulative distance traveled along the stroke up to the current one.

freestyle.utils. iter_distance_from_camera ( stroke , range_min , range_max , normfac ) 

For each stroke vertex, produces the distance to the camera as a fraction of the greatest distance possible, held within the supplied minimum and maximum bounds.

freestyle.utils. iter_distance_from_object ( stroke , location , range_min , range_max , normfac ) 

for each stroke vertex, produces the distance to the named object as a fraction of the greatest distance possible, held within the supplied minimum and maximum bounds.

freestyle.utils. iter_material_value ( stroke , func , attribute ) 

Produces one chosen material attribute taken from the material beneath the vertex.

freestyle.utils. iter_t2d_along_stroke ( stroke ) 

Produces the fractional progress made along the stroke.

freestyle.utils. material_from_fedge ( fe ) 

pull the diffuse RGBA color off an FEdge

freestyle.utils. normal_at_I0D ( it : Interface0DIterator ) → Vector 

The normal at an Interface0D object. Unlike Normal2DF0D, this routine relies on the real data rather than the underlying Fedge objects.

freestyle.utils. pairwise ( iterable , types={<class 'StrokeVertexIterator'> , <class 'Stroke'>} ) 

Produces a tuple holding the previous object alongside the current one

freestyle.utils. rgb_to_bw ( r , g , b ) 

Routine that turns rgb into a single bw intensity value.

freestyle.utils. simplify ( points , tolerance ) 

Reduces a collection of points

freestyle.utils. stroke_curvature ( it ) 

Works out the 2D curvature at the stroke vertex the iterator 'it' points to.
K = 1 / R
where R is the radius of the circle passing through the current vertex together with its neighbors

freestyle.utils. stroke_normal ( stroke ) 

Works out the 2D normal at the stroke vertex the iterator 'it' points to. Note that Normal2DF0D instead derives normals from the underlying FEdges, which is a poor fit for strokes once stroke geometry modifiers have already changed them.

The normals returned are dynamic, refreshing whenever the vertex position (and thus the vertex normal) shifts. When using this in geometry modifiers, you are advised to cast this generator function into a tuple or list

freestyle.utils. tripplewise ( iterable ) 

Produces a tuple holding the current object together with the neighbors on either side

class freestyle.utils. BoundingBox 

An object standing for a bounding box made up of 2 2D vectors

inside ( other ) 

True when self lies within other, False if not

classmethod from_sequence ( sequence ) 

BoundingBox built from a sequence of 2D or 3D Vector objects

class freestyle.utils. StrokeCollector 

Gathers and keeps stroke objects

shade ( stroke )

## GPU Capabilities Utilities (gpu.capabilities)

### GPU Capabilities Utilities (gpu.capabilities)

Through this module you can query what the GPU is able to do.

gpu.capabilities. compute_shader_support_get ( )

Reports whether compute shaders can run.

Returns :

True when supported, False when not supported.

Return type :

bool

gpu.capabilities. extensions_get ( )

Lists the extensions available in the active context.

Returns :

Extensions.

Return type :

tuple[str, …]

gpu.capabilities. hdr_support_get ( )

Tells you if the GPU backend can drive High Dynamic Range output in the viewport.

Returns :

HDR support available.

Return type :

bool

gpu.capabilities. max_batch_indices_get ( )

Reports the largest number of vertex array indices allowed.

Returns :

Number of indices.

Return type :

int

gpu.capabilities. max_batch_vertices_get ( )

Reports the largest number of vertex array vertices allowed.

Returns :

Number of vertices.

Return type :

int

gpu.capabilities. max_images_get ( )

Reports the ceiling on image units the GPU will accept.

Returns :

Number of image units.

Return type :

int

gpu.capabilities. max_texture_layers_get ( )

Reports how many layers a texture may hold at most.

Returns :

Number of layers.

Return type :

int

gpu.capabilities. max_texture_size_get ( )

Reports an estimate of the biggest texture the hardware can cope with.

Returns :

Texture size.

Return type :

int

gpu.capabilities. max_textures_frag_get ( )

Reports the ceiling on texture image units the fragment shader may use when
sampling texture maps.

Returns :

Texture image units.

Return type :

int

gpu.capabilities. max_textures_geom_get ( )

Reports the ceiling on texture image units the geometry shader may use when
sampling texture maps.

Returns :

Texture image units.

Return type :

int

gpu.capabilities. max_textures_get ( )

Reports the ceiling on texture image units shared by the vertex shader and the
fragment processor when sampling texture maps.

Returns :

Texture image units.

Return type :

int

gpu.capabilities. max_textures_vert_get ( )

Reports the ceiling on texture image units the vertex shader may use when
sampling texture maps.

Returns :

Texture image units.

Return type :

int

gpu.capabilities. max_uniforms_frag_get ( )

Reports how many values a fragment shader's uniform variable storage can hold.

Returns :

Number of values.

Return type :

int

gpu.capabilities. max_uniforms_vert_get ( )

Reports how many values a vertex shader's uniform variable storage can hold.

Returns :

Number of values.

Return type :

int

gpu.capabilities. max_varying_floats_get ( )

Reports the cap on varying variables shared between the vertex and fragment shaders.

Returns :

Number of variables.

Return type :

int

gpu.capabilities. max_vertex_attribs_get ( )

Reports how many vertex attributes a single vertex shader can reach.

Returns :

Number of attributes.

Return type :

int

gpu.capabilities. max_work_group_count_get ( index )

Reports the cap on work groups that a compute shader dispatch may launch.

Parameters :

index ( int ) – Index of the dimension.

Returns :

Maximum number of work groups for the queried dimension.

Return type :

int

gpu.capabilities. max_work_group_size_get ( index )

Reports the largest work group a compute shader dispatch may launch.

Parameters :

index ( int ) – Index of the dimension.

Returns :

Maximum size of a work group for the queried dimension.

Return type :

int

gpu.capabilities. shader_image_load_store_support_get ( )

Reports whether image load/store is available.

Returns :

True when supported, False when not supported.

Return type :

bool

## GPU Shader Utilities (gpu.shader)

### GPU Shader Utilities (gpu.shader)

This module opens up the internal functions of GPUShader.

Built-in shaders

A mat4 ModelViewProjectionMatrix uniform is present on every built-in shader.

You change its value through the gpu.matrix module.

Important

Be sure to set shader uniforms explicitly so that leftover values from earlier runs are not carried over.

`FLAT_COLOR`

Attributes :

vec3 pos, vec4 color

Uniforms :

none

IMAGE

Attributes :

vec3 pos, vec2 texCoord

Uniforms :

sampler2D image

`IMAGE_SCENE_LINEAR_TO_REC709_SRGB`

Attributes :

vec3 pos, vec2 texCoord

Uniforms :

sampler2D image

Note :

Expect texture to be in scene linear color space

`IMAGE_COLOR`

Attributes :

vec3 pos, vec2 texCoord

Uniforms :

sampler2D image, vec4 color

`IMAGE_COLOR_SCENE_LINEAR_TO_REC709_SRGB`

Attributes :

vec3 pos, vec2 texCoord

Uniforms :

sampler2D image, vec4 color

Note :

Expect texture to be in scene linear color space

`SMOOTH_COLOR`

Attributes :

vec3 pos, vec4 color

Uniforms :

none

`UNIFORM_COLOR`

Attributes :

vec3 pos

Uniforms :

vec4 color

`POLYLINE_FLAT_COLOR`

Attributes :

vec3 pos, vec4 color

Uniforms :

vec2 viewportSize, float lineWidth

`POLYLINE_SMOOTH_COLOR`

Attributes :

vec3 pos, vec4 color

Uniforms :

vec2 viewportSize, float lineWidth

`POLYLINE_UNIFORM_COLOR`

Attributes :

vec3 pos

Uniforms :

vec2 viewportSize, float lineWidth, vec4 color

`POINT_FLAT_COLOR`

Attributes :

vec3 pos, vec4 color

Uniforms :

float size

`POINT_UNIFORM_COLOR`

Attributes :

vec3 pos

Uniforms :

vec4 color, float size

gpu.shader. create_from_info ( shader_info )

Build a shader out of a GPUShaderCreateInfo.

Parameters :

shader_info (gpu.types.GPUShaderCreateInfo) – GPUShaderCreateInfo

Returns :

Shader object corresponding to the given shader info.

Return type :

gpu.types.GPUShader

gpu.shader. from_builtin ( shader_name , * , config = 'DEFAULT' )

These are the shaders baked into Blender's own code (refer to Built-in shaders).
Each of them reads the uniform mat4 ModelViewProjectionMatrix ,
which you can adjust through the gpu.matrix module.

A shader configuration relying on clip_planes is also selectable: pass CLIPPED as the config parameter. Be aware that doing so means you must also set the value of mat4 ModelMatrix by hand.

Parameters :

- shader_name ( str ) – One of the builtin shader names.

- config ( str ) – One of these types of shader configuration:

- DEFAULT

- CLIPPED

Returns :

Shader object corresponding to the given name.

Return type :

gpu.types.GPUShader

gpu.shader. unbind ( )

Release the currently bound shader object.

## GPU Texture Utilities (gpu.texture)

### GPU Texture Utilities (gpu.texture)

This module bundles helpers for working with textures.

gpu.texture. from_image ( image )

Obtain the GPUTexture tied to an Image data-block. That GPUTexture shares its memory with Blender.
Note: Colors read from the texture will be in scene linear color space and have premultiplied or straight alpha matching the image alpha mode.

Parameters :

image (bpy.types.Image) – The Image data-block.

Returns :

The GPUTexture used by the image.

Return type :

gpu.types.GPUTexture

# Gpu Types Gpu Types (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### GPU Types (gpu.types)

class gpu.types. Buffer ( format , dimensions , data )

Lets Python reach GPU functions that expect a pointer.

Parameters :

- format ( Literal [ 'FLOAT' , 'INT' , 'UINT' , 'UBYTE' , '`UINT_24_8`' , '10_11_11_REV' ] ) – Format type to interpret the buffer.
`UINT_24_8` is deprecated, use FLOAT instead.

- dimensions ( int | Sequence [ int ] ) – Array describing the dimensions.

- data (Buffer | Sequence [ float ] | Sequence [ int ] ) – Optional data array.

to_list ( )

Hand back the buffer as a list.

Returns :

The buffer as a list.

Return type :

list

dimensions

Undocumented, consider contributing.

class gpu.types. GPUBatch ( type , buf , elem = None )

Reusable container for drawable geometry.

Parameters :

- type ( Literal [ 'POINTS' , 'LINES' , 'TRIS' , '`LINE_STRIP`' , '`LINE_LOOP`' , '`TRI_STRIP`' , '`TRI_FAN`' , '`LINES_ADJ`' , '`TRIS_ADJ`' , '`LINE_STRIP_ADJ`' ] ) – The primitive type of geometry to be drawn.

- buf (gpu.types.GPUVertBuf) – Vertex buffer containing all or some of the attributes required for drawing.

- elem (gpu.types.GPUIndexBuf | None) – An optional index buffer.

draw ( shader = None )

Execute the drawing shader using the parameters bound to the batch.

Parameters :

shader (gpu.types.GPUShader | None) – Shader that performs the drawing operations.
If None is passed, the last shader set to this batch will run.

draw_instanced ( program , * , instance_start = 0 , instance_count = 0 )

Render several copies of the drawing program with the batch's bound parameters.
Inside the vertex shader, gl_InstanceID holds the index of the instance currently
being drawn.

Parameters :

- program (gpu.types.GPUShader) – Program that performs the drawing operations.

- instance_start ( int ) – Number of the first instance to draw.

- instance_count ( int ) – Number of instances to draw. When not provided or set to 0
the number of instances will be determined by the number of rows in the first
vertex buffer.

draw_range ( program , * , elem_start = 0 , elem_count = 0 )

Execute the drawing program with the batch's bound parameters. Restrict drawing to the elem_count elements of the index buffer beginning at elem_start .

Parameters :

- program (gpu.types.GPUShader) – Program that performs the drawing operations.

- elem_start ( int ) – First index to draw. When not provided or set to 0 drawing
will start from the first element of the index buffer.

- elem_count ( int ) – Number of elements of the index buffer to draw. When not
provided or set to 0 all elements from elem_start to the end of the
index buffer will be drawn.

program_set ( program )

Bind a shader to this batch so it serves for drawing unless replaced afterward.
Note: This method has to be called in the draw context that the batch will be drawn in.
This function does not need to be called when you always
set the shader when calling gpu.types.GPUBatch.draw().

Parameters :

program (gpu.types.GPUShader) – The program/shader the batch will use in future draw calls.

vertbuf_add ( buf )

Attach an extra vertex buffer to the Batch.
You cannot grow the batch's vertex count with this method.
What it does instead is let you layer more attributes onto the vertices already present.
A typical scenario is having one
vertex buffer for vertex positions and a separate one for vertex normals.
At present a batch is limited to at most `GPU_BATCH_VBO_MAX_LEN` vertex buffers.

Parameters :

buf (gpu.types.GPUVertBuf) – The vertex buffer that will be added to the batch.

class gpu.types. GPUFrameBuffer ( * , depth_slot = None , color_slots = None )

This object opens up the framebuffer functionality.
Supplying a ‘layer’ in an argument attaches a single layer of a 3D or array texture to the frame-buffer.
With cube map textures, the layer maps onto a cube map face.

Parameters :

- depth_slot (gpu.types.GPUTexture | dict[str, int | gpu.types.GPUTexture] | None) – GPUTexture to attach or a dict containing keywords: ‘texture’, ‘layer’ and ‘mip’.

- color_slots (gpu.types.GPUTexture | dict[str, int | gpu.types.GPUTexture] | Sequence[gpu.types.GPUTexture | dict[str, int | gpu.types.GPUTexture]] | None) – Tuple where each item can be a GPUTexture or a dict containing keywords: ‘texture’, ‘layer’ and ‘mip’.

bind ( )

Context manager to ensure balanced bind calls, even in the case of an error.

clear ( * , color = None , depth = None , stencil = None )

Load the color, depth, and stencil textures with a chosen value.
Common values: color=(0.0, 0.0, 0.0, 1.0), depth=1.0, stencil=0.

Parameters :

- color ( Sequence [ float ] | None ) – Sequence of 3 or 4 floats representing (r, g, b, a) .

- depth ( float | None ) – depth value.

- stencil ( int | None ) – stencil value.

read_color ( x , y , xsize , ysize , channels , slot , format , * , data = None )

Pull a rectangle of pixels out of the frame buffer.

Parameters :

- x ( int ) – Lower left corner x of a rectangular block of pixels.

- y ( int ) – Lower left corner y of a rectangular block of pixels.

- xsize ( int ) – Width of the pixel rectangle.

- ysize ( int ) – Height of the pixel rectangle.

- channels ( int ) – Number of components to read.

- slot ( int ) – The framebuffer slot to read data from.

- format ( Literal [ 'FLOAT' , 'INT' , 'UINT' , 'UBYTE' , '`UINT_24_8`' , '10_11_11_REV' ] ) – The format that describes the content of a single channel.
`UINT_24_8` is deprecated, use FLOAT instead.

- data (gpu.types.Buffer | None) – Optional Buffer object to fill with the pixels values.

Returns :

The Buffer with the read pixels.

Return type :

gpu.types.Buffer

read_depth ( x , y , xsize , ysize , * , data = None )

Pull a block of depth pixels out of the frame buffer.

Parameters :

- x ( int ) – Lower left corner x of a rectangular block of pixels.

- y ( int ) – Lower left corner y of a rectangular block of pixels.

- xsize ( int ) – Width of the pixel rectangle.

- ysize ( int ) – Height of the pixel rectangle.

- data (gpu.types.Buffer | None) – Optional Buffer object to fill with the pixels values.

Returns :

The Buffer with the read pixels.

Return type :

gpu.types.Buffer

viewport_get ( )

Reports the position and size of the current viewport.

Returns :

The viewport as (x, y, width, height) .

Return type :

tuple[int, int, int, int]

viewport_set ( x , y , xsize , ysize )

Assign the viewport for this framebuffer object.
Note: The viewport state is not saved upon framebuffer rebind.

Parameters :

- x ( int ) – Lower left corner x of the viewport rectangle, in pixels.

- y ( int ) – Lower left corner y of the viewport rectangle, in pixels.

- xsize ( int ) – Width of the viewport.

- ysize ( int ) – Height of the viewport.

is_bound

Tests whether this is the frame-buffer currently active in the context.

class gpu.types. GPUIndexBuf ( type , seq )

Holds an index buffer.

Parameters :

- type ( Literal [ 'POINTS' , 'LINES' , 'TRIS' , '`LINES_ADJ`' , '`TRIS_ADJ`' ] ) – The primitive type this index buffer is composed of.

- seq (Buffer | Sequence [ int ] | Sequence [ Sequence [ int ] ] ) – Indices this index buffer will contain.
Whether a 1D or 2D sequence is required depends on the type.
Optionally the sequence can support the buffer protocol.

class gpu.types. GPUOffScreen ( width , height , * , format = 'RGBA8' )

This object opens up the off screen buffers.

Parameters :

- width ( int ) – Horizontal dimension of the buffer.

- height ( int ) – Vertical dimension of the buffer.

- format ( Literal [ 'RGBA8' , 'RGBA16' , 'RGBA16F' , 'RGBA32F' ] ) – Internal data format inside GPU memory for color attachment texture.

bind ( )

Context manager to ensure balanced bind calls, even in the case of an error.

Returns :

A context manager for the off-screen binding.

Return type :

gpu.types.OffScreenStackContext

draw_view3d ( scene , view_layer , view3d , region , view_matrix , projection_matrix , * , do_color_management = False , draw_background = True )

Render the 3d viewport into the offscreen object.

Parameters :

- scene (bpy.types.Scene) – Scene to draw.

- view_layer (bpy.types.ViewLayer) – View layer to draw.

- view3d (bpy.types.SpaceView3D) – 3D View to get the drawing settings from.

- region (bpy.types.Region) – Region of the 3D View (required as temporary draw target).

- view_matrix (mathutils.Matrix) – View Matrix (e.g. camera.matrix_world.inverted() ).

- projection_matrix (mathutils.Matrix) – Projection Matrix (e.g. camera.calc_matrix_camera(...) ).

- do_color_management ( bool ) – Color manage the output.

- draw_background ( bool ) – Draw background.

free ( )

Release the offscreen object.
Its framebuffer, texture, and render objects stop being reachable afterward.

unbind ( * , restore = True )

Release the offscreen object's binding.

Parameters :

restore ( bool ) – Restore the OpenGL state, can only be used when the state has been saved before.

height

Height of the texture.

Type :

int

texture_color

The color texture attached.

Type :

gpu.types.GPUTexture

width

Width of the texture.

Type :

int

class gpu.types. GPUShader

attr_from_name ( name )

Look up an attribute's location from its name.

Parameters :

name ( str ) – The name of the attribute variable whose location is to be queried.

Returns :

The location of an attribute variable.

Return type :

int

attrs_info_get ( )

Details about the attributes that the Shader uses.

Returns :

tuples containing information about the attributes in order (name, type)

Return type :

tuple[tuple[str, str | None], …]

bind ( )

Bind the shader object. You need this before any of its uniforms can be changed.

format_calc ( )

Construct a fresh format from the shader's attributes.

Returns :

vertex attribute format for the shader

Return type :

gpu.types.GPUVertFormat

image ( name , texture )

Assign a value to an image variable on the current GPUShader.

Parameters :

- name ( str ) – Name of the image variable to which the texture is to be bound.

- texture (gpu.types.GPUTexture) – Texture to attach.

uniform_block ( name , ubo )

Assign a value to a uniform buffer object variable on the current GPUShader.

Parameters :

- name ( str ) – Name of the uniform variable whose UBO is to be specified.

- ubo (gpu.types.GPUUniformBuf) – Uniform Buffer to attach.

uniform_block_from_name ( name )

Look up a uniform block's location from its name.

Parameters :

name ( str ) – Name of the uniform block variable whose location is to be queried.

Returns :

The location of the uniform block variable.

Return type :

int

uniform_bool ( name , value )

Assign a value to a uniform variable on the current program object.

Parameters :

- name ( str ) – Name of the uniform variable whose value is to be changed.

- value ( bool | Sequence [ bool ] ) – Value that will be used to update the specified uniform variable.

uniform_float ( name , value )

Assign a value to a uniform variable on the current program object.

Parameters :

- name ( str ) – Name of the uniform variable whose value is to be changed.

- value ( float | Sequence [ float ] ) – Value that will be used to update the specified uniform variable.

uniform_from_name ( name )

Look up a uniform's location from its name.

Parameters :

name ( str ) – Name of the uniform variable whose location is to be queried.

Returns :

Location of the uniform variable.

Return type :

int

uniform_int ( name , seq )

Assign a value to a uniform variable on the current program object.

Parameters :

- name ( str ) – Name of the uniform variable whose value is to be changed.

- seq ( int | Sequence [ int ] ) – Value that will be used to update the specified uniform variable.

uniform_sampler ( name , texture )

Assign a value to a texture uniform variable on the current GPUShader.

Parameters :

- name ( str ) – Name of the uniform variable whose texture is to be specified.

- texture (gpu.types.GPUTexture) – Texture to attach.

uniform_vector_float ( location , buffer , length , count )

Supply the buffer that fills the uniform.

Parameters :

- location ( int ) – Location of the uniform variable to be modified.

- buffer ( Sequence [ float ] ) – The data that should be set. Can support the buffer protocol.

- length ( int ) – Size of the uniform data type:

- 1: float

- 2: vec2 or float[2]

- 3: vec3 or float[3]

- 4: vec4 or float[4]

- 9: mat3

- 16: mat4

- count ( int ) – Specifies the number of elements, vector or matrices that are to be modified.

uniform_vector_int ( location , buffer , length , count )

Supply the buffer that fills the uniform.

Parameters :

- location ( int ) – Location of the uniform variable to be modified.

- buffer (Buffer) – Buffer object with format matching the uniform.

- length ( int ) – Size of the uniform data type.

- count ( int ) – Specifies the number of elements that are to be modified.

name

The shader object's name, kept for debugging purposes (read-only).

Type :

str

program

The program object's name as the OpenGL API sees it (read-only).
It is deprecated and from now on always yields -1.

Type :

int

class gpu.types. GPUShaderCreateInfo

Records and describes the types and variables that shader sources rely on.

compute_source ( source )

compute shader source code written in GLSL.

Example:

`text
"""void main() {
int2 index = int2(gl_GlobalInvocationID.xy);
vec4 color = vec4(0.0, 0.0, 0.0, 1.0);
imageStore(img_output, index, color);
}"""
`

Parameters :

source ( str ) – The compute shader source code.

See also

GLSL Cross Compilation

define ( name , value )

Register a preprocessing define directive. The GLSL equivalent looks roughly like:

`text
#define name value
`

Parameters :

- name ( str ) – Token name.

- value ( str ) – Text that replaces token occurrences.

depth_write ( value )

Declare how depth writing should behave when gl_FragDepth is altered.

GPUs often apply an optimization that runs an early depth
test ahead of the fragment shader, letting the shader work be
skipped when the fragment turns out to be occluded and thus discarded.

This optimization leaves the final image untouched, and it is generally
available as long as the fragment does not change its depth programmatically.
That said, there is a set of depth operations in the shader that
can still happen while keeping the early depth test usable.

This function adjusts the optimization's behavior so those operations
can be carried out.

Parameters :

value ( Literal [ 'UNCHANGED' , 'ANY' , 'GREATER' , 'LESS' ] ) – Depth write value.
:UNCHANGED: disables depth write in a fragment shader and execution of the fragments can be optimized away.
:ANY: enables depth write in a fragment shader for any fragments
:GREATER: enables depth write in a fragment shader for depth values that are greater than the depth value in the output buffer.
:LESS: enables depth write in a fragment shader for depth values that are less than the depth value in the output buffer.

fragment_out ( slot , type , name , * , blend = 'NONE' )

Declare a fragment output that maps to a framebuffer target slot.

Parameters :

- slot ( int ) – The attribute index.

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the output.

- name ( str ) – Name of the attribute.

- blend ( Literal [ 'NONE' , '`SRC_0`' , '`SRC_1`' ] ) – Dual Source Blending Index.

fragment_source ( source )

Fragment shader source code written in GLSL.

Example:

`text
"void main() {fragColor = vec4(0.0, 0.0, 0.0, 1.0);}"
`

Parameters :

source ( str ) – The fragment shader source code.

See also

GLSL Cross Compilation

image ( slot , format , type , name , * , qualifiers = {'`NO_RESTRICT`'} )

Declare an image resource for arbitrary load and store operations.

Parameters :

- slot ( int ) – The image resource index.

- format ( Literal [ 'RGBA8UI' , 'RGBA8I' , 'RGBA8' , 'RGBA32UI' , 'RGBA32I' , 'RGBA32F' , 'RGBA16UI' , 'RGBA16I' , 'RGBA16F' , 'RGBA16' , 'RG8UI' , 'RG8I' , 'RG8' , 'RG32UI' , 'RG32I' , 'RG32F' , 'RG16UI' , 'RG16I' , 'RG16F' , 'RG16' , 'R8UI' , 'R8I' , 'R8' , 'R32UI' , 'R32I' , 'R32F' , 'R16UI' , 'R16I' , 'R16F' , 'R16' , '`R11F_G11F_B10F`' , '`DEPTH32F_STENCIL8`' , '`DEPTH24_STENCIL8`' , '`SRGB8_A8`' , 'RGB16F' , '`SRGB8_A8_DXT1`' , '`SRGB8_A8_DXT3`' , '`SRGB8_A8_DXT5`' , '`RGBA8_DXT1`' , '`RGBA8_DXT3`' , '`RGBA8_DXT5`' , '`DEPTH_COMPONENT32F`' , '`DEPTH_COMPONENT24`' , '`DEPTH_COMPONENT16`' ] ) – The GPUTexture format that is passed to the shader.

- type ( Literal [ '`FLOAT_BUFFER`' , '`FLOAT_1D`' , '`FLOAT_1D_ARRAY`' , '`FLOAT_2D`' , '`FLOAT_2D_ARRAY`' , '`FLOAT_3D`' , '`FLOAT_CUBE`' , '`FLOAT_CUBE_ARRAY`' , '`INT_BUFFER`' , '`INT_1D`' , '`INT_1D_ARRAY`' , '`INT_2D`' , '`INT_2D_ARRAY`' , '`INT_3D`' , '`INT_CUBE`' , '`INT_CUBE_ARRAY`' , '`UINT_BUFFER`' , '`UINT_1D`' , '`UINT_1D_ARRAY`' , '`UINT_2D`' , '`UINT_2D_ARRAY`' , '`UINT_3D`' , '`UINT_CUBE`' , '`UINT_CUBE_ARRAY`' , '`SHADOW_2D`' , '`SHADOW_2D_ARRAY`' , '`SHADOW_CUBE`' , '`SHADOW_CUBE_ARRAY`' , '`DEPTH_2D`' , '`DEPTH_2D_ARRAY`' , '`DEPTH_CUBE`' , '`DEPTH_CUBE_ARRAY`' ] ) – The data type describing how the image is to be read in the shader.

- name ( str ) – The image resource name.

- qualifiers ( set [ Literal [ '`NO_RESTRICT`' , 'READ' , 'WRITE' ] ] ) – Set containing values that describe how the image resource is to be read or written.

local_group_size ( x , y = 1 , z = 1 )

Declare the local group size for compute shaders.

Parameters :

- x ( int ) – The local group size in the x dimension.

- y ( int ) – The local group size in the y dimension. Optional. Defaults to 1.

- z ( int ) – The local group size in the z dimension. Optional. Defaults to 1.

push_constant ( type , name , size = 0 )

Declare a globally accessible constant.

Parameters :

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the constant.

- name ( str ) – Name of the constant.

- size ( int ) – If not zero, indicates that the constant is an array with the specified size.

sampler ( slot , type , name )

Declare an image texture sampler.

Parameters :

- slot ( int ) – The image texture sampler index.

- type ( Literal [ '`FLOAT_BUFFER`' , '`FLOAT_1D`' , '`FLOAT_1D_ARRAY`' , '`FLOAT_2D`' , '`FLOAT_2D_ARRAY`' , '`FLOAT_3D`' , '`FLOAT_CUBE`' , '`FLOAT_CUBE_ARRAY`' , '`INT_BUFFER`' , '`INT_1D`' , '`INT_1D_ARRAY`' , '`INT_2D`' , '`INT_2D_ARRAY`' , '`INT_3D`' , '`INT_CUBE`' , '`INT_CUBE_ARRAY`' , '`UINT_BUFFER`' , '`UINT_1D`' , '`UINT_1D_ARRAY`' , '`UINT_2D`' , '`UINT_2D_ARRAY`' , '`UINT_3D`' , '`UINT_CUBE`' , '`UINT_CUBE_ARRAY`' , '`SHADOW_2D`' , '`SHADOW_2D_ARRAY`' , '`SHADOW_CUBE`' , '`SHADOW_CUBE_ARRAY`' , '`DEPTH_2D`' , '`DEPTH_2D_ARRAY`' , '`DEPTH_CUBE`' , '`DEPTH_CUBE_ARRAY`' ] ) – The data type describing the format of each sampler unit.

- name ( str ) – The image texture sampler name.

typedef_source ( source )

Source code dropped in ahead of the resource declaration. Handy for defining structs that Uniform Buffers use.

Example:

`text
"struct MyType {int foo; float bar;};"
`

Parameters :

source ( str ) – The source code defining types.

uniform_buf ( slot , type_name , name )

Declare a uniform variable whose type may be any of those listed in gpu.types.GPUShaderCreateInfo.typedef_source().

Parameters :

- slot ( int ) – The uniform variable index.

- type_name ( str ) – Name of the data type. It can be a struct type defined in the source passed through the gpu.types.GPUShaderCreateInfo.typedef_source().

- name ( str ) – The uniform variable name.

vertex_in ( slot , type , name )

Register a vertex shader input attribute.

Parameters :

- slot ( int ) – The attribute index.

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the attribute.

- name ( str ) – name of the attribute.

vertex_out ( interface )

Register a vertex shader output interface block.

Parameters :

interface (gpu.types.GPUStageInterfaceInfo) – Object describing the block.

vertex_source ( source )

Vertex shader source code written in GLSL.

Example:

`text
"void main() {gl_Position = vec4(pos, 1.0);}"
`

Parameters :

source ( str ) – The vertex shader source code.

See also

GLSL Cross Compilation

class gpu.types. GPUStageInterfaceInfo ( name )

List of varyings between shader stages.

Parameters :

name ( str ) – Name of the interface block.

flat ( type , name )

Append an attribute carrying the flat qualifier to the interface block.

Parameters :

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the attribute.

- name ( str ) – name of the attribute.

no_perspective ( type , name )

Append an attribute carrying the no_perspective qualifier to the interface block.

Parameters :

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the attribute.

- name ( str ) – name of the attribute.

smooth ( type , name )

Append an attribute carrying the smooth qualifier to the interface block.

Parameters :

- type ( Literal [ 'FLOAT' , 'VEC2' , 'VEC3' , 'VEC4' , 'MAT3' , 'MAT4' , 'UINT' , 'UVEC2' , 'UVEC3' , 'UVEC4' , 'INT' , 'IVEC2' , 'IVEC3' , 'IVEC4' , 'BOOL' ] ) – The data type of the attribute.

- name ( str ) – name of the attribute.

name

Name of the interface block.

Type :

str

class gpu.types. GPUTexture ( size , * , layers = 0 , is_cubemap = False , format = 'RGBA8' , data = None )

This object opens up GPU textures.

Parameters :

- size ( int | Sequence [ int ] ) – Dimensions of the texture 1D, 2D, 3D or cubemap.

- layers ( int ) – Number of layers in texture array or number of cubemaps in cubemap array

- is_cubemap ( bool ) – Indicates the creation of a cubemap texture.

- format ( Literal [ 'RGBA8UI' , 'RGBA8I' , 'RGBA8' , 'RGBA32UI' , 'RGBA32I' , 'RGBA32F' , 'RGBA16UI' , 'RGBA16I' , 'RGBA16F' , 'RGBA16' , 'RG8UI' , 'RG8I' , 'RG8' , 'RG32UI' , 'RG32I' , 'RG32F' , 'RG16UI' , 'RG16I' , 'RG16F' , 'RG16' , 'R8UI' , 'R8I' , 'R8' , 'R32UI' , 'R32I' , 'R32F' , 'R16UI' , 'R16I' , 'R16F' , 'R16' , '`R11F_G11F_B10F`' , '`DEPTH32F_STENCIL8`' , '`DEPTH24_STENCIL8`' , '`SRGB8_A8`' , 'RGB16F' , '`SRGB8_A8_DXT1`' , '`SRGB8_A8_DXT3`' , '`SRGB8_A8_DXT5`' , '`RGBA8_DXT1`' , '`RGBA8_DXT3`' , '`RGBA8_DXT5`' , '`DEPTH_COMPONENT32F`' , '`DEPTH_COMPONENT24`' , '`DEPTH_COMPONENT16`' ] ) – Internal data format inside GPU memory.
`DEPTH24_STENCIL8` is deprecated, use `DEPTH32F_STENCIL8` .
`DEPTH_COMPONENT24` is deprecated, use `DEPTH_COMPONENT32F` .

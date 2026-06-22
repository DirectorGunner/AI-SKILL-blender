# Gpu Module Gpu

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### GPU Module (gpu)

The gpu module exposes Python bindings over Blender's internal GPU layer.
Additional convenience helpers live in the gpu_extras module.

### Geometry Batches

Drawing happens one batch at a time.
Each batch holds everything required to issue a draw call.
That means a mandatory Vertex Buffer plus an optional Index Buffer ,
both of which the sections below cover further.
On top of that a batch carries a draw type.
Common draw types include POINTS , LINES and TRIS .
This draw type controls how the stored data is read back and rendered.

### Vertex Buffers

The Vertex Buffer Object (VBO) (gpu.types.GPUVertBuf)
holds an array of the per-vertex attributes a given shader needs in order to draw.
Common examples of such attributes are location , normal , color , and uv .
Each vertex buffer carries a Vertex Format (gpu.types.GPUVertFormat)
along with a length matching how many vertices it stores.
The vertex format lays out which attributes sit on each vertex and what type each one is.

The snippet below builds a vertex buffer holding 6 vertices.
Two attributes are kept for every vertex: its position and its normal.

`text
import gpu
vertex_positions = [(0, 0, 0), ...]
vertex_normals = [(0, 0, 1), ...]

fmt = gpu.types.GPUVertFormat()
fmt.attr_add(id="pos", comp_type='F32', len=3, fetch_mode='FLOAT')
fmt.attr_add(id="normal", comp_type='F32', len=3, fetch_mode='FLOAT')

vbo = gpu.types.GPUVertBuf(len=6, format=fmt)
vbo.attr_fill(id="pos", data=vertex_positions)
vbo.attr_fill(id="normal", data=vertex_normals)
`

From this single buffer you might render 6 points, 3 standalone lines, 5 chained lines, 2 standalone triangles, and so on.
With lines, for example, every consecutive pair of vertices forms one segment.
Exactly which primitive gets rendered is settled at the moment the batch is built later on.

### Index Buffers

It is common for neighbouring triangles and lines to reuse the same vertices.
Relying on a vertex buffer alone forces you to repeat all the attributes of those shared vertices over and over.
That wastes a lot of memory, since in a connected triangle mesh each vertex is touched roughly 6 times.
A leaner option is the Index Buffer (IBO) (gpu.types.GPUIndexBuf),
which also goes by the name Element Buffer .
An Index Buffer simply holds an array pointing at vertices by their position inside the vertex buffer.

As an illustration, a rectangle made from two triangles can be expressed with an index buffer.

`text
positions = (
(-1, 1), (1, 1),
(-1, -1), (1, -1))

indices = ((0, 1, 2), (2, 1, 3))

ibo = gpu.types.GPUIndexBuf(type='TRIS', seq=indices)
`

In this code the first tuple inside indices names the vertices that make up the first triangle
(and the second tuple does the same for the second one).
Notice that vertices 1 and 2, lying on the diagonal, belong to both triangles.

### Shaders

Think of a shader as a small program executed by the GPU (here authored in GLSL).
Several shader kinds exist.
The two you care about most are the Vertex Shaders and the Fragment Shaders .
In general several shaders get linked together to form a Program .
Within Blender's Python API, though, the word Shader is used to mean an OpenGL Program.
A single gpu.types.GPUShader is made up of a vertex shader, a fragment shader, and optionally a geometry shader.
Blender ships a handful of ready-made shaders, reachable through gpu.shader.from_builtin
via identifiers like `UNIFORM_COLOR` or `FLAT_COLOR` . Dedicated builtins also exist for
rendering triangles, lines, and points.

Every shader declares the attributes and uniforms you must supply before it can run.
Attributes come from a vertex buffer and may vary from one vertex to the next.
Uniforms stay fixed for the whole draw call.
You assign them through the shader.uniform_* calls once the shader is bound.

Note

Keep in mind that on Apple operating systems the GLSL sources are translated into MSL (Metal Shading Language).
A thin compatibility layer handles this, and it does not implement every part of the GLSL specification.
The points below list the divergences worth remembering when you aim for Apple compatibility:

- Only these matrix constructors are supported:

- diagonal scalar (example: mat2(1) )

- all scalars (example: mat2(1, 0, 0, 1) )

- column vector (example: mat2(vec2(1,0), vec2(0,1)) )

- reshape constructors work only for square matrices (example: mat3(mat4(1)) )

- vertex , fragment and kernel are reserved keywords.

- every type and keyword laid down by the
MSL specification
counts as reserved and must be avoided.

### Batch Creation

You can assemble a batch the manual way by constructing VBOs and IBOs yourself.
Even so, reaching for the gpu_extras.batch.batch_for_shader helper is the recommended path.
It guarantees that all the vertex attributes a particular shader expects are present.
Because of that, you also have to hand the shader to the function.
Going this route, you seldom need to think about the vertex format, VBOs, or IBOs that get spun up behind the scenes.
You should still understand all of that when you start drawing, though.

Given that a batch can be reused across many draws, cache it and reuse it wherever you can.

### Offscreen Rendering

The image visible on screen once rendering finishes is known as the Front Buffer .
As draw calls fire, the batches land on a Back Buffer , and that only appears
once every draw has completed and the current back buffer is promoted to the new front buffer.
There are times when you would rather render the batches into a separate buffer, perhaps to use as a
texture on some other object or to save out as an image file.
That technique is Offscreen Rendering.
Blender handles Offscreen Rendering through the gpu.types.GPUOffScreen type.

Warning

gpu.types.GPUOffScreen objects stay tied to the OpenGL context in which they were created.
So as soon as Blender lets go of that context (for instance when the window closes),
the offscreen instance is released.

### Examples

To give these examples a spin, paste them straight into Blender's text editor and run them.
So that the examples stay short, they merely register a draw function that can no longer be removed easily.
You will need to restart Blender to clear out the draw handlers.

3D Points with Single Color

`text
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

coords = [(1, 1, 1), (-2, 0, 0), (-2, -1, 3), (0, 1, 1)]
shader = gpu.shader.from_builtin('`POINT_UNIFORM_COLOR`')
batch = batch_for_shader(shader, 'POINTS', {"pos": coords})

def draw():
shader.uniform_float("color", (1, 1, 0, 1))
gpu.state.point_size_set(4.5)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')

"""

3D Lines with Single Color
--------------------------
"""

import bpy
import gpu
from gpu_extras.batch import batch_for_shader

coords = [(1, 1, 1), (-2, 0, 0), (-2, -1, 3), (0, 1, 1)]
shader = gpu.shader.from_builtin('`POLYLINE_UNIFORM_COLOR`')
batch = batch_for_shader(shader, 'LINES', {"pos": coords})

def draw():
shader.uniform_float("viewportSize", gpu.state.viewport_get()[2:])
shader.uniform_float("lineWidth", 4.5)
shader.uniform_float("color", (1, 1, 0, 1))
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Triangle with Custom Shader

`text
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

vert_out = gpu.types.GPUStageInterfaceInfo("my_interface")
vert_out.smooth('VEC3', "pos")

shader_info = gpu.types.GPUShaderCreateInfo()
shader_info.push_constant('MAT4', "viewProjectionMatrix")
shader_info.push_constant('FLOAT', "brightness")
shader_info.vertex_in(0, 'VEC3', "position")
shader_info.vertex_out(vert_out)
shader_info.fragment_out(0, 'VEC4', "FragColor")

shader_info.vertex_source(
"void main()"
"{"
" pos = position;"
" gl_Position = viewProjectionMatrix * vec4(position, 1.0f);"
"}"
)

shader_info.fragment_source(
"void main()"
"{"
" FragColor = vec4(pos * brightness, 1.0);"
"}"
)

shader = gpu.shader.create_from_info(shader_info)
del vert_out
del shader_info

coords = [(1, 1, 1), (2, 0, 0), (-2, -1, 3)]
batch = batch_for_shader(shader, 'TRIS', {"position": coords})

def draw():
matrix = bpy.context.region_data.perspective_matrix
shader.uniform_float("viewProjectionMatrix", matrix)
shader.uniform_float("brightness", 0.5)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Wireframe Cube using Index Buffer

`text
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

coords = (
(-1, -1, -1), (+1, -1, -1),
(-1, +1, -1), (+1, +1, -1),
(-1, -1, +1), (+1, -1, +1),
(-1, +1, +1), (+1, +1, +1))

indices = (
(0, 1), (0, 2), (1, 3), (2, 3),
(4, 5), (4, 6), (5, 7), (6, 7),
(0, 4), (1, 5), (2, 6), (3, 7))

shader = gpu.shader.from_builtin('`POLYLINE_UNIFORM_COLOR`')
batch = batch_for_shader(shader, 'LINES', {"pos": coords}, indices=indices)

def draw():
shader.uniform_float("viewportSize", gpu.state.viewport_get()[2:])
shader.uniform_float("lineWidth", 4.5)
shader.uniform_float("color", (1, 0, 0, 1))
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Mesh with Random Vertex Colors

`text
import bpy
import gpu
import numpy as np
from random import random
from gpu_extras.batch import batch_for_shader

mesh = bpy.context.active_object.data
mesh.calc_loop_triangles()

vertices = np.empty((len(mesh.vertices), 3), 'f')
indices = np.empty((len(mesh.loop_triangles), 3), 'i')

mesh.vertices.foreach_get(
"co", np.reshape(vertices, len(mesh.vertices) * 3))
mesh.loop_triangles.foreach_get(
"vertices", np.reshape(indices, len(mesh.loop_triangles) * 3))

vertex_colors = [(random(), random(), random(), 1) for _ in range(len(mesh.vertices))]

shader = gpu.shader.from_builtin('`SMOOTH_COLOR`')
batch = batch_for_shader(
shader, 'TRIS',
{"pos": vertices, "color": vertex_colors},
indices=indices,
)

def draw():
gpu.state.depth_test_set('`LESS_EQUAL`')
gpu.state.depth_mask_set(True)
batch.draw(shader)
gpu.state.depth_mask_set(False)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### 2D Rectangle

`text
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

vertices = (
(100, 100), (300, 100),
(100, 200), (300, 200))

indices = (
(0, 1, 2), (2, 1, 3))

shader = gpu.shader.from_builtin('`UNIFORM_COLOR`')
batch = batch_for_shader(shader, 'TRIS', {"pos": vertices}, indices=indices)

def draw():
shader.uniform_float("color", (0, 0.5, 0.5, 1.0))
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_PIXEL`')
`

### 2D Image

Running this example requires you to supply an image to be shown.

`text
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

`IMAGE_NAME` = "Untitled"
image = bpy.data.images[`IMAGE_NAME`]
texture = gpu.texture.from_image(image)

shader = gpu.shader.from_builtin('`IMAGE_SCENE_LINEAR_TO_REC709_SRGB`')
batch = batch_for_shader(
shader, '`TRI_STRIP`',
{
"pos": ((100, 100), (200, 100), (100, 200), (200, 200)),
"texCoord": ((0, 0), (1, 0), (0, 1), (1, 1)),
},
)

def draw():
shader.bind()
shader.uniform_sampler("image", texture)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_PIXEL`')

"""
3D Image
--------

Similar to the 2D Image shader, but works with 3D positions for the image vertices.
To use this example you have to provide an image that should be displayed.
"""
import bpy
import gpu
from gpu_extras.batch import batch_for_shader

`IMAGE_NAME` = "Untitled"
image = bpy.data.images[`IMAGE_NAME`]
texture = gpu.texture.from_image(image)

shader = gpu.shader.from_builtin('`IMAGE_SCENE_LINEAR_TO_REC709_SRGB`')
batch = batch_for_shader(
shader, 'TRIS',
{
"pos": ((0, 0, 0), (0, 1, 1), (1, 1, 1), (1, 1, 1), (1, 0, 0), (0, 0, 0)),
"texCoord": ((0, 0), (0, 1), (1, 1), (1, 1), (1, 0), (0, 0)),
},
)

def draw():
shader.uniform_sampler("image", texture)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Generate a texture using Offscreen Rendering

- Create an gpu.types.GPUOffScreen object.

- Draw some circles into it.

- Make a new shader for drawing a planar texture in 3D.

- Draw the generated texture using the new shader.

`text
import bpy
import gpu
from mathutils import Matrix
from gpu_extras.batch import batch_for_shader
from gpu_extras.presets import draw_circle_2d

### Create and fill offscreen
##########################################

offscreen = gpu.types.GPUOffScreen(512, 512)

with offscreen.bind():
fb = gpu.state.active_framebuffer_get()
fb.clear(color=(0.0, 0.0, 0.0, 0.0))
with gpu.matrix.push_pop():
### Reset matrices -> use normalized device coordinates [-1, 1].
gpu.matrix.load_matrix(Matrix.Identity(4))
gpu.matrix.load_projection_matrix(Matrix.Identity(4))

amount = 10
for i in range(-amount, amount + 1):
x_pos = i / amount
draw_circle_2d((x_pos, 0.0), (1, 1, 1, 1), 0.5, segments=200)

### Drawing the generated texture in 3D space
#############################################

vert_out = gpu.types.GPUStageInterfaceInfo("my_interface")
vert_out.smooth('VEC2', "uvInterp")

shader_info = gpu.types.GPUShaderCreateInfo()
shader_info.push_constant('MAT4', "viewProjectionMatrix")
shader_info.push_constant('MAT4', "modelMatrix")
shader_info.sampler(0, '`FLOAT_2D`', "image")
shader_info.vertex_in(0, 'VEC2', "position")
shader_info.vertex_in(1, 'VEC2', "uv")
shader_info.vertex_out(vert_out)
shader_info.fragment_out(0, 'VEC4', "FragColor")

shader_info.vertex_source(
"void main()"
"{"
" uvInterp = uv;"
" gl_Position = viewProjectionMatrix * modelMatrix * vec4(position, 0.0, 1.0);"
"}"
)

shader_info.fragment_source(
"void main()"
"{"
" FragColor = texture(image, uvInterp);"
"}"
)

shader = gpu.shader.create_from_info(shader_info)
del vert_out
del shader_info

batch = batch_for_shader(
shader, '`TRI_STRIP`',
{
"position": ((-1, -1), (1, -1), (-1, 1), (1, 1)),
"uv": ((0, 0), (1, 0), (0, 1), (1, 1)),
},
)

def draw():
shader.uniform_float("modelMatrix", Matrix.Translation((1, 2, 3)) @ Matrix.Scale(3, 4))
shader.uniform_float("viewProjectionMatrix", bpy.context.region_data.perspective_matrix)
shader.uniform_sampler("image", offscreen.texture_color)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Copy Off-screen Rendering result back to RAM

This makes a fresh image under the name you give.
Should an image with that name already be present, it gets replaced.

At the moment nearly the whole runtime goes into that final line.
The plan is to fix this down the road by adding Python buffer protocol support
to gpu.types.Buffer and bpy.types.Image.pixels (aka bpy_prop_array ).

`text
import bpy
import gpu
import random
from mathutils import Matrix
from gpu_extras.presets import draw_circle_2d

`IMAGE_NAME` = "Generated Image"
WIDTH = 512
HEIGHT = 512
`RING_AMOUNT` = 10

offscreen = gpu.types.GPUOffScreen(WIDTH, HEIGHT)

with offscreen.bind():
fb = gpu.state.active_framebuffer_get()
fb.clear(color=(0.0, 0.0, 0.0, 0.0))
with gpu.matrix.push_pop():
### Reset matrices -> use normalized device coordinates [-1, 1].
gpu.matrix.load_matrix(Matrix.Identity(4))
gpu.matrix.load_projection_matrix(Matrix.Identity(4))

for i in range(`RING_AMOUNT`):
draw_circle_2d(
(random.uniform(-1, 1), random.uniform(-1, 1)),
(1, 1, 1, 1), random.uniform(0.1, 1),
segments=20,
)

buffer = fb.read_color(0, 0, WIDTH, HEIGHT, 4, 0, 'UBYTE')

offscreen.free()

if `IMAGE_NAME` not in bpy.data.images:
bpy.data.images.new(`IMAGE_NAME`, WIDTH, HEIGHT)
image = bpy.data.images[`IMAGE_NAME`]
image.scale(WIDTH, HEIGHT)

buffer.dimensions = WIDTH * HEIGHT * 4
image.pixels = [v / 255 for v in buffer]
`

### Rendering the 3D View into a Texture

For this example to run, the scene needs a camera.
You could instead make it work without a particular camera,
but at present Blender lacks convenient functions for building view and projection matrices.

`text
import bpy
import gpu
from gpu_extras.presets import draw_texture_2d

WIDTH = 512
HEIGHT = 256

offscreen = gpu.types.GPUOffScreen(WIDTH, HEIGHT)

def draw():
context = bpy.context
scene = context.scene

view_matrix = scene.camera.matrix_world.inverted()

projection_matrix = scene.camera.calc_matrix_camera(
context.evaluated_depsgraph_get(), x=WIDTH, y=HEIGHT)

offscreen.draw_view3d(
scene,
context.view_layer,
context.space_data,
context.region,
view_matrix,
projection_matrix,
do_color_management=True)

gpu.state.depth_mask_set(False)
draw_texture_2d(offscreen.texture_color, (10, 10), WIDTH, HEIGHT)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_PIXEL`')
`

### Custom Shader for dotted 3D Line

Here, each vertex computes its arc length, meaning the distance back to the line's first point.
That figure is then interpolated automatically across the vertex and fragment shaders
for every on-screen point in between.
The fragment shader takes the sine of that arc length.
From the outcome it decides whether or not to draw the fragment.

`text
import bpy
import gpu
from random import random
from mathutils import Vector
from gpu_extras.batch import batch_for_shader

vert_out = gpu.types.GPUStageInterfaceInfo("my_interface")
vert_out.smooth('FLOAT', "v_ArcLength")

shader_info = gpu.types.GPUShaderCreateInfo()
shader_info.push_constant('MAT4', "u_ViewProjectionMatrix")
shader_info.push_constant('FLOAT', "u_Scale")
shader_info.vertex_in(0, 'VEC3', "position")
shader_info.vertex_in(1, 'FLOAT', "arcLength")
shader_info.vertex_out(vert_out)
shader_info.fragment_out(0, 'VEC4', "FragColor")

shader_info.vertex_source(
"void main()"
"{"
" v_ArcLength = arcLength;"
" gl_Position = u_ViewProjectionMatrix * vec4(position, 1.0f);"
"}"
)

shader_info.fragment_source(
"void main()"
"{"
" if (step(sin(v_ArcLength * u_Scale), 0.5) == 1) discard;"
" FragColor = vec4(1.0);"
"}"
)

shader = gpu.shader.create_from_info(shader_info)
del vert_out
del shader_info

coords = [Vector((random(), random(), random())) * 5 for _ in range(5)]

arc_lengths = [0.0]
for a, b in zip(coords[:-1], coords[1:]):
arc_lengths.append(arc_lengths[-1] + (a - b).length)

batch = batch_for_shader(
shader, '`LINE_STRIP`',
{"position": coords, "arcLength": arc_lengths},
)

def draw():
matrix = bpy.context.region_data.perspective_matrix
shader.uniform_float("u_ViewProjectionMatrix", matrix)
shader.uniform_float("u_Scale", 10)
batch.draw(shader)

bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

### Custom compute shader (using image store) and vertex/fragment shader

This sample shows the workflow of running a custom compute shader
that writes into a texture, then feeding that texture to a vertex/fragment shader.
What you should see is a 2x2 plane (matching the default cube's size),
whose color shifts from a green-to-black gradient over to a green-to-red gradient,
driven by the current time.

`text
import bpy
import gpu
from mathutils import Matrix
from gpu_extras.batch import batch_for_shader
import time

start_time = time.time()

size = 128
texture = gpu.types.GPUTexture((size, size), format='RGBA32F')

### Create the compute shader to write to the texture.
compute_shader_info = gpu.types.GPUShaderCreateInfo()
compute_shader_info.image(0, 'RGBA32F', "`FLOAT_2D`", "img_output", qualifiers={"WRITE"})
compute_shader_info.compute_source('''
void main()
{
vec4 pixel = vec4(
sin(time / 1.0),
gl_GlobalInvocationID.y/128.0,
0.0,
1.0
);
imageStore(img_output, ivec2(gl_GlobalInvocationID.xy), pixel);
}''')
compute_shader_info.push_constant('FLOAT', "time")
compute_shader_info.local_group_size(1, 1)
compute_shader = gpu.shader.create_from_info(compute_shader_info)

### Create the shader to draw the texture.
vert_out = gpu.types.GPUStageInterfaceInfo("my_interface")
vert_out.smooth('VEC2', "uvInterp")
shader_info = gpu.types.GPUShaderCreateInfo()
shader_info.push_constant('MAT4', "viewProjectionMatrix")
shader_info.push_constant('MAT4', "modelMatrix")
shader_info.sampler(0, '`FLOAT_2D`', "img_input")
shader_info.vertex_in(0, 'VEC2', "position")
shader_info.vertex_in(1, 'VEC2', "uv")
shader_info.vertex_out(vert_out)
shader_info.fragment_out(0, 'VEC4', "FragColor")

shader_info.vertex_source(
"void main()"
"{"
" uvInterp = uv;"
" gl_Position = viewProjectionMatrix * modelMatrix * vec4(position, 0.0, 1.0);"
"}"
)

shader_info.fragment_source(
"void main()"
"{"
" FragColor = texture(img_input, uvInterp);"
"}"
)

shader = gpu.shader.create_from_info(shader_info)

batch = batch_for_shader(
shader, '`TRI_STRIP`',
{
"position": ((-1, -1), (1, -1), (-1, 1), (1, 1)),
"uv": ((0, 0), (1, 0), (0, 1), (1, 1)),
},
)

def draw():
shader.uniform_float("modelMatrix", Matrix.Translation((0, 0, 0)) @ Matrix.Scale(1, 4))
shader.uniform_float("viewProjectionMatrix", bpy.context.region_data.perspective_matrix)
shader.uniform_sampler("img_input", texture)
batch.draw(shader)
compute_shader.image('img_output', texture)
compute_shader.uniform_float("time", time.time() - start_time)
gpu.compute.dispatch(compute_shader, 128, 128, 1)

def drawTimer():
for area in bpy.context.screen.areas:
if area.type == '`VIEW_3D`':
area.tag_redraw()
return 1.0 / 60.0

bpy.app.timers.register(drawTimer)
bpy.types.SpaceView3D.draw_handler_add(draw, (), 'WINDOW', '`POST_VIEW`')
`

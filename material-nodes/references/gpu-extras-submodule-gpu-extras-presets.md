# Gpu Extras Submodule Gpu Extras Presets, Image Buffer Imbuf, Image Buffer Types Imbuf Types, Blender As A Python Module ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: gpu_extras submodule (gpu_extras.presets); Image Buffer (imbuf); Image Buffer Types (imbuf.types); Blender as a Python Module; Troubleshooting Errors & Crashes; Modes and Mesh Access.

## gpu_extras submodule (gpu_extras.presets)

### gpu_extras submodule (gpu_extras.presets)

gpu_extras.presets. draw_circle_2d ( position , color , radius , * , segments = None )

Render a circle.

Parameters :

- position ( Sequence [ float ] ) – 2D position where the circle will be drawn.

- color ( Sequence [ float ] ) – Color of the circle (RGBA).
To use transparency blend must be set to ALPHA , see: gpu.state.blend_set().

- radius ( float ) – Radius of the circle.

- segments ( int | None ) – How many segments will be used to draw the circle.
Higher values give better results but the drawing will take longer.
If None or not specified, an automatic value will be calculated.

gpu_extras.presets. draw_texture_2d ( texture , position , width , height , is_scene_linear_with_rec709_srgb_target = False )

Render a 2d texture.

Parameters :

- texture (gpu.types.GPUTexture) – GPUTexture to draw (e.g. gpu.texture.from_image(image) for bpy.types.Image).

- position ( Sequence [ float ] ) – 2D position of the lower left corner.

- width ( float ) – Width of the image when drawn (not necessarily
the original width of the texture).

- height ( float ) – Height of the image when drawn.

- is_scene_linear_with_rec709_srgb_target ( bool ) – True if the texture is stored in scene linear color space and
the destination frame-buffer uses the Rec.709 sRGB color space
(which is true when drawing textures acquired from bpy.types.Image inside a
‘`PRE_VIEW`’, ‘`POST_VIEW`’ or ‘`POST_PIXEL`’ draw handler).
Otherwise the color space is assumed to match the one of the frame-buffer. (default=False)

## Image Buffer (imbuf)

### Image Buffer (imbuf)

This module hands you Blender's image manipulation API.

It lets you work with image buffers that sit outside the
bpy.types.Image data-block context.

imbuf. load ( filepath )

Read an image in from a file.

Parameters :

filepath ( str | bytes ) – The filepath of the image.

Returns :

The newly loaded image.

Return type :

ImBuf

imbuf. load_from_buffer ( buffer )

Read an image in from a buffer.

Parameters :

buffer ( collections.abc.Buffer ) – A buffer containing the image data.

Returns :

The newly loaded image.

Return type :

ImBuf

imbuf. new ( size )

Make a fresh image.

Parameters :

size ( tuple [ int , int ] ) – The size of the image in pixels.

Returns :

The newly created image.

Return type :

ImBuf

imbuf. write ( image , * , filepath = None )

Save an image out.

Parameters :

- image ( ImBuf ) – The image to write.

- filepath ( str | bytes | None ) – Optional filepath of the image (fallback to the image’s file path).

## Image Buffer Types (imbuf.types)

### Image Buffer Types (imbuf.types)

This module hands you the image buffer types.

Note

Image buffer is also the structure used by bpy.types.Image
ID type to store and manipulate image data at runtime.

class imbuf.types. ImBuf

copy ( )

Hand back a copy of the image.

Returns :

A copy of the image.

Return type :

ImBuf

crop ( min , max )

Crop the image without making a copy.

Parameters :

- min ( tuple [ int , int ] ) – Minimum pixel coordinates (X, Y), inclusive.

- max ( tuple [ int , int ] ) – Maximum pixel coordinates (X, Y), inclusive.

free ( )

Release the image data right away (which makes any later use raise an error).

resize ( size , * , method = 'FAST' )

Resize the image without making a copy.

Parameters :

- size ( tuple [ int , int ] ) – New size.

- method ( str ) – Method of resizing (‘FAST’, ‘BILINEAR’).

channels

Number of color channels.

Type :

int

filepath

Filepath associated with this image.

Type :

str

planes

Number of bits per pixel.

Type :

int

ppm

Pixels per meter.

Type :

tuple[float, float]

size

Size of the image in pixels.

Type :

tuple[int, int]

## Blender as a Python Module

### Blender as a Python Module

You can compile Blender into a Python module, which then lets
import bpy slot into any Python script and unlock Blender's capabilities.

Note

You won't find the Blender as a Python Module build listed among the official downloads on Blender's site.

- You can pull a ready-built bpy module
straight from PIP.

- Alternatively, build it from source by following the
build instructions.

### Use Cases

A Python developer might want to fold Blender scripts into projects whose focus lies elsewhere than Blender.

A few of the possibilities it opens up:

- Turning datasets into rendered stills and animations.

- Running images through Blender’s compositor.

- Cutting video by way of Blender’s sequencer.

- Converting between 3D file formats.

- Development work, such as reaching bpy from Python IDEs and debugging tools.

- Automation.

### Usage

By and large, treating Blender as a Python module mirrors running a script in background-mode
(the one you get by passing the command-line arguments --background or -b ),
yet a few distinctions are worth keeping in mind.

Blender’s Executable Access
The bpy.app.binary_path attribute starts out as an empty string.

Should you want it aimed at a known executable, you are free to assign the value.

The snippet below hunts for the binary and assigns it once located:

`text
import bpy
import shutil

blender_bin = shutil.which("blender")
if blender_bin:
print("Found:", blender_bin)
bpy.app.binary_path = blender_bin
else:
print("Unable to find blender!")
`

Blender’s Internal Modules
Blender bundles a number of modules, gpu and mathutils among them.
Be sure to import these only after bpy ; otherwise they will not be located.

Command Line Arguments Unsupported
Anything driven by command line arguments (which blender --help lists) is out of reach.

Usually that is no great loss, though a handful of command line arguments have no
counterpart in Blender's Python API ( --threads and --log being examples).

Note

These settings might gain exposure later on, if a need for them arises.

Resource Sharing (GPU)
It can happen that other Python modules grab the GPU in a manner that locks Blender/Cycles out of it.

Signal Handlers
Because Blender's usual signal handlers stay uninitialized, there is no dedicated handling of Control-C
to abort a render, and no crash log gets written should a crash occur.

Startup and Preferences
Loading the bpy module brings in the default startup scene
(rather than the “empty” blend-file you might assume), so a default cube, camera, and light are present.

To begin instead from a blank file, call: bpy.ops.wm.read_factory_settings(use_empty=True) .

To keep your local setup from coloring how the script runs, the user's startup and preferences are skipped.
The Python module acts just as though --factory-startup had been supplied as a command line argument.

Should you need them, the user's startup and preferences can be brought in through operators:

`text
import bpy

bpy.ops.wm.read_userpref()
bpy.ops.wm.read_homefile()
`

### Limitations

The bulk of Blender's constraints as an application carry over:

Reloading Unsupported
Trying to reload the bpy module through importlib.reload throws an exception
rather than reloading and resetting it.

To get the internal state back to a clean slate, reach for the bpy.ops.wm.read_factory_settings() operator instead.

Single Blend File Restriction
You can only have one .blend file open for editing at any moment.

Hint

As with the full application, nothing stops you from launching multiple instances at once,
each holding its own bpy and, by extension, its own Blender state.
For talking to those sub-processes more comfortably, Python ships the multiprocessing module.

For certain workflows the library API can stand in for spawning separate processes,
though it works by reading and writing ID data-blocks and therefore isn’t
a full replacement for opening .blend files, see:

- bpy.types.BlendDataLibraries.load()

- bpy.types.BlendDataLibraries.write()

- bpy.types.BlendData.temp_data()
supports a temporary data-context to avoid manipulating the current .blend file.

## Troubleshooting Errors & Crashes

### Troubleshooting Errors & Crashes

### Help! My script crashes Blender

TL;DR Don't hang on to direct references to Blender data (of whatever kind) while you're editing the container holding that data, or anywhere undo/redo might fire (for instance during a modal operator's run). Instead, work through indices — or other things Python stores by value, such as string keys — that let you fetch the data you're after.

In an ideal world Python could never crash Blender, but in practice there are spots in the API where a crash is reachable. Technically that's an API bug, yet patching it would require memory checks on every single access: most crashes trace back to Python objects pointing straight at Blender's memory, and once that memory is freed or moved, any further Python access to it can take the script down. Fixing it properly would either make scripts crawl, or demand a wholly different API that never references the memory directly.

Some broad pointers for steering clear of these traps:

- Watch your memory footprint,
above all with large lists, since Blender can crash purely by exhausting memory.

- A lot of stubborn crashes boil down to referencing freed data; when you delete data make sure you're not still holding a reference to it.

- Re-allocation lands you in the same trouble
(e.g. piling many items into a Collection can force the backing container's memory to move, which voids every reference you held to existing items).

- Long-lived modules or classes that persist as Blender runs
shouldn't hold onto data the user could remove; rather,
have the script re-read whatever it needs from the context on each activation.

- Crashes can be intermittent — surfacing more readily on certain setups or operating systems.

- Tread carefully with recursion, which is remarkably good at masking the problems described here.

- See the closing Unfortunate Corner Cases section for some known exceptions that break.

Note

To pin down which line of your script crashes, the faulthandler module helps.
See the Faulthandler docs.

The crash itself may sit inside Blender's C/C++ code, but this can go a long way toward locating the part of the script that triggers it.

Note

A few container edits are in fact safe, because they never relocate existing data
(e.g. linked-list containers never move existing items when others are added or removed).

But telling the safe cases from the unsafe ones demands a deep grasp of Blender's internals. So unless you're prepared to wade into the RNA C implementation, the simpler stance is to always assume that modifying a container — in any way at all — invalidates references into it.

Do not:

`\text
class TestItems(bpy.types.PropertyGroup):
name: bpy.props.StringProperty()

bpy.utils.register_class(TestItems)
bpy.types.Scene.test_items = bpy.props.CollectionProperty(type=TestItems)

first_item = bpy.context.scene.test_items.add()
for i in range(100):
bpy.context.scene.test_items.add()

### This is likely to crash, as internal code may re-allocate
### the whole container (the collection) memory at some point.
first_item.name = "foobar"
`

Do:

`\text
class TestItems(bpy.types.PropertyGroup):
name: bpy.props.StringProperty()

bpy.utils.register_class(TestItems)
bpy.types.Scene.test_items = bpy.props.CollectionProperty(type=TestItems)

first_item = bpy.context.scene.test_items.add()
for i in range(100):
bpy.context.scene.test_items.add()

### This is safe, we are getting again desired data *after*
### all modifications to its container are done.
first_item = bpy.context.scene.test_items[0]
first_item.name = "foobar"
`

### Undo/Redo

To stay safe, treat every undo and redo as invalidating all bpy.types.ID instances (Object, Scene, Mesh, Light, etc.), and of course all of their sub-data along with them.

The snippet below demonstrates how undo shifts where things sit in memory:

`\text
>>> hash(bpy.context.object)
-9223372036849950810
>>> hash(bpy.context.object)
-9223372036849950810
`

Delete the active object, then undo:

`\text
>>> hash(bpy.context.object)
-9223372036849951740
`

As said above, the one dependable way to keep a script stable is simply to avoid holding references to data while a person is working in Blender interactively.

Note

The modern undo/redo system no longer wipes every pointer without exception. Data that a given history step found unchanged — which, in ordinary use, is most of it — can stay put, and so its pointers can stay valid.

Keep in mind, though, that should you decide to lean on that behavior for whatever reason, there's no guarantee at all of safety or consistency — doing so is at your own risk.

#### Modifying Blender Data & Undo

As a rule, changing Blender data should always spawn an undo step. Skip it and you invite trouble, anywhere from a corrupt or broken undo stack to outright crashes on undo/redo.

That holds doubly when you edit Blender data inside operators.

#### Undo & Library Data

A nice property of Blender's library linking is that undo can skip diffing library data, on the premise that it stays static. Blender's own tools aren't permitted to alter library data — but Python doesn't impose that limit.

That can be handy at times, say a script that nudges material values. Yet you could also script library data into pointing at freshly made local data, which isn't supported: a later undo strips the local data while leaving the library still referencing it, and that will likely crash.

So treat editing library data as an advanced corner of the API, and only reach for it when you're sure of what you're doing.

### Abusing RNA property callbacks

RNA properties defined in Python can carry custom callbacks. Doing anything heavy from inside one — calling an operator, for instance — might work, but it's neither officially advised nor supported.

Chiefly it's because such callbacks are supposed to be very fast; on top of that, code like this can, for instance, tangle up undo/redo (a history step gets stored by most operators, and the same happens when you edit an RNA property), kick off never-ending update cycles, and the like.

### Edit-Mode / Memory Access

Switching mode with bpy.ops.object.mode_set(mode='EDIT') or bpy.ops.object.mode_set(mode='OBJECT') relocates an object's data, so any references you held to a mesh's vertices/polygons/UVs, an armature's bones, a curve's points, and so on, can't be used once the mode flips.

It's only the reference to the data itself that you can fetch again; the snippet below will crash.

`\text
mesh = bpy.context.active_object.data
polygons = mesh.polygons
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.object.mode_set(mode='OBJECT')

### This will crash!
print(polygons)
`

That's why, after a mode switch, you have to re-fetch any object-data variables; the version below shows how to dodge the crash above.

`\text
mesh = bpy.context.active_object.data
polygons = mesh.polygons
bpy.ops.object.mode_set(mode='EDIT')
bpy.ops.object.mode_set(mode='OBJECT')

### Polygons have been re-allocated.
polygons = mesh.polygons
print(polygons)
`

The same class of problem can crop up for any function that relocates object data, though switching mode is where it shows up most.

### Array Re-Allocation

When you append new points onto a curve — or new vertices, edges or polygons onto a mesh — the internal array storing that data gets relocated by Blender.

`\text
bpy.ops.curve.primitive_bezier_curve_add()
point = bpy.context.object.data.splines[0].bezier_points[0]
bpy.context.object.data.splines[0].bezier_points.add()

### This will crash!
point.co = 1.0, 2.0, 3.0
`

You can sidestep this by re-fetching the point variables after the new one goes in, or by keeping indices to the points rather than the point objects.

The cleanest fix, though, is to dodge the whole issue by adding every point to the curve in one go. Then there's no array re-allocation to worry about, and it's quicker as well, since rebuilding the entire array for each individual point is wasteful.

### Removing Data

After data is removed, reading or modifying it is off-limits. The rule spans constraints and modifiers, markers on the timeline, render layers, drivers and F-Curves, as well as bones, collections, scenes, objects, and the rest.

The remove() API calls deliberately invalidate whatever they free, heading off common slip-ups. The example below shows that safeguard in action:

`\text
mesh = bpy.data.meshes.new(name="MyMesh")
### Normally the script would use the mesh here.
bpy.data.meshes.remove(mesh)
print(mesh.name) #

`\text
mesh = bpy.data.meshes.new(name="MyMesh")
vertices = mesh.vertices
bpy.data.meshes.remove(mesh)
print(vertices) #

### Unfortunate Corner Cases

On top of every expected case above, a handful of others ought to be fine but, owing to internal implementation quirks, currently aren't:

#### Collection Objects

Setting Object.hide_viewport , Object.hide_select or Object.hide_render kicks off a rebuild of the Collection caches, which derails any in-progress iteration over Collection.all_objects .

Do not:

`\text
### `all_objects` is an iterator. Using it directly while performing operations on its members that will update
### the memory accessed by the `all_objects` iterator will lead to invalid memory accesses and crashes.
for object in bpy.data.collections["Collection"].all_objects:
object.hide_viewport = True
`

Do:

`\text
### `all_objects[:]` is an independent list generated from the iterator. As long as no objects are deleted,
### its content will remain valid even if the data accessed by the `all_objects` iterator is modified.
for object in bpy.data.collections["Collection"].all_objects[:]:
object.hide_viewport = True
`

#### Data-Blocks Renaming During Iteration

Whenever a data-block reached through bpy.data has its name set, the collection re-sorts. So any loop walking data such as bpy.data.objects that also assigns names must grab every item from the iterator up front (usually by turning it into a list or tuple), or it risks skipping some objects and visiting others more than once.

### sys.exit

Certain Python modules call sys.exit() on their own when something goes wrong. It's not common, but it's worth knowing about, because sys.exit() shuts Blender down at once and can look as if Blender simply crashed.

The argparse module, for one, prints an error and exits when handed invalid arguments.

One crude debugging trick: assign sys.exit = None , then see which Python line is the one quitting. You could equally replace sys.exit with a function of your own, though manipulating Python this way counts as bad practice.

## Modes and Mesh Access

### Modes and Mesh Access

Working with mesh data, you can run into a script that misbehaves under Edit-Mode. The cause is that Edit-Mode keeps its own copy of the data, which only gets written back into the mesh when you leave Edit-Mode.

Take a common case: with the user in Edit-Mode, an exporter gets at the mesh via obj.data (a bpy.types.Mesh) — the data is there, but it's drifted out of sync with the live edit mesh.

When you hit this, your options are…

- Leave Edit-Mode first, then run the tool.

- Force the mesh to sync up with a call to bmesh.types.BMesh.to_mesh().

- Rework the script so it operates on the edit-mode data straight away, see: bmesh.from_edit_mesh().

- Flag the context as wrong, permitting the script only when outside Edit-Mode.

### N-Gons and Tessellation

N-gons have been supported since 2.63, which adds a wrinkle, because in certain situations (some exporters, say) you still need triangles.

Faces can now be reached three ways:

- bpy.types.MeshPolygon –
these days the structure storing faces in Object-Mode
(its accessor is mesh.polygons , not the old mesh.faces ).

- bpy.types.MeshLoopTriangle –
the product of tessellating polygons into triangles
(its accessor is mesh.loop_triangles ).

- bmesh.types.BMFace –
how the faces show up while in Edit-Mode.

In the documentation that follows, the three will be named polygons, loop triangles and BMesh-faces, in that order.

Faces carrying five or more sides are called ngons .

### Support Overview

| Usage | bpy.types.MeshPolygon | bpy.types.MeshLoopTriangle | bmesh.types.BMFace |
| Import/Create | Poor (inflexible) | Unusable (read-only) . | Best |
| Manipulate | Poor (inflexible) | Unusable (read-only) . | Best |
| Export/Output | Good (n-gon support) | Good (When n-gons cannot be used) | Good (n-gons, extra memory overhead) |

Note

The bmesh API stands entirely apart from bpy ; which one you pick usually comes down to how much editing you need, not merely a different doorway to the same faces.

### Creating

Faces can be built from any of the three data types:

- Polygons make faces with the least overhead, but the structure is stiff and unbending — every vertex and face has to be ready so you can create them all in one shot. It's made fiddlier still by the fact that a polygon doesn't carry its own vertices; instead it points at an index and a length in bpy.types.Mesh.loops , itself a fixed array.

- BMesh-faces are likely the easiest route to creating faces in new scripts: faces go in one by one, and the API is designed around mesh editing. Although bmesh.types.BMesh uses up more memory, processing just one mesh at any given moment keeps that under control.

### Editing

Of the three, editing is where they differ the most.

- Polygons are quite restricted for editing; swapping materials and toggling options like smooth works, but for anything beyond that they're too rigid and exist purely for storage.

- Loop-triangles shouldn't be used to edit geometry, since doing so tessellates any existing n-gons.

- BMesh-faces are comfortably the best choice for reshaping geometry.

### Exporting

All three can serve for export; the pick mostly turns on whether the destination format handles n-gons.

- Polygons give the most direct, efficient export, provided they map cleanly into the target format.

- Loop-triangles suit exporting to formats that lack n-gon support — in fact that's the one place their use is recommended.

- BMesh-Faces can export too, but may be overkill where polygons would do, since BMesh carries some overhead for not being the native storage in Object-Mode.

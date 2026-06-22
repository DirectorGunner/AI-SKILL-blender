# Quickstart

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Quickstart

For the most part this API has settled, though a handful of areas continue to receive additions and refinements.

What the Blender Python API lets you do:

- Reach into any data the interface touches (Scenes, Meshes, Particles, and so on).

- Adjust user preferences, keymaps, and themes.

- Invoke tools while supplying your own parameters.

- Build interface components like menus, headers, and panels.

- Author brand-new tools.

- Author tools that respond interactively.

- Add rendering engines that hook into Blender.

- Watch for changes on data and its properties.

- Register additional settings onto Blender's existing data.

- Render directly into the 3D Viewport from Python.

Features that aren't available (yet):

- Defining entirely new space types.

- Attaching custom properties to absolutely every type.

### Before Starting

The aim here is to get you oriented with Blender's Python API rather than to walk through every subject exhaustively.

A short rundown of things worth knowing in advance:

- Turn on Developer Extra and Python Tooltips.

- The Python Console shines for trying out single lines; its autocompletion lets you probe the API on the fly.

- Hovering over a button shows its Python attribute and operator name (once the option above is on).

- Right-clicking a button to open its context menu jumps straight to the matching page in this documentation (once enabled, as noted above).

- The text editor's template menu is a good source of ready-made Python examples.

- For a deeper look at the scripts shipped alongside Blender, check:

- scripts/startup/bl_ui for the user interface.

- scripts/startup/bl_operators for operators.

Where exactly these sit varies by platform; consult the directory layout docs.

### Running Scripts

When it comes to running Python, two routes dominate: the bundled text editor, or typing straight into the console. As space types, the editor and the console alike can be picked from the header. And rather than hand-arrange spaces for Python work yourself, just reach for the Scripting workspace over in the Topbar tabs.

In the text editor you can load .py files or drop them in from the clipboard, then try them out with Run Script. People generally lean on the Python Console for short snippets and quick experiments where the feedback is instant, though you can also paste whole scripts into it. Blender can run scripts from the command line as well, but that's not something you need in order to pick up scripting inside Blender.

### Key Concepts

### Data Access

#### Accessing Data-Blocks

Reaching Blender's data through the Python API mirrors how the animation system or the interface does it; the upshot is that whatever a button can change, Python can change too. To get at the data in the blend-file currently open, go through the bpy.data module. That gives you a way into library data, such as:

`\text
>>> bpy.data.objects

`

`\text
>>> bpy.data.scenes

`

`\text
>>> bpy.data.materials

`

#### Accessing Collections

You'll see that collection members can be reached either by index or by string. That's unlike Python dictionaries, where only one applies; here both work, though keep in mind a member's index can shift while Blender is running.

`\text
>>> list(bpy.data.objects)
[bpy.data.objects["Cube"], bpy.data.objects["Plane"]]
`

`\text
>>> bpy.data.objects['Cube']
bpy.data.objects["Cube"]
`

`\text
>>> bpy.data.objects[0]
bpy.data.objects["Cube"]
`

#### Accessing Attributes

After you've got hold of a data-block (a material, object, collection, and the like), reading or setting its attributes feels much like flipping a setting in the graphical interface. Indeed, each button's tooltip spells out the Python attribute, which is handy for tracking down which setting a script should touch.

`\text
>>> bpy.data.objects[0].name
'Camera'
`

`\text
>>> bpy.data.scenes["Scene"]
bpy.data.scenes['Scene']
`

`\text
>>> bpy.data.materials.new("MyMaterial")
bpy.data.materials['MyMaterial']
`

When you're figuring out which data to reach for, the Python Console (a space type of its own) comes in handy. With auto-complete on tap, it's a quick route to browsing the data in your file.

A sample data path that the console makes easy to discover:

`\text
>>> bpy.data.scenes[0].render.resolution_percentage
100
>>> bpy.data.scenes[0].objects["Torus"].data.vertices[0].co.x
1.0
`

#### Data Creation/Removal

Coming from other Python APIs, it might catch you off guard that you can't spin up fresh data-blocks in the bpy API by calling the class itself:

`\text
>>> bpy.types.Mesh()
Traceback (most recent call last):
File " ", line 1, in
TypeError: bpy_struct.__new__(type): expected a single argument
`

That restriction is deliberate. Blender's Python API won't let you make Blender data that lives outside the central Blender database (reached via bpy.data), since Blender itself looks after that data across save, load, undo, append, and so on.

Adding and removing data happens through methods on the bpy.data collections, for instance:

`\text
>>> mesh = bpy.data.meshes.new(name="MyMesh")
>>> print(mesh)

`

`\text
>>> bpy.data.meshes.remove(mesh)
`

#### Custom Properties

From Python you can attach properties to any data-block carrying an ID (data that gets linked in and shows up under bpy.data). You're free to choose your own property names when assigning; they spring into existence as required, or replace an existing one of the same name.

Such data rides along in the blend-file and travels with copied objects, for example:

`\text
bpy.context.object["MyOwnProperty"] = 42

if "SomeProp" in bpy.context.object:
print("Property found")

### Use the get function like a Python dictionary
### which can have a fallback value.
value = bpy.data.scenes["Scene"].get("test_prop", "fallback value")

### Dictionaries can be assigned as long as they only use basic types.
collection = bpy.data.collections.new("MyTestCollection")
collection["MySettings"] = {"foo": 10, "bar": "spam", "baz": {}}

del collection["MySettings"]
`

Keep in mind that what you store here is limited to the elementary Python types:

- the scalars int, float and string;

- an array whose entries are all ints, or all floats;

- a dictionary — its keys have to be strings, and its values likewise must stay within these basic types.

Their reach extends beyond Python itself: such properties can feed animation curves or turn up inside driver paths.

For the set of types that allow custom properties, refer to: types supporting custom properties.

### Context

Pulling data straight by name or as a list has its place, yet far more often you'll want to act on whatever the user has selected. That's where context comes in: it's always reachable through bpy.context and hands you the active object, scene, tool settings, plus a wide range of other attributes.

A few typical situations:

`\text
>>> bpy.context.object
>>> bpy.context.selected_objects
>>> bpy.context.visible_bones
`

Keep in mind context is read-only, so you can't assign to these values straight away. Changing them instead happens by invoking API functions or by reaching through the data API.

That's why bpy.context.active_object = obj throws an error, whereas bpy.context.view_layer.objects.active = obj behaves just fine.

Which context attributes exist shifts according to where you read them from. Members available in the 3D Viewport differ from those in the Python Console, so be mindful of the user's current state when you pull a context attribute.

See bpy.context API reference.

### Operators (Tools)

Operators are the tools a user normally triggers from buttons, menu entries, or shortcut keys. They look like tools from the user's side, but Python can fire them off with custom settings by way of the bpy.ops module.

Examples:

`\text
>>> bpy.ops.mesh.flip_normals()
{'FINISHED'}
>>> bpy.ops.mesh.hide(unselected=False)
{'FINISHED'}
>>> bpy.ops.object.transform_apply()
{'FINISHED'}
`

Tip

The Operator Cheat Sheet lays out every operator alongside its default values in Python form, together with the auto-generated docs. It's a handy way to survey the full set of Blender operators at a glance.

#### Operator Poll()

A lot of operators carry a "poll" function that verifies the cursor sits in a suitable area or the object is in the right mode (Edit Mode, Weight Paint Mode, and similar). Should that poll function fail while called from Python, an exception gets thrown.

For instance, running bpy.ops.view3d.render_border() from the console produces this error:

`\text
RuntimeError: Operator bpy.ops.view3d.render_border.poll() failed, context is incorrect
`

Here the context needs to be the 3D Viewport together with an active camera.

Rather than wrapping every operator call in a try-except block, you can first invoke the operator's own poll() function to find out whether it's able to run in the present context.

`\text
if bpy.ops.view3d.render_border.poll():
bpy.ops.view3d.render_border()
`

### Integration

Python scripts have several routes for plugging into Blender:

- by defining a render engine;

- by defining operators;

- by laying out panels, headers, and menus;

- by adding fresh buttons onto panels, headers, and menus that already exist.

However you go about it, in Python the mechanism is the same: you author a class that subclasses one of the types Blender already provides.

### Example Operator

`\text
import bpy

def main(context):
for ob in context.scene.objects:
print(ob)

class SimpleOperator(bpy.types.Operator):
"""Tooltip"""
bl_idname = "object.simple_operator"
bl_label = "Simple Object Operator"

@classmethod
def poll(cls, context):
return context.active_object is not None

def execute(self, context):
main(context)
return {'FINISHED'}

def menu_func(self, context):
self.layout.operator(SimpleOperator.bl_idname, text=SimpleOperator.bl_label)

### Register and add to the "object" menu (required to also use F3 search "Simple Object Operator" for quick access).
def register():
bpy.utils.register_class(SimpleOperator)
bpy.types.`VIEW3D_MT`_object.append(menu_func)

def unregister():
bpy.utils.unregister_class(SimpleOperator)
bpy.types.`VIEW3D_MT`_object.remove(menu_func)

if __name__ == "__main__":
register()

### Test call.
bpy.ops.object.simple_operator()
`

Run this script and Blender then knows about SimpleOperator, which from there you can reach via Operator Search or drop onto the toolbar.

To run the script:

- Start Blender and switch to the Scripting workspace.

- Click the New button in the text editor to create a new text data-block.

- Copy the code from above and paste it into the text editor.

- Click on the Run Script button.

- Move your cursor into the 3D Viewport, open the Operator Search menu, and type "Simple".

- Click on the "Simple Operator" item found in search.

See also

Those class members carrying the bl_ prefix have their documentation in the API reference under bpy.types.Operator.

Note

Whatever the main function prints lands in the terminal; to actually see it, make sure you're running with a terminal open.

### Example Panel

Like operators, panels get registered as a class. Note the additional bl_ variables, which pin down the context where the panel appears.

`\text
import bpy

class HelloWorldPanel(bpy.types.Panel):
"""Creates a Panel in the Object properties window"""
bl_label = "Hello World Panel"
bl_idname = "`OBJECT_PT`_hello"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"

def draw(self, context):
layout = self.layout

obj = context.object

row = layout.row()
row.label(text="Hello world!", icon='`WORLD_DATA`')

row = layout.row()
row.label(text="Active object is: " + obj.name)
row = layout.row()
row.prop(obj, "name")

row = layout.row()
row.operator("mesh.primitive_cube_add")

def register():
bpy.utils.register_class(HelloWorldPanel)

def unregister():
bpy.utils.unregister_class(HelloWorldPanel)

if __name__ == "__main__":
register()
`

To run the script:

- Start Blender and switch to the Scripting workspace.

- Click the New button in the text editor to create a new text data-block.

- Copy the code from above and paste it into the text editor.

- Click on the Run Script button.

To view the results:

- Select the default cube.

- Click on the Object properties icon in the buttons panel (far right; appears as a tiny cube).

- Scroll down to see a panel named "Hello World Panel".

- Changing the object name also updates Hello World Panel's name: field.

Notice how the rows are arranged and how the label and properties get laid out by the code.

See also

bpy.types.Panel

### Types

Blender brings its own collection of Python types into play while also relying on Python's built-in ones. You can divide Blender's Python API into three buckets.

### Native Types

In the trivial cases, dressing up a bare number or string as a custom type would only get in the way, so what you get back is just an everyday native value.

- Blender float, int, boolean -> float, int, boolean

- Blender enumerator -> string

`\text
>>> C.object.rotation_mode = '`AXIS_ANGLE`'
`

- Blender enumerator (multiple) -> set of strings

`\text
### Setting multiple snap targets.
bpy.context.scene.tool_settings.snap_elements_base = {'VERTEX', 'EDGE'}

### Passing as an operator argument for report types.
self.report({'WARNING', 'INFO'}, "Some message!")
`

### Internal Types

bpy.types.bpy_struct backs Blender's data-blocks and collections, plus any data that carries its own attributes such as collections, meshes, bones, scenes, and the rest.

Two principal types wrap Blender's data: one stands in for data-blocks (referred to internally as bpy_struct), and the other for properties.

`\text
>>> bpy.context.object
bpy.data.objects['Cube']
`

`\text
>>> C.scene.objects
bpy.data.scenes['Scene'].objects
`

Because these types point back at Blender's own data, any edit you make to them shows up at once.

### Mathutils Types

The mathutils module exposes vectors, quaternions, Euler angles, matrices, and color types. Certain attributes, among them bpy.types.Object.location, bpy.types.PoseBone.rotation_euler, and bpy.types.View3DCursor.location, are surfaced as these dedicated math types, which combine and transform in many handy ways.

A sample of multiplying a matrix by a vector:

`\text
bpy.context.object.matrix_world @ bpy.context.object.data.vertices[0].co
`

Note

mathutils types hold onto a reference back to Blender's internal data, so changes flow back to it.

Example:

`\text
### Modifies the Z axis in place.
bpy.context.object.location.z += 2.0

### Location variable holds a reference to the object too.
location = bpy.context.object.location
location *= 2.0

### Copying the value drops the reference so the value can be passed to
### functions and modified without unwanted side effects.
location = bpy.context.object.location.copy()
`

### Animation

Python gives you two avenues for adding keyframes.

One keys the properties straight away, much as a user clicking the keyframe button would. The other has you assemble the curves and keyframe data by hand and then aim the path at the property. An example of each follows below, and in either case what gets keyed is the Z axis of whatever object is active.

Simple example:

`\text
obj = bpy.context.object
obj.location[2] = 0.0
obj.keyframe_insert(data_path="location", frame=10.0, index=2)
obj.location[2] = 1.0
obj.keyframe_insert(data_path="location", frame=20.0, index=2)
`

Using low-level functions:

`\text
obj = bpy.context.object

### Create the action, with a slot for the object, a layer, and a keyframe strip:
action = bpy.data.actions.new(name="MyAction")
slot = action.slots.new(obj.id_type, obj.name)
strip = action.layers.new("MyLayer").strips.new(type='KEYFRAME')

### Create a channelbag to hold the F-Curves for the slot:
channelbag = strip.channelbag(slot, ensure=True)

### Create the F-Curve with two keyframes:
fcu_z = channelbag.fcurves.new(data_path="location", index=2)
fcu_z.keyframe_points.add(2)
fcu_z.keyframe_points[0].co = 10.0, 0.0
fcu_z.keyframe_points[1].co = 20.0, 1.0

### Assign the action and the slot to the object:
adt = obj.animation_data_create()
adt.action = action
adt.action_slot = slot
`

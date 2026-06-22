# Api Reference Usage, Best Practice

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: API Reference Usage; Best Practice.

## API Reference Usage

### API Reference Usage

The web of interconnected data types in Blender ships with an auto-generated reference API. That reference usually holds whatever a script author needs, yet newcomers tend to find it awkward to navigate. The aim of this page is to make the reference API approachable.

### Reference API Scope

What the reference API documents is bpy.types — the types you reach either through bpy.context (the user's current context) or through bpy.data (the data inside the blend-file).

It does not extend to modules like bmesh and aud, since those sit outside Blender's data API; nothing on this page carries over to them.

### Data Access

By far the usual reason to open the reference API is to work out the route to some piece of data in the blend-file. It pays to first understand ID data-blocks, because a great many properties are described in relation to them.

### ID Data

At the top level, data in Blender is held inside ID data-blocks. The interface keeps this mostly invisible, yet once you move to development it's something you have to know about. Texture, Image, Armature, World, Workspace, Mesh, Object, Collection and Scene are all examples of ID data types; for the exhaustive set, look at what subclasses bpy.types.ID.

Traits common to ID data-blocks:

- Because IDs belong to the blend-file, opening a different blend-file swaps in a whole fresh set of them.

- From Python they are reached through bpy.data.* .

- Every data-block carries a unique .name attribute that the interface shows.

- An ID stores its animation under .animation_data .

- Only IDs may be linked across blend-files.

- Python can create, duplicate and delete IDs.

- A dedicated garbage-collection mechanism drops IDs that go unused when you save.

- Where one data-block points at some outside data, that referenced thing is generally an ID data-block too.

### Simple Data Access

Here a short Python script nudges an object's position. The starting task is to track down where that data actually lives.

Locate the control in the interface at Properties editor -> Object -> Transform -> Location . Opening the button's context menu and choosing Online Python Reference jumps you to:
bpy.types.Object.location.
Such reference pages frequently say little beyond what the tooltip already told you, though a number of them carry examples (usually near the top). The payoff is knowing you reach it through .location and that it holds three floats in an array.

What remains is finding the entry point for objects: scroll to the references section at the foot of the page. Objects show up in plenty of references, but among the most frequent ways in is through the context. It's tempting to feel swamped here, given how widely Object is referenced — across modifiers, functions, textures and constraints. Still, when your goal is whatever the user has currently selected, the bpy.context references are normally all you need to consult.

Even there the list runs fairly long, and skimming it reveals that most entries are tied to a particular mode. Suppose your tool only operates in Weight Paint Mode — then weight_paint_object is the right pick. To instead grab whatever the user selected last, hunt for the active members. Reaching a single active member that follows the user's selection is a standard Blender pattern: see active_bone , active_pose_bone , active_node , etc., and for this scenario active_object fits.

That gives you everything required to reach the active object's location.

`\text
bpy.context.active_object.location
`

Enter that in the Python console to see what comes back. Objects also commonly appear in the reference under bpy.types.BlendData.objects.

Note

You won't see it written as bpy.data.objects in the docs;
the reason is that bpy.data is one instance of bpy.types.BlendData ,
so that class is where the documentation directs you.

Since bpy.data.objects holds a collection, you have to index into one of its members:

`\text
bpy.data.objects["Cube"].location
`

### Nested Properties

That first example stayed simple, because location belongs to Object and the context hands it to you directly.

A few trickier cases follow:

`\text
### Access the number of samples for the Cycles render engine.
bpy.context.scene.cycles.samples

### Access to the current weight paint brush size.
bpy.context.tool_settings.weight_paint.brush.size

### Check if the window is full-screen.
bpy.context.window.screen.show_fullscreen
`

So in places the data you're after sits buried, and reaching it means stepping through several layers of indirection. The property layout mirrors how Blender stores things internally in its C code — often sensible, yet not always matching the mental model you build from using Blender. Picking that up takes a while; the upside is it teaches you how Blender's data interlocks, which is worth understanding when you script.

Early on the recurring snag is simply not knowing how to reach a given piece of data. A handful of approaches help:

- Lean on the Python console's auto-complete to poke at properties.
This is somewhat unreliable but lets you read property values and set them to watch the effect interactively.

- Copy the data path straight out of the user interface.
Covered below under Copy Data Path.

- Walk the references in the documentation.
Covered below under Indirect Data Access.

### Copy Data Path

The tooltip already shows the Python string for a property, on the line beginning Python: ... . That spares you a trip to the API references just to learn the access path. The context menu also carries a copy data-path tool, which returns the route from a bpy.types.ID data-block down to its property.

For a worked example you'll grab the path to the Levels setting on the Subdivision Surface modifier. From the default scene open the Modifiers tab, then give the cube a Subdivision Surface modifier. Hover over the button marked Levels Viewport . Its tooltip reads bpy.types.SubsurfModifier.levels , yet what you're after is the route from the object to that property.

Note that what gets copied omits the bpy.data.collections["name"]. prefix. The reasoning: collection look-ups on every access aren't the norm, and most of the time you'll go through the context rather than addressing each bpy.types.ID instance by its name.

Enter the ID path bpy.context.active_object into a Python console. Keep the dot at the end and hold off on running it.

Now from the button's context menu pick Copy Data Path , then paste what you get into the console:

`\text
bpy.context.active_object.modifiers["Subdivision"].levels
`

Hit Return and the current value 1 comes back. Next set it to 2:

`\text
bpy.context.active_object.modifiers["Subdivision"].levels = 2
`

The change shows up at once both in the Subdivision Surface modifier's UI and on the cube itself.

### Indirect Data Access

This tougher example walks through reaching the texture on the active sculpt brush — say you want to tweak its contrast from Python.

- Open the default scene and switch on Sculpt Mode from the 3D Viewport header.

- In the Sidebar open the Texture subpanel under Brush Settings and add a fresh texture.
You'll notice the texture data-block menu offers few helpful links (check the tooltips to confirm).

- Since contrast isn't surfaced in the Sidebar, look at the texture through the
Properties Editor.

- Right-click the contrast field for its context menu and choose Online Python Reference .
That lands you on bpy.types.Texture.contrast , confirming contrast belongs to texture.

- To learn how the brush reaches the texture, look over the reference list down at the page's foot.
That list can run long, and identifying the correct entry sometimes takes a bit of guesswork, but in this instance it proves to be tool_settings.sculpt.brush.texture .

- You now have bpy.data.brushes["BrushName"].texture as the way to the texture, though indexing the brush by name is rarely what you want — the active brush is. So the following step is to check the references for where brushes come from.

At this point the Python console lets you assemble the chain of nested properties down to the brush texture's contrast:
Context ‣ Tool Settings ‣ Sculpt ‣ Brush ‣ Texture ‣ Contrast .

Because each step hands you its attribute, you can stitch the data path together in the Python console:

`\text
bpy.context.tool_settings.sculpt.brush.texture.contrast
`

Or reach the brush directly:

`\text
bpy.data.textures["Texture"].contrast
`

For a user-facing tool you'll generally route through bpy.context, since people expect the tool to act on whatever they've selected. Automation leans the other way toward bpy.data, because there you want to address and edit specific data no matter where the user's view happens to be.

### Operators

The bulk of Blender's buttons and hotkeys fire an operator, and those operators are exposed to Python through bpy.ops as well.

For the Python form, hover the button and read its tooltip, e.g Python: bpy.ops.render.render() . When no tooltip shows or the Python: line is absent, that button isn't backed by an operator and Python can't reach it.

To grab it for a script, hover the button and hit Ctrl - C , which copies it onto the clipboard. From the same button's context menu there's Online Python Reference too; that mostly enumerates the arguments and their defaults, and for Python-written operators it also names the file and line — useful if you want a look at the source.

Note

A Python call to certain operators won't accomplish anything useful;
the using operators section goes into this.

### Info Editor

Operators you run get logged by Blender and shown in the Info editor. Open the Scripting workspace that comes with Blender by default to view that log. Carry out a few actions and watch them appear — deleting a vertex, for instance.

Select any entry and copy it via Ctrl - C , usually so you can paste it into the Python console or text editor.

Note

Not every operator is recorded for display;
re-running a view zoom, say, isn't worth repeating, so it's left out.

To surface every operator that fires, see Show All Operators.

## Best Practice

### Best Practice

Python is an easy language for a beginning developer to get productive in when writing scripts, but along the way it's just as easy to absorb sloppy habits or end up with scripts other people struggle to follow. That's perfectly fine for your private work; once you want to collaborate or get your code bundled with Blender, though, there are conventions we'd recommend.

### Style Conventions

For Blender Python work we've settled on Python's recommended style guide, which keeps our own scripts from drifting into clashing styles and makes pulling in Python from elsewhere smoother. Following the same guide in your scripts pays off if you later decide to contribute them to Blender.

That guide goes by the name pep8,
and what follows is a short rundown of its rules:

- Class names written in camel caps: MyClass

- Module names kept lower case with words joined by underscores: my_module

- Four-space indentation, never tabs

- Operators padded with spaces: 1 + 1 , not 1+1

- Imports always explicit — no wildcard importing *

- One statement per line: instead of if val: body on a single line, break it across two.

On top of pep8 we layer a few extra conventions for Blender Python scripts:

- Wrap enums in single quotes and ordinary strings in double quotes.

Technically both are strings, but in our internal API an enum is a distinct item drawn from a fixed set, e.g:

`\text
bpy.context.scene.render.image_settings.file_format = 'PNG'
bpy.context.scene.render.filepath = "//render_out"
`

- pep8 additionally caps lines at 79 characters; we've judged that too tight, so we leave it optional on a per-script basis.

### User Interface Layout

A few things worth bearing in mind as you write UI layouts:

The layout code stays straightforward. Layout declarations exist so you can throw together a respectable arrangement with little fuss. The rule of thumb: if your layout declaration needs more code than the properties it's arranging, something's gone wrong.

Example layouts:

layout()
Top-to-bottom stacking is what the plain layout gives you.

`\text
layout.prop()
layout.prop()
`

layout.row()
When two or more properties should share a single line, that's the job for row().

`\text
row = layout.row()
row.prop()
row.prop()
`

layout.column()
When properties should run down a column, that's the job for column().

`\text
col = layout.column()
col.prop()
col.prop()
`

layout.split()
This is your tool for richer arrangements — for instance, splitting the layout to sit two column() layouts next to one another. Putting two properties on one line isn't a reason to split; row() handles that.

`\text
split = layout.split()

col = split.column()
col.prop()
col.prop()

col = split.column()
col.prop()
col.prop()
`

Declaration names:

When you declare layouts, try to keep to this set of variable names:

row :

names a row() layout

col :

names a column() layout

split :

names a split() layout

flow :

names a column_flow() layout

sub :

names a nested layout (such as a column placed inside another column)

### Script Efficiency

### List Manipulation (General Python Tips)

#### Searching for List Items

Python ships a few convenient list functions that spare you from scanning the list by hand. Even though you aren't writing the loop yourself, Python still is — so stay mindful of calls that drag your script down by walking the whole list.

`\text
my_list.count(list_item)
my_list.index(list_item)
my_list.remove(list_item)
if list_item in my_list: ...
`

#### Modifying Lists

Adding to or removing from a Python list gets slower once the list's length changes, and worse near the front, because every element past the edit point has to shift one slot up or down.

For appending at the end, your fastest options are my_list.append(list_item) or my_list.extend(some_list) ; to discard the final element, reach for my_list.pop() or del my_list[-1] .

If you instead need to work by index, my_list.insert(index, list_item) adds and list.pop(index) removes — but expect both to run more slowly.

At times it's quicker — though heavier on memory — to simply rebuild the list outright. Take stripping every triangular polygon from a list. Rather than:

`\text
polygons = mesh.polygons[:] # Make a list copy of the meshes polygons.
p_idx = len(polygons) # Loop backwards
while p_idx: # While the value is not 0.
p_idx -= 1

if len(polygons[p_idx].vertices) == 3:
polygons.pop(p_idx) # Remove the triangle.
`

A list comprehension builds the new list faster:

`\text
polygons = [p for p in mesh.polygons if len(p.vertices) != 3]
`

#### Adding List Items

When you've got one list to merge into another, instead of:

`\text
for l in some_list:
my_list.append(l)
`

Use:

`\text
my_list.extend([a, b, c...])
`

Keep in mind insert is there for when you need it, yet it lags append, particularly when you insert near the front of a long list. The snippet below is a thoroughly inefficient way to build a reversed list:

`\text
reverse_list = []
for list_item in some_list:
reverse_list.insert(0, list_item)
`

Python offers tidier ways to reverse a list via slicing, though it's worth timing before you lean on it heavily:

`\text
some_reversed_list = some_list[::-1]
`

#### Removing List Items

Prefer my_list.pop(index) over my_list.remove(list_item) . That does mean having the item's index on hand, but it's quicker since remove() has to search the list. Here's how to clear items inside a single loop, taking the last ones first, which (as noted above) is faster:

`\text
list_index = len(my_list)

while list_index:
list_index -= 1
if my_list[list_index].some_test_attribute == 1:
my_list.pop(list_index)
`

The next snippet is a fast removal trick, suitable wherever you can shuffle the list order without breaking what the script does. It swaps two entries so the one you're dropping always ends up last:

`\text
pop_index = 5

### Swap so the pop_index is last.
my_list[-1], my_list[pop_index] = my_list[pop_index], my_list[-1]

### Remove last item (pop_index).
my_list.pop()
`

Across a big list with many items to clear, this can buy you a solid speed-up.

#### Avoid Copying Lists

Handing a list or dictionary to a function and letting it edit the thing in place beats returning a brand-new one, since that way Python skips copying the list in memory.

A function that edits a list in place runs leaner than one that spins up a fresh list. The pattern below is generally slower, so save it for the cases where leaving the original untouched genuinely matters:

`\text
>>> my_list = some_list_func(my_list)
`

This one is generally quicker, with no reassignment and no duplicated list:

`\text
>>> some_list_func(vec)
`

Note too that handing over a sliced list copies that list into Python memory:

`\text
>>> foobar(my_list[:])
`

Where my_list runs to tens of thousands of entries, a copy like that could swallow a good deal of extra memory.

### Writing Strings to a File — General Python

Below are three ways to fuse several strings into one before writing. The same lessons carry over to anywhere your code does heavy string joining:

String concatenation
The slowest of the bunch — steer clear where you can, above all when writing data inside a loop.

`\text
>>> file.write(str1 + " " + str2 + " " + str3 + "\n")
`

String formatting
Reach for this when you're emitting string data built from floats and ints.

`\text
>>> file.write("%s %s %s\n" % (str1, str2, str3))
`

String joining
Use this to weld together a list of strings (which can be temporary). In the example below a space " " sits between them; other separators might be "" or ", ".

`\text
>>> file.write(" ".join((str1, str2, str3, "\n")))
`

For many strings join wins; string formatting is pretty quick too, and better when you're converting data types. Concatenation trails the field.

### Parsing Strings (Import/Exporting)

With so many file formats being ASCII, how you parse and export strings can swing your script's speed considerably.

A few options exist for parsing strings as you bring them into Blender.

#### Parsing Numbers

Prefer float(string) to eval(string) ; and where you know the value is an int, int(string) . float() copes with an int as well, but reading ints through int() is quicker.

#### Checking String Start/End

To test the front of a string for a keyword, rather than:

`\text
>>> if line[0:5] == "vert ": ...
`

Use:

`\text
>>> if line.startswith("vert "):
`

startswith() runs a touch faster (roughly 5%) and sidesteps a possible bug where the slice length doesn't line up with the string length.

my_string.endswith("foo_bar") works the same way for line endings.

When you can't be sure of the casing, fold it first with the lower() or upper() string method:

`\text
>>> if line.lower().startswith("vert ")
`

### Error Handling

A try statement is a handy shortcut around writing your own error checks. The catch is that try costs noticeably more than an if, since an exception has to be armed each pass, so keep try out of code that loops and runs heavily.

That said, there are situations where try beats testing up front whether something will error, so it's worth experimenting.

### Value Comparison

Python gives you two value comparisons, a == b and a is b . The distinction: == may invoke the object's own __eq__() method, whereas is tests identity — whether both names point at the very same object in memory.

When you already know you're comparing one shared value that's referenced from several places, is comes out faster.

### Time Your Code

As you build a script it's handy to time it so you catch any shift in performance, and that's easy to do:

`\text
import time
time_start = time.time()

### Do something...

print("My Script Finished: %.4f sec" % (time.time() - time_start))
`

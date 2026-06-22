# Contribute Documentation, File Paths String Encoding, Api Overview

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Contribute Documentation; File Paths & String Encoding; API Overview.

## Contribute Documentation

### Contribute Documentation

This page walks through contributing to the Blender Python API documentation — covering how to write examples, how to format the docs, and how to build them on your own machine.

### Setting Up Your Environment

### Prerequisites

A few things have to be in place before a build:

Blender Source Code
Pull down a clone of the Blender repository, working from the
official build instructions.

Python Environment (optional)
Get a Python virtual environment going.

### Installing Documentation Requirements

The usual route is to spin up a virtual environment and install whatever is listed in doc/python_api/requirements.txt . That said, Sphinx is the lone hard dependency, and you can grab it on its own:

`\text
pip install -r doc/python_api/requirements.txt
`

### Building the Documentation

With the requirements in place, you can go ahead and build the docs:

`\text
### From the Blender source root
make doc_py
`

When it's done, point your browser at doc/python_api/sphinx-out/index.html .

### Modifying API Documentation

Because the API docs are produced directly out of Blender's source, things like method signatures and class descriptions originate either in C/C++ files (via PyDoc_STRVAR ) or in plain Python doc-strings.

To revise an API class or method description:

- Track down the source file you need within the Blender repository.

- Find the doc-string you're after: in the Python C/API it sits within PyDoc_STRVAR(...) ,
while in a Python file it's just a regular doc-string.

- Make your edits in reStructuredText.

- Regenerate the pages by rebuilding the Python API docs with make doc_py .

### Adding Example Code Snippets

Examples carry a lot of weight in the API docs. Sitting above the reference for each class, function or module, they show people how the thing is actually used.

### Example File Naming Convention

Rather than inlining code-blocks inside the doc-string, examples can live as standalone script files. Drop a file that follows the naming rules below and it gets pulled in for you.

Such example files belong in doc/python_api/examples/ , where the filename decides what each one attaches to:

- A module is targeted by module.N.py (for instance gpu.0.py ).

- A class is targeted by module.ClassName.N.py (for instance bpy.types.Operator.0.py ).

- A method is targeted by module.ClassName.method.N.py (for instance bpy.types.Operator.invoke.0.py ).

- An attribute is targeted by module.ClassName.attribute.N.py (for instance bpy.types.Scene.frame_start.0.py ).

- A module member is targeted by module.member.N.py (for instance bpy.context.object.0.py ).

Multiple examples are allowed; their sequence is governed by N .

### Example File Structure

It's frequently useful to describe what a particular example is demonstrating. So that you can, the file's leading doc-string is extracted and displayed above the code, with its body rendered as reStructuredText.

Lay out each example file along these lines:

`\text
"""
Example Title
+++++++++++++

A description of what this example demonstrates.
This doc-string appears above the code in the documentation.

You can use **reStructuredText** formatting here, for example:

- *Italic* text with single asterisks
- **Bold** text with double asterisks
- ``inline code`` with double backticks
- :class:`bpy.types.Operator` to link to API classes
- Links to `external resources `__

.. note::

You can use this to highlight important information.

Everything after this doc-string is included as code.
"""
import bpy

### Example code goes here
print("This is an example")
`

#### Important Notes

- Triple double-quotes """ have to open the file; doc-strings using single quotes go unrecognized.

- For the title, underline the section header with + characters.

- Whatever follows the doc-string is treated as code in the documentation.

- Need more code-blocks separated by text? Add further files.

### Best Practices for Documentation

### Writing Good Examples

- Keep it simple : show a single concept per example.

- Make it runnable : the example ought to work as-is when pasted into the text editor or Python console.

- Use comments : annotate generously, writing as though the reader has never met the APIs or ideas on display.

### Style Guidelines

We're aiming for solid technical writing in the docs. For markup and conventions, lean on these style guides from the User Manual:

- Markup Guide

- Writing Guide

- reStructuredText Primer

### Testing Your Changes

Having added or revised documentation, rebuild it (see Building the Documentation) and keep an eye out for warnings — dead links, references that don't resolve, or formatting problems. Then load the generated HTML in a browser and verify it all renders as it should.

### Contributing Your Changes

With your documentation additions or improvements complete,
open a pull request by following
Blender's contribution guidelines.

## File Paths & String Encoding

### File Paths & String Encoding

### Relative File Paths

The relative paths Blender uses don't sit well with the standard Python modules such as os and sys . To a built-in Python function, the leading // that Blender treats as the blend-file's directory means nothing.

You'll typically hit this when exporting a material that carries associated image paths:

`\text
>>> bpy.path.abspath(image.filepath)
`

With Blender data drawn from linked libraries a snag appears: the path resolves relative to the library rather than to the blend-file currently open. If a data-block might originate in an external blend-file, supply the bpy.types.ID 's library argument.

`\text
>>> bpy.path.abspath(image.filepath, library=image.library)
`

That hands back an absolute path you can feed to native Python modules.

### Unicode Problems

Python handles a wide range of encodings, so nothing stops you from authoring a script in latin1 or iso-8859-15 .
See PEP 263.

For Blender's Python API, though, that's a complication, because a .blend file carries no explicit encoding. To keep the headache away from Python integration and script writers, we've ruled that every string inside a blend-file must be UTF-8 , and ASCII-compatible at that. The upshot: assigning a string in some other encoding to, say, an object name throws an error.

Paths are the exception, because you can't simply pretend non-UTF-8 paths won't show up on a user's filesystem. That means even innocent-looking expressions can raise errors, e.g:

`\text
>>> print(bpy.data.filepath)
UnicodeEncodeError: 'ascii' codec can't encode characters in position 10-21: ordinal not in range(128)
`

`\text
>>> bpy.context.object.name = bpy.data.filepath
Traceback (most recent call last):
File " ", line 1, in
TypeError: bpy_struct: item.attr= val: Object.name expected a string type, not str
`

There are a couple of ways to route around filesystem-encoding snags:

`\text
>>> print(repr(bpy.data.filepath))
`

`\text
>>> import os
>>> filepath_bytes = os.fsencode(bpy.data.filepath)
>>> filepath_utf8 = filepath_bytes.decode('utf-8', "replace")
>>> bpy.context.object.name = filepath_utf8
`

Encoding and decoding Unicode is a deep subject with thorough Python documentation; to keep things brief, here are a few suggestions about encoding trouble:

- Stick with UTF-8 throughout, and when the input's encoding is a mystery, convert it to UTF-8.

- Rather than slicing file paths around as raw strings, lean on the os.path functions.

- For path work, prefer os.fsencode() or os.fsdecode() over Python's built-in string decoding calls.

- When you need to print a path or surface it in the interface, run it through repr(path) first,
or use "%r" % path via string formatting.

Note

Now and then the tidiest move is to dodge string-encoding problems entirely and operate on bytes instead of Python strings; reading input as binary data is often the simpler path, though you'll still need a plan for any strings you mean to hand to Blender — an approach taken by some importers.

## API Overview

### API Overview

What this page sets out to do is explain how Python and Blender mesh together, touching on parts of the functionality that the API references and example scripts don't make obvious on their own.

### Python in Blender

Blender carries an embedded Python interpreter, loaded the moment Blender starts and kept alive for as long as Blender runs. That interpreter executes the scripts that draw the user interface and powers several of Blender's internal tools as well.

The embedded interpreter offers a standard Python environment, so code from ordinary tutorials on writing Python scripts runs under it too. Blender exposes its own Python modules — bpy and mathutils among them — to that interpreter, so a script can import them and reach Blender's data, classes and functions. Any script touching Blender data has to import the relevant modules to function.

Here's a small example that shifts a vertex belonging to an object named "Cube":

`\text
import bpy
bpy.data.objects["Cube"].data.vertices[0].co.x += 1.0
`

That edits Blender's internal data straight away. Run it in the interactive console and you'll watch the 3D Viewport refresh.

### The Default Environment

When you're writing your own scripts, it helps to know how Blender lays out its Python environment. Plenty of Python scripts ship with Blender and make good reference material, because they're written against the very same API that tool authors use. Scripts get put to work on all sorts of jobs: building the user interface, handling import/export, reshaping the scene, automating tasks, rolling your own tool set, and customization.

As it boots, Blender looks through scripts/startup/ for any Python modules there and imports each one. Where that folder actually lives will vary with your installation; the directory layout docs cover this.

### Script Loading

It may sound obvious, but it's worth flagging the gap between running a script directly and importing one as a module.

Extending Blender by running a script outright means the classes that script defines stay around inside Blender after it has finished. Used that way, getting back at those classes later — to unregister them, for instance — is harder than if you'd imported the script as a module. Import a script as a module and its class instances stay within the module, reachable again later by re-importing it.

For that reason it's preferable to steer clear of directly running scripts that extend Blender by registering classes.

Several routes let you run a script outright inside Blender:

- Open it in the text editor and hit Run Script .

- Type or paste it straight into the interactive console.

- Hand a Python file to Blender on the command line, e.g:

`\text
blender --python /home/me/my_script.py
`

And to load them as modules:

- The obvious one — issuing import some_module from the interactive console or the text editor.

- Open it as a text data-block and tick the Register option, so it loads alongside the blend-file.

- Drop it into one of the scripts/startup directories, from where it's imported automatically at startup.

- Build it into an add-on; once that add-on is enabled it comes in as a module.

### Add-ons

Some of what Blender does is best left optional. Alongside the scripts loaded at startup sit add-ons, which keep to their own directory scripts/addons , and which only load at startup once you've ticked them in the user preferences.

What sets an add-on apart from an ordinary built-in Python module comes down to one requirement: it has to declare a bl_info variable. Blender pulls its metadata from there — the author, the project link, the category, the name — and the add-on list under User Preferences uses bl_info to present each add-on's details. The bl_info dictionary is documented under Add-ons.

### Integration through Classes

Running scripts in the text editor is great for trying things out, but you'll want to extend Blender so your tools sit alongside the rest of its built-in functionality.

The Blender Python API permits integration for:

- bpy.types.Panel

- bpy.types.Menu

- bpy.types.Operator

- bpy.types.PropertyGroup

- bpy.types.KeyingSet

- bpy.types.RenderEngine

The shortness of that list is on purpose. More involved capabilities — shader nodes, new object types, mesh modifiers and the like — remain, for now, the province of C/C++.

To integrate with Python, Blender provides methods common across all types. It works by subclassing a Blender class in Python; that subclass then inherits the variables and functions its parent defines, all set up in advance to talk to Blender.

For example:

`\text
import bpy
class SimpleOperator(bpy.types.Operator):
bl_idname = "object.simple_operator"
bl_label = "Tool Name"

def execute(self, context):
print("Hello World")
return {'FINISHED'}

bpy.utils.register_class(SimpleOperator)
`

Notice first that the subclass it defines belongs to bpy.types — the norm for every class that integrates with Blender, and what lets registration distinguish an Operator from a Panel. The two class properties each begin with bl_ , a convention separating Blender's properties from ones of your own. After that is the execute function, which receives the operator instance plus the running context; no common prefix applies to functions. Last, register is called to take the class and load it into Blender. See Class Registration.

As for inheritance, Blender imposes no restriction on what styles of class inheritance you employ; when registering, the checks will consult whatever functions and attributes the parent classes define.

Class mix-in example:

`\text
import bpy
class BaseOperator:
def execute(self, context):
print("Hello World BaseClass")
return {'FINISHED'}

class SimpleOperator(bpy.types.Operator, BaseOperator):
bl_idname = "object.simple_operator"
bl_label = "Tool Name"

bpy.utils.register_class(SimpleOperator)
`

Note

An exception is modal operators, which hold their instance variable for as long as Blender runs; see the modal operator template.

So after a class has been registered, it falls to Blender to instantiate it and invoke its functions. Indeed you can't create instances of these classes from your script as most Python APIs would let you. Running an operator means going through the operator API instead, e.g:

`\text
import bpy
bpy.ops.object.simple_operator()
`

User interface classes are handed a context to draw in — buttons, window, file header, toolbar, and so on — and they're drawn whenever that area shows, so Python scripts never call them directly.

### Construction & Destruction

Notice that in the examples above the classes never define an __init__(self) function. As a rule you shouldn't need custom constructors or destructors, and they're not recommended.

A class instance's lifetime is typically very brief (see also the dedicated section); a panel, for one, gets a brand-new instance on every redraw. A few other types, such as bpy.types.Operator, are handled in an even more intricate way internally, which can spawn several instantiations for a single operator run.

There are a handful of cases where an __init__() does earn its keep, e.g. when subclassing a bpy.types.RenderEngine. When you do, the parent's matching function must always be called, or Blender's internal initialization won't run properly:

`\text
import bpy
class AwesomeRaytracer(bpy.types.RenderEngine):
def __init__(self, *args, **kwargs):
super().__init__(*args, **kwargs)
self.my_var = 42
...
`

Warning

Before any data on the object is touched, you have to invoke the Blender-defined parent constructor —
that applies to access from the __init__() functions of any other parent types too.

Warning

Since Blender 4.4, invoking the parent's __init__() function is mandatory. Go with the 'generic' signature, given that the only caller of these functions is usually Blender's own internal BPY code. Whatever arguments reach the constructor are wholly internal data and can change with the implementation.

Sadly, the error you get when the expected constructor goes uncalled can be rather cryptic and unhelpful. As a rule it complains that some (python) object couldn't be built:

MemoryError: couldn't create bpy_struct object

For Operators the wording runs more like:

RuntimeError: could not create instance of <`OPERATOR_OT`_identifier> to call callback function execute

Note

With complex or multiple inheritance in play, super() can come up short — the Blender-defined parent may not sit first in the MRO. The safer approach is then to invoke that Blender-defined parent's constructor by name, ahead of every other. As an illustration:

`\text
import bpy
class FancyRaytracer(AwesomeRaytracer, bpy.types.RenderEngine):
def __init__(self, *args, **kwargs):
bpy.types.RenderEngine.__init__(self, *args, **kwargs)
AwesomeRaytracer.__init__(self, *args, **kwargs)
self.my_var = 42
...
`

Note

Writing a custom __new__() function is something we strongly advise against — it's untested and, for now, not treated as supported. Going ahead with it brings a genuine risk of crashes or of corrupting Blender's internal data. If you do write one regardless, it must accept the same pair of generic arguments (positional and keyword) and forward them to the parent's __new__() whenever it actually constructs a new object.

Note

Because of how CPython is implemented internally, Blender types defined in C++ presently neither declare nor make use of a __del__() destructor (otherwise known as tp_finalize() ). Since that function isn't there unless you write it yourself, a super().__del__() call from inside a subclass's __del__() trips this error: AttributeError: 'super' object has no attribute '__del__' . Should you genuinely need the MRO 'parent' destructor, your calling code has to confirm it exists beforehand — for example along these lines:
getattr(super(), "__del__", lambda self: None)(self)

### Registration

### Module Registration

A startup-loaded Blender module is required to provide both a register() and an unregister() function. Those two are the sole entry points Blender calls into your code; everything else is just a plain Python module.

Here's roughly what a minimal Blender Python module might look like:

`\text
import bpy

class SimpleOperator(bpy.types.Operator):
""" See example above """

def register():
bpy.utils.register_class(SimpleOperator)

def unregister():
bpy.utils.unregister_class(SimpleOperator)

if __name__ == "__main__":
register()
`

You'll usually see these at the foot of the script that registers the classes, sometimes adding menu items too. They're also usable for internal needs, like setting up data for your own tools — just bear in mind register won't run again when a fresh blend-file loads.

A register/unregister pair is precisely what lets add-ons be switched on and off, and scripts be reloaded, without a Blender restart. Were those register calls placed directly in the script body, they'd run at import time, blurring the line between importing a module and loading its classes into Blender. That gets messy as soon as one script pulls classes in from another module, since it becomes hard to keep track of what loads and when.

Those final two lines serve testing only:

`\text
if __name__ == "__main__":
register()
`

It allows the script to run directly in the text editor for testing your edits. Import the script as a module and that register() call stays quiet, because __main__ is reserved for running a file directly.

### Class Registration

When you register a class, its definition gets loaded into Blender and joins the functionality already there. Once loaded, it's reachable from bpy.types, where you address it by bl_idname rather than by the name the class originally had.

Note

A few class names can't be promised to be unique, and those are the exceptions here.
For them, reach for: bpy.types.Struct.bl_rna_get_subclass_py().

As it loads a class, Blender runs sanity checks confirming that every required property and function is present, that properties carry the right type, and that functions take the correct number of arguments.

Mostly this won't concern you, but if the class definition has a problem it'll surface at registration:

Give the function the arguments def execute(self, context, spam) and you'll trip an exception:

ValueError: expected Operator, SimpleOperator class "execute" function to have 2 args, found 3

Setting bl_idname = 1 throws:

TypeError: validating class error: Operator.bl_idname expected a string type, not int

#### Inter-Class Dependencies

As you customize Blender you may want to gather your own settings in one place; after all they'll have to live next to other scripts. Grouping them means defining classes, and for groups nested in groups, or collections inside groups, there's no dodging the question of registration/unregistration order.

Custom property groups are themselves classes that need registering.

Say, for example, you want a custom engine's material settings stored:

`\text
### Create new property:
### bpy.data.materials[0].my_custom_props.my_float
import bpy

class MyMaterialProps(bpy.types.PropertyGroup):
my_float: bpy.props.FloatProperty()

def register():
bpy.utils.register_class(MyMaterialProps)
bpy.types.Material.my_custom_props = bpy.props.PointerProperty(type=MyMaterialProps)

def unregister():
del bpy.types.Material.my_custom_props
bpy.utils.unregister_class(MyMaterialProps)

if __name__ == "__main__":
register()
`

Note

Registration of the class has to happen before any property uses it; skip that and you'll get an error:

ValueError: bpy_struct "Material" registration error: my_custom_props could not register

`\text
### Create new property group with a sub property:
### bpy.data.materials[0].my_custom_props.sub_group.my_float
import bpy

class MyMaterialSubProps(bpy.types.PropertyGroup):
my_float: bpy.props.FloatProperty()

class MyMaterialGroupProps(bpy.types.PropertyGroup):
sub_group: bpy.props.PointerProperty(type=MyMaterialSubProps)

def register():
bpy.utils.register_class(MyMaterialSubProps)
bpy.utils.register_class(MyMaterialGroupProps)
bpy.types.Material.my_custom_props = bpy.props.PointerProperty(type=MyMaterialGroupProps)

def unregister():
del bpy.types.Material.my_custom_props
bpy.utils.unregister_class(MyMaterialGroupProps)
bpy.utils.unregister_class(MyMaterialSubProps)

if __name__ == "__main__":
register()
`

Important

Register the innermost class ahead of the rest, and make sure unregister() mirrors register() in reverse.

#### Manipulating Classes

Properties can be tacked on and stripped off while Blender runs — normally during register or unregister, though for some special situations it can be handy to reshape types as the script executes.

For example:

`\text
### Add a new property to an existing type.
bpy.types.Object.my_float: bpy.props.FloatProperty()
### Remove it.
del bpy.types.Object.my_float
`

PropertyGroup subclasses of your own respond to the same technique just as well.

`\text
class MyPropGroup(bpy.types.PropertyGroup):
pass
MyPropGroup.my_float: bpy.props.FloatProperty()
`

Which amounts to the same thing as:

`\text
class MyPropGroup(bpy.types.PropertyGroup):
my_float: bpy.props.FloatProperty()
`

#### Dynamic Class Definition (Advanced)

At times what specifies some data sits outside Blender — the shader definitions of an external render engine, for example — and it can be worthwhile to register them as types and drop them again dynamically.

`\text
for i in range(10):
idname = "object.operator_{:d}".format(i)

def func(self, context):
print("Hello World", self.bl_idname)
return {'FINISHED'}

op_class = type(
"DynOp{:d}".format(i),
(bpy.types.Operator, ),
{"bl_idname": idname, "bl_label": "Test", "execute": func},
)
bpy.utils.register_class(op_class)
`

Note

Here the class is defined by calling type() .
In Python that's an alternative way to write a class, and it lends itself better to building classes on the fly.

Invoking the operators built just above:

`\text
>>> bpy.ops.object.operator_1()
Hello World `OBJECT_OT`_operator_1
{'FINISHED'}
`

`\text
>>> bpy.ops.object.operator_2()
Hello World `OBJECT_OT`_operator_2
{'FINISHED'}
`

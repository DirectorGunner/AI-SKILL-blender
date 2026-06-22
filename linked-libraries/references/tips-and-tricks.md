# Tips And Tricks

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Tips and Tricks

Below are a handful of pointers that may come in useful while you write scripts. A few are simply Python tricks you might not have considered applying to Blender; others are specific to Blender itself.

### Use the Terminal

It pays to keep a terminal handy when scripting in Python; not the embedded Python console, but the terminal application you use to launch Blender.

A terminal earns its keep in three main ways:

- You get to watch print() output as the script executes, which helps for inspecting debug info.

- The complete error traceback lands in the terminal, whereas Blender's interface won't always surface a report message for it (it depends on how the script was run).

- If a script drags on or you stumble into an infinite loop, hitting Ctrl - C in the terminal (Ctrl - Break on Windows) bails out of it early.

See also

Launching from the Command Line.

### Interface Tricks

### Access Operator Commands

As you may have spotted, the tooltip on menu entries and buttons carries the bpy.ops.[...] command that runs that button; a tidy (and not obvious) trick is that pressing Ctrl - C while hovering over any menu item or button copies that command onto the clipboard.

### Access Data Path

Working out the path from an ID data-block down to one of its settings isn't always straightforward, since the setting can be buried deep. A fast shortcut is to open the setting's context menu and pick Copy Data Path; when no full path can be produced, you just get the property name on its own.

Note

This relies on the same path-building machinery used for the animation paths behind bpy.types.FCurve.data_path and bpy.types.DriverTarget.data_path drivers.

### Show All Operators

Blender does record operators in the Info editor, but only those flagged with the REGISTER option, so the Info view doesn't get swamped with bpy.ops.view3d.smoothview and bpy.ops.view3d.zoom calls. For testing, though, it can help to watch every operator fire in a terminal; turn that on with the debug option, either by handing Blender the --debug-wm argument at startup or by flipping bpy.app.debug_wm to True while it's already running.

### Use an External Editor

Blender's text editor does fine for minor tweaks and dashing off tests, but it isn't fully featured, so on bigger projects you'll likely want a standalone editor or a Python IDE. You can edit a file externally while keeping the same text open in Blender, and it does function, just not ideally; so here are two ways to drive an external file from Blender. With the examples that follow you'll still need a text data-block inside Blender to kick things off, but it points at an external file instead of holding the code itself.

### Executing External Scripts

This amounts to the same thing as running the script directly, pointing at a script's path from a two-line block of code.

`\text
filename = "/full/path/to/myscript.py"
exec(compile(open(filename).read(), filename, 'exec'))
`

Or perhaps, instead of an absolute path, you'd rather point at a script sitting relative to the blend-file itself.

`\text
import bpy
import os

filename = os.path.join(os.path.dirname(bpy.data.filepath), "myscript.py")
exec(compile(open(filename).read(), filename, 'exec'))
`

### Executing Modules

Here's how you'd pull a script in as a module and then call a function from it.

`\text
import myscript
import importlib

importlib.reload(myscript)
myscript.main()
`

See how the script gets reloaded each time; that's what forces the updated copy to be used, since otherwise the cached version sitting in sys.modules would stick around until Blender restarted.

What sets this apart from running the script outright is that it has to invoke a function within the module, main() in this case, though any function will do. One upside is that you can feed arguments into the function from this little script, which often comes in handy for quickly testing different settings.

The catch here is that the script needs to live on Python's module search path. Extending the search path isn't best practice, but for testing it's fine; the next example tacks the current blend-file's directory onto the search path and then brings the script in as a module.

`\text
import sys
import os
import bpy

blend_dir = os.path.dirname(bpy.data.filepath)
if blend_dir not in sys.path:
sys.path.append(blend_dir)

import myscript
import importlib
importlib.reload(myscript)
myscript.main()
`

### Use Blender without its User Interface

While you're developing scripts of your own, Blender's interface can become a nuisance; all the manual reloading, re-running, opening file imports, and so on piles on overhead. For scripts that don't need interaction, it can turn out faster to skip Blender's interface entirely and run the script from the command line.

`\text
blender --background --python myscript.py
`

You'll probably want to launch it against a blend-file so the script has data to work with.

`\text
blender myscene.blend --background --python myscript.py
`

Note

On some setups the Blender executable won't be found unless you give its location in full.

With the script ticking over nicely under background mode, your next concern is reading back what it produced; the right way to do that turns entirely on the task, though here are a few ideas:

- Render to an image, open it in an image viewer, and keep overwriting the same file each pass.

- Save out a fresh blend-file, or push the file through one of Blender's exporters.

- When the results lend themselves to text, print them or write them to a file.

Setting this up takes a moment, but it can repay the effort handsomely by trimming the turnaround on testing changes. You can even leave Blender re-running the script every few seconds with a viewer refreshing the output, so there's no need to step away from your editor to watch the changes.

### Use External Tools

When no off-the-shelf Python module covers the task at hand, it's worth remembering you can often have Python run an external command against your data and read the output back in.

Leaning on outside programs introduces an extra dependency and may narrow who can run the script, but for quickly rigging up your own custom pipeline or knocking out one-off scripts it can be very convenient.

A few examples:

- Drive Gimp in batch mode to run custom scripts for heavier image processing.

- Export 3D models out to external mesh-editing tools and then read the results back.

- Convert files into a recognizable format ahead of reading them.

### Bundled Python & Extensions

Blender's official releases from blender.org ship a full Python installation across every platform; the downside is that any extensions sitting in your system's own Python environment stay invisible to Blender.

There are a couple of ways around this:

- Delete Blender's Python subdirectory, at which point Blender drops back to the system's Python and uses that.

Your platform may require you to point explicitly at where your Python lives, by way of the PYTHONPATH environment variable, for example:

`\text
PYTHONPATH=/usr/lib/python3.7 ./blender --python-use-system-env
`

Warning

The Python (major, minor) version has to line up with the one Blender ships with. So Python 3.6 won't work against a Blender built for Python 3.7.

- Copy or symlink the extensions into Blender's Python subdirectory so Blender picks them up; you can even drop the whole Python installation into Blender's subdirectory, swapping out the one it came with. That holds up as long as the Python versions agree and the paths land in matching relative spots. The payoff is that you can then hand this bundle, Blender plus whatever extensions you depend on, off to others.

### Insert a Python Interpreter into your Script

Partway through a script you might want to peek at variables, call functions, and trace the flow.

`\text
import code
code.interact(local=locals())
`

To reach both global and local variables, run this:

`\text
import code
namespace = globals().copy()
namespace.update(locals())
code.interact(local=namespace)
`

This next one is a one-line equivalent of the snippet above, which makes it simpler to drop into your code:

`\text
__import__('code').interact(local=dict(globals(), **locals()))
`

You can stick code.interact on any line of the script; it halts execution and opens an interactive interpreter in the terminal, and once you're finished you quit the interpreter and the script picks up where it left off.

Should you have IPython installed, its embed() function works too and inherits the current namespace. The IPython prompt brings auto-complete and a few niceties that the stock Python eval-loop lacks.

`\text
import IPython
IPython.embed()
`

Granted, this rather underscores that Blender ships without any built-in Python debugging support, but it's still a useful thing to have in your back pocket.

### Advanced

### Blender as a Module

From a Python standpoint it's tidier to treat the whole thing as an extension, letting a Python script stitch together many pieces.

Among the benefits:

- Outside editors and IDEs can be wired up against the Python API of Blender, with scripts run straight from within the IDE (stepping through code, watching variables as it goes).

- Editors and IDEs can offer auto-complete for Blender's modules and variables.

- Scripts you already have can import Blender's APIs without needing to run inside Blender.

This carries the advanced label because running Blender as a Python module calls for a special build option. For build instructions, see Building Blender as a Python module.

### Python Safety (Build Option)

Since it's possible to reach data that has already been freed (see Gotchas), chasing down what caused a crash can be tough. To have Python throw exceptions when freed data is accessed, rather than crashing outright, switch on the CMake build option `WITH_PYTHON_SAFETY`. Doing so turns on data tracking, which roughly halves data-access speed, which is exactly why release builds leave it off.

# Bones Armatures, Internal Data Their Python Objects

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Bones & Armatures; Internal Data & Their Python Objects.

## Bones & Armatures

### Bones & Armatures

### Edit Bones, Pose Bones, Bone… Bones

In Blender, armature bones are held in three separate data structures. If you reach a bone through the wrong one of them, the properties you actually need may be out of reach.

Note

Throughout the examples below, bpy.context.object is taken to be an armature object.

### Edit Bones

Edit bones live in bpy.context.object.data.edit_bones ; to touch them the armature must first be in Edit-Mode (they simply don't exist in Object or Pose-Mode). Reach for these when you want to spawn new bones, set head/tail or roll, rewire parenting between bones, and so on.

An example with bpy.types.EditBone , which only runs on an armature in Edit-Mode:

`\text
>>> bpy.context.object.data.edit_bones["Bone"].head = Vector((1.0, 2.0, 3.0))
`

Outside Edit-Mode this comes back empty:

`\text
>>> mybones = bpy.context.selected_editable_bones
`

Only while in Edit-Mode does this yield an edit bone:

`\text
>>> bpy.context.active_bone
`

### Bones (Object-Mode)

Plain bones sit in bpy.context.object.data.bones . They exist in Object-Mode and expose several properties you can edit, with the caveat that head and tail are read-only.

An example with bpy.types.Bone , run from Object or Pose-Mode; outside Edit-Mode it returns a bone, not an edit bone:

`\text
>>> bpy.context.active_bone
`

This works because the setting — as it is in Blender — can be changed from whichever mode you're in:

`\text
>>> bpy.context.object.data.bones["Bone"].use_deform = True
`

Readable, but you can't write to it:

`\text
>>> tail = myobj.data.bones["Bone"].tail
`

### Pose Bones

Pose bones are found in bpy.context.object.pose.bones . This is the home of animation data — the animatable transforms land on pose bones, and so do constraints and IK settings.

Some bpy.types.PoseBone examples, usable from Object or Pose-Mode:

`\text
### Gets the name of the first constraint (if it exists).
bpy.context.object.pose.bones["Bone"].constraints[0].name

### Gets the last selected pose bone (Pose-Mode only).
bpy.context.active_pose_bone
`

Note

Observe that the pose hangs off the object instead of the object data; that's exactly what lets two or more objects share one armature while striking different poses.

Note

In a strict sense pose bones aren't bones at all; they capture the armature's present state, which lives on the object (bpy.types.Object) and not on the armature data (bpy.types.Armature). From any pose bone the actual bone remains reachable through bpy.types.PoseBone.bone.

### Armature Mode Switching

Scripts that handle armatures often have to hop between modes, and when you leave Edit-Mode you must be careful not to keep holding edit bones or their head/tail vectors. Reaching for them afterward will crash Blender, so it's vital the script keeps the code for different modes cleanly partitioned.

This bites mainly with Edit-Mode, because pose data can be edited without ever entering Pose-Mode — though to drive operators you may still have to switch into Pose-Mode.

## Internal Data & Their Python Objects

### Internal Data & Their Python Objects

Compared with ordinary Python data, the wrappers around Blender's internal data carry certain restrictions and constraints. This section collects the points that matter most.

### Life-Time of Python Objects Wrapping Blender Data

As a rule, the Python objects that stand in for (wrap) Blender data don't live long. They're spun up when something asks for them and torn down the moment Python stops using them.

The practical lesson: don't stash Python-only data on these objects whenever you need it to persist.

There are a few carve-outs. IDs, once they've made their Python instance, keep it and reuse it instead of minting a fresh Python object on every access. And a modal operator holds onto its instance for as long as it's running. But that's done for speed and counts as an internal implementation detail; leaning on it from Python for any purpose isn't recommended.

Beyond that, when Blender frees internal data it will try to invalidate whatever Python object it knows wraps that data. This isn't always possible, and the result can be an invalid memory access — one more argument for never keeping these around persistently in Python code. The troubleshooting crashes documentation covers this as well.

### Data Names

### Naming Limitations

It's a common mistake to expect newly made data to take precisely the name you requested. The bugs surface when you add data — typically during import — and later try to fetch it back by that name:

`\text
bpy.data.meshes.new(name=meshid)

### Normally some code, function calls, etc.
bpy.data.meshes[meshid]
`

Or when assigning the name:

`\text
obj.name = objname

### Normally some code, function calls, etc.
obj = bpy.data.meshes[objname]
`

Data names can diverge from the values you assigned if those run past the maximum length, are already taken, or are empty.

The better practice is to avoid name references for objects entirely; after creating the data, hold it in a dictionary, a list, on a class, or wherever suits — rarely is there cause to keep looking the same data up by name over and over.

If name references are genuinely necessary, your best bet is a dictionary mapping the imported assets' names to the newly created data; that way you avoid the risk of grabbing — or worse, mutating — data that already exists in the blend-file.

`\text
### Typically declared in the main body of the function.
mesh_name_mapping = {}

mesh = bpy.data.meshes.new(name=meshid)
mesh_name_mapping[meshid] = mesh

### Normally some code, or function calls, etc.

### Use own dictionary rather than `bpy.data`.
mesh = mesh_name_mapping[meshid]
`

### Library Collisions

Data names are kept unique by Blender (bpy.types.ID.name), which stops you from accidentally handing the same name to two scenes, meshes, objects and so on. Pulling in library data from a separate blend-file, though, can throw up name collisions — yet another argument against addressing data by name.

It can get tricky, and Blender itself doesn't always resolve it correctly (when choosing the modifier object, say, you have no way to pick among several same-named objects); even so, it's worth heading the issue off here. Should you need to tell local data apart from library data, there's a facility on bpy.data members for it.

`\text
### Typical name lookup, could be local or library.
obj = bpy.data.objects["my_obj"]

### Library object name lookup using a pair,
### where the second argument is the library path matching bpy.types.Library.filepath.
obj = bpy.data.objects["my_obj", "//my_lib.blend"]

### Local object name look up using a pair,
### where the second argument excludes library data from being returned.
obj = bpy.data.objects["my_obj", None]

### Both the examples above also work for `get`.
obj = bpy.data.objects.get(("my_obj", None))
`

### Stale Data

### No updates after setting values

There are times you set a value from Python and want to read the updated result straight away, e.g: after changing an object's bpy.types.Object.location you might reach for its transform immediately via bpy.types.Object.matrix_world, only to find it doesn't behave as you'd hope. Changes to the UI have comparable issues, covered in the next section.

Consider all the inputs that may shape where an object finally ends up, among them:

- F-curves driving animation.

- Drivers, along with the Python expressions behind them.

- Constraints

- The parents of the object — and in turn their constraints, F-Curves, and the rest.

To avoid pricey recomputation every time a property changes, Blender holds off on evaluating until the result is actually needed. While your script runs, though, you may want the fresh values right away. For that, call bpy.types.ViewLayer.update once you've changed values, for example:

`\text
bpy.context.object.location = 1, 2, 3
bpy.context.view_layer.update()
`

Once that runs, every piece of dependent data — modifiers, drivers, child objects and the like — gets recalculated for the active view layer and is then there for the script to read.

### No updates after changing UI context

Much like the previous case, some UI changes don't take effect at once. Setting bpy.types.Window.workspace, for instance, appears to do nothing in the code right after it (bpy.types.Window.workspace still reads the same), yet the UI does end up reflecting the change. A few of the properties that act this way are:

- bpy.types.Window.workspace

- bpy.types.Window.screen

- bpy.types.Window.scene

- bpy.types.Area.type

- bpy.types.Area.ui_type

Changes like these reshape the UI, and with it the context (bpy.context), quite sharply. That can wreck Blender's context handling. So Blender postpones the change until after operators have finished and just before the UI redraws, which keeps the context switch safe.

When your code depends on running against an updated context, the way around it is to defer that code's execution too. Some options:

- Modal Operator.

- bpy.app.handlers.

- bpy.app.timers.

You can also tie it to drawing callbacks, but that's usually best steered clear of: if a hidden panel, cursor, region or similar fails to draw, your script could turn unreliable.

### Can I redraw during script execution?

The official line on this is no — or, put another way, "You don't want to do that". For some background on why:

For the duration of a script's run, Blender sits and waits for it to finish, effectively locked until it's done; in that state Blender neither redraws nor reacts to user input. Usually that's no great hardship, since the scripts shipped with Blender tend to be short-lived — yet a script can take a while, and it'd be pleasant to watch progress in the viewport.

Tools that pin Blender inside a redraw loop are firmly discouraged, because they fight against Blender's capacity to juggle several operators at once and to refresh different bits of the interface while a tool runs.

The answer here, then, is to write a modal operator — one that supplies a modal() function; the text editor ships a template for exactly this. Such operators fire on user input, or set up their own timers to run at intervals; they can consume the events or let them fall through to the keymap or to other modal operators. Transform, Painting, Fly Navigation and File Select are all examples of modal operators.

Authoring a modal operator takes more effort than a bare for loop crammed with draw calls, yet it's the more flexible choice and meshes far more cleanly with how Blender is built.

Fine, fine — drawing from Python anyway

Should you insist, then yes, the trick exists — but any script relying on it is barred from being bundled with Blender, won't have its resulting issues counted as bugs, and carries no guarantee of still working in later releases.

`\text
bpy.ops.wm.redraw_timer(type='`DRAW_WIN_SWAP`', iterations=1)
`

# Using Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Using Operators

Operators are the tools Blender hands to its users, and the fact that Python can drive them too is very handy. Even so, operators come with limits that can make them clumsy to script.

The headline restrictions:

- There's no handing them a target — objects, meshes, materials and the like — since operators read the context rather than accept such arguments.

- Calling an operator returns only whether it succeeded (finished versus canceled); in some cases it would make more sense, from an API standpoint, to return the actual result of the operation.

- An operator's poll function can simply fail, where an equivalent API function would raise an exception spelling out precisely what went wrong.

### Why does an operator's poll fail?

Calling an operator can throw an error like this:

`\text
>>> bpy.ops.action.clean(threshold=0.001)
RuntimeError: Operator bpy.ops.action.clean.poll() failed, context is incorrect
`

Which begs the question of what the right context actually is.

Typically an operator wants something to act on — an active object, a selection, or the active area type — and a few are fussier yet about the conditions for running. In most cases you can work out the context it expects by observing where it's used in Blender and thinking through what it accomplishes.

If that leaves you stuck, the only sure way to learn what's tripping the error is, unfortunately, to read the poll function's source and see what it checks. For Python operators the source is easy enough to find, since it ships with Blender and the operator reference docs cite the file and line. Tracking it down in the C code is less convenient — especially if C isn't your language — but searching on the operator's name or description should still lead you to the poll function with no C knowledge required.

Note

Blender does carry the machinery for poll functions to report their own failure reasons, though at present it's barely used; should you want to improve the API, you're welcome to drop in bpy.types.Operator.poll_message_set ( CTX_wm_operator_poll_msg_set in C) calls anywhere the cause of a poll failure isn't obvious, e.g:

`\text
>>> bpy.ops.object.vertex_group_add()
RuntimeError: Operator bpy.ops.object.vertex_group_add.poll() No active editable object
`

In some cases using bpy.types.Context.temp_override to enable temporary logging or using the
context category when logging can help.

### The operator still doesn't work!

A number of Blender operators are built for one specific context only; some, for instance, fire only out of the properties editor, where what they examine is whichever constraint, modifier or material is currently active.

A few such cases:

- bpy.ops.texture.slot_move()

- bpy.ops.constraint.limitdistance_reset()

- bpy.ops.object.modifier_copy()

- bpy.ops.buttons.file_browse()

The other possibility is that you're the first to try driving this operator from a script, and it needs some tweaking to run in a different context. If an operator ought to work logically yet fails when called from a script, that should be filed on the bug tracker.

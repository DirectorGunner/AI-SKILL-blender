# Message Bus Bpy Msgbus

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Message Bus (bpy.msgbus)

Allows subscription to property changes within Blender's data-blocks through the RNA change notification system.

### Limitations

The message bus fires on RNA-layer modifications. Changes that trigger notifications:

- Python API updates, e.g. some_object.location.x += 3 .

- Interactive edits via UI sliders, input fields, and buttons.

These do not generate message bus alerts:

- Viewport manipulation of objects.

- Animation playback-driven updates.

Side effects of msgbus callbacks skip undo integration, so users may erase them with Undo then Redo.

Unlike direct property callbacks, message bus events queue until all active operators conclude. Each property fires its callback a maximum of once per update pass, even if modified multiple times.

### Example Use

Below demonstrates subscription to transformations on the focused object.

`\text
import bpy

### Any Python object can act as the subscription's owner.
owner = object()

subscribe_to = bpy.context.object.location

def msgbus_callback(*args):
### This will print:
### Something changed! (1, 2, 3)
print(\"Something changed!\", args)

bpy.msgbus.subscribe_rna(
key=subscribe_to,
owner=owner,
args=(1, 2, 3),
notify=msgbus_callback,
)
`\

Certain properties become Python-wrapped on retrieval. To establish subscriptions, unwrap them with datablock.path_resolve(\"property_name\", False) :

`\text
import bpy

subscribe_to = bpy.context.object.path_resolve(\"name\", False)
`\

Subscriptions can also target properties across all instances of a given type:

`\text
import bpy

subscribe_to = (bpy.types.Object, \"location\")
`\

bpy.msgbus. clear_by_owner ( owner )

Purge all subscriptions tied to a given owner.

Parameters :

owner ( Any ) – The owner reference supplied to subscribe_rna().

bpy.msgbus. publish_rna ( * , key )

Parameters :

key (bpy.types.Property | bpy.types.Struct | tuple[bpy.types.Struct, str]) – Marks the category of subscribed data

Options are
- A property instance.
- A struct type.
- A tuple of (struct, property name) .

Inform subscribers about updates to this element
(automatic publication typically handles this without explicit calls). In some scenarios, explicit publication using broader keys proves helpful.

bpy.msgbus. subscribe_rna ( * , key , owner , args , notify , options = set() )

Establish a message bus listener. It persists until a new .blend loads or removal via bpy.msgbus.clear_by_owner().

Parameters :

- key (bpy.types.Property | bpy.types.Struct | tuple[bpy.types.Struct, str]) – Marks the category of subscribed data

Options are
- A property instance.
- A struct type.
- A tuple of (struct, property name) .

- owner ( Any ) – Reference for this listener (matches by identity).

- args ( tuple ) – Parameters delivered to the callback.

- notify ( Callable [ ... , None ] ) – The notification handler.

- options ( set [ Literal [ 'PERSISTENT' ] ] ) – Customize listener behavior.

- PERSISTENT when enabled, survives ID data remapping.

Note

All listeners vanish at file-load. Re-register them during post-load events, consult bpy.app.handlers.load_post.

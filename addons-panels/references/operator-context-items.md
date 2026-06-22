# Operator Context Items, Operator Property Tag Items, Operator Type Flag Items, Property String Search Flag Items ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Operator Context Items; Operator Property Tag Items; Operator Type Flag Items; Property String Search Flag Items; Property Subtype String Items; Property Type Items; Wm Report Items; ID Properties Module (idprop); ID Property Access (idprop.types).

## Operator Context Items

### Operator Context Items

`INVOKE_DEFAULT` :

Invoke Default.

`INVOKE_REGION_WIN` :

Invoke Region Window.

`INVOKE_REGION_CHANNELS` :

Invoke Region Channels.

`INVOKE_REGION_PREVIEW` :

Invoke Region Preview.

`INVOKE_AREA` :

Invoke Area.

`INVOKE_SCREEN` :

Invoke Screen.

`EXEC_DEFAULT` :

Exec Default.

`EXEC_REGION_WIN` :

Exec Region Window.

`EXEC_REGION_CHANNELS` :

Exec Region Channels.

`EXEC_REGION_PREVIEW` :

Exec Region Preview.

`EXEC_AREA` :

Exec Area.

`EXEC_SCREEN` :

Exec Screen.

## Operator Property Tag Items

### Operator Property Tag Items

ADVANCED :

Advanced.

This is an advanced property, so the UI is encouraged to keep it tucked away.

## Operator Type Flag Items

### Operator Type Flag Items

REGISTER :

Register.

Show it in the info window and allow the redo toolbar panel.

UNDO :

Undo.

Emit an undo event once the operator returns `FINISHED` (required for operator redo, and obligatory whenever the operator alters Blender data).

`UNDO_GROUPED` :

Grouped Undo.

Collapse repeated runs of this operator into one undo event.

BLOCKING :

Blocking.

Stop everything else from grabbing the cursor.

MACRO :

Macro.

Apply this to test whether a given operator is a macro.

`GRAB_CURSOR` :

Grab Pointer.

Make the operator capture mouse focus, switching on wrapping while continuous grab is active.

`GRAB_CURSOR_X` :

Grab Pointer X.

Grab, only warping the X axis.

`GRAB_CURSOR_Y` :

Grab Pointer Y.

Grab, only warping the Y axis.

`DEPENDS_ON_CURSOR` :

Depends on Cursor.

The starting cursor position matters; launched from a menu or button, the user is asked to set the cursor first.

PRESET :

Preset.

Show a preset button alongside the operator's settings.

INTERNAL :

Internal.

Take the operator out of the search results.

`MODAL_PRIORITY` :

Modal Priority.

Process events ahead of other modal operators that lack this flag. Apply it carefully, and do not alter data that those operators expect to stay constant while they run..

## Property String Search Flag Items

### Property String Search Flag Items

SORT :

Sort Search Results.

SUGGESTION :

Suggestion.

The search hits are offered as suggestions; other values remain acceptable.

## Property Subtype String Items

### Property Subtype String Items

`FILE_PATH` :

File Path.

`DIR_PATH` :

Directory Path.

`FILE_NAME` :

File Name.

`BYTE_STRING` :

Byte String.

PASSWORD :

Password.

A string shown masked (’********’).

NONE :

None.

## Property Type Items

### Property Type Items

BOOLEAN :

Boolean.

INT :

Integer.

FLOAT :

Float.

STRING :

String.

ENUM :

Enumeration.

POINTER :

Pointer.

COLLECTION :

Collection.

## Wm Report Items

### Wm Report Items

DEBUG :

Debug.

INFO :

Info.

OPERATOR :

Operator.

PROPERTY :

Property.

WARNING :

Warning.

ERROR :

Error.

`ERROR_INVALID_INPUT` :

Invalid Input.

`ERROR_INVALID_CONTEXT` :

Invalid Context.

`ERROR_OUT_OF_MEMORY` :

Out of Memory.

## ID Properties Module (idprop)

### ID Properties Module (idprop)

Through this module you reach the ID property types, the ones behind
custom properties on data-blocks that you read and write with ["key"] syntax.

- See Custom Properties for example usage.

- See Types with Custom Property Support for types that support custom properties.

## ID Property Access (idprop.types)

### ID Property Access (idprop.types)

class idprop.types. IDPropertyArray

A fixed-type array of values that you can index into and slice.

to_list ( )

Hand back the array as a list.

Returns :

The array as a list.

Return type :

list[int] | list[float] | list[bool]

typecode

The type of the data in the array {‘f’: float (32-bit), ‘d’: double (64-bit), ‘i’: int, ‘b’: bool}. Both ‘f’ and ‘d’ use Python’s float type but differ in storage precision.

class idprop.types. IDPropertyGroup

A group of ID properties that acts like a dictionary, allowing key lookup, iteration, and membership tests.

clear ( )

Drop every member out of this group.

get ( key , default = None )

Hand back the value for key when present, otherwise default.

Parameters :

- key ( str ) – The key to look up.

- default ( Any ) – Value to return if key is not found.

Returns :

The value for the key, or default if not found.

Return type :

Any

items ( )

Hand back a view over the group's items, working like the dictionary items method.

Returns :

A view of the items.

Return type :

IDPropertyGroupViewItems

keys ( )

Hand back a view over the group's keys.

Returns :

A view of the keys.

Return type :

IDPropertyGroupViewKeys

pop ( key , default )

Take an item out of the group and hand back its Python form.

Raises :

KeyError – When the item doesn’t exist and no default is given.

Parameters :

- key ( str ) – Name of item to remove.

- default ( Any ) – Value to return when key isn’t found (optional, a KeyError is raised when omitted and the key is not found).

Returns :

A Python representation of the removed item, or default .

Return type :

Any

to_dict ( )

Hand back a fully Python version of the group.

Returns :

A dictionary representation of the group.

Return type :

dict[str, Any]

update ( other )

Merge in key-value pairs from other , replacing any keys that already exist.

Note

Unlike dict.update() , keyword arguments are not supported.

Parameters :

other (IDPropertyGroup | dict[str, Any]) – Updates the values in the group with this.

values ( )

Hand back the values held in this group.

Returns :

A view of the values.

Return type :

IDPropertyGroupViewValues

name

The name of this Group.

class idprop.types. IDPropertyGroupIterItems

Iterator over IDPropertyGroup items (key/value pairs).

class idprop.types. IDPropertyGroupIterKeys

Iterator over IDPropertyGroup keys.

class idprop.types. IDPropertyGroupIterValues

Iterator over IDPropertyGroup values.

class idprop.types. IDPropertyGroupViewItems

A view of IDPropertyGroup items as key/value pairs (supports len() , in , iteration, and reversed() ).

class idprop.types. IDPropertyGroupViewKeys

A view of IDPropertyGroup keys (supports len() , in , iteration, and reversed() ).

class idprop.types. IDPropertyGroupViewValues

A view of IDPropertyGroup values (supports len() , in , iteration, and reversed() ).

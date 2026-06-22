# Huecorrectmodifier Stripmodifier, Idoverridelibraryproperties Bpy Prop Collection, Idoverridelibraryproperty Bpy Struct, Idoverridelibrarypropertyoperation Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: HueCorrectModifier(StripModifier); IDOverrideLibraryProperties(bpy_prop_collection); IDOverrideLibraryProperty(bpy_struct); IDOverrideLibraryPropertyOperation(bpy_struct); IDOverrideLibraryPropertyOperations(bpy_prop_collection); IDPropertyWrapPtr(bpy_struct); IDViewerPathElem(ViewerPathElem); IKParam(bpy_struct); IndexSwitchItem(bpy_struct); Int2Attribute(Attribute); Int2AttributeValue(bpy_struct).

## HueCorrectModifier(StripModifier)

### HueCorrectModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. HueCorrectModifier ( StripModifier )

Adjusts hue on a sequencer strip via a curve.

curve_mapping

(readonly)

Type :

CurveMapping

open_mask_input_panel

(default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## IDOverrideLibraryProperties(bpy_prop_collection)

### IDOverrideLibraryProperties(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. IDOverrideLibraryProperties ( bpy_prop_collection )

The set of properties that an override carries.

add ( rna_path )

Register a property on the override library if it has not been added already.

Parameters :

rna_path ( str ) – RNA Path, RNA-Path of the property to add (never None)

Returns :

New Property, Newly created override property or existing one

Return type :

IDOverrideLibraryProperty

remove ( property )

Detach and delete a property.

Parameters :

property (IDOverrideLibraryProperty) – Property, Override property to be deleted

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| IDOverrideLibrary.properties | |

## IDOverrideLibraryProperty(bpy_struct)

### IDOverrideLibraryProperty(bpy_struct)

base class — bpy_struct

class bpy.types. IDOverrideLibraryProperty ( bpy_struct )

Captures the details of one property that has been overridden.

operations

List of overriding operations for a property (default None, readonly)

Type :

IDOverrideLibraryPropertyOperations[IDOverrideLibraryPropertyOperation]

rna_path

The RNA path that reaches the property, starting from the owning ID (default "", readonly, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| IDOverrideLibrary.properties IDOverrideLibraryProperties.add | IDOverrideLibraryProperties.remove |

## IDOverrideLibraryPropertyOperation(bpy_struct)

### IDOverrideLibraryPropertyOperation(bpy_struct)

base class — bpy_struct

class bpy.types. IDOverrideLibraryPropertyOperation ( bpy_struct )

Captures one operation applied to an overridden property.

flag

Status flags (default set(), readonly)

- MANDATORY
Mandatory – On templates, stops the user deleting a predefined operation (NOT USED).

- LOCKED
Locked – Stops the user from changing this override operation (NOT USED).

- `IDPOINTER_MATCH_REFERENCE`
Match Reference – Whatever ID pointer this operation overrides should line up with the reference hierarchy.

- `IDPOINTER_ITEM_USE_ID`
ID Item Use ID Pointer – For RNA collections of IDs only, where the item is referenced by its ID pointer itself rather than just its name.

Type :

set[Literal['MANDATORY', 'LOCKED', '`IDPOINTER_MATCH_REFERENCE`', '`IDPOINTER_ITEM_USE_ID`']]

operation

What override operation is performed (default 'REPLACE' , readonly)

- NOOP
No-Op – A do-nothing entry that blocks real overrides from being added (NOT USED).

- REPLACE
Replace – Swap the reference value out for the overriding one.

- `DIFF_ADD`
Differential – Records and applies the difference between the reference and local value (NOT USED).

- `DIFF_SUB`
Differential – Records and applies the difference between the reference and local value (NOT USED).

- `FACT_MULTIPLY`
Factor – Records and applies a multiplication factor between the reference and local value (NOT USED).

- `INSERT_AFTER`
Insert After – Drop a fresh item into the collection just past the one named in subitem_reference_name/_id or _index.

- `INSERT_BEFORE`
Insert Before – Drop a fresh item into the collection just ahead of the one named in subitem_reference_name/_id or _index (NOT USED).

Type :

Literal['NOOP', 'REPLACE', '`DIFF_ADD`', '`DIFF_SUB`', '`FACT_MULTIPLY`', '`INSERT_AFTER`', '`INSERT_BEFORE`']

subitem_local_id

For ID collections only, this tells apart same-named IDs that come from separate libraries (readonly)

Type :

ID

subitem_local_index

Helps track edits made within the collection (in [-1, inf], default -1, readonly)

Type :

int

subitem_local_name

Helps track edits made within the collection (default "", readonly, never None)

Type :

str

subitem_reference_id

For ID collections only, this tells apart same-named IDs that come from separate libraries (readonly)

Type :

ID

subitem_reference_index

Helps track edits made within the collection (in [-1, inf], default -1, readonly)

Type :

int

subitem_reference_name

Helps track edits made within the collection (default "", readonly, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| IDOverrideLibraryProperty.operations IDOverrideLibraryPropertyOperations.add | IDOverrideLibraryPropertyOperations.remove |

## IDOverrideLibraryPropertyOperations(bpy_prop_collection)

### IDOverrideLibraryPropertyOperations(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. IDOverrideLibraryPropertyOperations ( bpy_prop_collection )

A collection holding the individual override operations.

add ( operation , * , use_id = False , subitem_reference_name = '' , subitem_local_name = '' , subitem_reference_id = None , subitem_local_id = None , subitem_reference_index = -1 , subitem_local_index = -1 )

Append a fresh operation.

Parameters :

- operation ( Literal [ 'NOOP' , 'REPLACE' , '`DIFF_ADD`' , '`DIFF_SUB`' , '`FACT_MULTIPLY`' , '`INSERT_AFTER`' , '`INSERT_BEFORE`' ] ) – Operation, Which override operation to carry out

- NOOP
No-Op – A placeholder that performs nothing and keeps real overrides from being added (NOT USED).

- REPLACE
Replace – Swap the reference value out for the overriding one.

- `DIFF_ADD`
Differential – Keeps, then reapplies, the gap between the reference and local value (NOT USED).

- `DIFF_SUB`
Differential – Keeps, then reapplies, the gap between the reference and local value (NOT USED).

- `FACT_MULTIPLY`
Factor – Keeps, then reapplies, a multiplier relating the reference and local value (NOT USED).

- `INSERT_AFTER`
Insert After – Place a new collection item just past the one named in subitem_reference_name/_id or _index.

- `INSERT_BEFORE`
Insert Before – Place a new collection item just ahead of the one named in subitem_reference_name/_id or _index (NOT USED).

- use_id ( bool ) – Use ID Pointer Subitem, Whether the matched or newly made liboverride operation relies on ID pointers (optional)

- subitem_reference_name ( str ) – Subitem Reference Name, Drives insertion or ID swapping within the collection (optional, never None)

- subitem_local_name ( str ) – Subitem Local Name, Drives insertion or ID swapping within the collection (optional, never None)

- subitem_reference_id (ID) – Subitem Reference ID, Drives ID swapping within the collection (optional)

- subitem_local_id (ID) – Subitem Local ID, Drives ID swapping within the collection (optional)

- subitem_reference_index ( int ) – Subitem Reference Index, Drives insertion or ID swapping within the collection (in [-1, inf], optional)

- subitem_local_index ( int ) – Subitem Local Index, Drives insertion or ID swapping within the collection (in [-1, inf], optional)

Returns :

New Operation, Created operation

Return type :

IDOverrideLibraryPropertyOperation

remove ( operation )

Delete a given operation and discard it.

Parameters :

operation (IDOverrideLibraryPropertyOperation) – Operation, Override operation to be deleted

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| IDOverrideLibraryProperty.operations | |

## IDPropertyWrapPtr(bpy_struct)

### IDPropertyWrapPtr(bpy_struct)

base class — bpy_struct

class bpy.types. IDPropertyWrapPtr ( bpy_struct )

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. A back door into the runtime-defined RNA data store, meant purely for tests and debugging. Steer clear of it during normal scripting, and never count on the data it returns being writable.

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| MovieClip.metadata | MovieStrip.metadata |

## IDViewerPathElem(ViewerPathElem)

### IDViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. IDViewerPathElem ( ViewerPathElem )

id

(readonly)

Type :

ID

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |

## IKParam(bpy_struct)

### IKParam(bpy_struct)

base class — bpy_struct

subclasses —
Itasc

class bpy.types. IKParam ( bpy_struct )

The parent type from which IK solver parameter sets derive.

ik_solver

The IK solver that owns this parameter set (default 'LEGACY' , readonly)

- LEGACY
Standard – The original IK solver.

- ITASC
iTaSC – A stateful IK solver handling multiple constraints.

Type :

Literal[‘LEGACY’, ‘ITASC’]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Pose.ik_param | |

## IndexSwitchItem(bpy_struct)

### IndexSwitchItem(bpy_struct)

base class — bpy_struct

class bpy.types. IndexSwitchItem ( bpy_struct )

identifier

A stable identifier kept for the item (in [-inf, inf], default 0, readonly)

Type :

int

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| GeometryNodeIndexSwitch.index_switch_items NodeIndexSwitchItems.new | NodeIndexSwitchItems.remove |

## Int2Attribute(Attribute)

### Int2Attribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. Int2Attribute ( Attribute )

A geometry attribute holding 2D integer vectors.

data

(default None, readonly)

Type :

bpy_prop_collection[Int2AttributeValue]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Attribute.name Attribute.data_type Attribute.storage_type | Attribute.domain Attribute.is_internal Attribute.is_required |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Attribute.bl_rna_get_subclass Attribute.bl_rna_get_subclass_py |

## Int2AttributeValue(bpy_struct)

### Int2AttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. Int2AttributeValue ( bpy_struct )

A 2D value within a geometry attribute.

value

A 2D vector (array of 2 items, in [-inf, inf], default (0, 0))

Type :

bpy_prop_array[int]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Int2Attribute.data | |

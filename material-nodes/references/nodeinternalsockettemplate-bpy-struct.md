# Nodeinternalsockettemplate Bpy Struct (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### NodeInternalSocketTemplate(bpy_struct)

base class — bpy_struct

class bpy.types. NodeInternalSocketTemplate ( bpy_struct )

A node socket's data type paired with its default value.

identifier

The socket's identifier (default “”, readonly, never None)

Type :

str

name

The socket's name (default “”, readonly, never None)

Type :

str

type

The socket's data type (default 'VALUE' , readonly)

Type :

Literal[Node Socket Type Items]

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

## See also

- [Bpy Struct](bpy-struct.md)

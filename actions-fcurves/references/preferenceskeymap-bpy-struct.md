# Preferenceskeymap Bpy Struct, Primitiveboolean Bpy Struct, Primitivefloat Bpy Struct, Primitiveint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PreferencesKeymap(bpy_struct); PrimitiveBoolean(bpy_struct); PrimitiveFloat(bpy_struct); PrimitiveInt(bpy_struct); PrimitiveString(bpy_struct); Property(bpy_struct); PropertyGroupItem(bpy_struct); QuaternionAttribute(Attribute); QuaternionAttributeValue(bpy_struct); ReadOnlyInteger(bpy_struct); Region(bpy_struct); RepeatZoneViewerPathElem(ViewerPathElem).

## PreferencesKeymap(bpy_struct)

### PreferencesKeymap(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesKeymap ( bpy_struct )

Shortcut configuration for keyboards and other input devices

active_keyconfig

Name of the key configuration that is currently active (default “”, never None)

Type :

str

show_ui_keyconfig

(default True)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Preferences.keymap | |

## PrimitiveBoolean(bpy_struct)

### PrimitiveBoolean(bpy_struct) 

base class — bpy_struct

class bpy.types. PrimitiveBoolean ( bpy_struct ) 

RNA wrapped boolean

value 

(default False, readonly)

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

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

## PrimitiveFloat(bpy_struct)

### PrimitiveFloat(bpy_struct) 

base class — bpy_struct

class bpy.types. PrimitiveFloat ( bpy_struct ) 

RNA wrapped float

value 

(in [-inf, inf], default 0.0, readonly)

Type :

float

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

## PrimitiveInt(bpy_struct)

### PrimitiveInt(bpy_struct) 

base class — bpy_struct

class bpy.types. PrimitiveInt ( bpy_struct ) 

RNA wrapped int

value 

(in [-inf, inf], default 0, readonly)

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

## PrimitiveString(bpy_struct)

### PrimitiveString(bpy_struct) 

base class — bpy_struct

class bpy.types. PrimitiveString ( bpy_struct ) 

RNA wrapped string

value 

(default b””, readonly, never None)

Type :

bytes

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

## Property(bpy_struct)

### Property(bpy_struct) 

base class — bpy_struct

subclasses —
BoolProperty, CollectionProperty, EnumProperty, FloatProperty, IntProperty, PointerProperty, StringProperty

class bpy.types. Property ( bpy_struct ) 

RNA property definition

deprecated_note 

Text explaining the deprecation (default “”, readonly, never None)

Type :

str

deprecated_removal_version 

The Blender release in which removal is anticipated (array of 3 items, in [-inf, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

deprecated_version 

The Blender release that marked this as deprecated (array of 3 items, in [-inf, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

description 

Text shown in the tooltip for this property (default “”, readonly, never None)

Type :

str

icon 

The icon assigned to the item (default 'NONE' , readonly)

Type :

Literal[Icon Items]

identifier 

The unique name referenced in code and scripts (default “”, readonly, never None)

Type :

str

is_animatable 

Whether the property can be animated via RNA (default False, readonly)

Type :

bool

is_argument_optional 

Set when the property is optional in a Python function backing an RNA function (default False, readonly)

Type :

bool

is_deprecated 

Whether this property is deprecated (default False, readonly)

Type :

bool

is_enum_flag 

Set when several enums apply at once (default False, readonly)

Type :

bool

is_hidden 

Set when the property is concealed (default False, readonly)

Type :

bool

is_library_editable 

The property may be edited on linked instances (those edits are not saved) (default False, readonly)

Type :

bool

is_never_none 

Set when this value may never be assigned None (default False, readonly)

Type :

bool

is_output 

Set when this property serves as an output of an RNA function (default False, readonly)

Type :

bool

is_overridable 

Whether the property can be overridden through RNA (default False, readonly)

Type :

bool

is_path_output 

The property holds a filename, filepath, or directory output (default False, readonly)

Type :

bool

is_path_supports_blend_relative 

The property is a path that accepts the “//” prefix, which marks the location as relative to the directory of the “.blend” file (default False, readonly)

Type :

bool

is_path_supports_templates 

The property is a path that accepts the “{variable_name}” expression syntax, swapping in the value of the named variable wherever the expression appears (default False, readonly)

Type :

bool

is_readonly 

Whether the property can be edited through RNA (default False, readonly)

Type :

bool

is_registered 

The property was registered during type registration (default False, readonly)

Type :

bool

is_registered_optional 

The property is optionally registered during type registration (default False, readonly)

Type :

bool

is_required 

Cleared when this property is an optional argument of an RNA function (default False, readonly)

Type :

bool

is_runtime 

The property was generated dynamically while running (default False, readonly)

Type :

bool

is_skip_preset 

Set when the property is excluded from presets (default False, readonly)

Type :

bool

is_skip_save 

Set when the property relies on ghost values (default False, readonly)

Type :

bool

name 

The name meant for people to read (default “”, readonly, never None)

Type :

str

srna 

The struct definition tied to properties given to this item (readonly)

Type :

Struct

subtype 

How the property should be interpreted semantically (default 'NONE' , readonly)

Type :

Literal[Property Subtype Items]

tags 

The subset of tags (declared in the parent struct) enabled for this property (default set(), readonly)

Type :

set[str]

translation_context 

The translation context attached to the property's name (default “”, readonly, never None)

Type :

str

type 

What kind of data the property holds (default 'BOOLEAN' , readonly)

Type :

Literal[Property Type Items]

unit 

Which unit category applies to this property (default 'NONE' , readonly)

Type :

Literal[Property Unit Items]

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

| bpy.context.texture_user_property Function.parameters | Struct.properties |

## PropertyGroupItem(bpy_struct)

### PropertyGroupItem(bpy_struct) 

base class — bpy_struct

class bpy.types. PropertyGroupItem ( bpy_struct ) 

Property holding arbitrary, user-supplied data

bool 

(default False)

Type :

bool

bool_array 

(array of 1 items, default (False,))

Type :

bpy_prop_array[bool]

collection 

(default None, readonly)

Type :

bpy_prop_collection[PropertyGroup]

double 

(in [-inf, inf], default 0.0)

Type :

float

double_array 

(array of 1 items, in [-inf, inf], default (0.0,))

Type :

bpy_prop_array[float]

enum 

(default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

float 

(in [-inf, inf], default 0.0)

Type :

float

float_array 

(array of 1 items, in [-inf, inf], default (0.0,))

Type :

bpy_prop_array[float]

group 

(readonly)

Type :

PropertyGroup

id 

Type :

ID

idp_array 

(default None, readonly)

Type :

bpy_prop_collection[PropertyGroup]

int 

(in [-inf, inf], default 0)

Type :

int

int_array 

(array of 1 items, in [-inf, inf], default (0,))

Type :

bpy_prop_array[int]

string 

(default “”, never None)

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

## QuaternionAttribute(Attribute)

### QuaternionAttribute(Attribute) 

base classes — bpy_struct, Attribute

class bpy.types. QuaternionAttribute ( Attribute ) 

Geometry attribute holding rotation data

data 

(default None, readonly)

Type :

bpy_prop_collection[QuaternionAttributeValue]

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

## QuaternionAttributeValue(bpy_struct)

### QuaternionAttributeValue(bpy_struct) 

base class — bpy_struct

class bpy.types. QuaternionAttributeValue ( bpy_struct ) 

A rotation value stored in a geometry attribute

value 

Quaternion (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

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

| QuaternionAttribute.data | |

## ReadOnlyInteger(bpy_struct)

### ReadOnlyInteger(bpy_struct) 

base class — bpy_struct

class bpy.types. ReadOnlyInteger ( bpy_struct ) 

value 

(in [-inf, inf], default 0, readonly)

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

| Mesh.loop_triangle_polygons | |

## Region(bpy_struct)

### Region(bpy_struct) 

base class — bpy_struct

class bpy.types. Region ( bpy_struct ) 

A region inside a subdivided screen area

active_panel_category 

The panel category currently active; this may be Null when the region lacks support for the feature (NOTE: these categories are built at runtime, so the list can be empty at initialization, before any drawing has happened) (default 'UNSUPPORTED' )

Type :

Literal[Region Panel Category Items]

alignment 

How the region is aligned inside the area (default 'NONE' , readonly)

- NONE
None – Don’t use any fixed alignment, fill available space.

- TOP
Top.

- BOTTOM
Bottom.

- LEFT
Left.

- RIGHT
Right.

- `HORIZONTAL_SPLIT`
Horizontal Split.

- `VERTICAL_SPLIT`
Vertical Split.

- FLOAT
Float – Region floats on screen, does not use any fixed alignment.

- `QUAD_SPLIT`
Quad Split – Region is split horizontally and vertically.

Type :

Literal[‘NONE’, ‘TOP’, ‘BOTTOM’, ‘LEFT’, ‘RIGHT’, ‘`HORIZONTAL_SPLIT`’, ‘`VERTICAL_SPLIT`’, ‘FLOAT’, ‘`QUAD_SPLIT`’]

data 

Data particular to the region (its type varies with the region type) (readonly)

Type :

AnyType

height 

The height of the region (in [0, 32767], default 0, readonly)

Type :

int

type 

Which type this region is (default 'WINDOW' , readonly)

Type :

Literal[Region Type Items]

view2d 

The region's 2D view (readonly, never None)

Type :

View2D

width 

The width of the region (in [0, 32767], default 0, readonly)

Type :

int

x 

Where the region sits vertically, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

y 

Where the region sits horizontally, relative to the window (in [-inf, inf], default 0, readonly)

Type :

int

tag_redraw ( ) 

tag_redraw

tag_refresh_ui ( ) 

tag_refresh_ui

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

| Area.regions Context.region | Context.region_popup |

## RepeatZoneViewerPathElem(ViewerPathElem)

### RepeatZoneViewerPathElem(ViewerPathElem)

base classes — bpy_struct, ViewerPathElem

class bpy.types. RepeatZoneViewerPathElem ( ViewerPathElem )

repeat_output_node_id

(in [-inf, inf], default 0)

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

| bpy_struct.id_data ViewerPathElem.type | ViewerPathElem.ui_name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ViewerPathElem.bl_rna_get_subclass ViewerPathElem.bl_rna_get_subclass_py |

# Objectconstraints Bpy Prop Collection, Objectdisplay Bpy Struct, Objectmodifiers Bpy Prop Collection, Objectshaderfx Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ObjectConstraints(bpy_prop_collection); ObjectDisplay(bpy_struct); ObjectModifiers(bpy_prop_collection); ObjectShaderFx(bpy_prop_collection); OperatorFileListElement(PropertyGroup); OperatorMacro(bpy_struct); OperatorMousePath(PropertyGroup); OperatorOptions(bpy_struct); OperatorProperties(bpy_struct); OperatorStrokeElement(PropertyGroup); PaintCurve(ID); Palette(ID).

## ObjectConstraints(bpy_prop_collection)

### ObjectConstraints(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ObjectConstraints ( bpy_prop_collection ) 

The set of constraints attached to an object

active 

Active Object constraint

Type :

Constraint

new ( type ) 

Attach a fresh constraint to this object

Parameters :

type (Literal[Constraint Type Items]) – Constraint type to add

Returns :

New constraint

Return type :

Constraint

remove ( constraint ) 

Detach a constraint from this object

Parameters :

constraint (Constraint) – Removed constraint (never None)

clear ( ) 

Detach every constraint from this object

move ( from_index , to_index ) 

Shift a constraint to another slot

Parameters :

- from_index ( int ) – From Index, Index to move (in [-inf, inf])

- to_index ( int ) – To Index, Target index (in [-inf, inf])

copy ( constraint ) 

Attach a fresh constraint duplicated from the one given

Parameters :

constraint (Constraint) – Constraint to copy - may belong to a different object (never None)

Returns :

New constraint

Return type :

Constraint

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

| Object.constraints | |

## ObjectDisplay(bpy_struct)

### ObjectDisplay(bpy_struct) 

base class — bpy_struct

class bpy.types. ObjectDisplay ( bpy_struct ) 

Display settings an object uses in the 3D viewport

show_shadows 

Let the object cast shadows within the 3D viewport (default True)

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

| Object.display | |

## ObjectModifiers(bpy_prop_collection)

### ObjectModifiers(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ObjectModifiers ( bpy_prop_collection ) 

The set of modifiers attached to an object

active 

The active modifier in the list

Type :

Modifier

new ( name , type ) 

Attach a fresh modifier

Parameters :

- name ( str ) – New name for the modifier (never None)

- type (Literal[Object Modifier Type Items]) – Modifier type to add

Returns :

Newly created modifier

Return type :

Modifier

remove ( modifier ) 

Detach an existing modifier from the object

Parameters :

modifier (Modifier) – Modifier to remove (never None)

clear ( ) 

Detach every modifier from the object

move ( from_index , to_index ) 

Shift a modifier to another slot

Parameters :

- from_index ( int ) – From Index, Index to move (in [-inf, inf])

- to_index ( int ) – To Index, Target index (in [-inf, inf])

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

| Object.modifiers | |

## ObjectShaderFx(bpy_prop_collection)

### ObjectShaderFx(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ObjectShaderFx ( bpy_prop_collection ) 

The set of effects attached to an object

new ( name , type ) 

Attach a fresh shader fx

Parameters :

- name ( str ) – New name for the effect (never None)

- type (Literal[Object Shaderfx Type Items]) – Effect type to add

Returns :

Newly created effect

Return type :

ShaderFx

remove ( shader_fx ) 

Detach an existing effect from the object

Parameters :

shader_fx (ShaderFx) – Effect to remove (never None)

clear ( ) 

Detach every effect from the object

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

| Object.shader_effects | |

## OperatorFileListElement(PropertyGroup)

### OperatorFileListElement(PropertyGroup) 

base classes — bpy_struct, PropertyGroup

class bpy.types. OperatorFileListElement ( PropertyGroup ) 

name 

Name of a file or directory inside a file list (default “”, never None)

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

| bpy_struct.id_data | PropertyGroup.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values PropertyGroup.bl_system_properties_get PropertyGroup.bl_rna_get_subclass PropertyGroup.bl_rna_get_subclass_py |

## OperatorMacro(bpy_struct)

### OperatorMacro(bpy_struct) 

base class — bpy_struct

class bpy.types. OperatorMacro ( bpy_struct ) 

Holds a sub operator within a macro once it has been added

properties 

(readonly, never None)

Type :

OperatorProperties

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

## OperatorMousePath(PropertyGroup)

### OperatorMousePath(PropertyGroup) 

base classes — bpy_struct, PropertyGroup

class bpy.types. OperatorMousePath ( PropertyGroup ) 

Stored mouse-path values for operators that capture such paths

loc 

Mouse location (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

time 

Time of mouse location (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data | PropertyGroup.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values PropertyGroup.bl_system_properties_get PropertyGroup.bl_rna_get_subclass PropertyGroup.bl_rna_get_subclass_py |

## OperatorOptions(bpy_struct)

### OperatorOptions(bpy_struct) 

base class — bpy_struct

class bpy.types. OperatorOptions ( bpy_struct ) 

Runtime options

is_grab_cursor 

True while the cursor is grabbed (default False, readonly)

Type :

bool

is_invoke 

True when invoked (even if only the execute callbacks are available) (default False, readonly)

Type :

bool

is_repeat 

True while run from the ‘Adjust Last Operation’ panel (default False, readonly)

Type :

bool

is_repeat_last 

True while run from the operator ‘Repeat Last’ (default False, readonly)

Type :

bool

use_cursor_region 

Switch on to make modal execution use whichever region sits under the cursor (default False)

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

| Operator.options | |

## OperatorProperties(bpy_struct)

### OperatorProperties(bpy_struct) 

base class — bpy_struct

class bpy.types. OperatorProperties ( bpy_struct ) 

The input properties belonging to an operator

bl_system_properties_get ( * , do_create = False ) 

DEBUG ONLY. Internal hook into the runtime-defined RNA data storage, meant purely for testing and debugging. Steer clear of it in normal scripting, and in particular don't count on it holding writable data

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

| Gizmo.target_set_operator KeyConfigurations.find_item_from_operator KeyMapItem.properties KeyMapItems.find_from_operator Macro.properties Operator.description Operator.properties OperatorMacro.properties | UILayout.operator UILayout.operator_menu_enum UILayout.operator_menu_hold UILayout.template_popup_confirm WindowManager.operator_properties_last WorkSpaceTool.operator_properties XrActionMapItem.op_properties |

## OperatorStrokeElement(PropertyGroup)

### OperatorStrokeElement(PropertyGroup) 

base classes — bpy_struct, PropertyGroup

class bpy.types. OperatorStrokeElement ( PropertyGroup ) 

is_start 

(default False)

Type :

bool

location 

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

mouse 

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

mouse_event 

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

pressure 

Tablet pressure (in [0, 1], default 0.0)

Type :

float

size 

Brush size in screen space (in [0, inf], default 0.0)

Type :

float

time 

(in [0, inf], default 0.0)

Type :

float

x_tilt 

Pen tilt from left (-1.0) to right (+1.0) (in [-1, 1], default 0.0)

Type :

float

y_tilt 

Pen tilt from backward (-1.0) to forward (+1.0) (in [-1, 1], default 0.0)

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

| bpy_struct.id_data | PropertyGroup.name |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values PropertyGroup.bl_system_properties_get PropertyGroup.bl_rna_get_subclass PropertyGroup.bl_rna_get_subclass_py |

## PaintCurve(ID)

### PaintCurve(ID) 

base classes — bpy_struct, ID

class bpy.types. PaintCurve ( ID ) 

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| BlendData.paint_curves | Brush.paint_curve |

## Palette(ID)

### Palette(ID) 

base classes — bpy_struct, ID

class bpy.types. Palette ( ID ) 

colors 

(default None, readonly)

Type :

PaletteColors[PaletteColor]

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| BlendData.palettes BlendDataPalettes.new | BlendDataPalettes.remove Paint.palette |

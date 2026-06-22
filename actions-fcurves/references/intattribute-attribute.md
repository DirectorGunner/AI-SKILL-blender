# Intattribute Attribute, Intattributevalue Bpy Struct, Intproperty Property, Io Fh Gltf2 Filehandler ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: IntAttribute(Attribute); IntAttributeValue(bpy_struct); IntProperty(Property); `IO_FH`_gltf2(FileHandler); `IO_FH`_svg_as_curves(FileHandler); Itasc(IKParam); Key(ID); KeyConfig(bpy_struct); KeyConfigPreferences(bpy_struct); KeyConfigurations(bpy_prop_collection).

## IntAttribute(Attribute)

### IntAttribute(Attribute)

base classes — bpy_struct, Attribute

class bpy.types. IntAttribute ( Attribute )

A geometry attribute holding integer values.

data

(default None, readonly)

Type :

bpy_prop_collection[IntAttributeValue]

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

## IntAttributeValue(bpy_struct)

### IntAttributeValue(bpy_struct)

base class — bpy_struct

class bpy.types. IntAttributeValue ( bpy_struct )

An integer value within a geometry attribute.

value

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Curves.curve_offset_data GreasePencilDrawing.curve_offsets | IntAttribute.data |

## IntProperty(Property)

### IntProperty(Property)

base classes — bpy_struct, Property

class bpy.types. IntProperty ( Property )

The RNA definition of an integer-number property.

array_dimensions

The size of every dimension of the array (array of 3 items, in [0, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

array_length

The array's maximum length, where 0 means no limit (in [0, inf], default 0, readonly)

Type :

int

default

This number's default value (in [-inf, inf], default 0, readonly)

Type :

int

default_array

This array's default value (array of 3 items, in [-inf, inf], default (0, 0, 0), readonly)

Type :

bpy_prop_array[int]

hard_max

The buttons' upper limit (in [-inf, inf], default 0, readonly)

Type :

int

hard_min

The buttons' lower limit (in [-inf, inf], default 0, readonly)

Type :

int

is_array

(default False, readonly)

Type :

bool

soft_max

The buttons' upper limit (in [-inf, inf], default 0, readonly)

Type :

int

soft_min

The buttons' lower limit (in [-inf, inf], default 0, readonly)

Type :

int

step

The increment used by number buttons; for floats this is 1/100th of it (in [0, inf], default 0, readonly)

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

| bpy_struct.id_data Property.name Property.identifier Property.description Property.translation_context Property.type Property.subtype Property.srna Property.unit Property.icon Property.is_readonly Property.is_animatable Property.is_overridable Property.is_required Property.is_argument_optional Property.is_never_none Property.is_hidden | Property.is_skip_save Property.is_skip_preset Property.is_output Property.is_registered Property.is_registered_optional Property.is_runtime Property.is_enum_flag Property.is_library_editable Property.is_path_output Property.is_path_supports_blend_relative Property.is_path_supports_templates Property.is_deprecated Property.deprecated_note Property.deprecated_version Property.deprecated_removal_version Property.tags |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Property.bl_rna_get_subclass Property.bl_rna_get_subclass_py |

## `IO_FH`_gltf2(FileHandler)

### `IO_FH`_gltf2(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `IO_FH`_gltf2 ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## `IO_FH`_svg_as_curves(FileHandler)

### `IO_FH`_svg_as_curves(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `IO_FH`_svg_as_curves ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## Itasc(IKParam)

### Itasc(IKParam)

base classes — bpy_struct, IKParam

class bpy.types. Itasc ( IKParam )

Settings for the iTaSC IK solver.

damping_epsilon

The singular value below which damping ramps in (larger values trade reactivity for stability) (in [0, 1], default 0.0)

Type :

float

damping_max

The top damping coefficient applied as the singular value approaches 0 (larger values trade reactivity for stability) (in [0, 1], default 0.0)

Type :

float

feedback

The coefficient used to correct error; mean response time works out to 1/feedback (in [0, 100], default 0.0)

Type :

float

iterations

The cap on iterations toward convergence when reiterating (in [0, 1000], default 0)

Type :

int

mode

(default 'ANIMATION' )

- ANIMATION
Animation – Stateless solver computing pose starting from current action and non-IK constraints.

- SIMULATION
Simulation – State-full solver running in real-time context and ignoring actions and non-IK constraints.

Type :

Literal[‘ANIMATION’, ‘SIMULATION’]

precision

The convergence precision used while reiterating (in [0, 0.1], default 0.0)

Type :

float

reiteration_method

Sets whether the solver may reiterate (converge to the precision target) on no frames, only the first, or all of them (default 'NEVER' )

- NEVER
Never – The solver does not reiterate, not even on first frame (starts from rest pose).

- INITIAL
Initial – The solver reiterates (converges) on the first frame but not on subsequent frame.

- ALWAYS
Always – The solver reiterates (converges) on all frames.

Type :

Literal[‘NEVER’, ‘INITIAL’, ‘ALWAYS’]

solver

Pick the solving method: automatic or manual damping (default 'SDLS' )

- SDLS
SDLS – Selective Damped Least Square.

- DLS
DLS – Damped Least Square with Numerical Filtering.

Type :

Literal[‘SDLS’, ‘DLS’]

step_count

How many steps the frame interval is split into (in [1, 50], default 0)

Type :

int

step_max

The upper limit on the timestep, in seconds, for automatic substeps (in [0, 1], default 0.0)

Type :

float

step_min

The lower limit on the timestep, in seconds, for automatic substeps (in [0, 0.1], default 0.0)

Type :

float

translate_root_bones

Move root (that is, parentless) bones onto the armature origin (default False)

Type :

bool

use_auto_step

Work out the optimal step count automatically for the best speed/accuracy balance (default False)

Type :

bool

velocity_max

The top joint velocity, in radians per second (in [0, 100], default 0.0)

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

| bpy_struct.id_data | IKParam.ik_solver |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values IKParam.bl_rna_get_subclass IKParam.bl_rna_get_subclass_py |

## Key(ID)

### Key(ID)

base classes — bpy_struct, ID

class bpy.types. Key ( ID )

A shape-keys data-block holding the various shapes of geometric data-blocks.

animation_data

This data-block's animation data (readonly)

Type :

AnimData

eval_time

The evaluation time for absolute shape keys (in [0, 1.04857e+06], default 0.0)

Type :

float

key_blocks

The shape keys (default None, readonly)

Type :

bpy_prop_collection[ShapeKey]

reference_key

(readonly, never None)

Type :

ShapeKey

use_relative

Treat shape keys as relative; otherwise step through the shapes as a sequence using the evaluation time (default False)

Type :

bool

user

The data-block that draws on these shape keys (readonly, never None)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| BlendData.shape_keys Curve.shape_keys | Lattice.shape_keys Mesh.shape_keys |

## KeyConfig(bpy_struct)

### KeyConfig(bpy_struct)

base class — bpy_struct

class bpy.types. KeyConfig ( bpy_struct )

An input configuration, keymaps included.

is_user_defined

Marks a keyconfig as one the user created (default False, readonly)

Type :

bool

keymaps

The key maps set up as part of this configuration (default None, readonly)

Type :

KeyMaps[KeyMap]

name

The key configuration's name (default “”, never None)

Type :

str

preferences

(readonly)

Type :

KeyConfigPreferences

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

| GizmoGroup.setup_keymap KeyConfigurations.active KeyConfigurations.addon KeyConfigurations.default | KeyConfigurations.new KeyConfigurations.remove KeyConfigurations.user WindowManager.keyconfigs |

## KeyConfigPreferences(bpy_struct)

### KeyConfigPreferences(bpy_struct)

base class — bpy_struct

class bpy.types. KeyConfigPreferences ( bpy_struct )

bl_idname

(default “”, never None)

Type :

str

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

| KeyConfig.preferences | |

## KeyConfigurations(bpy_prop_collection)

### KeyConfigurations(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyConfigurations ( bpy_prop_collection )

A collection of KeyConfigs.

active

The active key configuration (preset)

Type :

KeyConfig

addon

A key configuration add-ons can extend, merged into the active configuration as events are handled (readonly)

Type :

KeyConfig

default

The built-in default key configuration (readonly)

Type :

KeyConfig

user

The final key configuration, blending keymaps from the active and add-on configurations and open to user edits (readonly)

Type :

KeyConfig

new ( name )

new

Parameters :

name ( str ) – Name, (never None)

Returns :

Key Configuration, Added key configuration

Return type :

KeyConfig

remove ( keyconfig )

remove

Parameters :

keyconfig (KeyConfig) – Key Configuration, Removed key configuration (never None)

find_item_from_operator ( idname , * , context = '`INVOKE_DEFAULT`' , properties = None , include = {'ACTIONZONE', 'KEYBOARD', 'MOUSE', 'NDOF'} , exclude = set() )

find_item_from_operator

Parameters :

- idname ( str ) – Operator Identifier, (never None)

- context (Literal[Operator Context Items]) – context, (optional)

- properties (OperatorProperties) – (optional)

- include (set[Literal[Event Type Mask Items]]) – Include, (optional)

- exclude (set[Literal[Event Type Mask Items]]) – Exclude, (optional)

Returns :

keymap , KeyMap

item , KeyMapItem

Return type :

tuple[KeyMap, KeyMapItem]

update ( * , keep_properties = False )

update

Parameters :

keep_properties ( bool ) – Keep Properties, Operator properties are kept to allow the operators to be registered again in the future (optional)

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

| WindowManager.keyconfigs | |

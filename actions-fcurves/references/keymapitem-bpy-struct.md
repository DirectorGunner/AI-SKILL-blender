# Keymapitem Bpy Struct, Keymapitems Bpy Prop Collection, Kinematicconstraint Constraint, Lattice Id ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: KeyMapItem(bpy_struct); KeyMapItems(bpy_prop_collection); KinematicConstraint(Constraint); Lattice(ID); LatticePoint(bpy_struct); LayerCollection(bpy_struct).

## KeyMapItem(bpy_struct)

### KeyMapItem(bpy_struct) 

base class — bpy_struct

class bpy.types. KeyMapItem ( bpy_struct ) 

A single entry within a Key Map

active 

Turn the item on or off (default False)

Type :

bool

alt 

Alt key pressed, -1 for any state (in [-1, 1], default 0)

Type :

int

alt_ui 

Alt key pressed (default False)

Type :

bool

any 

Any modifier keys pressed (default False)

Type :

bool

ctrl 

Control key pressed, -1 for any state (in [-1, 1], default 0)

Type :

int

ctrl_ui 

Control key pressed (default False)

Type :

bool

direction 

Which direction applies, used only for drag events (default 'ANY' )

Type :

Literal[Event Direction Items]

hyper 

Hyper key pressed, -1 for any state (in [-1, 1], default 0)

Type :

int

hyper_ui 

Hyper key pressed. On Linux this extra modifier can be set up, most often in place of CapsLock (default False)

Type :

bool

id 

The item's ID (in [-32768, 32767], default 0, readonly)

Type :

int

idname 

Name of the operator launched when the input event fires (default “”, never None)

Type :

str

is_user_defined 

Whether the user created this keymap item rather than it merely overriding a builtin one (default False, readonly)

Type :

bool

is_user_modified 

Whether the user has changed this keymap item (default False, readonly)

Type :

bool

key_modifier 

A normal key held down to act as a modifier (default 'NONE' )

Type :

Literal[Event Type Items]

map_type 

Which category of event is being mapped (default 'KEYBOARD' )

Type :

Literal[‘KEYBOARD’, ‘MOUSE’, ‘NDOF’, ‘TEXTINPUT’, ‘TIMER’]

name 

Translated name of the operator triggered by the input event (default “”, readonly, never None)

Type :

str

oskey 

Operating system key pressed, -1 for any state (in [-1, 1], default 0)

Type :

int

oskey_ui 

Operating system key pressed (default False)

Type :

bool

properties 

Values handed to the operator at call time (readonly)

Type :

OperatorProperties

propvalue 

What this event maps to inside a modal keymap (default 'NONE' )

Type :

Literal[Keymap Propvalue Items]

repeat 

Fires on key-repeat events, i.e. while a key stays held (default False)

Type :

bool

shift 

Shift key pressed, -1 for any state (in [-1, 1], default 0)

Type :

int

shift_ui 

Shift key pressed (default False)

Type :

bool

show_expanded 

Reveal the key map's event and property details in the interface (default False)

Type :

bool

type 

Which event this is (default 'NONE' )

Type :

Literal[Event Type Items]

value 

(default 'NOTHING' )

Type :

Literal[Event Value Items]

compare ( item ) 

compare

Parameters :

item (KeyMapItem) – Item

Returns :

Comparison result

Return type :

bool

to_string ( * , compact = False ) 

to_string

Parameters :

compact ( bool ) – Compact, (optional)

Returns :

result, (never None)

Return type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| KeyConfigurations.find_item_from_operator KeyMap.keymap_items KeyMap.restore_item_to_default KeyMapItem.compare KeyMapItems.find_from_operator KeyMapItems.find_match KeyMapItems.find_match KeyMapItems.from_id | KeyMapItems.match_event KeyMapItems.new KeyMapItems.new_from_item KeyMapItems.new_from_item KeyMapItems.new_modal KeyMapItems.remove UILayout.template_event_from_keymap_item UILayout.template_keymap_item_properties |

## KeyMapItems(bpy_prop_collection)

### KeyMapItems(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. KeyMapItems ( bpy_prop_collection ) 

The items contained in a keymap

new ( idname , type , value , * , any = False , shift = 0 , ctrl = 0 , alt = 0 , oskey = 0 , hyper = 0 , key_modifier = 'NONE' , direction = 'ANY' , repeat = False , head = False ) 

new

Parameters :

- idname ( str ) – Operator Identifier, (never None)

- type (Literal[Event Type Items]) – Type

- value (Literal[Event Value Items]) – Value

- any ( bool ) – Any, (optional)

- shift ( int ) – Shift, (in [-1, 1], optional)

- ctrl ( int ) – Ctrl, (in [-1, 1], optional)

- alt ( int ) – Alt, (in [-1, 1], optional)

- oskey ( int ) – OS Key, (in [-1, 1], optional)

- hyper ( int ) – Hyper, (in [-1, 1], optional)

- key_modifier (Literal[Event Type Items]) – Key Modifier, (optional)

- direction (Literal[Event Direction Items]) – Direction, (optional)

- repeat ( bool ) – Repeat, When set, accept key-repeat events (optional)

- head ( bool ) – At Head, Force item to be added at start (not end) of key map so that it doesn’t get blocked by an existing key map item (optional)

Returns :

Item, Added key map item

Return type :

KeyMapItem

new_modal ( propvalue , type , value , * , any = False , shift = 0 , ctrl = 0 , alt = 0 , oskey = 0 , hyper = 0 , key_modifier = 'NONE' , direction = 'ANY' , repeat = False ) 

new_modal

Parameters :

- propvalue ( str ) – Property Value, (never None)

- type (Literal[Event Type Items]) – Type

- value (Literal[Event Value Items]) – Value

- any ( bool ) – Any, (optional)

- shift ( int ) – Shift, (in [-1, 1], optional)

- ctrl ( int ) – Ctrl, (in [-1, 1], optional)

- alt ( int ) – Alt, (in [-1, 1], optional)

- oskey ( int ) – OS Key, (in [-1, 1], optional)

- hyper ( int ) – Hyper, (in [-1, 1], optional)

- key_modifier (Literal[Event Type Items]) – Key Modifier, (optional)

- direction (Literal[Event Direction Items]) – Direction, (optional)

- repeat ( bool ) – Repeat, When set, accept key-repeat events (optional)

Returns :

Item, Added key map item

Return type :

KeyMapItem

new_from_item ( item , * , head = False ) 

new_from_item

Parameters :

- item (KeyMapItem) – Item, Item to use as a reference (never None)

- head ( bool ) – At Head, (optional)

Returns :

Item, Added key map item

Return type :

KeyMapItem

remove ( item ) 

remove

Parameters :

item (KeyMapItem) – Item, (never None)

from_id ( id ) 

from_id

Parameters :

id ( int ) – id, ID of the item (in [-inf, inf])

Returns :

Item

Return type :

KeyMapItem

find_from_operator ( idname , * , properties = None , include = {'ACTIONZONE', 'KEYBOARD', 'MOUSE', 'NDOF'} , exclude = set() ) 

find_from_operator

Parameters :

- idname ( str ) – Operator Identifier, (never None)

- properties (OperatorProperties) – (optional)

- include (set[Literal[Event Type Mask Items]]) – Include, (optional)

- exclude (set[Literal[Event Type Mask Items]]) – Exclude, (optional)

Return type :

KeyMapItem

find_match ( keymap , item ) 

find_match

Parameters :

- keymap (KeyMap) – The matching keymap

- item (KeyMapItem) – The matching keymap item

Returns :

The keymap item from this keymap which matches the keymap item from the arguments passed in

Return type :

KeyMapItem

match_event ( event ) 

match_event

Return type :

KeyMapItem

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| KeyMap.keymap_items | |

## KinematicConstraint(Constraint)

### KinematicConstraint(Constraint) 

base classes — bpy_struct, Constraint

class bpy.types. KinematicConstraint ( Constraint ) 

Inverse Kinematics

chain_count 

Count of bones taking part in the IK effect; 0 means every bone is used (in [0, 255], default 0)

Type :

int

distance 

Radius of limiting sphere (in [0, 100], default 0.0)

Type :

float

ik_type 

(default '`COPY_POSE`' )

Type :

Literal[‘`COPY_POSE`’, ‘DISTANCE’]

iterations 

Cap on how many iterations the solver may run (in [0, 10000], default 0)

Type :

int

limit_mode 

Which distances relative to the sphere of influence are permitted (default '`LIMITDIST_INSIDE`' )

- `LIMITDIST_INSIDE`
Inside – The object is constrained inside a virtual sphere around the target object, with a radius defined by the limit distance.

- `LIMITDIST_OUTSIDE`
Outside – The object is constrained outside a virtual sphere around the target object, with a radius defined by the limit distance.

- `LIMITDIST_ONSURFACE`
On Surface – The object is constrained on the surface of a virtual sphere around the target object, with a radius defined by the limit distance.

Type :

Literal[‘`LIMITDIST_INSIDE`’, ‘`LIMITDIST_OUTSIDE`’, ‘`LIMITDIST_ONSURFACE`’]

lock_location_x 

Hold the position fixed on the X axis (default True)

Type :

bool

lock_location_y 

Hold the position fixed on the Y axis (default True)

Type :

bool

lock_location_z 

Hold the position fixed on the Z axis (default True)

Type :

bool

lock_rotation_x 

Hold the rotation fixed on the X axis (default True)

Type :

bool

lock_rotation_y 

Hold the rotation fixed on the Y axis (default True)

Type :

bool

lock_rotation_z 

Hold the rotation fixed on the Z axis (default True)

Type :

bool

orient_weight 

For Tree-IK: how heavily this target's orientation control counts (in [0.01, 1], default 0.0)

Type :

float

pole_angle 

Pole rotation offset (in [-3.14159, 3.14159], default 0.0)

Type :

float

pole_subtarget 

(default “”, never None)

Type :

str

pole_target 

Object for pole rotation

Type :

Object

reference_axis 

Whether the axis Lock options are taken relative to the Bone or to the Target reference (default 'BONE' )

Type :

Literal[‘BONE’, ‘TARGET’]

subtarget 

Armature bone, mesh or lattice vertex group, … (default “”, never None)

Type :

str

target 

Target object

Type :

Object

use_location 

Make the chain track the target's position (default False)

Type :

bool

use_rotation 

Make the chain track the target's rotation (default False)

Type :

bool

use_stretch 

Turn on IK Stretching (default False)

Type :

bool

use_tail 

Treat the bone's tail as the final link in the chain (default False)

Type :

bool

weight 

For Tree-IK: how heavily this target's position control counts (in [0.01, 1], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Constraint.name Constraint.type Constraint.is_override_data Constraint.owner_space Constraint.target_space Constraint.space_object Constraint.space_subtarget | Constraint.mute Constraint.enabled Constraint.show_expanded Constraint.is_valid Constraint.active Constraint.influence Constraint.error_location Constraint.error_rotation |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Constraint.bl_rna_get_subclass Constraint.bl_rna_get_subclass_py |

## Lattice(ID)

### Lattice(ID) 

base classes — bpy_struct, ID

class bpy.types. Lattice ( ID ) 

Lattice data-block defining a grid for deforming other objects

animation_data 

Animation data for this data-block (readonly)

Type :

AnimData

interpolation_type_u 

(default '`KEY_BSPLINE`' )

Type :

Literal[‘`KEY_LINEAR`’, ‘`KEY_CARDINAL`’, ‘`KEY_CATMULL_ROM`’, ‘`KEY_BSPLINE`’]

interpolation_type_v 

(default '`KEY_BSPLINE`' )

Type :

Literal[‘`KEY_LINEAR`’, ‘`KEY_CARDINAL`’, ‘`KEY_CATMULL_ROM`’, ‘`KEY_BSPLINE`’]

interpolation_type_w 

(default '`KEY_BSPLINE`' )

Type :

Literal[‘`KEY_LINEAR`’, ‘`KEY_CARDINAL`’, ‘`KEY_CATMULL_ROM`’, ‘`KEY_BSPLINE`’]

is_editmode 

True when the lattice is being used in edit mode (default False, readonly)

Type :

bool

points 

The grid points making up the lattice (default None, readonly)

Type :

bpy_prop_collection[LatticePoint]

points_u 

Point count along U (locked once shape keys exist) (in [1, 64], default 0)

Type :

int

points_v 

Point count along V (locked once shape keys exist) (in [1, 64], default 0)

Type :

int

points_w 

Point count along W (locked once shape keys exist) (in [1, 64], default 0)

Type :

int

shape_keys 

(readonly)

Type :

Key

use_outside 

Show and account for only the outermost vertices (default False)

Type :

bool

vertex_group 

Vertex group controlling where the lattice exerts its influence (default “”, never None)

Type :

str

transform ( matrix , * , shape_keys = False ) 

Apply a matrix transform to the lattice

Parameters :

- matrix (mathutils.Matrix) – Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- shape_keys ( bool ) – Transform Shape Keys (optional)

update_gpu_tag ( ) 

update_gpu_tag

unit_test_compare ( * , lattice = None , threshold = 7.1526e-06 ) 

unit_test_compare

Parameters :

- lattice (Lattice) – Lattice to compare to (optional)

- threshold ( float ) – Threshold, Comparison tolerance threshold (in [0, inf], optional)

Returns :

Return value, String description of result of comparison (never None)

Return type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.lattice BlendData.lattices BlendDataLattices.new | BlendDataLattices.remove Lattice.unit_test_compare |

## LatticePoint(bpy_struct)

### LatticePoint(bpy_struct) 

base class — bpy_struct

class bpy.types. LatticePoint ( bpy_struct ) 

One point of the lattice grid

co 

The point's rest position, before deformation, which drives how strong the deform effect is here (to edit or animate, use the Deformed Location instead) (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

co_deform 

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

groups 

This point's weights across the vertex groups it belongs to (default None, readonly)

Type :

bpy_prop_collection[VertexGroupElement]

select 

Whether the point is selected (default False)

Type :

bool

weight_softbody 

Softbody goal weight (in [0.01, 100], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| Lattice.points | |

## LayerCollection(bpy_struct)

### LayerCollection(bpy_struct) 

base class — bpy_struct

class bpy.types. LayerCollection ( bpy_struct ) 

Layer collection

children 

Nested layer collections of this one (default None, readonly)

Type :

bpy_prop_collection[LayerCollection]

collection 

The Collection that this layer collection wraps (readonly, never None)

Type :

Collection

exclude 

Leave this out of the view layer (default False)

Type :

bool

hide_viewport 

Hide in the viewport for now (default False)

Type :

bool

holdout 

Hold out the collection's objects from the view layer (default False)

Type :

bool

indirect_only 

Let the collection's objects contribute only indirectly, via shadows and reflections, within the view layer (default False)

Type :

bool

is_visible 

Whether this collection shows for the view layer, with the parent collection taken into account (default False, readonly)

Type :

bool

name 

Name of this layer collection (same as its collection one) (default “”, readonly, never None)

Type :

str

visible_get ( ) 

Whether this collection is visible, take into account the collection parent and the viewport

Return type :

bool

has_objects ( ) 

Return type :

bool

has_selected_objects ( view_layer ) 

Parameters :

view_layer (ViewLayer) – View layer the layer collection belongs to

Return type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| bpy.context.collection Context.layer_collection LayerCollection.children | ViewLayer.active_layer_collection ViewLayer.layer_collection |

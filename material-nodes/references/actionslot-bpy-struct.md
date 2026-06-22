# Actionslot Bpy Struct, Animdata Bpy Struct, Annotation Id, Arealight Light

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ActionSlot(bpy_struct); AnimData(bpy_struct); Annotation(ID); AreaLight(Light).

## ActionSlot(bpy_struct)

### ActionSlot(bpy_struct)

Action Slots organize animation data within an action. Each action has slots with specific animation
data. An animated data-block specifies an action and a slot, determining the animation data it uses.
See the Blender Manual for guidance on Action Slots, or the technical documentation for details on the animation system's structure.

### Create & Access an Action Slot

Begin by inserting a keyframe on an object to quickly set up Action Slots. Blender automatically builds an Action & Slot for that data-block.

import bpy

### Assume Suzanne mesh is present in the scene.
suzanne = bpy.data.objects["Suzanne"]

### Build animation data and an action for Suzanne:
### Slot will be automatically created.
suzanne.keyframe_insert("location", index=0)

### Action slots can be accessed like this:
action = suzanne.animation_data.action
for slot in action.slots:
print(f"Slot Identifier {slot.identifier!r} "
f"with name {slot.name_display!r} "
f"targets ID type {slot.target_id_type!r}")

### Manually Create an Action Slot

You may also manually build Action Slots on an Action. Take note of the target_id_type that matches the data-block type. Identifiers begin with a prefix determined by the ID type, e.g. "OB" for objects, then the name. Identifiers like OBSuzanne and MESuzanne can coexist, and the name (Suzanne) can be shared between them. This is intended, so that the slots and the datablocks can have the same name.

import bpy

### Actions creation.
action = bpy.data.actions.new("SuzanneAction")

### Creation of slots requires an ID type and a name.
slot = action.slots.new(id_type='OBJECT', name="Suzanne")
print(f"slot type={slot.target_id_type!r} "
f"name={slot.name_display!r} "
f"identifier={slot.identifier!r}")

### Output:
### slot type=OBJECT name=Suzanne identifier=OBSuzanne

### Explicitly Assigning Action Slots

An action slot is compatible with a data-block if the slot's target_id_type matches the data-block's type. If the Action holds multiple slots and you wish to select just the first matching one, apply the following. anim_data.action_suitable_slots becomes usable after the Action is assigned; it is a list of action slots from that Action, but only the ones that are truly compatible with the owner of anim_data (Suzanne in this example).

import bpy

### Assume Suzanne mesh is present in the scene.
suzanne = bpy.data.objects["Suzanne"]

### Build an action with an object slot.
action = bpy.data.actions.new("SuzanneAction")
action.slots.new(id_type='OBJECT', name="Suzanne")

### If several slots exist on the Action, pick the first one that's compatible.
anim_data = suzanne.animation_data_create()
anim_data.action = action
assert anim_data.action_suitable_slots, "expecting at least one suitable slot"
anim_data.action_slot = anim_data.action_suitable_slots[0]

### Finding Action Slot Users

To retrieve a list of the data-blocks animated by a particular slot of an Action, invoke the users() method of the ActionSlot.

import bpy

### Traverse all actions in the Blender data.
print("Action & slot users:")
for action in bpy.data.actions:
for slot in action.slots:
### Retrieve the data-blocks that are animated by this slot of this action
users = slot.users()
print(f"{action.name:20} slot={slot.identifier:12s} users: {users}")

base class — bpy_struct

class bpy.types.ActionSlot(bpy_struct)

An identifier for a set of channels in this Action that can be used by a data-block to specify what it is animated by

active

Whether this is the current slot, may be set by assigning to action.slots.active (default False, readonly)

Type: bool

handle

A number specific to this Slot, unique within the Action. This is used, for instance, on a ActionKeyframeStrip to look up the ActionChannelbag for this Slot

([-inf, inf], default 0, readonly)

Type: int

identifier

Used when linking an Action to a data-block, to locate the proper slot handle. This is the UI name, prepended by two characters determined by the slot's ID type (default "", never None)

Type: str

name_display

The display name of the slot. This name together with the slot's data-block type is unique within its Action (default "", never None)

Type: str

select

Whether the slot is selected (default False)

Type: bool

show_expanded

Whether the slot is expanded (default False)

Type: bool

target_id_type

The type of data-block this slot is meant to animate; assignable when 'UNSPECIFIED' but otherwise read-only (default 'UNSPECIFIED')

- ACTION
Action.

- ARMATURE
Armature.

- BRUSH
Brush.

- CACHEFILE
Cache File.

- CAMERA
Camera.

- COLLECTION
Collection.

- CURVE
Curve.

- CURVES
Curves.

- FONT
Font.

- GREASEPENCIL
Grease Pencil.

- `GREASEPENCIL_V3`
Grease Pencil v3.

- IMAGE
Image.

- KEY
Key.

- LATTICE
Lattice.

- LIBRARY
Library.

- LIGHT
Light.

- `LIGHT_PROBE`
Light Probe.

- LINESTYLE
Line Style.

- MASK
Mask.

- MATERIAL
Material.

- MESH
Mesh.

- META
Metaball.

- MOVIECLIP
Movie Clip.

- NODETREE
Node Tree.

- OBJECT
Object.

- PAINTCURVE
Paint Curve.

- PALETTE
Palette.

- PARTICLE
Particle.

- POINTCLOUD
Point Cloud.

- SCENE
Scene.

- SCREEN
Screen.

- SOUND
Sound.

- SPEAKER
Speaker.

- TEXT
Text.

- TEXTURE
Texture.

- VOLUME
Volume.

- WINDOWMANAGER
Window Manager.

- WORKSPACE
Workspace.

- WORLD
World.

- UNSPECIFIED
Unspecified – Not yet specified. When this slot is first assigned to a data-block, this will be set to the type of that data-block.

Type: Literal['ACTION', 'ARMATURE', 'BRUSH', 'CACHEFILE', 'CAMERA', 'COLLECTION', 'CURVE', 'CURVES', 'FONT', 'GREASEPENCIL', '`GREASEPENCIL_V3`', 'IMAGE', 'KEY', 'LATTICE', 'LIBRARY', 'LIGHT', '`LIGHT_PROBE`', 'LINESTYLE', 'MASK', 'MATERIAL', 'MESH', 'META', 'MOVIECLIP', 'NODETREE', 'OBJECT', 'PAINTCURVE', 'PALETTE', 'PARTICLE', 'POINTCLOUD', 'SCENE', 'SCREEN', 'SOUND', 'SPEAKER', 'TEXT', 'TEXTURE', 'VOLUME', 'WINDOWMANAGER', 'WORKSPACE', 'WORLD', 'UNSPECIFIED']

target_id_type_icon

([-inf, inf], default 0, readonly)

Type: int

users()

Retrieve the data-blocks that are animated by this slot of this action

Returns: users

Return type: bpy_prop_collection[ID]

duplicate()

Duplicate this slot, including all the animation data associated with it

Returns: Duplicated Slot, The slot created by duplicating this one

Return type: ActionSlot

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Action.slots ActionChannelbag.slot ActionChannelbags.new ActionConstraint.action_slot ActionConstraint.action_suitable_slots ActionKeyframeStrip.channelbag ActionKeyframeStrip.key_insert ActionSlot.duplicate | ActionSlots.active ActionSlots.new ActionSlots.remove AnimData.action_slot AnimData.action_suitable_slots NlaStrip.action_slot NlaStrip.action_suitable_slots |

### ActionSlots(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionSlots(bpy_prop_collection)

A set of action slots

active

Current slot for this action

Type: ActionSlot

new(id_type, name)

Introduce a slot into the Action

Parameters:

- id_type (Literal[Id Type Items]) – Data-block Type, The data-block type that the slot is intended for. This is combined with the slot name to create the slot's unique identifier, and is also used to limit (on a best-effort basis) which data-blocks the slot can be assigned to.

- name (str) – Name, Name of the slot. This will be made unique within the Action among slots of the same type (never None)

Returns: Newly created action slot

Return type: ActionSlot

remove(action_slot)

Erase the slot from the Action, including all animation linked to that slot

Parameters:

action_slot (ActionSlot) – Action Slot, The slot to remove

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Action.slots | |

## AnimData(bpy_struct)

### AnimData(bpy_struct)

base class — bpy_struct

class bpy.types.AnimData(bpy_struct)

Animation data associated with a data-block

action

Current Action for this data-block

Type: Action

action_blend_type

Approach for merging the Active Action's result with NLA stack output (default 'REPLACE')

- REPLACE
Replace – Stack values replace accumulated results based on influence.

- COMBINE
Combine – Stack values integrate with accumulated results using addition, multiplication, or quaternion operations per channel type.

- ADD
Add – Weighted stack result is summed with accumulated results.

- SUBTRACT
Subtract – Weighted stack result is subtracted from accumulated results.

- MULTIPLY
Multiply – Weighted stack result is multiplied into accumulated results.

Type: Literal['REPLACE', 'COMBINE', 'ADD', 'SUBTRACT', 'MULTIPLY']

action_extrapolation

Behavior past the Active Action's span (when evaluating with NLA) (default 'HOLD')

- NOTHING
Nothing – Stack has no effect outside its boundaries.

- HOLD
Hold – Maintain the first frame if no prior strips exist in the track, and always maintain the last frame.

- `HOLD_FORWARD`
Hold Forward – Maintain the last frame only.

Type: Literal['NOTHING', 'HOLD', '`HOLD_FORWARD`']

action_influence

Weight applied to the Active Action's contribution to the NLA stack result ([0, 1], default 1.0)

Type: float

action_slot

The slot that determines which subset of the Action is used by this data-block; its name locates the correct slot when a different Action is assigned

Type: ActionSlot

action_slot_handle

A number that determines which subset of the Action is used by this data-block ([-inf, inf], default 0)

Type: int

action_slot_handle_tweak_storage

A temporary holder for the main action slot during tweak mode ([-inf, inf], default 0)

Type: int

action_suitable_slots

The set of slots within this animation data-block (default None, readonly)

Type: bpy_prop_collection[ActionSlot]

action_tweak_storage

A temporary holder for the main action during tweak mode

Type: Action

drivers

The Drivers/Expressions assigned to this data-block (default None, readonly)

Type: AnimDataDrivers[FCurve]

last_slot_identifier

The identifier of the most recently assigned action slot. The slot that determines which subset of the Action is used by this data-block, and its identifier is used to locate the correct slot when a different Action is assigned. (default "", never None)

Type: str

nla_tracks

NLA Tracks (animation Layers) (default None, readonly)

Type: NlaTracks[NlaTrack]

use_nla

The NLA stack is evaluated when processing this block (default True)

Type: bool

use_pin

(default False)

Type: bool

use_tweak_mode

Whether to turn on or off tweak mode in NLA (default False)

Type: bool

nla_tweak_strip_time_to_scene(frame, *, invert=False)

Translate a time from the tweaked strip's local time to scene time, exactly like built-in key editing tools. Leaves time unchanged if not in tweak mode.

Parameters:

- frame (float) – Input time ([-1.04857e+06, 1.04857e+06])

- invert (bool) – Invert, Translate scene time to action time (optional)

Returns: Translated time ([-1.04857e+06, 1.04857e+06])

Return type: float

fix_paths_rename_all(*, prefix='', old_name='', new_name='')

Update the property paths in the animation system, since properties are animated through string paths, updates are necessary to keep them valid after properties are renamed

Parameters:

- prefix (str) – Prefix, Name prefix (optional, never None)

- old_name (str) – Old Name, Old name (optional, never None)

- new_name (str) – New Name, New name (optional, never None)

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns: The RNA type or default when not found.

Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:

- id (str) – The RNA type identifier.

- default (type | None) – The value to return when not found.

Returns: The class or default when not found.

Return type: type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Annotation.animation_data Armature.animation_data CacheFile.animation_data Camera.animation_data Curve.animation_data Curves.animation_data FreestyleLineStyle.animation_data GreasePencil.animation_data ID.animation_data_create Key.animation_data Lattice.animation_data Light.animation_data LightProbe.animation_data Mask.animation_data | Material.animation_data Mesh.animation_data MetaBall.animation_data MovieClip.animation_data NodeTree.animation_data Object.animation_data ParticleSettings.animation_data PointCloud.animation_data Scene.animation_data Speaker.animation_data Texture.animation_data Volume.animation_data World.animation_data |

## Annotation(ID)

Data block for freehand sketched notes.

base classes — bpy_struct, ID

class bpy.types. Annotation ( ID )

Freehand sketched annotation storage.

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

layers

(default None, readonly)

Type :

AnnotationLayers[AnnotationLayer]

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

| BlendData.annotations BlendDataAnnotations.new BlendDataAnnotations.remove MovieClip.annotation MovieTrackingTrack.annotation | NodeTree.annotation Scene.annotation SpaceImageEditor.annotation SpaceSequenceEditor.annotation |

## AreaLight(Light)

A light source emitting from a rectangular surface.

base classes — bpy_struct, ID, Light

class bpy.types. AreaLight ( Light )

A light emitting from a rectangular plane.

energy

Light energy emitted over the entire area of the light in all directions, in units of radiant power (W) (in [-inf, inf], default 10.0)

Type :

float

shadow_buffer_clip_start

Shadow map clip start, below which objects will not generate shadows (in [1e-06, inf], default 0.05)

Type :

float

shadow_filter_radius

Blur shadow aliasing using Percentage Closer Filtering (in [0, inf], default 1.0)

Type :

float

shadow_jitter_overblur

Apply shadow tracing to each jittered sample to reduce under-sampling artifacts (in [0, 100], default 10.0)

Type :

float

shadow_maximum_resolution

Minimum size of a shadow map pixel. Higher values use less memory at the cost of shadow quality. (in [0, inf], default 0.001)

Type :

float

shadow_soft_size

Light size for ray shadow sampling (Raytraced shadows) (in [0, inf], default 0.0)

Type :

float

shape

Shape of the area Light (default 'SQUARE' )

Type :

Literal['SQUARE', 'RECTANGLE', 'DISK', 'ELLIPSE']

size

Size of the area of the area light, X direction size for rectangle shapes (in [0, inf], default 0.25)

Type :

float

size_y

Size of the area of the area light in the Y direction for rectangle shapes (in [0, inf], default 0.25)

Type :

float

spread

How widely the emitted light fans out, as in the case of a gridded softbox (in [0, 3.14159], default 3.14159)

Type :

float

use_absolute_resolution

Limit the resolution at 1 unit from the light origin instead of relative to the shadowed pixel (default False)

Type :

bool

use_shadow_jitter

Enable jittered soft shadows to increase shadow precision (disabled in viewport unless enabled in the render settings). Has a high performance impact. (default False)

Type :

bool

inline_shader_nodes ( )

Get the inlined shader nodes of this light. This preprocesses the node tree
to remove nested groups, repeat zones and more.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data | ID.override_library ID.preview Light.type Light.use_temperature Light.color Light.temperature Light.temperature_color Light.specular_factor Light.diffuse_factor Light.transmission_factor Light.volume_factor Light.use_custom_distance Light.cutoff_distance Light.use_shadow Light.exposure Light.normalize Light.node_tree Light.use_nodes Light.animation_data Light.cycles |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Light.area Light.inline_shader_nodes Light.bl_rna_get_subclass Light.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)

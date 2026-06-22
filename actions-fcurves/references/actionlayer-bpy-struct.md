# Actionlayer Bpy Struct, Actionlayers Bpy Prop Collection, Actionposemarkers Bpy Prop Collection, Actionslots Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ActionLayer(bpy_struct); ActionLayers(bpy_prop_collection); ActionPoseMarkers(bpy_prop_collection); ActionSlots(bpy_prop_collection); ActionStrip(bpy_struct); ActionStrips(bpy_prop_collection); Addon(bpy_struct); AddonPreferences(bpy_struct); Addons(bpy_prop_collection).

## ActionLayer(bpy_struct)

### ActionLayer(bpy_struct)

base class — bpy_struct

class bpy.types.ActionLayer(bpy_struct)

name

(default "", never None)

Type: str

strips

The collection of strips present on this animation layer (default None, readonly)

Type: ActionStrips[ActionStrip]

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

| Action.layers ActionLayers.new | ActionLayers.remove |

## ActionLayers(bpy_prop_collection)

### ActionLayers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionLayers(bpy_prop_collection)

A set of animation layers

new(name)

Introduce a layer into the Animation. Currently an Animation may hold at most one layer.

Parameters:

name (str) – Name, Name of the layer, will be made unique within the Action (never None)

Returns: Newly created animation layer

Return type: ActionLayer

remove(anim_layer)

Erase the layer from the animation

Parameters:

anim_layer (ActionLayer) – Animation Layer, The layer to remove

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

| Action.layers | |

## ActionPoseMarkers(bpy_prop_collection)

### ActionPoseMarkers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionPoseMarkers(bpy_prop_collection)

A set of timeline markers

active

Current pose marker for this action

Type: TimelineMarker

active_index

Index of the current pose marker ([0, inf], default 0)

Type: int

new(name)

Append a pose marker to the action

Parameters:

name (str) – New name for the marker (not required to be unique) (never None)

Returns: Newly created marker

Return type: TimelineMarker

remove(marker)

Erase a timeline marker

Parameters:

marker (TimelineMarker) – Timeline marker to remove (never None)

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

| Action.pose_markers | |

## ActionSlots(bpy_prop_collection)

### ActionSlots(bpy_prop_collection)
base classes — bpy_prop, bpy_prop_collection

class bpy.types. ActionSlots ( bpy_prop_collection )
A collection of action slots.

active
The active slot for this action.
Type: ActionSlot

new ( id_type , name )
Adds a slot to the Action.
Parameters:
- id_type (Literal[Id Type Items]) – Data-block Type, The data-block type that the slot is intended for. This is combined with the slot name to create the slot's unique identifier, and is also used to limit (on a best-effort basis) which data-blocks the slot can be assigned to.
- name ( str ) – Name, Name of the slot. This will be made unique within the Action among slots of the same type (never None)
Returns: Newly created action slot
Return type: ActionSlot

remove ( action_slot )
Removes the slot from the Action, including all animation associated with that slot.
Parameters: action_slot (ActionSlot) – Action Slot, The slot to remove

classmethod bl_rna_get_subclass ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.
Returns: The RNA type or default when not found.
Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default ( type | None ) – The value to return when not found.
Returns: The class or default when not found.
Return type: type

### Inherited Properties
| bpy_struct.id_data | |

### Inherited Functions
| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References
| Action.slots | |

## ActionStrip(bpy_struct)

### ActionStrips(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types.ActionStrips(bpy_prop_collection)

A set of animation strips

new(*, type='KEYFRAME')

Introduce a new strip onto the layer. Currently a layer may contain only one strip, with unbounded span.

Parameters:

type (Literal['KEYFRAME']) – Type, The kind of strip to build (optional)

- KEYFRAME
Keyframe – A strip containing keyframes on F-Curves.

Returns: Newly created animation strip

Return type: ActionStrip

remove(anim_strip)

Erase the strip from the animation layer

Parameters:

anim_strip (ActionStrip) – Animation Strip, The strip to remove

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

| ActionLayer.strips | |

## ActionStrips(bpy_prop_collection)

### Addon(bpy_struct)

base class — bpy_struct

class bpy.types.Addon(bpy_struct)

Python modules that are loaded on startup

module

The identifier of the module (default "", never None)

Type: str

preferences

(readonly)

Type: AddonPreferences

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

| Addons.new Addons.remove | Preferences.addons |

## Addon(bpy_struct)

### AddonPreferences(bpy_struct)

bl_info = {
"name": "Example Add-on Preferences",
"author": "Your Name Here",
"version": (1, 0),
"blender": (2, 65, 0),
"location": "SpaceBar Search -> Add-on Preferences Example",
"description": "Example Add-on",
"warning": "",
"doc_url": "",
"tracker_url": "",
"category": "Object",
}

import bpy
from bpy.types import Operator, AddonPreferences
from bpy.props import StringProperty, IntProperty, BoolProperty

class ExampleAddonPreferences(AddonPreferences):
### This must match the add-on name, use `__package__`
### when defining this for add-on extensions or a sub-module of a Python package.
bl_idname = __name__

filepath: StringProperty(
name="Example File Path",
subtype='`FILE_PATH`',
)
number: IntProperty(
name="Example Number",
default=4,
)
boolean: BoolProperty(
name="Example Boolean",
default=False,
)

def draw(self, context):
layout = self.layout
layout.label(text="This is a preferences view for our add-on")
layout.prop(self, "filepath")
layout.prop(self, "number")
layout.prop(self, "boolean")

class `OBJECT_OT`_addon_prefs_example(Operator):
"""Display example preferences"""
bl_idname = "object.addon_prefs_example"
bl_label = "Add-on Preferences Example"
bl_options = {'REGISTER', 'UNDO'}

def execute(self, context):
preferences = context.preferences
addon_prefs = preferences.addons[__name__].preferences

info = "Path: {:s}, Number: {:d}, Boolean {!r}".format(
addon_prefs.filepath, addon_prefs.number, addon_prefs.boolean,
)
self.report({'INFO'}, info)
print(info)

return {'FINISHED'}

### Registration
def register():
bpy.utils.register_class(`OBJECT_OT`_addon_prefs_example)
bpy.utils.register_class(ExampleAddonPreferences)

def unregister():
bpy.utils.unregister_class(`OBJECT_OT`_addon_prefs_example)
bpy.utils.unregister_class(ExampleAddonPreferences)

base class — bpy_struct

class bpy.types.AddonPreferences(bpy_struct)

bl_idname

(default "", never None)

Type: str

bl_system_properties_get(*, do_create=False)

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters:

do_create (bool) – Ensure that system properties are created if they do not exist yet (optional)

Returns: The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type: PropertyGroup

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

| Addon.preferences | |

## AddonPreferences(bpy_struct)

### AddonPreferences(bpy_struct)
```python
bl_info = {
    "name": "Example Add-on Preferences",
    "author": "Your Name Here",
    "version": (1, 0),
    "blender": (2, 65, 0),
    "location": "SpaceBar Search -> Add-on Preferences Example",
    "description": "Example Add-on",
    "warning": "",
    "doc_url": "",
    "tracker_url": "",
    "category": "Object",
}

import bpy
from bpy.types import Operator, AddonPreferences
from bpy.props import StringProperty, IntProperty, BoolProperty

class ExampleAddonPreferences(AddonPreferences):
    # This must match the add-on name, use `__package__`
    # when defining this for add-on extensions or a sub-module of a Python package.
    bl_idname = __name__

    filepath: StringProperty(
        name="Example File Path",
        subtype='FILE_PATH',
    )
    number: IntProperty(
        name="Example Number",
        default=4,
    )
    boolean: BoolProperty(
        name="Example Boolean",
        default=False,
    )

    def draw(self, context):
        layout = self.layout
        layout.label(text="This is a preferences view for our add-on")
        layout.prop(self, "filepath")
        layout.prop(self, "number")
        layout.prop(self, "boolean")

class OBJECT_OT_addon_prefs_example(Operator):
    """Display example preferences"""
    bl_idname = "object.addon_prefs_example"
    bl_label = "Add-on Preferences Example"
    bl_options = {'REGISTER', 'UNDO'}

    def execute(self, context):
        preferences = context.preferences
        addon_prefs = preferences.addons[__name__].preferences

        info = "Path: {:s}, Number: {:d}, Boolean {!r}".format(
            addon_prefs.filepath, addon_prefs.number, addon_prefs.boolean,
        )
        self.report({'INFO'}, info)
        print(info)

        return {'FINISHED'}

# Registration
def register():
    bpy.utils.register_class(OBJECT_OT_addon_prefs_example)
    bpy.utils.register_class(ExampleAddonPreferences)

def unregister():
    bpy.utils.unregister_class(OBJECT_OT_addon_prefs_example)
    bpy.utils.unregister_class(ExampleAddonPreferences)
```

base class — bpy_struct

class bpy.types. AddonPreferences ( bpy_struct )

bl_idname
(default "", never None)
Type: str

bl_system_properties_get ( * , do_create = False )
DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular do not assume that it contains writable data.
Parameters: do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)
Returns: The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested.
Return type: PropertyGroup

classmethod bl_rna_get_subclass ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.
Returns: The RNA type or default when not found.
Return type: bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )
Parameters:
- id ( str ) – The RNA type identifier.
- default ( type | None ) – The value to return when not found.
Returns: The class or default when not found.
Return type: type

### Inherited Properties
| bpy_struct.id_data | |

### Inherited Functions
| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References
| Addon.preferences | |

## Addons(bpy_prop_collection)

### AddStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types.AddStrip(EffectStrip)

Add Strip

input_1

The initial contribution to the effect strip (never None)

Type: Strip

input_2

The secondary contribution to the effect strip (never None)

Type: Strip

input_count

([0, inf], default 0, readonly)

Type: int

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

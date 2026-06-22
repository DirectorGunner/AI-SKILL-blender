# Greasepenciltintmodifier Modifier, Greasepenciltreenode Bpy Struct, Greasepencilv3Layergroup Bpy Prop Collection, Greasepencilweightanglemodifier Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GreasePencilTintModifier(Modifier); GreasePencilTreeNode(bpy_struct); GreasePencilv3LayerGroup(bpy_prop_collection); GreasePencilWeightAngleModifier(Modifier); GreasePencilWeightProximityModifier(Modifier); Histogram(bpy_struct); HydraRenderEngine(RenderEngine).

## GreasePencilTintModifier(Modifier)

### GreasePencilTintModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilTintModifier ( Modifier )

color

Color used for tinting (array of 3 items, in [0, 1], default (1.0, 1.0, 1.0))

Type :

mathutils.Color

color_mode

Attributes to modify (default 'BOTH' )

- BOTH
Stroke & Fill – Affect the colors of both fill and stroke.

- STROKE
Stroke – Affect the stroke color alone.

- FILL
Fill – Affect the fill color alone.

Type :

Literal['BOTH', 'STROKE', 'FILL']

color_ramp

Gradient tinting colors (readonly)

Type :

ColorRamp

custom_curve

Custom curve to apply effect (readonly)

Type :

CurveMapping

factor

Factor for tinting (in [0, 2], default 0.5)

Type :

float

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

object

Object used for the gradient direction

Type :

Object

open_influence_panel

(default False)

Type :

bool

radius

Influence distance from the object (in [1e-06, inf], default 1.0)

Type :

float

tint_mode

(default 'UNIFORM' )

Type :

Literal['UNIFORM', 'GRADIENT']

tree_node_filter

Layer name (default "", never None)

Type :

str

use_custom_curve

Use a custom curve to define a factor along the strokes (default False)

Type :

bool

use_layer_group_filter

Filter by layer group name (default False)

Type :

bool

use_layer_pass_filter

Use layer pass filter (default False)

Type :

bool

use_material_pass_filter

Use material pass filter (default False)

Type :

bool

use_weight_as_factor

Use vertex group weight as factor instead of influence (default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## GreasePencilTreeNode(bpy_struct)

### GreasePencilTreeNode(bpy_struct)

base class — bpy_struct

subclasses —
GreasePencilLayer, GreasePencilLayerGroup

class bpy.types. GreasePencilTreeNode ( bpy_struct )

An entry in the Grease Pencil layer tree, representing either a single layer or a group.

channel_color

Color of the channel in the dope sheet (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

hide

Set tree node visibility (default False)

Type :

bool

lock

Protect tree node from editing (default False)

Type :

bool

name

The name of the tree node (default "", never None)

Type :

str

next_node

The tree node sitting just after (above) this one in the layer tree (readonly)

Type :

GreasePencilTreeNode

parent_group

The group that contains this layer tree node (readonly)

Type :

GreasePencilLayerGroup

prev_node

The tree node sitting just before (below) this one in the layer tree (readonly)

Type :

GreasePencilTreeNode

select

Tree node is selected (default False)

Type :

bool

use_masks

Let the layers in the masks list drive how drawings in this tree node show or hide (default True)

Type :

bool

use_onion_skinning

Show onion skins on either side of the current frame (default True)

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

| GreasePencil.root_nodes GreasePencilLayerGroup.children | GreasePencilTreeNode.next_node GreasePencilTreeNode.prev_node |

## GreasePencilv3LayerGroup(bpy_prop_collection)

### GreasePencilv3LayerGroup(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. GreasePencilv3LayerGroup ( bpy_prop_collection )

A set of Grease Pencil layers grouped together.

active

Active Grease Pencil layer group

Type :

GreasePencilLayerGroup

new ( name , * , parent_group = None )

Create another Grease Pencil layer group.

Parameters :

- name ( str ) – Name, Name of the layer group (never None)

- parent_group (GreasePencilLayerGroup) – The parent layer group the new group will be created in (use None for the main stack) (optional)

Returns :

The newly created layer group

Return type :

GreasePencilLayerGroup

remove ( layer_group , * , keep_children = False )

Delete a Grease Pencil layer group.

Parameters :

- layer_group (GreasePencilLayerGroup) – The layer group to remove (never None)

- keep_children ( bool ) – Keep the children nodes of the group and only delete the group itself (optional)

move ( layer_group , type )

Shift a layer group within its parent group or the main stack.

Parameters :

- layer_group (GreasePencilLayerGroup) – The layer group to move (never None)

- type ( Literal [ 'DOWN' , 'UP' ] ) – Direction of movement

move_top ( layer_group )

Send a layer group up to the top of its parent group or the main stack.

Parameters :

layer_group (GreasePencilLayerGroup) – The layer group to move (never None)

move_bottom ( layer_group )

Send a layer group down to the bottom of its parent group or the main stack.

Parameters :

layer_group (GreasePencilLayerGroup) – The layer group to move (never None)

move_to_layer_group ( layer_group , parent_group )

Relocate a layer group inside a parent layer group.

Parameters :

- layer_group (GreasePencilLayerGroup) – The layer group to move (never None)

- parent_group (GreasePencilLayerGroup) – The parent layer group the layer group will be moved into (use None for the main stack)

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

| GreasePencil.layer_groups | |

## GreasePencilWeightAngleModifier(Modifier)

### GreasePencilWeightAngleModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilWeightAngleModifier ( Modifier )

Computes vertex weights on the fly from stroke orientation.

angle

Angle (in [0, 3.14159], default 0.0)

Type :

float

axis

(default 'Y' )

Type :

Literal['X', 'Y', 'Z']

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

minimum_weight

Minimum value for vertex weight (in [0, 1], default 0.0)

Type :

float

open_influence_panel

(default False)

Type :

bool

space

Coordinates space (default 'LOCAL' )

Type :

Literal['LOCAL', 'WORLD']

target_vertex_group

Output Vertex group (default "", never None)

Type :

str

tree_node_filter

Layer name (default "", never None)

Type :

str

use_invert_output

Invert output weight values (default False)

Type :

bool

use_layer_group_filter

Filter by layer group name (default False)

Type :

bool

use_layer_pass_filter

Use layer pass filter (default False)

Type :

bool

use_material_pass_filter

Use material pass filter (default False)

Type :

bool

use_multiply

Multiply the calculated weights with the existing values in the vertex group (default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## GreasePencilWeightProximityModifier(Modifier)

### GreasePencilWeightProximityModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. GreasePencilWeightProximityModifier ( Modifier )

Computes vertex weights on the fly from distance to a reference.

distance_end

Distance mapping to 1.0 weight (in [0, inf], default 20.0)

Type :

float

distance_start

Distance mapping to 0.0 weight (in [0, inf], default 0.0)

Type :

float

invert_layer_filter

Invert layer filter (default False)

Type :

bool

invert_layer_pass_filter

Invert layer pass filter (default False)

Type :

bool

invert_material_filter

Invert material filter (default False)

Type :

bool

invert_material_pass_filter

Invert material pass filter (default False)

Type :

bool

invert_vertex_group

Invert vertex group weights (default False)

Type :

bool

layer_pass_filter

Layer pass filter (in [0, 100], default 0)

Type :

int

material_filter

Material used for filtering

Type :

Material

material_pass_filter

Material pass (in [0, 100], default 0)

Type :

int

minimum_weight

Minimum value for vertex weight (in [0, 1], default 0.0)

Type :

float

object

Object used as distance reference

Type :

Object

open_influence_panel

(default False)

Type :

bool

target_vertex_group

Output Vertex group (default "", never None)

Type :

str

tree_node_filter

Layer name (default "", never None)

Type :

str

use_invert_output

Invert output weight values (default False)

Type :

bool

use_layer_group_filter

Filter by layer group name (default False)

Type :

bool

use_layer_pass_filter

Use layer pass filter (default False)

Type :

bool

use_material_pass_filter

Use material pass filter (default False)

Type :

bool

use_multiply

Multiply the calculated weights with the existing values in the vertex group (default False)

Type :

bool

vertex_group_name

Vertex group name for modulating the deform (default "", never None)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## Histogram(bpy_struct)

### Histogram(bpy_struct)

base class — bpy_struct

class bpy.types. Histogram ( bpy_struct )

A graph showing the distribution of color levels across an image.

mode

Channels to display in the histogram (default 'LUMA' )

- LUMA
Luma – Luma.

- RGB
RGB – Red Green Blue.

- R
R – Red.

- G
G – Green.

- B
B – Blue.

- A
A – Alpha.

Type :

Literal['LUMA', 'RGB', 'R', 'G', 'B', 'A']

show_line

Display lines rather than filled shapes (default False)

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

| Scopes.histogram | SpaceImageEditor.sample_histogram |

## HydraRenderEngine(RenderEngine)

### HydraRenderEngine(RenderEngine)

Base class for plugging USD Hydra renderers into Blender.

### USD Hydra Based Renderer

`text
import bpy

class CustomHydraRenderEngine(bpy.types.HydraRenderEngine):
### Identifier and name in the user interface.
bl_idname = "`CUSTOM_HYDRA_RENDERER`"
bl_label = "Custom Hydra Renderer"

### Name of the render plugin.
bl_delegate_id = "HdCustomRendererPlugin"

### Use MaterialX instead of `UsdPreviewSurface` for materials.
bl_use_materialx = True

### Register path to plugin.
@classmethod
def register(cls):
### Make `pxr` module available, for running as `bpy` PIP package.
bpy.utils.expose_bundled_modules()

import pxr.Plug
pxr.Plug.Registry().RegisterPlugins(['/path/to/plugin'])

### Render settings that will be passed to the delegate.
def get_render_settings(self, engine_type):
return {
'myBoolean': True,
'myValue': 8,
'aovToken:Depth': "depth",
}

### RenderEngine methods for update, render and draw are implemented in
### HydraRenderEngine. Optionally extra work can be done before or after
### by implementing the methods like this.
def update(self, data, depsgraph):
super().update(data, depsgraph)
### Do extra work here.

def update_render_passes(self, scene, render_layer):
if render_layer.use_pass_z:
self.register_pass(scene, render_layer, 'Depth', 1, 'Z', 'VALUE')

### Registration.
def register():
bpy.utils.register_class(CustomHydraRenderEngine)

def unregister():
bpy.utils.unregister_class(CustomHydraRenderEngine)

if __name__ == "__main__":
register()
`

base classes — bpy_struct, RenderEngine

class bpy.types. HydraRenderEngine ( RenderEngine )

Base class from USD Hydra based renderers

get_render_settings ( engine_type : str )

Provide render settings for HdRenderDelegate .

render ( depsgraph )

update ( data , depsgraph )

view_draw ( context , depsgraph )

view_update ( context , depsgraph )

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

| bpy_struct.id_data RenderEngine.is_animation RenderEngine.is_preview RenderEngine.camera_override RenderEngine.layer_override RenderEngine.resolution_x RenderEngine.resolution_y RenderEngine.temporary_directory RenderEngine.render RenderEngine.use_highlight_tiles RenderEngine.bl_idname | RenderEngine.bl_label RenderEngine.bl_use_preview RenderEngine.bl_use_postprocess RenderEngine.bl_use_eevee_viewport RenderEngine.bl_use_custom_freestyle RenderEngine.bl_use_image_save RenderEngine.bl_use_gpu_context RenderEngine.bl_use_shading_nodes_custom RenderEngine.bl_use_spherical_stereo RenderEngine.bl_use_stereo_viewport RenderEngine.bl_use_materialx |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values RenderEngine.update RenderEngine.render RenderEngine.render_frame_finish RenderEngine.draw RenderEngine.bake RenderEngine.view_update RenderEngine.view_draw RenderEngine.update_script_node | RenderEngine.update_render_passes RenderEngine.update_custom_camera RenderEngine.tag_redraw RenderEngine.tag_update RenderEngine.begin_result RenderEngine.update_result RenderEngine.end_result RenderEngine.add_pass RenderEngine.get_result RenderEngine.test_break RenderEngine.pass_by_index_get RenderEngine.active_view_get RenderEngine.active_view_set RenderEngine.camera_shift_x RenderEngine.camera_model_matrix RenderEngine.use_spherical_stereo RenderEngine.update_stats RenderEngine.frame_set RenderEngine.update_progress RenderEngine.update_memory_stats RenderEngine.report RenderEngine.error_set RenderEngine.bind_display_space_shader RenderEngine.unbind_display_space_shader RenderEngine.support_display_space_shader RenderEngine.get_preview_pixel_size RenderEngine.free_blender_memory RenderEngine.tile_highlight_set RenderEngine.tile_highlight_clear_all RenderEngine.register_pass RenderEngine.bl_rna_get_subclass RenderEngine.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)

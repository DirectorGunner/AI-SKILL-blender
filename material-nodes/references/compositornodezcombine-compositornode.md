# Compositornodezcombine Compositornode, Context Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: CompositorNodeZcombine(CompositorNode); Context(bpy_struct).

## CompositorNodeZcombine(CompositorNode)

### CompositorNodeZcombine(CompositorNode)

base classes — bpy_struct, Node, NodeInternal, CompositorNode

class bpy.types. CompositorNodeZcombine ( CompositorNode )

Merges a pair of images guided by their depth maps.

classmethod is_registered_node_type ( )

Returns True when the node type has been registered.

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Template describing an input socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Template describing an output socket.

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py CompositorNode.poll CompositorNode.bl_rna_get_subclass CompositorNode.bl_rna_get_subclass_py |

## Context(bpy_struct)

### Context(bpy_struct)

base class — bpy_struct

class bpy.types. Context ( bpy_struct )

The live data context together with the active window manager.

area

(readonly)

Type :

Area

asset

(readonly)

Type :

AssetRepresentation

blend_data

(readonly)

Type :

BlendData

collection

(readonly)

Type :

Collection

engine

(default "", readonly, never None)

Type :

str

gizmo_group

(readonly)

Type :

GizmoGroup

layer_collection

(readonly)

Type :

LayerCollection

mode

(default '`EDIT_MESH`' , readonly)

Type :

Literal[Context Mode Items]

preferences

(readonly)

Type :

Preferences

region

(readonly)

Type :

Region

region_data

(readonly)

Type :

RegionView3D

region_popup

The short-lived region behind pop-ups such as menus and pop-overs (readonly)

Type :

Region

scene

(readonly)

Type :

Scene

screen

(readonly)

Type :

Screen

space_data

Whatever space is currently active; this can come back None in background mode, when the pointer sits outside the window, or while menu-search is in use (readonly)

Type :

Space

tool_settings

(readonly)

Type :

ToolSettings

view_layer

(readonly)

Type :

ViewLayer

window

(readonly)

Type :

Window

window_manager

(readonly)

Type :

WindowManager

workspace

(readonly)

Type :

WorkSpace

Buttons Context

texture_slot

Type :

TextureSlot

scene

Type :

Scene

world

Type :

World

object

Type :

Object

mesh

Type :

Mesh

armature

Type :

Armature

lattice

Type :

Lattice

curve

Type :

Curve

meta_ball

Type :

MetaBall

light

Type :

Light

speaker

Type :

Speaker

lightprobe

Type :

LightProbe

camera

Type :

Camera

material

Type :

Material

material_slot

Type :

MaterialSlot

texture

Type :

Texture

texture_user

Type :

ID

texture_user_property

Type :

Property

texture_node

Type :

Node

bone

Type :

Bone

edit_bone

Type :

EditBone

pose_bone

Type :

PoseBone

particle_system

Type :

ParticleSystem

particle_system_editable

Type :

ParticleSystem

particle_settings

Type :

ParticleSettings

cloth

Type :

ClothModifier

soft_body

Type :

SoftBodyModifier

fluid

Type :

FluidModifier

collision

Type :

CollisionModifier

brush

Type :

Brush

dynamic_paint

Type :

DynamicPaintModifier

line_style

Type :

FreestyleLineStyle

collection

Type :

LayerCollection

gpencil

Type :

GreasePencil

grease_pencil

Type :

GreasePencil

curves

Type :

Curves

pointcloud

Type :

PointCloud

volume

Type :

Volume

strip

Type :

Strip

strip_modifier

Type :

StripModifier

Clip Context

edit_movieclip

Type :

MovieClip

edit_mask

Type :

Mask

File Context

active_file

Type :

FileSelectEntry

selected_files

Type :

Sequence[FileSelectEntry]

asset_library_reference

Type :

AssetLibraryReference

asset

Type :

AssetRepresentation

selected_assets

Type :

Sequence[AssetRepresentation]

id

Type :

ID

selected_ids

Type :

Sequence[ID]

Image Context

edit_image

Type :

Image

edit_mask

Type :

Mask

Node Context

selected_nodes

Type :

Sequence[Node]

active_node

Type :

Node

light

Type :

Light

material

Type :

Material

world

Type :

World

Screen Context

scene

Type :

Scene

view_layer

Type :

ViewLayer

visible_objects

Type :

Sequence[Object]

selectable_objects

Type :

Sequence[Object]

selected_objects

Type :

Sequence[Object]

editable_objects

Type :

Sequence[Object]

selected_editable_objects

Type :

Sequence[Object]

objects_in_mode

Type :

Sequence[Object]

objects_in_mode_unique_data

Type :

Sequence[Object]

visible_bones

Type :

Sequence[EditBone]

editable_bones

Type :

Sequence[EditBone]

selected_bones

Type :

Sequence[EditBone]

selected_editable_bones

Type :

Sequence[EditBone]

visible_pose_bones

Type :

Sequence[PoseBone]

selected_pose_bones

Type :

Sequence[PoseBone]

selected_pose_bones_from_active_object

Type :

Sequence[PoseBone]

active_bone

Type :

EditBone | Bone

active_pose_bone

Type :

PoseBone

active_object

Type :

Object

object

Type :

Object

edit_object

Type :

Object

sculpt_object

Type :

Object

vertex_paint_object

Type :

Object

weight_paint_object

Type :

Object

image_paint_object

Type :

Object

particle_edit_object

Type :

Object

pose_object

Type :

Object

active_nla_track

Type :

NlaTrack

active_nla_strip

Type :

NlaStrip

selected_nla_strips

Type :

Sequence[NlaStrip]

selected_movieclip_tracks

Type :

Sequence[MovieTrackingTrack]

annotation_data

Type :

GreasePencil

annotation_data_owner

Type :

ID

active_annotation_layer

Type :

AnnotationLayer

grease_pencil

Type :

GreasePencil

active_operator

Type :

Operator

active_action

Type :

Action

selected_visible_actions

Type :

Sequence[Action]

selected_editable_actions

Type :

Sequence[Action]

visible_fcurves

Type :

Sequence[FCurve]

editable_fcurves

Type :

Sequence[FCurve]

selected_visible_fcurves

Type :

Sequence[FCurve]

selected_editable_fcurves

Type :

Sequence[FCurve]

active_editable_fcurve

Type :

FCurve

selected_editable_keyframes

Type :

Sequence[Keyframe]

ui_list

Type :

UIList

property

Type :

AnyType | str | int

Fetches the property under whatever button the pointer is over.
Comes back as a tuple holding the data-block, the data path leading to the property, and an array index.

Note

If no bpy.types.ID is tied to the property, what you get back may be non-ID data.
That can happen when reaching into windowing data — operator properties, for instance.

`	ext
import bpy

### Example inserting keyframe for the hovered property.
active_property = bpy.context.property
if active_property:
datablock, data_path, index = active_property
datablock.keyframe_insert(data_path=data_path, index=index, frame=1)
`

asset_library_reference

Type :

AssetLibraryReference

active_strip

Type :

Strip

strips

Type :

Sequence[Strip]

selected_strips

Type :

Sequence[Strip]

selected_editable_strips

Type :

Sequence[Strip]

sequencer_scene

Type :

Scene

Sequencer Context

edit_mask

Type :

Mask

tool_settings

Type :

ToolSettings

Text Context

edit_text

Type :

Text

View3D Context

active_object

Type :

Object

selected_ids

Type :

Sequence[ID]

Methods

evaluated_depsgraph_get ( )

Retrieve the dependency graph tied to the current scene and view layer; through it you reach data-blocks that already have their animation and modifiers resolved. Pending edits to any data-block trigger a rebuild of the graph, and doing so makes every existing reference to its evaluated data-blocks stale.

Returns :

Evaluated dependency graph

Return type :

Depsgraph

copy ( )

Hand back the context members packed into a dictionary.

Return type :

dict[str, Any]

path_resolve ( path , coerce = True )

Look up the property named by the path, throwing an exception if it can't be located.

Parameters :

- path ( str ) – patch which this property resolves.

- coerce ( bool ) – optional argument, when True, the property will be converted into its Python representation.

Returns :

Property value or property object.

Return type :

Any | bpy.types.bpy_prop

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

temp_override ( * , window = None , screen = None , area = None , region = None , ** keywords )

A context manager that swaps out chosen context members for the duration of a block.

Parameters :

- window (bpy.types.Window | None) – Window override or None.

- screen (bpy.types.Screen | None) – Screen override or None.

Note

Moving into or out of full-screen areas and temporary screens is not handled. Hand in one of those screens and an exception is raised; operations that exit the context with such screens won't bring back the previous screen.

Note

A screen swap reaches further than the other arguments, since it can pull the workspace along — and the scene too, where pinning applies.

- area (bpy.types.Area | None) – Area override or None.

- region (bpy.types.Region | None) – Region override or None.

- keywords – Additional keywords override context members.

Returns :

The context manager.

Return type :

ContextTempOverride

Use a context override to bring a different window / area & region to the foreground for a moment, or to swap in members like the active_object or bone .

Notes:

- The window, area, and region arguments have to agree with one another: a region you pass must belong to the current area or to the area you also pass. Likewise the area must belong to the current window.

- These overrides can sit inside one another; nesting simply layers the new members on top of the overrides already in place.

- Once the context-manager's block ends, the members go back to what they were. The lone exception is when the underlying data has since vanished.

Should the windowing data disappear (for one reason or another), the context simply keeps whatever state it currently holds.
Although it's an unusual situation, deliberate window actions — closing windows, or loading another file — wipe out the windowing data that was assigned before the temporary context began.

Setting up the context after a file load is one good use, since otherwise it would be None. For instance:

`	ext
import bpy
from bpy import context

### Reload the current file and select all.
bpy.ops.wm.open_mainfile(filepath=bpy.data.filepath)
window = context.window_manager.windows[0]
with context.temp_override(window=window):
bpy.ops.mesh.primitive_uv_sphere_add()
### The context override is needed so it's possible to set edit-mode.
bpy.ops.object.mode_set(mode='EDIT')
`

Here is how you can drop an object into the scene under a different window.

`	ext
import bpy
from bpy import context

win_active = context.window
win_other = None
for win_iter in context.window_manager.windows:
if win_iter != win_active:
win_other = win_iter
break

### Add cube in the other window.
with context.temp_override(window=win_other):
bpy.ops.mesh.primitive_cube_add()
`

Logging Context Member Access

To record which members are touched, call logging_set(True) on the object returned by the "with" of a temporary override.
It prints out the members accessed over the course of the operation, which can be handy for working out which members still need overriding.

When an operator refuses to run because a context member is absent, this logging can point you at the missing one.

The snippet below records which context members get read.
The log lines go to your system console.

Important

Some operators don't consult Context Members at all, so bpy.types.Context.temp_override leaves them unaffected; lean on logging to find which members, if any, are read.

`	ext
import bpy
from bpy import context

my_objects = [context.scene.camera]

with context.temp_override(selected_objects=my_objects) as override:
override.logging_set(
True, # Enable logging.
hide_missing=True, # Don't show failed attempts.
)
bpy.ops.object.delete()
`

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| AssetShelf.draw_context_menu AssetShelf.poll FileHandler.poll_drop Gizmo.draw Gizmo.draw_select Gizmo.exit Gizmo.invoke Gizmo.modal Gizmo.test_select GizmoGroup.draw_prepare GizmoGroup.invoke_prepare GizmoGroup.poll GizmoGroup.refresh GizmoGroup.setup Header.draw KeyingSetInfo.generate KeyingSetInfo.iterator KeyingSetInfo.poll Macro.draw Macro.poll Menu.draw Menu.poll Node.draw_buttons Node.draw_buttons_ext Node.init Node.socket_value_update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeSocket.draw NodeSocket.draw_color NodeSocketStandard.draw NodeSocketStandard.draw_color NodeTree.get_from_context NodeTree.interface_update NodeTree.poll NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocketBool.draw NodeTreeInterfaceSocketBundle.draw NodeTreeInterfaceSocketClosure.draw NodeTreeInterfaceSocketCollection.draw NodeTreeInterfaceSocketColor.draw NodeTreeInterfaceSocketFloat.draw NodeTreeInterfaceSocketFloatAngle.draw NodeTreeInterfaceSocketFloatColorTemperature.draw NodeTreeInterfaceSocketFloatDistance.draw NodeTreeInterfaceSocketFloatFactor.draw NodeTreeInterfaceSocketFloatFrequency.draw NodeTreeInterfaceSocketFloatMass.draw NodeTreeInterfaceSocketFloatPercentage.draw NodeTreeInterfaceSocketFloatTime.draw NodeTreeInterfaceSocketFloatTimeAbsolute.draw NodeTreeInterfaceSocketFloatUnsigned.draw NodeTreeInterfaceSocketFloatWavelength.draw NodeTreeInterfaceSocketGeometry.draw NodeTreeInterfaceSocketImage.draw NodeTreeInterfaceSocketInt.draw NodeTreeInterfaceSocketIntFactor.draw NodeTreeInterfaceSocketIntPercentage.draw NodeTreeInterfaceSocketIntUnsigned.draw NodeTreeInterfaceSocketMaterial.draw NodeTreeInterfaceSocketMatrix.draw NodeTreeInterfaceSocketMenu.draw NodeTreeInterfaceSocketObject.draw NodeTreeInterfaceSocketRotation.draw | NodeTreeInterfaceSocketShader.draw NodeTreeInterfaceSocketString.draw NodeTreeInterfaceSocketStringFilePath.draw NodeTreeInterfaceSocketTexture.draw NodeTreeInterfaceSocketVector.draw NodeTreeInterfaceSocketVector2D.draw NodeTreeInterfaceSocketVector4D.draw NodeTreeInterfaceSocketVectorAcceleration.draw NodeTreeInterfaceSocketVectorAcceleration2D.draw NodeTreeInterfaceSocketVectorAcceleration4D.draw NodeTreeInterfaceSocketVectorDirection.draw NodeTreeInterfaceSocketVectorDirection2D.draw NodeTreeInterfaceSocketVectorDirection4D.draw NodeTreeInterfaceSocketVectorEuler.draw NodeTreeInterfaceSocketVectorEuler2D.draw NodeTreeInterfaceSocketVectorEuler4D.draw NodeTreeInterfaceSocketVectorFactor.draw NodeTreeInterfaceSocketVectorFactor2D.draw NodeTreeInterfaceSocketVectorFactor4D.draw NodeTreeInterfaceSocketVectorPercentage.draw NodeTreeInterfaceSocketVectorPercentage2D.draw NodeTreeInterfaceSocketVectorPercentage4D.draw NodeTreeInterfaceSocketVectorTranslation.draw NodeTreeInterfaceSocketVectorTranslation2D.draw NodeTreeInterfaceSocketVectorTranslation4D.draw NodeTreeInterfaceSocketVectorVelocity.draw NodeTreeInterfaceSocketVectorVelocity2D.draw NodeTreeInterfaceSocketVectorVelocity4D.draw NodeTreeInterfaceSocketVectorXYZ.draw NodeTreeInterfaceSocketVectorXYZ2D.draw NodeTreeInterfaceSocketVectorXYZ4D.draw Operator.cancel Operator.check Operator.description Operator.draw Operator.execute Operator.invoke Operator.modal Operator.poll Panel.draw Panel.draw_header Panel.draw_header_preset Panel.poll RenderEngine.draw RenderEngine.view_draw RenderEngine.view_update UIList.draw_filter UIList.draw_item UIList.filter_items XrSessionState.action_binding_create XrSessionState.action_create XrSessionState.action_set_create XrSessionState.action_state_get XrSessionState.active_action_set_set XrSessionState.controller_aim_location_get XrSessionState.controller_aim_rotation_get XrSessionState.controller_grip_location_get XrSessionState.controller_grip_rotation_get XrSessionState.controller_pose_actions_set XrSessionState.haptic_action_apply XrSessionState.haptic_action_stop XrSessionState.is_running XrSessionState.reset_to_base_pose |

## See also

- [Bpy Struct](bpy-struct.md)

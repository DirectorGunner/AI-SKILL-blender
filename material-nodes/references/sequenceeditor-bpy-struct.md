# Sequenceeditor Bpy Struct, Sequencercacheoverlay Bpy Struct, Sequencercompositormodifierdata Stripmodifier, Sequencertonemapmodifierdata Stripmodifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SequenceEditor(bpy_struct); SequencerCacheOverlay(bpy_struct); SequencerCompositorModifierData(StripModifier); SequencerTonemapModifierData(StripModifier); ShaderFxFlip(ShaderFx); ShaderFxSwirl(ShaderFx); ShaderNode(NodeInternal); ShaderNodeAddShader(ShaderNode).

## SequenceEditor(bpy_struct)

### SequenceEditor(bpy_struct)

base class — bpy_struct

class bpy.types. SequenceEditor ( bpy_struct )

Holds the strip-editing data belonging to a Scene data-block

active_strip

The strip the sequencer currently treats as active

Type :

Strip

cache_final_size

How much memory, in megabytes, the final rendered-image cache occupies (in [-inf, inf], default 0, readonly)

Type :

int

cache_raw_size

How much memory, in megabytes, the raw source-image cache occupies (in [-inf, inf], default 0, readonly)

Type :

int

channels

(default None, readonly)

Type :

bpy_prop_collection[SequenceTimelineChannel]

meta_stack

Stack of meta strips, whose last entry is the meta strip open for editing (default None, readonly)

Type :

bpy_prop_collection[Strip]

overlay_frame

How many frames the overlay is shifted by (in [-inf, inf], default 0)

Type :

int

proxy_dir

(default “”, never None, blend relative // prefix supported)

Type :

str

proxy_storage

Where proxies for this project are kept (default '`PER_STRIP`' )

- `PER_STRIP`
Per Strip – Keep proxies according to each strip's own settings.

- PROJECT
Project – Keep proxies in the project directory.

Type :

Literal[‘`PER_STRIP`’, ‘PROJECT’]

selected_retiming_keys

(default False, readonly)

Type :

bool

show_missing_media

Draw absent images or movies as a flat magenta fill (default False)

Type :

bool

show_overlay_frame

Lay a partial overlay over the sequencer using a frame offset (default False)

Type :

bool

strips

Only the top-level strips (default None, readonly)

Type :

StripsTopLevel[Strip]

strips_all

Every strip, descending recursively into metastrips as well (default None, readonly)

Type :

bpy_prop_collection[Strip]

use_cache_final

Hold the finished image for every frame in cache (default False)

Type :

bool

use_cache_raw

Hold raw images straight from disk in cache so strip parameters tweak faster, trading memory for speed (default False)

Type :

bool

use_overlay_frame_lock

(default False)

Type :

bool

use_prefetch

Pre-render upcoming frames in the background for smoother playback (default False)

Type :

bool

display_stack ( meta_sequence )

Show the stack of strips

Parameters :

meta_sequence (Strip) – Meta Strip, Meta to display its stack

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

| Scene.sequence_editor | Scene.sequence_editor_create |

## SequencerCacheOverlay(bpy_struct)

### SequencerCacheOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SequencerCacheOverlay ( bpy_struct )

show_cache

Mark which images are cached along the timeline (default False)

Type :

bool

show_cache_final_out

Mark which finished frames are held in cache (default False)

Type :

bool

show_cache_raw

Mark which raw images are held in cache (default False)

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

| SpaceSequenceEditor.cache_overlay | |

## SequencerCompositorModifierData(StripModifier)

### SequencerCompositorModifierData(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. SequencerCompositorModifierData ( StripModifier )

Compositor Modifier

node_group

The node group that governs how this modifier behaves

Type :

NodeTree

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

## SequencerTonemapModifierData(StripModifier)

### SequencerTonemapModifierData(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. SequencerTonemapModifierData ( StripModifier )

Tone mapping modifier

adaptation

A value of 0 keeps it global; a value of 1 ties it to pixel intensity (in [0, 1], default 0.0)

Type :

float

contrast

Leave at 0 to let the input image supply the estimate (in [0, 1], default 0.0)

Type :

float

correction

A value of 0 treats all channels alike; a value of 1 handles each on its own (in [0, 1], default 0.0)

Type :

float

gamma

Leave at 1 when this is not in use (in [0.001, 3], default 0.0)

Type :

float

intensity

Negative values darken the image while positive values brighten it (in [-8, 8], default 0.0)

Type :

float

key

The target value that the mean luminance maps onto (in [0, 1], default 0.0)

Type :

float

offset

Usually kept at 1, but available as a further handle on the brightness curve (in [0.001, 10], default 0.0)

Type :

float

open_mask_input_panel

(default False)

Type :

bool

tonemap_type

Which tone-mapping algorithm to run (default '`RH_SIMPLE`' )

Type :

Literal[‘`RD_PHOTORECEPTOR`’, ‘`RH_SIMPLE`’]

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

## ShaderFxFlip(ShaderFx)

### ShaderFxFlip(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxFlip ( ShaderFx )

Flip effect

use_flip_x

Mirror the image left to right (default False)

Type :

bool

use_flip_y

Mirror the image top to bottom (default False)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxSwirl(ShaderFx)

### ShaderFxSwirl(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxSwirl ( ShaderFx )

Swirl effect

angle

How far the rotation goes (in [-31.4159, 31.4159], default 0.0)

Type :

float

object

Object that fixes where the center sits

Type :

Object

radius

How far out the effect reaches (in [0, 32767], default 0)

Type :

int

use_transparent

Clear the image beyond the radius (default False)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderNode(NodeInternal)

### ShaderNode(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

subclasses —
ShaderNodeAddShader, ShaderNodeAmbientOcclusion, ShaderNodeAttribute, ShaderNodeBackground, ShaderNodeBevel, ShaderNodeBlackbody, ShaderNodeBrightContrast, ShaderNodeBsdfAnisotropic, ShaderNodeBsdfDiffuse, ShaderNodeBsdfGlass, ShaderNodeBsdfHair, ShaderNodeBsdfHairPrincipled, ShaderNodeBsdfMetallic, ShaderNodeBsdfPrincipled, ShaderNodeBsdfRayPortal, ShaderNodeBsdfRefraction, ShaderNodeBsdfSheen, ShaderNodeBsdfToon, ShaderNodeBsdfTranslucent, ShaderNodeBsdfTransparent, ShaderNodeBump, ShaderNodeCameraData, ShaderNodeClamp, ShaderNodeCombineColor, ShaderNodeCombineXYZ, ShaderNodeCustomGroup, ShaderNodeDisplacement, ShaderNodeEeveeSpecular, ShaderNodeEmission, ShaderNodeFloatCurve, ShaderNodeFresnel, ShaderNodeGamma, ShaderNodeGroup, ShaderNodeHairInfo, ShaderNodeHoldout, ShaderNodeHueSaturation, ShaderNodeInvert, ShaderNodeLayerWeight, ShaderNodeLightFalloff, ShaderNodeLightPath, ShaderNodeMapRange, ShaderNodeMapping, ShaderNodeMath, ShaderNodeMix, ShaderNodeMixRGB, ShaderNodeMixShader, ShaderNodeNewGeometry, ShaderNodeNormal, ShaderNodeNormalMap, ShaderNodeObjectInfo, ShaderNodeOutputAOV, ShaderNodeOutputLight, ShaderNodeOutputLineStyle, ShaderNodeOutputMaterial, ShaderNodeOutputWorld, ShaderNodeParticleInfo, ShaderNodePointInfo, ShaderNodeRGB, ShaderNodeRGBCurve, ShaderNodeRGBToBW, ShaderNodeRadialTiling, ShaderNodeRaycast, ShaderNodeScript, ShaderNodeSeparateColor, ShaderNodeSeparateXYZ, ShaderNodeShaderToRGB, ShaderNodeSqueeze, ShaderNodeSubsurfaceScattering, ShaderNodeTangent, ShaderNodeTexBrick, ShaderNodeTexChecker, ShaderNodeTexCoord, ShaderNodeTexEnvironment, ShaderNodeTexGabor, ShaderNodeTexGradient, ShaderNodeTexIES, ShaderNodeTexImage, ShaderNodeTexMagic, ShaderNodeTexNoise, ShaderNodeTexSky, ShaderNodeTexVoronoi, ShaderNodeTexWave, ShaderNodeTexWhiteNoise, ShaderNodeUVAlongStroke, ShaderNodeUVMap, ShaderNodeValToRGB, ShaderNodeValue, ShaderNodeVectorCurve, ShaderNodeVectorDisplacement, ShaderNodeVectorMath, ShaderNodeVectorRotate, ShaderNodeVectorTransform, ShaderNodeVertexColor, ShaderNodeVolumeAbsorption, ShaderNodeVolumeCoefficients, ShaderNodeVolumeInfo, ShaderNodeVolumePrincipled, ShaderNodeVolumeScatter, ShaderNodeWavelength, ShaderNodeWireframe

class bpy.types. ShaderNode ( NodeInternal )

Material shader node

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get | Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py |

### References

| ShaderNodeTree.get_output_node | |

## ShaderNodeAddShader(ShaderNode)

### ShaderNodeAddShader(ShaderNode)

base classes — bpy_struct, Node, NodeInternal, ShaderNode

class bpy.types. ShaderNodeAddShader ( ShaderNode )

Combine two shaders by summing them

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py ShaderNode.poll ShaderNode.bl_rna_get_subclass ShaderNode.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)

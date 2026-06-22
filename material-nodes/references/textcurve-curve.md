# Textcurve Curve, Textstrip Effectstrip, Texture Id, Texturenode Nodeinternal ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: TextCurve(Curve); TextStrip(EffectStrip); Texture(ID); TextureNode(NodeInternal); TextureNodeAt(TextureNode).

## TextCurve(Curve)

### TextCurve(Curve)

base classes — bpy_struct, ID, Curve

class bpy.types. TextCurve ( Curve )

Data-block that holds the text for a curve.

active_textbox

(in [-inf, inf], default 0)

Type :

int

align_x

Where text sits horizontally relative to the object or text-box center (default 'LEFT' )

- LEFT
Left – Push the text against the left edge.

- CENTER
Center – Keep the text centered.

- RIGHT
Right – Push the text against the right edge.

- JUSTIFY
Justify – Stretch lines so both margins line up.

- FLUSH
Flush – Stretch to both margins while spacing characters evenly.

Type :

Literal[‘LEFT’, ‘CENTER’, ‘RIGHT’, ‘JUSTIFY’, ‘FLUSH’]

align_y

Where text sits vertically relative to the object center (default '`TOP_BASELINE`' )

- TOP
Top – Anchor the text at the top.

- `TOP_BASELINE`
Top Baseline – Anchor at the baseline of the first line.

- CENTER
Middle – Anchor the text at its middle.

- `BOTTOM_BASELINE`
Bottom Baseline – Anchor at the baseline of the last line.

- BOTTOM
Bottom – Anchor the text at the bottom.

Type :

Literal[‘TOP’, ‘`TOP_BASELINE`’, ‘CENTER’, ‘`BOTTOM_BASELINE`’, ‘BOTTOM’]

body

The text this object contains (default “”, never None)

Type :

str

body_format

Per-character styling for the text (default None, readonly)

Type :

bpy_prop_collection[TextCharacterFormat]

edit_format

Character formatting used while editing (readonly)

Type :

TextCharacterFormat

family

Drive font characters from objects: name your font objects with a shared prefix plus the character they stand in for (e.g. ‘family-a’, ‘family-b’), set this field to that prefix such as ‘family-’, and switch on Vertex Instancing (default “”, never None)

Type :

str

follow_curve

Curve that the text object is deformed along

Type :

Object

font

Type :

VectorFont

font_bold

Type :

VectorFont

font_bold_italic

Type :

VectorFont

font_italic

Type :

VectorFont

has_selection

Reports whether any text is currently selected (default False, readonly)

Type :

bool

is_select_bold

Reports whether the current selection is bold (default False, readonly)

Type :

bool

is_select_italic

Reports whether the current selection is italic (default False, readonly)

Type :

bool

is_select_smallcaps

Reports whether the current selection is small caps (default False, readonly)

Type :

bool

is_select_underline

Reports whether the current selection is underlined (default False, readonly)

Type :

bool

offset_x

Shift along the horizontal from the object origin (in [-inf, inf], default 0.0)

Type :

float

offset_y

Shift along the vertical from the object origin (in [-inf, inf], default 0.0)

Type :

float

overflow

What happens to text that exceeds its text boxes (default 'NONE' )

- NONE
Overflow – Allow the text to spill past the boxes.

- SCALE
Scale to Fit – Shrink the text until it fits inside the boxes.

- TRUNCATE
Truncate – Cut off any text past the box edges.

Type :

Literal[‘NONE’, ‘SCALE’, ‘TRUNCATE’]

shear

Slant applied to the characters for an italic look (in [-1, 1], default 0.0)

Type :

float

size

(in [0.0001, 10000], default 1.0)

Type :

float

small_caps_scale

How much small capitals are scaled down (in [-inf, inf], default 0.75)

Type :

float

space_character

(in [0, 10], default 1.0)

Type :

float

space_line

(in [0, 10], default 1.0)

Type :

float

space_word

(in [0, 10], default 1.0)

Type :

float

text_boxes

(default None, readonly)

Type :

bpy_prop_collection[TextBox]

underline_height

(in [0, 0.8], default 0.05)

Type :

float

underline_position

Where the underline sits vertically (in [-0.2, 0.8], default 0.0)

Type :

float

use_fast_edit

Skip polygon filling during editing for speed (default False)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview Curve.shape_keys Curve.splines Curve.path_duration Curve.use_path Curve.use_path_follow Curve.use_path_clamp Curve.use_stretch Curve.use_deform_bounds Curve.use_radius Curve.bevel_mode | Curve.bevel_profile Curve.bevel_resolution Curve.offset Curve.extrude Curve.bevel_depth Curve.resolution_u Curve.resolution_v Curve.render_resolution_u Curve.render_resolution_v Curve.eval_time Curve.bevel_object Curve.taper_object Curve.dimensions Curve.fill_mode Curve.fill_solver Curve.fill_rule Curve.twist_mode Curve.taper_radius_mode Curve.bevel_factor_mapping_start Curve.bevel_factor_mapping_end Curve.twist_smooth Curve.use_fill_caps Curve.use_map_taper Curve.use_auto_texspace Curve.texspace_location Curve.texspace_size Curve.materials Curve.bevel_factor_start Curve.bevel_factor_end Curve.is_editmode Curve.animation_data Curve.cycles |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Curve.transform Curve.validate_material_indices Curve.update_gpu_tag Curve.bl_rna_get_subclass Curve.bl_rna_get_subclass_py |

## TextStrip(EffectStrip)

### TextStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. TextStrip ( EffectStrip )

A sequencer strip that generates text.

alignment_x

Horizontal alignment of the text (default 'LEFT' )

Type :

Literal[‘LEFT’, ‘CENTER’, ‘RIGHT’]

anchor_x

Where the text box sits horizontally with respect to Location (default 'LEFT' )

Type :

Literal[‘LEFT’, ‘CENTER’, ‘RIGHT’]

anchor_y

Where the text box sits vertically with respect to Location (default 'TOP' )

Type :

Literal[‘TOP’, ‘CENTER’, ‘BOTTOM’]

box_color

(array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

box_margin

Margin around the box given as a fraction of image width (in [0, 1], default 0.01)

Type :

float

box_roundness

Corner rounding of the box as a fraction of its height (in [0, 1], default 0.0)

Type :

float

color

Color of the text (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

font

Typeface for the text; if unset, the UI font is used.

Type :

VectorFont

font_size

How large the text is drawn (in [0, 2000], default 0.0)

Type :

float

input_count

(in [0, inf], default 0, readonly)

Type :

int

location

Where the text is placed (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

outline_color

(array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

outline_width

(in [0, 1], default 0.05)

Type :

float

shadow_angle

(in [0, 6.28319], default 1.13446)

Type :

float

shadow_blur

(in [0, 1], default 0.0)

Type :

float

shadow_color

(array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

shadow_offset

(in [0, 1], default 0.04)

Type :

float

text

The text shown on screen (default “”, never None)

Type :

str

use_bold

Render the text in bold (default False)

Type :

bool

use_box

Draw a filled box behind the text (default False)

Type :

bool

use_italic

Render the text in italic (default False)

Type :

bool

use_outline

Draw an outline around the text (default False)

Type :

bool

use_shadow

Draw a shadow behind the text (default False)

Type :

bool

wrap_width

Wrap width as a factor; a value of zero turns wrapping off (in [0, inf], default 0.0)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## Texture(ID)

### Texture(ID)

base classes — bpy_struct, ID

subclasses —
BlendTexture, CloudsTexture, DistortedNoiseTexture, ImageTexture, MagicTexture, MarbleTexture, MusgraveTexture, NoiseTexture, StucciTexture, VoronoiTexture, WoodTexture

class bpy.types. Texture ( ID )

Data-block that supplies texture data to materials, lights, worlds and brushes.

animation_data

Animation data attached to this data-block (readonly)

Type :

AnimData

color_ramp

(readonly)

Type :

ColorRamp

contrast

Tweak how much contrast the texture has (in [0, 5], default 1.0)

Type :

float

factor_blue

(in [0, 2], default 1.0)

Type :

float

factor_green

(in [0, 2], default 1.0)

Type :

float

factor_red

(in [0, 2], default 1.0)

Type :

float

intensity

Tweak how bright the texture is (in [0, 2], default 1.0)

Type :

float

node_tree

The node tree behind node-based textures (readonly)

Type :

NodeTree

saturation

Tweak how saturated the texture colors are (in [0, 2], default 1.0)

Type :

float

type

(default 'IMAGE' )

Type :

Literal[Texture Type Items]

use_clamp

Clamp negative RGB and intensity values up to zero; turn this off when you need the full range, such as for displacement (default False)

Type :

bool

use_color_ramp

Route the texture intensity through the color ramp. The alpha value applies to image textures, so for images that lack an alpha channel switch on “Calculate Alpha”. (default False)

Type :

bool

use_nodes

Turn this into a node-based texture (default False)

Type :

bool

use_preview_alpha

Include alpha in the preview render (default False)

Type :

bool

users_material

Materials referencing this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers referencing this texture

Type :

tuple[Object, …]

Note

Takes O(len(bpy.data.objects) * len(obj.modifiers)) time.

(readonly)

evaluate ( value )

Sample the texture at a coordinate and hand back the result.

Parameters :

value (mathutils.Vector) – The (x,y,z) coordinate to sample. For a 3D texture the z component picks the slice being read; for 2D textures such as images z is ignored., (array of 3 items, in [-inf, inf])

Returns :

The texture result, where (x,y,z,w) map to (red, green, blue, intensity). Grayscale textures generally only fill in intensity., (array of 4 items, in [-inf, inf])

Return type :

mathutils.Vector

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.texture BlendData.textures BlendDataTextures.new BlendDataTextures.remove Brush.mask_texture Brush.texture DisplaceModifier.texture DynamicPaintSurface.init_texture FieldSettings.texture FluidFlowSettings.noise_texture FreestyleLineStyle.active_texture | NodeSocketTexture.default_value NodeTreeInterfaceSocketTexture.default_value ParticleSettings.active_texture TextureNodeTexture.texture TextureSlot.texture VertexWeightEditModifier.mask_texture VertexWeightMixModifier.mask_texture VertexWeightProximityModifier.mask_texture VolumeDisplaceModifier.texture WarpModifier.texture WaveModifier.texture |

## TextureNode(NodeInternal)

### TextureNode(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

subclasses —
TextureNodeAt, TextureNodeBricks, TextureNodeChecker, TextureNodeCombineColor, TextureNodeCompose, TextureNodeCoordinates, TextureNodeCurveRGB, TextureNodeCurveTime, TextureNodeDecompose, TextureNodeDistance, TextureNodeGroup, TextureNodeHueSaturation, TextureNodeImage, TextureNodeInvert, TextureNodeMath, TextureNodeMixRGB, TextureNodeOutput, TextureNodeRGBToBW, TextureNodeRotate, TextureNodeScale, TextureNodeSeparateColor, TextureNodeTexBlend, TextureNodeTexClouds, TextureNodeTexDistNoise, TextureNodeTexMagic, TextureNodeTexMarble, TextureNodeTexMusgrave, TextureNodeTexNoise, TextureNodeTexStucci, TextureNodeTexVoronoi, TextureNodeTexWood, TextureNodeTexture, TextureNodeTranslate, TextureNodeValToNor, TextureNodeValToRGB, TextureNodeViewer

class bpy.types. TextureNode ( NodeInternal )

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

## TextureNodeAt(TextureNode)

### TextureNodeAt(TextureNode)

base classes — bpy_struct, Node, NodeInternal, TextureNode

class bpy.types. TextureNodeAt ( TextureNode )

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

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py TextureNode.poll TextureNode.bl_rna_get_subclass TextureNode.bl_rna_get_subclass_py |

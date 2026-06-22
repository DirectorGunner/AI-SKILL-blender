# Freestylelineset Bpy Struct, Freestylelinestyle Id, Freestylesettings Bpy Struct, Functionnode Nodeinternal

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FreestyleLineSet(bpy_struct); FreestyleLineStyle(ID); FreestyleSettings(bpy_struct); FunctionNode(NodeInternal).

## FreestyleLineSet(bpy_struct)

### FreestyleLineSet(bpy_struct) 

base class — bpy_struct

class bpy.types. FreestyleLineSet ( bpy_struct ) 

Pairs a group of lines with the style parameters that drive how they render

collection 

The object group that determines which feature edges become eligible for selection

Type :

Collection

collection_negation 

Choose whether feature edges tied to the object collection are kept or filtered out (default 'INCLUSIVE' )

- INCLUSIVE
Inclusive – Select feature edges belonging to some object in the group.

- EXCLUSIVE
Exclusive – Select feature edges not belonging to any object in the group.

Type :

Literal[‘INCLUSIVE’, ‘EXCLUSIVE’]

edge_type_combination 

Sets how the per-edge-type selection tests are combined logically (default 'OR' )

- OR
Logical OR – Select feature edges satisfying at least one of edge type conditions.

- AND
Logical AND – Select feature edges satisfying all edge type conditions.

Type :

Literal[‘OR’, ‘AND’]

edge_type_negation 

Choose whether the edge-type tests keep matching edges or reject them (default 'INCLUSIVE' )

- INCLUSIVE
Inclusive – Select feature edges satisfying the given edge type conditions.

- EXCLUSIVE
Exclusive – Select feature edges not satisfying the given edge type conditions.

Type :

Literal[‘INCLUSIVE’, ‘EXCLUSIVE’]

exclude_border 

Leave border edges out of the selection (default False)

Type :

bool

exclude_contour 

Leave contours out of the selection (default False)

Type :

bool

exclude_crease 

Leave crease edges out of the selection (default False)

Type :

bool

exclude_edge_mark 

Leave edge marks out of the selection (default False)

Type :

bool

exclude_external_contour 

Leave external contours out of the selection (default False)

Type :

bool

exclude_material_boundary 

Leave edges sitting on material boundaries out of the selection (default False)

Type :

bool

exclude_ridge_valley 

Leave ridges and valleys out of the selection (default False)

Type :

bool

exclude_silhouette 

Leave silhouette edges out of the selection (default False)

Type :

bool

exclude_suggestive_contour 

Leave suggestive contours out of the selection (default False)

Type :

bool

face_mark_condition 

Decide how face marks on adjacent faces qualify an edge for selection (default 'ONE' )

- ONE
One Face – Select a feature edge if either of its adjacent faces is marked.

- BOTH
Both Faces – Select a feature edge if both of its adjacent faces are marked.

Type :

Literal[‘ONE’, ‘BOTH’]

face_mark_negation 

Choose whether the face-mark tests keep matching edges or reject them (default 'INCLUSIVE' )

- INCLUSIVE
Inclusive – Select feature edges satisfying the given face mark conditions.

- EXCLUSIVE
Exclusive – Select feature edges not satisfying the given face mark conditions.

Type :

Literal[‘INCLUSIVE’, ‘EXCLUSIVE’]

linestyle 

The style configuration applied to this set (never None)

Type :

FreestyleLineStyle

name 

Identifier for the line set (default “”, never None)

Type :

str

qi_end 

Upper bound of the QI range (in [0, inf], default 0)

Type :

int

qi_start 

Lower bound of the QI range (in [0, inf], default 0)

Type :

int

select_border 

Include border edges, meaning open edges of a mesh (default False)

Type :

bool

select_by_collection 

Restrict selection to feature edges drawn from an object collection (default False)

Type :

bool

select_by_edge_types 

Restrict selection to feature edges matching the chosen edge types (default False)

Type :

bool

select_by_face_marks 

Restrict selection to feature edges qualified through face marks (default False)

Type :

bool

select_by_image_border 

Restrict selection to feature edges along the image border, which uses less memory (default False)

Type :

bool

select_by_visibility 

Restrict selection to feature edges according to their visibility (default False)

Type :

bool

select_contour 

Include contours, the outer silhouette of every object (default False)

Type :

bool

select_crease 

Include crease edges, where two faces meet at an angle below the Crease Angle (default False)

Type :

bool

select_edge_mark 

Include edge marks, edges flagged manually with Freestyle edge marks (default False)

Type :

bool

select_external_contour 

Include external contours, the outer silhouettes spanning occluding and occluded objects (default False)

Type :

bool

select_material_boundary 

Include edges located where two materials meet (default False)

Type :

bool

select_ridge_valley 

Include ridges and valleys, the dividing lines between convex and concave regions of a surface (default False)

Type :

bool

select_silhouette 

Include silhouettes, edges along the boundary between visible and hidden faces (default False)

Type :

bool

select_suggestive_contour 

Include suggestive contours, edges that sit just short of being a silhouette or contour (default False)

Type :

bool

show_render 

Toggle whether this line set participates when strokes are rendered (default False)

Type :

bool

visibility 

Decide how an edge's visibility factors into whether it is selected (default 'VISIBLE' )

- VISIBLE
Visible – Select visible feature edges.

- HIDDEN
Hidden – Select hidden feature edges.

- RANGE
Quantitative Invisibility – Select feature edges within a range of quantitative invisibility (QI) values.

Type :

Literal[‘VISIBLE’, ‘HIDDEN’, ‘RANGE’]

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

| Linesets.active Linesets.new | Linesets.remove FreestyleSettings.linesets |

## FreestyleLineStyle(ID)

### FreestyleLineStyle(ID) 

base classes — bpy_struct, ID

class bpy.types. FreestyleLineStyle ( ID ) 

A line style definition that several line sets can share

active_texture 

The texture slot currently shown as active

Type :

Texture

active_texture_index 

Position of the active texture slot (in [0, 17], default 0)

Type :

int

alpha 

Starting alpha value, which alpha modifiers may further adjust (in [0, 1], default 1.0)

Type :

float

alpha_modifiers 

The set of alpha transparency modifiers attached to this style (default None, readonly)

Type :

LineStyleAlphaModifiers[LineStyleAlphaModifier]

angle_max 

Largest 2D angle at which chains are split (in [0, 3.14159], default 0.0)

Type :

float

angle_min 

Smallest 2D angle at which chains are split (in [0, 3.14159], default 0.0)

Type :

float

animation_data 

Animation data attached to this data-block (readonly)

Type :

AnimData

caps 

Choose the cap shape used at both ends of each stroke (default 'BUTT' )

- BUTT
Butt – Butt cap (flat).

- ROUND
Round – Round cap (half-circle).

- SQUARE
Square – Square cap (flat and extended).

Type :

Literal[‘BUTT’, ‘ROUND’, ‘SQUARE’]

chain_count 

How many leading chains are kept when selecting the first N chains (in [0, inf], default 10)

Type :

int

chaining 

Choose the method used to join feature edges into chains (default 'PLAIN' )

- PLAIN
Plain – Plain chaining.

- SKETCHY
Sketchy – Sketchy chaining with a multiple touch.

Type :

Literal[‘PLAIN’, ‘SKETCHY’]

color 

Starting line color, which color modifiers may further adjust (array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

color_modifiers 

The set of line color modifiers attached to this style (default None, readonly)

Type :

LineStyleColorModifiers[LineStyleColorModifier]

dash1 

How long the 1st dash runs on dashed lines (in [0, 65535], default 0)

Type :

int

dash2 

How long the 2nd dash runs on dashed lines (in [0, 65535], default 0)

Type :

int

dash3 

How long the 3rd dash runs on dashed lines (in [0, 65535], default 0)

Type :

int

gap1 

How long the 1st gap runs on dashed lines (in [0, 65535], default 0)

Type :

int

gap2 

How long the 2nd gap runs on dashed lines (in [0, 65535], default 0)

Type :

int

gap3 

How long the 3rd gap runs on dashed lines (in [0, 65535], default 0)

Type :

int

geometry_modifiers 

The set of stroke geometry modifiers attached to this style (default None, readonly)

Type :

LineStyleGeometryModifiers[LineStyleGeometryModifier]

integration_type 

Choose how a single sort key is derived from each chain (default 'MEAN' )

- MEAN
Mean – The value computed for the chain is the mean of the values obtained for chain vertices.

- MIN
Min – The value computed for the chain is the minimum of the values obtained for chain vertices.

- MAX
Max – The value computed for the chain is the maximum of the values obtained for chain vertices.

- FIRST
First – The value computed for the chain is the value obtained for the first chain vertex.

- LAST
Last – The value computed for the chain is the value obtained for the last chain vertex.

Type :

Literal[‘MEAN’, ‘MIN’, ‘MAX’, ‘FIRST’, ‘LAST’]

length_max 

Largest curvilinear 2D length permitted when chains are selected (in [0, 10000], default 10000.0)

Type :

float

length_min 

Smallest curvilinear 2D length permitted when chains are selected (in [0, 10000], default 0.0)

Type :

float

material_boundary 

When enabled, chains break apart wherever they cross a material boundary (default False)

Type :

bool

node_tree 

The node tree backing node-based shaders (readonly)

Type :

NodeTree

panel 

Pick which property panel is currently displayed (default 'STROKES' )

- STROKES
Strokes – Show the panel for stroke construction.

- COLOR
Color – Show the panel for line color options.

- ALPHA
Alpha – Show the panel for alpha transparency options.

- THICKNESS
Thickness – Show the panel for line thickness options.

- GEOMETRY
Geometry – Show the panel for stroke geometry options.

- TEXTURE
Texture – Show the panel for stroke texture options.

Type :

Literal[‘STROKES’, ‘COLOR’, ‘ALPHA’, ‘THICKNESS’, ‘GEOMETRY’, ‘TEXTURE’]

rounds 

How many passes a sketchy multiple touch makes (in [1, 1000], default 3)

Type :

int

sort_key 

Pick the value that determines how chains stack on top of one another (default '`DISTANCE_FROM_CAMERA`' )

- `DISTANCE_FROM_CAMERA`
Distance from Camera – Sort by distance from camera (closer lines lie on top of further lines).

- 2`D_LENGTH`
2D Length – Sort by curvilinear 2D length (longer lines lie on top of shorter lines).

- `PROJECTED_X`
Projected X – Sort by the projected X value in the image coordinate system.

- `PROJECTED_Y`
Projected Y – Sort by the projected Y value in the image coordinate system.

Type :

Literal[‘`DISTANCE_FROM_CAMERA`’, ‘2`D_LENGTH`’, ‘`PROJECTED_X`’, ‘`PROJECTED_Y`’]

sort_order 

Pick the direction in which the sort key is applied (default 'DEFAULT' )

- DEFAULT
Default – Default order of the sort key.

- REVERSE
Reverse – Reverse order.

Type :

Literal[‘DEFAULT’, ‘REVERSE’]

split_dash1 

How long the 1st dash runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_dash2 

How long the 2nd dash runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_dash3 

How long the 3rd dash runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_gap1 

How long the 1st gap runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_gap2 

How long the 2nd gap runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_gap3 

How long the 3rd gap runs in the splitting pattern (in [0, 65535], default 0)

Type :

int

split_length 

Curvilinear 2D length at which a chain is split (in [0, 10000], default 100.0)

Type :

float

texture_slots 

The texture slots that set up how textures map onto and influence strokes (default None, readonly)

Type :

LineStyleTextureSlots[LineStyleTextureSlot]

texture_spacing 

How far apart textures are repeated along the stroke (in [0.01, 100], default 1.0)

Type :

float

thickness 

Starting line thickness, which thickness modifiers may further adjust (in [0, 10000], default 3.0)

Type :

float

thickness_modifiers 

The set of line thickness modifiers attached to this style (default None, readonly)

Type :

LineStyleThicknessModifiers[LineStyleThicknessModifier]

thickness_position 

Where thickness sits relative to silhouette and border edges, used when plain chaining runs with Same Object (default 'CENTER' )

- CENTER
Center – Silhouettes and border edges are centered along stroke geometry.

- INSIDE
Inside – Silhouettes and border edges are drawn inside of stroke geometry.

- OUTSIDE
Outside – Silhouettes and border edges are drawn outside of stroke geometry.

- RELATIVE
Relative – Silhouettes and border edges are shifted by a user-defined ratio.

Type :

Literal[‘CENTER’, ‘INSIDE’, ‘OUTSIDE’, ‘RELATIVE’]

thickness_ratio 

A value from 0 (inside) to 1 (outside) that places the stroke thickness relative to the line (in [0, 1], default 0.5)

Type :

float

use_angle_max 

Break chains wherever the 2D angle exceeds the maximum (default False)

Type :

bool

use_angle_min 

Break chains wherever the 2D angle drops below the minimum (default False)

Type :

bool

use_chain_count 

Turn on selection limited to the first N chains (default False)

Type :

bool

use_chaining 

Allow feature edges to be joined into chains (default True)

Type :

bool

use_dashed_line 

Switch dashed lines on or off (default False)

Type :

bool

use_length_max 

Turn on chain selection capped at a maximum 2D length (default False)

Type :

bool

use_length_min 

Turn on chain selection requiring a minimum 2D length (default False)

Type :

bool

use_nodes 

Drive this line style through shader nodes (default False)

Type :

bool

use_same_object 

When enabled, only feature edges from the same object are chained together (default True)

Type :

bool

use_sorting 

Order how strokes stack against one another (default False)

Type :

bool

use_split_length 

Turn on chain splitting based on curvilinear 2D length (default False)

Type :

bool

use_split_pattern 

Turn on chain splitting based on dashed-line patterns (default False)

Type :

bool

use_texture 

Switch textured strokes on or off (default True)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.line_style BlendData.linestyles BlendDataLineStyles.new | BlendDataLineStyles.remove FreestyleLineSet.linestyle |

## FreestyleSettings(bpy_struct)

### FreestyleSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. FreestyleSettings ( bpy_struct ) 

The Freestyle configuration carried by a ViewLayer data-block

as_render_pass 

Output Freestyle results into their own pass rather than compositing them onto the Combined pass (default False)

Type :

bool

crease_angle 

Angle past which an edge counts as a crease (in [0, 3.14159], default 0.0)

Type :

float

kr_derivative_epsilon 

The Kr derivative epsilon used when calculating suggestive contours (in [-1000, 1000], default 0.0)

Type :

float

linesets 

(default None, readonly)

Type :

Linesets[FreestyleLineSet]

mode 

Pick which Freestyle control mode is in effect (default 'SCRIPT' )

- SCRIPT
Python Scripting – Advanced mode for using style modules written in Python.

- EDITOR
Parameter Editor – Basic mode for interactive style parameter editing.

Type :

Literal[‘SCRIPT’, ‘EDITOR’]

modules 

An ordered set of style modules, evaluated from the top down (default None, readonly)

Type :

FreestyleModules[FreestyleModuleSettings]

sphere_radius 

The sphere radius used when curvatures are computed (in [0, 1000], default 1.0)

Type :

float

use_culling 

When on, edges falling outside the view are skipped (default False)

Type :

bool

use_material_boundaries 

Turn on detection of material boundaries (default False)

Type :

bool

use_ridges_and_valleys 

Turn on detection of ridges and valleys (default False)

Type :

bool

use_smoothness 

Factor face smoothness into how the view map is built (default False)

Type :

bool

use_suggestive_contours 

Turn on detection of suggestive contours (default False)

Type :

bool

use_view_map_cache 

Reuse the stored view map and skip recomputing it while the mesh geometry stays the same (default False)

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

| ViewLayer.freestyle_settings | |

## FunctionNode(NodeInternal)

### FunctionNode(NodeInternal) 

base classes — bpy_struct, Node, NodeInternal

subclasses —
FunctionNodeAlignEulerToVector, FunctionNodeAlignRotationToVector, FunctionNodeAxesToRotation, FunctionNodeAxisAngleToRotation, FunctionNodeBitMath, FunctionNodeBooleanMath, FunctionNodeCombineColor, FunctionNodeCombineMatrix, FunctionNodeCombineTransform, FunctionNodeCompare, FunctionNodeEulerToRotation, FunctionNodeFindInString, FunctionNodeFloatToInt, FunctionNodeFormatString, FunctionNodeHashValue, FunctionNodeInputBool, FunctionNodeInputColor, FunctionNodeInputInt, FunctionNodeInputRotation, FunctionNodeInputSpecialCharacters, FunctionNodeInputString, FunctionNodeInputVector, FunctionNodeIntegerMath, FunctionNodeInvertMatrix, FunctionNodeInvertRotation, FunctionNodeMatchString, FunctionNodeMatrixDeterminant, FunctionNodeMatrixMultiply, FunctionNodeMatrixSVD, FunctionNodeProjectPoint, FunctionNodeQuaternionToRotation, FunctionNodeRandomValue, FunctionNodeReplaceString, FunctionNodeRotateEuler, FunctionNodeRotateRotation, FunctionNodeRotateVector, FunctionNodeRotationToAxisAngle, FunctionNodeRotationToEuler, FunctionNodeRotationToQuaternion, FunctionNodeSeparateColor, FunctionNodeSeparateMatrix, FunctionNodeSeparateTransform, FunctionNodeSliceString, FunctionNodeStringLength, FunctionNodeStringToValue, FunctionNodeTransformDirection, FunctionNodeTransformPoint, FunctionNodeTransposeMatrix, FunctionNodeValueToString

class bpy.types. FunctionNode ( NodeInternal ) 

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

## See also

- [Bpy Struct](bpy-struct.md)

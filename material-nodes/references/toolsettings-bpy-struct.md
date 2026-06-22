# Toolsettings Bpy Struct, Udimtile Bpy Struct, Udimtiles Bpy Prop Collection

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ToolSettings(bpy_struct); UDIMTile(bpy_struct); UDIMTiles(bpy_prop_collection).

## ToolSettings(bpy_struct)

### ToolSettings(bpy_struct) 

base class — bpy_struct

class bpy.types. ToolSettings ( bpy_struct ) 

anim_fix_to_cam_use_loc 

Insert location keys while fixing to the scene camera (default True)

Type :

bool

anim_fix_to_cam_use_rot 

Insert rotation keys while fixing to the scene camera (default True)

Type :

bool

anim_fix_to_cam_use_scale 

Insert scale keys while fixing to the scene camera (default True)

Type :

bool

anim_mirror_bone 

Which bone the mirroring is taken from (default “”, never None)

Type :

str

anim_mirror_object 

Object to mirror across. Leave it unset and supply a bone name to always mirror across that bone of the active armature

Type :

Object

anim_relative_object 

Object that matrices are taken relative to

Type :

Object

annotation_stroke_placement_view2d 

(default 'IMAGE' )

- IMAGE
Image – Stick stroke to the image.

- VIEW
View – Stick stroke to the view.

Type :

Literal[‘IMAGE’, ‘VIEW’]

annotation_stroke_placement_view3d 

The way annotation strokes are oriented within 3D space (default 'CURSOR' )

- CURSOR
3D Cursor – Draw stroke at 3D cursor location.

- VIEW
View – Stick stroke to the view.

- SURFACE
Surface – Stick stroke to surfaces.

Type :

Literal[‘CURSOR’, ‘VIEW’, ‘SURFACE’]

annotation_thickness 

Line thickness of annotation strokes (in [1, 10], default 3)

Type :

int

auto_keying_mode 

Adds extra conditions limiting when auto keying is allowed to insert keyframes (default '`ADD_REPLACE_KEYS`' )

Type :

Literal[‘`ADD_REPLACE_KEYS`’, ‘`REPLACE_KEYS`’]

curve_paint_settings 

(readonly, never None)

Type :

CurvePaintSettings

curves_sculpt 

(readonly)

Type :

CurvesSculpt

custom_bevel_profile_preset 

Used when shaping a profile’s path (readonly)

Type :

CurveProfile

double_threshold 

Distance under which Auto Merge collapses vertices (in [0, 1], default 0.001)

Type :

float

gpencil_interpolate 

Configuration for the Grease Pencil interpolation tools (readonly)

Type :

GPencilInterpolateSettings

gpencil_paint 

(readonly)

Type :

GpPaint

gpencil_sculpt 

Configuration for the stroke sculpting tools and brushes (readonly)

Type :

GPencilSculptSettings

gpencil_sculpt_paint 

(readonly)

Type :

GpSculptPaint

gpencil_selectmode_edit 

(default 'POINT' )

Type :

Literal[Grease Pencil Selectmode Items]

gpencil_stroke_placement_view3d 

(default 'ORIGIN' )

- ORIGIN
Origin – Draw stroke at Object origin.

- CURSOR
3D Cursor – Draw stroke at 3D cursor location.

- SURFACE
Surface – Stick stroke to surfaces.

- STROKE
Stroke – Stick stroke to other strokes.

Type :

Literal[‘ORIGIN’, ‘CURSOR’, ‘SURFACE’, ‘STROKE’]

gpencil_stroke_snap_mode 

(default 'NONE' )

- NONE
All Points – Snap to all points.

- ENDS
End Points – Snap to first and last points and interpolate.

- FIRST
First Point – Snap to first point.

Type :

Literal[‘NONE’, ‘ENDS’, ‘FIRST’]

gpencil_surface_offset 

How far along the normal strokes sit when drawn on surfaces (in [-inf, inf], default 0.15)

Type :

float

gpencil_vertex_paint 

(readonly)

Type :

GpVertexPaint

gpencil_weight_paint 

(readonly)

Type :

GpWeightPaint

image_paint 

(readonly)

Type :

ImagePaint

keyframe_type 

Which keyframe type new keyframes get when inserted (default 'KEYFRAME' )

Type :

Literal[Beztriple Keyframe Type Items]

lock_markers 

Stop markers from being edited (default False)

Type :

bool

lock_object_mode 

Limit selection to objects sharing the active object’s mode, so the mode is not switched by accident during selection (default True)

Type :

bool

mesh_select_mode 

Which mesh element types selection acts on (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

normal_vector 

Normal vector applied for copy, add, or multiply operations (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

paint_mode 

(readonly)

Type :

PaintModeSettings

particle_edit 

(readonly)

Type :

ParticleEdit

plane_axis 

Axis along which the base region is placed (default 'Z' )

Type :

Literal[Axis Xyz Items]

plane_axis_auto 

Pick the nearest axis when placing objects, with surfaces taking priority (default True)

Type :

bool

plane_depth 

Starting depth applied when placing the cursor (default 'SURFACE' )

- SURFACE
Surface – Start placing on the surface, using the 3D cursor position as a fallback.

- `CURSOR_PLANE`
Cursor Plane – Start placement using a point projected onto the orientation axis at the 3D cursor position.

- `CURSOR_VIEW`
Cursor View – Start placement using a point projected onto the view plane at the 3D cursor position.

Type :

Literal[‘SURFACE’, ‘`CURSOR_PLANE`’, ‘`CURSOR_VIEW`’]

plane_orientation 

Starting depth applied when placing the cursor (default 'SURFACE' )

- SURFACE
Surface – Use the surface normal (using the transform orientation as a fallback).

- DEFAULT
Default – Use the current transform orientation.

Type :

Literal[‘SURFACE’, ‘DEFAULT’]

playhead_snap_distance 

Largest pixel distance allowed for snapping (in [-inf, inf], default 20)

Type :

int

proportional_distance 

On-screen radius of the proportional editing circle (in [1e-05, 5000], default 1.0)

Type :

float

proportional_edit_falloff 

Falloff curve used by proportional editing mode (default 'SMOOTH' )

Type :

Literal[Proportional Falloff Items]

proportional_size 

On-screen radius of the proportional editing circle (in [1e-05, 5000], default 1.0)

Type :

float

sculpt 

(readonly)

Type :

Sculpt

sequencer_tool_settings 

(readonly, never None)

Type :

SequencerToolSettings

show_uv_local_view 

Show only the faces that have the currently displayed image assigned (default False)

Type :

bool

snap_angle_increment_2d 

Step size for rotation increments inside 2D editors (in [0, 3.14159], default 0.0872665)

Type :

float

snap_angle_increment_2d_precision 

Fine step size for rotation increments inside 2D editors (in [0, 3.14159], default 0.0174533)

Type :

float

snap_angle_increment_3d 

Step size for rotation increments inside 3D editors (in [0, 3.14159], default 0.0872665)

Type :

float

snap_angle_increment_3d_precision 

Fine step size for rotation increments inside 3D editors (in [0, 3.14159], default 0.0174533)

Type :

float

snap_anim_element 

Which element kind to snap onto (default 'FRAME' )

Type :

Literal[Snap Animation Element Items]

snap_elements 

Which element kind to snap onto (default { 'INCREMENT' })

Type :

set[Literal[Snap Element Items]]

snap_elements_base 

Which element kind the “Snap Base” snaps onto (default { 'INCREMENT' })

- INCREMENT
Increment – Snap to increments.

- GRID
Grid – Snap to grid.

- VERTEX
Vertex – Snap to vertices.

- EDGE
Edge – Snap to edges.

- FACE
Face – Snap by projecting onto faces.

- VOLUME
Volume – Snap to volume.

- `EDGE_MIDPOINT`
Edge Center – Snap to the middle of edges.

- `EDGE_PERPENDICULAR`
Edge Perpendicular – Snap to the nearest point on an edge.

- `FACE_MIDPOINT`
Face Center – Snap to the middle of faces.

Type :

set[Literal[‘INCREMENT’, ‘GRID’, ‘VERTEX’, ‘EDGE’, ‘FACE’, ‘VOLUME’, ‘`EDGE_MIDPOINT`’, ‘`EDGE_PERPENDICULAR`’, ‘`FACE_MIDPOINT`’]]

snap_elements_individual 

Which element kind individually transformed elements snap onto (default set())

- `FACE_PROJECT`
Face Project – Snap by projecting onto faces.

- `FACE_NEAREST`
Face Nearest – Snap to nearest point on faces.

Type :

set[Literal[‘`FACE_PROJECT`’, ‘`FACE_NEAREST`’]]

snap_elements_tool 

Which target snapping should aim at (default 'GEOMETRY' )

- GEOMETRY
Geometry – Snap to all geometry.

- DEFAULT
Default – Use the current snap settings.

Type :

Literal[‘GEOMETRY’, ‘DEFAULT’]

snap_face_nearest_steps 

How many sub-steps a transform is split into for face nearest snapping (in [1, 100], default 1)

Type :

int

snap_playhead_element 

Which element kind to snap onto (default { 'KEY' , 'Strip' })

- FRAME
Frames – Snap to frame increments.

- SECOND
Seconds – Snap to second increments.

- MARKER
Markers – Snap to markers.

- KEY
Keyframes – Snap to keyframes.

- Strip
Strips – Snap to Strips.

Type :

set[Literal[‘FRAME’, ‘SECOND’, ‘MARKER’, ‘KEY’, ‘Strip’]]

snap_playhead_frame_step 

Frame interval the playhead snaps to (in [1, 32768], default 2)

Type :

int

snap_playhead_second_step 

Second interval the playhead snaps to (in [1, 32768], default 1)

Type :

int

snap_target 

Which portion of the source is placed onto the target (default 'CLOSEST' )

Type :

Literal[Snap Source Items]

snap_uv_element 

Which element kind to snap onto (default { 'INCREMENT' })

- INCREMENT
Increment – Snap to increments of grid.

- GRID
Grid – Snap to grid.

- VERTEX
Vertex – Snap to vertices.

Type :

set[Literal[‘INCREMENT’, ‘GRID’, ‘VERTEX’]]

statvis 

(readonly, never None)

Type :

MeshStatVis

transform_pivot_point 

Center used when rotating or scaling (default '`MEDIAN_POINT`' )

- `BOUNDING_BOX_CENTER`
Bounding Box Center – Pivot around bounding box center of selected object(s).

- CURSOR
3D Cursor – Pivot around the 3D cursor.

- `INDIVIDUAL_ORIGINS`
Individual Origins – Pivot around each object’s own origin.

- `MEDIAN_POINT`
Median Point – Pivot around the median point of selected objects.

- `ACTIVE_ELEMENT`
Active Element – Pivot around active object.

Type :

Literal[‘`BOUNDING_BOX_CENTER`’, ‘CURSOR’, ‘`INDIVIDUAL_ORIGINS`’, ‘`MEDIAN_POINT`’, ‘`ACTIVE_ELEMENT`’]

use_annotation_project_only_selected 

Limit stroke projection to selected objects (default False)

Type :

bool

use_annotation_stroke_endpoints 

Snap using only the stroke’s first and last segments (default False)

Type :

bool

use_auto_normalize 

Keep every bone-deforming vertex group summing to 1.0 during weight painting or vertex assignment (default False)

Type :

bool

use_edge_path_live_unwrap 

Recompute the UV unwrap whenever edge seams change (default False)

Type :

bool

use_gpencil_automerge_strokes 

Merge the most recent stroke into nearby strokes on the active layer by distance (default False)

Type :

bool

use_gpencil_draw_additive 

When a new frame is made, carry over the strokes of the previous or active frame as its starting point (default False)

Type :

bool

use_gpencil_draw_onback 

Place new strokes beneath every existing stroke in the layer (default False)

Type :

bool

use_gpencil_project_only_selected 

Limit stroke projection to selected objects (default False)

Type :

bool

use_gpencil_select_mask_point 

Sculpt only the selected stroke points (default False)

Type :

bool

use_gpencil_select_mask_segment 

Sculpt only the selected stroke points lying between other strokes (default False)

Type :

bool

use_gpencil_select_mask_stroke 

Sculpt only the selected strokes (default False)

Type :

bool

use_gpencil_thumbnail_list 

Use a compact color list rather than thumbnails (default True)

Type :

bool

use_gpencil_vertex_select_mask_point 

Paint only the selected stroke points (default False)

Type :

bool

use_gpencil_vertex_select_mask_segment 

Paint only the selected stroke points lying between other strokes (default False)

Type :

bool

use_gpencil_vertex_select_mask_stroke 

Paint only the selected strokes (default False)

Type :

bool

use_gpencil_weight_data_add 

New strokes receive weight data from the active vertex group and weight. With no vertex group chosen, no weight is added. (default False)

Type :

bool

use_grease_pencil_multi_frame_editing 

Turn on multi-frame editing (default False)

Type :

bool

use_keyframe_cycle_aware 

On channels with cyclic extrapolation, inserted keyframes are remapped into the cycle’s time range and the ends are kept matched. Curves freshly added to actions that use a Manual Frame Range with Cyclic Animation become cyclic automatically. (default False)

Type :

bool

use_keyframe_insert_auto 

Insert keyframes automatically when properties change (default True)

Type :

bool

use_keyframe_insert_keyingset 

Use only the active Keying Set for automatic keyframe insertion (default False)

Type :

bool

use_lock_relative 

Show bone-deforming groups as though every locked deform group were removed and the rest re-normalized (default False)

Type :

bool

use_mesh_automerge 

Merge vertices automatically once they share a location (default False)

Type :

bool

use_mesh_automerge_and_split 

Split edges and faces automatically (default False)

Type :

bool

use_multipaint 

Paint over the weights of every selected bone while keeping their relative influence (default False)

Type :

bool

use_proportional_action 

Use proportional editing within the action editor (default False)

Type :

bool

use_proportional_connected 

Restrict proportional editing to connected geometry (default False)

Type :

bool

use_proportional_edit 

Turn on proportional edit mode (default False)

Type :

bool

use_proportional_edit_mask 

Turn on proportional editing in mask mode (default False)

Type :

bool

use_proportional_edit_objects 

Turn on proportional editing in object mode (default False)

Type :

bool

use_proportional_fcurve 

Use proportional editing within the F-Curve editor (default False)

Type :

bool

use_proportional_projected 

Base proportional editing on screen-space positions (default False)

Type :

bool

use_record_with_nla 

For each loop or pass over the animation, add a fresh NLA Track and Strip so edits stay non-destructive (default False)

Type :

bool

use_snap 

Snap while transforming (default False)

Type :

bool

use_snap_align_rotation 

Match rotation to the snapping target (default False)

Type :

bool

use_snap_anim 

Snap while transforming keyframes (default True)

Type :

bool

use_snap_backface_culling 

Leave back-facing geometry out of snapping (default False)

Type :

bool

use_snap_driver 

Snap while transforming keys within the Driver Editor (default False)

Type :

bool

use_snap_driver_absolute 

Snap onto whole values (default False)

Type :

bool

use_snap_edit 

Snap onto other objects in edit mode (edit mode only) (default True)

Type :

bool

use_snap_grid_absolute 

Use absolute grid alignment when translating, based on the pivot center (default False)

Type :

bool

use_snap_node 

Snap nodes while transforming (default False)

Type :

bool

use_snap_nonedit 

Snap onto objects outside edit mode (edit mode only) (default True)

Type :

bool

use_snap_peel_object 

Treat objects as whole when locating the volume center (default False)

Type :

bool

use_snap_playhead 

Snap the playhead while scrubbing (default False)

Type :

bool

use_snap_rotate 

Apply snapping settings to rotation (default False)

Type :

bool

use_snap_scale 

Apply snapping settings to scaling (default False)

Type :

bool

use_snap_selectable 

Snap only onto objects that can be selected (default False)

Type :

bool

use_snap_self 

Snap onto itself only when enabled (edit mode only) (default True)

Type :

bool

use_snap_sequencer 

Snap strips while transforming (default True)

Type :

bool

use_snap_time_absolute 

Use absolute time alignment when transforming keyframes (default False)

Type :

bool

use_snap_to_same_target 

Snap only onto the target the source started near (“Face Nearest” only) (default False)

Type :

bool

use_snap_translate 

Apply snapping settings to movement (default True)

Type :

bool

use_snap_uv 

Snap UVs while transforming (default False)

Type :

bool

use_transform_correct_face_attributes 

Adjust data such as UVs and color attributes during a transform (default False)

Type :

bool

use_transform_correct_keep_connected 

While correcting Face Attributes, merge attributes that share a vertex (default False)

Type :

bool

use_transform_data_origin 

Move object origins while keeping the shape where it is (default False)

Type :

bool

use_transform_pivot_point_align 

Move only object locations, leaving rotation and scale untouched (default False)

Type :

bool

use_transform_skip_children 

Transform the parents while leaving children where they are (default False)

Type :

bool

use_uv_custom_region 

A user-defined region (default False)

Type :

bool

use_uv_select_island 

Select by island (default False)

Type :

bool

use_uv_select_sync 

Keep the UV selection in sync with the edit-mode mesh selection (default True)

Type :

bool

uv_sculpt 

(readonly)

Type :

UvSculpt

uv_sculpt_all_islands 

Have the brush act on every island (default False)

Type :

bool

uv_sculpt_lock_borders 

Stop boundary edges from being edited (default False)

Type :

bool

uv_select_mode 

Selection and display mode for UVs (default 'VERTEX' )

Type :

Literal[Mesh Select Mode Uv Items]

uv_sticky_select_mode 

How UV vertex selection is extended (default '`SHARED_LOCATION`' )

- DISABLED
Disabled – Sticky vertex selection disabled.

- `SHARED_LOCATION`
Shared Location – Select UVs that are at the same location and share a mesh vertex.

- `SHARED_VERTEX`
Shared Vertex – Select UVs that share a mesh vertex, whether or not they are at the same location.

Type :

Literal[‘DISABLED’, ‘`SHARED_LOCATION`’, ‘`SHARED_VERTEX`’]

vertex_group_subset 

Restrict which Vertex groups are shown (default 'ALL' )

- ALL
All – All Vertex Groups.

- `BONE_DEFORM`
Deform – Vertex Groups assigned to Deform Bones.

- `OTHER_DEFORM`
Other – Vertex Groups assigned to non Deform Bones.

Type :

Literal[‘ALL’, ‘`BONE_DEFORM`’, ‘`OTHER_DEFORM`’]

vertex_group_user 

Show vertices that carry no weight (default 'ACTIVE' )

- NONE
None.

- ACTIVE
Active – Show vertices with no weights in the active group.

- ALL
All – Show vertices with no weights in any group.

Type :

Literal[‘NONE’, ‘ACTIVE’, ‘ALL’]

vertex_group_weight 

Weight given when assigning to vertex groups (in [0, 1], default 1.0)

Type :

float

vertex_paint 

(readonly)

Type :

VertexPaint

weight_paint 

(readonly)

Type :

VertexPaint

workspace_tool_type 

What happens when dragging inside the viewport (default 'FALLBACK' )

Type :

Literal[‘DEFAULT’, ‘FALLBACK’]

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

| bpy.context.tool_settings Context.tool_settings | Scene.tool_settings |

## UDIMTile(bpy_struct)

### UDIMTile(bpy_struct) 

base class — bpy_struct

class bpy.types. UDIMTile ( bpy_struct ) 

Properties belonging to a UDIM tile.

channels 

How many channels the tile’s pixel buffer holds (in [0, inf], default 0, readonly)

Type :

int

generated_color 

Color used to fill the generated image (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

generated_height 

Height of the generated image (in [1, 65536], default 0)

Type :

int

generated_type 

Kind of image to generate (default 'BLANK' )

Type :

Literal[Image Generated Type Items]

generated_width 

Width of the generated image (in [1, 65536], default 0)

Type :

int

is_generated_tile 

Whether this image tile was generated (default False, readonly)

Type :

bool

label 

Label of the tile (default “”, never None)

Type :

str

number 

Index of the position covered by this tile (in [-inf, inf], default 0)

Type :

int

size 

Pixel width and height of the tile buffer, reported as zero when the image data cannot load (array of 2 items, in [-inf, inf], default (0, 0), readonly)

Type :

bpy_prop_array[int]

use_generated_float 

Produce a floating-point buffer (default False)

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

| Image.tiles UDIMTiles.active UDIMTiles.get | UDIMTiles.new UDIMTiles.remove |

## UDIMTiles(bpy_prop_collection)

### UDIMTiles(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. UDIMTiles ( bpy_prop_collection ) 

A set holding the UDIM tiles.

active 

Active Image Tile (never None)

Type :

UDIMTile

active_index 

Active index in tiles array (in [0, inf], default 0)

Type :

int

new ( tile_number , * , label = '' ) 

Add a tile to the image

Parameters :

- tile_number ( int ) – Number of the newly created tile (in [1, inf])

- label ( str ) – Optional label for the tile (optional, never None)

Returns :

Newly created image tile

Return type :

UDIMTile

get ( tile_number ) 

Get a tile based on its tile number

Parameters :

tile_number ( int ) – Number of the tile (in [0, inf])

Returns :

The tile

Return type :

UDIMTile

remove ( tile ) 

Remove an image tile

Parameters :

tile (UDIMTile) – Image tile to remove (never None)

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

| Image.tiles | |

## See also

- [Bpy Struct](bpy-struct.md)

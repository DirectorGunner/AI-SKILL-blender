# Brush Id (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Type :

float

unprojected_size

Brush diameter expressed in Blender units (in [0.001, inf], default 0.1)

Type :

float

use_accumulate

Build stroke daubs up over one another (default False)

Type :

bool

use_adaptive_space

Space daubs by surface orientation rather than by screen space (default False)

Type :

bool

use_alpha

With this off, alpha stays locked while painting (default True)

Type :

bool

use_automasking_boundary_edges

Leave non-manifold boundary edges untouched (default False)

Type :

bool

use_automasking_boundary_face_sets

Leave vertices on a face set boundary untouched (default False)

Type :

bool

use_automasking_cavity

Leave peak vertices untouched, judged by surface curvature (default False)

Type :

bool

use_automasking_cavity_inverted

Leave vertices inside crevices untouched, judged by surface curvature (default False)

Type :

bool

use_automasking_custom_cavity_curve

Apply a custom curve (default False)

Type :

bool

use_automasking_face_sets

Touch only vertices sharing face sets with the active vertex (default False)

Type :

bool

use_automasking_start_normal

Touch only vertices whose normal resembles the one where the stroke begins (default False)

Type :

bool

use_automasking_topology

Touch only vertices linked to the active vertex beneath the brush (default False)

Type :

bool

use_automasking_view_normal

Touch only vertices whose normal points toward the viewer (default False)

Type :

bool

use_automasking_view_occlusion

Touch only vertices that no other faces hide (slower performance) (default False)

Type :

bool

use_cloth_collision

Let the simulation collide with objects (default False)

Type :

bool

use_cloth_pin_simulation_boundary

Pin the vertices in the simulation falloff region to prevent artifacts and ease the transition into unaffected areas (default False)

Type :

bool

use_color_as_displacement

Treat each pixel's color as its own displacement vector (area plane mapping only) (default False)

Type :

bool

use_color_jitter

Apply jitter to the brush color (default False)

Type :

bool

use_connected_only

Touch only topologically connected elements (default False)

Type :

bool

use_cursor_overlay

Display the cursor in the viewport (default False)

Type :

bool

use_cursor_overlay_override

Hide the overlay while a stroke is in progress (default False)

Type :

bool

use_density_pressure

Let pressure drive density (default False)

Type :

bool

use_edge_to_edge

Drag the anchor brush across from one edge to another (default False)

Type :

bool

use_flow_pressure

Let pressure drive flow (default False)

Type :

bool

use_frontface

Have the brush touch only vertices facing the viewer (default False)

Type :

bool

use_frontface_falloff

Scale brush influence by how directly vertices face the front (default False)

Type :

bool

use_grab_active_vertex

Direct the full grab strength onto the active vertex rather than the cursor position (default False)

Type :

bool

use_grab_silhouette

Have grabs attempt to automask the object's silhouette (default False)

Type :

bool

use_hardness_pressure

Let pressure drive hardness (default False)

Type :

bool

use_inverse_smooth_pressure

Lighter pressure yields more smoothing (default False)

Type :

bool

use_locked_size

Whether brush size is gauged against the view or the scene (default 'VIEW' )

- VIEW
View – Gauge brush size against the view.

- SCENE
Scene – Gauge brush size against the scene.

Type :

Literal['VIEW', 'SCENE']

use_multiplane_scrape_dynamic

Let the angle between the planes shift during the stroke to match the surface beneath the cursor (default False)

Type :

bool

use_offset_pressure

Turn on tablet pressure sensitivity for offset (default False)

Type :

bool

use_original_normal

While locked, keep using the surface normal from where the stroke began (default False)

Type :

bool

use_original_plane

While locked, keep using the plane origin of the surface where the stroke began (default False)

Type :

bool

use_paint_antialiasing

Soften the edges of the strokes (default True)

Type :

bool

use_paint_grease_pencil

Make this brush available in Grease Pencil drawing mode (default False)

Type :

bool

use_paint_image

Make this brush available in texture paint mode (default True)

Type :

bool

use_paint_sculpt

Make this brush available in sculpt mode (default True)

Type :

bool

use_paint_sculpt_curves

Make this brush available in sculpt curves mode (default False)

Type :

bool

use_paint_uv_sculpt

Make this brush available in UV sculpt mode (default False)

Type :

bool

use_paint_vertex

Make this brush available in vertex paint mode (default True)

Type :

bool

use_paint_weight

Make this brush available in weight paint mode (default True)

Type :

bool

use_persistent

Sculpt against a persistent layer of the mesh (default False)

Type :

bool

use_plane_trim

Cap how far from the offset plane a vertex may be affected (default False)

Type :

bool

use_pose_ik_anchored

Hold the last segment of the IK chain in place (default False)

Type :

bool

use_pose_lock_rotation

Skip rotating the segment when in scale deform mode (default False)

Type :

bool

use_pressure_area_radius

Turn on tablet pressure sensitivity for area radius (default False)

Type :

bool

use_pressure_jitter

Turn on tablet pressure sensitivity for jitter (default False)

Type :

bool

use_pressure_masking

Have pen pressure shrink the texture's influence (default 'NONE' )

Type :

Literal['NONE', 'RAMP', 'CUTOFF']

use_pressure_size

Turn on tablet pressure sensitivity for size (default False)

Type :

bool

use_pressure_spacing

Turn on tablet pressure sensitivity for spacing (default False)

Type :

bool

use_pressure_strength

Turn on tablet pressure sensitivity for strength (default True)

Type :

bool

use_primary_overlay

Display the texture in the viewport (default False)

Type :

bool

use_primary_overlay_override

Hide the overlay while a stroke is in progress (default False)

Type :

bool

use_random_press_hue

Let pressure drive randomness (default False)

Type :

bool

use_random_press_sat

Let pressure drive randomness (default False)

Type :

bool

use_random_press_val

Let pressure drive randomness (default False)

Type :

bool

use_scene_spacing

Whether brush spacing is computed from view distance or scene distance (default 'VIEW' )

- VIEW
View – Compute brush spacing against the view.

- SCENE
Scene – Compute brush spacing against the scene, using the stroke location.

Type :

Literal['VIEW', 'SCENE']

use_secondary_overlay

Display the texture in the viewport (default False)

Type :

bool

use_secondary_overlay_override

Hide the overlay while a stroke is in progress (default False)

Type :

bool

use_smooth_stroke

Have the brush trail behind the mouse along a smoother path (default False)

Type :

bool

use_space_attenuation

Tweak strength automatically so different spacings give consistent results (default True)

Type :

bool

use_stroke_random_hue

Apply randomness at the stroke level (default False)

Type :

bool

use_stroke_random_sat

Apply randomness at the stroke level (default False)

Type :

bool

use_stroke_random_val

Apply randomness at the stroke level (default False)

Type :

bool

use_vertex_grease_pencil

Make this brush available in Grease Pencil vertex color mode (default False)

Type :

bool

use_wet_mix_pressure

Let pressure drive wet mix (default False)

Type :

bool

use_wet_persistence_pressure

Let pressure drive wet persistence (default False)

Type :

bool

value_jitter

How much color jitter is applied to value (in [0, 1], default 0.0)

Type :

float

vertex_brush_type

(default 'DRAW' )

Type :

Literal[Brush Vertex Brush Type Items]

vertex_paint_capabilities

(readonly, never None)

Type :

BrushCapabilitiesVertexPaint

weight

Weight assigned to vertices where the brush is applied (in [0, 1], default 1.0)

Type :

float

weight_brush_type

(default 'DRAW' )

Type :

Literal[Brush Weight Brush Type Items]

weight_paint_capabilities

(readonly, never None)

Type :

BrushCapabilitiesWeightPaint

wet_mix

How much paint is lifted off the surface back into the brush color (in [0, 1], default 0.0)

Type :

float

wet_paint_radius_factor

Proportion of the brush radius used when sampling the color blended into wet paint (in [0, 2], default 0.5)

Type :

float

wet_persistence

How much wet paint lingers in the brush after it is applied to the surface (in [0, 1], default 0.0)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.brush BlendData.brushes BlendDataBrushes.create_gpencil_data BlendDataBrushes.new | BlendDataBrushes.remove Paint.brush Paint.eraser_brush |

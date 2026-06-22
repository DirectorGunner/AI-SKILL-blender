# Spaceuveditor Bpy Struct, Spaceview3D Space, Spline Bpy Struct, Spotlight Light

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpaceUVEditor(bpy_struct); SpaceView3D(Space); Spline(bpy_struct); SpotLight(Light).

## SpaceUVEditor(bpy_struct)

### SpaceUVEditor(bpy_struct)

base class — bpy_struct

class bpy.types. SpaceUVEditor ( bpy_struct )

UV editor data belonging to the image editor space

custom_grid_subdivisions

Count of grid units within UV space that constitute a single UV Unit (array of 2 items, in [1, 5000], default (0, 0))

Type :

bpy_prop_array[int]

display_stretch_type

Which stretch measure to show (default 'ANGLE' )

- ANGLE
Angle – Distortion of angles between UV and 3D.

- AREA
Area – Distortion of areas between UV and 3D faces.

Type :

Literal[‘ANGLE’, ‘AREA’]

edge_display_type

How UV edges are styled (default 'OUTLINE' )

- OUTLINE
Outline – Draw white edges outlined in black.

- DASH
Dash – Draw black-and-white dashed edges.

- BLACK
Black – Draw edges in black.

- WHITE
White – Draw edges in white.

Type :

Literal[‘OUTLINE’, ‘DASH’, ‘BLACK’, ‘WHITE’]

grid_shape_source

Where the grid shape is sourced from (default 'DYNAMIC' )

- DYNAMIC
Dynamic – A grid that adapts dynamically.

- FIXED
Fixed – Grid divisions you set by hand.

- PIXEL
Pixel – A grid that lines up with the image's pixels.

Type :

Literal[‘DYNAMIC’, ‘FIXED’, ‘PIXEL’]

lock_bounds

Keep edits confined within the image bounds (default False)

Type :

bool

pixel_round_mode

Snap UVs to pixels during editing (default 'DISABLED' )

- DISABLED
Disabled – Perform no pixel rounding.

- CORNER
Corner – Snap to the corners of pixels.

- CENTER
Center – Snap to the centers of pixels.

Type :

Literal[‘DISABLED’, ‘CORNER’, ‘CENTER’]

show_faces

Draw faces on top of the image (default True)

Type :

bool

show_grid_over_image

Draw the grid on top of the image (default True)

Type :

bool

show_metadata

Show the image's metadata properties (default False)

Type :

bool

show_modified_edges

Show edges once modifiers have been applied (default False)

Type :

bool

show_pixel_coords

Give UV coordinates in pixels instead of the 0.0 to 1.0 range (default True)

Type :

bool

show_stretch

Color faces by how much UV shape diverges from 3D shape (blue marks little distortion, red marks heavy distortion) (default False)

Type :

bool

show_uv

Show the UV layer as an overlay (default True)

Type :

bool

stretch_opacity

How opaque the UV Stretch overlay is (in [0, 1], default 0.0)

Type :

float

tile_grid_shape

Number of tiles drawn behind the image (array of 2 items, in [1, 100], default (0, 0))

Type :

bpy_prop_array[int]

use_live_unwrap

Re-unwrap the chosen UV island on the fly as pinned vertices are moved (default False)

Type :

bool

uv_edge_opacity

How opaque edges are within UV overlays (in [0, 1], default 0.0)

Type :

float

uv_face_opacity

How opaque faces are within UV overlays (in [0, 1], default 0.0)

Type :

float

uv_opacity

How opaque the UV overlays are (in [0, 1], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceImageEditor.uv_editor | |

## SpaceView3D(Space)

### SpaceView3D(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceView3D ( Space )

Data for the 3D View space

camera

Camera that is active in this view (once unlocked from the scene's active camera)

Type :

Object

clip_end

Far clipping distance of the 3D View (in [1e-06, inf], default 1000.0)

Type :

float

clip_start

Near clipping distance of the 3D View (perspective view only) (in [1e-06, inf], default 0.01)

Type :

float

icon_from_show_object_viewport

(in [-inf, inf], default 0, readonly)

Type :

int

lens

Lens angle of the viewport (in [1, 250], default 50.0)

Type :

float

local_view

Show only an isolated subset of objects, separate from scene visibility (readonly)

Type :

SpaceView3D

lock_bone

Pin the 3D View center onto this bone's position (default “”, never None)

Type :

str

lock_camera

Allow navigation of the view while inside the camera view (default False)

Type :

bool

lock_cursor

Pin the 3D View center onto the cursor's position (default False)

Type :

bool

lock_object

Pin the 3D View center onto this object's position

Type :

Object

mirror_xr_session

Keep the viewer perspective of VR sessions in sync with this 3D viewport (default False)

Type :

bool

overlay

Configuration for how overlays appear in the 3D viewport (readonly, never None)

Type :

View3DOverlay

region_3d

The 3D region of this space; in quad view, this is the camera region (readonly)

Type :

RegionView3D

region_quadviews

The 3D regions (the third holds quad view settings; the fourth matches 'region_3d') (default None, readonly)

Type :

bpy_prop_collection[RegionView3D]

render_border_max_x

Largest X value of the render region (in [0, 1], default 0.0)

Type :

float

render_border_max_y

Largest Y value of the render region (in [0, 1], default 0.0)

Type :

float

render_border_min_x

Smallest X value of the render region (in [0, 1], default 0.0)

Type :

float

render_border_min_y

Smallest Y value of the render region (in [0, 1], default 0.0)

Type :

float

shading

Configuration for shading in the 3D viewport (readonly, never None)

Type :

View3DShading

show_bundle_names

Display names for the objects of reconstructed tracks (default False)

Type :

bool

show_camera_path

Display the reconstructed path of the camera (default False)

Type :

bool

show_gizmo

Reveal every kind of gizmo (default True)

Type :

bool

show_gizmo_camera_dof_distance

Gizmo for tuning the camera's focus distance (relies on limits display) (default False)

Type :

bool

show_gizmo_camera_lens

Gizmo for tuning the camera's focal length or orthographic scale (default False)

Type :

bool

show_gizmo_context

Gizmos that adapt to the active item's context (default True)

Type :

bool

show_gizmo_empty_force_field

Gizmo for tuning the force field (default False)

Type :

bool

show_gizmo_empty_image

Gizmo for tuning image size and position (default False)

Type :

bool

show_gizmo_light_look_at

Gizmo for steering the light's direction (default False)

Type :

bool

show_gizmo_light_size

Gizmo for tuning spot and area size (default False)

Type :

bool

show_gizmo_modifier

Gizmos belonging to the active modifier (default True)

Type :

bool

show_gizmo_navigate

Gizmo for moving around the viewport (default True)

Type :

bool

show_gizmo_object_rotate

Gizmo for tuning rotation (default False)

Type :

bool

show_gizmo_object_scale

Gizmo for tuning scale (default False)

Type :

bool

show_gizmo_object_translate

Gizmo for tuning location (default False)

Type :

bool

show_gizmo_tool

Gizmo for the active tool (default True)

Type :

bool

show_object_select_armature

Permit armatures to be selected (default True)

Type :

bool

show_object_select_camera

Permit cameras to be selected (default True)

Type :

bool

show_object_select_curve

Permit curves to be selected (default True)

Type :

bool

show_object_select_curves

Permit hair curves to be selected (default True)

Type :

bool

show_object_select_empty

Permit empties to be selected (default True)

Type :

bool

show_object_select_font

Permit text objects to be selected (default True)

Type :

bool

show_object_select_grease_pencil

Permit Grease Pencil objects to be selected (default True)

Type :

bool

show_object_select_lattice

Permit lattices to be selected (default True)

Type :

bool

show_object_select_light

Permit lights to be selected (default True)

Type :

bool

show_object_select_light_probe

Permit light probes to be selected (default True)

Type :

bool

show_object_select_mesh

Permit mesh objects to be selected (default True)

Type :

bool

show_object_select_meta

Permit metaballs to be selected (default True)

Type :

bool

show_object_select_pointcloud

Permit point clouds to be selected (default True)

Type :

bool

show_object_select_speaker

Permit speakers to be selected (default True)

Type :

bool

show_object_select_surf

Permit surfaces to be selected (default True)

Type :

bool

show_object_select_volume

Permit volumes to be selected (default True)

Type :

bool

show_object_viewport_armature

Display armatures (default True)

Type :

bool

show_object_viewport_camera

Display cameras (default True)

Type :

bool

show_object_viewport_curve

Display curves (default True)

Type :

bool

show_object_viewport_curves

Display hair curves (default True)

Type :

bool

show_object_viewport_empty

Display empties (default True)

Type :

bool

show_object_viewport_font

Display text objects (default True)

Type :

bool

show_object_viewport_grease_pencil

Display Grease Pencil objects (default True)

Type :

bool

show_object_viewport_lattice

Display lattices (default True)

Type :

bool

show_object_viewport_light

Display lights (default True)

Type :

bool

show_object_viewport_light_probe

Display light probes (default True)

Type :

bool

show_object_viewport_mesh

Display mesh objects (default True)

Type :

bool

show_object_viewport_meta

Display metaballs (default True)

Type :

bool

show_object_viewport_pointcloud

Display point clouds (default True)

Type :

bool

show_object_viewport_speaker

Display speakers (default True)

Type :

bool

show_object_viewport_surf

Display surfaces (default True)

Type :

bool

show_object_viewport_volume

Display volumes (default True)

Type :

bool

show_reconstruction

Display reconstruction data taken from the active movie clip (default True)

Type :

bool

show_region_asset_shelf

Display a region holding assets that may be relevant right now (for example, brushes while painting, or poses during Pose Mode) (default False)

Type :

bool

show_region_hud

(default False)

Type :

bool

show_region_tool_header

(default False)

Type :

bool

show_region_toolbar

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

show_stereo_3d_cameras

Display both the left and right cameras (default False)

Type :

bool

show_stereo_3d_convergence_plane

Display the convergence plane for stereo 3D (default True)

Type :

bool

show_stereo_3d_volume

Display the frustum volume for stereo 3D (default False)

Type :

bool

show_viewer

Display non-final geometry coming from viewer nodes (default True)

Type :

bool

stereo_3d_camera

(default 'S3D' )

Type :

Literal[‘LEFT’, ‘RIGHT’, ‘S3D’]

stereo_3d_convergence_plane_alpha

Opacity (alpha) applied to the convergence plane (in [0, 1], default 0.15)

Type :

float

stereo_3d_eye

The stereo eye shown at the moment (default '`LEFT_EYE`' , readonly)

Type :

Literal[‘`LEFT_EYE`’, ‘`RIGHT_EYE`’]

stereo_3d_volume_alpha

Opacity (alpha) applied to the frustum volume of the cameras (in [0, 1], default 0.05)

Type :

float

tracks_display_size

How large tracks from reconstructed data appear (in [0, inf], default 0.2)

Type :

float

tracks_display_type

Style used to draw tracks in the viewport (default '`PLAIN_AXES`' )

Type :

Literal[‘`PLAIN_AXES`’, ‘ARROWS’, ‘`SINGLE_ARROW`’, ‘CIRCLE’, ‘CUBE’, ‘SPHERE’, ‘CONE’]

use_local_camera

Rely on a local camera here rather than the scene's active camera (default False)

Type :

bool

use_local_collections

Show a separate set of collections within this viewport (default False)

Type :

bool

use_render_border

Restrict the rendered viewport to a region inside the frame (except when looking through the camera) (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this space type. The handler runs each time the named region of the
space type is redrawn. Keep in mind that, for the moment, every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – Function invoked while the region is being drawn.
The supplied arguments are passed to it, and whatever it returns is discarded.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – Which region type the callback renders into; typically WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Generally `POST_PIXEL` for 2D and `POST_VIEW` for 3D; `PRE_VIEW` occasionally applies, and BACKDROP serves node-editor backdrops.

Returns :

A handler you can later remove.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to detach.

- region_type ( str ) – Region type to which the callback had been attached.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

### References

| Object.local_view_get Object.local_view_set Object.visible_get | Object.visible_in_viewport_get SpaceView3D.local_view |

## Spline(bpy_struct)

### Spline(bpy_struct)

base class — bpy_struct

class bpy.types. Spline ( bpy_struct )

A single curve element: NURBS, Bézier, Polyline, or a character on text objects

bezier_points

Set of points used solely by Bézier curves (default None, readonly)

Type :

SplineBezierPoints[BezierSplinePoint]

character_index

Where this character sits within the text data (text curves only) (in [0, inf], default 0, readonly)

Type :

int

hide

Conceal this curve while in Edit mode (default False)

Type :

bool

material_index

Index of this curve's material slot (in [0, 32767], default 0)

Type :

int

order_u

NURBS order along U. Larger values let each point affect a wider area, but slow things down. (in [2, 64], default 0)

Type :

int

order_v

NURBS order along V. Larger values let each point affect a wider area, but slow things down. (in [2, 64], default 0)

Type :

int

point_count_u

Number of points along U for the curve or surface (in [0, inf], default 0, readonly)

Type :

int

point_count_v

Number of points along V for the surface (in [0, inf], default 0, readonly)

Type :

int

points

Set of points forming this poly or nurbs spline (default None, readonly)

Type :

SplinePoints[SplinePoint]

radius_interpolation

How radius is interpolated for Bézier curves (default 'LINEAR' )

Type :

Literal[‘LINEAR’, ‘CARDINAL’, ‘BSPLINE’, ‘EASE’]

resolution_u

Subdivisions per segment of the curve or surface (in [1, 1024], default 0)

Type :

int

resolution_v

Subdivisions per segment of the surface (in [1, 1024], default 0)

Type :

int

tilt_interpolation

How tilt is interpolated for 3D Bézier curves (default 'LINEAR' )

Type :

Literal[‘LINEAR’, ‘CARDINAL’, ‘BSPLINE’, ‘EASE’]

type

Interpolation type for this curve element (default 'POLY' )

Type :

Literal[‘POLY’, ‘BEZIER’, ‘NURBS’]

use_bezier_u

Have this nurbs curve or surface behave like a Bézier spline along U (default False)

Type :

bool

use_bezier_v

Have this nurbs surface behave like a Bézier spline along V (default False)

Type :

bool

use_cyclic_u

Close this curve or surface into a loop along U (default False)

Type :

bool

use_cyclic_v

Close this surface into a loop along V (default False)

Type :

bool

use_endpoint_u

Have this nurbs curve or surface touch its endpoints along U (default False)

Type :

bool

use_endpoint_v

Have this nurbs surface touch its endpoints along V (default False)

Type :

bool

use_smooth

Smooth the normals on the surface or beveled curve (default False)

Type :

bool

calc_length ( * , resolution = 0 )

Compute the length of the spline

Parameters :

resolution ( int ) – Resolution, Spline resolution to be used, 0 defaults to the resolution_u (in [0, 1024], optional)

Returns :

Length, Length of the polygonaly approximated spline (in [0, inf])

Return type :

float

valid_message ( direction )

Return the message

Parameters :

direction ( int ) – Direction, The direction where 0-1 maps to U-V (in [0, 1])

Returns :

Return value, The message or an empty string when there is no error

Return type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Curve.splines CurveSplines.active | CurveSplines.new CurveSplines.remove |

## SpotLight(Light)

### SpotLight(Light)

base classes — bpy_struct, ID, Light

class bpy.types. SpotLight ( Light )

A cone-shaped directional Light

energy

Power this light would radiate across its whole area if the spot angle did not constrain it, in radiant power (W) (in [-inf, inf], default 10.0)

Type :

float

shadow_buffer_clip_start

Start of the shadow map clip; objects nearer than this cast no shadows (in [1e-06, inf], default 0.05)

Type :

float

shadow_filter_radius

Soften shadow aliasing through Percentage Closer Filtering (in [0, inf], default 1.0)

Type :

float

shadow_jitter_overblur

Run shadow tracing on every jittered sample to cut down under-sampling artifacts (in [0, 100], default 10.0)

Type :

float

shadow_maximum_resolution

Smallest size of a shadow-map pixel. Larger values save memory but lower shadow quality. (in [0, inf], default 0.001)

Type :

float

shadow_soft_size

Size of the light used when sampling ray shadows (Raytraced shadows) (in [0, inf], default 0.0)

Type :

float

show_cone

Draw a transparent cone in the 3D view so you can see which objects fall inside it (default False)

Type :

bool

spot_blend

How soft the edge of the spotlight is (in [0, 1], default 0.15)

Type :

float

spot_size

Angular width of the spotlight beam (in [0.0174533, 3.14159], default 0.785398)

Type :

float

use_absolute_resolution

Cap resolution at 1 unit out from the light origin rather than relative to the shadowed pixel (default False)

Type :

bool

use_shadow_jitter

Turn on jittered soft shadows for greater shadow precision (off in the viewport unless enabled in render settings). Costs a lot of performance. (default False)

Type :

bool

use_soft_falloff

Use falloff to soften sharp edges where the light geometry crosses other objects (default True)

Type :

bool

use_square

Project a square-shaped spot light (default False)

Type :

bool

inline_shader_nodes ( )

Return this light's inlined shader nodes. As a preprocessing step it strips nested groups, repeat zones, and similar constructs from the node tree.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data | ID.override_library ID.preview Light.type Light.use_temperature Light.color Light.temperature Light.temperature_color Light.specular_factor Light.diffuse_factor Light.transmission_factor Light.volume_factor Light.use_custom_distance Light.cutoff_distance Light.use_shadow Light.exposure Light.normalize Light.node_tree Light.use_nodes Light.animation_data Light.cycles |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values | ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Light.area Light.inline_shader_nodes Light.bl_rna_get_subclass Light.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)

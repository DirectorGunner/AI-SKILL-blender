# Vectorfont Id, View3Doverlay Bpy Struct, View3Dshading Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: VectorFont(ID); View3DOverlay(bpy_struct); View3DShading(bpy_struct).

## VectorFont(ID)

### VectorFont(ID) 

base classes — bpy_struct, ID

class bpy.types. VectorFont ( ID ) 

A vector typeface used by Text objects

filepath 

(default "", never None, blend relative // prefix supported)

Type :

str

packed_file 

(readonly)

Type :

PackedFile

pack ( ) 

Embed the font inside the current blend file

unpack ( * , method = '`USE_LOCAL`' ) 

Extract the font to the samples filename

Parameters :

method (Literal[Unpack Method Items]) – method, The unpacking strategy (optional)

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

| BlendData.fonts BlendDataFonts.load BlendDataFonts.remove NodeSocketFont.default_value NodeTreeInterfaceSocketFont.default_value | TextCurve.font TextCurve.font_bold TextCurve.font_bold_italic TextCurve.font_italic TextStrip.font |

## View3DOverlay(bpy_struct)

### View3DOverlay(bpy_struct) 

base class — bpy_struct

class bpy.types. View3DOverlay ( bpy_struct ) 

Controls for how overlays are drawn inside the 3D viewport

bone_wire_alpha 

The highest opacity bones reach while shown in wireframe display mode (in [0, inf], default 1.0)

Type :

float

display_handle 

Cap how curve handles appear while in Edit Mode (default 'SELECTED' )

Type :

Literal['NONE', 'SELECTED', 'ALL']

fade_inactive_alpha 

How pronounced the fade effect is (in [0, 1], default 0.4)

Type :

float

gpencil_fade_layer 

Opacity applied to fading every Grease Pencil layer other than the active one (in [0, 1], default 0.5)

Type :

float

gpencil_fade_objects 

Fade factor (in [0, 1], default 0.5)

Type :

float

gpencil_grid_color 

Canvas grid color (array of 3 items, in [0, 1], default (0.5, 0.5, 0.5))

Type :

mathutils.Color

gpencil_grid_offset 

Canvas grid offset (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

gpencil_grid_opacity 

Canvas grid opacity (in [0.1, 1], default 0.9)

Type :

float

gpencil_grid_scale 

Canvas grid scale (array of 2 items, in [0, inf], default (1.0, 1.0))

Type :

mathutils.Vector

gpencil_grid_subdivisions 

Canvas grid subdivisions (in [1, 100], default 4)

Type :

int

gpencil_vertex_paint_opacity 

Vertex Paint mix factor (in [0, 1], default 1.0)

Type :

float

grid_lines 

How many grid lines to draw in perspective view (in [0, 1024], default 16)

Type :

int

grid_scale 

Factor scaling the spacing between 3D View grid lines (in [0, inf], default 1.0)

Type :

float

grid_scale_unit 

Grid cell size after scaling by the scene's unit system settings (in [-inf, inf], default 0.0, readonly)

Type :

float

grid_subdivisions 

How many subdivisions sit between grid lines (in [1, 1024], default 10)

Type :

int

normals_constant_screen_size 

The on-screen size used for normals in the 3D view (in [0, 100000], default 7.0)

Type :

float

normals_length 

The drawn length used for normals in the 3D view (in [1e-05, 100000], default 0.1)

Type :

float

retopology_offset 

The offset that pushes the edit mesh in front of surrounding geometry (in [0, inf], default 0.01)

Type :

float

sculpt_curves_cage_opacity 

The opacity of the cage overlay while in curves sculpt mode (in [0, 1], default 0.0)

Type :

float

sculpt_mode_face_sets_opacity 

(in [0, 1], default 1.0)

Type :

float

sculpt_mode_mask_opacity 

(in [0, 1], default 0.75)

Type :

float

show_annotation 

Display this view's annotations (default True)

Type :

bool

show_axis_x 

Draw the X axis line (default True)

Type :

bool

show_axis_y 

Draw the Y axis line (default True)

Type :

bool

show_axis_z 

Draw the Z axis line (default False)

Type :

bool

show_bones 

Draw bones (turn off to leave only motion paths visible) (default True)

Type :

bool

show_camera_guides 

Draw the camera's composition guides (default True)

Type :

bool

show_camera_passepartout 

Draw the camera passepartout (default True)

Type :

bool

show_cursor 

Draw the 3D Cursor Overlay (default True)

Type :

bool

show_curve_normals 

Draw 3D curve normals while in Edit Mode (default False)

Type :

bool

show_edge_bevel_weight 

Draw the weights set up for the Bevel modifier (default True)

Type :

bool

show_edge_crease 

Draw the creases set up for the Subdivision Surface modifier (default True)

Type :

bool

show_edge_seams 

Draw the seams used for UV unwrapping (default True)

Type :

bool

show_edge_sharp 

Draw sharp edges, as used by the Edge Split modifier (default True)

Type :

bool

show_extra_edge_angle 

Draw the angle of the selected edge, using global values when the transform panel sets them (default False)

Type :

bool

show_extra_edge_length 

Draw the length of selected edges, using global values when the transform panel sets them (default False)

Type :

bool

show_extra_face_angle 

Draw the angles along the selected edges, using global values when the transform panel sets them (default False)

Type :

bool

show_extra_face_area 

Draw the area of the selected faces, using global values when the transform panel sets them (default False)

Type :

bool

show_extra_indices 

Draw the index numbers of the selected vertices, edges, and faces (default False)

Type :

bool

show_extras 

Extra object detail such as empty wires, cameras, and other visual guides (default True)

Type :

bool

show_face_center 

Draw the face center while face selection is on in solid shading modes (default False)

Type :

bool

show_face_normals 

Draw face normals as lines (default False)

Type :

bool

show_face_orientation 

Draw the Face Orientation Overlay (default False)

Type :

bool

show_faces 

Draw an overlay marking the face selection (default True)

Type :

bool

show_fade_inactive 

Fade out inactive geometry toward the viewport background color (default False)

Type :

bool

show_floor 

Draw the ground plane grid (default True)

Type :

bool

show_freestyle_edge_marks 

Draw Freestyle edge marks, as used by the Freestyle renderer (default True)

Type :

bool

show_freestyle_face_marks 

Draw Freestyle face marks, as used by the Freestyle renderer (default True)

Type :

bool

show_light_colors 

Show light colors (default False)

Type :

bool

show_look_dev 

Draw reference spheres with neutral shading that respond to lighting, helping with look development (default False)

Type :

bool

show_motion_paths 

Draw the Motion Paths Overlay (default True)

Type :

bool

show_object_origins 

Draw object center dots (default True)

Type :

bool

show_object_origins_all 

Draw the object origin center dot across every object, whether selected or not (default False)

Type :

bool

show_onion_skins 

Draw the Onion Skinning Overlay (default False)

Type :

bool

show_ortho_grid 

Draw the grid in orthographic side views (default True)

Type :

bool

show_outline_selected 

Draw an outline highlight surrounding the selected objects (default True)

Type :

bool

show_overlays 

Draw overlays such as gizmos and outlines (default True)

Type :

bool

show_paint_wire 

Use a wireframe display while in painting modes (default False)

Type :

bool

show_performance 

Draw viewport performance timings:

- Evaluation: Time to evaluate the dependency graph.

- Synchronization: Time to build the GPU buffers.

(default False)

Type :

bool

show_relationship_lines 

Draw dashed lines that mark parent or constraint relationships (default True)

Type :

bool

show_retopology 

Conceal the solid mesh and push the overlay toward the view. Inactive geometry occludes the selection unless X-Ray is on (default False)

Type :

bool

show_sculpt_curves_cage 

Draw the original curves that are presently being edited (default False)

Type :

bool

show_sculpt_face_sets 

(default True)

Type :

bool

show_sculpt_mask 

(default True)

Type :

bool

show_split_normals 

Draw vertex-per-face normals as lines (default False)

Type :

bool

show_stats 

Draw the scene statistics overlay text (default False)

Type :

bool

show_statvis 

Draw statistical information about the mesh (default False)

Type :

bool

show_text 

Draw the overlay text (default True)

Type :

bool

show_vertex_normals 

Draw vertex normals as lines (default False)

Type :

bool

show_viewer_attribute 

Draw the attribute overlay for the active viewer node (default True)

Type :

bool

show_viewer_text 

Draw attribute values as text inside the viewport (default False)

Type :

bool

show_weight 

Draw weights while in editmode (default False)

Type :

bool

show_wireframes 

Draw the wires of face edges (default False)

Type :

bool

show_wpaint_contours 

Draw contour lines that join points sharing the same interpolated weight (default False)

Type :

bool

show_xray_bone 

Draw the bone selection overlay (default False)

Type :

bool

texture_paint_mode_opacity 

The opacity of the texture paint mode stencil mask overlay (in [0, 1], default 1.0)

Type :

float

use_debug_freeze_view_culling 

Freeze view culling bounds (default False)

Type :

bool

use_gpencil_canvas_xray 

Draw the Canvas grid in front (default False)

Type :

bool

use_gpencil_edit_lines 

Draw Edit Lines while editing strokes (default True)

Type :

bool

use_gpencil_fade_gp_objects 

Fade Grease Pencil Objects, except the active one (default False)

Type :

bool

use_gpencil_fade_layers 

Switch fading on or off for every Grease Pencil layer other than the active one (default False)

Type :

bool

use_gpencil_fade_objects 

Fade every viewport object behind a full color layer to make things easier to see (default False)

Type :

bool

use_gpencil_grid 

Draw a grid over the Grease Pencil paper (default False)

Type :

bool

use_gpencil_multiedit_line_only 

Draw Edit Lines only while in multiframe (default False)

Type :

bool

use_gpencil_onion_skin 

Draw ghosts of the keyframes that come before and after the current frame (default False)

Type :

bool

use_gpencil_onion_skin_active_object 

Draw onion skins for the active object alone (default False)

Type :

bool

use_gpencil_show_directions 

Indicate stroke drawing direction with a larger green start dot and a smaller red end dot (default False)

Type :

bool

use_gpencil_show_material_name 

Draw the material name assigned to each stroke (default False)

Type :

bool

use_normals_constant_screen_size 

Hold the size of normals steady relative to the 3D view (default False)

Type :

bool

vertex_opacity 

Opacity for edit vertices (in [0, 1], default 1.0)

Type :

float

vertex_paint_mode_opacity 

The opacity of the texture paint mode stencil mask overlay (in [0, 1], default 1.0)

Type :

float

viewer_attribute_opacity 

The opacity of the attribute being visualized right now (in [0, 1], default 1.0)

Type :

float

weight_paint_mode_opacity 

The opacity of the weight paint mode overlay (in [0, 1], default 1.0)

Type :

float

wireframe_opacity 

The opacity of the drawn edges (1.0 for opaque) (in [0, 1], default 1.0)

Type :

float

wireframe_threshold 

Tune the angle threshold that governs which edges are drawn (1.0 for all) (in [0, 1], default 1.0)

Type :

float

xray_alpha_bone 

The opacity applied to bone selection (in [0, 1], default 0.5)

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

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| SpaceView3D.overlay | |

## View3DShading(bpy_struct)

### View3DShading(bpy_struct)

base class — bpy_struct

class bpy.types. View3DShading ( bpy_struct )

Controls how geometry is shaded inside the 3D viewport.

aov_name

Identifier of the Shader AOV that is currently active (default "", never None)

Type :

str

background_color

The RGB triple applied when a custom viewport background is chosen (array of 3 items, in [0, 1], default (0.05, 0.05, 0.05))

Type :

mathutils.Color

background_type

Chooses what fills the viewport background (default 'THEME' )

- THEME
Theme – Take the background tint straight from the active theme.

- WORLD
World – Derive the background from the scene's world.

- VIEWPORT
Custom – Apply a fixed color that affects only this viewport.

Type :

Literal['THEME', 'WORLD', 'VIEWPORT']

cavity_ridge_factor

Strength applied to the cavity ridges (in [0, 250], default 1.0)

Type :

float

cavity_type

Picks how cavity shading is computed (default 'SCREEN' )

- WORLD
World – Compute cavity in world space; handy for broad occlusion.

- SCREEN
Screen – Curvature-driven shading that brings out small surface detail.

- BOTH
Both – Combine the two cavity methods at once.

Type :

Literal['WORLD', 'SCREEN', 'BOTH']

cavity_valley_factor

Strength applied to the cavity valleys (in [0, 250], default 1.0)

Type :

float

color_type

Color Type (default 'MATERIAL' )

- MATERIAL
Material – Display the color of the material.

- OBJECT
Object – Display the per-object color.

- RANDOM
Random – Assign each object a random tint.

- VERTEX
Attribute – Display the active color attribute.

- TEXTURE
Texture – Pull the texture from the active image texture node, mapped through the active UV layer.

- SINGLE
Custom – Paint the whole scene with one chosen color.

Type :

Literal['MATERIAL', 'OBJECT', 'RANDOM', 'VERTEX', 'TEXTURE', 'SINGLE']

curvature_ridge_factor

Strength applied to the curvature ridges (in [0, 2], default 1.0)

Type :

float

curvature_valley_factor

Strength applied to the curvature valleys (in [0, 2], default 1.0)

Type :

float

cycles

(readonly)

Type :

CyclesView3DShadingSettings

light

Lighting Method for Solid/Texture Viewport Shading (default 'STUDIO' )

- STUDIO
Studio – Shade with studio lighting.

- MATCAP
MatCap – Shade using a matcap material and its lighting.

- FLAT
Flat – Shade with flat lighting only.

Type :

Literal['STUDIO', 'MATCAP', 'FLAT']

object_outline_color

The RGB triple used to draw object outlines (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

render_pass

Which render pass is shown in the viewport (default 'COMBINED' )

Type :

Literal['COMBINED', 'EMISSION', 'ENVIRONMENT', 'AO', 'SHADOW', 'TRANSPARENT', '`DIFFUSE_LIGHT`', '`DIFFUSE_COLOR`', '`SPECULAR_LIGHT`', '`SPECULAR_COLOR`', '`VOLUME_LIGHT`', 'POSITION', 'NORMAL', 'MIST', 'CryptoObject', 'CryptoAsset', 'CryptoMaterial', 'AOV']

selected_studio_light

Selected StudioLight (readonly)

Type :

StudioLight

shadow_intensity

How dark cast shadows appear (in [0, 1], default 0.5)

Type :

float

show_backface_culling

Cull back faces so the rear side of geometry stays hidden (default False)

Type :

bool

show_cavity

Show Cavity (default False)

Type :

bool

show_object_outline

Show Object Outline (default False)

Type :

bool

show_shadows

Show Shadow (default False)

Type :

bool

show_specular_highlight

Draw specular highlights (default True)

Type :

bool

show_xray

Make the entire scene see-through (default False)

Type :

bool

show_xray_wireframe

Make the entire scene see-through (default True)

Type :

bool

single_color

The RGB triple used by single-color mode (array of 3 items, in [0, 1], default (0.8, 0.8, 0.8))

Type :

mathutils.Color

studio_light

Studio lighting setup (default 'DEFAULT' )

Type :

Literal['DEFAULT']

studiolight_background_alpha

How visible the studiolight is in the background (in [0, 1], default 0.0)

Type :

float

studiolight_background_blur

How much the background studiolight is blurred (in [0, 1], default 0.5)

Type :

float

studiolight_intensity

How bright the studiolight is (in [0, inf], default 1.0)

Type :

float

studiolight_rotate_z

How far the studiolight is spun about the Z axis (in [-3.14159, 3.14159], default 0.0)

Type :

float

type

How objects get displayed or shaded in the 3D View (default 'SOLID' )

Type :

Literal[Shading Type Items]

use_compositor

Controls when the compositor result is previewed in the viewport (default 'DISABLED' )

- DISABLED
Disabled – Turn the compositor off.

- CAMERA
Camera – Run the compositor only while in camera view.

- ALWAYS
Always – Keep the compositor on for every view.

Type :

Literal['DISABLED', 'CAMERA', 'ALWAYS']

use_dof

Apply depth of field in the viewport, taken from the active camera's settings (default False)

Type :

bool

use_scene_lights

Include the scene's lights and light probes (default False)

Type :

bool

use_scene_lights_render

Include the scene's lights and light probes (default True)

Type :

bool

use_scene_world

Light using the scene world (default False)

Type :

bool

use_scene_world_render

Light using the scene world (default True)

Type :

bool

use_studiolight_view_rotation

Lock the HDR rotation so it stays put instead of tracking the camera (default True)

Type :

bool

use_world_space_lighting

Lock the lighting so it stays put instead of tracking the camera (default False)

Type :

bool

wireframe_color_type

Wire Color Type (default 'THEME' )

- THEME
Theme – Draw scene wireframes in the theme's wire color.

- OBJECT
Object – Draw wireframes using the object's color.

- RANDOM
Random – Draw wireframes with a random object color.

Type :

Literal['THEME', 'OBJECT', 'RANDOM']

xray_alpha

Opacity level to apply (in [0, 1], default 0.5)

Type :

float

xray_alpha_wireframe

Opacity level to apply (in [0, 1], default 0.5)

Type :

float

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Low-level entry point to runtime-defined RNA storage, meant purely for tests and debugging. Steer clear of it in normal scripts, and never assume what it returns is writable.

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The root container for system properties, or None when none are stored yet on this data and creation was not asked for

Return type :

PropertyGroup

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SceneDisplay.shading SpaceView3D.shading | XrSessionSettings.shading |

## See also

- [Bpy Struct](bpy-struct.md)

# Preferencesinput Bpy Struct, Raytraceeevee Bpy Struct, Regionview3D Bpy Struct, Remeshmodifier Modifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: PreferencesInput(bpy_struct); RaytraceEEVEE(bpy_struct); RegionView3D(bpy_struct); RemeshModifier(Modifier); RenderPass(bpy_struct); RenderPasses(bpy_prop_collection); RenderView(bpy_struct).

## PreferencesInput(bpy_struct)

### PreferencesInput(bpy_struct)

base class — bpy_struct

class bpy.types. PreferencesInput ( bpy_struct )

Options for input devices

drag_threshold

Pixels of motion required before a drag event fires for keyboard and other non mouse/tablet input (otherwise the motion reads as a click) (in [1, 255], default 30)

Type :

int

drag_threshold_mouse

Pixels of motion required before a drag event fires for mouse/trackpad input (otherwise the motion reads as a click) (in [1, 255], default 3)

Type :

int

drag_threshold_tablet

Pixels of motion required before a drag event fires for tablet input (otherwise the motion reads as a click) (in [1, 255], default 10)

Type :

int

invert_mouse_zoom

Reverse the mouse-movement axis used for zooming (default False)

Type :

bool

invert_zoom_wheel

Reverse the Mouse Wheel zoom direction (default False)

Type :

bool

mouse_double_click_time

How long (in ms) a double click may take (in [1, 1000], default 350)

Type :

int

mouse_emulate_3_button_modifier

The modifier held down to stand in for the middle mouse button (default 'ALT' )

Type :

Literal[‘ALT’, ‘OSKEY’]

move_threshold

Pixels the cursor must travel before it counts as moved (used when cycling selected items through repeated clicks) (in [0, 255], default 2)

Type :

int

navigation_mode

The technique used for viewport navigation (default 'WALK' )

Type :

Literal[Navigation Mode Items]

ndof_deadzone

How much initial motion away from the device's rest position is ignored (in [0, 1], default 0.0)

Type :

float

ndof_fly_helicopter

Device up/down maps straight onto the Z position of the 3D viewport (default False)

Type :

bool

ndof_fly_speed_auto

Tune fly navigation speed automatically from how far away objects near the viewport center are, easing travel through busy scenes. The speed is recomputed whenever movement begins. (default False)

Type :

bool

ndof_lock_camera_pan_zoom

Pan/zoom inside the camera view rather than dropping out of it while orbiting (default True)

Type :

bool

ndof_lock_horizon

Lock Horizon holds the horizon level at its current orientation (default True)

Type :

bool

ndof_navigation_mode

3D Mouse Navigation Mode (default 'OBJECT' )

- OBJECT
Object – Feels like reaching into the screen to grip the model directly. Nudge the 3D Mouse cap leftward and the model slides left; nudge it right and it slides right.

- FLY
Fly – Treats the 3D Mouse like a camera. Press into the scene to drive the camera deeper in, as though piloting through it. Pan & zoom are also inverted for 2D views.

- DRONE
Drone – Behaves like Fly Mode, except tilting the cap forward while looking down leaves the camera's altitude untouched..

Type :

Literal[‘OBJECT’, ‘FLY’, ‘DRONE’]

ndof_orbit_center_auto

Places the orbit center on the fly. With the whole model framed, its overall volume center becomes the pivot; as you close in, the pivot shifts to an object near the middle of your view. (default True)

Type :

bool

ndof_orbit_center_selected

Limits the orbit center to just the objects that are currently selected. (default False)

Type :

bool

ndof_panx_invert_axis

(default False)

Type :

bool

ndof_pany_invert_axis

(default False)

Type :

bool

ndof_panz_invert_axis

(default False)

Type :

bool

ndof_rotation_sensitivity

How responsive the 3D Mouse is when rotating, overall (in [0.01, 40], default 4.0)

Type :

float

ndof_rotx_invert_axis

(default False)

Type :

bool

ndof_roty_invert_axis

(default False)

Type :

bool

ndof_rotz_invert_axis

(default False)

Type :

bool

ndof_show_guide_orbit_axis

Draw the center and axis while rotating (default False)

Type :

bool

ndof_show_guide_orbit_center

Draw the orbit center while rotating (default True)

Type :

bool

ndof_translation_sensitivity

How responsive the 3D Mouse is when translating, overall (in [0.01, 40], default 4.0)

Type :

float

ndof_zoom_direction

Which axis of the 3D Mouse cap drives the zoom (default '`NDOF_ZOOM_FORWARD`' )

- `NDOF_ZOOM_FORWARD`
Forward/Backward – Pull the 3D Mouse cap up or press it down to zoom.

- `NDOF_ZOOM_UP`
Up/Down – Pull the 3D Mouse cap up or press it down to zoom.

Type :

Literal[‘`NDOF_ZOOM_FORWARD`’, ‘`NDOF_ZOOM_UP`’]

pressure_softness

Shape the onset of the low-pressure response via a gamma curve (in [-inf, inf], default 0.0)

Type :

float

pressure_threshold_max

The raw input pressure that Blender reads as 100% (in [0, 1], default 1.0)

Type :

float

show_tablet_debug_values

Display pressure values whenever a paint operator runs (default False)

Type :

bool

tablet_api

Pick which tablet API drives pressure sensitivity (may need a Blender restart to apply) (default 'AUTOMATIC' )

- AUTOMATIC
Automatic – Pick Wintab or Windows Ink based on the device on its own.

- `WINDOWS_INK`
Windows Ink – Go through the native Windows Ink API, suited to current tablet and pen devices. Needs Windows 8 or later..

- WINTAB
Wintab – Go through the Wintab driver, for older tablets and Windows releases.

Type :

Literal[‘AUTOMATIC’, ‘`WINDOWS_INK`’, ‘WINTAB’]

touchpad_scroll_direction

Scroll direction (Wayland only) (default 'TRADITIONAL' )

- TRADITIONAL
Traditional – Traditional scroll direction.

- NATURAL
Natural – Natural scroll direction.

Type :

Literal[‘TRADITIONAL’, ‘NATURAL’]

use_auto_perspective

Flip between orthographic and perspective on its own when switching to top/front/side views (default True)

Type :

bool

use_drag_immediately

Confirm a mouse-drag move when the button is released (default True)

Type :

bool

use_emulate_numpad

Let the main 1 to 0 keys behave like the numpad ones (handy on laptops) (default False)

Type :

bool

use_mouse_continuous

Wrap the mouse around the view edges so movement isn't capped by the screen size (relied on by transform, UI-control dragging, and the like) (default True)

Type :

bool

use_mouse_depth_navigate

Use the depth beneath the mouse to refine view pan/rotate/zoom (default False)

Type :

bool

use_mouse_emulate_3_button

Stand in for the Middle Mouse using Alt+Left Mouse (default False)

Type :

bool

use_multitouch_gestures

Navigate with multi-touch touchpad gestures instead of emulating the scroll wheel (default True)

Type :

bool

use_numeric_input_advanced

While typing numbers during a transform, start in advanced mode so full math expressions evaluate (default False)

Type :

bool

use_rotate_around_active

Orbit around the selection (or, in Paint modes, the last stroke center) as the pivot (default False)

Type :

bool

use_zoom_to_mouse

Zoom toward the mouse pointer in the 3D view rather than the 2D window center (default False)

Type :

bool

view_rotate_method

The orbit technique used in the viewport (default 'TURNTABLE' )

- TURNTABLE
Turntable – Holds the Z-axis upright as you orbit.

- TRACKBALL
Trackball – Lets you tumble the view to any angle.

Type :

Literal[‘TURNTABLE’, ‘TRACKBALL’]

view_rotate_sensitivity_trackball

Scale the sensitivity of trackball orbiting (in [0.1, 10], default 1.0)

Type :

float

view_rotate_sensitivity_turntable

Rotation per pixel that sets how quickly the viewport orbits (in [1.74533e-05, 0.261799], default 0.00698132)

Type :

float

view_zoom_axis

Which axis of mouse motion zooms the view (default 'VERTICAL' )

- VERTICAL
Vertical – Drive zoom from vertical mouse motion.

- HORIZONTAL
Horizontal – Drive zoom from horizontal mouse motion.

Type :

Literal[‘VERTICAL’, ‘HORIZONTAL’]

view_zoom_method

The style used for viewport scaling (default 'DOLLY' )

- CONTINUE
Continue – Zoom continuously, with direction and speed set by how far the mouse has traveled along the chosen Zoom Axis..

- DOLLY
Dolly – Zoom by moving the mouse along the chosen Zoom Axis.

- SCALE
Scale – Zoom as though scaling the view, with mouse motion measured from center.

Type :

Literal[‘CONTINUE’, ‘DOLLY’, ‘SCALE’]

walk_navigation

Options for walk navigation mode (readonly, never None)

Type :

WalkNavigation

xr_navigation

Options for navigation in XR (readonly, never None)

Type :

XrNavigation

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

| Preferences.inputs | |

## RaytraceEEVEE(bpy_struct)

### RaytraceEEVEE(bpy_struct) 

base class — bpy_struct

class bpy.types. RaytraceEEVEE ( bpy_struct ) 

Settings controlling the quality of the raytracing pipeline

denoise_bilateral 

Soften the resolved radiance with a bilateral filter (default True)

Type :

bool

denoise_spatial 

Borrow rays from adjacent pixels (default True)

Type :

bool

denoise_temporal 

Build up samples by reprojecting the previous tracing results (default True)

Type :

bool

resolution_scale 

Sets how many rays are cast per pixel. Greater resolution consumes more memory. (default '2' )

- 1
1:1 – Full resolution.

- 2
1:2 – Render this effect at 50% render resolution.

- 4
1:4 – Render this effect at 25% render resolution.

- 8
1:8 – Render this effect at 12.5% render resolution.

- 16
1:16 – Render this effect at 6.25% render resolution.

Type :

Literal[‘1’, ‘2’, ‘4’, ‘8’, ‘16’]

screen_trace_quality 

How precise the screen-space ray-tracing is (in [0, 1], default 0.25)

Type :

float

screen_trace_thickness 

Assumed surface thickness used to find intersections during screen-tracing (in [1e-06, inf], default 0.2)

Type :

float

trace_max_roughness 

Highest roughness that still routes through the tracing pipeline. Rougher surfaces fall back to the fast GI approximation, and a value of 1 turns that approximation off. (in [0, 1], default 0.5)

Type :

float

use_denoise 

Apply noise-reduction methods to raytraced effects (default True)

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

| SceneEEVEE.ray_tracing_options | |

## RegionView3D(bpy_struct)

### RegionView3D(bpy_struct) 

base class — bpy_struct

class bpy.types. RegionView3D ( bpy_struct ) 

Data for a 3D View region

clip_planes 

(multi-dimensional array of 6 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

bpy_prop_array[float]

is_orthographic_side_view 

Reports whether the view lines up with an axis (this does not test for orthographic projection — use “is_perspective” for that). Assigning it rotates the view toward the nearest axis (default False)

Type :

bool

is_perspective 

(default False)

Type :

bool

lock_rotation 

Hold side-view rotation fixed to Top/Front/Right (default False)

Type :

bool

perspective_matrix 

The active perspective matrix ( window_matrix * view_matrix ) (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

show_sync_view 

Keep the view position synchronized across side views (default False)

Type :

bool

use_box_clip 

Clip the view's contents to what other side views can see (default False)

Type :

bool

use_clip_planes 

(default False)

Type :

bool

view_camera_offset 

How far the view is shifted in camera view (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

view_camera_zoom 

The zoom amount in camera view (in [-30, 600], default 0.0)

Type :

float

view_distance 

How far the viewpoint sits from the view location (in [0, inf], default 0.0)

Type :

float

view_location 

The pivot point of the view (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

view_matrix 

The active view matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

view_perspective 

View Perspective (default 'ORTHO' )

Type :

Literal[‘PERSP’, ‘ORTHO’, ‘CAMERA’]

view_rotation 

Rotation expressed as quaternions (keep them normalized) (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

window_matrix 

The active window matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

update ( ) 

Recalculate the view matrices

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

| Context.region_data SpaceView3D.region_3d | SpaceView3D.region_quadviews |

## RemeshModifier(Modifier)

### RemeshModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. RemeshModifier ( Modifier ) 

Build a fresh surface with even topology that conforms to the input mesh's shape

adaptivity 

Lowers the final face count by simplifying areas that need little detail, producing triangles. Any value above 0 turns off Fix Poles. (in [-inf, inf], default 0.0)

Type :

float

mode 

(default 'VOXEL' )

- BLOCKS
Blocks – Output a blocky surface with no smoothing.

- SMOOTH
Smooth – Output a smooth surface with no sharp-features detection.

- SHARP
Sharp – Output a surface that reproduces sharp edges and corners from the input mesh.

- VOXEL
Voxel – Output a mesh corresponding to the volume of the original mesh.

Type :

Literal[‘BLOCKS’, ‘SMOOTH’, ‘SHARP’, ‘VOXEL’]

octree_depth 

The octree resolution; larger values yield finer detail (in [1, 24], default 4)

Type :

int

scale 

How the model's largest dimension compares to the grid size (in [0, 0.99], default 0.9)

Type :

float

sharpness 

How much outliers are tolerated; smaller values cut noise while larger ones track input edges more closely (in [-inf, inf], default 1.0)

Type :

float

threshold 

When stripping out disconnected pieces, the smallest component size to keep, given as a fraction of the polygon count of the largest component (in [0, 1], default 1.0)

Type :

float

use_remove_disconnected 

(default True)

Type :

bool

use_smooth_shade 

Produce smooth-shaded faces in place of flat-shaded ones (default False)

Type :

bool

voxel_size 

The voxel size, in object space, used to evaluate the volume. Smaller values keep finer detail. (in [0, inf], default 0.1)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## RenderPass(bpy_struct)

### RenderPass(bpy_struct) 

base class — bpy_struct

class bpy.types. RenderPass ( bpy_struct ) 

channel_id 

(default “”, readonly, never None)

Type :

str

channels 

(in [-inf, inf], default 0, readonly)

Type :

int

fullname 

(default “”, readonly, never None)

Type :

str

name 

(default “”, readonly, never None)

Type :

str

rect 

(in [-inf, inf], default 0.0)

Type :

float

view_id 

(in [-inf, inf], default 0, readonly)

Type :

int

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

| RenderEngine.pass_by_index_get RenderLayer.passes | RenderPasses.find_by_name |

## RenderPasses(bpy_prop_collection)

### RenderPasses(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. RenderPasses ( bpy_prop_collection ) 

A collection holding render passes

find_by_name ( name , view ) 

Look up the render pass that matches the supplied name together with the view

Parameters :

- name ( str ) – Pass, (never None)

- view ( str ) – View, Render view to get pass from (never None)

Returns :

The matching render pass

Return type :

RenderPass

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

| RenderLayer.passes | |

## RenderView(bpy_struct)

### RenderView(bpy_struct)

base class — bpy_struct

class bpy.types. RenderView ( bpy_struct )

name

(default “”, readonly, never None)

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| RenderResult.views | |

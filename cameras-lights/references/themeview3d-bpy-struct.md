# Themeview3D Bpy Struct, Timelinemarker Bpy Struct, Triangulatemodifier Modifier, Usersolidlight Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ThemeView3D(bpy_struct); TimelineMarker(bpy_struct); TriangulateModifier(Modifier); UserSolidLight(bpy_struct); UVProjectModifier(Modifier); UVWarpModifier(Modifier); VertexWeightEditModifier(Modifier).

## ThemeView3D(bpy_struct)

### ThemeView3D(bpy_struct) 

base class — bpy_struct

class bpy.types. ThemeView3D ( bpy_struct ) 

Color theming for the 3D viewport.

after_current_frame 

Tint used for elements following the current frame, such as onion skinning and motion paths (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

before_current_frame 

Tint used for elements preceding the current frame, such as onion skinning and motion paths (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

bevel 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

bone_locked_weight 

Tint marking bones tied to a locked weight group while painting (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

bone_pose 

Outline tint for pose bones that are selected (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

bone_pose_active 

Outline tint for the active pose bone (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

bone_solid 

Base tint for the solid bone shapes (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

bundle_solid 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

camera 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

camera_passepartout 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

camera_path 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

clipping_border_3d 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

crease 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

edge_mode_select 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

edge_select 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

edge_width 

(in [1, 32], default 0)

Type :

int

editmesh_active 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

empty 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

extra_edge_angle 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

extra_edge_len 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

extra_face_angle 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

extra_face_area 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

face 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

face_back 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

face_front 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

face_mode_select 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

face_retopology 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

face_select 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

facedot_size 

(in [1, 10], default 0)

Type :

int

freestyle 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

gp_vertex 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gp_vertex_select 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

gp_vertex_size 

(in [1, 10], default 0)

Type :

int

gp_wire_edit 

Wireframe tint for Grease Pencil while in edit mode (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

grid 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

grid_major 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

light 

(array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

normal 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

nurb_sel_uline 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

nurb_sel_vline 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

nurb_uline 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

nurb_vline 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

object_active 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

object_origin_size 

Pixel diameter used when drawing object and light origins (in [4, 10], default 0)

Type :

int

object_selected 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

outline_width 

(in [1, 5], default 0)

Type :

int

seam 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

sharp 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

skin_root 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

space 

Settings for space (readonly, never None)

Type :

ThemeSpaceGradient

speaker 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

split_normal 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

text_grease_pencil 

Tint marking Grease Pencil keyframes (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

transform 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_normal 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_select 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

vertex_size 

(in [1, 32], default 0)

Type :

int

vertex_unreferenced 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

view_overlay 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

wire 

(array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

wire_edit 

Wireframe tint shown in edit mode while edge selection is on (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

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

| Theme.view_3d | |

## TimelineMarker(bpy_struct)

### TimelineMarker(bpy_struct) 

base class — bpy_struct

class bpy.types. TimelineMarker ( bpy_struct ) 

A marker that flags a point of interest on the timeline.

camera 

Camera made active when this frame is reached

Type :

Object

frame 

Frame where the marker sits on the timeline (in [-inf, inf], default 0)

Type :

int

name 

(default “”, never None)

Type :

str

select 

Whether the marker is currently selected (default False)

Type :

bool

bl_system_properties_get ( * , do_create = False ) 

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

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

| Action.pose_markers ActionPoseMarkers.active ActionPoseMarkers.new ActionPoseMarkers.remove | Scene.timeline_markers TimelineMarkers.new TimelineMarkers.remove |

## TriangulateModifier(Modifier)

### TriangulateModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. TriangulateModifier ( Modifier ) 

Triangulate Mesh

keep_custom_normals 

Try to preserve custom normals.
Warning: Depending on chosen triangulation method, shading may not be fully preserved, “Fixed” method usually gives the best result here

(default False)

Type :

bool

min_vertices 

Only triangulate polygons whose vertex count is at least this value (in [4, inf], default 4)

Type :

int

ngon_method 

How n-gons are split into triangles (default 'BEAUTY' )

Type :

Literal[Modifier Triangulate Ngon Method Items]

quad_method 

How quads are split into triangles (default '`SHORTEST_DIAGONAL`' )

Type :

Literal[Modifier Triangulate Quad Method Items]

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

## UserSolidLight(bpy_struct)

### UserSolidLight(bpy_struct) 

base class — bpy_struct

class bpy.types. UserSolidLight ( bpy_struct ) 

A light driving Studio lighting while solid shading is active

diffuse_color 

The color applied to this light's diffuse highlight (array of 3 items, in [0, inf], default (0.8, 0.8, 0.8))

Type :

mathutils.Color

direction 

The way the light points (array of 3 items, in [-inf, inf], default (0.0, 0.0, 1.0))

Type :

mathutils.Vector

smooth 

Soften the contribution coming from this light (in [0, 1], default 0.5)

Type :

float

specular_color 

The color applied to this light's specular highlight (array of 3 items, in [0, inf], default (0.8, 0.8, 0.8))

Type :

mathutils.Color

use 

Switch this light on while solid shading is active (default True)

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

| PreferencesSystem.solid_lights | StudioLight.solid_lights |

## UVProjectModifier(Modifier)

### UVProjectModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. UVProjectModifier ( Modifier ) 

A modifier that derives UVs from one or more projectors

aspect_x 

Aspect ratio across the horizontal (applies only to camera projectors) (in [1, inf], default 1.0)

Type :

float

aspect_y 

Aspect ratio across the vertical (applies only to camera projectors) (in [1, inf], default 1.0)

Type :

float

projector_count 

How many projectors to apply (in [1, 10], default 1)

Type :

int

projectors 

(default None, readonly)

Type :

bpy_prop_collection[UVProjector]

scale_x 

Scaling across the horizontal (applies only to camera projectors) (in [0, inf], default 1.0)

Type :

float

scale_y 

Scaling across the vertical (applies only to camera projectors) (in [0, inf], default 1.0)

Type :

float

uv_layer 

UV map name (default "", never None)

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

## UVWarpModifier(Modifier)

### UVWarpModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. UVWarpModifier ( Modifier ) 

Offset UV coordinates by a target position

axis_u 

The pole axis used for rotation (default 'X' )

Type :

Literal[Axis Xyz Items]

axis_v 

The pole axis used for rotation (default 'Y' )

Type :

Literal[Axis Xyz Items]

bone_from 

The bone that sets the offset (default "", never None)

Type :

str

bone_to 

The bone that sets the offset (default "", never None)

Type :

str

center 

The pivot used for rotate/scale (array of 2 items, in [-inf, inf], default (0.5, 0.5))

Type :

bpy_prop_array[float]

invert_vertex_group 

Flip the vertex group's influence (default False)

Type :

bool

object_from 

The object that sets the offset

Type :

Object

object_to 

The object that sets the offset

Type :

Object

offset 

Two-dimensional offset applied by the warp (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

rotation 

Two-dimensional rotation applied by the warp (in [-inf, inf], default 0.0)

Type :

float

scale 

Two-dimensional scale applied by the warp (array of 2 items, in [-inf, inf], default (1.0, 1.0))

Type :

bpy_prop_array[float]

uv_layer 

UV map name (default "", never None)

Type :

str

vertex_group 

Vertex group name (default "", never None)

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

## VertexWeightEditModifier(Modifier)

### VertexWeightEditModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. VertexWeightEditModifier ( Modifier ) 

Adjust the weights carried by vertices in a group

add_threshold 

The inclusive lower limit a vertex's weight must reach to be added to the vgroup (in [-1000, 1000], default 0.01)

Type :

float

default_weight 

The weight assumed for a vertex that is absent from the vgroup (in [0, 1], default 0.0)

Type :

float

falloff_type 

The mapping from old weights to their new values (default 'LINEAR' )

- LINEAR
Linear – Null action.

- CURVE
Custom Curve.

- SHARP
Sharp.

- SMOOTH
Smooth.

- ROOT
Root.

- `ICON_SPHERECURVE`
Sphere.

- RANDOM
Random.

- STEP
Median Step – Map all values below 0.5 to 0.0, and all others to 1.0.

Type :

Literal['LINEAR', 'CURVE', 'SHARP', 'SMOOTH', 'ROOT', '`ICON_SPHERECURVE`', 'RANDOM', 'STEP']

invert_falloff 

Flip the falloff weight that results (default False)

Type :

bool

invert_mask_vertex_group 

Flip the influence of the vertex group mask (default False)

Type :

bool

map_curve 

Custom mapping curve (readonly)

Type :

CurveMapping

mask_constant 

How strongly the current changes act on the vgroup overall (in [-inf, inf], default 1.0)

Type :

float

mask_tex_map_bone 

The bone supplying texture coordinates (default "", never None)

Type :

str

mask_tex_map_object 

The object supplying texture coordinates

Type :

Object

mask_tex_mapping 

The texture coordinates to drive the mapping (default 'LOCAL' )

- LOCAL
Local – Use local generated coordinates.

- GLOBAL
Global – Use global coordinates.

- OBJECT
Object – Use local generated coordinates of another object.

- UV
UV – Use coordinates from a UV layer.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT', 'UV']

mask_tex_use_channel 

The texture channel used for masking (default 'INT' )

Type :

Literal['INT', 'RED', 'GREEN', 'BLUE', 'HUE', 'SAT', 'VAL', 'ALPHA']

mask_tex_uv_layer 

UV map name (default "", never None)

Type :

str

mask_texture 

Masking texture

Type :

Texture

mask_vertex_group 

Masking vertex group name (default "", never None)

Type :

str

normalize 

Renormalize the resulting weights (otherwise they merely get clamped into the 0.0 to 1.0 range) (default False)

Type :

bool

remove_threshold 

The inclusive upper limit a vertex's weight must stay under to be removed from the vgroup (in [-1000, 1000], default 0.01)

Type :

float

use_add 

Add to the vgroup any vertex whose weight exceeds the threshold (default False)

Type :

bool

use_remove 

Remove from the vgroup any vertex whose weight falls under the threshold (default False)

Type :

bool

vertex_group 

Vertex group name (default "", never None)

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

# Curve Id, Curvemapping Bpy Struct, Curves Id

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curve(ID); CurveMapping(bpy_struct); Curves(ID).

## Curve(ID)

### Curve(ID)

base classes — bpy_struct, ID

subclasses —
SurfaceCurve, TextCurve

class bpy.types. Curve ( ID )

A data-block that holds curves, splines, and NURBS.

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

bevel_depth

How wide the bevel geometry reaches, before any extrusion is added (in [-inf, inf], default 0.0)

Type :

float

bevel_factor_end

Set the point along the spline where the curve geometry stops (0 at the start, 1 at the end) (in [0, 1], default 1.0)

Type :

float

bevel_factor_mapping_end

Pick how the end factor for the geometry is projected onto a spline (default 'RESOLUTION' )

- RESOLUTION
Resolution – Tie the geometry factor to a spline's subdivision count (its U resolution).

- SEGMENTS
Segments – Tie the geometry factor both to a segment's length and to how many subdivisions that segment has.

- SPLINE
Spline – Tie the geometry factor to the overall length of a spline.

Type :

Literal['RESOLUTION', 'SEGMENTS', 'SPLINE']

bevel_factor_mapping_start

Pick how the start factor for the geometry is projected onto a spline (default 'RESOLUTION' )

- RESOLUTION
Resolution – Tie the geometry factor to a spline's subdivision count (its U resolution).

- SEGMENTS
Segments – Tie the geometry factor both to a segment's length and to how many subdivisions that segment has.

- SPLINE
Spline – Tie the geometry factor to the overall length of a spline.

Type :

Literal['RESOLUTION', 'SEGMENTS', 'SPLINE']

bevel_factor_start

Set the point along the spline where the curve geometry begins (0 at the start, 1 at the end) (in [0, 1], default 0.0)

Type :

float

bevel_mode

Pick the method used to build the curve's bevel geometry (default 'ROUND' )

- ROUND
Round – Shape the bevel cross-section as a circle.

- OBJECT
Object – Drive the bevel cross-section from a chosen object.

- PROFILE
Profile – Apply a custom profile across each quarter of the bevel geometry.

Type :

Literal['ROUND', 'OBJECT', 'PROFILE']

bevel_object

The name of the Curve object that defines the bevel shape

Type :

Object

bevel_profile

The path for the curve's custom profile (readonly)

Type :

CurveProfile

bevel_resolution

How many segments make up each quarter-circle of the bevel (in [0, 32], default 4)

Type :

int

cycles

Cycles mesh settings (readonly)

Type :

CyclesMeshSettings

dimensions

Switch between a 2D and a 3D curve (default '2D' )

- 2D
2D – Hold the curve's Z axis fixed.

- 3D
3D – Free up Z-axis editing for the curve, which also unlocks tilt and per-point radius.

Type :

Literal['2D', '3D']

eval_time

Where, parametrically, an Object 'following' the curve should sit along its length (the value is read by dividing by the 'Path Length') (in [-inf, inf], default 0.0)

Type :

float

extrude

How far depth is added along the curve in the local Z direction, at right angles to its normals (in [0, inf], default 0.0)

Type :

float

fill_mode

Mode of filling curve (default 'FULL' )

Type :

Literal['FULL', 'BACK', 'FRONT', 'HALF']

fill_rule

Fill rule for Delaunay fill solver (default '`EVEN_ODD`' )

- `EVEN_ODD`
Even-Odd – Flip between inside and outside according to how many crossings are counted.

- NONZERO
Non-Zero – Where overlapping curves wind the same way, treat the result as a single union.

Type :

Literal['`EVEN_ODD`', 'NONZERO']

fill_solver

Triangulation solver for filling 2D curves (default '`SWEEP_LINE`' )

- `SWEEP_LINE`
Sweep Line – Quick, though it can't cope with self-intersection.

- CDT
Delaunay – Constrained Delaunay Triangulation (CDT), sturdy and able to handle self-intersections.

Type :

Literal['`SWEEP_LINE`', 'CDT']

is_editmode

True when used in editmode (default False, readonly)

Type :

bool

materials

(default None, readonly)

Type :

IDMaterials[Material]

offset

How far to shift the curve sideways along its normals (in [-inf, inf], default 0.0)

Type :

float

path_duration

How many frames it takes to walk the whole path, which caps the 'Evaluation Time' setting (in [1, 1048574], default 100)

Type :

int

render_resolution_u

U-direction surface resolution applied at render time (a value of zero falls back to the preview resolution) (in [0, 1024], default 0)

Type :

int

render_resolution_v

V-direction surface resolution applied at render time (a value of zero falls back to the preview resolution) (in [0, 1024], default 0)

Type :

int

resolution_u

How many points are computed along U between each pair of control points (in [1, 1024], default 12)

Type :

int

resolution_v

How many points are computed along V between each pair of control points (in [1, 1024], default 12)

Type :

int

shape_keys

(readonly)

Type :

Key

splines

Collection of splines in this curve data object (default None, readonly)

Type :

CurveSplines[Spline]

taper_object

Curve object name that defines the taper (width)

Type :

Object

taper_radius_mode

Pick how the spline point's effective radius is worked out once a taper object is in play (default 'OVERRIDE' )

- OVERRIDE
Override – Swap the spline point's radius out for the taper radius.

- MULTIPLY
Multiply – Scale the spline point's radius by the taper radius.

- ADD
Add – Sum the bevel point's radius together with the taper radius.

Type :

Literal['OVERRIDE', 'MULTIPLY', 'ADD']

texspace_location

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

texspace_size

(array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

twist_mode

Which tilt-calculation method 3D Curves use (default 'MINIMUM' )

- `Z_UP`
Z-Up – Derive each point's twist from the Z-Up axis.

- MINIMUM
Minimum – Keep the twist as small as possible across the whole curve.

- TANGENT
Tangent – Derive the twist from the tangent.

Type :

Literal['`Z_UP`', 'MINIMUM', 'TANGENT']

twist_smooth

Smoothing iteration for tangents (in [-inf, inf], default 0.0)

Type :

float

use_auto_texspace

Recompute the active object's texture space on its own as the object is transformed (default True)

Type :

bool

use_deform_bounds

A curve-deform setting: clamp the deformation against the mesh bounds (default False)

Type :

bool

use_fill_caps

Fill caps for beveled curves (default False)

Type :

bool

use_map_taper

Project the taper object's effect onto the beveled portion of the curve (default False)

Type :

bool

use_path

Let the curve act as a path that drives translation (default False)

Type :

bool

use_path_clamp

Keep path children inside the curve so they don't run off either end (default False)

Type :

bool

use_path_follow

Have path children turn to follow the path's direction (default False)

Type :

bool

use_radius

A paths and curve-deform setting: carry the curve radius onto followers and deformed objects (default True)

Type :

bool

use_stretch

A curve-deform setting: stretch the deformed child across the full path (default False)

Type :

bool

transform ( matrix , * , shape_keys = False )

Transform curve by a matrix

Parameters :

- matrix (mathutils.Matrix) – Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

- shape_keys ( bool ) – Transform Shape Keys (optional)

validate_material_indices ( )

Check the material indices on the splines or letters; returns True when invalid ones were found and reset (to default 0)

Returns :

Result

Return type :

bool

update_gpu_tag ( )

update_gpu_tag

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

| bpy.context.curve BlendData.curves BlendDataCurves.new | BlendDataCurves.remove Object.to_curve |

## CurveMapping(bpy_struct)

### CurveMapping(bpy_struct)

base class — bpy_struct

class bpy.types. CurveMapping ( bpy_struct )

A curve, drawn by the user, that remaps color, vector, and scalar values onto new ones.

black_level

On RGB curves, which color black gets remapped to (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

clip_max_x

(in [-100, 100], default 0.0)

Type :

float

clip_max_y

(in [-100, 100], default 0.0)

Type :

float

clip_min_x

(in [-100, 100], default 0.0)

Type :

float

clip_min_y

(in [-100, 100], default 0.0)

Type :

float

curves

(default None, readonly)

Type :

bpy_prop_collection[CurveMap]

extend

Whether the curve is extrapolated past its ends or simply held flat (default 'HORIZONTAL' )

Type :

Literal['HORIZONTAL', 'EXTRAPOLATED']

tone

Tone of the curve (default 'STANDARD' )

- STANDARD
Standard – Run the combined curve on each channel by itself, which can shift the hue.

- FILMLIKE
Filmlike – Holds the hue steady.

Type :

Literal['STANDARD', 'FILMLIKE']

use_clip

Constrain the curve view so it stays inside a set boundary (default False)

Type :

bool

white_level

On RGB curves, which color white gets remapped to (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

update ( )

Apply the changes you've made to the curve mapping

reset_view ( )

Set the curve mapping grid back to match its clipping size

initialize ( )

Initialize curve

evaluate ( curve , position )

Evaluate curve at given location

Parameters :

- curve (CurveMap) – curve, Curve to evaluate (never None)

- position ( float ) – Position, Position to evaluate curve at (in [-inf, inf])

Returns :

Value, Value of curve at given location (in [-inf, inf])

Return type :

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

| Brush.automasking_cavity_curve Brush.curve_distance_falloff Brush.curve_jitter Brush.curve_random_hue Brush.curve_random_saturation Brush.curve_random_value Brush.curve_size Brush.curve_strength BrushCurvesSculptSettings.curve_parameter_falloff BrushGpencilSettings.curve_jitter BrushGpencilSettings.curve_random_hue BrushGpencilSettings.curve_random_pressure BrushGpencilSettings.curve_random_saturation BrushGpencilSettings.curve_random_strength BrushGpencilSettings.curve_random_uv BrushGpencilSettings.curve_random_value BrushGpencilSettings.curve_sensitivity BrushGpencilSettings.curve_strength ColorManagedViewSettings.curve_mapping CompositorNodeCurveRGB.mapping CompositorNodeHueCorrect.mapping CompositorNodeTime.curve CurvesModifier.curve_mapping EQCurveMappingData.curve_mapping GPencilInterpolateSettings.interpolation_curve GPencilSculptSettings.multiframe_falloff_curve GPencilSculptSettings.thickness_primitive_curve GreasePencilColorModifier.custom_curve GreasePencilHookModifier.custom_curve GreasePencilNoiseModifier.custom_curve GreasePencilOpacityModifier.custom_curve GreasePencilSmoothModifier.custom_curve GreasePencilThickModifierData.custom_curve GreasePencilTintModifier.custom_curve | HookModifier.falloff_curve HueCorrectModifier.curve_mapping LineStyleAlphaModifier_AlongStroke.curve LineStyleAlphaModifier_CreaseAngle.curve LineStyleAlphaModifier_Curvature_3D.curve LineStyleAlphaModifier_DistanceFromCamera.curve LineStyleAlphaModifier_DistanceFromObject.curve LineStyleAlphaModifier_Material.curve LineStyleAlphaModifier_Noise.curve LineStyleAlphaModifier_Tangent.curve LineStyleThicknessModifier_AlongStroke.curve LineStyleThicknessModifier_CreaseAngle.curve LineStyleThicknessModifier_Curvature_3D.curve LineStyleThicknessModifier_DistanceFromCamera.curve LineStyleThicknessModifier_DistanceFromObject.curve LineStyleThicknessModifier_Material.curve LineStyleThicknessModifier_Tangent.curve Paint.cavity_curve ParticleBrush.curve ParticleSettings.clump_curve ParticleSettings.roughness_curve ParticleSettings.twist_curve RenderSettings.motion_blur_shutter_curve Sculpt.automasking_cavity_curve Sculpt.automasking_cavity_curve_op ShaderNodeFloatCurve.mapping ShaderNodeRGBCurve.mapping ShaderNodeVectorCurve.mapping TextureNodeCurveRGB.mapping TextureNodeCurveTime.curve UvSculpt.curve_distance_falloff VertexWeightEditModifier.map_curve VertexWeightProximityModifier.map_curve WarpModifier.falloff_curve |

## Curves(ID)

### Curves(ID)

base classes — bpy_struct, ID

class bpy.types. Curves ( ID )

A data-block for hair, built from hair curves.

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

attributes

Geometry attributes (default None, readonly)

Type :

AttributeGroupCurves[Attribute]

color_attributes

Geometry color attributes (default None, readonly)

Type :

AttributeGroupCurves[Attribute]

curve_offset_data

(default None, readonly)

Type :

bpy_prop_collection[IntAttributeValue]

curves

All curves in the data-block (default None, readonly)

Type :

bpy_prop_collection[CurveSlice]

materials

(default None, readonly)

Type :

IDMaterials[Material]

normals

The normal value of the curve at every one of its control points (default None, readonly)

Type :

bpy_prop_collection[FloatVectorValueReadOnly]

points

Control points of all curves (default None, readonly)

Type :

bpy_prop_collection[CurvePoint]

position_data

(default None, readonly)

Type :

bpy_prop_collection[FloatVectorAttributeValue]

selection_domain

(default 'POINT' )

Type :

Literal[Attribute Curves Domain Items]

surface

Mesh object that the curves can be attached to

Type :

Object

surface_collision_distance

How far the curves are kept clear of the surface (in [1.192e-07, inf], default 0.005)

Type :

float

surface_uv_map

Which surface-mesh attribute defines where each curve attaches (default "", never None)

Type :

str

use_mirror_x

Turn on X-axis symmetry (default False)

Type :

bool

use_mirror_y

Turn on Y-axis symmetry (default False)

Type :

bool

use_mirror_z

Turn on Z-axis symmetry (default False)

Type :

bool

use_sculpt_collision

Let the curves collide with the surface during sculpting (default False)

Type :

bool

add_curves ( sizes )

add_curves

Parameters :

sizes ( Sequence [ int ] ) – Sizes, The number of points in each curve (array of 1 items, in [0, inf])

remove_curves ( * , indices = (0,) )

Drop every curve, or — when indices are supplied — only the curves at those indices.

Parameters :

indices ( Sequence [ int ] ) – Indices, The indices of the curves to remove (array of 1 items, in [0, inf], optional)

resize_curves ( sizes , * , indices = (0,) )

Resize all the curves, or just those at the given indices. Shrinking a curve trims it, while growing one default-initializes the extra end values.

Parameters :

- sizes ( Sequence [ int ] ) – Sizes, The number of points in each curve (array of 1 items, in [1, inf])

- indices ( Sequence [ int ] ) – Indices, The indices of the curves to resize (array of 1 items, in [0, inf], optional)

reorder_curves ( new_indices )

Shuffle the curves into the order given by the new indices.

Parameters :

new_indices ( Sequence [ int ] ) – New indices, The new index for each of the curves (array of 1 items, in [0, inf])

set_types ( * , type = '`CATMULL_ROM`' , indices = (0,) )

Assign the curve type, applying it only to the curves at the given indices when those are provided.

Parameters :

- type (Literal[Curves Type Items]) – Type, (optional)

- indices ( Sequence [ int ] ) – Indices, The indices of the curves to resize (array of 1 items, in [0, inf], optional)

unit_test_compare ( * , curves = None , threshold = 7.1526e-06 )

unit_test_compare

Parameters :

- curves (Curves) – Curves to compare to (optional)

- threshold ( float ) – Threshold, Comparison tolerance threshold (in [0, inf], optional)

Returns :

Return value, String description of result of comparison (never None)

Return type :

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.curves BlendData.hair_curves BlendDataHairCurves.new | BlendDataHairCurves.remove Curves.unit_test_compare |

## See also

- [Bpy Struct](bpy-struct.md)

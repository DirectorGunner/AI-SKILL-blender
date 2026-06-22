# Brushgpencilsettings Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### BrushGpencilSettings(bpy_struct)

base class — bpy_struct

class bpy.types. BrushGpencilSettings ( bpy_struct )

Configures behavior and properties for Grease Pencil brush strokes

active_smooth_factor

Smoothing intensity during the drawing process (in [0, 1], default 0.0)

Type :

float

angle

Direction of maximum brush stroke thickness (0° is horizontal) (in [-1.5708, 1.5708], default 0.0)

Type :

float

angle_factor

Multiplier that thins the stroke when perpendicular to the Angle direction (in [0, 1], default 0.0)

Type :

float

aspect

(array of 2 items, in [0.01, 1], default (0.0, 0.0))

Type :

mathutils.Vector

brush_draw_mode

Initial drawing mode when activating this brush (default 'ACTIVE' )

- ACTIVE
Active – Use current mode.

- MATERIAL
Material – Use always material mode.

- VERTEXCOLOR
Vertex Color – Use always Vertex Color mode.

Type :

Literal['ACTIVE', 'MATERIAL', 'VERTEXCOLOR']

caps_type

Appearance of stroke beginning and endpoints (default 'ROUND' )

Type :

Literal['ROUND', 'FLAT']

curve_jitter

Mapping used to modulate the jitter effect (readonly)

Type :

CurveMapping

curve_random_hue

Curve for controlling hue variability (readonly)

Type :

CurveMapping

curve_random_pressure

Curve for controlling pressure variability (readonly)

Type :

CurveMapping

curve_random_saturation

Curve for controlling saturation variability (readonly)

Type :

CurveMapping

curve_random_strength

Curve for controlling strength variability (readonly)

Type :

CurveMapping

curve_random_uv

Curve for controlling UV variability (readonly)

Type :

CurveMapping

curve_random_value

Curve for controlling value variability (readonly)

Type :

CurveMapping

curve_sensitivity

Mapping used to control drawing responsiveness (readonly)

Type :

CurveMapping

curve_strength

Mapping used to regulate stroke intensity (readonly)

Type :

CurveMapping

dilate

Pixel expansion or contraction applied to fill regions (in [-40, 40], default 1)

Type :

int

eraser_mode

Behavior of the eraser tool (default 'SOFT' )

- SOFT
Dissolve – Erase strokes, fading their points strength and thickness.

- HARD
Point – Erase stroke points.

- STROKE
Stroke – Erase entire strokes.

Type :

Literal['SOFT', 'HARD', 'STROKE']

eraser_strength_factor

Removal intensity affecting stroke color strength (in [0, 100], default 0.0)

Type :

float

eraser_thickness_factor

Removal intensity affecting stroke width (in [0, 100], default 0.0)

Type :

float

extend_stroke_factor

Distance for extending stroke ends to close gaps, zero disables this feature (in [0, inf], default 0.0)

Type :

float

fill_direction

Orientation of the fill operation (default 'NORMAL' )

- NORMAL
Normal – Fill internal area.

- INVERT
Inverted – Fill inverted area.

Type :

Literal['NORMAL', 'INVERT']

fill_draw_mode

Which strokes define fill boundaries (default 'BOTH' )

- BOTH
All – Use both visible strokes and edit lines as fill boundary limits.

- STROKE
Strokes – Use visible strokes as fill boundary limits.

- CONTROL
Edit Lines – Use edit lines as fill boundary limits.

Type :

Literal['BOTH', 'STROKE', 'CONTROL']

fill_extend_mode

How to connect stroke gaps when filling (default 'EXTEND' )

- EXTEND
Extend – Extend strokes in straight lines.

- RADIUS
Radius – Connect endpoints that are close together.

Type :

Literal['EXTEND', 'RADIUS']

fill_factor

Adjustment for boundary precision; greater values increase accuracy but reduce speed (in [0.05, 8], default 0.0)

Type :

float

fill_layer_mode

Which layers supply fill boundaries (default 'VISIBLE' )

- VISIBLE
Visible – Visible layers.

- ACTIVE
Active – Only active layer.

- ABOVE
Layer Above – Layer above active.

- BELOW
Layer Below – Layer below active.

- `ALL_ABOVE`
All Above – All layers above active.

- `ALL_BELOW`
All Below – All layers below active.

Type :

Literal['VISIBLE', 'ACTIVE', 'ABOVE', 'BELOW', '`ALL_ABOVE`', '`ALL_BELOW`']

fill_simplify_level

Count of simplification passes (higher counts reduce accuracy) (in [0, 10], default 0)

Type :

int

fill_threshold

Color opacity level for detecting transparent regions during fill (in [0, 1], default 0.0)

Type :

float

hardness

Gradient strength from Dot and Box stroke centers (1.0 = solid) (in [0.001, 1], default 1.0)

Type :

float

input_samples

Intermediate points created during fast cursor motion (set to 0 to turn off) (in [0, 10], default 0)

Type :

int

material

Stroke material assigned to this brush

Type :

Material

material_alt

Secondary material for alternative brush functions

Type :

Material

outline_thickness_factor

Scale of outline stroke relative to the brush size (in [0, 1], default 0.0)

Type :

float

pen_jitter

Randomness applied to brush radius when initiating strokes (in [0, 100], default 0.0)

Type :

float

pen_smooth_factor

Post-stroke smoothing to reduce tremor and noise (in [0, 2], default 0.0)

Type :

float

pen_smooth_steps

Repetitions of the smoothing algorithm (in [0, 100], default 0)

Type :

int

pen_strength

Initial color intensity for new strokes (affects transparency) (in [0, 1], default 0.0)

Type :

float

pen_subdivision_steps

Subdivisions added to reduce stroke jaggedness (in [0, 3], default 0)

Type :

int

pin_draw_mode

Lock the mode to the brush (default False)

Type :

bool

random_hue_factor

Variability in hue from the original color (in [0, 1], default 0.0)

Type :

float

random_pressure

Variability of pressure effect in strokes (in [0, 1], default 0.0)

Type :

float

random_saturation_factor

Variability in saturation from the original color (in [0, 1], default 0.0)

Type :

float

random_strength

Variability of intensity in strokes (in [0, 1], default 0.0)

Type :

float

random_value_factor

Variability in brightness from the original color (in [0, 1], default 0.0)

Type :

float

show_fill

Display guide lines as fill boundaries (default True)

Type :

bool

show_fill_boundary

Show reference lines indicating fill regions (default True)

Type :

bool

show_fill_extend

Show reference lines for gap closure (default True)

Type :

bool

show_lasso

Suppress fill color display while drawing (default True)

Type :

bool

simplify_factor

Reduction amount using adaptive simplification (in [0, 100], default 0.0)

Type :

float

simplify_pixel_threshold

Screen-space distance below which points align as collinear (in [0, 10], default 0.0)

Type :

float

stroke_type

Drawing technique selection (default 'STROKE' )

Type :

Literal['STROKE', 'FILL', 'BOTH']

use_active_layer_only

Restrict edits to the current layer (default False)

Type :

bool

use_auto_remove_fill_guides

Clean up fill boundary strokes once filling finishes (default True)

Type :

bool

use_collide_strokes

Test whether extension lines intersect with strokes (default False)

Type :

bool

use_edit_position

Allow brush to reposition stroke points (default False)

Type :

bool

use_edit_strength

Allow brush to adjust point color strength (default False)

Type :

bool

use_edit_thickness

Allow brush to modify point width (default False)

Type :

bool

use_edit_uv

Allow brush to rotate point UV (default False)

Type :

bool

use_fill_limit

Restrict filling to visible viewport regions (default True)

Type :

bool

use_jitter_pressure

Apply tablet pressure to jitter (default False)

Type :

bool

use_keep_caps_eraser

Preserve stroke ends without flattening during erasure (default False)

Type :

bool

use_material_pin

Maintain the material tied to this brush (default False)

Type :

bool

use_occlude_eraser

Target only visible and unobstructed strokes for removal (default False)

Type :

bool

use_pressure

Utilize tablet pressure (default False)

Type :

bool

use_random_press_hue

Use pressure to vary hue randomness (default False)

Type :

bool

use_random_press_radius

Use pressure to vary radius randomness (default False)

Type :

bool

use_random_press_sat

Use pressure to vary saturation randomness (default False)

Type :

bool

use_random_press_strength

Use pressure to vary strength randomness (default False)

Type :

bool

use_random_press_uv

Use pressure to vary UV randomness (default False)

Type :

bool

use_random_press_val

Use pressure to vary value randomness (default False)

Type :

bool

use_settings_outline

Convert strokes to outlines (default False)

Type :

bool

use_settings_postprocess

Activate additional processing for fresh strokes (default False)

Type :

bool

use_settings_random

Enable randomization parameters (default False)

Type :

bool

use_settings_stabilizer

Smooth strokes using delayed processing (hold Shift to bypass during drawing) (default True)

Type :

bool

use_strength_pressure

Apply tablet pressure to color strength (default False)

Type :

bool

use_stroke_random_hue

Randomize hue at the stroke level (default False)

Type :

bool

use_stroke_random_radius

Randomize radius at the stroke level (default False)

Type :

bool

use_stroke_random_sat

Randomize saturation at the stroke level (default False)

Type :

bool

use_stroke_random_strength

Randomize intensity at the stroke level (default False)

Type :

bool

use_stroke_random_uv

Randomize UV at the stroke level (default False)

Type :

bool

use_stroke_random_val

Randomize value at the stroke level (default False)

Type :

bool

use_trim

Remove overlapping stroke endings (default False)

Type :

bool

uv_random

Randomization factor for auto-generated UV rotation (in [0, 1], default 0.0)

Type :

float

vertex_color_factor

Blending strength between vertex color and brush color (in [0, 1], default 0.0)

Type :

float

vertex_mode

How vertex color interacts with strokes (default 'STROKE' )

- STROKE
Stroke – Vertex Color affects to Stroke only.

- FILL
Fill – Vertex Color affects to Fill only.

- BOTH
Stroke & Fill – Vertex Color affects to Stroke and Fill.

Type :

Literal['STROKE', 'FILL', 'BOTH']

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

| Brush.gpencil_settings | |

### BrushGpencilSettings(bpy_struct)

Mode to use when creating strokes (default 'STROKE' )

Type :

Literal['STROKE', 'FILL', 'BOTH']

use_active_layer_only

Restrict edits to the current layer (default False)

Type :

bool

use_auto_remove_fill_guides

Clean up fill boundary strokes once filling finishes (default True)

Type :

bool

use_collide_strokes

Test whether extension lines intersect with strokes (default False)

Type :

bool

use_edit_position

Allow brush to reposition stroke points (default False)

Type :

bool

use_edit_strength

Allow brush to adjust point color strength (default False)

Type :

bool

use_edit_thickness

Allow brush to modify point width (default False)

Type :

bool

use_edit_uv

Allow brush to rotate point UV (default False)

Type :

bool

use_fill_limit

Restrict filling to visible viewport regions (default True)

Type :

bool

use_jitter_pressure

Apply tablet pressure to jitter (default False)

Type :

bool

use_keep_caps_eraser

Preserve stroke ends without flattening during erasure (default False)

Type :

bool

use_material_pin

Maintain the material tied to this brush (default False)

Type :

bool

use_occlude_eraser

Target only visible and unobstructed strokes for removal (default False)

Type :

bool

use_pressure

Utilize tablet pressure (default False)

Type :

bool

use_random_press_hue

Use pressure to vary hue randomness (default False)

Type :

bool

use_random_press_radius

Use pressure to vary radius randomness (default False)

Type :

bool

use_random_press_sat

Use pressure to vary saturation randomness (default False)

Type :

bool

use_random_press_strength

Use pressure to vary strength randomness (default False)

Type :

bool

use_random_press_uv

Use pressure to vary UV randomness (default False)

Type :

bool

use_random_press_val

Use pressure to vary value randomness (default False)

Type :

bool

use_settings_outline

Convert strokes to outlines (default False)

Type :

bool

use_settings_postprocess

Activate additional processing for fresh strokes (default False)

Type :

bool

use_settings_random

Enable randomization parameters (default False)

Type :

bool

use_settings_stabilizer

Smooth strokes using delayed processing (press Shift key to override while drawing) (default True)

Type :

bool

use_strength_pressure

Apply tablet pressure to color strength (default False)

Type :

bool

use_stroke_random_hue

Randomize hue at the stroke level (default False)

Type :

bool

use_stroke_random_radius

Randomize radius at the stroke level (default False)

Type :

bool

use_stroke_random_sat

Randomize saturation at the stroke level (default False)

Type :

bool

use_stroke_random_strength

Randomize intensity at the stroke level (default False)

Type :

bool

use_stroke_random_uv

Randomize UV at the stroke level (default False)

Type :

bool

use_stroke_random_val

Randomize value at the stroke level (default False)

Type :

bool

use_trim

Remove overlapping stroke endings (default False)

Type :

bool

uv_random

Randomization factor for auto-generated UV rotation (in [0, 1], default 0.0)

Type :

float

vertex_color_factor

Blending strength between vertex color and brush color (in [0, 1], default 0.0)

Type :

float

vertex_mode

How vertex color interacts with strokes (default 'STROKE' )

- STROKE
Stroke – Vertex Color affects to Stroke only.

- FILL
Fill – Vertex Color affects to Fill only.

- BOTH
Stroke & Fill – Vertex Color affects to Stroke and Fill.

Type :

Literal['STROKE', 'FILL', 'BOTH']

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

| Brush.gpencil_settings | |

## See also

- [Bpy Struct](bpy-struct.md)

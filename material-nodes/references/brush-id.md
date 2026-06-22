# Brush Id (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Brush(ID)

base classes — bpy_struct, ID

class bpy.types. Brush ( ID )

A data-block that holds the settings of a brush used for painting and sculpting.

area_radius_factor

Proportion of the brush radius used when sampling where the area is centered (in [0, 2], default 0.5)

Type :

float

auto_smooth_factor

Degree of smoothing automatically layered onto every stroke (in [0, 1], default 0.0)

Type :

float

automasking_boundary_edges_propagation_steps

How far boundary-edge automasking reaches when shielding vertices from a fully masked edge (in [1, 20], default 1)

Type :

int

automasking_cavity_blur_steps

How many passes of blur are applied to the cavity mask (in [0, 25], default 0)

Type :

int

automasking_cavity_curve

Curve driving the sensitivity (readonly)

Type :

CurveMapping

automasking_cavity_factor

Strength of the cavity mask's contrast (in [0, 5], default 1.0)

Type :

float

automasking_start_normal_falloff

Widen the angular band with a gradient that fades off (in [0.0001, 1], default 0.25)

Type :

float

automasking_start_normal_limit

How wide a span of angles gets affected (in [0.0001, 3.14159], default 0.349066)

Type :

float

automasking_view_normal_falloff

Widen the angular band with a gradient that fades off (in [0.0001, 1], default 0.25)

Type :

float

automasking_view_normal_limit

How wide a span of angles gets affected (in [0.0001, 3.14159], default 1.5708)

Type :

float

blend

The blending mode the brush paints with (default 'MIX' )

- MIX
Mix – Paint using the Mix blending mode.

- DARKEN
Darken – Paint using the Darken blending mode.

- MUL
Multiply – Paint using the Multiply blending mode.

- COLORBURN
Color Burn – Paint using the Color Burn blending mode.

- LINEARBURN
Linear Burn – Paint using the Linear Burn blending mode.

- LIGHTEN
Lighten – Paint using the Lighten blending mode.

- SCREEN
Screen – Paint using the Screen blending mode.

- COLORDODGE
Color Dodge – Paint using the Color Dodge blending mode.

- ADD
Add – Paint using the Add blending mode.

- OVERLAY
Overlay – Paint using the Overlay blending mode.

- SOFTLIGHT
Soft Light – Paint using the Soft Light blending mode.

- HARDLIGHT
Hard Light – Paint using the Hard Light blending mode.

- VIVIDLIGHT
Vivid Light – Paint using the Vivid Light blending mode.

- LINEARLIGHT
Linear Light – Paint using the Linear Light blending mode.

- PINLIGHT
Pin Light – Paint using the Pin Light blending mode.

- DIFFERENCE
Difference – Paint using the Difference blending mode.

- EXCLUSION
Exclusion – Paint using the Exclusion blending mode.

- SUB
Subtract – Paint using the Subtract blending mode.

- HUE
Hue – Paint using the Hue blending mode.

- SATURATION
Saturation – Paint using the Saturation blending mode.

- COLOR
Color – Paint using the Color blending mode.

- LUMINOSITY
Value – Paint using the Value blending mode.

- `ERASE_ALPHA`
Erase Alpha – Erase alpha while painting.

- `ADD_ALPHA`
Add Alpha – Add alpha while painting.

Type :

Literal['MIX', 'DARKEN', 'MUL', 'COLORBURN', 'LINEARBURN', 'LIGHTEN', 'SCREEN', 'COLORDODGE', 'ADD', 'OVERLAY', 'SOFTLIGHT', 'HARDLIGHT', 'VIVIDLIGHT', 'LINEARLIGHT', 'PINLIGHT', 'DIFFERENCE', 'EXCLUSION', 'SUB', 'HUE', 'SATURATION', 'COLOR', 'LUMINOSITY', '`ERASE_ALPHA`', '`ADD_ALPHA`']

blur_kernel_radius

Kernel radius, in pixels, used by the soften and sharpen operations (in [1, 10000], default 2)

Type :

int

blur_mode

(default 'GAUSSIAN' )

Type :

Literal['BOX', 'GAUSSIAN']

boundary_deform_type

The kind of deformation the brush applies (default 'BEND' )

Type :

Literal['BEND', 'EXPAND', 'INFLATE', 'GRAB', 'TWIST', 'SMOOTH']

boundary_falloff_type

Manner in which the brush falloff spreads over the boundary (default 'CONSTANT' )

- CONSTANT
Constant – Deforms the whole boundary by the same amount.

- RADIUS
Brush Radius – Confines the deformation to a region bounded by the brush radius.

- LOOP
Loop – Lays the brush falloff out in a repeating loop.

- `LOOP_INVERT`
Loop and Invert – Repeats the falloff radius in a loop, flipping the displacement direction with each repetition.

Type :

Literal['CONSTANT', 'RADIUS', 'LOOP', '`LOOP_INVERT`']

boundary_offset

How far the boundary origin sits from the brush radius (in [0, 30], default 0.0)

Type :

float

brush_capabilities

What this brush is able to do (readonly, never None)

Type :

BrushCapabilities

cloth_constraint_softbody_strength

Degree to which the cloth holds onto its starting shape, behaving like a soft body (in [0, 1], default 0.0)

Type :

float

cloth_damping

Degree to which applied forces travel through the cloth (in [0.01, 1], default 0.01)

Type :

float

cloth_deform_type

The kind of deformation the brush applies (default 'DRAG' )

Type :

Literal['DRAG', 'PUSH', '`PINCH_POINT`', '`PINCH_PERPENDICULAR`', 'INFLATE', 'GRAB', 'EXPAND', '`SNAKE_HOOK`']

cloth_force_falloff_type

The shape the brush uses to push force into the cloth (default 'RADIAL' )

Type :

Literal['RADIAL', 'PLANE']

cloth_mass

Weight assigned to each simulated particle (in [0.01, 2], default 1.0)

Type :

float

cloth_sim_falloff

Region over which the simulation's effects fade out (in [0, 1], default 0.75)

Type :

float

cloth_sim_limit

Multiplier relative to the radius that caps how far the cloth simulation reaches (in [0.1, 10], default 2.5)

Type :

float

cloth_simulation_area_type

Which portion of the mesh gets simulated while the stroke runs (default 'LOCAL' )

- LOCAL
Local – Simulates just a region around the brush, bounded by a fixed radius.

- GLOBAL
Global – Simulates the whole mesh.

- DYNAMIC
Dynamic – Keeps the simulated area following the brush as it moves.

Type :

Literal['LOCAL', 'GLOBAL', 'DYNAMIC']

color

(array of 3 items, in [0, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Color

color_type

Whether painting uses one flat color or a gradient (default 'COLOR' )

- COLOR
Color – Paint using a single flat color.

- GRADIENT
Gradient – Paint using a gradient.

Type :

Literal['COLOR', 'GRADIENT']

crease_pinch_factor

Strength of the pinch produced by the crease brush (in [0, 1], default 0.5)

Type :

float

cursor_color_add

Cursor color shown while adding (array of 4 items, in [0, inf], default (1.0, 0.39, 0.39, 0.9))

Type :

bpy_prop_array[float]

cursor_color_subtract

Cursor color shown while subtracting (array of 4 items, in [0, inf], default (0.39, 0.39, 1.0, 0.9))

Type :

bpy_prop_array[float]

cursor_overlay_alpha

(in [0, 100], default 33)

Type :

int

curve_distance_falloff

The falloff curve you can edit (readonly, never None)

Type :

CurveMapping

curve_distance_falloff_preset

(default 'CUSTOM' )

Type :

Literal[Brush Curve Preset Items]

curve_jitter

Curve mapping pen pressure onto brush jitter (readonly)

Type :

CurveMapping

curve_random_hue

Curve that modulates the effect (readonly)

Type :

CurveMapping

curve_random_saturation

Curve that modulates the effect (readonly)

Type :

CurveMapping

curve_random_value

Curve that modulates the effect (readonly)

Type :

CurveMapping

curve_size

Curve mapping pen pressure onto brush size (readonly)

Type :

CurveMapping

curve_strength

Curve mapping pen pressure onto brush strength (readonly)

Type :

CurveMapping

curves_sculpt_brush_type

(default 'COMB' )

Type :

Literal[Brush Curves Sculpt Brush Type Items]

curves_sculpt_settings

(readonly)

Type :

BrushCurvesSculptSettings

dash_ratio

Fraction of a cycle's samples during which the brush stays active (in [0, 1], default 1.0)

Type :

float

dash_samples

Length of one dash cycle counted in stroke samples (in [1, 10000], default 20)

Type :

int

deform_target

What the brush's deformation acts upon in the object (default 'GEOMETRY' )

- GEOMETRY
Geometry – The brush moves the mesh's vertices directly.

- `CLOTH_SIM`
Cloth Simulation – The brush reshapes the mesh by altering a cloth simulation's constraints.

Type :

Literal['GEOMETRY', '`CLOTH_SIM`']

density

Proportion of random elements the brush will touch (in [0, 1], default 0.0)

Type :

float

direction

(default 'ADD' )

- ADD
Add – Add the brush's effect.

- SUBTRACT
Subtract – Subtract the brush's effect.

Type :

Literal['ADD', 'SUBTRACT']

disconnected_distance_max

How far to look for loose, disconnected parts within the mesh (in [0, 10], default 0.1)

Type :

float

elastic_deform_type

The kind of deformation the brush applies (default 'GRAB' )

Type :

Literal['GRAB', '`GRAB_BISCALE`', '`GRAB_TRISCALE`', 'SCALE', 'TWIST']

elastic_deform_volume_preservation

Poisson ratio governing elastic deformation. Larger values hold volume better but produce more bulging. (in [0, 0.9], default 0.0)

Type :

float

falloff_angle

Concentrate paint on faces angled toward the view within this angle (in [0, 1.5708], default 0.0)

Type :

float

falloff_shape

Whether falloff is projected or spherical (default 'SPHERE' )

- SPHERE
Sphere – Spreads brush influence outward from the center in a sphere.

- PROJECTED
Projected – Spreads brush influence as a flat circle projected from the view.

Type :

Literal['SPHERE', 'PROJECTED']

fill_threshold

Above this threshold, filling stops spreading (in [0, 100], default 0.2)

Type :

float

flow

How much paint each stroke sample lays down (in [0, 1], default 0.0)

Type :

float

gpencil_brush_type

(default 'DRAW' )

Type :

Literal[Brush Gpencil Types Items]

gpencil_sculpt_brush_type

(default 'SMOOTH' )

Type :

Literal[Brush Gpencil Sculpt Types Items]

gpencil_settings

(readonly)

Type :

BrushGpencilSettings

gpencil_vertex_brush_type

(default 'DRAW' )

Type :

Literal[Brush Gpencil Vertex Types Items]

gpencil_weight_brush_type

(default 'WEIGHT' )

Type :

Literal[Brush Gpencil Weight Types Items]

grad_spacing

How much spacing passes before the brush gradient completes a full loop (in [1, 10000], default 0)

Type :

int

gradient

(readonly)

Type :

ColorRamp

gradient_fill_mode

(default 'LINEAR' )

Type :

Literal['LINEAR', 'RADIAL']

gradient_stroke_mode

(default 'PRESSURE' )

Type :

Literal['PRESSURE', '`SPACING_REPEAT`', '`SPACING_CLAMP`']

hardness

Where the brush falloff begins relative to the brush edge (in [0, 1], default 0.0)

Type :

float

has_unsaved_changes

Signals that user-visible edits have occurred since the brush was imported or loaded from file (default False, readonly)

Type :

bool

height

Height the brush can reach (that is, the layer height for the layer tool) (in [0, 1], default 0.5)

Type :

float

hue_jitter

How much color jitter is applied to hue (in [0, 1], default 0.0)

Type :

float

image_brush_type

(default 'DRAW' )

Type :

Literal[Brush Image Brush Type Items]

image_paint_capabilities

(readonly, never None)

Type :

BrushCapabilitiesImagePaint

input_samples

Count of input samples averaged together to smooth out the stroke (in [1, 64], default 1)

Type :

int

invert_density_pressure

Reverse how pressure modulates density (default False)

Type :

bool

invert_flow_pressure

Reverse how pressure modulates flow (default False)

Type :

bool

invert_hardness_pressure

Reverse how pressure modulates hardness (default False)

Type :

bool

invert_to_scrape_fill

While inverting this brush, switch to the Scrape or Fill brush rather than flipping its displacement direction (default False)

Type :

bool

invert_wet_mix_pressure

Reverse how pressure modulates wet mix (default False)

Type :

bool

invert_wet_persistence_pressure

Reverse how pressure modulates wet persistence (default False)

Type :

bool

jitter

Randomly offset the brush position as you paint (in [0, 1000], default 0.0)

Type :

float

jitter_absolute

Randomly offset the brush position in pixels as you paint (in [0, 1000000], default 0)

Type :

int

jitter_unit

Whether jitter is measured in screen space or relative to brush size (default 'VIEW' )

- VIEW
View – Jitter is measured in screen-space pixels.

- BRUSH
Brush – Jitter is measured relative to the brush size.

Type :

Literal['VIEW', 'BRUSH']

mask_overlay_alpha

(in [0, 100], default 33)

Type :

int

mask_stencil_dimension

Size of the mask stencil within the viewport (array of 2 items, in [-inf, inf], default (256.0, 256.0))

Type :

mathutils.Vector

mask_stencil_pos

Where the mask stencil sits within the viewport (array of 2 items, in [-inf, inf], default (256.0, 256.0))

Type :

mathutils.Vector

mask_texture

Type :

Texture

mask_texture_slot

(readonly)

Type :

BrushTextureSlot

mask_tool

(default 'DRAW' )

Type :

Literal['DRAW', 'SMOOTH']

multiplane_scrape_angle

Angle separating the two planes of the crease (in [0, 160], default 0.0)

Type :

float

normal_radius_factor

Proportion of the brush radius used when sampling the normal (in [0, 2], default 0.5)

Type :

float

normal_weight

Degree to which grab drags vertices off the surface during a grab (in [0, 1], default 0.0)

Type :

float

paint_curve

The paint curve currently active

Type :

PaintCurve

plane_depth

Furthest distance below the plane that vertices are affected. Larger depth reaches vertices deeper beneath the plane. (in [0, 1], default 0.0)

Type :

float

plane_height

Furthest distance above the plane that vertices are affected. Larger height reaches vertices higher above the plane. (in [0, 1], default 1.0)

Type :

float

plane_inversion_mode

Inversion Mode (default '`INVERT_DISPLACEMENT`' )

- `INVERT_DISPLACEMENT`
Invert Displacement – Pushes the vertices in the opposite direction, away from the plane..

- `SWAP_DEPTH_AND_HEIGHT`
Swap Height and Depth – Exchanges what Height and Depth control..

Type :

Literal['`INVERT_DISPLACEMENT`', '`SWAP_DEPTH_AND_HEIGHT`']

plane_offset

Shift the plane the brush works on toward or away from the object's surface (in [-2, 2], default 0.0)

Type :

float

plane_trim

Any vertex farther from the offset plane than this is left untouched (in [0, 1], default 0.5)

Type :

float

pose_deform_type

The kind of deformation the brush applies (default '`ROTATE_TWIST`' )

Type :

Literal['`ROTATE_TWIST`', '`SCALE_TRANSLATE`', '`SQUASH_STRETCH`']

pose_ik_segments

How many segments of the IK chain will bend the mesh (in [1, 20], default 1)

Type :

int

pose_offset

How far the pose origin sits from the brush radius (in [0, 2], default 0.0)

Type :

float

pose_origin_type

How the rotation origins for the brush's segments get chosen (default 'TOPOLOGY' )

- TOPOLOGY
Topology – Picks the rotation origin on its own, guided by the mesh's topology and shape.

- `FACE_SETS`
Face Sets – Builds one pose segment for each face set, beginning at the active one.

- `FACE_SETS_FK`
Face Sets FK – Mimics an FK deformation, using the face set beneath the cursor to control it.

Type :

Literal['TOPOLOGY', '`FACE_SETS`', '`FACE_SETS_FK`']

pose_smooth_iterations

Smoothing passes run once each vertex's pose factor is computed (in [0, 100], default 4)

Type :

int

rake_factor

Degree to which grab tracks the rotation of the cursor (in [0, 10], default 0.0)

Type :

float

rate

Time between paint applications for the Airbrush (in [0.0001, 10000], default 0.1)

Type :

float

saturation_jitter

How much color jitter is applied to saturation (in [0, 1], default 0.0)

Type :

float

sculpt_brush_type

(default 'DRAW' )

Type :

Literal[Brush Sculpt Brush Type Items]

sculpt_capabilities

(readonly, never None)

Type :

BrushCapabilitiesSculpt

sculpt_plane

(default 'AREA' )

Type :

Literal['AREA', 'VIEW', 'X', 'Y', 'Z']

secondary_color

(array of 3 items, in [0, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

sharp_threshold

Below this threshold no sharpening takes place (in [0, 100], default 0.0)

Type :

float

show_multiplane_scrape_planes_preview

Display a preview of the scrape planes on the cursor during the stroke (default False)

Type :

bool

size

Brush diameter measured in pixels (in [1, 10000], default 70)

Type :

int

slide_deform_type

The kind of deformation the brush applies (default 'DRAG' )

Type :

Literal['DRAG', 'PINCH', 'EXPAND']

smear_deform_type

The kind of deformation the brush applies (default 'DRAG' )

Type :

Literal['DRAG', 'PINCH', 'EXPAND']

smooth_deform_type

The kind of deformation the brush applies (default 'LAPLACIAN' )

- LAPLACIAN
Laplacian – Smooths both the surface and the volume.

- SURFACE
Surface – Smooths only the mesh surface, holding the volume in place.

Type :

Literal['LAPLACIAN', 'SURFACE']

smooth_stroke_factor

Larger values produce a smoother stroke (in [0.5, 0.99], default 0.9)

Type :

float

smooth_stroke_radius

How far the cursor must travel from the previous point before the stroke resumes (in [10, 200], default 75)

Type :

int

snake_hook_deform_type

The kind of deformation the brush applies (default 'FALLOFF' )

- FALLOFF
Radius Falloff – Lays the brush falloff out at the brush tip.

- ELASTIC
Elastic – Reshapes the whole mesh through elastic deform.

Type :

Literal['FALLOFF', 'ELASTIC']

spacing

Gap between brush daubs given as a percentage of the brush diameter (in [1, 1000], default 10)

Type :

int

stabilize_normal

How steady the plane normal stays throughout the stroke. At 0 the current normal is used; at 1 the starting normal is used. (in [0, 1], default 0.0)

Type :

float

stabilize_plane

How steady the plane center stays throughout the stroke. At 0 the current center is used; at 1 the starting center is used. (in [0, 1], default 0.0)

Type :

float

stencil_dimension

Size of the stencil within the viewport (array of 2 items, in [-inf, inf], default (256.0, 256.0))

Type :

mathutils.Vector

stencil_pos

Where the stencil sits within the viewport (array of 2 items, in [-inf, inf], default (256.0, 256.0))

Type :

mathutils.Vector

strength

How forceful the brush's effect is once applied (in [0, 10], default 1.0)

Type :

float

stroke_method

(default 'DOTS' )

- DOTS
Dots – Lay paint down at each mouse-move step.

- `DRAG_DOT`
Drag Dot – Lets you carefully place one single dot.

- SPACE
Space – Restrict brush application to the gap set by spacing.

- AIRBRUSH
Airbrush – Keep spraying paint for as long as the mouse is held.

- ANCHORED
Anchored – Pin the brush to where it first landed.

- LINE
Line – Stroke out a line whose dabs are spaced according to spacing.

- CURVE
Curve – Lay the stroke along a Bézier curve (dabs spaced according to spacing).

Type :

Literal['DOTS', '`DRAG_DOT`', 'SPACE', 'AIRBRUSH', 'ANCHORED', 'LINE', 'CURVE']

surface_smooth_current_vertex

How strongly each individual vertex's position weighs on the end result (in [0, 1], default 0.0)

Type :

float

surface_smooth_iterations

Smoothing passes performed for each brush step (in [1, 10], default 0)

Type :

int

surface_smooth_shape_preservation

How much of the starting shape survives the smoothing (in [0, 1], default 0.0)

Type :

float

texture

Type :

Texture

texture_overlay_alpha

(in [0, 100], default 33)

Type :

int

texture_sample_bias

Amount added to texture samples (in [-1, 1], default 0.0)

Type :

float

texture_slot

(readonly)

Type :

BrushTextureSlot

tilt_strength_factor

How strongly pen tilt influences the brush. Negative values reverse the tilt directions. (in [-1, 1], default 0.0)

Type :

float

tip_roundness

How round the brush tip is (in [0, 1], default 1.0)

Type :

float

tip_scale_x

Scaling of the brush tip along the X axis (in [0.0001, 1], default 1.0)

Type :

float

topology_rake_factor

Snap edges into line with the brush direction to produce tidier topology and bring out sharp features. Works best on low-poly meshes since it carries a performance cost. (in [0, 1], default 0.0)

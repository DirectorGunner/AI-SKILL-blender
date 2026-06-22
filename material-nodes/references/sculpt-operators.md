# Sculpt Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Sculpt Operators

bpy.ops.sculpt. brush_stroke ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False , override_location = False , ignore_background_click = False )

Form a mark into the surface

Parameters :

- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)

- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, How the brush applies when drawing a mark (optional)

- NORMAL
Regular – Apply brush normally.

- INVERT
Invert – Invert action of brush for duration of stroke.

- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Alternative brush available during the mark (optional)

- None
None – Apply brush normally.

- SMOOTH
Smooth – Switch to smooth brush for duration of stroke.

- ERASE
Erase – Switch to erase brush for duration of stroke.

- MASK
Mask – Switch to mask brush for duration of stroke.

- pen_flip ( bool ) – Pen Flip, Whether a tablet's eraser mode is being used (optional)

- override_location ( bool ) – Override Location, Recalculate object space positions from provided "mouse_event" positions instead of using the given "location" array (optional)

- ignore_background_click ( bool ) – Ignore Background Click, Background clicks do not commence the mark (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. cloth_filter ( * , start_mouse = (0, 0) , area_normal_radius = 0.25 , strength = 1.0 , iteration_count = 1 , event_history = None , type = 'GRAVITY' , force_axis = {'X', 'Y', 'Z'} , orientation = 'LOCAL' , cloth_mass = 1.0 , cloth_damping = 0.0 , use_face_sets = False , use_collisions = False )

Enact a fabric simulation deformation across the entire surface

Parameters :

- start_mouse ( Sequence [ int ] ) – Starting Mouse, (array of 2 items, in [0, 16384], optional)

- area_normal_radius ( float ) – Normal Radius, Span for computing surface orientation when clicked, measured as a share of brush radius(in [0.001, 5], optional)

- strength ( float ) – Strength, How much the filter affects the surface (in [-10, 10], optional)

- iteration_count ( int ) – Repeat, How many times to execute the filter (in [1, 10000], optional)

- event_history ( bpy_prop_collection [ OperatorStrokeElement ]) – (optional)

- type ( Literal [ 'GRAVITY' , 'INFLATE' , 'EXPAND' , 'PINCH' , 'SCALE' ] ) – Filter Type, Transformation that will be applied to the surface (optional)

- GRAVITY
Gravity – Applies gravity to the simulation.

- INFLATE
Inflate – Inflates the cloth.

- EXPAND
Expand – Expands the cloth's dimensions.

- PINCH
Pinch – Pulls the cloth to the cursor's start position.

- SCALE
Scale – Scales the mesh as a soft body using the origin of the object as scale.

- force_axis ( set [ Literal [ 'X' , 'Y' , 'Z' ] ] ) – Force Axis, Which axis receives the force (optional)

- X
X – Apply force in the X axis.

- Y
Y – Apply force in the Y axis.

- Z
Z – Apply force in the Z axis.

- orientation ( Literal [ 'LOCAL' , 'WORLD' , 'VIEW' ] ) – Orientation, Frame of reference used to constrain the filter force (optional)

- LOCAL
Local – Use the local axis to limit the force and set the gravity direction.

- WORLD
World – Use the global axis to limit the force and set the gravity direction.

- VIEW
View – Use the view axis to limit the force and set the gravity direction.

- cloth_mass ( float ) – Cloth Mass, Weight of every simulation particle (in [0, 2], optional)

- cloth_damping ( float ) – Cloth Damping, How extensively the applied forces diffuse through the fabric (in [0, 1], optional)

- use_face_sets ( bool ) – Use Face Sets, Restrict the filter to the face set beneath the cursor (optional)

- use_collisions ( bool ) – Use Collisions, Contact with other collider objects in the scene (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. color_filter ( * , start_mouse = (0, 0) , area_normal_radius = 0.25 , strength = 1.0 , iteration_count = 1 , event_history = None , type = 'FILL' , fill_color = (1.0, 1.0, 1.0) )

Enact a transformation to change the current color property

Parameters :

- start_mouse ( Sequence [ int ] ) – Starting Mouse, (array of 2 items, in [0, 16384], optional)

- area_normal_radius ( float ) – Normal Radius, Span for computing surface orientation when clicked, measured as a share of brush radius(in [0.001, 5], optional)

- strength ( float ) – Strength, How much the filter affects the colors (in [-10, 10], optional)

- iteration_count ( int ) – Repeat, How many times to execute the filter (in [1, 10000], optional)

- event_history ( bpy_prop_collection [ OperatorStrokeElement ]) – (optional)

- type ( Literal [ 'FILL' , 'HUE' , 'SATURATION' , 'VALUE' , 'BRIGHTNESS' , 'CONTRAST' , 'SMOOTH' , 'RED' , 'GREEN' , 'BLUE' ] ) – Filter Type, (optional)

- FILL
Fill – Fill with a specific color.

- HUE
Hue – Change hue.

- SATURATION
Saturation – Change saturation.

- VALUE
Value – Change value.

- BRIGHTNESS
Brightness – Change brightness.

- CONTRAST
Contrast – Change contrast.

- SMOOTH
Smooth – Smooth colors.

- RED
Red – Change red channel.

- GREEN
Green – Change green channel.

- BLUE
Blue – Change blue channel.

- fill_color (mathutils.Color) – Fill Color, (array of 3 items, in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. detail_flood_fill ( )

Flood the surface with the chosen detail level

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. dynamic_topology_toggle ( )

Dynamic topology allows retopologizing while sculpting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. dyntopo_detail_size_edit ( )

Interactively adjust the dyntopo detail setting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. expand ( * , target = 'MASK' , falloff_type = 'GEODESIC' , invert = False , use_mask_preserve = False , use_falloff_gradient = False , use_modify_active = False , use_reposition_pivot = True , max_geodesic_move_preview = 10000 , use_auto_mask = False , normal_falloff_smooth = 2 )

Multi-purpose sculpt extend capability

Parameters :

- target ( Literal [ 'MASK' , '`FACE_SETS`' , 'COLOR' ] ) – Data Target, Which property receives modification during the extend operation (optional)

- falloff_type ( Literal [ 'GEODESIC' , 'TOPOLOGY' , '`TOPOLOGY_DIAGONALS`' , 'NORMALS' , 'SPHERICAL' , '`BOUNDARY_TOPOLOGY`' , '`BOUNDARY_FACE_SET`' , '`ACTIVE_FACE_SET`' ] ) – Falloff Type, Starting falloff characteristic of the extend operation (optional)

- invert ( bool ) – Invert, Flip the extend active areas (optional)

- use_mask_preserve ( bool ) – Preserve Previous, Keep the earlier condition of the target property (optional)

- use_falloff_gradient ( bool ) – Falloff Gradient, Extend applying a linear falloff (optional)

- use_modify_active ( bool ) – Modify Active, Alter the active face set rather than forming a fresh one (optional)

- use_reposition_pivot ( bool ) – Reposition Pivot, Shift the sculpt transform anchor to the limit of the extend active zone (optional)

- max_geodesic_move_preview ( int ) – Max Vertex Count for Geodesic Move Preview, Highest number of mesh vertices permitting geodesic falloff during anchor movement. Beyond this, falloff switches to spherical (in [0, inf], optional)

- use_auto_mask ( bool ) – Auto Create, Populate mask if no existing mask exists (optional)

- normal_falloff_smooth ( int ) – Normal Smooth, Softening iterations for normal falloff (in [0, 10], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_box_gesture ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , use_front_faces_only = False )

Establish a face set enclosed in a rectangular boundary specified by the cursor

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_change_visibility ( * , mode = 'TOGGLE' , active_face_set = 0 )

Regulate whether face sets display on the sculpted form

Parameters :

- mode ( Literal [ 'TOGGLE' , '`SHOW_ACTIVE`' , '`HIDE_ACTIVE`' ] ) – Mode, (optional)

- TOGGLE
Toggle Visibility – Hide all face sets except for the active one.

- `SHOW_ACTIVE`
Show Active Face Set – Show the active face set.

- `HIDE_ACTIVE`
Hide Active Face Set – Hide the active face set.

- active_face_set ( int ) – Active Face Set, (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_edit ( * , active_face_set = 1 , mode = 'GROW' , strength = 1.0 , modify_hidden = False )

Adjust the currently active face set

Parameters :

- active_face_set ( int ) – Active Face Set, (in [0, inf], optional)

- mode ( Literal [ 'GROW' , 'SHRINK' , '`DELETE_GEOMETRY`' , '`FAIR_POSITIONS`' , '`FAIR_TANGENCY`' ] ) – Mode, (optional)

- GROW
Grow Face Set – Grows the face set boundary by one face based on mesh topology.

- SHRINK
Shrink Face Set – Shrinks the face set boundary by one face based on mesh topology.

- `DELETE_GEOMETRY`
Delete Geometry – Deletes the faces that are assigned to the face set.

- `FAIR_POSITIONS`
Fair Positions – Creates the smoothest possible geometry patch from the face set minimizing changes in vertex positions.

- `FAIR_TANGENCY`
Fair Tangency – Creates the smoothest possible geometry patch from the face set minimizing changes in vertex tangents.

- strength ( float ) – Strength, (in [0, 1], optional)

- modify_hidden ( bool ) – Modify Hidden, Execute the alteration on hidden geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_extract ( * , add_boundary_loop = True , smooth_iterations = 4 , apply_shrinkwrap = True , add_solidify = True )

Produce a fresh mesh form from the chosen face set

Parameters :

- add_boundary_loop ( bool ) – Add Boundary Loop, Introduce an additional edge loop for improved shape retention when a subdivision surface modifier is applied (optional)

- smooth_iterations ( int ) – Smooth Iterations, Smoothing passes applied to the fresh mesh (in [0, inf], optional)

- apply_shrinkwrap ( bool ) – Project to Sculpt, Conform the fresh mesh to the original sculpt (optional)

- add_solidify ( bool ) – Extract as Solid, Form the selection as a solid item with a solidify modifier (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_lasso_gesture ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , use_front_faces_only = False )

Establish a face set in a form specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Cursor motion lags behind and pursues a softer route (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Greater levels yield softer motion (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Smallest span from prior point prior to resuming motion (in [10, 200], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False )

Establish a face set to either edge of a line described by the cursor

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer appearance during the interactive operation (in [0, inf], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

- use_limit_to_segment ( bool ) – Limit to Segment, Confine the gesture activity to the zone within the segment without extending along the complete line (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_set_polyline_gesture ( * , path = None , use_front_faces_only = False )

Establish a face set in a form specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Influence only surfaces oriented toward the camera (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_sets_create ( * , mode = 'MASKED' )

Form a novel face set

Parameters :

mode ( Literal [ 'MASKED' , 'VISIBLE' , 'ALL' , 'SELECTION' ] ) – Mode, (optional)

- MASKED
Face Set from Masked – Create a new face set from the masked faces.

- VISIBLE
Face Set from Visible – Create a new face set from the visible vertices.

- ALL
Face Set Full Mesh – Create a unique face set with all faces in the sculpt.

- SELECTION
Face Set from Edit Mode Selection – Create a face set corresponding to the Edit Mode face selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_sets_init ( * , mode = '`LOOSE_PARTS`' , threshold = 0.5 )

Establish every face set in the surface

Parameters :

- mode ( Literal [ '`LOOSE_PARTS`' , 'MATERIALS' , 'NORMALS' , '`UV_SEAMS`' , 'CREASES' , '`BEVEL_WEIGHT`' , '`SHARP_EDGES`' , '`FACE_SET_BOUNDARIES`' ] ) – Mode, (optional)

- `LOOSE_PARTS`
Face Sets from Loose Parts – Create a face set per loose part in the mesh.

- MATERIALS
Face Sets from Material Slots – Create a face set per material slot.

- NORMALS
Face Sets from Mesh Normals – Create face sets for faces that have similar normal.

- `UV_SEAMS`
Face Sets from UV Seams – Create face sets using UV seams as boundaries.

- CREASES
Face Sets from Edge Creases – Create face sets using edge creases as boundaries.

- `BEVEL_WEIGHT`
Face Sets from Bevel Weight – Create face sets using bevel weights as boundaries.

- `SHARP_EDGES`
Face Sets from Sharp Edges – Create face sets using sharp edges as boundaries.

- `FACE_SET_BOUNDARIES`
Face Sets from Face Set Boundaries – Create a face set per isolated face set.

- threshold ( float ) – Threshold, Lower limit to treat a feature as a boundary when forming face sets (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. face_sets_randomize_colors ( )

Yield a new palette of hues for displaying face sets in the live view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mask_by_color ( * , contiguous = False , invert = False , preserve_previous_mask = False , threshold = 0.35 , location = (0, 0) )

Form a mask using the present color property

Parameters :

- contiguous ( bool ) – Contiguous, Apply masking exclusively to adjoining color zones (optional)

- invert ( bool ) – Invert, Reverse the generated mask (optional)

- preserve_previous_mask ( bool ) – Preserve Previous Mask, Maintain the earlier mask and incorporate or withdraw the fresh one derived from the colors (optional)

- threshold ( float ) – Threshold, How color shifts influence the masking generation (in [0, 1], optional)

- location ( Sequence [ int ] ) – Location, Zone coordinates of sampling (array of 2 items, in [0, 32767], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mask_filter ( * , filter_type = 'SMOOTH' , iterations = 1 , auto_iteration_count = True )

Enact a transformation to modify the present mask

Parameters :

- filter_type ( Literal [ 'SMOOTH' , 'SHARPEN' , 'GROW' , 'SHRINK' , '`CONTRAST_INCREASE`' , '`CONTRAST_DECREASE`' ] ) – Type, Transformation that will be applied to the mask (optional)

- iterations ( int ) – Iterations, Frequency of filter application (in [1, 100], optional)

- auto_iteration_count ( bool ) – Auto Iteration Count, Determine iteration frequency based on mesh vertex count (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mask_from_boundary ( * , mix_mode = 'MIX' , mix_factor = 1.0 , settings_source = 'OPERATOR' , boundary_mode = 'MESH' , propagation_steps = 1 )

Form a mask determined by the perimeter of the geometry

Parameters :

- mix_mode ( Literal [ 'MIX' , 'MULTIPLY' , 'DIVIDE' , 'ADD' , 'SUBTRACT' ] ) – Mode, Blend approach (optional)

- mix_factor ( float ) – Mix Factor, (in [0, 5], optional)

- settings_source ( Literal [ 'OPERATOR' , 'BRUSH' , 'SCENE' ] ) – Settings, Source for parameter values (optional)

- OPERATOR
Operator – Use settings from operator properties.

- BRUSH
Brush – Use settings from brush.

- SCENE
Scene – Use settings from scene.

- boundary_mode ( Literal [ 'MESH' , '`FACE_SETS`' ] ) – Mode, Which boundary style to mask (optional)

- MESH
Mesh – Calculate the boundary mask based on disconnected mesh topology islands.

- `FACE_SETS`
Face Sets – Calculate the boundary mask between face sets.

- propagation_steps ( int ) – Propagation Steps, (in [1, 20], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mask_from_cavity ( * , mix_mode = 'MIX' , mix_factor = 1.0 , settings_source = 'OPERATOR' , factor = 0.5 , blur_steps = 2 , use_curve = False , invert = False )

Form a mask based on the curvature characteristic of the geometry

Parameters :

- mix_mode ( Literal [ 'MIX' , 'MULTIPLY' , 'DIVIDE' , 'ADD' , 'SUBTRACT' ] ) – Mode, Blend approach (optional)

- mix_factor ( float ) – Mix Factor, (in [0, 5], optional)

- settings_source ( Literal [ 'OPERATOR' , 'BRUSH' , 'SCENE' ] ) – Settings, Source for parameter values (optional)

- OPERATOR
Operator – Use settings from operator properties.

- BRUSH
Brush – Use settings from brush.

- SCENE
Scene – Use settings from scene.

- factor ( float ) – Factor, The intensity of the cavity mask (in [0, 5], optional)

- blur_steps ( int ) – Blur, How often the cavity mask is softened (in [0, 25], optional)

- use_curve ( bool ) – Custom Curve, (optional)

- invert ( bool ) – Cavity (Inverted), (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mask_init ( * , mode = '`RANDOM_PER_VERTEX`' )

Form a fresh mask spanning the entire surface

Parameters :

mode ( Literal [ '`RANDOM_PER_VERTEX`' , '`RANDOM_PER_FACE_SET`' , '`RANDOM_PER_LOOSE_PART`' ] ) – Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. mesh_filter ( * , start_mouse = (0, 0) , area_normal_radius = 0.25 , strength = 1.0 , iteration_count = 1 , event_history = None , type = 'INFLATE' , deform_axis = {'X', 'Y', 'Z'} , orientation = 'LOCAL' , surface_smooth_shape_preservation = 0.5 , surface_smooth_current_vertex = 0.5 , sharpen_smooth_ratio = 0.35 , sharpen_intensify_detail_strength = 0.0 , sharpen_curvature_smooth_iterations = 0 )

Enact a transformation to adjust the present surface

Parameters :

- start_mouse ( Sequence [ int ] ) – Starting Mouse, (array of 2 items, in [0, 16384], optional)

- area_normal_radius ( float ) – Normal Radius, Span for computing surface orientation when clicked, measured as a share of brush radius(in [0.001, 5], optional)

- strength ( float ) – Strength, How much the filter affects the surface (in [-10, 10], optional)

- iteration_count ( int ) – Repeat, How many times to execute the filter (in [1, 10000], optional)

- event_history ( bpy_prop_collection [ OperatorStrokeElement ]) – (optional)

- type ( Literal [ 'SMOOTH' , 'SCALE' , 'INFLATE' , 'SPHERE' , 'RANDOM' , 'RELAX' , '`RELAX_FACE_SETS`' , '`SURFACE_SMOOTH`' , 'SHARPEN' , '`ENHANCE_DETAILS`' , '`ERASE_DISPLACEMENT`' ] ) – Filter Type, Transformation that will be applied to the surface (optional)

- SMOOTH
Smooth – Smooth mesh.

- SCALE
Scale – Scale mesh.

- INFLATE
Inflate – Inflate mesh.

- SPHERE
Sphere – Morph into sphere.

- RANDOM
Random – Randomize vertex positions.

- RELAX
Relax – Relax mesh.

- `RELAX_FACE_SETS`
Relax Face Sets – Smooth the edges of all the face sets.

- `SURFACE_SMOOTH`
Surface Smooth – Smooth the surface of the mesh, preserving the volume.

- SHARPEN
Sharpen – Sharpen the cavities of the mesh.

- `ENHANCE_DETAILS`
Enhance Details – Enhance the high frequency surface detail.

- `ERASE_DISPLACEMENT`
Erase Displacement – Deletes the displacement of the Multires Modifier.

- deform_axis ( set [ Literal [ 'X' , 'Y' , 'Z' ] ] ) – Deform Axis, Which axis receives the deformation (optional)

- X
X – Deform in the X axis.

- Y
Y – Deform in the Y axis.

- Z
Z – Deform in the Z axis.

- orientation ( Literal [ 'LOCAL' , 'WORLD' , 'VIEW' ] ) – Orientation, Frame of reference used to constrain the filter displacement (optional)

- LOCAL
Local – Use the local axis to limit the displacement.

- WORLD
World – Use the global axis to limit the displacement.

- VIEW
View – Use the view axis to limit the displacement.

- surface_smooth_shape_preservation ( float ) – Shape Preservation, What amount of the base form remains when smoothing (in [0, 1], optional)

- surface_smooth_current_vertex ( float ) – Per Vertex Displacement, The amount the position of every individual vertex influences the result (in [0, 1], optional)

- sharpen_smooth_ratio ( float ) – Smooth Ratio, What amount of smoothing occurs on polished zones (in [0, 1], optional)

- sharpen_intensify_detail_strength ( float ) – Intensify Details, How much surface indentations and ridges are heightened (in [0, 10], optional)

- sharpen_curvature_smooth_iterations ( int ) – Curvature Smooth Iterations, How much the final shape is softened, disregarding surface texture (in [0, 10], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. optimize ( )

Recalculate the sculpt spatial index for improved efficiency

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt. paint_mask_extract ( * , mask_threshold = 0.5 , add_boundary_loop = True , smooth_iterations = 4 , apply_shrinkwrap = True , add_solidify = True )

Produce a fresh mesh form from the present paint mask

Parameters :

- mask_threshold ( float ) – Threshold, Lowest mask level needed to classify the point viable for creating a surface from the original (in [0, 1], optional)

- add_boundary_loop ( bool ) – Add Boundary Loop, Introduce an additional edge loop for improved shape retention when a subdivision surface modifier is applied (optional)

- smooth_iterations ( int ) – Smooth Iterations, Smoothing passes applied to the fresh mesh (in [0, inf], optional)

- apply_shrinkwrap ( bool ) – Project to Sculpt, Conform the fresh mesh to the original sculpt (optional)

- add_solidify ( bool ) – Extract as Solid, Form the selection as a solid item with a solidify modifier (optional)

# Object Operators (part 5)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_external_pack ( ) 

Internalize external displacement data into the .blend file

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_external_save ( * , filepath = '' , hide_props_region = True , check_existing = True , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = True , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , modifier = '' ) 

Export displacement data to an external file location

Parameters :

- filepath ( str ) – File Path, Directory and filename (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Minimize the operator settings area (optional)

- check_existing ( bool ) – Check Existing, Warn before overwriting (optional)

- filter_blender ( bool ) – Filter .blend files, (optional)

- filter_backup ( bool ) – Filter backup .blend files, (optional)

- filter_image ( bool ) – Filter image files, (optional)

- filter_movie ( bool ) – Filter movie files, (optional)

- filter_python ( bool ) – Filter Python files, (optional)

- filter_font ( bool ) – Filter font files, (optional)

- filter_sound ( bool ) – Filter sound files, (optional)

- filter_text ( bool ) – Filter text files, (optional)

- filter_archive ( bool ) – Filter archive files, (optional)

- filter_btx ( bool ) – Filter btx files, (optional)

- filter_alembic ( bool ) – Filter Alembic files, (optional)

- filter_usd ( bool ) – Filter USD files, (optional)

- filter_obj ( bool ) – Filter OBJ files, (optional)

- filter_volume ( bool ) – Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_blenlib ( bool ) – Filter Blender IDs, (optional)

- filemode ( int ) – File Browser Mode, The setting for the file browser mode to load a .blend file, a library or a special file (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Automatically determine display type for files.

- `LIST_VERTICAL`
Short List – Display files as short list.

- `LIST_HORIZONTAL`
Long List – Display files as a detailed list.

- THUMBNAIL
Thumbnails – Display files as thumbnails.

- sort_method ( str ) – File sorting mode, (optional)

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_higher_levels_delete ( * , modifier = '' ) 

Erase the finer resolution mesh, discarding stored sculpting detail

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_rebuild_subdiv ( * , modifier = '' ) 

Regenerate all subdivision tiers to fabricate a lower-resolution base

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_reshape ( * , modifier = '' ) 

Copy vertex positions from another object

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_subdivide ( * , modifier = '' , mode = '`CATMULL_CLARK`' ) 

Introduce an additional subdivision level

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- mode ( Literal [ '`CATMULL_CLARK`' , 'SIMPLE' , 'LINEAR' ] ) – Subdivision Mode, Strategy for splitting the mesh into a finer tier (optional)

- `CATMULL_CLARK`
Catmull-Clark – Split using Catmull-Clark algorithm.

- SIMPLE
Simple – Split using simple neighbor averaging.

- LINEAR
Linear – Split using linear interpolation of manual sculpting.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. multires_unsubdivide ( * , modifier = '' ) 

Lower-level reconstruction from the existing subdivision hierarchy

Parameters :

modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. ocean_bake ( * , modifier = '' , free = False ) 

Render and store a time series of ocean simulation data

Parameters :

- modifier ( str ) – Modifier, Name of the modifier to edit (optional, never None)

- free ( bool ) – Free, Release the stored data rather than generate it (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. origin_clear ( ) 

Reset the object's origin point

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. origin_set ( * , type = '`GEOMETRY_ORIGIN`' , center = 'MEDIAN' ) 

Position the object's origin point, either by moving the data or repositioning to data bounds or 3D cursor

Parameters :

- type ( Literal [ '`GEOMETRY_ORIGIN`' , '`ORIGIN_GEOMETRY`' , '`ORIGIN_CURSOR`' , '`ORIGIN_CENTER_OF_MASS`' , '`ORIGIN_CENTER_OF_VOLUME`' ] ) – Type, (optional)

- `GEOMETRY_ORIGIN`
Geometry to Origin – Relocate geometry to the object origin.

- `ORIGIN_GEOMETRY`
Origin to Geometry – Set origin to the geometric center (using the chosen pivot standard or bounding envelope).

- `ORIGIN_CURSOR`
Origin to 3D Cursor – Place the object origin where the 3D cursor is positioned.

- `ORIGIN_CENTER_OF_MASS`
Origin to Center of Mass (Surface) – Calculate the point of equal weight using surface area.

- `ORIGIN_CENTER_OF_VOLUME`
Origin to Center of Mass (Volume) – Calculate the point of equal weight using enclosed volume (requires closed geometry).

- center ( Literal [ 'MEDIAN' , 'BOUNDS' ] ) – Center, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. parent_clear ( * , type = 'CLEAR' ) 

Sever the object's parent connection

Parameters :

type ( Literal [ 'CLEAR' , '`CLEAR_KEEP_TRANSFORM`' , '`CLEAR_INVERSE`' ] ) – Type, (optional)

- CLEAR
Clear Parent – Fully remove the parent link and any tied constraints.

- `CLEAR_KEEP_TRANSFORM`
Clear and Keep Transformation – Sever the parent link while holding the current visual position.

- `CLEAR_INVERSE`
Clear Parent Inverse – Erase the transform offset built into the parent link without breaking the connection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. parent_inverse_apply ( ) 

Bake the parenting offset into the object's native geometry

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. parent_no_inverse_set ( * , keep_transform = False ) 

Make the object a child without adjusting the parent transform correction

Parameters :

keep_transform ( bool ) – Keep Transform, Preserve the world alignment while parenting (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. parent_set ( * , type = 'OBJECT' , xmirror = False , keep_transform = False ) 

Establish the object's parent connection

Parameters :

- type ( Literal [ 'OBJECT' , 'ARMATURE' , '`ARMATURE_NAME`' , '`ARMATURE_AUTO`' , '`ARMATURE_ENVELOPE`' , 'BONE' , '`BONE_RELATIVE`' , 'CURVE' , 'FOLLOW' , '`PATH_CONST`' , 'LATTICE' , 'VERTEX' , '`VERTEX_TRI`' ] ) – Type, (optional)

- xmirror ( bool ) – X Mirror, Duplicate weights symmetrically across the X axis, for Envelope/Automatic influence group assignment (optional)

- keep_transform ( bool ) – Keep Transform, Preserve the object's world position before establishing the link (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. particle_system_add ( ) 

Insert a particle emission system

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. particle_system_remove ( ) 

Discard the current particle emission system

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. paste_transform ( * , method = 'CURRENT' , bake_step = 0 , use_mirror = False , mirror_axis_loc = 'x' , mirror_axis_rot = 'z' , use_relative = False ) 

Transfer the stored translation/rotation/scale matrix from the clipboard to the active pose bone or object. Uses global-space transformation data

Parameters :

- method ( Literal [ 'CURRENT' , '`EXISTING_KEYS`' , 'BAKE' ] ) – Paste Method, Overwrite immediate values, marked animation frames, or produce new animation frames (optional)

- CURRENT
Current Transform – Overwrite the now-active values only, respecting auto-keying if enabled.

- `EXISTING_KEYS`
Selected Keys – Overwrite marked animation frames, potentially creating new frames on those times.

- BAKE
Bake on Key Range – Overwrite all frames between the first and last marked key, creating animation frames if required.

- bake_step ( int ) – Frame Step, Only applies to baking; step=1 adds a frame per tick, step=2 every other tick (in [1, inf], optional)

- use_mirror ( bool ) – Mirror Transform, When pasting, invert the transform relative to an anchor object or bone (optional)

- mirror_axis_loc ( Literal [ 'x' , 'y' , 'z' ] ) – Location Axis, Which spatial axis to flip for position (optional)

- mirror_axis_rot ( Literal [ 'x' , 'y' , 'z' ] ) – Rotation Axis, Which spatial axis to flip for orientation (optional)

- use_relative ( bool ) – Use Relative Paste, When pasting, treat the matrix as relative to another object (configured in the interface) (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/copy_global_transform.py:325

bpy.ops.object. paths_calculate ( * , display_type = 'RANGE' , range = 'SCENE' ) 

Build tracking trails for chosen objects

Parameters :

- display_type (Literal[Motionpath Display Type Items]) – Display Type, (optional)

- range (Literal[Motionpath Range Items]) – Computation Range, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. paths_clear ( * , only_selected = False ) 

Undocumented, consider contributing.

Parameters :

only_selected ( bool ) – Only Selected, Limit the operation to chosen objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. paths_update ( ) 

Recalculate tracking trails for chosen objects

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. paths_update_visible ( ) 

Recalculate all visible tracking trails for objects and skeletal rigs

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. pointcloud_random_add ( * , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , scale = (0.0, 0.0, 0.0) ) 

Place a point cloud object into the scene

Parameters :

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, Direction the inserted object will face (optional)

- WORLD
World – Orient the object to global axes.

- VIEW
View – Orient the object to match the camera view.

- CURSOR
3D Cursor – Use the 3D cursor's orientation for the object.

- location (mathutils.Vector) – Location, Placement point for the newly inserted object (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, Orientation to apply when inserting the object (array of 3 items, in [-inf, inf], optional)

- scale (mathutils.Vector) – Scale, Size scaling during insertion (array of 3 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. posemode_toggle ( ) 

Switch between posing and standard object interaction

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. quadriflow_remesh ( * , use_mesh_symmetry = True , use_preserve_sharp = False , use_preserve_boundary = False , preserve_attributes = False , smooth_normals = False , mode = 'FACES' , target_ratio = 1.0 , target_edge_length = 0.1 , target_faces = 4000 , mesh_area = -1.0 , seed = 0 ) 

Rebuild the mesh using quadrilateral topology computed from the existing surface. All per-vertex layers will be erased

Parameters :

- use_mesh_symmetry ( bool ) – Use Mesh Symmetry, Outputs a symmetrical mesh using configured symmetry settings (optional)

- use_preserve_sharp ( bool ) – Preserve Sharp, Attempt to maintain sharp corners (optional)

- use_preserve_boundary ( bool ) – Preserve Mesh Boundary, Attempt to maintain the outer perimeter (optional)

- preserve_attributes ( bool ) – Preserve Attributes, Re-transfer properties to the newly built mesh (optional)

- smooth_normals ( bool ) – Smooth Normals, Configure output surface normals as smooth (optional)

- mode ( Literal [ 'RATIO' , 'EDGE' , 'FACES' ] ) – Mode, How to set the granularity of the new mesh (optional)

- RATIO
Ratio – Set density as a ratio of face count relative to original.

- EDGE
Edge Length – Set density using target spacing between vertices.

- FACES
Faces – Set density using target face count.

- target_ratio ( float ) – Ratio, Density relative to the original face count (in [0, inf], optional)

- target_edge_length ( float ) – Edge Length, Spacing goal for the new mesh (in [1e-07, inf], optional)

- target_faces ( int ) – Number of Faces, Expected face count (quads) in the new mesh (in [1, inf], optional)

- mesh_area ( float ) – Old Object Face Area, Cache for computing object bounds; used internally (in [-inf, inf], optional)

- seed ( int ) – Seed, RNG state for solver variation. Changing will alter the quad distribution pattern (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.object. quick_explode ( * , style = 'EXPLODE' , amount = 100 , frame_duration = 50 , frame_start = 1 , frame_end = 10 , velocity = 1.0 , fade = True ) 

Detonate chosen objects into fragments

Parameters :

- style ( Literal [ 'EXPLODE' , 'BLEND' ] ) – Explode Style, (optional)

- amount ( int ) – Number of Pieces, (in [2, 10000], optional)

- frame_duration ( int ) – Duration, (in [1, 300000], optional)

- frame_start ( int ) – Start Frame, (in [1, 300000], optional)

- frame_end ( int ) – End Frame, (in [1, 300000], optional)

- velocity ( float ) – Outwards Velocity, (in [0, 300000], optional)

- fade ( bool ) – Fade, Dim the fragments progressively (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_quick_effects.py:273

bpy.ops.object. quick_fur ( * , density = 'MEDIUM' , length = 0.1 , radius = 0.001 , view_percentage = 1.0 , apply_hair_guides = True , use_noise = True , use_frizz = True ) 

Build a hair/fur system on chosen objects

Parameters :

- density ( Literal [ 'LOW' , 'MEDIUM' , 'HIGH' ] ) – Density, (optional)

- length ( float ) – Length, (in [0.001, 100], optional)

- radius ( float ) – Hair Radius, (in [0, 10], optional)

- view_percentage ( float ) – View Percentage, (in [0, 1], optional)

- apply_hair_guides ( bool ) – Apply Hair Guides, (optional)

- use_noise ( bool ) – Noise, (optional)

- use_frizz ( bool ) – Frizz, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_quick_effects.py:92

bpy.ops.object. quick_liquid ( * , show_flows = False ) 

Set chosen objects as liquid contributors

Parameters :

show_flows ( bool ) – Render Liquid Objects, Display liquid object geometry when rendering (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_quick_effects.py:553

bpy.ops.object. quick_smoke ( * , style = 'SMOKE' , show_flows = False ) 

Attach smoke/fire emitters to chosen objects

Parameters :

- style ( Literal [ 'SMOKE' , 'FIRE' , 'BOTH' ] ) – Smoke Style, (optional)

- show_flows ( bool ) – Render Smoke Objects, Display smoke object geometry when rendering (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_quick_effects.py:447

bpy.ops.object. randomize_transform ( * , random_seed = 0 , use_delta = False , use_loc = True , loc = (0.0, 0.0, 0.0) , use_rot = True , rot = (0.0, 0.0, 0.0) , use_scale = True , scale_even = False , scale = (1.0, 1.0, 1.0) ) 

Vary objects position, direction, and dimension unpredictably

Parameters :

- random_seed ( int ) – Random Seed, Initialization state for the random generator (in [0, 10000], optional)

- use_delta ( bool ) – Transform Delta, Randomize offset transformation instead of primary transformation (optional)

- use_loc ( bool ) – Randomize Location, Vary the placement values (optional)

- loc (mathutils.Vector) – Location, Maximum scatter span per axis (array of 3 items, in [-100, 100], optional)

- use_rot ( bool ) – Randomize Rotation, Vary the orientation values (optional)

- rot (mathutils.Euler) – Rotation, Maximum turn per axis (array of 3 items, in [-3.14159, 3.14159], optional)

- use_scale ( bool ) – Randomize Scale, Vary the scaling values (optional)

- scale_even ( bool ) – Scale Even, Apply identical scaling on all axes (optional)

- scale ( Sequence [ float ] ) – Scale, Maximum scaling shift per axis (array of 3 items, in [-100, 100], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/object_randomize_transform.py:163

bpy.ops.object. reset_override_library ( ) 

Reinstate the chosen editable instances to match their linked sources

# Uv Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### UV Operators

Blender provides many UV mapping methods, from basic plane projections to more sophisticated approaches.

### Unwrap

Reference

Editor:

3D Viewport

Mode:

Edit Mode

Menu:

UV → Unwrap Angle Based, Unwrap Conformal, Unwrap Minimum Stretch

Shortcut:

U

Reference

Editor:

UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Unwrap Angle Based, Unwrap Conformal, Unwrap Minimum Stretch

Shortcut:

U

Cuts selected faces at seams, flattens them, and arranges them across the UV map. Pre-existing UV coordinates get replaced.
Well-suited for organic forms.

Result of unwrapping Suzanne.

### Options

Adjust Last Operation panel allows detailed control:

Method

Angle Based:

Uses Angle Based Flattening (ABF). Produces a precise 2D representation.

Conformal:

Uses Least Squares Conformal Mapping (LSCM).
Typically gives less accurate UV mapping than Angle Based, yet performs better on simpler shapes.

Minimum Stretch:

Uses Scalable Locally Injective Mapping (SLIM). Seeks to reduce both area and angle distortion.

Fill Holes
Pre-fill holes to better reduce overlaps and maintain symmetry during unwrap.

Use Subdivision Surface
Apply vertex positions from the Subdivision Surface Modifier (rather than pre-modifier positions).

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Iterations Minimum Stretch
Repetitions for Minimum Stretch method, with each reducing distortion further.

No Flip Minimum Stretch
Prevent faces from flipping. Flipping occasionally lowers distortion when pins are used.

Importance Weights Minimum Stretch
Use a vertex group to manually control face sizes in the UV map.
High-weight faces consume more UV space than low-weight ones.

Enabling reveals two additional settings:

Weight Group
The vertex group name to apply.

Weight Factor
A scale applied to all weights. Larger values exaggerate high-weight versus low-weight zones.

Margin Method
The Margin parameter's meaning, governing empty space between UV islands.

Scaled
Margin is somewhat arbitrary, independent of UV island sizes or texture dimensions.

Add
Like above, but without internal scaling.

Fraction
Margin is a fraction of UV bounds. On a 1024x1024 texture with Margin at 1/1024, islands get 1-pixel margins (and stay 2+ pixels apart).

Margin
Empty space between islands. Margin Method controls its interpretation.

### Smart UV Project

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Smart UV Project

Shortcut:

U

Evaluates angles between selected faces, cuts them where edges are sharp, then projects each separated group along its mean normal onto the UV map. Seams can enable extra cutting. Suited for rigid shapes and structures.

Smart UV project on a truncated pyramid.

### Options

Adjust Last Operation panel allows detailed control:

Angle Limit
The highest angle allowed between adjacent-face normals before separation. Low limits create many small islands with little distortion; high limits yield few large islands with potential distortion.

Margin Method
The Island Margin parameter's meaning, governing empty space between UV islands.

Scaled
Island Margin is somewhat arbitrary, independent of UV island sizes or texture.

Add
Like above, but without internal scaling.

Fraction
Island Margin is a fraction of the UV square. On a 1024x1024 texture with Island Margin at 1/1024, islands get 1-pixel margins (and stay 2+ pixels apart).

Rotation Method

Axis-aligned
Auto-rotate to conserve space.

Axis-aligned (Horizontal)
Rotate islands to sit horizontally.

Axis-aligned (Vertical)
Rotate islands to sit vertically.

Island Margin
Empty space between islands. Margin Method controls its interpretation.

Area Weight
At 0, each group's projection vector is the average of its face normals.
At 1, it's an area-weighted average. Intermediate values blend both.

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Scale to Bounds
Scale the produced UV map outward until it occupies the whole texture.

### Lightmap Pack

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Lightmap Pack

Shortcut:

U

Positions each selected face individually on the UV map. Lightmaps are widely used for baking lighting into textures for real-time rendering – they maximize texture usage, typically producing a fragmented and skewed UV map unsuitable for hand texturing.

### Options

Adjust Last Operation panel allows detailed control:

Selection

Selected Faces
Only unwraps chosen faces.

All Faces
Unwraps the entire mesh.

Share Texture Space
Multi-Object Editing allows generating UV maps for several meshes simultaneously.
When Share Texture Space is on, UV maps won't cross, so a single lightmap texture can serve all meshes.

New UV Map
Generates a fresh UV map instead of overwriting the current one. See UV Maps.

Pack Quality
Increased values yield less-wasted UV space (yet take longer to process).

Margin
Empty space between faces in the UV map.

### Follow Active Quads

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Follow Active Quads

Shortcut:

U

Starting from the active quad, attaches its chosen neighboring quads sequentially to its pre-existing UV quad. Non-quad faces are skipped.

Note

Since the active quad's UV stays unchanged, you typically want to first ensure it has similar proportions in the UV and mesh (e.g., by unwrapping just that face first). Otherwise, distortion spreads outward.

Note

The resulting UV map can exceed bounds. Scale it manually or apply Pack Islands to correct.

### Options

Adjust Last Operation panel allows detailed control:

Edge Length Mode
Method for computing the UV edge lengths of newly attached quads.

Even
Each new UV edge gets the same length as the UV edge it extends, regardless of mesh edge length.

Length
Each new UV edge length is proportional to its mesh edge length.

Length Average
Each new UV edge length is proportional to its edge ring's average mesh edge length.

### Cube Projection

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Cube Projection

Shortcut:

U

Assigns each selected face to the most fitting side of an imaginary cube, then lays all sides across the UV map, overlapping. Use Pack Islands to separate if needed.

The cube aligns with the Transform Pivot Point center and the mesh's local axes.

### Options

Adjust Last Operation panel allows detailed control:

Cube Size
The projection cube's dimension.

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Clip to Bounds
Relocates out-of-bounds UVs to the closest border.

Scale to Bounds
Scale the produced UV map outward until it occupies the whole texture.

### Cylinder Projection

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Cylinder Projection

Shortcut:

U

Maps selected faces onto a virtual cylinder, then unwraps it.
The cylinder centers on the Transform Pivot Point, typically at the selected faces' averaged position; you can move it elsewhere (e.g., using the 3D Cursor).

### Options

Adjust Last Operation panel allows detailed control:

Direction, Align
The cylinder axis's orientation.

View on Equator
Use an axis perpendicular to the current viewport direction.
If Align is Polar ZX, use the vertical viewport axis; if Polar ZY, use the horizontal.

View on Poles
Use an axis parallel to the current viewport direction.
The cylinder rotates 90° on its axis, and the UV map shifts a quarter-width, based on Align.

Align to Object
Use the object's local Z axis.
The cylinder rotates 90° on its axis, and the UV map shifts a quarter-width, based on Align.

Pole
How to treat vertices on the cylinder axis.

Pinch
Gather all UV versions of the vertex to the same U coordinate.
Often results in heavy UV face distortion.

Fan
Spread each UV version across U coordinates that reduce distortion.

| Unwrapping the top of a dome. | Pole set to Pinch. | Pole set to Fan. |

Preserve Seams
Cut the mesh along seams before applying projection.

Radius
Half the cylinder height (not its radius; the cylinder exists only for projection, so its radius is irrelevant).

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Clip to Bounds
Relocates out-of-bounds UVs to the closest border.

Scale to Bounds
Scale the produced UV map outward until it occupies the whole texture.

### Sphere Projection

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Unwrap → Sphere Projection

Shortcut:

U

Casts selected faces onto an imaginary sphere, then flattens it like a world map: latitude lines run vertical, longitude lines space evenly. Helpful for texturing globular objects like eyes or planets.

The sphere centers on the Transform Pivot Point, typically at the selected faces' averaged position; you can move it elsewhere (e.g., using the 3D Cursor).

Using an equirectangular image with a Sphere Projection.

### Options

Adjust Last Operation panel allows detailed control:

Direction, Align
The sphere axis's orientation.

View on Equator
Use an axis perpendicular to the current viewport direction.
If Align is Polar ZX, use the vertical viewport axis; if Polar ZY, use the horizontal.

View on Poles
Use an axis parallel to the current viewport direction.
The sphere rotates 90° on its vertical axis, and the UV map shifts a quarter-width, based on Align.

Align to Object
Use the object's local Z axis.
The sphere rotates 90° on its vertical axis, and the UV map shifts a quarter-width, based on Align.

Pole
How to treat vertices on the sphere axis.
(See Cylinder Projection for an example.)

Pinch
Gather all UV versions of the vertex to the same U coordinate.
Often results in heavy UV face distortion.

Fan
Spread each UV version across U coordinates that reduce distortion.

Preserve Seams
Cut the mesh along seams before applying projection.

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Clip to Bounds
Relocates out-of-bounds UVs to the closest border.

Scale to Bounds
Scale the produced UV map outward until it occupies the whole texture.

### Project from View

Reference

Editor:

3D Viewport

Mode:

Edit Mode

Menu:

UV → Project from View

Shortcut:

U

Maps selected faces onto the viewport plane. The UV map becomes a wireframe view of the mesh from the current angle. Choose this when using a photo of a real object as texture. Receding areas will show stretching.

### Options

Adjust Last Operation panel allows detailed control:

Orthographic
Apply Orthographic instead of Perspective projection.

Camera Bounds
Align the image borders that would display through the current camera with UV map borders.
Only affects rendering through the camera; see Viewing the Active Camera.

Correct Aspect
Compensates UV mapping for the target image's aspect ratio.
UVs scale properly when unwrapping to non-square textures.

For this to function, the mesh needs a material with an Image Texture node, which must be chosen in the Shader Editor.

Clip to Bounds
Relocates out-of-bounds UVs to the closest border.

Scale to Bounds
Scale the produced UV map outward until it occupies the whole texture.

### Project from View (Bounds)

Reference

Editor:

3D Viewport

Mode:

Edit Mode

Menu:

UV → Project from View (Bounds)

Shortcut:

U

Identical to Project from View, but with Scale to Bounds enabled by default.

### Reset

Reference

Editor:

3D Viewport, UV Editor

Mode:

Edit Mode

Menu:

UV → Reset

Shortcut:

U

Resets each selected face's UV layout to cover the full UV area.

## Uv Operators

### Uv Operators 

bpy.ops.uv. align ( * , axis = '`ALIGN_AUTO`' , position_mode = 'MEAN' ) 

Lines up the chosen UV vertices along a straight line

Parameters :

- axis ( Literal [ '`ALIGN_S`' , '`ALIGN_T`' , '`ALIGN_U`' , '`ALIGN_AUTO`' , '`ALIGN_X`' , '`ALIGN_Y`' ] ) – Axis, Axis to align UV locations on (optional)

- `ALIGN_S`
Straighten – Snap UV vertices to the line running between the two endpoints.

- `ALIGN_T`
Straighten X – Snap UV vertices to that endpoint line by shifting them horizontally.

- `ALIGN_U`
Straighten Y – Snap UV vertices to that endpoint line by shifting them vertically.

- `ALIGN_AUTO`
Align Auto – Pick automatically whichever direction is already closest to aligned.

- `ALIGN_X`
Align Vertically – Place UV vertices along a vertical line.

- `ALIGN_Y`
Align Horizontally – Place UV vertices along a horizontal line.

- position_mode ( Literal [ 'MEAN' , 'MIN' , 'MAX' ] ) – Position Mode, Method of calculating the alignment position (optional)

- MEAN
Mean – Line the UVs up on their average position.

- MIN
Minimum – Line the UVs up on their minimum position.

- MAX
Maximum – Line the UVs up on their maximum position.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. align_rotation ( * , method = 'AUTO' , axis = 'X' , correct_aspect = False ) 

Sets the rotation of the UV island

Parameters :

- method ( Literal [ 'AUTO' , 'EDGE' , 'GEOMETRY' ] ) – Method, Method to calculate rotation angle (optional)

- AUTO
Auto – Derive the angle from every edge.

- EDGE
Edge – Use only the edges that are selected.

- GEOMETRY
Geometry – Align against the Geometry axis.

- axis ( Literal [ 'X' , 'Y' , 'Z' ] ) – Axis, Axis to align to (optional)

- X
X – X axis.

- Y
Y – Y axis.

- Z
Z – Z axis.

- correct_aspect ( bool ) – Correct Aspect, Take image aspect ratio into account (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/uvcalc_transform.py:360

bpy.ops.uv. arrange_islands ( * , initial_position = '`BOUNDING_BOX`' , axis = 'Y' , align = 'MIN' , order = '`LARGE_TO_SMALL`' , margin = 0.05 ) 

Lays the chosen UV islands out along a line

Parameters :

- initial_position ( Literal [ '`BOUNDING_BOX`' , '`UV_GRID`' , '`ACTIVE_UDIM`' , 'CURSOR' ] ) – Initial Position, Initial position to arrange islands from (optional)

- `BOUNDING_BOX`
Bounding Box – Start the layout from the bounding box of the islands.

- `UV_GRID`
UV Grid – Start the layout from the UV Tile Grid.

- `ACTIVE_UDIM`
Active UDIM – Start the layout from the Active UDIM.

- CURSOR
2D Cursor – Start the layout from the 2D cursor.

- axis ( Literal [ 'X' , 'Y' ] ) – Axis, Axis to arrange UV islands on (optional)

- X
X – Lay the UV islands out along the X axis.

- Y
Y – Lay the UV islands out along the Y axis.

- align ( Literal [ 'MIN' , 'MAX' , 'CENTER' , 'NONE' ] ) – Align, Location to align islands on (optional)

- MIN
Min – Snap the islands to their own min edge.

- MAX
Max – Snap the islands to their own max edge.

- CENTER
Center – Snap the islands to the center of the biggest island.

- NONE
None – Leave the island alignment untouched.

- order ( Literal [ '`LARGE_TO_SMALL`' , '`SMALL_TO_LARGE`' , 'Fixed' ] ) – Order, Order of islands (optional)

- `LARGE_TO_SMALL`
Largest to Smallest – Order islands big-first down to small.

- `SMALL_TO_LARGE`
Smallest to Largest – Order islands small-first up to large.

- Fixed
Fixed – Leave the island order as it is.

- margin ( float ) – Margin, Space between islands (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. average_islands_scale ( * , scale_uv = False , shear = False ) 

Evens out the scale of distinct UV islands using their 3D-space area

Parameters :

- scale_uv ( bool ) – Non-Uniform, Scale U and V independently (optional)

- shear ( bool ) – Shear, Reduce shear within islands (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. copy ( ) 

Copies the UV vertices that are selected

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. copy_mirrored_faces ( * , direction = 'POSITIVE' , precision = 3 ) 

Mirrors UV coordinates across the X axis using a mirrored mesh as reference

Parameters :

- direction ( Literal [ 'POSITIVE' , 'NEGATIVE' ] ) – Axis Direction, (optional)

- precision ( int ) – Precision, Tolerance for finding vertex duplicates (in [1, 16], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. cube_project ( * , cube_size = 1.0 , correct_aspect = True , clip_to_bounds = False , scale_to_bounds = False ) 

Maps the mesh's UV vertices onto the six sides of a cube

Parameters :

- cube_size ( float ) – Cube Size, Size of the cube to project on (in [0, inf], optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- clip_to_bounds ( bool ) – Clip to Bounds, Clip UV coordinates to bounds after unwrapping (optional)

- scale_to_bounds ( bool ) – Scale to Bounds, Scale UV coordinates to bounds after unwrapping (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. cursor_set ( * , location = (0.0, 0.0) ) 

Places the 2D cursor at a given location

Parameters :

location (mathutils.Vector) – Location, Cursor location in normalized (0.0 to 1.0) coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. custom_region_set ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True )

Defines the limits of the user region

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. cylinder_project ( * , direction = '`VIEW_ON_EQUATOR`' , align = '`POLAR_ZX`' , pole = 'PINCH' , seam = False , radius = 1.0 , correct_aspect = True , clip_to_bounds = False , scale_to_bounds = False ) 

Maps the mesh's UV vertices onto the curved side of a cylinder

Parameters :

- direction ( Literal [ '`VIEW_ON_EQUATOR`' , '`VIEW_ON_POLES`' , '`ALIGN_TO_OBJECT`' ] ) – Direction, Direction of the sphere or cylinder (optional)

- `VIEW_ON_EQUATOR`
View on Equator – The 3D viewpoint sits at the equator.

- `VIEW_ON_POLES`
View on Poles – The 3D viewpoint sits at the poles.

- `ALIGN_TO_OBJECT`
Align to Object – Follow the object's transform for alignment.

- align ( Literal [ '`POLAR_ZX`' , '`POLAR_ZY`' ] ) – Align, How to determine rotation around the pole (optional)

- `POLAR_ZX`
Polar ZX – Take X as polar 0.

- `POLAR_ZY`
Polar ZY – Take Y as polar 0.

- pole ( Literal [ 'PINCH' , 'FAN' ] ) – Pole, How to handle faces at the poles (optional)

- PINCH
Pinch – Squeeze the UVs together at the poles.

- FAN
Fan – Spread the UVs out at the poles.

- seam ( bool ) – Preserve Seams, Separate projections by islands isolated by seams (optional)

- radius ( float ) – Radius, Radius of the sphere or cylinder (in [0, inf], optional)

- correct_aspect ( bool ) – Correct Aspect, Map UVs taking aspect ratio of the image associated with the material into account (optional)

- clip_to_bounds ( bool ) – Clip to Bounds, Clip UV coordinates to bounds after unwrapping (optional)

- scale_to_bounds ( bool ) – Scale to Bounds, Scale UV coordinates to bounds after unwrapping (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. export_layout ( * , filepath = '' , export_all = False , export_tiles = 'NONE' , modified = False , mode = 'PNG' , size = (1024, 1024) , opacity = 0.25 , check_existing = True ) 

Writes the UV layout out to a file

Parameters :

- filepath ( str ) – filepath, (optional, never None)

- export_all ( bool ) – All UVs, Export all UVs in this mesh (not just visible ones) (optional)

- export_tiles ( Literal [ 'NONE' , 'UDIM' , 'UV' ] ) – Export Tiles, Choose whether to export only the [0, 1] range, or all UV tiles (optional)

- NONE
None – Write out only the UVs that fall in the [0, 1] range.

- UDIM
UDIM – Write tiles using the UDIM numbering scheme: 1001 + u_tile + 10*v_tile.

- UV
UVTILE – Write tiles using the UVTILE numbering scheme: u(u_tile + 1)_v(v_tile + 1).

- modified ( bool ) – Modified, Exports UVs from the modified mesh (optional)

- mode ( Literal [ 'SVG' , 'EPS' , 'PNG' ] ) – Format, File format to export the UV layout to (optional)

- SVG
Scalable Vector Graphic (.svg) – Save the UV layout as a vector SVG file.

- EPS
Encapsulated PostScript (.eps) – Save the UV layout as a vector EPS file.

- PNG
PNG Image (.png) – Save the UV layout as a bitmap image.

- size ( Sequence [ int ] ) – Size, Dimensions of the exported file (array of 2 items, in [8, 32768], optional)

- opacity ( float ) – Fill Opacity, Set amount of opacity for exported UV layout (in [0, 1], optional)

- check_existing ( bool ) – check_existing, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/io_mesh_uv_layout/__init__.py:139

bpy.ops.uv. follow_active_quads ( * , mode = '`LENGTH_AVERAGE`' ) 

Propagates UVs from the active quads through connected face loops

Parameters :

mode ( Literal [ 'EVEN' , 'LENGTH' , '`LENGTH_AVERAGE`' ] ) – Edge Length Mode, Method to space UV edge loops (optional)

- EVEN
Even – Give every UV the same spacing.

- LENGTH
Length – Space each loop's UVs by its average edge length.

- `LENGTH_AVERAGE`
Length Average – Space each loop's UVs by its average edge length.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/uvcalc_follow_active.py:302

bpy.ops.uv. hide ( * , unselected = False ) 

Hides the selected or unselected UV vertices

Parameters :

unselected ( bool ) – Unselected, Hide unselected rather than selected (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.uv. lightmap_pack ( * , `PREF_CONTEXT` = '`SEL_FACES`' , `PREF_PACK_IN_ONE` = True , `PREF_NEW_UVLAYER` = False , `PREF_BOX_DIV` = 12 , `PREF_MARGIN_DIV` = 0.1 ) 

Fits the UVs of each face inside the UV bounds

Parameters :

- `PREF_CONTEXT` ( Literal [ '`SEL_FACES`' , '`ALL_FACES`' ] ) – Selection, (optional)

- `SEL_FACES`
Selected Faces – Restrict packing to the selected faces.

- `ALL_FACES`
All Faces – Pack every face the mesh contains.

- `PREF_PACK_IN_ONE` ( bool ) – Share Texture Space, Objects share texture space, map all objects into a single UV map (optional)

- `PREF_NEW_UVLAYER` ( bool ) – New UV Map, Create a new UV map for every mesh packed (optional)

- `PREF_BOX_DIV` ( int ) – Pack Quality, Quality of the packing. Higher values will be slower but waste less space (in [1, 48], optional)

- `PREF_MARGIN_DIV` ( float ) – Margin, Size of the margin as a division of the UV (in [0.001, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/uvcalc_lightmap.py:664

bpy.ops.uv. mark_seam ( * , clear = False ) 

Flags the chosen UV edges as seams

Parameters :

clear ( bool ) – Clear Seams, Clear instead of marking seams (optional)

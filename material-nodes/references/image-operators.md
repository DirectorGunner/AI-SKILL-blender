# Image Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Image Display and Rendering Operations

bpy.ops.image.add_render_slot ( )
Introduce a fresh render output slot

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.change_frame ( * , frame = 0 )
Alter the timeline position interactively

Parameters:
frame ( int ) – Frame, (in [-1048574, 1048574], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.clear_render_border ( )
Erase render region boundaries and deactivate region rendering

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.clear_render_slot ( )
Blank out the current render output slot

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.clipboard_copy ( )
Transfer the image to the system clipboard

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.clipboard_paste ( )
Import a fresh image from the system clipboard

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.convert_to_mesh_plane ( * , interpolation = 'Linear' , extension = 'CLIP' , use_auto_refresh = True , relative = True , shader = 'PRINCIPLED' , emit_strength = 1.0 , use_transparency = True , render_method = 'DITHERED' , use_backface_culling = False , show_transparent_back = True , overwrite_material = True , name_from = 'OBJECT' , delete_ref = True )
Transform active reference images into textured plane geometry

Parameters:
- interpolation ( Literal [ 'Linear' , 'Closest' , 'Cubic' , 'Smart' ] ) – Interpolation, How pixels are interpolated (optional)
- Linear: Linear interpolation
- Closest: No interpolation (nearest texel)
- Cubic: Cubic interpolation
- Smart: Bicubic magnification, bilinear otherwise (OSL only)
- extension ( Literal [ 'CLIP' , 'EXTEND' , 'REPEAT' ] ) – Extension, Behaviour at image edges (optional)
- CLIP: Truncate at edge and make surrounding transparent
- EXTEND: Extend edge pixels across boundary
- REPEAT: Tile the image horizontally and vertically
- use_auto_refresh ( bool ) – Auto Refresh, Rerender image on every frame change (optional)
- relative ( bool ) – Relative Paths, Store file paths as relative (optional)
- shader ( Literal [ 'PRINCIPLED' , 'SHADELESS' , 'EMISSION' ] ) – Shader, Which material shader to apply (optional)
- PRINCIPLED: Use principled shader
- SHADELESS: Visible to camera and reflections only
- EMISSION: Use emission shader
- emit_strength ( float ) – Emission Strength, Radiance magnitude (in [0, inf], optional)
- use_transparency ( bool ) – Use Alpha, Employ alpha for blending (optional)
- render_method ( Literal [ 'DITHERED' , 'BLENDED' ] ) – Render Method, (optional)
- DITHERED: Use hash-based opacity with pass/raytracing compatibility (deferred rendering)
- BLENDED: Colored transparency (incompatible with passes/raytracing, forward rendering)
- use_backface_culling ( bool ) – Backface Culling, Hide rear-facing surface (optional)
- show_transparent_back ( bool ) – Show Backface, Render stacked transparent layers (may create sorting issues) (optional)
- overwrite_material ( bool ) – Overwrite Material, Swap existing material with matching title (optional)
- name_from ( Literal [ 'OBJECT' , 'IMAGE' ] ) – Name After, What to name the new plane and material (optional)
- OBJECT: Use object name with suffix
- IMAGE: Use image name
- delete_ref ( bool ) – Delete Reference Object, Discard the image reference once plane is created (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File:
startup/bl_operators/image_as_planes.py:1133

bpy.ops.image.curves_point_set ( * , point = '`BLACK_POINT`' , size = 1 )
Designate dark or light anchor for curve adjustment

Parameters:
- point ( Literal [ '`BLACK_POINT`' , '`WHITE_POINT`' ] ) – Point, Anchor location for curve control (optional)
- size ( int ) – Sample Size, (in [1, 128], optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.cycle_render_slot ( * , reverse = False )
Rotate through accessible render output slots

Parameters:
reverse ( bool ) – Cycle in Reverse, (optional)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

bpy.ops.image.external_edit ( * , filepath = '' )
Open image in a third-party editing application

Parameters:
filepath ( str ) – filepath, (optional, never None)

Returns:
Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File:
startup/bl_operators/image.py:54

bpy.ops.image.file_browse ( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )
Browse for an image file, Shift-click to open, Alt-click for containing folder

Parameters:
- filepath ( str ) – File Path, Location of the file (optional, never None)
- hide_props_region ( bool ) – Hide Operator Properties, Minimize the operator properties panel (optional)
- check_existing ( bool ) – Check Existing, Warn before replacing files (optional)
- filter_blender ( bool ) – Filter .blend files, (optional)
- filter_backup ( bool ) – Filter backup .blend files, (optional)
- filter_image ( bool ) – Filter image files, (optional)
- filter_movie ( bool ) – Filter movie files, (optional)
- filter_python ( bool ) – Filter Python files, (optional)

- filter_font ( bool ) – Show font files in the dialog, (optional)

- filter_sound ( bool ) – Show sound files in the dialog, (optional)

- filter_text ( bool ) – Show text files in the dialog, (optional)

- filter_archive ( bool ) – Show archive files in the dialog, (optional)

- filter_btx ( bool ) – Show btx files in the dialog, (optional)

- filter_alembic ( bool ) – Show Alembic files in the dialog, (optional)

- filter_usd ( bool ) – Show USD files in the dialog, (optional)

- filter_obj ( bool ) – Show OBJ files in the dialog, (optional)

- filter_volume ( bool ) – Show OpenVDB volume files in the dialog, (optional)

- filter_folder ( bool ) – Show folders in the dialog, (optional)

- filter_blenlib ( bool ) – Show Blender IDs in the dialog, (optional)

- filemode ( int ) – File Browser Mode, Which file-browser mode to use when loading a .blend file, a library, or a special file (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Pick the file relative to the current blend file (optional)

- show_multiview ( bool ) – Enable Multi-View, (optional)

- use_multiview ( bool ) – Use Multi-View, (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Let Blender pick the display type for files automatically.

- `LIST_VERTICAL`
Short List – Show files in a compact list.

- `LIST_HORIZONTAL`
Long List – Show files in a detailed list.

- THUMBNAIL
Thumbnails – Show files as thumbnail previews.

- sort_method ( str ) – File sorting mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. flip ( * , use_flip_x = False , use_flip_y = False )

Flip the image

Parameters :

- use_flip_x ( bool ) – Horizontal, Mirror the image left-to-right (optional)

- use_flip_y ( bool ) – Vertical, Mirror the image top-to-bottom (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. import_as_mesh_planes ( * , interpolation = 'Linear' , extension = 'CLIP' , use_auto_refresh = True , relative = True , shader = 'PRINCIPLED' , emit_strength = 1.0 , use_transparency = True , render_method = 'DITHERED' , use_backface_culling = False , show_transparent_back = True , overwrite_material = True , filepath = '' , align = 'WORLD' , location = (0.0, 0.0, 0.0) , rotation = (0.0, 0.0, 0.0) , files = None , directory = '' , filter_image = True , filter_movie = True , filter_folder = True , force_reload = False , image_sequence = False , offset = True , offset_axis = '+X' , offset_amount = 0.1 , align_axis = '`CAM_AX`' , prev_align_axis = 'NONE' , align_track = False , size_mode = 'ABSOLUTE' , fill_mode = 'FILL' , height = 1.0 , factor = 600.0 )

Build mesh plane(s) from image files, matching each plane to its image's aspect ratio

Parameters :

- interpolation ( Literal [ 'Linear' , 'Closest' , 'Cubic' , 'Smart' ] ) – Interpolation, How the texture is sampled (optional)

- Linear
Linear – Linear sampling between texels.

- Closest
Closest – Take the nearest texel with no blending.

- Cubic
Cubic – Cubic sampling for smoother results.

- Smart
Smart – Bicubic when magnifying, bilinear otherwise (OSL only).

- extension ( Literal [ 'CLIP' , 'EXTEND' , 'REPEAT' ] ) – Extension, Behavior for pixels sampled outside the image's original bounds (optional)

- CLIP
Clip – Limit to the image size and make pixels outside it transparent.

- EXTEND
Extend – Carry on by repeating the image's edge pixels.

- REPEAT
Repeat – Tile the image across both axes.

- use_auto_refresh ( bool ) – Auto Refresh, Re-read the image whenever the frame changes (optional)

- relative ( bool ) – Relative Paths, Store file paths relative to the blend file (optional)

- shader ( Literal [ 'PRINCIPLED' , 'SHADELESS' , 'EMISSION' ] ) – Shader, Which node shader to apply (optional)

- PRINCIPLED
Principled – Use the Principled shader.

- SHADELESS
Shadeless – Visible only to the camera and to reflections.

- EMISSION
Emission – Use an Emission shader.

- emit_strength ( float ) – Emission Strength, How strongly the plane emits light (in [0, inf], optional)

- use_transparency ( bool ) – Use Alpha, Read the alpha channel for transparency (optional)

- render_method ( Literal [ 'DITHERED' , 'BLENDED' ] ) – Render Method, (optional)

- DITHERED
Dithered – Grayscale hashed transparency that works with render passes and ray-tracing; also called deferred rendering..

- BLENDED
Blended – Colored transparency that does not work with render passes or ray-tracing; also called forward rendering..

- use_backface_culling ( bool ) – Backface Culling, Hide the reverse side of faces with backface culling (optional)

- show_transparent_back ( bool ) – Show Backface, Draw several transparent layers (can cause transparency sorting artifacts) (optional)

- overwrite_material ( bool ) – Overwrite Material, Replace any existing material that shares the same name (optional)

- filepath ( str ) – File Path, Filepath used for importing the file (optional, never None)

- align ( Literal [ 'WORLD' , 'VIEW' , 'CURSOR' ] ) – Align, (optional)

- WORLD
World – Orient the new object to world space.

- VIEW
View – Orient the new object to the current view.

- CURSOR
3D Cursor – Take the new object's orientation from the 3D cursor.

- location (mathutils.Vector) – Location, (array of 3 items, in [-inf, inf], optional)

- rotation (mathutils.Euler) – Rotation, (array of 3 items, in [-inf, inf], optional)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – files, (optional)

- directory ( str ) – directory, (optional, never None)

- filter_image ( bool ) – filter_image, (optional)

- filter_movie ( bool ) – filter_movie, (optional)

- filter_folder ( bool ) – filter_folder, (optional)

- force_reload ( bool ) – Force Reload, Reload the image even if it is already open somewhere else in Blender (optional)

- image_sequence ( bool ) – Detect Image Sequences, Bring numbered image runs in as a single animated sequence rather than separate planes (optional)

- offset ( bool ) – Offset Planes, Space the planes apart; when off, every plane lands at the same spot (optional)

- offset_axis ( Literal [ '+X' , '+Y' , '+Z' , '-X' , '-Y' , '-Z' ] ) – Offset Direction, Which local axis the planes are arranged along (optional)

- +X
+X – Side by Side to the Left.

- +Y
+Y – Side by Side, Downward.

- +Z
+Z – Stacked Above.

- -X
-X – Side by Side to the Right.

- -Y
-Y – Side by Side, Upward.

- -Z
-Z – Stacked Below.

- offset_amount ( float ) – Offset Distance, Spacing placed between neighboring planes (in [-inf, inf], optional)

- align_axis ( Literal [ '+X' , '+Y' , '+Z' , '-X' , '-Y' , '-Z' , 'CAM' , '`CAM_AX`' ] ) – Align, Which way the planes face (optional)

- +X
+X – Facing positive X.

- +Y
+Y – Facing positive Y.

- +Z
+Z – Facing positive Z.

- -X
-X – Facing negative X.

- -Y
-Y – Facing negative Y.

- -Z
-Z – Facing negative Z.

- CAM
Face Camera – Facing camera.

- `CAM_AX`
Camera's Main Axis – Facing the camera's dominant axis.

- prev_align_axis ( Literal [ '+X' , '+Y' , '+Z' , '-X' , '-Y' , '-Z' , 'CAM' , '`CAM_AX`' , 'NONE' ] ) – prev_align_axis, (optional)

- +X
+X – Facing positive X.

- +Y
+Y – Facing positive Y.

- +Z
+Z – Facing positive Z.

- -X
-X – Facing negative X.

- -Y
-Y – Facing negative Y.

- -Z
-Z – Facing negative Z.

- CAM
Face Camera – Facing camera.

- `CAM_AX`
Camera's Main Axis – Facing the camera's dominant axis.

- NONE
Undocumented.

- align_track ( bool ) – Track Camera, Constrain the planes so they keep facing the camera (optional)

- size_mode ( Literal [ 'ABSOLUTE' , 'CAMERA' , 'DPI' , 'DPBU' ] ) – Size Mode, How the plane size is worked out (optional)

- ABSOLUTE
Absolute – Use an absolute size.

- CAMERA
Scale to Camera Frame – Size to fit or fill the camera frame.

- DPI
Pixels per Inch – Size from pixels per inch.

- DPBU
Pixels per Blender Unit – Size from pixels per Blender Unit.

- fill_mode ( Literal [ 'FILL' , 'FIT' ] ) – Scale, How the plane is sized against the camera frame (optional)

- FILL
Fill – Cover the camera frame, overflowing its edges.

- FIT
Fit – Keep the whole image inside the camera frame.

- height ( float ) – Height, Height of the plane that gets created (in [0.001, inf], optional)

- factor ( float ) – Definition, Pixels per inch or per Blender Unit (in [1, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. invert ( * , invert_r = False , invert_g = False , invert_b = False , invert_a = False )

Invert image's channels

Parameters :

- invert_r ( bool ) – Red, Flip the red channel (optional)

- invert_g ( bool ) – Green, Flip the green channel (optional)

- invert_b ( bool ) – Blue, Flip the blue channel (optional)

- invert_a ( bool ) – Alpha, Flip the alpha channel (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. match_movie_length ( )

Set the image's frame range to match the video's duration

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. new ( * , name = 'Untitled' , width = 1024 , height = 1024 , color = (0.0, 0.0, 0.0, 1.0) , alpha = True , generated_type = 'BLANK' , float = False , use_stereo_3d = False , tiled = False )

Create a new image

Parameters :

- name ( str ) – Name, Name of the image data-block (optional, never None)

- width ( int ) – Width, Image width (in [1, inf], optional)

- height ( int ) – Height, Image height (in [1, inf], optional)

- color ( Sequence [ float ] ) – Color, Color used to fill the image (array of 4 items, in [0, inf], optional)

- alpha ( bool ) – Alpha, Give the new image an alpha channel (optional)

- generated_type (Literal[Image Generated Type Items]) – Generated Type, Fill with a grid useful for checking UV maps (optional)

- float ( bool ) – 32-bit Float, Make the image use 32-bit floating-point depth (optional)

- use_stereo_3d ( bool ) – Stereo 3D, Give the image separate left and right views (optional)

- tiled ( bool ) – Tiled, Make a tiled image (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. open ( * , allow_path_tokens = True , filepath = '' , directory = '' , files = None , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' , use_sequence_detection = True , use_udim_detecting = True )

Open image

Parameters :

- allow_path_tokens ( bool ) – Permit substitution tokens inside the path (optional)

- filepath ( str ) – File Path, Path to file (optional, never None)

- directory ( str ) – Directory, Directory of the file (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – Files, (optional)

- hide_props_region ( bool ) – Hide Operator Properties, Fold away the area that shows the operator settings (optional)

- check_existing ( bool ) – Check Existing, Warn before overwriting files that already exist (optional)

- filter_blender ( bool ) – Show .blend files in the dialog, (optional)

- filter_backup ( bool ) – Show backup .blend files in the dialog, (optional)

- filter_image ( bool ) – Show image files in the dialog, (optional)

- filter_movie ( bool ) – Show movie files in the dialog, (optional)

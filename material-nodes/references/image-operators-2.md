# Image Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- filter_python ( bool ) – Show Python files in the dialog, (optional)

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

- use_sequence_detection ( bool ) – Detect Sequences, Spot animated sequences among the selected images using their file names (optional)

- use_udim_detecting ( bool ) – Detect UDIMs, Find selected UDIM files and pull in every matching tile (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. open_images ( * , directory = '' , files = None , relative_path = True , use_sequence_detection = True , use_udim_detection = True )

Undocumented, consider contributing.

Parameters :

- directory ( str ) – directory, (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – files, (optional)

- relative_path ( bool ) – Use relative path, (optional)

- use_sequence_detection ( bool ) – Use sequence detection, (optional)

- use_udim_detection ( bool ) – Use UDIM detection, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. pack ( )

Pack an image as embedded data into the .blend file

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. project_apply ( )

Project edited image back onto the object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. project_edit ( )

Edit a snapshot of the 3D Viewport in an external image editor

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. read_viewlayers ( )

Read all the current scene's view layers from cache, as needed

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. reload ( )

Reload current image from disk

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. remove_render_slot ( )

Remove the current render slot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. render_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True )

Set the boundaries of the render region and enable render region

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

bpy.ops.image. replace ( * , filepath = '' , hide_props_region = True , check_existing = False , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Replace current image by another one from disk

Parameters :

- filepath ( str ) – File Path, Path to file (optional, never None)

- hide_props_region ( bool ) – Hide Operator Properties, Fold away the area that shows the operator settings (optional)

- check_existing ( bool ) – Check Existing, Warn before overwriting files that already exist (optional)

- filter_blender ( bool ) – Show .blend files in the dialog, (optional)

- filter_backup ( bool ) – Show backup .blend files in the dialog, (optional)

- filter_image ( bool ) – Show image files in the dialog, (optional)

- filter_movie ( bool ) – Show movie files in the dialog, (optional)

- filter_python ( bool ) – Show Python files in the dialog, (optional)

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

bpy.ops.image. resize ( * , size = (0, 0) , all_udims = False )

Resize the image

Parameters :

- size ( Sequence [ int ] ) – Size, (array of 2 items, in [1, inf], optional)

- all_udims ( bool ) – All UDIM Tiles, Rescale every UDIM tile in the image (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. rotate_orthogonal ( * , degrees = '90' )

Rotate the image

Parameters :

degrees ( Literal [ '90' , '180' , '270' ] ) – Degrees, How far to rotate, in degrees (90, 180, 270) (optional)

- 90
90 Degrees – Turn 90 degrees clockwise.

- 180
180 Degrees – Turn 180 degrees clockwise.

- 270
270 Degrees – Turn 270 degrees clockwise.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. sample ( * , size = 1 )

Use mouse to sample a color in current image

Parameters :

size ( int ) – Sample Size, (in [1, 128], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. sample_line ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 )

Sample a line and show it in Scope panels

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer style shown while the modal operator runs (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. save ( )

Save the image with current name and settings

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. save_all_modified ( )

Save all modified images

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. save_as ( * , save_as_render = False , copy = False , allow_path_tokens = True , filepath = '' , check_existing = True , filter_blender = False , filter_backup = False , filter_image = True , filter_movie = True , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = False , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 9 , relative_path = True , show_multiview = False , use_multiview = False , display_type = 'DEFAULT' , sort_method = '' )

Save the image with another name and/or settings

Parameters :

- save_as_render ( bool ) – Save As Render, Write the image with render color management.For display formats such as PNG, bake in the view and display transform.For intermediate formats such as OpenEXR, keep the default render-output color space(optional)

- copy ( bool ) – Copy, Write a fresh image file while leaving the current Blender image untouched (optional)

- allow_path_tokens ( bool ) – Permit substitution tokens inside the path (optional)

- filepath ( str ) – File Path, Path to file (optional, never None)

- check_existing ( bool ) – Check Existing, Warn before overwriting files that already exist (optional)

- filter_blender ( bool ) – Show .blend files in the dialog, (optional)

- filter_backup ( bool ) – Show backup .blend files in the dialog, (optional)

- filter_image ( bool ) – Show image files in the dialog, (optional)

- filter_movie ( bool ) – Show movie files in the dialog, (optional)

- filter_python ( bool ) – Show Python files in the dialog, (optional)

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

bpy.ops.image. save_sequence ( )

Save a sequence of images

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. tile_add ( * , number = 1002 , count = 1 , label = '' , fill = True , color = (0.0, 0.0, 0.0, 1.0) , generated_type = 'BLANK' , width = 1024 , height = 1024 , float = False , alpha = True )

Adds a tile to the image

Parameters :

- number ( int ) – Number, UDIM number for the tile (in [1001, 2000], optional)

- count ( int ) – Count, How many tiles to add (in [1, inf], optional)

- label ( str ) – Label, Optional label for the tile (optional, never None)

- fill ( bool ) – Fill, Populate the new tile with a generated image (optional)

- color ( Sequence [ float ] ) – Color, Color used to fill the image (array of 4 items, in [0, inf], optional)

- generated_type (Literal[Image Generated Type Items]) – Generated Type, Fill with a grid useful for checking UV maps (optional)

- width ( int ) – Width, Image width (in [1, inf], optional)

- height ( int ) – Height, Image height (in [1, inf], optional)

- float ( bool ) – 32-bit Float, Make the image use 32-bit floating-point depth (optional)

- alpha ( bool ) – Alpha, Give the new image an alpha channel (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. tile_fill ( * , color = (0.0, 0.0, 0.0, 1.0) , generated_type = 'BLANK' , width = 1024 , height = 1024 , float = False , alpha = True )

Fill the current tile with a generated image

Parameters :

- color ( Sequence [ float ] ) – Color, Color used to fill the image (array of 4 items, in [0, inf], optional)

- generated_type (Literal[Image Generated Type Items]) – Generated Type, Fill with a grid useful for checking UV maps (optional)

- width ( int ) – Width, Image width (in [1, inf], optional)

- height ( int ) – Height, Image height (in [1, inf], optional)

- float ( bool ) – 32-bit Float, Make the image use 32-bit floating-point depth (optional)

- alpha ( bool ) – Alpha, Give the new image an alpha channel (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. tile_remove ( )

Removes a tile from the image

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. unpack ( * , method = '`USE_LOCAL`' , id = '' )

Save an image packed in the .blend file to disk

Parameters :

- method (Literal[Unpack Method Items]) – Method, How to unpack (optional)

- id ( str ) – Image Name, Name of the image data-block to unpack (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_all ( * , fit_view = False )

View the entire image

Parameters :

fit_view ( bool ) – Fit View, Size the frame to the viewport (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_center_cursor ( )

Center the view so that the cursor is in the middle of the view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_cursor_center ( * , fit_view = False )

Set 2D cursor to center view location

Parameters :

fit_view ( bool ) – Fit View, Size the frame to the viewport (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_ndof ( )

Use a 3D mouse device to pan/zoom the view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_pan ( * , offset = (0.0, 0.0) )

Pan the view

Parameters :

offset (mathutils.Vector) – Offset, Offset in floating-point units, where 1.0 equals the image's width and height (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_selected ( )

View all selected UVs

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_zoom ( * , factor = 0.0 , use_cursor_init = True )

Zoom in/out the image

Parameters :

- factor ( float ) – Factor, Zoom factor; above 1.0 zooms in and below it zooms out (in [-inf, inf], optional)

- use_cursor_init ( bool ) – Use Mouse Position, Let the starting mouse position be used (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_zoom_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , zoom_out = False )

Zoom in the view to the nearest item contained in the border

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- zoom_out ( bool ) – Zoom Out, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_zoom_in ( * , location = (0.0, 0.0) )

Zoom in the image (centered around 2D cursor)

Parameters :

location (mathutils.Vector) – Location, Cursor position in screen coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_zoom_out ( * , location = (0.0, 0.0) )

Zoom out the image (centered around 2D cursor)

Parameters :

location (mathutils.Vector) – Location, Cursor position in screen coordinates (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.image. view_zoom_ratio ( * , ratio = 0.0 )

Set zoom ratio of the view

Parameters :

ratio ( float ) – Ratio, Zoom ratio where 1.0 is 1:1; higher zooms in and lower zooms out (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

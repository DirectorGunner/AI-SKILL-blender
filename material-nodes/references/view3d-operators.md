# View3D Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### View3D Operators 

bpy.ops.view3d. bone_select_menu ( * , name = '' , extend = False , deselect = False , toggle = False ) 

Selects a bone through a menu

Parameters :

- name ( str ) – Bone Name, (optional)

- extend ( bool ) – Extend, (optional)

- deselect ( bool ) – Deselect, (optional)

- toggle ( bool ) – Toggle, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. camera_background_image_add ( * , filepath = '' , relative_path = True , name = '' , session_uid = 0 ) 

Attaches a fresh background image to the active camera

Parameters :

- filepath ( str ) – Filepath, Path to image file (optional, never None, blend relative // prefix supported)

- relative_path ( bool ) – Relative Path, Select the file relative to the blend file (optional)

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. camera_background_image_remove ( * , index = 0 ) 

Detaches a background image from the camera

Parameters :

index ( int ) – Index, Background image index to remove (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. camera_to_view ( ) 

Aligns the camera view with the current view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. camera_to_view_selected ( ) 

Repositions the camera to frame the selected objects

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. clear_render_border ( ) 

Removes the border render boundaries and turns border render off

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. clip_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True ) 

Defines the clipping region of the view

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

bpy.ops.view3d. copybuffer ( ) 

Copies the selected objects onto the internal clipboard

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. cursor3d ( * , use_depth = True , orientation = 'VIEW' ) 

Positions the 3D cursor

Parameters :

- use_depth ( bool ) – Surface Project, Project onto the surface (optional)

- orientation ( Literal [ 'NONE' , 'VIEW' , 'XFORM' , 'GEOM' ] ) – Orientation, Preset viewpoint to use (optional)

- NONE
None – Keep the orientation as it is.

- VIEW
View – Match the viewport orientation.

- XFORM
Transform – Match the active transform setting.

- GEOM
Geometry – Follow the surface normal.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. dolly ( * , mx = 0 , my = 0 , delta = 0 , use_cursor_init = True ) 

Dollies the view in or out

Parameters :

- mx ( int ) – Region Position X, (in [0, inf], optional)

- my ( int ) – Region Position Y, (in [0, inf], optional)

- delta ( int ) – Delta, (in [-inf, inf], optional)

- use_cursor_init ( bool ) – Use Mouse Position, Allow the initial mouse position to be used (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. drop_world ( * , name = '' , session_uid = 0 ) 

Places a world into the scene

Parameters :

- name ( str ) – Name, Name of the data-block to use by the operator (optional, never None)

- session_uid ( int ) – Session UID, Session UID of the data-block to use by the operator (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. edit_mesh_extrude_individual_move ( ) 

Extrudes each face on its own along its local normal

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/view3d.py:30

bpy.ops.view3d. edit_mesh_extrude_manifold_normal ( ) 

Extrudes a manifold region along its normals

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/view3d.py:198

bpy.ops.view3d. edit_mesh_extrude_move_normal ( * , dissolve_and_intersect = False ) 

Extrudes a region as a whole along the averaged normal

Parameters :

dissolve_and_intersect ( bool ) – Dissolve and Intersect, Dissolves adjacent faces and intersects new geometry (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/view3d.py:166

bpy.ops.view3d. edit_mesh_extrude_move_shrink_fatten ( ) 

Extrudes a region as a whole along the local normals

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/view3d.py:182

bpy.ops.view3d. fly ( ) 

Lets you fly through the scene interactively

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. interactive_add ( * , primitive_type = 'CUBE' , plane_origin_base = 'EDGE' , plane_origin_depth = 'EDGE' , plane_aspect_base = 'FREE' , plane_aspect_depth = 'FREE' , wait_for_input = True ) 

Adds an object interactively

Parameters :

- primitive_type ( Literal [ 'CUBE' , 'CYLINDER' , 'CONE' , '`SPHERE_UV`' , '`SPHERE_ICO`' ] ) – Primitive, (optional)

- plane_origin_base ( Literal [ 'EDGE' , 'CENTER' ] ) – Origin, The initial position for placement (optional)

- EDGE
Edge – Begin placement from the edge position.

- CENTER
Center – Begin placement from the center position.

- plane_origin_depth ( Literal [ 'EDGE' , 'CENTER' ] ) – Origin, The initial position for placement (optional)

- EDGE
Edge – Begin placement from the edge position.

- CENTER
Center - Initiates placement of the center position.

- plane_aspect_base ( Literal [ 'FREE' , 'FIXED' ] ) - Aspect, Initial aspect ratio preference (optional)

- FREE
Free - Permits unrestricted aspect ratios.

- FIXED
Fixed - Enforces a 1:1 aspect ratio.

- plane_aspect_depth ( Literal [ 'FREE' , 'FIXED' ] ) - Aspect, Initial aspect ratio preference (optional)

- FREE
Free - Permits unrestricted aspect ratios.

- FIXED
Fixed - Enforces a 1:1 aspect ratio.

- wait_for_input ( bool ) - Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. localview ( * , frame_selected = True ) 

Isolates the display of picked object(s), centered and magnified in the viewport

Parameters :

frame_selected ( bool ) - Frame Selected, Moves the viewport to encompass the chosen objects (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. localview_remove_from ( ) 

Extracts chosen items from isolated view

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. move ( * , use_cursor_init = True ) 

Shift the view

Parameters :

use_cursor_init ( bool ) - Use Mouse Position, Permits the first mouse position as the pivot point (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. navigate ( ) 

Enables navigation through the environment using preference-driven input (walk/fly mode)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ndof_all ( ) 

Manipulate the viewport with lateral and rotational inputs via 3D input device

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ndof_orbit ( ) 

Rotate the viewport with a 3D input device

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ndof_orbit_zoom ( ) 

Rotate and magnify the viewport using a 3D input device

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ndof_pan ( ) 

Shift the viewport using a 3D input device

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. object_as_camera ( ) 

Designates the current object as the active camera for the viewport or composition

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. object_mode_pie_or_toggle ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. pastebuffer ( * , autoselect = True , active_collection = True ) 

Inserts items previously stored in the internal clipboard

Parameters :

- autoselect ( bool ) - Select, Marks inserted items as picked (optional)

- active_collection ( bool ) - Active Collection, Places inserted items in the active collection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. render_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True ) 

Defines the extent of the render region and engages border rendering

Parameters :

- xmin ( int ) - X Min, (in [-inf, inf], optional)

- xmax ( int ) - X Max, (in [-inf, inf], optional)

- ymin ( int ) - Y Min, (in [-inf, inf], optional)

- ymax ( int ) - Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) - Wait for Input, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. rotate ( * , use_cursor_init = True ) 

Orbit the viewport

Parameters :

use_cursor_init ( bool ) - Use Mouse Position, Permits the first mouse position as the pivot point (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ruler_add ( ) 

Create a measurement tool

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. ruler_remove ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. select ( * , extend = False , deselect = False , toggle = False , deselect_all = False , select_passthrough = False , center = False , enumerate = False , object = False , location = (0, 0) ) 

Highlight and make current specific item(s)

Parameters :

- extend ( bool ) - Extend, Adds to the current selection rather than clearing it beforehand (optional)

- deselect ( bool ) - Deselect, Removes from the current selection (optional)

- toggle ( bool ) - Toggle Selection, Reverses the selection state (optional)

- deselect_all ( bool ) - Deselect On Nothing, Clears all selection when the cursor points to empty space (optional)

- select_passthrough ( bool ) - Only Select Unselected, Ignores the choose action when the element is already highlighted (optional)

- center ( bool ) - Center, Uses the object's midpoint when choosing, in edit mode used to expand object selection (optional)

- enumerate ( bool ) - Enumerate, Displays items beneath the cursor (object mode only) (optional)

- object ( bool ) - Object, Uses object selection (edit mode only) (optional)

- location ( Sequence [ int ] ) - Location, Cursor position (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. select_box ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' ) 

Highlight elements via rectangular selection

Parameters :

- xmin ( int ) - X Min, (in [-inf, inf], optional)

- xmax ( int ) - X Max, (in [-inf, inf], optional)

- ymin ( int ) - Y Min, (in [-inf, inf], optional)

- ymax ( int ) - Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) - Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' , 'XOR' , 'AND' ] ) - Mode, (optional)

- SET
Set - Establishes a new selection.

- ADD
Extend - Expands the current selection.

- SUB
Subtract - Removes from the current selection.

- XOR
Difference - Reverses the selection state.

- AND
Intersect - Keeps only overlapping selections.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' ) 

Highlight elements via circular selection

Parameters :

- x ( int ) - X, (in [-inf, inf], optional)

- y ( int ) - Y, (in [-inf, inf], optional)

- radius ( int ) - Radius, (in [1, inf], optional)

- wait_for_input ( bool ) - Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) - Mode, (optional)

- SET
Set - Establishes a new selection.

- ADD
Extend - Expands the current selection.

- SUB
Subtract - Removes from the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. select_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' ) 

Highlight elements via freehand selection

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) - Path, (optional)

- use_smooth_stroke ( bool ) - Stabilize Stroke, The cursor motion lags and traces a smoother trajectory (optional)

- smooth_stroke_factor ( float ) - Smooth Stroke Factor, Higher settings produce more refined motion paths (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) - Smooth Stroke Radius, Threshold spacing from last point before selection resumes (in [10, 200], optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' , 'XOR' , 'AND' ] ) - Mode, (optional)

- SET
Set - Establishes a new selection.

- ADD
Extend - Expands the current selection.

- SUB
Subtract - Removes from the current selection.

- XOR
Difference - Reverses the selection state.

- AND
Intersect - Keeps only overlapping selections.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. select_menu ( * , name = '' , extend = False , deselect = False , toggle = False ) 

Choose an item from a dropdown menu

Parameters :

- name ( str ) - Object Name, (optional)

- extend ( bool ) - Extend, (optional)

- deselect ( bool ) - Deselect, (optional)

- toggle ( bool ) - Toggle, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. smoothview ( ) 

Undocumented, consider contributing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_cursor_to_active ( ) 

Relocates the 3D cursor to the picked item

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_cursor_to_center ( ) 

Relocates the 3D cursor to the global origin

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_cursor_to_grid ( ) 

Relocates the 3D cursor to the nearest grid intersection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_cursor_to_selected ( ) 

Relocates the 3D cursor to the midpoint of the highlighted item(s)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_selected_to_active ( ) 

Relocates highlighted item(s) to the picked item

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_selected_to_cursor ( * , use_offset = True , use_rotation = False ) 

Relocates highlighted item(s) to the 3D cursor

Parameters :

- use_offset ( bool ) - Offset, Moves the selection as a unit or each item individually by its center (optional)

- use_rotation ( bool ) - Rotation, Aligns the selection's orientation to match the cursor (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. snap_selected_to_grid ( ) 

Relocates highlighted item(s) to the nearest grid intersection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. toggle_matcap_flip ( ) 

Reverse MatCap orientation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. toggle_shading ( * , type = 'WIREFRAME' ) 

Cycles display shading in the 3D viewport

Parameters :

type ( Literal [ 'WIREFRAME' , 'SOLID' , 'MATERIAL' , 'RENDERED' ] ) - Type, Display mode to toggle (optional)

- WIREFRAME
Wireframe - Cycle wireframe display.

- SOLID
Solid - Cycle solid display.

- MATERIAL
Material Preview - Cycle material preview display.

- RENDERED
Rendered - Cycle rendered display.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. toggle_xray ( ) 

Permits visualization through all geometry for item selection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. transform_gizmo_set ( * , extend = False , type = set() ) 

Activates the specified transformation controller

Parameters :

- extend ( bool ) - Extend, (optional)

- type ( set [ Literal [ 'TRANSLATE' , 'ROTATE' , 'SCALE' ] ] ) - Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/view3d.py:245

bpy.ops.view3d. view_all ( * , use_all_regions = False , center = False ) 

Displays all geometry in the scene

Parameters :

- use_all_regions ( bool ) - All Regions, Displays the selection for all regions (optional)

- center ( bool ) - Center, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_axis ( * , type = 'LEFT' , align_active = False , relative = False ) 

Adopts a standard viewpoint configuration

Parameters :

- type ( Literal [ 'LEFT' , 'RIGHT' , 'BOTTOM' , 'TOP' , 'FRONT' , 'BACK' ] ) - View, Standard viewpoint to apply (optional)

- LEFT
Left - Perspective from the left.

- RIGHT
Right - Perspective from the right.

- BOTTOM
Bottom - Perspective from the bottom.

- TOP
Top - Perspective from the top.

- FRONT
Front - Perspective from the front.

- BACK
Back - Perspective from the back.

- align_active ( bool ) - Align Active, Orients to the active object's axes (optional)

- relative ( bool ) - Relative, Adjusts relative to the current position (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_camera ( ) 

Switches between standard and camera perspective

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_center_camera ( ) 

Positions the camera view and resizes to encompass its boundaries

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_center_cursor ( ) 

Repositions the viewport such that the cursor appears at its midpoint

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_center_lock ( ) 

Repositions the lock offset for the viewport

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_center_pick ( ) 

Positions the viewport based on the Z-depth at the cursor location

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_lock_clear ( ) 

Eliminates all viewport constraints

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_lock_to_active ( ) 

Constrains the viewport to the picked object/bone

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_orbit ( * , angle = 0.0 , type = 'ORBITLEFT' ) 

Revolves the viewport

Parameters :

- angle ( float ) - Roll, (in [-inf, inf], optional)

- type ( Literal [ 'ORBITLEFT' , 'ORBITRIGHT' , 'ORBITUP' , 'ORBITDOWN' ] ) - Orbit, Rotational direction (optional)

- ORBITLEFT
Orbit Left - Spin the viewport leftward.

- ORBITRIGHT
Orbit Right - Spin the viewport rightward.

- ORBITUP
Orbit Up - Rotate the viewport upward.

- ORBITDOWN
Orbit Down - Rotate the viewport downward.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_pan ( * , type = 'PANLEFT' ) 

Slides the view toward a specified direction

Parameters :

type ( Literal [ 'PANLEFT' , 'PANRIGHT' , 'PANUP' , 'PANDOWN' ] ) - Pan, Lateral direction (optional)

- PANLEFT
Pan Left - Shift the view leftward.

- PANRIGHT
Pan Right - Shift the view rightward.

- PANUP
Pan Up - Shift the view upward.

- PANDOWN
Pan Down - Shift the view downward.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_persportho ( ) 

Alternates between perspective and orthographic projection modes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_roll ( * , angle = 0.0 , type = 'ANGLE' ) 

Tilts the viewport

Parameters :

- angle ( float ) - Roll, (in [-inf, inf], optional)

- type ( Literal [ 'ANGLE' , 'LEFT' , 'RIGHT' ] ) - Roll Angle Source, Mechanism for computing roll rotation (optional)

- ANGLE
Roll Angle - Tilts using a supplied angle.

- LEFT
Roll Left - Tilts the viewport leftward.

- RIGHT
Roll Right - Tilts the viewport rightward.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. view_selected ( * , use_all_regions = False ) 

Repositions the viewport to the selection midpoint

Parameters :

use_all_regions ( bool ) - All Regions, Displays the selection for all regions (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. walk ( ) 

Enables interactive exploration of the scene

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. zoom ( * , mx = 0 , my = 0 , delta = 0 , use_cursor_init = True ) 

Magnifies or reduces the viewport

Parameters :

- mx ( int ) - Region Position X, (in [0, inf], optional)

- my ( int ) - Region Position Y, (in [0, inf], optional)

- delta ( int ) - Delta, (in [-inf, inf], optional)

- use_cursor_init ( bool ) - Use Mouse Position, Permits the first mouse position as the pivot point (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. zoom_border ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , zoom_out = False ) 

Magnifies the viewport to encompass the nearest item within the border

Parameters :

- xmin ( int ) - X Min, (in [-inf, inf], optional)

- xmax ( int ) - X Max, (in [-inf, inf], optional)

- ymin ( int ) - Y Min, (in [-inf, inf], optional)

- ymax ( int ) - Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) - Wait for Input, (optional)

- zoom_out ( bool ) - Zoom Out, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.view3d. zoom_camera_1_to_1 ( ) 

Synchronizes the camera with 1:1 relative to the rendering output

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

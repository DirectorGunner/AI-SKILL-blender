# Wm Operators (part 9)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- lock_location_z ( bool ) – Lock Elevation, Avert variations to watcher height (optional)

- lock_direction ( bool ) – Lock Direction, Restrict shifting to watcher's initial bearing (optional)

- speed_frame_based ( bool ) – Frame Based Speed, Implement unchanged shifting quantities every session (optional)

- turn_speed_factor ( float ) – Turn Speed Factor, Portion of the minimal and maximal pivot rate (in [0, 1], optional)

- fly_speed_factor ( float ) – Fly Speed Factor, Portion of the minimal and maximal travel rate (in [0, 1], optional)

- speed_interpolation0 (mathutils.Vector) – Speed Interpolation 0, Initial cardinal spline anchor point among minimal/maximal rates (cluster of 2 items, in [0, 1], optional)

- speed_interpolation1 (mathutils.Vector) – Speed Interpolation 1, Next cardinal spline anchor point among minimal/maximal rates (cluster of 2 items, in [0, 1], optional)

- alt_mode ( Literal [ 'FORWARD' , 'BACK' , 'LEFT' , 'RIGHT' , 'UP' , 'DOWN' , 'TURNLEFT' , 'TURNRIGHT' , '`VIEWER_FORWARD`' , '`VIEWER_BACK`' , '`VIEWER_LEFT`' , '`VIEWER_RIGHT`' , '`CONTROLLER_FORWARD`' ] ) – Mode (Alt), Flight pattern when tools are reversed (optional)

- FORWARD
Forward – Shift along pathway ahead marker.

- BACK
Back – Shift along pathway rear marker.

- LEFT
Left – Shift along pathway left marker.

- RIGHT
Right – Shift along pathway right marker.

- UP
Up – Shift along pathway upper marker.

- DOWN
Down – Shift along pathway lower marker.

- TURNLEFT
Turn Left – Pivot leftward about pathway upper marker.

- TURNRIGHT
Turn Right – Pivot rightward about pathway upper marker.

- `VIEWER_FORWARD`
Viewer Forward – Shift along watcher's ahead marker.

- `VIEWER_BACK`
Viewer Back – Shift along watcher's rear marker.

- `VIEWER_LEFT`
Viewer Left – Shift along watcher's left marker.

- `VIEWER_RIGHT`
Viewer Right – Shift along watcher's right marker.

- `CONTROLLER_FORWARD`
Controller Forward – Shift along gadget's ahead marker.

- alt_lock_location_z ( bool ) – Lock Elevation (Alt), When tools are reversed, avert variations to watcher height (optional)

- alt_lock_direction ( bool ) – Lock Direction (Alt), When tools are reversed, limit shifting to watcher's initial bearing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_navigation_grab ( * , lock_location = False , lock_location_z = False , lock_rotation = False , lock_rotation_z = False , lock_scale = False ) 

Traverse the VR setting by grabbing via tools

Parameters :

- lock_location ( bool ) – Lock Location, Avert variations to watcher location (optional)

- lock_location_z ( bool ) – Lock Elevation, Avert variations to watcher height (optional)

- lock_rotation ( bool ) – Lock Rotation, Avert variations to watcher pivot (optional)

- lock_rotation_z ( bool ) – Lock Up Orientation, Avert variations to watcher upper bearing (optional)

- lock_scale ( bool ) – Lock Scale, Avert variations to watcher dimension (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_navigation_reset ( * , location = True , rotation = True , scale = True ) 

Restore VR pathway shifts matching the session base posture

Parameters :

- location ( bool ) – Location, Restore location shifts (optional)

- rotation ( bool ) – Rotation, Restore rotation shifts (optional)

- scale ( bool ) – Scale, Restore dimension shifts (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_navigation_swap_hands ( ) 

Exchange VR pathway regulation among left / right tools

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_navigation_teleport ( * , selectable_only = True , force = 8.5 , range = 0.15 , ray_line_width = 6.0 , destination_indicator_width = 0.18 , hit_color = (0.4, 0.6, 0.9, 1.0) , miss_color = (1.0, 0.35, 0.35, 1.0) , fallback_color = (0.5, 0.45, 0.8, 1.0) ) 

Position VR watcher spot to tool ray collision area

Parameters :

- selectable_only ( bool ) – Selectable Only, Permit merely selectable things to have an impact on ray-casting output (optional)

- force ( float ) – Force, Strength push handling the shifting arc flight in m/s (in [0, inf], optional)

- range ( float ) – Range, Temporal segmentation span handling the shifting arc flight (in [0, inf], optional)

- ray_line_width ( float ) – Ray Line Width, Graphic breadth of the shifting ray direction (in [0, inf], optional)

- destination_indicator_width ( float ) – Destination Indicator Width, Graphic breadth of the impact target marker (in [0, inf], optional)

- hit_color ( Sequence [ float ] ) – Hit Color, Hue of ray-casting when it is successful (grouping of 4 items, in [0, 1], optional)

- miss_color ( Sequence [ float ] ) – Miss Color, Hue of ray-casting when it is unsuccessful (grouping of 4 items, in [0, 1], optional)

- fallback_color ( Sequence [ float ] ) – Fallback Color, Hue of ray-casting when a fallback instance is successful (grouping of 4 items, in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_session_toggle ( ) 

Show a panel for application with immersive reality equipment, or finish it if already active

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

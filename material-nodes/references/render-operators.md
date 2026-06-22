# Render Operators, Rigidbody Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Render Operators; Rigidbody Operators.

## Render Operators

### Render Operators 

bpy.ops.render. color_management_white_balance_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Create or delete a white balance preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. cycles_integrator_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Enlist an Integrator Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. cycles_performance_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Enlist a Performance Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. cycles_sampling_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Enlist a Sampling Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. cycles_viewport_sampling_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Enlist a Viewport Sampling Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. eevee_raytracing_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Create or delete an EEVEE ray-tracing preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. opengl ( * , animation = False , render_keyed_only = False , sequencer = False , write_still = False , view_context = True ) 

Grab a snapshot of the currently active viewport

Parameters :

- animation ( bool ) – Animation, Render files from the animation range of this scene (optional)

- render_keyed_only ( bool ) – Render Keyframes Only, Render only those frames where selected objects have a key in their animation data. Only used when rendering animation (optional)

- sequencer ( bool ) – Sequencer, Render using the sequencer's OpenGL display (optional)

- write_still ( bool ) – Write Image, Save the rendered image to the output path (used only when animation is disabled) (optional)

- view_context ( bool ) – View Context, Use the current 3D view for rendering, else use scene settings (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. play_rendered_anim ( ) 

Present rendered frames or sequences using an external application

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/screen_play_rendered_anim.py:87

bpy.ops.render. preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Create or delete a Render Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

bpy.ops.render. render ( * , animation = False , write_still = False , use_viewport = False , use_sequencer_scene = False , layer = '' , scene = '' , frame_start = 0 , frame_end = 0 ) 

Undocumented, consider contributing.

Parameters :

- animation ( bool ) – Animation, Render files from the animation range of this scene (optional)

- write_still ( bool ) – Write Image, Save the rendered image to the output path (used only when animation is disabled) (optional)

- use_viewport ( bool ) – Use 3D Viewport, When inside a 3D viewport, use layers and camera of the viewport (optional)

- use_sequencer_scene ( bool ) – Use Sequencer Scene, Render the sequencer scene instead of the active scene (optional)

- layer ( str ) – Render Layer, Single render layer to re-render (used only when animation is disabled) (optional, never None)

- scene ( str ) – Scene, Scene to render, current scene if not specified (optional, never None)

- frame_start ( int ) – Start Frame, Frame to start rendering animation at. If not specified, the scene start frame will be assumed. This should only be specified if doing an animation render (in [-inf, inf], optional)

- frame_end ( int ) – End Frame, Frame to end rendering animation at. If not specified, the scene end frame will be assumed. This should only be specified if doing an animation render (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. shutter_curve_preset ( * , shape = 'SMOOTH' ) 

Regulate shutter curve

Parameters :

shape ( Literal [ 'SHARP' , 'SMOOTH' , 'MAX' , 'LINE' , 'ROUND' , 'ROOT' ] ) – Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. view_cancel ( ) 

Discontinue viewing the render output

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. view_show ( ) 

Switch between showing and hiding the render output

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. view_cancel ( ) 

Discontinue viewing the render output

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.render. view_show ( ) 

Switch between showing and hiding the render output

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Rigidbody Operators

### Rigidbody Operators

bpy.ops.rigidbody. bake_to_keyframes ( * , frame_start = 1 , frame_end = 250 , step = 1 )

Records rigid body object transformations at each frame, storing them as animation keyframes

Parameters :

- frame_start ( int ) – Start Frame, Opening frame where recording begins (in [0, 300000], optional)

- frame_end ( int ) – End Frame, Closing frame where recording ends (in [1, 300000], optional)

- step ( int ) – Frame Step, Interval between recorded frames (in [1, 120], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/rigidbody.py:108

bpy.ops.rigidbody. connect ( * , con_type = 'FIXED' , pivot_type = 'CENTER' , connection_pattern = '`SELECTED_TO_ACTIVE`' )

Establish constraints linking multiple selected rigid bodies

Parameters :

- con_type ( Literal [ 'FIXED' , 'POINT' , 'HINGE' , 'SLIDER' , 'PISTON' , 'GENERIC' , '`GENERIC_SPRING`' , 'MOTOR' ] ) – Type, Relationship style between constrained bodies (optional)

- FIXED
Fixed – Glue rigid bodies together.

- POINT
Point – Constrain rigid bodies to move around common pivot point.

- HINGE
Hinge – Restrict rigid body rotation to one axis.

- SLIDER
Slider – Restrict rigid body translation to one axis.

- PISTON
Piston – Restrict rigid body translation and rotation to one axis.

- GENERIC
Generic – Restrict translation and rotation to specified axes.

- `GENERIC_SPRING`
Generic Spring – Restrict translation and rotation to specified axes with springs.

- MOTOR
Motor – Drive rigid body around or along an axis.

- pivot_type ( Literal [ 'CENTER' , 'ACTIVE' , 'SELECTED' ] ) – Location, Where the constraint pivot sits (optional)

- CENTER
Center – Pivot location is between the constrained rigid bodies.

- ACTIVE
Active – Pivot location is at the active object position.

- SELECTED
Selected – Pivot location is at the selected object position.

- connection_pattern ( Literal [ '`SELECTED_TO_ACTIVE`' , '`CHAIN_DISTANCE`' ] ) – Connection Pattern, How objects are linked to form the constraint structure (optional)

- `SELECTED_TO_ACTIVE`
Selected to Active – Connect selected objects to the active object.

- `CHAIN_DISTANCE`
Chain by Distance – Connect objects as a chain based on distance, starting at the active object.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/rigidbody.py:277

bpy.ops.rigidbody. constraint_add ( * , type = 'FIXED' )

Attach a constraint governing how the active object moves

Parameters :

type (Literal[Rigidbody Constraint Type Items]) – Rigid Body Constraint Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. constraint_remove ( )

Detach constraint settings from the object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. mass_calculate ( * , material = 'DEFAULT' , density = 1.0 )

Derive mass from volume for every selected Rigid Body, estimating based on material type

Parameters :

- material ( Literal [ 'DEFAULT' ] ) – Material Preset, Material category governing how heavy the objects behave (optional)

- density ( float ) – Density, Mass per unit volume (kg/m^3), allows custom value if the 'Custom' preset is used (in [1.17549e-38, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. object_add ( * , type = 'ACTIVE' )

Enable the current object to participate in rigid body dynamics

Parameters :

type (Literal[Rigidbody Object Type Items]) – Rigid Body Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. object_remove ( )

Disable rigid body behavior on the object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. object_settings_copy ( )

Transfer rigid body configuration from active to each selected object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/rigidbody.py:45

bpy.ops.rigidbody. objects_add ( * , type = 'ACTIVE' )

Enable selected objects to participate in rigid body dynamics

Parameters :

type (Literal[Rigidbody Object Type Items]) – Rigid Body Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. objects_remove ( )

Detach selected objects from rigid body simulation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. shape_change ( * , type = 'MESH' )

Modify collision bounds on selected Rigid Body Objects

Parameters :

type (Literal[Rigidbody Object Shape Items]) – Rigid Body Shape, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. world_add ( )

Create a physics world to govern all rigid body interactions in the scene

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.rigidbody. world_remove ( )

Disable rigid body physics governing in the scene

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

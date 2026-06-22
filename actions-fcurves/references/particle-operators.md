# Particle Operators, Pointcloud Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Particle Operators; Pointcloud Operators.

## Particle Operators

### Particle Operators 

bpy.ops.particle. brush_edit ( * , stroke = None , pen_flip = False ) 

Execute a brush stroke on the particle system

Parameters :

- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)

- pen_flip ( bool ) – Pen Flip, Whether a tablet's eraser mode is being used (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. connect_hair ( * , all = False ) 

Bind hair strands to the base mesh

Parameters :

all ( bool ) – All Hair, Connect all hair systems to the emitter mesh (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. copy_particle_systems ( * , space = 'OBJECT' , remove_target_particles = True , use_active = False ) 

Transfer particle systems from the selected active object to other chosen objects

Parameters :

- space ( Literal [ 'OBJECT' , 'WORLD' ] ) – Space, Space transform for copying from one object to another (optional)

- OBJECT
Object – Copy inside each object's local space.

- WORLD
World – Copy in world space.

- remove_target_particles ( bool ) – Remove Target Particles, Remove particle systems on the target objects (optional)

- use_active ( bool ) – Use Active, Use the active particle system from the context (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. delete ( * , type = 'PARTICLE' ) 

Discard selected particles or their keyframes

Parameters :

type ( Literal [ 'PARTICLE' , 'KEY' ] ) – Type, Delete a full particle or only keys (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. disconnect_hair ( * , all = False ) 

Unbind hair strands from the base mesh

Parameters :

all ( bool ) – All Hair, Disconnect all hair systems from the emitter mesh (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. duplicate_particle_system ( * , use_duplicate_settings = False ) 

Make a duplicate particle system within the current object

Parameters :

use_duplicate_settings ( bool ) – Duplicate Settings, Duplicate settings as well, so the new particle system uses its own settings (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. dupliob_copy ( ) 

Replicate the active instance object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. dupliob_move_down ( ) 

Shift the instance object toward the bottom of the list

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. dupliob_move_up ( ) 

Shift the instance object toward the top of the list

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. dupliob_refresh ( ) 

Update the collection of instance objects and recalculate their weights

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. dupliob_remove ( ) 

Take away the currently selected instance object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. edited_clear ( ) 

Revert all manual adjustments made to the particle system

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. hair_dynamics_preset_add ( * , name = '' , remove_name = False , remove_active = False ) 

Create or delete a Hair Dynamics Preset

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

bpy.ops.particle. hide ( * , unselected = False ) 

Conceal selected particles from view

Parameters :

unselected ( bool ) – Unselected, Hide unselected rather than selected (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. mirror ( ) 

Replicate and flip selected particles across the local X axis

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. new ( ) 

Add fresh particle properties

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. new_target ( ) 

Establish a fresh particle target

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. particle_edit_toggle ( ) 

Turn particle edit on or off

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. particle_system_remove_all ( ) 

Erase all particle systems from the current object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. rekey ( * , keys_number = 2 ) 

Adjust the count of keys on selected particles (includes root and tip)

Parameters :

keys_number ( int ) – Number of Keys, (in [2, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. remove_doubles ( * , threshold = 0.0002 ) 

Discard selected particles that are sufficiently near to other particles

Parameters :

threshold ( float ) – Merge Distance, Threshold distance within which particles are removed (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. reveal ( * , select = True ) 

Make hidden particles visible

Parameters :

select ( bool ) – Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_all ( * , action = 'TOGGLE' ) 

Switch selection state for all particles' keys

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_less ( ) 

Deselect boundary selected keys of each particle

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_linked ( ) 

Highlight all keys connected to keys that are currently selected

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_linked_pick ( * , deselect = False , location = (0, 0) ) 

Highlight the nearest particle from the cursor position

Parameters :

- deselect ( bool ) – Deselect, Deselect linked keys rather than selecting them (optional)

- location ( Sequence [ int ] ) – Location, (array of 2 items, in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_more ( ) 

Highlight keys touching boundary-selected keys of each particle

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_random ( * , ratio = 0.5 , seed = 0 , action = 'SELECT' , type = 'HAIR' ) 

Pick an arbitrary set of hair or point positions

Parameters :

- ratio ( float ) – Ratio, Portion of items to select randomly (in [0, 1], optional)

- seed ( int ) – Random Seed, Seed for the random number generator (in [0, inf], optional)

- action ( Literal [ 'SELECT' , 'DESELECT' ] ) – Action, Selection action to execute (optional)

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- type ( Literal [ 'HAIR' , 'POINTS' ] ) – Type, Select either hair or points (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_roots ( * , action = 'SELECT' ) 

Highlight the anchors of all visible particles

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. select_tips ( * , action = 'SELECT' ) 

Highlight the endpoints of all visible particles

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. shape_cut ( ) 

Shorten hair to align with the designated shape object

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. subdivide ( ) 

Split selected particles' segments (introduces keys)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. target_move_down ( ) 

Shift particle target toward the bottom of the list

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. target_move_up ( ) 

Shift particle target toward the top of the list

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. target_remove ( ) 

Take away the currently selected particle target

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. unify_length ( ) 

Set all selected hair strands to an equal length

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.particle. weight_set ( * , factor = 1.0 ) 

Assign a weight value to selected keys

Parameters :

factor ( float ) – Factor, Interpolation factor between current brush weight, and keys' weights (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Pointcloud Operators

### Pointcloud Operators 

bpy.ops.pointcloud. attribute_set ( * , value_float = 0.0 , value_float_vector_2d = (0.0, 0.0) , value_float_vector_3d = (0.0, 0.0, 0.0) , value_int = 0 , value_int_vector_2d = (0, 0) , value_color = (1.0, 1.0, 1.0, 1.0) , value_bool = False ) 

Populate the active attribute for chosen elements with given values

Parameters :

- value_float ( float ) – Value, (in [-inf, inf], optional)

- value_float_vector_2d ( Sequence [ float ] ) – Value, (array of 2 items, in [-inf, inf], optional)

- value_float_vector_3d ( Sequence [ float ] ) – Value, (array of 3 items, in [-inf, inf], optional)

- value_int ( int ) – Value, (in [-inf, inf], optional)

- value_int_vector_2d ( Sequence [ int ] ) – Value, (array of 2 items, in [-inf, inf], optional)

- value_color ( Sequence [ float ] ) – Value, (array of 4 items, in [-inf, inf], optional)

- value_bool ( bool ) – Value, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. delete ( ) 

Erase selected points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. duplicate ( ) 

Replicate selected points

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. duplicate_move ( * , `POINTCLOUD_OT`_duplicate = {} , `TRANSFORM_OT`_translate = {} ) 

Duplicate selected elements and shift them

Parameters :

- `POINTCLOUD_OT`_duplicate ( dict [ str , Any ] ) – Duplicate, Copy selected points (optional, bpy.ops.pointcloud.duplicate() keyword arguments)

- `TRANSFORM_OT`_translate ( dict [ str , Any ] ) – Move, Move selected items (optional, bpy.ops.transform.translate() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. select_all ( * , action = 'TOGGLE' ) 

Switch selection state for all points

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Toggle selection for all elements.

- SELECT
Select – Select all elements.

- DESELECT
Deselect – Deselect all elements.

- INVERT
Invert – Invert selection of all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. select_random ( * , seed = 0 , probability = 0.5 ) 

Shuffle the current selection or generate a fresh random selection

Parameters :

- seed ( int ) – Seed, Source of randomness (in [-inf, inf], optional)

- probability ( float ) – Probability, Chance of every point being included in the selection (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.pointcloud. separate ( ) 

Partition selected geometry into a standalone point cloud

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

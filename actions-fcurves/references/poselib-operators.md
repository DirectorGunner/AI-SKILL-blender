# Poselib Operators, Sculpt Curves Operators

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Poselib Operators; Sculpt Curves Operators.

## Poselib Operators

### Poselib Operators 

bpy.ops.poselib. apply_pose_asset ( * , asset_library_type = 'LOCAL' , asset_library_identifier = '' , relative_asset_identifier = '' , blend_factor = 1.0 , flipped = False ) 

Impose the provided Pose Action onto the rig

Parameters :

- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)

- asset_library_identifier ( str ) – Asset Library Identifier, (optional, never None)

- relative_asset_identifier ( str ) – Relative Asset Identifier, (optional, never None)

- blend_factor ( float ) – Blend Factor, Amount that the pose is applied on top of the existing poses. A negative value will subtract the pose instead of adding it (in [-inf, inf], optional)

- flipped ( bool ) – Apply Flipped, When enabled, applies the pose flipped over the X-axis (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.poselib. asset_delete ( ) 

Discard the chosen Pose Asset

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.poselib. asset_modify ( * , mode = 'ADJUST' ) 

Refresh the chosen pose asset in the library from the presently selected bones. The mode determines what portion of the asset is refreshed

Parameters :

mode ( Literal [ 'ADJUST' , 'REPLACE' , 'ADD' , 'REMOVE' ] ) – Overwrite Mode, Specify which parts of the pose asset are overwritten (optional)

- ADJUST
Adjust – Update existing channels in the pose asset but don't remove or add any channels.

- REPLACE
Replace with Selection – Completely replace all channels in the pose asset with the current selection.

- ADD
Add Selected Bones – Add channels of the selection to the pose asset. Existing channels will be updated.

- REMOVE
Remove Selected Bones – Remove channels of the selection from the pose asset.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.poselib. blend_pose_asset ( * , asset_library_type = 'LOCAL' , asset_library_identifier = '' , relative_asset_identifier = '' , blend_factor = 0.0 , flipped = False , release_confirm = False ) 

Mix the provided Pose Action with the rig's current configuration

Parameters :

- asset_library_type (Literal[Asset Library Type Items]) – Asset Library Type, (optional)

- asset_library_identifier ( str ) – Asset Library Identifier, (optional, never None)

- relative_asset_identifier ( str ) – Relative Asset Identifier, (optional, never None)

- blend_factor ( float ) – Blend Factor, Amount that the pose is applied on top of the existing poses. A negative value will subtract the pose instead of adding it (in [-inf, inf], optional)

- flipped ( bool ) – Apply Flipped, When enabled, applies the pose flipped over the X-axis (optional)

- release_confirm ( bool ) – Confirm on Release, Always confirm operation when releasing button (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.poselib. copy_as_asset ( ) 

Form a fresh pose asset in the clipboard, prepared for insertion into an Asset Browser

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/pose_library/operators.py:116

bpy.ops.poselib. create_pose_asset ( * , pose_name = '' , asset_library_reference = '' , catalog_path = '' ) 

Construct a fresh asset from the presently selected bones in the environment

Parameters :

- pose_name ( str ) – Pose Name, Name for the new pose asset (optional, never None)

- asset_library_reference ( str ) – Library, Asset library used to store the new pose (optional)

- catalog_path ( str ) – Catalog, Catalog to use for the new asset (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.poselib. paste_asset ( ) 

Put the Asset that was previously retained using Copy As Asset

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/pose_library/operators.py:190

bpy.ops.poselib. pose_asset_select_bones ( * , select = True , flipped = False ) 

Highlight the bones that are engaged in this pose

Parameters :

- select ( bool ) – Select, (optional)

- flipped ( bool ) – Flipped, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/pose_library/operators.py:228

bpy.ops.poselib. restore_previous_action ( ) 

Return to the previously active Action, after making a pose asset

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

addons_core/pose_library/operators.py:65

## Sculpt Curves Operators

### Sculpt Curves Operators

bpy.ops.sculpt_curves. brush_stroke ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False )

Form curves using a tool

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

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt_curves. min_distance_edit ( )

Modify the spacing setting of the density brush

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt_curves. select_grow ( * , distance = 0.1 )

Highlight curves positioned near curves currently highlighted

Parameters :

distance ( float ) – Distance, By how much to grow the selection (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.sculpt_curves. select_random ( * , seed = 0 , partial = False , probability = 0.5 , min = 0.0 , constant_per_curve = True )

Vary the existing selection or establish a new random one

Parameters :

- seed ( int ) – Seed, Randomness origin (in [-inf, inf], optional)

- partial ( bool ) – Partial, Permit control points or curves to be partially selected (optional)

- probability ( float ) – Probability, Likelihood of every control point or curve being included (in [0, 1], optional)

- min ( float ) – Min, Lower threshold for the random selection (in [0, 1], optional)

- constant_per_curve ( bool ) – Constant per Curve, The generated random value applies uniformly to all control points of a curve (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

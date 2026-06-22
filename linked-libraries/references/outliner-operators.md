# Outliner Operators

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Outliner Operators 

bpy.ops.outliner. action_set ( * , action = '' ) 

Shift the working activity in use

Parameters :

action ( str ) – Action, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. animdata_operation ( * , type = '`CLEAR_ANIMDATA`' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ '`CLEAR_ANIMDATA`' , '`SET_ACT`' , '`CLEAR_ACT`' , '`REFRESH_DRIVERS`' , '`CLEAR_DRIVERS`' ] ) – Animation Operation, (optional)

- `CLEAR_ANIMDATA`
Clear Animation Data – Strip this animation information holder.

- `SET_ACT`
Set Action.

- `CLEAR_ACT`
Unlink Action.

- `REFRESH_DRIVERS`
Refresh Drivers.

- `CLEAR_DRIVERS`
Clear Drivers.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. clear_filter ( ) 

Wipe out the inquiry limitation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_color_tag_set ( * , color = 'NONE' ) 

Implement a pigment marking for the chosen hierarchies

Parameters :

color (Literal[Collection Color Items]) – Color Tag, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_disable ( ) 

Switch off viewport rendering in the display tiers

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_disable_render ( ) 

Prevent rendering of this hierarchy

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_drop ( ) 

Move utilizing drag to position to hierarchy in Outliner

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_duplicate ( ) 

Iteratively reproduce the hierarchy, every subordinate entities, items and item information

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_duplicate_linked ( ) 

Iteratively reproduce the hierarchy, every subordinate entities and items, with transferred item information

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_enable ( ) 

Activate viewport rendering in the display tiers

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_enable_render ( ) 

Bring the hierarchy into rendering

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_exclude_clear ( ) 

Incorporate hierarchy in the operating display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_exclude_set ( ) 

Leave out hierarchy from the operating display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_hide ( ) 

Conceal the hierarchy in this display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_hide_inside ( ) 

Conceal every items and hierarchies enclosed in the hierarchy

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_hierarchy_delete ( ) 

Discard chosen hierarchy pathways

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_holdout_clear ( ) 

Lift masking of hierarchy in the operating display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_holdout_set ( ) 

Implement masking of hierarchy in the operating display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_indirect_only_clear ( ) 

Lift the hierarchy providing just marginally in the display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_indirect_only_set ( ) 

Establish hierarchy to apply just marginally (by means of shadows and reflectivity) in the display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_instance ( ) 

Exemplify chosen hierarchies to operating setting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_isolate ( * , extend = False ) 

Conceal every except this hierarchy and its forbears

Parameters :

extend ( bool ) – Extend, Prolong present obvious hierarchies (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_link ( ) 

Attach chosen hierarchies to operating setting

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_new ( * , nested = True ) 

Introduce a fresh hierarchy inside chosen hierarchy

Parameters :

nested ( bool ) – Nested, Introduce as offspring of chosen hierarchy (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_objects_deselect ( ) 

Unselect items in hierarchy

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_objects_select ( ) 

Opt for items in hierarchy

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_show ( ) 

Expose the hierarchy in this display tier

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. collection_show_inside ( ) 

Expose every items and hierarchies enclosed in the hierarchy

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. constraint_operation ( * , type = 'ENABLE' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ 'ENABLE' , 'DISABLE' , 'DELETE' ] ) – Constraint Operation, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. data_operation ( * , type = 'DEFAULT' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ 'DEFAULT' ] ) – Data Operation, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. datastack_drop ( ) 

Mirror or rearrange modifiers, limitations, and outcomes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. delete ( * , hierarchy = False ) 

Discard chosen items and hierarchies

Parameters :

hierarchy ( bool ) – Hierarchy, Discard offspring items and hierarchies (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. drivers_add_selected ( ) 

Introduce motivations to chosen pieces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. drivers_delete_selected ( )

Erase motivations delegated to chosen pieces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. expanded_toggle ( ) 

Unfold/Collapse every pieces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. hide ( ) 

Conceal chosen items and hierarchies

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. highlight_update ( ) 

Refresh the piece marker dependent on the existing cursor situation

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_copy ( ) 

Duplicate the chosen information-blocks to the internal storage

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_delete ( ) 

Discard the identification below cursor

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_linked_relocate ( ) 

Exchange the operating transmitted identification (and its connections if present) by alternate, coming from matching or differing vault

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_operation ( * , type = 'UNLINK' ) 

Standard information-block handling operations

Parameters :

type ( Literal [ 'UNLINK' , 'LOCAL' , 'SINGLE' , 'DELETE' , 'REMAP' , 'COPY' , 'PASTE' , '`ADD_FAKE`' , '`CLEAR_FAKE`' , 'RENAME' , '`SELECT_LINKED`' ] ) – ID Data Operation, (optional)

- UNLINK
Unlink.

- LOCAL
Make Local.

- SINGLE
Make Single User.

- DELETE
Delete.

- REMAP
Remap Users – Redirect every holders of chosen information-blocks to employ the alternative (tapped) unit.

- COPY
Copy.

- PASTE
Paste.

- `ADD_FAKE`
Add Fake User – Safeguard information-block acquires kept regardless if it's inactive (e.g. for movement and fabric reserves).

- `CLEAR_FAKE`
Clear Fake User.

- RENAME
Rename.

- `SELECT_LINKED`
Select Linked.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_paste ( ) 

Insert information-blocks from the interior storage

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. id_remap ( * , id_type = 'OBJECT' , old_id = 0 , new_id = 0 ) 

Undocumented, consider contributing.

Parameters :

- id_type (Literal[Id Type Items]) – ID Type, (optional)

- old_id ( int ) – Old ID, Previous ID's conference designation to shift information from (in [-inf, inf], optional)

- new_id ( int ) – New ID, Updated ID's conference designation to shift every chosen IDs' holders to (in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. item_activate ( * , extend = False , extend_range = False , deselect_all = False , recurse = False ) 

Regulate pointer clicks to opt for and trigger pieces

Parameters :

- extend ( bool ) – Extend, Broaden choosing for triggering (optional)

- extend_range ( bool ) – Extend Range, Opt for a progression from energized component (optional)

- deselect_all ( bool ) – Deselect On Nothing, Unselect every when zilch below the cursor (optional)

- recurse ( bool ) – Recurse, Opt for items cyclically from energized component (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. item_drag_drop ( ) 

Shift and plop component to alternate spot

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. item_openclose ( * , all = False ) 

Change if component below cursor becomes available or shut

Parameters :

all ( bool ) – All, Shut or unfold every pieces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. item_rename ( * , use_active = False ) 

Alter the designation of the energized component

Parameters :

use_active ( bool ) – Use Active, Alter the designation of the energized piece, rather than the one the pointer is throughout (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. keyingset_add_selected ( ) 

Introduce chosen pieces (azure-beige rows) to operating Keying Reservoir

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. keyingset_remove_selected ( ) 

Erase chosen pieces (azure-beige rows) from operating Keying Reservoir

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. lib_operation ( * , type = 'DELETE' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ 'DELETE' , 'RELOCATE' , 'RELOAD' ] ) – Library Operation, (optional)

- DELETE
Delete – Discard this vault and every its pieces.

- RELOCATE
Relocate – Opt for a fresh route for this vault, and pull every its information.

- RELOAD
Reload – Pull every information from this vault.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. lib_relocate ( ) 

Reposition the vault below cursor

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. liboverride_operation ( * , type = '`OVERRIDE_LIBRARY_CREATE_HIERARCHY`' , selection_set = 'SELECTED' ) 

Establish, restart or drop vault modification pathways

Parameters :

- type ( Literal [ '`OVERRIDE_LIBRARY_CREATE_HIERARCHY`' , '`OVERRIDE_LIBRARY_RESET`' , '`OVERRIDE_LIBRARY_CLEAR_SINGLE`' ] ) – Library Override Operation, (optional)

- `OVERRIDE_LIBRARY_CREATE_HIERARCHY`
Make – Establish a household alteration of the chosen transmitted information-blocks, and their progression of connections.

- `OVERRIDE_LIBRARY_RESET`
Reset – Restore the chosen household adjustments to their transmitted references quantities.

- `OVERRIDE_LIBRARY_CLEAR_SINGLE`
Clear – Erase the chosen household adjustments and relink their employments to the transmitted information-blocks when feasible, or else restart them and indicate them as non alterable.

- selection_set ( Literal [ 'SELECTED' , 'CONTENT' , '`SELECTED_AND_CONTENT`' ] ) – Selection Set, Throughout which portion of the arrangement pieces to implement the operation (optional)

- SELECTED
Selected – Execute the operation throughout chosen information-blocks merely.

- CONTENT
Content – Execute the operation throughout substance of the chosen pieces merely (the information-blocks in their sub-pathway).

- `SELECTED_AND_CONTENT`
Selected & Content – Execute the operation throughout chosen information-blocks and every their connections.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. liboverride_troubleshoot_operation ( * , type = '`OVERRIDE_LIBRARY_RESYNC_HIERARCHY`' , selection_set = 'SELECTED' )

Sophisticated operations throughout vault modification to facilitate fix harmed pathways

Parameters :

- type ( Literal [ '`OVERRIDE_LIBRARY_RESYNC_HIERARCHY`' , '`OVERRIDE_LIBRARY_RESYNC_HIERARCHY_ENFORCE`' , '`OVERRIDE_LIBRARY_DELETE_HIERARCHY`' ] ) – Library Override Troubleshoot Operation, (optional)

- `OVERRIDE_LIBRARY_RESYNC_HIERARCHY`
Resync – Rebuild the chosen household adjustments from their transmitted references, with their progressions of connections.

- `OVERRIDE_LIBRARY_RESYNC_HIERARCHY_ENFORCE`
Resync Enforce – Rebuild the chosen household adjustments from their transmitted references, with their progressions of connections, compelling these progressions to correspond to the transmitted information (specifically overlooking persisting adjustments on information-block indicator attributes).

- `OVERRIDE_LIBRARY_DELETE_HIERARCHY`
Delete – Erase the chosen household adjustments (plus their progressions of modification connections) and relink their employments to the transmitted information-blocks.

- selection_set ( Literal [ 'SELECTED' , 'CONTENT' , '`SELECTED_AND_CONTENT`' ] ) – Selection Set, Throughout which portion of the arrangement pieces to implement the operation (optional)

- SELECTED
Selected – Execute the operation throughout chosen information-blocks merely.

- CONTENT
Content – Execute the operation throughout substance of the chosen pieces merely (the information-blocks in their sub-pathway).

- `SELECTED_AND_CONTENT`
Selected & Content – Execute the operation throughout chosen information-blocks and every their connections.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. material_drop ( ) 

Shift substance to item in Outliner

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. modifier_operation ( * , type = 'APPLY' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ 'APPLY' , 'DELETE' , 'TOGVIS' , 'TOGREN' ] ) – Modifier Operation, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. object_operation ( * , type = 'SELECT' ) 

Undocumented, consider contributing.

Parameters :

type ( Literal [ 'SELECT' , 'DESELECT' , '`SELECT_HIERARCHY`' , 'REMAP' , 'RENAME' ] ) – Object Operation, (optional)

- SELECT
Select.

- DESELECT
Deselect.

- `SELECT_HIERARCHY`
Select Hierarchy.

- REMAP
Remap Users – Redirect every holders of chosen information-blocks to utilize a fresh opted choice.

- RENAME
Rename.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. operation ( ) 

Sidebar for piece operations

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. orphans_manage ( ) 

Open a spot to supervise unutilized information

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. orphans_purge ( * , do_local_ids = True , do_linked_ids = True , do_recursive = True ) 

Erase every unoccupied information-blocks devoid of every holders from the record

Parameters :

- do_local_ids ( bool ) – Local Data-blocks, Comprise unused domestic information-blocks into annihilation (optional)

- do_linked_ids ( bool ) – Linked Data-blocks, Comprise unused transmitted information-blocks into annihilation (optional)

- do_recursive ( bool ) – Recursive Delete, Cyclically examine for obliquely unused information-blocks, verifying that no unoccupied information-blocks stay following execution (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. parent_clear ( ) 

Shift to erase forbear in Outliner

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. parent_drop ( ) 

Shift to forbear in Outliner

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. scene_drop ( ) 

Shift item to setting in Outliner

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. scene_operation ( * , type = 'DELETE' ) 

Sidebar for setting operations

Parameters :

type ( Literal [ 'DELETE' ] ) – Scene Operation, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. scroll_page ( * , up = False ) 

Flip sheet elevated or downward

Parameters :

up ( bool ) – Up, Flip sheet upward single division (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. select_all ( * , action = 'TOGGLE' ) 

Flip the Outliner choosing of pieces

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Choosing activity to execute (optional)

- TOGGLE
Toggle – Flip choosing for every components.

- SELECT
Select – Opt for every components.

- DESELECT
Deselect – Unselect every components.

- INVERT
Invert – Invert choosing of every components.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. select_box ( * , tweak = False , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' ) 

Employ rectangle choosing to opt for arrangement components

Parameters :

- tweak ( bool ) – Tweak, Tweak motion from unoccupied room for rectangle choosing (optional)

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Put a refreshed choosing.

- ADD
Extend – Broaden persisting choosing.

- SUB
Subtract – Deduct persisting choosing.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. select_walk ( * , direction = 'UP' , extend = False , toggle_all = False ) 

Employ trekking navigation to opt for arrangement components

Parameters :

- direction ( Literal [ 'UP' , 'DOWN' , 'LEFT' , 'RIGHT' ] ) – Walk Direction, Opt for/Unselect component in this orientation (optional)

- extend ( bool ) – Extend, Broaden choosing on trekking (optional)

- toggle_all ( bool ) – Toggle All, Flip available/shut arrangement (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. show_active ( ) 

Accessible the pathway and modify the observation enabling the operating item is proven centralized

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. show_hierarchy ( ) 

Accessible every item registrations and shut every additional

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. show_one_level ( * , open = True ) 

Broaden/curtail every registrations by sole depth

Parameters :

open ( bool ) – Open, Broaden every registrations sole depth deep (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. start_filter ( ) 

Initiate entering sieve writing

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.outliner. unhide_all ( ) 

Expose every items and hierarchies

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

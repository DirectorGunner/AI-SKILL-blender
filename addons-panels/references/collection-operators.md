# Collection Operators, Extensions Operators, Fluid Operators, Gpencil Operators ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Collection Operators; Extensions Operators; Fluid Operators; Gpencil Operators; Import Curve Operators; Paintcurve Operators; Ptcache Operators.

## Collection Operators

### Collection Operators

bpy.ops.collection. create ( * , name = '' )

Assemble a group from the chosen entities

Parameters :

name ( str ) – Name, Name of the new collection (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. export_all ( )

Execute every configured writer on this group

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. exporter_add ( * , name = '' )

Register a writer to the writer catalog

Parameters :

name ( str ) – Name, FileHandler idname (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. exporter_export ( * , index = 0 )

Launch the output procedure

Parameters :

index ( int ) – Index, Exporter index (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. exporter_move ( * , direction = 'UP' )

Shift a writer higher or lower in the writer catalog

Parameters :

direction ( Literal [ 'UP' , 'DOWN' ] ) – Direction, Direction to move the active exporter (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. exporter_remove ( * , index = 0 )

Unregister a writer from the writer catalog

Parameters :

index ( int ) – Index, Exporter index (in [0, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. objects_add_active ( * , collection = '' )

Enroll selected entities in one of the groups the highlighted-entity participates in. Optionally enroll in "All Collections" to verify selected entities join the same groups as the highlighted entity

Parameters :

collection ( str ) – Collection, The collection to add other selected objects to (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. objects_remove ( * , collection = '' )

Exclude selected entities from a collection

Parameters :

collection ( str ) – Collection, The collection to remove this object from (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. objects_remove_active ( * , collection = '' )

Withdraw the entity from an entity group that includes the highlighted entity

Parameters :

collection ( str ) – Collection, The collection to remove other selected objects from (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.collection. objects_remove_all ( )

Exclude selected entities from every collection

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Extensions Operators

### Extensions Operators

bpy.ops.extensions.package_disable()

Switch off the extension

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.extensions.package_install(*, repo_directory='', repo_index=-1, pkg_id='', enable_on_install=True, url='', do_legacy_replace=False)

Retrieve and set up an extension from the web

Parameters:

- repo_directory (str) – Repo Directory, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)
- pkg_id (str) – Package ID, (optional, never None)
- enable_on_install (bool) – Enable on Install, Activate once set up completes (optional)
- url (str) – URL, (optional, never None)
- do_legacy_replace (bool) – Do Legacy Replace, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.package_install_files(*, filter_glob='*.zip;*.py', directory='', files=None, filepath='', repo='', enable_on_install=True, target='', overwrite=True, url='')

Install extension bundles from your disk into a user-managed source

Parameters:

- filter_glob (str) – filter_glob, (optional, never None)
- directory (str) – Directory, (optional, never None)
- files (bpy_prop_collection[OperatorFileListElement]) – files, (optional)
- filepath (str) – filepath, (optional, never None)
- repo (str) – User Repository, Deposit into this user-controlled source (optional)
- enable_on_install (bool) – Enable on Install, Activate once set up finishes (optional)
- target (str) – Legacy Target Path, Destination for legacy add-on package installation (optional)
- overwrite (bool) – Legacy Overwrite, Purge current add-ons using the matching ID (optional)
- url (str) – URL, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.package_install_marked(*, enable_on_install=True)

Undocumented, consider contributing.

Parameters:

enable_on_install (bool) – Enable on Install, Activate once set up finishes (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.package_mark_clear(*, pkg_id='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3680

bpy.ops.extensions.package_mark_clear_all()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3727

bpy.ops.extensions.package_mark_set(*, pkg_id='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3666

bpy.ops.extensions.package_mark_set_all()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3691

bpy.ops.extensions.package_obsolete_marked()

Clears extension versioning, handy for build testing before rollout

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3784

bpy.ops.extensions.package_show_clear(*, pkg_id='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3753

bpy.ops.extensions.package_show_set(*, pkg_id='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3739

bpy.ops.extensions.package_show_settings(*, pkg_id='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3767

bpy.ops.extensions.package_theme_disable(*, pkg_id='', repo_index=-1)

Switch the active theme back to factory default

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3621

bpy.ops.extensions.package_theme_enable(*, pkg_id='', repo_index=-1)

Make this custom theme active

Parameters:

- pkg_id (str) – Package ID, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3607

bpy.ops.extensions.package_uninstall(*, repo_directory='', repo_index=-1, pkg_id='')

Switch off and purge the extension

Parameters:

- repo_directory (str) – Repo Directory, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)
- pkg_id (str) – Package ID, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.package_uninstall_marked()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.package_uninstall_system()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3584

bpy.ops.extensions.package_upgrade_all(*, use_active_only=False)

Fetch updated extension versions from the configured remote sources

Parameters:

use_active_only (bool) – Active Only, Refresh only the chosen source (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.repo_enable_from_drop(*, repo_index=-1)

Undocumented, consider contributing.

Parameters:

repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1835

bpy.ops.extensions.repo_lock_all()

Establish file-system locking on sources - for build & debug use

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3853

bpy.ops.extensions.repo_refresh_all(*, use_active_only=False)

Sync extension & legacy add-ons by dumping and re-importing code & metadata (akin to reboot)

Parameters:

use_active_only (bool) – Active Only, Refresh only the chosen source (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1744

bpy.ops.extensions.repo_sync(*, repo_directory='', repo_index=-1)

Undocumented, consider contributing.

Parameters:

- repo_directory (str) – Repo Directory, (optional, never None)
- repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.repo_sync_all(*, use_active_only=False)

Fetch the current catalog of extension packages from all active remote sources

Parameters:

use_active_only (bool) – Active Only, Refresh only the chosen source (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1502

bpy.ops.extensions.repo_unlock()

Clear repository file-system lock

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1922

bpy.ops.extensions.repo_unlock_all()

Lift file-system locking on sources - for build & debug use

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3879

bpy.ops.extensions.status_clear()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3652

bpy.ops.extensions.status_clear_errors()

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3641

bpy.ops.extensions.userpref_allow_online()

Grant web connectivity capability. Blender gains ability to reach manually configured remote source catalogs. Included third party modules may employ the web for their own needs

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:4004

bpy.ops.extensions.userpref_allow_online_popup()

Grant web connectivity capability. Blender gains ability to reach manually configured remote source catalogs. Included third party modules may employ the web for their own needs

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:4018

bpy.ops.extensions.userpref_show_for_update()

Bring up extensions settings

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3944

bpy.ops.extensions.userpref_show_online()

Launch machine configuration "Network" section to permit web connectivity

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3984

bpy.ops.extensions.userpref_tags_set(*, value=False, data_path='')

Control the state of every tag

Parameters:

- value (bool) – Value, Flip all tags between on and off (optional)
- data_path (str) – Data Path, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3913

## Fluid Operators

### Fluid Operators

bpy.ops.fluid.bake_all()

Compute the Entire Fluid Movement

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.bake_data()

Compute Fluid Content

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.bake_guides()

Compute Fluid Steering

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.bake_mesh()

Compute Fluid Outline

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.bake_noise()

Compute Fluid Detail

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.bake_particles()

Compute Fluid Droplets

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_all()

Wipe the Entire Fluid Movement

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_data()

Wipe Fluid Content

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_guides()

Wipe Fluid Steering

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_mesh()

Wipe Fluid Outline

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_noise()

Wipe Fluid Detail

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.free_particles()

Wipe Fluid Droplets

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.pause_bake()

Stop Computation

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.fluid.preset_add(*, name='', remove_name=False, remove_active=False)

Insert or erase a Fluid Setup

Parameters:

- name (str) – Name, Label of the preset, utilized for the route label (optional, never None)
- remove_name (bool) – remove_name, (optional)
- remove_active (bool) – remove_active, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

startup/bl_operators/presets.py:119

## Gpencil Operators

### Gpencil Operators

bpy.ops.gpencil.annotate(*, mode='DRAW', arrowstyle_start='NONE', arrowstyle_end='NONE', use_stabilizer=False, stabilizer_factor=0.75, stabilizer_radius=35, stroke=None, wait_for_input=True)

Place sketches upon the present work

Parameters:

- mode (Literal['DRAW', '`DRAW_STRAIGHT`', '`DRAW_POLY`', 'ERASER']) – Mode, Technique to read cursor motions (optional)

- DRAW
Draw Freehand – Sketch unguided movements.

- `DRAW_STRAIGHT`
Draw Straight Lines – Sketch direct line divisions.

- `DRAW_POLY`
Draw Poly Line – Click to place finish marks of straight divisions (chained).

- ERASER
Eraser – Wipe Sketch marks.

- arrowstyle_start (Literal['NONE', 'ARROW', '`ARROW_OPEN`', '`ARROW_OPEN_INVERTED`', 'DIAMOND']) – Start Arrow Style, Sketch initiate form (optional)

- NONE
None – Avoid arrow/symbol in corner.

- ARROW
Arrow – Employ closed arrow form.

- `ARROW_OPEN`
Open Arrow – Employ open arrow form.

- `ARROW_OPEN_INVERTED`
Segment – Employ orthogonal split form.

- DIAMOND
Square – Employ squared form.

- arrowstyle_end (Literal['NONE', 'ARROW', '`ARROW_OPEN`', '`ARROW_OPEN_INVERTED`', 'DIAMOND']) – End Arrow Style, Sketch finish form (optional)

- NONE
None – Avoid arrow/symbol in corner.

- ARROW
Arrow – Employ closed arrow form.

- `ARROW_OPEN`
Open Arrow – Employ open arrow form.

- `ARROW_OPEN_INVERTED`
Segment – Employ orthogonal split form.

- DIAMOND
Square – Employ squared form.

- use_stabilizer (bool) – Stabilize Stroke, Instrument to pull even and refined strokes. Hit Shift to get backward consequence (even if this choice is dormant) (optional)

- stabilizer_factor (float) – Stabilizer Stroke Factor, Taller amounts yield sleeker strokes (in [0, 1], optional)

- stabilizer_radius (int) – Stabilizer Stroke Radius, Least separation from final point prior to mark persists (in [0, 200], optional)

- stroke (bpy_prop_collection[OperatorStrokeElement]) – Stroke, (optional)

- wait_for_input (bool) – Wait for Input, Hold back before starting to paint (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.annotation_active_frame_delete()

Purge the live phase for the energized Sketch Sheet

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.annotation_add()

Build a fresh Sketch collection

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.data_unlink()

Sever active Sketch collection

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.layer_annotation_add()

Build a fresh Sketch sheet or remark for the living collection

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.layer_annotation_move(*, type='UP')

Shift the live Sketch sheet up or down the listing

Parameters:

type (Literal['UP', 'DOWN']) – Type, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

bpy.ops.gpencil.layer_annotation_remove()

Purge the live Sketch sheet

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

## Import Curve Operators

### Import Curve Operators

bpy.ops.import_curve. svg ( * , filepath = '' , filter_glob = '*.svg' , directory = '' , files = None )

Load a SVG file

Parameters :

- filepath ( str ) – File Path, Filepath used for importing the file (optional, never None)

- filter_glob ( str ) – filter_glob, (optional, never None)

- directory ( str ) – directory, (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – File Path, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Paintcurve Operators

### Paintcurve Operators 

bpy.ops.paintcurve. add_point ( * , location = (0, 0) ) 

Insert a fresh Paint Curve anchor point

Parameters :

location ( Sequence [ int ] ) – Location, Location of vertex in area space (array of 2 items, in [0, 32767], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. add_point_slide ( * , `PAINTCURVE_OT`_add_point = {} , `PAINTCURVE_OT`_slide = {} ) 

Create a fresh curve point and immediately shift it

Parameters :

- `PAINTCURVE_OT`_add_point ( dict [ str , Any ] ) – Add New Paint Curve Point, Add New Paint Curve Point (optional, bpy.ops.paintcurve.add_point() keyword arguments)

- `PAINTCURVE_OT`_slide ( dict [ str , Any ] ) – Slide Paint Curve Point, Select and slide paint curve point (optional, bpy.ops.paintcurve.slide() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. cursor ( ) 

Reposition cursor

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. delete_point ( ) 

Erase a Paint Curve point

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. draw ( ) 

Render the curve

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. new ( ) 

Create a paint curve instance

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. select ( * , location = (0, 0) , toggle = False , extend = False ) 

Highlight a point on the paint curve

Parameters :

- location ( Sequence [ int ] ) – Location, Location of vertex in area space (array of 2 items, in [0, 32767], optional)

- toggle ( bool ) – Toggle, (De)select all (optional)

- extend ( bool ) – Extend, Extend selection (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paintcurve. slide ( * , align = False , select = True ) 

Choose and reposition a paint curve point

Parameters :

- align ( bool ) – Align Handles, Aligns opposite point handle during transform (optional)

- select ( bool ) – Select, Attempt to select a point handle before transform (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Ptcache Operators

### Ptcache Operators 

bpy.ops.ptcache. add ( ) 

Establish a new cache

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. bake ( * , bake = False ) 

Compute physics simulation

Parameters :

bake ( bool ) – Bake, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. bake_all ( * , bake = True ) 

Compute all physics simulations

Parameters :

bake ( bool ) – Bake, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. bake_from_cache ( ) 

Compute from saved cache

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. free_bake ( ) 

Erase computed physics data

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. free_bake_all ( ) 

Remove all precomputed simulations of all objects in the active scene

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.ptcache. remove ( ) 

Erase the active cache

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

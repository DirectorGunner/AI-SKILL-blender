# Application Data Bpy App, Action Operators

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Application Data (bpy.app); Action Operators.

## Application Data (bpy.app)

### Application Data (bpy.app)
This module contains application values that stay unchanged during runtime.

bpy.app. autoexec_fail
Boolean, True when auto-execution of scripts failed (read-only).
Type: bool

bpy.app. autoexec_fail_message
String, a message describing the auto-execution failure (read-only).
Type: str

bpy.app. autoexec_fail_quiet
Boolean, True when an auto-execution failure should be quiet, set after the warning has shown once for the current blend file (read-only).
Type: bool

bpy.app. binary_path
The location of Blender's executable, handy for utilities that open new instances. Read-only unless Blender is built as a Python module — in that case it's an empty string that script authors may point at a Blender binary.
Type: str

bpy.app. cachedir
String, the cache directory Blender uses (read-only). Returns None if the parent of the cache folder (the non-Blender-specific part of the path) doesn't exist.
Type: str | None

bpy.app. debug
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph_build
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph_eval
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph_pretty
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph_tag
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_depsgraph_time
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_events
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_freestyle
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_handlers
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_io
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_python
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_simdata
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. debug_value
An integer that can be set to non-zero values for testing purposes.
Type: int

bpy.app. debug_wm
Boolean for debug info (enabled with the matching --debug / --debug-* command-line flag).
Type: bool

bpy.app. driver_namespace
Dictionary for the drivers namespace, editable in place, reset on file load (read-only).
Type: dict[str, Any]
File Loading & Order of Initialization: since drivers may be evaluated right after a blend-file loads, the driver name-space must be initialized beforehand. Do this by registering text data-blocks to run on startup, so the scripts execute before drivers are evaluated (see Text → Register in Blender's text editor).
Hint: you may prefer external files over Blender's text-blocks, using a text-block that executes an external file. This example runs driver_namespace.py from the same directory as the text-blocks' blend-file:
```python
import os
import bpy
blend_dir = os.path.normpath(os.path.join(__file__, "..", ".."))
bpy.utils.execfile(os.path.join(blend_dir, "driver_namespace.py"))
```
Using __file__ keeps the text resolving to the expected path even when library-linked from another file. Other ways to populate the driver name-space work but tend to be error-prone: the --python command-line argument often fails because the first evaluation looks up a function that doesn't exist yet, marking the driver invalid and stopping further evaluation; and populating it before the blend-file loads also fails, since opening a file clears the name-space. You can instead run a script via --python before the blend file that registers a load-post handler (bpy.app.handlers.load_post) to initialize the name-space — this works for background tasks but won't set up the name-space when opening the file from the file selector.

bpy.app. online_access
Boolean, true when internet access is allowed by Blender & 3rd party scripts (read-only).
Type: bool

bpy.app. online_access_override
Boolean, true when the internet-access preference is overridden by the command line (read-only).
Type: bool

bpy.app. python_args
Leading arguments to use when calling Python directly (via sys.executable). These arguments match the settings Blender uses to ensure Python runs in a compatible environment (read-only).
Type: tuple[str, …]

bpy.app. render_icon_size
Reference size for icon renders (read-only).
Type: int

bpy.app. render_preview_size
Reference size for preview renders (read-only).
Type: int

bpy.app. tempdir
String, the temp directory Blender uses (read-only).
Type: str

bpy.app. use_event_simulate
Boolean for application behavior (enabled with the matching --enable-* command-line flag).
Type: bool

bpy.app. use_userpref_skip_save_on_exit
Boolean for application behavior (enabled with the matching --enable-* command-line flag).
Type: bool

bpy.app. background
Boolean, True when Blender runs without a user interface (started with -b).
Type: bool

bpy.app. factory_startup
Boolean, True when Blender runs with --factory-startup.
Type: bool

bpy.app. module
Boolean, True when running Blender as a Python module.
Type: bool

bpy.app. portable
Boolean, True unless Blender was built to reference absolute paths (on UNIX).
Type: bool

bpy.app. build_branch
The branch this Blender instance was built from.
Type: bytes

bpy.app. build_cflags
C compiler flags.
Type: bytes

bpy.app. build_commit_date
The date of the commit this Blender instance was built from.
Type: bytes

bpy.app. build_commit_time
The time of the commit this Blender instance was built from.
Type: bytes

bpy.app. build_cxxflags
C++ compiler flags.
Type: bytes

bpy.app. build_date
The date this Blender instance was built.
Type: bytes

bpy.app. build_hash
The commit hash this Blender instance was built with.

Type: bytes

bpy.app. build_linkflags
Binary linking flags.
Type: bytes

bpy.app. build_platform
The platform this Blender instance was built for.
Type: bytes

bpy.app. build_system
The build system used.
Type: bytes

bpy.app. build_time
The time this Blender instance was built.
Type: bytes

bpy.app. build_type
The type of build (Release, Debug).
Type: bytes

bpy.app. build_commit_timestamp
The unix timestamp of the commit this Blender instance was built from.
Type: int

bpy.app. version_cycle
The release status of this build: alpha/beta/rc/release.
Type: str

bpy.app. version_string
The Blender version formatted as a string.
Type: str

bpy.app. version
The Blender version as a tuple of 3 numbers (major, minor, micro), e.g. (4, 3, 1).
Type: tuple[int, int, int]

bpy.app. version_file
The Blender file version, as a tuple of 3 numbers (major, minor, file sub-version), used to save a .blend file. The last item is the file sub-version, which differs from the release micro version (the last item of the bpy.app.version tuple); the file sub-version can be incremented several times while a Blender version is in development, and this value is — and should be — used for handling compatibility changes between Blender versions.
Type: tuple[int, int, int]

bpy.app. alembic
Constant value bpy.app.alembic(supported=True, version=(1, 8, 3), version_string='1, 8, 3')

bpy.app. build_options
Constant value bpy.app.build_options(bullet=True, codec_avi=False, codec_ffmpeg=True, codec_sndfile=True, compositor_cpu=True, cycles=True, cycles_osl=True, freestyle=True, image_cineon=True, image_dds=True, image_hdr=True, image_openexr=True, image_openjpeg=True, image_tiff=True, image_webp=True, input_ndof=True, audaspace=True, international=True, openal=True, opensubdiv=True, sdl=False, coreaudio=False, jack=True, pulseaudio=True, wasapi=False, libmv=True, mod_oceansim=True, mod_remesh=True, io_wavefront_obj=True, io_ply=True, io_stl=True, io_fbx=True, io_gpencil=True, opencolorio=True, openmp=False, openvdb=True, alembic=True, usd=True, fluid=True, xr_openxr=True, potrace=True, pugixml=True, haru=True, experimental_features=False)

bpy.app. ffmpeg
Constant value bpy.app.ffmpeg(supported=True, avcodec_version=(61, 19, 101), avcodec_version_string='61, 19, 101', avdevice_version=(61, 3, 100), avdevice_version_string='61, 3, 100', avformat_version=(61, 7, 100), avformat_version_string='61, 7, 100', avutil_version=(59, 39, 100), avutil_version_string='59, 39, 100', swscale_version=(8, 3, 100), swscale_version_string='8, 3, 100')

bpy.app. ocio
Constant value bpy.app.ocio(supported=True, version=(2, 5, 0), version_string='2, 5, 0')

bpy.app. oiio
Constant value bpy.app.oiio(supported=True, version=(3, 1, 7), version_string='3, 1, 7')

bpy.app. opensubdiv
Constant value bpy.app.opensubdiv(supported=True, version=(3, 7, 0), version_string='3, 7, 0')

bpy.app. openvdb
Constant value bpy.app.openvdb(supported=True, version=(13, 0, 0), version_string='13, 0, 0')

bpy.app. sdl
Constant value bpy.app.sdl(supported=False, version=(0, 0, 0), version_string='Unknown')

bpy.app. usd
Constant value bpy.app.usd(supported=True, version=(0, 25, 8), version_string='0, 25, 8')

static bpy.app. help_text ( * , all = False )
Returns the help text as a string.
Parameters: all ( bool ) – Return all arguments, even those which aren't available for the current platform.
Returns: Help text.
Return type: str

static bpy.app. is_job_running ( job_type )
Checks whether a job of the given type is running.
Parameters: job_type ( str ) – job type in Wm Job Type Items.
Returns: Whether a job of the given type is currently running.
Return type: bool

static bpy.app. memory_usage_undo ( )
Gets undo memory-usage information.
Returns: Memory usage of the undo stack in bytes.
Return type: int

## Action Operators

### Action Operators

bpy.ops.action. bake_keys ( )

Fill every frame between picked keyframes with intermediate keys.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. clean ( * , threshold = 0.001 , channels = False )

Reduce F-Curve complexity by pruning tightly-packed keyframes.

Parameters :

- threshold ( float ) – Threshold, (in [0, inf], optional)

- channels ( bool ) – Channels, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. clickselect ( * , wait_to_deselect_others = False , use_select_on_click = False , mouse_x = 0 , mouse_y = 0 , extend = False , deselect_all = False , column = False , channel = False )

Mark keyframes as chosen via cursor clicks.

Parameters :

- wait_to_deselect_others ( bool ) – Wait to Deselect Others, (optional)

- use_select_on_click ( bool ) – Act on Click, Instead of selecting on mouse press, wait to see if there's drag event. Otherwise select on mouse release (optional)

- mouse_x ( int ) – Mouse X, (in [-inf, inf], optional)

- mouse_y ( int ) – Mouse Y, (in [-inf, inf], optional)

- extend ( bool ) – Extend Select, Add keyframe selections instead of replacing the current set (optional)

- deselect_all ( bool ) – Deselect On Nothing, Unselect everything when the cursor finds nothing (optional)

- column ( bool ) – Column Select, Pick every keyframe on the timeline at the cursor position (optional)

- channel ( bool ) – Only Channel, Mark all keyframes in the channel beneath the cursor (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. copy ( )

Transfer chosen keyframes into the clipboard.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. delete ( * , confirm = True )

Erase every selected keyframe.

Parameters :

confirm ( bool ) – Confirm, Prompt for confirmation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. duplicate ( )

Replicate all picked keyframes.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. duplicate_move ( * , `ACTION_OT`_duplicate = {} , `TRANSFORM_OT`_transform = {} )

Replicate all picked keyframes and reposition them.

Parameters :

- `ACTION_OT`_duplicate ( dict [ str , Any ] ) – Duplicate Keyframes, Replicate all picked keyframes (optional, bpy.ops.action.duplicate() keyword arguments)

- `TRANSFORM_OT`_transform ( dict [ str , Any ] ) – Transform, Transform selected items by mode type (optional, bpy.ops.transform.transform() keyword arguments)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. easing_type ( * , type = 'AUTO' )

Govern the easing curve for segments starting at picked keyframes.

Parameters :

type (Literal[Beztriple Interpolation Easing Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. extrapolation_type ( * , type = 'CONSTANT' )

Adjust how curves extend past their final keyframes.

Parameters :

type ( Literal [ 'CONSTANT' , 'LINEAR' , '`MAKE_CYCLIC`' , '`CLEAR_CYCLIC`' ] ) – Type, (optional)

- CONSTANT
Constant Extrapolation – Endpoint keyframe values carry forward.

- LINEAR
Linear Extrapolation – End segment slopes extend as straight lines past the endpoints.

- `MAKE_CYCLIC`
Make Cyclic (F-Modifier) – Insert Cycles modifier if absent.

- `CLEAR_CYCLIC`
Clear Cyclic (F-Modifier) – Discard Cycles modifier if no longer needed.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. frame_jump ( )

Move the playhead to the average time of picked keyframes.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. handle_type ( * , type = 'FREE' )

Choose how selected keyframe handles behave.

Parameters :

type (Literal[Keyframe Handle Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. interpolation_type ( * , type = 'CONSTANT' )

Establish how curves behave between picked keyframes.

Parameters :

type (Literal[Beztriple Interpolation Mode Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. keyframe_insert ( * , type = 'ALL' )

Inject keyframes into the specified channels.

Parameters :

type ( Literal [ 'ALL' , 'SEL' , 'GROUP' ] ) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. keyframe_type ( * , type = 'KEYFRAME' )

Determine the category of picked keyframes.

Parameters :

type (Literal[Beztriple Keyframe Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. markers_make_local ( )

Transfer active scene markers into the current Action as local 'pose' markers.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. mirror ( * , type = 'CFRA' )

Reflect picked keyframes across a centerline.

Parameters :

type ( Literal [ 'CFRA' , 'XAXIS' , 'MARKER' ] ) – Type, (optional)

- CFRA
By Times Over Current Frame – Mirror frame positions relative to the active frame.

- XAXIS
By Values Over Zero Value – Mirror value magnitudes (negatives become positive and vice versa).

- MARKER
By Times Over First Selected Marker – Mirror frame positions using the earliest picked marker as the axis.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. new ( )

Build a fresh action.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. paste ( * , offset = 'START' , merge = 'MIX' , flipped = False )

Place keyframes from the clipboard onto the active channels beginning at the current timeline position.

Parameters :

- offset (Literal[Keyframe Paste Offset Items]) – Offset, Adjust frame timing for pasted keys (optional)

- merge (Literal[Keyframe Paste Merge Items]) – Type, Strategy for combining inserted and existing keys (optional)

- flipped ( bool ) – Flipped, Paste keyframes from matching bones on the opposite side if available (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. previewrange_set ( )

Mark Preview Range using bounds of picked Keyframes.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. push_down ( )

Stack the action onto the NLA editor as a fresh strip.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_all ( * , action = 'TOGGLE' )

Change selection state of every keyframe.

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Selection action to execute (optional)

- TOGGLE
Toggle – Change selection for all elements.

- SELECT
Select – Pick all elements.

- DESELECT
Deselect – Unselect all elements.

- INVERT
Invert – Flip selection state for all elements.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_box ( * , axis_range = False , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , mode = 'SET' , tweak = False )

Mark every keyframe within a rectangular region.

Parameters :

- axis_range ( bool ) – Axis Range, (optional)

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Establish a new selection.

- ADD
Extend – Enlarge the current selection.

- SUB
Subtract – Shrink the current selection.

- tweak ( bool ) – Tweak, Operator has been activated using a click-drag event (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_circle ( * , x = 0 , y = 0 , radius = 25 , wait_for_input = True , mode = 'SET' )

Pick keyframe points via circular lasso.

Parameters :

- x ( int ) – X, (in [-inf, inf], optional)

- y ( int ) – Y, (in [-inf, inf], optional)

- radius ( int ) – Radius, (in [1, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Establish a new selection.

- ADD
Extend – Enlarge the current selection.

- SUB
Subtract – Shrink the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_column ( * , mode = 'KEYS' )

Mark all keyframes along a timeline frame.

Parameters :

mode ( Literal [ 'KEYS' , 'CFRA' , '`MARKERS_COLUMN`' , '`MARKERS_BETWEEN`' ] ) – Mode, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_lasso ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , mode = 'SET' )

Choose keyframe points with a freehand lasso.

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Selection trails behind cursor movement for a smoother trajectory (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Greater numbers produce smoother paths (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Minimum offset from the prior point before the selection advances (in [10, 200], optional)

- mode ( Literal [ 'SET' , 'ADD' , 'SUB' ] ) – Mode, (optional)

- SET
Set – Establish a new selection.

- ADD
Extend – Enlarge the current selection.

- SUB
Subtract – Shrink the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_leftright ( * , mode = 'CHECK' , extend = False )

Mark keyframes before or after the playhead.

Parameters :

- mode ( Literal [ 'CHECK' , 'LEFT' , 'RIGHT' ] ) – Mode, (optional)

- extend ( bool ) – Extend Select, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_less ( )

Unselect keyframes at the edges of contiguous selection zones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_linked ( )

Mark keyframes in the same F-Curves as already-picked ones.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. select_more ( )

Mark keyframes neighboring the current selection.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. snap ( * , type = 'CFRA' )

Realign picked keyframes to specified timeline positions.

Parameters :

type ( Literal [ 'CFRA' , '`NEAREST_FRAME`' , '`NEAREST_SECOND`' , '`NEAREST_MARKER`' ] ) – Type, (optional)

- CFRA
Selection to Current Frame – Move selected keyframes to match the active frame.

- `NEAREST_FRAME`
Selection to Nearest Frame – Align selected keyframes to the nearest integer frame (useful for correcting subframe drift).

- `NEAREST_SECOND`
Selection to Nearest Second – Realign selected keyframes to whole-second marks.

- `NEAREST_MARKER`
Selection to Nearest Marker – Snap selected keyframes to the nearest marker.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. stash ( * , create_new = True )

Archive the current action in the NLA as a dormant strip for future retrieval.

Parameters :

create_new ( bool ) – Create New Action, Generate a replacement action after shelving the present one (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. stash_and_create ( )

Archive the current action in the NLA as a dormant strip for future retrieval, and generate a replacement action.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. unlink ( * , force_delete = False )

Disconnect this action from its active slot (and/or quit Tweak Mode).

Parameters :

force_delete ( bool ) – Force Delete, Erase Fake User status and purge the copy archived in the data-block's NLA (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. view_all ( )

Zoom to encompass the whole keyframe timeline.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. view_frame ( )

Recenter the display on the active frame.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.action. view_selected ( )

Zoom to show the extent of picked keyframes.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

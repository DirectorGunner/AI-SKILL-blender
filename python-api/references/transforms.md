# Transforms, Selection Visibility, Editing Texture Paint Colors, Symmetry ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Transforms; Selection & Visibility; Editing Texture Paint Colors; Symmetry; Crashes; - Blender 5.1 Manual; Laptops; Network; Startup; Blender Manual Versions; Adjustment Layer Strip; Gaussian Blur Strip; Additional Math Functions (bl_math); BMesh Geometry Utilities (bmesh.geometry); BMesh Utilities (bmesh.utils); Application Icons (bpy.app.icons); Application Timers (bpy.app.timers); Context Access (bpy.context).

## Transforms

### Transforms

### Move

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Move

Repositions geometry.

### Rotate

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Rotate

Reorients geometry.

### Scale

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Scale

Resizes geometry.

### Transform

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Transform

Alters object position, orientation, and dimensions in a single operation.

### Tool Settings

Each tool offers the following settings to configure how unmasked geometry transforms.

Transform Mode
Determines the method for applying transformations.

All Vertices :

Applies the transformation to every vertex in the mesh.

Elastic :

Applies the transformation with simulated elasticity dynamics. Rather than transforming all vertices, it confines the effect area to the cursor radius.

## Selection & Visibility

### Selection & Visibility

### Selection Masking

When dealing with geometrically complex meshes, targeting intended vertices precisely can prove challenging. Perhaps you wish to paint only a constrained region while leaving surrounding areas unaltered. Selection masking addresses this scenario. Enabling this feature restricts brush application to only chosen vertices or faces. Access the feature via the 3D Viewport header (look for icons in the yellow-highlighted area):

You may select between Face Selection masking (leftmost), Vertex selection masking (center), and Bone selection (rightmost). The latter applies exclusively when the mesh has an Armature modifier. 

Selection masking provides advantages relative to standard paint mode:

- Mesh topology remains visible, even with active modifiers.

- Adjust face selection directly without switching to Edit Mode.

### Details About Selecting

The following standard operations work with selection:

- Alt - LMB – Individual faces

- Shift - Alt - LMB – Add or remove from selection.

- A – Toggle all, A A to empty selection.

- B – Box selection.

- C – Circle brush selection.

- Ctrl - I – Flip selection state.

- L – Grab connected geometry (under cursor).

- Ctrl - L – Grab all linked geometry.

- Ctrl - NumpadPlus – Expand perimeter

- Ctrl - NumpadMinus – Contract perimeter

- Alt - LMB – Vertex Loop Select

### Vertex Selection Masking

Reference

Mode :

Vertex and Weight Paint Modes

Header :

Vertex Selection

Shortcut :

2

In this mode you can pick individual or multiple vertices and restrict paint operations to those alone. All other vertices receive protection from unintended edits.

Vertex Selection masking.

### Face Selection Masking

Reference

Mode :

Texture, Vertex, and Weight Paint Modes

Header :

Paint Mask

Shortcut :

1

This method restricts painting to user-chosen faces, working much like vertex selection masking.

Face Selection masking.

### Hide/Unhide Faces

Hidden faces.

Conceal chosen faces as in Edit Mode using the H key, then paint the exposed areas, and finally reveal the hidden sections again with Alt - H.

### Hide/Unhide Vertices

You cannot independently hide selected faces in vertex mask selection mode. However, switching selection modes converts the selection state. A useful technique is:

- Switch to Face selection mask mode to convert to face selection.

- Refine the selection or conceal the faces.

- Switch back to Vertex Selection mask mode.

Hiding faces ensures exposed faces keep their vertices visible.

### The Clipping Region

Further constrain the paint region using the Clipping Region. Press Alt - B and drag LMB to mark a rectangular zone. The enclosed area becomes your primary region of interest, while the surrounding viewport is obscured.

The Clipping Region isolates important areas for localized work.

Restore full visibility by pressing Alt - B once more.

All paint operations respecting viewport orientation utilize this constraint, including box select and brush application.

Two visual indicators mark active clipping:

- The clipping region boundary displays as gray in the viewport

- The Info overlay indicates "Clipped" display mode

### Select Linked

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked ‣ Linked

Shortcut :

Ctrl - L , Shift - L

Gather geometry connected to presently chosen elements. This proves invaluable when a mesh contains isolated, superimposed sections where standard isolation would be cumbersome. Press Shift - L to deselect linked elements.

Use L to pick linked geometry directly beneath the cursor.

## Editing Texture Paint Colors

### Editing Texture Paint Colors

### Sample Color

Reference

Mode :

Texture Paint Mode

Shortcut :

Shift - X , Shift - Ctrl - X

Extracts a color from the displayed surface and sets it as the active Paint brush color.

This enables seamless matching of brush color to existing painted information directly visible on the mesh.

- Use Shift - X to pick a color at the cursor spot.

- Use Shift - Ctrl - X to pick the rendered viewport color, incorporating lighting, material effects, and all visible elements.

The captured color becomes the primary Paint brush color.

## Symmetry

### Symmetry

Reference

Mode :

Texture Paint Mode

Tool :

Toolbar ‣ Tool ‣ Symmetry

Mirror
Duplicate brush application across chosen local axes. To realign axes, rotate geometry in Edit Mode, not Object Mode.

### Symmetry

Reference

Mode :

Vertex Paint Mode

Tool :

Toolbar ‣ Tool ‣ Symmetry

Mirror
Replicate brush applications across designated local axes. To modify axis orientation, rotate geometry in Edit Mode rather than Object Mode.

### Symmetry

Reference

Mode :
Vertex Paint Mode

Tool :
Toolbar ‣ Tool ‣ Symmetry

Mirror Vertex Groups
Utilize for mirrored painting on groups bearing symmetrical titles,
such as ".R"/ ".L" or "_R" / "_L". Missing mirrors paint symmetrically on
itself.
Naming standards appear in
Editing Armatures: Naming conventions.
Bone/armature rules apply identically here.

Mirror X, Y, Z
Duplicate brush motion across designated local directions.
To adjust axis direction, rotate in Edit Mode rather than Object Mode.

Radial X, Y, Z
Settings enabling radial mirroring along specified directions.
Value determines repetition frequency within full 360-degree rotation along that axis.

Topology Mirror
Employ topology mirroring for matching mirrored mesh sides.
Visit reference for further details.

## Crashes

### Crashes

Common Blender crash sources:

- Memory depletion.

- GPU or driver complications.

- Blender defects.

Auto Save might recover work first.

Repeated issues may resolve via updating GPU drivers
(see Troubleshooting Graphics Hardware), upgrading RAM or GPU, and deactivating demanding settings:

- Reduce undo count Preferences ‣ System ‣ Memory & Limits ‣ Undo Steps .

- Multisample anti-aliasing heightens memory needs and slows performance.

- Linux window managers (KDE, Gnome) often employ graphics acceleration (window decoration, translucency) competing for Blender resources. Disabling effects or lightweight managers help.

Check Blender consumption:

- Windows: Task Manager, ordered by Memory.

- macOS: Activity Monitor.app Memory panel. Or run top -o MEM .

- Linux: run top -o %MEM .

Worst cases warrant reinstalling OS. Windows accumulates latent trouble from patches and remnants.

### Crash Log

Crashes produce logs (text format) with clues.
Usually written to Temporary Directory.

Contents detail tool activity pre-crash plus debugging data. Attaching these helps bug reports, particularly when others lack reproduction.

### Windows

Crashes write files named post blend-file; test.blend makes test.crash.txt .

Batch scripts in Blender folder extract logs:

- blender_debug_log.cmd covers most scenarios.

- blender_debug_gpu.cmd and blender_debug_gpu_workaround.cmd capture GPU data.

- blender_factory_startup.cmd begins with defaults, suggested for debugging.

Module crashes append to blender.crash.txt .
Read blender_debug_out.txt end for location.

### macOS

Post-crash, macOS Crash Reporter displays backtrace afterward, or on restart. Save the display content. Attach to bug reports following guidelines.

~/Library/Logs/DiagnosticReports/ holds .crash entries formatted:
Blender_YYYY-MM-DD-`HHMMSS_MACNAME`.crash . Matching reports offer hints. Alternatively, Console.app explores all "User Reports"
(app sidebar).

### Linux

/tmp receives blender.crash.txt post-crash.

Note

Command Line execution with --factory-startup --debug-all yields extra data.
See Launching from the Command Line and Command Line Arguments.

### Attaching to a Bug Report

Include crash logs when Reporting a Bug.

## - Blender 5.1 Manual

macOS integrates drivers within the OS; upgrading macOS itself updates them.

Numerous driver improvements for AMD and Intel chips appear in Mesa releases. Fresh Mesa point releases prove advisable. Specific OS editions support upgrading via dedicated channels. Ubuntu's kisak-mesa PPA serves as an example.

## Laptops

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

## Network

### Network

### 403 Error Accessing Extensions

Some enterprise networks add extra SSL security layers that block Blender's access to 

This restriction is outside Blender's control; your IT team must grant connection permission for 

See: this report.

## Startup

### Startup

If Blender won't start, check these common issues:

- Verify your system meets minimum requirements.

- Check that your GPU is compatible and drivers are recent (see Troubleshooting Graphics Hardware).

- Turn off antivirus software that may block Blender launch.

- Confirm you have sufficient permissions on your account.

If you cannot resolve the issue yourself, the community forum can help.

### Common Startup Messages

Note

When launching Blender from your desktop GUI, you may not see the terminal window.
To catch startup errors, open a terminal, navigate to the Blender executable location, and launch it from there.

This procedure differs by OS. See command line.

The Blender Console shows many messages. Some simply report status with little impact; others flag serious problems that prevent functions from running or cause the app to hang or exit. Messages can come from Blender's core or from add-ons like Python scripts.

found bundled python: {DIR}
Blender found its embedded Python. Missing or inaccessible folders typically trigger errors, and this message won't display.

Read prefs: {DIR}/userpref.blend
Preferences are stored here.

## Blender Manual Versions

### Blender Manual Versions

### 5 Series | 2025 – 2027

- Blender 5.1

- Blender 5.0

### 4 Series | 2023 – 2025

- Blender 4.5 LTS

- Blender 4.4

- Blender 4.3

- Blender 4.2 LTS

- Blender 4.1

- Blender 4.0

### 3 Series | 2021 – 2023

- Blender 3.6 LTS

- Blender 3.5

- Blender 3.4

- Blender 3.3 LTS

- Blender 3.2

- Blender 3.1

- Blender 3.0

### 2.9 Series | 2020 – 2021

- Blender 2.93 LTS

- Blender 2.92

- Blender 2.91

- Blender 2.90

### 2.8 Series | 2019 – 2020

- Blender 2.83 LTS

- Blender 2.82

- Blender 2.81

- Blender 2.80

### 2.7 Series | 2014 – 2018

- Blender 2.79

### 2.6 Series | 2011 – 2013

- Blender 2.6x

### 2.5 Series | 2009 – 2011

- Blender 2.5x

### 2.4 Series | 2005 – 2009

- Blender 2.4x

## Adjustment Layer Strip

### Adjustment Layer Strip

An Adjustment Layer functions as a standard input strip except it treats all strips underneath as its feed.

Common applications include adding finishing color tweaks across sections without touching meta structures.
Just stack one on top and enable color correction.

You can layer primary and secondary color treatments (maybe with masking for targeting).

### Options

This strip has no settings.

## Gaussian Blur Strip

### Gaussian Blur Strip

This effect softens a strip in a particular direction.
Good for blurring backgrounds or transition material.

### Options

Size X
How far the blur spreads horizontally.

Size Y
How far the blur spreads vertically.

### Example

Gaussian Blur Effect.

## Additional Math Functions (bl_math)

### Additional Math Functions (bl_math) 

Miscellaneous math utilities module.

bl_math. clamp ( value , min = 0 , max = 1 ) 

Constrains a float value within a min/max range. To avoid
confusion, any call must use either one or all three arguments.

Parameters :

- value ( float ) – The numeric value to constrain.

- min ( float ) – The minimum value, defaults to 0.

- max ( float ) – The maximum value, defaults to 1.

Returns :

The clamped value.

Return type :

float

bl_math. lerp ( from_value , to_value , factor ) 

Smoothly interpolates between two float values using a blend factor.

Parameters :

- from_value ( float ) – Starting point when factor is 0.

- to_value ( float ) – Ending point when factor is 1.

- factor ( float ) – The blend weight, normally in [0.0, 1.0].

Returns :

The interpolated value.

Return type :

float

bl_math. smoothstep ( from_value , to_value , value ) 

Computes a smooth transition between 0 and 1 using the specified boundary values.
At positions outside this range, the result clamps to the nearest boundary value.

Parameters :

- from_value ( float ) – Lower boundary where output is 0.

- to_value ( float ) – Upper boundary where output is 1.

- value ( float ) – Position for interpolation.

Returns :

The interpolated value in [0.0, 1.0].

Return type :

float

## BMesh Geometry Utilities (bmesh.geometry)

### BMesh Geometry Utilities (bmesh.geometry) 

This module provides access to bmesh geometry evaluation functions.

bmesh.geometry. intersect_face_point ( face , point ) 

Tests if the projection of a point is inside a face (using the face's normal).

Parameters :

- face (bmesh.types.BMFace) – The face to test.

- point ( tuple [ float , float , float ] | Sequence [ float ] ) – The 3D point to test.

Returns :

True when the projection of the point is in the face.

Return type :

bool

## BMesh Utilities (bmesh.utils)

### BMesh Utilities (bmesh.utils)
This module provides bmesh utility functions for splitting, joining, and modifying mesh elements.

bmesh.utils. edge_rotate ( edge , ccw = False )
Rotates the edge and returns the newly created edge; returns None if the rotation fails.
Parameters:
- edge (bmesh.types.BMEdge) – The edge to rotate.
- ccw ( bool ) – When True the edge will be rotated counter clockwise.
Returns: The newly rotated edge.
Return type: bmesh.types.BMEdge | None

bmesh.utils. edge_split ( edge , vert , fac )
Splits an edge and returns the newly created data.
Parameters:
- edge (bmesh.types.BMEdge) – The edge to split.
- vert (bmesh.types.BMVert) – One of the verts on the edge, defines the split direction.
- fac ( float ) – The point on the edge where the new vert will be created [0 - 1].
Returns: The newly created (edge, vert) pair.
Return type: tuple[bmesh.types.BMEdge, bmesh.types.BMVert]

bmesh.utils. face_flip ( face )
Flips the face's direction.
Parameters: face (bmesh.types.BMFace) – Face to flip.

bmesh.utils. face_join ( faces , remove = True )
Joins a sequence of faces.
Parameters:
- faces (Sequence[bmesh.types.BMFace]) – Sequence of faces.
- remove ( bool ) – Remove the edges and vertices between the faces.
Returns: The newly created face, or None on failure.
Return type: bmesh.types.BMFace | None

bmesh.utils. face_split ( face , vert_a , vert_b , * , coords = () , use_exist = True , source = None )
Splits a face, optionally through intermediate points.
Parameters:
- face (bmesh.types.BMFace) – The face to cut.
- vert_a (bmesh.types.BMVert) – First vertex to cut in the face (face must contain the vert).
- vert_b (bmesh.types.BMVert) – Second vertex to cut in the face (face must contain the vert).
- coords ( Sequence [ Sequence [ float ] ] ) – Optional sequence of 3D points in between vert_a and vert_b.
- use_exist ( bool ) – Use an existing edge if it exists (only used when coords argument is empty or omitted)
- source (bmesh.types.BMEdge | None) – Newly created edge will copy settings from this one.
Returns: The newly created face and loop.
Return type: tuple[bmesh.types.BMFace, bmesh.types.BMLoop]

bmesh.utils. face_split_edgenet ( face , edgenet )
Splits a face into any number of regions defined by an edgenet.
Parameters:
- face (bmesh.types.BMFace) – The face to split.
- edgenet (Sequence[bmesh.types.BMEdge]) – Sequence of edges.
Returns: The newly created faces.
Return type: tuple[bmesh.types.BMFace, …]
Note: regions defined by edges must connect to the face, otherwise they're ignored as loose edges.

bmesh.utils. face_vert_separate ( face , vert )
Rips a vertex in a face away and adds a new vertex.
Parameters:
- face (bmesh.types.BMFace) – The face to separate.
- vert (bmesh.types.BMVert) – A vertex in the face to separate.
Returns: The newly created vertex, or None on failure.
Return type: bmesh.types.BMVert | None
Note: this is the same as loop_separate, added only for convenience.

bmesh.utils. loop_separate ( loop )
Rips a vertex in a face away and adds a new vertex.
Parameters: loop (bmesh.types.BMLoop) – The loop to separate.
Returns: The newly created vertex, or None on failure.
Return type: bmesh.types.BMVert | None

bmesh.utils. uv_select_check ( bm , / , * , sync = True , flush = False , contiguous = False )
Checks the UV selection state for consistency issues.
Parameters:
- bm (bmesh.types.BMesh) – The BMesh to check.
- sync ( bool ) – Check the data is properly synchronized between UV's and the underlying mesh. Failure to synchronize with the mesh selection may cause tools not to behave properly.
- flush ( bool ) – Check the selection has been properly flushed between elements (based on the current bmesh.types.BMesh.select_mode).
- contiguous ( bool ) – Check connected UV's and edges have a matching selection state.
Returns: An error dictionary, or None when no errors are found.
Return type: dict[str, int] | None

bmesh.utils. vert_collapse_edge ( vert , edge )
Collapses a vertex into an edge.
Parameters:
- vert (bmesh.types.BMVert) – The vert that will be collapsed.
- edge (bmesh.types.BMEdge) – The edge to collapse into.
Returns: The resulting edge from the collapse operation.
Return type: bmesh.types.BMEdge

bmesh.utils. vert_collapse_faces ( vert , edge , fac , join_faces )
Collapses a vertex that has only two manifold edges onto a vertex it shares an edge with.
Parameters:
- vert (bmesh.types.BMVert) – The vert that will be collapsed.
- edge (bmesh.types.BMEdge) – The edge to collapse into.
- fac ( float ) – The factor to use when merging customdata [0 - 1].
- join_faces ( bool ) – When true the faces around the vertex will be joined, otherwise collapse the vertex by merging the 2 edges this vertex connects to into one.
Returns: The resulting edge from the collapse operation.
Return type: bmesh.types.BMEdge

bmesh.utils. vert_dissolve ( vert )
Dissolves this vertex (it will be removed).
Parameters: vert (bmesh.types.BMVert) – The vert to be dissolved.
Returns: True when the vertex dissolve is successful.
Return type: bool

bmesh.utils. vert_separate ( vert , edges )
Separates this vertex at every edge.
Parameters:
- vert (bmesh.types.BMVert) – The vert to be separated.
- edges (Sequence[bmesh.types.BMEdge]) – The edges to separate.
Returns: The newly separated verts (including the vertex passed).
Return type: tuple[bmesh.types.BMVert, …]

bmesh.utils. vert_splice ( vert , vert_target )
Splices vert into vert_target, merging them.
Parameters:
- vert (bmesh.types.BMVert) – The vertex to be removed.
- vert_target (bmesh.types.BMVert) – The vertex to merge into.
Note: the verts mustn't share an edge or face.

## Application Icons (bpy.app.icons)

### Application Icons (bpy.app.icons)

bpy.app.icons. new_triangles ( range , coords , colors )
Creates a new icon from triangle geometry.
Parameters:
- range ( tuple [ int , int ] ) – Pair of ints.
- coords ( bytes ) – Sequence of bytes (6 floats for one triangle) for (X, Y) coordinates.
- colors ( bytes ) – Sequence of bytes (12 for one triangle) for RGBA.
Returns: Unique icon value (pass to the interface icon_value argument).
Return type: int

bpy.app.icons. new_triangles_from_file ( filepath )
Creates a new icon from triangle geometry.
Parameters: filepath ( str | bytes ) – File path.
Returns: Unique icon value (pass to the interface icon_value argument).
Return type: int

bpy.app.icons. release ( icon_id )
Releases the icon.
Parameters: icon_id ( int ) – The icon id to release.

## Application Timers (bpy.app.timers)

### Application Timers (bpy.app.timers)

### Run a Function in x Seconds
```python
import bpy

def in_5_seconds():
    print("Hello World")

bpy.app.timers.register(in_5_seconds, first_interval=5)
```

### Run a Function every x Seconds
```python
import bpy

def every_2_seconds():
    print("Hello World")
    return 2.0

bpy.app.timers.register(every_2_seconds)
```

### Run a Function n times every x seconds
```python
import bpy

counter = 0

def run_10_times():
    global counter
    counter += 1
    print(counter)
    if counter == 10:
        return None
    return 0.1

bpy.app.timers.register(run_10_times)
```

### Assign parameters to functions
```python
import bpy
import functools

def print_message(message):
    print("Message:", message)

bpy.app.timers.register(functools.partial(print_message, "Hello"), first_interval=2.0)
bpy.app.timers.register(functools.partial(print_message, "World"), first_interval=3.0)
```

bpy.app.timers. is_registered ( function )
Checks whether this function is registered as a timer.
Parameters: function ( Callable [ [ ] , float | None ] ) – Function to check.
Returns: True when this function is registered, otherwise False.
Return type: bool

bpy.app.timers. register ( function , * , first_interval = 0 , persistent = False )
Adds a new function to be called after the given number of seconds. The function takes no arguments and should return either None or a float: returning None unregisters the timer, while a returned number sets the delay until it's called again. functools.partial can be used to assign some parameters.
Parameters:
- function ( Callable [ [ ] , float | None ] ) – The function that should called.
- first_interval ( float ) – Seconds until the callback should be called the first time.
- persistent ( bool ) – Don't remove timer when a new file is loaded.

bpy.app.timers. unregister ( function )
Unregisters a timer.
Parameters: function ( Callable [ [ ] , float | None ] ) – Function to unregister.

## Context Access (bpy.context)

### Context Access (bpy.context)

Contextual members vary depending on the current Blender workspace zone and editing mode.

Important: all context values are read-only. Modifications happen through the data API or operator execution.

bpy.context. context

Retrieves the active window environment and data state.

Type :

bpy.types.Context

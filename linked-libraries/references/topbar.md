# Topbar, Curve Pen, Attributes, Geometry To Instance Node ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Topbar; Curve Pen; Attributes; Geometry to Instance Node; Join Geometry Node; Gizmos; Simulation Zone.

## Topbar

The Topbar provides access to key file and scene management features.

Splash Screen
Access the Splash Screen.

About Blender
Displays version and build information including:
- Version : The Blender version.
- Date : Date when Blender was compiled.
- Hash : The Git Hash of the build (useful for support diagnostics).
- Branch : Optional branch name.
- Windowing Environment : On Linux, shows either Wayland or X11 depending on the windowing environment.
- Donate : Open Blender's Development Fund website.
- What's New : Open the latest release notes.
- Credits : Open the credits webpage.
- License : Open the license webpage.
- Blender Store : Open the Blender Store website.
- Blender Website : Open main Blender website.

Install Application Template
Install a new application template.

File Menu covers these operations:

New Ctrl - N
Start with a fresh scene using your chosen application template.

Open Ctrl - O
Load a blend-file.

Open Recent Shift - Ctrl - O
Access a history of recently opened blend-files with preview and metadata.
Choose any file name to load it.

Clear Recent Files List
Erase items from the recent files history.

Revert
Reopen the file to its previously saved state.

Recover
Restore a blend-file from Blender crashes or unexpected closures.
Options:
- Last Session
- Auto Save

Save Ctrl - S
Write the current blend-file to disk.

Save As… Shift - Ctrl - S
Open File Browser to set filename and save location.

Save Copy…
Store a duplicate of the current file without changing the working file.

Save Incremental Ctrl - Alt - S
Write to disk with a numerical suffix, preserving existing files.

Link…
Pull data from another blend-file (library) into the current one.
Linked data updates only when the source library changes.
Link and Append load only selected data from another file.
See Linked Libraries.

Append…
Bring data from an external blend-file into the current one as an independent copy.
The new data is no longer connected to the source file.

Data Previews
Manage data-block preview images.

Import
Bring in information from other graphics software file formats.
See Import/Export.

Export
Save your work in a format that other graphics applications can process.
See Import/Export.

Export All Collections
Run all configured exporters for every collection.

External Data
Resources like image textures can live inside the blend-file (packed) or as separate files (unpacked).
Blender tracks all unpacked resources via relative or absolute paths.
See pack or unpack external data.

Automatically Pack Resources
Bundle all active external files and any new files added later. Disable to halt automatic packing of new content; existing packed data remains.

Pack Resources
Collect all active external files into the blend-file. After saving, external files stop being used—changes to them won't appear in the file, and they can be moved or removed.

Unpack Resources
Restore previously packed files as external ones. Decide whether to use existing files or overwrite them.

Pack Linked Libraries
Bundle data-blocks sourced from an external
blend-file into the current one.

Unpack Linked Libraries
Export previously bundled data-blocks back to external blend-files. Overwrites existing files.

Make Paths Relative
Convert all external file paths to be relative to the current blend-file.

Make Paths Absolute
Convert all external file paths to full system paths.

Report Missing Files
Check for broken links to unpacked files. After selecting, a warning appears in the Info editor's header if any are found.

Find Missing Files
Locate and repair broken links. A File Browser opens to let you choose a directory; the search runs recursively across all contained directories.
Every missing file discovered is recovered.
Recovery uses absolute paths; select Make Paths Relative later if needed.

Note

Recovered files may need reloading. Save and reload the entire file to refresh all external resources simultaneously.

Clean Up

Purge Unused Data
Open a dialog to delete unused data-blocks from the blend-file or any Linked Data (cannot be undone).
See the Outliner for more information.

Manage Unused Data
Open an Outliner pop-up in Unused Data mode showing data-blocks and other data that are unused or will be discarded on reload. Includes data-blocks with only a fake user.
Add or remove Fake User by clicking the icon on the right side of the Outliner.

Defaults
This menu controls the startup file used to load default scene, workspace, and interface when creating a new file.

Initially contains the built-in startup scene.
Replace this with your own setup.

Save Startup File
Store the current blend-file as the startup file.

Load Factory Settings
Restore the default startup file and preferences.

When an Application Template is active:

Load Factory Blender Settings
Restore original Blender settings without the current template's changes.

Load Factory (Application Template Name) Settings
Restore original template settings.

See also

Managing Preferences.

Quit Ctrl - Q
Exit Blender. The active scene saves to "quit.blend" in Blender's temp directory
(location shown in "File Paths" tab of the Preferences).

Edit Menu provides these operations:

Undo, Redo, Undo History
See Undo & Redo.

Adjust Last Operation, Repeat Last, Repeat History
See Undo & Redo.

Menu Search
Find a menu by name.

Operator Search
Run an operator by name (Developer Extras only).

Rename Active Item
Change the name of the active object or node;
see Rename tool for more information.

Batch Rename
Change names across multiple data types at once;
see Batch Rename tool for more information.

Lock Object Modes
Restrict selection to objects in the current working mode.

Note

This guards against unwanted mode switches, such as clicking background scenery while in Pose Mode when you meant to select a bone. You may disable this when rigging objects, sculpting, or painting to intentionally switch between different object modes.

Preferences Ctrl - Comma
Open the Preferences window.

Render Menu covers:

Render Image F12
Produce output for the active scene at the current frame.

Render Animation Ctrl - F12
Generate a sequence for the active scene.

See also

- Rendering Animations for details.

Render Sequencer Image Alt - F12
If a Sequencer Scene exists and differs from the active one, generate that
scene instead.

Render Sequencer Animation Ctrl - Alt - F12
Generate a sequence for the Sequencer Scene.

Note

Both sequencer render options automatically enable the
Show Sequencer Scene toggle in the image editor Render
Result after generation.

Render Audio
Mix the scene's audio track to a sound file.

See also

- Rendering audio for details.

View Render F11
Show the Render window. (Press again to switch back to the main Blender window.)

View Animation Ctrl - F11
Play back rendered output in a separate player.

See also

- Animation player for details.

- Preferences for selecting a
different animation player than the default one.

Lock Interface
Freeze the interface during rendering to allocate more memory to the renderer.

Window Menu provides:

New Window
Duplicate the current window.

New Main Window
Create a window with its own workspace and scene selection.

Toggle Window Fullscreen
Switch the current window fullscreen.

Next Workspace
Move to the next workspace.

Previous Workspace
Move to the previous workspace.

Show Status Bar
Toggle the Status Bar visibility at the bottom of the window.

Save Screenshot
Capture the current Blender window.
A File Browser opens to choose the save location.

Save Screenshot (Editor)
Capture a specific Editor.
Click LMB within its area after running the operator.
A File Browser opens to choose the save location.

Help Menu
See Help Menu.

Workspaces
This set of tabs switches between Workspaces,
which are predefined window layouts.

Scenes & Layers
These data-block menus select
the current Scene and View Layer.

## Curve Pen

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Curve Pen

Construct and edit curves efficiently.

Usage:

Curve Pen Preferences 

These preferences configure via:
Preferences ‣ Keymap ‣ 3D View ‣ Curve ‣ 3D View Tool: Edit Curve, Curve Pen .

Extrude Point
LMB click adds a new point connected to an existing one.

Extrude Handle Type
The handle type of extruded points.
Choose Vector or Auto .
Moving handles switches the type to Align (See Move Point ).

Delete Point
Ctrl - LMB click an existing point to remove it.

Insert Point
Ctrl - LMB click a Curve Segment to add a point between two
adjacent points. Ctrl - LMB click and drag to adjust the handles.

Move Segment
LMB drag a segment between two points to adjust handles, changing the
curve shape without moving any points.

Select Point
LMB click to pick a single point or handle.

Move point
LMB drag to move points or handles. With a spline endpoint chosen,
click and drag empty space to Extrude Point and move the handle simultaneously.

Close Spline
Close the spline by clicking the endpoints one after another.

Close Spline Method
When Close Spline activates.

None :

Disable Close Spline.

On Press :

Close on mouse down. Click and drag to adjust endpoint handles.

On Click :

Activate on release. Click and drag won't trigger Close Spline.

Toggle Vector
Double LMB click a handle to switch between Vector and Auto types.
Easily switch between sharp corners and smooth curves.

Cycle Handle Type
Double LMB click the point to cycle all handle types.

Hotkeys:

Free-Align Toggle
Hold LeftShift while dragging a handle to switch between Free and Align types.
Useful for sharp corners along the curve.

Move Adjacent Handle
Hold LeftCtrl while dragging a handle to move the neighboring handle of the adjacent point.
Handy for tuning newly made curve segments.

Move Entire
Hold Spacebar while dragging to move the whole point.

Link Handles
Press RightCtrl while dragging a handle to mirror movement on the opposite point handle.

Lock Handle Angle
Hold LeftAlt while dragging to keep the handle to its current direction,
adjusting only its length.

## Attributes

An attribute stores per-element data within geometry. Every vertex might hold a number or a vector. Values update via a Group Output connection or through nodes that alter specific attributes.

Data types and domains convert implicitly where supported, like node sockets.

Named attributes appear in other Blender workflows: shaders, painting, UV mapping. In modifiers, use the icon next to a value to pick an attribute by searching existing ones on the input geometry.

Attribute Search display: left shows domain, middle the name, right the data type.

The Normal and Rotation outputs exemplify attribute fields—data stored on geometry referenced by socket.

Anonymous attributes are generic data without a name. Most Blender interfaces expose named attributes, but geometry nodes pass attributes via sockets as Attribute Field outputs. Nodes find the referenced data in the input geometry.

Anonymous attributes stay stored and interpolate across geometry changes, except in rare cases. As long as the socket connection persists, the attribute remains available. They cannot bridge completely separate geometries from different sources. Use Sample Index Node or Sample Nearest Surface Node to transfer between unrelated geometry.

The attribute's underlying representation.

Float: Scalar value (weights, intensity).
Boolean: True/false (conditions).
Integer: 32-bit whole number (indices, counts).
Vector: 3D direction or position.
Color: RGBA in linear space, 32-bit per channel (HDR, wide gamut).
Byte Color: RGBA in sRGB, 8-bit per channel (compact).
String: Text (names, labels).
2D Vector: Flat direction or UV pair.
8-Bit Integer: Compact range (−128 to 127).
2D 16-Bit Integer Vector: Compact 2D pair (signed).
2D Integer Vector: Standard 2D pair (signed, 32-bit).
Quaternion: Rotation representation.
4x4 Matrix: Transformation or spatial relationship.

Ordered from least to most "data-rich" (integer > boolean, more complex = more data). When joining geometries with matching names, the richer type is preferred. This matters with Join Geometry Node.

2D Vectors (UV) and Byte Colors require Store Named Attribute (no sockets).

Data conversions via Geometry Nodes:

Color ↔ Vector: Channel-to-component mapping.
Color ↔ Float: Color becomes grayscale.
Float ↔ Integer: Integer → Float direct; Float → Integer truncates.
Float ↔ Vector: Float → Vector copies to all components; Vector → Float averages.
Float ↔ Boolean: > 0 → True; True → 1, False → 0.

The domain defines the geometry element type the attribute binds to.

Point domain: Single spatial locations (mesh vertices, cloud points, curve control points).
Edge domain: Mesh edges.
Face domain: Mesh faces.
Face Corner domain: Face corners (e.g., UV maps).
Spline domain: Connected curve control point groups.
Instance domain: Instances in geometry; only in geometry nodes.
Layer domain: Grease Pencil layers.

Attributes auto-convert between domains. When Position (point domain) feeds a face selection, values interpolate to faces. Boolean interpolation uses special rules:

| From | To | Conversion |
| Point | Edge | An edge is selected if both of its vertices were selected. |
| Point | Face | A face is selected if all of its vertices were selected too. |
| Point | Corner | Each corner's value is simply a copy of the value at its vertex. |
| Point | Spline | A spline is selected if all of its control points were selected. |
| Edge | Point | A vertex is selected if any connected edge was selected. |
| Edge | Face | A face is selected if all of its edges are selected. |
| Edge | Corner | A corner is selected if its two adjacent edges were selected. |
| Face | Point | A vertex is selected if any of the connected faces were selected. |
| Face | Edge | An edge is selected if any connected face was selected. |
| Face | Corner | Each corner's value is simply a copy of the value at its face. |
| Corner | Point | A vertex is selected if all connected face corners were selected and it is not a loose vertex. |
| Corner | Edge | An edge is selected if all corners on adjacent faces were selected. |
| Corner | Face | A face is selected if all of its corners were selected. |
| Spline | Point | Each point's value is simply a copy of the corresponding value of the spline. |

Built-in attributes always exist and cannot be deleted. Type and domain are fixed.

| Name | Type | Domain | Notes |
| position | Vector | Point | Vertex or point location in object-local space. Moved by Transform Geometry Node, Set Position Node, and similar. |
| radius | Float | Point | Point cloud size marker. On curves, scales control points when converted to mesh or used in operations. |
| id | Integer | Point | Stability marker from Distribute Points on Faces, and instance motion-blur index. Expected to be high-valued, unordered. Unlike other built-ins, can be removed. Used by Random Value Node and similar for seeding. |
| material_index | Integer | Face | Material slot assignment per face. |
| sharp_edge | Boolean | Edge | Flat (vs. smooth) shading toggle for viewport and render. |
| sharp_face | Boolean | Face | Flat (vs. smooth) shading toggle for viewport and render. |
| resolution | Integer | Spline | Evaluated points between control points (NURBS and Bézier only; poly always 1). |
| cyclic | Boolean | Spline | Whether the spline connects first and last control points. |
| handle_left | Vector | Point | Left Bézier handle location (curve start side). Present only with Bézier splines. |
| handle_right | Vector | Point | Right Bézier handle location (curve end side). Present only with Bézier splines. |

These attributes do not exist by default but are expected by certain Blender functions. Type can change, unlike built-ins, but Blender may expect specific types.

| Name | Type | Domain | Notes |
| bevel_weight_vert | Float | Point | Bevel modifier vertex control. |
| bevel_weight_edge | Float | Edge | Bevel modifier edge control. |
| crease_edge | Float | Edge | Subdivision Surface modifier input (range 0–1). |
| crease_vert | Float | Point | Subdivision Surface modifier input (range 0–1). |
| custom_normal | 2D 16-Bit Integer Array | Face Corner | Custom Split Normals mesh support. |
| freestyle_edge | Boolean | Edge | Mesh edge mark. |
| freestyle_face | Boolean | Edge | Mesh face mark. |
| rest_position | Vector | Point | Pre-deformation point location. Auto-created before Shape Keys and Modifiers with Add Rest Position. |
| sculpt_face_set | Integer | Face | Sculpt Face Sets Feature marker. |
| sculpt_mask | Float | Point | Sculpt Masking Feature marker. |
| surface_uv_coordinate | 2D Vector | Curve | Curve anchor location on mesh surface; hair system use. |
| uv_seam | Boolean | Edge | UV island boundary marker. |
| velocity | Vector | Point | Motion-blur indicator during animation render. |

Vertex groups, UV maps, and Color Attributes are accessible as attributes. Reference them by name. Avoid name collisions (same name across categories); a collision masks one attribute. Other names are created on first use.

Geometry nodes may not always output expected types (e.g., Join Geometry may not create vertex groups). If you change a vertex group's type from Float, it ceases being a vertex group.

The Attributes panel in the property editor houses this operator, which converts an attribute's domain or data type.

Since attributes are still maturing in many Blender areas, some tools do not yet support the generic attributes (named, any domain, any type) that geometry nodes produce. This operator bridges that gap for cases requiring compatibility.

Mode:

Generic: Interpolate and convert per domain/type rules described here.
Vertex Group: Create a Vertex Group (float, point domain).

Note: This only affects original object data, not modifier results. To change procedurally generated attributes, apply modifiers first.

## Geometry to Instance Node

Geometry to Instance Node

Wraps every connected input as a separate instance. Visually resembles Join Geometry Node but outputs instances rather than merged data. Faster than Join Geometry on large inputs because data merging is avoided.

Useful with Pick Instances in Instance on Points Node to select among node-tree-generated geometries (vs. picking from Collection Info Node instances).

Inputs:
Geometry — Input geometries to wrap. Multiple links accepted. Muting passes only the first link.

Outputs:
Geometry — Standard geometry output.

Examples:
Paired with Instance on Points Node to randomly pick among primitives.

## Join Geometry Node

Join Geometry Node

Merges multiple geometry sources into a single result. Output data type reflects the union of inputs.

Note: Cannot handle multiple volume inputs simultaneously.

Materials:
When inputs carry different material sets, output consolidates all materials from all inputs.

Attributes:
During merging, the highest-complexity data type is chosen. Example: weight boolean on one input and vector on another becomes vector on output.

Note: Vertex groups survive instance realization and geometry joining. If domain and type rules produce vertex domain and float type, the attribute becomes a vertex group on output.

Inputs:
Geometry — Geometries to merge. Multiple links accepted. Muting passes only the first link.

Outputs:
Geometry — Standard geometry output.

## Gizmos

Gizmos let you change Geometry Nodes inputs directly in the 3D viewport, which is often more intuitive than adjusting them in the modifier or node editor.

Using Gizmos: node inputs that a gizmo can control carry an extra icon, and that node's gizmos show when it is selected; clicking the icon pins the gizmo so it shows even when the node isn't selected, and adjusting the gizmo in the viewport changes the socket's value.
Note: built-in nodes don't have their own gizmos yet, but you can build node groups that do.
Gizmos often propagate automatically when an input socket carrying a gizmo is linked — the gizmo then controls the value it propagates to, rather than the node group's input directly. Not every node supports propagating gizmos, but many math operations do, and a double link marks a successful propagation (for example, the gizmo propagated from the Size X input socket to the Value node). Gizmos can also propagate to Group Inputs, making them available on the parent group node too; and if the current group is used by a modifier directly, the gizmo is available on the modifier, where propagated gizmos always show while the modifier is active, regardless of whether any node is visible or selected.

Creating Custom Gizmos: adding custom gizmos to a node group that generates or modifies geometry can make it handier to use. To add one, use a gizmo node. The aspect that makes gizmos unintuitive at first is the bidirectional dependency: changing the gizmo position changes the controlled value, and vice versa. In the simplest setup, the Linear Gizmo node adds a gizmo drawn in the 3D viewport that controls the value plugged into it — but you'll notice the gizmo keeps jumping back to the origin even as the value changes, because the gizmo node's Position doesn't depend on the value yet. Once the gizmo position is made to depend on the value, it works more than you'd expect, now in both directions: changing the value moves the gizmo, and moving the gizmo changes the value. You can plug multiple values into a gizmo node's Value input at once, so moving the gizmo modifies them all together — use multiply or divide nodes if they should change at different rates. Join the gizmo node's Transform output into the geometry the gizmo controls, which helps Blender understand the gizmos should be transformed together with the geometry later on (for example, adding simple gizmos to the built-in Grid node).
Note: generally you can build the entire node group's functionality first and add gizmos afterward.

## Simulation Zone

Simulation Zone

Allow one frame's result to influence the next. Simple rules create complex results over time. Physics simulation is the most common type.

Two nodes define the "Simulation Zone" between them.

Inputs to Simulation Input evaluate once at start, pass to the next state and output. Other nodes link from outside, re-evaluating per frame.

No outbound links allowed. Results exit only via Simulation Output, enabling sub-frame interpolation for motion blur.

Note: Tool context not supported—Modifier context only.

Note: Anonymous attributes don't propagate unless stored in the simulation state. Detecting required anonymous attributes needs to look ahead.

Clock: The simulation ties to the animation system with sub-step support. Evaluates only on frame changes and caches like Blender's physics simulations.

Properties: Rename, shuffle, and remove inputs in the Node Editor. Sub-steps are configured here.

Inputs
Geometry: Default input for geometry into the zone. Add more items by dragging sockets into the blank or via Simulation State panel. Rename via Ctrl+LMB on the name or in Properties.
Delta Time: Time between frames in seconds (inverse of Frame Rate). Drives the simulation through rate-dependent node setups. Keeps playback consistent when frame rate changes.
Skip: Bypass the simulation zone, passing input directly to output.

Baking: Auto-caches during playback. Valid cache shows as a yellow line in the timeline, letting animators review all prior frames.

Users can opt out of "Cache" to save memory when only the current frame matters.

To render on a render-farm, bake to disk for non-sequential rendering. Note: Baking all modifiers on selected objects.

Examples: Combine with Index of Nearest to create sphere-based simulations.

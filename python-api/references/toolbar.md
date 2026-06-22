# Toolbar, Viewport Gizmos, Dope Sheet Overlays, Info Editor ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Toolbar; Viewport Gizmos; Dope Sheet Overlays; Info Editor; Selecting Outliner Items; Experimental; Gizmos; Sequencer.

## Toolbar

The Toolbar holds a list of tools. Links to each mode's Toolbar follow.
Object Mode: Object Mode.
Edit Mode: Mesh Edit Mode, Curve Edit Mode, Surface Edit Mode, Metaball Edit Mode.
Paint Modes: Sculpt Mode, Texture Paint Mode, Vertex Paint Mode, Weight Paint Mode.
Grease Pencil: Grease Pencil Edit, Grease Pencil Draw, Grease Pencil Sculpting, Grease Pencil Weight Paint.

Selection tools:
Tweak — select or move.
Select Box — select strips by dragging a box; every strip the box touches is selected.
Select Circle — select strips by dragging a circle; every strip the circle's path touches is selected.
Select Lasso — select strips by drawing a lasso.

Blade — cuts a strip in two: it first trims the strip to show only the content up to the cut, then adds a second strip showing the content after it. The Blade tool handles both point cuts and a box gesture for swiftly clearing unwanted strip sections. You can split in these ways:
- Choose the tool in the Toolbar, then click a strip wherever you want the split.
- Click and drag a box; everything inside it is sliced out and deleted.
With the box gesture, everything inside the box area is deleted. With Remove Gaps on, strips after the removed section move backward in time to close the gap (ripple). When rippling, this applies to every channel the box crosses; channels the box doesn't cover stay put, letting other strips keep their relative timing if you like. If the box starts at a strip's beginning or end, the ripple amount comes from the distance between the strip handle and the box's time-side, and when the box spans gaps between strips, those gaps can be removed when rippling too.
Tool Settings:
Type — the split type for point-based cuts. Soft (you can still restore the cut content in the new strips by dragging their handles) or Hard (you can't restore it by dragging handles, though it can still be recovered via the Hold Offset in the Sidebar).
Remove Gaps — in box blade mode, closes the gaps left between cut strips and ripples following strips earlier in time; hold Shift before dragging to skip this briefly and keep the gap.
Ignore Selection — in box blade mode, cuts every strip inside the box, selected or not.
Ignore Connections — keeps the cut from propagating to connected strips, such as effect strips.

Slip — moves only a strip's content. By default it only lets the content move within the strip handles; while that limit is in force the strip outline is drawn red, and pressing C toggles the limiting on or off.

Curve Edit Mode provides these tools:

Select
Choose or move.

Select Box
Pick objects by dragging a box.

All intersecting the box become active.

Select Circle
Pick objects by dragging a circle. All intersecting the circle path become active.

Select Lasso
Pick objects by drawing a freehand outline.

Cursor
Move the 3D Cursor.

Move
Translation tool.

Rotate
Rotation tool.

Scale
Scale tool.

Scale Cage
Adjust scale by controlling the cage.

Transform
Adjust translation, rotations, and scale.

Annotate
Free-hand annotations.

Annotate Line
Straight line annotation.

Annotate Polygon
Polygon annotation.

Annotate Eraser
Remove drawn annotations.

Measure
Find distances in the scene.

Draw
Free-hand creation of new curves.

Curve Pen
Build and edit splines.

Extrude
Extend the curve by adding points.

Radius
Adjust point radius values.

Tilt
Adjust point rotation around the curve axis.

Randomize
Move chosen points in pseudo-random directions.

Curves Edit Mode tools:

Select: Select or move.
Select Box: Select by rectangular region; all intersecting objects are included.
Select Circle: Select by circular region; all intersecting objects are included.
Select Lasso: Select by freehand outline.
Cursor: Reposition the 3D Cursor.
Move: Translation.
Rotate: Rotation.
Scale: Scaling.
Scale Cage: Scale via a deformable bounding box.
Transform: Combined position, rotation, and scaling.
Annotate: Draw freehand marks.
Annotate Line: Draw straight marks.
Annotate Polygon: Draw polygon marks.
Annotate Eraser: Remove marks.
Measure: Measure spatial distances.
Draw: Create new curves by hand.
Radius: Adjust point radius.
Tilt: Adjust point rotation around the curve axis.

Edit Mode Toolbar

The Edit Mode toolbar offers these selection and transformation tools:

Select — Select or move.

Select Box — Select geometry by dragging a box.

Select Circle — Select geometry by dragging a circle.

Select Lasso — Select geometry by drawing a lasso.

Cursor — Change the 3D Cursor location.

Move — Translation tool.

Rotate — Rotation tool.

Scale — Scale tool.

Scale Cage — Scale an object via its cage.

Transform — Adjust translation, rotation, and scale.

Annotate — Draw free-hand annotation.

Annotate Line — Draw straight line annotation.

Annotate Polygon — Draw polygon annotation.

Annotate Eraser — Erase previous annotations.

Measure — Measure distances in the scene.

Add Cube — Interactively add a cube.

Add Cone — Interactively add a cone.

Add Cylinder — Interactively add a cylinder.

Add UV Sphere — Interactively add a UV sphere.

Add Icosphere — Interactively add an icosphere.

Extrude Region — Extrude a selected region freely or along an axis.

Extrude Manifold — Extrude region and dissolve overlapping geometry.

Extrude Along Normals — Extrude along individual surface normals.

Extrude Individual — Extrude each element along its local normal.

Extrude To Cursor — Extrude selected elements toward the mouse cursor.

Inset Faces — Inset selected faces.

Bevel — Create a bevel from selected elements.

Loop Cut — Create a loop cut across the mesh.

Offset Edge Loop Cut — Add two edge loops flanking selected loops.

Knife — Cut the mesh with a knife. Press enter to confirm.

Bisect — Divide the mesh.

Poly Build — Add vertices one by one to build geometry.

Spin — Create geometry by extruding and rotating.

Smooth — Flatten angles of selected vertices.

Randomize — Randomize selected vertex positions.

Edge Slide — Slide an edge along a face.

Vertex Slide — Slide a vertex along an edge.

Shrink/Fatten — Move selected vertices along their normals.

Push/Pull — Move selected elements away from or toward the pivot.

Shear — Shear selected elements.

To Sphere — Move vertices outward in a spherical shape around the object center.

Rip Region — Separate polygons and move the result.

Rip Edge — Extend vertices and move the result.

UV Editor Toolbar

Select — Select or move.

Select Box — Select UVs by dragging a box.

Select Circle — Select UVs by painting.

Select Lasso — Select UVs by drawing a lasso.

Cursor — Change the 2D cursor location.

Move — Translation tool.

Rotate — Rotation tool.

Scale — Scale tool.

Transform — Adjust UV translation, rotation, and scale.

Annotate — Draw free-hand annotation.

Annotate Line — Draw straight line annotation.

Annotate Polygon — Draw polygon annotation.

Annotate Eraser — Erase previous annotations.

Rip — The Rip tool separates UV faces.

Grab — The Grab tool moves UVs using a brush.

Relax — The Relax tool distributes UVs evenly using a brush.

Pinch — The Pinch tool moves UVs toward the brush center.

Edit Mode toolset for metaballs:

Tweak selects or repositions geometry.

Select Box chooses objects by dragging an enclosing rectangle—all intersecting objects are included.

Select Circle chooses objects by dragging a circular path—all intersecting objects are included.

Select Lasso chooses objects by drawing a freehand loop.

Cursor repositions the 3D Cursor.

Move applies translation.

Rotate applies rotational transformation.

Scale applies uniform or directional resizing.

Scale Cage resizes via a visible cage control.

Transform adjusts translation, rotation, and scale simultaneously.

Annotate draws freehand marks.

Annotate Line draws straight marks.

Annotate Polygon draws polygonal marks.

Annotate Eraser removes previous marks.

Measure calculates distances between points.

Shear skews along a specified axis.

### Toolbar

These are the tools you'll find in Edit Mode:

Select
Pick out control points.

Cursor
Reposition the 3D Cursor.

Move
The translation tool.

Rotate
The rotation tool.

Scale
The scaling tool.

Scale Cage
An editable bounding box you scale control points with.

Transform
One tool that handles translating, rotating, and scaling at once.

Annotate
Sketch free-hand annotations.

Measure
Gauge distances within the scene.

Shear
Slant control points along a chosen axis.

### Toolbar

Tweak
Choose or shift.

Select Box
Choose items within a drawn rectangular area.
Any intersecting item becomes selected.

Select Circle
Choose items within a drawn circular area. All overlapping items get chosen.

Select Lasso
Choose items by hand-drawing a shape.

Cursor
Reposition the 3D cursor.

Move
Translation operation.

Rotate
Rotation operation.

Scale
Scaling operation.

Scale Cage
Alter object scale via boundary control.

Transform
Operation for adjusting position, orientation, and size.

Annotate
Sketch freehand notes.

Annotate Line
Draw a single straight annotation.

Annotate Polygon
Sketch a closed polygon annotation.

Annotate Eraser
Erase drawn notes.

Measure
Check distances within the scene.

Add Cube
Place a cube mesh interactively.

Add Cone
Place a cone mesh interactively.

Add Cylinder
Place a cylinder mesh interactively.

Add UV Sphere
Place a UV sphere mesh interactively.

Add Icosphere
Place an icosphere mesh interactively.

### Toolbar

The toolbar contains an extensive collection of sculpting tools. This overview organizes them by functional category.

### Sculpting Tools

Brush
The primary tool for applying any Sculpt mode brush.

### Gesture Tools

Universal gesture-based tools for executing operations via box, lasso, line, and polyline selections. Consult Gesture Tools for details.

Mask Gesture Tools
Establish masks via gesture selection.

Hide Gesture Tools
Show or conceal geometry via gesture selection.

Face Set Gesture Tools
Create face sets via gesture selection.

Trim Gesture Tools
Apply Boolean operations via gesture selection.

Line Project
Align geometry along a drawn reference line.

### Filter Tools

Operations affecting the full unmasked and visible mesh.

Mesh Filter
Deform all unmasked vertices.

Cloth Filter
Simulate cloth behavior on all unmasked vertices.

Color Filter
Adjust active color attributes across all unmasked vertices.

### Single Click Tools

Direct-action tools operating on clicked surfaces.

Edit Face Set
Adjust the face set at the cursor location.

Mask by Color
Generate a mask from a selected color attribute by clicking.

### General Tools

Standard translate, rotate, scale, and annotate functions.

Move
Position adjustment tool.

Rotate
Orientation adjustment tool.

Scale
Size adjustment tool.

Transform
Modify object position, orientation, and dimensions simultaneously.

Annotate
Create freehand notes.

Annotate Line
Create linear notes.

Annotate Polygon
Create multi-point notes.

Annotate Eraser
Remove existing notes.

## Viewport Gizmos

Reference — Mode: All Modes. Location: Header ‣ Gizmos.

Clicking Show Gizmo turns every gizmo in the Movie Clip Editor on or off. The drop-down opens a popover of finer settings, described below.

Viewport Gizmos:
Navigate — toggles the zoom and pan gizmos in the upper-right corner.

## Dope Sheet Overlays

Reference — Mode: All Modes. Location: Header ‣ Overlays.

Clicking Show Overlays turns every overlay in the Dope Sheet on or off. The drop-down opens a popover of finer settings below.
Show Scene Strip Range — while scene time synchronization is in use in the Sequence Editor, displays the range of the current scene strip.

## Info Editor

The Info editor logs the operators that ran along with errors, warnings, and informational messages. Click an entry to select it, holding Shift to add it to the existing selection.

Interface — View Menu:
Area — area controls; see the user-interface documentation.
Info Menu:
Select All (A) — selects every entry.
Deselect All (Alt-A) — deselects every entry.
Invert Selection (Ctrl-I) — selects the unselected entries and deselects the selected ones.
Toggle Selection — selects all entries if none are currently selected, otherwise deselects them.
Box Select (B) — drag a box to add the overlapping entries to the selection.
Delete (X, Delete) — removes the selected entries from the log.
Copy (Ctrl-C) — copies the selected entries to the clipboard.

## Selecting Outliner Items

Selection happens with LMB (and/or the context menu) on a data-block's row; a single selection also makes it active. Selected rows highlight blue, the active one a lighter blue, and clicking empty space below the list deselects everything. Note: by default, selecting data-blocks here also selects the matching objects, bones, and sequences in the 3D Viewport and Video Sequencer, and selections in those sync back to every Outliner; turn off the toggle in the filter popover to disable selection syncing. You can also select a data-block's children by clicking the icon to the right of the parent's name.

Selecting Multiple Data-Blocks — extend the selection one at a time with Ctrl-LMB, each addition becoming active. Select a range from the active element with Shift-LMB, or with Shift-Ctrl-LMB to do so without dropping the previous selection. Double-click an item's icon to grab all its children. A click-and-drag from anywhere but a name or icon starts a box selection — Shift adds, Ctrl subtracts — and B also begins one. A selects everything; Alt-A deselects everything. The keyboard arrow keys navigate and select from the active data-block:
Up — selects the previous element in the list.
Down — selects the next element.
Shift-Up — selects the previous element without deselecting.
Shift-Down — selects the next element without deselecting.
Left — closes the data-block or selects the parent.
Right — opens the data-block to view children, or selects the first child.
Shift-Left — closes this and all child data-blocks.
Shift-Right — opens this and all child data-blocks.

Properties Editor Sync — clicking an item's icon (not its name) makes the Properties Editor switch to the matching tab; disable this via the Properties editor's Sync with Outliner option.

## Experimental

These preferences are reserved for features still under development and not yet finished. Experimental features show up only in Daily Builds.

## Gizmos

Reference — Location: Header ‣ Gizmos.

Clicking Show Gizmo toggles every gizmo in the Video Sequencer. The drop-down opens a popover of finer settings below.
Navigate — turns the navigation gizmo on or off.
Active Tools — turns the active tool's gizmo on or off.

## Sequencer

The Sequencer view type shows a timeline and lets you place and edit strips.

# Transform Pivot Point, Median Point, Object Modes, Viewpoint ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Transform Pivot Point; Median Point; Object Modes; Viewpoint; Contextual Views; Selecting Objects; Add Cone; Add Cube; Add Cylinder; Add Icosphere; Add UV Sphere.

## Transform Pivot Point

The Pivot Point sets the location of the Object Gizmo, and changing it can make transforming around your intended point easier. Reference — Mode: Object Mode and Edit Mode; Location: Header ‣ Transform Pivot Point; Shortcut: Period. (With the default "Median Point" pivot it's tricky to bring a second wheel spoke into place, but with "3D Cursor" it's easy.) Change the Pivot Point via the selector in the 3D Viewport's header. Pivot Types follow.

## Median Point

Reference — Mode: Object Mode and Edit Mode. Location: Header ‣ Transform Pivot Point ‣ Median Point. Shortcut: Period.

Sets the pivot at the mean location of whatever is currently selected.

In Object Mode that mean is derived purely from the origins of the chosen objects; their actual shape and dimensions play no part. Since an origin may sit anywhere — even outside the object's own mesh — the resulting Median Point can land somewhere other than you'd intuitively guess.

In Edit Mode the value is instead the average of the selected vertices, so the pivot drifts toward whichever region packs in the most geometry. Picture two equally sized cubes: with matching vertex counts the pivot rests exactly between them, but subdividing one of the two drags the pivot strongly toward that denser cube even though neither has changed in size.

## Object Modes

Modes let you edit different facets of objects: Object Mode handles position, rotation, and scale; Edit Mode changes geometry; Pose Mode handles posing; and so on.

Switch the active mode with the Mode selector in the 3D Viewport header. Which modes are offered depends on the object's type, and the full list appears below. Besides the selector, pressing Ctrl-Tab pops a pie menu around the cursor for faster access (with an Armature selected, that shortcut instead toggles Object Mode and Pose Mode), and Tab toggles Edit Mode for objects that support it.

Modes can change a lot in Blender:
Each mode swaps the header and Toolbar for its own menus and tools, which also alters the available keyboard shortcuts.
A mode can transform the viewport's appearance — Weight Paint mode, for instance, shades the object to expose its vertex weights, normally invisible.
A mode can reach into other editors — the UV Editor works only while the 3D Viewport is in Edit Mode, and in the Properties editor certain buttons and panels are restricted to particular modes.

Object Mode List:
Object Mode — the default mode, present for every object type; handles position, rotation, scale, duplication, and so on.
Edit Mode — for editing an object's shape (vertices/edges/faces on meshes, control points on curves/surfaces, points/strokes on Grease Pencil, etc.).
Sculpt Mode — an alternative toolset for reshaping an object (meshes only).
Vertex Paint Mode — a mesh-only mode for setting a mesh's vertex colors (i.e. "painting" them).
Weight Paint Mode — a mesh-only mode devoted to vertex-group weighting.
Texture Paint Mode — mesh-only; lets you paint a texture directly onto the model within the viewport.
Particle Edit Mode — mesh-only; geared toward particle systems, handy for editable ones such as hair.
Pose Mode — armature-only; used for posing.
Draw Mode — a Grease Pencil mode for laying down new strokes.
Sculpt Mode (Grease Pencil) — reshapes existing Grease Pencil strokes in a more organic fashion.
Edit Mode (Grease Pencil) — works on the individual points and strokes that make up a Grease Pencil object.
Vertex Paint Mode (Grease Pencil) — applies color straight to the vertices of strokes.
Weight Paint Mode (Grease Pencil) — assigns vertex weights onto strokes.
Note: the cursor turns into a brush in Paint and Sculpt Modes. The modes' actual usage is covered in their own sections rather than here.
Hint: if this manual mentions a button or menu option you can't find on screen, you may simply not be in the mode that makes that option valid.

Switching Objects — Reference: Mode: All Modes; Shortcut: Alt-Q. Say you switch into a mode like Weight Paint and then click a different object: Blender will usually revert to Object Mode, so weight-painting that second object means entering the mode again. There's a way around this: once you're in a mode, the Outliner shows a dot beside other objects that also support it, and clicking that dot moves you to the other object without leaving the mode. Alternatively, point the cursor at the other object in the viewport and tap Alt-Q. See also Lock Object Modes for guarding against accidental mode changes.

Multi-Object Editing — Edit Mode and Pose Mode go further, letting you keep several objects in the mode simultaneously. Two ways to do it: if you're not yet in the mode, just select all the objects and enter; if you're already in it, pull others in by Ctrl-LMB on their dot in the Outliner (removing objects works the same way). A few notes: the Properties Editor only ever shows the active object's details (shape keys, UV maps, …), not those of every selection; selecting any element of an object makes it active; and there are limits on what you can edit — you can't, for example, build an edge that joins vertices from two different objects.

## Viewpoint

The View ‣ Viewpoint menu squares the viewing direction to a specific axis, something you can also do with the Navigation Gizmo or these hotkeys:
Top — Numpad7
Front — Numpad1
Right — Numpad3
Bottom — Ctrl-Numpad7
Back — Ctrl-Numpad1
Left — Ctrl-Numpad3

Those hotkeys square the view to a global (world) axis. Add Shift to align to a local axis of the selected item instead, which lets you, for example, view any mesh face head-on regardless of its orientation (align to a global axis again to leave that local viewpoint). You can also align by holding Alt-MMB and dragging the mouse in a direction.

## Contextual Views

By default the 3D Viewport renders the scene from one vantage point. Quad View instead shows it from several at once, giving extra spatial context while you model, sculpt, or edit.

Quad View — Reference: Mode: All modes; Menu: View ‣ Area ‣ Toggle Quad View; Shortcut: Ctrl-Alt-Q. Toggling it splits the 3D Viewport into four panes: three orthographic views (Top, Front, and Right by default) plus one perspective (User) view. The arrangement makes spatial relationships easier to grasp and precise axis-aligned adjustments easier to make. Resize each pane by dragging from the center where the four meet. Note: Quad View differs from splitting the area and aligning views by hand — here all four panes belong to the same 3D Viewport, so they share display settings such as shading mode, overlays, and visibility options.

Options — Reference: Mode: All modes; Menu: Sidebar ‣ View ‣ Quad View.
Lock Rotation — blocks changes to the orientation and perspective of the orthographic side views, so navigating one view won't rotate or switch the others. Note: enabling it returns the three side views to their standard Top, Front, and Right orientations.
Sync Zoom/Pan — synchronizes zooming and panning across the orthographic side views; requires Lock Rotation to be on.
Clip Contents — clips objects to the region visible to the orthographic views, hiding geometry outside the combined viewing volume so you can more easily inspect interior detail or work in dense scenes.

## Selecting Objects

This page covers the selection tools unique to the 3D Viewport; the general-purpose ones live in the Interface section.

The 3D Viewport has two keys that influence selection:
Select by Origin (Ctrl) — selects objects by their origin instead of their geometry.
Selection Menu (Alt) — when several objects sit under the pointer, pops a menu so you can pick the one you mean.
Combine the two for a selection menu based on object origins.

The mode-specific selection pages follow.
Object Mode: Object Mode.
Edit Mode: Mesh Edit Mode, Curve Edit Mode, Surface Edit Mode, Metaball Edit Mode, Text Edit Mode, Grease Pencil Edit Mode, Bone Edit Mode, Lattice Edit Mode.
Pose Mode: Pose Mode.
Particle Edit Mode: Particle Edit Mode.

## Add Cone

Reference — Mode: Object Mode and Edit Mode. Tool: Toolbar ‣ Add Cone. Drops a cone mesh object into the scene interactively.

Usage: start by dragging with LMB to lay out the object's base; release LMB and slide the mouse to set its height; then click LMB once more to lock in the shape. A few keys can be held to flip a setting for as long as you hold them:
Ctrl — turns snapping on or off.
Alt — switches the Origin setting.
Shift — switches the Aspect setting.

Tool Settings:
Depth — the starting depth (measured from the screen into the scene) used when the object is placed.
  Surface — begins placement on the surface beneath the pointer; with nothing there, it behaves like Cursor Plane.
  Cursor Plane — begins placement on a plane passing through the 3D Cursor, oriented by the Orientation and Plane Axis settings.
  Cursor View — begins placement on a plane through the 3D Cursor that faces the view.
Orientation — the orientation given to the new object: a trio of axes from which Plane Axis selects one.
  Surface — adopts the normal orientation of the surface under the pointer; with no surface, it matches Default.
  Default — adopts the current Transform Orientation.
Snap To — what to target while Snapping.
  Geometry — snaps to every kind of geometry (vertices, edges, faces).
  Default — snaps to whatever the global snapping options specify.
Plane Axis — which of the three Orientation axes (X, Y, or Z) counts as "up" for the object; its base ends up perpendicular to that axis.
Auto Axis — instead of the axis named by Plane Axis, uses the one nearest the viewport's viewing direction (when you aren't hovering a surface).
Base:
  Origin — how the base gets laid out. Edge draws it from one corner across to the opposing corner; Center draws it from the middle out to a corner.
  Aspect — whether the base keeps a free or a fixed aspect ratio. Free lets width and depth be set independently; Fixed forces them equal.
Height:
  Origin — how the height gets laid out. Edge treats the base as the bottom and then you set the top; Center treats the base as the middle and then you set the top.
  Aspect — whether the bounding box's side keeps a free or fixed aspect ratio. Free lets height be set independently of the base; Fixed forces height to match the base's largest side.
Vertices — how many vertices form the base.
Base Fill Type — how the circle at the base is closed off. Triangle Fan fills it with triangles meeting at a central vertex; N-gon fills it with one N-gon; Nothing leaves it open, producing only the outer ring of vertices.

## Add Cube

Reference — Mode: Object Mode and Edit Mode. Tool: Toolbar ‣ Add Cube. Drops a cube mesh object into the scene interactively.

Usage: start by dragging with LMB to lay out the object's base; release LMB and slide the mouse to set its height; then click LMB once more to lock in the shape. A few keys can be held to flip a setting for as long as you hold them:
Ctrl — turns snapping on or off.
Alt — switches the Origin setting.
Shift — switches the Aspect setting.

Tool Settings:
Depth — the starting depth (measured from the screen into the scene) used when the object is placed.
  Surface — begins placement on the surface beneath the pointer; with nothing there, it behaves like Cursor Plane.
  Cursor Plane — begins placement on a plane passing through the 3D Cursor, oriented by the Orientation and Plane Axis settings.
  Cursor View — begins placement on a plane through the 3D Cursor that faces the view.
Orientation — the orientation given to the new object: a trio of axes from which Plane Axis selects one.
  Surface — adopts the normal orientation of the surface under the pointer; with no surface, it matches Default.
  Default — adopts the current Transform Orientation.
Snap To — what to target while Snapping.
  Geometry — snaps to every kind of geometry (vertices, edges, faces).
  Default — snaps to whatever the global snapping options specify.
Plane Axis — which of the three Orientation axes (X, Y, or Z) counts as "up" for the object; its base ends up perpendicular to that axis.
Auto Axis — instead of the axis named by Plane Axis, uses the one nearest the viewport's viewing direction (when you aren't hovering a surface).
Base:
  Origin — how the base gets laid out. Edge draws it from one corner across to the opposing corner; Center draws it from the middle out to a corner.
  Aspect — whether the base keeps a free or a fixed aspect ratio. Free lets width and depth be set independently; Fixed forces them equal.
Height:
  Origin — how the height gets laid out. Edge treats the base as the bottom and then you set the top; Center treats the base as the middle and then you set the top.
  Aspect — whether the object's side keeps a free or fixed aspect ratio. Free lets height be set independently of the base; Fixed forces height to match the base's largest side.

## Add Cylinder

Reference — Mode: Object Mode and Edit Mode. Tool: Toolbar ‣ Add Cylinder. Drops a cylinder mesh object into the scene interactively.

Usage: start by dragging with LMB to lay out the object's base; release LMB and slide the mouse to set its height; then click LMB once more to lock in the shape. A few keys can be held to flip a setting for as long as you hold them:
Ctrl — turns snapping on or off.
Alt — switches the Origin setting.
Shift — switches the Aspect setting.

Tool Settings:
Depth — the starting depth (measured from the screen into the scene) used when the object is placed.
  Surface — begins placement on the surface beneath the pointer; with nothing there, it behaves like Cursor Plane.
  Cursor Plane — begins placement on a plane passing through the 3D Cursor, oriented by the Orientation and Plane Axis settings.
  Cursor View — begins placement on a plane through the 3D Cursor that faces the view.
Orientation — the orientation given to the new object: a trio of axes from which Plane Axis selects one.
  Surface — adopts the normal orientation of the surface under the pointer; with no surface, it matches Default.
  Default — adopts the current Transform Orientation.
Snap To — what to target while Snapping.
  Geometry — snaps to every kind of geometry (vertices, edges, faces).
  Default — snaps to whatever the global snapping options specify.
Plane Axis — which of the three Orientation axes (X, Y, or Z) counts as "up" for the object; its base ends up perpendicular to that axis.
Auto Axis — instead of the axis named by Plane Axis, uses the one nearest the viewport's viewing direction (when you aren't hovering a surface).
Base:
  Origin — how the base gets laid out. Edge draws it from one corner across to the opposing corner; Center draws it from the middle out to a corner.
  Aspect — whether the base keeps a free or a fixed aspect ratio. Free lets width and depth be set independently; Fixed forces them equal.
Height:
  Origin — how the height gets laid out. Edge treats the base as the bottom and then you set the top; Center treats the base as the middle and then you set the top.
  Aspect — whether the bounding box's side keeps a free or fixed aspect ratio. Free lets height be set independently of the base; Fixed forces height to match the base's largest side.
Vertices — how many vertices form the caps.
Cap Fill Type — how the caps are closed off. Triangle Fan fills with triangles sharing a central vertex; N-gon fills each ring with an N-gon; Nothing leaves them open, producing only the outer rings of vertices.

## Add Icosphere

Reference — Mode: Object Mode and Edit Mode. Tool: Toolbar ‣ Add Icosphere. Drops an Icosphere mesh object into the scene interactively.

Usage: start by dragging with LMB to lay out the object's base; release LMB and slide the mouse to set its height; then click LMB once more to lock in the shape. A few keys can be held to flip a setting for as long as you hold them:
Ctrl — turns snapping on or off.
Alt — switches the Origin setting.
Shift — switches the Aspect setting.

Tool Settings:
Depth — the starting depth (measured from the screen into the scene) used when the object is placed.
  Surface — begins placement on the surface beneath the pointer; with nothing there, it behaves like Cursor Plane.
  Cursor Plane — begins placement on a plane passing through the 3D Cursor, oriented by the Orientation and Plane Axis settings.
  Cursor View — begins placement on a plane through the 3D Cursor that faces the view.
Orientation — the orientation given to the new object: a trio of axes from which Plane Axis selects one.
  Surface — adopts the normal orientation of the surface under the pointer; with no surface, it matches Default.
  Default — adopts the current Transform Orientation.
Snap To — what to target while Snapping.
  Geometry — snaps to every kind of geometry (vertices, edges, faces).
  Default — snaps to whatever the global snapping options specify.
Plane Axis — which of the three Orientation axes (X, Y, or Z) counts as "up" for the object; its base ends up perpendicular to that axis.
Auto Axis — instead of the axis named by Plane Axis, uses the one nearest the viewport's viewing direction (when you aren't hovering a surface).
Base:
  Origin — how the base gets laid out. Edge draws it from one corner across to the opposing corner; Center draws it from the middle out to a corner.
  Aspect — whether the base keeps a free or a fixed aspect ratio. Free lets width and depth be set independently; Fixed forces them equal.
Height:
  Origin — how the height gets laid out. Edge treats the base as the bottom and then you set the top; Center treats the base as the middle and then you set the top.
  Aspect — whether the bounding box's side keeps a free or fixed aspect ratio. Free lets height be set independently of the base; Fixed forces height to match the base's largest side.
Subdivisions — drives how many vertices define the sphere. At level 1 the icosphere is an icosahedron — a 20-faced solid of equilateral triangles — and every added subdivision splits each triangular face into four.
Note: subdividing an icosphere multiplies its vertex count alarmingly fast; ten iterations yield 5,242,880 triangles, and adding a mesh that heavy will reliably crash the program.

## Add UV Sphere

Reference — Mode: Object Mode and Edit Mode. Tool: Toolbar ‣ Add UV Sphere. Drops a UV sphere mesh object into the scene interactively.

Usage: start by dragging with LMB to lay out the object's base; release LMB and slide the mouse to set its height; then click LMB once more to lock in the shape. A few keys can be held to flip a setting for as long as you hold them:
Ctrl — turns snapping on or off.
Alt — switches the Origin setting.
Shift — switches the Aspect setting.

Tool Settings:
Depth — the starting depth (measured from the screen into the scene) used when the object is placed.
  Surface — begins placement on the surface beneath the pointer; with nothing there, it behaves like Cursor Plane.
  Cursor Plane — begins placement on a plane passing through the 3D Cursor, oriented by the Orientation and Plane Axis settings.
  Cursor View — begins placement on a plane through the 3D Cursor that faces the view.
Orientation — the orientation given to the new object: a trio of axes from which Plane Axis selects one.
  Surface — adopts the normal orientation of the surface under the pointer; with no surface, it matches Default.
  Default — adopts the current Transform Orientation.
Snap To — what to target while Snapping.
  Geometry — snaps to every kind of geometry (vertices, edges, faces).
  Default — snaps to whatever the global snapping options specify.
Plane Axis — which of the three Orientation axes (X, Y, or Z) counts as "up" for the object; its base ends up perpendicular to that axis.
Auto Axis — instead of the axis named by Plane Axis, uses the one nearest the viewport's viewing direction (when you aren't hovering a surface).
Base:
  Origin — how the base gets laid out. Edge draws it from one corner across to the opposing corner; Center draws it from the middle out to a corner.
  Aspect — whether the base keeps a free or a fixed aspect ratio. Free lets width and depth be set independently; Fixed forces them equal.
Height:
  Origin — how the height gets laid out. Edge treats the base as the bottom and then you set the top; Center treats the base as the middle and then you set the top.
  Aspect — whether the bounding box's side keeps a free or fixed aspect ratio. Free lets height be set independently of the base; Fixed forces height to match the base's largest side.
Segments — the count of vertical segments, running pole to pole like the Earth's meridians.
Rings — the count of horizontal segments, akin to the Earth's parallels.
Note: rings are face loops rather than edge loops, which would number one fewer.

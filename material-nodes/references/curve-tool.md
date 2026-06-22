# Curve Tool, Eyedropper, Fill Tool, Line Tool ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Curve Tool; Eyedropper; Fill Tool; Line Tool; Polyline Tool; Grease Pencil Menu; Selecting Grease Pencil Elements.

## Curve Tool

### Curve Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Curve

Complex Bézier style curves, drawn with any Draw type brush, are what the Curve tool produces.

### Tool Settings

The brush's core settings sit right in the Tool Settings for handy access; Draw Brush documents that configuration.

Subdivisions
Count of stroke points placed along each edge of the stroke.

Thickness Profile
A curve widget governs how thick the stroke runs from its left start to its right end.

Use Curve
Enable it to let a curve profile steer thickness along the curve.

### Brush Asset
Chooses which brush asset the tool draws with.

See Brush Asset for more information.

See Draw Brushes for a detailed list of all draw brushes and their options.

### Brush Settings
Parameters shaping how the stroke looks.

See Draw Brushes for details.

### Color
Settings that fix the stroke color.

See Color

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. Curve relies on Draw Brush types. Brush Settings has more.

### Creating Curves

- Press down with LMB (or the Pen tip) where the shape begins, then drag.

- Let go at the spot where it should finish.

- Once released, two cyan Bézier-like manipulators let you adjust the curve.

- Then confirm ( Return / MMB ) or cancel ( Esc / RMB ).

Mid-drag, hold Shift to adjust the curve with a lone manipulator (as the Arc tool does), or Alt to build the arc outward from a center.

NumpadPlus and NumpadMinus or the mouse Wheel raise or lower how many points end up in the curve.

F tunes line thickness; Shift - F tunes stroke opacity.

| click and dragging the start point.  | Tweaking curve with the manipulators.  | The curve after confirming.  |

### Extruding
Ahead of confirming, E drags the curve's end point outward so you can chain curves together.

| End point extruding.  | Tweaking the last curve with the manipulators.  | The connected curves after confirming.  |

## Eyedropper

### Eyedropper

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Eyedropper

Sampling colors out of the 3D Viewport, the Eyedropper tool spins them into materials or palette colors.

### Tool Settings

Material :

Spawns a fresh material whose Stroke Base Color is set to the color you sampled.

Material Mode
The color transformation lands on the stroke color, the fill color, or both.

Stroke :

Only paint over strokes.

Fill :

Only paint over fill areas.

Both :

Paint over strokes and fill areas

Palette :

Add a new color to the color palette based on the sampled color.

Brush :

Sets the brush color to the sampled color.

### Usage

- LMB Create a stroke material.

- Shift - LMB Create a fill material.

- Shift - Ctrl - LMB Create both a stroke and fill material.

- Holding LMB and dragging accumulates the average color under the mouse cursor.

## Fill Tool

### Fill Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Fill

The Fill tool drops material into closed stroke areas automatically.

It works through any of the Grease Pencil Fill draw-mode brushes. Firing up a brush from an asset shelf or brush selector also flips on this tool for convenience.

### Tool Settings

### Brush Asset
The asset selector opens a pop-up asset browser where you pick the tool's active brush asset.

See Asset Operators for more information.

### Brush Settings
For convenience the brush's main settings are surfaced right in the Tool Settings.

Direction Ctrl
Which slice of the region to fill.

Normal :

Floods the inside of the shape sitting under the cursor.

Inverted :

Click outside the drawing and every shape bordering the cursor's region gets flooded.

Precision
Accuracy multiplier for the fill boundary; higher means more precise but slower.

Dilate/Contract
Pixel amount by which the fill grows or shrinks away from the stroke boundary.

Thickness
Boundary stroke's thickness radius, in pixels.

#### Advanced

Boundary
Chooses how the fill boundary limits get computed.

All :

Combine stroke thickness with the editing lines.

Strokes :

Lean on stroke thickness alone, ignoring edit lines.

Edit Lines :

Lean on the edit lines alone, ignoring strokes.

Show Lines (eye icon)
Flip on helper lines that reveal the fill boundary.

Layers
Picks which Layers supply the boundary strokes.

Visible :

Derives boundaries from every visible layer.

Active :

Derives boundaries from the active layer.

Layer Above :

Derives boundaries from the layer just above the active one.

Layer Below :

Derives boundaries from the layer just below the active one.

All Above :

Derives boundaries from every layer above the active one.

All Below :

Derives boundaries from every layer below the active one.

Simplify
How many simplify steps run on the boundary line; higher counts cut the precision of the filled region.

Ignore Transparent
Switch this on and transparent strokes are left out of the boundary math.

A value slider sets where the transparency threshold falls for a material.

Limit to Viewport
Switch this on and the fill reaches only the viewport's visible regions.

Auto-Remove Fill Guides
Switch this on and the guide strokes clear themselves away once a fill lands.

##### Gap Closure
Temporary lines spawned automatically to seal up gaps left in the strokes.

Size
Length of the extension line, or the circumference feeding the gap-closing calculation.

Mode S
Chooses which Gap closure method runs.

Radius :

Works out a closing line from the circle radius around the nearest open points.

Extend :

Stretches the open strokes out to bridge gaps.

Visual Aids
Flip on the closure-line helper display.

Strokes Collision D
Watches for extension lines hitting strokes and halts the extension at the first collision.

### Usage

### Selecting a Brush and Material
Over in the Tool Settings, pick the brush, material, and color type for the tool. The Fill tool runs on Fill Brush types. Brush Settings has more.

### Filling Areas
Click LMB inside a closed stroke area. The tool maps out the boundary on its own and makes a new closed stroke filled with the chosen material.

| Original Drawing.  | Use the fill tool to leak materials on closed areas.  | Final filled drawing.  |

### Fill Guides
Got a wide gap in a region you want filled? Add fill guides by hand, temporary helper lines that seal open shapes. To make one, press Alt - LMB and draw a line closing off the area you want.

| Original drawing.  | Add fill guide to close open areas (red lines).  | Use the Fill tool to leak material on the new closed area.  |

Once the fill looks right, remove the fill guide with the Clean Up tool found in the Grease Pencil Menu in Edit Mode.

### Automatic Gap Closure
For a hands-off way to seal gaps in a region you want filled, lean on temporary helper lines. Two methods exist, "Radius" and "Extend".

Radius draws temporary helper lines worked out from the radius of nearby open points to seal open shapes. Push the size above zero to govern the circle size over open points (the circle vanishes once the line shuts the gap). Click the region you want filled and tune the stroke length with PageUp PageDown or Wheel . Once the length suits you and the temporary strokes clearly cross, click again to fill.

| Original Drawing.  | Use Radius mode to close open areas (Red circles and cyan lines).  | Use Fill Tool to leak material on the new closed area.  |

Extend draws temporary helper lines by stretching the existing stroke ends out to seal open shapes. Push the size above zero to bring the extended lines into play, click the region you want filled, and tune the stroke length with PageUp / PageDown , Wheel , or a pen's MMB . Once the length suits you and the temporary strokes clearly cross, click again to fill.

| Original Drawing.  | Use Extend mode to close open areas (cyan lines).  | Use Fill Tool to leak material on the new closed area.  |

## Line Tool

### Line Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Line

Straight lines, drawn with any Draw type brush, are what the Line tool produces.

### Tool Settings

The brush's core settings sit right in the Tool Settings for handy access; Draw Brush documents that configuration.

Subdivisions
Count of stroke points placed along each edge of the stroke.

Thickness Profile
A curve widget governs how thick the stroke runs from its left start to its right end.

Use Curve
Enable it to let a curve profile steer thickness along the line.

### Brush Asset
Chooses which brush asset the tool draws with.

See Brush Asset for more information.

See Draw Brushes for a detailed list of all draw brushes and their options.

### Brush Settings
Parameters shaping how the stroke looks.

See Draw Brushes for details.

### Color
Settings that fix the stroke color.

See Color

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. Line relies on Draw Brush types. Brush Settings has more.

### Creating Lines

- Press down with LMB (or the Pen tip) where the shape begins, then drag.

- Let go at the spot where it should finish.

- Once released, drag the yellow manipulators to reposition either the start or the end point.

- Then confirm ( Return / MMB ) or cancel ( Esc / RMB ).

Mid-drag, Shift snaps the line to horizontal, vertical, or a 45° angle, while Alt builds the line outward from a center.

NumpadPlus and NumpadMinus or the mouse Wheel raise or lower how many points end up in the line.

F tunes line thickness; Shift - F tunes stroke opacity.

| click and dragging the start point.  | Moving start and end points with manipulators.  | The line after confirming.  |

### Extruding
Ahead of confirming, E drags the line's end point outward so you can chain lines together.

| End point extruding.  | Moving the end point of the last line with the manipulator.  | The connected lines after confirming.  |

## Polyline Tool

The Polyline tool generates multiple connected straight lines using any of the available Draw-type brushes.

**Tool Settings.**
Configure brush settings directly in the Tool Settings panel for convenience; see Draw Brush for full options.

Subdivisions — number of stroke points between each stroke edge.

Thickness Profile — a curve widget sets stroke thickness from the stroke start (left) to end (right).

Use Curve — when enabled, applies the curve profile to control thickness along the line.

**Brush Asset.** Selects the brush asset for the tool; see Brush Asset and Draw Brushes for details.

**Brush Settings.** Parameters control stroke appearance; see Draw Brushes documentation.

**Color.** Stroke color settings; see Color for configuration.

**Usage.**

To select a brush and material, open Tool Settings and pick the brush, material, and color type; the Polyline tool uses Draw Brush types (see Brush Settings).

To create polylines:
- Click (LMB or Pen tip) and drag the start point.
- Release at the desired end point.
- Click multiple times on different positions to create connected lines.
- Confirm with Return or MMB; cancel with Esc or RMB.

While dragging, Shift snaps the line to horizontal, vertical, or 45° angles. NumpadPlus and NumpadMinus (or mouse Wheel) adjust the point count in the final line. F adjusts line thickness; Shift+F adjusts opacity.

## Grease Pencil Menu

**Transform.**

Strokes can be edited by adjusting point positions.

Move, Rotate & Scale — accessible via Toolbar ‣ Move, Rotate, Scale; Menu ‣ Grease Pencil ‣ Transform ‣ Move, Rotate, Scale; or shortcuts G, R, S.

Points and strokes move (G), rotate (R), or scale (S) as described in Basic Transformations; Proportional Editing applies in Edit Mode.

Transform Snapping — basic move, rotate, and scale transformations for selected points or strokes (see Move, Rotate, Scale Basics).

Tools — accessible via Menu ‣ Grease Pencil ‣ Transform or Toolbar with Bend/Shear shortcuts. Bend, Shear, To Sphere, Extrude, and Shrink Fatten are covered in the Editing tools section.

**Mirror.**

Menu ‣ Grease Pencil ‣ Mirror; shortcut Ctrl+M. Behaves identically to mesh vertex mirroring.

**Snap.**

Menu ‣ Grease Pencil ‣ Snap; shortcut Shift+S. Mesh snapping applies to Grease Pencil components.

**Active Layer.**

Menu ‣ Grease Pencil ‣ Active Layer; shortcut Y. Selects the active layer.

**Animation.**

Menu ‣ Grease Pencil ‣ Animation; shortcut I. Stroke animation operations (see Animation section).

**Interpolate Sequence.**

Menu ‣ Grease Pencil ‣ Interpolate Sequence (see Interpolate Sequence).

**Duplicate.**

Menu ‣ Grease Pencil ‣ Duplicate; shortcut Shift+D. Duplicates selected elements as independent strokes at their original positions (unlike Extrude).

**Split.**

Menu ‣ Grease Pencil ‣ Split; shortcut V. Separates the selected curve portion into a new, independent segment that can be moved or edited without affecting the rest.

When a curve segment is selected, it splits off as a new editable curve. When only a single control point is selected, it duplicates as a loose point while the original stays attached.

**Copy.**

Menu ‣ Grease Pencil ‣ Copy; shortcut Ctrl+C. Copies selected points or strokes to the clipboard.

**Paste.**

Menu ‣ Grease Pencil ‣ Paste; shortcut Ctrl+V. Places Grease Pencil points or strokes from the internal clipboard into the active layer.

Paste on Back (Shift+Ctrl+V) — inserts pasted strokes behind all existing ones.

Keep World Transform — maintains the world-space position of clipboard strokes.

**Show/Hide.**

Adjusts visibility of points and strokes in the viewport.

Show All Layers — Menu ‣ Grease Pencil ‣ Show/Hide ‣ Show All Layers; shortcut Alt+H. Displays all Grease Pencil layers.

Hide Active Layer — Menu ‣ Grease Pencil ‣ Show/Hide ‣ Hide Active Layer; shortcut H. Conceals the active layer only.

Hide Inactive Layers — Menu ‣ Grease Pencil ‣ Show/Hide ‣ Hide Inactive Layers; shortcut Shift+H. Makes all non-active layers invisible.

**Separate.**

Menu ‣ Grease Pencil ‣ Separate; shortcut P. Creates new Grease Pencil objects based on criteria.

Selection — splits selected points or strokes into a new object.

By Material — each material becomes a separate object.

By Layer — each layer becomes a separate object (see 2D Layers).

**Clean Up.**

Tools to remove degenerate geometry.

Clean Loose Points — Menu ‣ Grease Pencil ‣ Clean Up ‣ Delete Loose Points. Eliminates strokes composed of very few points. Limit defines the point count below which a stroke is considered loose.

Delete Duplicate Frames — Menu ‣ Grease Pencil ‣ Clean Up ‣ Delete Duplicate Frames. Removes duplicate keyframes.

Merge by Distance — Menu ‣ Grease Pencil ‣ Clean Up ‣ Merge by Distance. Simplifies strokes by merging selected points closer than a specified distance.

Merge Distance — threshold for merging points.

Unselected — allows selected points to merge with unselected ones; when disabled, only selected points merge together. Note: selected points must be contiguous unless Unselected is enabled.

Reproject Strokes — Menu ‣ Grease Pencil ‣ Clean Up ‣ Reproject. When strokes are drawn unintentionally at different 3D depths but appear correct from a particular view or camera, Reproject flattens them from a chosen viewpoint.

Reprojected Type:
- Front: onto the front plane (XZ).
- Side: onto the side plane (YZ).
- Top: onto the top plane (XY).
- View: onto the current viewport.
- Surface: onto mesh surfaces.

Surface Offset — controls stroke offset from the object when Surface mode is active.

Cursor — reprojected onto 3D cursor rotation.

Keep Original — preserves the original strokes after applying the tool.

**Outline.**

Menu ‣ Grease Pencil ‣ Outline. Converts selected strokes into closed perimeter shapes, creating new strokes around the stroke boundary with adjustable thickness.

View — defines the projection method:
- View: current viewport perspective.
- Front: X-Z axes (front view).
- Side: Y-Z axes (side view).
- Top: X-Y axes (top view).
- Camera: active camera perspective.

Radius — sets outline thickness on both sides of the original stroke; higher values produce wider perimeters.

Offset Factor — scales the outline inward or outward:
- Positive values expand the perimeter away.
- Negative values contract it toward center.
- 0 places the perimeter directly on the original stroke.

Corner Subdivisions — subdivisions for smoothing corners at stroke endpoints and joints; higher values create smoother corners but increase complexity.

**Delete.**

Menu ‣ Grease Pencil ‣ Delete; shortcuts X, Delete. Opens a menu for removing geometry.

Strokes — Menu ‣ Grease Pencil ‣ Delete ‣ Strokes. Removes selected points; a stroke with only one point becomes invisible, and a stroke with all points removed is deleted entirely.

Only Strokes — Menu ‣ Grease Pencil ‣ Delete ‣ Only Strokes. Removes the stroke outline while preserving any fill geometry.

Only Fills — Menu ‣ Grease Pencil ‣ Delete ‣ Only Fills. Removes only fill components, leaving the stroke outline.

Dissolve — Menu ‣ Grease Pencil ‣ Delete ‣ Dissolve; shortcut Ctrl+X. Removes points between other points and reconnects the remaining ones.

Ctrl+X opens a menu to choose the dissolve type:
- Dissolve: removes selected points without splitting the stroke; remaining points stay connected.
- Dissolve Between: removes all points between selected points without splitting.
- Dissolve Unselect: removes all unselected points without splitting.

Delete Active Keyframe (Active Layer) — Menu ‣ Grease Pencil ‣ Delete ‣ Delete Active Keyframe (Active Layer). Wipes whatever strokes occupy the present frame on that one active layer.

Delete Active Keyframes (All Layers) — Menu ‣ Grease Pencil ‣ Delete ‣ Delete Active Keyframes (All Layers); shortcut Shift+Delete. Purges every stroke existing on this keyframe across all available layers.

## Selecting Grease Pencil Elements

**Select Mode.**

Edit Mode offers three selection modes accessible via header buttons or shortcuts 1, 2, 3.

Points — select individual points.

Strokes — select an entire stroke.

Segments — select all points between other strokes.

**Select All/None/Invert.**

Behaves identically to Object Mode.

**Select Random.**

Menu ‣ Select ‣ Select Random. Randomly selects unselected points or strokes.

Ratio — probability that an unselected element gets picked (not percentage count).

Random Seed — seed for the pseudo-random number generator.

Action — toggle between picking and unpicking elements.

**Select Alternated.**

Menu ‣ Select ‣ Select Alternated. Picks alternate points in selected strokes.

**Select More/Less.**

Menu ‣ Select ‣ More/Less; shortcuts Ctrl+NumpadPlus, Ctrl+NumpadMinus. Expands or shrinks the current selection within a stroke (never crossing stroke boundaries).

More — for each selected point, select all linked points (one or two adjacent ones).

Less — for each selected point, retain the selection only if every linked point is also selected; else remove it.

Hint: when all stroke points are picked, no change occurs (all linked ones are inherently selected, so More has nothing to add). Identical behavior occurs when no points are selected.

**By Stroke Type.**

Menu ‣ Select ‣ By Stroke Type. Selects curves based on type.

Type:
- Stroke: all stroke curves (outlines).
- Fill: all fill curves (enclosed filled shapes).

Deselect — when enabled, matching curves are deselected instead of selected.

**Select Similar.**

Menu ‣ Select ‣ Select Similar; shortcut Shift+G. Selects all strokes with similar characteristics.

Mode — the characteristic to compare:
- Layer: points/strokes with a similar layer index.
- Material: points/strokes with a similar material index.
- Vertex Color: points/strokes with a similar vertex color.
- Radius: points/strokes with a similar stroke radius.
- Opacity: points/strokes with a similar layer opacity.

Threshold — how closely characteristics must match.

**Select Fill.**

Menu ‣ Select ‣ Select Fill; shortcut Ctrl+L. Selects all curves belonging to the same fill region as the active curve.

Grease Pencil fills may consist of multiple boundary curves; this operator grows the selection to encompass all curves that bound the same enclosed fill area, valuable when transforming entire filled compositions.

**Select Linked.**

Menu ‣ Select ‣ Select Linked; shortcut L. Adds the cursor's nearest control point and all linked points (all points in the same stroke) to the selection.

**Select First/Last.**

Menu ‣ Select ‣ First/Last. Toggles selection of the first or last point(s) of strokes in the object, useful for quickly finding stroke starts.

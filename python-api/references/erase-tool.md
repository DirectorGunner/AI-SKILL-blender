# Erase Tool, Trim Tool, Pen, Sculpting Brushes ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Erase Tool; Trim Tool; Pen; Sculpting Brushes; Sculpting Tools; Vertex Paint Brushes; Vertex Paint Tools; Weight Paint Brushes; Weight Paint Tools; Weights Menu; Opacity Modifier; Tint Modifier; Lattice Modifier; Thickness Modifier; Texture Mapping Modifier; Length Modifier; Mirror Modifier; Multiple Strokes.

## Erase Tool

### Erase Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Brush

The Erase tool wipes away strokes you have already drawn.

It works through any of the Grease Pencil Erase draw-mode brushes. Firing up a brush from an asset shelf or brush selector also flips on this tool for convenience.

### Tool Settings

### Brush Asset
The asset selector opens a pop-up asset browser where you pick the tool's active brush asset.

See Asset Operators for more information.

### Brush Settings

Radius
Brush radius measured in pixels.

Tap F to resize on the fly by dragging the pointer, or punch in a number and confirm.

(Size Pressure)
With a Graphics Tablet, stylus pressure steers the radius.

Strength
Governs how hard the eraser eats into a stroke's transparency (alpha).

Set strength live with Shift - F in the 3D Viewport, moving the pointer and clicking LMB ; a typed value works as well.

(Strength Pressure)
With a Graphics Tablet, stylus pressure steers the strength.

Mode
Governs the way the erase tool acts.

Dissolve :

Playing the part of a raster eraser, this type whittles down a stroke's strength and thickness before any point actually disappears.

Point :

Remove a single point per pass.

Stroke :

Remove a whole stroke at once.

#### Cursor
Switch the cursor off with the checkbox in the Cursor pop-over menu.

### Usage

### Selecting a Brush
In the Tool Settings, pick the brush for the tool. The Erase tool runs on Erase Brush types (soft, point, and stroke).

### Dissolve Erasing

- Select an erase brush of type Soft/Hard.

- Adjust brush settings.

- Click and hold LMB or use the Pen tip to delete strokes on the viewport.

| Original drawing.  | The eraser affect the transparency of the strokes.  | Final result.  |

### Point Erasing

- Select an erase brush of type Point.

- Adjust brush settings.

- Click and hold LMB or use the Pen tip to delete strokes on the viewport.

| Original drawing.  | The eraser delete one point at a time.  | Final result.  |

### Stroke Erasing

- Select an erase brush of type Stroke.

- Adjust brush settings.

- Click and hold LMB or use the Pen tip to delete strokes on the viewport.

| Original drawing.  | The eraser delete one stroke at a time.  | Final result.  |

## Trim Tool

The Trim tool removes points where strokes intersect.

**Tool Settings.**

Flat Caps — marks newly created end caps as Flat.

Threshold — controls the threshold for detecting stroke intersections.

**Usage.**

Sketch a dotted lasso encircling the strokes to trim. Upon releasing, points along selected strokes get removed until the next intersection point is encountered.

## Pen

The Pen tool constructs and edits Bézier curves.

**Usage.**

Extrude Point — LMB click to create a new point extending from the currently selected one (Vector handle type); Shift+LMB creates an Auto-type point (morphs to Align upon handle movement).

Delete Point — Ctrl+LMB on any existing point removes it.

Insert Point — Ctrl+LMB on a curve segment places a new control point between two adjacent ones; Ctrl+LMB drag then steers the inserted point's handles.

Move Segment — LMB drag along a segment between control points to reshape the curve via handle adjustment without relocating control points.

Select Point — LMB to pick a single point or handle.

Move Point — LMB drag repositions existing points or handles; with an endpoint active, click-drag over empty space to extend and simultaneously shift the handle.

Close Stroke — click both endpoints to make the stroke cyclic.

Cycle Handle Type — double-LMB on the control point to rotate through all handle modes.

**Hotkeys.**

Free-Align Toggle — press LeftCtrl while dragging a handle to swap between Free and Align modes, enabling sharp corners.

Move Entire Point — press LeftAlt while dragging a handle to reposition the whole point.

Snap Handle Angle — press LeftShift while dragging to constrain handle motion to 45-degree increments (up/down, left/right, or diagonal).

**Tool Settings.**

Radius — governs the radius of freshly inserted points.

Stroke Placement — where along the stroke new points materialize.

Drawing Plane — which plane new points inhabit.

## Sculpting Brushes

Sculpt mode includes brushes bundled in the Essentials library; see Brush for details.

Smooth Stroke — flattens irregularities inside the brush region by homogenizing point spacing.

Thickness Stroke — expands or contracts point width inside the brush region.

Strength Stroke — heightens or diminishes point visibility (alpha) inside the brush region.

Randomize Stroke — injects variation into strokes inside the brush region by jittering point locations.

Grab Stroke — relocates a point cluster; uniquely, Grab samples the group on mouse-down then drags it, akin to Proportional Editing in Edit Mode.

Pull Stroke — displaces points along the direction of the brush movement.

Twist Stroke — spins points counter-clockwise (CCW) or clockwise (CW).

Pinch Stroke — draws points toward the brush center; Inflate (converse) pushes them outward.

Clone Stroke — pastes copies of clipboard strokes at the brush location; pre-copy strokes via Ctrl+C.

## Sculpting Tools

Sculpt mode toolbar options:

Brush — tool for accessing any of the sculpting brushes.

Annotate — sketch loose annotations.

Annotate Line — sketch straight-line annotations.

Annotate Polygon — sketch multi-sided annotations.

Annotate Eraser — remove drawn annotations.

## Vertex Paint Brushes

Vertex Paint mode includes brushes bundled in the Essentials library.

Paint Point Color — applies a chosen color across the object.

Blur Point Color — homogenizes adjacent vertex colors; the Color Value parameter is bypassed. Strength controls blur magnitude.

Average Point Color — blends color by depositing the mean hue from all colors inside the brush footprint.

Smear Point Color — displaces hues by grabbing and "pulling" them (finger-painting simulation).

Replace Point Color — alters color exclusively on stroke points that already bear a color.

## Vertex Paint Tools

Vertex Paint mode toolbar options:

Brush — interface for any of the vertex paint brushes.

Annotate — sketch loose annotations.

Annotate Line — sketch straight-line annotations.

Annotate Polygon — sketch multi-sided annotations.

Annotate Eraser — remove drawn annotations.

### Vertex Paint Tools

Brush
The principal tool for vertex paint brush application.

Annotate
Create handwritten notes.

Annotate Line
Create linear notes.

Annotate Polygon
Create multi-point notes.

Annotate Eraser
Remove existing notes.

## Weight Paint Brushes

Weight Paint mode includes brushes bundled in the Essentials library.

Paint Point Weight — applies a specified weight magnitude across strokes.

Blur Point Weight — diffuses the weight distribution of neighboring points; the Weight Value slot is omitted. Strength controls diffusion intensity.

Average Point Weight — even-outs weights by applying the mean weight from all weights in the brush footprint.

Smear Point Weight — displaces weights by grabbing and "pulling" them (finger-painting simulation).

## Weight Paint Tools

Weight Paint mode toolbar options:

For Grease Pencil Weight Paint workflows, each brush variant is available as a tool; modify the brush via Tool Settings; see Brush for specifics.

Brush — interface for any of the weight paint brushes.

Annotate — sketch loose annotations.

Annotate Line — sketch straight-line annotations.

Annotate Polygon — sketch multi-sided annotations.

Annotate Eraser — remove drawn annotations.

### Weight Paint Tools

Brush
Instrument for any weight brush task.

Gradient
Implements linear/radial weight gradient;
valuable when producing incremental weight shifts manually becomes cumbersome.
Merges selected vertex weights toward unselected vertices.

Example of the Gradient tool being used with selected vertices.

Weight
Gradient onset at the current brush value, fading away.

Strength
Reduced amounts allow blending into current weights (mirror brush).

Type
Gradient appearance.

Linear :
Straight-line form.

Radial :
Spherical form.

Note

These also activate through shortcuts as menu choices.

Sample

Weights
Locks the brush Weight to the weight beneath the pointer.
Acquired weight displays in the tool area.

Vertex Group
Lists options among groups under the pointer.

Annotate
Sketch annotation freely.

Annotate Line
Sketch linear annotation.

Annotate Polygon
Sketch polygon annotation.

Annotate Eraser
Remove sketched annotations.

## Weights Menu

**Normalize All.**

Menu ‣ Weights ‣ Normalize All. For each point, guarantees all vertex group weights sum to unity, normalizing all except those locked, which remain static.

Lock Active — keeps the active group's values unaltered while rescaling others.

**Normalize.**

Menu ‣ Weights ‣ Normalize. Acts exclusively on the active vertex group; all points preserve relative weight ratios, yet the overall magnitude scales so peak weight equals 1.0.

**Invert.**

Menu ‣ Weights ‣ Invert. Multiplies each weight in the selected vertex group by × -1.0.

Examples:
- Original 1.0 becomes 0.0
- Original 0.5 stays 0.5
- Original 0.0 becomes 1.0

**Smooth.**

Menu ‣ Weights ‣ Smooth. Diffuses the weights across the active vertex group.

**Sample Weight.**

Menu ‣ Weights ‣ Sample Weight; shortcut Shift+X. Syncs the Draw tool's Weight parameter to the vertex weight under the cursor.

## Opacity Modifier

The Opacity Modifier tweaks the opacity (alpha) value of stroke points. Alpha lodges per-point; the modifier rescales values from fully see-through to fully opaque.

**Options.**

Mode — the opacity transformation impacts stroke/fill output or stroke Hardness. When Hardness is active, opacity governs stroke fade (alpha) from interior to edge:
- Stroke & Fill, Stroke, Fill, or Hardness.

Uniform Opacity — when engaged, equalizes opacity throughout strokes.

Strength — fixed opacity for all stroke points.

Opacity Factor — steers stroke point opacity:
- 1.0 honors the source alpha.
- Below 1.0 amplifies transparency versus source.
- Above 1.0 amplifies opacity; 2.0 yields complete solidity.

**Influence.**

See Influence Filters.

## Tint Modifier

The Tint Modifier applies color to original stroke or fill with a selected color.

**Options.**

Mode — the color transformation applies to stroke and/or fill color:
- Stroke & Fill, Stroke, Fill.

Strength — regulates color mixing magnitude:
- 0 maintains the original stroke hue.
- 1.0 wholly substitutes tint for original.
- Above 1.0 reduces transparency versus source (2.0 yields full solidity).

Tint Type:
- Uniform: Color provides the tint for blending.
- Gradient: Color Ramp furnishes the tint gradient for blending (see Color Ramp Widget).

Object — a Data ID selecting an object (often an empty) whose transform locates the effect origin.

Radius — sets the radius of maximum effect spread.

**Influence.**

See Influence Filters.

## Lattice Modifier

The Lattice modifier reshapes the base object to match a Lattice object's topology.

Tip: quickly graft a Lattice Modifier onto selected targets by picking them, then picking the lattice last and hitting Ctrl+P, selecting Lattice Deform. This installs modifiers and links the targets as offspring to the lattice.

This documentation covers the Lattice Modifier specific to Grease Pencil. For other object types, check the general Lattice Modifier.

**Options.**

Object — the Lattice object governing the deformation.

Strength — mixes between undeformed and deformed point placements.

**Influence.**

See Influence Filters.

The Lattice modifier deforms meshes, curves, surfaces, text, lattices, and particles according to a Lattice object's shape.

Parenting objects to a lattice quickly adds this modifier.

Object specifies the Lattice object controlling deformation.

Vertex Group limits the effect to a specific mesh region.

Invert reverses the group influence.

Strength blends between original and deformed positions.

Lattice deformation suits several workflows:

For models with high vertex counts, direct Edit Mode manipulation is tedious. A lattice provides efficient large-scale deformation.

Smooth lattice-based deformation is difficult to achieve by hand.

A single lattice can deform multiple objects simultaneously.

Like all modifiers, it is non-destructive—changes layer on top of the original, allowing recovery and re-editing.

Lattices do not alter texture coordinates.

When lattices deform particles, the modifier stack order matters. Place Lattice after Particle System.

## Thickness Modifier

The Thickness Modifier tweaks stroke point width.

**Options.**

Uniform Thickness — when active, equalizes width throughout strokes.

Thickness — fixed width for all stroke points.

Thickness Factor — delta applied to each point's native width.

**Influence.**

See Influence Filters.

## Texture Mapping Modifier

The Texture Mapping Modifier repositions stroke texture UV coordinates.

**Options.**

Mode — which texture data to transform (stroke/fill or stroke alone):

Stroke:
- Fit Method: chooses the texture alignment approach.
  - Constant Length: texture preserves fixed length along strokes.
  - Stroke Length: texture rescales per stroke span.
- UV Offset: shifts the texture progression along strokes.
- Rotation: reorients stroke points.
  Note: Rotation limited to -90 through 90 degrees.
- Scale: texture magnitude scaling.

Fill:
- Fill Rotation: establishes texture orientation.
- Offset: moves texture center point (X, Y).
- Scale: texture magnitude scaling.

**Influence.**

See Influence Filters.

## Length Modifier

The Length Modifier shrinks or extends strokes.

Mode: Absolute measures length in geometry space. Relative uses stroke-length ratio.

Start: Length added at the stroke start; negative shrinks. End: Length added at the stroke end; negative shrinks. Used Length: Stroke portion used for extension direction.

Curvature: When enabled, extensions follow the stroke curve. Point Density: Multiplied by Start/End for total point count. Segment Influence: Controls how much individual segment length shapes overall curvature; higher factors reduce influence of short segments. Filter Angle: Ignores points deviating beyond this angle from neighbors during extrapolation. Invert: Reverses extension curvature.

Random Offsets: Random Offset Start/End adds variable length to stroke extremities. Random Noise Offset: Smoothly drifts each stroke's random value. Seed: Noise generation value.

Randomize: Re-calculates values by frame interval. Step: Frame count before recalculating.

Influence Filters: See Influence Filters.

## Mirror Modifier

The Mirror Modifier reflects strokes along chosen axes (X, Y, Z), centered at the Object Origin or at a specified object. When using another object as mirror center, that object's local axes apply instead.

Note: This documentation addresses Mirror Modifier for Grease Pencil. See the general Mirror Modifier for other types.

Axis: The axis perpendicular to the mirror plane. Mirroring along X inverts X-direction values. Multiple axes can be selected: one axis produces one mirror, two axes produce four mirrors, three axes produce eight. Object: A Data ID selecting an object (typically empty) whose position and rotation define mirror planes instead of the modified object's.

Influence: See Influence Filters.

## Multiple Strokes

The Multiple Strokes Modifier generates parallel copies around original strokes. Duplicates: Count of additional strokes. Distance: Spacing between original and duplicates. Offset: Inner/outer positioning for duplicates.

Fade: When active, copies fade via opacity or thickness. Center: Initial fade position. Thickness: Fade impact on thickness. Opacity: Fade impact on opacity.

Influence: See Influence Filters.

## Subdivide Modifier

The Subdivide Modifier adds points between existing ones, refining stroke geometry. Subdivision Type: Catmull-Clark subdivides and smooths. Simple subdivides without smoothing. Subdivisions: Recursive point addition count.

Influence: See Influence Filters.

## Flip Visual Effect

The Flip Visual Effect shows horizontally and/or vertically flipped appearance. Axis: Flip direction(s). Horizontal: Flips left-right. Vertical: Flips top-bottom.

## Shadow Visual Effect

The Shadow Visual Effect simulates shadow via displaced color silhouette behind the object.

Shadow Color: Shadow appearance. Offset X, Y: Displacement in pixels. Scale X, Y: Size scaling. Rotation: Object-center rotation (or Object Pivot). Object Pivot: Uses object as rotation center.

Blur—Blur X, Z: X/Z scale in pixels. Samples: Count (0 disables). Wave Effect: Distortion overlay. Orientation: Horizontal/vertical. Amplitude: Wave strength. Period: Cycle duration. Phase: Pattern shift.

Example: Simple Shadow, Blurred Shadow, Stretched shadow with empty pivot.

## Swirl Visual Effect

The Swirl Visual Effect creates swirling patterns with an object as the center. Object: Swirl center. Radius: Swirl external extent. Angle: Rotation (0 = none). Example: 0°, 15°, 45°, 90°.

## Wave Distortion Visual Effect

The Wave Distortion Visual Effect applies undulating distortion.

Orientation: Horizontal/vertical direction. Amplitude: Wave depth and intensity. Period: Cycle time. Phase: Pattern displacement. Example: 10 (horizontal), 30 (horizontal), 10 (vertical), 30 (vertical) amplitudes.

## Color Palette

### Color Palette

Color Palette.

Stashing a brush's color away for later reuse is what Color Palettes do. They come in handy when several colors are in play at once.

Palette
A Data-Block Menu to select a palette.

(New Pallet Color)
Adds the current brush's primary Color to the palette.

(Delete Pallet Color)
Removes the currently selected color from the palette.

/ (Move Pallet Color)
Moves the selected color up/down one position.

(Sort By)
Sort Colors by Hue, Saturation, Value, Luminance.

Color List
Every color in the palette shows up as a list entry. Click a color and the brush's primary Color switches to it.

### Shortcuts

- Ctrl - LMB brings up the color picker so you can change the color. See Color Picker.

- Backspace resets the value.

## Color Ramp Widget

### Color Ramp Widget

What a Color Ramp describes is a color gradient built from color stops, each carrying a position and a color. From those stops the gradient is worked out by interpolating between them with whichever interpolation method you pick.

Color ramp.

### Controls
Inserts a fresh stop midway between the selected stop and its predecessor.

Removes the selected color stop.

Tools
Holds further operators for the color ramp.

Flip Color Ramp
Reverses the gradient, mirroring where the stops sit.

Distribute Stops from Left
Spreads the stops so each step leaves equal room on its right. Pairs best with Constant interpolation mode.

Distribute Stops Evenly
Spreads the stops so the gap between every pair of neighbors is identical.

Eyedropper E
An Eyedropper for pulling a color or gradient off the interface into the color ramp.

Reset Color Ramp
Returns the color ramp to its default state.

Color Mode
Picks the Color Model that interpolation runs in.

RGB :

Mixes each channel separately and recombines them.

HSV/HSL :

Converts first to HSV or HSL, mixes there, then recombines. The payoff is that saturation holds across differing hues, where the RGB route would wash out — yielding a richer gradient.

Color Interpolation
Which interpolation method runs along the ramp.

RGB

B-Spline :

Uses a B-spline interpolation for the color stops.

Cardinal :

Uses a cardinal interpolation for the color stops.

Linear :

Uses a linear interpolation for the color stops.

Ease :

Uses an ease interpolation for the color stops.

Constant :

Uses a constant interpolation for the color stops.

HSV/HSL

Clockwise :

Clockwise interpolation around the HSV/HSL wheel.

Counter-Clockwise :

Counterclockwise around the HSV/HSL wheel.

Near :

Nearest route around the wheel.

Far :

Furthest route around the wheel.

HSV and HSL interpolation options.

Active Color Stop
The active stop's index (drawn as a dashed line). Hands you a fallback way to pick a stop when it crowds others too tightly to grab on its own.

Position
Where the selected color stop sits in the range is set by this slider.

Color
A color field for setting the chosen stop's color and alpha.

### Shortcuts

- LMB (drag) moves color stops.

- Ctrl - LMB (click) adds a new color stop.

## Other

This section covers curve editing tools not in edit menus.

Set Goal Weight:

Reference

Mode :

Edit Mode

Menu :

Context Menu ‣ Set Goal Weight

Set the Weight for a chosen control point.
Multiple selected points set the Mean Weight .

Add Vertex:

Reference

Mode :

Edit Mode

Shortcut :

Ctrl - RMB

Place new points interactively at the cursor with Ctrl - RMB .
Selection behaves like Extrude Curve and Move tool.

## Curve Primitives

Reference

Mode :

Object Mode and Edit Mode

Menu :

Add ‣ Curve

Shortcut :

Shift - A

See also

Adding curves follows the same patterns as other Objects.

Note

Primitive curves will eventually use the hair curve system.
Until then, feature differences will persist.

They convert interchangeably to access full editing and sculpting.

In Object/Edit Mode, the Add Curve menu provides these primitives:

Bézier Curve:

Adds an open 2D Bézier curve with two control points.

Bézier Circle:

Adds a closed, circular 2D Bézier curve (four control points).

NURBS Curve:

Adds an open 2D NURBS curve with four control points and Uniform knots.

NURBS Circle:

Adds a closed, circular 2D NURBS curve (eight control points).

Path:

Adds a NURBS open 3D curve made of five aligned control points,
with Endpoint knots and Curve Path enabled.

## Editing Curve Objects

Curves can be edited through sculpting.

Curves objects have foundational editing in "Edit Mode".

## Curve Structure

Splines form the backbone of curve geometry, determining the curve shape. A single curve object can hold multiple independent splines, analogous to multiple separate mesh islands within one mesh. Each spline's contour derives from its control points.

Three primary types exist: Poly, Bézier, and NURBS, each using a distinct formula for representing curves (covered in Spline Types below).

Splines consist of control points linked together. Selecting and moving these points adjusts the spline's form. This mirrors how vertices work in mesh editing.

Refer to Curve Editing for additional information.

Poly splines offer the simplest representation, with no smoothing between points. They match mesh-to-curve conversion precisely. While exact, they lack the fluidity of Bézier or NURBS.

Bézier splines combine control points with extended handles to define shape. Between two points lies one segment, with handles controlling the curvature.

In the diagram, the center of each pink line marks a control point, with handles extending outward. The arrows indicate the normal direction (how the curve is oriented).

A Bézier Curve in Edit Mode.

Four handle types exist, activated via V :

A Bézier Curve showing different handle types.

Automatic: The handles self-adjust for maximum smoothness, shown in yellow. Moving the handle converts it to Aligned.
Vector: Handles point straight toward neighbors, creating straight segments or corners, shown in green. Movement converts to Free.
Aligned: Handles stay collinear, preserving smooth curves across the point, shown in purple.
Free: Independent movement per handle, enabling asymmetric shapes, shown in black.

When a point is active, its handles highlight in red, masking their normal coloration. For instance, Vector (normally green) appears yellow when selected, risking confusion with Automatic.

To turn off this overlay, adjust colors in 3D Viewport ‣ Active Spline within Theme Preferences.

NURBS (Non-Uniform Rational B-Splines) are mathematically exact, capable of true precision. Unlike Bézier curves, which approximate (e.g., a Bézier circle approximates roundness), NURBS represent exact forms.

See Wikipedia for thorough coverage.

If all control points carry equal weight, their effects cancel. Variation in weight shifts the curve toward or away from specific points.

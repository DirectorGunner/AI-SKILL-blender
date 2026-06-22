# Interpolation, Animation Tools, Drawing Operations, Interpolate ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Interpolation; Animation Tools; Drawing Operations; Interpolate; Grease Pencil Object Modes; Options; Armature Modifier; Hook Modifier; Noise Modifier; Smooth Modifier; Time Offset Modifier; Build Modifier; Simplify Modifier; Multiframe.

## Interpolation

### Interpolation

### Interpolate

Reference

Mode :

Draw and Edit Modes

Tool :

Toolbar ‣ Interpolate

Shortcut :

Ctrl - E

For animating basic shapes, reach for the interpolate tool to drop in fresh breakdown keyframes for you.

The Interpolate tool page goes into the specifics.

### Interpolate Sequence

Reference

Mode :

Draw and Edit Modes

Menu :

Header ‣ Interpolate

Shortcut :

Shift - Ctrl - E

Fills the gap between the surrounding keyframes by generating a run of strokes across the intervening frames. Sit on any frame that falls between two keyframes, hit the sequence button, and a breakdown keyframe lands on every frame separating the previous keyframe from the next.

Step
How many frames apart the generated interpolated frames sit.

Layer
Confine the interpolation to either the Active or All layers.

Only Selected Edit Mode
Once active, the interpolation touches selected strokes only.

Exclude Breakdowns
Keep existing Breakdown keyframes from serving as interpolation extremes.

Flip Mode
Swap each stroke's start and end. Automatic tries to pick the correct mode per stroke on its own.

Smooth
How much smoothing gets applied to the interpolated strokes to cut down jitter and noise.

Iterations
How many smoothing passes run over the freshly made strokes.

Type
Which interpolation method drives the sequence.

## Animation Tools

### Animation Tools

### Insert Blank Keyframe (Active Layer)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Insert Blank Keyframe (Active Layer)

Shortcut :

Shift - I

Drops a fresh blank keyframe onto the active layer at the current frame. Should one already sit on the current frame, the new blank keyframe lands on the following frame instead.

All Layers
With this on, the blank keyframe goes onto every layer rather than just the active one.

Duration
Count of blank frames to insert.

### Insert Blank Keyframe (All Layers)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Insert Blank Keyframe (All Layers)

Behaves like Insert Blank Keyframe (Active Layer), only with All Layers switched on from the start.

### Duplicate Active Keyframe (Active Layer)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Duplicate Active Keyframe (Active Layer)

Takes the strokes on the most recent keyframe and copies them onto the current frame.

Mode
Choose which layers get duplicated.

Active :

Duplicate only the active layer.

All :

Duplicate all the layers.

### Duplicate Active Keyframe (All Layers)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Duplicate Active Keyframe (All Layers)

Behaves like Duplicate Active Keyframe (Active Layer), only with Mode preset to All.

### Delete Active Keyframe (Active Layer)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Delete Active Keyframe (Active Layer)

Shortcut :

Alt - I

Removes the last keyframe in the Dope Sheet, or the current one if you happen to be sitting on it.

Type
Choose which layer loses keyframes.

Active Frame :

Deletes current frame in the active layer.

All Active Frames :

Delete active frames for all layers.

### Delete Active Keyframe (All Layers)

Reference

Mode :

Draw Mode, Edit Mode, Sculpt Mode

Menu :

Stroke ‣ Animation ‣ Delete Active Keyframes (All Layers)

Shortcut :

Shift - Delete

Behaves like Duplicate Active Keyframe (Active Layer), only with Type preset to All Active Frames.

### Interpolate Sequence

Reference

Mode :

Draw Mode, Edit Mode

Menu :

Grease Pencil ‣ Interpolate Sequence

Shortcut :

Shift - Ctrl - E

Bridges the surrounding keyframes by generating strokes across the frames between them. A breakdown keyframe lands on every frame separating the previous keyframe from the next.

Step
Frame gap between generated interpolated frames.

Layer
Layers taken into the interpolation.

Exclude Break Downs
Keep existing Breakdown keyframes from serving as interpolation extremes.

Flip Mode
Reverse the destination stroke so its start and end line up with the source stroke.

Smooth
How much smoothing the interpolated strokes get, to trim jitter and noise.

Iterations
Count of smoothing passes over the freshly made strokes.

Type
Which interpolation method applies on the next Interpolate Sequence run.

### Bake Object Transform to Grease Pencil

Reference

Editor :

3D Viewport

Mode :

Object Mode

Menu :

Object ‣ Animation ‣ Bake Object Transform to Grease Pencil

Takes all Object-level transform animation across a chosen frame range and writes it into Grease Pencil object keyframes.

Start Frame, End Frame
Where the baking process starts and stops.

Step
Frame stride for the baking process.

Only Selected Keyframes
Convert only the selected keyframes.

Target Frame
Where the baked animation lands.

Projection Type
Picks the projection type for the converted strokes.

## Drawing Operations

### Drawing Operations

### Active Layer

Reference

Mode :

Draw Mode

Menu :

Draw ‣ Active Layer

Shortcut :

Y

Select the active layer.

### Animation

Reference

Mode :

Draw Mode

Menu :

Draw ‣ Animation

Shortcut :

I

The Animation section documents the stroke animation operations.

### Interpolate Sequence

Reference

Mode :

Draw Mode

Menu :

Draw ‣ Interpolate Sequence

See Interpolate Sequence.

### Erase Lasso

Reference

Mode :

Draw Mode

Shortcut :

Ctrl - Alt - RMB

Erase Lasso wipes out every Grease Pencil stroke caught inside a freeform selection.

- Hold Ctrl - Alt - RMB and trace a lasso around whatever you intend to erase.

- Let go of the mouse to commit the erase.

- Just the points that fall inside the lasso get cleared.

### Box Erase

Reference

Mode :

Draw Mode

Shortcut :

B

Box Erase clears every Grease Pencil stroke caught inside a rectangular selection.

- Hit B , then drag out a rectangle.

- Let go of the mouse to commit the erase.

- Every stroke point enclosed by the box gets cleared.

## Interpolate

### Interpolate

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Interpolate

By interpolating strokes across the previous and next Grease Pencil keyframes, the Interpolate tool builds an in-between keyframe. Sit on a frame between two keyframes, then click and drag to add a fresh breakdown keyframe whose stroke shape is set by how far you drag.

This hands artists manual say over how strokes shift from one pose or drawing to the next, with fine control over the result.

Note

Interpolating across curves of differing types triggers a priority system that settles which curve type wins. From highest priority to lowest: NURBS –> Bézier –> Catmull-Rom –> Polyline .

### Usage

Park the Timeline playhead at any frame sitting between two existing Grease Pencil keyframes. Then drag sideways in the viewport — the horizontal distance sets the blend amount — and let go to lock it in. A fresh breakdown keyframe appears, holding strokes blended between its two neighbours according to the amount you dialled in.

### Tool Settings

Layer
Hold interpolation to the Active Layer or All Layers .

Only Selected ( Edit Mode )
Once active, the interpolation touches selected strokes only.

Exclude Breakdowns
Keep existing Breakdown keyframes from serving as interpolation extremes.

Flip Mode
Flips the interpolation direction, trading the start and end strokes. Automatic mode tries to work out the right direction per stroke on its own.

Smooth
How much smoothing the interpolated strokes get, to cut jitter or visual noise.

Iterations
How many smoothing passes run over the freshly made strokes. Higher counts smooth more but can erode shape fidelity.

## Grease Pencil Object Modes

Grease Pencil offers specialized object modes for editing different aspects.

Draw Mode is where new strokes are created by directly sketching on a canvas using different tools and brushes.

Sculpt Mode deforms and shapes existing strokes organically; strokes can be smoothed, deformed, or reshaped for expressive, lifelike motion.

Edit Mode allows modifying individual strokes and points; fitting for line precision adjustment, shape refinement, and detail work.

Vertex Paint Mode applies color directly to stroke vertices; beneficial for creating shading, color gradients, and effects with granular control.

Weight Paint Mode applies vertex weights to strokes for rigging and animation workflows, enabling smooth and exact deformations tied to weight distribution.

Object Mode operates on the entire Grease Pencil asset as one unit for global transforms and placement within the scene graph.

## Options

**Auto Normalize.**

Guarantees all deforming vertex groups total one during painting. When disabled, each point's weight can be any value between 0 and 1. However, when vertex groups serve as deform groups for character animation, Blender interprets weights comparatively, always normalizing across all deform bones. Operationally, strict normalization is unnecessary, and weight normalization does not disrupt animation playback.

This toggle proves most useful when re-normalizing while painting atop weights previously normalized via a different method.

### Options

Paint options.

Brush operation shifts with these paint parameters.

Auto Normalize
Maintains deforming group sums at unity during painting.
Off mode permits any weight between 0 and 1 per vertex.
Yet when animation uses groups for deformation,
Blender interprets weights relative to neighbors.
Blender perpetually normalizes all deform bones.
Practically, strict normalization stays unnecessary and
post-painting normalization preserves animation.

Works intuitively maintaining normalization atop
already-normalized data via different sources.

Lock-Relative
Shows bone groups as if all locked deform groups vanished,
with remaining ones recalculated for unity.
Intended for perfecting bone balance while others stay locked.
Temporarily examine non-normalized weights as normalized
without permanent changes.

Multi-Paint
Simultaneously paint multiple chosen groups, sustaining their balance.
Beneficial when tweaking regions touched by beyond-three bones,
like particular character zones.

Only functional in the Armature area, where multiple groups
activate via multiple chosen bones. Two or more chosen groups
shift viewport hue and paint behavior to Multi-Paint,
pooling selected group totals if Auto Normalize runs,
or averaging otherwise. Strokes affecting collective influence
apply to each group so relative ratios endure.

Since undefined ratios arise from all-zero weights, Multi-Paint skips
zero-weight vertices on applicable groups.
It prevents reducing weight to complete zero.
Combined with X Mirror , complete symmetrical effect
occurs solely with initially symmetrical weights.

Tip

Though Multi-Paint skips zero-weight vertices by default,
Smooth Weight tool can transplant fitting nonzero balance
from neighbors without exiting Multi-Paint or changing choices.

Engage vertex selection, mark targets, and apply one smoothing cycle
from Selected Pose Bones with modest Factor.
Then simply paint to assign target influence.

Restrict
Narrows painting reach to vertices (including zero-weight
ones) in the chosen group.

See also

See the Brush Display options.

## Armature Modifier

The Armature Modifier erects skeletal rigs for pose animation of characters and other poseable assets.

Attaching an armature to an object enables automatic deformation, freeing geometry from hand-keyframing requirements.

See also: armature section for armature mechanics.

This documentation covers the Armature Modifier tailored to Grease Pencil objects. For other object types, consult the general Armature Modifier.

**Options.**

Object — the armature object referenced by this modifier.

Vertex Group — the object's vertex group whose weights regulate this modifier's blending with other Armature modifiers.

Applies only when at least two Armature modifiers coexist on the same object with Multi Modifier engaged.

Invert — reverses the vertex group's influence directivity (flips weight polarity).

Bind to:
- Vertex Groups: when active, bones by name deform points in vertex groups of the same name (e.g., a "forearm" bone affects only "forearm" group points). Influence scales with the point's group weight—precise but setup-intensive versus Bone Envelopes.
- Bone Envelopes: when active, bones warp adjacent points per each bone's envelope span and reach; switch on/off per deformation need.

The Armature modifier constructs skeletal rigs for posing and animating characters and deformable objects.

By binding an armature system to geometry, that shape deforms according to the rig's bone movements without manual vertex-by-vertex animation.

The modifier panel displays the armature object name.

Vertex Group restricts the modifier's output blending to vertices in a specified group—useful only when multiple Armature modifiers are active with Multi Modifier enabled.

Invert reverses the group's weight influence.

Preserve Volume uses quaternion-based deformation to prevent volume loss during high-angle rotations. Without it, geometry near joints shrinks as bones rotate far from rest position (nearly to zero at 180°). With it enabled, the geometry stays full but develops a discontinuity at exactly 180°.

Multi Modifier uses output from a previous modifier (typically another Armature) as its input, allowing multiple armatures to deform the same geometry independently rather than sequentially. Results mix using vertex-group weights as blending guides.

Armature modifiers can be quickly stacked by parenting objects to an armature.

Bind to selects how the armature links to the mesh.

Vertex Groups (for meshes and lattices): bones named identically to vertex groups deform only those group vertices, weighted by their values. This is precise but setup-intensive.

Bone Envelopes: bones deform nearby vertices within their envelope radius and falloff distance. Less precise but faster to set up.

When envelopes are disabled, existing vertex group names determine which bones are evaluated, reducing computational overhead. Removing unused groups is beneficial, especially when the mesh is used as a constraint target.

## Hook Modifier

The Hook Modifier warps stroke points by coupling them to another object (typically an empty or bone, yet any object suffices).

As the hook travels, it yanks points along—comparable to animated Proportional Editing in motion.

This documentation targets the Hook Modifier as implemented for Grease Pencil. For other object types, check the general Hook Modifier.

**Options.**

Object — the object to which points link.

Strength — tweaks hook potency on stroke points, ranging from 0.0 (inert) to 1.0 (point trails the hook).

**Falloff.**

Type — picks the Strength decay curve; author a custom profile for fine-grain governance.

Radius — the extent of hook influence.

Uniform Falloff — worthwhile when hooking scaled objects, especially if non-uniform scaling would distort the deformation.

**Influence.**

See Influence Filters.

Note: The Hook Modifier caches point indices from original strokes to define affected geometry; modifiers synthesizing new geometry (e.g., Subdivision Surface) must apply downstream of the Hook Modifier, otherwise their output sits outside the hook's reach.

The Hook modifier deforms meshes, curves, or lattices by tethering selected vertices to another object (typically an empty or bone). As the hook object moves, it pulls bound vertices along, similar to animated Proportional Editing.

Unlike shape keys, hooks lack fine per-vertex control but allow direct selection of vertices to manipulate.

In Edit Mode, use the Assign button on the modifier panel or the Add Hook menu to bind selected vertices.

Object specifies the hook object.

Vertex Group enables per-vertex influence weighting, useful for non-spherical falloff patterns.

Invert reverses the group effect.

Strength scales the hook's pull (0.0 to 1.0). Multiple hooks can affect the same vertices; this weight balances their relative influence.

Edit-Mode-only settings:

Reset recalculates and clears the hook's offset transformation.

Recenter moves the hook to the 3D Cursor position.

Select highlights all vertices affected by this hook.

Assign binds currently selected vertices to this hook.

Warning: the Hook modifier stores indices from the original mesh. Geometry-generating modifiers (Subdivision Surface) must appear after Hook in the stack, or newly created geometry will be excluded from the hook's influence.

Falloff Type adjusts how the hook's strength changes from its center to its Radius—see Proportional Editing for descriptions. A custom curve offers fine control.

Radius sets the influence distance.

Uniform Falloff is useful on scaled objects, especially with non-uniform scaling. Lattices benefit particularly, as non-uniform scaling is common for them.

## Noise Modifier

The Noise Modifier destabilizes stroke/point data (position, strength, thickness, UV texture placement) by layering fluctuating offsets that roughen the linework.

Stochastic amplitude can intensify the visual artifact.

**Options.**

Position — noise magnitude impacting point location.

Strength — noise magnitude impacting point strength (opacity).

Thickness — noise magnitude impacting point width.

UV — noise magnitude impacting point UV rotation.

Noise Scale — governs noise frequency bandwidth.

Noise Offset — shifts noise progression along strokes.

Seed — initialization for the pseudo-random sequence.

**Randomize.**

When engaged, noise draws from random values temporally.

Mode:
- Steps: fresh random value at regular intervals.
  Step — frame intervals before value changes.
- Keyframes: fresh random value exclusively on keyframe events.

**Influence.**

See Influence Filters.

## Smooth Modifier

The Smooth Modifier refines stroke/point data (location, strength, thickness, UV texture placement) by averaging to create flowing, continuous linework.

**Options.**

Affect — which stroke/point characteristics the smooth operation targets:
- Position: averages point spacing.
- Strength: averages point strength (opacity).
- Thickness: averages point width.
- UV: averages point UV rotation.

Factor — magnitude of smoothing applied per iteration.

Repeat — how many smoothing passes to execute, like running the Smooth tool repeatedly; excessive counts degrade playback frame rate (FPS).

Keep Shape — when active, the algorithm tries to retain the stroke's original silhouette.

Smooth Ends — averages the stroke's start and terminal points.

**Influence.**

See Influence Filters.

## Time Offset Modifier

The Time Offset Modifier shifts Grease Pencil keyframes along the animation timeline. When duplicating Grease Pencil objects, this modifier on duplicated versions can offset animations to achieve more organic appearances. Using this modifier, Grease Pencil ranges can be configured as looping sequences. Looped 2D animation traditionally features characters in motion, billowing smoke, or cascading precipitation. In Fixed Frame mode, the modifier allows individual drawings to appear independent of where the playhead sits on the timeline. This is useful when you want certain graphics to display repeatedly throughout your sequence—such as switching among several predefined mouth positions.

Mode: Regular offsets keyframes in forward playback direction (left to right). Reverse offsets in backward playback (right to left). Fixed Frame displays the frame set by the Frame parameter, which must be animated for onscreen changes during playback. Ping Pong loops animation back and forth. Chain combines the modes sequentially. Repeat sets the number of cycle repeats. Frame Offset is the number of frames to shift from the original keyframes. Scale governs frame playback speed, where 1 matches standard frame rate; positive values speed up, negative ones slow down. Keep Loop repositions the final frame to the animation start to sustain continuity.

Custom Range: When active, animation playback occurs only within specified frame boundaries. Frame Start/End define the range limits.

Influence: See Influence Filters.

## Build Modifier

The Build Modifier animates strokes to appear or vanish across a frame range, producing the illusion of lines being drawn or erased.

Note: This documentation addresses Build Modifier for Grease Pencil. Refer to the general Build Modifier for other object types.

Mode: Sequential—one stroke changes at a time. Concurrent—multiple strokes change together. Additive—only newly added strokes animate compared to the prior keyframe, assuming Additive Drawing was used and shared strokes remain identical.

Transition (Sequential/Concurrent): Grow reveals points in order, simulating drawing. Shrink hides points backward, simulating erasure. Vanish conceals points forward, simulating fading ink.

Timing: Natural Drawing Speed uses recorded stylus speed (Sequential/Additive only); Speed Factor multiplies recorded velocity. Maximum Gap sets longest gap in seconds. Number of Frames: Fixed frame count for animation. Frames: Maximum frame count used. Delay: Frames to wait after each keyframe before the modifier activates. Percentage Factor: Manual visibility percentage (0–1 range). Factor: Visibility percentage. Time Alignment (Concurrent only): Align Start means all strokes begin together. Align End means all strokes finish together. Object: Stroke appearance order based on distance to a reference object.

Custom Range: If enabled, affects only the specified frame interval. Start/End: Range frame values.

Fade: Factor defines fade strength. Thickness: Fade applied to thickness. Opacity: Fade applied to opacity. Weight Output: Assigns weight values to points finishing/beginning fade.

Influence Filters: See Influence Filters.

This modifier sequences the appearance or disappearance of object faces over a time interval, advancing by default in creation order (changeable via Sort Mesh Elements in Edit Mode).

Start Frame marks when the building process begins.

Length specifies the number of frames for the build sequence.

Reversed inverts the effect, causing a deconstruction where faces progressively vanish; useful for gradually hiding sets of instanced objects.

Randomize shuffles the order in which faces build.

Seed controls the randomization pattern; the same seed always produces the same sequence for a given mesh.

Common use: instancing vertices from a vertex-only mesh with the Build modifier creates a workaround for semi-random item layouts (leaves, balls on a surface) without particle system limitations like clustering and gaps.

## Simplify Modifier

The Simplify Modifier reduces point count in strokes while maintaining shape. Applying this modifier improves viewport performance during animation.

Mode: Fixed alternates point deletion (start/end exempt). Iterations: Repetition count. Adaptive: RDP algorithm (Ramer-Douglas-Peucker) deletes points while preserving shape. Factor: Algorithm recursion depth. Sample: Recreates with fixed point spacing. Length: Distance between points; smaller requires more, larger requires fewer. Sharp Threshold: Preserves corners sharper than threshold. Merge: Combines nearby points. Distance: Merge threshold.

Influence: See Influence Filters.

Example: Original, Iteration 1, Iteration 2, Iteration 3 shown. Also: Factor 0.1, Factor 0.5, Factor 1.0 shown.

## Multiframe

Multiframe pop-over shows the control. Multiframe enables drawing, editing, sculpting, or weight painting across multiple frames simultaneously, invaluable for animation tasks repeating per-frame.

Use Falloff: Effects decrease from current frame per a curve. Usage: Select desired keyframes. Activate Multiframe in the 3D Viewport header (toggle icon—faded lines). Once active: Select points across keyframes and edit. Sculpt—brushes affect all selected-keyframe strokes. Weight paint—affects all strokes. Draw—new strokes appear in all; Fill applies everywhere. During interpolation, select strokes in order for correct pair calculation.

Note: Not all operators support Multiframe.

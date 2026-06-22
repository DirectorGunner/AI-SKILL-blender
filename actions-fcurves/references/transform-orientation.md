# Transform Orientation, Editing Dopesheet Data, Action Editor, Mask ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Transform Orientation; Editing Dopesheet Data; Action Editor; Mask; Shape Key Editor; Sidebar; Drivers Editor.

## Transform Orientation

The Transform Orientation sets the orientation of the Object Gizmo, and changing it can make transforming in your intended direction easier. Reference — Mode: Object and Edit Modes; Panel: Header ‣ Transform Orientation; Shortcut: Comma. (With the default Global orientation it's tricky to move a plane in the direction it faces, but with Local it's easy.) Change the orientation via the selector in the 3D Viewport's header, or temporarily during a hotkey transformation using axis locking — e.g. press G to start moving, X to lock to the orientation's X axis, then X again to lock to an alternative orientation: Local if it was Global before, and Global otherwise. Besides the built-in orientations, you can define your own (see Custom Orientations). Orientations — Global (align the axes to world space, shown by the Navigation Gizmo in the top-right corner and the Grid Floor); Local (align the axes to the active object's orientation); Normal (in Edit Mode, orient the axes so the gizmo's Z axis matches the average Normal of the selected elements — in Object Mode this equals Local); Gimbal (orient the axes to visualize the object's Rotation Mode, especially useful for Euler modes where the object rotates one axis at a time, so the rotation axes don't stay perpendicular and may even overlap, the phenomenon called gimbal lock that complicates animation); View (align the axes to the view, so they change as you orbit — X: Left/Right, Y: Up/Down, Z: Towards/Away from the screen); Cursor (align to the 3D Cursor); and Parent (align to the Parent). Custom Orientations (Reference — Mode: Object and Edit Modes; Panel: Header ‣ Transform Orientation): define custom orientations from objects or mesh elements — one from an object uses that object's Local orientation, while one from mesh elements (vertices, edges, faces) uses those elements' average Normal orientation. The Transform Orientation panel in the 3D Viewport header selects, adds, removes, and renames orientations, and a new one's default name derives from the selection (an object takes its name, an edge is titled "Edge," and so on). Create Orientation: select an object or mesh element(s) and click the "+" button in the panel; right after, the Create Orientation Adjust Last Operation panel offers Name (a text field for the new orientation), Use View (align the new orientation to view space), Use After Creation (keep the new orientation selected), and Overwrite Previous (if the new orientation reuses an existing name, a suffix is added to avoid overwriting unless this is checked, in which case it overwrites). Delete Orientation: select it and click the × button.

## Editing Dopesheet Data

Select Menu — see also Selecting.
All (A) — selects every keyframe.
None (Alt-A) — deselects every keyframe.
Invert (Ctrl-I) — flips the selection.
Box Select (B) — drag a box to select the keyframes within it.
Box Select (Axis Range) (Alt-B) — drag a box to select keyframes in the matching time range, even those above or below the box.
Circle Select (C) — shows a circle at the cursor that you drag across keyframes to select them.
Lasso Select (Ctrl-RMB) — draw a freehand shape to select the keyframes inside it.
More (Ctrl-NumpadPlus) — grows the selection to take in the time-neighbors of the currently selected keys.
Less (Ctrl-NumpadMinus) — drops keyframes that have fewer than two selected neighbors.
Select Linked (L) — selects keys sharing a channel with an already-selected key.
Columns on Selected Keys (K) — selects keys on the same frame as an already-selected key.
Column on Current Frame (Ctrl-K) — selects every key on the current frame.
Columns on Selected Markers (Shift-K) — selects keys sharing a frame with a selected marker.
Between Selected Markers (Alt-K) — selects keys falling between the leftmost and rightmost selected markers.
Before Current Frame ([) — selects keys at or before the current frame; you can also Shift-Ctrl-LMB anywhere left of the Playhead.
After Current Frame (]) — selects keys at or after the current frame; you can also Shift-Ctrl-LMB anywhere right of the Playhead.

Marker Menu — markers flag frames that carry key points or notable events in an animation and, as in most animation editors, appear along the bottom. A few options are exclusive to the Dope Sheet editor:
Sync Markers — whether moving the selected keyframes also moves the selected markers.
Show Pose Markers (Action Editor) — shows the local pose markers (which exist only inside the action) rather than the global scene markers; while it's active, the Add Marker item likewise produces pose markers in place of scene ones.
Make Markers Local (Action Editor) — turns the selected scene markers into pose markers, so they appear only inside the currently selected action.
For the rest of the marker tools, see Editing Markers.

Channel Menu — see Graph Editor Channels.

Key Menu — most of this menu is documented on the Graph Editor's Editing F-Curves page. One key difference: scaling keyframes in the Dope Sheet Editor shifts them only along the time axis (with the Playhead as pivot) and leaves their values untouched. The Dope Sheet adds these items:
Slide (Shift-T) — stretches one set of keyframes across time while squeezing an adjacent set to compensate, keeping the total duration the same. To use it, first select three or more keyframes, drop the cursor somewhere in the middle, and press Shift-T; the range temporarily splits in two at the cursor, marked by a dashed vertical line, and moving the mouse lengthens or shortens the two halves while their keyframes follow along. Confirm with LMB or back out with RMB.
Keyframe Type (R) — assigns a type to the selected keyframes.

Snap — the toggle button enables or disables automatic keyframe snapping, and the dropdown shows a popover:
Snap To — the kind of element to snap to. Frame snaps to whole frames; Second snaps to seconds; Nearest Marker snaps to the closest Marker.
Absolute Time Snap — when off, keyframes move in increments of Snap To; e.g. with Second chosen and a key currently at 0:06+5, dragging right snaps it to 0:07+5 — its time grows by a second while its 5-frame subsecond offset stays put. When on, keyframes snap to multiples of Snap To, so in that same example the key lands on 0:07+0, dropping the subsecond offset.

Proportional Editing — see Proportional Editing.

## Action Editor

Where Dope Sheet mode works with the keyframes of every animation in the scene at once, Action Editor mode narrows to the keyframes within a single action.

Actions serve as Blender's containers for animation data; objects, like other animatable data-blocks, point at actions to be animated by the data they hold, a data-block can reference one action as its active action plus more through Nonlinear Animation tracks.

Header:
Note: the Previous/Next Layer (down/up arrow) operators were dropped from the UI in 4.4 and are slated for full removal in 5.0 (see #119626).
Action — a data-block menu for changing — or clearing — the object's active action.
Slot Display Name — the slot's name for display in the interface; combined with the slot's data-block type it stays unique inside its Action.

Action Menu:
Note: the "Merge Animation" and "Separate Slots" operators act only on directly-assigned actions and skip actions referenced by NLA strips.
Merge Animation — folds the animation of every selected object into the active object's animation. Because the data is moved rather than copied, the source Actions can wind up empty and userless. This merges not just the object-level Action but Actions on related data-blocks too (see Related data-blocks), so it can also merge the Actions of a single object — for example Translation & Rotation together with Shape Key animation.
Separate Slots — splits all Slots of the active object's Action into separate Actions; every user of those Slots is reassigned to its respective Action, and the new Actions take their names from the Slots. The source Action isn't deleted but may end with 0 users if no Fake User is set.
Replace Action — pops up so you can choose another action; the operator then finds all data-blocks using the active object's action and replaces it on each with your choice. This skips the action on NLA strips and action constraints — to replace those, see Remap Users.
Replace with New Action — makes a new Action (a duplicate of the current one) and points all users of the current Action at it. It ignores NLA Strips and Action Constraints.
Move Slots to new Action — moves the Slots selected in the Channels Region into a brand-new Action and reassigns all their users to it; with more than one Slot selected, they all go into a single Action.
Push Down Action — makes a new NLA track beneath the Action Track and shifts the active action into it, equivalent to hitting Push Down Action over in the NLA editor.
Stash Action — makes a new muted NLA track at the bottom of the NLA stack and shifts the active action there, effectively setting it aside and disabling it so it stops affecting the animation; later you can unmute it or delete it. Clicking New Action in an object's data-block menu when it already has an active action stashes the previous one automatically.
Note: both Push Down and Stash leave the object with no active action (so the Action Editor goes empty and the action can no longer be edited). To keep editing the action, pick it in the NLA editor and hit Tab to drop into Tweak Mode.

## Mask

This mode lists every mask in the blend-file that has at least one layer and lets you adjust their keyframes.

## Shape Key Editor

The Shape Key Editor shows the active object's shape keys and lets you create and tune keyframes for their influence values. It's a specialized Dope Sheet mode aimed squarely at shape-key animation. Each row stands for one shape key, and each keyframe marker marks a point where that key's value shifts over time, giving an efficient way to time and polish facial expressions, morph targets, and other shape-key-driven mesh deformations. Further shape-key properties — names, values, relative settings — can be viewed and edited in the Sidebar.

Usage:
Use the editor to keyframe shape-key influences over time.
Tune timing by moving or scaling keyframes right in the timeline.
Pair it with other Dope Sheet modes (the Action Editor, say) for involved character-animation workflows.
See also Shape Key Basics for how to create and manage shape keys.

## Sidebar

Action Panel — while the editor sits in Action Editor mode, or in Dope Sheet mode with a selected channel that belongs to an action, this panel lets you change some of that action's settings (see Action Properties).

Custom Properties — create and manage your own properties to stash data in the action's data block; see the Custom Properties page.

Edited Action — Reference: Panel: Sidebar ‣ Edited Action. Holds settings for the object's active action; visible only when the Action Track is selected.
Action — a data-block menu to view, change, and clear the active action (see also the Action Editor's Action).
Slot — which slot within the active action to use.
Extrapolation — decides whether the action influences the frames before/after its bounds once it's pushed down into a strip. (While it's still the active action, Hold applies regardless of the choice.)
  Hold — the values from the action's first keyframe extend back over the earlier frames (if the strip is first in the track), and the values from its last keyframe extend forward over the later ones (up to the next strip).
  Hold Forward — only the last keyframe's values carry to later frames (up to the next strip).
  Nothing — the animated properties revert to their defaults outside the strip's bounds.
Blending — how the action's values combine with those of the tracks below.
  Replace — overwrites the lower tracks' values; with Influence under 1, a linear interpolation between the old and new values is used instead.
  Multiply, Subtract, Add — combines the action's values with the lower tracks' by a simple calculation; with Influence under 1, a linear interpolation between the old values and the calculated ones is used.
  \(result = mix(previous, previous (+-×) value, influence)\)
  Combine — picks one of the following automatically per property type:
  Axis/Angle Rotation: \(result = previous + value × influence\) — which averages the axis while summing the rotation amounts.
  Quaternion Rotation — quaternion math runs on all four channels at once: \(result = {previous} × {value} ^ {influence}\)
  Proportional (Scale): \(result = previous × (value / default) ^ {influence}\)
  Others: \(result = previous + (value - default) × {influence}\)
  Note: since this mode relies on quaternion multiplication for the Quaternion Rotation properties, every one of the four channels is driven during playback, and Insert Single Keyframe must lay down all four keys; other channel types can still be keyed on their own.
Influence — the action's contribution to the NLA stack's overall result.

Strip:
Name — the strip's name.
Mute (checkbox) — unchecked, the strip stops contributing to the animation and shows a dotted outline.

Active Strip — Reference: Panel: Sidebar ‣ Strip ‣ Active Strip. Holds common strip properties.
Frame Start — the frame the strip begins on; changing it moves the strip while keeping its duration.
Frame End — the frame the strip ends on; changing it also changes the Action Clip Frame End, cropping or extending the action. To speed it up or slow it down instead, scale it via Strip ‣ Transform ‣ Scale or the Playback Scale setting.
Extrapolation — see Extrapolation.
Blending — see Blending.
Blend In, Out — how many frames the strip's influence takes to ramp up at the start and wind down at the end.
Auto Blend In/Out — computes Blend In/Out automatically from the strips in the track above or below that overlap this one in time.
Playback:
  Reversed — plays the strip backwards.
  Cyclic Strip Time — whether the Animated Strip Time loops back to the beginning once it runs past the Action Clip Frame End.
Animated Influence — lets you set, and animate, how strongly the strip affects the animation, an alternative to the (Auto) Blend In/Out settings. To set an influence keyframe, enter a value and then either pick Insert Keyframe from its context menu or hover over it and press I; the keyframes show in, e.g., the Graph Editor.
Animated Strip Time — lets you set, and animate, the frame at which the underlying action is sampled. Note: despite the name Strip Time, its value is a frame inside the action, not inside the strip — for an action spanning frames 1 to 50 referenced by a strip spanning 101 to 150, you'd put the Strip Time at 1, not 101, to land on the first keyframe. Combined with Cyclic Strip Time, this lets the action's keyframes play several times within one strip: if the action's keys lie between frames 1 and 50 and you animate the strip time to run 1 to 100 instead, they play twice (at double speed). In practice, though, the Repeat setting below is easier.

Action Clip — Reference: Panel: Sidebar region ‣ Strip ‣ Action Clip. Holds properties specific to Action strips.
Action — the action the strip references.
Slot — which slot within the action to use.
Frame Start, End — how much of the action to use; adjusting these crops or extends the action (and the strip, since its Frame End shifts accordingly), and extending it brings F-Curve Extrapolation into play. One handy case is cyclic animation where the action's first and last keyframes share a value (so the value lasts two frames on restart): lowering the Frame End drops the last keyframe so the value lasts only one frame.
Sync Length — on leaving Tweak Mode, automatically pins Frame Start/End to the action's first and last keyframe.
Now — snaps Frame Start/End to the action's first and last keyframe immediately.
Playback Scale — plays the animation faster (scale < 1) or slower (scale > 1) than the original action.
Repeat — plays the action several times.

Action — Reference: Panel: Sidebar region ‣ Strip ‣ Action. See Action Properties.

Modifiers — Reference: Panel: Sidebar region ‣ Modifiers. Strip modifiers let you make non-destructive changes to every curve inside the strip's action. See F-Curve Modifiers.

## Drivers Editor

This editor is where you set up Drivers, which compute a property's value from other properties — letting a set of source properties "drive" a target property, an alternative to animating that property by hand.

Its interface largely matches the Graph Editor's, with two notable differences:
The Sidebar gains an extra Drivers tab, where the source properties are brought together to compute an intermediate value for the target property.
The curve plots not the property's value over time but a mapping from that intermediate value (X axis) to the final value (Y axis).

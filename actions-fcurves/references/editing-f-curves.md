# Editing F Curves, Editors, Editing Strips, Track ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing F-Curves; Editors; Editing Strips; Track; Strips.

## Editing F-Curves

Transform — Reference: Mode: Edit Mode; Menu: Key ‣ Transform. You edit an F-Curve by transforming where its keyframes sit.
Move, Rotate, Scale — like other Blender elements, keyframes can be moved, rotated, and scaled as covered in Basic Transformations.
Extend (E) — quickly shifts whichever selected keyframes lie on one side of the Playhead, handy when, say, you need to push everything after a certain time to the right to clear room. To use it, select some or all keyframes, put the pointer left or right of the Playhead, press E, move the mouse to drag only the keyframes on that side, and confirm with LMB (or cancel with RMB).
Tip: for exact figures you can also edit the Key Frame and Value properties in Sidebar ‣ F-Curve ‣ Active Keyframe. While transforming, hold Shift to move keyframes more slowly for precision, or Ctrl to move them in coarse steps.

Snap — Reference: Menu: Key ‣ Snap; Shortcut: Shift-S. Besides this menu's snapping operators, you can also switch snapping on in the header.
Selection to Current Frame — sets the selected keyframes' time to the current frame.
Selection to Cursor Value — sets the selected keyframes' value to the 2D Cursor's.
Selection to Nearest Frame — rounds each keyframe's time to the nearest frame.
Selection to Nearest Second — rounds each keyframe's time to the nearest second; Use Timecode shows seconds rather than frames at the editor's top.
Selection to Nearest Marker — sets each keyframe's time to the nearest marker's.
Flatten Handles — flattens the Bézier handles of the selected keyframes.
Equalize Handles — gives the selected keyframes' handles equal length.
  Side — which handles to touch (left, right, or both).
  Handle Length — the length to give the selected keyframes' Bézier handles.
  Flatten — sets the handle values equal to their own keyframes.
Cursor to Selected (Ctrl-G) — sends the 2D Cursor to the mean time and value across the picked keyframes.
Cursor Value to Selection — sets the 2D Cursor's value to the picked keyframes' mean value.

Mirror — Reference: Menu: Key ‣ Mirror; Shortcut: Ctrl-M. Mirrors the selected keyframes about a reference point.
By Times over Current Frame — mirrors horizontally about the current frame.
By Values over Cursor Value — mirrors vertically about the 2D Cursor's value.
By Times over Zero Time — mirrors horizontally about frame 0.
By Values over Zero Value — mirrors vertically about value 0.
By Times over First Selected Marker — mirrors horizontally about the first selected marker.

Jump to Selected — Reference: Menu: Key ‣ Jump to Selected; Shortcut: Ctrl-G. Parks the 2D Cursor at the mean time and value of the picked keyframes.

Insert — Reference: Menu: Key ‣ Insert; Shortcut: I. Adds new keyframes and selects them, leaving any previously selected ones selected too.
All Channels — keys every visible, editable F-Curve at its current value.
Only Selected Channels — keys the selected F-Curves at their current value.
Only Active F-Curve — keys the active F-Curve at its current value.
Active Channels at Cursor — keys the active F-Curve at the 2D Cursor's value.
Selected Channels at Cursor — keys the selected F-Curves at the 2D Cursor's value.

Copy/Paste — Reference: Menu: Key ‣ Copy, Key ‣ Paste; Shortcut: Ctrl-C, Ctrl-V. Ctrl-C copies the selected keyframes, Ctrl-V pastes them; afterward the Adjust Last Operation panel adds options:
Frame Offset — shifts the pasted keyframes horizontally so that… Frame Start (the first lands on the current frame), Frame End (the last lands on the current frame), Frame Relative (they keep the same distance from the current frame as when copied), or No Offset (they stay at their original frames).
Value Offset — shifts the pasted keyframes vertically so that… Left Key (the first takes the value of the existing key left of the Playhead), Right Key (the last takes the value of the key right of the Playhead), Current Frame Value (the first takes the curve's value at the current frame), Cursor Value (the first takes the 2D Cursor's value), or No Offset (they keep their original values).
Type — Mix (blends the pasted keyframes with existing ones, overwriting only those sharing a frame), Overwrite All (clears all prior keyframes in the target F-Curves), Overwrite Range (within each F-Curve, removes existing keys lying within the range of the keys pasted into it), Overwrite Entire Range (within each F-Curve, removes existing keys within the combined range of all pasted keys).
Flipped — if you copied keys from one or more pairs of symmetrically opposite bones, this pastes the left bones' keys into the right bones' curves and vice versa, inverting the values to mirror the animation.

Duplicate — Reference: Menu: Key ‣ Duplicate; Shortcut: Shift-D. Duplicates the selected keyframes; reposition them by moving the mouse.

Delete — Reference: Menu: Key ‣ Delete; Shortcut: X, Delete. X or Delete opens a pop-up for deleting the selected keyframes.

Handle Type — Reference: Menu: Key ‣ Handle Type; Shortcut: V. Sets the handle type of the selected keyframes.

Interpolation Mode — Reference: Menu: Key ‣ Interpolation Mode; Shortcut: T. Sets the selected keyframes' interpolation mode, which governs how the curve runs from each keyframe to the next.

Easing Type — Reference: Menu: Key ‣ Easing Type; Shortcut: Ctrl-E. Sets the selected keyframes' easing mode, which decides whether easing touches the left, the right, or both ends of each segment running from one keyframe to the next.

Density:
Decimate — Reference: Menu: Key ‣ Density ‣ Decimate (Ratio), Key ‣ Density ‣ Decimate (Allowed Change). Simplifies an F-Curve by dropping the keyframes that least affect its shape.
  Mode — how to decide how many keyframes to delete.
  Ratio — deletes a set percentage of keyframes.
  Remove — the percentage to remove.
  Error Margin — deletes as many keyframes as it can while keeping the F-Curve's shape within a set tolerance.
  Max Error Margin — how far the decimated curve may stray from the original.
Bake Keyframes — Reference: Menu: Key ‣ Density ‣ Bake Keyframes; Shortcut: Shift-Alt-O. Drops a keyframe on every frame. See also Bake Channels, which adds options for which range to bake and how.
Clean Keyframes — Reference: Menu: Key ‣ Density ‣ Clean Keyframes; Shortcut: X. Hunts down redundant keyframes among the selected ones and deletes them; a keyframe counts as redundant when it matches its neighbors' value, even if the surrounding curve segments aren't flat. Tip: it tends to alter the affected curves' shape, so run it after, e.g., bulk keyframe insertion across all an armature's bones (which leaves useless keys on bones that didn't move) and before hand-tweaking the curves.
  Threshold — the value threshold; raise it to also delete keys that nearly match their neighbors.
  Channels — cleans all keyframes (even unselected ones) in the selected F-Curves; a curve left with a single keyframe is deleted outright.

Blend — Reference: Menu: Key ‣ Blend; Shortcut: Alt-D. Nudges the selected keyframes' values by a percentage: pick a blending operator, move the mouse left or right to set the factor, and confirm with LMB (or cancel with RMB). Several blending operators work off "neighboring keyframes," meaning they split the selection into contiguous groups and reference the unselected keys just before and after each group.
Breakdown — Reference: Menu: Key ‣ Blend ‣ Breakdown. Sets the selected keyframes to an interpolation of their neighbors.
  Factor — at -1 the keys take the left neighbor's value; at 1 the right neighbor's; in between they interpolate, 0 sitting dead center.
Blend to Neighbor — Reference: Menu: Key ‣ Blend ‣ Blend to Neighbor. Moves each selected keyframe a percentage of the way toward its left or right neighbor's value.
  Blend — negative moves each key Blend percent toward the left neighbor; positive toward the right; zero keeps the originals.
Blend to Default Value — Reference: Menu: Key ‣ Blend ‣ Blend to Default Value. Moves the selected keyframes a percentage toward the property's default value.
  Factor — how far to shift, from 0 (no change) to 1 (full reset to default).
  See also the Reset to Default operator, which resets any property to its default without keyframing.
Ease — Reference: Menu: Key ‣ Blend ‣ Ease. Bends the selected keyframes onto an S-curve. While the slider shows (after activating but before confirming with LMB), press Tab to switch which setting you're editing:
  Curve Bend — negative weights the left side, positive the right, 0 gives a balanced curve.
  Sharpness — low gives a near-straight diagonal, high gives a steep rise/drop.
Blend Offset — Reference: Menu: Key ‣ Blend ‣ Blend Offset. Shifts the selected keyframes up or down by one shared amount until the first/last one meets the left/right neighbor.
  Offset Factor — at -1 the first selected key aligns to its left neighbor; at 1 the last aligns to its right neighbor; at 0 nothing moves.
Blend to Ease — Reference: Menu: Key ‣ Blend ‣ Blend to Ease. Blends the selected keys toward an "ease in" or "ease out" curve.
  Blend — at -1 the keys follow an "ease in" curve (small changes early, large changes late); at 1 an "ease out" curve (large early, small late); at 0 nothing moves.
Match Slope — Reference: Menu: Key ‣ Blend ‣ Match Slope. Blends the selected keys toward a straight line drawn through two keys just outside the selection.
  Factor — negative uses the two keys left of the selection, positive the keys to the right, zero changes nothing.
Push Pull — Reference: Menu: Key ‣ Blend ‣ Push Pull. Moves the selected keys toward or away from the straight line through the first and last selected key.
  Factor — at 0 the keys land on the straight line.

At 1 they stay where they are; at 2 each key ends up twice the distance from that line it had before.

Shear Keys — Reference: Menu: Key ‣ Blend ‣ Shear Keys. Shears the selected keyframes — changing each value by an amount that grows the further it lies in time from a reference keyframe. The reference defaults to the leftmost selected key, but pressing D switches to the rightmost.
  Shear Factor — how much to shear; negatives push keyframes down, positives push them up.
  Direction — whether the leftmost or rightmost selected keyframe is the reference.

Scale Average — Reference: Menu: Key ‣ Blend ‣ Scale Average. Scales the selected keyframes vertically about their average value.
  Factor — at 0 the keyframes all collapse to the average value; at 1 they stay put; at 2 each ends up twice the distance from the average it had before.

Scale from Neighbor — Reference: Menu: Key ‣ Blend ‣ Scale from Neighbor. Scales the selected keyframes vertically about a keyframe just outside the selection; that pivot defaults to the left neighbor, but pressing D uses the right one.
  Factor — the scale factor.
  Reference Key — whether the left or right neighbor is the pivot.

Time Offset — Reference: Menu: Key ‣ Blend ‣ Time Offset. Shifts the selected keyframes' values so the resulting F-Curve looks like it's traveling through time; works best with dense keyframes. As the curve runs off one end of the selected time range, it wraps in at the other, offset vertically so the ends meet without a jump.
  Frame Offset — by how many frames to slide the F-Curve; the slider caps at -10 … 10, but you can type larger numbers.

Smooth — Reference: Menu: Key ‣ Smooth; Shortcut: Alt-S.
Smooth (Gaussian) — Reference: Menu: Key ‣ Smooth ‣ Smooth (Gaussian). Smooths the selected keyframes with a Gaussian kernel: click the item, move the mouse left or right to set strength, and confirm with LMB (or cancel with RMB).
  Factor — how strongly to smooth.
  Sigma — the Gaussian distribution's shape; lower values sharpen it, weighting nearby keys more, while a high value acts like a plain average filter.
  Filter Width — a wider filter takes in more keyframes for a smoother result; at width 1 it only weighs the immediate left and right neighbors.
Smooth (Legacy) — Reference: Menu: Key ‣ Smooth ‣ Smooth (Legacy); Shortcut: Alt-O. Another way to smooth the selected curves, but beware: its algorithm appears to halve the gap between each keyframe and the curve's average linear value, which smooths quite hard. The first and last keys seem never to be touched.
Butterworth Smooth — Reference: Menu: Key ‣ Smooth ‣ Butterworth Smooth. Smooths the selected keyframes with a Butterworth filter: click the item, move the mouse left or right to set the frequency, and confirm with LMB (or cancel with RMB). It's great for smoothing large amounts of data because it keeps the animation's peaks, though it can add a ripple where key values change fast.
  Frequency Cutoff — lower means smoother; there's an implicit ceiling, at half the sample rate, beyond which it no longer changes the curve, the sample rate being the scene frame rate times this operator's Samples per Frame.
  Filter order — higher makes the frequency cutoff steeper.
  Samples per Frame — before filtering, the curve is resampled at this interval to avoid errors from uneven frame spacing; if keys land on subframes (a 60fps file in a 30fps scene, say), raise this to 2.
  Blend — a 0-to-1 value blending the original curve with the smoothed one.
  Blend In/Out — how many frames at the start and end to blend between original and smoothed, which can soften jumps at the selection's edge; at value 1 it locks just the first and last frames of the selection to their originals.

## Editors

Blender ships a range of editors for viewing and changing different kinds of data. An Editor lives inside an Area, which fixes its size and place within the Blender window, and any area can host any editor type. The Editor Type selector — the first button at the left of a header — switches the editor in that area, and you can have the same editor type open in several areas at once. See User Interface for the general interface docs.
General.
Animation.
Scripting.
Data.

## Editing Strips

Transform — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Transform.
Move (G) — shifts the selected strips in time or onto a different track.
Extend (E) — quickly moves whichever selected strips sit on one side of the Playhead, handy when, say, you need to push everything after a certain time to the right to clear room. Select some or all strips, put the pointer left or right of the Playhead, press E, move the mouse to drag only the strips on that side, and confirm with LMB (or cancel with RMB). A strip straddling the Playhead has only its start or end moved, again depending on the pointer's side.
Scale (S) — scales the selected strips about the Playhead.
Swap — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Transform ‣ Swap; Shortcut: Alt-F. Swaps the order of the selected strips within their track.
Move Up — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Transform ‣ Move Up; Shortcut: PageUp. Moves the selected strips up a track when there's room.
Move Down — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Transform ‣ Move Down; Shortcut: PageDown. Moves the selected strips down a track when there's room.

Snap — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Snap.
Selection to Current Frame — moves the selected strips' start to the current frame.
Selection to Nearest Frame — moves their start to the nearest whole frame.
Selection to Nearest Second — moves their start to the nearest second.
Selection to Nearest Marker — moves their start to the nearest marker.

Split — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Split; Shortcut: Y. Cuts the selected strips in two at the current frame.

Duplicate — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Duplicate; Shortcut: Alt-D. Copies the selected strips, duplicating any actions they reference, so editing a copy's keyframes leaves the original untouched.

Linked Duplicate — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Linked Duplicate; Shortcut: Shift-D. Copies the selected strips while reusing the actions they reference, so editing a copy's keyframes also changes the original (and vice versa); Blender flags this by highlighting the other strip in red.

Delete — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Delete; Shortcut: Delete, X. Removes the selected NLA-Strips.

Make Meta — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Make Meta; Shortcut: Ctrl-G. Groups the selected NLA-strips into a meta strip.

Remove Meta — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Remove Meta; Shortcut: Ctrl-Alt-G. Ungroups the selected meta strips, putting their contents back in place.

Toggle Muting — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Toggle Muting; Shortcut: H. Mutes or unmutes the selected strips; muted ones get a dotted border and stop affecting the animation.

Bake Action — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Bake Action. Also Reference: Editor: 3D Viewport; Mode: Object and Pose Modes; Menu: Header ‣ Object ‣ Animation ‣ Bake Action…. An object's or bone's final motion comes not only from keyframed animation but also from F-Curve modifiers, drivers, and constraints; Bake Action computes that final motion and lays down a keyframe on every scene frame. It's handy for adding variation to a cyclic action like a Walk Cycle, or for turning drivers or constraints into keyframe animation.
  Start Frame — the first frame to bake.
  End Frame — the last frame to bake.
  Frame Step — how many frames to skip ahead between baked frames.
  Only Selected Bones — keys only the selected bones (Pose baking only).
  Visual Keying — keys from the final transformations, with constraints applied.
  Clear Constraints — strips all constraints from the keyed objects/bones and does "visual" keying.
  Clear Parents — bakes the animation onto the object then clears parents (objects only).
  Overwrite Current Action — bakes into the current action rather than a new one (handy for baking only some bones of an armature).
  Clean Curves — removes redundant keys after baking.
  Bake Data — which transforms to bake: Pose (bone transforms) or Object (object transforms).
  Channels — which channels to bake: Location, Rotation, Scale, B-Bone, or Custom Properties.

Apply Scale — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Apply Scale; Shortcut: Ctrl-A. Bakes the selected strips' scale into their referenced actions.

Clear Scale — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Clear Scale; Shortcut: Alt-S. Resets the selected strips' scale.

Sync Action Length — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Sync Action Length. Resets a strip's length to its underlying action's, so it plays only from the action's first keyframe to its last. See also the Sidebar's Sync Length Now button, which does the same.

Make Single User — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Make Single User; Shortcut: U. Duplicates actions as needed so each selected strip gets its own action used by no others, letting you edit a strip's keyframes without touching the rest of the animation.

Note: this doesn't recurse into meta strips.

Start Editing Stashed Action — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Start Editing Stashed Action; Shortcut: Shift-Tab. Enters Tweak Mode for the selected strip's action so its keyframes can be edited in, e.g., the Graph Editor, and marks the strip's track as Solo, muting every other track so they stop influencing the animation and you can focus solely on the action at hand. Despite the name's "stashed (muted)" wording — which just reflects the usual case — it works on unmuted actions too. When done, click Strip ‣ Stop Editing Stashed Action or press Shift-Tab again.

Start Tweaking Strips Actions (Full Stack) — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Start Tweaking Strips Actions (Full Stack); Shortcut: Tab. Enters Tweak Mode for the selected strip's action so its keyframes can be edited, leaving every other track on so you still see their effects while you work. When done, click Strip ‣ Stop Tweaking Strips Actions or press Tab again. Note: for transitions sitting above the tweaked strip, keyframe remapping breaks down for any channel values the transition affects; the way around it is to tweak the active strip while skipping evaluation of the upper NLA stack.

Start Tweaking Strips Actions (Lower Stack) — Reference: Editor: Nonlinear Animation; Menu: Strip ‣ Start Tweaking Strips Actions (Lower Stack). Enters Tweak Mode for the selected strip's action so its keyframes can be edited, muting any tracks above the current one so they don't influence the animation while you work. When done, click Strip ‣ Stop Tweaking Strips Actions or press Tab.

## Track

Add — Reference: Editor: Nonlinear Animation; Menu: Track ‣ Add. Adds a new track beneath the Action Track.

Add Above Selected — Reference: Editor: Nonlinear Animation; Menu: Track ‣ Add Above Selected. Adds a new track above each selected one.

Delete Tracks — Reference: Editor: Nonlinear Animation; Menu: Track ‣ Delete; Shortcut: Delete, X. Removes the selected tracks and their strips. When using the shortcuts, keep the pointer over the track region, or Blender will only delete the selected strips instead.

Move — Reference: Editor: Nonlinear Animation; Menu: Track ‣ Move.
To Top (Shift-PageUp) — moves the selected tracks to the top.
Up (PageUp) — moves them up by one.
Down (PageDown) — moves them down by one.
To Bottom (Shift-PageDown) — moves them to the bottom.
When using the shortcuts, keep the pointer over the track region, or Blender will move the selected strips to other tracks rather than moving the tracks.

Remove Empty Animation Data — Reference: Editor: Nonlinear Animation; Menu: Track ‣ Remove Empty Animation Data. Drops objects with no drivers, NLA tracks, or active action from the NLA editor to cut clutter — essentially the reverse of Add ‣ Selected Objects.

## Strips

A strip says when something happens in the animation and for how long. A few types exist, described below.

Action Strips — this kind of strip plays back the keyframes held in an action. Create one with Add ‣ Action, or by clicking Push Down Action in the NLA's Action Track, which builds a strip from the object's active action. Several strips can reference the same action, so editing one set of keyframes can change multiple parts of the animation at once. A strip may be shorter than its underlying action (by cropping, speeding up, or both) or longer (by extending, slowing down, or both); see the Sidebar for details.

Transition Strips — a transition strip interpolates between two neighboring action strips: select them and click Add ‣ Transition.

Sound Strips — these control when a Speaker Objects begins playing its audio; playback runs the length of the audio file and ignores the sound strip's length.

Meta Strips — a meta strip bundles other strips so you can move, scale, and copy them as one unit.

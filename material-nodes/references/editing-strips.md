# Editing Strips (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Editing Strips

### Controls

### Overlap Mode

Overlap Mode determines what happens when you move a strip to overlap another.

Expand :

Strips to the right shift forward in time to make room for the moved strip.

Overwrite :

The overlapped strip gets overwritten, trimmed, or divided by the overlapping one.

Shuffle :

The overlapping strip relocates to the nearest vacant area to avoid collision.

### Snapping

Toggle snapping by clicking (Snap Off) / (Snap On) in the header, or hold Ctrl while dragging a strip.

The dropdown menu provides:

Snap to

Frame Range
Aligns with start and end frames of the play/scene range or, inside a Meta Strip, the meta boundaries.

Current Frame
Aligns the selection with the Playhead.

Hold Offset
Aligns the selection with the Hold Offset.

Markers
Aligns the selection with Markers.

Retiming Keys
Aligns the selection with Retiming Keys.

Ignore

Muted Strips
Muted items do not act as snap targets.

Sound Strips
Audio items do not act as snap targets.

### Transform

### Move

Reference

Menu :

Strip ‣ Transform ‣ Move

Shortcut :

G

Press G to start moving selected strip(s).
Drag left/right to shift temporal position.
Drag up/down to change channel.

Holding Ctrl toggles snap on or off while dragging.

Lock movement to time via X or to channel via Y.

Drag strips with LMB to move them; currently only one strip can be moved at a time this way.

#### Start Frame Offset

Click LMB on the left edge of the strip to adjust its start frame.
Hold or press G and move the mouse left/right to shift the starting frame by the distance moved.
The label below the strip shows the start frame.

- A 20-image sequence can be offset by clicking the left edge right by 10 frames, skipping the first 10 images.
Useful for trimming unwanted openings.

- Dragging the left edge leftward extends the start with duplicates of the first frame.
Good for adding transition space at the beginning.

#### End Frame

Click LMB on the right edge to adjust when the strip stops.
Hold or press G and move the mouse to shift the end frame.
The label above the strip displays the end frame.

- Drag the right edge left to shorten; trailing frames are omitted. Removes unwanted endings quickly.

- Drag the right edge right to lengthen.
For video and image sequences, additional content displays up to the source limit.
If extended past the source, the last frame repeats.
Use for outgoing transitions.

Note

Multiple selection

You can pick several (edges of) strips by Shift - LMB clicking: pressing G then moves everything with your cursor—meaning you might move one strip, shorten two others, and extend another.

### Move/Extend from Current Frame

Reference

Menu :

Strip ‣ Transform ‣ Move/Extend from Current Frame

Shortcut :

E

Press E with multiple selections to stretch or shrink them interactively.
Similar to dragging, but designed for duration tweaks relative to playback position.

Handles nearest the cursor move as a group, enabling you to adjust strip extent near the playhead.

Hint

Extending streamlines rough edits like "animatics" (sketch-storyboard sequences).
Select everything and adjust lengths around the playhead.
Handy when audio or other timing changes need accommodation.

You might want to turn on Markers ‣ Sync Markers during this task.

This saves the work of picking strips on one side and edges on overlapping strips, then manually shifting markers. Adjusting edits becomes much faster.

### Slip Strip Contents

Reference

Menu :

Strip ‣ Transform ‣ Slip Strip Contents

Shortcut :

S

Slip Strip Contents shifts where a strip begins pulling from its source without moving or resizing the strip itself.
Useful for showing a different part of the source material.

Commonly applied when the strip's place in the cut matters but you want to show different source frames.

Offset
How many frames to advance (positive) or go back (negative) in the content.

Slip Keyframes
When on, keyframes tied to strip properties (like opacity or position) shift with the content. Turn off to keep keyframes in place.

Usage

Move your mouse left or right to shift content, then execute.
More choices appear during the action:

- Confirm : LMB , Return , Spacebar

- Cancel : Esc , RMB

- Precision Mode : Hold Shift for subframe sliding of audio.
Subframe amount shows as Sound Offset in the header.

- Clamp : Hit C to keep slipping within strip bounds.

### Snap Strips to the Current Frame

Reference

Menu :

Strip ‣ Transform ‣ Snap Strips to the Current Frame

Shortcut :

Shift - S

Locks selected items to the playhead location.
The highest strip serves as anchor; cursor proximity to the playhead determines which side aligns.

Using the menu, click LMB left or right of the playhead to specify alignment direction.

Frame
The frame for snapping.

Snap Side
Which edge snaps when no edges are selected.

Keep Offset
Enabled: strips move together, keeping their spacing.
Disabled: each strip snaps individually.

### Clear Strip Offset

Reference

Menu :

Strip ‣ Transform ‣ Clear Strip Offset

Shortcut :

Alt - O

Returns soft start/end handles to their factory state.

### Swap Strip

Reference

Menu :

Strip ‣ Transform ‣ Swap Strip

Left Alt - Left
Trades places with the left neighbor.

Right Alt - Right
Trades places with the right neighbor.

### Remove Gaps

Reference

Menu :

Strip ‣ Transform ‣ Remove Gaps

Shortcut :

Backspace

Deletes silence between the playhead and the first strip leftward.
Works regardless of what is selected or locked.

All Gaps
Also removes gaps to the right.

### Remove Gaps (All)

Reference

Menu :

Strip ‣ Transform ‣ Remove Gaps (All)

Same as Remove Gaps with All Gaps turned on.

### Insert Gaps

Reference

Menu :

Strip ‣ Transform ‣ Insert Gaps

Shortcut :

Shift - Equals

Creates silence between the playhead and the strips rightward.
Unaffected by current selection or strip locking.

### Retiming Keys

You can control playback speed by inserting and repositioning retiming points. These give frame-level control independent of strip length.

Note

- Speed changes only affect the strip itself, not embedded animations.

- Retime controls cannot be used on effects.

Hint

Hit R and enter a number for quick speed adjustment of selected strips.

Selecting Retiming Keys

Keys show as inactive by default.
To pick them, enable Show Retiming Keys.
You can also toggle them with Toggle Retiming Keys.

Use Shift+LMB to select many at once with box select. Box select targets keys only if one is already selected; otherwise it selects strips.

Ctrl - LMB picks all keys to the right of one you choose.

Moving Retiming Keys

Drag keys with the mouse or press G. Each key maps to a specific frame, so moving it shifts that frame's position and speeds up or slows down playback.

Moving one key does not shift others inside the strip. For multiple adjustments, pick all the keys in that region. Keys outside the visible strip bounds move with the edge keys to preserve adjustments.

### Add Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Retiming Key

Click the retiming menu or hit I and choose Add Retiming Key to place one at playback position.
Boundary points form automatically—they are always required.

With points selected, strips lose selection, yet you may still insert additional ones.
New points bind to any strip already containing a selected point.

### Add Freeze Frame and Slide

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Freeze Frame and Slide

A frozen frame halts playback at a given point indefinitely.
Access it via the retiming dropdown or context menu.

Note

Smooth transitions entering or exiting a frozen state are unsupported.

### Add Speed Transition and Slide

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Speed Transition and Slide

Build a ramp between different playback rates.
Select a retiming point between zones with mismatched speeds, then open the menu or context and pick Add Speed Transition.
Coupled points form, moving opposite each other.
Adjusting their position shifts the transition span.

### Delete Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Delete Retiming Keys

Erase a point via Delete or X.
When removed, the strip's span remains unchanged; playback velocity averages the adjacent zones.

Note

Erasing a transition reverts it to a basic retiming point.

### Reset Retiming

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Reset Retiming

Restores the strip to standard timing.

### Set Speed

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Set Speed

Adjusts the playback pace of a timed section.

Speed
Ratio relative to the source.

Preserve Current retiming
Keeps surrounding retiming segments at their current speeds by modifying the overall strip Duration instead.

### Toggle Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Toggle Retiming Keys

Shortcut :

Ctrl - R

Activates the Show Retiming Keys strip attribute.
Allows keys to become visible and editable.

### Split

Reference

Menu :

Strip ‣ Split

Shortcut :

K

Divides the active strip into two at the playhead.
Both pieces use the source, spanning the original timing.

Hint

Think of this as quickly copying the strip and trimming the copies to show non-overlapping content from the source.

### Hold Split

Reference

Menu :

Strip ‣ Hold Split

Shortcut :

Shift - K

Similar to Split, creates two separate pieces, but the endpoints cannot be dragged to reveal frames past the division.

You can enter values for Hold Offset in the Strip Info panel instead.

Hint

Imagine splitting the video file itself, replacing the strip with the two resulting pieces.

### Duplicate

Reference

Menu :

Strip ‣ Duplicate

Shortcut :

Shift - D

Produce a copy that stands alone; position it in time and channel, then release LMB.

If the strip references an asset like a scene, duplication also duplicates that asset and uses the copy in the new strip.

### Duplicate Linked

Reference

Menu :

Strip ‣ Duplicate Linked

Shortcut :

Alt - D

Produce a linked copy; place it in time and channel, then click LMB.

If the strip points to an asset like a scene, the copy references the original asset.

### Delete

Reference

Menu :

Strip ‣ Delete

Shortcut :

Delete , X

Remove the active strip(s).

### Update Scene Frame Range

Reference

Menu :

Strip ‣ Update Scene Frame Range

For Scene strips—Updates the strip's Time settings to match the scene's frame range.
Use this when a scene's span has expanded or contracted.

### Separate Images

Reference

Menu :

Strip ‣ Separate Images

Shortcut :

Y

For image sequences—Divides the strip into separate pieces, one per frame.
Great for slideshows and scenarios with individual, non-sequential images.

Length
Set how long each new strip should run.

### Movie Strip

### Set Render Size

Reference

Menu :

Strip ‣ Set Render Size

Matches the render output dimensions and aspect to the strip's resolution.

### Deinterlace Movies

Reference

Menu :

Strip ‣ Deinterlace Movies

Converts interlaced footage to progressive.

### Effect Strip

### Change Effect Type

Reference

Menu :

Strip ‣ Effect Strip ‣ Change Effect Type

Substitutes the active effect for a different type with identical input counts.

Retains current inputs and settings when feasible, speeding up effect swaps without rebuilding.

You can switch between matching effects like Cross, Gamma Cross, and Wipe, each accepting two sources.

### Reassign Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Reassign Inputs

Shortcut :

R

Reconnect effect strips in new ways.
Pick three arbitrary strips and press R.
If no loop forms, a fresh effect connects them.

### Swap Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Swap Inputs

Shortcut :

Alt - S

Reverses the first two effect inputs.

### Lock/Mute

Lock Strips Ctrl - H
Disables movement of the strip.

Unlock Strips Ctrl - Alt - H
Re-enables movement.

Mute/Unmute Strips H , Alt - H
Silence or restore sound for selected strips.

Mute/Unmute Deselected Strips Shift - H , Shift - Alt - H
Silence or restore sound for all but the selected.

### Inputs

Reload Strips Alt - R
Refreshes strips from disk.

Reload Strips and Adjust Length Shift - Alt - R
Refreshes strips from disk and updates strip span.

Change Path/Files
Alters the source for a selected strip.

Swap Data
Trades content between two strips.

### Image Menu

### Clear

#### Position

Reference

Menu :

Image ‣ Clear ‣ Position

Sets strip Position Transforms to zero.

#### Scale

Reference

Menu :

Image ‣ Clear ‣ Scale

Sets strip Scale Transforms to one.

#### Rotation

Reference

Menu :

Image ‣ Clear ‣ Rotation

Sets strip Rotation Transform to zero.

#### All Transforms

Reference

Menu :

Strip ‣ Clear ‣ All Transforms

Resets position, scale, and rotation back to defaults.

### Apply

#### Scale to Fit

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fit

Adjusts Scale so content fills the project's Resolution while keeping the original proportions.

Clear areas may appear at the edges to fit content correctly.

#### Scale to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fill

Adjusts Scale so content spans the project's Resolution while keeping the original proportions.

Some content may fall outside the rendered frame.

#### Stretch to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Stretch to Fill

Adjusts Scale to occupy the entire project Resolution.
Note this method does not maintain aspect ratio.

Content may distort to fit the frame.

### Context Menu

Right-click in the timeline to open quick-access options.

### Fades

Reference

Menu :

Add ‣ Fades

This submenu holds fade controls.
With visual content, opacity animates; with audio, volume animates.

Clear Fades
Removes fade from selected strips.

Fade In and Out
Applies fade in and out to selected strips.

Fade In
Applies fade in to selected strips.

Fade Out
Applies fade out to selected strips.

From Current Frame
Fades from the playhead to where overlapping clips end.

To Current Frame
Fades from overlapping clip starts to the playhead.

- Clamp : Hit C to restrict slipping to strip limits.

### Snap Strips to the Current Frame

Reference

Menu :

Strip ‣ Transform ‣ Snap Strips to the Current Frame

Shortcut :

Shift - S

Syncs selected items to the playhead position.
The leading selection functions as reference; cursor distance from the playhead determines alignment side.

Via menu, LMB on the left or right side of the playhead to choose alignment.

Frame
Which frame the strips align to.

Snap Side
Which edge aligns when no edges are selected.

Keep Offset
On: strips move as one group, preserving spacing.
Off: each strips aligns separately.

### Clear Strip Offset

Reference

Menu :

Strip ‣ Transform ‣ Clear Strip Offset

Shortcut :

Alt - O

Resets smooth start/end handles.

### Swap Strip

Reference

Menu :

Strip ‣ Transform ‣ Swap Strip

Left Alt - Left
Swaps with the left neighbor.

Right Alt - Right
Swaps with the right neighbor.

### Remove Gaps

Reference

Menu :

Strip ‣ Transform ‣ Remove Gaps

Shortcut :

Backspace

Clears empty space between the playhead and the nearest leftward item.
Ignores selection and locking state.

All Gaps
Also clears empty space to the right.

### Remove Gaps (All)

Reference

Menu :

Strip ‣ Transform ‣ Remove Gaps (All)

Identical to Remove Gaps with All Gaps active.

### Insert Gaps

Reference

Menu :

Strip ‣ Transform ‣ Insert Gaps

Shortcut :

Shift - Equals

Adds empty space between the playhead and rightward items.
Independent of selection and locking.

### Retiming Keys

By placing and moving retiming points, you control individual frame playback rate.

Note

- Only the strip plays differently, not keyframed content inside.

- Effects cannot use retiming.

Hint

Press R and type a speed for rapid adjustment of selected strips.

Selecting Retiming Keys

By default, points appear as disabled.
Engage Show Retiming Keys to activate selection mode.
Toggle Retiming Keys also controls this.

Multiple points pick together with box select, but only if a point is already selected; otherwise strips pick instead.

Ctrl - LMB selects every point to the right of your chosen point.

Moving Retiming Keys

Drag a point with your mouse or use G. Each point connects to a source frame, so repositioning shifts that frame in the timeline, compressing or extending playback speed.

Moving a point does not move others within the strip. For grouped changes, select all relevant points. Points outside the visible strip extend or contract with outer points to keep adjustments intact.

### Add Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Retiming Key

Insert a point from the retiming menu or press I then pick Add Retiming Key. The point goes at the playhead position.
Boundary points are created automatically, as they are required.

With points selected, strips become deselected, but you can keep adding.
Points anchor to any strip with a chosen point.

### Add Freeze Frame and Slide

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Freeze Frame and Slide

A freeze point halts playback at one frame for a custom span.
Access it through the retiming menu or context.

Note

Smooth entry into or exit from a frozen frame is unsupported.

### Add Speed Transition and Slide

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Add Speed Transition and Slide

Set up a gradual shift from one playback rate to another.
Locate a retiming point between zones with differing speeds, then pick Add Speed Transition from the menu or context.
Two coupled points form, moving in opposition.
Moving them together alters the transition range.

### Delete Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Delete Retiming Keys

Drop a point using Delete or X.
When a point vanishes, the strip length stays put, making the speed settle to the midpoint between edges.

Note

Erasing a transition point reverts to a basic retiming point.

### Reset Retiming

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Reset Retiming

Returns the strip to standard playback timing.

### Set Speed

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Set Speed

Controls the playback velocity of a timed zone.

Speed
The multiplier versus the original speed.

Preserve Current retiming
Leaves surrounding timed zones unmodified by adjusting the entire Duration instead.

### Toggle Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Toggle Retiming Keys

Shortcut :

Ctrl - R

Engages the Show Retiming Keys strip attribute.
Allows keys to render and be modified.

### Split

Reference

Menu :

Strip ‣ Split

Shortcut :

K

Cuts the active strip into two pieces at the playhead.
Both sides keep the source material, preserving the original timeline span.

Hint

Comparable to duplicating and trimming to create two non-overlapping sections.

### Hold Split

Reference

Menu :

Strip ‣ Hold Split

Shortcut :

Shift - K

Divides like Split, making two separate strips where handles cannot go past the cut.

You may edit Hold Offset values directly in the Strip Info panel.

Hint

Acts like splitting the video file, replacing the strip with separate pieces.

### Duplicate

Reference

Menu :

Strip ‣ Duplicate

Shortcut :

Shift - D

Copy the strip as independent; move to the desired spot and place with LMB.

Where the strip links to an asset (e.g., a scene), duplication also copies that asset and uses the duplicate.

### Duplicate Linked

Reference

Menu :

Strip ‣ Duplicate Linked

Shortcut :

Alt - D

Copy the strip as linked; place where desired and click LMB.

Where the strip references an asset, both copies use the original.

### Delete

Reference

Menu :

Strip ‣ Delete

Shortcut :

Delete , X

Remove selected strip(s).

### Update Scene Frame Range

Reference

Menu :

Strip ‣ Update Scene Frame Range

For Scene strips only—Updates Time settings when the scene's boundaries shift.

### Separate Images

Reference

Menu :

Strip ‣ Separate Images

Shortcut :

Y

For image sets—Breaks the strip into individual pieces, one per image.
Helpful for photo slideshows and discrete-frame compositions.

Length
Set the span for each new piece.

### Movie Strip

### Set Render Size

Reference

Menu :

Strip ‣ Set Render Size

Synchronizes the output resolution and format with the strip's specs.

### Deinterlace Movies

Reference

Menu :

Strip ‣ Deinterlace Movies

Transforms interlaced media into non-interlaced.

### Effect Strip

### Change Effect Type

Reference

Menu :

Strip ‣ Effect Strip ‣ Change Effect Type

Replaces the current effect with a compatible variant (matching input count).

Preserves existing connections and settings where compatible, saving reconfiguration work.

Experiment with paired effects—Cross, Gamma Cross, Wipe—all accept dual inputs.

### Reassign Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Reassign Inputs

Shortcut :

R

Reroute how effect strips receive input.
Choose three arbitrary strips and hit R.
If creating no cycle, they connect via a new effect.

### Swap Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Swap Inputs

Shortcut :

Alt - S

Flips the first pair of effect inputs.

### Lock/Mute

Lock Strips Ctrl - H
Blocks strip transformation.

Unlock Strips Ctrl - Alt - H
Allows transformation again.

Mute/Unmute Strips H , Alt - H
Toggle audio on or off.

Mute/Unmute Deselected Strips Shift - H , Shift - Alt - H
Toggle audio for everything except selected items.

### Inputs

Reload Strips Alt - R
Refreshes from the source location.

Reload Strips and Adjust Length Shift - Alt - R
Refreshes and resizes to match.

Change Path/Files
Swaps the strip's source material.

Swap Data
Exchanges content between strips.

### Image Menu

### Clear

#### Position

Reference

Menu :

Image ‣ Clear ‣ Position

Zeros out Position values.

#### Scale

Reference

Menu :

Image ‣ Clear ‣ Scale

Zeros out Scale values (sets to 1.0).

#### Rotation

Reference

Menu :

Image ‣ Clear ‣ Rotation

Zeros out Rotation value.

#### All Transforms

Reference

Menu :

Strip ‣ Clear ‣ All Transforms

Resets all position, scale, and rotation to factory settings.

### Apply

#### Scale to Fit

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fit

Changes Scale values to seat content within the project's Resolution, preserving proportions.

Padding may show on the borders.

#### Scale to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fill

Changes Scale values to expand content across the project's Resolution, preserving proportions.

Content might exceed frame limits.

#### Stretch to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Stretch to Fill

Adjusts Scale to fill the project's full Resolution.
Unlike the methods above, this does not keep proportions.

Image may become warped.

### Context Menu

Open by RMB-clicking in the timeline for quick actions.

### Fades

Reference

Menu :

Add ‣ Fades

Tools for fade effects are here.
Visual strips get opacity animation; audio gets volume.

Clear Fades
Strips lose fade animation.

Fade In and Out
Both fade in and fade out apply.

Fade In
Entry fade applies.

Fade Out
Exit fade applies.

From Current Frame
Fades from playhead through overlapping end.

To Current Frame
Fades from overlapping starts through playhead.

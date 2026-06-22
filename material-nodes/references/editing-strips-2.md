# Editing Strips (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Toggle Retiming Keys

Reference

Editor :

Video Sequencer

Menu :

Strip ‣ Retiming ‣ Toggle Retiming Keys

Shortcut :

Ctrl - R

Turns on the Show Retiming Keys property.
This lets retiming points become visible for the first time and be interacted with.

### Split

Reference

Menu :

Strip ‣ Split

Shortcut :

K

Separates the selected strip at the playhead into two independent pieces.
Both use the source, preserving the original length and timing.

Hint

Equivalent to duplicating and adjusting endpoints to create two non-overlapping strips.

### Hold Split

Reference

Menu :

Strip ‣ Hold Split

Shortcut :

Shift - K

Like Split, results in two distinct pieces, but edges cannot be expanded past the cut point.

Modify Hold Offset numbers in the Strip Info panel to make fine changes.

Hint

Simulates dividing the video file, using the portions as two separate strips.

### Duplicate

Reference

Menu :

Strip ‣ Duplicate

Shortcut :

Shift - D

Generate a standalone copy; position it by moving and releasing LMB.

For strips using data assets like scenes, duplication also copies the referenced asset.

### Duplicate Linked

Reference

Menu :

Strip ‣ Duplicate Linked

Shortcut :

Alt - D

Generate a shared copy; place it and click LMB.

For strips using assets, the copy points to the original asset.

### Delete

Reference

Menu :

Strip ‣ Delete

Shortcut :

Delete , X

Drop selected strip(s).

### Update Scene Frame Range

Reference

Menu :

Strip ‣ Update Scene Frame Range

For Scene strips only—Aligns Time properties with the scene's timing span.
When a scene's length changes, apply this.

### Separate Images

Reference

Menu :

Strip ‣ Separate Images

Shortcut :

Y

For image sequences only—Splits into separate pieces, one image per strip.
Ideal for photo sequences and non-continuous layouts.

Length
Duration for each generated piece.

### Movie Strip

### Set Render Size

Reference

Menu :

Strip ‣ Set Render Size

Applies the strip's proportions and resolution to the render output.

### Deinterlace Movies

Reference

Menu :

Strip ‣ Deinterlace Movies

Transforms interlaced content into standard (non-interlaced) format.

### Effect Strip

### Change Effect Type

Reference

Menu :

Strip ‣ Effect Strip ‣ Change Effect Type

Substitutes the current effect with a compatible type (same input count).

Keeps existing configurations and connections where feasible, simplifying effect experiments.

Swap between compatible effects like Cross, Gamma Cross, and Wipe (all accept dual inputs).

### Reassign Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Reassign Inputs

Shortcut :

R

Redirect effect strip inputs.
Select three strips and press R.
Without cycles, a new effect joins them.

### Swap Inputs

Reference

Menu :

Strip ‣ Effect Strip ‣ Swap Inputs

Shortcut :

Alt - S

Reverses the pair of inputs for the effect.

### Lock/Mute

Lock Strips Ctrl - H
Prevents strip modification.

Unlock Strips Ctrl - Alt - H
Allows strip modification.

Mute/Unmute Strips H , Alt - H
Toggle audio playback on/off.

Mute/Unmute Deselected Strips Shift - H , Shift - Alt - H
Toggle audio for non-selected strips.

### Inputs

Reload Strips Alt - R
Pulls updated versions from the source.

Reload Strips and Adjust Length Shift - Alt - R
Pulls updated versions and re-fits duration.

Change Path/Files
Updates the strip's media source.

Swap Data
Exchanges strip contents.

### Image Menu

### Clear

#### Position

Reference

Menu :

Image ‣ Clear ‣ Position

Restores Position to starting values.

#### Scale

Reference

Menu :

Image ‣ Clear ‣ Scale

Restores Scale to starting values (1.0).

#### Rotation

Reference

Menu :

Image ‣ Clear ‣ Rotation

Restores Rotation to starting values (0).

#### All Transforms

Reference

Menu :

Strip ‣ Clear ‣ All Transforms

Restores all transforms to original settings.

### Apply

#### Scale to Fit

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fit

Modifies Scale to fit content in the project's Resolution, keeping proportions.

May add transparent margins.

#### Scale to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Scale to Fill

Modifies Scale to cover the project's Resolution, keeping proportions.

Content might go beyond frame edges.

#### Stretch to Fill

Reference

Menu :

Strip ‣ Image Transform ‣ Stretch to Fill

Modifies Scale to cover the entire project Resolution.
Does not preserve aspect ratio.

Content may become skewed.

### Context Menu

RMB in the sequencer brings up shortcuts.

### Fades

Reference

Menu :

Add ‣ Fades

Fade management is in this section.
Images receive opacity transitions; audio receives volume transitions.

Clear Fades
Removes all fade animations.

Fade In and Out
Uses both entry and exit fades.

Fade In
Uses entry fade only.

Fade Out
Uses exit fade only.

From Current Frame
Fades forward from the playhead to the finish of crossing items.

To Current Frame
Fades backward from the start of crossing items to the playhead.

Adjusts Scale so content covers the project's Resolution.
Note this approach differs from the above two—aspect ratio is not maintained.

Visual content may become distorted fitting the area.

### Context Menu

Right-click anywhere on the timeline to access convenience tools.

### Fades

Reference

Menu :

Add ‣ Fades

Fade and anti-fade features sit here.
Visuals get opacity tweening; sound gets level tweening.

Clear Fades
Strips stop fading.

Fade In and Out
Both types play.

Fade In
Entry plays.

Fade Out
Exit plays.

From Current Frame
Plays forward from the cursor to where overlapping strips finish.

To Current Frame
Plays backward from where overlapping strips start to the cursor.

# Strip Modifiers, Add Strip, Alpha Over Alpha Under Strips, Color Mix Strip ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Strip Modifiers; Add Strip; Alpha Over & Alpha Under Strips; Color Mix Strip; Glow Strip; Multicam Selector Strip; Multiply Strip; Speed Control Strip; Subtract Strip; Image/Sequence Strip; Mask Strip; Movie Strip; Sound Strip.

## Strip Modifiers

### Strip Modifiers

Reference

Panel :

Properties Editor ‣ Strip Modifiers

Modifiers let you fine-tune image qualities like contrast, brightness, saturation, color balance, and masking.

Apply these directly to a media strip, or use them in an Adjustment Layer to affect multiple strips together.

Linear Modifiers
When on, modifiers work in linear color rather than sequencer color space.

Linear processing matches compositor behavior. Usually enable this; non-linear workflows may yield unexpected behavior.

### Common Options

Each modifier shows several controls:

/ Enable
Toggle the modifier on or off. Handy to see before/after comparisons.

Remove Strip Modifier
Erase the modifier.

Move Strip Modifier
Click and drag to reorder in the stack, changing processing sequence.

### Masking

Limit a modifier's effect area with a Mask or another strip.

Mask Input Type
What kind of input shapes the mask.

Strip :

Use another strip's grayscale values.

Mask :

Use a Mask data-block.

Mask
Pick the Strip or Mask to use.

Mask Time Mask Input Only
How the mask's beginning frame is determined.

Relative :

Mask plays from the strip's start.

Absolute :

Mask stays synced with scene playback.

### Types

Supported modifiers:

### Brightness/Contrast Modifier

Fine-tune how bright and contrasty the picture appears.

### Color Balance Modifier

Shift colors using Lift/Gamma/Gain or Offset/Power/Slope.

Functions like the Color Balance Node.

The chosen method applies these operations to scene colors:

Lift/Gamma/Gain

Lift
Brightens dark tones.

Gamma
Tweaks mid-brightness.

Gain
Tweaks bright tones.

Offset/Power/Slope (ASC-CDL)
For each RGB: \\(c_{out} = (c_{in}×s + o)^p\\)

Slope
Multiplier \\(s\\) shifts most color except black. Bright colors show stronger shifts.

Offset
After applying Slope, adds the Offset \\(o\\). UI shows minus 1, so default 1 means no shift.

Power
Exponent \\(p\\) , mostly affecting middle tones.

### Compositor Modifier

Compositor provides flexible effects. Switch the node context to sequencer in the compositor editor, add a tree, and use it on strips. Node trees become reusable assets.

Compositing explains further.

### Curves Modifier

Color and RGB curves.

Functions identically to the RGB Curves Node.

### Hue Correct Modifier

HSV multi-point curves.

Matches the Hue Correct Node.

### Mask Modifier

Shapes the Alpha Channel using a Mask or strip.

Mask Input Type
What kind of input defines the masking.

Strip :

Another strip's grayscale modulates alpha.

Mask :

A mask data-block modulates alpha.

Mask
The Strip or Mask to use.

Mask Time Mask Input Only
How the mask's start is timed.

Relative :

Mask offset to the strip start.

Absolute :

Mask syncs with scene time.

### Tone Map Modifier

Translates one set of hues to another to display high-range images on limited-range displays.

Matches the Tone Map Node.

### White Balance Modifier

Corrects white tint by picking what should appear white.

### Sound Equalizer Modifier

Boosts or cuts audio frequencies.
Range: 35Hz to 20kHz, ±35dB.

### Pitch

Shifts tone without changing speed.
Helpful for fixing pitch, creating audio effects, or matching keys.

Mode
How pitch shifting works.

Semitones :

Adjust by musical steps.

Semitones
Shift amount in notes.
Positive raises, negative lowers.

Cents
Small steps (1/100 note).

Ratio :

Adjust by a scaling factor.

Ratio
How much the pitch stretches.
Over 1 raises, under 1 lowers.

Preserve Vocal Formants
Keep voice characteristics when shifting.
Keeps speech natural (pitch up without "chipmunk" effects), though may add artifacts.

Quality
How well pitch shifts.

High :

Best processing quality, often slower.
Good for final output.

Fast :

Prioritizes speed over fidelity.
Good for editing.

Consistent :

Maintains stability when pitch changes over time.
Can reduce sudden quality shifts, though may introduce noise.

### Echo

Repeats the sound with delay, building echo depth.
Creates atmosphere, adds texture, or produces rhythmic effects.

Delay
Time gap between each repeat in seconds.
Bigger gaps space echoes further; smaller gaps pack them closer.

Feedback
How much echoed signal loops back.
Higher values extend repeats; lower values shorten.

Mix
Balance between the original and the repeated signal.
Zero means only original, one means only repeat.

Mix
How much original stays versus how much echo appears.
0 = original only; 1 = echo only.

## Add Strip

### Add Strip

The Add effect unites color values from two strips.
Pair a base image with a modifier strip.
The modifier is solid color, grayscale shape, or other media.

Use to elevate overall brightness, or apply a BW shape to selectively brighten areas. The Mix node in Add mode matches this strip and responds to Factor input.

The illustration shows combining gray to an image.
Gray brightens an image since we contribute gray RGB(0.5, 0.5, 0.5) to, say, blue RGB(0.1, 0.1, 0.5) → RGB(0.6, 0.6, 1.0).
Hue (color proportion) stays; value (brightness) climbs significantly. Applied broadly, it appears to flash.

### Options

This strip has no configurations.

### Example

Add Effect.

## Alpha Over & Alpha Under Strips

### Alpha Over & Alpha Under Strips

Transparency info (the alpha layer) governs how this effect combines them.
Solid areas have alpha 1 (total opacity); transparent spots have alpha 0 (invisible).

Use Alpha Over / Alpha Under to layer CG components over footage.
Your 3D model sits as though filmed.
The Adjust ‣ Compositing ‣ Opacity sets how fully the top layer mixes, fading the overlay over the base.
Where the top is transparent, base colors show unchanged.

### Alpha Over

Alpha Over layers items in selection order; the first is ground, the second is foreground.
Opacity regulates foreground transparency. 0.0 shows only ground; 1.0 fully covers ground (except where foreground is see-through).

Warning

Press Premultiply Alpha in the Sidebar of the foreground strip to adjust how transparency combines.
Apply when overlaying a strip with mixed transparency (some see-through, some opaque, some partial) over a completely opaque strip. If edges glow or unexpected transparent spots appear, turn Premultiply on.

Alpha Over Effect.

### Alpha Under

Alpha Under reverses the layers: the first is foreground, the second is ground.
Opacity adjusts ground transparency. 0.0 shows only foreground; 1.0 matches Alpha Over.

## Color Mix Strip

### Color Mix Strip

The Color Mix effect blends two strips by processing each pixel pair.

Does the work of Add, Subtract, or Multiply but opens other color mixing options.

### Options

Blend
Pick the combination mode from the list.
For mode descriptions, see Color Blend Modes.

Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light

Opacity
How heavily the second picture layers onto the first.

## Glow Strip

### Glow Strip

This makes bright patches of an image radiate by handling its brightness info.
Glow stacks the base over a shifted version with blurred bright spots.

To "animate" the glow, fade it with the base using Gamma Cross.

### Options

Threshold
Brightness level above which areas blur.

Clamp
Top brightness contributed.

Boost Factor
Brightness multiplier.

Blur Distance
Blur radius.

Quality
Boosts smoothness but uses more computation.

Only Boost
When on, displays only the "modified" side without the base.

### Example

Glow effect.

## Multicam Selector Strip

### Multicam Selector Strip

This strip handles multi-camera work.
Multi-camera describes recording a scene from various positions and combining afterward.

### Workflow

Video Sequencer makes multi-camera assembly fast with setup.
Steps:

- Import video from each camera.

- Sync cameras by comparing audio waves or object motion.

Tip

Group cameras, their sound, and effects with Meta Strips to simplify organization.

- Break the timeline into multiple Preview sections for each input.
Each preview's Display Channel shows a different input track.

- Add a Multicam Selector above the video channels.

Result resembles:

Multi-camera editing setup.

- Select the Multicam strip. The sidebar shows Multicam is basic: it pulls one channel.
Keyboard shortcuts handle the rest.

- When Multicam is active, keys 1 to 9 map to cut choices.
Start playback, watch, and press numbers for the right camera during play.

- Each keystroke cuts, creating small Multicam Selector segments.

Process: monitor sequences, replay, and roughly cut using number keys.
Then fine-tune cuts by adjusting overlapping Multicam edge handles.

Tip

Turn on Proxies to improve playback speed.

### Options

Source Channel
Input channel the Multicam gets from.

Cut To
Splits at the playhead and moves to the chosen channel automatically.

## Multiply Strip

### Multiply Strip

Multiply combines two color values.
Blender uses 0.0–1.0 scales.
Two 0.0–1.0 values multiply to stay 0.0–1.0, no normalization needed.

(Standard RGB bytes like RGB(124, 255, 56) produce out-of-range products like RGB(7316, 46410, 1848), requiring division by 256 to fit RGB(0–255).)

Main uses:

With a Mask

A black-and-white mask, when multiplied with an image, reveals only white zones (other areas turn black).

James Bond opening sequences, where the camera peers down a gun barrel, exemplify this.

With Uniform Colors

Multiplying a hue with an image softens certain color bands (and boosts complementary ones).

A brown pixel RGB(0.50, 0.29, 0.05) multiplied by cyan RGB(0.0, 1.0, 1.0) becomes RGB(0.0, 0.29, 0.05).
Reds disappear while blue and green heighten. Physically, cyan light on chocolate results in greener greens and bluer blues. Naturally, plants flourish more vivid, seawater looks tropical, skies feel open.

Note

This operation darkens overall output (result below both inputs).
All white → other picture; all black → all black!

### Options

This strip has no options.

### Example

Multiply Effect.

## Speed Control Strip

### Speed Control Strip

Speed Control reshapes how quickly or slowly a strip plays.
Faster playback skips frames, running out before the stop point.
When frames expire, the last one holds (appears frozen). Place the next strip where you want action resuming.

### Options

Speed Control
How to modify play velocity.

Stretch :

Calculates speed from the strip's span.
Half-scale → double speed.

Multiply :

Multiplies playback pace by a Multiply Factor.
0.5 = half speed; 2.0 = double speed.
Negative = reverse while adjusting; negative 2 = reverse + double speed.

Note

You adjust strip length by hand.

Frame Number :

Picks which frame to show at the present moment.
E.g., Frame Number 50 displays frame 50.
Keyframe this to recreate animation effects.

Length :

Uses percentage mapping. 50% picks the halfway frame.

Interpolation
Blurs between frames to soften visual break when playback drops below source rate.

### Examples

### Creating a Slow-Motion Effect

Want slow playback?
Use Add ‣ Effect ‣ Speed Control on the clip.

In the Effect Strip panel, select Multiply.
Enter the speed ratio.
To cut speed in half, enter 0.5.
A 275-frame video plays at half speed, showing 137 frames.

To show the remaining frames in slow-mo, double the source span.
(Effects span from source spans.)
For other ratios, apply:

new_length = real_length / speed_factor

Render all frames (here: 550).

### Keyframing the Speed Control

Keyframing the Frame number.

For finer control, animate!
Keyframing Frame Number directly is typical.
Keyframes are needed for any speed change; otherwise it looks frozen. Graph editor usually wants Linear interpolation (Bézier is rarely wanted).

Tip

Keyframing the Multiply factor also works but remember to Refresh All to apply.

### Changing Video Frame Rates

Remap frame rates using speed.
Rendering as image sequences lets you adjust output image count.
Use Multiply above or below one.

A 30 fps 5-minute video going to 24 fps film uses 30/24 = 1.25.
Instead of 5 × 60 × 30 = 9000 frames, you get 9000 / 1.25 = 7200 = 5 × 60 × 24 frames.
Set start = 1, end = 7200, Format = jpeg 30fps output.
Write 0001.jpg to 7200.jpg, covering the whole 9000.
Image 7200.jpg matches frame 9000.
Reading at 24 fps lasts exactly 5 minutes.

## Subtract Strip

### Subtract Strip

This effect removes one strip's hue from the next.

Build a negative image with this, or invert strip order and darken.
Subtracting blue from white yields yellow (red + green = yellow).

### Options

This strip has no options.

### Example

Subtract Effect.

## Image/Sequence Strip

### Image/Sequence Strip

Image strips serve to integrate photographic content or sequenced image sets into the Video Sequencer, making them suitable for presentations, overlaid graphics, base footage, rendered frame collections, or hand-drawn animation workflows.

A single-frame strip shows one static image for a defined span, while a sequence strip plays through a collection of images sequentially, each occupying one frame slot. Both formats accommodate spatial transformation, applied effects, color space configuration, and blending operations alongside other timeline content.

Tip: Display frame previews directly on image strips in the Sequencer through the Thumbnails overlay option.

### Single Image

When you load one still image (*.jpg, *.png, etc.), Blender defaults to a 25-frame duration, displaying the image across that entire span. You can modify this length using the "Add Image Strip" operator and adjusting the property via the sidebar.

### Image Sequence

For numbered image collections (*-0001.jpg, *-0002.jpg, *-0003.jpg, etc. in any format), two primary selection modes are available:

Range
Open the directory and drag the mouse over a group of consecutive filenames to highlight them. Use page navigation and Shift-drag to extend the selection further.

Batch
Use Shift-click on individual files to gather non-consecutive images; each will play as a single frame in file order, allowing mixed formats (jpg, png, exr, etc.).

All
Press A to select or deselect every file in the current folder.

Tip

Managing Size Mismatches

Working with images of varying dimensions alongside different output resolutions requires planning. When source dimensions differ from render dimensions, the Video Sequencer attempts automatic scaling to fit the entire image within the render boundary, but this can result in parts being cut off. To avoid clipping, use Crop and/or Offset in the Input panel to reposition and select the needed region. When Crop or Offset are applied, automatic scaling disables, and manual size adjustment via the Transform effect becomes possible.

### Add Image Strip

Reference

Menu: Add ‣ Image/Sequence

Move Strips
Enable mouse positioning to place the strip immediately after insertion. When this option is on, Start Frame and Channel fields are hidden since they update interactively.

Start Frame
Designate where the strip's left edge begins on the timeline.

Channel
Which row to place the strip within.

Replace Selection
Currently highlighted strips become unselected, and only the new strip is marked as active.

Relative Path
Store file location as a path relative to the blend document.

Fit Method
Specifies how media with aspect ratios mismatched to the output resolution scale to fit the display area.

Scale to Fit:
Modifies the strip's Scale Transform so the visual material fits within the project boundary while keeping proportions unchanged. This often adds transparent borders around the content.

Scale to Fill:
Adjusts the strip's Scale Transform to fill the entire output area while preserving aspect ratio. Parts of the image may extend beyond the visible region.

Stretch to Fill:
Resizes the strip to occupy the entire output without aspect constraint. The image may become warped to fit.

Set View Transform
Automatically applies an appropriate View Transform matching the imported media's Color Space. Standard is usually correct; wrong settings risk color inaccuracy or reduced performance.

Import As
Governs how media loads into the editor.

Auto Detect:
Consecutively numbered files are loaded as a single sequence spanning their count; otherwise files appear as individual strips using the specified length.

Image Sequence:
All files become a single sequence regardless of extension or naming, and placeholders are not supported.

Individual Images:
Each file becomes a separate strip of the given length, arranged sequentially.

Use Placeholders
Image sequences can utilize placeholder files. Enable the Use Placeholders option when adding a strip. Blender recognizes the frame numbering pattern (filename + frame index + .extension) and builds a sequence spanning the detected range even if some frames are absent. This lets you render with missing frames while keeping the sequence properly timed. Missing frames appear in pink in the preview. Once the missing images are rendered or added, refreshing the Sequencer fills in the placeholder frames. This option also works with the Change Data/File operator to extend the range.

Length
Duration in frames of the inserted strip. This parameter is ignored when importing sequences, as their length matches the file count.

## Mask Strip

### Mask Strip

The Mask strip constructs a mask image from a selected mask object created in the Movie Clip Editor. Functionally similar to the Mask Node but with fewer customization choices. The mask renders at the project's output resolution, adjusting scale based on proxy levels.

### Options

Mask
Selector for choosing which mask data-block to use.

## Movie Strip

### Movie Strip

To load a movie file (optionally containing sound) open the File Browser and pick a file, such as *.avi format videos.

Note

Media Files Can Be Large

A three-minute .mov file may reach 140MB. Loading it, even over network, requires time. Avoid assuming Blender has frozen if there's a delay.

Tip

Movie strips can show frame previews in the Sequencer through the Thumbnails overlay option.

### Add Movie Strip

Reference

Menu: Add ‣ Movie

Move Strips
Position the strip using the mouse immediately upon insertion. When enabled, Start Frame and Channel fields don't display.

Start Frame
Frame position for the left boundary of the strip.

Channel
Row assignment for the strip.

Relative Path
File location is stored relative to the blend document.

Replace Selection
Currently selected strips are replaced with the new strip.

Fit Method
Controls how media with mismatched aspect ratios fit into the render area.

Scale to Fit:
Adjusts the strip's Scale Transform for the content to fit the project area while maintaining proportions. Transparent bands may be added around the content edges.

Scale to Fill:
Alters the strip's Scale Transform to span the entire output while maintaining proportions. Parts of the original media may fall outside the visible area.

Stretch to Fill:
Resizes the strip to fill the full output without maintaining proportions. Distortion may occur.

Set View Transform
Chooses an appropriate View Transform based on the imported media's Color Space. Standard is typically correct; misalignment risks wrong colors or degraded rendering speed.

Adjust Playback Rate
Automatically scales playback velocity to match the original speed, accounting for scene frame rate differences.

Sound
Includes a Sound Strip containing the movie's audio track.

Set Scene Frame Rate
Updates the Scene Frame Rate to the frame rate stored in the video file.

### Example

Imported Movie strip with audio track underneath.

The strip itself shows its name, source file path, and duration.

## Sound Strip

### Sound Strip

Beyond images and video, the Video Sequencer handles audio work. Load Waveform Audio format (WAV), MP3, and other sound files, or extract audio from movie files, then blend them using animation curves for volume management.

Example of sound editing.

### Working with Audio Tracks

A Sound strip operates like other strips in the Video Sequencer. Select and reposition it, adjust its starting offset by dragging the strip edges, and use K to divide it into segments. A practical use case is removing pauses or unwanted sounds.

Multiple Sound strips can overlap and mix during rendering. Assign each a name and volume via the sidebar. Overlapping strips automatically combine during output. For example, dialogue might sit on channel 5, background music on channel 6, and sound effects on channel 7.

See also

The Playback menu in the Timeline offers settings for audio playback behavior.

### Waveform

Audio waveform visibility depends on two factors:

Overlay
The Sequencer Overlay menu provides options to display all strip waveforms, none, or follow per-strip settings.

Strip
Each strip has a Display Waveform option, visible only when overlay is set to Use Strip Option.

Waveform clipping (amplitude above 100%) shows in red.

Further strip settings appear in the Sound Sidebar Panel.

### Animating Audio Track Properties

To animate Sound strips, press I over any property. Fading music in/out or adjusting levels are common use cases. Overlapping/crossed Sound strips combine together; lower channels don't suppress higher ones (unlike video/image strips), enabling Blender to function as an audio mixer. Layer tracks and animate curves to manage each sound level, creating an automated multi-channel mixer!

See also

Audio crossfading uses the Sound Crossfade effect.

### Output

Two rendering approaches are available. Encode audio into a video file, or render to a separate audio file. See documentation on audio format selection and rendering initiation.

### Add Sound Strip

Reference

Menu: Add ‣ Sound

Move Strips
Position using the mouse immediately after adding. When enabled, Start Frame and Channel don't display.

Start Frame
Timeline frame for the left edge.

Channel
Row assignment.

Relative Path
File location is stored relative to the blend document.

Replace Selection
Swap currently selected strips with the new sound strip.

Cache
Buffer the sound in RAM, activates Caching in Source properties.

Mono
Merge all channels into a single channel, activates Mono in Sound properties.

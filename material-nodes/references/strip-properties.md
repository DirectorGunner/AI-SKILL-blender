# Strip Properties, Text Strip, Wipe Strip, Video Editing App Template ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Strip Properties; Text Strip; Wipe Strip; Video Editing App Template; Font Drawing (blf).

## Strip Properties

### Strip Properties

Type
Strip classification, shown via icon.

Name
Text field for adjusting the strip identifier, displayed on the timeline.

Color Tag
Strips receive a Type-based default color; use the color tag to apply a custom color for organizational purposes.

Mute
Turn off to silence strip output.

### Compositing

Reference

Panel: Sidebar ‣ Strip ‣ Compositing

Blend
Blending strategy for combining the strip with lower-channel content. See Blend Modes for details.

Opacity
The transparency (alpha) value of the strip.

When animated, opacity displays as an overlay on the strip—a dark section following the animation curve. The F-Curves overlay can be hidden to remove this visualization.

### Transform

Reference

Panel: Sidebar ‣ Strip ‣ Transform

Filter
Method for calculating pixel values at non-integer image coordinates.

Auto:
Filter selection adapts to scaling factors.

- No scale/rotation/integer coords: Nearest

- Upscaling over 2x: Cubic Mitchell

- Downscaling over 2x: Box

- All else: Bilinear

Nearest:
Direct pixel matching without interpolation (lowest processing).

Bilinear:
Interpolates across a 2×2 grid.

Cubic Mitchell:
Cubic Mitchell on a 4×4 grid.

Cubic B-Spline:
Cubic B-Spline (smooth, minimal artifacts) on a 4×4 grid.

Box:
Averages source samples within destination pixels.

Position X, Y
Shifts the frames along horizontal and vertical axes.

Scale X, Y
Resizes along horizontal and vertical axes.

Rotation
Applies 2D rotation about the Z axis.

Mirror
Flips along the X (left-right) or Y (top-bottom) axis.

### Crop

Reference

Panel: Sidebar ‣ Strip ‣ Crop

Trims the source image edges. Control trimming with Top, Left, Bottom, and Right parameters.

### Video

Reference

Panel: Sidebar ‣ Strip ‣ Video

Strobe
Render every nth frame. Setting this to 10 shows only frames 1, 11, 21, 31, 41…. This is a float value, allowing beat-synchronized effects.

Reverse Frames
Plays the strip backwards from the final frame.

### Color

Reference

Panel: Sidebar ‣ Strip ‣ Color

Saturation
Modifies color intensity.

Multiply
Scales all color channels by this amount, raising brightness.

Multiply Alpha
When using Multiply, also scale the alpha channel.

Convert to Float
Changes input to floating-point format.

### Sound

Reference

Panel: Sidebar ‣ Strip ‣ Sound

Audio handling is covered in Sound Strip.

Volume
Governs loudness level.

Animated volume displays as an overlay—a dark section following the animation curve. Hide via F-Curves disable. The waveform shows the updated level.

Offset
Audio playback delay from the strip start, in seconds.

Mono
Collapse all channels to a single channel.

Pan
Positions audio across speakers in multi-channel systems. Only mono sources pan; enable Mono to convert non-mono files. The value represents the angle (multiply by 90 degrees).

For stereo: left (-1) to center (0) to right (1). Higher values address rear speakers: -2 is back-left, 2 is back-right.

Tip

Apply values beyond soft bounds for smooth animation, as angle wraps across rotations.

Note

Audio channel count is configurable in Audio Output settings.

Preserve Pitch
When active, holds the original pitch despite strip speed changes. When off, speed adjustments alter pitch (slower = lower pitch, faster = higher pitch). Useful for syncing audio to edited timing without affecting tone or musical key.

Display Waveform
Displays a visual representation of the audio waveform within the Sound strip. Animation keyframes and volume settings influence the waveform appearance. Red indicates clipped audio (above 100% amplitude). Visibility depends on setting the Waveforms overlay option to Per-Strip mode.

### Time

Reference

Panel: Sidebar ‣ Strip ‣ Time

The Time panel adjusts source and timeline positioning.

Lock (padlock icon in panel header)
Prevents repositioning.

Show Retiming Keys
Toggle display and selection of Retiming Keys.

Channel
Alters the row number.

Start
Updates the strip's start frame; equivalent to selecting and moving it.

Duration
Changes the length in frames by adjusting the end position.

End
Displays the strip's conclusion time and frame.

Strip Offset Start/End
Positive values shift edges inward, starting later and stopping earlier than source bounds. Trim via the Offsets overlay to see the full source. Negative values shift outward, revealing the first or last frame extended as a freeze frame.

Hold Offset Start/End
Freezes frames at the start/end beyond simple trimming. You can combine Hold Offset and Strip Offset to hold a frame other than the first or last. For instance, setting Hold Offset Start to 10 and Strip Offset Start to -20 displays the 11th frame for 21 frames, then plays onward.

Current Frame
The playhead position within the strip, relative to its start.

### Source

Reference

Panel: Sidebar ‣ Strip ‣ Source

The Source panel displays and allows modification of the source file and its display handling.

Directory
The folder housing the source file.

Filename
The source file name. File names cap at 256 characters.

Color Space
Color space classification of the source media. Available spaces depend on the active OCIO profile. Default options are documented in Default OpenColorIO Configuration.

Alpha Mode
For sources with transparency, choose between Straight Alpha and Premultiplied Alpha.

Stream Index (Movie Strip)
Which video stream to play from when multiple exist.

Deinterlace
Removes interlacing from analog video.

Source Information
Displays media attributes.

Resolution
Output dimensions of the active strip.

FPS (Movie Strip)
Frame rate stored in the video file. Mismatch with scene Frame Rate may cause playback speed issues unless adjusted.

### Options for Image Strips

Directory
Folder holding the source file(s).

Filename
Source file identifier. For sequences, varies per frame.

Change Data/Files
Opens a File Browser to select new images, equivalent to Strip ‣ Inputs ‣ Change Paths/Files.

### Options for Sound Strips

Sound
Data-block selector for picking a sound.

File Path
Location of the audio file.

Pack
Embed the sound into the blend document.

Caching
Audio is decoded and cached in RAM.

Source Information
Displays media attributes.

Sample Rate
Samples per second in the audio encoding.

Channels
Audio channel count.

Instead of adjusting these offsets in the Sidebar, you can also drag the strip's handles.
Hold Offset Start/End — trim frames off the start/end of the source material. At first glance this matches the Strip Offset properties, but you can in fact combine the two to hold (freeze) a frame other than the first or last: for example, with Hold Offset Start at 10 and Strip Offset Start at -20, the video first shows the source's 11th frame for 21 frames, then plays the remaining frames.
Current Frame — the Playhead's frame number relative to the start of the strip.

Source (Panel: Sidebar ‣ Strip ‣ Source): shows (and lets you change) the file the strip points to, as well as how that file is displayed.
Directory — the folder containing the strip's source file.
Filename — the name of the source file; note that file names are limited to 256 characters.
Color Space — the source file's color space; the available list depends on the active OCIO config, with the default supported color spaces described in detail under Default OpenColorIO Configuration.
Alpha Mode — if the source file has an Alpha (transparency) channel, choose between Straight Alpha and Premultiplied Alpha.
Stream Index (Movie Strip) — which video stream to use, in case there are multiple.
Deinterlace — apply deinterlacing to analog video.
Source Information — displays information about the strip's media.
Resolution — the resolution of the active strip's image output.
FPS (Movie Strip) — the frame rate encoded into the video file; if it doesn't match the scene's Frame Rate, the perceived speed of the media will be wrong unless the speed is changed to account for the difference.

Options for Image Strips:
Directory — the directory that contains the source file(s).
Filename — the name of the source file; for image sequences this differs for each frame.
Change Data/Files — opens a File Browser to select a new set of images (an alternative to editing the textboxes above); same as Strip ‣ Inputs ‣ Change Paths/Files.

Options for Sound Strips:
Sound — a data-block menu to select a sound.
File Path — the path to the file used by the selected sound data-block.
Pack — pack the sound into the blend-file.
Caching — the sound file is decoded and loaded into RAM.
Source Information — displays information about the strip's media.
Sample Rate — the number of samples per second the audio is encoded at.
Channels — the number of audio channels encoded into the audio stream.

## Text Strip

### Text Strip

The Text strip outputs text directly in the Sequence editor. The text appears in the rendered sequence according to its field content.

Text effect.

Tip

All Text strips in a sequence can export to SubRip format, enabling use as subtitles.

### Options

Text
The displayed text content. Limited to 512 characters.

Wrap Width
Wraps text at a percentage of frame width; zero disables wrapping.

### Style

Font
Data-block selector for the font file rendering the text.

(Bold)
Use bold font appearance.

(Italic)
Use slanted font appearance.

Size
Text height.

Color
Text hue.

#### Outline

Draws a boundary line around the text shape.

Color
Outline hue and opacity.

Width
Boundary thickness.

#### Shadow

Adds a shadow beneath the text.

Color
Shadow hue and opacity.

Angle
Shadow placement as an angle, 0° right and 90° down.

Offset
Shadow displacement distance.

Blur
Shadow softness intensity.

#### Box

Generates a background box to improve text legibility.

Color
Box hue and opacity.

Margin
Box boundary expansion from glyph bounds, measured as frame width fraction.

Roundness
Corner rounding, defined as box height fraction.

### Layout

Location X, Y
Text placement on horizontal and vertical axes.

Alignment X, Y
Horizontal text positioning: left, center, or right alignment.

Anchor X, Y
Horizontal (X) or vertical (Y) text origin relative to location.

### Text Editing in Preview

Text strips edit directly in the Preview area for intuitive workflow.

- Enable Editing: Press Tab to activate edit mode. A boundary and cursor appear.

- Disable Editing: Press Tab again to leave edit mode.

### Editing

Reference

View Type: Preview

Menu: Strip ‣ Text

Copy Text (Ctrl-C)
Copy highlighted text.

Paste Text (Ctrl-V)
Inserts from system clipboard, enabling external application text.

Cut Text (Ctrl-X)
Remove highlighted text.

Delete Character (Backspace)
Remove character before cursor.

Insert Line Break (Return)
Start a new line.

Select All (Ctrl-A)
Mark all text.

Deselect All (Esc)
Clear selection.

### Navigation

- Left – Move cursor one position left.

- Right – Move cursor one position right.

- Up – Move cursor one line up.

- Down – Move cursor one line down.

- Home – Move cursor to line start.

- End – Move cursor to line end.

- Ctrl-Left – Move cursor one word left.

- Ctrl-Right – Move cursor one word right.

- PageUp – Move cursor to text start.

- PageDown – Move cursor to text end.

### Text Selection

Hold Shift while pressing navigation keys to select.

- Shift-Left – Select previous character.

- Shift-Right – Select next character.

- Shift-Up – Select previous line.

- Shift-Down – Select next line.

- Shift-Home – Select to line start.

- Shift-End – Select to line end.

- Shift-Ctrl-Left – Select previous word.

- Shift-Ctrl-Right – Select next word.

- Shift-PageUp – Select to text start.

- Shift-PageDown – Select to text end.

## Wipe Strip

### Wipe Strip

The Wipe transition strip transitions from one strip to another using a wipe motion. Single-source wiping has no visible effect. The wipe span equals the source overlap and cannot be adjusted directly. To change wipe timing, adjust source strip boundaries to alter their intersection.

### Options

Transition
Wipe motion style.

Single
Uncovers the next strip along a straight line moving across.

Double
Resembles Single but uses two lines originating from the middle or outside edges. Like a blinking eye.

Iris
Uncovers content through a circular boundary that opens outward or contracts inward, similar to a camera aperture or pupil. Optional blur creates a feathered, bleeding-ink appearance.

Clock
Mimics analog clock hands sweeping clockwise (or counterclockwise if Wipe In is on) from the 9 o'clock point, revealing the next strip beneath.

Direction
Fade In or Out orientation.

Blur Width
Transition boundary softness.

Angle
Line angle for Single and Double styles.

Default Fade
Automatically computes a linear fade over the strip span.

Effect Fader
Allows custom keyframe animation of the fade. Easing options let you refine the wipe.

### Example

Wipe Effect.

## Video Editing App Template

### Video Editing App Template

The Video Editing app template offers a preconfigured workspace for complete video production.

The default Video Editing app template.

### Overview

This template accelerates video editing by combining video, image, and sound content on a unified timeline. Each media element appears as its own strip, allowing arrangement, trimming, and integration with effects for polished output.

### Features

- File Browser:
Filters display to show only video, image, and audio types for streamlined file location and import.

- Preview:
An interactive viewing area where strips can be selected, repositioned, and previewed as final output.

- Sequencer:
The workspace for composing and editing video, image, and sound strips.

- Properties Editor:
Streamlined to show critical panels: Render, Output, Scene, and Strip Modifiers.

### Default Settings

- The Edit scene spans 10 seconds by default, giving new projects a starting framework.

- The Edit scene is both the current and active Sequencer scene.

- Output is 1920 × 1080 HD at 24 FPS, standard for video production.

- Video rendering format is preset for quick export.

### Usage

- Open File ‣ New ‣ Video Editing to launch the template.

- Locate media in the File Browser.

- Import media (clips, images, sound) into the Sequencer via drag-and-drop.

- Compose and edit strips as desired.

- Export using Render ‣ Render Animation.

This template supplies an efficient foundation, combining layout, settings, and workflow tailored for video creation.

## Font Drawing (blf)

### Font Drawing (blf) 

This module provides access to Blender's text drawing functions.

### Hello World Text Example 

Example of using the blf module. For this module to work we
need to use the GPU module gpu as well.

`\text
### Import stand alone modules.
import blf
import bpy

font_info = {
"font_id": 0,
"handler": None,
}

def init():
\"\"\"init function - runs once\"\"\"
import os
### Create a new font object, use external TTF file.
font_path = bpy.path.abspath('//Zeyada.ttf')
### Store the font index - to use later.
if os.path.exists(font_path):
font_info["font_id"] = blf.load(font_path)
else:
### Default font.
font_info["font_id"] = 0

### Set the font drawing routine to run every frame.
font_info["handler"] = bpy.types.SpaceView3D.draw_handler_add(
draw_callback_px, (None, None), 'WINDOW', '`POST_PIXEL`')

def draw_callback_px(self, context):
\"\"\"Draw on the viewports\"\"\"
### BLF drawing routine.
font_id = font_info["font_id"]
blf.position(font_id, 2, 80, 0)
blf.size(font_id, 50.0)
blf.draw(font_id, "Hello World")

if __name__ == '__main__':
init()
`\

### Drawing Text to an Image 

Example showing how text can be drawn into an image.
This can be done by binding an image buffer (imbuf) to the font's ID.

`\text
import blf
import imbuf

image_size = 512, 512
font_size = 20

ibuf = imbuf.new(image_size)

font_id = blf.load(\"/path/to/font.ttf\")

blf.color(font_id, 1.0, 1.0, 1.0, 1.0)
blf.size(font_id, font_size)
blf.position(font_id, 0, image_size[1] - font_size, 0)

blf.enable(font_id, blf.`WORD_WRAP`)
blf.word_wrap(font_id, image_size[0])

with blf.bind_imbuf(font_id, ibuf, display_name=\"sRGB\"):
blf.draw_buffer(font_id, \"Lots of wrapped text. \" * 50)

imbuf.write(ibuf, filepath=\"/path/to/image.png\")
`\

blf. aspect ( fontid , aspect ) 

Set the aspect for drawing text.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- aspect ( float ) – Aspect ratio for non-uniform text scaling.

blf. bind_imbuf ( fontid , imbuf , * , display_name = None ) 

Context manager to draw text into an image buffer instead of the GPU's context.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- imbuf (imbuf.types.ImBuf) – The image to draw into.

- display_name ( str | None ) – Ignored (formerly a color-space transform name), kept for backwards compatibility.

Returns :

The BLF ImBuf context manager.

Return type :

BLFImBufContext

blf. clipping ( fontid , xmin , ymin , xmax , ymax ) 

Set the clipping, enable/disable using CLIPPING.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- xmin ( float ) – Left edge of the clipping rectangle.

- ymin ( float ) – Bottom edge of the clipping rectangle.

- xmax ( float ) – Right edge of the clipping rectangle.

- ymax ( float ) – Top edge of the clipping rectangle.

blf. color ( fontid , r , g , b , a ) 

Set the color for drawing text.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- r ( float ) – Red channel 0.0 - 1.0.

- g ( float ) – Green channel 0.0 - 1.0.

- b ( float ) – Blue channel 0.0 - 1.0.

- a ( float ) – Alpha channel 0.0 - 1.0.

blf. dimensions ( fontid , text ) 

Return the width and height of the text.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- text ( str ) – The text to measure.

Returns :

The width and height of the text.

Return type :

tuple[float, float]

blf. disable ( fontid , option ) 

Disable a font drawing option.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- option ( int ) – One of ROTATION, CLIPPING, SHADOW, MONOCHROME or `WORD_WRAP`.

blf. draw ( fontid , text ) 

Draw text in the current context.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- text ( str ) – The text to draw.

blf. draw_buffer ( fontid , text ) 

Draw text into the image buffer bound via blf.bind_imbuf().

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- text ( str ) – The text to draw into the bound image buffer.

blf. enable ( fontid , option ) 

Enable a font drawing option.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- option ( int ) – One of ROTATION, CLIPPING, SHADOW, MONOCHROME or `WORD_WRAP`.

blf. load ( filepath ) 

Load a new font.

Parameters :

filepath ( str | bytes ) – The filepath of the font.

Returns :

The new font's fontid or -1 if there was an error.

Return type :

int

blf. position ( fontid , x , y , z ) 

Set the position for drawing text.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- x ( float ) – X axis position to draw the text.

- y ( float ) – Y axis position to draw the text.

- z ( float ) – Z axis position to draw the text (typically 0).

blf. rotation ( fontid , angle ) 

Set the text rotation angle, enable/disable using ROTATION.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- angle ( float ) – The angle for text drawing to use (in radians).

blf. shadow ( fontid , level , r , g , b , a ) 

Shadow options, enable/disable using SHADOW.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- level ( int ) – The shadow type: 0 for none, 3 for 3x3 blur, 5 for 5x5 blur or 6 for outline. Other values raise a TypeError .

- r ( float ) – Shadow color (red channel 0.0 - 1.0).

- g ( float ) – Shadow color (green channel 0.0 - 1.0).

- b ( float ) – Shadow color (blue channel 0.0 - 1.0).

- a ( float ) – Shadow color (alpha channel 0.0 - 1.0).

blf. shadow_offset ( fontid , x , y ) 

Set the offset for shadow text, enable/disable using SHADOW.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- x ( int ) – Horizontal shadow offset value in pixels.

- y ( int ) – Vertical shadow offset value in pixels.

blf. size ( fontid , size ) 

Set the size for drawing text.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- size ( float ) – Point size of the font.

blf. unload ( filepath ) 

Unload an existing font.

Parameters :

filepath ( str | bytes ) – The filepath of the font.

blf. word_wrap ( fontid , wrap_width ) 

Set the wrap width, enable/disable using `WORD_WRAP`.

Parameters :

- fontid ( int ) – The id of the typeface as returned by blf.load(), for default font use 0.

- wrap_width ( int ) – The width (in pixels) to wrap words at.

blf. CLIPPING 

Constant value 2

blf. MONOCHROME 

Constant value 128

blf. ROTATION 

Constant value 1

blf. SHADOW 

Constant value 4

blf. `WORD_WRAP` 

Constant value 64

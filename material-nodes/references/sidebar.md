# Sidebar, Chromatic Aberration Node, Camera Lens Effects Nodes, Sensor Noise Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Sidebar; Chromatic Aberration Node; Camera & Lens Effects Nodes; Sensor Noise Node; Vignette Node; Brightness/Contrast Node; Color Balance Node; Color Correction Node; Exposure Node; Gamma Node; Hue Correct Node; Hue/Saturation/Value Node.

## Sidebar

Compositor Sidebar — View. Backdrop (Sidebar region ‣ View): the backdrop shows a Viewer node's output behind the node editor — e.g. Shift-Ctrl-LMB on an Image node previews the image, while on a Mix node it shows the mix result — and it's toggled by the Backdrop panel header checkbox or the Compositor header's Backdrop button, useful for evaluating node results while editing and comparing the graph to its output. Its options: Channels (which color channels of the backdrop show), Zoom (Alt-V, V — the backdrop's display size), Offset X, Y (screen-space offset), Move (Alt-MMB — move it interactively), and Fit (scale it to fit the view). Options (Sidebar region ‣ Options) — Performance: tweak the compositor's performance with Device (CPU or GPU for compositing) and Precision (GPU — the precision of intermediate results: Auto, full for final renders and half otherwise, or Full, full for final renders and viewport).

Tool — shows the active tool's settings.

Image:
Image — tools for working with images (see Image Settings).
Metadata — lists the image's metadata.

View:
Display — the editor's display options live here.
  Aspect Ratio — the display aspect for this image; doesn't affect rendering.
  Repeat Image — tiles the image so it fills the editor entirely.
Annotations — options for the annotation tool (see Annotations).

Scopes — shows various statistics about the image's colors. The Scopes tab is hidden while the active object is in Edit Mode or Texture Paint Mode.
Histogram — graphs the image's color distribution: for each color value (Luminance, say) on the X axis it plots the pixel count on the Y axis, so a mostly dark image peaks toward the left. Use it to balance an image's tonal range — a well-balanced image shows a smooth spread of values. Drag LMB in the histogram to adjust its vertical zoom.
  Luma — a luminosity histogram.
  RGB — the RGB channels stacked on each other.
  R/G/B/A — a single channel.
  Show Line — draws lines instead of filled shapes.
Waveform — plots the color distribution for each vertical column of pixels: the Waveform's X axis matches the image's X axis, while its Y axis spans a color component such as Luminance, and the brighter a point, the more pixels in that column share that value.
  Waveform Opacity — the points' opacity.
  Waveform Mode — Luma (one Waveform of the luminosity spread), YCbCr (the Y, Cb, and Cr Waveforms side by side), Parade (the R, G, and B Waveforms side by side), Red Green Blue (the R, G, and B Waveforms overlaid).
Vectorscope — shows color distribution radially: angle is hue, distance from center is saturation.
  Vectorscope Opacity — the points' opacity.
Sample Line — like the Histogram, but it reads its sample data from a line.
  Sample Line — used to draw the line the sample data is read from.
Samples:
  Full Sample — samples every pixel.
  Accuracy — the proportion of pixels sampled when Full Sample is off.

Image Tab:
UV Vertex — the mean position of the selected UV vertices.
Image — see Image Settings.
UDIM Tiles — see UDIM Tiles.

Tool Tab — shows the active tool's settings.

View Tab — Display: this panel holds the editor's display options.
Aspect Ratio X, Y — the display aspect for this image; doesn't affect rendering.
Repeat Image — tiles the image so it fills the editor completely.
Pixel Coordinates — uses pixel coordinates rather than relative ones (0 to 1) for the UV Vertex and 2D Cursor Location fields.
2D Cursor — Location X, Y: view and change the 2D Cursor's position.
Annotations — options for the Annotate tool.

Scopes — see Scopes in the Image Editor.

Toggle the Sidebar with View ‣ Sidebar or the shortcut N. Below you can see two Video Sequencers side by side — one in Preview mode, the other in Sequencer mode — both with their Sidebar open.

Tool — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ Tool tab. Settings for the active tool.
Drag — what dragging LMB does somewhere other than the tool's gizmo. Active Tool (the same action as dragging the gizmo), Tweak (move the image under the cursor), or Select Box (drag a rectangle and select every image partly or wholly inside it).

View — View Settings — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ View Settings.
Proxy Render Size — sets the preview resolution; lower values lose detail but run faster. No Display (preview off entirely), Scene Size (full resolution, no proxies), or 25%, 50%, 75%, 100% (a downscaled resolution, optionally using proxies — even 100% can speed things up thanks to the lower image quality and smaller file size).
Use Proxies — turns on proxies, lower-resolution and/or lower-quality copies of the footage for better preview performance; configure them in the Sidebar's Proxy tab, which only shows in the Sequencer and Sequencer & Preview modes.
Channel — set it to 0 to show every channel; a higher number shows only the channels up to and including it.
Show Overexposed — flags overexposed (blown-white) areas with a zebra pattern, the threshold set by the slider.
Show Missing Media — renders missing images/movies in solid magenta; off, missing content renders fully transparent. Tip: strips with missing content show red in the timeline.

2D Cursor — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ 2D Cursor. The 2D Cursor is the white-red crosshair circle in the preview region (when the 2D Cursor overlay is on); it can act as the Pivot Point that rotation and scaling work around.
Location X, Y — the 2D Cursor's position relative to the video's center; each edge sits 0.5 out, so (0.5, 0.5) lands at the top-right corner. You can also set it with the Cursor tool or by dragging Shift-RMB.

Frame Overlay — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ Frame Overlay. The Frame Overlay lets you display a reference frame to compare against the current one.
Set Overlay Region — drag a rectangle to bound the overlay; instead of the button you can press O while hovering the preview.
Frame Offset — the time gap, in frames, between the reference frame and the current frame.
Overlay Type — how the reference frame appears. Rectangle (part of the reference frame, set by the Overlay Region, over the current frame), Reference (only the reference frame), or Current (only the current frame). Tip: each Video Sequencer can have its own Overlay Type, so you can open two side by side for the current and reference frames.
Overlay Lock — keeps showing the same reference frame even as you move to a different time, by auto-adjusting the Frame Offset.

Safe Areas — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ Safe Areas. Shows guides marking the video area visible across all screens. See also Camera Safe Areas.

Scene Strip Display — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ Scene Strip Display. Controls how Scene Strips appear in the preview.
Shading — the shading mode to use.
Override Scene Settings — uses the current scene's Workbench render settings rather than the strips' referenced scenes; available only for the Wireframe and Solid shading modes.

Annotations — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ View tab ‣ Annotations. For managing the Sequencer's Annotations.

Metadata — Reference: Editor: Video Sequencer; View Type: Preview; Panel: Sidebar ‣ Metadata tab. Lists data baked into whichever movie or image file is currently visible (not the file the selected strip points to) — the filename, creation date, camera model, and so on. It also works for Blender-produced images; see Render Output for what metadata can be included. Other programs may store metadata too, but only text in the header's "Comments" field can be read. Some of this metadata can also appear in the preview via the Metadata overlay.
Tip: Blender can't edit the metadata; use an external program like exiftool instead. For example, to change the "Comments" field:
```text
exiftool --comments="My new comment" name-of-file.png
```
Note: metadata shows only for images/movies that have no effect applied.

## Chromatic Aberration Node

The Chromatic Aberration node simulates a lens dispersing light, refracting different wavelengths (colors) by slightly different amounts to produce subtle color fringing near edges or high-contrast transitions, for realistic lens simulation or stylistic distortion — and it can combine with effects like Vignette or Lens Distortion for convincing camera imperfections. Inputs: Image (standard color input); Type, the method used — Offset (shift individual color channels along X or Y, a simple fast way to get horizontal or vertical fringing), Scale (scale each channel differently from the center for radial dispersion), Directional Blur (blur channels along a direction for motion-like chromatic smearing), or Lens Dispersion (simulate wavelength-dependent refraction for realistic radial rainbow edges near the borders); Axis Offset (which axis the channel offsets occur along — Vertical or Horizontal); Factor (the aberration's intensity, higher values separating channels more); Center (Directional Blur — the pivot for directional transforms, in normalized 0.0-1.0 coordinates); Samples (Directional Blur — the directional-blur sample count, more samples being smoother but slower, the count being 2ⁿ and growing exponentially); and Fit (Lens Dispersion — scale the result to fit the frame, avoiding empty borders from radial dispersion). Output: Image (the result with chromatic aberration applied).

## Camera & Lens Effects Nodes

The Camera & Lens Effects nodes simulate real-world camera and lens imperfections and optical traits, used to add realism, match rendered imagery to live action, or hit specific cinematic looks. They usually sit near the end of a compositing chain to stylize or enhance the final image, and include effects like sensor noise, chromatic aberration, and vignetting that help replicate the subtleties of physical camera systems.

## Sensor Noise Node

The Sensor Noise node simulates the random noise of digital camera sensors, used to match real footage, add realism to renders, or stylistically mimic digital-imaging imperfections. Inputs: Image (standard color input); Luminance Noise (the amount of brightness variation, higher values giving stronger light/dark fluctuations like high-ISO noise); Chroma Noise (the amount of color noise, higher values adding visible color speckling typical of low-light images); and Animated (when on, a new noise pattern each frame mimicking real sensor noise; when off, the noise stays static). Output: Image (the input with sensor noise applied).

## Vignette Node

The Vignette node darkens or fades an image's edges to draw attention to the center, often used artistically or cinematically for focus, mood, or depth. Inputs: Image (standard color input); Factor (the overall strength — 0 disables it, higher values darken the vignette more); and Feather (the softness of the transition from center to edges, higher values giving a smoother fade). Transform: Corner Roundness (the corner shape — 0 gives square corners, 1 a fully circular vignette); Scale (the vignette area's size, smaller values tightening it near the center); Offset (shift the center along X and Y to emphasize a specific area); and Angle (rotate the mask around the image center). Outputs: Image (the result with the vignette) and Mask (the generated vignette mask as grayscale, usable for custom compositing or selective application via mix nodes).

## Brightness/Contrast Node

Brightness/Contrast node — Inputs: Image (standard color input); Brightness (an additive factor that raises overall brightness, negative to darken); and Contrast (a scaling factor that brightens bright pixels while keeping dark ones dark, higher values making details stand out, negative to reduce overall contrast). Output: Image (standard color output). Notes: this node can output values beyond the normal range (above one or below zero), so if you'll mix the output with normal-range images, clamp the values with the Map Value node (Min and Max enabled) or pass them through a Color Ramp node (with normal defaults) — either rescales them to normal range. In the example, intensifying the specular pass without clamping makes the specular pass's sub-one dark areas turn black when added to medium gray, while passing the brightened image through Map Value or Color Ramp gives the desired effect.

### Brightness/Contrast Node 

### Inputs 

Image
Standard color input.

Brightness
An additive adjustment to boost overall image luminance. Use negative values to reduce brightness.

Contrast
A scaling adjustment making bright areas brighter while preserving dark areas dark. Higher values emphasize detail. Use negative values to reduce overall contrast.

### Outputs 

Image
Standard color output.

### Notes 

Output may produce values outside standard range—exceeding 1.0 or below 0.0. For mixing with normal-range images, clamp values using the Map Value node (with Min and Max active) or pass through a Color Ramp node (standard defaults).

Clamp the values to normal range. 

Both approaches rescale values to standard boundaries. In our example, we isolate and intensify the specular pass. Without clamping (bottom path), the specular contribution falls below 1.0 in dark regions, turning dark gray when combined with medium gray. Applying either Map Value or Color Ramp recovers the desired effect.

### Example 

A basic example.

## Color Balance Node

The Color Balance node adjusts an image's color and values. Inputs: Image (standard color input); Factor (how much the node influences the output); and Type, the adjustment method — Lift/Gamma/Gain (adjust the color and tonal range by handling shadows, midtones, and highlights separately), Offset/Power/Slope (ASC-CDL) (a standardized model so the same values give the same result across applications; see Advanced for the implementation), or White Point (adjust which color counts as white, set by the input's color temperature and the desired output temperature). Lift/Gamma/Gain: Lift (the image's darkest areas, the shadows), Gamma (mainly the midtones), and Gain (the brightest parts, the highlights). Offset/Power/Slope (ASC-CDL): Offset (the shadows), Basis (an additional offset allowing a negative value), Power (mainly the midtones), and Slope (the highlights). Input: Temperature (the input primary illuminant's blackbody temperature, default a D65 white point) and Tint (the input white point's green/magenta shift, default 10 matching daylight). Output: Temperature and Tint, the same for the output's white point. Output: Image (standard output image). Advanced — the Offset/Power/Slope formula is out = (i × s + o)^p, where out is the graded pixel value, i the input pixel value (0 to 1, black to white), s the Slope (≥ 0, nominal 1.0), o the Offset (any number, nominal 0), and p the Power (> 0, nominal 1.0).

## Color Correction Node

The Color Correction node adjusts an image's color separately across tonal ranges (highlights, midtones, shadows). Inputs: Image (standard color input) and Mask (how much the node influences the output). Master (targeting the whole tonal range): Saturation (adjust saturation), Contrast (adjust contrast), Gamma (exponential gamma correction affecting midtones, like Power in Color Balance), Gain (a multiplier with stronger effect on highlights, like Slope in Color Balance), and Offset (a value, possibly negative, added linearly to lighten or darken). Highlights / Midtones / Shadows: each range supports the same controls as Master. Tonal Ranges: Midtones Start, Midtones End define where the range splits into highlights, midtones, and shadows (with a smooth 0.2-unit transition between ranges). Channels: Red, Green, Blue choose which RGB channels the correction affects. Output: Color (standard color output).

## Exposure Node

The Exposure node adjusts an image's brightness via a camera exposure parameter (exposure can also be set in the scene Color Management). Inputs: Image (standard color input) and Exposure (a scalar factor adjusting the exposure). Output: Image (standard color output). Example: the node increases the brightness of a window area using a mask.

## Gamma Node

Use the Gamma node to apply a gamma correction — typically converting from gamma-encoded to linear color space, or the reverse with 1/gamma. Inputs: Color (standard color input) and Gamma (an exponential brightness factor applied as output_value = input_value^γ). Output: Color (standard color output).

Use the Gamma node for gamma correction (converting between gamma-encoded and linear color space, or vice versa with 1/gamma).

Color: Standard input.
Gamma: Exponential brightness factor, applied as output = input ^ gamma.

Color: Standard output.

Example of a Gamma node.

### Gamma Node 

Apply gamma correction using this node. Typical use converts from gamma-encoded to linear color space or vice versa with 1/gamma.

### Inputs 

Color
Standard color input.

Gamma
An exponential brightness coefficient applied as \\(output\\_value = input\\_value ^ {\\gamma}\\)

### Outputs 

Color
Standard color output.

### Examples 

Example of a Gamma node.

## Hue Correct Node

The Hue Correct node adjusts an image's hue, saturation, and value through an input curve. Inputs: Image (standard color input) and Factor (how much the node influences the output). Properties: Level (H for Hue, S for Saturation, V for Value) and Curve (see the Curve widget) — by default the curve is a straight line (no change), and the spectrum lets you raise or lower the HSV level for each range of pixel colors by moving the curve points up or down, with pixels whose hue sits at each horizontal point changed by the curve's shape. Output: Image (standard color output).

## Hue/Saturation/Value Node

The Hue/Saturation/Value node transforms an image's colors within the HSV color model. Inputs: Image/Color (standard color input); Hue (the hue rotation offset, 0 being -180° and 1 being +180°, where 0 and 1 give the same result); Saturation (0 removes color for black-and-white, above 1.0 increases saturation); Value (the value shift — 0 makes the color black, 1 keeps it, higher makes it brighter); and Factor (how much the node influences the image). Output: Image/Color (standard color output). Hue/Saturation tips: hues lie on a circle, so a Hue offset of 1 (+180°) on a blue image gives the opposite color, yellow, and applying it again returns blue; grayscale images have no hue, so changing their Hue or Saturation does nothing (you can only brighten or darken via Value, and adding color needs the Mix node); and the values can be animated over time with a Time Curve node or keyframes.

The Hue/Saturation/Value Node applies a color transformation within the HSV Color Model.

Inputs:
Image/Color — the usual color input.
Hue — the hue rotation offset, from 0 (-180°) to 1 (+180°); note 0 and 1 give the same result.
Saturation — 0 drains all color, leaving black-and-white, while above 1.0 boosts saturation.
Value — the value shift: 0 makes the color black, 1 leaves it unchanged, and higher values brighten it.
Factor — how much sway the node has over the image.

Outputs:
Image/Color — the usual color output.

Hue/Saturation Tips — a few things that may help you use this node:
Hues sit on a circle — apply a Hue offset of 1 (+180°) to a blue image and you land on the opposite color, yellow; apply 1 again and you're back to blue.
Grayscale images have no hue — changing Hue or Saturation on a grayscale image does nothing; you can only brighten or darken it via Value. To add color, reach for the Mix node.
Animating the effect — the various values can be animated with a Time Curve node or by keyframing.

HSV Example — a basic example, plus an example of the Factor input used for masking.

### Hue/Saturation/Value Node 

The Hue/Saturation/Value Node implements HSV Color Model transformations.

### Inputs 

Image/Color
Standard color input.

Hue
The hue rotation offset, from 0 (-180°) to 1 (+180°). Note that 0 and 1 produce identical results.

Saturation
A value of 0 produces grayscale, eliminating color. Greater than 1.0 intensifies color saturation.

Value
The brightness offset. Zero makes the color black, 1 preserves it unchanged, and higher values increase brightness.

Factor
The degree to which this node influences the image.

### Outputs 

Image/Color
Standard color output.

### Hue/Saturation Tips 

Consider these guidelines for improved node application:

Hues are laid out on a circle
A Hue offset of 1 (+180°) applied to blue produces the opposite color—yellow. Reapplying it returns blue.

Grayscale images have no hue
Hue or Saturation adjustments have no effect on grayscale. Adjustment is limited to brightness manipulation via Value. For color introduction, employ the Mix node.

Changing the effect over time
Animate adjustments through a Time Curve node or frame-by-frame keyframing.

### HSV Example 

A basic example. 

An example of using the Factor input for masking.

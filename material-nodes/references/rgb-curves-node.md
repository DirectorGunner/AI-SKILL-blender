# Rgb Curves Node, Tone Map Node, Alpha Convert Node, Alpha Over Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RGB Curves Node; Tone Map Node; Alpha Convert Node; Alpha Over Node; Blackbody Node; Color Ramp Node; Combine Color Node; Convert Colorspace Node; Convert to Display Node; Depth Combine Node; Color Nodes; Invert Color Node.

## RGB Curves Node

The RGB Curves node makes level adjustments on each color channel. Inputs: Image/Color (standard color input); Factor (how much the node influences the image); Black Level (Compositor only — the input color mapped to black); and White Level (Compositor only — the input color mapped to white) — and to set the black and white levels, use the eyedropper to sample a color from a displayed image. Properties: Tone (Compositor only) — Standard (the Combined curve applied to each channel individually, which can shift hue) or Filmlike (keeps hue constant); Channel (which curve to show — C Combined, R Red, G Green, B Blue); and Curve (a Bézier curve mapping each input level on X to an output level on Y; see the Curve widget). Output: Image/Color (standard color output). Examples: common curves include lightening shadows, negative, decreasing contrast, and posterize. Color correction with curves: for an image with too much red, run it through RGB Curves and reduce the Red channel (the Mix Color Node docs have an example about fixing overexposure). Color correction with Black/White Levels: since manually adjusting the curves can be hard, the Black and White Levels are another option (really their main purpose) — set the White Level to a bright sand spot in the background and the Black Level to the center of the fish's eye, ideally with the Image Editor showing the original input so you can use the levels' color picker (zooming to pixel level if needed), then fine-tune with the R, G, B curves, using the C curve to compensate for the contrast increase that setting Black and White Levels causes. Effects: change colors by inverting the red channel.

The RGB Curves Node adjusts levels on each color channel.

Inputs:
Image/Color — the usual color input.
Factor — how much sway the node has over the image.
Black Level (Compositor Only) — sets the input color that should map to black.
White Level (Compositor Only) — sets the input color that should map to white.
Tip: to set the black and white levels, use the eyedropper to grab a color sample from a displayed image.

Properties:
Tone (Compositor Only) — Standard (the Combined curve hits each channel on its own, which may shift hue) or Filmlike (holds the hue steady).
Channel — which curve to show: C (Combined), R (Red), G (Green), B (Blue).
Curve — a Bézier curve mapping each input level (X axis) to an output level (Y axis); for the controls, see Curve widget.

Outputs:
Image/Color — the usual color output.

Examples — below are some common curves for desired effects, from left to right: 1. Lighten shadows, 2. Negative, 3. Decrease contrast, 4. Posterize.
Color Correction using Curves — in this example the image is too red, so we run it through an RGB Curves node and pull the Red channel down. The Mix Color Node's docs have an extra example on fixing overexposure.
Color Correction using Black/White Levels — adjusting the RGB curves by hand for color correction can be fiddly; another route is the Black and White Levels, which may well be their real purpose. Here the White Level is set to a bright spot of sand in the background and the Black Level to the center of the fish's eye. To do this efficiently, bring up the Image Editor showing the original input image and use the levels' color picker to grab the right colors, zooming to pixel level if needed; fine-tune with the R, G, and B curves as before. The C curve compensates for the extra contrast that setting Black and White Levels brings.
Effects — changing colors by inverting the red channel.

The RGB Curves node adjusts each color channel independently.

Image/Color: Standard input.
Factor: Blend strength.

Black Level (Compositor only): Input color mapped to black.
White Level (Compositor only): Input color mapped to white.

Tip: Use the eyedropper on displayed images to set levels.

Tone (Compositor only):

Standard: Combined curve applied per-channel (may shift hue).
Filmlike: Hue stays constant.

Channel: Which curve to display (C = Combined, R = Red, G = Green, B = Blue).

Curve: Bézier curve mapping input (X) to output (Y). See Curve widget for controls.

Image/Color: Standard output.

Common curve shapes, left to right: Lighten shadows, Negate, Reduce contrast, Posterize. 

Color correction by reducing red:

The image has excess red. Run it through RGB Curves and dial back the Red channel.

The Mix Color Node documentation covers fixing overexposure.

Alternative approach: Black/White Level.

Manually tweaking RGB curves is tricky. Black and White Levels offer another route. Set White Level to a bright reference (e.g., sand), Black Level to a dark one (e.g., an eye). Using the level pickers on the input image makes this efficient. Fine-tune afterward with R, G, B curves. Use the C curve to offset contrast changes from the level adjustments.

Curve Color correction with Black/White Levels. 

Effect: Inverting the red channel.

### RGB Curves Node 

The RGB Curves Node adjusts tonal levels within each color channel.

### Inputs 

Image/Color
Standard color input.

Factor
The degree of node influence on the image.

Black Level Compositor Only
The input color mapped to black.

White Level Compositor Only
The input color mapped to white.

Tip

Use the eyedropper when identifying black and white levels. Sample colors from displayed image output.

### Properties 

Tone Compositor Only

Standard :

The shared curve applies independently to each channel, potentially causing hue shifts.

Filmlike :

Maintains hue consistency.

Channel
The curve to display.

C :

Combined

R :

Red

G :

Green

B :

Blue

Curve
A Bézier path mapping input (X axis) to output (Y axis). See Curve widget for controls.

### Outputs 

Image/Color
Standard color output.

### Examples 

Common curves achieving frequent outcomes follow.

From left to right: 1. Lighten shadows 2. Negative 3. Decrease contrast 4. Posterize. 

### Color Correction using Curves 

Color correction with curves. 

In this example, an image has excessive red. We employ an RGB Curves node to reduce the Red channel.

The Mix Color Node documentation features another overexposure-correction example.

### Color Correction using Black/White Levels 

Color correction with Black/White Levels. 

Manual curve adjustment for correction presents challenges. Black and White Levels offer an alternative approach, potentially their primary utility.

Here, the White Level is calibrated to a bright sand area, and the Black Level to the fish eye interior. For efficiency, display the input image in the Image Editor. Use the levels' picker to select directly from displayed content, zooming to pixel precision as needed.

Fine-tuning proceeds with R, G, B curves as in the prior example.

The C curve compensates for heightened contrast from Black/White Level adjustments.

### Effects 

Changing colors by inverting the red channel.

## Tone Map Node

Tone mapping maps high-dynamic-range colors into the display's more limited range while keeping the appearance as close as possible. This is a legacy node — it's recommended instead to use view transforms in the color management settings and output linear HDR images from the compositor rather than low dynamic range. Inputs: Image (an HDR image); Type, the algorithm — Rh Simple (a simplified Reinhard operator using the image's average luminance, good for quick general-purpose tone mapping) or R/D Photoreceptor (a more complex model of human photoreceptor response allowing finer adaptation, contrast, and color-correction tuning); Intensity (R/D Photoreceptor — below zero darkens, above brightens); Contrast (R/D Photoreceptor — 0 uses an estimate from the input); Light Adaptation (R/D Photoreceptor — 0 global, 1 by pixel intensity); Chromatic Adaptation (R/D Photoreceptor — 0 the same for all channels, 1 independent per channel); Key (Rh Simple — the value the average luminance maps to); Balance (Rh Simple — normally 1, but usable to alter the brightness curve); and Gamma (Rh Simple — set to 1 if unused). Output: Image (an LDR image).

## Alpha Convert Node

The Alpha Convert node changes an image's alpha-channel format. In Blender, Premultiplied Alpha is the standard for compositing and rendering — render layers are premultiplied, and images loaded for rendering or compositing are converted to it. To do a compositing operation with straight alpha (typically a color-correction step that works better on RGB without alpha), use this node, and convert back to premultiplied before the Group Output node to avoid artifacts. Inputs: Image (standard color input) and Type, the conversion direction (see Alpha Channel for the difference) — To Premultiplied (Straight → Premultiplied) or To Straight (Premultiplied → Straight). Output: Image (standard color output).

## Alpha Over Node

The Alpha Over node composites two images by layering the Foreground over the Background with standard alpha blending — commonly used to combine rendered elements, overlays, or effects in one image, such as text, logos, or transparent effects over footage. Inputs: Background (the background image); Foreground (the image placed over it); Factor (the foreground's opacity, 0 fully transparent to 1 fully opaque); Type, the compositing method — Over (the standard alpha-over, placing the foreground by its alpha), Disjoint Over (like Over but assuming the background was held out by the foreground, for cleaner edges when layering many), or Conjoint Over (like Over but assuming the foreground overlaps or extends into the background, for a more—but not fully—opaque foreground); and Straight Alpha (whether the foreground uses straight, non-premultiplied alpha — usually left off since most compositor images are premultiplied, enabled only if the foreground was explicitly converted to straight). Output: Image (the combined result). Examples — Disjoint/Conjoint/Over: the example shows how the methods differ, assembling four layers with Disjoint, Conjoint, and Over to create depth between overlapping elements. Fade In: a Time Curve Node animates the Factor from 0 to 1 over 30 frames for a smooth text fade-in over a background.

## Blackbody Node

The Blackbody node converts a blackbody temperature to an RGB value, useful for materials that emit light at naturally occurring frequencies. Input: Temperature (in Kelvin). This node has no properties. Output: Color (an RGB color output). Example: the color ranges of the Blackbody node.

The Blackbody node maps thermal radiation temperature to RGB.

Use this for materials emitting light at natural frequencies.

Temperature: Heat in Kelvin.

This node has no properties.

Color: RGB output.

Example of the color ranges of the Blackbody node.

### Blackbody Node 

The Blackbody node translates thermal radiation frequency to RGB output. This proves beneficial for materials emitting light at naturally-occurring wavelengths.

### Inputs 

Temperature
The emission temperature measured in Kelvin.

### Properties 

This node has no properties.

### Outputs 

Color
RGB color output.

### Examples 

Example of the color ranges of the Blackbody node.

## Color Ramp Node

The Color Ramp node maps values to colors through a gradient. Input: Factor (the value to map — 0.0 gives the leftmost color, 1.0 the rightmost). Properties: Color Ramp (see the Color Ramp Widget). Outputs: Image/Color (standard color output) and Alpha (standard alpha output). Examples — Creating an alpha mask: an overlooked use is turning a black-and-white image into a colored one with transparency — feed a black-and-white swirl (lacking alpha) into Color Ramp as the Factor, set the left end fully transparent and the right fully red, and the node outputs an image transparent where the input is black and opaque where it's white. Colorizing an image: add several colors to the gradient to turn a black-and-white image into a flaming swirl — gray shades map to blue, yellow, and red (all opaque), so black becomes blue (the first stop), grays become corresponding gradient colors, and white becomes red.

The Color Ramp Node maps values to colors through a gradient.

Inputs:
Factor — the value to map; 0.0 gives the leftmost color, 1.0 the rightmost.

Properties:
Color Ramp — see Color Ramp Widget.

Outputs:
Image/Color — the usual color output.
Alpha — the usual alpha output.

Examples:
Creating an Alpha Mask — an easily missed use of the Color Ramp is turning a black-and-white image into a colored, partly transparent one. In the example a black-and-white swirl lacking an alpha channel feeds the Color Ramp as a Factor; the ramp is fully transparent at its left end and fully red at its right, so (as the Viewer node shows) it outputs an image transparent where the input is black and opaque where it's white.
Colorizing an Image — here several colors are added to the gradient, turning a black-and-white image into a flaming swirl. The input's grays map to three fully opaque colors — blue, yellow, red: black areas become blue (the first stop), gray areas become a matching gradient color (bluish through yellow to reddish), and white areas become red.

The Color Ramp node maps scalar values to colors via a gradient.

Factor: The value to translate (0.0 = left color, 1.0 = right).

Color Ramp: See Color Ramp Widget.

Image/Color: Color output.
Alpha: Alpha output.

A common technique: convert a black-and-white image (without alpha) to a colored, transparent result.

In this case, a grayscale swirl (lacking alpha) feeds the Color Ramp as Factor. The gradient runs from transparent (left) to opaque red (right). The Viewer output shows: transparent where black, opaque where white.

Another approach: layer multiple colors onto a grayscale image.

Here, blue-yellow-red span the gradient, converting grayscale to color. Black maps to blue (first stop), gray to intermediate tones, white to red (last stop).

### Color Ramp Node 

The Color Ramp Node maps numeric values to colors utilizing a gradient.

### Inputs 

Factor
The numeric input to map. Zero yields the gradient's left color; 1.0 yields the right.

### Properties 

Color Ramp
See Color Ramp Widget.

### Outputs 

Image/Color
Standard color output.

Alpha
Standard alpha output.

### Examples 

### Creating an Alpha Mask 

A common, underutilized application of Color Ramp converts monochrome imagery into colored, transparent output.

Our example begins with a black-and-white swirl, lacking an alpha channel. The Color Ramp accepts this as input Factor.

The gradient spans from transparent (left edge) to opaque red (right edge). The Viewer node shows the result: transparent in black regions and fully visible where the input is white.

### Colorizing an Image 

A second example assigns multiple gradient colors, converting grayscale into vibrant flames.

Input gray levels map to three hues—blue, yellow, red—all completely opaque. The Color Ramp substitutes blue at black input, progresses through the gradient for gray tones, and outputs red at white.

## Combine Color Node

The Combine Color node builds an image from its composite color channels, supporting multiple color models per the Mode property. Inputs: depend on Mode (see below), plus Alpha (the channel handling transparency). Properties: Mode, the color model to output — RGB (combine Red, Green, Blue), HSV (Hue, Saturation, Value), HSL (Hue, Saturation, Lightness), YCbCr (Luminance, Chrominance Blue, Chrominance Red), with a Color Space option (ITU 601, ITU 709, JPEG), or YUV (Luminance, U chrominance, V chrominance). Output: Image (standard image output). Examples — Blur Alpha: take the Alpha channel, blur it, and recombine it with the colors so the edges blend into a scene instead of having a hard edge (almost like anti-aliasing but in 3D), useful when adding CG to live action to remove hard edges, and animating it broadly makes the object appear to "phase" in and out. Increase Luminance: a Math (Multiply) node raises the luminance channel (Y) to brighten the image — and a tip notes that when adjusting these channels through a Color Ramp, the Cardinal scale gives accurate representation while the Exponential scale on luminance gives a high-contrast effect.

Merges four grayscale channels into one color image according to a chosen Color Model.

Inputs — these depend on the Mode property (below).
Alpha — the output color's opacity.

Properties:
Mode — the color model to use. RGB (Red, Green, Blue), HSV (Hue, Saturation, Value), or HSL (Hue, Saturation, Lightness).

Output:
Color — the usual color output.

The Combine Color node merges four grayscale inputs into a single color based on the chosen color model.

The inputs depend on the Mode (below).

Alpha: Opacity of the output.

Mode: Color space used.

RGB: Red, Green, Blue.
HSV: Hue, Saturation, Value.
HSL: Hue, Saturation, Lightness.

Color: Standard output.

### Combine Color Node 

Assembles four grayscale channels into a color image using a specified Color Model.

### Inputs 

Channel inputs depend on the Mode property (see below).

Alpha
Output color transparency.

### Properties 

Mode
The color space to apply.

RGB :

Red, Green, Blue.

HSV :

Hue, Saturation, Value.

HSL :

Hue, Saturation, Lightness.

### Output 

Color
Standard color output.

## Convert Colorspace Node

The Convert Colorspace node converts images between color spaces. Note that images are auto-converted to linear color space unless set otherwise in the image's Color Space option. Input: Image (standard color input). Properties: From, To (the input image's color space and the one to convert to) — the available list depends on the active OCIO config, with the defaults described in the Default OpenColorIO Configuration. Output: Image (standard color output).

## Convert to Display Node

The Convert to Display node runs an OpenColorIO display, view, and look transform on a scene-linear image, turning linear render data into a color-accurate version for a particular display-and-view pairing per the active color management settings. It complements the Convert Colorspace node by supporting display-view-look combinations (not represented as individual color spaces in modern OCIO configs), and unlike Convert Colorspace it reproduces the same transforms used by Save As Render or the Render View display. Note: it offers no exposure, gamma, or white-point controls — use the dedicated Exposure, Gamma, or RGB Curves nodes for those. Workflow: it's often used for extra grading control in place of the color-management display and view transform; to avoid stacking transforms twice, put a second Convert to Display node — Standard view transform, Inverse on — as the graph's last node, and set the scene's view transform to Standard — the compositor then outputs working-space colors as usual but with grading baked in, which (unlike Raw-view-transform workflows) works correctly with the video sequencer and OpenEXR output. Inputs: Image (the scene-linear input to convert) and Invert (convert from display space back to scene-linear, though not all view transforms invert exactly, so the result may differ from the original). Properties: Display (the target display device in the current OCIO config; see Display), View (the view transform for the display; see View), and Look (the optional look transform, possibly None per the config; see Look). Output: Image (the converted image suited to the chosen display, view, and look).

## Depth Combine Node

The Depth Combine node merges two images using their depth maps, overlaying them by their depth values to decide which parts of one are in front of the other. Inputs: A (the background image), Depth A (its depth pass), B (the foreground image), Depth B (its depth pass), Use Alpha (also carry over the chosen image's pixel alpha, so a partly or fully transparent pixel makes the result partly transparent, letting the background show through), and Anti-Alias (apply anti-aliasing to avoid artifacts at sharp or high-contrast edges). Outputs: Result (if the depths are equal it uses the foreground, otherwise the smaller depth wins; see Z-buffer) and Depth (the combined depth, for chaining several Depth Combine nodes). Examples: the render outputs of two scenes — a size-1.3 sphere and a size-1.0 cube at the same place — are mixed; the cube tips forward so its center corner is nearer than the sphere surface (Depth Combine uses the cube's pixels there), but the larger sphere doesn't fit entirely inside the cube, so where the cube's sides recede the sphere's sides become closer and its pixels are used. It can combine a foreground with a background matte painting (Walt Disney pioneered multi-plane mattes, painting three or four partial mattes on glass at different depths so minimal camera moves created depth). Note — valid input: the depth sockets don't accept fixed values (they need a vector set, see Map Value), and image sockets won't accept a color since they lack UV coordinates. It can also merge two images: using the sphere/cube depths but different images yields the shown result — a render scene mixed with a flat image where the orange cube is 10 units from the camera, the blue ball 20, and the image depth is 15, inserting it between them so the cube appears on the green image. Note — invisible man effect: a foreground image with higher alpha than the background, mixed via Depth Combine with a slightly magnified background, distorts the background around the transparent area enough to look like a Fresnel-lens object.

## Color Nodes

The Color Nodes adjust an image's colors — for example raising contrast, warming it, or overlaying another image.

## Invert Color Node

The Invert Color node inverts the input image's colors to produce a negative. Inputs: Color (standard color input), Factor (how much the node influences the image), Invert Color (invert the color channels), and Invert Alpha (invert the alpha channel). Output: Color (standard color output). Example: the Invert node inverts a mask.

Flips the input image's colors to produce a negative.

Inputs:
Color — the usual color input.

Properties — this node exposes no properties.

Outputs:
Color — the usual color output.

### Invert Color Node 

Produces a negative by reversing input image colors.

### Inputs 

Factor
The node's influence strength on the image.

Color
Standard color input.

### Properties 

This node has no properties.

### Outputs 

Color
Standard color output.

# Mix Color Node, Rgb To Bw Node, Separate Color Node, Set Alpha Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mix Color Node; RGB to BW Node; Separate Color Node; Set Alpha Node; Creative Nodes; Kuwahara Node; Pixelate Node; Posterize; Sepia Node; Split Toning Node; Tune Image Node; Unsharp Mask Node; Anti-Aliasing Node; Bilateral Blur Node; Blur Node; Bokeh Blur Node.

## Mix Color Node

The Mix Color node mixes value, color, and vector inputs using a factor that controls the interpolation amount, with the Color mode adding blending modes. Inputs: Factor (how much A and B are mixed) and A/B (the two inputs). Properties: Data Type (float, vector, color, or rotation); Factor Mode (Vector only — Uniform, where one float controls the factor, or Non-Uniform, where a vector controls it per XYZ channel); Mix (Color only — the blend mode from the menu; see Color Blend Modes), with options Add, Subtract, Multiply, Screen, Divide, Difference, Darken, Lighten, Overlay, Color Dodge, Color Burn, Hue, Saturation, Value, Color, Soft Light, Linear Light; Clamp Factor (limit the factor to 0.0-1.0, otherwise the node uses Extrapolation); and Clamp Result (Color only — limit the Result to 0.0-1.0). Output: Result (the mix in the chosen data type). Examples — Fixing overexposure: darken an overexposed render and raise contrast — the top RGB Curves node darkens by linearly scaling each value smaller, the bottom one raises contrast by making small values smaller and large ones larger, and a Mix node blends the two. Watermark images: long ago a mark was pressed into drying paper to identify its maker, barely visible except in the right light (an early subliminal advertising); today people watermark images to mark intellectual property, for subliminal advertising, or to track proliferation, and Blender has a full set of tools to encode a watermark and detect one. Encoding: build a personal watermark (a name, word, shape, or hard-to-replicate image — neutral gray works best with this method, but any color or pattern works, from one pixel to a gradient); in the example it's encoded at a specific location via the Translate node (so you only look there later), converted to grayscale with the RGB to BW node, reduced to one-tenth intensity with the Map Range node, and added with the Add node (a Mix node in Add mode) so marked pixels become slightly brighter — scale it less or use a contrasting color if you want it noticed, and experiment with other mix settings and rigs. Decoding: compare a suspect image to your non-watermarked original with the node tree shown, where the Mix node uses Difference and the Map Value node amplifies whatever difference remains, making the original mark clearly stand out.

The Mix Color Node mixes value, color, and vector inputs, using a factor to control the amount of interpolation; the Color mode adds extra blending modes.

Inputs:
Factor — how much mixing happens between the A and B inputs.
A/B — the two inputs mixed together.

Properties:
Data Type — the data type used for mixing; the node supports float, vector, color, and rotation data types.
Factor Mode (Vector only) — set to Uniform or Non-Uniform: Uniform uses a single float for the factor, Non-Uniform uses a vector controlling the factor for each XYZ channel separately.
Mix (Color only) — pick a blend mode from the select menu (see Color Blend Modes for details on each): Add, Subtract, Multiply, Screen, Divide, Difference, Darken, Lighten, Overlay, Color Dodge, Color Burn, Hue, Saturation, Value, Color, Soft Light, Linear Light.
Clamp Factor — limit the factor to between 0.0 and 1.0; unchecked, the node operates using Extrapolation.
Clamp Result (Color only) — limit the Result to between 0.0 and 1.0.

Outputs:
Result — the mix result, in the selected data type.

Examples: below are blending-mode examples plus some practical use cases, such as blending a colored pattern with a flat color (top row) and with a circular mask (bottom row).
Fixing overexposure: the compositing setup fixes an overexposed render by darkening it and increasing contrast. The top RGB Curves Node darkens the image by linearly scaling each color value down; the bottom curve node raises contrast by making small values smaller and large values larger; finally the Mix node blends the two together.
Watermark Images: in the old days a pattern pressed into the paper mush as it dried made a mark identifying who made the paper and where it came from, barely perceptible except in just the right light — probably the first form of subliminal advertising. Nowadays people watermark images to mark them as personal intellectual property, for subliminal advertising of the author or hosting service, or simply to track an image's spread across the web. Blender provides a complete set of tools to both encode your watermark and tell whether an image carries it.
- Encoding your watermark in an image: first build your own watermark — a name, a word, or a shape or image not easily replicated; neutral gray works best with the suggested encoding method, but you may use other colors or patterns, from a single pixel to a whole gradient. In the example, the watermark is encoded at a specific location using the Translate node (so later you only have to look at that spot for the mark), converted to grayscale numbers with the RGB to BW node, then fed into the Map Range node to reduce the mark to one-tenth of its original intensity. The Add node (a Mix node with blending mode Add) adds the corresponding pixels, making the ones holding the mark ever so slightly brighter. Of course, to have people notice the mark, scale it less or use a contrasting color — and there are many other approaches with different mix settings and fancier rigs, so experiment.
- Decoding an image for your watermark: when you see an image you think might be yours, compare it to your non-watermarked stock original with a node tree where the Mix node is set to Difference and the Map Value node amplifies any difference, so the original mark clearly stands out.

### Mix Color Node 

The Mix Node blends values, vectors, and colors by interpolating between inputs A and B, controlled by a factor. When set to Color mode, additional blending modes become available.

### Inputs 

Factor
Determines the interpolation degree between A and B.

A/B
The two inputs to blend together.

### Properties 

Data Type
The data category for blending. Float, vector, color, and rotation types are supported.

Factor Mode (Vector only)
Selects between Uniform (single float factor) and Non-Uniform (vector factor per XYZ channel separately).

Mix (Color only)
Select from available Blend modes. Consult Color Blend Modes for detailed descriptions.

Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light

Clamp Factor
Restricts factor to 0.0 to 1.0 range. When unchecked, Extrapolation applies.

Clamp Result (Color only)
Limits Result to 0.0 to 1.0 bounds.

### Outputs 

Result
Outputs the mix outcome using the selected data category.

### Examples 

Below are demonstrations of blending modes and practical applications.

Blending a colored pattern with a flat color (top row) and a circular mask (bottom row). 

### Fixing overexposure 

The Compositing network demonstrates correcting overexposed output via darkening and contrast boost.

Example node setup showing two RGB Curves nodes and a Mix node for composition. 

The upper RGB Curves Node reduces brightness by linearly scaling color down.

The lower Curves node enhances contrast via nonlinear scaling—small values become smaller, large values become larger.

Finally, the Mix node combines both adjustments.

### Watermark Images 

Watermarking identifies work ownership or origin. In papermaking, a watermark is an impressed pattern made during drying, marking maker identity. Contemporary digital watermarks establish intellectual property ownership, provide subtle branding, or track distribution.

Blender supplies complete functionality for both embedding and verifying watermarks.

#### Encoding your Watermark in an Image 

Start by creating a personal watermark—text, symbol, or distinctive image hard to replicate. Though neutral gray functions optimally with the proposed technique, any color or pattern works. Size flexibility ranges from single pixel to complete gradient.

Below, we position the watermark using the Translate node; later we need only check a specific area. The RGB to BW node converts the color image to grayscale, fed to Map Range to diminish the mark to one-tenth strength.

The Add node (Mix with Add mode) sums pixel values, making watermarked areas subtly brighter.

Embedding a watermark in an image. 

For visible watermarks, scale less aggressively or use contrasting colors. Many alternate approaches exist with different mix settings and refined rigs. Experimentation is encouraged!

#### Decoding an Image for your Watermark 

When examining suspect images, employ the tree below to compare against your original unmarked copy. The Mix node uses Difference mode to isolate variations, and the Map Value node magnifies contrast. Your watermark stands out distinctly.

Checking an image for your watermark.

## RGB to BW Node

The RGB to BW node turns a color image black-and-white, outputting its luminance. Note that you can connect Color sockets directly to Value sockets in node graphs, which also converts to black-and-white, so this node isn't always necessary. Input: Image (color image input). Output: Value (grayscale value output).

The RGB to BW Node turns a color image black-and-white by outputting its luminance.

Note: you can wire Color sockets straight into Value sockets in a node graph, which also converts to black-and-white, so this node isn't always needed.

Inputs:
Image — a color image input.

Outputs:
Value — a grayscale value output.

### RGB to BW Node 

The RGB to BW Node creates monochrome output by computing image luminance.

Note

Color sockets can directly attach to Value sockets in node graphs, achieving the same conversion. This node therefore becomes optional in many cases.

### Inputs 

Image
Color image input.

### Outputs 

Value
Grayscale value output.

## Separate Color Node

The Separate Color node splits an image into its composite color channels, outputting multiple color models per the Mode property. Input: Image (standard image input). Properties: Mode, the color model to output — RGB (three outputs: Red, Green, Blue), HSV (Hue, Saturation, Value), HSL (Hue, Saturation, Lightness), YCbCrA (Luminance, Chrominance Blue, Chrominance Red), with a Color Space option (ITU 601, ITU 709, JPEG), or YUV (Luminance, U chrominance, V chrominance). Outputs: depend on Mode (above), plus Alpha (the transparency channel). Examples — Blur Alpha: take the Alpha channel, blur it, and recombine it so edges blend into a scene rather than ending hard (almost like 3D anti-aliasing), useful when adding CG to live action, and animating it broadly makes the object appear to "phase" in and out. Increase Luminance: a Math (Multiply) node raises the luminance channel (Y) to brighten the image — and when adjusting these channels through a Color Ramp, the Cardinal scale is accurate while the Exponential scale on luminance gives high contrast.

Splits an image into its channels according to a chosen Color Model.

Inputs:
Color — the usual color input.

Properties:
Mode — the color model to output. RGB (Red, Green, Blue), HSV (Hue, Saturation, Value), or HSL (Hue, Saturation, Lightness).

Outputs — these depend on the Mode property (above).
Alpha — the opacity value.

The Separate Color node splits a color into its channels per a given color model.

Color: Standard input.

Mode: Color space to output.

RGB: Red, Green, Blue.
HSV: Hue, Saturation, Value.
HSL: Hue, Saturation, Lightness.

The outputs depend on Mode (above).
Alpha: Opacity value.

### Separate Color Node 

Decomposes image channels according to a specified Color Model.

### Inputs 

Color
Standard color input.

### Properties 

Mode
The color space for channel output.

RGB :

Red, Green, Blue.

HSV :

Hue, Saturation, Value.

HSL :

Hue, Saturation, Lightness.

### Outputs 

Channel outputs depend on the Mode property (see above).

Alpha
The opacity value.

## Set Alpha Node

The Set Alpha node gives an image an alpha channel. Inputs: Image (standard color input); Alpha (set for the whole image via the field, or per pixel via the socket); and Type, how the alpha mixes with the image — Apply Mask (multiply the input's RGBA by the Alpha input, output using Premultiplied Alpha) or Replace Alpha (replace the input's alpha with the Alpha input, output using Straight Alpha). Output: Image (standard color output). Note: this isn't a general-purpose fix for compositing an image lacking alpha — prefer chroma keying or difference keying where possible — and it's most used (with a suitable socket input) when those techniques can't be applied directly. Example — Fade to black: to move the audience between shots, a common technique fades the scene to a black screen (you can fade to white or any color, but black neutrally resets the viewer); using Set Alpha, the swirl image's alpha is ignored and instead a Time Curve node feeds a factor from 0.0 to 1.0 over 60 frames (~2 seconds), the curve being exponential so the blackness fades in slowly then accelerates, and Set Alpha needs no input image (a flat black color is used) to create a black image whose alpha goes 0.0 to 1.0 (transparent to opaque) — think of alpha as a multiplier for pixel vividness — which an Alpha Over node combines fully (Factor 1.0) into the composite, giving an image sequence that fades to black over two seconds. Note — no scene information used: this tree uses no Render Layer node and no Blender scene data, demonstrating compositing separate from modeling and animation (a Render Layer could replace the Image layer with the same effect). Fade in a title: present your title over a background, flying or fading it in — to fade, use Set Alpha with a Time Curve node, where the Time curve provides the Alpha to the input socket and the current Render Layer node supplies the title image, with Alpha Over mixing the background swirl and the alpha title into the composite. Colorizing a BW image: the blue tinge of the render input colors the swirl — use Set Alpha's color field with this kind of tree to add a consistent color to a BW image, threading the input image and the Set Alpha node into an Alpha Over node, and use the Set Alpha Alpha value for the degree of colorization.

## Creative Nodes

The Creative Nodes category provides artistic, stylistic effects that change an image's appearance beyond simple correction or realism, enabling expressive, illustrative, or cinematic looks by reworking color, tone, texture, and clarity in distinctive ways. They can emulate analog photography, painterly effects, stylized post-processing, or other creative treatments, and are often applied toward the end of a compositing chain to finalize a scene's mood, style, or aesthetic.

## Kuwahara Node

The Kuwahara node implements the Kuwahara filter and its anisotropic variant — a smoothing filter that tries to preserve image edges, the anisotropic variant's smoothing resembling brush strokes for stylized painting effects. Inputs: Image (standard color input); Size (the smoothing neighborhood's size, where large values may add artifacts in highly detailed areas and, for the anisotropic method, slow the filter); Type — Classic (a simple method averaging the local square neighborhood while preserving edges, blocky due to the square shape, with no tuning parameters but faster) or Anisotropic (a complex method averaging the neighborhood along the edge flow to preserve edges, giving painterly results with multiple tuning parameters but slower); Uniformity (how uniform the edge directions are — non-uniform directions are rarely wanted, so raise this until the result stops changing significantly, as further increases worsen results and add compute time); Sharpness (the edges' sharpness); Eccentricity (how thin and directional the filter is — low for circular omnidirectional features, high for thin directional ones); and High Precision (Classic — a more precise but slower method, for when the output has undesirable noise). Output: Image (standard color output). Notes — Iterations: chain the node multiple times to apply the filter repeatedly, producing flatter filtering. Performance: it can be costly for large sizes and high resolutions, so to improve performance, scale the image down, filter, then scale back up — which works well since the filter already attenuates low-frequency detail.

## Pixelate Node

The Pixelate node reduces an image's detail by making individual pixels more prominent, giving a blocky, mosaic-like look where fine detail is obscured and the image is represented with larger, more noticeable pixels. Inputs: Color (standard color input) and Size (the output pixel size, measured in pixels). Output: Color (standard color output).

## Posterize

The Posterize node cuts the number of colors in an image, turning smooth gradients into sharp transitions — useful for generating masks, particularly for rotoscoping. Inputs: Image (standard color input) and Steps (the number of colors per channel — a value of 8 gives 8³ = 512 total colors). Output: Image (standard color output).

## Sepia Node

The Sepia node lays a warm, brownish tint over an image to emulate vintage photographs or old film prints, useful for nostalgic, cinematic, or stylized grades that mimic chemical sepia toning. Inputs: Image (standard color input); Contrast (the sepia effect's tonal contrast — higher values deepen shadows and brighten highlights, widening the dynamic range); Tone (the tint's hue — lower values shift toward reddish-brown, higher toward yellow or golden); and Saturation (the tint's intensity — 0 gives pure monochrome, higher values a richer color). Output: Image (the result with the sepia effect).

## Split Toning Node

The Split Toning node tints the highlights and shadows of an image with different colors — a common photography and grading technique for mood, contrast, or style by giving bright and dark regions distinct tones (e.g. warm highlights with cool shadows for a cinematic or nostalgic look, or complementary tones for a dramatic effect). Inputs: Image (standard color input); Highlights (the tint for bright areas); Factor Highlights (how strongly that color affects the bright regions — 0 disables it, 1 applies it fully); Shadows (the tint for darker areas); and Factor Shadows (the shadow tint's strength). Transition: Balance (shift the midpoint dividing highlights from shadows — raising it favors the highlight color, lowering it the shadow color) and Smoothness (how gradually the image moves between tinted shadows and highlights — higher values blend smoothly, lower ones abruptly). Output: Image (the result with split toning).

## Tune Image Node

The Tune Image node is a quick, all-in-one way to improve an image's overall look by adjusting key parameters like contrast, clarity, and sharpness — a compact correction tool for fine-tuning rendered or composited images without several separate nodes. Inputs: Image (standard color input); Contrast (the gap between light and dark areas — raising it deepens shadows and brightens highlights, lowering it flattens the tonal range); Color Boost (strengthen color intensity without oversaturating, for dull or washed-out images); Clarity (emphasize midtone contrast and local detail for more depth and definition); Detail (the visibility of small-scale texture — higher brings out fine detail, lower smooths it); Sharpen (sharpen edges by boosting high-frequency detail, countering blur from downsampling or lenses); and Preserve Colors (keep the natural color balance during tonal adjustments — off, contrast and clarity may shift hue or saturation). Output: Image (the tuned result).

## Unsharp Mask Node

The Unsharp Mask node boosts an image's apparent sharpness by increasing edge contrast — despite the name it doesn't blur, but sharpens by subtracting a blurred (unsharp) version from the original and emphasizing the resulting edges, a technique common in photography, printing, and digital compositing for clarity and definition. Inputs: Image (standard color input); Radius (how wide an area is sampled when detecting edges — larger values reach broader regions and bigger features, smaller ones focus on fine detail); Factor (the sharpening intensity — higher values give stronger edge contrast but can cause halos or artifacts if overdone); and Threshold (how different a pixel must be from its surroundings before sharpening applies — higher values limit it to more distinct edges, reducing noise). Output: Result (the sharpened image).

## Anti-Aliasing Node

The Anti-Aliasing node removes jagged edges. Inputs: Image (standard color input); Threshold (edge-detection sensitivity across the whole image); Contrast Limit (the contrast level to consider when detecting edges — since the eye doesn't perceive all edges equally and tends to mask low-contrast edges amid much higher surrounding contrast, anti-aliasing those unperceived edges makes artifacts, and this quantifies the difference between low- and high-contrast neighboring edges); and Corner Rounding (detect corners to preserve the original shape — 0 means no corner detection or rounding, and higher values better preserve corners). Output: Image (standard color output). Examples show that changing the threshold affects all edges, the contrast limit affects neighboring edges below it, and corner detection/rounding off (0) smooths corners as artifacts while full detection preserves the sharp edges.

## Bilateral Blur Node

The Bilateral Blur node does a high-quality adaptive blur, softening the image while keeping sharp edges — useful for smoothing noisy render passes to save computation (e.g. ray-traced ambient occlusion, blurry refractions/reflections, soft shadows) or for non-photorealistic effects. Inputs: Image (standard color input — with only this connected, it blurs based on the edges in the source); Determinator (if connected, the source defining edges/borders for the blur, a big advantage when the source image is too noisy but normals plus the Z-buffer can still define exact object borders); Size (the blur size in pixels); and Threshold (pixels enter the blur area when the average difference between their determinator and the center pixel's is below this). Output: Image (standard color output).

## Blur Node

The Blur node blurs an image, offering several modes. Inputs: Image (standard color input) and Size (an optional input multiplied with the X/Y blur radius, also accepting a value image to control the radius by a mask, ideally mapped 0 to 1). Type, differing in how they handle sharp edges, smooth gradients, and the highs/lows: Flat (blur everything uniformly), Tent (preserve highs and lows better via a linear falloff), Quadratic (Gaussian-like but a little faster and slightly worse), Cubic (keep the highs while giving an almost out-of-focus blur that smooths sharp edges), Gaussian (best-looking but slowest), Fast Gaussian (a Gaussian approximation), Catmull-Rom (keeps sharp contrast edges crisp), and Mitch (much like Cubic — highs kept, with a soft defocus-style blur over sharp edges). Also: Extend Bounds (let the blurred image extend past its original size) and Separable (a faster approximation blurring horizontally and vertically independently). Output: Image (standard color output).

## Bokeh Blur Node

The Bokeh Blur node makes a bokeh-type blur similar to Defocus, but with an in-focus region defined in the Compositor and more flexibility in the blur type via the Bokeh Image node, plus performance optimizations like restricting the calculation area and masking. Inputs: Image (standard color input); Bokeh (an input for the Bokeh Image node); Size (the blur amount in pixels, either a single value over the whole image or a variable value from an input image); and Bounding Box (use a Box Mask matte node or a Mask input node to limit where the blur applies, handy for saving composite time while developing a node system by filtering only a small area per adjustment). Output: Image (standard color output). Examples: an ID-masked alpha image can blur a background while foreground objects stay in focus (use the Dilate Node to avoid strange edges); the Z pass can be visualized via a Map Range node and a Color Ramp node (then a multiply Math node so a blur value above one applies to objects outside the focal range); and a manually made grayscale image can define sharp and blurry areas of an existing image (again with a Multiply Node for a blur value above one).

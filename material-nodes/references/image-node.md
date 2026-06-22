# Image Node, Image Coordinates Node, Image Info Node, Input Nodes ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Image Node; Image Coordinates Node; Image Info Node; Input Nodes; Mask Node; Render Layers Node; Scene Time Node; Time Curve Node; Sequencer Strip Info Node; Channel Key Node; Chroma Key Node; Color Key Node; Color Spill Node; Difference Key Node; Distance Key Node; Keying Nodes; Keying Node; Keying Screen Node.

## Image Node

The Image node injects any image format Blender supports. It has no input sockets. Properties: Image (a selection of media types — for controls see the Data-Block Menu, for options Image Settings); Source (the image type — Single Image, Movie, etc.; see Image Settings); Frames (how many frames of a movie-type image to play, after which it pauses unless Cyclic is on — to play the whole video, use Match Movie Length in the Image Editor's Sidebar and copy its Frames here); Start Frame (the scene frame at which the video starts); Offset (frames to offset the video earlier — i.e. how many starting frames to skip); Cyclic (loop after the last frame); Auto-Refresh (update the video texture in the 3D Viewport while moving through the timeline); Color Space (the space the file was saved in; see Image Settings); and Alpha (how the image uses its alpha channel; see Image Settings). A hint notes Blender plays video textures at the scene's frame rate rather than their own, so they run faster or slower if the rates differ, and you can work around this with a Driver on Offset: `#(frame - StartFrame) * (VideoFrameRate - SceneFrameRate) / SceneFrameRate`, replacing the names with the numbers. Outputs (the first two are the minimum): Image (standard color output) and Alpha (a separate alpha value) — and for a multi-layer format like EXR, each layer becomes its own socket.

The Image node loads an external image.

Inputs — this node takes no inputs.

Properties:
Image — see Data-Block Menu.

Outputs:
Color — the usual color output.

### Image Node

Image node.

The Image node opens access to an image file, letting you conveniently enter and switch images for several nodes across the tree.

See also

Image Info Node

### Inputs

No inputs on this node.

### Properties

Image Data-Block
A data-block selector — pick an image that exists or open a new one through the file browser.

### Outputs

Image
The image file picked from the data-block selector.

## Image Coordinates Node

The Image Coordinates node outputs coordinate fields for an input image, giving each pixel's location in different coordinate spaces — useful for procedural texturing, compositing effects, or image-based masking — computed per pixel from the image resolution and placement in the compositor's virtual space. Input: Image (used to determine dimensions and placement). Outputs: Uniform (normalized coordinates centered at zero, scaled by the image's largest dimension, for aspect-ratio-independent procedural effects, like Object coordinates in shader nodes), Normalized (normalized 0-to-1 coordinates across the image, with half-pixel offsets to align to pixel centers), and Pixel (pixel-space coordinates for each pixel's center, integer-based with a half-pixel offset).

## Image Info Node

The Image Info node reports an image's spatial and transformation information in the compositor, useful for procedural effects that depend on image size or position (e.g. building a vignette with math nodes, or scaling effects to image dimensions). Input: Image (the image to read). Outputs: Dimensions (the image size in pixels with transformations applied), Resolution (the image's width and height in pixels), Location (its position in compositing space), Rotation (its rotation in radians about its center), and Scale (its scale relative to its original size in compositing space).

### Image Info Node

The Image Info node outputs image and animation parameters. Useful for generating geometry-node parameters from arbitrary image data. Information is either general (whole image) or frame-specific.

### Inputs

Image
Source image to query.

Frame
Frame index (for frame-specific outputs).

### Outputs

Width
Pixel count along X axis. Frame-specific.

Height
Pixel count along Y axis. Frame-specific.

Has Alpha
Boolean: true if the transparency channel differs from 1 for any pixel in this frame. Frame-specific.

Frame Count
Total frames in the image or sequence (always 1 for static images).

FPS
Frames per second (always 0 for static images).

## Input Nodes

Input nodes produce information from a data source — for instance the active camera in a selected scene, a static image, a movie clip (image sequence or video), or a color or value. They generate the data passed to other nodes, so they have no input sockets, only outputs.

## Mask Node

The Mask node selects a Mask data-block, usable with other nodes (to Invert, Multiply, or Mix, or as a factor input). Inputs: Feather (use or ignore the feather points defined for splines; see Mask Feathers) and Size Source (where the mask gets its aspect/size — Scene Size, giving the scene render resolution and scaling with it; Fixed, a fixed pixel size; or Fixed/Scene, a pixel size that still scales with the render-resolution percentage). Motion Blur (for animated masks, built from surrounding frames): Samples (the motion-blur sample count, higher being smoother and more accurate but slower) and Shutter (the motion-blur duration in seconds, matching the per-frame exposure). Properties: Masks (the selectable mask data-block — if its label is blank, the mask name is used). Output: Mask (the black-and-white mask output). Example: the Mask node isolates an object from the background to keep it from being corrected.

## Render Layers Node

The Render Layers node renders a View Layer and pulls its Passes into the compositing graph. It has no input sockets. Properties: Scene (the scene to render a view layer for) and View Layer (the view layer to render, with the adjacent button re-rendering it immediately). A hint notes that to use another scene's compositing output rather than its raw render, first render that scene into multi-layered images (e.g. OpenEXR), then load them into the current scene's Compositor with the Image Node. Outputs: Image (the rendered image), Alpha (the alpha channel), and render-pass sockets (one per enabled pass) — and the viewport compositor only supports render passes with EEVEE, leaving them empty for other engines.

## Scene Time Node

The Scene Time node outputs the scene animation's current time in seconds or frames. It has no inputs. Outputs: Seconds (the current scene time in seconds) and Frames (the current scene frame — as a geometry-nodes input it may give non-round numbers to support higher-quality motion blur).

### Scene Time Node

The Scene Time node outputs the current animation playhead position in seconds or frames.

### Inputs

None.

### Outputs

Seconds
Playhead position in seconds.

Frames
Current frame number. May output non-integer values in geometry nodes to support higher-fidelity motion blur.

## Time Curve Node

The Time Curve node produces a factor (0.0 to 1.0) between the scene's start and end time via a curve mapping. Inputs: Start/End Frame (the time range whose values the output should span, becoming the graph's X axis — and reversible by setting a start frame greater than the end). Properties: Curve (the curve's Y value is the factor output; see the Curve widget) — and flipping the curve reverses the time input, which is easy to overlook. Output: Factor (the curve's Y value at the current frame). A hint notes the Map Range Node can remap the output, and since some curves can push the Time Curve above one or below zero, the Map Value node's Min/Max clamping can keep it safe.

The Time Curve node produces a factor value (0.0 to 1.0) between the scene's start and end time via a curve mapping.

Inputs:
Start/End Frame — the start and end frames of the time range whose values the output should span; this range becomes the graph's X axis. Set a start frame past the end frame to run the time input in reverse.

Properties:
Curve — the Y value the curve defines is the factor output; for the controls, see Curve widget. Tip: flipping the curve reverses the time input, but that's easy to miss in the node setup.

Outputs:
Factor — the curve's Y value at the current frame.
Hint: the Map Range Node can remap the output to a more fitting value. Some curves can make the Time Curve node output above one or below zero, so to be safe use the Map Value node's Min/Max clamping to bound the output.

Example — the time controls, left to right: none, slow down, freeze, speed up, reverse.

## Sequencer Strip Info Node

The Sequencer Strip Info node returns information about the Video Sequencer strip the Compositor modifier is applied to, including timing and transform data like frame range, position, rotation, and scale. Note it's only supported when the Compositor runs in the Video Sequencer's context (e.g. a Compositor modifier on a strip), outputting default values otherwise. It has no input sockets. Outputs: Start Frame and End Frame (the strip's start/end in the Sequencer timeline), Location (its 2D position offset, from its transform), Rotation (its rotation, from its transform settings), and Scale (its X/Y scale, from its transform settings).

## Channel Key Node

The Channel Key node separates background from foreground by the difference in a chosen channel's levels — for example, in the YUV color model it suits compositing stock explosion footage (very bright) shot against a solid dark background. Inputs: Image (standard color input); Minimum (the lowest values counted as foreground — meant to be relatively high, from this value to 1.0); and Maximum (the highest values counted as background — meant to be relatively low, from 0.0 to this value), where leaving a gap between Minimum and Maximum gives a transparency gradient between foreground and background. Also: Color Space (the color model the channels represent — RGB, HSV, YUV, YCbCr); Key Channel (which of that model's channels determines the matte); Limit Method (how the level difference is computed — Max, limiting by the maximum of the two channels other than the Key Channel, or Single, limiting by the maximum of a chosen Limit Channel); and Limit Channel (the channel used for the maximum, its options set by the Color Space). Outputs: Image (with its alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key).

## Chroma Key Node

The Chroma Key node decides whether a pixel is foreground or background (and so transparent) from its chroma values — use it, for example, to composite footage shot before a green or blue screen. Inputs: Image (standard color input); Key Color (the background color, usually picked with the color picker from the original image); Minimum (an angle on the color wheel for how tolerant the keying color is — larger angles allow more variation to count as background); Maximum (the level considered pure background — higher cutoffs make more pixels fully transparent if within the angle tolerance); and Falloff (raise it to make nearby pixels partly transparent for a smoother edge blend). Outputs: Image (alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key).

## Color Key Node

The Color Key node does chroma keying — removing parts of an image by color — commonly to drop green- or blue-screen backgrounds, making a matte where the selected colors turn transparent. Inputs: Image (standard color input); Key Color (the target color to key out, typically the background, e.g. pure green or blue); Hue (the tolerance for hue difference from the key color — wider keys out more similar hues); Saturation (the tolerance for saturation difference, helping avoid removing unintended desaturated areas like skin or clothing); and Value (the tolerance for brightness difference, useful when lighting or background luminance is uneven). Outputs: Image (alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key).

## Color Spill Node

The Color Spill node suppresses an unwanted color cast — usually green or blue — caused by light bouncing off a chroma-key screen onto the subject, a common compositing problem that gives an unnatural tint; the node reduces the chosen color channel's influence to restore a more natural look. Inputs: Image (the RGBA input to process); Factor (how strongly the node applies — 1.0 fully, lower values blending with the original); Spill Channel (which channel to reduce — R for red spill, G for green spill, common with green screens, or B for blue spill, common with blue screens); Limit Method (the reduction method — Simple, comparing the Limiting Channel to the others and reducing it where higher, or Average, using the average of the other two channels as the despill channel's limit); Limit Channel (Simple only — which channel(s) serve as the limiting reference: R, G, or B); and Limit Strength (the limit channel's strength). Spill Strength: when enabled, set the spill strength per color channel; when disabled, the spill channel uses a unit scale while the others are zero — with Strength setting each channel's spilling strength. Output: Image (the corrected image).

## Difference Key Node

The Difference Key node makes a matte that isolates foreground content by comparing it against a reference background image. Inputs: Image 1 (the foreground content over the background to remove); Image 2 (the reference background); Tolerance (where pixels match the reference within this threshold, the matte turns transparent); and Falloff (raise it to make nearby pixels partly transparent for a smoother edge blend). Outputs: Image (alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key).

## Distance Key Node

The Distance Key node sets a pixel's alpha from the 3D distance between its color and the key color in a 3D color space — working well for isolating a specific background color (not only green). Inputs: Image (standard color input); Key Color (the color to key); Color Space (RGB or YCC — and with YCbCr only the Cb and Cr channels count toward the foreground/background distance); Tolerance (the threshold for what counts as a match — how close a pixel must be to the background to be an absolute match); and Falloff (high values make pixels close to the Key Color more transparent than those farther but still keyed, while low values make any keyed pixel transparent regardless of closeness). Outputs: Image (alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key).

## Keying Nodes

The Keying nodes give the essential tools for making a Matte for images that lack their own alpha channel — a typical case being blue- or green-screen footage where live action is shot before a colored backdrop to be replaced by a matte painting or virtual background. In general, hook them to a viewer, set the Image Editor to the Viewer node, and adjust the sliders in real time on a sample frame to dial in the settings, where small tweaks can remove artifacts or foreground degradation (taking out too much green can leave actors flat or bluish/purplish). You can and should chain these nodes, refining masking and color correction in successive passes that each build on the previous output — the Keying Node comes closest to a do-it-all green-screen node, but the best results combine techniques. Note: a Garbage Matte isn't a node but a technique — a Mask identifying content to remove that automatic processes like chroma keying can't, used either to select specific content to drop or as the inverse of a rough subject selection (removing everything else); some nodes take a garbage matte directly, and for those that don't, you can subtract the garbage matte from the node's generated matte. Simple garbage mattes come from the Box Mask or Ellipse Mask, and more complex shapes from a Double Edge Mask or a Mask.

## Keying Node

The Keying node is a one-stop tool for green-/blue-screen removal: it does both chroma keying to drop the backdrop and despill to fix the backdrop's color cast, plus common operations to tweak the resulting matte. Inputs: Image (standard color input) and Key Color (the color to remove — a single color, or a reference image such as from the Keying Screen Node). Preprocess: Blur Size (cut color noise by blurring only color by this amount while leaving luminosity intact, affecting only matte calculation, not the result image). Key: Balance (the balance between color channels compared with the key color — 0.5 averages the other channels, red and blue for a green screen — tweakable alongside Clip Black and Clip White while watching the Matte output for optimal separation). Tweak: Black Level (the threshold for what becomes fully transparent, i.e. black in the matte — set it as low as possible, raising it for uneven backdrops, with the Keying Screen Node helping keep it low or a Garbage Matte excluding problem areas, and edges are exempt to preserve detail) and White Level (the threshold for what becomes fully opaque, i.e. white in the matte — set it as high as possible, lowering it and/or adjusting Screen Balance for near-green foreground colors, with a Core Matte fixing especially problematic parts rather than a low Clip White, again exempting edges). Edges: Size (the pixel radius used to detect an edge) and Tolerance (the threshold for whether pixels in the radius match the current one — above it, the point is an edge), with a tip that for edge problems it helps to adjust the edge kernel before feathering (detected edges ignore Clip Black/White to preserve fine detail, and you can check edge detection via a Viewer Node on the Edges output) — sharper edges (small Size like 2, larger Tolerance like 0.4) give a sharper matte but may lose stray hairs, while fat edges (larger Size like 8, smaller Tolerance like 0.05) capture more detail but can halo the subject (adjustable with Feather plus Dilate/Erode). Mask: Garbage Matte (an optional mask of areas to always exclude, removed from the generated matte) and Core Matte (an optional mask of areas to always include, merged with the generated matte). Postprocess: Blur Size (soften the matte for smoother transitions and noise reduction), Dilate Size (enlarge with positive numbers or shrink with negative by that many pixels, like the Dilate/Erode Node on the matte), Feather Size (feather the matte inward with negative or outward with positive numbers), and Feather Falloff (the feathering falloff rate at the edges). Despill: Strength (how much key-color bleed is removed — 0 none, 1 all possible, using the same implementation as the Color Spill Node's Unspill amount) and Balance (how the color channels are compared when computing spill, affecting the corrected hue/shade, like the Color Spill Node's Limiting Channel). Outputs: Image (the processed image with the matte applied to its alpha), Matte (the matte, for checking the key's quality or applying manually via Set Alpha or Mix), and Edges (the detected edges, for tuning Edge Size and Tolerance).

## Keying Screen Node

The Keying Screen node makes plates to serve as a color reference for keying nodes, generating gradients from colors sampled at motion-tracking points on movie clips — useful for handling a green screen's uneven colors. Inputs: Smoothness (the keying screen's smoothness). Properties: Movie Clip (the clip used as the source for the gradient colors) and Tracking Object (the tracking object generating the gradient — you'll likely make a new tracking object in the Object panel, since tracks used for gradients can't double as camera/object tracking; place these tracks where gradient colors should be sampled, track or move them by hand so the gradients update through the movie, and they may carry an offset for easier tracking of featureless screens). Output: Screen (the gradient image). Example: in a green-screen setup using a Color Key, lighting is often uneven across the backdrop, giving a bad matte; widening the Color Key tolerances accepts more green to mask but may wrongly mask foreground, so instead the Keying Screen node lets you vary which shade is used per area. Start in the Movie Clip Editor (open the Sidebar and Toolbar for tracking config), create a new object track in the Objects selector (gradient tracks don't solve cameras well), place markers to sample different backdrop parts (trackable or hand-moved so gradients update over time, and a marker disabled on a frame isn't used), then add the node, select that tracking object, and feed its generated gradient plate into the Keying node's Color input for a better matte.

## Luminance Key Node

The Luminance Key node separates background from foreground by the difference in luminance (brightness) — stock footage of explosions, smoke, or debris is usually shot against a solid dark background rather than a green screen, and this node can split the foreground effect from it; it also suits sky replacement for overexposed or gray skies unfit for chroma keying. Tip: for footage of something that emits light over a dark background, like fire, a Mix Node using Screen or Add gives better results. Inputs: Image (standard color input); Minimum (the lowest values counted as foreground — meant to be relatively light, from this value to 1.0); and Maximum (the highest values counted as background — meant to be relatively dark, from 0.0 to this value), with brightness between the two forming a transparency gradient. Outputs: Image (alpha adjusted for the keyed selection) and Matte (a black-and-white alpha mask of the key). Example: a model shot against a white background gives a matte with a white background and a black model — the opposite of what's wanted — so a Color Ramp node reverses it (left color White Alpha 1.0, right Black Alpha 0.0), turning the reversed mask's white outline into a usable alpha mask; then, rather than an Alpha Over node, you can use the matte directly as the Factor input, feeding the background to the bottom socket and the original photo to the top (since the Mix node uses the top socket at factor 0.0 and the bottom at 1.0), so the model appears where the Luminance Key output black.

## Layout Nodes

The Layout Nodes help you control the layout and connectivity of nodes within the Compositor.

## Box Mask Node

The Box Mask node makes an image suitable for a simple matte. Inputs: Mask Type, the operation against the input mask — Add (the union: the generated mask's area is set to the given Value, while the rest of the input mask passes through unchanged, or black if there's no input mask), Subtract (the given Value is taken away from the input mask's values), Multiply (the intersection: the input mask is multiplied by Value within the generated area, and everything else becomes black), or Not (areas in both masks become black; generated-mask areas that are black on the input become Value; areas the generated mask doesn't cover stay unchanged); Mask (an optional base mask for the operations); Value (the generated mask's intensity); Position (the box center as a fraction of width or height — 0.5, 0.5 centers it, 0.0, 0.0 puts it lower-left); Size (the box's width/height as a fraction of the total image width); and Rotation (the box's rotation about its center). Output: Mask (a rectangular mask merged with the input mask, at the current scene render dimensions). Tip: for soft edges, pass the output through a slight Blur node.

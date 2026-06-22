# Defocus Node, Directional Blur Node, Vector Blur Node, Convolve Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Defocus Node; Directional Blur Node; Vector Blur Node; Convolve Node; Denoise Node; Despeckle Node; Dilate/Erode Node; Filter Node; Glare Node; Filter Nodes; Inpaint Node; Mask To SDF Node; Group; Bokeh Image Node; Boolean Node; Integer Node; Normal Node; Color Node.

## Defocus Node

The Defocus node blurs areas of an image from a Z depth map or mask input, typically emulating depth of field (DOF) as a post-process with a Z-buffer input, though it can also blur non-Z-based images. Inputs: Image (standard color input) and Z (a Z-buffer input, or a grayscale image used as a mask, or a single value). Properties: Bokeh Type (the number of iris blades of the virtual camera's diaphragm — Disk for a perfect circle, Triangle for 3 blades, Square for 4, Pentagon for 5, Hexagon for 6, Heptagon for 7, or Octagon for 8); Angle (deactivated for Disk — a rotation offset for the bokeh shape, in degrees); F-Stop (controls focal blur like a real camera's aperture f without changing luminosity — the default 128 is treated as infinity, everything in focus, and halving the value doubles the blur; deactivated when No Z-buffer is on); Max Blur (cap the blur by a maximum radius to optimize performance, 0 meaning no limit); Scene (select the linked scene); No Z-buffer (enable for a non-Z-buffer Z input — auto-enabled whenever a non-image-based node connects to Z); and Z Scale (active only with No Z-buffer — the input directly controls the blur radius, like F-Stop with the Z-buffer, and this scales the Z input's range). Output: Image (standard color output). Examples: in the blend-file example the ball-array image is blurred as if shot at an f-stop of 2.8, giving a fairly narrow depth of field centered 7.5 units from the camera, with farther balls blurrier. No-Z-Buffer examples: for more control (blur only one object, or the whole image uniformly), use something other than a real Z-buffer in Z — an Image node with a grayscale image where white is maximum blur and black none, or a Time node to blur uniformly over time, or a fake depth-shaded image (made via a linear blend texture on all objects, or a fog/mist fake-depth method) for a possibly better DoF blur that can also carry anti-aliasing (impossible with a real Z-buffer) — with No Z-buffer becoming the main blur control and the input needing scaling since a texture's value is usually only 0.0 to 1.0. Camera settings: the Defocus node uses the actual scene camera data when supplied by a Render Layer node — set the focal plane via the camera's Distance parameter (shorthand for Depth of Field Distance), found in the main Camera panel below Depth of Field, and enable the camera Limits option to see the focal point as a yellow cross along the camera's view direction. Hints: for minimum artifacts, avoid very large distance differences between objects that may visibly overlap; remember this is a post-process, not real DoF, so a "focus pull" (where a nearby object all but disappears as focus shifts to a distant one) can't be done in a single pass — instead split the scene into "nearby" and "far" objects, render them in two passes, and combine each with its own Defocus node driven by the same Time node but with one inverted (e.g. a Map Value node with Size -1), so as one's defocus rises the other's falls. At very low f-stop values (under 5) the node removes oversampling and brings objects at DoF Distance sharply into focus, which against a contrasting background can cause aliasing (stair-stepping) — if so:

To counter that aliasing: do your own OSA by rendering at twice the intended size then scaling down so adjacent pixels blur together; use the Blur node at a setting of 2 for X and Y; set DoF Distance off by a little so the in-focus object blurs by the tiniest bit; use a higher f-stop to start the blur and then route the Z socket through a Map Value into a Blur node to enhance it; or rearrange the scene for a lower-contrast background. No Z-Buffer warning: since there's no way to detect whether a real Z-buffer is connected, be careful with the No Z-buffer switch — if the Z scale is large and you forget to lower it, the values may be read as huge blur radii and cause processing times to explode.

## Directional Blur Node

The Directional Blur node blurs an image along a chosen direction, usable to fake motion blur. Inputs: Image (standard color input); Samples (the sample count — more samples are smoother but slower, the actual number being two to the power of this input, so it grows exponentially); Center (the pivot for the transformations, in normalized coordinates where 0 is the lower-left and 1 the upper-right); Rotation (how much rotation the blur spans); and Scale (how much scaling the blur spans). Translation: Amount (how much translation the blur spans in the given direction relative to the image size, with negative values going the opposite way) and Direction (the angle setting the translation direction). Output: Image (standard color output).

## Vector Blur Node

The Vector Blur node is a fast way to fake Motion Blur in compositing, using the vector speed render pass to blur the image pixels in 2D. Inputs: Image (linked to the "Combined" render pass); Speed (the "Vector" render pass; see Cycles render passes); Z (Z depth, linked to the "Depth" pass); Samples (a quality factor); and Shutter (the motion-blur duration in seconds, matching the per-frame exposure time). Output: Image (the motion-blurred result). Usage: even a correct Image/Z/Speed setup can still show artifacts, since the 2D passes lack 3D information so what's behind a moving object or off-camera is lost — better results come from rendering into multiple render layers, applying vector blur to each, then compositing them (typically an animated character on a separate layer from the background, especially with hair or transparency); for other artifacts, slightly blurring the Speed pass or setting a Maximum Speed limit can help smooth the motion, though too much blurring brings its own problems.

## Convolve Node

The Convolve node performs a 2D convolution on an image using a custom Image Kernel, enabling effects like blurring, sharpening, and edge detection depending on the kernel values — it multiplies a neighborhood of pixels around each pixel by the kernel values and sums them for the output color, a common image-processing way to emphasize or suppress spatial features. Inputs: Image (the image to process); Kernel (the convolution kernel, given as a constant value or an input image whose pixel values define the weights); and Normalize Kernel (a factor deciding whether to auto-normalize the kernel — divide by its total sum — to keep brightness consistent). Properties: Kernel Data Type — Float (a numeric kernel from the Kernel input socket) or Image (a full image as the kernel for more complex patterns). Output: Image (the convolved result). Usage covers blurring (an evenly weighted positive kernel), sharpening (a high central value with negative surroundings), and edge detection (Sobel or Laplacian kernels) — and when designing custom kernels, balance the size and values to avoid over-brightening or darkening, with Normalize Kernel often recommended.

## Denoise Node

The Denoise node denoises renders from Cycles and other ray tracers, cutting render time by allowing fewer samples; it uses Open Image Denoise, which turns noisy images into clean ones with machine learning. Inputs: Image (the noisy input); Albedo (an optional albedo pass to better preserve detail — for Cycles, use the Denoising Albedo pass available with the Denoising Data passes); Normal (an optional normal pass, likewise the Denoising Normal pass); HDR (preserve colors outside the 0 to 1 range); Prefilter — None (no prefiltering, retaining the most detail and fastest but assuming noise-free inputs, which may need a high sample count, else noise remains), Fast (assumes noisy inputs but doesn't prefilter — faster than Accurate but blurrier), or Accurate (prefilter the inputs before denoising for more detail at more processing time); and Quality — Follow Scene (use the scene's setting), High (highest quality, long processing), Balanced (about half the time of High while keeping most quality), or Fast (quick output at a noticeable quality cost). Output: Image (the denoised result).

## Despeckle Node

The Despeckle node smooths noticeably noisy areas of an image while leaving complex areas alone, working by computing each pixel's standard deviation with its neighbors to gauge whether an area is high- or low-complexity, then smoothing it with a simple mean filter if the complexity is below the threshold. Inputs: Image (standard color input); Factor (how much the filter affects the image); Color Threshold (the threshold separating high and low complexity); and Neighbor Threshold (the threshold for how many pixels must match). Output: Image (standard color output).

## Dilate/Erode Node

The Dilate/Erode node grows or shrinks a mask with a morphological operator. Inputs: Mask (a grayscale image); Size (the surrounding area examined per pixel — i.e. how much to dilate, for positive values, or erode, for negative); and Type — Steps (set each pixel to the maximum, for dilation, or minimum, for erosion, found in a surrounding square, keeping the original gray levels and best for masks with sharp corners, while rounded shapes look more square — and despite the name it runs once regardless of Size), Threshold (force pixels fully black or white by whether they're darker or brighter than 50% gray, then take the max/min within a surrounding circle, losing gray levels and suiting rounded corners while rounding off sharp ones), Distance (take the max/min within a surrounding circle while preserving gray levels, suiting rounded corners), or Feather (blur the image); plus Falloff Size (Threshold — how much to blur the edges after dilation/erosion) and Falloff (Feather — the brightness curve of the blurred edges). Output: Mask (the resulting mask).

## Filter Node

The Filter node implements several common image-enhancement filters. Inputs: Image (standard color input); Factor (how much the node influences the output); and Type — where Soften, Laplace, Sobel, Prewitt, and Kirsch all detect edges (in slightly different ways) via vector calculus and set theory: Soften (slightly blur), Box Sharpen (raise contrast, especially at edges), Diamond Sharpen (less aggressive than Box, reducing artifacts), Laplace (edge highlighting, prone to highlighting noise), Sobel (a negative image highlighting edges), Prewitt (similar to Sobel), Kirsch (better blending than Sobel or Prewitt near an edge), and Shadow (a relief/emboss effect, darkening outside edges). Output: Image (standard color output).

## Glare Node

The Glare node enhances bright areas with effects like lens flares, bloom, and fog glow, simulating how light interacts with lenses for realistic or artistic highlights and reflections. Inputs: Image (standard color input); Glare Type — Bloom (a soft glow around bright areas from light scattering in eyes and lenses), Ghosts (overlapping glare artifacts resembling lens reflections or a hazy glow), Streaks (bright streaks radiating from highlights, for lens flares), Fog Glow (a more physically accurate Bloom giving a softer, more realistic glow at more compute cost), Simple Star (a simpler star-shaped version of Streaks), Sun Beams (scattering of bright light through a medium — crepuscular rays — cheaper than full volumetric lighting), or Kernel (a custom convolution filter using a numeric or image kernel for user-defined glare or diffusion); and Quality — High (full resolution, best quality), Medium (lower resolution, less time), or Low (fastest, least detail). Highlights: Threshold (the minimum luminance to contribute to glare — lower includes more areas, higher restricts it to the brightest) and Smoothness (how gradually pixels enter the glare, higher being smoother). Clamp: clamp bright highlights to the Maximum input for a more consistent bloom across large luminance variation, where Maximum sets the clamp value. Adjust: Strength (overall glare intensity — above 1 boosts the glare's luminance, below 1 blends it with the original), Saturation (the glare's color saturation), and Tint (a color tint for the glare). Glare: Size (Bloom/Fog Glow/Sun Beams — the effect's relative spread, 1 covering the full image, 0.5 half), Streaks (Streaks — the number of streaks from highlights), Streaks Angle (Streaks — the first streak's angle to the horizontal), Iterations (Ghosts/Streaks/Simple Star — the number of ghosts, or the quality and spread of streaks/simple-star glare), Color Modulation (Ghosts/Streaks — subtle color variation simulating chromatic dispersion), Fade (Streaks/Simple Star — the streaks' fade-out), Diagonal (Simple Star — rotate the streaks 45° for an alternate pattern), Sun Position (Sun Beams — the rays' source point as a factor of image dimensions), Jitter (Sun Beams — jitter while computing rays, higher being faster but grainier), Kernel Data Type (Kernel — Float for a numeric kernel from the socket, or Color for a full color image), and Kernel (Kernel — the numeric values for Float, or a connected image for Color). Outputs: Image (the final image with glare added), Glare (the isolated glare effect, for further compositing), and Highlights (the extracted bright areas used to make the glare). Gizmos: the node offers an interactive Node-Editor gizmo (enable Active Node Gizmo and select the Glare node), and for Sun Beams a cross-shaped gizmo appears in the image preview to set Sun Position. Examples — Sun Beams: first define the area casting rays (real-world diffuse reflected light doesn't contribute, so exclude it) via a separate light-source image, brightness/contrast tweaking to keep only the brightest areas, muting shadow and midtone colors, or masking for full control; then overlay the generated beams on the original, usually with a simple "Add" Mix node (physically correct, since scattered light adds to the result).

## Filter Nodes

The Filter Nodes process an image's pixels to bring out extra detail or apply some post-processing effect.

## Inpaint Node

The Inpaint node extends an image's borders into transparent or masked regions, useful for problems like "wire removal" and holes left by chroma keying. Inputs: Image (standard color input) and Size (how many times to extend the image). Output: Image (standard color output). Examples: after chroma keying removes a "wire," you're left with a blank space (shown as a black line, but alpha in your output), and inpainting fills a few pixels from the surrounding image to remove the wire — but the wider the hole, the more noticeable the effect, so using more than a few pixels of infill is about as irritating as the wire; it can also cover other minor sins like motion-capture control points, so use it sparingly.

## Mask To SDF Node

The Mask To SDF node builds a signed distance field (SDF) from a mask, storing for each pixel the distance to the nearest mask boundary, with the sign showing whether the pixel is inside or outside the masked region — useful for soft edges, outlines, glows, erosion/dilation, or procedural distance-based compositing. Input: Mask (the mask generating the field, where inside pixels are interior and outside ones exterior). Outputs: SDF (the signed distance to the nearest boundary pixel in pixels, negative inside the mask and positive outside) and Nearest Pixel (the integer coordinates of the nearest boundary pixel, for advanced effects needing the closest edge position).

## Group

A Group node bundles a set of nodes into one, selectively exposing their inputs and outputs — simplifying a node tree by hiding complexity and reusing functionality. Group Input: exposes the group's inputs, and you can have several in a tree to keep it clean by bringing each input in where it's needed (rather than dragging long links), with the input slots editable in the Sidebar's Group tab. Group Output: receives the group's outputs, likewise allowing several to output each result where it's produced, with the output slots editable in the Group tab. Node Groups: this section lists every node group — those in the current blend-file plus any Linked or Appended from another.

A Group Node folds a set of nodes into one and selectively exposes those nodes' inputs and outputs. Group nodes tidy a node tree by tucking complexity away and letting you reuse functionality.

Group Input — exposes the node group's inputs. You can place several in one tree to keep it tidy, pulling each input in right where it's needed instead of dragging long links across the graph. The input slots are edited in the Sidebar's Group tab.

Group Output — receives the node group's outputs. You can place several in one tree to keep it tidy, emitting each result right where it's produced instead of dragging long links across the graph. The output slots are edited in the Sidebar's Group tab.

Node Groups — this section lists every node group: those in the current blend-file plus any Linked or Appended in from elsewhere.

### Group

Combines multiple nodes into a reusable unit, exposing selected inputs and outputs.

Simplifies trees and enables reuse.

**Group Input**
Exposes group inputs; multiple instances clean up complex layouts by placing inputs near their use sites instead of long cross-graph connections.

Edit in Group tab of Sidebar.

**Group Output**
Receives group outputs; multiple instances keep results near their production points.

Edit in Group tab of Sidebar.

**Node Groups**
Lists all groups (current file, linked, or appended).

### Group 

A Group Node packages nodes into a single reusable unit, selectively exposing contained input and output sockets.

Groups streamline node networks by encapsulating complexity and promoting reusability.

### Group Input 

Presents the node group's input sockets. Multiple instances can exist to keep the tree organized, routing each input directly to the point of use rather than stretching links globally.

Input slots are managed in the Group tab of the Sidebar.

### Group Output 

Collects node group outputs. Multiple nodes can exist, allowing each result to be positioned near its source rather than creating distant links.

Output slots are managed in the Group tab of the Sidebar.

### Node Groups 

This section catalogs all node groups: those contained in the current .blend file and those linked or imported from external .blend files.

## Bokeh Image Node

The Bokeh Image node makes a special input image for the Bokeh Blur filter node — a reference image simulating optical parameters like aperture shape and lens distortions that strongly affect real-camera bokeh. Inputs (the first three simulate the camera aperture): Flaps (an integer number of iris-diaphragm blades), Angle (an angular offset for those blades relative to the image plane), Roundness (the blade curvature from 0, straight, to 1, a perfect circle), Catadioptric Size (a mirror-lens/telescope distortion useful for visually complex bokeh), and Color Shift (chromatic aberration in the blur, as from a tilt-shift lens). Output: Image (the generated bokeh image).

## Boolean Node

The Boolean node supplies a Boolean value. It has no input sockets. Properties: a single Boolean value (true/false). Output: Boolean (standard Boolean output).

### Boolean Node

The Boolean node supplies a Boolean value.

### Inputs

This node has no input sockets.

### Properties

A single Boolean value (true/false).

### Outputs

Boolean
Standard Boolean output.

## Integer Node

The Integer node supplies an integer value. It has no input sockets. Properties: a single integer value. Output: Integer (standard integer output).

### Integer Node

The Integer node supplies an integer value.

### Inputs

This node has no input sockets.

### Properties

A single integer value.

### Outputs

Integer
Standard integer output

## Normal Node

The Normal node generates a normal vector. Input: Normal (a normal vector input). Properties: Normal Direction (set a fixed normal direction by LMB-click-dragging on the sphere, holding Ctrl to snap to 45° increments). Output: Normal (a normal vector output).

### Normal Node

Outputs a unit vector indicating normal direction per evaluated point. Output varies by domain:
- Face: Surface "up" direction.
- Mesh Vertices: Average of connected face normals; or normalized position if isolated.
- Edge: Average of the two vertex normals.
- Face Corner: Same as face normal.
- Curve Control Points: Evaluated curve normal, perpendicular to curve path.

Caution: For NURBS and Bézier curves, output is at control points, not evaluated points; may differ visually. Use Resample Curve Node to create poly spline with points at every evaluated location.

**Inputs**
None.

**Outputs**
- Normal: Direction vector.
- True Normal: Mesh normals without custom attribute override.

### Normal Node

This node produces a normal vector and its dot product.

### Inputs

Normal
Normal vector input.

### Properties

Normal Direction
Manually specify a fixed normal direction. Use LMB click-drag on the sphere to set direction. Hold Ctrl while dragging to snap to 45 degree increments.

### Outputs

Normal
Normal vector output.

Dot
Dot product as a scalar.

- Matching normal directions yield a dot product of 1.

- Perpendicular normals yield zero (0).

- Opposite normals yield -1.

## Color Node

The Color node outputs the color chosen with the color-picker widget. Tip: dragging a color from a color-picker button into the node editor creates a Color node, preserving alpha (or using 1.0 if the source has none). It has no input sockets. Properties: the color-picker widget. Output: Color (the chosen color as a single constant value).

### Color Node

The Color node puts out the color value set with the color-picker widget.

Tip

Drag a color off a color-picker button into a node editor and a Color node appears. Any alpha is kept; where the source has none, 1.0 stands in.

### Inputs

No inputs on this node.

### Outputs

Color
The color value marked by the color-picker widget.

### Example

Color converted into a vector by reading RGB as XYZ values.

### Color Node

Output a constant color value via the color picker widget.

Tip: Dragging colors from color picker buttons into the node editor creates a Color node. Alpha values are preserved; missing alpha defaults to 1.0.

### Inputs

None.

### Properties

Uses the color picker widget.

### Outputs

- **Color** — The chosen color as a constant.

## Value Node

The Value node feeds numerical values into other nodes in the tree. It has no input sockets. Properties: a single floating-point value. Output: Value (the value set in the properties). Example: it can control multiple values at once, making it a handy organizational tool — and a tip notes you can make values proportional to each other by inserting a Math Node between the links.

### Value Node

The Value Node is a simple way to feed numerical values into other nodes across the tree.

### Inputs

This node has no input sockets.

### Properties

One numerical value, floating-point.

### Outputs

Value
Whatever value the node properties hold.

### Example

Below, the Value Node steers several values together — a handy bit of organization.

Example of the Value node.

Tip

You can also tie values into fixed proportions of one another by slotting a Math Node between the links.

### Value Node

Input numerical values to other nodes in the tree.

### Inputs

None.

### Properties

Single floating-point numerical value.

### Outputs

- **Value** — The value set in node properties.

### Example

Use Value Node to control multiple inputs simultaneously, making it a useful organizational tool. Add Math Nodes between Value outputs to make values proportional.

Tip: Combine with Math nodes to adjust relationships between values.

## Vector Node

The Vector input node creates a single vector. It has no inputs. Properties: X, Y, Z. Output: Vector (standard vector output).

### Vector Node

A single vector comes out of the Vector input node.

### Inputs

No inputs on this node.

### Properties

- X

- Y

- Z

### Output

Vector
Standard vector output.

## Group Input Node

The Group Input node gives access to a node group's input sockets, serving as the entry point for data passed into the group from outside — images, values, or other types. Add or remove its input sockets through the Sidebar's Group panel or the Node Editor header's group-interface editor, and when the group is used in another compositor tree, the sockets defined here appear as inputs on the Group node itself. It has no inputs. Properties: see Group Sockets. Outputs: Image (the default image input available when the group is created, for feeding in images or render layers) plus any additional inputs defined in the group's interface, appearing here as output sockets.

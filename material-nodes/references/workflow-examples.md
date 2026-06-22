# Workflow Examples, Compositing Workspace, Compositor System, Image Kernels ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Workflow & Examples; Compositing Workspace; Compositor System; Image Kernels; Limitations.

## Workflow & Examples

Workflow and examples. Simple drivers can be set up from the pop-over shown when adding one, while adding several or doing advanced setups is easier with the Drivers Editor open. Transform Driver — control a property with an object's transform (here Object 1's X position drives Object 2's Y rotation): add a Driver to the second object's Rotation Y (context menu or Ctrl-D); open the Drivers Editor and select the Y Euler Rotation property in the channels region; open the Sidebar and select the Drivers tab; configure the driver as the Averaged Value of a Transform Channel of the first object; then move the first object and watch the second's Y rotation change. Scripted Expression — Orbit a Point: orbit an object around a point with a custom expression so its position changes while scrubbing — using trigonometry, 2D circular motion comes from sine and cosine (see Unit Circle), with the current frame as the variable (frame is a Simple Expression equal to bpy.context.scene.frame_current): add a driver to X Location, set Driver Type to Scripted Expression, and add the expression `0 + (sin(frame / 8) * 4)`, where frame/8 is the current frame divided by 8 to slow the orbit, (sin( )*4) multiplies by 4 for a bigger circle, and 0 + offsets the orbit center; add a driver to Y Location with `0 + (cos(frame / 8) * 4)`; then scrub to see it, experimenting to change size and center. Custom Function — Square Value: make a custom function for a value squared and add it to the Driver Namespace so driver expressions can use it (the namespace holds built-in functions plus constants like π and e, inspectable via the Python Console, e.g. `bpy.app.driver_namespace[...]`). To add one, implement it and register it — add this to the Text Editor and press Run Script:
```text
import bpy

def square(val):
    """Returns the square of the given value"""
    return val * val

# Add function to driver_namespace.
bpy.app.driver_namespace['square'] = square
```
then add a driver with a Scripted Expression such as `square(frame)` and scrub to observe it (more examples live in Templates ‣ Python ‣ Driver Functions; since Simple Expressions can't reach custom functions, these only make sense for complex computations, and replacing built-in namespace entries gives undefined behavior). View Layer Attribute Lookup: the material Attribute Node in View Layer mode auto-searches several locations (so a custom attribute can be set at Scene or World level and overridden per View Layer); drivers' Context Properties don't do this, so emulate it manually with fallback values and a conditional expression — for an attribute "attr" the node tries six RNA-path lookups in order: ["attr"] in the active View Layer (custom property), attr in the active View Layer (built-in), ["attr"] in the active Scene, attr in the active Scene, world["attr"] in the active Scene, and world.attr in the active Scene; checking a subset may suffice, driver variables for non-final links should use fallbacks invalid for the attribute (e.g. negative colors) that the conditional then checks, and the final variable should fall back to a valid default for when the property is unset. Shape Key Drivers — Improved Mesh Deformation: fix intersection problems from armatures and weight painting (especially at joints) and refine a rig (e.g. suggesting muscle) using a shape key, here improving a rudimentary arm's elbow. Setup: add a mesh (a cylinder with loop cuts), an armature with a bone chain, and skin the mesh via weight painting (to parent: select the mesh, then the armature, and Ctrl-P with auto weights); pose the armature and watch the joint deformation, then associate a Shape Key with a pose to fix intersections or bad angles. Shape Key: pose the armature so the problems show (covering the extreme poses you want to support), then with the mesh selected add a new Shape Key beside the Basis (Properties ‣ Mesh tab ‣ Shape Keys).

Continuing the shape-key driver: to build the shape key over the armature deformation, switch on both Edit Mode Display and Cage Editing on the Armature modifier (Properties ‣ Modifiers tab ‣ Armature Modifier ‣ Header); enter Edit Mode, select the new shape key in the properties panel, and adjust the vertices (pick the Basis key to switch back and forth between the original mesh and your edits, being careful to edit only your shape, not the original or other keys). Once the deformation looks right for the problem pose, configure a driver to activate the shape smoothly when entering it. Driver: add a driver to the new shape key's Value, then open the Drivers Editor and select it. Method 1 – direct mapping to a bone rotation value: map a bone rotation channel directly to the shape key's activation Value — simple, but relying on one rotation channel may not precisely capture when the shape should activate. In the Drivers tab, select the Averaged Value of the bone's rotation; identify the axis you care about (enable axes display or watch the bone's transform values), select that rotation channel and set it to local (the bone's rotation relative to its parent); then set points in the driver curve by dragging a handle or entering values in the F-Curve tab, where Y is the shape key Value (going 0.0 to 1.0) and X here is the rotation value in radians (you can use more than two points and tweak transitions with the handles, G to move); to verify, deselect "only show drivers for selected objects" so you can pose the armature and watch the driver. Method 2 – rotational difference to a target bone: needs an extra target/corrective bone but better captures the bone's 3D spatial condition. In armature Edit Mode, extrude a new bone from Bone 1 at the position where Bone 2 should have the shape active (such bones usually follow a "TAR-" or "COR-" naming convention); in the Drivers tab, choose the Averaged Value of the rotational difference between the rotated bone and the target bone (a rotational difference is the minimum World-Space angle between two objects, so the bones must share a root, making that angle depend only on the rotation of one — when the deform bone reaches the target rotation the difference is 0°); adjust the driver curve handles so the shape key Value (Y) is 1.0 when the rotational difference (X) is 0°, and 0.0 when the arm is extended at roughly 90° or more (in radians); then, as in Method 1, adjust the handles and pose the armature to confirm the ranges. Chained Relative Shape Keys: activate shape keys in succession — here moving one bone activates Key 1 then Key 2 (relative shape keys mix additively). Shape Keys: add two shape keys to a mesh besides the Basis. Drivers: add an armature with one bone to control them, activating the keys in succession as the bone rises — when it's halfway up both have some influence, and whether Key 1 maxes out before Key 2 starts (or how much they overlap) is preference; this example shows a seamless overlapping blend where Key 1 rises linearly from 0.0 at the bottom to 1.0 just past the midpoint and Key 2 stays 0.0 until the midpoint then rises at the same rate to 1.0 at maximum height. Add a driver to each key's Value, configuring both as the Averaged Value of a variable holding the bone's Z location; find the bone's World-Z motion range by raising it to align with the mesh top when both keys are active (here [0.0, 2.5]); then configure the driver functions so each key's Value (Y) suits the bone's height (X) — they should be linear, so define them analytically as y = a + bx (a being a Y offset, b the slope); add an Extended Polynomial Generator modifier to both drivers (Modifiers tab); and tune a and b so the curves run [0.0, 1.0] on Y over [0.0, 2.5] on X, overlapping in the middle with the same slope b.

Possible values are Key 1: y = 0.0 + 0.6x and Key 2: y = −0.5 + 0.6x. The functions go outside the [0.0, 1.0] range for the keys' Value, but that doesn't matter because Value is clamped by a Range in the Shape Keys panel.

## Compositing Workspace

The default Compositing workspace gives an efficient layout for building and previewing compositing node setups, arranging common editors so node editing, visual feedback, and animation control are all available at once. Image Editor: a large editor at the top, usually showing a Viewer node's output for immediate feedback as nodes are edited; it can switch to other image sources but defaults to previewing the compositor output (see Image Editor). Properties Editor: to the right of the Image Editor, giving access to settings that affect compositing such as render settings, color management, and output, with relevant panels including Color Management and Output Properties (see Properties Editor). Compositor: below the Image Editor, where node trees are built and edited (see Compositor) — it includes an Asset Shelf for quickly dragging in compositing node-group assets to reuse common effects, utilities, and production-ready groups. Timeline: at the bottom, for scrubbing frames, controlling playback, and animating values that affect compositing — especially useful for image sequences or video, or animating node parameters (see Timeline). Together these editors form a workflow-focused layout supporting interactive compositing, asset reuse, and time-based effects.

## Compositor System

Compositor system — Data. Dimensionality: compositing nodes act on data that's either an image or a single dimensionless value — for example the Levels node outputs a single value while the Render Layers node outputs an image. An input expecting a single value ignores an image and assumes a default (e.g. the Transform node uses defaults of zero for X, Y, and Angle and one for Scale, which are identity values with no effect), while an input expecting an image given a single value treats that value as covering the whole compositing space (e.g. the Filter node expects an image Factor, but a single value applies the same to all pixels). Type: three data types exist, all stored in half precision — Float (a signed floating-point number, with integer data also stored as float since no integer type exists), Vector (a 4D vector interpreted variously by node — as 2D with the last two components ignored for the Displace node's Vector input, as 3D with the last ignored for the Separate XYZ node, or as two consecutive 2D vectors, e.g. the Velocity Pass for the Vector Blur node packs 2D Previous Velocity in X/Y and 2D Next Velocity in Z/W), and Color (a 4D vector of Red, Green, Blue, Alpha, free-form and not tied to a specific color space or alpha model, with nodes providing settings to control representation and conversion). Implicit conversion: when an input gets a type other than its own, these conversions apply — Float→Vector: f ⇒ Vector(f, f, f, 0); Float→Color: f ⇒ Color(f, f, f, 1); Vector→Float: (x, y, z, w) ⇒ Average(x, y, z); Vector→Color: (x, y, z, w) ⇒ Color(x, y, z, 1); Color→Float: (r, g, b, a) ⇒ Luminance(r, g, b); and Color→Vector: (r, g, b, a) ⇒ Vector(r, g, b, 0) — the example showing color-to-float conversion since the Math node expects float inputs. Compositing space — Image Domain: the compositor allows an infinite compositing space, so images carry not just a size but a transformation in that space (like 3D objects), where an identity transformation centers the image; the rectangular area an image occupies, set by its transformation and size, is its Domain (the figure shows two images, one centered and one scaled down and translated into the upper-right quadrant, with similar pixel sizes but different apparent sizes), and images can be transformed with nodes like Transform, Translate, and Rotate. Operation Domain: a node operates on a specific rectangular area of the space called the Operation Domain, considering only the parts of input images that overlap it and ignoring the rest; where an input doesn't fully overlap, the remainder is assumed zero (a zero value, zero vector, or transparent zero color by type) — illustrated by a node whose operation domain (blue) is larger than an input's domain (red), with the uncovered area assumed zero, a real-world case being Alpha Over overlaying a small logo where the rest is a transparent zero color.

A real-world example uses Alpha Over to lay a small logo over an image: the logo covers only part of the operation domain (the whole viewport here), so the rest is assumed a transparent zero color. Interpolation: when an input image isn't perfectly aligned with the node's operation domain or differs in pixel size, the node interpolates — reading the input at the operation domain's exact pixel positions via Nearest-Neighbor, Bilinear, or Bicubic interpolation (transformation nodes like Transform and Rotate include an interpolation option for how their output is read). Determining the operation domain: mechanisms vary by node type, falling into three classes. Input nodes (like the Image node) have an operation domain with an identity transformation and the same size as their output. Output nodes (like the Viewer node) have an operation domain with an identity transformation, sized to match the final compositor output — the viewport size for viewport compositing, the scene render size for final render compositing. Other nodes (unless their docs say otherwise) designate one input as the Domain Input, and the node's operation domain matches that input's domain; for many nodes this is intuitively the main input (e.g. the Filter node's Image input), but each input has a Domain Priority, and the operation domain is the domain of the non-single-value input with the highest priority. So the Filter node's Image input outranks its Factor input, giving four cases: both connected to images (Image is the domain input, having higher priority and an image); only Image connected (Image is, being the only one with an image regardless of priority); only Factor connected (Factor is, for the same reason); and neither connected (no domain input, since the node runs on single values). Considerations: this mechanism has some possibly undesirable consequences. Clipping: a node's output is clipped to the operation domain (the domain input's domain) — so in Alpha Over, if the Foreground is bigger than the Background, the output clips to the Background since that's the domain input; Alpha Over can't currently change input domain priority, so as a workaround use a Mix node (whose first Image input has the highest domain priority). Output: the compositor supports a single active output target, so only one of the node tree's Group Output or Viewer nodes is active and the rest are ignored — it searches the Active Node Tree Context (the tree of an expanded node group being edited) and falls back to the Root Node Tree Context (the top-level tree without expanded groups) if none is found, looking first for the active Group Output node and then the active Viewer node, running not at all if neither exists; consequently, adding a Viewer node has no effect on the viewport render when a Group Output node exists, since Group Output takes priority.

## Image Kernels

An image kernel is a small matrix of numbers that processes an image through a mathematical operation called convolution, where each kernel value sets how much a neighboring pixel contributes to the output pixel. Kernels are fundamental to image processing, used for blurring, sharpening, and edge detection by weighting and combining pixel neighborhoods to produce new detail. Concept: convolving an image with a kernel centers the kernel over each pixel, multiplies each neighborhood pixel by the matching kernel value, and sums the results into the output pixel's color, repeating for every pixel; the kernel values may be positive, negative, or fractional, and their pattern sets the effect. Common examples — Blur: a simple blur uses evenly weighted positive values, e.g. a 3x3 average blur kernel
```text
1/9 1/9 1/9
1/9 1/9 1/9
1/9 1/9 1/9
```
that softens the image by averaging neighbors. Sharpen: a sharpening kernel boosts edge contrast by emphasizing the center pixel against its neighbors:
```text
0 -1 0
-1 5 -1
0 -1 0
```
Edge Detection: edge kernels highlight brightness transitions by measuring differences between adjacent pixels, e.g. the Laplacian kernel
```text
0 -1 0
-1 4 -1
0 -1 0
```
or the Sobel kernel (horizontal edges):
```text
-1 -2 -1
0 0 0
1 2 1
```
Normalization: kernels are often normalized so all values sum to 1, preventing overall brightening or darkening — e.g. dividing each blur-kernel element by the total keeps brightness consistent after convolution. Creating a kernel in the Compositor: kernels can be built directly from Blender's nodes without an external image, useful for procedural or parameterized filters, blurs, and glare patterns editable interactively — start with a constant image (an Image Node at a small resolution like 9x9 or 15x15, or a solid color from an RGB node); shape the kernel by editing pixel values (use Ellipse Mask or Blur nodes for soft circular falloffs, combine masks with Mix nodes for complex or directional shapes like a star or streak, and scale strength with a Math node in Multiply mode or normalize by dividing by the total); then feed the procedural image into the Convolve Node's Kernel input, where its pattern and brightness control the effect. Tips: small images (under 20x20) make efficient, responsive kernels; use Normalize Kernel in the Convolve node to keep brightness balanced; animated masks or procedural noise make dynamic or flickering effects; and kernels with positive and negative values emphasize edges or textures.

## Limitations

Compositor limitations — Hardware limitations: the usual hardware limits apply to the GPU compositor (see Troubleshooting Graphics Hardware). Blender uses the same GPU resources for both the UI and the GPU compositor, with a few consequences. UI freezes: unlike Cycles rendering, the UI can become unresponsive with the GPU compositor on some slower GPUs. TDR on Windows: Timeout Detection Recovery (TDR) resets the GPU driver if a GPU compositing task exceeds the default 2-second limit — common on older GPUs with expensive nodes like the Bokeh Blur node — so to avoid unexpected resets, raise the TDR timeout.

Limitations — Known Constraints

EEVEE is designed as an interactive renderer. Some capabilities remain incomplete or fundamentally incompatible with its architecture without sacrificing speed.

This catalog covers the principal limitations encountered when working with EEVEE.

### Attributes and Properties

- Only 14 attributes from Geometry Nodes can be used in a single material.
- Up to 8 custom object attributes are accessible per material.

### Cameras

- Only perspective and orthographic camera types are currently available.

### Lights

- Lights use a single color and do not support node-based light definitions.
- Spot light Size does not affect cone softness, unlike Cycles.
- Area light Beam spread is unsupported.

### Light Probes

- Up to 128 light probe spheres may be active simultaneously.
- Up to 16 light probe planes can be active within the view frustum.
- Active light probe volumes must reside within Light Probes Volume Memory Pool.

### Indirect Lighting

- Light probe capture does not handle specular reflection; specular energy becomes diffuse.

### Shadows

- Shadow Map Raytracing may cause light leaks due to overlapping shadow sources. Reduce step count, enable jitter, or scale down light geometry to mitigate.
- Thin geometry (e.g., single-wall structures) leaks light on shadowed faces. Add thickness or lower Resolution Limit.

### Volumetrics

- Only single scattering is supported.
- Volumetric rendering affects camera rays only; reflections, refractions, and probes exclude volumetrics.
- Volumetric shadowing applies only to volumes and not to solid surfaces.
- Volumetric shadowing is restricted to the camera view frustum.

### Depth of Field

- Blended materials may exhibit artifacts with post-process blur but render correctly with sample-based methods. Disable post-process depth of field by setting Max Size to zero.

### Screen Space Effects

Scene representation relies on the depth buffer rather than ray-triangle intersection, which reduces complexity and increases performance but limits effect computation to visible areas. Only the nearest surface depth is recorded per pixel.

This architecture imposes constraints:

- Effects vanish past screen borders. The overscan feature partially alleviates this.
- Effects lack depth thickness information. Most provide a thickness parameter to govern pixel consideration.
- Occluded objects are excluded from calculations.
- Blended surfaces are invisible to these effects; they bypass the depth prepass.
- Objects in Holdout Collections do not render with screen space effects.

### Raytracing

- Blended and raytrace refraction materials do not appear in dithered material reflections.
- Blended materials are incompatible with raytracing.
- Only one refraction layer is correctly modeled. Secondary refraction can be approximated using the Thickness workflow.
- Only dithered materials without Raytrace Refractions can undergo refraction.

### Shader Nodes

- All BSDFs employ approximations for real-time performance, producing small visual differences from Cycles.
- Several utility nodes are incompatible with EEVEE.
- Certain BSDF combinations generate more noise than others, particularly Diffuse BSDF mixed with Refraction BSDF.
- Flat shaded displaced surfaces split into triangles.

See also
See Nodes Support for the complete unsupported node list.

### Numerical Limitations

- EEVEE operates on half-precision (16-bit) floating point by default, except shader node tree evaluation uses single-precision (32-bit).
- Render output maintains half-precision (16-bit) resolution.
- Combined and Light data passes clamp negative values to zero.

### Memory Management

GPU memory is handled by the GPU driver. Theoretically, only resources needed for a single draw call must fit. Complex scenes cause the driver to manage memory by swapping. In practice, excessive GPU memory use risks driver crash, freeze, or application termination.

No standard exists to predict whether resources will fit or render successfully.

### CPU Rendering

As a rasterization renderer, EEVEE relies exclusively on GPU processing. CPU rendering is not planned, as it would be inefficient. CPU involvement remains necessary for scene preparation before each frame.

### Multiple GPU Support

No current support exists for multi-GPU systems.

### Headless Rendering

Headless rendering is not available on Windows headless systems.

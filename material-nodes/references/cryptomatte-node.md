# Cryptomatte Node, Double Edge Mask Node, Ellipse Mask Node, Id Mask Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Cryptomatte Node; Double Edge Mask Node; Ellipse Mask Node; ID Mask Node; Enable Output Node; File Output Node; Group Output; Viewer Node; Brick Texture Node; Checker Texture Node.

## Cryptomatte Node

The Cryptomatte node uses a Cryptomatte image to mask one or several objects or materials, the matte usually produced by Blender itself (see the Cryptomatte render pass) but can come from other software supporting the standard. Inputs: Image (a color render of the scene, only needed for the Image output to work; if only the grayscale mask is wanted, leave it unconnected). Properties: Source (Render, using a View Layer's Cryptomatte passes, or Image, using a Cryptomatte from a multilayered OpenEXR file); Scene (the scene to take the Cryptomatte from, only with Source Render); Image (the image to use, only with Source Image); Cryptomatte Layer (the image layer, typically a View Layer plus a Cryptomatte type — Object/Material/Asset); and Matte ID (the comma-separated names of the objects/materials to mask, typeable but easier set with the + and - buttons; see Typical Usage). Outputs: Image (the Image input with the mask applied so only the selected objects/materials remain, the rest transparent), Matte (a grayscale mask of the selection), and Pick (a colored representation of the Cryptomatte for picking objects/materials). Typical usage: enable the Cryptomatte Object render pass in Properties ‣ View Layer ‣ Passes and render; create a Cryptomatte Node and a Viewer Node; connect the Render Layers node's Image output (or the Cryptomatte node's Pick output) to the Viewer's Image input; the render (or Cryptomatte) appears in the background (enable Backdrop in the header if not); click the node's button and click the object to include, repeating for others; then use the Matte output for a mask, or connect the Render Layers Image output to the Cryptomatte node and use its Image output for a masked render. Limitations: Cryptomatte sidecar metadata files aren't supported, the node can't be used in node groups, and Volume Objects aren't supported.

## Double Edge Mask Node

The Double Edge Mask node makes a gradient between two masks. Inputs: Outer Mask (the outside shape, fading from black at its own edges to white where it meets the Inner Mask); Inner Mask (the inside shape, fully white); Images Edges (when on, the image edges that intersect the outer mask count as outer-mask edges; otherwise the outer mask is open-ended); and Only Inside Outer (when on, only inner-mask edges inside the outer mask count; otherwise all inner-mask edges do). Output: Mask (standard mask output).

## Ellipse Mask Node

The Ellipse Mask node makes an image suitable for a simple matte or vignette mask. Inputs: Operation against the input mask — Add (the union: the generated mask's area is set to the given Value, while the rest of the input mask passes through unchanged, or black if there's no input mask), Subtract (the given Value is taken away from the input mask's values), Multiply (the intersection: the input mask is multiplied by Value within the generated area, and everything else becomes black), or Not (areas in both masks become black; generated-mask areas that are black on the input become Value; areas the generated mask doesn't cover stay unchanged); Mask (an optional base mask); Value (the generated mask's intensity); Position (the ellipse center as a fraction of width or height — 0.5, 0.5 centers it, 0.0, 0.0 puts its center lower-left); Size (the ellipse's width/height as a fraction of the total image width, not height — equal width and height give a circle); and Rotation (rotation about its center). Output: Mask (an elliptical mask merged with the input mask, at the current scene render dimensions). Tips: for soft edges, pass it through a slight Blur node; for a vignette, through a heavy blur. Usage: the node supports an interactive node-editor gizmo (enable Active Node gizmo and select the Ellipse Mask node) — drag edges to size width or height, corners to size both, the center cross (X) to move it, the center dot to rotate it, and hold Shift while dragging edges or corners to keep the aspect ratio.

## ID Mask Node

The ID Mask node makes a mask for a particular object or material in the render, relying on the Object Index or Material Index render pass available only with Cycles. (It's superseded by the Cryptomatte Node, which is more versatile and works in both Cycles and EEVEE.) Inputs: ID Value (the Object Index or Material Index pass — once enabled, reached via the IndexOB or IndexMA slot of the Render Layers Node) and Index (the index to mask, configured for objects at Properties ‣ Object ‣ Relations ‣ Pass Index and for materials at Properties ‣ Material ‣ Settings ‣ Pass Index), plus Anti-Aliasing (smooth the mask edges). Output: Alpha (a grayscale image, white where the object exists and black where it doesn't). Limitation: Volume Objects aren't supported.

## Enable Output Node

The Enable Output node toggles the visibility and value of a Node Group output socket, so a group output can be shown or hidden by an input value or condition. Inputs: Enable (a Boolean controlling whether the connected output socket is visible and active — when False, the group's matching output is hidden) and Value (the value passed to the output when enabled, of any supported type per the node's Data Type). Properties: Data Type (the type of the Value input and output, e.g. Float, Vector, Color, Geometry). Output: Value (the same data as the Value input when Enable is True; when False, the output is disabled and unavailable to the group output).

The Enable Output node toggles visibility and value of node-group output sockets, conditionally showing/hiding outputs based on input conditions. Enable (boolean field) controls socket visibility/activity; when False, the socket hides. Value is output when enabled; supports any data type. Data Type selects the output type. When enabled, Value outputs match input; when disabled, the output hides and unavailable to group output.

Enable Output Node

Toggles visibility and value of a Node Group output socket. Conditionally shows or hides outputs based on input values.

Inputs
Enable: Boolean field controlling socket visibility and activity. When False, the group's output hides.
Value: The data passed to the output when enabled. Type depends on the Data Type property.

Properties
Data Type: The format of the Value input and output (Float, Vector, Color, Geometry, etc.).

Outputs
Value: Passes through the Value input when Enable is True. Disables when Enable is False.

## File Output Node

The File Output node saves one or more images to disk while rendering or compositing, writing each connected input to the given directory and filename with the frame number appended — for example {Directory}/{File Name}{Socket Name}{frame number}.{extension}. Uses: automatically store the final image after a render, capture intermediate results from any point in the tree, or export multiple passes/outputs to files. Tips: save raw passes or intermediate steps without overwriting the main result; combine with the Cryptomatte Node or other utility passes to export custom compositing data; it's especially handy in production pipelines needing multiple outputs per render; and both the File Name and the image names (when saving several) can use #### to force the zero-padded frame number into a specific spot, which also embeds the frame number in a single render. Inputs: none by default — add them by dragging an output onto the blank socket area or via the Images/Layers panel, each input being an image written to disk; when Media Type is Image, input names also build subdirectories, so a name containing a slash (/ or \) is read as a directory hierarchy with missing folders created automatically (e.g. passes/diffuse or masks/object_01). Properties: Directory (the base output directory); File Name (the base file name, possibly extended with frame numbers or layer names); and Media Type (how multiple inputs are stored — Image, saving each input as a separate file with its own format settings, or Multi-Layer EXR, saving all inputs in one multi-layer OpenEXR). Node Format (Sidebar ‣ Node ‣ Properties ‣ Node Format): file format and encoding per Media Type — for Image, the default for all outputs (override an individual one with Override Node Format in Images/Layers; see Saving Images), and for Multi-Layer EXR, see OpenEXR. Images/Layers (same Sidebar path): lists the input sockets whose names build the final file name — saving individual images, each output can be renamed and use the global Node Format or its own override; with Multi-Layer EXR, each input is a separate layer — with Override Node Format letting a selected output use a custom format (its options in the Item Format panel). Output Paths (same Sidebar path): shows each input/layer's final path and extension to verify naming. The node has no output sockets.

## Group Output

The Group Output node defines a node group's final output, deciding which values pass out to the parent node tree (or, in the Compositor, to the renderer) — in the Compositor it sets the image result sent to the renderer or image output after rendering. It updates automatically after each evaluation or render, and interactively when connected inputs change, provided all inputs are fully evaluated. Note: with several Group Output nodes in a tree, only the active one is used and the rest show an "Unused Output" warning, the active one being chosen in the node header. Inputs: none by default — sockets appear when outputs are defined in the Sidebar's Group tab (or when dragging a connection onto the blank socket area), each input being a group output socket exposable to the parent tree, and in the Compositor only the first image input is the final render result while extras are ignored. Properties: see Group Sockets. The node has no output sockets, its sole job being to define which values leave the group.

## Viewer Node

The Viewer node previews image data or value maps anywhere in a compositor graph — a diagnostic tool to inspect intermediate results without affecting the final output. Assign a node to a Viewer quickly with Shift-Ctrl-LMB on it, switch between Viewers by selecting one with LMB, and only the active Viewer (with the header icon) shows in the backdrop or Image Editor. Input: Image (sent straight to the viewer result; unconnected, the output is black). The node has no output sockets. Usage — keyboard shortcuts: Viewers offer a quick way to toggle between viewer nodes while compositing — Assign Shortcut (Ctrl-1, Ctrl-2, etc.: select a node and press to assign it, creating and activating a Viewer if none is attached, with the number shown at the node's upper right) and Activate Node (1, 2, etc.: press the assigned number to activate that node's Viewer output), supporting only number keys 1-9. Using the Image Editor: the Viewer can display results there by selecting Viewer Node in the header's linked Image data-block menu, showing the currently selected Viewer's image; save it with Image ‣ Save As… (Alt-S); and the Image Editor's header has three more options to view images with or without alpha, or the alpha or Z itself, with click-and-hold sampling values. (For Viewer-specific overlays like text info and render guides, see Guides Overlays.)

The Viewer node previews a node's results.

Inputs:
Color — the usual color input.

Properties — this node exposes no properties.

Outputs — this node produces no outputs.

Viewer Node

Displays data from inside a geometry node group in the Spreadsheet Editor and 3D Viewport. Geometry and attributes connected to the viewer display in the viewport; evaluated values appear in the spreadsheet. Scalar values and grids also show in the spreadsheet.

Note: The Viewer node cannot be used in the Tool context—only in the Modifier context.

Activation and Deactivation: Use Shift+Ctrl+LMB on a node or socket to connect it to the active viewer. In the View menu, toggle Viewer Node to show or hide all visualizations, comparing the result against the final output.

Keyboard Shortcuts
Assign (Ctrl+1, Ctrl+2, etc.): Select a viewer node and press to assign a number shown in the upper-right.
Activate (1, 2, etc.): Press the assigned number to activate that viewer. Only keys 1–9 work.

Viewing Single Socket Values: Sockets can show evaluated values directly in the node editor. The current value displays beside the input, enabling inspection without a Viewer node. Works for scalars and small types (Float, Integer, Boolean, Vector). Geometry and grids need the Viewer node or Spreadsheet.

Attribute Field Visualization: With both Geometry and field inputs connected, values visualize in the Viewport via Viewer Overlay. The domain auto-detects when possible, otherwise defaulting to Face Corner for meshes and Point for curves. Set manually from the node's properties if needed. The Spreadsheet shows only columns for the selected domain. Note: Geometry socket must be first.

Pinning: Pin the Viewer in the Spreadsheet to keep data visible even when inactive. Pinned data persists regardless of object or selection changes.

Inputs: Add by dragging a socket into the blank socket or via Viewer Items properties.

Properties
Domain: The attribute domain for Value input. Auto chooses based on connected nodes.

Viewer Items
Socket Type: The data type for the input.
Auto Remove: Remove automatically when unlinked.

Outputs: This node has no outputs.

Examples: Visualizing Noise Texture Factor and Index Attribute as text on the default cube.

## Brick Texture Node

The Brick Texture node adds a procedural texture of bricks. Inputs: Color 1/2 (the brick colors); Mortar (the color between bricks); Scale (overall texture scale); Mortar Size (the size of the filling, the "mortar," between bricks — 0 means none); Mortar Smooth (blur/soften the edge between mortar and bricks, useful with textures and displacement); Bias (the color variation between Color 1/2 — -1 and 1 use only one of the two colors, values between mix them); Brick Width (the brick width relative to the texture scale); and Row Height (the brick row height relative to the texture scale). Properties: Offset (the brick offset of the rows); Frequency (how often rows are offset — 2 gives an even/uneven row pattern); Squash (a factor adjusting brick width for particular rows set by Frequency); and Frequency (how often rows hold squished bricks). Outputs: Color (the texture color) and Factor (the mortar mask, 1 = mortar).

Brick Texture Node

Note: Ported from shader nodes; manual and images reference the shader version. Accepts field inputs/outputs. Vector input defaults to implicit position.

Tip: Texture nodes create details finer than geometry resolution. May cause Moiré patterns or aliasing.

Produces procedural brick texture.

Inputs
Color 1/2: Brick color.
Mortar: Color between bricks.
Scale: Overall texture scale.
Mortar Size: Grout width; 0 = no mortar.
Mortar Smooth: Softens the mortar/brick edge. Useful with displacement.
Bias: Color mix between Color 1/2. −1 and 1 use single colors; in-between values mix.
Brick Width: Brick width.
Row Height: Height of brick rows.

Properties
Offset: Determines the brick offset of the various rows.
Frequency: Determines the offset frequency. A value of 2 gives an even/uneven pattern of rows.
Squash: Amount of brick squashing.
Frequency: Brick squashing frequency.

Outputs
Color: Texture color output.
Factor: Mortar mask (1 = mortar).

Examples: Brick texture with colors changed, Squash 0.62, Squash Frequency 3.

### Brick Texture Node

A procedural texture that lays down a brick pattern.

### Inputs

Color 1/2
Colour of the bricks.

Mortar
Colour of the gaps between bricks.

Scale
Overall texture scale.

Mortar Size
How wide the filler between bricks — the "mortar" — runs; 0 removes it entirely.

Mortar Smooth
Softens and blurs the boundary where mortar meets brick, which can help alongside a texture and displacement textures.

Bias
Shifts the colour mix between Color 1/2 . At -1 and 1 only a single colour shows; values in between blend the two.

Brick Width
A brick's width as a fraction of the texture scale.

Row Height
A row's height as a fraction of the texture scale.

### Properties

Offset
Sets how far successive rows are shifted.

Frequency
How often rows get offset; a value of 2 alternates offset and non-offset rows.

Squash
Scales brick width on the rows picked out by the Frequency

Frequency
How often a row is made of "squished" bricks.

### Outputs

Color
Texture color output.

Factor
Mortar mask (1 = mortar).

### Examples

Brick texture: Colors changed, Squash 0.62, Squash Frequency 3.

## Checker Texture Node

The Checker Texture node adds a checkerboard texture. Inputs: Vector (the texture coordinate to sample at, defaulting to Generated coordinates if unconnected — and note this node can have precision issues with some vector inputs, with mitigations on the White Noise Texture page); Color1, Color 2 (the checker colors); and Scale (overall texture scale — the bounding box of the face divided by the scale, so a scale of 15 gives 15 alternating patterns over the UV bounding box, and other nodes like the Math Node can drive different patterns into this socket). This node has no properties. Outputs: Color (the texture color) and Factor (the Checker 1 mask, 1 = Checker 1).

Checker Texture Node

Note: Ported from shader nodes; manual references shader version. Accepts field inputs/outputs. Vector defaults to implicit position.

Tip: Texture nodes exceed geometry resolution, causing Moiré or aliasing.

Produces checkerboard texture.

Inputs
Vector: Sample coordinate; defaults to Generated coordinates if unconnected. Warning: Precision issues with some inputs (see White Noise Texture notes).
Color1, Color 2: Checker colors.
Scale: Overall scale. A factor of the bounding box divided by scale. Example: scale 15 = 15 patterns across the UV box. Vary patterns via Math node or other inputs.

Outputs
Color: Texture color output.
Factor: Checker 1 mask (1 = Checker 1).

Examples: Default Checker texture.

### Checker Texture Node

A texture that lays down a checkerboard.

### Inputs

Vector
Where the texture is sampled; with nothing plugged in it falls back to Generated coordinates.

Warning

Some vector inputs can give this node precision trouble. The notes on the White Noise Texture cover ways to work around it.

Color1, Color 2
Colour of the two checker squares.

Scale
Overall texture scale. It works as the face's bounding box divided by the scale, so a value of 15 lays 15 alternating squares across the whole UV bounding box. Feeding other nodes into this socket — the Math Node, for one — produces different patterns.

### Properties

This node has no properties.

### Outputs

Color
Texture color output.

Factor
Checker 1 mask (1 = Checker 1).

### Examples

Default Checker texture.

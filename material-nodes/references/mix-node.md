# Mix Node, Menu Switch Node, Normalize Node, Relative To Pixel Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mix Node; Menu Switch Node; Normalize Node; Relative To Pixel Node; Retime Node; Split Node; Switch Node; Switch View Node; Combine Cylindrical Node; Combine Spherical Node; Combine XYZ Node; Vector Nodes; Mix Vector Node.

## Mix Node

The Mix node blends value, color, and vector inputs by a factor controlling the interpolation, with extra blend modes in Color mode. Inputs: Factor (how much A and B mix) and A/B (the two inputs). Properties: Data Type (float, vector, color, or rotation); Factor Mode (Vector only — Uniform, one float, or Non-Uniform, a per-XYZ vector); Mix (Color only — the blend mode from the menu, see Color Blend Modes), with Add, Subtract, Multiply, Screen, Divide, Difference, Darken, Lighten, Overlay, Color Dodge, Color Burn, Hue, Saturation, Value, Color, Soft Light, Linear Light; Clamp Factor (limit the factor to 0.0-1.0, otherwise Extrapolation); and Clamp Result (Color only — limit the Result to 0.0-1.0). Output: Result (the mix in the chosen type). See the Mix Color Node for more examples.

Blends two images together, much as an image editor blends two layers.

Inputs:
Factor — the foreground image's opacity.
A — the background image; it sets the output's dimensions.
B — the foreground image.
Bear in mind that, unlike image editors where the foreground layer sits on top, Blender's foreground slot is the bottom one.

Properties:
Blending Mode — the blend to apply.
  Mix — plain alpha blending, usually called Normal in image editors.
  Darken — per color component, keeps the smaller of the two blended values.
  Multiply — multiplies the colors component by component; blending with white (1.0) does nothing, while blending with black (0.0) always yields black.
  Color Burn — inverts the background color, divides by the foreground color, and inverts the result.
  Lighten — per color component, keeps the larger of the two blended values.
  Screen — inverts both colors, multiplies, then inverts again.
  Color Dodge — divides the background color by the inverted foreground color.
  Add — sums the two colors.
  Overlay — uses Multiply blending when the foreground color's lightness is below 0.5, Screen blending when above.
  Soft Light — like Overlay, but gentler.
  Linear Light — uses Linear Burn (background + foreground - 1) when the foreground color's lightness is below 0.5, Linear Dodge (background + foreground) when above.
  Difference — per component, subtracts the lower value from the higher.
  Exclusion — adds the two colors, then subtracts twice their product.
  Subtract — takes the foreground color away from the background.
  Divide — splits the background color by the foreground.
  Hue — takes the background's saturation and value and the foreground's hue.
  Saturation — takes the background's hue and value and the foreground's saturation.
  Color — takes the background's value and the foreground's hue and saturation.
  Value — takes the background's hue and saturation and the foreground's value.
Use Alpha — whether to use the foreground image's alpha channel while mixing; the background's alpha is always used.
Clamp — clamps the output to the [0.0, 1.0] range.

Outputs:
Image — the mix result.

Examples — below are blending-mode examples plus some practical uses, such as blending a colored pattern with a flat color and a circular mask.

Fixing overexposure — the setup below shows how to rescue an overexposed render by darkening it and lifting contrast. The top RGB Curves Node darkens the image by scaling every color value down linearly; the bottom curve node raises contrast by pushing small values lower and large values higher; the Mix node then blends the pair.

Watermark Images — long ago a pattern was stamped into the wet paper pulp as it dried, leaving a sign of who made the paper and where, barely visible except in just the right light — probably the first subliminal advertising. Nowadays people watermark images to claim them as personal intellectual property, for subliminal promotion of the author or host, or simply to follow an image's spread across the web. Blender gives you a full toolset both to encode your watermark and to tell whether an image carries it.
  Encoding your Watermark in an Image — first build your own watermark: a name, a word, or a shape or image that's hard to replicate. Neutral gray works best with the suggested method, but you're free to use other colors or patterns, from a single pixel to a whole gradient. In the example we encode it at a set spot in the image with the Translate node, which helps later since we only check one location for the mark; we then run the color image through the RGB to BW node to get grayscale numbers, which feed the Map Range node to cut the mark to a tenth of its original strength. The Add node (a Mix node set to Add) sums the matching pixels, making the marked ones ever so slightly brighter. Of course, if you want the mark noticed, scale it less or give it a contrasting color; there are plenty of other approaches using different mix settings and fancier rigs, so experiment.
  Decoding an Image for your Watermark — when you spot an image you think is yours, use the node tree below to compare it against your stock (non-watermarked) original; here the Mix node sits on Difference while the Map Value node boosts whatever differs, so the original mark clearly stands out.

### Mix Node

Blend values, colors, vectors using a factor.
Color mode: additional blending modes.

### Inputs

**Factor**
Interpolation degree between A and B.

**A/B**
Inputs to blend.

### Properties

**Data Type**
Blend type: float, vector, color, rotation.

**Factor Mode (Vector)**

- **Uniform:** Single float controls.
- **Non-Uniform:** Vector controls per axis.

**Mix (Color)**
Blend mode: Add, Subtract, Multiply, Screen, Divide, Difference, Darken, Lighten, Overlay, Color Dodge, Color Burn, Hue, Saturation, Value, Color, Soft Light, Linear Light.

**Clamp Factor**
Limit factor to [0.0, 1.0] (off: Extrapolation).

**Clamp Result (Color)**
Limit result to [0.0, 1.0].

### Outputs

**Result**
Blended output per selected type.

### Examples

See Mix Color Node for more.

### Mix Node

The Mix Node blends value, color and vector inputs, with a factor controlling how much interpolation there is. Color mode brings extra blending modes along.

### Inputs

Factor
Sets how much mixing happens between the A and B inputs.

A/B
The two inputs that get mixed together.

### Properties

Data Type
The data type used for mixing. The node handles float, vector, color, and rotation data types.

Factor Mode (Vector only)
The factor mode can be set to Uniform or Non-Uniform . Uniform drives the factor from a single float; non-uniform drives the factor of each XYZ channel from its own vector component.

Mix (Color only)
Pick the blend mode from the select menu. See Color Blend Modes for what each one does.

Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light

Clamp Factor
Hold the factor value between 0.0 and 1.0. Leave it unchecked and the node runs with Extrapolation instead.

Clamp Result (Color only)
Hold the Result within 0.0 to 1.0.

### Outputs

Result
Outputs the mix result in the chosen data type.

### Examples

See the Mix Color Node for additional examples.

## Menu Switch Node

The Menu Switch node outputs one of its inputs by a selected menu item, evaluating only the active input for efficient switching. The menu entries are user-defined — added, removed, renamed, and reordered in the editor sidebar, and renaming an entry keeps the matching input socket's links. It works in node groups and the nodes-modifier UI: connecting the menu input to a Group Input node exposes the menu as a group input, and a menu socket in a group, reroute, or other pass-through node must connect to a Menu Switch node to work (an unconnected menu socket shows an empty menu). Connecting several Menu Switch nodes to the same output socket conflicts (even with identical entries), avoidable by wrapping a menu switch in a node group, since multiple groups of the same type share the same menu switch. (The Index Switch Node is similar but exposes the choices as an integer index.) Inputs: Menu (which input socket passes through), with one input per entry — the selected entry's input is evaluated and passed, labels renamable via Ctrl-LMB on the socket name or the Properties panel, more inputs added by dragging a connection onto the bottom empty socket or clicking the header icon, and unused inputs not computed (improving performance). Properties: Type (the data type handled). Outputs: Output (the value from the selected item's input, unchanged) plus a Boolean output per entry — true for the selected one, false for the rest — usable to trigger branches, control visibility, or drive conditional operations.

Passes one of its inputs through to the output based on an active menu selection.
Only the chosen input evaluates, making it efficient for switching between alternatives.

Menu entries are user-defined and editable through the editor sidebar or node properties.
The menu can appear in node groups when linked to a Group Input node.
For a menu socket to function in node groups or reroute nodes, it must connect to a Menu Switch node;
unconnected menu sockets show an empty menu.

If different menus connect to the same output, Blender reports a conflict.
Wrapping the Menu Switch in a node group avoids this, since identical group instances share the same internal switch.

See also: The Index Switch Node for switching via integer index.

**Inputs**

Menu
Selects which input socket to pass through.

Each menu entry creates one input socket. The active entry's input evaluates and propagates to the output.

Labels can be edited via Ctrl-LMB on the socket name or in the Properties panel.

New inputs are added by:
- Dragging onto the empty socket below the list
- Clicking the header icon

Inactive inputs skip evaluation, improving performance on large graphs.

**Properties**

Type
Sets the data type handled by the node.

**Outputs**

Output
Passes the selected input without modification.

For each menu entry, a Boolean output is also created.
The active entry's Boolean is true; all others are false.
Use these to activate downstream branches, toggle visibility, or control conditional logic.

### Menu Switch Node

The Menu Switch node passes one of its inputs through based on the menu item picked. Only the active input is evaluated, which makes switching between options efficient.

You define the menu entries yourself. Entries can be added, removed, renamed and reordered in the editor sidebar; renaming one keeps the existing links on its input socket.

The menu works in node groups and in the nodes modifier UI. Wire the menu input to a Group Input node and it shows up as a group input. A menu socket inside a node group, a reroute node, or other pass-through nodes has to reach a Menu Switch node to do anything; left unconnected, it shows an empty menu by default.

Hooking several Menu Switch nodes to the same output socket causes a conflict, even with identical menu entries. Wrapping a menu switch in a node group sidesteps it: several node groups of the same type can share one menu, since they all contain the same menu switch node.

| Conflict caused by connecting different menus. | Same node group can be connected without conflict. |

See also

The Index Switch Node is similar, but it exposes the choices as an integer index.

### Inputs

Menu
Decides which input socket passes through to the output.

One input is spawned per menu entry, and whichever input matches the chosen item gets evaluated and forwarded onward.

Relabel a menu item via Ctrl - LMB over its socket name, or from the node's Properties panel.

Two ways to add input sockets:
- Drop a connection onto the spare socket sitting at the bottom of the list.
- Hit the icon up in the node header.

Inputs nobody uses stay uncomputed, a help to performance across crowded node networks.

### Properties

Type
Decides the type of data the node handles.

### Outputs

Output
Passes through the value from the input tied to the selected menu item, unchanged.

A Boolean output is also spawned per menu entry. The one belonging to the chosen item reads true , the rest false . You can wire these Booleans to fire separate node branches, switch things visible or hidden, or steer conditional behaviour anywhere else in the tree.

## Normalize Node

The Normalize node finds a single channel's minimum and maximum values, then maps them to a 0-to-1 range — mostly useful for the Z-buffer. Input: Value (standard value input). Output: Value (standard value output).

## Relative To Pixel Node

The Relative To Pixel node converts values relative to the image size into pixel units — useful for screen-space operations needing absolute pixels, like blurring or positioning effects. Inputs: Value (a float or vector relative to the image size, to convert to pixels) and Image (used to determine the resolution, defining the reference size). Properties: Data Type (Float or Vector) and Reference Dimension — Per Dimension (scale X and Y independently by image width and height), X (scale by width), Y (scale by height), Greater (scale by the larger dimension), Smaller (scale by the smaller), or Diagonal (scale by the image's diagonal length). Output: Value (the input converted from relative to absolute pixels, matching the chosen Data Type).

## Retime Node

The Retime node adjusts the timing of input sequences, animations, or time-based effects by offsetting, skipping, or repeating frames — for slow motion, fast-forward, looping, or rhythmic stutter within compositing. Inputs: Offset (add or subtract a constant frame offset — positive delays, negative advances); Step (skip frames by this size — 2 plays every other frame, doubling speed); Speed (scale time globally — 1.0 normal, 0.5 half, 2.0 double); Cyclic (loop the input continuously when the retimed output exceeds the original range); and Cycle Length (the frames per loop cycle when Cyclic is on). Output: Frame (the remapped frame, connectable to frame-based inputs to drive animated or sequential effects).

## Split Node

The Split node combines two input images into one output, showing them side by side or along a rotated split line — useful for comparing two versions of one image — say, before and after a color correction or render tweak. Inputs: Position (a 2D vector locating the split line in normalized 0-to-1 coordinates, so (0.5, 0.5) centers it); Rotation (the split line's angle in degrees); Image (the first input, on one side); and Image (the second input, on the opposite side). Output: Image (the combined image divided by the split line). Gizmos: an interactive Node-Editor gizmo (enable Active Node Gizmo and select the Split node) shows a split line with draggable handles — drag the line to move the split, and use the central circular handle to rotate it interactively. Examples: typically used to compare two images in the compositor (connect to a Viewer Node for before/after, like an ungraded versus color-corrected render), and also to align scene transitions by showing one scene's last frame beside another's first for visual consistency.

## Switch Node

The Switch node switches between two images via a checkbox. Tip: the switch state can be animated with a keyframe, making it handy for bypassing nodes you don't want during part of a sequence. Inputs: Switch (unchecked passes the first input, "Off," to the output; checked passes the second, "On"), Off (the first image), and On (the second image). Output: Image (standard color output).

Routes one of two inputs based on a boolean condition.

When inputs are regular values, only the routed input evaluates.
When inputs are Fields, both may evaluate before selection is applied; do not rely on this node to skip expensive field computations.

See also: Menu Switch Node and Index Switch Node for multi-input selection.

**Inputs**

Switch
Determines which input passes through.

False
Routed when switch is false.

True
Routed when switch is true.

**Properties**

Type
Sets the data type handled by the node.

**Outputs**

Output
One of the two inputs unchanged.

## Switch View Node

The Switch View node combines the left and right views into one stereo 3D output — useful when you need to treat the views as separate images and combine them (see the multi-view workflow). Inputs: Left (the left-eye image) and Right (the right-eye image). Output: Image (a stereo 3D image). Example: the views to render are defined in the current scene views, much as the composite output resolution is defined in the scene render panel, regardless of the Image nodes' resolutions or Render Layers from other scenes.

## Combine Cylindrical Node

The Combine Cylindrical node turns cylindrical coordinates (R, Φ, Z) into a Cartesian vector (X, Y, Z) — the inverse of the Separate Cylindrical node — useful for building positions or directions from radial distance, rotation angle, and height, such as spiral shapes or cylindrical displacements. Inputs: R (the radial distance from the origin in the X-Y plane), Phi (the angle around the Z axis), and Z (the vertical height component). Output: Vector (the Cartesian vector for the input cylindrical coordinates).

Converts cylindrical coordinates (R, Φ, Z) to a Cartesian vector (X, Y, Z).
Inverse of Separate Cylindrical.

Useful for building positions or directions via radial distance, rotation angle, and height—
e.g., spirals or cylindrical deformations.

**Inputs**

R
Radial distance in the X-Y plane.

Phi
Angular rotation around the Z axis.

Z
Vertical or height component.

**Outputs**

Vector
The resulting Cartesian vector.

### Combine Cylindrical Node

This node converts cylindrical coordinates (R, Φ, Z) to Cartesian form (X, Y, Z), providing the inverse operation of the Separate Cylindrical node.

Use this node when constructing positions or directions from radial distance, rotation angle, and height—such as spiral formations or cylindrical deformations.

### Inputs

R
Radial distance from the origin measured in the X-Y plane.

Phi
Angle of rotation about the Z axis.

Z
Vertical component or height value.

### Outputs

Vector
The resulting Cartesian vector derived from the input cylindrical coordinates.

## Combine Spherical Node

The Combine Spherical node turns spherical coordinates (R, Φ, Θ) into a Cartesian vector (X, Y, Z) — the inverse of the Separate Spherical node — where spherical coordinates give a 3D point by its distance from the origin, horizontal rotation, and vertical inclination, useful for radial or rotational patterns and points on a sphere. Inputs: R (the radial distance from the origin), Phi (the azimuthal angle, horizontal rotation, around the Z axis), and Theta (the polar angle, vertical inclination, from the ground plane). Output: Vector (the Cartesian vector for the input spherical coordinates).

Converts spherical coordinates (R, Φ, Θ) to a Cartesian vector (X, Y, Z).
Inverse of Separate Spherical.

Spherical representation uses distance, horizontal rotation, and vertical inclination—
useful for radial or rotational patterns and sphere-surface coordinates.

**Inputs**

R
Radial distance from the origin.

Phi
Azimuthal angle (horizontal rotation) around the Z axis.

Theta
Polar angle (vertical inclination) from the ground plane.

**Outputs**

Vector
The resulting Cartesian vector.

### Combine Spherical Node

This node converts spherical coordinates (R, Φ, Θ) to Cartesian coordinates (X, Y, Z), functioning as the inverse of the Separate Spherical node.

Spherical representation describes a location using radius, azimuthal rotation, and polar inclination. This form proves valuable for creating radial or rotational arrangements and positioning points on a spherical surface.

### Inputs

R
Distance from the origin.

Phi
Azimuthal angle (horizontal rotation) measured around the Z axis.

Theta
Polar angle (vertical inclination) measured from the ground plane.

### Outputs

Vector
The resulting Cartesian vector from the input spherical coordinates.

## Combine XYZ Node

The Combine XYZ node builds a vector from its individual components. Inputs: X, Y, Z. This node has no properties. Output: Vector (standard vector output) — note the vector isn't normalized.

Assembles a vector from three scalar components.

**Inputs**

X, Y, Z
Scalar components.

**Outputs**

Vector
Standard vector output. Note: not normalized.

### Combine XYZ Node

This node constructs a vector from individual component values.

### Inputs

- X

- Y

- Z

### Properties

This node has no properties.

### Output

Vector
Standard vector output.

Note

The vector is not normalized.

## Vector Nodes

The Vector Nodes manipulate various kinds of vectors, such as surface normals and speed vectors.

## Mix Vector Node

The Mix node blends value, color, and vector inputs by a factor controlling the interpolation, with extra blend modes in Color mode. Inputs: Factor (how much A and B mix) and A/B (the two inputs). Properties: Data Type (float, vector, color, or rotation); Factor Mode (Vector only — Uniform, one float, or Non-Uniform, a per-XYZ vector); Mix (Color only — the blend mode from the menu, see Color Blend Modes), with Add, Subtract, Multiply, Screen, Divide, Difference, Darken, Lighten, Overlay, Color Dodge, Color Burn, Hue, Saturation, Value, Color, Soft Light, Linear Light; Clamp Factor (limit the factor to 0.0-1.0, otherwise Extrapolation); and Clamp Result (Color only — limit the Result to 0.0-1.0). Output: Result (the mix in the chosen type). See the Mix Color Node for more examples.

Blends two inputs using a control factor, supporting float, vector, color, and rotation types.
Color mode adds blend modes.

**Inputs**

Factor
Strength of interpolation between A and B.

A/B
The two inputs to blend.

**Properties**

Data Type
Supported: float, vector, color, rotation.

Factor Mode (Vector only)

Uniform: Single float controls all channels.

Non-Uniform: Vector controls each XYZ channel separately.

Mix (Color only)
Choose from: Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light.
(See Color Blend Modes for details.)

Clamp Factor
Lock factor between 0.0 and 1.0, or allow Extrapolation.

Clamp Result (Color only)
Constrain output to [0.0, 1.0].

**Outputs**

Result
The blended value in the selected data type.

**Examples**

See Mix Color Node for additional examples.

### Mix Vector Node

This node blends values, colors, and vectors using a factor to manage interpolation strength. Color mode supports additional blending operations.

### Inputs

Factor
Controls the interpolation proportion between A and B.

A/B
The two sources being blended.

### Properties

Data Type
The data type for blending. Supports float, vector, color, and rotation types.

Factor Mode (Vector only)
The factor mode may be Uniform or Non-Uniform. Uniform uses a single scalar. Non-uniform applies a vector independently to each XYZ component.

Mix (Color only)
Blend modes are selectable. Consult Color Blend Modes for mode details.

Add, Subtract, Multiply, Screen, Divide, Difference,
Darken, Lighten, Overlay, Color Dodge, Color Burn,
Hue, Saturation, Value, Color, Soft Light, Linear Light

Clamp Factor
Restrict the factor to the 0.0–1.0 range. Unchecked allows Extrapolation.

Clamp Result (Color only)
Restrict the Result to 0.0–1.0.

### Outputs

Result
The blended outcome based on the selected data type.

### Examples

See the Mix Color Node for additional examples.

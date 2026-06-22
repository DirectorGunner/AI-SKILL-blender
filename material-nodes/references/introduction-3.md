# Introduction (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Reference: Properties ‣ Visual Effects

Grease Pencil includes viewport real-time visual effects applicable to objects. Effects treat objects as images, applying whole-object changes (unlike modifiers targeting layers/materials/groups). Unlike modifiers, effects don't apply permanently. They provide quick visual-effect application—blur, pixelation, wave distortion, etc.

Note: Visual Effects suit quick viewport use. Final render use is possible but less precise than Compositor; use Compositor for accuracy.

Interface: Effect panels resemble modifier interfaces; similar fundamental components. See Modifiers Interface.

### Introduction

Geometry Nodes is a node-based modifier system for altering object geometry. Add a Geometry Nodes Modifier and configure nodes in the Geometry Node Editor to use it.

Modifier properties in the modifier stack are shown visually.

A node tree linked to a modifier is a Node Group. Geometry from before the modifier (original or prior-modifier output) enters the Group Input node. The node group processes it and outputs to Group Output, feeding the next modifier.

Geometry Nodes works on multiple geometry types:

- Meshes

- Curves

- Point Clouds

- Volumes

- Instances

See Modifier page for modifier interface details.

For expanding Blender with operator-building nodes, see Node-Based Tools.

3D scenes require at least three key components: Models, materials, and lights. This section covers modeling—the art and science of creating surfaces that mimic real-world shapes or express imaginative abstractions.

Modeling Modes — Depending on object type, different modes apply. Cross-mode switching during modeling is common; some tools exist in multiple modes, others are mode-specific.

Edit Mode: Primary modeling context. Used to edit meshes, curves, surfaces, metaballs, text objects, lattices. Only mesh modification occurs; to edit other objects, exit Edit Mode, select, and re-enter, or use Multi-Object Editing.

### Introduction

Think of modifiers as automatic, non-destructive operations applied to an object's geometry. Through them you can pull off plenty of effects that would be painfully tedious by hand (subdivision surfaces among them), all while the object's underlying geometry stays untouched.

The thing they alter is how the object shows up on screen and in renders, not the geometry you edit directly. You're free to pile several modifiers onto one object, where together they make up The Modifier Stack, and any time you want a modifier's effect made permanent you can Apply it.

To add one to the active object, reach for the Add Modifier operator, the "Add Modifier" button sitting atop the Modifiers tab of the Properties Editor, or Shift - A while that tab is focused. Whatever you add lands at the foot of the stack, so it runs last.

A wide assortment of modifiers ships with Blender, and on top of that users can roll their own by way of Geometry Nodes.

### Categories

Built-in modifiers fall into four categories:

Edit
Akin to the Deform modifiers described below,
yet for the most part these leave the object's geometry alone
and act on other data instead, vertex groups among them.

Generate
Constructive or destructive modifiers that reshape the mesh's whole Topology.
They can shift the object's overall look or graft new geometry onto it…

Deform
Set apart from the Generate group above, these alter only an object's shape, leaving its topology intact.

Simulate
Stand in for physics simulations. Usually they get slotted into
the modifier stack on their own the moment a Particle System or Physics simulation is switched on. Their sole job is to mark
the point in the stack where the simulation they stand for reads its base data.
For that reason they tend to carry no properties of their own, being driven instead by settings found in
other parts of the Properties Editor.

A category labeled "Hair" will also catch your eye;
it originates from a bundled Asset Library shipped alongside Blender.
See Hair Nodes for more information.

Users can roll their own categories by turning geometry node groups into assets
and filing them under an Asset Catalog. Whatever the catalog is called becomes the category name.
Should a user name a catalog after one of the built-in categories,
its node group lands at the foot of the matching menu.

Node Groups that are non-assets, or that fall under no category, show up in the "Unassigned" sub-menu.

Note

A Geometry Node Group only appears in the Add Modifier menu once its Modifier
property has been switched on.

### Interface

Every modifier's interface is built from the same set of basic parts, see Fig. Panel layout (Subdivision Surface as an example)..

Panel layout (Subdivision Surface as an example).

The panel header sits at the top.
Reading left to right, each icon stands for a different setting on the modifier:

/ Expand
Folds the modifier down so only its header shows and the options are hidden.

Type
An icon serving as a quick visual cue to the modifier's type.

Name
Within a single object every modifier carries its own unique name. Two on the same object can't share a name,
yet two on different objects can. The default name derives from the modifier type.

On Cage Meshes
Hinges on the prior setting; when on, you can edit the modified geometry directly
rather than the original.

Warning

Although items appear in their final, modified positions, what you edit is still the original data.

Wherever those positions drift apart the result can get confusing,
so you might prefer to switch it off in such cases.

Worth noting too: a few features ignore the cage positions, including:

- Snapping targets, vertex snapping among them.

- The transform gizmo works off the original positions.

Apply On Spline Curves Surfaces Text
Run the whole modifier stack, up to and including this one, on the control points of the curve or surface
rather than on its tessellated geometry.

Note

Out of the box, curves, texts and surfaces get turned into mesh-like geometry
before the modifier stack ever runs on them.

Edit Mode
Shows the modified geometry while in Edit Mode, alongside the original geometry you can still edit.

/ Realtime
Switches the modifier's effect on or off in the 3D Viewport.

/ Render
Switches the modifier's effect on or off in the render.

Note

Depending on the object and modifier type, the Square , Triangle and Surface icons might not show up.

Extras

Apply Ctrl - A
Turns the modifier "real": rewrites the object's geometry to match what the applied modifier produced,
and removes the modifier.

If you apply a modifier on an object that shares Object Data with others,
the object has to be made a Single User first,
done by accepting the pop-up message.

Warning

Apply a modifier that isn't first in line and the stack order gets disregarded
(it acts as though it were first), which can yield results you didn't want.

Apply as Shape Key
Tucks that modifier's result into a fresh relative shape key
and then drops the modifier from the stack.
Only modifiers that leave topology alone offer this (Deform modifiers, as a rule).

Note

In principle it ought to handle any geometry type that supports shape keys,
but right now meshes are the only thing it works on.

Save as Shape Key
Tucks that modifier's result into a fresh relative shape key
while leaving the modifier sitting in the stack.
Only modifiers that leave topology alone offer this (Deform modifiers, as a rule).

Duplicate Shift - D
Drops a copy of the modifier into the stack right beneath the current one.

Copy to Selected
Pushes the modifier from the Active object out to every selected object.

Move to First/Last
Shifts the modifier to the very top or very bottom of the stack.

Pin to Last
Holds the modifier at the tail of the stack.
A pinned modifier shows a pin icon on the right-hand side of its panel header.

Move to Nodes
Converts the current Geometry Nodes Modifier
node tree into a group node, ready for reuse across other trees.
The Move to Nodes Operator section spells this out.

Only the Geometry Nodes Modifier offers this operator.

Delete X , Delete
Removes the modifier.

(Move)
Shifts the modifier up or down the stack,
which alters the order in which the modifiers are evaluated.

A modifier can't be moved while Pin to Last is on.

Underneath this header sit all the options that belong to each individual modifier.

Tip

Hold Alt to act on every selected object at once
during operators like add, apply, remove, and move to index.

See Multi-Object Editing for more information.

### The Modifier Stack

A modifier is one link in a chain of non-destructive operations stacked over an object's geometry, and you can sequence them in almost whatever order suits you. People commonly call this arrangement a "modifier stack," and you'll run into it across various other 3D packages as well.

Inside a stack, the sequence the modifiers run in shapes the outcome. To reshuffle them, grab the grip icon at the upper right and drag your chosen modifier higher or lower. For example, the picture below shows Subdivision Surface and Mirror modifiers once they've traded places.

| The Mirror modifier is the last item in the stack and the result looks like two surfaces. | The Subdivision Surface modifier is the last item in the stack and the result is a single merged surface. |

The stack is evaluated top to bottom. Here the wanted outcome (shown on the right) comes from mirroring the object first and then working out the subdivision surface.

#### Active Modifier

Click a modifier in the stack and it becomes Active, drawn with an outline framing its panel. To make one active, click its panel background or its icon, or pick the modifier over in the Outliner.

The Geometry Node Editor relies on the active modifier to know which node group it's editing.

### Example

Here a plain subdivided cube has been worked up into a fairly intricate object by stacking modifiers on it.

Download example file.

### Introduction

In Blender, a Volume object amounts to a thin shell wrapped around an OpenVDB file.
OpenVDB is both a library and a file format built for storing volumetric data and moving it between programs.
Other software, Houdini among them, can produce OpenVDB files,
as can Blender's own fluid simulation cache.

You make Volume objects from the Add menu in the 3D Viewport,
or simply by dragging vdb-files and dropping them into Blender.
To animate, bring in a frame sequence of OpenVDB files.

WDAS cloud data set rendered in wireframe, Workbench, and Cycles.

### Rendering

Rendering volumes works just like rendering smoke simulations. By default,
the Principled Volume shader
handles volume objects. It looks for grids named density ,
color and temperature out of the box. When those aren't around,
you'll need to point the shader nodes at a different grid name.

### Limitations

- OpenVDB is great at holding sparse volumes — ones that aren't packed
into a tight bounding box but may sprawl across space.
In Blender, though, they still get rendered as dense volumes,
which isn't great for performance or memory. A future release will improve this.

- OpenVDB files can additionally hold level sets and points.
Level set grids can be read, but rendering them as surfaces isn't supported yet.
Importing OpenVDB points isn't supported either.

### Introduction

To start a mask, flip an Image or Movie Clip editor's header mode over to Mask.
Doing so brings up the tools and properties masks need in the editor panels
while tucking away the ones that don't apply.

Masks serve plenty of purposes. In a motion tracking workflow they can mask out
or steer a particular object within the footage.
They handle manual rotoscoping to lift an object out of the footage,
or act as a rough matte for green-screen keying. Since a mask isn't bound to any one image or movie clip,
it works just as well for building motion graphics or other Compositor effects.

Using the Mask node to isolate an object in compositing.

Masks get edited in the Movie Clip Editor and Image Editor,
whereas the Compositor and Sequencer merely consume masks that already exist.

A mask can be animated over time so it tracks some object in the footage —
a running actor, for instance. Pull that off with shape keys, or by parenting the mask to tracking markers.

### Mask Data-block

A mask data-block bundles together multiple mask layers and splines.
It's the top-level entity used for masking.
Masks can be reused across different places and carry global parameters covering every entity inside them.

Blender's 2D video stabilization builds on its image feature-tracking: you use tracking points to remove shake, bumps, and jerks from footage. It's typically part of a 2D workflow that prepares and improves footage before further processing or modeling. This page explains how it works, introduces the related terms and concepts, details the interface controls, and ends with practical hints. Typical uses: fixing minor flaws (a shaky tripod, a jerk in camera movement); a "poor man's steadycam" when a real one wasn't available, affordable, or practical; and prepping footage for masking, matching, and rotoscoping. 2D stabilization often has to cope with somewhat imperfect, flawed footage.

How It Works: to detect spurious movement in a shot, the stabilizer assumes a simplified movement model and fits the tracked features' movement to it to derive a compensation. This only works as far as the model is adequate, yet in practice the approach works surprisingly well even on complicated shots where the basic assumption is just an approximation of much more elaborate movement. The model assumes movement by an affine-linear transform: the camera is pushed up/down/sideways by a translation component, then the image is tilted and scaled around a pivot point (the rotation center). Compensation proceeds in two steps: first the translation offset is detected from the weighted average of all translation tracking points; after compensating it, additional rotation/scale tracking points detect rotation around a given pivot, again via a weighted average of those points. In the current version the pivot is anchored to the weight center of the translation tracking points, so the detected translation is effectively factored out — not always optimal, especially when tracks have gaps or don't span the whole footage, and better pivot control is planned for future releases.

Stabilization Tracks: any stabilization needs tracked image features to derive the movements; these tracking points or "tracks" come from Blender's image feature-tracking component. Choosing which points to track is tricky but crucial — since you're often dealing with imperfect footage, averaging tracks helps work around image or tracking errors, and when the footage has perspective-induced movement, tracking points placed symmetrically above and below the horizon can cancel spurious movement and stabilize the focal area between them. Tracks go into two groups: first, a list used to compensate for jumps in camera location, from which a weighted average is computed and kept constant through the whole shot (so it's good to use markers close to and centered on the most important subject); and second, a selection used to keep the image's rotation and scale constant, where you may reuse the same tracks but usually do best with points far from the image center and symmetric on both sides to capture angular movement more precisely, again averaged and held constant.

Footage, Image & Canvas: stabilizing video means distinguishing several frames of reference. The image elements in the footage move irregularly within the original image boundaries — the very reason we stabilize. When stabilization succeeds, those elements can be considered stable while, in exchange, the footage's image boundaries take on irregular movement and jump around the opposite way. Since the actual subject is now stable, we can treat it as attached to a fixed backdrop, which we call the canvas. The canvas concept helps handle deliberate camera moves and offers another benefit: video pixels are frequently non-square, so they must be stretched and expanded before any sensible rotation stabilization, making the canvas, by definition, the reference for an undistorted display of the image contents. When the camera was moved intentionally, there's yet another frame of reference beyond the canvas: the frame (or "cadre") of the final image we want to create. To see the distinction, consider a hand-held pan to the right: since the camera turned right, the contents move left within the original frame, but if the stabilizer succeeds in "fixing" the contents relative to the canvas, the original boundaries drift irregularly to the right and the contents gradually vanish behind the left boundary — pan far enough and you're left with an empty black backdrop. The only fix is to move the final image frame along to the right, following the originally intended pan, this time smoothly and cleanly.

Animate Expected position/rotation/scale to apply intentional camera movement.

The "Dancing" Black Borders

Stabilization success creates jittery footage boundaries (inevitable). Zoom-reduction hides them; Expected position animation centers content to lower zoom demand.

Autoscale finds minimum zoom eliminating borders. Large jumps trigger over-zoom (single zoom across entire duration). Manual animation of zoom + Expected position often yields better results.

Motion Tracking serves camera/object motion capture and applies tracking data to 3D objects (created or imported) via constraints.

Blender's toolkit includes powerful 2D tracking and 3D reconstruction (camera and object tracking), plus specialized features (plane tracks for compositing). Tracks also drive Mask Editor deformation for rotoscoping.

Views

Tracking Mode offers three views; toggle using the header selector. The entire Movie Clip editor switches. To show curve or dope sheet, split the editor with one in the alternate view.

Manual Lens Calibration

All cameras record distorted video—intrinsic to optical design.

Accurate camera solving demands exact focal length and distortion values.

Focal length comes from camera settings or EXIF; external OpenCV tools estimate distortion. Within Blender, use Annotation tool to draw (poly line brush) straight edges on footage; adjust distortion values until annotations align edges.

For precision, OpenCV Grid calibration (identical distortion model) suits Blender workflows.

Camera and Object Motion Solving

Blender solves camera motion (including tripod shots) and object motion relative to camera. Plane Tracks solve marker motion across a single plane.

Tools for Scene Orientation and Stabilization

Post-solve, orient the 3D scene for convenient compositing. Tools define floor, origin, and X/Y axes.

Footage often contains spurious jumps, jitter, or handheld camera wobble. 2D Stabilization detects and compensates such motion (based on tracked elements) to enhance final quality.

### Introduction

Simulating cloth is among the most challenging problems in computer graphics. At first glance, cloth seems straightforward—a daily-life object we ignore—yet its behavior involves intricate dynamics and environmental responses. Modeling fabrics, flags, and banners typically employs 2D meshes, though 3D representations work too for items like stuffed animals, cushions, inflatable objects, and spheres.

Fabric responds to forces, collisions, wind, and aerodynamic effects—all configurable to suit your needs.

| Cloth example.  | Cloth on carved wooden men (made by motorsep).  | Cloth example.  |

When cloth physics are activated on a mesh, the Cloth Modifier is appended to the object's modifier chain. As a modifier, it participates with others (Armature, Smooth) where the final shape results from the modifier sequence order. For instance, apply smoothing after the cloth computes its deformed state.

You can Apply the Cloth Modifier to finalize the mesh's current state at a specific frame, which removes the modifier itself. Suppose you drape cloth over a table, allow the sim to conclude, then apply the modifier—you've effectively used the simulator to reduce modeling work.

Simulation results store in a cache, so the mesh's calculated state at any frame needn't be recomputed. If changes are needed, you retain control over cache clearing and rerunning. The first simulation run is fully automatic—no baking step interrupts the process.

Background computation of mesh deformation at each frame occurs automatically, permitting continued work during calculation. Computation intensity depends on hardware and simulation detail; you'll notice lag corresponding to computational demand.

Note

Do Not Jump Ahead

If you create a cloth sim and Blender hasn't yet computed shapes through the duration, then advance many frames forward, the simulator may fail to show an accurate mesh state for that frame if prior frames haven't been processed.

### Workflow

A standard approach involves these steps:

- Model the cloth object with an initial shape.

- Classify the object as "cloth" in the Properties Physics tab.

- Design other objects that will obstruct the cloth.
Ensure the Deflection modifier appears last in the modifier chain, after any other deforming modifiers.

- Apply lighting, materials, textures, and unwrap UVs if needed.

- Optionally add particle effects such as steam from the surface.

- Execute the simulation and refine parameters until results satisfy you.
The Timeline editor's playback controls excel in this phase.

- Consider aging the mesh to a point in the sim to create a new default starting posture.

- Make frame-by-frame mesh adjustments to remedy minor defects.

Tip

To prevent unstable behavior, ensure the cloth object doesn't intersect any deflection objects beforehand.

### Springs

Internally, cloth simulation employs virtual springs linking mesh vertices. Four spring types regulate cloth bending, each detailed below and shown in the accompanying image:

Illustration of cloth springs; tension springs (blue),
compression springs (red), shear springs (cyan),
and angular bending springs (green). 

Tension Springs
Establish cloth rigidity against pulling.

Compression Springs
Determine resistance to collapsing or squashing.

Shear Springs
Like compression springs, but manage angular warping.

Angular Bending Springs
Govern resistance to folding and crumpling.

These four spring varieties can be tuned independently in the Physical Properties panel. While these handle surface springs, internal springs are an option for 3D meshes and behave akin to Soft Bodies.

### Introduction

Dynamic paint transforms objects into canvases and brushes via modifier and physics, outputting Color Attributes, image sequences, or deformation. This enables effects like snow footprints, rain wetting, wall paint adhesion, or gradual freezing.

### Activating the Modifier

How to activate the Dynamic Paint. 

Dynamic Paint activates in the Properties Physics tab "Physics" section.

### Types

The modifier has two types: Canvas and Brush.

Note

Brush and canvas can coexist. The same object's brush doesn't influence its canvas, though it affects others.

See also

- A step-by step introduction.

- A detailed guide covering every parameter with images and examples (currently outdated).

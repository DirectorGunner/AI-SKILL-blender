# Introduction (part 1)

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

Python is an interpreted, interactive, object-oriented language featuring modules, exceptions, dynamic typing, high-level built-in data structures, and classes, pairing considerable power with clear syntax. Scripts are a flexible way to extend Blender — most areas can be scripted, including animation, rendering, import/export, object creation, and automating repetitive work — and they reach Blender through its tightly integrated API. General information, useful while scripting: Python.org (about Python), the Blender Python API (the official reference to consult while writing), and the API Introduction (a short, example-filled starter); for distribution, Creating Add-ons (encapsulating and sharing scripts) and Creating Extensions (sharing on the Blender Extensions platform). Getting started: the manual's Text Editor, Python Console, and Info Editor pages take you from basics to advanced scripting, and external resources include the Python API Quickstart, "CG Cookie: Blender 2.8 Python Scripting Superpowers for Non-Programmers," "Olav3D: 3D Programming for Beginners Using Python," and the Blender Artists Python Support forum. Extending Blender — add-ons: scripts that give Blender extra functionality, enabled in the Preferences; beyond the executable, many people have written hundreds of them, with officially supported ones bundled with Blender and others provided through Blender Extensions (not part of official releases, often reliable and useful but not yet guaranteed stable) — see the Add-ons docs for those included with Blender. Scripts: besides add-ons, other script types extend Blender — Modules (utility libraries imported by other scripts), Presets (settings for tools and key configurations), Startup (imported when Blender starts; they define most of the UI and some core operators), and Custom Scripts (typically run once from the Text Editor). Saving your own scripts — file location: scripts load from the scripts folder of the local, system, and user paths, and you can add another search path in Preferences ‣ File Paths; installation: add-ons install conveniently through Preferences via the Install… button and selecting the .zip.

Animation is making an object move or change shape over time, which can happen several ways: moving the whole object (changing its position, orientation, or size over time), deforming it (animating its vertices or control points), or inherited animation (moving based on another object such as a parent, hook, or armature). This chapter covers the first two, whose basics also underpin later chapters, and animation is usually done with keyframes (see also Physical Simulation and Motion Tracking). State colors: properties take different colors and menu items per state — Gray (not animated), Yellow (keyframed on the current frame), Green (keyframed on a different frame), Orange (changed from the keyframed value), and Purple (driven) — though the changed-value highlight currently doesn't work with NLA. Rigging is the general term for adding controls to objects, typically for animation, often using one or more of: Armatures (flexible joints for mesh objects, common for skeletal animation), Constraints (to control which motions make sense and add rig functionality), Object Modifiers (several help control mesh deformation), Shape Keys (to control target shapes such as facial expressions), and Drivers (so the rig controls many values at once and updates some properties automatically from changes elsewhere). Rigging can be as advanced as the project needs — a rig effectively defines a UI for the animator without exposing the underlying mechanisms. Examples: an armature is often paired with a modifier to deform a mesh for character animation; and a camera rig can replace animating the camera directly, simulating real-world rigs (a boom arm on a rotating pedestal, with effects like camera jitter). This chapter is a reference and pairs well with resources such as Nathan Vegdahl's character-rigging introduction, Humane Rigging.

A keyframe is a time marker storing a property's value — for example, that a cube's horizontal position is 3 m on frame 1. Its purpose is interpolated animation: add another key on frame 10 putting the cube at 20 m, and Blender computes the cube's position for every frame between, per the chosen interpolation (Linear, Bézier, Quadratic, etc.). An overview of existing keyframes is in the Dope Sheet. Visualization: in the 3D Viewport, when the current frame is a keyframe for the active object, that object's name (upper-left) turns yellow. Interpolation: keyframe interpolation is shown and controlled by animation curves (F-Curves), viewable and editable in the Graph Editor, where the curve's X axis is time and Y is the property value, keyframes define points, and interpolation is set by extra parameters. The Interpolation Mode is the main per-keyframe setting for how the curve runs from that key to the next, with fixed-shape modes (Constant, Linear, Quadratic, etc.) and a free-form Bézier mode. Extrapolation sets how the curve extends before the first and after the last key, mainly Constant and Linear, and it can also loop. Bézier interpolation uses handles with a type and position: Free and Aligned handles are positioned manually in the Graph editor, while Vector, Automatic, and Auto Clamped handles are computed from keyframe values; Interpolation, Extrapolation, and Handle Type can also be changed in the Dope Sheet. The three automatic handle types are computed per the per-curve Auto Handle Smoothing setting: None resembles most software, considering only the immediately adjacent keys, while Continuous Acceleration considers the whole curve's shape for smoother out-of-the-box results, though changes to one key then affect a larger section and Automatic handles tend to overshoot more. Keyframe types: keyframes can be colored to distinguish regular keys from animation events or states — Keyframe (white/yellow diamond, normal), Breakdown (small cyan diamond, e.g. transitions between key poses), Moving Hold (dark gray/orange diamond, a key adding slight motion around a holding pose, with a bar shown between them in the Dope Sheet), Extreme (big pink diamond, an "extreme" state or other use), Jitter (tiny green diamond, a filler or baked key for keying on ones or other use), and Generated (dark diamond, made by a tool such as Copy Global Transform: Fix to Camera — this type tells Blender and add-ons it's safe to remove and regenerate, so mark hand-made animation with it carefully). Handles & interpolation display: the Dope Sheet can show a keyframe's Bézier handle type and flag segments with non-Bézier interpolation, for basic interpolation editing without the Graph Editor — the icon shape is the handle type: Circle (Auto Clamped, default), Circle With Dot (Automatic), Square (Vector), Clipped Diamond (Aligned), Diamond (Free); when a keyframe's handles differ, or for summary rows over multiple curves, the icon furthest down that list is used (so a circle on a grouped row guarantees no grouped channel has a non-auto key). Horizontal green lines mark non-Bézier interpolation (dimmed in summary rows where not all grouped channels share it), and this display can be turned off via the Dope Sheet's View menu "Show Handles and Interpolation".

The Dope Sheet gives a bird's-eye view of the keyframes in the scene. It draws on classical hand-drawn animation, where animators used a chart marking exactly when each drawing, sound, and camera move happens and for how long. You can also bring up Playback Controls to drive the playhead.

Dope Sheet Modes — the editor has several modes, picked from a header dropdown. The default Dope Sheet mode surveys most kinds of animatable data; for others, such as masks, you switch to a more specific mode. They are:
Dope Sheet, Action Editor, Shape Key Editor, Grease Pencil, Mask, and Cache File (originally intended to display baked animation data from Alembic files, though it was never implemented).

Main Region — the Dope Sheet Editor presents a stack of channels (animatable properties), and for each channel a row of keyframes spread along the time axis. Keyframes vary in color and shape:
  Gray — unselected.
  Yellow — selected.
  Other colors — a custom keyframe tag you set (Key ‣ Keyframe Type).
  Diamond — Free Keyframe Handle (Key ‣ Handle Type).
  Round — Auto-Clamped Keyframe Handle.
  Circle — Automatic Keyframe Handle.
  Square — Vector Keyframe Handle.
  Rhombus — Aligned Keyframe Handle.
  Gray bar between keys — a held key, meaning the pair of keyframes match.
  Green line between keys — that curve segment runs on custom interpolation (Key ‣ Interpolation Mode).
  Upwards arrow — a local maximum in the curve (shown when View ‣ Show Curve Extremes is on).
  Downwards arrow — a local minimum in the curve.
Click to select a keyframe and drag to move it; the Select and Key menus hold more options.

Channels Region — sits down the left side of time-based editors such as the Dope Sheet and the Graph Editor. It lists a tree of items (objects, bones…) and their animated properties, the latter also called "channels," each with an F-curve that describes how its value changes over time.

The rows carry color codes:
Dark blue — scenes, objects.
Light blue — actions, shape keys, and the like.
Green — channel groups.
Gray — channels.
Search (Ctrl-F) — filters the channels by part of their name; click Invert to instead show channels that lack the search text.

Channels — the headers hold these toggle buttons:
/ Pin — keeps the row and its children visible even after you select a different object.
/ Hide — hides the keyframes and curve tied to the channel.
/ Modifiers — switches off the curve's modifiers.
/ Mute — switches off the curve, so the animation acts as if it isn't there.
/ Lock (Tab) — stops the curve from being edited.
Note: this works in the Nonlinear Animation Editor too, but there it only locks the strips, not the underlying F-curves.

Selection:
Select single header — LMB.
Add/Remove single header — Ctrl-LMB.
Select range — Shift-LMB.
Select All — A.
Deselect All — Alt-A, or double-tap A.
Box Select — drag LMB.
Box Add — drag Shift-LMB.
Box Remove — drag Ctrl-LMB.
Select all keyframes in the channel — double-click LMB on its header.

Editing:
Rename (anything but a channel) — double-click LMB.
Delete selected — X or Delete.
Lock selected — Tab.
Sliders — turning on View ‣ Show Sliders adds a value slider beside each channel; changing one alters the curve's value at the current frame, inserting a keyframe if none exists yet.

The Outliner shows the blend-file's content as a tree, which you can use to survey the scene's data; pick and unpick objects; render objects unselectable or hidden in the 3D Viewport; keep objects out of the render; duplicate and delete objects; and manage parent/child relationships and collections. Items with a left-hand arrow expand: LMB it to expand one, drag LMB to expand several, or Shift-LMB to expand recursively.

### Introduction

### Animating with Grease Pencil

Grease Pencil exists to bring a 2D animation toolset fully inside a 3D environment.

Sample animation showing Grease Pencil object keyframes in the Dope Sheet with onion skinning enabled.

Several animation routes are open to Grease Pencil objects in Blender:

Moving as a whole object
Shifting the object's position, orientation, or size over time;

Drawing frame by frame
Hand-drawing a single frame at a time, the traditional approach.

Deforming them
Animating the underlying points;

Inherited animation
Letting one object ride along on another object's motion (a parent, hook, armature, and so on). Handy for cut-out animation, among other uses.

The Animation & Rigging chapter gives the full picture of animation in Blender.

### 2D Traditional Animation

### Keyframes
Traditional Grease Pencil animation runs on keyframes, each storing the stroke data for one frame or a span of frames.

Turn Auto keyframe on, and drawing a stroke in a Grease Pencil object's Draw Mode drops a new keyframe at the current frame on the active channel. Turn it off, and you either add a keyframe by hand or your new strokes pile onto the active keyframe.

Keyframe Editing has the details.

Note

A Dope Sheet channel maps to the active 2D layer of the Grease Pencil object.

For keyframe work, Grease Pencil supplies its own Dope Sheet mode; the Grease Pencil mode in the Dope Sheet section explains it. The Stroke menu also carries several keyframe-and-stroke tools, documented under Animation tools.

### Onion Skinning
Onion skinning is a staple of traditional animation, and Grease Pencil packs plenty of flexibility and settings into the feature. Onion Skinning covers it.

### Animation Options

### Draw Mode
Draw Mode exposes three animation-related options to work with.

General drawing/animation options.

Add Weight Data
Switch this on and fresh strokes pick up weight data from the active vertex group and its weights. With no vertex group chosen, no weight data is written.

Cut-out animation benefits here, for instance, letting you add a drawing onto the same vertex group without having to build it afterward.

Weight Paint Mode has more.

Additive Drawing
On a new frame, the strokes from the previous or active frame carry over as a foundation for the new one.

Multiframe
To paint new strokes across several frames of your animation, switch on multiframe drawing.

Toggle it with the Multiframe button beside the modes selector (the faded-lines icon). Multiframe has more.

### Edit Mode
Edit Mode offers one animation-related option.

Multiframe editing.

Multiframe
At times you need to tweak several frames together with the edit tools, say to reposition drawings throughout an animation.

Turn on multiframe editing with the Multiframe button beside the modes selector (the faded-lines icon). Multiframe has more.

### Examples

### Traditional Animation
Here is how to animate a bouncing ball the traditional 2D way using Grease Pencil.

Begin by choosing File ‣ New ‣ 2D Animation to open a fresh 2D animation template. It comes primed for a fast start: a Grease Pencil object already exists, Onion Skinning is on, Auto Keyframe is enabled, and you are in camera view.

Set the Timeline to span frames 1 through 24. On the first frame, reach for the Draw Tool and place a ball in the upper-left of the viewport — your opening extreme. Advance to frame 12 and add a squashed ball down in the centre for the breakdown, then move to frame 24 and set another extreme over in the upper-right. From there, sketch in as many of the intervening frames as you like, leaning on the onion-skin ghosts to judge spacing. Press Spacebar to play it back.

Curves and Surfaces are specialized Blender object types.
They use mathematical functions (interpolation)
rather than linear interpolation between points.

Blender supports both Bézier and NURBS.
Both are defined using "control points"
(or "control vertices") forming a "control polygon".

Blender logo made from Bézier curves. 

Both are named for their mathematics. Choosing between them depends on computation style
rather than visual outcome. Bézier curves are intuitive—they start and end at chosen points.
NURBS are more efficient to calculate with many curves.

The main benefit of curves over polygonal meshes is that curves need
less data, consuming less memory and storage. However, this procedural approach can increase render costs.

Certain techniques, like
extruding a profile along a path,
require curves. Conversely, mesh editing offers finer vertex control; if precision matters,
mesh modeling may work better.

Bézier curves are standard for typography and logo design.

They appear often in animation, as motion paths (see constraints)
and as F-Curves
to vary object properties over time.

See also

Modifiers & Constraints

- Curve Modifier

- Follow Path Constraint

- Clamp To Constraint

Metaballs are implicit surfaces, defined not by explicit vertices or control handles but as mathematical formulas evaluated in real time by the renderer.

Visually, metas produce soft, fluid, gel-like shapes with pronounced curvature. When two metas approach each other, they interact—the surfaces merge and blend together like water droplets in freefall. Moving them apart restores each to its original form.

Each metaball corresponds to an underlying mathematical structure. The Active Element panel allows switching between these underlying types at any time.

Metas serve well for special effects or as the foundation for detailed modeling. A collection of metas can establish an initial form, which is later converted to a mesh for refinement or sculpting. They are also highly efficient for ray-traced rendering.

Objects bearing meta names determine family associations and interaction rules—only metas within the same family affect each other. Transformations applied in Object Mode directly alter the resulting geometry for affected families.

In Object Mode, the computed surface displays with a black selection ring.

In Edit Mode, the meta appears as a wireframe mesh (shaded or black outline, without individual vertices) surrounded by two colored circles: red for selection (highlighted pink when chosen) and green to directly adjust the meta's stiffness value (light green when active). Outside of scaling, highlighting either circle produces the same effect.

### Introduction

Text objects hold a string of text and belong to the same family as curve and surface objects, since fonts are vector data — they're built from curves.

To map letter codes onto the geometry that represents them in the 3D Viewport, Blender leans on a "Font System."
That system ships with a font of its own, yet it can also pull in external fonts —
PostScript Type 1 , OpenType and TrueType among them.
On top of that, any object already in the current blend-file can stand in as a letter.

An example of an extruded text.

With text objects you can author and render 2D or 3D text, complete with advanced layout options such as justification and frames.
Out of the gate, letters are nothing more than flat filled surfaces, just like any closed 2D curve.
But, like curves, they can be extruded
and have modifiers applied to them
(to make them follow a curve, for instance).

Blender lets you lay text out in fairly sophisticated ways:
splitting it into columns or blocks, mixing alignments, and the like.

Conceptually those capabilities echo what DTP software
(Scribus, say) offers, even if they're fairly rudimentary at this stage.

Tip

A text object can be converted either to a curve or straight to a mesh
via Convert in Object Mode.

Note

Each text object tops out at 50,000 characters. Keep in mind, though,
that the more characters one text object holds,
the more sluggishly it responds as you work with it.

### Introduction

Transform covers the family of operations that reshape 2D and 3D elements.
That covers things such as moving, rotating, scaling,
and putting other operations to work on the objects in your scene.

They do their job by altering the geometry, which you're free to edit directly.

### Operators

Blender bundles several transformation operations.
A few of the main ones are:

### Move

Use this to slide elements along the scene's X, Y, and Z axes.

### Rotate

Turn elements around the X, Y, and Z axes with this one.

### Scale

Scaling grows or shrinks an object along the X, Y, and Z axes.

### Align to View

Handy for lining objects up with the camera's view or some other chosen viewpoint.

### Mirror

Mirrors objects along one or more axes.

The Clip View is where motion tracking lives.

Three solver stages: 2D feature tracking → camera intrinsics calibration (focal length, distortion) → camera/scene solving.

Main View

A Timeline appears at the bottom when a clip loads, spanning the animation range. Drag the Playhead (blue line) with LMB to navigate.

Visual indicators:
- Blue line: Playhead position
- Yellow: Motion track
- Yellow line: Keyframe
- Orange line: Shape keyframe
- Purple: Prefetched frames
- Light green line: Solve keyframe boundaries

### Introduction 

Particle trajectories allow extensive manipulation. The Physics panel settings govern particle-specific behavior. Additional trajectory control pathways include:

- Soft body simulation (Hair particle systems exclusively).

- External forces and curves.

- Lattice deformation.

### Common Physics Settings 

Size

Sets particle scale.

Random Size

Distributes particles with scale variance.

Mass

Specifies particle heaviness.

Multiply Mass with Particle Size

Scales mass proportionally with size.

### No Physics 

Particles receive zero motion control, remaining outside physics systems. Although stationary physics sounds counterintuitive, it serves valuable functions. None physics anchors particles to their emission source throughout existence. Initial velocity assignments apply when harmonic effectors cease influence, for instance.

Additionally, maintaining available particles (with both Unborn and Died visible during render) facilitates ecosystem construction and vegetation arrangement via Object or Group visualization modes.

### Introduction 

Hair-type particle systems model strand-like structures: hair, fur, grass, quills, and similar forms.

Particle hair systems example. Used for the grass and fur. 

### Growing 

Hair creation starts with specifying strand count and initial length.

Particle paths are pre-calculated in advance. Hair capabilities match particle capabilities: a hair's length corresponds to a particle's 100-frame lifetime path.
Rather than rendering each animation frame separately, control points with interpolated segments represent the path.

### Styling 

Hair appearance changes through styling adjustments. Base hair alterations use Physics Settings.

Advanced styling employs Children, adding supplementary strands with distinct shape properties.

Interactive hair sculpting occurs in Particle Edit Mode, where particle settings suspend and brushes enable combing, trimming, lengthening operations.

### Animating 

Hair becomes dynamic through the cloth solver, documented in the Hair Dynamics page.

### Rendering 

Cycles provides specialized hair BSDFs for rendering: Hair BSDF and Principled Hair BSDF.

Hair also serves as input for the Particle Instance Modifier, enabling mesh deformation along curves—useful for thick strands, grass, feathers, and similar structures requiring specialized appearance.

### Introduction 

Particles are numerous elements emitted from mesh surfaces, typically numbering in thousands.
Each can be a light source or mesh, linked or dynamic.
They respond to numerous forces and influences, with finite lifespans.
Dynamic particles simulate fire, smoke, mist, dust, magical effects, and similar phenomena.

Hair particles form curves representing hair, fur, grass, and bristles.

Particles appear as Particle Modifiers, though all configuration occurs in the Particle tab.

Example fur created from particles. 

Particles generally flow from emitting geometry into space.
Movement occurs through multiple influences:

- Initial velocity away from the mesh.

- Emitter movement (vertex, face, or object).

- Gravity or air resistance effects.

- Force field effects: wind, vortices, curve guides.

- Object interactions: collisions.

- Swarm intelligence where flock members interact while pursuing targets or avoiding threats.

- Soft-body physics-driven motion (Hair particle systems only).

- Lattice-based manual transformation.

Particle rendering modes include:

- Halos (for Flames, Smoke, Clouds).

- Meshes with animation (fish, bees, etc.); each particle carries another object.

- Hair curves following particle paths, editable in the 3D Viewport (combing, adding, cutting, moving, etc.).

Every object may host multiple particle systems. Each system supports up to 10,000,000 particles. Certain particle types (Hair and Keyed) permit up to 10,000 children per particle.
Memory and patience provide practical boundaries.

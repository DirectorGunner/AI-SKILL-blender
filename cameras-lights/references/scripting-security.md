# Scripting Security, Bendy Bones, Viewport Display, Camera Solver Constraint ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Scripting & Security; Bendy Bones; Viewport Display; Camera Solver Constraint; Object Solver Constraint; Follow Path Constraint; Locked Track Constraint; Copy Location Constraint; Lattice; Motion Paths.

## Scripting & Security

Scripting and security. Embedding Python in blend-files is valuable for advanced work like rigging and automation, but it's a security risk since Python doesn't limit what a script can do, so only run scripts from sources you trust. Automatic execution is off by default, though some blend-files need it; when a blend-file tries to run a script and isn't allowed, a dialog lets you Allow Execution or Ignore the scripts. Scripts in blend-files — auto execution happens via registered text-blocks (a text data-block with its Register option on loads at startup) and animation drivers (Python expressions that drive values, common in advanced rigs and animation). Manual execution: some scripts run only with user interaction, so they execute even with auto-execution off, but be aware they're not always obvious — running a script in the Text editor, or rendering with Freestyle (which uses scripts to control line styles). Controlling script execution: the File Browser has a Trusted Source option for case-by-case control of auto execution, and because you might forget it or open a file without the browser, you can change the default. Setting defaults: the Preferences "Auto Run Python Scripts" toggle makes Trusted Source on by default and lets scripts run when blend-files load outside the File Browser; once on, you can exclude certain directories, a typical setup being to trust every path except the download directory. Command line: for batch rendering or other UI-less tasks the Preferences still apply but can be overridden — enable with -y or --enable-autoexec, disable with -Y or --disable-autoexec. For example, to render an animation in background mode while allowing drivers and other scripts:
```text
blender --background --enable-autoexec my_movie.blend --render-anim
```
These arguments also work when starting a normal Blender instance and still override the Preferences.

## Bendy Bones

Bendy Bones (B-Bones) (All Modes; Bone ‣ Bendy Bones) are an easy replacement for long chains of small rigid bones, commonly used for spines or facial bones. Technically, Blender treats the bone as a section of a Bézier curve through the bone's joints, and each Segment bends and rolls to follow that invisible curve; the curve's end control points are the bone's endpoints, and its shape is set by a set of properties or indirectly by neighboring bones (first child and parent), which build handles at each end to control curvature. When the bone is a constraint target, its Data ID offers an option to follow the curvature — though when it serves as a target instead of deforming geometry, only the Armature and Copy Transforms constraints use the full transformation including roll and scale. Display: the segments only show when bones are visualized as B-Bones; otherwise bones draw as rigid sticks while the segments stay present and effective, so even in, say, Octahedron view a multi-segment chain still deforms its geometry smoothly. Rest pose: a B-Bone's initial shape can be set in Edit Mode as the bone's rest pose (useful for curved eyebrows or mouths), and B-Bones keep two sets of Bendy Bone properties — one for Edit Mode (the rest pose / base rig) and one for Pose Mode — adding or multiplying them for the final transform. Options: Segments is how many segments the bone is subdivided into — small rigid linked child bones interpolating between root and tip — where higher values bend more smoothly but cost more to compute. Display Size X, Z set the visible thickness of the segments in B-Bones mode. Vertex Mapping weights vertices to the individual segments for deformation: Straight (a fast mapping suited to straight or gently curved rest poses) or Curved (slower, improving deformation for strongly curved rest poses, used selectively). Curve In/Out X, Y, Z shift the curve-handle positions within the plane lying perpendicular to the bone's primary (Y) axis, moving each handle per axis (XZ) to bend the curve. Roll In, Out interpolate the roll (twist about the main Y axis) per segment between the start and end values, applied as a rotational offset atop the handle bones' rotation; Inherit End Roll implicitly adds the Start Handle bone's Roll Out (the connected parent by default) to this bone's Roll In. Scale In/Out X, Y, Z adjust each segment's thickness on X and Z or add non-uniform Y spacing, interpolated per segment like Roll — and since all segments are uniformly scaled in Y to fit the curve length, only the ratio of Scale In Y to Scale Out Y matters. Ease In, Out change the length of the "auto" Bézier handle controlling the root and tip handles respectively, proportional to the default length (which varies with bone length, angle to the reference handle, and so on); although easing is scale-like, the Edit- and Pose-Mode values are added, giving default start values of 1 and 0. Scale Easing, if on, implicitly multiplies the final easing values by the matching Scale Y values. Custom handles: B-Bones can use custom bones as reference handles instead of only the connected parent/child. Start/End Handle picks the handle type — Automatic (the connected parent, or first connected child, is the handle, computed as Absolute below), Absolute (the Bézier handle is driven by the handle bone's head/tail position relative to this bone's head/tail, requiring a nonzero distance between them, with extra smoothing applied if the handle is itself a B-Bone in a chain), or Relative.

Relative: the Bézier handle is driven by the offset of the handle bone's head/tail from its rest pose (best avoided, since values near a zero offset cause numerical-stability problems). Tangent: the handle is driven by the handle bone's orientation, independent of its location. Custom Handle: for any type other than Automatic you must pick a bone as the handle, and switching to a custom type without choosing a bone effectively disables that handle; two bones may legitimately reference each other as handles, which is applied in connected chains using Automatic handles. Scale X/Y/Z/Ease, when enabled, multiply the final Scale and/or Ease values by the matching local-scale channels of the handle bone — applied independently of Scale Easing and not interacting with it (so enabling Y plus Scale Easing doesn't replace the Ease toggle); these toggles efficiently stand in for as many as eight trivial drivers that would otherwise feed segment-scale data from the handle bones into the B-Bone properties. The "BBone Shape" Keying Set covers all Bendy Bone properties.

## Viewport Display

Viewport Display (Object, Pose, and Edit Mode; Bone ‣ Viewport Display) customizes how bones look. General: Hide hides the bone in the 3D Viewport (unchecked, visibility follows its bone collections); Display As sets how the selected bones appear, overriding the armature's Display Type — Armature Defined (use the armature's mode), Octahedral (octahedral shape), Stick (simple 2D lines with dots), B-Bone (boxes showing subdivision and B-Splines), Envelope (extruded spheres showing influence volume), or Wire (thin wires showing subdivision and B-Splines). Bone colors: bones can be colored individually, choosing a predefined theme color set or a custom one (Custom Color Set needs three colors — Regular for unselected, Selected, and Active), and you can temporarily disable all color assignments by unchecking Bone Colors in the armature's Viewport Display panel. Bone Color is the bone's primary color for Edit and Pose Mode, stored on the armature data-block so objects sharing it use the same color; Copy Bone Color to Selected copies the active bone's color to the selection. Pose Bone Color (Pose Mode) optionally overrides Bone Color in Pose Mode (set it to something other than Default Colors), stored on the Pose Bone so it can differ per armature object even when they share a data-block, with its own Copy Bone Color to Selected. Custom shape: bones can also take a custom shape (in Object and Pose Mode) using another object as a template, disableable by unchecking Shapes in the armature's Viewport Display panel. Custom Object is the shape-defining object; Translation/Rotation/Scale X, Y, Z add extra transform to the shape; Override Transform names a bone whose location and orientation the shape is placed at (visual only, not changing this bone's transform values); Affect Gizmo makes that Override Transform bone's location/orientation drive transform gizmos and operators; Use As Pivot transforms the bone as though it were a child of the Override Transform bone (useful when the mesh is deformed away from the bind pose by another mechanism such as Shape Keys, though it affects gizmo interaction only, not the bone's transform values or interpolation); Scale to Bone Length scales the shape by the bone's length; Wireframe always draws the bone as wireframe regardless of viewport shading; and Wire Width sets that wireframe's line thickness. Note that custom shapes never render (visible only in the 3D Viewport), the template object's own transforms are ignored, each instanced shape's origin is at the bone's root with its Y axis along the bone's direction, and for best results with Scale to Bone Length the template should be 1 unit along its Y axis so it matches each bone.

### Viewport Display

Thickness
Grid display thickness scale.

Interpolation
Grid visualization interpolation.

Linear :

Linear between voxels. Good smoothness/speed.

Cubic :

Cubic between voxels. High quality, slower.

Closest :

No interpolation. Raw voxels.

Slice per Voxel
Slices generated per voxel.

### Slice

2D domain section rendering.

Axis

Auto :

Slice follows view.

X/Y/Z :

X/Y/Z-axis slices.

Position
Slice relative placement (domain-side fraction).

Gridlines Closest Interpolation Only
Underlying-cell differentiation gridlines in current slice.

### Grid Display

Uses a color scheme for simulation field visualization, handy for debugging or advanced tweaking. Barely-visible fire? Try a different color profile.

Field
Display field (density, fuel, heat).

| "Fire" grid without color mapping.  | "Fire" grid with color mapping.  |

Scale
Displayed field scaling.

### Vector Display

Vector field visualization options.

Display As

Streamlines :

Vector "Streamlines" display.

Needle :

Vector "Needles" display.

MAC Grid :

"Marker-And-Cell Grid" display.

Mac Grid X, Y, Z Mac Grid
Distinct X/Y/Z MAC grid component view.

Magnitude Streamlines or Needle Only
Vector display scaling by magnitude.

Field
Vector field representation (fluid velocity, external forces).

Scale
Vector size in viewport.

### Advanced Gridlines Only

Gridline coloring choices.

Color Gridlines

Flags :

Flag-based coloring.

Highlight Range :

Grid Display Only
Highlight cells within the value range. Lower and Upper Bounds define inclusion.

Lower Bound
Range floor.

Upper Bound
Range ceiling.

Color
Highlight color.

Cell Type
Highlight specific cell category.

### Viewport Display 

Reference

Panel :

Particle System ‣ Display

Rendered

Presents hair as curves.

Path

Presents the hair terminal points alone.

Steps

Tallies the segments (control point count less one) composing a hair segment. Segment interpolation bridges control points. Control point quantity matters:

- For soft body animation, control points simulate like mesh nodes, so elevated counts increase computation duration.

- For interactive editing, only control points move (though Particle Edit Mode permits control point count adjustment).

Hint

Segments

Ten Segments adequately covers extended hair. Five Segments suit shorter lengths. Two or three Segments suffice for fur.

## Camera Solver Constraint

The Camera Solver constraint makes a Blender camera mimic a real-world camera's motion. Usage: load a video into the Movie Clip Editor and motion-track at least eight markers in the real scene, run Solve Camera/Object Motion to reconstruct the physical camera's motion, then add this constraint to a Blender camera. Options: Active Clip (follow the scene's Active Clip's physical camera; unchecked, a selector appears for another clip); Constraint to F-Curve (replace the constraint with equivalent keyframes); and Influence (how strongly it affects the camera).

## Object Solver Constraint

The Object Solver constraint makes a Blender object mimic a real-world object's motion. Usage: load a video into the Movie Clip Editor, register the physical object in the Objects panel, motion-track at least eight markers on it, run Solve Camera/Object Motion to reconstruct its motion, then add this constraint to a Blender object. Options: Active Clip (whether the object is in the scene's Active Clip; unchecked, choose another); Object (the physical object to imitate — set up in the Movie Clip Editor's Sidebar Objects panel); Camera (the Blender camera matching the recording camera; empty uses the active one — and if the physical camera moved, the Blender camera should have a Camera Solver Constraint, which is useful even for a stationary camera since it puts the tracking markers at their reconstructed world positions in the viewport when the Motion Tracking overlay is on); Set Inverse (tell the constraint that the Blender object's current Location with the constraint disabled is correct for the current frame, after which it'll be correct on other frames too — when first adding it: position the object for the current frame, add the constraint, click Set Inverse; when later tweaking: run Apply Visual Transform, disable the constraint, tweak the position, click Set Inverse, re-enable); Clear Inverse (reset the relative transform Set Inverse stored); Constraint to F-Curve (replace with keyframes); and Influence.

## Follow Path Constraint

The Follow Path constraint places an object or bone on a Curve, with the position set either by a frame number (the Curve's Evaluation Time plus an optional constraint Offset) or by a number from 0 to 1 (the constraint's Offset Factor); animating these moves it along the Curve, and it can also rotate to match the Curve's direction — useful for cameras on rails, vehicles on roads, boxes on conveyors, and so on. For a quick setup, select the object, add the Curve, press Ctrl-P, and click Path Constraint. (It can combine with a tracking constraint to, say, keep a moving camera aimed at an object; the Clamp To Constraint instead snaps an object to a Curve by its location.) Position offsetting: the constraint uses the owner's World-Space position and rotation as offsets to the position and rotation on the Curve — with Follow Curve off, offsets are added in the Curve's Local Space; with it on, in the space of the current curve point, the global Y axis being the tangent direction — and in both cases the Curve's scale multiplies the position offset. For a perfectly positioned, aligned owner, make its world position and rotation zero (Alt-G and Alt-R). Options: Target (the Curve to follow); Offset (Fixed Position off — frames subtracted from the Curve's Evaluation Time, positive moving the owner earlier on the Curve, negative later); Offset Factor (Fixed Position on — relative position along the Curve independent of Evaluation Time, 0 the start and 1 the end); Forward Axis (the owner's local axis aligned to the Curve's tangent, needs Follow Curve on, a negative axis pointing the opposite way); Up Axis (the owner's local axis aligned as much as possible to global Z, needs Follow Curve on) — and Forward and Up must differ, or the constraint stops and its icon turns red; Fixed Position (ignore Evaluation Time and position by Offset Factor alone, though the owner can still move over time by animating Offset Factor); Curve Radius (scale the owner by the Curve's control-point radii); Follow Curve (rotate the owner by Forward and Up Axis); Animate Path (animate the Curve's Evaluation Time to always equal the current scene frame, though you can also animate it by hand); and Influence.

## Locked Track Constraint

The Locked Track constraint points an object or bone toward a target — often "Look At" or "Aim" elsewhere — where "locked" means it rotates around only one axis, that axis keeping its orientation while the other two stay in their original plane. Use cases include distant tree billboards that turn to face the camera while staying upright, or a compass needle that spins horizontally toward a magnet but never points up or down. (It can combine with other Track constraints — e.g. first a Damped Track to orient the X/Y plane toward one target, then a Locked Track to rotate within that plane toward another.) Options: Target (the object or bone to point at); Track Axis (the owner's local axis that should point at the target, typically Y for bones, a negative axis pointing away); Locked Axis (the owner's local axis that keeps its orientation — the only axis it can rotate around) — and Track Axis and Locked Axis must differ, or the constraint stops and its icon turns red; and Influence.

## Copy Location Constraint

The Copy Location constraint forces an object or bone to match a target's location. Note it has no effect on connected bones, whose position is set by their parent. Options: Target (the object or bone whose location to copy); Axis (which axes to copy); Invert (which axes to flip the sign of, so 10 becomes -10 and vice versa); Offset (when on, the target's current position is added to the owner's original position from preceding constraints rather than copied over); Target/Owner (the spaces for reading from the target and applying to the owner); and Influence. Examples: a video shows the Head/Tail effect when targeting a bone and the Vertex Group effect when targeting a mesh; and a solar-system animation has a camera follow the moon orbiting Earth, then Earth orbiting the Sun, then a fixed view of the Sun — done with two Copy Location constraints (one per body) whose Influence values are animated to smoothly hand off from one to the other.

## Lattice

A Lattice — often called a deformation cage outside Blender — is a non-renderable 3D grid of vertices whose main use is deforming the object it controls via a Lattice Modifier (parenting with Lattice Deform applies one automatically). Editing: Flip (Distortion Free) mirrors the vertices' displacement from their base position along U, V, or W; Make Regular resets the whole lattice to a regular grid with cells scaled to one cubic unit. Properties — Lattice (a data-block menu): Points sets the subdivision rate on each of U, V, W; Interpolation Type is a per-axis selector (Linear, Cardinal, Catmull-Rom, B-Spline); Outside considers only the lattice's surface vertices; and Vertex Group assigns the influence strength as a weight to the chosen vertex group's vertices. Usage: scale and move the lattice to fit around your object in Object Mode — any scaling applied in Edit Mode deforms the object, including applying its scale with Ctrl-A, which has the same effect as scaling the lattice in Edit Mode (and thus the object).

## Motion Paths

Motion Paths (3D Viewport, Properties; Object Mode at Properties ‣ Object Properties ‣ Motion Paths, or Pose Mode at Properties ‣ Armature ‣ Motion Paths and Pose ‣ Motion Paths) visualizes the motion of points — object origins and bone joints — as paths across a range of frames. To create or remove them, first select the bones, then click Calculate Path to show or update them, or Clear Paths to hide them (only selected bones and their paths are affected). The past section draws red and the future section green (following the "Before Current Frame" and "After Current Frame" preferences in the 3D Viewport section), with a small dot per frame; paths update automatically as you edit poses/keyframes and stay active during playback, though playing only affects them with the Around Frame type. Options: Paths Type — Around Frame (paths within a fixed number of frames before and after the current one) or In Range (paths within a specified range); Calculation Range (active only with In Range, taking effect on update via Update Path/Update All Paths) — All Keys (first to last keyframe, only the active object/bone's keys), Selected Keys (first to last selected keyframe), Scene Frame Range (the scene's start/end, or the preview range if active), or Manual Range (set start and end by hand); Frame Range Start, End (the displayed/calculated range, not for Around Frame — always editable but reset on update per Calculation Range, so choose Manual Range to keep your range); Frame Range Before, After (frames before and after the current one, only for Around Frame); Step (show one point every n frames, useful with frame-number display to reduce clutter); Bake to Active Camera (calculate the path in screen space for the active scene camera, useful only for that camera, with no marker-based camera switching — it bakes to whichever camera was active when the bake began); Cache/Bone Cache From, To (the start/end frames the paths show, not changeable without deleting the path first); Calculate (Calculate Paths makes a new cached path from the options in the pop-up or Adjust Last Operation panel — and for an armature calculating object paths rather than bone paths, it also calculates all the armature's bone paths); Start, End (the shown range's start/end, the start being inclusive); Bake Location (which bone point is used — Heads or Tails — bones only, in Pose Mode); Update Paths (update an existing path's shape to the current animation — change its frame range by deleting and recalculating); Clear Paths (clear paths on all objects/bones, or just the selected ones with Shift); and Update All Paths (recalculate for all visible objects and poses). Display: Frame Numbers (a small number by each frame dot); Keyframes (big yellow squares on paths at keyed bones' keyframes); + Non-Grouped Keyframes (for bone paths, search the whole Action for keyframes rather than name-matched groups — slower); Keyframe Numbers (the displayed keyframes' numbers, valid only with Keyframes on); Lines (toggle the lines between points); Thickness (the path's line thickness); and Custom Color (a custom color, separately settable for before and after the current frame).

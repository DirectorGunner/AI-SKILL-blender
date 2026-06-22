# Selecting Curve Elements, Propagate To Shapes, Select Random, Cast Modifier ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Selecting Curve Elements; Propagate to Shapes; Select Random; Cast Modifier; Mesh Deform Modifier; Warp Modifier; Wave Modifier; Remesh Modifier; Mesh Cache Modifier; Mesh Sequence Cache Modifier; Collision Modifier.

## Selecting Curve Elements

This section covers curve-specific selection in Edit Mode.
The Curve Edit Mode also uses general select tools described
in the interface section.

Curve selection has fewer options than meshes.
Mainly because there's one selectable type: control points
(no select mode needed). These are more complex than simple vertices,
especially for Bézier curves, with central vertex and two handles.

Basic tools match meshes:
select a point with LMB ,
add with Shift - LMB , Box Select B , and so on.

For Bézier points: selecting the main vertex auto-selects both handles, moving the whole point
without creating angles. Selecting a handle alone changes just that vector.

Note: unlike mesh edges, segments can't be directly selected. Select all points making up the segment instead.

Select Menu:

All advanced selection options for curves
appear in the 3D Viewport header's Select menu.

All:

Reference

Mode :

Edit Mode

Menu :

Select ‣ All

Shortcut :

A

Activate all selectable elements.

None:

Reference

Mode :

Edit Mode

Menu :

Select ‣ None

Shortcut :

Alt - A

Deselect all, but the active element remains.

Invert:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Invert

Shortcut :

Ctrl - I

Choose all unselected geometry and deselect current components.

Box Select:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Box Select

Shortcut :

B

Interactive box selection.

Circle Select:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Circle Select

Shortcut :

C

Interactive circle selection.

Lasso Select:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Lasso Select

Shortcut :

Ctrl - Alt - LMB

See Select Lasso.

Select Random:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Random

Activate control points randomly.

Percent
Choose the percentage of control points to activate.

Random Seed
Seed for the pseudo-random generator.

Action
Decide whether to Select or Deselect points.

Checker Deselect:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Checker Deselect

Create an alternating selected/deselected checker pattern.
Works only with multiple already-selected points.

Modifies the selection so every Nth
point stays selected, starting from the active one.

Deselected
Deselected count in each pattern unit.

Selected
Selected count in each pattern unit.

Offset
Starting point offset.

Select More/Less:

Reference

Mode :

Edit Mode

Menu :

Select ‣ More/Less

Shortcut :

Ctrl - NumpadPlus , Ctrl - NumpadMinus

Based on current selection, shrink or expand it.

More
For each chosen point, activate its linked points (one or two).

Less
For each chosen point, if all linked points are active, keep it chosen.
Otherwise, deselect it.

Two consequences:

- When all points are chosen, nothing occurs
(all linked points are already active, and More can't add). Same for no selection.

- These tools stay within a curve
(they don't jump to another curve in the object).

Select Linked:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked

Shortcut :

Ctrl - L

Activate all points connected to the active one.

Makes it easier to select or deselect whole curve sections, especially in
dense curves, where manual point selection takes time.

Select Linked Pick:

Reference

Mode :

Edit Mode

Hotkeys :

L , Shift - L

Select ( L ) or deselect ( Shift - L ) points
connected to the point nearest the cursor.

Note

For Bézier curves with a handle active,
this operator activates the whole point and all linked ones.

Select Similar:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Similar

Shortcut :

Shift - G

Choose points with properties matching the active one.
The Adjust Last Operation panel shows several choices:

Type

Type
Activate splines of the same spline Type (Bézier, NURBS, or Poly).

Radius
Activate points with similar Radius value.

Weight
Activate all points with similar Weight value.

Direction
Activate points with similar handle direction.

Compare
For numerical properties, choose the comparison type between values.

Equal :

Choose items with matching property value as the active item.

Greater :

Choose items with larger property value as the active item.

Less :

Choose items with smaller property value as the active item.

Threshold
For numerical properties, control how
close property values must be for comparison.

(De)select First/Last:

Reference

Mode :

Edit Mode

Menu :

Select ‣ (De)select First ,
Select ‣ (De)select Last

Toggle the active status of the first or last point(s).
Handy to quickly locate the curve start
(e.g. when using it as path…).

Select Next/Previous:

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Next , Select ‣ Select Previous

Choose the next or prior point(s),
based on the current selection
(points following or preceding chosen ones along the curve).
With a cyclic curve, first and last points are not neighbors.

Pick Shortest Path:

Reference

Mode :

Edit Mode

Menu :

Menu Search ‣ Pick Shortest Path

Shortcut :

Ctrl - LMB

Choose the curve segments between two points: the active and the one below the cursor.
For closed curves, the shortest path activates.

Hair curves, though similar to standard curves, have their own selection mechanics. Many tools parallel regular curve operations but use different underlying implementations. All selection operations for hair are documented here.

Both Sculpt and Edit modes support these selection operators.

Reference

Mode: Edit Mode
Menu: 3D Viewport Header ‣ Select Mode
Shortcut: 1 , 2

Hair Curves only.

Selection modes restrict operators to particular domains, allowing easy bulk selection or fine-grained control.

Control Points: Select individual control points.
Curve: Restrict selection to whole curve segments.

Reference

Mode: Edit Mode
Menu: Select ‣ All
Shortcut: A

Activate all selectable items.

Reference

Mode: Edit Mode
Menu: Select ‣ None
Shortcut: Alt+A

Clear the current selection while keeping the active element unchanged.

Reference

Mode: Edit Mode
Menu: Select ‣ Invert
Shortcut: Ctrl+I

Toggle selection: deselect what is chosen and choose what is deselected.

Reference

Mode: Edit Mode
Menu: Select ‣ Select Random

Pick a random subset based on seed and probability.

Seed: Pseudo-random sequence starter.
Probability: The percentage of control points to include.

Reference

Mode: Edit Mode
Menu: Select ‣ More/Less
Shortcut: Ctrl+NumpadPlus , Ctrl+NumpadMinus

Expand or contract selection based on connectivity.

More: For each selected point, add all its neighbors (typically one or two adjacent points).
Less: Keep a selected point only if all its neighbors are also selected.

Two consequences follow:
- If all points in a curve are chosen, More adds nothing. Conversely, Less leaves everything unchanged.
- These never "jump" to a neighboring curve—expansion stays within the current curve boundary.

Reference

Mode: Edit Mode
Menu: Select ‣ Select Linked
Shortcut: Ctrl+L

Extend selection to all points reachable from the active point along the curve path. This is especially valuable in dense curves, where point-by-point selection would be tedious.

Reference

Mode: Edit Mode
Hotkeys: L , Shift+L

Activate selection ( L ) or deactivate it ( Shift+L ) for points adjacent to the cursor position.

Note: When a Bézier handle is selected, the entire point and its chain are selected.

Reference

Mode: Edit Mode
Menu: Select ‣ Select Endpoints

Activate only the start and end points of curve segments. Only available in Control Point selection mode.

## Propagate to Shapes

### Propagate to Shapes

Reference

Mode:

Edit Mode

Menu:

Vertex → Propagate to Shapes

Transfers current positions of chosen vertices to all other shape keys.
This spreads edits made in Edit Mode uniformly across every shape key.

Beneficial for:

- Fixing vertex positions that match across shape keys.

- Correcting topology issues or small modeling flaws without touching each shape key individually.

- Maintaining consistent base form through shape key variations.

Warning

- This overwrites affected vertex positions in all shape keys.
Use caution if certain shape keys need special deformations for those vertices.

- Structural corrections that must be consistent (e.g. raising an eyelid edge loop in all expressions) work best.

## Select Random

### Select Random

Reference

Mode :

Object Mode and Edit Mode

Menu :

Select ‣ Select Random

Adds random items to the selection.

### Options

Ratio
The ratio of items that should end up selected, e.g. 0.5 to select half of all items (that are not hidden).

Whatever is already selected gets ignored. So if half the items are selected and you set Ratio to 0.1, nothing is deselected, nor does it pick 10% of the unselected items; it always grabs 10% of every visible item and adds them on.

Random Seed
A number steering exactly which items come up.

Action

Select :

Throw random items into the selection.

Deselect :

Pull random items out of the selection.

## Cast Modifier

The Cast modifier deforms meshes, curves, surfaces, or lattices toward a predefined shape—sphere, cylinder, or cuboid. It is equivalent to the To Sphere tool in Edit Mode, though supporting multiple target shapes.

Pairing Cast with the Smooth modifier improves visual quality, as cast shapes sometimes benefit from smoothing to resolve distortions.

The modifier operates in local space only. Incorrect results may indicate that the object's transformations need application, particularly when casting to cylinders.

Shape selects the target: Sphere, Cylinder, or Cuboid.

Axis toggles the effect along X, Y, Z axes (only X and Y for Cylinder, as Z is unaffected).

Factor controls the blend between original and cast positions. At 0.0, no change occurs; at 1.0, full casting applies. Values outside the 0.0–1.0 range exaggerate results in sometimes interesting ways.

Radius, if nonzero, restricts the effect to vertices inside a spherical zone. Outside vertices remain unaffected.

Size sets an alternative target shape size. When zero, the initial shape and control object (if present) determine it.

Size from Radius, when active, calculates Size from Radius for smoother transitions.

Vertex Group restricts the effect to a specific group, enabling selective, real-time casting via weight painting.

Invert reverses the group effect.

Object names a control object whose origin defines the projection center. Its scale and rotation also transform the cast vertices, allowing animation of the control object to animate casting deformation.

## Mesh Deform Modifier

The Mesh Deform modifier uses an arbitrary closed mesh as a deformation cage, allowing it to control another mesh's shape.

Setup is straightforward but binding computation can be slow.

Object specifies the cage mesh.

Vertex Group restricts deformation to group vertices; others remain unchanged.

Invert reverses the group influence.

Precision controls cage-to-deformed accuracy. Higher values increase binding calculation time but improve cage mapping accuracy.

This setting is unavailable after binding.

Dynamic, when enabled, factors other mesh-altering features (modifiers, shape keys) into binding for better deformation quality.

Dynamic is off by default to reduce memory and binding time. Unavailable after binding.

Bind connects the modified geometry's current vertices to the deforming cage.

An unbound Mesh Deform modifier has no effect; binding is necessary for the cage to alter the modified object.

Warning: depending on modifier settings and cage/object complexity, binding may take significant time, potentially freezing Blender. Save before proceeding; memory exhaustion and crashes are possible.

Unbind, after binding is complete, disassociates the modified object from its cage. The cage retains its current shape; it does not reset. The modified object reverts to its pre-binding shape.

To preserve the original cage form, save a copy before altering it.

Significant whole-cage transformations (like inversion) can introduce artifacts. Higher Precision reduces them but cannot eliminate them entirely—this is an inherent limitation.

Ensure cage mesh normals point outward (they determine inside/outside).

Additional faces inside the cage—loose or forming smaller cages—provide extra control. Smaller cages may overlap the main cage. For instance, small sphere cages around eyes enable fine eye deformation.

## Warp Modifier

The Warp modifier warps mesh portions to new locations flexibly, using two objects to specify "from" and "to" regions.

Understanding requires knowledge of two points from the target objects' origins. The "from" point designates a region drawn toward the "to" point, analogous to Proportional Editing in Edit Mode.

Object From specifies the origin transformation for the warp source.

Object To specifies the origin transformation for the warp destination.

Preserve Volume, when active, prevents volume loss when rotating the transforms.

Strength sets effect intensity.

Vertex Group controls influence per vertex. When empty, all vertices are equally affected.

Invert reverses the group influence.

Falloff Type controls how strength changes from the transform center to the Radius—see Proportional Editing for descriptions.

Radius sets how far from the transform centers the effect reaches.

Texture enables fine per-vertex control of which vertices warp and by how much (see common masking options for reference).

Warp is sometimes awkward to use and has limited application, but it serves a few cases. For instance, it enables interactive Proportional Editing suitable for animation. It also resembles the Deform Modifier, enabling mesh warping without vertex groups.

## Wave Modifier

The Wave modifier adds a ripple-like motion to an object's geometry. It is available for meshes, lattices, curves, surfaces, and texts.

Options:
Motion — the wave deforms vertices/control points in the Z direction, starting from the given point and propagating along the object with circular wave fronts (when both X and Y are enabled) or rectilinear wave fronts (when only one axis is enabled), then parallel to the axis of whichever X or Y button is active.
Cyclic — repeat the waves cyclically rather than as a single pulse.
Along Normals — meshes only: displace the mesh along the surface normals instead of the object's Z axis.
X/Y/Z — restrict displacement along normals to the selected local axes.
Falloff — how fast the waves fade out as they travel away from the coordinates above (or those of the Start Position Object).
Height — the height or amplitude of the ripple.
Width — half the width between the tops of two subsequent ripples (when Cyclic is enabled); this indirectly affects amplitude, since if the pulses are too near each other the wave may not reach the zero Z position, so Blender lowers the whole wave to make the minimum zero, leaving the maximum lower than the expected amplitude (see Technical Details and Hints).
Narrowness — the actual width of each pulse: the higher the value, the narrower the pulse. The width of the area in which a single pulse is apparent is 4 / Narrowness — so if Narrowness is 1 the pulse is 4 units wide, and if Narrowness is 4 the pulse is 1 unit wide.
Vertex Group — the name of a vertex group used to control the modifier's influence; left empty, the modifier affects all vertices equally.
Invert — invert the influence of the selected vertex group, so the group now represents vertices that will not be deformed; the setting reverses the group's weight values.
Important: all the values above are in local object space, so they must be multiplied by the object's corresponding Scale values to get the real dimensions.

Start Position:
Object — use another object as the reference for the wave's starting position; you can then animate that object's position to change the wave's origin over time.
Start Position X/Y — coordinates of the center of the waves, in the object's local space.

Time — settings to control the animation.
Offset — time offset in frames: the frame at which the wave begins (if Speed is positive) or ends (if Speed is negative); use a negative frame number to prime and pre-start the waves.
Life — duration of the animation in frames; set to zero to loop the animation forever.
Damping — an additional number of frames over which the wave slowly damps from the Height value to zero after Life is reached; the damping affects all ripples and begins on the first frame after Life is over, with ripples disappearing over Damping frames.
Speed — the speed of the ripple, per frame.

Texture — finely control which vertices the wave affects, and to what extent, using a texture (see the common masking options for a complete reference).

Technical Details and Hints: to get a nice wave effect similar to sea waves and close to a sinusoidal wave, make the distance between following ripples and the ripple width equal — that is, set Narrowness equal to 2 / Width (e.g. for Width to be 1, set Narrow to 2).

## Remesh Modifier

This modifier regenerates mesh topology, outputting only quads that follow input surface curvature.

Mode offers three variants differing in smoothing: Blocks applies none, Smooth creates a smooth surface, Sharp preserves sharp edges like Smooth but also respects input corners.

Sharpness controls edge fidelity; higher values match input geometry more closely, lower values filter noise.

Voxel mode uses OpenVDB to generate a manifold mesh preserving the original volume.

Adaptivity reduces final face count by simplifying geometry where detail is unnecessary, introducing triangulation for flat regions.

Octree Depth sets resolution; low values create larger faces, high values create denser output.

Scale further tweaks output resolution; lower values reduce resolution.

Smooth Shading applies smooth shading to output faces instead of flat, independent of input shading.

Remove Disconnected filters out small isolated pieces; thin mesh sections can fragment. Threshold controls what counts as too small.

Important: the input mesh should have some thickness; completely flat input benefits from a preceding Solidify Modifier.

## Mesh Cache Modifier

### Mesh Cache Modifier

The Mesh Cache modifier pulls animated mesh data out of an external file and feeds it to a mesh, letting the mesh deform across time. Its usual role is importing animation built in other software, delivering smooth playback of those cached deformations.

In behavior it sits close to shape keys, yet the modifier exists specifically to play back animation stored externally rather than deformations driven by keyframes.

Important

The .mdd and .pc2 formats both count on the vertex order holding steady across the whole animation.
Add, drop, or shuffle vertices downstream of this modifier and you may get results you didn't intend.

### Options

Mesh Cache Modifier.

Format
Names the input file format. For now the modifier handles .mdd and .pc2 .

File Path
Where the external cache file holding the animation data lives.

Influence
Sets how strong the deformation comes through. Drop it lower and the cached animation blends with the original mesh shape.

Deform Mode
Sets the way the cache data acts on the mesh:

Overwrite :

Swaps vertex positions out for the ones held in the cache file.

Integrate :

Folds the cache deformation in with deformations already present, like shape keys or modifiers.

Note

This mode suits small, localized tweaks best.
Sweeping changes, reposing limbs for instance, may not behave as you'd expect.

Interpolation
Sets how the frames sitting between cache data get handled:

None :

Draws on nothing but the raw cache frames, with no interpolation.

Linear :

Blends across frames for smoother transitions, handy when cache frames don't line up exactly with the scene
frames.

Vertex Group
When given, limits the effect to just the vertices held in that vertex group.

Invert
Flips which vertices the chosen vertex group covers, so the group instead
marks the vertices the modifier will leave undeformed.

The group's weight values are reversed by this setting.

### Time Remapping

Time Mode
Sets how animation time gets read:

Frame :

Disregards the cache's timing data and runs the frames straight through.
This gives you direct say over playback speed.

Time :

Draws on the cache's own timing data, offsets and frame durations included.

Factor :

Fits the whole animation into a 0-to-1 range for fine control.

Play Mode
Sets how playback timing is worked out:

Scene :

Plays back against the scene's current frame.

Frame Start
Sets which frame playback begins on.

Frame Scale
Speeds up or slows down playback by scaling time.

Custom :

Allows manual control of animation timing.

Evaluation Value
Fixes where playback sits in the animation, and can be animated for fine control.

### Axis Mapping

Forward/Up Axis
Names the forward and up axes of the imported animation so it's oriented properly.

Flip Axis
Mirrors the animation across a chosen axis when the imported data needs correcting.

## Mesh Sequence Cache Modifier

### Mesh Sequence Cache Modifier

Data from Alembic and USD files is what the Mesh Sequence Cache modifier reads in. It will take static meshes, but loading animated ones is its principal purpose. Its name aside, the modifier copes with curves too, and it deals with file sequences as well as with meshes and curves whose topology shifts (the output of fluid simulations, for example).

Bring in an Alembic or USD file and Mesh Sequence Cache modifiers attach themselves automatically to any time-varying meshes. Where it's the object transform that varies over time (animated rotation, location, or scale), the Transform Cache Constraint takes care of that instead. Anything that isn't Alembic or USD, MDD and PC2 among them, comes in through the Mesh Cache modifier instead.

### Options

Cache File
Data-block menu for picking the Alembic or USD file.

File Path
Where the Alembic or USD file is located.

Object Path
The route to the Alembic or USD object held inside the archive or stage.

Read Data
Sets which mesh data is brought in from the cache file.
You can switch each of the following on or off as you like:

Vertices :

Reads vertex positions and (if animated) deformations for each frame.

Faces :

Brings in the mesh's face topology and structure.

UV :

Pulls UVs (texture coordinates) out of the cache file.

Color :

Brings in vertex color attributes from the cache file when they're present.

Attributes :

Pulls in custom attributes (creases, custom normals, or generic attributes, for example).

### Time

Sequence
Whether the cache is split across a run of files or not.

Override Frame
Whether a custom frame is used to look up data in the cache file
in place of the current scene frame.

The Frame value is the time used to look up data in the cache file,
or to settle which file to use in a sequence.

Frame Offset
Taken off the current frame when looking up data in the cache file,
or when settling which file to use in a sequence.

### Velocity

Velocity Attribute
Names the Alembic attribute that feeds motion blur generation;
this defaults to .velocities , the standard across most Alembic files.

Note

For now, Velocity Attribute applies to Alembic files alone.

Velocity Unit
Sets how the velocity vectors are read with respect to time.

Frame :

The velocity unit was set in frames, so no scaling by scene FPS is needed.

Second :

The velocity unit was encoded in seconds, so the scene FPS (1 / FPS) has to scale it.

Note

At present, Velocity Unit works with Alembic files only.

Velocity Scale
A multiplier for dialing the velocity vector's magnitude up or down, feeding time effects like motion blur.

Note

Right now, Velocity Scale is limited to Alembic files.

## Collision Modifier

### Collision Modifier

Think of the Collision modifier as a wrapper around a Collision Physics. Collision physics are what let separate physics simulations interact with each other.

### Options

A wrapper and nothing more, this modifier puts its working settings on the Physics Properties tab instead.
Full detail lives on the Collision Physics Properties page.

### Example

Deflected particles.

Shown here is a Meta object that uses Instancing Vertices onto a downward-emitting particle system,
with a mesh cube doing the deflecting.

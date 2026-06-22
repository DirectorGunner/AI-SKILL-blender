# Viewport Display, Common, Geometry Attribute Constraint, Drivers Panel

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Viewport Display; Common; Geometry Attribute Constraint; Drivers Panel.

## Viewport Display

Viewport Display (All Modes; Armature ‣ Viewport Display). Display As sets how all the armature's bones appear (individual bones can override this via their Display Type): Octahedral (the default, good for most editing — it shows the root (big joint) and tip (small joint), the bone's size since thickness is proportional to length, and the roll via its square section); Stick (the simplest, least intrusive — constant thin sticks giving no info on root/tip, size, or roll); B-Bone (the curves of smooth multi-segmented bones; see Bendy Bones); Envelope (the bone's deformation influence; see the bone page); and Wire (also shows the curves of smooth multi-segmented bones). Show: Names (display each bone's name); Shapes (in Object and Pose Mode, replace the default bone shape with a chosen object's; see Shaped Bones); Bone Colors (draw bones in their configured colors — disable to always use the default; see Bone Colors); In Front (always draw the armature on top of solid objects so it stays visible and selectable, the same option as in the Object data tab's Display panel, handy outside Wireframe mode); Axis (show each bone's local axes, relevant only in Edit and Pose Mode); Position (where the axes display sits along the bone — higher moves toward the tip, lower toward the root); and Relations (whether the Relationship Lines overlay draws from each parent's tail or head, the lines always going to the children's heads).

### Viewport Display 

Reference

Panel :

Particle System ‣ Viewport Display

The Display Panel governs how particles render in the 3D Viewport. Viewport appearance does not necessarily dictate final rendering results.

Display As

None
Particles vanish from the 3D Viewport and do not render. The emitter object may still render.

Rendered
Particles appear as they will render.

Point
Particles appear as square dots. Scaling stays independent from camera distance.

Circle
Particles appear as view-facing circles. Scaling remains independent from camera proximity.

Cross
Particles appear as 6-point crosses oriented to particle rotation. Scaling remains independent from camera distance.

Axis
Particles display as 3-point axis markers. Reveals orientation and rotation information within the viewport. Increase Display Size for clear axis visualization.

Note

Point, Circle, Cross, and Axis modes lack specialized options but prove valuable when multiple particle systems operate simultaneously, particularly for Boids physics simulations where distinguishing particle system membership becomes important.

Color

The Color Menu specifies particle coloration by chosen properties.

None
Particles render in black.

Material
Particles take coloration from their assigned material.

Velocity
Particles color-code by speed. A blue-to-green-to-red gradient represents velocity; blue indicates slowest movement, red indicates velocities matching or exceeding Max. Increase Max for wider velocity range visualization.

Acceleration

Particles color according to acceleration magnitude.

Amount

Specifies the viewport particle display percentage (all particles still render).

Show Emitter

Toggles emitter object visibility in the viewport.

### Viewport Display

Workbench does not use shader networks. The Viewport Display panels in various Properties tabs hold the settings that Workbench applies for shading.

### Object

The Object Properties Viewport Display panel contains settings for the Workbench Engine.

Reference

Panel :

Properties ‣ Object ‣ Viewport Display

Shadow
When Shadow is enabled in Options, this object will cast a shadow.

In Front
Renders the object ahead of other scene objects.

Color
The color for rendering the object. The alpha channel controls transparency.

### Material

The Material Properties Viewport Display panel contains settings for the Workbench Engine.

Reference

Panel :

Properties ‣ Material ‣ Viewport Display

Color
The color for rendering the material. The alpha channel controls transparency.

Metallic
Adjusts the intensity of specular lighting, available only when Specular Lighting is active in Options.

Roughness
Adjusts the amount of roughness applied to specular lighting, available only when Specular Lighting is active in Options.

### World

The World Properties Viewport Display panel contains settings for the Workbench Engine.

Reference

Panel :

Properties ‣ World ‣ Viewport Display

Color
The color of the world background rendered in the scene.

### Viewport Display

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Viewport Display

This panel lets you configure display options for the 3D Viewport.

Viewport Display panel.

Show

Name
Displays the object's name in the 3D Viewport.

Axes
Displays an object similar to an empty that shows the object's orientation.

Wireframe
Displays the object's wireframe on top of the solid display.

All Edges
Displays all wireframe edges. This overrides the wireframe threshold that you can set in the 3D Viewport's overlay settings.

Texture Space
Displays the object's Texture Space in the 3D Viewport. The texture space overlay can be disabled for all objects using the Extras Overlay.

Shadow
Allows the object to cast shadows in the viewport.

In Front
Makes the object display in front of others. Unsupported for instanced objects. Limited support in the Material Preview and Rendered shading modes (works for e.g. armatures, but not for meshes).

Display As
Lets you display the object with less detail, going from removing the textures to only showing a bounding box. This can be useful if you have a high-poly object that is slowing down the viewport.

Color
The object's color in the Wireframe and Solid viewport shading modes. Used when the viewport's (Wire) Color shading option is set to Object .

Bounds
Displays a bounding shape around an object. You can choose between different primitive shapes that might be closer to what the original object looks like.

## Common

Common constraint settings. Target: the object a constraint refers to — for instance, Copy Location copies the target's location to the constrained object. A target starts empty with a red icon (inactive); once set, the icon turns gray and the constraint works. By default the target's Origin location is used, but for a Mesh or Lattice target you can pick a Vertex Group (using the weighted average of those vertices' positions), and for an Armature target you can pick a Bone and an interpolated point somewhere between its Head and Tail, with a button to track a Bendy Bone's curved shape. Space: the Target Space is the frame of reference for reading the target's location, rotation, and scale, while the Owner Space is the frame for applying those to the constraint's owner; using World Space for both places the owner at the target regardless of parents. Space types — World Space (relative to the world axes); Custom Space (relative to an arbitrary object or bone); Pose Space, bones only (relative to the armature object); Local Space (for an object, relative to its parent; for a bone, relative to its rest state once that rest state has been transformed by the bone's ancestors — i.e., with no other constraints, the bone's transform as shown in the Properties Editor in Pose Mode), with a warning that for parentless objects Local Space has a special, backwards-compatible meaning that may be removed, so use World Space instead; Local with Parent, bones only (relative to the bone's rest state, but unlike Local Space including the rotation and location difference from rotating any ancestor); and Local Space (Owner Orientation), bone targets only (meant for an Owner set to Local Space — it reads the target bone's Local Space adjusted to the owner bone's rest orientation, so when both bones' parents are at rest the owner undergoes the same transform as the target in armature space; initially like Pose or World Space, but differing once the parent bones are rotated too — illustrated by three armatures: a manually rotated Target bone, a middle bone copying its Local Space rotation around its own Y, and a right bone copying Local Space (Owner Orientation) so it rotates around that same axis in armature space). Influence: a strength multiplier — 1 (the default) fully applies the constraint (e.g. Copy Location wholly overrides the location), 0 is like disabling or deleting it, and a value between gives an interpolated result (0.5 places the object halfway between its previous location and the target's); Influence can be keyframed to turn constraints on and off during an animation. Disable and Keep Transform applies the constraint's result to the owner's own transform but, rather than deleting the constraint, disables it by setting Influence to 0 (and, like applying, may not work perfectly if the constraint isn't first in the stack).

## Geometry Attribute Constraint

The Geometry Attribute constraint transforms an object or bone from a target object's sampled geometry-attribute data, so motion and deformation can be driven directly by procedural geometry outputs such as Geometry Nodes positions or orientations. Options: Target (the object to read geometry from — Mesh, Curve, Point Cloud, or Instance); Offset with Target Transform (apply the target's world transform atop the attribute's); Attribute Name (the sampled attribute, default "position"); Data Type (which components drive the transform) — Vector (affects location), Quaternion (affects rotation), or 4x4 Matrix (affects the whole transform, with Location/Rotation/Scale toggleable separately but removing matrix shearing); Domain — Point (Mesh, Curve, or Point Cloud), Edge or Face or Face Corner (Mesh), Spline (Curve), or Instance; Sample Index (which geometry element to sample, clamped to what's present); Mix Mode, combining the copied and existing transforms — Replace, Before Original (Full) (simple matrix multiply as if the target is a parent in Full Inherit Scale mode, shearing when rotation meets non-uniform scale), Before Original (Split Channels) (location, rotation, scale handled separately, like three Copy constraints), After Original Full (the same as a child in Full mode, with the same shear caveat), and After Original (Split Channels); and Influence.

## Drivers Panel

Drivers panel (Graph editor, Drivers mode; Sidebar region ‣ Drivers; N — or Context menu ‣ Edit Driver, Ctrl-D): shown in the Drivers Editor's Sidebar or as a popover when adding a driver to a property, it displays the driven property followed by the settings that govern the driver. Driver settings — Type: two categories — built-in functions (Average, Sum, Min, Max — the driven property takes the average, sum, lowest, or highest of the referenced Driver Variables, all giving the same result with a single variable) and Custom (Scripted Expression — an arbitrary Python expression referring to the variables by name; see Expressions). Driver Value shows the current result (useful for debugging). Variables: see Driver Variables. Update Dependencies forces an update of the Driver Value's dependencies. Show in Drivers Editor opens the full Drivers Editor (only in the popover). Driver Variables are references to properties, transformation channels, or the result of comparing two objects' transformations — drivers should reach object data through Driver Variables rather than direct Python references so dependencies are tracked. Add Input Variable adds one; Copy/Paste Variables copy the list to another driver. Each variable has a Name (for use in expressions — must start with a letter and contain only letters, digits, or underscores) and a Variable Type: Single Property (read an RNA property by data-block reference and path string — for transform properties this returns the exact UI value, while Transform Channel accounts for parenting and constraints), with ID Type (the ID-block type, e.g. Key, Image, Object, Material), ID (the specific ID-block, e.g. "Material.001"), RNA Path (the property's RNA name via a subset of Python attribute syntax — e.g. location.x or location[0] for the X location channel before parenting/constraints, or ["prop_name"] for a custom property), and Fallback (a value to use if the RNA Path can't be resolved, instead of failing the driver — see Context Property) — and the easiest way to make one is the input property's Copy As New Driver context option pasted in via Paste Driver Variables; Transform Channel (read a Transform channel from an object or bone), with ID (the object), Bone (the armature bone name, e.g. "Bone", "Bone.002", "Arm.r"), Type (e.g. X Location, X Rotation, X Scale — and Average Scale returns the combined scale as the cubic root of the total volume change, which, unlike X/Y/Z Scale, can be negative if the object is flipped), Mode (for rotation channels — the rotation data type including explicit Euler orders, defaulting to the target's; see Rotation Channel Modes), and Space (World, Transform, or Local Space); Rotational Difference (the rotational difference between two objects or bones in radians), with Bone; Distance (the distance between two objects or bones), with Bone and Space; and Context Property (a property implicitly referring to the currently evaluating animation system's scene or view layer — a weak reference that doesn't link the referenced scene/view layer when linking animation data, useful for, say, referencing the active camera's transform so a driver set up in a character file uses the set camera when the character is linked into a set), with Context (Active Scene or Active View Layer), RNA Path (e.g. camera.location.x or camera.location[0], or ["prop_name"]), and Fallback (a value used if the RNA Path can't be resolved — very useful for robust scene-global options via custom properties that may not exist in another scene, and for emulating the material Attribute Node's View Layer lookup). A tip notes that while the camera location channels are reachable via camera.location[0/1/2], getting its world-space location and orientation after parenting and constraints currently needs camera.matrix_world, viewed as four world-space vectors: matrix_world[0][0/1/2] is the Screen Right vector (camera local X), matrix_world[1][0/1/2] is the Screen Up vector (camera local Y).

Continuing matrix_world: matrix_world[2][0/1/2] is the opposite of the camera's pointing direction, and matrix_world[3][0/1/2] is the camera's location. Value shows the variable's value. Rotation Channel Modes: rotation Transform Channels support several modes — Auto Euler (decompose using the target's Euler order), XYZ Euler and the rest (an explicit Euler order), Quaternion (the rotation's quaternion form), and Swing and X/Y/Z Twist (split the rotation into a Swing that aims the chosen axis in its final direction, then a Twist around that axis — often needed for corrective Shape Keys and bones for organic joint rotation, and frequently produced in rigs with a helper bone using a Damped Track Constraint for the swing and its child using Copy Transforms for the twist). The Swing/Y-Twist channel values are: Y Rotation (the twist rotation's true angle), W Rotation (the swing rotation's true angle, independent of direction), and X/Z Rotation (weighted angles for the swing around the X/Z axis, whose magnitude matches W Rotation for a rotation purely around that axis and tapers to zero as the direction swings toward the other axis, following the falloff curves). Mathematically the swing angles come from quaternion components, using 2·arccos(w) for W and 2·arcsin(x) etc. for the others, with the component along the twist axis always 0 and replaced by the twist angle. Expressions: the Expression field takes an arbitrary Python expression referring to Driver Variables by name, with access to standard constants and math functions from math, bl_math, and other modules in the Driver Namespace (see the driver namespace example for adding a custom function) — for performance, lean on the Simple Expressions subset. Use Self lets the variable "self" reference the driver's own data (handy for objects and bones to avoid a self-pointing variable — e.g. self.location.x on the same object's Y rotation makes it tumble while moving), though dependencies via self may not be fully tracked. Simple Expressions: Blender can evaluate a useful subset of driver expressions natively, greatly improving performance (especially on multi-core systems), provided the expression uses only — Variable Names (ASCII only), Literals (floating-point and decimal integer), Globals (frame), Constants (pi, True, False), Operators (+, -, *, /, ==, !=, <, <=, >, >=, and, or, not, and the conditional/ternary if), Standard Functions (min, max, radians, degrees, abs, fabs, floor, ceil, trunc, round, int, sin, cos, tan, asin, acos, atan, atan2, exp, log, sqrt, pow, fmod), and Blender-provided functions (lerp, clamp, smoothstep). Simple expressions evaluate even when Python execution is disabled; an expression outside the subset triggers a "Slow Python expression" warning, but using a complex one in a few drivers is fine as long as most stay simple.

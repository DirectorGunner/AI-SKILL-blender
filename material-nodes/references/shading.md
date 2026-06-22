# Shading, Axis Locking, Visibility, Selecting Objects ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Shading; Axis Locking; Visibility; Selecting Objects; Object Types; Scene Properties; Manage Brushes.

## Shading

### Shading 

### Shade Smooth 

Reference

Mode:
Object Mode

Menu:
Object ‣ Shade Smooth

Makes an object display with soft or jagged appearance.
This enforces the "smoothing" property on all faces in the mesh,
including during geometry addition or removal.

This function will also strip out any Smooth By Angle Modifiers.

The edge of the object still appears distinctly faceted despite smoothing.
Activating smoothing doesn't alter the mesh structure;
it changes normal computation across surfaces (normals blend together),
creating a smoother appearance.

To revert to faceted shading, use Shade Flat (normals become flat)
as shown in the first comparison below.

Keep Sharp Edges
Do not strip marked edges (which are unneeded for flat-shaded objects).
This toggle helps preserve data for future reversals.

### Shade Auto Smooth 

Reference

Mode:
Object Mode

Menu:
Object ‣ Shade Auto Smooth

Attaches a Smooth By Angle Modifier that automatically sets
edge sharpness according to the difference between adjacent face normals.
Note, the modifier is anchored to stay the last modifier.

Auto Smooth
When off, any Smooth By Angle Modifiers get removed.

Angle
Largest angle difference between adjacent face normals before they stop being treated as smooth.

### Shade Flat 

Reference

Mode:
Object Mode

Menu:
Object ‣ Shade Flat

Instructs the object to display and output all faces uniformly,
using each face's normal orientation.
This is often preferred for polygonal forms.

This function will also strip out any Smooth By Angle Modifiers.

Keep Sharp Edges
Do not strip marked edges (which are unneeded for flat-shaded objects).
This toggle helps preserve data for future reversals.

## Axis Locking

### Axis Locking 

Axis locking illustration. 

This toggle narrows transformations to the chosen axis.

Transformations (movement/resizing/rotation)
in Object and Edit Modes (plus extrusions in Edit Mode)
can be limited to a specific axis according to
the active transform orientation.
By confining a transformation to one axis, you restrict movement to a single dimension.

### Usage 

A locked axis displays in higher brightness than an unlocked axis. In the picture on the right,
the Z axis glows brightly since movement is confined to this axis. This state can be achieved in two ways:

### Hotkey 

The axis of operation can switch during a transform by pressing X, Y, or Z.

### Pointing 

Axis constraint in action. 

Pressing MMB after starting a transform lets you select an axis to limit to.
A clickable option to define the translation path is displayed,
showing the three axes in the viewport. A dashed white line indicates direction.
The axis to confirm will be the one highlighted when the MMB is released.

When you've moved in the target direction,
pressing MMB will snap to the highlighted axis.

### Axis Locking Types 

### Axis Locking 

Reference

Mode:
Object and Edit Modes (move, rotate, scale, extrude)

Shortcut:
X, Y, Z or MMB after moving the mouse in the target direction.

Axis locking narrows the transformation to a single dimension (or blocks movement along two axes).
A face, vertex, or other selectable thing can only shift,
resize, or rotate along one axis.

### Plane Locking 

Reference

Mode:
Object and Edit Modes (move, scale)

Shortcut:
Shift - X, Shift - Y, Shift - Z or Shift - MMB
after moving the mouse in the target direction.

Plane locking example. 

Plane locking limits the transformation to two dimensions
(or forbids movement along one axis),
establishing a space where the element can shift or resize easily.
Plane locking only influences movement and sizing.

Keep in mind that for turning, both axis and plane locking work identically as a rotation occurs
around one axis only.
Trackball rotations R R cannot be confined in any way.

### Axis Locking Modes 

A single press of a key locks movement to the current transform orientation setting.
A second press of the same key locks movement to the matching world axis
(if the transform orientation is already Global, the Local orientation is selected instead).
A third press removes all limits.

The orientation is configured
in the Transform Orientation
dropdown of the viewport header.

For example, when transform orientation is set to Normal,
hitting G to start moving, then Z locks moving
in the Z direction according to the Normal orientation. Pressing Z
a second time locks moving to the world Z direction.
Pressing Z once more deactivates all limits.
The active mode appears in the left corner of the viewport header.

| Z axis locking in world space.  | Z axis locking in object space.  | Z axis locking in world space with vertex selection.  | Z axis locking in Normal space with vertex selection.  |

As shown in the Axis locking modes example,
the movement direction considers the selection too.

Note that using an axis lock doesn't block numerical transform entry.

## Visibility

### Visibility

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Visibility

The Visibility panel controls how objects are interacted with in the viewport and in the final render. These visibility options can also be set in the Outliner.

Selectable
The object is able to be selected in the 3D Viewport.

Show In

Viewports
The object will be displayed in the 3D Viewport.

Renders
The object is able to be in the final render, note that it will still be visible in rendered shading view.

See also

Cycles has additional Visibility properties and also Grease Pencil objects have additional Visibility properties.

Mask

Holdout
Render objects as a holdout or matte, creating a hole in the image with zero Alpha, to fill out in compositing with real footage or another render.

## Selecting Objects

### Selecting Objects

Selection determines which elements will be the target of our actions. Selections work on the current scene visible objects. Blender has advanced selection methods. Both in Object Mode and in Edit Mode .

### Selections and the Active Object

Blender distinguishes between two different states of selection:

Active object in yellow, selected object in orange, and unselected object in black.

In Object Mode the last (de)selected item is called the "Active Object" and is outlined in yellow (the others are orange). There is at most one active object at any time.

Many actions in Blender use the active object as a reference (for example linking operations). If you already have a selection and need to make a different object the active one, simply reselect it with Shift - LMB .

All other selected objects are just selected. You can select any number of objects. In order to change a property or to perform an operation on all selected objects (bones, and sequencer strips) hold Alt , while confirming.

### Select Menu

### All

Reference

Mode :

All Modes

Menu :

Select ‣ All

Shortcut :

A

Select all selectable objects.

### None

Reference

Mode :

All Modes

Menu :

Select ‣ None

Shortcut :

Alt - A

Deselect all objects, but the active object stays the same.

### Invert

Reference

Mode :

All Modes

Menu :

Select ‣ Invert

Shortcut :

Ctrl - I

Toggle the selection state of all visible objects.

### Box Select

Reference

Mode :

All Modes

Menu :

Select ‣ Box Select

Shortcut :

B

Interactive box selection.

### Circle Select

Reference

Mode :

All Modes

Menu :

Select ‣ Circle Select

Shortcut :

C

Interactive circle selection.

### Lasso Select

Reference

Mode :

All modes

Menu :

Select ‣ Lasso Select

Shortcut :

Ctrl - Alt - LMB

See Select Lasso.

### Select Active Camera

Reference

Mode :

Object Mode

Menu :

Select ‣ Select Active Camera

Selects the active camera, this is especially handy in complex scene.

### Select Mirror

Reference

Mode :

All Modes

Menu :

Select ‣ Select Mirror

Select the Mirror objects of the selected object, based on their names, e.g. "sword.L" and "sword.R".

### Select Random

Reference

Mode :

Object Mode

Menu :

Select ‣ Select Random

Randomly selects unselected objects based on percentage probability. The percentage can be modified in the Adjust Last Operation panel. It is important to note that the percentage is the likelihood of an unselected object being selected and not the percentage amount of objects that will be selected.

### Select More/Less

Reference

Mode :

Object Mode

Menu :

Select ‣ More/Less

Shortcut :

Ctrl - NumpadPlus , Ctrl - NumpadMinus

Their purpose, based on the hierarchical.

More
Expand the selection to the immediate parent and children of the selected objects.

Less
Contrast the selection, deselect objects at the boundaries of parent/child relationships.

Parent
Deselects the currently selected objects and selects their immediate parents.

Child
Deselects the currently selected objects and selects their immediate children.

Extend Parent
Extends the selection to the immediate parents of the currently selected objects.

Extend Child
Extends the selection to the immediate children of the currently selected objects.

### Select All by Type

Reference

Mode :

Object Mode

Menu :

Select ‣ Select All by Type

With this tool, it becomes possible to select objects of a certain type in one go. For a description of all object types see Object Types.

### Select Grouped

Reference

Mode :

Object Mode

Menu :

Select ‣ Select Grouped

Shortcut :

Shift - G

There are two ways to organize the objects in relation to one another. The first one is parenting , and the second is simple grouping . These relationships to an artist's advantage by selecting members of respective families or groups. Select Grouped uses the active object as a basis to select all others.

Children
Selects all hierarchical descendants of the active object.

Immediate Children
Selects all direct children of the active object.

Parent
Selects the parent of this object if it has one.

Siblings
Select objects that have the same parent as the active object. This can also be used to select all root level objects (objects with no parents).

Type
Select objects that are the same type as the active one.

Collection
Select all objects that are in the same collection as the active one. If the active object belongs to more than one collection, a list will pop up so that you can choose which collection to select.

Object Hooks
Every hook that belongs to the active object.

Pass
Select objects assigned to the same Render Pass.

Color
Select objects with same Object Color.

Keying Set
Select objects included in the active Keying Set.

Light Type
Select matching light types.

### Select Linked

Reference

Mode :

Object Mode

Menu :

Select ‣ Select Linked

Shortcut :

Shift - L

Selects all objects which share a common data-block with the active object. Select Linked uses the active object as a basis to select all others.

Object Data
Selects every object that is linked to the same Object Data, i.e. the data-block that specifies the type (mesh, curve, etc.) and the build (constitutive elements like vertices, control vertices, and where they are in space) of the object.

Material
Selects every object that is linked to the same material data-block.

Instanced Collection
Select every object that is linked to the instanced collection.

Texture
Selects every object that is linked to the same texture data-block.

Particle System
Selects all objects that use the same Particle System .

Library
Selects all objects that are in the same Library.

Library (Object Data)
Selects all objects that are in the same Library and limited to Object Data .

### Select Pattern

Reference

Mode :

Object Mode

Menu :

Select ‣ Select Pattern…

Selects all elements whose name matches a given pattern. Supported wild-cards: * matches everything, ? matches any single character, [abc] matches characters in abc , and [!abc] match any character not in abc . As an example *house* matches any name that contains house , while floor* matches any name starting with floor .

Matching can be configured to respect or ignore letter casing.

Extend
When the Extend checkbox is active, the selection expands rather than being replaced.

## Object Types

### Object Types

Reference

Mode :

Object Mode

Menu :

Add

Shortcut :

Shift - A

Objects are created using the Add menu in the 3D Viewport header.

Mesh
Structures made of vertices, edges, and polygonal surfaces
that can be extensively modified with Blender's mesh tools.
See Mesh Primitives.

Curve
Forms defined mathematically, manipulated with handles
or influence points (instead of vertices), to govern shape and bending.
See Curves Primitives.

Surface
Mathematically-defined areas modified through influence points.
These serve well for basic rounded forms and natural landforms.
See Surfaces Primitives.

Metaball
Forms generated by a mathematical formula (lacking vertices or control points)
defining the 3D area they inhabit. Meta objects exhibit a fluid-like property
where overlapping metaballs blend into each other,
appearing as a unified form.
See Meta Primitives.

Text
A planar representation of characters.

Volume
Repository for OpenVDB storage data generated
by external applications or Blender's simulation systems.

Grease Pencil
Objects built through drawn strokes.
See Grease Pencil Primitives

Armature
Employed for rigging 3D constructs to enable positioning and animation.

Lattice
Non-visible mesh-like structures commonly applied to alter other objects
with the assistance of the Lattice Modifier.

Empty
Basic null objects serving as visual transform anchors that do not appear in output.
They serve to manage the placement or motion of other objects.

Image
Null objects that show image data in the 3D workspace.
These help artists with sculpting or movement work.

Image Plane
Adds a face with applied materials and textures derived from an image.
The plane dimensions scale to preserve the image's proportions.

Light
Null objects that cast illumination and control lighting in output.

Light Probe
Applied within the EEVEE rendering system to capture light details for ambient illumination.

Camera
The synthetic lens determining rendered output content.

Speaker
Null objects that introduce audio elements to the environment.

Force Field
Null objects that supply external influences to simulations, generating motion,
displayed as small control nodes.

Collection Instance
Select from a catalog of established collections. Upon selection, a null object forms,
creating an instance of the chosen collection (collection instancing enabled).

### Common Options

Object properties can be adjusted in the Adjust Last Operation panel
following object creation:

Type
Several objects allow type reassignment after creation through a selection menu.

Radius/Size
Sets the initial dimensions.

Align
Rotates the new object according to one of the following modes:

World :

The object aligns with the universal coordinate axes, with its front pointing toward the negative Y axis (default).

View :

The object aligns with the viewport's coordinate system, with its front addressing the viewing angle.

3D Cursor :

The object matches the 3D Cursor's rotational orientation.

Location
Items spawn at the 3D Cursor position by default.
These parameters allow placement at alternative positions.

Rotation
Values enable object rotation, overriding the standard orientation.

## Scene Properties

### Scene Properties

### Scene

Reference

Panel :

Properties ‣ Scene ‣ Scene

Camera
Designates the rendering perspective.
You can also set the rendering perspective in the 3D Viewport using Ctrl - Numpad0 .

Background Scene
Provides the ability to display a scene as a backdrop,
useful when focusing on foreground animation, for instance,
without background elements obstructing the workspace.

This scene can include its own movement timeline, physics effects, etc,
though you must activate it via the Scene data-block menu to adjust its internals.

Background Scenes can themselves reference another Background Scene (they're embedded recursively).
This allows expanding current scenes by setting them as a backdrop
to a newly built scene where modifications happen.

Tip

This pairs effectively with Linking to a Scene,
where one blend-file supplies the context, reusable in multiple locations.

Active Clip
Assigns a Movie Clip usable in
Motion Tracking Constraints or a camera's Background Images.

### Units

Reference

Panel :

Properties ‣ Scene ‣ Units

Unit System
The measurement framework for UI fields.

None :

Employ systems lacking connection to actual scales,
largely equivalent to Metric minus labels.

Metric :

Employ the metric measurement framework in this scene.

Imperial :

Employ the imperial measurement framework in this scene.

Unit Scale
Conversion ratio between system units and interface-displayed quantities.
This adjustment becomes useful when modeling at microscopic or astronomical proportions.

Note

This governs UI presentation only,
not underlying behavior. As an illustration, physics effects
disregard the unit scale.

Separate Units
For Metric or Imperial , show properties as multiple amounts.
For instance, 2.285m becomes 2m 28.5cm .

Rotation
Angle presentation option.

Degrees :

Show angles as degrees in the interface.

Radians :

Show angles as radians in the interface.

Length
Measurement for displaying length data.

Adaptive :

The dimension adopted for a specific value shifts based on scale.
For instance, some might display as 23cm while others read as 10km .

Meters/Centimeters/Feet :

A consistent dimension used across all length values in the interface.

Mass
See Length .

Time
See Length .

Temperature
See Length .

| Full Name | Short Name(s) | Scale of a Meter |
| thou | mil | 0.0000254 |
| inch | " , in | 0.0254 |
| foot, feet | ' , ft | 0.3048 |
| yard | yd | 0.9144 |
| chain | ch | 20.1168 |
| furlong | fur | 201.168 |
| mile | mi , m | 1609.344 |

| Full Name | Short Name(s) | Scale of a Meter |
| micrometer | um | 0.000001 |
| millimeter | mm | 0.001 |
| centimeter | cm | 0.01 |
| decimeter | dm | 0.1 |
| meter | m | 1.0 |
| dekameter | dam | 10.0 |
| hectometer | hm | 100.0 |
| kilometer | km | 1000.0 |

### Gravity

Reference

Panel :

Properties ‣ Scene ‣ Gravity

Options governing universal gravity for simulation effects.

Consult the Physics documentation for thorough information.

### Simulation

Simulation Range
Apply a simulation period distinct from the scene period for
Simulation Nodes
that don't establish their own frame bounds.

Start, End
The frame at which simulation commences/terminates.

### Keying Sets

Reference

Panel :

Properties ‣ Scene ‣ Keying Sets

See Keying Sets.

### Audio

Reference

Panel :

Properties ‣ Scene ‣ Audio

Options managing universal sound characteristics.
For control of sound replay from within Blender itself, consult the sound options
in the Settings.

Volume
Sound magnitude for the scene.

Distance Model
Specifies how volume reduction relates to distance.
The Inverse method is most physically accurate,
though linear and exponential options exist as alternatives.
The clamped versions restrict volume to not exceed 100% (1.0),
meaning that if separation is smaller than the baseline separation, volume remains 100%.
For in-depth explanations of each mode
consult the OpenAL specification.

Doppler Speed
Sound velocity for Doppler shift math.
The standard measurement is 343.3 m/s in standard conditions, around 1560 m/s in seawater for instance.

Doppler Factor
Affects the magnitude of the Doppler shift.
You can amplify or minimize pitch variation intensity, with 1.0 being physically accurate.

Update Animation Cache
Refreshes the sound animation record. Beneficial if audio artifacts emerge.

### Rigid Body World

Reference

Panel :

Properties ‣ Scene ‣ Rigid Body World

The Rigid Body World organizes rigid body components,
supplying parameters applicable to each rigid body within the environment.

See Rigid Body World for detailed documentation.

### Animation

Reference

Panel :

Properties ‣ Scene ‣ Animation

Manages animation content for scene-level characteristics, such as active Actions
and their designated Slot.

See Manually Assigning Actions and Slots for thorough guidance.

Scene
Specifies where animation content for scene characteristics is held/retrieved.

### Custom Properties

Add and handle personal attributes to keep information in the scene's data store.
See the Custom Properties documentation for comprehensive information.

## Manage Brushes

### Manage Brushes

Brush assets are stored in asset libraries to make them accessible from any Blender session. There are two ways of managing brush assets:

- Using asset operators: Create and update brush assets using utility operators from any Blender file. Storage is managed by Blender. Convenient for simple "on the fly" management of personal brush asset libraries.

- Using manual storage: Create and update brush assets by opening blend files within asset libraries, and managing brush asset data-blocks in there. Useful for careful curation of asset libraries, especially to prepare them for sharing with others.

### Asset Operators

Brushes can be managed through a few operators that let Blender handle the act of saving and updating the brushes in asset libraries for you. Assets managed this way will be saved in special asset system files using a .asset.blend file extension.

Note

Note that only brush assets created via Duplicate Asset can be edited further using these asset operators. For others, these operations will be grayed out, and manual management is necessary.

Brushes from the Essentials asset library cannot be edited.

Reference

Mode :

All Paint Modes

Panel :

Sidebar ‣ Tool ‣ Brush Asset
Properties ‣ Tool ‣ Brush Asset

Menu :

Asset Shelf ‣ Context Menu

Brush Asset panel in the Sidebar showing asset operators.

Duplicate Asset…
Creates a copy of the currently active brush as asset, and activates it. A popup is spawned to input some settings to use:

Name
A custom name to use for the new brush.

Library
Choose an Asset Library to store the new brush asset in. The available asset libraries are configured in the Preferences.

Catalog
Choose an Asset Catalog to assign the brush asset to. Entering a non-existent name/path will create a new catalog accordingly.

Delete Asset
Permanently remove this brush asset from the Asset Library it is stored in. This cannot be undone, so a popup will ask for confirmation.

Edit Metadata…
Spawns a popup to change some of the available asset metadata fields:

Catalog
Choose an Asset Catalog to assign the brush asset to. Entering a non-existent name/path will create a new catalog accordingly.

Author
See Asset Author.

Description
See Asset Description.

Edit Preview Image…
Opens a window with the File Browser to select an image for the asset preview.

Save Changes to Asset
Saves any changes made to the active brush to the asset library.

Revert to Asset
Discards any unsaved changes made to the brush asset.

### Manual Storage

See also

Life Cycle of an Asset
Complete description of the manual asset create, edit, share and use workflow.

It is also possible to manually manage brushes in blend-files like any other asset data-block. By marking brushes as assets and saving the file in an asset library, they become available from any Blender session. This gives full control over how assets are stored, and is particularly useful for curating asset libraries that can be shared with others.

The Mark as Asset operator used on a brush in the Outliner.

Brushes can be imported as normal data-blocks from other files (including from .asset.blend files from an asset library) through appending. In the Blender File mode of the Outliner, the brush will be listed under Brushes . Right-click the brush and select Mark as Asset . By saving the file inside of an asset library directory, the asset becomes available from all Blender sessions. If necessary, configure an asset library directory in the Preferences.

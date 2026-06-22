# Light Objects, Speaker Objects, Frame Range, Options ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Light Objects; Speaker Objects; Frame Range; Options; Performance; Precision; Move; Object Origin; Faces.

## Light Objects

### Light Objects

Reference

Panel :

Properties ‣ Object Data
and Shader Editor ‣ Sidebar ‣ Options

### Common Settings

Type
Specifies the light category.

Temperature
Heat rating in Kelvin, for ordinary illumination hues.

Color
Tone tint of the released illumination.

Exposure
Scale the light strength by \\(2^{exposure}\\) .
This streamlines handling a broad variety of output ranges using a single variable.

Normalize
By default, complete light output stays constant as light shape and scale change.
Deactivating this option releases more illumination as the light gets bigger.

### Renderer Settings

- EEVEE specific settings

- Cycles specific settings

### Point Light

Point light.

A point light projects uniform luminescence outward in all directions.
It gets shown by a vacant, encircled mark.
Since the light originates from a point, the path of the light striking an item's surface
stems from the trajectory joining the light and the surface location.
It approximates the behavior of (for instance) a filament bulb.

Light intensity/energy weakens proportional to (along other influences)
spacing from the point light to the item. Stated differently,
distant matter gets shown darker.

Power
Output measure of the light. Larger quantities raise the light's brightness.
Sub-zero quantities are permitted, however should get avoided for authentic plus unbiased outcomes.

Radius
When beyond zero, the light emits from a round shell with the designated spacing.
Greater light range softens shadows plus specular effects, yet reduces perceptual brightness
because strength distributes across larger region.

Soft Falloff
Employ falloff to prevent harsh transitions where the light form meets additional things.

### Spot Light

A spot light sends a narrowing column of light from the point, aimed in one trajectory.

Power
Output measure of the light. Greater amounts boost the light's strength.
Negative quantities are permitted, however should get sidestepped for authentic plus unbiased outcomes.

Radius
When surpassing zero, the light emits from a round shell with the chosen spacing.
Greater light range generates gentler shadows plus specular effects.

Soft Falloff
Employ falloff to prevent harsh transitions where the light form meets additional items.

### Beam Shape

Spot option modifications update the spotlight's visual representation in the 3D Viewport.

Angle
The breadth of the outer cone of a spot light, which sets how broad the light disperses.
Narrower angles produce tight, focused projection, while broader angles create wider,
softer spread region.

This metric denotes the apex angle of the light cone in degrees,
and spans from 1.0° (tight projection) to 180.0° (expansive projection).

| Angle: 45° | Angle: 60° |

Blend
The Blend variable governs the interior cone of the spot.
The Blend figure can run from (0.0 to 1.0).
The figure is proportionate and conveys that portion of space that the interior cone must
fill in the outer cone Size .

The interior cone edge shows the boundary line where light from the spot will start to blurry/mellow;
previous to here it stays practically full strength.
Raising the Blend value creates blurrier/mellower spotlight limits,
and lowers the interior cone's round zone (by initiating blur/soften earlier).

To make the spot deliver a quicker fade price and therefore less blurry/mellow limits,
lower the Blend value.
At Blend of 0.0 you receive extremely sharp spotlight limits, zero transition in between light and dark.

The fade price of the spot light is determined by the gap separating Blend and Size values;
the bigger the round opening separating them, the more steady the light darkens separating Blend and Size .

Blend and Size regulate the spot light cone's opening and mellowness ("radial" falloff);
they do not regulate the shadow's mellowness as displayed below.

Render showing the mellow edge spotlighted zone and the crisp/firm item shadow.

Notice in the picture that the item's shadow stays crisp because of path-tracing,
whereas the spotlight openings turn mellow.
To get additional items casting mellow shadows inside the spot zone, you have to change further shadow settings.

Show Cone
Displays a semi-transparent column in 3D Viewport to show which items stay inside it.

### Area Light

The area light replicates light released from a plane (or plane-approximation) supplier.
For instance, a movie screen, office fluorescent bulb, portal, or layers of clouds are samples of area light. The area light yields shadows with
gentle limits by sampling a light via a lattice the breadth of which comes from the designer.
This differs sharply from dot-like synthetic lights which yield sharp limits.

Power
Output measure of the light. Greater amounts boost the light's strength.
Negative quantities are permitted, however should get sidestepped for authentic plus unbiased outcomes.

Shape
Projection form of the light.

Rectangle :

The light form can get depicted as a four-sided shape plus modified with the "X" plus "Y" values.

Square :

The light form can get depicted as a four-sided shape plus modified with the Size variable.

Disk :

The light form can get depicted as a rounded shape plus modified with the Size variable.

Ellipse :

The light form can get depicted as an elliptical form plus modified with the X plus Y values.

Tip

Choosing the fitting projection for your area light improves the genuineness of your setting.
For instance, you could build an internal setting plus would like to mirror light moving through an entrance.
You could position a Four-sided area light inside an entrance (up) or from fluorescent bulbs (sideways)
with suitable ratio for Size X plus Size Y . For the simulation of the light released by
a movie screen, an up-facing Four-sided area light suits greatest in typical scenarios.

Size / Size X / Size Y
Dimensions for the Square or Rectangle .

### Sun Light

A sun light provides light of constant intensity emitted in a single direction from infinitely far away. It can be very handy for a uniform clear daylight open-space illumination. In the 3D Viewport, the sun light is represented by an encircled black dot with rays emitting from it, plus a dashed line indicating the direction of the light.

Note

This direction can be changed by rotating the sun light, like any other object, but because the light is emitted from a location considered infinitely far away, the location of a sun light does not affect the rendered result.

Strength
Strength of the lights. See more details at Power of Lights.

Angle
The size of the sun light according to its angular diameter as seen from earth.

### Power of Lights

When Normalize is enabled, the power of sun lights is specified in Watts per square meter. The power of point lights, spot lights, and area lights is specified in Watts.

But this is not the electrical Watts that consumer light bulbs are rated at. It is Radiant Flux or Radiant Power which is also measured in Watts. It is the energy radiated from the light in the form of visible light.

If you want to set the power to real world values, you have to convert the wattage of consumer bulbs or LED lights to radiant flux, but it is not a straightforward process. The wattage of bulbs means the electrical power required to power them. LED lights have a "Watt equivalent" which is neither the electrical power they require nor the amount of light they put out. Some consumer lights specify lumens or luminous flux which is the radiant flux weighted with the wavelengths perceived by the human eye.

To save you from doing the conversion, here is a table of typical power values for point, spot, and area lights:

| Real world light | Power | Suggested Light Type |
| Candle | 0.05 W | Point |
| 800 lm LED bulb | 2.1 W | Point |
| 1000 lm light bulb | 2.9 W | Point |
| 1500 lm PAR38 floodlight | 4 W | Area, Disk |
| 2500 lm fluorescent tube | 4.5 W | Area, Rectangle |
| 5000 lm car headlight | 22 W | Spot, size 125 degrees |

And a table of typical Strength values for sun lights:

| Sun type | Strength |
| Clear sky | 1000 W/m 2 |
| Cloudy sky | 500 W/m 2 |
| Overcast sky | 200 W/m 2 |
| Moonlight | 0.001 W/m 2 |

These values will produce much brighter or dimmer lights than you would expect, because our eyes adapt while a render engine does not. So to compensate, adjust the Exposure in Render ‣ Film .

To get realistic results, remember to also set the light size and color to realistic values. The color of your lights will also influence how bright they appear to the human visual system. If you leave the power unchanged, a green light will seem the brightest, red darker and blue the darkest. Thus you might want to manually compensate for these perceived differences.

## Speaker Objects

### Speaker Objects 

Speaker objects are designed to emit audio within the 3D Viewport. They enable spatial audio playback, making them ideal for animated projects and real-time environments. Speaker configuration is managed through the Properties editor.

Speaker object. 

### Playback Time 

Unlike other objects, speaker timing is not set directly via properties. The NLA editor manages speaker playback instead, utilizing Sound Strips:

- Sound strips in the NLA editor govern when playback begins.

- When a new speaker is created, a sound strip is automatically assigned at the current frame.

- Separate sound strips allow the same speaker to play at different times.

- Audio plays for the full file duration regardless of the sound strip length.

### Data Properties 

Reference

Panel :

Properties editor ‣ Data

Speaker properties. 

### Sound 

Open
The Data-Block Menu for importing audio files. Two audio-loading properties are available:

Cache
Converts sound to memory storage for quicker playback. Best for brief, frequently-used sounds but unsuitable for lengthy audio.

Mono
Restricts audio to a single channel. Necessary for spatial audio and directional effects since multi-channel files assume pre-mixed spatial information.

Mute
Toggles audio output off.

Volume
Adjusts speaker loudness.

Pitch
Changes playback speed and pitch. Increasing values accelerates playback and raises pitch; decreasing values slow it down and lower pitch.

### Distance 

Distance-dependent attenuation manages how speaker volume decays with listener distance. This emulates natural sound behavior, enhancing spatial audio realism by creating louder nearby sounds and quieter distant ones.

These options fine-tune volume falloff over distance:

Volume Min, Max
Sets minimum and maximum volume limits based on distance. Volume will not fall below or rise above these thresholds regardless of listener proximity.

Attenuation
Determines how quickly volume drops with increasing distance. Behavior depends on the scene's Distance Model.

Max Distance
The farthest point where attenuation is computed. Beyond this distance, volume stays constant.

Distance Reference
The distance at which volume reaches full (1.0). Should correspond to the recording distance for accurate playback.

### Cone 

Directional speaker behavior settings.

Picture a cone emanating from the speaker's origin, aligned with the speaker's forward direction. Audio propagates directionally via inner and outer cone zones. Cone angles define their opening spread, where 360° creates a fully open cone with no directionality.

- Inside the inner cone : Maximum volume.

- Between the inner and outer cone : Linear interpolation of volume.

- Outside the outer cone : Volume follows the Outer Cone Volume setting.

Angle Outer
The outer cone opening angle in degrees. Beyond this boundary, Outer Cone Volume dictates the output level.

Angle Inner
The inner cone opening angle in degrees. Full volume is maintained within this region.

Outer Cone Volume
Loudness outside the outer cone. Smaller values increase directionality.

### Animation 

Controls animation metadata for scene-wide properties, including active Actions and their designated Slot.

See Manually Assigning Actions and Slots for further information.

### Custom Properties 

Define and organize custom attributes to store data on the action's data block. Refer to the Custom Properties page for complete details.

## Frame Range

### Frame Range 

Frame Range panel. 

This panel establishes animation duration measured in frames. Dividing total frames by the scene's Frame Rate yields animation duration in seconds. For instance, a 250-frame sequence at 30 fps lasts 8.3 seconds.

Frame Start, End
Specify the first and final frames to use for Rendering Animations.

Step
Determines frame increment per render iteration. Values above 1 skip intermediate frames. This parameter also applies when reviewing rendered results.

### Time Stretching 

Rescale animation playback to make it run faster or slower. The Old and New values can function either as absolute frame counts or as a ratio: for example, setting Old to 2 and New to 1 accelerates the animation by half.

Warning

Time Stretching does not affect the Start or End frames configured above. Ensure your animation runs completely within these bounds without truncation or trailing blank frames.

Old
The original animation length in frames.

New
The target duration in frames for the remapped animation.

## Options

### Options

Reference

Menu :

Properties ‣ Render ‣ Options panel.

Backface Culling
Hide the reverse sides of faces using backface culling.

X-Ray
Render the scene as transparent. The slider adjusts transparency intensity.

Shadow
Render a sharp shadow in the scene.

Darkness
The shadow's darkness level, sliding between 0 (invisible) and 1 (black).

Light Direction
Sets the light source orientation casting shadows.

Shadow Shift
Adjusts the Shadow termination angle to limit self-shadowing artifacts.

Shadow Focus
Determines the falloff near the shadow boundary.

Depth of Field
Employ the active camera's Depth of Field settings in the viewport. Shows only when looking through the camera.

Settings are located at Properties ‣ Camera ‣ Depth of Field.

Outline
Render object boundaries in the viewport. The outline color is adjustable.

Specular Highlighting
Render specular reflections.

Note

Available only when Lighting uses Studio mode or when a MatCap with a specular component is active.

Cavity
Accentuate ridge and valley features in scene geometry.

Type
Cavity calculation method.

World :

More precise but slower computation.

Screen :

Quick but ignores ridge/valley dimensions.

Both :

Applies both methods.

Ridge
Adjusts the prominence of ridges.

Valley
Adjusts the prominence of valleys.

## Performance

### Performance

Reference

Panel :

Properties ‣ Render ‣ Performance

High Quality Normals
Employs higher precision normals and tangents, improving visual fidelity for complex geometry with high-detail textures, at the cost of increased memory consumption.

## Precision

### Precision 

Reference

Mode:
Object and Edit Modes

Shortcut:
Ctrl and/or Shift

Pressing Ctrl while doing a transform (such as moving, rotating, or resizing)
toggles Transform Snapping.
With Increment Snap
enabled, transformations happen in discrete steps.

Holding Shift while doing a transform will execute
at 10% speed, permitting very subtle control.

The transformation amount appears in the viewport header.
Releasing Ctrl or Shift reverts
the action to regular pace.

Note

The snapping techniques detailed here only activate
when Increment Snap is turned on.

Tip

It is achievable to enable snapping and precision simultaneously,
hold Ctrl and Shift. This produces:

Move
Increments of 0.1 unit, independent of zoom.

Rotation
Increments of 1 unit.

Scale
Increments of 0.01 unit.

### Usage 

### With Hotkeys 

Press G, R, or S and then hold either Ctrl,
Shift, or Shift - Ctrl.

### With the Transform Gizmo 

Pick the gizmo handle then while positioning hold Ctrl, Shift, or Shift - Ctrl
to engage precision or snapping controls.

Reference

Learn about the Transform Gizmo.

Tip

Combining With Other Controls

Each precision choice here works alongside
the Axis Locking techniques and
can be paired with the various Pivot Points.

### Snapping 

### Move 

One unit (baseline zoom). 

Snapping during movement shifts the object in 1 unit intervals.
In an aligned perspective,
The jump amount changes with magnification.
For instance, at standard zoom objects shift in 1 unit intervals (i.e. between the two light gray bands).
Magnifying to show the following grid band causes 1/10 unit steps.
Further magnification causes 1/100 unit steps until the magnification limit.
Decreasing magnification causes movement in 10, 100 unit jumps, etc.

### Rotation 

Holding Ctrl causes rotations in 5 degree steps.

### Scale 

Holding Ctrl causes size changes in 0.1 unit intervals.

Note

Alternative Snapping

Note that when you are Snapping To
a choice besides Increment,
holding Ctrl causes the selection to snap to that closest thing.

Reference further snapping documentation.

### Precision 

Holding Shift when transforming grants very subtle control without
depending on set increments. Instead, large pointer movements across
the screen cause only small changes to the selection.

In rotation mode the chosen item will turn in 0.01 degree intervals.

## Move

### Move 

Reference

Mode:
Object Mode, Edit Mode, and Pose Mode

Menu:
Object/Mesh/Curve/Surface ‣ Transform ‣ Move

Shortcut:
G

In Object Mode, the move operation relocates objects.
Displacement refers to changing position in 3D space. It also lets you move the pieces
that compose the object within the active viewport.

Pressing G initiates "Move" mode. The chosen object
or part then drifts with the mouse and viewport angle.
To finalize, click LMB.
While moving, the shift on each X, Y, and Z direction displays in the viewport header.

Position Display. 

Tip

Shifting an object in Object Mode changes its anchor.
Moving the object's corners/lines/surfaces in Edit Mode keeps the anchor unchanged.

Reference

Mixing shortcuts provides better control. Refer to Transform Control.

### Options 

Move X, Y, Z
The displacement on each axis.

Orientation
Realigns the transformation directions to a specified orientation.
Reference Transform Orientations for details.

Proportional Editing
The extruded side will impact nearby components.
See Proportional Editing for complete information.

## Object Origin

### Object Origin

Each object has an origin point. The location of this point determines where the object is located in 3D space. When an object is selected, a small dot appears, denoting the origin point. The location of the origin point is important when translating, rotating or scaling an object. See Pivot Points for more.

The color of the origin changes based on the selection state of the object.

Yellow :

Object is active.

Orange :

Object is selected, but not active.

White :

Object is not linked and not selected.

Turquoise :

Object is linked.

Light Turquoise :

Object is selected, linked, but not active.

Note

Colors are themeable and might appear different. The colors described here are from the default Dark Theme.

### Set Origin

Reference

Mode :

Object Mode

Menu :

Object ‣ Set Origin

The object origin and geometry can be moved relative to each other and to the 3D cursor.

Type

Geometry to Origin
Moves the model to the origin and this way the origin of the object will also be at the center of the object.

Origin to Geometry
Moves the origin to the center of the object.

Origin to 3D Cursor
Moves the origin of the model to the position of the 3D cursor.

Origin to Center of Mass
Moves the origin to the calculated center of mass of model (assuming the mesh has a uniform density).

Center
Median Point Center, Bounding Box Center

Tip

To transform an object's origin directly, enable Affect Only Origins in the Tool Settings Options .

## Faces

### Faces

Reference

Mode :

Object Mode

Panel :

Properties ‣ Object Properties ‣ Instancing

Instancing Faces is the capability to replicate an object on each face of a parent object. One of the best ways to explain this is through an example illustration.

Scale
Scales each instance according to the size of its corresponding face.

Inherit Scale
Scale the instance faces objects.

Make Instance Face tool converts linked objects (that share mesh data) into instanced faces. This tool creates the parent object (instancer) with faces where the objects were, then it uses Instancing Faces to put instances at the location of every created face.

You can go back from Instancing Faces to multiple linked objects using Make Instances Real.

See also

Example blend-file

Download the blend-file used for the examples on this page here.

### Basic Usage

In this example we will use a UV sphere with an extruded "north pole" as our base object and a cube as our parent mesh. To parent the sphere to the cube, in Object Mode , first LMB select the sphere, then Shift - LMB select the cube (order is very important here), and finally Ctrl - P to parent.

| A cube and a sphere. | Instancing Faces applied to the cube. |

Next, in the Properties ‣ Object Properties ‣ Instancing , select Faces . The sphere is instanced, one for each face of the cube.

Note

Inherited properties

The location, orientation, and scale of the instanced child(ren) matches that of the faces of the parent. So, if several objects are parented to the cube, they will all be instanced once for each face on the cube. If the cube is subdivided, every child will be instanced for each face on the cube.

Both the parent object and original are displayed as editable "templates" in 3D Viewport, but neither is rendered.

### Scale

| Scale enabled. | Top face of cube scaled down. |

By enabling Scale for the parent object, the scale of the child objects will be adapted to the size of each face in the parent object.

Thus, by rescaling the face of the parent object, the size of the instanced object will change accordingly.

### Limitations/Considerations

The positioning of the instanced geometry relative to the face is dependent upon the position of the child objects relative to the instancer's origin. This can lead to some visual artifacts in the 3D Viewport as the geometry of the original objects overlaps or intersects with the instanced geometry. One workaround is to move the origin of the instancer mesh off of the plane of the faces.

If the geometry of the children is not symmetrical then the orientation of the face (as determined by the order of its vertices) could matter. As of 2.70 Blender does not have tools which allow you to adjust the ordering of the vertices on a face.

However, there is a workflow that lets you control for this. Make a single square and enable the Instancing Faces so you can see the instanced geometry in the 3D Viewport. If the orientation is not what you want, rotate the face until it is how you want. Typically you want to do the rotation in Edit Mode, not Object Mode, but this is not a hard rule.

Once you have the orientation correct, Duplicate the face and move the duplicate where you want it. Repeat this process until you have enough faces. Since it is common for these faces to butt up against one another, your geometry will have lots of duplicate vertices. Use the Merge by Distance button in the Tools panel.

Demo Video

A short video illustrating this workflow

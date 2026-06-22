# Brush Settings, Brush Asset, Color, Drawing Tools ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Brush Settings; Brush Asset; Color; Drawing Tools; Arc Tool; Box Tool; Brush Tool; Circle Tool.

## Brush Settings

### Brush Settings

Material
Data-block selector for the material. The Erase tool is the lone exception.

/ Pin Material
Pin the material to the brush.

Strokes end up looking the way they do because of how the brush and material work together; binding the material to the brush hands you tighter control and heads off any mismatch between the two.

**Brush Settings.**

A Brush panel shows in the Toolbar during Vertex Paint Mode.

Brush — picks a preset Brush configuration from the Data-Block menu; generate original presets as desired.

Radius — governs the brush footprint in pixels. F enables interactive resizing by moving and clicking LMB (the brush texture displays inside the circle); input a value then press enter while in F mode for numerical entry.

(Size Pressure) — modulates radius by stylus force when a Graphics Tablet is active.

Strength — governs the potency of each brush application.

(Strength Pressure) — modulates strength by stylus force.

Mode:
- Stroke: apply color only to stroke outlines.
- Fill: apply color only to fill zones.
- Stroke & Fill: apply to both.

Cursor — reference global brush settings for Cursor documentation.

**Color Picker.**

The brush hue; see Color Picker documentation.

Note: Vertex Paint functions in sRGB color space; RGB values differ when comparing paint tools and linear-space materials.

**Color Palette.**

The current Color Palette in use; see Color Palette documentation.

**Falloff.**

Reference global brush settings for Falloff configuration.

### Brush Settings

Each mode and brush has unique brush settings. But there is also a lot of overlap or similar settings. This page explains general and mode specific settings that are used across various brushes in more detail.

Changes to the settings of a brush asset are temporary and will be discarded when Blender is closed. To preserve settings, save them to the currently active brush asset using Save Changes to Asset , or create a new brush asset using Duplicate Asset , see Asset Operators. Loading a different file while Blender remains open does not discard the settings.

### Unified Settings

Some settings (e.g. size, strength, color), indicated with , allow for using a per-mode setting instead of the individual brush setting. These settings are shared across all brushes of a given mode (e.g. Sculpt Mode) but do not overwrite the individual brush value.

### General

Size
This option controls the size of the brush, measured in pixels. F allows you to change the brush size interactively by dragging the mouse from left to right and then LMB to accept. Meanwhile the texture of the brush will be visible inside the circle. You can also enter the size numerically with the number keys.

The size can be decreased/increased using [ and ] respectfully.

(Size Pressure)
Adjusts the size based on the stylus pressure when using a Graphics Tablet.

(Use Unified Size)
Use the same brush Size across all brushes.

/ (Expand/Collapse)
Show or hide the customizable pressure curve.

Custom Curve
By default this is a straight line with positive slope such that increased pressure results in a larger brush size.

For the curve controls see: Curve widget.

Size Unit Sculpt Mode
Controls how the brush Size is measured.

View :

The Size is measured based on how the cursor appears on the monitor i.e. "screen space".

Scene :

The Size is measured based on real world units. This means that the brush size stays consistent, independently from zooming in and out in the viewport. The unit type and scaling can be configured in the Scene Units.

Strength
For painting brushes the Strength defines the maximum effect of each brush stroke. For example, higher values cause a Paint brush to give each stroke a higher opacity. The opacity is never stronger than the set Strength , no matter how often the same surface is painted during the same stroke.

For sculpting brushes on the other hand the Strength relates to how strong each step of the stroke is, resulting in a slower/faster buildup towards the full brush effect during the stroke.

You can change the brush strength interactively by pressing Shift - F and then moving the brush and then LMB . You can also enter the strength numerically with the number keys.

(Strength Pressure)
Adjusts the strength based on the stylus pressure when using a Graphics Tablet.

(Use Unified Strength)
Use the same brush Strength across all brushes.

/ (Expand/Collapse)
Show or hide the customizable pressure curve.

Custom Curve
By default this is a straight line with positive slope such that increased pressure results in a stronger brush deformation.

For the curve controls see: Curve widget.

Blend
Set the way the color or value is applied over the targeted Color Attribute, Vertex Group or Image Texture. See Color Blend Modes.

- Add Alpha: makes the image more opaque where painted.

- Erase Alpha: makes the image transparent where painted, allowing background colors and lower-level textures to show through. As you "paint", the false checkerboard background will be revealed. Using a tablet pen's eraser end will toggle on this mode.

Tip

In order to see the effects of the Erase and Add Alpha mix modes in the Image Editor, the Display Channels must be set to Color & Alpha or Alpha . Transparent (no alpha) areas will then show a checkered background.

Weight Weight Paint
The weight value that is applied to the vertex group.

Use Shift - X to sample the weight value of clicked vertex. Shift - Ctrl - X lets you select the group from which to sample from.

Direction Ctrl Sculpt Mode
Brush direction toggle, Add raises geometry towards the brush, Subtract lowers geometry away from the brush. This setting can be toggled with Ctrl while sculpting.

Normal Radius Sculpt Mode
Determines the ratio of how much the brush radius is used to sample the normal direction of the sculpt plane of the brush. For example, a smaller Normal Radius will lead to drastic changes in the brush orientation, like for following the contours of hard surface meshes more closely. A large Normal Radius will lead to smoother changes in orientation, like for building overall forms on organic sculptures.

Area Radius
The ratio between the brush radius and the radius that is going to be used to sample the area plane depth.

Tilt Strength Sculpt Mode
Determines how much the tilt of the user's tablet pen affects the brush normal. Negative values correspond to inverting the direction of the tilt.

Hardness Sculpt Mode
How close the brush falloff starts from the edge of the brush.

Tip Roundness
The factor to control how round the brush is. A value of zero will make the brush square. Note, the Brush Falloff is only applied to the rounded portions of the brush.

Auto-smooth Sculpt Mode
Sets the amount of smoothing to be applied to each stroke.

Topology Rake Sculpt Mode
The higher this setting is set, the more Dyntopo aligns mesh edges to the brush direction while tessellating the surface. This generates cleaner edge flow to help define sharp features. Topology Rake can have a severe performance impact so it works best on low-poly meshes.

Normal Weight Ctrl Sculpt Mode
Constrains brush movement along the surface normal. Especially useful with the Grab brush, can be temporarily enabled by holding Ctrl . E.g. Grab brush can be used to push a depression (hole) into the mesh when Normal Weight is set.

Applies to Grab and Snake Hook brushes.

Plane Offset Sculpt Mode
Offset for planar brushes (Clay, Fill, Flatten, Scrape), shifts the plane that is found by averaging the faces above or below.

Plane Trim Sculpt Mode
Ability to limit the distance that planar brushes act. If trim is enabled vertices that are further away from the offset plane than the trim distance are ignored during sculpting.

Pinch/Magnify Sculpt Mode
Pushes the mesh towards/away from the brush center during the stroke.

Deformation Target
How the deformation of the brush will affect the object.

Geometry :

Deform the geometry directly.

Cloth Simulation :

Deform the mesh while a cloth simulation is applied to it at the same time.

### Advanced

Brush Type
Defines the basic behavior and the available settings. Through the settings of a brush type, brushes can be created that produce vastly different effects.

The Essentials asset library contains brushes for each of the brush types. Their preview image and description should give a good idea of the effect the brush produces, with the particular combination of brush type and settings. Because of this, they are usually the more useful starting point for custom brushes than the mere brush type is, which is why the brush type is part of the Advanced brush settings.

Brushes and Brush Types of each mode:

- Sculpt

- Vertex Paint

- Weight Paint

- Texture Paint

Accumulate
Causes stroke dabs to accumulate on top of each other.

Front Faces Only
When enabled, the brush only affects vertices that are facing the viewer.

Affect Alpha 2D Painting Only
When this is disabled, it prevents changes to the alpha channel while painting (Only in 3D Viewport).

Anti-Aliasing 2D Painting Only
Toggles Anti-Aliasing around the brush, this is useful if you are working with pixel art or low resolution textures.

Auto-Masking Sculpt Mode
The auto-masking toggles in the brush settings are the same as the sculpt mode auto-masking settings. The difference is that these toggles can be customized per brush to create specific brush behaviors.

See also

For more information on the Auto-Masking toggles, see Auto-Masking.

Sculpt Plane Sculpt Mode
Use this menu to set the plane in which the sculpting takes place. In other words, the primary direction that the vertices will move.

Area Plane :

The movement takes place in the direction of average normal for all active vertices within the brush area. Essentially, this means that the direction is dependent on the surface beneath the brush.

View Plane :

Sculpting in the plane of the current 3D Viewport.

X, Y, Z Plane :

The movement takes place in the positive direction of one of the global axes.

Original Sculpt Mode

Normal
When locked it keeps using the normal of the surface where stroke was initiated, instead of the surface normal currently under the cursor.

Plane
When locked keep using the plane origin of surface where stroke was initiated, instead of the surface plane currently under the cursor.

### Color Picker

Color

Brushes have two colors that can be set using the Color Picker:

- Primary Color : The active color used for painting by default.

- Secondary Color : An alternate color that can be quickly accessed.

By default, painting uses the primary color. The secondary color can be used temporarily by holding Ctrl while painting. The two colors can also be swapped at any time using Swap Colors.

Tip

- Press Shift - X to sample a color at the mouse cursor position.

- Press Shift - Ctrl - X to sample the merged viewport color , including lighting, shading, and all visible layers.

The sampled color becomes the primary color of the active Paint brush.

(Swap Colors) X
Swaps the primary and secondary colors.

(Use Unified Color)
Use the same brush color across all brushes.

Note

Note that Vertex Paint works in sRGB space, and the RGB representation of the same colors will be different between the paint tools and the materials that are in linear space.

Gradient

A gradient can be used as a color source.

Gradient Colors
The Color Ramp Widget to define the gradient colors.

Mode

Pressure :

Will choose a color from the color ramp according to the stylus pressure.

Clamp :

Will alter the color along the stroke and as specified by Gradient Spacing option. With Clamp it uses the last color of the color ramp after the specified gradient.

Repeat :

Similar to Clamp . After the last color it resets the color to the first color in the color ramp and repeats the pattern.

### Randomize Color

Applies random variation to the brush color for more natural and varied strokes. Useful for hand-painting textures or adding subtle irregularities.

The randomness can affect hue, saturation, and value independently. Each channel also supports pressure sensitivity and stroke-based randomness.

Hue
Amount of random variation applied to the hue of the brush color.

(Stroke Random)
Apply a single random hue per stroke instead of varying continuously during the stroke.

(Use Pressure)
Modulate hue variation based on pen pressure.

Saturation
Amount of random variation applied to the saturation of the brush color.

(Stroke Random)
Apply a single random saturation per stroke instead of varying continuously during the stroke.

(Use Pressure)
Modulate saturation variation based on pen pressure.

Value
Amount of random variation applied to the value (brightness) of the brush color.

(Stroke Random)
Apply a single random value per stroke instead of varying continuously during the stroke.

(Use Pressure)
Modulate value variation based on pen pressure.

### Color Palette

Color Palettes are a way of storing a brush's color so that it can be used at a later time. This is useful when working with several colors at once.

Palette
A Data-Block Menu to select a palette.

(New Pallet Color)
Adds the current brush's primary Color to the palette.

(Delete Pallet Color)
Removes the currently selected color from the palette.

/ (Move Pallet Color)
Moves the selected color up/down one position.

(Sort By)
Sort Colors by Hue, Saturation, Value, Luminance.

Color List
Each color that belongs to the palette is presented in a list. Clicking on a color will change the brush's primary Color to that color.

## Brush Asset

### Brush Asset

Brush data-block panel.

Brush
The Data-Block Menu to select a preset brush type or a custom brush.

Add Brush
Add a brush and it arrives as a clone of the one you have now.

Brush Specials

Reset Brush
Return the current brush to its factory defaults.

Reset All Brushes
Return every brush to its factory defaults.

Custom Icon
Lets you assign a custom icon to the brush.

Image Path
Points to the image file serving as the custom icon.

Note

Saving a custom brush in a blend-file means switching on Fake User .

### Brush Types

### Draw Brushes
Draw brushes are the dedicated brush type that drives Grease Pencil drawing tools. Swap brushes from the Tool Settings. Pencil, Ink, marker, and the rest are really just setting variations on one shared Draw Brush . Build as many brushes as you like, each tuned differently to chase a distinct artistic look while drawing.

### Fill Brushes
Fill brushes are the dedicated brush type that drives the Grease Pencil Fill tools. Swap brushes from the Tool Settings. The various fill brushes are setting variations on a single shared Fill Brush . Build as many brushes as you like, each tuned differently for a distinct result when filling areas.

### Erase Brushes
Erase brushes are the dedicated brush type that drives the Grease Pencil Erase tools. Swap brushes from the Tool Settings. Soft and hard erasers are setting variations on one shared Erase Brush . Build as many brushes as you like, each tuned differently for distinct erasing effects. The Erase Brush also carries two more special eraser types: point and stroke.

## Color

### Color

Paint Mode
Sets where the stroke color comes from. Pin the mode to the brush by switching on the Pin icon in the Tool Settings header.

Material :

Use the stroke/fill base color material.

Color Attribute :

Use Color Attribute.

Color Picker
Sets the primary brush color.

Color, Secondary Color
The color of the brush. See Color Picker.

Mode
The color transformation lands on the stroke color, the fill color, or both.

Stroke :

Only paint over strokes.

Fill :

Only paint over fill areas.

Stroke & Fill :

Paint over strokes and fill areas.

Mix Factor
Mixing factor between the selected color and the base material color.

### Palette

Active Color Palette. See Color Palette.

Color — Stroke Appearance

This tab controls stroke color.

Line Style: Color.

Base Color
Stroke color for this line style.

### Modifiers

### Common Options

Mix
Blend modifier output with the base property via standard methods (e.g., Mix compositing node).

Influence
Modifier effect magnitude on the current property.

Color Ramp
Each modifier employs a color ramp mapping the property to stroke color.

### Types

- Along Stroke
- Crease Angle
- Curvature 3D
- Distance from Camera
- Distance from Object
- Material
- Noise
- Tangent

## Drawing Tools

### Drawing Tools

Cursor
Reposition the 3D Cursor.

Brush
The tool that runs any of the drawing brushes.

Erase
Wipe out strokes.

Fill
Flood closed stroke regions automatically.

Box
Lay down rectangles.

Circle
Lay down ovals.

Line
Lay down straight lines.

Polyline
Lay down several straight segments.

Arc
Lay down basic arcs.

Curve
Lay down elaborate Bézier-style curves.

Trim
Slice strokes where they cross others.

Eyedropper
Builds new materials or palette colors from colors sampled out of the 3D Viewport.

Interpolate Ctrl - E
Drops a breakdown keyframe in between two ordinary keyframes for you.

## Arc Tool

### Arc Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Arc

Simple arcs, drawn with any Draw type brush, are what the Arc tool produces.

### Tool Settings

The brush's core settings sit right in the Tool Settings for handy access; Draw Brush documents that configuration.

Subdivisions
Count of stroke points placed along each edge of the stroke.

Thickness Profile
A curve widget governs how thick the stroke runs from its left start to its right end.

Use Curve
Enable it to let a curve profile steer thickness along the arc.

### Brush Asset
Chooses which brush asset the tool draws with.

See Brush Asset for more information.

See Draw Brushes for a detailed list of all draw brushes and their options.

### Brush Settings
Parameters shaping how the stroke looks.

See Draw Brushes for details.

### Color
Settings that fix the stroke color.

See Color

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. Arc relies on Draw Brush types. Brush Settings has more.

### Creating Arcs

- Press down with LMB (or the Pen tip) where the shape begins, then drag.

- Let go at the spot where it should finish.

- Once released, a single cyan manipulator (hand icon) lets you adjust the arc.

- Then confirm ( Return / MMB ) or cancel ( Esc / RMB ).

Mid-drag, Shift locks a perfect arc, Alt builds the arc outward from a center, and M flips it.

NumpadPlus and NumpadMinus or the mouse Wheel raise or lower how many points end up in the arc.

F tunes line thickness; Shift - F tunes stroke opacity.

| click and dragging the start point.  | Tweaking arc with the manipulator.  | The arc after confirming.  |

### Extruding
Ahead of confirming, E drags the arc's end point outward so you can chain arcs together.

| End point extruding.  | Tweaking the last arc with the manipulator.  | The connected arcs after confirming.  |

## Box Tool

### Box Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Box

Rectangular shapes are what the Box tool produces.

### Tool Settings

The brush's core settings sit right in the Tool Settings for handy access; Draw Brush documents that configuration.

Subdivisions
Count of stroke points placed along each edge of the stroke.

Thickness Profile
A curve widget governs how thick the stroke runs from its left start to its right end.

Use Curve
Enable it to let a curve profile steer thickness along the line.

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. Box relies on Draw Brush types. Brush Settings has more.

### Creating Boxes

- Press down with LMB (or the Pen tip) where the shape begins, then drag.

- Let go at the spot where it should finish.

- Once released, drag the yellow manipulators to reposition either the start or the end point.

- Then confirm ( Return / MMB ) or cancel ( Esc / RMB ).

Mid-drag, Shift locks a perfect square while Alt builds the box outward from a center.

NumpadPlus and NumpadMinus or the mouse Wheel raise or lower how many points end up in the box.

F tunes line thickness; Shift - F tunes stroke opacity.

| click and dragging the start point.  | Moving start and end points with manipulators.  | The box after confirming.  |

## Brush Tool

### Brush Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Brush

A tool for free-form drawing of Grease Pencil strokes with any of the Draw type brushes.

Tip

Firing up a brush asset from an asset shelf or brush selector also flips on this tool for convenience.

### Tool Settings

### Brush Asset
Chooses which brush asset the tool draws with.

See Brush Asset for more information.

See Draw Brushes for a detailed list of all draw brushes and their options.

### Brush Settings
Parameters shaping how the stroke looks.

See Draw Brushes for details.

### Eraser
Default Eraser Brush
Pick a brush to serve as eraser; Ctrl - LMB then jumps to it quickly from the main brush.

### Color
Settings that fix the stroke color.

See Color

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. The Draw tool relies on Draw Brush types. Brush Settings has more.

### Free-hand Drawing
Hold LMB or the pen tip to sketch freely across the viewport.

### Stabilize Stroke
Shift - LMB flips Stabilize Stroke on for the brush, lending extra control while drawing and producing cleaner lines.

### Straight Lines
Alt - LMB forces each stroke onto a straight horizontal or vertical track.

### Switching to the Erase Tool
Ctrl - LMB momentarily hands you the active Erase tool. Erase Tool has more.

B also clears every point inside the chosen drawing region.

## Circle Tool

### Circle Tool

Reference

Mode :

Draw Mode

Tool :

Toolbar ‣ Circle

Oval shapes, drawn with any Draw type brush, are what the Circle tool produces.

### Tool Settings

The brush's core settings sit right in the Tool Settings for handy access; Draw Brush documents that configuration.

Subdivisions
Count of stroke points placed along each edge of the stroke.

Thickness Profile
A curve widget governs how thick the stroke runs from its left start to its right end.

Use Curve
Enable it to let a curve profile steer thickness along the line.

### Brush Asset
Chooses which brush asset the tool draws with.

See Brush Asset for more information.

See Draw Brushes for a detailed list of all draw brushes and their options.

### Brush Settings
Parameters shaping how the stroke looks.

See Draw Brushes for details.

### Color
Settings that fix the stroke color.

See Color

### Usage

### Selecting a Brush and Material
Within the Tool Settings, choose the brush, material, and color type the tool should use. Circle relies on Draw Brush types. Brush Settings has more.

### Creating Circles

- Press down with LMB (or the Pen tip) where the shape begins, then drag.

- Let go at the spot where it should finish.

- Once released, drag the yellow manipulators to reposition either the start or the end point.

- Then confirm ( Return / MMB ) or cancel ( Esc / RMB ).

Mid-drag, Shift locks a perfect circle while Alt builds the circle outward from a center.

NumpadPlus and NumpadMinus or the mouse Wheel raise or lower how many points end up in the circle.

F tunes line thickness; Shift - F tunes stroke opacity.

| Click and dragging the start point.  | Moving start and end points with manipulators.  | The circle after confirming.  |

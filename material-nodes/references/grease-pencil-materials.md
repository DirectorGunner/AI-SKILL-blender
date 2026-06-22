# Grease Pencil Materials, Grease Pencil Material Properties, Draw Brushes, Tint Brush

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Grease Pencil Materials; Grease Pencil Material Properties; Draw Brushes; Tint Brush.

## Grease Pencil Materials

### Grease Pencil Materials

Strokes are what Grease Pencil objects are made of. Any stroke can carry a stroke (outline) part, a fill part, or both, and Grease Pencil materials decide how those parts look.

A stroke points to one material data-block, and inside it the Stroke and Fill parts are set up on their own. So a stroke and its fill may run off a single shared material while still having their visual settings dialed in separately within it.

A material sets the base color, texture, and shading for both the stroke outline and the filled region.

The list always holds exactly one active material, the selected entry. New strokes you draw take that active material.

Override the base material color with the tools in Vertex Mode, or with the Draw and Tint tool over in Draw Mode.

A material stays bound to its strokes, so editing it updates every stroke that uses it on the spot.

Same stroke linked to different materials.

### Material Shader

To render stroke outlines and fills, Grease Pencil materials lean on a purpose-built shader.

Two independent sections make up the material:

Stroke
Governs how the outline looks, that is line color, thickness shading, and stroke textures.

Fill
Governs how enclosed areas look. Fill only reaches regions bounded by closed strokes, where the start and end points join up.

A checkbox in each panel header turns either part on or off independently.

Note

This is no ordinary BSDF shader. You set up the Grease Pencil shader in the Material Properties panel, and it sits apart from the Shader Editor node system.

### Setting Up Materials

Reference

Mode :

Drawing Mode

Panel :

Material ‣ Material Slots

Shortcut :

U

Just like any other Blender material, Grease Pencil materials get created and handled from the Material properties. Material assignment covers general usage.

Flip the 3D Viewport to Material Preview or Rendered shading for a live look at materials as you work.

Being data-blocks, Grease Pencil materials can be assigned across one or many objects, and a single object can mix different materials on different strokes.

A stroke's final look in Grease Pencil comes from the brush settings paired with the chosen material.

Material slots add further controls for handling and switching materials mid-draw or mid-edit.

### Properties

### Material Slots

### Surface

### Settings

## Grease Pencil Material Properties

### Grease Pencil Material Properties

How strokes and fills render is what Grease Pencil materials set. Each stroke points at a single material, and that material keeps separate Stroke and Fill settings inside it.

From the Material Properties panel you handle material slots, toggle visibility and locking, and dial in the look of stroke and fill shading.

### Material Slots

Grease Pencil material slots panel.

Material slots are how materials get attached to the Grease Pencil object, and every stroke keeps a reference to one of them.

Newly drawn strokes use the active material, while existing strokes hold onto their assigned material until you change it by hand.

Beside each material name sit controls for the usual visibility and editing toggles:

/ (Show/Hide in Ghosts)
Sets whether the material appears in Onion Skinning previews.

/ (Hide/Show Material)
Flips viewport visibility for strokes drawn with this material.

/ (Lock/Unlock Material)
Stops strokes using this material from being edited in Edit Mode.

### Specials

A set of operators for handling visibility and locking across many materials at once:

Show All
Make every material visible.

Hide Others
Conceal every material apart from the active one.

Lock All
Lock the whole set against editing.

Unlock All
Free the whole set for editing.

Lock Unselected
Lock any material the selected strokes do not use.

Lock Unused
Lock and conceal any material no stroke is assigned to.

Copy Material to Selected
Push the active material onto the selected Grease Pencil objects.

Copy All Materials to Selected
Push every material slot onto the selected Grease Pencil objects.

Remove Unused Slots
Clear out slots that no stroke is assigned to.

### Lock & Visibility Controls

(Isolate Material)
Lock everything else so editing is confined to the active material.

(Isolate Material)
Conceal everything else so only the active material shows.

### Surface

Shader panel with only Stroke component enabled.

The look of strokes and fills falls to the Surface panel, where each material splits into two independent components:

- Stroke – Drives how the outline renders.

- Fill – Drives how the interior of closed strokes renders.

Each component can be enabled or disabled independently.

### Stroke

The Stroke component decides how the line itself is rendered.

Line Type
Picks the way stroke geometry is drawn.

Line :

A solid line links the stroke points together.

Dots :

Plants a circle at every stroke point, leaving them unjoined.

Squares :

Plants a square at every stroke point, leaving them unjoined.

Style
Sets the stroke's shading.

Solid :

A single flat base color.

Texture :

An image texture wrapped along the stroke.

Image
The image data-block feeding the texture.

Blend
Mix factor between the texture and the Base Color.

UV Factor
Scales the texture across the stroke's length.

Base Color
The stroke's main color.

Holdout
Makes the stroke behave as a mask, cutting color from any strokes and fills below.

Alignment
Sets how Dots and Squares are oriented.

Path :

Follows both the drawing direction and the object's rotation.

Object :

Follows the object's rotation alone.

Fixed :

Locks to screen space.

Rotation
Turns the Dots or Squares shapes, held within -90° to 90°.

Self Overlap
Decides how a stroke's own overlapping parts blend, an effect most visible on semi-transparent materials.

| Line / Solid  | Line / Texture  | Dot / Solid  | Dot / Texture  |

### Fill

The Fill component takes care of rendering closed stroke regions.

Style
Sets the fill's shading.

Solid :

One flat base color.

Gradient :

A blend running between two colors.

Gradient Type

Linear :

Blends along one axis.

Radial :

Blends outward from a center point.

Texture :

An image texture.

Image
The image data-block feeding the fill texture.

| Solid  | Gradient (Linear)  | Gradient (Radial)  | Texture  |

Base Color
Primary fill color.

Secondary Color Gradient
Secondary color used for gradients.

Holdout
Turns the fill into a mask that strips color from the strokes beneath it.

Blend Gradient / Texture
Controls mixing between Base Color and the gradient or texture.

Flip Colors Gradient
Swaps Base and Secondary colors.

Location X, Y Gradient / Texture
Offsets gradient or texture coordinates.

Rotation Gradient / Texture
Rotates the gradient or texture mapping.

Scale X, Y Gradient / Texture
Scales the gradient or texture mapping.

Clip Image Texture
Prevents texture tiling when enabled.

### Settings

Pass Index
A custom integer ID you can feed into modifiers and compositing. It lets you single out specific materials within Grease Pencil Modifiers.

## Draw Brushes

### Draw Brushes

Reference

Mode :

Draw Mode

Brush :

Asset Shelf ‣ Draw

Free-hand strokes are what the Draw brush is for.

### Brush Settings

Material
The material's data-block selector.

Size
Brush radius measured in pixels.

Tap F to resize on the fly by dragging the pointer, or punch in a number and confirm.

(Size Pressure)
With a Graphics Tablet, stylus pressure steers the radius, and a curve widget shapes that pressure response.

Strength
Governs stroke transparency (alpha), spanning fully transparent (0.0) through fully opaque (1.0).

Set strength live with Shift - F in the 3D Viewport, moving the pointer and clicking LMB ; a typed value works as well.

(Strength Pressure)
With a Graphics Tablet, stylus pressure steers the strength, and a curve widget shapes that pressure response.

Stroke Mode
Picks which part of the Grease Pencil material a draw touches.

Stroke :

Touches only the material's stroke (outline) part; the fill is left untouched.

Fill :

Touches only the material's fill part; no outline is drawn.

Both :

Touches both stroke and fill parts of the material while creating or editing strokes.

Caps Type
Shape given to the stroke's two ends.

Round :

Strokes begin and end on a rounded cap.

Flat :

Strokes begin and end on a flat cutoff.

### Advanced

Spacing
Sets the smallest gap allowed between stroke points, given as a percentage of the brush size.

Low spacing pays off during fast strokes. A quick movement would ordinarily yield few samples and wide gaps; dropping the spacing percentage forces extra points so the minimum gap holds.

Draw slowly and the points already come thick, so the spacing setting adds nothing new. It merely guarantees a minimum gap and never deletes points.

Active Smooth
Number of smoothing passes applied to the stroke as you draw.

Angle
Heading of the input device that yields the thickest stroke (0° means horizontal).

Factor
How much thickness drops off when the stroke runs perpendicular to the Angle value.

Hardness
Alpha falloff from a point's edge in toward its center. Only takes effect with stroke materials of Dot or Box style.

Aspect X, Y
Sets the width and height of the alpha gradient.

### Stroke

#### Post-Processing
Steps that fire on the strokes the moment you finish, right as the LMB or Pen tip lifts. Toggle the whole set with the checkbox in the section panel header.

Smooth
How strongly point positions get smoothed along the stroke.

Iterations
Count of smoothing passes run over the stroke.

Subdivision Steps
Count of subdivisions added to freshly made strokes.

Simplify
Trims the final point count via an adaptive algorithm.

Trim Strokes End
Clips intersecting stroke ends on its own.

Outline
Switches on conversion of a freshly made stroke into its outline.

Material
The material the outline stroke uses.

Thickness
The thickness the outline stroke uses.

#### Randomize
Throws the stroke's points around for a randomized feel. The checkbox in the section panel header toggles Randomize.

Radius
How far randomness leans on the input device's pressure.

Strength
How far randomness reaches the stroke's strength value (alpha).

UV
How far randomness reaches the UV rotation.

Hue, Saturation, Value
Scatters the hue, saturation, and value of the stroke's Color.

Jitter
How much jitter gets mixed into the stroke.

Common Options

Stroke Random
Use randomness only at stroke level.

Use Pressure
Stylus pressure drives the effect's strength, and a curve widget shapes the pressure response.

#### Stabilize Stroke
By holding back and nudging point placement, Stabilize Stroke cuts jitter out of your strokes as you draw. Toggle it with the checkbox in the section panel header.

Radius
Smallest distance from the last point before the stroke carries on.

Factor
A smoothing factor; raise it for smoother strokes, though drawing starts to feel as if you are dragging the stroke behind you.

### Cursor

The checkbox in the Cursor header turns the cursor off.

Show Fill Color while Drawing
Displays, in the viewport, the material color the brush is bound to.

## Tint Brush

### Tint Brush

Reference

Mode :

Draw Mode

Brush :

Brush ‣ Tint

With the Tint brush you paint over stroke points, blending the material base color into a color you pick.

### Brush Settings

Mode
Sets how Color Attributes reach the strokes.

Stroke and Fill :

Color Attributes affects both the Stroke and Fill materials.

Stroke :

Color Attributes affects the Stroke material only.

Fill :

Color Attributes affects the Fill material only.

### Usage

### Selecting a Brush, Color & Mode
Head to the Tool Settings and pick the brush, color, and mode for the tool.

For convenience the brush's main settings are surfaced right in the Tool Settings. Vertex Paint Brush covers configuration and settings for the vertex paint brushes.

Ctrl - LMB erase the Color Attribute.

### Painting
Hold LMB or use the pen tip to paint over the stroke points.

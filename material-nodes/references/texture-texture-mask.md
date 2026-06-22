# Texture Texture Mask, Mesh Sculpt Brush Assets, Clay Thumb, Draw ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Texture & Texture Mask; Mesh Sculpt Brush Assets; Clay Thumb; Draw; Grab; Face Sets; Brushes; Mask; Options.

## Texture & Texture Mask

### Texture & Texture Mask

This page covers both the Texture and Texture Mask panels. Add a Texture to the brush to control the color of the brush. A Texture Mask is used to control the strength of the brush. Both the Texture and Texture Mask offer the same settings.

Example of the Texture panel and a textured brush in use.

Texture
In paint modes the texture is used as a color source, while for sculpting it is used to determine the strength of the brush.

Any image texture or procedural texture can be assigned in the texture and texture mask panels. Textures can be further edited in the properties editor (Click the properties icon for quick access)

Tip

It's recommended to load all needed images ahead of time as image textures into Blender. Then they can be easily selected by clicking on the texture and picking it from the data-block popup. Textures can also be appended/linked from other Blender files.

Mapping & Mask Mapping
How the texture is applied to the brush stroke.

Tip

It is recommended to set this to Area Plane or View Plane for the most common behavior. Ideally match this setting with the Sculpt Plane setting if in sculpt mode.

View Plane :

If View Plane is enabled, the current viewing angle is used to project the brush texture onto the model. This is especially useful for projection painting.

Area Plane :

Projects the brush texture along the local surface normal, which keeps the texture from stretching on steep angles. This is an ideal default for most brushes.

Tiled :

The Tile option repeats the texture across the screen, so moving the brush will not change where the texture is applied. The Tile option is most useful with tileable images, rather than procedural textures.

3D :

The 3D option allows the brush to take full advantage of procedural textures. This mode uses vertex coordinates rather than the brush location to determine what area of the texture to use.

This option is not available for the Texture Mask.

Random :

Picks a random texture coordinate to sample from for each step of the stroke.

Stencil :

This is the ideal option for stamping textures for projection painting. Stencil mapping works by projecting the texture from the camera space on the mesh or canvas. Painting is applied only inside the boundaries of the stencil. The stencil is displayed as a screen space overlay on the viewport. To transform the stencil texture use the following shortcuts (Hold Alt for the Texture Mask):

- Move RMB

- Scale Shift - RMB

- Rotate Ctrl - RMB

While using stencil scaling, X and Y are used to constrain the scaling to one axis. Pressing one of the buttons twice reverts to unconstrained scaling.

Image Aspect
Restore the aspect ratio of the original image to reset stretching introduce by scaling, (Image textures only.) This operator can use the tiling and scale values of the brush texture if the relevant are enabled in Adjust Last Operation panel.

Reset Transform
Restores the position of the stencil.

Pressure Masking
Only available for the Texture Mask. It allows to clip the mask result based on pressure.

Off :

Disabled.

Ramp :

Fades out the mask effect on higher pressure.

Cutoff :

Expands the used values from the image based on stylus pressure.

Angle Ctrl - F
This is the rotation angle of the texture brush. It can be changed interactively via Ctrl - F in the 3D Viewport. While rotating the angle via the hotkey you can enter a value numerically as well.

Rake
Texture angle follows the direction of the brush stroke. Useful for stamping textures repeatedly along the stroke. Not available with 3D , Tiled , or Stencil Mapping types. The shortcut is not available in Sculpt mode.

Random
Angle is randomized on each step of the stroke. Not available with 3D , Tiled , or Stencil Mapping types. The shortcut is not available in Sculpt mode.

Random Angle
Constraints the random deviation to a range.

Offset X, Y, Z
Offset the texture map placement in X, Y, and Z axes.

Size X, Y, Z
Set the scale of the texture in each axis.

Sample Bias Sculpt Mode
Value added to texture samples. This can be used if the mid-level of a height map is not correct.

Vector Displacement Sculpt Mode
Use the color channels to displace geometry in 3 vectors.

Note

This is only supported for the Draw brush with Area Plane mapping enabled.

## Mesh Sculpt Brush Assets

### Mesh Sculpt Brush Assets

This is a list of all provided 'Essentials' brush assets that come with Blender. These are based on various Brush Types which are mentioned for each brush.

### Add/Subtract Brushes

These brushes generally push vertices outwards and inwards and are the most customizable to achieve a wide variety of effects. They typically don't use a color in their thumbnail.

Draw

Brush Type: Draw

Shortcut: V

The standard brush for pushing vertices inwards and outwards from the surface direction.

Draw Sharp

Brush Type: Draw Sharp

Shortcut: Shift V

Same as Draw but with a much sharper Falloff. Useful for creating creases and sharp angles.

Clay
Brush Type: Clay

Similar to the Draw brush but with a flattening effect and subtle smoothing. Useful for polishing and building volumes.

Clay Strips

Brush Type: Clay Strips

Shortcut: C

The same as the Clay brush, but more aggressive with a square falloff. A common standard for building rough volumes.

Clay Thumb

Brush Type: Clay Thumb

The same as the Clay brush, but specifically for emulating the effect of running your thumb over surfaces. Pushes geometry in and sideways.

Layer
Brush Type: Layer

Draw with a fixed height. Useful for adding flat layers to a surface.

Inflate/Deflate

Brush Type: Inflate

Shortcut: I

Moves the mesh in multiple direction. Useful for inflating or shrinking surfaces and volumes.

Blob
Brush Type: Blob

Magnifies the mesh as you draw. Useful for an additional inflation effect on the stroke.

Crease Polish

Brush Type: Crease

Shortcut: Shift C

A Draw brush with a pinching effect. Useful for polishing existing creases or carefully creating new ones.

Crease Sharp
Brush Type: Crease

Much sharper and stronger Crease brush. Great for creating thin and deep pinches.

### Contrast Brushes

Recognizable by their red thumbnail and cursor. These brushes generally flatten or heighten the contrast of the surface.

Smooth

Brush Type: Smooth

Shortcut: S

Smooths out irregularities in the surface and shrinks volumes by averaging the vertices positions. An essential brush that is frequently used.

Flatten/Contrast
Brush Type: Plane

Pushes vertices to an average height to create a flat surfaces. Alternatively pushes them away from the center for more contrast.

Plateau
Brush Type: Plane

Similar to Flatten but with a locked orientation and depth to create a consistently flat surface.

Fill/Deepen
Brush Type: Plane

Pushes surfaces upwards towards a flat plane. Useful for filling in holes and crevices. Alternatively deepens existing holes when holding 'Ctrl'.

Scrape/Fill

Brush Type: Plane

Shortcut: Shift T

Pushes surfaces inwards. Alternatively fills surfaces while holding 'Ctrl'. This is the most common brush for flattening meshes.

Trim
Brush Type: Plane

Pushes surfaces inwards toward a locked direction. The depth can be defined by going deeper towards surfaces along the stroke.

Scrape Multiplane
Brush Type: Scrape Multiplane

Scrapes the mesh with two angled planes at the same time, producing a sharp edge between them.

### Transform Brushes

Recognizable by their yellow icon and cursor. These brushes generally move, pinch and magnify the mesh.

Pinch/Magnify

Brush Type: Pinch

Shortcut: P

Pulls vertices towards the center of the brush. Useful for polishing angles and creases. Alternatively pushes them away from the center.

Grab

Brush Type: Grab

Shortcut: G

Moves vertices along with the mouse. An essential brush for building shapes and adjusting proportions.

Grab 2D
Brush Type: Grab

Similar to Grab but with an infinitely projected falloff. Useful for grabbing broader shapes and giving a similar feel to using Liquify tools in image painting applications.

Grab Silhouette
Brush Type: Grab

Similar to Grab but only affects vertices with the normal facing sideways away from the view. Very useful for adjusting outer silhouettes of thin objects.

Elastic Grab
Brush Type: Elastic Deform

Used to simulate realistic deformations from grabbing of Elastic objects.

Elastic Snake Hook
Brush Type: Snake Hook

Similar to Elastic Grab but rotates affected geometry based on the stroke direction.

Snake Hook

Brush Type: Snake Hook

Shortcut: K

Pulls vertices along with the stroke to create long, snake-like forms. Geometry is rotated and magnified to allow continuous pulling. Much more useful while having Dyntopo enabled.

Pull
Brush Type: Snake Hook

Iteratively picks up and lets go of geometry like the Snake Hook, but much softer. Useful for subtle small scale deforming over longer strokes.

Thumb
Brush Type: Thumb

Same as Grab but moves vertices along the surface direction. Useful for preserving specific surfaces.

Pose
Brush Type: Pose

Simulating an armature-like deformations. Useful for quick posing and transformations.

Nudge
Brush Type: Nudge

Similar as Thumb but dynamically picks up vertices like the Snake Hook . Useful for nudging something along the mesh surface.

Twist
Brush Type: Rotate

Rotates vertices within the brush in the direction the cursor is moved.

Relax Slide
Brush Type: Relax Slide

Slides the topology of the mesh in the direction of the stroke while preserving the geometrical shape of the mesh. Alternatively smooths the mesh on 'Shift'. Also useful for redistributing topology where it is needed.

Relax Pinch
Brush Type: Relax Slide

Similar to the Relax Slide brush but pinches/relaxes geometry instead.

Boundary
Brush Type: Boundary

Transform specifically mesh boundaries with various deformations.

### Utility Brushes

No clear color assignment. These brushes are general purpose brushes or specific.

Density
Brush Type: Density

Cleans up geometry by collapsing short edges. Specifically for use with Dyntopo.

Mask

Brush Type: Mask

Shortcut: M

Paints a selection on parts of the mesh to be unaffected by other brushes. It is possible to temporarily toggle this brush with Alt - LMB , to temporarily toggle mask erasing use Ctrl - Alt - LMB ,

Draw Face Sets
Brush Type: Draw Face Sets

Paint new, smooth or extend existing Face Sets.

Erase Multires Displacement
Brush Type: Erase Multires Displacement

Remove displacement information on a Multiresolution modifier.

Smear Multires Displacement
Brush Type: Smear Multires Displacement

Smear displacement information on a Multiresolution modifier.

### Painting Brushes

Recognizable by their blue thumbnails. These brushes are used for painting color attributes within sculpt mode.

Airbrush
Brush Type: Paint

A soft round brush that builds up over time instead of stroke distance.

Blend Hard
Brush Type: Paint

Similar to Average brushes in other modes with a hard round falloff. Used to blend colors along the stroke.

Blend Soft
Brush Type: Paint

Same as Blend Hard but with a soft round falloff.

Blend Square
Brush Type: Paint

Same as Blend Hard but with a hard square falloff.

Blur
Brush Type: Paint

Smooths painted colors; softening transitions and reducing sharp color differences.

Paint Blend
Brush Type: Paint

A mix of a Paint and Blend brush. On low pen pressure the brush averages colors and with high pen pressure it paints colors.

Paint Hard
Brush Type: Paint

A simple hard round falloff.

Paint Hard Pressure
Brush Type: Paint

A hard round falloff with pressure sensitivity for the brush size.

Paint Soft
Brush Type: Paint

A soft round falloff with pressure sensitivity for only the strength.

Paint Soft Pressure
Brush Type: Paint

A soft round falloff with pressure sensitivity for both size and strength.

Paint Square
Brush Type: Paint

A hard square brush falloff.

Sharpen
Brush Type: Smear

Pinches the colors inwards to create sharp edges or points.

Smear
Brush Type: Smear

Smears colors along the stroke.

### Simulation Brushes

These brushes are similar to regular brushes but with an additional cloth simulation applied. These are ideally used on a relatively low resolution, since the mesh density defines the size of cloth dynamics.

Drag Cloth
Brush Type: Cloth

Nudges the geometry along the surface while minimally affecting the overall shape of the object.

Push Cloth
Brush Type: Cloth

Pushes geometry inwards or outwards.

Grab Cloth
Brush Type: Cloth

Grabs geometry within the brush radius firmly, while surrounding geometry is being simulated to follow.

Grab Planar Cloth
Brush Type: Cloth

Similar to Grab Cloth but with a line as the brush radius instead of a circle.

Grab Random Cloth
Brush Type: Cloth

Similar to Grab Cloth but with a noise texture applied to create more random variation.

Inflate Cloth
Brush Type: Cloth

Inflates the geometry outwards or inwards.

Expand/Contract Cloth
Brush Type: Cloth

Creates compression or stretching on geometry.

Pinch Point Cloth
Brush Type: Cloth

Pinches geometry to the center point of the radius, creating folds from all sides.

Pinch Folds Cloth
Brush Type: Cloth

Pinches only from two perpendicular sides along the stroke direction, creating parallel folds along the stroke.

Bend/Twist Cloth
Brush Type: Pose

A pose brush that rotates geometry.

Stretch/Move Cloth
Brush Type: Pose

A pose brush that translates and scales geometry.

Bend Boundary Cloth
Brush Type: Boundary

Bend only open boundaries of the mesh, folding the surrounding geometry in the process.

Twist Boundary Cloth
Brush Type: Boundary

Twist open boundaries of the mesh, creating twisting folds.

## Clay Thumb

### Clay Thumb

Reference

Mode :

Sculpt Mode

Brush :

Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Similar to the Clay brush. It imitates the effect of deforming clay with the finger, accumulating material during the stroke. The sculpt plane tilts during the stroke in the front part of the brush to achieve this effect.

### Brush Settings

Note

More info at General brush settings and on Advanced brush settings.

## Draw

### Draw

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Moves vertices inward or outward, based on the average vertex normals within the brush radius.
Versatile, essential for most sculpting work.

This brush type commonly receives extensive customization for specialized applications.

### Brush Settings

Note

More info at General brush settings
and on Advanced brush settings.

### VDM Displacement

Vector Displacement Maps enable complex, undercut geometry insertion on the Draw brush.
Unlike standard displacement relying on a single channel,
this method employs all three color channels for three-axis repositioning.

Various VDM brushes applied to a polished head from reference material.

Access the reference file
to understand and experiment with this capability.

To activate, toggle Vector Displacement in the texture
controls. All stroke techniques work, though
Anchored is preferred.

Optimal source files are uncompressed EXR with unrestricted color range.

Note

Area Plane mapping alone is supported.

## Grab

### Grab

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Drag geometry following cursor; affects only initially-enclosed vertices. Core shaping tool.

Note

Similar to Edit Mode Proportional Editing,
except Grab leverages Sculpt Mode specifics and brush parameters.

### Brush Settings

### General

Size
Pressure Sensitivity not available for this brush. More info at Size.

Strength
Pressure Sensitivity not available for this brush. More info at Strength.

Normal Radius
Purely visual for this brush.
Does not affect functional behavior. More info at Normal Radius.

Auto-Smooth
Unsupported. More info at Auto-Smooth.

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Grab Active Vertex
Concentrates maximum force on the highlighted focal vertex,
simplifying manipulation of coarse or modified meshes.

Enabling reveals a white mesh preview within the radius.
Helps visualize true base geometry during modification.

Grab Silhouette
Maintains shape profile by only grabbing vertices on one side of the mesh curvature.
Silhouette orientation derives from viewport perspective and stroke initiation.

The image shows only the underside affected despite brush size.

Tip

Useful for isolating and deepening a single crease side.

### Additional Workflows

2D Grab Brush
Setting Falloff Shape to Projected
allows infinite depth reach through the viewport.
Valuable for sweeping large-scale adjustments.

Strokes originate beyond the mesh boundary (empty space)
and capture vertices within the radius.
Beneficial for flat and cylindrical forms.

## Face Sets

### Face Sets

Documents Face Set hotkey operators and menu actions available in sculpt mode.

Tip

Face Set pie menu at Alt - W.

### Face Set from Masked

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Face Set from Masked

Generates a Face Set from protected areas.

### Face Set from Visible

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Face Set from Visible

Generates a Face Set from visible geometry.

### Face Set from Edit Mode Selection

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Face Set from Edit Mode Selection

Generates a Face Set from Edit Mode selections.

### Initialize Face Sets

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Initialize Face Sets

Prepares all Face Sets at once leveraging one of multiple connectivity characteristics.

Mode
The connectivity characteristic defining Face Set divisions.

By Loose Parts:
One Face Set per unconnected component.

By Face Set Boundaries:
One Face Set per separated Face Set.
Good for dividing Face Set Expand
design into distinct Face Sets for modification.

By Materials:
One Face Set per Material assignment.

By Normals:
Face Sets matching comparable surface angles.

By UV Seams:
Face Sets utilizing UV divisions as splits.

By Edge Creases:
Face Sets utilizing Edge Crease marks as divisions.

By Edge Bevel Weight:
Face Sets utilizing Bevel marks as divisions.

By Sharp Edges:
Face Sets utilizing Sharpness marks as divisions.

Threshold
Baseline value for designating a characteristic as a split in Face Set generation.

### Grow/Shrink Face Sets

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Grow/Shrink Face Sets

Tool:
Edit Face Set

Shortcut:
Ctrl - W , Ctrl - Alt - W

Enlarges or diminishes the Face Set under the cursor by introducing or eliminating neighboring polygons.

### Expand Face Set

Note

Further data on Face Set Expand at the Expand section.

### Extract Face Set

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Extract Face Set

Constructs a separate mesh from the chosen Face Set.
Post-initiation, position over the target Face Set and LMB to build the fresh mesh.
Upon finishing the fresh mesh gets picked in Object Mode.

### Randomize Colors

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Randomize Colors

Generates fresh random coloration for Face Set rendering in the 3D Viewport.

### Display Settings

Reference

Mode:
Sculpt Mode

Popover:
Viewport Overlays – Sculpt ‣ Face Sets

Face Set presentation can be shown as a viewport display.
The overlay control allows brightness modification
to make Face Sets more or less apparent.

## Brushes

### Brushes

### Brush Types

Refer to Brush Type reference.

Below is a listing of accessible brush types paired with Essentials asset library brushes using those types.

Draw
Brushes: Paint Hard, Paint Soft, Paint Hard Pressure, Paint Soft Pressure, Erase Hard, Erase Soft, Erase Hard Pressure, Erase Pixel Art, Paint Pixel Art.

The foundational brush, deposits a line of pigmentation.

Soften
Brushes: Blur

Employs a "softening effect" to diminish or sharpen imagery.

Direction

Soften
Produces a blurring effect.

Kernel Radius (2D only)
Blur extent measured in pixels.

Sharpen
The Sharpen tool increases edge definition by heightening tonal contrast as you paint.

Sharp Threshold
Sets the minimum tonal gap required to trigger sharpening on pixels.

Kernel Radius (2D only)
Controls the sampling region size when computing that difference.

Blur Mode
Specifies which blur weighting approach to employ when calculating the softening operation.

Gaussian :

Gives more weight to pixels toward the center.

Box :

Weights all surrounding pixels equally.

Smear
Brushes: Smear

Gathers colors from beneath the cursor and mixes them along your brush motion. Comparable to the "smudge" capability in Gimp.

Clone
Brushes: Clone

Transfers pigmentation from a reference location to the active surface.

In 3D painting, set the clone source with Ctrl - LMB. In 2D mode, reposition by dragging with RMB.

Clone from Paint Slot (3D projective only)
Select a reference image instead of using the 3D reference position in the current image.

Source Clone Slot
Designate an image as the clone reference.

Image (2D only)
The reference image for cloning.

Alpha (2D only)
Transparency level of the clone image display.

Fill
Brushes: Fill

Fills sizable regions with a chosen color. Adjacent pixels resembling the clicked color receive application.

Fill Threshold (2D only)
Sets the color similarity needed for a pixel to receive the fill. Low values match only very comparable hues. Higher thresholds encompass a wider spectrum.

Gradient option via the Color Picker allows gradient filling.

Apply gradient using the Fill brush by pressing LMB and dragging to mark the gradient line, or radius for radial gradients (depending on Gradient Fill Mode).

Gradient Fill Mode
Linear, Radial

Note

Overrides

For 3D painting, certain choices bypass standard options to apply color to the mesh. This means hidden, rear-facing, and unculled faces always receive application, regardless of settings.

Mask
Brushes: Mask

Deposits grayscale values on the designated mask texture channel. Any masked regions resist other paint brush application, similar to sculpt masking.

Mask Value
The strength of the mask, where zero = unmasked and one = completely masked. Press Ctrl to reverse the value.

Tip

Simpler alternative is face selection masking. Consult Face Selection Masking for information.

### Brush Assets

### Pixel Art Brushes

Paint Pixel Art
Brush Type: Draw

Deposits specified pixels (Image Editor only).

Erase Pixel Art
Brush Type: Draw

Clears pixels in the transparency channel (Image Editor only).

## Mask

### Mask

Mask settings.

### Stencil Mask

Define an extra image texture that controls masked regions. Masked areas can be established with the Mask brush and resist painting.

Enable or disable the mask using the header checkbox.

Stencil Image
The image serving as the mask. See Data-Block Menu.

UV Layer
Choose the UV mapping for the mask image.

Display Color
The color shown in the viewport for the mask area. See Color Picker.

Invert
Reverses the masked region.

### Cavity Mask

Cavity masking restricts brush application where the surface contains cavities or protrusions, depending on mesh properties. This calculation operates on a per-vertex basis.

## Options

### Options

Bleed
Seam Bleed spreads pigmentation beyond UV boundaries to reduce visual interruptions (akin to bake bleed).

Dither
Adds color variation when painting 8-bit images.

Occlude
Activating geometry occlusion ensures only exposed (unobstructed by other mesh regions) pixels receive application. Stencils may also block specific zones.

Backface Culling
Enabling prevents painting rear-facing surfaces, restricting application to front-facing faces.

See also

Consult Brush Display settings.

### External

Screen Grab Size
Dimensions of the snapshot extracted for reapplication.

Quick Edit
Change a viewport snapshot in an exterior editing program.

Apply
Reproject the edited snapshot onto the mesh.

Apply Camera Image
Reproject an edited rendering from the primary camera onto the mesh.

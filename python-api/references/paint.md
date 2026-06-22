# Paint, Plane, Pose, Density ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Paint; Plane; Pose; Density; Relax Slide; Smear; Smooth; Snake Hook; Thumb; The Brush; Cloth Sculpting; Filters; General; Transforming; Options; Brush; Cloth Filter; Color Filter.

## Paint

### Paint

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Color the active attribute; Shift blurs colors.

Access color options via the palette control in the top toolbar.

Note

More information in the
Painting Introduction.

### Brush Settings

### General

Strength
Behaves distinctly on this brush.
Defines overall Color intensity rather than per-step magnitude.

Apply Flow instead for speed-controlled buildup.

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Flow
Hue applied per stroke interval.
Controls accumulation pace.

Wet Mix
Hue extracted from the surface into brush color.
Replicates wet-canvas behavior.

Wet Persistence
Hue retained by the brush post-application.

Wet Paint Radius
Ratio of brush radius to sampling radius for wet-hue blending.

Density
Proportion of random elements receiving brush influence.
Enhances airbrush effects.
Performs best on high-density geometry.

Tip Scale X
Horizontal stretch of the brush profile.
Useful for marker or roller-like paint application.

## Plane

### Plane

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Flatten or raise geometry relative to virtual plane.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Height
Controls influence reach above the plane.
Higher values affect vertices positioned further up.

Depth
Controls influence reach below the plane.
Higher values affect vertices positioned further down.

Inversion Mode
Dictates brush action when inverted.

Invert Displacement
When inverted, geometry moves away from the plane, increasing definition.

Swap Height and Depth
When inverted, Height and Depth roles reverse.

As an example, if Height equals 0.7 and Depth 0.3, inversion causes
effective Height of 0.3 and Depth of 0.7.

Stabilize Normal
Governs plane orientation consistency. The plane normal gets averaged across recent
steps, with quantity and blend factor set by this value.

At 0, orientation updates immediately.

At 1, orientation remains static throughout.

Intermediate settings create gradual transitions via weighted moving average of
surface normals.

Stabilize Plane
Governs plane position consistency. Functions as Stabilize Normal by averaging
position across prior steps.

Position is calculated as interpolation between unstabilized placement and projection
onto the prior step's plane.

## Pose

### Pose

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Skeletal-like deformation for posing without rigs.

The brush computes a starting point,
indicated by a white line on the cursor.

Altering Deformation Target
allows cloth-sculpting use.

### Brush Settings

### General

Only Size and Auto-Masking influence function on this brush.

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation
Operation type employed.

Rotate/Twist:
Spins mesh around the pose anchor.
Holding Ctrl generates twisting instead
(disabling any inverse-kinematic segments).

Scale/Translate:
Enlarges relative to the anchor.
While holding Ctrl, the brush displaces the mesh.

Squash/Stretch:
Like Scale/Translate yet uses unequal
scale ratios along different axes for stretching.

Rotation Origins
Method for establishing rotation anchor for the pose or specific IK segments.

Topology:
Automatically selects based on mesh structure and shape.

Face Sets:
Constructs a pose segment per Face Set, beginning with the active Face Set.
Typically generates most accurate results.

Face Sets FK:
Applies Forward Kinematics deformation with the Face Set
beneath the cursor as the control.

Pose Origin Offset
Distance of the pose anchor relative to the active radius.
Beneficial for intricate regions like appendages.

Smooth Iterations
Adjusts deformation gradient smoothness.

Pose IK Segments
Sets inverse-kinematic segment quantity
rendered as a segmented white line on the cursor.
Produces curved deformations—like hair clumps and limbs.

Lock Rotation when Scaling
Under Scale/Translate Deformation, prevents rotation; only scaling occurs.

Keep Anchor Point
Secures the terminal IK segment position.
If disabled, the mesh shifts more unrestricted,
mimicking serpentine motion.

Connected Only
Restricts to topologically joined components.
Disabling lets multiple separate meshes deform simultaneously,
like dressed figures.

Performance suffers with disconnection; reducing Max Element Distance helps.

Max Element Distance
Search extent for separate mesh portions.

## Density

### Density

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Manage geometry density with Dyntopo.

Even when Refine Method
specifies Subdivide Edges, this brush continually collapses edges.
This keeps detail addition and surface simplification both accessible.

Non-functional if Dyntopo remains inactive.

Tip

Combined with auto-smooth, the brush refines while remeshing.
On tube-shaped forms, it can reduce and dissolve volumes entirely.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

## Relax Slide

### Relax Slide

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Redistribute topology while preserving shape.

Particularly useful for shifting topology to high-detail zones,
or repositioning geometry to intended locations.

Holding Shift applies relaxation,
distributing topology uniformly.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation
The operation mode.

Drag:
Slides mesh connectivity in stroke direction.

Pinch:
Slides mesh connectivity toward the center.

Expand:
Slides mesh connectivity outward from the center.

## Smear

### Smear

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Blend colors along stroke direction.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation

Drag:
Blends hues in stroke heading.

Pinch:
Blends hues toward the brush focal point.

Expand:
Blends hues outward from the brush focal point.

## Smooth

### Smooth

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Polish surfaces or reduce volume. Always accessible via Shift.

Also provided as a Mesh Filter
for concurrent smoothing of unmasked zones.

Note

This named Smooth brush activates whenever Shift and sculpting occur.
Alter Smooth behavior or strength by selecting the Smooth
brush and tuning options.

### Brush Settings

### General

Strength
Smoothing magnitude scales with mesh density.
Finer resolution reduces strength; increase as needed.

Direction Ctrl

Smooth
Refines mesh surfaces.

Enhance Details
Amplifies surface features through reverse-direction smoothing.

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation
Two methods available.

Laplacian:
Refines both surfaces and interiors. Default action.

Surface:
Refines only surfaces, conserving volume.

Shape Preservation
Extent the original form survives refining. Higher values
lower multi-iteration smoothing strength.

Per-Vertex Displacement
Degree each vertex affects the outcome.
Higher values reduce total smoothing magnitude.

Iterations
Count of refinement applications per brush action.

Note

This works by applying standard refinement, computing
the difference between the original (blended between starting point and fully original per Shape Preservation)
and the refined geometry, refining these differences, shifting vertices via refined differences,
and finally merging the original based on Per-Vertex Displacement.

## Snake Hook

### Snake Hook

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Pull vertices, dynamically picking up and releasing geometry.

When Rake gets used,
the brush can revolve geometry through dragging.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Magnify
Pulled geometry tends toward volume reduction along paths.
With Magnify above 0.5 this remains prevented.
More info at Pinch/Magnify

Rake
Spins geometry in line with stroke heading.

Deformation
The operation type.

Radius Falloff:
Applies brush gradient to the leading point.

Elastic:
Reshapes all geometry via Elastic transformation.
More info in the Elastic Deform brush.

## Thumb

### Thumb

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Like Grab, slides geometry along surface.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

## The Brush

### The Brush

Sculpt Mode stands out through its distinctive brush operation and display.
Common brush controls persist, yet the sculpting brush renders in three-space.
This causes the brush to match the form curvature
by realigning the circumference to match the surface Normal.

The middle band of the brush outline indicates the brush magnitude.

Note

How precisely the outline follows form bulges is configurable in
the Brush Settings with "Normal Radius".
This simplifies angular-form sculpting, like the
Plane brush.

The brush supports alternative mode functions
to better demonstrate operations. As an example, the Box Trim
and Lasso Trim options can draw from the current brush radius
for removal or inclusion extent.

### Common Brushes

Numerous variants are ready, yet the following perform common duties when sculpting.
Detailed brush specifics are in the Tool Choices.

Clay Strips
Create general volumes and add bulk prior to refining.

Grab
Reposition geometry onscreen for general shaping.

Smooth
Refine and diminish surfaces to clean or even forms.

Draw
Standard adjusting on surfaces.
Frequently tailored with alternate stroke techniques and decorations for results.

Plane
Scrape and build surfaces for angular sculpting or vigorous refinement.

Inflate
Enlarge or reduce bulk or surfaces.
Helpful for controlling dimension of tube-shaped forms.

Draw Sharp
Resembles Draw yet with much stronger gradient. Good for adding grooves, fractures and other sharp lines.

Crease
A mixture of the Draw and Pinch options.
Good for producing defined grooves or strengthening for finishing.

Snake Hook.
Like Grab yet this option will fluidly release and pick up geometry during application.
The repositioned geometry orients with the stroke angle, making it excellent for
extracting geometry out.
Works optimally with Dyntopo.

## Cloth Sculpting

### Cloth Sculpting

Fabric modification without hand-sculpting or elaborate simulation rigs.
Integrated Cloth Physics Simulation provides simplified approaches.

Excellent for starting shapes and major drapery.
Refinement stays possible though performance drops on dense geometry and realism suffers.

Connectivity quality determines fold size
and detail fidelity. Uniform, well-distributed topology proves critical.

Most tools integrate smoothly—Masked vertices
anchor in place for example.
Auto-masked boundaries assist similarly.
Scene gravity applies to cloth.

Main controls center on the Cloth Brush
and Cloth Filter,
along with other reshape utilities like Pose and
Boundary offering cloth options in brush settings.

Reference file showing techniques is available
here.

## Filters

### Filters

Filters provide an alternative modification approach, since they work without a brush circumference.
Instead they impact any non-masked shown surfaces.

Strength gets set via drag from left to right.
The mouse position addresses unique zones, provided auto-masking applies.

Numerous identical brush varieties come as filter alternatives.
This grants concurrent smoothing, tinting or cloth action across broad areas.

Tip

A standard usage for the Mesh Filter
is to refine all surfaces post-density boost via
the Voxel Remesher
or Dyntopo.

See also

Further material at Mesh Filter,
Cloth Filter,
Color Filter
and Mask Filters.

## General

### General

Sculpt Mode functions like Edit Mode by adjusting model configuration,
yet Sculpt Mode implements a contrasting workflow:
rather than targeting components (points, connections, and surfaces),
a configuration zone gets changed using tools.

Sculpting Mode Example.

Sculpt Mode starts from the mode selector in the 3D View toolbar
or through the pie from Ctrl - Tab.
Upon activation, the Tool Area and Configuration of the 3D View shift to
Sculpt Mode particulars. The aim adjusts to a ring, signaling brush dimension.

Warning

For consistent brush behavior,
verify you've normalized your mesh size.

The following materials quickly introduce Sculpt Mode essentials,
with various cross-references for further study.

## Transforming

### Transforming

Move, rotate, and scale operations exist in Sculpt Mode with a key distinction from other modes. Sculpt Mode maintains its dedicated pivot point, which can be positioned manually using Shift - RMB or automatically adjusted with Mask Expand. This design permits the pivot point to be placed with greater precision and always stays anchored to the sculpted geometry.

You may alternatively toggle viewport gizmos to maintain consistent gizmo access during your workflow.

Note

The gizmo may sometimes obstruct areas you wish to sculpt. To resolve this, reposition the pivot point elsewhere to reach the target surface.

Beyond standard transform tools, Sculpt Mode provides specialized brushes—including Pose, Boundary, and Elastic Deform—that allow you to transform mesh structure directly.

## Options

### Options

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Options

Display

Fast Navigate
For high-subdivision models, render the low-resolution version while moving through the viewport.

Delay Viewport Updated
Apply geometry changes only once the region enters the view. This enables faster viewport navigation.

Use Deform Only
Constrains the active object's modifiers to Deform-type modifiers and Multiresolution only. Non-deforming modifiers (like Subdivision Surface and Mirror) are temporarily deactivated to ensure accurate results.

See also

Refer to the Display options section.

### Gravity

Factor
Adjusting this factor introduces gravity to your brush strokes, producing a draping behavior.

Orientation
Gravity direction can be aligned to a specified object's local Z axis, changing how gravity pulls.

## Brush

### Brush

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Brush

Primary tool for applying the available Sculpt mode brushes. Selecting a brush from an asset shelf or picker automatically activates this tool.

Review the Essentials Brushes list (organized by Brush Types) for comprehensive information.

## Cloth Filter

### Cloth Filter

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Cloth Filter

This tool mirrors the Cloth Brush behavior but applies cloth physics to all mesh vertices at once. Drag away from the object for positive effect or toward for negative effect.

Tip

Vertices can be "pinned" by masking regions that should stay stationary, or by using Face Sets.

### Tool Settings

Filter Type
Determines which operation gets applied to the mesh.

Gravity :

Applies gravitational force to the simulation.

Inflate :

Expands the fabric outward.

Expand :

Extends the fabric dimensions outward.

Pinch :

Compresses the fabric toward the cursor position where the operation started.

Scale :

Resizes the mesh using Soft Body dynamics, scaling based on distance from the object origin. This creates surface undulations. Control undulation orientation using Force Axis and Orientation settings.

Strength
Controls the intensity of the filter's effect on the mesh.

Force Axis
Restrict force application to a specific axis.

Orientation
Sets the axis alignment for force limitation.

Local :

Apply force and gravity along local axes.

World :

Apply force and gravity using global axes.

View :

Apply force and gravity relative to viewport orientation.

Cloth Mass
Mass value per simulation node.

Cloth Damping
How readily applied forces distribute through the cloth.

Use Face Sets
Restricts cloth forces to vertices within the Face Set under the mouse cursor.

Use Collisions
Activates collision detection with other scene objects during simulation. For the sculptable mesh to collide, the other object must have Collision Physics enabled.

## Color Filter

### Color Filter

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Color Filter

Perform color adjustments or transformations on the active color attribute across all mesh vertices at once.

Operate this tool by clicking and dragging left to right for positive effect, or right to left for negative effect.

### Tool Settings

Filter Type

Fill :

Applies uniform pigmentation.

Hue :

Shifts the hue spectrum.

Saturation :

Increases or reduces saturation.

Value :

Increases or reduces brightness values.

Brightness :

Increases or reduces overall luminance.

Contrast :

Increases or reduces tonal separation.

Smooth :

Blurs or sharpens pigmentation.

Red :

Increases or reduces red channel intensity.

Green :

Increases or reduces green channel intensity.

Blue :

Increases or reduces blue channel intensity.

Fill Color
Choose a hue for the fill operation.

Strength
Determines the intensity of the filter effect on the color attribute.

## Face Set Gesture Tools

### Face Set Gesture Tools

Reference

Mode :

Sculpt Mode

These tools apply a fresh Face Set to all faces within the designated selection region.

All Face Set gesture tools are available from the Toolbar and include:

### Box Face Set

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Box Face Set

Establishes a new Face Set using box-shaped selection.

### Lasso Face Set

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Lasso Face Set

Establishes a new Face Set using lasso-shaped selection.

### Line Face Set

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Line Face Set

Establishes a new Face Set using line-based selection.

### Polyline Face Set

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Polyline Face Set

Establishes a new Face Set using multi-segment line selection.

### Tool Settings

Front Faces Only
Creates a face set only on geometry facing toward the viewport.

## Hide Gesture Tools

### Hide Gesture Tools

Reference

Mode :

Sculpt Mode

These tools conceal selected vertices plus their connected edges and associated faces. Use Ctrl during selection to reveal hidden elements instead.

Pressing LMB without dragging restores visibility to all mesh elements.

All hide gesture tools are accessible from the Toolbar and comprise:

### Box Hide

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Box Hide

Conceals vertices and linked edges/faces using box selection.

### Lasso Hide

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Lasso Hide

Conceals vertices and linked edges/faces using lasso selection.

### Line Hide

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Line Mask

Conceals vertices and linked edges/faces using line selection.

### Polyline Hide

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Polyline Mask

Conceals vertices and linked edges/faces using polyline selection.

Note

The Polyline Hide tool does not support full reveal via LMB alone.

### Tool Settings

Visibility Area
Controls whether hidden geometry is inside or outside the selection boundary.

Inside :

Hides vertices and connected elements within the selection region.

Outside :

Hides vertices and connected elements outside the selection region.

## Mask by Color

### Mask by Color

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Mask by Color

Click any surface color to generate a fresh mask (using the active color attribute).

### Tool Settings

Threshold
Controls how sensitive the mask is to color variations. Smaller values select only closely matching colors. Higher values include a broader color range.

Contiguous
Restricts masking to color regions touching the clicked color. Disconnected areas remain unmasked.

Invert
Reverses the mask region.

Preserve Previous Mask
Maintains existing mask state and applies the new color-based mask as an addition or subtraction.

## Mask Gesture Tools

### Mask Gesture Tools

Reference

Mode :

Sculpt Mode

These tools assign a mask value uniformly to every vertex in the selection area. Use Ctrl during selection to clear the mask instead.

All mask gesture tools are accessible from the Toolbar and include:

### Box Mask

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Box Mask

Shortcut :

B

Generates a new Mask via box-shaped selection.

### Lasso Mask

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Lasso Mask

Generates a new Mask via lasso-shaped selection.

### Line Mask

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Line Mask

Generates a new Mask via line-based selection.

### Polyline Mask

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Polyline Mask

Generates a new Mask via polyline-shaped selection.

### Tool Settings

Front Faces Only
Creates a mask only on geometry oriented toward the viewport.

## Mesh Filter

### Mesh Filter

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Mesh Filter

Applies a transformation to every unmasked vertex at once. Masking, auto-masking, and visibility parameters are considered.

Use by clicking and dragging left to right for positive action, or right to left for negative action.

### Tool Settings

Filter Type
Encompasses all accessible deformation operations.

Smooth :

Softens vertex positions to polish surfaces or minimize volume from larger features. Particularly valuable for fixing voxel remesher imperfections. Functions comparably to the Smooth brush.

Scale :

Enlarges the mesh overall. Functions comparably to the Scale Transform.

Inflate :

Shifts vertices uniformly outward along their normals. Functions comparably to the Inflate brush.

Sphere :

Morphs the mesh incrementally into a spherical form. Functions comparably to the To Sphere Transform.

Random :

Displaces vertices at random along their normals. Functions comparably to the Randomize Transform.

Relax :

Creates an equitable quad distribution without altering mesh volume. Works identically to pressing Shift with the Slide Relax brush.

Relax Face Sets :

Eliminates visible roughness from face set boundaries. Works identically to pressing Shift with the Draw Face Set brush.

Surface Smooth :

Corrects mesh imperfections by equalizing vertex positions while retaining volume. Functions comparably to the Surface deformation mode of the Smooth brush.

Shape Preservation
Retains what portion of the original geometry remains unaltered when smoothing occurs.

Per-Vertex Displacement
Controls how much individual vertex movement factors into the final outcome.

Sharpen :

Emphasizes and softens geometry according to its curvature, pinching sharp features and refining flat zones. Particularly effective for hard-surface sculpting and stylized geometries featuring creases.

Smooth Ratio
Determines polish intensity applied to flat regions.

Intensify Details
Amplifies fine surface features by strengthening the distinction between grooves and peaks.

Curvature Smooth Iterations
How many times the smoothing calculation repeats per brush step. Regulates the resulting smoothness level and minimizes high-frequency noise.

Enhance Details :

Emphasizes fine surface features by strengthening the distinction between grooves and peaks. Works comparably to reversing the Smooth brush direction.

Erase Displacement :

Removes displacement data from the Multires Modifier, resetting the mesh to a standard subdivision result. Helpful for clearing sculpt areas or correcting reprojection anomalies after Shrinkwrap operations.

Negative strokes will strengthen displacement nuance, functioning like Enhance Details but sometimes producing improved results.

Strength
Dictates the force of the filter upon the mesh. Adjusting this at particular object scales can be beneficial.

Deformation Axis
Limit transformations to the designated axis.

Orientation
Establishes the axis alignment for displacement restriction.

Local :

Apply displacement using local axes.

World :

Apply displacement using global axes.

View :

Apply displacement using viewport-relative axes.

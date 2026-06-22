# Cursor, Stroke, Density Brush, Navigating In Paint Modes ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Cursor; Stroke; Density Brush; Navigating in Paint Modes; Controls; Mask; Working with Multiple Objects; Visibility, Masking & Face Sets.

## Cursor

### Cursor

Reference

Mode :

All Paint Modes

Header :

Tool Settings ‣ Brush Settings ‣ Cursor

Panel :

Sidebar ‣ Tool ‣ Brush Settings ‣ Cursor

Cursor arrangement.

While applying or sculpting a particular pointer style communicates brush characteristics.
The pointer displays as a ring in the 3D space, with the ring dimension reflecting brush dimensions.

The pointer can be concealed by toggling the switch in the section's heading.

Cursor Color
Establish the hue of the brush outline throughout an enhance/forward touch.

Inverse Color
In certain application/sculpting modes the device can be inverted and eliminate information from the application focus;
these implements can be allocated an alternative hue.

Opacity Options
Depending on the application or sculpting technique various displays appear inside the pointer
to communicate characteristics of brush application.
This commonly communicates brush reduction utilizing a transition from ring core to limit.

Alpha
You can modify the clearness quantity when
exhibiting the image utilizing the dial.

Override Overlay
Permits disabling the display enhancement throughout touches.

/ Use Cursor Overlay
Toggles exhibiting or concealing the specific brush image screen.

## Stroke

### Stroke

The mark environment establishes how sculpted/applied marks are implemented.
Every different implement behavior and result sits on this.

Mark panel.

Stroke Method Alt - E
Specifies the manner mark marks are used to the exterior.

Dots :

Apply tint per input shift. This ignores their comparative distances,
and rather depends on the mark velocity.
This implies that a deliberate mark will have greater aggregation.

Drag Dot :

Leaves a lone dab on the exterior at chosen location.

Space :

Generates mark mark as a succession of dots,
their spacing (distance between) regulated by the Spacing configuration.

Spacing
Restricts mark usage to the range specified by the share of the implement width.

(Spacing Pressure)
Implement Spacing can get awareness by enabling the pen consciousness switch,
if you operate a Graphics Tablet.

Airbrush :

Pigment supply sustains while the input is pushed (dispersal),
dictated by the Frequency setting.

Rate
Duration for how frequent the implement is utilized throughout the mark.

Anchored :

Generates a lone mark at the implement spot.
Moving and dragging will grow the mark diameter.

Edge to Edge
The implement spot and direction are governed by a couple point shape,
where the starting press is one location, and dragging establishes the next location, opposing the beginning.

Line :

Dragging enables establishing a path in screen area.
The path marks break by Spacing , matching area marks.
Using Alt the path mark is confined to 45 unit dividings.

Curve :

Specifies the mark form via a Bézier form (marks break per Spacing ).
This Bézier form gets saved in Blender as a "Paint Curve" information form.

Use Ctrl - RMB to establish the beginning node of the form.

Paint Curves
Paint Curves are replicable and become saveable and selectable via the Resource Selector interface.

-
Add Points
You can establish supplementary form management locations through Ctrl - RMB .
The regulators are established through moving the input.
The mark streams from the beginning management location to the following management location, then continuing.

-
Transforming Points
The management locations and regulators can be moved with RMB (In click choose with LMB ).
To guarantee the regulators of a location remain proportionate,
shift them applying Shift - RMB .
A handful of transition operations are useable like repositioning
( G ), spinning ( R ) and adjusting ( S ).

-
Selection
The regulators turn chooseable separately via LMB (In click choose with RMB ),
broaden the choice through Shift - LMB and drop/choose all via A .

-
Delete Points X
To erase a form location, apply X .

Draw Curve Return
To authorize and carry out the curved mark,
hit Return or use the Draw Curve option.
Option way, Ctrl - LMB is available for execution (In click choose with LMB ).

Spacing Distance Sculpt Mode Only
Calculation strategy for the gap to produce a pristine implement action.

View :

Determines the spacing in correlation to the viewport.

Scene :

Determines the spacing in correlation to each direction utilizing the mark placement.
This avoids artifacts when sculpting through curved forms and maintains spacing uniformly.

Adjust Strength for Spacing
Sustain the implement potency steady, despite spacing modifications.
Obtainable for the Space , Line , and Curve mark techniques.

Dash Ratio
Fraction of marks in a period the implement works.
Beneficial to generate dashed pathways in image application or stitching in Sculpt Technique.
Obtainable for the Space , Line , and Curve mark techniques.

Dash Length
Period of a line cycle evaluated in mark marks.
Beneficial to generate dashed pathways in image application or stitching in Sculpt Technique.
Obtainable for the Space , Line , and Curve mark techniques.

Jitter
Shift the location of each mark action in the mark path.

(Jitter Pressure)
Implement Jitter can get awareness through enabling the pen consciousness switch,
if you operate a Graphics Tablet.

/ (Expand/Collapse)
Reveal or conceal the adjustable force line.

Custom Curve
Default configuration is an ascending path indicating enhanced pen impact creates higher mark change.

For curve management see: Curve widget.

Jitter Unit
Specifies how the implement Jitter gets evaluated.

View :

The Jitter is matching the viewport bearing i.e. "display-grounded".

Scene :

The Jitter stays grounded in every direction of the planetary area.
The dimension classification and adjustments can get customized in the Scene Units.

Input Samples
Current input locations (input marks) get blended together to refine mark marks.

Use Unified Input Samples
Keep equivalent implement Input Samples across all techniques.

### Stabilize Stroke

Stabilize Stroke lags the mark behind the pointer
and yields a refined form to the pointer movement.
This turns active inputting Shift S or by pressing the swap present in the heading.

Radius
Minimum gap from the past position till the mark progresses.

Factor
A refinement measure, where enhanced quantities generate refined marks though the sensation
is akin to dragging the mark.

## Density Brush

### Density Brush

Create (or remove) curves based on a target distance. It generates a high number of points and then rejects the ones that are too close to existing points.

### Brush Settings

Density Mode
Determines whether the brush adds or removes curves.

Auto :

Either add or remove curves depending on the distance between existing curve roots under the cursor.

Add :

Add new curves between existing curves, taking the minimum distance into account.

Remove :

Remove curves whose root points are too close.

Distance Min
Goal distance between the curve roots.

Edit Minimum Distance R
Interactively sets the Distance Min value by displaying a graphic inside the brush cursor, giving a representation of the density.

The density can be adjusted by moving the mouse cursor closer or farther from the paint cursor. The Distance Min will be changed once the operator is confirmed.

Count Max
The maximum amount of points that the brush tries to sample in the surface.

## Navigating in Paint Modes

### Navigating in Paint Modes

There are different preferences for navigating the 3D Viewport in Blender. For painting and sculpting specific workflows it is recommended to use any of the following methods.

Center View to Mouse Alt MMB
Center the View on the surface directly under the mouse position. This way the rotation point of the viewport can be manually changed to any point you wish to orbit around.

Center on Last Stroke NumpadPeriod
Center the View on the average position of the last stroke.

Various preferences can also make navigation more convenient. These can be found in the "Navigation" tab of the preferences.

Orbit Method = Trackball
Tumble the view based on the mouse position in your 3D Viewport while rotating. This makes it very easy to tilt the viewport freely, instead of having the Z axis of the viewport locked.

Zoom to Mouse Position
Use the mouse position to zoom towards and rotate around the surface that is pointed at. This can be an alternative to the repeated manual use of the Center View to Mouse operator.

The disadvantage is that this navigation preference can lead to accidental navigation around backfacing geometry or very distant geometry.

## Controls

### Controls

### Auto-Masking

Reference

Mode:
Sculpt Mode

Tool:
Header ‣ Auto-Masking

Shortcut:
Alt - A

These features automatically protect areas per geometric characteristics.
Offering rapid masking without frequent manual adjustments.
Masks reset with each brush stroke or tool use and never appear as overlays.

Note that these are active across all sculpt brushes but also configurable
per brush via Advanced Brush Settings.

Access via Pie Menu at Alt - A.

All modes combine to generate targeted masks.
As an example, mask a specific face set,
exclude unattached topology and boundaries,
and target faces visible from the viewport via View Normal.

Topology
Only geometry topologically joined to the stroke/tool starting point gets affected.
Separate islands get protected.

For the Grab and
Thumb brushes specifically, anything unconnected inside the radius also gets protected.
Even joined geometry counts as isolated if the link lies outside the radius.

Face Sets
Only geometry belonging to the Face Set at stroke/tool start is affected.

Tip

If nothing appears under the cursor at initiation,
the previously protected area remains active.
Particularly handy with the "Projected" shape in the
Falloff Settings.

Mesh Boundary
Geometry at open borders is not affected.
Boundary borders to concealed faces are included.

Propagation Steps
Softens the boundary transition gradient.
Every iteration extends one edge further.
Applies to both Mesh Boundary and Face Sets Boundary.

Create Mask
Executes Mask From Mesh Boundary with active auto-masking
options. Helps render the current auto-mask or customize it manually.

Face Sets Boundary
Geometry at Face Set borders is not affected.
Boundary borders to concealed faces are included.
Propagation Steps are shared with Mesh Boundary auto-masking.

Create Mask
Executes Mask From Face Sets Boundary with active auto-masking
options. Helps render the current auto-mask or customize it manually.

Cavity
Geometry at surface peaks gets skipped.
While geared toward painting,
it works for standard sculpting too.

Factor
General intensity of cavity protection. Default is 0.5,
but 0.2 with a Custom Curve yields better outcomes.

Blur
Repetitions of cavity mask smoothing. 0 provides raw cavity masking.
Over 6 progressively diminishes visibility and speed.
Capped at 10, though typing raises the limit to 25.

Custom Curve
Refine cavity masking with a custom curve.
Beneficial for small recesses or flat areas alone.
Or modify intensity distribution in particular ranges.

Create Mask
Executes Mask From Cavity with current settings.
Renders the current auto-mask or permits further editing.

Cavity (Inverted)
Matches "Cavity" yet reversed.
Valleys and surface hollows don't activate.
Cannot combine with Cavity; shares its configuration.
Toggle to quickly flip cavity protecting.

View Normal
Only geometry with surface normals facing the viewer is affected.
Matches the "Front Faces Only" setting in the
Brush Setting, narrowing to visible areas.
This version supplies more flexibility and operates on sculpt as a whole.

Occlusion
Update View Normal to only affect geometry not hidden by other faces.
This mode conflicts with other Limit and Falloff controls.
Substantially slower performance results.

Limit
Sets the angular window of affected geometry. 90° covers all visible.

Falloff
Broadens the Limit slider's angular scope with smooth transition.
Extends perceived limits further.

Area Normal
Parallels View Normal yet derives the direction from the surface normal at stroke/tool origin.
Permits any direction for affected geometry.
Employs identical Limit and Falloff as View Normal auto-masking.

## Mask

### Mask

This covers mask-related shortcut operators and menu operations in sculpt mode.
Mask background is documented at the bottom.

Reference

Mode:
Sculpt Mode

Menu:
Mask

Shortcut:
A

Mask all shown surfaces.
Pressing A brings up a pie with frequent actions.

### Invert Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Invert Mask

Shortcut:
A , Ctrl - I

Flips the current mask.
Use when unmasked areas need modification.
Create then invert for quick coverage.

### Fill Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Fill Mask

Masks all visible geometry.
Or hit A
and clear, then invert
for identical result.

### Clear Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Clear Mask

Shortcut:
A , Alt - M

Unmasks all visible points.
To fully delete mask data, see Clear Sculpt-Mask Data.

### Box Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Box Mask

Shortcut:
B

Creates rectangular masked regions.
Shift or MMB removes masking from selected area.

### Lasso Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Lasso Mask

Shortcut:
Ctrl - RMB

Draws freeform mask boundaries.
Frequently used operation.

Tip

To clear the Lasso Mask areas, first flip the mask,
use Lasso Mask, and then reverse the mask again.

### Mask Filters

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Smooth/Sharpen Mask, Grow/Shrink Mask, Increase/Decrease Contrast

Shortcut:
A

Like other Filters,
these alter the entire mask.

Type

Smooth/Sharpen Mask
Changes mask edge definition.
Frequently more efficient than brush-based refinement.

Grow/Shrink Mask
Expands or contracts the mask across the surface.

Increase/Decrease Contrast
Modulates mask value distribution.

The Adjust Last Operation section has extra choices
for strength multiplication.

Iterations
How many times the operation repeats.

Auto Iteration Count
Employ calculated repetitions per mesh vertex proportion.
Uncheck for manual Iterations.

Tip

Instead of Iterations, try Repeat Last
through Shift - R.

### Expand Mask

Note

Further data on Mask Expand along connectivity at the Expand section.

### Mask Extract

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask Extract

Duplicates a mesh based on protected zones.
Extracted geometry additionally undergoes standard refinement for neater outcomes.

Threshold
Baseline protected value for vertex consideration during extraction.

Add Boundary Loop
Generates edge loops on boundaries,
facilitating boundary smoothing and supplementary option use.

Smooth Iterations
Iterations applied to the extracted component.

Project to Sculpt
Aligns the extracted mesh with the starting sculpt component.

Extract as Solid
Implements a Solidify Modifier on the new component.

### Mask Slice

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask Slice

Eliminates protected points from the mesh.

Threshold
Baseline protected value for vertex consideration during extraction.

Fill Holes
Fills interior gaps that may form post-Mask Slice.

Tip

Without masking, this works to fill all gaps.
Handy when using Trim Tools
options and the Voxel Remesher.

Slice to New Object
Constructs a fresh component from protected areas.

### Mask From Cavity

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask from Cavity

Builds a mask per surface topology. Settings are provided
in the Adjust Last Operation section.

Mode
How the generated mask combines with present masking. Default substitutes the current mask via
"Mix".

Mix Factor
Blend proportion. Governs intensity of the fresh mask on the present one.

Automask Settings
Identical choices as the Auto-Masking configurations.

Factor
Identical to Auto-Masking.

Blur
Identical to Auto-Masking.

Invert
Identical to Auto-Masking.

Custom Curve
Identical to Auto-Masking.

### Mask From Mesh Boundary

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask from Mesh Boundary

Builds a mask per isolated mesh components. Settings are provided
in the Adjust Last Operation section.

Mode
How the generated mask combines with present masking. Default substitutes the current mask via
"Mix".

Mix Factor
Blend proportion. Governs intensity of the fresh mask on the present one.

Automask Settings
Identical choices as the Auto-Masking configurations.

Propagation Steps
Identical to Auto-Masking.

### Mask From Face Sets Boundary

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask from Face Sets Boundary

Builds a mask per Face Set isolation. Settings are provided
in the Adjust Last Operation section.

Mode
How the generated mask combines with present masking. Default substitutes the current mask via
"Mix".

Mix Factor
Blend proportion. Governs intensity of the fresh mask on the present one.

Automask Settings
Identical choices as the Auto-Masking configurations.

Propagation Steps
Identical to Auto-Masking.

### Mask by Color

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Mask by Color

Select any hue on the geometry to generate masking (per the live color characteristic).

Threshold
How color divergence affects masking computation. Smaller scope limits related hues.
Broader scope captures significantly more matching hues.

Contiguous
Mask just touching color zones. Disconnected hues don't activate.

Invert
Flip the resulting masking.

Preserve Previous Mask
Maintain present masking and add or remove the fresh masking from hue choice.

See also

Mask by Color Tool

### Random Mask

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Random Mask

Generates masking with random values for the full component per multiple connectivity options.

Per Vertex
Assigns distinct random masking for each point.

Per Face Set
Assigns distinct random masking for each Face Set.

Per Loose Mask
Assigns distinct random masking for each unattached component section.

### Display Settings

Reference

Mode:
Sculpt Mode

Popover:
Viewport Overlays – Sculpt ‣ Mask

Mask presentation can be shown as a viewport display.
The overlay control allows brightness modification to adjust visibility.

### Clear Sculpt-Mask Data

Reference

Mode:
Object/Edit Mode

Menu:
Properties ‣ Object Data ‣ Geometry Data ‣ Clear Sculpt-Mask Data

Completely frees the masking information from the mesh. Though not a massive gain,
this can enhance speed when masking no longer applies.

## Working with Multiple Objects

### Working with Multiple Objects

Unlike Edit Mode, Sculpt Mode does not allow simultaneous editing across multiple objects. When sculpting involves working on several distinct objects, use the Alt Q shortcut while hovering over each object to efficiently switch between them.

Using multiple objects offers several benefits: each maintains its own origin point and modifier stack. Distributing mesh data across separate objects can also enhance viewport performance during sculpting. Alternatively, objects can be merged together, eliminating the need for switching.

If Face Sets have been established previously, merging objects or adding new geometry within Edit Mode automatically generates fresh Face Sets. This makes it straightforward to isolate and target newly created geometry, particularly when using auto-masking features. To establish Face Sets where none exist, invoke the Initialize Face Sets operator.

Masked regions and Face Set geometry can be extracted using the Mask Extract operation, or partitioned into a separate object through the Mask Slice function.

## Visibility, Masking & Face Sets

### Visibility, Masking & Face Sets

### Visibility Control

Mesh sections can be concealed in Sculpt Mode. Since hidden faces cannot be sculpted, this feature helps you concentrate on specific regions. Concealing geometry also enhances rendering performance in the viewport.

Hiding applies consistently across all modes except Object Mode (concealing faces in one mode hides the same faces in other modes too).

In contrast to Selection Masking in other painting tools, Sculpt Mode relies primarily on Masks and Face Sets to manage mesh display and control which regions can be modified. The Clipping Region is an exception and functions across any mode.

Common navigation shortcuts include pressing H to conceal the active face set beneath the cursor, plus Shift - H for solo-viewing (or exposing all regions).

Toggling visibility state and displaying all content is available from the Alt - W pie menu.

Adjusting visibility can also be accomplished with the Hide Gesture Tools.

See also

Consult Show & Hide for additional visibility control options.

### Masks

A mask restricts which mesh vertices are affected by sculpting and painting operations. Masks are created or adjusted via the Mask Gesture Tools and Mask by Color tool.

The internal representation of masks relies on the sculpt_mask Attributes storage system.

### Clear & Invert

Mask creation uses a different conceptual approach compared to selection in other modes. For instance, Shift - LMB performs smoothing rather than extending a mask.

Masking is also reversed from selection (masked vertices cannot be edited, while selected vertices can be).

A mask is typically added to the existing mask with LMB and removed with Ctrl - LMB. To edit the masked regions, apply the Invert operator. When masking all visible geometry, the recommended approach is to Clear the mask first, then Invert.

Both operations are accessible from the A pie menu.

See also

Explore the Mask Menu for additional mask management options.

### Face Sets

Face sets organize your mesh into distinctly colored groups of faces for quick visibility toggling as previously mentioned. They also facilitate rapid mask creation via the Mask Expand feature. The Face Set Expand function is useful for creating, adjusting, and combining face sets.

Further options are available in the Alt - W pie menu.

Face Sets can be created and modified using the Draw Face Sets brush, Mask Gesture Tools. The Edit Face Set tool provides additional modification capabilities.

See also

Visit the Face Sets Menu for comprehensive face set management information.

Face sets use the sculpt_face_set Attributes for internal storage.

### Auto-Masking

Auto-Masking is an efficient method to target specific mesh regions without manually establishing a mask or concealing geometry. This feature proves particularly effective when combined with face sets.

### Display Settings

The visibility and appearance of masks and face sets are customizable in the Display Settings panel.

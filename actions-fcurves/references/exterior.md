# Exterior, Goal, Self Collision, Elastic Deform ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Exterior; Goal; Self Collision; Elastic Deform; Expand; Gesture Tools; Painting; Brushes; Recovering Data; Cross Strip; Gamma Cross Strip; Sound Crossfade.

## Exterior

### Exterior 

External forces apply to soft-body vertices (nearly exclusively).
Newton's Laws govern behavior:

- Unforced vertices remain stationary or move at constant velocity.

- Acceleration depends on mass and force magnitude. Heavier mass causes slower acceleration; larger forces yield greater acceleration.

- Every action has equal opposite reaction.

Computing introduces damping to prevent overshoot.

### Example 

Start with a default cube.

- Disable Goal initially to prevent vertex return to original positions, isolating external-force effects.

- Begin playback.

What occurs? The cube moves downward (negative Z).
Eight vertices experience constant global gravitation.
Gravity without friction proves mass-independent, so all soft-body objects fall identically.
The cube resists deformation because all vertices move identically.

### Force Fields 

Soft body vertices interact with all Force Fields applied (typically to particles): wind, force fields, physics field effects on shared layers.

### Soft Body Field Weights 

Reference

Panel :

Physics ‣ Soft Body ‣ Field Weights

The Soft Body Field Weights panel controls external force-field influence magnitude.

Effector Collection
Restricts effectors to a specified group. Only effectors in this group affect the current system.

Gravity
Adjusts Global Gravity influence.

All
Scales all effector weights.

### Aerodynamics 

Edges respond to wind, fluttering and sailing in breezes.
A flag catching wind demonstrates simple aerodynamics.

This specialized exterior force applies to edges, not vertices.
Technically, perpendicular-to-edge force applies.
Force scales with relative-speed projection along the edge (dot product).
Wind blowing and dragging an edge through air at identical speed produce equal force. An edge moving along itself experiences zero force; perpendicular motion experiences maximum force.

Angle and relative speed between medium and edge determine force.
This causes vertices with few edges (plane front) falling faster than those with many (plane center).
Identical edge counts per direction produce equal fall speed.

Soft Body Edges panel contains Aerodynamics settings.

### Goal 

A "goal" represents the target shape a soft body attempts to match.
It acts like a pin on specific vertices, controlling soft-body influence magnitude.

Enabling Soft Body Goal uses vertex position (including animation) in simulation.
Animate vertices through standard methods (F-Curves, armatures, parents, lattices, etc.) before soft-body simulation.
The "goal" specifies desired vertex position.
How strongly the soft body pursues this goal uses stiffness and damping controls.

See Goal Settings for details.

### Goal Strength 

Goal Strength defines animation-system influence magnitude.

Goal = 1.0 means no soft body—the object behaves as regular animated object (vertex stays at original position).
Goal = 0.0 (no goal) means vertices respond only to physical laws.

Goal values between 0.0 and 1.0 blend animation and soft-body effects.

Goal serves as memory, preventing excessive deformation from the unannotated soft-body state.
Vertex Group weight system defines per-vertex Goal weight. Weight Paint frequently adjusts these comfortably.
Non-mesh objects use control-point weights instead; use Edit Mode context menu or Sidebar Transform panel.
Hair particle weights paint in Particle Edit Mode.

### Technical Details 

Soft-body mesh vertices function as mass-bearing particles.
Forces determine movement. Particles interact along edges using physical models resembling automotive shock absorbers:

- A spring maintains specific particle distance.
Soft body parameter Stiffness controls spring effort.

- Damping dampens movement.
Soft body parameter Damping controls resistance.

## Goal

### Goal 

Reference

Panel :

Physics ‣ Soft Body ‣ Goal

This enables Blender to incorporate animation (F-Curves, armatures, parents, lattices, etc.) into simulation.
The "goal" represents the animation-driven desired vertex position.

See exterior forces for details.

Vertex Group
Allows per-vertex goal weights, multiplying the Default goal.

### Settings 

Stiffness
Spring stiffness for Goal. Lower values create weak springs (flexible attachment); higher values create strong springs (stiff attachment).

Damping
Goal friction. Higher values dampen spring effects (reduced jiggle), ending motion quickly.

### Strengths 

Default
Goal weight/strength for all vertices without a Vertex Group.
With a vertex group, vertex weight specifies its goal.

Min/Max
Fine-tune vertex group weights via clamping.
Lowest vertex weight becomes Minimum; highest becomes Maximum.

## Self Collision

### Self Collision 

Reference

Panel :

Physics ‣ Soft Body ‣ Self Collision

Note

Self-Collision functions only when Use Edges is enabled.

When enabled, controls soft-body self-intersection prevention.
Every vertex gains an elastic virtual ball.
Vertices cannot penetrate adjacent balls.
Default options usually succeed; adjustment may occasionally help.

Calculation Type

Manual :

Ball Size sets directly.

Average :

Average edge length attached to the vertex multiplies by Ball Size. Suits evenly distributed vertices.

Minimal/Maximal :

Ball size equals smallest/largest vertex spring length multiplied by Ball Size.

Average Min Max :

Size = ((Min + Max)/2) × Ball Size.

Ball Size
Fraction of attached-edge length.
Edge length depends on the chosen algorithm.
Multiply by this factor to get the radius within which vertices avoid others.
Set to the fractional distance between vertices defining their "personal space".
Higher values include too many vertices, slowing calculation; lower values allow intersection despite insufficient time for avoidance.

Stiffness
How elastic the personal-space ball is.
High stiffness means immediate reaction when a vertex enters the space.

Dampening
Vertex reaction type.
Low values slow approaching vertices. High values repulse them.

Note

Configure other-object collisions in the Collision panel.
Soft-body and collision-object must share a layer to collide.

## Elastic Deform

### Elastic Deform

Reference

Mode:
Sculpt Mode

Brush:
Sidebar ‣ Tool ‣ Brush Settings ‣ Advanced ‣ Brush Type

Elastic physics deformations ideal for organic shapes. Ctrl constrains to active vertex normal.

### Brush Settings

### General

Note

More info at General brush settings
and on Advanced brush settings.

### Unique

Deformation
Surface modification approach.

Grab:
Repositions a vertex cluster.

Bi-scale Grab:
Grab with tighter falloff around the center.

Tri-scale Grab:
Grab with even more concentrated falloff.

Scale:
Spreads vertices outward from the center.

Twist:
Rotates vertices around the focal point.

Volume Preservation
Greater values maintain object size but increase lateral bulging.
(Determines Poisson ratio for elastic deformation)

## Expand

### Expand

Interactive multi-purpose operator for mask and face set creation/editing.
Activation uniformly enlarges outward from a starting point.

Note

Best used interactively through shortcuts.

Detailed workflows and feature showcase available.

Expand Mask by Topology in action

### Expand Mask by Topology

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Expand Mask by Topology

Shortcut:
Shift - A

Extends a mask beginning at the focal vertex.

### Usage

Mask from A to B
Start the operation and grow from origin to cursor distance.
Confirm via LMB or Return.

Default uses Geodesic mode 1
for surface-accurate distances.
Switch via 2, 3 & 4 for
faces, complete zones or viewport spacing.

Example output demonstrates using Diagonals on face quads.

Positioning at an open boundary extends from that entire loop.
Always applies Topology propagation.

Fill Connected Meshes
Position your cursor outside the mesh limit to mask the full linked component.
Repeat to quickly mask separate components.

Fill Face Sets
Press Ctrl to snap toward Face Sets under the cursor and fill them.
Previously entirely covered Face Sets get filled as well.

Automatically Set Transform Pivot
During Transform use, the pivot location automatically snaps to an Expand result line.
This lets regions (Like appendages) mask and immediately rotate or otherwise adjust.

Pattern Creation
The varied approaches can make loops, angles and squares.
Increase or subtract more repetitions via W & Q to multiply patterns.

An instance showing expand with reflection options,
repeats and recursion to construct detail patterns.

Tip

Reflection
capabilities work alongside the expansion.

Linear gradients G or brush-based gradients B help introduce faceted areas
to the layouts.

A "Recursion" using R or Alt - R launches
fresh expansion along the current line.
Doing repeatedly creates progressively distinct arrangements
or detailed pattern work.

An instance using repetitions and gradients with multiple expanded regions.

Tip

Keep in mind that Expand touches only visible mesh.
To limit design to a region, hide unwanted areas first.

Employ the Mesh Filter
to alter form and the Color Filter
to implement hues, applying designs onto the sculpt.

Expanding Textures
Pattern images modify the range and gradients of the expanded region.
This works with repetitions and recursion for novel results.

To apply a pattern, link it to your current brush via the
Texture Brush Settings. Modify/make it
in the Texture Properties.

Note

This pattern only functions with Mapping set to 3D.

Use Y and T to strengthen or weaken pattern effect on the region boundary.

### Controls

Invert:
F
Switches between positive (full) or negative (empty) masking.
Face Sets: toggle inside vs. outside coverage.

Toggle Preserve State:
E
Combine new masking with existing or replace entirely.
Face Sets: add boundaries or overwrite them.

Move Origin:
Spacebar
Reposition the starting vertex for distance measurement.

Geodesic Falloff:
1
Surface-distance based spacing.

Topology Falloff:
2
Edge-traversal based spacing.

Diagonals Falloff:
3
Diagonal and edge-traversal based spacing.

Spherical Falloff:
4
Straight-line distance based spacing.

Toggle Gradient:
G
Enable linear gradient from origin to target.

Toggle Brush Gradient:
B
Linear gradient using current brush Falloff shape.

Geodesic Recursive Step:
R
New expansion with surface-distance from current edge.

Topology Recursive Step:
Alt - R
New expansion with edge-traversal from current edge.

Snap Expanded to Face Sets:
Ctrl
Limit expansion to Face Set boundary.

Loop Count Increase:
W
Add repetitions; four splits region into quarters.

Loop Count Decrease:
Q
Remove repetitions; four makes quarter sections.

Texture Distortion Increase:
Y
Amplify pattern edge displacement.

Texture Distortion Decrease:
T
Reduce pattern edge displacement.

### Expand Mask by Normals

Reference

Mode:
Sculpt Mode

Menu:
Mask ‣ Expand Mask by Normals

Shortcut:
Shift - Alt - A

Extends a mask following surface contour.
Leverages the operator as Expand,
making all shortcuts and options equivalent.

This operator proves especially valuable for angular-surface work.

Tip

If a single expansion doesn't fully cover the target,
rerun from a different point.

Note

Using any Falloff shortcuts 1 - 4
substitutes the curvature approach for this operator.

### Expand Face Set by Topology

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Expand Face Set by Topology

Shortcut:
Shift - W

Constructs a Face Set from the focal vertex.
The operator parallels Expand,
sharing all hotkeys and capacities,
excluding gradient characteristics.

### Usage

Saving Masks
Expanding Face Sets mirrors expanding masks.
Key distinction: they maintain across uses.
Any mask loads as a Face Set,
reducing rework.
(And naturally Face Sets can
hide Face Sets)

Pivot Points for Pose Brush
For Pose Brush consistency, use
Face Sets to designate pivot anchor spots.
Construct from a point or from a concealed boundary between Face Sets
for rapid creation.
Alternatively Grow/Shrink Face Sets
or Expand Active Face Set to scale them.

Cloth Sculpting
Options like the Cloth Filter
and Cloth Brush
excel when adjusting small regions.
Construct Face Sets with Expand to label operation zones.

### Expand Active Face Set

Reference

Mode:
Sculpt Mode

Menu:
Face Sets ‣ Expand Face Set by Topology

Shortcut:
Shift - Alt - W

Expands a current Face Set with surface-length-based growth.
The operator parallels Expand,
sharing all hotkeys and capacities.

Note

Using any Falloff shortcuts 1 - 4
the operator to convert to Expand Face Set by Topology.

### Usage

Resizing Face Sets
Scale a Face Set perpendicular to surface proportions.
Provides an alternative to Grow/Shrink Face Sets
which adheres to links instead of surface separation.

Joining Face Sets
While pressing Ctrl the growth will alternatively snap toward other Face Sets.
This rapidly links various Face Sets into one.

## Gesture Tools

### Gesture Tools

Distinct from brushes and filters, Sculpt mode carries gesture choices that conduct actions to a sketched
picking region. These parallel choice methods (for instance rectangular and freeform choosing in different regions).

These do not make a picking of components which receives alteration; they straight alter the underlying
mesh.

### Box Gestures

Pulling forms a rectangular area from button press to button launch.

### Controls

Move Spacebar
Keep to shift the picking zone.

### Lasso Gestures

Pulling forms a freeform area conforming to the aim from button press to button launch.

### Controls

Move Spacebar
Keep to shift the picking zone.

### Tool Settings

Stabilize Stroke
Decreases jitter while pulling by delaying and fixing point spots.

Radius
Minimal gap from the past point prior to the stroke continues.

Factor
A smoothness level, with larger settings giving more refined paths
yet the draw sensation feels like you're tugging the path.

### Line Gestures

Pulling forms a line. The resulting action works on everything on the shaded side of the line. The zone worked
on broadens in both viewport paths.

### Controls

Flip F
Reverses which side of the line the choice operates on.

Snap Ctrl
Keep to limit the line tilt to specific steps. Chooses 5° increments,
editable through the Choice menu shown by the magnet symbol in the top menu.

Move Spacebar
Keep to shift the line.

### Tool Settings

Limit to Segment
The acted zone won't surpass the sketch path length.
Helpful for picking a smaller zone rather than lengthening the line forever.

### Polyline Gestures

Clicking puts a node in the viewport. Each button press puts a fresh node. Clicking on the start,
pushing LMB twice,
or pressing Return seals the picking zone.

### Controls

Move Spacebar
Keep to shift the picking zone.

## Painting

### Painting

Sculpt Mode enables you to paint your mesh surface through Color Attributes, including Vertex Colors. This consolidates frequently-used sculpting tasks within one workspace, minimizing the need to switch between different modes.

Painting capabilities can be combined with other sculpt mode features such as face sets, masking, and filters.

The painting toolset available in Sculpt Mode includes the Paint and Smear brushes, as well as the Color Filter and Mask by Color tools.

Like other brushes, pressing Shift initiates smoothing. For painting brushes specifically, this blurs the pigmentation within the brush area rather than blending geometry.

Note

When any painting tool begins operation, the viewport rendering automatically shifts to "Attribute" mode. This ensures that color attributes remain visible on all meshes whenever painting occurs.

## Brushes

### Brushes

### Brush Types

Refer to Brush Type reference.

Below is a listing of accessible brush types paired with Essentials asset library brushes using those types.

Draw
Brushes: Paint

Deposits assigned weight values onto the mesh.

Blend
The brush Blend Modes establishes how the weight applies to the vertex group while painting.

Mix
Here the Weight establishes the target weight ultimately reached with continuous application at the same location. Brush strength indicates stroke count to hit the target. Note: strength = 1.0 applies target immediately; Weight = 0.0 has no effect.

Add
Adds the specified weight to vertex weighting. Brush strength determines the fraction added per stroke. Weights stay below 1.0.

Subtract
Removes the specified weight from vertex weighting. Brush strength determines the fraction removed per stroke. Weights stay above 0.0.

Lighten
Uses the specified weight as the target. Similar to Mix mode, but only affects weights beneath the target. Weights above the target stay unchanged.

Darken
Comparable to Lighten mode. Alters only weights above the target. Weights below the target stay unchanged.

Multiply
Scales vertex weighting by the specified weight. Similar to subtraction, but the removed amount relies on the Weight value itself.

Blur
Smooths vertex weighting across adjacent vertices. The Weight Value parameter is ignored here. Brush strength governs the smoothing amount.

Blur
Brushes: Blur

Smooths vertex weighting across adjacent vertices. The Weight Value parameter is ignored here. Brush strength governs the smoothing amount.

Average
Brushes: Average

Balances weights by applying the averaged result across all weights in the brush zone.

Smear
Brushes: Smear

Transfers weights by gathering them from the brush zone and "dragging" them. Comparable to finger painting.

## Recovering Data

### Recovering Data

Unexpected shutdowns, power failures, or neglecting to save your project can lead to lost or corrupted content. Blender's Auto Save feature reduces the chance of losing work in such situations.

Three features help prevent accidental loss:

- Save Prompt shows a confirmation when exiting with unsaved modifications

- Save Versions stores backup copies with sequential numbering

- Auto Save creates periodic snapshots at set intervals (default: every 2 minutes)

Note

For undoing actions during normal work, see Undo , Redo and Undo History to roll back changes or jump to a prior state. See Undo & Redo.

### Recovering Save Versions

By default Blender maintains one backup whenever you save.
Instead of overwriting the old file, Blender renames it with a .blend1 suffix.

This copy lets you revert to an older version.

Check Save Versions to adjust how many backups are retained.

### Recovering The Last Session

Reference

Menu :

File ‣ Recover ‣ Last Session

Recover Last Session opens the quit.blend file stored in the Temporary Directory when Blender closes normally (see Blender Session). Keep in mind files in your temp folder may be removed when you restart your computer or when maintenance scripts run, depending on your setup.

### Recovering an Auto Save

Blender continuously saves automatic backups while you work.
If Blender crashes or closes unexpectedly, the autosave may contain recoverable work.

Follow these instructions to restore from autosave:

- Start Blender.

- Click the top-left menu: File –> Recover –> Auto Save.

- Browse the file dialog that opens to locate the backup you want.
Files follow the naming pattern: <filename>_autosave.blend
Note these files include timestamps to help you identify the right one.

- Pick the desired file and press Open.

- Once loaded, use Save As right away to preserve it separately from the autosave.

Tip

Enable detailed list mode when browsing autosaves to identify the most recent version.

File Browser showing a vertical list.

See also

Auto Save Interval Preference

## Cross Strip

### Cross Strip

The Cross transition creates a fade between two strips, known as a crossfade. Strips may overlap or have spacing; however, with spacing, the final and initial frames extend, potentially causing pauses if strips are sequences.

### Options

Default Fade
Automatically computes a linear fade across the strip duration.

Effect Fader
Allows custom keyframe animation of the fade. Various easing functions enable precise control.

### Example

Cross Effect.

## Gamma Cross Strip

### Gamma Cross Strip

The Gamma Cross transition mirrors the Cross Strip but applies color correction during the transition between strips, producing a visually gentler transition.

### Options

Default Fade
Automatically computes a linear fade across the strip duration.

Effect Fader
Allows custom keyframe animation of the fade. Easing options enable precise fade tuning.

## Sound Crossfade

### Sound Crossfade

The Sound Crossfade transition adjusts the Volume of two overlapping Sound strips to fade between them evenly. Because this animates a property rather than generating a new strip like other effects, it operates differently from traditional transitions.

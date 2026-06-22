# Texture Slots, Tiling, Editing Weight Paint

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Texture Slots; Tiling; Editing Weight Paint.

## Texture Slots

### Texture Slots

Texture Slots settings.

A "slot" represents the grouping of images paired with UV layers.

Choosing a Paint Slots or Canvas Image will also show the related image in the Image Editor.

Mode
The slot framework provides two painting approaches:

Material
This mode extracts slots from the material composition of the mesh.

In Cycles rendering, every Image Texture node in the material's node architecture is placed in the slots.

Active Paint Texture Index
Shows all available slots. Trigger a slot by LMB clicking for painting.

Single Image
Pick an image and painting applies using the active UV layer.

Image
Pick the image as your painting surface.

New
Establish a fresh image.

UV Map
Pick the UV mapping for painting. (Equivalent to the active UV map in the mesh's UV Maps settings.)

Texture Filter Type
Choose the texture sampling method. Choices: Linear or Closest.

Save All Images
Repack (or write if stored separately) every altered image. Same as in Image Editor.

Add Simple UVs
Creates a cube unwrap and arranges it. Custom unwrapping is still preferable.

This choice is available only when the object doesn't contain a UV Map yet.

## Tiling

### Tiling

Reference

Editor :

Image Editor

Mode :

Paint Mode

Menu :

Sidebar ‣ Tools ‣ Tiling

Repeats strokes to the opposing side as your brush exits the canvas, useful for creating seamless patterns.

X
left/right

Y
top/bottom

## Editing Weight Paint

### Editing Weight Paint

Reference

Mode :
Edit Mode and Weight Paint Mode

Menu :
Weights

Weight Paint Tools.

Blender offers multiple utilities to facilitate weight painting operations.

The Subset Option

Many tools provide a Subset filter allowing you to narrow their scope to particular vertex groups
(available in the Adjust Last Operation panel after tool activation)
with these available choices:

- Active Group
- Selected Pose Bones
- Deform Pose Bones
- All Groups

All tools are compatible with Vertex Selection Masking and Face Selection Masking.
When active, tools only influence selected vertices or faces.

### Assign from Bone Envelopes

Transfer envelope weights from chosen bone(s) to the active vertex group.

### Assign Automatic from Bone

Use the same automated weighting approaches on the chosen bone(s) and their vertex group
as found in the Parent armature menu.

### Normalize All

Ensures each vertex's total weight across all groups sums to 1. All vertex groups are normalized
except locked ones, which retain unchanged values.

Lock Active
Maintain active group values while normalizing the remaining groups.

### Normalize

Works exclusively on the active vertex group. Vertex relative weights stay the same,
while the entire weight set is scaled such that the peak value reaches 1.0.

Normalize example.

### Mirror

The Mirror Vertex Group operation duplicates weights
across a perfectly symmetrical mesh's opposite sides.
Vertices lacking a corresponding match remain unaffected.
Note: weights transfer to the matching opposite bone's group only with additional configuration.

Note

Mirroring requires perfect X-axis symmetry in the object's rest pose.

Mirror example.

Mirror Weights
When enabled, any selected vertex obtains
the weight profile from its symmetrical opposite.
If both vertices are selected, weights exchange;
if only one is selected, unselected vertex data replaces selected data.
Active group transfers receive weight information,
or all groups if All Groups is selected.

Flip Group Names
Works on selected vertices in groups with "symmetrical nomenclature"
(containing components like "L", "R", "right", "left").
Selected vertices in the active group or its symmetrical partner
get reassigned to the symmetrical counterpart;
the original weight value persists.
With All Groups active, all such reassignments
change to their symmetrical equivalents, preserving old weights.

All Groups
Apply to every vertex group instead of just the current one.

Topology Mirror
Mirror for asymmetric meshes (approximate mirror).
Refer to documentation for additional details.

Tip

Mirror to Opposite Bone

To generate a mirrored group for an opposing bone
(in a symmetric character), follow these:

- Delete the destination vertex group (target for mirrored data).

- Duplicate the source bone vertex group
(the one containing weights to copy).

- Rename this new group to the destination group name
(the one you removed above).

- Activate the destination group and invoke Mirror
(use Mirror Weights only and optionally Topology Mirror for asymmetric meshes).

### Invert

Changes each weight in a selected group by × -1.0.

Examples:

- 1.0 becomes 0.0
- 0.5 stays 0.5
- 0.0 becomes 1.0

Invert.

Subset
Limit operation to a subset.
See The Subset Option above for subset definitions.

Add Weights
Include vertices with zero weight prior to inverting (set to 1.0).

Remove Weights
Eliminate vertices from the group if they hit 0.0 post-inversion.

Note

Locked groups remain unchanged.

### Clean

Clean Vertex Group Weights strips vertices from
Vertex Groups
whose weights fall below the Limit threshold. Removes low weights.
Useful for clearing groups of minimal (or empty) weight assignments.

In the example, a threshold of 0.2 removes
all blue sections.

Note, images display Show Zero weights Active
so unassigned weights appear Black.

Clean example.

Subset
Limit operation to a subset.
See The Subset Option above for subset definitions.

Limit
The minimum weight magnitude retained. Weights below this remove from the group.

Keep Single
Prevents the Clean operation from producing completely unassigned vertices
(not linked to any group), ensuring each keeps at least one weight even below threshold!

### Quantize

This tool uses Quantization,
constraining input weights to discrete steps between (0 - 1),
eliminating smooth gradients.

Quantize example (Steps = 2).

Steps
How many discrete intervals between 0 and 1 to divide weights into.
For instance, 5 yields allowed values [0.0, 0.2, 0.4, 0.6, 0.8, 1.0] .

### Levels

Applies offset and scaling to active group weights.
Adjust the perceived "intensity" of the weight group using this tool.

Note

All results clamp between 0.0 and 1.0 regardless of input values.

Levels example.

Subset
Limit operation to a subset.
See The Subset Option above for subset definitions.

Offset
A value within (-1.0 - 1.0) added across all weights in the group.

Gain
All Subset weights multiply by the gain factor.

Note

Whichever Gain and Offset values apply,
the final result always clamps to
(0.0 - 1.0). Negative weights and excessive areas
(weight > 1.0) never occur with this tool.

### Smooth

The Smooth operator averages selected vertex weights based on adjacent vertices,
producing smoother transitions in weight distributions. Use this for refining weight flows,
improving deformation during rigging, and removing sharp transitions between adjacent weights.

Note

This tool requires active vertex selection; without it, it becomes unavailable.

Subset
Limit operation to a subset.
See The Subset Option above for subset definitions.

Factor
Governs blending intensity toward connected vertex average weight.

- A Factor of 0.0 leaves weights untouched.

- A Factor of 1.0 applies the calculated average fully.

- Between 0.0 and 1.0 performs partial blending.

Iterations
Defines repetition count of the smoothing pass.
Higher counts yield smoother results but risk unwanted fine-detail degradation.

Expand/Contract
Modifies smoothing reach by expanding or contracting the affected region:

- Positive values widen the area to encompass nearby vertices.

- Negative values narrow focus to a smaller subset.

### Examples

Example: Single Selected Vertex

Suppose one selected vertex connects to four unselected ones.
The unselected vertices carry weights: 1, 0, 0, and 0.
Averaging unselected neighbors yields: \\((1 + 0 + 0 + 0) / 4 = 0.25\\)

With Factor set to:

- 0.0: Original weight preserved.

- 1.0: Adopts average (0.25).

- Between 0 and 1: Weight gradually shifts toward 0.25 proportionally.

Single vertex select with a Factor of 1.0.

Example: Multiple Selected Vertices

With multiple selected vertices,
Smooth evaluates each against its unselected neighbors.

For example:

- Three unselected neighbors with \\((1, 0, 0)\\) average to \\(0.333\\) .

- One unselected neighbor with weight 1 averages to \\(1.0\\) .

- Only unselected neighbors with \\((0, 0, 0)\\)
stays unchanged at \\(0.0\\) .

Factor value determines these final values.

Three selected vertices with a Factor of 1.0.

Example: Edge Loop Smoothing

A practical scenario involves selecting a center edge loop to
blend across adjacent regions. For instance:

- Two flanking unselected vertices on either edge carry \\(1\\) and \\(0\\) .

- Their average is \\((1 + 0) / 2 = 0.5\\) .

- Running Smooth with Factor at 1.0 colors the loop green,
creating gradual transition between "active" (left) and "inactive" (right) zones.

Center edge loop of vertices selected with a Factor of 1.0.

### Transfer Weights

Move weights from other objects to the active object's groups.

By default transfers only the active group of source to
the active group of target or generates a new one if absent.
Behavior adjusts through the Adjust Last Operation panel.

For instance, shift Source Layers Selection to By Name
to copy all source groups to target.

Note

This tool applies generic "data transfer" from all selected objects to the target.
Consult Data Transfer
documentation for option explanations.

### Prepare the Copy

First choose all source objects, then pick the target
(target must remain active).

Source and target positioning matters.
Placement at opposite sides prevents successful transfer. (Review Vertex Mapping.)
Separate layer assignment works,
yet all must stay visible during tool invocation.

Ensure target sits in Weight Paint Mode.
Access the Toolbar and locate Transfer Weights in the Weight Tools area.

### Adjust Last Operation Panel Confusion

The Adjust Last Operation panel persists
post-transfer completion. It vanishes
only after calling another Operator with its own panel.
This confuses when reusing Transfer weights after vertex group changes.
Reapplying the existing panel
resets work to its initial state before your original Transfer Weights activation.

Wanting to invoke Transfer Weights afresh after modifying
groups? Always press the Transfer Weights button,
unless intentionally reverting to the first call.

### Limit Total

Reduce each vertex's weight count to the specified Limit.
Lowest weights get removed until threshold hits.

Hint

Operation works best with multiple selected groups.

Subset
Limit operation to a subset.
See The Subset Option above for subset definitions.

Limit
Maximum weights per vertex allowed.

### Set Weight

Reference

Mode :
Weight Paint Mode

Menu :
Weight ‣ Set Weight

Shortcut :
Ctrl - X

Populate the active group with the selected brush weight value.

### Sample Weight

Reference

Mode :
Weight Paint Mode

Menu :
Weight ‣ Sample Weight

Shortcut :
Shift - X

Modify the Draw
tool's current weight by capturing the weight beneath the cursor.

### Sample Group

Reference

Mode :
Weight Paint Mode

Menu :
Weight ‣ Sample Group

Shortcut :
Shift - Ctrl - X

Choose a vertex group from those under the current cursor location.

### Gradient (Linear)

Reference

Mode :
Weight Paint Mode

Menu :
Weights ‣ Gradient (Linear)

Shortcut :
Shift - A

Implements a linear weight gradient;
helpful when gradual painted transitions prove challenging.
Merges selected vertex weights toward unselected vertices.

Example of the Gradient tool being used with selected vertices.

Weight
The gradient begins at the current brush weight, diminishing outward.

Strength
Lower numbers blend smoothly with preexisting weights (like brush behavior).

Type
The gradient form.

Linear :
A straight-line gradient.

Radial :
A circular gradient.

### Gradient (Radial)

Reference

Mode :
Weight Paint Mode

Menu :
Weights ‣ Gradient (Radial)

Shortcut :
Shift - Alt - A

Implements a circular weight gradient;
helpful when gradual painted transitions prove challenging.
Merges selected vertex weights toward unselected vertices.

Weight
The gradient begins at the current brush weight, diminishing outward.

Strength
Lower numbers blend smoothly with preexisting weights (like brush behavior).

Type
The gradient form.

Linear :
A straight-line gradient.

Radial :
A circular gradient.

### Locks

Reference

Mode :
Edit Mode and Weight Paint Mode

Menu :
Weights ‣ Locks

Shortcut :
K

Locking vertex groups prevents unwanted alterations to particular groups.

Tip

Locked group bones show in red within the 3D Viewport.

Lock All
Apply locks to every group.

Lock Selected
Apply locks to chosen groups.

Lock Unselected
Apply locks to non-chosen groups.

Lock Only Selected
Lock chosen groups and release others.

Lock Only Unselected
Release chosen groups and lock others.

Unlock All
Remove locks from every group.

Unlock Selected
Remove locks from chosen groups.

Unlock Unselected
Remove locks from non-chosen groups.

Invert Locks
Flip all group lock statuses.

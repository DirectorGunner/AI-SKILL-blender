# Bevel, Edge Data, Triangles To Quads, Bisect ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Bevel; Edge Data; Triangles to Quads; Bisect; Deleting & Dissolving; Separate; Sort Elements; Move, Rotate, Scale.

## Bevel

Smooths out corners and edges to create realism—physical objects lack infinite sharpness. The Bevel Modifier performs this non-destructively.

Reference — Mode: Edit Mode | Menu: Vertex ‣ Bevel Vertices, Edge ‣ Bevel Edges | Shortcut: Shift - Ctrl - B (vertices), Ctrl - B (edges)

Usage: Select vertices, edges, or faces; press Ctrl - B (edges and corners) or Shift - Ctrl - B (corners only). Move mouse to increase radius; scroll wheel adjusts segment density. Confirm with LMB/Return; cancel with RMB/Esc.

While active, settings display at viewport top. Keyboard shortcuts (status bar) select settings; mouse or numeric input changes values. Hold Shift for slower precision; Ctrl snaps to coarse increments. After LMB confirmation, Adjust Last Operation panel retains setting access.

Affect — Target selection:
- Vertices: Bevel selected vertices, leaving edges unchanged
- Edges: Bevel selected edges plus vertices where 3+ edges meet

Width Type (M) — Width meaning (examples below use 50% for Percent, 1.0 for others): Offset, Width, Depth, Percent, Absolute

Width (A): Bevel size/radius (meaning depends on Width Type)

Note: Multi-edge beveling sometimes prevents simultaneous width matching; Bevel compromises. Disabling Loop Slide (below) can ease this.

Segments (S): Density of new geometry; higher = smoother result; adjustable with Wheel while active

Profile Shape (P): Number 0–1 controlling bevel profile shape (side view). For Miter Outer/Inner set to Arc, also controls miter shape.

Material Index: 0-based material slot for new faces; -1 inherits neighbors' materials

Harden Normals (H): Custom split normals on new faces for smooth shading without affecting rest of mesh

Clamp Overlap (C): Prevents beveled edges overshooting past neighboring face ends

Loop Slide: Whether new inner edges align perpendicular to beveled edge (off) or match existing inner edge direction (on)

Mark section:

Seams (U): When beveling 3+ edges sharing a vertex with 2 marked UV Seams, new edges between them also mark as Seams

Sharp (K): Like Mark Seams, but for Sharp edges

Miter Outer (O): For 3+ edges at one vertex forming 180°+ corner on face side, Outer Miter determines extra geometry creation to prevent pinching

Miter Inner (I): For 2+ edges at one vertex forming <180° corner on face side, Inner Miter determines extra geometry creation

Spread: Inner Miter arc size; also affects Outer Miter

Intersection Type (N) — Multi-edge intersection geometry:
- Grid Fill: Smoothly connect edges with geometry
- Cutoff: Cap each edge with flat face

Face Strength — Face strength application for bevel faces (works with Weight Normals Modifier, Face Influence checked):
- None: No face strength set
- New: New edge faces = Medium strength; new vertex faces = Weak
- Affected: New case + adjacent faces = Strong
- All: Affected case + remaining faces = Strong

Profile Type (Z) — Generated-edge flow along beveled edge:
- Superellipse: Auto profile from Profile Shape setting
- Custom: Custom profile from Curve Widget in Adjust Last Operation panel; side view of bevel between 90° faces; darkened area = mesh interior

Presets: Support Loops and Steps presets auto-generate based on Segments count; if segments change, reapply preset.

Sample Straight Edges: Whether to sample profile mid-segment on perfectly straight curve segments (Vector-handle lines). Disabled by default; control-point sampling usually sufficient.

Sample Even Lengths: By default, each profile segment (control-point pieces) gets equal sample points. Enable to distribute samples evenly along full profile length instead.

### Bevel

Reference

Mode:

Edit Mode

Menu:

Vertex → Bevel Vertices , Edge → Bevel Edges

Shortcut:

Shift - Ctrl - B (Bevel Vertices), Ctrl - B (Bevel Edges)

Bevel rounds corners and edges. This aids realism – in the real world, nothing stays infinitely sharp.

Cubes without and with bevel.

See also

The Bevel Modifier performs rounding non-destructively.

### Usage

Pick one or more vertices, edges, or faces, then press Ctrl - B to smooth both edges and corners, or Shift - Ctrl - B for corners alone. Drag to increase bevel radius and scroll to adjust geometry density.
Finally, press LMB / Return to apply or RMB / Esc to cancel.

| Before beveling. | Increased bevel width. | Increased bevel segments. |

### Options

While operating, settings appear at the viewport's top. Pick a setting via keyboard shortcut (status bar shows all), then drag the cursor or type a number. Press Shift while dragging to slow down for finer control, or Ctrl to jump in larger increments.

After applying with LMB, Adjust Last Operation panel preserves further changes.

Affect V

Vertices
Round selected vertices, keeping edges unchanged.

Edges
Round selected edges and vertices where three or more edges join.

Width Type M
What the Width setting represents. In the examples below, Width is 50% for "Percent" and 1.0 for others.

| Before beveling | Offset | Width |
| Depth | Percent | Absolute |

Width A
Bevel size/radius. Width Type determines its exact meaning.

Note

When multiple edges are beveled simultaneously, matching widths across all edges may be impossible.
Bevel compromises in such cases.
Disabling Loop Slide (below) sometimes helps.

Segments S
Geometry density. Higher values yield smoother results.

While active, Wheel adjusts this setting even if not selected.

Profile Shape P
A value between 0 and 1 managing the bevel profile shape (viewed from the edge's side).

When Miter Outer or Miter Inner is Arc, this also governs miter shape.

Material Index
The 0-based material slot index for newly created faces.
Use -1 to inherit from neighbors.

Harden Normals H
When on, applies custom split normals to new faces, creating smooth appearance without altering the rest.

Clamp Overlap C
Blocks beveled edges from extending past neighboring face ends.

Loop Slide
Whether new inner edges stay perpendicular to the beveled edge or follow existing inner edge directions.

| Before beveling. | Loop Slide off. | Loop Slide on. |

Mark

Seams U
When beveling three or more connected edges and two are marked UV Seams, new edges between them get marked too.

Sharp K
Mirrors Mark Seams but for Sharp edges.

| Before beveling. | Mark Seams off. | Mark Seams on. |

Miter Outer O
When beveling three or more edges meeting at one vertex, and two form a corner over 180° on the face side, Outer Miter determines whether extra geometry prevents pinching.

| Sharp outer miter (no extra geometry). | Patch outer miter. | Arc outer miter. |

(Miter) Inner I
When beveling two or more edges meeting at one vertex and they form a corner under 180° on the face side, Inner Miter determines whether extra geometry prevents pinching.

| Sharp inner miter (no extra geometry). | Arc inner miter. |

Spread
The size of the Inner Miter when Arc. This also impacts the Outer Miter.

Intersection Type N
Geometry type at points where three or more beveled edges converge.

Grid Fill:

Fill the space with geometry that smoothly joins the edges.

Cutoff:

Cap each edge with a flat surface.

| Grid fill. | Cutoff. | Cutoff with a center face. |

Face Strength
Whether to set a Face Strength for beveled faces.
Pair with a Weight Normals Modifier (Face Influence checked).

None:

No face strength assignment.

New:

Set new edge faces to Medium and new vertex faces to Weak.

Affected:

Plus all Set for New, also set neighboring faces to Strong.

All:

Plus all Set for Affected, also set remaining mesh faces to Strong.

Profile Type Z
Controls the edge flow generated along each beveled edge.

Superellipse
Auto-profile based on Profile Shape setting.

Custom

The custom profile widget.

Use a custom profile from the Curve Widget in Adjust Last Operation panel. The curve shows a side view of a bevel between two 90° faces; shaded zones represent the mesh interior.

Presets
Support Loops and Steps build dynamically with the bevel Segments count. Changing segment count requires re-applying the preset.

Sample Straight Edges
Whether to sample at the middle of fully straight curve segments (lines with Vector handles between control points).
Off by default, as sampling at control points typically suffices.

Sample Even Lengths
By default, each profile segment (between control points) gets the same sample count. Enable to distribute samples evenly along the entire profile length.

## Edge Data

Operators below modify edge properties affecting certain tools or modifiers. Press Ctrl - E to open Edge menu popover at mouse cursor for quick operator access.

Edge Bevel Weight:
Reference — Mode: Edit Mode | Menu: Edge ‣ Edge Bevel Weight
Interactively changes selected edges' Bevel Weight. After menu item selection, move mouse to change or type number (positive/negative) to adjust. Value displays at viewport top. Confirm with LMB/Return; cancel with RMB/Esc. Sidebar shows/edits Bevel Weight.

Edge Crease:
Reference — Mode: Edit Mode | Menu: Edge ‣ Edge Crease | Shortcut: Shift - E
Interactively changes selected edges' Crease amount. After menu/shortcut, move mouse to change or type number (positive/negative) to adjust. Value displays at viewport top. Confirm with LMB/Return; cancel with RMB/Esc. Sidebar shows/edits Crease value.

Mark/Clear Seam:
Reference — Mode: Edit Mode | Menu: Edge ‣ Mark/Clear Seam
Mark/unmark selected edges as UV Seams.

Mark/Clear Sharp:
Reference — Mode: Edit Mode | Menu: Edge ‣ Mark/Clear Sharp
Mark/unmark selected edges as Sharp. Used for:
- Sharp edge rendering and flat face rendering in otherwise smooth-shaded meshes (via vertex normal adjustment on sharp-connected vertices)
- Edge Split Modifier edge specification
- Smooth By Angle and Weighted Normal Modifier edge exclusion
- External format smoothing group export (FBX, OBJ)
Internal storage: sharp_edge attribute
See also: Is Edge Smooth Node, Set Shade Smooth Node

Set Sharpness by Angle:
Reference — Mode: Edit Mode | Menu: Edge ‣ Set Sharpness by Angle
Sets sharp edge attribute based on neighboring face angle.

Angle: Maximum face-normal angle for smooth classification
Extend: Add new sharp edges without clearing existing

Mark/Clear Freestyle Edge:
Reference — Mode: Edit Mode | Menu: Edge ‣ Mark/Clear Freestyle Edge
Mark/unmark selected edges for Freestyle lines. See Edge Marks.

## Triangles to Quads

### Triangles to Quads 

Reference

Mode :

Edit Mode

Menu :

Face ‣ Triangles to Quads

Shortcut :

Alt - J

Fuses neighboring triangles in the selection into quads — essentially the inverse of Triangulate
Faces, and runnable across a whole mesh in one pass.

To avoid producing malformed quads, the operator applies angle thresholds, which means a few
triangles can be left over.

| Before converting triangles to quads.  | After converting.  |

### Options 

Max Face Angle
The largest angle allowed between two triangle normals — coplanar triangles count as 0°, not 180°.
Triangle pairs exceeding this stay unmerged.

Max Shape Angle
How far from rectangular a quad may be. At 0° only triangles forming a perfect 90°-cornered quad
merge; at 40°, corners from 50° to 130° are allowed, and so on.

Topology Influence
How strongly to favor new quads that follow the topology of existing quads.

Tip

For best results, set Topology Influence between 100-130% and Max Angle to 180°.
Lower values may leave behind parallelograms and triangles, while higher values may cause errors.

Compare UVs
Don't merge triangles that are disjoint in any UV map.

Compare Color Attributes
Don't merge triangles that, for any Color Attribute, have different colors at their shared edge.

Compare Seam
Don't dissolve edges that are marked as UV Seams.

Compare Sharp
Don't dissolve edges that are marked as Sharp.

Compare Materials
Don't merge triangles that have different materials.

Deselect Joined
Drops the merged triangles from the selection, which makes it easy to find the triangles still
awaiting conversion.

## Bisect

### Bisect 

Reference

Mode :

Edit Mode

Tool :

Toolbar ‣ Knife ‣ Bisect

Menu :

Mesh ‣ Bisect

Slices the selected geometry into two halves using an infinitely large plane.

### Usage 

Angle the view so the cutting plane reads as a line — the Top view, say, when splitting the mesh
left from right. Then turn on the tool and drag out the cut line with LMB . These shortcuts are
live while dragging (and listed in the status bar):

Move Spacebar
Repositions the line.

Snap Ctrl
Locks the line's rotation to 15-degree steps.

Flip F
Swaps which side of the plane counts as the "outer" one. Fill and Clear Inner/Outer rely on this
later.

### Options 

Drag the line and a yellow arrow marks the way toward the "outer" side; the Adjust Last Operation
panel then exposes these:

Plane Point, Plane Normal
Type exact figures here to pin the plane down precisely.

Fill
Adds faces along the cutting plane to seal any gaps left by Clear Inner/Outer , drawing
materials, UVs, and Color Attributes from the surrounding geometry.

Clear Inner/Outer
Wipes out any geometry on the "inner" or "outer" side of the plane — including geometry that
wasn't originally selected.

Axis Threshold
Vertices nearer the plane than this threshold are reused; everywhere else, fresh vertices and
edges get built.

### Examples 

| Example of a common use of bisect.  | Example of bisect with the Fill option enabled.  |

## Deleting & Dissolving

### Deleting & Dissolving 

### Delete 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete

Shortcut :

X or Delete

Removes the selected mesh elements. The menu offers:

Vertices
Removes the selected vertices, plus every edge and face they belong to.

Edges
Removes the selected edges, plus any faces they belong to. Stranded vertices go too.

Faces
Removes the selected faces. Stranded vertices and edges go too.

Only Edges & Faces
Removes the selected edges and faces, plus any unselected face holding a selected edge. Stranded
vertices stay put.

Only Faces
Removes the selected faces. Stranded vertices and edges stay put.

### Dissolve 

Where deleting leaves a hole, dissolving instead keeps the surface sealed.

### Dissolve Vertices 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete ‣ Dissolve Vertices

Shortcut :

X , Delete , or Ctrl - X

Removes each selected vertex and fuses its surrounding faces into a single one. (N-gons often
result.)

Should a vertex belong to a wire — a chain of edges in no face — its surrounding edges merge
instead.

The Adjust Last Operation panel offers the following options:

Face Split
Where possible, splits surrounding faces so only a corner triangle merges rather than the whole
face. This shrinks the final "hole-filling" faces and evens them out.

Tear Boundaries
At the mesh boundary, deletes faces rather than merging them. Such faces always split, even with
Face Split off.

| Original mesh  | Face Split: Off  Tear Boundaries: Off | Face Split: On  Tear Boundaries: Off | Face Split: On/Off  Tear Boundaries: On |

### Dissolve Edges 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete ‣ Dissolve Edges

Shortcut :

X , Delete , or Ctrl - X

Removes each selected edge and fuses its surrounding faces into one, but only for edges with
exactly two neighboring faces.

The Adjust Last Operation panel offers the following options:

Dissolve Vertices
Dissolve the selected edges' vertices too, not merely the edges.

Angle Threshold
With Dissolve Vertices on, this preserves vertices at corners while still dissolving those in
flattish areas. Two faces count as a corner when the angle between their normals tops this value —
so coplanar faces register as 0°, not 180°.

Face Split
Where possible, splits surrounding faces so only a corner triangle merges rather than the whole
face. This shrinks the final "hole-filling" faces and evens them out.

### Dissolve Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete ‣ Dissolve Faces

Shortcut :

X , Delete , Ctrl - X , or F

Collapses each patch of connected faces down to one face.

Note

The F shortcut is normally used for creating faces, but when run on a selection of existing faces,
it dissolves them instead. See Dissolve Existing Faces.

| Before dissolving.  | After dissolving.  |

### Limited Dissolve 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete ‣ Limited Dissolve

Shortcut :

X or Delete

Trims the selected geometry by dissolving vertices and edges across flattish regions.

| Original mesh.  | Result of Limited Dissolve.  |

Max Angle
The largest angle between faces that still counts the surface as flat (and so dissolvable).
Specifically it's measured between face normals, so coplanar faces register as 0°, not 180°.

All Boundaries
Once the edges have dissolved per Max Angle , also dissolve every vertex at a boundary corner —
specifically, those with only two neighboring edges.

Delimit
Blocks merging across faces that differ in certain ways. Combine several of these by Shift - LMB
clicking them.

Normal :

Don't merge faces that have opposite
orientations.

Material :

Don't merge faces that have different materials.

Seam :

Don't dissolve edges that are marked as UV Seams.

Sharp :

Don't dissolve edges that are marked as Sharp.

UVs :

Don't merge faces that are disconnected in any UV map.

### Collapse Edges & Faces 

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Delete ‣ Collapse Edges & Faces

Shortcut :

X or Delete

Crushes each patch of connected edges and faces down to a single vertex — useful for collapsing
edge rings, for example.

| Selected edge rings.  | Edge rings collapsed.  |

Unlike the Dissolve operators, this one makes no n-gons and can add new vertices rather than only
removing old ones. The new vertices also pick up interpolated UVs, color attributes, and so on,
which makes it especially good for stripping detail by hand.

### Edge Loops 

Reference

Mode :

Edit Mode (Vertex or Edge select modes)

Menu :

Mesh ‣ Delete ‣ Edge Loops

Shortcut :

X or Delete

Dissolves the selected edge loops. It matches Dissolve Edges, save that it selects the surrounding
faces once done.

| Selected edge loop.  | Edge loop dissolved.  |

Note

In Blender terminology, an edge loop is any chain of connected edges –
it doesn't have to be a closed loop. See Select Edge Loops.

See also

- Vertex merging

- Triangles to Quads

- Un-Subdivide

## Separate

### Separate

Reference

Mode:

Edit Mode

Menu:

Mesh → Separate

Shortcut:

P

Breaks apart a mesh into two or more separate mesh objects.

Suzanne dissected neatly.

### Options

Selection
Isolates selected geometry from its surroundings and transfers it into a new object.

By Material
Divides the mesh by material slot—each slot becomes its own object, holding faces using that slot. Applied to the entire mesh, independent of selection.

By Loose Parts
Generates an object for each detached piece of the original mesh.
Applied to the entire mesh, independent of selection.

See also

- Split Selection for isolating geometry without moving it to a new object.

- Join for merging multiple objects into one.

## Sort Elements

### Sort Elements

Reference

Mode:

Edit Mode

Menu:

Mesh → Sort Elements…

Reorders the internal storage of selected mesh elements.

Hint

Enable Developer Extras in Preferences, then turn on the Indices overlay in the 3D Viewport to view element storage indices.

View Z Axis
Sort by the current viewport's Z axis, from farthest to nearest.

View X Axis
Sort by the current viewport's X axis, left to right.

Cursor Distance
Sort by distance from the 3D Cursor, nearest to farthest.

Material
Sort faces by material slot index, lowest to highest. Relative order within each "material group" persists.

Selected
Move all selected elements to the start (maintaining their relative order).
Warning: This also changes unselected element indices!

Randomize
Shuffle selected elements randomly.

Reverse
Flip the order of selected elements.

The Adjust Last Operation panel includes:

Type
The applied sort order (as listed above).

Elements
Choose to sort vertices, edges, or faces. Initially matches the current selection mode.

Reverse
Invert the default sort direction.

Seed
When using Randomize, different seeds generate different orderings.

## Move, Rotate, Scale

### Move, Rotate, Scale

Reference

Mode:

Edit Mode

Tool:

Toolbar → Move, Rotate, Scale

Menu:

Mesh → Transform → Move, Rotate, Scale

Shortcut:

G , R , S

Displace G, rotate R, or expand S selected vertices, edges, or faces.
Gizmos for transformation provide an alternative.

See also

- Manipulation in 3D Space

- Transform Orientation

- Transform Pivot Point

Proportional Editing influences these transformations.

Pressing G twice launches Vertex Slide or Edge Slide based on the current selection.

### Transform Panel

Reference

Mode:

Edit Mode

Panel:

Sidebar region → Item → Transform

This panel displays the selected vertex or edge properties.
When several items are selected, averages display instead.

X/Y/Z
Coordinates for the selected vertex. (With multiple selected vertices, the label reads "Median," though technically the panel computes geometric center rather than geometric median.)

Space
Coordinate display: Local Space or Global Space.

### Vertex Data

Bevel Weight
Commonly paired with the Bevel Modifier (with Affect as Vertices). The modifier normally applies identical bevel to all vertices, but when Limit Method is Weight, each vertex's Bevel Weight acts as a multiplier. This enables smaller or absent bevels on specific vertices.

Internally stored as an attribute called bevel_weight_vert. The Named Attribute Node in geometry nodes can also read this.

Crease
Higher Crease values make corners at the vertex appear more acute when using the Subdivision Surface Modifier.

Stored internally as an attribute named crease_vert.

Radius X/Y
The radii for the Skin Modifier.
Only displays when the mesh uses this modifier.

### Edge Data

When an edge is selected, these appear:

Bevel Weight
Commonly paired with the Bevel Modifier (with Affect as Edges). See vertex Bevel Weight above.

Stored internally as an attribute named bevel_weight_edge.
Also configurable through the Edge Bevel Weight operator.

Crease
Higher Crease values make corners at the edge appear more acute when using the Subdivision Surface Modifier.

Stored internally as an attribute named crease_edge.
Also configurable through the Edge Crease operator.

# Editing Uvs, Seams, Uvs Texture Space

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing UVs; Seams; UVs & Texture Space.

## Editing UVs

Editing UVs

After unwrapping, you need to arrange UV maps for texturing or painting. Your goals include:

Stitch UV map pieces back together.

Minimize unused space.

Enlarge faces where more detail is needed.

Resize stretched faces.

Shrink over-detailed faces.

With minimal wasted space, pixels can focus on maximum detail and fineness. A UV face ranges from single-pixel to entire-image size. Start with major adjustments, then fine-tune.

Transform Operations

Editor: UV Editor
Mode: Edit Mode
Toolbar: Move, Rotate, Scale, Transform
Menu: UV ‣ Transform

Move — G
Rotate — R
Scale — S
Shear — Shift - Ctrl - Alt - S

Axis Locking

After activating a transform tool, press X or Y to lock the transform axis. Holding MMB also constrains movement to X or Y.

Vertex Slide

Mode: Edit Mode
Menu: UV ‣ Transform ‣ Vertex Slide
Shortcut: Shift - V

Vertex Slide repositions a vertex along one of its adjacent edges. Activate with Shift - V. The selected vertex nearest the cursor becomes the control point. Drag along the edge direction to position the vertex, then LMB to confirm.

Factor — Controls the slide amount. Negative values slide toward one vertex; positive toward the other.

Even (E) — By default, offset is a percentage of edge length. When Even is active, vertices shift by a fixed value.

Flipped (F) — When active, vertices maintain equal distance from adjacent vertices instead of moving from their original position.

Clamp (Alt or C) — Toggle clamping the slide within edge bounds.

Edge Slide

Mode: Edit Mode
Menu: UV ‣ Transform ‣ Edge Slide

Slides one or more edges across adjacent faces (selection must define a valid loop).

Factor — Controls the slide amount. Negative slides toward one face; positive toward the other.

Even (E) — Forces the edge loop to match the shape of the adjacent edge loop. Press F to flip to the opposite vertex.

Flipped (F) — When Even is active, flips between adjacent edge loops that the active loop will match.

Clamp (Alt or C) — Toggle clamping within edge bounds.

Mirror Editing — Propagates the operation to mesh-symmetric elements (local X direction).

Randomize

Mode: Edit Mode
Menu: UV ‣ Transform ‣ Randomize

Randomizes scale, rotation, and offset of selected UV islands. Works similarly to Randomize Transform in the 3D view.

Random Seed — Changes the pseudo-random seed for different results.

Location — Amount of location randomization.

Rotation — Amount of rotation randomization.

Scale Even — Apply identical scale to U and V.

Scale — Amount of scale randomization in U and V.

Mirror

Mode: Edit Mode
Menu: UV ‣ Mirror
Shortcut: Ctrl - M

Mirror UVs on the X or Y axis by selecting the mirror option. Use hotkeys X or Y, or hold MMB and drag in the mirror direction.

Copy Mirrored UV Coordinates

Mode: Edit Mode
Menu: UV ‣ Copy Mirrored UV Coordinates

Copies UVs from one side of a mirrored mesh to the other. Only affects selected vertices on both sides.

Axis Direction — Positive/Negative.

Precision — Tolerance for finding vertex duplicates.

Snap

Mode: Edit Mode
Menu: UV ‣ Snap
Shortcut: Shift - S

UV snapping works similarly to 3D snapping. Pixel snap options require an image to be loaded.

Selected to Pixels — Moves selection to the nearest pixel.

Selected to Cursor — Moves selection to the 2D cursor.

Selected to Cursor (Offset) — Moves selection center to the 2D cursor while preserving vertex offsets.

Selected to Adjacent Unselected — Moves selection to adjacent unselected elements.

Cursor to Pixels — Snaps the cursor to the nearest pixel.

Cursor to Selected — Moves the cursor to the selection center.

Cursor to Origin — Places the cursor at (0, 0, 0).

Merge

Mode: Edit Mode
Menu: UV ‣ Merge
Shortcut: M

At Center — Moves selected UVs to their average position.

At Cursor — Moves selected UVs to the 2D cursor location.

By Distance

Mode: Edit Mode
Menu: UV ‣ Merge ‣ By Distance

Merges selected UVs within the specified distance.

Merge Distance — Maximum distance between merged vertices.

Unselected — Merge selected UVs to unselected ones.

Shared Vertex — Merge UVs corresponding to the same mesh vertex (even with different UV coordinates).

Split

Mode: Edit Mode
Menu: UV ‣ Split
Shortcut: Alt - M

Selection — Disconnects the selection from the rest of the UV map, duplicating the border edge to unselected elements.

UV Rip Move

Mode: Edit Mode
Menu: UV ‣ UV Rip Move
Shortcut: V

UV Rip Move separates selected UV elements from connected components, creating a rip in the map. After separation, the selection enters move mode for precise repositioning.

This isolates UV islands or unwraps overlapping elements without affecting surrounding geometry.

Two images show the before and after states of a rip operation.

Note: UV Rip Move is incompatible with Sync Selection. Disable Sync Selection in the UV Editor to use this tool.

See also: UV Rip Tool (modal version) and Mesh editing Rip (similar 3D Viewport functionality).

Unwrap

Mode: Edit Mode
Menu: UV ‣ Unwrap
Shortcut: U

Blender offers several UV mapping methods. Simpler projection methods map 3D space to 2D using formulas that interpolate positions toward a point, axis, or plane. Advanced methods suit complex models with specific applications.

Available unwrap methods include: Unwrap, Smart UV Project, Lightmap Pack, Follow Active Quads, Cube Projection, Cylinder Projection, Sphere Projection.

Pin & Unpin

Mode: Edit Mode
Menu: UV ‣ Pin/Unpin
Shortcut: P, Alt - P

Pinned UVs remain fixed during subsequent unwrap operations. Select a UV and press P to pin it; press Alt - P to unpin.

Pinning is most effective with Unwrap on organic objects. For example, when using a Mirror Modifier on a symmetrical object, pin the UVs along the mirror axis, align them on the X axis, and they stay locked in place.

The Pinch and Relax sculpting tools skip pinned UVs, allowing you to pin borders or interior holes for finer sculpting control.

With Live Unwrap enabled, pinning two or more UVs lets you interactively unwrap by moving or scaling the pinned UVs. You can even use the Grab tool to move pinned UVs, fitting islands to specific shapes or regions.

Invert Pins

Mode: Edit Mode
Menu: UV ‣ Invert Pins

Pin all unpinned selected UVs and unpin all currently pinned ones.

Mark/Clear Seams

Mode: Edit Mode
Menu: UV ‣ Mark/Clear Seam

See Seams.

Seams from Islands

Mode: View mode
Menu: UV ‣ Seams from Islands

Adds seams at the boundaries of existing UV islands, useful when modifying the UVs of already-unwrapped meshes.

Pack Islands

Mode: Edit Mode
Menu: UV ‣ Pack Islands

Pack Islands optimizes the UV layout by adjusting islands to fill the texture space efficiently. Based on options selected, the tool scales, translates, and rotates islands, ensuring specified margins exist between them to maximize UV space.

Pinned islands can have additional restrictions applied.

Shape Method

How to consider each island's shape:

Exact Shape (Concave) — Uses the island's complete shape, including holes and concave regions.

Boundary Shape (Convex) — Accounts for the boundary (Convex Hull), not placing islands inside holes.

Bounding Box — Uses the simple bounding box.

Scale — Scale islands to fill the unit square, or pack toward the lower left corner.

Rotate — Allows rotation alongside translation and scaling to optimize usage.

Rotation Method

Allowable rotations:

Any — Any rotation improving packing.

Axis-aligned — Islands rotate to fit the smallest rectangle, then only 90-degree turns.

Cardinal — Only 90-degree rotations (like compass directions).

Margin Method

How empty space is calculated:

Scaled — Multiply margin by the scale of existing UVs.

Add — Simple addition of margin.

Fraction — Precise fraction specification of the UV unit square (slower).

Margin — Scale for empty space between islands.

Lock Pinned Islands

Pinned Islands are those with any pinned UVs. When enabled, they stay in place while others pack around them.

Lock Method

How Pinned Islands are packed:

Scale — Pinned Island scale doesn't change.

Rotation — Pinned Islands don't rotate.

Rotation and Scale — Pinned Islands translate only.

Merge Overlapping

Detects and temporarily combines overlapping islands before packing, preserving their relative rotation and position.

Pack To

Where islands end up after packing:

Closest UDIM — Pack to the UDIM grid nearest the selection center.

Active UDIM — Pack to the active UDIM image tile or the UDIM grid at the 2D cursor.

Original bounding box — Find the original bounding box, pack islands, then move them back inside.

Custom Region — Pack into a user-defined custom region (requires Custom Region enabled). Allows packing into reserved atlas regions, trim sheet zones, or texture slot layouts.

Pack Islands performance depends heavily on selected options. Fastest results use "Bounding Box" shape method and "Add" margin method. Enabling "Rotate" slightly impacts performance but often improves efficiency. The "Fraction" margin method requires significantly more computation and may take 10 times longer. "Exact shape" and "Boundary shape" methods are much slower than "Bounding Box".

Average Island Scale

Mode: Edit Mode
Menu: UV ‣ Average Island Scale

Scales each UV island so all approximate the same scale.

Non-Uniform — Reduces average texture stretching within islands by scaling U and V axes independently.

Shear — Reduces average texture shearing by shearing the U axis.

Arrange/Align Islands

Mode: Edit Mode
Menu: UV ‣ Arrange/Align Islands

Aligns selected UV islands along a straight line on the UV grid. Customizable starting positions, alignment reference, sorting order, and spacing allow organizing UV layouts and modular texture pieces consistently.

Initial Position

Reference point for calculating initial alignment:

Bounding Box — Uses the bounding boxes of selected islands.

UV Grid — Aligns relative to the UV grid origin (0-1 UV tile).

Active UDIM — Aligns based on the active UDIM tile.

2D Cursor — Uses the current 2D cursor position.

Axis

The axis along which to arrange islands:

X — Align horizontally.

Y — Align vertically.

Align

How islands align relative to each other:

Min — Aligns by minimum boundary.

Max — Aligns by maximum boundary.

Center — Aligns by the center of the largest island.

None — Keeps each island's original offset and alignment.

Order

How islands are ordered:

Largest to Smallest — Sorts by area, largest first.

Smallest to Largest — Sorts by area, smallest first.

Fixed — Keeps the current selection order.

Margin

Space between arranged islands, in UV units.

Set User Region

Mode: Edit Mode
Menu: UV ‣ Set User Region
Shortcut: Ctrl - B

Defines a rectangular region in the UV Editor for use as a Custom Region. Once defined, this region becomes available as a Pack To target in Pack Islands by choosing Custom Region and enabling Custom Region.

Custom Region

Mode: Edit Mode
Menu: UV ‣ Custom Region
Shortcut: Ctrl - Alt - B

Enables or disables the use of a Custom Region for UV operations like Pack Islands. When enabled, the previously defined user region (created with Set User Region) becomes active and visible. This region defines boundaries for UV island packing or manipulation. Disabling restores default behavior where UV operations apply to the standard unit square or active UDIM tile.

Minimize Stretch

Mode: Edit Mode
Menu: UV ‣ Minimize Stretch

Minimize Stretch reduces UV stretch by minimizing angle differences between 3D and UV space. This operation resembles the Relax tool with the Geometry Method but uses a different algorithm.

Fill Holes — During minimize stretch, internal holes are filled with temporary polygons to prevent surrounding UV stretching and overlap.

Blend — Fraction (0-1) of the original UVs to blend after minimizing. Zero represents fully minimized stretch; 0.5 is halfway between original and minimized UVs.

Iterations — More iterations produce smoother UVs but take longer.

Stitch

Mode: Edit Mode
Menu: UV ‣ Stitch
Shortcut: Alt - V

Stitch joins selected UVs that share vertices. Use Limit and Limit Distance in the Adjust Last Operation panel to restrict stitching by distance.

Align

Mode: Edit Mode
Menu: UV ‣ Align
Shortcut: Shift - W

Positions selected UV vertices along a line specified by Axis.

Axis

Straighten — Positions UV vertices along the line defined by the endpoints.

Straighten X — Positions UV vertices horizontally along the line defined by endpoints.

Straighten Y — Positions UV vertices vertically along the line defined by endpoints.

Align Auto — Positions UV vertices automatically, choosing direction based on existing alignment.

Align Vertically — Positions UV vertices vertically along the line defined by the selection midpoint.

Align Horizontally — Positions UV vertices horizontally along the line defined by the selection midpoint.

Position Mode (Align Vertically / Align Horizontally)

How the final alignment line position is calculated:

Mean — Aligns UVs along the average position.

Minimum — Aligns UVs along the smallest coordinate value.

Maximum — Aligns UVs along the largest coordinate value.

Align Rotation

Mode: Edit Mode
Menu: UV ‣ Align Rotation

Aligns entire islands to the U or V axis. Three operation methods specify the alignment source and whether to align both axes or just V.

Auto method aligns islands so UV edges align with U or V axis; best for quads and organic meshes.

Edge method aligns only selected edges to the V axis; works best for aligning a particular edge or loop.

Geometry method considers 3D geometry. Choose X, Y, or Z axis. Edges with positive extent in the chosen axis rotate to extend upward in V axis. Works best for multiple islands sharing a geometric property.

In Auto method, edges end up aligned up/down/left/right depending on pre-existing island orientation. In Edge method, selected edges align up or down in V axis depending on current UV island orientation. In Geometry method, alignment always points upward in V axis, ignoring previous orientation.

Move on Axis

Mode: Edit Mode
Menu: UV ‣ Move on Axis

Moves selected UV coordinates along a chosen axis by a specified distance. Designed for precise adjustments and supports multiple movement modes, especially useful with number pad keys.

Use these shortcuts to move UVs directly:

Numpad8 / Numpad2 — Move up or down.

Numpad4 / Numpad6 — Move left or right.

Type

Movement unit:

Dynamic — Move using active grid size. Ctrl + number pad activates this.

Pixel — Move by pixel increments. Shift + number pad activates this.

UDIM — Move by full UV tiles (1.0 unit). Number pad without modifiers uses this.

Axis

Direction to move:

X Axis — Move horizontally.

Y Axis — Move vertically.

Distance — The distance to move, in selected units.

Copy UVs

Mode: Edit Mode
Menu: UV ‣ Copy UVs
Shortcut: Ctrl - C

Copy UVs stores the topology and UV coordinates of selected islands into an internal clipboard for use with Paste UVs.

Note: The internal clipboard is not shared between Blender instances.

Paste UVs

Mode: Edit Mode
Menu: UV ‣ Paste UVs
Shortcut: Ctrl - V

Paste UVs matches the topology of a stored island to currently selected islands. If a match is found, the stored UVs paste onto the selection.

For example, if a triangle-quad-quad sequence is stored, selecting a different triangle-quad-quad elsewhere pastes the stored UVs onto the new selection.

For best results, use the Rip tool or UV ‣ Split ‣ Selection before pasting.

Show/Hide Faces

Mode: Edit Mode
Menu: UV ‣ Show/Hide Faces

Reveal Hidden — Alt - H

Hide Selected — H

Hide Unselected — Shift - H

Export UV Layout

Mode: Edit Mode
Menu: UV ‣ Export UV Layout

When using external applications, this exports the UV layout so you know where on the mesh you are painting.

Note: This is an add-on activated by default.

Proportional Editing

Mode: Edit Mode
Header: Proportional Editing
Menu: UV ‣ Proportional Editing
Shortcut: O

Proportional Editing works in UV editing with the same controls as in the 3D Viewport. See Proportional Editing in 3D for complete reference.

UV Options

Mode: Edit Mode
Menu: UVs

Live Unwrap
Continuously unwraps selected UV islands when transforming pinned vertices. This differs from the Live Unwrap option in the 3D Viewport.

Round to Pixels
During UV transforms, Round to Pixels helps match features in the image and ensures precise horizontal, vertical, or diagonal alignment.

Note: Round to Pixels applies after any snapping modes.

Disabled — UVs don't round.

Corner — UVs round to the nearest pixel corner.

Center — UVs round to the nearest pixel center.

Constraining to Image Bounds

For standard textures, this prevents UVs from moving outside the 0-1 range. For UDIM textures, this prevents UVs from moving outside the nearest UDIM tile.

3D Viewport UV Operations

Rotate UVs

Editor: 3D Viewport
Mode: Edit Mode
Menu: Face ‣ Face Data ‣ Rotate UVs

The UV orientation on each face is defined by that face. If an image appears upside down or sideways, use Face ‣ Rotate UVs in 3D Viewport Face Select mode to rotate UVs in 90-degree increments per face.

Reverse UVs

Editor: 3D Viewport
Mode: Edit Mode
Menu: Face ‣ Face Data ‣ Reverse UVs

Reverse UVs mirrors the UVs per face, flipping the image so it displays reversed.

## Seams

Seams

For many simple models, Cube, Cylinder, Sphere, or standard Unwrap operators produce good UV layouts. Complex meshes with heavy indentations benefit from defined seams to guide and limit the unwrap operation.

Like fabric seams, a seam marks where image/cloth edges join. In unwrapping, the UV map is discontinuous at seams — think of peeling an orange or skinning an animal. You make cuts, peel away the skin, then flatten it with some stretching. These cuts are seams.

A simple seam illustration shows a cylindrical mesh with one seam cut.

Balance seam quantity against stretching. More seams reduce stretching but complicate texturing. Aim for few seams with minimal stretching. Hide seams in inconspicuous locations. With 3D projection painting, seams matter less; with 2D texturing, edge matching across seams is difficult.

Workflow

Mark seams.

Unwrap.

Adjust seams and iterate.

Manually refine UVs.

Marking Seams

Editor: 3D Viewport or UV Editor
Mode: Edit Mode
Toolbar/Menu: UV ‣ Mark/Clear Seam or Edge ‣ Mark/Clear Seam

Select an edge and press Ctrl - E to mark a seam, or Ctrl - E to clear it.

The back edge of a cylinder shows seaming applied to hide the seam, with standard unwrap producing clean face distribution.

Use Select Linked in Face Select mode to verify seams. It selects all connected faces up to a seam. If unintended faces are selected, your seam isn't continuous (though continuous seams aren't strictly required).

Think of seaming as cutting and spreading the object flat with minimal tearing. On the example model, the back-most cylinder edge is seamed, side seams separate head halves, and ear edges separate front from back. Eyes are disconnected sub-meshes and unwrap independently. A vertical seam runs along the back of the head so each side flattens separately.

Seams also limit unwrapped regions. For texturing a head, you might not need the top/back scalp (hidden by hair), so define a seam at the hairline. Select a frontal face and linked faces before unwrapping; the selection stops at the hairline, leaving the scalp unwrapped.

For bilateral objects (heads, bodies), seam along the mirror axis — split the head or body down the middle in front view. On unwrap, overlay both halves onto the same texture space so pixels for the right side match the left, and the right face matches the left.

Note: You don't need "one perfect unwrapping everywhere". You can have multiple UV unwrappings with different approaches in different areas.

Seams from Islands

Mode: View mode
Menu: UV ‣ Seams from Islands

Adds seams at the boundaries of existing UV islands, useful for modifying the UVs of already-unwrapped meshes.

## UVs & Texture Space

UVs and Texture Space

UV Maps

Mode: All Modes
Panel: Properties ‣ Data ‣ UV Maps

For mesh objects, find UV maps in the Data tab of the Properties editor. After selecting a map, view and edit it in the UV editor.

One mesh can contain multiple UV maps (one per texture, for example), or a single UV map can serve multiple textures.

/ Active Render
Marks the UV map as the default for rendering. The Active Render UV map determines:

The UV Pass for compositing.

The Texture Coordinate Node for material shading.

The UV Map Node for material shading when no specific UV map is selected.

Add UV Map
Duplicates the selected UV map or creates a new one if the list is empty.

Remove UV Map
Removes the selected UV map.

Texture Space

Mode: All Modes
Panel: Properties ‣ Data ‣ Texture Space

This panel configures the object's Texture Space — a 3D box for generating texture coordinates without UV mapping. Visualize texture space via the Viewport Display panel option.

Texture Mesh (Mesh objects only)
Use another mesh for texture indices. Both objects' vertices must align precisely or UVs distort.

Auto Texture Space
Automatically calculates the texture space.

Location X, Y, Z; Size X, Y, Z
Manually define texture space relative to the object. You can also edit in the 3D Viewport (see Editing below).

Match Texture Space (Curve objects only)
Adjusts Location and Size to match the object's bounding box, disabling Auto Texture Space.

Editing Texture Space

Mode: Object Mode and Edit Mode
Menu: Object ‣ Transform ‣ Move/Scale Texture Space

Click a menu item, move the mouse to adjust texture space, and LMB to confirm. Use keyboard shortcuts to lock axes; see the status bar.

Accessing Texture Space

In material shader setup, use the Generated output of the Texture Coordinate Node to read the 3D coordinate within the object's texture space. Pass this to a texture node.

Texture spaces lack rotation support. Use a Mapping Node to manually rotate coordinates in the material shader instead.

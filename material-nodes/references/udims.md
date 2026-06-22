# Udims, Editing Meta Objects, Displace Modifier, Smooth Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: UDIMs; Editing Meta Objects; Displace Modifier; Smooth Modifier; Bevel Modifier; Boolean Modifier; Curve to Tube Modifier; Decimate Modifier; Mirror Modifier.

## UDIMs

UV coordinate systems have a limitation: a single texture covers the entire model at one resolution. When geometry varies significantly in size and importance, this causes problems—smaller regions waste texture resolution while large regions lack sufficient pixel density.

UDIMs solve this by partitioning UV space across multiple texture images. Each tile is a separate texture in a grid. Within each tile, UV coordinates span from 0 to 1 (or 1 to 2, 2 to 3, etc. by column), and each tile receives its own image. Multiple textures of different resolutions can be assigned per tile—for instance, 4k for primary surface details, 2k and 1k for secondary regions.

The main tile carries index 1001. Adding tiles increments this: 1002 appears to the right, up to 1010 in the first row. Subsequent rows begin at 1011 directly above the main tile.

Start with an unwrapped model as you would for standard UV mapping. Decide on the number of textures needed—a reasonable starting point is three: 4k, 2k, and 1k resolutions. Create corresponding images.

Move UV islands to their assigned tiles and manage them like a standard layout. Once correctly positioned, add proper textures to tiles. Existing images cannot be directly placed into tiles; instead, create the tile, save it, then replace the saved file with the desired texture (either by overwriting the file or editing it in external software).

In addition to external editing, painting directly on UDIM textures is supported in both 2D and 3D painting modes.

Filenames can include special placeholders that expand based on the tile being loaded or saved. These tokens, enclosed in angle brackets, enable automatic tile identification.

`<UDIM>` becomes a four-digit code calculated as 1001 plus the u-tile index plus (v-tile index times 10). `<UVTILE>` expands to the format u(u-value)_v(v-value). For example, `texture.<UDIM>.png` might expand to `texture.1021.png`, while `texture.<UVTILE>.png` becomes `texture.u1_v3.png`.

The UDIM Tiles panel is used in the Image Editor or UV Editor to manage tiles—add new ones, delete existing ones, or fill them with generated content.

The panel shows all tiles linked to the primary 1000-index tile. Double-clicking a tile name allows renaming it for clarity.

Add Tile lets you specify a starting index and count. Tiles must begin at 1001 and typically ascend sequentially.

An optional label can be displayed in the viewport instead of the numeric index.

Fill occupies a tile with a generated image.

Remove Tile deletes a selected tile and its contents if unsaved.

Note: unfilled tiles are not saved.

## Editing Meta Objects

Meta objects can contain multiple distinct elements within a single object rather than distributing them across separate objects. Each element has its own shape and control properties.

In Edit Mode, selecting an element and pressing X or Del removes it; no extended options are available.

To convert a metaball surface into a standard mesh, use the Convert command from Object Mode.

Meta objects are organized into "families" based on the object name before the first period. For example, "MetaPlane.001" belongs to the MetaPlane family. Objects in the same family interact with one another.

Each family is controlled by a base meta object—the one whose name contains no period. If you have MetaThing, MetaThing.001, and MetaThing.round, the base is MetaThing. The base governs overall surface properties, geometric resolution, the field threshold, and spatial transformation, and it holds material and texture settings. Other metas in the family operate as child elements dependent on the base.

When organizing across multiple scenes, ensure the base meta remains in the same scene as its child metas to avoid rendering anomalies.

The base meta is visually identifiable by its orange mesh outline; child metas display black selection rings. Selecting any meta in a family highlights the entire family's surface.

The base meta controls how the overall surface is polygonalized (converted to mesh geometry). Transforming the base alters the mesh structure for all children. Transforming children, however, does not change the overall mesh structure—only the base's transformations recalculate it.

When the base is scaled down, the mesh subdivision increases while the shape remains the same; child mesh structures intensify their vertex density without changing their physical size.

## Displace Modifier

The Displace modifier shifts vertices based on a texture's brightness values. Procedural or image textures work equally well.

Displacement direction can be along a local axis, along vertex normals, or read as RGB values to displace simultaneously in X, Y, and Z (Vector Displacement).

Texture names the source texture. If empty, the default value is 1.0 (white).

Coordinates specifies the sampling method (see common masking options for full reference).

Direction selects the displacement axis:

X, Y, Z displaces along each axis.

Normal displaces along computed vertex normals.

Custom Normal displaces along averaged custom normals.

RGB to XYZ reads Red for X, Green for Y, Blue for Z displacement.

Space, when using X/Y/Z or XYZ direction, selects local or global axis alignment.

Strength scales the final displacement value. Negative values invert the effect.

Formula: vertex_offset = (texture_value - Midlevel) × Strength

Midlevel sets the texture value treated as zero displacement. Values below it displace negative; values above displace positive.

Formula: displacement = texture_value - Midlevel

Blender's color/luminosity values typically range 0.0–1.0, not 0–255.

Vertex Group controls the effect via group weights.

Invert reverses the group influence.

## Smooth Modifier

The Smooth modifier flattens the angles between adjacent faces, equivalent to the Smooth tool in Edit Mode. Vertex count stays constant—no subdivision occurs.

The modifier can do more than smoothing. Adjusting the control factor outside the 0.0–1.0 range, including negative values, produces interesting deformations.

Axis toggles deformation in X, Y, and/or Z directions.

Factor controls smoothing intensity. Higher values increase the effect. Values beyond the 0.0–1.0 range distort the mesh.

Repeat sets the iteration count, equivalent to applying Smooth multiple times.

Vertex Group restricts the effect to group vertices, enabling selective real-time smoothing via weight painting.

Invert reverses the group influence.

The algorithm is straightforward: each vertex moves toward the average position of its topologically connected neighbors—a geometric equivalent of image blurring.

## Bevel Modifier

The Bevel modifier bevels the edges of the mesh it's applied to, with some control over how and where the bevel is applied — a non-destructive alternative to the Bevel operation in Edit Mode.

Options:
Affect:
- Vertices: only the areas near vertices are beveled; the edges stay unchanged.
- Edges: bevel the edges, creating intersections at vertices.
(For example, three cubes at 0.1, 0.3, and 0.5 bevel widths with the Vertices option selected.)
Width Type — defines how Width is interpreted to determine the bevel amount.
- Offset: the distance from the new edge to the original.
- Width: the distance between the two new edges formed by the bevel (or the edges on either side of the bevel when there's more than one segment).
- Depth: the perpendicular distance from the new bevel face to the original edge.
- Percent: the percentage of the adjacent edge length that the new edges slide along.
- Absolute: the exact distance along edges adjacent to the beveled edge; it differs from Offset when the unbeveled edges attached to beveled edges meet at an angle other than a right angle.
Width — the size of the bevel effect (see Width Type above). (E.g. three cubes at 0.1, 0.3, and 0.5 bevel widths.)
Segments — the number of edge loops added along the bevel's face.
Limit Method — controls where the bevel is applied to the mesh.
- None: no limit; all edges are beveled.
- Angle: bevel only edges whose angle of adjacent face normals plus the defined Angle is less than 180 degrees — meant to bevel only an object's sharp edges without affecting its smooth surfaces.
- Weight: use an attribute to determine the bevel width; at bevel weight 0.0, no bevel is applied. Any attribute on the input mesh can be chosen — by default the bevel_weight_edge and bevel_weight_vert attributes adjusted in edit mode are used, and the modifier conveniently lists the original mesh's attributes in the dropdown, though attributes created by previous modifiers can also be used (attributes with non-matching domains or types are automatically interpolated to the correct type).
- Vertex Group: use weights from a vertex group to determine the bevel width; at vertex weight 0.0, no bevel is applied, and an edge is beveled only if both of its vertices are in the group.
Invert — invert the influence of the selected vertex group, so the group now represents vertices that will not be deformed by the modifier; the setting reverses the group's weight values.

Profile — Superellipse: creates a bevel with a uniform concave or convex curve.
Shape — the shape of the bevel, from concave to convex; it has no effect if Segments is less than 2.
Custom Profile — a widget for a user-defined profile with more complexity than the single Shape parameter; the modal tool can toggle the custom profile, but the profile's shape is only editable in the options panel after the operation is confirmed. The profile starts at the widget's bottom-right and ends at its top-left, as if between two edges meeting at a right angle; control points are created in the widget, then the path is sampled with the number of segments from the Bevel modifier.
Miter Shape — the shape of the miter patterns, from concave to convex; it has no effect if Segments is less than 2. (Note: the Miter Shape slider stays active when miters are enabled, because it still controls the shape of the miter profiles.)
Presets — the Support Loops and Steps presets build dynamically depending on the bevel's number of segments, so if the segments change the preset must be re-applied.
Sampling — samples are first added to each control point, then, if there are enough, divided evenly between the edges. The Sample Straight Edges option toggles whether samples are added to edges with sharp control points on either side; if there aren't enough samples to give each edge the same number, they go to the most curved edges, so use at least as many segments as there are control points.

Geometry:
Miter Inner/Outer — a miter is formed where two beveled edges meet at an angle: on the side where the angle is greater than 180 degrees it's an outer miter, and where it's less than 180 degrees it's an inner miter. Each can be set to one of these patterns:
- Sharp: edges meet at a sharp point, with no extra vertices introduced on the edges.
- Patch: edges meet at a sharp point, but two extra vertices are introduced near the point so the edges and faces are less pinched than in the Sharp case; this makes no sense for inner miters, so it behaves like Arc for them.
- Arc: two vertices are introduced near the meeting point, joined by a curved arc.
(The Spread slider controls how far the new vertices are from the meeting point, and the Profile curve widget controls the shape of the arc.)
Spread — the value used to spread extra vertices apart for non-sharp miters; available when Miter Inner is set to Arc.
Intersections — when more than two beveled edges meet at a vertex, a mesh is created to complete the intersection between the generated geometry; this option controls the method used to create that mesh.

Grid Fill (the default intersection method) continues the bevel profile through the intersection, or with a custom profile, creates a smooth grid within the boundary.

Cutoff creates a terminal face at each beveled edge entering the vertex, most useful for custom profiles when the intersection becomes too complex for a smooth grid. When inner corners of cutoff faces meet, no central face forms. The direction depends on the original vertex normal.

Clamp Overlap restricts beveled edge width to prevent overlapping with nearby geometry.

Loop Slide attempts to slide bevel along unbeveled edges when mixed with beveled edges; disabling this can produce more uniform bevel widths.

Harden Normals adjusts per-vertex face normals of bevel faces to match surrounding surfaces, maintaining flat appearance of original faces while bevel faces shade smoothly into them. This requires a custom split normals attribute (automatically created if missing).

Seam propagation maintains expected seam continuity when a seam edge crosses a non-seam edge and all are beveled.

Sharp mark handling applies the same principle to sharp edges.

Material Index selects the material slot for bevel faces; -1 uses the material from the nearest original face.

Face Strength modes: None applies no strength, New sets bevel edge faces to Medium and vertex faces to Weak, Affected also marks adjacent faces as Strong, All marks remaining faces as Strong and works with Weighted Normals modifier (Face Influence enabled).

## Boolean Modifier

The Boolean modifier combines multiple meshes using a Boolean operation (for example, applying the Intersection, Union, and Difference of a sphere and a cube).
Warning: only Manifold meshes are guaranteed to give proper results; non-manifold ones (especially meshes with holes) usually work but may produce odd glitches and artifacts, and the Manifold Solver won't work at all on non-manifold meshes.
Tip: if your objects show their edges (Properties ‣ Object ‣ Viewport Display, enable Wireframe), you'll see the edge-creation process as you move objects around; you can also enable X-Ray to see inside the objects.
See also Intersect (Boolean) for one-off Boolean operations within a mesh in Edit Mode.

Options:
Operation:
- Intersect: keep only the volume that's inside both the modified mesh and all the source meshes.
- Union: add the source meshes to the modified mesh while removing any interior faces.
- Difference: cut the source meshes out of the modified mesh.
Operand Type:
- Object: the source is a single mesh object.
- Collection: the source is a collection of any number of mesh objects; if the Solver is Float, the Intersect operation isn't allowed.
Object — the source mesh object.
Collection — the source collection; may be empty if the Solver is Exact, in which case the modifier simply removes the modified mesh's interior (self-intersecting) geometry.
Solver — the algorithm used to perform the Boolean operation.
- Float: a simple solver offering good performance but no support for overlapping geometry.
- Exact: a complex solver offering the best results with full support for overlapping geometry, but much slower.
- Manifold: usually the fastest solver, but only works on Manifold meshes (plus the special case of Difference with a plane).

Solver Options:
Materials (Exact solver) — the method for setting materials on the new faces.
- Index Based: map the source mesh's first material to the modified mesh's first, the second to the second, and so on; if a source face's material index exceeds the modified mesh's material-slot count, the modified mesh's first material is used.
- Transfer: use the same materials as the source mesh, adding new material slots to the modified mesh as needed, and for empty slots fall back to the source mesh's material index.
Self Intersection (Exact solver) — correctly handle self-intersection in the participating meshes, at the cost of performance.
Hole Tolerant (Exact solver) — optimize the Boolean output for non-manifold geometry at the cost of increased computation time; because of the performance impact, enable it only when the Exact solver shows errors with non-manifold geometry.
Overlap Threshold (Float solver) — the maximum distance between two faces to consider them overlapping; this helps work around the solver's limitation, and if the result still isn't as expected, try the Exact solver.

## Curve to Tube Modifier

This node generates a mesh tube along an input curve, creating cylindrical or profiled geometry following the curve shape, useful for modeling cables, pipes, wires, and other tubular forms.

Scale multiplies the curve's radius attribute to determine the output tube's radius.

Profile Mode: Round uses a circular cross-section (with configurable resolution), Custom uses a provided object or geometry as the profile shape.

Resolution Round controls the number of points around the circular profile and sets cap resolution.

Profile Input Custom can source from an Object or from input Geometry directly.

Shade Smooth enables smooth shading on the output.

Resampling reorders the curve before tube generation for evenly distributed geometry. Resample Mode: Evaluated uses existing curve points, Auto calculates sample spacing automatically, Count fixes the point count, Length fixes the spacing distance.

Scale Auto applies a multiplier to the automatic resample length.

Caps fill tube ends: Flat uses an n-gon, Round uses a half-circle, Custom uses provided geometry or an object. Smooth transitions between tube body and caps instead of creating hard edges.

UV Map generation creates or updates a UV map on the output. Parameter U and V can use Factor (normalized 0-1), Length (real curve length and circumference), or Index (point and profile indices). Consider Curve Radius includes radius variations in UV generation.

## Decimate Modifier

The Decimate modifier reduces a mesh's vertex/face count with minimal change to its shape. It's not usually used on carefully, economically modeled meshes (where every vertex and face is needed to define the shape), but it's useful when a mesh results from complex modeling, sculpting, and/or applied Subdivision Surface/Multiresolution modifiers — to cut the polygon count for a performance gain or simply remove unnecessary vertices and edges. Unlike most modifiers, this one doesn't let you visualize the changes in Edit Mode, and it displays the number of faces remaining as a result.

Options:
Collapse — merges vertices together progressively, taking the mesh's shape into account.
Ratio — the ratio of faces to keep after decimation. At 1.0 the mesh is unchanged; at 0.5 edges are collapsed so half the faces remain (see note below); at 0.0 all faces are removed.
Note: although Ratio is directly proportional to the number of remaining faces, triangles are used when calculating the ratio, so if your mesh contains quads or other polygons the remaining face count will be larger than expected, because those stay unchanged if their edges aren't collapsed — this is only true when the Triangulate option is disabled.
Symmetry — maintain symmetry on a single axis.
Triangulate — keep any triangulated geometry resulting from the decimation process.
Vertex Group — a vertex group controlling which parts of the mesh are decimated.
Factor — how much influence the Vertex Group has on the decimation.

Un-Subdivide — think of it as the reverse of subdivide: it attempts to remove edges that were the result of a subdivide operation. It's intended for meshes with mainly grid-based topology (to avoid uneven geometry); if additional editing was done after the subdivide, the results may be unexpected.
Iterations — the number of times to run the un-subdivide; two iterations equal one subdivide operation, so you'll usually want even numbers.

Planar — reduces detail on forms made up of mainly flat surfaces.
Angle Limit — dissolve geometry forming angles (between surfaces) higher than this setting.
Delimit — prevent dissolving geometry in certain places.
- Normal: don't dissolve edges on the borders of areas where the face normals are reversed.
- Material: don't dissolve edges on the borders between different assigned materials.
- Seam: don't dissolve edges marked as UV Seams.
- Sharp: don't dissolve edges marked as Sharp.
- UVs: don't dissolve edges that are part of a UV map.
All Boundaries — when enabled, all vertices along the boundaries of faces are dissolved; this can give better results when using a high Angle Limit.

## Mirror Modifier

The Mirror modifier mirrors a mesh along its local X, Y, and/or Z axes, across the Object Origin. It can also use another object as the mirror center, then use that object's local axes instead of its own.

Options:
Axis — the X, Y, Z axis to mirror along, i.e. the axis perpendicular to the mirror plane of symmetry. To picture how the axis maps to direction: mirroring on the X axis turns the original mesh's positive X values into negative X values on the mirrored side. You can select more than one axis for more copies — one axis gives a single mirror, two axes four mirrors, and all three axes eight mirrors.
Bisect — if the mesh already sits on both sides of the mirror plane, cut it by that plane and keep only one side (the "positive" one by default) to perform the mirror.
Flip — when Bisect is enabled on an axis, switch which side is kept and mirrored (enabled, the "negative" side is kept instead of the "positive").
Mirror Object — an Object Selector to pick an object (usually an empty) whose position and rotation define the mirror planes (instead of those of the modified object); you can animate it to move the mirror axis.
Clipping — stop vertices from moving through the mirror plane(s) when you transform them in Edit Mode. If it's enabled while vertices are beyond the plane and outside the Merge Distance, they won't merge, but once within Merge Distance they snap together and can't move past the plane.
Note: vertices on the mirror plane can't move away from it while Clipping is enabled — disable it to move them along the mirror axis again.
Merge — where a vertex sits in the same place (within Merge Distance) as its mirror, merge it with the mirrored vertex.
Merge Distance — the maximum distance between a vertex and its mirror copy at which they merge (snapping onto the mirror plane); needs Merge enabled.
Bisect Distance — the distance from the bisect plane within which vertices are removed.

Data:
Flip UV — mirror the UV texture coordinates across the middle of the image; e.g. a vertex with UV coordinates of (0.3, 0.9) gets a mirror copy with UV coordinates of (0.7, 0.1).
UV Offsets — how far to shift mirrored UVs on the U/V axes; useful for baking (since overlapping UVs can cause artifacts in the baked map), so the UVs can be moved outside the image and left out of baking while still used for display.
Vertex Groups — try to mirror existing vertex groups, given these prerequisites: the groups must be named with the usual left/right pattern (suffixes like ".R", ".right", ".L", etc.), and the mirror-side group must already exist (it isn't created automatically) and be completely empty (no vertices assigned to it).
Flip UDIM — mirror the texture coordinates around each tile center.

Hints: many modeling tasks involve symmetrical objects, and this modifier offers a simple, efficient way to make them, with real-time mirror updates as you edit; once modeling is done, click Apply to make a real version of the mesh, or leave it as-is for future editing.
Accurately Positioning the Mirror Plane: applying a Mirror modifier often means moving the object's origin onto the edge or face that will be the mirror axis, which is tricky to do visually. For an exact position, select the edge, then snap Cursor to Selection (placing the 3D Cursor at the edge's center), then use the Set Origin menu and choose Origin to 3D Cursor, which moves the object's origin (and thus the mirror plane) to the cursor for an exact mirror. An alternative is to use an empty as a Mirror Object that you move to the correct position.

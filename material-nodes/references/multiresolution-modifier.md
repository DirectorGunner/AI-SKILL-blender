# Multiresolution Modifier, Scatter On Surface Modifier, Skin Modifier, Solidify Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Multiresolution Modifier; Scatter on Surface Modifier; Skin Modifier; Solidify Modifier; Subdivision Surface Modifier.

## Multiresolution Modifier

The Multiresolution modifier (often shortened to "Multires") subdivides a mesh much like the Subdivision Surface modifier, but also lets you edit the new subdivision levels in Sculpt Mode.
Note: Multiresolution is the only modifier that can't be repositioned in the stack after any modifier that changes geometry or other object data (so all Generate, some Modify, and some Simulate modifiers can't come before it). Deform modifiers placed after Multires apply to the Multires subdivision levels rather than the base mesh.
Tip: this is especially handy for re-projecting details from another sculpt with a Shrinkwrap modifier — for the best result, set the wrap method to Project, snap mode to Above Surface, and enable Negative.

Options:
Levels Viewport — the subdivision level shown in the viewport.
Sculpt — the subdivision level used specifically in Sculpt Mode; while sculpting, use Alt-1 to decrease the level or Alt-2 to increase it.
Render — the subdivision level shown when rendering.
Sculpt Base Mesh — deform the unsubdivided base mesh instead of the higher levels while the set level is previewed, so you can make much broader changes in visual context to higher sculpted detail without creating surface noise and artifacts.
Optimal Display — display only the original geometry's edges, so the wireframe render skips the subdivided edges.

Subdivision:
Subdivide — create a smooth subdivision level (using the default Catmull-Clark algorithm).
Simple — create a level with unsmoothed base-mesh edges (a simple interpolation that subdivides edges without smoothing).
Linear — create a completely unsmoothed level (linear interpolation of the current sculpted displacement).
Unsubdivide — rebuild a lower subdivision level of the current base mesh.
Delete Higher — delete all subdivision levels above the current one.

Shape:
Reshape — copy another object's shape onto the multires levels by copying its vertex coordinates; to use it, select a different mesh object with matching topology and vertex indices, Shift-select the object to copy onto, and click Reshape.
Apply Base — modify the original unsubdivided mesh to match the subdivided mesh's form, applying a heuristic to the base-mesh vertices that assumes a Subdivision Surface modifier will be added.
Conform Base — modify the original unsubdivided mesh to match the subdivided mesh's form, with the base-mesh vertices ending at their subdivided positions.

Generate:
Rebuild Subdivisions — rebuild all possible subdivision levels to generate a lower-resolution base mesh, used to make an optimized multiresolution version of a preexisting sculpt; available only when no subdivision level has been created through the modifier.
Save External — save displacements to an external .btx file.

Advanced:
Quality — how precisely vertices are positioned relative to their theoretical position; can be lowered for better performance on high-poly meshes.
UV Smooth — how UVs are handled during subdivision.
- None: UVs stay unchanged.
- Keep Corners: UV islands are smoothed, but their boundary stays unchanged.
- Keep Corners, Junctions: UVs are smoothed, with corners on a discontinuous boundary and junctions of three or more regions kept sharp.
- Keep Corners, Junctions, Concave: UVs are smoothed, with those corners, junctions, and also darts and concave corners kept sharp.
- Keep Boundaries: UVs are smoothed, but boundaries stay sharp.
- All: both UVs and their boundaries are smoothed.
Boundary Smooth — how open boundaries (and corners) are smoothed.
- All: smooth boundaries, including corners.
- Keep Corners: smooth boundaries, but keep corners sharp.
Use Creases — use the Weighted Edge Creases values stored in edges to control how smooth they're made.
Use Custom Normals — interpolate the resulting mesh's existing Custom Split Normals.

Usage — Baking: baking converts high-resolution geometry detail, such as sculpted displacement or surface normals, into 2D texture maps that you then apply to a lower-resolution mesh to reproduce fine surface detail without the performance cost of dense geometry — essential where high-res sculpt data is transferred to low-res meshes for rendering or game engines. To make a normal or displacement map, use the Bake from Multires option in the Render panel, which compares two resolution levels of the Multiresolution modifier: Viewport Levels (used as the low-resolution base mesh) and Render Levels (used as the high-resolution detail mesh); the difference between them is baked into a texture map.
Bake Types — what surface information is extracted from the modifier:
- Normals: bake the surface-normal direction differences between the base and detailed levels; the normal map encodes lighting that reproduces fine sculpted detail in shading without changing the geometry — ideal for normal-mapped materials in Cycles, Eevee, and real-time engines.
- Displacement: bake the height differences between the base and high-resolution mesh as a grayscale image, with lighter areas raised and darker areas recessed; usable for true displacement in render engines or for parallax/height-based shading.
- Vector Displacement: bake 3D displacement vectors for the full spatial offset from the base to the detailed surface; unlike regular displacement it captures overhangs and non-vertical displacements for a more accurate representation, encoding XYZ displacement in the RGB color channels.
Important: for a correct bake, set the modifier's Viewport Levels to 0 so the base mesh is truly low-resolution, and set Render Levels to the highest sculpt level that contains the desired detail.

Ensure proper UV layout and an active Image Texture node in Shader Editor so the baked map can be applied.

Higher Viewport Levels partially apply sculpted displacement beforehand, corrupting bakes.

For best precision with height maps, choose OpenEXR or TIFF at 16 or 32 bits rather than standard formats.

Check that image color space is set to Non-Color (not sRGB) in Image Editor or Shader Editor.

Additional baking options and workflows are documented under Render Baking.

## Scatter on Surface Modifier

This node scatters points or instances across mesh surfaces with flexible density and randomization control, useful for procedural placement of grass, rocks, debris, or other scattered elements.

Selection determines which faces participate in scattering; unselected areas receive no scatters.

Density Method: Density bases scatters on per-unit-area density, Amount sets a total fixed count.

Distribution Method with Density: Random places points without order, Poisson Disk spaces points evenly using minimum separation.

Distribution Mask limits scattering to masked regions (1.0 enables, 0.0 excludes).

Minimum Distance Poisson Disk defines minimum spacing between points in Poisson mode; higher values create fewer, more evenly distributed points.

Keep Surface preserves the original surface geometry alongside instances.

Scatter on Instances enables scattering directly on existing instances.

Seed varies the distribution pattern.

Instance Input Type: Data-Block sources instances from an object or collection, Geometry uses input geometry directly.

When using Data-Block, Instance Type selects Object or Collection.

Viewport Visibility controls the percentage of instances shown in the viewport.

Realize Instances converts all instances to real geometry, necessary for some downstream operations.

Pick Instance (collection mode): Choose randomly or with control which member object gets instanced at each scattered location.

Reset Transform clears instance transforms before applying scattering transforms.

Instance Seed controls randomization per instance.

Surface Offset moves instances along the element normal away from the surface.

Align Rotation aligns instance orientation to the surface element orientation.

Randomize offsets (maximum translation per axis), rotations (maximum per axis), and scales (uniform or per-axis). Flipping randomly mirrors instances along selected axes. Seed initializes the random generator.

Image Mask uses a texture to control density via UV mapping.

UV Map specifies the mapping used for the image mask.

## Skin Modifier

The Skin modifier turns vertices and edges into a skinned surface, using a per-vertex radius to better shape it; the output is mostly quads, with some triangles around intersections. It's a quick way to make base meshes for sculpting and/or smooth organic shapes with arbitrary topology.
Note: faces in the original geometry are ignored.

Options:
Branch Smoothing — a branch point is a vertex with three or more connected edges, which tend to produce more complicated, sometimes overlapping topology; this setting relaxes the surface around such points, with the side effect of shrinking it.
Symmetry — these checkboxes keep the output topology symmetrical on their respective axes, avoiding merging triangles across an axis unless they form a symmetric quad.
Note: they don't add geometry flipped across an axis — for that, use the Mirror modifier, typically placed above the Skin one.
Smooth Shading — output faces with smooth shading rather than flat; the input geometry's smooth/flat shading isn't preserved.
Create Armature — create an armature over the object, with each edge becoming a bone.
Note: if the root vertex has more than one adjacent edge, an extra bone is created to serve as the root.
This does the following: adds a new armature object with bones matching the input mesh and switches the active selection to it; adds weight groups to the input mesh (which the Skin modifier propagates to the output); and adds an Armature modifier directly below the Skin one — placed after Skin because it should only deform the output, since above it might change the resulting topology.
Add Skin Data — this modifier uses a custom set of data in the mesh, generated automatically the first time you add the modifier; if you remove or otherwise lose that data, this operator regenerates it.
Mark/Clear Loose — by default a branch vertex (three or more connected edges) generates extra edge loops along adjacent edges to keep the output tight; click Mark Loose to make branches loose so the output stretches between all adjacent vertices, and Clear Loose to disable that again.
Mark Root — marking a vertex as root makes it the basis for calculating rotations of connected limbs, and it also affects the armature output as the origin for root bones; each set of connected vertices should have one root (one is selected by default if you assign none), and Mark Root enforces the one-root-per-set rule, so you needn't manually unmark roots.
Equalize Radii — make the skin radii of selected vertices equal on each axis.

Skin Mesh Data: the modifier needs a specific set of data in the original mesh to work — defining each tree's root vertices, which ones are loose, and the skin size (radius) at each vertex; input vertex radii can be scaled individually in Edit Mode with Skin Resize.

Examples: a simple creature made with only the Skin and Subdivision Surface modifiers.

External Links: an early demonstration of the Skin Modifier by Nicholas Bishop (March 2011) at Blender Nation; the research this modifier is based on — Ji, Zhongping; Liu, Ligang; Wang, Yigang (2010), "B-Mesh: A Fast Modeling System for Base Meshes of 3D Articulated Shapes," Computer Graphics Forum 29(7), pp. 2169-2178 (DOI 10.1111/j.1467-8659.2010.01805.x); and a related thread on Blender Artists.

## Solidify Modifier

This modifier adds thickness or depth to any mesh surface, converting surfaces into shells.

Mode: Simple extrudes geometry directly but fails on edges with more than two adjacent faces. Important: when adjacent face normals do not point in the same general direction, Simple mode cannot solidify the boundary; recalculate normals or avoid one-sided surfaces like Möbius strips.

Complex handles all geometric situations, including Möbius strips, Klein bottles, and architectural layouts, guaranteeing manifold output but running slower. Recommended for special cases only.

Thickness Mode (Complex): Fixed maintains constant distance to original vertices (like Simple without Even Thickness), Even adjusts for sharp corners similar to Simple with Even Thickness and High Quality Normals (may fail with 3+ faces), Constraints provides advanced thickness solving (guaranteed optimal for 3 faces, approximate beyond).

Boundary (Complex): None applies no fix (stable results), Round adjusts inward-facing boundaries (like a hole in an egg), Flat creates flat planar openings (like a cut sphere).

Thickness specifies the solid depth. Important: calculated using local vertex coordinates, so non-uniform scale causes varying thickness; Apply or Clear the scale to fix.

Offset positions solidified output from -1 to 1 relative to the original mesh (0.0 centers it).

Even Thickness (Simple) maintains thickness by adjusting for sharp corners; sometimes improves quality but increases computation.

Merge Threshold (Complex) merges degenerated geometry within this distance.

Rim – Fill creates edge loops and faces between inner and outer surfaces on face edges (slow; disable when unnecessary).

Only Rim (Simple) leaves only extruded surface and perpendicular rim, (Complex) leaves only the rim.

Vertex Group weights multiplied onto thickness; lower weights produce less thick geometry. Vertices outside the group have zero weight. Invert reverses weights.

Factor controls weight influence (0.0 = zero weight has no thickness, 0.5 = half thickness, 1.0 = weights ignored).

Flat Faces (Complex) uses minimum vertex weight to keep new faces parallel to originals; slow, disable if unused.

Flip Normals reverses all geometry normals.

High Quality Normals (Simple) calculates normals for more even thickness; sometimes improves quality but increases computation.

Material Offset selects a material slot for new geometry as an offset from the original (0 = same, 1 = next slot, -2 = two slots back). Values clamp to available slots.

Rim assigns a separate material to rim faces.

Inner/Outer/Rim (Simple) set creases on interior, exterior, and rim edges respectively.

Bevel Convex adds bevel weight to outside edges.

Clamp prevents self-intersection by clamping offsets based on shortest adjacent edge length (0 to 2).

Angle Clamp includes geometric angles in clamping calculations, not just lengths.

Shell and Rim Vertex Groups weight generated geometry for selective modifier application.

Known limitations: Even Thickness is approximate and not guaranteed to be exact, especially for vertices with 3+ faces. Maintaining precise wall thickness requires adding/removing faces (not performed by this modifier). Complex mode with constraints thickness provides the best approximation but is still not guaranteed perfect.

Rim Vertex Group weights generated rim geometry, allowing other modifiers to affect only rim geometry via their vertex group influence settings.

Known limitations on Even Thickness: the modifier's Even Thickness and High Quality Normals produce good results, but final wall thickness is approximate and may vary with mesh topology, especially at vertices with more than three adjacent faces.

Preserving exact wall thickness everywhere would require adding or removing faces during solidification, a complexity this modifier avoids. Complex mode with Constraints thickness mode offers the best solution but still cannot guarantee perfection in all cases.

## Subdivision Surface Modifier

The Subdivision Surface modifier (slang "Subdiv" or "Subsurf") splits a mesh's faces into smaller faces for a smooth appearance, letting you create complex smooth surfaces while modeling simple, low-vertex meshes — avoiding the need to save and maintain huge amounts of data and giving an "organic" look. As with any modifier, its order of execution (position in the stack) has an important bearing on the results. It's a different operation from its companion Smooth Shading (the manual's grid image shows subdivision levels 0 to 3 without and with Smooth Shading).
Tip: this modifier doesn't let you edit the new subdivided geometry without applying it, but the Multiresolution modifier does (in Sculpt Mode).
Note: this modifier uses the OpenSubdiv library as a backend.

Options:
Catmull-Clark — subdivide and smooth the surfaces for a more pleasant-looking mesh; per its Wikipedia page, the "arbitrary-looking formula was chosen by Catmull and Clark based on the aesthetic appearance of the resulting surfaces rather than on a mathematical derivation."
Simple — only subdivide the surfaces, which usually gives no smoothing unless the surface is non-coplanar (the same as the Subdivide operator in Edit Mode); to work around this for non-coplanar geometry, triangulate so all geometry is coplanar. Simple mode can, for example, raise the base-mesh resolution when using displacement maps.
Levels Viewport, Render — the number of subdivision levels shown in the 3D Viewport or the final render.
Warning: higher subdivision levels produce more vertices and thus higher memory use (both system RAM and display video memory), which can hang or crash Blender without enough memory.
Tip: the right combination keeps a fast, lightweight approximation in the viewport while rendering a higher-quality version — and be careful not to set Viewport subdivisions higher than Render, which would make the viewport quality higher than the render.
Optimal Display — when rendering the wireframe, skip the new subdivided edges (display only the original geometry's edges).

Advanced:
Use Limit Surface — place vertices on the surface that infinite subdivision levels would produce (the smoothest possible shape).
Quality — with Use Limit Surface enabled, how precisely vertices are positioned on the limit surface (relative to their theoretical position on an infinitely subdivided mesh); can be lowered for better performance. Higher values don't necessarily improve quality — ideal results may be reached well before the maximum Quality value. Note: this value can affect Edge Crease accuracy, since a higher Quality allows a wider range of crease values to work accurately.
UV Smooth — how subdivision smoothing is applied to UVs.
- None: UVs stay unchanged.
- Keep Corners: UV islands are smoothed, but their boundary stays unchanged.
- Keep Corners, Junctions: UVs are smoothed, with corners on a discontinuous boundary and junctions of three or more regions kept sharp.
- Keep Corners, Junctions, Concave: UVs are smoothed, with those corners, junctions, and also darts and concave corners kept sharp.
- Keep Boundaries: UVs are smoothed, but boundaries stay sharp.
- All: both UVs and their boundaries are smoothed.
Boundary Smooth — how open boundaries (and corners) are smoothed.
- All: smooth boundaries, including corners.
- Keep Corners: smooth boundaries, but keep corners sharp.
Use Creases — use the Weighted Edge Creases values stored in edges to control how smooth they're made.
Use Custom Normals — interpolate the resulting mesh's existing Custom Split Normals; otherwise, new faces take the overall normal orientation of the original face.

Adaptive Subdivision (Cycles Only):
Adaptive Subdivision — subdivide objects by their distance to the camera, automatically adding more or less detail; especially useful for fine displacement detail.
Adaptive Space:
- Pixel: subdivide polygons to reach a specified pixel size on screen.
- Object: subdivide to reach a specified edge length in object space; required to use adaptive subdivision for instanced meshes.
Pixel Size — the target polygon pixel size for adaptive subdivision.
Edge Length — the target object-space edge length.
Limitations: multi-view renders can show some inconsistencies between views; instancing works poorly with Pixel-space subdivision (it's based on the original object's position relative to the camera), so Object space is recommended.

Keyboard Shortcuts: to quickly add a Subdivision Surface modifier to one or more objects, select them and press Ctrl-1, which adds the modifier with Viewport subdivisions set to 1; other numbers work too (Ctrl-2, Ctrl-3, etc.) to add a modifier with that many subdivisions, and adding it this way doesn't change the Render subdivisions. If an object already has one, doing this simply changes its subdivision level instead of adding another modifier.

Control: Catmull-Clark subdivision rounds off edges, which often isn't what you want, and several solutions let you control it.
Weighted Edge Creases — these let you change how the Subdivision Surface modifier subdivides geometry to give edges a smooth or sharp appearance. Change the crease weight of selected edges in the Transform panel of the 3D Viewport's Sidebar, or with the scale-like dedicated tool Shift-E; a higher value makes the edge "stronger" and more resistant to the smoothing effect of subdivision surfaces.

### Edge Loops

Subdivision Level 2 cube, the same with an extra Edge Loop, and the same with six extra Edge Loops.

Why does tidy topology matter so much? The Subdivision Surface modifier puts the answer on display. Drop it onto a stock cube and the change is dramatic: as the figure makes plain, the shape stays almost unreadable as a cube right up until you introduce more loops (using Loop Cut and Slide, say).

When a mesh is built with intent, its edge loops sit where they should, and that careful layout is exactly what gives you the freedom to insert or strip away further loops and tune how crisp or rounded the final mesh ends up.

### Known Limitations

### Non-Contiguous Normals

Anywhere the normals shift sharply, the mesh in that area cannot be subdivided smoothly. Such regions, where the normals are non-contiguous, instead get handled through the "Simple" subdivision method.

| Comparison of good normals and bad normals. | Side view of image on the left. |

Your quickest fix here is to Recalculate Normals. Should that fail to clear it up, flipping the normals by hand may be necessary.

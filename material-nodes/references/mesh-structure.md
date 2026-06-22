# Mesh Structure, Loop Cut, Using Uv Maps

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mesh Structure; Loop Cut; Using UV Maps.

## Mesh Structure

### Mesh Structure

Every mesh comes down to three building blocks: vertices , edges , and faces .

Example of mesh structure.

### Vertices

A vertex (plural vertices) is the simplest piece of a mesh, just one point or position in 3D space. In Edit Mode the 3D Viewport draws them as small dots, and an object keeps its vertices as an array of coordinates.

Tip

Don't confuse the object origin with a vertex. It looks alike but is larger and can't be selected.

The vertex is labeled as "A"; the object's origin dot is labeled as "B".

### Edges

Every edge is a straight line joining two vertices. These are the "wires" visible in wireframe view, normally absent from the render, and they're what faces are built on.

### Faces

Faces make up the object's actual surface, the part you get when the mesh renders. Where no face covers an area, that spot simply renders as transparent or nothing at all.

A face spans three (triangles), four (quadrangles), or more (n-gons) vertices, bounded by an edge on each side. People shorten these to tris, quads & n-gons .

Triangles, being flat by nature, are cheap to compute. Quads "deform well," so they win out for animating and for subdivision work.

See also

- Why should triangles be avoided for character animation?

- When should N-gons be used, and when shouldn't they?

### Normals

A normal, in geometry, is a direction or line at right angles to something, typically a triangle or surface, though it may also be taken relative to a line, the tangent line at a point on a curve, or the tangent plane at a point on a surface.

Among other roles, normals govern how the mesh is shaded.

A visualization of the face normals of a torus.

Above, every blue line is one face's normal on the torus, each running perpendicular to the face it sits on. You can switch this view on in Edit Mode from the Mesh Display Viewport Overlays panel.

### Shading

How light meets a 3D object hinges on surface normals, so they weigh heavily on its shading. Normals can be shaded smooth or flat.

With flat shading, faces render uniformly, which usually suits flat-surfaced objects like a cube or pyramid.

With smooth shading, normals are interpolated across a polygonal mesh's vertices, smoothing the transitions between adjacent polygons for a more lifelike look.

Face normals default to flat shading, but you can change this for a whole object or face by face.

For the whole object, use:

- Shade Smooth – marks the entire object smooth.

- Shade Auto Smooth – marks only parts of it smooth.

Shade Flat brings it back to flat.

Shading can equally be set on a per-face, per-edge, or per-vertex basis.

### Custom Split Normals

Custom split normals let you tweak or fake shading by aiming normals somewhere other than their default auto-computed direction. They turn up mostly in game development, where they help offset problems from low-poly objects (classic cases being low-poly trees, bushes, grass, and "rounded" corners).

The basis Blender uses is a "smooth fan": neighboring face corners that meet at one vertex and are "linked" through smooth edges. That lets normals be defined per face corner, across a cluster of adjacent face corners, or per vertex.

This data lives as the custom_normal Attribute on the face corner Domain.

Tip

You can turn off computing custom split normals to gain performance. The toggle lives in the Simplify Rendering Settings.

#### Free Normals

Free normals are a kind of custom normal kept straight as direction vectors in object space. Where ordinary custom normals are defined against the surrounding geometry (so-called tangent or corner fan space), free normals owe nothing to mesh topology and lean on neither smooth groups nor edge connectivity.

Being plain vectors, free normals are:

- Efficient: quick to evaluate, so the viewport runs noticeably faster than with tangent-space normals.

- Lightweight: lighter on memory, a real win for dense or heavily instanced meshes.

- Static: they hold still as the mesh deforms (under modifiers or animation), making them best for static geometry or wherever speed is paramount.

Assign them through the Set Mesh Normal Node in Free mode; whichever granularity you want decides whether they land on the vertex, face, or face corner domain.

#### Editing Custom Split Normals

Reference

Mode :

Edit Mode

Menu :

Mesh ‣ Normals

Shortcut :

Alt - N

Several tools exist for editing custom split normals. By default the custom-normal edit tools touch every normal, but they can be limited to just the selected ones. To select a custom normal tied to a specific vertex and face:

- Turn on Vertex and Face element selection modes together ( Shift - LMB enables the second).

- Pick one or more vertices, then a face, repeating with further vertices and another face as needed. The tools' effect reads most clearly with the Edit Mode Overlays option Display vertex-per-face normals as lines switched on.

See also

Editing Normals.

### Importing Custom Split Normals

Certain tools, CAD ones especially, tend to spit out irregular geometry when they tessellate objects into meshes (long, sliver-thin triangles and the like). Auto-computed normals over such geometry often look wrong, so being able to import and use the normals the CAD tool itself produced matters.

Mesh Structure — Topology and Loops

Only the FBX Importer and Alembic Importer currently support importing custom normals.

Understanding Topology

Edge and face loops form continuous chains across mesh geometry. These loops are essential for mesh organization and character animation.

Continuous loops that don't terminate at poles are cyclic — they start and end at the same vertex, dividing the model into two regions. Loops provide a fast, powerful way to select and work with specific mesh areas and are fundamental for organic character rigging.

Poles are vertices where three, five, or more edges meet. At these points, a loop cannot continue uniquely, so it terminates. Vertices with exactly one, two, or four edges are not poles.

Edge Loops

Edge loops connect vertices such that each vertex on the loop has exactly two neighbors outside the loop (on either side), except at terminal vertices on poles. These loops are critical in organic and subsurface modeling, allowing you to build natural-looking models with fewer vertices that deform smoothly when used with subdivision surfaces and animation.

In character models, edge loops should follow anatomical contours and muscle lines. Areas subject to greater deformation (shoulders, knees) have denser loop placement to ensure smooth movement.

Face Loops

Face loops consist of the faces lying between two adjacent edge loops. For non-circular loops, the faces containing poles are excluded from the loop selection.

Additional topology concepts include N-poles and E-poles, as well as non-manifold topology, which are discussed in their respective sections.

## Loop Cut

Loop Cut

Mode: Edit Mode
Toolbar: Loop Cut
Shortcut: Ctrl - R

Loop Cut inserts new edge loops that cross an existing loop of faces. The tool operates interactively with two phases.

Phase 1: Pre-Visualizing the Cut

Move the cursor over an edge after activating the tool. The prospective cut appears as a magenta line across the mesh. The new edge loop terminates at poles (triangles and n-gons) where the existing face loop ends.

Phase 2: Perform the Cut

Click LMB at the desired edge loop position to create the cut.

Tool Options

Number of Cuts
Sets how many cuts to add. Cuts space uniformly across the original face loop; you cannot control individual positions.

Correct UVs
When enabled, adjusts UV coordinates to prevent image distortion.

After executing Loop Cut, additional settings appear in the Adjust Last Operation panel.

## Using UV Maps

Using UV Maps

At some point, you'll want to apply image textures to your model using the UV Editor. The 3D Viewport shows your object being textured. Setting the 3D Viewport to Textured shading mode lets you see UV Editor changes immediately (and vice versa) through viewport shading, not actual rendering.

To render an image texture, you must:

Create a Material for the object.

Configure Blender to use UV textures for rendering.

Add a material by clicking Add New Material in the Shading context.

Two paths exist for using UV texture during rendering:

Quick method: use generated UV coordinates. Generated coordinates are the default for all Texture nodes except Image textures, which use UVs by default. Use the Texture Coordinate node's Generated output for images.

Standard method: use UV unwrapping to generate UV coordinates manually. Pair the Texture Coordinate node (UV output) or the UV Map node with a selected UV map (default: "UVMap").

See Image Textures for complete details.

Material is Essential for Rendering

You can UV texture a mesh in Blender without assigning a material and see it in textured viewport mode. However, render output will show default gray if no material is assigned, or black if no image is loaded. Without a texture using the image, the object renders according to procedural material settings alone.

Using Test Grids

For uniform pattern images that should look like cloth without stretching (unless intentional), test your UV mapping:

Two images show a test grid applied to UVs and the resulting geometry preview.

When rendered, the mesh displays the test grid. Blender includes a built-in test image: press New in the Image editor header and set Generated Type to UV Grid.

Modifying Image Textures

You can save textures as separate files (allowing easy swapping and external editing) or embed them in your project file (keeping everything in one .blend file).

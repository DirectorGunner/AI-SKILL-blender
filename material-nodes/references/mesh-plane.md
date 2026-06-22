# Mesh Plane, Mesh Primitives, Object Data, Assigning A Vertex Group ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Mesh Plane; Mesh Primitives; Object Data; Assigning a Vertex Group; Select Linked; Select Similar.

## Mesh Plane

### Mesh Plane

Reference

Menu :

3D Viewport ‣ Add ‣ Image ‣ Mesh Plane

In one step, Mesh Plane builds a plane, fits its proportions to the chosen image, and gives it a material textured with that image. Filenames drive the names of the resulting plane, material, and texture.

Accepted inputs are a single image, several images at once, an image sequence, or a movie clip:

- Single Image : one plane carrying the image as its texture.

- Multiple Images : several planes, either stacked together or spread out.

- Image Sequence/Movie Clip : one plane that plays back the animated frames.

### Properties

Whatever import settings you choose can be stored as an Operator Preset.

### Options

Relative Paths
Records the image path relative to the open blend-file. See Relative Paths.

Force Reload
Re-reads the file even when its image data-block is already loaded.

Detect Image Sequences
Treats numbered image files as one animated sequence rather than as individual planes. Blender sets the frame range for you, and you can tweak it afterward.

### Material

So the imported picture shows up, Blender builds a material for the plane. These shader choices exist:

Shader
The type of node shader to use.

Principled :

Routes the image into the Base Color input of a Principled BSDF shader.

Shadeless :

Yields a material that ignores lighting, mixing Diffuse and Emission shaders under the control of a Light Path node.

Emission :

Like Principled , except the texture feeds the Emission input rather than Base Color .

Emission Strength
Adjusts the intensity of emission.

Render Method
Governs blending behavior and which features stay compatible. See Material Settings for more information.

Dithered :

Supports grayscale hashed transparency and works with render passes and raytracing. This is the deferred-rendering path.

Under the Dithered method, rendering happens in stacked layers. Any given layer can only transmit (for instance, refract) light coming from the layers before it, and where nothing below is hit, transmissive BSDFs fall back to light probes.

Blended :

Supports colored transparency but rules out render passes and raytracing. This is forward rendering.

Show Backface
Reveals the far side through transparent areas.

Backface Culling
Conceals the plane's far side.

Overwrite Material
Normally a name clash makes Blender add a number to keep the new material distinct; turning this on lets the new material replace the existing one instead.

### Texture

Note

Each option is covered in depth under Image Texture Node.

Interpolation
How the picture is scaled as it's shown on the plane.

Extension
How the picture extends past its own edges.

Alpha
Turns on transparency from the image's alpha channel.

Auto Refresh
Refreshes viewport images as the frame advances.

### Transform

New planes appear at the 3D Cursor. When you bring in several, the Offset Planes option keeps them apart.

Size Mode
Determines how the plane's size is set:

Absolute :

You give the height in Height , and the width follows to keep the aspect ratio. Example: An image of 800 × 600 pixels with a height of 1 m results in a width of 1.33 m.

Height
Sets the plane's height.

Scale to Camera Frame :

The plane's size follows the active camera.

Scale
How the plane scales against the camera frame.

Fit :

Sizes the plane to sit inside the camera frame with its aspect ratio intact.

Fill :

Sizes the plane to cover the whole camera frame, which may crop parts of it.

Pixels per Inch :

Derives the plane's size from the Definition value, expressed in pixels per inch. Example: With a 600 DPI setting, an 800 × 600 px image results in a plane size of ~0.0339 × 0.0254 m.

Definition
The pixels-per-inch count.

Pixels per Blender Unit :

Takes Definition as pixels per Blender Unit. Example: With a setting of 600, an 800 × 600 px image results in a plane size of 1.33 × 1 BU.

Definition
The pixels-per-Blender-Unit count.

Align
How the plane is rotated as it comes in.

Z- (Down), Y-, X-, Z+ (Up), Y+, X+ :

Turns the plane to line up with the chosen axis.

Face Camera :

Points straight at the camera.

Camera's Main Axis :

Snaps the plane to a major axis pointed along the camera's view.

Track Camera Face Camera Camera's Main Axis
Adds a Locked Track constraint, so the plane stays turned toward the camera.

Offset Planes
Spreads multiple planes out rather than stacking them.

Offset Direction
The axis the planes are spaced along.

Distance
The gap between planes.

## Mesh Primitives

### Mesh Primitives

Reference

Mode :

Object Mode, Edit Mode

Menu :

Add ‣ Mesh

Shortcut :

Shift - A

Meshes are the most common object type used in 3D scenes. As launch points for modeling, Blender ships a set of built-in mesh primitives. You can drop them in from either Object Mode or Edit Mode, and they show up at the 3D Cursor.

Blender's standard mesh primitives.

Tip

Flat primitives such as Plane , Circle , and Grid turn three-dimensional once you pull vertices off their starting plane.

Note

More primitives become available via add-on extensions. See Get Extensions for more information.

### Common Options

The Adjust Last Operation panel, shown right after creation, exposes these settings. The ones shared across more than one primitive are:

Generate UVs
Lays down a default UV unwrap for the new geometry, placing it in the first UV layer (adding that layer if there isn't one).

Align to View, Location, Rotation
See Common Object Options.

### Plane

A plain plane is one quad: four vertices, four edges, a single face. Flat and without thickness, it's strictly two-dimensional.

You'll see planes standing in for floors, walls, tabletops, or mirrors, and just as often serving as emitters, camera backdrops, or projection-mapping surfaces.

Size
The plane's width and height, edge to edge.

See also

Mesh Plane allows importing an image as a textured plane. The plane's dimensions are automatically scaled to match the image's aspect ratio.

Tip

A plane makes a good base for panels, ceilings, cloth sims, or sculpting surfaces. Run a modifier such as Subdivision Surface or Displace over it and the flat sheet becomes detailed geometry.

### Cube

Drops in a standard cube: six quad faces, eight vertices, twelve edges. Among the most fundamental and heavily used primitives, it's a natural starting block for boxes, crates, buildings, or sculpt bases.

Size
Total width, height, and depth, that is, the full diameter on each axis. At a size of 2 the cube reaches from -1 to +1 everywhere.

Tip

For hard-surface work the cube is the go-to base, and it pairs well with modifiers like Subdivision Surface , Boolean , or Bevel .

### Circle

Drops in a flat 2D ring of vertices that approximates a circle as a polygon. It's a handy launch point for cylindrical shapes, holes, pipe ends, or extrusion-driven modeling.

Vertices
How many vertices ring the circle; more of them, smoother the shape.

Fill Type
How the circle's interior is capped:

Triangle Fan :

Triangles meeting at a shared central vertex.

N-gon :

A single N-gon face.

Nothing :

No fill, just the rim vertices.

Radius
Center-to-rim distance.

### UV Sphere

Quad faces stacked into horizontal rings and vertical segments, capped by triangle fans at each pole, make up a UV sphere. The arrangement matches the usual way 2D textures get mapped (hence "UV"), so it textures cleanly.

Think latitude and longitude lines on a globe, which also makes it a fit for planetary models or any spherical shape needing pole-to-pole UV seams.

Segments
Count of vertical (longitudinal) divisions, the globe's meridians from pole to pole.

Rings
Count of horizontal (latitudinal) divisions, the globe's parallels stacked top to bottom.

Note

Rings map to face loops rather than edge loops, so you'll see one fewer edge loop than the ring count.

Radius
Center-to-surface distance.

Tip

For tidy shading, turn on Smooth Shading and add a Subdivision Surface modifier.

### Icosphere

Built entirely from equilateral triangles, an icosphere spreads its vertices more evenly than a UV sphere does, which suits sculpting, simulations, and anywhere uniform topology matters.

You get one by repeatedly subdividing an icosahedron, a 20-faced triangular polyhedron.

Subdivisions
Number of recursive subdivision steps. Each pass cuts every triangle into four, so resolution climbs exponentially.

- Level 1 gives you the bare icosahedron.

- Each level beyond that smooths the surface and adds vertices.

Warning

Vertex counts on an icosphere balloon fast. At 10 subdivisions, for instance, you'd top 5 million triangles and possibly crash Blender.

Radius
Center-to-surface distance.

Tip

Icospheres show up a lot in simulations, particle emitters, and sculpting, where even, triangle-only topology pays off.

### Cylinder

Builds a cylinder from two round ends and a band of vertical faces. Reach for it when modeling handles, rods, pillars, and barrels.

Vertices
How many vertices form each round end; more of them, smoother the profile.

Radius
End radius, center to rim.

Depth
The cylinder's height along Z.

Cap Fill Type
How the two ends are capped:

Nothing :

No caps, just the sides, so a tube. Good for pipes or hollow containers.

N-gon :

A single N-gon face per end.

Triangle Fan :

Triangles meeting at a shared central vertex, per end.

### Cone

Builds a cone or pyramid shape. It's the basis for spikes, traffic cones, or wizard hats, and dialing in a top radius gives you frustums (truncated cones) or plain pyramids.

Vertices
How many vertices form the round base (or the polygon base of a pyramid); more of them, smoother the curve.

Radius 1
Radius of the bottom circle, the cone's base.

Radius 2
Radius of the top circle. At 0 you get an ordinary pointed cone; above 0 it becomes a frustum.

Depth
The cone's height along Z.

Cap Fill Type
How the base is capped:

Nothing :

No bottom cap, just the sides. Good for open containers or hollow cones.

N-gon :

A single N-gon face.

Triangle Fan :

Triangles meeting at a shared central vertex.

Tip

For a pyramid, set Vertices to 4 and pick N-gon or Triangle Fan as the cap type. Keep Radius 2 at 0 so the top stays pointed.

### Torus

A doughnut shape made by sweeping a circle around an axis. Handy for rings, pipes, and decorative trim.

Operator Presets
Reusable saved torus settings, kept as Python scripts under the presets directory.

Major Segments
How many segments make up the torus's main ring, the step count as the cross-section spins about the central axis.

Minor Segments
How many segments form the circular cross-section, each one rotated around the main ring.

Dimensions Mode
Picks how the torus's shape and size get specified:

Major/Minor :

Set it from the main ring's radius plus the cross-section's radius.

Exterior/Interior :

Set it from the overall outer radius plus the central hole's radius.

Major Radius Major/Minor
From the torus center out to the center of the cross section.

Minor Radius Major/Minor
The cross-section's radius, that is, the ring's thickness.

Exterior Radius Exterior/Interior
From the torus center out to its outer edge.

Interior Radius Exterior/Interior
The radius of the central hole.

### Grid

An even grid of quad faces, good as groundwork for landscapes, cloth, or organic surfaces. Bump up the subdivisions for a denser mesh better suited to sculpting or simulation.

X Subdivisions
Face spans across X.

Y Subdivisions
Face spans across Y.

Size
The grid's width and height, edge to edge.

### Monkey

Drops in a stylized monkey head called "Suzanne." A gift from old NaN to the community, she lingers in Blender as a playful Easter egg and is widely known as its mascot.

People reach for her to test materials, lighting rigs, and modifiers like Subdivision Surface.

In spirit she's Blender's answer to standard test models such as the Utah Teapot or the Stanford Bunny.

Size
The mesh's overall scale.

## Object Data

### Object Data

Select a mesh object and these panels appear in the Data tab of the Properties Editor.

Mesh data-block
Use the Data-Block Menu up top to repoint the object at different mesh object data.

### Vertex Groups

A vertex group tags a set of vertices, optionally weighted, for some operator to act on. One object can hold several, assignable in Weight Paint mode or in Edit Mode through this panel.

See Vertex Groups for more information.

### Shape Keys

Use Shape Keys to morph one shape into another. See Shape Keys Panel for more information.

### UV Maps

A UV Map projects a 3D object onto a 2D plane, fixing where a texture lands on it. You can keep separate UV Maps for separate textures. For more information see UV Maps.

### Color Attributes

Rather than going through a texture or material, you can paint color straight onto an object's vertices. Two paint modes exist. Vertex Paint mode paints per face corner once you turn on the header's paint mask, which helps keep crisp edges in the color attribute on low-poly assets. Sculpt mode, by contrast, lets you paint across a far denser vertex count.

### Creating a New Color Attribute

Click the plus icon beside the attribute list to make one. A pop-up opens asking for:

Name
What the Color Attribute is called, usable as a reference elsewhere in Blender.

Domain
Which slice of geometry holds the attribute. See Attribute Domains for more information.

Vertex :

One color value per vertex.

Face Corner :

One color value per face corner.

Data Type
How colors are represented internally.

Color :

Floating-point RGBA.

Byte Color :

8-bit RGBA.

Color
The starting fill color for every element in the domain.

### Color Attribute Specials

The menu to the right of the list holds these operators.

Duplicate Color Attribute
Copies the active color attribute into a new list entry.

Convert Color Attribute
Switches the storage format of the color attribute.

Domain
Which slice of geometry holds the attribute. See Attribute Domains for more information.

Vertex :

One color value per vertex.

Face Corner :

One color value per face corner.

Data Type
How colors are represented internally.

Color :

Floating-point RGBA.

Byte Color :

8-bit RGBA.

### Attributes

An attribute is per-element mesh data, each one carrying a data type, domain, and name. This panel shows only custom attributes, leaving out built-ins like position and the likes of vertex groups.

See Attributes Reference for more information.

### Texture Space

Every object can carry an auto-generated UV map, tunable from here.

See Generated UV Properties for more information.

### Remesh

Meshes built to portray organic forms often end up with uneven geometry, which trips up rigging or any workflow wanting simpler topology, 3D printing among them. Remeshing regenerates that geometry with more uniform topology, adding or cutting detail to hit your chosen resolution. It's a particular help in sculpting, giving you cleaner topology once the rough shape is blocked in.

See Remeshing for more information.

### Geometry Data

A mesh object can hold various kinds of custom data. It's mostly for internal use, though some exporters can write it out. See Geometry Data for more information.

## Assigning a Vertex Group

### Assigning a Vertex Group

### Creating Vertex Groups

Empty Vertex Groups panel.

The Object Data tab (1) in the Properties is where vertex groups live. New mesh objects start with none, so the panel sits empty (2).

To make one, LMB the button at the right edge of the panel (3). It comes in named "Group" (or "Group.nnn" if that name is taken) and shows up in the panel (2) (see next image).

### Vertex Groups Panel Controls

One vertex group.

A freshly added group appears in the Vertex Groups panel, where three clickable parts await:

Group Name
Double-click LMB on the name to rename the group, then type whatever you want.

Filter (arrow icon)
Clicking the small arrow at the lower left opens a row for a search term, which earns its keep once you've amassed a lot of vertex groups.

Drag Handle
With many groups and a wish to see more at once, LMB the little drag handle to grow or shrink the list.

Active Group
Creating a group also makes it the Active Group , flagged by a light-gray background on its panel entry. With two or more in the list, LMB another entry to switch which is active.

### Deleting Vertex Groups

Delete a vertex group.

Make the group active (pick it in the panel), then LMB the button at the panel's right edge to delete it.

Removing a group only drops the vertex assignments; the vertices stay put.

### Locking Vertex Groups

Lock a vertex group.

A new group shows an open padlock at the right of its entry, signaling that it's editable. You're free to add or pull assignments and paint it with the weight brushes, and so on.

Click the icon and it closes, freezing every change to the group. From there you can only rename, delete, or unlock it. Nothing else is permitted, so the matching buttons gray out for locked groups.

### Working with Content of Vertex Groups

### Assigning Vertices to a Group

Assign weights to active group.

To add vertices to a group:

- In the group list, click the group so it becomes active (1).

- Back in the 3D Viewport, Shift - LMB each vertex you mean to add.

- Dial in the weight that every chosen vertex should take (2).

- LMB Assign to bind the selection into the active group at that weight (3).

Locked groups don't allow this; the Assign button grays out when one is locked.

Note

Assign is additive

Pressing Assign only adds the current selection to the active group. Vertices already in the group stay, and a single vertex can belong to several groups at once.

### Checking Assignments

To confirm your selected vertices really sit in the group you mean, try the deselect button. Any vertices that stay selected aren't in the group yet.

You can assign them now, but be careful: every selected vertex takes on whatever weight is in the Weight field.

### Removing Assignments from a Group

To take vertices out of a group:

- Click the group in the list to make it active.

- Select the vertices you want gone from it.

- LMB the Remove button.

Locked groups block this too; with one locked, Remove sits grayed out.

### Using Groups for Selecting/Deselecting

To quickly grab every vertex assigned to a group:

- Optionally, hit Alt - A first to clear the selection.

- Click the group in the list to make it active.

- LMB Select and the group's vertices light up in the 3D Viewport.

- LMB Deselect instead and those vertices drop out of the selection.

Note

Selecting/Deselecting is additive

If vertices are already selected, adding a group's vertices keeps the old ones too. Likewise, deselecting a group's vertices only drops that group's vertices and leaves everything else selected.

### Finding Ungrouped Vertices

To track down ungrouped vertices:

- Hit Alt - A to clear the selection.

- From the 3D Viewport header, go to Select ‣ Select All by Trait ‣ Ungrouped Vertices .

## Select Linked

### Select Linked

### Linked

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked ‣ Linked

Shortcut :

Ctrl - L

Grabs all geometry tied directly or indirectly to the current selection. It's a lifesaver when a mesh has separate but overlapping parts that would be tedious to isolate any other way.

Rather than selecting an element and hitting Ctrl - L , you can also just hover over an element and press L . Or press Shift - L to deselect.

The Adjust Last Operation panel has the following option:

Delimit
Halt the spread once it hits set boundaries. Several can be on at once, toggled with Shift - LMB .

Normal :

Halt at oppositely oriented faces.

Material :

Halt where the material changes.

Seam :

Halt at edges flagged as UV Seams.

Sharp :

Halt at edges flagged as Sharp.

UVs :

Halt at UV island borders in any map.

### Shortest Path

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked ‣ Shortest Path

Shortcut :

Ctrl - LMB

Selects the geometry running along the shortest path between your two most recently selected mesh elements.

For the shortcut, select the start element the usual way, then pick the end element with Ctrl - LMB .

Shortest paths for vertices (left) and faces (right).

### Options

Edge Tag Edge Mode
What happens to the selected edges:

Select :

Just select them.

Tag Seam :

Flag them as UV Seams.

Tag Sharp :

Flag them as Sharp.

Tag Crease :

Set their Crease to 1.0.

Tag Bevel :

Set their Bevel Weight to 1.0.

Tag Freestyle Edge Mark :

Flag them as Freestyle edges.

Face Stepping
Permits diagonal paths for vertices and faces, and edge rings for edges.

Topology Distance
Favors the route over the fewest edges instead of the shortest spatial distance.

Fill Region Shift - Ctrl - LMB
Grabs every shortest path at once rather than a single one.

Deselected, Selected, Offset
Lets the path come out "dashed" instead of solid, a recurring run of a few skipped elements then a few selected ones. See also Checker Deselect.

### Linked Flat Faces

Reference

Mode :

Edit Mode

Menu :

Select ‣ Select Linked ‣ Linked Flat Faces

Spreads the selection across connected faces until it hits a sharp corner.

Sharpness
The widest angle two faces may span and still pass as one flat surface. Read off the face normals, so coplanar faces sit at 0° (not 180°), and the sharper the corner the larger the angle (not the smaller).

| Initial selection.  | After running Select Linked Flat Faces.  | Comparison to Select Similar ‣ Normal .  |

To halt the selection at edges you manually marked Sharp, use Linked instead.

## Select Similar

### Select Similar

Reference

Mode :

Edit Mode

Menu :

Select ‣ Similar

Shortcut :

Shift - G

Selects every mesh element that resembles an already-selected one in some way. Which properties you can compare depends on the current selection mode:

Vertex Selection Mode:

Normal
By normal-vector direction.

Amount of Adjacent Faces
By count of neighboring faces.

Vertex Groups
By shared membership in any of the same vertex groups; weights don't matter.

Amount of Connecting Edges
By count of neighboring edges.

Vertex Crease
By Crease value.

Edge Selection Mode:

Length
By edge length.

Direction
By the edge's direction vector.

Amount of Faces Around an Edge
By count of neighboring faces.

Face Angles
By the angle between the two adjoining faces.

Crease
By Crease value.

Bevel
By Bevel Weight.

Seam
By UV Seam mark.

Sharpness
By Sharp mark.

Freestyle Edge Marks
By Freestyle mark.

Face Selection Mode:

Material
By face material.

Area
By area.

Polygon Sides
By edge count.

Perimeter
By summed edge length.

Normal
By normal-vector direction.

Coplanar
Like Normal , except it only extends the current selection along its borders rather than grabbing faces anywhere on the mesh, the same effect as Select Linked Flat Faces.

Flat/Smooth
By face shading mode.

Freestyle Face Marks
By Freestyle mark.

Pick a property from the menu and more controls turn up in the Adjust Last Operation panel:

Compare
How numeric properties are matched:

Equal :

Items whose value matches.

Greater :

Items whose value is equal or larger.

Less :

Items whose value is equal or smaller.

Threshold
Slack for numeric values that nearly hit the target.

### Face Regions

Reference

Mode :

Edit Mode

Menu :

Select ‣ Similar ‣ Face Regions

For every region of connected faces in the selection, it finds and selects other regions sharing the same topology.

| Initial selection.  | After running Select Similar Face Regions.  |

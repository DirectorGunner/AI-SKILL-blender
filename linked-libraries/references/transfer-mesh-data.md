# Transfer Mesh Data, Transfer Mesh Data Layout, Collection, Instancing ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Transfer Mesh Data; Transfer Mesh Data Layout; Collection; Instancing; Scene Strip; Storyboarding App Template.

## Transfer Mesh Data

### Transfer Mesh Data

Reference

Mode :

Object Mode

Menu :

Object ‣ Link/Transfer Data ‣ Transfer Mesh Data

This operation duplicates a particular data category from the active mesh to the selected meshes. This could be UV maps, color attributes, custom normals, and more.

For each component (vertex/edge/face) in each destination mesh, the operator identifies one or more matching components in the source mesh, then interpolates between those source component values.

See also

Data Transfer Modifier

The Adjust Last Operation panel offers the following options.

Freeze Operator
Blocks settings changes from re-running data transfer. Helpful when adjusting multiple settings simultaneously with complex geometry.

Data Type
Which data to transfer.

Data types.

Create Data
Introduces any missing data layers to the destination meshes (e.g. create missing vertex groups).

Mapping
The method for finding matching source component(s) for each destination component. Various options are described in the Mapping section.

Auto Transform
When source and destination meshes do not align in world space, enable this option to determine a transformation algorithmically. Though quick and convenient, manual overlap may yield superior results.

Object Transform
Whether to factor in the world space transformations of source and destination objects. Unchecked means all objects are treated as if in the same position with default rotation and scale.

Only Neighbor Geometry
Evaluate only source elements near the destination component.

Max Distance
The highest acceptable distance between source and destination component (for non-topology mappings).

Ray Radius
The initial radius for ray casting operations.

For specified mapping types, the operator executes a series of ray casts from each destination component to locate matching source components. These casts start at the specified radius and progressively increase until a match is found or a limit is reached.

A low starting radius yields higher precision but diminishes performance if overly compact. A high starting radius improves efficiency but may yield suboptimal matches.

Generally, use a low radius for high-density source meshes and a high one for simpler ones.

Islands Precision
Governs the computation preventing destination faces from obtaining UV coordinates from disparate source UV islands (seam-bordered regions). A value of 0.0 skips island handling, while higher values enhance accuracy at the cost of additional computation.

Typically, modest values like 0.02 achieve good outcomes, but when mapping from extremely high-poly sources to extremely low-poly destinations, you may need substantially higher values.

Source Layers Selection
Specifies which source layers to transfer to destination meshes (e.g. only the active vertex group, all vertex groups, or a named vertex group).

Destination Layers Matching
The method for identifying destination layers for provided source layers: by identity or by sequential order.

Mix Mode
How to combine transferred source data with existing destination mesh data.

Replace
Blend between original and new values using Mix Factor.

Above Threshold
Substitute the destination value if it surpasses or equals Mix Factor. For multi-component data such as colors, threshold evaluation compares against component averages.

For boolean Data Types like Freestyle Mark, this achieves a logical AND: ensure Mix Factor is 0.5 or higher, and marked edges/faces in both source and destination are retained.

Below Threshold
Substitute the destination value if it falls below or equals Mix Factor. For multi-component data such as colors, threshold evaluation compares against component averages.

For boolean Data Types like Freestyle Mark, this achieves a logical OR: ensure Mix Factor is 0.5 or higher, and marked edges/faces from either source or destination are retained.

Mix
Combine transferred source value with destination value, like alpha blending for color attributes. Then, blend using Mix Factor.

Add
Add transferred source value to destination value, then blend using Mix Factor.

Subtract
Remove transferred source value from destination value, then blend using Mix Factor.

Multiply
Amplify destination value by transferred source value, then blend using Mix Factor.

Mix Factor
Interpolation balance between original destination value and newly computed value. When Mix Mode is Above Threshold or Below Threshold, this becomes a threshold value instead.

### Mapping

### Topology

Matches components by numerical ordering. All meshes must have matching element counts and identical ordering. Best for destination meshes that are deformed copies of sources.

See also

Sort Elements to guarantee matching element ordering.

### One-To-One Mappings

These mappings select only one source component for each destination one.

Vertex Data

Nearest Vertex
Applies the nearest source vertex.

Nearest Edge Vertex
Applies the nearest source vertex on the nearest (by center point distance) source edge.

Nearest Face Vertex
Applies the nearest source vertex on the nearest (by center point distance) source face.

Edge Data

Nearest Vertices
Applies the source edge whose vertices are nearest to the destination edge's.

Nearest Edge
Applies the source edge whose center is nearest to the destination edge's center.

Nearest Face Edge
Applies the nearest source edge on the nearest face (both by center distance).

Face Corner Data
A face corner represents a vertex within a face context. This idea is frequently used in UV maps: each face corner can have distinct UV coordinates, or equivalently, one 3D vertex can map to numerous UV vertices (one per face).

Selection Options for Corner Data
Nearest Corner and Best Matching Normal — identifies the source corner nearest to the destination, prioritizing those whose split normals align most closely.
Nearest Corner and Best Matching Face Normal — selects the source corner nearest to the target corner, preferring one whose face normal closely resembles the target's face normal.
Nearest Corner of Nearest Face — takes the closest source corner residing on the nearest source face.

Face Data

Nearest Face — targets the nearest source face, measured from its midpoint.

Best Normal-Matching — projects a ray from the center of the destination face along its normal direction to find intersecting source faces.

### Interpolated Mappings 

These methods can combine multiple source elements and blend their values.

Vertex Data

Nearest Edge Interpolated — locates the closest point on the nearest source edge and blends the vertices of that edge.

Nearest Face Interpolated — finds the closest position on the nearest source face and interpolates across its vertex values.

Projected Face Interpolated — casts a ray from the destination vertex along its normal to strike a source face, then interpolates the face's vertex values.

Edge Data

Projected Edge Interpolated — projects multiple points along the destination edge (each using the interpolated normal of adjacent vertices) onto source edges, then blends their values.

Face Corner Data

Nearest Face Interpolated — locates the nearest point on the closest source face and blends the corner values of that face.

Projected Face Interpolated — projects the destination corner along its normal onto a source face and interpolates corner values at the projected location.

Face Data

Projected Face Interpolated — casts rays from multiple points on the destination face along its normal to locate source faces, then blends their values.

## Transfer Mesh Data Layout

### Transfer Mesh Data Layout 

Reference

Mode:
Object Mode

Menu:
Object ‣ Link/Transfer Data ‣ Transfer Mesh Data Layout

Transfers the layer configuration from the active mesh to every target in the selection.

Data Type
Indicates what data classes to replicate.

Data Layer Categories 

Exact Match
Additionally removes extraneous layers from target objects to mirror the source structure exactly.

Source Layers Selection
Specifies which layers to copy when dealing with multi-layer categories.

Active Layer
Copy only the currently active data layer.

All Layers
Copy every available data layer.

Destination Layers Matching
Determines how source layers are paired with target layers.

By Name
Pairs layers sharing identical names.

By Order
Pairs layers according to their position in the list (numeric indices).

See also

Data Transfer Modifier

## Collection

### Collection 

Reference

Mode:
Object Mode

Panel:
Properties ‣ Object Properties ‣ Instancing ‣ Collection

Collection Instances let you duplicate an entire collection for each manifestation of another item.
Collections may contain motion sequences, objects with dynamic effects, and nested collections.

### Basic Usage 

Establish a Collection:

- Build a fresh collection (via the Outliner).

- Tie the items needing duplication into the new collection.

Make a Collection Manifestation:

- Add ‣ Collection Instance

An instance of the collection and an empty shape emerge.
You can multiply the empty, and the Instance Collection options remain across copies.
This way, you obtain numerous copies of distributed information very easily.

### Collections and Dynamic Linking 

See Appending and Linking
for guidance on how to bring content from a different file into this one.
You can drag collections from one file to another.
When you do, the dragged collection doesn't show in the viewport
until you build an item setting where the collection manifestation appears.

### Making an Instanced Collection Real 

For further work on an instanced collection, choose the Instance Collection.
Next use Make Instances Real to change
the collection into standalone items that can be shifted and animated.

Note

Note that when the instanced collection was imported, the Object Data
(geometry, material assignments, textures, orientations) remains imported from the origin collection.
But the various object's connections don't transfer over.

## Instancing

### Instancing 

Note

Procedural Nodes supplies a more advanced approach to duplicating shapes, using the
Instance using Spots Node.

Corners
This makes a copy of every descendant of this item at each corner
(for geometric shapes exclusively).

Surfaces
This makes a copy of every descendant of this item at each surface
(for geometric shapes exclusively).

Collection
This makes a copy of the collection with the orientation of the item.
Collection instancers may be animated via clips,
or may take a Library Variant.

## Scene Strip

### Scene Strip

Scene strips allow you to embed the render output from another scene into your edit. Rather than rendering to a file then importing it, you can reference the scene directly.

The strip duration matches the animation settings of the referenced scene.

Note

Scene strips cannot reference the Sequencer's own scene; a different scene is required.

### Adding Scene Strips

Scenes are added via Add ‣ Scene ‣ "Scene Name". Scene assets from the current project or an Asset Library also appear in Add ‣ Scene. Scene assets assigned to a Catalog show that hierarchy as submenus. When adding a scene asset as a strip, it is always duplicated.

New scenes are created directly through Add ‣ Scene ‣ Empty Scene.

Options

Start Frame
The frame where the scene strip begins playback.

Channel
The row location for the strip.

Replace Selection
Swap the current active strip with the new scene strip.

When creating a new scene, these options are available:

Type
Scene creation approach.

New:
Generates a new strip with a fresh, empty scene using default parameters.

Copy Settings:
Generates a new strip with an empty scene and transfers settings from the current scene.

Linked Copy:
Generates a strip and links in the current scene's collections (shallow copy).

Full Copy:
Generates a strip and duplicates the entire scene.

### Options

Scene
Data-block picker for selecting or generating the scene to render from.

Input
Source specification for the scene strip.

Camera:
Renders using the scene's 3D camera.

Sequencer:
Uses the scene's Sequencer timeline, enabling a scene to incorporate another scene's edit (similar to Meta Strips but with multi-instance support).

Camera
Override the default scene camera with any other object. Helps switch perspectives within the same scene setup.

Show

Annotations
Shows Annotations in non-render display modes (Solid, Wireframe).

Transparent
Generates transparency in the background, useful for overlay effects like exporting Grease Pencil compositions.

### Sound

Strip Volume
Controls the loudness of audio from the scene.

### Limitations

Scene strips do not produce individual Render Passes; only the Combined pass is output.

## Storyboarding App Template

### Storyboarding App Template

The Storyboarding app template furnishes a preconfigured environment for planning storyboards in Blender, merging 2D illustration and scene handling into a cohesive workspace.

Built on the 2D Animation template, it incorporates a Video Sequence Editor (VSE) configured with the Sync Scene feature for shot arrangement.

The default Storyboarding App template.

### Overview

This template facilitates shot planning and visual sketching for animation or film. Each shot is its own scene, hosting independent Grease Pencil drawings, camera positioning, and timing, while the Sequencer acts as a master timeline coordinating shots.

### Features

- Based on the 2D Animation Template:
Supplies the 2D workspace with a Grease Pencil object for drawing.

- Sequencer with Sync Scene Enabled:
The Sequencer is set to Sync Scene, automatically switching and displaying the matching scene when a strip is selected. Navigating between shots becomes seamless.

- Preconfigured Scenes:

- Edit Scene: The master scene used in the Sequencer for shot assembly.

- Shot.000 (Asset): A template Scene Asset for duplicating fresh shots quickly.

- Shot.001 and Shot.002: Example shot scenes made from Shot.000.

### Default Settings

- The Edit scene is 10 seconds long by default, presenting a concise storyboard overview.

- Each shot runs 2 seconds by default, a shorter duration aiding pacing visualization in the Sequencer.

- Frame ranges are compact (versus typical 250-frame defaults) for practical storyboard navigation.

### Usage

- Access Storyboarding via File → New → Storyboarding.

- Arrange shots in the Edit scene Sequencer.

- Duplicate Shot.000 in the Sequencer to generate new shots.

- Sketch within each shot's 2D workspace using Grease Pencil.

- Modify timing and sequence in the Sequencer to adjust flow.

This setup enables rapid visual storytelling planning with tight linkage between drawings and the master storyboard sequence.

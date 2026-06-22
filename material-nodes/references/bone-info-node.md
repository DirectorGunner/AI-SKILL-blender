# Bone Info Node, Camera Info Node, Collection Info Node, Is Viewport Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Bone Info Node; Camera Info Node; Collection Info Node; Is Viewport Node; Mouse Position Node; Object Info Node; Self Object Node; Viewport Transform Node; Inspection; Instances; Instance Bounds Node; Instance on Elements Node; Instance on Points Node; Instance Rotation Node; Instance Scale Node; Instance Transform Node; Instances to Points Node; Randomize Transforms Node.

## Bone Info Node

### Bone Info Node

The Bone Info node retrieves bone transform data from an armature object. Useful for rig-driven geometry control or implementing skeletal deformation via vertex-group attributes.

Note: A dependency cycle can occur if the node references one bone while another bone in the same armature depends on the modified object (e.g., via a Geometry Attribute Constraint). The modifier can only add a dependency on the entire armature, not individual bones, because the bone name is a generic string.

### Inputs

Armature
Source armature object for bone pose data.

Bone Name
Name of the bone whose pose transforms to retrieve.

### Properties

Transform Space
Coordinate system for pose output.

Original:
Output pose and rest pose relative to armature origin.

Relative:
Project pose and rest pose into the modified object's space.

### Outputs

Pose
The bone's evaluated final transform.

Local Pose
Pose minus rest pose, relative to the parent bone. Not affected by transform space.

Transform Pose
Matrix encoding the bone's location, rotation, and scale. Not affected by transform space.

Rest Pose
The bone's original transform (edit-mode definition).

Rest Length
The bone's original length.

## Camera Info Node

### Camera Info Node

The Camera Info node outputs camera object parameters.

Useful for customizing geometry based on camera settings—building camera-dependent visual effects, aligning geometry to camera view, or similar tasks.

### Inputs

Camera
The camera to query.

To retrieve the active camera, use Active Camera Node.

### Outputs

Projection Matrix
A 4×4 matrix combining focal length, sensor size, shift, and clipping range. Projects 3D coordinates to screen space.

Focal Length
Camera focal length in millimeters. Affects perspective field-of-view.

Sensor
Physical sensor dimensions in millimeters as a 2D vector (X, Y), influenced by sensor-fit settings.

Shift
Horizontal and vertical view shift as a 2D vector.

Clip Start
Near clipping distance.

Clip End
Far clipping distance.

Focus Distance
Distance from camera to focus plane, in Blender units. Typically for depth-of-field.

Is Orthographic
Boolean: true for orthographic, false for perspective.

Orthographic Scale
Orthographic-mode zoom factor. Controls view size instead of focal length.

## Collection Info Node

### Collection Info Node

The Collection Info node retrieves collection properties. Useful for parameterizing geometry-node trees via external collections.

Tip: Drag a collection into the node editor to quickly add this node.

### Inputs

Collection
The collection to query.

Separate Children
Output each child as a distinct instance, sorted alphabetically by object and collection. Use with the Pick Instance option in Instance on Points Node to vary instances per point.

Note: Renaming objects and collections does not trigger a modifier re-evaluation; manual updates are needed.

Reset Children
Remove each child's initial transform when converting to instances. Keeps children visually distinct in the viewport while centering them at the instancing point.

### Properties

Transform Space
The coordinate system for output instances (the instances are transformed, but not the geometry of the collection in them).

Original:
Instances relative to collection offset.

Relative:
Merge input collection instances with modified geometry, preserving scene-space relationships.

### Outputs

Instances
World-space collection instances with all modifiers applied, represented as geometry.

## Is Viewport Node

### Is Viewport Node

The Is Viewport node outputs true during viewport evaluation, false during final render.

### Inputs

None.

### Outputs

Is Viewport
Boolean indicating viewport-vs.-render context.

### Example

Using Is Viewport to switch between low and high quality settings.

## Mouse Position Node

### Mouse Position Node

The Mouse Position node returns cursor location and region dimensions.

Tip: Enable "Wait for Click" when using this node to wait for mouse input (LMB) before executing the operator from a menu.

Note: Tool context only.

### Inputs

None.

### Outputs

Mouse X
Region-space X coordinate in pixels (0 at left edge).

Mouse Y
Region-space Y coordinate in pixels (0 at bottom edge).

Region Width
Region width in pixels.

Region Height
Region height in pixels.

## Object Info Node

### Object Info Node

The Object Info node retrieves object properties. Useful for linking geometry-node behavior to external objects—either directly via geometry or indirectly via transformation data.

Drag an object into the node editor to add this node quickly.

### Inputs

Object
The object to query.

As Instance
Output the object as a single instance rather than realized geometry. Allows instancing non-geometry types.

### Properties

Transform Space
Coordinate system for vector and geometry outputs.

Original:
Geometry relative to the input object; location, rotation, scale relative to world origin.

Relative:
Project input geometry, location, rotation, scale into the modified object, preserving scene relationships.

### Outputs

Transform
Matrix encoding object location, rotation, and scale.

Location
Object location in world space.

Rotation
Object rotation in world space.

Scale
Object scale in world space.

Geometry
Object geometry in world space with all modifiers applied.

### Object Info Node

Access object instance data to vary a single material across multiple instances—via object index, location, or randomization. For example, pair with a Noise texture for random colors or a Color Ramp for color selection.

### Inputs

None.

### Properties

None.

### Outputs

- **Location** — Object position in world space.
- **Color** — Object color (same as Viewport Display ‣ Properties ‣ Object Properties ‣ Color).
- **Alpha** — Alpha Channel component of viewport display color (see Color output).
- **Object Index** — Pass Index (same as Properties ‣ Object Properties ‣ Relations ‣ Pass Index).
- **Material Index** — Pass Index (same as Properties ‣ Material ‣ Settings ‣ Pass Index).
- **Random** — Float between 0.0–1.0 unique to each object instance.

Note: This node works only for material shading nodes, not light or world shaders.

### Example

Example blend-file.

## Self Object Node

### Self Object Node

The Self Object node outputs the object being modified by the active geometry-nodes modifier. Useful for retrieving original transform data.

In Tool context, returns the active object.

Note: Geometry cannot be retrieved from this object using Object Info Node, because its final form is still being computed.

### Inputs

None.

### Outputs

Self Object
The object under evaluation.

## Viewport Transform Node

### Viewport Transform Node

The Viewport Transform node outputs the 3D Viewport's view and projection state.

Note: Tool context only.

### Inputs

None.

### Outputs

Projection
The viewport's perspective or orthographic projection matrix.

View
View direction and location of the 3D viewport.

Is Orthographic
Boolean: viewport is orthographic.

## Inspection

### Inspection

Intermediate socket values and tree behavior are useful to understand during node-tree building or debugging. Blender offers multiple tools for this.

Note: Inspection tools generally show data from the most recent tree evaluation. If not yet evaluated, no information is available.

### Socket Inspection

Displays socket values from the last evaluation. For primitive types (integers, vectors, strings) the exact value is shown; for geometry, metadata such as data types and element counts are stored.

Socket values log only when the tree executes (so nodes must connect to Group Output), not during rendering (for performance).

### Attribute Search

Triggered by clicking an attribute input in the modifier. Lists all attributes available at that point in the execution.

### Viewer Node

Displays intermediate geometry in the Spreadsheet Editor and viewport. See Viewer Node for details.

### Node Warnings

Invalid node inputs trigger a warning icon in the title bar. Hover to see the error. Warnings only appear after node execution (nodes must connect to Group Output).

### Node Timings Overlay

Execution time for each node during the last evaluation. Enable from the overlay popover (top-right, node editor). When a node group runs in multiple contexts, timing reflects the current editor context (shown in the top-left path).

Frame nodes show combined time for all contained nodes; Group Output shows total tree time.

Timings are approximate (copying/deleting geometry inputs may be included). When nodes use multiple cores, the evaluation system may work on other nodes simultaneously. Field nodes typically contribute no direct time—their cost rolls into the data-flow nodes they feed.

### Named Attributes Overlay

Shows which custom named attributes are in use by nodes or groups. Named attributes (Capture Attribute Node, Named Attribute Node, Remove Named Attribute Node) can be written, read, or removed.

Named attributes (unlike anonymous ones) risk overwriting input-geometry attributes with the same name, potentially corrupting essential data. The overlay simplifies detection.

The same information appears in the Named Attributes panel within the modifier UI.

### Geometry Randomization

Many nodes do not guarantee output-element order. For example, Triangulate produces deterministic but undocumented ordering, which may shift across Blender versions. Setups depending on specific indices may break on updates.

"Geometry randomization" temporarily shuffles result elements to expose index-order dependencies. Enable it to verify long-term stability of complex setups.

To enable: turn on Developer Extras in preferences, then search for "Set Geometry Randomization." The popup toggles it on/off.

## Instances

### Instances

In addition to real data (meshes, curves), objects can hold instances—references to other geometry, objects, or collections. Instancing avoids duplicating data, letting render engines like Cycles handle repeated geometry efficiently.

Each instance tracks its source geometry and transformation relative to the source. Instances also store the id attribute for correcting motion blur during animation.

Use the Instance on Points Node to create instances.

Warning: Geometry-node instancing cannot combine with the Instancing panel in the property editor.

### Nested Instancing

Since instances hold geometry and geometry holds instances, nesting is possible—instancing instances, or collections of instances. The Instance on Points Node creates nested instances by default.

A node group creating nested instancing via chained Instance on Points nodes.

Here, nested instancing distributes geometry containing both mesh and instance data. Output holds a "real" mesh plus an instance group. Each instance contains a sphere mesh and many cone instances.

Instance hierarchy for the above example.

This approach helps because the output contains only three unique meshes (plane, sphere, cone), dramatically improving performance vs. unique copies.

Warning: Only eight levels of nested instancing render and display in the viewport. Deeper trees can exist in geometry nodes but must be realized at the tree's end.

### Realizing Instances

"Realizing" converts instances into unique geometry. Realized instances consume more memory and require per-instance manipulation rather than per-source-geometry processing.

Use the Realize Instances Node.

### Instance Processing

Nearly all geometry-processing nodes work on each unique geometry once, not on each realized copy. For example, placing a Subdivision Surface Node after the nested-instancing example above processes three meshes, not each instance separately. Similarly, processing String to Curves output handles each unique character once.

This boosts performance but means all instances of the same geometry change identically. To vary individual instances, use Realize Instances Node first.

## Instance Bounds Node

### Instance Bounds Node

For every top-level instance, Instance Bounds returns its axis-aligned bounding box.

Useful for determining instance spatial extent—positioning or scaling based on size, etc.

Note: Only top-level instances are considered; nested instances inside instance geometry are not included (avoids realizing nested instances for performance).

See Nested Instancing.

### Inputs

Use Radius
For curves, point clouds, and Grease Pencil data, account for the radius attribute when computing bounds.

### Outputs

Min
Bounding-box minimum corner per instance, in local space.

Max
Bounding-box maximum corner per instance, in local space.

## Instance on Elements Node

### Instance on Elements Node

The Instance on Elements node creates instances of objects, collections, or geometry on selected elements (points, edges, faces, or corners) of input geometry. Offers flexibility for varied instancing workflows.

### Inputs

Geometry
Base geometry for instancing.

Instance On
Target element type.

Points:
One instance per point location.

Edges:
Instances along edges.

Faces:
Instances on each face surface.

Corners:
One instance per face corner (vertex per face).

Mask
Boolean selection controlling which elements receive instances. Floating-point values (0–1) act as probabilistic selection, yielding a random subset.

Input Type
Source geometry specification mode.

Data-Block:
Instance from an object or collection data-block.

Geometry:
Instance from node input geometry.

Instance Type Data-Block
When Data-Block input: Object or Collection.

Object / Collection Data-Block
Which object or collection to instance (Data-Block mode).

Instance Geometry
Which geometry to instance (Geometry input mode).

Realize Instances
Convert all instances to real geometry for a single merged output. Required for some downstream operations.

Keep Surface
Retain the underlying surface used for instancing instead of outputting only instances.

Seed
Random-number seed for probabilistic selections or instance-index randomization.

### Pick Instance Data-Block Collection

When instancing from a collection, optionally select which child object to instance per element.

Instance Index
Selection method for children.

Random:
Pick a random collection object per element.

Sequence:
Cycle through collection objects in order.

Input:
Use Instance Index input socket.

Instance Index Input
Index value (for "Input" mode).

### Transform

Surface Offset
Displace instances along the element normal.

Align Rotation
Align instance rotation to element orientation (e.g., surface normal).

Scale
Per-axis or uniform instance scaling.

### Outputs

Geometry
Result geometry with instances on selected elements.

## Instance on Points Node

### Instance on Points Node

The Instance on Points node places instances on each point of input geometry. Instances are efficient duplicates that avoid copying underlying data. Works with any point-domain geometry (meshes, point clouds, curve control points).

Point attributes propagate to the instance domain.

Tip: Use the Make Instances Real operator to convert instances to objects.

Note: For non-geometry object types (lights), use Object Info Node. Metaball objects are not supported.

### Inputs

Points
Input geometry; point positions control instance transforms.

Note: If input contains instances, the node creates instances on points inside the instances (nested instancing). New instances inherit the Rotation and Scale from inputs but also the parent instance transforms.

Selection
Boolean: true = create instance, false = skip.

Instance
Geometry to place on each selected point. May contain real geometry or multiple instances (useful with Pick Instance).

Pick Instances
If enabled, select an instance from the geometry's instance list per point instead of copying all geometry. Intended use: Collection Info Node.

Instance Index
Which instance to pick (only when Pick Instances = true). Defaults to point ID or index. Negative/out-of-range values wrap.

Rotation
Euler rotation per instance. Accepts outputs from Distribute Points on Faces, Curve to Points, or direction vectors converted via Align Rotation to Vector Node.

Scale
Size per generated instance.

### Outputs

Instances
Output geometry. If the input's id attribute exists, it copies to result instances.

## Instance Rotation Node

### Instance Rotation Node

The Instance Rotation node outputs the XYZ Euler rotation of each top-level instance in local modifier-object space.

See Instances for more information.

Note: Rotations display in degrees in the spreadsheet/editor but store internally as radians.

### Inputs

None.

### Outputs

Rotation
Vector indicating each top-level instance's rotation in radians.

## Instance Scale Node

### Instance Scale Node

The Instance Scale node outputs the per-axis size of top-level instances in local modifier-object space.

See Instances.

### Inputs

None.

### Outputs

Scale
Vector indicating each top-level instance's size.

## Instance Transform Node

### Instance Transform Node

The Instance Transform node outputs the Transformation Matrix of each top-level instance in local modifier-object space.

See Instances.

### Inputs

None.

### Outputs

Transformation
Matrix encoding each top-level instance's transform.

## Instances to Points Node

### Instances to Points Node

The Instances to Points node generates points at top-level instance origins. Instance-domain attributes move to the output point cloud.

Note: Top-level instances belong to the input geometry. Instances owned by other instances (nested) are not included.

### Inputs

Instances
Input geometry.

Selection
Boolean: true = create point, false = skip instance.

Position
Override default point position.

Radius
Output point radius.

### Outputs

Points
Output geometry.

## Randomize Transforms Node

### Randomize Transforms Node

Randomize Transforms perturbs instances with random translation, rotation, and scale. Common use: natural variation in scattered objects (rocks, trees, etc.).

### Inputs

Instances
Input geometry containing instances.

Selection
Boolean: true = randomize, false = leave unchanged.

Local Space

- Enabled: transformations in each instance's local space.

- Disabled: randomization in global space.

Offset
Maximum translation per axis. Sets the random movement range.

Rotation
Maximum rotation per axis. Sets how much rotation varies.

Scale Axes
How scaling applies.

Uniform:
Single random scale factor for all axes.

Axes:
Independent factor per axis.

Scale
Maximum scaling amount.

Flipping
Randomly mirror instances along one or more axes.

Seed
Integer seed for the random-number generator. Different seeds yield different arrangements with identical parameters.

### Outputs

Instances
Result geometry with randomized instance transforms.

## Realize Instances Node

### Realize Instances Node

The Realize Instances node converts instances into unique geometry data. This allows per-instance modification; without it, the same changes apply to all instances of shared geometry. However, performance degrades when realizing many complex-geometry instances, a fundamental computational trade-off.

Note: If input contains multiple volume instances, only the first volume moves to output.

### Attributes

When merging attributes from multiple geometry sources, the highest-complexity data type is chosen. For example, if a weight attribute is boolean on one source and vector on another, the output uses vector.

Named and anonymous attributes propagate from the instance domain to realized geometry. If an attribute exists on both base geometry and an instance, base-geometry values take precedence.

Note:

- The id attribute receives special handling to avoid duplication. Indices of each instance merge with id values from geometry points.

- Vertex groups preserve when realizing instances or joining geometries. If propagation rules yield vertex domain and float type, the attribute becomes a vertex group on output.

### Inputs

Geometry
Input geometry.

Selection
Which top-level instances to realize.

Realize All
Realize all nested-instancing levels for each top-level instance (overrides Depth).

Depth
Nesting levels to realize per top-level instance.

### Outputs

Geometry
Output geometry.

## Rotate Instances Node

### Rotate Instances Node

The Rotate Instances node rotates instances in local or global space.

See Instances.

### Inputs

Instances
Input geometry.

Selection
Boolean: true = rotate, false = leave unchanged.

Rotation
Euler rotation to apply.

Pivot Point
Rotation center. For local-space = true, relative to each instance's initial transform; for local-space = false, relative to modifier-object space.

Local Space
If enabled, rotate around the instance's local axes. If disabled, pivot-point and rotation are in modifier-object space.

### Outputs

Instances
Output geometry.

## Scale Instances Node

### Scale Instances Node

The Scale Instances node scales instances in local or global space.

See Instances.

### Inputs

Instances
Input geometry.

Selection
Boolean: true = scale, false = leave unchanged.

Scale
Scale factor per axis.

Center
Scale origin. Each instance moves away from this location. For local-space = true, relative to instance initial transform; for local-space = false, relative to modifier-object space.

Local Space
If enabled, scale along the instance's local axes. If disabled, center and scale inputs are in modifier-object space.

### Outputs

Instances
Output geometry.

## Set Instance Transform Node

### Set Instance Transform Node

The Set Instance Transform node applies a Transformation Matrix to instances.

See Instances.

### Inputs

Instances
Input geometry.

Selection
Boolean: true = transform, false = leave unchanged.

Transform
Matrix for translation, rotation, and scaling.

### Outputs

Instances
Output geometry.

## Translate Instances Node

### Translate Instances Node

The Translate Instances node moves top-level instances in local or global space.

See Instances.

### Inputs

Instances
Input geometry.

Selection
Boolean: true = translate, false = leave unchanged.

Translation
Displacement vector.

Local Space
If enabled, translation is relative to each instance's initial rotation. If disabled, translation is in modifier-object space.

### Outputs

Instances
Output geometry.

## Dual Mesh Node

### Dual Mesh Node

Dual Mesh takes a mesh and emits its dual: every face turns into a vertex and every vertex into a face. Face-domain attributes transfer to the point domain in the dual.

Warning: Only works on manifold (water-tight) geometry. Remesh non-manifold input first.

### Inputs

Mesh
Input geometry.

Keep Boundaries
Preserve non-manifold mesh boundaries by creating additional geometry and skipping the dual transformation there.

### Output

Dual Mesh
Output geometry.

### Examples

The Dual Mesh Node pairs well with triangulated meshes. An Ico Sphere (evenly-spaced triangles) is a good example.

## Edge Paths to Curves Node

### Edge Paths to Curves Node

The Edge Paths to Curves node outputs curves following paths across mesh edges.

See also: Use with the Shortest Edge Paths Node output. Similar to Edge Paths to Selection Node but creates a curve per path instead of edge selections.

### Inputs

Mesh
Input mesh.

Start Vertices
Which vertices to begin traversal.

Next Vertex Index
Path direction at each vertex.

### Outputs

Mesh
Output curves.

## Edge Paths to Selection Node

### Edge Paths to Selection Node

The Edge Paths to Selection node traverses paths across mesh edges and outputs a boolean selection of all visited edges.

See also: Intended to receive Shortest Edge Paths Node output. Combine with Separate Geometry Node to discard unused edges.

### Inputs

Start Vertices
Which vertices to begin traversal.

Next Vertex Index
Path direction at each vertex.

### Outputs

Selection
Boolean field marking all visited edges.

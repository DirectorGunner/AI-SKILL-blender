# Clump Hair Curves, Create Guide Index Map, Curl Hair Curves, Curve Info ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Clump Hair Curves; Create Guide Index Map; Curl Hair Curves; Curve Info; Curve Root; Curve Segment; Curve Tip; Hair Attachment Info; Attach Hair Curves to Surface; Redistribute Curve Points; Restore Curve Segment Length; Set Hair Curve Profile; Geometry Nodes; Collection Node; Material Node; Object Node; Rotation Node; String Node.

## Clump Hair Curves

### Clump Hair Curves

Clump Hair Curves draws nearby strands together around chosen guide curves, forming the clumps seen in real hair, fur, and grass. A cornerstone of grooming for realism and structure, it stands in for how strands bunch from moisture, product, or contact.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for clumping.

Factor
Overall strength of the clump. At 0.0 nothing clumps; at 1.0 curves pull fully toward their guides.

Shape
How the clump reads along each strand. At 0.0 the strength is even; at 0.5 it falls off linearly from root to tip.

Tip Spread
Works random variation into curve-tip positions, blocking perfect convergence so clumps read natural.

Clump Offset
Lays a random directional offset over whole clumps, adding subtle variation between groups.

Distance Falloff
How a guide's pull fades with distance. At 0.0 there is no falloff, so every nearby curve is affected equally.

Distance Threshold
The farthest a curve can sit from a guide and still feel the clump. Past this threshold, that guide has no influence.

Seed
Drives the randomization behind offsets and variation. Move it to redistribute clumping randomly under the same settings.

Preserve Length
On, each strand holds its starting length. Off, curves may stretch or shrink a bit as they are drawn toward guides.

### Guide Map

Guide Index
A map of which guide curve sits at the heart of each clump. Provide one and it outranks any guide_curve_index attribute already present; the spacing and mask inputs below drop out.

Guide Distance
Smallest gap allowed between picked guide curves when one of these maps is generated. Bigger values give fewer, chunkier clumps.

Guide Mask
Gates which curves qualify as guides while a map is auto-generated.

Existing Guide Map
On, fall back on whatever guide map attribute is already around. Off, lacking a Guide Index, the node makes one from the distance and mask above. Authoring it on its own lets you fine-tune where guides land and how they group.

### Outputs

Geometry
Output geometry with the clumped hair curves.

### Guide Map

Guide Index
The index map this run relied on. Generated fresh here? It is stored and emitted through this output for reuse down the line.

## Create Guide Index Map

### Create Guide Index Map

Create Guide Index Map writes an integer attribute called guide_curve_index tying every hair curve to its nearest guide curve. Each non-guide curve gets the index of the guide it should follow.

Downstream hair-grooming nodes (for example, Braid Hair Curves, Clump Hair Curves) lean on this map to bundle curves into logical groups around shared guides and apply effects uniformly.

Other nodes in the Hair Guides Nodes category can build a map internally for convenience, but the attribute they produce matches what this node writes.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for grouping, optionally carrying existing guide curves too.

Guides
The curves or points eligible to act as guides — the candidates other curves get assigned to.

Guide Distance
The minimum spacing between chosen guides. It stops guides from being picked too close together and shapes how broad each guide's influence region runs.

Guide Mask
A mask limiting which curves may turn into guides; those with a mask value of 0 cannot be chosen.

Group ID
An ID splitting the curves into independent groups for guide assignment; a curve only picks a guide carrying the same Group ID value. Handy for keeping separate regions — say the left versus right side of a groom — from mixing.

### Outputs

Geometry
The geometry you fed in, now with two extras:

- A guide_curve_index attribute that records each curve's assigned-guide index.

- A anonymous attribute standing for the guide selection. Normal curves and the picked guide curves both remain in the result.

Guide Curves
A geometry output carrying only the curves picked as guides.

Guide Index
An integer attribute giving, per curve, the index of the closest guide curve with the matching Group ID .

Guide Selection
A boolean selection attribute, true only on curves that were chosen as guides. Use it to isolate, visualize, or further process the guide curves.

## Curl Hair Curves

### Curl Hair Curves

Curl Hair Curves bends existing strands into curls by winding them around nearby guide curves — the tool for coiled, spiral, or wavy looks and for layering stylized flair or realism onto a groom. Each curl's radius, turn rate, and start point can shift, and optional random offsets break up the regularity.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for curling.

Factor
Overall strength of the curl. At 0.0 the effect is off; at 1.0 the full curl deform applies.

Subdivision
Subdivisions applied before the deform. Higher values smooth the curls but add processing time.

Curl Start
The percentage along each strand (root to tip) where the curl begins, letting you keep part of the strand straight ahead of it.

Radius
The curls' overall radius. Larger values loosen the curls; smaller values tighten them into spirals.

Factor Start
Multiplies curl radius near the start of the curl region, so tightness tapers in or builds gradually.

Factor End
Multiplies curl radius near the strand's end, steering how curls taper off or unwind toward the tip.

Frequency
How many full turns run down the strand's length; higher values pack in more curls. It can vary per point along the strand, enabling complex wave patterns.

Random Offset
Works random variation into each strand's curl phase or starting angle, for a more natural, less uniform look.

Seed
The random seed behind the random offsets. Move it for different curl variations under the same settings.

### Guide Map

Guide Index
A map flagging which curve is the guide, or central reference, for each cluster of curled curves. Pass one in and it trumps any guide_curve_index attribute on hand; the two settings below sit idle.

Guide Distance
How far apart picked guides must be when the node spins up its own map. Raise it for fewer guide curves and wider curl groups.

Guide Mask
A mask choosing which curves can stand in as guides.

Existing Guide Map
On, reuse a guide map attribute that already exists. Off, absent a Guide Index, the node derives one from the spacing and mask above. Authoring it separately buys you steadier control and consistency across grooming steps.

### Outputs

Geometry
Output geometry with the curled hair curves.

### Guide Map

Guide Index
The index map this operation leaned on. Should the node have generated a fresh one, it lands here for downstream nodes to pick up.

## Curve Info

### Curve Info

Curve Info hands back per-curve attributes covering each curve's identity, geometry, and relationships in a hair or curve system. It turns up often in procedural grooming and deform setups, driving randomization, orientation, or any effect keyed to curve properties.

### Inputs

No inputs on this node.

### Outputs

Curve Index
Each curve's index within the geometry component. Use it for deterministic indexing or pattern generation.

Curve ID
A stable, unique ID per curve. Unlike Curve Index , it holds steady as curves are added or removed.

Length
Each curve's total length along its evaluated spline. Useful for scaling effects or tuning deform strength by hair length.

Direction
A unit vector from root toward tip on each curve. It captures overall heading and can orient instances or drive direction-dependent effects.

Random
A random vector per curve, seeded from the Curve ID . Randomization stays consistent across evaluations, so results read reproducible yet varied.

Surface UV
On the surface mesh, the UV coordinates of each curve's attachment point. The usual jobs: sampling textures, ferrying color across, or driving procedural effects from surface position.

## Curve Root

### Curve Root

Curve Root reports on the root point of each curve. It turns up in hair grooming and procedural setups to anchor deforms, apply transforms relative to the curve base, or isolate operations that hit only the roots.

### Inputs

No inputs on this node.

### Outputs

Root Selection
A boolean mask flipped true at curve root points and nowhere else. Handy for running operations strictly at the curve base.

Root Position
Each curve's root point in 3D space. Use it to align objects, sample data off a surface, or build root-based effects.

Root Direction
A unit vector for the first segment's heading, away from the root toward the next control point. Useful for orienting instances or reading initial growth direction.

Root Index
The index of each curve's root point. Usually 0 on every curve, but it can flag root points across several curves processed together.

## Curve Segment

### Curve Segment

Curve Segment reports on the segment linking each point to the one before it. It helps when analyzing or reworking per-segment data — length, direction, connectivity — and when building effects keyed to local curve structure.

### Inputs

No inputs on this node.

### Outputs

Segment Length
How far the current point sits from its predecessor on the same curve. Use it to gauge curve smoothness, catch segment stretching, or deform relative to curve length.

Segment Direction
A unit vector aimed from the prior point at the current one. It captures the segment's local tangent heading.

Neighbor Index
The index of the previous neighboring point along the curve. Use it to reference or sample attributes from the adjacent point.

## Curve Tip

### Curve Tip

Curve Tip reports on the tip — the end point — of each curve. It comes up in hair grooming, deform, and simulation setups to steer operations at curve ends: shaping, alignment, or tip-based effects.

### Inputs

No inputs on this node.

### Outputs

Tip Selection
A boolean mask reading true at curve tip points alone. Use it to single out operations that touch just the curve ends.

Tip Position
Each curve's tip point in 3D space. Useful for pinning where curves end, placing instances, or measuring length.

Tip Direction
A unit vector for the heading of each curve's final segment, toward the tip. Use it to orient instances or drive effects keyed to curve direction.

Tip Index
The index of each curve's tip point — the last point in the curve's point list.

## Hair Attachment Info

### Hair Attachment Info

Hair Attachment Info reports how and where hair curves bind to a surface mesh — letting nodes pull stored attachment coordinates, check whether the attachment still holds, and read the surface normal there. Such data is vital for deforming, simulating, and reattaching hair when the mesh shifts.

### Inputs

Surface Geometry
Whatever surface geometry the hair curves are bound to — usually the very mesh that drove hair generation or interpolation.

Surface UV Map
A UV map across the surface mesh that pins down each curve's attachment point, so the node can pull back the stored coordinates per curve.

### Outputs

Attachment UV
Per-curve UV coordinates marking where on the surface a curve binds. Held per curve, they usually let the right attachment spot be found even after the surface topology shifts.

Attachment is Valid
A boolean output flagging whether each curve carries a valid stored attachment. Use it to catch invalid or missing attachment data after topology edits or a surface swap.

Surface Normal
The surface mesh's normal heading evaluated at the curve's attachment point. Use it to align hair roots, orient instances, or drive deformation by surface orientation.

## Attach Hair Curves to Surface

### Attach Hair Curves to Surface

Attach Hair Curves to Surface ties hair curves to a surface mesh, fixing their attachment positions and, if you want, aligning them to the surface orientation. It is a backbone of hair generation and grooming, holding curves anchored where they belong on the base mesh through later deforms or topology edits.

Note

This node or modifier only works given valid Surface geometry or object inputs together with a Surface UV Map .

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for attaching to the surface.

Surface Input Type
How the surface geometry arrives for attachment. With both wired, the geometry input wins.

Object :

Use an object reference as the target surface.

Geometry :

Wire a geometry input straight to the surface mesh.

Surface
Whatever object or geometry serves as the attachment target. For clean alignment, its transforms must match the modifier object.

Surface UV Map
A UV map that nails down attachment points across the surface; the resulting coordinates are kept per curve so attachment stays steady.

Surface Rest Position
On, the surface mesh drops to its rest pose ahead of attachment, keeping results consistent when curves later deform along that same surface.

Tip

Run this alongside Deform Curves on Surface and turn on Surface Rest Position when that step comes after, so attachment coordinates are logged in the pre-deformed state.

Sample Attachment UV
Reads the Surface UV Map at the attachment point and banks those UV coordinates per curve, leaving the attachment data on hand for later nodes.

Snap to Surface
Drops each curve's root onto the closest spot on the surface mesh, planting every root right on the surface.

Align to Surface Normal
Spins each curve so its root direction meets the surface normal. Stable output here usually wants guide data or consistent curve orientation.

Blend along Curve
Brings the deform or alignment in by degrees from root to tip, rather than slapping it on uniformly.

### Outputs

Geometry
Output geometry with refreshed curve attachments.

Surface UV Coordinate
Per curve, the matching UV coordinate on the surface mesh at its attachment point.

Surface Normal
The surface mesh's normal vector taken at each curve's attachment point.

## Redistribute Curve Points

### Redistribute Curve Points

Redistribute Curve Points moves existing control points to sit evenly spaced down each curve. It improves uniformity — especially after deforms or procedural steps that warp point spacing — keeping interpolation consistent and results smoother.

### Inputs

Curves
Curves — the input geometry whose control points get redistributed.

Factor
Strength of the redistribution. At 0.0 the curves are unchanged; at 1.0 even spacing applies fully.

Feature Awareness
A lightweight feature-preserving algorithm that tries to hold local curve features and direction changes as points move, keeping detailed areas or sharp bends more accurate.

### Outputs

Curves
Output geometry with redistributed, evenly spaced curve control points.

## Restore Curve Segment Length

### Restore Curve Segment Length

Restore Curve Segment Length brings each curve segment back to its original length from a reference position, usually a pre-deformation state. It fixes unwanted stretch or squeeze that creeps in after curve deforms, simulations, or procedural edits.

### Inputs

Curves
Curves — the input geometry whose segment lengths get restored.

Selection
A boolean field choosing which points or segments are affected; unselected ones stay put.

Factor
How much the length restoration weighs in. At 0.0 the curves are left as-is; at 1.0 the original segment lengths are fully restored.

Reference Position
The pre-deformation position of curve points, used to work out the original segment lengths the node tries to restore.

Pin at Parameter
Names a parameter along each curve as a fixed anchor during restoration; other points shift relative to that pinned spot, heading off unwanted drift.

### Outputs

Curves
Output geometry with per-segment lengths restored against the supplied reference positions.

## Set Hair Curve Profile

### Set Hair Curve Profile

Set Hair Curve Profile sets strand radius down the length via a customizable profile shape, giving artists control over thickness variation from root to tip — natural tapering or stylized width tweaks.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in, whose radius gets modified.

Replace Radius
On, the node swaps the existing radius attribute for a new one. Off, the new radius multiplies into the existing value.

Radius
The base radius applied to every curve when Replace Radius is on, setting the overall scale of hair thickness.

Shape
How the radius shifts down the curve — for instance, a tapered profile with thicker roots and thinner tips.

Factor Min
The radius multiplier at each curve's start (root), steering how thick the curve begins.

Factor Max
The radius multiplier at each curve's end (tip), steering how thin the curve gets toward the tip.

### Outputs

Geometry
Output geometry with updated radius attributes down each hair curve.

## Geometry Nodes

### Geometry Nodes

### Node Types

Tip

Asset Catalogs holding geometry node groups will show up in the add menu too.

## Collection Node

### Collection Node

A single collection comes out of the Collection input node. Feed it into other collection sockets and one collection becomes easy to share across many spots.

### Inputs

No inputs on this node.

### Properties

- Collection

### Output

Collection
A handle pointing at the chosen Collection.

## Material Node

### Material Node

The Material input node puts out a single material. Wire it to other material sockets to make reusing the same material name in several places more convenient.

Tip

Dragging a material data-block into the node editor and dropping it also spawns the Material node, with the dropped material already chosen in the Data-Block Menu.

### Inputs

No inputs on this node.

### Properties

- Material

### Output

Material
A handle pointing at the chosen material.

## Object Node

### Object Node

A single object emerges from the Object input node. Run it into other object sockets and one object is simple to reuse in many spots.

### Inputs

No inputs on this node.

### Properties

- Object

### Output

Object
A handle pointing at the chosen object.

## Rotation Node

### Rotation Node

The Rotation input assembles a rotation out of euler values.

### Inputs

No inputs on this node.

### Properties

X, Y, Z
The rotation amount about each axis.

### Output

Rotation
Standard rotation output.

## String Node

### String Node

A single string comes out of the String input node. Connect it to attribute-name sockets and one attribute name is easy to reuse across many spots.

### Inputs

No inputs on this node.

### Properties

- String

### Output

String
Standard string output.

## Dial Gizmo

### Dial Gizmo

The Dial Gizmo node is well suited to building gizmos that control angles.

### Inputs

Value
Special gizmo value socket. Anything wired into this socket gets modified as the gizmo is rotated.

Position
Where the gizmo sits in the object's local space.

Up
The gizmo's up or normal direction in the viewport.

Screen Space
On, the gizmo holds the same on-screen size whatever the zoom level. This shifts what the radius input means.

Radius
In screen-space mode, a factor layered on top of the default radius. Otherwise, the gizmo's radius in Blender units.

### Properties

Color
Sets which theme color this gizmo uses.

### Outputs

Transform
Meant to be joined into the geometry this gizmo controls.

## Linear Gizmo

### Linear Gizmo

The Linear Gizmo node is the most broadly applicable gizmo. It can, for instance, control the height of something.

### Inputs

Value
Special gizmo value socket. Anything wired into this socket gets modified as the gizmo is moved.

Position
Where the gizmo sits in the object's local space.

Direction
Sets the direction the gizmo points or moves in.

### Properties

Color
Sets which theme color this gizmo uses.

Draw Style
Lets you pick among different gizmo styles.

### Outputs

Transform
Meant to be joined into the geometry this gizmo controls.

## Transform Gizmo

### Transform Gizmo

A compound gizmo, the Transform Gizmo node can steer position, rotation, and scale together.

### Inputs

Value
Special gizmo value socket. Whatever feeds in here changes as the gizmo is adjusted.

Position
Where the gizmo sits in the object's local space.

Rotation
The gizmo's local orientation.

Note

The 3D viewport ignores the rotation input when the transform orientation is set to global.

### Properties

The node carries sidebar properties that let you disable parts of the gizmo. Handy when, for instance, controlling only a translation or only a rotation.

### Outputs

Transform
Meant to be joined into the geometry this gizmo controls.

## Import CSV Node

### Import CSV Node

The Import CSV node loads tabular (Comma-Separated Values) files and generates a point cloud. Each row becomes a single point; numeric columns map to point attributes.

The header row (if present) furnishes attribute names. Column types are inferred from the first value: integers yield integer attributes, floats yield float attributes.

Note: Only integer and float columns are imported; other types are skipped.

Useful for embedding external tabular datasets into Geometry Nodes workflows—scientific visualization, data-driven procedural generation, or similar tasks.

### Inputs

Path
File path to the CSV source. Must be structured with one row per point, values delimited by a separator character.

Delimiter
Character separating values within each row (comma, semicolon, tab, etc.).

Tip: Use the Special Characters Node to insert tab characters.

### Outputs

Point Cloud
Output geometry as a point cloud; each CSV row produces one point.

## Import Nodes

### Import Nodes

Nodes that pull data from external file formats into the workspace.

Geometry Nodes supports automatic import-node creation: drag a supported file type into the node editor and it creates and configures the appropriate import node with the file path pre-filled.

## Import OBJ Node

### Import OBJ Node

The Import OBJ node reads geometric data from a .obj file and outputs instances.

Each OBJ-defined object becomes a separate instance, preserving scene hierarchy and enabling efficient manipulation within Geometry Nodes. Useful for incorporating externally modeled static 3D assets.

Note: Mesh geometry only; materials and textures are excluded.

See also: OBJ Import Operator

### Inputs

Path
File path to the .obj source.

### Outputs

Instances
Instance collection representing objects from the imported file.

## Import PLY Node

### Import PLY Node

The Import PLY node pulls mesh data from a .ply (Polygon File Format / Stanford Triangle Format) file.

PLY files store scanned or modeled geometry and may contain per-vertex attributes such as colors or normals. The result is a single unified mesh.

Lets procedural workflows incorporate external static geometry directly into Geometry Nodes.

See also: PLY Import Operator

### Inputs

Path
File path to the .ply source.

### Outputs

Mesh
The imported mesh.

## Import STL Node

### Import STL Node

The Import STL node loads surface geometry from a .stl (Stereolithography) file.

STL files are typical in 3D printing and CAD, storing surface-only geometry as a triangle collection. No color, texture, or other attributes are present.

Enables procedural processing and visualization of external STL assets within Geometry Nodes.

See also: STL Import Operator

### Inputs

Path
File path to the .stl source.

### Outputs

Mesh
The imported mesh.

## Import Text Node

### Import Text Node

The Import Text node reads a plain text file and outputs its full contents as a single string. Suitable for motion-graphics or data-driven workflows needing external text handling or display.

Note: .txt extension files only.

### Inputs

Path
File path to the text source.

### Outputs

String
Complete file contents as a single string.

## Import VDB Node

### Import VDB Node

The Import VDB node reads volumetric data from a .vdb file and outputs it as Volume geometry. All grids in the file are loaded into the resulting volume.

Useful for incorporating simulation output or procedurally generated volumes from external software.

### Inputs

Path
File path to the .vdb source.

### Outputs

Volume
A Volume geometry holding all grids from the file.

## 3D Cursor Node

### 3D Cursor Node

The 3D Cursor node outputs the scene's 3D cursor position and orientation.

Note: Available in Tool context only.

### Inputs

None.

### Outputs

Location
The cursor's world position.

Rotation
The cursor's orientation as a standard rotation value.

## Active Camera Node

### Active Camera Node

The Active Camera node returns the currently active camera in the scene.

### Inputs

None.

### Outputs

Active Camera
The scene's active camera object.

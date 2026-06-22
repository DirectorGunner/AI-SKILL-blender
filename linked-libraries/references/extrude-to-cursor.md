# Extrude To Cursor, Extrude Region, Common Modifier Options, Array Legacy Modifier ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Extrude to Cursor; Extrude Region; Common Modifier Options; Array (Legacy) Modifier; Sidebar; Reconstruction; Solve; Baking Physics Simulations; Shader Nodes; Light Linking.

## Extrude to Cursor

Extrude to Cursor

Mode: Edit Mode
Shortcut: Ctrl - RMB

Ctrl - RMB creates new vertices interactively at the mouse cursor position. This fundamental operation lets you build connected geometry by placing vertices and edges.

A single vertex is created by Ctrl - RMB when no vertices are selected. Since the 2D screen cannot convey full 3D position from a click alone, the new vertex is placed at the 3D cursor's depth.

Building connected sequences: after placing one vertex, keep the most recent vertex selected and repeat Ctrl - RMB to add subsequent vertices. Each new click creates a vertex at the cursor and links it to the previous vertex with an edge. This workflow builds open chains and networks quickly.

Creating Planar Faces with Two Vertices

Two connected vertices with an existing edge allow Ctrl - RMB to create a planar quad. Blender follows your mouse and constructs the quad in your current viewport plane.

By default, Blender automatically rotates the source edge (the last selected one) to smooth angles between the new edge and existing neighbors. This automatic rotation uses the X and Y displacement of the new and previous edges. If the angle exceeds a threshold, Blender wraps the faces. To prevent automatic rotation, use Shift - Ctrl - RMB instead.

Three or more selected vertices with Ctrl - RMB create planar faces along the selection, following cursor direction — an operation similar to extrusion.

Extrusions are viewport-dependent: the extrusion direction changes when you switch viewports (top, side, front), aligning the geometry to your current orthographic view.

## Extrude Region

Extrude Region

Mode: Edit Mode
Toolbar: Extrude Region
Shortcut: E

Extrusion duplicates vertices while maintaining connectivity to original geometry. Vertices become edges; edges become faces. This is a core operation for building new mesh topology.

You can create boxes from squares, cylinders from circles, and tree branches or organic structures. The extrusion direction is interactive and defaults to the surface normal for faces. Extrusion can be restricted to a single axis (see Axis Locking).

Different extrusion tools vary in how new geometry connects internally. The border loop of the selection extrudes while the interior stays in place.

The Algorithm

Extrude operates through several steps:

First, the algorithm finds the outer edge boundary of the extrusion region. By default, edges belonging to two or more selected faces are treated as internal and excluded from the boundary.

Boundary edges are converted to faces.

If boundary edges belong to only one face in the entire mesh, all selected faces are duplicated and linked to the new faces (producing boxes from rectangles, for example).

Otherwise, selected faces link to new faces without duplication, preventing unwanted interior faces in the result.

For fully closed volumes (like a cube with all six faces), extrusion simply duplicates the volume without connecting it to the original.

Edges in "open" loops (not part of selected faces) are duplicated, with a new face created between the original and duplicate edge.

Single isolated vertices duplicate and form a new edge between the original and new vertex.

## Common Modifier Options

Many modifiers share common options for controlling their effect on specific vertices using weights or textures.

Vertex Groups enable targeted per-vertex control. A group's weights determine how strongly the modifier acts on each vertex.

A field displays the current group name. When a group is renamed, any modifier referencing it loses the link (the field turns red), requiring manual re-selection.

Invert reverses the group's effect—selected vertices now represent areas the modifier will not touch. The inversion flips the weight values.

Texture-based masking allows any image (including procedural textures) to control modifier strength. Most often the grayscale value is used, though some modifiers (like Displace in certain modes) read RGB channels.

The Texture field selects which texture to use. A properties icon button jumps to that texture's settings.

Texture Coordinates specify how to sample the texture at each vertex:

UV uses face UV coordinates from the geometry. The system finds UV values for each vertex from the first face using it; additional faces are ignored. This can produce artifacts on meshes with discontinuous UVs.

UV Map selects which UV layer to sample. If missing, the system defaults to Local coordinates.

Object reads texture coordinates from another object's local space. Moving that object updates the texture position. If empty, Local is used.

Moving the source object also shifts the texture mapping. If you need stable displacement relative to the modified object, consider parenting the source object to it.

Global uses world-space coordinates.

Local uses the modified object's local space.

Use Channel selects which texture information to read:

Intensity takes the average of RGB channels (RGB 1.0, 0.0, 0.0 = 0.33 intensity).

Red/Green/Blue/Alpha reads individual color channels.

Hue extracts the HSV hue value (color position on the standard wheel).

Saturation extracts the HSV saturation (1.0 for pure colors, 0.0 for grays).

Value extracts the HSV brightness component.

All channels are gamma-corrected except Intensity.

## Array (Legacy) Modifier

The Array modifier creates an array of copies of the base object, each offset from the previous in any of several possible ways. Vertices in adjacent copies can be merged if nearby, allowing smooth Subdivision Surface frameworks to be generated. It's useful with tileable meshes for quickly developing large scenes, and for creating complex repetitive shapes. Multiple Array modifiers can be active on one object at the same time (e.g. to create complex three-dimensional constructs).

Options:
Fit Type — controls how the array's length is determined; the three choices each activate the display of the Curve, Length, or Count settings below.
- Fit Curve: generate enough copies to fit within the length of the curve object specified in Curve.
- Fit Length: generate enough copies to fit within the fixed length given by Length.
- Fixed Count: generate the number of copies specified in Count.
Note: both Fit Curve and Fit Length use the base object's local coordinate-system size, so scaling the base object in Object Mode won't change the number of copies generated; Fit Curve uses the curve's local coordinate-system length, so scaling the curve in Object Mode won't change it either — applying the scale can be useful for both.

Relative Offset:
Factor X/Y/Z — add a translation equal to the object's bounding-box size along each axis, multiplied by a scaling factor; X, Y, and Z scaling factors can be specified.

Constant Offset:
Distance X/Y/Z — add a constant translation component to the duplicate's offset; X, Y, and Z constant components can be specified.

Object Offset — add a transformation taken from an object (relative to the current object) to the offset. It's good practice to use an empty centered on or near the initial object — for example, rotating that empty creates a circle or helix of objects.

Merge — when enabled, vertices in each copy are merged with vertices in the next copy within the given Distance.
First and Last Copies — when enabled along with Merge, vertices in the first copy are merged with those in the last copy (again within Distance range), useful for circular objects.
Distance — controls the merge distance for Merge and First and Last Copies.

UVs:
Offset U/V — shift the UVs of each new duplicate by a settable amount.

Caps:
Cap Start, End — give either endpoint of the array a different mesh: the start as if at position -1 (one "array step" before the first regular copy), the end as if at position n + 1 (one "array step" after the last regular copy). When Merge is on, cap vertices within the Distance threshold are merged.
Note: the start/end cap objects currently do not support the First and Last Copies option.

Hints — Offset Calculation: the transformation from one copy to the next is the sum of three components (Relative, Constant, and Object), each independently enabled/disabled. This allows, for example, a relative offset of (1.0, 0.0, 0.0) and a constant offset of (0.1, 0.0, 0.0), giving an array neatly spaced along the X axis with a constant 0.1 unit between objects whatever the original object's size.

Examples: a chain created from a single link; a tentacle made with an Array Modifier followed by a Curve Modifier, where the foreground segment is the base mesh and the tentacle is capped by two specially-modeled objects deformed by the same Curve object as the main part. Fractal: a multi-level array animated with motion blur, and a fractal created with multiple arrays.

## Sidebar

### Sidebar

### Mask Settings

Start Frame, End Frame
Pin down the mask's frame range for the Sequencer .

### Mask Layers

Mask Layer panel.

A mask layer collects one or more splines so that operations treat them as a single group.
With layers you can build up complex shapes and set how the splines play off one another.
Splines sharing a layer can be animated as a unit — driven, say, by an item
from motion tracker footage.
Such tooling might parent the whole batch of splines to a single piece of motion tracking data, or
simply transform them all at once.

Opacity
Dials in how opaque the mask layer is.

Invert
Flips the values (colors) of the mask layer.

Blend
Which blending operation the layer performs. See Color Blend Modes.

Modes Merge Add and Merge Subtract
hold up better than plain mathematical addition and subtraction
when a Feather is in play on overlapping masks.

Falloff
Which Feather falloff type to use; it shapes how the transition from black to white runs.

Overlap
Fills in the areas where the spline crosses itself.

Holes
Splines that overlap within the same layer will punch holes into the mask.

| The Overlap option example. | The Holes option example. |

### Example

A concrete scenario makes the point of mask layers clearer.
Imagine the footage has two people you'd rather hide, one walking left to right and
the other heading the opposite way. Put each on its own mask layer, both within
one mask data-block, and you can mask them separately. Where the two shapes cross, they add together rather than
punching a hole — which is what would happen if they shared a layer. When the motion is straightforward enough,
one motion-tracked point can drive the whole mask layer's position.

### Active Spline

Active Spline panel.

Feather Offset
Which method works out the offset of the mask spline's feather.

Even :

Holds the feather's thickness steady, though it can throw unwanted loops into the feather curve.

Smooth :

Produces a cleaner, smoother shape,
yet may leave an unwanted sharp feather wherever a curve segment bends into an S.

Weight Interpolation
Which way the weight (feather thickness) is interpolated from one point to the next —
Linear or Ease (that is, the change eases in slowly at the start and the end).

Cyclic
Whether the spline is closed or left open.

Fill
Builds splines with their interiors filled in.
Switch it off and Blender draws curves with a thickness instead, to mask thin objects like wires or hair.

Self Intersection Check
Keeps the feather (not the curve itself) from crossing over itself.

### Active Point

Active Point panel.

This panel turns up whenever both a tracking marker and a mask are selected.

### Parent

Inside the Movie Clip Editor you can tie an entire mask, or just its points, to motion tracks,
so that the mask or those points ride along with the tracks.

Parent
The Data ID the mask or spline is parented to;
when parenting to movie tracking data, it points at a Movie Clip data-block.

Parent Type
Point Track, Plane Track

Object
Which object to parent to.

Track
The name of an individual track.

### Animation

Manages the animation data behind the mask's properties, the active Actions
and the Slot each is assigned included.

See Manually Assigning Actions and Slots for more information.

## Reconstruction

Align 3D bundles and reconstructed geometry within your scene using orientation operators.

Set Origin
Reference
Mode: Tracking
Menu: Reconstruction ‣ Set Origin

Reposition the camera so your active track sits at the origin; applies translation only.

Set Floor
Reference
Mode: Tracking
Menu: Reconstruction ‣ Set Floor

Three markers define a horizontal reference plane; camera shifts to place these markers at Z = 0.

Set Wall
Reference
Mode: Tracking
Menu: Reconstruction ‣ Set Wall

Anchors a vertical plane instead of horizontal—selected tracks align to the XZ plane.

Set X/Y Axis
Reference
Mode: Tracking
Menu: Reconstruction ‣ Set X/Y Axis

Positions your active track along the X or Y axis without moving the origin point.

Set Scale
Reference
Mode: Tracking
Menu: Reconstruction ‣ Set Scale

Scales camera or object to make the distance between two marks match a specified value.

Apply Solution Scale
Reference
Mode: Tracking
Menu: Reconstruction ‣ Apply Solution Scale

Permanently scales the tracking solution instead of the camera.

Link Empty to Track
Reference
Mode: Tracking
Menu: Reconstruction ‣ Link Empty to Track

Creates an empty and constrains it to follow the active track.

3D Markers to Mesh
Reference
Mode: Tracking
Menu: Reconstruction ‣ 3D Markers to Mesh

Converts solved track positions into mesh vertices; builds a starting point for hand-sculpting geometry. A motion solve must complete first; only the current tracking object contributes.

## Solve

Solve panel options.

Plane Track
See Create Plane Track documentation.

Solve

Tripod
Tripod Motion solves rotation-only footage (camera stationary). Generic solving cannot determine 3D feature positions (insufficient parallax), so this solver recovers relative rotation only, reprojecting features to a sphere (uniform camera-to-feature distance).

Note: Tripod solving behaves differently—more tracks don't guarantee accuracy. 5–10 tracks per frame suffice.

Keyframe
Automatically selects keyframe pairs. Complex algorithms find minimal reconstruction error and optimal scene scale.

Keyframe A/B
Reconstruction range start (A) and end (B).

Refine
Specifies camera-intrinsic parameters to refine during solving. Useful when uncertain; solver explores best values. Requires approximate initial values—completely wrong initial values prevent convergence.

Focal Length: Refines focal length.

Optical Center: Refines optical center.

Radial Distortion: Refines radial coefficients.

Tangential Distortion: Refines tangential coefficients.

Solve Camera/Object Motion
See Solve Camera/Object Motion documentation.

Cleanup

Operators and settings remove poor-quality tracks (insufficient length, high reconstruction error).

Frames
Removes tracks or segments shorter than this frame count.

Error
Removes tracks exceeding this error threshold.

Type
Action applied to flagged tracks.

Select: Highlights them.

Delete Track: Removes entirely.

Delete Segments: Removes bad segments.

Clean Tracks
See Clean Tracks documentation.

Filter Tracks
See Filter Tracks documentation.

Geometry

3D Markers to Mesh
See 3D Markers to Mesh documentation.

Link Empty to Track
See Link Empty to Track documentation.

Orientation

Scene orientation tools reposition objects to bundles.

Floor
See Set Floor documentation.

Wall
See Set Wall documentation.

Set Origin
See Set Origin documentation.

Set X, Y Axis
See Set X/Y Axis documentation.

Set Scale
See Set Scale documentation.

Apply Scale
See Apply Solution Scale documentation.

Distance
Scene-unit distance used by Set/Apply scale.

Scene Setup

Set as Background
See Set as Background documentation.

Setup Tracking Scene
See Setup Tracking Scene documentation.

## Baking Physics Simulations

Baking caches calculated simulation results to memory.

Automatic caching occurs during playback; subsequent playbacks replay from cached data faster.

Baking protects the cache; simulation settings become uneditable until cache deletion (Delete Bake).

It is recommended practice to bake physics simulations before rendering. Avoids re-simulation time; prevents glitches; ensures consistent results across renders.

Note: Most physics simulators use similar caching; not all expose identical settings. Coverage below is comprehensive; individual types may omit some options.

Options

Two simultaneous caches displayed.

Caches List
Blender manages multiple simultaneous caches for one physics object.

Rename by double-clicking. Named caches store disk files prefixed with the name (e.g., MyCache → MyCache_xxxxxx_yy.bphys). Unnamed caches use object-name-derived filenames (Cube → 43756265_xxxxxx_yy.bphys, where 43756265 encodes the object name).

Warning: Multiple caches on one object require explicit Cache Names. Unnamed-cache conflicts (same object name) cause file loss.

External
Reads cache from disk via specified path.

Note: Cache name in Caches List and Index must match external filenames (format: name_frame_index.bphys).

Index
External file index (last two digits of filename).

Path
Cache file directory.

Disk Cache
Saves simulation cache to disk (separate from blend file) in blendcache_[filename] folder.

Note: Blend file must be saved first.

Use Library Path
Share disk cache when the physics object is linked into another blend file. Enabled = linked versions share cache; disabled = independent caches.

Start
Simulation start frame.

End
Simulation end frame.

Note: Calculation occurs only for positive frames between Start and End, baked or not. Extend End frame for longer simulations.

Cache Step
Interval for storing simulation data.

Note: Some systems (particles) allow position storage at every nth frame, with interpolation between. Cache Step > 1 yields smaller files but different results.

Baking

Bake
Initiates baking (Blender freezes). Cursor shows progress. Object Mode only.

Delete Bake
Marks cache temporary—removed on next edit/frame change. (Post-bake only.)

Calculate to Frame
Bakes to current frame (End frame limit applies).

Current Cache to Bake
Converts playback cache (auto-simulated physics) to permanent. Normally erased on modification; this preserves it.

Bake All Dynamics
Bakes all scene physics (all types). Multi-physics setups.

See Bake.

Delete All Bakes
Removes all scene bakes.

See Delete Bake.

Update All to Frame
Bakes all scene physics to current frame.

See Calculate To Frame.

## Shader Nodes

### Shader Nodes 

Cycles runs a slate of shader node optimizations at compile time and run-time both.
Lean on them and you can put together elaborate "Uber Shader" style node groups whose unused features cost barely any render time.

### Node Optimizations 

Step one in readying a node shader for execution is expanding every node group, as the Ungroup tool would, while tossing UI-only bits like frames and reroute nodes.

That done, it works through a handful of plain transformations; the sampling below is far from complete:

- Where every input of a node turns out constant, swap the node for the constant its evaluation yields. This covers:

RGB, Value, Mix RGB, Math, Vector Math, RGB to BW, Gamma, Bright Contrast,
Invert, Separate/Combine RGB/XYZ/HSV, Blackbody, RGB Curves, Vector Curves, Color Ramps.

- Spot Mix RGB, Math and Vector Math nodes that go no-op (Clamp off), or collapse to 0, once an addition, subtraction, multiplication, division or dot/cross product meets a known 0 or 1 input, and stand in the right link or constant.

- Drop a Mix RGB Mix (Clamp off) or Mix Shader node the moment Factor is pinned at 0 or 1, putting the matching input value or link in its place.

- Drop no-op Mix RGB nodes (barring Color Burn, Color Dodge, Lighten, or an enabled Clamp), plus Invert, RGB Curves and Vector Curves nodes, whenever their Factor is a known zero.

- Drop Emission and Background shader nodes that throw off no light, along with Add Shader nodes missing one or both input arguments.

- Drop a Bump whose Height input is constant, reaching for its Normal input or Geometry Normal in its stead. That helps when a node group input defaults to normal by passing through a no-op Bump ahead of the math.

- Swap Attribute nodes of the View Layer kind for the evaluated attribute value, which holds constant over the entire Render Layer.

- Fold several copies of one node sharing identical inputs down to a single instance.

Finally, any nodes left unconnected to the Output node, directly or indirectly, are dropped.

### Run-Time Optimizations 

A special optimization fires for Mix Shader nodes while shaders run.
Should Factor land on 0 or 1, the nodes reachable only down the mix's unused branch go unevaluated.

That can sharply cut the performance toll of folding several materials into one shader where a Color Attribute, texture, or other input plays the switch.

### Open Shading Language 

With Open Shading Language set as the rendering backend, node shaders translate into OSL code that the OSL runtime then compiles and runs.
Along the way it brings its own broad battery of optimizations to bear, at compile time and run-time alike.

Open Shading Language may optimize a Script node away when its outputs go unused or stay constant, even where its OSL shader carries side effects such as debug tracing and message passing, a result that can mislead. For that reason, to move data forward through the graph, steer clear of message passing with setmessage and getmessage; route the information explicitly through sockets instead.

## Light Linking

### Light Linking

With light linking, you can set up lights that only illuminate specific objects in the scene. Shadow linking additionally gives control over which objects block the light (cast shadows).

This adds more artistic control by breaking the laws of physics. For example, you could have a rim light that only illuminates a character in a scene (light linking) and is not blocked by any objects in the scene (shadow linking).

### Setup

- Select the light or emissive mesh object and go to the Cycles Shading panel or EEVEE Shading panel.

- Create a new light/shadow linking collection.

- Drag & drop objects or collections from the Outliner onto the list.

You can also use the Link Data menu for this: select the objects, add the light to the selection, press Ctrl - L , and choose Link Receivers/Blockers to Emitter .

Note

Emissive mesh objects only support light linking with Cycles.

Grease Pencil objects don't support light linking at all.

Multiple light objects can use the same linking collection. They can also use an existing scene collection, but in general, it's recommended to create dedicated linking collections so you can change these without affecting the scene layout.

### Include & Exclude

Light receiver/blocker objects can be set to be either included or excluded. The behavior is as follows:

- If only included objects are specified, the light only affects those objects.

- If only excluded objects are specified, the light affects all objects in the scene except those specified.

- If both included and excluded objects are specified, the light affects only included objects minus the excluded objects. This can be used to for example set a character collection to be included, and then exclude specific objects part of the character.

### Performance

Sampling for light linking is most efficient with the light tree enabled, where a specialized acceleration structure is built for light linking.

When using shadow linking, renders can be slower and trace additional rays, as direct and indirect lighting take different paths.

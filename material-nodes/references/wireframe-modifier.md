# Wireframe Modifier, Geometry Nodes Modifier, Uv Project Modifier, Uv Warp Modifier ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Wireframe Modifier; Geometry Nodes Modifier; UV Project Modifier; UV Warp Modifier; Smooth By Angle Modifier; Ocean Modifier; Particle Instance Modifier.

## Wireframe Modifier

### Wireframe Modifier

Turning a mesh into a wireframe is the job of the Wireframe modifier: it steps through every face, collects all the edges it finds, and swaps each edge out for a four-sided polygon. Bear in mind this only functions on a mesh that actually has faces. The thickness, the assigned material, and a number of further traits of the wireframe it builds can all be driven on the fly through the modifier's settings.

### Options

The Wireframe modifier.

Thickness
How thick the wireframe bars are.

Offset
A figure from -1 to 1 that decides whether the wireframes form on the inside or the outside of the original mesh.
At zero, Offset sits the wireframes centered on the original edges.

Boundary
Builds wireframes along the boundaries of mesh islands.

Replace Original
Turn this on and the source mesh gives way to the wireframe that was built.
Leave it off and the wireframe sits over the top of it instead.

Thickness

Even
Holds thickness steady by compensating at sharp corners.
This can sharpen quality in places, at the price of longer computation.

Relative
Sets each edge's thickness from how long that edge is, so longer edges come out thicker.

Crease Edges
Meant to pair with
the Subdivision modifier.
Switch it on to crease edges at their junctions, heading off broad curved intersections.

Crease Weight
Controls the crease applied at junction edges, from 0 (none) up to 1 (full).

Material Offset
Picks the named material index to use for the wireframe,
applied as an offset counted from the first material.

Warning

Wireframe thickness is only an estimate. Even Thickness does fine much of the time, yet
narrow faces can throw off unsightly spikes. When that happens, either ease the steep angles out of the geometry
or turn the Even Thickness option off.

### Vertex Group

Each weight in the chosen vertex group is multiplied against the Thickness,
which makes lower-weighted vertices come out thinner. Any vertex left out
of the group behaves as though its weight were zero.

Invert
Flips the vertex group weights so the weight actually applied becomes one minus the real weight.

Factor
The degree to which the vertex weights count toward the result.

- At 0.0 , a zero-weight vertex ends up with no thickness whatsoever.

- At 0.5 , a zero-weight vertex comes out half as thick as a full-weight one.

- At 1.0 , weights drop out of the picture and Thickness applies to every vertex alike.

Note

Even where a vertex ends up at zero thickness, a wireframe is still produced.
That leaves duplicate geometry behind, which can occasionally call for extra attention.

### Examples

Wireframes on a displaced plane.

Here the wireframes are given a second, darker material, while the displaced plane keeps the one it started with.

Vertex group weighting.

The weights of the vertex group gradually change from 0 to 1.

Wireframe and Subdivision Surface modifier.

Cube with enabled Crease Edges option. The Crease Weight is set to 0, 0.5 and 1.

## Geometry Nodes Modifier

### Geometry Nodes Modifier

What the Geometry Nodes modifier does is spin up a modifier whose behavior comes entirely from a node group you attach to it.

A new Geometry Nodes modifier with a new node group.

Objects of the mesh, curve, text, and volume kinds can all carry this modifier.

### Options

Node Group
A Node Group carrying the geometry input and output.
These are, in turn, what arrives from and gets handed to the prior and following modifier in the stack.
See Nodes for all available nodes.

Inputs
A roster of the node group's inputs, each able to hold its own value even
when several modifiers share the same group.

When the input ties into a Field socket,
a toggle appears that flips between feeding the input a single value and
drawing from an attribute on the input geometry. Drawing from an attribute lets the
value vary across every element.

Which attribute name is picked the first time a node group is used in a modifier
comes from the node group inputs panel.

Note

Whatever node the input feeds from is what sets the attribute domain and the means of reading that attribute.

### Warnings

If a node raises a warning in the node editor, that same warning surfaces here too.

You can author your own warning text with the Warning Node.

### Output Attributes

Wire a field socket into the group output node and you can mint custom Attributes
out of a Field output belonging to any node anywhere in the tree.
The attribute's domain is set in the group node's output properties.
Be aware this has no effect with Instanced Data.

Which attribute name is picked the first time a node group is used in a modifier
comes from the node group outputs panel.

This panel stays hidden unless the output node carries attribute sockets.

### Manage

Surfaces controls for handling the data held inside the node group,

You can tuck the Manage panel away by turning off Show Manage Panel
among the modifier's header options.
That governs whether the panel appears for that one specific modifier.

To keep the panel off by default on new modifiers spun up from a node group asset,
flip Show Manage Panel Geometry Nodes
in the node group's properties.

#### Bake

Bake Target
Sets where baked data goes. Individual bakes can override the choice.

Packed :

The baked data is folded into the .blend file, so no separate file is needed.

Disk :

The baked data lives in its own directory on disk.

Bake Path
The on-disk spot where baked data for
Simulation Zones
and Bake Nodes ends up.

See also

Geometry Node Baking

#### Named Attributes

Here you get a rundown of every custom named attribute the node group makes use of.
Further detail lives on the
geometry nodes inspection page.

### Move to Nodes Operator

Spins up a fresh geometry node tree named after the current one with .wrapper tacked onto the end.
Every input and output from the former modifier is shifted across into a new node group.
For the operator to work, the node group needs both a Group Input and a Group Output,
each wired to a Geometry socket.
As a result, all Output Attributes turn into Internal Dependencies driven by the
Store Named Attribute Node.
All of the modifier's "inputs" then become inputs of the freshly made node group as well.

Where this operator earns its keep is in letting a node tree be reused across other trees,
or tagged as an Asset for reuse in separate projects.

## UV Project Modifier

### UV Project Modifier

Projecting the Blender logo onto Suzanne.

Picture a slide projector and you've got the UV Project modifier. It throws a UV map out from the negative Z axis of some controller object (an empty, say) and lays that map onto the object everywhere the "light" falls.

Download an example.

### Options

The UV Project modifier.

UV Map
Picks which UV map gets modified. Defaults to the active rendering layer.

Aspect X/Y
Adjusts the image's aspect ratio. Takes effect only when a camera serves as the projector object.

Scale X/Y
Sizes the image up or down. Takes effect only when a camera serves as the projector object.

Projectors
As many as ten projector objects can be used.
Every face latches onto the nearest projector aligned with its surface normal.
The projections fire from the negative Z axis, that is straight down out of a camera or light.
Where the projector is a camera, the projection respects its perspective or orthographic setting.

Object
Names the projector object or objects.

### Usage

### General

UV Project shines for giving spotlights more variety, and likewise for laying down decals that break up repetition.

The usual move is to add an Image Texture node, pointed at the UV map
the modifier drives, into the object's material.

### Known Limitations

### Perspective Projection on Low Poly Meshes

Casting a perspective UV projection onto low poly geometry, a plane for instance, can throw up obvious artifacts.
It's a built-in shortcoming, since UV interpolation makes no allowance for perspective projection.

Subdividing the geometry can lessen the problem.

### Vertices Behind the Camera

Project geometry in a perspective view and any vertices sitting behind the camera don't get mapped correctly.
The way around it is to subdivide so the faces ahead of the camera end up with properly mapped UVs.

## UV Warp Modifier

### UV Warp Modifier

An object's UV map gets reshaped by the UV Warp modifier, drawing on either set values or a pair of objects. The aim is to hand you direct command of the object's UVs right inside the 3D Viewport, so the existing UV coordinates can be moved, rotated, and scaled using fixed values or a controller object or bone.

### Options

UV Map
Picks which UV map gets modified; left unset, it falls back to the active rendering layer.

UV Center
The point on the UV map that scaling or rotation pivots around,
where the bottom left reads (0, 0) and the top right reads (1, 1).

Axis U, V
Sets which axes carry the 3D coordinates as they're flattened into 2D.

Object From, To
The pair of objects that set the transformation. See Usage below.

Vertex Group
The vertex group serves to scale the transformation's influence on a per-vertex basis.

Invert
Flips which vertices the chosen vertex group covers, so the group instead
marks the vertices the modifier will leave undeformed.

The group's weight values are reversed by this setting.

### Transform

Offset
How far to shift the UV map.

Scale
How much to scale the UV map.

Rotation
How far to rotate the UV map.

### Usage

What warps the UVs is the mismatch in transform, that is location, rotation and scale,
separating the from object and the to object.

Should the to object carry the same transforms as the from object, the UVs stay put.

Take a UV Axis of X/Y on the modifier and object scales of (1, 1, 1): move the to object
a single unit from the from object along X, and the UVs shift on the U axis (horizontally)
across one whole UV space, the full width of the image.

## Smooth By Angle Modifier

### Smooth By Angle Modifier

Sets each mesh edge's sharpness according to the angle formed between the two faces beside it.

Note

It ships as a geometry nodes asset within the bundled "Essentials" asset library.

Tip

Shade Auto Smooth puts this modifier on an object with little effort,
while Shade Smooth or Shade Flat takes it back off.

### Options

Angle
The largest angle between face normals still counted as smooth.

Ignore Sharpness
Smooths every edge, even the ones flagged as Sharp.

## Ocean Modifier

### Ocean Modifier

What the Ocean modifier offers is a way to simulate and build a deforming ocean surface, paired with a texture that renders out the simulation data. The point of it is to model deep ocean waves and foam.

It comes across as a port of the open source Houdini Ocean Toolkit.

### Options

The Ocean modifier.

Geometry

Generate
Lays down a tiled grid of mesh that lines up exactly with the resolution of the simulation data.

When a mesh surface gets generated, the existing mesh object is wiped out entirely and replaced by the ocean grid,
which also sweeps away anything produced by earlier modifiers in the stack.
A UV channel comes along too, mapping the (0.0 to 1.0) UV space onto the simulation grid.

Repeat X, Y
Sets how many times the grid tiles across the X and Y directions.
UVs for those tiled mesh areas run on past the (0.0 to 1.0) UV space.

Displace
Keeps the existing geometry instead of swapping it out. Vertices get pushed along the local Z axis.

Resolution Viewport, Render
The chief knob trading quality against speed in the simulation engine.
It sets the resolution of the internal 2D grids the simulation builds for the 3D Viewport
or for the final render.

Those internal grids run to powers of two of the resolution value,
so a value of 16 yields simulation data sized 256×256 .
Crank the resolution up for more detail, at the cost of slower calculation.

Note

With the Generate modifier geometry option in use,
this resolution value also governs the resolution of the generated mesh surface,
matching that of the internal simulation data.

Time
The moment at which the ocean surface is evaluated.
For an animated ocean, you'll want to animate this value.
How fast the time value moves sets the pace of the wave animation.

Depth
The fixed depth of the ocean floor beneath the simulated patch.
Lower values stand in for shallower water, throwing up
higher frequency detail and smaller waves.

Size
A plain scaling factor that leaves the wave height and the simulation's behavior untouched.

Spatial Size
How wide a stretch of ocean surface gets simulated, in meters.
It also fixes the size of the generated mesh, or of the displaced area.
You can of course scale the Ocean modifier's object in Object Mode
to nudge its apparent size within your scene.

Random Seed
Change the Seed and you get a different simulation result.

Generate Normals
Works up extra normal map data.
The Ocean texture can draw on it, when mapped to Normals,
as a bump map, and it lets you generate normal map image sequences during baking.

### Waves

Scale
An overall handle on the amplitude of the waves.
It roughly stands in for how far the waves rise above or drop below zero.
Rather than merely scaling the ocean object in Z, it scales every facet of the simulation,
displacement in X and Y, plus the matching foam and normals.

Smallest Wave
A floor on how small generated waves may get.
It works rather like a low-pass filter, stripping out higher frequency wave detail.

Choppiness
How choppy the wave peaks come out.
At a choppiness of 0, the ocean surface only rises and falls along Z,
but raise it and the waves also shift sideways in X and Y, sharpening the peaks.

Wind Velocity
Wind speed in meters/second. Keep it low and the waves stay confined to smaller surface ripples.

Alignment
How strongly the wave shapes line up under the wind.
At 0, wind and waves point every which way, evenly and at random.
Push Alignment up and the wind blows more steadily in one direction,
leaving the waves looking more compressed and lined up along a single heading.

Direction
While Alignment is in use, the heading in degrees the waves line up to (measured against the local X axis).

Damping
While Alignment is in use, this sets how far inter-reflected waves are damped out.
The effect is to make the wave motion more directional, not just the wave shape.

At a Damping of 0.0, waves bounce off one another every which way; at a Damping of 1.0,
those inter-reflected waves are killed off, so only waves running with the wind remain.

### Foam

Works up extra foam data.

The Ocean texture can pull this back for use in texturing (as a mask, perhaps),
and it lets you generate foam map image sequences during baking.

Data Layer
An optional name for the vertex data layer
the Ocean Modifier uses to hold foam maps as a Color Attribute.
You need this to reach the foam data in the renderer.

Coverage
Dials how much foam blankets the waves: negative values thin it out
(leaving just the topmost peaks), positive values pile more on. Usually ranges from (-1.0 to 1.0).

Using foam Color Attributes with a named data layer.

#### Spray

Works up a map of spray direction as a Color Attribute.
That map can serve to set the velocities for spray particles.

Spray Map
The name of the Color Attribute holding the spray direction map.

Invert
Flips the spray direction map.

### Spectrum

Spectrum
Picks which wave spectrum model gets used.
Wave spectra describe how energy travels through waves at various frequencies.
That energy moves differently depending on the water's depth and the wind speed.

Turbulent Ocean
For turbulent seas carrying foam (Phillips).

Established Ocean
For a broad, established ocean stretching for miles
with wind blowing for days, long enough for the waves to settle into equilibrium (Pierson-Moskowitz method).

Established Ocean (Sharp Peaks)
Much like plain Established Ocean, except the waves keep growing over time,
sharpening the peaks ( JONSWAP and Pierson-Moskowitz method).
An additional parameter sets how sharp those peaks get.

Shallow Water
For shallow water under roughly 10 meters deep, which makes it ideal
for small lakes and ponds without strong wind (JONSWAP and TMA – Texel-Marsen-Arsloe methods).

| Turbulent Ocean. | Established Ocean. |
| Established Ocean (Sharp Peaks). | Shallow Water. |

Sharpness Peak
A contrived factor governing how sharp the wave peaks come out in
the Established Ocean (Sharp Peaks) and Shallow Water spectrum models.

Fetch
The fetch is the distance out from a lee shore, the run over which the wind holds a steady speed.
Both the Established Ocean (Sharp Peaks) and Shallow Water spectrum models draw on it.

### Bake

Rather than running the ocean data live, you can bake it out to files in a directory of your choosing. After a sim is baked, the simulator engine drops out of the picture completely and everything the modifier or texture needs is read back from the baked files.

Baking has the following advantages:

- Pulling stored data is quicker than working it out afresh.

- It opens the door to rendering ocean data in outside renderers.

- It makes richer foam maps possible.

The sim data lands as sequences of OpenEXR image maps,
one apiece for displacement, normals, and foam (where foam is set to be generated).
As these baked files load, each frame of the bake sequence gets held
in memory the moment it's read. So reaching those loaded frames again later is quick,
sparing you the cost of going back to the drive.

Because these baked files are ordinary OpenEXR's,
any other application or renderer that reads the format can open and render them too.

Cache Path
The folder where the baked EXR files are kept.
The sequences take the form disp_####.exr , normal_####.exr ,
and foam_####.exr , where #### is the four digit frame number.
Should the cache path folder not exist, it gets created.

Frame Start, End
Which frames of the simulation to bake (inclusive).
Reaching for frames outside the baked span just repeats the bake's start and end frames.

Foam Fade
Baking brings better foam handling along with it. Running live,
the ocean simulator fetches data only for the current frame.
For the foam map, that amounts to the tips of the wave crests on that one frame.
In real life, once wave interactions throw up foam,
it lingers atop the wave surface for a time as it breaks apart. Baking lets you
approximate that, gathering foam from earlier frames
so it stays sitting on the surface.

### Example

Blender built and rendered the example below;
notice the white wave crests, an effect the foam data produces.

## Particle Instance Modifier

### Particle Instance Modifier

Attach a Particle Instance modifier to an object and that object's mesh gets copied at every particle location belonging to the chosen particle system on a separate target object. So putting the modifier to use means you need at least one other object carrying a Particles System.

Since the Particle Instance modifier takes its cues from particle systems living on other objects, what it produces can look and act wildly different from case to case, hinging on how those underlying particle systems are set up. Bear that in mind any time the Particle Instance modifier's settings aren't giving you the results you were after.

### Options

The Particle Instance modifier.

Object
The target object that carries a particle system.

Particle System
Which of the target Object's particle systems this modifier acts on.

Create Instances

Regular
Switched on, the modifier copies the modified object's mesh onto the regular (parent) particles.

Children
Switched on, the modifier copies the modified object's mesh onto the child particles.

Size
Scales the instanced copies of the mesh by the particle's size attribute.
Switch it off and every copy comes out the same size as the original.

For the particle's size options, look to the particle system's Render
and Children panels.

Show

Unborn
Switched on, the modifier copies the modified object's mesh onto the unborn particles.

Alive
Switched on, the modifier copies the modified object's mesh onto the alive particles.

Dead
Switched on, the modifier copies the modified object's mesh onto the dead particles.

Amount
What fraction of the particles get used.
Lets you randomly drop particles to dial the instance count up or down.

Warning

As things stand the random algorithm only guarantees the relative amount statistically .
How many instances actually get made will stray from the theoretical figure,
governed by the Seed value of the target particle system (and the Offset value covered below, as well).

That gap stays minor when particle counts run high,
but it grows very obvious at low counts
(say the target system holds 100 particles and Amount is set to 0.1 :
you might end up with as many as 15 or as few as 5 instances rather than the 10 you'd expect).

Offset
A relative shift within the band of particles used for instancing.
Lets you keep the used particles from overlapping
when one particle system feeds several modifier instances.

Tip

To rule out overlaps entirely, set your Offset value no lower than your Amount value.

Coordinate Space

World, Local
Work in World Space, or in the Local Space of the target object the particle system sits on.

- World space means the copies of the modified mesh land at positions that depend
on where both the modified object and the target object are.

- Local space means the copies of the modified mesh land at positions that depend
on the modified object's location alone.

Axis
Picks which axis of the modified object serves as the pole axis for applying
the rotation taken from the instantiated particles.

### Create Along Paths

Out of the box, instances sit wherever the particles happen to be on the current frame. Switch on Create Along Paths and the modified object's instance bends its shape to trail the particle path (or hair strand), which frees you to choose a spot along that path independent of the current frame.

Tip

To tune the particles' path, switch to the Path visualization type
over on the Render panel of the Particle System tab.

Note

A baked particle system is required, the exceptions being Hair type and Keyed physics.

Position
Sets what share of the path the instance fills,
or where it sits on the path when the Keep Shape option is on.

Random
Sprinkles randomness onto each instance's Position value.

Rotation
Sets the rotation about the path.

Random
Sprinkles randomness onto each instance's Rotation value.

Keep Shape
Switching this on keeps the instance from deforming
and drops it onto the path at the spot given by the Position value.

### Layers

Through these fields you pick the Color Attribute to be loaded with colors derived from the particle data. Such Color Attributes can serve, for instance, inside a shader to bring variation to a material.

Index
A Color Attribute holding values drawn from the particle's index.

Value
A Color Attribute holding random per-particle values.

### Examples

Particle Instance modifier example.

In the render above, one plane mesh object carries two separate vertex groups,
and each group feeds its own independent particle system,
with every particle system tied to a distinct Particle Instance modifier.
Here the Particle Instance modifiers sit on a sphere and a cube.
See example blend-file.

Create Along Path example.

Here a lone Keyed particle runs through four points (the green planes)
along an elliptical path. The Particle Instance modifier goes onto a cylinder object,
which is then linked to that Keyed particle system.

Switch Create Along Paths on and, rather than the cylinder simply sitting where the particle is,
the cylinder mesh bends to match the path the particle traces.
How cleanly that deformation comes off depends on the geometry of the object being bent.
The cylinder here carries plenty of loop cuts down its length,
giving it points at which to flex and follow the particle path.

Create Along Paths on the Particle Instance modifier handles hair (strand) particles
just as it does keyed ones. With hair, the modifier's mesh tracks
the length and profile of the strand paths.

Note

Since strands die the instant they're generated, the Create Along Paths checkbox is
only of any use when you've also turned the Dead checkbox on.

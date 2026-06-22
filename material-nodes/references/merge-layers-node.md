# Merge Layers Node, Named Layer Selection Node, Set Grease Pencil Color Node, Set Grease Pencil Depth Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Merge Layers Node; Named Layer Selection Node; Set Grease Pencil Color Node; Set Grease Pencil Depth Node; Set Grease Pencil Softness Node; Blend Hair Curves; Displace Hair Curves; Frizz Hair Curves; Hair Curves Noise; Roll Hair Curves; Rotate Hair Curves; Shrinkwrap Hair Curves; Smooth Hair Curves; Straighten Hair Curves; Trim Hair Curves; Duplicate Hair Curves; Generate Hair Curves; Interpolate Hair Curves.

## Merge Layers Node

### Merge Layers Node

Combines multiple Grease Pencil layers into one.

**Inputs**
- Grease Pencil: Multi-layer input.
- Selection: Boolean per layer (true = include; all included by default).
- Group ID: Integer cluster identifier (visible in By Group ID Mode).

**Properties**
- Mode: Merge strategy.
  - By Name: Consolidate layers sharing identical names.
  - By Group ID: Merge layers with matching custom group ID.

**Outputs**
- Grease Pencil: Consolidated result.

Related: Merge Layers Operator.

## Named Layer Selection Node

### Named Layer Selection Node

Outputs a boolean field marking Grease Pencil layers by name match.

**Inputs**
- Name: Target layer name (must exist; no partial matching).

**Outputs**
- Selection: Boolean (true for matches, false elsewhere).

Returns false for all if no match found.

## Set Grease Pencil Color Node

### Set Grease Pencil Color Node

Applies color and opacity to Grease Pencil strokes or fills.

**Inputs**
- Grease Pencil: Standard input.
- Selection: Boolean (true = modify).
- Color: New color.
- Opacity: New transparency.

**Properties**
- Mode: Target component.
  - Stroke: Stroke points.
  - Fill: Stroke fills.

**Outputs**
- Grease Pencil: Modified geometry.

## Set Grease Pencil Depth Node

### Set Grease Pencil Depth Node

Controls depth (Z-order) rendering of Grease Pencil strokes.

**Inputs**
- Grease Pencil: Standard input.

**Properties**
- Depth Order: Ordering method.
  - 2D Layers: Order by 2D layer list (top to bottom), ignoring 3D position.
  - 3D Location: Order by 3D position.

**Outputs**
- Grease Pencil: Modified geometry.

## Set Grease Pencil Softness Node

### Set Grease Pencil Softness Node

Adjusts stroke edge fade (softness). Higher values = more transparent, blurred edges; lower = crisp.

**Inputs**
- Grease Pencil: Standard input.
- Selection: Boolean (true = modify; all by default).
- Softness: Edge fade magnitude.

**Outputs**
- Grease Pencil: Modified geometry.

Example: 0.0 (sharp) vs. 0.16 (soft).

## Blend Hair Curves

### Blend Hair Curves

Smooths hair curve shapes by averaging positions with nearby curves within a radius, reducing noise and harmonizing groom flow.

**Inputs**
- Geometry: Hair curves.
- Factor: Blend strength (0.0 = none, 1.0 = full average).
- Blend Radius: Distance threshold for neighbor detection.
- Blend Neighbors: Neighbor count cap (higher = smoother but slower).
- Preserve Length: Toggle curve length conservation during blending.

**Outputs**
- Geometry: Blended curves.

## Displace Hair Curves

### Displace Hair Curves

Displace Hair Curves shifts where strands sit or how they are shaped via a displacement vector — a procedural lever for movement, a directional push, or surface alignment. The offset resolves in object, world, or surface-normal space, per the setup.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for displacing.

Factor
How strongly the displacement reads overall. At 0.0 nothing moves; at 1.0 the displacement vector applies in full.

Shape
How the displacement factor varies from root to tip. At 0.0 the offset stays even along the strand; at 0.5 it ramps linearly from root to tip.

Object Space
The object whose transform supplies the offset's coordinate frame. Empty, and the modifier's own local space is used.

Displace Vector
Supplies both heading and length for the offset. Fields or other procedural sources can drive it.

### Surface Normal

Switch this on to push curves along a surface normal — handy for "lifting" or "pushing" strands off a mesh. The toggle sits in the header.

Surface Input Type
The route by which surface data arrives for normal sampling. A connected geometry input wins over an object input.

Object :

Sample surface normals through an object reference.

Geometry :

Read normals straight from a geometry input.

Surface
The surface object that normals are sampled from for the offset.

Surface UV Map
Which UV map gets used while reading surface normals for the offset.

Surface Normal Displacement
How far curves travel along the sampled surface normal. Sign sets direction — positive or negative.

### Outputs

Geometry
Output geometry, now carrying the displaced hair curves.

## Frizz Hair Curves

### Frizz Hair Curves

Frizz Hair Curves scatters tiny random offsets down each strand for a frizzy, rough read. It injects natural irregularity, breaking up strands that would otherwise look too clean or identical.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for frizzing.

Cumulative Offset
On, each point's offset builds on the displacement of earlier points along the strand, so bending comes out continuous and more lifelike.

Factor
The blend strength of the whole effect. At 0.0 there is no frizz; at 1.0 the full random offset lands.

Distance
Scales how large the random per-point offset gets.

Shape
How the offset strength tracks along the strand. At 0.0 the effect is uniform; at 0.5 it falls off linearly from root to tip.

Seed
The random seed behind each unique offset pattern. Move it to change the variation between strands.

Preserve Length
On, the strand keeps its starting length. Off, curves may grow or shrink a little as frizz is added.

### Outputs

Geometry
Output geometry with the frizz applied to the hair curves.

Offset Vector
A vector field recording the per-point displacement that hit each strand.

## Hair Curves Noise

### Hair Curves Noise

Hair Curves Noise deforms strands with procedural noise, yielding believable randomness or turbulence — wind buffeting, wave and curl, or faint groom imperfection.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for noise deformation.

Cumulative Offset
On, every point's offset takes cues from the points ahead of it along the strand — gentler, continuous bending instead of each point moving on its own.

Factor
The overall punch of the noise deform. At 0.0 the effect is off; at 1.0 the displacement applies fully.

Distance
A multiplier on noise amplitude. Raise it and strands stray farther from their starting shape.

Shape
How the effect changes across the strand. At 0.0 the deform is even; at 0.5 it tapers linearly from root to tip.

Scale
The noise-texture scale relative to each strand's root position. Lower values give broad, smooth waves; higher values give fine detail.

Scale along Curve
Noise frequency running along an individual strand. Higher values pack in tighter, more frequent variation down the hair.

Offset per Curve
Throws a random offset into each strand's noise pattern, so every hair varies.

Seed
The random seed that initializes the noise pattern. Shift it for different random results under the same settings.

Preserve Length
On, each curve segment holds its original length. Off, the noise may stretch or squeeze the curve a touch.

### Outputs

Geometry
Output geometry carrying the noise deform on the hair curves.

Offset Vector
A vector field marking the displacement applied at each point down the strands.

## Roll Hair Curves

### Roll Hair Curves

Roll Hair Curves winds strand tips into coils, rolling them in or out under a handful of geometric controls — good for spiral or curled looks, rolled fur, or stylized motion.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for rolling.

Factor
Overall strength of the roll. At 0.0 nothing happens; at 1.0 the full roll lands.

Subdivision
How finely each strand subdivides ahead of the deform. Higher values smooth and detail the rolls at more compute cost.

Variation Level
Works variation into the roll path by smoothing or warping it. Raise it for more natural, uneven rolls.

Roll Length
The stretch of each strand, back from the tip, that gets rolled. Larger values lengthen the coiled section.

Roll Radius
The roll's radius, fixing how tightly each strand winds.

Roll Depth
Offsets along the roll axis to stretch or compress the spiral.

Roll Taper
Sets how the roll radius shrinks toward the tip, tapering the spiral.

Retain Overall Shape
On, the roll is offset along the strand's original path so the initial flow and shape of the hair survive better.

Roll Direction
The axis the roll turns around (for example X, Y, or Z), which fixes how the curls are oriented.

Random Orientation
Randomizes roll direction to break up uniform patterns and read naturally.

Seed
The random seed for that orientation randomization. Change it to redistribute curl directions while other settings hold.

Preserve Length
On, each strand keeps its full length. Off, curves may stretch or compress slightly from the rolling.

### Outputs

Geometry
Output geometry with the rolled hair curves applied.

## Rotate Hair Curves

### Rotate Hair Curves

Rotate Hair Curves spins each strand about a chosen axis — soft twisting, spiral motion, or directional flow across a groom. It covers both light styling variation and heavier twisting deforms.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for rotating.

Factor
Overall strength of the rotation. At 0.0 nothing turns; at 1.0 the full rotation angle is reached.

Axis
The axis each strand rotates around. By default this is the tangent at the strand's root.

Angle
How much rotation is applied about the chosen axis, in radians. Positive spins one way, negative the other.

Random Offset
A random nudge to each strand's rotation angle, adding natural variation and breaking up uniformity.

Lock Ends
On, the deform preserves each strand's root-to-tip relationship, keeping the hair's overall heading and placement intact.

Seed
The random seed behind the random offsets. Move it for different rotation patterns under the same settings.

### Outputs

Geometry
Output geometry with the rotated hair curves.

## Shrinkwrap Hair Curves

### Shrinkwrap Hair Curves

Shrinkwrap Hair Curves casts strands onto a target surface, nudging them to ride a mesh's shape. Use it to conform hair to a scalp or underlying geometry, holding curves correctly placed against the surface.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for shrinkwrapping.

Surface Input Type
Picks how surface data is supplied for the shrinkwrap. A connected geometry input wins over an object input.

Object :

Sample the target surface through an object reference.

Geometry :

Read the surface straight from a geometry input.

Surface
The surface object or geometry that the projection targets.

Factor
How much the shrinkwrap pulls overall. At 0.0 the hair is untouched; at 1.0 it fully conforms to the surface.

Offset Distance
A standoff distance from the target surface. Positive pushes curves off the surface; negative draws them inward.

Above Surface
Blends the shrinkwrap for points starting above the surface, easing the transition when only parts of a strand should stick to the mesh.

Smoothing Steps
How many smoothing passes run after the shrinkwrap. More passes cut artifacts and smooth the outcome.

Lock Roots
On, each strand's root is held in place through the shrinkwrap, keeping roots pinned where they started — say, fixed to a scalp.

### Outputs

Geometry
Output geometry with curves conformed to the target surface.

## Smooth Hair Curves

### Smooth Hair Curves

Smooth Hair Curves relaxes strand shapes, evening them out by averaging control points across several passes. It cuts noise, cleans up deformation artifacts, and polishes groomed shapes after steps such as frizz or noise.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for smoothing.

Amount
Smoothing strength. Positive values smooth by averaging point positions; negative values widen the differences between points for a crumpled, distorted look.

Shape
How the smoothing reads along the strand. At 0.0 the effect is even; at 0.5 it falls off linearly from root to tip.

Iterations
How many smoothing passes run. More passes smooth further but can add processing time.

Weight
A per-point weight on how much each point feeds the smoothing. Closer to 0 means less influence there.

Lock Tips
On, the strand tips stay pinned and do not move while smoothing runs.

Preserve Length
On, each strand holds its starting length. Off, smoothing may shorten the curves a little.

### Outputs

Geometry
Output geometry with the smoothed hair curves.

## Straighten Hair Curves

### Straighten Hair Curves

Straighten Hair Curves pulls each strand's points onto a straight line from root to tip. Use it to relax curly or noisy hair, build stylized grooms, or prep curves for later deform or simulation.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for straightening.

Amount
How far each strand is straightened. At 0.0 the hair is unchanged; at 1.0 points line up fully along a straight line. Negative values overstate the strand's wiggles, crumpling or distorting it.

Shape
How the straightening reads along the strand. At 0.0 the effect is even; at 0.5 it tapers linearly from root to tip.

Preserve Length
On, each strand keeps its starting length. Off, curves may shorten or stretch a little as they straighten.

### Outputs

Geometry
Output geometry with the straightened hair curves.

## Trim Hair Curves

### Trim Hair Curves

Trim Hair Curves cuts strands down or scales them against a target length or length factor — precise overall length, varied or randomized trims, and adjustable groom density and layering.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for trimming.

Scale Uniform
On, each strand scales uniformly to the target length. Off, the trim works progressively from root to tip.

Length Factor
Multiplies original strand length by this number. At 1.0 the hair holds; at 0.5 it is halved.

Replace Length
On, the Length input takes over the strand length outright rather than scaling it by the Length Factor .

Length
Target length for the op, consulted while Replace Length is on.

Mask
A per-curve mask modulating how much the trim bites. At 0.0 that strand is left alone; at 1.0 the full effect applies.

Random Offset
Works random variation into each strand's trimmed length for more natural hair.

Pin at Parameter
Names a parameter along each strand as the pivot or anchor while trimming; the trim runs relative to it.

Seed
The random seed behind the random offset. Move it for different trim variations under the same settings.

### Outputs

Geometry
Output geometry with the trimmed or scaled hair curves.

## Duplicate Hair Curves

### Duplicate Hair Curves

Duplicate Hair Curves spins up extra copies of existing strands, scattering them around the original guides inside a set radius. Handy for boosting density, surrounding guides with secondary strands, or filling out a groom without hand-placing more guides.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in, holding the originals to duplicate.

Amount
How many duplicates each original strand spawns. Higher values raise density.

Viewport Amount
The share of Amount used for viewport display. Drop it for better viewport performance while the render result stays the same.

Radius
The farthest a duplicate can sit from its guide curve. Larger values spread the copies wider apart.

Distribution Shape
How duplicates spread inside the radius, center to outer edge. Shapes yield uniform, clustered, or edge-weighted spreads.

Tip Roundness
How rounded duplicate curves run near their tips. Higher values make the spread more circular and natural at the ends.

Even Thickness
On, density holds even across the duplicate radius. Off, it can swing with the distribution pattern.

Seed
Random seed for placing duplicates. Move it to rearrange the copies under the same settings.

### Outputs

Geometry
Output geometry with the duplicated hair curves.

Guide Index
An integer attribute holding each duplicate's original guide-curve index. Use it downstream to match colors or follow guide motion.

## Generate Hair Curves

### Generate Hair Curves

Generate Hair Curves builds brand-new strands procedurally over a mesh surface, growing them from nothing at sampled points rather than reusing existing hair. When curves should instead interpolate or trail existing guides, switch to the Interpolate Hair Curves node.

Note

This node or modifier only works with valid Surface geometry or object inputs plus a Surface UV Map .

### Inputs

Surface Input Type
Picks how surface data is supplied for interpolation.

Object :

Provide the surface through an object reference.

Geometry :

Wire a geometry input straight to the surface mesh.

Surface
The surface object generation runs on. For placement to land right, its transforms must line up with the modifier object's.

Surface UV Map
The UV map that fixes where strand roots sit on the surface mesh.

Surface Rest Position
On, the surface mesh drops to its rest pose before strands grow, keeping attachment spots consistent when the surface deforms later.

Tip

Pairing this with Deform Curves on Surface, enable Surface Rest Position when the deform node sits after this one in the stack, so generation reads pre-deformed surface positions.

Hair Length
Length of the generated strands.

Hair Material
Material handed to the generated strands.

Control Points
Control points per generated strand. More points mean smoother deforms and finer control.

### Distribution

Distribution Method
Sets how root points spread over the surface.

Random :

Drops points randomly across the surface.

Poisson Disk :

Holds a minimum gap between points via Poisson disk distribution. Distribute Points on Faces covers the specifics.

Density
Strands per unit of surface area. Crank it up for denser coverage.

Density Mask
A scalar factor modulating density over the surface, so regions carry more or fewer curves.

Mask Texture
An image texture that discards curves by pixel value, read through the Surface UV Map input. White keeps curves; black clears them.

Tip

Read once root points exist, the texture is not capped by mesh vertex density. The Density Mask input tends to be quicker; pairing both trades flexibility against efficiency.

Viewport Amount
A factor thinning viewport curve density for speed; the final render stays whole.

Seed
The distribution's random seed. Move it to reshape the pattern with everything else held.

### Outputs

Geometry
Output geometry holding the generated hair curves.

Curves
A standalone output of the generated curve data alone, ready to process or inspect.

Surface Normal
Where each strand attaches, the surface normal heading there.

## Interpolate Hair Curves

### Interpolate Hair Curves

Interpolate Hair Curves grows new strands by blending existing guide curves across a surface mesh. A few guides set the broad shape; the node fills in interpolated curves for a dense, detailed hair system.

For lighter, duplication-style setups, the Duplicate Hair Curves node is a thinner alternative that may run faster.

Note

This node or modifier only works with valid Surface geometry or object inputs plus a Surface UV Map .

### Inputs

Geometry
Geometry — the hair-curve geometry fed in, holding the guide curves to interpolate.

Surface Input Type
Picks how surface data is supplied for interpolation.

Object :

Provide the surface through an object reference.

Geometry :

Wire a geometry input straight to the surface mesh.

Surface
The surface object the interpolated curves attach to. Its transforms have to match the modifier object's.

Surface UV Map
The UV map that locates attachment spots for the interpolated curves on the surface.

Surface Rest Position
On, the surface mesh drops to its rest pose before curves attach, holding root positions steady when deformation follows.

Tip

Pairing this with Deform Curves on Surface, enable Surface Rest Position when the deform node sits after this one, so pre-deformed coordinates feed consistent interpolation.

Follow Surface Normal
On, each interpolated curve orients to the surface normal sampled where its root attaches.

Part by Mesh Islands
On, distinct mesh islands count as separate interpolation zones, blocking guides from blending across disconnected patches.

Interpolation Guides
How many nearest guide curves shape each new strand. Higher values smooth transitions but may dent performance slightly.

Distance to Guides
The farthest a guide can sit and still join the interpolation. Guides past this range have no say.

### Distribution

Distribution Method
Sets how root points for interpolated curves spread over the surface.

Random :

Scatters roots randomly across the surface.

Poisson Disk :

Uses Poisson disk sampling to keep a minimum distance between root points, giving an even, natural spread.

Density
Interpolated strands grown per unit of surface area. Higher values lift total hair density.

Density Mask
A scalar factor that locally scales curve density over the surface.

Mask Texture
An image texture deciding which surface areas grow hair, sampled via the Surface UV Map input.

Tip

Sampling runs after root points exist, so mesh resolution does not cap accuracy. The Density Mask input is usually faster; both together balance quality and performance.

Viewport Amount
A factor thinning viewport curve density for performance; final render density is untouched.

Seed
Random seed for interpolation and distribution. Move it for a different spread under the same settings.

### Outputs

Geometry
Output geometry holding the interpolated hair curves.

Guide Index
An integer attribute holding, per interpolated curve, the index of the main guide curve that generated it.

Surface Normal
The surface normal heading at each strand's root attachment point.

## Braid Hair Curves

### Braid Hair Curves

Braid Hair Curves bends existing strands into braids by clustering nearby curves around guide curves. The deform lays a multi-strand braid pattern, with knobs for radius, twist rate, strand thickness, and an optional flare or tied finish.

It targets grooming where a few curves act as braid guides and the surrounding curves wrap them into a structured braid.

### Inputs

Geometry
Geometry — the hair-curve geometry fed in for braiding.

Factor
How strongly the braid effect lands. At 0.0 the hair is untouched; at 1.0 the full braid deform applies.

Subdivision
Subdivisions applied before the deform. Higher values smooth the braids at a performance cost.

Braid Start
Sets where along each strand the braid begins, measured from the root. Lower values start it nearer the root; higher values leave more unbraided length.

Radius
The braid's overall radius. Larger values fatten the braid by pushing strands farther from its center.

Shape
Tunes the radius profile down each strand. Use it to taper or vary braid width from root to tip.

Frequency
How fast the curves twist around the braid's center; higher values wrap tighter and more often. It can vary per point along a strand, so twists tighten or loosen down the length.

### Shape Parameters

Factor Min
The braid cross-section's lower radius factor, fixing how close strands may approach the center.

Factor Max
The braid cross-section's upper radius factor, fixing how far strands may travel outward.

Thickness
How thick each hair strand sits within the braid.

Thickness Shape
How strand thickness shifts down the braid's length.

Shape Asymmetry
Works asymmetry into the strand shaping, breaking perfect radial uniformity so the braid reads more organic.

Flare Length
How long the flare runs at the braid's end, where strands loosen or fan out.

Flare Opening
That flare's radius at the braid tip. Push it higher for a wider opening.

### Hair Tie

Hair Tie Input Type
How the hair tie object — a band or wrap, say — gets supplied for instancing.

Object :

Point at the tie through an object reference.

Geometry :

Take the tie straight from a geometry input.

Hair Tie
Whatever object or geometry caps or binds the braid end as the hair tie.

Scale
Scale of the hair tie instance.

### Guide Map

Guide Index
A map saying which curve serves as central "guide" for a given braid group. Hand one in and it supersedes any existing guide_curve_index attribute; the two inputs below get bypassed.

Guide Distance
Minimum spacing between picked guides when the map is generated on the fly. Bigger numbers thin out the guides and widen each braid group.

Guide Mask
A mask gating which curves are even eligible to count as guides.

Existing Guide Map
On, lean on a guide map attribute already in place (guide_curve_index, for instance). Off, with no Guide Index handed in, the node generates one from the spacing and mask above. Prebuilding it elsewhere — a separate node or modifier — wins you finer say over which curves end up as braid guides.

### Outputs

Geometry
Output geometry with the braid deform applied.

Flare Parameter
Runs 0 to 1 to mark position within the braid's flare region. Drive shading from it, or layer on effects — tying, binding, loosening toward the tip.

Strand Index
Tags which braid strand a curve belongs to inside its braid group.

### Guide Map

Guide Index
The map of guide indices that actually drove this braid. Built fresh by the node? It exits here so later nodes can reuse it.

# Glossary (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Glossary

Definitions of terms that appear throughout Blender and this manual.

Action
Where Blender stores animation data. Animatable data-blocks don't keep their own animation data; instead they hold it in actions.

Action Safe
The screen region visible on most devices. Keep content within it so nothing gets clipped.

Active
With several items selected, the last one selected is the active item. Used where the interface only shows options for a single item at a time.

See also selection states.

Aliasing
Rendering artifacts that show up as jagged lines.

Alpha Channel
An extra image channel carrying transparency.

Straight Alpha
RGBA stored as (R, G, B, A), the RGB channels left untouched by alpha.
This is the alpha type paint programs like Photoshop or Gimp use,
and the one in common formats such as PNG, BMP, or TARGA.
So image textures and web output are usually straight alpha.

Premultiplied Alpha
RGBA stored as (R × A, G × A, B × A, A),
with alpha already folded into the RGB channels.

It's the natural output of render engines: RGB stands for the light heading
toward the viewer, and alpha for how much of the background's light is blocked.
OpenEXR works in this alpha type, so intermediate render and
composite files are commonly premultiplied.

Conversion (Straight/Premultiplied) Alpha
Converting between the two isn't trivial and can lose data,
since each type can express something the other can't, though the difference is often subtle.

Straight alpha is essentially an RGB image plus a separate alpha mask.
Where that mask is fully transparent, the RGB channels can still hold color.
Convert to premultiplied and the mask is applied, so those areas turn black and the color is lost.

Premultiplied alpha, by contrast, can describe renders that both emit light
and pass background light. A transparent fire render, for instance, might emit
light yet still let through everything behind it.
Convert that to straight alpha and the effect is gone.

Channel Packed
Each color and alpha channel gets its own stored image map.
Game engines often channel-pack to save memory and speed memory access.

Ambient Light
Light arriving from the surrounding environment as a whole.

Ambient Occlusion
A measure of how much Ambient Light a surface point is likely to catch.
A point tucked under a foot or table ends up far darker
than the top of someone's head or a tabletop.

Animation
The simulation of motion.

Anti-Aliasing
The technique for reducing Aliasing, e.g. by rendering several samples per pixel.

Armature
An Object made of Bones. Used to Rig characters, props, etc.

Asset
Curated data-blocks meant for reuse, usually held in an Asset Library.
See also Asset Libraries.

Note the word "asset" has other senses too — sometimes it's used
more loosely for any "useful thing," like images, models, materials, and more.

Asset Catalog
A container for assets, much as a directory is for files.
See also Asset Catalogs.

Asset Library
A directory on disk, registered in the preferences' list of asset libraries.
See also Asset Libraries and Current File Asset Library.

Asset Metadata
Details about an asset: its catalog,
description, author, preview, and tags. See Asset Details Region.

Attribute
A general term for per-element data held in a geometry data-block.

Axis
A reference line defining coordinates along one cardinal direction in n-dimensional space.

Axis Angle
A rotation method where X, Y, and Z give the axis definition,
while W gives the angle around that axis, in radians.

Baking
Computing a potentially costly result once and storing it
so it needn't be calculated again.

Bevel
The operation that chamfers or bevels an object's edges.

Bézier
A computer-graphics method for generating and representing curves.

Bit Depth
The base-two exponent for how many colors a single channel can hold.
A higher bit depth allows more possible colors, reducing banding and raising precision.
Yet a higher bit depth raises memory use exponentially.

Blend Modes
Color Blend Modes
Ways to blend two colors together.

See also Blend Modes on Krita docs.

Blender Session
Session
The lifespan of a Blender instance. It begins when you start an instance of Blender
and ends when you close it.

Sometimes loading a new file may count as starting a new
session. Where it does, the documentation should say so.

Bone
The building block of an Armature. It has a Head,
Tail and Roll Angle that set a local axis system and a
rotation point at the Head. See also Pose Bone.

Bone Collection
A named collection of an Armature's bones.
Bone collections help organize bones and toggle their
visibility. See Bone Collections.

Boolean
A kind of logic working in binary true/false states.

See also Boolean Modifier.

Bounding Box
The box enclosing an object's shape. It's aligned to the object's local space.

Bump Mapping
A technique that fakes slight surface-height variation from a grayscale "heightmap" texture.

BVH
Bounding Volume Hierarchy
A hierarchy of geometric objects.

See also Bounding Volume Hierarchy on Wikipedia.

Caustics
The optical effect of light concentrated by specular reflection or refraction.
Seen, for instance, when light through a glass of water casts shapes on a table, or
in the rippling pattern on a pool floor.

In rendering it refers to diffuse-reflected light paths after a glossy or refractive bounce.

See also Caustics on Wikipedia.

Child
An Object affected by its Parent.

Chroma
Chrominance
Broadly, the color part left after an image's luminance ( L or Y ) channel is separated out.
The term is used in two different contexts:

Video Systems
The general split into Y (Luminance) and C (Chrominance) channels,
where chrominance is given by U = ( Blue minus Luminance ) and V = ( Red minus Luminance ).

Matte Compositing
A point in the color gamut ringed by a mix of a chosen spectrum of its RGB
neighboring colors. That point is the Chroma key, and this key (a chosen color) is used to make
an Alpha Mask . How much gamut space this chrominance point spans is set by users
in a circular or square shape.

Chromaticities
Where the Primaries sit on the CIE 1931 xy chromaticity diagram.

Clamp
Clamping
Restricting a variable to a range. Values past either end are set
to the constant minimum or maximum of the range.

Collection
A means of organizing objects. See also Collections.

Color Gamut
Traditionally, the span of color a particular color model/space can reproduce.
It's often illustrated as a 2D figure using CIE Yxy coordinates.

Color Model
A scheme for expressing colors as numbers.

RGB
An additive system mixing three primaries — red, green, and blue — to make other colors.

HSV
Three values many find more intuitive (closer to human perception) than RGB.
Here colors are given as Hue, Saturation, and Value.

HSL
Like HSV, except the trio is Hue, Saturation, and Luminance.

YUV
A luminance-chrominance standard from analog PAL (European) broadcast video.

YCbCr
Luminance-ChannelBlue-ChannelRed component video for digital broadcast,
whose standards were updated for HDTV and is often dubbed the HDMI component-video format.

Color Space
A coordinate system where a vector encodes a color value.
Defining one fixes three things:

- The precise color of every Primary.

- The White Point.

- A transfer function (also called a tone response curve).

Which spaces are on hand depends on the active OCIO config;
the defaults are laid out in detail at
Default OpenColorIO Configuration.

Linear
A space whose channel values rise in direct proportion
to light intensity. It's the most physically faithful way to represent color, used internally
for rendering, shading, and compositing so blending and lighting come out right.

sRGB
A widely used display-referred color space on the Rec.709 Primaries with a D65 white point.
It applies a roughly 2.2 gamma transfer function to better suit human brightness perception.
sRGB is the norm for monitors, images, and the web, the usual choice for saving
or showing images outside Blender.

- Linear is the recommended choice for internal work like rendering and compositing.

- sRGB is typical for output images bound for screens and general distribution.

- Wide-gamut and high-dynamic-range pipelines may reach for other spaces, ACES among them, according to
the active OCIO config.

Concave Face
A face with one vertex sitting inside a triangle formed by the face's other vertices.

See also Convex and concave polygons
on Wikipedia.

Constraint
A way to control one Object using another's data.

Convex Face
A face where lines drawn from each vertex to every other vertex
all stay within the face. The opposite of a Concave Face.

Coplanar
Describing any set of elements all lying on the same 2D plane in 3D space.

Crease
An Edge property. Used to set the sharpness of edges on Subdivision Surface meshes.

Current File Asset Library
An asset library that isn't a disk directory but only mirrors the assets in
the current blend-file. It's available no matter where the
blend-file lives. See The Current File Asset Library.

Curve
An object defined by a line interpolated between Control Vertices.
Types include Bézier, NURBS and Poly.

Curve Segment
The stretch of a curve between two neighboring control points.

Cyclic
Usually meaning an object is closed/circular. The term is often paired with Curve.

Data User
An existing Blender object that uses either its own data or
data linked in (owned and managed by a different Blender object).

Data-Block
Data-blocks are the named items that form the base unit of
data in a blend file, and that can be linked into other blend files. Some
examples are objects, materials, armatures, meshes,
node-trees, and actions.

Dielectric Material
A material for real-world objects that are electrical insulators, such as plastic, wood, glass, etc.
In short, anything solid and non-metallic.

Diffuse Light
Even, directed light leaving a surface.
For most subjects, diffuse light is the main illumination we register.
It comes from a particular direction or place and produces shading.
Surfaces toward the light source read brighter,
those facing away darker.

Directional Light
Light with a specific direction but no location.
It appears to come from an infinitely far source, like the sun.
Surfaces facing it are lit more than those facing away, but their position is irrelevant.
A directional light lights every object in the scene, wherever they sit.

Displacement Mapping
A method for distorting vertices from an image or texture.
Like Bump Mapping, but acting on the mesh's real geometry.
So the mesh needs enough geometry to carry the image's detail.

Display Referenced
Describing an image whose Luminance channel is capped to a set range of values (usually 0-1).
It's called display referenced because a display can't show an infinite range of values.
So a Scene Referenced image must pass through a transfer function to convert
from one to the other.

DOF
Depth of Field
The span in front of and behind the subject that appears in focus. For any lens setting,
only one distance is precisely in focus, but focus drops off gradually to either
side of it, leaving a zone where the blur is tolerable. That zone is larger behind
the focus point than in front, because the light rays' angle changes more rapidly there;
they near parallel as distance grows.

Double Buffer
A way of rendering and showing content on the screen.
Blender uses two buffers (images) to draw the interface:
one buffer is displayed while drawing happens on the other.
When drawing finishes, the buffers swap.

DPI
Dots Per Inch
A physical measure of how many individual dots fit in a one-inch line span.

The term properly applies to printing, though it's loosely stretched to mean PPI just as often.

See also:

- Pixel Density support for image formats

- Pixel Density support for render output

Edge
A straight segment (line) joining two Vertices, which can form part of a Face.

Edge Loop
A chain of Edges along consecutive Quads.
It ends at a pole or a boundary. Otherwise it's cyclic.

Edge Ring
Every Edge running along a Face Loop whose two faces both belong to that loop.

Elastic
Objects able to snap back to their original shape
once all outside forces are removed.

Elasticity
How elastic versus inelastic a material is.

Empty
An Object with no Vertices, Edges, or Faces.

Euler
Euler Rotation
A rotation method applying rotations to each of the X, Y, Z axes in a set order.

Euler orders in Blender read most naturally backwards: XYZ Euler is like rotating
around Local Z with the Rotate tool in the 3D Viewport, then Local Y, then Local X .

F-Curve
A curve holding the animation values of one specific property.

Face
A mesh element defining a patch of surface. It's bounded by three or more Edges.

Face Loop
A chain of consecutive Quads. It stops at a Triangle or N-gon
(neither of which belongs to the loop), or at a boundary. Otherwise it's cyclic.

Face Normal
The normalized vector perpendicular to the plane a Face lies in. Each face has its own.

Fake User
A special Data User, a program construct
used to mark an object (a material, say) to be saved in a blend-file,
even when no Real User references it.
Objects used by no Data User aren't written into saved blend-files.

Field of View
The region in which objects are visible to the camera. See also Focal Length.

Fireflies
Path-tracing artifacts from
improbable samples that dump very high values into pixels.

FK
Forward Kinematics
Working out the motion of linked segments or bones of
a body or model in order from the parent bones down to the child bones.
With forward kinematics on a hierarchy, you can move
the upper arm and the lower arm and hand follow along.
Without it, the lower arm and hand detach from the
upper arm and move on their own in space.

See also Inverse Kinematics.

Focal Length
The distance a lens needs to focus collimated light.
It sets a lens's magnifying power. See also Field of View.

Frame Types
In video compression, a frame can be encoded by several different algorithms.
These are called picture types or frame types,
and there are three major ones: I , P , and B frames.

I‑frames
The least compressible, but they need no other video frames to decode.

P‑frames
Draw on data from earlier frames to decode, and compress better than I‑frames.

B‑frames
Use both earlier and later frames for reference to get the most compression.

Gamma
An operation for adjusting an image's brightness.

See also Gamma correction on Wikipedia.

Geodesic
Pertaining to the shortest route between two points across a curved surface.

Geometric Center
The mean of the positions of every vertex making up the object.

Gimbal
A pivoted mount that lets an object turn about one axis.

See also Gimbal on Wikipedia.

Gimbal Lock
The snag where rotation axes line up,
losing the ability to rotate on an axis (typically tied to Euler Rotation).

- See also Gimbal lock on Wikipedia.

- See also Gimbal lock on Stack Exchange.

Global Illumination
A superset of Radiosity and ray tracing. The goal is to compute every possible light interaction
in a scene, and so obtain a truly photorealistic image.
All combinations of diffuse and specular reflection and transmission must be counted.
Effects such as color bleeding and caustics must be part of a global illumination simulation.

Global Space
See World Space.

Glossy Map
See Roughness Map.

HDRI
High Dynamic Range Image
A set of techniques giving a far wider range of exposures than ordinary digital imaging.
The aim is to faithfully capture the broad span of intensity levels in real scenes,
from blazing direct sun down to the deepest shadow.

See also HDRI on Wikipedia.

Head
A subcomponent of a Bone. The bone's rotation point,
with X, Y, and Z coordinates in the Local Space of the Armature object.
Paired with the Tail to define the bone's local Y axis
in Pose Mode. The larger of the two ends when drawn as an Octahedron.

Hue
A shade of light from the color spectrum.

IK
Inverse Kinematics
Working out the motion of linked segments or bones of
a body or model in order from the child bones up to the parent bones.
With inverse kinematics on a hierarchy, you can move
the hand and the upper and lower arm follow that movement automatically.
Without it, the hand comes off the model
and moves on its own in space.

See also Forward Kinematics.

Interpolation
Computing new data between points of known value, such as Keyframes.

IOR
Index of Refraction
A property of transparent materials.
A light ray travels straight while within one volume.
But crossing from one transparent volume into another, it bends.
The bend angle follows the IOR of both volumes' materials.

Keyframe
A frame in an animated sequence built directly by the animator.
In classical animation, where every frame was drawn,
the senior artist drew these frames and left the "in between" frames to an apprentice.
Now the animator makes just a simple sequence's opening and closing frames (the keyframes),
and the software fills the gap.

Keyframing
Inserting Keyframes to build an animated sequence.

Lattice
An object built from a non-renderable 3D grid of vertices.

See also Lattice Modifier.

Light Bounces
The reflection or transmission of a light ray when it meets a material.
See also Light Paths.

Local Space
A 3D coordinate system rooted at the Object Origin for Objects,
or at the Bone's Head for Bones.

Compare to World Space.

Luminance
Light intensity, either within an image/model channel
or radiated from a surface per square unit toward a given direction.

Manifold
Manifold meshes, also called 'water-tight' meshes, enclose a closed, non-self-intersecting volume
(see also Non-manifold). In a manifold mesh, the connected
faces of a closed volume always send their normals (and surfaces) consistently to the outside
or to the inside, with no overlaps. Recalculate those normals
and they'll always point predictably (all out, or all in).
For non-closed volumes, a manifold mesh is one in which
the normals always define two distinct, non-consecutive surfaces.
A manifold mesh always defines an even number of non-overlapping surfaces.

MatCap
Short for "material capture": using an image to stand in for a full material,
lighting and reflections included.

Matte
Mask
A grayscale image for masking parts of another image in or out.
A matte serves as an Alpha Channel,
or as a mix factor when applying Color Blend Modes.

Mesh
An object made of Vertices, Edges and Faces.

Micropolygons
A polygon roughly a pixel across, or less.

MIP
Mip-map
Mip-mapping
'MIP' stands for the Latin 'multum in parvo' — 'much in little'.
A mip-map is a chain of ever-lower-resolution copies of an image,
usually halved via squared interpolation using Anti-Aliasing.
Mip-mapping is the process of computing those lower resolutions of
the same image, cutting memory use to speed display but raising
memory use for calculation and allocation. Mip-mapping is also
used to make small anti-aliased samples of an image for texturing.
The math runs on CPUs, but modern graphic processors
can be chosen for the task and are far faster.

MIS
Multiple Importance Sampling
Gauging which way light rays travel so as to sample more efficiently.

See Multiple Importance Sampling and
also Importance sampling on Wikipedia.

Modifiers
A non-destructive operation applied on top of some data.

Motion Blur
What we perceive with a rapidly moving object.
It looks blurred thanks to our persistence of vision.
Simulating motion blur makes computer animation feel more realistic.

Multisampling
Rendering several samples per pixel, for Anti-Aliasing.

N-gon
A Face containing more than four Vertices.

NDOF
3D Mouse
A general term for a 3D mouse, or any input device that supports
more degrees of freedom than a conventional 2D one, see: Touchpad.

Non-manifold
Non-manifold meshes essentially describe geometry that couldn't exist in the real world.
Such geometry is unsuited to several kinds of operation,
especially those that need a clear inside/outside
(refraction, fluids, Boolean operations, or 3D printing, among others).
In such a mesh, a non-overlapping surface (from its connected faces)
won't settle a volume's inside or outside from its normals, defining
a single surface for both sides but ending with flipped normals.
For non-closed volumes, a non-manifold mesh always
has at least one break in normal direction, either
from an inverted connected loop or from an odd number of surfaces.
Such a mesh always works out to an odd surface count.

Non-manifold geometry comes in several forms:

- Some borders and holes (edges with only one connected face), since faces have no thickness.

- Edges and vertices belonging to no face (wire).

- Edges joined to three or more faces (interior faces).

- Vertices on faces that don't adjoin (e.g. two cones sharing the apex vertex).

See also: Select Non-Manifold tool.

Nonlinear Animation
An animation technique letting the animator edit motions as wholes,
not just individual keys. It lets you combine,
mix, and blend different motions into wholly new animations.

Normal
The unit vector standing perpendicular to a surface.

Normals can be attached to vertices and
faces and varied across a surface via Normal Mapping.

See also Normals on Wikipedia.

Normal Mapping
Like Bump Mapping, but instead of a grayscale heightmap
the image's colors say which direction the normal should shift,
the three color channels nudging the normal along X, Y, or Z.
That buys more detail and finer control.

NURBS
Non-uniform Rational Basis Spline
A computer-graphics method for generating and representing curves and surfaces.

Object
A container for a type (mesh, curve, surface, meta-ball, text, armature,
lattice, empty, camera, light) carrying basic 3D transform data (the Object Origin).

Object Center
Object Origin
The reference point for placing, rotating, and scaling an Object
and for setting its Local Space coordinates.

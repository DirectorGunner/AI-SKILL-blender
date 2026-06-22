# Glossary (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Octahedron
The eight-faced shape Blender draws to represent the Bones inside an Armature.

OpenGL
Blender's rendering backend for 3D graphics, shared with countless other graphics programs, and usually run on accelerated hardware.

Operator
A one-shot action that runs and finishes the instant it is triggered. The user-interface chapter covers Operators in depth.

Overscan
A name for the case where part of a broadcast picture spills past the edges of the display and is never shown.

Panel
An interface block holding buttons. Panels fold shut to tuck their contents away and are usually free to reposition. The interface chapter covers Panels.

Parent
An Object whose behavior drives its Child objects.

Parenting
Setting up a Parent-Child link that ties two objects together.

Particle System
A method for faking soft, fuzzy phenomena that ordinary rendering struggles to recreate. Typical uses range from fire, explosions, smoke, sparks, falling leaves, clouds, fog, snow, dust, meteor tails, stars, and galaxies to abstract effects such as glowing trails or magic spells. It also drives fur, grass, and hair.

Phong
A local lighting model that lends believable depth to 3D objects by summing three contributions per surface point: diffuse, specular, and ambient. It rests on simplifying assumptions: every light is treated as a point, only the surface geometry matters, diffuse and specular are modeled locally, the specular tint matches the light's own color, and ambient stays a single global constant.

Pivot Point
The fixed location that rotation, scaling, and mirroring all turn or flip around.

Pixel
The tiniest piece of data in a 2D raster image, holding one color built from red, green, and blue channels. Should the image carry an Alpha Channel, a fourth channel rides along in each pixel.

Point Cloud
A collection of 3D-space points.

Pole
Any Vertex joined by three, five, or more edges. Stop at one, two, or four edges and it is not a pole.

Pose Bone
The pose-level data of a Bone: its location, rotation, and scale measured against the Armature's rest pose. Because this data lives on the Object, every user of the Armature can hold its own values. Constraints are stored here too.

Pose Mode
The mode for Posing, Keyframing, Weight Painting, Constraining, and Parenting an Armature's Bones.

Posing
Translating, Rotating, and Scaling an Armature's Pose Bones until a character reaches a visually appealing stance.

PPI
Pixels Per Inch
A hardware metric counting how many separate pixels fit across one inch of length.

People often swap this term with DPI.

See also

- Pixel Density support for image formats

- Pixel Density support for render output

Premultiplied Alpha
See Alpha Channel.

Primaries
Within color theory, primaries (the primary colors) are the abstract lights, expressed through an absolute model, from which a Color Space is built.

Primitive
A simple starting object you build more elaborate models on top of.

Procedural Texture
Algorithmically produced (generic) textures whose look you adjust through assorted parameters.

Projection
Two camera projections turn up most often in computer graphics.

Perspective
You build a perspective view geometrically: take a 3D scene, drop an observer at point O, then set a plane (think of a sheet of paper) in front of O and perpendicular to the line of sight, where the 2D image will land. For every scene point P, draw the line PO running through O and P. Where that PO line crosses the plane is point S, the perspective projection of P. Do this for all points P and the perspective view appears.

Orthographic
An orthographic projection keeps a viewing direction but drops the viewing point O. Now the line through P runs parallel to the viewing direction, and its crossing point S on the plane gives the orthographic projection of P. Repeat for all points P to get the orthographic view.

Proxy
In video editing a proxy is a shrunk-down stand-in for the source file, typically lower in resolution and built on an efficient codec so it loads quickly, substituting for the real image or video.

With proxies in place, editing chores like scrubbing, scrolling, and compositing speed up considerably, at the price of coarser resolution and slightly less precise results.

Quad
Quadrilateral
Quadrangle
A Face built from exactly four Vertices.

Quaternion
Quaternion Rotation
A rotation scheme described by four numbers (X, Y, Z, and W). The trio X, Y, and Z fixes an Axis while W carries an angle, yet the whole thing behaves quite unlike Axis Angle.

Geometrically, a quaternion marks a point on a unit sphere sitting in 4D space. Travel along any great circle of that sphere and you are rotating about a fixed axis, where a single loop equals two complete turns.

Radiosity
A global-illumination approach that works out how light and shadow fall when rendering images from 3D models. It is one of several Blender techniques capable of mimicking diffuse lighting.

See also
Radiosity (computer graphics)
on Wikipedia.

Random Seed
Seed
The number generators Blender relies on are pseudo-random: their output looks random, but feed them the same starting state and they replay the identical sequence every single time.

That repeatability matters for stable, reproducible results; without it a hair simulation, for instance, would shift on every re-run with no way to pin it down.

A seed encodes that starting state of the generator. Swap in a different seed and a fresh pseudo-random sequence comes out.

See also Random seed on Wikipedia.

Ray Tracing
A rendering approach that follows each light ray as it travels the scene, computing reflection, refraction, or absorption at every object the ray strikes. It beats Scanline on accuracy but pays for it heavily in speed.

Real User
A genuine Blender object that counts as a Data User, the counterpart to a Fake User, which exists only as a software bookkeeping trick.

Refraction
A wave bending its course because its speed changes. This occurs as a wave crosses from one medium, with its own Index of Refraction, into another. At the dividing line the wave shifts direction and its wavelength grows or shrinks, though its frequency holds steady.

Render
Turning 3D geometry into a finished 2D image by computation.

Resource
Outside files, images, sounds, fonts, and volume data, that you can bundle inside a blend-file.

Rest Pose
The starting transforms of one bone or an entire Armature, sometimes called the default pose. You set it in Armature Edit Mode through each bone's head, tail, and roll. Nothing added by a constraint or driver counts toward it.

RGB
A color model rooted in the classic primaries Red, Green, and Blue. Most computer displays receive RGB color straight.

Rig
The network of relationships governing how an object moves, plus the work of constructing that network.

Roll
Roll Angle
How a Bone's local X and Z axes are oriented. The local Y axis is unaffected, since the Head and Tail positions already fix it.

Rolling Shutter
On real CMOS sensors the readout happens scanline by scanline, so each scanline captures its image at a slightly different instant. That is why a horizontal camera pan can warp straight vertical lines into curves. See also Rolling Shutter on Wikipedia.

Roughness Map
A grayscale image that tells the renderer how rough or smooth a material's surface should appear. It also goes by Glossy Map.

Saturation
Saturation, or colorfulness, measures how much hue a color holds, running from desaturated grays up to vivid, intense colors.

Scanline
A rendering method that easily outpaces Ray Tracing, at the cost of a narrower effect set: reflections, refractions, motion blur, and focal blur are among those it handles less of.

Scene Referenced
An image whose Luminance channel has no imposed ceiling.

See also Display Referenced.

Shading
Reworking the color of a surface in the 3D scene according to its angle toward lights and its distance from them, producing a photorealistic look.

Smoothing
Sets how Faces take their shading. A face is either solid, rendered flat, or smooth, where the normal is interpolated across every point of the face.

Specular Light
Light bounced back cleanly, mirror-fashion. The word also names the highlights seen on shiny surfaces.

SSS
Subsurface Scattering
The way light enters a translucent object's surface, bounces around inside the material, and leaves again somewhere else. Every non-metal is translucent to a degree, and substances like marble, skin, and milk simply cannot be rendered convincingly unless subsurface scattering is modeled.

Straight Alpha
See Alpha Channel.

Subdiv
Subdivision Surface
A way to derive a smooth, high-poly surface from a low-poly mesh fed in as the starting cage.

See also
Catmull-Clark subdivision surface
on Wikipedia.

Subdividing
A method that packs extra geometry into a mesh. Splitting an edge spawns new vertices, fresh edges link the splits, and new faces form around those edges; wherever two new edges intersect, another vertex appears at the crossing.

Swing
Swing and Twist
Breaking any rotation down into two single-axis rotations in sequence: first a swing that points a chosen axis at its target along the shortest path, then a twist spinning about that same axis.

You can reach this decomposition via Driver Variables and through inputs on the Transformation constraint. The Damped Track constraint yields a swing-only rotation.

In Quaternion form the swing always shows 0 in the X/Y/Z slot matching the chosen axis, while the twist always shows 0 in the remaining two.

Tail
One end-piece of a Bone, carrying X, Y, and Z coordinates expressed in the armature object's Local Space. Paired with the Head it sets a bone's local Y axis in Pose Mode. When drawn as an Octahedron it is the narrower of the two tips.

Tangent
A line touching a surface at a single point; a tangent runs perpendicular to a Normal.

Tessellation
Covering a plane with one or several geometric shapes, a process that usually yields Micropolygons.

Texture
A description of the visual patterns on a surface, also mimicking real physical surface structure.

Texture Space
The bounding box used when Generated mapping applies a Texture onto an image.

Timecode
An encoded track on videotape or film that records each frame's number and the time it was captured. Timecodes keep media in sync across separate recording devices, covering both audio and video.

Title Safe
The portion of the frame guaranteed to show on every device. Keep text and graphics within it so nothing gets clipped.

Topology
How a mesh's Vertices, Edges, and Faces are laid out to give it shape. See Vertex, Edge, and Face.

Transform
Transformation
Location, rotation, and scale taken together. It can be stated in World Space or in Local Space.

Transformation Matrix
The matrix standing in for an item's Transformation.

Triangle
A Face made of exactly three Vertices.

UV Map
A mapping that links a mesh's surface to a 2D texture; each mesh face corresponds to a face on the texture. Sending several mesh faces to the same or overlapping spots on the texture is both possible and routine.

Value
How bright a color is, from dark to light.

Vertex
Vertices
A single location-bearing point in 3D space. Vertices sit at the ends of Edges.

Vertex Group
A named set of Vertices. Such groups help confine an operation to chosen parts of a mesh.

Voxel
The volumetric cousin of the flat 2D pixel, a small cube. Its name fuses "Volumetric" with "Pixel." Blender uses voxels to hold smoke and fire data coming out of physics simulations.

Walk Cycle
In animation, a walk cycle holds only a character's walking motion. Further along in production the character gets dropped into a setting and its remaining motions are animated.

Weight Painting
Tying Vertices to a Vertex Group at a weight somewhere between 0.0 and 1.0.

White Point
The benchmark for white light produced when every primary of a color model mixes in equal measure.

You fix a white point with a chosen set of CIE illuminants tied to a color temperature; D65, for example, maps to 6500 K light and D70 to 7000 K.

World Space
A 3D coordinate frame anchored at the world's origin. Contrast it with Local Space.

Z-buffer
A raster store of how far each surface point lies from the camera. Points ahead of the camera carry a positive Z, those behind it carry negative ones, and the resulting Z-depth map can be shown as a grayscale image.

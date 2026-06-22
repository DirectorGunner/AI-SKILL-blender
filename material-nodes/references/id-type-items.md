# Id Type Items, Image Color Depth Items, Image Color Mode Items, Image Generated Type Items ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Id Type Items; Image Color Depth Items; Image Color Mode Items; Image Generated Type Items; Image Type All Items; Linestyle Alpha Modifier Type Items; Linestyle Color Modifier Type Items; Linestyle Thickness Modifier Type Items; Mesh Delimit Mode Items; Mesh Walk Delimit Edge Ring Items; Mesh Walk Delimit Face Loop Items; Node Boolean Math Items; Node Clamp Items; Node Combsep Color Items; Node Compare Operation Items; Node Compositor Extension Items; Node Compositor Interpolation Items; Node Float To Int Items.

## Id Type Items

### Id Type Items

ACTION :

Action.

ARMATURE :

Armature.

BRUSH :

Brush.

CACHEFILE :

Cache File.

CAMERA :

Camera.

COLLECTION :

Collection.

CURVE :

Curve.

CURVES :

Curves.

FONT :

Font.

GREASEPENCIL :

Grease Pencil.

`GREASEPENCIL_V3` :

Grease Pencil v3.

IMAGE :

Image.

KEY :

Key.

LATTICE :

Lattice.

LIBRARY :

Library.

LIGHT :

Light.

`LIGHT_PROBE` :

Light Probe.

LINESTYLE :

Line Style.

MASK :

Mask.

MATERIAL :

Material.

MESH :

Mesh.

META :

Metaball.

MOVIECLIP :

Movie Clip.

NODETREE :

Node Tree.

OBJECT :

Object.

PAINTCURVE :

Paint Curve.

PALETTE :

Palette.

PARTICLE :

Particle.

POINTCLOUD :

Point Cloud.

SCENE :

Scene.

SCREEN :

Screen.

SOUND :

Sound.

SPEAKER :

Speaker.

TEXT :

Text.

TEXTURE :

Texture.

VOLUME :

Volume.

WINDOWMANAGER :

Window Manager.

WORKSPACE :

Workspace.

WORLD :

World.

## Image Color Depth Items

### Image Color Depth Items

8 :

-

8-bit color channels.

10 :

-

10-bit color channels.

12 :

-

12-bit color channels.

16 :

-

16-bit color channels.

32 :

-

32-bit color channels.

## Image Color Mode Items

### Image Color Mode Items

BW :

BW.

Saves the image as 8-bit grayscale; available only for PNG, JPEG, TGA, and TIF.

RGB :

RGB.

Writes the file using RGB (color) channels.

RGBA :

RGBA.

Writes the file with RGB channels plus an Alpha channel where the format allows it.

## Image Generated Type Items

### Image Generated Type Items

BLANK :

Blank.

Produces an empty image.

`UV_GRID` :

UV Grid.

A grid pattern useful for checking how UVs map.

`COLOR_GRID` :

Color Grid.

A refined, colored grid pattern for inspecting UV mapping.

## Image Type All Items

### Image Type All Items

AVIF :

AVIF (.avif).

Writes the result as an AVIF file.

JPEG :

JPEG (.jpg).

Writes the result as a JPEG file.

`OPEN_EXR` :

OpenEXR (.exr).

Writes the result as an OpenEXR file.

PNG :

PNG (.png).

Writes the result as a PNG file.

WEBP :

WebP (.webp).

Writes the result as a WebP file.

BMP :

Bitmap (.bmp).

Writes the result as a bitmap file.

CINEON :

Cineon (.cin).

Writes the result as a Cineon file.

DPX :

DPX (.dpx).

Writes the result as a DPX file.

IRIS :

Iris (.rgb).

Writes the result using the SGI IRIS format.

JPEG2000 :

JPEG 2000 (.jp2).

Writes the result as a JPEG 2000 file.

HDR :

Radiance HDR (.hdr).

Writes the result using the Radiance HDR format.

TARGA :

Targa (.tga).

Writes the result as a Targa file.

`TARGA_RAW` :

Targa Raw (.tga).

Writes the result as an uncompressed Targa file.

TIFF :

TIFF (.tif).

Writes the result as a TIFF file.

`OPEN_EXR_MULTILAYER` :

OpenEXR MultiLayer (.exr).

Writes the result as a multilayer OpenEXR file.

FFMPEG :

FFmpeg Video.

## Linestyle Alpha Modifier Type Items

### Linestyle Alpha Modifier Type Items

`ALONG_STROKE` :

Along Stroke.

`CREASE_ANGLE` :

Crease Angle.

`CURVATURE_3D` :

Curvature 3D.

`DISTANCE_FROM_CAMERA` :

Distance from Camera.

`DISTANCE_FROM_OBJECT` :

Distance from Object.

MATERIAL :

Material.

NOISE :

Noise.

TANGENT :

Tangent.

## Linestyle Color Modifier Type Items

### Linestyle Color Modifier Type Items

`ALONG_STROKE` :

Along Stroke.

`CREASE_ANGLE` :

Crease Angle.

`CURVATURE_3D` :

Curvature 3D.

`DISTANCE_FROM_CAMERA` :

Distance from Camera.

`DISTANCE_FROM_OBJECT` :

Distance from Object.

MATERIAL :

Material.

NOISE :

Noise.

TANGENT :

Tangent.

## Linestyle Thickness Modifier Type Items

### Linestyle Thickness Modifier Type Items

`ALONG_STROKE` :

Along Stroke.

CALLIGRAPHY :

Calligraphy.

`CREASE_ANGLE` :

Crease Angle.

`CURVATURE_3D` :

Curvature 3D.

`DISTANCE_FROM_CAMERA` :

Distance from Camera.

`DISTANCE_FROM_OBJECT` :

Distance from Object.

MATERIAL :

Material.

NOISE :

Noise.

TANGENT :

Tangent.

## Mesh Delimit Mode Items

### Mesh Delimit Mode Items

NORMAL :

Normal.

Bound the selection by the directions faces point in.

MATERIAL :

Material.

Bound the selection by the material assigned to faces.

SEAM :

Seam.

Bound the selection by marked edge seams.

SHARP :

Sharp.

Bound the selection by edges flagged sharp.

UV :

UVs.

Bound the selection by UV coordinates.

## Mesh Walk Delimit Edge Ring Items

### Mesh Walk Delimit Edge Ring Items

SEAM :

Seam.

Halt the edge-ring selection wherever a seam is met.

SHARP :

Sharp.

Halt the edge-ring selection wherever a sharp edge is met.

MATERIAL :

Material.

Halt the edge-ring selection at boundaries between materials.

NGONS :

N-gons.

Permit the edge-ring selection to cross n-gons that have an even side count.

## Mesh Walk Delimit Face Loop Items

### Mesh Walk Delimit Face Loop Items

SEAM :

Seam.

Halt the face-loop selection wherever a seam is met.

SHARP :

Sharp.

Halt the face-loop selection wherever a sharp edge is met.

MATERIAL :

Material.

Halt the face-loop selection at boundaries between materials.

## Node Boolean Math Items

### Node Boolean Math Items

AND :

And.

Outputs true only if both inputs are true.

OR :

Or.

Outputs true if one input or more is true.

NOT :

Not.

Outputs the inverse of the input.

NAND :

Not And.

Outputs true if one input or more is false.

NOR :

Nor.

Outputs true only if both inputs are false.

XNOR :

Equal.

Outputs true only if the two inputs match (exclusive nor).

XOR :

Not Equal.

Outputs true only if the two inputs differ (exclusive or).

IMPLY :

Imply.

Outputs true except in the case where the first input is true and the second is false.

NIMPLY :

Subtract.

Outputs true only when the first input is true while the second is false (not imply).

## Node Clamp Items

### Node Clamp Items

MINMAX :

Min Max.

Hold the value between the min and max bounds.

RANGE :

Range.

Hold the value between min and max, switching the two whenever min exceeds max.

## Node Combsep Color Items

### Node Combsep Color Items

RGB :

RGB.

Process color through RGB (Red, Green, Blue) channels.

HSV :

HSV.

Process color through HSV (Hue, Saturation, Value) channels.

HSL :

HSL.

Process color through HSL (Hue, Saturation, Lightness) channels.

## Node Compare Operation Items

### Node Compare Operation Items

`LESS_THAN` :

Less Than.

Outputs true when the first input falls below the second.

`LESS_EQUAL` :

Less Than or Equal.

Outputs true when the first input is below the second or matches it.

`GREATER_THAN` :

Greater Than.

Outputs true when the first input rises above the second.

`GREATER_EQUAL` :

Greater Than or Equal.

Outputs true when the first input is above the second or matches it.

EQUAL :

Equal.

Outputs true when the two inputs are roughly equal.

`NOT_EQUAL` :

Not Equal.

Outputs true when the two inputs are not roughly equal.

BRIGHTER :

Brighter.

Outputs true when the first input is the brighter of the two.

DARKER :

Darker.

Outputs true when the first input is the darker of the two.

## Node Compositor Extension Items

### Node Compositor Extension Items

CLIP :

Clip.

Pixels beyond the image edge are set to zero.

EXTEND :

Extend.

Pixels beyond the image edge take the value of the nearest border pixel.

REPEAT :

Repeat.

Pixels beyond the image edge tile the image over and over.

## Node Compositor Interpolation Items

### Node Compositor Interpolation Items

NEAREST :

Nearest.

Apply Nearest interpolation.

BILINEAR :

Bilinear.

Apply Bilinear interpolation.

BICUBIC :

Bicubic.

Apply Cubic B-Spline interpolation.

ANISOTROPIC :

Anisotropic.

Apply Anisotropic interpolation.

## Node Float To Int Items

### Node Float To Int Items

ROUND :

Round.

Snap the float to whichever whole number sits closest, rounding either up or down.

FLOOR :

Floor.

Drop the float down to the next-lower integer.

CEILING :

Ceiling.

Push the float up to the next-higher integer.

TRUNCATE :

Truncate.

Move the float toward zero to reach the nearest integer (that means floor for positives, ceiling for negatives).

## Node Geometry Curve Handle Side Items

### Node Geometry Curve Handle Side Items

LEFT :

Left.

Operate on the left-side handles.

RIGHT :

Right.

Operate on the right-side handles.

## Node Integer Math Items

### Node Integer Math Items

Functions

ADD :

Add.

A + B.

SUBTRACT :

Subtract.

A - B.

MULTIPLY :

Multiply.

A * B.

DIVIDE :

Divide.

A / B.

`MULTIPLY_ADD` :

Multiply Add.

A * B + C.

ABSOLUTE :

Absolute.

Non-negative value of A, abs(A).

NEGATE :

Negate.

-A.

POWER :

Power.

A power B, pow(A,B).

Comparison

MINIMUM :

Minimum.

The minimum value from A and B, min(A,B).

MAXIMUM :

Maximum.

The maximum value from A and B, max(A,B).

SIGN :

Sign.

Return the sign of A, sign(A).

Rounding

`DIVIDE_ROUND` :

Divide Round.

Divide, then round the quotient in the direction of zero.

`DIVIDE_FLOOR` :

Divide Floor.

Divide, then floor the quotient down to the greatest integer no larger than A.

`DIVIDE_CEIL` :

Divide Ceiling.

Divide, then take the ceiling, the least integer no smaller than A.

`FLOORED_MODULO` :

Floored Modulo.

A modulo whose period holds for operands of either sign.

MODULO :

Modulo.

The leftover from dividing A by B.

GCD :

Greatest Common Divisor.

The biggest positive integer dividing evenly into both A and B; for instance GCD(8,12) = 4.

LCM :

Least Common Multiple.

The smallest positive integer that both A and B divide into; for instance LCM(6,10) = 30.

## Node Map Range Items

### Node Map Range Items

LINEAR :

Linear.

A straight-line blend across the From Min and From Max range.

STEPPED :

Stepped Linear.

A straight-line blend across the From Min and From Max range, advanced in discrete steps.

SMOOTHSTEP :

Smooth Step.

A smooth Hermite-eased blend across the From Min and From Max range.

SMOOTHERSTEP :

Smoother Step.

An even smoother Hermite-eased blend across the From Min and From Max range.

## Node Math Items

### Node Math Items

Functions

ADD :

Add.

A + B.

SUBTRACT :

Subtract.

A - B.

MULTIPLY :

Multiply.

A * B.

DIVIDE :

Divide.

A / B.

`MULTIPLY_ADD` :

Multiply Add.

A * B + C.

POWER :

Power.

A power B.

LOGARITHM :

Logarithm.

Logarithm A base B.

SQRT :

Square Root.

Square root of A.

`INVERSE_SQRT` :

Inverse Square Root.

1 / Square root of A.

ABSOLUTE :

Absolute.

Magnitude of A.

EXPONENT :

Exponent.

exp(A).

Comparison

MINIMUM :

Minimum.

The minimum from A and B.

MAXIMUM :

Maximum.

The maximum from A and B.

`LESS_THAN` :

Less Than.

1 if A < B else 0.

`GREATER_THAN` :

Greater Than.

1 if A > B else 0.

SIGN :

Sign.

Returns the sign of A.

COMPARE :

Compare.

1 if (A == B) within tolerance C else 0.

`SMOOTH_MIN` :

Smooth Minimum.

The minimum from A and B with smoothing C.

`SMOOTH_MAX` :

Smooth Maximum.

The maximum from A and B with smoothing C.

Rounding

ROUND :

Round.

Send A to its nearest whole number, breaking a .5 fraction upward.

FLOOR :

Floor.

The greatest integer no larger than A.

CEIL :

Ceil.

The least integer no smaller than A.

TRUNC :

Truncate.

A with its fractional digits stripped off, leaving the integer part.

FRACT :

Fraction.

The fraction part of A.

MODULO :

Truncated Modulo.

The leftover of truncated division, computed via fmod(A,B).

`FLOORED_MODULO` :

Floored Modulo.

The leftover from floored division.

WRAP :

Wrap.

Wrap value to range, wrap(A,B).

SNAP :

Snap.

Snap to increment, snap(A,B).

PINGPONG :

Ping-Pong.

Folds a value back and forth, reversing direction each cycle (A,B).

Trigonometric

SINE :

Sine.

sin(A).

COSINE :

Cosine.

cos(A).

TANGENT :

Tangent.

tan(A).

ARCSINE :

Arcsine.

arcsin(A).

ARCCOSINE :

Arccosine.

arccos(A).

ARCTANGENT :

Arctangent.

arctan(A).

ARCTAN2 :

Arctan2.

The signed angle arctan(A / B).

SINH :

Hyperbolic Sine.

sinh(A).

COSH :

Hyperbolic Cosine.

cosh(A).

TANH :

Hyperbolic Tangent.

tanh(A).

Conversion

RADIANS :

To Radians.

Convert from degrees to radians.

DEGREES :

To Degrees.

Convert from radians to degrees.

## Node Socket Data Type Items

### Node Socket Data Type Items

FLOAT :

Float.

INT :

Integer.

BOOLEAN :

Boolean.

VECTOR :

Vector.

RGBA :

Color.

ROTATION :

Rotation.

MATRIX :

Matrix.

STRING :

String.

MENU :

Menu.

SHADER :

Shader.

OBJECT :

Object.

IMAGE :

Image.

GEOMETRY :

Geometry.

COLLECTION :

Collection.

TEXTURE :

Texture.

MATERIAL :

Material.

BUNDLE :

Bundle.

CLOSURE :

Closure.

FONT :

Font.

SCENE :

Scene.

TEXT :

Text.

MASK :

Mask.

SOUND :

Sound.

## Node Socket Structure Type Items

### Node Socket Structure Type Items

AUTO :

Auto.

Have a fitting structure type chosen for you from the way the socket gets used.

DYNAMIC :

Dynamic.

This socket accepts several different structure kinds.

FIELD :

Field.

This socket wants a field.

GRID :

Grid.

This socket wants a grid.

LIST :

List.

This socket wants a list.

SINGLE :

Single.

This socket wants one lone value.

## Node Socket Type Items

### Node Socket Type Items

CUSTOM :

Custom.

VALUE :

Value.

INT :

Integer.

BOOLEAN :

Boolean.

VECTOR :

Vector.

ROTATION :

Rotation.

MATRIX :

Matrix.

STRING :

String.

RGBA :

RGBA.

SHADER :

Shader.

OBJECT :

Object.

IMAGE :

Image.

GEOMETRY :

Geometry.

COLLECTION :

Collection.

TEXTURE :

Texture.

MATERIAL :

Material.

MENU :

Menu.

BUNDLE :

Bundle.

CLOSURE :

Closure.

FONT :

Font.

SCENE :

Scene.

TEXT :

Text.

MASK :

Mask.

SOUND :

Sound.

## Node Vec Math Items

### Node Vec Math Items

ADD :

Add.

A + B.

SUBTRACT :

Subtract.

A - B.

MULTIPLY :

Multiply.

Entry-wise multiply.

DIVIDE :

Divide.

Entry-wise divide.

`MULTIPLY_ADD` :

Multiply Add.

A * B + C.

`CROSS_PRODUCT` :

Cross Product.

A cross B.

PROJECT :

Project.

Project A onto B.

REFLECT :

Reflect.

Bounce A across the normal B; B need not be normalized..

REFRACT :

Refract.

Given an incident vector A, a surface normal B and an index-of-refraction ratio Ior, hand back the refracted vector R.

FACEFORWARD :

Faceforward.

Flip vector A so it faces away from surface B per its normal C; yields (dot(B, C) < 0) ? A : -A.

`DOT_PRODUCT` :

Dot Product.

A dot B.

DISTANCE :

Distance.

Distance between A and B.

LENGTH :

Length.

Length of A.

SCALE :

Scale.

A multiplied by Scale.

NORMALIZE :

Normalize.

Normalize A.

ABSOLUTE :

Absolute.

Entry-wise absolute.

POWER :

Power.

Entry-wise power.

SIGN :

Sign.

Entry-wise sign.

MINIMUM :

Minimum.

Entry-wise minimum.

MAXIMUM :

Maximum.

Entry-wise maximum.

ROUND :

Round.

Per entry, snap to the closest integer, sending a .5 fraction upward.

FLOOR :

Floor.

Entry-wise floor.

CEIL :

Ceil.

Entry-wise ceil.

FRACTION :

Fraction.

The fraction part of A entry-wise.

MODULO :

Modulo.

Entry-wise modulo using fmod(A,B).

WRAP :

Wrap.

Entry-wise wrap(A,B).

SNAP :

Snap.

Bring A down to the greatest multiple of B that does not exceed it.

SINE :

Sine.

Entry-wise sin(A).

COSINE :

Cosine.

Entry-wise cos(A).

TANGENT :

Tangent.

Entry-wise tan(A).

## Object Empty Drawtype Items

### Object Empty Drawtype Items

`PLAIN_AXES` :

Plain Axes.

ARROWS :

Arrows.

`SINGLE_ARROW` :

Single Arrow.

CIRCLE :

Circle.

CUBE :

Cube.

SPHERE :

Sphere.

CONE :

Cone.

IMAGE :

Image.

## Object Modifier Type Items

### Object Modifier Type Items

Modify

`GREASE_PENCIL_VERTEX_WEIGHT_PROXIMITY` :

Vertex Weight Proximity.

Derive vertex weights from how far points sit from an object.

Modify

`DATA_TRANSFER` :

Data Transfer.

Copy assorted data (vertex groups, UV maps, vertex colors, custom normals) across from one mesh onto another.

`MESH_CACHE` :

Mesh Cache.

Drive the mesh from an external per-frame cache of vertex transforms.

`MESH_SEQUENCE_CACHE` :

Mesh Sequence Cache.

Drive the mesh or curve from an external Alembic-format mesh cache.

`NORMAL_EDIT` :

Normal Edit.

Adjust which way the surface normals point.

`WEIGHTED_NORMAL` :

Weighted Normal.

Adjust the surface-normal directions through a weighting scheme.

`UV_PROJECT` :

UV Project.

Cast UV coordinates onto the mesh from another object's negative Z axis.

`UV_WARP` :

UV Warp.

Distort the UV map by the offset between a pair of objects.

`VERTEX_WEIGHT_EDIT` :

Vertex Weight Edit.

Edit the weights belonging to a vertex group.

`VERTEX_WEIGHT_MIX` :

Vertex Weight Mix.

Blend together the weights of a pair of vertex groups.

`VERTEX_WEIGHT_PROXIMITY` :

Vertex Weight Proximity.

Drive a vertex group's weights from proximity to a target object.

`GREASE_PENCIL_COLOR` :

Hue/Saturation.

Shift the strokes' hue, saturation, and value.

`GREASE_PENCIL_TINT` :

Tint.

Apply a color tint to the strokes.

`GREASE_PENCIL_OPACITY` :

Opacity.

Adjust how opaque the strokes are.

`GREASE_PENCIL_VERTEX_WEIGHT_ANGLE` :

Vertex Weight Angle.

Derive vertex weights from the angle of a stroke.

`GREASE_PENCIL_TIME` :

Time Offset.

Shift keyframes in time.

`GREASE_PENCIL_TEXTURE` :

Texture Mapping.

Alter the UV texture values along strokes.

Generate

ARRAY :

Array.

Lay out repeated copies of the shape at given offsets.

BEVEL :

Bevel.

Produce angled corners by inserting geometry along the mesh's edges or vertices.

BOOLEAN :

Boolean.

Bring in a second shape to cut, merge, or subtract from this one.

BUILD :

Build.

Make the object's faces appear or vanish one by one as time passes.

DECIMATE :

Decimate.

Thin out how dense the geometry is.

`EDGE_SPLIT` :

Edge Split.

Break joined faces apart along their shared edges.

NODES :

Geometry Nodes.

MASK :

Mask.

Hide vertices on the fly using a vertex group or an armature.

MIRROR :

Mirror.

Reflect across the local X, Y, and/or Z axes about the object origin.

`MESH_TO_VOLUME` :

Mesh to Volume.

MULTIRES :

Multiresolution.

Subdivide such that you can sculpt on the higher subdivision levels.

REMESH :

Remesh.

Build fresh mesh topology from the existing shape.

SCREW :

Screw.

Spin the input mesh as a profile around an axis.

SKIN :

Skin.

Grow a solid form out of vertices and edges, with each vertex radius setting the thickness.

SOLIDIFY :

Solidify.

Give the surface thickness.

SUBSURF :

Subdivision Surface.

Break faces into finer pieces for a smoother look.

TRIANGULATE :

Triangulate.

Turn every polygon into triangles.

`VOLUME_TO_MESH` :

Volume to Mesh.

WELD :

Weld.

Locate vertices nearer than dist and fuse them into one.

WIREFRAME :

Wireframe.

Turn faces into thickened edge wireframe.

`GREASE_PENCIL_ARRAY` :

Array.

Repeat strokes into an array.

`GREASE_PENCIL_BUILD` :

Build.

Grease Pencil build modifier.

`GREASE_PENCIL_LENGTH` :

Length.

Grease Pencil length modifier.

LINEART :

Line Art.

Produce Line Art out of the scene's geometry.

`GREASE_PENCIL_MIRROR` :

Mirror.

Mirror strokes to create duplicates.

`GREASE_PENCIL_MULTIPLY` :

Multiple Strokes.

Surround each original stroke with extra strokes.

`GREASE_PENCIL_SIMPLIFY` :

Simplify.

Cut down the point count to simplify a stroke.

`GREASE_PENCIL_SUBDIV` :

Subdivide.

Grease Pencil subdivide modifier.

`GREASE_PENCIL_ENVELOPE` :

Envelope.

Form an enveloping shape.

`GREASE_PENCIL_OUTLINE` :

Outline.

Turn a stroke into its outline.

Deform

ARMATURE :

Armature.

Drive the shape's deformation with an armature object.

CAST :

Cast.

Nudge the shape toward one of the preset primitives.

CURVE :

Curve.

Bend the mesh along a curve object.

DISPLACE :

Displace.

Push vertices around according to a texture.

HOOK :

Hook.

Move chosen points using a separate object.

LAPLACIANDEFORM :

Laplacian Deform.

Reshape the mesh from a set of anchor points.

LATTICE :

Lattice.

Deform following the form of a lattice object.

`MESH_DEFORM` :

Mesh Deform.

Deform via another mesh that serves as a deformation cage.

SHRINKWRAP :

Shrinkwrap.

Wrap the shape down onto another object.

`SIMPLE_DEFORM` :

Simple Deform.

Reshape by twisting, bending, tapering, or stretching.

SMOOTH :

Smooth.

Even out the mesh by softening the angles between neighboring faces.

`CORRECTIVE_SMOOTH` :

Smooth Corrective.

Smooth the mesh yet keep its volume intact.

LAPLACIANSMOOTH :

Smooth Laplacian.

Cut surface noise off a mesh while barely altering its form.

`SURFACE_DEFORM` :

Surface Deform.

Carry motion over from a second mesh.

WARP :

Warp.

Bend regions of a mesh to fresh positions with great freedom using two named objects.

WAVE :

Wave.

Send a ripple-style motion through an object's geometry.

`VOLUME_DISPLACE` :

Volume Displace.

Distort a volume using noise or another vector field.

`GREASE_PENCIL_HOOK` :

Hook.

Move stroke points around with objects.

`GREASE_PENCIL_NOISE` :

Noise.

Introduce noisy wobble into Grease Pencil strokes.

`GREASE_PENCIL_OFFSET` :

Offset.

Alter a stroke's location, rotation, or scale.

`GREASE_PENCIL_SMOOTH` :

Smooth.

Smooth out Grease Pencil strokes.

`GREASE_PENCIL_THICKNESS` :

Thickness.

Alter how thick a stroke is.

`GREASE_PENCIL_LATTICE` :

Lattice.

Deform strokes through a lattice object.

`GREASE_PENCIL_DASH` :

Dot Dash.

Produce dot-and-dash patterned strokes.

`GREASE_PENCIL_ARMATURE` :

Armature.

Move stroke points using an armature object.

`GREASE_PENCIL_SHRINKWRAP` :

Shrinkwrap.

Wrap the shape down onto another object.

Physics

CLOTH :

Cloth.

A physics sim for fabric.

COLLISION :

Collision.

For colliders taking part in physics, pick which level of the modifier stack supplies the collision surface.

`DYNAMIC_PAINT` :

Dynamic Paint.

Convert objects into paint canvases and brushes that produce color attributes, image sequences, or displacement.

EXPLODE :

Explode.

Split the mesh faces apart and have them ride along with particles.

FLUID :

Fluid.

A physics sim for fluids such as water, oil, and smoke.

OCEAN :

Ocean.

Build an animated ocean surface.

`PARTICLE_INSTANCE` :

Particle Instance.

Place a copy of the mesh at each particle.

`PARTICLE_SYSTEM` :

Particle System.

Emit particles from the shape.

`SOFT_BODY` :

Soft Body.

Simulate squishy, deformable objects.

SURFACE :

Surface.

## Object Shaderfx Type Items

### Object Shaderfx Type Items

`FX_BLUR` :

Blur.

Apply Gaussian Blur to object.

`FX_COLORIZE` :

Colorize.

Apply different tint effects.

`FX_FLIP` :

Flip.

Flip image.

`FX_GLOW` :

Glow.

Create a glow effect.

`FX_PIXEL` :

Pixelate.

Pixelate image.

`FX_RIM` :

Rim.

Add a rim to the image.

`FX_SHADOW` :

Shadow.

Create a shadow effect.

`FX_SWIRL` :

Swirl.

Create a rotation distortion.

`FX_WAVE` :

Wave Distortion.

Apply sinusoidal deformation.

## Shading Type Items

### Shading Type Items

WIREFRAME :

Wireframe.

Show just the geometry edges, with no surface shading.

SOLID :

Solid.

Show objects under flat lighting with simple surface shading.

MATERIAL :

Material Preview.

Preview materials lit by predefined environment lights.

RENDERED :

Rendered.

Preview the finished scene through the active render engine.

## Space Image Mode All Items

### Space Image Mode All Items

VIEW :

View.

Look over images or render output.

UV :

UV Editor.

Display and adjust UVs.

PAINT :

Paint.

Do 2D painting on images.

MASK :

Mask.

Display and adjust masks.

## Space Image Mode Items

### Space Image Mode Items

`IMAGE_EDITOR` :

Image Editor.

Look over images or render output.

UV :

UV Editor.

Display and adjust UVs.

## Space Type Items

### Space Type Items

EMPTY :

Empty.

General

`VIEW_3D` :

3D Viewport.

Work with objects inside a 3D environment.

`IMAGE_EDITOR` :

UV/Image Editor.

Display and adjust images along with UV Maps.

`NODE_EDITOR` :

Node Editor.

The editor for node-driven shading and compositing tools.

`SEQUENCE_EDITOR` :

Video Sequencer.

A non-linear editor for laying out and blending scenes, video, audio, and effects.

`CLIP_EDITOR` :

Movie Clip Editor.

Tools for tracking motion.

Animation

`DOPESHEET_EDITOR` :

Dope Sheet.

Tune the timing of keyframes.

`GRAPH_EDITOR` :

Graph Editor.

Work with drivers and keyframe interpolation.

`NLA_EDITOR` :

Nonlinear Animation.

Stack and blend Actions.

Scripting

`TEXT_EDITOR` :

Text Editor.

Write scripts and in-file documentation.

CONSOLE :

Python Console.

An interactive programmatic console for advanced editing and script work.

INFO :

Info.

A log of operations, warnings, and error messages.

TOPBAR :

Top Bar.

The screen-top global bar for per-window settings that apply everywhere.

STATUSBAR :

Status Bar.

The screen-bottom global bar for general status readouts.

Data

OUTLINER :

Outliner.

A survey of the scene graph and every available data-block.

PROPERTIES :

Properties.

Adjust properties of the active object and its related data-blocks.

`FILE_BROWSER` :

File Browser.

Look through files and assets.

SPREADSHEET :

Spreadsheet.

Inspect geometry data laid out in a table.

PREFERENCES :

Preferences.

Adjust persistent configuration settings.

## Stereo3D Display Items

### Stereo3D Display Items

ANAGLYPH :

Anaglyph.

Combine the left- and right-eye views as two color-filtered layers in one image (needs anaglyph glasses).

INTERLACE :

Interlace.

Combine the left- and right-eye views interlaced into one image (needs a 3D-ready monitor).

TIMESEQUENTIAL :

Time Sequential.

Alternate between eyes when rendering (page flip, requiring quad buffer support on the graphics card).

SIDEBYSIDE :

Side-by-Side.

Place the left- and right-eye views next to each other.

TOPBOTTOM :

Top-Bottom.

Stack the left- and right-eye views one over the other.

## Strip Scale Method Items

### Strip Scale Method Items

FIT :

Scale to Fit.

Keeps the whole image inside the canvas without cropping, holding the aspect ratio.

FILL :

Scale to Fill.

Covers the canvas completely, cropping as needed, while holding the aspect ratio.

STRETCH :

Stretch to Fill.

Stretches the image to the canvas and ignores the aspect ratio.

ORIGINAL :

Use Original Size.

Shows the image at its native size.

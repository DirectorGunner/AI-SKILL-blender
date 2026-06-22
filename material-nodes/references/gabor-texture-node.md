# Gabor Texture Node, Gradient Texture Node, Texture Nodes, Magic Texture Node

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Gabor Texture Node; Gradient Texture Node; Texture Nodes; Magic Texture Node.

## Gabor Texture Node

The Gabor Texture node samples Gabor noise at the supplied texture coordinates. Visually, Gabor noise reads as randomly interleaved bands whose direction and width you can steer. It can also produce omnidirectional noise much like the standard Noise Texture node, but since it costs more to compute, the Noise Texture node is usually the better pick for that purpose — see the examples for more.

Inputs:
Vector — where the Gabor noise is sampled; in the 2D case the Z component is ignored, and an unconnected socket falls back to Generated texture coordinates.
Scale — overall scale of the Gabor noise.
Frequency — how fast the noise varies across space; unlike Scale, it stretches only perpendicular to the noise's direction.
Anisotropy — how directional the noise is: 1 means fully directional, 0 means omnidirectional.
Orientation — the direction of anisotropic noise — an angle in the 2D case, a unit direction vector in the 3D case.

Properties:
Type — the kind of Gabor noise texture.
- 2D: evaluates the noise in 2D space, ignoring the input vector's Z component.
- 3D: evaluates the noise in 3D space.
Note: higher dimensions cost more render time, so prefer lower dimensions unless higher ones are necessary.

Outputs:
Value — the Gabor noise value carrying both random intensity and phase; it equals the sine of the phase multiplied by the intensity.
Phase — the noise phase, without the random intensity.
Intensity — the noise intensity, without the random phase.

Examples: varying the parameters changes the look. The noise shows interleaved bands generally aligned to one direction, and dropping Anisotropy below 1 makes the band directions more random. Frequency sets how many bands run perpendicular to the noise direction, but Scale also raises the band count globally, so try raising Scale first, since high-frequency noise can suffer from low contrast and poorly interleaved bands. Gabor noise decomposes into Phase and Intensity components, with the Gabor value computed as the sine of the phase multiplied by the intensity (the phase output is normalized to the [0, 1] range). The Phase output's advantage is that it carries no random intensities and none of the low-contrast patches seen in the value output, making it a good base for more structured textures such as sand dunes. The Intensity output mainly reveals where singularities sit in the Phase output — the spots where bands meet (shown in red in the manual's figure), which fall near zero in the Intensity output; if those spots are unwanted, hide them by multiplying with a variant of the Intensity output. Inputs can also be varied across space — for instance varying the frequency and orientation — to produce more interesting patterns.

The Gabor Texture node samples Gabor noise at the input texture coordinates. Visually, Gabor noise reads as randomly interleaved bands whose direction and width you can steer. It can also produce omnidirectional noise much like the standard Noise Texture node, but since it costs more to compute, the Noise Texture node is usually the better pick for that purpose — see the examples for more.
Note: this node is ported from shader nodes, so the manual and images reference the shader version of the node. It accepts field inputs and outputs, and when the Vector input is unconnected it carries an implicit position attribute value.

Inputs:
Vector — where the Gabor noise is evaluated; in the 2D case the Z component is ignored, and an unconnected socket falls back to Generated texture coordinates.
Scale — overall scale of the Gabor noise.
Frequency — how fast the noise changes across space; unlike Scale, it stretches only perpendicular to the noise's direction.
Anisotropy — how directional the noise is: 1 means fully directional, 0 means omnidirectional.
Orientation — the direction of anisotropic noise — an angle in the 2D case, a unit direction vector in the 3D case.

Properties:
Type — the kind of Gabor noise texture.
- 2D: evaluates the noise in 2D space, ignoring the input vector's Z component.
- 3D: evaluates the noise in 3D space.
Note: higher dimensions cost more render time, so prefer lower dimensions unless higher ones are necessary.

Outputs:
Value — the Gabor noise value carrying both random intensity and phase; it equals the sine of the phase multiplied by the intensity.
Phase — the noise phase, without the random intensity.
Intensity — the noise intensity, without the random phase.

Examples: varying the parameters changes the look. The noise shows interleaved bands generally aligned to one direction, and dropping Anisotropy below 1 makes the band directions more random. Frequency sets how many bands run perpendicular to the noise direction, but Scale also raises the band count globally, so try raising Scale first, since high-frequency noise can suffer from low contrast and poorly interleaved bands. Gabor noise decomposes into Phase and Intensity components, with the Gabor value computed as the sine of the phase multiplied by the intensity (the phase output is normalized to the [0, 1] range). The Phase output's advantage is that it carries no random intensities and none of the low-contrast patches seen in the value output, making it a good base for more structured textures such as sand dunes. The Intensity output mainly reveals where singularities sit in the Phase output — the spots where bands meet (shown in red in the manual's figure), which fall near zero in the Intensity output; if those spots are unwanted, hide them by multiplying with a variant of the Intensity output. Inputs can also be varied across space — for instance varying the frequency and orientation — to produce more interesting patterns.

### Gabor Texture Node

This node evaluates Gabor noise at the texture coordinates you feed in. Visually, Gabor noise reads as randomly interleaved bands whose orientation and width you can dial in. It can also produce omnidirectional noise the way the regular Noise Texture node does, but it costs more to compute, so the Noise Texture node is usually the smarter pick for that. The examples go into more detail.

### Inputs

Vector
Coordinates where Gabor noise gets evaluated. In the 2D case the Z component is dropped. With nothing plugged in it falls back to Generated coordinates.

Scale
Scale of the Gabor noise.

Frequency
How fast the Gabor noise varies across space. Unlike Scale, it only stretches the noise perpendicular to its direction.

Anisotropy
How directional the Gabor noise is. At 1 the noise is fully directional; at 0 it is omnidirectional.

Orientation
Which way anisotropic Gabor noise points. It is an angle in the 2D case and a unit direction vector in the 3D case.

### Properties

Type
Type of Gabor noise texture.

2D :

Evaluates the noise in 2D space; the Z component of the input vector is dropped.

3D :

Evaluates the noise in 3D space.

Note

Higher dimensions cost more render time, so stay with lower ones unless you genuinely need more.

### Outputs

Value
The Gabor noise value, carrying both a random intensity and a random phase. It equals the sine of the phase times the intensity.

Phase
The phase of the Gabor noise, which carries no random intensity.

Intensity
The intensity of the Gabor noise, which carries no random phase.

### Examples

The table below shows the node's output under various parameters. As you can see, the noise reads as interleaved bands generally pointing one way. Drop Anisotropy below 1 to make those band directions more random. Frequency sets how many bands run perpendicular to the noise direction. Scale can also globally raise the band count, so try bumping the scale first, since high-frequency noise tends to suffer from low contrast and poorly interleaved bands.

| Value output. Frequency = 2. Anisotropy = 1. | Phase output. Frequency = 2. Anisotropy = 1. | Intensity output. Frequency = 2. Anisotropy = 1. |
| Value output. Frequency = 3. Anisotropy = 1. | Phase output. Frequency = 3. Anisotropy = 1. | Intensity output. Frequency = 3. Anisotropy = 1. |
| Value output. Frequency = 2. Anisotropy = 0.7. | Phase output. Frequency = 2. Anisotropy = 0.7. | Intensity output. Frequency = 2. Anisotropy = 0.7. |

Gabor noise splits into a Phase and an Intensity part; the Gabor value emerges as sine-of-phase scaled by intensity, while the phase result is rescaled to span [0, 1].

Compute the value output from the phase and intensity outputs.

The Phase output's advantage is that it has no random intensities and none of the low-contrast patches you get in the value output, so it works as a base for more structured textures like sand dunes.

Sand dune-like structures creates using the phase output.

Mostly, the Intensity output earns its keep by pinpointing where singularities sit in the Phase output. Those singularities are the spots at which bands converge — picked out in red in the figure below — and the Intensity output dips toward zero right there. To suppress them, multiply through by some reworked form of that output.

Visualization of the areas where singularities happen.

Varying the inputs across space yields more interesting patterns.

Varying the frequency and orientation across space.

## Gradient Texture Node

The Gradient Texture node makes interpolated color and intensity values from the input vector. Input: Vector (the coordinate to sample at, defaulting to Generated coordinates if unconnected). Properties: Gradient Type — Linear (output the input X coordinate directly), Quadratic (interpolate X quadratically), Easing (a mix of quadratic and linear for a smooth gradient from X), Diagonal (average X and Y), Spherical (an inverse gradient from the input vector's length, peaking at (0, 0, 0)), Quadratic Sphere (Spherical but interpolated quadratically), and Radial (a value from the input's angle around the Z axis). Outputs: Color (the texture color) and Factor (the texture intensity).

Gradient Texture Node

Note: Ported from shader nodes; manual references shader version. Accepts field inputs/outputs. Vector defaults to implicit position.

Generates interpolated color and intensity from the input vector.

Inputs
Vector: Sample coordinate; defaults to Generated if unconnected.

Properties
Type: Gradient type.
  Linear: Outputs input X directly.
  Quadratic: Interpolates X quadratically.
  Easing: Mixes quadratic and linear for smooth gradient.
  Diagonal: Averages X and Y.
  Spherical: Inverse gradient by vector length; max at (0,0,0).
  Quadratic Sphere: Spherical with quadratic interpolation.
  Radial: Value based on angle around Z axis.

Outputs
Color: Texture color output.
Factor: Texture intensity output.

Examples: Gradient texture using object coordinates.

### Gradient Texture Node

This node produces interpolated colour and intensity values driven by the input vector.

### Inputs

Vector
Where the texture is sampled; with nothing plugged in it falls back to Generated coordinates.

### Properties

Gradient Type
Sets which kind of gradient is produced.

Linear :

Passes the input X coordinate straight out.

Quadratic :

Takes the input X coordinate and interpolates it quadratically.

Easing :

Blends quadratic and linear interpolation to ease the input X coordinate into a smooth gradient.

Diagonal :

Averages the input X and Y coordinates.

Spherical :

Builds an inverse gradient from the length of the input vector, peaking at (0, 0, 0).

Quadratic Sphere :

Like Spherical, but interpolated quadratically.

Radial :

Returns a value from the input's angle around the Z axis.

### Outputs

Color
Texture color output.

Factor
Texture intensity output.

### Examples

Gradient texture using object coordinates.

## Texture Nodes

The Texture Nodes add textures. Tip: texture nodes can produce detail at a higher frequency than the compositor can show — more evident with abrupt-change textures like brick and checker — which can cause artifacts like Moiré patterns or a loss of detail from too few sampling points.

These nodes generate procedural textures and behave just like their non-node-based counterparts.

Common Options:
Color 1/Color 2 — remap the procedural texture with these colors; they have no effect in the Magic node.

Texture Nodes

Nodes to add textures.

Tip: The detail a texture node generates can sit at a finer frequency than the geometry is able to display. The effect is clearest on textures that jump sharply, brick and checker among them. The upshot can be artifacts — Moiré-style patterns, or missing detail wherever sample points are too sparse.

## Magic Texture Node

The Magic Texture node adds a psychedelic color texture — usable for "thin film interference" by assigning a Reflection Texture Coordinate to the Vector input with a relatively high Turbulence — generating the RGB components independently with a sine formula. Inputs: Vector (the coordinate to sample at, defaulting to Generated coordinates if unconnected); Scale (the texture scale); and Distortion (the amount of distortion). Properties: Depth (the number of iterations). Outputs: Color (the texture color) and Factor (the texture intensity).

Magic Texture Node

Note: Ported from shader nodes; manual references shader version. Accepts field inputs/outputs. Vector defaults to implicit position.

Produces psychedelic color texture.

Inputs
Vector: Sample coordinate; defaults to Generated if unconnected.
Scale: Texture scale.
Distortion: Distortion amount.

Properties
Depth: Number of iterations.

Outputs
Color: Texture color output.
Factor: Texture intensity output.

Examples: Magic texture with Depth 10, Distortion 2.0.

### Magic Texture Node

This node lays down a psychedelic colour texture. Feed a Reflection Texture Coordinate into Vector and crank the Distortion fairly high and you get a "Thin Film Interference" look. Each RGB component is generated on its own from a sine formula.

### Inputs

Vector
Where the texture is sampled; with nothing plugged in it falls back to Generated coordinates.

Scale
Scale of the texture.

Distortion
Amount of distortion.

### Properties

Depth
Number of iterations.

### Outputs

Color
Texture color output.

Factor
Texture intensity output.

### Examples

Magic texture: Depth 10, Distortion 2.0.

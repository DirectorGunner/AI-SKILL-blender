# Noise Texture Node, Voronoi Texture Node

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Noise Texture Node; Voronoi Texture Node.

## Noise Texture Node

The Noise Texture node samples a fractal Perlin noise at the input texture coordinates. Use it for a single Perlin evaluation, or to stack multiple octaves (layers) of progressively finer detail.

Inputs (dynamic — they appear as the node's properties require them):
Vector — coordinate to sample the noise at; an unconnected socket defaults to Generated texture coordinates.
W — coordinate to sample the noise at.
Scale — scale of the base noise octave.
Detail — number of noise octaves; a fractional value blends (for example, a Detail of 2.5 gives a 50% blend between 2 and 3 octaves).
Roughness — shifts between a smoother pattern and a rougher one with sharper peaks.
Lacunarity — the scale gap between each pair of consecutive octaves; larger values make higher octaves larger in scale.
Offset — an offset added to each octave, setting the level at which the highest octave appears.
Gain — an extra multiplier for tuning the magnitude of octaves.
Distortion — amount of distortion.

Properties:
Dimensions — the space the noise is evaluated in.
- 1D: in 1D space at the input W.
- 2D: in 2D space at the input Vector; the Z component is ignored.
- 3D: in 3D space at the input Vector.
- 4D: in 4D space at the input Vector with the input W as the fourth dimension.
Note: higher dimensions raise render time, so keep to lower dimensions unless higher ones are necessary.
Type — the Noise texture variety, differing in how octaves combine.
- fBM: fractal Brownian motion — homogeneous and isotropic; octave values are added together.
- Multifractal: more uneven and location-dependent, akin to real terrain; octave values are multiplied together.
- Hybrid Multifractal: peaks and valleys with varying roughness, like real mountains rising from flat plains; combines octaves by both addition and multiplication.
- Ridged Multifractal: sharp peaks — takes the absolute value of the noise to carve "canyons," then flips the surface upside down.
- Hetero Terrain: like Hybrid Multifractal, a heterogeneous terrain but with the likeness of river channels.
Normalize fBM — when enabled, keeps output within 0.0 to 1.0; when disabled, the range reaches at most -(Detail + 1) to Detail + 1 (narrower if Roughness < 1).

Outputs:
Factor — value of the fractal noise.
Color — a color carrying different fractal noise in each component.

Notes: although the noise is random in nature, it follows a pattern that may not yield random values in some setups. Consider a grid of objects whose material samples a noise texture at each object's location — you might expect random values from the differing locations, but you won't get them: every object reads 0.5. The reason appears in a plot of 1D noise with zero detail and zero distortion: with a noise scale of 1, the curve always crosses the 0.5 line at whole numbers, and since the objects sit on a grid at whole-number locations they all evaluate to 0.5. In general, any discrete sampling of noise at integer multiples of the reciprocal of the noise scale lands on 0.5, and samples near those points land close to 0.5; in such cases the White Noise Texture is almost always preferable. You can also work around it by: adjusting the noise scale so it doesn't align with the evaluation domain; adding an arbitrary offset to the texture coordinates to break that alignment; or evaluating the noise in a higher dimension and tuning the extra dimension until the result looks right. A related artifact is banding — alternating bands of high- and low-contrast noise — seen, for example, on planar surfaces slightly tilted along one axis: the slight tilt makes values along the perpendicular axis change very slowly, exposing the noise's grid structure; rotating the coordinates by an arbitrary amount is the easiest fix.

Note: this node is ported from shader nodes, so the manual and images reference the shader version of the node. It accepts field inputs and outputs, and when the Vector input is unconnected it carries an implicit position attribute value.

The Noise Texture node samples a fractal Perlin noise at the input texture coordinates. Use it for a single Perlin evaluation, or to combine multiple octaves (layers) of progressively finer detail.

Inputs (dynamic — they appear as the node's properties require them):
Vector — coordinate to sample the noise at; an unconnected socket defaults to Generated texture coordinates.
W — coordinate to sample the noise at.
Scale — scale of the base noise octave.
Detail — number of noise octaves; the input's fractional part is multiplied by the magnitude of the highest octave, and more octaves mean longer render time.
Roughness — shifts between a smoother pattern and a rougher one with sharper peaks.
Lacunarity — the scale gap between each pair of consecutive octaves; larger values make higher octaves larger in scale.
Offset — an offset added to each octave, setting the level at which the highest octave appears.
Gain — an extra multiplier for tuning the magnitude of octaves.
Distortion — amount of distortion.

Properties:
Dimensions — the space the noise is evaluated in.
- 1D: in 1D space at the input W.
- 2D: in 2D space at the input Vector; the Z component is ignored.
- 3D: in 3D space at the input Vector.
- 4D: in 4D space at the input Vector with the input W as the fourth dimension.
Note: higher dimensions raise render time, so keep to lower dimensions unless higher ones are necessary.
Normalize — when enabled, keeps output values within 0.0 to 1.0; when disabled, output values land in the range -1.0 to 1.0.
Type — the Noise texture variety, differing in how octaves combine.
- FBM: fractal Brownian motion — homogeneous and isotropic; octave values are added together.
- Multifractal: more uneven and location-dependent, akin to real terrain; octave values are multiplied together.
- Hybrid Multifractal: peaks and valleys with varying roughness, like real mountains rising from flat plains; combines octaves by both addition and multiplication.
- Ridged Multifractal: sharp peaks — takes the absolute value of the noise to carve "canyons," then flips the surface upside down.
- Hetero Terrain: like Hybrid Multifractal, a heterogeneous terrain but with the likeness of river channels.

Outputs:
Factor — value of the fractal noise.
Color — a color carrying different fractal noise in each component.

Notes: although the noise is random in nature, it follows a pattern that may not yield random values in some setups. Consider a grid of objects whose material samples a noise texture at each object's location — you might expect random values from the differing locations, but you won't get them: every object reads 0.5. The reason appears in a plot of 1D noise with zero detail and zero distortion: with a noise scale of 1, the curve always crosses the 0.5 line at whole numbers, and since the objects sit on a grid at whole-number locations they all evaluate to 0.5. In general, any discrete sampling of noise at integer multiples of the reciprocal of the noise scale lands on 0.5, and samples near those points land close to 0.5; in such cases the White Noise Texture is almost always preferable. You can also work around it by: adjusting the noise scale so it doesn't align with the evaluation domain; adding an arbitrary offset to the texture coordinates to break that alignment; or evaluating the noise in a higher dimension and tuning the extra dimension until the result looks right. A related artifact is banding — alternating bands of high- and low-contrast noise — seen, for example, on planar surfaces slightly tilted along one axis: the slight tilt makes values along the perpendicular axis change very slowly, exposing the noise's grid structure; rotating the coordinates by an arbitrary amount is the easiest fix.

### Noise Texture Node

This node evaluates fractal Perlin noise at the texture coordinates you feed in. Use it for a single Perlin evaluation, or to stack several octaves (layers) of ever-finer detail.

### Inputs

Which inputs appear is dynamic: they show up only as the node properties call for them.

Vector
Where the noise is evaluated; with nothing plugged in it falls back to Generated coordinates.

W
Coordinate at which to evaluate the noise.

Scale
Scale of the base noise octave.

Detail
How many noise octaves there are. A fractional figure blends between counts — a Detail of 2.5, say, gives a 50% mix of 2 and 3 octaves.

Roughness
Slides between smoother noise and rougher noise with sharper peaks.

Lacunarity
The scale gap between any two neighbouring octaves. Larger values push higher octaves to larger scales.

Offset
An offset added to every octave; it sets the level at which the top octave shows up.

Gain
An extra multiplier for fine-tuning octave magnitude.

Distortion
Amount of distortion.

### Properties

Dimensions
Which space the noise is evaluated in.

1D :

Evaluate the noise in 1D space at the input W .

2D :

Evaluate the noise in 2D space at the input Vector . The Z component is ignored.

3D :

Evaluate the noise in 3D space at the input Vector .

4D :

Evaluate the noise in 4D space, using the input Vector plus the input W as the fourth dimension.

Note

Higher dimensions cost more render time, so stay with lower ones unless you genuinely need more.

Type
Type of Noise texture, with different ways to combine octaves.

fBM :

Fractal Brownian motion: a uniform, isotropic result. Octave values are summed.

Multifractal :

Choppier, varying by location like real terrain. Octave values are multiplied.

Hybrid Multifractal :

Peaks and valleys of varying roughness, the way real mountains lift out of flat plains. Combines octaves through both addition and multiplication.

Ridged Multifractal :

Sharp peaks. It takes the absolute value of the noise to carve "canyons", then flips the surface upside down.

Hetero Terrain :

Like Hybrid Multifractal, a heterogeneous terrain, but suggestive of river channels.

Normalize fBM
On, it keeps the output within 0.0 to 1.0. Off, the range runs at most -( Detail + 1) to Detail + 1 (narrower if Roughness < 1).

### Outputs

Factor
Value of fractal noise.

Color
Color with different fractal noise in each component.

### Examples

Noise Texture with high detail.

| fBM (fractal Brownian Motion). | Multifractal. |
| Hybrid Multifractal. | Heterogeneous Terrain. |
| Ridged Multifractal. | |

### Notes

Random though it looks, the noise follows a pattern that can fail to produce random values in some setups. Picture a grid of objects whose material samples a noise texture at each location. You would expect varied values since the locations differ, but that is not what happens.

An example configuration where the noise evaluates to a constant value.

Every object reads 0.5. To see why, look at the plot of a 1D noise texture below.

A plot of a 1D noise with zero details and zero distortion.

The horizontal line marks 0.5 and the vertical lines mark whole numbers, assuming a noise scale of 1. As shown, the noise always crosses the 0.5 line right at whole numbers. Since those objects sat on a grid at whole-number locations, they all came out 0.5 — which is the issue.

More generally, sampling the noise at integer multiples of one over the noise scale always returns 0.5, and samples near those points land close to 0.5. When that happens, reaching for the White Noise Texture is almost always the better call.

Either way, a few tricks ease the problem:

- Change the noise scale so the noise stops lining up with the evaluation domain.

- Add some arbitrary offset to the texture coordinates to break that alignment.

- Evaluate the noise at a higher dimension and tweak the extra dimension until it looks right.

| Constant value issue. | Mitigating the issue by adjusting the scale. |
| Mitigating the issue by adding an arbitrary offset. | Mitigating the issue by evaluating at a higher dimension. |

A similar thing shows up as banding in other setups, where high-contrast bands alternate with low-contrast ones. Planar surfaces tilted slightly along one axis, for instance, will show this banding.

An example configuration where the noise have a banding pattern.

It happens because the slight tilt makes values along the perpendicular axis change very slowly, which exposes the noise's underlying grid. Rotating the coordinates by an arbitrary amount is the easiest fix.

Mitigating the issue by rotating the coordinates by an arbitrary amount.

## Voronoi Texture Node

The Voronoi Texture node samples a Worley Noise at the input texture coordinates.

Inputs (dynamic — they appear as the node's properties require them):
Vector — coordinate to sample the noise at; an unconnected socket defaults to Generated texture coordinates.
W — coordinate to sample the noise at.
Scale — scale of the noise.
Detail — number of noise octaves; the input's fractional part is multiplied by the magnitude of the highest octave, and more octaves mean longer evaluation time.
Roughness — shifts between a smoother pattern and a rougher one with sharper peaks.
Lacunarity — the scale gap between each pair of consecutive octaves; larger values make higher octaves larger in scale.
Smoothness — how smooth the noise is (illustrated at 0.0, 0.25, 0.5, and 1.0).
Exponent — exponent of the Minkowski distance metric (illustrated at 0.5, 1.0, 2.0, and 32.0).
Randomness — how random the noise is (illustrated at 1.0, 0.5, 0.25, and 0.0).

Properties:
Dimensions — the space the noise is evaluated in.
- 1D: in 1D space at the input W.
- 2D: in 2D space at the input Vector; the Z component is ignored.
- 3D: in 3D space at the input Vector.
- 4D: in 4D space at the input Vector with the input W as the fourth dimension.
Higher dimensions raise render time, so keep to lower dimensions unless higher ones are necessary.
Feature — which Voronoi feature the node computes.
- F1: the distance to the closest feature point, plus its position and color.
- F2: the distance to the second-closest feature point, plus its position and color.
- Smooth F1: a smoothed version of F1.
- Distance to Edge: the distance to the edges of the Voronoi cells.
- N-Sphere Radius: the radius of the n-sphere inscribed in the Voronoi cells — that is, half the distance between the closest feature point and the feature point closest to it (handy for creating tightly packed n-spheres).
Distance Metric — the metric used to compute the texture.
- Euclidean: the Euclidean distance metric.
- Manhattan: the Manhattan distance metric.
- Chebychev: the Chebychev distance metric.
- Minkowski: the Minkowski distance metric, a generalization of the others taking an Exponent as a parameter — an exponent of one is equivalent to Manhattan, two is equivalent to Euclidean, and an infinite exponent is equivalent to Chebychev.
Normalize — when enabled, keeps output within 0.0 to 1.0; in rare cases the value may fall outside that range when Feature is F2.

Outputs:
Distance — distance.
Color — cell color (the color is arbitrary).
Position — position of the feature point.
W — position of the feature point.
Radius — n-sphere radius.

Notes: in some node configurations, especially at low Randomness, rendering artifacts can occur for the same reasons covered in the Notes section of the White Noise Texture page, and they can be fixed in the same way described there.

Examples: the difference between F1 and Smooth F1 can be used to create beveled Voronoi cells, and the node can build a hammered-metal shader.

Note: this node is ported from shader nodes, so the manual and images reference the shader version of the node. It accepts field inputs and outputs, and when the Vector input is unconnected it carries an implicit position attribute value.

The Voronoi Texture node samples a Worley Noise at the input texture coordinates.

Inputs (dynamic — they appear as the node's properties require them):
Vector — coordinate to sample the noise at; an unconnected socket defaults to Generated texture coordinates.
W — coordinate to sample the noise at.
Scale — scale of the noise.
Detail — number of noise octaves; the input's fractional part is multiplied by the magnitude of the highest octave, and more octaves mean longer evaluation time.
Roughness — shifts between a smoother pattern and a rougher one with sharper peaks.
Lacunarity — the scale gap between each pair of consecutive octaves; larger values make higher octaves larger in scale.
Smoothness — how smooth the noise is (illustrated at 0.0, 0.25, 0.5, and 1.0).
Exponent — exponent of the Minkowski distance metric (illustrated at 0.5, 1.0, 2.0, and 32.0).
Randomness — how random the noise is (illustrated at 1.0, 0.5, 0.25, and 0.0).

Properties:
Dimensions — the space the noise is evaluated in.
- 1D: in 1D space at the input W.
- 2D: in 2D space at the input Vector; the Z component is ignored.
- 3D: in 3D space at the input Vector.
- 4D: in 4D space at the input Vector with the input W as the fourth dimension.
Higher dimensions raise render time, so keep to lower dimensions unless higher ones are necessary.
Feature — which Voronoi feature the node computes.
- F1: the distance to the closest feature point, plus its position and color.
- F2: the distance to the second-closest feature point, plus its position and color.
- Smooth F1: a smoothed version of F1.
- Distance to Edge: the distance to the edges of the Voronoi cells.
- N-Sphere Radius: the radius of the n-sphere inscribed in the Voronoi cells — that is, half the distance between the closest feature point and the feature point closest to it (handy for creating tightly packed n-spheres).
Distance Metric — the metric used to compute the texture.
- Euclidean: the Euclidean distance metric.
- Manhattan: the Manhattan distance metric.
- Chebychev: the Chebychev distance metric.
- Minkowski: the Minkowski distance metric, a generalization of the others taking an Exponent as a parameter — an exponent of one is equivalent to Manhattan, two is equivalent to Euclidean, and an infinite exponent is equivalent to Chebychev.
Normalize — when enabled, keeps output within 0.0 to 1.0; in rare cases the value may fall outside that range when Feature is F2.

Outputs:
Distance — distance.
Color — cell color (the color is arbitrary).
Position — position of the feature point.
W — position of the feature point.
Radius — n-sphere radius.

Notes: in some node configurations, especially at low Randomness, rendering artifacts can occur for the same reasons covered in the Notes section of the White Noise Texture page, and they can be fixed in the same way described there.

Examples: the difference between F1 and Smooth F1 can be used to create beveled Voronoi cells, and the node can build a hammered-metal shader.

### Voronoi Texture Node

This node evaluates a Worley Noise at the texture coordinates you feed in.

### Inputs

Which inputs appear is dynamic: they show up only as the node properties call for them.

Vector
Where the noise is evaluated; with nothing plugged in it falls back to Generated coordinates.

W
Coordinate at which to evaluate the noise.

Scale
Scale of the noise.

Detail
How many noise octaves there are. The fractional part scales the magnitude of the top octave. More octaves mean longer evaluation.

Roughness
Slides between smoother noise and rougher noise with sharper peaks.

Lacunarity
The scale gap between any two neighbouring octaves. Larger values push higher octaves to larger scales.

Smoothness
The smoothness of the noise.

| Smoothness: 0.0. | Smoothness: 0.25. | Smoothness: 0.5. | Smoothness: 1.0. |
| Smoothness: 0.0. | Smoothness: 0.25. | Smoothness: 0.5. | Smoothness: 1.0. |

Exponent
Exponent of the Minkowski distance metric.

| Exponent: 0.5. | Exponent: 1.0. | Exponent: 2.0. | Exponent: 32.0. |

Randomness
The randomness of the noise.

| Randomness: 1.0. | Randomness: 0.5. | Randomness: 0.25. | Randomness: 0.0. |

### Properties

Dimensions
Which space the noise is evaluated in.

1D :

Evaluate the noise in 1D space at the input W.

2D :

Evaluate the noise in 2D space at the input Vector. The Z component is ignored.

3D :

Evaluate the noise in 3D space at the input Vector.

4D :

Evaluate the noise in 4D space, using the input Vector plus the input W as the fourth dimension.

Higher dimensions cost more render time, so stay with lower ones unless you genuinely need more.

Feature
Which Voronoi feature the node computes.

F1 :

Distance to the nearest feature point, plus that point's position and color.

| Distance. | Color. | Position. |

F2 :

Distance to the second-nearest feature point, plus that point's position and color.

| Distance. | Color. | Position. |

Smooth F1 :

A smooth version of F1.

| Distance. | Color. | Position. |

Distance to Edge :

The distance to the edges of the Voronoi cells.

| Distance. | Distance smaller than 0.05. |

N-Sphere Radius :

Radius of the n-sphere that fits inside the Voronoi cells — equivalently, half the gap separating the nearest feature point from the one nearest to it.

| The n-sphere radius can be used to create tightly packed n-spheres. | Node tree for the shader to the left. |

Distance Metric
The distance metric used to compute the texture.

Euclidean :

Use the Euclidean distance metric.

Manhattan :

Use the Manhattan distance metric.

Chebychev :

Use the Chebychev distance metric.

Minkowski :

Use the Minkowski distance metric. Minkowski generalizes the metrics above, taking an Exponent as a parameter. An exponent of one matches the Manhattan distance metric, two matches the Euclidean distance metric, and an infinite exponent matches the Chebychev distance metric.

| Minkowski Exponent: 0.5 (Minkowski 1/2). | Minkowski Exponent: 1.0 (Manhattan). | Minkowski Exponent: 2.0 (Euclidean). | Minkowski Exponent: 32.0 (approximation of Chebychev). |

Normalize
On, it keeps the output within 0.0 to 1.0. On rare occasions the value can fall outside that range when Feature is F2 .

### Outputs

Distance
Distance.

Color
Cell color. The color is arbitrary.

Position
Position of feature point.

W
Position of feature point.

Radius
N-Sphere radius.

### Notes

For some node setups, especially at low Randomness , rendering artifacts can crop up. The cause is the same one described in the Notes section of the White Noise Texture page, and the same fix described there applies.

### Examples

The difference between F1 and Smooth F1 can be used to create beveled Voronoi cells.

Creating a hammered metal shader using the Voronoi Texture node.

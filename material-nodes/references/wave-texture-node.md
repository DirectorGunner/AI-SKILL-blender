# Wave Texture Node, White Noise Texture Node, Plane Track Deform Node, Stabilize 2D Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Wave Texture Node; White Noise Texture Node; Plane Track Deform Node; Stabilize 2D Node; Track Position Node; Corner Pin Node; Crop Node; Displace Node; Flip Node; Transform Nodes; Lens Distortion Node; Map UV Node; Movie Distortion Node; Rotate Node; Scale Node; Transform Node; Translate Node.

## Wave Texture Node

The Wave Texture node makes procedural bands or rings carrying noise distortion. Inputs: Vector (the coordinate to sample at, defaulting to Generated coordinates if unconnected); Scale (overall texture scale); Distortion (the wave's distortion amount — and a hint notes that, like distorting any texture by mixing its coordinates with another, the built-in distortion uses the Noise Texture Node's Color output, replicable by centering that range on zero, multiplying by a factor proportional to Distortion / Scale, and adding it to the coordinates, with Detail, Detail Scale, and Roughness here matching the Noise Texture Node's inputs); Detail (the distortion-noise detail); Detail Scale (the distortion-noise scale); Roughness (blend between smoother and rougher with sharper peaks); and Phase Offset (the wave's position along the Bands Direction, usable as an input for more distortion control). Properties: Type (Bands or Rings); Bands/Rings Direction (the axis the bands or rings are perpendicular to — Bands allow a Diagonal axis, Rings allow Spherical to radiate from a point); and Wave Profile (the wave's look — Saw, a sawtooth, or Sine, the standard sine). Outputs: Color (the texture color) and Factor (the texture intensity).

Wave Texture Node

Note: Ported from shader nodes; manual references shader version. Accepts field inputs/outputs. Vector defaults to implicit position.

Produces procedural bands or rings with noise distortion.

Hint: Textures distort by mixing coordinates with another texture. Wave uses Noise Color for built-in distortion. To replicate: zero-center the noise value, multiply by Distortion/Scale, add to coordinates. Wave Detail/Detail Scale/Roughness match Noise Texture inputs.

Inputs
Vector: Sample coordinate; defaults to Generated if unconnected.
Scale: Overall texture scale.
Distortion: Wave distortion amount. (See Hint above for replicating the distortion effect.)
Detail: Distortion noise detail amount.
Detail Scale: Distortion noise scale.
Roughness: Smooth to sharp peaks blend.
Phase Offset: Wave position along Bands Direction. Controls distortion.

Properties
Type: Bands or Rings waves.
Bands/Rings Direction: Axis for propagation (perpendicular axis). Bands allow Diagonal. Rings allow Spherical for radial propagation.
Wave Profile: Wave appearance.
  Saw: Sawtooth profile.
  Sine: Standard sine profile.

Outputs
Color: Texture color output.
Factor: Texture intensity output.

Examples: Wave Texture.

### Wave Texture Node

This node lays down procedural bands or rings carrying noise distortion.

### Inputs

Vector
Where the texture is sampled; with nothing plugged in it falls back to Generated coordinates.

Scale
Overall texture scale.

Distortion
Amount of distortion of the wave.

Hint

As a rule, you can distort textures by mixing their coordinates with another texture. The distortion baked into this node uses the Color output of the
Noise Texture Node.

Reproduce it yourself by shifting that output's range so it centres on zero, multiplying through by a factor in proportion to Distortion / Scale , and folding what you get back into the coordinates. On this node, Detail , Detail Scale , and Roughness map straight onto the matching inputs over on the
Noise Texture Node.

Detail
Amount of distortion noise detail.

Detail Scale
Scale of distortion noise.

Roughness
Slides between smoother noise and rougher noise with sharper peaks.

Phase Offset
Position of the wave along the Bands Direction . Use it as an input for finer control over the distortion.

### Properties

Type
Bands or Rings shaped waves.

Bands/Rings Direction
The axis the bands or rings run out from, i.e. the one they sit perpendicular to. Bands add a Diagonal option, while Rings can radiate from a single point through the Spherical direction.

Wave Profile
Sets the look of the wave type.

Saw :

Uses a sawtooth profile.

Sine :

Uses the standard sine profile.

### Outputs

Color
Texture color output.

Factor
Texture intensity output.

### Examples

Wave Texture.

## White Noise Texture Node

The White Noise Texture node returns a random number from an input Seed — a number, or a 2D/3D/4D vector per the Dimensions property — ranging from zero to one. Inputs (dynamic, appearing as needed): Vector (the seed in 2D, 3D, and 4D) and W (the seed in 1D and 4D). Properties: Dimensions — 1D (W is the seed), 2D (the Vector's X and Y), 3D (the Vector), or 4D (both Vector and W). Outputs: Value (a random value) and Color (a random color). Notes: the slightest seed difference gives completely different output, so poor precision can matter a lot — mitigate by eliminating a problematic constant seed value (choose a lower dimension or multiply it by zero), adding an arbitrary value to the seed (issues often arise only at boundaries like unit boundaries), or taking the seed's absolute value (since computing has signed zeros, this unifies zero). Example: generate cell noise using the Snap vector operation with the White Noise node.

### White Noise Texture Node

**Note:** This node originates as a port from shader nodes; the manual references the shader version.
This node accepts field inputs and outputs.
The Vector input defaults to an implicit position attribute value when unconnected.

A random number generator based on an input Seed, the White Noise Texture node outputs a value between zero and one. The seed input type depends on the Dimensions setting: it can be a scalar, 2D vector, 3D vector, or 4D vector.
The output is a scalar random number in the [0, 1] range.

### Inputs

Dynamic inputs appear based on node properties.

**Vector**
Seed vector for 2D, 3D, and 4D modes.

**W**
Seed scalar for 1D and 4D modes.

### Properties

**Dimensions**
Space dimensionality for noise evaluation.

- **1D:** Uses the W input as seed.
- **2D:** Uses X and Y components of Vector as seed.
- **3D:** Uses Vector as seed.
- **4D:** Uses both Vector and W as seed.

### Outputs

**Value**
A scalar random output.

**Color**
A random color output.

### Notes

Minimal seed differences yield entirely different outputs.
Bad precision has serious implications.
Mitigation approaches:

- **Eliminate problematic seed components.** If a problematic seed is constant, reduce dimensions or multiply by zero.
- **Add an arbitrary offset.** Boundary-related issues often resolve with a constant offset.
- **Use absolute value.** Signed zero ambiguity unifies with absolute value.

| Precision loss from signed zeros on Z | Fix: remove Z axis |
| Fix: add constant offset | Fix: apply absolute value |

### White Noise Texture Node

This node hands back a random number off an input Seed. What form that seed takes — a plain number, or a 2D, 3D, or 4D vector — follows from the Dimensions property. Whatever comes back falls somewhere from zero up to one.

### Inputs

Which inputs appear is dynamic: they show up only as the node properties call for them.

Vector
Vector used as seed in 2D, 3D, and 4D dimensions.

W
Value used as seed in 1D and 4D dimensions.

### Properties

Dimensions
Which space the noise is evaluated in.

1D :

The W input is used as seed.

2D :

The X and Y components of the Vector input are used as seed.

3D :

The Vector input is used as seed.

4D :

Both the Vector input and the W input are used as seed.

### Outputs

Value
Output random value.

Color
Output random color.

### Notes

The tiniest change in seed values yields a completely different output, so poor precision can hit the result hard. Usually you can ease this by:

- Getting rid of the seed value causing trouble. Where it stays constant, drop a dimension or multiply it out by zero.

- Tacking some arbitrary number onto the seed. The trouble can show up only at particular boundaries, unit boundaries among them, so a throwaway offset often clears it.

- Folding the seed through an absolute value. Computing lets zero be signed either way, and an absolute value collapses both signed zeros into a single one.

| Precision issue due to signed zeros on the Z axis. | Mitigating the issue by eliminating the Z axis. |
| Mitigating the issue by adding an arbitrary value. | Mitigating the issue by taking the absolute value. |

### Examples

Generating cell noise using the Snap vector operation and the White Noise node.

## Plane Track Deform Node

The Plane Track Deform node replaces flat planes in footage with another image, using plane tracks from motion tracking. Before using it, make a plane track for the footage in the Movie Clip Editor. Inputs: Image (the image to place over the plane track, overriding that area in the clip). Motion Blur — whether to use blur from the plane track's motion: Samples (the samples per frame, higher being smoother but longer to render, since each virtual intermediate frame is rendered — and samples come only from the next frame, not the previous, so the blurred object appears slightly ahead) and Shutter (the time in frames the shutter is open — at 24 fps with Shutter 0.5, the 41.67 ms between frames means the shutter is open half that, 20.83 ms). Properties: Movie Clip (the clip whose plane track to use; see the Data-Block Menu), Object (the object the plane track links to), and Track (the plane track to use). Outputs: Image (the image perspective-wrapped to the plane track) and Plane (a black-and-white mask of the plane track). Examples: using the Image output is done simply with an Alpha Over node; using the Plane output mixes the clip and the image with the plane output as the factor. Image output vs original image: the Image output scales, moves, and skews the input image to the track, whereas using the original image mixed with the clip via the Plane output as factor shows the part of the image inside that mask.

## Stabilize 2D Node

The Stabilize 2D node stabilizes footage per the settings in Movie Clip Editor ‣ Properties ‣ Stabilization ‣ 2D Stabilization (see 2D Stabilization). Inputs: Image (standard color input) and Invert (reverse the stabilization — if the calculated move was up by 5 units, this moves down by 5). Sampling — Filter, how pixel values are interpolated when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, though animated motion steps one pixel at a time and can jitter), Bilinear (an average of neighboring pixels, smoother than Nearest and a good speed/quality balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients needing fine detail), and Anisotropic (interpolation adapted to the transform's direction and scale, cutting blur or aliasing when scaling at steep angles or uneven resolutions, useful for textures at oblique angles or detailed 3D projections). Properties: Movie Clip (the clip whose stabilization to use). Output: Image (standard color output).

## Track Position Node

The Track Position node feeds a tracking marker's information into the Compositor. Inputs: Mode, which marker position to output — Absolute (a marker's absolute position), Relative Start (positions relative to the track's first marker), Relative Frame (positions relative to a given Frame's markers), or Absolute Frame (absolute positions at a given Frame). Properties: Movie Clip (the clip to use; see the Data-Block Menu), Tracking Object (the camera object to read track info from), and Track (the track name to read from). Outputs: X/Y (the marker's location) and Speed (its velocity in pixels per frame, usable to fake motion blur by connecting it to the Vector Blur Node).

## Corner Pin Node

The Corner Pin node warps a plane using explicit corner values — like the Plane Track Deform node but without "plane track" data from the Movie Clip Editor. The input Image's transformation is applied before distortion, so translations introduce clipping. Inputs: Image (standard color input); Corners (four vector inputs defining the plane warp). Sampling — Interpolation, how pixel values are interpolated when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, though animated motion steps one pixel at a time and can jitter), Bilinear (an average of neighboring pixels, smoother than Nearest and a good speed/quality balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients needing fine detail), and Anisotropic (interpolation adapted to the transform's direction and scale, cutting blur or aliasing when scaling at steep angles or uneven resolutions, useful for textures at oblique angles or detailed 3D projections). Outputs: Image (the distorted image) and Plane (a black-and-white alpha mask of the plane).

## Crop Node

The Crop node crops an input image to a chosen region, either making the cropped-out area transparent or resizing the image. Inputs: Image (standard color input — if none is selected, an image of the chosen color is used, croppable in combination with another background); X and Y (the lower-left corner of the crop region); Width and Height (the region's size); and Alpha Crop (make the outside transparent rather than actually shrinking the image). Output: Image (standard color output).

## Displace Node

The Displace node shifts pixel positions by an input vector — usable to model phenomena like hot-air distortion, refraction through uneven glass, or surreal video effects. Inputs: Image (standard color input) and Displacement (the displacement map — a color input is implicitly read as a vector, with the red channel driving X displacement and green driving Y, while a grayscale image with equal channel values displaces equally in X and Y). Sampling — Interpolation, how pixel values are interpolated when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, though animated motion steps one pixel at a time and can jitter), Bilinear (an average of neighboring pixels, smoother than Nearest and a good speed/quality balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients needing fine detail), and Anisotropic (interpolation adapted to the transform's direction and scale, cutting blur or aliasing). Extension X/Y, the mode applied per axis — Clip (areas outside the image become transparent), Extend (filled with the closest boundary pixel), or Repeat (filled with image repetitions) — not available for Anisotropic interpolation. Output: Image (standard color output).

## Flip Node

The Flip node flips the input image horizontally, vertically, or both — usable to mirror an image or to blend the original with a flipped copy for symmetry effects. Inputs: Image (the standard color input to flip); Flip X (flip horizontally, left to right); and Flip Y (flip vertically, top to bottom). Output: Image (the flipped result).

## Transform Nodes

The Transform Nodes distort the image in some way, acting either uniformly across the image or varying the effect via a mask.

## Lens Distortion Node

The Lens Distortion node simulates the distortions real camera lenses produce. Inputs: Image (standard color input); Type — Radial (radial distortion for a barrel or pincushion effect) or Horizontal (horizontal distortion for a channel/color-shifting effect); Distortion (Radial — a bulging or pinching from the image center); Dispersion (simulate chromatic aberration, where wavelengths refract slightly differently into a rainbow fringe); Jitter (add jitter to the distortion — faster but noisier); and Fit (Radial — scale the image so black areas aren't visible, only for positive distortion). Output: Image (standard color output).

## Map UV Node

The Map UV node maps a texture using UV coordinates, to apply a texture to objects during compositing — and combined with the Cryptomatte Node it can apply only to specific objects. Inputs: Image (the texture to distort) and UV (the coordinates to sample the texture at, either from the UV render pass, Cycles only, or from image coordinates, in which case the Z component must be set to 1; the UV info can also be stored in a multi-layer OpenEXR). Sampling — Interpolation, how pixel values are sampled when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, though animated motion steps one pixel at a time and can jitter), Bilinear (an average of neighboring pixels, smoother than Nearest and a good speed/quality balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients needing fine detail), and Anisotropic (interpolation adapted to the transform's direction and scale, cutting blur or aliasing when scaling at steep angles or uneven resolutions). Extension X/Y, the mode per axis — Clip (outside the image becomes transparent), Extend (filled with the closest boundary pixel), or Repeat (filled with image repetitions) — not available for Anisotropic. Output: Image (the distorted texture, overlaid on the render with, e.g., the Alpha Over Node). Examples: overlay a grid on two rendered Suzanne heads by enabling the UV pass, distorting the grid with it, and combining via Alpha Over; do the same with the Blender logo using a cryptomatte to apply it to one cube only — which reveals the node's limit, since the overlaid image is just "plastered on" and isn't lit or shadowed by the scene (you can cheat by making it translucent), so it's handy for post fixes but not a replacement for rendering the image in; and a third example distorts an input image with Map UV using UV coordinates from the Image Coordinates node.

## Movie Distortion Node

Real camera lenses all produce some lens distortion, but a render has none, so the Movie Distortion node either removes distortion from movies or adds it to a render so the render blends with the clip — usually during motion tracking. Calculating distortion: first compute the clip's lens distortion by adjusting K1, K2, and K3 in Movie Clip Editor ‣ Properties ‣ Lens. Inputs: Image (standard color input) and Type — Undistort (undistort the image, usually for the raw distorted clip) or Distort (distort the image, usually for rendered images). Properties: Movie Clip (the clip whose distortion to use, useful when several clips have different distortion settings; see the Data-Block Menu). Output: Image (after distorting/undistorting). Distortion vs undistortion: both produce similar results but differ — for a clip bulging out, distort the render and leave the clip alone, since undistorting it would need extra pixel information Blender lacks; for a clip bulging in, undistort the clip and leave the render, since distorting it would need those unavailable pixels — and doing the wrong one gives weird edges.

## Rotate Node

The Rotate node rotates the input image around its center by a given angle. Inputs: Image (standard color input) and Angle (the rotation amount — positive clockwise, negative counterclockwise). Sampling — Interpolation, how pixel values are sampled when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, though animated motion steps one pixel at a time and can jitter), Bilinear (an average of neighboring pixels, smoother than Nearest and a good speed/quality balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients needing fine detail), and Anisotropic (interpolation adapted to the transform's direction and scale, cutting blur or aliasing at steep angles or uneven resolutions). Extension X/Y, the mode per axis — Clip (outside the image becomes transparent), Extend (the closest boundary pixel), or Repeat (image repetitions). Output: Image (standard color output).

Rotates an image's or texture's texture coordinates.

Inputs:
Color — the usual color input.
Turns — how many full 360° turns to rotate the coordinates about the chosen axis.
Axis — the axis to rotate the mapping about.

Properties — this node exposes no properties.

Outputs:
Color — the usual color output.

## Scale Node

The Scale node resizes an image. Inputs: Image (standard color input) and Space, the coordinate space to scale relative to — Relative (percentages of the input's dimensions), Absolute (absolute pixel sizes), Scene Size (size to the scene's final render resolution — e.g. rendering 1080p at 50% render percentage gives a 1080p image with the scene scaled down 50% and the rest alpha), or Render Size (the dimensions set in the Render panel). Frame Type (Render Size — how the image fits the camera frame): Stretch (distort to fit the render size), Fit (scale until the larger axis fits), or Crop (cut to the render size's aspect ratio). X, Y (axis scale, only with Space Relative or Absolute). Sampling — Interpolation, how pixel values are sampled when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, with single-pixel jitter in animation), Bilinear (an average of neighboring pixels, smoother and a good balance), Bicubic (a weighted average over a larger neighborhood for even smoother results, ideal for photos or gradients), and Anisotropic (adapted to the transform's direction and scale, cutting blur or aliasing at steep angles or uneven resolutions). Extension X/Y per axis — Clip (transparent outside), Extend (closest boundary pixel), or Repeat (image repetitions). Output: Image (standard color output). Examples: X 0.5, Y 0.5 halves the width and height — and since most nodes output an image the size of their top image input, use this node to scale a second image up to match a first before uniformly combining them.

Scales an image's or texture's texture coordinates.

Inputs:
Color — the usual color input.
Scale — how much to scale the coordinates along each of the three axes.

Properties — this node exposes no properties.

Outputs:
Color — the usual color output.

## Transform Node

The Transform node combines the Scale, Translate, and Rotate nodes. Inputs: Image (standard color input); X, Y (move the image horizontally and vertically); Angle (rotate around the center — positive counterclockwise, negative clockwise); and Scale (resize relatively, so 0.5 is half size and 2.0 is double). Sampling — Filter, how pixel values are sampled when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, with single-pixel jitter in animation), Bilinear (an average of neighboring pixels, smoother and a good balance), Bicubic (a weighted average over a larger neighborhood, ideal for photos or gradients), and Anisotropic (adapted to the transform's direction and scale, cutting blur or aliasing at steep angles or uneven resolutions). Extension X/Y per axis — Clip (transparent outside), Extend (closest boundary pixel), or Repeat (image repetitions). Output: Image (standard color output).

## Translate Node

The Translate node moves an image — also usable to add a 2D camera shake. Inputs: Image (standard color input) and X, Y (move it horizontally and vertically). Sampling — Interpolation, how pixel values are sampled when scaling or transforming: Nearest (the closest pixel's value with no smoothing, the fastest, suiting pixel art or low-res images wanting sharp blocky edges, with single-pixel jitter in animation), Bilinear (an average of neighboring pixels, smoother and a good balance), Bicubic (a weighted average over a larger neighborhood, ideal for photos or gradients), and Anisotropic (adapted to the transform's direction and scale, cutting blur or aliasing at steep angles or uneven resolutions). Extension X/Y per axis — Clip (transparent outside), Extend (closest boundary pixel), or Repeat (image repetitions). Output: Image (standard color output).

Offsets an image's or texture's texture coordinates.

Inputs:
Color — the usual color input.
Offset — how much to offset the coordinates along each of the three axes.

Properties — this node exposes no properties.

Outputs:
Color — the usual color output.

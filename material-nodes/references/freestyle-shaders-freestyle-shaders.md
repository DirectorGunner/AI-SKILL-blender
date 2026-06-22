# Freestyle Shaders Freestyle Shaders

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Freestyle Shaders (freestyle.shaders) 

The stroke shaders gathered here are used to build stylized strokes. The module additionally serves as a set of worked samples for defining your own shaders in Python.

Any stroke shader you write yourself derives from the freestyle.types.StrokeShader class.

class freestyle.shaders. BackboneStretcherShader 

Class hierarchy: freestyle.types.StrokeShader > BackboneStretcherShader

[Geometry shader]

__init__ ( amount = 2.0 ) 

Builds a BackboneStretcherShader object.

Parameters :

amount ( float ) – How much stretching to apply.

shade ( stroke ) 

Extends the stroke at each of its two ends, along the matching directions v(1)v(0) and v(n-1)v(n).

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. BezierCurveShader 

Class hierarchy: freestyle.types.StrokeShader > BezierCurveShader

[Geometry shader]

__init__ ( error = 4.0 ) 

Builds a BezierCurveShader object.

Parameters :

error ( float ) – How much error the approximation is permitted, measured as the largest distance tolerated between the new curve and the original geometry.

shade ( stroke ) 

Reshapes the stroke's backbone geometry so it matches a Bezier Curve fit to the backbone it started from.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. BlenderTextureShader 

Class hierarchy: freestyle.types.StrokeShader > BlenderTextureShader

[Texture shader]

__init__ ( texture ) 

Builds a BlenderTextureShader object.

Parameters :

texture (bpy.types.LineStyleTextureSlot | bpy.types.ShaderNodeTree) – A line style texture slot or a shader node tree to define a set of textures.

shade ( stroke ) 

Attaches a blender texture slot to the stroke's shading so that marks can be simulated.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. CalligraphicShader 

Class hierarchy: freestyle.types.StrokeShader > CalligraphicShader

[Thickness Shader]

__init__ ( thickness_min , thickness_max , orientation , clamp ) 

Builds a CalligraphicShader object.

Parameters :

- thickness_min ( float ) – The thinnest thickness, taken along the direction at right angles to the main one.

- thickness_max ( float ) – The thickest thickness, taken along the main direction.

- orientation (mathutils.Vector) – A 2D vector that points along the principal direction.

- clamp ( bool ) – When true, strokes come out black wherever their direction lands within -90 to 90 degrees of that principal direction and white elsewhere; when false, they stay black throughout.

shade ( stroke ) 

Sets thicknesses on the stroke's vertices so the line looks calligraphic — at its heaviest along one chosen direction, at its lightest along the direction square to it, and blended through the range in between.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. ColorNoiseShader 

Class hierarchy: freestyle.types.StrokeShader > ColorNoiseShader

[Color shader]

__init__ ( amplitude , period ) 

Builds a ColorNoiseShader object.

Parameters :

- amplitude ( float ) – The amplitude of the noise signal.

- period ( float ) – The period of the noise signal.

shade ( stroke ) 

A shader that lays noise over the stroke colors.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. ConstantColorShader 

Class hierarchy: freestyle.types.StrokeShader > ConstantColorShader

[Color shader]

__init__ ( red , green , blue , alpha = 1.0 ) 

Builds a ConstantColorShader object.

Parameters :

- red ( float ) – The red component.

- green ( float ) – The green component.

- blue ( float ) – The blue component.

- alpha ( float ) – The alpha value.

shade ( stroke ) 

Gives every vertex of the Stroke one and the same color.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. ConstantThicknessShader 

Class hierarchy: freestyle.types.StrokeShader > ConstantThicknessShader

[Thickness shader]

__init__ ( thickness ) 

Builds a ConstantThicknessShader object.

Parameters :

thickness ( float ) – The thickness to apply to the stroke.

shade ( stroke ) 

Gives every vertex of the Stroke the same absolute, fixed thickness.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. ConstrainedIncreasingThicknessShader 

Class hierarchy: freestyle.types.StrokeShader > ConstrainedIncreasingThicknessShader

[Thickness shader]

__init__ ( thickness_min , thickness_max , ratio ) 

Builds a ConstrainedIncreasingThicknessShader object.

Parameters :

- thickness_min ( float ) – The minimum thickness.

- thickness_max ( float ) – The maximum thickness.

- ratio ( float ) – The largest thickness/length ratio that should not be passed.

shade ( stroke ) 

Works like the IncreasingThicknessShader, except it lets you cap the thickness/length ratio so short lines don't come out fat.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. GuidingLinesShader 

Class hierarchy: freestyle.types.StrokeShader > GuidingLinesShader

[Geometry shader]

__init__ ( offset ) 

Builds a GuidingLinesShader object.

Parameters :

offset ( float ) – The replacement line starts out centered in the original stroke's bounding box; offset is how far that line gets shifted along its normal.

shade ( stroke ) 

A shader that reworks the Stroke geometry so it follows its main-direction line. Pair it with the splitting operator that uses the curvature criterion, since how accurate the approximation turns out depends on the size of the stroke's pieces — the larger the pieces, the coarser the result.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. IncreasingColorShader 

Class hierarchy: freestyle.types.StrokeShader > IncreasingColorShader

[Color shader]

__init__ ( red_min , green_min , blue_min , alpha_min , red_max , green_max , blue_max , alpha_max ) 

Builds an IncreasingColorShader object.

Parameters :

- red_min ( float ) – The first color red component.

- green_min ( float ) – The first color green component.

- blue_min ( float ) – The first color blue component.

- alpha_min ( float ) – The first color alpha value.

- red_max ( float ) – The second color red component.

- green_max ( float ) – The second color green component.

- blue_max ( float ) – The second color blue component.

- alpha_max ( float ) – The second color alpha value.

shade ( stroke ) 

Paints the stroke with a shifting color. You give two colors, A and B; the stroke's color moves linearly from A to B across the span from the first vertex to the last.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. IncreasingThicknessShader 

Class hierarchy: freestyle.types.StrokeShader > IncreasingThicknessShader

[Thickness shader]

__init__ ( thickness_A , thickness_B ) 

Builds an IncreasingThicknessShader object.

Parameters :

- thickness_A ( float ) – The first thickness value.

- thickness_B ( float ) – The second thickness value.

shade ( stroke ) 

Sets thicknesses that climb from value A up to value B between the first vertex and the midpoint vertex, then drop back from B to A between that midpoint and the last vertex, with thickness interpolated linearly from A to B.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. PolygonalizationShader 

Class hierarchy: freestyle.types.StrokeShader > PolygonalizationShader

[Geometry shader]

__init__ ( error ) 

Builds a PolygonalizationShader object.

Parameters :

error ( float ) – How much error the polygonal approximation may carry against the original geometry; the smaller it is, the nearer the new stroke stays to the original. It is the maximum distance allowed between the new stroke and the old one.

shade ( stroke ) 

Reworks the Stroke geometry to give it a more "polygonal" look. The approach begins from the smallest possible stroke approximation — a single line from the first vertex to the last — then subdivides it using the original stroke vertices until a chosen error is met.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. RoundCapShader 

round_cap_thickness ( x ) 

shade ( stroke ) 

class freestyle.shaders. SamplingShader 

Class hierarchy: freestyle.types.StrokeShader > SamplingShader

[Geometry shader]

__init__ ( sampling ) 

Builds a SamplingShader object.

Parameters :

sampling ( float ) – The sampling applied when resampling the stroke.

shade ( stroke ) 

Resamples the stroke.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. SmoothingShader 

Class hierarchy: freestyle.types.StrokeShader > SmoothingShader

[Geometry shader]

__init__ ( num_iterations = 100 , factor_point = 0.1 , factor_curvature = 0.0 , factor_curvature_difference = 0.2 , aniso_point = 0.0 , aniso_normal = 0.0 , aniso_curvature = 0.0 , carricature_factor = 1.0 ) 

Builds a SmoothingShader object.

Parameters :

- num_iterations ( int ) – The number of iterations.

- factor_point ( float ) – 0.1

- factor_curvature ( float ) – 0.0

- factor_curvature_difference ( float ) – 0.2

- aniso_point ( float ) – 0.0

- aniso_normal ( float ) – 0.0

- aniso_curvature ( float ) – 0.0

- carricature_factor ( float ) – 1.0

shade ( stroke ) 

Smooths the stroke by nudging its vertices so the line reads more smoothly. Curvature flow drives it toward a curve of constant curvature, and the diffusion is made anisotropic so it does not bleed across corners.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. SpatialNoiseShader 

Class hierarchy: freestyle.types.StrokeShader > SpatialNoiseShader

[Geometry shader]

__init__ ( amount , scale , num_octaves , smooth , pure_random ) 

Builds a SpatialNoiseShader object.

Parameters :

- amount ( float ) – The amplitude of the noise.

- scale ( float ) – The noise frequency.

- num_octaves ( int ) – The number of octaves

- smooth ( bool ) – Set true for smooth noise.

- pure_random ( bool ) – Set true if no coherence is wanted.

shade ( stroke ) 

A Spatial Noise stroke shader that shifts vertices to roughen the stroke.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. SquareCapShader 

shade ( stroke ) 

class freestyle.shaders. StrokeTextureStepShader 

Class hierarchy: freestyle.types.StrokeShader > StrokeTextureStepShader

[Texture shader]

__init__ ( step ) 

Builds a StrokeTextureStepShader object.

Parameters :

step ( float ) – The spacing along the stroke.

shade ( stroke ) 

Sets a spacing factor on the Stroke's texture coordinates.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. ThicknessNoiseShader 

Class hierarchy: freestyle.types.StrokeShader > ThicknessNoiseShader

[Thickness shader]

__init__ ( amplitude , period ) 

Builds a ThicknessNoiseShader object.

Parameters :

- amplitude ( float ) – The amplitude of the noise signal.

- period ( float ) – The period of the noise signal.

shade ( stroke ) 

Lays some noise over the stroke thickness.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. TipRemoverShader 

Class hierarchy: freestyle.types.StrokeShader > TipRemoverShader

[Geometry shader]

__init__ ( tip_length ) 

Builds a TipRemoverShader object.

Parameters :

tip_length ( float ) – How long a piece of stroke to strip off at each end.

shade ( stroke ) 

Strips off the stroke's ends.

Parameters :

stroke (freestyle.types.Stroke) – A Stroke object.

class freestyle.shaders. py2DCurvatureColorShader 

Colors the stroke in grayscale according to its curvature, with greater curvature giving a lighter color.

shade ( stroke ) 

class freestyle.shaders. pyBackboneStretcherNoCuspShader 

Lengthens the stroke's backbone while leaving cusp vertices (the end junctions) alone.

shade ( stroke ) 

class freestyle.shaders. pyBackboneStretcherShader 

Lengthens the stroke's backbone by a chosen number of pixels.

shade ( stroke ) 

class freestyle.shaders. pyBluePrintCirclesShader 

Renders the object's silhouette as a circle.

shade ( stroke ) 

class freestyle.shaders. pyBluePrintDirectedSquaresShader 

Swaps the stroke out for a directed square.

shade ( stroke ) 

class freestyle.shaders. pyBluePrintEllipsesShader 

shade ( stroke ) 

class freestyle.shaders. pyBluePrintSquaresShader 

shade ( stroke ) 

class freestyle.shaders. pyConstantColorShader 

Gives the stroke a single fixed color.

shade ( stroke ) 

class freestyle.shaders. pyConstantThicknessShader 

Holds the thickness constant along the stroke.

shade ( stroke ) 

class freestyle.shaders. pyConstrainedIncreasingThicknessShader 

Thickens the stroke progressively, capped by a fraction of the stroke's length.

shade ( stroke ) 

class freestyle.shaders. pyDecreasingThicknessShader 

The reverse of pyIncreasingThicknessShader: it thins the stroke down progressively.

shade ( stroke ) 

class freestyle.shaders. pyDepthDiscontinuityThicknessShader 

Sets the stroke's thickness from how far the stroke sits from the camera (its Z-value).

shade ( stroke ) 

class freestyle.shaders. pyDiffusion2Shader 

Repeatedly shifts each stroke vertex's position along the direction perpendicular to the stroke at that point, scaling the shift by the 2D curvature (how sharply the stroke bends) there.

shade ( stroke ) 

class freestyle.shaders. pyFXSVaryingThicknessWithDensityShader 

Sets a stroke's thickness from how dense the diffuse map is.

shade ( stroke ) 

class freestyle.shaders. pyGuidingLineShader 

shade ( stroke ) 

class freestyle.shaders. pyHLRShader 

Drives visibility off the quantitative invisibility (QI) derived from hidden line removal (HLR).

shade ( stroke ) 

class freestyle.shaders. pyImportance2DThicknessShader 

Sets thickness from how far each vertex sits from a chosen point in 2D space. The mapping is inverted, so vertices nearest that point end up thinnest.

shade ( stroke ) 

class freestyle.shaders. pyImportance3DThicknessShader 

Sets thickness from how far each vertex sits from a chosen point in 3D space.

shade ( stroke ) 

class freestyle.shaders. pyIncreasingColorShader 

Blends from one color into another along the stroke.

shade ( stroke ) 

class freestyle.shaders. pyIncreasingThicknessShader 

Thickens the stroke progressively.

shade ( stroke ) 

class freestyle.shaders. pyInterpolateColorShader 

Blends from one color into another and then back again.

shade ( stroke ) 

class freestyle.shaders. pyLengthDependingBackboneStretcherShader 

Lengthens the stroke's backbone in proportion to the stroke's length. NOTE: you'll most likely want l somewhere in the (0.5 - 0) range; setting it too high can produce surprising results.

shade ( stroke ) 

class freestyle.shaders. pyMaterialColorShader 

Colors the stroke with the color of the material beneath it.

shade ( stroke ) 

class freestyle.shaders. pyModulateAlphaShader 

Clamps the stroke's alpha to stay within a minimum and maximum value.

shade ( stroke ) 

class freestyle.shaders. pyNonLinearVaryingThicknessShader 

Sets a stroke's thickness via an exponential function.

shade ( stroke ) 

class freestyle.shaders. pyPerlinNoise1DShader 

Distorts the stroke from its curvilinear abscissa, so lines sharing the same length and sampling interval get distorted the same way.

shade ( stroke ) 

class freestyle.shaders. pyPerlinNoise2DShader 

Distorts the stroke from the stroke's own coordinates, so within a scene no two strokes get distorted alike.

More information on the noise shaders can be found at:

shade ( stroke ) 

class freestyle.shaders. pyRandomColorShader 

Colors the stroke from a supplied seed.

shade ( stroke ) 

class freestyle.shaders. pySLERPThicknessShader 

Sets a stroke's thickness via spherical linear interpolation.

shade ( stroke ) 

class freestyle.shaders. pySamplingShader 

Resamples the stroke so it ends up with the requested number of vertices.

shade ( stroke ) 

class freestyle.shaders. pySinusDisplacementShader 

Bends the stroke into a sine-wave shape.

shade ( stroke ) 

class freestyle.shaders. pyTVertexRemoverShader 

Strips t-vertices out of the stroke.

shade ( stroke ) 

class freestyle.shaders. pyTVertexThickenerShader 

Thickens TVertices (the visible crossings where two edges meet).

shade ( stroke ) 

class freestyle.shaders. pyTimeColorShader 

Assigns a grayscale value that rises with each successive vertex, so brightness grows along the stroke.

shade ( stroke ) 

class freestyle.shaders. pyTipRemoverShader 

Trims the stroke's tips off.

shade ( stroke ) 

static check_vertex ( v , length ) 

class freestyle.shaders. pyZDependingThicknessShader 

Sets thickness from an object's local Z depth, where the point nearest the camera is 1 and the point farthest from it is zero.

shade ( stroke )

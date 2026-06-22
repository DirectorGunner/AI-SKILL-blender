# Freestyle Functions Freestyle Functions (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Returns :

The average depth around the pointed Interface0D.

Return type :

float

class freestyle.functions. LocalAverageDepthF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > LocalAverageDepthF1D

__init__ ( sigma , integration_type = IntegrationType.MEAN ) 

Builds a LocalAverageDepthF1D object.

Parameters :

- sigma ( float ) – The same sigma that DensityF0D uses, fixing the window size applied on each density lookup.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the mean depth measured for an Interface1D. Points are sampled along the Interface1D (through the freestyle.functions.LocalAverageDepthF0D functor) at a sampling rate you choose, and the results are then folded into one figure by an integration method you choose.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The average depth evaluated for the Interface1D.

Return type :

float

class freestyle.functions. MaterialF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DMaterial > MaterialF0D

__init__ ( ) 

Builds a MaterialF0D object.

__call__ ( it ) 

Yields the material of the object taken at the freestyle.types.Interface0D referenced by the Interface0DIterator. That reading can be ambiguous (for a freestyle.types.TVertex, say). To resolve it, the functor leans on the context supplied by the 1D element that the Interface0DIterator sits on, and when two distinct materials sit on either side of the point it arbitrarily picks the material of the face lying to the left as the 1D element is followed. Tricky cases can still arise, however, and anyone needing to handle them a particular way should write their own getMaterial functor.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The material of the object evaluated at the pointed
Interface0D.

Return type :

freestyle.types.Material

class freestyle.functions. Normal2DF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DVec2f > Normal2DF0D

__init__ ( ) 

Builds a Normal2DF0D object.

__call__ ( it ) 

Yields a 2-component vector holding the normalized 2D normal of the 1D element that the freestyle.types.Interface0D referenced by the Interface0DIterator belongs to. The normal is taken at the pointed Interface0D.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The 2D normal of the 1D element evaluated at the pointed
Interface0D.

Return type :

mathutils.Vector

class freestyle.functions. Normal2DF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVec2f > Normal2DF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a Normal2DF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the 2D normal of the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The 2D normal for the Interface1D.

Return type :

mathutils.Vector

class freestyle.functions. Orientation2DF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVec2f > Orientation2DF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds an Orientation2DF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the 2D orientation of the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The 2D orientation of the Interface1D.

Return type :

mathutils.Vector

class freestyle.functions. Orientation3DF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVec3f > Orientation3DF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds an Orientation3DF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the 3D orientation of the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The 3D orientation of the Interface1D.

Return type :

mathutils.Vector

class freestyle.functions. QuantitativeInvisibilityF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DUnsigned > QuantitativeInvisibilityF0D

__init__ ( ) 

Builds a QuantitativeInvisibilityF0D object.

__call__ ( it ) 

Yields the quantitative invisibility of the freestyle.types.Interface0D referenced by the Interface0DIterator. That reading can be ambiguous (for a freestyle.types.TVertex, say). The functor tries to clear up the ambiguity by drawing on the context of the 1D element the Interface0D belongs to. Tricky cases can still occur, though, and anyone needing to handle them a particular way should write their own getQIF0D functor.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The quantitative invisibility of the pointed Interface0D.

Return type :

int

class freestyle.functions. QuantitativeInvisibilityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DUnsigned > QuantitativeInvisibilityF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a QuantitativeInvisibilityF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the Quantitative Invisibility of an Interface1D element. When the Interface1D is a freestyle.types.ViewEdge the result is unambiguous, but when it comes out of a chaining operation (chain, stroke) it may comprise several 1D elements whose Quantitative Invisibilities differ.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The Quantitative Invisibility of the Interface1D.

Return type :

int

class freestyle.functions. ReadCompleteViewMapPixelF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > ReadCompleteViewMapPixelF0D

__init__ ( level ) 

Builds a ReadCompleteViewMapPixelF0D object.

Parameters :

level ( int ) – Which level of the pyramid the pixel gets read from.

__call__ ( it ) 

Fetches a pixel from one of the levels of the complete viewmap.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

A pixel in one of the level of the complete viewmap.

Return type :

float

class freestyle.functions. ReadMapPixelF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > ReadMapPixelF0D

__init__ ( map_name , level ) 

Builds a ReadMapPixelF0D object.

Parameters :

- map_name ( str ) – Which map gets read, by name.

- level ( int ) – Which level of the pyramid the pixel gets read from.

__call__ ( it ) 

Fetches a pixel out of a map.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

A pixel in a map.

Return type :

float

class freestyle.functions. ReadSteerableViewMapPixelF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > ReadSteerableViewMapPixelF0D

__init__ ( orientation , level ) 

Builds a ReadSteerableViewMapPixelF0D object.

Parameters :

- orientation ( int ) – An integer in [0, 4] picking the orientation (E, NE, N, NW) of interest.

- level ( int ) – Which level of the pyramid the pixel gets read from.

__call__ ( it ) 

Fetches a pixel from one of the levels of one of the steerable viewmaps.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

A pixel in one of the level of one of the steerable viewmaps.

Return type :

float

class freestyle.functions. ShapeIdF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DId > ShapeIdF0D

__init__ ( ) 

Builds a ShapeIdF0D object.

__call__ ( it ) 

Yields the freestyle.types.Id of the Shape that the freestyle.types.Interface0D referenced by the Interface0DIterator belongs to. That reading can be ambiguous (for a freestyle.types.TVertex, say). The functor tries to clear up the ambiguity by drawing on the context of the 1D element the Interface0DIterator sits on. Tricky cases can still occur, though, and anyone needing to handle them a particular way should write their own getShapeIdF0D functor.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The Id of the Shape the pointed Interface0D belongs to.

Return type :

freestyle.types.Id

class freestyle.functions. TimeStampF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVoid > TimeStampF1D

__init__ ( ) 

Builds a TimeStampF1D object.

__call__ ( inter ) 

Yields the time stamp of the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

class freestyle.functions. VertexOrientation2DF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DVec2f > VertexOrientation2DF0D

__init__ ( ) 

Builds a VertexOrientation2DF0D object.

__call__ ( it ) 

Yields a 2-component vector holding the 2D oriented tangent of the 1D element that the freestyle.types.Interface0D referenced by the Interface0DIterator belongs to. That oriented tangent is taken at the pointed Interface0D.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The 2D oriented tangent to the 1D element evaluated at the
pointed Interface0D.

Return type :

mathutils.Vector

class freestyle.functions. VertexOrientation3DF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DVec3f > VertexOrientation3DF0D

__init__ ( ) 

Builds a VertexOrientation3DF0D object.

__call__ ( it ) 

Yields a 3-component vector holding the 3D oriented tangent of the 1D element that the freestyle.types.Interface0D referenced by the Interface0DIterator belongs to. That oriented tangent is taken at the pointed Interface0D.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The 3D oriented tangent to the 1D element evaluated at the
pointed Interface0D.

Return type :

mathutils.Vector

class freestyle.functions. ZDiscontinuityF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > ZDiscontinuityF0D

__init__ ( ) 

Builds a ZDiscontinuityF0D object.

__call__ ( it ) 

Yields a real number for the gap between the freestyle.types.Interface0D referenced by the Interface0DIterator and the shape sitting behind it (the occludee). That gap is measured in camera space and rescaled into the 0-to-1 range, so when the shape the Interface0D belongs to occludes nothing, the result is 1.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The normalized distance between the pointed Interface0D
and the occludee.

Return type :

float

class freestyle.functions. ZDiscontinuityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > ZDiscontinuityF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a ZDiscontinuityF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields a real number for the gap between an Interface1D and the shape sitting behind it (the occludee). That gap is measured in camera space and rescaled into the 0-to-1 range, so when the shape the Interface1D belongs to occludes nothing, the result is 1.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The normalized distance between the Interface1D and the occludee.

Return type :

float

class freestyle.functions. pyCurvilinearLengthF0D 

class freestyle.functions. pyDensityAnisotropyF0D 

Gauges how anisotropic the density is.

class freestyle.functions. pyDensityAnisotropyF1D 

class freestyle.functions. pyGetInverseProjectedZF1D 

class freestyle.functions. pyGetSquareInverseProjectedZF1D 

class freestyle.functions. pyInverseCurvature2DAngleF0D 

class freestyle.functions. pyViewMapGradientNormF0D 

class freestyle.functions. pyViewMapGradientNormF1D 

class freestyle.functions. pyViewMapGradientVectorF0D 

Yields the gradient vector at a pixel.

__init__ ( self , level ) 

Builds a pyViewMapGradientVectorF0D object.

Parameters :

level ( int ) – the level at which the gradient is computed

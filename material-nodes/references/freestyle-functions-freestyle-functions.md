# Freestyle Functions Freestyle Functions (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Freestyle Functions (freestyle.functions) 

The functions collected here act on vertices (0D elements) and on polylines (1D elements). The module additionally serves as a set of worked samples for writing your own functions in Python.

Any function you define yourself derives from one of the base classes below, the choice depending on whether it works on a 0D or 1D object and on what return type it produces:

- freestyle.types.UnaryFunction0DDouble

- freestyle.types.UnaryFunction0DEdgeNature

- freestyle.types.UnaryFunction0DFloat

- freestyle.types.UnaryFunction0DId

- freestyle.types.UnaryFunction0DMaterial

- freestyle.types.UnaryFunction0DUnsigned

- freestyle.types.UnaryFunction0DVec2f

- freestyle.types.UnaryFunction0DVec3f

- freestyle.types.UnaryFunction0DVectorViewShape

- freestyle.types.UnaryFunction0DViewShape

- freestyle.types.UnaryFunction1DDouble

- freestyle.types.UnaryFunction1DEdgeNature

- freestyle.types.UnaryFunction1DFloat

- freestyle.types.UnaryFunction1DUnsigned

- freestyle.types.UnaryFunction1DVec2f

- freestyle.types.UnaryFunction1DVec3f

- freestyle.types.UnaryFunction1DVectorViewShape

- freestyle.types.UnaryFunction1DVoid

class freestyle.functions. ChainingTimeStampF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVoid > ChainingTimeStampF1D

__init__ ( ) 

Builds a ChainingTimeStampF1D object.

__call__ ( inter ) 

Writes the chaining time stamp onto the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

class freestyle.functions. Curvature2DAngleF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > Curvature2DAngleF0D

__init__ ( ) 

Builds a Curvature2DAngleF0D object.

__call__ ( it ) 

Yields a real number expressing, as an angle, the 2D curvature of the 1D element that the freestyle.types.Interface0D referenced by the Interface0DIterator sits on. That 2D curvature is measured at the Interface0D itself.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The 2D curvature of the 1D element evaluated at the
pointed Interface0D.

Return type :

float

class freestyle.functions. Curvature2DAngleF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > Curvature2DAngleF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a Curvature2DAngleF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields, for an Interface1D, the 2D curvature expressed as an angle.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The 2D curvature as an angle.

Return type :

float

class freestyle.functions. CurveMaterialF0D 

A stand-in for the built-in MaterialF0D when building strokes, since MaterialF0D will not operate on Curves and Strokes. Where two materials meet at a boundary, line color priority decides which of the pair is selected.

Notes: it expects to iterate across CurvePoint instances
it may return None when no fedge turns up

class freestyle.functions. CurveNatureF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DEdgeNature > CurveNatureF0D

__init__ ( ) 

Builds a CurveNatureF0D object.

__call__ ( it ) 

Yields the freestyle.types.Nature of the 1D element that the Interface0D referenced by the Interface0DIterator belongs to.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The nature of the 1D element to which the pointed Interface0D
belongs.

Return type :

freestyle.types.Nature

class freestyle.functions. CurveNatureF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DEdgeNature > CurveNatureF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a CurveNatureF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the nature of the Interface1D — silhouette, ridge, crease, and the like. Unless the Interface1D happens to be a freestyle.types.ViewEdge, the answer can be ambiguous, because the Interface1D may have been assembled from several 1D elements of differing natures, and an integration scheme such as MEAN can then produce a meaningless figure.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The nature of the Interface1D.

Return type :

freestyle.types.Nature

class freestyle.functions. DensityF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > DensityF0D

__init__ ( sigma = 2.0 ) 

Builds a DensityF0D object.

Parameters :

sigma ( float ) – The gaussian sigma, i.e. the X position at which the gaussian drops to 0.5; this in turn fixes the window size (larger means smoother).

__call__ ( it ) 

Yields the density of the resulting image taken at the freestyle.types.Interface0D referenced by the Interface0DIterator. The measurement uses a square window of pixels centred on the sample point, integrating those values with a gaussian.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The density of the image evaluated at the pointed
Interface0D.

Return type :

float

class freestyle.functions. DensityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > DensityF1D

__init__ ( sigma = 2.0 , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a DensityF1D object.

Parameters :

- sigma ( float ) – The same sigma that DensityF0D takes, fixing the window size applied on each density lookup.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: the matching 0D function fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter ) 

Yields the density measured for an Interface1D. Points are sampled along the Interface1D (through the freestyle.functions.DensityF0D functor) at a sampling rate you choose, and the per-point densities are then folded into one figure by an integration method you choose.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The density evaluated for an Interface1D.

Return type :

float

class freestyle.functions. GetCompleteViewMapDensityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetCompleteViewMapDensityF1D

__init__ ( level , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a GetCompleteViewMapDensityF1D object.

Parameters :

- level ( int ) – Which level of the pyramid the pixel gets read from.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: the matching 0D function fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter ) 

Yields the density measured for an Interface1D within the complete viewmap image. Points are sampled along the Interface1D (through the freestyle.functions.ReadCompleteViewMapPixelF0D functor) and then folded into one figure by an integration method you choose.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The density evaluated for the Interface1D in the complete
viewmap image.

Return type :

float

class freestyle.functions. GetCurvilinearAbscissaF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > GetCurvilinearAbscissaF0D

__init__ ( ) 

Builds a GetCurvilinearAbscissaF0D object.

__call__ ( it ) 

Yields the curvilinear abscissa, taken within its 1D element, of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The curvilinear abscissa of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetDirectionalViewMapDensityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetDirectionalViewMapDensityF1D

__init__ ( orientation , level , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a GetDirectionalViewMapDensityF1D object.

Parameters :

- orientation ( int ) – Which directional map (by its number) is to be used.

- level ( int ) – Which level of the pyramid the pixel gets read from.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: the matching 0D function fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter ) 

Yields the density measured for an Interface1D inside the steerable viewmaps image. You name explicitly which Directional map applies via the direction. Points are sampled along the Interface1D (through the freestyle.functions.ReadSteerableViewMapPixelF0D functor) and then folded into one figure by an integration method you choose.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

the density evaluated for an Interface1D in of the
steerable viewmaps image.

Return type :

float

class freestyle.functions. GetOccludeeF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DViewShape > GetOccludeeF0D

__init__ ( ) 

Builds a GetOccludeeF0D object.

__call__ ( it ) 

Yields the freestyle.types.ViewShape that gets occluded by the Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The ViewShape occluded by the pointed Interface0D.

Return type :

freestyle.types.ViewShape

class freestyle.functions. GetOccludeeF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVectorViewShape > GetOccludeeF1D

__init__ ( ) 

Builds a GetOccludeeF1D object.

__call__ ( inter ) 

Yields the set of occluded shapes that this Interface1D spans.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

A list of occluded shapes covered by the Interface1D.

Return type :

list[freestyle.types.ViewShape]

class freestyle.functions. GetOccludersF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DVectorViewShape > GetOccludersF0D

__init__ ( ) 

Builds a GetOccludersF0D object.

__call__ ( it ) 

Yields the set of freestyle.types.ViewShape that occlude the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

A list of ViewShape objects occluding the pointed
Interface0D.

Return type :

list[freestyle.types.ViewShape]

class freestyle.functions. GetOccludersF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVectorViewShape > GetOccludersF1D

__init__ ( ) 

Builds a GetOccludersF1D object.

__call__ ( inter ) 

Yields the set of occluding shapes that span this Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

A list of occluding shapes that cover the Interface1D.

Return type :

list[freestyle.types.ViewShape]

class freestyle.functions. GetParameterF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > GetParameterF0D

__init__ ( ) 

Builds a GetParameterF0D object.

__call__ ( it ) 

Yields the parameter, within its 1D element, of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The parameter of an Interface0D.

Return type :

float

class freestyle.functions. GetProjectedXF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetProjectedXF0D

__init__ ( ) 

Builds a GetProjectedXF0D object.

__call__ ( it ) 

Yields the projected X 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The X 3D projected coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetProjectedXF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetProjectedXF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetProjectedXF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the projected X 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The projected X 3D coordinate of an Interface1D.

Return type :

float

class freestyle.functions. GetProjectedYF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetProjectedYF0D

__init__ ( ) 

Builds a GetProjectedYF0D object.

__call__ ( it ) 

Yields the projected Y 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The Y 3D projected coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetProjectedYF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetProjectedYF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetProjectedYF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the projected Y 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The projected Y 3D coordinate of an Interface1D.

Return type :

float

class freestyle.functions. GetProjectedZF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetProjectedZF0D

__init__ ( ) 

Builds a GetProjectedZF0D object.

__call__ ( it ) 

Yields the projected Z 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The Z 3D projected coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetProjectedZF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetProjectedZF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetProjectedZF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the projected Z 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The projected Z 3D coordinate of an Interface1D.

Return type :

float

class freestyle.functions. GetShapeF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DViewShape > GetShapeF0D

__init__ ( ) 

Builds a GetShapeF0D object.

__call__ ( it )

Yields the freestyle.types.ViewShape that holds the Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The ViewShape containing the pointed Interface0D.

Return type :

freestyle.types.ViewShape

class freestyle.functions. GetShapeF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVectorViewShape > GetShapeF1D

__init__ ( ) 

Builds a GetShapeF1D object.

__call__ ( inter ) 

Yields the set of shapes that this Interface1D spans.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

A list of shapes covered by the Interface1D.

Return type :

list[freestyle.types.ViewShape]

class freestyle.functions. GetSteerableViewMapDensityF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetSteerableViewMapDensityF1D

__init__ ( level , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a GetSteerableViewMapDensityF1D object.

Parameters :

- level ( int ) – Which level of the pyramid the pixel gets read from.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: the matching 0D function fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter ) 

Yields the ViewMap density for a supplied Interface1D. Each freestyle.types.FEdge has its density taken in whichever steerable freestyle.types.ViewMap matches its orientation.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The density of the ViewMap for a given Interface1D.

Return type :

float

class freestyle.functions. GetViewMapGradientNormF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DFloat > GetViewMapGradientNormF0D

__init__ ( level ) 

Builds a GetViewMapGradientNormF0D object.

Parameters :

level ( int ) – Which level of the pyramid the pixel gets read from.

__call__ ( it ) 

Yields how large the gradient of the global viewmap density image is.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The norm of the gradient of the global viewmap density
image.

Return type :

float

class freestyle.functions. GetViewMapGradientNormF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetViewMapGradientNormF1D

__init__ ( level , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a GetViewMapGradientNormF1D object.

Parameters :

- level ( int ) – Which level of the pyramid the pixel gets read from.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: the matching 0D function fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter ) 

Yields the ViewMap density for a supplied Interface1D. Each freestyle.types.FEdge has its density taken in whichever steerable freestyle.types.ViewMap matches its orientation.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The density of the ViewMap for a given Interface1D.

Return type :

float

class freestyle.functions. GetXF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetXF0D

__init__ ( ) 

Builds a GetXF0D object.

__call__ ( it ) 

Yields the X 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The X 3D coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetXF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetXF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetXF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the X 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The X 3D coordinate of the Interface1D.

Return type :

float

class freestyle.functions. GetYF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetYF0D

__init__ ( ) 

Builds a GetYF0D object.

__call__ ( it ) 

Yields the Y 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The Y 3D coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetYF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetYF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetYF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the Y 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The Y 3D coordinate of the Interface1D.

Return type :

float

class freestyle.functions. GetZF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > GetZF0D

__init__ ( ) 

Builds a GetZF0D object.

__call__ ( it ) 

Yields the Z 3D coordinate of the freestyle.types.Interface0D referenced by the Interface0DIterator.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

The Z 3D coordinate of the pointed Interface0D.

Return type :

float

class freestyle.functions. GetZF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DDouble > GetZF1D

__init__ ( integration_type = IntegrationType.MEAN ) 

Builds a GetZF1D object.

Parameters :

integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

__call__ ( inter ) 

Yields the Z 3D coordinate of an Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

The Z 3D coordinate of the Interface1D.

Return type :

float

class freestyle.functions. IncrementChainingTimeStampF1D 

Class hierarchy: freestyle.types.UnaryFunction1D > freestyle.types.UnaryFunction1DVoid > IncrementChainingTimeStampF1D

__init__ ( ) 

Builds an IncrementChainingTimeStampF1D object.

__call__ ( inter ) 

Bumps up the chaining time stamp held by the Interface1D.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

class freestyle.functions. LocalAverageDepthF0D 

Class hierarchy: freestyle.types.UnaryFunction0D > freestyle.types.UnaryFunction0DDouble > LocalAverageDepthF0D

__init__ ( mask_size = 5.0 ) 

Builds a LocalAverageDepthF0D object.

Parameters :

mask_size ( float ) – How large the mask is.

__call__ ( it ) 

Yields the mean depth in the neighbourhood of the freestyle.types.Interface0D referenced by the Interface0DIterator. It comes from sampling the depth buffer across a window around that point.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

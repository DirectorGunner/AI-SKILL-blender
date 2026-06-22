# Freestyle Predicates Freestyle Predicates

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Freestyle Predicates (freestyle.predicates) 

The predicates gathered here act on vertices (0D elements) and on polylines (1D elements). The module additionally serves as a set of worked samples for defining your own predicates in Python.

Any predicate you write yourself derives from one of the base classes below, the choice turning on whether it works on a 0D or 1D object and on its arity (unary or binary):

- freestyle.types.BinaryPredicate0D

- freestyle.types.BinaryPredicate1D

- freestyle.types.UnaryPredicate0D

- freestyle.types.UnaryPredicate1D

class freestyle.predicates. AndBP1D 

class freestyle.predicates. AndUP1D 

class freestyle.predicates. ContourUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > ContourUP1D

__call__ ( inter ) 

Comes back true when the Interface1D is a contour. An Interface1D qualifies as a contour when a different shape borders each of its two sides.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if the Interface1D is a contour, false otherwise.

Return type :

bool

class freestyle.predicates. DensityLowerThanUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > DensityLowerThanUP1D

__init__ ( threshold , sigma = 2.0 ) 

Builds a DensityLowerThanUP1D object.

Parameters :

- threshold ( float ) – The threshold density value. An Interface1D whose density falls under it is a match.

- sigma ( float ) – The sigma that sets the size of the density evaluation window used by the freestyle.functions.DensityF0D functor.

__call__ ( inter ) 

Comes back true when the density measured for the Interface1D falls below a density value you specify.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if the density is lower than a threshold.

Return type :

bool

class freestyle.predicates. EqualToChainingTimeStampUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > freestyle.types.EqualToChainingTimeStampUP1D

__init__ ( ts ) 

Builds a EqualToChainingTimeStampUP1D object.

Parameters :

ts ( int ) – A time stamp value.

__call__ ( inter ) 

Comes back true when the Interface1D's time stamp matches a value you specify.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if the time stamp is equal to a user-defined value.

Return type :

bool

class freestyle.predicates. EqualToTimeStampUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > EqualToTimeStampUP1D

__init__ ( ts ) 

Builds a EqualToTimeStampUP1D object.

Parameters :

ts ( int ) – A time stamp value.

__call__ ( inter ) 

Comes back true when the Interface1D's time stamp matches a value you specify.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if the time stamp is equal to a user-defined value.

Return type :

bool

class freestyle.predicates. ExternalContourUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > ExternalContourUP1D

__call__ ( inter ) 

Comes back true when the Interface1D is an external contour. An Interface1D counts as an external contour when one of its sides has no shape bordering it.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if the Interface1D is an external contour, false
otherwise.

Return type :

bool

class freestyle.predicates. FalseBP1D 

Class hierarchy: freestyle.types.BinaryPredicate1D > FalseBP1D

__call__ ( inter1 , inter2 ) 

Returns false in every case.

Parameters :

- inter1 (freestyle.types.Interface1D) – The first Interface1D object.

- inter2 (freestyle.types.Interface1D) – The second Interface1D object.

Returns :

False.

Return type :

bool

class freestyle.predicates. FalseUP0D 

Class hierarchy: freestyle.types.UnaryPredicate0D > FalseUP0D

__call__ ( it ) 

Returns false in every case.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

False.

Return type :

bool

class freestyle.predicates. FalseUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > FalseUP1D

__call__ ( inter ) 

Returns false in every case.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

False.

Return type :

bool

class freestyle.predicates. Length2DBP1D 

Class hierarchy: freestyle.types.BinaryPredicate1D > Length2DBP1D

__call__ ( inter1 , inter2 ) 

Comes back true when inter1's 2D length is shorter than inter2's 2D length.

Parameters :

- inter1 (freestyle.types.Interface1D) – The first Interface1D object.

- inter2 (freestyle.types.Interface1D) – The second Interface1D object.

Returns :

True or false.

Return type :

bool

class freestyle.predicates. MaterialBP1D 

Tests whether the two given ViewEdges carry the same material.

class freestyle.predicates. NotBP1D 

class freestyle.predicates. NotUP1D 

class freestyle.predicates. ObjectNamesUP1D 

class freestyle.predicates. OrBP1D 

class freestyle.predicates. OrUP1D 

class freestyle.predicates. QuantitativeInvisibilityRangeUP1D 

class freestyle.predicates. QuantitativeInvisibilityUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > QuantitativeInvisibilityUP1D

__init__ ( qi = 0 ) 

Builds a QuantitativeInvisibilityUP1D object.

Parameters :

qi ( int ) – The Quantitative Invisibility you wish the Interface1D to carry.

__call__ ( inter ) 

Comes back true when the Quantitative Invisibility measured at an Interface1D, by way of the freestyle.functions.QuantitativeInvisibilityF1D functor, matches a value you specify.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if Quantitative Invisibility equals a user-defined
value.

Return type :

bool

class freestyle.predicates. SameShapeIdBP1D 

Class hierarchy: freestyle.types.BinaryPredicate1D > SameShapeIdBP1D

__call__ ( inter1 , inter2 ) 

Comes back true when inter1 and inter2 are part of the same shape.

Parameters :

- inter1 (freestyle.types.Interface1D) – The first Interface1D object.

- inter2 (freestyle.types.Interface1D) – The second Interface1D object.

Returns :

True or false.

Return type :

bool

class freestyle.predicates. ShapeUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > ShapeUP1D

__init__ ( first , second = 0 ) 

Builds a ShapeUP1D object.

Parameters :

- first ( int ) – The first Id component.

- second ( int ) – The second Id component.

__call__ ( inter ) 

Comes back true when the shape the Interface1D belongs to carries the same freestyle.types.Id that the user named.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True if Interface1D belongs to the shape of the
user-specified Id.

Return type :

bool

class freestyle.predicates. TrueBP1D 

Class hierarchy: freestyle.types.BinaryPredicate1D > TrueBP1D

__call__ ( inter1 , inter2 ) 

Returns true in every case.

Parameters :

- inter1 (freestyle.types.Interface1D) – The first Interface1D object.

- inter2 (freestyle.types.Interface1D) – The second Interface1D object.

Returns :

True.

Return type :

bool

class freestyle.predicates. TrueUP0D 

Class hierarchy: freestyle.types.UnaryPredicate0D > TrueUP0D

__call__ ( it ) 

Returns true in every case.

Parameters :

it (freestyle.types.Interface0DIterator) – An Interface0DIterator object.

Returns :

True.

Return type :

bool

class freestyle.predicates. TrueUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > TrueUP1D

__call__ ( inter ) 

Returns true in every case.

Parameters :

inter (freestyle.types.Interface1D) – An Interface1D object.

Returns :

True.

Return type :

bool

class freestyle.predicates. ViewMapGradientNormBP1D 

Class hierarchy: freestyle.types.BinaryPredicate1D > ViewMapGradientNormBP1D

__init__ ( level , integration_type = IntegrationType.MEAN , sampling = 2.0 ) 

Builds a ViewMapGradientNormBP1D object.

Parameters :

- level ( int ) – Which level of the pyramid the pixel gets read from.

- integration_type (freestyle.types.IntegrationType) – Which integration scheme collapses a collection of values down to one.

- sampling ( float ) – How finely the chain gets sampled: GetViewMapGradientNormF0D fires at every sample point and the per-point results are merged into one value via the scheme named by integration_type.

__call__ ( inter1 , inter2 ) 

Comes back true when the Gradient norm Function evaluates higher on inter1 than it does on inter2.

Parameters :

- inter1 (freestyle.types.Interface1D) – The first Interface1D object.

- inter2 (freestyle.types.Interface1D) – The second Interface1D object.

Returns :

True or false.

Return type :

bool

class freestyle.predicates. WithinImageBoundaryUP1D 

Class hierarchy: freestyle.types.UnaryPredicate1D > WithinImageBoundaryUP1D

__init__ ( xmin , ymin , xmax , ymax ) 

Builds an WithinImageBoundaryUP1D object.

Parameters :

- xmin ( float ) – X lower bound of the image boundary.

- ymin ( float ) – Y lower bound of the image boundary.

- xmax ( float ) – X upper bound of the image boundary.

- ymax ( float ) – Y upper bound of the image boundary.

__call__ ( inter ) 

Comes back true when the Interface1D crosses the image boundary.

class freestyle.predicates. pyBackTVertexUP0D 

Tests whether an Interface0DIterator points at a TVertex and is specifically the hidden one (deduced from context).

class freestyle.predicates. pyClosedCurveUP1D 

class freestyle.predicates. pyDensityFunctorUP1D 

class freestyle.predicates. pyDensityUP1D 

class freestyle.predicates. pyDensityVariableSigmaUP1D 

class freestyle.predicates. pyHighDensityAnisotropyUP1D 

class freestyle.predicates. pyHighDirectionalViewMapDensityUP1D 

class freestyle.predicates. pyHighSteerableViewMapDensityUP1D 

class freestyle.predicates. pyHighViewMapDensityUP1D 

class freestyle.predicates. pyHighViewMapGradientNormUP1D 

class freestyle.predicates. pyHigherCurvature2DAngleUP0D 

class freestyle.predicates. pyHigherLengthUP1D 

class freestyle.predicates. pyHigherNumberOfTurnsUP1D 

class freestyle.predicates. pyIsInOccludersListUP1D 

class freestyle.predicates. pyIsOccludedByIdListUP1D 

class freestyle.predicates. pyIsOccludedByItselfUP1D 

class freestyle.predicates. pyIsOccludedByUP1D 

class freestyle.predicates. pyLengthBP1D 

class freestyle.predicates. pyLowDirectionalViewMapDensityUP1D 

class freestyle.predicates. pyLowSteerableViewMapDensityUP1D 

class freestyle.predicates. pyNFirstUP1D 

class freestyle.predicates. pyNatureBP1D 

class freestyle.predicates. pyNatureUP1D 

class freestyle.predicates. pyParameterUP0D 

class freestyle.predicates. pyParameterUP0DGoodOne 

class freestyle.predicates. pyProjectedXBP1D 

class freestyle.predicates. pyProjectedYBP1D 

class freestyle.predicates. pyShapeIdListUP1D 

class freestyle.predicates. pyShapeIdUP1D 

class freestyle.predicates. pyShuffleBP1D 

class freestyle.predicates. pySilhouetteFirstBP1D 

class freestyle.predicates. pyUEqualsUP0D 

class freestyle.predicates. pyVertexNatureUP0D 

class freestyle.predicates. pyViewMapGradientNormBP1D 

class freestyle.predicates. pyZBP1D 

class freestyle.predicates. pyZDiscontinuityBP1D 

class freestyle.predicates. pyZSmallerUP1D

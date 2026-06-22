# Freestyle Types Freestyle Types (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Freestyle Types (freestyle.types) 

This module holds the core classes of the Freestyle Python API: the data types for view map components (0D and 1D elements), the base classes you subclass for user-defined line stylization rules (predicates, functions, chaining iterators, and stroke shaders), and the operators.

Class hierarchy:

- BBox

- BinaryPredicate0D

- BinaryPredicate1D

- Id

- Interface0D

- CurvePoint

- StrokeVertex

- SVertex

- ViewVertex

- NonTVertex

- TVertex

- Interface1D

- Curve

- Chain

- FEdge

- FEdgeSharp

- FEdgeSmooth

- Stroke

- ViewEdge

- Iterator

- AdjacencyIterator

- CurvePointIterator

- Interface0DIterator

- SVertexIterator

- StrokeVertexIterator

- ViewEdgeIterator

- ChainingIterator

- orientedViewEdgeIterator

- Material

- Noise

- Operators

- SShape

- StrokeAttribute

- StrokeShader

- UnaryFunction0D

- UnaryFunction0DDouble

- UnaryFunction0DEdgeNature

- UnaryFunction0DFloat

- UnaryFunction0DId

- UnaryFunction0DMaterial

- UnaryFunction0DUnsigned

- UnaryFunction0DVec2f

- UnaryFunction0DVec3f

- UnaryFunction0DVectorViewShape

- UnaryFunction0DViewShape

- UnaryFunction1D

- UnaryFunction1DDouble

- UnaryFunction1DEdgeNature

- UnaryFunction1DFloat

- UnaryFunction1DUnsigned

- UnaryFunction1DVec2f

- UnaryFunction1DVec3f

- UnaryFunction1DVectorViewShape

- UnaryFunction1DVoid

- UnaryPredicate0D

- UnaryPredicate1D

- ViewMap

- ViewShape

- IntegrationType

- MediumType

- Nature

class freestyle.types. AdjacencyIterator 

Class hierarchy: Iterator > AdjacencyIterator

The class behind the adjacency iterators that the chaining process relies on. A ChainingIterator spins one up inside its increment() and decrement() methods and hands it off to the ChainingIterator's traverse() method.

__init__ ( ) 

__init__ ( brother )

__init__ ( vertex , restrict_to_selection = True , restrict_to_unvisited = True )

Constructs an AdjacencyIterator via the default constructor, the copy constructor, or the overloaded one.

Parameters :

- brother (AdjacencyIterator) – An AdjacencyIterator object.

- vertex (ViewVertex) – The vertex that forms the next crossing.

- restrict_to_selection ( bool ) – Whether chaining is kept confined to the pool of selected ViewEdges or allowed to leave it.

- restrict_to_unvisited ( bool ) – Whether a ViewEdge already used in a chain should be skipped or reused.

is_incoming 

True when the current ViewEdge runs toward the iteration vertex, False otherwise.

Type :

bool

object 

The ViewEdge this iterator currently points at.

Type :

ViewEdge

class freestyle.types. BBox 

A class that stands for a bounding box.

__init__ ( ) 

Default constructor.

class freestyle.types. BinaryPredicate0D 

The base class for binary predicates that operate on Interface0D objects. A BinaryPredicate0D usually expresses an ordering between two Interface0D objects: it weighs a relation between the pair of Interface0D instances and hands back a boolean (true or false). You invoke it through the __call__() method.

__init__ ( ) 

Default constructor.

__call__ ( inter1 , inter2 ) 

Inheriting classes must override this. It weighs a relation between two Interface0D objects.

Parameters :

- inter1 (Interface0D) – The first Interface0D object.

- inter2 (Interface0D) – The second Interface0D object.

Returns :

True or false.

Return type :

bool

name 

The name of the binary 0D predicate.

Type :

str

class freestyle.types. BinaryPredicate1D 

The base class for binary predicates that operate on Interface1D objects. A BinaryPredicate1D usually expresses an ordering between two Interface1D objects: it weighs a relation between the pair of Interface1D instances and hands back a boolean (true or false). You invoke it through the __call__() method.

__init__ ( ) 

Default constructor.

__call__ ( inter1 , inter2 ) 

Inheriting classes must override this. It weighs a relation between two Interface1D objects.

Parameters :

- inter1 (Interface1D) – The first Interface1D object.

- inter2 (Interface1D) – The second Interface1D object.

Returns :

True or false.

Return type :

bool

name 

The name of the binary 1D predicate.

Type :

str

class freestyle.types. Chain 

Class hierarchy: Interface1D > Curve > Chain

A class standing for a 1D element produced by the chaining process. A Chain is the final stage ahead of the Stroke and feeds into the Splitting and Creation processes.

__init__ ( ) 

__init__ ( brother )

__init__ ( id )

Constructs a Chain through the default constructor, the copy constructor, or from an Id.

Parameters :

- brother (Chain) – A Chain object.

- id (Id) – An Id object.

push_viewedge_back ( viewedge , orientation ) 

Appends a ViewEdge onto the end of the Chain.

Parameters :

- viewedge (ViewEdge) – The ViewEdge that must be added.

- orientation ( bool ) – The orientation with which the ViewEdge must be processed.

push_viewedge_front ( viewedge , orientation ) 

Prepends a ViewEdge at the start of the Chain.

Parameters :

- viewedge (ViewEdge) – The ViewEdge that must be added.

- orientation ( bool ) – The orientation with which the ViewEdge must be
processed.

class freestyle.types. ChainingIterator 

Class hierarchy: Iterator > ViewEdgeIterator > ChainingIterator

The base class for chaining iterators. It is meant to be subclassed so you can spell out chaining rules, which it makes more straightforward to describe. The two key methods to override are traverse() and init(). traverse() decides which ViewEdge to take next among the adjacent ones. Any restriction rules you set (for instance, "chain only ViewEdges in the selection") get folded into the adjacency iterator, so that iterator will halt solely on "valid" edges.

__init__ ( restrict_to_selection = True , restrict_to_unvisited = True , begin = None , orientation = True ) 

__init__ ( brother )

Constructs a Chaining Iterator from the seed ViewEdge iteration begins on plus its orientation, or through the copy constructor.

Parameters :

- restrict_to_selection ( bool ) – Whether chaining is kept confined to the pool of selected ViewEdges or allowed to leave it.

- restrict_to_unvisited ( bool ) – Whether a ViewEdge already used in a chain should be skipped or reused.

- begin (ViewEdge | None) – The ViewEdge the chain starts from.

- orientation ( bool ) – Which way to head when exploring the graph; when true, the direction set by the first ViewEdge is taken.

- brother (ChainingIterator)

init ( ) 

Sets up the iterator's context. It runs at the start of every new chain and is the place to clear any history you may wish to retain.

traverse ( it ) 

Walks across the candidate next ViewEdges and hands back the one chaining should proceed with. The result is either the upcoming ViewEdge or None once the chain has run out.

Parameters :

it (AdjacencyIterator) – The iterator covering the ViewEdges next to the end vertex of the active ViewEdge. Because the adjacency iterator honors the restriction rules, it only visits ViewEdges that qualify.

Returns :

The following ViewEdge to chain to, or None once there is nothing left to chain.

Return type :

ViewEdge | None

is_incrementing 

Set to True whenever the present pass is moving forward by incrementing.

Type :

bool

next_vertex 

The ViewVertex marking the crossing that comes up next.

Type :

ViewVertex

object 

Whatever ViewEdge this iterator is sitting on right now.

Type :

ViewEdge

class freestyle.types. Curve 

Class hierarchy: Interface1D > Curve

Serves as the parent type for curves assembled from CurvePoints. The vertices a curve starts from are SVertex instances, and a Chain is simply a particular kind of Curve.

__init__ ( ) 

__init__ ( brother )

__init__ ( id )

Constructs a FrsCurve, either with the default constructor, by copying another, or starting from an Id.

Parameters :

- brother (Curve) – A Curve object.

- id (Id) – An Id object.

push_vertex_back ( vertex ) 

Appends one vertex onto the tail end of the Curve.

Parameters :

vertex (SVertex | CurvePoint) – A vertex object.

push_vertex_front ( vertex ) 

Prepends one vertex at the head of the Curve.

Parameters :

vertex (SVertex | CurvePoint) – A vertex object.

is_empty 

Reports True while the Curve still holds no Vertex.

Type :

bool

segments_size 

How many segments the polyline forming the Curve is divided into.

Type :

int

class freestyle.types. CurvePoint 

Class hierarchy: Interface0D > CurvePoint

Represents one point sitting on a curve. Such a point need not coincide with a curve vertex; it can fall anywhere along a 1D curve. Since every Interface1D rests on ViewEdges, which in turn rest on FEdges, a curve amounts to a polyline strung together from SVertex objects. A CurvePoint is therefore produced by linearly blending two SVertex instances, which lets it act as a virtual point when 0D data is sampled along a curve at some chosen resolution.

__init__ ( ) 

__init__ ( brother )

__init__ ( first_vertex , second_vertex , t2d )

__init__ ( first_point , second_point , t2d )

Constructs a CurvePoint via the default constructor, the copy constructor, or one of the extra overloads. Those overloads accept either a pair of SVertex or a pair of CurvePoint objects together with an interpolation factor.

Parameters :

- brother (CurvePoint) – A CurvePoint object.

- first_vertex (SVertex) – The first SVertex.

- second_vertex (SVertex) – The second SVertex.

- first_point (CurvePoint) – The first CurvePoint.

- second_point (CurvePoint) – The second CurvePoint.

- t2d ( float ) – A 2D interpolation parameter used to linearly interpolate
first_vertex and second_vertex or first_point and second_point.

fedge 

Retrieves the FEdge spanning the two SVertices that the given CurvePoints are made of. This is shorthand for CurvePoint.first_svertex.get_fedge(CurvePoint.second_svertex).

Type :

FEdge

first_svertex 

The first of the two SVertex on which this CurvePoint rests.

Type :

SVertex

second_svertex 

The second of the two SVertex on which this CurvePoint rests.

Type :

SVertex

t2d 

The 2D interpolation parameter.

Type :

float

class freestyle.types. CurvePointIterator 

Class hierarchy: Iterator > CurvePointIterator

Provides an iterator that walks along a curve and can step past the original vertices. At each position a CurvePoint is created and exposed through the .object attribute.

__init__ ( ) 

__init__ ( brother )

__init__ ( step = 0.0 )

Constructs a CurvePointIterator with the default constructor, the copy constructor, or the overload taking a step.

Parameters :

- brother (CurvePointIterator) – A CurvePointIterator object.

- step ( float ) – The spacing at which the curve gets resampled. A value of zero turns resampling off, so the iterator only visits the original vertices.

object 

Whatever CurvePoint this iterator is sitting on right now.

Type :

CurvePoint

t 

The curvilinear abscissa of the current point.

Type :

float

u 

The point parameter at the current point in the stroke (0 <= u <= 1).

Type :

float

class freestyle.types. FEdge 

Class hierarchy: Interface1D > FEdge

Acts as the parent type for feature edges. Such an FEdge may stand for a silhouette, a crease, a ridge or valley, a border, or a suggestive contour. With silhouettes, orientation places the visible face on the edge's left side; borders likewise keep their face on the left. Depending on whether the mesh is smooth or sharp, an FEdge may coincide with an original mesh edge or instead cut across one of its faces. Because their properties differ somewhat, the class branches into a smooth variant and a sharp variant.

FEdge ( ) 

FEdge ( brother )

Constructs an FEdge using the default constructor, the copy constructor, or from a pair of SVertex objects.

Parameters :

- brother (FEdge) – An FEdge object.

- first_vertex (SVertex) – The first SVertex.

- second_vertex (SVertex) – The second SVertex.

first_svertex 

The first SVertex making up this FEdge.

Type :

SVertex

id 

The Id of this FEdge.

Type :

Id

is_smooth 

Set to True when this FEdge happens to be a smooth FEdge.

Type :

bool

nature 

The nature of this FEdge.

Type :

Nature

next_fedge 

Whatever FEdge comes after this one within the ViewEdge. None is reported when this FEdge sits at the end of the ViewEdge.

Type :

FEdge

previous_fedge 

Whatever FEdge comes before this one within the ViewEdge. None is reported when this FEdge sits at the start of the ViewEdge.

Type :

FEdge

second_svertex 

The second SVertex making up this FEdge.

Type :

SVertex

viewedge 

The ViewEdge that this FEdge is part of.

Type :

ViewEdge

class freestyle.types. FEdgeSharp 

Class hierarchy: Interface1D > FEdge > FEdgeSharp

Describes a sharp FEdge. A sharp FEdge maps onto one of the original edges of the input mesh and may be a silhouette, a crease, or a border. When it is a crease edge it is flanked by two mesh faces, with Face a on its right and Face b on its left. When it is a border edge nothing lies on its right, so Face a comes back as None.

__init__ ( ) 

__init__ ( brother )

__init__ ( first_vertex , second_vertex )

Constructs an FEdgeSharp using the default constructor, the copy constructor, or from a pair of SVertex objects.

Parameters :

- brother (FEdgeSharp) – An FEdgeSharp object.

- first_vertex (SVertex) – The first SVertex object.

- second_vertex (SVertex) – The second SVertex object.

face_mark_left 

The face mark belonging to the face on the left-hand side of the FEdge.

Type :

bool

face_mark_right 

The face mark belonging to the face on the right-hand side of the FEdge. When the FEdge is a border there is no face on the right, so this property comes back as false.

Type :

bool

material_index_left 

The material index of the face on the left-hand side of the FEdge.

Type :

int

material_index_right 

The material index of the face on the right-hand side of the FEdge. When the FEdge is a border there is no Face on its right, so it carries no material.

Type :

int

material_left 

The material of the face on the left-hand side of the FEdge.

Type :

Material

material_right 

The material of the face on the right-hand side of the FEdge. When the FEdge is a border there is no Face on its right, so it carries no material.

Type :

Material

normal_left 

The normal vector of the face on the left-hand side of the FEdge.

Type :

mathutils.Vector

normal_right 

The normal vector of the face on the right-hand side of the FEdge. When the FEdge is a border there is no Face on its right, so it carries no normal.

Type :

mathutils.Vector

class freestyle.types. FEdgeSmooth 

Class hierarchy: Interface1D > FEdge > FEdgeSmooth

Describes a smooth edge. Edges of this sort usually cut straight across a face of the input mesh and may be a silhouette, a ridge or valley, or a suggestive contour.

__init__ ( ) 

__init__ ( brother )

__init__ ( first_vertex , second_vertex )

Constructs an FEdgeSmooth using the default constructor, the copy constructor, or from a pair of SVertex.

Parameters :

- brother (FEdgeSmooth) – An FEdgeSmooth object.

- first_vertex (SVertex) – The first SVertex object.

- second_vertex (SVertex) – The second SVertex object.

face_mark 

The face mark of the face that this FEdge cuts across.

Type :

bool

material 

The material of the face that this FEdge cuts across.

Type :

Material

material_index 

The material index of the face that this FEdge cuts across.

Type :

int

normal 

The normal vector of the face that this FEdge cuts across.

Type :

mathutils.Vector

class freestyle.types. Id 

Represents an object Id.

__init__ ( brother ) 

__init__ ( first = 0 , second = 0 )

Assembles the Id either from a pair of numbers or, via the copy constructor, from another Id.

Parameters :

- brother (Id :arg first: The first number.) – An Id object.

- second ( int ) – The second number.

first 

The first number making up the Id.

Type :

int

second 

The second number making up the Id.

Type :

int

class freestyle.types. IntegrationType 

Class hierarchy: int > IntegrationType

The set of integration approaches available for collapsing into one value the collection of values gathered from each 0D element of a 1D element:

- IntegrationType.MEAN: The 1D element's value is taken as the average of the values gathered from the 0D elements.

- IntegrationType.MIN: The 1D element's value is taken as the smallest of the values gathered from the 0D elements.

- IntegrationType.MAX: The 1D element's value is taken as the largest of the values gathered from the 0D elements.

- IntegrationType.FIRST: The 1D element's value is taken from the first of the values gathered from the 0D elements.

- IntegrationType.LAST: The 1D element's value is taken from the last of the values gathered from the 0D elements.

class freestyle.types. Interface0D 

Serves as the parent type for every 0D element.

__init__ ( ) 

Default constructor.

get_fedge ( inter ) 

Hands back the FEdge sitting between this 0D element and the one passed in as the argument.

Parameters :

inter (Interface0D) – A 0D element.

Returns :

The FEdge lying between the two 0D elements.

Return type :

FEdge

id 

The Id of this 0D element.

Type :

Id

name 

The name string carried by this 0D element.

Type :

str

nature 

The nature of this 0D element.

Type :

Nature

point_2d 

The 2D point of this 0D element.

Type :

mathutils.Vector

point_3d 

The 3D point of this 0D element.

Type :

mathutils.Vector

projected_x 

The X coordinate of this 0D element's projected 3D point.

Type :

float

projected_y 

The Y coordinate of this 0D element's projected 3D point.

Type :

float

projected_z 

The Z coordinate of this 0D element's projected 3D point.

Type :

float

class freestyle.types. Interface0DIterator 

Class hierarchy: Iterator > Interface0DIterator

Supplies an iterator that runs over Interface0D elements. Such an iterator is always handed back from a 1D element.

__init__ ( brother ) 

__init__ ( it )

Constructs a nested Interface0DIterator from either the copy constructor or the constructor accepting a Function0D argument.

Parameters :

- brother (Interface0DIterator) – An Interface0DIterator object.

- it (SVertexIterator | CurvePointIterator | StrokeVertexIterator) – An iterator object to be nested.

at_last 

Set to True while the iterator sits on the final valid element. To test the opposite end (the first valid element), check it.is_begin instead.

Type :

bool

object 

Whatever 0D object this iterator is sitting on right now. Keep in mind it may actually be an instance of an Interface0D subclass; for example, when the iterator originated from the Stroke class's vertices_begin() method, the .object property gives back a StrokeVertex object.

Type :

Interface0D or one of its subclasses.

t 

The curvilinear abscissa of the current point.

Type :

float

u 

The point parameter at the current point in the 1D element (0 <= u <= 1).

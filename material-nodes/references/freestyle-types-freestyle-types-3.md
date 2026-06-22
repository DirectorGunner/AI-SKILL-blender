# Freestyle Types Freestyle Types (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

name ( str ) – The name of the attribute.

Returns :

True if the attribute is available.

Return type :

bool

has_attribute_vec2 ( name ) 

Tests whether the attribute name of two-dimensional vector type exists.

Parameters :

name ( str ) – The name of the attribute.

Returns :

True if the attribute is available.

Return type :

bool

has_attribute_vec3 ( name ) 

Tests whether the attribute name of three-dimensional vector type exists.

Parameters :

name ( str ) – The name of the attribute.

Returns :

True if the attribute is available.

Return type :

bool

set_attribute_real ( name , value ) 

Registers a user-defined attribute of float type. When no attribute carries that name yet, it gets created; otherwise the fresh value overwrites the previous one.

Parameters :

- name ( str ) – The name of the attribute.

- value ( float ) – The attribute value.

set_attribute_vec2 ( name , value ) 

Registers a user-defined attribute of two-dimensional vector type. When no attribute carries that name yet, it gets created; otherwise the fresh value overwrites the previous one.

Parameters :

- name ( str ) – The name of the attribute.

- value (mathutils.Vector | tuple[float, float, float] | list[float]) – The attribute value.

set_attribute_vec3 ( name , value ) 

Registers a user-defined attribute of three-dimensional vector type. When no attribute carries that name yet, it gets created; otherwise the fresh value overwrites the previous one.

Parameters :

- name ( str ) – The name of the attribute.

- value (mathutils.Vector | tuple[float, float, float] | list[float]) – The attribute value as a 3D vector.

alpha 

Alpha component of the stroke color.

Type :

float

color 

RGB components of the stroke color.

Type :

mathutils.Color

thickness 

The right and left parts of the stroke thickness. Following the stroke, the right (left) part is the thickness lying to the right (left) of the vertex.

Type :

mathutils.Vector

visible 

The visibility flag, True whenever the StrokeVertex can be seen.

Type :

bool

class freestyle.types. StrokeShader 

Serves as the parent type for stroke shaders. Every stroke shader has to derive from this class and override the shade() method. A StrokeShader exists to alter stroke attributes such as thickness, color, geometry, texture, blending mode, and the like. The usual approach is to walk the Stroke's stroke vertices and adjust each one's StrokeAttribute. Below is a code example showing such a loop:

`\text
it = ioStroke.strokeVerticesBegin()
while not it.is_end:
att = it.object.attribute
### perform here any attribute modification
it.increment()
`

__init__ ( ) 

Default constructor.

shade ( stroke ) 

The shading method. Must be overloaded by inherited classes.

Parameters :

stroke (Stroke) – A Stroke object.

name 

The name of the stroke shader.

Type :

str

class freestyle.types. StrokeVertex 

Class hierarchy: Interface0D > CurvePoint > StrokeVertex

Represents a stroke vertex.

__init__ ( ) 

__init__ ( brother )

__init__ ( first_vertex , second_vertex , t3d )

__init__ ( point )

__init__ ( svertex )

__init__ ( svertex , attribute )

Constructs a StrokeVertex with the default constructor, the copy constructor, from a pair of StrokeVertex plus an interpolation parameter, from a CurvePoint, from an SVertex, or from an SVertex together with a StrokeAttribute object.

Parameters :

- brother (StrokeVertex) – A StrokeVertex object.

- first_vertex (StrokeVertex) – The first StrokeVertex.

- second_vertex (StrokeVertex) – The second StrokeVertex.

- t3d ( float ) – An interpolation parameter.

- point (CurvePoint) – A CurvePoint object.

- svertex (SVertex) – An SVertex object.

- svertex – An SVertex object.

- attribute (StrokeAttribute) – A StrokeAttribute object.

attribute 

StrokeAttribute for this StrokeVertex.

Type :

StrokeAttribute

curvilinear_abscissa 

Curvilinear abscissa of this StrokeVertex in the Stroke.

Type :

float

point 

2D point coordinates.

Type :

mathutils.Vector

stroke_length 

Stroke length, though it is merely a figure cached by the StrokeVertex and altering it leaves the actual stroke length untouched.

Type :

float

u 

Curvilinear abscissa of this StrokeVertex in the Stroke.

Type :

float

class freestyle.types. StrokeVertexIterator 

Class hierarchy: Iterator > StrokeVertexIterator

Provides an iterator built to traverse the StrokeVertex of a Stroke. You get a StrokeVertexIterator instance from a Stroke by calling iter(), stroke_vertices_begin() or stroke_vertices_begin(). It covers the very same vertices an Interface0DIterator would; the distinction lies in object access, since an Interface0DIterator only reaches an Interface0D while you may need the more specific StrokeVertex type. For that case a StrokeVertexIterator is the right choice. To call UnaryFuntion0D-type functions, a StrokeVertexIterator can be turned into an Interface0DIterator by calling Interface0DIterator(it).

__init__ ( ) 

__init__ ( brother )

Constructs a StrokeVertexIterator with either the default constructor or the copy constructor.

Parameters :

brother (StrokeVertexIterator) – A StrokeVertexIterator object.

decremented ( ) 

Hands back a copy of a StrokeVertexIterator that has been stepped back.

Returns :

A StrokeVertexIterator pointing the previous StrokeVertex.

Return type :

StrokeVertexIterator

incremented ( ) 

Hands back a copy of a StrokeVertexIterator that has been stepped forward.

Returns :

A StrokeVertexIterator pointing the next StrokeVertex.

Return type :

StrokeVertexIterator

reversed ( ) 

Hands back a StrokeVertexIterator that runs through the stroke vertices in reverse order.

Returns :

A StrokeVertexIterator traversing stroke vertices backward.

Return type :

StrokeVertexIterator

at_last 

Set to True while the iterator sits on the final valid element. To test the opposite end (the first valid element), check it.is_begin instead.

Type :

bool

object 

Whatever StrokeVertex this iterator is sitting on right now.

Type :

StrokeVertex

t 

The curvilinear abscissa of the current point.

Type :

float

u 

The point parameter at the current point in the stroke (0 <= u <= 1).

Type :

float

class freestyle.types. TVertex 

Class hierarchy: Interface0D > ViewVertex > TVertex

Represents a T vertex, that is, a crossing of two edges. It references two SVertex and four ViewEdges. Of those ViewEdges, two are front and two are back, and a front edge conceals part of a back edge. Among the back pair, one carries invisibility N while the other carries invisibility N+1.

__init__ ( ) 

Default constructor.

get_mate ( viewedge ) 

Hands back the mate edge of the ViewEdge passed in. Given frontEdgeA the result is frontEdgeB; given frontEdgeB the result is frontEdgeA; the back edges work the same way.

Parameters :

viewedge (ViewEdge) – A ViewEdge object.

Returns :

The mate edge of the given ViewEdge.

Return type :

ViewEdge

get_svertex ( fedge ) 

Hands back whichever of the two SVertex is part of the supplied FEdge.

Parameters :

fedge (FEdge) – An FEdge object.

Returns :

The SVertex belonging to the given FEdge.

Return type :

SVertex

back_svertex 

The SVertex positioned further from the viewpoint.

Type :

SVertex

front_svertex 

The SVertex positioned nearer to the viewpoint.

Type :

SVertex

id 

The Id of this TVertex.

Type :

Id

class freestyle.types. UnaryFunction0D 

Serves as the parent type for unary functions (functors) operating on Interface0DIterator. A unary function gets invoked by calling __call__() on an Interface0DIterator. Within Python, the particular UnaryFunction0D subclass you use depends on what type the functor returns; for instance, to write a function returning a double you would derive from UnaryFunction0DDouble. The UnaryFunction0D subclasses on offer are:

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

name 

The name of the unary 0D function.

Type :

str

class freestyle.types. UnaryFunction0DDouble 

Class hierarchy: UnaryFunction0D > UnaryFunction0DDouble

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a float value.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DEdgeNature 

Class hierarchy: UnaryFunction0D > UnaryFunction0DEdgeNature

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a Nature object.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DFloat 

Class hierarchy: UnaryFunction0D > UnaryFunction0DFloat

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a float value.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DId 

Class hierarchy: UnaryFunction0D > UnaryFunction0DId

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back an Id object.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DMaterial 

Class hierarchy: UnaryFunction0D > UnaryFunction0DMaterial

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a Material object.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DUnsigned 

Class hierarchy: UnaryFunction0D > UnaryFunction0DUnsigned

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back an int value.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DVec2f 

Class hierarchy: UnaryFunction0D > UnaryFunction0DVec2f

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a 2D vector.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DVec3f 

Class hierarchy: UnaryFunction0D > UnaryFunction0DVec3f

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a 3D vector.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DVectorViewShape 

Class hierarchy: UnaryFunction0D > UnaryFunction0DVectorViewShape

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a list of ViewShape objects.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction0DViewShape 

Class hierarchy: UnaryFunction0D > UnaryFunction0DViewShape

Serves as the parent type for unary functions (functors) operating on Interface0DIterator and giving back a ViewShape object.

__init__ ( ) 

Default constructor.

class freestyle.types. UnaryFunction1D 

Serves as the parent type for unary functions (functors) operating on Interface1D. A unary function gets invoked by calling __call__() on an Interface1D. Within Python, the particular UnaryFunction1D subclass you use depends on what type the functor returns; for instance, to write a function returning a double you would derive from UnaryFunction1DDouble. The UnaryFunction1D subclasses on offer are:

- UnaryFunction1DDouble

- UnaryFunction1DEdgeNature

- UnaryFunction1DFloat

- UnaryFunction1DUnsigned

- UnaryFunction1DVec2f

- UnaryFunction1DVec3f

- UnaryFunction1DVectorViewShape

- UnaryFunction1DVoid

name 

The name of the unary 1D function.

Type :

str

class freestyle.types. UnaryFunction1DDouble 

Class hierarchy: UnaryFunction1D > UnaryFunction1DDouble

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a float value.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DEdgeNature 

Class hierarchy: UnaryFunction1D > UnaryFunction1DEdgeNature

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a Nature object.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DFloat 

Class hierarchy: UnaryFunction1D > UnaryFunction1DFloat

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a float value.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DUnsigned 

Class hierarchy: UnaryFunction1D > UnaryFunction1DUnsigned

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back an int value.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DVec2f 

Class hierarchy: UnaryFunction1D > UnaryFunction1DVec2f

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a 2D vector.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DVec3f 

Class hierarchy: UnaryFunction1D > UnaryFunction1DVec3f

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a 3D vector.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DVectorViewShape 

Class hierarchy: UnaryFunction1D > UnaryFunction1DVectorViewShape

Serves as the parent type for unary functions (functors) operating on Interface1D and giving back a list of ViewShape objects.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function with either the default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryFunction1DVoid 

Class hierarchy: UnaryFunction1D > UnaryFunction1DVoid

Serves as the parent type for unary functions (functors) operating on Interface1D.

__init__ ( ) 

__init__ ( integration_type )

Constructs a unary 1D function from either a default constructor or the integration method supplied as an argument.

Parameters :

integration_type (IntegrationType) – An integration method.

integration_type 

The integration method.

Type :

IntegrationType

class freestyle.types. UnaryPredicate0D 

Serves as the parent type for unary predicates operating on Interface0DIterator. A UnaryPredicate0D is a functor that checks a condition on an Interface0DIterator and reports true or false according to whether that condition holds. You use a UnaryPredicate0D by calling its __call__() method, and any derived class must override __call__().

__init__ ( ) 

Default constructor.

__call__ ( it ) 

Must be overload by inherited classes.

Parameters :

it (Interface0DIterator) – The Interface0DIterator pointing onto the Interface0D at
which we wish to evaluate the predicate.

Returns :

True if the condition is satisfied, false otherwise.

Return type :

bool

name 

The name of the unary 0D predicate.

Type :

str

class freestyle.types. UnaryPredicate1D 

Serves as the parent type for unary predicates operating on Interface1D. A UnaryPredicate1D is a functor that checks a condition on an Interface1D and reports true or false according to whether that condition holds. You use a UnaryPredicate1D by calling its __call__() method, and any derived class must override __call__().

__init__ ( ) 

Default constructor.

__call__ ( inter ) 

Must be overload by inherited classes.

Parameters :

inter (Interface1D) – The Interface1D on which we wish to evaluate the predicate.

Returns :

True if the condition is satisfied, false otherwise.

Return type :

bool

name 

The name of the unary 1D predicate.

Type :

str

class freestyle.types. ViewEdge 

Class hierarchy: Interface1D > ViewEdge

Represents a ViewEdge, an edge belonging to the image graph. It joins a pair of ViewVertex objects and is formed by stringing together a set of FEdges.

__init__ ( ) 

__init__ ( brother )

Constructs a ViewEdge with the default constructor or the copy constructor.

Parameters :

brother (ViewEdge) – A ViewEdge object.

update_fedges ( ) 

Points the Viewedge of every embedded fedge at this one.

chaining_time_stamp 

The time stamp of this ViewEdge.

Type :

int

first_fedge 

The first FEdge that makes up this ViewEdge.

Type :

FEdge

first_viewvertex 

The first ViewVertex.

Type :

ViewVertex

id 

The Id of this ViewEdge.

Type :

Id

is_closed 

Set to True when this ViewEdge closes back on itself into a loop.

Type :

bool

last_fedge 

The last FEdge that makes up this ViewEdge.

Type :

FEdge

last_viewvertex 

The second ViewVertex.

Type :

ViewVertex

nature 

The nature of this ViewEdge.

Type :

Nature

occludee 

The shape hidden by the ViewShape that owns this ViewEdge. When nothing is occluded, this property is None.

Type :

ViewShape

qi 

The quantitative invisibility.

Type :

int

viewshape 

The ViewShape that this ViewEdge is part of.

Type :

ViewShape

class freestyle.types. ViewEdgeIterator 

Class hierarchy: Iterator > ViewEdgeIterator

Serves as the parent type for iterators that run over the ViewEdges of the ViewMap Graph. Essentially this class's increment() operator is responsible for deciding, while sitting on a particular ViewEdge, which ViewEdge to move to next.

__init__ ( begin = None , orientation = True ) 

__init__ ( brother )

Constructs a ViewEdgeIterator either from a starting ViewEdge along with its orientation, or via the copy constructor.

Parameters :

- begin (ViewEdge | None) – The ViewEdge from where to start the iteration.

- orientation ( bool ) – If true, we'll look for the next ViewEdge among
the ViewEdges that surround the ending ViewVertex of begin. If
false, we'll search over the ViewEdges surrounding the ending
ViewVertex of begin.

- brother (ViewEdgeIterator) – A ViewEdgeIterator object.

change_orientation ( ) 

Flips the orientation now in effect.

begin 

The first ViewEdge used for the iteration.

Type :

ViewEdge

current_edge 

Whatever ViewEdge this iterator is sitting on right now.

Type :

ViewEdge

object 

Whatever ViewEdge this iterator is sitting on right now.

Type :

ViewEdge

orientation 

The orientation of the ViewEdge pointed at during iteration. When true, the iterator hunts for the next ViewEdge among those circling the ending ViewVertex of the "begin" ViewEdge; when false, it scans the ViewEdges around the ending ViewVertex of the "begin" ViewEdge.

Type :

bool

class freestyle.types. ViewMap 

Represents the ViewMap.

__init__ ( ) 

Default constructor.

get_closest_fedge ( x , y ) 

Fetches the FEdge closest to the 2D point given as the arguments.

Parameters :

- x ( float ) – X coordinate of a 2D point.

- y ( float ) – Y coordinate of a 2D point.

Returns :

The FEdge nearest to the specified 2D point.

Return type :

FEdge

get_closest_viewedge ( x , y ) 

Fetches the ViewEdge closest to the 2D point given as the arguments.

Parameters :

- x ( float ) – X coordinate of a 2D point.

- y ( float ) – Y coordinate of a 2D point.

Returns :

The ViewEdge nearest to the specified 2D point.

Return type :

ViewEdge

scene_bbox 

The 3D bounding box of the scene.

Type :

BBox

class freestyle.types. ViewShape 

Brings together the ViewMap elements (namely ViewVertex and ViewEdge) that all stem from one and the same input shape.

__init__ ( ) 

__init__ ( brother )

__init__ ( sshape )

Constructs a ViewShape with the default constructor, the copy constructor, or from an SShape.

Parameters :

- brother (ViewShape) – A ViewShape object.

- sshape (SShape) – An SShape object.

add_edge ( edge ) 

Appends a ViewEdge onto the list of ViewEdge objects.

Parameters :

edge (ViewEdge) – A ViewEdge object.

add_vertex ( vertex ) 

Appends a ViewVertex onto the list of ViewVertex objects.

Parameters :

vertex (ViewVertex) – A ViewVertex object.

edges 

The list of ViewEdge objects held within this ViewShape.

Type :

List of ViewEdge

id 

The Id of this ViewShape.

Type :

Id

library_path 

The library path of the ViewShape.

Type :

str, or None if the ViewShape is not part of a library.

name 

The name of the ViewShape.

Type :

str

sshape 

The SShape that this ViewShape is built on top of.

Type :

SShape

vertices 

The list of ViewVertex objects held within this ViewShape.

Type :

List of ViewVertex

class freestyle.types. ViewVertex 

Class hierarchy: Interface0D > ViewVertex

Represents a view vertex. A view vertex is a feature vertex matching a point of the image graph where an edge's traits (such as nature and visibility) may shift. A ViewVertex comes in two forms: a TVertex marks where two ViewEdges cross, whereas a NonTVertex maps onto one of the original input mesh's own vertices (as happens with features like corners). The class therefore branches into two subclasses, TVertex and NonTVertex.

edges_begin ( ) 

Hands back an iterator over the ViewEdges arriving at or leaving this ViewVertex, sitting on the list's first ViewEdge. The orientedViewEdgeIterator lets you walk these ViewEdges in CCW order and read the orientation (incoming or outgoing) of each one.

Returns :

An orientedViewEdgeIterator pointing to the first ViewEdge.

Return type :

orientedViewEdgeIterator

edges_end ( ) 

Hands back an orientedViewEdgeIterator over the ViewEdges around this ViewVertex, sitting just past the last ViewEdge.

Returns :

An orientedViewEdgeIterator pointing after the last ViewEdge.

Return type :

orientedViewEdgeIterator

edges_iterator ( edge ) 

Hands back an orientedViewEdgeIterator sitting on the ViewEdge supplied as the argument.

Parameters :

edge (ViewEdge) – A ViewEdge object.

Returns :

An orientedViewEdgeIterator pointing to the given ViewEdge.

Return type :

orientedViewEdgeIterator

nature 

The nature of this ViewVertex.

Type :

Nature

class freestyle.types. orientedViewEdgeIterator 

Class hierarchy: Iterator > orientedViewEdgeIterator

Provides an iterator over the oriented ViewEdges surrounding a ViewVertex. It supports a CCW walk within the image plane. An orientedViewEdgeIterator instance can come only from a ViewVertex, obtained by calling edges_begin() or edges_end().

__init__ ( ) 

__init__ ( iBrother )

Constructs an orientedViewEdgeIterator with either the default constructor or the copy constructor.

Parameters :

iBrother (orientedViewEdgeIterator) – An orientedViewEdgeIterator object.

object 

The oriented ViewEdge this iterator is sitting on right now, given as a tuple pairing the pointed ViewEdge with a boolean. A true boolean marks the ViewEdge as incoming.

Type :

tuple[ViewEdge, bool]

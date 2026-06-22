# Freestyle Types Freestyle Types (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Type :

float

class freestyle.types. Interface1D 

Serves as the parent type for every 1D element.

__init__ ( ) 

Default constructor.

points_begin ( t = 0.0 ) 

Hands back an iterator over the Interface1D points that starts on the first point. Unlike vertices_begin(), this lets you step through the 1D element's points at whatever sampling you choose, since a virtual point is spawned on every iteration.

Parameters :

t ( float ) – The sampling rate to use when stepping across this 1D
element's points.

Returns :

An Interface0DIterator pointing to the first point.

Return type :

Interface0DIterator

points_end ( t = 0.0 ) 

Hands back an iterator over the Interface1D points that sits just past the last point. Unlike vertices_end(), this lets you step through the 1D element's points at whatever sampling you choose, since a virtual point is spawned on every iteration.

Parameters :

t ( float ) – The sampling rate to use when stepping across this 1D
element's points.

Returns :

An Interface0DIterator pointing after the last point.

Return type :

Interface0DIterator

vertices_begin ( ) 

Hands back an iterator over the Interface1D vertices that starts on the first vertex.

Returns :

An Interface0DIterator pointing to the first vertex.

Return type :

Interface0DIterator

vertices_end ( ) 

Hands back an iterator over the Interface1D vertices that sits just past the last vertex.

Returns :

An Interface0DIterator pointing after the last vertex.

Return type :

Interface0DIterator

id 

The Id of this Interface1D.

Type :

Id

length_2d 

The 2D length of this Interface1D.

Type :

float

name 

The name string carried by the 1D element.

Type :

str

nature 

The nature of this Interface1D.

Type :

Nature

time_stamp 

This 1D element's time stamp, used chiefly during selection.

Type :

int

class freestyle.types. Iterator 

Serves as the parent type for defining iterators.

__init__ ( ) 

Default constructor.

decrement ( ) 

Moves the iterator back onto the preceding element.

increment ( ) 

Moves the iterator forward onto the following element.

is_begin 

Set to True while the iterator sits on the first element.

Type :

bool

is_end 

Set to True while the iterator sits on the last element.

Type :

bool

name 

The name string carried by this iterator.

Type :

str

class freestyle.types. Material 

Represents a material.

__init__ ( ) 

__init__ ( brother )

__init__ ( line , diffuse , ambient , specular , emission , shininess , priority )

Constructs a FrsMaterial with the default constructor, the copy constructor, or an overloaded constructor.

Parameters :

- brother (Material) – A Material object to be used as a copy constructor.

- line (mathutils.Vector | tuple[float, float, float, float] | list[float]) – The line color.

- diffuse – The diffuse color.

- ambient (mathutils.Vector | tuple[float, float, float, float] | list[float]) – The ambient color.

- specular (mathutils.Vector | tuple[float, float, float, float] | list[float]) – The specular color.

- emission (mathutils.Vector | tuple[float, float, float, float] | list[float]) – The emissive color.

- shininess ( float ) – The shininess coefficient.

- priority ( int ) – The line color priority.

ambient 

The material's ambient color given as RGBA components.

Type :

mathutils.Color

diffuse 

The material's diffuse color given as RGBA components.

Type :

mathutils.Vector

emission 

The material's emissive color given as RGBA components.

Type :

mathutils.Color

line 

The material's line color given as RGBA components.

Type :

mathutils.Vector

priority 

The material's line color priority.

Type :

int

shininess 

The material's shininess coefficient.

Type :

float

specular 

The material's specular color given as RGBA components.

Type :

mathutils.Vector

class freestyle.types. MediumType 

Class hierarchy: int > MediumType

The selection of blending modes provided to mimic how media interact with one another:

- Stroke.`DRY_MEDIUM`: Mimics a dry tool like a Pencil or Charcoal.

- Stroke.`HUMID_MEDIUM`: Mimics ink painting, blending by subtracting color.

- Stroke.`OPAQUE_MEDIUM`: Mimics an opaque tool such as oil or spray.

class freestyle.types. Nature 

Class hierarchy: int > Nature

The range of possible natures for the 0D and 1D elements of the ViewMap.

Vertex natures:

- Nature.POINT: True for any 0D element.

- Nature.`S_VERTEX`: True for SVertex.

- Nature.`VIEW_VERTEX`: True for ViewVertex.

- Nature.`NON_T_VERTEX`: True for NonTVertex.

- Nature.`T_VERTEX`: True for TVertex.

- Nature.CUSP: True for CUSP.

Edge natures:

- Nature.`NO_FEATURE`: True for non feature edges (always false for 1D
elements of the ViewMap).

- Nature.SILHOUETTE: True for silhouettes.

- Nature.BORDER: True for borders.

- Nature.CREASE: True for creases.

- Nature.RIDGE: True for ridges.

- Nature.VALLEY: True for valleys.

- Nature.`SUGGESTIVE_CONTOUR`: True for suggestive contours.

- Nature.`MATERIAL_BOUNDARY`: True for edges at material boundaries.

- Nature.`EDGE_MARK`: True for edges having user-defined edge marks.

class freestyle.types. Noise 

Supplies Perlin noise capabilities.

__init__ ( seed = -1 ) 

Constructs a Noise object. The seed argument is optional. Any seed of zero or more is fed into random number generation as the seed; otherwise the current time is used in its place.

Parameters :

seed ( int ) – Seed for random number generation.

Undocumented, consider contributing.

smoothNoise1 ( v ) 

Hands back a smooth noise value computed for a 1D element.

Parameters :

v ( float ) – One-dimensional sample point.

Returns :

A smooth noise value.

Return type :

float

smoothNoise2 ( v ) 

Hands back a smooth noise value computed for a 2D element.

Parameters :

v (mathutils.Vector | tuple[float, float] | list[float]) – Two-dimensional sample point.

Returns :

A smooth noise value.

Return type :

float

smoothNoise3 ( v ) 

Hands back a smooth noise value computed for a 3D element.

Parameters :

v (mathutils.Vector | tuple[float, float, float] | list[float]) – Three-dimensional sample point.

Returns :

A smooth noise value.

Return type :

float

turbulence1 ( v , freq , amp , oct = 4 ) 

Hands back a noise value computed for a 1D element.

Parameters :

- v ( float ) – One-dimensional sample point.

- freq ( float ) – Noise frequency.

- amp ( float ) – Amplitude.

- oct ( int ) – Number of octaves.

Returns :

A noise value.

Return type :

float

turbulence2 ( v , freq , amp , oct = 4 ) 

Hands back a noise value computed for a 2D element.

Parameters :

- v (mathutils.Vector | tuple[float, float] | list[float]) – Two-dimensional sample point.

- freq ( float ) – Noise frequency.

- amp ( float ) – Amplitude.

- oct ( int ) – Number of octaves.

Returns :

A noise value.

Return type :

float

turbulence3 ( v , freq , amp , oct = 4 ) 

Hands back a noise value computed for a 3D element.

Parameters :

- v (mathutils.Vector | tuple[float, float, float] | list[float]) – Three-dimensional sample point.

- freq ( float ) – Noise frequency.

- amp ( float ) – Amplitude.

- oct ( int ) – Number of octaves.

Returns :

A noise value.

Return type :

float

Undocumented, consider contributing.

class freestyle.types. NonTVertex 

Class hierarchy: Interface0D > ViewVertex > NonTVertex

A view vertex tied to a single SVertex, used for corners, cusps, and similar features. It may be linked to two or more view edges.

__init__ ( ) 

__init__ ( svertex )

Constructs a NonTVertex with the default constructor or from an SVertex.

Parameters :

svertex (SVertex) – An SVertex object.

svertex 

The SVertex that this NonTVertex is built on top of.

Type :

SVertex

class freestyle.types. Operators 

Holds the operators a style module relies on. They come in five categories: selection, chaining, splitting, sorting, and creation. The user steers all of them through functors, predicates, and shaders supplied as arguments.

static bidirectional_chain ( it , pred ) 

static bidirectional_chain ( it )

Assembles a collection of chains out of the present set of ViewEdges. Any ViewEdge in the current list may seed a fresh chain. The chaining operator then walks the ViewMap's ViewEdges with the iterator the user provides. Since it uses both the increment and decrement operators, the walk runs in both directions. The operator relies on a ChainingIterator that carries the chaining rules; that iterator is what can be configured to chain only selected edges or to avoid revisiting a ViewEdge during chaining. Every time a ViewEdge joins a chain its chaining time stamp goes up, which lets you tally how many chains a given ViewEdge belongs to.

Parameters :

- it (ChainingIterator) – A ChainingIterator covering the ViewMap's ViewEdges; it
holds the chaining rule.

- pred (UnaryPredicate1D) – A ViewEdge predicate giving the stopping condition.
You can leave it out: when the iterator definition already bakes in the stopping
criterion, no separate one is needed here.

static chain ( it , pred , modifier ) 

static chain ( it , pred )

Assembles a collection of chains out of the present set of ViewEdges. Each ViewEdge in the current list seeds a fresh chain. The chaining operator then walks the ViewMap's ViewEdges with the iterator the user provides. Since it uses only the increment operator, the walk runs in a single direction.

Parameters :

- it (ViewEdgeIterator) – An iterator covering the ViewMap's ViewEdges; it
holds the chaining rule.

- pred (UnaryPredicate1D) – A ViewEdge predicate giving the
stopping condition.

- modifier (UnaryFunction1DVoid) – A function accepting a ViewEdge that adjusts
the state of the ViewEdge being processed; bumping the timestamp is the
classic example of such a modifier. Omit this argument and the time stamp is
handled for you automatically.

static create ( pred , shaders ) 

Builds and shades the strokes from the present set of chains. An optional predicate may be supplied to filter the chains down.

Parameters :

- pred (UnaryPredicate1D) – The predicate a chain has to satisfy before it can
become a stroke.

- shaders (list[StrokeShader]) – The collection of shaders applied to shade the strokes.

static get_chain_from_index ( i ) 

Hands back the Chain found at the given index within the present set of Chains.

Parameters :

i ( int ) – index (0 <= i < Operators.get_chains_size()).

Returns :

The Chain object.

Return type :

Chain

static get_chains_size ( ) 

Hands back how many Chains there are.

Returns :

The number of Chains.

Return type :

int

static get_stroke_from_index ( i ) 

Hands back the Stroke found at the given index within the present set of Strokes.

Parameters :

i ( int ) – index (0 <= i < Operators.get_strokes_size()).

Returns :

The Stroke object.

Return type :

Stroke

static get_strokes_size ( ) 

Hands back how many Strokes there are.

Returns :

The number of Strokes.

Return type :

int

static get_view_edges_size ( ) 

Hands back how many ViewEdges there are.

Returns :

The number of ViewEdges.

Return type :

int

static get_viewedge_from_index ( i ) 

Hands back the ViewEdge found at the given index within the present set of ViewEdges.

Parameters :

i ( int ) – index (0 <= i < Operators.get_view_edges_size()).

Returns :

The ViewEdge object.

Return type :

ViewEdge

static recursive_split ( func , pred_1d , sampling = 0.0 ) 

static recursive_split ( func , pred_0d , pred_1d , sampling = 0.0 )

Breaks up the present set of chains recursively. Each chain's points are scanned (at the chosen sampling) to locate the point that minimizes a given function; the chain is cut in two there, and both halves are then handled the same way. A 1D predicate, stating a stopping condition on the chain about to be handled, governs how deep the recursion goes.

You may additionally hand in a 0D predicate to pre-filter which points are eligible for splitting. Any point that fails the 0D predicate is excluded from the search for the minimum.

Parameters :

- func (UnaryFunction0DDouble) – The Unary Function evaluated at each point of the chain.
The splitting point is the point minimizing this function.

- pred_0d (UnaryPredicate0D) – A 0D predicate that narrows down which points
are eligible to be split on. Often, say, you would prefer a chain to break near
its center rather than at either tip; a 0D predicate keyed on the curvilinear
abscissa is how you impose constraints of that sort.

- pred_1d (UnaryPredicate1D) – A 1D predicate stating when recursion should halt.
Before any curve is cut, this predicate runs against it; once pred_1d(chain)
comes back true, that curve is left whole and split no further.

- sampling ( float ) – The spacing at which the chain is sampled while the
predicates are evaluated. (No real resampling happens; a virtual point merely
advances along the curve at this spacing.)

static reset ( delete_strokes = True ) 

Returns the line stylization pipeline to its starting state. With delete_strokes left as False, the stroke-creation results pile up instead of being cleared.

Parameters :

delete_strokes ( bool ) – Whether the strokes presently held should be discarded.

static select ( pred ) 

Picks out the ViewMap's ViewEdges that satisfy a given condition.

Parameters :

pred (UnaryPredicate1D) – The predicate that states this condition.

static sequential_split ( starting_pred , stopping_pred , sampling = 0.0 ) 

static sequential_split ( pred , sampling = 0.0 )

Cuts every chain in the present set of chains one after another. A chain's points are handled in order (at the chosen sampling). The opening point of the original chain becomes the opening point of one of the chains produced. Splitting stops once no further chain can begin.

Tip

Supplying both a starting and a stopping predicate lets the resulting chains overlap rather than partition one another.

Parameters :

- starting_pred (UnaryPredicate0D) – A per-point predicate carrying the start
condition. Whenever it holds true, a fresh chain is opened.

- stopping_pred (UnaryPredicate0D) – A per-point predicate carrying the stop
condition. The chain closes the moment this predicate holds true.

- pred (UnaryPredicate0D) – A per-point predicate carrying the split condition.
Whenever it holds true, the chain breaks in two, so the chains produced amount
to a partition of the chain you started with.

- sampling ( float ) – The spacing at which the chain is sampled while the
predicates are evaluated. (No real resampling happens; a virtual point merely
advances along the curve at this spacing.)

static sort ( pred ) 

Orders the present set of chains (or viewedges) by the comparison predicate handed in as the argument.

Parameters :

pred (BinaryPredicate1D) – The binary predicate driving the comparison.

class freestyle.types. SShape 

Represents a feature shape. It is the collection of feature elements drawn from one identified input shape.

__init__ ( ) 

__init__ ( brother )

Constructs an SShape with either the default constructor or the copy constructor.

Parameters :

brother (SShape) – An SShape object.

add_edge ( edge ) 

Appends an FEdge onto the list of FEdges.

Parameters :

edge (FEdge) – An FEdge object.

add_vertex ( vertex ) 

Appends an SVertex onto this Shape's list of SVertex. The SVertex's SShape attribute is also pointed at this SShape.

Parameters :

vertex (SVertex) – An SVertex object.

compute_bbox ( ) 

Compute the bbox of the SShape.

bbox 

The bounding box of the SShape.

Type :

BBox

edges 

The list of edges that make up this SShape.

Type :

List of FEdge

id 

The Id of this SShape.

Type :

Id

name 

The name of the SShape.

Type :

str

vertices 

The list of vertices that make up this SShape.

Type :

List of SVertex

class freestyle.types. SVertex 

Class hierarchy: Interface0D > SVertex

Represents a vertex of the embedding.

__init__ ( ) 

__init__ ( brother )

__init__ ( point_3d , id )

Constructs an SVertex with the default constructor, the copy constructor, or the overload that builds one from a set of 3D coordinates plus an Id.

Parameters :

- brother (SVertex) – A SVertex object.

- point_3d (mathutils.Vector) – A three-dimensional vector.

- id (Id) – An Id object.

add_fedge ( fedge ) 

Appends an FEdge onto the list of edges leaving this SVertex.

Parameters :

fedge (FEdge) – An FEdge.

add_normal ( normal ) 

Adds a normal into the SVertex's collection of normals. Nothing happens if that same normal is already present.

Parameters :

normal (mathutils.Vector | tuple[float, float, float] | list[float]) – A three-dimensional vector.

curvatures 

Curvature data given as a seven-entry tuple (K1, e1, K2, e2, Kr, er, dKr). Here K1 and K2 are scalars holding the first (maximum) and second (minimum) principal curvatures at this SVertex; e1 and e2 are 3D vectors holding the first and second principal directions, that is, the directions within the normal plane where curvature reaches its largest and smallest values; and Kr, er, and dKr hold this SVertex's radial curvature, radial direction, and the derivative of the radial curvature.

Type :

tuple

id 

The Id of this SVertex.

Type :

Id

normals 

This Vertex's normals as a list. On a sharp surface an SVertex carries precisely one normal, whereas on a smooth surface it may carry any count of normals.

Type :

list of mathutils.Vector

normals_size 

How many distinct normals this SVertex has.

Type :

int

point_2d 

The SVertex's 3D coordinates after projection.

Type :

mathutils.Vector

point_3d 

The SVertex's 3D coordinates.

Type :

mathutils.Vector

viewvertex 

When this SVertex doubles as a ViewVertex, this property points at that ViewVertex; otherwise it is None.

Type :

ViewVertex

class freestyle.types. SVertexIterator 

Class hierarchy: Iterator > SVertexIterator

Provides an iterator over the SVertex of a ViewEdge. You obtain an SVertexIterator instance from a ViewEdge by calling verticesBegin() or verticesEnd().

__init__ ( ) 

__init__ ( brother )

__init__ ( vertex , begin , previous_edge , next_edge , t )

Constructs an SVertexIterator with the default constructor, the copy constructor,

or the overload that begins iterating from a given SVertex object vertex.

Parameters :

- brother (SVertexIterator) – An SVertexIterator object.

- vertex (SVertex) – The SVertex from which the iterator starts iteration.

- begin (SVertex) – The first SVertex of a ViewEdge.

- previous_edge (FEdge) – The previous FEdge coming to vertex.

- next_edge (FEdge) – The next FEdge going out from vertex.

- t ( float ) – The curvilinear abscissa at vertex.

object 

Whatever SVertex this iterator is sitting on right now.

Type :

SVertex

t 

The curvilinear abscissa of the current point.

Type :

float

u 

The point parameter at the current point in the 1D element (0 <= u <= 1).

Type :

float

class freestyle.types. Stroke 

Class hierarchy: Interface1D > Stroke

Represents a stroke. A stroke consists of a set of evenly spaced 2D vertices (StrokeVertex) whose arrangement forms the stroke's backbone geometry, with each such vertex setting the stroke's form and look at its own position.

Stroke ( ) 

Stroke ( brother )

Constructs a Stroke with the default constructor or the copy constructor.

compute_sampling ( n ) 

Works out the sampling required to end up with N vertices. Should the requested vertex count fall below the count already present, the existing sampling value is returned instead. (To take vertices away, call this class's RemoveVertex() method.)

Parameters :

n ( int ) – The number of stroke vertices we eventually want
in our Stroke.

Returns :

The sampling that must be used in the Resample(float)
method.

Return type :

float

insert_vertex ( vertex , next ) 

Places the StrokeVertex passed in into the Stroke just ahead of the point indicated by next. Length and curvilinear abscissa are refreshed accordingly.

Parameters :

- vertex (StrokeVertex) – The StrokeVertex to insert in the Stroke.

- next (StrokeVertexIterator) – A StrokeVertexIterator pointing to the StrokeVertex
before which vertex must be inserted.

remove_all_vertices ( ) 

Clears every vertex out of the Stroke.

remove_vertex ( vertex ) 

Takes the StrokeVertex passed in out of the Stroke. Length and curvilinear abscissa are refreshed accordingly.

Parameters :

vertex (StrokeVertex) – the StrokeVertex to remove from the Stroke.

resample ( n ) 

resample ( sampling )

Resamples the stroke through one of two routes, aiming to yield a stroke that keeps the same shape with fewer points.

Parameters :

- n ( int ) – Drives the stroke to wind up holding N points; concretely it tacks
on N minus vertices_size more, where vertices_size counts the points already
present. Whenever vertices_size is N or greater, nothing is resampled.

- sampling ( float ) – Resamples the stroke at the sampling value you supply.
Should that value undercut the current sampling value, the stroke is left as is.

stroke_vertices_begin ( t = 0.0 ) 

Hands back a StrokeVertexIterator sitting on the Stroke's first StrokeVertex. A sampling value may be passed to re-sample the Stroke on the fly when needed.

Parameters :

t ( float ) – The resampling value to apply to the Stroke. Supply 0 and no
resampling takes place.

Returns :

A StrokeVertexIterator pointing on the first StrokeVertex.

Return type :

StrokeVertexIterator

stroke_vertices_end ( ) 

Hands back a StrokeVertexIterator sitting just past the Stroke's last StrokeVertex.

Returns :

A StrokeVertexIterator pointing after the last StrokeVertex.

Return type :

StrokeVertexIterator

stroke_vertices_size ( ) 

Hands back how many StrokeVertex make up the Stroke.

Returns :

The number of stroke vertices.

Return type :

int

update_length ( ) 

Refreshes the Stroke's 2D length.

id 

The Id of this Stroke.

Type :

Id

length_2d 

The 2D length of the Stroke.

Type :

float

medium_type 

The MediumType in effect for this Stroke.

Type :

MediumType

texture_id 

The ID of the texture driving the marks system for this Stroke.

Type :

int

tips 

Set to True when this Stroke draws on a texture that has tips, and false otherwise.

Type :

bool

class freestyle.types. StrokeAttribute 

Holds the bundle of attributes attached to a StrokeVertex. The bundle keeps the color, alpha, and thickness values for a Stroke Vertex.

__init__ ( ) 

__init__ ( brother )

__init__ ( red , green , blue , alpha , thickness_right , thickness_left )

__init__ ( attribute1 , attribute2 , t )

Constructs a StrokeAttribute object via the default constructor, the copy constructor, the overloaded constructor, or an interpolation constructor that blends between two StrokeAttribute objects.

Parameters :

- brother (StrokeAttribute) – A StrokeAttribute object to be used as a copy constructor.

- red ( float ) – Red component of a stroke color.

- green ( float ) – Green component of a stroke color.

- blue ( float ) – Blue component of a stroke color.

- alpha ( float ) – Alpha component of a stroke color.

- thickness_right ( float ) – Stroke thickness on the right.

- thickness_left ( float ) – Stroke thickness on the left.

- attribute1 (StrokeAttribute) – The first StrokeAttribute object.

- attribute2 (StrokeAttribute) – The second StrokeAttribute object.

- t ( float ) – The interpolation parameter (0 <= t <= 1).

get_attribute_real ( name ) 

Hands back an attribute whose type is float.

Parameters :

name ( str ) – The name of the attribute.

Returns :

The attribute value.

Return type :

float

get_attribute_vec2 ( name ) 

Hands back an attribute whose type is a two-dimensional vector.

Parameters :

name ( str ) – The name of the attribute.

Returns :

The attribute value.

Return type :

mathutils.Vector

get_attribute_vec3 ( name ) 

Hands back an attribute whose type is a three-dimensional vector.

Parameters :

name ( str ) – The name of the attribute.

Returns :

The attribute value.

Return type :

mathutils.Vector

has_attribute_real ( name ) 

Tests whether the float-type attribute name exists.

Parameters :

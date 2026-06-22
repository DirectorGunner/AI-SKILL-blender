# Object Id (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Object(ID) 

### Basic Object Operations Example 

The snippet below walks through the everyday handling of an object: building a
new one, dropping it into a view layer, selecting it, and setting it active.

`	ext
import bpy

view_layer = bpy.context.view_layer

### Create new light data-block.
light_data = bpy.data.lights.new(name="New Light", type='POINT')

### Create new object with our light data-block.
light_object = bpy.data.objects.new(name="New Light", object_data=light_data)

### Link light object to the active collection of current view layer,
### so that it'll appear in the current scene.
view_layer.active_layer_collection.collection.objects.link(light_object)

### Place light to a specified location.
light_object.location = (5.0, 5.0, 5.0)

### And finally select it and make it active.
light_object.select_set(True)
view_layer.objects.active = light_object
`

base classes — bpy_struct, ID

class bpy.types. Object ( ID ) 

A data-block that describes an object inside a scene

active_material 

The material currently shown as active

Type :

Material

active_material_index 

Slot index of the active material (in [0, inf], default 0)

Type :

int

active_selection_set 

Index pointing at the selection set in use right now (in [-inf, inf], default 0)

Type :

int

active_shape_key 

The shape key in use at the moment (readonly)

Type :

ShapeKey

active_shape_key_index 

Index of the shape key in use (in [-32768, 32767], default 0)

Type :

int

add_rest_position_attribute 

Attach a “rest_position” attribute that mirrors the position attribute as it stands before shape keys and modifiers run (default False)

Type :

bool

animation_data 

This data-block's animation data (readonly)

Type :

AnimData

animation_visualization 

This data-block's animation data (readonly, never None)

Type :

AnimViz

bound_box 

The object's bounding box given in object-space coordinates; every entry is -1.0 when none is available (multi-dimensional array of 8 * 3 items, in [-inf, inf], default ((0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0), (0.0, 0.0, 0.0)), readonly)

Type :

bpy_prop_array[float]

collision 

Configuration for treating the object as a collider in a physics sim (readonly)

Type :

CollisionSettings

color 

The object's color and alpha, applied while Object Color mode is on (array of 4 items, in [0, inf], default (1.0, 1.0, 1.0, 1.0))

Type :

bpy_prop_array[float]

constraints 

The constraints that act on how the object is transformed (default None, readonly)

Type :

ObjectConstraints[Constraint]

cycles 

The object's Cycles settings (readonly)

Type :

CyclesObjectSettings

data 

The object's data

Type :

ID

delta_location 

A further translation layered onto the object's location (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

delta_rotation_euler 

A further rotation layered onto the object's rotation (when Euler rotations are in use) (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

delta_rotation_quaternion 

A further rotation layered onto the object's rotation (when Quaternion rotations are in use) (array of 4 items, in [-inf, inf], default (1.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

delta_scale 

A further scaling layered onto the object's scale (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

dimensions 

The object's bounding box dimensions in absolute terms.
Warning: Writing to this property or its members several times in a row will not behave correctly, since it depends on up-to-date evaluated data

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

display 

The object's display options for the 3D viewport (readonly, never None)

Type :

ObjectDisplay

display_bounds_type 

Which boundary shape the object draws (default 'BOX' )

- BOX
Box – Display bounds as box.

- SPHERE
Sphere – Display bounds as sphere.

- CYLINDER
Cylinder – Display bounds as cylinder.

- CONE
Cone – Display bounds as cone.

- CAPSULE
Capsule – Display bounds as capsule.

Type :

Literal[‘BOX’, ‘SPHERE’, ‘CYLINDER’, ‘CONE’, ‘CAPSULE’]

display_type 

The style used to draw the object in the viewport (default 'TEXTURED' )

- BOUNDS
Bounds – Display the bounds of the object.

- WIRE
Wire – Display the object as a wireframe.

- SOLID
Solid – Display the object as a solid (if solid drawing is enabled in the viewport).

- TEXTURED
Textured – Display the object with textures (if textures are enabled in the viewport).

Type :

Literal[‘BOUNDS’, ‘WIRE’, ‘SOLID’, ‘TEXTURED’]

empty_display_size 

Viewport draw size for empties (in [0.0001, 1000], default 1.0)

Type :

float

empty_display_type 

The viewport drawing style for empties (default '`PLAIN_AXES`' )

Type :

Literal[Object Empty Drawtype Items]

empty_image_depth 

Sets which surrounding objects hide the image (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’, ‘FRONT’, ‘BACK’]

empty_image_offset 

Distance the origin is shifted (array of 2 items, in [-inf, inf], default (-0.5, -0.5))

Type :

bpy_prop_array[float]

empty_image_side 

Choose whether the front or back side is shown (default '`DOUBLE_SIDED`' )

Type :

Literal[‘`DOUBLE_SIDED`’, ‘FRONT’, ‘BACK’]

field 

Configuration for using the object as a field in a physics sim (readonly)

Type :

FieldSettings

hide_probe_plane 

Switch off everywhere in planar light probes (default False)

Type :

bool

hide_probe_sphere 

Switch off everywhere in spherical light probes (default False)

Type :

bool

hide_probe_volume 

Switch off everywhere in volume probes (default False)

Type :

bool

hide_render 

Switch off everywhere in renders (default False)

Type :

bool

hide_select 

Turn off selectability in the viewport (default False)

Type :

bool

hide_surface_pick 

Remove the surface from selection, snapping and depth-picking operators. Commonly used so semi-transparent objects do not interfere with navigating the scene (default False)

Type :

bool

hide_viewport 

Switch off everywhere in viewports (default False)

Type :

bool

image_user 

Settings that pick which layer, pass and frame of the image gets shown (readonly, never None)

Type :

ImageUser

instance_collection 

Create an instance of an existing collection

Type :

Collection

instance_faces_scale 

Scale factor for the per-face instance objects (in [0.001, 10000], default 1.0)

Type :

float

instance_type 

When set, which instancing method the object applies (default 'NONE' )

- NONE
None.

- VERTS
Vertices – Instantiate child objects on all vertices.

- FACES
Faces – Instantiate child objects on all faces.

- COLLECTION
Collection – Enable collection instancing.

Type :

Literal[‘NONE’, ‘VERTS’, ‘FACES’, ‘COLLECTION’]

is_from_instancer 

Marks an object originating from an instancer (default False, readonly)

Type :

bool

is_from_set 

Marks an object originating from a background set (default False, readonly)

Type :

bool

is_holdout 

Treat the object as a holdout or matte, punching a zero-alpha hole in the image to be filled later in compositing with real footage or another render (default False)

Type :

bool

is_instancer 

(default False, readonly)

Type :

bool

is_shadow_catcher 

Render only the shadows and reflections falling on this object, for compositing renders over real footage. Objects flagged this way are taken to already be present in the footage, while those without the flag are synthetic objects placed into it. (default False)

Type :

bool

light_linking 

The object's light linking configuration (readonly, never None)

Type :

ObjectLightLinking

lightgroup 

The lightgroup this object is assigned to (default “”, never None)

Type :

str

lineart 

The object's Line Art configuration

Type :

ObjectLineArt

location 

Where the object sits (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

lock_location 

Prevent the location from being edited during a transform (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

lock_rotation 

Prevent the rotation from being edited during a transform (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

lock_rotation_w 

Prevent the ‘angle’ part of four-component rotations from being edited during a transform (default False)

Type :

bool

lock_rotations_4d 

Prevent four-component rotations from being edited per component (rather than as Eulers) (default True)

Type :

bool

lock_scale 

Prevent the scale from being edited during a transform (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

material_slots 

The object's material slots (default None, readonly)

Type :

bpy_prop_collection[MaterialSlot]

matrix_basis 

Matrix entry point for location, rotation and scale (deltas included), taken before constraints and parenting apply (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_local 

Transformation matrix relative to the parent.
Warning: This accounts for object parenting only, so for example with bone parenting you get a matrix relative to the Armature object rather than to the actual parent bone

(multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

matrix_parent_inverse 

The inverse of the parent matrix captured at the moment of parenting (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((1.0, 0.0, 0.0, 0.0), (0.0, 1.0, 0.0, 0.0), (0.0, 0.0, 1.0, 0.0), (0.0, 0.0, 0.0, 1.0)))

Type :

mathutils.Matrix

matrix_world 

The transformation matrix in world space (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)))

Type :

mathutils.Matrix

mode 

The object's current interaction mode (default 'OBJECT' , readonly)

Type :

Literal[Object Mode Items]

modifiers 

The modifiers acting on the object's geometric data (default None, readonly)

Type :

ObjectModifiers[Modifier]

motion_path 

This element's Motion Path (readonly)

Type :

MotionPath

parent 

The object's parent

Type :

Object

parent_bone 

The parent bone's name when bone parenting is used (default “”, never None)

Type :

str

parent_type 

The kind of parenting relationship (default 'OBJECT' )

- OBJECT
Object – The object is parented to an object.

- ARMATURE
Armature.

- LATTICE
Lattice – The object is parented to a lattice.

- VERTEX
Vertex – The object is parented to a vertex.

- `VERTEX_3`
3 Vertices.

- BONE
Bone – The object is parented to a bone.

Type :

Literal[‘OBJECT’, ‘ARMATURE’, ‘LATTICE’, ‘VERTEX’, ‘`VERTEX_3`’, ‘BONE’]

parent_vertices 

The vertex indices used when vertex parenting applies (array of 3 items, in [0, inf], default (0, 0, 0))

Type :

bpy_prop_array[int]

particle_systems 

The particle systems given off by the object (default None, readonly)

Type :

ParticleSystems[ParticleSystem]

pass_index 

The index used by the “Object Index” render pass (in [0, 32767], default 0)

Type :

int

pose 

The armature's current pose (readonly)

Type :

Pose

rigid_body 

Configuration for the rigid body simulation (readonly)

Type :

RigidBodyObject

rigid_body_constraint 

The constraint that ties rigid bodies together (readonly)

Type :

RigidBodyConstraint

rotation_axis_angle 

The rotation angle for the Axis-Angle rotation representation (array of 4 items, in [-inf, inf], default (0.0, 0.0, 1.0, 0.0))

Type :

bpy_prop_array[float]

rotation_euler 

Rotation expressed as Eulers (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Euler

rotation_mode 

Which rotation method to use; values from the other rotation modes are ignored (default 'XYZ' )

Type :

Literal[Object Rotation Mode Items]

rotation_quaternion 

Rotation expressed as Quaternions (array of 4 items, in [-inf, inf], default (1.0, 0.0, 0.0, 0.0))

Type :

mathutils.Quaternion

scale 

The object's scaling (array of 3 items, in [-inf, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

selection_sets 

Groups of bones gathered for quick selection (default None, readonly)

Type :

bpy_prop_collection[ SelectionSet ]

shader_effects 

The effects that influence how the object is displayed (default None, readonly)

Type :

ObjectShaderFx[ShaderFx]

shadow_terminator_geometry_offset 

Nudge rays away from the surface to cut down the shadow terminator artifact on low-poly meshes. Only triangles sitting at grazing angles to the light are affected (in [0, inf], default 0.1)

Type :

float

shadow_terminator_normal_offset 

Nudge rays away from the surface to cut down the shadow terminator artifact on low-poly meshes. Affects only the triangles touched by the geometry offset (in [0, inf], default 0.0)

Type :

float

shadow_terminator_shading_offset 

Shift the shadow terminator toward the light so artifacts on low-poly meshes are concealed (in [0, inf], default 0.0)

Type :

float

show_all_edges 

Show every edge on mesh objects (default False)

Type :

bool

show_axis 

Show the object's origin together with its axes (default False)

Type :

bool

show_bounds 

Show the object's bounds (default False)

Type :

bool

show_empty_image_only_axis_aligned 

Reveal the image only while it lines up with the view axis (default False)

Type :

bool

show_empty_image_orthographic 

Show the image in orthographic mode (default True)

Type :

bool

show_empty_image_perspective 

Show the image in perspective mode (default True)

Type :

bool

show_in_front 

Have the object draw on top of the others (default False)

Type :

bool

show_instancer_for_render 

Keep the instancer visible at render time (default True)

Type :

bool

show_instancer_for_viewport 

Keep the instancer visible inside the viewport (default True)

Type :

bool

show_name 

Show the object's name (default False)

Type :

bool

show_only_shape_key 

Show just the active shape key at its full value (default False)

Type :

bool

show_texture_space 

Draw the texture space belonging to the object (default False)

Type :

bool

show_transparent 

Render material transparency on the object in the viewport (default False)

Type :

bool

show_wire 

Overlay the object's wireframe on top of solid shading (default False)

Type :

bool

soft_body 

Configuration for the soft body simulation (readonly)

Type :

SoftBodySettings

track_axis 

The axis treated as the 'forward' direction (used by Instance Vertices when Align to Vertex Normal is on) (default '`POS_X`' )

Type :

Literal[Object Axis Items]

type 

The object's kind (default 'EMPTY' , readonly)

Type :

Literal[Object Type Items]

up_axis 

The axis treated as the upward direction (used by Instance Vertices when Align to Vertex Normal is on) (default 'X' )

Type :

Literal[‘X’, ‘Y’, ‘Z’]

use_camera_lock_parent 

With View Lock active, 3D viewport camera moves are applied to the object's parent rather than to itself (default False)

Type :

bool

use_dynamic_topology_sculpting 

(default False, readonly)

Type :

bool

use_empty_image_alpha 

Blend by alpha rather than testing it (this may cause sorting artifacts) (default False)

Type :

bool

use_grease_pencil_lights 

Have lights influence the Grease Pencil object (default True)

Type :

bool

use_instance_faces_scale 

Size each instance relative to the area of its face (default False)

Type :

bool

use_instance_vertices_rotation 

Orient each instance to follow the vertex normal (default False)

Type :

bool

use_mesh_mirror_x 

Turn on mesh symmetry along the X axis (default False)

Type :

bool

use_mesh_mirror_y 

Turn on mesh symmetry along the Y axis (default False)

Type :

bool

use_mesh_mirror_z 

Turn on mesh symmetry along the Z axis (default False)

Type :

bool

use_parent_final_indices 

Reference the final evaluated indices in place of the original mesh indices (default False)

Type :

bool

use_shape_key_edit_mode 

Show shape keys while in edit mode (meshes only) (default False)

Type :

bool

use_simulation_cache 

Store frames in cache as simulation nodes play back (default True)

Type :

bool

vertex_groups 

The object's vertex groups (default None, readonly)

Type :

VertexGroups[VertexGroup]

visible_camera 

Whether the object can be seen by camera rays (default True)

Type :

bool

visible_diffuse 

Whether the object can be seen by diffuse rays (default True)

Type :

bool

visible_glossy 

Whether the object can be seen by glossy rays (default True)

Type :

bool

visible_shadow 

Whether the object can be seen by shadow rays (default True)

Type :

bool

visible_transmission 

Whether the object can be seen by transmission rays (default True)

Type :

bool

visible_volume_scatter 

Whether the object can be seen by volume scattering rays (default True)

Type :

bool

children 

Every object parented under this one.

Type :

tuple[Object, …]

Note

Takes O(len(bpy.data.objects)) time.

(readonly)

children_recursive 

The complete descendant list under this object.

Type :

list[Object]

Note

Takes O(len(bpy.data.objects)) time.

(readonly)

users_collection 

Which collections include this object.

Type :

tuple[Collection, …]

Note

Takes O(len(bpy.data.collections) + len(bpy.data.scenes)) time.

(readonly)

users_scene 

Which scenes include this object.

Type :

tuple[Scene, …]

Note

Takes O(len(bpy.data.scenes) * len(bpy.data.objects)) time.

(readonly)

select_get ( * , view_layer = None ) 

Report whether the object is selected; selection is tracked per view layer.

Parameters :

view_layer (ViewLayer) – Use this instead of the active view layer (optional)

Returns :

Object selected

Return type :

bool

select_set ( state , * , view_layer = None ) 

Mark the object as selected or deselected; selection is tracked per view layer.

Parameters :

- state ( bool ) – Selection state to define

- view_layer (ViewLayer) – Use this instead of the active view layer (optional)

hide_get ( * , view_layer = None ) 

Report whether the object is hidden from viewport editing; this state is tracked per view layer.

Parameters :

view_layer (ViewLayer) – Use this instead of the active view layer (optional)

Returns :

Object hidden

Return type :

bool

hide_set ( state , * , view_layer = None ) 

Hide the object from viewport editing; this state is tracked per view layer.

Parameters :

- state ( bool ) – Hide state to define

- view_layer (ViewLayer) – Use this instead of the active view layer (optional)

visible_get ( * , view_layer = None , viewport = None ) 

Report whether the object shows in the 3D viewport once every visibility setting is accounted for

Parameters :

- view_layer (ViewLayer) – Use this instead of the active view layer (optional)

- viewport (SpaceView3D) – Use this instead of the active 3D viewport (optional)

Returns :

Object visible

Return type :

bool

holdout_get ( * , view_layer = None ) 

Report whether the object acts as a holdout (mask) in the view layer

Parameters :

view_layer (ViewLayer) – Use this instead of the active view layer (optional)

Returns :

Object holdout

Return type :

bool

indirect_only_get ( * , view_layer = None ) 

Report whether the object only contributes indirectly — via shadows and reflections — in the view layer

Parameters :

view_layer (ViewLayer) – Use this instead of the active view layer (optional)

Returns :

Object indirect only

Return type :

bool

local_view_get ( viewport ) 

Read this object's local view state

Parameters :

viewport (SpaceView3D) – Viewport in local view (never None)

Returns :

Object local view state

Return type :

bool

local_view_set ( viewport , state ) 

Assign this object's local view state

Parameters :

- viewport (SpaceView3D) – Viewport in local view (never None)

- state ( bool ) – Local view state to define

visible_in_viewport_get ( viewport ) 

Evaluate local view and local collections for this viewport/object pair

Parameters :

viewport (SpaceView3D) – Viewport in local collections (never None)

Returns :

Object viewport visibility

Return type :

bool

convert_space ( * , pose_bone = None , matrix = ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)) , from_space = 'WORLD' , to_space = 'WORLD' ) 

Transform the supplied matrix from one coordinate space into another

Parameters :

- pose_bone (PoseBone) – Bone to use to define spaces (may be None, in which case only the two ‘WORLD’ and ‘LOCAL’ spaces are usable) (optional)

- matrix (mathutils.Matrix) – The matrix to transform (multi-dimensional array of 4 * 4 items, in [-inf, inf], optional)

- from_space ( Literal [ 'WORLD' , 'POSE' , '`LOCAL_WITH_PARENT`' , 'LOCAL' ] ) – The space in which ‘matrix’ is currently (optional)

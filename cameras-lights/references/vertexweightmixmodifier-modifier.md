# Vertexweightmixmodifier Modifier, Vertexweightproximitymodifier Modifier, Viewlayereevee Bpy Struct, Viewlayers Bpy Prop Collection ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: VertexWeightMixModifier(Modifier); VertexWeightProximityModifier(Modifier); ViewLayerEEVEE(bpy_struct); ViewLayers(bpy_prop_collection); VolumeDisplaceModifier(Modifier); VolumeRender(bpy_struct); VolumeToMeshModifier(Modifier); WarpModifier(Modifier).

## VertexWeightMixModifier(Modifier)

### VertexWeightMixModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. VertexWeightMixModifier ( Modifier ) 

Blend together the weights of a pair of vertex groups

default_weight_a 

The weight assumed for a vertex that is absent from the first A vgroup (in [0, 1], default 0.0)

Type :

float

default_weight_b 

The weight assumed for a vertex that is absent from the second B vgroup (in [0, 1], default 0.0)

Type :

float

invert_mask_vertex_group 

Flip the influence of the vertex group mask (default False)

Type :

bool

invert_vertex_group_a 

Flip how much vertex group A contributes (default False)

Type :

bool

invert_vertex_group_b 

Flip how much vertex group B contributes (default False)

Type :

bool

mask_constant 

How strongly the current changes act on the vgroup overall (in [-inf, inf], default 1.0)

Type :

float

mask_tex_map_bone 

The bone supplying texture coordinates (default "", never None)

Type :

str

mask_tex_map_object 

The object supplying texture coordinates

Type :

Object

mask_tex_mapping 

The texture coordinates to drive the mapping (default 'LOCAL' )

- LOCAL
Local – Use local generated coordinates.

- GLOBAL
Global – Use global coordinates.

- OBJECT
Object – Use local generated coordinates of another object.

- UV
UV – Use coordinates from a UV layer.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT', 'UV']

mask_tex_use_channel 

The texture channel used for masking (default 'INT' )

Type :

Literal['INT', 'RED', 'GREEN', 'BLUE', 'HUE', 'SAT', 'VAL', 'ALPHA']

mask_tex_uv_layer 

UV map name (default "", never None)

Type :

str

mask_texture 

Masking texture

Type :

Texture

mask_vertex_group 

Masking vertex group name (default "", never None)

Type :

str

mix_mode 

The way VGroup B's weights modify those of VGroup A (default 'SET' )

- SET
Replace – Replace VGroup A's weights by VGroup B's ones.

- ADD
Add – Add VGroup B's weights to VGroup A's ones.

- SUB
Subtract – Subtract VGroup B's weights from VGroup A's ones.

- MUL
Multiply – Multiply VGroup A's weights by VGroup B's ones.

- DIV
Divide – Divide VGroup A's weights by VGroup B's ones.

- DIF
Difference – Difference between VGroup A's and VGroup B's weights.

- AVG
Average – Average value of VGroup A's and VGroup B's weights.

- MIN
Minimum – Minimum of VGroup A's and VGroup B's weights.

- MAX
Maximum – Maximum of VGroup A's and VGroup B's weights.

Type :

Literal['SET', 'ADD', 'SUB', 'MUL', 'DIV', 'DIF', 'AVG', 'MIN', 'MAX']

mix_set 

The set of vertices to act on (default 'AND' )

- ALL
All – Affect all vertices (might add some to VGroup A).

- A
VGroup A – Affect vertices in VGroup A.

- B
VGroup B – Affect vertices in VGroup B (might add some to VGroup A).

- OR
VGroup A or B – Affect vertices in at least one of both VGroups (might add some to VGroup A).

- AND
VGroup A and B – Affect vertices in both groups.

Type :

Literal['ALL', 'A', 'B', 'OR', 'AND']

normalize 

Renormalize the resulting weights (otherwise they merely get clamped into the 0.0 to 1.0 range) (default False)

Type :

bool

vertex_group_a 

First vertex group name (default "", never None)

Type :

str

vertex_group_b 

Second vertex group name (default "", never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## VertexWeightProximityModifier(Modifier)

### VertexWeightProximityModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. VertexWeightProximityModifier ( Modifier ) 

Drive a group's vertex weights from how far they sit from a target object

falloff_type 

The mapping from old weights to their new values (default 'LINEAR' )

- LINEAR
Linear – Null action.

- CURVE
Custom Curve.

- SHARP
Sharp.

- SMOOTH
Smooth.

- ROOT
Root.

- `ICON_SPHERECURVE`
Sphere.

- RANDOM
Random.

- STEP
Median Step – Map all values below 0.5 to 0.0, and all others to 1.0.

Type :

Literal['LINEAR', 'CURVE', 'SHARP', 'SMOOTH', 'ROOT', '`ICON_SPHERECURVE`', 'RANDOM', 'STEP']

invert_falloff 

Flip the falloff weight that results (default False)

Type :

bool

invert_mask_vertex_group 

Flip the influence of the vertex group mask (default False)

Type :

bool

map_curve 

Custom mapping curve (readonly)

Type :

CurveMapping

mask_constant 

How strongly the current changes act on the vgroup overall (in [-inf, inf], default 1.0)

Type :

float

mask_tex_map_bone 

The bone supplying texture coordinates (default "", never None)

Type :

str

mask_tex_map_object 

The object supplying texture coordinates

Type :

Object

mask_tex_mapping 

The texture coordinates to drive the mapping (default 'LOCAL' )

- LOCAL
Local – Use local generated coordinates.

- GLOBAL
Global – Use global coordinates.

- OBJECT
Object – Use local generated coordinates of another object.

- UV
UV – Use coordinates from a UV layer.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT', 'UV']

mask_tex_use_channel 

The texture channel used for masking (default 'INT' )

Type :

Literal['INT', 'RED', 'GREEN', 'BLUE', 'HUE', 'SAT', 'VAL', 'ALPHA']

mask_tex_uv_layer 

UV map name (default "", never None)

Type :

str

mask_texture 

Masking texture

Type :

Texture

mask_vertex_group 

Masking vertex group name (default "", never None)

Type :

str

max_dist 

The distance that maps to a weight of 1.0 (in [0, inf], default 1.0)

Type :

float

min_dist 

The distance that maps to a weight of 0.0 (in [0, inf], default 0.0)

Type :

float

normalize 

Renormalize the resulting weights (otherwise they merely get clamped into the 0.0 to 1.0 range) (default False)

Type :

bool

proximity_geometry 

Take the smallest computed distance to the target object's geometry as the weight (default { 'FACE' })

- VERTEX
Vertex – Compute distance to nearest vertex.

- EDGE
Edge – Compute distance to nearest edge.

- FACE
Face – Compute distance to nearest face.

Type :

set[Literal['VERTEX', 'EDGE', 'FACE']]

proximity_mode 

Which distances to the target object to rely on (default 'GEOMETRY' )

- OBJECT
Object – Use distance between affected and target objects.

- GEOMETRY
Geometry – Use distance between affected object's vertices and target object, or target object's geometry.

Type :

Literal['OBJECT', 'GEOMETRY']

target 

The object whose distance to the vertices is measured

Type :

Object

vertex_group 

Vertex group name (default "", never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## ViewLayerEEVEE(bpy_struct)

### ViewLayerEEVEE(bpy_struct)

base class — bpy_struct

class bpy.types. ViewLayerEEVEE ( bpy_struct )

View Layer settings for EEVEE

ambient_occlusion_distance

How far away objects can sit and still feed into the ambient occlusion effect (in [0, 100000], default 10.0)

Type :

float

use_pass_bloom

Output a bloom pass (deprecated) (default False)

Type :

bool

use_pass_transparent

Output alpha-blended surfaces on their own pass (default False)

Type :

bool

use_pass_volume_direct

Output a volume direct-light pass (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| ViewLayer.eevee | |

## ViewLayers(bpy_prop_collection)

### ViewLayers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ViewLayers ( bpy_prop_collection )

A set of render layers.

new ( name )

Append a view layer onto the scene

Parameters :

name ( str ) – New name for the view layer (not unique) (never None)

Returns :

Newly created view layer

Return type :

ViewLayer

remove ( layer )

Delete a view layer

Parameters :

layer (ViewLayer) – View layer to remove (never None)

move ( from_index , to_index )

Reposition a view layer

Parameters :

- from_index ( int ) – From Index, Index to move (in [-inf, inf])

- to_index ( int ) – To Index, Target index (in [-inf, inf])

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Scene.view_layers | |

## VolumeDisplaceModifier(Modifier)

### VolumeDisplaceModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. VolumeDisplaceModifier ( Modifier )

strength

Strength of the displacement (in [-inf, inf], default 0.0)

Type :

float

texture

Type :

Texture

texture_map_mode

(default 'LOCAL' )

- LOCAL
Local – Read texture coordinates from the local coordinate system.

- GLOBAL
Global – Read texture coordinates from the global coordinate system.

- OBJECT
Object – Read texture coordinates from a linked object's local coordinate system.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT']

texture_map_object

The object whose mapping drives the texture coordinates

Type :

Object

texture_mid_level

Removed from the texture color to obtain a displacement vector (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

texture_sample_radius

Lower values run faster but can clip the volume (in [0, inf], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## VolumeRender(bpy_struct)

### VolumeRender(bpy_struct)

base class — bpy_struct

class bpy.types. VolumeRender ( bpy_struct )

Render settings for a volume object.

clipping

Threshold below which voxels count as empty so rendering can be optimized (in [0, 1], default 0.001)

Type :

float

precision

Choose the precision of the volume data. Smaller settings save memory but lose detail. (default 'HALF' )

- FULL
Full – Store every value as a 32-bit float.

- HALF
Half – Store every value as a 16-bit float.

- VARIABLE
Variable – Quantize using a variable number of bits.

Type :

Literal['FULL', 'HALF', 'VARIABLE']

space

Choose whether volume density and step size are measured in object or world space (default 'OBJECT' )

- OBJECT
Object – Hold opacity and detail steady no matter the object's scale.

- WORLD
World – Measure the step size and density in world space.

Type :

Literal['OBJECT', 'WORLD']

step_size

Spacing between volume samples. Smaller values capture more detail but cost performance. A value of zero lets Blender derive the step size from voxel size. (in [0, inf], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Volume.render | |

## VolumeToMeshModifier(Modifier)

### VolumeToMeshModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. VolumeToMeshModifier ( Modifier )

adaptivity

Cuts the final face count by thinning out geometry wherever detail isn't required (in [0, 1], default 0.0)

Type :

float

grid_name

Which grid inside the volume object gets turned into a mesh (default "", never None)

Type :

str

object

Object

Type :

Object

resolution_mode

How the target voxel size gets specified (default 'GRID' )

- GRID
Grid – Adopt the resolution of the volume grid.

- `VOXEL_AMOUNT`
Voxel Amount – Target a voxel count along a single axis.

- `VOXEL_SIZE`
Voxel Size – Target a specific voxel edge length.

Type :

Literal['GRID', '`VOXEL_AMOUNT`', '`VOXEL_SIZE`']

threshold

Voxels above this value end up inside the resulting mesh (in [0, inf], default 0.0)

Type :

float

use_smooth_shade

Emit smooth-shaded faces in place of flat-shaded ones (default False)

Type :

bool

voxel_amount

Roughly how many voxels lie along one axis (in [0, inf], default 0)

Type :

int

voxel_size

The smaller this is, the finer the output resolution (in [0, inf], default 0.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## WarpModifier(Modifier)

### WarpModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. WarpModifier ( Modifier )

Warp modifier

bone_from

Bone the transform starts from (default "", never None)

Type :

str

bone_to

Bone that sets the offset (default "", never None)

Type :

str

falloff_curve

Custom falloff curve (readonly)

Type :

CurveMapping

falloff_radius

Radius over which the effect applies (in [-inf, inf], default 1.0)

Type :

float

falloff_type

(default 'SMOOTH' )

Type :

Literal['NONE', 'CURVE', 'SMOOTH', 'SPHERE', 'ROOT', '`INVERSE_SQUARE`', 'SHARP', 'LINEAR', 'CONSTANT']

invert_vertex_group

Flip the vertex group's influence (default False)

Type :

bool

object_from

Object to transform from

Type :

Object

object_to

Object to transform to

Type :

Object

strength

(in [-inf, inf], default 1.0)

Type :

float

texture

Type :

Texture

texture_coords

(default 'LOCAL' )

- LOCAL
Local – Read texture coordinates from the local coordinate system.

- GLOBAL
Global – Read texture coordinates from the global coordinate system.

- OBJECT
Object – Read texture coordinates from a linked object's local coordinate system.

- UV
UV – Read texture coordinates from the UV layer.

Type :

Literal['LOCAL', 'GLOBAL', 'OBJECT', 'UV']

texture_coords_bone

Bone supplying the texture coordinates (default "", never None)

Type :

str

texture_coords_object

Object supplying the texture coordinates

Type :

Object

use_volume_preserve

Hold volume constant while rotations are in play (default False)

Type :

bool

uv_layer

UV map name (default "", never None)

Type :

str

vertex_group

Vertex group name used to modulate the deform (default "", never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

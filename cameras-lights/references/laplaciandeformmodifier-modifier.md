# Laplaciandeformmodifier Modifier, Laplaciansmoothmodifier Modifier, Latticemodifier Modifier, Lightgroup Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: LaplacianDeformModifier(Modifier); LaplacianSmoothModifier(Modifier); LatticeModifier(Modifier); Lightgroup(bpy_struct); Lightgroups(bpy_prop_collection); LightProbe(ID); LightProbePlane(LightProbe); LightProbeSphere(LightProbe).

## LaplacianDeformModifier(Modifier)

### LaplacianDeformModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. LaplacianDeformModifier ( Modifier ) 

Mesh deform modifier

invert_vertex_group 

Flip how the vertex group weights apply (default False)

Type :

bool

is_bind 

Indicates whether the geometry is currently bound to its anchors (default False, readonly)

Type :

bool

iterations 

(in [0, inf], default 1)

Type :

int

vertex_group 

Vertex Group whose members act as the Anchors (default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## LaplacianSmoothModifier(Modifier)

### LaplacianSmoothModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. LaplacianSmoothModifier ( Modifier ) 

Smoothing effect modifier

invert_vertex_group 

Flip how the vertex group weights apply (default False)

Type :

bool

iterations 

(in [0, 32767], default 1)

Type :

int

lambda_border 

Lambda factor in border (in [-inf, inf], default 0.01)

Type :

float

lambda_factor 

Smooth effect factor (in [-inf, inf], default 0.01)

Type :

float

use_normalized 

Refine and steady the enhanced shape (default True)

Type :

bool

use_volume_preserve 

Preserve volume once the smoothing has run (default True)

Type :

bool

use_x 

Apply smoothing on the X axis (default True)

Type :

bool

use_y 

Apply smoothing on the Y axis (default True)

Type :

bool

use_z 

Apply smoothing on the Z axis (default True)

Type :

bool

vertex_group 

Vertex Group that sets the modifier's per-point influence (default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## LatticeModifier(Modifier)

### LatticeModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. LatticeModifier ( Modifier ) 

Lattice deformation modifier

invert_vertex_group 

Flip how the vertex group weights apply (default False)

Type :

bool

object 

Lattice object that drives the deformation

Type :

Object

strength 

How strongly the modifier acts (in [-inf, inf], default 1.0)

Type :

float

vertex_group 

Vertex Group that sets the modifier's per-point influence (default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## Lightgroup(bpy_struct)

### Lightgroup(bpy_struct) 

base class — bpy_struct

class bpy.types. Lightgroup ( bpy_struct ) 

name 

Name of the Lightgroup (default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| Lightgroups.add Lightgroups.remove | ViewLayer.active_lightgroup ViewLayer.lightgroups |

## Lightgroups(bpy_prop_collection)

### Lightgroups(bpy_prop_collection) 

base classes — bpy_prop, bpy_prop_collection

class bpy.types. Lightgroups ( bpy_prop_collection ) 

Collection of Lightgroups

add ( * , name = '' ) 

add

Parameters :

name ( str ) – Name, Name of newly created lightgroup (optional, never None)

Returns :

Newly created Lightgroup

Return type :

Lightgroup

remove ( lightgroup ) 

Take the given light group out

Parameters :

lightgroup (Lightgroup) – Lightgroup to remove (never None)

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| ViewLayer.lightgroups | |

## LightProbe(ID)

### LightProbe(ID) 

base classes — bpy_struct, ID

subclasses —
LightProbePlane, LightProbeSphere, LightProbeVolume

class bpy.types. LightProbe ( ID ) 

Light Probe data-block for lighting capture objects

animation_data 

Animation data for this data-block (readonly)

Type :

AnimData

clip_start 

Probe clip start, below which objects will not appear in reflections (in [1e-06, inf], default 0.8)

Type :

float

data_display_size 

Size at which the sampled data is shown in the viewport (in [0, inf], default 0.1)

Type :

float

influence_distance 

Influence distance of the probe (in [0, inf], default 2.5)

Type :

float

invert_visibility_collection 

Invert visibility collection (Deprecated) (default False)

Type :

bool

show_clip 

Draw the clipping distances in the 3D view (default False)

Type :

bool

show_data 

Deprecated, use use_data_display instead (default False)

Type :

bool

show_influence 

Draw the influence volume in the 3D view (default True)

Type :

bool

type 

Type of light probe (default 'SPHERE' , readonly)

- SPHERE
Sphere – Light probe that captures precise lighting from all directions at a single point in space.

- PLANE
Plane – Light probe that captures incoming light from a single direction on a plane.

- VOLUME
Volume – Light probe that captures low frequency lighting inside a volume.

Type :

Literal[‘SPHERE’, ‘PLANE’, ‘VOLUME’]

use_data_display 

Show the sampled data in the viewport to help debug captured light (default False)

Type :

bool

visibility_bleed_bias 

Bias for reducing light-bleed on variance shadow maps (Deprecated) (in [0, 1], default 0.0)

Type :

float

visibility_blur 

Filter size of the visibility blur (Deprecated) (in [0, 1], default 0.2)

Type :

float

visibility_buffer_bias 

Bias for reducing self shadowing (Deprecated) (in [0.001, 9999], default 1.0)

Type :

float

visibility_collection 

Restrict objects visible for this probe (Deprecated)

Type :

Collection

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.lightprobe BlendData.lightprobes | BlendDataProbes.new BlendDataProbes.remove |

## LightProbePlane(LightProbe)

### LightProbePlane(LightProbe) 

base classes — bpy_struct, ID, LightProbe

class bpy.types. LightProbePlane ( LightProbe ) 

Light probe that captures incoming light from a single direction on a plane

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library | ID.library_weak_reference ID.asset_data ID.override_library ID.preview LightProbe.type LightProbe.clip_start LightProbe.show_clip LightProbe.show_influence LightProbe.influence_distance LightProbe.visibility_buffer_bias LightProbe.visibility_bleed_bias LightProbe.visibility_blur LightProbe.visibility_collection LightProbe.invert_visibility_collection LightProbe.show_data LightProbe.use_data_display LightProbe.data_display_size LightProbe.animation_data |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py LightProbe.bl_rna_get_subclass LightProbe.bl_rna_get_subclass_py |

## LightProbeSphere(LightProbe)

### LightProbeSphere(LightProbe) 

base classes — bpy_struct, ID, LightProbe

class bpy.types. LightProbeSphere ( LightProbe ) 

Light probe that captures precise lighting from all directions at a single point in space

clip_end 

Probe clip end, beyond which objects will not appear in reflections (in [1e-06, inf], default 20.0)

Type :

float

falloff 

Sets how quickly the probe's influence drops off (in [0, 1], default 0.2)

Type :

float

influence_type 

Type of influence volume (default 'ELIPSOID' )

Type :

Literal[‘ELIPSOID’, ‘BOX’]

parallax_distance 

Lowest corner of the parallax bounding box (in [0, inf], default 2.5)

Type :

float

parallax_type 

Type of parallax volume (default 'ELIPSOID' )

Type :

Literal[‘ELIPSOID’, ‘BOX’]

show_parallax 

Draw the parallax correction volume in the 3D view (default False)

Type :

bool

use_custom_parallax 

Switch on custom settings for the parallax correction volume (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The matching RNA type, or the supplied default if there is none.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The matching class, or the supplied default if there is none.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library | ID.library_weak_reference ID.asset_data ID.override_library ID.preview LightProbe.type LightProbe.clip_start LightProbe.show_clip LightProbe.show_influence LightProbe.influence_distance LightProbe.visibility_buffer_bias LightProbe.visibility_bleed_bias LightProbe.visibility_blur LightProbe.visibility_collection LightProbe.invert_visibility_collection LightProbe.show_data LightProbe.use_data_display LightProbe.data_display_size LightProbe.animation_data |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py LightProbe.bl_rna_get_subclass LightProbe.bl_rna_get_subclass_py |

# Blendtexture Texture, Booleanmodifier Modifier

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: BlendTexture(Texture); BooleanModifier(Modifier).

## BlendTexture(Texture)

### BlendTexture(Texture)

base classes — bpy_struct, ID, Texture

class bpy.types.BlendTexture(Texture)

A generated texture that interpolates between colors.

progression

The pattern used when blending between the colors (default 'LINEAR')

- LINEAR
Linear – Create a linear progression.

- QUADRATIC
Quadratic – Create a quadratic progression.

- EASING
Easing – Create a progression easing from one step to the next.

- DIAGONAL
Diagonal – Create a diagonal progression.

- SPHERICAL
Spherical – Create a spherical progression.

- `QUADRATIC_SPHERE`
Quadratic Sphere – Create a quadratic progression in the shape of a sphere.

- RADIAL
Radial – Create a radial progression.

Type:
Literal['LINEAR', 'QUADRATIC', 'EASING', 'DIAGONAL', 'SPHERICAL', '`QUADRATIC_SPHERE`', 'RADIAL']

use_flip_axis

Swap the texture's X and Y axis (default 'HORIZONTAL')

- HORIZONTAL
Horizontal – No flipping.

- VERTICAL
Vertical – Flip the texture's X and Y axis.

Type:
Literal['HORIZONTAL', 'VERTICAL']

users_material

Materials that use this texture

Type:
tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier

Object modifiers that use this texture

Type:
tuple[Object, …]

Note

Takes O(len(bpy.data.objects) * len(obj.modifiers)) time.

(readonly)

classmethod bl_rna_get_subclass(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (bpy.types.Struct | None) – The value to return when not found.

Returns:
The RNA type or default when not found.

Return type:
bpy.types.Struct

classmethod bl_rna_get_subclass_py(id, default=None, /)

Parameters:
- id (str) – The RNA type identifier.
- default (type | None) – The value to return when not found.

Returns:
The class or default when not found.

Return type:
type

### Inherited Properties

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference | ID.asset_data ID.override_library ID.preview Texture.type Texture.use_clamp Texture.use_color_ramp Texture.color_ramp Texture.intensity Texture.contrast Texture.saturation Texture.factor_red Texture.factor_green Texture.factor_blue Texture.use_preview_alpha Texture.use_nodes Texture.node_tree Texture.animation_data Texture.users_material Texture.users_object_modifier |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Texture.evaluate Texture.bl_rna_get_subclass Texture.bl_rna_get_subclass_py |

## BooleanModifier(Modifier)

### BooleanModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. BooleanModifier ( Modifier )

A modifier that performs Boolean operations between meshes.

collection

The collection whose mesh objects feed into the Boolean operation.

Type :

Collection

debug_options

Diagnostic switches, available only when Blender is launched with '-d' (default set())

Type :

set[Literal['SEPARATE', '`NO_DISSOLVE`', '`NO_CONNECT_REGIONS`']]

double_threshold

Tolerance used when detecting geometry that overlaps (in [0, 1], default 1e-06)

Type :

float

material_mode

How materials get assigned to the newly generated faces (default 'INDEX' )

- INDEX
Index Based – Assigns the material to new faces by matching the order of the material slot lists. When the modifier object lacks a given material, the face reuses that same slot index, or the first slot if there aren't enough..

- TRANSFER
Transfer – Carries materials over from filled slots into the result mesh, creating new ones where required. Where a slot is empty, the operand mesh's own material index is used as a fallback..

Type :

Literal['INDEX', 'TRANSFER']

object

The mesh object that serves as the operand for the Boolean operation.

Type :

Object

operand_type

(default 'OBJECT' )

- OBJECT
Object – Treat one mesh object as the Boolean operand.

- COLLECTION
Collection – Treat a whole collection of mesh objects as the Boolean operand.

Type :

Literal['OBJECT', 'COLLECTION']

operation

(default 'DIFFERENCE' )

- INTERSECT
Intersect – Retains only the volume shared by every operand.

- UNION
Union – Merges the meshes additively.

- DIFFERENCE
Difference – Merges the meshes subtractively.

Type :

Literal['INTERSECT', 'UNION', 'DIFFERENCE']

solver

Which algorithm computes the Boolean result (default 'EXACT' )

- FLOAT
Float – A lightweight, fast solver that cannot cope with overlapping geometry.

- EXACT
Exact – A slower solver that handles coplanar faces most accurately.

- MANIFOLD
Manifold – The quickest solver; it requires manifold meshes but produces higher-quality output.

Type :

Literal['FLOAT', 'EXACT', 'MANIFOLD']

use_hole_tolerant

Produces cleaner output where holes are present, at the cost of speed (default False)

Type :

bool

use_self

Permit operands to intersect themselves (default False)

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

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

# Material Id, Material Ul Matslots Uilist, Materialslot Bpy Struct

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Material(ID); `MATERIAL_UL`_matslots(UIList); MaterialSlot(bpy_struct).

## Material(ID)

### Material(ID)

base classes — bpy_struct, ID

class bpy.types. Material ( ID )

A material data-block that sets how geometric objects look when rendered.

alpha_threshold

A pixel only renders when its alpha sits above this cutoff (in [0, 1], default 0.5)

Type :

float

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

blend_method

Blend Mode for Transparent Faces (Deprecated: use ‘surface_render_method’) (default 'OPAQUE' )

- OPAQUE
Opaque – Render surface without transparency.

- CLIP
Alpha Clip – Use the alpha threshold to clip the visibility (binary visibility).

- HASHED
Alpha Hashed – Use noise to dither the binary visibility (works well with multi-samples).

- BLEND
Alpha Blend – Render polygon transparent, depending on alpha channel of the texture.

Type :

Literal[‘OPAQUE’, ‘CLIP’, ‘HASHED’, ‘BLEND’]

cycles

Cycles material settings (readonly)

Type :

CyclesMaterialSettings

diffuse_color

The material's diffuse color (array of 4 items, in [0, inf], default (0.8, 0.8, 0.8, 1.0))

Type :

bpy_prop_array[float]

displacement_method

Which method handles the displacement (default 'BUMP' )

- BUMP
Bump Only – Bump mapping to simulate the appearance of displacement.

- DISPLACEMENT
Displacement Only – Use true displacement of surface only, requires fine subdivision.

- BOTH
Displacement and Bump – Combination of true displacement and bump mapping for finer detail.

Type :

Literal[‘BUMP’, ‘DISPLACEMENT’, ‘BOTH’]

grease_pencil

Grease Pencil color settings for material (readonly)

Type :

MaterialGPencilStyle

is_grease_pencil

True if this material has Grease Pencil data (default False, readonly)

Type :

bool

line_color

Line color used for Freestyle line rendering (array of 4 items, in [0, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

line_priority

At material boundaries the line color belonging to the higher priority wins (in [0, 32767], default 0)

Type :

int

lineart

Line Art settings for material (readonly)

Type :

MaterialLineArt

max_vertex_displacement

The greatest distance a vertex may move. Displacements beyond this threshold can produce visibility problems. (in [0, inf], default 0.0)

Type :

float

metallic

Quantity of mirror reflection used by raytracing (in [0, 1], default 0.0)

Type :

float

node_tree

Node tree for node based materials (readonly)

Type :

NodeTree

paint_active_slot

Index of active texture paint slot (in [0, 32767], default 0)

Type :

int

paint_clone_slot

Index of clone texture paint slot (in [0, 32767], default 0)

Type :

int

pass_index

Index number for the “Material Index” render pass (in [0, 32767], default 0)

Type :

int

preview_render_type

Type of preview render (default 'SPHERE' )

- FLAT
Flat – Flat XY plane.

- SPHERE
Sphere – Sphere.

- CUBE
Cube – Cube.

- HAIR
Hair – Hair strands.

- SHADERBALL
Shader Ball – Shader ball.

- CLOTH
Cloth – Cloth.

- FLUID
Fluid – Fluid.

Type :

Literal[‘FLAT’, ‘SPHERE’, ‘CUBE’, ‘HAIR’, ‘SHADERBALL’, ‘CLOTH’, ‘FLUID’]

refraction_depth

Estimate the object's thickness so two refraction events can be computed (0 disables) (Deprecated) (in [0, inf], default 0.0)

Type :

float

roughness

Roughness of the material (in [0, 1], default 0.4)

Type :

float

show_transparent_back

Render multiple transparent layers (may introduce transparency sorting problems) (Deprecated: use ‘use_tranparency_overlap’) (default True)

Type :

bool

specular_color

Specular color of the material (array of 3 items, in [0, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Color

specular_intensity

Brightness of the specular reflection (in [0, 1], default 0.5)

Type :

float

surface_render_method

Governs blending and compatibility with certain features (default 'DITHERED' )

- DITHERED
Dithered – Allows for grayscale hashed transparency, and compatible with render passes and raytracing. Also known as deferred rendering..

- BLENDED
Blended – Allows for colored transparency, but incompatible with render passes and raytracing. Also known as forward rendering..

Type :

Literal[‘DITHERED’, ‘BLENDED’]

texture_paint_images

Texture images used for texture painting (default None, readonly)

Type :

bpy_prop_collection[Image]

texture_paint_slots

Texture slots defining the mapping and influence of textures (default None, readonly)

Type :

bpy_prop_collection[TexPaintSlot]

thickness_mode

Approximation used to model the light interactions inside the object (default 'SPHERE' )

- SPHERE
Sphere – Approximate the object as a sphere whose diameter is equal to the thickness defined by the node tree.

- SLAB
Slab – Approximate the object as an infinite slab of thickness defined by the node tree.

Type :

Literal[‘SPHERE’, ‘SLAB’]

use_backface_culling

Use back face culling to hide the back side of faces (default False)

Type :

bool

use_backface_culling_lightprobe_volume

Treat the material as single sided during light probe volume capture. This also helps discard probes inside the object so light does not leak. (default True)

Type :

bool

use_backface_culling_shadow

Use back face culling when casting shadows (default False)

Type :

bool

use_nodes

Use shader nodes to render the material (default False)

Deprecated since version 5.0: removal planned in version 6.0

Unused but kept for compatibility reasons. Setting the property has no effect, and getting it always returns True.

Type :

bool

use_preview_world

Use the current world background to light the preview render (default False)

Type :

bool

use_raytrace_refraction

Determine transmitted color by raytracing rather than relying solely on light probes. This keeps the surface from contributing to the lighting of surfaces that do not use this option. (default False)

Type :

bool

use_screen_refraction

Determine transmitted color by raytracing rather than relying solely on light probes. This keeps the surface from contributing to the lighting of surfaces that do not use this option. Deprecated: use ‘use_raytrace_refraction’. (default False)

Type :

bool

use_sss_translucency

Add translucency effect to subsurface (Deprecated) (default False)

Type :

bool

use_thickness_from_shadow

Refine the thickness set by the material node tree using shadow maps from shadow-casting lights (default False)

Type :

bool

use_transparency_overlap

Render multiple transparent layers (may introduce transparency sorting problems) (default True)

Type :

bool

use_transparent_shadow

Cast transparent shadows for this material when it includes a Transparent BSDF; turning it off renders faster but gives less accurate shadows (default True)

Type :

bool

volume_intersection_method

Sets which inner region of the mesh generates the volumetric effect (default 'FAST' )

- FAST
Fast – Each face is considered as a medium interface. Gives correct results for manifold geometry that contains no inner parts..

- ACCURATE
Accurate – Faces are considered as medium interface only when they have different consecutive facing. Gives correct results as long as the max ray depth is not exceeded. Have significant memory overhead compared to the fast method..

Type :

Literal[‘FAST’, ‘ACCURATE’]

inline_shader_nodes ( )

Return this material's inlined shader nodes. The node tree is first preprocessed
to strip out nested groups, repeat zones, and similar constructs.

Returns :

The inlined shader nodes.

Return type :

bpy.types.InlineShaderNodes

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.material BlendData.materials BlendDataMaterials.create_gpencil_data BlendDataMaterials.new BlendDataMaterials.remove BlendDataMaterials.remove_gpencil_data BrushGpencilSettings.material BrushGpencilSettings.material_alt Curve.materials Curves.materials GeometryNodeInputMaterial.material GreasePencil.materials GreasePencilArrayModifier.material_filter GreasePencilBuildModifier.material_filter GreasePencilColorModifier.material_filter GreasePencilDashModifierData.material_filter GreasePencilEnvelopeModifier.material_filter GreasePencilHookModifier.material_filter GreasePencilLatticeModifier.material_filter GreasePencilLengthModifier.material_filter GreasePencilLineartModifier.target_material GreasePencilMirrorModifier.material_filter GreasePencilMultiplyModifier.material_filter GreasePencilNoiseModifier.material_filter | GreasePencilOffsetModifier.material_filter GreasePencilOpacityModifier.material_filter GreasePencilOutlineModifier.material_filter GreasePencilOutlineModifier.outline_material GreasePencilShrinkwrapModifier.material_filter GreasePencilSimplifyModifier.material_filter GreasePencilSmoothModifier.material_filter GreasePencilSubdivModifier.material_filter GreasePencilTextureModifier.material_filter GreasePencilThickModifierData.material_filter GreasePencilTintModifier.material_filter GreasePencilWeightAngleModifier.material_filter GreasePencilWeightProximityModifier.material_filter IDMaterials.append IDMaterials.pop MaterialSlot.material Mesh.materials MetaBall.materials NodeSocketMaterial.default_value NodeTreeInterfaceSocketMaterial.default_value Object.active_material PointCloud.materials ViewLayer.material_override Volume.materials |

## `MATERIAL_UL`_matslots(UIList)

### `MATERIAL_UL`_matslots(UIList)

base classes — bpy_struct, UIList

class bpy.types. `MATERIAL_UL`_matslots ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## MaterialSlot(bpy_struct)

### MaterialSlot(bpy_struct)

base class — bpy_struct

class bpy.types. MaterialSlot ( bpy_struct )

A material slot belonging to an object.

link

Bind the material to the object or to the object's data (default 'DATA' )

Type :

Literal[‘OBJECT’, ‘DATA’]

material

Material data-block used by this material slot

Type :

Material

name

Material slot name (default “”, readonly, never None)

Type :

str

slot_index

(in [-inf, inf], default 0, readonly)

Type :

int

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

| bpy.context.material_slot | Object.material_slots |

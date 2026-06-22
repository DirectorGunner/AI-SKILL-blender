# Nodetreeinterfacesocketvectorxyz2D Nodetreeinterfacesocket, Nodetreeinterfacesocketvectorxyz4D Nodetreeinterfacesocket, Nodetreepath Bpy Struct, Noisetexture Texture ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: NodeTreeInterfaceSocketVectorXYZ2D(NodeTreeInterfaceSocket); NodeTreeInterfaceSocketVectorXYZ4D(NodeTreeInterfaceSocket); NodeTreePath(bpy_struct); NoiseTexture(Texture); OceanModifier(Modifier); PackedFile(bpy_struct); Paint(bpy_struct).

## NodeTreeInterfaceSocketVectorXYZ2D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorXYZ2D(NodeTreeInterfaceSocket) 

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorXYZ2D ( NodeTreeInterfaceSocket ) 

A node socket transporting a 3D vector

default_value 

The value applied to the socket without an incoming link (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

dimensions 

Number of components carried by the vector socket (in [2, 4], default 0)

Type :

int

max_value 

Topmost value allowed (in [-inf, inf], default 0.0)

Type :

float

min_value 

Bottommost value allowed (in [-inf, inf], default 0.0)

Type :

float

subtype 

The subtype label of the default value (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout ) 

Show the option controls for this interface socket

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

init_socket ( node , socket , data_path ) 

Bring up a fresh node socket instance

Parameters :

- node (Node) – Node, Node of the socket to initialize (never None)

- socket (NodeSocket) – Socket, Socket to initialize (never None)

- data_path ( str ) – Data Path, Path to specialized socket data (never None)

from_socket ( node , socket ) 

Form the template parameters from an existing socket

Parameters :

- node (Node) – Node, Node of the original socket (never None)

- socket (NodeSocket) – Socket, Original socket (never None)

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

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreeInterfaceSocketVectorXYZ4D(NodeTreeInterfaceSocket)

### NodeTreeInterfaceSocketVectorXYZ4D(NodeTreeInterfaceSocket) 

base classes — bpy_struct, NodeTreeInterfaceItem, NodeTreeInterfaceSocket

class bpy.types. NodeTreeInterfaceSocketVectorXYZ4D ( NodeTreeInterfaceSocket ) 

A 3D vector socket that a node provides

default_value 

Value supplied to the socket whenever it lacks a connection (array of 4 items, in [-inf, inf], default (0.0, 0.0, 0.0, 0.0))

Type :

mathutils.Vector

dimensions 

Amount of components in the vector socket (in [2, 4], default 0)

Type :

int

max_value 

The value's ceiling (in [-inf, inf], default 0.0)

Type :

float

min_value 

The value's floor (in [-inf, inf], default 0.0)

Type :

float

subtype 

Subtype recorded for the default (default 'DEFAULT' )

Type :

Literal[‘DEFAULT’]

draw ( context , layout ) 

Draw this interface socket's settings interface

Parameters :

- context (Context) – (never None)

- layout (UILayout) – Layout, Layout in the UI (never None)

init_socket ( node , socket , data_path ) 

Prepare a node socket instance from new

Parameters :

- node (Node) – Node, Node of the socket to initialize (never None)

- socket (NodeSocket) – Socket, Socket to initialize (never None)

- data_path ( str ) – Data Path, Path to specialized socket data (never None)

from_socket ( node , socket ) 

Establish the template parameters from a socket already made

Parameters :

- node (Node) – Node, Node of the original socket (never None)

- socket (NodeSocket) – Socket, Original socket (never None)

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

| bpy_struct.id_data NodeTreeInterfaceItem.item_type NodeTreeInterfaceItem.parent NodeTreeInterfaceItem.position NodeTreeInterfaceItem.index NodeTreeInterfaceSocket.name NodeTreeInterfaceSocket.identifier NodeTreeInterfaceSocket.description NodeTreeInterfaceSocket.socket_type NodeTreeInterfaceSocket.in_out NodeTreeInterfaceSocket.hide_value NodeTreeInterfaceSocket.hide_in_modifier | NodeTreeInterfaceSocket.force_non_field NodeTreeInterfaceSocket.is_inspect_output NodeTreeInterfaceSocket.is_panel_toggle NodeTreeInterfaceSocket.layer_selection_field NodeTreeInterfaceSocket.menu_expanded NodeTreeInterfaceSocket.optional_label NodeTreeInterfaceSocket.select NodeTreeInterfaceSocket.attribute_domain NodeTreeInterfaceSocket.default_attribute_name NodeTreeInterfaceSocket.structure_type NodeTreeInterfaceSocket.default_input NodeTreeInterfaceSocket.bl_socket_idname |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id | bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values NodeTreeInterfaceItem.bl_rna_get_subclass NodeTreeInterfaceItem.bl_rna_get_subclass_py NodeTreeInterfaceSocket.bl_system_properties_get NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocket.init_socket NodeTreeInterfaceSocket.from_socket NodeTreeInterfaceSocket.bl_rna_get_subclass NodeTreeInterfaceSocket.bl_rna_get_subclass_py |

## NodeTreePath(bpy_struct)

### NodeTreePath(bpy_struct) 

base class — bpy_struct

class bpy.types. NodeTreePath ( bpy_struct ) 

One entry along the node space's tree path

node_tree 

The root node tree taken from context (readonly)

Type :

NodeTree

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

| SpaceNodeEditor.path | |

## NoiseTexture(Texture)

### NoiseTexture(Texture) 

base classes — bpy_struct, ID, Texture

class bpy.types. NoiseTexture ( Texture ) 

A texture generated procedurally from noise

users_material 

The materials that reference this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier 

The object modifiers that reference this texture

Type :

tuple[Object, …]

Note

Takes O(len(bpy.data.objects) * len(obj.modifiers)) time.

(readonly)

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference | ID.asset_data ID.override_library ID.preview Texture.type Texture.use_clamp Texture.use_color_ramp Texture.color_ramp Texture.intensity Texture.contrast Texture.saturation Texture.factor_red Texture.factor_green Texture.factor_blue Texture.use_preview_alpha Texture.use_nodes Texture.node_tree Texture.animation_data Texture.users_material Texture.users_object_modifier |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast | bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py Texture.evaluate Texture.bl_rna_get_subclass Texture.bl_rna_get_subclass_py |

## OceanModifier(Modifier)

### OceanModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. OceanModifier ( Modifier ) 

Generate a simulated ocean surface

bake_foam_fade 

Rate at which foam builds up as time passes (baked ocean only) (in [0, inf], default 0.98)

Type :

float

choppiness 

How choppy the wave crests are (introduces a horizontal element to the displacement) (in [0, inf], default 1.0)

Type :

float

damping 

Damp reflected waves moving against the wind direction (in [0, 1], default 0.5)

Type :

float

depth 

Distance down to the solid floor beneath the water surface (in [-inf, inf], default 200.0)

Type :

float

fetch_jonswap 

The fetch — how far from a lee shore, or across what stretch the wind blows at steady speed. Applied by the ‘JONSWAP’ and ‘TMA’ models. (in [0, inf], default 120.0)

Type :

float

filepath 

Path to a folder to store external baked images (default “”, never None, blend relative // prefix supported)

Type :

str

foam_coverage 

How much foam gets generated (in [-inf, inf], default 0.0)

Type :

float

foam_layer_name 

Name of the vertex color layer used for foam (default “”, never None)

Type :

str

frame_end 

End frame of the ocean baking (in [-inf, inf], default 250)

Type :

int

frame_start 

Start frame of the ocean baking (in [-inf, inf], default 1)

Type :

int

geometry_mode 

Approach used to alter the geometry (default 'GENERATE' )

- GENERATE
Generate – Build ocean surface geometry at the chosen resolution.

- DISPLACE
Displace – Push existing geometry around to match the simulation.

Type :

Literal[‘GENERATE’, ‘DISPLACE’]

invert_spray 

Flip the spray direction map (default False)

Type :

bool

is_cached 

Whether the ocean draws on cached data or is simulating live (default False, readonly)

Type :

bool

random_seed 

Seed feeding the random generator (in [0, inf], default 0)

Type :

int

repeat_x 

How many times the generated surface tiles in X (in [1, 1024], default 1)

Type :

int

repeat_y 

How many times the generated surface tiles in Y (in [1, 1024], default 1)

Type :

int

resolution 

Resolution of the generated surface used for rendering and baking (in [1, 1024], default 7)

Type :

int

sharpen_peak_jonswap 

Peak sharpening applied by the ‘JONSWAP’ and ‘TMA’ models (in [0, 1], default 0.0)

Type :

float

size 

Scale factor for the surface (leaves the wave height unchanged) (in [0, inf], default 1.0)

Type :

float

spatial_size 

Extent of the simulation domain (in meters) and of the generated geometry (in BU) (in [-inf, inf], default 50)

Type :

int

spectrum 

Spectrum to use (default 'PHILLIPS' )

- PHILLIPS
Turbulent Ocean – Pick this for choppy seas with foam.

- `PIERSON_MOSKOWITZ`
Established Ocean – Pick this for a wide, established ocean (Pierson-Moskowitz method).

- JONSWAP
Established Ocean (Sharp Peaks) – Pick this for established oceans (‘JONSWAP’, Pierson-Moskowitz method) with peak sharpening.

- `TEXEL_MARSEN_ARSLOE`
Shallow Water – Pick this for shallow water (‘JONSWAP’, ‘TMA’ - Texel-Marsen-Arsloe method).

Type :

Literal[‘PHILLIPS’, ‘`PIERSON_MOSKOWITZ`’, ‘JONSWAP’, ‘`TEXEL_MARSEN_ARSLOE`’]

spray_layer_name 

Name of the vertex color layer used for the spray direction map (default “”, never None)

Type :

str

time 

The simulation's current time (in [0, inf], default 1.0)

Type :

float

use_foam 

Produce a foam mask stored as a vertex color channel (default False)

Type :

bool

use_normals 

Emit normals for bump mapping — turning this off can be faster when they aren't required (default False)

Type :

bool

use_spray 

Produce a spray-direction map stored as a vertex color channel (default False)

Type :

bool

viewport_resolution 

Viewport resolution of the generated surface (in [1, 1024], default 7)

Type :

int

wave_alignment 

Degree to which the waves line up with one another (in [0, 1], default 0.0)

Type :

float

wave_direction 

Dominant wave direction once they are (partly) aligned (in [-inf, inf], default 0.0)

Type :

float

wave_scale 

Strength of the displacement effect (in [0, inf], default 1.0)

Type :

float

wave_scale_min 

Smallest wavelength permitted (in [0, inf], default 0.01)

Type :

float

wind_velocity 

Speed of the wind (in [-inf, inf], default 30.0)

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

## PackedFile(bpy_struct)

### PackedFile(bpy_struct) 

base class — bpy_struct

class bpy.types. PackedFile ( bpy_struct ) 

A file from outside that has been packed into the .blend file

data 

Raw data (bytes, exact content of the embedded file) (default b””, readonly, never None)

Type :

bytes

size 

Size of packed file in bytes (in [-inf, inf], default 0, readonly)

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

| Image.packed_file ImagePackedFile.packed_file Library.packed_file | Sound.packed_file VectorFont.packed_file Volume.packed_file |

## Paint(bpy_struct)

### Paint(bpy_struct) 

base class — bpy_struct

subclasses —
CurvesSculpt, GpPaint, GpSculptPaint, GpVertexPaint, GpWeightPaint, ImagePaint, Sculpt, VertexPaint

class bpy.types. Paint ( bpy_struct ) 

brush 

Active brush (readonly)

Type :

Brush

brush_asset_reference 

A weak reference to the matching brush asset, used e.g. to restore the last used brush on file load (readonly)

Type :

AssetWeakReference

cavity_curve 

Editable cavity curve (readonly, never None)

Type :

CurveMapping

eraser_brush 

Default eraser brush for quickly alternating with the main brush

Type :

Brush

eraser_brush_asset_reference 

A weak reference to the matching brush asset, used e.g. to restore the last used brush on file load (readonly)

Type :

AssetWeakReference

palette 

Active Palette

Type :

Palette

show_brush 

(default True)

Type :

bool

show_brush_on_surface 

(default False)

Type :

bool

show_bvh_nodes 

Render the underlying BVH nodes as faces drawn in distinct colors (default False)

Type :

bool

show_jitter_curve 

(default False)

Type :

bool

show_low_resolution 

While navigating with multires, keep the display at low resolution (default False)

Type :

bool

show_size_curve 

(default False)

Type :

bool

show_strength_curve 

(default False)

Type :

bool

tile_offset 

Stride at which tiled strokes are copied (array of 3 items, in [0.01, inf], default (1.0, 1.0, 1.0))

Type :

mathutils.Vector

tile_x 

Tile along X axis (default False)

Type :

bool

tile_y 

Tile along Y axis (default False)

Type :

bool

tile_z 

Tile along Z axis (default False)

Type :

bool

unified_paint_settings 

(readonly, never None)

Type :

UnifiedPaintSettings

use_cavity 

Restrict mask painting to follow the mesh's surface cavities (default False)

Type :

bool

use_sculpt_delay_updates 

Refresh the geometry only as it comes into view, which speeds up navigating (default False)

Type :

bool

use_symmetry_feather 

Weaken the brush wherever it overlaps its symmetrical daubs (default True)

Type :

bool

use_symmetry_x 

Mirror brush across the X axis (default False)

Type :

bool

use_symmetry_y 

Mirror brush across the Y axis (default False)

Type :

bool

use_symmetry_z 

Mirror brush across the Z axis (default False)

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

## See also

- [Bpy Struct](bpy-struct.md)

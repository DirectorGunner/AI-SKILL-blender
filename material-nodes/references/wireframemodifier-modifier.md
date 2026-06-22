# Wireframemodifier Modifier, Woodtexture Texture, World Id, Bpy Utils Submodule Bpy Utils Previews ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: WireframeModifier(Modifier); WoodTexture(Texture); World(ID); bpy.utils submodule (bpy.utils.previews); bpy_extras submodule (bpy_extras.image_utils).

## WireframeModifier(Modifier)

### WireframeModifier(Modifier) 

base classes — bpy_struct, Modifier

class bpy.types. WireframeModifier ( Modifier ) 

A modifier that converts geometry into a wireframe

crease_weight 

Weight used for creasing, when creasing is on (in [-inf, inf], default 1.0)

Type :

float

invert_vertex_group 

Flip the effect of the chosen vertex group (default False)

Type :

bool

material_offset 

Shift the material slot index assigned to the new faces (in [-32768, 32767], default 0)

Type :

int

offset 

How far the thickness extends out from the midline (in [-inf, inf], default 0.0)

Type :

float

thickness 

Multiplier controlling wire thickness (in [-inf, inf], default 0.02)

Type :

float

thickness_vertex_group 

The thickness multiplier applied where vertex group weight is zero (in [0, 1], default 0.0)

Type :

float

use_boundary 

Also generate wires along open edges of the mesh (default False)

Type :

bool

use_crease 

Mark hub edges as creased so subdivision surfaces behave better (default False)

Type :

bool

use_even_offset 

Adjust the offset so wire thickness stays more uniform (default True)

Type :

bool

use_relative_offset 

Make the offset scale with nearby geometry (default False)

Type :

bool

use_replace 

Discard the source geometry, leaving only the wires (default True)

Type :

bool

vertex_group 

Name of the vertex group that limits which areas are affected (default “”, never None)

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

## WoodTexture(Texture)

### WoodTexture(Texture) 

base classes — bpy_struct, ID, Texture

class bpy.types. WoodTexture ( Texture ) 

A procedurally generated noise-based texture

nabla 

Step size of the offset used when deriving the surface normal (in [0.001, 0.1], default 0.025)

Type :

float

noise_basis 

The underlying noise function driving the turbulence (default '`BLENDER_ORIGINAL`' )

- `BLENDER_ORIGINAL`
Blender Original – Noise algorithm - Blender original: Smooth interpolated noise.

- `ORIGINAL_PERLIN`
Original Perlin – Noise algorithm - Original Perlin: Smooth interpolated noise.

- `IMPROVED_PERLIN`
Improved Perlin – Noise algorithm - Improved Perlin: Smooth interpolated noise.

- `VORONOI_F1`
Voronoi F1 – Noise algorithm - Voronoi F1: Returns distance to the closest feature point.

- `VORONOI_F2`
Voronoi F2 – Noise algorithm - Voronoi F2: Returns distance to the 2nd closest feature point.

- `VORONOI_F3`
Voronoi F3 – Noise algorithm - Voronoi F3: Returns distance to the 3rd closest feature point.

- `VORONOI_F4`
Voronoi F4 – Noise algorithm - Voronoi F4: Returns distance to the 4th closest feature point.

- `VORONOI_F2_F1`
Voronoi F2-F1 – Noise algorithm - Voronoi F1-F2.

- `VORONOI_CRACKLE`
Voronoi Crackle – Noise algorithm - Voronoi Crackle: Voronoi tessellation with sharp edges.

- `CELL_NOISE`
Cell Noise – Noise algorithm - Cell Noise: Square cell tessellation.

Type :

Literal[‘`BLENDER_ORIGINAL`’, ‘`ORIGINAL_PERLIN`’, ‘`IMPROVED_PERLIN`’, ‘`VORONOI_F1`’, ‘`VORONOI_F2`’, ‘`VORONOI_F3`’, ‘`VORONOI_F4`’, ‘`VORONOI_F2_F1`’, ‘`VORONOI_CRACKLE`’, ‘`CELL_NOISE`’]

noise_basis_2 

(default 'SIN' )

- SIN
Sine – Use a sine wave to produce bands.

- SAW
Saw – Use a saw wave to produce bands.

- TRI
Tri – Use a triangle wave to produce bands.

Type :

Literal[‘SIN’, ‘SAW’, ‘TRI’]

noise_scale 

Scale factor applied to the noise input (in [0.0001, inf], default 0.25)

Type :

float

noise_type 

(default '`SOFT_NOISE`' )

- `SOFT_NOISE`
Soft – Generate soft noise (smooth transitions).

- `HARD_NOISE`
Hard – Generate hard noise (sharp transitions).

Type :

Literal[‘`SOFT_NOISE`’, ‘`HARD_NOISE`’]

turbulence 

Amount of turbulence applied to the bandnoise and ringnoise variants (in [0.0001, inf], default 5.0)

Type :

float

wood_type 

(default 'BANDS' )

- BANDS
Bands – Use standard wood texture in bands.

- RINGS
Rings – Use wood texture in rings.

- BANDNOISE
Band Noise – Add noise to standard wood.

- RINGNOISE
Ring Noise – Add noise to rings.

Type :

Literal[‘BANDS’, ‘RINGS’, ‘BANDNOISE’, ‘RINGNOISE’]

users_material 

Materials that reference this texture

Type :

tuple[Material, …]

Note

Takes O(len(bpy.data.materials) * len(material.texture_slots)) time.

(readonly)

users_object_modifier 

Object modifiers that reference this texture

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

## World(ID)

### World(ID) 

base classes — bpy_struct, ID

class bpy.types. World ( ID ) 

A data-block holding a scene's environment and ambient lighting

animation_data 

Animation data attached to this data-block (readonly)

Type :

AnimData

color 

The background color (array of 3 items, in [0, inf], default (0.05, 0.05, 0.05))

Type :

mathutils.Color

cycles 

Cycles world settings (readonly)

Type :

CyclesWorldSettings

cycles_visibility 

Cycles visibility settings (readonly)

Type :

CyclesVisibilitySettings

light_settings 

Lighting configuration for the world (readonly, never None)

Type :

WorldLighting

lightgroup 

The light group this world is assigned to (default “”, never None)

Type :

str

mist_settings 

Mist configuration for the world (readonly, never None)

Type :

WorldMistSettings

node_tree 

The node tree used when the world is node-based (readonly)

Type :

NodeTree

probe_resolution 

Texture resolution used when the world is baked (default '1024' )

Type :

Literal[‘128’, ‘256’, ‘512’, ‘1024’, ‘2048’, ‘4096’]

sun_angle 

Apparent angular size of the Sun viewed from Earth (in [0, 3.14159], default 0.00918043)

Type :

float

sun_shadow_filter_radius 

Soften shadow stair-stepping with Percentage Closer Filtering (in [0, inf], default 1.0)

Type :

float

sun_shadow_jitter_overblur 

Run shadow tracing on every jittered sample to cut down on under-sampling artifacts (in [0, 100], default 10.0)

Type :

float

sun_shadow_maximum_resolution 

Largest allowed shadow-map texel size. Bigger values save memory but lower shadow fidelity. (in [0, inf], default 0.001)

Type :

float

sun_threshold 

When non-zero, caps the world contribution stored in the world light probe. Anything beyond that cap becomes a sun light, cutting the bleed from extremely bright sources. (in [0, inf], default 10.0)

Type :

float

use_eevee_finite_volume 

This world's volume was previously rendered by EEVEE Legacy and must be converted to render correctly. (default False)

Type :

bool

use_nodes 

Render the world through shader nodes (default False)

Deprecated since version 5.0: removal planned in version 6.0

Unused but kept for compatibility reasons. Setting the property has no effect, and getting it always returns True.

Type :

bool

use_sun_shadow 

Turn on shadow casting from the sun (default True)

Type :

bool

use_sun_shadow_jitter 

Switch on jittered soft shadows for finer shadow detail (off in the viewport unless turned on in the render settings). Carries a heavy performance cost. (default False)

Type :

bool

inline_shader_nodes ( ) 

Return this world's inlined shader nodes. Preprocessing flattens the node tree by stripping nested groups, repeat zones, and similar constructs.

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

| bpy.context.world BlendData.worlds BlendDataWorlds.new | BlendDataWorlds.remove Scene.world ViewLayer.world_override |

## bpy.utils submodule (bpy.utils.previews)

### bpy.utils submodule (bpy.utils.previews) 

Utility functions for working with custom previews live in this module.

It acts as a high-level "cached" manager for previews.

With it, scripts can build their own previews and apply them as icons in UI widgets
('icon_value' for UILayout functions).

### Custom Icon Example 

`text
### This sample script demonstrates how to place a custom icon on a button or
### menu entry.
#
### IMPORTANT NOTE: if you run this sample, there will be no icon in the button
### You need to replace the image path with a real existing one.
### For distributable scripts, it is recommended to place the icons inside the
### addon folder and access it relative to the py script file for portability
#
#
### Other use cases for UI-previews:
### - provide a fixed list of previews to select from
### - provide a dynamic list of preview (eg. calculated from reading a directory)
#
### For the above use cases, see the template `ui_previews_dynamic_enum.py`.

import os
import bpy

class PreviewsExamplePanel(bpy.types.Panel):
"""Creates a Panel in the Object properties window"""
bl_label = "Previews Example Panel"
bl_idname = "`OBJECT_PT`_previews"
bl_space_type = 'PROPERTIES'
bl_region_type = 'WINDOW'
bl_context = "object"

def draw(self, context):
layout = self.layout
pcoll = preview_collections["main"]

row = layout.row()
my_icon = pcoll["my_icon"]
row.operator("render.render", icon_value=my_icon.icon_id)

### my_icon.icon_id can be used in any UI function that accepts
### icon_value # try also setting text=""
### to get an icon only operator button

### We can store multiple preview collections here,
### however in this example we only store "main"
preview_collections = {}

def register():

### Note that preview collections returned by bpy.utils.previews
### are regular py objects - you can use them to store custom data.
import bpy.utils.previews
pcoll = bpy.utils.previews.new()

### path to the folder where the icon is
### the path is calculated relative to this py file inside the addon folder
my_icons_dir = os.path.join(os.path.dirname(__file__), "icons")

### load a preview thumbnail of a file and store in the previews collection
pcoll.load("my_icon", os.path.join(my_icons_dir, "icon-image.png"), 'IMAGE')

preview_collections["main"] = pcoll

bpy.utils.register_class(PreviewsExamplePanel)

def unregister():

for pcoll in preview_collections.values():
bpy.utils.previews.remove(pcoll)
preview_collections.clear()

bpy.utils.unregister_class(PreviewsExamplePanel)

if __name__ == "__main__":
register()
`

bpy.utils.previews. new ( ) 

Returns :

a new preview collection.

Return type :

ImagePreviewCollection

bpy.utils.previews. remove ( pcoll ) 

Discard the named previews collection.

Parameters :

pcoll (ImagePreviewCollection) – Preview collection to close.

class bpy.utils.previews. ImagePreviewCollection 

A dict-like container of previews.

It derives from Python's built-in dict type
and holds several image previews.

Note

- instance with bpy.utils.previews.new

- keys must be str type.

- values will be bpy.types.ImagePreview

clear ( ) 

Clear all previews.

close ( ) 

Shut the collection and wipe every preview.

load ( name , filepath , file_type , force_reload = False ) 

Build a new preview from the given file path.

Parameters :

- name ( str ) – The name (unique id) identifying the preview.

- filepath ( str | bytes ) – The file path to generate the preview from.

- file_type ( Literal [ 'IMAGE' , 'MOVIE' , 'BLEND' , 'FONT' , '`OBJECT_IO`' ] ) – The type of file, needed to generate the preview.

- force_reload ( bool ) – If True, run the thumbnail manager again even when the preview is already cached.

Returns :

The Preview matching given name, or a new empty one.

Return type :

bpy.types.ImagePreview

Raises :

KeyError – if name already exists.

new ( name ) 

Build a new empty preview.

Parameters :

name ( str ) – The name (unique id) identifying the preview.

Returns :

The Preview matching given name, or a new empty one.

Return type :

bpy.types.ImagePreview

Raises :

KeyError – if name already exists.

## bpy_extras submodule (bpy_extras.image_utils)

### bpy_extras submodule (bpy_extras.image_utils) 

bpy_extras.image_utils. load_image ( imagepath , dirname = '' , place_holder = False , recursive = False , ncase_cmp = True , convert_callback = None , verbose = False , relpath = None , check_existing = False , force_reload = False ) 

Hand back an image loaded from the file path, with options to search several
locations and to substitute a placeholder when nothing is found.

Parameters :

- imagepath ( str ) – The image filename
If a path precedes it, this will be searched as well.

- dirname ( str ) – is the directory where the image may be located - any file at
the end will be ignored.

- place_holder ( bool ) – if True a new place holder image will be created.
this is useful so later you can relink the image to its original data.

- recursive ( bool ) – If True, directories will be recursively searched.
Be careful with this if you have files in your root directory because
it may take a long time.

- ncase_cmp ( bool ) – on non windows systems, find the correct case for the file.

- convert_callback ( Callable [ [ str ] , str ] | None ) – a function that takes an existing path and returns
a new one. Use this when loading image formats blender may not support,
the `CONVERT_CALLBACK` can take the path for a GIF (for example),
convert it to a PNG and return the PNG's path.
For formats blender can read, simply return the path that is given.

- verbose ( bool ) – If True, print extra information when searching for the image.

- relpath ( str | None ) – If not None, make the file relative to this path.

- check_existing ( bool ) – If true,
returns already loaded image data-block if possible
(based on file path).

- force_reload ( bool ) – If true,
force reloading of image (only useful when check_existing
is also enabled).

Returns :

an image or None

Return type :

bpy.types.Image | None

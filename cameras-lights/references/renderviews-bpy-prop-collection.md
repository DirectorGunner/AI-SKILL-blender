# Renderviews Bpy Prop Collection, Scenehydra Bpy Struct, Screwmodifier Modifier, Shaderfx Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: RenderViews(bpy_prop_collection); SceneHydra(bpy_struct); ScrewModifier(Modifier); ShaderFx(bpy_struct); ShaderFxBlur(ShaderFx); ShaderFxColorize(ShaderFx); ShaderFxGlow(ShaderFx); ShaderFxPixel(ShaderFx); ShaderFxRim(ShaderFx); ShaderFxShadow(ShaderFx); ShaderFxWave(ShaderFx).

## RenderViews(bpy_prop_collection)

### RenderViews(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. RenderViews ( bpy_prop_collection )

Collection of render views

active

Active Render View (never None)

Type :

SceneRenderView

active_index

Active index in render view array (in [0, 32767], default 0)

Type :

int

new ( name )

Append a render view onto the scene

Parameters :

name ( str ) – New name for the marker (not unique) (never None)

Returns :

Newly created render view

Return type :

SceneRenderView

remove ( view )

Delete a render view

Parameters :

view (SceneRenderView) – Render view to remove (never None)

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

| RenderSettings.views | |

## SceneHydra(bpy_struct)

### SceneHydra(bpy_struct)

base class — bpy_struct

class bpy.types. SceneHydra ( bpy_struct )

Scene Hydra render engine settings

export_method

The route by which the Blender scene is sent to the Hydra render engine (default 'HYDRA' )

- HYDRA
Hydra – Quick interactive editing via the built-in Hydra integration.

- USD
USD – Send the scene out through a USD file, for an accurate match against USD file export.

Type :

Literal[‘HYDRA’, ‘USD’]

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

| Scene.hydra | |

## ScrewModifier(Modifier)

### ScrewModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ScrewModifier ( Modifier )

Sweeps edges around an axis to build a revolved surface.

angle

How far the profile is swept around the axis (in [-inf, inf], default 6.28319)

Type :

float

axis

Which axis the revolution turns about (default 'Z' )

Type :

Literal[Axis Xyz Items]

iterations

Count of repeated applications of the screw operation (in [1, 10000], default 1)

Type :

int

merge_threshold

Vertices closer together than this distance get welded (in [0, inf], default 0.01)

Type :

float

object

Object that supplies the screw axis

Type :

Object

render_steps

How many segments make up the sweep (in [1, 10000], default 16)

Type :

int

screw_offset

Shift applied along the axis as it revolves (in [-inf, inf], default 0.0)

Type :

float

steps

How many segments make up the sweep (in [1, 10000], default 16)

Type :

int

use_merge_vertices

Weld neighbouring vertices together; requires a screw offset of zero (default False)

Type :

bool

use_normal_calculate

Work out edge ordering, which meshes require though curves do not (default False)

Type :

bool

use_normal_flip

Reverse the normals on the lathed faces (default False)

Type :

bool

use_object_screw_offset

Derive the screw amount from the gap between the two objects (default False)

Type :

bool

use_smooth_shade

Emit smooth-shaded faces in place of flat ones (default True)

Type :

bool

use_stretch_u

When UVs exist, rescale the U coordinate to span 0 to 1 (default False)

Type :

bool

use_stretch_v

When UVs exist, rescale the V coordinate to span 0 to 1 (default False)

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

## ShaderFx(bpy_struct)

### ShaderFx(bpy_struct)

base class — bpy_struct

subclasses —
ShaderFxBlur, ShaderFxColorize, ShaderFxFlip, ShaderFxGlow, ShaderFxPixel, ShaderFxRim, ShaderFxShadow, ShaderFxSwirl, ShaderFxWave

class bpy.types. ShaderFx ( bpy_struct )

An effect that acts on the Grease Pencil object

name

A name for the effect (default “”, never None)

Type :

str

show_expanded

Whether the effect is expanded in the interface (default False)

Type :

bool

show_in_editmode

Render the effect while in Edit mode (default False)

Type :

bool

show_render

Apply the effect at render time (default False)

Type :

bool

show_viewport

Render the effect in the viewport (default False)

Type :

bool

type

(default '`FX_BLUR`' , readonly)

Type :

Literal[Object Shaderfx Type Items]

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

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Object.shader_effects ObjectShaderFx.new | ObjectShaderFx.remove |

## ShaderFxBlur(ShaderFx)

### ShaderFxBlur(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxBlur ( ShaderFx )

Gaussian Blur effect

rotation

How much the effect is turned (in [-inf, inf], default 0.0)

Type :

float

samples

Sample count for the blur, where zero turns blurring off (in [0, 32], default 4)

Type :

int

size

Strength of the blur (array of 2 items, in [0, inf], default (0.0, 0.0))

Type :

mathutils.Vector

use_dof_mode

Blur according to the camera's depth of field (default False)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxColorize(ShaderFx)

### ShaderFxColorize(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxColorize ( ShaderFx )

Colorize effect

factor

How strongly the colors are mixed (in [0, 1], default 0.0)

Type :

float

high_color

The effect's second color (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

low_color

The effect's first color (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

mode

Which mode the effect runs in (default 'GRAYSCALE' )

Type :

Literal[‘GRAYSCALE’, ‘SEPIA’, ‘DUOTONE’, ‘TRANSPARENT’, ‘CUSTOM’]

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxGlow(ShaderFx)

### ShaderFxGlow(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxGlow ( ShaderFx )

Glow effect

blend_mode

Which blend mode applies (default 'REGULAR' )

Type :

Literal[‘REGULAR’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’]

glow_color

The color the generated glow uses (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

mode

Which glow mode is active (default 'LUMINANCE' )

Type :

Literal[‘LUMINANCE’, ‘COLOR’]

opacity

How opaque the effect is (in [0, 1], default 0.0)

Type :

float

rotation

How much the effect is turned (in [-inf, inf], default 0.0)

Type :

float

samples

Sample count for the blur (in [1, 32], default 4)

Type :

int

select_color

The color picked out to receive the glow (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

size

How large the effect is (array of 2 items, in [0, inf], default (0.0, 0.0))

Type :

mathutils.Vector

threshold

Cutoff for picking the color that glows (in [0, 1], default 0.0)

Type :

float

use_glow_under

Glow only where alpha is present, which the Regular blend mode does not support (default False)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxPixel(ShaderFx)

### ShaderFxPixel(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxPixel ( ShaderFx )

Pixelate effect

size

The dimensions of each pixel block (array of 2 items, in [1, 32767], default (0, 0))

Type :

bpy_prop_array[int]

use_antialiasing

Smooth the edges of the pixels (default True)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxRim(ShaderFx)

### ShaderFxRim(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxRim ( ShaderFx )

Rim effect

blur

Pixel width used to soften the rim, with 0 turning it off (array of 2 items, in [0, 32767], default (0, 0))

Type :

bpy_prop_array[int]

mask_color

The color that should be preserved (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

mode

Which blend mode applies (default 'NORMAL' )

Type :

Literal[‘NORMAL’, ‘OVERLAY’, ‘ADD’, ‘SUBTRACT’, ‘MULTIPLY’, ‘DIVIDE’]

offset

How far the rim is shifted (array of 2 items, in [-32768, 32767], default (0, 0))

Type :

bpy_prop_array[int]

rim_color

The color applied to the rim (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

samples

Sample count for the blur, where zero turns blurring off (in [0, 32], default 4)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxShadow(ShaderFx)

### ShaderFxShadow(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxShadow ( ShaderFx )

Shadow effect

amplitude

Height of the wave (in [0, inf], default 0.0)

Type :

float

blur

Pixel width used to soften the shadow, with 0 turning it off (array of 2 items, in [0, 32767], default (0, 0))

Type :

bpy_prop_array[int]

object

Object that sets where the rotation centers

Type :

Object

offset

How far the shadow is shifted (array of 2 items, in [-32768, 32767], default (0, 0))

Type :

bpy_prop_array[int]

orientation

Which way the wave travels (default 'HORIZONTAL' )

Type :

Literal[‘HORIZONTAL’, ‘VERTICAL’]

period

Length of one wave cycle (in [0, inf], default 0.0)

Type :

float

phase

Offset applied to the wave's phase (in [-inf, inf], default 0.0)

Type :

float

rotation

Turn applied around the center or the object (in [-6.28319, 6.28319], default 0.0)

Type :

float

samples

Sample count for the blur, where zero turns blurring off (in [0, 32], default 4)

Type :

int

scale

How large the shadow is drawn (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

shadow_color

The color applied to the shadow (array of 4 items, in [0, 1], default (0.0, 0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

use_object

Treat the object as the rotation center (default False)

Type :

bool

use_wave

Turn on the wave effect (default False)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

## ShaderFxWave(ShaderFx)

### ShaderFxWave(ShaderFx)

base classes — bpy_struct, ShaderFx

class bpy.types. ShaderFxWave ( ShaderFx )

Wave Deformation effect

amplitude

Height of the wave (in [0, inf], default 0.0)

Type :

float

orientation

Which way the wave travels (default 'HORIZONTAL' )

Type :

Literal[‘HORIZONTAL’, ‘VERTICAL’]

period

Length of one wave cycle (in [0, inf], default 0.0)

Type :

float

phase

Offset applied to the wave's phase (in [-inf, inf], default 0.0)

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

| bpy_struct.id_data ShaderFx.name ShaderFx.type ShaderFx.show_viewport | ShaderFx.show_render ShaderFx.show_in_editmode ShaderFx.show_expanded |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values ShaderFx.bl_rna_get_subclass ShaderFx.bl_rna_get_subclass_py |

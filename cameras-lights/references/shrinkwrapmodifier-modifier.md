# Shrinkwrapmodifier Modifier, Simpledeformmodifier Modifier, Skinmodifier Modifier, Smoothmodifier Modifier ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ShrinkwrapModifier(Modifier); SimpleDeformModifier(Modifier); SkinModifier(Modifier); SmoothModifier(Modifier); SoftBodyModifier(Modifier); StudioLights(bpy_prop_collection); SubsurfModifier(Modifier); SurfaceDeformModifier(Modifier); SurfaceModifier(Modifier).

## ShrinkwrapModifier(Modifier)

### ShrinkwrapModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ShrinkwrapModifier ( Modifier )

A modifier that wraps an object's surface onto a target.

auxiliary_target

Additional mesh target to shrink to

Type :

Object

cull_face

Prevents vertices from projecting onto a target face that faces toward or away (default 'OFF' )

Type :

Literal[Shrinkwrap Face Cull Items]

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

offset

Distance to keep from the target (in [-inf, inf], default 0.0)

Type :

float

project_limit

Cap the distance allowed for projection (zero disables) (in [0, inf], default 0.0)

Type :

float

subsurf_levels

How many subdivisions to run before reading vertex positions and normals (in [0, 6], default 0)

Type :

int

target

Mesh target to shrink to

Type :

Object

use_invert_cull

When the projection runs the negative way, flip the face cull mode (default False)

Type :

bool

use_negative_direction

Permit vertices to travel along the axis's negative direction (default False)

Type :

bool

use_positive_direction

Permit vertices to travel along the axis's positive direction (default True)

Type :

bool

use_project_x

(default False)

Type :

bool

use_project_y

(default False)

Type :

bool

use_project_z

(default False)

Type :

bool

vertex_group

Vertex group name (default “”, never None)

Type :

str

wrap_method

(default '`NEAREST_SURFACEPOINT`' )

Type :

Literal[Shrinkwrap Type Items]

wrap_mode

Choose how vertices are held to the target surface (default '`ON_SURFACE`' )

Type :

Literal[Modifier Shrinkwrap Mode Items]

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

## SimpleDeformModifier(Modifier)

### SimpleDeformModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SimpleDeformModifier ( Modifier )

A straightforward deformation modifier for effects like twist and bend.

angle

Angle of deformation (in [-inf, inf], default 0.785398)

Type :

float

deform_axis

Deform around local axis (default 'X' )

Type :

Literal[Axis Xyz Items]

deform_method

(default 'TWIST' )

- TWIST
Twist – Spin the geometry about the modifier space's Z axis.

- BEND
Bend – Curve the mesh across the modifier space's Z axis.

- TAPER
Taper – Scale linearly down the modifier space's Z axis.

- STRETCH
Stretch – Elongate the object down the modifier space's Z axis.

Type :

Literal[‘TWIST’, ‘BEND’, ‘TAPER’, ‘STRETCH’]

factor

Amount to deform object (in [-inf, inf], default 0.785398)

Type :

float

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

limits

Lower/Upper limits for deform (array of 2 items, in [0, 1], default (0.0, 1.0))

Type :

bpy_prop_array[float]

lock_x

Do not allow deformation along the X axis (default False)

Type :

bool

lock_y

Do not allow deformation along the Y axis (default False)

Type :

bool

lock_z

Do not allow deformation along the Z axis (default False)

Type :

bool

origin

Offset the origin and orientation of the deformation

Type :

Object

vertex_group

Vertex group name (default “”, never None)

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

## SkinModifier(Modifier)

### SkinModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SkinModifier ( Modifier )

Generate Skin

branch_smoothing

Even out tangled geometry where branches meet (in [0, 1], default 0.0)

Type :

float

use_smooth_shade

Produce smooth-shaded faces instead of flat-shaded ones (default False)

Type :

bool

use_x_symmetry

Steer clear of asymmetric quads across the X axis (default True)

Type :

bool

use_y_symmetry

Steer clear of asymmetric quads across the Y axis (default False)

Type :

bool

use_z_symmetry

Steer clear of asymmetric quads across the Z axis (default False)

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

## SmoothModifier(Modifier)

### SmoothModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SmoothModifier ( Modifier )

A modifier that applies a smoothing effect.

factor

Strength of modifier effect (in [-inf, inf], default 0.5)

Type :

float

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

iterations

(in [0, 32767], default 1)

Type :

int

use_x

Smooth object along X axis (default True)

Type :

bool

use_y

Smooth object along Y axis (default True)

Type :

bool

use_z

Smooth object along Z axis (default True)

Type :

bool

vertex_group

Name of Vertex Group which determines influence of modifier per point (default “”, never None)

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

## SoftBodyModifier(Modifier)

### SoftBodyModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SoftBodyModifier ( Modifier )

A modifier that runs a soft body simulation.

point_cache

(readonly, never None)

Type :

PointCache

settings

(readonly, never None)

Type :

SoftBodySettings

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

## StudioLights(bpy_prop_collection)

### StudioLights(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. StudioLights ( bpy_prop_collection )

A group of studio lights.

load ( path , type )

Load studiolight from file

Parameters :

- path ( str ) – File Path, File path where the studio light file can be found (never None)

- type ( Literal [ 'STUDIO' , 'WORLD' , 'MATCAP' ] ) – Type, The type for the new studio light

Returns :

Newly created StudioLight

Return type :

StudioLight

new ( path )

Create studiolight from default lighting

Parameters :

path ( str ) – Path, Path to the file that will contain the lighting info (without extension) (never None)

Returns :

Newly created StudioLight

Return type :

StudioLight

remove ( studio_light )

Remove a studio light

Parameters :

studio_light (StudioLight) – The studio light to remove (never None)

refresh ( )

Refresh Studio Lights from disk

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

| Preferences.studio_lights | |

## SubsurfModifier(Modifier)

### SubsurfModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SubsurfModifier ( Modifier )

A subdivision surface modifier.

adaptive_object_edge_length

Target object space edge length for adaptive subdivision (in [0.0001, 1000], default 0.01)

Type :

float

adaptive_pixel_size

Target polygon pixel size for adaptive subdivision (in [0.1, 1000], default 1.0)

Type :

float

adaptive_space

How to adaptively subdivide the mesh (default 'PIXEL' )

- PIXEL
Pixel – Subdivide polygons to reach a specified pixel size on screen.

- OBJECT
Object – Subdivide to reach a specified edge length in object space. This is required to use adaptive subdivision for instanced meshes.

Type :

Literal[‘PIXEL’, ‘OBJECT’]

boundary_smooth

Controls how open boundaries are smoothed (default 'ALL' )

Type :

Literal[Subdivision Boundary Smooth Items]

levels

Number of subdivisions to perform in the 3D viewport (in [0, 11], default 1)

Type :

int

open_adaptive_subdivision_panel

(default False)

Type :

bool

open_advanced_panel

(default False)

Type :

bool

quality

How precisely vertices are placed; smaller numbers run faster yet with less accuracy (in [1, 10], default 3)

Type :

int

render_levels

Number of subdivisions to perform when rendering (in [0, 11], default 2)

Type :

int

show_only_control_edges

Skip displaying interior subdivided edges (default True)

Type :

bool

subdivision_type

Select type of subdivision algorithm (default '`CATMULL_CLARK`' )

- `CATMULL_CLARK`
Catmull-Clark – Create a smooth curved surface using the Catmull-Clark subdivision scheme.

- SIMPLE
Simple – Subdivide faces without changing shape.

Type :

Literal[‘`CATMULL_CLARK`’, ‘SIMPLE’]

use_adaptive_subdivision

Adaptively subdivide mesh based on camera distance (default False)

Type :

bool

use_creases

Use mesh crease information to sharpen edges or corners (default True)

Type :

bool

use_custom_normals

Interpolates existing custom normals to resulting mesh (default False)

Type :

bool

use_limit_surface

Snap vertices onto the limit surface an infinite subdivision would yield, giving the smoothest shape attainable (default True)

Type :

bool

uv_smooth

Controls how smoothing is applied to UVs (default '`PRESERVE_BOUNDARIES`' )

Type :

Literal[Subdivision Uv Smooth Items]

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

## SurfaceDeformModifier(Modifier)

### SurfaceDeformModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SurfaceDeformModifier ( Modifier )

falloff

Sets the degree to which neighbouring polygons sway the deformation (in [2, 16], default 4.0)

Type :

float

invert_vertex_group

Invert vertex group influence (default False)

Type :

bool

is_bound

Whether geometry has been bound to target mesh (default False, readonly)

Type :

bool

strength

Strength of modifier deformations (in [-100, 100], default 1.0)

Type :

float

target

Mesh object to deform with

Type :

Object

use_sparse_bind

At bind time, store binding data solely for the vertices that belong to the vertex group (default False)

Type :

bool

vertex_group

Vertex group name for selecting/weighting the affected areas (default “”, never None)

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

## SurfaceModifier(Modifier)

### SurfaceModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. SurfaceModifier ( Modifier )

A modifier that marks a stack position used by surface fields.

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

# Meshtovolumemodifier Modifier, Meshuvlooplayer Bpy Struct, Mirrormodifier Modifier, Modifier Bpy Struct ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MeshToVolumeModifier(Modifier); MeshUVLoopLayer(bpy_struct); MirrorModifier(Modifier); Modifier(bpy_struct); MovieReconstructedCamera(bpy_struct); MovieTracking(bpy_struct); MovieTrackingCamera(bpy_struct); MovieTrackingObject(bpy_struct).

## MeshToVolumeModifier(Modifier)

### MeshToVolumeModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MeshToVolumeModifier ( Modifier )

density

Density of the new volume (in [0, inf], default 0.0)

Type :

float

interior_band_width

Width of the gradient inside of the mesh (in [0, inf], default 0.0)

Type :

float

object

Object

Type :

Object

resolution_mode

Mode for how the desired voxel size is specified (default '`VOXEL_AMOUNT`' )

- `VOXEL_AMOUNT`
Voxel Amount – Desired number of voxels along one axis.

- `VOXEL_SIZE`
Voxel Size – Desired voxel side length.

Type :

Literal[‘`VOXEL_AMOUNT`’, ‘`VOXEL_SIZE`’]

voxel_amount

Approximate number of voxels along one axis (in [0, inf], default 0)

Type :

int

voxel_size

Smaller values result in a higher resolution output (in [0, inf], default 0.0)

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

## MeshUVLoopLayer(bpy_struct)

### MeshUVLoopLayer(bpy_struct)

base class — bpy_struct

class bpy.types. MeshUVLoopLayer ( bpy_struct )

active

Set the map as active for display and editing (default False)

Type :

bool

active_clone

Set the map as active for cloning (default False)

Type :

bool

active_render

Set the UV map as active for rendering (default False)

Type :

bool

data

Deprecated, use ‘uv’, ‘vertex_select’, ‘edge_select’ or ‘pin’ properties instead (default None, readonly)

Type :

bpy_prop_collection[MeshUVLoop]

name

Name of UV map (default "", never None)

Type :

str

pin

UV pinned state in the UV editor (default None, readonly)

Type :

bpy_prop_collection[BoolAttributeValue]

uv

UV coordinates on face corners (default None, readonly)

Type :

bpy_prop_collection[Float2AttributeValue]

pin_ensure ( )

pin_ensure

Returns :

The boolean attribute

Return type :

BoolAttribute

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

| Mesh.uv_layer_clone Mesh.uv_layer_stencil Mesh.uv_layers | UVLoopLayers.active UVLoopLayers.new UVLoopLayers.remove |

## MirrorModifier(Modifier)

### MirrorModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. MirrorModifier ( Modifier )

Modifier that mirrors geometry across an axis or plane

bisect_threshold

Vertices closer to the bisecting plane than this distance get removed (in [0, inf], default 0.001)

Type :

float

merge_threshold

Threshold under which a vertex and its mirror image are welded together (in [0, inf], default 0.001)

Type :

float

mirror_object

Object that defines the mirror reference

Type :

Object

mirror_offset_u

Shift applied to the mirrored UV flip line away from 0.5 along the U axis (in [-1, 1], default 0.0)

Type :

float

mirror_offset_v

Shift applied to the mirrored UV flip line away from the 0.5 mark along the V axis (in [-1, 1], default 0.0)

Type :

float

offset_u

Offset given to mirrored UVs along the U axis (in [-10000, 10000], default 0.0)

Type :

float

offset_v

Offset given to mirrored UVs along the V axis (in [-10000, 10000], default 0.0)

Type :

float

use_axis

Turn on mirroring along the axis (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

use_bisect_axis

Slices the mesh where it crosses the mirror plane (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

use_bisect_flip_axis

Reverses which side of the cut is kept (array of 3 items, default (False, False, False))

Type :

bpy_prop_array[bool]

use_clip

Stops vertices from crossing past the mirror while transforming (default False)

Type :

bool

use_mirror_merge

Weld together vertices that fall inside the merge threshold (default True)

Type :

bool

use_mirror_u

Reflect the U texture coordinate about the flip offset position (default False)

Type :

bool

use_mirror_udim

Reflect the texture coordinate about the center of every tile (default False)

Type :

bool

use_mirror_v

Reflect the V texture coordinate about the flip offset position (default False)

Type :

bool

use_mirror_vertex_groups

Mirror the vertex groups themselves (e.g. .R->.L) (default True)

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

## Modifier(bpy_struct)

### Modifier(bpy_struct)

base class — bpy_struct

subclasses —
ArmatureModifier, ArrayModifier, BevelModifier, BooleanModifier, BuildModifier, CastModifier, ClothModifier, CollisionModifier, CorrectiveSmoothModifier, CurveModifier, DataTransferModifier, DecimateModifier, DisplaceModifier, DynamicPaintModifier, EdgeSplitModifier, ExplodeModifier, FluidModifier, GreasePencilArmatureModifier, GreasePencilArrayModifier, GreasePencilBuildModifier, GreasePencilColorModifier, GreasePencilDashModifierData, GreasePencilEnvelopeModifier, GreasePencilHookModifier, GreasePencilLatticeModifier, GreasePencilLengthModifier, GreasePencilLineartModifier, GreasePencilMirrorModifier, GreasePencilMultiplyModifier, GreasePencilNoiseModifier, GreasePencilOffsetModifier, GreasePencilOpacityModifier, GreasePencilOutlineModifier, GreasePencilShrinkwrapModifier, GreasePencilSimplifyModifier, GreasePencilSmoothModifier, GreasePencilSubdivModifier, GreasePencilTextureModifier, GreasePencilThickModifierData, GreasePencilTimeModifier, GreasePencilTintModifier, GreasePencilWeightAngleModifier, GreasePencilWeightProximityModifier, HookModifier, LaplacianDeformModifier, LaplacianSmoothModifier, LatticeModifier, MaskModifier, MeshCacheModifier, MeshDeformModifier, MeshSequenceCacheModifier, MeshToVolumeModifier, MirrorModifier, MultiresModifier, NodesModifier, NormalEditModifier, OceanModifier, ParticleInstanceModifier, ParticleSystemModifier, RemeshModifier, ScrewModifier, ShrinkwrapModifier, SimpleDeformModifier, SkinModifier, SmoothModifier, SoftBodyModifier, SolidifyModifier, SubsurfModifier, SurfaceDeformModifier, SurfaceModifier, TriangulateModifier, UVProjectModifier, UVWarpModifier, VertexWeightEditModifier, VertexWeightMixModifier, VertexWeightProximityModifier, VolumeDisplaceModifier, VolumeToMeshModifier, WarpModifier, WaveModifier, WeightedNormalModifier, WeldModifier, WireframeModifier

class bpy.types. Modifier ( bpy_struct )

Base type for anything that operates on an object's geometry data

execution_time

How many seconds the modifier needed to evaluate. Populated only on evaluated objects, and unreliable when several modifiers evaluate concurrently. (in [-inf, inf], default 0.0, readonly)

Type :

float

is_active

Whether this is the currently active entry in the modifier list (default False)

Type :

bool

is_override_data

On a local override object, indicates whether the modifier originates from the linked reference or was added locally to the override (default True, readonly)

Type :

bool

name

Name given to the modifier (default “”, never None)

Type :

str

persistent_uid

Identifier that stays unique for the modifier inside its containing stack (in [-inf, inf], default 0, readonly)

Type :

int

show_expanded

Whether the modifier panel is unfolded in the interface (default False)

Type :

bool

show_in_editmode

Keep the modifier visible while in Edit mode (default False)

Type :

bool

show_on_cage

Make the edit cage follow the modifier output (default False)

Type :

bool

show_render

Apply the modifier when rendering (default False)

Type :

bool

show_viewport

Show the modifier result in the viewport (default False)

Type :

bool

type

(default '`GREASE_PENCIL_VERTEX_WEIGHT_PROXIMITY`' , readonly)

Type :

Literal[Object Modifier Type Items]

use_apply_on_spline

Run this modifier and every deform modifier before it on the control points of splines rather than on the tessellated curve/surface (default False)

Type :

bool

use_pin_to_last

Force the modifier to stay pinned to the bottom of the stack (default False)

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

| Object.modifiers ObjectModifiers.active | ObjectModifiers.new ObjectModifiers.remove |

## MovieReconstructedCamera(bpy_struct)

### MovieReconstructedCamera(bpy_struct)

base class — bpy_struct

class bpy.types. MovieReconstructedCamera ( bpy_struct )

Camera data reconstructed by the match-mover from the tracker

average_error

Mean reconstruction error (in [-inf, inf], default 0.0, readonly)

Type :

float

frame

Frame on which the marker holds a keyframe (in [-inf, inf], default 0, readonly)

Type :

int

matrix

Transformation matrix in world space (multi-dimensional array of 4 * 4 items, in [-inf, inf], default ((0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0), (0.0, 0.0, 0.0, 0.0)), readonly)

Type :

mathutils.Matrix

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

| MovieTrackingReconstructedCameras.find_frame | MovieTrackingReconstruction.cameras |

## MovieTracking(bpy_struct)

### MovieTracking(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTracking ( bpy_struct )

Container for match-moving tracking data

active_object_index

Position of the active object in the list (in [-inf, inf], default 0)

Type :

int

camera

(readonly)

Type :

MovieTrackingCamera

dopesheet

(readonly)

Type :

MovieTrackingDopesheet

objects

Set of objects belonging to this tracking data (default None, readonly)

Type :

MovieTrackingObjects[MovieTrackingObject]

plane_tracks

Set of plane tracks belonging to this tracking data. Deprecated, use objects[name].plane_tracks (default None, readonly)

Type :

MovieTrackingPlaneTracks[MovieTrackingPlaneTrack]

reconstruction

(readonly)

Type :

MovieTrackingReconstruction

settings

(readonly)

Type :

MovieTrackingSettings

stabilization

(readonly)

Type :

MovieTrackingStabilization

tracks

Set of tracks belonging to this tracking data. Deprecated, use objects[name].tracks (default None, readonly)

Type :

MovieTrackingTracks[MovieTrackingTrack]

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

| MovieClip.tracking | |

## MovieTrackingCamera(bpy_struct)

### MovieTrackingCamera(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingCamera ( bpy_struct )

Camera parameters used during match-moving tracking

brown_k1

Brown-Conrady fourth-order radial distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

brown_k2

Brown-Conrady fourth-order radial distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

brown_k3

Brown-Conrady fourth-order radial distortion, third coefficient (in [-inf, inf], default 0.0)

Type :

float

brown_k4

Brown-Conrady fourth-order radial distortion, fourth coefficient (in [-inf, inf], default 0.0)

Type :

float

brown_p1

Brown-Conrady second-order tangential distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

brown_p2

Brown-Conrady second-order tangential distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

distortion_model

Which distortion model applies to the camera lenses (default 'POLYNOMIAL' )

- POLYNOMIAL
Polynomial – Radial distortion model which fits common cameras.

- DIVISION
Divisions – Division distortion model which better represents wide-angle cameras.

- NUKE
Nuke – Nuke distortion model.

- BROWN
Brown – Brown-Conrady distortion model.

Type :

Literal[‘POLYNOMIAL’, ‘DIVISION’, ‘NUKE’, ‘BROWN’]

division_k1

Second-order division distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

division_k2

Second-order division distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

focal_length

Focal length of the camera (in [0.0001, inf], default 0.0)

Type :

float

focal_length_pixels

Focal length of the camera (in [0, inf], default 0.0)

Type :

float

k1

Third-order polynomial radial distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

k2

Third-order polynomial radial distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

k3

Third-order polynomial radial distortion, third coefficient (in [-inf, inf], default 0.0)

Type :

float

nuke_k1

Second-order Nuke distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

nuke_k2

Second-order Nuke distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

nuke_p1

Tangential Nuke distortion, first coefficient (in [-inf, inf], default 0.0)

Type :

float

nuke_p2

Tangential Nuke distortion, second coefficient (in [-inf, inf], default 0.0)

Type :

float

pixel_aspect

Aspect ratio of the pixels (in [0.1, inf], default 1.0)

Type :

float

principal_point

Lens optical center (array of 2 items, in [-1, 1], default (0.0, 0.0))

Type :

bpy_prop_array[float]

principal_point_pixels

Lens optical center, expressed in pixels (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

bpy_prop_array[float]

sensor_width

CCD sensor width, in millimeters (in [0, 500], default 0.0)

Type :

float

units

Which units the camera focal length uses (default 'PIXELS' )

- PIXELS
px – Use pixels for units of focal length.

- MILLIMETERS
mm – Use millimeters for units of focal length.

Type :

Literal[‘PIXELS’, ‘MILLIMETERS’]

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

| MovieTracking.camera | |

## MovieTrackingObject(bpy_struct)

### MovieTrackingObject(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingObject ( bpy_struct )

Tracking and reconstruction data for a match-moved object

is_camera

Whether the object serves as the camera-tracking object (default False, readonly)

Type :

bool

keyframe_a

First keyframe seeding the reconstruction (in [-inf, inf], default 0)

Type :

int

keyframe_b

Second keyframe seeding the reconstruction (in [-inf, inf], default 0)

Type :

int

name

Object's unique name (default “”, never None)

Type :

str

plane_tracks

Set of plane tracks belonging to this tracking data (default None, readonly)

Type :

MovieTrackingObjectPlaneTracks[MovieTrackingPlaneTrack]

reconstruction

(readonly)

Type :

MovieTrackingReconstruction

scale

Object-solution scale within camera space (in [0.0001, 10000], default 1.0)

Type :

float

tracks

Set of tracks belonging to this tracking data (default None, readonly)

Type :

MovieTrackingObjectTracks[MovieTrackingTrack]

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

| MovieTracking.objects MovieTrackingObjects.active | MovieTrackingObjects.new MovieTrackingObjects.remove |

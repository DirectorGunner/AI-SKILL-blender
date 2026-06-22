# Camera Id, Camerabackgroundimage Bpy Struct, Camerabackgroundimages Bpy Prop Collection, Cameradofsettings Bpy Struct

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Camera(ID); CameraBackgroundImage(bpy_struct); CameraBackgroundImages(bpy_prop_collection); CameraDOFSettings(bpy_struct).

## Camera(ID)

### Camera(ID)

base classes — bpy_struct, ID

class bpy.types. Camera ( ID )

Camera data-block containing optical and rendering settings

angle

Lens angle of view (in [0.00640536, 3.01675], default 0.69115)

Type :

float

angle_x

Lens horizontal angle of view (in [0.00640536, 3.01675], default 0.0)

Type :

float

angle_y

Lens vertical angle of view (in [0.00640536, 3.01675], default 0.0)

Type :

float

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

background_images

Set of reference images (default None, readonly)

Type :

CameraBackgroundImages[CameraBackgroundImage]

central_cylindrical_radius

Virtual cylinder radius (in [1e-05, inf], default 1.0)

Type :

float

central_cylindrical_range_u_max

Maximum horizontal angle for the central cylindrical lens (in [-inf, inf], default 3.14159)

Type :

float

central_cylindrical_range_u_min

Minimum horizontal angle for the central cylindrical lens (in [-inf, inf], default -3.14159)

Type :

float

central_cylindrical_range_v_max

Maximum vertical extent for the central cylindrical lens (in [-inf, inf], default 1.0)

Type :

float

central_cylindrical_range_v_min

Minimum vertical extent for the central cylindrical lens (in [-inf, inf], default -1.0)

Type :

float

clip_end

Far clipping plane distance from camera (in [1e-06, inf], default 1000.0)

Type :

float

clip_start

Near clipping plane distance from camera (in [1e-06, inf], default 0.1)

Type :

float

composition_guide_color

Overlay tint and opacity for composition guides (array of 4 items, in [0, inf], default (0.5, 0.5, 0.5, 1.0))

Type :

bpy_prop_array[float]

custom_bytecode

Compiled bytecode of the custom shader (default "", never None)

Type :

str

custom_bytecode_hash

Bytecode checksum for fast comparison (default "", never None)

Type :

str

custom_filepath

Shader file path for custom camera (default "", never None)

Type :

str

custom_mode

(default 'INTERNAL' )

- INTERNAL
Internal – Use internal text data-block.

- EXTERNAL
External – Use external file.

Type :

Literal['INTERNAL', 'EXTERNAL']

custom_shader

Shader for the custom camera

Type :

Text

cycles_custom

Settings for custom (OSL-based) cameras (readonly)

Type :

CyclesCustomCameraSettings

display_size

Viewport icon scale (in [0.01, 1000], default 1.0)

Type :

float

dof

(readonly)

Type :

CameraDOFSettings

fisheye_fov

Viewing angle for fisheye projection (in [0.1745, 31.4159], default 3.14159)

Type :

float

fisheye_lens

Focal length in millimeters (mm) (in [0.01, 100], default 10.5)

Type :

float

fisheye_polynomial_k0

Polynomial coefficient K0 (in [-inf, inf], default -1.17351e-05)

Type :

float

fisheye_polynomial_k1

Polynomial coefficient K1 (in [-inf, inf], default -0.0199887)

Type :

float

fisheye_polynomial_k2

Polynomial coefficient K2 (in [-inf, inf], default -3.3525e-06)

Type :

float

fisheye_polynomial_k3

Polynomial coefficient K3 (in [-inf, inf], default 3.0993e-06)

Type :

float

fisheye_polynomial_k4

Polynomial coefficient K4 (in [-inf, inf], default -2.61e-08)

Type :

float

latitude_max

Upper latitude boundary for equirectangular lens (in [-1.5708, 1.5708], default 1.5708)

Type :

float

latitude_min

Lower latitude boundary for equirectangular lens (in [-1.5708, 1.5708], default -1.5708)

Type :

float

lens

Focal length in millimeters (in [1, inf], default 50.0)

Type :

float

lens_unit

Display unit for focal length (default 'MILLIMETERS' )

- MILLIMETERS
Millimeters – Specify focal length of the lens in millimeters.

- FOV
Field of View – Specify the lens as the field of view's angle.

Type :

Literal['MILLIMETERS', 'FOV']

longitude_max

Upper horizontal boundary for equirectangular lens (in [-inf, inf], default 3.14159)

Type :

float

longitude_min

Lower horizontal boundary for equirectangular lens (in [-inf, inf], default -3.14159)

Type :

float

ortho_scale

Orthographic zoom level (in [0, inf], default 6.0)

Type :

float

panorama_type

Projection mode for panoramic rendering (default '`FISHEYE_EQUISOLID`' )

- EQUIRECTANGULAR
Equirectangular – Spherical camera for environment maps, also known as Lat Long panorama.

- `EQUIANGULAR_CUBEMAP_FACE`
Equiangular Cubemap Face – Single face of an equiangular cubemap.

- MIRRORBALL
Mirror Ball – Mirror ball mapping for environment maps.

- `FISHEYE_EQUIDISTANT`
Fisheye Equidistant – Ideal for fulldomes, ignore the sensor dimensions.

- `FISHEYE_EQUISOLID`
Fisheye Equisolid – Similar to most fisheye modern lens, takes sensor dimensions into consideration.

- `FISHEYE_LENS_POLYNOMIAL`
Fisheye Lens Polynomial – Defines the lens projection as polynomial to allow real world camera lenses to be mimicked.

- `CENTRAL_CYLINDRICAL`
Central Cylindrical – Projection onto a virtual cylinder from its center, similar as a rotating panoramic camera.

Type :

Literal['EQUIRECTANGULAR', '`EQUIANGULAR_CUBEMAP_FACE`', 'MIRRORBALL', '`FISHEYE_EQUIDISTANT`', '`FISHEYE_EQUISOLID`', '`FISHEYE_LENS_POLYNOMIAL`', '`CENTRAL_CYLINDRICAL`']

passepartout_alpha

Transparency of the darkened area outside frame (in [0, 1], default 0.5)

Type :

float

sensor_fit

Aspect scaling method (default 'AUTO' )

- AUTO
Auto – Fit to the sensor width or height depending on image resolution.

- HORIZONTAL
Horizontal – Fit to the sensor width.

- VERTICAL
Vertical – Fit to the sensor height.

Type :

Literal['AUTO', 'HORIZONTAL', 'VERTICAL']

sensor_height

Vertical sensor dimensions in millimeters (in [1, inf], default 24.0)

Type :

float

sensor_width

Horizontal sensor dimensions in millimeters (in [1, inf], default 36.0)

Type :

float

shift_x

Horizontal shift amount (in [-inf, inf], default 0.0)

Type :

float

shift_y

Vertical shift amount (in [-inf, inf], default 0.0)

Type :

float

show_background_images

Display background images behind objects (default False)

Type :

bool

show_composition_center

Show center guide in frame (default False)

Type :

bool

show_composition_center_diagonal

Show diagonal center guide in frame (default False)

Type :

bool

show_composition_golden

Show golden ratio guide in frame (default False)

Type :

bool

show_composition_golden_tria_a

Show golden triangle A guide in frame (default False)

Type :

bool

show_composition_golden_tria_b

Show golden triangle B guide in frame (default False)

Type :

bool

show_composition_harmony_tri_a

Show harmony A guide in frame (default False)

Type :

bool

show_composition_harmony_tri_b

Show harmony B guide in frame (default False)

Type :

bool

show_composition_thirds

Show rule of thirds grid in frame (default False)

Type :

bool

show_limits

Display focus point and clipping range (default False)

Type :

bool

show_mist

Draw line indicating mist distance (default False)

Type :

bool

show_name

Display camera name in frame view (default False)

Type :

bool

show_passepartout

Darken areas outside the frame (default True)

Type :

bool

show_safe_areas

Show title and action safe zones (default False)

Type :

bool

show_safe_center

Show safe zone for alternative aspect ratios (default False)

Type :

bool

show_sensor

Display film gate outline (default False)

Type :

bool

stereo

(readonly, never None)

Type :

CameraStereoData

type

Projection mode (default 'PERSP' )

Type :

Literal['PERSP', 'ORTHO', 'PANO', 'CUSTOM']

view_frame ( * , scene = None )

Get 4 corner points of the camera frame (pre-transformation)

Parameters :

scene (Scene) – Scene to use for aspect calculation, when omitted 1:1 aspect is used (optional)

Returns :

result_1 , Result, mathutils.Vector

result_2 , Result, mathutils.Vector

result_3 , Result, mathutils.Vector

result_4 , Result, mathutils.Vector

Return type :

tuple[mathutils.Vector, mathutils.Vector, mathutils.Vector, mathutils.Vector]

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.camera BlendData.cameras BlendDataCameras.new | BlendDataCameras.remove RenderEngine.update_custom_camera |

### Camera(ID)

Type :

bool

show_composition_thirds

Show rule of thirds grid in frame (default False)

Type :

bool

show_limits

Display focus point and clipping range (default False)

Type :

bool

show_mist

Draw line indicating mist distance (default False)

Type :

bool

show_name

Display camera name in frame view (default False)

Type :

bool

show_passepartout

Darken areas outside the frame (default True)

Type :

bool

show_safe_areas

Show title and action safe zones (default False)

Type :

bool

show_safe_center

Show safe zone for alternative aspect ratios (default False)

Type :

bool

show_sensor

Display film gate outline (default False)

Type :

bool

stereo

(readonly, never None)

Type :

CameraStereoData

type

Projection mode (default 'PERSP' )

Type :

Literal['PERSP', 'ORTHO', 'PANO', 'CUSTOM']

view_frame ( * , scene = None )

Get 4 corner points of the camera frame (pre-transformation)

Parameters :

scene (Scene) – Scene to use for aspect calculation, when omitted 1:1 aspect is used (optional)

Returns :

result_1 , Result, mathutils.Vector

result_2 , Result, mathutils.Vector

result_3 , Result, mathutils.Vector

result_4 , Result, mathutils.Vector

Return type :

tuple[mathutils.Vector, mathutils.Vector, mathutils.Vector, mathutils.Vector]

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References

| bpy.context.camera BlendData.cameras BlendDataCameras.new | BlendDataCameras.remove RenderEngine.update_custom_camera |

## CameraBackgroundImage(bpy_struct)

### CameraBackgroundImage(bpy_struct)

base class — bpy_struct

class bpy.types. CameraBackgroundImage ( bpy_struct )

Reference image and viewport display controls

alpha

Blending strength (in [0, 1], default 0.0)

Type :

float

clip

Movie clip for display and editing

Type :

MovieClip

clip_user

Frame selection for the movie clip (readonly, never None)

Type :

MovieClipUser

display_depth

Layer stacking order (default 'BACK' )

Type :

Literal['BACK', 'FRONT']

frame_method

How the image fits in the viewport (default 'FIT' )

Type :

Literal['STRETCH', 'FIT', 'CROP']

image

Image for display and editing

Type :

Image

image_user

Frame, layer, and pass selection (readonly, never None)

Type :

ImageUser

is_override_data

In a local override camera, whether this background image is local or inherited (default True, readonly)

Type :

bool

offset

(array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

rotation

Spin angle for ortho view (in [-inf, inf], default 0.0)

Type :

float

scale

Zoom factor (in [0, inf], default 0.0)

Type :

float

show_background_image

Include in viewport (default True)

Type :

bool

show_expanded

Display details (default False)

Type :

bool

show_on_foreground

Layer in front of geometry (default False)

Type :

bool

source

Image origin (default 'IMAGE' )

Type :

Literal['IMAGE', '`MOVIE_CLIP`']

use_camera_clip

Link to active scene camera's clip (default False)

Type :

bool

use_flip_x

Mirror image horizontally (default False)

Type :

bool

use_flip_y

Mirror image vertically (default False)

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

| Camera.background_images CameraBackgroundImages.new | CameraBackgroundImages.remove |

## CameraBackgroundImages(bpy_prop_collection)

### CameraBackgroundImages(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. CameraBackgroundImages ( bpy_prop_collection )

Group of background images

new ( )

Append a background image

Returns :

Newly added image

Return type :

CameraBackgroundImage

remove ( image )

Delete a background image

Parameters :

image (CameraBackgroundImage) – Image to remove (never None)

clear ( )

Remove all background images

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

| Camera.background_images | |

## CameraDOFSettings(bpy_struct)

### CameraDOFSettings(bpy_struct)

base class — bpy_struct

class bpy.types. CameraDOFSettings ( bpy_struct )

Depth of Field configuration

aperture_blades

Blade count for bokeh shape (minimum 3) (in [0, 16], default 0)

Type :

int

aperture_fstop

F-number (lower = more blur, higher = sharper) (in [0, inf], default 2.8)

Type :

float

aperture_ratio

Anamorphic bokeh distortion (in [0.01, inf], default 1.0)

Type :

float

aperture_rotation

Blade rotation angle (in [-3.14159, 3.14159], default 0.0)

Type :

float

focus_distance

Distance from camera to focal plane (in [0, inf], default 10.0)

Type :

float

focus_object

Object to use as focus point

Type :

Object

focus_subtarget

Armature bone or deforming group for focus (default "", never None)

Type :

str

use_dof

Activate depth of field (default False)

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

| Camera.dof | |

## See also

- [Bpy Struct](bpy-struct.md)

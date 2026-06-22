# Movieclip Id, Movieclipproxy Bpy Struct, Movieclipuser Bpy Struct, Movietrackingplanetrack Bpy Struct ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MovieClip(ID); MovieClipProxy(bpy_struct); MovieClipUser(bpy_struct); MovieTrackingPlaneTrack(bpy_struct); MovieTrackingSettings(bpy_struct); MovieTrackingTrack(bpy_struct).

## MovieClip(ID)

### MovieClip(ID)

base classes — bpy_struct, ID

class bpy.types. MovieClip ( ID )

A data-block that points at an external movie file

animation_data

Animation data attached to this data-block (readonly)

Type :

AnimData

annotation

Annotation data tied to this movie clip

Type :

Annotation

colorspace_settings

Settings for the input color space (readonly)

Type :

ColorManagedInputColorspaceSettings

display_aspect

Aspect ratio used for display only; it has no impact on rendering (array of 2 items, in [0.1, inf], default (1.0, 1.0))

Type :

mathutils.Vector

filepath

Path to the movie or image-sequence file (default “”, never None, blend relative // prefix supported)

Type :

str

fps

Frame rate detected from the movie clip, in frames per second (in [-inf, inf], default 0.0, readonly)

Type :

float

frame_duration

Length of the movie clip in frames, as detected (in [-inf, inf], default 0, readonly)

Type :

int

frame_offset

Shift of the footage's first frame relative to its filename; this only changes how footage loads and leaves the clip's data untouched (in [-inf, inf], default 0)

Type :

int

frame_start

Scene frame on which this movie begins playback; this touches every piece of data tied to the clip (in [-inf, inf], default 1)

Type :

int

proxy

(readonly)

Type :

MovieClipProxy

size

Pixel width and height; reports zero when the image data fails to load (array of 2 items, in [-inf, inf], default (0, 0), readonly)

Type :

bpy_prop_array[int]

source

Origin of the clip (default 'SEQUENCE' , readonly)

- SEQUENCE
Image Sequence – Multiple image files, as a sequence.

- MOVIE
Movie File – Movie file.

Type :

Literal[‘SEQUENCE’, ‘MOVIE’]

tracking

(readonly)

Type :

MovieTracking

use_proxy

Enable a preview proxy and/or timecode index for the clip (default False)

Type :

bool

use_proxy_custom_directory

Place proxy images in a directory you choose (default is movie location) (default False)

Type :

bool

metadata ( )

Retrieve metadata of the movie file

Returns :

Dict-like object containing the metadata

Return type :

IDPropertyWrapPtr

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

| bpy.context.edit_movieclip BlendData.movieclips BlendDataMovieClips.load BlendDataMovieClips.remove CameraBackgroundImage.clip CameraSolverConstraint.clip CompositorNodeKeyingScreen.clip CompositorNodeMovieClip.clip CompositorNodeMovieDistortion.clip CompositorNodePlaneTrackDeform.clip | CompositorNodeStabilize.clip CompositorNodeTrackPos.clip FollowTrackConstraint.clip MovieClipStrip.clip ObjectSolverConstraint.clip Scene.active_clip SpaceClipEditor.clip StripsMeta.new_clip StripsTopLevel.new_clip |

## MovieClipProxy(bpy_struct)

### MovieClipProxy(bpy_struct)

base class — bpy_struct

class bpy.types. MovieClipProxy ( bpy_struct )

Proxy configuration for a movie clip

build_100

Generate a proxy at the full 100% of the original footage resolution (default False)

Type :

bool

build_25

Generate a proxy at 25% of the original footage resolution (default True)

Type :

bool

build_50

Generate a proxy at 50% of the original footage resolution (default False)

Type :

bool

build_75

Generate a proxy at 75% of the original footage resolution (default False)

Type :

bool

build_record_run

Generate the record-run timecode index (default True)

Type :

bool

build_undistorted_100

Generate a proxy at the full 100% of the original undistorted footage resolution (default False)

Type :

bool

build_undistorted_25

Generate a proxy at 25% of the original undistorted footage resolution (default False)

Type :

bool

build_undistorted_50

Generate a proxy at 50% of the original undistorted footage resolution (default False)

Type :

bool

build_undistorted_75

Generate a proxy at 75% of the original undistorted footage resolution (default False)

Type :

bool

directory

Folder where the proxy files are kept (default “”, never None, blend relative // prefix supported)

Type :

str

quality

JPEG compression quality used for proxy images (in [0, 32767], default 50)

Type :

int

timecode

(default 'NONE' )

- NONE
None – Ignore generated timecodes, seek in movie stream based on calculated timestamp.

- `RECORD_RUN`
Record Run – Seek based on timestamps read from movie stream, giving the best match between scene and movie times.

- `FREE_RUN_NO_GAPS`
Record Run No Gaps – Effectively convert movie to an image sequence, ignoring incomplete or dropped frames, and changes in frame rate.

Type :

Literal[‘NONE’, ‘`RECORD_RUN`’, ‘`FREE_RUN_NO_GAPS`’]

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

| MovieClip.proxy | |

## MovieClipUser(bpy_struct)

### MovieClipUser(bpy_struct)

base class — bpy_struct

class bpy.types. MovieClipUser ( bpy_struct )

Settings that describe how one data-block consumes a MovieClip data-block

frame_current

Frame currently shown within the movie or image sequence (in [-1048574, 1048574], default 1)

Type :

int

proxy_render_size

Show the preview at full resolution or at one of the proxy resolutions (default 'FULL' )

Type :

Literal[‘`PROXY_25`’, ‘`PROXY_50`’, ‘`PROXY_75`’, ‘`PROXY_100`’, ‘FULL’]

use_render_undistorted

Render the preview from the undistorted proxy (default False)

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

| CameraBackgroundImage.clip_user SpaceClipEditor.clip_user | UILayout.template_marker UILayout.template_movieclip_information |

## MovieTrackingPlaneTrack(bpy_struct)

### MovieTrackingPlaneTrack(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingPlaneTrack ( bpy_struct )

Plane-track data used during match-moving tracking

image

Image shown over the track while editing it in the clip editor

Type :

Image

image_opacity

How opaque the image appears (in [0, 1], default 0.0)

Type :

float

markers

Set of markers held by the track (default None, readonly)

Type :

MovieTrackingPlaneMarkers[MovieTrackingPlaneMarker]

name

Track's unique name (default “”, never None)

Type :

str

select

Whether the plane track is selected (default False)

Type :

bool

use_auto_keying

Insert a keyframe automatically whenever plane corners are moved (default False)

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

| MovieTracking.plane_tracks MovieTrackingObject.plane_tracks | MovieTrackingPlaneTracks.active |

## MovieTrackingSettings(bpy_struct)

### MovieTrackingSettings(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingSettings ( bpy_struct )

Settings that govern match-moving

clean_action

Which cleanup action to run (default 'SELECT' )

- SELECT
Select – Select unclean tracks.

- `DELETE_TRACK`
Delete Track – Delete unclean tracks.

- `DELETE_SEGMENTS`
Delete Segments – Delete unclean segments of tracks.

Type :

Literal[‘SELECT’, ‘`DELETE_TRACK`’, ‘`DELETE_SEGMENTS`’]

clean_error

Applies to tracks whose re-projection error exceeds this value (in [0, inf], default 0.0)

Type :

float

clean_frames

Applies to tracks shorter than the given number of frames (in [0, inf], default 0)

Type :

int

default_correlation_min

Lowest correlation between the matched pattern and the reference that still counts as a successful track, by default (in [0, 1], default 0.0)

Type :

float

default_frames_limit

How many frames get tracked in each tracking cycle (in [0, 32767], default 0)

Type :

int

default_margin

Default border distance at which a marker stops tracking near the image edge (in [0, 300], default 0)

Type :

int

default_motion_model

Which motion model new tracks use by default (default 'Loc' )

- Perspective
Perspective – Search for markers that are perspectively deformed (homography) between frames.

- Affine
Affine – Search for markers that are affine-deformed (t, r, k, and skew) between frames.

- LocRotScale
Location, Rotation & Scale – Search for markers that are translated, rotated, and scaled between frames.

- LocScale
Location & Scale – Search for markers that are translated and scaled between frames.

- LocRot
Location & Rotation – Search for markers that are translated and rotated between frames.

- Loc
Location – Search for markers that are translated between frames.

Type :

Literal[‘Perspective’, ‘Affine’, ‘LocRotScale’, ‘LocScale’, ‘LocRot’, ‘Loc’]

default_pattern_match

Which reference frame the pattern is tracked from when advancing the marker to the next frame (default 'KEYFRAME' )

- KEYFRAME
Keyframe – Track pattern from keyframe to next frame.

- `PREV_FRAME`
Previous frame – Track pattern from current frame to next frame.

Type :

Literal[‘KEYFRAME’, ‘`PREV_FRAME`’]

default_pattern_size

Pattern-area size given to newly created tracks (in [5, 1000], default 0)

Type :

int

default_search_size

Search-area size given to newly created tracks (in [5, 1000], default 0)

Type :

int

default_weight

How much a newly created track contributes to the final solution (in [0, 1], default 0.0)

Type :

float

distance

Spacing between two bundles, used to scale the scene (in [-inf, inf], default 1.0)

Type :

float

object_distance

Spacing between two bundles, used to scale the object (in [0.001, 10000], default 1.0)

Type :

float

refine_intrinsics_focal_length

Adjust the focal length while solving the camera (default False)

Type :

bool

refine_intrinsics_principal_point

Adjust the principal point while solving the camera (default False)

Type :

bool

refine_intrinsics_radial_distortion

Adjust the distortion model's radial coefficients while solving the camera (default False)

Type :

bool

refine_intrinsics_tangential_distortion

Adjust the distortion model's tangential coefficients while solving the camera (default False)

Type :

bool

speed

Cap the tracking speed to make the visual feedback easier to follow (this leaves tracking quality unchanged) (default 'FASTEST' )

- FASTEST
Fastest – Track as fast as possible.

- DOUBLE
Double – Track with double speed.

- REALTIME
Realtime – Track with realtime speed.

- HALF
Half – Track with half of realtime speed.

- QUARTER
Quarter – Track with quarter of realtime speed.

Type :

Literal[‘FASTEST’, ‘DOUBLE’, ‘REALTIME’, ‘HALF’, ‘QUARTER’]

use_default_blue_channel

Track using the footage's blue channel (default True)

Type :

bool

use_default_brute

Begin tracking with a brute-force translation-only pass (default False)

Type :

bool

use_default_green_channel

Track using the footage's green channel (default True)

Type :

bool

use_default_mask

Mask with a Grease Pencil data-block so only chosen areas of the pattern are tracked (default False)

Type :

bool

use_default_normalization

Even out light intensities during tracking (slower) (default False)

Type :

bool

use_default_red_channel

Track using the footage's red channel (default True)

Type :

bool

use_keyframe_selection

Pick keyframes automatically while solving the camera or object motion (default False)

Type :

bool

use_tripod_solver

Engage the special solver meant for a fixed camera position such as a tripod (default False)

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

| MovieTracking.settings | |

## MovieTrackingTrack(bpy_struct)

### MovieTrackingTrack(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingTrack ( bpy_struct )

Track data used during match-moving tracking

annotation

Annotation data tied to this track

Type :

Annotation

average_error

Mean re-projection error (in [-inf, inf], default 0.0, readonly)

Type :

float

bundle

Location of the bundle reconstructed from this track (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0), readonly)

Type :

mathutils.Vector

color

Track color shown in the Movie Clip Editor and the 3D viewport once solved (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

correlation_min

Lowest correlation between the matched pattern and the reference that still counts as a successful track (in [0, 1], default 0.0)

Type :

float

frames_limit

How many frames get tracked in each tracking cycle (in [0, 32767], default 0)

Type :

int

has_bundle

True when the track carries a valid bundle (default False, readonly)

Type :

bool

hide

Whether the track is hidden (default False)

Type :

bool

lock

When locked, all edits to the track are blocked (default False)

Type :

bool

margin

Border distance at which a marker stops tracking near the image edge (in [0, 300], default 0)

Type :

int

markers

Set of markers held by the track (default None, readonly)

Type :

MovieTrackingMarkers[MovieTrackingMarker]

motion_model

Which motion model the track uses by default (default 'Loc' )

- Perspective
Perspective – Search for markers that are perspectively deformed (homography) between frames.

- Affine
Affine – Search for markers that are affine-deformed (t, r, k, and skew) between frames.

- LocRotScale
Location, Rotation & Scale – Search for markers that are translated, rotated, and scaled between frames.

- LocScale
Location & Scale – Search for markers that are translated and scaled between frames.

- LocRot
Location & Rotation – Search for markers that are translated and rotated between frames.

- Loc
Location – Search for markers that are translated between frames.

Type :

Literal[‘Perspective’, ‘Affine’, ‘LocRotScale’, ‘LocScale’, ‘LocRot’, ‘Loc’]

name

Track's unique name (default “”, never None)

Type :

str

offset

Track's offset from the parenting point (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

pattern_match

Which reference frame the pattern is tracked from when advancing the marker to the next frame (default 'KEYFRAME' )

- KEYFRAME
Keyframe – Track pattern from keyframe to next frame.

- `PREV_FRAME`
Previous frame – Track pattern from current frame to next frame.

Type :

Literal[‘KEYFRAME’, ‘`PREV_FRAME`’]

select

Whether the track is selected (default False)

Type :

bool

select_anchor

Whether the track's anchor point is selected (default False)

Type :

bool

select_pattern

Whether the track's pattern area is selected (default False)

Type :

bool

select_search

Whether the track's search area is selected (default False)

Type :

bool

use_alpha_preview

Apply the track's mask when drawing the preview (default False)

Type :

bool

use_blue_channel

Track using the footage's blue channel (default True)

Type :

bool

use_brute

Run a brute-force translation-only pre-track ahead of refinement (default False)

Type :

bool

use_custom_color

Use a personalized color rather than the theme default (default False)

Type :

bool

use_grayscale_preview

Show, in the preview, what the tracking algorithm actually sees (default False)

Type :

bool

use_green_channel

Track using the footage's green channel (default True)

Type :

bool

use_mask

Mask with a Grease Pencil data-block so only chosen areas of the pattern are tracked (default False)

Type :

bool

use_normalization

Even out light intensities during tracking (slower) (default False)

Type :

bool

use_red_channel

Track using the footage's red channel (default True)

Type :

bool

weight

How much this track contributes to the final solution (in [0, 1], default 0.0)

Type :

float

weight_stab

How much this track contributes to 2D stabilization (in [0, 1], default 0.0)

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

| bpy.context.selected_movieclip_tracks MovieTracking.tracks MovieTrackingObject.tracks MovieTrackingObjectPlaneTracks.active MovieTrackingObjectTracks.active MovieTrackingObjectTracks.new | MovieTrackingStabilization.rotation_tracks MovieTrackingStabilization.tracks MovieTrackingTracks.active MovieTrackingTracks.new UILayout.template_marker |

## See also

- [Bpy Struct](bpy-struct.md)

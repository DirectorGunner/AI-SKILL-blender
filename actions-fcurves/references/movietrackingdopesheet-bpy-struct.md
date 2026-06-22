# Movietrackingdopesheet Bpy Struct, Movietrackingmarker Bpy Struct, Movietrackingmarkers Bpy Prop Collection, Movietrackingobjectplanetracks Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MovieTrackingDopesheet(bpy_struct); MovieTrackingMarker(bpy_struct); MovieTrackingMarkers(bpy_prop_collection); MovieTrackingObjectPlaneTracks(bpy_prop_collection); MovieTrackingObjects(bpy_prop_collection); MovieTrackingObjectTracks(bpy_prop_collection); MovieTrackingPlaneMarker(bpy_struct); MovieTrackingPlaneMarkers(bpy_prop_collection); MovieTrackingPlaneTracks(bpy_prop_collection); MovieTrackingReconstruction(bpy_struct).

## MovieTrackingDopesheet(bpy_struct)

### MovieTrackingDopesheet(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingDopesheet ( bpy_struct )

Dopesheet data belonging to match-moving

show_hidden

Bring in channels from objects or bones that are not visible (default False)

Type :

bool

show_only_selected

Limit channels to those of the selected objects and data (default False)

Type :

bool

sort_method

Which ordering applies to channels in the dopesheet view (default 'NAME' )

- NAME
Name – Sort channels by their names.

- LONGEST
Longest – Sort channels by longest tracked segment.

- TOTAL
Total – Sort channels by overall amount of tracked segments.

- `AVERAGE_ERROR`
Average Error – Sort channels by average reprojection error of tracks after solve.

- START
Start Frame – Sort channels by first frame number.

- END
End Frame – Sort channels by last frame number.

Type :

Literal[‘NAME’, ‘LONGEST’, ‘TOTAL’, ‘`AVERAGE_ERROR`’, ‘START’, ‘END’]

use_invert_sort

Reverse the dopesheet channel ordering (default False)

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

| MovieTracking.dopesheet | |

## MovieTrackingMarker(bpy_struct)

### MovieTrackingMarker(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingMarker ( bpy_struct )

Marker data used during match-moving tracking

co

Where the marker sits on the frame, in normalized coordinates (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

frame

Frame on which the marker holds a keyframe (in [-inf, inf], default 0)

Type :

int

is_keyed

Whether the marker's position is keyframed rather than tracked (default True)

Type :

bool

mute

Whether the marker is muted on the current frame (default False)

Type :

bool

pattern_bound_box

Bounding box of the pattern area, in normalized coordinates (multi-dimensional array of 2 * 2 items, in [-inf, inf], default ((0.0, 0.0), (0.0, 0.0)), readonly)

Type :

bpy_prop_array[float]

pattern_corners

Coordinates of the pattern's corners, in normalized coordinates relative to the marker position (multi-dimensional array of 4 * 2 items, in [-inf, inf], default ((0.0, 0.0), (0.0, 0.0), (0.0, 0.0), (0.0, 0.0)))

Type :

bpy_prop_array[float]

search_max

Search-area top-right corner, in normalized coordinates relative to the marker position (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

search_min

Search-area bottom-left corner, in normalized coordinates relative to the marker position (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

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

| MovieTrackingMarkers.find_frame MovieTrackingMarkers.insert_frame | MovieTrackingTrack.markers |

## MovieTrackingMarkers(bpy_prop_collection)

### MovieTrackingMarkers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingMarkers ( bpy_prop_collection )

Set of markers attached to a movie-tracking track

find_frame ( frame , * , exact = True )

Get marker for specified frame

Parameters :

- frame ( int ) – Frame, Frame number to find marker for (in [0, 1048574])

- exact ( bool ) – Exact, Get marker at exact frame number rather than get estimated marker (optional)

Returns :

Marker for specified frame

Return type :

MovieTrackingMarker

insert_frame ( frame , * , co = (0.0, 0.0) )

Insert a new marker at the specified frame

Parameters :

- frame ( int ) – Frame, Frame number to insert marker to (in [0, 1048574])

- co (mathutils.Vector) – Coordinate, Place new marker at the given frame using specified in normalized space coordinates (array of 2 items, in [-1, 1], optional)

Returns :

Newly created marker

Return type :

MovieTrackingMarker

delete_frame ( frame )

Delete marker at specified frame

Parameters :

frame ( int ) – Frame, Frame number to delete marker from (in [0, 1048574])

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

| MovieTrackingTrack.markers | |

## MovieTrackingObjectPlaneTracks(bpy_prop_collection)

### MovieTrackingObjectPlaneTracks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingObjectPlaneTracks ( bpy_prop_collection )

Set of plane tracks used in tracking

active

The plane track currently active in this tracking data

Type :

MovieTrackingTrack

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

| MovieTrackingObject.plane_tracks | |

## MovieTrackingObjects(bpy_prop_collection)

### MovieTrackingObjects(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingObjects ( bpy_prop_collection )

Set of movie-tracking objects

active

The object currently active in this tracking data

Type :

MovieTrackingObject

new ( name )

Add tracking object to this movie clip

Parameters :

name ( str ) – Name of new object (never None)

Returns :

New motion tracking object

Return type :

MovieTrackingObject

remove ( object )

Remove tracking object from this movie clip

Parameters :

object (MovieTrackingObject) – Motion tracking object to be removed (never None)

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

| MovieTracking.objects | |

## MovieTrackingObjectTracks(bpy_prop_collection)

### MovieTrackingObjectTracks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingObjectTracks ( bpy_prop_collection )

Set of movie-tracking tracks

active

The track currently active in this tracking data

Type :

MovieTrackingTrack

new ( * , name = '' , frame = 1 )

create new motion track in this movie clip

Parameters :

- name ( str ) – Name of new track (optional, never None)

- frame ( int ) – Frame, Frame number to add tracks on (in [0, 1048574], optional)

Returns :

Newly created track

Return type :

MovieTrackingTrack

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

| MovieTrackingObject.tracks | |

## MovieTrackingPlaneMarker(bpy_struct)

### MovieTrackingPlaneMarker(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingPlaneMarker ( bpy_struct )

Plane-marker data used during match-moving tracking

corners

Coordinates representing the corners of the UI rectangle, in frame-normalized coordinates (multi-dimensional array of 4 * 2 items, in [-inf, inf], default ((0.0, 0.0), (0.0, 0.0), (0.0, 0.0), (0.0, 0.0)))

Type :

bpy_prop_array[float]

frame

Frame on which the marker holds a keyframe (in [-inf, inf], default 0)

Type :

int

mute

Whether the marker is muted on the current frame (default False)

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

| MovieTrackingPlaneMarkers.find_frame MovieTrackingPlaneMarkers.insert_frame | MovieTrackingPlaneTrack.markers |

## MovieTrackingPlaneMarkers(bpy_prop_collection)

### MovieTrackingPlaneMarkers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingPlaneMarkers ( bpy_prop_collection )

Set of markers attached to a movie-tracking plane track

find_frame ( frame , * , exact = True )

Get plane marker for specified frame

Parameters :

- frame ( int ) – Frame, Frame number to find marker for (in [0, 1048574])

- exact ( bool ) – Exact, Get plane marker at exact frame number rather than get estimated marker (optional)

Returns :

Plane marker for specified frame

Return type :

MovieTrackingPlaneMarker

insert_frame ( frame )

Insert a new plane marker at the specified frame

Parameters :

frame ( int ) – Frame, Frame number to insert marker to (in [0, 1048574])

Returns :

Newly created plane marker

Return type :

MovieTrackingPlaneMarker

delete_frame ( frame )

Delete plane marker at specified frame

Parameters :

frame ( int ) – Frame, Frame number to delete plane marker from (in [0, 1048574])

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

| MovieTrackingPlaneTrack.markers | |

## MovieTrackingPlaneTracks(bpy_prop_collection)

### MovieTrackingPlaneTracks(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MovieTrackingPlaneTracks ( bpy_prop_collection )

Set of movie-tracking plane tracks

active

The plane track currently active in this tracking data. Deprecated, use objects[name].plane_tracks.active

Type :

MovieTrackingPlaneTrack

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

| MovieTracking.plane_tracks | |

## MovieTrackingReconstruction(bpy_struct)

### MovieTrackingReconstruction(bpy_struct)

base class — bpy_struct

class bpy.types. MovieTrackingReconstruction ( bpy_struct )

Reconstruction data produced by the match-mover from the tracker

average_error

Mean reconstruction error (in [-inf, inf], default 0.0, readonly)

Type :

float

cameras

Set of solved cameras (default None, readonly)

Type :

MovieTrackingReconstructedCameras[MovieReconstructedCamera]

is_valid

Whether the tracking data holds usable reconstruction information (default False, readonly)

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

| MovieTracking.reconstruction | MovieTrackingObject.reconstruction |

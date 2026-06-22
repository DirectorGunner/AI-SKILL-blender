# Masklayers Bpy Prop Collection, Maskparent Bpy Struct, Maskspline Bpy Struct, Masksplinepoint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: MaskLayers(bpy_prop_collection); MaskParent(bpy_struct); MaskSpline(bpy_struct); MaskSplinePoint(bpy_struct); MaskSplinePoints(bpy_prop_collection); MaskSplinePointUW(bpy_struct); MaskSplines(bpy_prop_collection); MaskStrip(Strip); MaskStripModifier(StripModifier); MeshEdge(bpy_struct); MeshEdges(bpy_prop_collection).

## MaskLayers(bpy_prop_collection)

### MaskLayers(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MaskLayers ( bpy_prop_collection )

The group of layers belonging to a mask.

active

The layer currently active in this mask

Type :

MaskLayer

new ( * , name = '' )

Append a layer to this mask

Parameters :

name ( str ) – Name, Name of new layer (optional, never None)

Returns :

New mask layer

Return type :

MaskLayer

remove ( layer )

Delete a layer from this mask

Parameters :

layer (MaskLayer) – Shape to be removed (never None)

clear ( )

Delete every mask layer

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

| Mask.layers | |

## MaskParent(bpy_struct)

### MaskParent(bpy_struct)

base class — bpy_struct

class bpy.types. MaskParent ( bpy_struct )

Settings that parent a masking element.

id

ID-block that the masking element is parented to, or one of its properties

Type :

ID

id_type

Which kind of ID-block may be used (default 'MOVIECLIP' )

Type :

Literal[‘MOVIECLIP’]

parent

Name of the parent object inside the chosen data-block that drives the parenting (default “”, never None)

Type :

str

sub_parent

Name of the parent sub-object inside the chosen data-block that drives the parenting (default “”, never None)

Type :

str

type

Parent Type (default '`POINT_TRACK`' )

Type :

Literal[‘`POINT_TRACK`’, ‘`PLANE_TRACK`’]

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

| MaskSplinePoint.parent | |

## MaskSpline(bpy_struct)

### MaskSpline(bpy_struct)

base class — bpy_struct

class bpy.types. MaskSpline ( bpy_struct )

A single spline that helps define the mask's shape.

offset_mode

Which method computes the feather offset (default 'EVEN' )

- EVEN
Even – Calculate even feather offset.

- SMOOTH
Smooth – Calculate feather offset as a second curve.

Type :

Literal[‘EVEN’, ‘SMOOTH’]

points

Set of points (default None, readonly)

Type :

MaskSplinePoints[MaskSplinePoint]

use_cyclic

Close this spline into a loop (default False)

Type :

bool

use_fill

Fill this spline (default True)

Type :

bool

use_self_intersection_check

Stop the feather from crossing itself (default False)

Type :

bool

weight_interpolation

Interpolation mode used for the spline's weights (default 'LINEAR' )

Type :

Literal[‘LINEAR’, ‘EASE’]

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

| MaskLayer.splines MaskSplines.active | MaskSplines.new MaskSplines.remove |

## MaskSplinePoint(bpy_struct)

### MaskSplinePoint(bpy_struct)

base class — bpy_struct

class bpy.types. MaskSplinePoint ( bpy_struct )

A single point on a spline used to define the mask.

co

Coordinates of the control point (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

feather_points

Points that lay out the feather (default None, readonly)

Type :

bpy_prop_collection[MaskSplinePointUW]

handle_left

Coordinates of the first handle (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

handle_left_type

Handle type (default 'FREE' )

Type :

Literal[‘AUTO’, ‘VECTOR’, ‘ALIGNED’, ‘`ALIGNED_DOUBLESIDE`’, ‘FREE’]

handle_right

Coordinates of the second handle (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

handle_right_type

Handle type (default 'FREE' )

Type :

Literal[‘AUTO’, ‘VECTOR’, ‘ALIGNED’, ‘`ALIGNED_DOUBLESIDE`’, ‘FREE’]

handle_type

Handle type (default 'FREE' )

Type :

Literal[‘AUTO’, ‘VECTOR’, ‘ALIGNED’, ‘`ALIGNED_DOUBLESIDE`’, ‘FREE’]

parent

(readonly)

Type :

MaskParent

select

Selection status of the control point. (Deprecated: use Select Control Point instead) (default False)

Type :

bool

select_control_point

Selection status of the control point (default False)

Type :

bool

select_left_handle

Selection status of the left handle (default False)

Type :

bool

select_right_handle

Selection status of the right handle (default False)

Type :

bool

select_single_handle

Selection status of the Aligned Single handle (default False)

Type :

bool

weight

Weight of the point (in [0, 1], default 0.0)

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

| MaskSpline.points MaskSplinePoints.remove | MaskSplines.active_point |

## MaskSplinePoints(bpy_prop_collection)

### MaskSplinePoints(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MaskSplinePoints ( bpy_prop_collection )

The group of points belonging to a masking spline.

add ( count )

Insert a given number of points into this spline

Parameters :

count ( int ) – Number, Number of points to add to the spline (in [0, inf])

remove ( point )

Delete a point from a spline

Parameters :

point (MaskSplinePoint) – The point to remove (never None)

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

| MaskSpline.points | |

## MaskSplinePointUW(bpy_struct)

### MaskSplinePointUW(bpy_struct)

base class — bpy_struct

class bpy.types. MaskSplinePointUW ( bpy_struct )

A single point within a spline segment that defines the feather.

select

Selection status (default False)

Type :

bool

u

The point's U coordinate measured along the spline segment (in [0, 1], default 0.0)

Type :

float

weight

Weight of feather point (in [0, 1], default 0.0)

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

| MaskSplinePoint.feather_points | |

## MaskSplines(bpy_prop_collection)

### MaskSplines(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MaskSplines ( bpy_prop_collection )

The group of splines that shape a mask.

active

The spline currently active in this masking layer

Type :

MaskSpline

active_point

The point currently active in this masking layer

Type :

MaskSplinePoint

new ( )

Append a fresh spline to the layer

Returns :

The newly created spline

Return type :

MaskSpline

remove ( spline )

Delete a spline from a layer

Parameters :

spline (MaskSpline) – The spline to remove (never None)

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

| MaskLayer.splines | |

## MaskStrip(Strip)

### MaskStrip(Strip)

base classes — bpy_struct, Strip

class bpy.types. MaskStrip ( Strip )

A sequencer strip that pulls a video from a mask.

alpha_mode

How alpha is stored in the RGBA pixels (default 'STRAIGHT' )

- STRAIGHT
Straight – RGB channels in transparent pixels are unaffected by the alpha channel.

- PREMUL
Premultiplied – RGB channels in transparent pixels are multiplied by the alpha channel.

Type :

Literal[‘STRAIGHT’, ‘PREMUL’]

animation_offset_end

Animation end offset (trim end) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_end’.

Type :

int

animation_offset_start

Animation start offset (trim start) (in [0, inf], default 0)

Deprecated since version 5.10: removal planned in version 6.0

Replaced by ‘.content_trim_start’.

Type :

int

color_multiply

(in [0, 20], default 1.0)

Type :

float

color_saturation

Tune how saturated the input's color appears (in [0, 20], default 1.0)

Type :

float

content_trim_end

Frames dropped from the end of the underlying source; the source is trimmed and later frames become holds (in [0, inf], default 0)

Type :

int

content_trim_start

Frames dropped from the start of the underlying source; the source is trimmed and earlier frames become holds (in [0, inf], default 0)

Type :

int

crop

(readonly)

Type :

StripCrop

mask

Mask consumed by this strip

Type :

Mask

multiply_alpha

Scale alpha together with the color channels (default False)

Type :

bool

strobe

Show only every nth frame (in [1, 30], default 0.0)

Type :

float

transform

(readonly)

Type :

StripTransform

use_deinterlace

Strip fields out of video footage (default False)

Type :

bool

use_flip_x

Flip on the X axis (default False)

Type :

bool

use_flip_y

Flip on the Y axis (default False)

Type :

bool

use_float

Convert the input into float data (default False)

Type :

bool

use_reverse_frames

Play the frames back in reverse (default False)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start | Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py |

## MaskStripModifier(StripModifier)

### MaskStripModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. MaskStripModifier ( StripModifier )

A mask modifier applied to a sequence strip.

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

| bpy_struct.id_data StripModifier.name StripModifier.type StripModifier.mute StripModifier.enable StripModifier.show_expanded | StripModifier.input_mask_type StripModifier.mask_time StripModifier.input_mask_strip StripModifier.input_mask_id StripModifier.is_active |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values StripModifier.bl_rna_get_subclass StripModifier.bl_rna_get_subclass_py |

## MeshEdge(bpy_struct)

### MeshEdge(bpy_struct)

base class — bpy_struct

class bpy.types. MeshEdge ( bpy_struct )

Edge in a Mesh data-block

hide

(default False)

Type :

bool

index

Index of this edge (in [0, inf], default 0, readonly)

Type :

int

is_loose

Edge is not connected to any faces (default False, readonly)

Type :

bool

select

(default False)

Type :

bool

use_edge_sharp

Sharp edge for shading (default False)

Type :

bool

use_seam

Seam edge for UV unwrapping (default False)

Type :

bool

vertices

Vertex indices (array of 2 items, in [0, inf], default (0, 0))

Type :

bpy_prop_array[int]

key

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

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| Mesh.edges | |

## MeshEdges(bpy_prop_collection)

### MeshEdges(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. MeshEdges ( bpy_prop_collection )

Collection of mesh edges

add ( count )

add

Parameters :

count ( int ) – Count, Number of edges to add (in [0, inf])

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

| Mesh.edges | |

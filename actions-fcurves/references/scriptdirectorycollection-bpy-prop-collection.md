# Scriptdirectorycollection Bpy Prop Collection, Sculpt Paint, Selecteduvelement Propertygroup, Sequencer Fh Image Strip Filehandler ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ScriptDirectoryCollection(bpy_prop_collection); Sculpt(Paint); SelectedUvElement(PropertyGroup); `SEQUENCER_FH`_image_strip(FileHandler); `SEQUENCER_FH`_movie_strip(FileHandler); `SEQUENCER_FH`_sound_strip(FileHandler); SequencerPreviewOverlay(bpy_struct); SequencerTimelineOverlay(bpy_struct); SequencerToolSettings(bpy_struct).

## ScriptDirectoryCollection(bpy_prop_collection)

### ScriptDirectoryCollection(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. ScriptDirectoryCollection ( bpy_prop_collection )

classmethod new ( )

Register an additional Python script directory

Return type :

ScriptDirectory

classmethod remove ( script_directory )

Delete one of the Python script directories

Parameters :

script_directory (ScriptDirectory) – (never None)

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

| PreferencesFilePaths.script_directories | |

## Sculpt(Paint)

### Sculpt(Paint)

base classes — bpy_struct, Paint

class bpy.types. Sculpt ( Paint )

automasking_boundary_edges_propagation_steps

How far inward from a fully masked edge the boundary-edge automask keeps shielding vertices (in [1, 20], default 1)

Type :

int

automasking_cavity_blur_steps

How many blur passes are run over the cavity mask (in [0, 25], default 0)

Type :

int

automasking_cavity_curve

Curve that drives the sensitivity (readonly)

Type :

CurveMapping

automasking_cavity_curve_op

Curve that drives the sensitivity (readonly)

Type :

CurveMapping

automasking_cavity_factor

Contrast applied to the cavity mask (in [0, 5], default 1.0)

Type :

float

automasking_start_normal_falloff

Widen the angular band with a graded falloff (in [0.0001, 1], default 0.25)

Type :

float

automasking_start_normal_limit

Span of angles that gets affected (in [0.0001, 3.14159], default 0.349066)

Type :

float

automasking_view_normal_falloff

Widen the angular band with a graded falloff (in [0.0001, 1], default 0.25)

Type :

float

automasking_view_normal_limit

Span of angles that gets affected (in [0.0001, 3.14159], default 1.5708)

Type :

float

constant_detail_resolution

Longest edge allowed in dynamic-topology sculpting, expressed as a divisor of the Blender unit so larger values yield shorter edges (in [0.0001, inf], default 3.0)

Type :

float

detail_percent

Longest edge allowed in dynamic-topology sculpting, given as a percentage of brush size (in [0.5, 100], default 25.0)

Type :

float

detail_refine_method

Within dynamic-topology mode, the way mesh detail gets added or stripped away (default '`SUBDIVIDE_COLLAPSE`' )

- SUBDIVIDE
Subdivide Edges – Split long edges so extra detail appears wherever it is required.

- COLLAPSE
Collapse Edges – Merge short edges to strip out detail wherever that is feasible.

- `SUBDIVIDE_COLLAPSE`
Subdivide Collapse – Combine both: split long edges and merge short ones to refine the detail.

Type :

Literal[‘SUBDIVIDE’, ‘COLLAPSE’, ‘`SUBDIVIDE_COLLAPSE`’]

detail_size

Longest edge allowed in dynamic-topology sculpting, measured in pixels (in [0.5, 40], default 12.0)

Type :

float

detail_type_method

Within dynamic-topology mode, the basis on which detail size is figured (default 'RELATIVE' )

- RELATIVE
Relative Detail – Detail is gauged against both brush size and the detail-size setting.

- CONSTANT
Constant Detail – Detail stays fixed in world space at the chosen detail size.

- BRUSH
Brush Detail – Detail scales with brush size alone.

- MANUAL
Manual Detail – Detail holds steady across strokes and only updates on a Flood Fill.

Type :

Literal[‘RELATIVE’, ‘CONSTANT’, ‘BRUSH’, ‘MANUAL’]

gravity

Strength of the gravity pull applied per dab (in [0, 1], default 0.0)

Type :

float

gravity_object

Object whose Z axis sets the gravity direction

Type :

Object

lock_x

Block any movement of vertices along the X axis (default False)

Type :

bool

lock_y

Block any movement of vertices along the Y axis (default False)

Type :

bool

lock_z

Block any movement of vertices along the Z axis (default False)

Type :

bool

symmetrize_direction

Which side feeds which for the symmetrize operator (default '`NEGATIVE_X`' )

Type :

Literal[Symmetrize Direction Items]

transform_mode

The manner in which the transform is carried over to the target (default '`ALL_VERTICES`' )

- `ALL_VERTICES`
All Vertices – Carries the transform across every vertex of the mesh.

- `RADIUS_ELASTIC`
Elastic – Carries the transform with an elastic simulation driven by the cursor radius.

Type :

Literal[‘`ALL_VERTICES`’, ‘`RADIUS_ELASTIC`’]

use_automasking_boundary_edges

Leave non-manifold boundary edges untouched (default False)

Type :

bool

use_automasking_boundary_face_sets

Leave vertices sitting on a face-set boundary untouched (default False)

Type :

bool

use_automasking_cavity

Skip vertices on peaks, judged from how the surface curves (default False)

Type :

bool

use_automasking_cavity_inverted

Skip vertices down in crevices, judged from how the surface curves (default False)

Type :

bool

use_automasking_custom_cavity_curve

Apply a user-defined curve (default False)

Type :

bool

use_automasking_face_sets

Touch only vertices sharing face sets with the active vertex (default False)

Type :

bool

use_automasking_start_normal

Touch only vertices whose normal resembles the one where the stroke began (default False)

Type :

bool

use_automasking_topology

Touch only vertices linked to the active vertex beneath the brush (default False)

Type :

bool

use_automasking_view_normal

Touch only vertices whose normal points back toward the viewer (default False)

Type :

bool

use_automasking_view_occlusion

Touch only vertices left unhidden by other faces, at a performance cost (default False)

Type :

bool

use_deform_only

Apply deformation modifiers alone, temporarily switching off every constructive modifier apart from multi-resolution (default False)

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

| bpy_struct.id_data Paint.brush Paint.brush_asset_reference Paint.eraser_brush Paint.eraser_brush_asset_reference Paint.palette Paint.show_brush Paint.show_brush_on_surface Paint.show_low_resolution Paint.use_sculpt_delay_updates Paint.show_bvh_nodes Paint.use_symmetry_x Paint.use_symmetry_y | Paint.use_symmetry_z Paint.use_symmetry_feather Paint.cavity_curve Paint.use_cavity Paint.tile_offset Paint.tile_x Paint.tile_y Paint.tile_z Paint.show_strength_curve Paint.show_size_curve Paint.show_jitter_curve Paint.unified_paint_settings |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Paint.bl_rna_get_subclass Paint.bl_rna_get_subclass_py |

### References

| ToolSettings.sculpt | |

## SelectedUvElement(PropertyGroup)

### SelectedUvElement(PropertyGroup)

base classes — bpy_struct, PropertyGroup

class bpy.types. SelectedUvElement ( PropertyGroup )

element_index

(in [0, inf], default 0)

Type :

int

face_index

(in [0, inf], default 0)

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

| bpy_struct.id_data | PropertyGroup.name |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values PropertyGroup.bl_system_properties_get PropertyGroup.bl_rna_get_subclass PropertyGroup.bl_rna_get_subclass_py |

## `SEQUENCER_FH`_image_strip(FileHandler)

### `SEQUENCER_FH`_image_strip(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `SEQUENCER_FH`_image_strip ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## `SEQUENCER_FH`_movie_strip(FileHandler)

### `SEQUENCER_FH`_movie_strip(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `SEQUENCER_FH`_movie_strip ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## `SEQUENCER_FH`_sound_strip(FileHandler)

### `SEQUENCER_FH`_sound_strip(FileHandler)

base classes — bpy_struct, FileHandler

class bpy.types. `SEQUENCER_FH`_sound_strip ( FileHandler )

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

| bpy_struct.id_data FileHandler.bl_idname FileHandler.bl_import_operator | FileHandler.bl_export_operator FileHandler.bl_label FileHandler.bl_file_extensions |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values FileHandler.poll_drop FileHandler.bl_rna_get_subclass FileHandler.bl_rna_get_subclass_py |

## SequencerPreviewOverlay(bpy_struct)

### SequencerPreviewOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SequencerPreviewOverlay ( bpy_struct )

show_annotation

Draw the annotations belonging to this view (default False)

Type :

bool

show_cursor

(default False)

Type :

bool

show_image_outline

(default False)

Type :

bool

show_metadata

Display the metadata from the first strip that is visible (default False)

Type :

bool

show_safe_areas

Overlay TV title-safe and action-safe regions on the preview (default False)

Type :

bool

show_safe_center

Overlay safe regions for fitting content into another aspect ratio (default False)

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

| SpaceSequenceEditor.preview_overlay | |

## SequencerTimelineOverlay(bpy_struct)

### SequencerTimelineOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SequencerTimelineOverlay ( bpy_struct )

show_fcurves

Draw the opacity or volume curve of strips (default False)

Type :

bool

show_grid

Draw vertical grid lines (default False)

Type :

bool

show_strip_duration

(default False)

Type :

bool

show_strip_name

(default False)

Type :

bool

show_strip_offset

Draw the in and out offsets of strips (default False)

Type :

bool

show_strip_retiming

Draw retiming keys over the top of strips (default False)

Type :

bool

show_strip_source

Draw the source file path, or the source data-block name (default False)

Type :

bool

show_strip_tag_color

Draw the color tags of strips in the sequencer (default False)

Type :

bool

show_thumbnails

Draw thumbnail previews on strips (default False)

Type :

bool

waveform_display_style

The way waveforms get drawn (default '`FULL_WAVEFORMS`' )

- `FULL_WAVEFORMS`
Full – Draw the complete waveform.

- `HALF_WAVEFORMS`
Half – Draw only the top half of the absolute-value waveform.

Type :

Literal[‘`FULL_WAVEFORMS`’, ‘`HALF_WAVEFORMS`’]

waveform_display_type

The way waveforms get drawn (default '`DEFAULT_WAVEFORMS`' )

- `ALL_WAVEFORMS`
On – Draw waveforms across every sound strip.

- `DEFAULT_WAVEFORMS`
Strip – Draw waveforms based on each strip's own setting.

- `NO_WAVEFORMS`
Off – Suppress waveforms on all sound strips.

Type :

Literal[‘`ALL_WAVEFORMS`’, ‘`DEFAULT_WAVEFORMS`’, ‘`NO_WAVEFORMS`’]

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

| SpaceSequenceEditor.timeline_overlay | |

## SequencerToolSettings(bpy_struct)

### SequencerToolSettings(bpy_struct)

base class — bpy_struct

class bpy.types. SequencerToolSettings ( bpy_struct )

fit_method

Method used to scale and fit (default 'FIT' )

Type :

Literal[Strip Scale Method Items]

overlap_mode

The way overlaps are settled once a transform is applied (default 'EXPAND' )

- EXPAND
Expand – Push strips aside so the transformed ones fit.

- OVERWRITE
Overwrite – Cut or split strips so the overlap goes away.

- SHUFFLE
Shuffle – Relocate transformed strips into the closest open gap to clear the overlap.

Type :

Literal[‘EXPAND’, ‘OVERWRITE’, ‘SHUFFLE’]

pivot_point

Point used as the center of rotation or scaling (default 'CENTER' )

- CENTER
Bounding Box Center.

- MEDIAN
Median Point.

- CURSOR
2D Cursor – Rotate or scale about the 2D cursor.

- `INDIVIDUAL_ORIGINS`
Individual Origins – Rotate or scale about each selected island's own median point.

Type :

Literal[‘CENTER’, ‘MEDIAN’, ‘CURSOR’, ‘`INDIVIDUAL_ORIGINS`’]

snap_distance

Largest pixel gap that still allows a snap (in [-inf, inf], default 15)

Type :

int

snap_ignore_muted

Skip snapping onto strips that are hidden (default False)

Type :

bool

snap_ignore_sound

Skip snapping onto sound strips (default False)

Type :

bool

snap_to_borders

Snap onto the borders of the preview (default False)

Type :

bool

snap_to_center

Snap onto the center of the preview (default False)

Type :

bool

snap_to_current_frame

Snap onto the current frame (default False)

Type :

bool

snap_to_frame_range

Snap onto the start and end frame of the preview or scene (default False)

Type :

bool

snap_to_hold_offset

Snap onto the start and end of a strip's underlying content when the strip runs past that range and creates holds (default False)

Type :

bool

snap_to_markers

Snap onto markers (default False)

Type :

bool

snap_to_retiming_keys

Snap onto retiming keys (default False)

Type :

bool

snap_to_strips_preview

Snap onto the borders and origins of deselected strips that are visible (default False)

Type :

bool

use_snap_current_frame_to_strips

Snap the current frame onto a strip's start or end (default False)

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

| ToolSettings.sequencer_tool_settings | |

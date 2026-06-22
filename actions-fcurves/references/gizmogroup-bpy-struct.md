# Gizmogroup Bpy Struct, Gizmogroupproperties Bpy Struct, Gizmoproperties Bpy Struct, Gizmos Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GizmoGroup(bpy_struct); GizmoGroupProperties(bpy_struct); GizmoProperties(bpy_struct); Gizmos(bpy_prop_collection); GlowStrip(EffectStrip); GPencilInterpolateSettings(bpy_struct); GPencilSculptGuide(bpy_struct); GpSculptPaint(Paint); GpVertexPaint(Paint); GpWeightPaint(Paint).

## GizmoGroup(bpy_struct)

### GizmoGroup(bpy_struct)

base class — bpy_struct

class bpy.types. GizmoGroup ( bpy_struct )

Holds an operator that is mid-execution, or one registered once it has finished running.

bl_idname

(default “”, never None)

Type :

str

bl_label

(default “”, never None)

Type :

str

bl_options

Options for this operator type (default set())

- 3D
3D – Use in 3D viewport.

- SCALE
Scale – Scale to respect zoom (otherwise zoom independent display size).

- `DEPTH_3D`
Depth 3D – Supports culled depth by other objects in the view.

- SELECT
Select – Supports selection.

- PERSISTENT
Persistent.

- `SHOW_MODAL_ALL`
Show Modal All – Keep everything visible during interaction, including this group when a different one is being interacted with.

- `EXCLUDE_MODAL`
Exclude Modal – Keep everything except this group visible during interaction.

- `TOOL_INIT`
Tool Init – Hold off running until the tool operator runs (when paired with a tool).

- `TOOL_FALLBACK_KEYMAP`
Use fallback tools keymap – Attach the fallback tools keymap to this gizmo type.

- `VR_REDRAWS`
VR Redraws – These gizmos target virtual-reality sessions and need their redraws handled specially.

Type :

set[Literal[‘3D’, ‘SCALE’, ‘`DEPTH_3D`’, ‘SELECT’, ‘PERSISTENT’, ‘`SHOW_MODAL_ALL`’, ‘`EXCLUDE_MODAL`’, ‘`TOOL_INIT`’, ‘`TOOL_FALLBACK_KEYMAP`’, ‘`VR_REDRAWS`’]]

bl_owner_id

(default “”, never None)

Type :

str

bl_region_type

The region where the panel is going to be used in (default 'WINDOW' )

Type :

Literal[Region Type Items]

bl_space_type

The space where the panel is going to be used in (default 'EMPTY' )

Type :

Literal[Space Type Items]

gizmos

List of gizmos in the Gizmo Map (default None, readonly)

Type :

Gizmos[Gizmo]

name

(default “”, readonly, never None)

Type :

str

classmethod poll ( context )

Checks whether this gizmo group is allowed to run.

Parameters :

context (Context) – (never None)

Return type :

bool

classmethod setup_keymap ( keyconfig )

Sets up the keymaps for this gizmo group, falling back to the default keymap when none is supplied.

Parameters :

keyconfig (KeyConfig) – (never None)

Returns :

(never None)

Return type :

KeyMap

setup ( context )

The function that creates the group’s gizmos.

Parameters :

context (Context) – (never None)

refresh ( context )

Rebuilds the data; invoked when shared state such as the selection changes.

Parameters :

context (Context) – (never None)

draw_prepare ( context )

Runs ahead of every redraw.

Parameters :

context (Context) – (never None)

invoke_prepare ( context , gizmo )

Runs just before invoke.

Parameters :

- context (Context) – (never None)

- gizmo (Gizmo) – (never None)

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

| Context.gizmo_group | Gizmo.group |

## GizmoGroupProperties(bpy_struct)

### GizmoGroupProperties(bpy_struct)

base class — bpy_struct

class bpy.types. GizmoGroupProperties ( bpy_struct )

Input properties of a Gizmo Group

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

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

| WorkSpaceTool.gizmo_group_properties | |

## GizmoProperties(bpy_struct)

### GizmoProperties(bpy_struct)

base class — bpy_struct

class bpy.types. GizmoProperties ( bpy_struct )

Input properties of a Gizmo

bl_system_properties_get ( * , do_create = False )

DEBUG ONLY. Internal access to runtime-defined RNA data storage, intended solely for testing and debugging purposes. Do not access it in regular scripting work, and in particular, do not assume that it contains writable data

Parameters :

do_create ( bool ) – Ensure that system properties are created if they do not exist yet (optional)

Returns :

The system properties root container, or None if there are no system properties stored in this data yet, and its creation was not requested

Return type :

PropertyGroup

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

| Gizmo.properties | |

## Gizmos(bpy_prop_collection)

### Gizmos(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. Gizmos ( bpy_prop_collection )

Collection of gizmos

new ( type )

Add gizmo

Parameters :

type ( str ) – Gizmo identifier (never None)

Returns :

New gizmo

Return type :

Gizmo

remove ( gizmo )

Delete gizmo

Parameters :

gizmo (Gizmo) – New gizmo (never None)

clear ( )

Delete all gizmos

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

| GizmoGroup.gizmos | |

## GlowStrip(EffectStrip)

### GlowStrip(EffectStrip)

base classes — bpy_struct, Strip, EffectStrip

class bpy.types. GlowStrip ( EffectStrip )

A sequencer strip that produces a glow effect.

blur_radius

How far the glow spreads (in [0.5, 20], default 0.0)

Type :

float

boost_factor

Factor that scales brightness (in [0, 10], default 0.0)

Type :

float

clamp

Ceiling placed on the intensity (in [0, 1], default 0.0)

Type :

float

input_1

The effect strip’s first input (never None)

Type :

Strip

input_count

(in [0, inf], default 0, readonly)

Type :

int

quality

How precise the blur is (in [1, 5], default 0)

Type :

int

threshold

Lowest intensity that sets off a glow (in [0, 1], default 0.0)

Type :

float

use_only_boost

Display nothing but the glow buffer (default False)

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

| bpy_struct.id_data Strip.name Strip.type Strip.select Strip.select_left_handle Strip.select_right_handle Strip.mute Strip.lock Strip.frame_final_duration Strip.duration Strip.frame_duration Strip.content_duration Strip.frame_start Strip.content_start Strip.content_end Strip.frame_final_start Strip.left_handle Strip.frame_final_end Strip.right_handle Strip.frame_offset_start Strip.left_handle_offset Strip.frame_offset_end Strip.right_handle_offset | Strip.channel Strip.use_linear_modifiers Strip.blend_type Strip.blend_alpha Strip.effect_fader Strip.use_default_fade Strip.color_tag Strip.modifiers Strip.show_retiming_keys EffectStrip.use_deinterlace EffectStrip.alpha_mode EffectStrip.use_flip_x EffectStrip.use_flip_y EffectStrip.use_float EffectStrip.use_reverse_frames EffectStrip.color_multiply EffectStrip.multiply_alpha EffectStrip.color_saturation EffectStrip.strobe EffectStrip.transform EffectStrip.crop EffectStrip.use_proxy EffectStrip.proxy |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve | bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Strip.bl_system_properties_get Strip.strip_elem_from_frame Strip.swap Strip.move_to_meta Strip.parent_meta Strip.invalidate_cache Strip.split Strip.bl_rna_get_subclass Strip.bl_rna_get_subclass_py EffectStrip.bl_rna_get_subclass EffectStrip.bl_rna_get_subclass_py |

## GPencilInterpolateSettings(bpy_struct)

### GPencilInterpolateSettings(bpy_struct)

base class — bpy_struct

class bpy.types. GPencilInterpolateSettings ( bpy_struct )

Configuration for the Grease Pencil interpolation tools.

interpolation_curve

A custom curve that governs ‘sequence’ interpolation from one Grease Pencil frame to the next (readonly)

Type :

CurveMapping

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

| ToolSettings.gpencil_interpolate | |

## GPencilSculptGuide(bpy_struct)

### GPencilSculptGuide(bpy_struct)

base class — bpy_struct

class bpy.types. GPencilSculptGuide ( bpy_struct )

Drawing guides.

angle

The heading the guide lines follow (in [-6.28319, 6.28319], default 0.0)

Type :

float

angle_snap

Snapping applied to the angle (in [-6.28319, 6.28319], default 0.0)

Type :

float

location

A user-set reference point the guides use (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

bpy_prop_array[float]

reference_object

The object that supplies the reference point

Type :

Object

reference_point

Which speed-guide reference is in use (default 'CURSOR' )

- CURSOR
Cursor – Take the cursor as the reference point.

- CUSTOM
Custom – Take a custom reference point.

- OBJECT
Object – Take an object as the reference point.

Type :

Literal[‘CURSOR’, ‘CUSTOM’, ‘OBJECT’]

spacing

Gap left between guides (in [0, inf], default 20.0)

Type :

float

type

Which kind of speed guide to use (default 'CIRCULAR' )

- CIRCULAR
Circular – Build rings from one point.

- RADIAL
Radial – Use one point to set the direction.

- PARALLEL
Parallel – Parallel lines.

- GRID
Grid – Lay out horizontal and vertical lines.

- ISO
Isometric – Lay out isometric and vertical lines.

Type :

Literal[‘CIRCULAR’, ‘RADIAL’, ‘PARALLEL’, ‘GRID’, ‘ISO’]

use_guide

Enable speed guides (default False)

Type :

bool

use_snapping

Snap to the guide’s angle or spacing settings (default False)

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

| GPencilSculptSettings.guide | |

## GpSculptPaint(Paint)

### GpSculptPaint(Paint)

base classes — bpy_struct, Paint

class bpy.types. GpSculptPaint ( Paint )

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

| ToolSettings.gpencil_sculpt_paint | |

## GpVertexPaint(Paint)

### GpVertexPaint(Paint)

base classes — bpy_struct, Paint

class bpy.types. GpVertexPaint ( Paint )

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

| ToolSettings.gpencil_vertex_paint | |

## GpWeightPaint(Paint)

### GpWeightPaint(Paint)

base classes — bpy_struct, Paint

class bpy.types. GpWeightPaint ( Paint )

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

| ToolSettings.gpencil_weight_paint | |

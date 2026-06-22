# Volumegrids Bpy Prop Collection, Walknavigation Bpy Struct, Whitebalancemodifier Stripmodifier, Window Bpy Struct

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: VolumeGrids(bpy_prop_collection); WalkNavigation(bpy_struct); WhiteBalanceModifier(StripModifier); Window(bpy_struct).

## VolumeGrids(bpy_prop_collection)

### VolumeGrids(bpy_prop_collection)

base classes — bpy_prop, bpy_prop_collection

class bpy.types. VolumeGrids ( bpy_prop_collection )

A set of 3D volume grids.

active_index

Index of active volume grid (in [0, inf], default 0)

Type :

int

error_message

When grid loading fails, the detailed error text (default "", readonly, never None)

Type :

str

frame

Frame the volume grids are loaded at, derived from scene time and the volume parameters (in [-inf, inf], default 0, readonly)

Type :

int

frame_filepath

Volume file used to load the current frame. Blank when nothing has loaded yet or the frame lives only in memory. (default "", readonly, never None, blend relative // prefix supported)

Type :

str

is_loaded

Whether the grid list and metadata are held in memory (default False, readonly)

Type :

bool

load ( )

Read the grid list and metadata in from file

Returns :

True if grid list was successfully loaded

Return type :

bool

unload ( )

Drop every grid and its voxel data from memory

save ( filepath )

Write the grids and metadata out to file

Parameters :

filepath ( str ) – File path to save to (never None)

Returns :

True if grid list was successfully loaded

Return type :

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

| Volume.grids | |

## WalkNavigation(bpy_struct)

### WalkNavigation(bpy_struct)

base class — bpy_struct

class bpy.types. WalkNavigation ( bpy_struct )

Settings for walk navigation.

jump_height

How high a jump can reach (in [0.1, 100], default 0.4)

Type :

float

mouse_speed

How responsive looking around feels; larger numbers make the mouse turn faster (in [0.01, 10], default 1.0)

Type :

float

teleport_time

Length of the time warp applied when teleporting during navigation (in [0, 10], default 0.2)

Type :

float

use_gravity

Walk under gravity, or move around freely (default False)

Type :

bool

use_mouse_reverse

Flip the mouse's vertical axis (default False)

Type :

bool

view_height

Eye height above the floor while walking (in [0, 1000], default 1.6)

Type :

float

walk_speed

Baseline speed used for both walking and flying (in [0.01, 100], default 2.5)

Type :

float

walk_speed_factor

Multiplier applied when the fast or slow modifier keys are held (in [0.01, 10], default 5.0)

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

| PreferencesInput.walk_navigation | |

## WhiteBalanceModifier(StripModifier)

### WhiteBalanceModifier(StripModifier)

base classes — bpy_struct, StripModifier

class bpy.types. WhiteBalanceModifier ( StripModifier )

White balance modifier applied to a sequence strip.

open_mask_input_panel

(default False)

Type :

bool

white_value

The color that marks what should read as white in the strip (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

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

## Window(bpy_struct)

### Window(bpy_struct)

base class — bpy_struct

class bpy.types. Window ( bpy_struct )

An open window.

height

Window height (in [0, 32767], default 0, readonly)

Type :

int

modal_operators

The modal operators that are running right now (default None, readonly)

Type :

bpy_prop_collection[Operator]

parent

This window's active workspace and scene track this one (readonly)

Type :

Window

scene

Scene currently being edited in this window (never None)

Type :

Scene

screen

Workspace screen currently shown in this window (never None)

Type :

Screen

stereo_3d_display

Settings for stereo 3D display (readonly, never None)

Type :

Stereo3dDisplay

support_hdr_color

True when the window provides an HDR graphics buffer that accepts wide-gamut, high-dynamic-range colors in extended sRGB space. (default False, readonly)

Type :

bool

view_layer

View layer of the active workspace shown in this window (never None)

Type :

ViewLayer

width

Window width (in [0, 32767], default 0, readonly)

Type :

int

workspace

Workspace currently shown in this window (never None)

Type :

WorkSpace

x

The window's horizontal position (in [-32768, 32767], default 0, readonly)

Type :

int

y

The window's vertical position (in [-32768, 32767], default 0, readonly)

Type :

int

cursor_warp ( x , y )

Move the cursor to the given position

Parameters :

- x ( int ) – (in [-inf, inf])

- y ( int ) – (in [-inf, inf])

cursor_set ( cursor )

Set the cursor

Parameters :

cursor (Literal[Window Cursor Items]) – cursor

cursor_modal_set ( cursor )

Change the cursor while keeping the old one available to restore

Parameters :

cursor (Literal[Window Cursor Items]) – cursor

cursor_modal_restore ( )

Bring back the cursor that was in use before cursor_modal_set

event_simulate ( type , value , * , unicode = '' , x = 0 , y = 0 , shift = False , ctrl = False , alt = False , oskey = False , hyper = False )

event_simulate

Parameters :

- type (Literal[Event Type Items]) – Type

- value (Literal[Event Value Items]) – Value

- unicode ( str ) – (optional)

- x ( int ) – (in [-inf, inf], optional)

- y ( int ) – (in [-inf, inf], optional)

- shift ( bool ) – Shift, (optional)

- ctrl ( bool ) – Ctrl, (optional)

- alt ( bool ) – Alt, (optional)

- oskey ( bool ) – OS Key, (optional)

- hyper ( bool ) – Hyper, (optional)

Returns :

Item, Added key map item

Return type :

Event

find_playing_scene ( * , scrub = False )

find_playing_scene

Parameters :

scrub ( bool ) – Scrubbing, Check if time in the scene is being scrubbed (optional)

Returns :

Scene, Scene that is currently playing

Return type :

Scene

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

| Context.window Window.parent WindowManager.event_timer_add | WindowManager.windows Windows.find_playing |

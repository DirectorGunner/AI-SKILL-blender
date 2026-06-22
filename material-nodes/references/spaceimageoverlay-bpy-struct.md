# Spaceimageoverlay Bpy Struct, Spaceinfo Space, Spacenla Space, Spacenodeeditor Space ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpaceImageOverlay(bpy_struct); SpaceInfo(Space); SpaceNLA(Space); SpaceNodeEditor(Space); SpaceNodeOverlay(bpy_struct); SpacePreferences(Space).

## SpaceImageOverlay(bpy_struct)

### SpaceImageOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SpaceImageOverlay ( bpy_struct )

Configuration for the overlays drawn in the UV/Image editor

passepartout_alpha

How opaque the darkened overlay is outside the render region (in [0, 1], default 0.5)

Type :

float

show_grid_background

Draw the grid background together with its borders (default False)

Type :

bool

show_overlays

Draw overlays such as UV Maps and Metadata (default False)

Type :

bool

show_render_size

Draw the area that the final render covers (default False)

Type :

bool

show_text_info

Draw the overlay text (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceImageEditor.overlay | |

## SpaceInfo(Space)

### SpaceInfo(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceInfo ( Space )

The space data for the Info editor

show_report_debug

Draw the debug reporting info (default False)

Type :

bool

show_report_error

Draw the error text (default False)

Type :

bool

show_report_info

Draw general information (default False)

Type :

bool

show_report_operator

Draw the operator log (default False)

Type :

bool

show_report_warning

Draw warnings (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceNLA(Space)

### SpaceNLA(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceNLA ( Space )

The space data for the NLA editor

dopesheet

Options that filter the animation data (readonly)

Type :

DopeSheet

show_local_markers

Draw action-local markers on the strips, handy for lining up timing between strips (default True)

Type :

bool

show_markers

If any are defined, give markers a dedicated strip along the editor's lower edge (default False)

Type :

bool

show_region_channels

(default False)

Type :

bool

show_region_footer

(default False)

Type :

bool

show_region_hud

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

show_seconds

Label timing with timecode rather than frame numbers (default False)

Type :

bool

show_strip_curves

Draw the influence F-Curves on the strips (default True)

Type :

bool

use_realtime_update

While strips are being transformed, push the animation-data changes through to other views (default True)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceNodeEditor(Space)

### SpaceNodeEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceNodeEditor ( Space )

The space data for the node editor

backdrop_channels

Which channels of the image get drawn (default 'COLOR' )

- `COLOR_ALPHA`
Color & Alpha – Display image with RGB colors and alpha transparency.

- COLOR
Color – Display image with RGB colors.

- ALPHA
Alpha – Display alpha transparency channel.

- RED
Red.

- GREEN
Green.

- BLUE
Blue.

Type :

Literal[‘`COLOR_ALPHA`’, ‘COLOR’, ‘ALPHA’, ‘RED’, ‘GREEN’, ‘BLUE’]

backdrop_offset

Backdrop offset (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

backdrop_zoom

Backdrop zoom factor (in [0.01, inf], default 1.0)

Type :

float

cursor_location

Where new nodes get placed (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

edit_tree

The node tree currently shown and edited (readonly)

Type :

NodeTree

id

The data-block whose nodes are under edit (readonly)

Type :

ID

id_from

The data-block that the edited data-block is linked from (readonly)

Type :

ID

insert_offset_direction

Which way nodes shift when one is inserted (default 'RIGHT' )

Type :

Literal[‘RIGHT’, ‘LEFT’]

node_tree

The base node tree taken from context

Type :

NodeTree

node_tree_sub_type

Type :

str

overlay

Configuration for the overlays drawn in the Node Editor (readonly, never None)

Type :

SpaceNodeOverlay

path

The route from the data-block to the node tree being edited (default None, readonly)

Type :

SpaceNodeEditorPath[NodeTreePath]

pin

Work with the pinned node tree (default False)

Type :

bool

selected_node_group

The node group to edit

Type :

NodeTree

shader_type

Which data the shader is taken from (default 'OBJECT' )

- OBJECT
Object – Edit shader nodes from Object.

- WORLD
World – Edit shader nodes from World.

- LINESTYLE
Line Style – Edit shader nodes from Line Style.

Type :

Literal[‘OBJECT’, ‘WORLD’, ‘LINESTYLE’]

show_annotation

Draw annotations in this view (default False)

Type :

bool

show_backdrop

Use the active Viewer Node output as a backdrop behind the compositing nodes (default False)

Type :

bool

show_gizmo

Draw gizmos of every type (default True)

Type :

bool

show_gizmo_active_node

Context-sensitive gizmo for whichever node is active (default True)

Type :

bool

show_region_asset_shelf

Draw a region holding assets that might be relevant right now (brushes in paint modes, poses in Pose Mode, and the like) (default False)

Type :

bool

show_region_toolbar

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

supports_previews

Whether this node editor's type can display node previews (default False, readonly)

Type :

bool

texture_type

Which data the texture is taken from (default 'WORLD' )

- WORLD
World – Edit texture nodes from World.

- BRUSH
Brush – Edit texture nodes from Brush.

- LINESTYLE
Line Style – Edit texture nodes from Line Style.

Type :

Literal[‘WORLD’, ‘BRUSH’, ‘LINESTYLE’]

tree_type

Which node tree type is shown and edited (default 'DEFAULT' )

- GeometryNodeTree
Geometry Node Editor – Advanced geometry editing and tools creation using nodes.

- CompositorNodeTree
Compositor – Create effects and post-process renders, images, and the 3D Viewport.

- ShaderNodeTree
Shader Editor – Edit materials, lights, and world shading using nodes.

- TextureNodeTree
Texture Node Editor – Edit textures using nodes.

Type :

Literal[‘GeometryNodeTree’, ‘CompositorNodeTree’, ‘ShaderNodeTree’, ‘TextureNodeTree’]

cursor_location_from_region ( x , y )

Place the cursor using coordinates within the region

Parameters :

- x ( int ) – x, Region x coordinate (in [-inf, inf])

- y ( int ) – y, Region y coordinate (in [-inf, inf])

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceNodeOverlay(bpy_struct)

### SpaceNodeOverlay(bpy_struct)

base class — bpy_struct

class bpy.types. SpaceNodeOverlay ( bpy_struct )

Configuration for the overlays drawn in the Node Editor

preview_shape

Which shape the node previews take (default 'FLAT' )

- FLAT
Flat – Use the default flat previews.

- 3D
3D – Use the material preview scene for the node previews.

Type :

Literal[‘FLAT’, ‘3D’]

show_context_path

Draw breadcrumbs showing the editor's context (default True)

Type :

bool

show_named_attributes

Indicate when nodes make use of named attributes (default True)

Type :

bool

show_overlays

Draw overlays such as colored or dashed wires (default True)

Type :

bool

show_previews

Draw a node's preview when that node is toggled on (default False)

Type :

bool

show_reroute_auto_labels

Label reroute nodes from the label of the reroute nodes they connect to (default False)

Type :

bool

show_timing

Draw how long each node took to run last time (default False)

Type :

bool

show_wire_color

Tint node links according to the sockets they connect (default True)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| SpaceNodeEditor.overlay | |

## SpacePreferences(Space)

### SpacePreferences(Space)

base classes — bpy_struct, Space

class bpy.types. SpacePreferences ( Space )

The space data for the Blender preferences

filter_text

The term used to filter the UI (default “”, never None)

Type :

str

filter_type

Which method drives the filtering (default 'NAME' )

- NAME
Name – Filter based on the operator name.

- KEY
Key-Binding – Filter based on key bindings.

Type :

Literal[‘NAME’, ‘KEY’]

search_filter

The string used for live search filtering (default “”, never None)

Type :

str

show_region_ui

(default False)

Type :

bool

tab_search_results

Whether each visible tab turned up a search result (default False, readonly)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

The matching RNA type, or the default if none is found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier for the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

The matching class, or the default if none is found.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this kind of space.
Whenever the named region of that space type is redrawn, the handler runs.
Note: for the moment, every argument here is positional-only.

Parameters :

- callback ( Callable [ ... , Any ] ) – A function invoked at region draw time.
It is handed the arguments listed below, and any value it hands back gets thrown away.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – The region type the callback draws in; usually WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Usually `POST_PIXEL` for 2D drawing and `POST_VIEW` for 3D drawing. In some cases `PRE_VIEW` can be used. BACKDROP can be used for backdrops in the node editor.

Returns :

A handler reference you can remove afterward.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to take off.

- region_type ( str ) – The region type that handler was attached to.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## See also

- [Bpy Struct](bpy-struct.md)

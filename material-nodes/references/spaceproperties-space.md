# Spaceproperties Space, Spacesequenceeditor Space, Spacespreadsheet Space, Spacetexteditor Space

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: SpaceProperties(Space); SpaceSequenceEditor(Space); SpaceSpreadsheet(Space); SpaceTextEditor(Space).

## SpaceProperties(Space)

### SpaceProperties(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceProperties ( Space )

Data for the Properties editor space

context

(default 'RENDER' )

- TOOL
Tool – Active tool together with workspace settings.

- SCENE
Scene – Properties for the scene.

- RENDER
Render – Properties for rendering.

- OUTPUT
Output – Properties for output.

- `VIEW_LAYER`
View Layer – Properties for the view layer.

- WORLD
World – Properties for the world.

- COLLECTION
Collection – Properties for the collection.

- OBJECT
Object – Properties for the object.

- CONSTRAINT
Constraints – Properties for object constraints.

- MODIFIER
Modifiers – Properties for modifiers.

- DATA
Data – Properties for the object's data.

- BONE
Bone – Properties for the bone.

- `BONE_CONSTRAINT`
Bone Constraints – Properties for bone constraints.

- MATERIAL
Material – Properties for the material.

- TEXTURE
Texture – Properties for the texture.

- PARTICLES
Particles – Properties for particles.

- PHYSICS
Physics – Properties for physics.

- SHADERFX
Effects – Properties for visual effects.

- STRIP
Strip – Properties for the strip.

- `STRIP_MODIFIER`
Strip Modifiers – Properties for strip modifiers.

Type :

Literal[‘TOOL’, ‘SCENE’, ‘RENDER’, ‘OUTPUT’, ‘`VIEW_LAYER`’, ‘WORLD’, ‘COLLECTION’, ‘OBJECT’, ‘CONSTRAINT’, ‘MODIFIER’, ‘DATA’, ‘BONE’, ‘`BONE_CONSTRAINT`’, ‘MATERIAL’, ‘TEXTURE’, ‘PARTICLES’, ‘PHYSICS’, ‘SHADERFX’, ‘STRIP’, ‘`STRIP_MODIFIER`’]

outliner_sync

Switch to the matching tab whenever an outliner data icon gets clicked (default 'AUTO' )

- ALWAYS
Always – Switch tabs on every outliner icon click.

- NEVER
Never – Leave tabs unchanged when an outliner icon is clicked.

- AUTO
Auto – Switch tabs only while this editor borders an outliner.

Type :

Literal[‘ALWAYS’, ‘NEVER’, ‘AUTO’]

pin_id

Type :

ID

search_filter

String applied for live filtering of the search (default “”, never None)

Type :

str

show_properties_bone

(default False)

Type :

bool

show_properties_bone_constraints

(default False)

Type :

bool

show_properties_collection

(default False)

Type :

bool

show_properties_constraints

(default False)

Type :

bool

show_properties_data

(default False)

Type :

bool

show_properties_effects

(default False)

Type :

bool

show_properties_material

(default False)

Type :

bool

show_properties_modifiers

(default False)

Type :

bool

show_properties_object

(default False)

Type :

bool

show_properties_output

(default False)

Type :

bool

show_properties_particles

(default False)

Type :

bool

show_properties_physics

(default False)

Type :

bool

show_properties_render

(default False)

Type :

bool

show_properties_scene

(default False)

Type :

bool

show_properties_strip

(default False)

Type :

bool

show_properties_strip_modifier

(default False)

Type :

bool

show_properties_texture

(default False)

Type :

bool

show_properties_tool

(default False)

Type :

bool

show_properties_view_layer

(default False)

Type :

bool

show_properties_world

(default False)

Type :

bool

tab_search_results

Indicates, per visible tab, whether a search result was found (default False, readonly)

Type :

bool

use_pin_id

Work from the pinned context rather than the active one (default False)

Type :

bool

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this space type. The handler runs each time the named region of the
space type is redrawn. Keep in mind that, for the moment, every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – Function invoked while the region is being drawn.
The supplied arguments are passed to it, and whatever it returns is discarded.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – Which region type the callback renders into; typically WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Generally `POST_PIXEL` for 2D and `POST_VIEW` for 3D; `PRE_VIEW` occasionally applies, and BACKDROP serves node-editor backdrops.

Returns :

A handler you can later remove.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to detach.

- region_type ( str ) – Region type to which the callback had been attached.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceSequenceEditor(Space)

### SpaceSequenceEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceSequenceEditor ( Space )

Data for the sequence editor space

annotation

Annotation data tied to this Preview region

Type :

Annotation

cache_overlay

Configuration controlling how overlays are shown (readonly, never None)

Type :

SequencerCacheOverlay

cursor_location

Where the 2D cursor sits for this view (array of 2 items, in [-inf, inf], default (0.0, 0.0))

Type :

mathutils.Vector

display_channel

Preview only channels at or beneath this value. With 0 the whole set is shown; negative numbers descend that many meta-strip levels when present and reveal every channel there. (in [-5, 128], default 0)

Type :

int

display_mode

Which view mode the sequencer output is shown in (default 'IMAGE' )

Type :

Literal[‘IMAGE’, ‘WAVEFORM’, ‘`RGB_PARADE`’, ‘`VECTOR_SCOPE`’, ‘HISTOGRAM’]

overlay_frame_type

How the overlay frame is drawn (default 'RECTANGLE' )

- RECTANGLE
Rectangle – Draw an overlay across the rectangle area.

- REFERENCE
Reference – Draw the reference frame by itself.

- CURRENT
Current – Draw the current frame by itself.

Type :

Literal[‘RECTANGLE’, ‘REFERENCE’, ‘CURRENT’]

preview_channels

Which preview channels get shown (default 'COLOR' )

- `COLOR_ALPHA`
Color & Alpha – Show the image with RGB color plus alpha transparency.

- COLOR
Color – Show the image with RGB color.

Type :

Literal[‘`COLOR_ALPHA`’, ‘COLOR’]

preview_overlay

Configuration controlling how overlays are shown (readonly, never None)

Type :

SequencerPreviewOverlay

proxy_render_size

Choose between full-resolution preview and the various proxy resolutions (default 'SCENE' )

Type :

Literal[‘NONE’, ‘SCENE’, ‘`PROXY_25`’, ‘`PROXY_50`’, ‘`PROXY_75`’, ‘`PROXY_100`’]

show_frames

Use frames for display instead of seconds (default False)

Type :

bool

show_gizmo

Reveal every kind of gizmo (default True)

Type :

bool

show_gizmo_context

Gizmos that adapt to the active item's context (default True)

Type :

bool

show_gizmo_navigate

Gizmo for moving around the viewport (default True)

Type :

bool

show_gizmo_tool

Gizmo for the active tool (default True)

Type :

bool

show_markers

When present, place markers on their own row along the bottom of the editor (default False)

Type :

bool

show_overexposed

Mark overexposed regions using zebra striping (in [0, 110], default 0)

Type :

int

show_overlays

(default False)

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

show_region_tool_header

(default False)

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

show_seconds

Present timing as a timecode in place of frames (default True)

Type :

bool

show_transform_preview

While dragging a strip handle, preview the resulting start or end frame of that strip (default False)

Type :

bool

timeline_overlay

Configuration controlling how overlays are shown (readonly, never None)

Type :

SequencerTimelineOverlay

use_clamp_view

Cap timeline height at the highest channel slot in use (default False)

Type :

bool

use_marker_sync

Move markers along with strips during transforms (default False)

Type :

bool

use_proxies

When they exist, rely on optimized files so scrubbing runs faster (default False)

Type :

bool

use_zoom_to_fit

Auto-scale the preview image so it fills the region completely (default False)

Type :

bool

view_type

Which Sequencer view to use: sequencer, preview, or both (default 'SEQUENCER' )

Type :

Literal[Space Sequencer View Type Items]

zoom_percentage

Percentage of zoom (in [0.4, 80000], default 100.0)

Type :

float

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this space type. The handler runs each time the named region of the
space type is redrawn. Keep in mind that, for the moment, every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – Function invoked while the region is being drawn.
The supplied arguments are passed to it, and whatever it returns is discarded.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – Which region type the callback renders into; typically WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Generally `POST_PIXEL` for 2D and `POST_VIEW` for 3D; `PRE_VIEW` occasionally applies, and BACKDROP serves node-editor backdrops.

Returns :

A handler you can later remove.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to detach.

- region_type ( str ) – Region type to which the callback had been attached.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceSpreadsheet(Space)

### SpaceSpreadsheet(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceSpreadsheet ( Space )

Data for the spreadsheet space

attribute_domain

The attribute domain that is shown (default 'POINT' )

Type :

Literal[Attribute Domain Items]

geometry_component_type

Which portion of the geometry supplies the displayed data (default 'MESH' )

Type :

Literal[Geometry Component Type Items]

geometry_item_type

Item Type (default 'DOMAIN' )

- DOMAIN
Domain – Data on a domain.

- BUNDLE
Bundle – Data on a bundle.

Type :

Literal[‘DOMAIN’, ‘BUNDLE’]

is_pinned

Whether the context path has been pinned (default False)

Type :

bool

object_eval_state

(default 'EVALUATED' )

- EVALUATED
Evaluated – Pull data from an object that is fully or partially evaluated.

- ORIGINAL
Original – Pull data from the original object, with no modifiers in effect.

- `VIEWER_NODE`
Viewer Node – Pull intermediate data from the viewer node.

Type :

Literal[‘EVALUATED’, ‘ORIGINAL’, ‘`VIEWER_NODE`’]

row_filters

Filters that drop rows from the shown data (default None, readonly)

Type :

bpy_prop_collection[SpreadsheetRowFilter]

show_internal_attributes

Include attributes whose names begin with a period and are intended for internal use (default False)

Type :

bool

show_only_selected

Keep just the rows that map to selected elements (default False)

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

show_region_toolbar

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

tables

State that persists for the tables presented in this spreadsheet editor (default None, readonly)

Type :

SpreadsheetTables[SpreadsheetTable]

use_filter

(default False)

Type :

bool

viewer_path

Path leading to the data shown in the spreadsheet (readonly)

Type :

ViewerPath

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this space type. The handler runs each time the named region of the
space type is redrawn. Keep in mind that, for the moment, every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – Function invoked while the region is being drawn.
The supplied arguments are passed to it, and whatever it returns is discarded.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – Which region type the callback renders into; typically WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Generally `POST_PIXEL` for 2D and `POST_VIEW` for 3D; `PRE_VIEW` occasionally applies, and BACKDROP serves node-editor backdrops.

Returns :

A handler you can later remove.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to detach.

- region_type ( str ) – Region type to which the callback had been attached.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

## SpaceTextEditor(Space)

### SpaceTextEditor(Space)

base classes — bpy_struct, Space

class bpy.types. SpaceTextEditor ( Space )

Data for the text editor space

find_text

The string the find tool will look for (default “”, never None)

Type :

str

font_size

Size of the font used when showing the text (in [1, 256], default 0)

Type :

int

margin_column

At which column number the right margin appears (in [0, 1024], default 0)

Type :

int

replace_text

The string the replace tool swaps in for the selected text (default “”, never None)

Type :

str

show_line_highlight

Emphasize the line the cursor is on (default False)

Type :

bool

show_line_numbers

Display line numbers along the side of the text (default False)

Type :

bool

show_margin

Display the right margin (default False)

Type :

bool

show_region_footer

(default False)

Type :

bool

show_region_ui

(default False)

Type :

bool

show_syntax_highlight

Apply syntax highlighting for scripts (default False)

Type :

bool

show_word_wrap

Wrap text onto the next line when horizontal room runs out (default False)

Type :

bool

tab_width

How many spaces a tab is displayed as (in [2, 8], default 0)

Type :

int

text

The text shown and edited within this space

Type :

Text

top

The topmost visible line (in [0, inf], default 0)

Type :

int

use_find_all

Look through every text data-block instead of only the active one (default False)

Type :

bool

use_find_wrap

On reaching the end, resume searching from the start of the file (default False)

Type :

bool

use_live_edit

Execute Python as you edit (default False)

Type :

bool

use_match_case

Make the search string case sensitive (default False)

Type :

bool

use_overwrite

Type over existing characters rather than inserting new ones (default False)

Type :

bool

visible_lines

Number of lines that fit in the current editor (in [-inf, inf], default 0, readonly)

Type :

int

is_syntax_highlight_supported ( )

Reports True when the editor can syntax-highlight the active text data-block

Return type :

bool

region_location_from_cursor ( line , column )

Work out the region position for a given line together with its column offset

Parameters :

- line ( int ) – Line, Line index (in [-inf, inf])

- column ( int ) – Column, Column index (in [-inf, inf])

Returns :

Region coordinates (array of 2 items, in [-1, inf])

Return type :

bpy_prop_array[int]

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default (bpy.types.Struct | None) – Value returned if nothing matches.

Returns :

Either the matching RNA type, or the default when there is no match.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – Identifier of the RNA type.

- default ( type | None ) – Value returned if nothing matches.

Returns :

Either the matching class, or the default when there is no match.

Return type :

type

classmethod draw_handler_add ( callback , args , region_type , draw_type )

Register a fresh draw handler on this space type. The handler runs each time the named region of the
space type is redrawn. Keep in mind that, for the moment, every argument is positional only.

Parameters :

- callback ( Callable [ ... , Any ] ) – Function invoked while the region is being drawn.
The supplied arguments are passed to it, and whatever it returns is discarded.

- args ( tuple [ Any , ... ] ) – Arguments handed to the callback.

- region_type ( str ) – Which region type the callback renders into; typically WINDOW . (bpy.types.Region.type)

- draw_type ( str ) – Generally `POST_PIXEL` for 2D and `POST_VIEW` for 3D; `PRE_VIEW` occasionally applies, and BACKDROP serves node-editor backdrops.

Returns :

A handler you can later remove.

Return type :

object

classmethod draw_handler_remove ( handler , region_type )

Detach a draw handler that had been registered earlier.

Parameters :

- handler ( object ) – The draw handler to detach.

- region_type ( str ) – Region type to which the callback had been attached.

### Inherited Properties

| bpy_struct.id_data Space.type | Space.show_locked_time Space.show_region_header |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert | bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Space.bl_rna_get_subclass Space.bl_rna_get_subclass_py Space.draw_handler_add Space.draw_handler_remove |

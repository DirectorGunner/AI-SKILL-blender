# Uilayout Bpy Struct (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- value ( str ) – Value, String to put in context (never None)

template_header ( )

Lays out the standard editor-type header controls shared across spaces.

template_ID ( data , property , * , new = '' , open = '' , unlink = '' , filter = 'ALL' , live_icon = False , text = '' , text_ctxt = '' , translate = True )

template_ID

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- new ( str ) – Operator identifier to create a new ID block (optional, never None)

- open ( str ) – Operator identifier to open a file for creating a new ID block (optional, never None)

- unlink ( str ) – Operator identifier to unlink the ID block (optional, never None)

- filter ( Literal [ 'ALL' , 'AVAILABLE' ] ) – Optionally limit the items which can be selected (optional)

- live_icon ( bool ) – Show preview instead of fixed icon (optional)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_ID_session_uid ( data , property , id_type )

ID search-menu button driven by a session_uid integer property.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_ID_preview ( data , property , * , new = '' , open = '' , unlink = '' , rows = 0 , cols = 0 , filter = 'ALL' , hide_buttons = False )

template_ID_preview

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- new ( str ) – Operator identifier to create a new ID block (optional, never None)

- open ( str ) – Operator identifier to open a file for creating a new ID block (optional, never None)

- unlink ( str ) – Operator identifier to unlink the ID block (optional, never None)

- rows ( int ) – Number of thumbnail preview rows to display, (in [0, inf], optional)

- cols ( int ) – Number of thumbnail preview columns to display, (in [0, inf], optional)

- filter ( Literal [ 'ALL' , 'AVAILABLE' ] ) – Optionally limit the items which can be selected (optional)

- hide_buttons ( bool ) – Show only list, no buttons (optional)

template_matrix ( data , property )

Adds a read-only matrix display showing the translation, rotation and scale components. Point the property argument at an existing 4x4 float vector property whose subtype is ‘MATRIX’.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_any_ID ( data , property , type_property , * , text = '' , text_ctxt = '' , translate = True )

template_any_ID

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- type_property ( str ) – Identifier of property in data giving the type of the ID-blocks to use (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_ID_tabs ( data , property , * , new = '' , menu = '' , filter = 'ALL' )

template_ID_tabs

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- new ( str ) – Operator identifier to create a new ID block (optional, never None)

- menu ( str ) – Context menu identifier (optional, never None)

- filter ( Literal [ 'ALL' , 'AVAILABLE' ] ) – Optionally limit the items which can be selected (optional)

template_action ( id , * , new = '' , unlink = '' , text = '' , text_ctxt = '' , translate = True )

template_action

Parameters :

- id (ID) – The data-block for which to select an Action (never None)

- new ( str ) – Operator identifier to create a new ID block (optional, never None)

- unlink ( str ) – Operator identifier to unlink the ID block (optional, never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_search ( data , property , search_data , search_property , * , new = '' , unlink = '' , text = '' , text_ctxt = '' , translate = True )

template_search

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- search_data (AnyType) – Data from which to take collection to search in (never None)

- search_property ( str ) – Identifier of search collection property (never None)

- new ( str ) – Operator identifier to create a new item for the collection (optional, never None)

- unlink ( str ) – Operator identifier to unlink or delete the active item from the collection (optional, never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_search_preview ( data , property , search_data , search_property , * , new = '' , unlink = '' , text = '' , text_ctxt = '' , translate = True , rows = 0 , cols = 0 )

template_search_preview

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- search_data (AnyType) – Data from which to take collection to search in (never None)

- search_property ( str ) – Identifier of search collection property (never None)

- new ( str ) – Operator identifier to create a new item for the collection (optional, never None)

- unlink ( str ) – Operator identifier to unlink or delete the active item from the collection (optional, never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- rows ( int ) – Number of thumbnail preview rows to display, (in [0, inf], optional)

- cols ( int ) – Number of thumbnail preview columns to display, (in [0, inf], optional)

template_path_builder ( data , property , root , * , text = '' , text_ctxt = '' , translate = True )

template_path_builder

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- root (ID) – ID-block from which path is evaluated from

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_modifiers ( )

Builds the interface for the modifier stack.

template_strip_modifiers ( )

Builds the interface for the strip modifier stack.

template_collection_exporters ( )

Builds the interface for the collection exporters.

template_constraints ( * , use_bone_constraints = True )

Builds the panels that make up the constraint stack.

Parameters :

use_bone_constraints ( bool ) – Add panels for bone constraints instead of object constraints (optional)

template_shaderfx ( )

Builds the panels that make up the shader effect stack.

template_greasepencil_color ( data , property , * , rows = 0 , cols = 0 , scale = 1.0 , filter = 'ALL' )

template_greasepencil_color

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- rows ( int ) – Number of thumbnail preview rows to display, (in [0, inf], optional)

- cols ( int ) – Number of thumbnail preview columns to display, (in [0, inf], optional)

- scale ( float ) – Scale of the image thumbnails, (in [0.1, 1.5], optional)

- filter ( Literal [ 'ALL' , 'AVAILABLE' ] ) – Optionally limit the items which can be selected (optional)

template_constraint_header ( data )

Builds the header row shown above a constraint panel.

Parameters :

data (Constraint) – Constraint data (never None)

template_preview ( id , * , show_buttons = True , parent = None , slot = None , preview_id = '' )

Item. A preview pane for previewing materials, textures, lights or worlds.

Parameters :

- id (ID) – ID data-block

- show_buttons ( bool ) – Show preview buttons? (optional)

- parent (ID) – ID data-block (optional)

- slot (TextureSlot) – Texture slot (optional)

- preview_id ( str ) – Identifier of this preview widget, if not set the ID type will be used (i.e. all previews of materials without explicit ID will have the same size…). (optional, never None)

template_curve_mapping ( data , property , * , type = 'NONE' , levels = False , brush = False , use_negative_slope = False , show_tone = False , show_presets = False )

Item. A curve-mapping control, useful for things like light falloff curves.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- type ( Literal [ 'NONE' , 'VECTOR' , 'COLOR' , 'HUE' ] ) – Type, Type of curves to display (optional)

- levels ( bool ) – Show black/white levels (optional)

- brush ( bool ) – Show brush options (optional)

- use_negative_slope ( bool ) – Use a negative slope by default (optional)

- show_tone ( bool ) – Show tone options (optional)

- show_presets ( bool ) – Show preset options (optional)

template_curveprofile ( data , property )

An editor for authoring custom profile paths.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_color_ramp ( data , property , * , expand = False )

Item. A color ramp widget.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- expand ( bool ) – Expand button to show more detail (optional)

template_icon ( icon_value , * , scale = 1.0 )

Draws a large icon.

Parameters :

- icon_value ( int ) – Icon to display, (in [0, inf])

- scale ( float ) – Scale, Scale the icon size (by the button size) (in [1, 100], optional)

template_icon_view ( data , property , * , show_labels = False , scale = 6.0 , scale_popup = 5.0 )

Enum. A large widget that displays icon previews.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- show_labels ( bool ) – Show enum label in preview buttons (optional)

- scale ( float ) – UI Units, Scale the button icon size (by the button size) (in [1, 100], optional)

- scale_popup ( float ) – Scale, Scale the popup icon size (by the button size) (in [1, 100], optional)

template_histogram ( data , property )

Item. A histogram widget for inspecting image data.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_waveform ( data , property )

Item. A waveform widget for inspecting image data.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_vectorscope ( data , property )

Item. A vectorscope widget for inspecting image data.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_layers ( data , property , used_layers_data , used_layers_property , active_layer )

template_layers

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- used_layers_data (AnyType) – Data from which to take property

- used_layers_property ( str ) – Identifier of property in data (never None)

- active_layer ( int ) – Active Layer, (in [0, inf])

template_color_picker ( data , property , * , value_slider = False , lock = False , lock_luminosity = False , cubic = False )

Item. A color-wheel control for choosing colors.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- value_slider ( bool ) – Display the value slider to the right of the color wheel (optional)

- lock ( bool ) – Lock the color wheel display to value 1.0 regardless of actual color (optional)

- lock_luminosity ( bool ) – Keep the color at its original vector length (optional)

- cubic ( bool ) – Cubic saturation for picking values close to white (optional)

template_palette ( data , property , * , color = False )

Item. A palette control for choosing colors.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- color ( bool ) – Display the colors as colors or values (optional)

template_image_layers ( image , image_user )

template_image_layers

template_image ( data , property , image_user , * , compact = False , multiview = False )

Item(s). Controls for choosing images and pointing them at their source files.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- image_user (ImageUser) – (never None)

- compact ( bool ) – Use more compact layout (optional)

- multiview ( bool ) – Expose Multi-View options (optional)

template_image_settings ( image_settings , * , color_management = False )

Controls for configuring the output image format.

Parameters :

- image_settings (ImageFormatSettings) – (never None)

- color_management ( bool ) – Show color management settings (optional)

template_image_stereo_3d ( stereo_3d_format )

Controls for configuring the stereo-3d image options.

Parameters :

stereo_3d_format (Stereo3dFormat) – (never None)

template_image_views ( image_settings )

Controls for configuring the image views output options.

Parameters :

image_settings (ImageFormatSettings) – (never None)

template_movieclip ( data , property , * , compact = False )

Item(s). Controls for choosing movie clips and pointing them at their source files.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- compact ( bool ) – Use more compact layout (optional)

template_track ( data , property )

Item. A movie-track control that previews the tracking image.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_marker ( data , property , clip_user , track , * , compact = False )

Item. A control for adjusting the settings of one marker.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- clip_user (MovieClipUser) – (never None)

- track (MovieTrackingTrack) – (never None)

- compact ( bool ) – Use more compact layout (optional)

template_movieclip_information ( data , property , clip_user )

Item. Movie clip information data.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- clip_user (MovieClipUser) – (never None)

template_list ( listtype_name , list_id , dataptr , propname , active_dataptr , active_propname , * , item_dyntip_propname = '' , rows = 5 , maxrows = 5 , type = 'DEFAULT' , columns = 9 , sort_reverse = False , sort_lock = False )

Item. A list control for showing collections of data such as vertex groups.

Parameters :

- listtype_name ( str ) – Identifier of the list type to use (never None)

- list_id ( str ) – Identifier of this list widget. Necessary to tell apart different list widgets. Mandatory when using default “`UI_UL`_list” class. If this not an empty string, the uilist gets a custom ID, otherwise it takes the name of the class used to define the uilist (for example, if the class name is “`OBJECT_UL`_vgroups”, and list_id is not set by the script, then bl_idname = “`OBJECT_UL`_vgroups”) (never None)

- dataptr (AnyType) – Data from which to take the Collection property

- propname ( str ) – Identifier of the Collection property in data (never None)

- active_dataptr (AnyType) – Data from which to take the integer property, index of the active item (never None)

- active_propname ( str ) – Identifier of the integer property in active_data, index of the active item (never None)

- item_dyntip_propname ( str ) – Identifier of a string property in items, to use as tooltip content (optional, never None)

- rows ( int ) – Default and minimum number of rows to display (in [0, inf], optional)

- maxrows ( int ) – Default maximum number of rows to display (in [0, inf], optional)

- type (Literal[Uilist Layout Type Items]) – Type, Type of layout to use (optional)

- columns ( int ) – Number of items to display per row, for GRID layout (in [0, inf], optional)

- sort_reverse ( bool ) – Display items in reverse order by default (optional)

- sort_lock ( bool ) – Lock display order to default value (optional)

template_running_jobs ( )

template_running_jobs

template_operator_search ( )

template_operator_search

template_menu_search ( )

template_menu_search

template_header_3D_mode ( )

template_edit_mode_selection ( )

Lays out the standard 3D-Viewport edit-mode header controls (the selection-mode picker).

template_reports_banner ( )

template_reports_banner

template_input_status ( )

template_input_status

template_status_info ( )

template_status_info

template_node_link ( ntree , node , socket )

template_node_link

template_node_view ( ntree , node , socket )

template_node_view

template_node_operator_registration_errors ( * , idname = '' )

template_node_operator_registration_errors

Parameters :

idname ( str ) – (optional, never None)

template_node_asset_menu_items ( * , catalog_path = '' , operator = 'ADD' )

template_node_asset_menu_items

Parameters :

- catalog_path ( str ) – (optional, never None)

- operator ( Literal [ 'ADD' , 'SWAP' ] ) – Operator, The operator the asset menu will use (optional)

- ADD
Add Node – Add a node to the active tree..

- SWAP
Swap Node – Replace the selected nodes with the specified type..

template_modifier_asset_menu_items ( * , catalog_path = '' , skip_essentials = False )

template_modifier_asset_menu_items

Parameters :

- catalog_path ( str ) – (optional, never None)

- skip_essentials ( bool ) – (optional)

template_node_operator_asset_menu_items ( * , catalog_path = '' )

template_node_operator_asset_menu_items

Parameters :

catalog_path ( str ) – (optional, never None)

template_node_operator_asset_root_items ( )

template_node_operator_asset_root_items

template_texture_user ( )

template_texture_user

template_keymap_item_properties ( item )

template_keymap_item_properties

Parameters :

item (KeyMapItem) – (never None)

template_component_menu ( data , property , * , name = '' )

Item. Shows an expanded property inside a popup menu.

Parameters :

- data (AnyType) – Data from which to take property

- property ( str ) – Identifier of property in data (never None)

- name ( str ) – (optional, never None)

template_colorspace_settings ( data , property )

Item. A control for adjusting the input color space settings.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_colormanaged_view_settings ( data , property )

Item. A control for adjusting the color-managed view settings.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_node_socket ( * , color = (0.0, 0.0, 0.0, 1.0) )

Node Socket Icon

Parameters :

color ( Sequence [ float ] ) – Color, (array of 4 items, in [0, 1], optional)

template_cache_file ( data , property )

Item(s). Controls for choosing cache files and pointing them at their source paths.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_cache_file_velocity ( data , property )

Displays the velocity-related properties of cache files.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_cache_file_time_settings ( data , property )

Displays the time-related settings of cache files.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_cache_file_layers ( data , property )

Displays the override-layer properties of cache files.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_recent_files ( * , rows = 6 )

Lists the .blend files that were saved most recently.

Parameters :

rows ( int ) – Maximum number of items to show (in [1, inf], optional)

Returns :

Number of items drawn (in [0, inf])

Return type :

int

template_file_select_path ( params )

Item. A text field for setting the file browser’s current path.

template_event_from_keymap_item ( item , * , text = '' , text_ctxt = '' , translate = True )

Renders a keymap item as a combination of icons and text.

Parameters :

- item (KeyMapItem) – Item, (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

template_light_linking_collection ( context_layout , data , property )

Shows the contents of a light linking collection.

Parameters :

- context_layout (UILayout) – Layout to set active list element as context properties (never None)

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

template_bone_collection_tree ( )

Shows the bone-collections tree.

template_grease_pencil_layer_tree ( )

Shows the tree of layers for the active Grease Pencil object.

template_node_tree_interface ( interface )

Shows the interface of a node tree.

Parameters :

interface (NodeTreeInterface) – Node Tree Interface, Interface of a node tree to display (never None)

## See also

- [Bpy Struct](bpy-struct.md)

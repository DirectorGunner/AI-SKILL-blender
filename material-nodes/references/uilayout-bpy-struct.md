# Uilayout Bpy Struct (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### UILayout(bpy_struct) 

base class — bpy_struct

class bpy.types. UILayout ( bpy_struct ) 

Layout for the user interface within a panel or header.

activate_init 

When set, buttons inside popups become active as soon as they appear, so a field can be typed into without clicking it first (default False)

Type :

bool

active 

(default False)

Type :

bool

active_default 

When set, an operator button declared after this becomes active on pressing return; use with popup dialogs (default False)

Type :

bool

alert 

(default False)

Type :

bool

alignment 

(default 'EXPAND' )

Type :

Literal[‘EXPAND’, ‘LEFT’, ‘CENTER’, ‘RIGHT’]

direction 

(default 'HORIZONTAL' , readonly)

Type :

Literal[‘HORIZONTAL’, ‘VERTICAL’]

emboss 

(default 'NORMAL' )

- NORMAL
Regular – Draw standard button emboss style.

- NONE
None – Draw only text and icons.

- `PULLDOWN_MENU`
Pull-down Menu – Draw pull-down menu style.

- `PIE_MENU`
Pie Menu – Draw radial menu style.

- `NONE_OR_STATUS`
None or Status – Draw with no emboss unless the button has a coloring status like an animation state.

Type :

Literal[‘NORMAL’, ‘NONE’, ‘`PULLDOWN_MENU`’, ‘`PIE_MENU`’, ‘`NONE_OR_STATUS`’]

enabled 

When unset, this (sub)layout appears grayed out (default False)

Type :

bool

operator_context 

Usually ‘`INVOKE_REGION_WIN`’, though a few bpy.types.Menu cases set it to ‘`EXEC_REGION_WIN`’. (default '`INVOKE_DEFAULT`' )

Type :

Literal[Operator Context Items]

scale_x 

X-direction scale factor for the items in this (sub)layout (in [0, inf], default 0.0)

Type :

float

scale_y 

Y-direction scale factor for the items in this (sub)layout (in [0, inf], default 0.0)

Type :

float

ui_units_x 

Fixed X-direction size for the items in this (sub)layout (in [0, inf], default 0.0)

Type :

float

ui_units_y 

Fixed Y-direction size for the items in this (sub)layout (in [0, inf], default 0.0)

Type :

float

use_property_decorate 

(default False)

Type :

bool

use_property_split 

(default False)

Type :

bool

row ( * , align = False , heading = '' , heading_ctxt = '' , translate = True ) 

Sub-layout. Items placed in this sublayout are placed next to each other in a row.

Parameters :

- align ( bool ) – Align buttons to each other (optional)

- heading ( str ) – Heading, Label to insert into the layout for this sub-layout (optional, never None)

- heading_ctxt ( str ) – Override automatic translation context of the given heading (optional, never None)

- translate ( bool ) – Translate the given heading, when UI translation is enabled (optional)

Returns :

Sub-layout to put items in

Return type :

UILayout

column ( * , align = False , heading = '' , heading_ctxt = '' , translate = True ) 

Sub-layout. Items placed in this sublayout are placed under each other in a column.

Parameters :

- align ( bool ) – Align buttons to each other (optional)

- heading ( str ) – Heading, Label to insert into the layout for this sub-layout (optional, never None)

- heading_ctxt ( str ) – Override automatic translation context of the given heading (optional, never None)

- translate ( bool ) – Translate the given heading, when UI translation is enabled (optional)

Returns :

Sub-layout to put items in

Return type :

UILayout

panel ( idname , * , default_closed = False ) 

Creates a collapsible panel. Whether it is open or closed is stored in the region using the given idname. This can only be used when the panel has the full width of the panel region available to it. So it can’t be used in e.g. in a box or columns.

Parameters :

- idname ( str ) – Identifier of the panel (never None)

- default_closed ( bool ) – Open by Default, When true, the panel will be open the first time it is shown (optional)

Returns :

layout_header , Sub-layout to put items in, UILayout

layout_body , Sub-layout to put items in. Will be none if the panel is collapsed., UILayout

Return type :

tuple[UILayout, UILayout]

panel_prop ( data , property ) 

Similar to .panel(...) but instead of storing whether it is open or closed in the region, it is stored in the provided boolean property. This should be used when multiple instances of the same panel can exist. For example one for every item in a collection property or list. This can only be used when the panel has the full width of the panel region available to it. So it can’t be used in e.g. in a box or columns.

Parameters :

- data (AnyType) – Data from which to take the open-state property (never None)

- property ( str ) – Identifier of the boolean property that determines whether the panel is open or closed (never None)

Returns :

layout_header , Sub-layout to put items in, UILayout

layout_body , Sub-layout to put items in. Will be none if the panel is collapsed., UILayout

Return type :

tuple[UILayout, UILayout]

column_flow ( * , columns = 0 , align = False ) 

column_flow

Parameters :

- columns ( int ) – Number of columns, 0 is automatic (in [0, inf], optional)

- align ( bool ) – Align buttons to each other (optional)

Returns :

Sub-layout to put items in

Return type :

UILayout

grid_flow ( * , row_major = False , columns = 0 , even_columns = False , even_rows = False , align = False ) 

grid_flow

Parameters :

- row_major ( bool ) – Fill row by row, instead of column by column (optional)

- columns ( int ) – Number of columns, positive are absolute fixed numbers, 0 is automatic, negative are automatic multiple numbers along major axis (e.g. -2 will only produce 2, 4, 6 etc. columns for row major layout, and 2, 4, 6 etc. rows for column major layout). (in [-inf, inf], optional)

- even_columns ( bool ) – All columns will have the same width (optional)

- even_rows ( bool ) – All rows will have the same height (optional)

- align ( bool ) – Align buttons to each other (optional)

Returns :

Sub-layout to put items in

Return type :

UILayout

box ( )

A nested layout whose items stack vertically in a single column, with a box drawn around the whole group.

Returns :

Sub-layout to put items in

Return type :

UILayout

split ( * , factor = 0.0 , align = False )

split

Parameters :

- factor ( float ) – Percentage, Fraction of the available width at which to divide; omit it to let Blender compute the split automatically (in [0, 1], optional)

- align ( bool ) – Align buttons to each other (optional)

Returns :

Sub-layout to put items in

Return type :

UILayout

menu_pie ( )

A nested layout in which child items are arranged radially around the center of the menu.

Returns :

Sub-layout to put items in

Return type :

UILayout

classmethod icon ( data )

Look up the custom icon belonging to the given data — handy, for instance, when you need a material or texture icon.

Parameters :

data (AnyType) – Data from which to take the icon (never None)

Returns :

Icon identifier (in [0, inf])

Return type :

int

classmethod enum_item_name ( data , property , identifier )

Fetch the display name shown in the UI for the given enum item.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- identifier ( str ) – Identifier of the enum item (never None)

Returns :

UI name of the enum item (never None)

Return type :

str

classmethod enum_item_description ( data , property , identifier )

Fetch the tooltip-style description shown in the UI for the given enum item.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- identifier ( str ) – Identifier of the enum item (never None)

Returns :

UI description of the enum item (never None)

Return type :

str

classmethod enum_item_icon ( data , property , identifier )

Fetch the icon associated with the given enum item.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- identifier ( str ) – Identifier of the enum item (never None)

Returns :

Icon identifier (in [0, inf])

Return type :

int

prop ( data , property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , placeholder = '' , expand = False , slider = False , toggle = -1 , icon_only = False , event = False , full_event = False , emboss = True , index = -1 , icon_value = 0 , invert_checkbox = False )

Item. Surfaces a single RNA item as a control in the layout.

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- placeholder ( str ) – Hint describing the expected value when empty (optional)

- expand ( bool ) – Expand button to show more detail (optional)

- slider ( bool ) – Use slider widget for numeric values (optional)

- toggle ( int ) – Use toggle widget for boolean values, or a checkbox when disabled (the default is -1 which uses toggle only when an icon is displayed) (in [-1, 1], optional)

- icon_only ( bool ) – Draw only icons in buttons, no text (optional)

- event ( bool ) – Use button to input key events (optional)

- full_event ( bool ) – Use button to input full events including modifiers (optional)

- emboss ( bool ) – Draw the button itself, not just the icon/text. When false, corresponds to the ‘`NONE_OR_STATUS`’ layout emboss type. (optional)

- index ( int ) – The index of this button, when set a single member of an array can be accessed, when set to -1 all array members are used (in [-2, inf], optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

- invert_checkbox ( bool ) – Draw checkbox value inverted (optional)

props_enum ( data , property )

props_enum

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

prop_menu_enum ( data , property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' )

prop_menu_enum

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

prop_with_popover ( data , property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , icon_only = False , panel )

prop_with_popover

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_only ( bool ) – Draw only icons in tabs, no text (optional)

- panel ( str ) – Identifier of the panel (never None)

prop_with_menu ( data , property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , icon_only = False , menu )

prop_with_menu

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_only ( bool ) – Draw only icons in tabs, no text (optional)

- menu ( str ) – Identifier of the menu (never None)

prop_tabs_enum ( data , property , * , data_highlight = None , property_highlight = '' , icon_only = False , expand_as = 'DEFAULT' )

prop_tabs_enum

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- data_highlight (AnyType) – Data from which to take highlight property (optional, never None)

- property_highlight ( str ) – Identifier of highlight property in data (optional, never None)

- icon_only ( bool ) – Draw only icons in tabs, no text (optional)

- expand_as ( Literal [ 'DEFAULT' , 'ROW' ] ) – (optional)

prop_enum ( data , property , value , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' )

prop_enum

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- value ( str ) – Enum property value (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

prop_search ( data , property , search_data , search_property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , results_are_suggestions = False , item_search_property = '' )

prop_search

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- search_data (AnyType) – Data from which to take collection to search in (never None)

- search_property ( str ) – Identifier of search collection property (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- results_are_suggestions ( bool ) – Accept inputs that do not match any item (optional)

- item_search_property ( str ) – Identifier of the string property in each collection’s items to use for searching (defaults to the items’ type ‘name property’) (optional, never None)

prop_decorator ( data , property , * , index = -1 )

prop_decorator

Parameters :

- data (AnyType) – Data from which to take property (never None)

- property ( str ) – Identifier of property in data (never None)

- index ( int ) – The index of this button, when set a single member of an array can be accessed, when set to -1 all array members are used (in [-2, inf], optional)

operator ( operator , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , emboss = True , depress = False , icon_value = 0 , search_weight = 0.0 )

Item. Adds a button to the layout that triggers an Operator when clicked.

Parameters :

- operator ( str ) – Identifier of the operator (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- emboss ( bool ) – Draw the button itself, not just the icon/text (optional)

- depress ( bool ) – Draw pressed in (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

- search_weight ( float ) – Search Weight, Influences the sorting when using menu-seach (in [-inf, inf], optional)

Returns :

Operator properties to fill in

Return type :

OperatorProperties

operator_menu_hold ( operator , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , emboss = True , depress = False , icon_value = 0 , menu )

Item. Adds a button to the layout that triggers an Operator when clicked.

Parameters :

- operator ( str ) – Identifier of the operator (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- emboss ( bool ) – Draw the button itself, not just the icon/text (optional)

- depress ( bool ) – Draw pressed in (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

- menu ( str ) – Identifier of the menu (never None)

Returns :

Operator properties to fill in

Return type :

OperatorProperties

operator_enum ( operator , property , * , icon_only = False )

operator_enum

Parameters :

- operator ( str ) – Identifier of the operator (never None)

- property ( str ) – Identifier of property in operator (never None)

- icon_only ( bool ) – Draw only icons in buttons, no text (optional)

operator_menu_enum ( operator , property , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' )

operator_menu_enum

Parameters :

- operator ( str ) – Identifier of the operator (never None)

- property ( str ) – Identifier of property in operator (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

Returns :

Operator properties to fill in

Return type :

OperatorProperties

label ( * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , icon_value = 0 )

Item. Puts a piece of text, an icon, or both into the layout.

Parameters :

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

menu ( menu , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , icon_value = 0 )

menu

Parameters :

- menu ( str ) – Identifier of the menu (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

menu_contents ( menu )

menu_contents

Parameters :

menu ( str ) – Identifier of the menu (never None)

popover ( panel , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , icon_value = 0 , direction = 'VERTICAL' )

popover

Parameters :

- panel ( str ) – Identifier of the panel (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

- direction ( Literal [ 'VERTICAL' , 'HORIZONTAL' ] ) – Popup Direction, Where the popup panel opens in relation to the button it springs from (optional)

- VERTICAL
Vertical – Draw popup panel above or below the button.

- HORIZONTAL
Horizontal – Draw popup panel to the side of the button.

popover_group ( space_type , region_type , context , category )

popover_group

Parameters :

- space_type (Literal[Space Type Items]) – Space Type

- region_type (Literal[Region Type Items]) – Region Type

- context ( str ) – panel type context (never None)

- category ( str ) – panel type category (never None)

separator ( * , factor = 1.0 , type = 'AUTO' )

Item. Adds a gap between neighbouring items in the layout.

Parameters :

- factor ( float ) – Percentage, Fraction of the width to leave empty; omit it to fall back to the standard gap (in [0, inf], optional)

- type ( Literal [ 'AUTO' , 'SPACE' , 'LINE' ] ) – Type, Which kind of separator to draw (optional)

- AUTO
Auto – Best guess at what type of separator is needed..

- SPACE
Empty space – Horizontal or Vertical empty space, depending on layout direction..

- LINE
Line – Horizontal or Vertical line, depending on layout direction..

separator_spacer ( )

Item. Adds a stretchy horizontal gap between layout items.

progress ( * , text = '' , text_ctxt = '' , translate = True , factor = 0.0 , type = 'BAR' )

Progress indicator

Parameters :

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- factor ( float ) – Factor, Amount of progress from 0.0f to 1.0f (in [0, 1], optional)

- type ( Literal [ 'BAR' , 'RING' ] ) – Type, The type of progress indicator (optional)

context_pointer_set ( name , data )

context_pointer_set

Parameters :

- name ( str ) – Name, Name of entry in the context (never None)

- data (AnyType) – Pointer to put in context

context_string_set ( name , value )

context_string_set

Parameters :

- name ( str ) – Name, Name of entry in the context (never None)

## See also

- [Bpy Struct](bpy-struct.md)

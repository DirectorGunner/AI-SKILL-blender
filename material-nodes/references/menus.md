# Menus, Arranging Nodes, Nodes, Node Parts ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Menus; Arranging Nodes; Nodes; Node Parts; Selecting Nodes; Frame Node; Combine Bundle Node; Get Bundle Item Node; Join Bundle Node.

## Menus

Blender uses many kinds of menus to reach options and Operators. Ways to interact with a menu:
Mouse selection — LMB the item you want.
Numerical selection — use the number keys or numpad to pick an item by position; Numpad1 selects the first item, and so on.
If a menu is too tall for the screen, a small scrolling triangle appears at the top or bottom; scroll by moving the mouse past that triangle.
Shortcuts:
- Use Wheel while hovering with the mouse.
- Navigate with the arrow keys.
- Each item has an underlined character you can press to trigger it.
- Number keys or numpad also activate items (1 for the first item, 2 for the second, and so on; in larger menus Alt-1 hits the 11th, up to Alt-0 for the 20th).
- Press Return to activate the highlighted item.
- Press Esc to close without choosing anything — you can also do this by moving the cursor far from the menu, or by LMB-clicking anywhere outside it.

Popup Menus: these list Operators you run by clicking with LMB or pressing the generated shortcut shown by the operator name's underlined character; every entry shows any relevant shortcut keys, which work without opening the menu. Search any popup menu by pressing Spacebar and typing the operator name; if the menu already has "Search" as an item, you can search it without pressing Spacebar first. All of an editor's popup menus can be searched via the Menu Search feature.
Collapsing Menus: to gain horizontal space in the header, collapse the menus from the header context menu — RMB the header and uncheck the Show Menus checkbox.

Select Menus: a Select Menu (or "selector") lets you pick from a predefined list of options, appearing as a text label and/or icon with a down arrow on the right. Click LMB to open it and choose; the choice then appears inside the button. You can also cycle options without opening it by scrolling over the button with Ctrl-Wheel.
Expanded View: some select menus use an expanded layout showing every option at once, with the active one highlighted by a colored background; in some cases you can pick multiple options by holding Shift and clicking LMB.

Popover Menus: like Select Menus, but able to show more varied content such as a title, buttons, sliders, and so on.

Context Menu: a pop-up opened with RMB (in most editors the Menu key works too), whose contents depend on where the pointer is. Opened in an editor, it lists operators sensitive to that editor's mode; opened over buttons and properties, common entries include:
Single — apply the change to a single value of a set (e.g. only the X coordinate of an object's Location).
All — apply the change to all values of a set (e.g. all coordinates of an object's Location).
Reset to Default Value(s) (Backspace) — replace the current value with the default.
Copy Data Path (Shift-Ctrl-C) — copy the Python property data path relative to the data-block; useful for Python scripting.
Copy Full Data Path (Shift-Ctrl-Alt-C) — copy the full Python property data path, including any needed context information.
Copy As New Driver — create a new driver using this property as input and copy it to the clipboard; use Paste Driver to add it to another property, or Paste Driver Variables to extend an existing driver with a new input variable.
Copy To Selected — copy the property value to the selected object's corresponding property (a use case is when the Properties context is pinned).
Assign Shortcut — define a keyboard or mouse shortcut for an operation; move the cursor over the button that pops up, and when "Press a key" appears, press and/or click the desired shortcut (Esc cancels). See Keymap.
Change Shortcut — redefine the shortcut.
Remove Shortcut — unlink the existing shortcut.
Open File Location, Open Location Externally — open the containing folder using the operating system's file manager.
Online Manual (F1) — open a Blender Manual page in a web browser.
Online Python Reference — context-sensitive access to the Python API Reference.
Edit Source — for UI development: create a text data-block with the source code associated with the control (when it's based on a Python script), pointing in the Text Editor at the line where the element is defined.
Edit Translation — for UI development: point at the translation code line.

Pie Menus: a pie menu spreads its items radially around the mouse. Tip: the fastest way to use one is to hold the invoking key(s), nudge the mouse slightly toward a selection, and release the key(s) to activate it — releasing without moving keeps the menu open so you can click an item, while moving before releasing instantly activates the item nearest the mouse.

The central disc widget of a pie menu shows the current direction; the selected item highlights. Menu validity for item selection depends on the mouse touching or extending beyond this center disc.

Pie menu items support key accelerators (underlined letters) and number keys for activation.

When sub-pies are present, a plus icon indicates their availability.

## Arranging Nodes

Node snapping aligns position and size to a background grid, toggled via the snap icon in the editor header or temporarily with Ctrl while transforming.

Auto-offset automatically repositions left or right nodes when a new node with input and output sockets is dropped onto an existing connection, organized by the direction setting. Enabled by default, it can be disabled in Preferences. Press T while moving a node to toggle offset direction. The margin is configurable in Preferences under Auto-offset Margin.

## Nodes

Blender contains node-based editors for different purposes; this section explains general node operation. Editor types: Geometry Nodes (procedural modeling), Shader Nodes (material creation), Composite Nodes (rendered-image editing), Texture Nodes (custom texture creation).

## Node Parts

All Blender nodes share a common construction — regardless of type — comprising the title, sockets, properties, and more.

Title — shows the node's name/type, which can be overridden via the node's Label. The collapse toggle on the title's left side collapses the node, which you can also do with H.
Preview — an overlay showing a small image above the node with the node's result. Not every node supports previews; those that do can be toggled via the icons in the node's top-right corner next to the title. Disable previews for the whole node tree with the Previews overlay toggle.

Sockets — a node's input and output values, shown as little colored circles on either side of the node; hide unused ones with Ctrl-H. Each socket is color-coded by the data type it handles.
Built-in:
- Shader (bright green) — shaders in Cycles and EEVEE.
- Geometry (Sea Green) — used in Geometry Nodes.
- Menu (Dark Grey) — enum-style inputs shown as a dropdown menu or radio button in the UI.
- Bundle (dark turquoise) — a generic bundle of multiple data types grouped together (e.g. geometry, vectors, or colors) for compact data transfer between nodes.
- Closure (light brown) — used in Shader Nodes and Geometry Nodes for logical or procedural encapsulation; a closure stores and passes groups of node inputs and logic, enabling reusable "callable" node behaviors.
Data:
- Boolean (light pink) — passes a true or false value.
- Color (yellow) — accepts/produces color information, with or without an alpha component depending on the node tree type.
- Float (light gray) — accepts/produces floating-point numbers.
- Integer (lime green) — passes an integer value (a number without a fractional component).
- String (light blue) — passes a text value.
- Vector (dark blue) — vector data such as coordinates and normals, with 2, 3, or 4 components: 2D (shows and uses only X and Y), 3D (X, Y, and Z), 4D (X, Y, Z, and W).
- Rotation (pink) — a rotation/quaternion.
- Matrix (dark pink) — a 4×4 matrix of float values, often used to represent a Transformation Matrix.
Data-Blocks:
- Collection (white) — passes a collection data-block.
- Object (orange) — passes an object data-block.
- Material (salmon) — passes a material data-block.
- Texture (pink) — passes a texture data-block.
- Image (apricot) — passes an image data-block.
- Font (brown) — passes a font data-block.

Socket Shape — data sockets can take different shapes for the data structure used to transport data; the structure sets how values are passed and interpreted, and more complex structures move multiple values through a single connection.
- Auto — automatically detects a good structure type based on how the socket is used.
- Dynamic (Circle) — works with multiple structure types.
- Single (Square) — expects a single value.
- Fields (Diamond) — a value that can vary per element (e.g. per point, edge, or face); think of a field as a "value map," similar to how a grayscale image's pixel brightness represents varying values across space. Connecting a single value to a field socket implicitly broadcasts it, so every element receives the same value. Field appearances: Diamond (the socket accepts a field input or outputs a field; a constant single value can connect, but then the output often won't vary per element) and Diamond with Dot (the socket can be a field but is currently a single value — helpful for tracking where single values are calculated rather than a many-result field, and it makes Socket Inspection show the value instead of field input names). See the Geometry Nodes Fields documentation.
- Grid (Four Squares) — a grid data structure storing values sampled across a 2D surface or a 3D volume (such as image pixels, voxel densities, or other sampled values in space), allowing complex operations where values are distributed continuously across space rather than attached to individual geometry elements.

Inputs — located on the node's bottom-left, supplying the data the node needs to do its job. Except for the green shader input, each input socket when disconnected has a default value editable via a color, numeric, or vector interface input. Some nodes have special sockets that accept multiple inputs, drawn with an ellipsis shape rather than a circle to mark their special behavior.
Outputs — located on the node's top-right, connectable to the inputs of nodes further down the node tree.
Conversion — some socket types can convert to others, implicitly or explicitly. Implicit conversion happens automatically without a conversion node — for example, Float sockets and Color sockets can link to each other. Once a conversion is made, data may be lost and can't be retrieved later down the tree, and implicit conversion can sometimes change the data units: plugging a Value input node into an angle socket defaults to radians regardless of the scene's Units, because the Value node has no unit while the angle input does.

Valid socket conversions connect color/vector, color/float, color/float/vector to shaders, integers/floats, floats/vectors, floats/booleans, and rotations/matrices. Explicit conversion uses nodes like Shader To RGB or RGB to BW. The Math Node also handles degree/radian conversion.

Most nodes have settings affecting input/output interaction, located below outputs and above inputs. Example: controls on the Chroma Key node illustrate property placement.

## Selecting Nodes

Nodes in the editor can be selected and manipulated; selections decide which nodes can be moved, duplicated, or connected. The active node (last selected) is highlighted with a lighter outline and serves as the reference for operations such as grouping or linking, and it also determines which properties show in the Sidebar and Properties Editor. Select nodes with LMB, or several at once with Shift-LMB. Blender also offers selection tools and shortcuts to pick nodes quickly by type, connections, or layout.

All (Menu: Select ‣ All; Shortcut: A) — select all nodes.
None (Menu: Select ‣ None; Shortcut: Alt-A) — deselect all nodes.
Invert (Menu: Select ‣ Invert; Shortcut: Ctrl-I) — flip the current selection, selecting the unselected nodes and deselecting the selected ones.
Box Select (Menu: Select ‣ Box Select; Shortcut: B) — click and drag to select nodes within a rectangular region (see Box Select).
Circle Select (Menu: Select ‣ Circle Select; Shortcut: C) — click and drag with a circular brush to select nodes (see Circle Select).
Lasso Select (Menu: Select ‣ Lasso Select) — draw a freeform lasso to select the nodes within the region (see Lasso Select).
Linked From (Menu: Select ‣ Linked From; Shortcut: L) — extend the selection to all nodes connected to the inputs of the selected nodes.
Linked To (Menu: Select ‣ Linked To; Shortcut: Shift-L) — extend the selection to all nodes connected from the outputs of the selected nodes.
Select Grouped (Menu: Select ‣ Select Grouped; Shortcut: Shift-G) — select nodes sharing similar properties with the active node:
- Type: all nodes of the same type (e.g. all Math nodes).
- Color: nodes with the same custom color (this means user-assigned editor colors, not the color data nodes process).
- Prefix/Suffix: nodes whose names match the same starting or ending text.
Activate Same Type Previous/Next (Menu: Select ‣ Activate Same Type Previous/Next; Shortcut: Shift-] / Shift-[) — cycle through nodes of the same type, activating the previous or next node in the tree and centering it in the view.
Find Node (Menu: Select ‣ Find Node; Shortcut: Ctrl-F) — open a search pop-up to quickly locate and select a node in the current node tree, searching by name, socket label, warning messages, or certain socket values such as strings and data-block references. Selecting a match automatically pans and centers the view on the found node and highlights it — especially useful for navigating complex networks in large node trees efficiently.

## Frame Node

The Frame node organizes and groups other nodes within the editor, helping manage complex node trees by visually clustering related nodes. It's especially useful when a setup is too large to view easily at once, or to separate logical sections of a tree without creating a reusable Node Group.

Usage:
- Add nodes to a frame by dragging them inside it.
- Moving the frame also moves all the nodes it contains.
- Resize a frame by dragging its corners or edges.
- A frame can display a custom label, handy for naming sections of your node setup.

Properties:
Label Size — the font size of the label, for example so subordinate frames have smaller titles.
Shrink — once a node is placed in the Frame, the Frame shrinks around it to remove wasted space; at that point you can no longer select the Frame's edge to resize it, since resizing instead happens automatically as the nodes inside are rearranged. Disable this option to change that behavior.
Text — to display more comprehensive text, a frame node can show the contents of a text data-block; this is read-only, so use the Text Editor to modify the contents.

Editing:
Join in New Frame (Menu: Node ‣ Join in new Frame; Shortcut: F) — create a new Frame node around the selected nodes; when invoked with F, a popup lets you assign a custom Label to the new frame, shown as its title to describe its contents.
Add to Frame (Shortcut: Ctrl-P) — once a frame node is placed, add nodes by dropping them onto the frame, or by selecting the node(s) then the frame and pressing Ctrl-P — think of it as parenting the selection to the frame.
Remove from Frame (Menu: Node ‣ Remove from Frame; Shortcut: Alt-P) — select nodes and press Alt-P to remove them from a frame — think of it as unparenting the selection from the frame.

## Combine Bundle Node

The Combine Bundle node creates a bundle from multiple inputs, each becoming an element identified by socket name. Access values elsewhere using Separate Bundle.

Inputs are arbitrary in count and type, supporting Geometry, Objects, Values (float, integer, boolean, vector, color), Fields, and Nested Bundles. Properties (sidebar Node tab): Sync Sockets updates the node to match connected nodes after renaming/adding/removing; Define Signature locks the list/types for stable interfaces when publishing (disables adding/removing until toggled off).

Bundle Items displays per-element entries (double-click to rename). Add Item creates a socket. Remove Item deletes one. Type selects the data type (float/vector/geometry/object/bundle); value types show a default-value control. Outputs the resulting bundle containing all inputs.

### Combine Bundle Node

Bundle creation from multiple inputs: each becomes a named bundle element.
Access individual items using Separate Bundle elsewhere in the network.

### Inputs

Arbitrary input sockets, custom names and types.
Supported types: Geometry, Objects, Values (float, integer, boolean, vector, color), Fields, Nested Bundles.

### Properties

Properties appear in the Node tab of the Sidebar.

**Sync Sockets**
Align the node to connected node signatures.
Use after socket rename, add, or remove.

**Define Signature**
Lock items and types for stable publication.
Blocks add/remove until disabled.

### Bundle Items

**List of bundle items**
One entry per element.
Double-click to rename.

**Add Item**
Insert a socket.

**Remove Item**
Delete the selected socket.

**Type**
Data type (e.g. Float, Vector, Geometry, Object, Bundle).
Value types show default value control.

### Outputs

**Bundle**
All defined inputs packaged together.

### Combine Bundle Node

This node assembles a new Bundle out of several input values. Each input lands in the bundle as an element keyed by its socket name. Elsewhere in the node tree you can pull those values back out with the
Separate Bundle

### Inputs

You can give the node any number of input sockets. Each one takes a custom name and type. Supported types include (but are not limited to):

- Geometry

- Objects

- Values (e.g. float, integer, boolean, vector, color)

- Fields

- Nested Bundles

### Properties

You will find the properties under the Sidebar's Node tab.

Sync Sockets
Realigns this node so its sockets match the signature of whatever it is wired to. Trigger it after any rename, addition, or removal among the sockets.

Define Signature
Locks down today's item list and their types, holding interfaces steady as node groups get published. With it on, you cannot add or drop items until it is switched back off.

### Bundle Items

List of bundle items
One row shows up for each element the bundle holds; rename a row by double-clicking it.

Add Item
Attach a fresh socket to the bundle.

Remove Item
Drop the socket you have selected.

Type
Data type carried by the chosen item (e.g. Float, Vector, Geometry, Object, Bundle). Value types surface a default-value control, which kicks in whenever that socket is left unlinked.

### Outputs

Bundle
The resulting bundle, holding every input you defined.

## Get Bundle Item Node

The Get Bundle Item node retrieves values from bundles using string paths. Bundles group heterogeneous data; this node accesses individual items. Non-existent paths return defaults with Exists set to false.

Bundle inputs the source bundle. Path identifies the item (slash-separated for nested bundles, e.g., settings/size, attributes/color). Remove (when enabled) deletes the item before passing the bundle through.

Socket Type (properties) sets the retrieved-item data type, determining Item output type. Shape (sidebar) specifies data structure (Single, Field, Grid).

Bundle outputs the resulting bundle (post-optionally-removing). Item outputs the value at the path or default if not found. Exists outputs True if found, False otherwise.

### Get Bundle Item Node

Retrieves a value from a bundle via string path.
Bundles group heterogeneous data; this node unpacks individual items.

If the path is absent, a default is returned and Exists outputs false.

### Inputs

**Bundle**
Input data source.

**Path**
Item location via slash-separated segments.
Examples: `settings/size`, `attributes/color`.

**Remove**
If on, delete the retrieved item before passing the bundle through.

### Properties

**Socket Type**
Item output data type.

**Shape**
Data structure (Single, Field, Grid).
Controls evaluation and passage through the network.
Sidebar option.

### Outputs

**Bundle**
Result after optional item removal.

**Item**
Retrieved value at the path, or the default if absent.

**Exists**
True if found; False otherwise.

## Join Bundle Node

The Join Bundle node combines multiple input bundles into a single output bundle. Each input bundle merges by name. If multiple bundles contain same-name sockets (duplicate keys), the first occurrence is used; an information icon signals detection.

Bundle inputs one or more bundles to combine. Bundle outputs the merged result containing all input items. Use Separate Bundle Node to extract items if needed.

### Join Bundle Node

Merge multiple bundles: each input's contents fold into the output.

### Inputs

**Bundle**
One or more input bundles to merge.
Contents merge by name into the output.

**Note:** If multiple inputs share socket names (duplicates), the first occurrence wins.
An information icon flags duplicates in the header.

### Outputs

**Bundle**
Combined bundle holding all input items.

Use Separate Bundle to extract individual items if needed.

### Join Bundle Node

This node folds several bundles into one output bundle. Each input bundle wired in is merged with the rest, leaving a lone bundle carrying everything the inputs held.

### Inputs

Bundle
A bundle or several, to be combined. Each one's contents fold into the output bundle keyed by name.

Note

Where several bundles carry sockets sharing a name (duplicate keys), the value from the first one wins. An information icon in the node header flags any duplicate keys it spots.

### Outputs

Bundle
The resulting bundle, holding every item from the input bundles.

Reach for the Separate Bundle Node to pull individual items back out of the combined bundle when you need them.

# Node Groups, Node Editors, Reroute Node, Node Bundles ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Node Groups; Node Editors; Reroute Node; Node Bundles; Data-Block Menu.

## Node Groups

Grouping nodes can simplify a node tree by hiding complexity and reusing common functionality. A node group is recognizable by its green title bar. Conceptually, node groups let you treat a set of nodes as a single unit — much like functions in programming: reusable, composable, and parametrizable. For instance, say you build a "Wood" material and want it in several colors: rather than duplicating the whole setup per color (a pain to maintain if you later change the grain detail), move the wood-pattern nodes into a node group, have each material reuse that group and pass its own color in, and then any grain-detail change is made once, inside the group. Node groups can be nested — a group can contain other groups.
Note: recursive node groups are forbidden to prevent infinite recursion; a group cannot contain itself, directly or indirectly.
Tip: like other data-blocks, node groups whose names start with . are hidden from menus and lists and reachable only via search — handy for node-asset authors who want internal utility groups hidden from end users.

Group Input and Group Output nodes represent the data flowing into and out of the group. The Group Input node exposes the group's input sockets from inside it; these act as parameters that steer the group's behavior from outside, and you connect them to internal nodes to drive values such as factors, colors, or geometry inputs.
Note: input values that don't affect the output are grayed out.
The Group Output node defines what the group passes out; only sockets connected to it become outputs on the group itself.
Important: avoid using output nodes such as Material Output inside node groups — keep those on the top-level node tree to make groups more reusable. Use Group Output to pass data out of a node group.

Usage — Managing Inputs/Outputs: add, remove, and reorder input/output sockets in the Group panel in the Sidebar; you can also create a socket directly by dragging a link to or from the hollow socket on the Group Input or Group Output node to another socket in the editor.
Reusing Node Groups (Menu: Add ‣ Group; Shortcut: Shift-A): once defined, a node group can be placed again, in the same tree or another, and you can import groups from another blend-file via File ‣ Link/Append.
Tip: when appending groups from another blend-file, Blender doesn't distinguish types like material vs. compositing groups, so adopt a naming convention — prefixes such as Mat_, Comp_, Geo_ — to signal each group's context.

Properties — Group (Panel: Sidebar ‣ Group ‣ Group): properties about the group node, such as its name and look.
Name — the node's name shown in the Title.
Description — the message shown when hovering the Title or in add menus.
Color Tag — the group's color tag, which influences the header color.
Node Width — the width for newly created group nodes.
(Set Default Node Width) — set the width from the parent group node in the current context.
Show Manage Panel (Geometry Nodes) — show the Manage panel in Geometry Nodes modifiers when creating a modifier from a node-group asset.
Usage (Geometry Nodes) — this panel shows only in the Geometry Node Editor.
- Modifier: the group is meant for the Geometry Nodes Modifier.
- Tool: the group is meant to be used as a tool.
The data-block menu in the Geometry Node Editor header lists only groups whose Usage matches the current Node Tree Sub-Type.
Tip: if you disable both Usages by accident, the group drops off the data-block menu; to get it back, add it as a node in another group (Add ‣ Group), select it, press Tab to enter it, and re-enable a Usage.

Group Sockets (Panel: Sidebar ‣ Group ‣ Group Sockets): add, remove, reorder, and edit a node group's interface elements, defining how sockets appear on the group node and organizing them for clarity and usability. Available item types:
- Inputs: define the group's input sockets.
- Outputs: define the group's output sockets.
- Panels: group related sockets together for structuring complex setups; panels always sit at the bottom of the node interface and can be nested by dragging one panel onto another in the interface item list.
- Panel Toggle: add a boolean checkbox to a panel's header to control its contents; available only when a panel is selected in the interface item list. Panel toggles have their own options under the Panel Toggle subpanel, and a toggle socket isn't listed directly — a panel with a toggle instead shows a boolean socket icon by its name; unlink it from the panel to make the toggle socket visible again.
Note: a panel toggle doesn't automatically disable or grey out its sockets; to disable sockets visually and functionally, use a Switch Node or similar logic and disconnect the socket manually.
Interface Item List — a UI list view of all input/output sockets and panels; each item can be renamed and configured individually, and its name appears in the node's user interface.

The Group panel contains properties for the group node itself. Name identifies the node uniquely within its tree. Label provides a custom title displayed in the header (not required to be unique). Color Tag influences header appearance. Node Width sets width for newly created group nodes; (Set Default Node Width) bases it on the parent.

Show Manage Panel Geometry Nodes enables the Manage panel in Geometry Nodes modifiers when creating from a node group asset.

Usage (Geometry Nodes only): Modifier indicates use with Geometry Nodes Modifier; Tool marks it as a tool. The data-block menu in the Geometry Node Editor header only lists groups matching the current Node Tree Sub-Type. If both Usages accidentally disable, add the group to another group (Add ‣ Group), select that node, press Tab to enter, and re-enable one Usage.

The Group Sockets panel adds, removes, reorders, and edits the user interface of a node group, organizing sockets for clarity. Item types include: Inputs (define input sockets), Outputs (define output sockets), Panels (group related sockets; appear at the bottom, nestable), Panel Toggle (boolean checkbox for panel headers; toggle sockets aren't listed directly—panels with toggles show a boolean icon; toggles don't auto-disable sockets, so use Switch Nodes or disconnect manually).

The Interface Item List displays all sockets and panels; each is renamable and configurable. Selecting a socket label on the node also selects it in this list. Specials: Duplicate Item copies a socket/panel; Make Panel Toggle converts a boolean input into a panel toggle (available when a panel is selected and the active item is boolean); Unlink Panel Toggle removes the toggle relationship, making it a regular input.

Socket properties vary by type, input/output, data type, and node tree. Type specifies the socket's data type. Description provides hover text. Attribute Domain (Geometry Nodes output—Integer, Color, Vector, Boolean, Float) indicates the geometry element type. Default Attribute (Geometry Nodes input) sets the default attribute name for modifiers. Subtype interprets and displays data; changing subtype doesn't alter the underlying type, only presentation. Integer subtypes: None (standard), Percentage (0–100), Factor (0.0–1.0 normalized). Float subtypes: None, Percentage, Factor, Mass (scene units), Angle (degrees/radians per scene settings), Time (Scene Relative—frames converted to seconds by frame rate), Time (Absolute—seconds), Distance (scene length units), Wavelength (mm/µm/nm/pm), Color Temperature (Kelvin), Frequency (hertz). Vector subtypes: None, Percentage (each component as percentage), Factor (normalized), Translation (scene units), Direction (typically normalized), Velocity (speed/direction), Acceleration (velocity rate), Euler Angles, XYZ (Cartesian, with optional W component). String subtypes: None (standard text), File Path (file selection dialogs). Dimensions Vector sets component count: 2D (X, Y), 3D (X, Y, Z), 4D (X, Y, Z, W). Default is the value when unconnected. Min/Max limit UI controls (not data clamping). Expanded Menu shows all options at once (in node editors without labels; in modifier/operator panels with labels). Default Input (Geometry Nodes input—Integer, Vector, Matrix) is used when unconnected (requires Hide Value enabled). Optional Label indicates the label isn't necessary. Hide Value hides default values even when unconnected. Layer Selection (Geometry Nodes input boolean) takes Grease Pencil layers. Hide in Modifier (Geometry Nodes input) hides the input value in modifier interfaces. Shape (Geometry Nodes input) specifies higher-order data: Auto (most appropriate), Dynamic (flexible), Single (constants only), Field (field values), Grid (grid data structure).

Panel properties: Description provides hover text. Closed by Default collapses the panel on new nodes.

Animation controls animation data and active Actions/Slots (see Manually Assigning Actions and Slots).

Make Group (Menu: Node ‣ Make Group; Shortcut: Ctrl-G): create a new node group containing all selected nodes. Group Input and Group Output nodes are made to represent connections to the unselected nodes outside the group, with inputs routed to the Group Input and outputs to the Group Output. Grouping a single node gives a group that preserves the original node's interface (including panels and default values) and inherits its name; grouping multiple nodes builds the group with input and output sockets generated from the connections and a generic name such as "NodeGroup", "NodeGroup.001", and so on.

Insert Into Group (Menu: Node ‣ Insert Into Group): move the selected nodes into the active group node — select a set of nodes ending with the destination group node, then run the operation to move them in. The moved nodes are gathered into a group of their own (with their own group input and output nodes) to preserve their connection context, and the group's existing input/output nodes gain new sockets from the added nodes as needed. The node group must be edited to hold a single Group Input and a single Group Output node.

Edit Group (Menu: Node ‣ Edit Group; Header: Go to Parent Node Tree; Shortcut: Tab, Ctrl-Tab): with a node group selected, press Tab to move into it and see its content; press Tab again (or Ctrl-Tab) to leave and return to its parent, whether the top-level node tree or another node group. The breadcrumbs in the editor's top-left corner show where you are in the hierarchy.

Ungroup (Menu: Node ‣ Ungroup; Shortcut: Ctrl-Alt-G): remove the group and place its individual nodes into your editor workspace, losing no internal connections, so you can now link those nodes to others in your workspace.

Separate (Shortcut: P): remove the selected nodes from a node group and place them in the parent node tree — useful when nodes need editing outside a group for clarity or reuse.
Copy — duplicate the selected nodes into the parent node tree while keeping the originals inside the group, useful for reusing nodes outside the group while preserving its definition.
Move — move the selected nodes to the parent node tree, removing them from the original group, useful for simplifying a group or exposing its contents directly.

Join Group Inputs (Menu: Node ‣ Join Group Inputs; Shortcut: Ctrl-J): merge multiple selected Group Input nodes into one consolidated Group Input node where possible, preserving existing links and unifying duplicate inputs to cut clutter and simplify the node tree — useful for tidying groups that have become disorganized or hold redundant input nodes.

## Node Editors

Header — holds menus, buttons, and options that depend partly on the current node tree type.
View — change your view of the editor.
Select — select a node or groups of nodes.
Add — add nodes.
Node — act on the selected nodes.
Pinned — when enabled, the editor always shows the currently selected node tree regardless of changes to the active object or scene, letting you edit a material, texture, or compositor node tree independently of the 3D Viewport selection or active scene; handy when working across objects or scenes while keeping the editor on one specific tree.
Parent Node Tree — leave the current node group and return to the parent node group/tree.
Snapping — change options for snapping node positions for a cleaner node tree layout (see Arranging Nodes).

Overlays — information drawn on top of the nodes and node trees; a toggle beside the overlay popover shows or hides all overlays for the node editor.
Wire Colors — color node links by their connected sockets.
Reroute Auto Labels — label Reroute Nodes from the label of connected reroute nodes.
Context Path — show breadcrumbs in the upper-left corner marking the hierarchy location of the displayed node tree/group.
Annotations — show Annotations in the preview region.
Previews — show each node's Preview when that node's preview is also toggled on.
Timings — show each node's last execution time; available only for compositing and geometry nodes (for geometry nodes, see Node Timings Overlay).

Toolbar — a set of tools for use in the node editor.
Select — select or move nodes and links.
Select Box — select nodes or links by dragging a box around them.
Select Circle — select nodes or links by clicking or dragging with a circular brush.
Select Lasso — select nodes or links by drawing a free-form lasso.
Annotate — draw free-hand annotation.
Annotate Line — draw a straight-line annotation.
Annotate Polygon — draw a polygon annotation.
Annotate Eraser — erase previously drawn annotations.
Link Cuts — delete connections between nodes by drawing a line across the links (see Cut Links).
Mute Links — mute connections by drawing a line across the links; muted links stay in place but are ignored in evaluation (see Mute Links).
Add Reroute — insert a Reroute Node point on links by drawing a line across them; reroute nodes help organize complex node trees by redirecting connections.

Sidebar — properties for the currently selected node plus node-editor-specific settings.
Node (Panel: Sidebar ‣ Node): properties controlling the active node's behavior and appearance; available options depend on the node type and the editor.
Node:
- Name — a unique identifier for the node within its node tree, used internally for references.
- Label — a custom title shown at the top of the node; unlike Name it need not be unique, and it helps organize complex node trees.
- Color — by default the node background color follows the current theme; enable this to override it with a custom color (useful as a visual cue to group related nodes or highlight important parts), with the preset button beside the color field for saving and reusing custom colors.
- Node Color Specials — operators related to custom node colors. Copy to Selected — copy the active node's color to all selected nodes.
- Show Options — show or hide extra node-specific options in the node header, where the node type offers them.
- Mute — temporarily disable the node without removing it; where possible it's bypassed and its inputs pass straight to its outputs.
- Propagation (Geometry Nodes) — control which of this node's messages propagate to the parent node group or modifier: All Messages (informational messages, warnings, and errors), Errors and Warnings (only warnings and errors), Errors (only error messages), or None (no messages).
Properties — the properties shown depend on the selected node's type (a Mix node differs from a Mask node).
Custom Properties — create and manage your own properties to store data on the active node (see the Custom Properties page).
Tool (Panel: Sidebar region ‣ Tool) — Active Tool: this panel's info changes with the selected tool.
View (Panel: Sidebar region ‣ View) — Annotations: select the Annotate tool in the Toolbar to make annotations in the node editor (see Annotate Tool).

Navigating — done with both mouse movement and keyboard shortcuts.
Pan (MMB) — move the view up, down, left, and right.
Zoom (Ctrl-MMB, Wheel) — move the camera forward and back.
Frame Selected (NumpadPeriod) — zoom to fit only the selected nodes in the view.
Frame All (Home) — zoom to fit all nodes in the view.

Adding Nodes (Menu: Add; Shortcut: Shift-A): add nodes from the editor header's Add menu or with the keyboard shortcut. You can also add a node by dragging a connection from an existing node's input or output socket and dropping it over empty space instead of onto another socket — this opens a search menu of compatible nodes and their sockets that can be added and connected to the existing node, and confirming the selection adds the node for you to move and place.

## Reroute Node

The Reroute node organizes node trees, supporting one input with multiple outputs (pill-shaped socket). Shift+RMB across a link quickly inserts a Reroute node. Input stores unconnected-socket values.

## Node Bundles

Bundles group multiple values into one socket, like programming structs, enabling single-link passage of many values. Mixed types include geometry, fields, values, objects, or nested bundles. This reduces exposed group inputs/outputs and clarifies interfaces.

Available nodes: Combine Bundle and related nodes for bundle manipulation.

Usage: Simplified interfaces (group inputs into single sockets); physics simulations (package entities/constraints); declarative systems (store structured data for later evaluation); texture sets (combine PBR maps into one socket).

Socket syncing matches bundle inputs/outputs by name. Auto-sync occurs on first connection. Existing sockets don't auto-update (avoiding data loss). A Sync Sockets button appears when mismatches are detected, enabling manual synchronization.

### Node Bundles

A container grouping multiple values into one socket—like a struct in programming.
Bundles pass many values through a single link.
Reduce exposed inputs/outputs in a node group.
Mix data types: geometry, fields, values, objects, nested bundles.

Combining a cube and cylinder into a bundle, then unpacking.

### Nodes

Dedicated nodes for bundle creation and decomposition.
Both support flexible socket count and type.

### Usage

Bundles serve multiple workflows:

- **Simplified interfaces:** Group inputs into one socket.
- **Physics solvers:** Package entities and constraints.
- **Declarative data:** Store complex structured state for later evaluation.
- **Texture sets:** Combine PBR maps (Base Color, Roughness, Normal).

### Socket Syncing

Names match bundle inputs to outputs.
Mismatched signatures prompt automatic sync.

- First connection syncs automatically.
- Existing sockets never change auto-sync to prevent data loss.
- A Sync Sockets button appears in the header when mismatch is detected.

## Data-Block Menu

### Data-Block Menu

Picking a Data-Block (a material, for instance) so it can be linked onto something else (an object, say) is what this menu is for.

A data-block menu with a search field.

Type
An icon here flags the data-block type. The popup menu opens when you click the image or the down arrow. Drag the image instead and you can apply the data-block elsewhere. (Dropping a material onto an object in the 3D Viewport assigns it, for example. Dropping onto Data ID fields works too.)

List
Available data-blocks in the current blend-file, or a way to link an item from somewhere else. Alongside the items the menu can carry a preview, plus a search field for finding items by name.

Note

Names that start with . keep their data-blocks out of the list, unless the search field is given a string that also begins with ., or the Show Hidden Files/Data-Blocks user preference is on.

Name
Shows, and lets you edit, the name of the selected data-block.

User Count
How many users the data has (when there's more than one) appears here. Click it to make a single-user copy.

Say three separate objects all pointed at one material — its user count would read 3, and editing the material would hit all three. Select one of those objects, click the user count, and that object gets its own private copy of the material, free to change without disturbing the original still shared by the other two.

Fake User (shield icon)
Normally a data-block with no real users gets cleaned up (deleted) when the blend-file is saved. Assigning it a fake user heads that off, guaranteeing it "survives." In the drop-down list, an "F" prefix marks data-blocks carrying a fake user.

For a rundown of every data-block in the blend-file that lacks real users, switch the Outliner's Display Mode to Orphan Data.

New/Add (files icon)
Makes a fresh data-block (or copies the current one) and selects it.

Open File (folder icon)
Brings up the File Browser — to import an image, for instance.

Unpack File (bin icon)
Writes the file packed inside the current blend-file back out to an external one.

(Unlink Data-block)
Drops the link. Use Shift - LMB to zero the user count so the data can be wiped from the blend-file entirely.

At times a list of applied data-blocks appears (the materials used on an object, say).

See also

The Data System chapter goes deeper into data-blocks.

### Preview
A Data-Block menu with preview.

Rather than plain icons and names, some data-block menus carry large preview images in their drop-down.

### Data ID
A Data ID field.

Much like a Data Block Menu, a Data ID field exists purely for selection — creating new data or managing users isn't part of it.

These elements may appear:

Type
On the left, an icon names which data-block type is accepted.

Name
This text field doubles as a search box, matching against the list. Tab auto-completes a name as far as one unique match allows; with several matches you carry on typing; an invalid entry leaves the value where it was.

List
Picks the data-block straight away.

Eyedropper
Certain Data IDs offer an Eyedropper, reached via the pipette icon over on the right.

(Clear Button String)
The button on the right clears the reference when clicked.

### ID Sub-Data
Depending on the data-block type and how it's meant to be used, related kinds of ID sub-data may open up for selection.

Sub-data Example.

Vertex Group
Should the Target field hold a mesh or lattice Object, an extra field can appear for picking one of its vertex groups.

Bone
Should the Target field hold an armature Object, an extra field can appear for picking one of its bones.

Head/Tail
Once a bone is chosen, a numeric field may turn up to name a spot along it. A value of 0.0 marks the head and 1.0 the tail, with everything between interpolated linearly (0.5 landing dead center).

Use B-Bone Shape
On a bendy bone, this button bends the point along the B-spline arc running head to tail instead of letting it track a plain straight line.

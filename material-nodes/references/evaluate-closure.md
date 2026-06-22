# Evaluate Closure, Node Closures, Color Picker, Tree View

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Evaluate Closure; Node Closures; Color Picker; Tree View.

## Evaluate Closure

### Evaluate Closure

Wire a Closure Zone to this node and it runs that zone — the call site of the closure, firing the zone's internal graph and returning its results.

Closures make node groups dynamic by letting logic be passed into a separate tree instead of hard-coding it. At run time the attached closure evaluates in the current context, sockets matched by name on both input and output sides.

Typical jobs for this node:

- Dropping user behaviors into procedural systems (custom scattering, placement rules, shading logic).

- Feeding logic into reusable groups for advanced effects.

- Exposing optional customization inputs on high-level tools.

### Inputs

Closure
The thing evaluated here, fed from a Closure Zone. With nothing wired in, pass-through mode kicks in (covered below).

### Interface
You may add your own sockets by hand; each pairs by name with a matching input on the attached closure. Once connected, the sockets refresh themselves to mirror the closure's declared interface.

### Properties
The node carries no functional properties, but its input/output interface is managed from the Node tab in the Sidebar.

Sync Sockets
Brings the node into alignment with the socket signature of whatever it's connected to. Reach for this after you rename, add, or delete sockets.

Define Signature
Flags this node as the one that defines a closure signature for sibling closure nodes to follow. The point is to keep input and output definitions consistent across related closures.

### Input Items
List of input sockets
One row shows up per socket the closure defines. Rename by double-clicking.

Add Item
Add a new input socket to the closure interface.

Remove Item
Delete the selected input socket.

Type
The data type for the selected socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types, a default value field appears and is used when the socket is unlinked.

Shape
Which data structure the input socket can carry — a Single value, Field, or Grid, for instance. How data moves through and gets evaluated across the network depends on this choice. See Socket Shape for more information.

### Output Items
List of output sockets
One row per output socket. Rename by double-clicking.

Add Item
Add a new output socket to the node.

Remove Item
Delete the selected output socket.

Type
The data type for the selected socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types, a default value field appears and is used when the socket is unlinked.

### Outputs
Whatever outputs this node exposes follow from how it's currently set up:

- When a closure is connected – every output lines up with a same-named output socket on the Closure Zone.

- When no closure is connected – you spell the outputs out by hand via the Sidebar's Output Items section.

### Behavior
At run time this node evaluates the attached closure's internal graph. Inputs are forwarded in by name, and produced values return through the matching outputs.

With no closure attached, or with the node muted, pass-through mode takes over: any inputs and outputs that match by name are simply forwarded. That fallback keeps closures optional and groups functional without one.

Evaluation runs in the local context of the node tree holding Evaluate Closure, drawing its fields, attributes, and geometry from there.

### Usage
Reach for this node to make part of a group customizable while the surrounding framework stays stable and reusable.

Picture a terrain generator using it to decide how trees spread over a landscape:

- Swap the generator group's hard-coded tree-placement logic out for an Evaluate Closure node.

- Surface that closure input on the group's interface.

- Back in the main node tree, hook up a Closure Zone that spells out the tree distribution you want.

Each time the closure evaluates, the wired-up graph executes inside the terrain generator's context and yields a tailored result.

Example: custom tree distribution using Evaluate Closure.

### Socket Syncing
Correct pairing of inputs and outputs hinges on socket names lining up between closures. When the attached Closure Zone and Evaluate Closure end up with clashing signatures, reconciliation can be handled for you by Blender.

- Differing socket layouts surface a sync icon.

- Hit that icon and the sockets get brought into line with the attached closure.

- The very first time you wire a closure up, syncing fires on its own.

- From then on, nothing touches existing sockets automatically, which keeps data safe.

### Limitations
- Across several contexts of evaluation, viewer and inspection nodes might report values that aren't accurate.

- Anything captured from outside is locked to read-only; the evaluation can't alter it.

- For now, reaching attributes or data that live beyond the evaluation context is off-limits to closures.

### Evaluate Closure

Execute a connected Closure Zone—the call site running its internal graph, returning results.

Closures enable flexible, customizable groups by passing procedural logic into another tree.
When executed, the connected closure evaluates in the current context, matching sockets by name.

Common uses:

- **Custom behavior injection:** User-defined scattering, placement, or shading inside procedural systems.
- **Logic reuse:** Inject into node groups for advanced effects.
- **Optional customization:** Provide high-level tool inputs.

### Inputs

**Closure**
The closure to run.
Expects Closure Zone connection.
Unconnected: pass-through mode (see below).

### Interface

Manual inputs sync by name to closure inputs.
When connected, sockets auto-sync to reflect the closure interface.

### Properties

No functional properties; manage interface in the Node tab of the Sidebar.

**Sync Sockets**
Align the node to connected node signatures.
Use after socket rename, add, or remove.

**Define Signature**
Mark as a closure signature source for other closure nodes.
Ensures consistent input/output.

### Input Items

**List of input sockets**
One per socket.
Double-click to rename.

**Add Item**
Insert a socket.

**Remove Item**
Delete the selected socket.

**Type**
Data type (e.g. Float, Vector, Geometry, Object, Bundle).
Value types show default value field.

**Shape**
Data structure (Single, Field, Grid).
Controls evaluation and network passage.
See Socket Shape.

### Output Items

**List of output sockets**
One per socket.
Double-click to rename.

**Add Item**
Insert a socket.

**Remove Item**
Delete the selected socket.

**Type**
Data type (e.g. Float, Vector, Geometry, Object, Bundle).
Value types show default value field.

### Outputs

Behavior varies by configuration:

- **Closure connected:** Each output mirrors a Closure Zone output by name.
- **No closure:** Manually define outputs via Output Items sidebar section.

### Behavior

When executed, evaluates the connected closure's internal graph.
Input values pass by name into the closure; results exit through corresponding outputs.

Unconnected or muted: auto pass-through by name.
Closures stay optional; groups function standalone.

Evaluation occurs in the local tree context, inheriting fields, attributes, geometry.

### Usage

Enable partial group customization while maintaining a stable framework.

Example—terrain with user-defined tree placement:

- Replace fixed placement logic with Evaluate Closure.
- Expose closure input on the group interface.
- Main tree: connect Closure Zone with desired distribution.

Whenever evaluated, the connected graph runs in the generator's context.

Tree distribution via Evaluate Closure.

### Socket Syncing

Closures match by socket name.
Mismatched signatures prompt automatic sync.

- Sync icon appears on mismatch.
- Click to align sockets.
- Auto-sync on first connection.
- Existing sockets stay protected afterward.

### Limitations

- Viewer and inspection nodes may show inaccurate values in multi-context evaluation.
- Captured values are read-only.
- Closures cannot access external attributes or context data.

### Evaluate Closure

The Evaluate Closure node runs a connected
Closure Zone. It serves as the closure's call site, running its internal node graph and handing back the resulting values.

Closures make dynamic, customizable node groups possible by letting users feed procedural logic into another node tree. When this node runs, the connected closure is evaluated in the current context, with its input and output sockets matched by name.

Where the Evaluate Closure node tends to show up:

- Opening up procedural systems to user-supplied behaviour (custom scatter, placement rules, shading logic, and so on).

- Threading extra logic into reusable groups to pull off advanced effects.

- Handing high-level node tools a set of optional knobs for customization.

### Inputs

Closure
The closure you want evaluated. Wire this input up to a
Closure Zone. Leave it empty and the node falls into pass-through mode (see below).

### Interface

You can give the node extra inputs by hand, matched by name to the connected closure's corresponding inputs. Once the closure is connected, these sockets sync automatically to reflect its declared interface.

### Properties

The Evaluate Closure node has no functional properties, but you can manage its input and output interface in the Node tab of the Sidebar.

Sync Sockets
Realigns this node so its sockets match the signature of whatever it is wired to. Trigger it after any rename, addition, or removal among the sockets.

Define Signature
Flags this node as the one defining a closure signature for sibling closure nodes to draw on, holding input and output definitions in step across the related closures.

### Input Items

List of input sockets
A row appears for each socket the closure declares; double-click one to rename it.

Add Item
Attach a fresh input socket to the closure interface.

Remove Item
Drop the input socket you have selected.

Type
Data type of the chosen socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types a default-value field turns up, taking effect whenever the socket is left unlinked.

Shape
Picks the data structure that socket conveys, such as a Single value, Field , or Grid . Its choice governs the way data gets computed and routed onward through the graph. See Socket Shape for more information.

### Output Items

List of output sockets
One row per output socket; double-click to rename.

Add Item
Attach a fresh output socket to the node.

Remove Item
Drop the output socket you have selected.

Type
Data type of the chosen socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types a default-value field turns up, taking effect whenever the socket is left unlinked.

### Outputs

What the Evaluate Closure node outputs depends on its current setup:

- With a closure connected – Each output maps to a same-named output socket of the Closure Zone.

- With no closure connected – Outputs are defined by hand through the Output Items section of the Sidebar.

### Behavior

Run it, and the node works through the inner graph of whatever closure it is wired to. Each incoming value is handed in by name, and each value the closure produces comes back out through its matching output.

When nothing is wired in, or the node is muted, Evaluate Closure simply forwards any name-matched inputs and outputs as-is. Thanks to that forwarding, a closure is optional and the surrounding group keeps functioning without one.

It all evaluates within the local scope of whatever tree the Evaluate Closure lives in, picking up the fields, attributes, and geometry on hand there.

### Usage

Reach for the Evaluate Closure node when you want part of a group to stay open to customization while the rest holds steady as a reusable framework.

Picture a terrain builder leaning on it to settle how trees scatter over the ground:

- Within the builder group, trade the locked-in tree-placement logic for an Evaluate Closure node.

- Surface that closure input out on the group's own interface.

- Over in the main tree, attach a Closure Zone that lays out the tree spread you are after.

Each time the closure evaluates, its wired-in graph fires inside the builder's own scope and yields a tailored result.

Example: custom tree distribution using Evaluate Closure .

### Socket Syncing

Closures lean on matching socket names to wire inputs and outputs up correctly. When a connected Closure Zone and Evaluate Closure node carry mismatched signatures, Blender can reconcile them automatically.

- A sync icon shows up when the socket layouts differ.

- Clicking it updates the sockets to match the connected closure.

- Automatic syncing runs the first time a closure is connected.

- After that, existing sockets are never altered automatically, to avoid data loss.

### Limitations

- Viewer and inspection nodes may report inaccurate values when closures are evaluated across several contexts.

- Any external value a closure captured is read-only; the evaluation cannot alter it.

- For now closures cannot reach attributes or data outside their evaluation context.

## Node Closures

### Node Closures

Handing custom functionality into a node group is what a closure is for. It behaves much like a function input: user-defined behavior gets evaluated inside some other node tree.

Flexibility and reuse are what closures buy you, because a slice of one node network can be injected into another. That opens the door to higher-level tools where a particular stage of a process stays customizable while the group is left untouched.

A terrain generator whose tree scattering is tailored through a closure.

### Overview
A closure is a socket type standing in for a callable node graph. It declares its own inputs and outputs, which then get evaluated inside a different node group by way of the Evaluate Closure node.

Connect a closure and its internal graph is woven into the evaluation of the node group hosting it. Procedural systems can thus stay flexible while still offering clear, customizable control points.

Picture closures as function parameters that node groups accept. Users get to define operations that run inside a controlled environment set by the parent node tree.

### Nodes
These are the nodes that create and evaluate closures:

### Socket Syncing
Closure nodes line their inputs and outputs up by socket name. Wire together two whose signatures clash, and a sync can be offered to you by Blender.

- The first connection of a node triggers syncing on its own.

- To keep from clobbering user data, no existing socket is altered automatically.

- Detect a mismatch and a button (Sync Sockets) button appears in the node header for manual synchronization.

### Example
Closures shine wherever a portion of a node group's logic ought to be left to the user. Take a terrain generator that relies on a closure to set tree placement:

- Drop an Evaluate Closure node at the point where tree instances get scattered.

- Surface a closure input on the group's interface.

- Wire up a Closure node that lays out whatever custom placement logic you like.

Evaluate the closure and the connected graph's contents run inside the terrain generator's context. The generator can therefore handle stable infrastructure (scattering, masks, attributes) while users contribute their own functional behavior.

A terrain-generator node group that drives custom tree placement with closures.

### Node Closures

Pass custom functionality into a node group—a function parameter for node graphs.
Closures inject part of a network elsewhere, enabling higher-level tools with customizable logic.

Using a closure to customize tree scattering.

### Overview

Closures: a socket type representing callable graphs.
Define inputs and outputs evaluated via Evaluate Closure in another group.

When connected, the closure's graph injects into the evaluation context.
Procedural systems stay flexible with clear control points.

Closures resemble function parameters—users define operations in a controlled parent context.

### Nodes

Creation and evaluation nodes for closures.

### Socket Syncing

Names match closure inputs to outputs.
Mismatched signatures prompt automatic sync.

- First connection syncs automatically.
- Existing sockets never change auto-sync to prevent data loss.
- A Sync Sockets button appears in the header when mismatch is detected.

### Example

User-defined logic for specific workflow parts.
Terrain with custom tree placement:

- Evaluate Closure at tree distribution point.
- Expose closure input on the group interface.
- Closure node connects with custom logic.

Connected graph executes in the terrain generator context.
Generator provides stable infrastructure (scattering, masks, attributes); user supplies behavior.

Terrain generator with custom tree placement via closures.

## Color Picker

### Color Picker

Circle HSV color picker.

A pop-up control for setting and tweaking color values is what the Color Picker provides. Edit any color property in Blender — materials, lights, brushes, interface themes — and it pops up.

Several color models and ways of interacting are on offer here to fit different workflows, and colors can be shown or edited in either linear or perceptual (display-referred) color spaces.

### Interface
Color Picker
Two color components at once are what the big color field lets you choose, with the pair depending on the picker type in use. A slider beside the field handles the remaining component (value or saturation, say).

How the picker looks and acts is governed by the type set in the Preferences; see Types below.

Value/Lightness
Brightness or lightness of the chosen color is what this vertical, gradient-backed slider sets. Scroll the Wheel for fine tweaks, or grab the handle and drag.

A handful of options sit under the color-picking widget; the first decides how component values get computed.

Linear :

Reports the component figures in the scene's linear working space — the one Blender keeps internally for compositing and rendering.

Perceptual :

Reports them instead in the color picking space (sRGB unless changed), the space that lines up with how the color widgets look and tends to feel more natural when you're choosing.

Which Color Model applies is what the next batch of options governs. Available choices hinge on the Color Picker Type.

RGB :

Builds a color straight from a blend of its Red, Green, and Blue parts.

HSV/HSL :

Builds a color through Hue, Saturation, and Value (or Lightness) instead — handy when you want tone and intensity dialed in separately.

Component Values
Beneath the picker, numeric fields carry the RGB or HSV/HSL components. The scale Blender uses runs from 0.0 to 1.0. Should the color carry an Alpha Channel, one more slider and field show up.

Hex
Displays or reads the color as a hexadecimal (hex) string. A shorthand form works too (FC0 standing in for FFCC00, say).

Note

Gamma correction for the sRGB Color Space is applied to hex values on their own. For more information, see Color Management.

Eyedropper
Picks up a color from any point within the Blender window via the Eyedropper.

Linear color space is how sampled colors are read, so display transforms like view or exposure adjustments are ignored. Pulling colors off overlays, reference images, or video preview regions can come out wrong, since those may render after color management transforms.

### Shortcuts

- Ctrl - LMB (drag): Snaps hue to 30° steps.

- Shift - LMB (drag): Slows the motion down for precise color tweaks.

- Wheel : Dials value or lightness.

- Backspace : Sends the current value back to its default.

### Types
How colors are shown and picked comes down to the Color Picker Type. Each type lays out hue, saturation, and value adjustment a little differently. Which one you use is purely a matter of taste and workflow.

A default picker type can be set in the Preferences under Interface Preferences.

| Circle HSV | Circle HSL | |
| Square (SV + H) | Square (HS + V) | Square (HV + S) |

### Notes

- Internally, Blender operates in linear color space; it converts from sRGB or any other space on its own.

- What the picker shows is the color under the present view transform, yet the value held in storage stays linear.

- To keep output steady across renders and across display hardware, see Color Management.

## Tree View

### Tree View

Example of a Tree View with expanded items.

Showing hierarchical data in a structured, expandable layout is what the Tree View handles. The difference from the List View is that items here can hold child items, which fold open or shut.

Organizing nested elements — node trees, collections, grouped settings — is the usual job for this control.

### Expand / Collapse
Any item with children carries a disclosure triangle. A LMB click on that triangle folds the item open or shut.

Open an item and its children appear, indented underneath; closed, its contents stay tucked away.

### Select
A LMB click on an item picks it.

Context can change how selection behaves, and multi-selection is permitted in some Tree Views.

### Rename
Where it's supported, renaming an item is done by double-clicking it or by pressing F2.

### Hierarchy
To signal how children relate to their parents, child items sit visually indented.

Per context, an item might allow:

- Reordering by drag-and-drop.

- Shifting items from one parent to another.

- Restructuring the nested layout.

### Context Menu
A right-click (RMB) on an item raises a context menu whose operators are tied to that particular entry.

### Filtering and Sorting
As with the List View, filtering and sorting can show up on certain Tree Views. Their presence comes down to how the particular case is implemented.

### Modification Buttons
By context, buttons for adding, removing, or reordering items may sit beside the Tree View.

Their behavior mirrors that of the List View's modification buttons.

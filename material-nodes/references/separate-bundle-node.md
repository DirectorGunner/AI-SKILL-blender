# Separate Bundle Node, Store Bundle Item Node, Closure

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Separate Bundle Node; Store Bundle Item Node; Closure.

## Separate Bundle Node

The Separate Bundle node extracts individual values from bundles, with each output corresponding to a named bundle element. It's the Combine Bundle counterpart, typically retrieving previously grouped structured data.

Bundle inputs the source bundle with grouped values. Properties (sidebar Node tab): Sync Sockets updates the node to match connected nodes; Define Signature locks the list/types for stable interfaces when publishing.

Bundle Items displays per-element entries (double-click to rename). Add Item creates a socket. Remove Item deletes one. Type selects data type (float/vector/geometry/object/bundle); value types show default-value controls.

Outputs are dynamic; each socket outputs the corresponding bundle-item value using the item's name and type.

### Separate Bundle Node

Unpacks individual values from a Bundle.
Each output corresponds to a bundle element by socket name.
Counterpart of Combine Bundle; retrieves grouped data.

### Inputs

**Bundle**
Grouped value source.

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

Dynamic output set: each socket outputs the corresponding bundle item by name and type.

### Separate Bundle Node

This node pulls individual values out of a
Bundle. Each output maps to one element in the bundle, keyed by its socket name.

It is the counterpart to the
Combine Bundle node and typically serves to fetch back structured data that was grouped together earlier.

### Inputs

Bundle
The input bundle that holds all the grouped values.

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

This node carries a dynamic set of output sockets. Each one outputs its matching bundle item's value, taking that item's name and type as set in the bundle.

## Store Bundle Item Node

The Store Bundle Item node writes values into bundles at specified paths, replacing existing items or creating new paths automatically. Commonly used for incremental bundle building, grouping heterogeneous data for network passage.

Bundle inputs the bundle to store data into. Path identifies storage location (slash-separated for nested bundles, e.g., settings/size, attributes/color). Item is the value to store; data type/structure depends on node properties.

Socket Type (properties) sets the Item-input data type. Shape (sidebar) specifies data structure (Single, Field, Grid).

Bundle outputs the resulting bundle with the stored item.

### Store Bundle Item Node

Insert a value into a bundle location via a path string.
Replace existing items at that location.
Automatically create new paths.
Incrementally construct or alter bundles.
Consolidate heterogeneous data for passage through node networks.

### Inputs

**Bundle**
Data destination.

**Path**
Item storage location via slash-separated segments.
Examples: `settings/size`, `attributes/color`.

**Item**
Value to store.
Data type and structure defined by node properties.

### Properties

**Socket Type**
Item input data type.
Determines storable data type.

**Shape**
Data structure (Single, Field, Grid).
Controls how data evaluates and stores in the bundle.
Sidebar option.

### Outputs

**Bundle**
Bundle with the stored item.

## Closure

The Closure node defines a zone encapsulating a reusable node section functioning like a custom node. It specifies inputs, outputs, and internal logic executable elsewhere via Evaluate Closure nodes. Closures enable passing user-defined procedural logic into node groups, creating modular, adaptable tools without duplicating or editing existing groups.

Closures define their own inputs acting as parameters for internal logic, created by dragging the blank input socket or adding manually. Properties (Node tab, sidebar): no functional properties of their own, but the interface is configurable. Inputs and outputs add, remove, and rename to define the closure signature.

Sync Sockets updates the node to match connected nodes after renaming/adding/removing. Define Signature marks the closure as the signature source, ensuring consistent definitions across instances.

Input Items list input sockets (double-click to rename). Add Item creates a socket. Remove Item deletes one. Type defines data type (float/vector/geometry/object/bundle); value types show defaults. Shape specifies structure support (Single, Field, Grid; see Socket Shape).

Output Items (when closure output is selected) list output sockets (double-click to rename). Add Item creates a socket. Remove Item deletes one. Type and Shape work as input items.

Closures define outputs returning values to the evaluation node tree, created by dragging sockets from within the zone to the output's blank socket or by adding manually.

Usage: Closures define reusable logic injected into other trees, commonly in procedural systems where behavior remains user-defined. Use cases include custom scattering rules (terrain generators), procedural distribution/modification (instance nodes), adjustable mappings/field evaluation/transformation logic.

External-value capture: Closures capture values from outside their zone, stored as part of the definition and available in different contexts. Captured values preserve external parameters (scale, density, color) without explicit sockets, making closures cleaner and more reusable.

Example: Terrain generators can substitute custom procedural behavior for default tree scattering by using an Evaluate Closure node in place of fixed tree-distribution code. Expose the closure parameter through the group's interface, then build a Closure Zone in the main node tree that connects to this input. Within that zone, construct the desired tree-positioning logic. Upon evaluation, the generator runs the custom placement instead of the default behavior. A Closure Zone defining procedural distribution for tree scattering demonstrates this pattern.

### Closure

A closure encapsulates reusable node logic like a function.
Define inputs, outputs, and internal behavior executable elsewhere via Evaluate Closure.

Closures inject custom procedural logic into node groups—more modular, less duplication.
Instead of editing an existing group, expose user-defined behavior while preserving structure.

An empty closure zone.

### Inputs

Closures define their own inputs as function parameters.
Create them by dragging the blank input socket or adding in node properties.
Each input is a parameter the closure receives when evaluated elsewhere.

### Properties

No functional properties; configure via the Node tab in the Sidebar.
Add, remove, and rename inputs and outputs to set the signature.

**Sync Sockets**
Align the node to connected node signatures.
Use after socket rename, add, or remove.

**Define Signature**
Mark this zone as the closure signature source for reference by other nodes.
Ensures consistent input/output across instances.

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
Value types show default value control.

**Shape**
Data structure (Single, Field, Grid).
Controls evaluation and network passage.
See Socket Shape.

### Output Items

Available with closure output zone selection.

**List of output sockets**
One per socket.
Double-click to rename.

**Add Item**
Insert a socket.

**Remove Item**
Delete the selected socket.

**Type**
Data type (e.g. Float, Vector, Geometry, Object, Bundle).
Value types show default value control.

**Shape**
Data structure (Single, Field, Grid).
Controls evaluation and network passage.
See Socket Shape.

### Outputs

Closures return values to the calling node tree.
Create them by dragging a socket from inside the zone to the blank output, or add in properties.

### Usage

Reusable logic injected elsewhere: user-defined behavior in procedural systems.

Common scenarios:

- **Custom scattering:** Define terrain distribution rules.
- **Procedural distribution:** Modify or arrange instances.
- **Flexible mappings:** Provide adjustable transformations or field logic.

### Using External Values

Closures capture values outside their zone.
A captured value stores with the closure and persists across contexts.

External value capture avoids explicit sockets, simplifying reuse across trees.

Capturing external input inside a closure.

### Example

- Terrain generator: replace fixed distribution with Evaluate Closure.
- Expose closure input on the group interface.
- Main tree: create Closure Zone, connect to that input.
- Inside zone: define desired placement logic.

When evaluated, the custom logic executes instead of defaults.

Closure Zone with custom tree distribution.

### Closure

The Closure node marks out a zone that wraps a reusable group of nodes acting like a function. It declares inputs, outputs, and internal logic that can run elsewhere in the node tree by way of an
Evaluate Closure node.

With closures, users can feed custom procedural logic into node groups, which makes tools more modular and adaptable. Rather than duplicate or edit an existing group, a closure can expose user-defined behaviour while leaving the main system's structure intact.

An empty closure zone.

### Inputs

A closure declares its own inputs, which serve as parameters for the internal node logic. To make one, drag the empty input socket onto another socket, or place sockets manually from the node's properties. Every such input names a parameter the closure will accept wherever it later runs.

### Properties

The Closure node carries no functional properties of its own; you shape its interface from the Node tab over in the Sidebar, where inputs and outputs may be added, dropped, and renamed to set the closure's signature.

Sync Sockets
Realigns this node so its sockets match the signature of whatever it is wired to. Trigger it after any rename, addition, or removal among the sockets.

Define Signature
Flags this zone as the origin of a closure signature other nodes are free to cite, holding input and output definitions in step across every instance of the closure.

### Input Items

List of input sockets
A row appears for each socket the closure declares; double-click one to rename it.

Add Item
Attach a fresh input socket to the closure.

Remove Item
Drop the input socket you have selected.

Type
Picks the data type of the chosen socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types a default-value control turns up, taking effect whenever the socket is left unlinked.

Shape
Picks the data structure that socket conveys, such as a Single value, Field , or Grid . Its choice governs the way data gets computed and routed onward through the graph. See Socket Shape for more information.

### Output Items

Available when the closure's output zone is selected.

List of output sockets
A row appears for each socket the closure output declares; double-click to rename.

Add Item
Attach a fresh output socket to the closure.

Remove Item
Drop the output socket you have selected.

Type
Picks the data type of the chosen socket (e.g. Float, Vector, Geometry, Object, Bundle). For value types a default-value control turns up, taking effect whenever the socket is left unlinked.

Shape
Picks the data structure that socket conveys, such as a Single value, Field , or Grid . Its choice governs the way data gets computed and routed onward through the graph. See Socket Shape for more information.

### Outputs

A closure declares outputs that hand values back to the node tree it runs in. To make one, drag a socket from within the zone onto the empty socket at the closure's output, or place sockets manually from the node's properties.

### Usage

Closures hold reusable logic you can inject into another node tree. They show up most in procedural systems where part of the behaviour should stay user-defined.

Common scenarios:

- Spelling out a bespoke scatter rule for some terrain builder.

- Laying out, procedurally, how instances get spread or altered.

- Supplying tunable mappings, field lookups, or transform rules.

### Using External Values

Values living outside the zone can be captured by a closure. Once captured, a value rides along as part of the closure's definition and remains on hand even where the closure later runs in another context.

This lets outside parameters — think scale, density, colour — travel with the closure without your having to wire up dedicated input sockets, which leaves closures tidier and simpler to reuse from one node tree to the next.

Capturing an external input value inside a closure.

### Example

- Within some terrain-builder group, replace whatever logic spreads the trees with an
Evaluate Closure node.

- Surface that closure input out on the group's own interface.

- Over in the main tree, build a Closure Zone and hook it to that input.

- Within the zone itself, spell out the tree-placement behaviour you are after.

Once the builder evaluates the closure, your zone's custom spread takes over from the stock behaviour.

A Closure Zone defining a custom distribution pattern for tree scattering.

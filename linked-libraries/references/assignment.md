# Assignment, Script Node, Collections, Duplicate ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Assignment; Script Node; Collections; Duplicate; Duplicate Linked; Link/Transfer Data; Link Data.

## Assignment

### Assignment

Reference

Panel :

Material ‣ Material Slots

Materials are data-blocks that can be created and then assigned to one or more objects. An object can also have multiple materials assigned in different material slots, which correspond to different parts of an object. If a smooth transition between materials is desired, then mixing shader nodes with a Mix shader is a better solution.

### Material Slots

Material slots link materials to objects and meshes. By default objects only have a single material slot, which assigns a material to the entire object. If different parts of the mesh need different materials, multiple material slots can be created.

Material slots panel.

### Slot List

The object's material slots and active material displayed in a List View.

(Add Material Slot)
Add a new material slot on the object.

(Remove Material Slot)
Remove a material slot from the object.

(Material Specials)

Copy Material
Copy material shader nodes and settings to clipboard.

Paste Material
Paste material shader nodes and settings from clipboard.

Copy Material to Selected
Copy the same material assignment from the active to other selected objects.

Remove Unused Slots
Removes all material slots not assigned to the object.

Remove All Materials
Clears all material slots from the active object. The material data-blocks remain available in the blend file but are no longer assigned.

### Data-Block

Material
The Material Data-Block Menu for the selected material slot. Here new materials can be created, or existing materials linked to the material slot.

Link
Specifies whether the material is to be linked to the object or to the object data.

The Link selector has two choices, Data and Object. These two menu choices determine whether the material is linked to the object or to the data (e.g. a mesh or curve). The Data menu item determines that this material will be linked to the mesh's data-block which is linked to the object's data-block. The Object menu item determines that the material will be linked to the object's data-block directly.

This has consequences of course. For example, different objects may share the same mesh data-block. Since this data-block defines the shape of the object any change in Edit Mode will be reflected on all of those objects. Moreover, anything linked to that mesh data-block will be shared by every object that shares that mesh. So, if the material is linked to the mesh, every object will share it.

On the other hand, if the material is linked directly to the object data-block, the objects can have different materials and still share the same mesh.

Short explanation: If connected to the object, you can have several instances of the same Object Data using different materials. If linked to mesh data, you cannot. See Data System for more information.

### Edit Mode

To assign materials to different parts of a mesh, enter Edit Mode on the mesh. Additional buttons will then appear in the material slots panel.

Material slots panel in Edit Mode.

Assign
Assign active material slot and material to the selected faces in the mesh, strokes in a Grease Pencil, and similar for other object types.

Select
Select faces assigned to the active material slot.

Deselect
Deselect faces assigned to the active material slot.

### Reusing Existing Materials

Blender is built to allow you to reuse anything , including material settings, between many objects. Instead of creating duplicate materials, you can simply reuse an existing material. There are several ways to do this using the Material's data-block menu:

Single Object – With the object selected, click the sphere located to the left of the Material name. A pop-up appears showing all the materials available in the current blend-file. To use one, just click on it.

Tip

Searching for Materials

The search field at the bottom of the material list allows you to search the names in the list. For example, by entering "wood" all existent materials are filtered so that only materials containing "wood" are displayed in the list.

Multiple Objects – In the 3D Viewport, with Ctrl - L you can quickly link all selected objects to the material (and other aspects) of the active object. Very useful if you need to set a large number of objects to the same material; just select all of them, then the object that has the desired material, and Ctrl - L links them to that "parent".

### Deleting a Material

To delete a material, select the material and click X in the Available Materials List entry.

Although the material will seem to disappear immediately, the Delete action can depend on how the material is used elsewhere.

If the material is linked to the object and there are other objects which use this material, then the material will be removed from that object (but remain on all its other objects).

If the "Fake User" button has been lit in the Available Materials list, then the material will be retained when the file is saved, even if it has no users.

Only if it has 0 "real" users, and no "Fake" user, will the material be permanently deleted. Note that it will still remain in the Materials list until the blend-file is saved, but will have disappeared when the file is reloaded.

### Multiple Materials

Normally, different colors or patterns on an object are achieved by adding textures to your materials. However, in some applications you can obtain multiple colors on an object by assigning different materials to the individual faces of the object.

To apply several materials to different faces of the same object, you use the Material Slots options in the Materials header panel.

The workflow for applying a second material to some faces of an object covered by a base material is as follows:

- In Object Mode, create a base material.

- Go into Edit Mode and Face Select (a new list will appear below the Active Material list with Assign , Select , Deselect buttons).

- Select the faces to be colored with the second material.

- In the Object Material Slots list, create a new slot or select an existing material.

- Click the Assign button, and the material will appear on the selected object faces.

## Script Node

### Script Node

Cycles Only

This node enables integration of custom shaders developed in Open Shading Language (OSL) within the Cycles rendering engine. It functions as a connection point between OSL shader implementations and Blender's node-based shading workflow.

Each Script node represents one OSL shader, with parameters derived from the code. Shaders may reside within the blend file itself or be loaded from external sources.

Technical artists and shader developers benefit from this feature when they require precise control over material behavior beyond standard node capabilities.

Note

The Script node only executes if Open Shading Language is activated.

Tip

For production pipelines, wrap script nodes in a node group and link it across blend-files. This approach simplifies future modifications, as socket changes do not require updates in every dependent file.

### Properties

Mode
Specifies how to reference OSL shader code.

Internal :

A text data-block stores the shader, with compiled bytecode embedded in the node. Useful for distributing self-contained blend files.

Script Node Update
Recompiles the text data-block and regenerates inputs/outputs as necessary.

External :

Loads a .osl file from disk, automatically compiling it into a .oso file in the same location. Alternatively, point directly to a pre-compiled .oso file. A third option references the module name within the shader search path.

The shader search path is located alongside scripts and configuration:

Linux:

`$HOME/.config/blender/5.1/shaders/`

Windows:

`C:\Users\$user\AppData\Roaming\Blender Foundation\Blender\5.1\shaders\`

macOS:

`/Users/$USER/Library/Application Support/Blender/5.1/shaders/`

## Collections

### Collections

Complex scenes often contain many objects: furniture, props, lights, backdrops, and more. Blender supports gathering objects into logical groups without imposing transform dependencies (distinct from parenting). This grouping capability aids organization and facilitates cross-file or cross-scene sharing.

### Collections Tab

Reference

Menu :

Properties ‣ Collection Properties

The Collection Properties tab supplies immediate access to settings for the selected collection.

Collection properties.

### Visibility

Selectable
Toggles selectability of collection objects in the 3D Viewport.

Useful when elements have been positioned and you prefer to avoid accidental selection while focusing on other content—for example, reference images.

Show In – Renders
Enables/disables collection visibility in renders.

#### View Layer

Each collection may be configured per View Layer for flexible rendering control. These settings permit including or excluding specific collections, masking objects, or controlling indirect contributions.

Include
Incorporates this collection in the active View Layer. Disabling hides all collection objects from renders, viewport, and the Outliner for the current view layer.

Enables alternate scene versions or isolates components for compositing work.

Holdout
Designates all collection objects as holdouts in the active view layer.

Holdout objects render as transparent regions, masking anything behind them. This is typically used in compositing to generate masks or separate foreground from background content.

See also

Holdout Shader Node

Indirect Only Cycles Only
Collection objects do not appear directly in the final image but contribute through lighting, shadows, and reflections.

Valuable for clean product shots while maintaining realistic environment lighting or reflections.

### Instancing

Instance Offset X, Y Z
Applies a spatial shift for instanced collections relative to the original object's position.

### Exporters

Each collection supports export to various file formats. These exporters are globally available (see Importing & Exporting Files), but this panel simplifies repeated exports. For instance, when iterating on glTF game assets or using Blender in studio production for USD asset creation.

Supported formats include:

- Alembic

- Universal Scene Description

- Wavefront OBJ

- Stanford PLY

- FBX

- glTF 2.0

Exporter List
A list view of all enabled exporters for the active collection. Selecting an exporter shows its options in the panel below.

(Add Exporter)
Opens a menu for selecting an exporter to add.

(Remove Exporter)
Removes the selected exporter.

Export All
Exports all configured exporters for the active collection.

Tip

Use File ‣ Export All Collections to export all exporters for all collections.

### Line Art

Usage
Determines how the collection loads into Line Art. Child objects may override this setting in Object Properties.

Include :

Generate feature lines for this collection.

Occlusion Only :

Collection objects cause occlusion to existing lines with their geometry remaining hidden.

Exclude :

Collection objects do not load into Line Art.

Intersection Only :

Collection objects generate intersection lines only with geometry remaining hidden.

No Intersection :

Include this collection without generating intersection lines.

Force Intersection :

Generate intersection lines regardless of object intersection settings.

Collection Mask
Applies custom intersection masking to collection faces. Intersection masks filter lines through the Line Art modifier. Consult Collection Masks for more information.

Mask
Intersection lines from this collection carry this mask value.

Intersection Priority
Specifies an intersection priority value for this collection. Intersection lines belong to the object with the greater priority value.

### Custom Properties

Define and manage custom properties to store data within the collection's data block. Consult the Custom Properties page for details.

### Collections Menu

Reference

Mode :

Object Mode

Menu :

Object ‣ Collection

The Collections menu supplies operations for organizing and managing scene objects. Grouping objects simplifies scene structure, controls visibility, and affects rendering behavior. Single objects may reside in multiple groups simultaneously, permitting complex scene management strategies.

Move to Collection M
Reassigns selected objects to another group. Choose from existing groups, create a new one, or shift to the Scene Collection (the top hierarchy level). Following reassignment, objects exit the former collection unless retained elsewhere.

Link to Collection Shift - M
Appends selected objects to an additional group without removing them from prior groups. Objects may simultaneously belong to numerous groups, facilitating cross-view element management. A new group is also creatable.

Create New Collection Ctrl - G
Produces a new group and enrolls selected object(s) in it. Enter the group name through the Create New Collection Adjust Last Operation panel. This group remains unlinked to the active scene.

Remove from Collection Ctrl - Alt - G
Excludes selected objects from a collection. Multi-collection members receive a choice pop-up with full-removal ability.

Remove from All Collections Shift - Ctrl - Alt - G
Excludes selected objects from all group membership.

Add Selected to Active Objects Collection Shift - Ctrl - G
Enrolls selected objects in group(s) that contain the active object. Alternatively, select "All Collections" to replicate the active object's full membership list.

### Collections

Remove Selected from Active Collection Shift - Alt - G
Removes selected objects from the active object's collections.

Hide Other Collections Ctrl - H
Hides all collections except those selected.

### Collections Panel

Reference

Mode :

Object Mode

Panel :

Object tab ‣ Collections

Collections panel.

All collections an object belongs to are listed in the Object Properties Collections panel.

Add to Collection
Adds the selected object to a collection. A pop-up allows specifying the target collection.

(Add to Collection)
Generates a new collection and adds the selected object to it.

Name
Click in the name field to rename a collection.

(Remove Collection)
Removes the object from the specified collection.

(Collection Specials)
Unlink Collection, Select Objects in Collection, Set Offset from Cursor

X, Y, Z
Applies a spatial offset for instanced collections relative to the original object's position.

See also

Appending or Linking Collections

To import a collection from another blend-file, consult this documentation. In summary: File ‣ Link/Append Link, select a blend-file, then the collection.

Tip

Selecting Collections

Collections may be selected through Select Grouped.

## Duplicate

### Duplicate

Reference

Mode :

Edit and Object Modes

Menu :

Object ‣ Duplicate Objects

Shortcut :

Shift - D

Creates a visually-matching copy of the selected object(s). The copy appears at the original location, and you enter move mode automatically. Refer to the examples below.

This copy is a new object sharing some data-blocks with the original (by default, materials, textures, and F-Curves) while copying others (such as the mesh). This duplication variant is sometimes termed "shallow link," as data-blocks are partially shared.

Tip

The Preferences lets you choose which data-block types are linked or copied during duplication.

### Examples

The Cube object was duplicated.

The Cube was duplicated with Shift - D. Both cubes have separate meshes with distinct names: Cube and Cube.001.

- When the original left cube is edited, the duplicated right cube stays unchanged. Mesh data is copied, not linked.

- When one cube is edited in Object Mode, the other remains unchanged. The new object's properties and data-block are copies, not linked.

- Upon duplication, the copy inherited the original's material. Material properties are linked, not copied.

See above to create separate copies of normally-linked data-blocks.

## Duplicate Linked

### Duplicate Linked

Reference

Mode :

Object Mode

Menu :

Object ‣ Duplicate Linked

Shortcut :

Alt - D

You may create a Linked Duplicate instead of a simple Duplicate, called a deep link. A new object is created with all data linked to the source object. If you edit one linked object in Edit Mode, all linked copies update. Transform properties (object data-blocks) remain copied, not linked, so rotation, scaling, and movement are independent. Consult the Examples section for discussion.

If the source object was animated, the duplicate links to the same Action. Though each object has independent transform properties, the animation system assigns them the same values. If this is unwanted, create a single-user copy of the action in the Action or NLA Editor.

Linked
In the Duplicate Objects Adjust Last Operation panel, the Linked checkbox is checked, unlike with Duplicate.

Hint

To alter a linked duplicate independently of the source, manually transform the object to a "single-user" copy by pressing LMB in the Object Data panel of the Properties. (See Data-Block Menu.)

See also

Make Single User for decoupling data-blocks.

### Examples

The Cube object was linked duplicated.

The Cube was linked duplicated with Alt - D. Though both cubes are separate objects with distinct names (Cube and Cube.001), the single mesh named Cube is shared.

- When you edit the mesh in Edit Mode on one object, the other cube changes identically. Mesh data is linked, not copied.

- Conversely, rotating or scaling one cube in Object Mode leaves the other unchanged. Transform properties are copied, not linked.

- As in the prior example, the newly created cube inherited the source's material. Material properties are linked, not copied.

A typical table has a top and four legs. Design one leg, then create linked duplicates three times for the remaining legs. Later modifications to the mesh preserve all legs. Linked duplicates apply similarly to drinking glass sets, vehicle wheels, or any repetitive or symmetrical arrangement.

See also

Linked Library Duplication

Linked Libraries also use duplication. Any object or data-block from other blend-files can be reused in the current file.

Hint

To make transform properties (i.e. object data-blocks) "linked," consult the parenting documentation.

## Link/Transfer Data

### Link/Transfer Data

Reference

Mode :

Object Mode

Menu :

Object ‣ Link/Transfer Data

Shortcut :

Ctrl - L

## Link Data

### Link Data

Reference

Mode :

Object Mode

Menu :

Object ‣ Link/Transfer Data

Shortcut :

Ctrl - L

Performs multiple assignments: including objects in a scene, giving objects matching data or modifiers, and so on.

When two objects link to the same data, modifications to one appear in the other. If you prefer each object to have separate data, use Making Single User to decouple them.

Link Objects to Scene
Incorporates the selected objects into the specified scene. Objects can exist in multiple scenes simultaneously and show the same position/animation across all.

Link Object Data
Swaps the object data of the selected objects with that of the active object.

Link Materials
Swaps the materials of the selected objects with those of the active object.

Link Animation Data
Swaps the actions and tracks of the selected objects with those of the active object.

Link Collections
Transfers the selected objects to the same collections as the active object.

Link Instance Collection
Swaps the instance collection of the selected objects with that of the active object.

Link Fonts to Text
Swaps the font of the selected text objects with that of the active text object.

Copy Modifiers
Swaps the modifiers of the selected objects with those of the active object.

Copy Constraints
Swaps the constraints of the selected objects with those of the active object.

Copy Grease Pencil Effects
Swaps the visual effects of the selected Grease Pencil objects with those of the active object.

Copy UV Maps
Swaps the active UV map of each selected mesh object with the active UV map of the active object. If a selected object lacks UV maps, one is created.

All objects must have matching geometry and face ordering. Use Sort Elements to ensure the latter; this operator is most applicable when the destination is a modified copy of the source. Try Transfer Mesh Data for other scenarios.

Transfer Mesh Data
See Transfer Mesh Data.

Transfer Mesh Data Layout
See Transfer Mesh Data Layout.

Link Receivers to Emitter
Incorporates the selected objects into the Light Linking collection of the active light object.

Link Blockers to Emitter
Incorporates the selected objects into the Shadow Linking collection of the active light object.

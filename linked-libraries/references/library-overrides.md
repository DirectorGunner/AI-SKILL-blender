# Library Overrides, Link Append

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Library Overrides; Link & Append.

## Library Overrides

Library Overrides is a system that lets you edit linked data while keeping it synced to the original library data. Most linked data-block types can be overridden, and an override's properties can then be edited; when the library data changes, the override's unmodified properties update to match. Note: the old proxy system was deprecated in Blender 3.0 and fully removed in Blender 3.2 — proxies convert to library overrides automatically on load, but results on complex characters aren't guaranteed and may need manual fixing.

Library overrides support:
- Several independent overrides of the same linked data (the same character several times in one scene, say).
- Adding new modifiers and constraints anywhere in the stack.
- Recursive chaining of overrides (linking and overriding overrides from another library file, and so on).
Note: there are known issues still to address; see the project's main task for details.
Warning: while override data usually survives losing the linked reference data (if the library file goes missing or moves), there are exceptions — chiefly posed (but not animated) armature objects when their Armature obdata itself isn't overridden, because an armature object's Pose bones are fully linked to its Armature obdata's bones, so if that obdata vanishes the pose bones are gone for good.
Note — Proper Collections Layout Matters: for overrides to work well, it's much better if every collection the character needs is a child of the root (linked and instantiated) one, giving a clear hierarchy; otherwise some data may not auto-override properly and other operations grow less reliable.

Override Hierarchies — hierarchy is a key idea for working with library overrides. In Blender a real-world asset (a character, prop, set, etc.) is almost never a single data-block but a group of data-blocks with dependencies — a character typically has an armature object, several geometry objects, rig-controller objects, the object data for all of them, materials, textures, and so on. Those relationships make a tree whose root data-block pulls in every dependency recursively; with library overrides, the hierarchy's root is usually also the data-block linked directly when importing the asset (commonly a collection). Think of this hierarchy as a kind of super meta-data-block: it's vital when several overrides of the same linked data exist, since it ties each data-block to one override unambiguously for processes that touch the whole hierarchy (resyncing overrides with their linked data, say), and it also lets relationships be shared across hierarchies, like a parenting relationship between two different overrides of one character.

Animation & Overrides — because of how animation data currently works in Blender, what's editable in an override's animation varies a lot with whether animation data already existed in the linked reference data-block (a data-block gains animation data once it's animated by keyframes or drivers). In general, an override can do far more with its animation data when its linked reference has none.
Keyframes (a.k.a. F-Curves) — keyframed animation lives in another data-block (an Action), so you can assign a purely local Action that replaces the one linked from the library — though this wholly replaces the linked keyframed animation rather than overriding it. Overridden Action data-blocks allow only very limited editing: an existing F-Curve can be muted, but its keyframes can't be edited and no new F-Curve can be added.
Drivers — when the linked reference data already has animation data, its overrides can edit existing drivers only in limited ways — you could change an existing driver's target, but not add new drivers or new targets to an existing one. If the linked reference has no animation data, its overrides create one when drivers are defined, and the drivers can then be fully edited, added, or removed, just like on purely local data-blocks.
NLA — the NLA editor data also belongs to a data-block's animation data, but it allows a greater degree of override editing, including shifting or resizing the linked data's existing strips and adding fresh local ones.

Resyncing Overrides — the relationships among linked data-blocks can change, leaving overrides outdated, at which point they need resyncing to match the hierarchy's new structure. Overrides resync automatically when needed on file open, though you may sometimes need to resync by hand; see Troubleshoot an Override Hierarchy. Tip: Blender can also resync library overrides coming from external libraries that get linked into a working file, but that's a costly process redone in full every time the working file loads, since Blender can't edit the external library directly — so anyone linking overrides (or making recursive ones) should keep their library files updated regularly to avoid that load-time overhead (opening and saving those library files is usually enough). Tip: auto resyncing can be switched off in the Experimental Preferences.

Non-Editable Overrides — for technical reasons (the way relationships between data-blocks are stored), Blender has to create overrides of many data-blocks even when only one or two actually need editing; to cut the clutter and the risk of unwanted edits, most of these are now marked non-editable by default, which you can change once the override exists.

Make an Override — Reference: Editor: 3D Viewport, Outliner, Properties; Mode: Object Mode; Menu: 3D Viewport ‣ Header ‣ Object ‣ Library Override ‣ Make, Outliner ‣ Context Menu ‣ Library Override ‣ Make, ID Widget ‣ Context Menu ‣ Library Override ‣ Make; Shortcut: Shift-LMB on an ID Widget's 'linked'/'overridden' button. Creates overrides from the selected data-blocks. Blender automatically makes overrides for every required data-block so that valid override hierarchies result, and only overrides created from selected items become user-editable. Warning: support for creating library overrides from the ID Widget (mainly in the Properties editor) is limited — common cases should work, especially with Objects, meshes, etc., but much is still unimplemented.
Selected Items — depending on where you create the override, you have a few ways to mark items for overriding and editing. Note: this also covers the other common operations (Reset and Clear); the Troubleshoot advanced operations, only in the Outliner, always act on a whole override hierarchy.
3DView — the selected objects count as selected. When a selected object is a local Empty instancing a linked collection: the Empty is removed; its linked collection is overridden and that override is instanced in the same collection of the current View Layer; and if the collection holds Armature objects they become user-editable, otherwise no created override is user-editable.
Outliner — the operation can act on the selected items only, their content only, or both. Tip: Selected & Content is an easy way to get every newly created override editable at once.
ID Widget — only the linked data-block in the ID Widget counts as selected and is made editable once overridden.
Make Editable — that same operation also makes existing overrides editable after they've been created or cleared.

Reset an Override — Reference: Editor: 3D Viewport, Outliner, Properties; Mode: Object Mode; Menu: 3D Viewport ‣ Header ‣ Object ‣ Library Override ‣ Reset, Outliner ‣ Context Menu ‣ Library Override ‣ Reset, ID Widget ‣ Context Menu ‣ Library Override ‣ Reset. Reverts the selected overrides to the linked reference data's original values; unlike Clear, they stay fully editable and are never deleted.

Clear an Override — Reference: Editor: 3D Viewport, Outliner, Properties; Mode: Object Mode; Menu: 3D Viewport ‣ Header ‣ Object ‣ Library Override ‣ Clear, Outliner ‣ Context Menu ‣ Library Override ‣ Clear, ID Widget ‣ Context Menu ‣ Library Override ‣ Clear; Shortcut: Shift-LMB on an ID Widget's 'overridden' button. Reverts the chosen overrides to their starting values and, where doing so won't break the existing hierarchy, deletes them and swaps in their linked reference data; otherwise it keeps them but marks them non-editable.

Edit an Override — an override is edited much like a regular local data-block: you can run operators on it, edit its properties from various editors, and so on. There are limits, though — most notably Edit Mode isn't allowed for overrides. Usually, as soon as you edit a property, its teal-blue outline/background marks it as overridden. Overrides can be animated too, where animated properties simply replace/supersede the overrides; note that existing animation can't be overridden or edited — you'll need a new action instead. You can set or remove an override by hand from the relevant property's context menu, and a non-editable override must be made editable first.
Add Overrides — Reference: Editor: Any; Mode: Object Mode; Property: Context Menu ‣ Add Override(s). Flags a property for overriding in the local blend file; for array properties, all elements are overridden.
Add Single Override — Reference: Editor: Any; Mode: Object Mode; Property: Context Menu ‣ Add Single Override. Flags a property for overriding in the local blend file; for array properties, only the selected element is.
Remove Overrides — Reference: Editor: Any; Mode: Object Mode; Property: Context Menu ‣ Remove Override(s). Drops the property from the overrides, using the linked-in data-block's value instead; for array properties, every element is removed from the override.
Remove Single Override — Reference: Editor: Any; Mode: Object Mode; Property: Context Menu ‣ Remove Single Override. Drops the property from the overrides, using the linked-in data-block's value instead; for array properties, only the selected elements are removed.

Troubleshoot an Override Hierarchy — Reference: Editor: Outliner; Mode: Object Mode; Outliner: Context Menu ‣ Library Override ‣ Troubleshoot. These operations live only in the Outliner context menu and can help fix a broken override hierarchy.
Resync — Reference: Editor: Outliner; Mode: Object Mode; Outliner: Context Menu ‣ Library Override ‣ Troubleshoot ‣ Resync. The linked data's hierarchy (the relationships among linked data-blocks) can change, and overrides then need resyncing to match it; this operator resyncs the override to the library's new hierarchy. Warning: while resyncing, edited overrides may be deleted if they changed in the original library — if so, a warning reports how many were deleted, and you can undo the resync before saving if that's unwanted. Note — This Process is Automatic: it usually happens on its own when Blender detects it's needed at file load, unless switched off in the Experimental Preferences.
Resync Enforce — Reference: Editor: Outliner; Mode:

Object Mode; Outliner: Context Menu ‣ Library Override ‣ Troubleshoot ‣ Resync Enforce. In some cases — especially older blend-files saved with "broken" (non-hierarchy-matching) overrides — a plain resync can't rebuild the override properly (some objects might go missing). To fix that, this operator rebuilds the local override from its linked reference, along with its dependency hierarchy, making that hierarchy match the linked data (that is, disregarding existing overrides on data-block properties). It's like a regular resync but more forceful and aggressive, at the risk of losing some overrides on ID-pointer properties.
Delete — Reference: Editor: Outliner; Mode: Object Mode; Outliner: Context Menu ‣ Library Override ‣ Troubleshoot ‣ Delete. Removes the whole library-override hierarchy and swaps every one of those override data-blocks for their original linked data-blocks, fully reverting the Make operation.

## Link & Append

These functions let you reuse objects, materials, and other data-blocks from another blend-file, so you can build libraries of common content and share them across many referencing files. Tip: instead of the menu, you can also Link/Append a blend-file by dragging and dropping it into the Blender window. Note: data coming out of much newer blend-files can't be Linked or Appended.

Link — Reference: Editor: Topbar; Mode: All modes except Edit Mode; Menu: File ‣ Link…. Link makes a reference to data in a source file, so changes there show up in the current file the next time it's reloaded; in the File Browser, head to the external source blend-file and choose the data-blocks to reuse. Linked data-blocks carry a chain icon in the Outliner and are also listed in its Blender File Display Mode along with their source blend-file's path. Linked data-blocks start out non-editable — including a linked object's location/rotation/scale, locked to its transform in the source file — but there are ways around that:
- If you link a collection with Instance Collections on, or some object data with Instance Object Data on, the collection/object data is referenced through an object made inside the current blend-file, which you can transform. (That new object appears at the 3D Cursor.)
- You can also do some editing/animating on linked (normally locked) data-blocks via Library Overrides.
Warning: since it isn't editable, linked data can't be protected with the Fake User option; adding a custom property that points at an otherwise-unused linked data-block (a Text block, say) is a solid way to hold a reference to it through saves and reloads.
Options — these sit in the File Browser's right-hand panel.
Relative Path — references the external blend-file by a relative path rather than an absolute one.
Select — selects the newly added objects.
Active Collection — on, objects and collections go into the active view layer's active collection; off, they go into a new "Linked Data" collection in the active view layer.
Instance Collections — on, each linked collection is added to the scene as an instance collection (a single object standing in for the whole collection); add more with Add ‣ Collection Instance, or swap an instance for the collection's contents with Make Instances Real. Off, the collections are added as-is so you can see their contents in the Outliner and create Library Overrides.
Instance Object Data — on, an object is made for each directly linked object data; off, no object is made and the object data stays invisible in the scene until you make one yourself (by dragging the object data from the Outliner into the 3D Viewport, say).

Append — Reference: Editor: Topbar; Mode: All modes except Edit Mode; Menu: File ‣ Append…. Append copies data-blocks into your blend-file with no reference back to the originals, so you can edit your local copy freely while changes in the external source won't show up here. In the File Browser, open the source blend-file and tick the data-blocks you'd like to copy in. Note: appending data you already have linked adds the objects/collections to the scene but keeps them linked (and uneditable), so existing relationships with linked data stay intact.
Options — these sit in the File Browser's right-hand panel.
Select — selects the newly added objects.
Active Collection — on, objects and collections go into the active view layer's active collection; off, they go into a new "Appended Data" collection in the active view layer.
Instance Collections — on, each appended collection is added to the scene as an instance collection (a single object standing in for the whole collection); add more with Add ‣ Collection Instance, or swap an instance for the collection's contents with Make Instances Real. Off, the collections are added as-is so you can see their contents in the Outliner.
Instance Object Data — on, an object is made for each directly appended object data; off, no object is made and the object data stays invisible until you make one yourself (by dragging the object data from the Outliner into the 3D Viewport, say).
Fake User — marks the appended data-blocks as Protected.
Localize All — also copies all indirectly linked data rather than keeping the links.

Reload Library — Reference: Editor: Outliner; Menu: Context menu ‣ Reload. With the Outliner in Blender File Display Mode, right-click a linked blend-file and choose Reload to bring the current blend-file up to date with the newest version of the linked data-blocks at once, without reopening the file.

Relocate Library — Reference: Editor: Outliner; Menu: Context menu ‣ Relocate. With the Outliner in Blender File Display Mode, right-clicking a library (a linked blend-file) offers Relocate, which swaps it for a different file — handy either to fix a broken linked library (the file was moved or renamed) or to jump to a variant of the same data kept in another file.
Broken Libraries — if Blender can't find a library while loading a blend-file, it makes placeholder data-blocks in place of the missing linked ones, so references to the missing data aren't lost and relocating the missing library can restore the lost data automatically.

Relocate Linked ID — Reference: Editor: Outliner; Menu: Context menu ‣ ID Data ‣ Relocate. Right-clicking a linked ID offers Relocate in the ID Data sub-menu, which swaps a directly linked ID for another, from the same library or a different one — handy either to fix a broken linked data-block (the ID was renamed) or to jump to a variant of the same data.

Note: this only works on data-blocks that are directly linked and that nothing else linked depends on.

Make Local — Reference: Editor: 3D Viewport; Mode: Object Mode; Menu: Object ‣ Relations ‣ Make Local…. Also Reference: Editor: Outliner; Menu: Context menu ‣ ID Data ‣ Make Local. Turns the selected (or all) external objects into local copies in the current blend-file; links to the original library file are lost, but the data-blocks turn fully editable, just like ones created directly in the current file.
Options — the Outliner context-menu version has no options and touches only the selected data-blocks. The 3D Viewport version touches only the selected objects but can also make their dependencies local:
Type — whether to localize just the objects, or their data and materials too.

Known Limitations — for the most part linking works as you'd expect, but a few limits are worth knowing.
Circular Dependencies — dependencies shouldn't run both ways; trying to link or append data that links back to the current file will likely leave missing links.
Scene-Level Settings — scene-level settings like the Rigid Body World aren't copied when linking objects; instead, you can link the whole scene and use it as a Background Scene.
Compression & Memory Use — pointing at compressed blend-files can eat a lot of memory, since they have to load in full even when you only link/append a small part; once the data-blocks are loaded, though, memory use is the same.

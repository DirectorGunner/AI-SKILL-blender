# File Browser, Editing Outliner Data, Interface, Usage ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: File Browser; Editing Outliner Data; Interface; Usage; Add-ons; Developer Tools.

## File Browser

The File Browser turns up in every file-related operation, including:
Opening and saving blend-files.
Browsing the contents of other blend-files while appending or linking data-blocks (see Linked Libraries).
Importing from, or exporting to, other file formats.
Updating the locations of media imported earlier (images, videos, fonts…).

Most often you meet it through modal operators — opening or saving a blend-file, say — where it pops up in its own window, waits for your file pick, and closes again. It can also run as an ordinary, always-visible editor; the built-in Video Editing workspace uses it that way, letting you drag media from the browser straight into the 3D Viewport or the Video Sequencer and skip some overhead.

Interface — Main Region: lists files, folders, or blend-file contents, and hovering an item shows a tooltip with extra detail.
Previews — in Thumbnail display mode the File Browser previews many kinds of content: image and video formats, fonts, blend-files, and internal data-blocks. Data-block previews have to be generated first (see Blend-Files Previews).

Directory Region — above the file list sits a textbox with the current folder path plus navigation buttons.
Previous Folder (Backspace, Alt-Left, Mouse4) — steps back through navigation history.
Next Folder (Shift-Backspace, Alt-Right, Mouse5) — steps forward through navigation history.
Parent Directory (P, Alt-Up) — moves up to the parent directory.
Refresh File List (R, NumpadPeriod) — refreshes the current folder.
Create New Directory (I) — makes a new directory inside the current one.
Directory (Ctrl-L) — the current folder path; Tab auto-completes an existing path, and typing a path that doesn't exist prompts you to create it.
Search (Ctrl-F) — filters items by name. The * wildcard matches anything, so bl*er catches both blender and blogger; there's always an implicit wildcard at both ends of the search text, so blender also matches test_blender_file.blend. You can also filter by a specific extension here (e.g. .png lists every PNG).
Display Mode — controls how files appear. Vertical List shows files and folders in a vertical list; Horizontal List shows them in a horizontal one; Thumbnails shows previews.

Display Settings:
Size — the thumbnail size.
Recursions — how many directory levels to show at once, flattened. None lists only the current directory's contents; Blend File lists a whole blend-file's contents (available only when linking or appending data-blocks); One Level, Two Levels, and Three Levels list subdirectory contents to one, two, or three levels of recursion.
Hint: flattening several directory levels is handy for, say, seeing your entire texture collection even when you've tidied it into a set of folders to avoid hundreds of files in one place. In the Append/Link case, showing a whole blend-file's contents lets you link several data-block types in one go.
Warning: the more levels shown at once, the longer the listing takes.
Sort By — orders items by one of four methods: Name (alphabetical), Extension (by extension/type), Modified Date (by modification time), or Size (by file size).

Filter Settings — the funnel toggle turns filtering on or off, and the dropdown beside it holds the options.
File Types — filters by category, such as folders, blend-files, images, etc.
Blender IDs — when appending or linking, also filters by data-block category, such as scenes, animations, materials, etc.
Show Hidden (H) — reveals hidden files (those starting with a .).

Execution Region — these controls live at the editor's bottom.
File Name — a text field for the file name and extension; it turns red to warn of overwriting an existing file, and Tab auto-completes to names already in the directory.
/ (Increment Number in Filename) — adds or bumps, or removes or lowers, a trailing number in the file name (used, e.g., to keep several versions of a file).
Cancel (Esc) — shuts the File Browser and cancels the operation.
Confirm (Return) — accepts the current directory and file name; double-clicking a file or data-block in the main region works too.

Quick Access Region — the left-hand region holds a few panels for jumping to certain directories in one click. The System and Recent panels can be hidden via the Save & Load preferences.
Bookmarks — your own list of frequently used folders; the buttons to the right of the list add, remove, or reorder entries.
System — common directories like the home directory on Linux or the "Documents" folder on Windows.
Volumes — drives and network mounts.
Recent — folders you've visited lately; the button to the right reveals Clear Recent Items for wiping the list.

Operator Options Region — the right-hand region shows the calling operator's options. Beyond the common actions below, many import/export add-ons surface their own options here.
Open, Save, Save As Blender File — see Opening & Saving.
Open, Replace, Save As Image — see Supported Graphics Formats.
Link/Append from Library — see Linked libraries.
And the common option: Relative Path — see Relative Paths.

Header Region — the header carries just two menus, one with the standard editor View controls and one listing a few Selecting operators for discoverability. Neither shows when the browser is in a modal window.

Navigating:
Entering a Directory (Return) — double-click a directory to go into it.
Parent Directory (P) — moves you up one level.

File Drop — you can also drag a file or folder out of your OS file manager and drop it onto Blender's File Browser, which then jumps to that item and selects it.

Selecting:
Select — click LMB to pick a single item; add Ctrl to add or remove it from the selection, or Shift to grab a range.
Dragging — dragging with LMB begins a box selection.
Note: you can always select several entries, with the last-picked one treated as active; if the calling operation wants a single path (the main blend-file Open, say), it takes that active item's path and ignores the rest.

Arrow Keys — you can also select or deselect by "walking" through files with the arrow keys: press an arrow to select the next/previous file and deselect the rest; hold Shift to keep (and extend) the current selection; hold Shift-Ctrl to invert the selection as you pass over it. With nothing selected, arrow navigation grabs the first or last file in the directory, depending on direction.

Editing — the file list's context menu offers these.
External — has the operating system act on the file or directory; the choices below may not all exist on every OS: Open (open the file), Open Folder (open the folder), Edit (edit the file), New (create a new file of this type), Find File (search for files of this type), Show (show this file), Play (play this file), Browse (browse this file), Preview (preview this file), Print (print this file), Install (install this file), Run As User (run as a specific user), Properties (show OS Properties for this item), Find in Folder (search for items in this folder), and Command Prompt Here (open a command prompt here).
Delete (Delete, X) — sends the selected files or directories to the OS "trash". On Linux, deleting directories needs KDE or GNOME.
Rename (F2) — changes the name of the selected file or directory.

## Editing Outliner Data

Context Menu — open it for a data-block with RMB on its icon or name; the options shown depend on the selected data-block type(s):
Copy/Paste — copies or pastes the selected data-blocks.
Delete (X, Delete) — wipes out every use of the selected data-blocks: objects leave all scenes, materials leave all meshes, and so on. Note: pressing these shortcuts over the 3D Viewport instead Unlinks the selected objects, removing them only from the current scene.
Delete Hierarchy — as above but also hits child collections/objects; run on a collection, child objects that also belong to another collection survive.
Select — adds the Outliner-selected items to the 3D Viewport selection, useful only when Sync Selection is off (with it on, the default, the Outliner selection syncs to the viewport automatically).
Select Hierarchy — adds the selected items' children to the Outliner selection; with Sync Selection on, also to the viewport selection.
Deselect — drops the Outliner-selected items from the 3D Viewport selection.
Unlink — removes the data-block's current use while keeping others: objects leave only the current scene, materials only the current mesh, and so on.

Collections — collections organize a scene's content and can hold objects as well as other collections.
New — creates a collection.
Duplicate Collections — makes a recursive copy of the collection, child collections, objects, and object data included.
Duplicate Linked — recursively copies the collection along with child collections and objects, but shares the object data.
Instance to Scene — creates a new collection instance.
Visibility — governs whether the collection appears in the 3D Viewport and in the final render.
  Isolate — shows the selected collection (plus its child and parent collections) and hides the rest.
  Show/Hide — flips the Hide in Viewports setting for the chosen collections.
  Show/Hide Inside — flips Hide in Viewports for the chosen collections and every child.
  Enable/Disable in Viewports — flips the Disable in Viewports setting for them.
  Enable/Disable in Renders — flips the Disable in Renders setting for them.
View Layer — governs the collection's interactions with the View Layer.
  Disable from View Layer — drops the collection from the active view layer; objects only in it won't render for that layer, handy for leaving out some object's influence on a particular view layer.
  Enable in View Layer — adds the collection to the active view layer so its objects render there.
  Set Holdout — turns on the Holdout property for the selected collections, so their objects cut a holdout/mask in the active view layer.
  Clear Holdout — turns that property off.
  Set Indirect Only (Cycles Only) — turns on Indirect Only for the selected collections, so their objects contribute to the image only indirectly, via shadows and reflections.
  Clear Indirect Only (Cycles Only) — turns that property off.
  Set Color Tag — applies or removes a color tag on the selected collection.

ID Data:
Unlink — removes the data-block's current use while keeping others (e.g. dropping a material from just the current mesh).
Make Local — converts an externally linked data-block into a local copy.
Make Single User — currently non-functional; use the Data-Block Menu's User Count button instead.
Delete — deletes the selected data-block.
Remap Users — points every use of the selected data-block at a different one — handy to swap one material for another everywhere, say.
Copy/Paste — copies or pastes selected data-blocks.
Add/Clear Fake User — adds or removes a fake user, which keeps unused data-blocks from being auto-deleted when you save and reload the blend-file.
Rename (F2) — renames the selected data-block.
Select Linked — selects the data-blocks that use the current one (e.g. every object using the selected material); see Select Linked.

Mark as Asset — see Creating an Asset.
Clear Asset — see Removing Assets.
Clear Asset (Set Fake User) — see Removing Assets.
Library Override — see Library Overrides.

View:
Show Active (Period) — centers the tree on the active item.
Expand/Collapse All (Shift-A) — expands or collapses every item in the tree.
Show Object Hierarchy (Home) — expands objects that have children and collapses those that don't.
Show/Hide One Level (NumpadPlus / NumpadMinus) — expands or collapses one level down/up the tree across all items.

## Interface

Header — Display Mode: this dropdown sets what the Outliner shows.
Scenes — the view layers, collections, and objects across every scene.
View Layer — the collections and objects in the current scene's current view layer.
Video Sequencer — the images and videos used in the Video Sequencer.
Blender File — all data in the current blend-file; a shield icon on the right shows the user count, and clicking it adds or removes a fake user.
Data API — every data-block in the file plus any properties it has.
Library Overrides — the library overrides, split into two view modes: Properties (the data-blocks with overridden properties, listed by type and expandable to view and change them) and Hierarchies (the overridden data-blocks in a tree showing their hierarchy, including parents overridden implicitly — override a material, say, and the tree shows object > mesh > material — with a right-hand column of icons toggling each override's editability).
Unused Data — the data-blocks that are unused or have only a fake user; the shield icon on the right adds/removes a fake user. Unused data-blocks auto-delete on save and reload, or you can remove them now with Purge in the header.

Search — the textbox filters the tree by a typed substring; focus it with Ctrl-F or clear it with Alt-F.

Filter — the header's funnel icon gives finer control over what's shown, with some options unavailable depending on the Display Mode.
Restriction Toggles — sets which Restriction Toggles are visible.
Sort Alphabetically — sorts the entries alphabetically.
Sync Selection — whether to sync the Outliner selection to and from the 3D Viewport and Video Sequencer.
Show Mode Column — shows the column for toggling object interaction mode.
Search — Exact Match (show only items whose name fully matches, not merely contains, the search text) and Case Sensitive (weigh upper/lower case when comparing).
Filter:
  All View Layers — shows every view layer in the scene rather than just the active one; with the Objects filter off, this gives a compact overview of all collections against the view layers.
  Collections — shows the collections in the scene hierarchy; off, only the collections themselves hide while their objects stay visible.
  Objects — shows the objects in the scene hierarchy; off, you get a collections-only overview.
  Object State — lists objects by state or restriction, invertible with the Invert toggle: All (every object), Visible (only those visible in the 3D Viewport, accounting for both Hide in Viewports and Disable in Viewports), Selected (only the currently selected ones), Active (only the active object, usually the last selected), Selectable (only those that can be selected in the viewport).
  Object Contents — lists relevant materials, modifiers, mesh data, and so on as each object's children.
  Object Children — shows child objects as child nodes; off, they appear as siblings instead (the exception: a child in a different collection from its parent isn't shown under the parent's collection at all).
  Meshes/Lights/… — filters objects out by type.
  System Overrides — shows the data-block properties defined or controlled automatically (to point data-blocks at overridden data rather than the original, say); available only in the Library Overrides Display Mode.

Miscellaneous — some header options appear only when they fit the active Display Mode.
New Collection (View Layer) — adds a new collection inside the selected one.
Filter by Type (Blender File, Unused Data) — restricts which data-block types the Outliner shows.
Keying Sets (Data API) — adds/removes the selected property to/from the active Keying Set.
Drivers — adds/removes Drivers on the selected item.
Purge (Orphan Data) (Unused Data) — opens a dialog to remove unused data-blocks from the current blend-file or any Linked Data (can't be undone).
  Local Data-Blocks — clears unused data-blocks out of the current blend-file.
  Linked Data-Blocks — clears unused data-blocks out of Linked Data.
  Recursive Delete — removes data-blocks used only by unused data-blocks, leaving no orphans behind.

Main Region — Object Interaction Mode: when a selected object sits in some interaction mode besides the default Object Mode, the Outliner draws an icon for it on the left. When the active object carries such an icon, a dot also appears next to objects of the same type; click a dot to switch to another object while staying in the mode, or Ctrl-LMB a dot (where Multi-Object Editing is supported) to add an object to the mode. Click the active object's mode icon to send it (and, under Multi-Object Editing, the others) back to Object Mode, or Ctrl-LMB the mode icon on a selected (but not active) object to return only that one to Object Mode.

Restriction Toggles — the Outliner's right side carries a row of toggle icons for every collection, object, bone, modifier, and constraint, used to make the item invisible, unselectable, and so on.

Note: only a few icons show by default; use the Filter pop-over to reveal more.
Shift-LMB an icon to toggle it for the item and all its children. Ctrl-LMB a collection's icon to enable it for that collection (and its parent/child collections) while disabling it for the rest; click again to re-enable the rest.

Exclude from View Layer (Collections) — toggles whether the collection is part of the current View Layer; when excluded, its contents vanish from the 3D Viewport, the render, and the Outliner (see Include).
Disable Selection — controls whether you can select the object or collection in the 3D Viewport, handy for, say, reference images you only want to display and never select or move.
Hide in Viewports — toggles the object's or collection's visibility in the 3D Viewport alone, for the current view layer, leaving the render untouched. Instead of this icon you can press H with the pointer over the 3D Viewport to hide what's selected, or Alt-H to bring everything back. It applies only within the current blend-file: Link or Append it elsewhere and everything is visible there. Objects hidden this way stay in the view layer, so they're still evaluated and still affect playback performance.
  See also: collections can be hidden per 3D Viewport (see Local Collections in the Sidebar).
Disable in Viewports — toggles the object's or collection's visibility in the 3D Viewport alone, for all view layers, leaving the render untouched. It's separate from Hide in Viewports — an object needs both enabled to show — and suits "long-term invisibility," keeping an object hidden even after Alt-H. It carries over to other blend-files when linking or appending, and objects hidden this way drop out of the view layer, so they're no longer evaluated and don't affect playback performance.
Disable in Renders — toggles the object's or collection's visibility in the render alone, for all view layers, leaving the 3D Viewport untouched; typically used for helper objects that aid modeling and animation but don't belong in the final image.
Holdout (Collections) — flips the collection's Holdout property on or off, which makes its objects punch a fully transparent hole into the view layer's render output.
Indirect Only (Collections, Cycles) — toggles the collection's Indirect Only property, so its objects contribute to the image only indirectly, through shadows and reflections.

## Usage

Relations Management — objects and collections can be reorganized, linked, or parented right in the Outliner by drag-and-drop — a natural way to handle scene hierarchies and the relationships between them.
Moving and Linking:
  Move — drop one object or collection onto a different collection to relocate it there.
  Link — hold Ctrl while dragging an object (or collection) onto a collection to link rather than move it, letting the same object or collection belong to several parent collections at once.
Parenting:
  Parent to Object — drop one object onto another to make the first a child of it; hold Alt as you drop to skip keeping the transform relationship (the child holds its world position).
  Clear Parent — drag the child out of its parent's hierarchy to sever the link; holding Alt as you drop clears the parent yet keeps the parent's transform applied to the child.
  Parent Across Collections — to parent an object living in a different collection, hold Shift while dragging.
  See Parenting Objects for more on parenting and transform inheritance.
Note: drag-and-drop applies to the whole current selection; any selected data-blocks incompatible with the operation are left alone.

Modifiers, Constraints, and Visual Effects — the Outliner offers a few ways to handle these: drag individual items to reorder them within the stack or copy them to another object; drag the group item (Modifiers, say) to copy the entire stack onto another object, replacing that object's existing stack; and apply or delete items through the context menu.

Drag & Dropping to 3D Viewport — drag an object out of the Outliner into the 3D Viewport and you get a duplicate — a fresh object carrying its own copy of the source object data; drag object data instead and you get a linked duplicate — a fresh object pointing at that same source object data.

## Add-ons

The Add-ons section manages secondary scripts — "Add-ons" — that extend Blender's functionality; most of the time you get them through the Extensions system. Here you can search for, install, enable, and disable Add-ons. Tip: if an Add-on doesn't activate when enabled, check the Console window for any errors.

Filtering Add-ons:
Search Add-ons — Blender ships with some Add-ons preinstalled and ready to enable, but you can add your own or any interesting ones from the web.
Enabled Add-ons Only — shows only the enabled add-ons in the current Category.
Add-on Tags — add-ons are tagged by which areas of Blender they affect.

Add-on Settings:
Refresh Local — rescans extension and legacy add-ons for changes to modules and metadata (much like a restart); any issues come back as warnings.
Install from Disk — installs an extension from a .zip package into a Local Repository, with no updates available. It also installs legacy Add-ons — see Installing Legacy Add-ons.

Enabling & Disabling Add-ons — check or uncheck the box to the right of an add-on; its functionality should be available right away.

Add-on Information — click the arrow at the left of an add-on's box for more, such as its location, a description, a documentation link, and a button to report a bug specific to it.
Add-on Preferences — some add-ons carry their own preferences in the Preferences part of the add-on's information box, used for instance to enable/disable certain functions, which sometimes all default to off — so check whether an enabled add-on has any.

Installing Legacy Add-ons — click Install from Disk and pick the add-on's .py file (if it's a single file) or its .zip. The add-on isn't enabled automatically after installation; tick its checkbox to do that.
Refresh — scans the Add-on Directory for new add-ons.
Tip: this screen won't install a folder-based addon made of loose .py files, but you can still do it by adding a Script Directory:
- Create an empty directory somewhere (e.g. my_scripts).
- Add a subdirectory under my_scripts named addons (Blender requires exactly this name).
- Put your addon folder inside that addons folder.
- Open the Preferences' File Paths section.
- Add a Script Directories entry pointing at your script folder (e.g. my_scripts).
- Save the preferences and restart Blender so it picks up the new add-on location.
The add-ons in that folder then become available automatically; you just enable them.

## Developer Tools

These preferences are set aside for features that aid Blender and add-on development; the category is hidden by default and appears once you enable Developer Extras.

Debug:
Undo Legacy — uses the legacy undo (slower than the new default but possibly steadier in some cases).
No Override Auto Resync — disables automatic resync detection and processing for library overrides on file load; enable it for older blend-files that need manual Resync (Enforce) handling.
Cycles Debug — shows the Cycles rendering debug panel.
Asset Debug Info — surfaces extra Asset Browser fields that help with debugging.
Asset Indexing — turning the asset indexer off makes every asset-library refresh reread assets from disk in full.
Viewport Debug — turns on viewport debugging options for developers in the overlays pop-over.
EEVEE Debug — turns on EEVEE debugging options for developers.

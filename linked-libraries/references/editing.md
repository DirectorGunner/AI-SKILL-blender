# Editing, File Paths, Save Load, Opening Saving ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing; File Paths; Save & Load; Opening & Saving; Packed Data.

## Editing

These preferences control how various tools respond to your input.

Objects — New Objects:
Link Materials To — to grasp this option, it helps to know how Blender treats Objects. Nearly everything in Blender lives in a hierarchy of data-blocks, each one acting as a container for a particular kind of information: the Object data-block carries the Object's location, rotation, and scale, while the linked Object Data data-block carries the mesh. A material can be linked two ways — Object Data (a new material becomes part of the Object Data's data-block) or Object (a new material becomes part of the Object's data-block). See also Blender's Data System.
Align to — World (new objects line up with world coordinates), View (new objects line up with view coordinates), 3D Cursor (new objects take the 3D cursor's orientation).
Enter Edit Mode — when on, Edit Mode switches on automatically as you create a new object.
Instance Empty Size — the display size of empties when a new collection instance is made.

Copy on Duplicate — these checkboxes set which data a duplicated object copies and which stays linked. A checked box copies that data with the duplicate; an unchecked box leaves it linked to the source object. Check Mesh, for instance, and the new object gets a full copy of the mesh data, each behaving on its own; leave it unchecked and editing one object's mesh shows up in the duplicate too. The same logic covers every checkbox in the data-block list.

3D Cursor:
Cursor – Surface Project — when you place the cursor by clicking, it lands projected onto the surface beneath it.
Cursor – Lock Adjust — while the viewport is locked to the cursor, moving the cursor keeps the view from jumping because of the new offset.

Annotations:
Default Color — the starting color for new Annotate layers.
Eraser Radius — the eraser's size with the Annotate Tool.
See also Annotations.

Weight Paint — mesh skin weighting governs how much a bone deforms a character's mesh. To show and paint these weights Blender uses a color ramp (blue to green, yellow to red); ticking the checkbox switches to an alternate map whose ramp starts from an empty range, letting you build a custom map with the usual color-ramp options. See the Color ramps page for detail.

Grease Pencil:
Manhattan — the fewest pixels the mouse must move horizontally or vertically before the motion is recorded; lowering it helps with curvy lines.
Euclidean — the shortest distance the mouse must travel before motion is recorded.
See also Grease Pencil.

Text Editor:
Auto Close Character Pairs — automatically adds the matching closing character when you type quotes, brackets, braces, or parentheses.

Node Editor:
Auto-Offset — automatically nudges the following or previous nodes in a chain when you insert a new node (see Auto-Offset).
Auto-offset Margin — the margin used when offsetting nodes.

Miscellaneous:
Sculpt Overlay Color — sets a color for the inner part of the brush circle in Sculpt Mode, laid over the brush to mark the focal point of its influence. The overlay color shows only when overlay visibility is on (click the eye to set it), and its transparency comes from the alpha slider in the Sidebar's Tool tab ‣ Display panel.

## File Paths

The File section of Preferences lets you configure auto-save and set default file paths for blend-files, rendered images, and more. You can set locations for various external files via the options below. Hint: the default path // points at the folder of the currently open blend-file (see Relative Paths).

Data:
Fonts — the default place to browse for text-object font files.
Textures — the default place to browse for image textures.
Sounds — the default place to browse for sound files.
Temporary Files — where temporary save files go; the path must point at an existing directory or it's ignored and the system's temp directory is used, and a blank value likewise falls back to the system's temp directory (see Temporary Directory).
Render:
  Render Output — where rendered images/videos are saved.
  Render Cache — where cached render images are kept.

Asset Libraries — the names and on-drive paths of asset libraries; add one to this list to make Blender aware of it. The name is only for your reference and shows up in asset-library selectors, while the path should point at the library's location. To make a new asset library, set up an empty directory and drop it into the List View — then any asset in any blend-file under it (or its subdirectories) shows up in the Asset Browser.
Import Method — how data is handled when an asset is imported, unless the Asset Browser overrides it.
  Link — the asset is linked into the current blend-file and stays read-only; later edits to the asset file propagate to every file that links it.
  Append — the whole asset and all its dependencies are appended into the current file. Drag a material in three times and you get three independent copies; same for an object. "Dependencies" here means everything the asset relies on — for an object that can be its mesh and materials, but also other objects pulled in by modifiers, constraints, or drivers. Because the file now owns its own copy, later edits to the asset file won't show up in the file it was appended to.
  Append (Reuse Data) — this one's specific to the Asset Browser. On an asset's first use it's appended together with its dependencies, exactly as above, but Blender notes where it came from and reuses as much data as possible on later uses. Drag a material in three times and it loads once, then gets assigned three times; drag an object in three times and you get three object copies that all share their mesh data, materials, and so on. Because the file now owns its own copy, later edits to the asset file won't show up here either.
  Pack — brings the asset in as linked data and packs it into the current blend-file straight away, keeping it available even if the original library data changes or goes missing; good for self-contained files that don't lean on external asset-library paths.
Relative Path — use a relative path when linking assets from this library.

Script Directories — extra places to look for Python scripts, each givable a Name to signal its purpose. By default Blender checks several platform-dependent directories for scripts; adding a user script path here brings in one more, handy for keeping your own scripts and add-ons separate from the current Blender version. You'll need to create subfolders matching the structure of the scripts folder in Blender's install directory. These subdirectories are used when present:
startup/ — modules here are imported at startup.
addons/ — legacy add-ons here are listed in the add-ons preferences.
modules/ — modules here can be imported by other scripts.
presets/ — presets here are added to the existing presets.
Hint: for add-ons it's now recommended to use a local extension repository if you want extra install/manage locations, defining them as extensions to use them.
Note: restart Blender for any changes to the user scripts to take effect.

Applications:
Image Editor — the path to an external image-editing program.
Animation Player — the program for playing back rendered animations via View Animation; the default, Internal, uses Blender's built-in player, which plays every format Blender supports and needs no third-party app.
Text Editor:
  Program — the command to launch the text editor for Edit Externally, either a full path or a command on $PATH; left blank, the internal editor is used.
  Arguments — the exact format of the arguments the text editor opens files with. The supported expansions: $filepath (the file's absolute path), $line (the line to open at, optional), $column (the column from the line's start, optional), and $line0 & $column0 (as those but zero-based). Example: -f $filepath -l $line -c $column.

Development — shown only with Developer Extras on.
I18n Branches — points at the /branches directory of your local SVN translation copy, so you can translate straight from the UI.

Known Limitations — Permissions on Windows: make sure you have the right privileges to run the executable that accesses the defined path. On Windows, for instance, enabling "Run this program as an administrator" for the executable makes the editor fail to open, due to a limitation in the OS's User Account Control. Running a program with elevated privileges is potentially dangerous.

## Save & Load

Blend Files:
Save – Save Prompt — prompts you to confirm before a blend-file is closed or a new one opened while the current file holds unsaved changes.
Save Versions — how many backup versions are kept when you save newer versions of a file, stored in the same directory with extensions .blend1, .blend2, etc., the number rising with the count you set; older saves carry the higher number. At the default of 2, for instance, you get three versions: *.blend (last saved), *.blend1 (second last), *.blend2 (third last).
Recent Files — how many files appear in File ‣ Open Recent.
Auto Save — turns on Blender's Auto Save, which periodically writes a temporary backup of the current file to the Temporary Directory, useful for recovering after a crash or sudden shutdown.
Timer (Minutes) — the gap, in minutes, between auto-saves; shorter gaps protect better but add disk writes, which can hurt performance on larger files.
File Preview Types — how blend-file previews are made, used both in the File Browser and in the OS file browser. None (no previews), Auto (a screenshot of the active Workspace when there's no camera, or a camera-view preview when there is one), Screenshot (a screenshot of the active Workspace), or Camera View (a Workbench render from the camera's viewpoint).
Default To – Relative Paths — the default for Relative Paths when loading external files like images, sounds, and linked libraries; ignored if a path is already set.
Default To – Compress File — the default for Compress file when saving blend-files.
Default To – Load UI — the default for Load UI when loading blend-files.
Text Files – Tabs as Spaces — pressing Tab in the Text Editor inserts the right number of spaces rather than tab characters.
Auto Run Python Scripts — for security, Python scripts (driver expressions included) don't run by default; if you only load files from trusted sources, letting them run automatically can be handier.
  Excluded Paths — blend-files in these folders never auto-run Python scripts, useful for marking where untrusted files live. See also Python Security.

File Browser:
Show Locations – Recent — hides the File Browser's Recent panel of recently visited folders.
Show Locations – System — hides the System Bookmarks in the File Browser.
Defaults – Filter Files — on, the File Browser's file region shows only suitable files (blend-files when loading a complete Blender setting, say); the file-type selection can be changed in the file region.
Defaults – Show Hidden Files/Data-Blocks — shows files and data-blocks whose names begin with . in File Browsers. Dot-prefixed data-block names are hidden by default so internal or helper data-blocks don't get used by mistake (see Dot-Prefixed Names (Hidden Data)). See also: hidden data-blocks can be shown in Data-Block Menus by enabling Search – Show Hidden.

## Opening & Saving

Opening and saving blend-files is normally handled through the File Browser. Tip: you can also open a blend-file by dragging and dropping it into the Blender window, which lets you link/append it too. Note — Unsaved Changes: by default, if you have unsaved changes when quitting Blender or loading another blend-file, a pop-up asks you to either discard them or save; you can switch this off with the Save Prompt option in the Preferences' Save & Load section.

Opening Files — Reference: Menu: File ‣ Open…; Shortcut: Ctrl-O. The upper text field shows the current directory path and the lower one holds the chosen filename.
Options:
Load UI — when on, the screen layout stored inside each blend-file is used, replacing your current layout and Workspaces; off, the file's layout is ignored. Tip: to work on a file with your own defaults, launch a fresh Blender, open the File Browser, turn Load UI off, and open the file.
Trusted Source — when on, any Python scripts and drivers the file may carry run automatically; turn it on only if you made the file yourself or trust whoever gave it to you not to have slipped in malicious code. See Python Security to set default trust options.

Open Recent — Reference: Menu: File ‣ Open Recent; Shortcut: Shift-Ctrl-O. Shows a list of recently opened blend-files; hovering an item previews it and shows its info, and clicking a name opens that file. RMB on a listed item opens a context menu whose options include Open File Location, which reveals that spot in your OS file explorer or Finder.
Clear Recent Files List — drops items from the recent list.
Remove — which items to drop. All Items (every recent file) or Items Not Found (files that can't be located, i.e. moved or deleted).

Recover — Last Session — Reference: Menu: File ‣ Recover ‣ Last Session. Loads the quit.blend file Blender auto-saved just before quitting, so you can recover your last session if you closed Blender by accident.
Auto Save — Reference: Menu: File ‣ Recover ‣ Auto Save. Recovers the most recent auto-saved version of your file, handy after a crash or quitting without saving. It opens a file browser pointed at your system's Temporary Directory; auto-saved files are usually named like <filename>_autosave.blend or a random identifier and use the .blend extension. Set how often and how autosave runs in the Auto Save Preferences. Warning: auto save has limits — notably it won't save changes in Sculpt, Texture Paint, or Edit mode. Important: only one auto-saved file is kept per project, recovering from one loses any changes made since the last save, and older auto saves aren't retained.

Saving Files — Reference: Menu: File ‣ Save; Shortcut: Ctrl-S. Saves the current blend-file over itself (if it was never saved, this switches to Save As… automatically).

Save Incremental — Reference: Menu: File ‣ Save Incremental; Shortcut: Ctrl-Alt-S. Saves the current file under a numerically bumped name that won't overwrite any existing file.

Save As — Reference: Menu: File ‣ Save As…; Shortcut: Shift-Ctrl-S. Pick where on disk to write the blend-file. Warning: if a file of that name already exists, the text field turns red to warn you it'll be overwritten. Tip: use the plus/minus buttons beside the file name, or NumpadPlus / NumpadMinus, to raise or lower a number at the end of the name (e.g. file_01.blend to file_02.blend).
Options:
Compress — shrinks the resulting blend-file but takes longer to save and load; useful for distributing files online and saving drive space on big projects, though it can cause slowdowns when quitting Blender or auto-saving backups. See Compression & Memory Use. Hint: the algorithm is Zstandard, which isn't Blender-specific, so files can be compressed/decompressed with outside tools. Changed in version 3.0: earlier versions used Gzip, so to open newer blend-files in versions before 3.0 you must first save them uncompressed in a newer Blender or decompress them with an external Zstandard tool.
Remap Relative — remaps Relative Paths (such as linked libraries and images) when you save a file to a new location.
Save Copy — saves a copy of the current working state without making the saved file active.

Save Copy — Reference: Menu: File ‣ Save Copy…. Choose a destination path for the blend-file, then go back to editing the original; handy for stashing backups of the working state without touching the original. For options see Save As.

Relative Paths — plenty of blend-files point to external images or other linked blend-files, and a path tells Blender where to find them; move those external files and the referencing blend-file no longer looks right. When you specify such a file, the default is to make the path relative: Blender keeps a partial path measured from the referencing blend-file's own directory, which helps when you reorganize folders or move your files.

With a relative path you can move the blend-file somewhere new as long as the linked files travel with it — you could, for instance, send someone a folder holding a blend-file plus a subfolder of the external images it references.

Where relative paths are supported, the File Browser shows a Relative Path checkbox; when typing a path into a text field, prefix it with a double slash (//) to make it relative. Relative paths are the default, but you can change that in the Preferences' File tab.

Note: you can't use relative paths in a brand-new untitled blend-file — save the file first, before you link to anything external.

Hint: if you must move a blend-file while keeping it positioned relative to its linked resources, turn to Blender's File Save As, which offers a Remap Relative option for the file links.

## Packed Data

Blender can wrap (incorporate) various kinds of data, normally kept outside the blend-file, inside it instead. An image texture that's an external image file, for example, can be tucked "inside" the blend-file, letting you share a whole project as one file rather than, say, an archive of the blend-file plus all its dependencies. You can tell data is packed by the little "gift box" icon beside its path. Warning — not all external files can be packed: some heavy ones, like videos from the Sequence Editor or Movie Clips, can't be packed into a blend-file.

Pack Data — Pack Resources — Reference: Panel: File ‣ External Data ‣ Pack Resources. Flags every eligible external resource the blend-file uses as packed; the actual packing happens on the next save.
Automatically Pack Resources — Reference: Panel: File ‣ External Data ‣ Automatically Pack Resources. When on, every eligible external resource — existing or added later — is automatically flagged as packed; as with Pack Resources, the file must be saved to drive to take effect. Turning it off unpacks nothing, but future external files simply stop being auto-flagged.
Selective Packing — pack a single file by clicking the little "gift box" icon to the left of its file-path widget.

Unpack Data — Unpack Resources — Reference: Panel: File ‣ External Data ‣ Unpack Resources. Unpacks every external resource stored in the blend-file.
Options:
Use files in current directory (create when necessary) — unpacks everything into the blend-file's own directory (//), sorted into proper folders (like "textures"); if the target file already exists, it uses that rather than unpacking.
Write files to current directory (overwrite existing files) — as above, but overwrites an existing target file.
Use files in original location (create when necessary) — unpacks everything to its original location; if the target already exists, it uses that rather than unpacking.
Write files to original location (overwrite existing files) — as above, but overwrites an existing target.
Disable AutoPack, keep all packed files — only turns the Automatically Pack Resources option off.
Selective Unpacking — unpack a single file by clicking the little "gift box" icon to the left of its file-path widget.
Options:
Remove Pack — just marks the file unpacked, without writing it or reloading it from drive.
Create <local file path> — unpacks the file to the proposed path, local to the current blend-file.
Use <original file path> (differs)|(identical) — if the original path still exists, marks it unpacked (it won't auto-reload from drive); (differs)/(identical) note whether the packed version and the on-drive one match.
Overwrite <original file path> — if the original path exists but differs from the packed version, marks it unpacked and overwrites the on-drive file with the packed one.
Create <original file path> — if the original path doesn't exist, marks it unpacked and writes it to drive.

Pack Linked Libraries — Reference: Panel: File ‣ External Data ‣ Pack Linked Libraries. Flags every linked library file in the current blend-file as packed; the actual packing happens on the next save.
Unpack Linked Libraries — Reference: Panel: File ‣ External Data ‣ Unpack Linked Libraries. Unpacks every linked library file used by this blend-file.

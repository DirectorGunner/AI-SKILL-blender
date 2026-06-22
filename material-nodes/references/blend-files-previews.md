# Blend Files Previews, Rename, Custom Properties, File Paths ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Blend-Files Previews; Rename; Custom Properties; File Paths; Alembic; FBX.

## Blend-Files Previews

A blend-file can hold previews, both of itself and of some of its data-blocks. You can stop any previews being written on save with the Save Preview Images setting in the Preferences' Save & Load section.

Blend-File Preview — Blender saves a small preview of the current scene in the blend-file by default, which appears in the File Browser's Thumbnail view. During installation, Blender also adds a small tool to your OS so your system file browser can show these previews as thumbnails too.
macOS — the Blender Thumbnail extension can be switched off in System Settings under "Login Items & Extensions", in the Quick Look category.

Data-Blocks Previews — Blender auto-generates previews for some data types, mainly shading-related ones (images, textures, materials, lights, world shaders). It can also keep previews for scenes, collections, and objects, though those you generate by hand. These previews then feed the File Browser's Thumbnail view when you link or append data-blocks.
Refresh Data-Block Previews — Reference: Menu: File ‣ Data Previews ‣ Refresh Data-blocks Previews. Refreshes every auto-generatable (shading-related) data-block preview in the current blend-file; you still need to save the file to write them to drive.
Batch Generate Previews — Reference: Menu: File ‣ Data Previews ‣ Batch Generate Previews. Generates some data-block types' previews (you choose which in its options) across one or more blend-files on your drive; don't run it on the file currently open in Blender. This is currently the only way to generate and store previews for scenes, collections, and objects in blend-files, and since it involves a lot of rendering — even at small sizes — it can take a while.
Scenes — generates previews of scenes and their collections.
Collections — generates previews of object collections.
Objects — generates previews of objects.
Materials & Textures — covers materials, textures, images, and the rest of the internal data.
Trusted Blend Files — when on, any Python scripts and drivers the file may carry run automatically; turn it on only if you made the file yourself or trust whoever gave it to you not to have slipped in malicious code. See Python Security.
Save Backups — keeps a backup copy (blend1-file) of each file when saving alongside generated previews.
Clear Data-Block Previews — Reference: Menu: File ‣ Data Previews ‣ Clear Data-blocks Previews. Clears all previews, a generic type, or a specific data-block type, in the current blend-file; you still need to save to clear them from drive.
Batch Clear Previews — Reference: Menu: File ‣ Data Previews ‣ Batch Clear Previews. Clears some data-block types' previews (you choose which) across one or more blend-files on your drive; don't run it on the file currently open in Blender.
Scenes — clears previews of scenes and their collections.
Collections — clears previews of object collections.
Objects — clears previews of objects.
Materials & Textures — clears previews for materials, textures, images, and other internal data.
Trusted Blend Files — as above; runs the file's Python scripts and drivers automatically, so enable it only for files you trust (see Python Security).
Save Backups — keeps a backup copy (blend1-file) of each file when saving alongside cleared previews.

## Rename

Rename Active Item — Reference: Menu: Edit ‣ Rename Active Item; Shortcut: F2. Renames the active Bone, Node, Object, and Sequence Strip. Running it pops a dialog whose text field holds the current name for you to overwrite; Return confirms, Esc cancels.

Batch Rename — Reference: Menu: Edit ‣ Batch Rename; Shortcut: Ctrl-F2. Renames many data-block names at once via a pop-up of operations and their options, applied one after another, top to bottom.
Data Source — where Blender looks for the data-blocks to rename. Selected (the currently selected objects) or All (all data in the blend file).
Data Type — which data-block type to run the batch rename on.
Operations — Batch Rename has several sub-operations for changing names; the default is Find/Replace, but you can add others to refine the names further, and each reports in the status bar how many data-blocks it renamed.
Find/Replace — searches for a piece of text in the names and optionally swaps in new text; Regular Expressions can tailor the Find/Replace text and are enabled by the icon to the right of the fields.
  Find — the text to search for.
  Replace — the text to substitute into matching names.
  Case Sensitive — matches the Find text's case exactly.
Set Name — works most like Rename Active Item, renaming the current data-block without a find-and-replace.
  Method — New (drops the current name for the "new" one), Prefix (adds text at the front, handy for tools that look for special prefix text), or Suffix (adds text at the end, for tools that look for special suffix text).
  Name — the new name or the text to add as prefix/suffix.
Strip Characters — tidies names by removing certain character types from the start or end.
  Characters — Spaces (e.g. "Living Room " becomes "Living Room"), Digits (e.g. cube.001 becomes cube.), or Punctuation (,.?!:; and the like, e.g. cube? becomes cube). Tip: remove several types at once with Shift-LMB on them.
  Strip From — Start (leading characters) or End (trailing characters).
Change Case — sets a name's case to one of:
  Convert To — Upper Case (e.g. cube.001 becomes CUBE.001), Lower Case (e.g. CUBE.001 becomes cube.001), or Title Case (e.g. living room becomes Living Room).

## Custom Properties

Custom properties let you stash your own data in Blender's data-blocks. They're handy for rigging (bones and objects can carry custom properties that drive other properties) and for Python scripts, where it's common to define settings Blender doesn't have; you can also reach them from materials via the Attribute Node. Only certain data supports them: every data-block type, bones and pose bones, and sequence strips. To add one, find the Custom Properties panel at the bottom of most Properties or Sidebar regions and click New; remove them from the same spot with the delete icon, and once added, configure them with the edit icon for a given use case (see Editing Properties).

Editing Properties — User Interface: custom properties are edited through the panel on data types that support them, where you set things like default values, ranges, and even a custom tooltip.
Type — the property's data type; each type allows only certain data settings.
  Float — a number with decimals, e.g. 3.141, 5.0, or 6.125.
  Float Array — several floats together, e.g. [3.141, 5.0, 6.125]; it also suits data representable as a float array, like colors, which you set via the Subtype selector.
  Integer — a number with no decimals, e.g. 1, 2, 3, or 4.
  Integer Array — several integers together, e.g. [1, 2, 3, 4].
  Boolean — two possible values, e.g. True or False.
  Boolean Array — several booleans together, e.g. [True, False, True].
  String — a run of characters such as "Some Text".
  Data-Block — a reference to a Blender object (see Data-Blocks).
  Python — edit a Python data type directly, for unsupported types.
Array Length — how many elements the array holds; above 7, you can't edit elements directly and must press Edit Value to do so.
Property Name — the text shown to the left of the value, also the key used to reach the property from Python.
Default Value — the property's default, used by the Reset to Default Value operator. Warning: default values seed NLA blending, so a nonsensical default (0 for a scaling property, say) on a property meant for keyframing is likely to cause trouble.
Min, Max — the smallest/largest value the property may take.
Library Overridable — lets the property be overridden when the data-block is linked.
Soft Limits — caps how far the Property Value slider reaches without typing the value in.
Soft Min, Max — the soft limit's smallest/largest value.
Step — a multiplier for how much the value changes per increment; the internal float step is 0.01, so a Step of 5 increments by 0.05 and a Step of 100 by 1.0, while the internal integer step is 1.
Precision — how many digits after the decimal show in the UI for float types.
Subtype — what kind of data the property holds, which shapes its UI; available only for float properties, with different choices for regular floats and float arrays (the unit often follows the Scene Units).
  For regular floats: Plain Data (no special behavior), Pixel (a digital-image-resolution measure), Percentage (shown as a percentage, usually with Min/Max of 0 and 100), Factor (a percentage between a lower and upper bound with numerical meaning), Angle (a measure between intersecting lines), Time (seconds), Distance (a measure of space between items), Power (work over time, in watts — Blender uses it for light intensity), Temperature (how much heat is present), Wavelength (the distance between wave cycles, in mm, µm, nm, or pm).
  For float arrays: Plain Data (no special behavior), Linear Color (color in linear space), Gamma-Corrected Color (color in gamma-corrected space), Euler Angles (Euler rotation angles), Quaternion Angles (Quaternion rotation angles).
  Note: for either color subtype to behave, the Property Value must be a vector of three or four values, depending on whether there's an Alpha Channel.
ID Type (Data-Block) — the ID-block type, e.g. Key, Image, Object, Material; see Data-Block Types for the full list.
Description — lets you write a custom Tooltip for the property.

Python Access — custom properties are reached much like dictionaries, with the catch that a key must be a string, while a value must be a string, a number, an array of those, or a nested property. See the API documentation for details.

## File Paths

Path Templates — path templates swap template expressions (written {abcd}, where "abcd" is a variable name) into a filepath when the path is used. For example, say the open blend file is dance.blend and your render output path reads:
```text
//my_render_dir/{blend_name}.png
```
then at render time Blender treats the path as:
```text
//my_render_dir/dance.png
```
with {blend_name} replaced by dance from dance.blend. The substitution happens internally at the moment of use (while rendering, say), so the template syntax stays as-is in the path field. Note: for now, templates apply only to the render output path under Scene properties and to the output paths on the compositor's File Output node; more filepaths will gain template support in future releases.

Available Variables — these are currently available in template expressions.
Available in every path that supports templates:
blend_name — the open blend file's name (minus the .blend).
blend_dir — the path up to (but not including) the open blend file.
blend_name_lib — like blend_name, except that on path properties of library-linked data-blocks it's the name of the library blend file the data-block comes from.
blend_dir_lib — like blend_dir, except that on path properties of library-linked data-blocks it's the path to the library blend file the data-block comes from.
Available only in render output paths (the compositor File Output node included):
fps — the current scene's frames per second.
resolution_x / resolution_y — the rendered image's x and y resolution; this folds in the resolution scale, so a 1000x600 scene at 50% scale gives resolution_x and resolution_y of 500 and 300.
scene_name — the current scene's name.
camera_name — the current render camera's name.
Found only on a node's path properties:
node_name — the name of the node carrying the path property.

Syntax — a basic template expression just wraps a variable name in curly braces:
```text
dance_{fps}.png
```
Format Specifiers — a template expression can also carry a format specifier telling Blender how to format the substituted value; it follows a separating colon:
```text
dance_{fps:FORMAT}.png
```
Format specifiers currently work only with variables that hold numbers, not strings. The available ones:
- dance_{fps:###}.png — formats as an integer with at least 3 digits.
- dance_{fps:.###}.png — formats as a float with exactly 3 digits after the decimal point.
- dance_{fps:###.##}.png — formats as a float with at least 3 integer digits and exactly 2 fractional digits.
In every case the count of hash symbols (#) sets how many digits you want. For instance, with fps of 29.97:
- dance_{fps:###}.png -> dance_030.png
- dance_{fps:.###}.png -> dance_29.970.png
- dance_{fps:###.##}.png -> -> dance_029.97.png
Note that values are properly rounded for the chosen digit count. With no format spec, the variable's default formatting applies (float for fps, integer for resolution).

Escape Sequences — because { and } drive template expressions in paths that support them, a literal { or } in such a path must be doubled:
- {{ becomes a single { in the final path.
- }} becomes a single } in the final path.
For example:
- my_weird}}_{{path.png -> my_weird}_{path.png
- //my_render_{{dir}}/{blend_name}.png -> //my_render_{dir}/dance.png
- //my_render_dir/{{{blend_name}}}.png -> //my_render_dir/{dance}.png

Errors — paths that support templates can hold template errors that block processing. In this path, for example:
```text
//my_render_dir/{blend_name.png
```
the expression {blend_name isn't closed properly, which errors. When a path has template errors, its field is highlighted red in the UI, and hovering it pops a tooltip listing the errors found. Note: depending on the path, template errors may block certain actions — errors in the render output path, for instance, make rendering an animation fail with a message about the path errors.

## Alembic

From the Alembic home page: Alembic is an open framework for computer-graphics interchange that distills complex, animated scenes down to a non-procedural, application-independent set of baked geometric results — a "distillation" of scenes into baked geometry exactly analogous to distilling lighting and rendering scenes into rendered image data. Alembic concentrates on efficiently storing the computed results of complex procedural geometric constructions; it deliberately doesn't concern itself with storing the complex dependency graph of procedural tools that made those results. It will, for example, efficiently store the animated vertex positions and transforms produced by an arbitrarily complex animation and simulation process — enveloping, corrective shapes, volume-preserving sims, cloth and flesh sims, and so on — but won't try to store a representation of the computation network (the rigs, basically) needed to produce those final positions and transforms.

In short, Alembic can save an animated mesh to disk and load it back fast and efficiently, so a mesh animated with a very CPU-heavy rig can be "baked" to an Alembic file and later loaded into the shot file for shading and lighting with only moderate CPU use. Thanks to the open-source nature of both the Alembic standard and its C++ implementation, Blender fits into a hybrid pipeline: other software such as Houdini or Maya can export to Alembic for loading, shading, and rendering in Blender, and you can equally animate characters or other models in Blender, export to Alembic, and load them into other software for further work.

Importing Alembic Files — on import, Mesh Sequence Cache modifiers are added automatically to time-varying meshes, and for time-varying object transforms (animated rotation, location, or scale) the Transform Cache Constraint is used.
General — Scale: how much to enlarge or shrink the objects about the world's origin.
Options:
Relative Path — pick the file relative to the blend-file.
Set Frame Range — if checked, updates the scene's start and end frame to match the Alembic archive's.
Is Sequence — set true when the cache is split across separate files.
Validate Meshes — checks the imported mesh for corrupt data and repairs it if needed; with it off, bad data may crash display or editing. It slows importing but is recommended, since data errors aren't always obvious.
Always Add Cache Reader — adds cache modifiers and constraints to imported objects even when they aren't animated, so they can update when the Alembic archive is reloaded.

Exporting to Alembic Files — this section covers what the export options do.
General — Scale: sets the Alembic file's global scale; keep it at the default 1.0 to use Blender's units.
Include – Selection Only — on, exports only the selected objects; off, all objects.
Scene — Frame Start, End: the frame range to export, defaulting to the current scene range.
Sub-frame Sampling — controls sub-frame sampling of animations.
  Samples Transform — Transform Samples sets how many times per frame animated transforms are sampled and written.
  Geometry — Geometry Samples does the same for animated geometry.
  Shutter Open, Close — define the [open, close] interval the samples span, valid from -1 to 1, where -1 is the previous frame, 0 the current, and 1 the next. To capture detailed mesh motion blur, for instance, you can write subframes around the current frame with a sample count of 5, Shutter Open set to -0.25 and Shutter Close to 0.25 — mimicking a "180 degree" shutter that opens 90 degrees before the frame and closes 90 degrees after.
Use Instancing — exports duplicated or instanced objects as Alembic instances, speeding the export; disable it for compatibility with other software.
Custom Properties — on by default, exports custom properties to Alembic too. Supported types:
  - Numbers (int, float) and strings, exported as single-element arrays, so 47 exports as [47] and "Agent" as ["Agent"], matching many other DCCs.
  - Lists of numbers and strings, exported as-is, so [327, 47] stays [327, 47].
  - Matrices and nested number arrays, flattened into one long list, so a 3×2 matrix becomes 6 numbers and nested [[1, 2, 3], [4, 5], [6]] becomes [1, 2, 3, 4, 5, 6].
  - Numbers can be animated too.
Flatten Hierarchy — off, parent/child relations are exported too, and any unexported parent with exported children is replaced by an empty; on, those relations aren't exported and all transforms are written in world coordinates.
Settings — sets which visibility, modifier, and other viewport-versus-render settings to use. Render (use Render settings) or Viewport (use Viewport settings).
Geometry — UV Coordinates: on, exports UV maps; although Alembic itself supports just one UV map, Blender exports all of them in a way other software should read.
Merge UVs — on, UVs sharing a vertex and location merge into one, shrinking the file slightly.
Normals — on, exports an object's Normals. See Custom Split Normals of Meshes below.

Color Attributes — on, exports Color Attributes.
Face Sets — exports the material name per face (only the names, not the material data).
Subdivisions:
Apply — bakes in any Subdivision Surface modifiers before the write to Alembic.
Use Schema — writes polygonal meshes with the "SubD" Alembic schema instead of "PolyMesh", setting an import hint for the opening program to apply its own non-destructive subdivision.
Triangulate — triangulates the mesh before writing; for the specific option, see the Triangulate modifier.
Particle Systems — Alembic has no Particle System support, just as it has none for armatures.
Export Hair — hair goes out as animated zero-width curves.
Export Particles — particles go out as animated points.

Custom Split Normals of Meshes — Blender can import and export custom normals to Alembic files. As a rule of thumb, a fully smooth mesh exports without normals and so makes the smallest Alembic file, and the importer mirrors this: an Alembic mesh with no normals loads as smooth.
On export, for each mesh: with Custom Loop Normals, those loop normals are written; if any polygon is flagged flat, loop normals go out too; otherwise none are.
On import, when the Alembic mesh holds: loop normals (kFacevaryingScope) become custom loop normals; vertex normals (kVertexScope or kVaryingScope) convert to loop normals and are handled as above; no normals means the mesh is marked smooth; and unsupported normal types (kConstantScope, kUniformScope, kUnknownScope) are treated as no normals. When an imported mesh has no normals, the final look can be steered with the Normal's Shading.

Handling Time — unlike Blender and many other apps and formats, Alembic files have no notion of frames; Alembic works purely in time and values sampled over time, so there's no way to tell 30 FPS with 2 samples per frame apart from 60 FPS with 1 sample per frame, which has led many developers to simply hard-code 24 FPS when reading Alembic files. Blender instead leans on the current scene's frame rate to turn a frame number (in Blender) into a time in seconds (in Alembic), so you can import a 120 FPS Alembic file into a 30 FPS Blender scene and still see no time stretching.

## FBX

The FBX (Filmbox) format is widely used to move 3D data between applications, especially animated characters and complex scene data; it's supported by software like Autodesk Maya, 3ds Max, and Cinema 4D, and by game engines such as Unity and Unreal Engine. Blender's FBX importer covers a broad range of FBX features and aims to be quick, light on memory, and broadly compatible with FBX files old and new.

Import — General — Scale: how much to scale the imported objects about the world's origin.
Custom Properties — imports user properties as Custom Properties.
Enums As Strings — stores custom-property enumeration values as strings.
Geometry:
Custom Normals — imports custom normals when present (otherwise Blender computes them).
Subdivision Data — imports FBX subdivision info as Subdivision Surface Modifiers.
Vertex Colors — imports vertex color attributes. None (skip color attributes), sRGB (file's vertex colors are in sRGB Color Space), or Linear (file's vertex colors are in Linear Color Space).
Materials — Material Name Collision: what to do when an imported material's name clashes with an existing one. Make Unique (bring each material in as its own Blender material) or Reference Existing (if a material of that name already exists, point at it rather than importing).
Animation:
Offset — how far to shift animation timestamps, measured in frames.
Layered Animation Support — each FBX "take" imports as its own Action, with each animated object given its own Action Slot.
Armature — Ignore Leaf Bones: skips the last bone at the end of each chain (which marks the previous bone's length).

Export — to export FBX files, use the FBX Add-on.

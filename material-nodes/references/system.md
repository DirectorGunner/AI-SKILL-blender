# System, Viewport, Properties Editor, Shader Editor ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: System; Viewport; Properties Editor; Shader Editor; Spreadsheet.

## System

The System section lets you set graphics-card options, memory limits, and sound settings. Options your hardware doesn't support are either hidden or corrected at startup.

Cycles Render Devices — changes the Computing Device the Cycles render engine uses; Cycles can render on the CPU or certain GPUs (see GPU Rendering).
None — when set to None, or when None is the only choice, the CPU is Cycles' computing device.
CUDA — a compatible NVIDIA CUDA device becomes available for rendering with Cycles.
OptiX — a compatible NVIDIA OptiX device becomes available for rendering with Cycles.
HIP — a compatible AMD HIP device becomes available for rendering with Cycles.
oneAPI — a compatible Intel oneAPI device becomes available for rendering with Cycles.
Metal — a compatible Apple Metal device becomes available for rendering with Cycles.
Distribute Memory Across Devices — spreads resources over several GPUs instead of duplicating data, freeing room for larger scenes; it's available only when the GPUs are linked by a high-bandwidth protocol, currently just NVLink on NVIDIA GPUs.
Embree on GPU — turns on hardware ray tracing on Intel GPUs for better overall performance; supported only with oneAPI render devices.
HIP RT — speeds rendering by enabling AMD hardware ray tracing on RDNA2 and newer; available only with a HIP render device.
MetalRT — using MetalRT for ray tracing saves memory on curve-heavy scenes and can run faster in specific cases. Off (disabled, using the BVH2 layout for intersection queries), On (MetalRT for intersection queries), or Auto (pick the fastest intersection method automatically).

Display Graphics — settings governing how Blender draws its UI and other display graphics, which can affect performance and compatibility.
Backend — the graphics API used to draw the interface and render display content; changing it needs a Blender restart. OpenGL (the traditional backend, broadly compatible) or Vulkan (potentially faster with better support for modern GPU features, though compatibility varies by system and drivers).
Device (Vulkan) — which GPU handles display drawing, useful on multi-GPU systems (integrated + discrete) where you want a specific GPU for UI rendering; changing it needs a restart. Auto picks the most suitable GPU from your configuration and driver support.

Operating System Settings — set the in-use installation as your default Blender (MS-Windows & Linux only). On Linux, if Blender came from a package manager like Snap, file association is the package manager's job.
Register — makes the in-use Blender installation the default for generating thumbnails and opening blend-files.
Unregister — removes the file association and thumbnailer.
For All Users — registers Blender for everyone, which needs escalated privileges.
Linux Registration — setup files live under /usr/local for all users, otherwise ~/.local: a desktop file and icon make the app available in launchers, a file association for *.blend is set up, and the thumbnailer is installed so blend-file thumbnails appear in file managers (For All Users only).

Network:
Allow Online Access — lets Blender reach the internet; add-ons that respect this setting only go online when it's enabled, though Blender can't stop third-party add-ons from breaking the rule.
Time Out — how long (in seconds) online operations may wait before timing out; zero uses the system default.
Connection Limit — the most simultaneous connections an online operation may open; zero means no limit.

Memory & Limits:
Undo Steps — how many Undo steps are available.
Undo Memory Limit — the maximum memory use in Mb (0 is unlimited).
Global Undo — lets Blender record actions taken outside Edit Mode, such as duplicating objects, changing panel settings, or switching modes. Warning: switching it off saves memory but stops the Adjust Last Operation panel from working and, in some cases, prevents changing tool options, so it's best left on for normal use. See also Undo and Redo.
Console Scroll-back Lines — how many console-window lines are buffered in memory, handy for debugging and command-line rendering.
Texture Time Out — seconds since a GL texture was last accessed before it's freed; 0 keeps textures allocated.
Garbage Collection Rate — seconds between runs of the GL texture garbage collector.
VBO Time Out — seconds since a GL vertex buffer object (VBO) was last accessed before it's freed (0 keeps VBOs allocated).
Garbage Collection Rate — seconds between runs of the GL vertex-buffer-object garbage collector.
Shader Compilation Method — how GPU shaders compile in parallel. Not available on macOS, requires the OpenGL backend, and a change needs a Blender restart. Thread (several threads in one process compile shaders at once — more memory-efficient but possibly slower on some systems) or Subprocess:

(continued) several separate subprocesses compile shaders in parallel — potentially faster, especially with high core counts, but using far more RAM.
Threads / Subprocesses — how many shader-compilation threads or subprocesses to use, capped by the system's logical CPU cores; raising it can cut compile time at the cost of more memory, and 0 lets Blender choose a sensible number from your configuration. Not available on macOS, requires the OpenGL backend, and a change needs a restart.

Video Sequencer:
Memory Cache Limit — the upper limit (in megabytes) of the Video Sequencer and Movie Clip Editor memory cache; high values are recommended for best Clip editor and Sequencer performance.
Proxy Setup — when and how Proxies are made. Automatic (build proxies for added movie and image strips at every preview size) or Manual (set up proxies by hand). See also Sequencer Cache Properties.

Sound — this panel holds the sound settings for live playback within Blender and is available only with a device other than None; for export-sound settings see the Encoding Panel and Audio Panel.
Audio Device — the audio engine that processes and outputs audio.
  None — no playback support (audio strips still load and render normally).
  CoreAudio — macOS's native audio API, the default and preferred choice there.
  PulseAudio — the most common sound server on modern Linux, the preferred Linux choice when available.
  WASAPI — Windows's native audio API since Windows Vista, the default and preferred Windows choice.
  Jack — a high-quality professional engine needing a properly configured server running, with accurate sync to other professional audio apps via Jack.
  OpenAL — available on every platform as a fallback when the native engines fail; 3D audio played back may sound different from when rendered.
  SDL — uses the Simple Direct Media Layer API from libsdl.org, available on all platforms; possibly lower quality, so use it only as a backup.
Channels — how many audio source "locations" to output. Mono (one channel), Stereo (two, typically left and right), 4 Channels (four), 5.1 Surround (five plus one LFE channel), or 7.1 Surround (seven plus one LFE channel).
Mixing Buffer — how many samples the audio mixing buffer uses; bigger buffers can add latency, but if you hear clicks or other glitches, try raising it.
Sample Rate — the audio sampling rate.
Sample Format — the audio sample format.

## Viewport

Display — Text Info Overlay:
Object Info — shows the active Object's name and the frame number at the 3D Viewport's top-left.
View Name — shows the current view's name and type at the 3D Viewport's top-left, e.g. "User Perspective" or "Top Orthographic".
Playback Frame Rate (FPS) — shows the frames-per-second refresh rate during playback, at the 3D Viewport's top-left, turning red when the set frame rate can't be met.
Frame Rate Samples — computes the displayed FPS from an average of the current and recent frames; zero uses the number of frames in 1.0 second. More samples average over a longer span, so sudden performance shifts ramp more gradually; fewer samples track actual performance more closely but may jitter, making the FPS harder to read.
Gizmo Size — the gizmo's diameter.
HDRI Preview Size — the diameter of the HDRI sphere overlay.
3D Viewport Axes — Interactive Navigation (draws the axis as an interactive gizmo: click to view along it, drag to orbit), Simple Axes (a simpler, less intrusive axis, with Brightness for how vivid its colors are), or Off (no viewport axis). Size — the diameter of the 3D Viewport Axis widget.
Fresnel – Edit Mode — adds a fresnel effect to edit-mesh overlays, improving readability on very dense meshes but tiring the eyes when modeling lower-poly.

Quality:
Viewport Anti-Aliasing — sets the anti-aliasing for higher-quality rendering.
Smooth Wires — Overlay (draws overlays with smooth wire; without it, wires render aliased — you can disable it for Edit Mode separately since edges don't blend into shaded regions) and Edit Mode (smooth wire in Edit Mode; without it, wires render aliased).

Textures:
Limit Size — caps the maximum resolution of pictures used in textured display to save memory, given as a square of pixels (256 means a 256×256 texture); useful for game work, where the texture limit matches the target card's texture paging blocks.
Anisotropic Filtering — sets the anisotropic-filtering level, improving rendered-texture quality at a performance cost.
Clip Alpha — clips alpha below this threshold in the 3D Viewport; the default is deliberately low to avoid issues on some GPUs.
Image Display Method — how images are rendered. Automatic (uses GLSL on the GPU for speed but falls back to the CPU for large images, which can be slow on the GPU), 2D Texture (uses the CPU for display transform and renders images as a 2D texture), or GLSL (the fastest, using GLSL for display transform and rendering images as a 2D texture).

Subdivision:
GPU Subdivision — in some cases the GPU subdivides a mesh carrying a Subdivision Surface modifier, usually boosting subdivision performance. Note: when on, normals and tangents are interpolated rather than recomputed after smoothing, which can shade differently from the CPU path. Note: unsupported on Qualcomm GPUs on Windows.

## Properties Editor

The Properties editor shows settings for the active scene, object, material, and other data types, giving access to a broad range of context-sensitive properties used across Blender.

Navigation Bar — properties are grouped into tabs shown as a vertical column of icons in the editor's Navigation Bar region. You can flip the Navigation Bar to the editor's left or right by RMB on the region and choosing Navigation Bar ‣ Flip to Left/Right, and hide it with RMB on the region then Navigation Bar ‣ Hide, or via the region toggle icon (see Changing the Size and Hiding Regions).
Active Tool and Workspace Settings — the first tab carries the active tool's settings (in the 3D Viewport) plus those of the current workspace.
Scene — tabs for the active scene: Render (EEVEE, Cycles, or Workbench settings), Output, View Layer, Scene, World.
Collection — settings for the active Collection.
Object — tabs for the active object, some shown only for certain types: Object, Modifiers (or Grease Pencil Modifiers), Effects, Particles, Physics, Object Constraints.
Object Data — the Object Data tab keeps its name but changes icon by object type. Geometry Objects: Mesh, Curve, Surface, Text, Metaball, Grease Pencil. Rigging and Deformation Objects: Armature, Bone, Bone Constraints, Lattice. Other Object Types: Empty, Speaker, Camera, Light, Light Probe.
Object Shading — tabs for an object's look, shown only when relevant: Material, Texture.
Strips — tabs for video-editing strips, shown only when relevant: Strip Modifiers, Strip Properties.
Visible Tabs — lets you hide specific tabs in the Properties editor, handy for tailoring it to a workflow: in the Video Editing workspace you might hide object and shading tabs to cut clutter, and in the Modeling workspace you might hide the strip tabs. Hidden tabs can be brought back anytime from this filter list.

Header:
Display Filter (Ctrl-F) — search for properties by name; matches stay visible while the rest gray out, and the editor highlights the first match and jumps to its tab automatically. Begin a search with Ctrl-F, and Alt-F clears it.
Data Context Path — shows the current data-block's name and icon (Object, Material, Scene, etc.) plus its place in the data hierarchy, e.g. Cube (Object) –> Mesh –> Material.
Toggle Pin ID — click the pin to lock the editor to the current data-block so it doesn't change with the selection; click again to unlock and return to context-based display.
Options — reached from the Options popover at the editor's top-right.
  Sync with Outliner — whether a click on an Outliner icon switches the active tab. Always (always heed the clicked Outliner icon), Never (ignore Outliner clicks), or Auto (heed it only when the Properties editor borders the Outliner).

## Shader Editor

The Shader Editor is where you build the materials used for rendering. Materials for Cycles and EEVEE are defined by a node tree, so the editor's main window is a node editor. A full list of shader nodes lives in the rendering section.

Header:
Shader Type — the kind of data whose shader nodes you're editing: Object (the active object's Material), World (the World background), or Line Style (Freestyle Line Styles).
Use Nodes (Line Style) — use shader nodes to define the freestyle line style's texture.
Slot — the Slot menu selects the active material slot on the active object, and the material selector beside it swaps which material sits in that slot.
/ Pinned — keeps the current material visible in the Shader editor even when another object or material is selected elsewhere.

Sidebar — Options: the Sidebar's Options panel carries the same settings found in the Properties' Material tab (they vary by render engine); they're duplicated so you can edit the whole material from the Shader editor.

## Spreadsheet

The Spreadsheet editor lets you inspect the active object's geometry attributes, usually to debug geometry nodes.

Header:
Show Only Selected — available only while the object is in Edit Mode; when ticked, only the selected geometry elements' data appears.
Use Filter — whether to apply the filters defined in the Sidebar (below).
View Menu:
  Toolbar (T) — shows or hides the left-hand tab panel for creating and working with markers and masks.
  Sidebar (N) — shows or hides the Sidebar.
  Internal Attributes — shows attributes whose names begin with a period, meant for internal use.
  Area — area controls; see the user-interface documentation.

Main Region — displays the attribute data as a spreadsheet, each column an attribute or data property and each row one element — a vertex, face, spline, or instance, say. The column names and row indices stay pinned as you scroll in either direction.
Columns resize by dragging the vertical line between them.
Double-clicking that line auto-sizes the column to its content.
Columns reorder by dragging their header.
Note: tooltips give more detail by type — Byte Color attributes show as scene-linear floats while the actual integer values appear on hover, and Matrix attribute values appear only in tooltips.

Data Set Region — on the left, this region chooses what the spreadsheet shows.
Context Path — shows the active object's name in the panel header. Click an arrow between names to hide the modifier. Click the lock icon to pin the Spreadsheet to the currently active object and data path so it stays put when you select another object; click again to unlock.
Object Evaluation State — which state of the object's data is shown: Evaluated (with all modifiers applied), Original (the raw object data, no modifiers), or Viewer Node (data from the active Viewer Node in Geometry Nodes). You can also flip between Evaluated and Viewer Node via the icon in the Viewer node's header.
  Viewer Path — shown when Object Evaluation State is Viewer Node; traces the path from the modifier to the active viewer node, with each enclosing group appearing in the path if the viewer is nested.
  Viewer Data — shown when Object Evaluation State is Viewer Node; picks which Viewer Items from the active Viewer node appear in the Spreadsheet. When a Viewer node puts out several data sets (geometry plus one or more evaluated fields, say), each becomes its own Viewer Item, and this setting selects which to show — a specific attribute, value field, or geometry component — without touching the Viewer node's connection. Note: the available viewer items track the active Viewer node and its inputs, and changing the active viewer or its connections refreshes this list on its own.
Geometry — lets you browse nested geometries (a mesh inside an instance or a geometry collection, say).
Domain — lets you pick the attribute domain to show, such as mesh vertices or curve splines; the element count for each domain sits beside its entry.
  Volume Grids — when the chosen geometry component is a Volume, the Spreadsheet details every grid it holds. Each grid is one data field — density, color, or velocity, say — and can be inspected on its own for structure and memory use. For each grid it lists:
    Grid Name — the grid data's name, like density or temperature.
    Data Type — the kind of data the grid stores, e.g. Float, Vector, or Boolean.
    Class — the grid class describing its purpose, such as Fog Volume or Level Set.
    Voxel Extent — the grid's bounding box in voxel coordinates, i.e. the voxel count along X, Y, and Z.
    Min Voxels — the grid bounding box's minimum voxel coordinates: the lowest X, Y, Z voxel indices it occupies, marking where the grid begins in voxel space.
    Voxels — the grid's total active voxel count, including every explicitly stored voxel even when held in tiles (a single leaf tile holds 512 voxels).
    Leaf Voxels — the active voxels stored in leaf nodes; unlike Voxels, this leaves out voxels belonging to higher-level tiles.
    Tiles — the grid's active-tile count; tiles are higher-level voxel containers that sparse volume formats (OpenVDB, say) use to optimize storage.
    Size — the grid's estimated memory size, covering all currently allocated voxel and tile data.
  These figures let you weigh the complexity, density, and performance cost of volumetric data from Geometry Nodes or imported volume files. Note: because volume grids are sparse, the Extent can far exceed the actual active-voxel count — only active regions sit in memory, keeping volume data efficient even across large domains.

Sidebar — here you define filters so only matching rows show; click Add Row Filter and configure the properties below.
Enabled — uncheck to switch a filter off temporarily.
Column — the column to filter on; with no column of that name, the filter grays out and is ignored.

To filter on an attribute from a different domain, use the Store Named Attribute Node to make a copy converted to the current domain, then filter on that.

Operation — numerical columns offer the comparison operators below; other columns support only Equal To.
  Equal To — shows only rows whose column value equals the filter value (within the set threshold).
  Greater Than — shows only rows whose column value exceeds the filter value.
  Less Than — shows only rows whose column value falls below the filter value.
Value — the filter value to compare each row's value against.
Threshold — how far a row's value may stray from the filter value before it's dropped.

Status Bar — reports the row and column totals plus how many rows survive filtering.

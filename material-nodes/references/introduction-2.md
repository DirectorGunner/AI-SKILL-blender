# Introduction (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

The Video Sequencer lets you arrange images, videos, sounds, and scenes along a timeline and merge them into a fresh video. This section only covers its UI; for usage, see the Video Editing section.

Editor Layout — the Video Sequencer is made of several regions, spelled out in the next sections; the combined Sequencer & Preview view type appears in Figure 1.
Header — holds menus and buttons for working with the editor; it shifts a little with the chosen view type (below).
Footer — holds menus and buttons for animation playback.
Preview — shows the Sequencer's output at the Playhead's time.
Sequencer — shows a timeline for managing the strip montage.
Sidebar — shows the active strip's properties, split into panels and tabs; toggle with N.
Toolbar — shows a list of tools; toggle with T.

View Types — the Video Sequencer has three view types, switched via the View Type selector (Figure 1, top left).
Sequencer — the timeline and strip properties.
Preview — the preview window and preview properties.
Sequencer & Preview — both the preview and the timeline together with their properties.
Tip: rather than a single Video Sequencer in Sequencer & Preview mode, it's often handier to keep one in Sequencer mode and another in Preview mode, because Sequencer & Preview is missing most Preview tools; Blender's default Video Editing workspace sets up this layout for you.

Performance — playback can be sped up in a few ways. The biggest win is letting the Video Sequencer cache generated frames; there are two cache levels — a memory cache (on by default, and enlargeable if RAM allows) and a disk cache (slower but roomier) — both configurable in the Preferences. Another route is Strip Proxies: lower-resolution and/or lower-quality copies of source images and videos that load faster than the originals.

Preview mode shows how the finished video will look and also offers tools for moving, rotating, and scaling images, plus scopes for analyzing color distribution.

You can pan with MMB and zoom with the Wheel or NumpadPlus / NumpadMinus, or use the gizmos. Pressing Home resets the view, filling the editor's area with the preview.

Playback Controls — this region holds controls and options for playback, keying, auto keyframing, and transport. They let you control how animations preview and sync with audio, add and manage keyframes via keying sets and auto keying, navigate the timeline with playback and transport controls, and set frame ranges and preview chosen segments. See also the Playback Controls documentation for the full footer rundown.

This section describes Blender's asset library system, introduced in Blender 3.0 and set to grow over upcoming releases.

See also: Asset Browser (the primary interface for arranging and using assets), Asset Catalogs (for organizing assets), and Pose Library (built atop the Asset Browser).

What is an Asset? — an asset is a data-block that carries meaning. A blend-file is itself a database of many data-blocks — objects, textures, materials, and so on — and to reuse or share them, the data needs meaning: what is this, and what's it for? Assets are curated data-blocks meant for easy reuse. Note: the general word "asset" often also covers other file types — images, sounds, videos, etc. — which Blender doesn't currently support as assets; see Future Development.

What is an Asset Library? — it's a directory on your drive that you register in the Preferences as a library. Registering means giving the library a name (like "Sprite Fright") and an on-drive location (like /home/sybren/projects/sprite-fright/assets). Once registered, you can pick it in the Asset Browser; all its blend-files are scanned for assets, and those assets all appear there. Note: loading a library the first time can take a while, but later loads are much faster — Blender builds an index of every asset in a library and keeps it current as files change, storing the indices in the Local Cache Directory. The blend-files can sit directly in the library's top level or in any subdirectory; the on-drive organization is entirely yours, and whichever blend-file holds them, each asset can be given a catalog (see Asset Catalogs).

Asset Types — assets split broadly into primitive and preset, depending on the data-block type. Primitive assets are data-blocks linked or appended into the current file — objects, materials, worlds — you drag them from the Asset Browser either into the scene (for objects and worlds) or onto an existing object (for materials). Preset assets are data-blocks that get loaded and then applied to something or activated: a pose asset, say, loads from its blend-file and applies the pose to the active armature, while a brush asset is loaded into the current file and activated for painting or sculpting without being saved in the file. The asset-type definition will broaden in future; see Future Development.
Supported Assets:
- Material (Primitive) — a Material data-block applied to objects; dragging it onto an object replaces the material slot.
- Collection (Primitive) — a set of objects you can link or append into a scene, its internal hierarchy preserved and usable instanced or for modular scene building.
- Object (Primitive) — a standard Object asset dragged into the scene; it may hold mesh, curve, light, or other data.
- Brush (Preset) — a Brush asset for sculpting, texture painting, or vertex painting; activating it makes it the current brush but doesn't store it permanently in the file.
- Node Group (Primitive) — a Node Group asset dragged into compatible node editors (Geometry Nodes, Shader Editor, Compositor); a reusable chunk of node logic.
- World (Primitive) — a World asset that sets ambient lighting and the background; dragged into the viewport it replaces the current world, and it can equally be appended as a data-block.
- Scene (Primitive) — a complete Scene asset, with its cameras, lights, and linked objects; scenes preview by rendering the active camera in Solid mode (so they need an active camera), and dragging one into a window (other than the Asset Browser) imports or links the scene and makes it that window's active scene.
- Pose Action (Preset) — a Pose Asset built on an Action data-block; applying it loads the pose and lays it on the selected or active armature, shifting bone transforms while leaving the source action untouched.

The Current File Asset Library — to help manage assets in the current blend-file, set the Asset Browser to the Current File asset library; this always shows the current file's assets even when the file isn't saved in an asset library, and it lets you create and use assets in one file for small single-file projects. When the current file is part of an asset library you can of course also see its assets there; the ones in the current file carry an icon and are the only editable ones.

Life Cycle of an Asset — this section covers creating, editing, sharing, and using assets.
Creating an Asset — first make the thing you want to turn into an asset: the object, material, world, or your character's pose. The next step depends on the asset type (above). For primitive assets, use Mark as Asset, found in the data-block selector, the Outliner, and (for objects) the 3D Viewport's Object menu; it auto-generates a preview, which you can swap for an image of your own via the folder button beside the preview in the Asset Browser's Asset Details region.

For preset assets there's a dedicated button per type — for poses, a Create Pose Asset button in the Action editor; brush assets are made with Duplicate Asset from existing brush assets. Once an asset is made, be sure the current blend-file is itself saved inside your asset library; Blender won't copy the asset into the library for you.

Editing Assets — since assets are ordinary data-blocks with a little metadata attached, you can edit them as you would any Blender data — open the file and change the object, material, world, and so on. For pose assets it's the same — with the pose library file open, click Assign Action to assign the pose action to the selected armature, then use all the animation tooling to edit the pose, remove or add keys, and so on. Asset metadata is edited via the Asset Browser.

Sharing Assets — because assets simply live in blend-files, you pass them on by passing on their blend-file; just remember to bundle the Asset Catalog Definition File as well. There's currently no built-in way to pull selected assets out and save them (with their catalog definitions) into a separate blend-file — that could be an add-on.

Using Assets — assets are used from the Asset Browser. The pose library goes further, adding an Asset View to the 3D Viewport; see Use from 3D Viewport.

Removing Assets — asset metadata is erased with the Clear Asset operator, available in data-block selectors, the Asset Browser, and (for objects) the 3D Viewport menu.
Clear Asset — strips the asset metadata (catalog, description, author, tags), turning an asset back into a plain data-block; the usual removal rules then apply, so if a mesh object still sits in the scene, Clear Asset won't remove it from the scene (see Life Time). The preview stays inside the data-block rather than being removed.
Clear Asset (Set Fake User) — does the same as Clear Asset and then marks the data-block as protected, so it's no longer an asset yet won't be lost when the blend-file is saved.

Bundled Assets — Blender ships with many assets out of the box in the "Essentials" library, including: Hair node groups, the Smooth By Angle Node Group, and Brushes (Mesh Sculpt, Curve Sculpt, Texture Paint, Vertex Paint, Weight Paint).

Asset System Files (.asset.blend Extension) — some asset types can be edited without opening a blend-file inside an asset library; Blender saves these to libraries in special .asset.blend files, managed entirely by the asset system and holding a single asset plus its dependencies. You can still save a normal file with the .asset.blend extension — that won't be treated as an asset system file, since Blender tells the difference. Asset system files have one more quirk: you can open but not save them; Save As still works to spin off a new, normal blend-file from one, so the contained assets can't be edited without opening the file itself, and Blender shows clear warnings that asset system files can't be changed and saved the usual way. They're special because the asset system may need to regenerate them, which would lose any extra user changes — so to prevent that data loss they're protected from user edits. Currently only brush assets support this.

Design Limitations — Blender may not write to any blend-file other than the one currently open, or the special .asset.blend files above, so editing an asset means opening its blend-file — luckily just one click away, both in the Asset Browser's Source List region and in the asset context menu.

Future Development — this section sketches interesting directions for further work; though not exhaustive, it may clarify Blender's current Asset Browser functionality.
Non-Data-Block Assets — non-Blender assets like image or audio files will likely be supported in a future version, with their metadata kept in XMP sidecar files as other software does; importers (USD, glTF, FBX, …) could add their file types as assets this way too, and it should become possible to enrich an asset with a Python script that runs when the asset is used.
Cross Blend-File Editing — as noted, Blender itself may not write to blend-files other than the open one, which keeps complexity down (a reliable undo system is hard when manipulating other files) but gets in the way of mass-updating assets spread across blend-files. Since there's already tooling that edits blend-files outside Blender (see Blender Asset Tracer), an external tool for such cross-file edits is possible — perhaps via Blender's application templates system, or as an add-on, since the rule applies to Blender itself, not its add-ons.
Asset Pushing — Note: the Brush assets introduced in Blender 4.3 include support for the asset-pushing concept described here, which may reach more asset types later. Asset pushing means getting assets into the library while you're working on a file and want to copy an asset from it into the library. It looks deceptively simple, and sometimes is, but often turns complex: pushing an object into an external library — should it copy the materials too? The texture images those materials reference? Objects referenced by custom properties, constraints, or modifiers? And into which files? One big assets.blend, individual blend-files, or a directory per asset type? Blender shouldn't be making such calls for you.

For specific cases these are all solvable, which is why the pose library was built as an add-on enabled by default; studios with particular needs can disable it and build their own, since the building blocks all live in Blender's core and needn't be copied for this, and add-ons can write to other blend-files, so they can make the decisions for users.

Asset pushing is desirable, but because of the questions above it's unclear how to implement it well in a way that still leaves artists in control of their assets.

### Introduction

Below are a few preferences worth setting up front. See the Preferences section for the full list of settings. The shortcut Ctrl - Comma opens the Preferences editor quickly.

### Auto-Save Preferences

A fresh Blender install auto-saves preference changes by default, so you don't lose an edit by accident. To switch that off:

- Open the Preferences dialog

- Click the small menu at the lower left (the three-line icon)

- Clear the " Auto-Save Preferences " checkbox

- A " Save Preferences " button then appears at the dialog's lower left — click it, or the change won't be saved.

To turn auto-save back on, just repeat steps 1-3 and tick the box at step 3.

### Language

Enable Edit ‣ Preferences ‣ Interface ‣ Translation , then set the Language and pick what to translate among Interface , Tooltips and New Data .

See Language for details.

### Input

On a compact keyboard with no separate number pad, enable Preferences ‣ Input ‣ Keyboard ‣ Emulate Numpad . This hands you the 3D-view shortcuts normally bound to the number pad.

With no middle mouse button, enable Preferences ‣ Input ‣ Mouse ‣ Emulate 3 Button Mouse . This lets you hold the Alt or OSKey key and drag with the mouse to orbit.

See Configuring Peripherals for more about these options, and Input Preferences for details on configuring their settings.

### File and Paths

Under Preferences ‣ File Paths you can choose things like which Image Editor (GIMP, Krita…) and Animation Player to rely on.

The Temporary Directory picks where temporary renders, auto-saves, and the like are kept.

Tip

A leading // in a Blender path stands for the folder of the currently open blend-file, which is how relative paths are written.

See File Preferences for details.

### Save & Load

When you trust where your blend-files come from, you can enable Auto Run Python Scripts . The setting exists to shield you from malicious Python in blend-files received from someone else. Plenty of users leave it on, since advanced rigs often rely on scripts of some kind. Take care, though: it's a global switch, and it can let possibly malicious Python from an untrusted source run.

See the Save & Load Auto Run Python Scripts Preference.

### Introduction

Grease Pencil is a Blender object that takes drawing input, from a mouse or a pressure-sensitive stylus, and lays it down in 3D space as a set of points making up a stroke.

Use a Grease Pencil object for traditional 2D animation, cut-out animation, motion graphics, storyboarding, and more besides.

An illustration in 3D space using the Grease Pencil object.

You make strokes in Draw Mode, which needs a new keyframe on the Grease Pencil object's animation timeline. From there, Edit Mode and Sculpt Mode let you adjust strokes already drawn. Lastly, artists can layer materials, modifiers, lighting, and visual effects onto the strokes.

### Quick Start

Drop Grease Pencil into any existing Blender scene, or kick off from a 2D Animation template whose preset options are geared toward animation and storyboarding.

### Create and Use Grease Pencil

- From Object Mode, Add ‣ Grease Pencil ‣ Blank .

- Create a new keyframe or turn on Auto Key. (See Keyframe Editing)

- Switch to Draw Mode.

- Click and drag across the viewport to add strokes to the Grease Pencil object.

### 2D Animation Template
Spin up a new Blender file from the "2D Animation" project template through File ‣ New ‣ 2D Animation .

What the 2D Animation template sets up ahead of time:

- The active workspace defaults to 2D Animation.

- The world background colour (World Properties ‣ Surface) starts out white.

- Colour management uses the Standard view transform.

- The drawing plane is set to Front (X-Z).

- Line and Fill layers, along with some stroke materials, are configured for Grease Pencil.

- The animation timeline will automatically create a new keyframe when Grease Pencil is used on empty frames.

Tip

Grease Pencil can read pressure-sensitivity information from a Graphics Tablet or stylus.

### Introduction

Within Grease Pencil, Draw Mode is the mode that lets you draw in the 3D Viewport, and it is the only mode where new strokes can come into being.

You cannot select strokes already drawn while in Draw Mode; to edit them, drop into Edit Mode or Sculpt Mode instead.

3D Viewport Mode selector: Draw Mode.

Pick Draw Mode from the Mode menu in the 3D Viewport header. The moment it activates, the 3D Viewport Toolbar switches over to Draw Mode panels, and a circle matching the active material's color appears and trails the cursor around the 3D Viewport.

Making new strokes means grabbing one of the drawing tools from the Toolbar. The Draw tool is the go-to for free-hand work, but plenty of others handle drawing, area filling, and stroke erasing, and a few build primitive shapes such as lines, arcs, curves, boxes, and circles.

Toolbar has the specifics.

### Strokes Location & Orientation Controls

Drawing through a 3D space differs from drawing on a flat sheet. With Grease Pencil you must pin down where the new strokes sit and how they are oriented in 3D.

3D Viewport header Controls for strokes.

### Stroke Placement
Where new strokes land in 3D space is what the Stroke Placement selector decides.

Stroke Placement has more.

### Drawing Planes
Which plane (orientation) confines the new strokes is what the Drawing Planes selector decides.

Drawing Planes has more.

### Drawing Options

General drawing options.

Multiframe
Lets you draw across several frames at once.

Multiframe has more.

Additive Drawing
When a new frame is created and you add strokes with the drawing tools, the strokes from the previous or active frame come along as a foundation for the new one. Erasing existing strokes under Additive Drawing spawns a new keyframe.

AutoMerge
Stitches new strokes onto the start or end of strokes already drawn on the active layer.

Add Weight Data
Switch this on and new strokes gain weight data from the active vertex group and weight. With no vertex group chosen, none is written.

Handy in cut-out work, say, where you can drop a fresh drawing straight onto the existing vertex group rather than rebuilding it later.

Weight Paint Mode has more.

Draw on Back
With this on, new strokes go beneath every other stroke in the layer. Handy when you want to paint a fill material under a character's line strokes that share the same layer.

Sculpt Mode modifies drawing shape using a brush rather than individual elements; an area is altered using the brush's region of influence instead of selecting specific points.

**Sculpt Mode.**

Selected from the Mode menu in the 3D Viewport header. Once activated, the Toolbar changes to Sculpt Mode panels, and a red circle appears and follows the cursor in the 3D Viewport.

**Sculpting Options.**

Selection Mask — confines sculpting operations to picked points or strokes. Employ Toolbar selection tools for rapid selection; use Selection mode buttons to apply restrictions. Toggle modes via 1, 2, or 3.

Multiframe — sometimes simultaneous modification across multiple frames is needed. Activate the Multiframe control next to the modes selector (faded lines icon); consult Multiframe for guidance.

**Auto-Masking.**

Menu ‣ Header ‣ Auto-Masking; shortcut Shift+Alt+A. Automatically hides geometry per stroke, layer, and material beneath the cursor—shorthand for repetitive manual masking. Masks regenerate on each tool invocation and never render as visual overlays.

Access through Pie Menus via Shift+Alt+A. All auto-masking options compose, creating stricter masks.

Stroke — affects only the strokes under the cursor upon tool start.

Layer — affects only strokes belonging to the same layer as those under the cursor at tool start.

Material — affects only strokes sharing the material under the cursor at tool start.

Active Layer — affects only the current active layer's strokes.

Active Material — affects only strokes using the current active material.

**Keyboard Shortcuts.**

Invert stroke toggle — Ctrl.

Change active material — U.

Vertex Painting deposits color onto Grease Pencil object vertices, circumventing reliance on material base hues alone.

Upon painting a point, the deposited hue blends with the base material hue per brush configuration.

Note: a vertex in Grease Pencil is termed a point; both names are interchangeable.

**Vertex Paint Mode.**

Selected from the Mode menu in the 3D Viewport header. Once engaged, the Toolbar reformats to Vertex Paint Mode sections.

**Vertex Paint Options.**

Selection Mask — gates painting operations to picked points or strokes. Deploy Toolbar selection tools for rapid selection; gate painting to picked elements via the Selection mode toggle (switch with 1, 2, or 3).

Multiframe — sometimes concurrent modification across frames is required. Engage the Multiframe control next to the modes selector (faded lines icon); consult Multiframe for specifics.

Reference: Properties ‣ Modifiers

Grease Pencil features distinct modifiers. Modifiers perform automatic operations non-destructively. They let you apply effects that would otherwise require tedious manual work, without altering base geometry. Geometry Nodes can create custom Grease Pencil modifiers.

Modifiers change display and rendering but not editable geometry. Multiple modifiers stack on a single object; applying a modifier makes changes permanent.

Four modifier types exist: Edit—tools similar to Deform but affecting data like vertex groups rather than geometry directly. Generate—constructive tools that change appearance or add new geometry. Deform—shape changes without new geometry. Color—output color adjustments.

Interface: Each modifier shares fundamental interface components similar to mesh modifiers. See Modifiers Interface.

Applying Modifiers: Applying makes a modifier's effects permanent, converting strokes to match results and removing the modifier. Objects sharing data across multiple instances require Single User conversion, confirmed via pop-up.

Warning: Applying a non-first modifier ignores stack order, treating it as first; may produce unwanted results.

Reference: Properties ‣ Modifiers ‣ Modifier Header ‣ Specials

Apply (Active Keyframe): Ctrl + A—applies to current keyframe only. Apply (All Keyframes)—applies to all keyframes.

Note: Geometry Nodes can add layers; applying creates a single keyframe on frame one. Duplicated layer names deduplicate. Empty-name layers rename to Layer (Layer.001, etc. if needed).

Influence Filters: Most Grease Pencil modifiers share filtering options. Invert selection by clicking the icon beside each control. Layer/Group: Restricts to specified layer; click icon for layer-group filtering. Layer Pass: Restricts to matching Pass Index. Material: Restricts to specified material. Material Pass: Restricts to material matching Pass Index. Vertex Group: Restricts to assigned group. Custom Curve: Applies falloff curve controlling influence along stroke. Note: Filter availability depends on the specific modifier.

# Data Blocks, Introduction

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Data-Blocks; Introduction.

## Data-Blocks

The basic unit of any Blender project is the data-block. Meshes, objects, materials, textures, node trees, scenes, texts, brushes, and even Workspaces are all examples. A data-block is a generic abstraction over very different kinds of data, sharing a common set of basic features, properties, and behaviors. Some common traits:
- They make up the bulk of the blend-file.
- They can point at one another for reuse and instancing (child/parent, object/object-data, materials/images, and within modifiers or constraints too…).
- Within a blend-file, each type keeps its own unique names.
- They can be added, removed, edited, and duplicated.
- They can be linked between files (only for a limited set of data-blocks).
- They can carry their own animation data.
- They can hold Custom Properties.
Usually you interact with the higher-level data types (objects, meshes, etc.); managing data-blocks matters more on complex projects, especially when inter-linking blend-files, and the main editor for that is the Outliner. Not everything in Blender is a data-block — bones, sequence strips, and vertex groups, for instance, aren't — they belong to the armature, scene, and mesh types instead.

Data-Block Types — for reference, here are the data-block types stored in blend-files. Link means it supports being linked into other blend-files; Pack means its file contents can be packed into the blend-file (not applicable to most data-blocks, which have no file reference).
- Action (Link ✓, Pack —) — stores animation F-Curves; used as data-block animation data and in the Nonlinear Animation editor.
- Armature (✓, —) — a skeleton for deforming meshes; used as armature-object data and by the Armature Modifier.
- Brush (✓, —) — used as brush assets in sculpt and paint modes.
- Cache File (✓, —) — used by Mesh Cache modifiers.
- Camera (✓, —) — used as data by camera objects.
- Collection (✓, —) — groups and organizes objects in scenes; used to instance objects and in library linking.
- Curve (✓, —) — used as data by curve, font, and surface objects.
- Curves (✓, —) — the new curve data type (replacing Curve).
- Font (✓, ✓) — references font files; used by the curve object-data of text objects.
- Grease Pencil (✓, —) — 2D/3D sketch data for Grease Pencil objects; also overlay helper info in the 3D Viewport, Image, Sequencer, and Movie Clip editors.
- Grease Pencil v3 (✓, —) — as above, for Grease Pencil objects, with the same overlay uses.
- Image (✓, ✓) — image files; used by shader nodes and textures.
- Key (Shape Keys) (Link ✗, —) — geometry shape storage that can be animated; used by mesh, curve, and lattice objects.
- Lattice (✓, —) — grid-based lattice deformation; used as lattice-object data and by the Lattice Modifier.
- Library (✗, ✓) — a reference to an external blend-file; reached from the Outliner's Blender File view.
- Light (✓, —) — used as object data by light objects.
- Light Probe (✓, —) — helps achieve complex real-time lighting in EEVEE.
- Line Style (✓, —) — used by the Freestyle renderer.
- Mask (✓, —) — 2D animated mask curves; used by compositing nodes and sequencer strips.
- Material (✓, —) — sets shading and texturing render properties; used by objects, meshes, and curves.
- Mesh (✓, —) — geometry of vertices/edges/faces; used as mesh-object data.
- Metaball (✓, —) — an isosurface in 3D space; used as metaball-object data.
- Movie Clip (✓, Pack ✗) — a reference to an image sequence or video file; used in the Movie Clip editor.
- Node Tree (✓, —) — groups of reusable nodes; used in the node editors.
- Object (✓, —) — an entity in the scene with location, scale, rotation; used by scenes and collections.
- Paint Curve (✓, —) — stores a paint or sculpt stroke; reached from the paint tools.
- Palette (✓, —) — stores color presets; reached from the paint tools.
- Particle (✓, —) — particle settings; used by particle systems.
- Point Cloud (✓, —) — a collection of points in 3D space.
- Scene (✓, —) — the primary store of all displayed and animated data; top-level storage for objects and animation.
- Screen (✓, —) — low-level user-interface storage.
- Sound (✓, ✓) — a reference to sound files; used as speaker-object data.
- Speaker (✓, —) — sound sources for a 3D scene; used as speaker-object data.
- Text (✓, ✗) — text data; used by Python scripts and OSL shaders.
- Texture (✓, —) — 2D/3D textures; used by brushes and modifiers.
- Volume (✓, —) — volumetric objects that hold grids of data.
- Window Manager (✗, —) — the overarching manager for all of Blender's UI, covering Workspaces, the notification system, operators, and keymaps.
- Workspace (✗, —) — a UI layout; each window has its own workspace.
- World (✓, —) — defines global render environment settings.

Life Time — each data-block keeps a tally of how many users it has (a reference count); when there's more than one, the current count shows to the right of its name in the interface. As a general rule, Blender eventually removes unused data.

Since you add and remove plenty of data while working, this saves you from hand-managing every single data-block; it works by skipping zero-user data-blocks when writing blend-files.

Protected — because zero-user data-blocks aren't saved, sometimes you want to force data to stick around regardless of its users. If you're building a blend-file as an asset library to link to and from other files, you'll want to make sure those assets aren't accidentally dropped from the library file. To protect a data-block, use the shield-icon button beside its name; Blender then never silently deletes it, though you can still remove it by hand. Note: linked data can't be protected this way.

Name & Rename — data-block names are unique within their namespace, where a namespace is set by the type and the blend-file it lives in. So an Object and a Mesh can share a name, but two local objects in one blend-file can't; you can, however, have one local and several linked Objects sharing a name. Names have a fixed length of 255 bytes — 255 basic ASCII characters, or fewer with diacritics or non-Latin glyphs, since UTF-8 then often uses more than one byte per character. When naming a new data-block or renaming one, Blender checks for collisions; if a data-block of that name already exists, the (re)named one gets a numeric suffix on its "root name", like .001, using the first free index (up to 999, after which the suffix just keeps incrementing until no collision remains). If the suffix would make the name too long, the root part is trimmed as needed. Blender never renames a different data-block during automatic naming, so adding a new Cube object when Cube and Cube.001 already exist locally names the new one Cube.002.
You can rename local data-blocks yourself in a number of UI spots (the ID selection widget, the Outliner, and so on). On a name collision from the UI:
- If the new root name differs from the original, the renamed data-block takes the first free numeric suffix — e.g. with objects Sphere, Cube, and Cube.001, renaming Sphere to Cube yields Cube.002.
- If the new root name matches the original, the renamed data-block gets the requested name and the conflicting one is renamed instead — e.g. with Sphere, Cube, and Cube.001, renaming Cube.001 to Cube makes it Cube and turns the other into Cube.001.
Dot-Prefixed Names (Hidden Data) — data-block names beginning with a dot (.) count as hidden. Hidden data-blocks aren't shown in File Browsers by default, hide in most data-block selection menus, and are commonly used for internal, temporary, or helper data; the convention marks implementation details users shouldn't normally pick or edit directly. You can reveal them through preferences: enable Defaults – Show Hidden Files/Data-Blocks to show dot-prefixed data-blocks in File Browsers and data ID selectors, and Search – Show Hidden to show them in search menus. Even while hidden from the interface, a dot-prefixed data-block still acts like any other for linking, usage counting, and saving.

Sharing — data-blocks can be shared among others. Common cases: sharing textures among materials, sharing meshes between objects (instances), and sharing animated actions between objects (to dim all the lights together, say). Data-blocks can be shared across files as well; see linked libraries.

Making Single User — when a data-block is shared by several users, you can make one user its own copy by clicking the user-count button to the right of its name; this duplicates the data-block and assigns the new copy to that use alone. Note: objects have more advanced routes to single-user status — see their docs.

Removing Data-Blocks — as Life Time explained, data-blocks normally vanish once unused; you can also unlink or delete them by hand. Unlinking means a user stops using it, done by clicking the "X" icon next to a data-block's name; unlink it from every user and Blender eventually deletes it as above (unless it's protected). Deleting erases it from the blend-file outright, unlinking it from all users at once, done with Shift-LMB on the "X" icon. Warning: deleting some data-blocks can delete their users, which would be invalid without them — chiefly, deleting object-data (mesh, curve, camera…) also deletes every object using it. Both operations are also in the context menu when you RMB a data-block in the Outliner.

## Introduction

Every blend-file holds a database, and that database carries all the scenes, objects, meshes, textures, and so on in the file. One file can hold several Scenes, each Scene several Objects; objects can carry several materials, which can carry many textures. You can also build links between objects, or share data among them, and a file can link data from other Blender files.

Outliner — the easiest way to inspect your file's contents is the Outliner editor, which shows all of your blend-file's data. It also lets you do simple operations on objects — selecting, renaming, deleting, linking, and parenting. Read more about the Outliner.

Introduction to UV Unwrapping

Begin unwrapping when only minor geometry adjustments remain. Adding or subdividing faces after unwrapping is possible, but may require additional mapping or editing. You can use the UV texture image to guide further geometry changes.

Understanding UVs

Each UV map point corresponds to a mesh vertex. Lines between UVs correspond to mesh edges. Each UV face corresponds to a mesh face. UV mapping projects your 3D model's surface onto a 2D image.

A mesh face can have multiple UV textures, each with its own image. When you unwrap a face to a UV texture, the face gains four UV coordinates defining the image mapping. U and V axes distinguish these from 3D XYZ coordinates, hence "UV unwrapping". These coordinates work for rendering and real-time viewport display.

Each mesh face links to a potentially different image. UV coordinates control how that image maps to the face. A 3D Viewport requires Face Select mode to assign images or modify UV coordinates of the active mesh. This allows a face to participate in multiple UV textures — for example, a character's hairline face might use both facial and scalp/hair textures.

Getting Started

The default UV Editing workspace setup divides the screen between the UV Editor and 3D Viewport.

By default, meshes lack UVs. You must first map the faces, then edit them. Unwrapping happens in Edit Mode within the 3D Viewport, creating one or more UV Islands in the UV Editor.

Choose the UV Editing workspace from the top-screen selection list.

Enter Edit Mode (all unwrapping occurs in Edit Mode). You can work in vertex, face, or edge selection mode.

General Workflow

Different models may require different unwrapping approaches, but this is the general process:

Mark Seams if necessary.

Select mesh faces in the 3D Viewport.

Pick a UV mapping method from UV ‣ Unwrap or the 3D Viewport UV menu.

Adjust unwrap settings in the Adjust Last Operation panel.

Add a test image to check for distortion. See Applying Images to UVs.

Refine UVs in the UV Editor. See Editing UVs.

### Introduction

The geometry of a scene is constructed from one or more objects. These objects can range from lights to illuminate your scene, basic 2D and 3D shapes to fill it with models, armatures to animate those models, to cameras to take pictures or make video of it all.

Each Blender object type (mesh, light, curve, camera, etc.) is composed from two parts: an Object and Object Data (sometimes abbreviated to "ObData"):

Object
Holds information about the position, rotation and size of a particular element.

Object Data
Holds everything else. For example:

Meshes :

Store geometry, material list, vertex groups, etc.

Cameras :

Store focal length, depth of field, sensor size, etc.

Each object has a link to its associated object-data, and a single object-data may be shared by many objects.

### Introduction

Scenes organize your projects. A single blend-file supports multiple scenes,
which can exchange data such as objects, materials, and collections.

A scene establishes the rendered elements, active viewing angle, light arrangement,
and output parameters that comprise a production component.
For instance, a single blend-file might contain multiple scenes representing various shots,
light configurations, or workflow phases.

Scene administration and library connections are grounded in Blender's
Library and Data System.
Prior familiarity with data-block concepts, linking, and importing
is beneficial before proceeding.

### Scenes as Assets

Scenes can be flagged as Assets and applied in other projects.
This enables their display in the Asset Browser for reuse.

Scene assets serve as handy instruments for managing preset scene structures, illumination configurations, or compositional templates.
They retain all pertinent information (including cameras, lights, and output parameters) and can be moved into any accessible Blender
document.

When a scene asset is brought into another interface (excluding the Asset Browser alone),
Blender carries out one of the following operations:

- Link or Append: Incorporates the scene into the current blend-file as a linked or imported data-block.

- Activate: Establishes the added (or connected) scene as the presently operating one in the interface.

Scene assets generate preview visuals mechanically by rendering with the primary camera in Solid Display mode.
The scene must feature a designated camera for this to work.

Typical applications for scene assets encompass:

- Building replicable lighting or workspace configurations.

- Saving shot arrangements for multi-shot works.

- Maintaining consistent output parameters across documents.

- Creating foundational frameworks for new documents or teams.

### Scenes in the Video Sequencer

Scenes can also act as Scene Strips within the
Video Sequencer.
This allows combining or editing multiple scenes together in one playback sequence.

For illustration, individual frames of an animated sequence might inhabit separate scenes,
which are subsequently organized in a master scene employing scene strips to arrange them sequentially.
This technique proves valuable for multi-shot work, promotional content,
or arrangement tasks without demanding intermediate output stages.

When deployed as strips, scenes render dynamically through playback or output,
and they employ shared data-blocks unless produced as complete duplicates.

### Controls

Reference

Menu :

Topbar ‣ Scene

The Scene data-block interface in the Topbar
allows scene selection and construction.

Scene data-block menu.

Scenes
A catalog of available scenes within the current blend-file.

Add

New
Generates a fresh scene with default settings.

Copy Settings
Generates a fresh scene inheriting output and planetary settings from the current scene.

Linked Copy
Generates a scene that references all information from the original.
The fresh scene incorporates pointers to matching collections, objects, and data-blocks as the original.
Adjustments in one automatically reflect in the other, as they reference matching resources.

Full Copy
Generates an autonomous scene with independent copies of all elements and their data.
This approach proves useful for differing approaches or alternate renditions that should remain independent.

Note

Add Scene options control which information gets replicated and which gets referenced.
Objects reference Object Data like meshes or lights, and scenes can reference or reproduce this linkage.

(Delete Scene)
Deletes the active scene data-block.
Note that Blender mandates a minimum of one scene in a document; deletion of the sole scene is impossible.

### Introduction

Beyond modeling and animation, Blender provides video editing capabilities. Two approaches exist: the Compositor and the Video Sequencer (detailed in this section). The Video Sequencer is a full editing platform combining multiple video channels with effects. These tools create sophisticated edits, especially when paired with Blender's animation capabilities!

The Video Sequencer lets you arrange video clips end-to-end (or overlapped), add fades and transitions connecting clip boundaries, synchronize audio, and time the overall sequence. Use this with Blender's rendering power for complete production workflows.

Default Video Editing screen layout.

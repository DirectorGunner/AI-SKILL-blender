# Pose Library, Follow Track Constraint, Markers, Movie Clip Node ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Pose Library; Follow Track Constraint; Markers; Movie Clip Node; Cryptomatte Node (Legacy); Online Editing; Markup Style Guide.

## Pose Library

The pose library is built on the Asset Browser (see the Asset Libraries section), meant for Pose Mode — it only works while posing an armature, not for general object animation. It's implemented as an add-on, enabled by default (disabling it removes the pose library from the UI); the underlying building blocks live in Blender itself, while the add-on holds only the UI and the logic for what a pose asset stores — deliberately so an artist or studio can change that behavior with their own add-on. A pose asset is an action marked as an asset that contains exactly one frame of animation; usually made with the Create Pose Asset button, though any action keyed on a single frame qualifies. Each pose lives in its own action data-block, so it gets its own name, preview image, and Asset Catalog placement. Since it's just an action, a pose asset can also contain slots, so one asset can hold a pose for several armatures — when applied, the best-matching slot for the given armature is used, falling back to the first; for generic poses, single-slot actions are recommended so Blender always uses the only slot regardless of character, while a pose specific to two or more characters can be stored together for convenience (see Pose Creation for multi-character assets). Creating a pose library: a pose library is a set of actions in the blend-files of an Asset Library, made manually or by exporting poses; an exported pose gets a .asset.blend file containing just that asset, which can't be opened as a normal blend-file, while otherwise any number of pose assets can sit in one blend-file, and you can also link in a character, props, and so on, for creating poses and rendering previews. Pose creation: in the Action Editor, pose the character, pick the bones you want, and press Create Pose Asset (also in the 3D Viewport's Pose menu in Pose Mode), which makes a new pose action keying each bone's current location, rotation, scale, and Bendy Bone properties — it doesn't matter whether the character is animated, so you can make assets from existing animation, and you can even include bones from two or more armatures by posing them all, selecting the bones, and clicking the button (still one action, but with a slot per armature). Choosing the "Current File" library creates the action in the open file and marks it an Asset; another library extracts the pose into a new .asset.blend. A pose made in the current file can be renamed in the Asset Browser, where you can also right-click the thumbnail and choose Assign Action to assign it to the active object. (The Create Pose Asset button makes a new asset and tries to make the Asset Shelf visible in the 3D Viewport so you can tell something happened.) Pose creation by copying from another file: since Blender only writes to the open blend-file or to an .asset.blend, to copy a pose from another file into a library, pose the character and select the bones; click Copy Pose as Asset (in the Action Editor) to create the asset (with thumbnail) and store it in a temporary file; choose an existing pose asset, open its context menu, and click Open Blend File — a new Blender process opens the library file holding that pose (this applies to every asset type, not only poses); back in the Asset Browser, click Paste as New Asset to load that temporary file and all assets in it (here just one pose, though future versions may extend this, which is why the button is named generically); then name the pose and click the refresh button in the preview panel to render a new preview if wanted.

Continuing pose creation by copying: save the file and quit that Blender, and the original Blender still running notices the quit and auto-refreshes the Asset Browser to show the new pose. Controlling preview-image look: pose-library previews are rendered with the active Scene camera (preferred over rendering a specific 3D Viewport because there's only one active scene camera, making it predictable, and the camera and scene can be set up specifically for thumbnails, which is what pose-library files are for). Previews use the Workbench Engine, so switch the scene's render engine to it to expose options that affect the look, then select a pose asset and press Generate Preview to re-render with the current settings; you can even animate settings like MatCap rendering and light positions and intensities. Modifying a pose asset: a pose asset can be changed after creation, but only for assets in the current file or exported to an .asset.blend; the operator (right-click a pose asset) works on the active object — so it can't update from selected bones across multiple armatures and instead finds the best-matching slot, falling back to the first — with four modes: Adjust Pose (update existing channels from the selected bones without adding or removing any), Replace (fully replace all channels with the selected bones'), Add (add the selected bones' channels, updating existing ones), and Remove (remove the selected bones' channels). Using the pose library: it can pose one or more characters, using the current bone selection to decide which bones change; when editing several armatures, a matching slot is found per armature, and you can fully apply a pose or interactively blend it into the current pose, with behavior depending on where you use it (the Asset Browser or the 3D Viewport). From the Asset Browser: the Pose Library panels appear when the active object is an armature in Pose Mode, and the catalog system plus the top filter bar find specific poses. RMB on a pose gives — Apply Pose (apply it to the character, or only to selected bones if any, so you can make a "finger guns" pose by applying a fist to the hand then an "open hand" to just the index and thumb; double-clicking also applies it); Apply Pose Flipped (mirror left/right, e.g. apply a left-hand pose to the right hand to halve the number of poses, also useful for asymmetric facial expressions that depend on camera angle, and hold Ctrl while blending to blend the flipped pose); Blend Pose (gradually blend a library pose into the character's pose — click, then move the mouse left/right to set the blend; a pose can be "subtracted" by dragging left; Tab toggles between original and blended; LMB or Return confirms, RMB or Esc cancels; and pressing E for Extrapolate lets you apply over 100% to exaggerate); and Select/Deselect Pose Bones (select or deselect the bones used in the pose, e.g. to make a selection set or show what the pose covered). From the 3D Viewport: poses apply quickly from the Asset Shelf (the library previously lived in the Sidebar's Pose Library panel, which now just opens the asset shelf) — click a pose to apply it (one click is enough), select and apply via the cursor keys for fast exploration, or drag the thumbnail left to right to blend it into the current pose, releasing the mouse to confirm.

## Follow Track Constraint

The Follow Track constraint makes an object mimic a motion-tracking marker so it appears in the render where the marker appears in the tracked video. By default the object follows the marker's 2D motion on a plane in 3D, but it can instead follow the marker's reconstructed 3D position, which needs at least eight markers and a click of Solve Camera/Object Motion. (The Movie Clip Editor's Link Empty to Track button makes an Empty and assigns this constraint in one click.) Options: Active Clip (whether the marker is in the scene's Active Clip; unchecked, choose another clip); 3D Position (use the marker's reconstructed world position rather than its flat-video position); Undistort (use the marker's video position after compensating for lens distortion — see Lens settings — unavailable with 3D Position); Frame Method, for an aspect-ratio mismatch between footage and render — Stretch (positioned as if the video were stretched to match the render), Fit (as if the video were enlarged as much as possible while keeping its aspect ratio and fitting inside the render on both axes), or Crop (the same but fitting on one axis); Object (the physical object holding the marker — see the Movie Clip Editor's Objects panel — and if empty, Track lists the markers used to reconstruct the camera); Track (the marker to follow); Camera (the Blender camera in whose view the object should appear; empty uses the scene's active camera); Depth Object (project the constrained object onto this object's surface, useful for a facial-makeup effect; unavailable with 3D Position); Constraint to F-Curve (replace with keyframes); and Influence. (The Movie Clip Editor's Set as Background button sets the video as the camera background, resizable via the same Frame Method in the camera's Background Images panel.)

## Markers

Markers denote frames with key points or significant events in an animation — a character's animation starting, the camera moving, a door opening — and can be named for quick legibility; they're available in many editors. Unlike keyframes, markers always sit on whole frame numbers (no frame 2.5). They can be created and edited in the Graph Editor, Dope Sheet, NLA Editor, and Video Sequence Editor, and a marker made in one appears in all the others that support them. Types: besides standard markers, pose markers are specific to armatures and shape keys, denoting poses in the Dope Sheet's Action Editor and Shape Keys Editor modes. Visualization: when at least one exists, markers show in a separate bottom row, which can be disabled per editor via View ‣ Show Markers (while disabled, the marker operators are unavailable and the header's Marker menu is hidden). Standard markers are small white triangles (empty if unselected, filled if selected) with a dashed line spanning the editor height at that frame, with any name in white to the right. The 3D Viewport can't create, edit, or remove markers but shows a marker's name in the upper-left Object Info when on its frame. Pose markers show a diamond icon in the Dope Sheet and a red dashed line inside the relevant action strip in the NLA editor. Add Marker (All modes; Marker ‣ Add Marker; M): move to the frame and press M (markers can also be added during playback); with Show Pose Markers on, a pose marker is added. Selecting (All modes; LMB): click a marker's triangle to select it, Shift-LMB for several; in the Graph Editor, Dope Sheet, NLA Editor, Timeline, and Video Sequence Editor you can also select all with A while hovering the marker row and use tools like Box Select (LMB to select, RMB to deselect), found in those editors' Select menu. Editing — Duplicate Marker (All modes; Marker ‣ Duplicate Marker; Shift-D): Shift-D duplicates the selected markers, leaving the copies in select mode for placement — note that, unlike most Blender duplications, the names aren't changed (no ".001" suffix). Duplicate Marker to Scene (Marker ‣ Duplicate Marker to Scene…) copies them into another scene. Delete Marker (Marker ‣ Delete Marker; X): press X and confirm. Rename Marker (Marker ‣ Rename Marker; F2): select a marker, press F2, type the name, and press Return. Move Marker (Marker ‣ Move Marker; G): with markers selected, press G while hovering the marker bar to move them (confirm with LMB or Return, cancel with RMB or Esc), or drag with LMB — by default in one-frame steps, or in 1-second steps (per the scene FPS) while holding Ctrl. Select (Marker ‣ Select): All (A, select all), None (Ctrl-A, deselect all), Invert (Ctrl-I), Before Current Frame (all to the left plus the one on the current frame if present), and After Current Frame (all to the right plus the current-frame one). Show Pose Markers (Dope Sheet, Action Editor or Shape Keys Editor mode; Marker ‣ Show Pose Markers) shows the active action's markers instead of scene markers. Make Markers Local (Marker ‣ Make Markers Local) converts standard markers into pose markers, removing the original (duplicate first to keep it). Jump to Next/Previous Marker (Marker ‣ Jump to Next/Previous Marker) moves the playhead to the next or previous marker.

Bind Camera to Markers (All modes; Marker ‣ Bind Camera to Markers; Ctrl-B) uses markers to switch the active camera to the active object. To use it, select the object to become the active camera and a marker to bind it to (if no marker is selected, one is added) — when bound, the marker is renamed to the active object and gets a camera icon to its left to distinguish it from informative markers, and moving the marker changes the frame at which the active camera switches to that object.

## Movie Clip Node

The Movie Clip node draws values from footage cameras and tracking and links them to its outputs — image sequences can be loaded, but only the Image and Alpha values are available then, since the other outputs have no associated values, while a tracked clip lets Blender fill the outputs from internal tracking values (with the start/end frames defined in the Movie Clip editor). It has no input sockets. Properties: Movie Clip (select the clip; for controls see the Data-Block Menu). Outputs (the first two are the minimum): Image (the whole image in the specified color space), Alpha (the alpha from the movie or image), Offset X and Offset Y (the X/Y offset from the footage camera or tracking), Scale (the image scale from them), and Angle (the lens angle from them).

## Cryptomatte Node (Legacy)

The Cryptomatte (Legacy) node uses the Cryptomatte standard to efficiently build mattes for compositing — Cycles and EEVEE output the needed render passes, which the Compositor (or another Cryptomatte-aware compositor) uses to mask chosen objects. In contrast to the Material and Object Index passes, you choose the objects to isolate during compositing, and the mattes are anti-aliased and account for motion blur and transparency. Important: the Legacy node is deprecated in favor of the Cryptomatte Node and will be removed in a future release. Inputs: Image (standard color input) and Crypto Passes (each crypto layer gets its own render pass that must connect to one of these layer inputs — four by default; see Adding/Removing Layers for more). Properties: Add/Remove (add or remove an object or material from the matte by picking a color from the Pick output) and Matte ID (the list of object/material crypto IDs to include — usable to clear all mattes by deleting the text, or to paste IDs from other software). Outputs: Image (a colored output with the matte applied to include only selected layers), Matte (a black-and-white alpha mask of all selected crypto layers), and Pick (a colored representation of the Cryptomatte pass, used with a Viewer node to choose which passes build the matte). Usage: enable the Cryptomatte Object render pass in the Passes panel and render; in the compositing nodes, make a Cryptomatte node and link the matching Render Layer Image and Cryptomatte passes; attach a Viewer to the Pick output; use the Add/Remove button to sample objects in the Pick Viewer; then use the Matte output for the alpha mask. Adding/Removing Layers: there are four crypto layers by default — add or remove inputs via Sidebar ‣ Item ‣ Properties ‣ Add/Remove Crypto Layer, which add or remove layers from the bottom of the pass inputs.

## Online Editing

This page explains how to contribute to Blender's documentation through the online editing workflow — whether fixing typos or adding whole sections, your contributions are valuable. Getting started: first create an account at projects.blender.org via the "Sign In" button, then you can edit straight from your browser once logged in. Finding the page to edit: go to the Blender Manual (docs.blender.org/manual) and browse to the page you want to improve (make sure you're under the development version, /dev), and click the "Edit Page" link at each page's top-right, which opens the online editor at projects.blender.org. Making changes: after clicking "Edit this page" you'll see the page source in a text area — Blender's docs use reStructuredText (RST) — and you can correct typos or grammar and add missing details or better explanations (see the Markup Style Guide for formatting help). Previewing your changes: the online editor currently has limited preview support, so double-check your formatting and consult similar existing pages. Committing your changes: at the bottom of the page, write a clear, concise summary in the commit message box (e.g., "Fixed typo in Sculpting documentation") and select "Commit Changes," which then guides you to open a Pull Request for review. Pull requests and reviews: your commit is sent as a pull request reviewed by the documentation team, who may suggest improvements — stay engaged and watch your email or projects.blender.org notifications to respond promptly; once approved, a reviewer merges it and your contribution goes live. Best practices: keep edits focused (one topic per PR), write specific commit messages, and respond promptly, since active communication speeds reviews. Getting help: if unsure about a change, formatting, or workflow, ask — join the Blender Chat #docs channel or open an issue at the documentation project for broader or complex questions.

## Markup Style Guide

This page covers conventions for writing Blender's documentation in reStructuredText (RST) markup, which keep the docs clear, consistent, and easy to maintain. General conventions: use three-space indentation; keep lines to 120 characters; use italics for button and menu names; avoid Unicode characters unless strictly necessary; prefer simple sentence structures; and avoid heavily wrapped text, favoring shorter paragraphs and clear sentences. Headings — use this hierarchy:
```text
#################
Document Part
#################

****************
Document Chapter
****************

Document Section
================

Document Subsection
-------------------

Document Subsubsection
^^^^^^^^^^^^^^^^^^^^^^

Document Paragraph
""""""""""""""""""
```
Each .rst file should have only one chapter heading (*), and Parts only on contents or index pages. Basic text styling:
```text
*italic text*
**bold text**
``literal text`` (e.g., filenames, Python code snippets)
```
Interface elements: `:kbd:`LMB`` for keyboard/mouse shortcuts, `*Mirror*` for interface labels (buttons, panels, etc.), and `:menuselection:`3D Viewport --> Add --> Mesh --> Monkey`` for menu navigation paths. Lists — bullet, numbered, and definition:
```text
- First item
- Second item
- Third item
```
```text
#. First step
#. Second step
#. Third step
```
```text
Term
   Definition text here.
```
Useful constructs: `|BLENDER_VERSION|` inserts the version number (e.g. "4.5"); `|BLENDER_VERSION_LABEL|` inserts the version label (e.g. "4.5 LTS"); `:abbr:`SSAO (Screen Space Ambient Occlusion)`` shows the full text on hover; `:term:`Manifold`` links to the Glossary entry; and `:bl-icon:`icon_name`` inlines a Blender icon (full list at Icons). Cross-references and links — internal doc links, explicit section labels, implicit same-document references, and external links:
```text
:doc:`Link Title </path/to/page>`
```
```text
.. _my-section-label:

Section Title
=============

Reference this section later with :ref:`Optional Title <my-section-label>`
```
```text
Section Title
=============

Reference it implicitly later using `Section Title`_
```
```text
`Blender's Official Website `__
```
Context-sensitive manual access — to link Blender UI properties and operators to manual entries: right-click the property/operator in Blender and choose Online Python Reference to get the RNA tag (shown in the OS console), then use an external reference matching that RNA tag:
```text
.. _bpy.types.FluidDomainSettings.use_fractions:

Fractional Obstacles
   Enables finer resolution in fluid/obstacle regions.
```
For operators:
```text
.. _bpy.ops.curve.subdivide:

Subdivide
=========
```
Blender uses these tags to link UI elements directly to documentation entries via the "Online Manual" option. Admonitions — special blocks highlighting notes, warnings, or extra information; common types are note, tip, important, warning, caution, and seealso, created like:
```text
.. note::

   This is a note for general information.
```
Swap note for any other type in the list. Images — use the figure directive with captions:
```text
.. figure:: /images/interface_splash_current.webp

   Splash screen of Blender.
```
Screenshots guidelines: use Blender's default theme and settings; zoom to maximum (Ctrl-MMB or NumpadPlus); zoom out exactly eight steps (NumpadMinus pressed eight times); and leave about a 30-pixel margin around the content where applicable. File naming: lowercase letters, no spaces, underscores between sections and dashes within multi-word sections; place images only in manual/images (no subfolders) — e.g. interface_splash_current.png, modeling_meshes_edit-mode.png. Image formats: .png for interface screenshots or solid-color images; .jpg for photos or high-color-variation renders; avoid .gif, using embedded videos for animations instead. Videos — embed videos hosted on Blender's PeerTube at video.blender.org:
```text
.. peertube:: ID
```
The ID comes from the video URL, e.g. for https://video.blender.org/videos/watch/47448bc1-0cc0-4bd1-b6c8-9115d8f7e08c the ID is 47448bc1-0cc0-4bd1-b6c8-9115d8f7e08c. Guidelines for videos: prefer videos without spoken or on-screen text for easier translation, and don't rely on videos alone — the manual text should clearly document the process. Code samples — use syntax highlighting and optional line numbering:
```text
.. code-block:: python
   :linenos:

   import bpy

   def example_function():
       print("Hello Blender")
```
Placeholders and editor notes — for content needing later updates: reader-visible todo or internal (hidden) notes:
```text
.. todo:: Complete this section when feature is finalized.
```
```text
.. Internal developer reminder goes here
```
Further reading: the Sphinx RST Primer (an introduction to RST syntax) and the Docutils reStructuredText Reference (comprehensive RST markup documentation).

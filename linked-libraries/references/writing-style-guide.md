# Writing Style Guide, Documenting New Features And Changes, Style Guide, Asset Browser

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Writing Style Guide; Documenting New Features and Changes; Style Guide; Asset Browser.

## Writing Style Guide

Primary goals — the manual aims to be: User Focused (written for people educated in computer graphics who grasp 3D basics and/or know other 3D software, yet kept understandable to non-technical users even where the topic is highly technical); Complete (a detailed functional description of every feature, tool, and option — though not every tiny detail, since each key area has a canonical source of truth; cover what a feature is, how to use it, and its purpose, adding background only when needed for deeper understanding of a 3D pipeline); Concise (computer graphics is full of rules, exceptions, and interesting details, but expanding into them adds unnecessary content, so keep the text concise and relevant to the end user); and Maintainable (Blender releases often, so write content that won't need redoing the moment a small change lands, which also helps a small documentation community keep up). Content guidelines — keep this page in mind and deviate only with good reason; when in doubt, check with the documentation team on Blender Chat. Rules of thumb: spell-checking is strongly recommended; use American English (modeling not modelling, color not colour, and number formatting like 2,718.28 not 2 718,28); mind grammar, wording, and simple English; keep sentences short and clear; explaining why or how an option is useful is a good idea; if unsure how a feature works, ask someone or find and ask its developer; and wrap RST files at column 120, with no line exceeding it. To be avoided: first-person writing, your own opinions, weasel words, and needless vagueness (e.g. "Reloading the file will probably fix the problem," "Most people do not use this option because…"); specific, quickly-outdated details (e.g. "Blender has 23 different kinds of modifiers," "Enabling previews adds 65536 bytes to each blend-file unless compressed"); documenting bugs (Blender fixes hundreds between releases, so the manual can't keep up — known unresolved issues can be documented as Known Limitations or in troubleshooting); product placements or promoting software/hardware brands (keep content vendor-neutral); mathematical/algorithmic implementation details when a simpler explanation exists (e.g. mesh-smoothing internals are unnecessary, but a Mix node's blend types do need a mathematical explanation); repeating large blocks of text (explain once, then refer back, and for general terminology define a :term: in the glossary); listing every menu option such as frame rates (summarize or omit, since such lists only restate the interface and are a lot to read and maintain); documenting release-to-release changes (that's what release notes are for — document only Blender's current state); naming a value's unit unless it's obscure and unpredictable; and copying Blender's tooltips verbatim (people come to the manual to learn more than the UI offers — as a last resort, add a comment, hidden from the HTML but useful to editors):
```text
.. TODO how does this tool work? ask Joe Blogg.
```
Glossary — for the Glossary section defining common Blender and computer-graphics terms: define the term before any further information; avoid constructs like "it is" or "xyz is" before the definition; don't repeat the term immediately or use it in its own definition; don't add terms absent from Blender's interface or the manual; avoid overly long entries (supplement complex terms with external links); avoid duplicating documentation (if explaining the term is another section's main focus — e.g. a tool name — just link there, or skip the glossary entry); and put URL references at the end, e.g.:
```text
See also `OpenGL `__ on Wikipedia.
```
Examples — this entry:
```text
Displacement Mapping
   Uses a grayscale heightmap, like Bump Mapping,
   but the image is used to physically move the vertices of the mesh at render time.
   This is of course only useful if the mesh has large amounts of vertices.
```
would instead be written definition-first:
```text
Displacement Mapping
   Distorts vertices with an image.
   Similar to Bump Mapping, but operates on the mesh's geometry.
   The mesh must have enough geometry.
```
And this entry:
```text
Doppler Effect
   The Doppler effect is the change in pitch that occurs
   when a sound has a velocity relative to the listener.
```
would be written to avoid the immediate repetition of the term:

```text
Doppler Effect
   Perceived change in pitch that occurs
   when the source of a sound is moving relative to the listener.
```
This entry:
```text
Curve
   It is a class of objects.
   In Blender there are Bézier curves and NURBS curves.
```
would be written to avoid the "it is":
```text
Curve
   A line interpolated between Control Vertices.
   Common types include Bézier and NURBS.
```

## Documenting New Features and Changes

Every Blender release brings new features, improvements, and changes, and the documentation must be updated in parallel so users can make the most of them. The documentation project tracks changes that need manual updates or additions; by contributing, you keep the manual accurate and valuable for the global community. This guide walks through documenting changes using release issues and commit logs. Using release issues to track changes — each release has an issue in the documentation project's Upcoming Releases Project, containing a curated list of code commits that introduce user-facing changes typically needing manual updates such as new sections, modified instructions, or updated screenshots. Steps to contribute: (1) Locate the release issue — open the issue for the current or upcoming release in the documentation project's tracker, and review the commits listed in its description, each representing a change or feature needing documentation. (2) Pick a commit — choose one that interests you or matches your expertise (e.g. if you know modeling tools, pick a modeling change), and check the comments or status to be sure no one else is already on it. (3) Understand the change — read the commit message (it often summarizes the change's purpose and scope and may link to a PR or discussion), check the PR or code (the linked PR adds context via descriptions, images, or videos, and reviewing the code clarifies how the feature works), test the feature (open Blender and try it to see how it behaves and how users will interact with it), and reach out if needed (if the message or PR lacks detail, contact the change's developer — usually named in the PR — or ask on Blender's development channels or forums). Key considerations for documentation: What's the purpose? (understand why the change was made — usability, a new capability, or a fix); Who benefits? (the target audience — animators, modelers, or another group); How does it work? (write clear, concise instructions with practical examples or use cases); Look for dependencies (some changes depend on or affect other features — check whether the manual is impacted elsewhere); and Screenshots and visuals (capture screenshots for interface changes, reflecting the correct Blender version). Submitting your work — once drafted: write in the manual style (follow the style guide for clarity and consistency); submit your contribution (open a pull request in the documentation project, referencing the release issue and commit in the description, and include any screenshots, diagrams, or examples); and collaborate (work with the review team to refine the documentation until it's ready to publish). Every contribution matters — documenting these changes supports the community and helps users understand the latest features, making Blender more accessible and enjoyable; start exploring the release issues and help bring Blender's innovations to life.

## Style Guide

This page covers conventions for translations. Note: readers are expected to use the English version of Blender, not a translated one, and the translations are licensed under the same License as the original. Should I translate…? — Maybe: Hyperlinks (translate only as an addition, not a replacement — leave the original link text in place and add the translation next to it; see also Adding Text); Technical Terms (translate only if the localized expression is commonly used and well understood, otherwise keep the English term; see Technical Terms); Unclear Text (if unsure you understood the meaning, mark the text fuzzy and/or add a translator comment so another translator can clarify); and UI Elements (use the same translation as Blender's interface, or, if the element isn't translated yet, keep the English term and add the translation in parentheses). Never: Images (you likely won't find the original scene for a screenshot of a file, and it's too much server load — and work — for you). Technical terms — computer-graphics terms are often new or outright neologisms coined as needed, so they don't always have a translation in your language, and many users run Blender's English interface; therefore, unless a term has an obvious translation, prefer the English one in italic, and you can adopt a translation to use occasionally (e.g. to avoid repetition) — and the reverse holds too: even when a term translates cleanly, use its English form now and then so the reader grows used to it. If a term truly can't be translated, just keep the English one, but ensure its glossary entry is translated. In the glossary the English term comes first (to keep alphabetic order), with the translated entry following in parenthesis where appropriate. Adding text — generally translate exactly what the text says and avoid adding updates or extra information, but sometimes extra information is necessary, for instance when the text discusses the manual itself: a foreign reader may not realize they can contribute English text only, though that's obvious to an English reader, so in these rare cases you can and should add extra information. Keeping pages up to date — when the manual updates, outdated translations are marked fuzzy; to track them, use the tool created for that task (see How to install it).

## Asset Browser

The Asset Browser is the principal interface for organizing and using assets. To open it, make a new area, click the Editor Type button at its top-left, and pick Asset Browser.

See also: Asset Libraries (general information on Blender's asset-library system, including creating and editing assets, and design rationale), Asset Catalogs (for organizing assets), and Pose Library (built atop the Asset Browser).

Interface — Header — Import Settings:
Import Method — decides how data is handled when an asset is brought in. It sits in the middle of the Asset Browser header whenever an asset library other than Current File or Essentials is active.
  Follow Preferences — uses the import method chosen in the File Path Preferences.
  Link — the asset is linked into the current blend-file and stays read-only; later edits to the asset file propagate to every file that links it.
  Append — the asset and all its dependencies are copied into the current file. Drag a material in three times and you get three independent copies; the same goes for an object. Here "dependencies" means everything the asset relies on — for an object that can be its mesh and materials, but also other objects pulled in by modifiers, constraints, or drivers. Because the file now owns its own copy, later edits to the asset file won't show up in the file it was appended into.
  Pack — imports the asset as linked data and packs it into the current blend-file right away, so it stays available even if the original library data changes or goes missing; handy for keeping self-contained files that don't lean on external asset-library paths.
Instance Collections – When Linking/Appending — mirrors the Instance Collections option used when appending from the file browser. Some asset types, collections among them, can be made as an instanced collection (by switching on the Instance option once collection assets have been dragged into the 3D Viewport): with these options on, an empty object is added that instances the collection, whereas with them off the whole collection hierarchy is dropped into the scene. Collection assets from the current file are always instanced.

Display Settings — tune how assets appear in the list.
Display Mode — controls how files are shown. Horizontal List lays files and folders out in a horizontal list; Thumbnails shows previews.
  Preview Size (Horizontal List) — resizes the thumbnails in list views.
  Column Size (Horizontal List) — the column width in horizontal list views.
  Size (Thumbnails) — resizes the preview thumbnails.
Sort By:
  Name — orders the list alphabetically.
  Asset Catalog — groups assets from the same catalog together, ordered by name within each catalog, with the catalogs following the flattened catalog hierarchy.

Main Region — the central area lists the assets held in the chosen catalog. Click LMB to pick one asset; add Ctrl to add or remove an asset from the selection, or Shift to grab a range; you can also drag LMB for a box select. Its context menu offers:
  Refresh Asset Library (R) — refreshes the list.
  Clear Asset — see Removing Assets.
  Clear Asset (Set Fake User) — see Removing Assets.
  Open Blend File — opens the blend-file holding the asset.
  Display Size — resizes the preview thumbnails.

Asset Library Region — the left-hand region lets you choose an asset library and shows its catalogs; toggle it with T.
  Asset Library — which library's catalogs to display. All Libraries shows catalogs from every available library; Current File shows the catalogs in the current blend-file (even before it joins an asset library — see The Current File Asset Library); Essentials shows the catalogs bundled with Blender. Any libraries you added in the File Path Preferences appear here as well.
  Copy Bundle to Asset Library — appears when Asset Library is Current File and the open blend-file is an asset bundle not yet part of a library. It lets you choose a target library, then opens a File Browser at that library's root folder so you can save the file there; once saved, its assets join the library.
  Catalogs — a Tree View of the selected library's catalogs. A catalog is a group of assets; selecting one limits the listing to the assets in that catalog and its children. Double-click to rename a catalog, or drag and drop to reparent it. Add-ons and features such as the Pose Library can add custom panels here.

Asset Details Region — the right-hand region shows the active asset's metadata; toggle it with N or the gear icon in the header. Only metadata for assets stored in the open blend-file may be edited.
  Name — the asset's name; it stays unique per asset data type inside a single blend-file.
  Source — the complete path of the blend-file the asset lives in.
  Open Blend File — opens that blend-file in a fresh Blender instance; closing that instance refreshes the Asset Browser automatically.
  License — an optional name for the license the asset is distributed under; Blender itself makes no use of it.
  Copyright — an optional copyright notice; Blender itself makes no use of it.
  Description — an optional asset description; Blender itself makes no use of it.
  Author — an optional field naming the asset's author; Blender itself makes no use of it.

Preview — shows the asset's preview image (see Asset Previews).
  Load Custom Preview — opens a File Browser to pick a new image for the preview.
  Generate Preview — auto-creates a fresh preview for the asset.
  Preview — a menu of extra preview operators.
  Render Active Object — builds a preview from the 3D Viewport's active object, useful for node groups, which can't generate their own preview automatically.
  Remove Preview — strips the asset's preview.
  Capture Screenshot Preview — drag-select a rectangle over part of Blender to grab it as the asset's preview image (see Screenshot Capture for Previews).

Tags — a panel for viewing and editing an asset's tags. Tags mean nothing to Blender and are yours to choose freely; when you filter assets with the search field, those whose tags partially match the term are pulled in too.
Note: more panels may appear depending on the object's current mode and the selected asset types — see Pose Library, for example.

Using Assets — broadly, you use an asset by dragging it from the Asset Browser to wherever you want it. Objects and worlds drag into the scene; materials drag onto the object meant to wear them; geometry nodes drag onto objects to attach a Geometry Nodes Modifier. Pose assets behave differently and are covered in Pose Library.

Dragging a collection adds it as an instance — a single object standing in for the whole collection, so its contents stay out of the Outliner and can't be edited. Two ways to change that:
Run Make Instances Real to swap the object for the collection's actual contents.
Or delete the object, locate the collection in the Outliner's Blender File display mode, and choose Link to Scene from its context menu.

What happens when an asset is used depends on the Import Method. Note that once the asset is in the current file, every ordinary Blender operation becomes available — you might, say, link an object into the scene (which links its mesh and materials too), then make just the object local via Object ‣ Relations ‣ Make Local… ‣ Selected Objects while leaving the mesh and materials linked to the asset files. The result is a local, editable object whose mesh and materials still track any changes in the asset library.

Asset Previews — preview images are usually generated on their own when you flag a data-block as an asset. Objects are shot from their local -Y axis, collections from the global -Y axis (since they have no local axis). If the auto-generated preview falls short, you can swap in a custom one. For pose-asset previews, see Controlling the Look of Preview Images.

Screenshot Capture for Previews — when a particular preview is wanted, a screenshot is a quick route. The operator lives under the Preview popover (see Capture Screenshot Preview). Screenshots are only possible for editable assets, i.e. those in the Current File and Asset System Files. Once it starts, click and drag a rectangle over any portion of Blender to grab a preview image; while dragging you can shift the whole capture area or unlock its aspect ratio (the status bar's shortcut help lists the keys). Re-running the operator remembers the area you grabbed last, so a single click repeats the same screenshot.
Note: choosing an area that falls entirely inside one 3D viewport actually performs a background render of that section, which permits a transparent background but also means UI elements can't be captured.

Asset Bundles — these are blend-files that reference no other file and whose names end in _bundle.blend; any textures and other external files must be packed into the blend-file itself. You can copy an asset bundle into an asset library through the Asset Browser:
Open the asset-bundle blend-file.
Set its Asset Browser to Current File if it isn't already.
Click Copy Bundle to Asset Library.
Pick the library to copy it into.
A File Browser opens at that library's root folder; choose where the blend-file should go and click the Copy to Asset Library button.
The file is saved at your chosen spot, and any of the bundle's catalogs are folded into the target library.
Note: the words "asset" and "bundle" both see broad use, and not always with the meaning given here. Not everything billed as an "asset bundle" offers the Copy to Asset Library function — for that, the file has to meet the definition above.

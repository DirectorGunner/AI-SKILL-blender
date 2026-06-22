# Display Mode, Sequencer Preview Overlays, Header, Toolbar ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Display Mode; Sequencer Preview Overlays; Header; Toolbar; Channels; Display; Cache; Proxy; Asset Catalogs.

## Display Mode

This pop-up lets you switch between showing the preview image and showing a scope that visualizes its color distribution.

Image Preview — previews the final video's look and lets you change the image layout with the various tools.

Luma Waveform — this scope plots the image's luminosity (brightness) distribution, so you can tell at a glance whether there's enough contrast and whether any areas are under- or overexposed. It works by drawing a curve for each scanline of the current video frame; put another way, each pixel column of the luma waveform is a brightness histogram of the matching pixel column in the frame. Specifically:
- A waveform pixel's horizontal position refers to a pixel column in the frame.
- A waveform pixel's vertical position refers to a brightness value, 0 at the bottom up to 1 at the top.
- A waveform pixel's brightness shows how many pixels in that frame column carry that brightness; with none, the waveform pixel is black, and with at least three, it's white.
When this scope is active, you get one option under Sidebar ‣ View ‣ View Settings. The examples show two images and their luma waveforms: in the first, the waveform's horizontal lines line up with the picture's uniform-colored lines (the one-pixel "gray 20%" line inside the yellow strip reads as a gray line, the two lines forming an "X" come from the two monochrome gradients, and the broken line matches the colored gradient at the bottom); in the second the curves are clear, with a luma of 80–100% for the sky, around 40% for the sea, and 10–20% for the mountains, rising near 40% on the sunny part.

RGB Parade — shows three waveforms, one each for the red, green, and blue channels, instead of a single one for overall brightness.

Chroma Vectorscope — plots the image's color distribution, each point carrying an angle for its hue, a distance-from-center for its saturation, and a brightness for how many frame pixels share that hue and saturation.

Histogram — shows three overlapping graphs, one per channel; within each, the X axis runs from 0 at the left (black) to 1 at the right (fully red/green/blue) for color intensity, and the Y axis is the pixel count. Use it to balance an image's tonal range — a well-balanced image shows a nice smooth spread of color values.

## Sequencer Preview Overlays

Reference — Location: Header ‣ Overlays.

Clicking Show Overlays toggles every overlay in the Video Sequencer. The drop-down opens a popover of finer settings below.
Image Outline — draws an outline around the selected images.
2D Cursor — shows the 2D Cursor.
Frame Overlay — shows the Frame Overlay for comparing the current frame to a reference frame.
Safe Areas — shows guides marking the video area visible across all screens. See also Camera Safe Areas.
Metadata — shows file metadata.
Annotations — shows Annotations.

## Header

View Menu:
Toolbar (T) — shows or hides the Toolbar.
Sidebar (N) — shows or hides the Sidebar.
Tool Settings — shows or hides the active tool's settings.
Footer — shows or hides the Footer.
Preview During Transform — shows a preview of a strip's start or end frame while you transform its matching handle.
Refresh All — pulls external files in afresh and rebuilds the current frame's preview, handy when you changed an external file or made a scene change Blender didn't notice.
Frame Selected — pans and zooms onto the selected image.
Fit Preview in Window (Home) — pans and zooms so the whole video is visible; this turns on Zoom to Fit.
Zoom — a menu of handy zoom levels and operations, figured from image resolution against screen resolution: 12.5% (1:8) Numpad8 out to 12.5%; 25% (1:4) Numpad4 to 25%; 50% (1:2) Numpad2 to 50%; 100% (1:1) Numpad1 back to 100%; 200% (2:1) Ctrl-Numpad2 in to 200%; 400% (4:1) Ctrl-Numpad4 to 400%; 800% (8:1) Ctrl-Numpad8 to 800%.
Zoom In/Out (Wheel) — zooms in or out.
Zoom to Fit (Shift-Home) — like Frame All, but grabs as much editor space as it can.
Zoom Region (Shift-B) — zooms in on the nearest item within the dragged border.
Auto Zoom — while on, the preview auto-zooms to keep the video size matched to the editor size.
Proxy — see Proxy.
Sequence Render Image — shows the current frame preview as a Render Result you can save as an image file.
Sequence Render Animation — saves previews of the scene-range frames (or the preview range, when active) out to a video file or a run of image files; see the Output panel.
Note: by default neither Sequence Render Image nor Sequence Render Animation outputs the finished video — both skip Scene Strips and fall back on the preview's shading mode (initially Solid). To output video with Scene Strips rendered, use the top-bar Render menu, or set Sidebar ‣ View ‣ Scene Strip Display ‣ Shading to Rendered.
Export Subtitles — exports Text strips, which can serve as subtitles, to a SubRip file (.srt); the exported file holds every Text strip in the video sequence.
Toggle Sequencer/Preview (Ctrl-Tab) — flips the editor between Sequencer and Preview.
Area — area controls; see the user-interface documentation.

Select Menu — see Selecting Strips.

Strip Menu — see Editing Strips.
Mirror:
Interactive Mirror (Ctrl-M) — begins a mirror based on the mouse position.
X Global — mirrors the image in global X.
Y Global — mirrors the image in global Y.
X Local — mirrors the image in local X.
Y Local — mirrors the image in local Y.
Duplicate (Shift-D) — copies the selected strip(s) into the nearest free channel above the original; the copy stays selected so you can reposition it at once. See also Duplicate.
Copy (Ctrl-C) — adds the selected strips to the copy-paste buffer.
Paste (Ctrl-V) — pastes strips from the copy-paste buffer.
Animation:
Insert Keyframe (I) — see Insert Keyframe.
Insert Keyframe with Keying Set (K) — see Insert Keyframe with Keying Set.
Change Keying Set (Shift-K) — see Set Active Keying Set.
Delete Keyframes (Alt-I) — see Delete Keyframes.
Clear Keyframes (Shift-Alt-I) — see Clear Keyframes.
See also Editing Keyframes.
Show/Hide:
Show Hidden Strips (Alt-H) — reveals all hidden/muted strips.
Hide Selected (H) — mutes the selected strips.
Hide Unselected (Shift-H) — mutes every strip but the selected ones.
Delete — deletes the selected strips.

Image Menu:
Transform — Move Origin (Ctrl-Period): moves the image strip's origin without shifting the strip's content; handy for setting the reference point for rotation, scaling, or further positioning — moving the origin to a corner, say, lets rotations pivot around that corner rather than the default center.
Clear — resets the selected images' position, rotation, or scale.
Apply:
Scale to Fit — sizes the selected images as large as they go while still fitting wholly inside the video; no cropping, aspect ratio kept.
Scale to Fill — sizes the selected images to fill the whole video space; they may be cropped, aspect ratio kept.
Stretch to Fill — sizes the selected images to the video's dimensions; no cropping, but aspect ratio may change.

Pivot Point — see Pivot Point.
Display Mode — see Display Mode.
Display Channels:
Color & Alpha — shows the preview with transparency over a checkerboard.
Color — ignores the preview's transparency (fully transparent areas turn black).
Gizmos — see Gizmos.
Overlays — see Sequencer Preview Overlays.

## Toolbar

Selection tools:
Tweak — select or move.
Select Box — select images by dragging a box; every image the box touches is selected.
Select Circle — select images by dragging a circle; every image the circle's path touches is selected.
Select Lasso — select images by drawing a lasso.

Cursor — moves the 2D Cursor when you click or drag with LMB. While dragging, press X or Y to lock movement to an axis; for extra precision, hold Shift to inch the cursor along below mouse speed, or type a number for an exact distance. The header reports how far the cursor has traveled, including the distance per axis. Instead of this tool you can drag with Shift-RMB (works with any tool) or edit the 2D Cursor Location in Sidebar ‣ View. Note: by default the 2D Cursor only shows while you drag it; enable the 2D Cursor overlay to keep it visible.

Move (G) — moves the selected images when you drag with LMB; alternatively press G, move the mouse, and click LMB to confirm (RMB to cancel). With the Active Tools gizmo on, drag one of the colored arrows to move along just that axis. You can also press X or Y while moving — once to lock to the global axis, twice for the local axis, three times to drop the constraint — or hold MMB and move the mouse horizontally or vertically. For more precision while moving: hold Shift to go slower, type a number for an exact amount, or use the arrow keys. The header reports how far the image has moved, per axis. Instead of this tool you can adjust the Position in the Sidebar's Strip tab (only in the Sequencer and Sequencer & Preview modes).

Rotate (R) — rotates the selected images when you hold LMB and circle the mouse; alternatively press R, move the mouse, and click LMB to confirm (RMB to cancel). Images turn around the Pivot Point, so an off-center pivot makes them swing around it rather than just spin. For more precision while rotating: hold Shift to go slower, hold Ctrl for 5-degree steps, type a number for an exact amount, or use the arrow keys. The header reports how far the image has turned. Instead of this tool you can adjust the Rotation in the Sidebar's Strip tab (only in the Sequencer and Sequencer & Preview modes).

Scale (S) — resizes the selected images when you drag with LMB; alternatively press S, move the mouse, and click LMB to confirm (RMB to cancel). With the Active Tools gizmo on, drag one of the colored lines to scale along just that axis. You can also press X or Y while scaling — once for the global axis, twice for the local axis, three times to drop the constraint — or hold MMB and move horizontally or vertically. Images scale around the Pivot Point, so with an off-center pivot, scaling down also pulls them toward it. For more precision while scaling: hold Shift to go slower, hold Ctrl for 10% steps, type a number for an exact factor (e.g. .5 to halve the size), or use the arrow keys. The header reports the current scale factor. Instead of this tool you can adjust the Scale in the Sidebar's Strip tab (only in the Sequencer and Sequencer & Preview modes).

Transform — handles move, rotate, and scale in a single tool: drag the central cross to move, drag the dot on the protruding line to rotate, drag a corner to scale evenly on both axes, or drag a side to scale on one axis.

Sample — samples a pixel's color while you hold LMB; the editor reports, along the bottom: the X and Y coordinates in pixels from the top-left corner; the pixel's red, green, blue, and alpha as decimals between 0 and 1; the pixel's red, green, and blue with Color Management applied; and its hue, saturation, value, and luminance with Color Management applied.

Annotate — draw free-hand annotations.
Annotate Line — draw a straight-line annotation.
Annotate Polygon — draw a polygon annotation.
Annotate Eraser — erase annotations you drew earlier.

## Channels

A channel is a horizontal track much like a layer in an image editor: higher channels draw in front of lower ones. Within a channel you make one or more strips, each carrying either a piece of video content (a rendered scene, an outside video file…) or an effect (color blending, blur…). The X axis is time, so the further right a strip sits, the later it plays in the final video. A channel can hold several strips, but they can't overlap — to play two strips at once, put them on different channels.

Channel Region — sits on the editor's left and holds the channel properties below; toggle its visibility with View ‣ Channels.
Name — the channel's name; double-click to change.
Mute Channel — disables the whole channel so none of its strips are seen or heard in the final video; individual strips can also be muted.
Lock Channel — locks the whole channel to guard all its strips against accidental changes; individual strips can also be locked.

## Display

Sequencer Overlays — Reference: Location: Header ‣ Overlays. Overlays are information drawn over the sequencer region. Clicking Show Overlays toggles them all at once, while the drop-down opens a pop-over for toggling individual ones.
Grid — shows vertical lines at regular time intervals.
Cache — visualizes cached images on the timeline.

Strips:
Name — shows each strip's Name.
Source — shows each strip's file path.
Duration — shows each strip's length in frames.
Animation Curves — draws the volume curve on Sound strips and the opacity curve on the rest.
Thumbnails — draws thumbnails across the full width of each Movie or Image strip; their size tracks the vertical zoom (adjusted by dragging up and down with Ctrl-MMB), so zooming in gives taller strips with bigger but fewer thumbnails, and zooming out gives narrower strips with smaller but more.
Color Tags — draws each strip in its assigned custom color (when set) rather than a type-based color; set one via the Color Tag button beside the strip's name in Sidebar ‣ Strip, or Set Color Tag in the strip's context menu.
Offsets — shows overflow bars for content trimmed from a strip (by moving its handles); see Strip Offset Start/End.

Waveforms:
Type — global control of waveform display on Sound strips. On (waveforms for every strip), Strip (each strip's own Display Waveform option), or Off (no waveforms).
Style — how Waveforms appear. Full (the audio amplitude) or Half (the audio level).

## Cache

The Cache keeps preview frames in memory so they display far faster during playback instead of being re-rendered each frame, which is especially useful for keeping things smooth while editing or scrubbing. The overall cache memory limit is set in the Preferences' System tab. See also: which frames are cached can be shown by enabling Show Cache in the Timeline overlay settings.

Cache Settings — Reference: Panel: Sidebar ‣ Cache ‣ Cache Settings. This panel configures how and when image data is cached during editing; the settings apply globally to every strip in the Video Sequence Editor.
Prefetch Frames — when on, Blender prefetches and caches frames ahead of the current one in the background, which can smooth playback. Note: prefetching isn't currently supported for Scene strips.
Cache:
Raw — caches raw image data right after it's read from disk, speeding up tweaks to strip parameters like color correction at the cost of more memory.
Final — caches each frame's final composited image, giving faster playback of fully processed strips.
Display — visual cues in the Timeline marking cached frames.
Cache:
Raw — draws a red bar in the Timeline beneath frames cached in their raw state.
Final — draws a blue bar along the Timeline's top wherever frames are cached in final composited form.
A readout at the panel's bottom gives live cache statistics: Current Cache Size (the total memory the cache system is using now), Raw (memory used by the raw image cache), and Final (memory used by the final rendered-frame cache).

## Proxy

As projects take on ever higher-resolution footage, the video preview can slow down badly. To fight that, Blender can build proxies — copies of the footage stored at lower quality and/or resolution — keeping editing smooth without hurting the final result's fidelity.

The fastest way to set up video proxies is simply to pick a Proxy Render Size in the View tab (shown when the editor is in Preview or Sequencer & Preview mode); this turns on the chosen proxy resolution for every strip and starts building the downscaled video files. Use the Proxy tab when you want to configure proxies in more detail (or make proxies for image sequences).

Proxy Settings — Reference: Panel: Sidebar region ‣ Proxy ‣ Proxy Settings. Holds scene-wide proxy settings.
Storage — how the project's proxies are stored. Per Strip (each strip says where its proxies go, below) or Project (all proxies in one directory).
Proxy Directory — where the project's proxies are stored.
Set Selected Strip Proxies — opens a pop-over to pick the resolution(s) to build and whether to overwrite existing proxy files; confirm with Set and your choices apply to the selected strips. View and tweak individual strips in the Strip Proxy & Timecode panel (below). In Preview mode, where the Proxy tab is missing, this runs through View ‣ Proxy ‣ Setup instead.
Rebuild Proxy and Timecode Indices — builds proxies and time indices for the selected strips. In Preview mode, where the Proxy tab is missing, this runs through View ‣ Proxy ‣ Rebuild instead.

Strip Proxy & Timecode — Reference: Panel: Sidebar region ‣ Proxy & Timecode ‣ Strip Proxy & Timecode. Holds strip-specific proxy settings; the header checkbox enables/disables proxy generation.
Custom Proxy:
Directory — by default generated proxy videos go to /BL_proxy/<clip name>, but this option points them at a custom directory.
File — lets you use preexisting proxies.
Resolutions — which proxy-video resolution(s) to build; you can pick several.
Overwrite — whether to overwrite existing proxy files or keep them.
Quality — the amount of lossy compression applied, as a percentage; lossy compression shrinks file size by dropping some image data, which can cost detail. 0% means maximum compression — smallest files, most obvious quality loss; 100% means none — full quality at a larger file size.
Timecode Index — footage copied straight off a camera without preprocessing can show many artifacts, mostly from seeking to a given frame, because such footage usually lacks correct frame-rate values in its header; this can crop up even when the clip's frame rate matches the scene's. For Blender to count frames and frame rate correctly there are two routes: preprocess the video with something like MEncoder to fix the header and insert proper keyframes, or use Blender's Timecode Index option.
None — disregards generated timecodes and seeks in the movie stream by calculated timestamp.
Record Run — seeks using timestamps read from the movie stream, giving the best alignment between scene and movie times.
Record Run No Gaps — in effect turns the movie into an image sequence, ignoring incomplete or dropped frames and frame-rate changes.
Note: Record Run is usually the best Timecode Index, but for a thoroughly damaged source file, Record Run No Gaps may be the only way to get a usable result.

## Asset Catalogs

Asset Catalogs help you organize your assets. They resemble file directories a little, but they're entirely independent of where your blend-files sit. Assign each asset in a blend-file to its own catalog, or keep one big catalog holding every asset from every blend-file — it's up to you. Like Collections, catalogs can be nested: a main catalog can contain several nested catalogs, so you might have a "Furniture" catalog with "Tables", "Chairs", "Lamps", and other sub-catalogs. For deeper technical detail, see Asset Catalogs in the Blender Developer Documentation.

The Home Location of Assets — you may have any number of catalogs, yet an asset belongs to only one of them at a time, much like a file in a single directory (ignoring tricks like symbolic links). Catalogs themselves can be nested and rearranged by drag-and-drop; moving a catalog leaves its assets alone, they simply travel to the catalog's new spot. Selecting a catalog in the Asset Browser shows every asset in it and in its child catalogs — so in the earlier example, selecting Characters/Ellie/Poses also shows assets from Characters/Ellie/Poses/Head and Characters/Ellie/Poses/Hands.

Creating Catalogs — make new catalogs in the Asset Browser via Header ‣ Catalog ‣ New Asset Catalog; once created, double-LMB its name in the editor's Source List region to give it a more descriptive name. You can also create catalogs in that region by clicking the plus icon at the top of the Tree View.

Assigning an Asset — to assign assets to a catalog, just select them and drag them onto the catalog. Tip: assigning an asset to the "Unassigned" catalog strips it from any catalogs it was in.

Saving Catalogs — saving makes any catalog edits permanent by writing the current setup to the asset library. Save catalogs in the Asset Browser via Header ‣ Catalog ‣ Save Asset Catalog, or in the editor's Source List region by clicking the save icon at the top of the Tree View.

Components of a Catalog — each catalog has a catalog path, a UUID, and a simple name. Normally you only handle the catalog path; the rest is for internal Blender use and/or emergencies.
Catalog Path — the path sets where in the hierarchy the catalog appears. Examples like Characters/Ellie/Poses/Hand or Kitbash/City/Skyscrapers produce a corresponding catalog tree; the highlighted catalog has path Characters/Ellie/Poses/Hand.
UUID — each catalog carries a UUID, normally hidden from the UI (switch on Developer Extras plus the experimental Asset Debug Info option to reveal them). It's what gets stored in the asset and what fixes the catalog's "identity", so a catalog can be renamed or moved (its path changed) and all its assets travel along — only the catalog itself changes, not any asset blend-file.
Simple Name — every catalog may carry an optional simple name, kept beside the UUID in each asset; its point is to let a human recognize the catalog an asset was assigned to even if the catalog definition file (below) is lost. Like the UUID, it's normally hidden from the UI; enable Developer Extras in the interface preferences to show it in the Asset Browser.

Catalog Definition Files — asset catalogs live in Catalog Definition Files (CDFs). Blender 3.0 supports one CDF per asset library, stored as blender_assets.cats.txt in the library's root directory. If the file is missing, Blender creates it when catalogs are saved; when catalogs change, Blender updates that file and also writes a backup of the previous state to blender_assets.cats.txt~.
Which File to Write To — asset catalogs are saved apart from the blend-file; the catalog editor carries its own "Save" button.
Format — CDFs are fairly simple text files in UTF-8: a version indicator plus one line of text per catalog, each line colon-separated in the form {UUID}:{path}:{simple name}.
Example — a valid catalog definition file:
```text
# This is an Asset Catalog Definition file for Blender.
#
# Empty lines and lines starting with `#` will be ignored.
# The first non-ignored line should be the version indicator.
# Subsequent lines are of the format "CATALOG_UUID:catalog/path/for/assets:simple catalog name"

VERSION 1

313ea471-7c81-4de6-af81-fb04c3535d0e:catalog/without/simple/name:
ee9c7b60-02f1-4058-bed6-539b8d2a6d34:character/Ellie/poselib:character-Ellie-poselib
cd66bf52-58f4-45cb-a4e2-dc0e0ee8f3fe:character/Ellie/poselib:character-Ellie
4eb44ec6-3424-405b-9782-ca006953e799:character/Ellie/poselib/white space:character-Ellie-poselib-white space
b63ed357-2511-4b96-8728-1b5a7093824c:character/Ružena/poselib:Ružena pose library
dcdee4df-926e-4d72-b995-33106983bb9a:character/Ružena/poselib/face:Ružena face
fb698f2e-9e2b-4146-a539-3af292d44899:character/Ružena/poselib/hand:Ružena hands
```
Valid Catalog Paths — paths obey these rules:
- Every path is absolute; /a/b and a/b are the same.
- Only / as the separator (no \; think less filesystem path, more URL).
- Not empty (a valid catalog needs one).
- No empty components (so not a//b; a/b is fine).
- Invalid characters: :, , \.
- Paths are always read as UTF-8.

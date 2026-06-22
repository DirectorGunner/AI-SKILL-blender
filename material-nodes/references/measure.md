# Measure, Viewport Render, Clip Display, Mask Display ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Measure; Viewport Render; Clip Display; Mask Display; Sidebar Region; Compositor.

## Measure

Reference — Mode: All Modes. Tool: Toolbar ‣ Measure.

Measure is an interactive tool: you drag lines across the scene to read off distances or angles. Switching on snapping to geometry sharpens accuracy and lets you gauge things like wall thickness. You reach it from the Toolbar.

Usage — a typical workflow:
Activate Measure from the Toolbar.
Drag in the viewport to lay down the ruler's first start and end points; you can place several rulers.
Drag either endpoint to reposition the ruler.
Hold Ctrl as you move to snap onto edges and vertices.
Hold Shift as you move to measure the gap between faces — this works best with parallel faces such as walls.
You can pan, zoom, or change the projection (orthographic, perspective) at any moment for a better angle on the ruler.
Click a ruler's midpoint to convert it into a protractor; that midpoint can then be dragged like the endpoints.
Remove a selected ruler with Delete or X. To wipe out every measurement, delete the "RulerData3D" layer in the Sidebar ‣ View ‣ Annotations panel.

Every measurement vanishes once another tool is chosen and reappears when Measure is active again; even so, you can still run editing operations while a ruler is live — adjusting the selected object's rotation or scale in the Sidebar, for instance. Measurements never appear in the Render output.

Dimensions are shown using the scene's unit settings and scale, so switching the unit system (metric versus imperial), the length units (cm, m, …), or the angle units (degrees, radians) refreshes the readouts.

Tip: in Edit Mode there's also a Measurement group in the Viewport Overlays popover; its settings let the viewport show measurements for selected edges and faces on their own, with no need to place a ruler by hand.

## Viewport Render

Viewport rendering turns out quick preview renders from your current vantage point, rather than from the active camera the way an ordinary render would. You can use it for both still images and animations.

Note: viewport rendering is limited to the Workbench and EEVEE engines — Cycles isn't supported.
Tip: switch overlays off to get a render free of clutter such as rigs and empties.

Settings: for the most part Viewport Render just honors the current viewport settings. A handful of settings come from the properties of whichever render engine draws the view — Solid mode uses Workbench's render settings, Material Preview mode uses EEVEE's. On top of that, several output settings apply: Resolution, Aspect, Output path, and File format.

Rendering: triggering Viewport Render renders from the currently active view. If you aren't in an active camera view, a stand-in camera is built to match the present perspective; to capture the camera's viewpoint, enter the active camera view with Numpad0. As with a normal render, Esc aborts it.
Render a Still Image — use 3D Viewport ‣ View ‣ Render Viewport Preview.
Render an Animation — use 3D Viewport ‣ View ‣ Render Playblast.
Render Keyframes — use 3D Viewport ‣ View ‣ Render Playblast on Keyframes to render only the frames where the selected objects hold an animation key. Frames without a key are still written out, but they simply repeat the last rendered frame. For example, with a six-frame animation whose selected objects are keyed on frames 3 and 5, the output runs like this: frame 1 always renders; frame 2 repeats it (no key); frame 3 renders; frame 4 repeats it; frame 5 renders; frame 6 repeats it.
Tip: you can confine the viewport render to a chosen area with Render Regions.

## Clip Display

This pop-over gathers display settings for both Tracking mode and Mask mode.

R, G, B — sets which color channels feed the frame preview. Because the tracker works on grayscale images, toggling channels lets you find the combination of enabled and disabled channels that yields the best contrast and the least noise. This affects the preview only; to choose the channels used for actual tracking, set a default for new markers from the Track tab in the Toolbar, or configure existing markers from the Track tab in the Sidebar.
Grayscale Preview (B/W) — renders the entire frame in grayscale.
Mute Footage (M) — hides the movie clip and shows a black image instead, which helps you spot markers that are tracked poorly or not at all.
Render Undistorted — uses the Lens settings on the video preview to cancel lens distortion, without altering the footage itself.
Show Stable — applies the 2D stabilization settings to the preview, without altering the footage itself.
Grid — draws a grid that starts out orthographic but gets bent by the Lens settings; useful for manual calibration, since the warped grid lines should coincide with footage lines that are supposed to read as straight.
Calibration — puts the Lens settings to work on annotation strokes; like Grid, it aids manual calibration.
Display Aspect Ratio — changes the aspect ratio for display only, leaving tracking and solving untouched.

Marker Display — governs how markers appear in the editor.
Pattern — whether to show the tracks' pattern areas; useful for cutting clutter and gauging tracking quality.
Search (Alt-S) — whether to show the search areas of selected tracks; again, useful for reducing clutter and checking tracking quality.
Path — shows a track's past (red) and future (blue) positions relative to the current frame, visualizing its motion so irregularities stand out.
Length — the Path's length in frames.
Show Disabled (Alt-D) — when off, hides tracks disabled on the current frame (except the active one, last selected); this declutters the view and makes tracking accuracy easier to judge.
Info — shows each selected track's name and status, where the status may read "keyframed," "tracked," "disabled," and so on.
3D Markers — shows the outcome of solving the markers' 3D positions from their 2D motion; each 3D point is projected back onto the clip and drawn as a small dot, green when it lands close to the original 2D marker (a good solve) or red when it's far off (needs tweaking).
Display Thin — by default marker areas appear as bright boxes with a black outline; this option draws them as thin dashed lines instead.

## Mask Display

This popover governs how masks appear in Mask mode.
Spline — toggles display of the mask splines; note that while they're hidden you can't edit them.
Edge Display Type — the line style used for the splines.
Overlay — shows masks by tinting the entire clip.
Overlay Mode:
  Alpha Channel — shows the masks alone as a grayscale image, excluded areas black and included areas white.
  Combined — shows the clip with excluded areas darkened.
Blending Factor — how strongly excluded areas are darkened under the "Combined" Overlay Mode.

## Sidebar Region

Footage — Proxy/Timecode: high-resolution video can drag down Blender's performance, making scrubbing and other operations sluggish. To counter that, generate one or more proxies — copies of the footage kept at lower resolution and/or quality — and use them as lighter stand-ins while you work.
Build Original — which proxy resolution(s) to make from the original, distorted footage.
Build Undistorted — which proxy resolution(s) to make from the undistorted footage (i.e. with the Lens settings applied to remove the recording's distortion).
Quality — the amount of lossy compression applied, given as a percentage. Lossy compression shrinks file size by discarding some image data, which can cost detail. 0% means maximum compression — smallest files, most obvious quality loss; 100% means none — full quality at a larger file size.
Proxy Custom Directory — proxies normally land in a BL_proxy subfolder beside the original file; use this to point somewhere else.
Build Proxy/Timecode — generates proxies from the settings above along with timecode files. Instead of this button you can also choose Clip ‣ Proxy ‣ Rebuild Proxy and Timecode Indices.
Timecode Index — footage copied straight off a camera without preprocessing can show many artifacts, mostly from seeking to a particular frame, because such footage usually lacks correct frame-rate values in its header; this can crop up even when the clip's frame rate matches the scene's. For Blender to count frames and frame rate correctly there are two routes: preprocess the video with something like MEncoder to fix the header and insert proper keyframes, or use Blender's Timecode Index option.
  None — disregards generated timecodes and seeks in the movie stream by calculated timestamp.
  Record Run — seeks using timestamps read from the movie stream, giving the best alignment between scene and movie times.
  Record Run No Gaps — in effect turns the movie into an image sequence, ignoring incomplete or dropped frames and frame-rate changes.
  Note: Record Run is usually the best Timecode Index, but for a thoroughly damaged source file, Record Run No Gaps may be the only way to get a usable result.
Proxy Render Size — which proxy size to display; depending on the Render Undistorted setting, Blender picks either the Original proxy or the Undistorted one.

Footage Settings — see Image Settings.
Animation — manages animation data for movie-clip properties, including the active Actions and their assigned Slot; see Manually Assigning Actions and Slots.

Track — see Track.
Stabilization — see 2D Stabilization.

View — 2D Cursor: the 2D Cursor appears as the dashed crosshair sitting in the main region and can act as a transformation pivot point if you pick that option in the editor's header. It's available only in Mask mode, not Tracking mode.
  Location X, Y — the 2D Cursor's relative position, from (0, 0) at the bottom-left corner to (1, 1) at the top-right. You can also place it with Shift-RMB in or near the video.
Annotations — see Annotations.

## Compositor

The Compositor is where you wire up nodes for compositing; its use is covered in Compositing.

Interface — Header:
Node Tree — selects which node group (compositor node tree) to show and edit. Each Scene can hold its own compositor node tree, and you can also make and switch to custom node groups for reuse.
Pinned — when on, the editor sticks with the chosen node tree no matter which scene is active, handy when juggling several scenes but wanting the compositor fixed on one tree.

Gizmos — controls gizmo display in the Compositor. Clicking Show Gizmos turns every gizmo in the Compositor on or off, and the drop-down opens a popover of finer settings below.
Viewport Gizmos:
  Active Node — shows a context-sensitive gizmo for whichever node is selected, which might include transform handles or other visual aids depending on the node type.

Asset Shelf — offers quick access to compositor node assets, letting you drag and drop ready-made node setups straight into the compositor workspace; any node group marked as an asset turns up here on its own. Sitting at the editor's bottom, the shelf gives a compact, easy-to-reach interface for inserting and arranging compositor assets, and compared with the Asset Browser it blends more smoothly into the compositing workflow, and you can show or hide it whenever you like. The Asset Shelf helps you assemble node setups quickly from reusable assets, explore common compositing techniques and effects, and stay entirely inside Blender for post-processing. Toggle it from the compositor editor's header.

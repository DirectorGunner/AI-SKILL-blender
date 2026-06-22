# Navigating, Geometry Node Editor, F Curve Properties

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Navigating; Geometry Node Editor; F-Curve Properties.

## Navigating

As in most editors, you can pan vertically (channels) and horizontally (time) by dragging MMB, and zoom by rolling Wheel or dragging Ctrl-MMB; the scrollbars work too.

View Menu:
Sidebar (N) — shows or hides the Sidebar Region.
Adjust Last Operation — opens a pop-up panel to alter the properties of the just-finished operation (see Adjust Last Operation).
Channels — toggles the Channels region, the column of animated property names down the left side.
Playback Controls — shows or hides the Playback Controls.
Frame Selected (NumpadPeriod) — pans and zooms to focus on the selected keyframes.
Frame All (Home) — pans and zooms to show every keyframe.
Frame Scene/Preview Range — resets the horizontal view to the current scene frame range, honoring the preview range if it's active.
Go to Current Frame (Numpad0) — pans so the Playhead is centered.
Multi-Word Match Search — lets you filter on several search terms at once (in the search box above the channel list and in the Filters popover); terms are space-separated, so "loc rot" finds channels with either "loc" or "rot" in the name, whereas with it off the list would show only channels containing the literal text "loc rot", of which there are probably none.
Realtime Updates — whether other views (the 3D Viewport, say) refresh while you drag keyframes; if off, they update only once you finish the move.
Show Sliders — adds a value slider beside each channel, and nudging one automatically inserts a keyframe.
Show Handles and Interpolation — draws keyframes with shapes reflecting their Bézier handle type, and marks a keyframe with a green line if the curve segment after it uses a non-default interpolation type (see Handles & Interpolation Display).
Show Curve Extremes — finds keys where the curve reverses direction and tags them with an arrow inside the shape: local maxima (hills) get up arrows, local minima (valleys) get down arrows. A keyframe can show both at once, namely in a summary row holding one channel with a maximum and another with a minimum.
Auto-Merge Keyframes — automatically merges keyframes that land on the same frame after a transform.
Show Markers — shows the marker region (when any markers exist); with it off, the Marker menu is hidden and marker operators are unavailable here.
Use Timecode (Ctrl-T) — shows timing in seconds rather than frames.
Sync Visible Range — keeps the editor's horizontal pan and scale in step with other time-based editors that also enable this, so they all show the same slice of time.
Set Preview Range (P) — drag a box to define a preview time range; while it's active, playback stays within it, letting you replay a segment without rewinding by hand. Change its start or end with the matching button in the Timeline editor's Playback popover, or simply run Set Preview Range again.
Clear Preview Range (Alt-P) — clears the preview range.
Set Preview Range to Selected (Ctrl-Alt-P) — sets a preview range spanning the selected keyframes.
Toggle Graph Editor (Ctrl-Tab) — swaps the area over to the Graph Editor.
Cache — picks which simulation caches appear on the timeline: baked sims show fully opaque, cached sims slightly transparent, and invalid caches slightly transparent with dark diagonal stripes.
Area — area controls; see the user-interface documentation.

Filters — available from the funnel dropdown in the header.
Summary — toggles the "Summary" row atop the Channels region, which shows the union of all keyframes across every channel.
Only Show Selected — shows only keyframes belonging to selected objects/bones/…. Note: with this on, the Dope Sheet may omit some material keyframes of the selected objects, showing instead only those tied to the nodes selected in the Shader Editor.
Show Hidden — shows keyframes from hidden objects/bones/….
Only Show Errors — shows only channels with errors (for instance, ones that try to animate a property the object doesn't have).
Search — filters the channel list by a search term (or several, if Multi-Word Match Search is on).
Filtering Collection — pick a collection to show only keyframes from objects in it.
Filter by Type — filters curves by property type.
Sort Data-Blocks — sorts data-blocks alphabetically for easier finding; if it hurts playback speed (really only a concern with lots of objects), you can switch it off.

Playback Controls — this region carries controls and options for playback, keying, auto keyframing, and transport. They let you control how animations are previewed and synced with audio, add and handle keyframes via keying sets and auto keying, navigate the timeline with playback and transport controls, and adjust frame ranges and preview chosen segments. See also the Playback Controls documentation for a full description of the properties and controls usually found in the footer.

Pan by dragging MMB. Zoom with the Wheel or NumpadPlus / NumpadMinus.

Gizmos — at the top of the Image Editor, beside the Sidebar, navigation gizmos give on-screen pan and zoom controls, handy without a mouse wheel or on touch or pen devices. The pan gizmo drags the view any direction, while the zoom gizmo scales it interactively; using the zoom gizmo shows the current zoom as a percentage for instant feedback. Hold Shift while dragging the zoom gizmo for finer control, or Ctrl to snap zoom to 10% steps for consistent, predictable adjustments.

View Menu:
Toolbar (T) — shows or hides the Toolbar.
Sidebar (N) — shows or hides the Sidebar.
Tool Settings — shows or hides the active tool's settings.
Asset Shelf — toggles the Asset Shelf.
Adjust Last Operation — opens a pop-up to alter the last operation's properties (see Adjust Last Operation).
Update Automatically — instantly refreshes any other editors affected by changes here; off, they may show stale information until manually refreshed (by orbiting in the 3D Viewport, say).
Show Metadata — shows metadata about the selected Render Result; change what's included via the Output tab's Metadata panel.
Zoom — a menu of handy zoom levels and operations, figured from image resolution against screen resolution: 12.5% (1:8) Numpad8 out to 12.5%; 25% (1:4) Numpad4 to 25%; 50% (1:2) Numpad2 to 50%; 100% (1:1) Numpad1 back to 100% (Ctrl-Numpad1 and Shift-Numpad1 also reset to 100%); 200% (2:1) Ctrl-Numpad2 in to 200%; 400% (4:1) Ctrl-Numpad4 to 400%; 800% (8:1) Ctrl-Numpad8 to 800%.
Zoom In/Out (Wheel) — zooms in or out.
Zoom to Fit (Shift-Home) — behaves like Frame All but claims as much editor space as it can.
Zoom Region (Shift-B) — zooms in on the nearest item within the dragged border.
Frame All (Home) — pans and zooms so the image is centered and fully visible.
Center View to Cursor — pans so the 2D cursor is at the editor's center.
Render Region (Ctrl-B) — shown only when the Render Result is in view (see Render Region).
Clear Render Region (Ctrl-Alt-B) — likewise only with the Render Result in view (see Render Region).
Render Slot Cycle Next/Previous (J / Alt-J) — moves to the next/previous render slot that holds a render.
Area — adjusts the area the Image Editor occupies.

2D Viewport — pan by dragging MMB; zoom with the Wheel or NumpadPlus / NumpadMinus.

Gizmos — at the top of the UV Editor, beside the Sidebar, navigation gizmos give on-screen pan and zoom controls, handy without a mouse wheel or on touch or pen devices. The pan gizmo drags the view any direction, while the zoom gizmo scales it interactively; using the zoom gizmo shows the current zoom as a percentage for instant feedback. Hold Shift while dragging the zoom gizmo for finer control, or Ctrl to snap zoom to 10% steps for consistent, predictable adjustments.

View Menu — see also Navigating in the Image Editor.
Frame Selected (NumpadPeriod) — adjusts the view so every selected UV vertex is visible.

2D Cursor — like the 3D Viewport, the UV Editor has a Cursor you can jump to (View ‣ Center View to Cursor); it can also act as a pivot point and a snapping target. To move it, press LMB with the Cursor tool active, or Shift-RMB with any tool active; you can also edit the "Location X/Y" fields in the Sidebar's View tab, in either relative (0 to 1) or pixel coordinates, with the image's lower-left corner as the (0, 0) origin in both cases. Press Shift-C to send the Cursor to the center.

Header — View Menu: the View menu governs the editor's view settings.
Toolbar (T) — shows or hides the Toolbar.
Sidebar (N) — shows or hides the Sidebar.
Tool Settings — shows or hides the active tool's settings.
Adjust Last Operation — opens a pop-up to alter the last operation's properties (see Adjust Last Operation).
Channels — shows or hides the Channel Region.
Playback Controls — shows or hides the Playback Controls.
Refresh All (Ctrl-E) — pulls external files in afresh and rebuilds the current frame's preview, handy when you changed an external file or made a scene change Blender didn't notice.
Frame Selected (NumpadPeriod) — zooms to show only the selected strips.
Frame All (Home) — zooms to show every strip.
Frame Scene/Preview Range — resets the horizontal view to the scene frame range, honoring the preview range if active.
Go to Current Frame (Numpad0) — centers the horizontal timeline on the current frame.
Zoom to Border (Shift-B) — click and drag a rectangle, then zoom to it.
Limit View to Contents — keeps you from panning above the topmost channel in use.
Show Markers — shows the marker region; off, the Marker menu hides and marker operators are unavailable here.
Use Timecode (Ctrl-T) — shows seconds rather than frames on the time axis.
Sync Visible Range — keeps the editor's horizontal pan and scale in step with other time-based editors that enable this, so they show the same slice of time.
Navigation:
Play Animation (Spacebar) — starts or stops playback, across every editor.
Go to Current Frame (Numpad0) — scrolls so the current frame sits at the timeline's center.
Jump to Previous Strip (PageUp) — sends the playhead to the nearest strip border (start or end) before the current frame.
Jump to Next Strip (PageDown) — sends the playhead to the nearest strip border after the current frame.
Jump to Previous Strip (Center) (Alt-PageUp) — sends the playhead to the nearest strip center before the current frame.
Jump to Next Strip (Center) (Alt-PageDown) — sends the playhead to the nearest strip center after the current frame.
Range:
Set Preview Range (P) — interactively define the frame range for preview playback/rendering; while active, playback stays within it (handy for replaying a segment without rewinding), and it also bounds what Sequence Render Animation renders.
Set Preview Range to Strips — applies a preview range spanning the selected strips.
Clear Preview Range (Alt-P) — clears the preview range.
Set Start Frame (Ctrl-Home) — sets the scene's Start frame to the current frame.
Set End Frame (Ctrl-End) — sets the scene's End frame to the current frame.
Set Frame Range to Strips — sets the scene's Start and End frames to span the selected strips.
Sequence Render Image — shows the current frame preview as a Render Result you can save as an image file.
Sequence Render Animation — saves previews of the scene-range frames (or the preview range, when active) out to a video file or a run of image files; see the Output panel.
Note: by default neither Sequence Render Image nor Sequence Render Animation outputs the finished video — both skip Scene Strips and fall back on the preview's shading mode (initially Solid). To output video with Scene Strips rendered, use the top-bar Render menu, or set Sidebar ‣ View ‣ Scene Strip Display ‣ Shading to Rendered; that option is only available with the Video Sequencer in Preview or Sequencer & Preview mode.
Export Subtitles — exports Text strips, which can serve as subtitles, to a SubRip file (.srt); the exported file holds every Text strip in the video sequence.
Toggle Sequencer/Preview (Ctrl-Tab) — flips the editor between Sequencer and Preview.
Area — area controls; see the user-interface documentation.

Marker Menu — markers flag frames carrying key points or notable events and, as in most animation editors, appear along the editor's bottom. See Editing Markers.

Sequencer Scene — a data-block menu to choose a scene; the Sequencer Scene is the scene the Sequencer's edit lives in.

Playback Controls — this region holds controls and options for playback, keying, auto keyframing, and transport. They let you control how animations preview and sync with audio, add and manage keyframes via keying sets and auto keying, navigate the timeline with playback and transport controls, and set frame ranges and preview chosen segments.
Sync Scene Time — sets the active scene and time from the current scene strip; see the workspace settings.
See also the Playback Controls documentation for the full footer rundown.

Main View — Adjusting the View: use these shortcuts:
- Pan: MMB.
- Horizontal scroll: Ctrl-Wheel, or drag the horizontal scrollbar.
- Vertical scroll: Shift-Wheel, or drag the vertical scrollbar.
- Zoom: Wheel.
- Scale view: Ctrl-MMB dragged left/right (horizontal scale) or up/down (vertical scale); or drag the scrollbar circles with LMB.
Playhead — the blue vertical line carrying the current time at its top; see the Playhead documentation for how to use it. The Video Sequencer adds a special case: start dragging on a strip and that strip gets highlighted and shown solo in the preview, with all others temporarily muted.

If scrubbing (or ordinary playback) runs poorly, you can speed it up by making proxies.

Hint: the current frame is synced across every editor, so moving the Playhead in the Timeline editor, say, also moves it in the Video Sequence editor (and the reverse).

## Geometry Node Editor

The Geometry Node editor edits Node Groups used by the Geometry Node Modifier; such a group can define plenty of operations to reshape an object's geometry. A full list of Geometry Nodes lives in the modeling section, and the Nodes page covers working with nodes in general.

Interface — Header:
Node Tree Sub-Type — Geometry Nodes can take on several contexts depending on what the group is for, and switching context adapts the UI to suit it. Modifier creates groups meant for the Geometry Nodes Modifier; Tool creates groups meant for Node-Based Tools.
View — the standard view menu.
Select — the menu for Selecting Nodes.
Add — the menu for adding new Geometry Nodes.
Node — the menu for Editing Nodes.
Geometry Node Group — a data-block menu for creating and choosing node groups.
/ Pinned — the pin button holds the current node-group selection fixed instead of following the Active Modifier; a pinned group stays visible in the editor even when you select another object or modifier elsewhere.
Parent Node Tree — jumps up a node-group level (see Edit Group).
Snapping — snapping options (see Arranging Nodes).
Overlays — see Overlays.

Toolbar:
Select — see Selecting Nodes.
Annotate — see Annotations.
Links Cut — see Cut Links.

Sidebar:
Node — reaches the active node's properties.
Tool — reaches the active tool's settings.
View — manages annotations.
Group — edits the current node group's inputs and outputs.
Tip: within the Geometry Node Modifier you're able to supply values for the root node group's inputs and choose destination Attributes for its outputs.

Tool Context — these popover menus show in the header once the tool context is on, and their properties decide where in the UI the tool is offered (see Supported Modes & Object Types).
Types — which Object Types the tool works with: Mesh covers Mesh Objects, Hair Curves covers Curve Objects, Grease Pencil covers Grease Pencil Objects, and Point Cloud covers Point Cloud Objects.
Modes — which Object Modes it runs in: Object Mode, Edit Mode, Sculpt Mode, and Draw Mode (Grease Pencil), enabling the group across Object, Edit, Sculpt, and Grease Pencil Draw modes respectively.
Options — Wait for Click: holds for a mouse click (LMB) before running the operator from a menu, which helps with the Mouse Position Node.

## F-Curve Properties

Active F-Curve — Reference: Panel: Sidebar region ‣ F-Curve ‣ Active F-Curve. Shows the active F-Curve's properties.
Channel Name — the name of the property the curve animates.
Data Path — the programmatic path to that property.
RNA Array Index — for a multi-value property, which element this curve drives; Location, for instance, has three values (X, Y, Z), so it can hold three curves with indices 0, 1, and 2.
Display Color — how the F-Curve's color in the Graph editor is decided. Auto Rainbow gives every curve using this setting a distinct color; Auto XYZ to RGB spots curves animating an X/Y/Z coordinate and colors them red/green/blue; User Defined lets you choose.
Handle Smoothing — how the Bézier handles are computed under the Automatic or Auto Clamped handle type.
  None — only the immediately adjacent key values feed the handle computation. This older method is simple and predictable but only produces truly smooth curves in trivial cases (notice the kinks in the middle of the red curve above).
  Continuous Acceleration — solves a system of equations to avoid or minimize acceleration jumps at each keyframe. It yields far smoother curves out of the box, but any change to key values can affect interpolation over a long stretch of curve, though the effect decays exponentially with distance; that propagation is halted by any key with Free, Aligned, or Vector handles, and by extremes with Auto Clamped handles. This mode also tends to overshoot and oscillate more with fully Automatic handles, so prefer Auto Clamped by default and switch to Automatic only where you want that behavior; adding in-between keys also tames it.
  Tip: weighing the trade-offs, Continuous Acceleration suits limited animation that leans on a few interpolated keys with little manual polish. For highly polished, high-key-rate animation, the smoothing may not be worth the disruption of wider change propagation.

Active Keyframe — Reference: Panel: Sidebar region ‣ F-Curve ‣ Active Keyframe.
Interpolation — the interpolation between the active keyframe and the next.
  Constant — the curve holds its value until the next keyframe, giving an abrupt stair-step; normally used only during the initial "blocking" stage of pose-to-pose workflows.
  Linear — the curve runs straight from one keyframe to the next, avoiding abrupt value changes (though not speed changes); two keyframes with Linear interpolation and extrapolation make an endless straight line easily.
  Bézier — the default, smooth in both value and speed.
  Note: F-Curves for properties that accept only discrete values always look stair-stepped, whatever you pick.
Easing (by strength) — a set of interpolations that specialize in speeding up or slowing down a value, easing it from rest into motion or the reverse. See also easings.net and Robert Penner's Easing Functions for explanations and live demos.
Dynamic Effects — extra easing types that fake physics-like effects such as bouncing.
  Back — with Ease In the value first pulls away from the target and then darts toward it; with Ease Out it heads for the target, overshoots, and returns. Its Back setting sets the overshoot's size and direction (above/below the curve).
  Bounce — the value bounces a few times with exponential decay, like a tennis ball dropped on the floor.
  Elastic — the value overshoots the target, rebounds and undershoots, overshoots again, and so on with ever-fading intensity until it settles. Amplitude sets how far it first overshoots; Period sets the time between oscillations.
Easing — applies only to the Easing and Dynamic Effects categories above.
  Automatic Easing — auto-picks the most common type: Ease In for the Easing interpolations, Ease Out for the Dynamic Effects.
  Ease In — the value accelerates, slow at the segment's start and faster toward the end.
  Ease Out — the value decelerates, fast at the start and slower toward the end.
  Ease In Out — slow at the start, quick through the middle, slow again toward the end.
Key Frame — the active keyframe's frame.
Value — the active keyframe's value.
Left/Right Handle Type — when the keyframe's interpolation is Bézier, the curve's shape around it depends on its handles, and each handle's type decides whether and how Blender places it automatically, and how freely you can place it by hand. Change handle types several ways: these Sidebar dropdowns, the Key ‣ Handle Type menu, or pressing V and picking from the popup. To move an automatic handle, just drag it — no need to change its type first.
  Automatic — automatic handles that yield smooth curves.
  Auto Clamped — automatic handles clamped to prevent overshoots and direction changes (S-shapes) between keyframes.
  Vector — automatic handles that produce straight segments, like linear interpolation.
  Aligned — manual handles locked together to always point opposite ways, giving a curve that's always smooth at the control point.

Free — manual handles that move independently, so they can produce a sharp change of direction.
Frame, Value — the frame and value of the active keyframe's left/right handle.

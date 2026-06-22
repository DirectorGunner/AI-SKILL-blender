# Vr Scene Inspection, Biovision Motion Capture Bvh, Using Blender From The Command Line, Operators

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: VR Scene Inspection; BioVision Motion Capture (BVH); Using Blender From The Command Line; Operators.

## VR Scene Inspection

VR Scene Inspection is a bundled (GPL) add-on that surfaces — and modestly extends — Blender's built-in virtual-reality support inside the UI; its scope is deliberately narrow (inspecting a scene), and going further generally means extending it in code. The underlying tech is the OpenXR specification, which needs the setup described under Head-Mounted Displays (HMD). Every control sits under 3D Viewport ▸ Sidebar ▸ VR tab.

VR Session: "Start VR Session" tries to reach the OpenXR runtime and share the viewport with a headset. Two tracking switches apply — Positional (turn it off to track only head rotation, leaving the viewer's location fixed) and Absolute (which drops the eye offsets that otherwise snap the viewer onto a landmark, so the origin can be set independently of the headset). "Use Controller Actions" turns on the stock bindings for haptics, controller tracking, and navigating the viewport.

View: a set of Show switches decide what appears inside the headset — the ground Floor, Annotations strokes, Selection outlines, the motion Controllers (needs Use Controller Actions), Custom Overlays (operator drawing such as the teleport beam), and Object Extras (empties, lights, cameras). Alongside them: an object-type visibility filter, a Controller Style, Clip Start/End (same idea as the viewport's clipping), and Fly Speed for free-flying.

Landmarks save reusable viewer base poses (a position with a rotation); for the Custom Object and Custom Pose types you can also set a base reference scale. The Landmark List drives which landmark's settings show beneath it, and merely changing the selection leaves the VR view untouched. Actions include: Activate (make a landmark the VR view's base pose), Add, Remove, and "Add from Session" (build one from the running session's viewer pose). More helpers cover making a camera plus landmark from the session, deriving a landmark from the active camera, refreshing a custom landmark from where the viewer currently is, snapping the 3D cursor onto a landmark, placing the scene camera there, or spawning a fresh camera from it. A landmark's Type is one of: Scene Camera (track whatever camera is active), Custom Object (any chosen object sets the pose), or Custom Pose (you key in the position and rotation by hand).

Action Maps: a gamepad (for instance a Microsoft Xbox Controller) can stand in for the motion controllers when issuing VR actions like navigation. Binding Extensions add per-device mappings — among them HP Reverb G2, HTC Vive Cosmos, HTC Vive Focus 3, and Huawei controllers — though support varies by platform.

Viewport Feedback: optionally draw, in the ordinary 3D Viewport, a marker for the live VR viewer pose (its place and orientation), markers for the tracked controllers (again gated on Use Controller Actions), and landmark markers; "Mirror VR Session" makes the viewport mimic the headset's view.

Preferences (under Preferences ▸ Navigation ▸ VR Navigation, visible only with the add-on on): Vignette Intensity dials the movement vignette's strength; Turn Speed governs rotation rate while turning continuously; Turn Amount fixes the per-step angle for snap turning; Snap Turn flips between continuous and stepped turning; and Invert Rotation flips the rotation controls. For reference, its category is 3D View, and it lets you view the viewport through VR head-mounted displays at 3D Viewport ▸ Sidebar ▸ VR tab.

## BioVision Motion Capture (BVH)

The BioVision Motion Capture (BVH) add-on moves .bvh data — a BioVision Hierarchical skeleton (rig) plus its animation — in and out of Blender through File ▸ Import/Export ▸ Motion Capture (.bvh); its usual job is pulling in mocap recordings. It ships enabled; otherwise switch on "BioVision Motion Capture (BVH) format" under Preferences ▸ Add-ons.

On import, Target decides interpretation: Armature for a rigged, animated skeleton (say a walk capture), or Object for a static mesh with no animation. The Transform group has Scale (enlarge the BVH physically), Rotation (its rotation order), and Forward/Up, which reconcile differing axis conventions — since tools disagree on which axis is "up," remapping converts rotations between their defaults. Blender treats Y as forward and Z as up (the front view sights down +Y), so a Y-up file usually wants -Z forward with Y up. The Animation group sets the Blender Start Frame for playback; Scale FPS, which retimes the file's rate to the scene (left off, one BVH frame equals one Blender frame); Loop for cyclic playback; plus options to push the scene's FPS and its duration to match the file.

On export, Transform again exposes Scale and Rotation; "Root Translation Only" limits written translation channels to the root bone; and Start/End picks the frame range to write.

## Using Blender From The Command Line

The Console Window (also called a Terminal) is an OS text window showing messages about Blender's operations, status, and internal errors; when you start Blender manually from a terminal, its output appears in that window. It's useful for rendering animation; for automation and batch processing that launch Blender with different arguments; for Python development, to read print() output; for diagnosing an unexpected exit, where the messages may show the cause; and, when troubleshooting, for reading --debug output. See "Launching from the Command Line" for platform-specific steps, and note that closing the Console Window also closes Blender, losing unsaved work. The launch instructions cover Linux, macOS, and Windows; the arguments are grouped into Render, Cycles Render, Format, Animation Playback, Window, Python, Network, Logging, Debug, GPU, and Misc options; and the page also covers sub-commands and workflows.

## Operators

Operators. Operator Cheat Sheet (Help ‣ Operator Cheat Sheet, requires Enable Developer Extras) writes a text file in the Text Editor listing every operator with its default values in Python syntax plus the generated docs — a handy overview of every operator Blender provides (see also the API documentation). System operators — Reload Scripts (All Modes; Topbar ‣ Blender ‣ System ‣ Reload Scripts) reloads every script in the scripts data folder, discarding any unsaved Text Editor changes. Memory Statistics (run with --debug-memory; Topbar ‣ Blender ‣ System ‣ Memory Statistics), also reachable by searching "Memory Statistics" in Operator Search, prints useful information about memory objects, their size, and user count — for full use, launch Blender from the console with --debug-memory. Debug Menu (All Modes; Topbar ‣ Blender ‣ System ‣ Debug Menu) opens a menu to put Blender into a debug mode (see the source code for what each value does; developers can search the code for G.debug_value for other uses; more debug options appear when launching in debug mode or setting bpy.app.debug = True). Redraw Timer (All Modes; Topbar ‣ Blender ‣ System ‣ Redraw Timer) opens a menu of tests that benchmark UI render times along with undo/redo. Clean Up Space-Data (All Modes; Topbar ‣ Blender ‣ System ‣ Clean Up Space-data) removes unused settings for invisible editors.

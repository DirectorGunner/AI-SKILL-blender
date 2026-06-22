# Editing Images, Image Settings, Image Overlays, Input ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Editing Images; Image Settings; Image Overlays; Input; Interface; Lights.

## Editing Images

New — Reference: Mode: All Modes; Menu: Image ‣ New; Shortcut: Alt-N. Makes a new Generated Image.

Open — Reference: Mode: All Modes; Menu: Image ‣ Open; Shortcut: Alt-O. Opens a file browser to load an image into the editor; you can also drag and drop images straight in. On open, these options appear:
Relative Path — makes the file path relative to the open blend-file (see Relative Paths).
Detect Sequences — auto-hunts for image sequences in the chosen images (by file name); switch it off when you really do want single images that belong to a sequence (see Opening an Image Sequence).
Detect UDIMs — auto-hunts for UDIM tiles in the chosen image's directory and loads any matches as UDIMs; it works by spotting a .xxxx (four-digit number) before the file extension.

Open Cached Render — Reference: Mode: All Modes; Menu: Image ‣ Open Cached Render; Shortcut: Ctrl-R. Finds the current scene's render cache file and loads it into the Render Result, so you can restore the last render from a previous Blender session and keep working in the Compositor without re-rendering. Note that Blender doesn't write these cache files by default — you must turn on Cache Result in the scene's Output options and render at least once.

Replace — Reference: Mode: All Modes; Menu: Image ‣ Replace. Swaps the current image for another.

Reload — Reference: Mode: All Modes; Menu: Image ‣ Reload; Shortcut: Alt-R. Reloads the image from the file on drive.

Edit Externally — Reference: Mode: All Modes; Menu: Image ‣ Edit Externally. Opens the image in the Image Editor program named in the File Paths Preferences.

Copy/Paste — Reference: Mode: All Modes; Menu: Image ‣ Copy/Paste. Copies and pastes images between Blender and the OS clipboard. Only PNG files support direct clipboard copy/paste. Platform notes: Windows can paste images by copying the image's file path, which allows every supported format; Linux needs Wayland for clipboard image support.

Save — Reference: Mode: All Modes; Menu: Image ‣ Save; Shortcut: Alt-S. Saves the image to its current path. Important: animation renders save automatically, but still renders don't — save those by hand.

Save As — Reference: Mode: All Modes; Menu: Image ‣ Save As; Shortcut: Shift-Alt-S. Saves the image to a separate file of any type; the output settings match the Render Output Properties.

Save a Copy — Reference: Mode: All Modes; Menu: Image ‣ Save a Copy. Saves under a chosen name while keeping the original open in the Image editor.

Save All Images — Reference: Mode: All Modes; Menu: Image ‣ Save All Images. Saves every modified image; packed images get repacked.

Invert — Reference: Mode: All Modes; Menu: Image ‣ Invert.
Invert Image Colors — inverts the whole image's colors.
Invert Red/Green/Blue/Alpha Channel — inverts a single channel.

Resize — Reference: Mode: All Modes; Menu: Image ‣ Resize. Rescales the image's pixel resolution to change its dimensions, useful for, e.g., dropping texture resolution to save performance and memory, or raising it for more detailed painting/editing.
Size X, Y — the new width and height in pixels.
All UDIM Tiles — applies the resize to every UDIM tile in the image.

Transform:
Flip Horizontally — mirrors the image left-to-right.
Flip Vertically — mirrors the image top-to-bottom.
Rotate 90° Clockwise — turns the image 90° clockwise.
Rotate 90° Counter-Clockwise — turns the image 90° counter-clockwise.
Rotate 180° — turns the image 180°.

Pack — Reference: Mode: All Modes; Menu: Image ‣ Pack. Packs the image into the blend-file (see Packed Data).

Unpack — Reference: Mode: All Modes; Menu: Image ‣ Unpack. Unpacks the image to a drive.

Extract Palette — Reference: Mode: All Modes; Menu: Image ‣ Extract Palette. Pulls a Color Palette out of the image for the painting tools.

## Image Settings

Source — pick the kind of image to use; for file-based images, see Supported Graphics Formats.
Single Image — one static image.
Image Sequence — an animation with each frame in its own file (see Opening an Image Sequence; for options, see Movie below).
Movie — a video file. If your aim is motion tracking and video compositing rather than just using the footage as a texture, load it into the Movie Clip Editor instead.
  Note: the options below only affect the preview, not the 3D Viewport or the render — for those, see the Image Texture Node.
  Note: Blender plays every video at the scene frame rate rather than the clip's own, so a mismatch makes them run faster or slower than intended; the Image Texture Node's Offset field (linked above) is the workaround.
  Frames — how many of the video's frames to play; past that point it pauses unless Cyclic is on.
  Match Movie Length — sets Frames to the count in the video file.
  Start — the scene frame at which the video begins playing.
  Offset — how many frames to shift the video earlier in time (equivalently, how many frames to skip at its start).
  Cyclic — loops back to the beginning after the last frame for a continuous cycle.
  Auto Refresh — plays the video in the Image Editor while the scene animation runs (the pointer must be over the Image Editor or the Timeline when you start playback).
  Deinterlace — applies deinterlacing to interlaced (analog) video.
Generated — an image Blender creates.
  X, Y — the image's pixel width and height.
  Float Buffer — makes a 32-bit image; it's larger but holds far more color information than the standard 8-bit one, which can help for close-ups and broad gradients.
  Type — Blank (a single specified color), UV Grid (a checkerboard with a colored cross in each square), or Color Grid (a busier colored grid lettered and numbered by location, useful for spotting stretching or distortion in the UV mapping).
  Color — the fill color for a Blank image.

Common Options:
File — used to replace or pack files.
Pack — embeds the resource into the current blend-file (see Packed Data).
Path — the path to the linked file.
Open — opens the File Browser to choose a file from a drive.
Reload — reloads the file, handy after it's been reworked in another application.
Use Multi-View — see Multi-View.
Color Space — names the Color Space the file was saved in, which Blender uses to convert the image correctly into its internal linear color space (used for all color math and rendering). Textures and final renders are often sRGB, while OpenEXR images are linear; images that don't really hold "colors" — normal, bump, or stencil maps — should never be color-converted, so set those to Non-Color. The available color spaces depend on the active OCIO config; the defaults are detailed under Default OpenColorIO Configuration.
Alpha — how the image treats its Alpha Channel; shown only when the format supports transparency.
  Straight — stores RGB and alpha separately with alpha acting as a mask (unassociated alpha), common in image editors and formats like PNG; it preserves color where alpha is zero.
  Premultiplied — stores RGB with alpha multiplied in (associated alpha), the natural format for renders and formats like OpenEXR; unlike straight alpha it can represent purely emissive effects such as fire correctly.
  Channel Packed — different images occupy the RGB and alpha channels and shouldn't affect each other; game engines often channel-pack to save memory.
  None — ignores the file's alpha and treats the image as fully opaque.
Half Float Precision — loads the image at 16 bits per channel instead of 32 to save memory.
View as Render — applies the color-management settings when showing this image on screen.
Seam Margin — the width of the margin around UV islands for texture painting to bleed into, ensuring no unpainted pixels are left at an island's border. A stroke crossing a seam in 3D extends past the UV island edges in the texture until it's cut off at the margin. Higher values give a thicker margin, useful if you'll make mipmaps of the texture, though it can slow painting. Note: this affects only Sculpt Mode, where texture painting is still experimental; Texture Paint Mode uses a fixed margin.

## Image Overlays

The Overlays pop-over sets up the overlays drawn over images. A header button switches all the Image Editor's overlays off, which also toggles UDIM tile information. Which options the pop-over shows depends on the Image Editor mode; the categories are:

Geometry:
Display UVs — shows the selected and active object's UVs.
UV Face Opacity — the opacity of faces, useful to tell UV islands apart; lower it while texture painting to keep faces from tinting the texture's colors.

Image:
Show Metadata — shows metadata about the selected Render Result; change what's included via the Output tab's Metadata panel.

Guides — these appear only while showing the Viewer Node image with the Image Editor in View or Mask mode.
Text Info — overlays text about the active Viewer node: Render Size (the final render output's resolution, set in Output Properties) and Image Size (the resolution of the image currently in the Viewer node).
Render Region — draws a border marking the scene's final render region, shading the space outside it for reference.
Passepartout Alpha — controls how opaque that shaded outside area is; higher values darken it more, making the render region pop.

## Input

In the Input preferences you can tune how Blender responds to the mouse and keyboard, and define your own keymap.

Keyboard:
Emulate Numpad — the Numpad keys see heavy use in Blender and aren't bound to the same actions as the regular number keys; on a keyboard without a Numpad (a laptop, say), tick Emulate Numpad to have Blender treat the ordinary number keys as Numpad keys.
Default to Advanced Numeric Input — for transform mode, start in Advanced Mode rather than Simple Mode.

Mouse:
Emulate 3 Button Mouse — Blender can be set up for pointing devices lacking an MMB, with the three buttons' roles reached by holding Alt-LMB. The mouse/keyboard combinations this manual cites can be expressed as shown in the table — MMB drag, for example, becomes Alt-LMB drag.
  Warning: this option locks you out of certain features, since Alt-LMB is itself used for some operations: adjusting several items' values in one go (objects, bones, and so on), peeling edge/face rings off the selection in Edit Mode, pulling node links apart, and shifting the Compositor's background image. Some touchpads offer a three-finger tap for the middle button, which may serve as an alternative.
  Modifier — the modifier key that emulates the middle-mouse bindings; unsupported on Microsoft Windows. Alt (use the Alt key) or OSKey (use the OSKey, which avoids clashing with the existing Alt-MMB shortcuts noted above).
Continuous Grab — keeps an action like moving objects or panning from being cut short by your screen's edges, by warping the mouse within the view. Note: cursor warping works only with relative input devices (mouse, trackball, trackpad); graphics tablets generally use absolute positioning, so the feature is off while a tablet is in use. This is detected per action, so a tablet's presence won't switch Continuous Grab off for ordinary mouse-cursor input.
Release Confirms — dragging an object with LMB moves it, and confirming that (and other) transforms normally needs an LMB click; turn this on and releasing LMB does the confirming.
Double Click Speed — the time in milliseconds that triggers a double click.
Mouse Drag Threshold — how many pixels a UI element must move before Blender treats it as a drag; smaller moves register as clicks.
Tablet Drag Threshold — the drag threshold applied to tablet events.
Drag Threshold — the threshold for non-mouse/tablet events (keyboard or NDOF, say); it affects the Pie Menu on Drag keymap preference.
Motion Threshold — how many pixels the cursor must move before the move registers, helpful for tablet pens that are hard to hold still and prone to cursor stutter. Note: unlike the click/drag distinction, this catches small movements — picking selection, for example, cycles through elements near the cursor until the cursor passes this threshold, at which point cycling stops and the closest item is chosen.

Touchpad — Note: this panel appears on Windows, macOS, and on Linux under Wayland.
Multi-touch Gestures — navigate with the touchpad using multi-touch gestures rather than scroll-wheel emulation (see Configuring Peripherals for the supported gestures).
Scroll Direction — which way scrolling responds to scroll gestures; Linux/Wayland only. Traditional (gestures up scroll content down) or Natural (gestures up scroll content up).

Tablet:
Tablet API (Windows only) — choose the native Windows Ink or the older Wintab system for pressure sensitivity; Blender auto-picks the API for your OS and tablet, but you can set it by hand if there are problems (you may need to restart Blender).
Max Threshold — how much pressure is needed for full intensity.
Softness — shapes the onset of the low-pressure response via a gamma curve.

NDOF — these control how an NDOF device (3D mouse) works with the 3D Viewport, covering navigation, orbit behavior, and motion sensitivity; on supported devices the NDOFMenu button opens a pop-up to adjust them right in the viewport.
Navigation Mode — how the 3D mouse navigates the 3D Viewport. Object (feels like holding the object — moving the 3D mouse moves the object that way), Fly (sends the camera through the scene as if flying or piloting a helicopter — push the 3D mouse up and the camera climbs), Drone (a Fly-style navigation where pushing the cap forward while looking down doesn't change altitude; "Lock Horizon" is always on here).
Lock Horizon — keeps the view level, preventing horizon tilt while navigating.
Orbit Center – Auto — works out the rotation center automatically: the full model's center of volume when it's all visible, shifting to the nearest visible object when zoomed in.
Orbit Center – Selected Items — keeps the orbit center at the midpoint of whatever objects are currently selected.
Show – Orbit Axis — overlays an axis showing the current orbit rotation direction.
Show – Orbit Center — overlays a marker at the current orbit center.

Advanced:
Pan Sensitivity — how fast the view pans per NDOF input.
Orbit Sensitivity — how fast the view orbits per NDOF input.
Deadzone — the minimum threshold for motion detection, avoiding stray movement from slight touches.
Zoom Direction — which 3D-mouse direction triggers zooming. Forward/Backward (push or pull the 3D mouse forward/backward to zoom).

Up/Down — push or pull the 3D mouse upward/downward to zoom.
Invert Pan — inverts panning on the chosen X, Y, or Z axis.
Invert Rotate — inverts rotation on the chosen X, Y, or Z axis.
Pan / Zoom Camera View — while in camera view, pans or zooms the camera rather than leaving the view during orbiting.

## Interface

Interface configuration changes how UI elements look and behave.

Display:
Resolution Scale — sizes fonts and buttons relative to the auto-detected DPI; in normal use you may prefer the zoom available across much of Blender's interface.
Line Width — the scale of lines and points in the interface, e.g. button outlines, plus mesh edges and vertex dots in the 3D Viewport. Thin, Default, Thick.
Splash Screen — show the Splash Screen at startup.
Developer Extras — surfaces settings and menu items aimed at developers, including Operator Search and Sequencer Cache Settings, plus these Button Context Menu entries: Online Python Reference (open the Python reference manual), Copy Python Command (copy the expression a button runs), Edit Source (edit the Python that defines the button), and Edit Translation (edit UI translations, available only with the Manage UI translations add-on enabled).
Preferences — Experimental Tab: lets you enable work-in-progress features currently under test.
Tooltips:
  User Tooltips — when on, hovering a control pops a tip explaining what's under the pointer and showing any hotkey; when off, you can still force a tip by holding Alt while hovering.
  Python Tooltips — adds a property's Python information beneath the tip.
Search – Sort by Most Recent — puts the most recently chosen items atop search results; otherwise results sort alphabetically.
Search – Show Hidden — shows data-blocks with dot-prefixed names in search menus, affecting search pop-ups and filtering data-block selectors. These names hide by default so internal or helper data-blocks aren't used by mistake (see Dot-Prefixed Names (Hidden Data)).

Editors:
Region Overlap — lets regions overlap the viewport, so the Toolbar and Sidebar draw over the main area.
Show – Corner Handles — draws small handles in each Area's corners for splitting or joining areas by click-and-drag, especially handy on touch devices where precise right-clicks or edge selection are harder.
Show – Numeric Input Arrows — on, numeric fields always show increase/decrease arrows; off, the arrows appear only on hover.
Show – Navigation Controls — shows navigation controls at the area's top-right, affecting the 3D Viewport and image spaces alike. Note: if you know the navigation shortcuts, you can switch this off.
Border Width — the padding around each editor area; a larger value widens the hit zone for area controls, improving usability on pen tablets, touch screens, or for accessibility.
Color Picker Type — which Color Space style you prefer for the Color picker shown when you LMB a color field: Circle HSV, Circle HSL, Square (SV + H), Square (HS + V), or Square (HV + S).
Header Position — the default header position for a newly opened editor. Keep Existing (top for most editor types, plus the positions saved in the start-up file) or Top/Bottom (always at the top or the bottom).
Factor Display Type — how factor values appear. Factor (floats from 0.0 to 1.0) or Percentage (0 to 100).
Temporary Editors — when certain operations open a new window, you configure their behavior here.
  Render In — when rendering, the UI can: Keep User Interface (no change; the render runs in the background), Maximize Area (a new Image editor opens as a full-screen temporary window), Image Editor (the largest on-screen area is swapped for a temporary Image editor), or New Window (a new Image editor opens as a regular-sized temporary window).
  File Browser — when opening files: Maximize Area (a new File Browser opens full-screen as a temporary window) or New Window (a regular-sized temporary window).
  Preferences — how the User Preferences editor opens: Maximize Area (a temporary full-screen editor in the current window) or New Window (a separate, regular-sized window).
Status Bar — preferences affecting the Status Bar.
  Show:
    Scene Statistics — information about the active scene's data: Collection (the active Collection's name), Active Object (the active selected object's name), Geometry (scene data by mode and object type — vertices, faces, triangles, or bones), Objects (the selected count and the total).
    Scene Duration — the playback's total time plus the current frame number and total frame count, formatted per the Timecode Style.
    System Memory — an estimate of Blender's RAM use; on a single-instance, single-machine setup it measures against the machine's hardware limit.
    Extensions Updates — how many extensions have updates available.
    Blender Version — the version number of the running Blender.

Language:
Language — the language used to translate the UI; the list is split into categories by how complete each translation is.
Translate:
  Tooltips — translates the descriptions shown when hovering UI elements.

Interface — translates all the labels across menus, buttons, and panels.
New Data — translates the names given to new data-blocks.

Accessibility:
Reduce Motion — avoids interface animations and motion effects, cutting visual distraction and easing comfort for users sensitive to motion or who prefer a static interface.

Text Rendering:
Anti-Aliasing — enables interface-text anti-aliasing; off, text is rendered straight, filling only absolute pixels.
Subpixel Anti-Aliasing — renders text for the best horizontal placement.
Hinting — adjusts font hinting, which controls the spacing and crispness of displayed text.
Interface Font — a replacement for the default UI font.
Mono-space Font — a replacement for the default mono-space UI font (it's used in the Text editor and the Python Console).

Menus:
Close Menu on Leave — closes menus when the mouse leaves the region.
Open on Mouse Over — pick this to open a menu by hovering its entry rather than clicking.
  Top Level — the delay, in 1/10 second, before a menu opens (needs Open on Mouse Over enabled).
  Sub Level — as above, but for submenus (e.g. File ‣ Open Recent).
Pie Menus:
  Animation Timeout — how long the opening animation of Pie Menus lasts.
  Tap Key Timeout — keystrokes held past this length dismiss the menu when released (measured in 1/100ths of a second).
  Recenter Timeout — the windowing system tries to hold the pie menu within the window's borders; for this span (in 1/100ths of a second) the pie uses the initial mouse position as its center, enabling fast dragged selections.
  Radius — the Pie Menu's size, given as the distance (in pixels) of the menu items from the pie's center.
  Threshold — the distance from center before a selection can be made.
  Confirm Threshold — the distance threshold past which a selection is made (zero disables it).

## Lights

Studio Lights — these light the 3D Viewport during Solid View and aren't rendered; unlike scene lights, their direction tracks the viewport's orientation.
Editor — you get up to four virtual light sources. The Light toggles switch individual lights on or off, though at least one of the four has to stay enabled for the 3D Viewport. The lights are identical apart from direction and color, and you can set each one's direction along with its diffuse and specular colors.
  Use Light — toggles that light.
  Diffuse — the light's constant color.
  Specular — the light's highlight color.
  Smooth — softens this light's shading, making the lighting less direct.
  Direction — the light's direction (see Direction Buttons); it matches what's shown on the sphere's surface.
  Ambient Color — the color of unlit areas.

MatCaps — this panel handles MatCap image files used to light the view when MatCap shading is on. Two image kinds are supported: regular image files and multilayered OpenEXR files. With multilayered OpenEXR, the "diffuse" layer serves as the diffuse pass and the "specular" layer as the specular pass; regular images count as "diffuse" only and have no specular highlighting. The diffuse pass multiplies the objects' base color and the specular pass adds on top, so MatCaps with only a diffuse pass tend to look metallic, while a separate specular pass lets you fake a wider range of materials.

HDRIs — this panel handles HDRI image files used to light the view when Material Preview or Rendered shading is on.

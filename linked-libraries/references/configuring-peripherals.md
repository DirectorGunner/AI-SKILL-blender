# Configuring Peripherals, Help System, Data Properties, Editing Nodes

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Configuring Peripherals; Help System; Data Properties; Editing Nodes.

## Configuring Peripherals

### Configuring Peripherals

### Displays

A full-HD display (1920x1080) or larger is recommended. Multi-monitor setups work, and workspaces can be set to span several monitors.

Example of Blender's multi-monitor support.

### Input Devices

Blender supports several kinds of input device:

- Keyboard (recommended: one with a numeric keypad; an English layout works best)

- Mouse (recommended: a three button mouse with scroll wheel)

- Graphic Tablet

- Touchpad

- NDOF Device (also known as 3D Mouse )

Note

Lacking a middle mouse button or numeric keypad, you can emulate either in the Input Preferences. Bear in mind that emulation can cost you some shortcut keys, so use the recommended hardware where you can.

### Mouse

Many Blender interactions use the middle button (a press of the scroll wheel) or the wheel itself. That's why the recommended mouse is a two-button one whose added scroll wheel doubles as a middle button (in effect a 3-button mouse). It gives the smoothest workflow across all of Blender's modules.

#### Mouse Button Emulation

Without a 3 button mouse, tick the emulation option in the Preferences. The combinations are:

| 3-button Mouse | LMB | MMB | RMB |
| 2-button Mouse | LMB | Alt - LMB | RMB |

### Keyboard

Many interactions use the keyboard's number pad (or numpad): the block of 10 number keys plus math functions on the right of a traditional 104-key full-size keyboard. It makes for the most efficient workflow across all of Blender's modules.

#### Numpad Emulation

Without a side numpad you can emulate one and use the top number row instead, at the cost of those keys' usual jobs (such as switching vertex/edge/face selection in Edit Mode).

See also

More on Numpad Emulation in the Preferences.

#### Non-English Keyboards

On a non-English layout, switching to a UK or US layout while working in Blender can still help.

Note

You can also change the keymap in the Preferences. However, this manual assumes you use the default keymap.

### Touch Screens

Several settings can be turned on to improve the experience on touch-enabled devices. They make areas, menus, and interactions easier to handle without precise mouse input.

- Turn on Show Handles
to make resizing and rearranging Areas simpler.

- Raise the Border Width
so area edges are easier to grab with a finger.

### Graphic Tablet

A graphics tablet lets you drive the cursor with a pen — a more traditional approach that feels familiar to artists used to painting and drawing with such tools, and that adds extras like pressure sensitivity.

Note

If you use a tablet instead of a mouse and pressure sensitivity misbehaves, park the pointer in the Blender window, then unplug and replug the tablet. That sometimes helps.

### Touchpad

Touchpad controls work on Windows, macOS, and Linux with Wayland. On a laptop without a mouse, you can emulate controls through multi-touch trackpad gestures, set in the Preferences.

| Gesture | Effect |
| Pan | Drag two fingers on the pad while holding Shift . |
| Zoom | Drag two fingers on the pad while holding Ctrl or OSKey . |
| Orbit | Drag two fingers on the pad. |
| Emulate right-click | Tap the pad with two fingers. |

### NDOF (3D Mouse)

3D mice, or NDOF devices, are hardware for navigating a Blender scene. Only 3Dconnexion units, such as the SpaceMouse™, are supported at present. They let you roam a scene and make Fly/Walk Navigation easier to steer. The NDOF device is set up in the Preferences, and those settings are also reachable straight from the viewport via the NDOFMenu button on the device.

See also

Input Preference covers configuring peripherals in more depth.

### Head-Mounted Displays (Virtual Reality)

HMDs drop the user into an interactive virtual environment. Worn on the head, they track head motion and project a seemingly all-around world onto small screens before the eyes. When it all works, the wearer feels genuinely inside that environment.

### Supported Platforms

Blender's virtual reality support is built on the cross-platform OpenXR standard. Being new, that standard still has limited support.

| Platform | Operating System | Notes |
| HTC Vive Cosmos | Windows | Developer Preview |
| HTC Vive Focus 3 | Windows | Developer Preview |
| Monado | GNU/Linux | Not recommended for general use yet. |
| Meta (formerly Oculus) (Rift and Quest) | Windows | Requires Oculus v31 Software Update. Oculus Link required for Quest. |
| SteamVR | Windows, GNU/Linux | Requires SteamVR 1.16 or greater. |
| Varjo | Windows | – |
| Windows Mixed Reality | Windows | Requires Windows 10 May 2019 Update (1903). |

### Getting Started

The subsections below explain how to set up an HMD on each supported platform. Skip the setup and Blender will throw an error when you try to begin a virtual reality session.

#### HTC Vive Cosmos

Its dedicated platform is aimed at developers for now and may miss features other platforms have.

- Follow the steps on the
Vive Developer Forums.

- Turn on Blender's VR Scene Inspection add-on.

#### HTC Vive Focus 3

Its dedicated platform is likewise developer-focused for now and may lack some features.

- Follow the steps on the
Vive Developer Forums.

- Turn on Blender's VR Scene Inspection add-on.

#### Monado

Monado is a free, open-source XR platform for Linux. It isn't production-ready yet and should be used only for testing.

- Packages exist for these distributions:

- Ubuntu (Eoan, Focal)

- Debian (bullseye,
sid)

Elsewhere you'll have to build it from source — not advised if you have little experience compiling software. If you go ahead anyway, follow Monado's Getting Started Guides.

- Turn on Blender's VR Scene Inspection add-on.

#### Meta (formerly Oculus)

Meta (formerly Oculus) gained full OpenXR support with the Oculus v31 Software Update.

- Grab and install the Oculus Rift/Oculus Link software.

- Make Oculus the active OpenXR runtime from the General tab of the Oculus App Settings.

- Turn on Blender's VR Scene Inspection add-on.

Passthrough Support

Over OpenXR, passthrough is off by default in the Quest Link app and must be switched on in that app's settings to use it.

Passthrough render performance tracks the connection quality between headset and computer. For better results, wire the headset straight to the PC over USB, or at least put the computer on the local network via Ethernet.

#### SteamVR

SteamVR has had full OpenXR support since SteamVR 1.16.

- Make SteamVR the active OpenXR runtime from the Developer tab of the SteamVR Settings.

- Turn on Blender's VR Scene Inspection add-on.

Note

The SteamVR runtime also covers HTC Vive Cosmos, Oculus, and Windows Mixed Reality HMDs.

#### Varjo

Varjo ships full OpenXR support through its required Varjo Base software.

- Turn on Blender's VR Scene Inspection add-on.

#### Windows Mixed Reality

Windows Mixed Reality has full OpenXR support.
To see whether a PC can run it, Microsoft offers the
Windows Mixed Reality PC Check
application.

- Confirm the Windows 10 May 2019 Update (1903) is installed.

- If the system qualifies, the Mixed Reality Portal is probably already installed. It's also in the Microsoft Store.

- Open the Mixed Reality Portal. Click the ... menu button at the lower left. In the menu that opens, choose Set up OpenXR .

- Turn on Blender's VR Scene Inspection add-on.

Note

To move to Windows Mixed Reality from another OpenXR runtime (SteamVR, say), pull the OpenXR Developer Tools off the Microsoft Store, then make Windows Mixed Reality the active runtime.

## Help System

### Help System

Blender offers a mix of built-in and web-based help.

### Tooltips

Tooltip of the Renderer selector in the Info Editor.

Hover the cursor over a button or setting for a moment and a tooltip pops up.

### Elements

A context-sensitive tooltip may include some of these:

Short Description
Relevant details that depend on the control.

Shortcut
A keyboard or mouse shortcut tied to the tool.

Value
The property's value.

Hovering over a color property shows a large swatch preview of the color plus its hex, RGBA, and HSVA values.

Tooltip showing color information.

Library
The active object's source file. See also Linked Libraries.

Disabled (red)
Why the value can't be edited.

Python
With Python Tooltips on, it shows a Python expression you can script with — usually an operator or a property.

### Context-Sensitive Manual Access

Reference

Mode :

All modes

Menu :

Context menu ‣ Online Manual

Shortcut :

F1

Sometimes you'll want a tool's or area's help from inside Blender.

To do so, hover over the tool or button you need help with, then use the keyboard shortcut or context-menu item to jump to pages of this reference manual from within Blender. A web page for the button under the cursor opens — it works for both tool and value buttons.

Note

Coverage isn't 100% yet. The info header may warn you when a tool has no manual link.

In other cases, a button may point to a broader section of the documentation.

### Help Menu

### Web Links

The menu's first entries link straight to Blender-related websites, the same links found on the Splash Screen.

Manual
A link to the Official Blender Manual (what you're reading now).

Support
Links to assorted sites offering both community and professional support.

User Communities
Lists of many community sites and support venues.

Get Involved
Ways to support the Blender community, by helping on projects or donating.

Release Notes
A link to the current Blender version's release notes.

Report a Bug
The Blender Bug Tracker (registration required). For more on bug reporting, see Reporting a Bug.

### Save System Info

This pulls together system information handy for bug reports, configuration checks, or troubleshooting.

You'll be asked to save a text file named system-info.txt .

It holds these sections:

Blender
The Blender version, build-configuration details, and the path Blender runs from.

Python
Your Python installation's version and path.

Directories
The paths for scripts, data files, presets, and temporary files. They're configured in the Preferences Editor.

FFmpeg
The versions of the installed FFmpeg components and codecs.

Other Libraries
Versions of other libraries Blender uses, such as OpenColorIO, Alembic, USD, etc.

GPU
The GPU vendor and version, plus your hardware's and driver's capabilities.

Implementation Dependent GPU Limits
Limits on GPU functions stemming from how this Blender build was compiled.

Cycles
The instruction sets and capabilities of every hardware render device available to Cycles.

Enabled Add-Ons
The active add-ons with their versions and paths.

## Data Properties

Grease Pencil Object Data shown. Grease Pencil: Data-block menu links data between objects.

Layers: Strokes group in 2D layers, organizing drawing order and visibility. Layer groups organize layers.

Onion Skinning: Shows multiple frames simultaneously for animation decisions.

Settings: General stroke settings.

Attributes: Layers store Custom Attributes on the Layer domain, e.g., Layer Adjustments. Attributes: List of layer attributes. Name: Attribute name. Data Type: Attribute type.

Vertex Groups: Groups assign to operators or weighted variants; Weight Paint Mode assigns.

Custom Properties: Create and manage Grease Pencil data-block properties.

## Editing Nodes

Transform (Node ‣ Move, Rotate, Resize; G, R, S): move selected node(s) by clicking and dragging any empty part of them, or press G, move the mouse, and click LMB to confirm. Dragging a node onto an existing link smartly inserts it into the link path, generally using the first socket that matches the link type; toggle this automatic node attachment with Alt. When a node auto-attaches, the surrounding nodes shift right or left depending on the T toggle (see Auto-Offset). While dragging, press F to toggle the nodes' parent Frame: nodes inside a frame are detached from it, and nodes outside one with a frame under the cursor are attached to it. As a rule, arrange nodes so data flows left to right, top to bottom. Drag a node's left or right border to change its width. Rotating (R) and scaling (S) apply only when multiple nodes are selected and only affect their positions.

Connecting Sockets: LMB-click a socket and drag — a line ("Connect to Output") emerges, called a link; keep dragging to an input socket of another node and release LMB. An output socket can feed many links, but an input socket typically takes only one, unless it's a multi-socket input (shown as a pill-shaped socket). Hold Alt while moving a link to swap multiple links of a similar type, which also works when adding a new link into a pre-existing socket. Hold Ctrl while dragging from an output socket to reposition a node's outgoing links rather than add a new one (works for single and multiple outgoing links). A node with no connections can be inserted on a link by moving it over the link and releasing when the link highlights.
Make Links (J) — select multiple nodes with open sockets, then use Make Links to create links between them; use it again to connect any other nodes that can be.
Make and Replace Links (Shift-J) — works like Make Links, but replaces existing links where present.

Disconnecting Sockets:
Interactively — drag a link away from its input socket and release it, leaving it unconnected.
Mute Links (Node ‣ Mute Links; Ctrl-Alt-RMB) — activate the menu item or hold the key combination, then draw a line across one or more links to mute/unmute them; a muted link acts as though it's no longer there, which also makes the input fields for fixed values visible again. Muting the links on a reroute node's input side mutes its output side too.
Cut Links (Node ‣ Cut Links; Ctrl-RMB) — activate the menu item or hold the key combination, then draw a line across one or more links to delete them. Note: that combination is normally reserved for Lasso Select; in node editors lasso selection is instead done with Ctrl-Alt-LMB.
Detach Links (Alt-LMB drag) — cut all the links attached to the selected nodes and move the nodes to a new location.

Cut/Copy/Paste (Node ‣ Cut, Node ‣ Copy, Node ‣ Paste; Ctrl-C, Ctrl-V): these operators transfer nodes within a node tree, between different trees, or even between Blender instances.
Cut — remove the selected nodes onto the clipboard, reconnecting links where possible to preserve the node flow.
Copy (Ctrl-C) — copy the selected nodes to the clipboard, including the connections between them.
Paste (Ctrl-V) — insert the clipboard nodes into the node tree. Note: pasted nodes land at the same coordinates they were copied from, with the same considerations as duplicating nodes. Tip: copy/paste works between Blender instances and across different node editors, provided the destination editor supports the node types.

Duplicate (Node ‣ Duplicate; Shift-D): select one or more nodes, activate the menu item or press the key combination, then move the mouse and click LMB (or press Return) to place the duplicate(s). Note: a duplicate is positioned exactly on top of its original, which is easy to miss — when unsure, select a node and move it slightly to see whether another hides underneath.
Duplicate Linked (Node ‣ Duplicate Linked; Alt-D): duplicate selected nodes but not their node trees (for group nodes), and move them.
Delete (Node ‣ Delete; X, Delete): delete the selected node(s).
Delete with Reconnect (Node ‣ Delete; Ctrl-Delete): delete the selected node(s), then create new links connecting their former input nodes to their former output nodes.
Swap (Node ‣ Swap; Shift-S): replace the selected node with another node type chosen from the menu.

When swapping nodes, existing connections auto-reconnect where possible, matching sockets by name and type; unmatched connections remain unconnected.

Muting (M) disables a node's contribution, making all links pass through as if unchanged (red appearance signals muting). Individual links can be muted separately via Mute Links.

Node Preview (Shift+H) shows/hides a preview region displaying the result after that node's operation (compositing only). Click the material ball icon to toggle.

Node Options shows/hides all node properties.

Unconnected Sockets (Ctrl+H) collapses/expands sockets with no external connections.

Collapse (H) hides the node body, displaying only the header; click the left triangle to toggle.

Collapse and Hide Unused Sockets applies both operations.

Read View Layers (Ctrl+R) loads current scene render layers from cache if Cache Result is enabled (compositing only), saving RAM and recovering render data.

Connect to Output (Shift+Alt+LMB) links the selected node's output to the final output (Material Output, World Output in Shader; Group Output in Geometry Nodes/Compositor; Output in Texture Nodes), or to Group Output if inside a group.

# Installing On Linux, Object Properties, Settings, Blur Visual Effect ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Installing on Linux; Object Properties; Settings; Blur Visual Effect; Eyedropper; Default Keymap; Industry Compatible Keymap; Status Bar.

## Installing on Linux

### Installing on Linux

If you haven't already, check the Downloading Blender page for the minimum requirements and the available versions.

### Install from blender.org

Download the Linux build for your architecture and unpack it wherever you like (e.g. ~/software or /usr/local ).

Double-click the executable to launch Blender.

Installed this way, several Blender versions can coexist.

For convenience you might add a menu entry and set up blend-file associations for the file browser, both done by Registering Blender.

For a completely self-contained install — configuration and all — arrange a Portable Installation.

### Install from a Package Manager

Some Linux distributions carry a Blender package in their repositories.

Going through the distribution's own machinery keeps Blender consistent with the rest of the system and can add niceties from the package manager — package listing, update notices, automatic menu setup. Bear in mind, though, that the packaged version may lag the latest official release or drop some features. Some distributions, for licensing or other reasons, build Blender without Cycles GPU rendering support.

Where your distribution has a package, pick whichever is handiest. Otherwise the official binary is on blender.org.

### Install from Snap

Snap is a universal package manager meant to span many distributions. With snap already present, install Blender via:

```text
snap install blender --classic
```

One perk here: Blender updates install themselves. The Snap build also tends to be more consistent than the various per-distro packages.

### Running from the Terminal

See Launching from the terminal.

### Graphics System (X11 & Wayland)

Blender supports both X11 and Wayland. See Linux Windowing Environment for details.

### Avoiding Alt-Mouse Conflict

Some window managers use Alt - LMB and Alt - RMB by default to move and resize windows.

Blender needs those combos for several things, notably:

- Emulate 3 Button Mouse.

- Select Edge Loops.

- Changing several properties at once.

To free up the full feature set, point the window manager at the Meta key instead (also called Super or the Windows key):

Gnome
Run this on a command line (takes effect at next login):

```text
gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier ' '
```

KDE
Under System Settings ‣ Window Management ‣ Window Behavior ‣ Window Actions ,
switch the key from 'Alt' to 'Meta'.

### Updating on Linux

There are two ways to update Blender on Linux. This section covers the common ones.

### Updating from blender.org

When a new release lands, download it from the Blender website and install it via the steps in Install from blender.org.

### Updating with a Package Manager

Many Linux distributions package Blender for their package manager. Once installed, you update it just like any other application.

See also

The Splash-screen Defaults page, on importing settings from earlier Blender versions and other quick options.

### Known Limitations

### Archive Extraction

Unpacking Blender's archive with 7-zip isn't supported. Use TAR instead. See issue #104070 for more.

## Object Properties

Visibility subpanel. Reference: Object Properties ‣ Visibility

Use Light: Enables light effect on the object. Object-wide setting; per-layer control available in Layers. See also: General visibility properties.

## Settings

General stroke settings shown in Settings panel. Stroke Depth Order: 3D space ordering (non-In Front objects).

2D Layers: Stroke order follows 2D layer order (top to bottom), ignoring 3D position. See 2D Layers.

Note: Affects scene Grease Pencil compositing; 2D-order objects render at their bounding-box midpoint depth.

Tip: Keep objects mostly flat with 2D ordering for correct compositing!

3D Location: Stroke order follows 3D position. Blue, Green, Red layers shown with 2D Layers and 3D Location ordering.

Reference — Panel: Physics ‣ Fluid ‣ Settings; Type: Domain.
The domain object contains the entire simulation: fluid can't leave it, instead colliding with the edge or disappearing depending on the domain's settings. Larger domains need higher resolutions and longer bake times, so make it just big enough to fit the simulation but no larger than necessary. To create one, add a cube and transform it (translation, rotation, and scaling all allowed) until it encloses the simulation area, then click Fluid in the Properties ‣ Physics tab and set the fluid Type to Domain.
Note: you can use other mesh-object shapes as domain objects, but the fluid simulator uses the shape's Bounding Box as the domain bounds, so the actual domain stays rectangular.

Domain Type — a fluid domain controls either liquid or gas flows: liquid domains consider all liquid flow objects intersecting the domain, while gas domains consider all intersecting Smoke, Fire, and Smoke & Fire flow objects; the domain type can't be changed dynamically.
Resolution Divisions — the domain is subdivided into many "cells" called Voxels that form the fluid's "pixels," and this sets the number of subdivisions; more subdivisions is one way to make higher-resolution fluids. Since resolution is defined in "subdivisions," larger domains need more divisions for an equivalent resolution — for example, a one-meter cube at 64 Resolution Divisions needs 128 to match a 2-meter cube — with the base division taken from the longest dimension of the object's bounding box. To help visualize the voxel size, the Resolution Divisions can be previewed with a small cube shown in the 3D Viewport.
Time Scale — controls the simulation speed: low values give a "slow motion" sim, while higher values advance it faster (good for generating fluids for still renders).
Adaptive Time Steps — let the solver automatically decide when to run multiple simulation steps per frame, taking into account the maximum and minimum number of time steps, the current Frame Rate, and the Time Scale.
CFL Number — the maximum velocity per grid cell, measured in grid cells per time step; fluid may move only up to this velocity in one step, and exceeding the threshold makes the solver subdivide the step. In general, a greater CFL (Courant–Friedrichs–Lewy) number minimizes the number of simulation steps and computation time but yields less physically accurate behavior for fast flows, while a smaller CFL number means more steps per frame and longer simulation times but more accurate behavior at high velocities (e.g. fast fluid flow colliding with an obstacle).
Note: when lowering the CFL number it's recommended to increase the maximum number of time steps; similarly, when increasing the CFL number, adjust the minimum.
Timesteps Maximum — the maximum number of time steps allowed per frame; the solver divides a step up to this many sub-steps if needed.
Timesteps Minimum — the minimum number of time steps allowed per frame; the solver always performs at least this many per frame.
Gravity — by default the fluid solver uses the global scene gravity; disabling that (in the scene settings) enables the fluid gravity options.
Empty Space (Gas Only) — voxels with values under this count as empty space; more empty space optimizes rendering and, with OpenVDB caching, also reduces cache sizes.
Delete in Obstacle — remove any volume of fluid that intersects an obstacle inside the domain.

Border Collisions (Panel: Physics ‣ Fluid ‣ Settings ‣ Border Collisions; Type: Domain (Gas)) — control which sides of the domain let fluid "pass through" (making it disappear without influencing the rest of the simulation) and which sides deflect fluid.

Gas (Panel: Physics ‣ Fluid ‣ Gas; Type: Domain (Gas)):
Buoyancy Density — buoyant force based on gas density: values above 0 make the gas rise (lighter than ambient air), values below 0 make it sink (heavier than ambient air).
Buoyancy Heat — how much temperature affects the gas, depending on each flow object's Initial Temperature: above 0, gas rises when the flow object's Initial Temperature is positive and sinks when it's negative; below 0, the opposite (gas from a positive Initial Temperature sinks, gas from a negative one rises). Gas from multiple flow objects with different temperatures mixes and warms up or cools down until an equilibrium is reached.
Vorticity — the amount of turbulence in the gas: higher values make lots of small swirls, lower values make smoother shapes (e.g. a vorticity of 0.0 vs 0.2).
Dissolve — allow gas to dissipate over time.
- Time: the speed of gas dissipation in frames.
- Slow: dissolve gas in a logarithmic fashion — quickly at first, but lingering longer.

Fire (Type: Domain; Panel: Physics ‣ Fluid ‣ Gas ‣ Fire):
Reaction Speed — how fast fuel burns: larger values give smaller flames (fuel burns before going far), smaller values give larger flames (fuel flows farther before being fully consumed).

Flame Smoke

Specifies the quantity of extra smoke created to replicate burnt fuel in flames. The resulting smoke becomes most apparent when a "Fire + Smoke" Flow Object is employed.

Vorticity

Contributes vorticity to flames in addition to the domain's baseline vorticity.

Temperature Maximum

Sets the upper limit for flame temperature. Higher temperatures cause flames to rise faster.

Minimum

Establishes the lower limit for flame temperature. Higher temperatures cause flames to rise faster.

Smoke Color

Defines the hue of smoke released from burning material.

### Liquid 

Reference

Type :

Domain

Panel :

Physics ‣ Fluid ‣ Liquid

Liquid settings govern the particles that comprise the simulation. Enabling the liquid checkbox automatically generates a particle system to visualize the simulation's flow. Displaying liquid particles remains optional; the simulation utilizes all fields regardless of whether an attached particle system exists.

Note

Unchecking the liquid checkbox removes the associated particle system and its configuration.

Simulation Method

Determines which particle simulation method governs the liquid behavior.

FLIP :

(FLuid Implicit Particle)
Generates highly splashy simulations with numerous particles suspended in air.

APIC :

(Affine Particle-In-Cell)
Yields an energetic yet more balanced simulation. This method retains vortices better compared to FLIP.

FLIP Ratio Simulation FLIP Only :
Specifies what proportion of FLIP velocity influences updates to liquid particle velocities. A setting of 1.0 enforces purely FLIP-based behavior. Entirely FLIP-based simulations exhibit more chaotic splashes and work well for large liquid volumes. Lower values produce less turbulent behavior with gentler splashes, making them suitable for small-scale scenarios.

System Maximum

Caps the total fluid particles allowed within the simulation. When nonzero, the simulation respects this limit. At zero, the solver continuously samples new particles as needed.

Particle Radius

Specifies the radius of an individual liquid particle in grid cell units. This dimension indicates the coverage area of each particle and determines how much surrounding space qualifies as liquid. Larger radii expand the coverage area, causing more grid cells to register as liquid rather than empty space.

When simulations leak or produce unphysical volume changes, this value warrants adjustment. Increasing it addresses disappearing liquid, while decreasing it handles excess production.

Sampling

Multiplier that determines particle sampling quantity. Higher settings yield more particles. Resampling occurs at every simulation substep.

Randomness

New particles receive randomized positioning within their source regions, with this field controlling the degree of randomization. Higher values generate particles with greater positional variation at inflow sites. A zero setting places all new particles uniformly throughout their grid cells.

This parameter proves valuable when establishing laminar inflows with minimal variation or turbulent flows with pronounced variation.

Particles Maximum

Establishes the upper particle count per grid cell. As simulation progresses, cell particle populations fluctuate through movement and removal. Resampling adds particles within this constraint.

This threshold indicates the peak particles per cell and facilitates pre-bake estimation of total particle count (grid resolution also factors into this calculation).

Minimum

Sets the lower particle count threshold per grid cell. Similar to the maximum value, this ensures each cell maintains a baseline particle population.

Narrow Band Width

Establishes the span in grid cell units of the narrow band confining liquid particles. Increased values thicken the band and may saturate inflow regions with particles. Unless particle visualization forms the primary objective, keeping the band narrow proves beneficial, since extra particles reduce simulation speed.

Increasing this value sometimes restores volume in leaking simulations. Otherwise, optimal performance results from the narrowest feasible band, as the liquid surface concentrates most geometric detail and computing resources are better spent there.

See also

The narrow band references Narrow Band FLIP for Liquid Simulations.

Fractional Obstacles

Activates higher resolution handling at fluid and obstacle boundaries, implementing second-order obstacle treatment. This reduces stepping artifacts that appear when inclined obstacles sit within the domain. Liquid movement flows more uniformly across obstacle surfaces.

Obstacle Distance

Determines the separation between fluid and obstacles. Increased values facilitate smoother liquid passage over inclined surfaces, with the adjustment depending on obstacle slope. Negative values permit fluid to penetrate obstacle interiors.

Obstacle Threshold

Manages the smoothness of fractional obstacle behavior. Lower values diminish stepping artifacts but risk particles adhering to obstacle surfaces.

Bake Data, Free Data

Available exclusively with Modular cache type. Bake Data calculates and archives the simulation foundation to disk. Both gas and liquid systems can layer refinements atop this base (noise for gas, mesh or secondary particles for liquids, or both).

The status bar displays progress. Pressing Esc pauses the simulation.

After completing the simulation bake, the cache becomes removable through Free Data. Bake All operations support pause and resume functionality.

## Blur Visual Effect

The Blur Visual Effect applies Gaussian blur. Samples: Blur sample count (0 disables). Use Depth of Field: Uses camera focal distance when active; camera-view only. Size X, Y: X/Y blur scale in pixels. Rotation: Blur rotation. Example: Original, Factor 10×10, Factor 50×50, Factor 100×100.

## Eyedropper

The eyedropper (pipette icon) samples from anywhere in Blender. Usage: Color—most common; samples pixel color. Note: View Transform affects results; set to Standard for consistency. Other settings return inaccurate color. Color Ramp—drag to sample a line converted to ramp. Objects/Object-Data—selects from Viewport/Outliner instead of drop-down. Bones—selects from Viewport/Outliner (Pose Mode/Edit Mode only). Camera Depth—sets depth-of-field via distance-field sampling. Shortcuts: E activates while hovering. LMB drag mixes sampled colors (noisy-imagery help). Spacebar resets color mixing.

## Default Keymap

### Default Keymap

Rather than a full catalog, what this page covers is the everyday keys of Blender's default keymap.

### Selecting
Two main selection modes ship with Blender: left-click select and right-click select. See the Select with Mouse Button preference.

### Hovering
Hover the cursor over an editable field and the shortcuts below become available.

### Properties

| Ctrl - C | Copy the (single) value of the field. |
| Ctrl - V | Paste the (single) value of the field. |
| Ctrl - Alt - C | Copy the entire vector or color of the field. |
| Ctrl - Alt - V | Paste the entire vector or color of the field. |
| RMB | Open the context menu. |
| Backspace | Reset the value to its default. |
| Minus | Invert the value's sign (multiply by -1.0). |
| Ctrl - Wheel | Change the value in incremental steps. For fields with a pop-up list of values, this cycles the value. |
| Return | Activates menus and toggles checkboxes. |
| Alt | Hold while editing values to apply the change to all selected items (objects, bones, sequence-strips). This can be used for number fields and toggles. |

### Dragging
The shortcuts below come into play while you move/rotate/scale an object in the 3D Viewport, drag a value slider, and so on. One catch: press them after the drag has begun, not before.

| Ctrl | Snap to coarse increments, making it easier to (say) rotate an object by exactly 90°. |
| Shift | Make the value change more slowly in response to mouse movement, giving you more precision. |
| Shift - Ctrl | Snap to fine increments. |

### General

| Ctrl - O | Open file. |
| Ctrl - S | Save file. |
| Ctrl - N | New file. |
| Ctrl - Z | Undo. |
| Shift - Ctrl - Z | Redo. |
| Ctrl - Q | Quit. |
| F1 | Help (context sensitive) . |
| F2 | Rename active item. |
| F3 | Menu Search . |
| F4 | File context menu. |
| F5 - F8 | Reserved for user actions. |
| F9 | Adjust Last Operation . |
| F10 | Reserved for user actions. |
| F11 | Show render window. |
| F12 | Render the current frame. |
| Q | Quick access (favorites). |
| Ctrl - Spacebar | Toggle Maximize Area . |
| Ctrl - PageUp / Ctrl - PageDown | Next/previous Workspace . |
| Spacebar | User configurable; see Spacebar Action . |
| Shift - Ctrl - Spacebar | Playback animation (reverse). |

### Common Editing Keys

| X | Delete the selected item with a confirmation dialog. |
| Delete | Delete the selected item without a confirmation dialog. |

### Common Editor Keys
Editors such as the 3D Viewport, UV and Graph editor all share these keys.

| A | Select all. |
| Alt - A / Double-tap A | Select none. |
| Ctrl - I | Invert selection. |
| H | Hide selected items. |
| Shift - H | Hide unselected items. |
| Alt - H | Reveal hidden items. |
| T | Toggle Toolbar. |
| N | Toggle Sidebar. |

### 3D Viewport Keys

| MMB | Orbit View |
| Shift - MMB | Pan View |
| Ctrl - MMB | Zoom View |
| Tab | Toggle Edit mode. |
| Ctrl - Tab | Toggle Pose mode for armatures, or show a mode switching pie menu for others. |
| 1 - 3 | In Edit Mode, switch between editing vertices ( 1 ), edges ( 2 ), or faces ( 3 ). Hold Shift to toggle one of these without disabling the others. Hold Ctrl to alter how the selection is transformed from the old mode to the new. See Mesh Selection Modes for details. |
| AccentGrave | Show 3D Viewport navigation pie menu. |
| Ctrl - AccentGrave | Toggle gizmos. |
| Shift - AccentGrave | Start Fly/Walk Navigation . |

See also

3D Viewport Navigation

### Animation

| I | Insert a keyframe . |
| Alt - I | Clear the keyframe. |
| Shift - Alt - I | Clear all keyframes. |
| Ctrl - D | Assign a driver . |
| Ctrl - Alt - D | Clear the driver. |
| K | Add the property to the current keying set . |
| Alt - K | Remove the property from the current keying set. |

### Python Scripting

| Ctrl - C | When pressed while hovering over an operator button , copies its Python command to the clipboard. This command can then be used in the Python Console or in the Text Editor when writing scripts. |
| Shift - Ctrl - C | When pressed while hovering over a field, copies its relative data path (also available from the context menu). Useful when writing drivers or scripts. |
| Shift - Ctrl - Alt - C | When pressed while hovering over a field, copies its full data path. |

### Platform Specific Keys

### macOS
On macOS the Cmd key stands in for Ctrl, save for a handful of exceptions that clash with the operating system.

List of additional macOS specific keys:

| Cmd - Comma | Preferences. |

## Industry Compatible Keymap

### Industry Compatible Keymap

Rather than a full catalog, what this page covers is the everyday keys of the industry compatible keymap.

### General

| 1 - 3 | Switch Selection mode |
| 4 | Object Mode |
| 5 | Modes Pie Menu |
| RMB | Context menu |
| Tab | Menu Search |
| Shift - Tab | Quick access (favorites) |
| Return | Rename |
| Ctrl - Return | Render |
| Ctrl - [ | Toggle Toolbar |
| Ctrl - ] | Toggle Sidebar |

### Common Editing Keys

| Backspace | Delete the selected item with a confirmation dialog |
| Delete | Delete the selected item without a confirmation dialog |
| Ctrl - D | Duplicate |
| P | Set Parent |
| B | Proportional Editing (a.k.a. Soft Selection) |

### Viewport

| Alt - LMB | Orbit View |
| Alt - MMB | Pan View |
| Alt - RMB | Zoom View |
| F1 - F4 | Front/Side/Top/Camera Viewpoints |
| F | Frame Selected |
| Shift F | Center View to Mouse |
| A | Frame All |

### Selection

| LMB | Select |
| Ctrl - A | Select All |
| Shift - Ctrl - A | Deselect All |
| Ctrl - I | Select Inverse |
| Up | Select More |
| Down | Select Less |
| Double LMB | Select Loop |
| Double Alt - LMB | Select Ring |
| Ctrl L | Select Linked |

### Tools

| W , E , R | Move, Rotate, Scale |
| Q | Selection Tools |
| D | Annotate Tool |
| C | Cursor Tool |

### Edit Mode Tools

| Ctrl - E | Extrude |
| Ctrl - B | Bevel |
| I | Inset |
| K | Knife |
| Alt - C | Loop Cut |

### Animation

| Spacebar | Play/Pause |
| S | Set Location + Rotation + Scale keyframe |
| Shift - S | Insert Keyframe menu |
| Shift - W | Set Location Key |
| Shift - E | Set Rotation Key |
| Shift - R | Set Scale Key |

### Platform Specific Keys

### macOS
On macOS the Cmd key stands in for Ctrl, save for a handful of exceptions that clash with the operating system.

## Status Bar

### Status Bar

Sitting along the bottom of the Blender window, the Status Bar surfaces contextual information — keyboard shortcuts, messages, and statistics. Hide it by switching off Show Status Bar in the Window menu, or by dragging down from its top edge.

Status Bar.

### Keymap Information
On the left, the Status Bar lists mouse button shortcuts and the active tool's keymap. In editors that carry a Toolbar, a tap of Alt (Option on macOS) reveals the hotkeys for switching to whichever tool you want.

Tip

Switch this behavior off through the Alt Click Tool Prompt preference over in the Keymap Preferences).

### Status Messages
In the middle, the Status Bar reports on operations still in progress.

Running Task
Tracks how far the task in flight has gotten (rendering or baking, say). Park the pointer over the progress bar and a time estimate appears. Click the cancel button ( ) to abort it.

Report Message
Notices or warnings — for instance, right after a file is saved. They fade out before long. A click opens the whole message in the Info Editor.

### Resource Information
On the right, the Status Bar reports on the Blender instance. Which details show is your call, set via RMB on the Status Bar or through the Preferences.

Scene Statistics
Reports on the data held in the active scene.

- Collection : The name of the active Collection.

- Active Object : The name of the active selected object.

- Geometry : Scene details that vary with the active mode and object type — a count of vertices, faces, triangles, or bones, for example.

- Objects : How many objects are selected, plus the overall object tally.

Scene Duration
Reports the full playback length together with the current frame and the total frame tally. How that duration text reads is set by the Timecode Style.

System Memory
Estimates how much RAM Blender is using. Run a single instance on a single machine and that figure gauges you against the machine's hardware ceiling.

Extensions Updates
Counts how many extensions have updates waiting.

Blender Version
Gives the version number of the Blender build now running.

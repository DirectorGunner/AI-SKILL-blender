# Tracks, Animation, Keymap, Python Console ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Tracks; Animation; Keymap; Python Console; Compatibility; Export Grease Pencil as PDF; Linux Windowing Environment.

## Tracks

A track plays one or more actions in sequence, and you can make several tracks to play multiple actions simultaneously.

The track region offers these properties:
Disable NLA stack (checkbox in the blue object header) — unchecked, mutes every track but the Action Track.
Track name — double-click to change (not possible for the Action Track, which just shows the action's name).
Mute (checkbox in the gray track header) — unchecked, the track stops contributing to the animation and its strips get a dotted outline; individual strips can be muted too.
Lock (padlock icon) — blocks changes to this track, handy when you want to move the strips in every track but a few.
Solo (star icon) — mutes all other tracks, the Action Track included, so only this one drives the animation, which is useful for inspecting a track without distraction.

Action Track — the topmost track, with the orange header, holds the action being edited. Normally that's the object's active action, but selecting a strip and pressing Tab for Tweak Mode temporarily makes that one editable instead — in the Action Editor or the Graph Editor, say. The Action Track carries one of these buttons:
Push Down Action — unavailable in Tweak Mode; makes a new track below the Action Track and moves the active action there as a strip, leaving the Action Track empty (key something afterward and Blender auto-creates a new active action to hold it).
Pin — available only in Tweak Mode; unchecked, the action's keyframes appear at their original time points rather than the new ones produced by moving and scaling the strip.

## Animation

The Animation section manages animation-related settings, covering how editors look as well as a few tool properties.

Timeline:
Allow Negative Frame — lets playback and animation happen during negative frame ranges.
Minimum Grid Spacing — the fewest pixels allowed between grid lines.
Timecode Style — the format for timecodes when timing isn't shown in frames.
  Minimal Info — the most compact form, using "+" to separate sub-second frame numbers and truncating left and right as needed.
  SMPTE (Full) — full SMPTE timecode (HH:MM:SS:FF).
  SMPTE (Compact) — SMPTE showing minutes, seconds, and frames only, adding hours when needed but not by default.
  Compact with Decimals — like SMPTE (Compact) but showing the second's decimal part instead of frames.
  Only Seconds — a straight conversion of frame numbers to seconds.
Zoom to Frame Type — sets which time range around the cursor shows when View Frame (Numpad0) runs.
  Keep Range — keeps the currently displayed time range.
  Seconds — shows the number of seconds set in Zoom Seconds around the cursor.
  Keyframes — shows the number of keyframes set in Zoom Keyframes around the cursor.

Keyframes — these control Keyframes, the building blocks of animation.
Default Key Channels — which channels to key when no keying set is active: Location, Rotation, Scale, Rotation Mode, or Custom Properties.
Only Insert Needed — keys only when the property's value has actually changed. Manual skips keys that don't affect the animation when keying by hand; Auto does the same for Auto-Keying.
Keyframing – Visual Keying — when an object uses constraints its property value doesn't really change, so Visual Keying keys the property using the visual transformation the constraint produces.
Auto-Keyframing:
  Enable in New Scenes — turns Auto Keyframe on by default for new scenes.
  Show Warning — shows a warning at the 3D Viewport's top-right while moving objects if Auto Keyframe is on.
  Only Insert Available — keys only channels of F-Curves that already exist.
  See also Auto-Keyframing.

F-Curves — these control how F-Curves look and behave by default.
Unselected Opacity — how opaque unselected F-Curves are against the Graph Editor's background.
Default Smoothing Mode — the default behavior of automatic curve handles on new F-Curves.
Default Interpolation — the default Interpolation for new keyframes.
Default Handles — the default Handle for new F-Curves.
XYZ to RGB — colors X, Y, or Z animation curves (location, scale, rotation) to match the X, Y, and Z axis colors.
Channel Group Colors — draws groups and channels in colors matching their groups.
Only Show Selected F-Curve Keyframes — shows keyframe markers only on the selected curves.
F-Curve High Quality Drawing — draws F-Curves with anti-aliasing and other effects (turn off for better performance).

## Keymap

On this screen you configure keyboard and mouse shortcuts. See also Keymap.

Presets — at the top you select and manage presets.
Keymap Presets — the selector offers built-in presets: Blender (the default keymap, the one this manual uses), Blender 27x (the legacy keymap from Blender 2.79 and earlier), and Industry Compatible (a keymap closer to other 3D editing apps).
Add Custom Keymap Configuration — adds a custom keymap configuration.
Remove Keymap Configuration — removes a custom keymap configuration.
Import — opens a File Browser to pick a .py file holding a custom preset.
Export — saves the current keymap configuration as a preset for others.
All Keymaps — off, only the shortcut assignments you've changed are exported (think of it as a "keymap delta"); on, the whole keymap is written.

Filtering — below the preset list you can filter the operations to quickly find one.
Filter Type — Name (filter operations by name, like New File) or Key Binding (filter by the currently assigned shortcut, like ctrl n).
Search — the text to search (blank shows every operation).

Preferences — these apply to the Blender keymap only.
Select with Mouse Button — which mouse button selects items. Left-click select is the default since it matches most software, but right-click select has workflow upsides in some cases.
  Left — LMB selects, RMB opens the context menu. Pros: familiar to users from other apps; context-menu access matches industry norms; easier transition from other 3D and design software. Cons: selection and transformation share the primary button, raising accidental movement near gizmos; placing the 3D Cursor needs a modifier (e.g. Shift-RMB).
  Right — RMB selects, LMB places the 3D Cursor. Pros: separates selection from transformation, cutting accidental edits during modeling; quick, direct 3D Cursor placement with LMB; historically tuned for precision modeling. Cons: less familiar to newcomers; the context menu needs an alternate shortcut depending on configuration.
Spacebar Action — what Spacebar does. Play (starts/stops playback, good for animation or video editing), Tools (opens the Toolbar under the cursor to swap the active tool fast, good for lots of modeling or rigging), or Search (opens Menu Search, good for newcomers unfamiliar with the menus and shortcuts — though F3 reaches search regardless). With Tools, you can pick a tool several ways: press Spacebar then click one; hold Spacebar, move to a tool, and release; press Spacebar then the key shown in the popover (e.g. T for Transform); or press Spacebar and the tool's key together (e.g. Spacebar-T for Transform). If you pick something other than Play, Shift-Spacebar starts/stops playback instead.
Activate Gizmo Event — the event that activates drag-capable gizmos; available only when Select with Mouse Button is Left. Press (the gizmo's operation starts, with extra options in the Status Bar, the moment you press the mouse button on it) or Drag (it starts only once you begin dragging).
Tool Keys — how tool-activation shortcuts behave. Immediate (the tool is in use at once — press Ctrl-B while editing a mesh and a Bevel starts straight away, mouse to size it, LMB to confirm) or Active Tool (the tool is merely selected, as if clicked in the Toolbar — press Ctrl-B and the Bevel tool is selected with its gizmo visible, and you drag the gizmo to bevel).
Alt Click Tool Prompt — tapping Alt shows a status-bar prompt for a second keystroke to activate the tool; unavailable with Emulate 3 Button Mouse.
Alt Tool Access — holding Alt lets you use the Active Tool where the gizmo would normally be needed (with the Move tool selected, say, hold Alt and drag anywhere in the viewport to move the selection rather than dragging its gizmo); available only when Select with Mouse Button is Left and Emulate 3 Button Mouse is off.
Select All Toggles — makes the Select All shortcut A deselect all whenever a selection exists.
Region Toggle Pie — with this on, N raises a pie menu for toggling Regions instead of always toggling just the Sidebar.

3D Viewport:
Grave Accent / Tilde Action — Navigate (a Viewpoint pie menu, handy without a numeric keypad) or Gizmos (a Transform-gizmos pie menu for switching gizmos fast; it doesn't apply to tools that force a gizmo — Move, Rotate, Scale, Transform — where the gizmo stays put whatever you pick).
Middle Mouse Action — what MMB dragging does in the viewport (trackpads too). Orbit (orbits the view around a central point, with Shift-MMB for panning).

Pan — pans the view, with Shift-MMB for orbiting.
Alt Middle Mouse Drag Action — how the new viewpoint is decided when dragging Alt-MMB. Relative (the result depends on both the mouse direction and the current viewpoint — dragging horizontally rotates 90° around the view's current vertical axis) or Absolute (the result depends only on the mouse direction — drag right and you always end up looking from the positive side of the global X axis).
Tab for Pie Menu — normally Tab toggles Edit Mode while Ctrl-Tab opens a pie menu of all modes; this option swaps the two shortcuts.
Pie Menu on Drag — when on, certain keys act differently when tapped versus held-and-dragged (which shows a pie menu):
  Tab — Tap: toggle Edit Mode. Drag: show the Object Mode pie menu.
  Z — Tap: toggle wireframe view. Drag: show the Viewport Shading pie menu.
  AccentGrave — Tap: start first-person Fly/Walk Navigation. Drag: show the viewpoint pie menu.
Extra Shading Pie Menu Items — adds more items to the shading menu (Z key).
Transform Navigation with Alt — requires holding Alt to navigate the view while transforming something, in exchange for not needing Alt for certain other operations. For example, with it off, MMB drag always orbits and Alt-MMB locks movement to an axis while moving an object; with it on, those invert while moving — MMB does the axis lock, and you use Alt-MMB to orbit, Shift-Alt-MMB to pan, and Alt-Wheel to zoom. It also applies to Proportional Editing (where Wheel sizes the influence area) and Auto IK (where Wheel sets the temporary IK chain's length): with it off, Wheel zooms the view and you use Alt-Wheel to change those. See also Transform Modal Map.
File Browser:
  Open Folders on Single Click — enter folders with one click rather than two.

Editor — the Keymap editor is where you reassign the default hotkeys for every one of Blender's editors.
Usage: find the operation whose shortcut you want to change (filtering helps); decide whether a keyboard key, a mouse button, or some other input should trigger it; then click the button at the right and press the shortcut you want.
Active — uncheck to disable this keymap item.
Map Type — Keyboard (a single hotkey or combination), Mouse (mouse-button, tablet, or touchpad input), NDOF (movement or a button from a 3D-mouse device), Tweak (mouse click-and-drag, optionally mapping drag direction to different actions), Text Input (used by entering text), or Timer (for Blender's internal use).
Operator ID Name — the identifier of the operator to call. Hint: see bpy.ops for the operator list (drop the bpy. prefix for the identifier).
Event:
  Type — the key or button that fires this item (per the map type).
  Value — the action (press, release, click, drag, etc.; per the map type).
  Modifier — extra keys to hold (Ctrl, Shift, Alt).
  Operator Properties — starting values for the operator's own properties.
See also Keymap Customization.
Restoring — to restore a keymap's defaults, click the Restore button at its top-right. Tip: rather than editing the default keymap, you can add a new one.

Known Limitations — Blender Versions: the trouble with editing your own keymap is that newer Blender versions may change how tools are reached, breaking your customizations. The keymap can be updated by hand, but the more you've changed, the likelier conflicts become in newer versions.

### Keymap

### Conventions Used in This Manual

### Keyboard
Throughout this manual, hotkeys appear the way they sit on a keyboard. For example:

| G | The "G" key by itself (as though you were typing a lowercase "g"). |
| Shift , Ctrl , Alt | Modifier keys. |
| Ctrl - W , Shift - Alt - A | Keys pressed simultaneously. |
| 0 to 9 | The number keys on the row above the letters. |
| Numpad0 to Numpad9 , NumpadPlus | The keys on the separate numeric keypad. |

Remaining keys go by name — Esc, Tab, and F1 through F12. The arrow keys are written Left, Right, and so on.

### Mouse
Here is how mouse buttons and wheel actions are named:

| LMB | Left Mouse Button |
| RMB | Right Mouse Button |
| MMB | Middle Mouse Button |
| Wheel , WheelUp , WheelDown | Scrolling the mouse wheel. |

### Built-in Keymaps
Two keymaps come built into Blender:

Blender
The default keymap, used throughout this manual.

Industry Compatible
A keymap that more closely matches the shortcuts of other 3D editing applications.

### Customizing
Both keyboard and mouse shortcuts can be tailored in the Preferences.

## Python Console

The Python Console is a fast way to try out code snippets and poke around Blender's API. It runs whatever you type at its >>> prompt and offers command history and auto-complete.

Interface — Header Menus — View Menu:
Zoom In / Zoom Out — grows/shrinks the font size.
Move to Previous Word (Ctrl-Left) — sends the cursor to the previous word's start; mid-word, to the current word's start.
Move to Next Word (Ctrl-Right) — advances the cursor to the next word's end; mid-word, to the current word's end.
Move to Line Begin (Home) — moves the cursor to the current line's start. Shift-Home selects from the cursor to the line's start.
Move to Line End (End) — moves the cursor to the current line's end. Shift-End selects from the cursor to the line's end.

Console Menu:
Clear All — wipes the console for a fresh view; the command history stays.
Clear Line (Shift-Return) — empties the prompt line.
Delete Previous Word (Ctrl-Backspace) — deletes from the cursor back to the start of the previous word (split on periods); mid-word, back to the current word's start.
Delete Next Word (Ctrl-Delete) — deletes from the cursor to the end of the next word; mid-word, to the current word's end.
Copy as Script (Shift-Ctrl-C) — copies the whole history buffer to the clipboard, ready to paste into a text file as a Python script.
Cut (Ctrl-X) — copies the selected text to the clipboard and removes it.
Copy (Ctrl-C) — copies the selected text to the clipboard.
Paste (Ctrl-V) — pastes onto the command line.
Indent (Tab) — inserts a tab character at the cursor.
Unindent (Shift-Tab) — unindents the selection.
Backward in History (Up) — replaces the current command with the previous one from history.
Forward in History (Down) — replaces the current command with the next one from history.
Autocomplete (Tab) — see Auto Completion.

Main View — Key Bindings:
LMB — moves the cursor along the input line.
Left / Right — moves the cursor one character.
Ctrl-Left / Ctrl-Right — moves the cursor one word.
Shift-Left / Shift-Right — selects characters to the left/right.
Shift-Ctrl-Left / Shift-Ctrl-Right — selects words to the left/right.
Ctrl-A — selects all text and text history.
Backspace / Delete — erase characters.
Ctrl-Backspace / Ctrl-Delete — erase words.
Return — execute command.
Shift-Return — add to command history without executing.

Usage — Aliases: a few variables and modules are provided for convenience:
C — shorthand for bpy.context.
D — shorthand for bpy.data.
bpy — the top-level Blender Python API module.

First Look at the Console Environment — to list the global functions and variables, type dir() and press Return.

Auto Completion — the Console can preview a module's or variable's available members; type bpy. and press Tab, for example. Submodules list in green, and attributes and methods list the same way, methods marked by a trailing (.

Examples:
bpy.context — this module reaches the current scene, the selected objects, the current object mode, and so on. Note: for the commands below to print useful output, have some object(s) selected in the 3D Viewport.
Get the current 3D Viewport mode (Object, Edit, Sculpt, etc.):
```text
bpy.context.mode
```
Get the active object:
```text
bpy.context.object
bpy.context.active_object
```
Change the active object's X coordinate to 1:
```text
bpy.context.object.location.x = 1
```
Move the active object by 0.5 along the X axis:
```text
bpy.context.object.location.x += 0.5
```
Change all three location coordinates in one go:
```text
bpy.context.object.location = (1, 2, 3)
```
Change only the X and Y coordinates:
```text
bpy.context.object.location.xy = (1, 2)
```
Get the selected objects:
```text
bpy.context.selected_objects
```
Get the selected objects excluding the active one:
```text
[obj for obj in bpy.context.selected_objects if obj != bpy.context.object]
```
bpy.data — reaches all the data in the blend-file, whether or not it's active or selected.
bpy.ops — "Operators" are actions usually fired from a button or menu item that can also be called from code; see the bpy.ops API documentation for the full list.

## Compatibility

Blender can open blend-files saved by both older versions (backward compatibility) and newer ones (forward compatibility), though with some limits. Tip: if you hit trouble opening much older (or newer) blend-files, stepping through a few intermediary Blender releases to convert in smaller hops can help. Note: there's fuller documentation on compatibility handling in the developer's docs.

Backward Compatibility — opening older files and converting them for the current Blender is usually straightforward and expected to give very good, usable results. Some major feature changes keep backward compatibility only for a limited time — the animation-system changes during the Blender 2.5x project, for example — but never less than a full major release cycle (so at least two years).

Forward Compatibility:
Loss of Data — forward compatibility is inherently harder, and you should always expect some feature loss when opening a blend-file saved by a newer Blender. The UI shows a warning when you edit a more recent blend-file, and trying to overwrite it with a plain "Save" also pops a confirmation, since that could make the data loss permanent.
Complete Incompatibility — when Blender moves to a new major version (3.x to 4.0, say), there can be changes big enough to make the blend-file wholly incompatible with older versions; an older Blender then fails to open (or append/link from) the newer file, with a message naming the minimum version needed. In those cases the previous cycle's last LTS release stays compatible with the newer file-format version and works as a converter between the two — Blender 3.6 LTS, for instance, can open Blender 4.x files and convert them so that, re-saved from 3.6, they become compatible with every 3.x Blender.

## Export Grease Pencil as PDF

The Portable Document Format (PDF) is used to exchange documents viewable in many apps, like PDF readers and modern browsers; exporting Grease Pencil animations makes a separate PDF page for each selected frame. Warning: the exporter runs only in Object Mode.

Scene Options — Object: which objects to include. Active (only the active Grease Pencil object), Selected (all selected Grease Pencil objects), or Visible (all visible Grease Pencil objects in the scene).

Export Options:
Frame — which frames to include. Active (only the active keyframe), Selected (all selected keyframes as separate PDF pages), or Scene (all frames as separate PDF pages).
Sampling — the precision of stroke sampling; lower values give a more accurate result.
Fill — on, exports the Grease Pencil strokes' fill.
Uniform Width — on, exports strokes at a constant thickness.
Note: the Grease Pencil strokes are always exported from the view of the current workspace's largest 3D Viewport.

## Linux Windowing Environment

### Linux Windowing Environment

On Linux, official Blender releases support both X11 and Wayland.

If Wayland is detected it's preferred; otherwise X11 is used.

Hint

The active Windowing Environment shows under Topbar ‣ Blender ‣ About Blender .

### X11

Historically the most widely used windowing environment on Linux and Unix systems.

There's no near-term plan to deprecate or drop X11 support.

### Wayland

Wayland support is a newer addition, so some configurations may be untested. Please file a bug if you hit trouble.

Blender has been tested against Gnome-Shell (mutter), KDE (plasma) & SWAY (wlroots) based compositors.

### Requirements

Gnome-Shell
Under Gnome-Shell the libdecor library is required. It's packaged on most Linux distributions.

If libdecor isn't found, Blender falls back to X11.

### Troubleshooting

Verbose Wayland output helps pin down problems. Start Blender from the command line with extra arguments:

Blender's Wayland Logging

```text
blender --log "ghost.wl.*" --log-level 2
```

Wayland Built-In Logging

```text
WAYLAND_DEBUG=1 blender
```

Disable Wayland (forcing X11)

```text
WAYLAND_DISPLAY="" blender
```

Disable libdecor (forcing borderless windows under Gnome-Shell)
Remove libdecor , then start Blender with an empty X11 display variable.

```text
DISPLAY="" blender
```

### Environment Variables

`XCURSOR_THEME`
The cursor theme to use (must name a locally installed cursor).

`XCURSOR_SIZE`
The cursor size; defaults to 28, and you may want it larger on Hi-DPI displays.

### Known Limitations

Gnome Shell's Fractional Scaling (before version 44)
Gnome-Shell older than 44 doesn't fully support fractional scaling.

Using fractional scaling on those older versions can cause glitches such as an undersized cursor.

NVIDIA GPU
NVIDIA drivers don't yet fully support what Wayland needs. Graphical glitches and flicker are common, and startup crashes happen at times. It isn't Blender-specific, so NVIDIA users may prefer X11 until driver support improves.

### Feature Comparison

| Feature | X11 | Wayland | Notes |
| Smooth Scroll | ✗ | ✓ | Smooth track-pad scrolling. |
| Multi-Touch Gestures | ✗ | ✓ | Track-pad and tablet support for pinch-zoom, pan, and orbit. |
| Reliable Cursor Warping | ✗ *1 | ✓ | Cursor warping, used e.g. while transforming and orbiting the viewport. |
| Window Positioning | ✓ | ✗ *2 | Needed to drag between windows and to restore window positions on file load. |

Features both systems share — Hi-DPI, 3D-mouse, tablet input, … etc. — are left off this list.

*1 On X11, rapid cursor motion can leave the window bounds while the cursor is grabbed (during a transform, say).

*2 Wayland won't let an app set its window position; that's a deliberate design choice and unlikely to change (see issues for position).

# Selecting, Undo Redo, Window System Introduction, Regions ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Selecting; Undo & Redo; Window System Introduction; Regions; Splash Screen; Workspaces.

## Selecting

### Selecting

Out of the box, LMB is what Blender selects with. Swap it to RMB in the Preferences if you prefer.

Across the various editors, Blender offers several selection tools.

Note

A few editors stray from the shortcuts listed below. Most, for example, add a single item with Shift - LMB, but the Outliner uses Ctrl - LMB. Likewise, a Lasso Select is Ctrl - RMB in most editors, yet node editors use Ctrl - Alt - LMB.

Most selection tools ship in two variants — one in the Toolbar, the other in the Select menu. The names sit almost on top of each other (Select Box in the Toolbar versus Box Select in the menu), but they work a bit differently. People arriving from other applications tend to find the Toolbar variants more familiar.

### Toolbar Selection Tools
Click an item and every Toolbar selection tool acts the same: it selects that item and drops any prior selection. Hold Shift as you click and the item joins the selection (if it wasn't selected) or leaves it (if it was).

Dragging is where the tools part ways.

### Tweak
Reference

Tool :

Toolbar ‣ Tweak

Shortcut :

W

Dragging an item will move it around.

### Select Box
Reference

Tool :

Toolbar ‣ Select Box

Shortcut :

W

Drag out a rectangle and, on release, every item partly or fully inside it gets selected. (Everything else is deselected.)

Drag with Shift held down to fold the items into the existing selection; hold Ctrl instead to take them out.

A Spacebar press mid-drag lets you reposition the rectangle with the mouse.

| Start. | Selecting vertices. | Complete. |

### Select Circle
Reference

Tool :

Toolbar ‣ Select Circle

Shortcut :

W

Drag and whatever the circle sweeps across gets selected. Anything it missed is deselected.

Drag with Shift held down to fold the items into the existing selection; hold Ctrl instead to take them out.

The circle's radius is adjustable in the tool settings (found in the area header, the Tool tab of the Sidebar N, or the Active Tool tab of the Properties editor).

Note

In Object Mode: where Select Box grabs an object the moment the box touches any part of its geometry, Select Circle only picks one up if the circle crosses its origin point. That origin shows as an orange dot on selected objects but stays invisible on unselected ones, unless "Origins (All)" is turned on in the Viewport Overlays.

Other modes — Edit Mode and Pose Mode among them — don't show this behavioural quirk.

| Start. | Selecting vertices. | Complete. |

### Select Lasso
Reference

Tool :

Toolbar ‣ Select Lasso

Shortcut :

W

Drag out a freeform shape and, on release, everything inside it gets selected. (Everything else is deselected.)

Drag with Shift held down to fold the items into the existing selection; hold Ctrl instead to take them out.

A Spacebar press mid-drag lets you reposition the shape with the mouse.

Note

Like Select Circle, Select Lasso only consults origin points in Object Mode.

### Selection Modes
Reference

Tool :

Select Tools

Panel :

Tool Settings ‣ Mode

How it works against an existing selection is set by a mode carried on each Toolbar selection tool. Not every tool offers all of them.

Set
Lays down a fresh selection and throws out the old one. The default.

Extend
Folds the newly picked items into what was already selected.

Subtract
Drops the newly picked items back out of the existing selection.

Invert Ctrl - I
Flips the selection — what was off turns on, and the reverse.

Intersect
Keeps only items that overlap the existing selection.

### Menu Selection Tools
Variants of the tools just covered, these live in the menu instead of the Toolbar and behave a little differently.

### Box Select
Reference

Menu :

Select ‣ Box Select

Shortcut :

B

Fire off the menu item or the shortcut first, then drag a box as usual. Unlike Select Box, what happens by default here is that items inside the box are added to the selection. (Those outside it stay selected.)

Pull the boxed items back out of the selection by holding Shift, or by dragging with MMB instead.

A Spacebar press mid-drag lets you reposition the box with the mouse.

### Circle Select
Reference

Menu :

Select ‣ Circle Select

Shortcut :

C

Fire off the menu item or the shortcut first, then drag a circle around as usual. Unlike Select Circle, the default here is that items inside the circle get added to the selection. (Those outside it stay selected.)

Pull the circled items back out of the selection by holding Shift, or by dragging with MMB instead.

Resize the circle's radius by scrolling the Wheel or pressing the NumpadPlus and NumpadMinus keys.

Once started, Circle Select stays put: release the mouse button and you can begin dragging somewhere else without pressing C again. Meanwhile, though, it locks out the rest of Blender while it's running. Press RMB, Return, or Esc to shut the tool off.

### Lasso Select
Reference

Menu :

Select ‣ Lasso Select

Shortcut :

Ctrl - RMB

Fire off the menu item first, then drag a freeform shape with LMB around whatever you want to select. Set, extend, or reduce the selection — the menu lets you pick which.

Alternatively, you can immediately start dragging with Ctrl - RMB. Where this departs from Select Lasso is that, by default, items inside the lasso get added to the selection. (Those outside it stay selected.)

Pull the lassoed items back out of the selection by dragging with Shift - Ctrl - RMB instead.

A Spacebar press mid-drag lets you reposition the lasso with the mouse.

## Undo & Redo

### Undo & Redo

The tools below let you back out of a mistaken action, redo your most recent one, or jump to a particular moment by choosing from the list of recent actions Blender keeps.

### Undo
Reference

Mode :

All Modes

Menu :

Edit ‣ Undo

Shortcut :

Ctrl - Z

Undo your last action with a simple Ctrl - Z.

See also

Memory & Limits Preferences to change undo settings.

### Redo
Reference

Mode :

All Modes

Menu :

Edit ‣ Redo

Shortcut :

Shift - Ctrl - Z

Reverse an Undo with Shift - Ctrl - Z.

### Adjust Last Operation
Reference

Mode :

All Modes

Menu :

Edit ‣ Adjust Last Operation…

Shortcut :

F9

After an operator runs, you can fine-tune its parameters. Where supported, a "head-up display" panel for the last operation sits in the bottom left of the editor. F9 raises the same thing as a pop-up if you'd rather.

Say your last action was a rotation in Object Mode: Blender surfaces the last angle value you changed (see Fig. Rotation (Object Mode, 60 degrees). left), and typing Numpad0 into the Angle Field reverses it entirely. Other useful options appear depending on the operator, so you're not limited to undoing — you can fully reshape an action through the available options.

Over in Edit Mode, Blender adapts the panel's contents to your last action too. In the second example (on the right), the last operation in Object Mode was a Move, but in Edit Mode it was a Scale on a Face — and, as you can see, the contents of Adjust Last Operation differ because of the mode (Edit Mode) (See Fig. Scale (Edit Mode, Resize face). right).

| Rotation (Object Mode, 60 degrees). | Scale (Edit Mode, Resize face). |

Tip

Particularly useful results come out of Adjust Last Operation for some operations. Add a Circle in the 3D Viewport, for example; drop the Vertices to three and you land a perfect equilateral triangle.

Tip

Tucking the Adjust Last Operation region out of sight is done through View ‣ Adjust Last Operation .

### Undo History
Reference

Mode :

All Modes

Menu :

Edit ‣ Undo History

The Undo History menu.

Blender also keeps an Undo History of the most recent actions taken.

Most recent actions sit at the top of the list. A small dot icon beside an entry flags the current status. Roll back through the Undo History and you land on whichever action you choose. Just as Undo walks you backward in time and Redo forward, you can hop freely around the Undo timeline as long as no new change is made. Make one new change and the Undo History is cut off at that point. Pick an entry from the list and the current status jumps to that position.

### Repeat Last
Reference

Mode :

All Modes

Panel :

Edit ‣ Repeat Last

Shortcut :

Shift - R

Press Shift - R and the Repeat Last feature re-runs your last action.

In the example images below, a Monkey mesh was duplicated and nudged a bit. A repeat with Shift - R duplicated and moved the Monkey a second time.

| Suzanne. | After a Shift - D and move. | After a Shift - R . |

### Repeat History
Reference

Mode :

All Modes

Menu :

Edit ‣ Repeat History…

The Repeat History menu.

A list of your last repeated actions is what the Repeat History feature hands you, and from it you pick the ones to run again. It mirrors the Undo History described above, except the list holds only repeated actions.

Important

Quitting Blender wipes the full list of user actions, even if you saved your file beforehand.

See also

Troubleshooting section on Recovering your lost work.

## Window System Introduction

### Window System Introduction

Once Blender starts and the Splash Screen is dismissed, the window should resemble the image below.

The default startup Blender window.

Blender's interface breaks into three main parts:

- At the very top sits the Topbar, home to the main menu — the place for saving, file import and export, settings, rendering, and more.

- The middle is given over to Areas, your principal workspace.

- Along the bottom runs the Status Bar, which surfaces shortcut hints and the statistics that matter.

Blender's default Screen Layout. Topbar (blue), Areas (green) and Status Bar (red).

### Customization
Keyboard shortcuts

To speed work along, Blender leans hard on keyboard shortcuts. The Keymap Editor is where you tailor them.

Theme colors

Nearly all of Blender's interface colors can be recolored to suit you. Should the colors on your screen not line up with the Manual's, your default theme has probably been changed. Open the Preferences, click the Themes tab, and you can craft a new theme or select and tweak an existing one.

Accessibility

Several visibility options come with Blender, among them resolution scale and the loading of custom fonts. The Interface Preferences is where these get configured.

## Regions

### Regions

Regions are what every Editor in Blender splits into. Inside a region you can find finer structuring pieces like tabs and panels, holding buttons, controls and widgets.

The regions of the 3D Viewport showing the Sidebar and the Adjust Last Operation panel after adding a Cube.

Header (green), Main region (yellow), Toolbar (blue), Sidebar (red) and Adjust Last Operation panel (pink).

### Main Region
One region is always on screen at minimum. The Main region is its name, and it's the editor's most prominent piece.

Since each editor has its own job, both the main region and the set of extra regions differ from one editor to the next. For per-editor detail, turn to the Editors chapter.

### Header
Running along an area's top or bottom, a header is a slim horizontal strip. Each editor has one, where it holds menus and the tools used most often. Which menus and buttons appear depends on the editor type along with the active object and mode.

The Header of the 3D Viewport.

### Context Menu
RMB on a header brings up a context menu with a few options:

Show Header
Switches the header on or off. Once hidden, a header returns when you click or drag the little arrow that shows up at the editor's top/bottom right.

Show Tool Settings
Switches the Tool Settings on or off.

Show Menus
Switches the Menus between collapsed and not.

Flip to Bottom/Top
Switches whether the header or Tool Settings ride along the editor's top or its bottom.

Vertical/Horizontal Split
Brings up a guide line for choosing the area and the spot to split at. Tab flips between vertical and horizontal.

Maximize Area / Focus Mode
See Maximize Area.

Duplicate Area into New Window
See Duplicate Area into New Window.

Close Area
Shuts the area, letting a neighboring area grow out to fill the gap.

### Toolbar
Down the left side of the editor area, the Toolbar gathers a group of interactive tools. Its visibility is toggled with T.

### Tool Settings
Resembling the header, a horizontal strip at the editor's top or bottom carries settings for the currently selected tool. Like the header, its context menu lets you hide and move it.

### Adjust Last Operation
Tweaking an operator after it runs is what the Adjust Last Operation region is for. Just added a cube, for example? Use this region to adjust its size.

### Sidebar
Down the right side of the editor area, the Sidebar gathers Panels with settings for the editor's objects and for the editor itself. Its visibility is toggled with N.

### Footer
Some editors carry a bar (top or bottom of the editor area) reporting on things like the active tool or operator.

Within animation editors, playback, keying, auto keyframing, and transport controls and options all live in the footer.

What these settings let you do:

- Steer how previews play and stay in sync with audio.

- Lay down and handle keyframes via keying sets and auto keying.

- Move along the timeline through playback and transport controls.

- Set frame ranges and preview chosen stretches of the animation.

See also

The Playback Controls documentation covers, in full detail, the footer's usual properties and controls.

### Arranging

### Scrolling
Drag a region with the MMB to scroll it vertically and/or horizontally. Where a region has no zoom level, the Wheel scrolls it too while the cursor hovers over it.

Certain regions — animation timelines above all — carry scrollbars fitted with control points that adjust the region's vertical or horizontal range. These special scrollbars sport extra widgets at their ends, shown in the following image:

Scrollbars with zoom widgets.

These let you stretch or squeeze the range to reveal more or less detail within the screen space on hand. Just drag one of the dots to widen or narrow the shown range. Dragging in the editor with Ctrl - MMB also adjusts both ranges at once, quickly.

### Changing the Size and Hiding Regions
Resizing a region means dragging its border, exactly as with Areas.

Shrink a region down to nothing to hide it. A hidden region leaves behind a small arrow. LMB that icon to bring the region back.

### Scaling
A handful of regions (the Toolbar included) take scaling: drag inside them with Ctrl - MMB, or use NumpadPlus and NumpadMinus while hovering over them. Home returns the scale to default.

### Asset Shelf
The Asset Shelf of the 3D View, showing material assets.

### Search
To hunt for assets, hover over the Asset Shelf, press Ctrl-F, and type a query. The poses filter down to match what you entered.

### Tabs
The usage of catalogs as tabs.

Catalogs can appear as individual tabs. A tab shows only its own content plus the content of its children, which makes narrowing to a particular set of assets easy.

### Display Options
Display options available for the asset shelf.

The size property lets you resize the items on the shelf.

Tick the "Names" checkbox and asset names show on the shelf. Failing that, hovering over an item also reveals its name.

By default the shelf is one item row tall. Drag its upper edge to grow it and make room for more rows.

### Filter
By Active Tool
Limits the asset shelf to brushes that suit whichever tool is currently active.

Note

Where this property's value is kept is the Preferences, so you may need to save it by hand if Auto-Save Preferences is off.

## Splash Screen

### Splash Screen

As Blender launches, the splash screen lands in the middle of the window. From it you can spin up new projects or reopen recent ones. There's a fuller rundown below.

Blender Splash Screen.

Dismiss the splash screen and begin a fresh project by clicking anywhere outside it (but still inside the Blender window) or by pressing Esc. The splash screen vanishes to reveal the default screen. To bring it back, click the Blender icon in the Topbar and choose Splash Screen.

Note

On a first launch of Blender, or after updating to a new version, the "interactive region" carries a Quick Set Up Process.

### Splash Image
Up top, the splash screen shows the splash image, with the Blender version tucked into the top right.

### Interactive Region
The bottom half of the splash screen is the interactive region.

New File
Begin a fresh project from a template.

Recent Files
The blend-files you opened most recently, putting your latest projects within easy reach.

Open
Lets you open an existing blend-file.

Recover Last Session
Blender attempts to bring back the previous session from temporary files. See Recovering Data.

What's New
Brings up the latest release notes.

Donate to Blender
Heads to Blender's Development Fund website.

## Workspaces

Workspaces are predefined window layouts.
Each consists of Areas
containing Editors, organized around a specific task like
modeling, animating, or scripting. Projects typically require switching between multiple Workspaces.

Access Workspaces via the Topbar. 

Controls:

Tabs
Click to switch workspaces.
Double-click a tab to rename it.

Add Workspace
Insert a new workspace from a template (e.g. Modeling , Sculpting , Compositing ).

Context Menu RMB

Duplicate
Create a copy of the workspace, including screen layout and editors.

Delete
Remove the workspace.
Cannot delete if it's the only one.

Reorder to Front/Back
Position the workspace tab at the beginning (front) or end (back) of the tab list.

Previous Workspace Ctrl - PageUp
Switch to the workspace immediately to the left.

Next Workspace Ctrl - PageDown
Switch to the workspace immediately to the right.

Delete Other Workspaces
Remove all workspaces except the one right-clicked.

Default Workspaces:

Blender's default startup displays the "Layout" workspace.
This workspace previews your scene
and contains:

- 3D Viewport on top left.

- Outliner on top right.

- Properties on bottom right.

- Timeline on bottom left.

Blender's 'Layout' Workspace with four editors. 

3D Viewport (yellow), Outliner (green), Properties (blue) and Timeline (red).

Blender ships with additional workspaces:

Modeling :

Geometry modification using modeling tools.

Sculpting :

Mesh modification using sculpting tools.

UV Editing :

Texture coordinate mapping onto 3D surfaces.

Texture Paint :

Image texture coloring in the 3D Viewport.

Shading :

Material definition for rendering.

Animation :

Time-dependent property changes.

Rendering :

Result viewing and analysis.

Compositing :

Image combination and post-processing.

Geometry Nodes :

Procedural modeling with Geometry Nodes.

Scripting :

Python API interaction and script writing.

Additional Workspaces:

Blender includes extra Workspaces when adding a new one:

2D Animation

2D Animation :

Base workspace for Grease Pencil work.

2D Full Canvas :

Extended "2D Animation" with a larger canvas.

VFX

Masking :

2D mask creation for compositing or video editing.

Motion Tracking :

Camera motion calculation and video stabilization.

Video Editing

Video Editing :

Media sequencing for video.

Save and Override:

Workspaces are stored inside blend-files.
Loading a file with Load UI enabled uses the file's layout instead of the current one.

Workspaces can be saved as part of Defaults.

Workspace Settings:

Reference

Editor :

Properties Editor

Panel :

Tool tab ‣ Workspace

Pin Scene
When enabled, the current workspace remembers which scene was active.
Activating the workspace switches to that scene.

Mode
Activate this Mode when switching to the workspace.

Sequencer Scene
The scene edited by the video sequence editor.
See Sequencer Scene.

Sync Scene Time
Align the active scene and time based on the current scene strip in the video sequence
editor.
See Sequencer Scene.

Filter Add-ons
Controls which add-ons show in the active workspace.
Unchecked uses global add-ons.
Checked lets you toggle individual add-ons below.

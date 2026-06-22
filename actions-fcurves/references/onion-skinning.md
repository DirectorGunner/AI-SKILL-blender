# Onion Skinning, Buttons, Decorators, Input Fields ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Onion Skinning; Buttons; Decorators; Input Fields; Operators; Tool System; Areas; Segments; Path Animation.

## Onion Skinning

Onion Skinning shows ghost frames before/after the current frame for animation sequencing decisions. Main toggle in Viewport Overlays; Grease Pencil per-layer toggling via layer list.

Onion Skinning panel shown. Options: Mode—Keyframes shows range-determined keyframes. Frames shows range-determined frames. Selected shows manually-selected Dope Sheet keyframes. Opacity: Ghost frame transparency. Filter by Type: Frame-type filtering. Keyframes Before/After: Range quantity (frames/keyframes per Mode).

Custom Colors: Before/After colors for ghost frames.

Display: Fade: Ghost opacity decreases distantly. Show Start Frame: Loop-animation helper showing first ghost at last frame. Example with Onion Skinning shown.

## Buttons

Operator Buttons: Execute an Operator (action) when LMB clicked. Text, icon, or text-with-icon format.

Checkboxes & Toggle Buttons: Activate/deactivate options. LMB changes state; ticks show activation. Toggling shown via color or icon change. Ctrl + Wheel cycles on/off. Dragging: LMB drag over multiple changes all at once.

Direction Buttons: LMB drag in sphere rotates direction. Ctrl (dragging) snaps to vertical/diagonal.

## Decorators

Decorators are small right-side buttons showing property state and animation capability. Clicking the dot adds a Keyframe; clicking again removes. Solid rhombus shows current-frame keyframe; non-solid shows other-frame keyframe. Clicking non-solid adds current-frame keyframe. Driver-controlled properties show driver icon. Decorators enable quick property-state glances.

See also: State Colors

## Input Fields

Text & Search Fields: a text field has a rounded rectangular border and may show an icon and/or text inside it. Text fields hold text strings and let you edit with the usual text-editing shortcuts:
- Home — go to the start of the line.
- End — go to the end of the line.
- Left, Right — move the cursor one character.
- Ctrl-Left, Ctrl-Right — move the cursor a whole word.
- Backspace, Delete — delete characters.
- Ctrl-Backspace, Ctrl-Delete — delete words.
- Shift — hold while moving the cursor to select.
- Ctrl-A — select all text.
- Ctrl-C — copy the selected text.
- Ctrl-X — cut the selected text.
- Ctrl-V — paste text at the cursor position.
For text fields with an icon and pop-ups, see Data ID.

Number Fields: these store values and units. The first kind shows left (<) and right (>) triangles on its sides when the pointer is over it. Sliders, a second kind, carry a colored background bar showing a value across a range, such as a percentage. You can edit the value several ways:
Incremental Steps — click LMB on the small triangles to step by units (not available for sliders); you can also use Ctrl-Wheel while hovering over the field to change the value.
Dragging — hold LMB and drag left or right to change the value with the mouse; hold Ctrl to snap to discrete steps while dragging, or Shift for precision input.
Keyboard Input — press LMB or Return to type the value. While typing, number fields behave like text fields:
- press Return, or LMB outside the field, to apply the change;
- press Esc or RMB to cancel;
- press Tab to jump to the next field, or Shift-Tab to go to the previous one;
- press Minus while hovering over a number field to negate the value.

Multi-Value Editing: edit several number fields at once by pressing LMB on the first field and dragging vertically across the fields you want, then either drag left or right to set the value with the mouse, or release LMB and type one in.

Value Limits: most numeric values are bounded by a "soft limit" and a "hard limit" range. Dragging with the mouse stays within the soft limit; keyboard entry can go wider, but never past the hard limit.

Expressions: you can type mathematical expressions into any number field — for example 3*2 or 10/5+4 instead of 6 — and even constants like pi (3.142) or functions like sqrt(2) (the square root of 2). These are evaluated by Python; for all available math expressions, see the Math module reference.
Expressions as Drivers: to have an expression re-evaluated after entry, Blender uses Drivers (a feature of the animation system). Expressions beginning with # are special: rather than evaluating the value and discarding the expression, they add a driver to the property carrying that expression. The expression #frame quickly maps a value to the current frame, and more complex ones like #fmod(frame, 24) / 24 also work — a convenient shortcut for adding drivers, which can also be added via the RMB menu.

Units: besides expressions, you can give numbers with units; with no unit, a default unit applies, and the unit system can be changed in the scene settings. Use either the unit abbreviation or the full name after the value. Valid length examples include: 1cm 1m 3mm 1m, 3mm and 2ft 3ft/0.5km 2.2mm + 5' / 3" - 2yards. Note: the decimal separator is optional; you can mix units (e.g. metric and imperial, even though only one shows at a time); and plurals are recognized, so both meter and meters work.

Color Fields: a color field stores a color value, and clicking it with LMB opens the Color Picker. Fields with an alpha channel are split in half — the left shows the color without an alpha channel, the right shows it with alpha over a checker pattern. Drag and drop to copy a color to another color field. Hovering over a color property shows a large swatch preview along with the color's hexadecimal, RGBA, and HSVA values.

## Operators

### Operators

The instant you trigger one, an operator carries out its action — which is what sets them apart from tools, where some kind of input is needed first. You can fire operators off from Operator Buttons, Popup Menus, or Menu Search. Adding a fresh object, deleting it, or switching its shading to smooth all count as operators.

### Operator Properties
Properties for refining the result come with most operators. The pattern is to run the operator first (it falls back on default settings), then tune the properties over in the Adjust Last Operation region.

### Modal Operators
Sitting conceptually between Tools and ordinary operators are modal operators. Interactive input of some kind is required for them.

| Esc , RMB | Cancels a modal operator. |
| Return , LMB | Confirms the action of a modal operator. |

### Slider Operators
A percentage value gets adjusted interactively in the editor's Header through slider operators.

Drag the slider left or right to set the percentage. Hold Ctrl to make it coarser (snapping in 10% increments) and Shift to make it finer. On some sliders, E toggles "overshoot," letting you push past the 0-100% range.

### Searching for Operators

### Menu Search
Reference

Mode :

All Modes

Menu :

Edit ‣ Menu Search

Shortcut :

F3

Searching Blender's interface for a given operator and running it is what the Menu Search pop-up does. Type part of the operator's name to narrow the list, then either click it with LMB or walk to it with Down and Up and fire it with Return.

Beyond the operator names, the pop-up also surfaces the menus that house them.

The Menu Search pop-up.

See also

The Spacebar Action option in the Preferences.

### Operator Search
Reference

Mode :

All Modes

Menu :

Edit ‣ Operator Search

Turn on Developer Extras and the Operator Search becomes reachable from the Edit menu in the Topbar. Every operator inside Blender falls under this search, even ones absent from any menu. Python developers find it handy for testing. Blender may also bundle a few advanced operators exposed nowhere but here.

See also

An option in the User Preferences governs how search results get scored.

## Tool System

### Tool System

The Toolbar is where you get at tools.

What follows is a broad introduction to tools; each individual tool keeps its own documentation.

Only one tool can be active per Workspace and mode, and it's remembered: pick Extrude in Edit Mode, hop over to Object Mode (where no Extrude tool exists) and back again, and Extrude is still waiting.

LMB drives most tools, though a few also carry modifier keys (shown in the Status Bar while the tool is in use). All of this is customizable in the Keymap Preferences.

A handful of tools (Shear and Spin, for instance) define gizmos to help steer them.

### Toolbar
Reference

Shortcut :

T

Expanded tool group.

Buttons for the assorted tools fill the Toolbar. A small triangle in a button's bottom right corner marks a tool group, which opens if you hold LMB on it briefly (or drag LMB to pop it open at once).

Hover briefly over a tool and its name appears; linger and the full tooltip shows.

Widen the Toolbar and the icons spread into two columns. Stretch it further and each icon gains its text.

### Pop-Up Toolbar
Reference

Shortcut :

Shift - Spacebar

Hit Shift - Spacebar and a compact toolbar pops up right under your cursor for quicker reach. Selection shortcuts for the tools sit on the right.

You can instead bind this to Spacebar in the Keymap Preferences. Then Spacebar works like a modifier key (much as holding Ctrl or Shift does). For instance, Spacebar T gives Transform, Spacebar D gives Annotate, Spacebar M gives Measure, and so on. See Spacebar Action.

### Quick Favorites
Reference

Shortcut :

Q

Your go-to tools collect in the Quick Favorites menu. Through its context menu, any tool or menu item can be added to this pop-up.

### Changing Tools
With Alt Click Tool Prompt switched on in the Keymap Preferences, a tap of Alt brings up a tool prompt in the Status Bar. Press a key to pick the matching tool, or tap Alt once more to back out.

### Fallback Tool
Selected by default — sitting at the top of the Toolbar — is the fallback tool. Change it by holding LMB on the toolbar button or pressing Alt - W for a pie menu.

### Cycling Tools
Bind a key to a tool that belongs to a group, then switch on the Cycle option in the keymap editor. Each further press then steps through the tools in that group.

The selection tools in the 3D Viewport ship with this on by default, for instance: press W and it cycles between Select Box, Select Circle and so on.

### Properties
Settings of their own can belong to tools, reachable from several spots:

- The Tool ‣ Active Tool panel in the Sidebar N .

- The Active Tool tab in the Properties editor.

- The Tool Settings region below the area header.

## Areas

### Areas

Area boundaries are indicated by rounded corners (yellow highlights).

A set of rectangles called Areas is what the Blender window breaks down into. Screen space for Editors — the 3D Viewport or the Outliner, say — is what Areas set aside, each editor delivering one specific piece of functionality.

Geared toward particular tasks (modeling, animating and so on), Workspaces are how Areas get grouped.

Note

A handful of Blender's keyboard shortcuts are global (Ctrl - S for saving, say), but plenty hinge on which editor the cursor happens to be over.

Suppose you've just picked two objects in the Outliner and want to join them. Press the shortcut for it (Ctrl - J) with the cursor still parked in the Outliner and nothing happens, since the shortcut doesn't apply there; move the cursor to the 3D Viewport first.

Tip

- Border Width in the user preferences sets how thick the border around areas is.

- For easier area handling on touch devices, handles can be set to stay visible at all times. See Show – Corner Handles:.

### Resizing
Drag an area's borders with LMB to resize it. Bring the cursor onto the border between two areas until it turns into a double-headed arrow, then click and drag. Hold Ctrl to snap area sizes to convenient values.

### Docking
Several interactive ways to manipulate the size and position of areas — plus splitting one area into new ones — fall under docking.

Kick off the interactive process by parking the cursor in an area corner, where it becomes a cross (+). With the cross showing, press and hold LMB to carry out any of these:

Hit Esc or RMB before you let go of the mouse and the whole operation is called off.

### Joining
Properties is being joined to the Outliner.

Drag from one area's corner into the body of a second area to join the two. The areas slated to merge brighten up.

### Splitting
A new area is born from splitting an existing one. Drag from an area corner left/right to split vertically; drag up/down to split horizontally.

Carry a split operation across into a different area and you split and join in one motion.

Drag one area onto the center of another and the second is swapped out for the first.

### Area Options
A RMB on the border raises the Area Options.

Vertical/Horizontal Split
Brings up a guide line for choosing the area and the spot to split at. Tab flips between vertical and horizontal.

Join Up/Down/Left/Right
Brings up the join-direction overlay.

Swap Areas
Trades this area with the one next to it.

### Swapping Contents
Swap two areas' contents by pressing Ctrl - LMB on a corner of the first area, dragging toward the target, and letting go there. The two need not sit side by side, though both must live in the same window.

### Maximize Area
Reference

Menu :

View ‣ Area ‣ Toggle Maximize Area

Shortcut :

Ctrl - Spacebar

Blows the editor area up to fill the whole window while the Topbar and Status Bar stay put. Handy when you want to bear down on a single editor (3D Viewport, Shader Editor, etc.) without disturbing your workspace layout.

Maximizing inside the 3D Viewport tucks these away for the moment:

- Navigation Gizmos

- Text Info overlay

- Statistics overlay

Press the shortcut once more, or hit the Back to Previous button in the Topbar, to drop back to normal size.

### Restore Area
Reference

Menu :

View ‣ Area ‣ Restore Area

Shortcut :

Ctrl - Spacebar

Shrinks the maximized area back to its earlier size and brings back the previous screen layout.

### Focus Mode
Reference

Menu :

View ‣ Area ‣ Focus Mode

Shortcut :

Ctrl - Alt - Spacebar

Stretches the editor area across the entire window, tucking away:

- The Topbar

- The Status Bar

- Secondary regions (such as toolbars, sidebars, headers, etc.) of the editor itself.

What you get is the largest screen area the active editor can have.

Press the shortcut again, or click the icon at the editor's top-right corner (shown only while you hover over the area), to go back to normal size.

### Duplicate Area into New Window
Reference

Menu :

View ‣ Area ‣ Duplicate Area into New Window

Spins up a fresh floating window holding a copy of the current editor area. Fully functional, the new window belongs to the same Blender instance.

It comes in particularly handy across a multi-monitor setup.

Tip

A new window can also be made by holding Shift - LMB on an area corner and dragging slightly outward.

## Segments

This section covers segment operations.

Subdivide:

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Subdivide

Add new control points to chosen segments by splitting them into smaller pieces.
Useful for smoother transitions, finer adjustments,
or additional detail in animation and modeling.

Number of Cuts
Specify divisions per segment; each cut creates one new control point per segment.

Switch Direction:

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Switch Direction

Reverse a chosen curve's direction.
The start becomes the end, and vice versa.
Visual appearance stays unchanged,
but behavior changes for paths, bevels, and tapers.

This section covers segment operations.

Subdivide:

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Subdivide

Add new points to chosen segments by breaking them into smaller parts.
Useful for smoother transitions, detail preparation,
or adding more complexity in animation and modeling.

Number of Cuts
Specify divisions per segment; each cut creates one new point per segment.

Switch Direction:

Reference

Mode :

Edit Mode

Menu :

Segments ‣ Switch Direction

Reverse the direction of a chosen curve.
The start becomes the end, and vice versa.
Visual look stays the same,
but behavior shifts for paths, bevels, and scaling.

## Path Animation

Path Animation settings govern how child objects move along a path.

Note

This feature is deprecated but still available.
A more sustainable method is the Follow Path Constraint.

Path Animation panel. 

Frames
Count of frames needed to complete the path,
setting the maximum Evaluation Time value.

Evaluation Time
Parametric position on the curve length (divided by Frames to get the actual position).
Defaults to the global frame number,
but can be keyframed for custom control.

Clamp
Prevent curve path children from travelling past the start/end points.

Follow
Rotate curve path children to align with the path's curvature.

Example:

This example shows Path Animation setup .

- Build something to animate plus a path for it to travel along.
Here the Monkey and the Bézier Circle stand in for those.

- Bind the monkey onto the Bézier circle: click the monkey first and the curve second
(which leaves the curve active), then press Ctrl - P and choose Follow Path .
That keyframes Evaluation Time on its own and switches Follow on within
the Path Animation panel.

- Pick the monkey and
Clear Origin to remove its offset.

- Adjust the monkey's orientation by changing
the Tracking Axis.

| Monkey parented to the Bézier Circle.  | The final result.  |

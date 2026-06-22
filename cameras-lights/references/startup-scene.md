# Startup Scene, Grease Pencil, Editing Channels, F Curve Modifiers ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Startup Scene; Grease Pencil; Editing Channels; F-Curve Modifiers; Themes; Import/Export SVG as Grease Pencil; Defaults.

## Startup Scene

After you dismiss the splash screen, the 3D Viewport shows the startup scene (assuming no other blend-file was opened). This startup scene is yours to customize.

Elements:
Cube — the gray cube at the scene's center is a mesh object. Its orange outline means it's selected, and the orange dot at its middle is its Origin, marking its exact position.
Light — the cluster of concentric black circles is a light source lighting the cube.
Camera — the pyramid topped by a large triangle is the camera, which supplies the viewpoint used for rendering.
3D Cursor — the 3D cursor, drawn as a cross with a red-and-white ring, sets where freshly added objects appear and can double as a transformation pivot point.
Grid Floor — the gray lines that make up the floor mark out the world's zero elevation, while the red and green lines trace the axes of the world coordinate system; the two sets cross at the world origin, which is also where the Cube's origin sits. Grid Floor options live in the Viewport Overlays popover.

Text Info — the viewport's top-left corner displays assorted readouts; see Viewport Overlays for specifics.

## Grease Pencil

This mode lets you fine-tune the timing of a Grease Pencil object's animation frames and is especially handy for blocking out shots.

Channels Region — the Grease Pencil object shows up in light blue here, its layers in gray. Each layer offers:
Opacity — the layer's opacity.
Use Mask — turns the layer's masks on or off.
Onion Skinning — turns onion skinning on or off.
Visibility (eye icon) — toggles the layer's visibility in viewport and render.
Show all keyframes (checkbox) — when off, the layer freezes as it is, so jumping to a different keyframe no longer changes its look.
Lock (padlock) — a locked layer can't be edited.

Header:
Add New Layer — adds a layer.
Remove Layer — removes the active layer.
Move Layer — moves the active layer down or up.
Isolate Layers (screen icon) — toggles whether the active layer is the only editable and visible one.
Isolate Layers (padlock icon) — toggles whether the active layer is the only editable one.

Insert Keyframe — press I while hovering the Dope Sheet Editor to insert a keyframe; it copies the active frame when Additive Drawing is on, and makes a blank frame otherwise.

Copying Frames — you can copy frames between layers, or between objects, with the Copy and Paste tools in the Key menu; keyframes paste into the selected layers, so make sure a destination layer is selected.

Main Region — keyframes behave like any other Dope Sheet data. Interpolated keyframes (a.k.a. breakdowns) appear as smaller light-blue dots.

Sidebar — holds a copy of the Grease Pencil Layer Properties.

### Grease Pencil

Reference

Panel :

Render ‣ Grease Pencil

This section governs Grease Pencil line rendering behavior.

### Viewport

SMAA Threshold
Edge detection threshold for 3D Viewport anti-aliasing correction. Higher values may remove detail through excessive softening.

### Render

SMAA Threshold
Edge detection threshold for final render anti-aliasing correction. Higher values may sacrifice detail to over-blur.

SSAA Samples
Super-sampling count in final renders. Higher counts smooth lines but extend render duration.

Motion Blur Steps
Adjusts motion blur precision; more steps increase accuracy but render time. Only applies when Motion Blur is active. Set to 0 to omit motion blur for Grease Pencil objects.

Grease Pencil — Line Rendering Settings

Reference
Panel: Render ‣ Grease Pencil

This panel configures Grease Pencil line rendering.

### Viewport

SMAA Threshold
Edge detection sensitivity for 3D Viewport alias correction. Higher values risk excessive blur and detail loss.

### Render

SMAA Threshold
Edge detection sensitivity for final render alias correction. Higher values risk excessive blur and detail loss.

SSAA Samples
Sample count for super-sampling anti-aliasing. Higher counts produce smoother lines but extend render time.

Motion Blur Steps
Accuracy control for motion blur; more steps mean longer render time.
Enabled only if Motion Blur is active.
Set to 0 to disable motion blur for Grease Pencil objects.

### Grease Pencil

Reference

Panel :

Render ‣ Grease Pencil

This panel contains options that govern how Grease Pencil strokes are rendered.

### Viewport

SMAA Threshold
The threshold for edge detection antialiasing in the 3D Viewport. Higher values may cause excessive blurring and detail loss.

### Render

SMAA Threshold
The threshold for edge detection antialiasing in final rendering. Higher values may cause excessive blurring and detail loss.

SSAA Samples
Sample count for super-sampling antialiasing in final rendering. Increased samples produce smoother strokes but extend render time.

Motion Blur Steps
Determines precision of motion blur; higher steps increase render time. Applies only when Motion Blur is enabled. Set to 0 to disable motion blur for Grease Pencil objects.

## Editing Channels

Delete Channels — Reference: Menu: Channel ‣ Delete Channels; Shortcut: Delete, X. Strips the selected channels out of the current action. Warning: keep the pointer over the channel region before using the shortcuts; over the main region instead, you'll only delete the selected keyframes, not whole channels.

Un/Group Channels — Reference: Menu: Channel ‣ Un/Group Channels; Shortcut: Ctrl-Alt-G, Ctrl-G. Bundles the selected channels into a collection (renamable by double-clicking its name) or ungroups them; grouping keeps the view tidier.

Toggle/Enable/Disable Channel Settings — Reference: Menu: Channel ‣ Toggle/Enable/Disable Channel Settings; Shortcut: Shift-W, Shift-Ctrl-W, Alt-W. Flips, switches on, or switches off a given setting for the selected channels:
Protect — a protected channel (closed-padlock icon) can't be edited; rather than Shift-W then Toggle, you can just press Tab.
Mute — a muted channel (empty checkbox) has no effect on the animation.

Toggle Channel Editability — Reference: Menu: Channel ‣ Toggle Channel Editability; Shortcut: Tab. Locks or unlocks a channel for editing.

Extrapolation Mode — Reference: Menu: Channel ‣ Extrapolation Mode; Shortcut: Shift-E. Sets how the curve behaves before its first keyframe and after its last.
Constant — carries on as a flat line at the first/last keyframe's value; this is the default.
Linear — carries on as a straight line at the same slope as the first/last keyframe.
Make Cyclic — repeats the whole curve, done by adding a Cycles modifier.
Clear Cyclic — removes that modifier, so the curve stops repeating.

Add F-Curve Modifier — Reference: Menu: Channel ‣ Add F-Curve Modifier; Shortcut: Shift-Ctrl-M. Opens a submenu for adding a modifier to the active curve; the modifiers' settings live in Sidebar ‣ Modifiers.

Show/Hide:
Hide Selected Curves (H) — hides the selected curves.
Hide Unselected (Shift-H) — hides every curve but the selected ones.
Reveal Curves (Alt-H) — brings back all previously hidden curves.

Expand/Collapse Channels — Reference: Menu: Channel ‣ Expand/Collapse Channels; Shortcut: NumpadPlus, NumpadMinus. Expands or collapses the selected headers.

Move — Reference: Menu: Channel ‣ Move…. Shuffles the selected channels or slots up and down the list: To the top (Shift-PageUp), Up one line (PageUp), Down one line (PageDown), To the bottom (Shift-PageDown).

Revive Disabled F-Curves — Reference: Menu: Channel ‣ Revive Disabled F-Curves. Clears the "disabled" tag from every F-Curve to get broken ones working again (a curve breaks when it points at a property that doesn't exist).

Keys to Samples — Reference: Menu: Channel ‣ Keys to Samples; Shortcut: Alt-C. Switches the selected curves from interpolating between keyframes to holding a sampled value at each whole frame. It's destructive — you lose the ability to edit the curve — and is used mainly to shrink file size on large datasets, since samples take less room than keyframes. On the subframes that fall between samples, interpolation runs linearly.

Samples to Keys — Reference: Menu: Channel ‣ Samples to Keys. Switches the selected curves from samples back to keyframes, making them editable; note this drops a keyframe on every frame.

Sound to Samples — Reference: Menu: Channel ‣ Sound to Samples. Builds a sampled curve out of a sound file (reach for Samples to Keys when it needs editing).
Lowest Frequency — the cutoff of a high-pass filter applied to the audio.
Highest Frequency — the cutoff of a low-pass filter applied to the audio.
Attack Time — a hull-curve value setting how fast the hull curve may rise; lower means steeper.
Release Time — a hull-curve value setting how fast the hull curve may fall; lower means steeper.
Threshold — the minimum amplitude needed to influence the hull curve.
Accumulate — sums just the upward jumps in the hull-curve amplitudes into the output.
Additive — the hull-curve amplitudes are summed; with Accumulate on, both positive and negative differences accumulate.
Square — outputs a square curve, negatives always becoming -1 and positives 1.
Square Threshold — anything below this threshold becomes 0.

Bake Channels — Reference: Menu: Channel ‣ Bake Channels. Generates fresh keyframes for the selected curves.
Frame Range — the range to bake; defaults to the scene or preview range.
Frame Step — the gap between keyframes; use it to key every 10 frames, or even every half frame.
Remove Outside Range — deletes existing keys outside the bake range.
Interpolation Type — the interpolation for the new keys.
Bake Modifiers — when on, the new keyframes reflect the modified curve and the modifiers are deleted; when off, they reflect the original curve and the modifiers stay applied.

Discontinuity (Euler) Filter — Reference: Menu: Channel ‣ Discontinuity (Euler) Filter. Cleans up Euler rotation channels plagued by Gimbal Lock; all three Euler axis channels must be selected for it to work.

Frame Selected Channels — Reference: Menu: Channel ‣ Frame Selected Channels; Shortcut: NumpadPeriod. Pans and zooms to show all keyframes of the selected curves; Alt-MMB on a channel does it too.

## F-Curve Modifiers

Reference — Panel: Sidebar region ‣ Modifiers.

F-Curve modifiers work like object modifiers: they add non-destructive effects you can tweak anytime and stack to build more elaborate results. They evaluate top to bottom, and you reorder them by dragging the dots at a modifier's top-right corner. A few must come first and can't be combined — currently the Cycles and Smooth (Gaussian) modifiers.

Interface:
Name — modifiers are named for their function by default, but you can rename them.
Mute — the checkbox in a modifier's header disables it.
Delete — the cross in a modifier's header removes it.
Influence — mixes the original curve with the modified one.
Restrict Frame Range:
  Start/End — the frame on which the modifier's effect begins/ends.
  Blend In/Out — how many frames, measured from the Start/End above, the modifier takes to fade in/out.

Adding a Modifier — manage modifiers on the Sidebar's Modifiers tab: choose an F-Curve — either in the channel region or by clicking one of its keyframes — then open the Add Modifier dropdown and pick one.

Types of Modifiers:
Generator Modifier — creates a polynomial function: basic formulas that draw lines, parabolas, and more elaborate curves depending on the values used. See also the Wikipedia Page for more on polynomials.
  Mode — how the equation is expressed. Expanded Polynomial uses the form \(y = A + Bx^1 + Cx^2 + ... + Dx^n\); Factorized Polynomial uses \(y = (Ax + B)(Cx + D)\).
  Additive — adds the polynomial onto the curve instead of replacing it.
  Order — the highest power of x in the polynomial.
  Constant — the constants A, B, C… in the equation.
Built-in Function Modifier — extra formulas, each with the same shape controls. Consult a mathematics reference for detail on each.
  Type — the built-in function: Sine, Cosine, Tangent, Square Root, Natural Logarithm, or Normalized Sine: \(sin(x)/x\).
  Additive — adds the function onto the curve instead of replacing it.
  Amplitude — adjusts the Y scaling.
  Phase Multiplier — adjusts the X scaling.
  Phase Offset — adjusts the X offset.
  Value Offset — adjusts the Y offset.
Envelope Modifier — lets you reshape the curve: first define an envelope (two horizontal lines roughly matching the curve's lower and upper bounds), then add control points, each of which can push, squeeze, and stretch the envelope — and the curve with it — at a given frame.
  Reference — the value the envelope centers on.
  Min/Max — how far the envelope's starting lower/upper bound sits from the reference value.
  Add Control Point — adds a control point at the current frame.
  Point — Frame (the control point's frame) and Min/Max (how far the envelope's adjusted lower/upper bound at this frame sits from the reference value).
Cycles Modifier — makes the curve repeat. Note: it has to be the first modifier in the list, because it needs to know exactly where the keyframes sit — impossible if other modifiers run first — which is why it's incompatible with the Smooth (Gaussian) Modifier.
  Before/After Mode — No Cycles (don't repeat before/after the original), Repeat Motion (repeats with each copy's values unchanged), Repeat with Offset (repeats, shifting each copy vertically so its first keyframe meets the previous last one), Repeat Mirrored (repeats, flipping every other copy horizontally).
  Count — how many copies to make; 0 means infinite.
  Trivially Cyclic Curves — when the Cycle Mode at both ends is Repeat Motion or Repeat with Offset and no other modifier options are changed from default, the result is a simple infinite cycle. This special case gets extra support elsewhere in Blender: automatic Bézier handle placement accounts for the cycle and adjusts for a smooth transition, and the Cycle-Aware Keying option can be turned on so new keyframes respect the cycle.
Noise Modifier — perturbs the curve with a noise formula, useful for adding subtle or wild randomness to motion, like camera shake.
  Blend Type — Replace (adds noise in [-0.5, 0.5]), Add (adds noise in [0, 1]), Subtract (subtracts noise in [0, 1]), Multiply (multiplies by noise in [0, 1]).
  Scale — the noise's horizontal scale; higher values give less dense oscillation.
  Strength — the noise's vertical scale.
  Offset — offsets the noise in time.
  Phase — adjusts the noise's random seed.
  Depth — adjusts how detailed the noise is.
  Lacunarity — the gap between successive frequencies; Depth must exceed 0 for it to matter.
  Roughness — the amount of high-frequency detail; Depth must exceed 0 for it to matter.
Limits Modifier — confines the curve to set time and value ranges.
  Minimum, Maximum X — drops the original curve data left of the minimum frame and right of the maximum, replacing it with Constant extrapolation.
  Minimum, Maximum Y — clamps the curve's values, never letting them dip below the minimum or rise above the maximum.
Stepped Interpolation Modifier — gives the curve a stair-step look by sampling it every N frames and holding each sampled value, effectively lowering its frame rate so it changes less often and moves choppily.
  Step Size — how many frames to hold each step.
  Offset — how many frames to offset the sample points.

Start Frame — the frame where the effect begins.
End Frame — the frame where the effect stops.

Smooth (Gaussian) Modifier — uses Gaussian smoothing to strip detail and noise from the curve, performing the same smoothing as the Smoothing Operator. It uses linear interpolation for subframes, which can cause motion-blur-related issues. It can also be resource-heavy, with a noticeable performance hit across many F-Curves. Note: it has to be the first modifier in the list, because it needs to know exactly where the keyframes sit — impossible if other modifiers run first — so it's incompatible with the Cycles Modifier.
  Sigma — the Gaussian distribution's shape in frames; lower values sharpen the curve and reduce smoothing, larger values smooth more but are bounded by Filter Width.
  Filter Width — how many frames the filter "sees" around each keyframe; higher values allow more smoothing (a larger Sigma can then reach across more frames) but cost performance.

## Themes

The Themes section lets you customize the interface's appearance and colors. Set each editor's colors on its own by picking the editor from the multi-choice list at the left and adjusting as needed — changes apply in real time on screen. Details like the dot size in the 3D Viewport or the Graph Editor can be changed too.

Preset Management:
Theme Presets — choose a Theme from a list of predefined ones.
Add Theme — puts a custom theme into the preset list.
Remove Theme — takes a custom theme out of the preset list.
Save Theme — saves a custom theme into the preset list as an XML file under the ./scripts/presets/interface_theme/ subdirectory inside one of the config directories.
Install — loads and applies a Blender XML theme file and adds it to the theme presets.
Reset — restores the default theme colors.
Blender ships with a small selection of themes.

## Import/Export SVG as Grease Pencil

The Scalable Vector Graphics (SVG) format is used to trade vector-based illustrations between apps and is supported by vector editors such as Inkscape and by modern browsers, among others. Warning: the exporter runs only in Object Mode.

Import — Reference: menu: File ‣ Import ‣ SVG as Grease Pencil.
Resolution — the resolution for the generated strokes.
Scale — the generated strokes' scale.

Export — Reference: menu: File ‣ Export ‣ Grease Pencil as SVG.
Scene Options — Object: which objects to include. Active (only the active Grease Pencil object), Selected (all selected Grease Pencil objects), or Visible (all visible Grease Pencil objects in the scene).
Export Options:
Frame — which frames to include. Active (only the active keyframe), Selected (all selected keyframes as SVG animation), or Scene (all frames as SVG animation).
Sampling — the precision of stroke sampling; lower values give a more accurate result.
Fill — on, exports the Grease Pencil strokes' fill.
Uniform Width — on, exports strokes at a constant thickness.
Clip Camera — on (with camera view active), exports only the strokes clipped from camera view.
Note: the Grease Pencil strokes are always exported from the view of the current workspace's largest 3D Viewport.

## Defaults

### Defaults

The first time you launch Blender, or after updating to a new version, the Splash Screen's interactive area is swapped for a handful of initial preferences that set how you interact with Blender.

The initial preferences dialog.

Note

You can change any of these later in the Preferences.

### Import Preferences From Previous Version

This option copies your settings from an older Blender — pulling in the previous version's preferences and startup files and loading them, installed add-ons and extensions included.

Importing is necessary because each Blender version keeps its configuration files in its own folders; the Blender's Directory Layout page gives their locations.

To begin fresh on the new version, head to Create New Preferences instead.

Note

Some older add-ons and extensions may not work with a new version, so this option can cause startup errors. If that happens, try Loading Factory Settings first.

### Create New Preferences

Language
The interface language. Entries are grouped into categories by how complete each translation is. More language options live in the Translation Preferences.

Theme
Pick a light or dark theme. Themes can be tuned further in the Preferences. More can be installed from the Blender Extensions Platform, which is optional and needs internet access.

Keymap
Presets for Blender's default keymap. Note this manual assumes you use the default "Blender" keymap.

Blender :

The default keymap. Read more about it here.

Blender 2.7x :

Matches an older series of Blender versions, for upgraders who'd rather not learn the new keymap.

Industry Compatible :

Matches common commercial creation software, for people juggling several such apps. Read more about it here.

Mouse Select
Sets whether the left or right mouse button selects items in Blender. The default is the left button.

Spacebar Action
Sets what Spacebar does.
This and other shortcuts can be remapped in the keymap preferences.

Play :

Starts/stops animation playback.
Handy for animation or video-editing work.

Tools :

Opens the Toolbar under the cursor for quick tool switching. Good for heavy modeling or rigging.

Search :

Opens the Menu Search. Good for someone new to Blender, still unfamiliar with its menus and shortcuts.

Save New Preferences
Stores the choices above and opens the normal Splash Screen.

### Saving Defaults

Preferences save automatically as you change them. You can alter this by following the instructions under Auto-Save Preferences.

To change the default startup file, use File ‣ Defaults ‣ Save Startup File . See Startup File.

Blender keeps its defaults in two places:

Preferences
The Preferences file holds the keymap, add-ons, theme, and other options.

Startup File
The Startup File holds the scene and UI layout shown at startup and on creating a new file ( File ‣ New ).

### Loading Factory Settings

You can roll your customizations back to Blender's defaults:

Preferences
The Preferences Load Factory Settings.

Startup File & Preferences
File ‣ Defaults ‣ Load Factory Settings .

Note

After a factory-settings load, preferences aren't auto-saved.

See Managing Preferences for details.

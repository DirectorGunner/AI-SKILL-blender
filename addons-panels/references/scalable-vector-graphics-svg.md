# Scalable Vector Graphics Svg, Feature Sets, Rigify, Basic ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Scalable Vector Graphics (SVG); Feature Sets; Rigify; Basic; Face; Faces; Rig Types; Spines; Manage UI Translations; Add-ons; Creating Extensions; Extension Licenses; Version Number Guidelines; Snapping; Local View.

## Scalable Vector Graphics (SVG)

The Scalable Vector Graphics (SVG) add-on brings .svg files in through File ▸ Import ▸ Scalable Vector Graphics (.svg). It is on by default (otherwise enable "Scalable Vector Graphics (SVG)" under Preferences ▸ Add-ons). For now it only imports, handles path geometry alone, and exposes no properties.

## Feature Sets

Feature Sets let third-party developers ship sub-add-ons for Rigify that add new Meta-Rigs and Rig Types; like ordinary add-ons, they install from zip files through Rigify's settings. Examples from past and present Rigify developers include Cessen's Rigify Extensions — the original Rigify rigs by Nathan Vegdahl, lightly ported and repackaged to run without legacy mode (their names changed, so legacy-mode meta-rigs aren't directly compatible) — and Experimental Rigs by Alexander Gavrilov, a set of rig experiments (such as limbs with an extra knee/elbow-based IK system and a spline tentacle) some of which may land in Rigify later. Install one by choosing Code ▸ Download ZIP and adding the file through Rigify settings; developer documentation lives on the Blender Developer Documentation.

## Rigify

Rigify covers Basics, Customization, Extensions, and Development, with developer documentation on the Blender Developer Documentation. For reference, its category is Rigging, it provides automatic rigging from building-block components, it is reached from Properties ▸ Armature/Bone, the 3D Viewport ▸ Tools panel, and 3D Viewport ▸ Add menu ▸ Armature, and it ships GPL-licensed with Blender.

## Basic

Rigify basic rig types generate simple single-bone features and support custom rigging done directly in the meta-rig. Unlike chain-based types that usually consume a whole connected chain, single-bone types must be applied to each bone individually even within a connected chain, and they can have connected children driven by a different rig type. basic.copy_chain copies a bone chain with its internal parenting intact (a handy utility for custom rigs); it requires a chain of at least two connected bones, and its Control and Deform booleans create control bones/widgets and deform bones respectively. basic.pivot is a single-bone type that creates a "custom pivot" control which rotates and scales the sub-rigs parented under it — rotating or scaling the control transforms those children, while moving it only relocates the pivot point used by that rotation/scaling. Its options: Master Control (adds a box-widget parent control to move the rig, and is required by every option except Deform Bone), Widget Type (pick a predefined widget for the master instead of the default cube), Switchable Parent (a mechanism to switch the rig's effective parent by a custom property), Register Parent (marks the rig as a candidate parent scope that its children's parent-switches can target), and Tags (comma-separated keywords for that scope used to filter parent choices or pick a default; useful ones include the special "injected", which opens the scope to every child of the parent sub-rig, not only this one's, and "held_object", a control for whatever the character holds, which finger IK favors — pairing injected with held_object suits exactly that kind of control). Pivot Control, when disabled, skips the actual custom pivot, turning the type into a basic.super_copy with parent-switching and a different widget; Deform Bone creates a deform bone. basic.raw_copy copies a bone without the ORG- name prefix — normally meta-rig bones are prefixed ORG- and placed on an invisible layer, which blocks their use as controls or deform bones and makes it hard to carry fully custom rigging over verbatim, so this type omits the automatic prefix, letting you include an appropriate ORG-, MCH-, or DEF- prefix in the meta-rig bone name (or none, to make a control bone). Relink Constraints retargets the bone's constraints to bones created during generation so custom rigging integrates with generated bones: add "@" plus the target name to the constraint name (the ...@bone_name form), and after generation the target is replaced — if the new name is just CTRL, MCH, or DEF, it only swaps the ORG prefix in the existing target name, and for the Armature constraint you can add a @ suffix per target or a single @CTRL/@MCH/@DEF to update all. Parent applies the same name-substitution to the bone's parent; with this on, the bone won't auto-parent to root even when it has no parent, so enter "root" in the Parent field if needed. basic.super_copy simply copies a bone (a utility for adding custom features or specific deform bones): its Control boolean makes a control bone and widget, Widget makes a replacement widget, Widget Type picks a predefined widget instead of the default circle, and Deform makes a deform bone; its Relink Constraints works as in basic.raw_copy and additionally moves constraints whose names are prefixed CTRL: to the control and DEF: to the deform bone.

## Face

Rigify face rig types implement parts of a modular face. face.basic_tongue generates a simple tongue (taken from the original PitchiPoy super_face rig), with B-Bone Segments setting how many b-bone segments each tweak control splits into and Primary Control Layers optionally assigning bone collections to the main control. face.skin_eye is a skin-system parent controller that manages two skin chains (the top and bottom eyelids) and also builds the eye-rotation mechanism: the rig needs two child skin chains whose names carry .T and .B symmetry markers for top and bottom, joined at their ends to form the eye corners, rigged to ride the eye's surface and twist to its normal. It also makes aiming targets for the eye, including a master shared by every eye under the same parent rig, and the eyelids track the eyeball's motion with adjustable influence. Its options: Eyeball and Iris Deforms (deform bones for the eyeball and iris, the iris copying XZ scale from the eye target and sitting at the ORG bone's tail); Eyelid Detach Option (a slider to switch off the mechanism that pins eyelid controls to the eye surface); Split Eyelid Follow Slider (two separate sliders for the eye rotation's effect on X and Z eyelid motion); and Eyelids Follow Default (depending on the split option, the default values for the split sliders, or fixed factors multiplied with the single common follow influence). face.skin_jaw is a skin-system parent controller that drives one or more mouth-skin chain loops as the jaw and mouth controls move: the rig needs one or more child chain loops, each made of four skin chains carrying .T/.B and .L/.R symmetrical names. Those lip loops get organized into layers by distance from the corners to the shared center and rigged with blended jaw and master-mouth influence, while other child rigs become children of the jaw. Its options: Bottom Lip Influence (the jaw's influence on the inner bottom lip with mouth lock off), Locked Influence (the jaw's influence on both lips of a locked mouth), and Secondary Influence Falloff (how much influence fades with each successive lip loop — for bottom loops, the blend shifts from the inner bottom lip toward full jaw influence).

## Faces

faces.super_face builds a face system from the bones childed to the parent that carries the property. It requires every face bone bundled in the faces.super_face sample to be present and parented to the master bone whose Rigify type face property is set. This rig type is being deprecated in favor of the newer modular skin-and-face rigging system.

## Rig Types

Rig types are the components Rigify applies to particular regions of the meta-rig as it generates the armature; each represents a common character feature such as the spine, limbs, or fingers. The available rig types appear in the Bone properties tab when a bone is selected in Pose Mode — scroll down to the Rigify Type panel. The following documents the rig types bundled with Rigify.

## Spines

Rigify spine rigs generate spine structures including the head and tail. spines.super_spine builds a complete bendy, stretchy B-Bone spine from your chain's bone count and the chosen options; it's a composite wrapper around spines.basic_spine, spines.super_head, and spines.basic_tail (note that for the tail, the bone direction is reversed compared with the standalone rig), and the base system needs a chain of at least three connected bones. Its options: Pivot Position (the torso/hips pivot); Head (adds the neck and head systems); Neck Position (the bone where the neck system starts, with the chain's last bone always the head — set neck position to the last bone to build only the head and skip the neck); Tail (adds the tail system); Tail Position (the bone where the tail starts, with the next bone always the hips); X/Y/Z (when generating a tail, which local-axis rotations replicate along the chain); and Assign Tweak Layers. spines.basic_spine defines a bendy, stretchy B-Bone spine, with Pivot Position, Assign Tweak Layers, FK Controls (whether to generate an FK chain), and Assign FK Layers. spines.basic_tail defines a bendy, stretchy B-Bone tail, with X/Y/Z (which local-axis rotations replicate from each control bone to the next) and Assign Tweak Layers. spines.super_head defines a head rig with follow-torso controls, with Assign Tweak Layers.

## Manage UI Translations

Manage UI Translations is enabled by searching "Manage UI Translations" in Preferences ▸ Add-ons and ticking it; the Blender translation guide in the Developer Handbook covers usage. For reference, its category is System, it lets you manage UI translations from inside Blender (updating the main po-files, updating scripts' translations, and so on), it's reached from Topbar ▸ File menu, the Text editor, or any UI control, and it ships bundled with Blender.

## Add-ons

Add-ons extend Blender through Python, and most are delivered via the Extensions system. If one doesn't activate when enabled, check the Console window for errors. Internet access: an add-on that needs the internet must consult the read-only property bpy.app.online_access (governed by Preferences and overridable on the command line with --offline-mode / --online-mode), and can also check bpy.app.online_access_override to learn whether the user is even allowed to toggle Allow Online Access; an add-on that honors this only connects when enabled, though Blender can't stop third-party add-ons that ignore it. Bundle dependencies: to ship as an extension an add-on must be self-contained, carrying every dependency (notably third-party Python modules) — the options are bundling Python wheels (the recommended route), bundling other add-ons together (recommended when one add-on depends on another, taking care that both the standalone and the combined add-on check for already-registered types such as Operators and Panels, so installing them as a bundle and individually doesn't duplicate operators and panels), or Vendorize (to bundle a pure-Python dependency as a sub-module, which avoids version conflicts but takes setup per package). Local storage: an add-on must not assume its own directory is writable (it isn't for "System" repositories), and writing into it is risky because upgrading the extension wipes all its files; an add-on needing a user directory should call `extension_directory = bpy.utils.extension_path_user(__package__, path="", create=True)` (use the path argument for subdirectories), which persists across upgrades but is removed on uninstall. Legacy vs extension add-ons: since Extensions arrived in Blender 4.2 the old add-on style is deprecated; the changes are small but affect existing add-ons, and legacy add-ons stay supported (installable via the "Install legacy Add-on" button in preferences) while maintainers are urged to convert so their add-ons stay future-proof and can update through the extensions platform. Converting a legacy add-on to an extension means: writing a manifest file, deleting the bl_info block (now held in the manifest), replace module-name references with __package__, switch module imports to relative imports, pack external Python dependencies as wheels, and test thoroughly (installing from disk gets you closest to the real experience). Extensions and namespace: legacy add-ons used their module name to reach preferences, which could clash when same-named extensions from different repositories were installed, so the repository name is now part of the namespace — for example, kitsu becomes bl_ext.{repository_module_name}.kitsu, with implications for preferences and imports. User preferences and __package__: an add-on's preferences use the package name as their identifier via __package__, which was allowed but not enforced in legacy add-ons, so this can break backward compatibility:
```text
# Before:
class KitsuPreferences(bpy.types.AddonPreferences):
    bl_idname = "kitsu"
    # ... snip ...
# Access with:
addon_prefs = bpy.context.preferences.addons["kitsu"]

# Now:
class KitsuPreferences(bpy.types.AddonPreferences):
    bl_idname = __package__
    # ... snip ...
# Access with:
addon_prefs = bpy.context.preferences.addons[__package__]
```
An add-on with sub-packages (sub-directories holding their own __init__.py) that needs this identifier must import the top-level package with a relative import — `from .. import __package__ as base_package` — then use base_package instead of __package__ (".." is relative to the package's parent; sub-sub-packages use "..." and so on). Note that __package__ varies between systems, so never hard-code it as a literal string, and extensions must not modify its value or they risk errors. Relative imports: imports of packages within the add-on module must be relative (e.g. `from . import utils` rather than `from kitsu import utils`) — a standard Python feature relevant only to multi-folder add-ons, again allowed but unenforced in legacy add-ons, so it can break backward compatibility.

## Creating Extensions

Extensions are the add-ons or themes that extend Blender's core functionality; they're shared on online platforms and can be installed and updated from inside Blender. The Blender project's official platform is extensions.blender.org and other third-party sites work too as long as they follow the Extensions Platform specification. For add-on guidelines (the requirements for extensions.blender.org) see the Developer Handbook; to configure and manage the extension settings see User Preferences; and for command-line management see the Extension Command Line Arguments.

## Extension Licenses

The Blender Extensions Platform accepts only free and open-source extensions compatible with Blender's own license: add-ons must use GNU General Public License v3.0 or later; themes are recommended to use that same license but any GPL-compatible license is accepted; and assets used within add-ons must be Public Domain (CC0).

## Version Number Guidelines

The Blender Extensions platform mandates no particular version-numbering scheme, so keep whatever you already use; if you don't have one, the following is recommended. Add-on extensions should follow semantic versioning in spirit — it was designed for software libraries with APIs, which add-ons typically aren't (they offer user-facing functionality), so it doesn't strictly apply, but the recommended approach is: use MAJOR.MINOR.PATCH (e.g. 2.3.1); raise MAJOR for changes that remove or alter existing functionality so users can't simply carry on as before (rules of thumb: bump it if the new version doesn't work with data from the old one, or if users must relearn anything non-trivial to keep using it as they were); raise MINOR when adding functionality without much affecting what exists (bump it if new functionality arrives that users can just ignore and continue as before); and raise PATCH for bug fixes and small changes that don't affect the intended functionality (bump it if, bug fixes aside, the version isn't notably different to an end user). These won't cover every case, so use your judgment. Theme extensions don't share those concerns and needn't follow semantic versioning; instead, use an X.Y.Z format (e.g. 2.3.1) where X rises for substantial visual changes or reworks, Y marks "tracks" of the theme for different Blender versions, and Z rises for minor tweaks or visual fixes. Tracks: new Blender versions can introduce breaking changes in the Python API or feature behavior, and if that affects your extension you may keep two concurrent "tracks," one for Blender "old" and one for "new." Use version numbering to do this clearly: if you're on 1.2.1 and want to release for the breaking changes in Blender "new," release that as 1.3.0, then keep fixing the "old" line by bumping its patch number to 1.2.2, 1.2.3, and so on — in effect 1.2.x and 1.3.x are two tracks, each still getting releases. Alternatively, bump the major number for tracks, especially if you expect more than bug fixes on the older line; either way, strongly avoid bumping only the patch for these updates, since you never know when a bug-fix release is needed. Be sure each version's manifest correctly states the Blender versions it's compatible with, and you can also update the compatibility of already-uploaded versions from the extensions website.

## Snapping

Reference — Mode: Object, Edit, and Pose Mode. Location: Header ‣ Snapping. Shortcut: Shift-Tab.

Snapping makes lining objects and mesh elements up with one another straightforward. Switch it on or off with the Snap Off / Snap On toggle in the 3D Viewport header, or engage it briefly by holding Ctrl.

See also Transform Modal Map for additional keyboard shortcuts.

Snap Base — Reference: Mode: Object, Edit, and Pose Mode; Header: Snapping ‣ Snap Base; Shortcut: Shift-Ctrl-Tab. This setting picks which point on your geometry actually meets the target.
Closest — snaps from whichever bounding-box corner (Object Mode) or vertex (Edit Mode) sits nearest the target.
Center — snaps from the current transformation center, i.e. the pivot point. Pairing this with the 3D Cursor lets you choose the snap point entirely by hand.
Median — snaps from the mean position of the selected objects' origins (Object Mode) or vertices (Edit Mode).
Active — snaps from the origin (Object Mode) or center (Edit Mode) of the active element.

Snap Target — Reference: Mode: Object, Edit, and Pose Mode; Header: Snapping ‣ Snap Target; Shortcut: Shift-Ctrl-Tab. This setting picks what the selection gets snapped onto.
Increment — snaps to a virtual grid that begins at the selection's starting location and matches the viewport grid's spacing, effectively shifting the selection in steps equal to one grid cell.
Grid — snaps to the grid drawn in the viewport.
Vertex — snaps to whichever vertex is nearest the mouse pointer.
Edge — snaps to whichever edge is nearest the mouse pointer.
Face — snaps onto the surface of the face beneath the pointer, which is handy for retopology.
Volume — snaps the selection to a depth centered within the object under the cursor. This helps when, say, you want an Armature bone centered inside a character's arm; the other modes would instead drop it on the arm's surface. (Despite the name, this is unrelated to Blender's Volume objects.)
Edge Center — snaps to the midpoint of the edge nearest the pointer.
Edge Perpendicular — snaps to the point on an edge where the line from the selection's start (marked by a white cross) to its new spot meets that edge at a right angle.
Face Center — snaps to the midpoint of the face under the pointer.
Tip: hold Shift-LMB to turn on several snapping modes together.

Snap Target for Individual Elements — Reference: Mode: Object, Edit, and Pose Mode; Header: Snapping ‣ Snap Target for Individual Elements; Shortcut: Shift-Ctrl-Tab.
Face Project — snaps each object (Object Mode) or vertex (Edit Mode) one at a time onto the face hit by projecting from the present viewing depth along the present viewing direction; useful, for instance, to wrap a flat sheet snugly over a curved form.
Face Nearest — snaps each object or vertex individually onto the face closest to its new location and, unlike Face Project, can snap to hidden geometry.
See also the Shrinkwrap constraint / modifier.

Target Selection: configures finer snapping behavior, with the available choices depending on both the mode (Object/Edit) and the chosen Snap Target.
Align Rotation to Target — turns the selection so its Z axis lines up with the target's normal.
Backface Culling — leaves back-facing geometry out of snapping.
Include Active (Edit Mode) — snaps to the active object's other mesh elements.
This is ignored while Proportional Editing is on.
Include Edited (Edit Mode) — snaps to other objects that are likewise in Edit Mode.
Include Non-Edited (Edit Mode) — snaps to other objects that are not in Edit Mode.
Exclude Non-Selectable — restricts snapping to objects that can be selected.
Absolute Increment Snap (Increment) — snaps to the viewport grid outright instead of advancing by grid-cell increments. This resembles a Snap Target of Grid, except Grid pulls the selection to the grid point nearest the cursor.
Snap Peel Object (Volume) — when the target object is made of several overlapping but disconnected mesh islands, Snap To Volume normally targets only the island beneath the cursor. Turning on Snap Peel Object treats the object as a single whole, looking just at its outer "peel" and ignoring inner or enclosed faces.
Snap to Same Target (Face Nearest) — snaps only to the object the selection was nearest before the transform began.
Face Nearest Steps (Face Nearest, Edit Mode) — divides the whole transform into several stages, snapping at each one, which can yield cleaner results in some situations.

Affect: chooses which transforms snapping applies to. Out of the box only movement snaps, but you can extend it to rotation and scaling as well.

Rotation Increment: the angle used for incremental snapping of the rotate operator. Its second figure, the Rotation Precision Increment, drives finer transforms and is engaged by default while Shift is held.

Snapping makes aligning UV elements to one another easy. Toggle it with the magnet icon in the UV Editor's header, or briefly by holding Ctrl. This page is about the Snap header button; the Snap menu is covered under UV Editing.

Snap Target — Reference: Header: Snapping ‣ Snap To; Shortcut: Shift-Ctrl-Tab.
Increment — snaps to grid points, using a virtual grid that begins at the selection's starting location and matches the editor's displayed grid resolution, so you can move the selection in steps of one grid cell.
Grid — snaps to grid points.
Vertex — snaps to whichever vertex is nearest the mouse pointer.

Additional Options:
Snap Base (Vertex) — see 3D Viewport Snapping for details.

Affect — chooses which transforms snapping applies to; out of the box only movement snaps, but you can extend it to rotation and scaling.

Rotation Increment — the angle used for incremental snapping of the rotate operator; its second figure, the Rotation Precision Increment, drives finer transforms and is on by default while Shift is held.

## Local View

Toggle Local View — Reference: Mode: All modes; Menu: View ‣ Local View ‣ Toggle Local View; Shortcut: NumpadSlash, Slash.

Global view shows every 3D object in the scene, whereas Local view isolates the selected object(s) so they alone remain visible. That helps when you're working on objects buried behind others, or when you want to lighten viewport load in heavy scenes. Local view is contextual, set independently per 3D Viewport.

Flip between Global and Local View through the View menu or with NumpadSlash.

Note: in Local View the 3D Cursor isn't tied to the scene — each view keeps its own cursor location.

Tip: newcomers hit NumpadSlash by accident fairly often, so if a swath of your scene seems to have vanished, try pressing NumpadSlash again.

Remove from Local View — Reference: Mode: All modes; Menu: View ‣ Local View ‣ Remove from Local View; Shortcut: Alt-NumpadSlash, Alt-Slash. Pull objects out of Local View by selecting them and running this operator; if the last one is removed, Blender returns to Global View automatically. Hint: this shines in dense scenes where carefully picking objects to isolate isn't practical, especially when they overlap or hide behind ones you'd rather exclude — easier to box-select a region, enter local view, and then strip out the ones you don't want.

# Get Extensions, Introduction, Importing Exporting Files, Stanford Ply ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Get Extensions; Introduction; Importing & Exporting Files; Stanford PLY; Installing on Windows; Point Menu; Brush Settings.

## Get Extensions

The Get Extensions section lets you install and manage extension preferences. See also the Extensions page to learn what extensions are and how to make them.

Installing Extensions — a few routes:
Install from the Website — drag the install URL into Blender.
Install from Blender — search for the extension's name and click Install.
Install from Disk — use the top-right drop-down, or drop an extension .zip package onto Blender.
Note: any installed extension can be removed, but that's permanent; to stop one temporarily, Disable it instead.
Hint: see network troubleshooting for trouble reaching remote repositories.

Updating Extensions — you check for updates yourself; once one is found, Blender lets you update any available extension, and if updates exist an Update All button appears to install them all at once. Whatever version the repository currently offers is always treated as the latest.

Enable/Disable — once installed, an extension can be disabled (or re-enabled) through the user preferences; some types don't support this and always read as enabled. Tip: if an Add-on doesn't activate when enabled, check the Console window for errors.

Extension Settings:
Visit Extensions Platform — opens extensions.blender.org in a browser.
Refresh Remote — manually checks the online repositories for updates.
Refresh Local — rescans extension and legacy add-ons for changes to modules and metadata (much like a restart); issues come back as warnings.
Install Available Updates — updates every extension that has one waiting.
Install from Disk — installs an extension from a .zip package into a Local Repository, with no updates available; it also installs legacy Add-ons (see Installing Legacy Add-ons).

Filter by Type — or narrow to a single type: All (every extension), Add-ons (only add-ons), Themes (only themes).

Repositories — out of the box Blender has one Remote Repository aimed at the Official Blender Extensions Platform plus two Local Repositories. When you need more (to reach third-party platforms, say), you can add them. Click the + icon to add: Add Remote Repository (from a URL) or Add Local Repository (user-managed, for use with Install from Disk). Click the - icon to remove: Remove Repository, or Remove Repository & Files (which also deletes all associated files). These changes are permanent and can't be undone.
Remote Repository — a remote repository that supports listing and updating extensions. Options: Check for Updates on Startup (lets Blender look for updates at launch, with a status-bar notification when any exist) and Access Token (a personal access token some repositories require).
Local Repository — a repository you manage by hand. There are two kinds; new local repositories default to User, which is what you want most of the time. After creating one you can switch it to a System source in the Advanced options; System repositories are meant to bundle extensions with Blender to keep it portable.

## Introduction

Reference — Menu: Edit ‣ Preferences…; Shortcut: Ctrl-Comma.

This chapter covers changing Blender's default configuration through the Preferences editor. Blender Preferences holds settings that govern how Blender behaves; the available options sit in sections down the left of the editor, with a search field above the section list for filtering preferences by name.

Managing Preferences — default preferences are handled from the ☰ menu in the preferences window, which offers:
Auto-Save Preferences — by default, preference changes are saved on exit, so edits to the keymap and Quick Favorites menu persist between Blender sessions; switch it off and a Save Preferences button appears to do it by hand.
Revert to Saved Preferences — undoes any unsaved changes, reloading the last saved state.
Load Factory Preferences — undoes every preference change, returning to the pre-customization state. Note: afterward, auto-save is disabled for the session, letting you drop to factory settings for testing or tutorials without risking auto-saving over your own preferences; run Save Preferences by hand if you want to keep these. Note: this resets only the preferences, not settings in the startup file (app templates, area locations, and any Blender properties outside the preferences) — those revert through File ‣ Defaults.

Searching Preferences — the search field atop the Preferences editor filters sections and panels by the text you enter, highlighting matching categories and panel headers so specific settings are easy to find in large sections. Ctrl-F focuses the field; Alt-F clears it. Note: the Extensions and Add-ons sections sit outside this filter, since they have their own search. Tip: it's worth backing up your preferences in case you lose your configuration — see the directory layout section for where they're stored.

### Introduction

The Vertex Groups panel.

The main job of a vertex group is to label vertices belonging to a given part of a mesh or Lattice object, the legs of a chair, a door's hinges, or a character's arms, hands, and head, say.

Each group can hold a per-vertex weight running from 0 to 1, drawn on by plenty of operators, tools, and modifiers, which is why people sometimes call them "weight groups."

### Usage

You can build vertex groups by hand or have them generated for you. Their most frequent role is armature-driven deformation (also called skinning ), but Blender leans on them in many other places too:

- Shape keys

- Modifiers

- Particle systems

- Physics simulations

See also

Skinning Mesh Objects

Note

Vertex groups are only available for mesh and lattice objects.

### Introduction 

Force fields provide mechanisms to shape simulation behavior, introducing additional motion. Particles, Soft Bodies, Rigid Bodies, and Cloth entities all respond to force field influence. Force fields automatically affect compatible systems. Remove specific simulations or particle systems from their reach by reducing that force field type's influence through the Field Weights panel.

- Objects and particles of any type generate fields, yet only curve objects can produce Curve Guide fields.

- Particles themselves can generate force fields. Refer to Particle Physics.

- Objects need to occupy a shared layer to exert reciprocal effects.

You can constrain field influence on particles to specified object groups (consult Particle Physics documentation).

### Creating a Force Field 

Reference

Mode :

Object Mode

Menu :

Add ‣ Force Field

Panel :

Physics ‣ Force Field

To establish a force field instance, navigate to Add ‣ Force Field and select the desired type. This approach generates an empty object with the field attached.

| Vortex: force field.  | Wind: force field.  | Force: force field.  |

Starting with an existing object, navigate to the Physics tab and select the field category from the Fields menu to attach a field to that object.

Note

Recalculation of particle, soft body, or cloth systems becomes necessary after modifying Fields or Collision settings, accomplished by accessing Free Cache. This does not happen automatically.

Particles interact with any force field type. Soft bodies respond exclusively to Force, Wind, and Vortex (Harmonic fields have minimal useful effect on soft bodies).

### Common Field Settings 

Most fields share identical settings, despite their different mechanisms. Field-specific configurations appear below. Curve Guide and Texture fields employ substantially different interfaces.

Shape

Determines the direction applied to compute effector force. Empty object fields support Point, Line, and Plane shapes, while 3D object fields additionally feature Surface and Every Point, plus Curve for curve objects.

Point :

Omnidirectional influence radiating from the object origin.

Line :

Force operates only within the local XY plane, utilizing the Z axis as the effector.

Plane :

Force affects solely the local Z direction, employing the XY plane as the effector.

Surface :

Force field acts on 3D object surfaces, where the Z axis represents the surface normal.

Every Point :

Each mesh vertex contributes independently as an effector point.

Strength

The intensity of field influence. Positive and negative values reverse the force direction. A force field's strength scales with the object's scale, enabling proportional scene adjustment.

Flow

Introducing nonzero values adds drag force proportional and opposite to point velocity. This reinterprets the force field so the Strength to Flow ratio at any location specifies the velocity of an "air flow" field, with objects drawn toward the flow through drag resistance.

Affect

Location
Influence the position of particles and additional physics entities.

Rotation
Influence the rotation of particles with Dynamic Rotation enabled. Not applicable to other physics systems.

Deactivating both options completely suppresses field influence.

Noise Amount

Adds random variation to force magnitude.

Seed

Determines the randomness seed for noise generation.

Absorption

Force dissipates when collision objects obstruct it.

Wind Factor

Specifies force reduction when directed parallel to a surface, such as cloth. At 1, only the normal component contributes.

### Falloff 

This section lets you configure the force field's spatial profile (when falloff Power exceeds 0).

Shape

Cone :

Falloff adopts a cone shape. Additional options mirror Tube configuration.

Sphere :

Falloff distributes uniformly in all directions like a sphere.

Tube :

Falloff creates a tube profile. Adjust Radial Power and configure Minimum and Maximum distance limits.

Z Direction

Dictates force effect along the Z axis.

+Z :

Force impacts exclusively the positive Z region.

-Z :

Force impacts exclusively the negative Z region.

Both Z :

Force influences both positive and negative Z regions.

Power

Governs how force magnitude decreases with distance. Where r represents the distance from the object origin, force diminishes with 1/( r - min + 1) power. A falloff of 2 yields 1/( r - min + 1) 2, resembling gravitational decay.

Min Distance

Establishes the distance threshold within which the field operates at complete strength. At zero falloff, this lacks effect because the field maintains full strength to Max Distance (or indefinitely). A supplementary circle marks this distance in the viewport.

Max Distance

Defines the upper bound for field influence radius, indicated by an additional circle surrounding the object.

### Introduction

Curves Sculpt Mode allows working with curves using various brushes. It is commonly used for hair grooming, but can be used with all kinds of curves.

The curves' surface object plays an important role in many curves sculpting brushes. Most brushes such as Add Curves require the surface to be set already.

Note

Curves Sculpt tools only use the original mesh of the surface object and don't take its modifiers into account.

### Curves Menu

Snap to Deformed Surface
Re-attach curves to a deformed surface using the existing attachment information. This only works when the topology of the surface mesh has not changed.

Snap to Nearest Surface
Find the closest point on the surface for the root point of every curve and move the root there. This needs to be run after the surface mesh topology changed

Convert to Particle System
Add a new hair particle system, or update an system on the surface object. The operator is used for backwards compatibility with the old hair type particle system.

### Selection Modes

Reference

Mode :

Sculpt Mode

Menu :

3D Viewport Header ‣ Select Mode

Shortcut :

1 , 2

Selection modes limits selection operators to certain curve domains. This feature is makes it easy to select whole segments at once, or to give more granular control over editing.

Control Points :

Allows selection of individual control points.

Curve :

Limits selection to whole curve segments.

### Select Menu

All
Select all control points or curves.

None
Deselect all control points or curves.

Invert
Invert the selection.

Random
Randomizes inside the existing selection or create new random selection if nothing is selected already.

Endpoints
Select endpoints of curves. Only supported in the Control Point selection mode.

Amount Start, End
Number of points to select from the front or back of the curve.

Grow
Select points or curves which are close to already selected elements.

### Controls

Sculpt mode provides several properties that give advanced control of the tool's behavior. These options can be found in the right-hand side of the 3D Viewport's Header.

Mirror
Allows tools to affect curves symmetrically according to the chosen axis.

Use Sculpt Collision
Prevents the curve segments from passing through the Surface Object.

### Display

### Overlays

Cage Opacity
Shows the original curves that are currently being edited which is useful with when procedural deformations or child curves are used.

### Introduction

The adage "a good foundation accelerates the rest" applies well to editing projects. Configuring your workspace and settings to match your requirements determines success. Two setup tiers exist:

- Work Environment settings and configurations:

Applied across all projects at "Blender level"—for instance, extension installation. These affect non-editing projects too. Usually stable across projects and set once.

- Project settings and configurations:

Specific to individual projects and highly variable; for example, output format. Each new project requires evaluating these options.

Many settings bridge both tiers. For instance, automatic proxy generation is togglable globally but adjustable per project or per strip. The Video Editing Workspace layout is defined system-wide but tunable per project.

## Importing & Exporting Files

Reference — Menu: Topbar ‣ File ‣ Import/Export.

Sometimes you want to use files from other 2D or 3D software, or to take what you made in Blender and edit it elsewhere. Handily, Blender supports a wide range of file formats for import and export (ABC, USD, OBJ, FBX, PLY, STL, etc.). Popular formats are enabled by default; others are supported and shipped with Blender and can be turned on in the Preferences via Add-ons. See also the add-ons section for more on the import/export add-ons for these file types.

## Stanford PLY

Reference — Category: Import-Export; Menu: File ‣ Import/Export ‣ Stanford (.ply).

Use the operator to import ASCII or binary PLY-files, picking several files at once; for export you can enable or disable the modifiers and choose which data to export (UV textures, Color Attributes, …).

Import — General — Scale: how much to scale the imported objects about the world's origin.
Scene Unit — applies the current scene's unit (per its unit scale) to the imported data.
Forward Axis, Up Axis — since many apps treat a different axis as "Up", these remap the Forward and Up axes to convert rotations between another app's default up/forward and Blender's. Blender itself uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up needs -Z Forward, Y Up.
Options:
Merge Vertices — tries to combine co-located vertices where it can.
Import Vertex Colors — the color space the PLY's color data was saved in. None (skip vertex color data), sRGB (file's vertex colors are in sRGB Color Space), or Linear (file's vertex colors are in Linear Color Space).

Export — General — Format: ASCII: writes the file in the simple ASCII format, useful when the importing program lacks binary support.
Include: Selected Only — export only selected objects; instanced objects (a collection instanced in the scene, say) count as "selected" when their instancer is.
Scale — how much to scale the exported objects about the world's origin.
Forward Axis, Up Axis — as on import: these remap the Forward and Up axes to convert rotations between another app's default up/forward and Blender's. Blender itself uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up needs -Z Forward, Y Up.
Geometry:
UV Coordinates — writes out the active UV layer's coordinates from Blender.
Vertex Normals — writes out Blender's face and vertex normals (per the faces' smooth setting); usually unneeded since most apps compute their own, but required to match Blender's normal-map textures.
Vertex Colors — the color space the PLY's color data was saved in. None (skip vertex color data), sRGB (in sRGB Color Space), or Linear (in Linear Color Space).
Triangulated Mesh — triangulates every N-gon of four or more vertices (the scene's meshes are untouched), behaving like the Triangulate Modifier set to N-gon Method "Beauty", Quad-method "Shortest Diagonal", Min vertices 4.
Apply Modifiers — exports objects as their evaluated mesh, i.e. the mesh that results once every Modifier has been computed.

## Installing on Windows

### Installing on Windows

If you haven't already, check the Downloading Blender page for the minimum requirements and the available versions.

Download either the zip-file or the Windows Installer File.

Important

On Windows, Blender supports both x64 and arm64 architectures. Grab the variant that matches your CPU's architecture.

### Install from Windows Installer File

The Windows installer lets you pick an installation folder, adds a Start-menu entry, and associates blend-files with Blender. It needs administrator rights.

### Install from Zip

With the zip-file you extract Blender yourself to a folder of choice, then double-click the executable to run it.

No Start-menu item is made and no blend-file association is registered, but you also need no administrator rights. Register the association by hand by clicking Register on the System tab of the Preferences. Alternatively, run blender -r from the Command Line.

For a fully self-contained setup, configuration included, see Portable Installation.

### Install from Microsoft Store

Search the Microsoft Store for Blender and install it from there. Afterward, launch Blender from the Windows Start menu.

### Updating on Windows

There are a few ways to update Blender on Windows. This section covers the common ones.

### Updating from a Windows Installer File

When a release lands, download it from the Blender website. Then run the Windows installer to put the updated version on. To remove an old version, uninstall it through Windows settings or the control panel.

### Updating from a Zip

When a release lands, download it from the Blender website and extract it to a folder of choice, where you can double-click the executable to run Blender. The Install from Zip section says more about making a portable version.

Note: you needn't overwrite your current install — several versions can sit side by side.

### Updating from the Microsoft Store

When a Blender update shows up on the Microsoft Store, it downloads and installs on its own.

See also

The Splash-screen Defaults page, on importing settings from earlier Blender versions and other quick options.

## Point Menu

**Extrude.**

Menu ‣ Point ‣ Extrude; Toolbar ‣ Extrude; shortcut E. Duplicates selected points, which can then be moved; the new points remain connected to the originals.

Note: Since Grease Pencil strokes have only one start and end point, extruding intermediate points creates a new stroke.

**Smooth.**

Menu ‣ Point ‣ Smooth. Softens strokes by reducing location differences among points while maintaining fluid appearance.

Iterations — number of procedure repeats.

Factor — smoothness amount to apply.

Smooth Endpoints — applies smoothing to the stroke's start and end.

Keep Shape — tries to retain the stroke's overall geometry.

Position — when enabled, affects point location.

Radius — when enabled, affects point thickness.

Opacity — when enabled, affects point strength (alpha).

**Vertex Groups.**

Operators for vertex group management.

**Set Handle Type.**

Menu ‣ Point ‣ Set Handle Type; shortcut V. Sets the handle type for Bézier curve points in the selection.

Type — the target handle type:
- Auto: automatic length and direction for smoothest result; converts to Align when moved.
- Vector: both handle parts point to adjacent handles, allowing straight lines or sharp corners; converts to Free when moved.
- Align: handles lie in a straight line for continuous curves without sharp angles.
- Free: independent handles.
- Toggle Free/Align: replaces Free with Align and vice versa.

**Set Corner Type.**

Menu ‣ Point ‣ Set Corner Type. Controls how corners between strokes or segments appear when using stroke thickness or fills, affecting geometry joins at sharp angles.

Corner Type — the style for selected points:
- Round: smoothly rounds the corner with a curved transition.
- Flat: cuts the corner flat with a beveled join.
- Sharp: preserves the original angle.

Miter Cut Angle — angle threshold (degrees) for flattening sharp corners; corners sharper than this become flat when Corner Type is Flat or Round.

## Brush Settings

**Brush Settings.**

Radius — controls the brush radius in pixels. F lets you interactively change size by dragging the mouse and clicking LMB (the brush texture appears inside the circle); type a number then enter while using F to set size numerically.

(Size Pressure) — adjusts radius based on stylus pressure when using a Graphics Tablet.

Strength — governs the intensity of each brush stroke's effect on the model; larger values make the Randomize brush noisier and the Smooth brush more effective. Adjust strength interactively by pressing Shift+F in the 3D Viewport, repositioning the brush, then clicking LMB; type the value numerically while in Shift+F mode.

(Strength Pressure) — modulates strength according to stylus pressure.

Use Falloff — when engaged, enforces Strength falloff; the brush's impact decreases away from the center.

Sculpt Strokes — gate the brush behavior across specific stroke properties (Smooth and Randomize only).

Note: if no filter is active, Affect Position becomes the default.

Affect Position — enable/disable brush influence on point location.

Affect Strength — enable/disable brush influence on point strength (alpha).

Affect Thickness — enable/disable brush influence on point width.

Affect UV — enable/disable brush influence on point UV orientation.

Direction — modality of brush influence (Add to increase, Subtract to decrease).

**Cursor.**

Disable the cursor via a toggle in the Cursor header.

Color — establish the brush ring appearance; mode determines whether a unified Color or distinct Adding/Subtracting hues are available.

**Brush Settings.**

A Brush panel shows in the Toolbar during Weight Paint Mode.

Brush — picks a preset Brush from the Data-Block menu; generate original presets as desired.

Radius (F) — establishes the brush footprint extent.

(Size Pressure) — modulates radius per stylus force with a Graphics Tablet.

Strength — magnitude of weight applied per stroke.

(Strength Pressure) — modulates strength by stylus force.

Use Falloff — when active, enforces Strength falloff; the brush's potency decreases radially outward.

Weight (Ctrl+F) — weight magnitude (shown as hue) deployed by the brush. Ctrl+RMB to inherit the weight value at the cursor.

Direction (D) — brush polarity toggle: Add increments weight; Subtract decrements it. Cycle with D.

### Brush Settings

Brush settings panel.

Details on brush settings applicable to all modes are available here:

Brush
Core and specialized options.

Texture
Pigmentation and mask texture controls.

Stroke
Stroke execution and adjustments.

Falloff
Falloff shape and configuration.

Cursor
Cursor styling and appearance options.

### Brush Settings

Brush settings panel.

Details on brush settings applicable to all modes are available here:

Brush
Core and specialized options.

Texture
Pigmentation and mask texture controls.

Stroke
Stroke execution and adjustments.

Falloff
Falloff shape and configuration.

Cursor
Cursor styling and appearance options.

### Brush Settings

Brush settings panel.

Details on brush settings applicable to all modes are available here:

Brush
Core and specialized options.

Texture
Pigmentation and mask texture controls.

Stroke
Stroke execution and adjustments.

Falloff
Falloff shape and configuration.

Cursor
Cursor styling and appearance options.

### Brush Settings

Brush settings panel.

Brush configuration guides live in these sections:

Brush
Fundamental and nuanced options.

Stroke
Stroke approaches and options.

Falloff
Falloff contours and options.

Cursor
Cursor and display options.

# Troubleshooting Windows Intel, Troubleshooting Windows Nvidia, Troubleshooting Windows Other Gpu, Selecting Strips ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Troubleshooting Windows – Intel; Troubleshooting Windows – NVIDIA; Troubleshooting Windows – Other GPU; Selecting Strips; Clip Strip; Sequencer Scene; Directory Structure; Storyboarding.

## Troubleshooting Windows – Intel

### Troubleshooting Windows – Intel

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

Windows sources GPU drivers from card makers (Intel). OS patches auto-install, or your computer vendor supplies variants.

Yet these don't always include newest versions or may degrade. Official driver sources remain advisable.

Download Latest Intel Drivers

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

### Compatibility

Startup crashes sometimes resolve via compatibility mode. Right-click the Blender app and pick Properties ‣
Compatibility then toggle Run this program in compatibility mode . Use Apply to confirm.

### Common Problems

### Unsupported Graphics Driver Error

Your GPU lacks minimum OpenGL 3.3 that Blender needs.

Latest driver version might raise OpenGL capacity; some hardware simply ages beyond modern Blender. Try Blender 2.79 previously. Post-2.8 Blender (introducing EEVEE) curtails older hardware backing.

### Crash on Startup

Try command-line launching to spot helpful debugging output.

Windows GPU drivers occasionally damage or get replaced by OS updates. Uninstall all (multiple vendors' sets exist) and reinstall clean from maker sources.

### Poor Performance

- Refresh GPU drivers (prior section).

- Laptops: confirm active dedicated GPU (earlier section).

- Dial down quality Preferences ‣ System ‣ Memory & Limits .

- Revert GPU setting changes if made.

### Render Errors

Consult EEVEE and Cycles material
individually.

### Wrong Selection in 3D Viewport

Reference Invalid Selection, Disable Anti-Aliasing.

### Virtual Machines

Inside VMs, OpenGL forwarding to hosts causes complications.

PCI passthrough setup solves this.

Certain hosts activate GPU sharing. Some makers limit to higher tiers.

### Information

View active GPU and driver via Help ‣ Save System Info in
Blender. OpenGL section reveals GPU, vendor, driver version.

### Legacy Intel HD 4000/5000

Intel 3rd, 4th or 5th generation iGPUs crash on latest Intel driver launch. Earlier versions work:

- 20.19.15.4835

- 20.19.15.4963

- 20.19.15.5063

Known failing versions:

- 20.19.15.5126

- 20.19.15.5144

- 20.19.15.5166

- 20.19.15.5171

Download older Intel Drivers

## Troubleshooting Windows – NVIDIA

### Troubleshooting Windows – NVIDIA

Blender relies on OpenGL to render the 3D Viewport and interface elements. The GPU and its drivers play a significant role in how Blender performs and behaves overall.

This section offers practical solutions for visual glitches, EEVEE and Cycles issues, and GPU-related crashes.

### Drivers

Keeping graphics drivers current frequently resolves performance and stability issues. Bug fixes in newer drivers enable Blender to function properly.

On Windows, GPU manufacturers provide drivers directly through NVIDIA. Windows Update may install graphics drivers automatically, or your system manufacturer may supply its own versions.

These bundled versions are not necessarily the latest releases and may have degradation. Always install official drivers from the manufacturer.

Download Latest NVIDIA Drivers

### Laptops

Many modern laptops include two graphics processors. One is integrated into the CPU (commonly Intel or AMD) with lower power consumption, and a dedicated GPU (AMD or NVIDIA) that delivers stronger performance but draws more power.

For optimal results with Blender, the dedicated GPU should handle rendering. Configure which GPU runs which program in your driver settings or the operating system.

If you experience glitches or crashes tied to the integrated GPU, switching to the dedicated option often resolves them. Similarly, if the dedicated GPU causes problems, the integrated option may be more stable.

### Common Problems

### Unsupported Graphics Driver Error

Your graphics card and drivers do not meet Blender's minimum OpenGL 3.3 requirement.

Installing the latest driver version can upgrade your OpenGL support, though some older hardware simply cannot run current Blender versions. Blender 2.79 or earlier may be your only option. From Blender 2.8 onward (with EEVEE added), compatibility with legacy graphics hardware has declined.

### Crash on Startup

Run Blender from a terminal to see if error output provides clues.

On Windows, GPU drivers sometimes become corrupted or are incorrectly replaced during Windows Update. In these situations, removing all graphics drivers (which may include multiple copies from Intel, AMD, and NVIDIA) and performing a fresh installation from the manufacturer's website often helps.

### Poor Performance

- Keep graphics drivers updated (see above).

- On laptops, verify you are using a dedicated GPU (see above).

- Lower quality settings via Preferences ‣ System ‣ Memory & Limits.

- Revert any modifications you made in graphics driver settings.

### Render Errors

Check EEVEE and Cycles documentation for specific guidance.

### Wrong Selection in 3D Viewport

See Invalid Selection, Disable Anti-Aliasing.

### Virtual Machines

Running Blender in a VM frequently encounters problems when OpenGL commands route through the host OS.

Use PCI passthrough to resolve this.

Some VM platforms need GPU paravirtualization enabled. Certain GPU makers limit this to higher-end cards or specific models.

### Information

Find your GPU and driver version in Help ‣ Save System Info within Blender. The OpenGL section displays your card model, vendor, and driver version.

## Troubleshooting Windows – Other GPU

### Troubleshooting Windows – Other GPU

OpenGL powers Blender's 3D Viewport and UI. Your graphics processor and drivers significantly influence Blender's stability and speed.

This section compiles troubleshooting options for visual artifacts, EEVEE and Cycles difficulties, and crashes caused by GPU problems.

### Drivers

Upgrading drivers regularly fixes many issues. Newer releases contain corrections that allow Blender to work reliably.

Windows GPU drivers come from the card manufacturer. Windows Update may install them automatically, or your computer manufacturer might provide versions.

### Laptops

Dual-GPU configurations are common in portable systems for efficiency. The first GPU resides on the processor (typically Intel or AMD) and uses less energy. The second is a standalone unit (AMD or NVIDIA) delivering faster performance at higher power cost.

For best Blender performance, the standalone GPU should be active. You can choose which GPU handles which application through your graphics driver or OS settings.

GPU-related crashes with the integrated version suggest trying the standalone; conversely, problems with the standalone might point toward using the integrated GPU.

### Common Problems

### Unsupported Graphics Driver Error

Your GPU and driver lack the required OpenGL 3.3 support that Blender needs.

Updating to the newest driver can boost OpenGL capability, but older cards may not support new Blender builds. In that case, Blender 2.79 or an earlier version is necessary. From version 2.8 forward (when EEVEE was introduced), older GPU support has decreased.

### Crash on Startup

Try launching Blender through a terminal window to view any debug output that appears during load.

Windows sometimes corrupts GPU drivers or replaces them incorrectly when updating the system. Removing all graphics drivers (there may be installations from Intel, AMD, and NVIDIA) and installing fresh copies from the vendor helps resolve this.

### Poor Performance

- Update graphics drivers (see above).

- On portable systems, make sure the standalone GPU is selected (see above).

- Lower quality via Preferences ‣ System ‣ Memory & Limits.

- Undo any settings changes you made in the graphics driver software.

### Render Errors

See EEVEE and Cycles documentation for details.

### Wrong Selection in 3D Viewport

See Invalid Selection, Disable Anti-Aliasing.

### Virtual Machines

VMs struggle when OpenGL drawing passes through the host system.

Set up PCI passthrough to fix this issue.

Some virtualization hosts require GPU paravirtualization support. Certain GPU vendors reserve this for high-end or professional cards.

### Information

To view your GPU and driver details, open Help ‣ Save System Info in Blender. Look at the OpenGL block for card name, maker, and driver version.

## Selecting Strips

### Selecting Strips

A light outline marks the active sequence strip.
Click LMB in the middle to pick the full item.

### Select Menu

The Select menu offers various selection approaches.

All A
Picks every strip in the timeline.

None Alt - A
Clears all selections.

Invert Ctrl - I
Reverses what is selected.

Box Select B
Refer to Box Select.

Box Select (Include Handles) Ctrl - B
Identical to Box Select; additionally grabs edges. Single edge alters span; paired edges shift the full strip.

Select Grouped Shift - G
Pick items matching the active one. By default, unlike items deselect; adjust in Adjust Last Operation panel.

Type
Picks strips of the same kind. For example, picks all Movies if a Movie is active.

Global Type
Picks strips of the same category (video or sound) as the active one.

Effect Type
If active is an effect, picks all effects. Otherwise picks non-effects.

Data
Picks strips using the same supply (video file, scene, movie clip or mask) as active.

Effect
Finds effects applied to the active item, and picks all strips also using them. E.g., picks all Gaussian Blurred strips.

Effect/Linked
Picks items below the active strip that overlap it timewise; then effect strips it uses; then content it powers.

Overlap
Picks items that fully or partly line up with the active one.

Select Linked

All Ctrl - L / Less Ctrl - NumpadMinus / More Ctrl - NumpadPlus
Append or drop adjacent items from selection.

Side of Frame

Left/Right [ / ]
Picks items wholly left or right of the playhead.

Current
Picks items crossing the playhead.

Handle

Both, Left, Right
Picks left, right, or both edges of selected items.

Both/Left/Right Neighbor
Picks the edge of the adjacent item in the selected direction(s).

Channel
Picks all items in the same rows as currently selected items.

## Clip Strip

### Clip Strip

A Clip Strip links to a Movie Clip data-block within the Movie Clip Editor timeline.

The clip can be refined in the Movie Clip Editor, including motion monitoring, image stabilization, and distortion fixes.

### Options

Reference

Panel :

Sidebar region ‣ Strip ‣ Movie Clip

Movie Clip
Selects the Movie Clip asset.
For asset menu usage, check Data-Block Menu.

Use: 2D Stabilized Clip
Shows the clip with motion stabilization enabled.
Tracking tools configure stabilization.

Use: Undistorted Clip
Shows the clip with lens aberration correction applied based on camera calibration.

Frame Range
Lists the clip's original beginning and conclusion, before strip-level changes.

## Sequencer Scene

### Sequencer Scene

The video sequencer relies on a dedicated scene data-block holding the edit. This is the Sequencer Scene.

Separating the sequencer into its own scene offers advantages: managing multiple edit versions in one file, and supporting workflows with different scenes and scene strips. See the section on multi-scene editing and scene strips below.

### Usage

### Creating a Sequencer Scene

To begin with the Sequencer, create or activate an existing Scene.

- Open a workspace including a Video Sequence Editor.

- Click the "New" button in the Sequencer header to make a new Sequencer Scene, or select an existing one.

### Working with Multiple Scenes

The sequencer scene is independent from the active window scene, enabling simultaneous work on scene strips and their referenced scenes within one workspace.

A typical arrangement:

- Workspace combining a Video Sequence Editor and a 3D Viewport.

- Sequencer Scene in the VSE (e.g., titled "Edit").

- Additional scenes for distinct shots or locations.

Add scene strips referencing the existing scenes (or new ones). Then activate Sync Scene Time in the Sequencer Playback Controls. The active scene (and 3D Viewport display) updates to match the current scene strip in the Sequencer.

This arrangement allows rapid scene switching via timeline scrubbing or playback.

### Playback Context

Since the Sequencer Scene is separate from the active scene, playback depends on context. Sequencer playback shows the Sequencer Scene. Other editors play the active window scene.

### Rendering

Render and output settings for the Sequencer Scene match regular scenes. These appear in the Output tab of the Properties editor. These settings follow the active window scene by default (unless a scene is pinned to the properties).

When the active scene differs from the Sequencer Scene in the workspace, the "Render" menu includes separate options to render the Sequencer Scene (bypassing the active Scene).

## Directory Structure

### Directory Structure

A video project typically combines varied asset categories:

- Video files: clips (or "movies"), photos, graphics (charts, symbols, …), and Visual Effects (masks, lens effects, motion graphics).

- Audio files: recorded speech, narration, soundtracks, and Sound Effects (ambience, transitions, …).

- Project files: blend documents and backups, render outputs, and supporting materials (scripts, visual plans).

These form a complex file ecosystem. Organizing into a main project folder with logical subfolders prevents accidents (accidental deletion → "file not found" errors) and loss (forgotten assets → "file missing" errors). Structure and naming conventions provide clarity.

See also

Blender can pack some files into blend documents (see Packed Data). Video files, being very large, should remain external and stored in the project directory.

Good practice includes consistent naming and metadata usage. Figure 1 shows one approach using the categorization above. Numbered directories match typical production workflow.

Figure 1: Organizing your project.

## Storyboarding

### Storyboarding

Storyboarding in Blender presents a flexible approach to planning, visualizing, and refining shots ahead of production. It unifies 2D drawing, 3D positioning, and editing into a single, non-destructive workflow.

Within Blender's unified environment, artists produce storyboards using the identical tools for layout, animation, and final render output. This maintains visual consistency in composition, timing, and camera movement from early planning through finished work.

A typical Blender storyboarding setup comprises:

- Multiple Scenes: Each houses an individual shot or camera position, keeping resources organized.

- Grease Pencil Drawings: Sketching panels in 3D space or atop camera views for rapid composition testing.

- Video Sequence Editor: Assembles scene strips, audio, and timing into a complete sequence.

- Linked Assets: Reuses characters, objects, and environments across scenes for visual unity.

- Asset Libraries and Overrides: Manages shared materials across production pipelines.

This workflow bridges 2D storyboarding and 3D previsualization (sometimes called "3D animatics"). It accommodates solo projects to group pipelines where multiple contributors work on shots, layout, and editing simultaneously.

Blender's integration keeps storyboards, edits, and scene information connected. A camera, character position, or Grease Pencil mark automatically updates in the edit timeline—simplifying revisions and supporting speedy iteration from concept to finished animation.

### Getting Started

Blender supplies a built-in Storyboarding app template designed as a quick, practical launching point for new storyboard projects.

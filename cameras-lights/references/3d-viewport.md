# 3D Viewport, Troubleshooting Macos Amd, Troubleshooting Macos Intel, Troubleshooting Macos Nvidia ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: 3D Viewport; Troubleshooting macOS – AMD; Troubleshooting macOS – Intel; Troubleshooting macOS – NVIDIA; Troubleshooting macOS – Other GPU; Drivers; Common Problems; Troubleshooting Graphics Hardware; Troubleshooting Linux – AMD; Troubleshooting Linux – Intel; Troubleshooting Linux – NVIDIA; Troubleshooting Linux – Other GPU; Troubleshooting Windows – AMD.

## 3D Viewport

### 3D Viewport

### Rendering

### Depth Buffer Glitches

Setting broad clipping ranges shows near and far items but cuts depth precision, creating errors.

| Model with no clipping artifacts. | Model with clipping artifacts. | Mesh with artifacts in Edit Mode. |

Avoidance tactics:

- Increase near clipping for expansive scenes.

- Decrease far clipping when objects remain close.

Orthographic mode uses far Clip End alone; high values still risk errors. Universal across 3D apps.

### Objects Invisible in Camera View

Broad scenes may hide objects in Camera View. Low camera clipping could cause this. Cameras show only objects
inside clipping bounds.

### Performance

### Slow Rendering

Viewport sluggishness stems from multiple sources.

Old Hardware
Occasionally, your system—chiefly the GPU—struggles keeping pace with dense models.

Upgrade Graphics Driver
Updating drivers occasionally resolves sluggish selection.

### Slow Selection

OpenGL selection in Blender sometimes slows on certain GPU drivers.
Dense geometry intensifies problems.

Remedies:

GPU Depth Picking (Preferences)
Navigate Preferences ‣ Viewport ‣ Selection .

Off by default, disabling trades selection precision for speed.

Upgrade Graphics Driver
Newer drivers resolve performance in some scenarios. Modern versions suit 3D work.

Select Centers (Workaround)
Object Mode with Ctrl -held selecting targets centers. Helps on its own, avoiding OpenGL checks.

Change Display Mode (Workaround)
Wireframe mode accelerates object switching.

Note

These workarounds lack permanence, yet help if stuck with inadequate OpenGL hardware.

Ultimately, upgrade hardware if stuck.

### Viewport Playback Frame Rate Limited

Viewport playback capped near 60 FPS typically means VSync is on, found in GPU settings.
Disable for higher rates, though display limits may apply.

Varies per system and GPU.

### Navigation

### Lost in Space

Accidental scene navigation leaves you blank-screened. Two fixes:

- Click an object in the Outliner, then focus with
View ‣ Frame Selected or NumpadPeriod .

- Press Home to display all scene items.

### Invisible Limit Zooming In

Zoom feels blocked sometimes. Blender orbits around a pivot.

Useful for multi-angle object viewing (like wheel pottery). But awkward for scene exploration or inner modeling.

#### Solutions

- Employ View Dolly.

- Use Walk/Fly Navigation.

- Auto Depth + Zoom to Mouse Position ensure distance to cursor point.

- Zoom Region resets the pivot meanwhile.

- Reposition around cursor Alt - MMB . Uses cursor location as your center.

- Get an NDOF (3D mouse), covered in peripherals settings.

### Tools

### Invalid Selection

Certain setups cause selection failure. Edit Mode vertex/edge/face picking shows erratic picks.

OpenGL-based picking requires correct GPU driver communication.

Attempted remedies:

Disable Multisampling
Most frequent cause.

Known issues exist on some cards with multisampling.

Access graphics settings and toggle multisampling off.

Change Anti-Aliasing Sample Settings
OpenGL setup affects which sample modes function.

Trial-and-error finds working setups.

Upgrade Graphics Driver
OpenGL questions need recent drivers.

Prevalent but unsolved on many versions.

## Troubleshooting macOS – AMD

### Troubleshooting macOS – AMD

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

macOS bundles drivers into the OS; upgrading macOS itself updates them.

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

## Troubleshooting macOS – Intel

### Troubleshooting macOS – Intel

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

macOS bundles drivers into the OS; upgrading macOS itself updates them.

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

## Troubleshooting macOS – NVIDIA

### Troubleshooting macOS – NVIDIA

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

macOS bundles drivers into the OS; upgrading macOS itself updates them.

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

## Troubleshooting macOS – Other GPU

### Troubleshooting macOS – Other GPU

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

macOS bundles drivers into the OS; upgrading macOS itself updates them.

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

## Drivers

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

## Common Problems

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

## Troubleshooting Graphics Hardware

### Troubleshooting Graphics Hardware

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

## Troubleshooting Linux – AMD

### Troubleshooting Linux – AMD

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

On Linux, packages supply GPU drivers from distributions. Installation usually happens via package/OS upgrades. Many distros provide several packages for multiple versions, letting you select.

AMD graphics code sits public, except OpenCL included with paid Pro versions. Distribution packages typically suit best. AMD hosts downloads if needing cutting-edge.

AMD Drivers and Support Website

Mesa packages numerous AMD and Intel chip improvements. Installing/upgrading fresh Mesa releases works best. Custom channels enable this on certain OS versions. Ubuntu's kisak-mesa PPA exemplifies this.

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

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

## Troubleshooting Linux – Intel

### Troubleshooting Linux – Intel

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

On Linux, packages supply GPU drivers from distributions. Installation usually happens via package/OS upgrades. Many distros provide several packages for multiple versions, letting you select.

Mesa packages numerous AMD and Intel chip improvements. Installing/upgrading fresh Mesa releases works best. Custom channels enable this on certain OS versions. Ubuntu's kisak-mesa PPA exemplifies this.

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

## Troubleshooting Linux – NVIDIA

### Troubleshooting Linux – NVIDIA

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

On Linux, packages supply GPU drivers from distributions. Installation usually happens via package/OS upgrades. Many distros provide several packages for multiple versions, letting you select.

NVIDIA offers community (Nouveau) and proprietary (NVIDIA) GPU options. Community lacks NVIDIA optimization/completeness. Blender works best on proprietary. Distribution packages suit most; manual download aids cutting-edge needs, particularly new GPUs.

Note, pre-550 drivers lack Vulkan compatibility!

NVIDIA Website

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

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

## Troubleshooting Linux – Other GPU

### Troubleshooting Linux – Other GPU

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

On Linux, packages supply GPU drivers from distributions. Installation usually happens via package/OS upgrades. Many distros provide several packages for multiple versions, letting you select.

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

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

## Troubleshooting Windows – AMD

### Troubleshooting Windows – AMD

Blender uses OpenGL for the 3D Viewport and interface. GPU and driver
significantly shape Blender function and speed.

Solutions for glitches, EEVEE/Cycles issues, and GPU crashes follow.

### Drivers

Latest GPU drivers often remedy issues. Updates patch problems improving Blender execution.

Windows sources GPU drivers from card makers (AMD). OS patches auto-install, or your computer vendor supplies variants.

Yet these don't always include newest versions or may degrade. Official driver sources remain advisable.

Download Latest AMD Drivers

### Laptops

Portable systems typically pack dual GPUs for efficiency. A slower built-in GPU in the processor (Intel/AMD,
lower power) coexists with speedier discrete GPU (AMD/NVIDIA, higher power).

Top performance comes from the discrete option for Blender. GPU preference per application is set via
driver or OS controls.

Discrete GPU glitches suggest trying built-in instead. Built-in problems suggest the opposite.

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

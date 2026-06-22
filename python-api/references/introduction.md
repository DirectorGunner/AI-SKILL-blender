# Introduction, Sequencer Preview, Stl, About Free Software And The Gpl ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Introduction; Sequencer & Preview; STL; About Free Software and the GPL; Installing Blender; Installing from Steam; Brushes; Drawing Plane; Stroke Placement.

## Introduction

The Sequencer view is where the bulk of video editing takes place; it presents a stack of channels for building strips in.

Blender offers various tools for editing Grease Pencil strokes, including operations to add, duplicate, move, and remove elements.

Note: Editing multiple Grease Pencil objects simultaneously is not currently supported.

**Accessing Stroke Editing Tools.**

Available via the Toolbar, the Stroke menu in the 3D Viewport header, context menus (RMB), and individual shortcuts.

Toolbar — upon selecting a stroke and pressing Tab to enter Edit Mode, the Toolbar transitions from Object Tools to Stroke editing panels; not every stroke tool is exposed in this panel.

Menus — the Stroke Menu is located in the header.

Context Menu — RMB displays the complete Stroke Menu.

### Introduction 

Blender ships a wide range of operators for mesh editing, reached through the 3D Viewport's menu
and context menu while in Edit Mode. A few of those menus also open as popovers via shortcut:

- Ctrl - V Vertex

- Ctrl - E Edge

- Ctrl - F Face

Certain operators let you transform a mesh element or change a value interactively by moving the
cursor. These generally also accept Ctrl to toggle snapping and Shift to slow things down for
extra precision.

### Introduction

A typical modeling session starts by roughing out a form from primitives, then layering on detail and refining the trickier parts with assorted tools.

Three main modes in the 3D Viewport serve this:

Object Mode
Handles top-level operations like making objects, joining them, and managing shape keys along with UV/color layers.

Edit Mode
Where most polygon-level mesh work happens; this chapter is mostly about it.

Sculpt Mode
A different editing approach that pushes the mesh around with brushes as if it were clay. See the Sculpting & Painting section.

### Introduction

The tools covered here are for selecting mesh elements.

See also

The Selecting page contains information about selecting in general.

### Selection Modes

Reference

Mode :

Edit Mode

Menu :

3D Viewport Header ‣ Select Mode

Shortcut :

1 , 2 , 3
( Shift Multiple Selection Modes,
Ctrl Expand/Contract Selection)

Edit Mode gives you three selection modes, Vertex, Edge, and Face. Switch among them with the header button in the 3D Viewport or the shortcut key.

Selection mode buttons

Vertex 1
Here vertices appear as dots, black when unselected, orange when selected, and white for the active one.

Edge 2
Here vertices are hidden. Edges show black when unselected, yellow when selected, and white for the active edge.

Face 3
Here selected faces fill with orange, and the active face also gets a white border.

| Vertex mode example.  | Edge mode example.  | Face mode example.  |

### Switching Selection Mode

Moving "up" the ladder, from Vertices to Edges or Edges to Faces, keeps the old selection only where it forms a whole element in the new mode.

So with all four of a face's edges selected, going from Edges to Faces keeps that face; any edges short of a full face fall away.

Going "down," everything stays selected. Select a face and switch to Edge mode, for instance, and all four of its edges come along.

| Selection in Edge mode.  | Switching to Face mode.  |

### Multiple Selection Modes

Hold Shift as you switch and several modes can run at once.

### Expand/Contract Selection

Holding Ctrl while moving to a "higher" mode expands the selection, fully taking in elements of the new mode that were only partly covered before.

| Selection in Vertex mode.  | Switching to Edge mode while holding Ctrl.  |

Holding Ctrl into a "lower" mode does the reverse, contracting the selection by dropping new-mode elements that have any unselected neighbor.

### X-Ray

X-Ray shading lets you both see hidden geometry and select it. The trade-off: you can no longer click a face anywhere on its surface, only on the selection dot at its center.

| X-ray enabled.  | X-ray disabled.  |

### Select Menu

All A
Select all.

None Alt - A
Select none.

Invert Ctrl - I
Swap selected and unselected geometry.

Box Select B
Interactive box selection.

Circle Select C
Interactive circle selection.

Lasso Select
Interactive free-form selection.

Select Mirror Shift - Ctrl - M
Mirror the selection to the mesh's other side.

Select Random
Grabs a random set of vertices, edges, or faces by percentage.

Checker Deselect
Drops every other element, keyed off the active one.

More/Less

More Ctrl - NumpadPlus
Push the selection outward to the bordering elements.

Less Ctrl - NumpadMinus
Pull the selection in, dropping its border elements.

Next Active Shift - Ctrl - NumpadPlus
Picks the element that "logically follows" your last two.

Previous Active Shift - Ctrl - NumpadMinus
Drops the last element and reactivates the one before it.

Select Similar Shift - G
Grabs elements resembling the current selection.

Select All by Trait
Grabs geometry hitting certain undesirable conditions.

Select Linked

Linked
Grabs everything joined, near or far, to the current selection.

Shortest Path
Grabs the elements on the shortest path between your last two.

Linked Flat Faces
Spreads to faces roughly coplanar with the selected ones.

Select Loops

Edge Loops
Grabs edges sharing an edge loop with the selected ones.

Edge Rings
Grabs edges sharing an edge ring with the selected ones.

Select Loop Inner-Region
Grabs the faces walled in by the selected boundary edges.

Select Boundary Loop
Trades the face selection for an edge selection of its borders.

Sharp Edges
Grabs edges at sharp corners.

Side of Active Vertex Mode
Grabs every vertex on one side, say the right, of the active vertex.

By Attribute
Grabs elements whose active attribute reads True.

### Known Issues

### Dense Meshes

With X-Ray off, a Box/Circle/Lasso Select over a dense mesh can miss vertices in the region because of overlap. If that happens, zoom in or turn on X-Ray to work around it.

### N-Gons in Face Select Mode

N-gon having its selection dot inside another face.

In X-Ray and Wireframe shading the face selection dot just sits at the face's center, which for a concave n-gon may not land on the face's surface. That can make the dot hard to find, all the more so when another face fills the cavity.

### Introduction

Picture a Curve as a smooth line; a Surface is its two-dimensional counterpart — a smooth sheet driven by a set of control points.
Put another way, it extends the idea of a Curve,
which is itself a smooth line, into a sheet.

Surface in Edit Mode.

The control points sit in a grid, with the rows (U direction) drawn as yellow lines and the columns (V direction) as pink ones.
Open or closed (cyclic) along one direction, the other, or both, the surface can take on shapes
such as a cylinder or, equally, a ball.

Turning a Surface into a mesh is done from
Object ‣ Convert ‣ Mesh or the context menu item
Convert To ‣ Mesh .

### Introduction

Blender stores objects within a primary database (the blend-file itself) rather than placing them directly in scenes.

The blend-file and its stored data.

They are then referenced into as many Scenes as desired.

When stored in a scene, they belong to a so-called scene collection. Ultimately all scene objects are contained within this special collection.

The scene collection.

### Collections

Though the scene collection contains all Scene's objects, users can create their own collections for improved organization.

It functions like a Venn diagram, where all objects are part of the scene collection but may also be part of multiple collections.

Venn diagram.

The result provides a clear and adaptable method to arrange objects at the Scene level.

Scene organization.

### Naming and Nesting

Collections can be named and arranged hierarchically. Like OS folders with subfolders, collections support nesting.

Nested collections.

Example: a building collection may hold a sleeping room collection, which itself contains a fixtures group listing a cot, storage cabinet, and related items.

### Color Tagging

Collections support color assignments for better visual grouping. The assigned color appears alongside collection icons in the Outliner and other interface areas. Blender's current Theme defines the available palette.

To assign a color, invoke the Set Color Tag tool via the Outliner.

### Introduction

Vertex Groups frequently contain enormous counts of associated vertices
and therefore enormous counts of weights (one per assigned vertex).
Weight Painting presents a method to organize vast weight information
in a highly intuitive manner.

Its principal application involves character setup, where groups determine
the relative bone effects on geometry. It also controls particle output, strands, numerous
modifiers, shape keys, and more.

Vertex group in Weight Paint Mode.

Access Weight Paint Mode via the Mode selector Ctrl - Tab .
The mesh appears softly colored using a rainbow gradient.
This coloring represents the weights assigned to each vertex in the current group.
Blue signals empty (0.0) and red signals full (1.0) by default.

By applying weight brushes to the surface, you assign weights to vertices.
Initial painting automatically generates weights in the active group
(creating it if nonexistent).

Vertex Groups appear in the list popover at the header center.

### The Weighting Color Code

A cold/hot gradient visualizes weights,
where minimal values (near 0.0) display blue (cold)
and maximal values (near 1.0) display red (hot).
Intermediate values show rainbow transitions (blue, green, yellow, orange, red).

The color spectrum and their respective weights.

Additionally, Blender offers a special visual marker
(toggleable) for vertices lacking reference: They render black.
Resulting display shows referenced sections (cold/hot tones) alongside
referenced-free sections (black) simultaneously.
Most helpful when diagnosing weight issues.
Check Viewport Overlays.

Unreferenced vertices example.

Note

Customize weight gradient hues via enabling
Custom Weight Paint Range within Editing preferences.

### Normalized Weight Workflow

For deformation purposes, weights typically demand normalization,
so all deforming group weights per vertex equal 1.
The Armature modifier performs this automatically, so strict painting-phase normalization remains optional.

However, despite complexity, normalized operation provides advantages,
unlocking specialized tools and simplifying influence calculations—
when normalized, the current group's impact needs no knowledge of
other group values on the same vertex.

Support tools aid normalized-weight workflows:

Normalize All
To start normalized-weight work, first normalize current data.
Normalize All handles this.
Confirm correct mode selection and deactivate Lock Active .

Auto Normalize
Once initially normalized,
enable Auto Normalize
to sustain normalization automatically during painting.
This alerts certain tools that weights remain pre-normalized.

Vertex group locking
Any group can lock against changes. Use
the lock toggle in the group interface, or employ bone selection with
the locks menu.

This guards against unintended modifications. Since Auto Normalize respects it as well, in normalized workflows
it carries greater significance—locking freezes chosen bone influences,
so repainting others redistributes across unlocked options only.

This becomes crucial in multi-bone regions, enabling careful tweaking and redistribution
using a targeted bone subset. Locking can help here,
complemented by
the Lock Relative option, which shows unlocked groups as
though re-scaled with locked groups absent, making locked bones seem invisible.

Multi-Paint
Finally, Multi-Paint lets
multiple picked bones behave as unified, shifting
their combined influence while maintaining their ratio. With locking,
this permits balancing one bone set versus others, with a third set
having unchanged influence via locks.

Technically unnecessary for normalized workflows, but given non-normalized
weights can exceed 1, visual feedback performs optimally with Auto Normalize active.

Tip

As illustration, when handling a ring, e.g. lips or aperture, selecting with
Multi-Paint exposes difference between the loop overall and adjacent bones,
whereas locking surrounding choices and using Lock Relative shows variation among
loop components. Thus the intricate cross-dimensional variation of each bone separates
into two independent one-dimensional shifts.

## Sequencer & Preview

This view type packs both the preview and the sequencer into one editor.

In general it's better to skip this view type and instead keep two editors, one as the Preview and one as the Sequencer, because:
- Most Preview tools, such as Move and Rotate, aren't available in Sequencer & Preview.
- You can't add a small editor (a File Browser, say) on the side that's only as tall as the preview.
- You can't maximize the preview on another screen.
One easy way to get two separate editors is to open the default Video Editing workspace (you might have to hit the "+" icon past the tabs on the right to find it).

## STL

Reference — Category: Import-Export; Menu: File ‣ Import/Export ‣ Stl (.stl).

The STL-file format is handy when you mean to import/export files for CAD software, and it's also common for loading into 3D-printing software.

Importing — General — Scale: how much to scale the imported objects about the world's origin.
Scene Unit — applies the current scene's unit (per its unit scale) to the imported data.
Forward / Up Axis — since many apps point a different axis upward, these remap the Forward and Up axes to convert rotations between another app's default up/forward and Blender's. Blender itself uses Y forward, Z up (its front view looks along +Y); an app that uses Y as up needs -Z forward, Y up.
Options:
Facet Normals — uses (imports) facet normals (this still gives flat shading).
Validate Mesh — checks the imported mesh for corrupt data and repairs it if needed; with it off, bad data may crash display or editing. It slows importing but is recommended, since data errors aren't always obvious.

Exporting — General — Format: ASCII: exports the stl-file as ASCII rather than binary.
Batch — exports each object as its own STL file.
Include: Selection Only — when checked, exports only selected objects; instanced objects (a collection instanced in the scene, say) count as "selected" when their instancer is.
Scale — how much to scale the exported objects about the world's origin.
Scene Unit — applies the current scene's unit (per its unit scale) to the exported data.
Forward, Up — since many apps treat a different axis as "Up", these remap the Forward and Up axes to convert rotations between another app's default up/forward and Blender's. Blender itself uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up needs -Z Forward, Y Up.
Geometry:
Apply Modifiers — exports objects as their evaluated mesh, i.e. the mesh that results once every Modifier has been computed.

## About Free Software and the GPL

### About Free Software and the GPL

Hearing "free software," many people first think "no cost." That's often the case, but as the Free Software Foundation uses it — the group behind the GNU Project and author of the GNU General Public License — the phrase means "free as in freedom," not "free as in price" (the latter is usually called "free as in free beer," or gratis). In this sense, free software is something you may use, copy, modify, and redistribute without limit. Compare that to how most commercial packages are licensed: you may install on one computer, may make no copies, and never see the source code. Free software hands enormous freedom to the end user. And because the source is available to everyone, far more bugs get spotted and fixed.

Once a program carries the GNU General Public License (the GPL):

- You may use the program for any purpose.

- You may modify it and access its source code.

- You may copy and distribute it.

- You may improve it and release your own versions.

In exchange, distributing a GPL'd program brings responsibilities — ones meant to protect your freedoms and everyone else's:

- Ship a copy of the GPL with the program so recipients know their rights under the license.

- Include the source code, or make it freely available.

- If you distribute a modified version, license your changes under the GPL (or a compatible license).

- You may not add licensing restrictions beyond the GPL's terms (you can't make a GPL'd program proprietary).

For more on the GPL, see its page on the GNU Project website.

Note

The GPL covers the Blender application, not the artwork you make with it; for more, see the Blender License.

## Installing Blender

### Installing Blender

A new Blender ships roughly every three months. The release notes keep you current on what's changed.

### System Requirements

Blender downloads for Windows, macOS, and Linux. Keep your graphics drivers current and make sure OpenGL is properly supported. There are minimum and recommended requirements, so confirm yours are met before installing.

Other hardware, such as graphics tablets and 3D mice, is covered later under Configuring Hardware.

### Download Blender

Several binary packages are on offer, each pitched at a different level of stability and trading newest features against reliability. Which suits you depends on how you weigh those two: a studio might prefer long-term support, a hobbyist the newest features, and others simply a look at what's coming. The packages below cover every case.

Stable Release
Carries the latest features and is regarded as stable, free of regressions. A new one lands about every three months.

Long-term Support
Built for long-running projects that need a rock-steady Blender. LTS releases get two years of support and receive no new features, API changes, or improvements. A fresh LTS arrives yearly. They do get the odd minor patch (such as 4.2.6) for stability or critical fixes.

Daily Builds
Refreshed each day with the newest in-development changes, built automatically on a schedule. They're less tested than the releases above and may break or crash. An Alpha build is still seeing major changes and new features, whereas a Beta is feature-complete and being polished for stability.

Expect stability to rise as you go Alpha → Beta → Release Candidate (RC) → final release.

Build from Source
Blender's source is free to study or to compile and run. Ordinary users aren't expected to build it, but doing so has upsides:

- You're always up to date.

- You can reach any version or branch where a feature is in progress.

- It can be customized freely.

- Curious users can read the source and make small tweaks to watch the effects and better understand how Blender works.

Installing a binary — whether the latest stable release or a daily build — works the same way. Follow your platform's steps below.

Note

Blender is built to run without an internet connection, so it has no built-in update system. That means you'll update Blender yourself, using the platform-specific upgrade steps in the sections below.

### Installation Guides

## Installing from Steam

### Installing from Steam

Steam is a software-distribution platform. Using the Steam client you can download and update Blender, following the steps below for Linux, macOS, or Windows.

Grab and install the Steam client for your OS.

Once it's installed, open the client and sign in to your Steam account, or make one if you don't already have it. After signing in, go to the Store tab, search for "Blender", and click the green Install button. Blender then turns up in the client's Library tab, ready to launch. If you like, right-click it in your library list to drop a shortcut on the desktop.

See also

Installing Blender from Steam on Linux and Windows won't auto-associate the .blend filename extension with Blender. To set that association, follow the processes on the Linux and Windows installation pages.

### Updating with Steam

When a Blender update appears on Steam, the client downloads and applies it for you.

## Brushes

### Brushes

The Essentials asset library ships a range of draw-mode brushes, and here they all are at a glance.

### Draw Brushes
Draw brushes are the dedicated brush type that drives Grease Pencil drawing tools. Swap brushes from the Tool Settings. Pencil, Ink, marker, and the rest are really just setting variations on one shared Draw Brush . Build as many brushes as you like, each tuned differently to chase a distinct artistic look while drawing.

### Fill Brushes
Fill brushes are the dedicated brush type that drives the Grease Pencil Fill tools. Swap brushes from the Tool Settings. The various fill brushes are setting variations on a single shared Fill Brush . Build as many brushes as you like, each tuned differently for a distinct result when filling areas.

### Erase Brushes
Erase brushes are the dedicated brush type that drives the Grease Pencil Erase tools. Swap brushes from the Tool Settings. Soft and hard erasers are setting variations on one shared Erase Brush . Build as many brushes as you like, each tuned differently for distinct erasing effects. The Erase Brush also carries two more special eraser types: point and stroke.

### Brushes

### Brush Types

Refer to Brush Type reference.

Below is a listing of accessible brush types paired with Essentials asset library brushes using those types.

Paint Vertex
Brushes: Paint Hard, Paint Soft, Paint Hard Pressure, Paint Soft Pressure, Airbrush

Applies chosen pigmentation to the mesh.

Blur
Brushes: Blur

Equalizes colors across adjacent vertices. In this method the Color Value parameter is not used. Brush strength determines the smoothing amount.

Average
Brushes: Average

Balances color by applying the averaged result across all colors in the brush region.

Smear
Brushes: Smear

Transfers colors by gathering them from the brush zone and "pulling" them. Functions like finger painting.

## Drawing Plane

### Drawing Plane

Reference

Mode :

Draw Mode and Sculpt Mode

Header :

Drawing Plane

Drawing Planes pop-over.

Use the Drawing Planes selector to choose which plane your strokes are drawn on.

To check which plane is active while drawing, switch on Canvas under Viewport Overlays. Viewport Display explains the Canvas settings.

Note

Drawing Plane changes apply to new strokes only and leave existing ones alone.

View :

Strokes are drawn with the current 3D Viewport orientation.

Front (X-Z) :

Strokes are drawn on the plane determined by the XZ axes (front view).

Side (Y-Z) :

Strokes are drawn on the plane determined by the YZ axes (side view).

Top (X-Y) :

Strokes are drawn on the plane determined by the XY axes (top view).

Cursor :

Strokes are drawn with the current 3D cursor orientation.

| Front.  | Side.  | Top.  | View.  | Cursor.  |

## Stroke Placement

### Stroke Placement

Reference

Mode :

Draw Mode

Header :

Stroke Placement

Stroke Placement pop-over.

Use the Stroke Placement selector to choose where your strokes are drawn.

Note

Stroke Placement changes apply to new strokes only and leave the existing ones alone.

Origin :

Strokes are placed at Grease Pencil object origin.

3D Cursor :

Strokes are placed at 3D cursor.

Surface :

Strokes will stick on mesh surfaces.

Offset
Distance from the mesh surface to place the new strokes.

Project Onto Selected
Only project the strokes onto selected objects.

Stroke :

Strokes will stick on other strokes.

Target

All Points :

All the points of the new stroke sticks to other strokes.

End Points :

Only the start and end points of the new stroke sticks to other strokes.

First Point :

Only the start point of the new stroke sticks to other strokes.

| Origin.  | 3D Cursor.  | Surface.  | Stroke.  |

# Dyntopo, Remesh, Symmetry, Edit Face Set ...

> Blender Add-ons, Panels, and Properties reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Dyntopo; Remesh; Symmetry; Edit Face Set; Using Vertex Groups; Python Errors; Reporting a Bug; Meta Strips; Color Strip; BMesh Module (bmesh); Boid Operators; Cloth Operators.

## Dyntopo

### Dyntopo

Reference

Mode :

Sculpt Mode

Panel :

Sidebar ‣ Tool ‣ Dyntopo

Dynamic Topology (Dyntopo) can be enabled via the checkbox. When active, most brushes subdivide the mesh as you sculpt.

For background on dynamic topology, see the Introduction.

Detail Size/Percentage, Resolution R
The detail level for each Detail Type is configured here. Depending on which Detail Type is in use, this displays as a pixel measurement (px) or percentage value.

R enables interactive detail adjustment with real-time density visualization in the 3D viewport.

Sample Detail Size
When using Constant Detail mode, you can sample the detail value from a specific mesh region by clicking the pipette icon next to the detail field and then clicking on that area.

Refine Method
This setting determines the topology adjustment technique applied.

Subdivide Edges :

Like the Subdivide operation, this subdivides topology to match the specified detail level.

Collapse Edges :

When geometry becomes excessively dense and falls below the detail specification, edges are collapsed to match the detail size.

Subdivide Collapse :

This combines both approaches, subdividing edges smaller than the detail size while collapsing overly dense areas.

Detailing
Dyntopo offers multiple detail creation methods to establish dynamic surface detail.

Relative Detail :

This approach bases detail on pixel count; as you zoom out, details appear coarser; zooming in reveals finer details.

Constant Detail :

This maintains uniform detail across the entire mesh. The detail represents a Blender unit divisor—larger values produce finer results.

Brush Detail :

This grants greater control by using brush size as the basis for topology generation. Increase or decrease topology by changing brush size. Full detail creates topology matching the brush radius.

Manual Detail :

Comparable to constant detail, this percentage-based approach only applies detailing when using Flood Fill.

Detail Flood Fill Ctrl - R
With Constant or Manual Detailing, this option activates and fills your whole mesh uniformly using the configured resolution value.

## Remesh

### Remesh

Reference

Mode :

Sculpt Mode

Header :

Tool Settings ‣ Remesh

Panel :

Sidebar ‣ Tool ‣ Remesh

Shortcut :

Ctrl - R

For background on remeshing fundamentals, visit the Introduction.

Voxel Size R
Determines the resolution or refinement level of the remeshed result. The value specifies the size (in object space) of individual Voxels. These voxels are assembled around the geometry and determine the new topology. For example, 0.5m creates topological patches of roughly 0.5m size (assuming Preserve Volume is active). Lower values retain finer details but generate denser topology.

Adjust voxel size from the 3D viewport using R. The shortcut shows an interactive grid showing the resulting voxel scale. Move the cursor toward the grid center to reduce voxel size, or away to increase it. Holding Shift refines adjustment precision.

Sample Voxel Size
Adjust Voxel Size by selecting a mesh area that represents your desired polygon density after remeshing.

Adaptivity
Reduces the face count by simplifying geometry where detail is unnecessary. This introduces triangulation to faces that don't require as much precision. Note: Adaptivity values above zero disable Fix Poles.

Fix Poles
Produces fewer poles at the cost of additional computation to achieve better topological layout.

Preserve

Volume
Instructs the algorithm to maintain the original mesh volume. Activation may increase processing time depending on mesh intricacy.

Paint Mask
Transfers the paint mask to the remeshed geometry.

Face Sets
Transfers Face Sets to the remeshed geometry.

Color Attributes
Transfers Color Attributes to the remeshed geometry.

Voxel Remesh
Executes the remeshing operation, creating a new manifold mesh from the current mesh's volume. This action discards all mesh data layers linked to the original geometry.

See also

Remesh modifier

### Known Limitations

- Remeshing operates only on base mesh data and ignores topology from modifiers, shape keys, rigging, and other deformations.

- Remeshing is incompatible with the Multiresolution Modifier.

## Symmetry

### Symmetry

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Tool ‣ Symmetry

Mirror
Duplicate brush strokes across specified local axes. To change axis directions, rotate the geometry in Edit Mode, not Object Mode.

Lock
These three buttons prevent model alteration along chosen local axes during sculpting.

Tiling
This option enables seamless stroke tiling along specified axes. Create repeating surface patterns with this feature.

Feather
Attenuates stroke strength at axis intersection zones.

Radial X, Y, Z
Enable radial symmetry around the specified axes. The value determines how many times the stroke repeats within a full 360-degree rotation.

Tile Offset X, Y, Z
Adjusts the spacing between tiles along each axis. The default spacing is one unit.

Symmetrize

Direction
Specifies which direction the symmetry operation applies.

Merge Distance
Controls the vertex proximity threshold for merging symmetrical vertices during the Symmetrize operation.

Symmetrize
Applies directional symmetry. Since Dyntopo generates detail progressively, meshes may drift from symmetry; this operator restores it.

## Edit Face Set

### Edit Face Set

Reference

Mode :

Sculpt Mode

Tool :

Toolbar ‣ Edit Face Set

Operator :

Grow/Shrink Face Sets

Modifies the Face Set at the cursor position.

### Tool Settings

Mode
Specifies the operation to execute on the face set.

Grow Face Set :

Extends the face set perimeter by one face following mesh topology. Also accessible as a shortcut operator via Ctrl - W.

Shrink Face Set :

Contracts the face set boundary by one face following mesh topology. Also accessible as a shortcut operator via Ctrl - Alt - W.

Delete Geometry :

Removes all faces assigned to the face set.

Fair Positions :

Generates a smooth, even geometry surface from the face set. Ideal for trimming areas with excessive vertex density or situations requiring vertex preservation (such as when using Multires sculpting).

Fair Tangency :

Creates the smoothest possible surface from the face set by minimizing tangent discontinuities. Valuable for establishing smooth curves on intricate topology where standard smoothing alone is insufficient.

| Before fairing. | After using Fair Positions. | After using Fair Tangency. |

Strength
Determines the magnitude of the operation's effect on mesh geometry. Only available for fairing modes.

Modify Hidden
Include hidden face sets when applying the operation.

## Using Vertex Groups

### Using Vertex Groups

### Vertex Groups for Bones

One of the principal applications of weight painting. Though Blender can
generate weights mechanically (see
Skinning),
manual tweaking or full creation suits many cases,
particularly near articulations.

Steps involved:

- Pick the armature, shift to Pose Mode using Ctrl - Tab .

- Verify that Edit ‣ Lock Object Modes remains off
in the menu bar.

- Pick the mesh and switch to Weight Paint Mode .

- Ensure Bone Selection appears enabled in the 3D Viewport header.

- Pick a bone using Alt - LMB (or Shift - Ctrl - LMB ).
The bone's group activates and displays its assignments on the surface.

- Use LMB to assign weights for that bone.

Note

Only one bone selection at a time in this context.

Tip

Bones frequently hide inside geometry, becoming hard to click.
Activate In Front
to address this for the armature.

Missing a group when starting? Blender creates one automatically.

Symmetrical mesh + symmetrical armature? Use
Mirror Vertex Groups
to auto-generate groups and assignments on the other side.

### Vertex Groups for Particles

Weight painted particle emission.

Via Vertex Groups
in a particle system's configuration,
control density, length, etc. across mesh zones.

## Python Errors

### Python Errors

### Precompiled Libraries

Though uncommon, Python add-ons sometimes bundle their own compiled libraries. These differ from plain Python code—they do not transfer between operating systems.

A precompiled library might not work with your Blender setup (perhaps it was compiled for a different Python version, or you are trying to load 32-bit code on a 64-bit system).

Check that any included .pyd or .so files match your OS.

### Platform Specific

### Windows

#### Mixed Python Libraries (DLLs)

Python errors or add-on failures during activation (e.g: ... is not a valid Win32 application.) often trace back to conflicting system libraries. Although Blender ships with its own Python, duplicate or incompatible copies can interfere.

A Python traceback.

To identify which library is causing failure, check the error output.

This usually appears near the end of the traceback. The example above pinpoints _socket. This corresponds to a file named _socket.py or _socket.pyd.

You can paste this script into the Text editor and run it to search for conflicting copies of your library.
(Output appears in the Command Line Window.)

`text
import os
import sys

### Change this based on the library you wish to test
test_lib = "_socket.pyd"

def GetSystemDirectory():
from ctypes import windll, create_string_buffer, sizeof
GetSystemDirectory = windll.kernel32.GetSystemDirectoryA
buffer = create_string_buffer(260)
GetSystemDirectory(buffer, sizeof(buffer))
return os.fsdecode(buffer.value)

def library_search_paths():
return (
### Windows search paths
os.path.dirname(sys.argv[0]),
os.getcwd(),
GetSystemDirectory(),
os.environ["WINDIR"], # GetWindowsDirectory
*os.environ["PATH"].split(";"),

### regular Python search paths
*sys.path,
)

def check_library_duplicate(libname):
paths = [p for p in library_search_paths()
if os.path.exists(os.path.join(p, libname))]

print("Library %r found in %d locations:" % (libname, len(paths)))
for p in paths:
print("- %r" % p)

check_library_duplicate(test_lib)
`

## Reporting a Bug

### Reporting a Bug

Helping the Blender team fix problems requires following the proper reporting workflow.

### Before Reporting

Before filing a report, take basic precautions to confirm you have a genuine issue.

- Confirm Blender was set up per the guidelines in this manual under Installing Blender.

- Work through the Troubleshooting section starting with factory settings. Many problems come from bad configuration or outdated add-ons incompatible with the latest Blender.

Registration Required

Reporting on the Blender Projects platform requires a Blender ID. The interface will walk you through creating one if this is your first time.

### Report from within Blender

Filing from inside Blender is suggested. This auto-fills fields like your machine details, OS version, and Blender build number.

To file a report:

- Use Topbar ‣ Help ‣ Report a Bug to open your web browser to the Blender reporting form with some details pre-filled.

- Give your report a clear, concise name—avoid complex sentences.

- Describe the steps that trigger the problem. Reproducible bugs are easier to track, so include any context you can. Make sure you complete the Short description of error and Exact steps for others to reproduce the error areas.

- Attach images if they clarify the issue. Video is acceptable but only if essential to show the problem.

- For crashes, upload the crash log as mentioned below: Attaching a Crash Log.

Note

If Blender crashes before fully launching, the in-app method will not work. In that case, follow Manual Report on the Web.

### Report on the Web

Web-based reporting mirrors the in-app approach, plus you manually enter system info.

To file a report:

- Go to the bug template on projects.blender.org.

- Write a clear, direct title—avoid long, winding phrases.

- Fill in your machine details and Blender version under System Information and Blender Version.

- Explain how to reproduce the issue. Hard-to-reproduce bugs take longer to resolve, so be thorough. Complete the Short description of error and Exact steps for others to reproduce the error sections.

- Include pictures if they help clarify the problem. Video is fine, but only when truly necessary.

- If a crash happened, supply the crash log per the section below: Attaching a Crash Log.

### Attaching a Crash Log

Providing a crash log (when Blender completely stops) can speed up developer investigation. Follow the steps in Crashes to find the file and attach it to your report.

## Meta Strips

### Meta Strips

A Meta Strip bundles multiple strips into a single composite item.
This minimizes visual noise in the Sequencer and simplifies intricate workflows.
After formation, a Meta strip acts like any other and can shift, be resized, muted, or get effects.

Meta strips serve as organization aids.
When edits stack many overlapping or layered strips, grouping related ones into a Meta strip reduces clutter.

Make Meta Strip Ctrl - G
Choose all strips to bundle, then press Ctrl - G.
The new Meta spans from the earliest strip's start to the latest's end, collapsing channels into one.

UnMeta Strip Ctrl - Alt - G
Break apart a Meta strip to restore its contents to their original places and channels.
Useful for removing the Meta shell while preserving interior strips.

Example of Meta strips.

### Editing Meta Strips

Open a Meta strip with Tab to see only its contents.
The timeline switches to display the interior.

Press Tab once more to exit and return to the full timeline.

Meta strips may be nested within other Meta strips.
Pressing Tab goes out one level.
To exit more levels, ensure no Meta is active before pressing Tab.

Note

Meta strips default to Replace blending.
Depending on what's inside, visuals might differ from the source strips. Adjust the Meta's blend mode if needed.

### Use Cases

A frequent use is applying one effect to several clips.
For instance, if a shot spans multiple video files, bundle them in a Meta strip and add effects there instead of duplicating effects.

Meta strips also help structure sections—intros, sequences, graphics—as individual items.

See also

An Adjustment Layer effect strip achieves similar outcomes, applying effects to all strips below without bundling.

### Properties

Meta strips match other strip types in attributes.
Changes to Meta properties act on all contained strips as a group.

## Color Strip

### Color Strip

This effect produces uniform-color frames.
By default, the Color strip creates 25 frames, but you can extend it by adjusting one edge.
Cross it with your primary strip for transition effects.

### Options

Color
Select the color field in the Effect panel in the Sidebar region to alter the appearance.

## BMesh Module (bmesh)

### BMesh Module (bmesh) 

This module provides access to Blender's bmesh data structures.

### Introduction 

This API grants access to Blender's internal mesh editing system, including geometry connectivity and
editing operations such as split, separate, collapse, and dissolve.
The exposed features closely match the C API,
providing Python access to the underlying functions used by Blender's mesh editing tools.

For a detailed explanation of BMesh data types and their relationships see:
BMesh Design Document.

Note

Disk and Radial data is not exposed by the Python API since this is for internal use only.

Warning

TODO items are…

- add access to BMesh walkers .

- add custom-data manipulation functions add, remove or rename.

### Example Script 

`\text
### This example assumes we have a mesh object selected

import bpy
import bmesh

### Get the active mesh
me = bpy.context.object.data

### Get a BMesh representation
bm = bmesh.new() # create an empty BMesh
bm.from_mesh(me) # fill it in from a Mesh

### Modify the BMesh, can do anything here...
for v in bm.verts:
v.co.x += 1.0

### Finish up, write the bmesh back to the mesh
bm.to_mesh(me)
bm.free() # free and prevent further access
`\

### Standalone Module 

The BMesh module is written to be standalone except for mathutils
which is used for vertex locations and normals.
The only other exception to this are when converting mesh data to and from bpy.types.Mesh.

### Mesh Access 

There are two ways to access BMesh data, you can create a new BMesh by converting a mesh from
bpy.types.BlendData.meshes or by accessing the current Edit-Mode mesh.
See: bmesh.types.BMesh.from_mesh() and bmesh.from_edit_mesh() respectively.

When explicitly converting from mesh data Python owns the data, that means that
the mesh only exists while Python holds a reference to it.
The script is responsible for putting it back into a mesh data-block when the edits are done.

Note that unlike bpy , a BMesh does not necessarily correspond to data in the currently open blend-file,
a BMesh can be created, edited and freed without the user ever seeing or having access to it.
Unlike Edit-Mode, the BMesh module can use multiple BMesh instances at once.

Take care when dealing with multiple BMesh instances since the mesh data can use a lot of memory.
While a mesh that the Python script owns will be freed when the script holds no references to it,
it's good practice to call bmesh.types.BMesh.free() which will remove all the mesh data immediately
and disable further access.

### Edit-Mode Tessellation 

When writing scripts that operate on Edit-Mode data you will normally want to re-calculate the tessellation after
running the script, this needs to be called explicitly.
The BMesh itself does not store the triangulated faces, instead they are stored in the bpy.types.Mesh,
to refresh tessellation triangles call bpy.types.Mesh.calc_loop_triangles().

### CustomData Access 

BMesh has a unified way to access mesh attributes such as UVs, vertex colors, shape keys, edge crease, etc.
This works by having a layers property on BMesh data sequences to access the custom data layers
which can then be used to access the actual data on each vert, edge, face or loop.

Here are some examples:

`\text
uv_lay = bm.loops.layers.uv.active

for face in bm.faces:
for loop in face.loops:
uv = loop[uv_lay].uv
print("Loop UV: %f, %f" % uv[:])
vert = loop.vert
print("Loop Vert: (%f,%f,%f)" % vert.co[:])
`\

`\text
shape_lay = bm.verts.layers.shape["Key.001"]

for vert in bm.verts:
shape = vert[shape_lay]
print("Vert Shape: %f, %f, %f" % (shape.x, shape.y, shape.z))
`\

`\text
### In this example the active vertex group index is used,
### this is stored in the object, not the `BMesh`.
group_index = obj.vertex_groups.active_index

### Only ever one deform weight layer.
dvert_lay = bm.verts.layers.deform.active

for vert in bm.verts:
dvert = vert[dvert_lay]

if group_index in dvert:
print("Weight %f" % dvert[group_index])
else:
print("Setting Weight")
dvert[group_index] = 0.5
`\

### Keeping a Correct State 

When modeling in Blender there are certain assumptions made about the state of the mesh:

- Hidden geometry isn't selected.

- When an edge is selected, its vertices are selected too.

- When a face is selected, its edges and vertices are selected.

- Duplicate edges / faces don't exist.

- Faces have at least three vertices.

To give developers flexibility these conventions are not enforced,
yet tools must leave the mesh in a valid state or else other tools may behave incorrectly.
Any errors that arise from not following these conventions is considered a bug in the script,
not a bug in Blender.

### Selection / Flushing 

As mentioned above, it is possible to create an invalid selection state
(by selecting a face and then deselecting one of its vertices for example),
mostly the best way to solve this is to flush the selection
after performing a series of edits. This validates the selection state.

### Module Functions 

bmesh. from_edit_mesh ( mesh ) 

Return a BMesh from this mesh, currently the mesh must already be in editmode.

Parameters :

mesh (bpy.types.Mesh) – The editmode mesh.

Returns :

the BMesh associated with this mesh.

Return type :

bmesh.types.BMesh

bmesh. new ( * , use_operators = True ) 

Parameters :

use_operators ( bool ) – Support calling operators in bmesh.ops (uses some extra memory per vert/edge/face).

Returns :

Return a new, empty BMesh.

Return type :

bmesh.types.BMesh

bmesh. update_edit_mesh ( mesh , * , loop_triangles = True , destructive = True ) 

Update the mesh after changes to the BMesh in editmode,
optionally recalculating n-gon tessellation.

Parameters :

- mesh (bpy.types.Mesh) – The editmode mesh.

- loop_triangles ( bool ) – Option to recalculate n-gon tessellation.

- destructive ( bool ) – Use when geometry has been added or removed.

## Boid Operators

### Boid Operators

bpy.ops.boid. rule_add ( * , type = 'GOAL' )

Introduce a boid constraint into the current boid state.

Parameters :

type (Literal[Boidrule Type Items]) – Type, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. rule_del ( )

Discard the current boid constraint.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. rule_move_down ( )

Shift the boid constraint downward in the series.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. rule_move_up ( )

Shift the boid constraint upward in the series.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. state_add ( )

Bring in a boid state into the particle engine.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. state_del ( )

Discard the current boid state.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. state_move_down ( )

Shift the boid state downward in the series.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.boid. state_move_up ( )

Shift the boid state upward in the series.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Cloth Operators

### Cloth Operators

bpy.ops.cloth. preset_add ( * , name = '' , remove_name = False , remove_active = False )

Add or remove a Cloth Preset

Parameters :

- name ( str ) – Name, Name of the preset, used to make the path name (optional, never None)

- remove_name ( bool ) – remove_name, (optional)

- remove_active ( bool ) – remove_active, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

File :

startup/bl_operators/presets.py:119

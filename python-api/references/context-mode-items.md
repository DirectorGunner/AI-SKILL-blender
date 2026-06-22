# Context Mode Items, Curve Fit Method Items, Curve Normal Mode Items, Curves Handle Type Items ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Context Mode Items; Curve Fit Method Items; Curve Normal Mode Items; Curves Handle Type Items; Driver Target Rotation Mode Items; Dt Layers Select Dst Items; Dt Layers Select Src Items; Dt Method Edge Items; Dt Method Loop Items; Dt Method Poly Items; Dt Method Vertex Items; Dt Mix Mode Items; Event Direction Items; Event Value Items; Fileselect Params Sort Items; Geometry Component Type Items; Grease Pencil Selectmode Items; Linestyle Geometry Modifier Type Items.

## Context Mode Items

### Context Mode Items

`EDIT_MESH` :

Mesh Edit.

`EDIT_CURVE` :

Curve Edit.

`EDIT_CURVES` :

Curves Edit.

`EDIT_SURFACE` :

Surface Edit.

`EDIT_TEXT` :

Text Edit.

`EDIT_ARMATURE` :

Armature Edit.

`EDIT_METABALL` :

Metaball Edit.

`EDIT_LATTICE` :

Lattice Edit.

`EDIT_GREASE_PENCIL` :

Grease Pencil Edit.

`EDIT_POINTCLOUD` :

Point Cloud Edit.

POSE :

Pose.

SCULPT :

Sculpt.

`PAINT_WEIGHT` :

Weight Paint.

`PAINT_VERTEX` :

Vertex Paint.

`PAINT_TEXTURE` :

Texture Paint.

PARTICLE :

Particle.

OBJECT :

Object.

`PAINT_GPENCIL` :

Grease Pencil Paint.

`EDIT_GPENCIL` :

Grease Pencil Edit.

`SCULPT_GPENCIL` :

Grease Pencil Sculpt.

`WEIGHT_GPENCIL` :

Grease Pencil Weight Paint.

`VERTEX_GPENCIL` :

Grease Pencil Vertex Paint.

`SCULPT_CURVES` :

Curves Sculpt.

`PAINT_GREASE_PENCIL` :

Grease Pencil Paint.

`SCULPT_GREASE_PENCIL` :

Grease Pencil Sculpt.

`WEIGHT_GREASE_PENCIL` :

Grease Pencil Weight Paint.

`VERTEX_GREASE_PENCIL` :

Grease Pencil Vertex Paint.

## Curve Fit Method Items

### Curve Fit Method Items

REFIT :

Refit.

Refit the curve step by step (high quality).

SPLIT :

Split.

Keep splitting the curve until it falls within tolerance (fast).

## Curve Normal Mode Items

### Curve Normal Mode Items

`MINIMUM_TWIST` :

Minimum Twist.

Work out normals so the twist around the curve tangent stays as small as possible over the entire curve.

`Z_UP` :

Z Up.

Work out normals at right angles to both the Z axis and the curve tangent. Where a run of points is vertical, the X axis stands in instead.

FREE :

Free.

Take the final normals straight from the stored custom normal attribute.

## Curves Handle Type Items

### Curves Handle Type Items

FREE :

Free.

This handle is free to go anywhere and leaves the point's opposite handle alone.

AUTO :

Auto.

Its position is worked out automatically to keep things smooth.

VECTOR :

Vector.

Its position is set so it aims at the neighboring control point.

ALIGN :

Align.

Its position is locked to face the reverse of the opposite handle.

## Driver Target Rotation Mode Items

### Driver Target Rotation Mode Items

AUTO :

Auto Euler.

Euler interpreted with the target's own rotation order.

XYZ :

XYZ Euler.

Euler interpreted with the XYZ rotation order.

XZY :

XZY Euler.

Euler interpreted with the XZY rotation order.

YXZ :

YXZ Euler.

Euler interpreted with the YXZ rotation order.

YZX :

YZX Euler.

Euler interpreted with the YZX rotation order.

ZXY :

ZXY Euler.

Euler interpreted with the ZXY rotation order.

ZYX :

ZYX Euler.

Euler interpreted with the ZYX rotation order.

QUATERNION :

Quaternion.

Rotation expressed as a quaternion.

`SWING_TWIST_X` :

Swing and X Twist.

Break the rotation into a swing that aims the X axis, then a twist about that axis.

`SWING_TWIST_Y` :

Swing and Y Twist.

Break the rotation into a swing that aims the Y axis, then a twist about that axis.

`SWING_TWIST_Z` :

Swing and Z Twist.

Break the rotation into a swing that aims the Z axis, then a twist about that axis.

## Dt Layers Select Dst Items

### Dt Layers Select Dst Items

ACTIVE :

Active Layer.

Apply to the active data layer on every target.

NAME :

By Name.

Pick which target data layers to affect by matching names.

INDEX :

By Order.

Pick which target data layers to affect by matching order (indices).

## Dt Layers Select Src Items

### Dt Layers Select Src Items

ACTIVE :

Active Layer.

Move over the active data layer only.

ALL :

All Layers.

Move over every data layer.

`BONE_SELECT` :

Selected Pose Bones.

Move over each vertex group tied to the selected pose bones.

`BONE_DEFORM` :

Deform Pose Bones.

Move over each vertex group tied to the deform bones.

## Dt Method Edge Items

### Dt Method Edge Items

TOPOLOGY :

Topology.

Take data from meshes whose topology matches exactly.

`VERT_NEAREST` :

Nearest Vertices.

Take from the most alike edge, the one whose vertices sit nearest the destination edge's.

NEAREST :

Nearest Edge.

Take from the nearest edge, judged by midpoints.

`POLY_NEAREST` :

Nearest Face Edge.

Take from the nearest edge on the nearest face, judged by midpoints.

`EDGEINTERP_VNORPROJ` :

Projected Edge Interpolated.

Blend across every source edge struck when the destination edge is projected along its own normal (from its vertices).

## Dt Method Loop Items

### Dt Method Loop Items

TOPOLOGY :

Topology.

Take data from meshes whose topology matches exactly.

`NEAREST_NORMAL` :

Nearest Corner and Best Matching Normal.

Take from the closest corner whose normal lines up best.

`NEAREST_POLYNOR` :

Nearest Corner and Best Matching Face Normal.

Take from the closest corner whose face normal best matches that of the destination corner's face.

`NEAREST_POLY` :

Nearest Corner of Nearest Face.

Take from the closest corner on the closest face.

`POLYINTERP_NEAREST` :

Nearest Face Interpolated.

Take from the blended corners of the closest source face.

`POLYINTERP_LNORPROJ` :

Projected Face Interpolated.

Take from the blended corners of the source face struck by projecting the corner normal.

## Dt Method Poly Items

### Dt Method Poly Items

TOPOLOGY :

Topology.

Take data from meshes whose topology matches exactly.

NEAREST :

Nearest Face.

Take from the closest face, judged by center points.

NORMAL :

Best Normal-Matching.

Take from the source face whose normal lies nearest the destination's.

`POLYINTERP_PNORPROJ` :

Projected Face Interpolated.

Blend across every source polygon crossed when the destination one is projected along its own normal.

## Dt Method Vertex Items

### Dt Method Vertex Items

TOPOLOGY :

Topology.

Take data from meshes whose topology matches exactly.

NEAREST :

Nearest Vertex.

Take from the nearest vertex.

`EDGE_NEAREST` :

Nearest Edge Vertex.

Take from the nearest vertex on the nearest edge.

`EDGEINTERP_NEAREST` :

Nearest Edge Interpolated.

Take from vertices blended at the closest point on the closest edge.

`POLY_NEAREST` :

Nearest Face Vertex.

Take from the nearest vertex on the nearest face.

`POLYINTERP_NEAREST` :

Nearest Face Interpolated.

Take from vertices blended at the closest point on the closest face.

`POLYINTERP_VNORPROJ` :

Projected Face Interpolated.

Take from vertices blended at the spot on the closest face struck by the normal projection.

## Dt Mix Mode Items

### Dt Mix Mode Items

REPLACE :

Replace.

Write over the data on every element.

`ABOVE_THRESHOLD` :

Above Threshold.

Replace destination elements only where the data sits above the given threshold (the precise rule depends on data type).

`BELOW_THRESHOLD` :

Below Threshold.

Replace destination elements only where the data sits below the given threshold (the precise rule depends on data type).

MIX :

Mix.

Blend the source value into the destination, with the threshold acting as the factor.

ADD :

Add.

Sum the source value onto the destination, with the threshold acting as the factor.

SUB :

Subtract.

Take the source value off the destination, with the threshold acting as the factor.

MUL :

Multiply.

Scale the destination by the source value, with the threshold acting as the factor.

## Event Direction Items

### Event Direction Items

ANY :

Any.

NORTH :

North.

`NORTH_EAST` :

North-East.

EAST :

East.

`SOUTH_EAST` :

South-East.

SOUTH :

South.

`SOUTH_WEST` :

South-West.

WEST :

West.

`NORTH_WEST` :

North-West.

## Event Value Items

### Event Value Items

ANY :

Any.

PRESS :

Press.

RELEASE :

Release.

CLICK :

Click.

`DOUBLE_CLICK` :

Double Click.

`CLICK_DRAG` :

Drag.

NOTHING :

Nothing.

## Fileselect Params Sort Items

### Fileselect Params Sort Items

`FILE_SORT_ALPHA` :

Name.

Order the file list alphabetically.

`FILE_SORT_EXTENSION` :

Extension.

Order the file list by extension or type.

`FILE_SORT_TIME` :

Modified Date.

Order files by when they were last modified.

`FILE_SORT_SIZE` :

Size.

Order files by their size.

`ASSET_CATALOG` :

Asset Catalog.

Group the asset list so that assets sharing a catalog stay side by side. Inside one catalog assets run by name, and the catalogs follow the flattened catalog hierarchy.

## Geometry Component Type Items

### Geometry Component Type Items

MESH :

Mesh.

The mesh component, holding point, corner, edge, and face data.

POINTCLOUD :

Point Cloud.

The point cloud component, holding point data only.

CURVE :

Curve.

The curve component, holding spline and control point data.

INSTANCES :

Instances.

Instances drawn from objects or collections.

GREASEPENCIL :

Grease Pencil.

The Grease Pencil component, holding layer and curve data.

## Grease Pencil Selectmode Items

### Grease Pencil Selectmode Items

POINT :

Point.

Restrict the selection to points alone.

STROKE :

Stroke.

Grab every point that makes up a stroke.

SEGMENT :

Segment.

Grab the run of stroke points lying between other strokes.

## Linestyle Geometry Modifier Type Items

### Linestyle Geometry Modifier Type Items

2`D_OFFSET` :

2D Offset.

2`D_TRANSFORM` :

2D Transform.

`BACKBONE_STRETCHER` :

Backbone Stretcher.

`BEZIER_CURVE` :

Bézier Curve.

BLUEPRINT :

Blueprint.

`GUIDING_LINES` :

Guiding Lines.

`PERLIN_NOISE_1D` :

Perlin Noise 1D.

`PERLIN_NOISE_2D` :

Perlin Noise 2D.

POLYGONIZATION :

Polygonization.

SAMPLING :

Sampling.

SIMPLIFICATION :

Simplification.

`SINUS_DISPLACEMENT` :

Sinus Displacement.

`SPATIAL_NOISE` :

Spatial Noise.

`TIP_REMOVER` :

Tip Remover.

## Mapping Type Items

### Mapping Type Items

POINT :

Point.

Apply the transform to a point.

TEXTURE :

Texture.

Map a texture by inverse-transforming its texture coordinate.

VECTOR :

Vector.

Apply the transform to a direction vector, ignoring Location.

NORMAL :

Normal.

Apply the transform to a unit normal vector, ignoring Location.

## Mesh Select Mode Items

### Mesh Select Mode Items

VERT :

Vertex.

Select by vertices.

EDGE :

Edge.

Select by edges.

FACE :

Face.

Select by faces.

## Mesh Select Mode Uv Items

### Mesh Select Mode Uv Items

VERTEX :

Vertex.

Select by vertices.

EDGE :

Edge.

Select by edges.

FACE :

Face.

Select by faces.

## Mesh Walk Delimit Edge Loop Items

### Mesh Walk Delimit Edge Loop Items

SEAM :

Seam.

Halt the edge-loop selection wherever a seam is met.

SHARP :

Sharp.

Halt the edge-loop selection wherever a sharp edge is met.

NGONS :

N-gons.

Stop growing the boundary selection at n-gons.

`INNER_CORNERS` :

Inner Corners.

Stop the boundary selection at any vertex joined by more than three edges.

`OUTER_CORNERS` :

Outer Corners.

Stop the boundary selection at two-edge vertices that share a face which is not an n-gon.

## Metaelem Type Items

### Metaelem Type Items

BALL :

Ball.

CAPSULE :

Capsule.

PLANE :

Plane.

ELLIPSOID :

Ellipsoid.

CUBE :

Cube.

## Modifier Shrinkwrap Mode Items

### Modifier Shrinkwrap Mode Items

`ON_SURFACE` :

On Surface.

Pins the point onto the target's surface, shifting it by the distance offset in the direction of where the point started.

INSIDE :

Inside.

Keeps the point held within the target object.

OUTSIDE :

Outside.

Keeps the point held beyond the target object.

`OUTSIDE_SURFACE` :

Outside Surface.

Pins the point to the target's surface, with the distance offset always pushing outward, either toward or away from where it began.

`ABOVE_SURFACE` :

Above Surface.

Pins the point to the target's surface, applying the distance offset precisely along the target's normal.

## Modifier Triangulate Ngon Method Items

### Modifier Triangulate Ngon Method Items

BEAUTY :

Beauty.

Lay out the resulting triangles uniformly; this is the slow option.

CLIP :

Clip.

Cut up the polygons using ear clipping.

## Modifier Triangulate Quad Method Items

### Modifier Triangulate Quad Method Items

BEAUTY :

Beauty.

Cut the quads into tidy triangles using the slower approach.

FIXED :

Fixed.

Cut each quad across its first and third vertices.

`FIXED_ALTERNATE` :

Fixed Alternate.

Cut each quad across its 2nd and 4th vertices.

`SHORTEST_DIAGONAL` :

Shortest Diagonal.

Cut each quad along whichever diagonal is shorter.

`LONGEST_DIAGONAL` :

Longest Diagonal.

Cut each quad along whichever diagonal is longer.

## Motionpath Bake Location Items

### Motionpath Bake Location Items

HEADS :

Heads.

Derive the bone paths from the bone heads.

TAILS :

Tails.

Derive the bone paths from the bone tails.

## Motionpath Display Type Items

### Motionpath Display Type Items

`CURRENT_FRAME` :

Around Frame.

Show pose paths spanning a set number of frames on either side of the current frame.

RANGE :

In Range.

Show pose paths across the range you specify.

## Navigation Mode Items

### Navigation Mode Items

WALK :

Walk.

Move through the scene interactively by walking or free-flying around.

FLY :

Fly.

Navigate the scene using fly dynamics.

## Normal Space Items

### Normal Space Items

OBJECT :

Object.

Bake the normals into object space.

TANGENT :

Tangent.

Bake the normals into tangent space.

## Normal Swizzle Items

### Normal Swizzle Items

`POS_X` :

+X.

`POS_Y` :

+Y.

`POS_Z` :

+Z.

`NEG_X` :

-X.

`NEG_Y` :

-Y.

`NEG_Z` :

-Z.

## Object Axis Items

### Object Axis Items

`POS_X` :

+X.

`POS_Y` :

+Y.

`POS_Z` :

+Z.

`NEG_X` :

-X.

`NEG_Y` :

-Y.

`NEG_Z` :

-Z.

## Object Gpencil Type Items

### Object Gpencil Type Items

EMPTY :

Blank.

Spawn an empty Grease Pencil object.

STROKE :

Stroke.

Spawn a basic stroke using simple colors.

MONKEY :

Monkey.

Build a Suzanne Grease Pencil object.

`LINEART_SCENE` :

Scene Line Art.

Rapidly configure Line Art across the whole scene.

`LINEART_COLLECTION` :

Collection Line Art.

Rapidly configure Line Art for the active collection.

`LINEART_OBJECT` :

Object Line Art.

Rapidly configure Line Art for the active object.

## Object Mode Items

### Object Mode Items

OBJECT :

Object Mode.

EDIT :

Edit Mode.

POSE :

Pose Mode.

SCULPT :

Sculpt Mode.

`VERTEX_PAINT` :

Vertex Paint.

`WEIGHT_PAINT` :

Weight Paint.

`TEXTURE_PAINT` :

Texture Paint.

`PARTICLE_EDIT` :

Particle Edit.

`EDIT_GPENCIL` :

Edit Mode.

Edit Grease Pencil Strokes.

`SCULPT_GREASE_PENCIL` :

Sculpt Mode.

Sculpt Grease Pencil Strokes.

`PAINT_GREASE_PENCIL` :

Draw Mode.

Paint Grease Pencil Strokes.

`WEIGHT_GREASE_PENCIL` :

Weight Paint.

Grease Pencil Weight Paint Strokes.

`VERTEX_GREASE_PENCIL` :

Vertex Paint.

Grease Pencil Vertex Paint Strokes.

`SCULPT_CURVES` :

Sculpt Mode.

## Object Rotation Mode Items

### Object Rotation Mode Items

QUATERNION :

Quaternion (WXYZ).

No Gimbal Lock.

XYZ :

XYZ Euler.

XYZ Rotation Order - prone to Gimbal Lock (default).

XZY :

XZY Euler.

XZY Rotation Order - prone to Gimbal Lock.

YXZ :

YXZ Euler.

YXZ Rotation Order - prone to Gimbal Lock.

YZX :

YZX Euler.

YZX Rotation Order - prone to Gimbal Lock.

ZXY :

ZXY Euler.

ZXY Rotation Order - prone to Gimbal Lock.

ZYX :

ZYX Euler.

ZYX Rotation Order - prone to Gimbal Lock.

`AXIS_ANGLE` :

Axis Angle.

Axis Angle (W+XYZ), defines a rotation around some axis defined by 3D-Vector.

## Particle Edit Disconnected Hair Brush Items

### Particle Edit Disconnected Hair Brush Items

COMB :

Comb.

Comb the hairs.

SMOOTH :

Smooth.

Smooth the hairs.

LENGTH :

Length.

Lengthen or shorten the hairs.

CUT :

Cut.

Cut the hairs.

WEIGHT :

Weight.

Set the weight on hair particles.

## Particle Edit Hair Brush Items

### Particle Edit Hair Brush Items

COMB :

Comb.

Comb the hairs.

SMOOTH :

Smooth.

Smooth the hairs.

ADD :

Add.

Add new hairs.

LENGTH :

Length.

Lengthen or shorten the hairs.

PUFF :

Puff.

Lift the hairs upright.

CUT :

Cut.

Cut the hairs.

WEIGHT :

Weight.

Set the weight on hair particles.

## Proportional Falloff Curve Only Items

### Proportional Falloff Curve Only Items

SMOOTH :

Smooth.

Smooth falloff.

SPHERE :

Sphere.

Spherical falloff.

ROOT :

Root.

Root falloff.

`INVERSE_SQUARE` :

Inverse Square.

Inverse Square falloff.

SHARP :

Sharp.

Sharp falloff.

LINEAR :

Linear.

Linear falloff.

## Proportional Falloff Items

### Proportional Falloff Items

SMOOTH :

Smooth.

Smooth falloff.

SPHERE :

Sphere.

Spherical falloff.

ROOT :

Root.

Root falloff.

`INVERSE_SQUARE` :

Inverse Square.

Inverse Square falloff.

SHARP :

Sharp.

Sharp falloff.

LINEAR :

Linear.

Linear falloff.

CONSTANT :

Constant.

Constant falloff.

RANDOM :

Random.

Random falloff.

## Region Type Items

### Region Type Items

WINDOW :

Window.

HEADER :

Header.

CHANNELS :

Channels.

TEMPORARY :

Temporary.

UI :

Sidebar.

TOOLS :

Tools.

`TOOL_PROPS` :

Tool Properties.

`ASSET_SHELF` :

Asset Shelf.

`ASSET_SHELF_HEADER` :

Asset Shelf Header.

PREVIEW :

Preview.

HUD :

Floating Region.

`NAVIGATION_BAR` :

Navigation Bar.

EXECUTE :

Execute Buttons.

FOOTER :

Footer.

`TOOL_HEADER` :

Tool Header.

XR :

XR.

## Rigidbody Constraint Type Items

### Rigidbody Constraint Type Items

FIXED :

Fixed.

Bonds rigid bodies so they stay locked together.

POINT :

Point.

Ties rigid bodies to a shared pivot they can swing about.

HINGE :

Hinge.

Limits a rigid body's spin to a single axis.

SLIDER :

Slider.

Limits a rigid body's movement to a single axis.

PISTON :

Piston.

Confines both movement and spin of a rigid body to one axis.

GENERIC :

Generic.

Limits movement and spin to whichever axes you pick.

`GENERIC_SPRING` :

Generic Spring.

Limits movement and spin to chosen axes while adding spring behavior.

MOTOR :

Motor.

Powers a rigid body to turn about or slide along an axis.

## Shrinkwrap Face Cull Items

### Shrinkwrap Face Cull Items

OFF :

Off.

Nothing is culled.

FRONT :

Front.

Skip projection where the face sits in front.

BACK :

Back.

Skip projection where the face sits behind.

## Shrinkwrap Type Items

### Shrinkwrap Type Items

`NEAREST_SURFACEPOINT` :

Nearest Surface Point.

Pull the mesh onto the closest spot on the target surface.

PROJECT :

Project.

Pull the mesh onto the closest target surface along a chosen axis.

`NEAREST_VERTEX` :

Nearest Vertex.

Pull the mesh onto the closest target vertex.

`TARGET_PROJECT` :

Target Normal Project.

Pull the mesh onto the closest target surface following the target's interpolated vertex normals.

## Snap Element Items

### Snap Element Items

INCREMENT :

Increment.

Lock onto increments.

GRID :

Grid.

Lock onto the grid.

VERTEX :

Vertex.

Lock onto vertices.

EDGE :

Edge.

Lock onto edges.

FACE :

Face.

Lock on by projecting toward faces.

VOLUME :

Volume.

Lock onto volume.

`EDGE_MIDPOINT` :

Edge Center.

Lock onto the middle of an edge.

`EDGE_PERPENDICULAR` :

Edge Perpendicular.

Lock onto the closest point along an edge.

`FACE_MIDPOINT` :

Face Center.

Lock onto the middle of a face.

`FACE_PROJECT` :

Face Project.

Lock on by projecting toward faces.

`FACE_NEAREST` :

Face Nearest.

Lock onto the closest point across faces.

## Snap Source Items

### Snap Source Items

CLOSEST :

Closest.

Place the nearest point on the target.

CENTER :

Center.

Place the transformation center on the target.

MEDIAN :

Median.

Place the median on the target.

ACTIVE :

Active.

Place the active element on the target.

## Space File Browse Mode Items

### Space File Browse Mode Items

FILES :

File Browser.

The built-in manager for opening, saving, and linking data.

ASSETS :

Asset Browser.

Handle this file's assets and reach linked asset libraries.

## Strip Color Items

### Strip Color Items

NONE :

None.

Leave the collection without a color tag.

`COLOR_01` :

Color 01.

`COLOR_02` :

Color 02.

`COLOR_03` :

Color 03.

`COLOR_04` :

Color 04.

`COLOR_05` :

Color 05.

`COLOR_06` :

Color 06.

`COLOR_07` :

Color 07.

`COLOR_08` :

Color 08.

`COLOR_09` :

Color 09.

## Strip Modifier Type Items

### Strip Modifier Type Items

`BRIGHT_CONTRAST` :

Brightness/Contrast.

`COLOR_BALANCE` :

Color Balance.

COMPOSITOR :

Compositor.

CURVES :

Curves.

`HUE_CORRECT` :

Hue Correct.

MASK :

Mask.

TONEMAP :

Tone Map.

`WHITE_BALANCE` :

White Balance.

`SOUND_EQUALIZER` :

Sound Equalizer.

PITCH :

Pitch.

ECHO :

Echo.

## Strip Video Modifier Type Items

### Strip Video Modifier Type Items

`BRIGHT_CONTRAST` :

Brightness/Contrast.

`COLOR_BALANCE` :

Color Balance.

COMPOSITOR :

Compositor.

CURVES :

Curves.

`HUE_CORRECT` :

Hue Correct.

MASK :

Mask.

TONEMAP :

Tone Map.

`WHITE_BALANCE` :

White Balance.

## Stroke Depth Order Items

### Stroke Depth Order Items

2D :

2D Layers.

Order strokes by depth using Grease Pencil layer and stroke order.

3D :

3D Location.

Order strokes by their actual position in 3D space.

## Subdivision Boundary Smooth Items

### Subdivision Boundary Smooth Items

`PRESERVE_CORNERS` :

Keep Corners.

Smooth the boundaries while leaving corners sharp.

ALL :

All.

Smooth the boundaries, corners included.

## Subdivision Uv Smooth Items

### Subdivision Uv Smooth Items

NONE :

None.

Leave UVs unsmoothed and keep boundaries sharp.

`PRESERVE_CORNERS` :

Keep Corners.

Smooth UVs but keep corners on a discontinuous boundary sharp.

`PRESERVE_CORNERS_AND_JUNCTIONS` :

Keep Corners, Junctions.

Smooth UVs while keeping sharp the corners on a discontinuous boundary and the junctions where three or more regions meet.

`PRESERVE_CORNERS_JUNCTIONS_AND_CONCAVE` :

Keep Corners, Junctions, Concave.

Smooth UVs while keeping sharp the corners on a discontinuous boundary, junctions of three or more regions, and darts and concave corners.

`PRESERVE_BOUNDARIES` :

Keep Boundaries.

Smooth UVs and keep boundaries sharp.

`SMOOTH_ALL` :

All.

Smooth both the UVs and the boundaries.

## Symmetrize Direction Items

### Symmetrize Direction Items

`NEGATIVE_X` :

-X to +X.

`POSITIVE_X` :

+X to -X.

`NEGATIVE_Y` :

-Y to +Y.

`POSITIVE_Y` :

+Y to -Y.

`NEGATIVE_Z` :

-Z to +Z.

`POSITIVE_Z` :

+Z to -Z.

## Transform Mode Type Items

### Transform Mode Type Items

INIT :

Init.

DUMMY :

Dummy.

TRANSLATION :

Translation.

ROTATION :

Rotation.

RESIZE :

Resize.

`SKIN_RESIZE` :

Skin Resize.

TOSPHERE :

To Sphere.

SHEAR :

Shear.

BEND :

Bend.

SHRINKFATTEN :

Shrink/Fatten.

TILT :

Tilt.

TRACKBALL :

Trackball.

PUSHPULL :

Push/Pull.

CREASE :

Crease.

`VERTEX_CREASE` :

Vertex Crease.

MIRROR :

Mirror.

`BONE_SIZE` :

Bone Size.

`BONE_ENVELOPE` :

Bone Envelope.

`BONE_ENVELOPE_DIST` :

Bone Envelope Distance.

`CURVE_SHRINKFATTEN` :

Curve Shrink/Fatten.

`MASK_SHRINKFATTEN` :

Mask Shrink/Fatten.

`BONE_ROLL` :

Bone Roll.

`TIME_TRANSLATE` :

Time Translate.

`TIME_SLIDE` :

Time Slide.

`TIME_SCALE` :

Time Scale.

`TIME_EXTEND` :

Time Extend.

`BAKE_TIME` :

Bake Time.

BWEIGHT :

Bevel Weight.

ALIGN :

Align.

EDGESLIDE :

Edge Slide.

SEQSLIDE :

Sequence Slide.

`GPENCIL_OPACITY` :

Grease Pencil Opacity.

## Transform Orientation Items

### Transform Orientation Items

GLOBAL :

Global.

Line the transform axes up with world space.

LOCAL :

Local.

Line the transform axes up with the selected objects' local space.

NORMAL :

Normal.

Line the transform axes up with the averaged normal of the selected elements (the bone Y axis in pose mode).

GIMBAL :

Gimbal.

Line each axis up with the Euler rotation axis used as input.

VIEW :

View.

Line the transform axes up with the window.

CURSOR :

Cursor.

Line the transform axes up with the 3D cursor.

PARENT :

Parent.

Line the transform axes up with the object's parent space.

## Transform Pivot Full Items

### Transform Pivot Full Items

`BOUNDING_BOX_CENTER` :

Bounding Box Center.

Pivot about the bounding box center of the selected object(s).

CURSOR :

3D Cursor.

Pivot about the 3D cursor.

`INDIVIDUAL_ORIGINS` :

Individual Origins.

Pivot about each object's own origin.

`MEDIAN_POINT` :

Median Point.

Pivot about the median point of the selected objects.

`ACTIVE_ELEMENT` :

Active Element.

Pivot about the active object.

## Uilist Layout Type Items

### Uilist Layout Type Items

DEFAULT :

Default Layout.

Use the standard multi-row layout.

COMPACT :

Compact Layout.

Use the tight single-row layout.

## Unpack Method Items

### Unpack Method Items

REMOVE :

Remove Pack.

`USE_LOCAL` :

Use Local File.

`WRITE_LOCAL` :

Write Local File (overwrite existing).

`USE_ORIGINAL` :

Use Original File.

`WRITE_ORIGINAL` :

Write Original File (overwrite existing).

## Views Format Items

### Views Format Items

INDIVIDUAL :

Individual.

Separate files per view, prefixed as the scene views specify.

`STEREO_3D` :

Stereo 3D.

One file holding an encoded stereo pair.

## Views Format Multilayer Items

### Views Format Multilayer Items

INDIVIDUAL :

Individual.

Separate files per view, prefixed as the scene views specify.

MULTIVIEW :

Multi-View.

One file holding every view.

## Views Format Multiview Items

### Views Format Multiview Items

INDIVIDUAL :

Individual.

Separate files per view, prefixed as the scene views specify.

`STEREO_3D` :

Stereo 3D.

One file holding an encoded stereo pair.

MULTIVIEW :

Multi-View.

One file holding every view.

## Volume Grid Data Type Items

### Volume Grid Data Type Items

BOOLEAN :

Boolean.

Boolean.

FLOAT :

Float.

Single precision float.

DOUBLE :

Double.

Double precision.

INT :

Integer.

32-bit integer.

INT64 :

Integer 64-bit.

64-bit integer.

MASK :

Mask.

No payload, just a boolean mask marking active voxels.

`VECTOR_FLOAT` :

Vector.

3D float vector.

`VECTOR_DOUBLE` :

Double Vector.

3D double vector.

`VECTOR_INT` :

Integer Vector.

3D integer vector.

POINTS :

Points (Unsupported).

A points grid, not yet handled by volume objects.

UNKNOWN :

Unknown.

A data type that isn't supported.

## Window Cursor Items

### Window Cursor Items

DEFAULT :

Default.

NONE :

None.

WAIT :

Wait.

CROSSHAIR :

Crosshair.

`MOVE_X` :

Move-X.

`MOVE_Y` :

Move-Y.

KNIFE :

Knife.

TEXT :

Text.

`PAINT_BRUSH` :

Paint Brush.

`PAINT_CROSS` :

Paint Cross.

DOT :

Dot Cursor.

ERASER :

Eraser.

HAND :

Open Hand.

`HAND_POINT` :

Pointing Hand.

`HAND_CLOSED` :

Closed Hand.

`SCROLL_X` :

Scroll-X.

`SCROLL_Y` :

Scroll-Y.

`SCROLL_XY` :

Scroll-XY.

EYEDROPPER :

Eyedropper.

`PICK_AREA` :

Pick Area.

STOP :

Stop.

COPY :

Copy.

CROSS :

Cross.

MUTE :

Mute.

`ZOOM_IN` :

Zoom In.

`ZOOM_OUT` :

Zoom Out.

## Workspace Object Mode Items

### Workspace Object Mode Items

OBJECT :

Object Mode.

EDIT :

Edit Mode.

POSE :

Pose Mode.

SCULPT :

Sculpt Mode.

`VERTEX_PAINT` :

Vertex Paint.

`WEIGHT_PAINT` :

Weight Paint.

`TEXTURE_PAINT` :

Texture Paint.

`PARTICLE_EDIT` :

Particle Edit.

`EDIT_GPENCIL` :

Grease Pencil Edit Mode.

Edit Grease Pencil Strokes.

`SCULPT_GREASE_PENCIL` :

Grease Pencil Sculpt Mode.

Sculpt Grease Pencil Strokes.

`PAINT_GREASE_PENCIL` :

Grease Pencil Draw.

Paint Grease Pencil Strokes.

`VERTEX_GREASE_PENCIL` :

Grease Pencil Vertex Paint.

Grease Pencil Vertex Paint Strokes.

`WEIGHT_GREASE_PENCIL` :

Grease Pencil Weight Paint.

Grease Pencil Weight Paint Strokes.

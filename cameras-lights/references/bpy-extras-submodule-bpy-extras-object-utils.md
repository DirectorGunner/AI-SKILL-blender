# Bpy Extras Submodule Bpy Extras Object Utils, Constraint Type Items, Fmodifier Type Items, Light Type Items ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: bpy_extras submodule (bpy_extras.object_utils); Constraint Type Items; Fmodifier Type Items; Light Type Items; Object Type Items; Preference Section Items; Property Subtype Items; Property Subtype Number Items; Property Unit Items; Ramp Blend Items; Wm Job Type Items; GPU Platform Utilities (gpu.platform); Python Threads are Not Supported.

## bpy_extras submodule (bpy_extras.object_utils)

### bpy_extras submodule (bpy_extras.object_utils) 

bpy_extras.object_utils. add_object_align_init ( context , operator ) 

Build a matrix from the operator settings together with the view context.

Parameters :

- context (bpy.types.Context) – The context to use.

- operator (bpy.types.Operator | None) – The operator, checked for location and rotation properties.

Returns :

the matrix from the context and settings.

Return type :

mathutils.Matrix

bpy_extras.object_utils. object_data_add ( context , obdata , operator = None , name = None ) 

Create an object, using the view context and preferences to set its initial
location, rotation and layer.

Parameters :

- context (bpy.types.Context) – The context to use.

- obdata (bpy.types.ID | None) – Valid object data to be used for the new object or None.

- operator (bpy.types.Operator | None) – The operator, checked for location and rotation properties.

- name ( str | None ) – Optional name

Returns :

the newly created object in the scene.

Return type :

bpy.types.Object

bpy_extras.object_utils. object_add_grid_scale ( context ) 

Give back the scale that object data should take on
so it lines up with the grid scale.

Parameters :

context (bpy.types.Context) – The context.

Returns :

The grid scale.

Return type :

float

bpy_extras.object_utils. object_add_grid_scale_apply_operator ( operator , context ) 

Multiply an operator's distance values by the grid size.

Parameters :

- operator (bpy.types.Operator) – The operator to scale.

- context (bpy.types.Context) – The context.

bpy_extras.object_utils. world_to_camera_view ( scene , obj , coord ) 

Give back the camera-space coordinates of a 3d point
(these are also called normalized device coordinates - NDC).

Here (0, 0) marks the bottom left and (1, 1)
the top right of the camera frame;
values beyond the 0-1 range are allowed too.
When 'z' is negative the point sits behind the camera.

Shift-x/y, the lens angle and the sensor size are all accounted for,
as are perspective and ortho projections.

Parameters :

- scene (bpy.types.Scene) – Scene to use for frame size.

- obj (bpy.types.Object) – Camera object.

- coord (mathutils.Vector) – World space location.

Returns :

a vector where X and Y map to the view plane and
Z is the depth on the view axis.

Return type :

mathutils.Vector

bpy_extras.object_utils. object_report_if_active_shape_key_is_locked ( obj , operator ) 

Tests whether the given object's active shape key is locked and reports an error when it is.

When the object carries no shape keys there is nothing to lock, so the function returns False.

Parameters :

- obj (bpy.types.Object) – Object to check.

- operator (bpy.types.Operator | None) – Currently running operator to report the error through. Use None to suppress emitting the message.

Returns :

True if the shape key was locked.

Return type :

bool

class bpy_extras.object_utils. AddObjectHelper 

align_update_callback ( _context ) 

Update callback for the align property; it clears rotation when world alignment is chosen.

classmethod poll ( context ) 

Confirm the scene isn't linked in from a library.

Parameters :

context (bpy.types.Context) – The context.

Returns :

True when the scene is local (not linked from a library).

Return type :

bool

## Constraint Type Items

### Constraint Type Items

Motion Tracking

`CAMERA_SOLVER` :

Camera Solver.

`FOLLOW_TRACK` :

Follow Track.

`OBJECT_SOLVER` :

Object Solver.

Transform

`COPY_LOCATION` :

Copy Location.

Make the owner share the target's location, optionally offset, so the two travel as one.

`COPY_ROTATION` :

Copy Rotation.

Make the owner share the target's rotation, optionally offset, so the two turn together.

`COPY_SCALE` :

Copy Scale.

Make the owner share the target's scale factors, optionally offset, so both end up scaled alike.

`COPY_TRANSFORMS` :

Copy Transforms.

Adopt every transformation of the target so the two move as one.

`LIMIT_DISTANCE` :

Limit Distance.

Keep motion bounded to a set distance from a target, checked only when the constraint is evaluated.

`LIMIT_LOCATION` :

Limit Location.

Clamp movement on each axis to the ranges you specify.

`LIMIT_ROTATION` :

Limit Rotation.

Clamp rotation on each axis to the ranges you specify.

`LIMIT_SCALE` :

Limit Scale.

Clamp scaling on each axis to the ranges you specify.

`MAINTAIN_VOLUME` :

Maintain Volume.

Offset scaling on one axis by scaling the remaining two axes to keep volume constant.

TRANSFORM :

Transformation.

Drive one property on the owner from a transform property read off the target (or itself).

`TRANSFORM_CACHE` :

Transform Cache.

Read the transformation matrix in from an external file.

Tracking

`CLAMP_TO` :

Clamp To.

Pin motion onto a curve by mapping location along the curve's longest axis.

`DAMPED_TRACK` :

Damped Track.

Aim at a target using the least rotation that gets there.

IK :

Inverse Kinematics.

Drive a chain of bones from a chosen endpoint target (bones only).

`LOCKED_TRACK` :

Locked Track.

Spin about a fixed ('locked') axis to face a target.

`SPLINE_IK` :

Spline IK.

Lay a chain of bones out along a curve (bones only).

`STRETCH_TO` :

Stretch To.

Extend along the Y axis to reach toward a target.

`TRACK_TO` :

Track To.

An older tracking constraint that tends to introduce twisting artifacts.

Relationship

ACTION :

Action.

Pull a pose for the owner from an Action, keyed off a transform property of the target.

ARMATURE :

Armature.

Blend weighted transforms from several bones, much like the Armature modifier does.

`CHILD_OF` :

Child Of.

Treat the target as a 'detachable' parent of the owner.

FLOOR :

Floor.

Turn the target's position (and optionally rotation) into a 'wall' or 'floor' the owner is blocked from passing.

`FOLLOW_PATH` :

Follow Path.

Drive an object or bone so it travels along a path.

`GEOMETRY_ATTRIBUTE` :

Geometry Attribute.

Read a transform out of an attribute stored on the target geometry.

PIVOT :

Pivot.

Shift the pivot point used for transforms (buggy).

SHRINKWRAP :

Shrinkwrap.

Keep motion clinging to the surface of the target mesh.

## Fmodifier Type Items

### Fmodifier Type Items

NULL :

Invalid.

GENERATOR :

Generator.

Build a curve from a factorized or expanded polynomial.

FNGENERATOR :

Built-In Function.

Build a curve from common math functions like sin and cos.

ENVELOPE :

Envelope.

Rework F-Curve values, for instance to scale the size of movements.

CYCLES :

Cycles.

Loop or repeat the keyframe sequence cyclically.

NOISE :

Noise.

Layer pseudo-random noise over the F-Curves.

LIMITS :

Limits.

Cap the highest and lowest values an F-Curve can reach.

STEPPED :

Stepped Interpolation.

Snap values onto the nearest grid step, handy for a stop-motion feel.

SMOOTH :

Smooth (Gaussian).

Smooth the curve with Gaussian smoothing.

## Light Type Items

### Light Type Items

POINT :

Point.

A light that radiates equally in every direction from a single point.

SUN :

Sun.

A light whose rays all travel in one fixed, parallel direction.

SPOT :

Spot.

A light that casts a directional cone.

AREA :

Area.

A directional light emitted from a surface.

## Object Type Items

### Object Type Items

MESH :

Mesh.

CURVE :

Curve.

SURFACE :

Surface.

META :

Metaball.

FONT :

Text.

CURVES :

Hair Curves.

POINTCLOUD :

Point Cloud.

VOLUME :

Volume.

GREASEPENCIL :

Grease Pencil.

ARMATURE :

Armature.

LATTICE :

Lattice.

EMPTY :

Empty.

LIGHT :

Light.

`LIGHT_PROBE` :

Light Probe.

CAMERA :

Camera.

SPEAKER :

Speaker.

## Preference Section Items

### Preference Section Items

INTERFACE :

Interface.

VIEWPORT :

Viewport.

LIGHTS :

Lights.

EDITING :

Editing.

ANIMATION :

Animation.

EXTENSIONS :

Get Extensions.

Search for, install, and handle extensions drawn from remote and local repositories.

ADDONS :

Add-ons.

Handle the add-ons that came in through Extensions.

THEMES :

Themes.

Tweak and store themes that arrived via Extensions.

INPUT :

Input.

NAVIGATION :

Navigation.

KEYMAP :

Keymap.

SYSTEM :

System.

`SAVE_LOAD` :

Save & Load.

`FILE_PATHS` :

File Paths.

`DEVELOPER_TOOLS` :

Developer Tools.

EXPERIMENTAL :

Experimental.

## Property Subtype Items

### Property Subtype Items

NONE :

None.

`FILE_PATH` :

File Path.

`DIR_PATH` :

Directory Path.

`FILE_NAME` :

File Name.

`BYTE_STRING` :

Byte String.

PASSWORD :

Password.

A string shown masked (’********’).

PIXEL :

Pixel.

A distance on screen.

`PIXEL_DIAMETER` :

Pixel.

An on-screen distance, taken to mean a diameter.

UNSIGNED :

Unsigned.

PERCENTAGE :

Percentage.

A percentage between 0 and 100.

FACTOR :

Factor.

A factor between 0.0 and 1.0.

MASS :

Mass.

A mass derived from the scene's unit settings.

ANGLE :

Angle.

A rotation given in radians.

TIME :

Time (Scene Relative).

A time given in frames, turned into seconds using the scene's frame rate.

`TIME_ABSOLUTE` :

Time (Absolute).

A time given in seconds, with no dependence on the scene.

DISTANCE :

Distance.

A distance between two points.

`DISTANCE_DIAMETER` :

Distance.

A span between two points, taken to mean a diameter.

`DISTANCE_CAMERA` :

Camera Distance.

POWER :

Power.

TEMPERATURE :

Temperature.

WAVELENGTH :

Wavelength.

`COLOR_TEMPERATURE` :

Color Temperature.

FREQUENCY :

Frequency.

COLOR :

Linear Color.

A color in the scene's linear working color space.

TRANSLATION :

Translation.

DIRECTION :

Direction.

VELOCITY :

Velocity.

ACCELERATION :

Acceleration.

MATRIX :

Matrix.

EULER :

Euler Angles.

Euler rotation angles given in radians.

QUATERNION :

Quaternion.

A quaternion rotation (it influences NLA blending).

AXISANGLE :

Axis-Angle.

An axis paired with the angle to spin about it.

XYZ :

XYZ.

`XYZ_LENGTH` :

XYZ Length.

`COLOR_GAMMA` :

sRGB Color.

A color in sRGB space (chiefly for UI colors).

COORDINATES :

Coordinates.

LAYER :

Layer.

`LAYER_MEMBER` :

Layer Member.

## Property Subtype Number Items

### Property Subtype Number Items

PIXEL :

Pixel.

A distance on screen.

`PIXEL_DIAMETER` :

Pixel.

An on-screen distance, taken to mean a diameter.

UNSIGNED :

Unsigned.

PERCENTAGE :

Percentage.

A percentage between 0 and 100.

FACTOR :

Factor.

A factor between 0.0 and 1.0.

MASS :

Mass.

A mass derived from the scene's unit settings.

ANGLE :

Angle.

A rotation given in radians.

TIME :

Time (Scene Relative).

A time given in frames, turned into seconds using the scene's frame rate.

`TIME_ABSOLUTE` :

Time (Absolute).

A time given in seconds, with no dependence on the scene.

DISTANCE :

Distance.

A distance between two points.

`DISTANCE_DIAMETER` :

Distance.

A span between two points, taken to mean a diameter.

`DISTANCE_CAMERA` :

Camera Distance.

POWER :

Power.

TEMPERATURE :

Temperature.

WAVELENGTH :

Wavelength.

`COLOR_TEMPERATURE` :

Color Temperature.

FREQUENCY :

Frequency.

NONE :

None.

## Property Unit Items

### Property Unit Items

NONE :

None.

LENGTH :

Length.

AREA :

Area.

VOLUME :

Volume.

ROTATION :

Rotation.

TIME :

Time (Scene Relative).

`TIME_ABSOLUTE` :

Time (Absolute).

VELOCITY :

Velocity.

ACCELERATION :

Acceleration.

MASS :

Mass.

CAMERA :

Camera.

POWER :

Power.

TEMPERATURE :

Temperature.

WAVELENGTH :

Wavelength.

`COLOR_TEMPERATURE` :

Color Temperature.

FREQUENCY :

Frequency.

## Ramp Blend Items

### Ramp Blend Items

MIX :

Mix.

DARKEN :

Darken.

MULTIPLY :

Multiply.

BURN :

Color Burn.

LIGHTEN :

Lighten.

SCREEN :

Screen.

DODGE :

Color Dodge.

ADD :

Add.

OVERLAY :

Overlay.

`SOFT_LIGHT` :

Soft Light.

`LINEAR_LIGHT` :

Linear Light.

DIFFERENCE :

Difference.

EXCLUSION :

Exclusion.

SUBTRACT :

Subtract.

DIVIDE :

Divide.

HUE :

Hue.

SATURATION :

Saturation.

COLOR :

Color.

VALUE :

Value.

## Wm Job Type Items

### Wm Job Type Items

RENDER :

Regular rendering.

`RENDER_PREVIEW` :

Rendering previews.

`OBJECT_BAKE` :

Object Baking.

COMPOSITE :

Compositing.

`SHADER_COMPILATION` :

Shader compilation.

## GPU Platform Utilities (gpu.platform)

### GPU Platform Utilities (gpu.platform)

This module exposes the GPU Platform definitions.

gpu.platform. backend_type_get ( )

Fetch the GPU backend that is currently active.

Returns :

Backend type (‘OPENGL’, ‘VULKAN’, ‘METAL’, ‘NONE’, ‘UNKNOWN’).

Return type :

str

gpu.platform. device_type_get ( )

Fetch the category of GPU device in use.

Returns :

Device type (‘APPLE’, ‘NVIDIA’, ‘AMD’, ‘INTEL’, ‘SOFTWARE’, ‘QUALCOMM’, ‘UNKNOWN’).

Return type :

str

gpu.platform. renderer_get ( )

Fetch the GPU that will handle rendering.

Returns :

GPU name.

Return type :

str

gpu.platform. vendor_get ( )

Fetch the GPU vendor.

Returns :

Vendor name.

Return type :

str

gpu.platform. version_get ( )

Fetch the GPU driver version.

Returns :

Driver version.

Return type :

str

## Python Threads are Not Supported

### Python Threads are Not Supported

The short version: Python threads make Blender crash in ways that are hard to diagnose. A crash might surface while Cycles is rendering, while Python drivers run, or while a background thread is busy fetching some file.

Thread safety for the way Python is wired into Blender has had no work done on it so far, and until that's properly sorted out the safest course is to steer clear of threads entirely.

Bear in mind, too, that parts of the standard library rely on threads internally — the multiprocessing.Queue class being a case in point.

Python threading works correctly with Blender only when the threads wrap up before the script does — for instance by calling threading.Thread.join() . Put differently, they're usable only while the main Blender thread is held from running.

### Alternative Approaches

To run Python code independently of Blender, the recommended tool is the multiprocessing module.

### Code Examples

Here's a threading example that Blender supports:

`\text
import threading
import requests

urls = [
"
"
"
]

def download(url: str) -> None:
name = threading.current_thread().name
print("{}: Starting".format(name))
response = requests.get(url)
print("{}: Request status code {}".format(name, response.status_code))

threads = [
threading.Thread(
name="thread-{}".format(index),
target=download,
args=(url,),
)
for index, url in enumerate(urls)
]

print("Starting threads...")
for t in threads:
t.start()

### NOTE: While threads are running, no code (including the main thread)
### may use bpy or any Blender API - only standard Python or third-party modules.
print("Waiting for threads to finish...")
for t in threads:
t.join()

### It's now safe to use bpy again since all threads have finished.
print("Threads all done, now Blender can continue")
`

And here's a case that isn't supported, a timer that fires many times each second:

`\text
from threading import Timer

def my_timer():
t = Timer(0.1, my_timer)
t.daemon = True
t.start()
print("Running...")

my_timer()
`

Patterns like that one, which leave a thread alive after the script ends, may appear to hold up for a while, but they wind up triggering random crashes or errors inside Blender's own drawing code.

# Introduction (part 2)

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

### Introduction 

Audio can be exported through the Render Menu.

### Options 

Relative Path
Enable file path relative to the .blend file.

Accuracy
Sample precision level, important when recording animation (lower values increase accuracy).

Container
See here.

Channels
The count of audio output "locations" to encode. Each channel can be rendered separately by activating Split Channels (see below).

Mono :

A single audio channel.

Stereo :

Two audio channels; usually left and right.

Stereo LFE :

Two channels plus a low-frequency effects track below 120 Hz.

4 Channels :

Four output channels.

5.1 Surround :

Five channels with one LFE.

6.1 Surround :

Six channels with one LFE.

7.1 Surround :

Seven channels with one LFE.

Format
Several audio containers offer codec selection. For details, see here.

Sample Rate
Audio sampling frequency setting.

Split Channels
Each channel is rendered into its own file.

See also

- Scene Audio settings.

- Audio Output settings.

- Audio Preferences.

### Introduction 

Multi-view encompasses a comprehensive framework for stereoscopic rendering in Blender. Compatibility extends to both EEVEE and Cycles render engines. Cycles additionally provides stereoscopic panoramic camera support. Many stereo 3D visualization approaches are available.

Note

If you possess a compatible 3D display, modify the display mode via the Window menu using the Stereo 3D operator. Note that certain modes demand full-screen operation and can be demanding on processing power.

### Introduction 

Transformations cover several operations that modify
an active Object or Mesh, altering its position or traits.

Every object can shift, spin, and resize in Object Mode.
However, these operations don't affect every object type identically.
For instance, resizing a camera doesn't change render output dimensions.

Core transformations include:

- Move

- Rotate

- Scale

These comprise the fundamental operations. More specialized transformations exist
in the Advanced Transformations portion.

To adjust the structure of editable shapes, go to Edit Mode.

When you establish a basic shape, you stay in Object Mode.
You can alternate between Object and Edit Modes by pressing Tab.
The object's edges should now be orange.
This signals the object is now chosen and in focus.

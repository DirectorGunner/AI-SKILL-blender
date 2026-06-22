# Explodemodifier Modifier, Ffmpegsettings Bpy Struct

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: ExplodeModifier(Modifier); FFmpegSettings(bpy_struct).

## ExplodeModifier(Modifier)

### ExplodeModifier(Modifier)

base classes — bpy_struct, Modifier

class bpy.types. ExplodeModifier ( Modifier )

A modifier that drives an explosion effect off a particle system.

invert_vertex_group

Flip the influence of the vertex group (default False)

Type :

bool

particle_uv

Which UV map gets altered as particles age (default “”, never None)

Type :

str

protect

Keep vertex-group edges clean (in [0, 1], default 0.0)

Type :

float

show_alive

Display the mesh for living particles (default True)

Type :

bool

show_dead

Display the mesh for dead particles (default True)

Type :

bool

show_unborn

Display the mesh for not-yet-born particles (default True)

Type :

bool

use_edge_cut

Split face edges so the shrapnel looks cleaner (default False)

Type :

bool

use_size

Scale shrapnel by particle size (default False)

Type :

bool

vertex_group

(default “”, never None)

Type :

str

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## FFmpegSettings(bpy_struct)

### FFmpegSettings(bpy_struct)

base class — bpy_struct

class bpy.types. FFmpegSettings ( bpy_struct )

The scene's settings that pertain to FFmpeg.

audio_bitrate

Bitrate of the audio in kb/s (in [32, 2048], default 192)

Type :

int

audio_channels

Number of audio channels (default 'STEREO' )

- MONO
Mono – Output a single audio channel.

- STEREO
Stereo – Output two audio channels.

- SURROUND4
4 Channels – Output four audio channels.

- SURROUND51
5.1 Surround – Output 5.1 surround-sound channels.

- SURROUND71
7.1 Surround – Output 7.1 surround-sound channels.

Type :

Literal[‘MONO’, ‘STEREO’, ‘SURROUND4’, ‘SURROUND51’, ‘SURROUND71’]

audio_codec

Which FFmpeg audio codec is used (default 'NONE' )

- NONE
No Audio – Turn off audio, for renders that contain video alone.

- AAC
AAC.

- AC3
AC3.

- FLAC
FLAC.

- MP2
MP2.

- MP3
MP3.

- OPUS
Opus.

- PCM
PCM.

- VORBIS
Vorbis.

Type :

Literal[‘NONE’, ‘AAC’, ‘AC3’, ‘FLAC’, ‘MP2’, ‘MP3’, ‘OPUS’, ‘PCM’, ‘VORBIS’]

audio_mixrate

Sample rate of the audio in samples/s (in [8000, 192000], default 48000)

Type :

int

audio_volume

Loudness of the audio (in [0, 1], default 1.0)

Type :

float

buffersize

Rate control: buffer size (kb) (in [0, 2000], default 0)

Type :

int

codec

Which FFmpeg codec is used to encode the video (default 'H264' )

- NONE
No Video – Turn off video, for renders that contain audio alone.

- AV1
AV1.

- H264
H.264.

- H265
H.265 / HEVC.

- WEBM
WebM / VP9.

- DNXHD
DNxHD.

- DV
DV.

- FFV1
FFmpeg video codec #1.

- FLASH
Flash Video.

- HUFFYUV
HuffYUV.

- MPEG1
MPEG-1.

- MPEG2
MPEG-2.

- MPEG4
MPEG-4 (divx).

- PNG
PNG.

- PRORES
ProRes.

- QTRLE
QuickTime Animation.

- THEORA
Theora.

Type :

Literal[‘NONE’, ‘AV1’, ‘H264’, ‘H265’, ‘WEBM’, ‘DNXHD’, ‘DV’, ‘FFV1’, ‘FLASH’, ‘HUFFYUV’, ‘MPEG1’, ‘MPEG2’, ‘MPEG4’, ‘PNG’, ‘PRORES’, ‘QTRLE’, ‘THEORA’]

constant_rate_factor

Constant Rate Factor (CRF); balances video quality against file size (default 'MEDIUM' )

- NONE
Constant Bitrate – Target a fixed bit rate instead of a fixed output quality.

- LOSSLESS
Lossless.

- `PERC_LOSSLESS`
Perceptually Lossless.

- HIGH
High Quality.

- MEDIUM
Medium Quality.

- LOW
Low Quality.

- VERYLOW
Very Low Quality.

- LOWEST
Lowest Quality.

- CUSTOM
Custom Quality – Pick your own Constant Rate Factor (CRF)..

Type :

Literal[‘NONE’, ‘LOSSLESS’, ‘`PERC_LOSSLESS`’, ‘HIGH’, ‘MEDIUM’, ‘LOW’, ‘VERYLOW’, ‘LOWEST’, ‘CUSTOM’]

custom_constant_rate_factor

Lower Constant Rate Factor (CRF) values yield higher quality at the cost of bigger files. Which CRF values are permitted depends on the codec. (in [0, 63], default 23)

Type :

int

ffmpeg_preset

Balance between how fast it encodes and how well it compresses (default 'GOOD' )

- BEST
Slowest – Best pick when you have plenty of time and want top compression efficiency.

- GOOD
Good – The default, suited to most uses.

- REALTIME
Realtime – Best pick when encoding speed matters most.

Type :

Literal[‘BEST’, ‘GOOD’, ‘REALTIME’]

ffmpeg_prores_profile

ProRes Profile (default '422_STD' )

Type :

Literal[‘422_PROXY’, ‘422_LT’, ‘422_STD’, ‘422_HQ’, ‘4444’, ‘4444_XQ’]

format

Container for the output file (default 'MKV' )

Type :

Literal[‘MPEG4’, ‘MKV’, ‘WEBM’, ‘AVI’, ‘DV’, ‘FLASH’, ‘MPEG1’, ‘MPEG2’, ‘OGG’, ‘QUICKTIME’]

gopsize

Spacing of key frames, the so-called GOP size; affects both file size and seekability (in [0, 500], default 25)

Type :

int

max_b_frames

Most B-frames allowed between non-B-frames; affects both file size and seekability (in [0, 16], default 0)

Type :

int

maxrate

Rate control: max rate (kbit/s) (in [-inf, inf], default 0)

Type :

int

minrate

Rate control: min rate (kbit/s) (in [-inf, inf], default 0)

Type :

int

muxrate

Mux rate (bits/second) (in [0, inf], default 0)

Type :

int

packetsize

Mux packet size (byte) (in [0, 16384], default 0)

Type :

int

use_autosplit

Split the output automatically once it reaches 2GB (default False)

Type :

bool

use_lossless_output

Encode video streams without loss (default False)

Type :

bool

use_max_b_frames

Impose a cap on the number of B-frames (default False)

Type :

bool

video_bitrate

Bitrate of the video in kbit/s (in [-inf, inf], default 0)

Type :

int

classmethod bl_rna_get_subclass ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / )

Parameters :

- id ( str ) – The RNA type identifier.

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| RenderSettings.ffmpeg | |

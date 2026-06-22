# Audio System Aud (part 1)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

### Audio System (aud)

Audaspace (pronounced "outer space") is a high-level audio processing library.

### Basic Sound Playback

This example demonstrates Device, Sound, and Handle usage.

```
import aud

device = aud.Device()
# Load sound file (works with video containing audio).
sound = aud.Sound('music.ogg')

# Play audio; returns a handle for controlling playback.
handle = device.play(sound)
# For recurring sounds, buffering reduces processing.
sound_buffered = aud.Sound.cache(sound)
handle_buffered = device.play(sound_buffered)

# Stop playback (otherwise audio runs to completion).
handle.stop()
handle_buffered.stop()
```

aud.`AP_LOCATION`

Constant value 3

aud.`AP_ORIENTATION`

Constant value 4

aud.`AP_PANNING`

Constant value 1

aud.`AP_PITCH`

Constant value 2

aud.`AP_PITCH_SCALE`

Constant value 6

aud.`AP_TIME_STRETCH`

Constant value 5

aud.`AP_VOLUME`

Constant value 0

aud.`CHANNELS_INVALID`

Constant value 0

aud.`CHANNELS_MONO`

Constant value 1

aud.`CHANNELS_STEREO`

Constant value 2

aud.`CHANNELS_STEREO_LFE`

Constant value 3

aud.`CHANNELS_SURROUND4`

Constant value 4

aud.`CHANNELS_SURROUND5`

Constant value 5

aud.`CHANNELS_SURROUND51`

Constant value 6

aud.`CHANNELS_SURROUND61`

Constant value 7

aud.`CHANNELS_SURROUND71`

Constant value 8

aud.`CODEC_AAC`

Constant value 1

aud.`CODEC_AC3`

Constant value 2

aud.`CODEC_FLAC`

Constant value 3

aud.`CODEC_INVALID`

Constant value 0

aud.`CODEC_MP2`

Constant value 4

aud.`CODEC_MP3`

Constant value 5

aud.`CODEC_OPUS`

Constant value 8

aud.`CODEC_PCM`

Constant value 6

aud.`CODEC_VORBIS`

Constant value 7

aud.`CONTAINER_AAC`

Constant value 8

aud.`CONTAINER_AC3`

Constant value 1

aud.`CONTAINER_FLAC`

Constant value 2

aud.`CONTAINER_INVALID`

Constant value 0

aud.`CONTAINER_MATROSKA`

Constant value 3

aud.`CONTAINER_MP2`

Constant value 4

aud.`CONTAINER_MP3`

Constant value 5

aud.`CONTAINER_OGG`

Constant value 6

aud.`CONTAINER_WAV`

Constant value 7

aud.`DISTANCE_MODEL_EXPONENT`

Constant value 5

aud.`DISTANCE_MODEL_EXPONENT_CLAMPED`

Constant value 6

aud.`DISTANCE_MODEL_INVALID`

Constant value 0

aud.`DISTANCE_MODEL_INVERSE`

Constant value 1

aud.`DISTANCE_MODEL_INVERSE_CLAMPED`

Constant value 2

aud.`DISTANCE_MODEL_LINEAR`

Constant value 3

aud.`DISTANCE_MODEL_LINEAR_CLAMPED`

Constant value 4

aud.`FORMAT_FLOAT32`

Constant value 36

aud.`FORMAT_FLOAT64`

Constant value 40

aud.`FORMAT_INVALID`

Constant value 0

aud.`FORMAT_S16`

Constant value 18

aud.`FORMAT_S24`

Constant value 19

aud.`FORMAT_S32`

Constant value 20

aud.`FORMAT_U8`

Constant value 1

aud.`RATE_11025`

Constant value 11025

aud.`RATE_16000`

Constant value 16000

aud.`RATE_192000`

Constant value 192000

aud.`RATE_22050`

Constant value 22050

aud.`RATE_32000`

Constant value 32000

aud.`RATE_44100`

Constant value 44100

aud.`RATE_48000`

Constant value 48000

aud.`RATE_8000`

Constant value 8000

aud.`RATE_88200`

Constant value 88200

aud.`RATE_96000`

Constant value 96000

aud.`RATE_INVALID`

Constant value 0

aud.`STATUS_INVALID`

Constant value 0

aud.`STATUS_PAUSED`

Constant value 2

aud.`STATUS_PLAYING`

Constant value 1

aud.`STATUS_STOPPED`

Constant value 3

aud.`STRETCHER_QUALITY_CONSISTENT`

Constant value 2

aud.`STRETCHER_QUALITY_FAST`

Constant value 1

aud.`STRETCHER_QUALITY_HIGH`

Constant value 0

class aud.AnimateableProperty

An AnimateableProperty stores float value arrays for animating sound parameters (such as pan, volume, pitch scale).

read(position)

Retrieves the property value at the specified position.

Parameters:

position (float) – The animation position in frames.

Returns:

A numpy array of property values.

Return type:

numpy.ndarray

readSingle(position)

Retrieves the property value at the specified position, if there is one value.

Parameters:

position (float) – The animation position in frames.

Returns:

The value at that position.

Return type:

float

write(data [, position])

Sets the property value. With position, the property becomes animated and values are written from that position onward.

Parameters:

- data (numpy.ndarray) – numpy array of float32 values.

- position (int) – The starting position in frames.

writeConstantRange(data, position_start, position_end)

Populates a span of frames with a single unchanging value and designates it animated.

Parameters:

- data (numpy.ndarray) – A numpy array holding float values for the constant.

- position_start (int) – Frame index marking the beginning.

- position_end (int) – Frame index marking the conclusion.

animated

Whether the property is animated.

count

The quantity of floats per property.

class aud.Device

Device objects represent audio output backends (OpenAL, SDL) and also file or memory output.

lock()

Locks the device, stopping sample reading from streams until unlock() is invoked. Useful for synchronizing sound start/stop/pause/resume operations.

Note

Unlock must match each lock call for playback to continue.

Warning

Keep the lock duration brief to avoid audio dropouts.

play(sound, keep=False)

Initiates sound playback.

Parameters:

- sound (Sound) – The sound to begin.

- keep (bool) – See Handle.keep.

Returns:

The playback handle for controlling playback.

Return type:

Handle

stopAll()

Halts all playing and paused sounds.

unlock()

Unlocks after lock(), see lock() details.

channels

The audio channel count of the device.

distance_model

The device's distance model.

See also

OpenAL Documentation

doppler_factor

The doppler scale factor. A value over 1 exaggerates the effect by increasing velocity scaling.

format

The device's native sample format.

listener_location

The listener's position in 3D, a 3D float tuple.

listener_orientation

The listener's orientation in 3D as quaternion, a 4-float tuple.

listener_velocity

The listener's velocity in 3D, a 3D float tuple.

rate

The device's sampling frequency in Hz.

speed_of_sound

The device's speed-of-sound value. Standard air speed is around 343.3 m/s.

volume

The device's overall audio level.

### Audio System (aud) continued: Device properties and DynamicMusic class

class aud.DynamicMusic

DynamicMusic handles music playback tied to scene context, managing transitions automatically with customizable options. Default is crossfade, default scene is silent with id 0.

addScene(scene)

Adds a music scene.

Parameters:

scene (Sound) – The music sound.

Returns:

The new scene identifier.

Return type:

int

addTransition(ini, end, transition)

Adds a transition between scenes.

Parameters:

- ini (int) – The starting scene for the transition.

- end (int) – The ending scene for the transition.

- transition (Sound) – The transition sound.

Returns:

false if ini or end don't exist, true otherwise.

Return type:

bool

pause()

Pauses the music scene.

Returns:

Success status.

Return type:

bool

resume()

Resumes music playback.

Returns:

Success status.

Return type:

bool

stop()

Stops the music scene.

Returns:

Success status.

Return type:

bool

fadeTime

Crossfade length in seconds.

position

Music playback position in seconds.

scene

The active music scene.

status

Music playback state: playing, paused, or stopped (invalid).

volume

Music loudness.

class aud.HRTF

An HRTF set represents head-related transfer function impulse responses for binaural audio.

loadLeftHrtfSet(extension, directory)

Loads HRTF data from a directory.

Parameters:

- extension (string) – File type of the HRTF files.

- directory – Path containing the HRTF files.

Returns:

The loaded HRTF object.

Return type:

HRTF

loadRightHrtfSet(extension, directory)

Loads HRTF data from a directory.

Parameters:

- extension (string) – File type of the HRTF files.

- directory – Path containing the HRTF files.

Returns:

The loaded HRTF object.

Return type:

HRTF

addImpulseResponseFromSound(sound, azimuth, elevation)

Adds an HRTF impulse response to the HRTF object.

Parameters:

- sound (Sound) – The audio file holding the HRTF.

- azimuth (float) – The azimuth angle of the HRTF.

- elevation (float) – The elevation angle of the HRTF.

Returns:

Success status.

Return type:

bool

class aud.Handle

Handle objects manage playback for a sound. Multiple Handle instances exist for sounds playing multiple times.

pause()

Pauses playback.

Returns:

Success status.

Return type:

bool

resume()

Resumes playback.

Returns:

Success status.

Return type:

bool

stop()

Stops playback.

Returns:

Success status.

Return type:

bool

Note

This invalidates the handle.

attenuation

Distance-based volume reduction scaling.

See also

Device.distance_model

cone_angle_inner

Inner cone opening angle. If cone values exist, two audible cones originate at the source location, pointing in the source direction. Within the inner cone, volume is unaffected. Outside the outer cone, volume reaches cone_volume_outer; between them, volume interpolates linearly.

cone_angle_outer

Outer cone opening angle.

See also

cone_angle_inner

cone_volume_outer

Volume beyond the outer cone.

See also

cone_angle_inner

distance_maximum

Maximum listener distance from the source. Beyond this, volume is zero.

See also

Device.distance_model

distance_reference

Reference distance for volume calculation. At this distance, volume equals the volume property.

See also

Device.distance_model

keep

Whether a sound pauses at the end rather than stopping, enabling later resume. Useful for seeking and restarting.

Warning

Set to true and forgotten = memory leak, as the handle persists until device destruction.

location

Source position in 3D, a 3D float tuple.

loop_count

Remaining loop cycles. Negative means infinite.

orientation

Source orientation in 3D as quaternion, a 4-float tuple.

pitch

Audio tone scale.

position

Playback position in seconds.

relative

Whether source position, velocity, and orientation are relative or absolute to the listener.

status

Playback state: playing, paused, or stopped (invalid).

velocity

Source velocity in 3D, a 3D float tuple.

volume

Audio loudness.

volume_maximum

Maximum source volume.

See also

Device.distance_model

volume_minimum

Minimum source volume.

See also

Device.distance_model

class aud.ImpulseResponse

An ImpulseResponse represents a convolution filter for sound processing.

class aud.PlaybackManager

PlaybackManager organizes and controls sound groups by category.

addCategory(volume)

Adds a category with custom loudness.

Parameters:

volume (float) – The initial category loudness.

Returns:

The new category key.

Return type:

int

clean()

Purges completed and invalid sounds from the playback manager.

getVolume(catKey)

Fetches a category's loudness.

Parameters:

catKey (int) – the category key.

Returns:

The category loudness.

Return type:

float

pause(catKey)

Pauses a category.

Parameters:

catKey (int) – the category key.

Returns:

Success status.

Return type:

bool

play(sound, catKey)

Plays sound in a category.

Parameters:

- sound (Sound) – The sound to begin.

- catKey (int) – the category key; created if absent.

Returns:

The playback handle for sound control.

Return type:

Handle

resume(catKey)

Resumes a category.

Parameters:

catKey (int) – the category key.

Returns:

Success status.

Return type:

bool

setVolume(volume, catKey)

Adjusts a category's loudness.

Parameters:

- volume (float) – the new loudness value.

- catKey (int) – the category key.

Returns:

Success status.

Return type:

int

stop(catKey)

Halts a category.

Parameters:

catKey (int) – the category key.

Returns:

Success status.

Return type:

bool

### Audio System (aud) continued: PlaybackManager and Sequence classes

class aud.Sequence

This sound type handles sequenced playback of multiple sounds.

add()

Adds an entry to the sequence.

Parameters:

- sound (Sound) – The sound this entry plays.

- begin (double) – The entry start time.

- end (double) – The entry end time or negative if determined by the sound.

- skip (double) – Seconds to skip from the beginning.

Returns:

The entry added.

Return type:

SequenceEntry

remove()

Removes an entry from the sequence.

Parameters:

entry (SequenceEntry) – The entry to remove.

setAnimationData()

Writes animation metadata to the sequence.

Parameters:

- type (int) – The animation data category.

- frame (int) – The frame for this data.

- data (sequence of float) – The values to write.

- animated (bool) – Whether the property is animated.

channels

The sequence's audio channel count.

distance_model

The sequence's distance model.

See also

OpenAL Documentation

doppler_factor

The doppler scale factor. A value over 1 exaggerates the effect.

fps

The listener's position in 3D, a 3D float tuple.

muted

Whether the entire sequence is silenced.

rate

The sequence's sampling frequency in Hz.

speed_of_sound

The sequence's speed-of-sound value. Standard air is around 343.3 m/s.

class aud.SequenceEntry

SequenceEntry represents a sound within a sequence.

move()

Relocates an entry.

Parameters:

- begin (double) – The new start time.

- end (double) – The new end time or negative if undetermined.

- skip (double) – Seconds to skip from the start.

setAnimationData()

Writes animation metadata to a sequence entry.

Parameters:

- type (int) – The animation data category.

- frame (int) – The frame for this data.

- data (sequence of float) – The values to write.

- animated (bool) – Whether the property is animated.

attenuation

Distance-based volume reduction factor.

See also

Device.distance_model

cone_angle_inner

Inner cone opening angle. If cone values are set, two audible cones exist with apex at source location, heading toward source orientation. Inside the inner cone, volume is standard. Outside the outer cone, volume becomes cone_volume_outer; between them, volume interpolates linearly.

cone_angle_outer

Outer cone opening angle.

See also

cone_angle_inner

cone_volume_outer

Volume beyond the outer cone.

See also

cone_angle_inner

distance_maximum

Maximum listener distance from the source. Beyond this, volume is zero.

See also

Device.distance_model

distance_reference

Reference distance where volume equals the volume property.

See also

Device.distance_model

muted

Whether the entry is silenced.

relative

Whether source position, velocity, and orientation are relative or absolute to the listener.

sound

The sound the entry plays in the sequence.

volume_maximum

Maximum entry volume.

See also

Device.distance_model

volume_minimum

Minimum entry volume.

See also

Device.distance_model

class aud.Sound

Sound objects are unchanging and represent audio that can play simultaneously multiple times. They act as factories generating internal reader objects for playback.

classmethod buffer(data, rate)

Builds a sound from a data buffer.

Parameters:

- data (numpy.ndarray) – Two-dimensional numpy array containing audio data.

- rate (double) – The sample rate.

Returns:

The new Sound object.

Return type:

Sound

classmethod file(filename)

Constructs a sound object from an audio file.

Parameters:

filename (string) – The file location.

Returns:

The new Sound object.

Return type:

Sound

Warning

File existence or readability errors don't trigger immediately; they appear during playback.

classmethod list()

Creates an empty sound container that can hold multiple sounds.

Parameters:

random (int) – whether playback is randomized or sequential.

Returns:

The new Sound object.

Return type:

Sound

classmethod sawtooth(frequency, rate=48000)

Creates a sawtooth wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Match playback device rate to avoid resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod silence(rate=48000)

Creates a silent sound.

Parameters:

rate (int) – The sampling rate in Hz. Match playback device rate to avoid resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod sine(frequency, rate=48000)

Creates a sine wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Match playback device rate to avoid resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod square(frequency, rate=48000)

Creates a square wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Match playback device rate to avoid resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod triangle(frequency, rate=48000)

Creates a triangle wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Match playback device rate to avoid resampling.

Returns:

The new Sound object.

Return type:

Sound

ADSR(attack, decay, sustain, release)

Applies Attack-Decay-Sustain-Release volume envelope to a sound.

Note: release triggering is not currently implemented in this API.

Parameters:

- attack (float) – Attack time in seconds.

- decay (float) – Decay time in seconds.

- sustain (float) – Sustain level.

- release (float) – Release level.

Returns:

The new Sound object.

Return type:

Sound

accumulate(additive=False)

Accumulates a sound by summing positive input differences to create a monotonic signal. With additivity enabled, negative differences also accumulate, and positive ones double.

Note that additivity breaks monotonicity.

Parameters:

additive – Whether accumulation is additive or not.

Returns:

The new Sound object.

Return type:

Sound

addSound(sound)

Appends a sound to a sound list.

Parameters:

sound (Sound) – The sound to append.

Note

You can only add sounds to a sound list.

animateableTimeStretchPitchScale(fps [, time_stretch, pitch_scale, quality, preserve_formant])

Applies time-stretching and pitch-scaling to sound.

Parameters:

- fps (float) – The animation frame rate.

- time_stretch (float or AnimateableProperty) – Time compression/expansion factor.

- pitch_scale (float or AnimateableProperty) – Pitch adjustment factor.

- quality (Rubberband stretcher quality (`STRETCHER_QUALITY`_*).) – Processing quality.

- preserve_formant (bool) – Whether vocal properties persist during pitch-shifting.

Returns:

The new Sound object.

Return type:

Sound

binaural()

Produces binaural audio from a mono source. The source must be mono.

Parameters:

- hrtfs – An HRTF collection.

- source (Source) – The source positioning object.

- threadPool (ThreadPool) – A thread pool for parallelizing convolution.

Returns:

The new Sound object.

Return type:

Sound

cache()

Buffers sound into RAM.

Reduces decoding and file I/O overhead if the source reads from disk, but uses substantial memory.

Returns:

The new Sound object.

Return type:

Sound

Note

Only fixed-length sounds can be cached.

Warning

Uncompressed PCM requires significant space; cache only short sounds.

convolver()

Creates a sound applying convolution filtering.

Parameters:

- impulseResponse (ImpulseResponse) – The filter for convolution.

- threadPool (ThreadPool) – A thread pool for parallelizing convolution.

Returns:

The new Sound object.

Return type:

Sound

data()

Extracts the sound as a numpy array.

Returns:

A two-dimensional numpy float array.

Return type:

numpy.ndarray

Note

Most efficient with cached sounds.

delay(time)

Adds silence at the beginning.

Parameters:

time (float) – Silence duration in seconds before the sound.

Returns:

The new Sound object.

Return type:

Sound

Echo(delay, feedback, mix)

Adds echo effect to sound.

Parameters:

- delay (float) – Echo delay time in seconds.

- feedback (float) – Feedback magnitude (0.0 to 1.0).

- mix (float) – Wet/dry balance (0.0 to 1.0).

- reset_buffer (bool) – Whether to reset the echo buffer on seek.

Returns:

The new Sound object.

Return type:

Sound

envelope(attack, release, threshold, arthreshold)

Applies a volume envelope based on input amplitude.

Parameters:

- attack (float) – Attack time in seconds.

- release (float) – Release time in seconds.

- threshold (float) – Amplitude threshold for detection.

- arthreshold (float) – Threshold for amplitude ratio.

Returns:

The new Sound object.

Return type:

Sound

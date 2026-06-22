# Audio System Aud (part 2)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Continuing Audio System (aud) documentation for additional Sound methods.

classmethod list()

Builds an empty sound group that can contain multiple sounds.

Parameters:

random (int) – whether playback cycles through randomly or sequentially.

Returns:

The new Sound object.

Return type:

Sound

classmethod sawtooth(frequency, rate=48000)

Produces a sawtooth wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Align with playback hardware rate to skip resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod silence(rate=48000)

Produces silent audio.

Parameters:

rate (int) – The sampling rate in Hz. Align with playback hardware rate to skip resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod sine(frequency, rate=48000)

Produces a sine wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Align with playback hardware rate to skip resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod square(frequency, rate=48000)

Produces a square wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Align with playback hardware rate to skip resampling.

Returns:

The new Sound object.

Return type:

Sound

classmethod triangle(frequency, rate=48000)

Produces a triangle wave sound.

Parameters:

- frequency (float) – The wave frequency in Hz.

- rate (int) – The sampling rate in Hz. Align with playback hardware rate to skip resampling.

Returns:

The new Sound object.

Return type:

Sound

ADSR(attack, decay, sustain, release)

Applies Attack-Decay-Sustain-Release volume contouring to sound. Note: release activation is not available in the current API.

Parameters:

- attack (float) – Attack duration in seconds.

- decay (float) – Decay duration in seconds.

- sustain (float) – Sustain level.

- release (float) – Release level.

Returns:

The new Sound object.

Return type:

Sound

accumulate(additive=False)

Tallies sound by adding positive input changes to yield a monotonic output. With additivity on, negative changes contribute, and positive ones double.

Note that additivity removes monotonicity.

Parameters:

additive – Whether accumulation uses additivity.

Returns:

The new Sound object.

Return type:

Sound

addSound(sound)

Inserts a sound into a sound group.

Parameters:

sound (Sound) – The sound to insert.

Note

You can only add sounds to a sound group.

animateableTimeStretchPitchScale(fps [, time_stretch, pitch_scale, quality, preserve_formant])

Applies time-stretching and pitch-scaling to sound.

Parameters:

- fps (float) – The animation frame rate.

- time_stretch (float or AnimateableProperty) – Time compression/expansion magnitude.

- pitch_scale (float or AnimateableProperty) – Pitch adjustment magnitude.

- quality (Rubberband stretcher quality (`STRETCHER_QUALITY`_*).) – Processing grade.

- preserve_formant (bool) – Whether vocal formants endure pitch-shifting.

Returns:

The new Sound object.

Return type:

Sound

binaural()

Constructs binaural audio from a mono source. Input must be mono.

Parameters:

- hrtfs – An HRTF collection.

- source (Source) – The source positioning object.

- threadPool (ThreadPool) – A thread pool for parallelizing convolution.

Returns:

The new Sound object.

Return type:

Sound

cache()

Stores sound in RAM.

Minimizes decoding and file overhead when reading from disk, but demands large memory.

Returns:

The new Sound object.

Return type:

Sound

Note

Only fixed-length sounds can be cached.

Warning

Uncompressed PCM consumes significant space; buffer only short sounds.

convolver()

Builds a sound applying convolution processing.

Parameters:

- impulseResponse (ImpulseResponse) – The filter for convolution.

- threadPool (ThreadPool) – A thread pool for parallelizing convolution.

Returns:

The new Sound object.

Return type:

Sound

data()

Exports sound as a numpy array.

Returns:

A two-dimensional numpy float array.

Return type:

numpy.ndarray

Note

Most efficient with cached sounds.

delay(time)

Prepends silence at the start.

Parameters:

time (float) – Silent duration in seconds preceding the sound.

Returns:

The new Sound object.

Return type:

Sound

Echo(delay, feedback, mix)

Applies echo effect to sound.

Parameters:

- delay (float) – Echo delay duration in seconds.

- feedback (float) – Feedback intensity (0.0 to 1.0).

- mix (float) – Wet/dry proportion (0.0 to 1.0).

- reset_buffer (bool) – Whether to clear the echo buffer on seek.

Returns:

The new Sound object.

Return type:

Sound

envelope(attack, release, threshold, arthreshold)

Applies a volume envelope determined by input amplitude.

Parameters:

- attack (float) – Attack duration in seconds.

- release (float) – Release duration in seconds.

- threshold (float) – Amplitude threshold for activation.

- arthreshold (float) – Threshold for amplitude ratio.

Returns:

The new Sound object.

Return type:

Sound

Postpones playback by inserting silence before the other sound source.

Parameters :

- attack ( float ) – Controls the onset intensity.

- release ( float ) – Controls the decay behavior.

- threshold ( float ) – The general threshold value.

- arthreshold ( float ) – The attack/release threshold value.

Returns :

The created Sound object.

Return type :

Sound

fadein ( start , length ) 

Gradually increases the volume of a sound over a specified duration.

Parameters :

- start ( float ) – Timestamp where fading begins (in seconds).

- length ( float ) – Duration of the fade effect (in seconds).

Returns :

The created Sound object.

Return type :

Sound

Note

Before the fade starts it plays silence.

fadeout ( start , length ) 

Gradually decreases the volume of a sound over a specified duration.

Parameters :

- start ( float ) – Timestamp where fading begins (in seconds).

- length ( float ) – Duration of the fade effect (in seconds).

Returns :

The created Sound object.

Return type :

Sound

Note

After the fade this sound plays silence, so that
the length of the sound is not altered.

filter ( b , a = (1,) ) 

Processes a sound using supplied IIR filter coefficients.
Without the second parameter you get a FIR filter instead.

If the initial value in the a sequence equals 0,
it will be set to 1 automatically.
If the first value in the a sequence is neither 0 nor 1, all
filter coefficients scale proportionally so the value becomes 1
at the end, eliminating the need for manual scaling.

Parameters :

- b ( sequence of float ) – The nominator filter coefficients.

- a ( sequence of float ) – The denominator filter coefficients.

Returns :

The created Sound object.

Return type :

Sound

highpass ( frequency , Q = 0.5 ) 

Constructs a second order highpass filter based on the transfer
function \\(H(s) = s^2 / (s^2 + s/Q + 1)\\)

Parameters :

- frequency ( float ) – Cutoff point for the highpass effect.

- Q ( float ) – Q factor of the lowpass.

Returns :

The created Sound object.

Return type :

Sound

join ( sound ) 

Plays two sound sources one after another in sequence.

Parameters :

sound (Sound) – The sound to play second.

Returns :

The created Sound object.

Return type :

Sound

Note

The two factories have to have the same specifications
(channels and samplerate).

limit ( start , end ) 

Restricts a sound to play between two specific time positions.

Parameters :

- start ( float ) – Starting point in seconds.

- end ( float ) – Ending point in seconds.

Returns :

The created Sound object.

Return type :

Sound

loop ( count ) 

Repeats a sound multiple times.

Parameters :

count ( integer ) – Number of repetitions to apply.
Negative values mean endlessly.

Returns :

The created Sound object.

Return type :

Sound

Note

This is a filter function, you might consider using
Handle.loop_count instead.

lowpass ( frequency , Q = 0.5 ) 

Constructs a second order lowpass filter based on the transfer function \\(H(s) = 1 / (s^2 + s/Q + 1)\\)

Parameters :

- frequency ( float ) – Cutoff point for the lowpass effect.

- Q ( float ) – Q factor of the lowpass.

Returns :

The created Sound object.

Return type :

Sound

mix ( sound ) 

Combines two sound sources together.

Parameters :

sound (Sound) – The sound to mix over the other.

Returns :

The created Sound object.

Return type :

Sound

Note

The two factories have to have the same specifications
(channels and samplerate).

modulate ( sound ) 

Applies frequency modulation using two sound sources.

Parameters :

sound (Sound) – The sound to modulate over the other.

Returns :

The created Sound object.

Return type :

Sound

Note

The two factories have to have the same specifications
(channels and samplerate).

mutable ( ) 

Generates a sound that restarts when you seek backward.
If the original sound is a sound list, the playing sound can change.

Returns :

The created Sound object.

Return type :

Sound

pingpong ( ) 

Plays a sound in both forward and backward directions sequentially.
This works similarly to joining a sound with its reverse.

Returns :

The created Sound object.

Return type :

Sound

pitch ( factor ) 

Modifies the pitch of a sound by a scaling value.

Parameters :

factor ( float ) – Pitch scaling multiplier.

Returns :

The created Sound object.

Return type :

Sound

Note

This is done by changing the sample rate of the
underlying sound, which has to be an integer, so the factor
value rounded and the factor may not be 100 % accurate.

Note

This is a filter function, you might consider using
Handle.pitch instead.

rechannel ( channels ) 

Remaps the sound to a different channel layout.

Parameters :

channels ( int ) – Target channel configuration.

Returns :

The created Sound object.

Return type :

Sound

resample ( rate , quality ) 

Changes the audio to a different sample rate.

Parameters :

- rate ( double ) – Target sample rate.

- quality ( int ) – Resampler performance vs quality choice (0=fastest, 3=slowest).

Returns :

The created Sound object.

Return type :

Sound

reverse ( ) 

Plays a sound in reverse order.

Returns :

The created Sound object.

Return type :

Sound

Note

The sound has to have a finite length and has to be seekable.
It's recommended to use this only with factories with
fast and accurate seeking, which is not true for encoded audio
files, such ones should be buffered using cache() before
being played reversed.

Warning

If seeking is not accurate in the underlying sound
you'll likely hear skips/jumps/cracks.

sum ( ) 

Combines all samples of a sound into a single value.

Returns :

The created Sound object.

Return type :

Sound

threshold ( threshold = 0 ) 

Converts an audio wave into a square wave by assigning samples with amplitude >= threshold to 1, samples with amplitude <= -threshold to -1, and all intermediate samples to 0.

Parameters :

threshold ( float ) – Amplitude limit for binary conversion.

Returns :

The created Sound object.

Return type :

Sound

timeStretchPitchScale ( time_stretch , pitch_scale , quality , preserve_formant ) 

Performs simultaneous time-stretching and pitch adjustment on the sound.

Parameters :

- time_stretch ( float ) – Duration scaling factor.

- pitch_scale ( float ) – Pitch adjustment multiplier.

- quality ( int ) – Rubberband stretcher quality (`STRETCHER_QUALITY`_*).

- preserve_formant ( bool ) – Whether to preserve the vocal formants during pitch-shifting.

Returns :

The created Sound object.

Return type :

Sound

volume ( volume ) 

Adjusts the loudness level of a sound.

Parameters :

volume ( float ) – New amplitude level.

Returns :

The created Sound object.

Return type :

Sound

Note

Should be in the range [0, 1] to avoid clipping.

Note

This is a filter function, you might consider using
Handle.volume instead.

write ( filename , rate , channels , format , container , codec , bitrate , buffersize ) 

Exports the sound to a file on disk.

Parameters :

- filename ( string ) – Output file path.

- rate ( int ) – Sample rate for output.

- channels ( int ) – Number of output channels.

- format ( int ) – Sample format for output.

- container ( int ) – Container format for the file.

- codec ( int ) – Codec to use in the file.

- bitrate ( int ) – Output bitrate.

- buffersize ( int ) – Size of the writing buffer.

length 

The sample specification of the sound as a tuple with rate and channel count.

specs 

The sample specification of the sound as a tuple with rate and channel count.

class aud. Source 

The source object represents the source position of a binaural sound.

azimuth 

The azimuth angle.

distance 

The distance value. 0 is min, 1 is max.

elevation 

The elevation angle.

class aud. ThreadPool 

A ThreadPool is used to parallelize convolution efficiently.

class aud. error

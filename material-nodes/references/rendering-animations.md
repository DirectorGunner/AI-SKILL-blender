# Rendering Animations, Animation Player, Format, Metadata ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Rendering Animations; Animation Player; Format; Metadata; Output; Post Processing.

## Rendering Animations

### Rendering Animations 

When rendering still images, you can view and save the result from the render buffer once complete. Animations, by contrast, are composed of sequential frames and are automatically stored to disk after rendering finishes.

The typical post-production workflow involves editing clips after rendering, or using the Compositor for tasks such as green-screen keying, matting, color adjustment, depth-of-field processing, and other enhancements applied to individual frames. These frames are then fed to the Sequencer where strips are edited, mixed, and final compositing is applied.

The final stage allows you to export from the Sequencer, encoding the frame sequence into a compressed video file.

### Workflow 

Most animation projects require multiple intermediate renders at different stages to validate timing, lighting, placement, material appearance, and other elements. Once you reach the desired quality level, you can proceed with the final render of the entire animation for distribution.

Two primary strategies exist for creating movies or animations with or without audio. Your choice depends on the total CPU time needed for rendering. You can estimate render time by timing a representative frame at the target resolution, then multiplying by the total number of frames. For example, a 60-second clip filmed at 24fps contains 1440 frames. If each frame takes 30 seconds to render, the total time would be 720 minutes—or 12 hours.

Rendering uses all available CPU resources. Typically you should render when the computer is idle (overnight, for example) or configure Blender to run at reduced priority while working on other tasks (though be mindful of available RAM).

Direct Approach

The Direct Approach is not recommended and represents outdated practice. In this method, you configure output as AVI or MOV format and press Animation to render directly to a movie file. Blender creates a single file containing all animation frames, which can later be processed in the Video Sequencer to add audio and output as MPEG format.

Frame Sequence

The Frame Sequence approach is significantly more reliable. You set output format to a still image type (JPG, PNG, or multi-layer format) and press Animation to render as a series of images where each file represents a single frame.

Blender produces one file per frame. You can then apply any frame-level adjustments in the Compositor, load the final image sequence into the Video Sequencer, add audio, and export to MPEG to create your final video. Though this method requires more storage space and additional steps, it provides greater flexibility during production.

These guidelines help you decide which approach suits your situation.

Direct Approach

- Shorter renders with total time under one hour.

- Steady power source.

- Computer not in use for other purposes.

Frame Sequence Approach

- Total render time exceeding one hour.

- Post-production adjustments needed:

- Color and lighting refinement

- Green screen or matte compositing

- Layering and effects

- Output in multiple resolutions or formats

- Adjustments to frames for compression optimization.

- Exact synchronization (such as audio alignment) in sections.

- May interrupt rendering to use the computer while preserving progress.

### Frame Sequence Workflow 

- Prepare your animation first.

- In the Format panel, specify render dimensions, Pixel Aspect Ratio, and Frame Range (Start and End), with frame rate typically pre-configured.

- In the Output panel, configure your animation to export as images, choosing a format that preserves quality.

- Define the output folder and file format in the Output panel, for instance //render/my-anim- .

- Verify your animation's start and end frames.

- Save your .blend file.

- Press the Animation button. Once rendering completes, open your file manager and browse to the output location (render in this example). A numbered series of image files awaits you—each corresponds to a single frame.

- Open the Video Sequencer in Blender.

Note

The Video Sequencer lacks multi-layer EXR support. To produce video, omit the following three operations and route your sequence through an Image Input node in the Compositor instead.

- From the add menu, select Add Image. Choose all desired frames from your output folder and import them as a strip in the Sequence editor.

- Edit the strip, apply effects if desired, or leave it unchanged. Combine with additional strips such as audio.

- Play through the animation to confirm all frames are present.

- In the Output panel, choose the video container and codec (for example, MPEG H.264) and adjust settings. Video codec specifications appear in Output Options.

- Press the Animation render button to encode the Sequence editor contents into a video file.

### Hints 

If your computer unexpectedly turns off during rendering, recovery is simplest with image-based output. Instead of rendering directly to a compressed video file, use a lossless format (PNG). This makes recovery straightforward—already-rendered frames remain in the output directory.

Simply uncheck the Overwrite option to resume from the last completed frame.

Create your final video using Blender's Sequence editor or external encoding tools.

Animation Preview
Previewing a subset of your animation can help isolate errors within specific sections.

Using image output format, the Frame Step option renders every Nth frame. Then disable Overwrite and re-render with Frame Step set to 1.

## Animation Player

### Animation Player 

Reference

Menu :

Topbar ‣ Render ‣ View Animation

Shortcut :

Ctrl - F11

The animation player enables preview of finished animations, supporting all image and video formats recognized by Blender. It allows playback of image sequences synchronized to the proper frame rate.

Opening the animation player creates a separate window that plays back images or video from your scene's render output location. You can drag images or video files into an active player window to switch playback to that media.

Tip

An external player can substitute for Blender's built-in player. Configure this in the Preferences.

### Player Options 

Ping Pong
When enabled, playback alternates direction—forward then backward.

X/Y Flip
Mirror the image along the horizontal or vertical axis.

Viewing the animation from an alternate orientation provides a fresh perspective on the motion.

### Hotkeys 

The following table shows available hotkeys for the animation player.

Playback

| Action | Hotkey |
| Start/Pause: | Spacebar |
| Start playback (when paused): | Return |
| Quit: | Esc |

Timeline

| Action | Hotkey |
| Scrub in time: | LMB |
| Step back one frame: | Left |
| Step forward one frame: | Right |
| Step back 10 frames: | Down |
| Step forward 10 frames: | Up |
| Manual frame stepping: | NumpadPeriod |

Playback Options

| Action | Hotkey |
| Backward playback: | Shift - Down |
| Forward playback | Shift - Up |
| Slow down playback: | NumpadMinus |
| Speed up playback: | NumpadPlus |
| Toggle looping: | Numpad0 |
| Toggle frame skipping: | A |
| Toggle ping-pong: | P |

Display

| Action | Hotkey |
| Toggle Playhead (Indicator): | I |
| Flip image on the X axis: | F |
| Flip image on the Y axis: | Shift - F |
| Hold to show frame numbers: | Shift |
| Zoom in: | Ctrl - NumpadPlus |
| Zoom out: | Ctrl - NumpadMinus |

Frame Rate

| Action | Hotkey |
| 60 fps | Numpad1 |
| 50 fps | Numpad2 |
| 30 fps | Numpad3 |
| 25 fps | Numpad4 |
| 24 fps | Shift - Numpad4 |
| 20 fps | Numpad5 |
| 15 fps | Numpad6 |
| 12 fps | Numpad7 |
| 10 fps | Numpad8 |
| 6 fps | Numpad9 |
| 5 fps | NumpadSlash |

### Frame Cache 

Image files are cached during playback to speed up access.

Though loading images rarely becomes a performance limitation, high-resolution images can sometimes cause slowdown and frame drops during playback.

See also

Memory Cache Limit preference to adjust the caching limit; increasing it allows more images to be retained in memory during playback.
Animation Playback Options to set this value when launching from the command line.

## Format

### Format 

Format panel. 

Many render presets provide common resolutions and frame rates for different displays and broadcast standards, available in the panel header.

Resolution X, Y
Horizontal and vertical pixel dimensions of the output.

Percentage
Adjustment slider for reducing or expanding rendered size relative to the Resolution settings. Useful for quick test renders at the same aspect ratio as the final output.

Aspect X, Y
Legacy televisions utilized non-square pixels, so this parameter adjusts pixel shape along each axis. Images are pre-distorted to appear stretched on computer displays but display correctly on TV sets. Using the correct pixel aspect ratio prevents re-scaling and associated quality loss.

Render Region
Restricts output to a portion of the view rather than the complete frame. See the Render Region documentation for defining region boundaries.

Crop to Render Region
Trims rendered output to match the render region size instead of rendering a transparent area around it.

Frame Rate
Frequency at which frames display per second, relevant for Animation. The menu includes standard frame rates, and custom rates can be set by selecting Custom to access these properties:

FPS
The frame rate expressed as frames per second.

Base
Certain standards require fractional frame rates, particularly NTSC. These are expressed as a fraction where the Base value becomes the denominator and the FPS becomes the numerator: \\(\\frac{FPS}{Base}\\) .

See also

Viewport Playback Frame Rate Limited

## Metadata

### Metadata 

Metadata panel. 

The Metadata panel offers controls for embedding metadata into render output.

Note

Only specific image formats support metadata embedding: See image formats.

Metadata Input
The source for metadata retrieval.

Scene :

Current scene metadata is used.

Sequencer Strips :

Metadata originates from Sequencer strips.

Include

Date
Appends the current date and moment.

Time
Includes the active scene time and render frame in HH:MM:SS.FF format.

Render Time
Appends total rendering duration.

Frame
Includes the current frame index.

Frame Range
Includes start and end frame values.

Memory
Appends peak memory consumption.

Hostname
Includes the rendering system's hostname.

Camera
Includes the active camera name.

Lens
Includes the active camera's focal length.

Scene
Includes the active scene name.

Marker
Includes the final marker name.

Filename
Includes the .blend filename.

Strip Name
Includes the foreground sequence strip name.

### Note 

Adds a custom text entry.

Hint

Utilizing the Note field proves helpful when managing render farms. Any information can be inserted via scripting, such as render node identifiers or job numbers. Refer to this page for stamping details.

### Burn into Image 

Renders metadata as visible text on the image.

Font Size
Adjusts text sizing.

Text Color
Sets the stamp text color and transparency.

Background
Sets the backdrop color and transparency behind the text.

Include Labels
Displays labels alongside metadata values. For example, "Camera" appears before the camera name.

## Output

### Output 

Output panel. 

This panel manages rendered frame storage location and saved image quality for animations.

File Path
Select where to save rendered output.

During animation rendering, frame numbers are appended to the filename using four zero-padded digits (e.g. image0001.png). Customize padding by inserting # characters in the filename (e.g. image_##_test.png converts to image_01_test.png).

This option respects Relative Paths, where // indicates the folder containing the active .blend file.

Saving – File Extensions
Adds the proper file extension per format to output.

Saving – Cache Result
Renders view layers and passes to a multi-layer OpenEXR image. The Compositor can leverage this cached file for enhanced performance during intensive compositing work.

Storage location is determined by the Render Cache folder in File Paths Preferences. You can retrieve it back to the Image Editor's Render Result even after closing and restarting Blender; see Open Cached Render.

Media Type
Output media classification.

Image :

Saves each input as a separate image.
Each input type supports independent image settings.

Multi-Layer EXR :

Combines all inputs into a single multi-layer OpenEXR file.

Video :

Encodes frames into a video format. Detailed codec options appear in the Encoding panel.

File Format Image
Select the image file format for saving. Different formats present different options such as channels, bit depth, and compression levels. Consult the image encoding options list.

Color Image Multi-Layer EXR
The output color format for the image or video. Some formats use this setting to optimize data storage. Note that RGBA is unavailable for certain formats; see the format list above.

BW :

Output using grayscale.

RGB :

Saves red, green, and blue channels.

RGBA :

Saves red, green, blue, and alpha channels.

Image Sequence – Overwrite Image Multi-Layer EXR
Replace existing files when rendering.

Image Sequence – Overwrite Image Multi-Layer EXR
Reserve placeholder files while rendering.

Hint

Primitive Render Farm

A simple setup for distributing rendering across multiple machines involves:

- Establish a shared directory over network file storage.

- Turn off Overwrite and turn on Placeholders in the Render Output panel.

- Trigger rendering on as many systems as desired pointing to the shared location.

### Color Management 

This panel controls how Color Management is applied when saving images.

Follow Scene :

Applies the same color settings defined in the active Scene. These options are specified in the Render Settings.

Override :

Uses bespoke color management settings defined below in this panel, disregarding scene-level color settings.

For complete information about color management options, consult the Color Management page.

### Pixel Density 

The pixel density (commonly called PPI or DPI) specifies the intended physical dimensions for an image. This proves valuable for print output or sizing in document layout programs.

The X/Y density calculation incorporates the render X/Y aspect ratio, making these parameters useful for storing the aspect ratio of non-square pixels.

Pixel-density functions as metadata without impacting image resolution.

See also

Pixel Density support for image formats

### Encoding 

Reference

Panel :

Properties ‣ Output ‣ Encoding

Encoding panel. 

Configure video container, codec, and compression parameters here. These compression choices involve trade-offs between storage size, cross-platform compatibility, and video quality. Use the presets in the header to quickly apply optimal settings for that output type.

Tip

Access the System Console to monitor encoding process output. More detailed output is visible when running Blender as blender -d .

Container
Video container or file format. Consult video formats for all available options.

Autosplit Output
For videos exceeding 2GiB, activate Autosplit Output. Output will automatically split into multiple files once the first file reaches 2GiB.

### Video 

Video Codec
Selects the compression and encoding approach. See video formats for all available options.

Note

Standards

Some video containers and codecs prove incompatible. If errors occur, verify container-codec compatibility. Additionally, certain codecs function only with specific frame dimensions. Default to standard sizes or investigate codec limitations.

Color Depth
The exponent (base-2) representing color count within each color channel. Higher bit depths enable richer color representation, lowering banding artifacts and improving fidelity. However, bit depth increases memory consumption exponentially.

Notably, not all formats support every color depth configuration.

8 :

Supports 256 levels per channel, totaling approximately 16.7 million colors (RGB). The standard for on-screen content and conventional video.

10 :

Supports 1,024 levels per channel, totaling over 1 billion colors (RGB). Available for H.264, H.265, and AV1 codecs.

12 :

Supports 4,096 levels per channel, totaling over 68 billion colors (RGB). Available for H.265 and AV1 codecs.

Profile ProRes
Defines encoded video quality, compression, and transmission rate.

ProRes 422 Proxy :

Minimal bitrate and quality. Useful for offline work where speed and storage are priorities.

ProRes 422 LT :

Lower bitrate than standard ProRes 422 with reasonable fidelity. Appropriate for editorial and preview stages.

ProRes 422 :

Equilibrium between image precision and file size. Recommended for standard workflows.

ProRes 422 HQ :

Superior quality and bitrate versus standard ProRes 422. Preferred for broadcast and premium post-production.

ProRes 4444 :

Retains complete RGB and alpha channel data. Designed for effects and visual effects work.

ProRes 4444 XQ :

Maximum ProRes fidelity. Maintains peak color detail and tonal range, ideal for color work and high-end visual effects.

Output Quality
These represent preset Rate choices.

CRF Custom Quality
Constant Rate Factor (CRF). Reducing CRF enhances video fidelity but enlarges output. Permitted ranges depend on the codec: 0-51 for AV1, H.264 and H.265/HEVC; 0-63 for WebP/VP9 and 1-31 for MPEG-4/DivX. Values outside the range are clipped to the nearest valid value. A CRF of 0 creates lossless encoding.

Encoding Speed
Choices balancing fast encoding (larger files) with heavy compression (smaller files).

Keyframe Interval
The count of pictures per Group of Pictures. Set to 0 for "intra_only" mode, which disables between-frame video coding. Larger intervals typically reduce file size but require more computing power for playback.

Max B-frames
Allows B-frame usage.

Interval
Maximum B-frames separating non-B-frames.

#### Rate 

Bitrate
Specifies average bit rate (quality) as the quantity of binary information per frame. Consult FFmpeg -b:v.

Minimum / Maximum
Video files can employ variable bit rate (VBR), distributing compressed data to allocate more to complex frames and less to simple ones. Configure this via Minimum and Maximum settings.

Buffer
The playback bitstream buffer capacity.

Mux Rate
Maximum transmission rate of the combined stream. Multiplexing merges separate video and audio tracks into one file, similar to packaging a video and MP3 into a container.

Mux Packet Size
Reduces muxer fragmentation or overhead based on input.

### Audio 

These controls govern audio export during rendering. For playback from Blender itself, refer to audio preferences in the Preferences menu.

Audio Codec
Codec selection for sound output. Consult video formats for all options.

Audio Channels
The quantity of audio output "locations" to encode.

Mono :

A single channel.

Stereo :

Two channels; usually left and right.

4 Channels :

Four output channels.

5.1 Surround :

Five channels with one LFE.

7.1 Surround :

Seven channels with one LFE.

Sample Rate
Audio frequency setting.

Bitrate
Control bit rate (quality) for each codec. Higher rates create larger files with inferior streaming but improved sound. Use powers of 2 for broad compatibility.

Volume
Output volume adjustment.

### Tips 

Tip

Video format selection depends on your intended use.

Direct video-format rendering is not advised initially. If issues occur during rendering, the file can become corrupted, necessitating a complete re-render. First produce a set of still images like the default PNG or high-fidelity OpenEXR (supporting HDR data), then combine them as an Image Strip in the Video Sequencer. This approach offers:

- Resumption from the interrupted frame if problems surface.

- Rapid codec testing in seconds versus minutes/hours, since encoding is quicker than 3D rendering.

- Full Video Sequencer capabilities, including compositing earlier renders, audio integration, and other clips.

Tip

Avoid post-processing lossy-compressed material as compression artifacts will be amplified. Employ lossy formats only for the final delivery stage.

## Post Processing

### Post Processing 

Reference

Panel :

Properties ‣ Output ‣ Post Processing

The Post Processing panel configures different output processing parameters applied after rendering.

Post Processing panel. 

Pipeline – Compositing
Executes the compositing node network, applying the Composite node tree across all rendered images and outputting the result from the Group Output node.

Pipeline – Sequencer
Outputs the Video Sequence editor instead of the 3D camera view. If the sequence incorporates Scene strips, these render as part of the workflow. When Compositing is enabled, Scene strip output is post-processed via the Compositor.

Dither
Dithering minimizes color banding artifacts in gradient regions where stair-stepping appears between hues. These artifacts become more conspicuous with extended or shallow gradients. Historically developed for reduced-color graphics with restricted palettes.

Dithering works by comparing pixel intensity against neighboring pixels and applying calculations to produce suitable colors. The process generates an impression of extended color palette through visual color blending. For instance, alternating red and yellow pixels create an orange appearance.

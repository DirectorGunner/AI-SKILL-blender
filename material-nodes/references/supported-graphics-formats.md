# Supported Graphics Formats, Supported Video Audio Formats, The Blender Community, About Blender ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Supported Graphics Formats; Supported Video & Audio Formats; The Blender Community; About Blender; Installing on macOS.

## Supported Graphics Formats

Image Formats — these image file formats are supported internally by Blender:
- JPEG — 8bit; Alpha ✗; Metadata ✓; DPI ✓; .jpg .jpeg
- OpenEXR — float 16, 32bit; Alpha ✓; Metadata ✓; DPI ✓; .exr
- PNG — 8, 16bit; Alpha ✓; Metadata ✓; DPI ✓; .png
- WebP — 8bit; Alpha ✓; Metadata ✓; DPI ✗; .webp
- AVIF — 8, 10, 12bit; Alpha ✓; Metadata ✗; DPI ✗; .avif
- BMP — 8bit; Alpha ✓; Metadata ✗; DPI ✓; .bmp
- Cineon — 8, 10, 12, 16bit; Alpha ✓; Metadata ✗; DPI ✗; .cin
- DPX — 8, 10, 12, 16bit; Alpha ✓; Metadata ✗; DPI ✗; .dpx
- Iris — 8, 16bit; Alpha ✓; Metadata ✗; DPI ✗; .sgi .rgb .bw
- JPEG 2000 — 8, 12, 16bit; Alpha ✓; Metadata ✗; DPI ✗; .jp2 .jp2 .j2c
- Radiance HDR — float; Alpha ✓; Metadata ✗; DPI ✗; .hdr
- Targa — 8bit; Alpha ✓; Metadata ✗; DPI ✗; .tga
- Targa Raw — 8bit; Alpha ✓; Metadata ✗; DPI ✗; .tga
- TIFF — 8, 16bit; Alpha ✓; Metadata ✗; DPI ✓; .tif .tiff
Hint: if the technical detail doesn't interest you, a good rule for picking an output format is — OpenEXR if you'll composite or color-grade the images, PNG for on-screen output or encoding into multiple video formats, JPEG for on-screen output where file size matters and some quality loss is fine. All of these support compression, which can matter when rendering animations.
Hint: image bit depths give these many tonal levels per channel — 8: 256 levels; 10: 1024 levels; 12: 4096 levels; 16: 65536 levels.

Opening Images:
Relative Path — sets the file path relative to the open blend-file (see Relative Paths).
Detect Sequences — auto-hunts for image sequences in the chosen images (by file name); switch it off when you really do want single images that belong to a sequence (see Opening an Image Sequence).
Detect UDIMs — auto-hunts for UDIM tiles in the chosen image's directory and loads any matches as UDIMs; it works by spotting a .xxxx (a four-digit number) ahead of the file extension.
Opening an Image Sequence — to load a sequence in any supported format, the filenames must hold a digit marking the frame order (e.g. *-0001.jpg, *-0002.jpg, *-0003.jpg, of any format), which sets the frame. Open it by selecting the images one of these ways and confirming with the Open Image button or Return:
Range — browse into the directory and LMB-drag over a span of names to highlight several; you can page down and keep Shift-LMB-dragging to add more.
Batch — Shift-LMB unrelated stills for batch processing; each image becomes one frame, in sort order, and they can mix file types (jpg, png, exr, etc.).
All — press A to select/deselect every file in the directory.

Saving Images:
File Format — pick the image format to save to; the chosen format determines which other options (channels, bit depth, compression level) appear.
Color — the color format to save the image or video in; some formats use it to trim how much data is written. RGBA isn't available for every format — check the list above. BW (grayscale), RGB (red, green, blue channels), or RGBA (red, green, blue, alpha channels).
Color Depth — the bit depth per color channel, setting how many color values can be represented; higher depths cut color banding and improve precision but grow file size and memory, and not every format supports every depth. 8 (the common choice for on-screen graphics, web, and standard video), 10/12/16 (used by photography and digital-cinema formats like DPX and JPEG 2000, with more tonal range than 8-bit), 32 (32-bit float per channel — the highest precision and dynamic range, mainly for OpenEXR VFX and compositing), Float (Half) (16-bit float per channel — high dynamic range at lower memory/storage cost, OpenEXR only), or Float (Full) (32-bit float per channel — highest precision and dynamic range, OpenEXR only). Note: internally Blender works only in 8-bit or 32-bit, so images above 8-bit precision (10-, 12-, 16-bit) convert to 32-bit float on load.
Compression — shrinks the image file's size, by a method that varies with the format and settings.
Quality — the amount of lossy compression applied, as a percentage; lossy compression shrinks file size by dropping some image data, which can cost detail. 0% means maximum compression — smallest files, most obvious quality loss; 100% means none — full quality at a larger file size.
Save As Render — saves the image with render color management: for display formats like PNG it applies the view and display transform, and for intermediate formats like OpenEXR it uses the default render output color space.

Copy — sets whether the data-block will reference the newly created file, or leave the reference unchanged and keep it on the original.
Color Space — names the color space of the source file. The list depends on the active OCIO config; the defaults are detailed under Default OpenColorIO Configuration. Note: the Cineon, DPX, OpenEXR, and Radiance HDR types are saved in a linear color space by default.

Format Details:
Cineon & DPX — Cineon is Kodak's film-scanning standard, 10 bits per channel and logarithmic. DPX, derived from Cineon, became the ANSI/SMPTE industry standard; it supports 16-bit colors/channels, linear or logarithmic, and is a widely adopted standard in the film hardware/software industry. Both DPX and Cineon only store and convert the "visible" color range of values between 0.0 and 1.0 (the result of rendering or compositing).
OpenEXR — ILM's OpenEXR is now a software-industry standard for HDR image files, largely thanks to its flexible, expandable structure. An OpenEXR file can hold multiple layers and passes, so OpenEXR images load into a Compositor with their render layers and passes intact. Note: when opening OpenEXR images, Blender sets the Color Space automatically if it detects Linear CIE-XYZ E or ACES2065-1.
Output Options — available for OpenEXR render output:
Color Depth — the base-two exponent for how many colors fit in one channel; a higher bit depth allows more colors, cutting banding and raising precision, but grows memory use exponentially. Float (Half) (a custom 16 bits per channel in floating point, which trims the effective bit depth to 10-bit — a 5-bit power value plus a 1-bit sign) or Float (Full) (32 bits per channel in floating point).
Codec — the compression used to encode the EXR-file. None (no compression — fastest encoding, biggest files), ZIP (lossless Zlib on 16-row blocks), PIZ (lossless wavelet, good for noisy/grainy images), DWAA (lossy) (JPEG-like lossy on 32-row blocks), DWAB (lossy) (JPEG-like lossy on 256-row blocks), HTJ2K (lossless, based on high-throughput JPEG 2000 — smaller files but new and not widely supported yet), ZIPS (lossless Zlib, each row compressed on its own), RLE (lossless run-length, good when rows share values), Pxr24 (lossy) (converts 32-bit floats to 24 bits then deflates — lossless for half and 32-bit integer data, slightly lossy for 32-bit float), B44 (lossy) (lossy for 16-bit float images at a fixed 2.3:1 ratio, compressing uniformly regardless of content), or B44A (lossy) (like B44 but with extra compression on flat-color areas such as alpha).
Quality (DWAA (lossy), DWAB (lossy)) — the amount of lossy compression applied, as a percentage; lossy compression shrinks file size by dropping some image data, which can cost detail. 0% means maximum compression — smallest files, most obvious quality loss; 100% means none — full quality at a larger file size.
Interleave — uses the legacy interleaved storage of views, layers, and passes for compatibility with apps that can't read the more efficient multi-part OpenEXR files.
Preview — when rendering an animation (or single frames from the command line), it saves a JPEG copy of the image as a quick preview.
Radiance HDR — Radiance is a toolkit for lighting simulation; since it had the first (and long the only) HDR image format, many other packages support it. Radiance .hdr files store colors in 8 bits per component plus a shared 8-bit exponent, making 32 bits per pixel.

Metadata — metadata is extra information stored inside an image file describing how it was made or how it should be read. Blender can write metadata into supported formats when enabled in the Output Properties.
Limitations — not every format supports metadata, and some support only a limited subset of fields; with formats that don't support it, render information isn't preserved in the saved file.
Orientation Metadata — EXIF orientation metadata (common in JPEG images) is ignored when loading into Blender, so images display from their stored pixel data without automatic rotation; if one looks wrongly rotated, fix it by hand with Rotate 90° Clockwise.

## Supported Video & Audio Formats

Blender uses FFmpeg for video encoding and decoding; these formats mostly serve to compress rendered image sequences into playable movies. A video file usually consists of: a container (wraps video, audio, and metadata into one file), a video codec (which compresses the video stream), and an audio codec (which compresses the audio stream, and is optional).

Supported Video Containers — the container holds the encoded streams but doesn't dictate how they're compressed.
MPEG-4 — also the name of a codec family, but as a container it can hold video and audio encoded with various codecs, and it's widely supported across modern software and hardware. Extensions: .mp4, .mpg, .mpeg.
Matroska — a free, open-standard container that can hold multiple video, audio, subtitle, and metadata tracks in one file. Extension: .mkv.
WebM — a free, open-standard container aimed mainly at web streaming, supporting VP9 or AV1 video and Vorbis or Opus audio. Extension: .webm.
AVI — one of the earliest and most widely used container formats, derived from the Resource Interchange File Format (RIFF). Extension: .avi.
DV — a digital-video container used by many legacy camcorders; it enforces the DV video codec and stores audio uncompressed. Extension: .dv.
Flash — a container once used to deliver internet video through Adobe Flash Player; it enforces specific codecs. Extension: .flv.
MPEG-1 — a container for lossy video and audio that locks in the MPEG-1 codec family. Extensions: .mpg, .mpeg.
MPEG-2 — a container for DVD and broadcast video; it enforces MPEG-2 encoding for the video and its audio streams. Extensions: .dvd, .vob, .mpg, .mpeg.
Ogg — a free, open-standard container that can hold multiple video, audio, subtitle, or metadata streams. Extensions: .ogg, .ogv.
QuickTime — a multi-track container that shares many codecs with MP4; the two are largely interchangeable in some workflows, but MP4 has wider support. Extension: .mov.

Supported Video Codecs — codecs compress video and audio data to cut file size and keep playback smooth. Lossy codecs shrink files by discarding some data, trading image or audio quality for size; lossless codecs still compress but keep all the original data, giving larger files at full fidelity. Some codecs suit distribution and streaming (H.264, AV1), others editing and intermediate work (ProRes, DNxHD). Because codecs are needed to both encode and decode, they must be present on the machine making the file and the device playing it, and not every codec works in every container.
No Video — for audio-only encoding.
AV1 — a free, open-standard lossy format meant as a successor to VP9; high compression efficiency with HDR output.
H.264 — a widely used lossy codec that balances size against quality well, common in streaming and general delivery.
H.265 / HEVC — a step up from H.264, with tighter compression, HDR output, and deeper color bit depths.
WEBM / VP9 — an open, royalty-free lossy codec popular for internet streaming; handles alpha-channel transparency.
DNxHD — meant as an intermediate editing format; can run lossy or lossless.
DV — see Containers.
FFmpeg video codec #1 — a lossless intra-frame codec; supports alpha-channel transparency.
Flash Video — see Containers.
HuffYUV — a lossless codec built to supplant uncompressed YCbCr capture formats.
MPEG-1 — see Containers.
MPEG-2 — see Containers.
MPEG-4(DivX) — a lossy codec extending the MPEG standards with extra compression features.
ProRes — a high-quality, visually lossless codec common in professional post-production; offers a configurable Profile.
PNG — stores each frame as its own image in the stream; lossless, with alpha-channel transparency.
QuickTime Animation — a legacy lossless QuickTime codec with alpha-channel transparency.
Theora — a free, open-standard lossy codec built for the Ogg container.
Supported Features:
- AV1 — Lossy; 8, 10, 12bit; Alpha ✗; HDR ✓
- H.264 — Lossy; 8, 10bit; Alpha ✗; HDR ✗
- H.265 / HEVC — Lossy; 8, 10, 12bit; Alpha ✗; HDR ✓
- WEBM / VP9 — Lossy; 8bit; Alpha ✓; HDR ✗
- DNxHD — Lossy / Lossless; 8bit; Alpha ✗; HDR ✗
- DV — Lossy; 8bit; Alpha ✗; HDR ✗
- FFmpeg video codec #1 — Lossless; 8, 10, 12, 16bit; Alpha ✓; HDR ✗
- Flash Video — Lossy; 8bit; Alpha ✗; HDR ✗
- HuffYUV — Lossless; 8bit; Alpha ✗; HDR ✗
- MPEG-1 — Lossy; 8bit; Alpha ✗; HDR ✗
- MPEG-2 — Lossy; 8bit; Alpha ✗; HDR ✗
- MPEG-4 (DivX) — Lossy; 8bit; Alpha ✗; HDR ✗
- ProRes — Visually Lossless; 8, 10bit; Alpha ✗; HDR ✗
- PNG — Lossless; 8bit; Alpha ✓; HDR ✗
- QuickTime Animation — Lossless; 8bit; Alpha ✓; HDR ✗
- Theora — Lossy; 8bit; Alpha ✗; HDR ✗

FFmpeg Audio Codecs:
No Audio — for video-only encoding.
AAC — a standardized lossy codec that beats MP3's quality at comparable bit rates.
AC3 — Dolby Digital audio compression.
FLAC — a free lossless codec that shrinks files while keeping full fidelity.
MP2 — a lossy audio format.
MP3 — a widely supported lossy audio format.
Opus — a modern lossy codec for speech and general audio, meant as a successor to Vorbis.
PCM — uncompressed digital audio.
Vorbis — a free, open-standard lossy codec comparable to AAC or MP3.

HDR Support — videos can be rendered in wide-gamut and HDR color spaces.

To export HDR video:
- Set Color Management Display to Rec.2100 PQ or HLG.
- Set Video Codec to H.265 / HEVC or AV1.
- Set Bit Depth to 10 or 12.
HDR videos are written with 100 nits diffuse white to match common video-player conventions. Compatibility varies by player and device; 10-bit PQ is generally the most compatible HDR setup.

Known Limitations — Video Output Size: some codecs cap output size — H.264, for instance, needs both width and height divisible by 2.

## The Blender Community

Being freely available from the very start, even while closed source, did a lot to spread Blender through the community. A large, steady, active body of users has formed around Blender since 1998, and in 2002 they showed their support by helping raise €100,000 in seven weeks to free Blender as Open Source under the GNU GPL License.

Independent Sites — several independent websites — forums, blogs, news, and tutorial sites — are devoted to Blender. One of the biggest community forums is Blender Artists, where users show off their work, trade feedback, ask for and offer help, and generally talk Blender.

Getting Support — the community is one of Blender's best features, so beyond this manual there are many ways to get help from other users, such as Chat, Stack Exchange, and Reddit. Studios and organizations have Enterprise support, and studios looking to fold Blender into their pipeline can turn to Blender Studio for documentation and training on the subject. If you think you've hit a bug, please report it. More on support is on the support page.

Development — being open source, Blender welcomes volunteer development, with developers communicating mostly through three platforms: the projects.blender.org system, the Developer Forum, and Online Chat (below). If you'd like to help develop Blender, see the Get Involved page.

Chat — for real-time discussion there's chat.blender.org, which authenticates via Blender ID. You can join these channels:
- #general — open chat with the community.
- #blender-coders — where developers discuss Blender's development.
- #python — support for developers using the Python API.
- #docs — discussion about Blender's documentation.
- #translations — about translating Blender and its docs.

Other Useful Links:
- Blender FAQ (Can I use Blender commercially? What is GPL/GNU? …).
- Demo and benchmark files.
- Developer's Ask Us Anything!

## About Blender

### About Blender

Blender is the free, open-source 3D creation suite. It covers the whole 3D pipeline — modeling, rigging, animation, simulation, rendering, compositing, motion tracking, and video editing.

Through OpenGL it behaves consistently across Linux, macOS, and Windows.

### Who uses Blender?

Its broad toolset suits almost any kind of media production. Professionals, hobbyists, and studios worldwide reach for it to make animations, game assets, motion graphics, TV shows, concept art, storyboards, commercials, and feature films.

The User Stories page on the Blender website has more examples.

### Key Features

- A fully integrated 3D content-creation suite with a wide range of essential tools: Modeling, Rendering, Animation & Rigging, Video Editing, VFX, Compositing, Texturing, and many kinds of Simulation.

- Cross-platform, with an OpenGL GUI that looks the same on every major platform (and is customizable via Python scripts).

- A high-quality 3D architecture that enables a fast, efficient workflow.

- Active community support. See blender.org/community for a long list of sites.

- It installs into and runs from any directory without touching the system.

The latest version can be downloaded here.

A rendered image being post-processed.

Blender can do a great many things, and the basics can feel daunting at first. Still, with a little motivation and the right learning material, a few hours of practice is enough to grow comfortable with it.

This manual is a good starting point, though it works more as a reference; specialized websites also host plenty of video tutorials.

For all it can do, Blender is still just a tool. Great artists don't make masterpieces by pushing buttons or wielding brushes, but by studying and practicing things like human anatomy, composition, lighting, and animation principles.

3D software like Blender carries extra technical complexity and jargon tied to the underlying tech. Terms such as UV maps, materials, shaders, meshes, and "subdivs" are the digital artist's medium, and grasping them, even loosely, will help you get the most from Blender.

So read on, learn this great tool, and stay curious about other artistic and technical fields — and you, too, can become a great artist.

### Further Reading

## Installing on macOS

### Installing on macOS

If you haven't yet, check the Downloading Blender page for the minimum requirements and the available versions.

Important

On macOS, Blender runs on both Intel and Apple Silicon architectures. Grab the variant that matches your CPU's architecture.

### Install from a DMG

The macOS build ships as disk images (dmg-files). Double-click the dmg-file to mount it, then drag Blender.app into the Applications folder.

Depending on your Mac's Security and Privacy preferences, macOS may ask you to approve Blender the first time it opens.

To keep everything self-contained, install and config alike, set up a Portable Installation.

### Updating on macOS

There's one main way to update Blender on macOS. This section covers it.

### Updating from a DMG

When a release comes out, download it from the Blender website. Install it by writing over the current Blender.app in your Applications folder. Rename Blender.app or stash it elsewhere to keep several versions on hand at once.

See also

The Splash-screen Defaults page, on importing settings from earlier Blender versions and other quick options.

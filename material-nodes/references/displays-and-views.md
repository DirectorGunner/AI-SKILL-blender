# Displays And Views, Opencolorio, Render Baking

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Displays and Views; OpenColorIO; Render Baking.

## Displays and Views

### Displays and Views 

### Overview 

To put an image on screen, you carry it from scene linear over into a display color space, a move that mixes technical and artistic calls.

Which display color space fits is the technical call, hinging on the target device and its reach. sRGB serves every computer monitor, while digital cinema, HD TVs, and wide-gamut or HDR machines may ask for other picks.

No display covers the full color spectrum or lights up without bound, so colors must be tucked inside the device gamut. For that, Blender lays out a choice of views, each landing on its own look.

The artistic side stretches further through color management options like exposure and white balance, plus color grading back in the compositor.
.

Conversion from linear to display device space. 

### Displays 

This is the color space of whichever display your images and video are aimed at.

Ordinary computer monitors take sRGB, and most images and video live there.
Even so, today's panels often reach a wider gamut and carry high dynamic range content.

Standard Dynamic Range (SDR)

sRGB :

Basic display supported everywhere.

Display P3 :

Wide gamut for Apple devices and other modern displays.

Rec.1886 :

Used by many older TVs.

Rec.2020 :

Even wider gamut than P3 supported by some displays.

High Dynamic Range (HDR)

Rec.2100 PQ :

For HDR displays with Rec.2020 wide gamut, up to 10000 nits.

Rec.2100 HLG :

For HDR TVs with Rec.2020 wide gamut, up to 1000 nits.

### Wide Gamut 

To view wide gamut colors, choose the "Display P3" or "Rec.2020" display.

Run it alongside an "ACEScg" or "Linear Rec.2020" working space for your materials, lights, rendering and compositing.

Requirements:

- A P3 or Rec.2020 capable monitor.

- macOS: Any Apple Silicon device.

- Linux: Use Wayland, and set the Vulkan backend in the Blender system preferences.

- Windows: Enable "Automatically manage color for apps" in the Windows display settings,
and set the Vulkan backend in the Blender system preferences.

### High Dynamic Range 

To view high dynamic range (HDR) colors, choose the "Rec.2100 PQ" or "Rec.21000 HLG" display.

Under standard dynamic range (SDR), views drag bright colors way down to keep them in range.
HDR frees you to push beyond and show the scene more faithfully. Even HDR panels have a ceiling, so there are separate views for 500, 1000, 2000 and 4000 nits, each aimed at a different peak luminance.

In Blender, HDR content scales up and down with display brightness. Catching the whole range often means dimming the display to open headroom over SDR white.

Requirements:

- A HDR capable monitor.

- macOS: Any Apple Silicon device.

- Linux: Use Wayland, and set the Vulkan backend in the Blender system preferences.

- Windows: Enable "Use HDR" in the Windows display settings, and set the Vulkan backend in the Blender system
preferences.

### Display Emulation 

Automatic :

Shows images the way most other apps do, for previewing material headed to export. Blender works hard to emulate your chosen display on the actual device.

Off :

Sends the image straight out of OpenColorIO. Usually that misses, but it serves when you know your system and physical display already match the chosen display.

Emulation is not supported with older OpenColorIO configurations.

### Views 

Different ways to read the same image on one display.

Standard :

Beyond the display conversion itself it adds nothing. A frequent pick for non-photorealistic work or for video editing where the source already carries its own baked look.

ACES 1.3 :

The ACES view transforms,
a film-and-TV production mainstay. A good fit where you want photorealism.

ACES 2.0 :

The ACES view transform at version 2.0, wearing a more neutral look. Its tone scale eases off, dropping mid-tone contrast and softening highlight rolloff, while gamut mapping improves.

Khronos PBR Neutral :

A tone mapping transform aimed squarely at PBR color accuracy, so the render's output sRGB colors track the materials' input sRGB base color as closely as they can under gray-scale lighting. Its target is product photography, where exposure is even and HDR values keep to tiny specular highlights.

AgX :

A tone mapping transform that outdoes Filmic for more photorealistic output. AgX serves up 16.5 stops of dynamic range and bleeds saturation from heavily exposed colors to echo film's natural answer to light.

Filmic :

A tone mapping transform built for high dynamic range colors. Filmic is deprecated; AgX supersedes it and copes better with saturated colors.

Filmic Log :

Recasts the image into Filmic log color space. Good for handing off to color grading apps, or for studying an image by flattening its darkest and brightest stretches.

False Color :

Paints a heat map of image intensities, putting the dynamic range on view and helping you nail exposure.

The table that follows maps each band of normalized linear color data to the hue False Color paints it.

| Luminance Value | Color |
| Low Clip | Black |
| 0.0001% to 0.05% | Blue |
| 0.05% to 0.5% | Blue-Cyan |
| 0.5% to 5% | Cyan |
| 5% to 16% | Green-Cyan |
| 16% to 22% | Gray |
| 22% to 35% | Green-Yellow |
| 35% to 55% | Yellow |
| 55% to 80% | Orange |
| 80% to 97% | Red |
| High Clip | White |

Raw :

For studying an image, not for final export. Raw gives you the image with no color space conversion whatsoever.

### Look 

Pick an artistic effect drawn from measured film response data that loosely echoes the look of particular film stocks. It lands ahead of color space conversion.

### Exposure 

Rides the picture's brightness, in stops, before color space conversion runs.
It is calculated as follows: \(output\_value = render\_value × 2^{(exposure)}\)

### Gamma 

One more gamma correction, this one landing after color space conversion.
Since the default display transforms already do the right conversion, it mostly stands by as an artistic tweak.

### Curves 

Reach for RGB Curves to steer the image's colors ahead of color space conversion.
Read more about using the Curve Widget.

### White Balance 

Nudges colors so a chosen white point, set by color temperature and tint, reads as white on the display.

Rather than punching in values, you can grab the color picker.
Pick a color and temperature and tint settle so that color balances to white.
This holds only when the color lands close enough to a blackbody emitter.

You may also white balance through the compositing pipeline by way of the Color Balance Node

Temperature
The blackbody temperature of the lead illuminant. A D65 white point is the default.

Tint
How far the blackbody curve leans toward green or magenta.

Blackbody temperature curve. 

### Images 

### Display 

By default, only renders show up and save with the render View baked in.
These are the "Render Result" and "Viewer" image data-blocks, plus the files the Render Animation operator writes straight to disk.
Reopen a render stored as an intermediate OpenEXR file, though, and Blender cannot work out by itself that it is a render
(for all it knows, the file is an image texture or a displacement map).
The settings below are how we tell it the file is indeed a render and that the transformations should go on.

View as Render
Show the image data-block, renders included, with view, exposure, gamma and RGB curves applied.
Good for eyeing rendered frames in linear OpenEXR files just as they look fresh from the renderer.

### Output 

For saving files, a matching option waits.

Save as Render
A switch in the image save operator that lays on the view, exposure, gamma and RGB curves.
Good for writing linear OpenEXR out to, say, PNG or JPEG in display space.

These file formats accept wide gamut images: PNG, JPEG, WebP, AVIF, TIFF and JPEG 2000.

For HDR images the choices are AVIF or PNG. Blender writes them at 203 nits diffuse white, the convention most browsers and image viewers expect.

### Video 

### Output 

Video renders out in wide gamut and HDR color spaces alike. The scene display is the default, though overriding the color management settings in the output properties lets you assign another color space.

Writing out HDR video brings a handful of extra demands:

- Set color management display to Rec.2100 PQ or HLG

- Set codec to H.265 or AV1

- Set bit depth to 10 or 12

Players and devices vary in how far they support HDR video.
For the broadest reach, bit depth 10 alongside PQ encoding stands as a solid default.

For HDR video Blender uses 100 nits diffuse white, the convention most video players and browsers expect.

## OpenColorIO

### OpenColorIO 

Blender arrives with a standard OpenColorIO configuration that packs a handy set of display devices and view transforms.

OpenColorIO, though, is also built for a steady experience across many applications, and for that one shared configuration file can drive them all.
Blender reads the standard OCIO environment variable to load a configuration other than its own default. The OpenColorIO website spells out how to wire up such a workflow.

There is a second variable too, `BLENDER_OCIO` , which retargets the configuration for Blender alone. Where you can, favor OCIO so things stay compatible with other software and pipelines that may know nothing of `BLENDER_OCIO` . That said, configuration files now and then carry incompatibilities that make them awkward to share between applications.

### ACES 

Blender's standard configuration ships the essentials for ACES workflows: the ACEScg working space, the ACES 2.0 view transform, and OpenEXR images stored in the ACES2065-1 and ACEScg color spaces.

That handles most of what an ACES pipeline asks for. For fuller coverage, you can install the official ACES configurations by hand and select them through the OCIO environment variable.

### Roles 

scene_linear
The color space behind rendering, behind compositing, and behind every float precision image held in memory.

data
The color space set aside for data that is not color.

aces_interchange
The ACES2065-1 color space. It supplies the chromaticities the scene_linear color space derives, feeding effects like blackbody emission.

cie_xyz_d65_interchange
An intermediate display linear color space, bridging view transforms over to display color spaces.

color_picking
Shapes how colors spread across the color pickers. Expect it to run close to perceptually linear, carry the scene_linear gamut, and map 0..1 onto 0..1 in scene linear so material albedo edits behave predictably.

default_sequencer
The Sequencer's fallback color space, scene_linear where nothing is set.

default_byte
The fallback color space for byte precision images and files, texture_paint where nothing is set.

default_float
The fallback color space for float precision images and files, scene_linear where nothing is set.

### Writing Configurations for Blender 

Read to the letter, an OpenColorIO configuration omits a few things Blender relies on to run at its best.
Follow the pointers here to keep a configuration sound:

- Pair OpenColorIO v2 display_colorspaces and view_transforms with the cie_xyz_d65_interchange
intermediate display linear space. Blender draws on it to emulate the chosen display on the real one.
Lacking it, an older config switches display emulation off, leaving wide gamut and HDR display
shaky, and the colorspace metadata Blender saves for images and video hinges on it too.

- Give every display a view transform that skips tone mapping. Blender hunts for one
named Standard or Un-tone-mapped, or for the config-wide default_view_transform .
Coming up empty, it falls back to the display's first view transform. The point carries more weight
on OpenColorIO v1 configs lacking display_colorspaces , where it pins down an image's color space
once a view transform has been applied.

- Wherever you can, attach the interop ID from the Color Interop Forum
to each color space and display color space. Doing so lets image and video save
with the right colorspace information. Register the interop ID as an alias of the colorspace, and on
OpenColor 2.5 configs go further by setting the native interop_id attribute where you can.

- The icc_profile_name interchange attribute is honored, so ICC profiles can ride along when images save.

- Flag HDR displays by putting encoding: hdr-video on the matching colorspace.

- On HDR view transforms, work HDR 500 nits , HDR 1000 nits , HDR 2000 nits or HDR 4000 nits
into the name so maximum luminance for the mastering display metadata is read off automatically.

## Render Baking

### Render Baking 

Cycles lets you bake shaders and lighting down into image textures.
The usual reasons make a short list:

- Writing out base color, normal maps and similar textures so a game engine can take them.

- Laying down ambient occlusion or procedural textures to seed texture painting or later edits.

- Building light maps that supply global illumination, or that make a game render quicker.

### Setup 

Baking asks that the mesh own a UV map together with either a Color Attribute or an Image Texture node holding an image to receive the bake.
Whichever of the two is active, the Image Texture node or the Color Attribute, serves as the bake target.

Pull out Render Bake for demanding light and shadow work, AO say, or the soft shadows of area lights. Bake AO once for your main objects and you skip it on the full render, shaving render time.
Cycles bakes with the render settings (samples, bounces, …) in play.
So baked textures should land matching what the rendered scene gives back.

### Settings 

Reference

Panel :

Render ‣ Bake

Bake
Fires off the bake using whatever settings stand right now.

Bake from Multires
Bakes a Normal or Displacement map right off a mesh wearing a Multiresolution Modifier.

It sets two of the modifier's resolution levels side by side:

- Viewport Levels The coarse base mesh stands in here.

- Render Levels The fine, detailed mesh stands in here.

What the bake writes out is the gap between those levels, so finely sculpted detail ends up captured in a texture map.

Bake Type
Picks which surface information gets drawn out of the Multiresolution modifier.
See Bake Types for more information.

Normals :

Records how the surface normal direction differs between the two levels.

Displacement :

Records height differences as a grayscale displacement map.

Vector Displacement :

Records each point's full 3D offset, writing it out as a vector displacement map.

Bake Type
Which pass gets baked.

Combined :

Rolls in every material, texture and light bar specularity.
The passes feeding the combined pass can each be flipped on or off to shape the final map.

Ambient Occlusion :

Records ambient occlusion per the World panels, ignoring every scene light.

Shadow :

Captures the lighting along with the shadows it throws.

Position :

Writes world-space position into the RGB channels.
Each pixel carries the surface point's XYZ position, taken relative to the scene origin.

Normal :

Lays the normals down onto an RGB image.

UV :

The mapped UV coordinates, flagging where on a mesh a texture sits.
They ride the image's red and green channels; the blue channel holds a flat 1 and carries no data.

Roughness :

Writes out a material's roughness as its own pass.

Emit :

Writes out a material's Emission, its Glow color.

Environment :

Writes out the environment, namely the scene's world surface shader, onto whatever objects you chose, as rays fired from the world origin would see it.

Diffuse :

Writes out a material's diffuse component as its own pass.

Glossy :

Writes out a material's glossiness as its own pass.

Transmission :

Writes out a material's transmission as its own pass.

View From
Where the reflection rays set out.

Above Surface :

Cast the rays from over the surface.

Active Camera :

Cast the rays from where the active camera sits.

### Influence 

Combined

Lighting

Direct
Fold in the direct lighting.

Indirect
Fold in the indirect lighting.

Contributions

Diffuse
Fold in the diffuse share.

Glossy
Fold in the glossy share.

Transmission
Fold in the transmission share.

Emit
Fold in the emission share.

Diffuse, Glossy, Transmission

Contributions

Direct
See above.

Indirect
See above.

Color
Colorize the pass.

- Select Color on its own and you receive the pass color, a surface trait that holds no matter how far sampling refines.

- Leave Color off and the direct or indirect contributions come back in gray-scale.

- Turn on Color together with Direct or Indirect, and those contributions come back tinted.

Normal

Space
You can bake normals into any of a few spaces:

For materials, the same set of spaces sits in the image texture options, right beside the Normal Map setting already there. For a correct result, keep this choice in step with whatever you baked with.

Object :

Normals stated in object coordinates: object transformation leaves them be, while deformation does move them.

Tangent :

Normals stated in tangent space coordinates, untouched by object transformation and by deformation alike.
This is the default and the right call most of the time, because the normal map then carries over to animated objects too.

Swizzle R, G, B
Which axis lands in each of the red, green and blue channels.

### Selected to Active 

Bakes the shading off the selected objects' surfaces onto the active object.
The rays head inward from the low-poly object toward the high-poly one.
Where the high-poly object is not fully wrapped by the low-poly one, set where the rays start through Max Ray Distance or Extrusion (which one depends on whether you run a cage).
For tighter control still, bring in a Cage Object .

Note

Every object you bake from carries a fixed CPU memory cost. Join the high-poly objects before baking to keep memory from running out and crashing.

Cage
Fire the rays at the active object off a cage.
Picture the cage as the low-poly mesh puffed outward, formed for you from the ray distance or set up by hand from an object you point to.
Drop the cage and the rays ride the mesh normals, which litters the edges with glitches, yet that is the wiser route when you bake onto planes, since it spares you extra edge loops.

Cage Object
The object to stand in as cage, rather than deriving one from the active object with Cage Extrusion .

Cage Extrusion
The inward ray-cast distance once Selected to Active and Cage are both at work.
The inward rays fire from a copy of the active object with its Edge Split Modifiers off.
Keep clear of hard splits, an applied Edge Split Modifier for one, since they hand you non-smooth normals around the edges.

Note

When extruding the base mesh comes up short, copy that mesh and reshape the copy to serve as a Cage .
The two meshes must share one Topology, meaning an identical face count and face order.

Max Ray Distance
The inward ray-cast distance under Selected to Active .
On offer only when no Cage is running.

### Output 

Target
Where the baked map goes.

Image Textures :

Bake to the image data-block bound to the active, selected Image Texture node. Should a material carry no active, selected image texture node, nothing bakes for it.

Clear Image
When on, wipes the image clean before the bake render.

Active Color Attribute :

Send the bake into the active mesh's Active Color Attributes layer.
Mind that the active object has to be a mesh, since other object types own no Color Attributes.

### Margin 

When baking to images, Blender by default lays a margin around each UV "island."
This wards off breaks at UV seams that texture filtering and mip-mapping would otherwise bring.

Type
How the margin gets built.

Extend :

Push the border pixels out past the edge.

Adjacent Faces :

Pull pixels from the neighboring faces across each UV seam to pack the margin.

Size
The margin's width in pixels.

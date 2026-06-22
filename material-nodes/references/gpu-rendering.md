# Gpu Rendering, Light Settings Cycles, Material Settings, Object

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GPU Rendering; Light Settings (Cycles); Material Settings; Object.

## GPU Rendering

### GPU Rendering 

GPU rendering hands the work to your graphics card in place of the CPU . It often comes out faster, since modern GPUs are made to chew through huge amounts of arithmetic.
The catch: limited memory leaves them weaker on complex scenes, and sharing one card between display and rendering hurts interactivity.

To enable GPU rendering:

- Select either CUDA , OptiX , HIP , oneAPI , or Metal
in the Cycles Render Devices user preference.

- Enable the available devices for the chosen backend.

- Configure each scene to use the GPU Compute Device.

### Rendering Technologies 

Which GPU technology Blender can use turns on the particular GPU maker and the operating system.

### CUDA – NVIDIA 

CUDA runs on Windows and Linux and wants an NVIDIA graphics card of compute capability 5.0 or higher. To check yours makes the cut, see the list of NVIDIA graphics cards with their compute capabilities and supported cards.

### OptiX – NVIDIA 

OptiX runs on Windows and Linux, asking for an NVIDIA graphics card of compute capability 5.0 or higher plus a driver no older than 535. To check yours makes the cut, see the list of NVIDIA graphics cards.

OptiX taps the hardware ray-tracing acceleration in RTX cards for a performance lift.

OpenImageDenoise picks up GPU acceleration from compute capability 7.0 upward, which takes in every NVIDIA RTX card.

### HIP – AMD 

HIP runs on Windows and Linux and wants an AMD graphics card of the RDNA1 architecture or newer. It works on discrete GPUs and APUs both.

Supported GPUs include:

- Radeon RX 5000 Series

- Radeon RX 6000 Series and Radeon Pro W6000 Series

- Radeon RX 7000 Series and Radeon Pro W7000 Series

- Radeon RX 9000 Series

Minimum driver versions:

- Windows: Radeon Software 24.9.1 or Radeon PRO Software 24.Q4

- Linux: Radeon Software 23.40 or ROCm HIP Runtime 6.0

For more on AMD graphics cards and their architectures, check AMD's website.

The latest drivers carry hardware ray-tracing support. Switch it on in the preferences; Radeon RX 6000 and newer back it.

GPU accelerated denoising lands on discrete Radeon RX 6000 and newer.

### oneAPI – Intel 

oneAPI is a compute library running on Windows and Linux that wants an Intel® Arc™ graphics card on the Xe HPG architecture. Hardware acceleration spans both ray-tracing and denoising.

Supported GPUs include:

- Intel® Arc™ A-Series

- Intel® Arc™ B-Series

Minimum driver versions:

- Windows: Intel Graphics Driver XX.X.101.5518

- Linux: intel-level-zero-gpu package 1.3.27642,
typically available through the intel-compute-runtime package XX.XX.34666.3

For more on Intel graphics cards and their architectures, check Intel's website.

GPU accelerated denoising reaches every supported GPU.

### Metal – Apple (macOS) 

Metal drives GPU acceleration on Apple computers running Apple Silicon. The full feature set asks for macOS 13.0 or newer.

Apple Silicon picks up GPU accelerated ray-tracing and denoising.

### Limitations 

- No GPU backs Path Guiding.

- Among the backends only OptiX runs Open Shading Language, and the documentation notes some caveats there.

### Frequently Asked Questions 

### Why is Blender unresponsive during rendering? 

On older GPU generations a card can only render or paint the interface, not both, which is what can leave Blender frozen mid-render.
A heavy enough scene can stall Blender even on newer GPUs, where a flood of memory or pricey shaders is in play, though that worry is usually smaller.

The only full cure is one GPU dedicated to rendering and another to display.

### Why does a scene that renders on the CPU not render on the GPU? 

The reasons can be several, but the most common is the graphics card running short on memory.
As a rule a GPU is held to the memory aboard it
(see Would multiple GPUs increase available memory? for more information).
That is usually a far cry below the system memory the CPU reaches.
On CUDA, OptiX, HIP and Metal devices, Blender will reach for system memory on its own once GPU memory fills. That costs some performance but still tends to beat a CPU render.

### Can multiple GPUs be used for rendering? 

Yes. Head to Preferences ‣ System ‣ Compute Device Panel and set it up however you like.

### Would multiple GPUs increase available memory? 

As a rule no; a GPU reaches only the memory that belongs to it.

There is one exception: link NVIDIA GPUs over NVLink and they can pool memory, at a slight performance cost.
Switch this on through Distributed Memory Across Devices
in the preferences.

### What renders faster? 

It rides on the hardware at hand. Compute times also split between technologies according to the scene under test. For the freshest numbers on how various devices fare, browse the Blender Open Data resource.

### Error Messages 

When something goes wrong, be sure to fetch the official graphics drivers from the GPU maker's site, or via the package manager on Linux.
Drivers the computer maker bundles can run stale or come up short.

### Error: Out of memory 

Most often this signals that the GPU lacks the memory to hold the scene.

Note

Dropping texture resolution is one route to lighter memory use.
By way of example, 8k, 4k, 2k, and 1k image textures run 256MB, 64MB, 16MB and 4MB apiece.

### The NVIDIA OpenGL driver lost connection with the display driver 

When a single GPU serves both display and rendering, Windows puts a ceiling on how long that card may spend computing a render.
A heavy enough scene can let Cycles overrun the ceiling.
Trimming Tile Size in the Performance panel may take the edge off, though the real fix is separate cards for display and rendering.

Bumping the time-out up is the other route, though it does leave the interface draggier while a heavy scene renders.
Learn More Here.

### Unsupported GNU version 

On Linux this error can surface depending on the GCC version you run.
For the list of supported GCC versions, consult the NVIDIA CUDA Installation Guide for Linux. Two fixes are open to you:

Use an alternate compiler
Have an older GCC around that the installed CUDA toolkit version takes? Then swap it in for the default compiler.
You do that by setting the `CYCLES_CUDA_EXTRA_CFLAGS` environment variable as Blender launches.

Launch Blender from the command line as follows:

`	ext
`CYCLES_CUDA_EXTRA_CFLAGS`="-ccbin gcc-x.x" blender
`

(Substitute the name or path of the compatible GCC compiler).

Remove compatibility checks
If that gets nowhere, strike this line out of
/usr/local/cuda/include/host_config.h :

`	ext
#error -- unsupported GNU version! gcc x.x and up are not supported!
`

Doing so opens the way for Cycles to build the CUDA rendering kernel on its first run against your GPU. With the kernel built, launch Blender as usual and it keeps using that CUDA kernel to render.

### CUDA Error: Kernel compilation failed 

This one can crop up with a new NVIDIA graphics card the installed Blender version and CUDA toolkit do not yet know.
Blender may then try to build a kernel for your card on the fly and fall short.

In this case you can:

- Check if the latest Blender version
(official or experimental builds)
supports your graphics card.

- If you build Blender yourself, try to download and install a newer CUDA developer toolkit.

As a rule there is no need to install the CUDA toolkit, since Blender arrives with precompiled kernels.

## Light Settings (Cycles)

### Light Settings (Cycles) 

Reference

Panel :

Properties ‣ Object Data
and Shader Editor ‣ Sidebar ‣ Options

On top of the lighting thrown by the background and by any emission-shaded object, lights give you a further way to pour illumination into a scene.
The distinction is that they never show up directly in the rendered image, and being their own object type, they are tidier to handle.

### Light 

Settings that apply no matter which renderer is active.

### Beam Shape 

Spread Area Lights
The fan width of the emitted light, ruling how diffuse the area light reads.
Wider values bring soft shadows, narrower ones a crisper light like a gridded softbox.

Example of Spread at different angles. 

### Settings 

Max Bounces
The ceiling on how many times this light's rays may Bounce.
The scene-wide bounce settings cap it.

Cast Shadow
Switch this off and intervening objects stop blocking the light.
Skipping the rays traced to the light source can speed rendering up.

Multiple Importance Sample
Out of the box lights lean on direct light sampling alone. For area lights and sharp glossy reflections that can read noisy, so flipping this on folds in indirect light sampling to quiet the noise.

Shadow Caustics
Tags a light as a refractive caustic caster. Paired with the
Cast and Receive caustics object settings,
it lets you single out objects and quicken their refractive caustic rendering.

Portals Area Lights
Area lights can pull double duty as light portals, helping sample the environment light and cutting noise hard in interior scenes.
Portals usually render slower, yet they converge sooner, so they ask for fewer samples.

Flip on the Portal option, then set area lights into windows, door openings, and anywhere light spills into the interior.

Outdoors most rays barely bounce and just sail off into the sky, so light portals buy you nothing on outdoor scenes.

White Room model by Jay Hardy. 

### Nodes 

In Cycles, shader nodes can spell out a light in full.
That unlocks rich, physically based light behavior reaching well past the basic light settings.

Note

The basic Light settings ride on top of the light output node.

You edit light shader nodes in the Shader Editor once the editor is on Light context with a light object selected.

### Emission Shader 

To set what they put out, light objects run on an Emission shader.

What the Emission shader governs:

- Color : the emitted light's spectral hue.

- Strength : how intense that emitted light is.

The Emission shader's output has to run into the
Light Output node.

### Using Shader Nodes 

A light defaults to a plain node setup: one Emission shader feeding straight into the Light Output .

Bring in further shader and utility nodes and richer setups open up, for instance:

- Blending several Emission shaders so the light carries layered colors.

- Letting Texture nodes shift a light's color or intensity from one part of its surface to another.

- Steering a light's intensity or color through math nodes or animation.

That is the path to effects such as patterned lights, an animated flicker, or a light tinting itself by time or some other input.

### Light Output 

The Light Output node names the final shader the light object uses.
In Cycles, only shader nodes feeding this output sway how the light looks.

### Limitations 

- Only Cycles honors shader-based light definitions.
EEVEE runs on simplified light models and pays light shader node trees no mind.

- Lighting draws solely on Emission -based shading.
Hang any other shader type on a light, a BSDF shader say, and it does nothing.

Going the shader-node route for lights hands you fine-grained control and opens procedural lighting workflows that the standard light settings can never reach on their own.

## Material Settings

### Material Settings 

Reference

Panel :

Material ‣ Settings and Shader Editor ‣ Sidebar ‣ Settings

### Surface 

Displacement
The way Displacement is carried out on materials.

Displacement Only :

The mesh vertices move before the render, reshaping the actual mesh.
A finely subdivided mesh gives the cleanest result here.
It is also why this route eats the most memory.

Bump Only :

As the surface shader runs, a doctored surface normal fills in for the genuine one.
Lighter on memory than real displacement, yet only an approximation.
Surface silhouettes come out off, and the displacement throws no self-shadow.

Displacement and Bump :

Pair the two: displace a coarser mesh, then let bump mapping carry the fine detail.

Emission Sampling
How the material's emissive part gets sampled.
It bites only when the material holds an emissive material node; without one it is skipped.

None :

Keep this surface out of light sampling entirely.

Auto :

Let emission intensity decide on its own whether the surface counts as a sampling light.

Front :

Sample only the surface's front face as a light, handy on closed meshes whose inside is never seen.

Back :

Sample only the surface's rear face as a light.

Front and Back :

Sample the surface as a light off both faces, front and back alike.

Transparent Shadows
Use transparent shadows where a Transparent BSDF lives; turning it off renders quicker but skews the shadows.

Bump Map Correction
Lays on fixes for the shadow terminator artifacts bump mapping stirs up.

### Volume 

Sampling Method

Distance :

For dense volumes lit from afar, Distance sampling is usually the leaner pick.

Equiangular :

Park a light inside or near the volume and Equiangular sampling pulls ahead.

Multiple Importance :

Got a blend of the two? Then multiple importance sampling comes out best.

Interpolation
Which interpolation method serves the volume objects and the smoke simulation grids.

Linear :

A plain interpolation that does fine on thin volumes.

Cubic :

A smoothed, high-grade interpolation denser volumes need, at the cost of speed.

Step Rate Biased
Sets the spacing between volume shader samples for volume shaders.
You typically tighten the step for procedural shaders that pile on detail through procedural textures the default step misses.
Live only while Render ‣ Volumes ‣ Biased is on.
See Volume Render Settings for more information.

## Object

### Object 

### Visibility 

Reference

Panel :

Object Properties ‣ Visibility

See also

There are several other general visibility properties.

Mask – Shadow Catcher
Sets the object to soak up shadow rays and nothing else. Worth noting: shadow catcher objects still swap indirect light with other CG objects.
That smooths the job of dropping CGI elements into real-world footage.

Note

What the Shadow Catcher hands back depends on whether the Shadow Catcher pass is on in the Render Layer settings. With the pass on, every indirect light interaction is logged. With it off, a plain approximation stands in, and that approximation is what viewport rendering leans on.

Example of the shadow catcher. Note how the material of the plane can still be viewed in the spheres. 

### Ray Visibility 

Objects can be hidden from particular ray types.
One use is keeping an emitting mesh out of camera rays.
Instanced objects inherit this; hide the parent from some ray types and the children go hidden from those too.

On performance, these options beat a shader node setup chasing the same look.
An object invisible to a given ray drops out early in ray traversal, which trims ray casts and shader runs.

Camera
Lets the Camera see the object, the viewport's own view included while it renders.

Diffuse
Lets diffuse rays see the object.

Glossy
Lets glossy rays see the object.

Transmission
Lets transmission rays see the object.

Volume Scatter
Lets volumetric scatter rays see the object.

Shadow
Lets the object throw shadows.

### Culling 

To switch these on you first have to enable the matching camera cull options over in the scene simplify panel.

Use Camera Cull
Hide objects from rays by tossing out anything past the camera frustum.

Use Distance Cull
Drops any object sitting farther from the camera than a set distance. Married to camera frustum culling, it spares nearby objects that fall outside the frustum yet still surface in reflections. It is handy too for culling small objects far off.

### Motion Blur 

Reference

Panel :

Properties ‣ Object Properties ‣ Motion Blur

Each object keeps its own motion blur settings beside the Scene Level Motion Blur.
You will find them under the Object Properties tab of the Properties.

Note

This bears only on the object's own motion. Switch it off and motion blur from elsewhere, camera movement or animated focal length say, stays put.

Steps
Rules deformation motion blur accuracy; more steps draw more memory.
The actual number of time steps is \(2^{steps -1}\) .

Deformation
Turns motion blur on for deformed meshes, animated characters and hair among them.

Warning

A modifier setup that shuffles mesh topology over time cannot render deformation motion blur right. Switch deformation blur off for such objects.
Animated Booleans, plus Deformation ahead of Edge Split, Remesh, Skin or Decimate modifiers, are the usual suspects.

### Shading 

Reference

Panel :

Properties ‣ Object Properties ‣ Shading

### Shadow Terminator 

Geometry Offset
Lifts rays off the surface to rein in shadow terminator artifacts on low-poly geometry.
Higher values reach more triangles, one touching them all and zero touching none.
The default reaches only triangles at grazing angles to light and should clear away most artifacts.

Unlike the Shading Offset , this barely sways the lighting, which makes it the better way to handle shadow terminator artifacts.

Shading Offset
Shoves the shadow terminator, the line parting lit from dark, toward the light to bury artifacts on low-poly geometry like the ones below:

| Shadow Terminator Artifacts.  | Result of using an offset of 0.15.  |

Note

This setting fakes a change to the scene's lighting; it neither conserves energy nor holds physically accurate (lean on Geometry Offset instead).

### Fast GI Approximation 

AO Distance
Overrides the world's AO Distance; set it to zero and the world's distance applies.

### Caustics 

Tag objects as caustic casters or receivers. This pairs with a
Light or
World Shader carrying Shadow Caustics
to selectively quicken caustic rendering on objects in your scene.

Note

The speed-up for caustic rendering leans on
MNEE . Both that approach and its Cycles build come hedged with a number of limits:

- It handles refractive caustics living in object shadows and nothing more. Reflection caustics, or any caustic landing outside a shadow, simply go unrendered.

- Being an approximation, MNEE Caustics turn out physically wrong in plenty of cases, brightnesses that miss and a faulty take on caustics from rough or curved surfaces among them.

- Where a complex material packs several refractive BSDFs, only one of them gets caustics out of MNEE.

- Any Filter Glossy setting is disregarded once MNEE is doing the refractive caustics.

- An MNEE Caustic ray may cross at most 6 Caustic Caster surfaces on its way from a Caustic Receiver to a Shadow Caustic light; beyond that the ray dies and its caustics drop out.

- While the scene holds an active Caustic caster, Caustic receiver, and Shadow Caustic Light together, the Ambient Occlusion and Bevel nodes return nothing valid on any object acting as a Caustic caster or receiver.

- Smooth normals on the caustic caster are a prerequisite for MNEE Caustics to fire at all.

- The MNEE caustic calculation pays volumetric materials no attention.

- Bump and normal maps drop out of the caustic calculation as well.

Cast Shadow Caustics
Tag an object as a caustic caster.

Receive Shadow Caustics
Tag an object as a caustic receiver.

| Rendering caustics inside an eye without MNEE at 32 samples per pixel.  | Rendering caustics inside an eye using MNEE at 32 samples per pixel.  |

### Light Group 

Light Group
Pick the Light Group the current Object or Light should join.

Add Light Group
Type a name into the Light Group field that no existing Light Group bears, hit this button, and Blender spins up a Light Group under that name and drops the chosen Object or Light into it.

### Light Linking 

Through Light Linking, pen a light's reach to a named set of objects.

Receiver Collection
The collection of objects that take in light the object emits.

### Shadow Linking 

Through Light Linking, pen the shadows to a named set of objects.

Shadow Blocker Collection
The collection of objects standing as shadow blockers for light the object emits.

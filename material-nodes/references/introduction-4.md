# Introduction (part 4)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Introduction

### Liquid Simulations

Fluid simulation represents liquid physics, mainly water. Objects in a Blender scene can enter fluid simulations. Liquid sim requires a domain setting simulation volume bounds and global parameters (viscosity, gravity).

Example of a liquid simulation. 

### Gas Simulations

Gas/smoke simulation is fluid-system subset modeling airborne solids, liquid droplets, and vapors comprising smoke. It calculates fluid airflow and generates time-varying Voxel textures capturing density, heat, and velocity for particle/fluid visualization during rendering.

Example of a fire simulation. 

Gas/smoke emits in a Domain from meshes or particle systems. Airflow responds to Effector objects and scene gravity/fields. Airflow can influence other physics via Fluid Flow force fields.

### Workflow

Liquid and gas require a Domain and at minimum one Flow object.

- Establish a Domain encompassing the simulation volume.

- Form Flow objects releasing fluid.

- Compose Effector objects for fluid interaction.

- Attach material to the domain.

- Save the .blend file.

- Bake Cache for simulation.

Note

Quick Liquid and Quick Smoke auto-create a domain with foundational liquid or smoke-and-fire material.

### Introduction 

Blender's physics infrastructure enables simulation of numerous real-world behaviors. These capabilities facilitate both static and dynamic effects including:

- Hair, grass, and flocks

- Rain

- Smoke and dust

- Water

- Cloth

- Jello

- etc.

### Quick Effects 

Reference

Editor :

3D Viewport

Mode :

Object Mode

Menu :

Object ‣ Quick Effects

Automatically constructs fundamental simulation configurations, pre-populating with essential components like domains or particle systems bearing predefined parameters. This approach delivers immediate visible results.

### Quick Fur 

Applies a fur configuration to target objects. The fur system builds on Geometry Nodes, utilizing Hair Node Groups bundled with Blender as native resources.

Density

The surface density of hair curves to generate.

Length

The span of produced hair curves.

Hair Radius

The width measurement of hair, used by rendering engines.

View Percentage

Density scale factor applied in the viewport.

Apply Hair Curves

Executes the modifier employing the Generate Hair Curves node group.

Noise

Applies noise-based deformation to hair curves. Inspect the Hair Curves Noise node group for implementation details.

Frizz

Uses random vectors per point to disorder hair curves. Reference the Frizz Hair Curves node group.

### Introduction 

Soft-body simulation models deformable-object behavior.
Originally designed for secondary-motion animation—character body jiggle—it extends to general soft objects that bend, deform, and respond to forces: gravity, wind, object collisions.

While soft-body simulation handles cloth to an extent, Cloth Simulation excels with dedicated solvers.

The simulation combines existing animation with acting forces—external (gravity, force fields) and interior (vertex connection forces).
This generates realistic object shapes as though possessing volume, internal fill, and external force effects.

Soft bodies interact with objects via Collision and with themselves via Self-Collision.

Convert soft-body simulation results to static objects or edit intermediate results and continue simulation.

### Typical Scenarios for using Soft Bodies 

The wind cone is a soft body, as the suspension. 

Animation

Soft bodies excel at:

- Character body jiggle.

- Elastic, deformable rubber or gelatin objects.

- Wind-blown tree branches, swinging ropes, etc.

- Flags, flowing sleeves, cushions, and fabric reacting to forces.

### Creating a Soft Body 

Soft-body simulation applies to objects with vertices or control points: meshes, curves, surfaces, lattices.

Activate soft-body simulation via Physics tab's Soft Body button.
Reference all settings here.

Start simulation with Alt - A playback; stop with Esc or Alt - A.

### Interaction in Real-Time 

The Timeline editor facilitates soft-body work.
Switch between frames; simulation displays current state.
Real-time interaction occurs: move collision objects, shake soft bodies.

While simulating, select the soft body and Apply the modifier in Properties Modifiers to permanentize deformation.

### Tips 

- Even vertex distribution optimizes soft bodies.
Sufficient vertices enable good collision. Add vertices in regions affecting stiffness deformation.

- Collision calculation may prove expensive. Skip invisible calculations.

- Accelerate collision calculation with simplified additional invisible larger objects.

- Apply soft bodies selectively.
Tight-cloth animation via soft-body alone typically fails. Self-collision for soft-body hair activates but requires careful handling.
Collisions appear later.

- Lattice or Curve Guide soft bodies often outpace object soft bodies significantly.

### Introduction 

Cycles is the physically-based path tracer Blender brings to production rendering.
It sets out to hand you physically based output from the start, paired with artistic control and the flexible shading nodes production work calls for.

To put Cycles to work, set it as the Render Engine over in the Render properties.
When you want the rendering GPU accelerated,
switch on compatible devices under Preferences ‣ System ‣ Cycles Render Devices .

See also

The Cycles website with more information and a gallery.

### Introduction

EEVEE functions as Blender's real-time rendering engine, optimized for rapid, responsive output while achieving PBR material goals. Simultaneously interactive in the 3D Viewport and capable of generating refined final renders.

EEVEE materials employ identical shader nodes as Cycles, streamlining scene porting. For Cycles artists, EEVEE accelerates material prototyping in real-time.

EEVEE rests on rasterization rather than path tracing. Instead of computing every light ray, rasterization identifies camera-visible surfaces, then approximates light interactions using various algorithms. While EEVEE embraces PBR ideas, Cycles remains more physically faithful. Consequently, EEVEE carries specific constraints.

EEVEE final render – "Temple" by Dominik Graf.

Introduction — Freestyle NPR Engine

Freestyle is an edge/line-based non-photorealistic (NPR) rendering system. It leverages mesh data and Z-depth to draw lines on chosen edge types. Varied line styling produces artistic (hand-drawn, painted, etc.) or technical (hard-line) visuals.

Freestyle supports rich stylization diversity. Two methods define line appearance. First: parameter-based Line Style creation, allowing intuitive editing of dotted lines and straightforward multi-line type setup. Style modifiers expand possibilities limitlessly. Second: Python scripting for advanced stylization. Blender includes pre-made styles like Japanese big brush, cartoon, blueprint, and thickness-with-depth.

| ATV buggy by Rylan Wright (RONIN). . (File:AtvBuggy.zip) | By mato.sus304. -SA. (File:Mato_sus304_cut02.zip) |
| Cartoon scene from OHA Studio © Mechanimotion Entertainment. (blend-file) | Blueprint render of Martin M-130 from 1935 by LightBWK. CC0. Warning: heavy file; stress tests Blender and may crash. Designed for limits testing. (File:M-130Blueprint.zip) |

### The Big Picture

- Toggle Freestyle via Properties ‣ Render ‣ Freestyle checkbox.
- Freestyle options reside in View Layer properties.
- Each view layer has one view map. A view map holds edge detection parameters (Crease Angle, Culling toggle, Face Smoothness toggle, Material Boundaries toggle, Sphere Radius, Kr Derivative Epsilon advanced options).
- A view map can hold multiple Line Sets.
- A line set determines which line types and selections render from your scene.
- Each line set links to one line style (shareable across multiple Line Sets).
- A line style tells Freestyle how to render linked Line Sets regarding color, alpha, thickness, and other traits.

Block diagram of Freestyle view map and processes.

### Known Limitations

- Memory intensive: All view layer mesh objects load simultaneously.
- Only faced mesh objects are supported.
- Mesh intersection edges are not yet detected.
- Freestyle rendering lacks Z depth information.
- Panoramic cameras are unsupported.

### Introduction

The act of rendering converts a three-dimensional scene representation into a two-dimensional image.
Blender supplies three distinct rendering engines, each optimized for particular use cases:

- EEVEE provides a physically accurate real-time rendering solution.

- Cycles implements a physically accurate path-tracing renderer.

- Workbench focuses on tasks involving spatial arrangement, surface geometry, and display preview.

Third-party suppliers make additional renderers available through add-ons.
Each engine offers its own set of configuration options to govern output fidelity and speed.

Cameras, lights, and material definitions set the visual characteristics of a render.
These fundamental elements are shared by both EEVEE and Cycles, though specific capabilities exist only on one or the other platform.

Rendering can be segmented into component layers and intermediate data streams that compose individually for artistic variation or blending with external imagery. Non-photorealistic edge stylization can be added via Freestyle.

Blender enables real-time 3D display rendering through all engine variants, supporting fast experimentation with illumination and surface properties. Following interactive refinement, final-quality output or animation can be rendered and stored.

### Introduction

View Layers allow you to separate a render into multiple layers, which can then be composited together. This is useful for rendering scene elements independently—such as characters, lighting variations, or background elements—without duplicating the entire scene or re-rendering everything after each change.

For example, you can:

- Apply different compositing effects to foreground and background elements.

- Render characters separately from the environment for post-processing.

- Generate multiple lighting passes without modifying the original scene setup.

View Layers also improve performance and flexibility during iteration by letting you re-render only the layers that have changed.

View Layers and collections.

Each View Layer references a combination of Collections, which define the visibility, selectability, and contribution of scene objects in the final render. Multiple View Layers can use the same or different collections, allowing for tailored layer setups.

### Selecting View Layers

At the top of the View Layer Properties tab is a list of all View Layers in the active scene.

View Layers list.

Name
The name of the active View Layer. Click to edit.

Add View Layer
Adds a new View Layer to the scene.

- New : Adds an empty View Layer.

- Copy Settings : Duplicates the current View Layer, including collection visibility and overrides.

- Blank : Adds a new View Layer with all collections disabled.

Remove View Layer
Deletes the selected View Layer from the scene.

Note

Each scene must contain at least one View Layer.

### Usage

### Visibility Management

Each Scene consists of one or more Collections. Collections can be enabled or disabled per View Layer, allowing you to control what appears in each layer's render.

This makes it easy to separate lighting, characters, props, or effects into their own passes.

Collection visibility for each View Layer can be adjusted in the Outliner or Collection View Layer Properties.

View Layer collections in the Outliner.

From the Outliner, you can:

- Enable or disable collections per View Layer.

- Set holdout and indirect-only options (Cycles only).

- Manage what objects contribute to the render or compositing.

### Rendering & Compositing

When a scene is rendered, each View Layer is available in the Compositor using the Render Layers Node. This allows you to process each layer independently, combining or adjusting them to create the final output.

Each View Layer can output multiple Render Passes including:

- Combined (final image)

- Diffuse, Glossy, Transmission components

- Shadow, Mist, Ambient Occlusion

- Cryptomatte and Object/Material/ID Masks

- Data passes like Normal, UV, and Depth

These passes make it possible to perform detailed color grading, masking, relighting, and other post-processing operations in a non-destructive workflow.

### Introduction

Materials control the appearance of meshes, curves, volumes and other objects. They define the substance that the object is made of, its color and texture, and how light interacts with it.

Physically based materials can be created using the Principled BSDF, Principled Hair, and Principled Volume shaders. With these uber shaders, a wide variety of materials including plastic, glass, metal, cloth, skin, hair, smoke and fire can be created.

A flexible shading nodes system is used to set up textures and create entirely different types of materials like toon shading.

### Setting up Materials

Materials can be created in either the Material properties, or in the Shader Editor. These provide a different view of the same shader nodes and material settings.

The default Shading workspace has a Shader Editor and a 3D Viewport that can be set to Material Preview or Rendered shading, to interactively preview how the material interacts with objects and lights in the scene.

Materials are data-blocks that can be assigned to one or more objects, and different materials can be assigned to different parts of meshes.

Image textures can be created from scratch in Texture Paint Mode, or by loading in existing images with the Image Texture node. A variety of procedural texture nodes is also available.

### Components

Materials consist of three shaders, defining the appearance of the surface, the volume inside the object, and the displacement of the surface.

### Surface Shader

The surface shader controls the textures and light interaction at the surface of the mesh.

### Volume Shader

The volume shader defines the interior of the mesh. A material can have just a volume shader for cases like smoke and fire, or it can be combined with a surface shader for materials like cloudy glass.

### Displacement

The shape of the surface and the volume inside it may be altered by displacement. This way, textures can then be used to make the mesh surface more detailed.

Depending on the settings, the displacement may be virtual, only modifying the surface normals to give the impression of displacement, which is known as bump mapping, or a combination of real and virtual displacement.

### Physically Based Shading

The material system is built with physically-based rendering in mind, separating how a material looks and which rendering algorithm is used to render it. This makes it easier to achieve realistic results and balanced lighting, though there are a few things to keep in mind.

In order for materials to work well with global illumination, they should be energy conserving. That means they cannot reflect more light than comes in. This property is not strictly enforced, but if colors are in the range 0.0 to 1.0, and BSDF s are only mixed together with the Mix Shader node, this will automatically be true.

It is however, possible to break this, with color values higher than 1.0 or using the Add Shader node, but one must be careful when doing this to keep materials behaving predictably under various lighting conditions.

### Introduction

The Texture Type list in the Texture panel of the Texture buttons.

Procedural textures are textures that are defined mathematically. They are generally relatively simple to use, because they do not need to be mapped in a special way. This does not mean that procedural textures cannot become very complex.

These types of textures are 'real' 3D. By that we mean that they fit together perfectly at the edges and continue to look like what they are meant to look like even when they are cut; as if a block of wood had really been cut in two. Procedural textures are not filtered or anti-aliased. This is hardly ever a problem: the user can easily keep the specified frequencies within acceptable limits.

### Common Options

### Noise Basis

Each noise-based Blender texture (except Voronoi and Simple Noise) has a Noise Basis setting that allows the user to select which algorithm is used to generate the texture. This list includes the original Blender noise algorithm. The Noise Basis settings makes the procedural textures extremely flexible (especially Musgrave ).

The Noise Basis governs the structural appearance of the texture:

| Blender Original. | Voronoi F1. | Voronoi F2-F1. |
| Original Perlin. | Voronoi F2. | Voronoi Crackle. |
| Improved Perlin. | Voronoi F3. | Cell Noise. |
| Voronoi F4. | | |

There are two more possible settings for Noise Basis , which are relatively similar to Blender Original : Improved Perlin and Original Perlin.

### Nabla

Almost all procedural textures in Blender use derivatives for calculating normals for texture mapping (except Blend and Magic ). This is important for Normal and Displacement Maps. The strength of the effect is controlled with the Nabla number field.

### Hints

Procedural textures can either produce colored textures, intensity only textures, textures with alpha values and normal textures. If intensity only ones are used the result is a black-and-white texture, which can be greatly enhanced by the use of ramps. If on the other hand you use ramps and need an intensity value, you have to switch on No RGB in the Mapping panel.

### Introduction 

Configuring render output is the initial step in the rendering process. This encompasses render resolution, frame rate, pixel aspect ratio, file destination, and format selection.

For single-frame renders, output should be an image format rather than video. Multiple image formats are supported.

Image formats offer benefits for animation rendering. For instance, rendering animations to image sequences allows you to stop and resume jobs at the last completed frame by adjusting the frame range. This becomes valuable for lengthy rendering tasks when computer resources are needed elsewhere.

Image sequences can subsequently be assembled into video using the Video Sequencer with an appropriate codec setting.

Tip

Rendered image sequences can be reviewed in the Animation Player.

See also

See Render Menu

### Introduction

Define materials, lights and backgrounds using shading node networks. These nodes output values, vectors, colors, and shaders.

### Shaders

The shader socket is a core concept: surface and volume shaders output a shader—a description of lighting interaction—not a surface color. The renderer uses this to compute all light interactions for direct lighting and global illumination.

**Shader types:**

- **BSDF shader** — Describes reflection, refraction and absorption at surfaces.
- **Emission shader** — Describes surface or volumetric light emission.
- **Volume shader** — Describes volumetric light scattering.
- **Background shader** — Describes environmental light emission.

Each shader node has a color input and outputs a shader. Mix and Add Shader nodes combine them; no other operations are allowed. The resulting output feeds the renderer's light computation.

See also: Shaders

### Textures

Blender provides built-in procedural texture nodes. No texture data-blocks are needed; node groups handle texture reuse.

For UV mapping and texture painting in the 3D Viewport, use the Image Texture node. When set as active, it displays in the viewport using Texture color mode—useful for previewing painted textures.

Default coordinates are Generated for most nodes, except Image textures (which default to UV). Each node includes options to modify texture mapping and output color, editable in texture properties.

See also: Textures

### More

Vector Nodes, Color Nodes, and Utilities Nodes cover geometric data, texture coordinates, shader layering, and non-physical tricks.

### Open Shading Language

Cycles supports custom nodes via Open Shading Language.

### Introduction

Workbench is a viewport shading engine optimized for responsive display during modeling and animation work. It is not designed for final image output, serving primarily to display the scene while being edited.

Note

Though not intended for final renders, Workbench can be selected as the Render Engine in Render properties.

By default the 3D Viewport employs Workbench shading. Unlike EEVEE and Cycles, Workbench does not use shader nodes. Instead, shading adjustments occur in the 3D Viewport Shading menu or render settings for final output.

Workbench supports random color assignment for objects to distinguish them visually. Other available coloring schemes include materials, Color Attributes, and textures.

Workbench offers X-ray rendering for object transparency, plus cavity and shadow shading for geometric detail emphasis. Several lighting options exist, including studio configurations and MatCaps.

The following example showcases Workbench's strengths: random coloring paired with shadows reveals geometric detail effectively.

Workbench example.

### Introduction

Brushes are the main way of interacting with any painting and sculpting mode. By click & dragging in the 3D Viewport (or the Image Editor when using Texture Paint), the active brush creates a stroke with a certain effect, depending on the used brush settings. Brushes are used as brush assets and stored in asset libraries, which makes it easy to reuse and share them. Typically they have a preview image and a name that indicate the effect they create.

Tip

It is highly recommended to use a Graphics Tablet for a better brush feel and additional features.

### Accessing Brushes

In modes that use painting or sculpting functionality, the Asset Shelf of the 3D Viewport and Image Editor displays brush assets that can be used in that mode. Clicking a brush asset will activate the Brush Tool if necessary, with the clicked brush set.

The Asset Shelf of the 3D Viewport, providing access to brush assets.

This asset shelf is also available as popup in the Tool Settings, the Sidebar, Properties and using a shortcut.

Reference

Mode :

All Paint Modes

Header :

Tool Settings

Panel :

Sidebar ‣ Tool ‣ Brush Asset ,
Properties ‣ Tool ‣ Brush Asset

Shortcut :

Shift - Spacebar

### Brush Control

These are the most common hotkeys for controlling the brush.

- Set brush size F

- Set brush strength Shift - F

- Rotate brush texture / Set brush weight Ctrl - F

After pressing these hotkeys, you can then either adjust the value interactively or by typing in numbers. Move the mouse right or left to increase/reduce the value (additionally with precision ( Shift ) and/or snapping ( Ctrl ) activated). Finally confirm ( LMB , Return ) or cancel ( RMB , Esc ).

You can also invert the brush direction/effect by holding Ctrl .

### Custom Brush Shortcuts

To give a brush a shortcut, simply right click it in the asset shelf or brush selector popup, and select Assign Shortcut . To modify or remove an existing shortcut, select Change Shortcut or Remove Shortcut accordingly.

### Brush Assets

Brushes are used as assets, and stored in asset libraries. This makes the brushes shared across project files. All available brush assets can be displayed in the Asset Browser, which also provides ways to organize them.

Blender comes bundled with a number of brushes in the Essentials asset library. These can be customized into all kinds of custom brushes by duplicating them (see Brush Editing).

While it's possible to have brush data-blocks that are local to the file and not marked as assets, such brushes cannot be activated for actual painting or sculpting. Use the Mark as Asset operator to make them brush assets that can be activated.

### Brush Tool

The Brush tool.

Painting or sculpting with brushes requires the brush tool to be active. Activating a brush from an asset shelf or brush selector also activates the brush tool for convenience.

# Introduction (part 5)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Introduction

Sculpting and painting offers a more freeform workflow of editing via brushes. There are several modes to do this, each with their own purpose.

- Sculpting:
Change and transform the topology of your mesh.

- Vertex Paint:
Change the color of vertices in the active Color Attribute.

- Weight Paint:
Change the weight of vertices in the active vertex group.

- Texture Paint:
Change the pixels of the active image texture.

### Introduction

A UV texture is an image (still frame, animation sequence, or video file) that colors the mesh surface. UV mapping connects the texture to the mesh through one or multiple UV coordinate layers. Image assignment for UV textures follows three approaches:

- Import artwork using an external program, then load it into the Image Editor, associating it with the UV texture. Blender then employs that texture's UV mapping to apply the colors to mesh surfaces.

- Create a fresh image within the Image Editor and paint on it flat, using the UV texture's mapping to color mesh surfaces.

- Paint the mesh in the 3D Viewport while Blender automatically updates the UV texture via the active UV mapping (covered subsequently).

Blender includes Texture Paint mode, purpose-built for quick UV texture editing and creation in the Image Editor or 3D Viewport. Alternatively, exterior painting applications like GIMP or Krita work equally well, since UV textures are simply images.

Texture painting in Blender.

A single mesh may carry multiple UV texture layers, resulting in numerous images that shade the mesh. However, each UV texture maps to a single image.

Texture Paint functions in both a 3D Viewport and the Image Editor. Using 3D Viewport Texture Paint, you paint surface detail by projecting onto the UVs.

Tip

Memory Optimization

Texture Paint remains fast and fluid when operating in the 3D Viewport and your image dimensions equal a power of two (like 256×256, 512×512, 1024×1024, etc.).

### Getting Started

The target object requires unwrapping first. Unwrapping methods include standard UV Unwrapping Tools or automatic Simple UVs from Texture Paint mode.

Note

When no UV layers are present, Blender will alert you with an alert message.

With a unwrapped model, you're prepared to begin painting. Start via any approach:

- Activate the Texture Paint workspace. The Viewport uses Texture Paint Mode and the Image Editor is set to Paint mode.

- From the Viewport header, change to Texture Paint Mode, then paint the mesh directly.

- In the Image Editor, set Paint mode (visible in the screenshot to the right).

Enabling Paint mode.

Activating Texture Painting converts your mouse into a brush. Once engaged, various tools appear in the Toolbar.

Within the Image Editor, you paint on a 2D surface that wraps around the mesh via UV placement. Any Image Editor edits immediately show in the Viewport, and vice versa.

To adjust UV layout (relocating coordinates), utilize the UV Editor.

Complete brush and color choices are accessible from the Sidebar in the Image Editor. Changes in either location instantly transfer. However, textures require explicit saving via Save Image.

### Texture Preview

If your texture already applies color, bump effects, displacement, transparency, etc. to a surface (is paired to a texture aspect through a texture channel using UV mapping), you see the results in real-time as you paint.

Arrange side-by-side Viewport areas: set one to Texture shading and position a second area to show the Image Editor holding your texture. Show the textured model in the Viewport. The right-side illustration shows bump mapping in action, where grayscale pixels simulate surface relief. Consult Texture Mapping Output for bump mapping details.

### Saving

When Image header shows an asterisk, the image has modifications but hasn't been saved. Employ Save Image or Save Image As to store your work with alternate naming or to overwrite the original.

Note

UV Textures

UV texture images differ functionally from other images and should be organized in separate directory structures.

Saved file format differs from rendering format. The UV image save format is selected via the File Browser header and typically defaults to PNG (.png).

If the File Browser header has Packing enabled or you pack manually, isolated storage becomes unnecessary.

### Using an External Image Editor

When using exterior software to edit UV textures:

- Launch the paint application (GIMP, Krita, etc.).

- Open or establish an image.

- Make modifications.

- Export within that program.

- Within Blender, reimport via the Image Editor.

External tools suit situations where groups collaborate across different platforms, specialized effects beyond Texture Paint capabilities are needed, or you favor a different interface.

### Known Limitations

### UV Overlap

Typically overlapping UVs lack support (like texture baking).

This becomes relevant only when a single brush path colors numerous faces referencing the same texture.

### Introduction

### Perspective View & Faces Behind the View

When painting faces partly outside the perspective view, those faces resist painting. To fix this, back away or switch to orthographic perspective.

### Perspective View & Low Poly

In perspective mode, painting low-resolution objects with normals pointing away from you may fail; deactivate Normal Falloff in stroke settings to work around this.

Typically happens when painting cube sides (see Blender bug #34665).

### Introduction

Vertex Painting constitutes a direct approach to applying color to objects by modifying vertex pigmentation rather than texture data. It operates straightforwardly. Vertex Painting saves color information as a Color Attribute, usable by various rendering systems.

Color attribute selections appear in the header's palette selector.

Vertex Painting Mode.

As a vertex receives color application, the vertex pigmentation changes per brush parameters. The pigmentation flows across all exposed faces and edges touching that vertex, transitioning toward adjacent vertex colors. Occluded face coloring remains unchanged.

See also

Dynamic Paint
can create Color Attribute information during physics and animation playback.

### Viewing Color Attributes

Within material node systems, Color Attributes are available via the Color Attribute Node.

Color Attributes display in the 3D viewport through the Workbench engine. Activate this: switch the Viewport to Solid Shading and select Attribute Color option.

### Introduction

A strip functions as a container holding frames sourced from one or multiple inputs. It spans from a Start Frame to a defined Length and appears as a colored horizontal band in the display.

Strip schematic.

### Adding Strips

Reference

Menu: Add

Shortcut: Shift-A

The Add Menu.

The Add menu serves as the primary interface for inserting content into the Video Sequencer. Access it from the Sequencer header or by hovering over the workspace and pressing Shift-A.

Generally, the workflow involves loading video and audio media, inserting effects and transitions, and composing your edit by arranging and timing these elements. When adding content requiring external files, a file browser opens for selection, with compatible formats automatically filtered.

The Add menu also provides a Search… function, enabling rapid lookup and insertion of strips by name, matching conventions in other software.

Newly created strips begin at the playhead's current position. Adding multiple media items (videos, sounds) simultaneously places each sequentially.

### Adding Effects & Transitions

Blender includes a collection of effect strips for enhancing sequences.

To add an effect, select one source strip (video, image, or scene) by left-clicking. Some effects, like Cross transitions, need Shift-left-click on a second overlapping strip (depending on the effect type). Open the Add menu and choose your effect. The effect strip appears above the inputs. Independent effects like Color Generator position at the playhead.

Note

Most effect strips depend on one or two source strips, so their frame span and duration come from the inputs. Moving them directly may not work; adjust the input strips instead. With some effects, like Alpha Over, the selection order is significant. An effect strip can feed into another, creating layered effects.

If you select the wrong effect, use Effect Strip to swap it. Some effects like Brightness/Contrast and Hue/Saturation can be used through Strip Modifiers.

### Visualization

Strip types are assigned specific colors in the Video Sequencer display:

- Scene strip: Pale green.

- Clip strip: Navy blue.

- Mask strip: Bright red.

- Movie strip: Cyan.

- Image strip: Violet.

- Sound strip: Light blue-green.

Effect strips each have their own distinct color.

Apart from these defaults, individual strips can get custom colors via Strip Properties.

Note

Color assignment follows the active interface theme. The colors listed refer to Blender's standard theme.

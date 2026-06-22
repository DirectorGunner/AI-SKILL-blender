# Text Properties, Objects Panel, Dope Sheet View, Graph View ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Text Properties; Objects Panel; Dope Sheet View; Graph View; Cache; Mesh; Particles; Gravity.

## Text Properties

### Text Properties

### Shape

Reference

Mode :

All Modes

Panel :

Properties ‣ Data ‣ Shape

Most settings in the Shape panel come straight from the
Curves
data-blocks, so check there for the details.

Fill Solver
Which triangulation method handles the filling of 2D curves.

Sweep Line :

A quick triangulation approach meant for tidy, well-behaved outlines.
It can't cope with curves that cross themselves.

Delaunay :

Relies on Constrained Delaunay Triangulation (CDT).
Sturdier and able to handle self-intersecting curves, though it runs slower.

Important

Since most font files contain self-intersecting curves,
Delaunay is the recommended choice
whenever you work with text objects.

Fill Rule
Which rule the Delaunay Fill Solver applies to decide which regions count as inside.

Even-Odd :

Flips between inside and outside according to how many boundary crossings there are.
Overlapping regions can cancel one another out, depending on the crossing tally.

Non-Zero :

Settles inside versus outside from the winding direction.
Overlapping curves winding the same way merge into a union,
while curves winding the opposite way can punch out holes.

Fast Editing
Skips filling the letters in Edit Mode and shows only their outline.

### Texture Space

Every Object can carry an automatically generated UV map, which you tweak here.

See Generated UV Properties for more information.

### Geometry

Reference

Mode :

All Modes

Panel :

Properties ‣ Data ‣ Geometry

Offset
Shifts the control points of the curves that define the letters, thinning or thickening them.
Handle it carefully, since artifacts crop up fast…

### Extrusion, Taper & Bevel

The panel's remaining settings, the ones that add volume to the letters,
likewise come from the Curves data-blocks,
so check there for the details.

Note

Exactly how the Taper object effect plays out hinges on how the curves defining the letters are built.
The outcome can look pretty unpredictable…

Note

Bevel acts on the curves that define the letters,
so it generally traces their outlines
(yielding two parallel beveled curves rather than the single one you might expect).

### Font

Reference

Mode :

All Modes

Panel :

Properties ‣ Data ‣ Font

By default Blender ships with a built-in font that turns up in
each of the four font-style data-block menus.
Always available, this built-in font appears in the list as "Bfont".
The data-block menu itself lists whatever fonts are currently loaded.
Pick one per font style.

To swap in a different Font , press a Load button
over in the Font panel, then browse your way to a font file.
In the File Browser every valid font gets a capital "F" icon.

Pick a font Blender can't handle and you'll see the error Not a valid font .

Note

Location of Fonts on Unix

You'll usually find fonts under /usr/lib/fonts , or a variant such as /usr/lib/X11/fonts ,
though not always. Other spots are possible too,
like /usr/share/local or /usr/local/share , along with related sub-trees.

Keep in mind that one font covers every character of the same style in a text,
yet each style needs its own font.
To italicize characters or words, for example, you'll have to load an Italics font.
With the font loaded, you then apply that font "Style" to the selected characters or to the whole object.
All told, representing every style means loading at least four different fonts
(Normal, Italics, Bold, Bold & Italics).

It's worth grasping that Blender doesn't mind which font
you assign to "normal", "bold", and so on.
That's how a single text can run as many as four different fonts at once,
though you do have to settle on either different styles of one font or different fonts.
Blender's typographic controls for adjusting the style and layout of text
sit in the Font panel.

Bold
With nothing selected, switches whether freshly typed text comes out bold .
With text selected, switches the selected text between bold and not.

You can also flip Bold on or off straight from the 3D Viewport via Toggle Bold.

Italic
With nothing selected, switches whether freshly typed text comes out italic .
With text selected, switches the selected text between italic and not.

Flipping Italic is likewise available in the 3D Viewport through Toggle Italic.

Underline
With nothing selected, switches whether freshly typed text comes out underlined.
With text selected, switches the selected text between underlined and not.

Underline can be flipped from the 3D Viewport as well, using Toggle Underline.

See also underline settings below.

Small Caps
With nothing selected, switches whether freshly typed text comes out in small capitals.
With text selected, switches the selected text into small capitals or back.

The 3D Viewport offers a Toggle Small Caps for flipping Small Caps too.

You can also drop text into small caps by selecting it and reaching for Toggle Small Caps.

How large the Small Caps end up is governed by Small Caps Scale.

### Transform

Size
Drives the size of the text as a whole (there's no sizing each character on its own).
Note, though, that characters in different fonts (different styles, see below) may turn up at different sizes.

Shear
Drives how far the whole text leans over.
Close as it looks, this isn't the same as the italics style.

Shear example.

Object Font
Lets you press your own objects into service as the font, so you can build a complex custom font right inside Blender!
Here you enter the prefix name (the object "family") used
to find the individual characters used for typing.
It's a fairly involved process, so here's a step-by-step:

- Build the font characters; each one can be any object type (mesh, curve, etc.).
Every name has to follow the schema:
"common prefix" then the "character name" (e.g. "ft.a", "ft.b", etc.).

- On the text object, switch on
Instancing Vertices.

- Over in the Font tab, set the Object Font field to the "common prefix" of your "font" objects.
From then on, whenever a character in your text matches the suffix of a "font" object's name,
that object gets duplicated onto the character.

Note

Each duplicate is placed with its center sitting at
the lower right corner of the matching character.

Text on Curve
Hand the text object a curve object to ride along.

Text on curve.

Tip

You're better off with the Curve modifier,
which gives you more control and is the usual way to pull off such effects in modern Blender.

Underline Position
Lets you nudge the underline up or down.

Underline Thickness
Governs how thick the underline comes out.

Small Caps Scale
By how much uppercase letters shrink once small caps is switched on.

### Paragraph

Reference

Mode :

All

Panel :

Properties ‣ Data ‣ Paragraph

Alignment and spacing of the text are controlled from the Paragraph Panel.

The Paragraph panel.

### Alignment

Horizontal

Left :

Pushes text to the left edge of the frames when frames are in use;
otherwise it treats the text object's origin as the text's starting point, growing rightward.

Center :

Centers text within the frames when frames are in use;
otherwise it treats the text object's origin as the text's midpoint,
growing equally left and right.

Right :

Pushes text to the right edge of the frames when frames are in use;
otherwise it treats the text object's origin as the text's end point, growing leftward.

Justify :

Flushes a line only when a word wrap ends it ( not a newline),
filling lines with whitespace rather than character spacing (kerning).

Flush :

Flushes every line, even one that's still being typed in.
It fills lines using character spacing (kerning).

Note

Both Justify and Flush only work within frames.

Vertical

Top :

- Using frames, the text's top edge snaps to the frames' top edge.

- Without a frame, the text's top edge meets the object's origin and the text grows downward.

Top Baseline :

- Using frames, the text's 'top' baseline snaps to the frames' top edge.

- Without a frame, the text's actual baseline meets the object's origin
and the text grows downward.

Note

That shift in reference point on the first line,
depending on whether boxes are used, is admittedly confusing.

Middle :

- Using frames, the text is centered within them.

- Without a frame, the text is centered on the object's origin
and grows upward and downward in equal measure.

Bottom Baseline :

- Using frames, the text's baseline snaps to the frames' bottom edge.

- Without a frame, the text's baseline meets the object's origin and the text grows upward.

Bottom :

- Using frames, the text's bottom edge snaps to the frames' bottom edge.

- Without a frame, the text's bottom edge meets the object's origin and the text grows upward.

### Spacing

Character Spacing
A multiplier that scales the width of the space between characters (kerning).

Within Edit Mode in the 3D Viewport, individual kerning at the text cursor
can be dialed down or up with Alt - Left / Alt - Right too.

Word Spacing
A multiplier that scales the width of the whitespace between words.

Line Spacing
A multiplier that scales the vertical space between lines.

Offset X, Y
Govern where the text sits within the object along X and Y.
This is reckoned relative to the object's origin — applied to the whole text, or to each frame once text boxes are in use.

### Text Boxes

Reference

Mode :

All

Panel :

Properties ‣ Data ‣ Text Boxes

Text boxes (frames) let you spread the text across rectangular regions inside one text object.
You can have any number of freely movable, resizable text frames per text object.

Text runs continuously from the lowest-numbered frame up to the highest, word-wrapped
inside each frame.
It spills into the next frame once a lower-numbered one can't hold any more.
Reach the last frame and text simply overflows it (by default — see the options below).

Text Boxes panel.

Add Textbox
Drops in a new frame right after the current one (in text-flow order).
It inherits the size and position of the selected frame.

(Remove Text Block)
Gets rid of the current frame.

Overflow
What becomes of text that spills past the room available in the defined boxes.

Overflow :

Simply let the text spill on out of the final box.

Scale to Fit :

Shrink the text down until it fits the room on hand.

Truncate :

Cut off whatever text won't fit the available room.

Note

Truncation only happens in Object Mode ;
in Edit Mode the whole text stays visible (and overflows as needed).

Size X, Y
Sets the text box's width and height; at zero no word wrapping occurs
(the value is ignored, and the entire text-box system shuts off when all are set to null).

Offset X, Y
Govern where the frame sits along X and Y, i.e. its position.

Multiple columns, text flowing between boxes.

## Objects Panel

Objects Panel

Lists all objects available for tracking, camera, or object solving.

One default object exists (camera solver only, non-deletable). Added objects serve object tracking/solving; camera solving uses the default only.

Tracks misassigned to wrong objects are copied via Track ‣ Copy Tracks and Track ‣ Paste Tracks.

Workflow is identical across objects: track, set camera data, solve. Camera data is shared; camera-motion solving refines intrinsics.

## Dope Sheet View

Dope Sheet View visualizes motion tracking data as a separate Movie Clip editor view (like Graph View).

Dope Sheet View displaying tracked segments.

The view shows channels for selected tracks. Dark bars represent tracked segments; small diamonds mark keyframed positions.

Frame background color indicates track count. Red = fewer than eight tracks (visual feedback, not a solve failure—just warrants attention). Yellow = eight to sixteen tracks. No guarantee that fewer tracks prevent accurate reconstruction; poor-feature tracks reduce accuracy more than sparse tracking.

Header

Channel sort-order controls.

Only Show Selected
Limits display to selected-track data.

Display Hidden
Includes hidden-track information.

Dopesheet Sort Field
Track ordering.

Name: Alphabetical.

Longest: By longest tracked segment.

Total: By total frame count.

Average Error: By average reprojection error post-solve.

Start Frame: By first frame.

End Frame: By last frame.

Invert
Reverses sort direction (ascending ↔ descending).

Usage

The Dope Sheet View is visualization-only; no editing tools exist.

## Graph View

Graph View displays tracking motion and error via colored curves.

Red and green lines show tracker velocity per frame (green = vertical, red = horizontal); first frames always zero.

Blue line (clickable film strip output) displays average per-frame error; post-solve only, non-editable. This line should be flat and close to zero—peaks reveal inaccurate tracking regions.

Out-of-range frames darken.

Graph View display.

Header

Only Show Selected
Displays selected-tracker graph.

Display Hidden
Displays hidden-object channels.

Show Frames
Visualizes per-frame average reprojection error of all active-object tracks.

Show Tracks Motion
Shows X/Y velocity curves.

Show Tracks Error
Shows per-frame reprojection error.

Usage

Curves reveal whether particular trackers deviate from the average. Spikes typically indicate tracking error.

Manual curve editing: select a point, drag or delete—this modifies the corresponding tracker on that frame.

Lock to Selection L
Anchors view to selected markers during playback.

## Cache

### Cache

Reference

Panel :

Physics ‣ Cloth Cache

After the deflection mesh is ready for the target frame range (including any animation via armatures),
instruct the cloth simulator to compute and handle collisions. Select the cloth object and in the Object tab, Physics tab, set Start and End frames for computation, then press Bake.

Cloth cache settings match those of other dynamic systems. See Particle Cache for more.

Note

If the cloth object moves or is edited after simulation has already run, the cache must be cleared; otherwise, Blender will misrepresent vertex positions using the stored mesh state.

Note

Subdivision Surface Modifier

Baking and caching occur at each subdivision level, so preview and render subdivision must match.

Note

Start and End cannot change without clearing the simulation. Once finished, options appear: free the bake, edit it, or re-bake.

### Editing the Cached Simulation

Important

Cached simulation editing is not currently functional, see:
blender/blender#77114 for details.

### Cache

Reference

Panel :

Physics ‣ Fluid ‣ Cache

Type :

Domain

The Cache panel manages fluid simulation baking and caching, storing outcomes to prevent recalculation.

Baking demands substantial processing (time). Scene-dependent; allocate adequate duration.

Modifier meshes use render settings for fluid export. Depending on config, time and memory can spike exponentially. Subdivision Surface on moving obstacles might warrant reduced subdivision to accelerate baking. With correct setup/rig, boost settings for realism.

Note

Fluid sims use proprietary cache. Other physics use General Baking.

Cache Directory
Location for baked files. Each simulation type (mesh, particles, noise) gets its subdirectory.

Frame Start
Sim first frame, first baked frame.

End
Sim last frame, last baked frame.

Note

Simulation only calculates positive frames within Start/End. Extend End frame for longer sims.

Offset
Frame shift on cache loading—not during baking.

Type
Cache baking methodology.

Replay :

Baking occurs as viewport playback happens.

Modular :

Step-by-step baking: bake tools are in individual panels (e.g., mesh baking in Mesh panel).

All :

Single-tool baking considering all settings. The tool lives in the Cache panel.

Important

"Replay" requires "Play Every Frame" Playback Sync. Use "Modular" or "All" for "Frame Dropping" or "Sync to Audio".

Resumable
Saves extra data for resuming post-pause. More drive usage; avoid on high-resolution bakes.

Bake All, Free All
With Final cache type. Bake All runs considering all settings (same as Modular, all at once). Status bar shows progress; Esc aborts. After baking, Free All clears cache. Pause/resume unavailable (only critical files save).

### Volumetric Data

Format
Volume sim data storage (grids, particles).

Uni Cache :

Blender proprietary format with compression. Each object stores in its .uni file.

OpenVDB :

Sophisticated, effective format. All objects (grids, particles) in one .vdb per frame.

Compression OpenVDB Only
OpenVDB file compression.

Zip :

Zip-compressed files. Effective, slower than Blosc.

Blosc :

Blosc-compressed files. Multithreaded, similar size/quality to Zip.

None :

No compression.

Precision OpenVDB Only
OpenVDB data precision.

Full :

Full 32-bit precision.

Half :

Half 16-bit precision.

Mini :

Mini 8-bit where feasible; 16-bit otherwise.

Meshes Liquids Only
Mesh cache file format.

Binary Object: Compressed mesh files.
Object: Standard mesh data format.

Export Mantaflow Script
Exports the sim as standalone Mantaflow script when baking (bake "Bake Data"). Generally for developers/advanced users familiar with Mantaflow GUI. Debug Value 3001 enables.

### Cache 

Reference

Panel :

Particle System ‣ Cache

Real-time responsiveness improves and unnecessary recalculation reduces when particle information gets cached in memory or persisted to disk.

Emitter particle systems employ a shared caching and baking mechanism (alongside Soft Body and Cloth).

Particles Cache settings. 

See also

General Baking documentation contains supplementary details.

### Hints 

- Simulation computes exclusively for positive frame numbers within the Cache panel's Start and End boundaries, baked or not. Extending the End frame becomes necessary for simulations surpassing the default frame duration.

- Throughout animation playback, each physics system writes every frame to cache. Playback must commence before or at the simulation's start frame for cache population.

- Automatic cache clearing happens on modifications, though not universally. Manual clearing may prove necessary after force field adjustments, for instance.

- Baked systems resist post-bake alteration. Mesh changes won't retrigger simulation computation.

- The Delete Bake button in simulation cache settings clears bake results.

- Particle Edit Mode editing requires in-memory bakes only. Disk Cache prevents editing capabilities.

- Path length constraints on the blend-file location may obstruct caching, particularly when OS path length limits apply.

- Modifier stack sequencing deserves careful attention. Different face counts may appear in viewport versus render (e.g., with subdivision surface), potentially creating divergent render output.

## Mesh

### Mesh

Liquid particles' companion, the mesh, is another visualization approach. It emanates from particles, often higher-res than Resolution Divisions.

Enabling Mesh signals cache which data to read. Enabled-but-missing mesh shows the original domain. Toggle-switching between original and baked mesh is possible without cache reset.

Mesh shape depends on parameter combinations. Adjusting Particle Radius shifts concavity interpretation.

Upres Factor
Mesh resolution booster, matching Resolution Divisions (mesh is this times bigger than simulation).

Particle Radius
Single liquid particle radius in voxel units, determining surface coverage and considered-liquid distance. Larger covers more area, expanding mesh volume around particles.

Relates to liquid domain Particle Radius yet interpreted independently. Mesh resolution differs from base via Upres Factor. Useful for mesh size per particle tuning.

Speed Vectors
Generates velocity Attribute recording per-frame vertex velocity. Auto-used with motion blur.

Note

Cycles motion blur requires Deformation Motion Blur enabled.

| Motion blur on.  | Motion blur off.  |

Mesh Generator
Mesh generator method determines accuracy. Final yields higher quality and more options; Preview runs faster, less smooth.

Smoothing Positive
Positive smoothing cycles. More = increasingly smooth outline, yet risks detail loss (small drops).

Smoothing Negative
Negative smoothing cycles. More = sharper outline. Preserves details but rougher (single particle has flat sides vs. rounded).

Liquid drop impact (top view) smoothing comparisons. Left: 1, 1. Middle: 10, 1. Right: 1, 10. Right shows slightly sharper splash corners. 

Concavity Upper
Upper concavity limit. High = filled/smoothed concavities.

Concavity Lower
Lower concavity limit. High = filled/smoothed concavities.

Lower > Upper produces distorted, non-manifold meshes. Avoid unless intentional.

| Upper: 1.0, Lower: 0.0.  | Upper: 1.0, Lower: 0.5.  | Upper: 1.0, Lower: 1.0.  |
| Upper: 1.5, Lower: 0.0.  | Upper: 1.5, Lower: 0.5.  | Upper: 1.5, Lower: 1.0.  |
| Upper: 2.0, Lower: 0.0.  | Upper: 2.0, Lower: 0.5.  | Upper: 2.0, Lower: 1.0.  |

Bake Mesh, Free Mesh
With Modular cache.

Status bar shows progress; Esc halts. Post-baking, Free Mesh clears cache. Pause/resume available.

## Particles

### Particles

Note

Secondary particle activation also creates a particle system. Deactivation deletes it and settings. These systems don't contribute to mesh generation, needing geometry assignment for rendering.

Spray
Generate spray during secondary simulation—those airborne particles from big splashes.

Foam
Generate foam—surface-riding particles.

Bubbles
Generate bubbles—subsurface particles.

Combined Export
Particle-type grouping into single particle system. No sim outcome change, only allocation.

Upres Factor
Particle sim resolution multiplier, matching Resolution Divisions.

Wave Crest Potential Maximum
Wave-crest marking threshold ceiling. Higher = fewer marked.

Wave Crest Potential Minimum
Wave-crest marking threshold floor. Lower = more marked.

Trapped Air Potential Maximum
Trapped-air marking ceiling. Higher = fewer marked.

Trapped Air Potential Minimum
Trapped-air marking floor. Lower = more marked.

Kinetic Energy Potential Maximum
Fluid-speed ceiling initiating particle emission. Higher = fewer particles.

Kinetic Energy Potential Minimum
Fluid-speed floor. Lower = more particles.

Potential Radius
Radius for per-cell potential. Higher = slower, smoother grids.

Particle Update Radius
Radius for per-particle position updating. Higher = slower, less chaotic movement.

Wave Crest Particle Sampling
Max particles per wave-crest cell per frame.

Trapped Air Particle Sampling
Max particles per trapped-air cell per frame.

Particle Life Maximum
Longest particle existence.

Particle Life Minimum
Shortest particle existence.

Bubble Buoyancy
Upward force strength. High = mainly upward movement.

Bubble Drag
Fluid-following force strength. High = fluid-aligned movement.

Particles in Boundary

Delete :

Remove secondary particles inside obstacles or leaving domain.

Push Out :

Reintroduce secondary particles to the domain.

Bake Particles, Free Particles
With Modular cache.

Status bar shows progress; Esc pauses. Post-baking, Free Particles clears. Pause/resume available.

## Gravity

### Gravity 

Reference

Panel :

Scene ‣ Gravity

Gravity operates as a global parameter influencing every physics system within the scene, positioned in the scene tab. Standard settings use -9.810 on the Z axis, representing real-world gravitational acceleration. Adjustments to this value simulate different planetary conditions.

Gravity gets designated as g with measurement units m × s -2.

All physics systems experience gravity identically.

Earth's gravitational field remains essentially constant across the planet's surface. For lunar renders, employ -1.622 m × s -2 on the Z axis. Mars gravity, another common choice, measures -3.69 m × s -2 on the Z Axis.

Note

Individual physics systems can scale down their gravity response through the Field Weights tab.

# Line Art Modifier, Outline Modifier, Grease Pencil Primitives, Curve Data ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Line Art Modifier; Outline Modifier; Grease Pencil Primitives; Curve Data; Layers; Grease Pencil Structure; Colorize Visual Effect; Glow Visual Effect; Pixelate Visual Effect; Rim Visual Effect; Blender 5.1 Reference Manual; Annotations.

## Line Art Modifier

Line Art is a modifier that derives stylized strokes by tracing geometry drawn from a whole scene, a chosen collection, or one isolated object. An active camera is required, because only the geometry visible from that camera's viewpoint will yield lines.

Note: Currently, each Line Art modifier independently executes full occlusion calculation. Using multiple modifiers (for varying styles) significantly increases compute time. Future improvements are planned.

Use Cache: Speeds up rendering by reusing cached scene data from the first Line Art modifier, at the cost of restricting certain settings. Available only with multiple Line Art modifiers when the current modifier is not first.

Source Type: Specifies geometry source. Scene uses all visible objects. Collection uses objects in a chosen collection. Object generates from a single object (supported types: Mesh, Text, Curve, Surface, Curves).

Object/Collection: Selects source based on type. Invert Collection Filtering: Selects everything except lines from specified collection.

Note: Line Art loads and processes the entire visible scene for correct occlusion, unless configured differently in object or collection Line Art Usage.

Layer: Grease Pencil layers receiving results. Material: Grease Pencil materials for strokes. Line Radius: Stroke width. Opacity: Stroke opacity.

Edge Types: Line Art recognizes multiple edge categories. Selected types appear in output.

Illumination Filtering: Filters feature lines by lighting. None—no filtering. Illuminated—only lit-region lines. Shaded—only shaded-region lines. Illuminated (Enclosed Shapes)—lit-region lines, with contour/light-contour/shadow combined into closed forms.

Create: Contour generates lines where front/backfacing faces separate; inversible. Contour shows surface contours. Silhouette shows object outline. Individual Silhouette shows each object's contour separately. Crease generates lines at sharp angles. Crease Threshold: Angle below which treated as crease (object override takes precedence). Intersections: Lines where faces meet. Material Borders: Lines separating different-material faces. Edge Marks: Lines from freestyle marks. Loose: Unpaired edges. Light Contour: Light/shadow boundaries from a light. Cast Shadow: Light-projected contour lines. Allow Overlapping Types: Multiple types per edge create separate strokes.

Light Reference: Light Object for Light Contour. Shadow Camera Size: Orthographic scale of shadow camera. Near/Far: Shadow camera clipping.

Geometry Processing: Custom Camera uses alternate camera instead of active. Overlapping Edges as Contour: Overlapped edges (e.g., split modifier or imported coincident edges) render as contour; slightly slower but handles overlap correctly. Instanced Objects: Loads particles/instanced objects; performance impact with many instances. Clipping Boundaries: Generates clipping contours at near/far plane intersections. Crease on Smooth: Crease edges visible in smooth surfaces. Crease on Sharp: Creases show on sharp edges. Force Backface Culling: Removes back faces to accelerate; changes occlusion levels.

Occlusion: Range (when enabled) selects lines within start/end occlusion levels. Level: Desired occlusion—0 means fully visible; 1 means occluded by one face layer.

Material Mask: Selects lines occluded by faces with specific masks. Masks: Matching bits. Exact Match: All bits must match, or any one.

Intersection: Allows edges between two collections. Collection Mask: Bits from Collection properties. Exact Match: All masks required.

Face Mark Filtering: Manual control using Freestyle marks. Invert: Reverses filter. Boundaries: Lines at mark edges. Keep Contour: Preserves contours during filtering.

Chaining: Chain: Intersection with Contour links intersection lines with contours. Note: Ambiguity may result; unchained intersections remain separate. All Lines: All lines treated as contour and chained. Loose Edges: Floating edges chain together. Loose Edges as Contour: Unpaired edges classified as contours. Preserve Details: Small details maintain across occlusion; omitting creates smoother results. Geometry Space: Uses geometry distance instead of image-space. Image Threshold: Short segments chain if 2D distance is within threshold. Smooth Tolerance: Smoothing strength on jagged sequences. Angle Splitting: Breaks chains at sharp turns above angle.

Vertex Weight Transfer: Filter Source: Vertex groups prefixed with this text transfer weights. Match Output: Transfers filtered weights to identically-named Grease Pencil groups. Target: Alternate group when Match Output is off; highest weight copied if multiple.

Composition: Overscan: Margin outside camera view prevents strokes ending abruptly; Blender only renders visible edges as an optimization. Image Boundary Trimming: Cuts strokes at image edge. Depth Offset: Shifts strokes toward camera, avoiding clipping; unavailable if Show in Front is enabled. Towards Custom Camera: Offsets toward selected camera.

Bake: Bake Line Art: Records Line Art strokes within start/end range; deactivates afterward. Bake All: Records all Grease Pencil objects with modifiers. Clear Baked Line Art: Clears recorded frames in range. Clear All: Clears all recorded.

Warning: Manual strokes drawn in the bake range also clear.

Continue without Clearing: Re-activates a modifier without clearing, useful for multi-section work.

Demonstration of material masks in action. Intersection: Edges can be selected where two collections meet. Collection Mask: Mask bits matched from Collection properties. Exact Match: Requires all intersection masks match instead of any one.

Demonstration of collection masks in use. Face Mark Filtering: Manual edge selection via Freestyle marks. Face Mark Filtering subpanel. Invert: Reverses the filter. Boundaries: Filters feature lines based on face-mark borders. Keep Contour: Retains contours during filter application.

Chaining: Line chaining merges nearby segments. Chaining subpanel. Chain: Intersection with Contour—intersection lines can merge with nearby contours. Note: Enabling creates ambiguity; unmerged intersections remain separate. All Lines—all become contour type and merge. Loose Edges—floating edges merge together. Loose Edges as Contour—unpaired edges become contour. Preserve Details—maintains small details rather than splitting at each occlusion change; omitting creates smoother output. Geometry Space—uses geometry distance instead of image-space distance. Image Threshold: Distance below which segment endpoints chain together. Smooth Tolerance: Smoothing applied to jagged chains. Angle Splitting: Chains separate at turn angles exceeding this value.

Vertex Weight Transfer: Weight data flows from source mesh to strokes. Vertex Weight Transfer subpanel. Filter Source: Vertex groups prefixed with this text transfer. Match Output: Copies filtered weights into Grease Pencil groups with identical names. Target: Assigned group when Match Output is off; uses highest weight if multiple.

Composition: Rendering optimizations. Composition subpanel. Overscan: Margin prevents stroke cutoff; without it, Blender only renders visible edges. Image Boundary Trimming: Clips strokes at image limits. Depth Offset: Camera-ward shift prevents z-clipping while maintaining depth; unavailable with Show in Front. Towards Custom Camera: Offsets toward selected camera instead of active.

Bake: Recording and management. Bake options. Bake Line Art: Records within start/end range; auto-disables. Bake All: Records all Grease Pencil objects containing modifiers. Clear Baked Line Art: Removes recorded frames in range. Clear All: Removes all recorded.

Warning: Manual strokes in the bake range also delete.

Continue without Clearing: Reactivates without clearing—helpful for sectioned work.

## Outline Modifier

The Outline Modifier traces the perimeter of strokes with new strokes. Thickness: Generated outline stroke width. Keep shape: Perimeter strokes stay inside original perimeter, preserving shape. Subdivisions: Generated outline detail level. Sample Length: Perimeter conversion precision. Outline Material: Material for generated outlines. Target Object: Origin for cyclic strokes.

Influence Filters: See Influence Filters.

## Grease Pencil Primitives

Reference: Mode—Object and Edit Modes. Menu—Add ‣ Grease Pencil. Shortcut—Shift + A

In Object Mode, Add provides three Grease Pencil primitives with preset materials and 2D layers: Blank adds without strokes. Stroke adds with a simple reference stroke. Monkey creates a 2D head (Suzanne, Blender's mascot); useful as a standard test. Scene Line Art configures a Line Art Modifier for the scene, creating an empty object with a modifier referencing all scene objects. Collection Line Art configures for the collection, creating an empty with a modifier referencing collection objects. Object Line Art configures for the object, creating an empty with a modifier referencing the active object.

## Curve Data

Reference: 3D Viewport Editor, Edit Mode, Sidebar ‣ Item ‣ Curve Data

The Curve Data panel in Edit Mode controls the active Grease Pencil curve's behavior, affecting evaluation, display, and rendering. Cyclic: Closes the spline by connecting the final control point to the first, forming a continuous loop when enabled; remains open when disabled.

Knot Mode (NURBS): Determines knot generation along the spline, affecting parameterization and shape. Normal uses evenly spaced knots for uniform influence. Endpoint clamps the curve through first and last control points. Bézier makes NURBS resemble Bézier curves; control points act like Free handles. Endpoint Bézier combines clamping with Bézier behavior. Custom permits manual knot specification.

Order (NURBS): Defines the mathematical order, controlling how many control points influence each segment. Higher values increase point influence and smoothness. Lower values reduce influence and create sharper transitions. Typical range is 2–6, depending on point count.

Resolution (NURBS/Bézier/Catmull Rom): Subdivisions per segment. Higher resolution smooths but increases cost. Lower resolution reduces detail but improves speed.

Fill Opacity: Fill area transparency—0 is fully transparent; higher increases visibility.

Start Cap: Round adds rounded beginning. Flat ends sharply. End Cap: Round adds rounded end. Flat ends sharply.

Softness: Fill transition toward boundary smoothness. Higher creates softer edges.

U Scale: Texture coordinate scaling along length; controls material/texture repetition.

Aspect Ratio: Width-to-height scaling for material/texture effects; stretches or compresses patterns.

## Layers

Reference — Mode: All Modes; Panel: Object Data tab ‣ Layers.

Grease Pencil objects organize their strokes into a tree (the layer tree) for grouping and arranging. A stroke belongs to just one 2D layer, and the selected layer is the active layer — only one layer or group is active at a time, and new strokes you draw land on the active layer. By default the viewport draws layers top to bottom. Layers can be gathered into Layer Groups (a layer sits in only one group at a time), moved into groups by drag-and-drop, and color-coded with a color tag. Each layer maps to a channel in the Dope Sheet editor (Grease Pencil mode; see Dope Sheet), can be combined with Modifiers to affect only part of a drawing (see Modifiers), and can mask other layers via Use Mask (mask icon) or the checkbox in the Masks panel header (see Masks). Tip: when off-layers distract you in the 3D Viewport, turn on the Fade Inactive Layers overlay to dim the non-active ones.

Layer Tree — a tree view of every layer and group on the Grease Pencil object. Each layer name carries four icon buttons for common properties:
- Use Mask (mask icon) — toggle whether Masks affect the layer.
- Onion Skinning (onion skin icon) — toggle whether the layer is used for Onion Skinning.
- Hide (eye icon) — toggle the layer's visibility in viewport and render.
- Lock (padlock icon) — toggle whether the layer is editable.

Add New Layer — add a new layer to the active object.
Add New Layer Group — add a new layer group to the active object; note that groups can't be added from the Dopesheet, only from the Properties editor.
Remove Layer/Group — remove the active layer or layer group.
Layer Specials — operators for working with layers:
- Duplicate — make an exact copy of the selected layer, appending a number to its name.
- Duplicate Empty Keyframes — copy the selected layer but with empty keyframes, handy for having empty keyframes ready for the cleanup or filling process.
- Show All — make every layer in the list visible.
- Hide Others — hide every layer in the list except the active one.
- Lock All — lock editing on all the layers in the list.
- Unlock All — unlock editing on all the layers in the list.
- Autolock Inactive Layer — automatically lock every layer in the list but the active one, so you don't accidentally change others without locking them each time.
- Ignore Material Locking — allow editing strokes even when they use locked materials.
- Merge Down (Shift-Ctrl-M) — combine the selected layer with the one below, keeping the lower layer's name.
- Merge Group — combine the active layer group's layers into a single layer.
- Merge All — combine all layers into the active layer.
- Mask with Layer Above/Below — add a mask to the active layer using the layer above or below.
- Copy Layer to Selected — copy the active layer to the selected Grease Pencil object.
- Copy All Layers to Selected — copy all layers to the selected Grease Pencil object.
- Reorder Layer — move the active layer or layer group up or down in the tree.

Below the layers list sit more settings:
Blend Mode — the layer blending operation to perform (see Color Blend Modes).
Opacity — set the layer's opacity.
Lights — when enabled, the layer is affected by lights.

Masks: in Grease Pencil there are no dedicated mask layers — any layer can mask others, and the system is flexible enough for both top-to-bottom and bottom-to-top masking. Layers used as masks can use all the blend modes and opacity values of any other layer (tip: for fully transparent masking, set the mask layer's opacity to 0). Add the layer(s) that should mask the current one to the Mask list view. In the Masks list, each name carries two icon buttons:
- Invert (mask icon) — invert the mask.
- Viewport/Render Visibility (eye icon) — toggle the layer's visibility in viewport and render.

Transform — allows per-layer location, rotation, and scale transformations.

Adjustments:
Tint Color — a color that tints any material colors used in the layer.
Factor — how much tint color to apply.
Stroke Thickness — a thickness value that overrides the strokes' thickness in the layer.

Relations:
Parent — choose a Parent object to manipulate the layer; the layer inherits the parent's transformations, especially useful when rigging for cut-out animation.
Pass Index — the layer's index number, usable with some modifiers to restrict changes to certain areas (see Modifiers).
View Layer — the View Layer the Grease Pencil layer uses; left empty, the layer is included in all View Layers, useful for separating drawing parts for compositing.
Use Masks in Render — when disabled, none of the layer's masks are included in the view layer render.

Display:
Channel Color — the color used in the Dope Sheet's channel region.

## Grease Pencil Structure

Points, edit lines, and strokes comprise Grease Pencil. Example of structure shown. Points: Single 3D-space positions. Store all stroke-appearance properties: location, thickness, alpha, weight, UV rotation. Note: Point (Grease Pencil) = Vertex (meshes).

Edit Lines: Straight connections between points; invisible in render; construct stroke. Strokes: Rendered image of points and edit lines using a Grease Pencil material (material links at stroke level).

## Colorize Visual Effect

The Colorize Visual Effect applies preset color transformations. Mode: Grayscale converts to grayscale. Sepia converts to sepia tones. Duotone creates high-contrast posterized versions. Low Color: First color. High Color: Second color. Transparent adds color opacity. Custom allows custom tint. Color: Tint. Factor: Mix amount. Example: Grayscale, Sepia, Duotone, Transparent modes.

## Glow Visual Effect

The Glow Visual Effect adds a glowing rim. Mode: Luminance illuminates overall. Color affects single color. Select Color: Glow-target color selection. Threshold: Color-affection limit (1 = none). Glow Color: Glow appearance. Blend Mode: Mask blending. See Color Blend Modes. Opacity: Glow strength. Size X, Y: X/Y glow scale in pixels. Rotation: Glow angle. Samples: Blur count (0 disables). Glow Under: Alpha-only when active. Example: Original, Luminance, Luminance (Glow Under), Color (Black lines).

## Pixelate Visual Effect

The Pixelate Visual Effect renders pixelated appearance. Size X, Y: Final pixel dimensions in horizontal/vertical. Anti-aliasing: Applies pixel edge smoothing. Example: Original, 20 px, 100 px, 200 px sizes.

## Rim Visual Effect

The Rim Visual Effect simulates rim lighting via color-silhouette displacement in horizontal and/or vertical directions. Multiple blend modes apply to the mask.

Rim Color: Light color. Mask Color: Unaltered color. Blend Mode: Mask blending operation. See Color Blend Modes. Offset X, Y: Displacement in pixels. Blur—Blur X, Y: X/Y scale in pixels. Samples: Count (0 disables).

Example: Original, No blur, Blur, Mask color Black.

## Blender 5.1 Reference Manual

### Blender 5.1 Reference Manual

Welcome to Blender's manual, the free, open-source 3D creation toolkit.

This site can be used offline: Download as HTML web pages or EPUB e-book.

Getting Started: About Blender, Installing Blender, Configuring Blender, Help System.

Sections: User Interface—window system, widgets, tools. Editors—interface and functionality overview. Scenes & Objects—objects, scenes, view layers, collections. Modeling—meshes, curves, metaballs, text, modeling tools, modifiers. Sculpting & Painting—sculpting, texture painting, vertex painting. Grease Pencil—2D drawing and animation. Animation & Rigging—keyframes, drivers, constraints, armatures, shape keys. Physics—simulations, particle systems, dynamic paint. Rendering—EEVEE, Cycles, Freestyle. Compositing—post-processing nodes. Motion Tracking & Masking—video motion tracking, masking. Video Editing—sequencer editing. Assets, Files, & Data System—data-block management, blend-file structure. Add-ons—additional functionality. Advanced—Python scripting, add-on writing, command-line arguments. Troubleshooting—crash solving, graphics issues, Python errors, data recovery, bug reporting. Glossary—terms and definitions. Manual Index—glossary-linked terms.

Get Involved: Help write Blender's future! Contribute to the Blender Manual. Translations: Bring Blender worldwide. Translate UI or Manual.

## Annotations

The annotation tool is available in several editors and lets you add notes to things like 3D objects or node setups (the arrow in the manual's screenshot is an annotation).

Annotation Tools — activate the tool in the Toolbar; its sub-tools are:
- Annotate — draw free-hand strokes in the main area.
- Annotate Line — click and drag to make a line, optionally choosing an arrow style for the start and end.
- Annotate Polygon — click repeatedly to chain connected lines, then press Return or Esc to confirm.
- Annotate Eraser — click and drag to remove lines; its Radius is set in Tool Settings.

Tool Settings — Common:
Color — set the color of existing and new strokes.
Annotation Layer — a pop-over menu (showing the current layer's name) for reaching the Annotation Layers.
Placement — where annotations are drawn:
- 3D Cursor: 3D Viewport only; the annotations join the 3D scene, drawn on an imaginary plane through the 3D Cursor and aligned to your view.
- Surface: 3D Viewport only; the annotations join the 3D scene, drawn onto the surface of the object under the mouse, falling back to 3D Cursor behavior where there's no surface.
- Image: 2D editors only (such as the Image Editor); the annotations join the 2D space, so their position and size shift as you pan and zoom.
- View: the annotations are 2D and stick to the screen, keeping their position, rotation, and size through any pan, orbit, or zoom.
Only End Points (Surface placement) — snap using only the first and last parts of the stroke.
Project Onto Selected (Surface placement) — project the strokes only onto selected objects.
Stabilize Stroke — curbs stroke jitter while drawing by delaying and correcting point locations.
Radius — the minimum distance from the last point before the stroke continues.
Factor — a smoothing factor; higher values give smoother strokes but make drawing feel like you're dragging the stroke along.

Annotate Line:
Style Start, End — the decoration at the beginning or end of the line segment, for example to make arrows pointing out specific scene details.

Annotation Layers — with the annotation tool enabled, the settings for managing multiple layers live in the Sidebar ‣ View ‣ Annotations panel.
Opacity — adjust the opacity of existing and new strokes.
Thickness — adjust the thickness of existing and new strokes.

Onion Skin — shows a ghosted image of strokes from frames before and after the current one; it works only in the 3D Viewport and Sequencer (see the Grease Pencil documentation on Onion Skinning).
Before/After — the color used for ghost frames before and after the current frame, with the number setting how many frames to show before and after.

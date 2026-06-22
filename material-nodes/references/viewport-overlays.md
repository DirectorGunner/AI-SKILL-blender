# Viewport Overlays, Viewport Shading, Object Type Visibility, Camera View ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Viewport Overlays; Viewport Shading; Object Type Visibility; Camera View; View Regions.

## Viewport Overlays

Reference — Mode: All Modes. Location: Header ‣ Overlays.

The Show Overlays button switches every overlay in the viewport on or off at once. Bear in mind that a camera's outline and passepartout aren't counted among the Viewport overlays. The drop-down opens a popover of finer settings described below, and depending on the active interaction mode a second button may add still more, also covered here.

General — these options are always present regardless of mode, and some can be tuned in the Viewport Preferences.

Guides:
Grid — shows the grid in an orthographic side view.
Floor — shows the ground plane in perspective view.
Axes — shows the X, Y, and/or Z axis lines.
Scale — the spacing between lines of the grid/floor.
Subdivisions — how many subdivisions sit between grid lines.
Text Info — places assorted readouts in the viewport's upper-left corner:
  View Perspective — the name of the View Perspective, e.g. "Top Orthographic" or "User Perspective."
  Playback Frame Rate (FPS) — the frames-per-second the animation is running at. By default Blender plays every frame, which can drop the FPS below the target (so playback runs slower than realtime); when that happens the FPS reads in red. Adjust this in the Playback popover of an editor's playback controls.
  Object Info — the current frame in parentheses, after which it names the active object, its data-block, and the Collection that holds it. Where relevant it also lists the selected Shape Key and, in angle brackets, any Marker on the current frame. If the object is keyframed on the current frame the Object Info shows in yellow.
  Grid Resolution — when the view is squared to a world axis (see Viewpoint), the Text Info additionally reports the smallest gap between two parallel grid lines.
Statistics — reports counts of objects and geometry, with the figures keyed to the current selection: selecting a mesh yields vertex, edge, and face counts, while selecting a light reports how many lights the scene holds.
  Objects — how many objects are selected versus the total.
  Geometry — scene data that varies by mode and object type, such as a count of vertices, faces, triangles, or bones.
3D Cursor — shows the 3D Cursor.
Annotations — shows annotations.
Camera Guides — shows the camera guides (Safe Areas and Composition Guides); available only in camera view.
Reference Spheres — shows two spheres, one glossy and one diffuse, that respond to lighting to aid look development; available only in Material Preview shading, with their size set in the Viewport Preferences.

Objects:
Extras — shows objects that carry no geometry (empties, cameras, lights). It also governs the display of the Rigid Body Collision Shape and the Object Texture Space.
Light Colors — tints a light object's outline with the color that light emits.
Relationship Lines — shows dashed lines marking parent or constraint relationships.
Outline Selected — draws an outline around selected objects.
Bones — shows Bones.
Motion Paths — shows the motion-path overlay.
Origin — shows the origins of the selected objects.
Origin (All) — shows every object's origin.
Bone Wireframe Opacity — the top opacity for bones drawn in Wireframe shading (or in Solid shading with X-Ray on); useful for cutting clutter so you can focus on the mesh rather than the bones.

Geometry:
Wireframe — draws mesh edges, like Wireframe Shading but layered over the existing shading. The slider sets which edges appear: low values hide edges across near-flat surfaces, while 1 reveals them all.
Opacity — how opaque those edges are, from 0 (invisible) to 1 (fully solid).
Fade Inactive Geometry — in any mode but Object Mode, dims objects you aren't currently working on, with the slider setting how strongly.
Face Orientation — paints the back side of faces red. As a rule, a face showing red on a mesh's exterior is probably facing the wrong way and needs its normal flipped, which you can do with the Flip or Recalculate operators on meshes, or with Switch Direction on Surface objects.

Viewer Node:
Visualizes Attributes — shows attributes wired into the Viewer Node.
Viewer Node — draws, as a grayscale shade, whatever value the attribute feeding the Viewer Node carries.
Color Opacity — the opacity of the attribute currently being shown.
Attribute Text — prints attribute values as text in the viewport.

Motion Tracking — shows the motion-tracking overlay.
Camera Path — shows the reconstructed camera path.
Marker Names — shows the names of the reconstructed tracking markers.
Tracks — changes how the tracking markers are drawn (plain axes, arrows, and so on).
Size — changes the drawn size of the tracking markers.

Mesh Edit Mode Overlays — available while in Mesh Edit Mode:
Faces — highlights selected faces, in every selection mode.
Center — shows face center points in solid shading modes (they always appear in wireframe shading). Applies only in face-selection mode.
Creases — shows edges marked with a crease for the Subdivision Surface Modifier.
Sharp — shows sharp edges used by the Edge Split modifier.
Bevel — shows the weights created for the Bevel Modifier.
Seams — shows the UV-unwrapping seams.
Indices — shows the indices of selected vertices, edges, and faces.

Shading:
Retopology — handy when you've sculpted a mesh into the shape you want and need to rebuild it with cleaner topology. It makes the edited mesh see-through (so the sculpt shows beneath it) and can optionally draw it in front of nearby geometry (so you can see it over the sculpt).
Offset — how far to pull the edited mesh toward the camera; use it to display the mesh ahead of objects that would normally hide it.

Vertex Groups Weights — shows the active vertex group's weights, much as Weight Paint mode does.
Zero Weights — paints unreferenced and zero-weighted regions black, helping you spot spots where very low weight has been applied.
  None — vertices appear as normal.
  Active — vertices read black if they carry no weight in the active vertex group.
  All — vertices read black if they carry no weight in any vertex group.

Mesh Analysis — shows the Mesh Analysis overlay.

Measurement — shows numeric measures of the selected elements, with Units set in the Scene properties.
Edge Length — the length of selected edges.
Edge Angle — the angle a selected edge forms between two faces.
Face Area — the area of selected faces.
Face Angle — the angle at selected face corners.
Tip: geometry attached to the selection is shown during a transform, so you can drag a vertex and watch the connected edge lengths update, for instance.
Note: these readings honor the Transform Space set in the Sidebar; choose Global if you want the object's scale folded into the measurements.
See also the Measure tool, which gauges whatever distances and angles you single out.

Normals — three independent toggles: one for vertex normals, one for split normals (face normals drawn at each vertex), and one for plain face normals.
Size — how large the chosen normals are drawn.
Constant Screen Size Normals — keeps the normals a fixed size regardless of zoom.

Freestyle — these settings target the Freestyle Line Art renderer.
Edge Marks — shows Freestyle edge marks.
Face Marks — shows Freestyle face marks.

Sculpt Mode Overlays:
Mask — overlays Masks onto an object, with adjustable opacity.
Face Sets — overlays Face Sets onto an object, with adjustable opacity.

Vertex Paint Overlays:
Stencil Mask Opacity — has no effect here (stencil masks exist only for texture painting).
Show Wire — draws mesh edges in white (whereas the Wireframe overlay draws them black).

Weight Paint Overlays:
Opacity — the overlay's opacity.
Zero Weights — paints unreferenced and zero-weighted regions black, helping you locate spots with very low painted weight.
  None — vertices appear as normal.
  Active — vertices read black with no weight in the active vertex group.
  All — vertices read black with no weight in any vertex group.
Show Weight Contours — draws contour lines linking points of equal interpolated weight. This exposes weight variation too subtle to read from color alone and is useful for judging how smooth and even a gradient is, e.g. while using smoothing tools and brushes.
Show Wire — draws mesh edges in white (the Wireframe overlay draws them black).

Texture Paint Overlays:
Stencil Mask Opacity — the opacity of the stencil-mask overlay.

Pose Mode Overlays:
Fade Geometry — keeps the bones up front and pushes other geometry to the back, with opacity on a slider; available only in Pose Mode.

Grease Pencil — these overlays appear when a Grease Pencil object is selected.
Onion Skin — shows ghosts of the keyframes flanking the current frame; with Multiframe on, it instead ghosts the selected keyframes (see Onion Skinning).
Active Object Only — limits the onion skins to the active object.
Fade Inactive Layers — lowers the opacity of every layer in the object except the active one, controlled by a slider.
Fade Inactive Objects — covers the whole viewport apart from the active Grease Pencil object with a solid-color layer, improving visibility while you draw over busy scenes.
Fade Grease Pencil Objects — includes or excludes Grease Pencil objects.
Edit Lines (Edit, Sculpt, Weight Paint, or Vertex Paint Modes; Shift-Q) — draws a line between points on top of other geometry while you edit strokes.
Only in Multiframe (Shift-Alt-Q) — with Multiframe on and keyframes other than the current one selected, those keyframes' strokes show as edit lines only, the strokes themselves hidden; this leaves Onion Skinning untouched.
Handles — sets the visibility of Bézier curve handles in edit mode.
  None — hides every Bézier handle for an unobstructed look at the curve.
  Selected — shows handles only for selected control points.
  All — shows handles for all of the curve's control points.
Stroke Direction (Edit) — toggles drawing the selected strokes' start points (green) and end points (red) to reveal their direction.
Material Name (Edit) — shows the material name beside the selected strokes.
Vertex Paint Opacity (Vertex Paint) — how opaque the vertex-color overlay appears, taking effect in both Vertex Paint Mode and Draw Mode. In Draw Mode vertex paint is by default visible only in Material Preview and Rendered shading; to see it in Solid mode, either switch to Vertex Paint Mode or set the Color shading option to Attribute.

Canvas — draws a grid across the Grease Pencil drawing plane.
Canvas Grid Opacity — the grid's opacity.
Canvas X-Ray — draws objects behind the canvas grid.
Subdivisions — the count of subdivisions dividing one grid line from the next.
Grid Color — what color those grid lines are drawn in.
Scale X/Y — the grid's horizontal/vertical size.
Offset X/Y — how far to shift the grid up/down and left/right.

## Viewport Shading

Reference — Mode: All Modes. Location: Header ‣ Viewport Shading. Shortcut: Z, Shift-Z.

Blender ships several shading modes suited to different jobs — Solid works well for modeling, for example, while Rendered helps when setting up lighting. The radio buttons switch mode, and the drop-down opens a popover of extra options below. Pressing Z brings up a pie menu of modes, and Shift-Z flips between your current mode and Wireframe.

Wireframe — draws only the objects' edges.
Wireframe Color — how wireframes are tinted; affects both the Wireframe shading mode and the overlay.
  Theme — uses the Active Object, Wire, or Wire Edit theme color according to the object's state.
  Object — uses the color from the object's Viewport Display settings.
  Random — gives each object a random color.
Background — how the 3D Viewport's backdrop is drawn.
  Theme — uses the theme background, configurable under 3D Viewport ‣ Theme Space ‣ Gradient Colors in the Themes Preferences.
  World — uses the World's Viewport Display color.
  Custom — picks a custom backdrop color.
Options:
  X-Ray (Alt-Z) — makes objects transparent so you can see and select items otherwise hidden behind them; the slider sets opacity.
  Outline — draws an outline around objects, with an adjustable color.

Solid — drives the 3D Viewport through the Workbench Render Engine, showing solid geometry with simplified shading and lighting and no shader nodes. It's strong for modeling and sculpting, with plenty of options to bring out specific geometric features.
Lighting — how light is computed.
  Flat — skips lighting entirely and renders the scene's base color.
  Studio — lights objects with studio lights, configured in the preferences; these can track the camera or stay fixed, and when fixed their angle is adjustable.
    World Space Lighting — uses world-space lighting so the lights don't follow the view camera.
    Rotation — the studio lights' rotation about the Z axis.
  MatCap — lights the scene with a material capture; MatCaps flip horizontally via the Flip MatCap button, and custom ones load in the preferences.
Object Color — where viewport objects take their color from.
  Material — the per-material color from the Viewport Display Material panel.
  Object — the per-object color from the Viewport Display Object panel.
  Random — a random color per object.
  Attribute — the object's active Color Attribute; with none active it falls back to the Viewport Display Object panel color.
  Texture — takes its color out of the active image-texture node, sampled via the active UV map; with no active texture it falls back to the Viewport Display Material panel.
  Custom — one chosen color for the entire scene.
Background — how the 3D Viewport's backdrop is drawn.
  Theme — the theme background, configurable under 3D Viewport ‣ Theme Space ‣ Gradient Colors in the Themes Preferences.
  World — the World's Viewport Display color.
  Custom — a custom backdrop color.
Options:
  Backface Culling — hides the back sides of faces via backface culling.
  Outline — draws an outline around viewport objects, with an adjustable color.
  Specular Highlighting — renders specular highlights. Note: available only when Lighting is Studio, or when the chosen MatCap carries a specular pass.
  X-Ray (Alt-Z) — renders the scene transparent, with the slider controlling how transparent it looks.
  Shadow — casts a crisp shadow into the scene.
    Darkness — how dark that shadow renders, from 0 (invisible) to 1 (black).
    Shadow Settings: Direction controls the shadow-casting light's direction; Offset sets the shadow termination angle and can curb self-shadowing artifacts; Focus governs the falloff at the shadow's edge.
  Depth of Field — applies the active camera's Depth of Field settings in the viewport; visible only while looking through the camera. The settings live on the Properties ‣ Camera ‣ Depth of Field panel.
  Cavity — accentuates ridges and valleys in the scene's geometry.
    Type — the method used to compute cavity. World is more accurate but slower; Screen is fast but ignores the size of the ridges and valleys; Both applies the two methods together.
    Ridge — controls how visible the ridges are.
    Valley — controls how visible the valleys are.

Material Preview — renders the 3D Viewport with EEVEE plus an HDRI environment, making it well-suited to previewing materials and painting textures, since you can swap lighting conditions to test materials. Note: it's unavailable when the scene's render engine is Workbench.
Lighting:
  Scene Lights — uses the scene's lights; when off (or with no lights present) a virtual light fills in.
  Scene World — uses the scene's World; when off, a world is built from the options below.
  HDRI Environment — the environment map lighting the scene.
  Rotation — the environment's rotation about the Z axis.

World Space Lighting — pins the lighting rotation so it no longer follows the camera.
Strength — the environment's light intensity.
World Opacity — how opaque the HDRI is as a backdrop in the viewport.
Blur — a factor that defocuses the HDRI; note this changes only the backdrop's look, not how the lighting diffuses.
Render Pass — instead of the combined render, displays one specific render pass, which helps when analyzing or debugging geometry, materials, and lighting.
Compositor — when to preview the compositing result in the 3D Viewport.
  Disabled — never show the compositing output.
  Camera — show it only in Camera View, the spot that best previews how the final image will look.
  Always — always show the compositing output.

Rendered — renders the 3D Viewport through the scene's Render Engine for interactive rendering, previewing the final pre-composite result including scene-lighting effects. Its options match Material Preview, except that the Render Pass selector offers a different set of passes when the scene uses the Cycles render engine.

## Object Type Visibility

Reference — Mode: All Modes. Location: Header ‣ Selectability & Visibility.

This popover governs which object types stay visible and selectable — for instance, one click can hide every Light in the scene.

The choices apply only to the current 3D Viewport: a type flagged unselectable here can still be selected in other viewports and in the Outliner.

Note: the object types act on the evaluated geometry type, not the original. A mesh object turned into a volume by geometry nodes, for example, stays visible even with the Mesh option unchecked.

See also Outliner Restriction Columns, which can hide or lock a single object throughout every viewport.

## Camera View

The Camera view presents the scene from the active camera's vantage point. Use it to block out shots and preview the rendered look — everything inside the dashed frame ends up in the rendered image.

See also Camera Settings for how camera settings drive display and rendering.

Hint: while looking through the camera, a click on its dashed frame selects it, as long as the camera object isn't hidden.

Viewing the Active Camera — Reference: Mode: All Modes; Menu: View ‣ Cameras ‣ Active Camera, View ‣ Viewpoint ‣ Camera; Shortcut: Numpad0. Flips the view to the active camera.

Setting the Active Camera — Reference: Mode: Object Mode; Menu: View ‣ Cameras ‣ Set Active Object as Camera; Shortcut: Ctrl-Numpad0. Promotes the current active object to active camera and switches to camera view. The active camera is the one used for rendering and the one you look through when you choose camera view. You can also assign it from the Scene tab of the Properties. Note: the active camera is normally a scene-level setting, identical across all 3D Viewports, but you can also make a camera active within a single Viewport only (see Local Camera).

Animated Camera Switching — a scene starts with one camera but may hold several, and you can bind cameras to specific points on the timeline to cut between viewpoints (see Animating Cameras).

Frame Camera Bounds — Reference: Mode: All Modes; Menu: View ‣ Cameras ‣ Frame Camera Bounds; Shortcut: Home. Centers the camera view within the 3D Viewport's area and resizes it to fit the area's bounds.

Zoom Camera 1:1 — Reference: Mode: All Modes; Menu: View ‣ Navigation ‣ Zoom Camera 1:1. Zooms so the camera frame matches the output resolution exactly, letting you preview precisely how big objects will appear in the rendered image/animation.

Camera Positioning — there are several ways to place a camera, letting you align it to the viewport, navigate while driving the camera, or perform classic cinematography moves. Hint: the active "camera" can be any object serving as the scene camera, and these techniques work for positioning and aiming other objects, such as lights, too.
Align Active Camera to View — see Align Active Camera to View. This operator matches the active camera to the current 3D View, useful once you've framed a composition in the viewport and want the camera dropped exactly there.
Camera Navigation — turn on Lock Camera to View and switch to camera view (Numpad0); with this on, navigating the viewport moves the camera rather than the view. You can also toggle the lock via the navigation gizmo while in camera view. This lets you position the camera interactively with the usual navigation controls. See also Fly/Walk Navigation for first-person navigation that likewise drives the active camera.
Roll, Pan, Dolly, and Track — to make these moves the camera must be selected (so transforms target it) and you should be in camera view. Then manipulate it with the same tools you'd use on any object:
  Roll — press R to start rotation; by default it rotates about the camera's local Z axis (the one perpendicular to the camera view), which is precisely a camera "roll".
  Vertical Pan or Pitch — a rotation about the local X axis: press R, then X twice (the first press chooses the global axis, the second the local; this works for any axis — see Axis Locking).
  Horizontal Pan or Yaw — a rotation about the camera's local Y axis: press R, then Y twice.
  Dolly — hit G, then MMB (pressing Z twice does the same thing).
  Sideways Tracking — begin with G and drag the mouse (tapping X or Y twice restricts it to purely horizontal or vertical tracking).

## View Regions

Clipping Region — Reference: Mode: All modes; Menu: View ‣ View Regions ‣ Clipping Region…; Shortcut: Alt-B. Lets you carve out a clipping region that restricts the 3D Viewport's display to a slice of 3D space, which helps when wrangling complex models and scenes. After activating it, drag a rectangle with the mouse; that becomes a four-plane clipping volume — a right-angled parallelepiped of infinite length under an orthographic view, or a rectangular-based pyramid of infinite height under perspective. With clipping on, only what's inside the volume shows, and tools like paint, sculpt, selection, and transform snapping ignore geometry beyond the bounds too. Press Alt-B again to clear it.

Example: the region/volume clipping illustration shows the tool used on a cube. Start it with Alt-B to get a dashed cross-hair cursor, then LMB-drag a rectangular region; clipping now applies to that slice of 3D space. Rotate with MMB and you'll see only what lies inside the clipping volume, with every editing tool still working but only within that volume. The dark gray area is the clipping volume itself, and once you deactivate it with another Alt-B, all of 3D space returns.

Render Region — Reference: Mode: All modes; Menu: View ‣ View Regions ‣ Render Region…, View ‣ View Regions ‣ Clear Render Region; Shortcut: Mark: Ctrl-B, Clear: Ctrl-Alt-B. Confines rendering to a rectangular 2D area. When you're tweaking just a small part of a scene, putting the whole viewport in Rendered shading or making full-frame renders wastes effort, so this saves time. You can define Render Regions in two contexts: set one while in Camera View and it applies both to the viewport and to the final render (to suspend it without clearing, use the Output tab of the Properties editor); set one outside Camera View and it applies to the viewport only (suspend it without clearing via the Sidebar). Both Render Regions can coexist. Note: under Cycles render regions affect the viewport, but under EEVEE they don't; either way they always affect the final render. See also Zoom Region.

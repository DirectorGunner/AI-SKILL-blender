# Introduction (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

In Pose Mode bones act like objects, so the transform actions (move, rotate, scale, all grouped in Pose ‣ Transform) resemble Object Mode's, with some specifics: bone relationships matter (see Bone Parenting), and a single bone's transform center (its default pivot when it alone is selected) is its root — note that some pivot-point options seem off, since apart from 3D Cursor they all appear to use the selection's median rather than, say, the active bone's root. Basic posing: transforms are based on the armature's Rest Position from Edit Mode, so in rest position each Pose-Mode bone has scale 1.0 and zero rotation and position (visible in the Sidebar Transform panel). The local space for these actions is the bone's own (shown when the Armature panel's Axes option is on), which matters for axis locking — there's no dedicated "bone roll" tool in Pose Mode because you rotate around the bone's main axis just by locking to local Y (R Y Y), and with several bones selected each locks to its own local axis. When posing you typically have objects skinned to the armature, so transforming a bone deforms its objects in real time; with a complex rig or heavy skin this can lag during interactive editing, in which case enable the Armature panel's Delay Deform button so the skin updates only once you confirm the transform.

Drivers control a property's value through a function or math expression. A driver has two parts: a driver configuration that takes zero, one, or more input values from other properties or transformation channels and combines them with a predefined function or a custom Python expression; and an animation F-Curve that maps the configuration's output to the final value applied to the driven property. For example, Object 2's scale can control Object 1's rotation — so Object 2's scale is said to drive Object 1's rotation. Drivers can not only set one property to another's value but also combine several values with a function or expression and further shape them with a manual curve and/or a modifier stack — making them an extremely powerful rigging tool, typically driving bone transforms and the influence of shape keys, action constraints, and modifiers, frequently from custom properties. Graph view: the Drivers editor's main area shows an F-Curve representing the driver function, where the X axis maps the configuration's output value (units depending on the setup) and the Y axis the value applied to the property (units depending on the property) — so in the example image a driver value of 2.0 yields a property value of 0.5. The default F-Curve is an identity map (the configuration's output applies unchanged, so output 2.0 gives property 2.0), and the function can be defined artistically with Bézier handles or mathematically with trigonometric functions or polynomials like y = a + bx, and procedurally modulated with noise or cyclic repetition (see Modifiers). Driver configuration: the Drivers panel shows the setup, where a driver has zero, one, or more variables specifying which properties, transformation channels, or inter-object distances feed it, and the driver type decides how the variables are used — a built-in function (e.g. the sum of the variables) or a scripted expression (an arbitrary Python expression referring to the variables by name). The configuration outputs a single value that changes with the variables, which is then run through the driver function curve to produce the value sent to the driven property. Notes on scripted expressions: where a driver uses a Scripted Expression, Blender can evaluate it without the full Python interpreter if it's simple enough, so drivers with simple divisions, additions, and other "simple" expressions are fast (built-in functions are always native) — see Simple Expressions for the full native-eval list. A non-simple expression is run through Python, making the driver slower and posing a security risk if the Python author is unknown, which matters for heavy scenes and shared files (see also Auto run).

Compositing Nodes let you assemble and enhance an image (or movie) — gluing footage together and colorizing the whole sequence at once, or enhancing the colors of a single image or a whole clip statically or dynamically over time — so you use them both to assemble clips and to enhance them. Note: "Image" may mean a single picture, one frame of a numbered sequence, or a movie-clip frame, and the Compositor handles one image at a time whatever the input. To process an image you use nodes to import it into Blender, change it, optionally merge it with others, and save it. Getting started: open the Compositor and make a new node tree with the header's New button, which adds a compositing node-tree data block to the scene (reusable across scenes or linkable from other blend-files) — and importantly, to make the render engine use it (or to disable compositing), the Compositing Pipeline option in the output's Post Processing properties must be enabled. With a tree created you get a first basic setup, from which you add and connect many Compositing Nodes for effects from simple color corrections to complex composites (general node concepts and controls are in the Nodes reference). Examples: you can do almost anything with images — layer blue-screen foreground footage or a rendered object over a background to composite footage, or change an image's mood: a blue tinge to feel colder, softening for a flashback or memory, a red tinge for hatred or frustration, sharpening and added contrast for a startling event, yellow (equal red and green, no blue) for a happy feeling, or an added cloud-texture of dust and airborne dirt for realism. Saving your composite: the Render button renders a single frame; save it with Save Image, using the Render panel's image format settings. To save an image sequence (say a movie-clip input, or a Time node where each frame is a separate file), use the Animation button with its settings, choosing an alpha-capable format like PNG if you may overlay them later, or a Z-depth-capable format like EXR if you may arrange them front-to-back or do depth-of-field; and to save a composite as a single movie file, use an AVI or QuickTime format with the Animation button.

Working in Blender's three-dimensional space means you need to shift both your vantage point and the direction you're looking. The description here centers on the 3D Viewport editor, but most other editors behave similarly — the Image editor, for example, also pans and zooms.

Tip: a few navigation tools want a middle mouse button or a numpad. If you lack either, the manual's Keyboard and Mouse page explains how to work around it.

Navigation Gizmo: you'll find it at the editor's top right. The Orbit gizmo up top reflects the view's current orientation; dragging it with LMB orbits the view, clicking any axis label aligns the view to that axis, and clicking the same axis again jumps to the opposite side of it.

Beneath the orbit gizmo sit four buttons, in order: one zooms the viewport, one pans it, one toggles the Camera View, and one toggles the Projection (or, while in camera view, Lock Camera to View).

The Movie Clip Editor handles tracking and masking of movies.

Header — Mode:
Tracking — for dropping markers onto a video and following their motion.
Mask — for creating masks and animating them.

View Type:
Clip — the standard view, where you place and track markers.
Graph — charts the markers' movement speed on a graph.
Dope Sheet — gives a timeline overview of marker keyframes.

View Menu:
Toolbar (T) — shows or hides the left-hand tab panel for creating and working with markers and masks.
Sidebar (N) — shows or hides the Sidebar.
Adjust Last Operation — opens a pop-up panel for changing the properties of the operation you just finished.
Show Metadata — displays any metadata baked into the video, if present.
Frame All (Home) — zooms and pans so the whole video fits in view.
Frame Selected (NumpadPeriod) — zooms and pans to center the selected items.
Center View to Cursor (Mask Mode) — pans so the 2D Cursor sits at the center.
Zoom — a menu of handy zoom levels and operations, the levels figured from the image resolution against the screen resolution: 12.5% (1:8) Numpad8 zooms out to 12.5%; 25% (1:4) Numpad4 to 25%; 50% (1:2) Numpad2 to 50%; 100% (1:1) Numpad1 resets to 100%; 200% (2:1) Ctrl-Numpad2 zooms in to 200%; 400% (4:1) Ctrl-Numpad4 to 400%; 800% (8:1) Ctrl-Numpad8 to 800%.
Zoom In/Out (Wheel) — zooms in or out.
Zoom to Fit (F) — behaves like Frame All but grabs as much editor space as possible.
Area — area controls; see the user-interface documentation.

Select Menu — for selecting markers and masks.
Clip Menu — for loading movie clips and building proxies.
Track Menu — for running tracking operations.
Reconstruction Menu — for setting up the reconstruction of 3D information from the points tracked in the 2D video.
Add Menu — adds primitive mask shapes: Circle adds a circular mask, Square a square one.
Mask Menu — operators for editing masks.

Other:
Clip — a data-block menu for loading and choosing movies; both video files and image sequences work, and loading a clip adds extra panels to the interface.
Pivot Point — see Pivot Points.
Proportional Editing (Mask Mode) — see Proportional Editing.
Mask (Mask Mode) — a data-block menu for creating and choosing masks.
Mask Display (Mask Mode) — see Mask Display.
Toggle Lock Selection (L) — keeps the view panning to follow the selected markers, so they hold the same on-screen spot during tracking and playback. This "locks the view onto the selection" and shouldn't be confused with the Sidebar's Lock option, which instead stops you changing the active marker.
Clip Display — see Clip Display.
Gizmos — see Viewport Gizmos.

Blender lets you animate almost any property, from an object's X coordinate to a material's transparency. How a property's value evolves over time is described by a function curve, or F-Curve.

A crucial trait of F-Curves is interpolation, which spares you from setting a value on every single frame — wildly impractical. Instead you place a few values on key frames and let the curve work out the rest.

In the example curve, two keyframes (the black dots) sit at frame 0 with value 0 and frame 25 with value 10; the curve fills in the other frames automatically, giving value 2 at frame 5, for instance.

Direction of Time — F-Curves resemble Curve objects in that they interpolate among user-placed control points. But since their job is to yield one value per frame, there's a key catch: they can't be closed or doubled back on themselves — they always press onward to the right. Try to drag one control point past another to make the curve go left, and it simply swaps the points' order to stop you.

The Image Editor lets you create, view, and edit images, and also see render results and intermediate Compositor output.

Toolbar:
Sample — reads the color of one or more pixels; while you hold LMB the footer shows the cursor's X and Y, the color in RGBA, the color in RGB after Color Management, the color in HSV, and the Luminance.
Sample Size — the side length of the square used to sample underlying pixels; above 1, the result averages all the pixels it covers.
Annotate — see Annotations.

Header — Mode: View (displays images), Paint (Texture Paint), Mask (Masking).
View — tools for how content is shown in the editor (see Navigating).
Image — tools for opening and manipulating images; an asterisk marks unsaved changes (see Editing Images).
Image — a data-block menu for choosing images; once one is chosen, the Image tab appears in the Sidebar. Beyond loading existing images you can also create new ones — the New Image pop-over's Tiled option makes a UDIM-capable image, and for the rest see Generated Images. The data-block selector also lists Render Result (displays renders; selecting it enables the Slot, View Layer, and Render Pass selectors below) and Viewer Node (displays whatever feeds the Compositor's Viewer Node).
Image Pin — stops the Image Editor from auto-switching to the selected object's texture (which only happens when the 3D Viewport is in Texture Paint mode).
Show Sequencer Scene — appears on the Render Result only when a Sequencer Scene exists and differs from the window's active scene; after a render its state gets picked automatically based on the render type.
Slot — the render slot to view and render into; pick an empty slot before rendering to keep earlier renders, then compare with J and Alt-J to cycle forward and back, or press number keys 1, 2, 3, etc. to jump to a slot. Rename slots by double-clicking their name in the Sidebar's Image panel.
View Layer — which View Layer to show.
Render Pass — which Render Pass to show.
Viewport Gizmos — toggle all gizmos with the button or specific ones via the drop-down.
  Navigate — turns the pan/zoom gizmos for the 2D viewport on or off (see Navigation Gizmos).
Display Channels — choose which color channels appear.
  Color & Alpha — turns on transparency, with a checkerboard shown behind the image.
  Color — disables transparency.
  Alpha — shows the alpha channel in grayscale; white is opaque, black transparent.
  Z-Buffer — shows depth from the camera, between Clip Start and Clip End from the Camera settings.
  Red, Green, Blue — one color channel shown as grayscale.

Asset Shelf Region — depending on the mode, the asset shelf may appear for quick access to mode-specific assets (brush assets in Paint mode, for instance); see Asset Shelf.

Main View — holding RMB samples the image like the Sample tool, except it always reads just one pixel.

The NonLinear Animation editor, or NLA editor, lets you animate at a higher level: instead of individual keyframes, it works with actions — named, reusable animation segments.

Main Region — the editor shows a stack of tracks that behave like layers in an image editor, higher tracks taking precedence over lower ones, though you can also blend them. Each track can hold any number of strips, usually Action Strips (instances of actions). The orange-highlighted top track is special: the Action Track holds no strips but instead the object's active action, where new keyframes go by default. Editors like the Dope Sheet Editor normally show only this active action's keyframes; to edit another action, select it in the NLA editor and press Tab for Tweak Mode.

Header — View Menu:
Sidebar (N) — shows or hides the Sidebar Region.
Adjust Last Operation — opens a pop-up to alter the last operation's properties (see Adjust Last Operation).
Channels — shows or hides the Track Region.
Playback Controls — shows or hides the Playback Controls.
Frame Selected (NumpadPeriod) — pans and zooms onto the selected strips.
Frame All (Home) — pans and zooms to show every strip.
Frame Scene/Preview Range — resets the horizontal view to the scene frame range, honoring the preview range if active.
Go to Current Frame (Numpad0) — centers the view on the Playhead.
Realtime Updates — whether other views (the 3D Viewport, say) refresh while you drag strips; off, they update only when you finish.
Show Control F-Curves — draws a graph atop each strip that uses Animated Influence.
Show Markers — shows the marker region (when markers exist); off, the Marker Menu hides and marker operators are unavailable here.
Show Local Markers — shows action-local markers (made in the Action Editor), useful for aligning strips to one another.
Use Timecode (Ctrl-T) — shows timing in seconds rather than frames.
Sync Visible Range — keeps the editor's horizontal pan and scale in step with other time-based editors that enable this, so they show the same slice of time.
Set Preview Range (P) — drag a box to set a preview time range; while active, playback stays inside it for replaying a segment without rewinding. Change its start/end with the matching button in the Timeline editor's Playback popover, or just run Set Preview Range again.
Clear Preview Range (Alt-P) — clears the preview range.
Set Preview Range to Selected (Ctrl-Alt-P) — sets a preview range spanning the selected strips.
Area — area controls; see the user-interface documentation.

Select Menu:
All (A) — selects every strip.
None (Alt-A) — deselects every strip.
Invert (Ctrl-I) — flips the current selection.
Box Select (B) — drag a box to select strips partly or wholly inside it.
Box Select (Axis Range) (Alt-B) — drag a box to select strips overlapping the matching time range, even above or below the box.
Before Current Frame ([) — selects every strip starting at or before the current frame.
After Current Frame (]) — selects every strip ending at or after the current frame.

Marker Menu — markers flag frames carrying key points or notable events and, as in most animation editors, appear along the bottom. For the marker tools, see Editing Markers.

Add Menu:
Action (Shift-A) — drops a strip that references an action onto the active track.
Transition (Shift-T) — inserts a transition strip linking the two selected action strips.
Sound (Shift-K) — adds a strip controlling when a Speaker Objects plays its sound clip.
Selected Objects — makes the selected objects show up in the NLA Editor without adding an action or track.
See Strips for the various strip types.

Track Menu — tools for NLA tracks (see Editing Tracks).
Strip Menu — tools for NLA strips (see Editing Strips).

Filters:
Only Show Selected — shows only tracks of selected objects.
Show Hidden — shows tracks of hidden objects.
Include Missing NLA — shows the Action Track even when it holds no action.
Search — filters the track list by a search term.
Filtering Collection — pick a collection to show only its objects' tracks.
Filter by Type — filters tracks by target type.
Sort Data-Blocks — sorts data-blocks alphabetically for easier finding; if it slows playback (really only with many objects), switch it off.

Snap — the toggle enables/disables automatic strip snapping; the dropdown adds:
Snap To — the element to snap to: Frame (whole frames), Second (seconds), Nearest Marker (the closest Marker).
Absolute Time Snap — off, strips move in increments of Snap To; e.g. with Second and a strip starting on 0:06+5, dragging right snaps it to 0:07+5, gaining a second while keeping its 5-frame subsecond offset.

On, strips snap to multiples of Snap To, so in that same example the strip lands on 0:07+0, losing the subsecond offset.

Playback Controls — this region holds controls and options for playback, keying, auto keyframing, and transport. They let you control how animations preview and sync with audio, add and manage keyframes via keying sets and auto keying, navigate the timeline with playback and transport controls, and set frame ranges and preview chosen segments. See also the Playback Controls documentation for the full footer rundown.

The Texture Node Editor lets you build custom textures by combining colors, procedural patterns, and images in assorted ways — a step beyond the built-in textures, where you mostly just pick a type from a list.

Note: textures — built-in and node-based alike — are a legacy feature. For their original main job, texturing objects, they've been superseded by Materials, set up in the Shader Editor. These days Textures are used only for:
Brushes.
The Displace Modifier.
Influencing the size, density, etc. of particle systems.
Influencing where fire/smoke simulations emit.
On top of that, the Displace modifier and fire/smoke simulations don't accept node-based textures and work only with the built-in ones.

Using Texture Nodes — the default Blender layout has no workspace with the Texture Node Editor, so you open it yourself in an area of choice. Once it's open, set the empty Texture Type selector to Brush, then use the Data-Block Menu to start creating textures; note that you must switch on Use Nodes in the header before nodes can be added.

Header — see Nodes for the header items shared by all node editors.
Texture Type:
  World — deprecated; the scene's World Environment now comes from a Material instead of a Texture.
  Brush — shows brush Textures in the data-block menu; since the other two types are deprecated, this effectively shows every Texture.
  Line Style — deprecated; Line Styles for the Freestyle renderer are now defined with Materials rather than Textures.

The UV Editor is for editing UV maps, which describe how a 2D image should wrap onto a 3D object.

Image textures are usually needed when the look you want is hard to get from procedural textures, or when the texture isn't uniform — a car, for instance, would have scratches only in a few sensible spots, not scattered randomly over its body. Blender offers several projections (Box, Sphere…) that auto-apply a 2D image to a 3D object, but those tend to suit only simple meshes; for trickier ones you build a UV map instead — a flat layout where each face of the 3D object is placed on the 2D image, marking which part of the image textures it, giving you full control of the mapping. The name "UV" points to the map's axes — U for horizontal, V for vertical — letters chosen so they don't clash with "X" and "Y", which name axes in 3D space.

UVs Explained — the clearest analogy is cutting up a cardboard box: snip along its edges with scissors and you can spread it flat on a table; looking down at it, U is the left-right direction and V the up-down. Next, lay the flattened box on a poster, cut the poster to its shape, glue the poster to the box, and reassemble — now you have a 3D box textured with a 2D image. A UV map, then, describes how the mesh's faces sit on the texture, and you have complete freedom in doing it: you could cut each face loose and position, rotate, scale, even skew it on the texture independently, and faces can overlap in the UV map to share the same patch of texture.
Example — in the image, a dome in 3D space is flattened to a disc in UV space, and each 3D face then gets the slice of the image it overlaps in the UV map. It also shows a common UV problem, distortion: although the checkered squares in the 2D texture are all one size, they come out different sizes on the 3D dome (smaller at the base than the top), because the UV-map faces have different relative sizes than in 3D space — a side effect of flattening. You'll usually want to minimize this by guiding and tweaking the flattening, with seams for example, though it can't always be wiped out entirely.

Interface — Header — the header holds several menus and options for working with UVs.
Sync Selection — keeps the selection in step across the UV Editor and the 3D Viewport (see Sync Selection).
Selection Mode — the UV element type to select (see Selection Mode).
Sticky Selection Mode — which other vertices to select automatically (see Sticky Selection Mode).
View — tools for how content is shown in the editor (see Navigating).
Select — tools for selecting UVs.
Image — tools for opening and manipulating images (see Editing Images).
UV — tools for Unwrapping Meshes and Editing UVs.
Pivot (Period) — see Transform Pivot Point.
Snap (Shift-Tab) — see Snapping.
Proportional Editing (O) — see Proportional Editing.
Image — a data-block menu for choosing images; once one is loaded or created here, the Image panel appears in the Sidebar.
Image Pin — when on, the current image stays visible regardless of the object selection; this switching only happens while the 3D Viewport is in Edit Mode or Texture Paint Mode, and it's handy when an image serves as reference.
(Show Gizmo) — toggle all gizmos with the button or specific ones via the drop-down. Navigate — turns the pan/zoom gizmos for the 2D viewport on or off (see Navigation Gizmos).
Show Overlays — toggle all overlays with the button or specific ones via the drop-down (see UV Overlays).
Active UV Map Layer — choose which UV map to use.
Display Channels — choose which color channels appear. Color & Alpha (enables transparency with a checkerboard behind the image), Color (the colored image, no alpha), Alpha (the alpha channel in grayscale — white opaque, black transparent), Z-Buffer (depth from the camera between Clip Start and Clip End per the Camera settings), or Red, Green, Blue (one channel as grayscale).

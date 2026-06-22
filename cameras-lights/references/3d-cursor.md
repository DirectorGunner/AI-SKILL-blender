# 3D Cursor, Global Transform, Align View, Navigation ...

> Blender Cameras, Lights, and Rendering reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: 3D Cursor; Global Transform; Align View; Navigation; Perspective/Orthographic; Fly/Walk Navigation; Sidebar.

## 3D Cursor

The 3D Cursor is a point in 3D space holding both a location and a rotation, and acting as a reference point for many Blender operations. Newly added objects appear at its location by default; the Cursor can also define the pivot for transformations, control tool orientation, and act as a target for snapping and placement. Certain modeling and transformation tools — Bend among them — treat the Cursor as their center of influence, and the Cursor's position and orientation can serve as the Pivot Point or as a Transform Orientation. Placement — several methods position the Cursor depending on the precision you need. Direct placement with the mouse (Reference — Mode: Object, Edit, and Pose Mode; Tool: Cursor; Shortcut: Shift-RMB): the Cursor tool is the most flexible way — select it in the Toolbar and click a scene location with LMB. The tool settings control orientation: View (align to the current view), Surface (align to the surface normal under the pointer), or Transform Orientation (use the currently selected transform orientation). Alternatively, press Shift-RMB with any tool active for a quick placement, in which case the Cursor always aligns to the view. For precise placement, two perpendicular orthographic views help, such as Top (Numpad7), Front (Numpad1), and Right (Numpad3), letting you set two axes in one view while adjusting depth in the other. By default the Cursor projects onto the surface under the mouse, which can be disabled via the Cursor Surface Project option in the Preferences. Sidebar (Reference — Mode: All Modes; Panel: Sidebar region ‣ View ‣ 3D Cursor): edit the Cursor's position and rotation numerically here for precise coordinate entry, adjusting both Location and Rotation to orient tools or transformations relative to the Cursor. Snapping: several operators align the Cursor to scene elements — Cursor to Selected (to the selected objects), Cursor to World Origin (to the world origin), Cursor to Grid (to the nearest grid-overlay point), and Cursor to Active (to the active object's origin) — useful for precisely aligning the Cursor with geometry or scene elements. Usage — the Cursor is a flexible reference point that, unlike most scene elements, stores both a position and an orientation, acting as a temporary coordinate system for many operations, so it's often used as a placement guide, transformation reference, or target location. Object placement: new objects are created at the Cursor by default, handy for precisely positioning new geometry, lights, cameras, or other elements before creation — artists commonly move the Cursor first, then add objects where needed. Transform reference: with the Transform Pivot Point set to 3D Cursor, rotate or scale operations occur relative to the Cursor's location, and the Cursor's rotation can define a Transform Orientation to align objects to custom directions. Modeling workflows: many operations use the Cursor as a center or reference — for example the center of spin, mirror, or other tools needing a user-defined origin — and it's commonly paired with snapping to place geometry or align objects precisely. Viewport navigation: the Cursor can influence the viewport too — Center View to Cursor centers the viewport on it, and Lock ‣ To 3D Cursor locks navigation to the Cursor instead of the active selection, making it a navigation anchor. Cursor-based operators: Selection to Cursor (moves selected objects to the Cursor's position and orientation) and Center Cursor and Frame All (moves the Cursor to the world origin and frames the whole scene). Because the Cursor is lightweight and easy to reposition, it makes a convenient temporary reference throughout Blender.

## Global Transform

Global Transform copies and pastes object and bone transforms easily. Copying places the global (World Space) transform on the clipboard, which you can then paste onto any object or bone, at the current frame or another. Reference — Panel: 3D Viewport ‣ Sidebar ‣ Animation ‣ Global Transform. The Copy Global Transform panel's main functions: Copy (inspect the active Object in Object mode or Bone in Pose mode and place its current global transform on the clipboard as a matrix); Paste (apply the copied global transform to the active Object or Bone by adjusting its location, rotation, and scale properties); Mirrored (like Paste but mirrored relative to another object or bone — useful, for example, to copy one foot's position to the other; see Mirror); Paste to Selected Keys (paste and additionally auto-key one or more frames, the key selection telling Blender which frames to act on but not which transform parts to key, which the active keying set determines); and Paste and Bake (almost the same, but instead of only the selected keys it pastes and auto-keys on each frame spanning the first through the last selected key). Mirror — the copied transform can be mirrored relative to an object or bone, chosen first: Object (mirror relative to the chosen object; choosing an Armature object shows the bone selector to pick a mirror bone, always using that named bone on that specific armature) and Bone (with no mirror object chosen, you can still pick a bone name to mirror against a bone in the active armature — useful, for example, to mirror bone transforms relative to a character's 'chest' bone); after 'Paste Mirrored', the mirror axes are chosen in the redo panel. Relative — the "Relative" panel's copy/paste buttons work relative to a chosen object: copying determines the world-space transform and makes it relative to the chosen object's world-space transform, and pasting reverses this; with no object chosen, copy/paste happens relative to the active scene camera (determined for each action, so a paste's camera can differ from the copy's), which helps keep an object visually in place when switching cameras or scenes. Fix to Camera — also called "bake to camera," this operator keeps selected objects/bones static relative to the camera on unkeyed frames by generating new keys of type 'Generated', so it stays clear which keys were manual versus generated and the tool can be re-run to regenerate them. Steps: ensure the animation is keyed with constant interpolation (if not, bake at least the transform channels — the tool does not work with the "Stepped" F-Curve modifier); choose which of the Location/Rotation/Scale channels to fix to the camera (when unsure, check them all); and press the "Fix to Camera" button. To undo it, click the trash-bin button, removing all generated keys in the scene or frame range. The tool works on the scene frame range, or the preview range when active, ignoring keys outside that range both when fixing and when removing generated keys. Warning: the tool assumes all keys of type 'Generated' are equal and will overwrite or remove them depending on the button pressed. Limitations: pasting a transform adjusts location, rotation, and scale, so copying a skewed transform loses the skew; and constraints on the Object/Bone may make the resulting visual transform differ from the pasted one — for example, a constraint that adds a rotation always adds it on top of the pasted transform. See also Pose Library for managing and sharing entire poses.

## Align View

These commands reorient the viewport with respect to objects, the scene, or the active camera.

Align View to Active — Reference: Menu: View ‣ Align View ‣ Align View to Active. Squares the view to a local axis of the active object or bone, or (in Edit Mode) to the active face's normal, and also drops the view into orthographic. It's handy for inspecting geometry against an object's local orientation. To get back to a normal perspective view, press Numpad3 to align to the global X axis, then orbit with MMB.

Align Active Camera to View — Reference: Menu: View ‣ Align View ‣ Align Active Camera to View; Shortcut: Ctrl-Alt-Numpad0. Moves and rotates the active camera to match the current viewport position and orientation — commonly used after you've framed a shot in the viewport to drop the camera onto that exact viewpoint.

Align Active Camera to Selected — Reference: Menu: View ‣ Align View ‣ Align Active Camera to Selected. Moves the active camera, without altering its orientation, so the selected objects sit centered in the camera frame.

Center Cursor and Frame All — Reference: Menu: View ‣ Align View ‣ Center Cursor and Frame All; Shortcut: Shift-C. Sends the 3D Cursor to the world origin and reframes the view to take in the whole scene.

Center View to Cursor — Reference: Menu: View ‣ Align View ‣ Center View to Cursor. Centers the viewport on the 3D Cursor.

View Lock to Active — Reference: Menu: View ‣ Align View ‣ View Lock to Active. Centers the view on the active object and makes it the point of interest, so the viewport keeps orbiting that object even as you pan elsewhere; if the object moves, the view tracks it.

View Lock Clear — Reference: Menu: View ‣ Align View ‣ View Lock Clear. Drops the active view lock and restores normal viewport navigation.

## Navigation

Orbit — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Orbit; Shortcut: MMB, Numpad2, Numpad4, Numpad6, Numpad8. Rotate around the point of interest by dragging MMB over the viewport area; RMB cancels the orbit. Alt changes orbiting in several ways: Alt-MMB on a point makes it the new point of interest the view circles; holding Alt and then dragging MMB in a direction squares the view to an axis and goes orthographic; dragging MMB and then holding Alt orbits while snapping to the world axes and the diagonals between them. To step the angle discretely, use Numpad8/Numpad2 for up/down and Numpad4/Numpad6 for left/right, and press Numpad9 to swap to the opposite side of the view (a 180° turn about the Z axis). See also the Orbit Style Preference and the Auto-Perspective Preference.

Roll — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Roll; Shortcut: Shift-Numpad4, Shift-Numpad6. Rotates the viewport camera about its viewing direction in 15° steps by default (configurable via the rotation-angle preference). To zero the roll, square the view to the global X axis with Numpad3, then orbit back to a normal perspective view; RMB cancels the roll.

Pan — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Pan; Shortcut: Shift-MMB, Ctrl-Numpad2, Ctrl-Numpad4, Ctrl-Numpad6, Ctrl-Numpad8. Slides the 3D Viewport left, right, up, or down without rotating, handy for repositioning the view while keeping its orientation:
Shift-MMB — pan freely by dragging.
Shift-WheelUp / Shift-WheelDown — pan vertically.
Shift-WheelLeft / Shift-WheelRight — pan horizontally.
Ctrl-Numpad8 / Ctrl-Numpad2 — pan up/down in fixed steps.
Ctrl-Numpad4 / Ctrl-Numpad6 — pan left/right in fixed steps.

Zoom In/Out — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Zoom In/Out; Shortcut: Ctrl-MMB, Wheel, NumpadPlus, NumpadMinus. Moves the view toward or away from the point of interest; zoom by rolling the Wheel or dragging Ctrl-MMB, or step discretely with NumpadPlus and NumpadMinus. Hint: if you get lost in 3D space (it happens), Frame All and Frame Selected will bring your scene's contents back into view. RMB cancels the zoom.

Zoom Region — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Zoom Region…; Shortcut: Shift-B. Drag a rectangle with LMB to mark a region and the view zooms into it; drag with MMB instead to zoom out.

Dolly View — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Dolly View…; Shortcut: Shift-Ctrl-MMB. Usually zooming is enough for a closer look, but zoom only carries you up to the point of interest and no further. When you hit that wall, Dolly instead by holding Shift-Ctrl and dragging up or down with MMB, which moves the point of interest (and the view with it); RMB cancels the dolly. Hint: dolly converts orthographic views to perspective, because moving forward/backward under an orthographic projection doesn't read as zooming, so dolly works poorly there.

Frame All — Reference: Mode: All modes; Menu: View ‣ Frame All; Shortcut: Home. Adjusts the view so every object is visible.

Frame Selected — Reference: Mode: Object, Edit, Pose; Menu: View ‣ Frame Selected; Shortcut: NumpadPeriod. Adjusts the view so the selected object(s) are visible.

Frame Last Stroke — Reference: Mode: Texture Paint, Vertex Paint, Weight Paint, Sculpt; Menu: View ‣ Frame Last Stroke; Shortcut: NumpadPeriod. Centers the view on the area of the most recent brush stroke.

Orbit & Pan:
Orbit Method — your preferred way of interactively rotating the 3D Viewport.
  Turntable — rotates while keeping the horizon level, like a potter's wheel or record player: two axes of rotation, and the world keeps a clear sense of "up" and "down." The trade-off is some lost flexibility with your objects, but you gain that orientation, which helps when you feel disoriented.
  Trackball — less restrictive, allowing any orientation.
Orbit Sensitivity — tunes how responsive and fast orbiting is, working differently per Orbit Method: under Turntable it's the rotation per pixel; under Trackball it's a simple speed factor.
Orbit Around Selection — makes the selection center the viewport's rotation center (the last selection is used when nothing is selected). How the center is found depends on mode: Object mode uses the selection's bounding-box center, Edit and Pose mode use the selected elements' center, and Paint modes use the last brush stroke's center. Note: handy as it sounds, it can be awkward for large objects like a terrain mesh, whose center isn't necessarily what you care about.
Auto – Perspective — on, the view goes Perspective when you orbit and Orthographic when you align to an axis (Top, Side, Front, Back, etc.); off, you switch by hand.
Auto – Depth — uses the depth under the mouse to improve pan, rotate, and zoom; good with Zoom To Mouse Position.
Smooth View — how long (in milliseconds) the transition animation runs when you switch views (Top/Side/Front/Camera…); set it to zero to drop the animation.
Rotation Angle — the rotation step in degrees when Numpad4, Numpad6, Numpad8, or Numpad2 rotate the 3D Viewport.

Zoom:
Zoom Method — your preferred interactive-zoom style.
  Scale — scale zooming keys off where you first click: move toward the area center to zoom out, away from it to zoom in.
  Continue — lets you control the speed (not the amount) of zoom by moving away from the initial cursor spot; up from the click point or to the right zooms out, down or left zooms in, and the further you move the faster it goes. The Vertical and Horizontal radio buttons and the Invert Zoom Direction option can change the directions.
  Dolly — works like Continue except the zoom speed stays constant.
Zoom Axis — the mouse axis used for zooming. Vertical (up zooms out, down zooms in) or Horizontal (left zooms in, right zooms out).
Zoom to Mouse Position — on, the pointer's position becomes the zoom focus instead of the 2D window center, which avoids panning when you zoom in and out a lot. Tip: pair it with Auto Depth to zoom straight to the point under the cursor.
Invert Zoom Direction – Mouse — flips which way Dolly and Continue zooming go.
Invert Zoom Direction – Wheel — inverts the mouse-wheel zoom direction.

Fly & Walk:
View Navigation — which mode interactive first-person navigation starts in by default (see Fly/Walk Navigation).
Walk:
  Reverse Mouse — inverts the mouse's Y movement.
  Mouse Sensitivity — the speed factor for looking around; higher means faster.
  Teleport Duration — the time-warp interval when teleporting in navigation mode.
  Walk Speed — the base speed for walking and flying.
  Speed Factor — the multiplier for the speed boost.
Gravity — simulates gravity while walking.
  View Height — the distance from the ground to the camera when walking.
  Jump Height — the highest a jump reaches.

## Perspective/Orthographic

Reference — Mode: All modes. Menu: View ‣ Perspective/Orthographic. Shortcut: Numpad5.

This operator switches the viewport camera's projection. Every 3D Viewport supports two projection types, illustrated in the figure.

Our eyes are accustomed to perspective, where farther objects look smaller. Orthographic projection can feel strange at first, since an object's size stays constant no matter how far away it is — as if you were viewing the scene from an infinitely remote point. Even so, it's genuinely useful: it gives a more "technical" read on the scene, making modeling and judging proportions easier.

Options: switch between the two projections with View ‣ Perspective/Orthographic or Numpad5. Changing a 3D Viewport's projection doesn't change how the scene renders — rendering defaults to perspective. For an orthographic render, select the camera, open the Camera tab in the Properties editor, and set Type to Orthographic in the Lens panel. See also the Auto-Perspective Preference, Camera Lens Type, and Camera Projections.

## Fly/Walk Navigation

The standard navigation controls can feel limiting, particularly in large environments like architectural models. There, first-person controls are often preferable: you look around while "standing" in place rather than orbiting a central point.

Blender provides two such methods, Flying and Walking. Launch either from the View ‣ Navigation menu, or start your preferred one (chosen in the Preferences) with Shift-AccentGrave.

Common uses for Fly/Walk:
Navigating — a fast way to cross a large scene.
Positioning a camera — started from a camera view (Numpad0), the camera travels with you.
Recording camera movement — capture your path by entering a camera view, turning on Auto Keying, starting playback, then activating Fly/Walk navigation; the route is stored as camera keyframes you can render. Playback can't be controlled while Fly/Walk is active, so when you finish recording you must first leave navigation with LMB before you can halt playback.

Walk Navigation — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Walk Navigation. This behaves like a typical first-person game, combining keyboard keys with mouse movement.
Usage: move the mouse toward what you want to look at and use the keys below to walk through the scene. When the view suits you, press LMB to confirm; to return to where you began, press Esc or RMB. Every one of these keys also shows up in the Status Bar as you move around, and you can tune options like mouse sensitivity and default speed in the Preferences.
W / Up — move forward.
S / Down — move backward.
A / Left — strafe left.
D / Right — strafe right.
E — move up (global); available only with Gravity off.
Q — move down (global); available only with Gravity off.
R — move up (local); available only with Gravity off.
F — move down (local); available only with Gravity off.
Spacebar — teleport to the spot under the crosshair (offset by the Camera Height value in the Preferences).
WheelUp / NumpadPlus — raise the movement speed.
WheelDown / NumpadMinus — lower the movement speed.
Shift — speed up temporarily.
Alt — slow down temporarily.
V — jump; available only with Gravity on.
Tab — toggle Gravity.
Z — straighten the view's Z axis (smoothly roll it upright rather than tilted).
Period — raise the jump height.
Comma — lower the jump height.

Fly Navigation — Reference: Mode: All modes; Menu: View ‣ Navigation ‣ Fly Navigation. On activation the cursor sits centered inside a rectangle marking a safe zone; move the cursor outside that zone and the view rotates/pans.
Usage: move the mouse beyond the safe zone toward what you want to look at. Click LMB or press Spacebar to keep the current view and leave Fly navigation; press Esc or RMB to return to where you started.
W / Up — accelerate forward.
S / Down — accelerate backward.
A / Left — accelerate left.
D / Right — accelerate right.
E — accelerate upward.
Q — accelerate downward.
MMB — drag to pan the view; flight pauses while you do.
WheelUp / NumpadPlus — increase acceleration along the current heading; with no motion, begin accelerating forward.
WheelDown / NumpadMinus — decrease acceleration along the current heading; with no motion, begin accelerating backward.
Alt — slow down while held, until the view eventually stops.
Ctrl — disable rotation while held, so view rotation doesn't steer the flight; this lets you fly past an object yet keep it centered as you move away.
X — toggle X-axis correction; when on, the view smoothly pitches toward the horizon while the cursor sits in the safe zone.
Z — toggle Z-axis correction; when on, the view smoothly rolls back to upright.

## Sidebar

Item — displays the Transform settings of the active object.

Tool — displays settings for the active tool and Workspace.

View:
View Panel — adjusts other 3D Viewport settings.
  Focal Length — sets the focal length of the 3D Viewport camera.
  Clip Start/End — sets the nearest and farthest distances at which geometry stays visible; anything closer than Start or farther than End is hidden. Note: in Orthographic view the viewport uses a negative End rather than Start. Warning: a wide clipping range lets you see both near and far objects but cuts depth precision, producing artifacts; a very large range can even make depth-buffer-dependent operations unreliable, though that varies by graphics card and drivers (see Troubleshooting Depth Buffer Glitches).
  Local Camera — lets this 3D Viewport keep its own active camera, separate from the scene-wide one; the selector beside the checkbox picks it.
  Passepartout — shows the camera passepartout while in camera view.
  Render Region — uses the Render Region; marking a region with Ctrl-B turns this on automatically. Note that while you're looking through the active camera this option does nothing — there you must instead use Output Properties ‣ Format ‣ Render Region in the Properties editor, which affects both the viewport and the final render.
  View Lock:
    Lock to Object — pick an object to become the viewpoint's point of interest, so the view orbits and zooms toward it; unavailable while looking through the active camera.
    Lock – To 3D Cursor — designates the 3D Cursor as the viewpoint's focus; available only when Lock to Object is off.
    Lock – Camera to View — while looking through a camera, glues the camera to the view so it follows along as you navigate, its frame outlined with a red dashed line.
    Lock – Rotation — blocks changes to the 3D Viewport's orientation and perspective.
    Hint: if the camera is parented to an object, you can enable Camera Parent Lock in the camera's properties so navigating the viewport moves the camera's topmost parent instead of the camera directly.
3D Cursor:
  Location — the 3D Cursor's location.
  Rotation — the 3D Cursor's rotation.
  Rotation Mode — how rotations are computed (more in the manual's appendix). Euler aligns the coordinate axes to the Euler axis, exposing the underlying discrete XYZ axes and any potential Gimbal Lock. Axis Angle uses the X, Y, Z coordinates to set a point relative to the object origin; that point and the origin define an axis, around which the W value sets the rotation. Quaternion treats X, Y, Z, and W as the Quaternion components.
Collections:
  The Collections panel lists collections and lets you control their visibility; a collection holding objects shows a circle to the left of its name.
  Local Collections — lets each viewport hold its own collection-visibility state instead of one shared globally.
  Hide in Viewport (eye icon) — toggles whether the collection is shown.
  Clicking a collection's name "isolates" it, surfacing that collection along with its ancestors and descendants while concealing the others.
Annotations — see Annotations for more.

Animation:
Global Transform.

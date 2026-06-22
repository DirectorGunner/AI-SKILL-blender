# Introduction (part 1)

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

Rigify automates building character rigs from a building-block approach, assembling complete rigs from smaller parts (arms, legs, spines, fingers, and so on); the part library is modest but grows, widening the range of characters and creatures it can rig. A core principle is that a finished rig no longer needs Rigify — you can hand a Rigify-made rig to people who don't have the add-on and it still works fully. Note that Rigify only generates the rig's controls and bones; it doesn't bind the rig to a mesh, so skinning is still your job. Main features: modular rigging (mix blocks to rig anything — even a character with five arms and one leg, complete with FK, IK, snapping tools, and UI, in seconds); nondisruptive re-rig (regenerate after adding, say, a sixth arm or a tail without losing previously generated features or animation data); a flexible animation feature set (the sample limbs, spines, tails, fingers, and faces add stretchy FK/IK plus a secondary direct-deformation layer via interactive Bendy Bones); shareable animation across Rigify rigs (since Rigify generates the control system, sharing a meta-rig across characters lets you share data even at different proportions); an extendable feature set (save/encode meta-rigs to a button for reuse or sharing, and extend Rigify with new types or samples via Python feature-set packages); and "ready to go" — once generated, the rig needs neither Rigify nor any other add-on. Enable it by searching "Rigify" in Preferences ▸ Add-ons and ticking it.

As with any object, you edit an armature in Edit Mode (Tab), and the bone-editing tools resemble the mesh ones. The key thing to grasp is that you're editing the armature's rest position — its default state, where every bone has no rotation and is scaled to 1.0 in its own local space — and any poses you make later build on it, so editing it in Edit Mode also alters existing poses; be sure the armature is final before skinning and posing. Note too that some tools act on bones' joints and others on the bones themselves, so don't confuse them. Add menu (Edit Mode; Add; Shift-A): in the 3D Viewport, Shift-A adds a new bone that's one unit long, oriented toward global Z, with its root at the 3D cursor and no relationship to any other bone. Locking bones: you can stop a bone from being transformed in Edit Mode in several ways — tick the Lock checkbox in its Transform panel (Bones tab), press Shift-W ‣ Toggle Bone Options ‣ Locked, or use Armature ‣ Bone Settings ‣ Toggle a Setting. If a locked bone's root is connected to an unlocked bone's tip, that root isn't locked (you can still move it), so in a connected chain locking a bone really only locks its tip; with unconnected bones the lock applies to both joints.

Much like a real skeleton, bones are the building blocks of armatures, each with a resting position, orientation, and length that can all change while posing or animating; you can adjust how bones look in the armature's Viewport Display settings. Bones fall into two types by their Deform setting. Deforming bones (Deform on) drag vertices with them — for instance, an upper-arm and a lower-arm bone let you rotate and flex the arm by transforming them. Control bones (Deform off) drag no vertices and instead usually control other bones; a common case is inverse kinematics — rather than rotating the two arm bones by hand, you add a control bone and set the arm bones to orient toward it, so you just place the control where the hand should be.

A Blender armature is much like a real skeleton: it can hold many bones, and moving them deforms whatever is attached to or associated with them. An "armature" is the object type used for rigging — a rig being the controls and strings that move a marionette — and it borrows heavily from real-world skeletons. Your first armature: open a default scene, delete all objects, center the cursor at the world origin with Shift-C, press Numpad1 for Front view, add a Single Bone (Add ‣ Armature), and press NumpadPeriod to zoom to it (armature editing is covered in the editing section). The armature object behaves like any other object: it has an origin, position, rotation, and scale; an Object Data data-block editable in Edit Mode; can be linked to other scenes and shared across objects; and any Object-Mode animation applies to the whole object, not its bones (use Pose Mode for those). Since armatures are made to be posed, statically or animated, they have a specific "rest position" — their default shape, the default position/rotation/scale of their bones as set in Edit Mode. Edit Mode always shows the armature in rest position, whereas Object and Pose Mode usually show the current pose (unless you enable the Armature panel's Rest Position button).

Because bones behave like objects in Pose Mode, they can be constrained, which is why the Constraints tab appears in Object and Edit Mode; the panel holds the active bone's constraints (its name shown at the top in the "To Bone:…" field). Constraining bones can limit their pose-transform freedom (for example with the Limit constraints), make a bone track another object or bone (in the same armature or another), and so on — and inverse kinematics is mainly available through the IK Solver constraint, which is bone-specific. For instance, a human elbow can't rotate backward (barring injury) or sideways, and its forward and roll rotations are bounded (perhaps 0 to 160, or -45 to 135, depending on the rest pose), so you'd apply a Limit Rotation constraint to the forearm bone (since elbow motion comes from rotating the forearm around its root). Using bones in constraints, as owners or targets, is detailed in the constraints pages.

Once an armature is skinned, you configure it into positions called poses by transforming the bones, which deforms or transforms the skinned objects. You can't do this in Edit Mode (which edits the default "rest" position) or Object Mode (which transforms whole objects), so armatures have a third mode for posing: Pose Mode. In rest position (from Edit Mode) each bone's position/rotation are neutral (0.0) and scale is 1.0, so editing a bone in Pose Mode creates an offset from its rest position — similar to relative shape keys or Delta Transformations. Even for purely static uses, posing is closely tied to animation, so if you're new to Blender animation it's worth reading the animation chapter first. Visualization — Bone state colors: a bone's color reflects its state, with six codes in precedence order (the bone takes the color of the lowest valid state): Gray (default), Blue wireframe (in Pose Mode), Green (with a constraint), Yellow (with an IK Solver constraint), and Orange (with a Targetless Solver constraint); when bone colors are enabled, they override the state colors.

The Properties' Armature tab gathers the armature settings into panels. Pose (All Modes; Armature ‣ Pose): Pose Position is a radio toggle between Pose Position and Rest Position — Edit Mode always shows rest position, while Object and Pose Mode show Pose Position (as transformed in Pose Mode) by default, so choose Rest Position to see rest in all modes. Bone Collections: see Bone Collections. Motion Paths (All Modes; Armature ‣ Motion Paths) enables visualizing the motion path the skeleton leaves when animated. Inverse Kinematics (All Modes; Armature ‣ Inverse Kinematics) sets the IK solver type used in the animation. Custom Properties (All Modes; Armature ‣ Custom Properties): see the Custom Properties page.

Having designed an armature and built bone chains, a good rig isn't the end goal — unless you're making a "Danse Macabre," you'll want to put flesh on the skeleton, and "linking" an armature to the object(s) it should transform or deform is, fittingly, called skinning. Blender has two main skinning types: Parent/Constrain Objects to Bones — transforming the bones in Pose Mode then transforms their "children" objects exactly like a normal parent/child relationship, and the children are never deformed; or Use the Armature Modifier on an entire mesh, tying parts of the object to bones inside the armature — the more complex and powerful method, and the only one that truly deforms the geometry by changing its vertices' relative positions. Retargeting — applying real-world motion-capture data to a rig — is available through add-ons and importers.

Constraints automatically control an object's or bone's location, rotation, and scale — for example attaching a sword to a knight's hand, or aiming a tennis player's eyes at the ball (see also Bone Constraints). Each object or bone can hold a stack of constraints evaluated top to bottom, and each constraint has an Influence factor to weaken it or mix it with others, which can be keyframed to switch constraints on and off across an animation. Adding and removing: add one via "Add Object/Bone Constraint" in the Properties Editor and pick a type; remove one with its button; reorder one by dragging its handle. The 3D-Viewport Constraints menu adds options like copying constraints and deleting them all at once, and the Track menu quickly adds a "track" (point-at) constraint. Visual transform: constraints give the owner a new location, rotation, and/or scale together called the visual transform, separate from the "base" transform in the Properties Editor's Transform panel, and it determines where the owner actually appears. So even when the Transform panel still shows the original Location (0, 0, 0), a constraint may have placed the object elsewhere, and trying to move or animate it won't visibly work (the Location numbers change but it stays put) — the only way to free it is to disable or delete the constraint, or set Influence to zero (unconstrained transform properties can still be changed normally). The visual transform isn't shown in the UI, but you can transfer it to the base transform by running Apply Visual Transform, or by applying the constraint (which also deletes it).

Shape keys deform objects into new shapes for animation — elsewhere called morph targets or blend shapes. They're most used in character facial animation (mouth positions, expressions, phonemes) and in refining a skeletal rig, and are especially useful for organic, soft body parts and muscles where you need more control over the result than rotation or scale give. They apply to vertex-based object types — meshes, curves, surfaces, and lattices. Relative or Absolute: every object with shape keys keeps a stack that's either Relative or Absolute type — use Relative for scenarios where shapes blend together (facial expressions, corrective poses) and Absolute for shape changes that progress in sequence over time (morphing smoothly between states). Relative: mainly for muscles, limb joints, and facial animation, where each shape is defined relative to the Basis or another chosen key, and the result shown in the viewport (the Mix) is the cumulative effect of each key's value — starting from the Basis, Blender layers on each shape's weighted offset relative to its reference key. Value blends between a shape key and its reference key (0.0 = 100% reference, 1.0 = 100% shape key), and Blender can extrapolate blends above 1.0 and below 0.0, amplifying or inverting the deformation. Basis is the first (top-most) key — the object's vertices in their original positions, with no weight value, unkeyable, and the default Reference Key for new shape keys. Absolute: mainly to deform an object into different shapes over time, where instead of blending, each key corresponds to a specific Evaluation Time, and the Mix is interpolated between the previous and next keys per the current Evaluation Time. Value is the Evaluation Time (in frames) at which the key is active. Basis is again the first key — the object's original vertex positions, defining the starting shape for the absolute sequence.

The 3D Viewport is where you interact with the 3D scene for all sorts of work — modeling, animating, texture painting, and the like.

Header Region: the header carries menus and controls that vary by current mode, and its contents fall into three groups.

Mode & Menus:
Mode (Ctrl-Tab) — the 3D Viewport provides multiple modes, each for editing a different kind of data; the default Object Mode lets you place a character in the scene, while Pose Mode lets you pose it. Ctrl-Tab raises a pie menu for quick mode switching, though with an Armature selected it instead toggles between Object Mode and Pose Mode. Tab flips between Object Mode and Edit Mode for objects that support it.
View — a menu of tools for moving around in 3D space.
The remaining menus depend on the mode; the Object Mode ones follow.
Select — tools for selecting objects.
Add (Shift-A) — a list of object types you can add to the scene.
Object — tools that act on objects, such as duplication; a subset is also reachable by right-clicking in the 3D Viewport.

Transform Controls:
Transform Orientation (Comma) — changes the Transform Orientation, which sets the rotation of the transform gizmo.
Pivot Point (Period) — changes the Pivot Point, which sets where the transform gizmo sits.
Snapping (Shift-Tab) — options for snapping items to nearby ones; hold Ctrl to toggle snapping on/off for as long as the key is down.
Proportional Editing (O) — smoothly transforms unselected items near the selected ones (see Proportional Editing).

Display & Shading:
Object Type Visibility — controls which object types can be seen and selected in this viewport (see Object Type Visibility).
Viewport Gizmos — sets how gizmos are drawn in the 3D Viewport.
Viewport Overlays — sets how overlays are drawn in the 3D Viewport.
Toggle X-Ray (Alt-Z) — makes the whole scene transparent so you can see and select otherwise-hidden items; it's a shortcut to the X-Ray option inside the Viewport Shading popover. In Pose Mode the same button drives a separate setting with its own on/off state: rather than going transparent, it draws the armature in front of any geometry.
Viewport Shading — sets the 3D Viewport's shading.

Toolbar Region: the Toolbar holds tools that depend on the mode (modeling tools in Edit Mode, brush tools in Sculpt Mode, and so on). See Tools for more.

Sidebar Region: the Sidebar holds properties of the active object and tool, plus the viewport's own. See Sidebar for more.

Asset Shelf Region: depending on the mode, the asset shelf may be available for quick access to mode-specific assets (Pose Mode surfaces pose assets, Sculpt Mode surfaces brush assets). See Asset Shelf for more.

The Graph Editor is where you edit animation curves, which dictate how properties change over time.

Main Region — the curve view lets you see and edit F-Curves. An F-Curve has a few key parts:
Curve — describes how a property's value (Y axis) evolves over time (X axis).
Keyframes — user-set values on certain frames, drawn as little black discs that turn orange when selected; the in-between frames are filled in automatically by interpolating between keyframes.
Handles — each keyframe has two handles, points you drag to shape the curve around it.
See also F-Curves for more.

Navigation — as in most editors:
Pan — drag with MMB.
Zoom — roll the mouse Wheel.
Scale View — drag with Ctrl-MMB to scale horizontally or vertically.
The scrollbars work too.
Tip: focus the view on an animated property's curve by right-clicking it and choosing View in Graph Editor. To bind a hotkey for this, open the Keymap preferences, expand the User Interface category, click Add New, enter the operator name anim.view_curve_in_graph_editor, and pick a shortcut. (The usual route — right-clicking the menu item and choosing Assign Shortcut — would file the shortcut under the wrong category and fail here.)

Playhead & 2D Cursor — the current frame is a vertical blue line, the Playhead, which (as in other Animation Editors) you move by clicking or dragging LMB in the scrubbing strip up top. Together with a horizontal blue line it forms the 2D Cursor, usable as a pivot for rotating and scaling; hide the horizontal line via View ‣ Show Cursor or Sidebar ‣ View ‣ Show Cursor. Move the 2D Cursor by clicking or dragging Shift-RMB, or by editing its coordinates in the Sidebar's View tab.

Header — View Menu:
Sidebar (N) — shows or hides the Sidebar Region.
Adjust Last Operation — opens a pop-up to alter the last operation's properties (see Adjust Last Operation).
Channels — shows or hides the Channels Region.
Playback Controls — shows or hides the Playback Controls.
Frame Selected (NumpadPeriod) — pans and zooms onto the selected keyframes.
Frame All (Home) — pans and zooms to show every keyframe.
Frame Scene/Preview Range — resets the horizontal view to the scene frame range, honoring the preview range if active.
Go to Current Frame (Numpad0) — centers the area on the Playhead.
Realtime Updates — whether other views (the 3D Viewport, say) refresh while you drag keyframes; if off, they update only when you finish.
Show Sliders — adds a value slider beside each channel; nudging one inserts a keyframe automatically.
Auto-Merge Keyframes — auto-merges keyframes landing on the same frame after a transform.
Auto-Lock Key Axis — auto-locks keyframe movement to whichever axis best matches the mouse direction.
Show Markers — shows the marker region; with it off, the Marker Menu hides and marker operators are unavailable here.
Show Cursor — toggles the horizontal blue line (see Playhead & 2D Cursor).
Use Timecode (Ctrl-T) — shows timing in seconds rather than frames; e.g. 01:03+02 reads "1 minute, 3 seconds, 2 frames."
Sync Visible Range — keeps the editor's horizontal pan and scale in step with other time-based editors that enable this, so they show the same slice of time.
Show Extrapolation — toggles the extrapolated portion of curves.
Show Handles (Ctrl-H) — toggles display of keyframe handles.
Only Selected Keyframes Handles — shows handles only for the selected keyframes.
Set Preview Range (P) — drag a box to set a preview time range; while active, playback stays inside it for replaying a segment without rewinding. Change its start/end with the matching button in the Timeline editor's Playback popover, or just run Set Preview Range again.
Clear Preview Range (Alt-P) — clears the preview range.
Set Preview Range to Selected (Ctrl-Alt-P) — sets a preview range covering the selected keyframes.
Toggle Dope Sheet — flips the area over to the Dope Sheet Editor.
Area — area controls; see the user-interface documentation.

Select Menu:
All (A) — selects all keyframes and handles.
None (Alt-A) — clears the selection.
Invert (Ctrl-I) — flips the selection.
Box Select (B) — drag a box to select the keyframes and handles inside it.
Box Select (Axis Range) (Alt-B) — drag a box to select keyframes and handles in the matching time range, even above or below the box.
Box Select (Include Handles) — selects keyframes and their handles inside the box.
Circle Select (C) — shows a circle at the cursor that you drag over keyframes and handles to select them.
Lasso Select (Ctrl-RMB) — draw a freehand shape to select the keyframes and handles inside it.
Columns on Selected Keys (K) — selects keys on the same frame as an already-selected key.
Column on Current Frame (Ctrl-K) — selects every key on the current frame.

Columns on Selected Markers (Shift-K) — selects keys sharing a frame with a selected marker.
Between Selected Markers (Alt-K) — selects keys between the leftmost and rightmost selected markers.
Before Current Frame ([) — selects keys at or before the current frame; you can also Shift-Ctrl-LMB anywhere left of the Playhead.
After Current Frame (]) — selects keys at or after the current frame; you can also Shift-Ctrl-LMB anywhere right of the Playhead.
Select Handles — selects the handles of the currently selected keyframes.
Select Keys — selects the keyframes of the currently selected handles.
Select More (Ctrl-NumpadPlus) — grows the selection to take in the time-neighbors of the selected keys.
Select Less (Ctrl-NumpadMinus) — drops keys with fewer than two selected neighbors.
Select Linked — selects keys on the same curve as an already-selected key.

Marker Menu — markers flag frames carrying key points or notable events in an animation and, as in most animation editors, appear along the bottom. For the various marker tools, see Editing Markers.

Channel Menu — see Editing Channels.

Key Menu — see Editing F-Curves.

Normalize — scales each curve's display so they all seem to span the same -1-to-1 range, which eases editing when curves have wildly different value ranges. Turning it on zooms the view to match and darkens the area outside the normalized range. With a preview range defined, keys inside it are normalized while the rest scale proportionally.
Auto Normalization — recomputes curve normalization on every curve edit.

View Controls:
Show Only Selected — shows only curves of selected objects/bones/….
Show Hidden — shows keyframes from hidden objects/bones/….
Show Only Errors — shows only channels with errors (e.g., ones animating a property the object lacks).
Create Ghost Curves (framed F-Curve icon) — snapshots the current curves and shows them in the background as a reference; click again to clear it.
Filter (funnel icon):
  Search — filters the channel list by a search term.
  Filtering Collection — pick a collection to show only its objects' keyframes.
  Filter by Type — filters curves by property type.
  Sort Data-Blocks — sorts data-blocks alphabetically for easier finding; if it slows playback (really only with many objects), switch it off.

Transform Controls:
Pivot Point — the pivot for rotating and scaling.
  Bounding Box Center — the center of the smallest box around the selected keyframes.
  2D Cursor — where the Playhead meets the horizontal Cursor line.
  Individual Centers — rotate/scale each handle about its own keyframe.
Snap — the icon toggles snapping; the dropdown adds:
  Snap To — the element to snap to: Frame (whole frames), Second (seconds), Nearest Marker (the closest Marker).
  Absolute Time Snap — off, keyframes move in increments of Snap To; e.g. with Second and a key on 0:06+5, dragging right snaps to 0:07+5, gaining a second while keeping its 5-frame subsecond offset. On, keyframes snap to multiples of Snap To, so the same key lands on 0:07+0, losing the offset.
Proportional Editing (O) — see Proportional Editing.

Playback Controls — this region holds controls and options for playback, keying, auto keyframing, and transport. They let you control how animations preview and sync with audio, add and manage keyframes via keying sets and auto keying, navigate the timeline with playback and transport controls, and set frame ranges and preview chosen segments. See also the Playback Controls documentation for the full footer rundown.

Sidebar Region — View Tab:
Show Cursor — toggles the 2D Cursor's horizontal line.
Cursor X, Y — shows and lets you edit the 2D Cursor's X (current frame) and Y (value) coordinates.
Cursor to Selection — sets the 2D Cursor to the mean time-and-value of the picked keyframes.
Cursor Value to Selection — drops the 2D Cursor at the selected keyframes' average value, leaving its time alone.
F-Curve Tab — see F-Curve Properties.
Modifiers Tab — see F-Curve Modifiers.

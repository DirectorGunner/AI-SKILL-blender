# Fill Between Joints, Naming, Parenting, Properties ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Fill Between Joints; Naming; Parenting; Properties; Separate Bones; Split; Subdivide; Switch Direction; Symmetrize; Transform; Custom Properties; Bone Properties; Inverse Kinematics.

## Fill Between Joints

Fill Between Joints (Edit Mode; Armature ‣ Fill Between Joints; F) mainly makes one bone between two selected joints, like "create edges/faces" in mesh editing. With one root and one tip selected, the new bone's root goes on the selected tip, its tip on the selected root, and it's parented and connected to the bone owning the selected tip. With two tips selected, the root goes on whichever tip is nearer the 3D cursor, the tip on the other, and it's parented and connected to the bone owning the root-side tip. With two roots selected you hit a quirk of Blender's event system not updating the UI in real time: pressing F gives a bone with its root on whichever root is nearer the 3D cursor, its tip on the other, and parented/connected to the owner of the root-side root — and trying to move the new bone triggers a UI update that shows its root snapping to the parent bone's tip. Pressing F with one joint selected makes a bone from that joint to the 3D cursor, parented to no bone. You'll get an error if you try to fill two joints of the same bone, or more than two joints.

## Naming

Naming (All Modes; Properties ‣ Bone Properties): rename bones via the Name field in Bone Properties or by double-clicking them in the Outliner. Blender also offers tools that exploit left/right-symmetric naming and others that auto-name an armature's bones. Naming conventions help you find the right bone and tell Blender which two bones are counterparts, so for a bilaterally symmetrical armature it pays to follow a left/right convention (it enables time-savers like X-Axis Mirror editing). Give bones meaningful base names ("leg", "arm", "finger", "back", "foot"), and for a bone with a mirror counterpart use one of the recognized left/right separators — placed second ("L_calf_bone") or last-but-one ("calf_bone.R"); Blender handles the counterpart when it sees an upper- or lower-case "L", "R", "left", or "right". Valid separators include nothing (handLeft → handRight), "_" (hand_L → hand_R), "." (hand.l → hand.r), "-" (hand-l → hand-r), and " " (hand LEFT → hand RIGHT); all also work with the left/right part first, but the short "L"/"R" code only works with a separator (so "handL"/"handR" won't). Before mirroring or flipping, Blender first strips a number extension like ".001", so copying "blah.L" and flipping with Flip Names names the copy "blah.L.001" and flipping its name yields "blah.R". Auto-Name (Edit Mode; Armature ‣ Names ‣ Auto-Name Left/Right, Front/Back, Top/Bottom): the three AutoName entries add a suffix to selected bones based on their root's position relative to the armature's origin — AutoName Left/Right adds ".L" for a positive-X root and ".R" for a negative-X one (using the tip's X if the root sits exactly at X=0, and a bare period suffix if both joints are at X=0, since left/right can't be decided); AutoName Front/Back adds ".Bk" for positive-Y and ".Fr" for negative-Y; and AutoName Top/Bottom adds ".Top" for positive-Z and ".Bot" for negative-Z, all handling the 0.0 case as Left/Right does. Flip Names (Edit Mode; Armature ‣ Names ‣ Flip Names) swaps the left/right markers in selected bone names — handy after building, duplicating, and mirroring half a symmetrical rig — swapping the text per the conventions and dropping number extensions where possible.

## Parenting

Parenting (Edit Mode; Armature ‣ Parent; Properties ‣ Bones ‣ Relations; Ctrl-P, Alt-P): you can build and change bone chains from the 3D Viewport or the Properties — for each bone it's a matter of whether it's parented to another and, if so, whether it's connected. To parent/connect in the 3D Viewport, select the bone then its future parent and press Ctrl-P (or Armature ‣ Parent ‣ Make Parent…), then in the pop-up choose Connected to connect the child to the parent or Keep Offset otherwise; selecting more than two bones parents them all to the last selected, selecting one already-parented bone (or bones all already parented to the last) leaves connecting as the only choice, and selecting one non-parented bone gives the "Need selected bone(s)" error (with this method the new children aren't scaled or rotated, just moved if you connect them to the parent's tip). In the Properties Bones tab, pick each selected bone's parent in the Parent Data ID at the top-right of its Relations panel and tick the checkbox beside it to connect (here the child's tip is never moved, so connecting fully transforms the child). To disconnect or free bones: in the 3D Viewport select them and press Alt-P (or Armature ‣ Parent ‣ Clear Parent…), choosing Clear Parent to free them or Disconnect Bone to only break connections; or in the Properties Bones tab set no parent in the Parent Data ID to free a bone, or untick Connected to just disconnect it — relationships with non-selected children are never changed. Bone Collections (Edit Mode, Pose Mode; Armature ‣ Bone Collections, Pose ‣ Bone Collections) manage which collections the bone belongs to: Move to Collection (M) moves bones to a collection; Assign to Collection (Shift-M) assigns the selection to a collection or unassigns it depending on whether the active bone is already in it; Show All (Ctrl-AccentGrave) unhides hidden collections; and Assign to new Collection puts the selected bones in a new "New Collection" that you can rename in the Armature properties' Bone Collections panel.

## Properties

Properties (Edit Mode; Armature ‣ Bone Settings ‣ …; Shift-W, Shift-Ctrl-W, Alt-W): most bone properties (apart from transforms) are grouped in each bone's panels in the Bones tab in Edit Mode, and some are also reachable in the 3D Viewport via three pop-up menus — Toggle Setting (Shift-W or Armature ‣ Bone Settings ‣ Toggle a Setting), Enable Setting (Shift-Ctrl-W or ‣ Enable a Setting), and Disable Setting (Alt-W or ‣ Disable a Setting). Display Wire always draws the bone as wireframe. Deform (also Shift-W ‣ Deform) and Multiply Vertex Group by Envelope control how the bone influences geometry, together with the bone joints' radius (detailed under skinning). Inherit Rotation makes the bone rotate with its parent in Pose Mode (see the relations page). Lock (also Shift-W ‣ Locked) blocks all editing of the bone in Edit Mode (see bone locking).

## Separate Bones

Separate Bones (Edit Mode; Armature ‣ Separate Bones; P) splits the selected bones into a new armature object (Armature ‣ Separate, Ctrl-Alt-P), much as with meshes; and in Object Mode you can join all selected armatures into one with Object ‣ Join Objects (Ctrl-J).

## Split

Split (Edit Mode; Armature ‣ Split; Y) disconnects the selected bones from the rest of the armature, forming a new, unconnected bone chain — useful for restructuring rigs, separating limbs, or preparing chains to transform on their own. It only changes connectivity; the bones stay in the same armature object, so to move the split chain to a separate object use Separate Bones.

## Subdivide

Subdivide (Edit Mode; Armature ‣ Subdivide) turns one bone into two or more, subdividing all selected bones while keeping their relationships, so the resulting bones always form a connected chain. To make an arbitrary number per bone, use Number of Cuts in the Subdivide Multi "Adjust Last Operation" panel: as in mesh editing, n cuts give n+1 bones per selected bone.

## Switch Direction

Switch Direction (Edit Mode; Armature ‣ Switch Direction; Alt-F) swaps each selected bone's root and tip. Doing so usually breaks the chains a bone belongs to, but switching a whole (part of a) chain keeps the bones parented and connected in reversed order — so switching one bone plus a three-bone chain can leave the lone bone (Bone.005) neither connected nor parented, while the reversed chain still exists with Bone.002 as its root and Bone as its tip, and Bone.003 freed.

## Symmetrize

Symmetrize (Edit Mode; Armature ‣ Symmetrize) mirrors selected bones across the X axis using Blender's symmetrical-naming convention, going left-to-right or right-to-left depending on the selection: when matching bones are selected on both sides, mirroring runs right to left; bones whose opposite-named counterparts don't exist are created and existing ones are overwritten; and bones that can't be classified left or right are skipped. Symmetrized bone and constraint properties are adjusted to mirror their behavior, and on bones that have Action Constraints, keyframes get written into the target Action so motion stays symmetrical when it's activated (bone or constraint drivers are neither created nor affected). Bone-collection assignments are symmetrized too — collections following the convention are mirrored, and a missing one is created and parented to the same collection as the original — though Blender doesn't stop a left bone from being assigned to a right collection, in which case the resulting right bone ends up in the left collection.

## Transform

Transform: this page doesn't repeat the general bone transforms, axis locking, pivot points, or mirroring, since they match most object editing (covered in the mesh section) — just remember that bone roots and tips behave roughly like mesh vertices and bones act like mesh edges. Recall bones can be both parented and connected: parented bones behave in Edit Mode as if they had no relations (moving, rotating, or scaling them doesn't affect descendants), but connected bones must keep parent tips at child roots, so transforming one affects its connected parent/children/siblings. Here "local axes" means the bone's own axes (locking to a local axis by pressing the key twice constrains along that selected bone's own local axis rather than the armature object's), and in the Sidebar Transform panel you can edit the positions and radius of the active bone's two joints plus its roll. Scale Radius (Edit Mode; Armature ‣ Transform ‣ Scale Radius; Alt-S): select a bone's head, body, or tail and press Alt-S, then move the mouse to change its radius — selecting the body scales the mean radius, and with connected bones the parent's tip and children's roots scale together; you can also set the radius via Properties ‣ Bone ‣ Deform ‣ Radius by entering Tail and Head values. Note that resizing a bone (by scaling or moving a joint) makes Blender adjust the envelope end-radii proportionally, so it's best to place all bones first and edit properties after. Scale Envelope Distance (Edit Mode and Pose Mode; Armature ‣ Transform ‣ Scale Envelope Distance; Ctrl-Alt-S): click a bone's body and Ctrl-Alt-S, then drag to change its Bone Envelope volume (or set Properties ‣ Bone ‣ Deform ‣ Envelope ‣ Distance directly); this changes only the range within which the bone influences child geometry, not the bone's size. Align Bones (Edit Mode; Armature ‣ Transform ‣ Align Bones; Ctrl-Alt-A) rotates the selected bones to match the active one's orientation.

Transform (Edit Mode and Pose Mode; Bone ‣ Transform): in Edit Mode this panel controls a bone's position and roll, while in Pose Mode you set only location for the main bone plus its rotation and scale, and you can additionally restrict position, rotation, and scale changes per axis on each bone. Head X, Y, Z is the head end's location; Tail X, Y, Z the tail end's; Roll the rotation about the head-tail axis; Length the head-to-tail distance (changing it moves the tail); and Lock stops the bone from being transformed in Edit Mode.

### Transform 

Reference

Mode:
Object Mode

Panel:
Properties ‣ Object Properties ‣ Transform

Panel:
3D Viewport ‣ Sidebar ‣ Transform

Transform Options. 

The Transform area in the Sidebar lets you view and
hands-on/numerically manage the placement, rotation, and other details of an item, in Object Mode.
Every item saves its placement, heading, and proportions.
These might require manual adjustment, resetting, or baking.
In Edit Mode. It chiefly lets you type exact spots for a corner,
or averaged location for a corner grouping (including a line/surface). Because each object class gets distinct
entry in its Transform area in Edit Mode,
examine their respective sections in the Modeling part.

Employ this area to examine or alter the item's transform values like position,
turning, and/or sizing. These numbers change the item's anchor and then impact the look of
every corner and surface.

Location
The item's anchor position in item-relative directions.

Rotation
The item's direction, relative to the world directions and its own anchor.

Rotation Mode
System for determining rotations, more material can be in
the appendix.

Euler:
The gizmo lines stick to the Euler direction,
giving you a view of the underlying XYZ direction in the Euler spin,
plus feasible Gimbal effects.

Axis Angle:
The X, Y, and Z values denote a spot from the item origin.
This spot and the origin establish a line around which the W setting establishes the turn.

Quaternion:
X, Y, Z, and W reflect the Quaternion features.

Scale
The item's comparative proportions along the item direction
(e.g. the Scale X value mirrors the proportions along the item X direction).
Every item (block, ball, etc.), when made, has a proportions of unit in every item direction.
To make the item bigger or tinier, you enlarge or minimize it in the target direction.

Dimensions
The area of the item's perimeter box
(arranged with the item directions – consider a mailing carton just roomy enough to hold the item).

Transform Properties Locking
While toggled, the corresponding transform number
stays unchanged in interactive procedures.
But the number can alter through non-interactive procedures,
like hand-entering the number or executing Python.

As a case, if you tied the Location X setting
you are unable to employ the viewport gizmo to shift the item across the world X line.
Still you can shift it by keying the Location X number area.
Think of the tie choice as a firm constraint, modifiable just from the area.

To tie a setting, tap the padlock image next to the key.
The button is unlocked when the image exhibits an undone padlock,
and it is locked when the image shows a done padlock.

### Delta Transforms 

Reference

Mode:
Object Mode

Panel:
Properties ‣ Object Properties ‣ Transform ‣ Delta Transforms

Delta Transforms are simply alterations done on top of the transforms shown before.
Delta Transforms work well in motion sequences. For instance,
you can animate an item with the core transforms then move them with Delta Transforms.

### Parent Inverse Transform 

Reference

Mode:
Object Mode

Panel:
Properties ‣ Object Properties ‣ Transform ‣ Parent Inverse

Condition:
Accessible when the chosen item is linked by a different item.

The Parent Inverse transform specifies how the child's item space
is positioned from its parent. It ensures that when linking is made,
the child keeps its live world position, even though it currently takes
shifts from the parent.

The matrix is displayed broken into Location, Rotation, and Scale amounts.
These show the positioning needed to protect the child's placement from its parent.
The amounts are read only and shown for review.

The Rotation Mode establishes how the turn section is shown,
and can be moved among frameworks like XYZ Euler, Axis Angle, or Quaternion.
This acts the same as the Rotation Mode choice in the core transform panel.

### Clear Parent Inverse Transform 

Removes the Parent Inverse matrix from the picked shapes. With a vacant matrix,
the placement, turning, and proportions of the child are handled
immediately in the parent's item space.

This fundamentally makes the child's transforms linked to the parent's anchor,
perhaps relocating the shape in world space.

See Clear Parent for alternate methods to remove or handle parent-child connections.

## Custom Properties

Custom Properties (Pose Mode; Bone ‣ Custom Properties): see the Custom Properties page for details.

## Bone Properties

Bone Properties (Object Mode, Edit Mode, and Pose Mode; Properties ‣ Bone): when bones are selected (so in Edit and Pose Mode), their properties appear in the Properties' Bone tab, which shows different panels for each selected bone's features depending on the current mode.

## Inverse Kinematics

Inverse Kinematics (Pose Mode; Bone ‣ Inverse Kinematics): this panel controls how a bone or set of bones behaves when linked in an inverse-kinematic chain.

Inverse Kinematics (IK) streamlines animation, enabling more advanced results with less effort: you position the last bone in a chain and the rest follow automatically, like moving a finger and having the arm follow. With ordinary posing you'd start at the root and set each bone in turn to the tip — each parent passing its location and rotation to its child — so small precise changes get harder farther down the chain because you may have to adjust every parent first; IK removes that effort. IK is mostly done with bone constraints, though Pose Mode also has a simple Auto IK feature; both use the same method, but the constraints offer more options and control (see the Inverse Kinematics Constraint and Spline IK Constraint pages). Armature IK panel (Pose Mode; Properties ‣ Armature ‣ Inverse Kinematics) selects the armature's IK solver type — Standard or iTaSC — and most people use Standard. iTaSC ("instantaneous Task Specification using Constraints") computes the Jacobian differently, letting it handle constraints beyond end-effector position and orientation as a generic multi-constraint IK solver; the current implementation only adds two others — Distance in Cartesian space (keeping an end effector inside, at, or outside a sphere around a target) and Joint Rotation in joint space (directly controlling a bone's rotation relative to its parent). iTaSC accepts a mix of constraints and several per bone, computing the optimal pose from each constraint's weight — a major improvement over the standard system, where constraints solve one by one in definition order so conflicting ones overwrite each other. Precision is the maximum end-effector change between successive iterations at which the pose is stable enough to stop (lower means higher end-effector precision); Iterations caps the iteration count; Solver picks the inverse-Jacobian solver — SDLS computes damping automatically by estimating "cancellation" in the armature kinematics (works well with Copy Pose but over-damps near a singular pose, slowing movement, noticeable only in Simulation mode), and DLS computes damping manually for more reactivity and precision, with Damping Max (smaller means less damping, more velocity and precision but more oscillation risk near singular poses; 0 means none) and Damping Epsilon (the damping zone's range around a singular pose; smaller means a smaller control zone and greater risk of overshooting into oscillation). Damping and Epsilon must be tuned per armature, using the smallest values that stay stable; note the SDLS solver doesn't work with a Distance constraint (use DLS if your animation has a singular pose with a Distance constraint), and both perform well without a singular pose. Animation mode: iTaSC acts as a stateless IK solver, using the F-Curve-interpolated pose as the start before convergence, ignoring target velocity and converging to the set precision — usually faster than the old solver, with multiple targets per bone and multiple constraint types. Simulation mode is the stateful mode: it estimates target velocity, runs in "true time," ignores keyframe rotation (except via a joint-rotation constraint), and builds a state cache automatically. Reiteration — Never (start from rest, don't reiterate even on the first frame, so it takes a few frames to reach the target at the start); Initial (start from rest and reiterate to the set precision but only on the first frame — letting you choose a non-rest start pose, the default — then track by integrating the Jacobian-computed joint velocity over each frame's interval, with precision depending on the feedback coefficient, substep count, and target velocity); and Always (reiterate every frame to the set precision, dropping most iTaSC dynamics — max joint velocity and frame-to-frame continuity aren't guaranteed — for better end-effector precision, an intermediate between Animation and real-time Simulation). Auto Step lets the solver decide how many substeps each frame needs (a substep subdivides the time between frames, evaluating the IK equation and updating joint position; more substeps cost more but track targets better), estimating the optimal count by gauging pose nonlinearity and capping joint-variation amplitude per substep, configured by the next two parameters.

iTaSC continued: Min is the proposed minimum substep duration in seconds (the auto-step algorithm may shorten it further by joint velocity); Max is the maximum substep duration it won't exceed; and Steps, when Auto Step is off, sets a fixed substep count — a substep shouldn't exceed 10 ms (so 4 steps for a 25 fps animation), and if the armature vibrates between frames, raising the step count improves stability. Feedback is a coefficient on end-effector position error that sets corrective joint velocity (the error-correction time constant is its inverse); it barely affects the armature's dynamic since the algorithm evaluates target velocity regardless, and setting it to 0 "opens the loop" (the solver tracks velocity but not position, so error accumulates fast) while setting it too high over-corrects and risks instability — keep it in the 20-100 range (default 20, correcting tracking errors in about 100-200 ms), and it's why the armature keeps drifting slightly in Simulation mode after the target stops, as residual error is suppressed frame by frame. Max Velocity is an indicative maximum joint velocity in radians per second that strongly affects the dynamic — a smaller value makes the armature move slowly and lag behind fast targets, so a low value simulates inertia. Bone IK panel (Pose Mode; Properties ‣ Bone ‣ Inverse Kinematics) controls how a pose bone works within the IK chain: IK Stretch (stretch influence toward the IK target), Lock (disallow movement around the axis), Stiffness (stiffness around the axis, disabled when Lock is used), and Limit (limit movement around the axis). iTaSC Solver: with the iTaSC solver, the bone IK panel adds Control Rotation (enable a joint-rotation constraint on that bone, converting the pose rotation from an Action or UI into a joint value passed to the solver as the joint's target, so you control the joint while the solver still tracks other IK targets — useful for a preferred joint pose like the rest pose, or to animate a joint angle via an action) and Weight (the joint-rotation constraint's importance by constraint weight when not all constraints can be met at once — e.g. set a high weight here and low on the IK constraints to strongly enforce the joint rotation). Arm rig example: this arm uses two bones to beat the forearm twist problem, with IK locking stopping the forearm from bending while it can still receive a manual twist via R Y Y in Pose Mode, or through other constraints — and note that with a Pole Target, IK locking won't work on the root bone.

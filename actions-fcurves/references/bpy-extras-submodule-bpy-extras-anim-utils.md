# Bpy Extras Submodule Bpy Extras Anim Utils, Beztriple Interpolation Easing Items, Beztriple Interpolation Mode Items, Beztriple Keyframe Type Items ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: bpy_extras submodule (bpy_extras.anim_utils); Beztriple Interpolation Easing Items; Beztriple Interpolation Mode Items; Beztriple Keyframe Type Items; Event Type Items; Event Type Mask Items; Fcurve Auto Smoothing Items; Keyframe Handle Type Items; Keyframe Paste Merge Items; Keyframe Paste Offset Items; Keyframe Paste Offset Value Items; Keying Flag Api Items; Keying Flag Items; Motionpath Range Items; Nla Mode Blend Items; Nla Mode Extend Items; Operator Return Items; Property Flag Enum Items.

## bpy_extras submodule (bpy_extras.anim_utils)

### bpy_extras submodule (bpy_extras.anim_utils) 

bpy_extras.anim_utils. bake_action ( obj , * , action , frames , bake_options ) 

Parameters :

- obj (bpy.types.Object) – Object to bake.

- action (bpy.types.Action | None) – An action to bake the data into, or None for a new action
to be created.

- frames ( Iterable [ int ] ) – Frames to bake.

- bake_options ( anim_utils.BakeOptions ) – Options for baking.

Returns :

Action or None.

Return type :

bpy.types.Action | None

bpy_extras.anim_utils. bake_action_objects ( object_action_pairs , * , frames , bake_options ) 

A wrapper around bake_action_objects_iter() that accepts frames and returns the result.

Parameters :

- object_action_pairs (Sequence[tuple[bpy.types.Object, bpy.types.Action | None]]) – Sequence of object action tuples,
action is the destination for the baked data. When None a new action will be created.

- frames ( Iterable [ int ] ) – Frames to bake.

- bake_options ( anim_utils.BakeOptions ) – Options for baking.

Returns :

A sequence of Action or None types (aligned with object_action_pairs )

Return type :

Sequence[bpy.types.Action]

bpy_extras.anim_utils. bake_action_iter ( obj , * , action , bake_options ) 

A coroutine that bakes the action for one object.

Parameters :

- obj (bpy.types.Object) – Object to bake.

- action (bpy.types.Action | None) – An action to bake the data into, or None for a new action
to be created.

- bake_options ( anim_utils.BakeOptions ) – Options for baking.

Returns :

an action or None

Return type :

bpy.types.Action | None

bpy_extras.anim_utils. bake_action_objects_iter ( object_action_pairs , bake_options ) 

A coroutine that bakes actions across several objects.

Parameters :

- object_action_pairs (Sequence[tuple[bpy.types.Object, bpy.types.Action | None]]) – Sequence of object action tuples,
action is the destination for the baked data. When None a new action will be created.

- bake_options ( anim_utils.BakeOptions ) – Options for baking.

Returns :

A generator yielding None per frame, and at the end
yielding a tuple of actions (aligned with object_action_pairs ).

Return type :

Generator

class bpy_extras.anim_utils. AutoKeying 

Support for auto-keying.

classmethod active_keyingset ( context ) 

Give back the active keying set when it ought to be used.

The active keying set is only returned when the auto-key settings call for it,
and when it avoids absolute paths (since
the Copy Global Transform add-on doesn't support those).

Parameters :

context (bpy.types.Context) – The context.

Returns :

The active keying set, or None when it should not be used.

Return type :

bpy.types.KeyingSet | None

classmethod autokey_transformation ( context , target ) 

Auto-key the transformation properties.

Parameters :

- context (bpy.types.Context) – The context.

- target (bpy.types.Object | bpy.types.PoseBone) – The object or pose bone to keyframe.

classmethod autokeying_options ( context ) 

Fetch the Auto Keyframe options, returning None when they're off.

Parameters :

context (bpy.types.Context) – The context.

Returns :

The keyframing option flags, or None when auto-keying is disabled.

Return type :

set[str] | None

classmethod key_transformation ( target , options ) 

Keyframe the transformation properties while skipping locked channels.

Parameters :

- target (bpy.types.Object | bpy.types.PoseBone) – The object or pose bone to keyframe.

- options ( set [ str ] ) – Keyframing options.

classmethod key_transformation_via_keyingset ( context , target , keyingset ) 

Auto-key the transformation properties using the supplied keying set.

Parameters :

- context (bpy.types.Context) – The context.

- target (bpy.types.Object | bpy.types.PoseBone) – The object or pose bone to keyframe.

- keyingset (bpy.types.KeyingSet) – The keying set to use.

classmethod keyframe_channels ( target , options , data_path , group , locks ) 

Keyframe the channels while skipping ones that are locked.

Parameters :

- target (bpy.types.Object | bpy.types.PoseBone) – The object or pose bone to keyframe.

- options ( set [ str ] ) – Keyframing options.

- data_path ( str ) – The data path to keyframe.

- group ( str ) – The group name for the keyframes.

- locks ( Iterable [ bool ] ) – Per-channel lock status.

classmethod keying_options ( context ) 

Fetch the general keyframing options from the user preferences.

Parameters :

context (bpy.types.Context) – The context.

Returns :

The keyframing option flags.

Return type :

set[str]

classmethod keying_options_from_keyingset ( context , keyingset ) 

Fetch the general keyframing options from the user preferences.

Parameters :

- context (bpy.types.Context) – The context.

- keyingset (bpy.types.KeyingSet) – The keying set to read options from.

Returns :

The keyframing option flags.

Return type :

set[str]

classmethod keytype ( the_keytype ) 

Context manager that sets which key type gets inserted.

Parameters :

the_keytype ( str ) – The key type to use.

Returns :

A context manager that resets the key type on exit.

Return type :

Iterator[None]

classmethod options ( * , keytype = '' , use_loc = True , use_rot = True , use_scale = True , force_autokey = False ) 

Context manager that adjusts several keyframing options.

Parameters :

- keytype ( str ) – The key type to use.

- use_loc ( bool ) – Key location channels.

- use_rot ( bool ) – Key rotation channels.

- use_scale ( bool ) – Key scale channels.

- force_autokey ( bool ) – Allow use without the user activating auto-keying.

Returns :

A context manager that resets the options on exit.

Return type :

Iterator[None]

static get_4d_rotlock ( bone ) 

Fetch the lock status of the 4D rotation.

Parameters :

bone (bpy.types.PoseBone) – The pose bone to check.

Returns :

Lock status for W, X, Y, Z rotation channels.

Return type :

list[bool]

class bpy_extras.anim_utils. BakeOptions 

BakeOptions(only_selected: bool, do_pose: bool, do_object: bool, do_visual_keying: bool, do_constraint_clear: bool, do_parents_clear: bool, do_clean: bool, do_location: bool, do_rotation: bool, do_scale: bool, do_bbone: bool, do_custom_props: bool)

## Beztriple Interpolation Easing Items

### Beztriple Interpolation Easing Items 

AUTO :

Automatic Easing.

The easing type is picked for you according to the interpolation in use (for instance Ease In for transitional types and Ease Out for dynamic ones).

`EASE_IN` :

Ease In.

Applied only at the end nearest the following keyframe.

`EASE_OUT` :

Ease Out.

Applied only at the end nearest the previous keyframe.

`EASE_IN_OUT` :

Ease In and Out.

Covers the span between the two keyframes.

## Beztriple Interpolation Mode Items

### Beztriple Interpolation Mode Items 

Interpolation

Plain transitions running from one keyframe to the next.

CONSTANT :

Constant.

No interpolation; A's value is held until B arrives.

LINEAR :

Linear.

A straight line drawn from A to B (that is, no ease in/out).

BEZIER :

Bézier.

A smooth path from A to B, with adjustable curve shaping.

Easing (by strength)

Built-in inertial transitions handy for motion graphics, ordered from least to most "dramatic".

SINE :

Sinusoidal.

Sinusoidal easing (the gentlest, nearly linear yet slightly curved).

QUAD :

Quadratic.

Quadratic easing.

CUBIC :

Cubic.

Cubic easing.

QUART :

Quartic.

Quartic easing.

QUINT :

Quintic.

Quintic easing.

EXPO :

Exponential.

Exponential easing (dramatic).

CIRC :

Circular.

Circular easing (the strongest and most dynamic).

Dynamic Effects

Easing effects modeled loosely on simple physics.

BACK :

Back.

Cubic easing that overshoots and then settles.

BOUNCE :

Bounce.

A parabolic bounce that decays exponentially, as if objects were colliding.

ELASTIC :

Elastic.

A sine wave that decays exponentially, like an elastic band.

## Beztriple Keyframe Type Items

### Beztriple Keyframe Type Items 

KEYFRAME :

Keyframe.

An ordinary keyframe, used for instance on key poses.

BREAKDOWN :

Breakdown.

A breakdown pose, e.g. bridging key poses.

`MOVING_HOLD` :

Moving Hold.

A keyframe forming part of a moving hold.

EXTREME :

Extreme.

An "extreme" pose, or whatever other use is required.

JITTER :

Jitter.

A filler or baked keyframe for keying on ones, or whatever other use is required.

GENERATED :

Generated.

A key produced automatically by a tool rather than placed by hand.

## Event Type Items

### Event Type Items

NONE :

LEFTMOUSE :

Left Mouse.

LMB.

MIDDLEMOUSE :

Middle Mouse.

MMB.

RIGHTMOUSE :

Right Mouse.

RMB.

BUTTON4MOUSE :

Button4 Mouse.

MB4.

BUTTON5MOUSE :

Button5 Mouse.

MB5.

BUTTON6MOUSE :

Button6 Mouse.

MB6.

BUTTON7MOUSE :

Button7 Mouse.

MB7.

PEN :

Pen.

ERASER :

Eraser.

MOUSEMOVE :

Mouse Move.

MsMov.

`INBETWEEN_MOUSEMOVE` :

In-between Move.

MsSubMov.

TRACKPADPAN :

Mouse/Trackpad Pan.

MsPan.

TRACKPADZOOM :

Mouse/Trackpad Zoom.

MsZoom.

MOUSEROTATE :

Mouse/Trackpad Rotate.

MsRot.

MOUSESMARTZOOM :

Mouse/Trackpad Smart Zoom.

MsSmartZoom.

WHEELUPMOUSE :

Wheel Up.

WhUp.

WHEELDOWNMOUSE :

Wheel Down.

WhDown.

WHEELINMOUSE :

Wheel In.

WhIn.

WHEELOUTMOUSE :

Wheel Out.

WhOut.

WHEELLEFTMOUSE :

Wheel Left.

WhLeft.

WHEELRIGHTMOUSE :

Wheel Right.

WhRight.

A :

-

B :

-

C :

-

D :

-

E :

-

F :

-

G :

-

H :

-

I :

-

J :

-

K :

-

L :

-

M :

-

N :

-

O :

-

P :

-

Q :

-

R :

-

S :

-

T :

-

U :

-

V :

-

W :

-

X :

-

Y :

-

Z :

-

ZERO :

-

ONE :

-

TWO :

-

THREE :

-

FOUR :

-

FIVE :

-

SIX :

-

SEVEN :

-

EIGHT :

-

NINE :

-

`LEFT_CTRL` :

Left Ctrl.

CtrlL.

`LEFT_ALT` :

Left Alt.

AltL.

`LEFT_SHIFT` :

Left Shift.

ShiftL.

`RIGHT_ALT` :

Right Alt.

AltR.

`RIGHT_CTRL` :

Right Ctrl.

CtrlR.

`RIGHT_SHIFT` :

Right Shift.

ShiftR.

OSKEY :

OS Key.

Cmd.

HYPER :

Hyper.

Hyp.

APP :

Application.

App.

GRLESS :

Grless.

ESC :

Esc.

TAB :

Tab.

RET :

Return.

Enter.

SPACE :

Space Bar.

Spacebar.

`LINE_FEED` :

Line Feed.

`BACK_SPACE` :

Backspace.

BkSpace.

DEL :

Delete.

Del.

`SEMI_COLON` :

;.

PERIOD :

COMMA :

,.

QUOTE :

“.

`ACCENT_GRAVE` :

`.

MINUS :

-.

PLUS :

+.

SLASH :

/.

`BACK_SLASH` :

\.

EQUAL :

=.

`LEFT_BRACKET` :

[.

`RIGHT_BRACKET` :

].

`LEFT_ARROW` :

Left Arrow.

←.

`DOWN_ARROW` :

Down Arrow.

↓.

`RIGHT_ARROW` :

Right Arrow.

→.

`UP_ARROW` :

Up Arrow.

↑.

`NUMPAD_2` :

Numpad 2.

Pad2.

`NUMPAD_4` :

Numpad 4.

Pad4.

`NUMPAD_6` :

Numpad 6.

Pad6.

`NUMPAD_8` :

Numpad 8.

Pad8.

`NUMPAD_1` :

Numpad 1.

Pad1.

`NUMPAD_3` :

Numpad 3.

Pad3.

`NUMPAD_5` :

Numpad 5.

Pad5.

`NUMPAD_7` :

Numpad 7.

Pad7.

`NUMPAD_9` :

Numpad 9.

Pad9.

`NUMPAD_PERIOD` :

Numpad ..

Pad..

`NUMPAD_SLASH` :

Numpad /.

Pad/.

`NUMPAD_ASTERIX` :

Numpad *.

Pad*.

`NUMPAD_0` :

Numpad 0.

Pad0.

`NUMPAD_MINUS` :

Numpad -.

Pad-.

`NUMPAD_ENTER` :

Numpad Enter.

PadEnter.

`NUMPAD_PLUS` :

Numpad +.

Pad+.

F1 :

F1.

F2 :

F2.

F3 :

F3.

F4 :

F4.

F5 :

F5.

F6 :

F6.

F7 :

F7.

F8 :

F8.

F9 :

F9.

F10 :

F10.

F11 :

F11.

F12 :

F12.

F13 :

F13.

F14 :

F14.

F15 :

F15.

F16 :

F16.

F17 :

F17.

F18 :

F18.

F19 :

F19.

F20 :

F20.

F21 :

F21.

F22 :

F22.

F23 :

F23.

F24 :

F24.

PAUSE :

Pause.

INSERT :

Insert.

Ins.

HOME :

Home.

`PAGE_UP` :

Page Up.

PgUp.

`PAGE_DOWN` :

Page Down.

PgDown.

END :

End.

`MEDIA_PLAY` :

Media Play/Pause.

⏯.

`MEDIA_STOP` :

Media Stop.

⏹.

`MEDIA_FIRST` :

Media First.

⏮.

`MEDIA_LAST` :

Media Last.

⏭.

TEXTINPUT :

Text Input.

TxtIn.

`WINDOW_DEACTIVATE` :

Window Deactivate.

TIMER :

Timer.

Tmr.

TIMER0 :

Timer 0.

Tmr0.

TIMER1 :

Timer 1.

Tmr1.

TIMER2 :

Timer 2.

Tmr2.

`TIMER_JOBS` :

Timer Jobs.

TmrJob.

`TIMER_AUTOSAVE` :

Timer Autosave.

TmrSave.

`TIMER_REPORT` :

Timer Report.

TmrReport.

TIMERREGION :

Timer Region.

TmrReg.

`NDOF_MOTION` :

NDOF Motion.

NdofMov.

`NDOF_BUTTON_MENU` :

NDOF Menu.

NdofMenu.

`NDOF_BUTTON_FIT` :

NDOF Fit.

NdofFit.

`NDOF_BUTTON_TOP` :

NDOF Top.

Ndof↑.

`NDOF_BUTTON_BOTTOM` :

NDOF Bottom.

Ndof↓.

`NDOF_BUTTON_LEFT` :

NDOF Left.

Ndof←.

`NDOF_BUTTON_RIGHT` :

NDOF Right.

Ndof→.

`NDOF_BUTTON_FRONT` :

NDOF Front.

NdofFront.

`NDOF_BUTTON_BACK` :

NDOF Back.

NdofBack.

`NDOF_BUTTON_ISO1` :

NDOF Isometric 1.

NdofIso1.

`NDOF_BUTTON_ISO2` :

NDOF Isometric 2.

NdofIso2.

`NDOF_BUTTON_ROLL_CW` :

NDOF Roll CW.

NdofRCW.

`NDOF_BUTTON_ROLL_CCW` :

NDOF Roll CCW.

NdofRCCW.

`NDOF_BUTTON_SPIN_CW` :

NDOF Spin CW.

NdofSCW.

`NDOF_BUTTON_SPIN_CCW` :

NDOF Spin CCW.

NdofSCCW.

`NDOF_BUTTON_TILT_CW` :

NDOF Tilt CW.

NdofTCW.

`NDOF_BUTTON_TILT_CCW` :

NDOF Tilt CCW.

NdofTCCW.

`NDOF_BUTTON_ROTATE` :

NDOF Rotate.

NdofRot.

`NDOF_BUTTON_PANZOOM` :

NDOF Pan/Zoom.

NdofPanZoom.

`NDOF_BUTTON_DOMINANT` :

NDOF Dominant.

NdofDom.

`NDOF_BUTTON_PLUS` :

NDOF Plus.

Ndof+.

`NDOF_BUTTON_MINUS` :

NDOF Minus.

Ndof-.

`NDOF_BUTTON_V1` :

NDOF View 1.

NdofView1.

`NDOF_BUTTON_V2` :

NDOF View 2.

NdofView2.

`NDOF_BUTTON_V3` :

NDOF View 3.

NdofView3.

`NDOF_BUTTON_SAVE_V1` :

NDOF Save View 1.

NdofSaveView1.

`NDOF_BUTTON_SAVE_V2` :

NDOF Save View 2.

NdofSaveView2.

`NDOF_BUTTON_SAVE_V3` :

NDOF Save View 3.

NdofSaveView3.

`NDOF_BUTTON_1` :

NDOF Button 1.

NdofB1.

`NDOF_BUTTON_2` :

NDOF Button 2.

NdofB2.

`NDOF_BUTTON_3` :

NDOF Button 3.

NdofB3.

`NDOF_BUTTON_4` :

NDOF Button 4.

NdofB4.

`NDOF_BUTTON_5` :

NDOF Button 5.

NdofB5.

`NDOF_BUTTON_6` :

NDOF Button 6.

NdofB6.

`NDOF_BUTTON_7` :

NDOF Button 7.

NdofB7.

`NDOF_BUTTON_8` :

NDOF Button 8.

NdofB8.

`NDOF_BUTTON_9` :

NDOF Button 9.

NdofB9.

`NDOF_BUTTON_10` :

NDOF Button 10.

NdofB10.

`NDOF_BUTTON_11` :

NDOF Button 11.

NdofB11.

`NDOF_BUTTON_12` :

NDOF Button 12.

NdofB12.

`ACTIONZONE_AREA` :

ActionZone Area.

AZone Area.

`ACTIONZONE_REGION` :

ActionZone Region.

AZone Region.

`ACTIONZONE_REGION_QUAD` :

ActionZone Quad.

AZone Quad.

`ACTIONZONE_FULLSCREEN` :

ActionZone Fullscreen.

AZone FullScr.

`XR_ACTION` :

XR Action.

## Event Type Mask Items

### Event Type Mask Items

`KEYBOARD_MODIFIER` :

Keyboard Modifier.

KEYBOARD :

Keyboard.

`MOUSE_WHEEL` :

Mouse Wheel.

`MOUSE_GESTURE` :

Mouse Gesture.

`MOUSE_BUTTON` :

Mouse Button.

MOUSE :

Mouse.

NDOF :

NDOF.

ACTIONZONE :

Action Zone.

## Fcurve Auto Smoothing Items

### Fcurve Auto Smoothing Items

NONE :

None.

Automatic handles look no further than the keys right beside them.

`CONT_ACCEL` :

Continuous Acceleration.

Automatic handles are tuned to keep acceleration from jumping, giving smoother curves. The trade-off is that editing a key can shift interpolation across a wider portion of the curve.

## Keyframe Handle Type Items

### Keyframe Handle Type Items

FREE :

Free.

A handle you position by hand, with no link to its partner.

ALIGNED :

Aligned.

A hand-positioned handle whose rotation stays locked in line with its pair.

VECTOR :

Vector.

Handles computed automatically to yield straight segments.

AUTO :

Automatic.

Handles computed automatically to yield smooth curves.

`AUTO_CLAMPED` :

Auto Clamped.

Automatic handles that smooth the curve but reverse direction solely at the keyframes.

## Keyframe Paste Merge Items

### Keyframe Paste Merge Items

MIX :

Mix.

Lay the new keys on top of whatever keys already exist.

`OVER_ALL` :

Overwrite All.

Swap out every existing key.

`OVER_RANGE` :

Overwrite Range.

Replace only the keys falling inside the pasted span.

`OVER_RANGE_ALL` :

Overwrite Entire Range.

Replace the keys within the pasted span, measured across the full extent of the copied keys.

## Keyframe Paste Offset Items

### Keyframe Paste Offset Items

START :

Frame Start.

Begin the pasted keys at the current frame.

END :

Frame End.

Finish the pasted keys on the current frame.

RELATIVE :

Frame Relative.

Position the pasted keys relative to where the current frame sat at copy time.

NONE :

No Offset.

Drop the keys back at the times they originally held.

## Keyframe Paste Offset Value Items

### Keyframe Paste Offset Value Items

`LEFT_KEY` :

Left Key.

Align the paste so its earliest key lands on the key just left of the cursor.

`RIGHT_KEY` :

Right Key.

Align the paste so its final key lands on the key just right of the cursor.

`CURRENT_FRAME` :

Current Frame Value.

Offset the keys against the curve's value beneath the cursor.

`CURSOR_VALUE` :

Cursor Value.

Offset the keys against the cursor's Y position.

NONE :

No Offset.

Paste the keys carrying the exact values they had when copied.

## Keying Flag Api Items

### Keying Flag Api Items

`INSERTKEY_NEEDED` :

Only Needed.

Add keyframes solely on the F-Curves that actually require them.

`INSERTKEY_VISUAL` :

Visual Keying.

Key from the evaluated 'visual transforms' rather than the raw values.

`INSERTKEY_REPLACE` :

Replace Existing.

Update keyframes that are already present and add none.

`INSERTKEY_AVAILABLE` :

Only Available.

Skip making new F-Curves for channels that have none yet.

`INSERTKEY_CYCLE_AWARE` :

Cycle Aware Keying.

For a curve set to cyclic extrapolation, fold the keyframe back into the cycle's time span, and when an end key changes, sync its counterpart too.

## Keying Flag Items

### Keying Flag Items

`INSERTKEY_NEEDED` :

Only Needed.

Add keyframes solely on the F-Curves that actually require them.

`INSERTKEY_VISUAL` :

Visual Keying.

Key from the evaluated 'visual transforms' rather than the raw values.

## Motionpath Range Items

### Motionpath Range Items

`KEYS_ALL` :

All Keys.

Spanning the earliest keyframe through the latest.

`KEYS_SELECTED` :

Selected Keys.

Spanning the earliest selected keyframe through the latest.

SCENE :

Scene Frame Range.

The full Scene or Preview range.

MANUAL :

Manual Range.

A frame range you set yourself.

## Nla Mode Blend Items

### Nla Mode Blend Items

REPLACE :

Replace.

The strip's values overwrite the running total, scaled by the influence setting.

COMBINE :

Combine.

The strip's values merge into the running total using addition, multiplication, or quaternion math as the channel type dictates.

ADD :

Add.

The strip's weighted output is added onto the running total.

SUBTRACT :

Subtract.

The strip's weighted output is taken away from the running total.

MULTIPLY :

Multiply.

The strip's weighted output is multiplied into the running total.

## Nla Mode Extend Items

### Nla Mode Extend Items

NOTHING :

Nothing.

The strip exerts no effect beyond its own bounds.

HOLD :

Hold.

Hold the first frame when no earlier strips occupy the track, and always hold the final frame.

`HOLD_FORWARD` :

Hold Forward.

Hold only the final frame.

## Operator Return Items

### Operator Return Items

`RUNNING_MODAL` :

Running Modal.

Leave the operator active inside Blender.

CANCELLED :

Cancelled.

The operator quit without making any change, so nothing needs to go on the undo stack.

FINISHED :

Finished.

The operator wrapped up its action and then exited.

`PASS_THROUGH` :

Pass Through.

Take no action and forward the event onward.

INTERFACE :

Interface.

Dealt with but not actually run (as with popup menus).

## Property Flag Enum Items

### Property Flag Enum Items

`READ_ONLY` :

Read Only.

While active, the property stays uneditable.

HIDDEN :

Hidden.

For operators: keep it out of the spots where Blender would auto-insert the property, such as Adjust Last Operation. The property is also left out of presets..

`SKIP_SAVE` :

Skip Save.

For operators: the property's value is not carried over from one invocation to the next; every run begins from the default instead. The property is also left out of presets..

ANIMATABLE :

Animatable.

`LIBRARY_EDITABLE` :

Library Editable.

This property stays editable even on linked data (normally read-only). Be aware that such edits are not stored in the blend file..

`ENUM_FLAG` :

Enum Flag.

## Property Flag Items

### Property Flag Items

`READ_ONLY` :

Read Only.

While active, the property stays uneditable.

HIDDEN :

Hidden.

For operators: keep it out of the spots where Blender would auto-insert the property, such as Adjust Last Operation. The property is also left out of presets..

`SKIP_SAVE` :

Skip Save.

For operators: the property's value is not carried over from one invocation to the next; every run begins from the default instead. The property is also left out of presets..

`SKIP_PRESET` :

Skip Preset.

Leave it out of presets.

ANIMATABLE :

Animatable.

`LIBRARY_EDITABLE` :

Library Editable.

This property stays editable even on linked data (normally read-only). Be aware that such edits are not stored in the blend file..

PROPORTIONAL :

Adjust values proportionally to each other.

`TEXTEDIT_UPDATE` :

Update on every keystroke in textedit ‘mode’.

`OUTPUT_PATH` :

Output Path.

`PATH_SUPPORTS_BLEND_RELATIVE` :

Relative Path Support.

This path accepts the relative “//” prefix, which expands to the folder holding the current “.blend” file..

`SUPPORTS_TEMPLATES` :

Variable expression support.

This path accepts the “{variable_name}” template syntax, swapping in the referenced variable's value wherever the template expression appears.

## Property Subtype Number Array Items

### Property Subtype Number Array Items

COLOR :

Linear Color.

A color in the scene's linear working color space.

TRANSLATION :

Translation.

DIRECTION :

Direction.

VELOCITY :

Velocity.

ACCELERATION :

Acceleration.

MATRIX :

Matrix.

EULER :

Euler Angles.

Euler rotation angles given in radians.

QUATERNION :

Quaternion.

A quaternion rotation (it influences NLA blending).

AXISANGLE :

Axis-Angle.

An axis paired with the angle to spin about it.

XYZ :

XYZ.

`XYZ_LENGTH` :

XYZ Length.

`COLOR_GAMMA` :

sRGB Color.

A color in sRGB space (chiefly for UI colors).

COORDINATES :

Coordinates.

LAYER :

Layer.

`LAYER_MEMBER` :

Layer Member.

NONE :

None.

## Rigidbody Object Shape Items

### Rigidbody Object Shape Items

BOX :

Box.

Cube-style volumes, planes such as ground planes included.

SPHERE :

Sphere.

CAPSULE :

Capsule.

CYLINDER :

Cylinder.

CONE :

Cone.

`CONVEX_HULL` :

Convex Hull.

A surface wrapped tightly around every vertex (shrinkwrap style); fewer vertices give the best outcome.

MESH :

Mesh.

A triangle-only mesh that supports finer contact than convex hulls do.

COMPOUND :

Compound Parent.

Merges its immediate rigid body children into a single rigid object.

## Rigidbody Object Type Items

### Rigidbody Object Type Items

ACTIVE :

Active.

The simulation results drive this object directly.

PASSIVE :

Passive.

The animation system drives this object directly.

## Snap Animation Element Items

### Snap Animation Element Items

FRAME :

Frame.

Lock onto the frame.

SECOND :

Second.

Lock onto whole seconds.

MARKER :

Nearest Marker.

Lock onto the closest marker.

## Space Action Mode Items

### Space Action Mode Items

DOPESHEET :

Dope Sheet.

Work with every keyframe in the scene.

TIMELINE :

Timeline.

A pared-down timeline whose header holds the playback controls, with no channel list, side-panel, or footer.

# Track, 2D Stabilization Panel, Workflow, Camera ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Track; 2D Stabilization Panel; Workflow; Camera; Plane Track.

## Track

Automated tracking pursues selected features through video sequences.

The Track Motion operator follows marked regions frame-by-frame (or across entire sequences) respecting Tracking Settings. When tracking fails mid-sequence, failed marks are disabled and the process resumes; single-frame tracking predicts the next location even if the current marker remains active.

Backwards
Reference
Mode: Tracking
Menu: Track ‣ Track Motion ‣ Backwards
Shortcut: Shift - Ctrl - T

Runs tracker in reverse through the footage.

Frame Backwards
Reference
Mode: Tracking
Menu: Track ‣ Track Motion ‣ Frame Backwards
Shortcut: Alt - Left

Advances one frame backward.

Forwards
Reference
Mode: Tracking
Menu: Track ‣ Track Motion ‣ Forwards
Shortcut: Ctrl - T

Runs tracker forward through the entire clip.

Frame Forwards
Reference
Mode: Tracking
Menu: Track ‣ Track Motion ‣ Frame Forwards
Shortcut: Alt - Right

Advances one frame forward.

Clear

Purge tracked and keyframed marks within ranges.

Before
Reference
Mode: Tracking
Menu: Track ‣ Clear ‣ Before
Shortcut: Shift - T

Erases all marks after the playhead for selected tracks.

Clear Active
Limits erasure to the active track only.

After
Reference
Mode: Tracking
Menu: Track ‣ Clear ‣ After
Shortcut: Alt - T

Erases all marks before the playhead for selected tracks.

Clear Active
Limits erasure to the active track only.

Track Path
Reference
Mode: Tracking
Menu: Track ‣ Clear ‣ Track Path
Shortcut: Shift - Alt - T

Empties all but the current mark from selected tracks.

Clear Active
Limits action to the active track only.

Clear Solution
Described elsewhere.

Refine

Reruns tracking from a prior keyframe forward (or backward), using existing mark positions as starting points. The algorithm then polishes the correspondence.

Useful when a tracked feature vanishes temporarily. After manually placing a mark where the feature reappears, Refine optimizes its position.

Direction (Refine Forwards or Backwards) matches your original tracking pass.

Backwards
Reference
Mode: Tracking
Menu: Track ‣ Refine ‣ Backwards

Refines backward.

Forwards
Reference
Mode: Tracking
Menu: Track ‣ Refine ‣ Forwards

Refines forward.

Add Marker
Reference
Mode: Tracking
Menu: Track ‣ Add Marker

Drops a marker under the cursor, movable before finalizing (LMB / Return / Spacebar confirms). Shortcut: Ctrl - LMB places the marker directly at the click point.

The track preview widget displays the pattern area live, letting you dial in position precision before committing.

Detect Features
Reference
Mode: Tracking
Menu: Track ‣ Detect Features

Identifies trackable points in the current frame and marks them. Detection is frame-local; moving objects and offscreen subjects are unmarked automatically.

Placement
How markers are distributed.

Whole Frame
Marks across the entire image.

Inside Annotated Area
Marks only within hand-drawn regions; narrows focus to areas of interest.

Outside Annotated Area
Marks exclude annotated zones; removes clutter (backgrounds, crowds).

Margin
Inset from image edges (pixels). Edge-adjacent markers fail quickly; increase this to reduce manual fixes.

Threshold
Minimum feature quality; low allows weak features (risky), high skips them. Balance to get desired count.

Distance
Spacing between marks. Prevents clustering, which degrades solver accuracy.

Create Plane Track
Reference
Mode: Tracking
Menu: Track ‣ Create Plane Track

Builds a plane track from coplanar point tracks; used for billboard/screen replacement in compositing.

The operator generates a plane object deforming identically to the plane defined by all selected point tracks.

Minimum requirement: four point tracks spanning the entire footage for the plane to be replaced. More tracks yield superior plane motion estimation.

Feature points need not be corners—they can lie anywhere on the plane. Corners are often occluded or difficult to track precisely. Positioning tracked features distant from the actual surface to be replaced supplies richer information about plane deformation; such markers track even when partially obscured.

Overlapping neighbor frames must share at least four common tracks.

The Plane Track Deform Node can project an image onto the solved plane.

Solve Camera/Object Motion
Reference
Mode: Tracking
Menu: Track ‣ Solve Camera/Object Motion

Computes camera or selected object motion using all tracks and two keyframes.

Requirements:

- At least eight tracks must appear in both keyframes.

- Parallax between keyframes must be significant.

Success reports average reprojection error (editor header)—mean distance from reconstructed 3D positions projected back to 2D footage versus original locations. Below 0.3 = accurate; 0.3–3.0 = acceptable; above 3.0 = tracking error or incorrect camera settings.

Join Tracks
Reference
Mode: Tracking
Menu: Track ‣ Join Tracks
Shortcut: Ctrl - J

Merges all selected tracks into one; selected tracks must not share markers on identical frames.

Average Tracks
Reference
Mode: Tracking
Menu: Track ‣ Average Tracks

Creates a new track by averaging data across selected tracks—useful for stabilizing blurry or low-contrast features. All marker properties are averaged; disabled markers are excluded.

Gaps between segments are linearly interpolated to suppress jumps. Interpolation applies only to interior gaps; tracks lacking markers at beginning or end frames will exhibit jumps in those regions.

Keep Original
When enabled, preserves selected tracks instead of removing them.

Copy Tracks
Referenced elsewhere.

Paste Tracks
Referenced elsewhere.

Animation
Referenced elsewhere.

Show/Hide
Referenced elsewhere.

Clean Up
Removes suspect tracks via filter criteria.

Clean Tracks
Reference
Mode: Tracking
Menu: Track ‣ Clean Up ‣ Clean Tracks

Identifies tracks matching criteria and applies a specified action.

Tracked Frames
Removes tracks or segments shorter than this frame count.

Reprojection Error
Removes tracks exceeding this error threshold.

Action
Selects the operation applied to flagged tracks.

Select
Highlights them for review.

Delete Track
Removes entire tracks.

Delete Segments
Removes only bad track segments.

Filter Tracks
Reference
Mode: Tracking
Menu: Track ‣ Clean Up ‣ Filter Tracks

Removes obviously poor tracks (too short, etc.) and highlights those with suspicious motion spikes.

Delete Track
Reference
Mode: Tracking
Menu: Track ‣ Delete Track
Shortcut: X

Removes all selected tracks.

Delete Marker
Reference
Mode: Tracking
Menu: Track ‣ Delete Marker
Shortcut: Shift - X

Removes selected markers.

Track panel settings.

Track panel configuration.

Name
Editable field for track identifier. Used when linking to constraints (Follow Track, etc.).

Enable
Toggle marker status. Disabled markers don't contribute to solving or constraints.

/ Lock
Toggles lock state. Locked tracks resist accidental editing—useful for finalized tracks.

Track Preview Widget

The preview widget displays the pattern area, checking tracking accuracy (feature position consistency) and repositioning. Drag with mouse to move the track directly via widget.

When an anchor differs from the tracked position (setup for masking without good on-position features), preview shows the anchor area. Expand widget height using the highlighted area below (two horizontal lines).

Further Options

R, G, B
Tracking occurs in grayscale; high feature-to-background contrast improves accuracy. Disabling color channels increases contrast.

Grayscale Preview (B/W)
Displays preview as grayscale even with all channels enabled.

Alpha
Applies annotation-tool mask in the preview.

Weight
3D reconstruction assigns reduced weight to problematic tracks, controlling influence on solution. Animatable.

Animating weights corrects jumps as features vanish/degrade. Alternatively: after careful tracking/solving, lock all markers (Ctrl - L), set tracker weight to zero, and use feature detection for quick placement. These markers won't influence solution but provide scene reference.

Stabilization Weight
Used for 2D stabilization (separate from Weight for 3D reconstruction).

Custom Color Presets
Preset selector for custom color.

Custom Color
Overrides default marker color in Clip editor and 3D Viewport; distinguishes feature types (background vs. foreground). Enables track-group selection by color via Select Grouped.

Tip: Select optimal tracking points near timeline midpoint and track bidirectionally outward. This maximizes the chance of markers remaining in-frame.

Track panel—Track header sections.

Clip

Set Scene Frames: See Set Scene Frames documentation.

Prefetch: See Prefetch documentation.

Reload: See Reload Clip documentation.

Marker

Add: See Add Marker documentation.

Delete: See Delete Track documentation.

Detect Features: See Detect Features documentation.

Tracking Settings

The Tracking Settings panel governs 2D tracking parameters. Presets (panel header) provide starting values based on real footage, facilitating workflow.

Pattern Size, Search Size
Dimensions for newly created tracks.

Motion Model
Defines expected feature motion—select based on actual feature behavior for maximum accuracy.

Location, Location & Rotation, Location & Scale, Location, Rotation & Scale, Affine: Standard motion models.

Perspective: Planar feature tracking; Affine approximates well with more stability.

Match
Determines which pattern frame is tracked. Example: the tracker receives search-area images and a first-image feature position, then locates that feature in the second image.

Sequence tracking selects the second image from an unknown-position frame (next tracking target). The first image varies:

Keyframe: Pattern from a keyframed frame. Prevents position drift (original pattern return) but may jump and fail with feature deformation (perspective).

Previous Frame: Keyframes inserted per-frame; tracking occurs between keyframe and next image. Handles large transformations but drifts from original.

Prepass
Enables two-pass tracking: first pass = brute-force location only; second pass = full motion model refining.

Normalize
Normalizes patterns by average intensity, compensating illumination change (e.g., marker in shadow).

R, G, B
Color channels used by the algorithm. Disabling channels increases contrast for feature detection.

Copy from Active Track
Duplicates all settings from the active track, easing multi-track setup.

Tracking Extra Settings

Weight
See Track Weight documentation.

Correlation
Minimum pattern-to-reference correlation for successful tracking. Low values extend tracking (risky); high values stop early. Adjust for desired behavior.

Margin
Disables tracks too close to image boundary (pixel distance).

Use Mask
Applies annotation-tool mask to pattern, narrowing the match region.

Frames Limit
Maximum frames tracked per Track Sequence call, aiding early-notice of slide-off.

Speed
Marker-specific—controls sequence-tracking speed (quality unchanged, aids visibility). Tracking often exceeds real-time; Speed adds delay to catch drift.

Track

Track: See Track Motion documentation.

Clear: See Before documentation.

Refine: See Refine documentation.

Merge

Join Tracks: See Join Tracks documentation.

## 2D Stabilization Panel

2D stabilization removes handheld jitter.

Enable: toggle the switch AND turn on Show Stable (Clip Display pop-over). Then add tracking points.

Configure location and rotation/scale tracks; weighted averaging per group generates per-frame compensation.

For panning shots, Expected parameters (position/rotation/zoom) simulate intentional motion, restoring framing.

Activation: switch + Show Stable.

Options

2D Stabilization panel configuration.

Anchor Frame
Reference frame anchoring the stabilization; other frames adjust relative to this frame's position, orientation, and scale. Choose a frame where the subject appears optimally.

Stabilization Type

Rotation: Stabilizes detected rotation around the rotation pivot (weighted average of location tracks) in addition to position.

Scale: Compensates scale changes relative to rotation center.

Tracks for Stabilization

Location: Tracks compensating camera position jumps.

Rotation/Scale: Tracks compensating camera tilt and scale. May share location tracks but typically use distant, symmetrical points.

Autoscale: Computes minimal zoom eliminating image boundary artifacts.

Max: Limits autoscale magnitude.

Expected Position X/Y: Subtracts known shot offset (e.g., panning).

Expected Rotation: Compensates original shot rotation (e.g., tilting).

Expected Zoom: Scales the result to offset original zoom.

Influence
Controls how much compensating motion applies. Some jumps may intentionally remain uncompensated. These parameters affect only compensation motion (not deliberate Expected movements).

Interpolate
Stabilization uses sub-pixel accuracy; adjacent source pixels must combine for result pixels. Interpolation softens and degrades sharpness slightly.

Nearest: No interpolation; retains original sharpness but preserves sub-pixel jitter as 1-pixel steps.

Bilinear: Linear interpolation; quality/performance balance.

Bicubic: Highest quality; most computationally expensive.

## Workflow

Good stabilization can be quick and easy or take work, dedication, and careful planning, depending on the footage; this section covers practical considerations to improve the results.

The Simple Case: when the camera is basically fixed — or nearly stationary — and the footage is crisp without motion blur, perfect stabilization is easy (e.g. a tripod with minor shake from wind or floor vibration, or a steady shoulder-camera shot by an experienced operator).
- Use as few points as possible; start with a single point right on the main subject.
- Track that point as accurately as you can, watching for movement and shape changes; proceed in small increments (e.g. 50 frames), zoom in, and readjust the target manually when it drifts — or use a larger target area, accepting the slower tracking since it's only one point.
- After enabling basic (location) stabilization, decide whether you really need rotation stabilization; minor, slow swinging is often unnoticeable and not worth the extra time and quality loss from rotation and scale stabilization.
- For rotation, start with one extra point, well spaced but preferably still attached to the main subject.
- Consider fixing slow residual motion by manually animating the "Expected *" parameters before adding more markers, since extra markers are often not worth the effort.
- If you do add points, the most important goal is symmetry: place location tracking points symmetrically above and below the horizon, and rotation tracking points in diagonally opposed directions, always centered on the main focal area.

Avoid Problematic Footage: the 2D stabilizer can't work miracles — some flaws simply can't be fixed satisfactorily, notably motion blur, rolling shutter, pumping autofocus, and moving compression artifacts, all of which become more noticeable once basic stabilization succeeds. Don't fall for "fix it in post production"; it rarely works out well.
- Prefer a short exposure time to avoid motion blur: while motion blur renders filmed movement more smooth and natural, it seriously impedes precise feature tracking — as a guideline, try to reach at least 1/250 s.
- Prefer higher frame rates; the more temporal resolution the stabilizer has, the better the results. Given a choice between progressive and interlaced, by all means use interlaced and deinterlace to the doubled frame rate — doable with FFmpeg's yadif filter in mode 1 (send_field).
- Beware the Rolling Shutter effect: avoid fast lateral movements, prefer a camera that produces less rolling shutter, and note that a higher frame rate reduces it (another reason to prefer interlaced here).
- Switch off autofocus: better plan your movement, set a fixed focus, and rely on depth of field via a small aperture; pumping movements may not be noticeable to a viewer, but feature tracking tends to slide on defocused elements, and fixing this after the fact can waste a lot of time.
- Increase the lighting level, or at least use a higher sensitivity, to allow a fast shutter speed plus a small aperture; better lighting and good exposure also reduce the impact of compression artifacts, and choosing a codec with less data reduction and a better color space helps — some quality is inevitably lost through the interpolation needed for stabilization, plus some through color-space conversion.

Elaborate Movements: when the footage relies on elaborate, intended camera movement — especially with a shift in the main area of interest — stabilization becomes more involved, and with many tracks and fine-grained animation it's easy to make manipulations that actually lower quality while the root cause is hard to spot. Proceed systematically, from the general outline down to specific aspects:
- Understand the nature of the shot's movements, both intended and accidental.
- Track some relevant features for location.
- Establish the basic location stabilization, including deciding which feature to use for which segment; work the track weights for an overall consistent movement of the weight center, matching the shot's inherent focus.
- Define the virtual camera's panning movements (by animating the Expected Position parameter).
- Add tracking for rotation and zoom stabilization.
- Fine-tuning pass: break the whole shot into logical segments to define the intended camera movement, then refine each incrementally, step by step, until the overall result looks satisfactory.

Animating Stabilization Parameters: animating some parameters across the shot is often necessary for the final touch, including controlling the scale factor to hide the dancing black borders. A known limitation in the current version: you can't open the generic animation editors (Graph editor and Dope Sheet) for animation data beyond the 3D scene. So while you can set keyframes right within the stabilizer's UI controls (via the I key or the context menu), you can't manipulate the resulting curves graphically — the only way to readjust or remove a misguided keyframe is to move the timeline to that very frame and use the animated UI control's context menu. (Hint: the UI control's color changes when you're located exactly at the keyframe's frame number.)

Irregular Track Setup: you may not be able to track a given feature for the whole shot — it might blur, get obscured, or leave the frame entirely from deliberate camera movement. Then another tracked feature must take over its role, with some overlap time for a smooth, jump-free transition. The stabilizer handles gaps and partial coverage within tracks, but its basic assumption is that each track covers a single, fixed reference point wherever there's usable/enabled data, so you must not "reuse" one track to follow several different points — instead disable and thus end a track once that feature is no longer feasible to track. You may include "gaps" (a point temporarily disabled or unavailable), but start a new track for each distinct new feature.
Each track contributes to the overall result by the degree set in its Stab Weight parameter, evaluated on a per-frame basis, so you can control a track's influence by animating Stab Weight. Picture the stabilizer's overall working as each tracking point "dragging" the image through a flexible spring: turning down a point's Stab Weight decreases the amount of "drag" it creates. Sometimes different tracks have to work partly counter to each other — which can be used to cancel out spurious movement, e.g. from perspective — but if one of those tracks suddenly goes away, a jump in image position or rotation can result. So whenever you notice a jump at the very frame where a partially covered track starts or ends, soften the transition by animating Stab Weight gradually down so it reaches zero at the boundary point. Likewise, when planning a "handover" between several partially covered tracks, define a cross-fade over the duration where they overlap by animating the Stab Weight parameters accordingly. Even with such cross-fade smoothing, some residual movement might remain, which then needs correcting with the Expected Position or Expected rotation parameters. It's crucial to avoid "overshooting" movements in such a situation — always strive to set the animation keyframes on precisely the same frame number for all the tracks and parameters involved.

## Camera

This panel holds all settings of the camera used to film the movie currently edited in the Clip editor. Predefined settings can be chosen from the panel header, but settings such as distortion coefficients and the principal point aren't part of the presets and should be filled in even when a preset is used.
Sensor Width — the width of the camera's CCD sensor, found in the camera specifications.
Pixel Aspect — the CCD sensor's pixel aspect, found in the specifications or sometimes guessable: for example, if the footage should be 1920×1080 but the images themselves are 1280×1080, the pixel aspect is 1920 / 1280 = 1.5.

Lens:
Focal Length — the focal length the movie was shot with; it can be set in millimeters or pixels.
Optical Center — defines the lens's optical center (also known as the principal point); in most cases this coincides with the image center, but certain lenses have an offset optical center (refer to the camera or lens specifications if needed), and the values are given in normalized image coordinates.
Lens Distortion — the mathematical function that converts distorted to undistorted coordinates.
- Polynomial: polynomial radial distortion, using three distortion coefficients: K1, K2, and K3.
- Division: defines high distortions, making this model much better suited to cameras with fisheye lenses; uses two distortion coefficients: K1, K2.
- Nuke: the distortion model used by the Nuke compositor; uses two distortion coefficients K1, K2.
- Brown: Brown-Conrady, one of the most advanced lens-distortion models, used to model both radial and tangential distortion; can use up to four radial distortion coefficients K1 - K4 and up to two tangential distortion coefficients P1 and P2.
Coefficients — used to compensate for the lens distortion present when the movie was shot. Currently these values can only be tweaked by hand (there are no calibration tools yet) using the tools available in Distortion mode — tweak K1 until the solve is closest to the known focal length, while also taking the grid and annotations into account to prevent "impossible" distortion.
Radial Distortion Coefficients (K1 - K4) — these coefficients work independently of each other; positive values give a barrel distortion while negative values give a pincushion distortion, and mixing negative and positive coefficients lets you define more complicated mustache distortions or other complex distortions that are less common but not rare.
Tangential Distortion Coefficients (P1, P2) — these work independently and let you compensate for situations where the sensor isn't perpendicular to a group of lenses, which shifts (distorts) the optical center (principal point) off the sensor center: P1 compensates for sensor rotation about the Z (vertical) axis, while P2 compensates for rotation about the X (horizontal) axis; such distortions appear in footage from cameras with a sensor-stabilization system.

## Plane Track

Plane Track panel displays properties when a plane track is selected.

Plane Track panel configuration.

Name
Displays and allows editing the selected plane track name.

Auto Keyframe
Toggles auto-keyframing for plane track corners. Enabled = keyframes inserted when any corner moves.

Image
Selects or creates an image displayed inside the plane track (preview only in Movie Clip editor). For final render output, use Plane Track Deform node.

New Image from Plane Track
Generates an image from Movie Clip pixels the plane marker "sees" at the current frame; creates unwarped texture for flat surfaces. Enables editing/retouching (paint-out, etc.).

Update Image from Plane Track
Refreshes the plane track image pixels.

Opacity
Sets image display opacity (preview only; does not affect render).

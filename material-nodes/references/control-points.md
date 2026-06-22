# Control Points, Editing Text Objects, Selecting Text, Volume Properties ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Control Points; Editing Text Objects; Selecting Text; Volume Properties; Editing Masks; Movie Clip Data-Blocks; Clip.

## Control Points

### Control Points

### Extrude Curve and Move

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Extrude Curve and Move

Shortcut :

E

Adding new control points to a surface is done primarily through extrusion — and unlike Curves, you can't simply add them directly.

The workflow: first select an entire border of the surface grid, then hit E to copy those control points and drag the mouse to position them where you want.
Wrap up by clicking LMB to lock them in. (Or back out with RMB or Esc, which cancels the move and leaves the new control points sitting where they started.)

### Example

To begin, pick one border control point and grow the selection to cover its whole row
with Select Control Point Row.

| Selecting control point | Selecting remaining control points in the row |

From there, run the extrusion a couple of times:

Control points extruded twice

### Make Segment

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Make Segment

Shortcut :

F

The name suggests a single grid line gets drawn between two control points, but the behavior is closer to Bridge Edge Loops for meshes: it spans the gap
between two separate surfaces, laying down however many new segments that takes. Just pick a border
row (or column) on each surface and press F to stitch those borders together.

Bear in mind that both surfaces have to belong to the same Surface object. Two standalone
objects must first be merged into one with Join.
On top of that, the two borders you're joining need an equal count of control points.

### Example

In the pictures below, two "surfaces" that are really just curves get bridged, though
joining full sheets works the same way.

| Before bridging. | After bridging. |

### Smooth

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Smooth

Nudges the chosen control points so the surface reads as smoother.

### Hooks

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Hooks

Shortcut :

Ctrl - H

Attaches a Hook Modifier so the selected control points
track a given object or bone.

### Make Vertex Parent

Reference

Mode :

Edit Mode

Menu :

Control Points ‣ Make Vertex Parent

Shortcut :

Ctrl - P

Sets up a parent-child link so a chosen object
trails the selected control point(s).

Staying in Edit Mode, pick another object by either Ctrl - LMB clicking it in the
3D Viewport or choosing it from the Outliner.
Next, select either one or three control points of the surface and hit Ctrl - P .
Parent the object to three control points and it tracks their averaged position.

## Editing Text Objects

### Editing Text Objects

Compared to other object types, text is edited in a fairly unusual way, split mainly across two locations. The first is
the 3D Viewport, where you do your typing and have a handful of shortcuts on hand, for instance to apply
styles (see Font) – though note that most of the Edit Mode shortcuts you're used to
simply don't exist for text. The second is the Properties, the Font tab in particular.

Editing a text object feels a bit like working in a plain text editor, just with fewer
features and a few quirks of its own.
The 3D Viewport header menu carries only a few entries — no transform tools, no mirror tools, and so on.
Leave Edit Mode with Tab; rather than inserting a tab character, it
toggles in and out of Edit Mode, the same as it does for other object types.

### Cut

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Cut

Shortcut :

Ctrl - X

Cut and copy text to the buffer with the shortcut or the matching Edit-menu entry.

### Copy

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Copy

Shortcut :

Ctrl - C

Copy text to the buffer with the shortcut or the matching Edit-menu entry.

### Paste

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Paste

Shortcut :

Ctrl - V

Paste text out of the buffer with the shortcut or the matching Edit-menu entry.

### Paste File

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Paste File

Pulls in text from an external text file.
A File Browser opens for you to locate a valid UTF-8 file.
Watch out for files with too many characters, since that drags down
interactive response.

### To Uppercase

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ To Uppercase

Switches the selected text to uppercase.

### To Lowercase

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ To Lowercase

Switches the selected text to lowercase.

### Insert Unicode

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Insert Unicode

Pops up a dialog where you enter any Unicode character by typing its hexadecimal code point value.

Wikipedia's List of Unicode characters
documents the matching hexadecimal code point values.

### Special Characters

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Special Characters

A small character map for slipping in characters the keyboard doesn't offer directly.
Plenty of other special characters can instead be "composed" — see Accent Characters.
Anything beyond that you'll have to copy-paste from an outside editor or character map program.

Note

The text buffer stays in step with the desktop clipboard.
When used inside Blender, though, text formatting rides along in the copy too.
For other ways of inserting a text, see Inserting Text.

### Toggle Bold, Italics, Underline, Small Caps

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Toggle Bold/Italics/Underline/Small Caps

To give a run of characters the Bold , Italics , Underline or Small Caps attribute,
either switch the relevant setting on before you start typing,
or select text you've already typed and toggle the style you want from the menu.

Warning

Blender's Bold and Italic buttons behave differently than they do in other applications,
since they double as slots for loading other fonts by hand.

### Kerning

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Kerning

Kerning refers to the gap between one character and the next.

Decrease Kerning Alt - Left
Tightens the gap between the characters flanking the cursor.

Increase Kerning Alt - Right
Widens the gap between the characters flanking the cursor.

Reset Kerning
Returns the gap between the characters flanking the cursor to its default.

### Delete

Reference

Editor :

3D Viewport

Mode :

Edit Mode

Menu :

Header ‣ Text ‣ Delete

Previous/Next Character
Wipes out the character sitting before or after the cursor.

Previous/Next Word
Wipes out the word sitting before or after the cursor.

### Inserting Text

Text can come in two ways: out of the internal text buffer, or out of a text file.

Take an existing text data-block and turn it into an object from the Text editor's header by
choosing Edit ‣ Text to 3D Object ,
then One Object or One Object per Line as your needs dictate.

You can also paste in from the clipboard or a file while editing 3D text.

### Accent Characters

A lot of special characters — accented letters and the like, which your keyboard doesn't provide directly —
can be "composed" out of two other characters. The recipe:
type the base character, press Alt - Backspace ,
then press the chosen "modifier" to form the special character.
A few examples follow:

| ã: A , Alt - Backspace , ~ á: A , Alt - Backspace , ' à: A , Alt - Backspace , \ â: A , Alt - Backspace , ^ å: A , Alt - Backspace , O æ: A , Alt - Backspace , E ª: A , Alt - Backspace , - ë: E , Alt - Backspace , " ç: C , Alt - Backspace , , ¢: C , Alt - Backspace , / | ø: O , Alt - Backspace , / §: S , Alt - Backspace , S †: / , Alt - Backspace , - ‡: / , Alt - Backspace , = ©: O , Alt - Backspace , C ®: O , Alt - Backspace , R ™: T , Alt - Backspace , M ½: 1 , Alt - Backspace , 2 ÷: - , Alt - Backspace , : ±: - , Alt - Backspace , + |

### Converting to a Mesh or Curve

Over in Object Mode, a text object can be turned into a mesh or a curve — see Convert.

Tip

Because the resulting topology tends to be a little messy,
running a Limited Dissolve deletion or applying a
Remesh modifier
at a low threshold can help tidy up your mesh.

### Assigning Materials

Reference

Mode :

Edit

Panel :

Properties ‣ Materials

Giving individual characters their own Material index lets you put different materials
on different characters.

Assign those indices as you type, or do it afterward by selecting blocks of text and
hitting the Assign button in the Materials panel.

Red Green Blue text example.

## Selecting Text

### Selecting Text

Text in Edit Mode.

Just like in any text editor, Edit Mode shows a white cursor that marks where the next characters you type will land.

Select All Ctrl - A
Picks out the entire text.

Top/Bottom Shift - Ctrl - Home / Shift - Ctrl - End
Jumps the cursor to the very start or very end of the text object.

Next/Previous Character Left / Right
Walk the cursor along with the arrow keys.

Next/Previous Word Ctrl - Left / Ctrl - Right
Hop the cursor to a word boundary.

Line Begin/End Home / End
Send the cursor to the start or the end of a line.

Next/Previous Line Up / Down
Skip from one line to another.

Next/Previous Block PageUp / PageDown
Leap ten lines back or forward at a stroke.

Hold Shift along with the arrow keys to select a stretch of text.
That's how you target a span for different materials or the normal/bold/italic style…

## Volume Properties

### Volume Properties

### Grids

In the List View you'll see each grid that the OpenVDB file holds, together with its name and data type.
A "grid" is a body of volumetric data; usually it records each voxel's density,
though it can just as well hold temperatures, velocities, and so on.

Pick a grid and the volume object switches to showing it.

### OpenVDB File

File Path
Which VDB file gets used.

Sequence
Pulls in extra VDB files, one for every animation frame. Just like image sequences,
each file wants a numbered suffix, so choosing smoke-000.vdb
in the File Path expects a smoke-001.vdb, a smoke-002.vdb, and so on after it.

Frames
How many of the sequence's frames to play through.

Start
The scene frame on which the sequence kicks off.

Offset
How many of the sequence's opening frames to leave out.

Mode
What the volume does before the sequence's opening frame ( Start ) and after its
closing one ( Start + Frames ).

Clip :

Display nothing at all.

Extend :

Hold on the sequence's first or last frame and keep it on screen.

Repeat :

Loop the sequence over and over (and over…).

Ping-Pong :

Run the sequence forward, then in reverse, then forward once more, and so on.

### Viewport Display

Wireframe
How the volume is drawn in wireframe shading mode.
When the volume data is heavy, you might prefer to keep the object locked to wireframe display the whole time.
Doing so keeps the 3D Viewport snappy while the volume still turns up in the final render.

None :

Leaves the volume out of wireframe mode entirely.

Bounds :

Draws the volume as one Bounding Box spanning the whole grid.

Boxes :

Draws a bounding box around each node of the volume tree.

Points :

Draws a point at each node of the volume tree.

Detail
How fine the Boxes or Points wireframe rendering gets.

Coarse :

Puts a single box or point at every intermediate node of the tree.

Fine :

Puts a box or point at each leaf node, which covers 8×8 voxels.

Density
How thick the volume looks in the 3D Viewport.
The volume's density at render time gets tuned through
Volume Shading instead.

Interpolation
Which interpolation method gets used when visualizing the fluid grid.

Linear :

Interpolates linearly from voxel to voxel — a good balance of smoothness and speed.

Cubic :

Interpolates cubically from voxel to voxel — smoother, higher quality, but heavier to compute.

Closest :

Skips interpolation between voxels, leaving the raw voxels as they are.

### Slice

Draws just one flat 2D cross-section of the domain object.

Axis

Auto :

Lets the slice direction follow whichever way you're looking.

X/Y/Z :

Cuts the slice along the X, Y, or Z axis.

Position
Where the slice sits, measured against the length of the matching side of the domain.

### Render

Space
How the volume's density and step size get worked out.

Object :

Holds volume Density and Detail steady no matter how the object is scaled.

World :

Lets you set Step Size and Density in world space.

Clipping Cycles Only
The cutoff below which voxels count as empty space, used to speed rendering up.

Precision Cycles Only
How precise the volume data is. Drop this down to use less memory, at the price of detail.

Full :

Full float — every value stored at 32 bit.

Half :

Half float — every value stored at 16 bit.

Variable :

Quietly drops to lower precision wherever the result is harder to notice.

Velocity Grid Cycles Only
The name of the grid that holds per-voxel velocities, used to compute motion blur.
It can either be the name of one grid carrying 3D vectors,
or the prefix shared by three separate grids carrying scalar values.
For the three-grid case, the X grid's name should end in x , .x or _x ,
and the Y and Z grids follow the same pattern.

Velocity Unit Cycles Only
Whether the velocity grid(s) are expressed in distance per frame or per second.

Velocity Scale Cycles Only
A multiplier of your own that gets applied to the velocities held in the VDB.

## Editing Masks

### Editing Masks

Whichever of the two editors you happen to be in, mask editing uses the same panels and tools.
Working with mask splines plays out much like editing Bézier curves or paths in GIMP and similar curve editors.

Tip

For live feedback on how the mask turns out,
wire a Mask node straight into a Viewer node in the Compositor,
and the compositing result will refresh as you edit.

### Transform

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Transform

Move G
Shifts control points to a new location. You can also drag control points with LMB .
Drag the center dot with LMB to move the whole spline at once.

Rotate R
Repositions control points by turning them around a pivot point.

Scale S
Repositions control points by widening or narrowing the gaps between them.

To Sphere Shift - Alt - S
Bends the control points into the shape of a circle.

Shear Shift - Ctrl - Alt - S
Slides control points along a chosen axis so that parallel ones slip past each other.

Push/Pull
Draws the control points nearer together (Push) or pushes them apart (Pull).

Scale Feather Alt - S
Resizes the feather.

### Clear Feather Weight

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Clear Feather Weight

Drops the feather weight back to zero.

### Toggle Cyclic

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Toggle Cyclic

Shortcut :

Alt - C

Flip between a closed curve and an open one.
Closing the mask ties the final control point back to the first.

### Set Handle Type

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Set Handle Type

Shortcut :

V

Choose the handle type for the selected spline points.

### Recalculate Handles

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Recalculate Handles

Shortcut :

Shift - N

Brings the normals (handle directions) into line with one another.

### Switch Direction

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Switch Direction

Flips the handle directions inward/outward.

### Copy Paste

### Clear Parent

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Clear Parent

Shortcut :

Alt - P

Breaks any parenting tie on the selected spline points.

### Make Parent

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Make Parent

Shortcut :

Ctrl - P

Ties one or more selected spline points to the active motion tracker.

### Animation

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Animation

The shape keying system can drive mask animation.
That comes in handy when the footage lacks enough solid feature points to track,
or when the mask isn't tied to footage at all.
Timing for mask animation can be edited from the Dope Sheet's Mask Mode.

Insert Shape Key I
Drops a shape key onto the active mask layer at the current frame.
It works at the level of the mask layer,
so the insert keyframes every spline and point the layer contains.

Clear Shape Key Alt - I
Wipes the shape key off the active mask layer at the current frame.

Feather Reset Animation
Clears the feather offset across every animated frame.

Re-Key Points of Selected Shapes
Re-interpolates the selected points over the span of keys you've picked in the Dope Sheet .

### Show/Hide

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Show/Hide

- Hide Selected H

- Hide Unselected Shift - H

- Clear Restricted View Alt - H

### Delete

Reference

Mode :

Mask Mode

Menu :

Mask ‣ Delete

Shortcut :

X

Strips out control points.

### Miscellaneous

Slide Spline Curvature LMB
Drags the curve and/or its control points by clicking on them and pulling.

Add Vertex and Slide Ctrl - LMB
Drops in new control points and sets their handle orientation through a continued drag of the mouse.
With the last point selected, a double-click also closes off the curve.

Add Feather Vertex and Slide Shift - Ctrl - LMB
Drops in new feather control points you can move independently of the main spline curve.
When no feather mask exists yet, this lays a basic feather mask onto the curve.

## Movie Clip Data-Blocks

### Movie Clip Data-Blocks

The video files and image sequences you use for motion tracking, masking, and compositing are held in Movie Clip data-blocks.

Their main home is the Movie Clip Editor,
but nodes and other systems that accept video input can reference them too.

### Creating a Movie Clip

There are a few ways to make a Movie Clip:

- Open a video file or image sequence inside the Movie Clip Editor.

- Drop a clip into the Compositor with a
Movie Clip node.

- Reach for the data-block selector in any editor that accepts Movie Clip references.

Once a file loads, a Movie Clip data-block springs into being and is kept inside the current
Blend file.

### Properties

These are the main properties a Movie Clip data-block exposes:

File Path
Where the video file or image sequence lives on disk.

Start Frame
Which scene frame the clip's opening frame is pinned to.
That's how you line the footage up against the timeline.

Frame Offset
Slides the clip's own internal frame numbering while leaving its place
in the scene timeline alone. Useful for syncing footage that doesn't
begin at frame 1.

Color Space
States which color space the image file was stored under.
Blender uses that to convert the image correctly into its
internal linear color space, where all color math and rendering happen.

sRGB is the common storage choice for textures and finished renders,
whereas OpenEXR images are kept in a linear color space.
Certain images — normal, bump, or stencil maps, for instance — don't really hold "colors" at all,
so no color conversion should ever touch them.
Set the color space of those images to Non-Color .

Which color spaces show up in the list comes down to the active OCIO config.
For a detailed write-up of the ones supported by default, see
Default OpenColorIO Configuration.

### Usage

Where Movie Clips most often come into play:

- Motion Tracking to rebuild camera movement
or follow objects.

- Masking for rotoscoping and compositing.

- Input in the Compositor through Movie Clip nodes.

A single Blend file can hold several Movie Clip data-blocks,
so one project can draw on different footage sources.

### Data-Block Management

Being ordinary Blender data-blocks, Movie Clips can be handled from the
Outliner.

What they allow:

- Renaming.

- Fake User (keeps an unused clip from being cleaned out automatically).

- Unlinking from editors or nodes.

Note

Deleting a Movie Clip data-block from the Blend file leaves
the original media file on disk untouched.

## Clip

### Clip

### Open Clip

Reference

Mode :

All modes

Menu :

Clip ‣ Open Clip

Shortcut :

Alt - O

### Set Scene Frames

Reference

Mode :

Tracking

Menu :

Clip ‣ Set Scene Frames

Pushes the scene's end frame out to match the current clip's length.

### Prefetch

Reference

Mode :

All modes

Menu :

Clip ‣ Prefetch

Shortcut :

P

Packs the cache with frames, loading as many as the cache will hold off the drive.
The idea is to fill the cache as quickly as possible for when you really need to track something,
while leaving the CPU and drive bandwidth idle whenever a Clip editor is open but you're not actively working in it.

### Reload Clip

Reference

Mode :

All modes

Menu :

Clip ‣ Open Clip

Forces the currently loaded movie clip to reload. Mostly handy when the clip gets edited outside of Blender.

### Proxy

### Set as Background

Reference

Mode :

Tracking

Menu :

Clip ‣ Set as Background

Makes the clip you're editing the camera background across every visible 3D Viewport.
Nothing happens if no 3D Viewport is visible or the Clip Editor is running full screen.

### Setup Tracking Scene

Reference

Mode :

Tracking

Menu :

Clip ‣ Setup Tracking Scene

Runs through the usual steps for getting a scene ready for match moving and compositing automatically.

It sketches out a bare-bones VFX workflow by:

- Dropping in reference objects — a floor plus a stand-in cube — so you can confirm the track holds up.

- Adding a camera object and wiring it to follow the motion that was tracked.

- Building a compositor node tree that lays the rendered 3D scene over the background plate.

The end result hands you a launch pad for placing 3D objects into live footage.

Tip

- Lean on the generated floor reference to seat 3D objects on the footage's ground plane.

- Swap out the stand-in cube, or keep it around to sanity-check that the tracked motion lines up.

- Push the compositor setup further with masks, color grading, or whatever extra effects you need.

Note

Treat this operator as a convenience shortcut.
Heavier VFX work may still call for a hand-built compositor node setup or manual scene tweaks.

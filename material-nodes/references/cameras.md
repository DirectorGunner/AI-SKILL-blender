# Cameras, Color Spaces

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Cameras; Color Spaces.

## Cameras

### Cameras 

Blender renders pictures of a scene through a camera, and that object decides which part of the scene the frame captures.

Because no camera ever turns up in a render, none carry material or texture options.
What they do offer is Object and Editing panels, surfaced once the camera becomes active.

See also

3D Viewport Camera Navigation
for documentation about managing cameras in the viewport.

### Properties 

Reference

Mode :

Object Mode

Editor :

Properties ‣ Camera

### Lens 

Type

These options decide the way solid 3D shapes get flattened into the 2D frame.

Perspective
This is the look the eye gives you day to day.
Far-off things shrink against near ones, and parallel rails seem to draw together with distance.

Focal Length/Field of View
Think of Focal Length as zoom: it fixes how much scene the frame holds at once.
Crank the length up for a tighter FOV and more zoom; shorten it to fit more scene in
(larger FOV , less zoom).

| Perspective camera with 35 mm focal length.  | Perspective camera with 210 mm focal length instead of 35 mm.  |

Lens Unit
State focal length either in millimeters or straight as the Field of View angle.

Hint

Pull Focal Length down while closing on a subject and you get a Dolly Zoom; push it up to reverse the effect.

This video demonstrates the Dolly Zoom camera effect.

Orthographic
Here every object keeps its real size whatever its distance from the camera.
Parallel lines stay parallel as a result, never meeting the way Perspective makes them.

Render from the same camera angle as the previous examples, but with orthographic perspective. 

Orthographic Scale
This dials the on-image size of the projected objects.

It is essentially the only knob orthographic perspective responds to.
With no vanishing points in this mode (parallel lines never meet), shifting the lens just mimics sliding the camera in the 3D Viewport.

Panoramic
Cycles Only

This single type gathers a whole assortment of panoramic projections.
See the Cycles panoramic camera settings for more information.

Custom
Cycles Only

The Custom type hands camera behavior over to your own OSL code.
See the Cycles custom camera documentation for more information.

Shift
Your handle on the vanishing points .
That term names the spot where parallel lines look like they meet.
The railroad's far end is the standout vanishing point throughout these examples.

| Horizontal lens shift of 0.330.  | Rotation of the camera object instead of a lens shift.  |

See how shifting the lens leaves horizontal lines dead level, whereas turning the camera body tilts them.

Note

Shifting the lens comes to the same thing as rendering a wider FOV and trimming the result off-center.

Clip Start and End
The band over which objects are drawn directly.
Whatever sits past it still tints the picture indirectly, since later light bounces escape clipping.

Note

Capping these distances counts in viewport rendering: it preserves enough rasterization precision.
Ray traced output shrugs the issue off, so it stomachs far wilder values.

Tip

Turn on Limits under Viewport Display and the clip bounds appear as two joined yellow dots running along the camera's sightline.

See also

- 3D Viewport clipping

### Depth of Field 

A real lens bends incoming light and brings it to a focus on the sensor.
The upshot: only subjects at one set distance read sharp, while everything closer or farther blurs.

Example of DOF bokeh effect. 

That sharp band is the focal point. Set it with a plain figure, or by the gap between the camera and an object you name:

Focus Object
Name the object that fixes the focal point. Linking one switches the distance parameter off.

Focal Distance
The focal-point distance used while no Focus Object is named.
Enable Limits in the camera's Viewport Display panel to picture this distance inside the 3D Viewport.

Hint

Either click the eyedropper or hover the Focal Distance field and press E to arm the Depth Picker .
Then LMB any point in the 3D Viewport to read its distance back to the camera.

#### Aperture 

F-Stop
This ratio governs the strength of the blur.
The lower you go, the heavier the depth of field.

Blades
How many polygonal blades reshape the blurred objects across the render and its preview. As in the viewport, the bokeh effect needs 3 blades at minimum, which gives a triangular blur.

Rotation
Turn the polygonal blades around the facing axis, either clockwise or the other way.

Ratio
Skew the distortion to mimic anamorphic bokeh.
1.0 leaves it undistorted; under 1.0 stretches the blur sideways, over 1.0 stretches it up and down.

### Camera 

The settings in this group echo what a physical camera body offers.
Reach for a Preset to line Blender up with a real-world camera.

Sensor Fit
Governs the way the sensor sits inside the output dimensions, and through that the angular field of view.

Auto :

Works out a square sensor from whichever of the Resolution dimensions is larger.

Horizontal :

Set the sensor Width yourself; the Height follows from the output Resolution aspect ratio.

Vertical :

Set the sensor Height yourself; the Width follows from the output Resolution aspect ratio.

Size / Width, Height
A second path to the field of view that leaves focal length alone.
Handy when pairing a Blender camera to a real lens-and-body combo, motion tracking being one case.

### Safe Areas 

Safe areas mark where to drop elements so a scene's vital content survives on screens of every kind.

Overscan differs from screen to screen, and old TV sets are the worst offenders.
So some content never reaches all viewers, because the band ringing the image edge stays hidden.
TV broadcasters answered this by defining two zones whose content is always shown: action safe and title safe.

Modern LCD and plasma sets run purely digital signals with zero Overscan, yet safe areas remain good practice and can be a broadcast legal requirement.

Inside Blender you open safe areas from either the Camera or the Sequencer view.

Red line: Action safe. Green line: Title safe. 

Tune the Safe Areas by their outer margin, a percentage of the run between center and render edge.
The camera view and the Video Sequence editor read the very same values.

Title Safe Margins X/Y
Also known as Graphics Safe .
Park all your key information, be it graphics or text, inside this zone so most viewers can take it in.

Action Safe Margins X/Y
Hold any notable action or character within this region.
Doubling as a screen "margin," it also keeps elements from bunching up against the edges.

Tip

Each nation lays down its own legal broadcast standard, and those specify, among plenty else, exact safe-area numbers.
Blender's safe-area defaults follow the EBU (European Union) standard.
Double-check you have the right figures before producing broadcast work, to sidestep trouble.

#### Center-Cut Safe Areas 

Center-cuts are an extra safe-area pair that keep content reading right on screens of a differing aspect ratio.
Feed an old TV 16:9 or 21:9 video and it lops off the sides.
Park content inside the center-cut zones so your composition's most important parts hold up on those screens.

Out of the box Blender draws a 4:3 (square) ratio sitting inside 16:9 (widescreen).

Cyan line: action center safe. Blue line: title center safe. 

### Background Images 

Dropping a backdrop image into the camera earns its keep in many jobs:
modeling is the clear one, but it pays off in painting too
(say, holding face references while you paint textures right onto the model…),
and in animation, where a video stands in as backdrop, among others.

Background Source
Where the backdrop image originates.

Image :

Draw on an outside image, an image sequence, a video file, or a generated texture.

Movie Clip :

Draw on one of the scene's Movie Clip data-blocks.

Active Clip
Display whichever Movie Clip the scene flags as its Active Clip.

Render Undistorted
Draw the backdrop through undistorted proxies wherever they are on hand.

Proxy Render Size
Pick either full non-proxy display or a proxy size for drawing the backdrop.

See also

To build a proxy, the Movie Clip Editor Proxy settings have to be used.
Otherwise the proxy settings here have no effect.

Color Space
The color space Blender reads the image or video file as.

View as Render
Apply the color management settings as this image goes to screen.

Opacity
Sets the backdrop image's transparency.

Depth
Place the image either behind every object or out ahead of them all.

Frame Method
How the image is sized into the camera view.

Stretch :

Pins the image's dimensions to the camera bounds, the aspect ratio shifting if it must.

Fit :

Shrinks the image until it sits wholly inside the camera view, the aspect ratio held intact.

Crop :

Enlarges the image until it covers the whole camera view, the aspect ratio held intact, so its overhanging parts get clipped.

Offset X, Y
Nudge the backdrop image by these amounts.

Under orthographic views the unit is ordinary scene units.
In the camera view it goes relative to the camera bounds (0.1 shifts it by 10% of view width or height).

Rotation
Spin the image about its own center.

Scale
Enlarge or reduce the image from its center.

Flip

X
Mirrors the image left to right, sending the left edge to the right and the reverse.

Y
Mirrors the image top to bottom, sending the top edge to the bottom and the reverse.

Note

A Movie Clip, or any image set to view as render, sits behind objects only with film transparency enabled or the scene world disabled in the viewport.

### Viewport Display 

Camera view displaying safe areas, sensor and name. 

Size
The camera's drawn size in the 3D Viewport. This touches nothing in the render output. The standard Scale S transform key resizes the camera visualization too.

Show

Limits
Draws an orange line marking Clip Start and End, plus a yellow cross at the Focus Distance .
With the Focus Distance gizmo switched on in the 3D Viewport's gizmo settings, you can drag that cross by mouse to set the distance.

Mist
Flips the mist-limit display on or off.
Two joined white dots along the camera sightline mark them.
You set the mist limits and their companion options over in the World panel's Mist section.

Sensor
Puts a dotted frame inside camera view.

Name
Flips the name display on or off in camera view.

Passepartout
Dims everything beyond the camera's field of view.
The value slider sets how opaque that dimming runs.

Tip

A fully opaque Passepartout lets Blender optimize, speeding up rendering of the area within the camera view.

#### Composition Guides 

Turn on Composition Guides to lay framing aids over the camera display.

Thirds
Rules the frame into vertical and horizontal thirds.

Center

Center
Rules the frame into vertical and horizontal halves.

Diagonal
Joins the opposite corners with lines.

Golden

Ratio
Splits width and height by Golden proportions (close to 0.618 of the size in from each frame edge).

Triangle A
Strikes a diagonal from lower-left up to upper-right, then drops perpendiculars passing through the corners at top-left and bottom-right.

Triangle B
As A, swapped to the other corner pair.

Harmony

Triangle A
Strikes a diagonal from lower-left up to upper-right, then sends lines from each of the bottom-right and top-left corners out to 0.618 along the facing side.

Triangle B
As A, swapped to the other corner pair.

Color
Fixes the color and opacity (alpha) every composition guide overlay shares.
Useful for dialing their visibility up or down against a lighter or darker shot.

### Cameras 

### Panoramic Cameras 

Cycles carries several panoramic camera types, each laid out below.
Note that none of them can show in non-rendered viewport modes, Solid mode among them; they kick in only for the final render.

### Equirectangular 

Render the scene as a panorama from the camera's spot using an equirectangular projection, always sweeping the full 360° on the X axis and 180° on the Y axis.

Since this projection agrees with the environment texture world shaders use, you can render an environment map with it. For the default mapping, give the camera object a rotation of (90, 0, -90), or simply aim it down the positive X axis.
That comes to looking at the image center under the default environment texture mapping.

Latitude Min, Max
Bounds on the vertical field of view angles.

Longitude Min, Max
Bounds on the horizontal field of view angles.

### Equiangular Cubemap Face 

A step up from Equirectangular, spreading the rendered pixels of the spherical environment more evenly.
The payoff is an image whose visual resolution scarcely budges across the whole spherical projection.
Equirectangular, by contrast, can bleed detail at the poles, and cube map projections bleed it near each face's edges.

This panorama type shines for virtual reality, where wringing the most visual detail out of a capped resolution matters.

One thing it gives up against Equirectangular is any longitude or latitude limits.

### Fisheye 

Fisheye lenses run wide angle with heavy distortion, useful for panoramic images bound for dome projection say, or for an artistic flourish.

For the closest match to real cameras, reach for the Fisheye Equisolid lens.
It hands you a focal length together with a field-of-view angle, and the sensor dimensions feed in as well.

The Fisheye Equidistant lens maps to no real lens model; it throws a circular fisheye that pays the sensor information no mind and instead works the whole sensor. That makes it a fine lens for full-dome projections.

Lens
The lens's focal length, given in millimeters.

Field of View
The field-of-view angle; push it to 360 and beyond to swallow the whole environment.

### Fisheye Lens Polynomial 

Pin down a real-world camera by handing over the coefficients of a degree-four polynomial.

Here is the projection's chain of steps.
Every image pixel finds a spot \((x, y)\), measured in mm, across the camera sensor.
From that sensor spot follows a direction whose spherical coordinates run
\((1, \theta, \phi)\), in radians, this way:

\[\begin{split}& r = \sqrt{x^2 + y^2}\\
& \theta = k_0 + k_1 r + k_2 r^2 + k_3 r^3 + k_4 r^4\\
& \phi = acos(x/r)\end{split}\]

Light coming in along that direction then lands on the matching pixel.

You can model both fisheye and perspective cameras this way.

### Mirror Ball 

Render as if photographing a reflective mirror ball.
On rare occasions it helps for comparing against a like photo shot to capture an environment.

## Color Spaces

### Color Spaces 

### Linear Workflow 

Rendering, showing, and storing images each demand a Different Color Space.

For rendering and compositing the best fit is a scene linear color space, since it follows nature more closely and keeps the math physically sound.
Blender leans on scene linear color across materials, lighting, geometry and compositing.

Those numbers, though, line up with neither human sight nor the workings of a display.
And image files frequently park in other color spaces to squeeze better compression.

A sound linear workflow hinges on tagging both images and displays with the right color spaces.
Blender then runs the conversions into and out of scene linear color.

An example of a linear workflow. 

### Working Space 

Reference

Editor :

Properties

Panel :

Render Properties ‣ Color Management ‣ Working Space

File
The color space behind every scene linear color in this file, and the one shader, compositing and geometry node processing run in. It defaults to Linear Rec.709, with Linear Rec.2020 and ACEScg on hand for a broader gamut and ACES compatibility.

Since each data-block draws its colors from the working space, the pick weighs on render and composite results in a big way. Best to lock the working space in at a project's start and hold it across every blend file.

Blender can move between working spaces, but only as an approximation that usually wants hand correction. Link or append a data-block and its colors convert automatically to the current file.

Sequencer
The color space the Sequencer works in.
By default that is sRGB, though you may switch it to Linear, matching the Compositing nodes, or to another color space.
Color correction, crossfades and the like come out differently from one color space to the next.

The default supported color spaces are described in
Built-in Color Spaces.

### Images and Video 

With image and video files, Blender first tries to detect the color space on its own.
Guesses wrong, and you can set the file's color space by hand in the image settings.

The classic case for a manual change is loading or baking normal maps and displacement maps.
Those maps carry no real color, only data wearing a color disguise.
Flag such images as Non-Color Data .

For intermediate production image files, OpenEXR is the recommended format.
It always sits in scene linear color spaces at high precision, so nothing is lost.
That makes it a good home for renders you will later composite, color grade, and recast into other output formats.

### Built-in Color Spaces 

Blender's OCIO configuration file is equipped by default to read/write files in these color spaces

### Display 

Color spaces for displays and image files.

sRGB :

Standard RGB display space using Rec. 709 chromaticities and a D65 white point.

Rec.2020 :

BT.2020 2.4 Exponent EOTF Display.

Rec.1886 :

BT.1886 2.4 Exponent EOTF Display, commonly used for TVs.

Display P3 :

Apple's Display P3 with sRGB compound (piece-wise) encoding transfer function, common on Mac devices.

Rec.2100 PQ :

For high dynamic range images and video with Rec.2020 wide gamut, up to 10000 nits.

Rec.2100 HLG :

For high dynamic range images and video with Rec.2020 wide gamut, up to 1000 nits.

### Linear 

Color spaces commonly used for OpenEXR files.

Working Space :

The current blend file's linear working space, the default for compositing, shader and geometry nodes.

Linear Rec.709 :

Linear BT.709 chromaticities with illuminant D65 white point.

Linear Rec.2020 :

Linear BT.2020 with illuminant D65 white point.

ACEScg :

An ACES color space meant for rendering and compositing.
Its makeup is AP1 primaries, a white point at D60, and a transfer function that is linear.
The standard working space in ACES workflows.

ACES2065-1 :

An ACES color space whose makeup is AP0 primaries, again a D60 white point, with a linear transfer function.
Built to store and ship data while holding onto the most information it can.
The usual choice for delivery and archival across ACES workflows.

Linear FilmLight E-Gamut :

Linear E-Gamut with illuminant D65 white point.

Linear DCI-P3 D65 :

Linear DCI-P3 with illuminant D65 white point.

Linear CIE-XYZ E :

1931 CIE XYZ standard with assumed illuminant E white point.

Linear CIE-XYZ D65 :

1931 CIE XYZ with adapted illuminant D65 white point.

### Other 

Non-Color :

Plain non-color data, left untouched by any color transform (normal or displacement maps, for instance).

Working Space :

Falls back on the File color space set in the scene's color management.

### Log 

ACEScc :

ACES color correction space, using AP1 primaries.

ACEScct :

ACES color correction space with toe, using AP1 primaries.

AgX Log :

Intermediate log color space of AgX view transform.

Filmic Log :

Intermediate log color space of Filmic view transform.

### Utilities 

Color spaces that pair with view transforms. Use them for backdrop images you want spared the view transform while the rest of the scene takes it.

ACES 1.3 sRGB :

ACES 1.3 view transform

ACES 2.0 sRGB :

ACES 2.0 view transform

AgX Base sRGB :

AgX view transform

Filmic sRGB :

Filmic view transform

Khronos PBR Neutral sRGB :

Khronos PBR Neutral view transform

# Principled Volume, Volume Scatter, Environment Texture Node, Ies Texture Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Principled Volume; Volume Scatter; Environment Texture Node; IES Texture Node; Sky Texture Node; Mapping Node; Vector Transform Node; Object Color; Lighting; Apply; Clean Up; Convert; Delete; Join; Make Single User; Rigid Body.

## Principled Volume

### Principled Volume

The Principled Volume shader gathers every volume-shading component behind one convenient node. A single node can render volumes like smoke and fire, since it bundles scattering, absorption and blackbody emission together.

### Inputs

Color
Volume scattering color.

Color Attribute
Volume grid that colours the volume. Use "color" for smoke simulations.

Density
Density of the volume.

Density Attribute
Volume grid that sets the density, usually "density".

Anisotropy
Backward or forward scattering direction.

Absorption Color
Volume shadow color tint.

Emission Strength
Amount of light to emit.

Emission Color
Emission color tint.

Blackbody Intensity
Blackbody emission for fire. Set to 1 for physically accurate intensity.

Blackbody Tint
Color tint for blackbody emission.

Temperature
Kelvin temperature driving blackbody emission; raise it to emit more.

Temperature Attribute
Volume grid that sets the temperature, usually "temperature".

### Properties

This node has no properties.

### Outputs

Volume
Feed the Volume Shader result to the Volume Input on either the Material or World Output node.

### Examples

## Volume Scatter

### Volume Scatter

This node lets light scatter as it crosses the volume. A common job is adding fog; paired with the Volume Absorption node it also makes smoke.

### Inputs

Color
Per-channel scattering coefficients.

Density
How strong the scatter effect is.

Anisotropy Henyey-Greenstein Draine
Sets the balance between back- and forward-scattering.

IOR Fournier-Forand
Index of refraction of the scattering particles relative to water. Ordinary ocean water sits between 1.0 and 1.2, while denser, murkier water climbs higher.

Backscatter Fournier-Forand
Share of light thrown back the way it came. Most ocean particles fall between 0.001 (such as very large phytoplankton) and 0.1 (such as very small mineral grains); pure water sits at 0.5. Figures from
Ocean Optics Web Book.

Alpha Draine
A blend control between the Henyey-Greenstein ( \(\alpha = 0\) ) and Cornette & Shanks ( \(\alpha = 1\) ) phase functions.

Diameter Mie
Diameter of the scattering particles in µm.

### Properties

Phase
Volume scattering phase function.

Henyey-Greenstein :

A simple, widely used phase function, handy for roughly modelling scattering inside biological tissue.

Fournier-Forand :

Cycles Only
Aimed at modelling how light scatters underwater.

Draine :

Cycles Only
Aimed at modelling how interstellar dust scatters.

Rayleigh :

Cycles Only
Covers scattering by particles smaller than light's wavelength, like sunlight scattering through Earth's atmosphere.

Mie :

Cycles Only
Covers scattering by particles larger than light's wavelength, like cloud and fog.

Tip

A Mix Shader lets you combine these phase functions.

Volume scattering phase plotted against the angle between incoming and outgoing direction, on a logarithmic scale. Light arrives from the left.

### Outputs

Volume
Feed the Volume Shader result to the Volume Input on either the Material or World Output node.

### Examples

Example of Volume Scatter.

## Environment Texture Node

### Environment Texture Node

The Environment Texture node lights your scene from an environment-map image used as a texture.

### Inputs

Vector
Coordinate for the texture look-up. Left unconnected, the image wraps as an environment with the Z axis pointing up.

### Properties

Image
Image data-block serving as the image source. More settings sit in Sidebar ‣ Item ‣ Properties : these cover the alpha channel along with extra colour-space options. Those extra options are written up alongside the rest of
Common Image Settings.

Color Space
What kind of data the image holds, either Color or Non-Color Data. Most colour textures want the Color default, but for something like a bump or alpha map the pixels should read as Non-Color Data so no unwanted colour-space conversion creeps in.

Which colour spaces are listed depends on the active OCIO config. The defaults are spelled out here:
Default OpenColorIO Configuration

Texture Interpolation
Which interpolation the environment texture is sampled with. The available options:

Linear :

Regular quality interpolation.

Closest :

No interpolation, use closest pixel.

Cubic :

Smoother, better quality interpolation.

Smart :

Bicubic when magnifying, otherwise Bilinear is used.
This is only available for OSL.

Projection Method
Lets you pick among different kinds of environment map. The supported choices:

Equirectangular :

Projection from an Equirectangular photo.

Mirror Ball :

Projection from an orthographic photo or mirror ball.

### Outputs

Color
RGB color from the image.

### Examples

HDR image from OpenFootage.net.

## IES Texture Node

### IES Texture Node

The IES Texture matches real-world lights using IES files ( IES ). An IES file records how a light source spreads its intensity across directions.

### Inputs

Vector
Coordinate used to look the light distribution up; with nothing supplied it takes the normal.

Strength
Light strength multiplier.

### Properties

Mode
Where the IES file is loaded from.

Internal :

Use an IES profile embedded in a text data-block inside the blend-file, which makes it easy to ship.

External :

Load an IES profile from a file on the drive.

### Outputs

Factor
Light intensity, usually fed into the Strength input of an Emission node.

### Examples

Lights with different IES profiles.

## Sky Texture Node

### Sky Texture Node

This node builds a procedural sky, normally paired with the World Output Node.

### Inputs

Vector
Where the texture is sampled; with nothing plugged in it falls back to Generated coordinates.

### Properties

Sky Type
Sky model to use.

Single Scattering
An improved take on the 1993 model by Nishita et al, accounting for single bounces in the atmosphere. Legacy, and may be dropped in a future version.

Multiple Scattering
Based on this work by Fernando García Liñán, the most accurate model on offer since it accounts for multiple bounces of light in the atmosphere.

Preetham
Based on the 1999 paper by Preetham et al. Legacy, and will be dropped in a future version.

Hosek/Wilkie
Based on the 2012 paper by Hosek and Wilkie. Legacy, and will be dropped in a future version.

Note

Single and Multiple Scattering skies are, accurately, very bright by default. Lower the scene's Exposure in Properties ‣ Color Management ‣ Exposure to bring it down.

Sun Direction
Sun direction vector.

Turbidity
Atmospheric turbidity.

- 2: Arctic like

- 3: clear sky

- 6: warm/moist day

- 10: hazy day

Ground Albedo
How much light the planet surface bounces back into the atmosphere.

Sun Disc Cycles Only
Turn sun-disc lighting on or off.

Sun Size
Angular diameter of the sun disc (in degrees).

Sun Intensity
Multiplier for sun disc lighting.

Sun Elevation
How far the sun is rotated up from the horizon (in degrees).

Sun Rotation
How far the sun is rotated around the zenith (in degrees).

Altitude
Height above sea level of the camera. Place the camera on a beach and 0 is right; put it in an airliner cockpit and 10 km fits better.

Air
Density of air molecules. A value of 1 is roughly urban city air; 0 is no air.

Aerosols
Density of aerosol particles (water droplets). A value of 1 is roughly urban city aerosols; 0 is none.

Ozone
Density of ozone molecules, useful for pushing the sky bluer. A value of 1 is roughly urban city ozone; 0 is none.

### Outputs

Color
Texture color output.

### Examples

Example of lighting with Sky Texture.

## Mapping Node

### Mapping Node

This node adjusts an input vector through translation, rotation, and scaling transformations.

### Inputs

Node inputs vary by configuration. The Location input appears only for Texture and Point vector interpretations.

Vector
The vector subject to transformation.

Location
Translation displacement along each axis.

Rotation
Rotation angle along each axis. XYZ order.

Scale
Scaling amount along each axis.

### Properties

Vector Type
The node applies the transformation based on the interpretation of the input vector.

Point :

The node performs a direct transformation.

Adjusting texture coordinates parallels adjusting a UV map. Moving texture coordinates in the positive X direction shifts the displayed texture in the negative X direction, similar to UV adjustment. Similarly, increasing texture coordinate values reduces the texture size. Coordinate transformation produces opposite visual effects compared to the texture itself.

Transformation order: Scale –> Rotate –> Translate, which means:

- Translation shifts the input along the local rotation axis.

- Rotation pivots the input around the origin.

- Scaling adjusts the input along the global axis.

Texture :

The node performs an opposite transformation.

Reverse-transforming texture coordinates, unlike Point mode, modifies the displayed texture directly. Moving texture coordinates in the positive X direction shifts the displayed texture in the positive X direction as expected. Similarly, raising texture coordinate values enlarges the texture as expected.

Transformation order: Translate –> Rotate –> Scale, which means:

- Translation shifts the input along the global axis.

- Rotation pivots the input around the translation vector.

- Scaling adjusts the input along the local rotation axis.

Vector :

The node applies a Point transformation without translation.

Normal :

The node performs the inverse transpose of the transformation and normalizes the result. This procedure ensures normals remain accurate under non-uniform scaling. Apply this type when transforming normals.

### Outputs

Vector
The input vector following transformation.

### Examples

Mapping node example.

## Vector Transform Node

### Vector Transform Node

This node enables conversion of a vector, point, or normal among world, camera, and object coordinate spaces.

### Inputs

Vector Input
Standard vector input.

### Properties

Type
Specifies the interpretation of the input/output.

Vector, Point, Normal.

Convert From
Source coordinate space:

World, Object, Camera.

Convert To
Target coordinate space:

World, Object, Camera.

### Outputs

Vector Output
The converted output vector.

## Object Color

### Object Color

The colors displayed in Workbench viewport rendering can be adjusted.

Reference

Panel :

Render ‣ Object Color

Material :

Display the color configured per material in the Material's Viewport Display panel.

Object :

Display the color configured per object in the Object's Viewport Display panel.

Random :

Assigns a different random color to every object in the scene.

Attribute :

Display the active Color Attribute of an object. Objects without an active Color Attribute render using the color from their Viewport Display Object panel.

Texture :

Render using the texture from the active Image Texture Node and active UV map. Absent an active texture, the object renders with its Material Viewport Display settings.

Custom :

Render the entire scene in a single user-selected color.

## Lighting

### Lighting

Workbench ignores scene lights, using settings from the Lighting panel instead.

Reference

Panel :

Properties ‣ Render ‣ Lighting

Flat :

Objects render in uniform color without highlights or shadows.

Studio :

A prepared studio lighting arrangement is applied, featuring a front-facing key light and a back-facing rim light. Click the sphere to select an alternative setup.

Studio lights can be customized in Preferences. By default they track the viewport camera, but this can be changed:

World Space Lighting
Fixes lights in place rather than following the viewport camera.

Rotation
The orientation of lights around the Z axis.

MatCap :

A Material Capture image is used, with texturing, lighting, and reflections prebaked. Objects are shaded by sampling colors from the image based on normal direction relative to the camera.

Click the sphere to choose a different MatCap, or use the double arrow button to flip it horizontally.

Custom MatCaps can be loaded in Preferences.

## Apply

### Apply

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply

Shortcut :

Ctrl - A

These operations apply multiple transformation types to selected objects. Transformation coordinates shift from objects to their data. If hierarchical children exist, transformations apply to them as well.

### Transforms

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Location / Rotation / Scale / Rotation & Scale

Applying transforms resets numerical Location, Rotation, or Scale values while preserving on-screen appearance.

Specifically:

- The object's position shifts to the global origin (for location).

- Rotation values zero out.

- Scale values reset to 1.0.

The geometry adjusts so the 3D Viewport and final render appearance remains identical.

For uncomplicated cases, you may perceive no difference, but applying transforms affects how modifiers, constraints, and parenting operate, as they often depend on object transform values.

Warning

Armature Objects

Transform application is supported for armatures but does not affect pose positions, animation curves, or constraints. Apply transforms prior to rigging and animation.

Important

When applying transforms to an object sharing Object Data with others, data must first become Single User. Blender prompts confirmation.

### Options

Location
Apply (set) the object's position. Blender designates the current position as 0 on each axis; the object remains in place but the location becomes the "default." The object origin moves to (0, 0, 0) (where the colored axis lines intersect).

Rotation
Apply (set) the object's rotation. The current rotation becomes 0 degrees on each axis; the object remains in place but the rotation becomes the "default."

Scale
Apply (set) the object's scale. The current scale becomes 1.0 on each axis; the object remains in place but the scale becomes the "default."

Rotation & Scale
Apply (set) both rotation and scale simultaneously.

Apply Properties
Modify attributes such as curve vertex radius, font size, and bone envelope according to the applied transformation. (Appears in the Adjust Last Operation panel)

Corrective Flip Normals
Inverts surface normals when applying negative scale, avoiding inverted shading from negative scaling.

### Transforms to Deltas

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Location / Rotation / Scale to Deltas

Moves the object's primary transforms (Location, Rotation, Scale) into Delta Transforms. Existing delta transforms are added to the new values.

This enables "baking" current transforms into the delta channels while freeing primary transform channels for new adjustments or keyframes.

Available options:

- Location to Deltas – Shifts the object's location to Delta Location.

- Rotation to Deltas – Shifts the object's rotation to Delta Rotation.

- Scale to Deltas – Shifts the object's scale to Delta Scale.

- All Transforms to Deltas – Performs all three simultaneously.

### Options

Reset Values
Clear primary transform values after transfer to deltas.

When enabled, primary Location, Rotation, and Scale reset (to 0 or 1 respectively) while the appearance remains unchanged because deltas hold the prior values.

### Animated Transform to Deltas

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Animated Transform to Deltas

Converts existing animation keyframes from primary transforms (Location, Rotation, Scale) to Delta Transforms.

Animation data shifts from main transform channels to the delta equivalents while main transforms remain at their current values.

### Visual Transform

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Visual Transform

Applies each selected object's constraints to its own transformation. Objects retain their position, rotation, and scale even if their constraints are later disabled or removed.

### Visual Geometry as Mesh

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Visual Geometry to Mesh

Applies the visual state of all selected objects (modifiers, shape keys, hooks, etc.) to their data. This freezes object data as static geometry and converts non-mesh types to mesh.

For details, consult the Convert mesh documentation.

### Visual Geometry to Objects

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Visual Geometry to Objects

Produces new objects from the evaluated geometry of the active object, incorporating all modifier, constraint, and instancing effects.

This operator differs from Make Instances Real in several ways:

- Instanced geometry is not realized. Shared data is maintained across objects using it.

- The source object remains unmodified, avoiding disruptions to object relationships.

- Instancing hierarchies are maintained through new objects and collections reflecting the evaluated structure.

Extracts visible results of geometry nodes, modifiers, or instancing setups without permanently changing the original scene.

Note

Instance attributes (e.g. custom per-instance data) are currently not preserved.

### Make Instances Real

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Make Instances Real

This operation generates a separate object for each instance produced by the selected objects and removes direct instancing from them.

Each instance becomes an actual object.

Warning

This applies to both direct (from verts or faces…) and indirect (from particle system…) instancing. With tens of thousands of instances (from particles for instance), Blender may slow considerably, as it struggles with large object counts.

### Apply

### Options

By default, new objects are added to the original instancer's collection without internal hierarchies. The following options alter this.

Parent
If Keep Hierarchy is not set, parents all generated objects to the original instancer.

Otherwise, parents generated objects not already parented to their instancer or its corresponding new copy (relevant for recursive instancing).

Keep Hierarchy
Maintains internal hierarchies (i.e. parent relationships) within newly generated objects.

Tip

Typically, to produce a new hierarchy matching the instancing arrangement, enable both options.

Note

Recursive instancing preservation (instancers instancing other instancer objects, etc.) is only partially supported.

Uncomplicated cases (like an empty instancing a collection with instances of other collections) typically function well, but complex cases may fail to fully reproduce the complete hierarchy.

### Parent Inverse

Reference

Mode :

Object Mode

Menu :

Object ‣ Apply ‣ Parent Inverse

Applies the object's Parent Inverse transform to the object data.

## Clean Up

### Clean Up

### Clean Vertex Group Weights

Reference

Mode :

Object Mode

Menu :

Object ‣ Clean Up ‣ Clean Vertex Group Weights

This operation removes vertex assignments from Vertex Groups whose weights fall below the Limit threshold. It eliminates insignificant (or zero) weights from your weight groups.

The displayed example uses a 0.2 cutoff (see operator options below), removing all blue areas.

Note: these images employ Show Zero weights Active so unreferenced Weights appear Black.

Clean example.

Subset
Narrow the tool to a subset. Refer to The Subset Option section for subset definition.

Limit
The minimum weight value retained in the group. Weights below this threshold are removed.

Keep Single
Guarantees the Clean Vertex Group Weights operation will not produce completely unlinked vertices (vertices not in any vertex group). Each vertex retains at least one weight, even below the limit.

### Limit Total Vertex Groups

Reference

Mode :

Object Mode

Menu :

Object ‣ Clean Up ‣ Limit Total Vertex Groups

Reduces the weight group count per vertex to the specified Limit. Lowest weights are discarded until the limit is met.

Hint

The tool requires more than one weight group selected to function well.

Subset
Narrow the tool to a subset. Refer to The Subset Option section for subset definition.

Limit
The maximum weight count permitted on each vertex.

### Remove Unused Material Slots

Reference

Mode :

Object Mode

Menu :

Object ‣ Clean Up ‣ Remove Unused Material Slots

Removes unused material slots.

## Convert

### Convert

### Curve

Reference

Mode :

Object Mode

Menu :

Object ‣ Convert ‣ Curve

Transforms the selected mesh or text into a curve object.

- For mesh objects : Only unattached edges (edges not part of any faces) are included.

- For text objects : The text converts to curve outlines, maintaining its form.

The resulting curve uses Poly Curve by default. For smooth segments, convert to a Bézier Curve via Set Spline Type.

### Mesh

Reference

Mode :

Object Mode

Menu :

Object ‣ Convert ‣ Mesh

Transforms the selected curve, metaball, surface, or text into a mesh object. The defined resolution is applied during conversion. Note: faces and volumes generated by closed and extruded curves are maintained.

### Grease Pencil

Reference

Mode :

Object Mode

Menu :

Object ‣ Convert ‣ Grease Pencil

Transforms the selected curve, mesh, or text into a Grease Pencil object, generating strokes following the original shape. Fundamental materials are generated. Multiple selected objects combine into a single Grease Pencil object.

Keep Original
Retains the original object by creating a duplicate prior to conversion.

Thickness
Specifies the stroke width.

Stroke Offset
Modifies the offset to separate strokes from filled regions.

Export Faces
Transforms mesh faces into filled strokes.

### Trace Image to Grease Pencil

Reference

Mode :

Object Mode

Menu :

Object ‣ Convert ‣ Trace Image to Grease Pencil

See Trace Image to Grease Pencil.

### Convert to Mesh Plane

Reference

Mode :

Object Mode

Menu :

Object ‣ Convert ‣ Convert to Mesh Plane

Transforms the selected image empty to a textured mesh plane.

Refer to Mesh Plane for option details.

## Delete

### Delete

Reference

Mode :

Object Mode

Menu :

Object ‣ Delete

Shortcut :

X or Delete

Removes the selected objects from the active scene.

### Delete Globally

Reference

Mode :

Object Mode

Menu :

Object ‣ Delete Globally

Shortcut :

Shift - X or Shift - Delete

Removes the selected objects from all scenes and other usages (like a shading node reference).

## Join

### Join

Reference

Mode :

Object Mode

Menu :

Object ‣ Join

Shortcut :

Ctrl - J

This operation merges all selected objects into the last active object. All object data links to the active object (which must be selected). All objects must be the same type: mesh, curve, surface or armature. If multiple curves are joined, each keeps its subtype (NURBS or Bézier).

Note

Object data carries numerous attributes handled during joining.

Materials, vertex groups, UV and Vertex layers merge.

Modifiers, constraints, groups and parent relationships are omitted during joining and will not apply to the active object.

## Make Single User

### Make Single User 

Reference

Mode:
Object Mode

Menu:
Object ‣ Relations ‣ Make Single User

Duplicates the chosen or all object data-blocks so they are no longer distributed
(linked) among other objects in the file.

It can also generate separate copies of related data,
such as meshes, curves, material definitions, animation tracks…

Type
These actions target the chosen objects, or every object in the viewport.

All, Selected Objects

Data-blocks
In addition to menu defaults, specify which data-blocks to duplicate individually.

Object:
Duplicates object instances.

Object Data:
Duplicates object data (geometry and properties).

Materials:
Make material definitions specific to each data-block.

Object Animation:
Make the Object Properties animation specific to each object.

Object Data Animation:
Make object data (mesh, curve etc.) animation specific to each data-block.

See also

Making Single User

## Rigid Body

### Rigid Body 

### Calculate Mass 

Reference

Editor:
3D Viewport

Mode:
Object Mode

Menu:
Object ‣ Rigid Body ‣ Calculate Mass

Derives mass for rigid body objects from their volume and material density.
The volume is derived mechanically; you supply density based on the material being simulated.

Material Preset
A list of preset density numbers for real-world substances,
if a substance isn't available, research its density and select Custom to enter it manually.

Density
When the Custom Material Preset is active, this specifies the input density in kg/m³.

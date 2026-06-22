# Universal Scene Description

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Importing USD Files — USD files usually lay out the scene as a hierarchy of primitives, or prims, each holding data for a scene entity such as geometry, lights, cameras, and transform hierarchies. Blender's USD importer turns USD prims into a hierarchy of Blender objects; like the exporter, it doesn't yet handle certain USD composition concepts, such as layers and references. These USD data types can import as Blender objects: Cameras, Curves, Lights, Materials, Meshes, Point Clouds, Primitive Shapes, and Volumes. For how each type is handled, see the Import Options below. Note: when importing a USDZ archive, weigh the Import Textures option carefully to decide whether and how to copy texture files out of the zip archive.

Xform and Scope Primitives — USD's Xform prim type holds transform data and can represent transform hierarchies and organize the scene; Xform prims import as Blender empty objects. USD also has Scope primitives — entities with no transform data that simply group other scene elements; Blender has no exact counterpart, so these import as Blender empties at the origin, an imperfect match (empties have a transform, Scopes don't) that nonetheless helps keep the scene hierarchy's structure.

PointInstancer Primitives — USD's UsdGeomPointInstancer prim type holds instances scattered over a primitive's points; these come into Blender as Point Clouds built with a Geometry Nodes Modifier and the Instance on Points Node.

Animations — the importer supports two kinds:
- Animating transforms — when a USD primitive carries time-varying transform data, a Transform Cache constraint is attached to the resulting Blender object.
- Animating geometry — animated mesh, curve, and point-cloud data is handled by attaching a Mesh Sequence Cache modifier to the imported data. Geometry attribute (USD Primvar) animation is supported for every data type with a Blender equivalent, including colors, UVs, velocities, and other generic attribute data. Note: USD file sequences (a unique file per frame) aren't supported.

Materials — when a USD mesh or geometry subset comes with a bound material, the importer hands the Blender object a material whose name matches the USD material; if a Blender material of that name already exists, it may be reused depending on the Material Name Collision option, otherwise a new one is created. When a USD material carries a USD Preview Surface shader source, its Viewport Display color, metallic, and roughness come from the matching USD Preview Surface inputs. There's also an Import USD Preview option that converts USD Preview Surface shaders to Blender Principled BSDF nodes; it can be lossy, since it doesn't yet handle every shader setting and type, but it produces approximate material visualizations.

Coordinate System Orientation — if the imported USD is Y up, a rotation is applied automatically to root objects to convert to Blender's Z up.

Import Options — these are available when importing from USD:
General:
Path Mask — imports just the part of the USD scene that hangs below the given primitive.
Include:
  Visible Primitives Only — skips invisible USD primitives; applies only to primitives with a non-animated visibility attribute, while ones with animated visibility always import.
  Defined Primitives Only — off, this allows importing USD primitives that aren't defined, such as those with an override specifier.
Set Frame Range — updates the scene's start and end frame to match the USD stage's.
Create Collection — adds all imported objects to a new collection.
Relative Path — picks the file relative to the blend-file.
Apply Unit Conversion Scale — scales the scene objects by the USD Stage metersPerUnit value, on top of the Scale option's value.
Scale — how much to scale the imported objects about the world's origin.
Light Intensity Scale — a scale for the intensity of imported lights.
Custom Properties — how to import USD attributes as Custom Properties. None (skip USD custom attributes), User (import attributes in the userProperties namespace as custom properties, with the namespace stripped from the names), or All Custom (import every USD custom attribute as a custom property, keeping namespaces in the names).
Object Types:
Cameras — imports UsdGeomCamera primitives as Camera Objects. Supported attributes include projection type (perspective and orthographic), focal length, depth-of-field distance, F-stop (aperture), clipping start and end, sensor shift (tilt) X and Y, and sensor size (aperture width and height). Note: most properties support animation, but aperture-size import is limited by differences between USD and Blender in how sensor dimensions are read; when aperture sizes are animated, the matching shift values are animated too for consistency.
Curves — imports UsdGeomBasisCurves primitives as Curves and UsdGeomNurbsCurves as Blender meshes.
Lights — imports lights as Light Objects; cylinder and geometry lights aren't included yet.
World Dome Light — turns the first UsdLuxDomeLight or UsdLuxDomeLight_1 dome light it finds into a world background shader.
Materials — imports UsdPreviewSurface materials.
Meshes — imports UsdGeomMesh primitives as Mesh Objects.
Volumes — imports UsdVolVolume OpenVDB assets as Volume Objects.
Point Clouds — imports UsdGeomPoints primitives as Point Cloud Objects.
USD Shapes — imports USD primitive shapes as Blender meshes; UsdGeomCapsule, UsdGeomCapsule_1, UsdGeomCone, UsdGeomCube, UsdGeomCylinder, UsdGeomCylinder_1, UsdGeomPlane, and UsdGeomSphere are supported.
Display Purpose:
  Render — includes primitives with purpose render.
  Proxy — includes primitives with purpose proxy.
  Guide — includes primitives with purpose guide.
Material Purpose — tries to import materials with the given purpose; if none of that purpose is bound to the primitive, the fallback behavior (if any) is noted below.

All Purpose — tries to import allPurpose materials.
Preview — tries to import preview materials, falling back to allPurpose ones.
Full — tries to import full materials, falling back to allPurpose then preview, in that order.

Geometry:
UV Coordinates — reads mesh UV coordinates.
Color Attributes — turns the USD mesh displayColor values into Blender's Color Attributes.
Mesh Attributes — reads USD Primvars as mesh attributes.
Subdivision — adds Subdivision Surface modifiers based on the USD SubdivisionScheme attribute.
Validate Meshes — checks the imported mesh for corrupt data and repairs it if needed; with it off, bad data may crash display or editing. It slows importing but is recommended, since data errors aren't always obvious.
Merge parent Xform — lets a USD primitive merge with its Xform parent when it's the parent's only child.

Rigging:
Shape Keys — imports USD blend shapes as Blender Shape Keys.
Armatures — imports USD skeletons as Blender Armatures.

Materials:
Import All Materials — also imports materials that no geometry uses; with this off, materials referenced by geometry still come in.
Import USD Preview — converts USD Preview Surface shaders to Principled BSDF shader networks.
Set Material Blend — when Import USD Preview is on, the material's blend method is set automatically from the opacity and opacityThreshold shader inputs, letting transparent objects show correctly.
Material Name Collision — what to do when an imported material's name clashes with an existing one. Make Unique (bring each material in as its own Blender material) or Reference Existing (point at the existing material of that name rather than importing).

Textures — when importing a USDZ package, these options decide whether and how the USD's texture asset dependencies are copied out of the zip archive so Blender can load them.
Import Textures — how textures from a USDZ archive are handled. None (skip them; material textures may then fail to resolve in Blender), Packed (bring textures in as packed data in the Blender file), or Copy (copy files to the Textures Directory below).
Textures Directory — where imported textures land when Import Textures is set to Copy. The default is the relative path //textures, which needs the Blender file saved first so the relative path can resolve.
File Name Collision — what to do when an imported texture filename clashes with an existing file. Use Existing (use the existing file rather than copying) or Overwrite (overwrite it).

Particles and Instancing:
Scene Instancing — imports USD scene-graph instances as collection instances; otherwise they come in as copies.

Exporting to USD Files — USD files can hold complex layering, overriding, and references to other files, but Blender's USD Exporter takes a far simpler tack: on export it writes every visible, supported object in the scene, optionally narrowed by selection, and doesn't (yet) export invisible objects, USD layers, variants, and the like. These objects can be exported to USD:
- Meshes (of several kinds, see below).
- Cameras (perspective only for now, not orthographic).
- Curves.
- Text (written as meshes).
- Lights.
- Hair (written as curves, limited to parent strands).
- Point Clouds.
- Metaballs (written as animated meshes).
- Volumes.
- Armatures.
Exporting an animation writes the final evaluated mesh to USD, so these meshes can be exported: static meshes; deforming meshes, where the topology stays put while the vertices move over time (animated characters, or bouncing-but-not-cracking objects); and arbitrarily animated meshes, where the topology does change (a fluid sim where splashes break off the main body, say).
Note: to export the Blender scene as a USDZ archive, give the output file the .usdz extension; the resulting USDZ package is a zip archive holding the USD and its texture dependencies.

Export Options — these are available when exporting to USD.
General:
Root Prim — if set, adds a transform primitive at the given path as the parent of all exported data on the stage.
Include — Selection Only (when checked, only selected objects export; an instanced object, such as a scene-instanced collection, counts as "selected" when its instancer is) and Animation (checked, the whole scene frame range exports; unchecked, only the current frame).
Blender Data — Custom Properties: exports Custom Properties as USD attributes, with the Namespace property setting the namespace they're written to. Namespace: if set, prefixes that namespace onto exported custom-property names, but only those without a prefix already (so it'd apply to name bar, not foo:bar) and never to Blender object and data names, which always go in the userProperties:blender namespace; userProperties is the default. Blender Names: writes USD custom attributes carrying the original Blender object and object-data names. Allow Unicode: keeps UTF-8 characters in USD prim and property names (the resulting files need software on USD 24.03 or newer to open).
File References — Relative Paths: references external files (textures, volumes) by relative path in the exported USD, otherwise by absolute path.
Convert Orientation — converts the orientation axis to another convention to suit other apps. Blender uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up, for instance, needs -Z Forward, Y Up.

Forward / Up Axis — remap these to different axes to convert rotations between another app's default up/forward and Blender's.
Units — sets the USD Stage metersPerUnit metadata to the chosen measure.
Meters Per Unit — the value to use for metersPerUnit when Custom Units is chosen.
Xform Ops — which transform operators carry a prim's transform. Translate, Rotate, Scale (export with translate, rotate, and scale Xform operators), Translate, Orient, Scale (translate, orient quaternion, and scale operators), or Matrix (a single matrix operator).
Use Settings for — whether export uses each object's Viewport or Render visibility, modifier settings, and other such properties.

Object Types:
Meshes — exports Mesh Objects.
Lights — exports Light Objects; the UsdLuxShapingAPI backs spot lights.
World Dome Light — converts the world material to a UsdLuxDomeLight; this works for now on simple materials — an environment texture wired to a background shader, optionally with a vector multiply of the texture color.
Cameras — exports Camera Objects; perspective cameras only.
Curves — exports Curve Objects.
Point Clouds — exports Point Cloud Objects.
Volumes — exports Volume Objects.
Hair — exports parent hair strands as a curve system; strand colors aren't exported.
Note: the USD schema type used on export mirrors the one read on import; see the Import section for details.

Geometry:
UV Maps — when checked, carries UV coordinates along for exported meshes, the USD UV map keeping the Blender name.
Rename UV Maps — exports UV maps under the USD default name (st) instead of Blender's default (UVMap).
Normals — when checked, includes normals for exported meshes, custom loop normals included.
Merge parent Xform — merges USD primitives with their Xform parent where possible; since USD forbids nested UsdGeomGprims, intermediary Xform prims are defined to keep the file valid across object hierarchies.
Triangulate — triangulates the mesh before writing; for the specific option, see the Triangulate modifier.

Rigging:
Shape Keys — exports shape keys as USD blend shapes; absolute shape keys aren't supported.
Armatures — writes Armatures, and meshes carrying Armature Modifiers, out as USD skeletons and skinned meshes. Limitations: modifiers beyond Armature modifiers aren't applied, and bendy bones aren't supported.
Only Deform Bones — exports only deform bones and their parents.

Materials — exports an object's material info; out of the box the exporter approximates the Principled BSDF node tree, recasting it into USD's Preview Surface format. When a mesh carries several materials, a geometry subset is made per material, and the first material, if there is one, also goes on the mesh itself no matter what subsets exist, because the Hydra viewport doesn't support materials on subsets (see USD issue #542). Note: with USD Preview Surface Network and MaterialX Network both off, the material is set to the meshes' viewport materials.
Displacement Support — displacement works with caveats: only object-space displacement (no vector displacement); Midlevel and Scale must be constants; and MaterialX isn't supported yet (see the feature commit).
USD Preview Surface Network — approximates a Principled BSDF node tree by recasting it into USD's Preview Surface format. Note: to support opacityThreshold (a.k.a. "Alpha Clip"), the node tree must either include a Math node set to Round (when the threshold is 0.5) or a pair of Math nodes computing 1 - (value < threshold), with the result plugged into the Principled BSDF's Alpha socket. Warning: not all nodes are supported — for now only simple trees of Diffuse BSDF, Principled BSDF, Image Textures, UVMap, and Separate RGB nodes work.
MaterialX Network — builds material shading graphs in the MaterialX standard, which is designed for high interoperability among DCCs <Digital Content Creation>; in Blender, MaterialX covers most shader nodes and their behavior, with a few caveats below. Implementation Caveats: with the Principled BSDF the resulting graph is very usable, but some of the other BSDFs produce graphs other DCCs find hard to read.
Export Textures — how textures are exported. Keep (use the textures' original location), Preserve (keep file paths of textures from already-imported USD files, and write the rest to a 'textures' folder beside the USD), or New Path (write textures to a 'textures' folder beside the USD).
Overwrite Textures — allows overwriting existing texture files on export.
USDZ Texture Downsampling — a maximum size for all exported textures. Keep (current sizes), 256, 512, 1024, 2048, or 4096 (cap at that many pixels), or Custom (a size you set).
USDZ Custom Downscale Size — the pixel size for Custom downsampling.

Accessibility:
Label — the accessibility label for the exported stage's default prim.
Description — the accessibility description for the exported stage's default prim.
See USD UI Accessibility for more.

Experimental:
Instancing — an experimental option. Unchecked, duplicated objects export as real objects, so a 100-particle system drawn with 100 meshes yields 100 individual meshes in the file; checked, duplicated objects export as a reference to the original, and if the original isn't part of the export, the first duplicate exports as a real object and serves as the reference.

Exporter Limitations:
Single-sided and Double-sided Meshes — USD appears to handle neither per-material nor per-face-group double-sidedness, so Blender takes the flag from the first material to mark the whole mesh single- or double-sided; with no material it defaults to double-sided.

Materials — with several materials, the mesh faces are stored as geometry subsets and each material is assigned to its subset; with only one material this is skipped. Note that the geometry subsets aren't time-sampled, so things may break if an animated mesh changes topology.
Hair — only the parent strands export, and only with a constant color: no UV coordinates and no normal information.
Camera — only perspective cameras export.
Particles — particles are written only while alive, meaning they're always visible; there's currently no code to mark them invisible outside their lifespan. Objects instanced by a particle system export with the object name suffixed by the particle's persistent ID, so every particle transform gets a unique name.
Geometry Node Modifiers — with Geometry Nodes, the node graph has to emit only the geometry components that match the original object type — to export a Mesh that uses a geometry-nodes modifier correctly, the modifier's output must hold only Mesh data, a Curves object only Curves data, and so on; any non-matching component yields a wrong export. The Separate Components Node is one way to make sure only the components you want export.
Instancing/Referencing — exporting instanced objects and collections is supported via an experimental USD-export option. Point instances made with Geometry Nodes are partly supported and export using the UsdGeomPointInstancer prim type; simple instancing through the Object Info Node or Collection Info Node works, but trickier cases — excluded collections, nested collections, or collections inside different Scenes — may come out wrong, so consider the Realize Instances Node where instances export incorrectly. Scene instances, made by directly instancing collections or objects, are written to USD as references to the original; supported types are Mesh, Curves, and Point Clouds.
USDZ — owing to a current USD-library limit, UDIM textures can't be included in the USDZ archive; this will likely be fixed in a future USD version (see USD pull request #2133).

USD Primvar data types — Blender handles a portion of the USD basic data types when importing and exporting; only those its attribute system natively understands are processed.
- Boolean — bool.
- 8-Bit Integer — uchar. USD's unsigned 8-bit value is cast to signed on import, and the signed value cast to unsigned on export.
- Integer — int. A 32-bit signed integer.
- Float — float. A 32-bit, single-precision float.
- Vector — float3. A 3D vector of 32-bit floats.
- 2D Vector — float2/texCoord2f. A 2D vector of 32-bit floats.
- Color — color4f. An RGBA color of 32-bit floats; as a special case, a Primvar or attribute for USD's displayColor reads or writes as color3f with an Alpha of 1.0.
- Byte Color — color4f. USD has no byte-color equivalent, so byte values convert to float and export as color4f.
- Quaternion — quatf. A floating-point Quaternion rotation.
Implementation Caveats — Blender doesn't support USD Primvars in 64-bit integers (int64), unsigned types (uint), or 64-bit double-precision or 16-bit half-precision floats; that rules out, for example, matrix4d (a 4×4 matrix of doubles) and quath (a half-precision quaternion). Note: the USD float4 type has no direct Blender equivalent and won't be read as a Blender Color or Quaternion.

USD UI Accessibility — Blender can author and load the UsdUIAccessibilityAPI schema on every supported data-block type that allows Custom Properties; the API records accessibility information for a USD primitive that a runtime's accessibility frameworks may surface, if present. Besides the root-prim accessibility export option above, you can set per-object accessibility info like so:
- Add these String Properties to the object data-block:
- Required: accessibility:<namespace>:label and accessibility:<namespace>:description.
- Optional: accessibility:<namespace>:priority.
The <namespace> may be any valid USD primvar identifier, including default, which is the recommended convention; priority may be low, standard, or high. It's well worth filling in the accessibility fields on the root prim for any long-lived USD document that may reach a wide range of software and people — when uploading to an asset marketplace, say. Implementation Caveats: Blender doesn't support time-varying accessibility schemas, since custom String properties can't be animated.

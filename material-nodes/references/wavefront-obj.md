# Wavefront Obj

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Reference — Menu: File ‣ Import/Export ‣ Wavefront (.obj).

OBJ is a popular plain-text format, but it offers only basic geometry and material support. Note: armatures, lights, cameras, empty objects, parenting, and transformations all go unsupported; see Compatibility for more.

Importing — brings geometry and curves in from the OBJ format; if there's a matching .MTL for the OBJ, its materials come in too.
General — Scale: how much to scale the imported objects about the world's origin.
Clamp Bounding Box — OBJ-files vary hugely in scale, so this caps the imported file at a fixed size.
Forward Axis, Up Axis — since many apps treat a different axis as "Up", these remap the Forward and Up axes so you can convert rotations between another app's default up/forward and Blender's. Blender itself uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up, for example, needs -Z Forward, Y Up.
Options:
Split By Object — brings in each OBJ "object name" group (o) as its own object.
Split By Group — brings in each OBJ group (g) as its own object.
Vertex Groups — imports OBJ groups as vertex groups.
Validate Meshes — checks the imported mesh for corrupt data and repairs it if needed; with it off, bad data may crash display or editing. It slows importing but is recommended, since data errors aren't always obvious.
Detect Cyclic Curves — joins curve endpoints where overlapping control points are found (off, no curve is cyclic).
Path Separator — the character that splits an object's name into a hierarchy via Collections.
Materials — Material Name Collision: what to do when an imported material's name clashes with an existing one. Make Unique (bring each material in as its own Blender material) or Reference Existing (if a material of that name already exists, point at it rather than importing).

Exporting — writes geometry and curves to the OBJ format.
General — Include: Selected Only: export only the selected objects; otherwise all objects in the scene.
Scale — the global scale to use on export.
Forward Axis, Up Axis — as on import: since many apps treat a different axis as "Up", these remap the Forward and Up axes to convert rotations between another app's default up/forward and Blender's. Blender itself uses Y Forward, Z Up (its front view looks along +Y); an app that uses Y as up needs -Z Forward, Y Up.
Geometry Properties:
UV Coordinates — writes out the active UV layer's coordinates from Blender.
Normals — writes out Blender's face and vertex normals (per the faces' smooth setting); usually unneeded since most apps compute their own, but required to match Blender's normal-map textures.
Colors — writes out the active vertex-color attribute layer, if present, in OBJ's "xyzrgb" extension format.
Curves as NURBS — writes NURBS curves out as OBJ NURBS rather than converting them to geometry.
Triangulated Mesh — writes quads as two triangles, for programs with only basic OBJ (triangle-only) support.
Apply Modifiers — exports objects as their evaluated mesh, i.e. the mesh that results once every Modifier has been computed.
Apply Transform — bakes an object's Location, Rotation, and Scale into the mesh before export, so vertices are written in world space; off, vertices export in local object space with no transforms applied. See Transforms for more.
Properties — for properties with separate viewport/final-render settings, pick which feeds the output; the Subdivision Surface Modifier is one case where it matters. Viewport (use viewport properties) or Render (use final-render properties).
Grouping:
Object Groups — writes each Blender object as an OBJ object.
Note: to Blender there's no difference between OBJ Groups and Objects; this option only exists for apps that treat them differently.
Material Groups — makes an OBJ group for each part of a geometry that uses a different material.
Vertex Groups — exports a face's vertex-group name, approximated by the vertex group with the most members among the face's vertices.
Smooth Groups — writes Blender's sharp edges as smooth groups.
Smooth Group Bitflags — generates bitflags for smooth Groups.
Materials — writes the MTL-file alongside the OBJ; most OBJ-capable importers also read the MTL-file.
PBR Extensions — exports the MTL library with PBR extensions (roughness, metallic, sheen, clearcoat, anisotropy, transmission).
Path Mode — controls how referenced paths are written, since absolute paths may only be right on your own system while relative ones are more portable but need files kept grouped; in some cases the path doesn't matter because the target app searches preset paths, so you can also strip it. Auto (relative for files in a subdirectory of the export location, absolute for anything outside), Absolute (full paths), Relative (always relative, except across drives on Windows), Match (relative/absolute to match the paths used in Blender), Strip Path (write only the filename, no path), or Copy (copy the file on export and reference it relatively).
Animation — exports a numbered OBJ for each frame from start to end; note this can take quite a while.

Frame Start, End — the first and last frame to export, which bounds the exported range.

Compatibility — at export time, NURBS surfaces, text3D, and metaballs all become meshes.

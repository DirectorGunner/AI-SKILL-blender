# Import Scene Operators, Material Operators

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Import Scene Operators; Material Operators.

## Import Scene Operators

### Import Scene Operators

bpy.ops.import_scene. fbx ( * , filepath = '' , directory = '' , filter_glob = '*.fbx' , files = None , ui_tab = 'MAIN' , use_manual_orientation = False , global_scale = 1.0 , bake_space_transform = False , use_custom_normals = True , colors_type = 'SRGB' , use_image_search = True , use_alpha_decals = False , decal_offset = 0.0 , use_anim = True , anim_offset = 1.0 , use_subsurf = False , use_custom_props = True , use_custom_props_enum_as_string = True , ignore_leaf_bones = False , force_connect_children = False , automatic_bone_orientation = False , primary_bone_axis = 'Y' , secondary_bone_axis = 'X' , use_prepost_rot = True , mtl_name_collision_mode = '`MAKE_UNIQUE`' , axis_forward = '-Z' , axis_up = 'Y' )

Load a FBX file

Parameters :

- filepath ( str ) – File Path, Filepath used for importing the file (optional, never None)

- directory ( str ) – directory, (optional, never None)

- filter_glob ( str ) – filter_glob, (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – File Path, (optional)

- ui_tab ( Literal [ 'MAIN' , 'ARMATURE' ] ) – ui_tab, Categories of import options (optional)

- MAIN
Main – Main basic settings.

- ARMATURE
Armatures – Armature-related settings.

- use_manual_orientation ( bool ) – Manual Orientation, Set orientation and scale yourself rather than relying on the data embedded in the FBX file (optional)

- global_scale ( float ) – Scale, (in [0.001, 1000], optional)

- bake_space_transform ( bool ) – Apply Transform, Bake the space transform into the object data, which avoids unwanted rotations when the target space is not aligned with Blender's space (WARNING! experimental option, use at own risk, known to be broken with armatures/animations) (optional)

- use_custom_normals ( bool ) – Custom Normals, Bring in custom normals when present (otherwise Blender recomputes them) (optional)

- colors_type ( Literal [ 'NONE' , 'SRGB' , 'LINEAR' ] ) – Vertex Colors, Bring in vertex color attributes (optional)

- NONE
None – Skip importing color attributes.

- SRGB
sRGB – Treat the file's colors as sRGB.

- LINEAR
Linear – Treat the file's colors as linear.

- use_image_search ( bool ) – Image Search, Look through subdirectories for related images (WARNING: may be slow) (optional)

- use_alpha_decals ( bool ) – Alpha Decals, Handle materials with alpha as decals that cast no shadows (optional)

- decal_offset ( float ) – Decal Offset, Push the geometry of alpha meshes outward (in [0, 1], optional)

- use_anim ( bool ) – Import Animation, Bring in the FBX animation (optional)

- anim_offset ( float ) – Animation Offset, Frame offset applied to the animation as it imports (in [-inf, inf], optional)

- use_subsurf ( bool ) – Subdivision Data, Turn FBX subdivision information into subdivision surface modifiers (optional)

- use_custom_props ( bool ) – Custom Properties, Bring in user properties as custom properties (optional)

- use_custom_props_enum_as_string ( bool ) – Import Enums As Strings, Keep enumeration values as strings (optional)

- ignore_leaf_bones ( bool ) – Ignore Leaf Bones, Skip the final bone of each chain (used only to mark the previous bone's length) (optional)

- force_connect_children ( bool ) – Force Connect Children, Connect child bones to their parent even when the computed head/tail positions disagree (handy for pure-joint armatures) (optional)

- automatic_bone_orientation ( bool ) – Automatic Bone Orientation, Try to point each bone's major axis toward its children (optional)

- primary_bone_axis ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Primary Bone Axis, (optional)

- secondary_bone_axis ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Secondary Bone Axis, (optional)

- use_prepost_rot ( bool ) – Use Pre/Post Rotation, Apply pre/post rotation from the FBX transform (you may need to turn this off in some cases) (optional)

- mtl_name_collision_mode ( Literal [ '`MAKE_UNIQUE`' , '`REFERENCE_EXISTING`' ] ) – Material Name Collision, What to do when an imported material's name clashes with an existing one (optional)

- `MAKE_UNIQUE`
Make Unique – Bring in each FBX material as its own Blender material.

- `REFERENCE_EXISTING`
Reference Existing – When a material of the same name already exists, point at it instead of importing a copy.

- axis_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Forward, (optional)

- axis_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Up, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.import_scene. gltf ( * , filepath = '' , export_import_convert_lighting_mode = 'SPEC' , filter_glob = '*.glb;*.gltf' , directory = '' , files = None , loglevel = 0 , import_pack_images = True , merge_vertices = False , import_shading = 'NORMALS' , bone_heuristic = 'BLENDER' , disable_bone_shape = False , bone_shape_scale_factor = 1.0 , guess_original_bind_pose = True , import_webp_texture = False , import_unused_materials = False , import_select_created_objects = True , import_scene_extras = True , import_scene_as_collection = True , import_merge_material_slots = True )

Load a glTF 2.0 file

Parameters :

- filepath ( str ) – File Path, Filepath used for importing the file (optional, never None)

- export_import_convert_lighting_mode ( Literal [ 'SPEC' , 'COMPAT' , 'RAW' ] ) – Lighting Mode, Optional backwards compatibility for render engines that aren't standard. Affects lights (optional)

- SPEC
Standard – Physically-based glTF lighting units (cd, lx, nt).

- COMPAT
Unitless – Non-physical, unitless lighting. Handy when exposure controls are missing.

- RAW
Raw (Deprecated) – Blender lighting strengths with no conversion.

- filter_glob ( str ) – filter_glob, (optional, never None)

- directory ( str ) – directory, (optional, never None)

- files ( bpy_prop_collection [ OperatorFileListElement ]) – File Path, (optional)

- loglevel ( int ) – Log Level, Log Level (in [-inf, inf], optional)

- import_pack_images ( bool ) – Pack Images, Embed every image inside the .blend file (optional)

- merge_vertices ( bool ) – Merge Vertices, The glTF format stores discontinuous normals, UVs, and other vertex attributes as separate vertices, which is what typical graphics hardware needs for rendering. This option tries to fold co-located vertices back together where it can. It currently cannot merge vertices whose normals differ (optional)

- import_shading ( Literal [ 'NORMALS' , 'FLAT' , 'SMOOTH' ] ) – Shading, How normals are worked out during import (optional)

- bone_heuristic ( Literal [ 'BLENDER' , 'TEMPERANCE' , 'FORTUNE' ] ) – Bone Dir, Strategy for laying out bones. Aims to keep them tidy (optional)

- BLENDER
Blender (best for import/export round trip) – Best when re-importing glTFs that Blender exported, and when re-exporting them to glTF after editing in Blender. Bone tips sit on their local +Y axis (in glTF space).

- TEMPERANCE
Temperance (average) – A solid general-purpose choice. A bone with a single child gets its tip placed on the local axis nearest that child.

- FORTUNE
Fortune (may look better, less accurate) – May look nicer than Temperance but can also be wrong. A bone with a single child gets its tip placed at that child's root. Watch out: non-uniform scaling can break with this option.

- disable_bone_shape ( bool ) – Disable Bone Shape, Skip creating bone shapes (optional)

- bone_shape_scale_factor ( float ) – Bone Shape Scale, Scale applied to bone shapes (in [-inf, inf], optional)

- guess_original_bind_pose ( bool ) – Guess Original Bind Pose, Attempt to recover the original bind pose of skinned meshes from their inverse bind matrices. When off, use the default/rest pose as the bind pose (optional)

- import_webp_texture ( bool ) – Import WebP Textures, When a WebP version of a texture exists, load it instead of the PNG/JPEG fallback (optional)

- import_unused_materials ( bool ) – Import Unused Materials & Images, Bring in materials and images even if no mesh uses them (optional)

- import_select_created_objects ( bool ) – Select Imported Objects, Select the created objects once the import finishes (optional)

- import_scene_extras ( bool ) – Import Scene Extras, Bring in scene extras as custom properties. Any existing custom properties get overwritten (optional)

- import_scene_as_collection ( bool ) – Import Scene as Collection, Bring the scene in as a collection (optional)

- import_merge_material_slots ( bool ) – Merge Material Slot when possible, Combine material slots wherever it can be done (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

## Material Operators

### Material Operators

bpy.ops.material. copy ( )

Copy the material settings and nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.material. new ( )

Add a new material

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.material. paste ( )

Paste the material settings and nodes

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

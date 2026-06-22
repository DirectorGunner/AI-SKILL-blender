# Export Scene Operators (part 1)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

### Export Scene Operators

**bpy.ops.export_scene.fbx**( * , filepath = '' , check_existing = True , filter_glob = '*.fbx' , use_selection = False , use_visible = False , use_active_collection = False , collection = '' , global_scale = 1.0 , apply_unit_scale = True , apply_scale_options = '`FBX_SCALE_NONE`' , use_space_transform = True , bake_space_transform = False , object_types = {'ARMATURE', 'CAMERA', 'EMPTY', 'LIGHT', 'MESH', 'OTHER'} , use_mesh_modifiers = True , use_mesh_modifiers_render = True , mesh_smooth_type = 'OFF' , colors_type = 'SRGB' , prioritize_active_color = False , use_subsurf = False , use_mesh_edges = False , use_tspace = False , use_triangles = False , use_custom_props = False , add_leaf_bones = True , primary_bone_axis = 'Y' , secondary_bone_axis = 'X' , use_armature_deform_only = False , armature_nodetype = 'NULL' , bake_anim = True , bake_anim_use_all_bones = True , bake_anim_use_nla_strips = True , bake_anim_use_all_actions = True , bake_anim_force_startend_keying = True , bake_anim_step = 1.0 , bake_anim_simplify_factor = 1.0 , path_mode = 'AUTO' , embed_textures = False , batch_mode = 'OFF' , use_batch_own_dir = True , use_metadata = True , axis_forward = '-Z' , axis_up = 'Y' )

Save scene as FBX file.

Parameters:
- filepath ( str ) – File Path, Filepath used for exporting the file (optional, never None)
- check_existing ( bool ) – Check Existing, Check and warn on overwriting existing files (optional)
- filter_glob ( str ) – filter_glob, (optional, never None)
- use_selection ( bool ) – Selected Objects, Only export chosen and visible objects (optional)
- use_visible ( bool ) – Visible Objects, Only export objects you can see (optional)
- use_active_collection ( bool ) – Active Collection, Only export objects from the active collection (and its children) (optional)
- collection ( str ) – Source Collection, Only export objects from this collection (and its children) (optional, never None)
- global_scale ( float ) – Scale, Resize all geometry (Note: Some importers do not support scaled armatures!) (in [0.001, 1000], optional)
- apply_unit_scale ( bool ) – Apply Unit, Account for Blender's native units (if off, raw Blender units are preserved) (optional)
- apply_scale_options ( Literal [ '`FBX_SCALE_NONE`' , '`FBX_SCALE_UNITS`' , '`FBX_SCALE_CUSTOM`' , '`FBX_SCALE_ALL`' ] ) – Apply Scalings, How to apply custom and units scalings in generated FBX file (Blender uses FBX scale to detect units on import, but many other applications do not handle the same way) (optional)

- `FBX_SCALE_NONE`
All Local – Apply custom scaling and units scaling to each object transformation, FBX scale remains at 1.0.

- `FBX_SCALE_UNITS`
FBX Units Scale – Apply custom scaling to each object transformation, and units scaling to FBX scale.

- `FBX_SCALE_CUSTOM`
FBX Custom Scale – Apply custom scaling to FBX scale, and units scaling to each object transformation.

- `FBX_SCALE_ALL`
FBX All – Apply custom scaling and units scaling to FBX scale.

- use_space_transform ( bool ) – Use Space Transform, Apply global space transform to the object rotations. When disabled only the axis space is written to the file and all object transforms are left as-is (optional)
- bake_space_transform ( bool ) – Apply Transform, Bake space transform into object data, avoids getting unwanted rotations to objects when target space is not aligned with Blender's space (WARNING! experimental option, use at own risk, known to be broken with armatures/animations) (optional)
- object_types ( set [ Literal [ 'EMPTY' , 'CAMERA' , 'LIGHT' , 'ARMATURE' , 'MESH' , 'OTHER' ] ] ) – Object Types, Which kind of object to export (optional)

- EMPTY
Empty.

- CAMERA
Camera.

- LIGHT
Lamp.

- ARMATURE
Armature – WARNING: not supported in dupli/group instances.

- MESH
Mesh.

- OTHER
Other – Other geometry types, like curve, meta-ball, etc. (converted to meshes).

- use_mesh_modifiers ( bool ) – Apply Modifiers, Apply modifiers to mesh objects (except Armature ones) - WARNING: prevents exporting shape keys (optional)
- use_mesh_modifiers_render ( bool ) – Use Modifiers Render Setting, Use render settings when applying modifiers to mesh objects (DISABLED in Blender 2.8) (optional)
- mesh_smooth_type ( Literal [ 'OFF' , 'FACE' , 'EDGE' , '`SMOOTH_GROUP`' ] ) – Smoothing, Export smoothing information (prefer 'Normals Only' option if your target importer understands custom normals) (optional)

- OFF
Normals Only – Export only normals instead of writing edge or face smoothing data.

- FACE
Face – Write face smoothing.

- EDGE
Edge – Write edge smoothing.

- `SMOOTH_GROUP`
Smoothing Groups – Write face smoothing groups.

- colors_type ( Literal [ 'NONE' , 'SRGB' , 'LINEAR' ] ) – Vertex Colors, Export vertex color attributes (optional)

- NONE
None – Do not export color attributes.

- SRGB
sRGB – Export colors in sRGB color space.

- LINEAR
Linear – Export colors in linear color space.

- prioritize_active_color ( bool ) – Prioritize Active Color, Make sure active color will be exported first. Could be important since some other software can discard other color attributes besides the first one (optional)
- use_subsurf ( bool ) – Export Subdivision Surface, Export the last Catmull-Rom subdivision modifier as FBX subdivision (does not apply the modifier even if 'Apply Modifiers' is enabled) (optional)
- use_mesh_edges ( bool ) – Loose Edges, Export loose edges (as two-vertices polygons) (optional)
- use_tspace ( bool ) – Tangent Space, Add binormal and tangent vectors, together with normal they form the tangent space (will only work correctly with tris/quads only meshes!) (optional)
- use_triangles ( bool ) – Triangulate Faces, Convert all faces to triangles (optional)
- use_custom_props ( bool ) – Custom Properties, Export custom properties (optional)
- add_leaf_bones ( bool ) – Add Leaf Bones, Append a final bone to the end of each chain to specify last bone length (use this when you intend to edit the armature from exported data) (optional)
- primary_bone_axis ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Primary Bone Axis, (optional)
- secondary_bone_axis ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Secondary Bone Axis, (optional)
- use_armature_deform_only ( bool ) – Only Deform Bones, Only write deforming bones (and non-deforming ones when they have deforming children) (optional)

- armature_nodetype ( Literal [ 'NULL' , 'ROOT' , 'LIMBNODE' ] ) – Armature FBXNode Type, FBX type of node (object) used to represent Blender's armatures (use the Null type unless you experience issues with the other app, as other choices may not import back perfectly into Blender…) (optional)

- NULL
Null – 'Null' FBX node, similar to Blender's Empty (default).

- ROOT
Root – 'Root' FBX node, supposed to be the root of chains of bones….

- LIMBNODE
LimbNode – 'LimbNode' FBX node, a regular joint between two bones….

- bake_anim ( bool ) – Baked Animation, Export baked keyframe animation (optional)
- bake_anim_use_all_bones ( bool ) – Key All Bones, Force exporting at least one key of animation for all bones (needed with some target applications, like UE4) (optional)
- bake_anim_use_nla_strips ( bool ) – NLA Strips, Export each non-muted NLA strip as a separated FBX's AnimStack, if any, instead of global scene animation (optional)
- bake_anim_use_all_actions ( bool ) – All Actions, Export each action as a separated FBX's AnimStack, instead of global scene animation (note that animated objects will get all actions compatible with them, others will get no animation at all) (optional)
- bake_anim_force_startend_keying ( bool ) – Force Start/End Keying, Always add a keyframe at start and end of actions for animated channels (optional)
- bake_anim_step ( float ) – Sampling Rate, How often to evaluate animated values (in frames) (in [0.01, 100], optional)
- bake_anim_simplify_factor ( float ) – Simplify, How much to simplify baked values (0.0 to disable, the higher the more simplified) (in [0, 100], optional)
- path_mode ( Literal [ 'AUTO' , 'ABSOLUTE' , 'RELATIVE' , 'MATCH' , 'STRIP' , 'COPY' ] ) – Path Mode, Method used to reference paths (optional)

- AUTO
Auto – Use relative paths with subdirectories only.

- ABSOLUTE
Absolute – Always write absolute paths.

- RELATIVE
Relative – Write relative paths where possible.

- MATCH
Match – Match absolute/relative setting with input path.

- STRIP
Strip – Filename only.

- COPY
Copy – Copy the file to the destination path (or subdirectory).

- embed_textures ( bool ) – Embed Textures, Embed textures in FBX binary file (only for "Copy" path mode!) (optional)
- batch_mode ( Literal [ 'OFF' , 'SCENE' , 'COLLECTION' , '`SCENE_COLLECTION`' , '`ACTIVE_SCENE_COLLECTION`' ] ) – Batch Mode, (optional)

- OFF
Off – Active scene to file.

- SCENE
Scene – Each scene as a file.

- COLLECTION
Collection – Each collection (data-block ones) as a file, does not include content of children collections.

- `SCENE_COLLECTION`
Scene Collections – Each collection (including master, non-data-block ones) of each scene as a file, including content from children collections.

- `ACTIVE_SCENE_COLLECTION`
Active Scene Collections – Each collection (including master, non-data-block one) of the active scene as a file, including content from children collections.

- use_batch_own_dir ( bool ) – Batch Own Dir, Create a dir for each exported file (optional)
- use_metadata ( bool ) – Use Metadata, (optional)
- axis_forward ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Forward, (optional)
- axis_up ( Literal [ 'X' , 'Y' , 'Z' , '-X' , '-Y' , '-Z' ] ) – Up, (optional)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/io_scene_fbx/__init__.py:604

**bpy.ops.export_scene.gltf**( * , filepath = '' , check_existing = True , export_import_convert_lighting_mode = 'SPEC' , gltf_export_id = '' , export_use_gltfpack = False , export_gltfpack_tc = True , export_gltfpack_tq = 8 , export_gltfpack_si = 1.0 , export_gltfpack_sa = False , export_gltfpack_slb = False , export_gltfpack_vp = 14 , export_gltfpack_vt = 12 , export_gltfpack_vn = 8 , export_gltfpack_vc = 8 , export_gltfpack_vpi = 'Integer' , export_gltfpack_noq = True , export_gltfpack_kn = False , export_format = '' , ui_tab = 'GENERAL' , export_copyright = '' , export_image_format = 'AUTO' , export_image_add_webp = False , export_image_webp_fallback = False , export_texture_dir = '' , export_jpeg_quality = 75 , export_image_quality = 75 , export_keep_originals = False , export_texcoords = True , export_normals = True , export_gn_mesh = False , export_draco_mesh_compression_enable = False , export_draco_mesh_compression_level = 6 , export_draco_position_quantization = 14 , export_draco_normal_quantization = 10 , export_draco_texcoord_quantization = 12 , export_draco_color_quantization = 10 , export_draco_generic_quantization = 12 , export_tangents = False , export_materials = 'EXPORT' , export_unused_images = False , export_unused_textures = False , export_vertex_color = 'MATERIAL' , export_vertex_color_name = 'Color' , export_all_vertex_colors = True , export_active_vertex_color_when_no_material = True , export_attributes = False , use_mesh_edges = False , use_mesh_vertices = False , export_cameras = False , use_selection = False , use_visible = False , use_renderable = False , use_active_collection_with_nested = True , use_active_collection = False , use_active_scene = False , collection = '' , at_collection_center = False , export_extras = False , export_yup = True , export_apply = False , export_shared_accessors = False , export_animations = True , export_frame_range = False , export_frame_step = 1 , export_force_sampling = True , export_sampling_interpolation_fallback = 'LINEAR' , export_pointer_animation = False , export_animation_mode = 'ACTIONS' , export_nla_strips_merged_animation_name = 'Animation' , export_def_bones = False , export_hierarchy_flatten_bones = False , export_hierarchy_flatten_objs = False , export_armature_object_remove = False , export_leaf_bone = False , export_optimize_animation_size = True , export_optimize_animation_keep_anim_armature = True , export_optimize_animation_keep_anim_object = False , export_optimize_disable_viewport = False , export_negative_frame = 'SLIDE' , export_anim_slide_to_zero = False , export_bake_animation = False , export_merge_animation = 'ACTION' , export_anim_single_armature = True , export_reset_pose_bones = True , export_current_frame = False , export_rest_position_armature = True , export_anim_scene_split_object = True , export_skins = True , export_influence_nb = 4 , export_all_influences = False , export_morph = True , export_morph_normal = True , export_morph_tangent = False , export_morph_animation = True , export_morph_reset_sk_data = True , export_lights = False , export_try_sparse_sk = True , export_try_omit_sparse_sk = False , export_gpu_instances = False , export_action_filter = False , export_convert_animation_pointer = False , export_nla_strips = True , export_original_specular = False , will_save_settings = False , export_hierarchy_full_collections = False , export_extra_animations = False , export_loglevel = -1 , filter_glob = '*.glb' )

Save scene as glTF 2.0 file.

Parameters:
- filepath ( str ) – File Path, Filepath used for exporting the file (optional, never None)

- check_existing ( bool ) – Check Existing, Check and warn on overwriting existing files (optional)
- export_import_convert_lighting_mode ( Literal [ 'SPEC' , 'COMPAT' , 'RAW' ] ) – Lighting Mode, Optional backwards compatibility for non-standard render engines. Applies to lights (optional)

- SPEC
Standard – Physically-based glTF lighting units (cd, lx, nt).

- COMPAT
Unitless – Non-physical, unitless lighting. Useful when exposure controls are not available.

- RAW
Raw (Deprecated) – Blender lighting strengths with no conversion.

- gltf_export_id ( str ) – Identifier, Identifier of caller (in case of add-on calling this exporter). Can be useful in case of Extension added by other add-ons (optional, never None)
- export_use_gltfpack ( bool ) – Use Gltfpack, Use gltfpack to simplify the mesh and/or compress its textures (optional)
- export_gltfpack_tc ( bool ) – KTX2 Compression, Convert all textures to KTX2 with BasisU supercompression (optional)
- export_gltfpack_tq ( int ) – Texture Encoding Quality, Texture encoding quality (in [1, 10], optional)
- export_gltfpack_si ( float ) – Mesh Simplification Ratio, Simplify meshes targeting triangle count ratio (in [0, 1], optional)
- export_gltfpack_sa ( bool ) – Aggressive Mesh Simplification, Aggressively simplify to the target ratio disregarding quality (optional)
- export_gltfpack_slb ( bool ) – Lock Mesh Border Vertices, Lock border vertices during simplification to avoid gaps on connected meshes (optional)
- export_gltfpack_vp ( int ) – Position Quantization, Use N-bit quantization for positions (in [1, 16], optional)
- export_gltfpack_vt ( int ) – Texture Coordinate Quantization, Use N-bit quantization for texture coordinates (in [1, 16], optional)
- export_gltfpack_vn ( int ) – Normal/Tangent Quantization, Use N-bit quantization for normals and tangents (in [1, 16], optional)
- export_gltfpack_vc ( int ) – Vertex Color Quantization, Use N-bit quantization for colors (in [1, 16], optional)
- export_gltfpack_vpi ( Literal [ 'Integer' , 'Normalized' , 'Floating-point' ] ) – Vertex Position Attributes, Type to use for vertex position attributes (optional)

- Integer
Integer – Use integer attributes for positions.

- Normalized
Normalized – Use normalized attributes for positions.

- Floating-point
Floating-point – Use floating-point attributes for positions.

- export_gltfpack_noq ( bool ) – Disable Quantization, Disable quantization; produces much larger glTF files with no extensions (optional)
- export_gltfpack_kn ( bool ) – Keep Named Nodes, Restrict some optimization to keep named nodes and meshes attached to named nodes so that named nodes can be transformed externally (optional)
- export_format ( str ) – Format, Output format. Binary is most efficient, but JSON may be easier to edit later (optional)
- ui_tab ( Literal [ 'GENERAL' , 'MESHES' , 'OBJECTS' , 'ANIMATION' ] ) – ui_tab, Export setting categories (optional)

- GENERAL
General – General settings.

- MESHES
Meshes – Mesh settings.

- OBJECTS
Objects – Object settings.

- ANIMATION
Animation – Animation settings.

- export_copyright ( str ) – Copyright, Legal rights and conditions for the model (optional, never None)
- export_image_format ( Literal [ 'AUTO' , 'JPEG' , 'WEBP' , 'NONE' ] ) – Images, Output format for images. PNG is lossless and generally preferred, but JPEG might be preferable for web applications due to the smaller file size. Alternatively they can be omitted if they are not needed (optional)

- AUTO
Automatic – Save PNGs as PNGs, JPEGs as JPEGs, WebPs as WebPs. For other formats, use PNG.

- JPEG
JPEG Format (.jpg) – Save images as JPEGs. (Images that need alpha are saved as PNGs though.) Be aware of a possible loss in quality.

- WEBP
WebP Format – Save images as WebPs as main image (no fallback).

- NONE
None – Don't export images.

- export_image_add_webp ( bool ) – Create WebP, Creates WebP textures for every texture. For already WebP textures, nothing happens (optional)
- export_image_webp_fallback ( bool ) – WebP Fallback, For all WebP textures, create a PNG fallback texture (optional)
- export_texture_dir ( str ) – Textures, Folder to place texture files in. Relative to the .gltf file (optional, never None)
- export_jpeg_quality ( int ) – JPEG Quality, Quality of JPEG export (in [0, 100], optional)
- export_image_quality ( int ) – Image Quality, Quality of image export (in [0, 100], optional)
- export_keep_originals ( bool ) – Keep Original, Keep original textures files if possible. WARNING: if you use more than one texture, where pbr standard requires only one, only one texture will be used. This can lead to unexpected results (optional)
- export_texcoords ( bool ) – UVs, Export UVs (texture coordinates) with meshes (optional)
- export_normals ( bool ) – Normals, Export vertex normals with meshes (optional)
- export_gn_mesh ( bool ) – Geometry Nodes Instances (Experimental), Export Geometry nodes instance meshes (optional)
- export_draco_mesh_compression_enable ( bool ) – Draco Mesh Compression, Compress mesh using Draco (optional)
- export_draco_mesh_compression_level ( int ) – Compression Level, Compression level (0 = most speed, 6 = most compression, higher values currently not supported) (in [0, 10], optional)
- export_draco_position_quantization ( int ) – Position Quantization Bits, Quantization bits for position values (0 = no quantization) (in [0, 30], optional)
- export_draco_normal_quantization ( int ) – Normal Quantization Bits, Quantization bits for normal values (0 = no quantization) (in [0, 30], optional)
- export_draco_texcoord_quantization ( int ) – Texcoord Quantization Bits, Quantization bits for texture coordinate values (0 = no quantization) (in [0, 30], optional)
- export_draco_color_quantization ( int ) – Color Quantization Bits, Quantization bits for color values (0 = no quantization) (in [0, 30], optional)
- export_draco_generic_quantization ( int ) – Generic Quantization Bits, Quantization bits for generic values like weights or joints (0 = no quantization) (in [0, 30], optional)
- export_tangents ( bool ) – Tangents, Export vertex tangents with meshes (optional)
- export_materials ( Literal [ 'EXPORT' , 'PLACEHOLDER' , 'VIEWPORT' , 'NONE' ] ) – Materials, Export materials (optional)

- EXPORT
Export – Export all materials used by included objects.

- PLACEHOLDER
Placeholder – Do not export materials, but write multiple primitive groups per mesh, keeping material slot information.

- VIEWPORT
Viewport – Export minimal materials as defined in Viewport display properties.

## See also

- [Scene Operators](scene-operators.md)

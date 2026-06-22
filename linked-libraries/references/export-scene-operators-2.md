# Export Scene Operators (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- NONE
No export – Do not export materials, and combine mesh primitive groups, losing material slot information.

- export_unused_images ( bool ) – Unused Images, Export images not assigned to any material (optional)
- export_unused_textures ( bool ) – Prepare Unused Textures, Export image texture nodes not assigned to any material. This feature is not standard and needs an external extension to be included in the glTF file (optional)
- export_vertex_color ( Literal [ 'MATERIAL' , 'ACTIVE' , 'NAME' , 'NONE' ] ) – Use Vertex Color, How to export vertex color (optional)

- MATERIAL
Material – Export vertex color when used by material.

- ACTIVE
Active – Export active vertex color.

- NAME
Name – Export vertex color with this name.

- NONE
None – Do not export vertex color.

- export_vertex_color_name ( str ) – Vertex Color Name, Name of vertex color to export (optional, never None)
- export_all_vertex_colors ( bool ) – Export All Vertex Colors, Export all vertex colors, even if not used by any material. If no Vertex Color is used in the mesh materials, a fake `COLOR_0` will be created, in order to keep material unchanged (optional)
- export_active_vertex_color_when_no_material ( bool ) – Export Active Vertex Color When No Material, When there is no material on object, export active vertex color (optional)
- export_attributes ( bool ) – Attributes, Export Attributes (when starting with underscore) (optional)
- use_mesh_edges ( bool ) – Loose Edges, Export loose edges as lines, using the material from the first material slot (optional)
- use_mesh_vertices ( bool ) – Loose Points, Export loose points as glTF points, using the material from the first material slot (optional)
- export_cameras ( bool ) – Cameras, Export cameras (optional)
- use_selection ( bool ) – Selected Objects, Export selected objects only (optional)
- use_visible ( bool ) – Visible Objects, Export visible objects only (optional)
- use_renderable ( bool ) – Renderable Objects, Export renderable objects only (optional)
- use_active_collection_with_nested ( bool ) – Include Nested Collections, Include active collection and nested collections (optional)
- use_active_collection ( bool ) – Active Collection, Export objects in the active collection only (optional)
- use_active_scene ( bool ) – Active Scene, Export active scene only (optional)
- collection ( str ) – Source Collection, Export only objects from this collection (and its children) (optional, never None)
- at_collection_center ( bool ) – Export at Collection Center, Export at Collection center of mass of root objects of the collection (optional)
- export_extras ( bool ) – Custom Properties, Export custom properties as glTF extras (optional)
- export_yup ( bool ) – +Y Up, Export using glTF convention, +Y up (optional)
- export_apply ( bool ) – Apply Modifiers, Apply modifiers (excluding Armatures) to mesh objects -WARNING: prevents exporting shape keys (optional)
- export_shared_accessors ( bool ) – Shared Accessors, Export Primitives using shared accessors for attributes (optional)
- export_animations ( bool ) – Animations, Exports active actions and NLA tracks as glTF animations (optional)
- export_frame_range ( bool ) – Limit to Playback Range, Clips animations to selected playback range (optional)
- export_frame_step ( int ) – Sampling Rate, How often to evaluate animated values (in frames) (in [1, 120], optional)
- export_force_sampling ( bool ) – Always Sample Animations, Apply sampling to all animations (optional)
- export_sampling_interpolation_fallback ( Literal [ 'LINEAR' , 'STEP' ] ) – Sampling Interpolation Fallback, Interpolation fallback for sampled animations, when the property is not keyed (optional)

- LINEAR
Linear – Linear interpolation between keyframes.

- STEP
Step – No interpolation between keyframes.

- export_pointer_animation ( bool ) – Export Animation Pointer (Experimental), Export material, Light & Camera animation as Animation Pointer. Available only for baked animation mode 'NLA Tracks' and 'Scene' (optional)
- export_animation_mode ( Literal [ 'ACTIONS' , '`ACTIVE_ACTIONS`' , 'BROADCAST' , '`NLA_TRACKS`' , 'SCENE' ] ) – Animation Mode, Export Animation mode (optional)

- ACTIONS
Actions – Export actions (actives and on NLA tracks) as separate animations.

- `ACTIVE_ACTIONS`
Active actions merged – All the currently assigned actions become one glTF animation.

- BROADCAST
Broadcast actions – Broadcast all compatible actions to all objects. Animated objects will get all actions compatible with them, others will get no animation at all.

- `NLA_TRACKS`
NLA Tracks – Export individual NLA Tracks as separate animation.

- SCENE
Scene – Export baked scene as a single animation.

- export_nla_strips_merged_animation_name ( str ) – Merged Animation Name, Name of single glTF animation to be exported (optional, never None)
- export_def_bones ( bool ) – Export Deformation Bones Only, Export Deformation bones only (optional)
- export_hierarchy_flatten_bones ( bool ) – Flatten Bone Hierarchy, Flatten Bone Hierarchy. Useful in case of non decomposable transformation matrix (optional)
- export_hierarchy_flatten_objs ( bool ) – Flatten Object Hierarchy, Flatten Object Hierarchy. Useful in case of non decomposable transformation matrix (optional)
- export_armature_object_remove ( bool ) – Remove Armature Object, Remove Armature object if possible. If Armature has multiple root bones, object will not be removed (optional)
- export_leaf_bone ( bool ) – Add Leaf Bones, Append a final bone to the end of each chain to specify last bone length (use this when you intend to edit the armature from exported data) (optional)
- export_optimize_animation_size ( bool ) – Optimize Animation Size, Reduce exported file size by removing duplicate keyframes (optional)
- export_optimize_animation_keep_anim_armature ( bool ) – Force Keeping Channels for Bones, If all keyframes are identical in a rig, force keeping the minimal animation. When off, all possible channels for the bones will be exported, even if empty (minimal animation, 2 keyframes) (optional)
- export_optimize_animation_keep_anim_object ( bool ) – Force Keeping Channel for Objects, If all keyframes are identical for object transformations, force keeping the minimal animation (optional)
- export_optimize_disable_viewport ( bool ) – Disable Viewport for Other Objects, When exporting animations, disable viewport for other objects, for performance (optional)
- export_negative_frame ( Literal [ 'SLIDE' , 'CROP' ] ) – Negative Frames, Negative Frames are slid or cropped (optional)

- SLIDE
Slide – Slide animation to start at frame 0.

- CROP
Crop – Keep only frames above frame 0.

- export_anim_slide_to_zero ( bool ) – Set All glTF Animation Starting at 0, Set all glTF animation starting at 0.0s. Can be useful for looping animations (optional)
- export_bake_animation ( bool ) – Bake All Objects Animations, Force exporting animation on every object. Can be useful when using constraints or driver. Also useful when exporting only selection (optional)
- export_merge_animation ( Literal [ '`NLA_TRACK`' , 'ACTION' , 'NONE' ] ) – Merge Animation, Merge Animations (optional)

- `NLA_TRACK`
NLA Track Names – Merge by NLA Track Names.

- ACTION
Actions – Merge by Actions.

- NONE
No Merge – Do Not Merge Animations.

- export_anim_single_armature ( bool ) – Export all Armature Actions, Export all actions, bound to a single armature. WARNING: Option does not support exports including multiple armatures (optional)
- export_reset_pose_bones ( bool ) – Reset Pose Bones Between Actions, Reset pose bones between each action exported. This is needed when some bones are not keyed on some animations (optional)
- export_current_frame ( bool ) – Use Current Frame as Object Rest Transformations, Export the scene in the current animation frame. When off, frame 0 is used as rest transformations for objects (optional)
- export_rest_position_armature ( bool ) – Use Rest Position Armature, Export armatures using rest position as joints' rest pose. When off, current frame pose is used as rest pose (optional)
- export_anim_scene_split_object ( bool ) – Split Animation by Object, Export Scene as seen in Viewport, But split animation by Object (optional)
- export_skins ( bool ) – Skinning, Export skinning (armature) data (optional)
- export_influence_nb ( int ) – Bone Influences, Choose how many Bone influences to export (in [1, inf], optional)
- export_all_influences ( bool ) – Include All Bone Influences, Allow export of all joint vertex influences. Models may appear incorrectly in many viewers (optional)
- export_morph ( bool ) – Shape Keys, Export shape keys (morph targets) (optional)
- export_morph_normal ( bool ) – Shape Key Normals, Export vertex normals with shape keys (morph targets) (optional)
- export_morph_tangent ( bool ) – Shape Key Tangents, Export vertex tangents with shape keys (morph targets) (optional)
- export_morph_animation ( bool ) – Shape Key Animations, Export shape keys animations (morph targets) (optional)
- export_morph_reset_sk_data ( bool ) – Reset Shape Keys Between Actions, Reset shape keys between each action exported. This is needed when some SK channels are not keyed on some animations (optional)
- export_lights ( bool ) – Punctual Lights, Export directional, point, and spot lights. Uses "KHR_lights_punctual" glTF extension (optional)
- export_try_sparse_sk ( bool ) – Use Sparse Accessor if Better, Try using Sparse Accessor if it saves space (optional)
- export_try_omit_sparse_sk ( bool ) – Omitting Sparse Accessor if Data is Empty, Omitting Sparse Accessor if data is empty (optional)
- export_gpu_instances ( bool ) – GPU Instances, Export using EXT_mesh_gpu_instancing. Limited to children of a given Empty. Multiple materials might be omitted (optional)
- export_action_filter ( bool ) – Filter Actions, Filter Actions to be exported (optional)
- export_convert_animation_pointer ( bool ) – Convert TRS/Weights to Animation Pointer, Export TRS and weights as Animation Pointer. Using KHR_animation_pointer extension (optional)
- export_nla_strips ( bool ) – Group by NLA Track, When on, multiple actions become part of the same glTF animation if they're pushed onto NLA tracks with the same name. When off, all the currently assigned actions become one glTF animation (optional)
- export_original_specular ( bool ) – Export Original PBR Specular, Export original glTF PBR Specular, instead of Blender Principled Shader Specular (optional)
- will_save_settings ( bool ) – Remember Export Settings, Store glTF export settings in the Blender project (optional)
- export_hierarchy_full_collections ( bool ) – Full Collection Hierarchy, Export full hierarchy, including intermediate collections (optional)
- export_extra_animations ( bool ) – Prepare Extra Animations, Export additional animations.This feature is not standard and needs an external extension to be included in the glTF file(optional)
- export_loglevel ( int ) – Log Level, Log Level (in [-inf, inf], optional)
- filter_glob ( str ) – filter_glob, (optional, never None)

Returns: Result of the operator call.
Return type: set[Literal[Operator Return Items]]

File: addons_core/io_scene_gltf2/__init__.py:1085

## See also

- [Scene Operators](scene-operators.md)

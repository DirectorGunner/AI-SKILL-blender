# Object Id (part 2)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- WORLD
World Space – Blender's outermost, most global space.

- POSE
Pose Space – A bone's pose space, equivalent to its armature's object space.

- `LOCAL_WITH_PARENT`
Local With Parent – A bone's rest-pose local space, carrying parent transforms within the matrix.

- LOCAL
Local Space – The local space belonging to an object or bone.

- to_space ( Literal [ 'WORLD' , 'POSE' , '`LOCAL_WITH_PARENT`' , 'LOCAL' ] ) – The space to which you want to transform ‘matrix’ (optional)

- WORLD
World Space – Blender's outermost, most global space.

- POSE
Pose Space – A bone's pose space, equivalent to its armature's object space.

- `LOCAL_WITH_PARENT`
Local With Parent – A bone's rest-pose local space, carrying parent transforms within the matrix.

- LOCAL
Local Space – The local space belonging to an object or bone.

Returns :

The transformed matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type :

mathutils.Matrix

calc_matrix_camera ( depsgraph , * , x = 1 , y = 1 , scale_x = 1.0 , scale_y = 1.0 ) 

Build this object's camera projection matrix (chiefly handy for Camera and Light types)

Parameters :

- depsgraph (Depsgraph) – Depsgraph to get evaluated data from

- x ( int ) – Width of the render area (in [0, inf], optional)

- y ( int ) – Height of the render area (in [0, inf], optional)

- scale_x ( float ) – Width scaling factor (in [1e-06, inf], optional)

- scale_y ( float ) – Height scaling factor (in [1e-06, inf], optional)

Returns :

The camera projection matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

Return type :

mathutils.Matrix

camera_fit_coords ( depsgraph , coordinates ) 

Work out where (and, for ortho cameras, at what scale) the object must sit to bring all the supplied coordinates into view

Parameters :

- depsgraph (Depsgraph) – Depsgraph to get evaluated data from

- coordinates ( Sequence [ float ] ) – Coordinates to fit in (array of 1 items, in [-inf, inf], never None)

Returns :

co_return , The location to aim to be able to see all given points, mathutils.Vector

scale_return , The ortho scale to aim to be able to see all given points (if relevant), float

Return type :

tuple[mathutils.Vector, float]

crazyspace_eval ( depsgraph , scene ) 

Build the orientation mapping between the vertices of the original object and those of the object once shape keys and deforming modifiers are applied. Release the evaluation afterward with crazyspace_eval_free.

Parameters :

- depsgraph (Depsgraph) – Dependency Graph, Evaluated dependency graph

- scene (Scene) – Scene, Scene of the object

crazyspace_displacement_to_deformed ( * , vertex_index = 0 , displacement = (0.0, 0.0, 0.0) ) 

Map a displacement vector out of non-deformed object space and into deformed object space

Parameters :

- vertex_index ( int ) – vertex_index, (in [-inf, inf], optional)

- displacement (mathutils.Vector) – displacement, (array of 3 items, in [-inf, inf], optional)

Returns :

displacement_deformed, (array of 3 items, in [-inf, inf])

Return type :

mathutils.Vector

crazyspace_displacement_to_original ( * , vertex_index = 0 , displacement = (0.0, 0.0, 0.0) ) 

Discard the crazyspace evaluated state

Parameters :

- vertex_index ( int ) – vertex_index, (in [-inf, inf], optional)

- displacement (mathutils.Vector) – displacement, (array of 3 items, in [-inf, inf], optional)

Returns :

displacement_original, (array of 3 items, in [-inf, inf])

Return type :

mathutils.Vector

crazyspace_eval_clear ( ) 

crazyspace_eval_clear

to_mesh ( * , preserve_all_data_layers = False , depsgraph = None ) 

Build a Mesh data-block from the object's present state. The data-block stays owned by the object; call to_mesh_clear() to free it manually. What you get is temporary and may not be attached to objects in the main database.

Parameters :

- preserve_all_data_layers ( bool ) – Preserve all data layers in the mesh, like UV maps and vertex groups. By default Blender only computes the subset of data layers needed for viewport display and rendering, for better performance. (optional)

- depsgraph (Depsgraph) – Dependency Graph, Evaluated dependency graph which is required when preserve_all_data_layers is true (optional)

Returns :

Mesh created from object

Return type :

Mesh

to_mesh_clear ( ) 

Discard the mesh data-block that to_mesh() produced

to_curve ( depsgraph , * , apply_modifiers = False ) 

Build a Curve data-block from the object's present state. Only curve and text objects qualify. The data-block stays owned by the object; call to_curve_clear() to free it manually. What you get is temporary and may not be attached to objects in the main database.

Parameters :

- depsgraph (Depsgraph) – Dependency Graph, Evaluated dependency graph

- apply_modifiers ( bool ) – Apply the deform modifiers on the control points of the curve. This is only supported for curve objects. (optional)

Returns :

Curve created from object

Return type :

Curve

to_curve_clear ( ) 

Discard the curve data-block that to_curve() produced

find_armature ( ) 

Locate the armature that drives this object, whether as a parent or through a modifier

Returns :

Armature object influencing this object or nullptr

Return type :

Object

shape_key_add ( * , name = 'Key' , from_mix = True ) 

Attach a shape key to this object

Parameters :

- name ( str ) – Unique name for the new key-block (optional, never None)

- from_mix ( bool ) – Create new shape from existing mix of shapes (optional)

Returns :

New shape key-block

Return type :

ShapeKey

shape_key_remove ( key ) 

Detach one Shape Key from this object

Parameters :

key (ShapeKey) – Key-block to be removed (never None)

shape_key_clear ( ) 

Detach every Shape Key from this object

shape_keys_selected ( ) 

Give back the selected shape keys

Returns :

keyblocks

Return type :

bpy_prop_collection[ShapeKey]

ray_cast ( origin , direction , * , distance = 1.70141e+38 , depsgraph = None ) 

Shoot a ray against the evaluated geometry in object space (pulling the evaluated mesh from the context's or a supplied depsgraph as needed)

Parameters :

- origin (mathutils.Vector) – Origin of the ray, in object space (array of 3 items, in [-inf, inf])

- direction (mathutils.Vector) – Direction of the ray, in object space (array of 3 items, in [-inf, inf])

- distance ( float ) – Maximum distance (in [0, inf], optional)

- depsgraph (Depsgraph) – Depsgraph to use to get evaluated data, when called from original object (only needed if current Context’s depsgraph is not suitable) (optional)

Returns :

result , Whether the ray successfully hit the geometry, bool

location , The hit location of this ray cast, mathutils.Vector

normal , The face normal at the ray cast hit location, mathutils.Vector

index , The face index, -1 when original data isn’t available, int

Return type :

tuple[bool, mathutils.Vector, mathutils.Vector, int]

closest_point_on_mesh ( origin , * , distance = 1.84467e+19 , depsgraph = None ) 

Locate the closest point on the evaluated geometry in object space (pulling the evaluated mesh from the context's or a supplied depsgraph as needed)

Parameters :

- origin (mathutils.Vector) – Point to find closest geometry from (in object space) (array of 3 items, in [-inf, inf])

- distance ( float ) – Maximum distance (in [0, inf], optional)

- depsgraph (Depsgraph) – Depsgraph to use to get evaluated data, when called from original object (only needed if current Context’s depsgraph is not suitable) (optional)

Returns :

result , Whether closest point on geometry was found, bool

location , The location on the object closest to the point, mathutils.Vector

normal , The face normal at the closest point, mathutils.Vector

index , The face index, -1 when original data isn’t available, int

Return type :

tuple[bool, mathutils.Vector, mathutils.Vector, int]

is_modified ( scene , settings ) 

Report whether this object differs from its base mesh data

Parameters :

- scene (Scene) – Scene in which to check the object (never None)

- settings ( Literal [ 'PREVIEW' , 'RENDER' ] ) – Modifier settings to apply

- PREVIEW
Preview – Apply modifier preview settings.

- RENDER
Render – Apply modifier render settings.

Returns :

Whether the object is modified

Return type :

bool

is_deform_modified ( scene , settings ) 

Report whether a deformation moves this object away from its base mesh data

Parameters :

- scene (Scene) – Scene in which to check the object (never None)

- settings ( Literal [ 'PREVIEW' , 'RENDER' ] ) – Modifier settings to apply

- PREVIEW
Preview – Apply modifier preview settings.

- RENDER
Render – Apply modifier render settings.

Returns :

Whether the object is deform-modified

Return type :

bool

update_from_editmode ( ) 

Push the object's edit-mode data back into its object data

Returns :

Success

Return type :

bool

cache_release ( ) 

Free the memory held by this object's caches. Meant for use by render engines only.

evaluated_geometry ( ) 

Fetch the evaluated geometry set of this evaluated object. Restricted to objects carrying geometry data such as meshes and curves, not e.g. cameras.

Returns :

The evaluated geometry.

Return type :

bpy.types.GeometrySet

classmethod bl_rna_get_subclass ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (bpy.types.Struct | None) – The value to return when not found.

Returns :

The RNA type or default when not found.

Return type :

bpy.types.Struct

classmethod bl_rna_get_subclass_py ( id , default = None , / ) 

Parameters :

- id ( str ) – The RNA type identifier.

- default (type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.active_object bpy.context.edit_object bpy.context.editable_objects bpy.context.image_paint_object bpy.context.object bpy.context.objects_in_mode bpy.context.objects_in_mode_unique_data bpy.context.particle_edit_object bpy.context.pose_object bpy.context.sculpt_object bpy.context.selectable_objects bpy.context.selected_editable_objects bpy.context.selected_objects bpy.context.vertex_paint_object bpy.context.visible_objects bpy.context.weight_paint_object Action.flip_with_pose ActionConstraint.target ArmatureModifier.object ArrayModifier.curve ArrayModifier.end_cap ArrayModifier.offset_object ArrayModifier.start_cap BlendData.objects BlendDataMeshes.new_from_object BlendDataObjects.new BlendDataObjects.remove BoidRuleAvoid.object BoidRuleFollowLeader.object BoidRuleGoal.object BooleanModifier.object CameraDOFSettings.focus_object CastModifier.object ChildOfConstraint.target ClampToConstraint.target Collection.all_objects Collection.objects CollectionObjects.link CollectionObjects.unlink Constraint.space_object ConstraintTarget.target ConstraintTargetBone.target CopyLocationConstraint.target CopyRotationConstraint.target CopyScaleConstraint.target CopyTransformsConstraint.target Curve.bevel_object Curve.taper_object CurveModifier.object Curves.surface CyclesRenderSettings.dicing_camera DampedTrackConstraint.target DataTransferModifier.object Depsgraph.objects DepsgraphObjectInstance.instance_object DepsgraphObjectInstance.object DepsgraphObjectInstance.parent DisplaceModifier.texture_coords_object DynamicPaintSurface.output_exists FieldSettings.source_object FloorConstraint.target FluidDomainSettings.guide_parent FollowPathConstraint.target FollowTrackConstraint.camera FollowTrackConstraint.depth_object GPencilSculptGuide.reference_object GeometryAttributeConstraint.target GeometryNodeInputObject.object GreasePencilArmatureModifier.object GreasePencilArrayModifier.offset_object GreasePencilBuildModifier.object GreasePencilHookModifier.object GreasePencilLatticeModifier.object GreasePencilLayer.parent GreasePencilLineartModifier.light_contour_object GreasePencilLineartModifier.source_camera GreasePencilLineartModifier.source_object GreasePencilMirrorModifier.object GreasePencilOutlineModifier.object GreasePencilShrinkwrapModifier.auxiliary_target GreasePencilShrinkwrapModifier.target GreasePencilTintModifier.object GreasePencilWeightProximityModifier.object HookModifier.object | KinematicConstraint.pole_target KinematicConstraint.target LatticeModifier.object LayerObjects.active LayerObjects.selected LimitDistanceConstraint.target LineStyleAlphaModifier_DistanceFromObject.target LineStyleColorModifier_DistanceFromObject.target LineStyleThicknessModifier_DistanceFromObject.target LockedTrackConstraint.target MaskModifier.armature MeshDeformModifier.object MeshToVolumeModifier.object MirrorModifier.mirror_object NodeSocketObject.default_value NodeTreeInterfaceSocketObject.default_value NormalEditModifier.target Object.find_armature Object.parent ObjectBase.object ObjectSolverConstraint.camera ParticleEdit.object ParticleEdit.shape_object ParticleHairKey.co_object ParticleHairKey.co_object_set ParticleInstanceModifier.object ParticleSettings.instance_object ParticleSettingsTextureSlot.object ParticleSystem.co_hair ParticleSystem.parent ParticleSystem.reactor_target_object ParticleTarget.object PivotConstraint.target PoseBone.custom_shape RenderEngine.bake RenderEngine.camera_model_matrix RenderEngine.camera_override RenderEngine.camera_shift_x RenderEngine.use_spherical_stereo RigidBodyConstraint.object1 RigidBodyConstraint.object2 RigidBodyWorld.convex_sweep_test BakeSettings.cage_object Scene.camera Scene.objects Scene.ray_cast Scene.uvedit_aspect SceneStrip.scene_camera ScrewModifier.object Sculpt.gravity_object ShaderFxShadow.object ShaderFxSwirl.object ShaderNodeTexCoord.object ShrinkwrapConstraint.target ShrinkwrapModifier.auxiliary_target ShrinkwrapModifier.target SimpleDeformModifier.origin SpaceView3D.camera SpaceView3D.lock_object SplineIKConstraint.target StretchToConstraint.target SurfaceDeformModifier.target TextCurve.follow_curve TimelineMarker.camera ToolSettings.anim_mirror_object ToolSettings.anim_relative_object TrackToConstraint.target TransformConstraint.target UVProjector.object UVWarpModifier.object_from UVWarpModifier.object_to VertexWeightEditModifier.mask_tex_map_object VertexWeightMixModifier.mask_tex_map_object VertexWeightProximityModifier.mask_tex_map_object VertexWeightProximityModifier.target ViewLayer.objects VolumeDisplaceModifier.texture_map_object VolumeToMeshModifier.object WarpModifier.object_from WarpModifier.object_to WarpModifier.texture_coords_object WaveModifier.start_position_object WaveModifier.texture_coords_object XrSessionSettings.base_pose_object |

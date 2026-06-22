# Wm Operators (part 8)

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

- only_deform_bones ( bool ) – Only Deform Bones, Write only deformation joints and their ancestors (optional)

- export_shapekeys ( bool ) – Shape Keys, Write shape keys as USD combine structures (optional)

- use_instancing ( bool ) – Instancing, Write duplicated items as cross-references in USD rather than replicated items (optional)

- evaluation_mode ( Literal [ 'RENDER' , 'VIEWPORT' ] ) – Use Settings for, Picks whether objects are shown, parameter adjustments, and additional zones where render and view setups differ (optional)

- RENDER
Render – Apply Rendering configuration for thing appearance, parameter adjustments, and so forth.

- VIEWPORT
Viewport – Apply View configuration for thing appearance, parameter adjustments, and so forth.

- generate_preview_surface ( bool ) – USD Preview Surface Network, Make a representative USD Preview SurfaceTemplate representation of a Principled BSDF diagram organization (optional)

- generate_materialx_network ( bool ) – MaterialX Network, Make a MaterialX diagram representation of the materials (optional)

- convert_orientation ( bool ) – Convert Orientation, Shift orientation direction to a distinct convention to correlate with alternative platforms (optional)

- export_global_forward_selection ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Forward Axis, (optional)

- X
X – Positive X axis.

- Y
Y – Positive Y axis.

- Z
Z – Positive Z axis.

- `NEGATIVE_X`
-X – Negative X axis.

- `NEGATIVE_Y`
-Y – Negative Y axis.

- `NEGATIVE_Z`
-Z – Negative Z axis.

- export_global_up_selection ( Literal [ 'X' , 'Y' , 'Z' , '`NEGATIVE_X`' , '`NEGATIVE_Y`' , '`NEGATIVE_Z`' ] ) – Up Axis, (optional)

- X
X – Positive X axis.

- Y
Y – Positive Y axis.

- Z
Z – Positive Z axis.

- `NEGATIVE_X`
-X – Negative X axis.

- `NEGATIVE_Y`
-Y – Negative Y axis.

- `NEGATIVE_Z`
-Z – Negative Z axis.

- export_textures_mode ( Literal [ 'KEEP' , 'PRESERVE' , 'NEW' ] ) – Export Textures, Surface map delivery method (optional)

- KEEP
Keep – Maintain original location of surfaces.

- PRESERVE
Preserve – Keep file positioning of surfaces from previously brought USD information.
Ship extra surfaces to a 'images' folder near the USD data.

- NEW
New Path – Ship surfaces to a 'images' folder near the USD data.

- overwrite_textures ( bool ) – Overwrite Textures, Overwrite existing documents when writing surfaces (optional)

- relative_paths ( bool ) – Relative Paths, Utilize relative links to mention external documents (e.g. surfaces, quantity) in USD, or else utilize full links (optional)

- xform_op_mode ( Literal [ 'TRS' , 'TOS' , 'MAT' ] ) – Xform Ops, Category of transform functions to create (optional)

- TRS
Translate, Rotate, Scale – Write utilizing move, rotate, and expand Xform functions.

- TOS
Translate, Orient, Scale – Write utilizing move, point quaternion, and expand Xform functions.

- MAT
Matrix – Write math function.

- root_prim_path ( str ) – Root Prim, If given, append a translate element with the specified label to the set as the chief of all written material (optional, never None)

- export_custom_properties ( bool ) – Custom Properties, Write personalized qualities as USD qualities (optional)

- custom_properties_namespace ( str ) – Namespace, If given, add the specified namespace as a label to written individualized characteristic codes. This operates only to names that lack a previous tag (e.g., it handles 'bar' but rejects 'foo:bar') and does not apply to blender thing and file labels which are constantly written in the 'userProperties:blender' namespace (optional, never None)

- accessibility_label ( str ) – Label, Make the ease-of-use identifier for the written set's principal element (optional, never None)

- accessibility_description ( str ) – Description, Make the ease-of-use narrative for the written set's principal element (optional, never None)

- author_blender_name ( bool ) – Blender Names, Compose USD personalized characteristics bearing the actual Blender thing and file information codes (optional)

- convert_world_material ( bool ) – World Dome Light, Shift the environmental material to a USD illuminated hemisphere. Presently functions for uncomplicated materials, made of a background photo attached to a lighting filter, with a possible arithmetic operation of the photo coloration (optional)

- allow_unicode ( bool ) – Allow Unicode, Maintain UTF-8 translation signs when composing USD label and characteristic codes (wants package utilizing USD 24.03 or greater when unlocking the output documents) (optional)

- export_meshes ( bool ) – Meshes, Send all surfaces (optional)

- export_lights ( bool ) – Lights, Send all illumination (optional)

- export_cameras ( bool ) – Cameras, Send all lenses (optional)

- export_curves ( bool ) – Curves, Send all arcs (optional)

- export_points ( bool ) – Point Clouds, Send all mark gatherings (optional)

- export_volumes ( bool ) – Volumes, Send all areas (optional)

- triangulate_meshes ( bool ) – Triangulate Meshes, Convert meshes to triangles during delivery (optional)

- quad_method (Literal[Modifier Triangulate Quad Method Items]) – Quad Method, Technique for breaking the quadrangles to triangles (optional)

- ngon_method (Literal[Modifier Triangulate Ngon Method Items]) – N-gon Method, Technique for breaking the n-sided shapes to triangles (optional)

- usdz_downscale_size ( Literal [ 'KEEP' , '256' , '512' , '1024' , '2048' , '4096' , 'CUSTOM' ] ) – USDZ Texture Downsampling, Establish a boundary size for shipped surfaces (optional)

- KEEP
Keep – Preserve all current surface measures.

- 256
256 – Modify to a boundary of 256 dots.

- 512
512 – Modify to a boundary of 512 dots.

- 1024
1024 – Modify to a boundary of 1024 dots.

- 2048
2048 – Modify to a boundary of 2048 dots.

- 4096
4096 – Modify to a boundary of 4096 dots.

- CUSTOM
Custom – Specify a custom measure.

- usdz_downscale_custom_size ( int ) – USDZ Custom Downscale Size, User-defined measure for shrinking written surfaces (in [64, 16384], optional)

- merge_parent_xform ( bool ) – Merge parent Xform, Merge USD building blocks with their Xform ancestor if feasible. USD does not authorize interior UsdGeomGprims, middle Xform blocks will be made to sustain the USD document authentic when meeting item lineages. (optional)

- convert_scene_units ( Literal [ 'METERS' , 'KILOMETERS' , 'CENTIMETERS' , 'MILLIMETERS' , 'INCHES' , 'FEET' , 'YARDS' , 'CUSTOM' ] ) – Units, Adjust the USD Phase meters per measurement to the chosen scale, or a user value (optional)

- METERS
Meters – Phase meters per measurement to 1.0.

- KILOMETERS
Kilometers – Phase meters per measurement to 1000.0.

- CENTIMETERS
Centimeters – Phase meters per measurement to 0.01.

- MILLIMETERS
Millimeters – Phase meters per measurement to 0.001.

- INCHES
Inches – Phase meters per measurement to 0.0254.

- FEET
Feet – Phase meters per measurement to 0.3048.

- YARDS
Yards – Phase meters per measurement to 0.9144.

- CUSTOM
Custom – Specify a user-defined phase meters per measurement amount.

- meters_per_unit ( float ) – Meters Per Unit, User value for meters per measurement in the USD Phase (in [0.0001, 1000], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. usd_import ( * , filepath = '' , check_existing = False , filter_blender = False , filter_backup = False , filter_image = False , filter_movie = False , filter_python = False , filter_font = False , filter_sound = False , filter_text = False , filter_archive = False , filter_btx = False , filter_alembic = False , filter_usd = True , filter_obj = False , filter_volume = False , filter_folder = True , filter_blenlib = False , filemode = 8 , relative_path = True , display_type = 'DEFAULT' , sort_method = '' , filter_glob = '*.usd' , scale = 1.0 , set_frame_range = True , import_cameras = True , import_curves = True , import_lights = True , import_materials = True , import_meshes = True , import_volumes = True , import_shapes = True , import_skeletons = True , import_blendshapes = True , import_points = True , import_subdivision = False , support_scene_instancing = True , import_visible_only = True , create_collection = False , read_mesh_uvs = True , read_mesh_colors = True , read_mesh_attributes = True , prim_path_mask = '' , import_guide = False , import_proxy = False , import_render = True , import_all_materials = False , import_usd_preview = True , set_material_blend = True , light_intensity_scale = 1.0 , mtl_purpose = '`MTL_FULL`' , mtl_name_collision_mode = '`MAKE_UNIQUE`' , import_textures_mode = '`IMPORT_PACK`' , import_textures_dir = '//textures/' , tex_name_collision_mode = '`USE_EXISTING`' , property_import_mode = 'ALL' , validate_meshes = False , create_world_material = True , import_defined_only = True , merge_parent_xform = True , apply_unit_conversion_scale = True ) 

Bring USD arrangement into the present setting

Parameters :

- filepath ( str ) – File Path, Location to file (optional, never None)

- check_existing ( bool ) – Check Existing, Verify and warn when writing over documents (optional)

- filter_blender ( bool ) – Filter .blend files, (optional)

- filter_backup ( bool ) – Filter backup .blend files, (optional)

- filter_image ( bool ) – Filter image files, (optional)

- filter_movie ( bool ) – Filter movie files, (optional)

- filter_python ( bool ) – Filter Python files, (optional)

- filter_font ( bool ) – Filter font files, (optional)

- filter_sound ( bool ) – Filter sound files, (optional)

- filter_text ( bool ) – Filter text files, (optional)

- filter_archive ( bool ) – Filter archive files, (optional)

- filter_btx ( bool ) – Filter btx files, (optional)

- filter_alembic ( bool ) – Filter Alembic files, (optional)

- filter_usd ( bool ) – Filter USD files, (optional)

- filter_obj ( bool ) – Filter OBJ files, (optional)

- filter_volume ( bool ) – Filter OpenVDB volume files, (optional)

- filter_folder ( bool ) – Filter folders, (optional)

- filter_blenlib ( bool ) – Filter Blender IDs, (optional)

- filemode ( int ) – File Browser Mode, Configuration for the file browser type to bring a .blend file, a library or specific document (in [1, 9], optional)

- relative_path ( bool ) – Relative Path, Choose the document relative to the blend file (optional)

- display_type ( Literal [ 'DEFAULT' , '`LIST_VERTICAL`' , '`LIST_HORIZONTAL`' , 'THUMBNAIL' ] ) – Display Type, (optional)

- DEFAULT
Default – Pick display method for documents automatically.

- `LIST_VERTICAL`
Short List – Show documents as short list.

- `LIST_HORIZONTAL`
Long List – Show documents as detailed list.

- THUMBNAIL
Thumbnails – Show documents as thumbnails.

- sort_method ( str ) – File sorting mode, (optional)

- filter_glob ( str ) – (optional, never None)

- scale ( float ) – Scale, Amount to magnify or minimize the things matching the place of beginning (in [0.0001, 1000], optional)

- set_frame_range ( bool ) – Set Frame Range, Refresh the setup's starting and closing frame to coincide with those of the USD information (optional)

- import_cameras ( bool ) – Cameras, (optional)

- import_curves ( bool ) – Curves, (optional)

- import_lights ( bool ) – Lights, (optional)

- import_materials ( bool ) – Materials, (optional)

- import_meshes ( bool ) – Meshes, (optional)

- import_volumes ( bool ) – Volumes, (optional)

- import_shapes ( bool ) – USD Shapes, (optional)

- import_skeletons ( bool ) – Armatures, (optional)

- import_blendshapes ( bool ) – Shape Keys, (optional)

- import_points ( bool ) – Point Clouds, (optional)

- import_subdivision ( bool ) – Import Subdivision Scheme, Build subdivision outer layer adjusters grounded in the USD SubdivisionScheme characteristic (optional)

- support_scene_instancing ( bool ) – Scene Instancing, Bring USD hierarchy examples as group examples (optional)

- import_visible_only ( bool ) – Visible Primitives Only, Skip importing hidden USD structures. Applies merely to structures lacking an shifting appearance characteristic. Structures with active appearance will forever be brought (optional)

- create_collection ( bool ) – Create Collection, Position every brought item into a newly made batch (optional)

- read_mesh_uvs ( bool ) – UV Coordinates, Read mesh shade coordinates (optional)

- read_mesh_colors ( bool ) – Color Attributes, Read mesh hue characteristics (optional)

- read_mesh_attributes ( bool ) – Mesh Attributes, Read USD Primvars as mesh characteristics (optional)

- prim_path_mask ( str ) – Path Mask, Bring merely the structural element at the given trail and its offspring. Many trails may be specified in a sequence split by commas or semicolons (optional, never None)

- import_guide ( bool ) – Guide, Bring guiding material (optional)

- import_proxy ( bool ) – Proxy, Bring surrogate material (optional)

- import_render ( bool ) – Render, Bring ultimate display material (optional)

- import_all_materials ( bool ) – Import All Materials, Also bring materials that lack usage by any material. Remember that when this choice is false, materials utilized by material will remain brought (optional)

- import_usd_preview ( bool ) – Import USD Preview, Transmute UsdPreviewSurface color programs to Principled BSDF color schemes (optional)

- set_material_blend ( bool ) – Set Material Blend, If the Bring USD Preview choice is turned on, the material mix method will be configured automatically grounded on the color program's opacity and opacityThreshold characteristics (optional)

- light_intensity_scale ( float ) – Light Intensity Scale, Growth for the power of brought-in illumination (in [0.0001, 10000], optional)

- mtl_purpose ( Literal [ '`MTL_ALL_PURPOSE`' , '`MTL_PREVIEW`' , '`MTL_FULL`' ] ) – Material Purpose, Endeavor to bring materials with the designated objective. If no material bearing this objective is fastened to the item, revert on bringing any substitute fastened material (optional)

- `MTL_ALL_PURPOSE`
All Purpose – Strive to bring 'allPurpose' materials.

- `MTL_PREVIEW`
Preview – Strive to bring 'preview' materials. Bring 'allPurpose' materials as a fallback.

- `MTL_FULL`
Full – Strive to bring 'full' materials. Bring 'allPurpose' or 'preview' materials, in that ranking, as a fallback.

- mtl_name_collision_mode ( Literal [ '`MAKE_UNIQUE`' , '`REFERENCE_EXISTING`' ] ) – Material Name Collision, Procedure when the identifier of a brought-in material overlaps with a present material (optional)

- `MAKE_UNIQUE`
Make Unique – Bring each USD material as a discrete Blender material.

- `REFERENCE_EXISTING`
Reference Existing – If a material carrying the same identifier currently remains, utilize that rather than bringing.

- import_textures_mode ( Literal [ '`IMPORT_NONE`' , '`IMPORT_PACK`' , '`IMPORT_COPY`' ] ) – Import Textures, Procedure when getting surfaces from a USDZ storage file (optional)

- `IMPORT_NONE`
None – Don't bring surfaces.

- `IMPORT_PACK`
Packed – Bring surfaces as compressed information.

- `IMPORT_COPY`
Copy – Duplicate documents to surfaces folder.

- import_textures_dir ( str ) – Textures Directory, Direction to the folder where brought surfaces will be duplicated (optional, never None)

- tex_name_collision_mode ( Literal [ '`USE_EXISTING`' , 'OVERWRITE' ] ) – File Name Collision, Procedure when the identifier of a brought document disputes with a present document (optional)

- `USE_EXISTING`
Use Existing – If a document with the matching identifier currently exists, utilize that rather than duplicating.

- OVERWRITE
Overwrite – Overwrite present documents.

- property_import_mode ( Literal [ 'NONE' , 'USER' , 'ALL' ] ) – Custom Properties, Procedure when getting USD qualities as Blender customized characteristics (optional)

- NONE
None – Do not get USD customized characteristics.

- USER
User – Get USD qualities in the 'userProperties' namespace as Blender customized characteristics. The namespace will be stripped from the property identifiers.

- ALL
All Custom – Get every USD customized qualities as Blender customized characteristics. Namespaces will be maintained in the property identifiers.

- validate_meshes ( bool ) – Validate Meshes, Verify that the content is sound (when deactivated, brought content may create slowdowns or crashes when viewing or altering) (optional)

- create_world_material ( bool ) – World Dome Light, Shift the initially encountered USD dome illumination to a planetary lighting filter (optional)

- import_defined_only ( bool ) – Defined Primitives Only, Bring merely interpreted USD structures. When deactivated this permits bringing USD structures which stay unfulfilled, for instance those bearing an alternative signifier (optional)

- merge_parent_xform ( bool ) – Merge parent Xform, Let USD structures unite with their Xform ancestor if they are the sole heir in the ranking (optional)

- apply_unit_conversion_scale ( bool ) – Apply Unit Conversion Scale, Modify the setup things by the USD set's meters per measurement amount. This alteration is employed in appendix to the amount specified in the Growth choice (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. window_close ( ) 

Shut the present window

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. window_fullscreen_toggle ( ) 

Alternate the present window complete screen

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. window_new ( ) 

Make a fresh window

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. window_new_main ( ) 

Make a fresh main window bearing its individual workplace and item choosing

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.wm. xr_navigation_fly ( * , mode = '`VIEWER_FORWARD`' , snap_turn_threshold = 0.95 , lock_location_z = False , lock_direction = False , speed_frame_based = False , turn_speed_factor = 0.333333 , fly_speed_factor = 0.333333 , speed_interpolation0 = (0.0, 0.0) , speed_interpolation1 = (1.0, 1.0) , alt_mode = '`VIEWER_FORWARD`' , alt_lock_location_z = False , alt_lock_direction = False ) 

Shift/pivot matching the VR watcher or tool

Parameters :

- mode ( Literal [ 'FORWARD' , 'BACK' , 'LEFT' , 'RIGHT' , 'UP' , 'DOWN' , 'TURNLEFT' , 'TURNRIGHT' , '`VIEWER_FORWARD`' , '`VIEWER_BACK`' , '`VIEWER_LEFT`' , '`VIEWER_RIGHT`' , '`CONTROLLER_FORWARD`' ] ) – Mode, Flight pattern (optional)

- FORWARD
Forward – Shift along pathway ahead marker.

- BACK
Back – Shift along pathway rear marker.

- LEFT
Left – Shift along pathway left marker.

- RIGHT
Right – Shift along pathway right marker.

- UP
Up – Shift along pathway upper marker.

- DOWN
Down – Shift along pathway lower marker.

- TURNLEFT
Turn Left – Pivot leftward about pathway upper marker.

- TURNRIGHT
Turn Right – Pivot rightward about pathway upper marker.

- `VIEWER_FORWARD`
Viewer Forward – Shift along watcher's ahead marker.

- `VIEWER_BACK`
Viewer Back – Shift along watcher's rear marker.

- `VIEWER_LEFT`
Viewer Left – Shift along watcher's left marker.

- `VIEWER_RIGHT`
Viewer Right – Shift along watcher's right marker.

- `CONTROLLER_FORWARD`
Controller Forward – Shift along gadget's ahead marker.

- snap_turn_threshold ( float ) – Snap Turn Threshold, Trigger rank for action when utilizing break pivot (in [0, 1], optional)

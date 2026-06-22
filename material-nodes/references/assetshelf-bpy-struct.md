# Assetshelf Bpy Struct, Bakesettings Bpy Struct, Bevelmodifier Modifier

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: AssetShelf(bpy_struct); BakeSettings(bpy_struct); BevelModifier(Modifier).

## AssetShelf(bpy_struct)

UI widget for quick asset browsing and picking.

base class — bpy_struct

subclasses —
`IMAGE_AST`_brush_paint, `NODE_AST`_compositor, `VIEW3D_AST`_brush_gpencil_paint, `VIEW3D_AST`_brush_gpencil_sculpt, `VIEW3D_AST`_brush_gpencil_vertex, `VIEW3D_AST`_brush_gpencil_weight, `VIEW3D_AST`_brush_sculpt, `VIEW3D_AST`_brush_sculpt_curves, `VIEW3D_AST`_brush_texture_paint, `VIEW3D_AST`_brush_vertex_paint, `VIEW3D_AST`_brush_weight_paint, `VIEW3D_AST`_pose_library

class bpy.types. AssetShelf ( bpy_struct )

Quick-access asset panel within an editor.

asset_library_reference

Choose the asset library to display assets from (default 'ALL' )

- ALL
All Libraries – Show assets from all of the listed asset libraries.

- LOCAL
Current File – Show the assets currently available in this Blender session.

- ESSENTIALS
Essentials – Show the basic building blocks and utilities coming with Blender.

- CUSTOM
Custom – Show assets from the asset libraries configured in the Preferences.

Type :

Literal['ALL', 'LOCAL', 'ESSENTIALS', 'CUSTOM']

bl_activate_operator

Operator to call when activating an item with asset reference properties (default "", never None)

Type :

str

bl_default_preview_size

Default size of the asset preview thumbnails in pixels (in [32, 256], default 0)

Type :

int

bl_drag_operator

Operator to call when dragging an item with asset reference properties (default "", never None)

Type :

str

bl_idname

If this is set, the asset gets a custom ID, otherwise it takes the name of the class used to define the asset (for example, if the class name is "`OBJECT_AST`_hello", and bl_idname is not set by the script, then bl_idname = "`OBJECT_AST`_hello") (default "", never None)

Type :

str

bl_options

Options for this asset shelf type (default set())

- `NO_ASSET_DRAG`
No Asset Dragging – Disable the default asset dragging on drag events. Useful for implementing custom dragging via custom key-map items..

- `DEFAULT_VISIBLE`
Visible by Default – Unhide the asset shelf when it's available for the first time, otherwise it will be hidden.

- `STORE_ENABLED_CATALOGS_IN_PREFERENCES`
Store Enabled Catalogs in Preferences – Store the shelf's enabled catalogs in the preferences rather than the local asset shelf settings.

- `ACTIVATE_FOR_CONTEXT_MENU`
When spawning a context menu for an asset, activate the asset and call `bl_activate_operator` if present, rather than just highlighting the asset.

Type :

set[Literal['`NO_ASSET_DRAG`', '`DEFAULT_VISIBLE`', '`STORE_ENABLED_CATALOGS_IN_PREFERENCES`', '`ACTIVATE_FOR_CONTEXT_MENU`']]

bl_space_type

The space where the asset shelf will show up in. Ignored for popup asset shelves which can be displayed in any space. (default 'EMPTY' )

Type :

Literal[Space Type Items]

filter_action

Show Action data-blocks (default False)

Type :

bool

filter_annotations

Show Annotation data-blocks (default False)

Type :

bool

filter_armature

Show Armature data-blocks (default False)

Type :

bool

filter_brush

Show Brushes data-blocks (default False)

Type :

bool

filter_cachefile

Show Cache File data-blocks (default False)

Type :

bool

filter_camera

Show Camera data-blocks (default False)

Type :

bool

filter_curve

Show Curve data-blocks (default False)

Type :

bool

filter_curves

Show/hide Curves data-blocks (default False)

Type :

bool

filter_font

Show Font data-blocks (default False)

Type :

bool

filter_grease_pencil

Show Grease Pencil data-blocks (default False)

Type :

bool

filter_group

Show Collection data-blocks (default False)

Type :

bool

filter_image

Show Image data-blocks (default False)

Type :

bool

filter_lattice

Show Lattice data-blocks (default False)

Type :

bool

filter_light

Show Light data-blocks (default False)

Type :

bool

filter_light_probe

Show Light Probe data-blocks (default False)

Type :

bool

filter_linestyle

Show Freestyle's Line Style data-blocks (default False)

Type :

bool

filter_mask

Show Mask data-blocks (default False)

Type :

bool

filter_material

Show Material data-blocks (default False)

Type :

bool

filter_mesh

Show Mesh data-blocks (default False)

Type :

bool

filter_metaball

Show Metaball data-blocks (default False)

Type :

bool

filter_movie_clip

Show Movie Clip data-blocks (default False)

Type :

bool

filter_node_tree

Show Node Tree data-blocks (default False)

Type :

bool

filter_object

Show Object data-blocks (default False)

Type :

bool

filter_paint_curve

Show Paint Curve data-blocks (default False)

Type :

bool

filter_palette

Show Palette data-blocks (default False)

Type :

bool

filter_particle_settings

Show Particle Settings data-blocks (default False)

Type :

bool

filter_pointcloud

Show/hide Point Cloud data-blocks (default False)

Type :

bool

filter_scene

Show Scene data-blocks (default False)

Type :

bool

filter_sound

Show Sound data-blocks (default False)

Type :

bool

filter_speaker

Show Speaker data-blocks (default False)

Type :

bool

filter_text

Show Text data-blocks (default False)

Type :

bool

filter_texture

Show Texture data-blocks (default False)

Type :

bool

filter_volume

Show/hide Volume data-blocks (default False)

Type :

bool

filter_work_space

Show workspace data-blocks (default False)

Type :

bool

filter_world

Show World data-blocks (default False)

Type :

bool

preview_size

Size of the asset preview thumbnails in pixels (in [24, 256], default 0)

Type :

int

search_filter

Filter assets by name (default "", never None)

Type :

str

show_names

Show the asset name together with the preview. Otherwise only the preview will be visible. (default False)

Type :

bool

classmethod poll ( context )

If this method returns a non-null output, the asset shelf will be visible

Return type :

bool

classmethod asset_poll ( asset )

Determine if an asset should be visible in the asset shelf. If this method returns a non-null output, the asset will be visible.

Return type :

bool

classmethod get_active_asset ( )

Return a reference to the asset that should be highlighted as active in the asset shelf

Returns :

The weak reference to the asset to be highlighted as active, or None

Return type :

AssetWeakReference

classmethod draw_context_menu ( context , asset , layout )

Draw UI elements into the context menu UI layout displayed on right click

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

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

UI widget for quick asset browsing and picking — continued methods.

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

## BakeSettings(bpy_struct)

Stores baking configuration parameters for a render scene.

base class — bpy_struct

class bpy.types. BakeSettings ( bpy_struct )

Rendering settings for baked shading data

cage_extrusion 

Extend the active object outward by this distance during baking, which improves correspondence with points on object surfaces. (in [0, inf], default 0.0)

Type :

float

cage_object 

Substitute mesh to use for ray-casting instead of auto-deriving one from cage extrusion

Type :

Object

displacement_space 

Determines the coordinate system for displacement output (default 'OBJECT' )

- OBJECT
Object – Output displacement data in object coordinates.

- TANGENT
Tangent – Output displacement data in tangent-space coordinates.

Type :

Literal['OBJECT', 'TANGENT']

filepath 

File path for external image output (default "", never None, blend relative // prefix supported)

Type :

str

height 

Vertical resolution of the baked texture (in [4, 10000], default 512)

Type :

int

image_settings 

(readonly, never None)

Type :

ImageFormatSettings

margin 

Spread baked colors beyond island edges as post-baking dilation (in [0, 32767], default 16)

Type :

int

margin_type 

Dilation method for the baked result (default '`ADJACENT_FACES`' )

Type :

Literal[Bake Margin Type Items]

max_ray_distance 

Upper limit on ray length when matching surface points between objects. Zero indicates unlimited distance. (in [0, inf], default 0.0)

Type :

float

normal_b 

Channel assignment for normal blue component (default '`POS_X`' )

Type :

Literal[Normal Swizzle Items]

normal_g 

Channel assignment for normal green component (default '`POS_X`' )

Type :

Literal[Normal Swizzle Items]

normal_r 

Channel assignment for normal red component (default '`POS_X`' )

Type :

Literal[Normal Swizzle Items]

normal_space 

Selects the coordinate frame for output normal data (default 'TANGENT' )

Type :

Literal[Normal Space Items]

pass_filter 

Rendering contributions to merge into the active pass (default { 'COLOR' , 'DIFFUSE' , 'DIRECT' , 'EMIT' , 'GLOSSY' , 'INDIRECT' , 'TRANSMISSION' }, readonly)

Type :

set[Literal[Bake Pass Filter Type Items]]

save_mode 

Where baked results are written (default 'INTERNAL' )

Type :

Literal[Bake Save Mode Items]

target 

Destination for baked output (default '`IMAGE_TEXTURES`' )

Type :

Literal[Bake Target Items]

type 

Selects what shading data to bake (default 'NORMALS' )

- NORMALS
Normals – Render surface normal information.

- DISPLACEMENT
Displacement – Render height/depth displacement.

- `VECTOR_DISPLACEMENT`
Vector Displacement – Render full vector displacement.

Type :

Literal['NORMALS', 'DISPLACEMENT', '`VECTOR_DISPLACEMENT`']

use_automatic_name 

Generate output filenames from the pass type designation (external mode only) (default False)

Type :

bool

use_cage 

Fire rays from a separate mesh cage for baking (default False)

Type :

bool

use_clear 

Erase output images before baking starts (internal mode only) (default True)

Type :

bool

use_lores_mesh 

Sample against the base mesh geometry without subdivision (default False)

Type :

bool

use_multires 

Bake directly from a multires-modified object (default False)

Type :

bool

use_pass_color 

Include color pass in output (default True)

Type :

bool

use_pass_diffuse 

Include diffuse shading in the result (default True)

Type :

bool

use_pass_direct 

Include direct illumination in the result (default True)

Type :

bool

use_pass_emit 

Include emitted light in the result (default True)

Type :

bool

use_pass_glossy 

Include specular highlight contributions (default True)

Type :

bool

use_pass_indirect 

Include bounced light in the result (default True)

Type :

bool

use_pass_transmission 

Include transmitted light in the result (default True)

Type :

bool

use_selected_to_active 

Bake colors from selected surfaces onto the target (default False)

Type :

bool

use_split_materials 

Generate separate images per material slot (external mode only) (default False)

Type :

bool

view_from 

Origin point for ray casting (default '`ABOVE_SURFACE`' )

- `ABOVE_SURFACE`
Above Surface – Initiate rays from surface outward.

- `ACTIVE_CAMERA`
Active Camera – Fire rays from the active viewpoint.

Type :

Literal['`ABOVE_SURFACE`', '`ACTIVE_CAMERA`']

width 

Horizontal resolution of the baked texture (in [4, 10000], default 512)

Type :

int

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

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| RenderSettings.bake | |

## BevelModifier(Modifier)

Procedural operator that smooths and rounds edge and corner geometry.

base classes — bpy_struct, Modifier

class bpy.types. BevelModifier ( Modifier )

Adds rounded corners and edges to geometry

affect 

Choose what geometry features to alter (default 'EDGES' )

- VERTICES
Vertices – Smooth only corner points.

- EDGES
Edges – Smooth only edge loops.

Type :

Literal['VERTICES', 'EDGES']

angle_limit 

Threshold angle for which edges qualify for beveling (in [0, 3.14159], default 0.523599)

Type :

float

custom_profile 

Defines the curvature shape along the beveled surface (readonly)

Type :

CurveProfile

edge_weight 

Name of the attribute controlling edge bevel intensity (default "", never None)

Type :

str

face_strength_mode 

How and where to apply face strength attributes (default '`FSTR_NONE`' )

- `FSTR_NONE`
None – Do not apply face strength.

- `FSTR_NEW`
New – Apply face strength only to freshly created surfaces.

- `FSTR_AFFECTED`
Affected – Apply to new surfaces and those altered by beveling.

- `FSTR_ALL`
All – Apply to all surfaces.

Type :

Literal['`FSTR_NONE`', '`FSTR_NEW`', '`FSTR_AFFECTED`', '`FSTR_ALL`']

harden_normals 

Make normals of new faces align with adjacent surfaces (default False)

Type :

bool

invert_vertex_group 

Reverse the influence range of the vertex group (default False)

Type :

bool

limit_method 

(default 'ANGLE' )

- NONE
None – Apply bevel uniformly across all edges.

- ANGLE
Angle – Restrict beveling to edges with sufficient angle between faces.

- WEIGHT
Weight – Use per-edge weights to control bevel depth.

- VGROUP
Vertex Group – Use group membership to determine what gets beveled.

Type :

Literal['NONE', 'ANGLE', 'WEIGHT', 'VGROUP']

loop_slide 

Prioritize edge travel over width consistency (default True)

Type :

bool

mark_seam 

Tag beveled edges as seams (default False)

Type :

bool

mark_sharp 

Flag beveled edges as sharp (default False)

Type :

bool

material 

Material slot for generated surfaces, -1 selects automatic assignment (in [-1, 32767], default -1)

Type :

int

miter_inner 

Corner style at inner miter intersections (default '`MITER_SHARP`' )

- `MITER_SHARP`
Sharp – Pointed corner.

- `MITER_ARC`
Arc – Rounded corner.

Type :

Literal['`MITER_SHARP`', '`MITER_ARC`']

miter_outer 

Corner style at outer miter intersections (default '`MITER_SHARP`' )

- `MITER_SHARP`
Sharp – Pointed corner.

- `MITER_PATCH`
Patch – Squared-off intersection.

- `MITER_ARC`
Arc – Rounded corner.

Type :

Literal['`MITER_SHARP`', '`MITER_PATCH`', '`MITER_ARC`']

offset_type 

Interpretation of the Width/Depth value (default 'OFFSET' )

- OFFSET
Offset – Distance outward from original edge.

- WIDTH
Width – Distance across the new beveled surface.

- DEPTH
Depth – Perpendicular height of the bevel strip.

- PERCENT
Percent – Relative to neighboring edge length.

- ABSOLUTE
Absolute – Distance along the neighboring edge.

Type :

Literal['OFFSET', 'WIDTH', 'DEPTH', 'PERCENT', 'ABSOLUTE']

profile 

Shape of the bevel cross-section (0.5 = circular) (in [0, 1], default 0.5)

Type :

float

profile_type 

Curve type for bevel shaping (default 'SUPERELLIPSE' )

- SUPERELLIPSE
Superellipse – Parabolic or elliptical profile.

- CUSTOM
Custom – User-defined arbitrary profile.

Type :

Literal['SUPERELLIPSE', 'CUSTOM']

segments 

Number of subdivisions in the beveled region (in [1, 1000], default 1)

Type :

int

spread 

Radius of inner miter arc (in [0, inf], default 0.1)

Type :

float

use_clamp_overlap 

Prevent bevel width from exceeding edge neighbors (default True)

Type :

bool

vertex_group 

Name of the vertex group controlling bevel (default "", never None)

Type :

str

vertex_weight 

Name of the attribute controlling vertex bevel intensity (default "", never None)

Type :

str

vmesh_method 

Algorithm for creating corner geometry (default 'ADJ' )

- ADJ
Grid Fill – Standard tessellation approach.

- CUTOFF
Cutoff – Trim the profile at intersections.

Type :

Literal['ADJ', 'CUTOFF']

width 

Distance to extend the bevel (in [0, inf], default 0.1)

Type :

float

width_pct 

Bevel extent for the percentage mode (in [0, inf], default 0.1)

Type :

float

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

- default ( type | None ) – The value to return when not found.

Returns :

The class or default when not found.

Return type :

type

### Inherited Properties 

| bpy_struct.id_data Modifier.name Modifier.type Modifier.show_viewport Modifier.show_render Modifier.show_in_editmode Modifier.show_on_cage | Modifier.show_expanded Modifier.is_active Modifier.use_pin_to_last Modifier.is_override_data Modifier.use_apply_on_spline Modifier.execution_time Modifier.persistent_uid |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete | bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Modifier.bl_rna_get_subclass Modifier.bl_rna_get_subclass_py |

## See also

- [Bpy Struct](bpy-struct.md)

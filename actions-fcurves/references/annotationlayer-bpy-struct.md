# Annotationlayer Bpy Struct, Annotationlayers Bpy Prop Collection, Annotationstroke Bpy Struct, Annotationstrokepoint Bpy Struct ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: AnnotationLayer(bpy_struct); AnnotationLayers(bpy_prop_collection); AnnotationStroke(bpy_struct); AnnotationStrokePoint(bpy_struct); AnyType(bpy_struct); AOV(bpy_struct); AOVs(bpy_prop_collection); Area(bpy_struct); AreaSpaces(bpy_prop_collection); Armature(ID).

## AnnotationLayer(bpy_struct)

A named layer within an annotation.

base class — bpy_struct

class bpy.types. AnnotationLayer ( bpy_struct )

A named grouping of sketches.

active_frame

Frame currently being displayed for this layer (readonly)

Type :

AnnotationFrame

annotation_hide

Set annotation Visibility (default False)

Type :

bool

annotation_onion_after_color

Base color for ghosts after the active frame (array of 3 items, in [0, 1], default (0.25, 0.1, 1.0))

Type :

mathutils.Color

annotation_onion_after_range

Maximum number of frames to show after current frame (in [-1, 120], default 0)

Type :

int

annotation_onion_before_color

Base color for ghosts before the active frame (array of 3 items, in [0, 1], default (0.302, 0.851, 0.302))

Type :

mathutils.Color

annotation_onion_before_range

Maximum number of frames to show before current frame (in [-1, 120], default 0)

Type :

int

annotation_onion_use_custom_color

Use custom colors for onion skinning instead of the theme (default False)

Type :

bool

annotation_opacity

Annotation Layer Opacity (in [0, 1], default 0.0)

Type :

float

color

Color for all strokes in this layer (array of 3 items, in [0, 1], default (0.0, 0.0, 0.0))

Type :

mathutils.Color

frames

Sketches for this layer on different frames (default None, readonly)

Type :

AnnotationFrames[AnnotationFrame]

info

Layer name (default "", never None)

Type :

str

is_ruler

This is a special ruler layer (default False, readonly)

Type :

bool

lock

Protect layer from further editing and/or frame changes (default False)

Type :

bool

lock_frame

Lock current frame displayed by layer (default False)

Type :

bool

select

Layer is selected for editing in the Dope Sheet (default False)

Type :

bool

show_in_front

Make the layer display in front of objects (default True)

Type :

bool

thickness

Thickness of annotation strokes (in [1, 10], default 0)

Type :

int

use_annotation_onion_skinning

Display annotation onion skins before and after the current frame (default False)

Type :

bool

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

### References 

| bpy.context.active_annotation_layer Annotation.layers | AnnotationLayers.new AnnotationLayers.remove |

## AnnotationLayers(bpy_prop_collection)

Container of annotation layers.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AnnotationLayers ( bpy_prop_collection )

Collection of annotation layer objects.

active_index

Index of active annotation layer (in [0, inf], default 0)

Type :

int

active_note

Note/Layer to add annotation strokes to (default 'DEFAULT' )

Type :

Literal['DEFAULT']

new ( name , * , set_active = True )

Instantiate a new annotation layer.

Parameters :

- name ( str ) – Name, Name of the layer (never None)

- set_active ( bool ) – Set Active, Set the newly created layer to the active layer (optional)

Returns :

The newly created layer

Return type :

AnnotationLayer

remove ( layer )

Delete a annotation layer.

Parameters :

layer (AnnotationLayer) – The layer to remove (never None)

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

### References 

| Annotation.layers | |

## AnnotationStroke(bpy_struct)

A single hand-drawn curve within an annotation frame.

base class — bpy_struct

class bpy.types. AnnotationStroke ( bpy_struct )

A sketched line segment in a frame.

points

Stroke data points (default None, readonly)

Type :

bpy_prop_collection[AnnotationStrokePoint]

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

### References 

| AnnotationFrame.strokes | |

## AnnotationStrokePoint(bpy_struct)

A single vertex of an annotation stroke.

base class — bpy_struct

class bpy.types. AnnotationStrokePoint ( bpy_struct )

A vertex location in a freehand sketch line.

co

(array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

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

### References 

| AnnotationStroke.points | |

## AnyType(bpy_struct)

A marker for any data type.

base class — bpy_struct

class bpy.types. AnyType ( bpy_struct )

RNA type that permits references to any data block.

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

### References 

| bpy.context.property BoneCollection.assign BoneCollection.unassign FCurve.update_autoflags Gizmo.target_set_prop KeyingSetInfo.generate Region.data UILayout.context_pointer_set UILayout.enum_item_description UILayout.enum_item_icon UILayout.enum_item_name UILayout.icon UILayout.panel_prop UILayout.prop UILayout.prop_decorator UILayout.prop_enum UILayout.prop_menu_enum UILayout.prop_search UILayout.prop_search UILayout.prop_tabs_enum UILayout.prop_tabs_enum UILayout.prop_with_menu UILayout.prop_with_popover UILayout.props_enum UILayout.template_ID UILayout.template_ID_preview UILayout.template_ID_session_uid UILayout.template_ID_tabs UILayout.template_any_ID UILayout.template_cache_file UILayout.template_cache_file_layers UILayout.template_cache_file_time_settings UILayout.template_cache_file_velocity | UILayout.template_color_picker UILayout.template_color_ramp UILayout.template_colormanaged_view_settings UILayout.template_colorspace_settings UILayout.template_component_menu UILayout.template_curve_mapping UILayout.template_curveprofile UILayout.template_greasepencil_color UILayout.template_histogram UILayout.template_icon_view UILayout.template_image UILayout.template_layers UILayout.template_layers UILayout.template_light_linking_collection UILayout.template_list UILayout.template_list UILayout.template_marker UILayout.template_matrix UILayout.template_movieclip UILayout.template_movieclip_information UILayout.template_palette UILayout.template_path_builder UILayout.template_search UILayout.template_search UILayout.template_search_preview UILayout.template_search_preview UILayout.template_track UILayout.template_vectorscope UILayout.template_waveform UIList.draw_item UIList.draw_item UIList.draw_item UIList.filter_items |

## AOV(bpy_struct)

A channel holding per-view-layer output data.

base class — bpy_struct

class bpy.types. AOV ( bpy_struct )

is_valid

Is the name of the AOV conflicting (default True)

Type :

bool

name

Name of the AOV (default "", never None)

Type :

str

type

Data type of the AOV (default 'COLOR' )

Type :

Literal['COLOR', 'VALUE']

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

| AOVs.add AOVs.remove | ViewLayer.active_aov ViewLayer.aovs |

## AOVs(bpy_prop_collection)

Collection for output channels.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AOVs ( bpy_prop_collection )

Container of output channels.

add ( )

add

Returns :

Newly created AOV

Return type :

AOV

remove ( aov )

Delete an AOV.

Parameters :

aov (AOV) – AOV to remove (never None)

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

### References 

| ViewLayer.aovs | |

## Area(bpy_struct)

A region of subdivided screen space.

base class — bpy_struct

class bpy.types. Area ( bpy_struct )

One subdivision of a screen displaying an editor.

height

Area height (in [0, 32767], default 0, readonly)

Type :

int

regions

Regions this area is subdivided in (default None, readonly)

Type :

bpy_prop_collection[Region]

show_menus

Show menus in the header (default True)

Type :

bool

spaces

Spaces contained in this area, the first being the active space (NOTE: Useful for example to restore a previously used 3D view space in a certain area to get the old view orientation) (default None, readonly)

Type :

AreaSpaces[Space]

type

Current editor type for this area (default '`VIEW_3D`' )

Type :

Literal[Space Type Items]

ui_type

Current editor type for this area

Type :

str

width

Area width (in [0, 32767], default 0, readonly)

Type :

int

x

The window relative vertical location of the area (in [-inf, inf], default 0, readonly)

Type :

int

y

The window relative horizontal location of the area (in [-inf, inf], default 0, readonly)

Type :

int

tag_redraw ( )

tag_redraw

header_text_set ( text )

Set the header status text

Parameters :

text ( str ) – Text, New string for the header, None clears the text

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

### References 

| Context.area | Screen.areas |

## AreaSpaces(bpy_prop_collection)

Container of spaces within an area.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AreaSpaces ( bpy_prop_collection )

Collection of editor spaces.

active

Space currently being displayed in this area (readonly)

Type :

Space

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

### References 

| Area.spaces | |

## Armature(ID)

A skeletal system for character rigging.

base classes — bpy_struct, ID

class bpy.types. Armature ( ID )

Hierarchical bone system, typically used for character animation and deformation.

animation_data

Animation data for this data-block (readonly)

Type :

AnimData

axes_position

The position for the axes on the bone. Increasing the value moves it closer to the tip; decreasing moves it closer to the root. (in [0, 1], default 0.0)

Type :

float

bones

(default None, readonly)

Type :

ArmatureBones[Bone]

collections

(default None)

Type :

BoneCollections[BoneCollection]

collections_all

List of all bone collections of the armature (default None, readonly)

Type :

bpy_prop_collection[BoneCollection]

display_type

(default 'OCTAHEDRAL' )

- OCTAHEDRAL
Octahedral – Display bones as octahedral shape (default).

- STICK
Stick – Display bones as simple 2D lines with dots.

- BBONE
B-Bone – Display bones as boxes, showing subdivision and B-Splines.

- ENVELOPE
Envelope – Display bones as extruded spheres, showing deformation influence volume.

- WIRE
Wire – Display bones as thin wires, showing subdivision and B-Splines.

Type :

Literal['OCTAHEDRAL', 'STICK', 'BBONE', 'ENVELOPE', 'WIRE']

edit_bones

(default None, readonly)

Type :

ArmatureEditBones[EditBone]

is_editmode

True when used in editmode (default False, readonly)

Type :

bool

pose_position

Show armature in binding pose or final posed state (default 'POSE' )

- POSE
Pose Position – Show armature in posed state.

- REST
Rest Position – Show Armature in binding pose state (no posing possible).

Type :

Literal['POSE', 'REST']

relation_line_position

The start position of the relation lines from parent to child bones (default 'TAIL' )

- TAIL
Tail – Draw the relationship line from the parent tail to the child head.

- HEAD
Head – Draw the relationship line from the parent head to the child head.

Type :

Literal['TAIL', 'HEAD']

show_axes

Display bone axes (default False)

Type :

bool

show_bone_colors

Display bone colors (default True)

Type :

bool

show_bone_custom_shapes

Display bones with their custom shapes (default True)

Type :

bool

show_names

Display bone names (default False)

Type :

bool

use_mirror_x

Apply changes to matching bone on opposite side of X-Axis (default False)

Type :

bool

transform ( matrix )

Transform armature bones by a matrix

Parameters :

matrix (mathutils.Matrix) – Matrix (multi-dimensional array of 4 * 4 items, in [-inf, inf])

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

| bpy_struct.id_data ID.name ID.name_full ID.id_type ID.session_uid ID.is_evaluated ID.original ID.users ID.use_fake_user ID.use_extra_user ID.is_embedded_data | ID.is_linked_packed ID.is_missing ID.is_runtime_data ID.is_editable ID.tag ID.is_library_indirect ID.library ID.library_weak_reference ID.asset_data ID.override_library ID.preview |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors | bpy_struct.type_recast bpy_struct.values ID.bl_system_properties_get ID.rename ID.evaluated_get ID.copy ID.asset_mark ID.asset_clear ID.asset_generate_preview ID.override_create ID.override_hierarchy_create ID.user_clear ID.user_remap ID.make_local ID.user_of_id ID.animation_data_create ID.animation_data_clear ID.update_tag ID.preview_ensure ID.bl_rna_get_subclass ID.bl_rna_get_subclass_py |

### References 

| bpy.context.armature BlendData.armatures | BlendDataArmatures.new BlendDataArmatures.remove |

# Filehandler Bpy Struct, Gpencil Ul Annotation Layer Uilist, Gpencil Ul Matslots Uilist, Grease Pencil Ul Attributes Uilist ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: FileHandler(bpy_struct); `GPENCIL_UL`_annotation_layer(UIList); `GPENCIL_UL`_matslots(UIList); `GREASE_PENCIL_UL`_attributes(UIList); `GREASE_PENCIL_UL`_masks(UIList); Header(bpy_struct).

## FileHandler(bpy_struct)

### FileHandler(bpy_struct)

### Basic FileHandler for importing a single file

Through a file handler you can attach custom drag-and-drop behavior to a particular Operator
(FileHandler.bl_import_operator) together with a list of file extensions
(FileHandler.bl_file_extensions). Which UI area is willing to receive the
drag-and-drop is decided by the FileHandler.poll_drop method.

Just like operators that open a file select window, an operator taking part in drag-and-drop while
handling only one file has to declare the property below:

`	ext
filepath: bpy.props.StringProperty(subtype='`FILE_PATH`', options={'`SKIP_SAVE`'})
`

Once the user drops a file, this filepath property receives that file's full path.

`	ext
import bpy

class CurveTextImport(bpy.types.Operator):
"""
Creates a text object from a text file.
"""
bl_idname = "curve.text_import"
bl_label = "Import a text file as text object"

### This Operator supports processing one `.txt` file at a time. The following file-path
### property must be defined.
filepath: bpy.props.StringProperty(subtype='`FILE_PATH`', options={'`SKIP_SAVE`'})

@classmethod
def poll(cls, context):
return (context.area and context.area.type == "`VIEW_3D`")

def execute(self, context):
### Direct calls to this Operator may use unsupported file-paths. Ensure the incoming
### file-path is one that is supported.
if not self.filepath or not self.filepath.endswith(".txt"):
return {'CANCELLED'}

### Create a Blender Text object from the contents of the provided file.
with open(self.filepath) as file:
text_curve = bpy.data.curves.new(type="FONT", name="Text")
text_curve.body = ''.join(file.readlines())
text_object = bpy.data.objects.new(name="Text", object_data=text_curve)
bpy.context.scene.collection.objects.link(text_object)
return {'FINISHED'}

### By default the file handler invokes the operator with the file-path property set. If the
### operator also supports being invoked with no file-path set, and allows the user to pick from a
### file select window instead, the following logic can be used.
#
### Note: It is important to use `options={'SKIP_SAVE'}` when defining the file-path property to
### avoid prior values from being reused on subsequent calls.

def invoke(self, context, event):
if self.filepath:
return self.execute(context)
context.window_manager.fileselect_add(self)
return {'`RUNNING_MODAL`'}

### Define a file handler that supports the following set of conditions:
### - Execute the `curve.text_import` operator
### - When `.txt` files are dropped in the 3D Viewport
class `CURVE_FH`_text_import(bpy.types.FileHandler):
bl_idname = "`CURVE_FH`_text_import"
bl_label = "File handler for curve text object import"
bl_import_operator = "curve.text_import"
bl_file_extensions = ".txt"

@classmethod
def poll_drop(cls, context):
return (context.area and context.area.type == '`VIEW_3D`')

bpy.utils.register_class(CurveTextImport)
bpy.utils.register_class(`CURVE_FH`_text_import)
`

### FileHandler for Importing multiple files and exposing Operator options

An operator that can run with several drag-and-dropped files at once needs these properties
declared:

`	ext
directory: StringProperty(subtype='`DIR_PATH`', options={'`SKIP_SAVE`', 'HIDDEN'})
files: CollectionProperty(type=OperatorFileListElement, options={'`SKIP_SAVE`', 'HIDDEN'})
`

The drag-and-drop operation fills these directory and files properties with the data it needs.

On top of that, when the operator exposes operator properties the user should be able to reach,
the ImportHelper.invoke_popup method can present a dialog that reuses the standard
Operator.draw method for its layout and display.

`	ext
import bpy
from bpy_extras.io_utils import ImportHelper
from mathutils import Vector

class ShaderScriptImport(bpy.types.Operator, ImportHelper):
"""
Creates one or more Shader Script nodes from text files.
"""
bl_idname = "shader.script_import"
bl_label = "Import a text file as a script node"

### This Operator supports processing multiple `.txt` files at a time. The following properties
### must be defined.
directory: bpy.props.StringProperty(subtype='`DIR_PATH`', options={'`SKIP_SAVE`', 'HIDDEN'})
files: bpy.props.CollectionProperty(type=bpy.types.OperatorFileListElement, options={'`SKIP_SAVE`', 'HIDDEN'})

### Allow the user to choose whether the node's label is set or not
set_label: bpy.props.BoolProperty(name="Set Label", default=False)

@classmethod
def poll(cls, context):
return (
context.region and context.region.type == 'WINDOW' and
context.area and context.area.ui_type == 'ShaderNodeTree' and
context.object and context.object.type == 'MESH' and
context.material
)

def execute(self, context):
### The directory property must be set.
if not self.directory:
return {'CANCELLED'}

x = 0.0
y = 0.0
for file in self.files:
### Direct calls to this Operator may use unsupported file-paths. Ensure the incoming
### files are ones that are supported.
if file.name.endswith(".txt"):
import os
filepath = os.path.join(self.directory, file.name)

node_tree = context.material.node_tree
text_node = node_tree.nodes.new(type="ShaderNodeScript")
text_node.mode = 'EXTERNAL'
text_node.filepath = filepath
text_node.location = Vector((x, y))

### Set the node's title to the file name.
if self.set_label:
text_node.label = file.name

x += 20.0
y -= 20.0

return {'FINISHED'}

### Use ImportHelper's invoke_popup() to handle the invocation so that this operator's properties
### are shown in a popup. This allows the user to configure additional settings on the operator
### like the `set_label` property. Consider having a draw() method on the operator in order to
### layout the properties in the UI appropriately.
#
### If filepath information is not provided the file select window will be invoked instead.

def invoke(self, context, event):
return self.invoke_popup(context)

### Define a file handler that supports the following set of conditions:
### - Execute the `shader.script_import` operator
### - When `.txt` files are dropped in the Shader Editor
class `SHADER_FH`_script_import(bpy.types.FileHandler):
bl_idname = "`SHADER_FH`_script_import"
bl_label = "File handler for shader script node import"
bl_import_operator = "shader.script_import"
bl_file_extensions = ".txt"

@classmethod
def poll_drop(cls, context):
return (
context.region and context.region.type == 'WINDOW' and
context.area and context.area.ui_type == 'ShaderNodeTree'
)

bpy.utils.register_class(ShaderScriptImport)
bpy.utils.register_class(`SHADER_FH`_script_import)
`

base class — bpy_struct

subclasses —
`IMAGE_FH`_drop_handler, `IO_FH`_gltf2, `IO_FH`_svg_as_curves, `NODE_FH`_image_node, `SEQUENCER_FH`_image_strip, `SEQUENCER_FH`_movie_strip, `SEQUENCER_FH`_sound_strip, `VIEW3D_FH`_camera_background_image, `VIEW3D_FH`_empty_image, `VIEW3D_FH`_vdb_volume

class bpy.types. FileHandler ( bpy_struct )

Adds extra capability to operators that work with files, including drag-and-drop support

bl_export_operator

Operator able to export files whose extensions are listed in bl_file_extensions (default “”, never None)

Type :

str

bl_file_extensions

A string listing the file extensions the file handler accepts; each one should begin with a “.” and be split apart by “;”.
For Example: ".blend;.ble"

(default “”, never None)

Type :

str

bl_idname

When set, gives the file handler a custom ID; otherwise it inherits the name of the class that defines it (so if the class is called “`OBJECT_FH`_hello” and the script leaves bl_idname unset, then bl_idname becomes “`OBJECT_FH`_hello”) (default “”, never None)

Type :

str

bl_import_operator

Operator able to import files whose extensions are listed in bl_file_extensions (default “”, never None)

Type :

str

bl_label

The label shown for the file handler (default “”, never None)

Type :

str

classmethod poll_drop ( context )

When this method returns True, it can be used to take over the drop of a drag-and-drop action

Return type :

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

## `GPENCIL_UL`_annotation_layer(UIList)

### `GPENCIL_UL`_annotation_layer(UIList)

base classes — bpy_struct, UIList

class bpy.types. `GPENCIL_UL`_annotation_layer ( UIList )

draw_item ( _context , layout , _data , item , _icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `GPENCIL_UL`_matslots(UIList)

### `GPENCIL_UL`_matslots(UIList)

base classes — bpy_struct, UIList

class bpy.types. `GPENCIL_UL`_matslots ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `GREASE_PENCIL_UL`_attributes(UIList)

### `GREASE_PENCIL_UL`_attributes(UIList)

base classes — bpy_struct, UIList

class bpy.types. `GREASE_PENCIL_UL`_attributes ( UIList )

draw_item ( _context , layout , _data , attribute , _icon , _active_data , _active_propname , _index )

filter_items ( _context , data , property )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `GREASE_PENCIL_UL`_masks(UIList)

### `GREASE_PENCIL_UL`_masks(UIList)

base classes — bpy_struct, UIList

class bpy.types. `GREASE_PENCIL_UL`_masks ( UIList )

draw_item ( _context , layout , _data , item , icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## Header(bpy_struct)

### Header(bpy_struct)

base class — bpy_struct

class bpy.types. Header ( bpy_struct )

Holds the UI widgets that make up an editor's header bar.

bl_idname

Set this to give the header a custom ID; leave it unset and the defining class name is used instead. So with a class named "`OBJECT_HT`_hello" and no bl_idname in the script, bl_idname = "`OBJECT_HT`_hello" (default "", never None)

Type :

str

bl_region_type

The region where the header is going to be used in (defaults to header region) (default 'HEADER' )

Type :

Literal[Region Type Items]

bl_space_type

The space where the header is going to be used in (default 'EMPTY' )

Type :

Literal[Space Type Items]

layout

Structure of the header in the UI (readonly)

Type :

UILayout

draw ( context )

Draw UI elements into the header UI layout

classmethod append ( draw_func )

Append a draw function to this menu,
takes the same arguments as the menus draw function

classmethod is_extended ( )

classmethod prepend ( draw_func )

Prepend a draw function to this menu, takes the same arguments as
the menus draw function

classmethod remove ( draw_func )

Remove a draw function that has been added to this menu.

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

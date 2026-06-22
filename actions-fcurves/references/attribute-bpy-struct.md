# Attribute Bpy Struct, Attributegroupcurves Bpy Prop Collection, Attributegroupgreasepencil Bpy Prop Collection, Attributegroupgreasepencildrawing Bpy Prop Collection ...

> Blender Actions, F-Curves, and Animation reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Attribute(bpy_struct); AttributeGroupCurves(bpy_prop_collection); AttributeGroupGreasePencil(bpy_prop_collection); AttributeGroupGreasePencilDrawing(bpy_prop_collection); AttributeGroupPointCloud(bpy_prop_collection); BezierSplinePoint(bpy_struct); BlendDataActions(bpy_prop_collection); BlendDataAnnotations(bpy_prop_collection).

## Attribute(bpy_struct)

A data channel attached to geometry elements.

Attributes store information tied to vertices, edges, faces, or other geometry components.
Each attribute has a name, a type, and is stored on a specific domain.

label
The assigned name of this attribute. Names are distinct within a given geometry.
If the label starts with a . , the attribute remains hidden in the user interface.

format
What kind of values this attribute holds, like floating-point, integer, color, and so forth.
See Attribute Type Items.

geometry_domain
The geometry area where the attribute is stored.
See Attribute Domain Items.

### Handling Attributes 

Attributes can be stored on geometries like Mesh, Curves, PointCloud, etc.
These geometries have attribute groups (usually called attributes ).
Using the groups, attributes can then be accessed by their label:

`\text
radii = curves.attributes["radius"]
`

Adding and storing user attributes is done using the attributes.new function:

`\text
### Add a new attribute labeled `my_attribute_name` of type `float` on the point domain of the geometry.
my_attribute = curves.attributes.new("my_attribute_name", 'FLOAT', 'POINT')
`

Deleting attributes can be done like so:

`\text
attribute = drawing.attributes["some_attribute"]
drawing.attributes.remove(attribute)
`

Note

Some attributes are required and cannot be removed, like "position" .

Attribute values are read by accessing their attribute.data collection property.
However, in cases where multiple values should be read at once,
it is better to use the bpy_prop_collection.foreach_get function and read the values into a numpy buffer.

`\text
import numpy as np

### Get the radius attribute.
radii = curves.attributes["radius"]
### Print the radius of the first point.
print(radii.data[0].value)
### Output: 0.005

### Get the total number of points.
num_points = attributes.domain_size('POINT')
### Create an empty buffer to read all the radii into.
radii_data = np.zeros(num_points, dtype=np.float32)
### Read all the radii of the curves into `radii_data` at once.
radii.data.foreach_get('value', radii_data)
### Print all the radii.
print(radii_data)
### Output: [0.1, 0.2, 0.3, 0.4, ... ]
`

Note

Some attribute types use different named properties to access their value.
Instead of value , vectors use vector , and colors use color .

Writing to different attribute types is very similar. You can simply assign to a value directly.
Again, when writing to multiple values, it is recommended to use the bpy_prop_collection.foreach_set function
to write the values from a numpy buffer.

`\text
import numpy as np

radii = curves.attributes["radius"]
### Write a radius with a value of 0.5 to the first point.
radii.data[0].value = 0.5
print(radii.data[0].value)
### Output: 0.5

num_points = attributes.domain_size('POINT')
### Generate random radii with values between 0.001 and 0.05 using numpy.
new_radii = np.random.uniform(0.001, 0.05, num_points)
### Write the new radii to the radius attribute.
radii.data.foreach_set('value', new_radii)
`

The bpy_prop_collection.foreach_get / bpy_prop_collection.foreach_set methods require a flat array.
This is sometimes not desirable, e.g. when reading/writing positions, which are 3D vectors.
In these cases, it's possible to use np.ravel to pass the data as a flat array:

`\text
num_points = attributes.domain_size('POINT')
positions = curves.attributes['position']
### Here, we're using a numpy array with shape (num_points, 3) so that each
### element is a 3d vector.
positions_data = np.zeros((num_points, 3), dtype=np.float32)
### The `np.ravel` function will pass the `positions_data` as a flat array
### without changing the original shape.
positions.data.foreach_get('vector', np.ravel(positions_data))
print(positions_data)
### Output: [[0.1, 0.2, 0.3], [0.4, 0.5, 0.6], ...]
`

base class — bpy_struct

subclasses —
BoolAttribute, ByteColorAttribute, ByteIntAttribute, Float2Attribute, Float4x4Attribute, FloatAttribute, FloatColorAttribute, FloatVectorAttribute, Int2Attribute, IntAttribute, QuaternionAttribute, Short2Attribute, StringAttribute

class bpy.types. Attribute ( bpy_struct )

Geometry attribute

data_type

Type of data stored in attribute (default 'FLOAT' , readonly)

Type :

Literal[Attribute Type Items]

domain

Domain of the Attribute (default 'POINT' , readonly)

Type :

Literal[Attribute Domain Items]

is_internal

The attribute is meant for internal use by Blender (default False, readonly)

Type :

bool

is_required

Whether the attribute can be removed or renamed (default False, readonly)

Type :

bool

name

Name of the Attribute (default "", never None)

Type :

str

storage_type

Method used to store the data (default 'ARRAY' , readonly)

Type :

Literal[Attr Storage Type Items]

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

| AttributeGroupCurves.active AttributeGroupCurves.new AttributeGroupCurves.remove AttributeGroupGreasePencil.active AttributeGroupGreasePencil.new AttributeGroupGreasePencil.remove AttributeGroupGreasePencilDrawing.active AttributeGroupGreasePencilDrawing.new AttributeGroupGreasePencilDrawing.remove AttributeGroupMesh.active AttributeGroupMesh.active_color AttributeGroupMesh.new AttributeGroupMesh.remove | AttributeGroupPointCloud.active AttributeGroupPointCloud.new AttributeGroupPointCloud.remove Curves.attributes Curves.color_attributes GreasePencil.attributes GreasePencil.color_attributes GreasePencilDrawing.attributes GreasePencilDrawing.color_attributes Mesh.attributes Mesh.color_attributes PointCloud.attributes PointCloud.color_attributes |

## AttributeGroupCurves(bpy_prop_collection)

Collection of geometry attributes on curves.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AttributeGroupCurves ( bpy_prop_collection )

Container of per-element data channels.

active

Active attribute

Type :

Attribute

active_index

Active attribute index or -1 when none are active (in [-1, inf], default 0)

Type :

int

new ( name , type , domain )

Attach an attribute to geometry.

Parameters :

- name ( str ) – Name, Name of geometry attribute (never None)

- type (Literal[Attribute Type Items]) – Type, Attribute type

- domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

New geometry attribute

Return type :

Attribute

remove ( attribute )

Detach an attribute from geometry.

Parameters :

attribute (Attribute) – Geometry Attribute (never None)

domain_size ( domain )

Get the number of elements in a domain.

Parameters :

domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

Size, Size of the domain (in [0, inf])

Return type :

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

| Curves.attributes | Curves.color_attributes |

## AttributeGroupGreasePencil(bpy_prop_collection)

Collection of geometry attributes on grease pencil.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AttributeGroupGreasePencil ( bpy_prop_collection )

Container of per-element data channels.

active

Active attribute

Type :

Attribute

active_index

Active attribute index or -1 when none are active (in [-1, inf], default 0)

Type :

int

new ( name , type , domain )

Attach an attribute to geometry.

Parameters :

- name ( str ) – Name, Name of geometry attribute (never None)

- type (Literal[Attribute Type Items]) – Type, Attribute type

- domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

New geometry attribute

Return type :

Attribute

remove ( attribute )

Detach an attribute from geometry.

Parameters :

attribute (Attribute) – Geometry Attribute (never None)

domain_size ( domain )

Get the number of elements in a domain.

Parameters :

domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

Size, Size of the domain (in [0, inf])

Return type :

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

| GreasePencil.attributes | GreasePencil.color_attributes |

## AttributeGroupGreasePencilDrawing(bpy_prop_collection)

Collection of geometry attributes on grease pencil drawing.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AttributeGroupGreasePencilDrawing ( bpy_prop_collection )

Container of per-element data channels.

active

Active attribute

Type :

Attribute

active_index

Active attribute index or -1 when none are active (in [-1, inf], default 0)

Type :

int

new ( name , type , domain )

Attach an attribute to geometry.

Parameters :

- name ( str ) – Name, Name of geometry attribute (never None)

- type (Literal[Attribute Type Items]) – Type, Attribute type

- domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

New geometry attribute

Return type :

Attribute

remove ( attribute )

Detach an attribute from geometry.

Parameters :

attribute (Attribute) – Geometry Attribute (never None)

domain_size ( domain )

Get the number of elements in a domain.

Parameters :

domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

Size, Size of the domain (in [0, inf])

Return type :

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

| GreasePencilDrawing.attributes | GreasePencilDrawing.color_attributes |

## AttributeGroupPointCloud(bpy_prop_collection)

This Python-API class represents a collection of geometry attributes for point cloud objects.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. AttributeGroupPointCloud ( bpy_prop_collection )

Manages point cloud geometry attribute groupings

active 

The currently selected attribute

Type :

Attribute

active_index 

Index position of the currently selected attribute, or -1 when nothing is active (in [-1, inf], default 0)

Type :

int

new ( name , type , domain ) 

Create and attach a new attribute to the geometry

Parameters :

- name ( str ) – Name, Name of geometry attribute (never None)

- type (Literal[Attribute Type Items]) – Type, Attribute type

- domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

New geometry attribute

Return type :

Attribute

remove ( attribute ) 

Delete an attribute from the geometry

Parameters :

attribute (Attribute) – Geometry Attribute (never None)

domain_size ( domain ) 

Query the size of a specified domain

Parameters :

domain (Literal[Attribute Domain Items]) – Domain, Type of element that attribute is stored on

Returns :

Size, Size of the domain (in [0, inf])

Return type :

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

| PointCloud.attributes | PointCloud.color_attributes |

## BezierSplinePoint(bpy_struct)

Spline anchor point with directional tangent handles for curve control.

base class — bpy_struct

class bpy.types. BezierSplinePoint ( bpy_struct )

Control point on a Bézier curve with attached tangent vector handles

co 

Location of the anchor point in 3D space (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

handle_left 

Position of the incoming tangent handle (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

handle_left_type 

Behavior mode for the incoming handle (default 'FREE' )

Type :

Literal['FREE', 'VECTOR', 'ALIGNED', 'AUTO']

handle_right 

Position of the outgoing tangent handle (array of 3 items, in [-inf, inf], default (0.0, 0.0, 0.0))

Type :

mathutils.Vector

handle_right_type 

Behavior mode for the outgoing handle (default 'FREE' )

Type :

Literal['FREE', 'VECTOR', 'ALIGNED', 'AUTO']

hide 

Whether the point is concealed (default False)

Type :

bool

radius 

Thickness value for extrusion along the curve (in [0, inf], default 0.0)

Type :

float

select_control_point 

Whether the anchor point is selected (default False)

Type :

bool

select_left_handle 

Whether the incoming handle is selected (default False)

Type :

bool

select_right_handle 

Whether the outgoing handle is selected (default False)

Type :

bool

tilt 

Rotational twisting along the curve direction (in [-376.991, 376.991], default 0.0)

Type :

float

weight_softbody 

Influence on softbody simulation (in [0.01, 100], default 0.0)

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

| bpy_struct.id_data | |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References 

| Spline.bezier_points | |

## BlendDataActions(bpy_prop_collection)

Enumeration of drawing annotation records.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataAnnotations ( bpy_prop_collection )

List of annotation sketches

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

new ( name ) 

Create a new annotation in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New annotation data-block

Return type :

Annotation

remove ( annotation , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Erase an annotation from the current file

Parameters :

- annotation (Annotation) – Grease Pencil to remove (never None)

- do_unlink ( bool ) – Break all references to this annotation before deletion (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

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

| BlendData.annotations | |

## BlendDataAnnotations(bpy_prop_collection)

Registry of skeletal rig definitions.

base classes — bpy_prop, bpy_prop_collection

class bpy.types. BlendDataArmatures ( bpy_prop_collection )

List of skeletal deformation rigs

new ( name ) 

Register a new armature in the database

Parameters :

name ( str ) – New name for the data-block (never None)

Returns :

New armature data-block

Return type :

Armature

remove ( armature , * , do_unlink = True , do_id_user = True , do_ui_user = True ) 

Unregister an armature from the current file

Parameters :

- armature (Armature) – Armature to remove (never None)

- do_unlink ( bool ) – Break all references to this armature before deletion (WARNING: will also delete objects instancing that armature data) (optional)

- do_id_user ( bool ) – Reduce user count for all data-blocks used (optional)

- do_ui_user ( bool ) – Ensure the interface is updated (optional)

tag ( value ) 

tag

Parameters :

value ( bool ) – Value

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

| BlendData.armatures | |

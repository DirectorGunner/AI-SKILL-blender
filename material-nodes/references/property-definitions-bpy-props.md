# Property Definitions Bpy Props (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Property Definitions (bpy.props) 

This unit establishes qualities to elongate Blender's interior material. The result of these operations is utilized to attribute qualities to groupings enlisted with Blender and cannot be utilized immediately.

Note

Every input to these operations must be transmitted as named.

### Assigning to Existing Classes 

Tailored qualities can be supplied to every subclass of an ID ,
Bone and PoseBone .

These qualities can be shifted, obtained by the client contact and Python
like Blender's pre-existing qualities.

Warning

Gain to these qualities might occur in concurrent framework, on a per-material-section basis.
This must be attentively examined when applying accessors or upgrade functions.

Customarily, these functions should not change every other information that the one managed by their material-section.
When acquiring outside non-Blender material, concurrent protection procedures must be examined.

`\text
import bpy

### Assign a custom property to an existing type.
bpy.types.Material.custom_float = bpy.props.FloatProperty(name="Test Property")

### Test the property is there.
bpy.data.materials[0].custom_float = 5.0
`

### Operator Example 

A widespread application of tailored qualities is for Python based Operator
groupings. Examine this regulation by operating it in the manuscript editor, or by selecting the
switch in the 3D Display's Apparatus section. The previous will display the qualities
in the Redo portion and let you modify them.

`\text
import bpy

class `OBJECT_OT`_property_example(bpy.types.Operator):
bl_idname = "object.property_example"
bl_label = "Property Example"
bl_options = {'REGISTER', 'UNDO'}

my_float: bpy.props.FloatProperty(name="Some Floating Point")
my_bool: bpy.props.BoolProperty(name="Toggle Option")
my_string: bpy.props.StringProperty(name="String Value")

def execute(self, context):
self.report(
{'INFO'}, "F: {:.2f} B: {!s} S: {!r}".format(
self.my_float, self.my_bool, self.my_string,
)
)
print('My float:', self.my_float)
print('My bool:', self.my_bool)
print('My string:', self.my_string)
return {'FINISHED'}

class `OBJECT_PT`_property_example(bpy.types.Panel):
bl_idname = "object_PT_property_example"
bl_label = "Property Example"
bl_space_type = '`VIEW_3D`'
bl_region_type = 'UI'
bl_category = "Tool"

def draw(self, context):
### You can set the property values that should be used when the user
### presses the button in the UI.
props = self.layout.operator('object.property_example')
props.my_bool = True
props.my_string = "Shouldn't that be 47?"

### You can set properties dynamically:
if context.object:
props.my_float = context.object.location.x
else:
props.my_float = 327

bpy.utils.register_class(`OBJECT_OT`_property_example)
bpy.utils.register_class(`OBJECT_PT`_property_example)

### Demo call. Be sure to also test in the 3D Viewport.
bpy.ops.object.property_example(
my_float=47,
my_bool=True,
my_string="Shouldn't that be 327?",
)
`

### PropertyGroup Example 

PropertyGroups can be utilized for gathering tailored adjustments into sole worth
to prevent numerous distinctive adjustments combined altogether.

`\text
import bpy

class MaterialSettings(bpy.types.PropertyGroup):
my_int: bpy.props.IntProperty()
my_float: bpy.props.FloatProperty()
my_string: bpy.props.StringProperty()

bpy.utils.register_class(MaterialSettings)

bpy.types.Material.my_settings = bpy.props.PointerProperty(type=MaterialSettings)

### Test the new settings work.
material = bpy.data.materials[0]

material.my_settings.my_int = 5
material.my_settings.my_float = 3.0
material.my_settings.my_string = "Foo"
`

### Collection Example 

Tailored qualities can be supplied to every subclass of an ID ,
Bone and PoseBone .

`\text
import bpy

### Assign a collection.
class SceneSettingItem(bpy.types.PropertyGroup):
name: bpy.props.StringProperty(name="Test Property", default="Unknown")
value: bpy.props.IntProperty(name="Test Property", default=22)

bpy.utils.register_class(SceneSettingItem)

bpy.types.Scene.my_settings = bpy.props.CollectionProperty(type=SceneSettingItem)

### Assume an armature object selected.
print("Adding 2 values!")

my_item = bpy.context.scene.my_settings.add()
my_item.name = "Spam"
my_item.value = 1000

my_item = bpy.context.scene.my_settings.add()
my_item.name = "Eggs"
my_item.value = 30

for my_item in bpy.context.scene.my_settings:
print(my_item.name, my_item.value)
`

### Update Example 

It can be advantageous to do an operation when a quality is moved and may be
utilized to refresh other qualities or link with external information.

Every qualities specify upgrade operations excluding for CollectionProperty.

Warning

Keep in mind that these functions may be carried out in concurrent framework.

Warning

If the quality is part of an Operator, the upgrade operation's opening
factor will be an OperatorProperties case, rather than an case
of the tool itself. This implies you cannot obtain additional inner functions
of the tool, merely its additional qualities.

`\text
import bpy

def update_func(self, context):
print("my test function", self)

bpy.types.Scene.testprop = bpy.props.FloatProperty(update=update_func)

bpy.context.scene.testprop = 11.0

### >>> my test function
`

### Getter/Setter Example 

Accessor operations may be utilized for boolean, integer, floating point, sequence and pick qualities.

If get or set functions are laid out, the quality will not be held in the ID qualities
instantly. Rather, the get and set operations will be termed when the quality
is correspondingly examined or penned from the interface, and are answerable to handle the information retention.

Keep in mind that:

- It is improper to lay out a set operation without a coordinating get single.

- When a get operation is laid out but no set sole, the quality is read-only.

get_transform and set_transform may be utilized when the yielded worth must be improved,
yet the ordinary interior retention is yet applied. They may exclusively modify the worth before it is
prepared or supplied, yet do not manage how/where that material is held.

Note

It is feasible to lay out both get / set and get_transform / set_transform operations
for the matching quality. In application, yet, this must infrequently be wanted, as almost all 'modify'
procedure may additionally occur within a get / set operation.

Warning

Keep in mind that these functions may be carried out in concurrent framework.

Warning

Take caution when obtaining further qualities in these operations, as it may quickly set off
difficult matters, for instance unending patterns (if e.g. two qualities strive to additionally prepare the alternate
quality's worth in their own set operation), or unexpected side-effects due to shifts
in information, prompted e.g. by an upgrade operation.

`\text
import bpy

scene = bpy.context.scene

### Simple property reading/writing from 'custom' IDProperties.
### This is similar to what the RNA would do internally, albeit using it own separate,
### internal 'system' IDProperty storage, since Blender 5.0.
def get_float(self):
return self.get("testprop", 0.0)

def set_float(self, value):
self["testprop"] = value

bpy.types.Scene.test_float = bpy.props.FloatProperty(get=get_float, set=set_float)

### Testing the property:
print("test_float:", scene.test_float)
scene.test_float = 7.5
print("test_float:", scene.test_float)

### The above outputs:
### test_float: 0.0
### test_float: 7.5

### Read-only string property, returns the current date.
def get_date(self):
import datetime
return str(datetime.datetime.now())

bpy.types.Scene.test_date = bpy.props.StringProperty(get=get_date)

### Testing the property:
### scene.test_date = "blah" # This would fail, property is read-only.
print("test_date:", scene.test_date)

### The above outputs something like:
### test_date: 2018-03-14 11:36:53.158653

### Boolean array.
### - Set function stores a single boolean value, returned as the second component.
### - Array getters must return a list or tuple.
### - Array size must match the property vector size exactly.
def get_array(self):
return (True, self.get("somebool", True))

def set_array(self, values):
self["somebool"] = values[0] and values[1]

bpy.types.Scene.test_array = bpy.props.BoolVectorProperty(size=2, get=get_array, set=set_array)

### Testing the property:
print("test_array:", tuple(scene.test_array))
scene.test_array = (True, False)
print("test_array:", tuple(scene.test_array))

### The above outputs:
### test_array: (True, True)
### test_array: (True, False)

### Boolean array, using 'transform' accessors.
### Note how the same result is achieved as with previous get/set example, but using default RNA storage.
### Transform accessors also have access to more information.
### Also note how the stored data _is_ a two-items array.
### - Set function stores a single boolean value, returned as the second component.
### - Array getters must return a list or tuple.
### - Array size must match the property vector size exactly.
def get_array_transform(self, curr_value, is_set):
print("Stored data:", curr_value, "(is set:", is_set, ")")
return (True, curr_value[1])

def set_array_transform(self, new_value, curr_value, is_set):
print("New data:", new_value, "; Stored data:", curr_value, "(is set:", is_set, ")")
return True, new_value[0] and new_value[1]

bpy.types.Scene.test_array_transform = bpy.props.BoolVectorProperty(
size=2, get_transform=get_array_transform, set_transform=set_array_transform)

### Testing the property:
print("test_array_transform:", tuple(scene.test_array_transform))
scene.test_array_transform = (True, False)
print("test_array_transform:", tuple(scene.test_array_transform))

### The above outputs:
### Stored data: (False, False) (is set: False )
### test_array_transform: (True, False)
### New data: (True, False) ; Stored data: (False, False) (is set: False )
### Stored data: (True, False) (is set: True )
### test_array_transform: (True, False)

### Enum property.
### Note: the getter/setter callback must use integer identifiers!
test_items = [
("RED", "Red", "", 1),
("GREEN", "Green", "", 2),
("BLUE", "Blue", "", 3),
("YELLOW", "Yellow", "", 4),
]

def get_enum(self):
import random
return random.randint(1, 4)

def set_enum(self, value):
print("setting value", value)

bpy.types.Scene.test_enum = bpy.props.EnumProperty(items=test_items, get=get_enum, set=set_enum)

### Testing the property:
print("test_enum:", scene.test_enum)
scene.test_enum = 'BLUE'
print("test_enum:", scene.test_enum)

### The above outputs something like:
### test_enum: YELLOW
### setting value 3
### test_enum: GREEN

### String, using 'transform' accessors to validate data before setting/returning it.
def get_string_transform(self, curr_value, is_set):
import os
is_valid_path = os.path.exists(curr_value)
print("Stored data:", curr_value, "(is set:", is_set, ", is valid path:", is_valid_path, ")")
return curr_value if is_valid_path else ""

def set_string_transform(self, new_value, curr_value, is_set):
import os
is_valid_path = os.path.exists(new_value)
print("New data:", new_value, "(is_valid_path:", is_valid_path, ");",
"Stored data:", curr_value, "(is set:", is_set, ")")
return new_value if is_valid_path else curr_value

bpy.types.Scene.test_string_transform = bpy.props.StringProperty(
subtype='`DIR_PATH`',
default="an/invalid/path",
get_transform=get_string_transform,
set_transform=set_string_transform,
)

### Testing the property:
print("test_string_transform:", scene.test_string_transform)
scene.test_string_transform = "try\\to\\find\\me"
print("test_string_transform:", scene.test_string_transform)

### The above outputs something like:
### Stored data: an/invalid/path (is set: False , is valid path: False )
### test_string_transform:
### New data: try\to\find\me (is_valid_path: False ) ; Stored data: an/invalid/path (is set: False )
### Stored data: an/invalid/path (is set: True , is valid path: False )
### test_string_transform:
`

bpy.props. BoolProperty ( * , name = '' , description = '' , translation_context = '*' , default = False , options = {'ANIMATABLE'} , override = set() , tags = set() , subtype = 'NONE' , update = None , get = None , set = None , get_transform = None , set_transform = None ) 

Returns a fresh boolean quality specification.

Parameters :

- name ( str ) – Name applied in the client contact.

- description ( str ) – Message applied for the hint and interface documentation.

- translation_context ( str ) – Message applied as situation to clear interpretation translations.

- default ( bool ) – The fundamental worth for this quality.

- options ( set [ str ] ) – Enumerator in Property Flag Items.

- override ( set [ str ] ) – Enumerator in Property Override Flag Items.

- tags ( set [ str ] ) – Enumerator of labels that are fixed by ancestor grouping.

- subtype ( str ) – Enumerator in Property Subtype Number Items.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Operation to be termed when this worth is modified,
This operation must assume 2 principles (self, context) and deliver None.
Caution there are no protection verifications to resist unending repetition.

- get (Callable[[bpy.types.bpy_struct], bool] | None) – Operation to be termed when this worth is 'examined', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 1 principle (self) and deliver the worth of the quality.

Note

Laying out this operation without a coordinating prepare single will create the quality read-only (even if `READ_ONLY` choice is not fixed).

- set (Callable[[bpy.types.bpy_struct, bool], None] | None) – Operation to be termed when this worth is 'penned', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 2 principles (self, value) and deliver None.

Note

Laying out this operation without a coordinating get single is incorrectly.

- get_transform (Callable[[bpy.types.bpy_struct, bool, bool], bool] | None) – Operation to be termed when this worth is 'examined',
if several extra handling must be managed on the held worth.
This operation must assume trio premises (self, the held worth,
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

Note

The operation is accountable to guarantee that worth boundaries of the quality (min/max, span…) are honored. Else a ValueError exception is elevated.

- set_transform (Callable[[bpy.types.bpy_struct, bool, bool, bool], bool] | None) – Operation to be termed when this worth is 'penned',
if several extra handling must be managed on the granted worth before keeping it.
This operation must assume quaternary premises (self, the granted worth to keep,
the currently held worth ('raw' worth, without every get_transform used to it),
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

Note

The operation is accountable to guarantee that worth boundaries (min/max, span…) are honored. Else a ValueError exception is elevated.

Returns :

Opaque category applied for joining.

Return type :

_PropertyDeferred

bpy.props. BoolVectorProperty ( * , name = '' , description = '' , translation_context = '*' , default = (False, False, False) , options = {'ANIMATABLE'} , override = set() , tags = set() , subtype = 'NONE' , size = 3 , update = None , get = None , set = None , get_transform = None , set_transform = None )

Returns a fresh vector boolean quality specification.

Parameters :

- name ( str ) – Name applied in the client contact.

- description ( str ) – Message applied for the hint and interface documentation.

- translation_context ( str ) – Message applied as situation to clear interpretation translations.

- default ( Sequence [ bool ] ) – row of booleans the span of measurement .

- options ( set [ str ] ) – Enumerator in Property Flag Items.

- override ( set [ str ] ) – Enumerator in Property Override Flag Items.

- tags ( set [ str ] ) – Enumerator of labels that are fixed by ancestor grouping.

- subtype ( str ) – Enumerator in Property Subtype Number Array Items.

- size ( int | Sequence [ int ] ) – Vector dimensions in [1, 32]. An int row can be utilized to lay out multi-measurement groupings.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Operation to be termed when this worth is modified,
This operation must assume 2 principles (self, context) and deliver None.
Caution there are no protection verifications to resist unending repetition.

- get (Callable[[bpy.types.bpy_struct], Sequence[bool]] | None) – Operation to be termed when this worth is 'examined', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 1 principle (self) and deliver the worth of the quality.

Note

Laying out this operation without a coordinating prepare single will create the quality read-only (even if `READ_ONLY` choice is not fixed).

- set (Callable[[bpy.types.bpy_struct, tuple[bool, …]], None] | None) – Operation to be termed when this worth is 'penned', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 2 principles (self, value) and deliver None.

Note

Laying out this operation without a coordinating get single is incorrectly.

- get_transform (Callable[[bpy.types.bpy_struct, Sequence[bool], bool], Sequence[bool]] | None) – Operation to be termed when this worth is 'examined',
if several extra handling must be managed on the held worth.
This operation must assume trio premises (self, the held worth,
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

Note

The operation is accountable to guarantee that worth boundaries of the quality (min/max, span…) are honored. Else a ValueError exception is elevated.

- set_transform (Callable[[bpy.types.bpy_struct, Sequence[bool], Sequence[bool], bool], Sequence[bool]] | None) – Operation to be termed when this worth is 'penned',
if several extra handling must be managed on the granted worth before keeping it.
This operation must assume quaternary premises (self, the granted worth to keep,
the currently held worth ('raw' worth, without every get_transform used to it),
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

Note

The operation is accountable to guarantee that worth boundaries (min/max, span…) are honored. Else a ValueError exception is elevated.

Returns :

Opaque category applied for joining.

Return type :

_PropertyDeferred

bpy.props. CollectionProperty ( type , * , name = '' , description = '' , translation_context = '*' , options = {'ANIMATABLE'} , override = set() , tags = set() ) 

Returns a fresh grouping quality specification.

Parameters :

- type (type[bpy.types.PropertyGroup]) – A subclass of a quality batch.

- name ( str ) – Name applied in the client contact.

- description ( str ) – Message applied for the hint and interface documentation.

- translation_context ( str ) – Message applied as situation to clear interpretation translations.

- options ( set [ str ] ) – Enumerator in Property Flag Items.

- override ( set [ str ] ) – Enumerator in Property Override Flag Collection Items.

- tags ( set [ str ] ) – Enumerator of labels that are fixed by ancestor grouping.

Returns :

Opaque category applied for joining.

Return type :

_PropertyDeferred

bpy.props. EnumProperty ( items , * , name = '' , description = '' , translation_context = '*' , default = None , options = {'ANIMATABLE'} , override = set() , tags = set() , update = None , get = None , set = None , get_transform = None , set_transform = None ) 

Returns a fresh enumerator quality specification.

Parameters :

- items (Iterable[tuple[str, str, str] | tuple[str, str, str, int] | tuple[str, str, str, str | int, int] | None] | Callable[[bpy.types.bpy_struct, bpy.types.Context | None], Iterable[tuple[str, str, str] | tuple[str, str, str, int] | tuple[str, str, str, str | int, int] | None]]) – row of pick options arranged:
[(identifier, name, description, icon, number), ...] .

The opening trio components of the groupings are mandatory.

identifier :

The identifier is utilized for Python admission.
An vacant identifier implies that the entry is a divider

name :

Name for the contact.

description :

Applied for guidance and hints.

icon :

An icon sequence identifier or integer icon worth
(e.g. yielded by bpy.types.UILayout.icon)

number :

Distinctive worth utilized as the identifier for this entry (held in file information).
Apply when the identifier might require change. If the `ENUM_FLAG` choice is utilized,
the principles are bit-covers and must be ranks of binary.

When an entry merely has 4 entries they lay out (identifier, name, description, number) .

Dividers may be included applying either None (nameless divider),
or a standard entry grouping with a vacant identifier sequence, in which situation the title,
if non-vacant, will be shown in the contact above the divider line.
For movable principles a request may be transmitted which yields a set in
the matching arrangement as the static set.
This operation must assume 2 premises (self, context) , context may be None .

Warning

There is a recognized issue with applying a request,
Python must maintain a mention to the sequences yielded by the request or Blender
will perform irregularly or even shut down.

- name ( str ) – Name applied in the client contact.

- description ( str ) – Message applied for the hint and interface documentation.

- translation_context ( str ) – Message applied as situation to clear interpretation translations.

# Property Definitions Bpy Props (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

- default ( str | int | set [ str ] | None ) – The fundamental worth for this pick, a sequence from the identifiers utilized in items , or integer fitting an entry figure.
If the `ENUM_FLAG` choice is utilized this must be a gather of such sequence identifiers instead.
CAUTION: Sequences cannot be laid out for movable picks
(i.e. if a request operation is granted as items input).

- options ( set [ str ] ) – Enumerator in Property Flag Enum Items.

- override ( set [ str ] ) – Enumerator in Property Override Flag Items.

- tags ( set [ str ] ) – Enumerator of labels that are fixed by ancestor grouping.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Operation to be termed when this worth is modified,
This operation must assume 2 principles (self, context) and deliver None.
Caution there are no protection verifications to resist unending repetition.

- get (Callable[[bpy.types.bpy_struct], int] | None) – Operation to be termed when this worth is 'examined', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 1 principle (self) and deliver the worth of the quality.

Note

Laying out this operation without a coordinating prepare single will create the quality read-only (even if `READ_ONLY` choice is not fixed).

- set (Callable[[bpy.types.bpy_struct, int], None] | None) – Operation to be termed when this worth is 'penned', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 2 principles (self, value) and deliver None.

Note

Laying out this operation without a coordinating get single is incorrectly.

- get_transform (Callable[[bpy.types.bpy_struct, int, bool], int] | None) – Operation to be termed when this worth is 'examined',
if several extra handling must be managed on the held worth.
This operation must assume trio premises (self, the held worth,
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

Note

The operation is accountable to guarantee that worth boundaries of the quality (min/max, span…) are honored. Else a ValueError exception is elevated.

- set_transform (Callable[[bpy.types.bpy_struct, int, int, bool], int] | None) – Operation to be termed when this worth is 'penned',
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

bpy.props. FloatProperty ( * , name = '' , description = '' , translation_context = '*' , default = 0.0 , min = -3.402823e+38 , max = 3.402823e+38 , soft_min = -3.402823e+38 , soft_max = 3.402823e+38 , step = 3 , precision = 2 , options = {'ANIMATABLE'} , override = set() , tags = set() , subtype = 'NONE' , unit = 'NONE' , update = None , get = None , set = None , get_transform = None , set_transform = None ) 

Returns a fresh floating point (one accuracy) quality specification.

Parameters :

- name ( str ) – Name applied in the client contact.

- description ( str ) – Message applied for the hint and interface documentation.

- translation_context ( str ) – Message applied as situation to clear interpretation translations.

- default ( float ) – The fundamental worth for this quality.

- min ( float ) – Firm bottom, seeking to appoint a worth below will silently appoint this bottom rather.

- max ( float ) – Firm upper bound, seeking to appoint a worth greater will silently appoint this upper bound rather.

- soft_min ( float ) – Tender bottom (>= min ), consumer will not be capable to move the gadget below this worth in the contact.

- soft_max ( float ) – Tender upper bound (<= max ), consumer will not be capable to move the gadget greater this worth in the contact.

- step ( float ) – Change of growth/loss in contact, in [1, 100], fixes to 3 (ALERT: genuine worth is /100).

- precision ( int ) – Peak quantity of fractional numbers to demonstrate, in [0, 6]. Divisor is instantly concealed for rigorous integer principles of sections with measurement 'NONE' or 'TIME' (frame count) and change divisible by 100.

- options ( set [ str ] ) – Enumerator in Property Flag Items.

- override ( set [ str ] ) – Enumerator in Property Override Flag Items.

- tags ( set [ str ] ) – Enumerator of labels that are fixed by ancestor grouping.

- subtype ( str ) – Enumerator in Property Subtype Number Items.

- unit ( str ) – Enumerator in Property Unit Items.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Operation to be termed when this worth is modified,
This operation must assume 2 principles (self, context) and deliver None.
Caution there are no protection verifications to resist unending repetition.

- get (Callable[[bpy.types.bpy_struct], float] | None) – Operation to be termed when this worth is 'examined', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 1 principle (self) and deliver the worth of the quality.

Note

Laying out this operation without a coordinating prepare single will create the quality read-only (even if `READ_ONLY` choice is not fixed).

- set (Callable[[bpy.types.bpy_struct, float], None] | None) – Operation to be termed when this worth is 'penned', and the fundamental,
arrangement-laid out retention is not utilized for this quality.
This operation must assume 2 principles (self, value) and deliver None.

Note

Laying out this operation without a coordinating get single is incorrectly.

- get_transform (Callable[[bpy.types.bpy_struct, float, bool], float] | None) – Operation to be termed when this worth is 'examined',
if several extra handling must be managed on the held worth.
This operation must assume trio premises (self, the held worth,
and a boolean signifying if the quality is presently prepared),
and deliver the remaining, modified worth of the quality.

The custom getter must ensure that property value limits (min/max, length, etc.) are enforced correctly. If constraints are violated, a ValueError is raised.

A setter function receives four parameters: the instance, the new value, the current 'raw' value (before any get transformation), and a boolean indicating whether the property is currently initialized. It must return the final, transformed value ready for storage.

The callback must validate that transformed values respect all configured limits. Violations result in a ValueError.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

bpy.props.FloatVectorProperty(*, name='', description='', translation_context='*', default=(0.0, 0.0, 0.0), min=-sys.float_info.max, max=sys.float_info.max, soft_min=-sys.float_info.max, soft_max=sys.float_info.max, step=3, precision=2, options={'ANIMATABLE'}, override=set(), tags=set(), subtype='NONE', unit='NONE', size=3, update=None, get=None, set=None, get_transform=None, set_transform=None)

Constructs a property definition for a floating-point vector.

Parameters:

- name (str) – Label shown in the user interface.

- description (str) – Tooltip and documentation text.

- translation_context (str) – Context string for localization disambiguation.

- default (Sequence[float]) – Initial sequence of floats, matching the vector size.

- min (float) – Hard minimum; assignment below this clamps to this value silently.

- max (float) – Hard maximum; assignment above this clamps to this value silently.

- soft_min (float) – Soft minimum (>= min); UI widgets cannot be dragged below this in normal interaction.

- soft_max (float) – Soft maximum (<= max); UI widgets cannot be dragged above this in normal interaction.

- step (float) – Increment/decrement step in the UI, [1, 100]; defaults to 3 (actual step is /100).

- precision (int) – Maximum decimal places displayed, [0, 6]. Exact integer values with unit 'NONE' or 'TIME' and steps divisible by 100 suppress the fractional component automatically.

- options (set[str]) – Flags from Property Flag Items.

- override (set[str]) – Override flags from Property Override Flag Items.

- tags (set[str]) – Tags defined by the parent class.

- subtype (str) – Subtype from Property Subtype Number Array Items.

- unit (str) – Unit from Property Unit Items.

- size (int | Sequence[int]) – Dimensions, [1, 32]. An int sequence defines multi-dimensional arrays.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Callback on value modification; receives (self, context) and must return None. Warning: no infinite-recursion protection.

- get (Callable[[bpy.types.bpy_struct], Sequence[float]] | None) – Callback on read when custom storage is used; receives (self) and must return the property value.

Note: If defined alone (without set), the property becomes read-only even if `READ_ONLY` is not set.

- set (Callable[[bpy.types.bpy_struct, tuple[float, …]], None] | None) – Callback on write when custom storage is used; receives (self, value) and must return None.

Note: Cannot be defined without a matching get.

- get_transform (Callable[[bpy.types.bpy_struct, Sequence[float], bool], Sequence[float]] | None) – Callback on read to perform additional processing; receives (self, stored_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

- set_transform (Callable[[bpy.types.bpy_struct, Sequence[float], Sequence[float], bool], Sequence[float]] | None) – Callback on write to process the given value before storage; receives (self, new_value, raw_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

bpy.props.IntProperty(*, name='', description='', translation_context='*', default=0, min=-2**31, max=2**31-1, soft_min=-2**31, soft_max=2**31-1, step=1, options={'ANIMATABLE'}, override=set(), tags=set(), subtype='NONE', update=None, get=None, set=None, get_transform=None, set_transform=None)

Constructs a property definition for an integer.

Parameters:

- name (str) – Label shown in the user interface.

- description (str) – Tooltip and documentation text.

- translation_context (str) – Context string for localization disambiguation.

- default (int) – Default value for this property.

- min (int) – Hard minimum; assignment below this clamps to this value silently.

- max (int) – Hard maximum; assignment above this clamps to this value silently.

- soft_min (int) – Soft minimum (>= min); UI widgets cannot be dragged below this in normal interaction.

- soft_max (int) – Soft maximum (<= max); UI widgets cannot be dragged above this in normal interaction.

- step (int) – Increment/decrement step in the UI, [1, 100]; defaults to 1 (WARNING: currently unused).

- options (set[str]) – Flags from Property Flag Items.

- override (set[str]) – Override flags from Property Override Flag Items.

- tags (set[str]) – Tags defined by the parent class.

- subtype (str) – Subtype from Property Subtype Number Items.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Callback on value modification; receives (self, context) and must return None. Warning: no infinite-recursion protection.

- get (Callable[[bpy.types.bpy_struct], int] | None) – Callback on read when custom storage is used; receives (self) and must return the property value.

Note: If defined alone (without set), the property becomes read-only even if `READ_ONLY` is not set.

- set (Callable[[bpy.types.bpy_struct, int], None] | None) – Callback on write when custom storage is used; receives (self, value) and must return None.

Note: Cannot be defined without a matching get.

- get_transform (Callable[[bpy.types.bpy_struct, int, bool], int] | None) – Callback on read to perform additional processing; receives (self, stored_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

- set_transform (Callable[[bpy.types.bpy_struct, int, int, bool], int] | None) – Callback on write to process the given value before storage; receives (self, new_value, raw_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

bpy.props.IntVectorProperty(*, name='', description='', translation_context='*', default=(0, 0, 0), min=-2**31, max=2**31-1, soft_min=-2**31, soft_max=2**31-1, step=1, options={'ANIMATABLE'}, override=set(), tags=set(), subtype='NONE', size=3, update=None, get=None, set=None, get_transform=None, set_transform=None)

Constructs a property definition for an integer vector.

Parameters:

- name (str) – Label shown in the user interface.

- description (str) – Tooltip and documentation text.

- translation_context (str) – Context string for localization disambiguation.

- default (Sequence[int]) – Initial sequence of integers, matching the vector size.

- min (int) – Hard minimum; assignment below this clamps to this value silently.

- max (int) – Hard maximum; assignment above this clamps to this value silently.

- soft_min (int) – Soft minimum (>= min); UI widgets cannot be dragged below this in normal interaction.

- soft_max (int) – Soft maximum (<= max); UI widgets cannot be dragged above this in normal interaction.

- step (int) – Increment/decrement step in the UI, [1, 100]; defaults to 1 (WARNING: currently unused).

- options (set[str]) – Flags from Property Flag Items.

- override (set[str]) – Override flags from Property Override Flag Items.

- tags (set[str]) – Tags defined by the parent class.

- subtype (str) – Subtype from Property Subtype Number Array Items.

- size (int | Sequence[int]) – Dimensions, [1, 32]. An int sequence defines multi-dimensional arrays.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Callback on value modification; receives (self, context) and must return None. Warning: no infinite-recursion protection.

- get (Callable[[bpy.types.bpy_struct], Sequence[int]] | None) – Callback on read when custom storage is used; receives (self) and must return the property value.

Note: If defined alone (without set), the property becomes read-only even if `READ_ONLY` is not set.

- set (Callable[[bpy.types.bpy_struct, tuple[int, …]], None] | None) – Callback on write when custom storage is used; receives (self, value) and must return None.

Note: Cannot be defined without a matching get.

- get_transform (Callable[[bpy.types.bpy_struct, Sequence[int], bool], Sequence[int]] | None) – Callback on read to perform additional processing; receives (self, stored_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

- set_transform (Callable[[bpy.types.bpy_struct, Sequence[int], Sequence[int], bool], Sequence[int]] | None) – Callback on write to process the given value before storage; receives (self, new_value, raw_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

bpy.props.PointerProperty(type, *, name='', description='', translation_context='*', options={'ANIMATABLE'}, override=set(), tags=set(), poll=None, update=None)

Constructs a property definition for a pointer to another data structure.

Parameters:

- type (type[bpy.types.PropertyGroup | bpy.types.ID]) – A subclass of PropertyGroup or ID.

- name (str) – Label shown in the user interface.

- description (str) – Tooltip and documentation text.

- translation_context (str) – Context string for localization disambiguation.

- options (set[str]) – Flags from Property Flag Items.

- override (set[str]) – Override flags from Property Override Flag Items.

- tags (set[str]) – Tags defined by the parent class.

- poll (Callable[[bpy.types.bpy_struct, bpy.types.ID], bool] | None) – Function to decide whether an item is valid for this property; receives (self, object) and returns a boolean.

Note: Return value is checked only for UI assignment. Direct property assignment can still set an "invalid" item.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Callback on value modification; receives (self, context) and must return None. Warning: no infinite-recursion protection.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

Note: Pointer properties cannot reference embedded IDs (e.g., bpy.types.Scene.collection, bpy.types.Material.node_tree). Access embedded IDs through their owning parent (e.g., the scene or material).

bpy.props.RemoveProperty(cls, attr)

Undefines a dynamically added property.

Parameters:

- cls (type[bpy.types.bpy_struct]) – The class hosting the property (positional argument required).

- attr (str) – Property name (keyword argument required).

Note: Typically not called directly. Instead use del cls.attr

bpy.props.StringProperty(*, name='', description='', translation_context='*', default='', maxlen=0, options={'ANIMATABLE'}, override=set(), tags=set(), subtype='NONE', update=None, get=None, set=None, get_transform=None, set_transform=None, search=None, search_options={'SUGGESTION'})

Constructs a property definition for a string.

Parameters:

- name (str) – Label shown in the user interface.

- description (str) – Tooltip and documentation text.

- translation_context (str) – Context string for localization disambiguation.

- default (str) – Starting string value.

- maxlen (int) – Upper bound on string length.

- options (set[str]) – Flags from Property Flag Items.

- override (set[str]) – Override flags from Property Override Flag Items.

- tags (set[str]) – Tags defined by the parent class.

- subtype (str) – Subtype from Property Subtype String Items.

- update (Callable[[bpy.types.bpy_struct, bpy.types.Context], None] | None) – Callback on value modification; receives (self, context) and must return None. Warning: no infinite-recursion protection.

- get (Callable[[bpy.types.bpy_struct], str] | None) – Callback on read when custom storage is used; receives (self) and must return the property value.

Note: If defined alone (without set), the property becomes read-only even if `READ_ONLY` is not set.

- set (Callable[[bpy.types.bpy_struct, str], None] | None) – Callback on write when custom storage is used; receives (self, value) and must return None.

Note: Cannot be defined without a matching get.

- get_transform (Callable[[bpy.types.bpy_struct, str, bool], str] | None) – Callback on read to perform additional processing; receives (self, stored_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

- set_transform (Callable[[bpy.types.bpy_struct, str, str, bool], str] | None) – Callback on write to process the given value before storage; receives (self, new_value, raw_value, is_set) and returns the final transformed value.

Note: Must ensure transformed values respect all limits, or a ValueError is raised.

- search (Callable[[bpy.types.bpy_struct, bpy.types.Context, str], Iterable[str | tuple[str, str]]] | None) – Function called to populate autocomplete options shown in the UI. Receives (self, context, edit_text) and must return a sequence, iterator, or generator. Each item must be either:

- A single string (candidate to display).

- A tuple pair (candidate, additional_info).

- search_options (set[str]) – Control set construction using:

- 'SORT' orders the results.

- 'SUGGESTION' allows user-entered values outside search results. WARNING: disabling this causes the search callback to run on every redraw, which can hurt performance if the callback is expensive.

Returns an opaque type suitable for property registration.

Returns: _PropertyDeferred

class bpy.props._PropertyDeferred

Intermediate holder for property definitions prior to registration.

Note: Not part of the stable API and may change between releases.

function

Undocumented, consider contributing.

keywords

Undocumented, consider contributing.

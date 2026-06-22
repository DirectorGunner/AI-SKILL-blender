# Paint Operators (part 1)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

### Paint Operators 

bpy.ops.paint. add_simple_uvs ( ) 

Affix cubic map coordinates on geometry

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. add_texture_paint_slot ( * , type = '`BASE_COLOR`' , slot_type = 'IMAGE' , name = 'Untitled' , color = (0.0, 0.0, 0.0, 1.0) , width = 1024 , height = 1024 , alpha = True , generated_type = 'BLANK' , float = False , domain = 'POINT' , data_type = '`FLOAT_COLOR`' ) 

Introduce a paint tray

Parameters :

- type ( Literal [ '`BASE_COLOR`' , 'SPECULAR' , 'ROUGHNESS' , 'METALLIC' , 'NORMAL' , 'BUMP' , 'DISPLACEMENT' ] ) – Material Layer Type, Substance tier category of updated paint tray (optional)

- slot_type ( Literal [ 'IMAGE' , '`COLOR_ATTRIBUTE`' ] ) – Slot Type, Genre of updated paint tray (optional)

- name ( str ) – Name, Title for updated paint tray resource (optional, never None)

- color ( Sequence [ float ] ) – Color, Preliminary padding tint (array of 4 items, in [0, inf], optional)

- width ( int ) – Width, Image extent (in [1, inf], optional)

- height ( int ) – Height, Image measurement (in [1, inf], optional)

- alpha ( bool ) – Alpha, Construct a picture incorporating an opacity channel (optional)

- generated_type (Literal[Image Generated Type Items]) – Generated Type, Replenish the picture with a lattice for coordinate atlas checking (optional)

- float ( bool ) – 32-bit Float, Construct picture with 32-bit floating-point bit profundity (optional)

- domain (Literal[Color Attribute Domain Items]) – Domain, Genre of component that characteristic is housed on (optional)

- data_type (Literal[Color Attribute Type Items]) – Data Type, Genre of data lodged in characteristic (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. brush_colors_flip ( ) 

Exchange primary and alternate brush pigments

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_all ( * , action = 'TOGGLE' ) 

Modify choosing for every faces

Parameters :

action ( Literal [ 'TOGGLE' , 'SELECT' , 'DESELECT' , 'INVERT' ] ) – Action, Choosing activity to execute (optional)

- TOGGLE
Toggle – Flip choosing for every components.

- SELECT
Select – Opt for every components.

- DESELECT
Deselect – Unselect every components.

- INVERT
Invert – Invert choosing of every components.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_hide ( * , unselected = False ) 

Conceal chosen faces

Parameters :

unselected ( bool ) – Unselected, Conceal non-chosen preferentially to chosen items (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_less ( * , face_step = True ) 

Unselect Faces neighboring to persisting choosing

Parameters :

face_step ( bool ) – Face Step, Similarly unselect faces that just interact at a bend (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_linked ( ) 

Opt for joined faces

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_linked_pick ( * , deselect = False ) 

Opt for joined faces below the cursor

Parameters :

deselect ( bool ) – Deselect, Unselect as opposed to opt for pieces (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_loop ( * , select = True , extend = False ) 

Opt for face progression below the cursor

Parameters :

- select ( bool ) – Select, Whether bogus, faces remain deselected (optional)

- extend ( bool ) – Extend, Broaden the choosing (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_select_more ( * , face_step = True ) 

Opt for Faces neighboring to persisting choosing

Parameters :

face_step ( bool ) – Face Step, Similarly opt for faces that just interact at a bend (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. face_vert_reveal ( * , select = True ) 

Uncover latent faces and vertices

Parameters :

select ( bool ) – Select, Indicates whether the refreshed information shall be opted (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. grab_clone ( * , delta = (0.0, 0.0) ) 

Displace the imitation foundation picture

Parameters :

delta (mathutils.Vector) – Delta, Positional offset of imitation picture in 0.0 to 1.0 positions (array of 2 items, in [-inf, inf], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , action = 'HIDE' , area = 'Inside' , use_front_faces_only = False ) 

Conceal/expose certain vertices

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

- area ( Literal [ 'OUTSIDE' , 'Inside' ] ) – Visibility Area, Whichever vertices to conceal or expose (optional)

- OUTSIDE
Outside – Conceal or expose vertices outside the choosing.

- Inside
Inside – Conceal or expose vertices inside the choosing.

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show_all ( * , action = 'HIDE' ) 

Conceal/expose every vertices

Parameters :

action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show_lasso_gesture ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , action = 'HIDE' , area = 'Inside' , use_front_faces_only = False ) 

Conceal/expose certain vertices

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Choosing delays behind cursor and adheres to a uniformer trajectory (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Increased quantities yield a uniformer stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Reduced gap from preceding spot prior to choosing persists (in [10, 200], optional)

- action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

- area ( Literal [ 'OUTSIDE' , 'Inside' ] ) – Visibility Area, Whichever vertices to conceal or expose (optional)

- OUTSIDE
Outside – Conceal or expose vertices outside the choosing.

- Inside
Inside – Conceal or expose vertices inside the choosing.

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , action = 'HIDE' , area = 'Inside' , use_front_faces_only = False , use_limit_to_segment = False ) 

Conceal/expose certain vertices

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer styling to utilize through the dynamic activity (in [0, inf], optional)

- action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

- area ( Literal [ 'OUTSIDE' , 'Inside' ] ) – Visibility Area, Whichever vertices to conceal or expose (optional)

- OUTSIDE
Outside – Conceal or expose vertices outside the choosing.

- Inside
Inside – Conceal or expose vertices inside the choosing.

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

- use_limit_to_segment ( bool ) – Limit to Segment, Employ the motion activity exclusively to the zone that stays enclosed within the progression devoid of magnifying its consequence to the full progression (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show_masked ( * , action = 'HIDE' ) 

Conceal/expose every obscured vertices above a tolerance

Parameters :

action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. hide_show_polyline_gesture ( * , path = None , action = 'HIDE' , area = 'Inside' , use_front_faces_only = False ) 

Conceal/expose certain vertices

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- action ( Literal [ 'HIDE' , 'SHOW' ] ) – Visibility Action, If to conceal or expose vertices (optional)

- HIDE
Hide – Conceal vertices.

- SHOW
Show – Expose vertices.

- area ( Literal [ 'OUTSIDE' , 'Inside' ] ) – Visibility Area, Whichever vertices to conceal or expose (optional)

- OUTSIDE
Outside – Conceal or expose vertices outside the choosing.

- Inside
Inside – Conceal or expose vertices inside the choosing.

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. image_from_view ( * , filepath = '' ) 

Assemble a picture from greatest 3D observation for reapplication

Parameters :

filepath ( str ) – File Path, Designation of the record (optional, never None)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. image_paint ( * , stroke = None , mode = 'NORMAL' , brush_toggle = 'None' , pen_flip = False ) 

Tint a movement inside the picture

Parameters :

- stroke ( bpy_prop_collection [ OperatorStrokeElement ]) – Stroke, (optional)

- mode ( Literal [ 'NORMAL' , 'INVERT' ] ) – Stroke Mode, Activity executed once a tint movement is created (optional)

- NORMAL
Regular – Operate brush habitually.

- INVERT
Invert – Reverse activity of brush throughout movement span.

- brush_toggle ( Literal [ 'None' , 'SMOOTH' , 'ERASE' , 'MASK' ] ) – Temporary Brush Toggle Type, Brush to utilize throughout movement span (optional)

- None
None – Operate brush habitually.

- SMOOTH
Smooth – Exchange to polishing brush throughout movement span.

- ERASE
Erase – Exchange to wiping brush throughout movement span.

- MASK
Mask – Exchange to mask brush throughout movement span.

- pen_flip ( bool ) – Pen Flip, When a stylus's eliminating manner is in consumption (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. mask_box_gesture ( * , xmin = 0 , xmax = 0 , ymin = 0 , ymax = 0 , wait_for_input = True , use_front_faces_only = False , mode = 'VALUE' , value = 1.0 ) 

Mask throughout a rectangular area specified by the cursor

Parameters :

- xmin ( int ) – X Min, (in [-inf, inf], optional)

- xmax ( int ) – X Max, (in [-inf, inf], optional)

- ymin ( int ) – Y Min, (in [-inf, inf], optional)

- ymax ( int ) – Y Max, (in [-inf, inf], optional)

- wait_for_input ( bool ) – Wait for Input, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

- mode ( Literal [ 'VALUE' , '`VALUE_INVERSE`' , 'INVERT' ] ) – Mode, (optional)

- VALUE
Value – Fix mask to the profundity indicated by the 'value' attribute.

- `VALUE_INVERSE`
Value Inverted – Fix mask to the profundity indicated by the flipped 'value' attribute.

- INVERT
Invert – Reverse the mask.

- value ( float ) – Value, Mask profundity to utilize whenever manner is 'Value'; naught implies no concealment and unity is absolutely concealed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. mask_flood_fill ( * , mode = 'VALUE' , value = 0.0 ) 

Replenish the comprehensive mask with a provided quantity, or invert its quantities

Parameters :

- mode ( Literal [ 'VALUE' , '`VALUE_INVERSE`' , 'INVERT' ] ) – Mode, (optional)

- VALUE
Value – Fix mask to the profundity indicated by the 'value' attribute.

- `VALUE_INVERSE`
Value Inverted – Fix mask to the profundity indicated by the flipped 'value' attribute.

- INVERT
Invert – Reverse the mask.

- value ( float ) – Value, Mask profundity to utilize whenever manner is 'Value'; naught implies no concealment and unity is absolutely concealed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. mask_lasso_gesture ( * , path = None , use_smooth_stroke = False , smooth_stroke_factor = 0.75 , smooth_stroke_radius = 35 , use_front_faces_only = False , mode = 'VALUE' , value = 1.0 ) 

Mask throughout a contour specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_smooth_stroke ( bool ) – Stabilize Stroke, Choosing delays behind cursor and adheres to a uniformer trajectory (optional)

- smooth_stroke_factor ( float ) – Smooth Stroke Factor, Increased quantities yield a uniformer stroke (in [0.5, 0.99], optional)

- smooth_stroke_radius ( int ) – Smooth Stroke Radius, Reduced gap from preceding spot prior to choosing persists (in [10, 200], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

- mode ( Literal [ 'VALUE' , '`VALUE_INVERSE`' , 'INVERT' ] ) – Mode, (optional)

- VALUE
Value – Fix mask to the profundity indicated by the 'value' attribute.

- `VALUE_INVERSE`
Value Inverted – Fix mask to the profundity indicated by the flipped 'value' attribute.

- INVERT
Invert – Reverse the mask.

- value ( float ) – Value, Mask profundity to utilize whenever manner is 'Value'; naught implies no concealment and unity is absolutely concealed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. mask_line_gesture ( * , xstart = 0 , xend = 0 , ystart = 0 , yend = 0 , flip = False , cursor = 5 , use_front_faces_only = False , use_limit_to_segment = False , mode = 'VALUE' , value = 1.0 ) 

Mask to singular flank of a progression specified by the cursor

Parameters :

- xstart ( int ) – X Start, (in [-inf, inf], optional)

- xend ( int ) – X End, (in [-inf, inf], optional)

- ystart ( int ) – Y Start, (in [-inf, inf], optional)

- yend ( int ) – Y End, (in [-inf, inf], optional)

- flip ( bool ) – Flip, (optional)

- cursor ( int ) – Cursor, Pointer styling to utilize through the dynamic activity (in [0, inf], optional)

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

- use_limit_to_segment ( bool ) – Limit to Segment, Employ the motion activity exclusively to the zone that stays enclosed within the progression devoid of magnifying its consequence to the full progression (optional)

- mode ( Literal [ 'VALUE' , '`VALUE_INVERSE`' , 'INVERT' ] ) – Mode, (optional)

- VALUE
Value – Fix mask to the profundity indicated by the 'value' attribute.

- `VALUE_INVERSE`
Value Inverted – Fix mask to the profundity indicated by the flipped 'value' attribute.

- INVERT
Invert – Reverse the mask.

- value ( float ) – Value, Mask profundity to utilize whenever manner is 'Value'; naught implies no concealment and unity is absolutely concealed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. mask_polyline_gesture ( * , path = None , use_front_faces_only = False , mode = 'VALUE' , value = 1.0 ) 

Mask throughout a contour specified by the cursor

Parameters :

- path ( bpy_prop_collection [ OperatorMousePath ]) – Path, (optional)

- use_front_faces_only ( bool ) – Front Faces Only, Modify merely faces addressing toward the observation (optional)

- mode ( Literal [ 'VALUE' , '`VALUE_INVERSE`' , 'INVERT' ] ) – Mode, (optional)

- VALUE
Value – Fix mask to the profundity indicated by the 'value' attribute.

- `VALUE_INVERSE`
Value Inverted – Fix mask to the profundity indicated by the flipped 'value' attribute.

- INVERT
Invert – Reverse the mask.

- value ( float ) – Value, Mask profundity to utilize whenever manner is 'Value'; naught implies no concealment and unity is absolutely concealed (in [0, 1], optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. project_image ( * , image = '' ) 

Project a modified rendering from the working camera backwards onto the item

Parameters :

image ( str ) – Image, (optional)

Returns :

Result of the operator call.

Return type :

set[Literal[Operator Return Items]]

bpy.ops.paint. sample_color ( * , location = (0, 0) , merged = False , palette = False ) 

Leverage the cursor to acquire a tint in the picture

Parameters :

- location ( Sequence [ int ] ) – Location, (array of 2 items, in [0, inf], optional)

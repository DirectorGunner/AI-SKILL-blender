# Uilayout Bpy Struct (part 3)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

template_node_inputs ( node )

Shows a node’s settings along with the values on its input sockets.

Parameters :

node (Node) – Node, Display inputs of this node (never None)

template_asset_shelf_popover ( asset_shelf , * , name = '' , icon = 'NONE' , icon_value = 0 )

Adds a button that opens an asset shelf inside a popover.

Parameters :

- asset_shelf ( str ) – Identifier of the asset shelf to display ( bl_idname ) (never None)

- name ( str ) – Optional name to indicate the active asset (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- icon_value ( int ) – Icon Value, Override automatic icon of the item (in [0, inf], optional)

template_popup_confirm ( operator , * , text = '' , text_ctxt = '' , translate = True , icon = 'NONE' , cancel_text = '' , cancel_default = False )

Adds confirm and cancel buttons to a popup; clicking either one dismisses the popup.

Parameters :

- operator ( str ) – Identifier of the operator (never None)

- text ( str ) – Override automatic text of the item (optional)

- text_ctxt ( str ) – Override automatic translation context of the given text (optional)

- translate ( bool ) – Translate the given text, when UI translation is enabled (optional)

- icon (Literal[Icon Items]) – Icon, Override automatic icon of the item (optional)

- cancel_text ( str ) – Optional text to use for the cancel, not shown when an empty string (optional, never None)

- cancel_default ( bool ) – Cancel button by default (optional)

Returns :

Operator properties to fill in

Return type :

OperatorProperties

template_shape_key_tree ( )

Shape Key tree view

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

introspect ( )

Returns a list of dictionaries giving a text-based representation of the UI layout.

Return type :

list[dict[str, Any]]

### Inherited Properties

| bpy_struct.id_data | |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items | bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values |

### References

| AssetShelf.draw_context_menu Header.layout Menu.layout Node.draw_buttons Node.draw_buttons_ext NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeSocket.draw NodeSocketStandard.draw NodeTreeInterfaceSocket.draw NodeTreeInterfaceSocketBool.draw NodeTreeInterfaceSocketBundle.draw NodeTreeInterfaceSocketClosure.draw NodeTreeInterfaceSocketCollection.draw NodeTreeInterfaceSocketColor.draw NodeTreeInterfaceSocketFloat.draw NodeTreeInterfaceSocketFloatAngle.draw NodeTreeInterfaceSocketFloatColorTemperature.draw NodeTreeInterfaceSocketFloatDistance.draw NodeTreeInterfaceSocketFloatFactor.draw NodeTreeInterfaceSocketFloatFrequency.draw NodeTreeInterfaceSocketFloatMass.draw NodeTreeInterfaceSocketFloatPercentage.draw NodeTreeInterfaceSocketFloatTime.draw NodeTreeInterfaceSocketFloatTimeAbsolute.draw NodeTreeInterfaceSocketFloatUnsigned.draw NodeTreeInterfaceSocketFloatWavelength.draw NodeTreeInterfaceSocketGeometry.draw NodeTreeInterfaceSocketImage.draw NodeTreeInterfaceSocketInt.draw NodeTreeInterfaceSocketIntFactor.draw NodeTreeInterfaceSocketIntPercentage.draw NodeTreeInterfaceSocketIntUnsigned.draw NodeTreeInterfaceSocketMaterial.draw NodeTreeInterfaceSocketMatrix.draw NodeTreeInterfaceSocketMenu.draw NodeTreeInterfaceSocketObject.draw NodeTreeInterfaceSocketRotation.draw NodeTreeInterfaceSocketShader.draw NodeTreeInterfaceSocketString.draw NodeTreeInterfaceSocketStringFilePath.draw NodeTreeInterfaceSocketTexture.draw NodeTreeInterfaceSocketVector.draw NodeTreeInterfaceSocketVector2D.draw | NodeTreeInterfaceSocketVector4D.draw NodeTreeInterfaceSocketVectorAcceleration.draw NodeTreeInterfaceSocketVectorAcceleration2D.draw NodeTreeInterfaceSocketVectorAcceleration4D.draw NodeTreeInterfaceSocketVectorDirection.draw NodeTreeInterfaceSocketVectorDirection2D.draw NodeTreeInterfaceSocketVectorDirection4D.draw NodeTreeInterfaceSocketVectorEuler.draw NodeTreeInterfaceSocketVectorEuler2D.draw NodeTreeInterfaceSocketVectorEuler4D.draw NodeTreeInterfaceSocketVectorFactor.draw NodeTreeInterfaceSocketVectorFactor2D.draw NodeTreeInterfaceSocketVectorFactor4D.draw NodeTreeInterfaceSocketVectorPercentage.draw NodeTreeInterfaceSocketVectorPercentage2D.draw NodeTreeInterfaceSocketVectorPercentage4D.draw NodeTreeInterfaceSocketVectorTranslation.draw NodeTreeInterfaceSocketVectorTranslation2D.draw NodeTreeInterfaceSocketVectorTranslation4D.draw NodeTreeInterfaceSocketVectorVelocity.draw NodeTreeInterfaceSocketVectorVelocity2D.draw NodeTreeInterfaceSocketVectorVelocity4D.draw NodeTreeInterfaceSocketVectorXYZ.draw NodeTreeInterfaceSocketVectorXYZ2D.draw NodeTreeInterfaceSocketVectorXYZ4D.draw Operator.layout Panel.layout UILayout.box UILayout.column UILayout.column_flow UILayout.grid_flow UILayout.menu_pie UILayout.panel UILayout.panel UILayout.panel_prop UILayout.panel_prop UILayout.row UILayout.split UILayout.template_light_linking_collection UIList.draw_filter UIList.draw_item UIPieMenu.layout UIPopover.layout UIPopupMenu.layout |

## See also

- [Bpy Struct](bpy-struct.md)

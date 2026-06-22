# Geometrynode Nodeinternal, Geometrynodeaccumulatefield Geometrynode, Geometrynodeattributedomainsize Geometrynode, Geometrynodeattributestatistic Geometrynode ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: GeometryNode(NodeInternal); GeometryNodeAccumulateField(GeometryNode); GeometryNodeAttributeDomainSize(GeometryNode); GeometryNodeAttributeStatistic(GeometryNode); GeometryNodeBake(GeometryNode).

## GeometryNode(NodeInternal)

### GeometryNode(NodeInternal)

base classes — bpy_struct, Node, NodeInternal

subclasses —
GeometryNodeAccumulateField, GeometryNodeAttributeDomainSize, GeometryNodeAttributeStatistic, GeometryNodeBake, GeometryNodeBlurAttribute, GeometryNodeBoneInfo, GeometryNodeBoundBox, GeometryNodeCameraInfo, GeometryNodeCaptureAttribute, GeometryNodeCollectionInfo, GeometryNodeConvexHull, GeometryNodeCornersOfEdge, GeometryNodeCornersOfFace, GeometryNodeCornersOfVertex, GeometryNodeCubeGridTopology, GeometryNodeCurveArc, GeometryNodeCurveEndpointSelection, GeometryNodeCurveHandleTypeSelection, GeometryNodeCurveLength, GeometryNodeCurveOfPoint, GeometryNodeCurvePrimitiveBezierSegment, GeometryNodeCurvePrimitiveCircle, GeometryNodeCurvePrimitiveLine, GeometryNodeCurvePrimitiveQuadrilateral, GeometryNodeCurveQuadraticBezier, GeometryNodeCurveSetHandles, GeometryNodeCurveSpiral, GeometryNodeCurveSplineType, GeometryNodeCurveStar, GeometryNodeCurveToMesh, GeometryNodeCurveToPoints, GeometryNodeCurvesToGreasePencil, GeometryNodeCustomGroup, GeometryNodeDeformCurvesOnSurface, GeometryNodeDeleteGeometry, GeometryNodeDistributePointsInGrid, GeometryNodeDistributePointsInVolume, GeometryNodeDistributePointsOnFaces, GeometryNodeDualMesh, GeometryNodeDuplicateElements, GeometryNodeEdgePathsToCurves, GeometryNodeEdgePathsToSelection, GeometryNodeEdgesOfCorner, GeometryNodeEdgesOfVertex, GeometryNodeEdgesToFaceGroups, GeometryNodeExtrudeMesh, GeometryNodeFaceOfCorner, GeometryNodeFieldAtIndex, GeometryNodeFieldAverage, GeometryNodeFieldMinAndMax, GeometryNodeFieldOnDomain, GeometryNodeFieldToGrid, GeometryNodeFieldToList, GeometryNodeFieldVariance, GeometryNodeFillCurve, GeometryNodeFilletCurve, GeometryNodeFlipFaces, GeometryNodeForeachGeometryElementInput, GeometryNodeForeachGeometryElementOutput, GeometryNodeGeometryToInstance, GeometryNodeGetGeometryBundle, GeometryNodeGetNamedGrid, GeometryNodeGizmoDial, GeometryNodeGizmoLinear, GeometryNodeGizmoTransform, GeometryNodeGreasePencilToCurves, GeometryNodeGridAdvect, GeometryNodeGridClip, GeometryNodeGridCurl, GeometryNodeGridDilateAndErode, GeometryNodeGridDivergence, GeometryNodeGridGradient, GeometryNodeGridInfo, GeometryNodeGridLaplacian, GeometryNodeGridMean, GeometryNodeGridMedian, GeometryNodeGridPrune, GeometryNodeGridToMesh, GeometryNodeGridToPoints, GeometryNodeGridVoxelize, GeometryNodeGroup, GeometryNodeImageInfo, GeometryNodeImageTexture, GeometryNodeImportCSV, GeometryNodeImportOBJ, GeometryNodeImportPLY, GeometryNodeImportSTL, GeometryNodeImportText, GeometryNodeImportVDB, GeometryNodeIndexOfNearest, GeometryNodeIndexSwitch, GeometryNodeInputActiveCamera, GeometryNodeInputCollection, GeometryNodeInputCurveHandlePositions, GeometryNodeInputCurveTilt, GeometryNodeInputEdgeSmooth, GeometryNodeInputID, GeometryNodeInputImage, GeometryNodeInputIndex, GeometryNodeInputInstanceBounds, GeometryNodeInputInstanceRotation, GeometryNodeInputInstanceScale, GeometryNodeInputMaterial, GeometryNodeInputMaterialIndex, GeometryNodeInputMeshEdgeAngle, GeometryNodeInputMeshEdgeNeighbors, GeometryNodeInputMeshEdgeVertices, GeometryNodeInputMeshFaceArea, GeometryNodeInputMeshFaceIsPlanar, GeometryNodeInputMeshFaceNeighbors, GeometryNodeInputMeshIsland, GeometryNodeInputMeshVertexNeighbors, GeometryNodeInputNamedAttribute, GeometryNodeInputNamedLayerSelection, GeometryNodeInputNormal, GeometryNodeInputObject, GeometryNodeInputPosition, GeometryNodeInputRadius, GeometryNodeInputSceneTime, GeometryNodeInputShadeSmooth, GeometryNodeInputShortestEdgePaths, GeometryNodeInputSplineCyclic, GeometryNodeInputSplineResolution, GeometryNodeInputTangent, GeometryNodeInputVoxelIndex, GeometryNodeInstanceOnPoints, GeometryNodeInstanceTransform, GeometryNodeInstancesToPoints, GeometryNodeInterpolateCurves, GeometryNodeIsViewport, GeometryNodeJoinGeometry, GeometryNodeListGetItem, GeometryNodeListLength, GeometryNodeMaterialSelection, GeometryNodeMenuSwitch, GeometryNodeMergeByDistance, GeometryNodeMergeLayers, GeometryNodeMeshBoolean, GeometryNodeMeshCircle, GeometryNodeMeshCone, GeometryNodeMeshCube, GeometryNodeMeshCylinder, GeometryNodeMeshFaceSetBoundaries, GeometryNodeMeshGrid, GeometryNodeMeshIcoSphere, GeometryNodeMeshLine, GeometryNodeMeshToCurve, GeometryNodeMeshToDensityGrid, GeometryNodeMeshToPoints, GeometryNodeMeshToSDFGrid, GeometryNodeMeshToVolume, GeometryNodeMeshUVSphere, GeometryNodeObjectInfo, GeometryNodeOffsetCornerInFace, GeometryNodeOffsetPointInCurve, GeometryNodePoints, GeometryNodePointsOfCurve, GeometryNodePointsToCurves, GeometryNodePointsToSDFGrid, GeometryNodePointsToVertices, GeometryNodePointsToVolume, GeometryNodeProximity, GeometryNodeRaycast, GeometryNodeRealizeInstances, GeometryNodeRemoveAttribute, GeometryNodeRepeatInput, GeometryNodeRepeatOutput, GeometryNodeReplaceMaterial, GeometryNodeResampleCurve, GeometryNodeReverseCurve, GeometryNodeRotateInstances, GeometryNodeSDFGridBoolean, GeometryNodeSDFGridFillet, GeometryNodeSDFGridLaplacian, GeometryNodeSDFGridMean, GeometryNodeSDFGridMeanCurvature, GeometryNodeSDFGridMedian, GeometryNodeSDFGridOffset, GeometryNodeSampleCurve, GeometryNodeSampleGrid, GeometryNodeSampleGridIndex, GeometryNodeSampleIndex, GeometryNodeSampleNearest, GeometryNodeSampleNearestSurface, GeometryNodeSampleUVSurface, GeometryNodeScaleElements, GeometryNodeScaleInstances, GeometryNodeSelfObject, GeometryNodeSeparateComponents, GeometryNodeSeparateGeometry, GeometryNodeSetCurveHandlePositions, GeometryNodeSetCurveNormal, GeometryNodeSetCurveRadius, GeometryNodeSetCurveTilt, GeometryNodeSetGeometryBundle, GeometryNodeSetGeometryName, GeometryNodeSetGreasePencilColor, GeometryNodeSetGreasePencilDepth, GeometryNodeSetGreasePencilSoftness, GeometryNodeSetGridBackground, GeometryNodeSetGridTransform, GeometryNodeSetID, GeometryNodeSetInstanceTransform, GeometryNodeSetMaterial, GeometryNodeSetMaterialIndex, GeometryNodeSetMeshNormal, GeometryNodeSetPointRadius, GeometryNodeSetPosition, GeometryNodeSetShadeSmooth, GeometryNodeSetSplineCyclic, GeometryNodeSetSplineResolution, GeometryNodeSimulationInput, GeometryNodeSimulationOutput, GeometryNodeSortElements, GeometryNodeSplineLength, GeometryNodeSplineParameter, GeometryNodeSplitEdges, GeometryNodeSplitToInstances, GeometryNodeStoreNamedAttribute, GeometryNodeStoreNamedGrid, GeometryNodeStringJoin, GeometryNodeStringToCurves, GeometryNodeSubdivideCurve, GeometryNodeSubdivideMesh, GeometryNodeSubdivisionSurface, GeometryNodeSwitch, GeometryNodeTool3DCursor, GeometryNodeToolActiveElement, GeometryNodeToolFaceSet, GeometryNodeToolMousePosition, GeometryNodeToolSelection, GeometryNodeToolSetFaceSet, GeometryNodeToolSetSelection, GeometryNodeTransform, GeometryNodeTranslateInstances, GeometryNodeTriangulate, GeometryNodeTrimCurve, GeometryNodeUVPackIslands, GeometryNodeUVTangent, GeometryNodeUVUnwrap, GeometryNodeVertexOfCorner, GeometryNodeViewer, GeometryNodeViewportTransform, GeometryNodeVolumeCube, GeometryNodeVolumeToMesh, GeometryNodeWarning

class bpy.types. GeometryNode ( NodeInternal )

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get | Node.socket_value_update Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py |

## GeometryNodeAccumulateField(GeometryNode)

### GeometryNodeAccumulateField(GeometryNode)

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeAccumulateField ( GeometryNode )

Sums the values of an evaluated field and reports the running tally for every element.

data_type

Kind of data being accumulated (default 'FLOAT' )

- FLOAT
Float – Add floating point values.

- INT
Integer – Add integer values.

- `FLOAT_VECTOR`
Vector – Add 3D vector values.

- TRANSFORM
Transform – Multiply transformation matrices.

Type :

Literal[‘FLOAT’, ‘INT’, ‘`FLOAT_VECTOR`’, ‘TRANSFORM’]

domain

(default 'POINT' )

Type :

Literal[Attribute Domain Items]

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeAttributeDomainSize(GeometryNode)

### GeometryNodeAttributeDomainSize(GeometryNode)

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeAttributeDomainSize ( GeometryNode )

Reports, per attribute domain, how many elements a geometry holds.

component

(default 'MESH' )

Type :

Literal[Geometry Component Type Items]

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeAttributeStatistic(GeometryNode)

### GeometryNodeAttributeStatistic(GeometryNode)

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeAttributeStatistic ( GeometryNode )

Works out statistics over a data set drawn from a field sampled on a geometry.

data_type

The type the attribute is cast to ahead of computing the results (default 'FLOAT' )

Type :

Literal[Attribute Type Items]

domain

The domain the data is read from (default 'POINT' )

Type :

Literal[Attribute Domain Items]

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

## GeometryNodeBake(GeometryNode)

### GeometryNodeBake(GeometryNode)

base classes — bpy_struct, Node, NodeInternal, GeometryNode

class bpy.types. GeometryNodeBake ( GeometryNode )

Stores the incoming data so it stays available without being recalculated.

active_index

Index of the active item (in [0, inf], default 0)

Type :

int

active_item

Index of the active item

Type :

RepeatItem

bake_items

(default None, readonly)

Type :

NodeGeometryBakeItems[NodeGeometryBakeItem]

classmethod is_registered_node_type ( )

True if a registered node type

Returns :

Result

Return type :

bool

classmethod input_template ( index )

Input socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

classmethod output_template ( index )

Output socket template

Parameters :

index ( int ) – Index, (in [0, inf])

Returns :

result

Return type :

NodeInternalSocketTemplate

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

| bpy_struct.id_data Node.type Node.location Node.location_absolute Node.width Node.height Node.dimensions Node.name Node.label Node.inputs Node.outputs Node.internal_links Node.parent Node.warning_propagation Node.use_custom_color Node.color Node.color_tag | Node.select Node.show_options Node.show_preview Node.hide Node.mute Node.show_texture Node.bl_idname Node.bl_label Node.bl_description Node.bl_icon Node.bl_static_type Node.bl_width_default Node.bl_width_min Node.bl_width_max Node.bl_height_default Node.bl_height_min Node.bl_height_max |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values Node.bl_system_properties_get Node.socket_value_update | Node.is_registered_node_type Node.poll Node.poll_instance Node.update Node.insert_link Node.init Node.copy Node.free Node.draw_buttons Node.draw_buttons_ext Node.draw_label Node.debug_zone_body_lazy_function_graph Node.debug_zone_lazy_function_graph Node.poll Node.bl_rna_get_subclass Node.bl_rna_get_subclass_py NodeInternal.poll NodeInternal.poll_instance NodeInternal.update NodeInternal.draw_buttons NodeInternal.draw_buttons_ext NodeInternal.bl_rna_get_subclass NodeInternal.bl_rna_get_subclass_py GeometryNode.poll GeometryNode.bl_rna_get_subclass GeometryNode.bl_rna_get_subclass_py |

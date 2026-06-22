# Texture Type Items, Change Log

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Texture Type Items; Change Log.

## Texture Type Items

### Texture Type Items

NONE :

None.

BLEND :

Blend.

Procedural - builds a ramp texture.

CLOUDS :

Clouds.

Procedural - builds a cloud-like fractal noise texture.

`DISTORTED_NOISE` :

Distorted Noise.

Procedural - a noise texture warped by a second noise algorithm.

IMAGE :

Image or Movie.

Lets images or movies serve as textures.

MAGIC :

Magic.

Procedural - a color texture driven by trigonometric functions.

MARBLE :

Marble.

Procedural - a marble-like noise texture banded by waves.

MUSGRAVE :

Musgrave.

Procedural - a very adaptable fractal noise texture.

NOISE :

Noise.

Procedural - random noise that changes each time, every frame, and every pixel.

STUCCI :

Stucci.

Procedural - builds a fractal noise texture.

VORONOI :

Voronoi.

Procedural - builds cell-like patterns from Worley noise.

WOOD :

Wood.

Procedural - wave-banded rings or bands, with noise as an option.

## Change Log

### Change Log

What shifted in Blender's Python API from one release to the next.

### 5.0 to 5.1

### bpy.types.AdjustmentStrip

#### Added

- bpy.types.AdjustmentStrip.content_trim_end

- bpy.types.AdjustmentStrip.content_trim_start

### bpy.types.Brush

#### Removed

- use_airbrush

- use_anchor

- use_curve

- use_line

- use_restore_mesh

- use_space

### bpy.types.BrushCapabilitiesSculpt

#### Added

- bpy.types.BrushCapabilitiesSculpt.has_hardness

- bpy.types.BrushCapabilitiesSculpt.has_normal_radius

### bpy.types.BrushGpencilSettings

#### Added

- bpy.types.BrushGpencilSettings.stroke_type

### bpy.types.CompositorNode

#### Removed

- tag_need_exec

- update

### bpy.types.CompositorNodeAlphaOver

#### Removed

- update

### bpy.types.CompositorNodeAntiAliasing

#### Removed

- update

### bpy.types.CompositorNodeBilateralblur

#### Removed

- update

### bpy.types.CompositorNodeBlur

#### Removed

- update

### bpy.types.CompositorNodeBokehBlur

#### Removed

- update

### bpy.types.CompositorNodeBokehImage

#### Removed

- update

### bpy.types.CompositorNodeBoxMask

#### Removed

- update

### bpy.types.CompositorNodeBrightContrast

#### Removed

- update

### bpy.types.CompositorNodeChannelMatte

#### Removed

- update

### bpy.types.CompositorNodeChromaMatte

#### Removed

- update

### bpy.types.CompositorNodeColorBalance

#### Removed

- update

### bpy.types.CompositorNodeColorCorrection

#### Removed

- update

### bpy.types.CompositorNodeColorMatte

#### Removed

- update

### bpy.types.CompositorNodeColorSpill

#### Removed

- update

### bpy.types.CompositorNodeCombineColor

#### Removed

- update

### bpy.types.CompositorNodeConvertColorSpace

#### Removed

- update

### bpy.types.CompositorNodeConvertToDisplay

#### Removed

- update

### bpy.types.CompositorNodeConvolve

#### Removed

- update

### bpy.types.CompositorNodeCornerPin

#### Removed

- update

### bpy.types.CompositorNodeCrop

#### Removed

- update

### bpy.types.CompositorNodeCryptomatte

#### Removed

- update

### bpy.types.CompositorNodeCryptomatteV2

#### Removed

- update

### bpy.types.CompositorNodeCurveRGB

#### Removed

- update

### bpy.types.CompositorNodeCustomGroup

#### Removed

- update

### bpy.types.CompositorNodeDBlur

#### Removed

- update

### bpy.types.CompositorNodeDefocus

#### Removed

- update

### bpy.types.CompositorNodeDenoise

#### Removed

- update

### bpy.types.CompositorNodeDespeckle

#### Removed

- update

### bpy.types.CompositorNodeDiffMatte

#### Removed

- update

### bpy.types.CompositorNodeDilateErode

#### Removed

- update

### bpy.types.CompositorNodeDisplace

#### Removed

- update

### bpy.types.CompositorNodeDistanceMatte

#### Removed

- update

### bpy.types.CompositorNodeDoubleEdgeMask

#### Removed

- update

### bpy.types.CompositorNodeEllipseMask

#### Removed

- update

### bpy.types.CompositorNodeExposure

#### Removed

- update

### bpy.types.CompositorNodeFilter

#### Removed

- update

### bpy.types.CompositorNodeFlip

#### Removed

- update

### bpy.types.CompositorNodeGamma

#### Removed

- update

### bpy.types.CompositorNodeGlare

#### Removed

- update

### bpy.types.CompositorNodeGroup

#### Removed

- update

### bpy.types.CompositorNodeHueCorrect

#### Removed

- update

### bpy.types.CompositorNodeHueSat

#### Removed

- update

### bpy.types.CompositorNodeIDMask

#### Removed

- update

### bpy.types.CompositorNodeImage

#### Removed

- update

### bpy.types.CompositorNodeImageCoordinates

#### Removed

- update

### bpy.types.CompositorNodeImageInfo

#### Removed

- update

### bpy.types.CompositorNodeInpaint

#### Removed

- update

### bpy.types.CompositorNodeInvert

#### Removed

- update

### bpy.types.CompositorNodeKeying

#### Removed

- update

### bpy.types.CompositorNodeKeyingScreen

#### Removed

- update

### bpy.types.CompositorNodeKuwahara

#### Removed

- update

### bpy.types.CompositorNodeLensdist

#### Removed

- update

### bpy.types.CompositorNodeLevels

#### Removed

- update

### bpy.types.CompositorNodeLumaMatte

#### Removed

- update

### bpy.types.CompositorNodeMapUV

#### Removed

- update

### bpy.types.CompositorNodeMask

#### Removed

- update

### bpy.types.CompositorNodeMovieClip

#### Removed

- update

### bpy.types.CompositorNodeMovieDistortion

#### Removed

- update

### bpy.types.CompositorNodeNormal

#### Removed

- update

### bpy.types.CompositorNodeNormalize

#### Removed

- update

### bpy.types.CompositorNodeOutputFile

#### Removed

- update

### bpy.types.CompositorNodePixelate

#### Removed

- update

### bpy.types.CompositorNodePlaneTrackDeform

#### Removed

- update

### bpy.types.CompositorNodePosterize

#### Removed

- update

### bpy.types.CompositorNodePremulKey

#### Removed

- update

### bpy.types.CompositorNodeRGB

#### Removed

- update

### bpy.types.CompositorNodeRGBToBW

#### Removed

- update

### bpy.types.CompositorNodeRLayers

#### Removed

- update

### bpy.types.CompositorNodeRelativeToPixel

#### Removed

- update

### bpy.types.CompositorNodeRotate

#### Removed

- update

### bpy.types.CompositorNodeScale

#### Removed

- update

### bpy.types.CompositorNodeSceneTime

#### Removed

- update

### bpy.types.CompositorNodeSeparateColor

#### Removed

- update

### bpy.types.CompositorNodeSetAlpha

#### Removed

- update

### bpy.types.CompositorNodeSplit

#### Removed

- update

### bpy.types.CompositorNodeStabilize

#### Removed

- update

### bpy.types.CompositorNodeSwitch

#### Removed

- update

### bpy.types.CompositorNodeSwitchView

#### Removed

- update

### bpy.types.CompositorNodeTime

#### Removed

- update

### bpy.types.CompositorNodeTonemap

#### Removed

- update

### bpy.types.CompositorNodeTrackPos

#### Removed

- update

### bpy.types.CompositorNodeTransform

#### Removed

- update

### bpy.types.CompositorNodeTranslate

#### Removed

- update

### bpy.types.CompositorNodeVecBlur

#### Removed

- update

### bpy.types.CompositorNodeViewer

#### Removed

- update

### bpy.types.CompositorNodeZcombine

#### Removed

- update

### bpy.types.Curve

#### Added

- bpy.types.Curve.fill_rule

- bpy.types.Curve.fill_solver

### bpy.types.FFmpegSettings

#### Added

- bpy.types.FFmpegSettings.custom_constant_rate_factor

### bpy.types.GeometryNodeListGetItem

#### Added

- bpy.types.GeometryNodeListGetItem.socket_type

- bpy.types.GeometryNodeListGetItem.structure_type

#### Removed

- data_type

### bpy.types.GeometryNodeRealizeInstances

#### Added

- bpy.types.GeometryNodeRealizeInstances.realize_to_point_domain

### bpy.types.GeometryNodeStringToCurves

#### Removed

- align_x

- align_y

- font

- overflow

- pivot_mode

### bpy.types.GeometryNodeTree

#### Added

- bpy.types.GeometryNodeTree.node_tool_idname

### bpy.types.Gizmo

#### Added

- bpy.types.Gizmo.use_undo

### bpy.types.GreasePencil

#### Added

- bpy.types.GreasePencil.root_nodes

### bpy.types.GreasePencilLayerGroup

#### Added

- bpy.types.GreasePencilLayerGroup.children

### bpy.types.ImageStrip

#### Added

- bpy.types.ImageStrip.content_trim_end

- bpy.types.ImageStrip.content_trim_start

### bpy.types.MaskStrip

#### Added

- bpy.types.MaskStrip.content_trim_end

- bpy.types.MaskStrip.content_trim_start

### bpy.types.MetaStrip

#### Added

- bpy.types.MetaStrip.content_trim_end

- bpy.types.MetaStrip.content_trim_start

- bpy.types.MetaStrip.volume

### bpy.types.MovieClipStrip

#### Added

- bpy.types.MovieClipStrip.content_trim_end

- bpy.types.MovieClipStrip.content_trim_start

### bpy.types.MovieStrip

#### Added

- bpy.types.MovieStrip.content_trim_end

- bpy.types.MovieStrip.content_trim_start

### bpy.types.MovieTrackingCamera

#### Added

- bpy.types.MovieTrackingCamera.nuke_p1

- bpy.types.MovieTrackingCamera.nuke_p2

### bpy.types.MulticamStrip

#### Added

- bpy.types.MulticamStrip.content_trim_end

- bpy.types.MulticamStrip.content_trim_start

### bpy.types.NodeTreeInterfacePanel

#### Added

- bpy.types.NodeTreeInterfacePanel.select

### bpy.types.NodeTreeInterfaceSocket

#### Added

- bpy.types.NodeTreeInterfaceSocket.select

### bpy.types.Object

#### Added

- bpy.types.Object.shape_keys_selected

### bpy.types.Paint

#### Added

- bpy.types.Paint.show_bvh_nodes

### bpy.types.PointCloud

#### Added

- bpy.types.PointCloud.resize

### bpy.types.Preferences

#### Added

- bpy.types.Preferences.show_hidden_ids

### bpy.types.PreferencesExperimental

#### Added

- bpy.types.PreferencesExperimental.use_geometry_bundle

- bpy.types.PreferencesExperimental.use_paint_debug

### bpy.types.PreferencesInput

#### Added

- bpy.types.PreferencesInput.show_tablet_debug_values

### bpy.types.SceneEEVEE

#### Added

- bpy.types.SceneEEVEE.direct_light_intensity

- bpy.types.SceneEEVEE.indirect_light_intensity

### bpy.types.SceneStrip

#### Added 

- bpy.types.SceneStrip.content_trim_end

- bpy.types.SceneStrip.content_trim_start

### bpy.types.SequenceTimelineChannel 

#### Added 

- bpy.types.SequenceTimelineChannel.number

### bpy.types.ShaderNodeNormalMap 

#### Added 

- bpy.types.ShaderNodeNormalMap.base

- bpy.types.ShaderNodeNormalMap.convention

### bpy.types.ShapeKey 

#### Added 

- bpy.types.ShapeKey.select

### bpy.types.SoundStrip 

#### Added 

- bpy.types.SoundStrip.content_trim_end

- bpy.types.SoundStrip.content_trim_start

### bpy.types.SpacePreferences 

#### Added 

- bpy.types.SpacePreferences.search_filter

- bpy.types.SpacePreferences.tab_search_results

### bpy.types.SpaceSpreadsheet 

#### Added 

- bpy.types.SpaceSpreadsheet.geometry_item_type

### bpy.types.SpaceUVEditor 

#### Added 

- bpy.types.SpaceUVEditor.uv_edge_opacity

### bpy.types.SpreadsheetTableIDGeometry 

#### Added 

- bpy.types.SpreadsheetTableIDGeometry.geometry_item_type

### bpy.types.Strip 

#### Added 

- bpy.types.Strip.content_duration

- bpy.types.Strip.content_end

- bpy.types.Strip.content_start

- bpy.types.Strip.duration

- bpy.types.Strip.left_handle

- bpy.types.Strip.left_handle_offset

- bpy.types.Strip.right_handle

- bpy.types.Strip.right_handle_offset

### bpy.types.ThemeDopeSheet 

#### Renamed 

- interpolation_line -> bpy.types.ThemeDopeSheet.anim_interpolation_constant

- interpolation_line -> bpy.types.ThemeDopeSheet.anim_interpolation_linear

- interpolation_line -> bpy.types.ThemeDopeSheet.anim_interpolation_other

### bpy.types.ThemePreferences 

#### Added 

- bpy.types.ThemePreferences.match

### bpy.types.ThemeView3D 

#### Added 

- bpy.types.ThemeView3D.gp_wire_edit

- bpy.types.ThemeView3D.grid_major

### bpy.types.UILayout 

#### Added 

- bpy.types.UILayout.template_ID_session_uid

- bpy.types.UILayout.template_node_operator_registration_errors

#### Function Arguments 

- bpy.types.UILayout.popover (panel, text, text_ctxt, translate, icon, icon_value, direction), was (panel, text, text_ctxt, translate, icon, icon_value)

- bpy.types.UILayout.prop_tabs_enum (data, property, data_highlight, property_highlight, icon_only, expand_as), was (data, property, data_highlight, property_highlight, icon_only)

### bpy.types.UserAssetLibrary 

#### Added 

- bpy.types.UserAssetLibrary.enabled

### bpy.types.`VIEWLAYER_UL`_aov 

#### Added 

- bpy.types.`VIEWLAYER_UL`_aov.aov_icon

### bpy.types.View3DOverlay 

#### Added 

- bpy.types.View3DOverlay.show_performance

### bpy.types.Window 

#### Added 

- bpy.types.Window.find_playing_scene

### bpy.types.WindowManager 

#### Added 

- bpy.types.WindowManager.extension_repo_filter

- bpy.types.WindowManager.extension_use_filter

### bpy.types.XrSessionSettings 

#### Added 

- bpy.types.XrSessionSettings.view_scale

### bpy.types.XrSessionState 

#### Added 

- bpy.types.XrSessionState.viewer_scale

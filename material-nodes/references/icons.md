# Icons, Maintenance, Templates, License ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Icons; Maintenance; Templates; License; 3D Cursor; Active Element; Bounding Box Center; Individual Origins; Proportional Editing; Viewport Gizmos.

## Icons

Blender icons can be embedded in the manual with this syntax:
```text
:bl-icon:`<icon_name>`
```
The available icon names follow below.

The available Blender icon names (each usable as `:bl-icon:`<name>``): action, action_slot, action_tweak, add, aliased, align_bottom, align_center, align_flush, align_justify, align_left, align_middle, align_right, align_top, anchor_bottom, anchor_center, anchor_left, anchor_right, anchor_top, anim, anim_data, antialiased, append_blend, area_dock, area_join, area_join_down, area_join_left, area_join_up, area_swap, armature_data, arrow_leftright, asset_manager, auto, automerge_off, automerge_on, axis_front, axis_side, axis_top, back, blank1, blender, blender_logo_large, boids, bold, bone_data, bookmarks, bordermove, brush_data, brushes_all, camera_data, camera_stereo, cancel, cancel_large, center_only, char_notdef, char_replacement, checkbox_dehlt, checkbox_hlt, checkmark, clipuv_dehlt, clipuv_hlt, collapsemenu, collection_color_01 through collection_color_08, collection_new, color, color_blue, color_green, color_red, community, con_action, con_armature, con_camerasolver, con_childof, con_clampto, con_distlimit, con_floor, con_followpath, con_followtrack, con_geometryattribute, con_kinematic, con_locktrack, con_loclike, con_loclimit, con_objectsolver, con_pivot, con_rotlike, con_rotlimit, con_samevol, con_shrinkwrap, con_sizelike, con_sizelimit, con_splineik, con_stretchto, con_trackto, con_transform, con_transform_cache, con_translike, cone, console, constraint, constraint_bone, copy_id, copydown, cube, current_file, cursor, curve_bezcircle, curve_bezcurve, curve_data, curve_ncircle, curve_ncurve, curve_path, curves, curves_data, decorate, decorate_animate, decorate_driver, decorate_keyframe, decorate_library_override, decorate_linked, decorate_locked, decorate_override, decorate_unlocked, desktop, disc, disc_large, disclosure_tri_down, disclosure_tri_right, disk_drive, disk_drive_large, documents, dot, downarrow_hlt, driver, driver_distance, driver_rotational_difference, driver_transform, duplicate, edge_bevel, edge_crease, edge_seam, edge_sharp, edgesel, editmode_hlt, empty_arrows, empty_axis, empty_data, empty_single_arrow, error, experimental, export, external_drive, external_drive_large, eyedropper, face_corner, face_maps, facesel, fake_user_off, fake_user_on, fcurve, fcurve_snapshot, ff, file, file_3d, file_alias, file_archive, file_backup, file_blank, file_blend, file_cache, file_folder, file_folder_large, file_font, file_hidden, file_image, file_large, file_movie, file_new, file_parent, file_parent_large, file_refresh, file_script, file_sound, file_text, file_tick, file_volume, filebrowser, filter, fixed_size, folder_redirect, font_data, fontpreview, force_boid, force_charge, force_curve, force_drag, force_fluidflow, force_force, force_harmonic, force_lennardjones, force_magnetic, force_texture, force_turbulence, force_vortex, force_wind, forward, frame_next, frame_prev, freeze, fullscreen_enter, fullscreen_exit, fund, geometry_nodes, geometry_set, gesture_pan, gesture_rotate, gesture_zoom, ghost_disabled, ghost_enabled, gizmo, gp_caps_flat, gp_caps_round, gp_multiframe_editing, gp_only_selected, gp_select_between_strokes, gp_select_points, gp_select_strokes, graph, greasepencil, greasepencil_layer_group, grid, grip, grip_v, group, group_bone, group_uvs, group_vcol, group_vertex, hand, handle_aligned, handle_auto, handle_autoclamped, handle_free, handle_vector, heart, help, hide_off, hide_on, holdout_off, holdout_on, home, hook, image, image_alpha, image_background, image_data, image_plane, image_reference, image_rgb, image_rgb_alpha, image_zdepth, imgdisplay, import, indirect_only_off, indirect_only_on, info, info_large, internet, internet_offline, inversesquarecurve, ipo_back, ipo_bezier, ipo_bounce, ipo_circ, ipo_constant, ipo_cubic, ipo_ease_in, ipo_ease_in_out, ipo_ease_out, ipo_elastic, ipo_expo, ipo_linear, ipo_quad, ipo_quart, ipo_quint, ipo_sine, italic, key_backspace, key_backspace_filled, key_command, key_command_filled, key_control, key_control_filled, key_dehlt, key_empty1, key_empty1_filled, key_empty2, key_empty2_filled, key_empty3, key_empty3_filled, key_hlt, key_menu, key_menu_filled, key_option_filled, key_return, key_return_filled, key_ring, key_ring_filled, key_shift, key_shift_filled, key_tab, key_tab_filled, key_windows_filled, keyframe, keyframe_hlt, keyingset, lattice_data, layer_active, layer_used, library_data_broken, library_data_direct, library_data_override, light, light_area, light_data, light_hemi, light_point, light_spot, light_sun, lightprobe_plane, lightprobe_sphere, lightprobe_volume, lincurve, line_data, linenumbers_off, linenumbers_on, link_blend, linked, locked, lockview_off, lockview_on, longdisplay, loop_back, loop_forwards, marker, marker_hlt, mat_sphere_sky, matcloth, matcube, material, material_data, matfluid, matplane, matshaderball, matsphere, memory, menu_panel, mesh_capsule, mesh_circle, mesh_cone, mesh_cube, mesh_cylinder, mesh_data, mesh_grid, mesh_icosphere, mesh_monkey, mesh_plane, mesh_torus, mesh_uvsphere, meta_ball, meta_capsule, meta_cube, meta_data, meta_ellipsoid, meta_plane, mod_armature, mod_array, mod_bevel, mod_boolean, mod_build, mod_cast, mod_cloth, mod_curve, mod_curves, mod_dash, mod_data_transfer, mod_decim, mod_displace, mod_dynamicpaint, mod_edgesplit, mod_envelope, mod_explode, mod_fluid, mod_fluidsim, mod_hue_correct, mod_hue_saturation, mod_instance, mod_lattice, mod_length, mod_lineart, mod_mask, mod_meshdeform, mod_mirror, mod_multires, mod_noise, mod_normaledit, mod_ocean, mod_offset, mod_opacity, mod_outline, mod_particle_instance, mod_particles, mod_physics, mod_remesh, mod_screw, mod_shrinkwrap, mod_simpledeform, mod_simplify, mod_skin, mod_smooth, mod_soft, mod_solidify, mod_subsurf, mod_thickness, mod_time, mod_tint, mod_tonemap, mod_triangulate, mod_uvproject, mod_vertex_weight, mod_warp, mod_wave, mod_white_balance, mod_wireframe, modifier, modifier_data, modifier_off, modifier_on, monkey, mouse_lmb, mouse_lmb_2x, mouse_lmb_drag, mouse_mmb, mouse_mmb_drag, mouse_mmb_scroll, mouse_move, mouse_rmb, mouse_rmb_drag, mute_ipo_off, mute_ipo_on, network_drive, network_drive_large, newfolder, next_keyframe, nla, nla_pushdown, nocurve, node, node_compositing, node_corner, node_insert_off, node_insert_on, node_material, node_sel, node_side, node_texture, node_top, nodetree, none, normalize_fcurves, normals_face, normals_vertex, normals_vertex_face, not_found, object_data, object_datamode, object_hidden, object_origin, onionskin_off, onionskin_on, options, orientation_cursor, orientation_gimbal, orientation_global, orientation_local, orientation_normal, orientation_parent, orientation_view, orphan_data, outliner, outliner_collection, outliner_data_armature, outliner_data_camera, outliner_data_curve, outliner_data_curves, outliner_data_empty, outliner_data_font, outliner_data_gp_layer, outliner_data_greasepencil, outliner_data_lattice, outliner_data_light, outliner_data_lightprobe, outliner_data_mesh, outliner_data_meta, outliner_data_pointcloud, outliner_data_speaker, outliner_data_surface, outliner_data_volume, outliner_ob_armature, outliner_ob_camera, outliner_ob_curve, outliner_ob_curves, outliner_ob_empty, outliner_ob_font, outliner_ob_force_field, outliner_ob_greasepencil, outliner_ob_group_instance, outliner_ob_image, outliner_ob_lattice, outliner_ob_light, outliner_ob_lightprobe, outliner_ob_mesh, outliner_ob_meta, outliner_ob_pointcloud, outliner_ob_speaker, outliner_ob_surface, outliner_ob_volume, output, overlay, package, panel_close, particle_data, particle_path, particle_point, particle_tip, particlemode, particles, pastedown, pasteflipdown, pasteflipup, pause, physics, pinned, pivot_active, pivot_boundbox, pivot_cursor, pivot_individual, pivot_median, play, play_reverse, play_sound, playhead_snap_off, playhead_snap_on, plugin, plus, pmarker, pmarker_act, pmarker_sel, pointcloud_data, pointcloud_point, pose_hlt, preferences, preset, preset_new, prev_keyframe, preview_loading, preview_range, prop_con, prop_off, prop_on, prop_projected, properties, question, question_large, quit, radiobut_off, radiobut_on, rec, record_off, record_on, recover_last, remove, render_animation, render_result, render_still, renderlayers, restrict_color_off, restrict_color_on, restrict_instanced_off, restrict_instanced_on, restrict_render_off, restrict_render_on, restrict_select_off, restrict_select_on, restrict_view_off, restrict_view_on, rew, rightarrow, rightarrow_thin, rigid_body, rigid_body_constraint, rna, rna_add, rndcurve, rootcurve, scene, scene_data, screen_back, script, scriptplugins, sculptmode_hlt, select_difference, select_extend, select_intersect, select_set, select_subtract, seq_chroma_scope, seq_histogram, seq_luma_waveform, seq_preview, seq_sequencer, seq_splitview, seq_strip_duplicate, seq_strip_meta, seq_strip_modifier, sequence, settings, shaderfx, shading_bbox, shading_rendered, shading_solid, shading_texture, shading_wire, shapekey_data, sharpcurve, shortdisplay, small_caps, smoothcurve, snap_edge, snap_face, snap_face_center, snap_face_nearest, snap_grid, snap_increment, snap_midpoint, snap_normal, snap_off, snap_on, snap_peel_object, snap_perpendicular, snap_vertex, snap_volume, solo_off, solo_on, sort_asc, sort_desc, sortalpha, sortbyext, sortsize, sorttime, sound, speaker, sphere, spherecurve, split_horizontal, split_vertical, spreadsheet, statusbar, sticky_uvs_disable, sticky_uvs_loc, sticky_uvs_vert, strands, stroke, stylus_pressure, surface_data, surface_ncircle, surface_ncurve, surface_ncylinder, surface_nsphere, surface_nsurface, surface_ntorus, syntax_off, syntax_on, system, tag, temp, text, texture, texture_data, three_dots, time, tool_settings, topbar, tpaint_hlt, tracker, tracker_data, tracking, tracking_backwards, tracking_backwards_single, tracking_clear_backwards, tracking_clear_forwards, tracking_forwards, tracking_forwards_single, tracking_refine_backwards, tracking_refine_forwards, transform_origins, trash, tria_down, tria_down_bar, tria_left, tria_left_bar, tria_right, tria_right_bar, tria_up, tria_up_bar, uglypackage, underline, unlinked, unlocked, unpinned, url, user, uv, uv_data, uv_edgesel, uv_facesel, uv_islandsel, uv_sync_select, uv_vertexsel, vertex_crease, vertexsel, view3d, view_camera, view_camera_unselected, view_locked, view_ortho, view_pan, view_perspective, view_unlocked, view_zoom, viewzoom, vis_sel_00, vis_sel_01, vis_sel_10, vis_sel_11, volume_data, vpaint_hlt, warning_large, window, wordwrap_off, wordwrap_on, workspace, world, world_data, wpaint_hlt, x, xray, zoom_all, zoom_in, zoom_out, zoom_previous, zoom_selected.

## Maintenance

Adding, removing, or moving files — when RST files are added or removed, the update script adds or removes the matching locale files automatically. To move files, however, use this Python script first:
```text
python tools/utils_maintenance/rst_remap.py start
```
You can then move the RST files freely, and the remap script relocates the locale file afterward:
```text
python tools/utils_maintenance/rst_remap.py finish
```
Avoid moving or renaming files where possible, since it breaks URLs and, without this script, translators lose all their work in those files — ask an administrator if you think something should be renamed or moved. (The script also handles image file names.) Release checklist: create a release branch (blender-3.2-release/); update the splash image, interface_splash_current.png, in the release branch; and bump the conf.py blender_version variable in the trunk version.

## Templates

This guide gives patterns for documenting interface elements and directories. Operator menus — each operator gets its own heading or page depending on content length, opening with a reference admonition documenting the operator's context:
```text
.. reference::

   :Mode: Edit Mode
   :Menu: :menuselection:`Curve --> Snap`
   :Shortcut: :kbd:`Shift-S`
```
Panels — document each panel under its own heading, with nested panels at decreasing heading levels; a panel may warrant its own page by documentation length or panel count, and expanded menus that toggle which properties show should be treated like subpanels:
```text
Panel Title
===========

Nested Panel Title
------------------
```
Properties — document with definition lists, using nested definitions for properties hidden behind other properties:
```text
Property
   Property description.

   Hidden Property
      Hidden property description.
```
Document select menus like:
```text
Menu Label
   General description of the menu.

   :Menu Item: Menu Item Definition.
   :Menu Item: Menu Item Definition.
   :Menu Item: Menu Item Definition.
```
Nodes — always give three headings (inputs, properties, outputs), noting absence where the node has none, with an optional example(s) section at the end of the page:
```text
**********
World Node
**********

.. figure:: /images/render_shader-nodes_output_world_node.png
   :align: right

   The World node.

Introduction and general use case(s).

Inputs
======

This node has no inputs.

Properties
==========

This node has no properties.

Outputs
=======

This node has no outputs.

Example
=======
```
Directory layout — structure sections generally as a directory holding index.rst (links to internal files), introduction.rst, then section_1.rst, section_2.rst, and so on; for example:
```text
- rendering/
  - index.rst
  - cycles/
    - index.rst
    - introduction.rst
  - materials/
    - index.rst
    - introduction.rst
    - volumes.rst
```
The idea is to enclose all of a section's content in a folder, ideally with an index.rst (the section's TOC) and an introduction.rst (introducing its contents). Table of contents — by default show two levels of depth:
```text
.. toctree::
   :maxdepth: 2

   introduction.rst
   perspective.rst
   depth_of_field.rst
```

## License

Blender itself is released under the GNU General Public License (GPL); details are at blender.org/about/license. Logos, trademarks, icons, source code, and Python scripts carry their own terms separate from the manual text. (The manual's prose has its own documentation license, covered on Blender's site, and questions about it can go to the Blender Foundation at foundation (at) blender (dot) org.)

## 3D Cursor

3D Cursor (pivot point) — Reference: Mode: Object Mode and Edit Mode; Location: Header ‣ Transform Pivot Point ‣ 3D Cursor; Shortcut: Period. Places the pivot point at the 3D Cursor's location. Example: the manual's image contrasts rotating an object around the 3D Cursor (left) with rotating it around the Median Point (right).

## Active Element

Active Element (pivot point) — Reference: Mode: Object Mode and Edit Mode; Location: Header ‣ Transform Pivot Point ‣ Active Element; Shortcut: Period. Places the pivot point at the active element, the one selected most recently. In Object Mode: rotation and scaling occur around the active object's origin — the object with a lighter outline than the others — so, as the manual's image shows, the active object (the cube) stays put while the others move. In Edit Mode: rotation and scaling occur around the active element's centerpoint — the element with a white outline — which stays put while everything else transforms around it; the manual illustrates rotation around the active vertex, edge, and face, where the active element rotates in place while the others "orbit" it (for vertices, the active vertex doesn't change at all, since a lone vertex is just a point with no concept of rotation).

## Bounding Box Center

Bounding Box Center (pivot point) — Reference: Mode: Object Mode and Edit Mode; Location: Header ‣ Transform Pivot Point ‣ Bounding Box Center; Shortcut: Period. Here the pivot point sits at the center of the bounding box — the box wrapped as tightly as possible around the selection while staying aligned to the world axes. In Object Mode: the pivot lands at the midpoint of the box enclosing the selected objects' origin points rather than their geometry, so for a single selected object the pivot equals the object's origin point (which can be customized and needn't be centered — in the manual's example the orange rectangle has it in a corner). With multiple objects selected, the pivot becomes the center of an imaginary box around their origins; the manual contrasts this with Median Point, which instead averages the origins' positions, so the pivot shifts toward the area with the most objects. In Edit Mode: the pivot becomes the center of the bounding box around the selected mesh elements (the manual shows rotation in different selection modes with the pivot as a yellow circle), and again Median Point may give a different result.

## Individual Origins

Individual Origins (pivot point) — Reference: Mode: Object Mode and Edit Mode; Location: Header ‣ Transform Pivot Point ‣ Individual Origins; Shortcut: Period. Unlike the other pivot modes, which move the entire selection about a single point, Individual Origins works on each item about its own center. In Object Mode: each object transforms around its own origin, a freely chosen point that needn't be centered (in the manual's example the orange rectangle has it in a corner); the manual's images compare Individual Origins to Median Point. In Edit Mode: each selected element transforms around its own centerpoint, and when you transform adjacent faces or edges they're treated as a single element, so they don't become disconnected.

## Proportional Editing

Reference — Mode: Object and Edit Mode. Location: Header ‣ Proportional Editing. Shortcut: O.

Proportional Editing transforms your current selection while also pulling along the unselected geometry around it. Influence drops off with distance — the more remote an unselected element is, the smaller the effect it receives (which is where the name comes from). It shines when you need to deform dense meshes gently.

Note: Blender's Sculpting workflow is an alternative, offering brushes and tools that proportionally reshape a mesh without exposing the individual vertices.

Controls:
Disable (O) — the feature is off and only the selected vertices respond.
Enable (O) — geometry beyond the selection is affected too, out to a set radius.

Proportional Size: during a transform you can grow or shrink the tool's reach from the Proportional Editing popover, or with WheelUp / WheelDown, or PageUp / PageDown. As the radius changes, the points around your selection reposition to match.

Falloff: mid-edit you can swap the curve profile either by clicking the Falloff icon in the header or by pressing Shift-O for a pie menu. The available profiles are Constant (No Falloff), Random, Linear, Sharp, Root, Sphere, Smooth, and Inverse Square.

Object Mode: although Proportional Editing lives mostly in Edit Mode, it works in Object Mode as well, where it acts on whole objects instead of individual mesh components. In the illustrated case the leftmost cylinder is being scaled upward, and the cylinders beside it are pulled along too.

Edit Mode: on heavy geometry, nudging things subtly without leaving visible bumps and ridges in the surface is hard, and that is exactly where Proportional Editing earns its keep.

Options:
Connected Only (Alt-O) — rather than relying on a plain radius, the falloff propagates through linked geometry. That lets you proportionally edit the vertices of one finger on a hand without disturbing the neighboring fingers: those other vertices are near in 3D space yet distant when you follow the mesh's edge connectivity. The icon shows a blue center while Connected is active, and the mode exists only in Edit Mode.
Projected from View — distance along the viewing direction is disregarded when the radius is applied.

Example: the sample render of a low-poly landscape was produced simply by raising the vertices of a triangulated grid with Proportional Editing turned on.

## Viewport Gizmos

Reference — Mode: All Modes. Location: Header ‣ Gizmos.

Clicking Show Gizmos toggles every gizmo in the 3D Viewport, while the adjacent drop-down opens a popover of finer settings, covered below.

Viewport Gizmos:
Navigate — turns the navigation gizmo on or off.
Active Tool — turns the active tool's gizmo on or off.
Active Object — turns the Object Gizmos on or off for the active element (see below).

Object Gizmos let you translate, rotate, and scale interactively with the mouse in the 3D Viewport. They're labeled "object" gizmos in the popover, but they also serve other transformable items such as mesh vertices. Each operation gets its own gizmo, usable on its own or alongside the others. Every gizmo carries three color-coded axes — X (red), Y (green), Z (blue) — and dragging an axis with LMB transforms along it; the Move and Scale gizmos add small colored squares that transform along two axes simultaneously.

Several modifier keys apply:
Holding Ctrl at any moment toggles snapping and also makes rotation and scaling jump in coarse steps.
Holding Shift after the LMB press does the reverse — it "slows" the transform relative to mouse motion for finer control.
Holding Shift before the LMB press constrains the transform to the plane perpendicular to the axis you clicked (see Plane Locking).

The Gizmos popover exposes these object-gizmo settings:
Orientation — the orientation the gizmo uses; Default adopts the viewport's Transform Orientation, while the remaining choices override it.
Move — shows the location gizmo; dragging its small white circle frees movement within the viewing plane.
Rotate — shows the rotation gizmo; dragging the large white circle rotates about the viewing direction, and dragging the faint white disc inside it (visible only on hover) gives trackball rotation.
Scale — shows the scale gizmo; dragging the band between the small and large white circles scales on all three axes at once.
Those last three also appear in a pie menu if the Grave Accent / Tilde Action in your Keymap Preferences is set to Gizmos.
Note: if you're on a tool bound to its own gizmo setup (Move, Rotate, Scale, or Transform), the Move/Rotate/Scale checkboxes do nothing.
See also the Gizmo Preferences.

Empty — gizmo settings for empties: Image (a gizmo for adjusting the image's size and position) and Force Field (a gizmo for tuning the force field).

Light — gizmo settings for lights: Size (adjusts a spotlight's Spot Size) and Look At (adjusts a light's direction).

Camera — gizmo settings for cameras: Lens (adjusts focal length for Perspective cameras or orthographic scale for Orthographic ones) and Focus Distance (a gizmo for the focus distance; to see it, enable Viewport Display ‣ Limits in the camera's properties).

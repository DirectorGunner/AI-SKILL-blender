# Text Editor, Distance Node, Value To Normal Node, At Node ...

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Text Editor; Distance Node; Value to Normal Node; At Node; Coordinates Node; Texture Node; Output Node; Bricks Node; Checker Node; Timeline; UV Overlays; Selecting UVs; Pivot Point; Preview Snapping.

## Text Editor

This editor handles Python scripts, scripting-based shaders like OSL and GLSL, or just plain text notes. Open it by switching to the Scripting workspace or pressing Shift-F11 to replace the current editor.

Header — a freshly opened Text editor is empty with a bare header; more options surface once a text file is created or opened.
Editor Type — the standard editor-selection button.
Menus — the editor's menus.
Resolve Conflict — sorts out modified-file conflicts when an external text file is changed by another program.
Reload from Disk — re-reads the file from drive, discarding local changes.
Make Text Internal — turns the external text data-block into an internal one.
Ignore — hides the warning until the external file is modified externally again.
Text — a data-block menu to choose a text or create a new one; the header then changes.
Run Script (play icon) — runs the text as a Python script (Alt-P); see Template Menu.
Show — toggles for line numbers, word wrapping, and syntax highlighting.
Script Node Update (refresh icon) — with an OSL file open, refreshes the Shader Script node with the script's new options and sockets.

View Menu:
Sidebar (Ctrl-T) — shows or hides the Sidebar.
Line Numbers — shows the file's line numbers at the left of the Main View.
Word Wrap — wraps words too wide for the horizontal space onto a new "pseudo line".
Syntax Highlight — colors the special words of the Python language in the Main View.
Highlight Line — emphasizes the active line by tinting its background.
Zoom In/Out — grows/shrinks the main view's font size.
Navigation:
  Top (Ctrl-Home) — moves the view and cursor to the file's start.
  Bottom (Ctrl-End) — moves the view and cursor to the file's end.
  Line Begin (Home) — moves the cursor to the current line's start.
  Line End (End) — moves the cursor to the current line's end.
  Previous Line (Up) — moves the cursor to the same spot on the line above.
  Next Line (Down) — moves the cursor to the same spot on the line below.
  Previous Word (Ctrl-Left) — moves the cursor to the previous word's start; mid-word, to the current word's start.
  Next Word (Ctrl-Right) — moves the cursor to the next word's end; mid-word, to the current word's end.

Text Menu:
New (Alt-N) — creates a new text Data Block.
Open (Alt-O) — loads an external text file chosen via the File Browser.
Reload (Alt-R) — reopens the current buffer, losing any unsaved changes.
Edit Externally — edits the text file in an external editor, configurable in the User Preferences.
Save (Alt-S) — saves an already-open file.
Save As (Shift-Ctrl-Alt-S) — saves the text as a new file; a File Browser opens to pick the directory, name, and extension.
Register — runs the text data-block as a Python script when the blend-file loads; see the API documentation on registering Python modules.
Live Edit — runs the Python script after every change you make.
Run Script (Alt-P) — runs the text as a Python script; see Running Scripts.

Edit Menu:
Undo/Redo — see Undo & Redo.
Cut (Ctrl-X) — cuts the marked text to the clipboard.
Copy (Ctrl-C) — copies the marked text to the clipboard.
Paste (Ctrl-V) — pastes from the clipboard at the cursor.
Duplicate Line (Ctrl-D) — duplicates the current line.
Move Line(s) Up (Shift-Ctrl-Up) — swaps the current/selected line(s) with those above.
Move Line(s) Down (Shift-Ctrl-Down) — swaps the current/selected line(s) with those below.
Find & Replace (Ctrl-F) — shows the Find & Replace panel in the Sidebar.
Find & Set Selection (Ctrl-G) — finds the next instance of the selected text.
Jump To (Ctrl-J) — pops up to let you pick a line number to jump the cursor to.
Text Auto Complete (Tab) — shows a selectable list of words already in the text.
Text to 3D Object — converts the text file to a Text Object, either as One Object or One Object Per Line.

Select Menu:
All (Ctrl-A) — selects the whole file.
Line (Shift-Ctrl-A) — selects the whole current line.
Word (double-click LMB) — selects the whole current word.
Top (Shift-Ctrl-Home) — selects everything above the cursor.
Bottom (Shift-Ctrl-End) — selects everything below the cursor.
Line Begin (Shift-Home) — selects from the current line's start to the cursor.
Line End (Shift-End) — selects from the cursor to the current line's end.
Previous Line (Shift-Up) — selects from the cursor to the matching spot one line up.
Next Line (Shift-Down) — selects from the cursor to the matching spot one line down.
Previous Word (Shift-Ctrl-Left) — selects from the cursor to the previous word's start; mid-word, to the current word's start.
Next Word (Shift-Ctrl-Right) — selects from the cursor to the next word's end; mid-word, to the current word's end.

Format Menu:
Indent (Tab) — inserts a tab character at the cursor.
Unindent (Shift-Tab) — unindents the selection.
Toggle Comments (Ctrl-Slash) — toggles whether the selected line(s) are a Python comment; with nothing selected, it toggles the current line.
Convert Whitespace — converts indentation characters To Spaces or To Tabs.

Template Menu — holds a set of templates for both Python and Open Shading Language scripts.

Main View — typing produces text in the buffer. As usual, press-drag-release LMB selects text and RMB opens the context menu. Tip: the Text editor is also handy for sharing a blend-file — leave a note explaining the file's structure, and keep the editor visible when you save so others spot it.

Sidebar — Find & Replace:
Find Text (Ctrl-F) — searches for instances of a text after the cursor; the eyedropper icon searches for the currently selected text and selects the match, and Find Next jumps to the next one.
Replace Text (Ctrl-H) — searches for the Find Text and swaps in the new text; the eyedropper icon sets the selected text as the replacement, Replace finds and swaps the next match, and Replace All swaps every occurrence.
Case — makes the search mind upper- and lowercase.
Wrap — restarts the search from the file's start once it reaches the end.
All — searches every text data-block, not just the active one.
Properties:
  Margin — shows a vertical margin line to help keep lines a sensible length; its position is the Margin Column.
  Font Size (Ctrl-WheelUp) — the size of the text font.
  Tab Width — how many character spaces a tab is drawn with.
  Indentation — whether indentation uses Tabs or Spaces.

Footer — the Text editor footer says whether the text is saved internally or externally and whether an external file has unsaved changes; for external files it also shows the file path.

Usage — Running Scripts: the standout keystroke is Alt-P, which runs the current text as a Python script. You can reach not just the standard Python modules but a whole set of Blender-specific ones too; see Scripting & Extending Blender.

## Distance Node

Works out the distance between two 3D coordinates.

Inputs:
Coordinate 1 — the first coordinate point.
Coordinate 2 — the second coordinate point.

Properties — this node exposes no properties.

Outputs:
Value — the computed distance.

## Value to Normal Node

Computes a normal map.

Inputs:
Val — the heightmap to derive the normal map from.
Nabla — the size of the derivative offset used when computing normals.

Properties — this node exposes no properties.

Outputs:
Normal — the usual normal output.

## At Node

Returns a texture's color at the given coordinates.

Inputs:
Texture — the usual color input.
Coordinates — the point to sample the color at; for images the space runs -1 to 1 in X and Y. If the coordinates don't vary spatially, the node returns a single color.

Properties — this node exposes no properties.

Outputs:
Texture — the usual color output.

## Coordinates Node

Inputs — this node takes no inputs.

Properties — this node exposes no properties.

Outputs:
Coordinates — outputs the geometry's local coordinates, measured against the bounding box.

## Texture Node

The Texture node loads another texture, node-based or not.

Inputs — these two colors can remap a grayscale texture.
Color 1 — White Level.
Color 2 — Black Level.

Properties:
Texture — the texture to load, from the current blend-file or a linked one.

Outputs:
Color — the usual color output.

## Output Node

This node receives the node-based texture's result.

Inputs:
Color — the color data the texture renders.

Properties:
Output Name — the output's name. (Textures could once have several differently named outputs.)

Outputs — this node produces no outputs.

## Bricks Node

The Bricks node builds a brick-like pattern.

Inputs:
Bricks 1, Bricks 2 — the bricks' color range; each brick's color is chosen at random between these two.
Mortar — the mortar color between the bricks.
Thickness — the mortar's thickness.
Bias — the bias of the random color pick, from -1 to 1; -1 makes every brick Color 1 and 1 makes them all Color 2.
Brick Width — the horizontal size of every brick.
Row Height — the vertical size of every brick.

Properties:
Offset — the relative offset of the next brick row.
Frequency — offset every N rows; the offset pattern repeats every N rows.
Squash — squeezes the bricks in those repeating N-row groups by this amount.
Frequency — squash every N rows.

Outputs:
Color — the usual color output.

## Checker Node

The Checker node builds a checkerboard pattern.

Inputs:
Color 1, Color 2 — the squares' colors.
Size — the checker pattern's scale.

Properties — this node exposes no properties.

Outputs:
Color — the usual color output.

## Timeline

The Timeline editor lets you jump between frames, work with keyframes, and drive animation playback.

Main View — the X axis is time, the figures 0/50/100/… are frame numbers; the blue line is the Playhead flagging the current frame, and the diamonds are Keyframes — points where you fixed a property's value at a given time.
Adjusting the View — pan by dragging MMB; zoom by dragging Ctrl-MMB, rolling the Wheel, or pressing NumpadMinus / NumpadPlus; the scrollbars at the bottom and right work too.
Frame Range — the Frame Range sets the scene animation's length, defaulting to frames 1 through 250; change it via the header's Start/End inputs or through the Output Properties.
Keyframes — by default the timeline shows only the selected items' keyframes; uncheck View ‣ Only Show Selected to show them all. Click a keyframe to select it alone, or Shift-click to add it to (or remove it from) the selection, and drag a box to grab several at once. Move the selected keyframes by dragging one, or press G, move the mouse, and click LMB to confirm (RMB to cancel); press S to scale them about the Playhead.
Markers — see the Markers page.

Header — Playback and Keying popovers, plus transport and frame controls.
View Menu:
  Adjust Last Operation — opens a pop-up to alter the last operation's properties (see Adjust Last Operation).
  Channels — shows or hides the Channels region, the left-hand tree of objects and their animatable properties.
  Frame All (Home) — pans and zooms so every keyframe is visible.
  Frame Scene/Preview Range — resets the horizontal view to the scene frame range, honoring the preview range if active.
  Go to Current Frame (Numpad0) — centers the Timeline on the Playhead.
  Show Markers — shows the Markers region (when markers exist); off, the Marker Menu hides and marker operators are unavailable here.
  Use Timecode (Ctrl-T) — shows the X-axis time and the Playhead as timestamps rather than frame numbers; e.g. 01:03+02 reads "1 minute, 3 seconds, 2 frames."
  Sync Visible Range — keeps the editor's horizontal pan and scale in step with other time-based editors that enable this, so they show the same slice of time.
  Only Show Selected — shows only keyframes tied to the selected items (objects, bones, nodes, and so on). Note: with this on, the Timeline may omit some material keyframes of the selected objects, showing instead only those for the nodes selected in the Shader Editor.
  Only Show Errors — shows only curves and drivers that are disabled or in error, handy for debugging.
  Cache — picks which simulation caches appear on the timeline; see Cache.
  Area — area controls; see the user-interface documentation.
Marker Menu — markers flag frames carrying key points or notable events and, as in most animation editors, appear along the Timeline's bottom. For the marker tools, see Editing Markers.
Playback Popover — properties for how animations play; see Playback.
Keying Popover — properties for how keyframes are added; see Keying.
Auto Keying — options for adding keyframes automatically; see Auto Keying.
Transport Controls — buttons that drive playback; see Transport Controls.
Frame Controls — set the current frame and the start/end frames; see Frame Controls.

## UV Overlays

A header button switches all the UV Editor's overlays off, which also toggles UDIM tile information. The drop-down opens a pop-over of finer settings, in these categories:

Guides:
Grid — shows the grid.
Over Image — draws the grid over the image rather than behind it.
Grid Shape Source — how the row and column counts are set. Dynamic (starts at 8×8 cells, subdividing further as you zoom in), Fixed (manually configured fixed counts), or Pixel (each cell matches one image pixel).
Fixed Subdivisions X, Y — the grid's column/row counts.
Tiles X, Y — how many UDIM tile grids to show in each cardinal direction.

UV Editing:
Display Stretch — shows how much shape difference there is between UV space and 3D space; blue is low distortion, red is high. You can base the display on Angle or Area.

Geometry:
Display UVs — shows the active UV map as an overlay in the UV Editor.
Faces — the opacity of face fill colors in UV overlays.
Edges — the opacity of edge colors in UV overlays.
UV Opacity (Edit Mode) — the opacity of edges and faces.
Display As (Edit Mode) — how edges are drawn. Outline (gray with a black outline), Dash (dashed black-gray lines), Black (black), or White (white).
Modified Edges (Edit Mode) — additionally shows the edges as they'd look after modifiers (in gray).
Faces (Edit Mode) — draws faces over the image.

Image:
Show Metadata — shows metadata about the selected Render Result; change what's included via the Output tab's Metadata panel.

## Selecting UVs

As in the 3D Viewport, the UV Editor offers selection-mode buttons in its header plus a Select menu.

Sync Selection — when on (the default), the UV Editor and 3D Viewport share one synchronized selection: selecting components (vertices, edges, faces) in either editor auto-selects the matching elements in the other. With it on, all faces stay visible in the UV Editor at all times, since UV visibility follows the 3D Viewport's mesh selection; selecting a vertex, edge, or face in the 3D Viewport selects its UV counterparts, but where one 3D vertex or edge maps to several UV vertices or edges (along a UV seam, say) you can't pick them individually — selecting one selects them all. With it off, only the UVs of the faces currently selected in the 3D Viewport appear, UV Editor selections are independent (so individual UV vertices and edges can be selected even when they share a mesh vertex or edge), and selecting in one editor no longer touches the other.
Note: currently only some 3D Viewport selection operations keep per-UV selection data — basic picking, box, circle, and lasso; others, such as Select Random or Select Similar, reset the stored UV selection so all UVs tied to the selected mesh elements get selected. More operators may follow.
Hint: internally, UV selection data is kept per face corner and built on demand to avoid overhead; Python scripts that change mesh selections can call the API functions to sync or clear the UV selection state as needed.

Selection Mode — Vertex (1, select vertices), Edge (2, select edges), Face (3, select faces). With Sync Selection on, hold Shift while clicking a mode to turn several on at once. See also Mesh Selection.

UV Island Selection — Reference: Mode: Edit Mode; Menu: Header ‣ UV Island Selection; Shortcut: 4. Selects contiguous groups of faces connected in the UV map.

Sticky Selection Mode — options for auto-selecting extra UV vertices; available only in Face selection mode, or when Sync Selection is off.
Disabled — each UV vertex selects on its own.
Shared Location — auto-selects UV vertices that map to the same mesh vertex and share its UV coordinates; the default, it gives the illusion that several faces in a UV map share a vertex when really they have separate, overlapping ones.
Shared Vertex — auto-selects UV vertices that map to the same mesh vertex even at different UV coordinates; also how it behaves when Sync Selection is on.

Select Menu:
All (A) — selects every UV element.
None (Alt-A) — deselects every UV element.
Invert (Ctrl-I) — flips the current selection.
Box Select (Alt-B) — see Box Select.
Box Select Pinned (Ctrl-B) — like Box Select but grabs only pinned UV vertices.
Circle Select — see Circle Select.
Lasso Select — see Lasso Select.
More/Less (Ctrl-NumpadPlus, Ctrl-NumpadMinus) — grows/shrinks the selection to/from neighboring elements.

Select Similar — Reference: Mode: Edit Mode; Menu: Select ‣ Select Similar; Shortcut: Shift-G. Selects UV elements similar in some way to the active one; the Adjust Last Operation panel offers several options.
Type — the property to compare, with the choices depending on the Selection Mode:
  Vertex mode: Pinned (vertices with the same pinned state).
  Edge mode: Length (similar UV-map length), Length 3D (similar 3D-mesh length), Pinned (same pinned state).
  Face mode: Area (similar UV-map area), Area 3D (similar 3D-mesh area), Material (the same Material), Object (the same object — handy with several objects in Edit mode at once), Polygon Sides (a similar edge count), Winding (the same orientation, facing up or down in the UV map).
  Island mode: Area (similar UV-map area), Area 3D (similar 3D-mesh area), Amount of Faces in Island (a similar face count).
Compare — the comparison operator: Equal (values that match), Greater (values greater or equal), Less (values less or equal).
Threshold — the tolerance for values that are nearly but not quite the same; a higher threshold selects more elements.

Select Linked — Linked: Reference: Mode: Edit Mode; Menu: Select ‣ Select Linked ‣ Linked; Shortcut: Ctrl-L. Selects every UV element connected to the currently selected ones, expanding the selection across the whole connected UV island; connectivity goes by shared UV edges, not the underlying mesh topology. Handy for grabbing a whole island from a portion of it, as when adjusting layout, packing, or transforming an island. With Sync Selection on, linked selection rides the mesh's connectivity rather than the UV island's.
Shortest Path — Reference: Mode: Edit Mode; Menu: Select ‣ Select Linked ‣ Shortest Path; Shortcut: Ctrl-LMB. Selects every UV element along the shortest path between two elements: the two selected ones when run from the menu, or the active one and the clicked one when run via the shortcut.

Face Stepping — for vertices, lets the path cross faces along their diagonal rather than their edges; for edges, selects disconnected edges perpendicular to the path (an edge ring) rather than connected edges along it (an edge loop); for faces, lets the path pass through faces that share only a vertex rather than an edge.
Topology Distance — measures distance by counting edges rather than gauging their lengths.
Fill Region (Shift-Ctrl-LMB) — selects every shortest path rather than just one.
The settings below select elements at regular intervals, making a "dashed line" instead of a continuous one.
Deselected — how many deselected elements sit in the repeating sequence.
Selected — how many selected elements sit in the repeating sequence.
Offset — how many elements to offset the sequence by.
See also Mesh edit Select Shortest Path.

Select Tile — Reference: Mode: Edit Mode; Menu: Select ‣ Select Tile. Selects the UV faces lying within a specific UV tile, mainly for UDIM workflows. The starting tile comes from the 2D Cursor's position, and every UV face whose coordinates fall inside it is selected. Useful with multi-tile UV layouts for quickly isolating and working on the UVs in one UDIM tile — for packing, transforming, or baking textures. To target a different tile, move the 2D Cursor there and run the operator again.

Select Pinned — Reference: Mode: Edit Mode; Menu: Select ‣ Select Pinned; Shortcut: Shift-P. Selects every pinned UV in the UV Editor. Pinned UVs are held fixed during unwrapping and certain transforms, staying put while other UVs move; this helps you quickly spot or tweak pinned regions, as when refining layouts or steering unwrap behavior.

Select Split — Reference: Mode: Edit Mode; Menu: Select ‣ Select Split; Shortcut: Y. "Detaches" the selected faces so you can move them elsewhere without disturbing their neighbors. Hint: unlike the mesh Split Selection, which truly disconnects faces, this is purely a selection operator — in UV space the faces were never joined to begin with; it only looked that way because Sticky Selection auto-selected neighboring faces' vertices, and Select Split deselects those again. As an alternative, set the Sticky Selection Mode to Disabled.

Select Overlap — Reference: Mode: Edit Mode; Menu: Select ‣ Select Overlap. Selects every UV face that overlaps another in the UV Editor. Overlapping UVs share, wholly or partly, the same texture space, which can cause rendering artifacts, texture bleeding, or wrong bakes, so this flags problem spots in a layout. It's commonly used when prepping UVs for texture baking, lightmaps, or game-engine export, where overlap is usually unwanted; once selected, overlapping faces can be moved, scaled, or repacked to fix it.

Select Edge Loop — Reference: Mode: Edit Mode; Shortcut: Alt-LMB, or Shift-Alt-LMB to extend the existing selection. Holding Alt while clicking an edge selects it and then runs the selection as far as it can in the two directions parallel to it; this works for edge loops that wrap a mesh and for partial loops too. Hold Shift as well to extend the current selection rather than replace it. See also Mesh edit Select Edge Loops.

Select Edge Ring — Reference: Mode: Edit Mode; Shortcut: Ctrl-Alt-LMB, or Shift-Ctrl-Alt-LMB to extend the existing selection. Holding Ctrl-Alt while clicking an edge selects it and then runs the selection as far as it can in the two directions perpendicular to it; this works for edge rings that wrap a mesh and even when no complete ring exists. Hold Shift as well to extend the current selection rather than replace it. See also Mesh edit Select Edge Rings.

## Pivot Point

Reference — Location: Header ‣ Pivot Point. Shortcut: Period.

The Pivot Point is the spot images rotate and scale around, shown by the selected tool's gizmo position. See also the 3D Viewport's Transform Pivot Point.

Bounding Box Center — uses the center of the rectangle drawn as tightly as it can around the selected images' origin points.
Median Point — uses the mean position of the selected images' origin points.
2D Cursor — uses the 2D Cursor's location, for when you want to place the pivot by hand.
Individual Origins — rotates/scales each image around its own origin, rather than turning them all about one shared point as the other options do.

## Preview Snapping

The icon toggles snapping; you can also do it briefly by holding Ctrl once you've started transforming an image. Images carry several snap points — they can snap by their edges, corners, or center.

The drop-down arrow offers:
Snap to:
Borders — snaps images to the render region's edges.
Center — snaps images to the render region's horizontal and vertical center lines.
Other Strips — snaps images to other images' snap points.

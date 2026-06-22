# Preferences Operators (part 2)

> Blender Material Nodes and Images reference. Original prose; identifiers preserved verbatim.

Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1256

bpy.ops.preferences. script_directory_remove ( * , index = 0 )
Undocumented, consider contributing.
Parameters: index ( int ) – Index, Index of the script directory to remove (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1286

bpy.ops.preferences. start_filter ( )
Starts entering filter text.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

bpy.ops.preferences. studiolight_copy_settings ( * , index = 0 )
Copies Studio Light settings to the Studio Light editor.
Parameters: index ( int ) – index, (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1227

bpy.ops.preferences. studiolight_install ( * , files = None , directory = '' , filter_folder = True , filter_glob = '*.png;*.jpg;*.hdr;*.exr' , type = 'MATCAP' )
Installs a user-defined light.
Parameters:
- files ( bpy_prop_collection [ OperatorFileListElement ]) – File Path, (optional)
- directory ( str ) – directory, (optional, never None)
- filter_folder ( bool ) – Filter Folders, (optional)
- filter_glob ( str ) – filter_glob, (optional, never None)
- type ( Literal [ 'MATCAP' , 'WORLD' , 'STUDIO' ] ) – Type, (optional)
- MATCAP — MatCap: install custom MatCaps.
- WORLD — World: install custom HDRIs.
- STUDIO — Studio: install custom Studio Lights.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1110

bpy.ops.preferences. studiolight_new ( * , filename = 'StudioLight' )
Saves a custom studio light from the studio light editor settings.
Parameters: filename ( str ) – Name, (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1157

bpy.ops.preferences. studiolight_uninstall ( * , index = 0 )
Deletes a Studio Light.
Parameters: index ( int ) – index, (in [-inf, inf], optional)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:1208

bpy.ops.preferences. theme_install ( * , overwrite = True , filepath = '' , filter_folder = True , filter_glob = '*.xml' )
Loads and applies a Blender XML theme file.
Parameters:
- overwrite ( bool ) – Overwrite, Remove existing theme file if exists (optional)
- filepath ( str ) – filepath, (optional, never None)
- filter_folder ( bool ) – Filter folders, (optional)
- filter_glob ( str ) – filter_glob, (optional, never None)
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]
File: startup/bl_operators/userpref.py:598

bpy.ops.preferences. unassociate_blend ( )
Removes this installation's associations with .blend files.
Returns: The operator's result.
Return type: set[Literal[Operator Return Items]]

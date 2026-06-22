# Volume Ul Grids Uilist, Workspace Ul Addons Items Uilist, Utilities Bpy Utils, Property Override Flag Collection Items ...

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: `VOLUME_UL`_grids(UIList); `WORKSPACE_UL`_addons_items(UIList); Utilities (bpy.utils); Property Override Flag Collection Items; Property Override Flag Items; Space Graph Mode Items.

## `VOLUME_UL`_grids(UIList)

### `VOLUME_UL`_grids(UIList)

base classes — bpy_struct, UIList

class bpy.types. `VOLUME_UL`_grids ( UIList )

draw_item ( _context , layout , _data , grid , _icon , _active_data , _active_propname , _index )

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## `WORKSPACE_UL`_addons_items(UIList)

### `WORKSPACE_UL`_addons_items(UIList) 

base classes — bpy_struct, UIList

class bpy.types. `WORKSPACE_UL`_addons_items ( UIList ) 

draw_item ( context , layout , _data , addon , _icon , _active_data , _active_propname , _index ) 

filter_items ( _context , data , property ) 

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

| bpy_struct.id_data UIList.bl_idname UIList.list_id UIList.layout_type UIList.use_filter_show UIList.filter_name | UIList.use_filter_invert UIList.use_filter_sort_alpha UIList.use_filter_sort_reverse UIList.use_filter_sort_lock UIList.bitflag_filter_item UIList.bitflag_item_never_show |

### Inherited Functions 

| bpy_struct.as_pointer bpy_struct.driver_add bpy_struct.driver_remove bpy_struct.get bpy_struct.id_properties_clear bpy_struct.id_properties_ensure bpy_struct.id_properties_ui bpy_struct.is_property_hidden bpy_struct.is_property_overridable_library bpy_struct.is_property_readonly bpy_struct.is_property_set bpy_struct.items bpy_struct.keyframe_delete bpy_struct.keyframe_insert bpy_struct.keys bpy_struct.path_from_id bpy_struct.path_from_module | bpy_struct.path_resolve bpy_struct.pop bpy_struct.property_overridable_library_set bpy_struct.property_unset bpy_struct.rna_ancestors bpy_struct.type_recast bpy_struct.values UIList.bl_system_properties_get UIList.draw_item UIList.draw_filter UIList.filter_items UIList.append UIList.is_extended UIList.prepend UIList.remove UIList.bl_rna_get_subclass UIList.bl_rna_get_subclass_py |

## Utilities (bpy.utils)

### Utilities (bpy.utils) 

This module gathers helper functions tied to Blender itself, rather than to
its internal data.

bpy.utils. blend_paths ( * , absolute = False , packed = False , local = False ) 

Gives back the list of external file paths that the open .blend file references.

Parameters :

- absolute ( bool ) – When true the paths returned are made absolute.

- packed ( bool ) – When true include file paths for packed data.

- local ( bool ) – When true skip linked library paths.

Returns :

path list.

Return type :

list[str]

bpy.utils. escape_identifier ( string ) 

A small helper that escapes strings for use in animation paths.

Parameters :

string ( str ) – text

Returns :

The escaped string.

Return type :

str

bpy.utils. flip_name ( name , * , strip_digits = False ) 

Swap a name's left and right sides, handy when
mirroring bone names.

Parameters :

- name ( str ) – Bone name to flip.

- strip_digits ( bool ) – Whether to remove .### suffix.

Returns :

The flipped name.

Return type :

str

bpy.utils. unescape_identifier ( string ) 

A small helper that un-escapes strings used in animation paths.
It undoes what escape_identifier() does.

Parameters :

string ( str ) – text

Returns :

The un-escaped string.

Return type :

str

bpy.utils. register_class ( cls ) 

Make a subclass of one of Blender's type classes known to Blender.

Parameters :

cls (type[bpy.types.Panel | bpy.types.UIList | bpy.types.Menu | bpy.types.Header | bpy.types.Operator | bpy.types.KeyingSetInfo | bpy.types.RenderEngine | bpy.types.AssetShelf | bpy.types.FileHandler | bpy.types.PropertyGroup | bpy.types.AddonPreferences | bpy.types.NodeTree | bpy.types.Node | bpy.types.NodeSocket | bpy.types.Gizmo | bpy.types.GizmoGroup]) – Registerable Blender class type.

Raises :

ValueError – if the class is not a subclass of a registerable blender class.

Note

A register class method on the class, if present, runs ahead of registration.

bpy.utils. register_cli_command ( id , execute ) 

Add a command that can be reached through the ( -c / --command ) command-line argument.

Parameters :

- id ( str ) – The command identifier (must pass an str.isidentifier check).

Should that id already exist, Blender warns and leaves the command unreachable, guarding against firing the wrong one by mistake.

- execute ( Callable [ [ list [ str ] ] , int ] ) – Callback, taking a single list of strings and returns an int.
Its arguments come from every command-line token that trails the command id.
A return of 0 means success and 1 means failure, though the os module's specific error codes are usable too.

Returns :

The command handle which can be passed to unregister_cli_command().

The implementation relies on Python's capsule type, but treat the result purely as an opaque token for later unregistering.

Return type :

Any

Custom Commands

Through registered commands you can readily surface command-line
features as commands invoked via ( -c / --command ).

`	ext
import os

import bpy

def sysinfo_print():
"""
Report basic system information.
"""

import pprint
import platform
import textwrap

width = 80
indent = 2

print("Blender {:s}".format(bpy.app.version_string))
print("Running on: {:s}-{:s}".format(platform.platform(), platform.machine()))
print("Processors: {!r}".format(os.cpu_count()))
print()

### Dump `bpy.app`.
for attr in dir(bpy.app):
if attr.startswith("_"):
continue
### Overly verbose.
if attr in {"handlers", "build_cflags", "build_cxxflags"}:
continue

value = getattr(bpy.app, attr)
if attr.startswith("build_"):
pass
elif isinstance(value, tuple):
pass
else:
### Otherwise ignore.
continue

if isinstance(value, bytes):
value = value.decode("utf-8", errors="ignore")

if isinstance(value, str):
pass
elif isinstance(value, tuple) and hasattr(value, "__dir__"):
value = {
attr_sub: value_sub
for attr_sub in dir(value)
### Exclude built-ins.
if not attr_sub.startswith(("_", "n_"))
### Exclude methods.
if not callable(value_sub := getattr(value, attr_sub))
}
value = pprint.pformat(value, indent=0, width=width)
else:
value = pprint.pformat(value, indent=0, width=width)

print("{:s}:\n{:s}\n".format(attr, textwrap.indent(value, " " * indent)))

def sysinfo_command(argv):
if argv and argv[0] == "--help":
print("Print system information & exit!")
return 0

sysinfo_print()
return 0

cli_commands = []

def register():
cli_commands.append(bpy.utils.register_cli_command("sysinfo", sysinfo_command))

def unregister():
for cmd in cli_commands:
bpy.utils.unregister_cli_command(cmd)
cli_commands.clear()

if __name__ == "__main__":
register()
`

Using Python Argument Parsing

The following example demonstrates pairing Python's argparse module with a custom command.

argparse is usually worth reaching for, since it brings a lot of handy utilities and
produces a --help message for your command automatically.

`	ext
import os
import sys

import bpy

def argparse_create():
import argparse

parser = argparse.ArgumentParser(
prog=os.path.basename(sys.argv[0]) + " --command keyconfig_export",
description="Write key-configuration to a file.",
)

parser.add_argument(
"-o", "--output",
dest="output",
metavar='OUTPUT',
type=str,
help="The path to write the keymap to.",
required=True,
)

parser.add_argument(
"-a", "--all",
dest="all",
action="store_true",
help="Write all key-maps (not only customized key-maps).",
required=False,
)

return parser

def keyconfig_export(argv):
parser = argparse_create()
args = parser.parse_args(argv)

### Ensure the key configuration is loaded in background mode.
bpy.utils.keyconfig_init()

bpy.ops.preferences.keyconfig_export(
filepath=args.output,
all=args.all,
)

return 0

cli_commands = []

def register():
cli_commands.append(bpy.utils.register_cli_command("keyconfig_export", keyconfig_export))

def unregister():
for cmd in cli_commands:
bpy.utils.unregister_cli_command(cmd)
cli_commands.clear()

if __name__ == "__main__":
register()
`

bpy.utils. unregister_cli_command ( handle ) 

Remove a previously registered CLI command.

Parameters :

handle ( Any ) – The return value of register_cli_command().

bpy.utils. resource_path ( type , * , major = bpy.app.version[0] , minor = bpy.app.version[1] ) 

Give back the root path where system files are kept.

Parameters :

- type ( Literal [ 'USER' , 'LOCAL' , 'SYSTEM' ] ) – The resource type.

- major ( int ) – major version, defaults to current.

- minor ( int ) – minor version, defaults to current.

Returns :

the resource path (not necessarily existing).

Return type :

str

bpy.utils. unregister_class ( cls ) 

Remove the Python class from Blender.

Parameters :

cls (type[bpy.types.Panel | bpy.types.UIList | bpy.types.Menu | bpy.types.Header | bpy.types.Operator | bpy.types.KeyingSetInfo | bpy.types.RenderEngine | bpy.types.AssetShelf | bpy.types.FileHandler | bpy.types.PropertyGroup | bpy.types.AddonPreferences | bpy.types.NodeTree | bpy.types.Node | bpy.types.NodeSocket | bpy.types.Gizmo | bpy.types.GizmoGroup]) – Blender type class,
see bpy.utils.register_class() for classes which can
be registered.

Note

An unregister class method on the class, if present, runs ahead of unregistration.

bpy.utils. keyconfig_init ( ) 

Set up and reload key configurations; the Blender window manager calls this at startup and on refresh.

bpy.utils. keyconfig_set ( filepath , * , report = None ) 

Read in a key configuration from a file and make it active.

Parameters :

- filepath ( str ) – Path to the key configuration preset file.

- report ( Callable [ [ set [ str ] , str ] , None ] | None ) – Optional callable used to report errors.

bpy.utils. load_scripts ( * , reload_scripts = False , refresh_scripts = False , extensions = True ) 

Load scripts and call each module's register function.

Parameters :

- reload_scripts ( bool ) – Makes every script run its unregister method
before being loaded again.

- refresh_scripts ( bool ) – Restricts loading to scripts that aren't yet present
as modules.

- extensions ( bool ) – Loads additional scripts (add-ons & app-templates).

bpy.utils. modules_from_path ( path , loaded_modules ) 

Load every module found in a path and hand them back as a list.

Parameters :

- path ( str ) – this path is scanned for scripts and packages.

- loaded_modules ( set [ str ] ) – names of modules already loaded; files whose names
match these are skipped.

Returns :

all loaded modules.

Return type :

list[ModuleType]

bpy.utils. preset_find ( name , preset_path , * , display_name = False , ext = '.py' ) 

Look up a preset by its name.

Parameters :

- name ( str ) – The preset name.

- preset_path ( str ) – The preset subdirectory (e.g. "keyconfig" ).

- display_name ( bool ) – If True, match against the display name rather than the filename.

- ext ( str ) – The file extension for the preset.

Returns :

The file path of the preset or None if not found.

Return type :

str | None

bpy.utils. preset_paths ( subdir ) 

Gives back a list of paths belonging to a particular preset.

Parameters :

subdir ( str ) – preset subdirectory (must not be an absolute path).

Returns :

Script paths.

Return type :

list[str]

bpy.utils. refresh_script_paths ( ) 

Call this once new script paths exist so sys.path picks them up.

bpy.utils. app_template_paths ( * , path = None ) 

Gives back the valid application template paths.

Parameters :

path ( str | None ) – Optional subdir.

Returns :

App template paths.

Return type :

Iterator[str]

bpy.utils. time_from_frame ( frame , * , fps = None , fps_base = None ) 

Gives back the time that corresponds to a frame number.

When fps and fps_base are omitted, the active scene supplies them.

Parameters :

- frame ( int | float ) – number.

- fps ( float | None ) – Frames per second, if not given the current scene is used.

- fps_base ( float | None ) – Frames per second base, if not given the current scene is used.

Returns :

the time in seconds.

Return type :

datetime.timedelta

bpy.utils. register_manual_map ( manual_hook ) 

Register a function that supplies manual URL mappings.

Parameters :

manual_hook ( Callable [ [ ] , tuple [ str , list [ tuple [ str , str ] ] ] ] ) – A callable returning (prefix, mapping),
where mapping lists (pattern, url) pairs.

bpy.utils. unregister_manual_map ( manual_hook ) 

Remove a manual map hook that was registered earlier.

Parameters :

manual_hook ( Callable [ [ ] , tuple [ str , list [ tuple [ str , str ] ] ] ] ) – The hook function to remove.

bpy.utils. register_preset_path ( path ) 

Add a directory to the preset search paths.

Parameters :

path ( str ) – preset directory (must be an absolute path).

Inside this path there must be a "presets" subdirectory, which usually holds presets contributed by add-ons.

From an add-on's __init__.py you can invoke bpy.utils.register_preset_path(os.path.dirname(__file__))
when that __init__.py sits alongside a presets directory.
As an illustration, an operator preset would live under presets/operator/{operator.id}/,
with operator.id being the bl_idname of the operator.

Returns :

success

Return type :

bool

bpy.utils. unregister_preset_path ( path ) 

Remove a directory from the preset search paths.

Parameters :

path ( str ) – preset directory (must be an absolute path).

The value supplied has to be identical to the path that was registered.

Returns :

success

Return type :

bool

bpy.utils. register_classes_factory ( classes ) 

Convenience helper that builds register and unregister functions
which just register and unregister a given sequence of classes.

Parameters :

classes ( Sequence [ type ] ) – Sequence of classes to register and unregister.

Returns :

register and unregister functions.

Return type :

tuple[Callable[[], None], Callable[[], None]]

bpy.utils. register_submodule_factory ( module_name , submodule_names ) 

Convenience helper that builds register and unregister functions
which simply import submodules
and call their register & unregister functions.

Note

Modules register in the order listed
and unregister in the reverse order.

Parameters :

- module_name ( str ) – The module name, typically __name__ .

- submodule_names ( list [ str ] ) – List of submodule names to load and unload.

Returns :

register and unregister functions.

Return type :

tuple[Callable[[], None], Callable[[], None]]

bpy.utils. register_tool ( tool_cls , * , after = None , separator = False , group = False ) 

Add a tool to the toolbar.

Parameters :

- tool_cls (type[bpy.types.WorkSpaceTool]) – A tool subclass.

- after ( Sequence [ str ] | set [ str ] | None ) – Optional identifiers after which this tool is placed.

- separator ( bool ) – If true, insert a separator ahead of this tool.

- group ( bool ) – If true, start a new nested group of tools.

bpy.utils. make_rna_paths ( struct_name , prop_name , enum_name ) 

Build RNA "paths" from the supplied names.

Parameters :

- struct_name ( str ) – Name of a RNA struct (like e.g. "Scene").

- prop_name ( str ) – Name of a RNA struct's property.

- enum_name ( str ) – Name of a RNA enum identifier.

Returns :

A triple of three "RNA paths"
(most_complete_path, "struct.prop", "struct.prop:'enum'").
When enum_name is omitted, the third entry is always empty.

Return type :

tuple[str, str, str]

bpy.utils. manual_map ( ) 

Yield manual URL mappings collected from every registered hook.

Returns :

An iterator of (prefix, mapping) pairs.

Return type :

Iterator[tuple[str, list[tuple[str, str]]]]

bpy.utils. manual_language_code ( default = 'en' ) 

Parameters :

default ( str ) – Language code to fall back to when the current one isn't available.

Returns :

The language code feeding the user-manual URL component, derived from the current language preference and
falling back to the default when that isn't available.

Return type :

str

bpy.utils. script_path_user ( ) 

Give back the user script path, or None.

Returns :

The user script path, or None if not found.

Return type :

str | None

bpy.utils. extension_path_user ( package , * , path = '' , create = False ) 

Give back a user-writable directory tied to an extension.

Note

This gives every extension its own user directory for storing files.

Storing files in the extension's own location is unsuitable, since that location
is wiped on each upgrade and users may lack write access
to the repository (usually a "System" repository).

Parameters :

- package ( str ) – The __package__ of the extension.

- path ( str ) – Optional subdirectory.

- create ( bool ) – Treat the path as a directory and create it if its not existing.

Returns :

a path.

Return type :

str

bpy.utils. script_paths ( * , subdir = None , user_pref = True , check_all = False , use_user = True , use_system_environment = True ) 

Give back a list of valid script paths.

Parameters :

- subdir ( str | None ) – Optional subdir.

- user_pref ( bool ) – Include the user preference script paths.

- check_all ( bool ) – Add local, user and system paths instead of only the ones Blender uses.

- use_user ( bool ) – Include user paths

- use_system_environment ( bool ) – Include `BLENDER_SYSTEM_SCRIPTS` variable path

Returns :

script paths.

Return type :

list[str]

bpy.utils. smpte_from_frame ( frame , * , fps = None , fps_base = None ) 

Give back an SMPTE-formatted string built from the frame :
HH:MM:SS:FF .

When fps and fps_base are omitted, the active scene supplies them.

Parameters :

- frame ( int | float ) – frame number.

- fps ( float | None ) – Frames per second, if not given the current scene is used.

- fps_base ( float | None ) – Frames per second base, if not given the current scene is used.

Returns :

the frame string.

Return type :

str

bpy.utils. smpte_from_seconds ( time , * , fps = None , fps_base = None ) 

Give back an SMPTE-formatted string built from the time :
HH:MM:SS:FF .

When fps and fps_base are omitted, the active scene supplies them.

Parameters :

- time ( int | float | datetime.timedelta ) – time in seconds.

- fps ( float | None ) – Frames per second, if not given the current scene is used.

- fps_base ( float | None ) – Frames per second base, if not given the current scene is used.

Returns :

the frame string.

Return type :

str

bpy.utils. unregister_tool ( tool_cls ) 

Remove a tool that was registered earlier.

Parameters :

tool_cls (type[bpy.types.WorkSpaceTool]) – The tool class to unregister.

bpy.utils. user_resource ( resource_type , * , path = '' , create = False ) 

Give back a user resource path (usually under the user's home directory).

Parameters :

- resource_type ( Literal [ 'DATAFILES' , 'CONFIG' , 'SCRIPTS' , 'EXTENSIONS' ] ) – The resource type.

- path ( str ) – Optional subdirectory.

- create ( bool ) – Treat the path as a directory and create it if its not existing.

Returns :

a path.

Return type :

str

bpy.utils. execfile ( filepath , * , mod = None ) 

Run a file path as a Python script.

Parameters :

- filepath ( str ) – Path of the script to execute.

- mod ( ModuleType | None ) – Optional cached module, the result of a previous execution.

Returns :

The module which can be passed back in as mod .

Return type :

ModuleType

bpy.utils. expose_bundled_modules ( ) 

When Blender runs as a Python module, this adds the bundled VFX library Python
bindings to sys.path . They can stand in for dedicated packages so that
the libraries stay compatible with Blender.

## Property Override Flag Collection Items

### Property Override Flag Collection Items

`LIBRARY_OVERRIDABLE` :

Library Overridable.

Let that property be edited within library overrides of linked data-blocks.
NOTE: A property is overridable only if every parent property up its chain is declared overridable too.

`NO_PROPERTY_NAME` :

No Name.

Skip the item names entirely and rely on their positions in the collection.

`USE_INSERTION` :

Use Insertion.

Permit users to insert fresh items into that collection within library overrides.

## Property Override Flag Items

### Property Override Flag Items

`LIBRARY_OVERRIDABLE` :

Library Overridable.

Let that property be edited within library overrides of linked data-blocks.
NOTE: A property is overridable only if every parent property up its chain is declared overridable too.

## Space Graph Mode Items

### Space Graph Mode Items

FCURVES :

Graph Editor.

Work with animation and keyframes shown as 2D curves.

DRIVERS :

Drivers.

Create and adjust drivers that tie properties to custom functions or to other data.

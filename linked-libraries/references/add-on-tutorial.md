# Add On Tutorial, Bone Collections

> Blender Linked Libraries and Append/Link reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Add-on Tutorial; Bone Collections.

## Add-on Tutorial

Add-on tutorial. Intended audience: technical artists or developers learning to extend Blender, assuming Python basics. Prerequisites: be comfortable in Blender, know how to run a script in the Text editor, understand Python's primitive types (integer, Boolean, string, list, tuple, dictionary, set), be familiar with modules, and have a basic grasp of classes. Suggested reading: parts of "Dive Into Python" (sections 1, 2, 3, 4, 7) and the Blender API Quickstart. To catch Python errors while scripting, run Blender from a terminal (see Use The Terminal), and consider enabling Developer Extras in the preferences. Documentation links worth keeping open: the Blender API Overview (detailed but helpful), the bpy.context reference (the items your script can act on), and bpy.types.Operator (since the tutorial defines operators). What is an add-on? Simply a Python module with a few extra requirements so Blender can list it with useful information. The simplest possible add-on:
```text
bl_info = {
    "name": "My Test Add-on",
    "blender": (2, 80, 0),
    "category": "Object",
}
def register():
    print("Hello World")
def unregister():
    print("Goodbye World")
```
Here bl_info is a dictionary of metadata (title, version, author, and the minimum Blender version — older versions hide the add-on); register runs only when the add-on is enabled, so the module can load without activating; and unregister undoes whatever register set up, running when the add-on is disabled. This example does nothing Blender-specific (it never imports bpy), illustrating that an add-on's base requirements are minimal — an add-on typically registers operators, panels, and menu items, but any script can do that from the Text editor or console, since that capability comes from the bpy module, not from being an add-on; an add-on is just a tidy way to package a module for easy reuse. Running this in the Text editor prints nothing — install it through Preferences to see the messages when enabling and disabling. Your first add-on: the example above is illustrative but does little. The next one integrates a script using an Operator, the usual way to define a tool reached from menus, buttons, and shortcuts; it simply moves every object in the scene. Write the script — add this to the Text editor:
```text
import bpy

scene = bpy.context.scene
for obj in scene.objects:
    obj.location.x += 1.0
```
Click Run Script and every object in the active scene shifts 1.0 unit. Write the add-on (simple) — move that body into an operator's execute() function:
```text
bl_info = {
    "name": "Move X Axis",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy

class ObjectMoveX(bpy.types.Operator):
    """My Object Moving Script"""      # Use this as a tooltip for menu items and buttons.
    bl_idname = "object.move_x"        # Unique identifier for buttons and menu items to reference.
    bl_label = "Move X by One"         # Display name in the interface.
    bl_options = {'REGISTER', 'UNDO'}  # Enable undo for the operator.

    def execute(self, context):        # execute() is called when running the operator.
        scene = context.scene
        for obj in scene.objects:
            obj.location.x += 1.0
        return {'FINISHED'}            # Lets Blender know the operator finished successfully.

def menu_func(self, context):
    self.layout.operator(ObjectMoveX.bl_idname)

def register():
    bpy.utils.register_class(ObjectMoveX)
    bpy.types.VIEW3D_MT_object.append(menu_func)  # Adds the new operator to an existing menu.

def unregister():
    bpy.utils.unregister_class(ObjectMoveX)

if __name__ == "__main__":
    register()
```
bl_info is split across lines purely as a style convention for easy editing. Note that execute() uses the context argument passed to it rather than bpy.context.scene — usually identical, but operators may receive a custom context, so prefer the passed-in one. Paste it into the Text editor and run it, which executes the script and calls register immediately; running won't move anything, though, so trigger the registered operator: open the Operator Search menu, type "Move X by One" (the bl_label), and press Return, and the objects move as before. Keep this open for the install step. Install the add-on: once it's in the Text editor, you'll want to install it so it can be enabled in Preferences and load on startup.

Even though this add-on is a test, the install steps are worth knowing. First save the Text-editor text to disk, obeying Python module naming rules and ending in .py; then install it as you would a downloaded add-on via Preferences ‣ Add-ons ‣ Install…, selecting the file. The add-on then appears in the list; tick its checkbox to enable it (press Save as Default to keep it enabled on restart), and run the operator as before. Enabling runs the add-on's register() function and disabling runs unregister(). The destination depends on your Blender configuration — the source and destination paths print to the console on install — and you can also find add-on locations from the Python Console:
```text
import addon_utils
print(addon_utils.paths())
```
(see Directory Layout for more). Your second add-on focuses on object instancing — making linked copies of an object, similar to the Array modifier. Write the script, starting simple before turning it into an add-on:
```text
import bpy
from bpy import context

# Get the current scene
scene = context.scene
# Get the 3D cursor location
cursor = scene.cursor.location
# Get the active object (assume we have one)
obj = context.active_object
# Now make a copy of the object
obj_new = obj.copy()
# The new object has to be added to a collection in the scene
scene.collection.objects.link(obj_new)
# Now we can place the object
obj_new.location = cursor
```
Run it on the default Cube, clicking first to move the 3D cursor so the duplicate appears there; entering Edit Mode to change the Cube then changes all copies too — these are Linked Duplicates. Next, loop it to build a row of objects spanning from the active object to the cursor:
```text
import bpy
from bpy import context

scene = context.scene
cursor = scene.cursor.location
obj = context.active_object

# Use a fixed value for now, eventually make this user adjustable
total = 10

# Add 'total' objects into the scene
for i in range(total):
    obj_new = obj.copy()
    scene.collection.objects.link(obj_new)

    # Now place the object in between the cursor
    # and the active object based on 'i'
    factor = i / total
    obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))
```
Run this with the active object and cursor spaced apart to see the result. The location math works because both are 3D mathutils.Vector instances — a convenient class from the mathutils module that lets vectors multiply by numbers and matrices; mathutils.Vector also offers handy helpers (angle between vectors, cross and dot products) and mathutils.geometry adds more (Bézier interpolation, ray-triangle intersection), useful for later. Write the add-on — first convert the script as-is:
```text
bl_info = {
    "name": "Cursor Array",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy

class ObjectCursorArray(bpy.types.Operator):
    """Object Cursor Array"""
    bl_idname = "object.cursor_array"
    bl_label = "Cursor Array"
    bl_options = {'REGISTER', 'UNDO'}

    def execute(self, context):
        scene = context.scene
        cursor = scene.cursor.location
        obj = context.active_object

        total = 10

        for i in range(total):
            obj_new = obj.copy()
            scene.collection.objects.link(obj_new)

            factor = i / total
            obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

        return {'FINISHED'}

def register():
    bpy.utils.register_class(ObjectCursorArray)

def unregister():
    bpy.utils.unregister_class(ObjectCursorArray)

if __name__ == "__main__":
    register()
```
Everything here was covered earlier; the two obvious gaps are the hard-coded total of 10 and the inconvenience of reaching the operator only through Operator Search, both fixed next. Operator property: tool settings use property types such as int, float, vector, color, Boolean, and string, handled differently from ordinary Python attributes because Blender displays them in the UI, stores them in keymaps, and keeps them for reuse — so although it feels Pythonic, you're defining tool settings loaded into and accessed by Blender outside Python. To replace the literal 10, use an operator property from the bpy.props module, added to the class body:
```text
# moved assignment from execute() to the body of the class...
total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

# and this is accessed on the class
# instance within the execute() function as...
self.total
```
Blender treats bpy.props specially at registration so they appear as buttons, and many arguments can set limits, change the default, and add a tooltip.

See bpy.props.IntProperty(); this tutorial doesn't detail other property types, but that link has more advanced examples. Menu item: add-ons can extend existing Python-defined panels, headers, and menus — here we add to an existing menu. To find a menu's identifier, enable Python Tooltips in the preferences, then hover over the menu item to see it. The method is to append a draw function into an existing class:
```text
def menu_func(self, context):
    self.layout.operator(ObjectCursorArray.bl_idname)

def register():
    bpy.utils.register_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.append(menu_func)
```
(see bpy.types.Menu for extending menus). Keymap: add-ons get their own keymaps so they don't disturb Blender's built-in ones. Below, a new Object Mode bpy.types.KeyMap is created and a bpy.types.KeyMapItem referencing our operator is added with Shift-Ctrl-T as the shortcut:
```text
# store keymaps here to access after registration
addon_keymaps = []

def register():
    # handle the keymap
    wm = bpy.context.window_manager
    km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
    kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
    kmi.properties.total = 4
    addon_keymaps.append((km, kmi))

def unregister():
    # handle the keymap
    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()
```
Note the keymap item can set total to a value different from the operator's default, letting several keys reach the same operator with different settings. Shift-Ctrl-T isn't a Blender default, but since you can't guarantee add-ons won't overwrite each other's keymaps, take care that your keys don't clash with important Blender functionality (see also the "is key free" add-on). For API docs see bpy.types.KeyMaps.new(), bpy.types.KeyMap, bpy.types.KeyMapItems.new(), and bpy.types.KeyMapItem. Bringing it all together:
```text
bl_info = {
    "name": "Cursor Array",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy

class ObjectCursorArray(bpy.types.Operator):
    """Object Cursor Array"""
    bl_idname = "object.cursor_array"
    bl_label = "Cursor Array"
    bl_options = {'REGISTER', 'UNDO'}

    total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

    def execute(self, context):
        scene = context.scene
        cursor = scene.cursor.location
        obj = context.active_object

        for i in range(self.total):
            obj_new = obj.copy()
            scene.collection.objects.link(obj_new)

            factor = i / self.total
            obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

        return {'FINISHED'}

def menu_func(self, context):
    self.layout.operator(ObjectCursorArray.bl_idname)

# store keymaps here to access after registration
addon_keymaps = []

def register():
    bpy.utils.register_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.append(menu_func)

    # handle the keymap
    wm = bpy.context.window_manager
    # Note that in background mode (no GUI available), keyconfigs are not available either,
    # so we have to check this to avoid nasty errors in background case.
    kc = wm.keyconfigs.addon
    if kc:
        km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
        kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
        kmi.properties.total = 4
        addon_keymaps.append((km, kmi))

def unregister():
    # Note: when unregistering, it's usually good practice to do it in reverse order you registered.
    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()

    bpy.utils.unregister_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.remove(menu_func)

if __name__ == "__main__":
    register()
```
Run it (or save and install it through Preferences) and it appears in the Object menu; after picking it, choose how many cube instances to create. Running the script directly several times re-adds the menu each time — harmless, and add-ons enabled through Preferences won't register twice. Conclusions: add-ons neatly package functionality for improving your own workflow or for sharing utilities, and although Python has limits within Blender, a great deal is achievable without touching its C/C++ code; the tutorial's example is small but shows the API used for common tasks you can build on. Further reading: Blender ships commented templates in the Text editor's header (a good place to find example code), plus the Blender/Python API Overview, "How to Think Like a Computer Scientist," the Blender Development pages, and the Blender Developer Forum.

## Bone Collections

Bone Collections group an armature's bones into named collections owned by the armature, so they're available in every mode; each is identified by a name unique within the armature, and collections can nest inside one another to organize complex rigs (here "collection" means bone collection, not Scene Collections). Manage them through the Armature and Bone property panels. Visibility: collections can be shown or hidden via the lists in the Armature and Bone properties, with a bone's visibility set by its collections plus its own "solo" and "hidden" flags — a bone flagged hidden is always invisible regardless of collections; hiding a parent collection also hides its children (same for soloed ones); a bone is visible if it's in any visible collection; a soloed collection is visible regardless of its hidden flag; and a bone in no collection is visible (otherwise you couldn't select it to assign it). Library overrides: collections can be added through library overrides, which requires overriding both the armature Object and the Armature data. Limitations: only collections local to the current blend-file can be edited; collections that were already present on the linked-in Armature stay read-only, with only their visibility toggleable (and those visibility changes aren't saved); and custom properties of overridden collections can't be edited in the panel (Python access works — it's just a UI limitation). How it works: collections introduced through overrides are "anchored" by name to whichever collection precedes them. For example, with FK Controls and IK Controls defined on the linked Armature (in armature.blend), overrides in armature_shot_47.blend add Left Pinky (anchored to "IK Controls") and Right Pinky (anchored to "Left Pinky"); if the linked Armature later gains Face Controls and Face Detail Controls, reloading armature_shot_47.blend keeps Left Pinky anchored to IK Controls and Right Pinky to Left Pinky, with the new Face collections following. History: Bone Collections arrived in Blender 4.0 to replace armature layers and bone groups; because they're owned by the Armature they work in all modes, whereas the old bone groups lived on the object's pose and so weren't available in armature edit mode.

Bone Collections (Object, Pose, and Edit Modes; Properties ‣ Armature ‣ Bone Collections) — introduced in Blender 4.0 to replace Armature Layers and Bone Groups, with bone colors now managed on the bone. This panel's Tree View manages bone collections: create, delete, rearrange, and more. Rename by double-clicking the name (or right-click ‣ Rename); nest a collection by dragging its name onto another's (or right-click ‣ Add Child Collection); and to the right of each name are Visible (Eye — bones in the collection show in the 3D Viewport) and Solo (Star — show only this and other "solo" collections), with a dot marking collections that have bones assigned. (The Bone Properties panel gives a slightly different view of a bone's collections — see Bone Relations.) Specials: Show All (unhide hidden collections), Un-Solo All (clear "solo" on all), and Remove Unused (recursively remove collections with neither bones nor children). Assign & Select (Pose and Edit Modes; Properties ‣ Armature ‣ Bone Collections; Pose ‣ Bone Collections ‣ …): Assign (put selected bones in the active collection), Remove (take them out), Select (select the collection's bones), and Deselect; individual bones can also be unassigned via the Bone Relations panel, and for custom selection sets see the bundled Selection Sets add-on. Moving bones between collections (Edit or Pose Mode; bones can belong to several collections at once): Move to Bone Collection lists the armature's editable collections, and picking one unassigns the selected bones from all others before assigning them to it (Pose ‣ Move to Collection in Pose Mode, Armature ‣ Move to Collection in Edit Mode, or M in either); Bone Collections lists the editable collections with the active bone's collections prefixed "-" (choosing one unassigns all selected bones from it) and others prefixed "+" (choosing one assigns them), available as Pose ‣ Bone Collections / Armature ‣ Bone Collections, or Shift-M. These operators show only editable collections — a linked Armature's collections are read-only, and new collections added via library overrides are the only editable ones (see Library Overrides of Bone Collections). Custom Properties: create and manage your own properties on the Bone Collection's data-block (see the Custom Properties page).

## See also

- [Quickstart](quickstart.md)

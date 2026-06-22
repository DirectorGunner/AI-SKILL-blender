# Blender Cameras, Lights, and Rendering — Gotchas

Recurring failure modes when relying on the Blender Cameras, Lights, and Rendering reference, and what to do instead. Read alongside `SKILL.md`.

- Blender's API and UI change across versions; verify version-sensitive operators, enum values, and defaults against the actual Blender build in use.
- `bpy` runs single-threaded against a live `bpy.context` / `bpy.data`; operator behavior depends on mode (Object/Edit/Pose), the active object, and selection — confirm context before relying on an operator.
- Treat every operator name, `bpy` path, enum value, keyboard shortcut, and number as an exact reference fact; verify project-specific behavior against actual `.blend` files, add-ons, and generated artifacts.
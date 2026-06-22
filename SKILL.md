---
name: blender
description: >-
  Use when work depends on Blender Manual or Blender Python API facts: bpy scripting, operators, add-ons and extensions; actions, F-curves, keyframes and animation; materials, shader nodes, textures and images; cameras, lights and rendering; linked libraries and append/link; and panels, properties and operators. Routes to six area sub-skills. Not for other DCC tools or non-Blender Python.
covers:
  - actions-fcurves
  - addons-panels
  - cameras-lights
  - linked-libraries
  - material-nodes
  - python-api
---

# Blender Documentation Reference

Faithful, task-routed reference for the Blender Manual and the Blender Python API, rendered from the
full documentation corpus into one focused file per subject. Original prose; identifiers are
preserved verbatim. This package routes to six area sub-skills — open the one that matches and use
its `references/INDEX.md`.

## When to use this

Use this skill whenever a task depends on how Blender behaves — UI/workflow or the `bpy` Python API —
and involves bpy scripting, operators, add-ons/extensions, animation, materials/nodes/images,
cameras/lights/rendering, linked libraries/append-link, or panels/properties. It applies even when
"Blender" is not named but a `.blend` file, `bpy`, or a Blender operator/shortcut is in play.

**Do not use** for other DCC tools (Maya, 3ds Max, Houdini, Cinema 4D), game-engine specifics, or
Python unrelated to `bpy`.

## Routes

| Area | Use for | Open |
| --- | --- | --- |
| Blender Linked Libraries and Append/Link | linking and appending data, library overrides, and reusing assets across .blend files. | `linked-libraries/SKILL.md` |
| Blender Material Nodes and Images | materials, shader and geometry nodes, textures, images, and UV data. | `material-nodes/SKILL.md` |
| Blender Cameras, Lights, and Rendering | cameras, lights, the render engines, and rendering behavior. | `cameras-lights/SKILL.md` |
| Blender Actions, F-Curves, and Animation | actions, F-curves, keyframes, drivers, the NLA, and animation behavior. | `actions-fcurves/SKILL.md` |
| Blender Add-ons, Panels, and Properties | add-ons, UI panels, properties, and operator-driven UI integration. | `addons-panels/SKILL.md` |
| Blender Python API Essentials | bpy scripting, operators, add-on and extension authoring, the command line, and application templates. | `python-api/SKILL.md` |

## Workflow

1. Identify the area above and open that sub-skill's `SKILL.md` (or its `references/INDEX.md`).
2. Pick the one reference file that matches; read only what you need.
3. Treat every operator name, `bpy` path, enum value, shortcut, and number as an exact reference fact.

## Gotchas

Recurring failure modes and what to do instead live in the sibling [GOTCHA.md](GOTCHA.md).

## References

Each sub-skill carries its own `references/INDEX.md`, `references/topics.json`, and per-subject
`references/*.md`. Start from the area's `INDEX.md`.

## Official documentation

Includes original content written for this skill. The official documentation is at https://docs.blender.org/manual/en/latest/ — consult it to verify anything uncertain, conflicting, or version-specific.

## Verification

```powershell
python "$env:DEVROOT\SKILLS\skills\skill-drafting\scripts\validate_skill_package.py" --package "$env:DEVROOT\SKILLS\skills\blender"
```

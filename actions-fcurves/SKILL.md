---
name: actions-fcurves
description: Use when a Blender task involves actions, F-curves, keyframes, drivers, NLA, animation. Part of the Blender reference router; covers actions, F-curves, keyframes, drivers, the NLA, and animation behavior.
---

# Blender Actions, F-Curves, and Animation Reference

Faithful, original-prose reference for actions, F-curves, keyframes, drivers, the NLA, and animation behavior. Identifiers (operator names, `bpy` paths, enum
values, shortcuts, numbers) are preserved verbatim. One subject per file across 97 reference files.

## When to use this

Use this sub-skill when the task involves actions, F-curves, keyframes, drivers, NLA, animation. It applies even when "Blender" is not named but
a `.blend` file, `bpy`, or a relevant operator/shortcut is in play.

## Workflow

1. Open `references/INDEX.md` (or `references/topics.json`) and pick the one file that matches — the INDEX "Covers" column lists the subjects in each file.
2. Read only that file; open another only if the task spans subjects. Grep across files when a subject may be split: `rg -n "PATTERN" references/*.md`.
3. Treat every operator name, `bpy` path, enum value, shortcut, and number as an exact reference fact — never invent or paraphrase identifiers.

## Gotchas

Recurring failure modes and what to do instead live in the sibling [GOTCHA.md](GOTCHA.md).

## References

All depth lives in `references/` — start at `references/INDEX.md`, with metadata in
`references/topics.json`. One subject per file.

## Verification

```powershell
python "$env:DEVROOT\SKILLS\skills\skill-drafting\scripts\validate_skill_package.py" "$env:DEVROOT\SKILLS\skills\blender\actions-fcurves"
```

# Blender Documentation Reference

> _Faithful, task-routed reference for the Blender Manual and the Blender Python API — bpy scripting, animation, materials/nodes, rendering, linked libraries, and add-ons._

Part of **[Agent Kaizen](https://github.com/DirectorGunner/agent-kaizen)** — Agent Kaizen is designed to support reliable AI agent workflows, context engineering, and AI systems engineering in VS Code, Codex, and Claude Code. Build reusable agent skills, reduce unnecessary context loading, add validation loops, and apply Spec → Verifier → Environment scaffolding to new and existing projects.

This repository is the `blender` skill: a reusable, trigger-rich task handbook that an AI coding agent (OpenAI Codex, Claude Code) loads on demand when a task matches its triggers.

## What this skill covers

This skill spans the Blender Manual and the Blender Python API (`bpy`): bpy scripting, operators, and add-ons/extensions; actions, F-curves, keyframes, and animation; materials, shader nodes, textures, and images; cameras, lights, and rendering; linked libraries and append/link; and panels, properties, and operators. It routes to **six area sub-skills** — `actions-fcurves`, `addons-panels`, `cameras-lights`, `linked-libraries`, `material-nodes`, and `python-api` — so the agent opens only the area that matches. It fires even when "Blender" isn't named but a `.blend` file, `bpy`, or a Blender operator/shortcut is in play. It is not for other DCC tools (Maya, 3ds Max, Houdini, Cinema 4D) or non-`bpy` Python.

## What's inside

- `SKILL.md` — the router frontmatter (`name` + trigger-rich `description`) that routes to sub-skills.
- sub-skill folders — each a focused area with its own `SKILL.md`, `references/`, and `GOTCHA.md`.
- `GOTCHA.md` — known pitfalls and edge cases.

## Use it

This skill is one git repo inside the Agent Kaizen **skills store**. The store nests two folders on purpose: the outer **`SKILLS\`** is a VS Code project for building and maintaining skills (its own workspace + tooling), and the inner lowercase **`skills\`** holds every skill as its own repo. That split lets a project pull skills two ways — the **whole `skills\` folder at once** (loads everything — **not recommended**) or **one skill at a time** (recommended: load only what a task needs and stay under Claude Code's skill-listing budget).

Paths below use **`%DEVROOT%`** — the `DEVROOT` environment variable pointing at the folder that contains `SKILLS\`. Set it once by running **`SetDevRoot.cmd`** in the SKILLS repo root (no admin); a new shell then resolves `%DEVROOT%` automatically.

Link **just this skill** (recommended) — a Windows directory junction, no admin:

```cmd
mklink /J .agents\skills\blender  "%DEVROOT%\SKILLS\skills\blender"
mklink /J .claude\skills\blender  "%DEVROOT%\SKILLS\skills\blender"
```

Or link the **whole store** at once (loads every skill — not recommended outside a skills-dev project):

```cmd
mklink /J .agents\skills  "%DEVROOT%\SKILLS\skills"
mklink /J .claude\skills  "%DEVROOT%\SKILLS\skills"
```

Remove a link (the store copy is untouched):

```cmd
rmdir .agents\skills\blender
rmdir .claude\skills\blender
```

The agent (OpenAI Codex, Claude Code) then auto-loads this skill whenever a task matches its triggers. Built and validated with **[skill-drafting](https://github.com/DirectorGunner/AI-skill-drafting)** to the Agent Kaizen gold standard.

## License

Licensed under **AGPL-3.0**, matching the [Agent Kaizen](https://github.com/DirectorGunner/agent-kaizen) project.

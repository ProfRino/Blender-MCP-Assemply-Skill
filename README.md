# Blender-MCP-Assemply-Skill
Blender Assembly is a geometry-building skill for creating reliable 3D models in Blender via MCP. It helps prevent common modelling errors by planning object connections, using correct primitive scaling, avoiding faulty cylinder rotations, verifying overlaps, and auditing final transforms.

## Before vs After

The image below shows how the Blender MCP Assembly Skill helps an AI agent move from a disconnected chair assembly to a cleaner, connected Blender model.

![Before vs After](Before%20vs%20After.png)

## What is included in the skill?

The Blender MCP Assembly Skill provides a practical workflow for any AI agent creating geometry in Blender through MCP tools. It guides the agent before, during, and after model creation, starting with connection planning. Before writing Blender Python code, the agent maps how each part of the model should physically connect, including joints, contact faces, and minimum overlaps. This helps reduce disconnected or “exploded” models by making the assembly logic explicit from the beginning.

The skill then defines geometry creation rules for building cleaner and more reliable models. It instructs agents to use `size=2` for cube primitives so scale values match real half-extents, avoid Euler rotations for cylinders or directional parts, and use bmesh-based geometry for beams, supports, rails, pipes, legs, or any element that must span between two points. It also requires transforms to be applied immediately after scaling, especially inside loops, to reduce the risk of Blender applying changes to the wrong object.

A key part of the skill is verification. It includes helper functions such as `verify_bounds()` and `verify_overlap()` so the agent can check the real world-space size and position of each part. Instead of guessing dimensions, the agent is encouraged to measure existing geometry and derive new dimensions from verified bounds. This makes the modelling process more reliable and helps reduce hidden gaps, alignment issues, and scaling errors.

Finally, the skill includes a finalisation and audit stage. Functions such as `finalize()` and `audit_all()` help apply transforms, set origins, smooth geometry, and confirm that mesh objects have clean rotation and scale values. The result is a more predictable Blender MCP workflow for AI agents, producing models that are better connected, correctly scaled, and easier to inspect or modify later.

## How to Use

The skill is defined in `SKILL.md`. To use it, add `SKILL.md` to your AI agent's skill or prompt library so it is automatically applied whenever Blender MCP geometry code is being written.

### GitHub Copilot

Copy `SKILL.md` into your repository and reference it from `.github/copilot-instructions.md`:

```
When creating geometry in Blender via MCP, follow the workflow in SKILL.md.
```

GitHub Copilot will read `.github/copilot-instructions.md` automatically for any repository that contains it.

### Other AI Agents

Place `SKILL.md` in the same directory as your agent's skill files. The `description` field in the YAML front matter is used by agents that support skill routing — it tells the agent when to invoke the skill automatically.

### Manual Use

Copy the relevant sections of `SKILL.md` into your system prompt or paste them directly into your Blender MCP session before asking an AI agent to generate geometry.

## Tutorial

Watch the full tutorial on YouTube to see how the **Blender MCP Assembly Skill** can be used in practice with Blender and AI agents.

In this video, I explain the purpose of the skill, how it helps prevent common Blender geometry problems, and how it can support more reliable AI-generated 3D modelling workflows through MCP.

[Watch the tutorial on YouTube](https://youtu.be/fsLkJNEtsTw?si=Yn5LQF2USk_PpWG1)

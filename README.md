# Blender-MCP-Assemply-Skill
Blender Assembly is a geometry-building skill for creating reliable 3D models in Blender via MCP. It helps prevent common modelling errors by planning object connections, using correct primitive scaling, avoiding faulty cylinder rotations, verifying overlaps, and auditing final transforms.

## What is included in the skill?

The Blender MCP Assembly Skill contains a practical workflow that guides an AI agent before, during, and after creating geometry in Blender. It starts with connection planning, where the agent maps how each part of the model should physically connect before writing any Blender Python code. This helps avoid disconnected or “exploded” models by making the agent think about joints, contact faces, and minimum overlaps from the beginning.

The skill then provides geometry creation rules for building cleaner models. It instructs agents to use `size=2` for cube primitives so scale values match real half-extents, to avoid rotating cylinders with Euler angles for directional parts, and to use bmesh-based geometry when creating beams, supports, rails, pipes, legs, or other elements that must span between two points. It also requires transforms to be applied immediately after scaling, especially inside loops, to prevent Blender from applying changes to the wrong object.

A key part of the skill is verification. It includes helper functions such as `verify_bounds()` and `verify_overlap()` so the agent can check the real world-space size and position of every part. Instead of guessing dimensions, the agent is encouraged to measure existing geometry and derive new dimensions from verified bounds. This makes the modelling process more reliable and reduces hidden gaps, alignment issues, and scaling errors.

Finally, the skill includes a finalisation and audit stage. Functions such as `finalize()` and `audit_all()` help apply transforms, set origins, smooth geometry, and confirm that all mesh objects have clean rotation and scale values. The result is a more predictable Blender workflow for AI agents, producing models that are better connected, correctly scaled, and easier to inspect or modify later.

## Tutorial

Watch the full tutorial on YouTube to see how the **Blender MCP Assembly Skill** can be used in practice with Blender and AI agents.

In this video, I explain the purpose of the skill, how it helps prevent common Blender geometry problems, and how it can support more reliable AI-generated 3D modelling workflows through MCP.

[Watch the tutorial on YouTube](https://youtu.be/fsLkJNEtsTw?si=Yn5LQF2USk_PpWG1)

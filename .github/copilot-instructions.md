# GitHub Copilot Instructions

When writing Blender Python code that creates geometry via MCP tools (`mcp__blender__execute_blender_code`), always follow the workflow defined in `SKILL.md`.

This applies to all object types: furniture, vehicles, architecture, characters, props, mechanical parts, and scenes.

The skill prevents the three most common geometry bugs in AI-generated Blender models:

1. Cube size math errors (`size=1` silently halves every dimension)
2. Euler rotation failures on cylinders and directional parts
3. Invisible gaps that cause exploded-looking renders

Key rules:
- Use `size=2` for all cube primitives
- Use `make_beam()` (bmesh) for any geometry spanning from point A to point B
- Call `transform_apply(scale=True)` immediately after every `obj.scale = (...)`, inside loops
- Call `verify_bounds()` after every part, `verify_overlap()` at every joint
- Call `finalize()` on every mesh object, then `audit_all()` before finishing

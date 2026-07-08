---
name: ue-blueprint
description: Use when creating, editing, compiling, wiring, inspecting, or debugging Unreal Blueprint assets, Blueprint graphs, variables, events, components, UMG-backed Blueprint assets, or Blueprint defaults through UE MCP.
---

# UE Blueprint

Use UE MCP AgentSkills as the authoritative workflow source for Blueprint asset work. Prefer C++ for core gameplay logic in this project, but use Blueprint tools for asset wiring, component setup, defaults, presentation, and existing Blueprint assets.

Before Blueprint work:

- Query live MCP toolsets with `ue5_list_toolsets` and `ue5_describe_toolset`.
- Call `ToolsetRegistry.AgentSkillToolset.ListSkills` through `ue5_call_tool`.
- Load `/EditorToolset/Python/editor_toolset/skills/blueprint_basics_PY.BlueprintBasicsSkill` with `ToolsetRegistry.AgentSkillToolset.GetSkills`.
- Call UE MCP tools sequentially because they run on the Unreal editor game thread.

Typical toolsets:

- `editor_toolset.toolsets.blueprint.BlueprintTools`
- `editor_toolset.toolsets.actor.ActorTools`
- `editor_toolset.toolsets.object.ObjectTools`
- `editor_toolset.toolsets.asset.AssetTools`
- `editor_toolset.toolsets.scene.SceneTools`
- `EditorToolset.EditorAppToolset`

Important workflow:

- Use `ObjectTools.list_properties` before `ObjectTools.get_properties` or `ObjectTools.set_properties`.
- Compile changed Blueprints with `BlueprintTools.compile_blueprint` when appropriate.
- Save changed binary assets with `AssetTools.save_assets`.
- Ask for explicit permission before deleting, renaming, or replacing assets or reflected Blueprint-visible members.

---
name: ue-lighting
description: Use when setting up, modifying, inspecting, or debugging Unreal outdoor lighting, sun, sky, skylight, clouds, fog, exposure, atmosphere, post-process, scene lighting, or lighting-related level actors through UE MCP.
---

# UE Lighting

Use UE MCP AgentSkills as the authoritative workflow source for outdoor lighting and atmosphere work.

Before lighting work:

- Query live MCP toolsets with `ue5_list_toolsets` and `ue5_describe_toolset`.
- Call `ToolsetRegistry.AgentSkillToolset.ListSkills` through `ue5_call_tool`.
- Load `/EditorToolset/Python/editor_toolset/skills/default_outdoor_lighting_PY.DefaultOutdoorLightingSkill` with `ToolsetRegistry.AgentSkillToolset.GetSkills`.
- Call UE MCP tools sequentially because they run on the Unreal editor game thread.

Typical toolsets:

- `EditorToolset.EditorAppToolset`
- `editor_toolset.toolsets.scene.SceneTools`
- `editor_toolset.toolsets.actor.ActorTools`
- `editor_toolset.toolsets.object.ObjectTools`
- `editor_toolset.toolsets.asset.AssetTools`

Important workflow:

- Inspect current level actors and properties before changing lighting.
- Use `ObjectTools.list_properties` before `ObjectTools.get_properties` or `ObjectTools.set_properties`.
- Capture the viewport when visual verification is useful.
- Save changed level/assets with `AssetTools.save_assets`.

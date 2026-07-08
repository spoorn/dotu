---
name: ue-material
description: Use when creating, editing, inspecting, wiring, recompiling, or instancing Unreal Materials, Material Functions, Material Instances, material parameters, textures, or mesh material assignments through UE MCP.
---

# UE Material

Use UE MCP AgentSkills as the authoritative workflow source for Material and MaterialInstance work. Prefer MaterialInstances over new Materials when an existing parent can support the requested look.

Before material work:

- Query live MCP toolsets with `ue5_list_toolsets` and `ue5_describe_toolset`.
- Call `ToolsetRegistry.AgentSkillToolset.ListSkills` through `ue5_call_tool`.
- Load `/EditorToolset/Python/editor_toolset/skills/material_basics_PY.MaterialBasicsSkill` with `ToolsetRegistry.AgentSkillToolset.GetSkills`.
- Call UE MCP tools sequentially because they run on the Unreal editor game thread.

Typical toolsets:

- `editor_toolset.toolsets.material.MaterialTools`
- `editor_toolset.toolsets.material_instance.MaterialInstanceTools`
- `editor_toolset.toolsets.texture.TextureTools`
- `editor_toolset.toolsets.static_mesh.StaticMeshTools`
- `editor_toolset.toolsets.skeletal_mesh.SkeletalMeshTools`
- `editor_toolset.toolsets.object.ObjectTools`
- `editor_toolset.toolsets.asset.AssetTools`

Important workflow:

- Query valid expression classes, pins, material slots, and parameters before editing.
- Recompile Materials or MaterialFunctions after graph edits.
- Save changed binary assets with `AssetTools.save_assets`.

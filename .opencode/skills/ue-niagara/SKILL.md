---
name: ue-niagara
description: Use when creating, placing, editing, optimizing, debugging, or Blueprint-wrapping Niagara VFX, particle systems, emitters, modules, renderers, user parameters, smoke, fire, explosions, trails, beams, or gameplay effects in Unreal Engine through UE MCP.
---

# UE Niagara

Use UE MCP AgentSkills as the authoritative workflow source. Do not guess Niagara stack schemas or parameter names.

Before Niagara work:

- Query live MCP toolsets with `ue5_list_toolsets` and `ue5_describe_toolset`.
- Call `ToolsetRegistry.AgentSkillToolset.ListSkills` through `ue5_call_tool`.
- Load relevant live Unreal skills with `ToolsetRegistry.AgentSkillToolset.GetSkills`.
- Call UE MCP tools sequentially because they run on the Unreal editor game thread.

Relevant Unreal AgentSkills:

- `/NiagaraToolsets/Python/skills/fundamentals_PY.NiagaraFundamentalsSkill`
- `/NiagaraToolsets/Python/skills/level_placement_PY.NiagaraLevelPlacementSkill`
- `/NiagaraToolsets/Python/skills/renderers_PY.NiagaraRenderersSkill`
- `/NiagaraToolsets/Python/skills/optimization_PY.NiagaraOptimizationSkill`
- `/NiagaraToolsets/Python/skills/blueprint_interop_PY.NiagaraBlueprintInteropSkill`
- `/NiagaraToolsets/Python/skills/cleanup_PY.NiagaraCleanupSkill`
- `/NiagaraToolsets/Python/skills/custom_hlsl_PY.NiagaraCustomHLSLSkill`

Typical toolsets:

- `NiagaraToolsets.NiagaraToolset_System`
- `NiagaraToolsets.NiagaraToolset_Assets`
- `NiagaraToolsets.NiagaraToolset_Component`
- `NiagaraToolsets.NiagaraToolset_Blueprint`
- `NiagaraToolsets.NiagaraToolset_Info`
- `editor_toolset.toolsets.scene.SceneTools`
- `editor_toolset.toolsets.asset.AssetTools`
- `editor_toolset.toolsets.object.ObjectTools`

For level placement, search and present existing Niagara assets before placing or creating new effects unless the user explicitly asks for a new effect. After modifying binary assets, save with `editor_toolset.toolsets.asset.AssetTools.save_assets`.

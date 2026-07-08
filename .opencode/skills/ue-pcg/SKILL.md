---
name: ue-pcg
description: Use when creating, editing, debugging, or placing Procedural Content Generation PCG graphs, PCG volumes, spatial rules, asset scattering, biomes, shape grammar, or instant level operations in Unreal Engine through UE MCP.
---

# UE PCG

Use UE MCP AgentSkills as the authoritative workflow source. Do not copy or rely on stale PCG instructions from memory.

Before PCG work:

- Query live MCP toolsets with `ue5_list_toolsets` and `ue5_describe_toolset`.
- Call `ToolsetRegistry.AgentSkillToolset.ListSkills` through `ue5_call_tool`.
- Load relevant live Unreal skills with `ToolsetRegistry.AgentSkillToolset.GetSkills`.
- Call UE MCP tools sequentially because they run on the Unreal editor game thread.

Relevant Unreal AgentSkills:

- `/PCGToolset/Skills/Skill_PCGGraphGeneration.Skill_PCGGraphGeneration_C`
- `/PCGToolset/Skills/Skill_InstantLevelOperations.Skill_InstantLevelOperations_C`
- `/PCGToolset/Skills/Skill_PCGAssetZoo.Skill_PCGAssetZoo_C`
- `/PCGToolset/Skills/Skill_PCGBiomeCore.Skill_PCGBiomeCore_C`
- `/PCGToolset/Skills/Skill_PCGBiomeCoreRefinement.Skill_PCGBiomeCoreRefinement_C`
- `/PCGToolset/Skills/Skill_PCGInstancingOnMeshActor.Skill_PCGInstancingOnMeshActor_C`
- `/PCGToolset/Skills/Skill_PCGMeshPartition.Skill_PCGMeshPartition_C`
- `/PCGToolset/Skills/Skill_PCGShapeGrammarDefinition.Skill_PCGShapeGrammarDefinition_C`

Typical toolsets:

- `PCGToolset.PCGToolset`
- `PCGToolset.PCGSpatialToolset`
- `editor_toolset.toolsets.scene.SceneTools`
- `editor_toolset.toolsets.asset.AssetTools`
- `editor_toolset.toolsets.object.ObjectTools`

After modifying binary assets, save with `editor_toolset.toolsets.asset.AssetTools.save_assets`.

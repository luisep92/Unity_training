# Unity_training

Unity 2022.3 LTS / URP. Was meant to be a small explorable diorama in a stylized, Keeper-leaning look — water, vegetation, a few reactive creatures, post-processing doing most of the work.

## Status: archived

The 2-day sprint that built it ran in early November 2025. Not under active development since, and not coming back.

## What actually shipped

Two pieces:

- **Stylized water shader (Phase 1)** — `Assets/GameAssets/Environment/Water/StylizedWater_Shader.shadergraph`. Animated gradient noise, configurable flow speed and tint, transparent surface. Pipeline: `Time → Multiply → Add ← UV → Gradient Noise → Remap → Color`. Has a small test scene next to it (`TestWater.unity`).
- **URP stylized configuration** — `Assets/GameAssets/_Core/Rendering/`. Custom Render Pipeline Asset, Renderer, Volume Profile (bloom + color grading + tonemapping), scene-based linear fog. Before/after captured in `docs/images/URP_default_vs_stylized.png`.

No character controller, no terrain, no vegetation, no creatures. The other module folders (`Character/`, `VFX/`, `Environment/_Shared/`, `Scenes/`) contain only intent READMEs describing what was supposed to go in them.

## Where the value actually is

If you came here for Unity content, the section above is what's here. The substance is in the docs:

- **[`docs/Learnings.md`](docs/Learnings.md)** — eight dated entries from the sprint. Each one has a "Core Concept" block with the universal principle behind the Unity-specific lesson. Examples: GPU shaders as parallel/stateless data flow (transferable to any visual shader editor — Unreal, Godot, Blender), post-processing as image-space ops after the 3D pass, why LTS releases trade features for stability, modular-by-feature vs by-file-type architecture. Worth reading independently of Unity.
- **`.claude/`** — three files (`context.md`, `instructions.md`, `development-log.md`) that documented the AI-assisted workflow used here. The patterns ended up worth reusing: a Teaching Mode that tells the assistant when to explain vs. guide, a Core Concept template that separates tool-specific knowledge from universal principles, and a dev-log structure (Built / Decisions / Problems / Next) that makes sessions resumable across days.
- **`.claudeignore`** — small but useful: keeps binaries (textures, audio, scenes) out of the assistant's context window so it doesn't get blown up by a single image.

## Why it stopped

Hit Claude Code context limits. As the project grew — more files, more decision history, more sub-system cross-references — each session got harder to manage. The project didn't survive it.

## Stack

Unity 2022.3.62f3 LTS, URP, Shader Graph, Git LFS for binary assets. Targets GTX 1080Ti at 60fps.

## License

Public for demonstration purposes only. No part of this code or its contents may be copied, used, or modified without explicit permission.

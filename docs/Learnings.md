# Learning Journey

High-level overview of what I built, learned, and overcame during this project.

---

## Project Initialization
**Date:** November 1, 2025
**Commit:** [`6921f64`](https://github.com/luisep92/Unity_training/commit/6921f64)

### What I Did
- Set up Unity 6 LTS (6000.2.10f1) project
- Configured Git with .gitignore for Unity
- Created project documentation (.claude/context.md)

### What I Learned
- Unity 6 LTS is recent and has stability issues (crashed ~6 times)
- Proper .gitignore is essential to avoid committing Library/ and Temp/

---

## Project Structure & Git LFS
**Date:** November 1, 2025
**Commits:** [`bc682dc`](https://github.com/luisep92/Unity_training/commit/bc682dc), [`4dc3745`](https://github.com/luisep92/Unity_training/commit/4dc3745)

### What I Did
- Created modular folder structure (GameAssets/ organized by feature)
- Configured Git LFS for binary assets (.fbx, .png, textures)
- Removed example code and cleaned up unused files

### What I Learned
- **Git LFS:** Essential for Unity - binary .meta files for every asset
- **Modular structure:** Organize by feature (Character/, Environment/), not file type
- Only create folders when needed (no empty placeholders)

---

## URP Configuration & Post-Processing
**Date:** November 1, 2025
**Commit:** [`0e84af3`](https://github.com/luisep92/Unity_training/commit/0e84af3)

### What I Did
- Created custom URP Render Pipeline Asset: `CustomURP_StylizedSettings`
- Configured HDR, MSAA 4x, shadow resolution 2048
- Created Volume Profile with bloom, color grading, fog
- Set up stylized look: +15 contrast, +20 saturation, bloom 0.3

### What I Learned
- **URP vs Built-in:** Materials show magenta without correct pipeline - incompatible shaders
- **Volume System:** Post-processing uses Volumes in URP (different from Built-in)
- **Fog in URP:** Not a volume override - configured in Lighting window
- **Per-camera setting:** Must enable "Render Post Processing" on each camera

### Challenges
- Post-processing not showing in Game view → forgot to enable on camera
- Searched for Fog in Volume overrides → it's in Lighting settings instead
- Unity 6 crashed multiple times (AssetImportWorker bug)

### Visual Results

![URP Default vs Stylized](images/URP_default_vs_stylized.png)

*Top: Unity default renderer (flat, unsaturated). Bottom: Custom URP with post-processing (vibrant colors, bloom, contrast, atmospheric fog).*

---

## Priority Shift: Visual-First Approach
**Date:** November 1, 2025
**Commit:** [`22fa41d`](https://github.com/luisep92/Unity_training/commit/22fa41d)

### What I Did
- Reprioritized development: shaders before character controller
- Updated project roadmap to focus on visual elements first

### Reasoning
- Full character (model + animations + controller) is heavy work
- Visual elements (shaders, environment) are primary interest
- Can test shaders in Scene view without player movement
- ShaderGraph knowledge needed for all custom shaders

### New Priority Order
1. Water shader (learning foundation)
2. Basic terrain
3. Vegetation/wind shader
4. Minimal controller (capsule only, no animations)
5. Character model/animations (deferred)

---

*Updated after each development session.*

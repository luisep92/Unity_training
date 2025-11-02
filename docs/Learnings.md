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

### Core Concept
*Game engines use cached/compiled data (Library/, Temp/) to speed up iteration. These folders are regenerated from source assets, so version control should only track source data.*

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

### Core Concept
*Organizing by feature/system rather than file type makes code more modular and reusable. This pattern appears in all large-scale software: UI components, game systems, microservices - coupling related code together reduces dependencies and improves maintainability.*

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

### Core Concept
*Post-processing is applied after the scene renders but before displaying to screen. Effects like bloom, color grading, and fog are image-space operations - they manipulate the final 2D image, not 3D geometry. This separation allows visual polish without impacting scene complexity. HDR (High Dynamic Range) preserves brightness data beyond 0-1, allowing bloom to work correctly on bright areas.*

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

### Core Concept
*In tech demos and portfolio projects, visual impact > gameplay complexity. Prioritize systems that demonstrate technical skill and are immediately impressive. Interactive gameplay requires player input, but rendering effects can be showcased through camera movement alone.*

---

## Documentation Enhancement: Learning-Focused Workflow
**Date:** November 2, 2025
**Commit:** [`054ff6a`](https://github.com/luisep92/Unity_training/commit/054ff6a)

### What I Did
- Updated `.claude/instructions.md` with "Teaching Mode" section
- Added "Core Concept" sections to existing entries in `Learnings.md`
- Created entry template with Core Concept field for future updates

### What I Learned
- Explicitly documenting learning goals changes how AI assistance works
- Separating "what I learned" (Unity-specific) from "core concepts" (universal principles) creates better reference material
- Good documentation templates ensure consistency across learning sessions

### Core Concept
*Learning documentation should capture both tool-specific knowledge and transferable principles. Tool knowledge becomes outdated, but fundamental concepts (rendering pipelines, architecture patterns, performance trade-offs) remain relevant across engines and technologies.*

---

## Entry Template for Future Updates

**Date:** [Date]
**Commit:** [`hash`](link)

### What I Did
- Bullet points of concrete actions

### What I Learned
- Unity-specific or technical learnings

### Core Concept *(only when applicable)*
*1-2 lines about fundamental game engine or game design concepts that transcend Unity - principles about rendering, architecture, performance, etc.*

### Challenges *(optional)*
- Problems encountered and solutions

---

*Updated after each development session.*

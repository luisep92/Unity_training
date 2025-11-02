# Learning Journey

High-level overview of what I built, learned, and overcame during this project.

---

## Project Initialization
**Date:** November 1, 2025
**Commit:** [`6921f64`](https://github.com/luisep92/Unity_training/commit/6921f64)

### What I Did
- Set up Unity 6 LTS (6000.2.10f1) project (later downgraded to 2022.3 LTS)
- Configured Git with .gitignore for Unity
- Created project documentation (.claude/context.md)

### What I Learned
- Unity 6 LTS is recent and has stability issues (crashed ~6 times, later forced downgrade)
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
- Unity 6 crashed multiple times (AssetImportWorker bug, later forced downgrade to 2022.3 LTS)

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

## Downgrade to Unity 2022.3 LTS for Stability
**Date:** November 2, 2025
**Commit:** [`96e3442`](https://github.com/luisep92/Unity_training/commit/96e3442)

### What I Did
- Downgraded from Unity 6.0 (6000.2.10f1) to Unity 2022.3.62f3 LTS
- Cleaned package manifest.json to remove Unity 6-specific packages
- Resolved package dependency conflicts (URP 17.x → 14.x, Visual Scripting 1.9.8 → 1.9.4)
- Deleted and regenerated Library/ folder for clean reimport
- Updated all documentation to reflect new version

### What I Learned
- **Package version compatibility:** Unity versions have specific package version ranges (URP 17.x only works with Unity 6)
- **Library/ regeneration:** Deleting Library/ forces Unity to reimport/recompile everything from source assets
- **Stability vs features:** Newer versions aren't always better - LTS releases are battle-tested and more stable
- **manifest.json vs packages-lock.json:** manifest is your intent, lock file is what's actually resolved

### Core Concept
*Semantic versioning and dependency resolution are fundamental to modern software. Breaking changes happen between major versions (Unity 6 vs 2022.3, URP 17 vs 14). LTS (Long Term Support) branches prioritize stability over features - critical for learning environments where crashes break flow. Production software often stays 1-2 versions behind cutting edge for this reason.*

### Challenges
- Initial downgrade failed with "invalid dependencies" errors
- Unity 6 had stored incompatible package versions in manifest.json
- Solution: Manually edited manifest.json to compatible versions + deleted Library/

### Why This Happened
- Unity 6 stability issues (frequent AssetImportWorker crashes)
- Learning projects need stable environments - crashes disrupt learning flow
- Unity 2022.3 LTS is mature (released 2023), widely used in production

---

## First Shader: Stylized Water (Phase 1 - Basic)
**Date:** November 2, 2025
**Commit:** [`fd608ba`](https://github.com/luisep92/Unity_training/commit/fd608ba)

### What I Did
- Created first Shader Graph: `StylizedWater_Shader.shadergraph`
- Built water shader with animated flow effect
- Implemented transparency with variable opacity
- Created configurable properties (Water Color, Flow Speed, Water Noise Scale)
- Set up TestWater scene with plane, camera, and test cube

### What I Learned
- **Shader Graph workflow:** Visual node editor → compiles to HLSL → GPU execution
- **UVs (Texture Coordinates):** 2D mapping (0-1) that defines how patterns map to 3D surfaces
- **Time-based animation:** Using Time node + math operations creates continuous motion
- **Gradient Noise:** Procedural pattern generation (Perlin-like noise for organic effects)
- **Remap node:** Transforms value ranges (e.g., 0-1 → 0.6-1) to control contrast
- **Alpha/Transparency:** Requires Surface Type: Transparent in both shader and material
- **Blackboard properties:** Expose shader parameters to Inspector for runtime tweaking
- **Vertex vs Fragment shaders:**
  - Vertex: Runs per vertex, can deform geometry (visual only, not physics)
  - Fragment: Runs per pixel, calculates color/transparency
- **Post-processing vs Shaders:**
  - Post-process: 2D image operations after rendering (no geometry)
  - Shaders: Run during 3D render (can affect geometry visually)

### Shader Structure (Phase 1)
```
Time → Multiply(Flow Speed) → Add ← UV
                                ↓
                         Gradient Noise(scale)
                                ↓
                         Remap(0.6 to 1.0)
                                ↓
                         [Water Color] → Multiply → Base Color
                                ↓
                              Alpha
```

**Effect:** Blue-green water with animated noise pattern, semi-transparent with variable opacity.

### Core Concept
*Shaders execute in parallel on the GPU, processing millions of pixels simultaneously. They're stateless (no memory between frames) and data-flow oriented (input → transformation → output). Understanding this parallel, stateless nature is fundamental to all GPU programming across engines and APIs.*

*Shader Graph abstracts HLSL syntax while teaching correct shader concepts (UVs, noise, time animation, remap). These concepts are universal - Unreal's Material Editor, Godot's Visual Shaders, and Blender's Shader Nodes use identical principles with different node names. Mastering visual shader editors provides 90% of the knowledge needed for any engine.*

*Vertex shaders move geometry VISUALLY (what you see) but don't update physics/collisions (what you touch). Fragment shaders only calculate color/transparency without moving anything. Post-processing operates on the final 2D image after all 3D rendering is complete.*

### Challenges
- Initial confusion about where to set Surface Type (Graph Settings vs Material Inspector)
- Understanding the difference between uniform transparency (Float) vs variable transparency (Remap → Alpha)
- High contrast in noise (black-to-blue) solved with Remap node
- Visual Scripting package causing warnings → removed via Package Manager

### Camera Configuration (Learned)
- Post Processing: Enable in camera
- Anti-aliasing: SMAA (post-process AA, complementary to MSAA)
- Stop NaNs: Prevents shader math errors
- Dithering: Reduces color banding in gradients

### Technical Details
- Shader Graph compiles to HLSL automatically
- Properties become shader uniforms (accessible from C# via Material.SetFloat/SetColor)
- Transparent surface type changes render queue (draws after opaque objects)
- Gradient Noise is GPU-computed (no texture lookup, procedural)

### Next Steps (Phase 2 - Planned)
- Add normal map animation for wave detail
- Implement Fresnel effect (edge transparency)
- Add foam at intersection with objects (depth fade)
- Explore vertex displacement for 3D waves (visual only)

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

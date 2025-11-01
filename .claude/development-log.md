# Development Log

## 2024-11-01 - Project Initialization

### Decisions Made

**Project Structure:**
- Modular organization by feature, not file type
- Each module self-contained and exportable
- `_Core/` for truly universal code only
- `_Shared/` within categories for domain-specific common code

**Folder Hierarchy:**
```
Assets/
├── Assets/                    # Third-party (gitignored)
├── ThirdParty_Modified/       # Modified third-party (Git LFS)
└── GameAssets/               # Our work
    ├── _Core/
    ├── Character/
    ├── Environment/
    │   ├── _Shared/
    │   ├── Water/
    │   ├── Vegetation/
    │   └── Creatures/
    ├── VFX/
    └── Scenes/
```

**Git Strategy:**
- Git LFS for binary assets (.fbx, .png, textures, audio)
- Modified third-party assets tracked separately
- Original asset packs documented but gitignored

**Visual Target:**
- Reference: Keeper by Microsoft
- Vibrant, saturated, cartoon/stylized
- Heavy post-processing (bloom, color grading)
- Low-poly hand-painted aesthetic

### Technical Constraints
- Unity 6000.0.61f1 LTS
- URP (no HDRP, no RTX features)
- GTX 1080Ti target hardware
- 60fps minimum

### Implementation
- Created base folder structure in Unity
- Configured Git LFS for binary assets
- Added README.md to each module describing purpose
- Created Main_scene.unity as starting point

### Cleanup (2025-11-01)
- Removed example Scripts/ folder (HelloWorld.cs)
- Tracked missing .meta files
- Established principle: only create subfolders when assets exist (no empty placeholders)

### Next Session Goals
1. Configure URP baseline (post-processing, quality settings for vibrant look)
2. Design character controller architecture
3. Implement basic movement
4. Create first shader (water suggested as most visually impactful)

### Open Questions
- Which specific asset packs to use? (TBD when we start scene composition)
- Exact post-processing values? (Will tune during URP setup)
- Character controller input system? (New Input System vs old?) - Likely new

### Code Architecture Principles Established
- Interface-based design
- Data classes for configuration
- Tests where applicable (acknowledge Unity limitations)
- Thin MonoBehaviours
- Event-driven environmental reactions
- ScriptableObjects for data

---

## 2025-11-01 - URP Configuration Complete

### What Was Built:
- Created custom URP Render Pipeline Asset: `CustomURP_StylizedSettings`
- Created custom URP Renderer: `CustomURP_StylizedSettings_Renderer`
- Created Volume Profile: `CustomVolumeProfile_Stylized`
- Configured scene-based fog for atmospheric depth
- Test scene (TestScene) created for validation

### Decisions Made:
- **URP Quality Settings:**
  - HDR: Enabled (wider color/brightness range)
  - MSAA: 4x (smooth edges on geometry)
  - Render Scale: 1.0 (native resolution)
  - Shadow Resolution: 2048 (high quality shadows)
  - Shadow Distance: 50 units
  - Depth Texture: Enabled (required for effects)
  - Opaque Texture: Enabled (required for advanced effects)

- **Post-Processing Stack (Volume Profile):**
  - Tonemapping: Neutral mode (HDR color mapping)
  - Bloom: Intensity 0.3 (subtle glow on bright areas)
  - Color Adjustments: Contrast +15, Saturation +20 (vibrant, punchy colors)
  - White Balance: Temperature -5 (slightly cooler/bluer tone)
  - Other effects present but inactive (intensity 0) for future use

- **Fog Configuration:**
  - Mode: Linear
  - Color: Light blue (matches skybox)
  - Start: 15 units
  - End: 70 units
  - Provides atmospheric depth and fantasy ambiance

### Technical Details:
- URP Asset referenced in Project Settings > Graphics
- Volume Profile assigned to URP Asset as default global volume
- Post-processing must be enabled per-camera (UniversalAdditionalCameraData component)
- Fog configured in Lighting window > Environment > Other Settings (not a Volume override in URP)

### Problems Encountered:
- Unity 6 stability issues: Multiple crashes during session (AssetImportWorker errors)
- Initial confusion about Volume system vs URP Asset roles clarified
- Fog is NOT a Volume override in URP (unlike HDRP) - configured in Lighting settings instead

### Next Steps:
1. Design character controller architecture (interfaces, data classes)
2. Implement basic third-person movement
3. Create first custom shader (water recommended)

### Open Questions:
- Should we reduce MSAA/quality settings to improve editor stability?
- Final post-processing values will be tuned once we have actual scene content

---

## 2025-11-01 - Priority Shift: Visual-First Approach

### Decision Made:
**Reprioritized development order: Shaders and environment BEFORE character controller**

### Reasoning:
- Character controller with full animations is heavy work:
  - Controller + input system
  - 3D model + rigging
  - Animation set (idle, walk, run, jump)
  - Blend trees for transitions
  - Integration with environment

- Visual elements (shaders, environment) are:
  - Developer's primary interest and learning goal
  - Can be tested/iterated in Scene view or with static Game camera
  - More impactful for portfolio showcase
  - Foundation for learning ShaderGraph (needed for all custom shaders)

- Scene inspection is sufficient for testing without player movement

### New Priority Order:
1. **Water shader** (ShaderGraph) - High visual impact, teaches foundation
2. **Basic terrain** - Context for water placement
3. **Vegetation/wind shader** - Builds on ShaderGraph knowledge
4. **Minimal controller** - Simple capsule + WASD + mouse (NO model/animations)
5. **Environmental reactivity** - Systems that react to player presence
6. **Character model/animations** - DEFERRED until environment complete

### Next Immediate Step:
Create stylized water shader using ShaderGraph (animated, cartoon aesthetic)

---

## Template for Future Entries

### [Date] - [Session Title]

**What Was Built:**
- Item 1
- Item 2

**Decisions Made:**
- Decision 1: Reasoning
- Decision 2: Reasoning

**Technical Details:**
- Implementation notes
- Performance considerations
- Shader specifics, etc.

**Problems Encountered:**
- Problem: Solution

**Next Steps:**
- Task 1
- Task 2

**Open Questions:**
- Question 1
- Question 2
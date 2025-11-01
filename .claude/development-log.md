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

### Next Session Goals
1. Create folder structure in Unity project
2. Configure URP baseline (post-processing, quality settings)
3. Design character controller architecture
4. Implement basic movement
5. Create first shader (water suggested as most visually impactful)

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
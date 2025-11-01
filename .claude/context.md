# Project Context - Unity Portfolio Diorama

## Project Goal
Create a visually impressive portfolio demo showcasing technical and artistic skills in Unity.
Single explorable diorama scene with emergent environmental interactions - NOT a full game.

## Technical Specs
- **Unity Version**: 6000.0.61f1 LTS
- **Render Pipeline**: URP (Universal Render Pipeline)
- **Target Hardware**: GTX 1080Ti (no RTX features)
- **Target Performance**: 60fps minimum
- **Platform**: Windows PC

## Visual Style
- Vibrant, stylized/cartoon aesthetic (reference: Keeper by Microsoft)
- Saturated colors, hand-painted textures, low-poly models
- Heavy post-processing (bloom, color grading, fog)
- Non-realistic, fantasy-oriented environment

## Core Features (In Priority Order)

### 1. Character Controller
- Basic third-person movement (WASD + mouse camera)
- Smooth, responsive controls
- NO complex mechanics (no combat, inventory, etc.)

### 2. Environmental Reactivity
- **Creatures**: Small animals (lizards, butterflies) that flee when player approaches
- **Vegetation**: Grass/plants that sway when player walks through
- **Particles**: Magical motes/dust that disperse with player movement
- All reactions are ORGANIC - no UI prompts, no interaction buttons

### 3. Custom Shaders (2-3 total)
- Water shader (stylized, animated)
- Vegetation wind/interaction shader
- Magical effect shader (particles, auras)

### 4. World Composition
- Single cohesive diorama scene
- Explorable but contained (not open world)
- Multiple areas of interest within small space
- Ambient life and movement throughout

## What We're NOT Building
❌ Complex gameplay mechanics
❌ AI systems beyond simple flee behavior
❌ Quest systems, dialogue, story
❌ Inventory, items, pickups
❌ UI interaction prompts
❌ Combat or progression systems

## What We ARE Building
✅ Beautiful, walkable environment
✅ Emergent ambient interactions
✅ Impressive VFX that react to player
✅ Clean, reviewable code architecture
✅ Custom shaders demonstrating technical skill

## Project Structure

```
Assets/
├── Assets/                          # Third-party assets (gitignored)
└── GameAssets/                      # Our custom work (tracked)
    ├── _Core/                       # Shared interfaces, utils, rendering config
    ├── Character/                   # Complete player module
    ├── Environment/                 # All environment systems
    │   └── _Shared/                # Common environmental code
    │       # Subfolders (Water, Vegetation, Creatures) created as needed
    ├── VFX/                        # Particle systems and magical effects
    └── Scenes/
```

### Module Philosophy
- Each folder is self-contained and exportable
- Modules group by FEATURE, not file type
- **Create subfolders only when assets/code exist** - no empty placeholder folders
- Use `_Shared/` for common code within a category
- `_Core/` only for things EVERYTHING needs

## Code Standards
- **Language**: All code, comments, and docs in English
- **Architecture**: Interface-based with data classes
- **Testing**: Write tests where applicable (especially for abstract classes)
- **No emojis** in code
- **Composition over inheritance** where it makes sense
- **ScriptableObjects** for configuration data
- **Thin MonoBehaviours** - logic in separate classes
- **Event-driven** architecture for environmental reactions

## Asset Strategy
- Use free/cheap Asset Store packs (Stylized Nature, Synty Studios, Quaternius)
- Custom shaders to demonstrate technical skill
- Well-configured post-processing stack
- Modified third-party assets go in `Assets/ThirdParty_Modified/` (Git LFS tracked)
- Pure third-party assets stay in `Assets/Assets/` (gitignored)

## Git Workflow
- Git LFS configured for large assets (.fbx, .png, .wav, etc.)
- Modified third-party assets are tracked and documented
- Original asset packs documented in `ThirdParty_Modified/README.md`

## Current Status
- ✅ Unity project created (Unity 6000.0.61f1 LTS)
- ✅ Git repository initialized with proper .gitignore
- ✅ Modular folder structure created (core modules only)
- ✅ Git LFS configured (.gitattributes)
- ✅ Basic project structure committed
- ✅ URP configured (vibrant, stylized look with post-processing and fog)
- ⏳ Water shader (first custom shader) - IN PROGRESS
- ⏳ Basic terrain/environment pending
- ⏳ Minimal character controller (capsule only, no animations) - DEFERRED

## Next Steps (Priority Order)
1. **Create water shader** (ShaderGraph) - Visual impact + learning foundation
2. **Create basic terrain** - Context for water and environment
3. **Vegetation/wind shader** - Build on ShaderGraph knowledge
4. **Minimal player controller** - Capsule + WASD + mouse look (no model/animations yet)
5. **Environmental reactivity system** - Creatures flee, grass sways, particles react
6. **Character model + animations** - LATER (when environment is complete)

## Reference Visual Style
See: `/mnt/project/keeper.png` - This is the vibrant, saturated, fantasy aesthetic we're aiming for.

## Development Notes
- Developer has strong C# knowledge but is "a bit rusty" with Unity
- Familiar with Godot and general game dev concepts
- NOT an artist - will use asset packs
- Strong interest in learning shaders
- Prefers clear, explicit instructions over implicit assumptions
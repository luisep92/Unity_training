# Instructions for Claude Code

## 🎓 LEARNING PROJECT - Teaching Mode

**THIS IS A LEARNING PROJECT. The user is learning Unity, shaders, and game development.**

### Default Behavior:
- **GUIDE, don't do the work** - Explain concepts, provide step-by-step instructions
- **Ask questions** to make the user think about solutions
- **Explain the "why"** behind each decision or technique
- **Let the user make the changes** in Unity/code unless they specifically ask for files/code

### When to Provide Direct Implementation:
- User explicitly asks: "create the file", "write the code", "do X for me"
- User asks for specific code examples to study
- User is stuck and asks for help after trying
- Documentation or boilerplate that doesn't have learning value

### Teaching Approach:
- Break complex tasks into small, manageable steps
- Explain Unity/shader concepts as they come up
- Point out common pitfalls before the user hits them
- Provide context: "This is how Unity handles X because..."
- Reference Unity documentation when relevant

**Remember: The goal is for the USER to learn, not for the project to be completed quickly.**

---

## Working Language
- All conversations with the user will be in **Spanish**
- All code, comments, variable names, and documentation must be in **English**
- No emojis in code or technical documentation

## Code Style Preferences

### Architecture
- **Prefer interfaces/abstract classes** for contracts
- **Use data classes** for interfaces (C# records when appropriate)
- **Write tests** where applicable:
  - Tests use abstract classes
  - Tests never depend on implementation details
  - Acknowledge that some game systems can't be easily tested
- **Implementation comes last**: Interface → Tests → Implementation

### Unity Specific
- **ScriptableObjects** for configuration data
- **Thin MonoBehaviours** - keep logic in separate classes
- **Event-driven** for environmental reactions (no polling when avoidable)
- **Composition over inheritance** where it makes sense

### File Organization
- Each module is self-contained
- Group by feature/domain, not file type
- If multiple systems share code within a domain, use `_Shared/` subfolder
- Only truly universal code goes in `_Core/`

## Project-Specific Rules

### What to Build
✅ Visual impressiveness
✅ Environmental reactivity (organic, emergent)
✅ Clean code architecture
✅ Custom shaders (2-3 focused on visual impact)
✅ Smooth character movement

### What NOT to Build
❌ Complex gameplay mechanics
❌ UI interaction prompts
❌ Inventory/pickup systems
❌ Quest/story systems
❌ Combat systems
❌ Artificial "juice" or game-feel polish (this is a tech demo, not a game)

## Working with Assets
- Third-party assets that we DON'T modify → `Assets/Assets/` (gitignored)
- Third-party assets that we DO modify → `Assets/ThirdParty_Modified/` (Git LFS)
- Always document modified assets in `ThirdParty_Modified/README.md`
- Our original work → `Assets/GameAssets/`

## Response Style Preferences
- **Be clear and explicit** - don't give multiple versions or alternate approaches unless asked
- **Don't overwhelm responses** with excessive options
- **When giving instructions**: One clear path, not "you could do A, or B, or C..."
- **For file operations**: Create the file and provide download link, don't just show code snippets
- **Avoid verbosity** in explanations - the user knows Unity basics

## Performance Considerations
- Target hardware: GTX 1080Ti (no RTX features)
- Must maintain 60fps minimum
- URP optimizations are important
- Shader complexity should be moderate (no RTX-only features, careful with overdraw)

## Current Project State
- Unity 2022.3.62f3 LTS
- URP template project created
- Git repo initialized
- Folder structure designed but not yet created in Unity
- No code written yet
- No assets imported yet

## Development Flow
When the user asks to implement something:
1. Design the interface/abstract class first
2. Show the data structures
3. Discuss architecture if needed
4. Write tests if applicable
5. Implement the concrete classes
6. Create Unity-specific MonoBehaviour wrappers if needed

## Communication
- User will point out if explanations are too verbose
- User prefers direct, actionable responses
- If something is unclear, user will ask - don't over-explain preemptively
- When in doubt about approach, present ONE recommended solution (not multiple options)

## Git Workflow
- Git LFS is configured for large binary files
- User will handle git operations (commits, pushes)
- Claude Code can create/modify files directly in the repository
- Always ensure changes are in appropriate module folders

## Testing Strategy
- Unit tests for core logic classes (in `_Core/`, `_Shared/`)
- Integration tests where it makes sense (character input → movement)
- Skip tests for pure MonoBehaviour/Unity-specific code that's hard to test
- Tests should be in same module as code they test: `[Module]/Tests/`
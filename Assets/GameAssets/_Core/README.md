# Core Systems

Contains code and interfaces that are used across the entire project.

## What goes here:
- ✅ Base interfaces used by multiple modules
- ✅ Universal utilities (math helpers, extension methods)
- ✅ Global rendering/quality configurations
- ✅ Event system infrastructure

## What does NOT go here:
- ❌ Domain-specific code (use module-specific folders)
- ❌ Code only used by one or two modules (use `_Shared/` within that domain)

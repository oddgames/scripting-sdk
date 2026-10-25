# Changelog

All notable changes to this package are documented in this file.

## [1.0.1] - 2026-10-25

### Changed
- Debug hooks (opt-in via ScriptCompileOptions.DebugHooks): IScriptDebugHook hears every statement (awaitable, so a host can park an async script before a line) and every exception no script catch will handle, answering Throw / Retry / Skip / Defer; ScriptDebugFrame exposes the line, method and read-only locals. Fixed: async catch/break/continue/return-through-finally leaving stale try handlers registered.

## [1.0.0]

### Added
- First standalone release of `au.com.oddgames.scripting`, split out of the Bugpunch SDK. Ships `ODDGames.Scripting.dll` (compiler, VM, sandbox, browser IDE) and `ODDGames.Scripting.Unity.dll` (`ScriptRuntime`, `ScriptIdeServerHost`, `UnityScriptConventions`) as precompiled assemblies.
- Protection by attribute name: any attribute type named `ScriptProtectedAttribute` exposing `RequiredLevel` (int-convertible, `ScriptTrustLevel` values) and optional `Reason` is honoured like `ODDGames.Scripting.ScriptProtectedAttribute`. `ScriptProtection.TryGet` / `IsProtected` expose the lookup to hosts.

### Changed
- `ODDGames.Scripting.Unity` is now a precompiled DLL instead of a source asmdef. Asmdefs that referenced it by name or GUID (`GUID:48fbb393c4f7441d85861b0c559eddbd`) should drop that reference; the DLL is auto-referenced.

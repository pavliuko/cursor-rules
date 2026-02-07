## Build Commands

Use XcodeBuildMCP tools for all build operations. Set session defaults first:

```
mcp__XcodeBuildMCP__session-set-defaults projectPath: "<project-name>.xcodeproj" scheme: "<project-name>" simulatorName: "<simulator-name>"
```

### Building

Build for iOS Simulator:

```
mcp__XcodeBuildMCP__build_sim
```

Build and run on simulator:

```
mcp__XcodeBuildMCP__build_run_sim
```

Clean build artifacts:

```
mcp__XcodeBuildMCP__clean
```

### Testing

Run all tests:

```
mcp__XcodeBuildMCP__test_sim
```

Run specific test target:

```
mcp__XcodeBuildMCP__test_sim extraArgs: ["-only-testing:APITests"]
```

Run specific test class:

```
mcp__XcodeBuildMCP__test_sim extraArgs: ["-only-testing:<TestTarget>/<TestClass>"]
```

### Project Info

List available schemes:

```
mcp__XcodeBuildMCP__list_schemes
```

List available simulators:

```
mcp__XcodeBuildMCP__list_sims
```

### Packages

- Core and Features packages are iOS-only — use `mcp__XcodeBuildMCP__build_simbuild_sim`/`mcp__XcodeBuildMCP__test_sim` with main project
- Do not use `swift_package_build` or `swift_package_test` for iOS packages
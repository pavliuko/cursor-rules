# SwiftUI View Organization

For architecture principles, see `docs/swiftui-architecture.md`. This document covers view structure and organization.

## View Structure

### Property Ordering (top → bottom)

1. Environment properties
2. `private`/`public let` constants
3. `@State` / other stored properties
4. Computed `var` (non-view)
5. `init`
6. `body`
7. Computed view builders / other view helpers
8. Helpers / async functions

### Large Bodies

- If `body` grows beyond a screen or has multiple logical sections, split into smaller subviews
- Extract large computed view properties (`var header: some View { ... }`) into dedicated `View` types when they carry state or complex branching
- Keep related subviews as computed view properties in the same file; extract to a standalone `View` struct only when it structurally makes sense or when reuse is intended
- Prefer passing small inputs (data, bindings, callbacks) over reusing the entire parent view state

### Organizing Helpers

Use extensions to group related helpers:

```swift
struct ProfileView: View {
    @Environment(\.dismiss) private var dismiss
    @State private var user: User?
    @State private var isLoading = false

    var body: some View {
        // ...
    }
}

// MARK: - Subviews

private extension ProfileView {
    var header: some View {
        // ...
    }

    var content: some View {
        // ...
    }
}

// MARK: - Actions

private extension ProfileView {
    func loadUser() async {
        // ...
    }

    func saveChanges() async {
        // ...
    }
}
```

Move async functions and helper functions into dedicated private extensions, separated with `// MARK: -` comments that describe their purpose.

## Apple Documentation

For Apple documentation lookups, use the sosumi MCP server.

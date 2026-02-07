# Document Core Package UI Components

**Purpose**: Generate a concise quick-reference for the Core package's UI-related modules - just names and brief descriptions of design system, shared UI components, and routing.

## Format Example

```markdown
**DesignSystem:**
Import: `import DesignSystem`
- `ColorName` - Brief one-line description
- `FontStyle` - Brief description
- View extensions or helpers

**SharedUI:**
Import: `import SharedUI`
- `ComponentName` - Brief one-line description
  - `.property` - What it does
  - `.method()` - What it does
```

## What to Document

Document only these three directories:
- `Packages/Core/Sources/DesignSystem/` - Design tokens, colors, fonts, images
- `Packages/Core/Sources/SharedUI/` - Reusable UI components
- `Packages/Core/Sources/Router/` - Navigation and routing abstractions

### Include:
- Public types (classes, structs, enums, protocols) with ONE-LINE description
- Public global functions with ONE-LINE description
- Public extensions with ONE-LINE description
- Colors, fonts, and asset references from DesignSystem
- UI components from SharedUI
- Router protocols and implementations from Router

### Keep it Brief:
- ❌ NO detailed explanations
- ❌ NO code examples or usage patterns
- ❌ NO full signatures with all parameters
- ❌ NO implementation details
- ✅ Just name + very short description (15 words max)
- ✅ Bullet points, not paragraphs
- ✅ Focus on discoverability, not teaching

## Analysis Approach

1. Scan `Packages/Core/Sources/DesignSystem/` for colors, fonts, images, and styles
2. Scan `Packages/Core/Sources/SharedUI/` for reusable UI components
3. Scan `Packages/Core/Sources/Router/` for routing protocols and implementations
4. Use `grep` to find `public` declarations in Swift files
5. Extract type/function/property names
6. Write one short sentence per item describing what it is/does

## Documentation Output

Update `docs/core-ui-components.md` as a **compact quick-reference** with:

- Brief intro (2-3 lines)
- Three main sections: DesignSystem, SharedUI, Router
- Bullet-point list of public APIs with minimal descriptions
- No examples, no detailed docs, no tutorials
- Keep existing structure and format
- Add new components/APIs discovered
- Update descriptions if changed
- Remove entries for deleted components

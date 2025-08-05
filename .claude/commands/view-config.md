### Steps

Refactor SwiftUI View into Configurable Component with nested ViewConfiguration struct and generate SwiftUI-style modifier functions to allow clean, chainable customizations.

1. **Locate Target View**

   * Find struct name in $ARGUMENTS or locate in chosen file if not specified.
   * Ensure it conforms to `View` protocol.

2. **Analyze Existing ViewConfiguration**

   * Detect if a nested struct named **ViewConfiguration** exists inside the View.
   * Collect all property names and types defined within ViewConfiguration.

3. **Detect Optional Configuration Properties**

   * Identify properties in the View struct that represent **optional configurations**:

     * Properties with default values.
     * Properties that affect visual appearance, behavior tuning, or component setup — but are not essential data or actions.
     * Examples: `color`, `font`, `radius`, `placeholder`, `rightImage`, `keyboardType`, `onChange`, `onSubmit`, etc.
   * **Exclude**:

     * Data-binding properties (e.g., `@Binding var text`).
     * Essential required data passed into the component (e.g., `title`, `errorMessage`).

4. **Move Properties to ViewConfiguration**

   * For each identified configurable property not yet in ViewConfiguration:

     * Move its definition into **ViewConfiguration** with default value.
     * Ensure the parent View struct has:

     ```swift
     private var config = ViewConfiguration()
     ```

     * Add if missing.

5. **Update View Body**

   * Replace all references of moved properties with `config.propertyName`.

6. **Update Initializer**

   * Remove moved configuration properties from the View’s initializer.
   * Retain only **required data parameters** (e.g., `title`, `onAction`, `binding`).

7. **Generate Modifier Functions**

   * For every property in ViewConfiguration:

     * Generate missing modifier functions as public extensions:

       ```swift
       public func titleColor(_ value: Color) -> Self {
           var copy = self
           copy.config.titleColor = value
           return copy
       }
       ```
     * Functions should:

       * Match property name.
       * Accept a parameter of the property’s type.
       * Return a modified instance of Self (immutably).

8. **Maintain Access Scope**

   * Ensure ViewConfiguration struct and generated functions have the same access level (e.g., `public`) as the View struct.

---

### Example Scenario

#### Input:

```swift
public struct GrindrButton: View {
    private let title: String
    private let onAction: () -> Void
    private var titleColor: Color = .black
    private var buttonBackgroundColor: Color = .yellow
    private var titleFont: Font = .body

    public init(title: String, onAction: @escaping () -> Void) {
        self.title = title
        self.onAction = onAction
    }

    public var body: some View {
        Button(action: onAction) {
            Text(title)
                .font(titleFont)
                .foregroundStyle(titleColor)
        }
        .background(buttonBackgroundColor)
    }
}
```

#### Output:

```swift
public struct GrindrButton: View {
    // Nested
    public struct ViewConfiguration {
        var titleColor: Color = .black
        var buttonBackgroundColor: Color = .yellow
        var titleFont: Font = .body
    }

    private let title: String
    private let onAction: () -> Void
    private var config = ViewConfiguration()

    public init(title: String, onAction: @escaping () -> Void) {
        self.title = title
        self.onAction = onAction
    }

    public var body: some View {
        Button(action: onAction) {
            Text(title)
                .font(config.titleFont)
                .foregroundStyle(config.titleColor)
        }
        .background(config.buttonBackgroundColor)
    }
}

// ViewConfiguration
public extension GrindrButton {
    func titleColor(_ value: Color) -> Self {
        var copy = self
        copy.config.titleColor = value
        return copy
    }

    func buttonBackgroundColor(_ value: Color) -> Self {
        var copy = self
        copy.config.buttonBackgroundColor = value
        return copy
    }

    func titleFont(_ value: Font) -> Self {
        var copy = self
        copy.config.titleFont = value
        return copy
    }
}
```

---

### Idempotency

* The tool must be safely re-runnable.
* No duplicate properties in ViewConfiguration.
* No duplicate modifier functions in extensions.

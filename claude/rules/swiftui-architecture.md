# UI-heavy Feature Architecture

## Core Philosophy

* SwiftUI is no longer a "new" framework — it’s the default UI paradigm for Apple platforms.
* Stop applying legacy patterns designed for UIKit.
* Embrace SwiftUI’s declarative nature and native data flow.
* Focus on simplicity, co-location of logic, and clear state ownership.


## Architecture Principles

### 1. Use SwiftUI's Built-in State System

* `@State` → Local view state (always use **structs**, never `@Observable` classes)
* `@Observable` → Shared app-wide state only (injected via `@Environment`)
* `@Binding` → Two-way binding from parent to child
* `@Environment` / `@EnvironmentObject` → For dependencies like theme, auth, routing, etc.

---

### 2. No Need for External Abstractions

Avoid adding layers between the data and the UI. Don’t introduce mediators like ViewModel, Presenter, or Controller.
* Use native tools: `@State`, `@Binding`, `@Observable`, and `@Environment`.
* Let the view own and manage its state unless reuse or sharing is *actually* required.

---

### 3. Follow Unidirectional Data Flow

* **State goes down, actions go up.**
* Views describe the UI; they do not own the business logic for the whole app.
* Mutate state via simple methods or property assignments, not command handlers.

```swift
struct SettingsView: View {
    @Binding var isDarkMode: Bool

    var body: some View {
        Toggle("Dark Mode", isOn: $isDarkMode)
    }
}
```

---

### 4. Lifecycle and Side Effects

* Use `.task`, `.onAppear`, `.onChange`, etc. — they are lifecycle-aware.
* Prefer `async/await` to Combine or manual callbacks.
* Avoid complex managers to coordinate view logic.

**`.task` vs `.onAppear`:**
* `.task` — Runs async work tied to view lifecycle; automatically cancelled when view disappears. Ideal for async/await operations.
* `.onAppear` — Fires every time the view appears; synchronous context. Use for non-async setup or when you need re-execution on each appearance.

```swift
.task {
    isLoading = true
    user = try? await API.fetchUser()
    isLoading = false
}
```

---

### 5. Compose UI with Small Views

* Keep views focused and readable.
* Extract subviews for repeated or logically isolated sections.
* Use functions or separate `View` types — whatever is simplest and clearest.

```swift
var body: some View {
    VStack {
        Header()
        Content()
        Footer()
    }
}
```

---

### 6. Avoid These Anti-patterns

* ❌ Using `@Observable` class for view-local state (use struct with `@State` instead)
* ❌ Wrapping properties in external objects just to "test better"
* ❌ Moving state out of views for no good reason
* ❌ Duplicating SwiftUI's existing data flow tools
* ❌ Creating "controllers" or "managers" that mimic UIKit patterns
* ❌ Pretending SwiftUI needs to be architected like UIKit

---

### 7. Modern Testing Approach

* **Test business logic in isolation** — Extract to services/utilities, not ViewModels
* **Use SwiftUI previews for UI testing** — They're faster and more reliable than UI tests
* **Embrace view testing** — Test view behavior with different state values
* **Don't force testability** — If logic is hard to test, it might not need testing

```swift
// ✅ Test business logic separately
struct UserValidatorTests {
    @Test func validEmail() {
        #expect(UserValidator.isValid(email: "test@example.com"))
    }
}

// ✅ Test views with different states
#Preview("Loading State") {
    UserListView(users: [], isLoading: true)
}

#Preview("Error State") {
    UserListView(users: [], error: "Network unavailable")
}
```

---

### 8. Async + Concurrency = First-Class Citizens

* Swift Concurrency should be your default tool for async logic.
* Use `Task {}` or `.task` in views; they integrate cleanly with the view lifecycle.
* Avoid Combine unless absolutely necessary (e.g. interop or reactive streams).

---

### 9. When to Extract Logic from Views

**Extract to @Observable when:**
- State needs to be shared across multiple views that aren’t in the same hierarchy
- Logic involves complex business rules
- State needs to persist across view lifecycle

**Keep in views when:**
- State is purely UI-related (isExpanded, selectedTab, etc.)
- Logic is simple transformations or validations
- State is tied to a specific view's lifecycle

---

### 10. Organize Code by Feature

* Group files by **feature**, not by type.
* Keep logic and UI close together until duplication or complexity makes it worth extracting.

---

### 11. Performance Tips

* **@Observable is more efficient** — Less overhead than ObservableObject
* **View updates are surgical** — SwiftUI only updates what changed
* **Avoid unnecessary @State splitting** — One @State object is often better than multiple primitives
* **Use view identity correctly** — Provide stable IDs for list items

---

### 12. Examples: Simple to Complex

#### Example 1: Views Own Their State

```swift
// ✅ Local state, no external abstractions
struct CounterView: View {
    @State private var count = 0
    
    var body: some View {
        VStack {
            Text("Count: \(count)")
                .font(.title)
            
            HStack {
                Button("Decrement") { count -= 1 }
                Button("Increment") { count += 1 }
            }
            .buttonStyle(.bordered)
        }
    }
}
```

#### Example 2: Simple Stateless Service

```swift
// ✅ View uses service directly, owns loading state
struct UserListView: View {
    @State private var users: [User] = []
    @State private var isLoading = false
    
    var body: some View {
        List(users, id: \.id) { user in
            Text(user.name)
        }
        .task {
            isLoading = true
            users = try await UserService.fetchUsers()
            isLoading = false
        }
        .overlay {
            if isLoading {
                ProgressView()
            }
        }
    }
}

// Service handles data operations
struct UserService {
    static func fetchUsers() async throws -> [User] {
        // Network call
        return []
    }
}
```

#### Example 3: Single State Object

```swift
// ✅ Single state object for related data
struct FormData {
    var name = ""
    var email = ""
    var isValid: Bool { !name.isEmpty && !email.isEmpty }
    var showingError = false
    
    mutating func validate() {
        showingError = !isValid
    }
}

struct FormView: View {
    @State private var form = FormData()
    
    var body: some View {
        VStack {
            TextField("Name", text: $form.name)
            TextField("Email", text: $form.email)
            
            if form.showingError {
                Text("Please fill all fields")
                    .foregroundColor(.red)
            }
            
            Button("Submit") { form.validate() }
                .disabled(!form.isValid)
        }
    }
}
```

#### Example 4: Shared State with @Observable

```swift
// ✅ Shared state for truly global concerns
@Observable
class AppState {
    var currentUser: User?
    var isAuthenticated = false
    
    func signIn(user: User) {
        currentUser = user
        isAuthenticated = true
    }
}

struct MyApp: App {
    @State private var appState = AppState()
    
    var body: some Scene {
        WindowGroup {
            ContentView()
                .environment(appState)
        }
    }
}

struct ProfileView: View {
    @Environment(AppState.self) private var appState
    
    var body: some View {
        if let user = appState.currentUser {
            Text("Welcome, \(user.name)")
        } else {
            Text("Not signed in")
        }
    }
}

struct SettingsView: View {
    @Environment(AppState.self) private var appState
    
    var body: some View {
        Button("Sign Out") {
            appState.currentUser = nil
            appState.isAuthenticated = false
        }
    }
}
```

---

SwiftUI is not UIKit. Don't try to make it behave like it is.
Let your code look like SwiftUI, not like 2015-era patterns.
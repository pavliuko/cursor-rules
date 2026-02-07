# Unit Testing Guidelines

## Core Principles

- Test non-trivial business logic that could cause production issues
- Use ONLY Swift Testing framework (not XCTest)
- Focus on behavior, not implementation

## What to Test

**DO test:**
- Non-trivial business logic with complex conditions or calculations
- State machines and transitions
- Edge cases that could fail silently (empty arrays, nil values, boundary conditions)
- Error handling paths and recovery logic
- Async operations and race condition-prone code
- Data transformations and parsing
- Integration points between components

**DO NOT test:**
- Getters/setters and simple property access
- Simple initializers with direct assignments
- Default values and nil checks
- Code that merely mirrors the implementation
- SwiftUI view bodies (use previews instead)
- Trivial computed properties
- Boilerplate or self-evident code

## Decision Framework

Before writing a test, ask:

1. **Could this bug reach production?** — If trivial and obvious, skip it
2. **Is this testing behavior or implementation?** — Test what it does, not how
3. **Would a failure here be hard to diagnose?** — Prioritize complex logic
4. **Is there meaningful state transformation?** — Simple pass-through doesn't need tests

## Swift Testing Framework

### Basic Structure

```swift
import Testing

struct UserValidationTests {
    @Test func validatesEmailFormat() {
        let validator = EmailValidator()
        #expect(validator.isValid("user@example.com"))
        #expect(!validator.isValid("invalid-email"))
    }

    @Test func rejectsEmptyEmail() throws {
        let validator = EmailValidator()
        #expect(throws: ValidationError.empty) {
            try validator.validate("")
        }
    }
}
```

### Key APIs

| API                   | Purpose                                            |
| --------------------- | -------------------------------------------------- |
| `@Test`               | Mark a function as a test                          |
| `@Suite`              | Group related tests (flat, no nesting)             |
| `#expect(condition)`  | Assert condition is true                           |
| `#require(condition)` | Assert and throw if false, safely unwrap optionals |
| `#expect(throws:)`    | Assert error is thrown                             |

### Safe Unwrapping with #require

```swift
@Test func parsesUserResponse() throws {
    let response = try #require(api.parseResponse(data), "Failed to parse response")
    #expect(response.userId == "123")
}
```

### Parameterized Tests

```swift
@Test(
  "Price calculation",
  arguments: [
    (quantity: 1, price: 10.0, expected: 10.0),
    (quantity: 5, price: 10.0, expected: 50.0),
    (quantity: 0, price: 10.0, expected: 0.0),
  ]
)
func priceCalculation(quantity: Int, price: Double, expected: Double) {
    let result = calculateTotal(quantity: quantity, unitPrice: price)
    #expect(result == expected)
}
```

Use `zip()` for paired arguments (avoids Cartesian product):

```swift
@Test("Paired inputs", arguments: zip([1, 2, 3], ["a", "b", "c"]))
func pairedTest(number: Int, letter: String) {
    // Runs 3 times, not 9
}
```

### Async Testing

```swift
@Test func fetchesUserData() async throws {
    let service = UserService()
    let user = try await service.fetchUser(id: "123")
    #expect(user.id == "123")
}
```

### Testing Errors

```swift
@Test func throwsOnInvalidInput() {
    #expect(throws: ParsingError.invalidFormat) {
        try parser.parse("invalid data")
    }
}
```

### Traits

Control test behavior with traits on `@Test` or `@Suite`:

```swift
// Define custom tags
extension Tag {
    @Tag static var authentication: Self
    @Tag static var critical: Self
    @Tag static var slow: Self
}

// Tags on suite apply to all tests
@Suite(.tags(.authentication))
struct LoginTests {
    @Test func validCredentials() { }
    @Test func invalidPassword() { }
}

// Tags on individual tests
@Test(.tags(.critical, .slow))
func testComplexCalculation() { }

// Conditional enable/disable
@Test(.enabled(if: FeatureFlags.newParser))
func testNewParser() { }

@Test(.disabled("Waiting for API v2"))
func testUpcomingFeature() { }

// Time limits
@Test(.timeLimit(.minutes(1)))
func testLongOperation() async { }

// Bug tracking (test still runs)
@Test(.bug("https://github.com/org/repo/issues/123"))
func testWithKnownBug() { }
```

### Known Issues

Mark expected failures without disabling the test:

```swift
@Test func testWithKnownIssue() {
    withKnownIssue("API returns wrong format until v2.1") {
        let result = api.fetch()
        #expect(result.format == .json)  // Won't fail the test
    }
}
```

## Test Organization

```
Tests/
├── CoreTests/
│   ├── ValidationTests.swift
│   └── ParsingTests.swift
└── FeaturesTests/
    └── OrderProcessingTests.swift
```

Keep test suites flat with descriptive names — avoid nested `@Suite` declarations.

## Running Tests

For running tests, see `.claude/rules/build-commands.md`
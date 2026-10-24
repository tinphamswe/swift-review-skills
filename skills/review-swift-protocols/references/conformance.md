# Swift Declaration and Conformance Convention

Use these section markers and ordering where they fit the declarations in a file:

```swift
// MARK: - SomeProtocol

protocol SomeProtocol {

}

// MARK: - SomeClass

final class SomeClass {
    // dependencies here
}

// MARK: - Conformance

extension SomeClass: SomeProtocol {

}

// MARK: - {Section name}

extension SomeClass {

}

// MARK: - Private

private extension SomeClass {

}
```

Prefer a separate extension for each protocol conformance and group related members into named extensions. Keep implementation-specific helpers private. Adapt section names to the declarations present; do not add empty sections solely to match the example.

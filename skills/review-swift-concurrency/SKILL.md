---
name: review-swift-concurrency
description: >
  Review Swift code for actor isolation, shared mutable state, data races,
  task cancellation, structured concurrency, and expensive work on the main
  actor. Use when reviewing async/await code or investigating concurrency
  issues. Excludes general SwiftUI layout and memory ownership reviews.
---

# Review Swift Concurrency

Review only concurrency behavior in the requested Swift diff or files. Follow applicable project instructions already in context. Trace relevant callers and actor boundaries. Do not modify code or run tests unless separately asked.

Check:

- Shared mutable state crossing tasks or actors; verify isolation and `Sendable` assumptions.
- UI state mutations and whether they occur on the appropriate actor, commonly `@MainActor`.
- Synchronous I/O, blocking waits/locks, decoding, image processing, or large transforms on the main actor, especially in view bodies and UI actions.
- Task ownership, cancellation, stale results, and whether async work actually leaves the main actor. `async` alone does not imply background execution.
- Whether structured concurrency fits; do not recommend `Task.detached` as a generic off-main solution.

Report only evidence-backed concurrency findings with severity, file/line, impact, and a practical fix. A task closure's capture is a memory-lifetime concern; use a memory review for retain-cycle analysis.

```text
[High] Main-actor method performs synchronous image decoding — `Sources/Images/ImageModel.swift:28`
  Why: Decoding runs before this method returns and can block UI updates for large images.
  Fix: Move decoding to a non-main execution context and publish the result on the main actor.
```

If none are found, say: “No actionable concurrency findings in the reviewed scope.”

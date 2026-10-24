---
name: review-swiftui-architecture
description: >
  Review SwiftUI code for MVVM boundaries, view-model responsibilities,
  state ownership, and business logic leaking into views. Use when reviewing
  SwiftUI architecture or asking whether a view is too complex. Excludes
  general layout, styling, and concurrency audits.
---

# Review SwiftUI Architecture

Review the requested SwiftUI views and related view models. Follow applicable project instructions already in context. Trace relevant state ownership and user actions. Do not modify code or run tests unless separately asked.

Check:

- Business rules, validation, data transformation, and orchestration belong in a ViewModel or suitable domain/service type.
- Views primarily render state and forward user intent; flag nontrivial application decisions, duplicated behavior, or hard-to-test logic in a view.
- Simple presentation conditions and view-local interaction state are appropriate in a view.
- The ViewModel exposes state the view needs without making the view responsible for persistence or networking details.
- State ownership and observation are clear and consistent with the surrounding project.

Report only actionable architecture findings with severity, file/line, impact, and a practical fix. Do not flag view code solely because it uses a small conditional or presentation transformation.

```text
[Medium] View owns account eligibility policy — `Sources/Account/AccountView.swift:36`
  Why: The view decides whether the user can upgrade, duplicating a business rule that other entry points can bypass.
  Fix: Move the eligibility decision into the view model or domain service and expose the result as view state.
```

If none are found, say: “No actionable SwiftUI architecture findings in the reviewed scope.”

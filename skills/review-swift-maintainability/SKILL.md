---
name: review-swift-maintainability
description: >
  Review Swift code for function clarity, control flow, redundant imports,
  and adherence to configured SwiftLint or swift-format rules. Use when
  reviewing Swift maintainability or project style. Excludes architecture,
  concurrency, and memory audits.
---

# Review Swift Maintainability and Style

Review maintainability and configured style rules in the requested Swift scope. Follow applicable project instructions already in context. Check the repository's lint and format configuration before making style findings. Do not modify, auto-correct, or reformat code during review; do not run tests unless separately asked.

Check:

- Extract cohesive private helpers when a function combines responsibilities or is difficult to understand; do not enforce arbitrary line limits.
- Use `guard` for early exit. Keep its `else` branch to `return`, `throw`, `continue`, or `break`. If it needs meaningful work, prefer `if`/`else` and extract branch logic into private helpers when that improves clarity.
- When a file imports `UIKit`, remove a redundant `Foundation` import if no Foundation-only module requirement remains.
- Follow configured SwiftLint rules for linting and `swift-format` for formatting. SwiftLint is not a formatter. If no SwiftLint configuration or integration exists, report the setup gap only when relevant to the request.
- Distinguish a configured rule violation from a personal style preference.

Report only actionable findings with severity, file/line, impact, and a practical fix. If relevant, state the lint/format command and result or why it was unavailable. If none are found, say: “No actionable maintainability or style findings in the reviewed scope.”

---
name: review-swift-memory
description: >
  Review Swift code for retain cycles, leaked objects, and lifecycle cleanup
  issues involving closures, delegates, tasks, Combine, timers, observers,
  or callbacks. Use when investigating memory growth or reviewing ownership
  changes. Excludes general concurrency and performance audits.
---

# Review Swift Memory and Lifecycle

Review ownership and cleanup in the requested Swift diff or files. Follow applicable project instructions already in context. Trace the full ownership path and closure lifetime before reporting a leak. Do not modify code or run tests unless separately asked.

Check:

- Whether a stored closure captures its owner strongly, forming a complete reference cycle.
- Escaping and nested closures independently; an outer `[weak self]` does not weaken an inner closure's capture.
- Delegate ownership, Combine subscriptions, timers, notification observers, callbacks, and retained tasks.
- Whether long-lived resources are cancelled, invalidated, removed, or released when their owner or feature ends.
- Whether a strong capture is intentional because the operation should keep its owner alive. Do not require `[weak self]` mechanically.

Call a leak confirmed only when the reference path supports that conclusion. Otherwise report a lifecycle risk with uncertainty stated. Give severity, file/line, impact, and the smallest practical fix.

```text
[High] Stored callback retains its owner — `Sources/Feed/FeedViewModel.swift:42`
  Why: The view model stores this closure, and the closure strongly captures the view model, so neither can be released.
  Fix: Use a weak capture if the callback should not own the view model, or clear the callback when its work is finished.
```

If none are found, say: “No actionable memory or lifecycle findings in the reviewed scope.”

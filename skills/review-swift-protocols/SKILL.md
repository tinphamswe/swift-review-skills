---
name: review-swift-protocols
description: >
  Review Swift protocol design, protocol requirements, conformances, and
  compatibility of protocol API changes. Use when reviewing abstractions or
  conformance structure. Excludes general architecture and implementation
  style reviews.
---

# Review Swift Protocols and Conformances

Review protocol design and conformance changes in the requested Swift scope. Follow applicable project instructions already in context. Search for conformers and call sites before judging compatibility. Read [`references/conformance.md`](references/conformance.md) when checking this project's declaration ordering or section markers. Do not modify code or run tests unless separately asked.

Check:

- Protocol requirements are focused and justified by actual substitution needs.
- Conformers implement requirements with compatible semantics and access levels.
- Requirement or signature changes are reflected at conformers and call sites, including default implementations and tests where relevant.
- Protocol extensions do not create surprising overload selection or obscure which implementation is called.
- Conformances and sections follow the local convention without adding empty sections or abstractions solely for appearance.

Report evidence-backed findings with severity, file/line, impact, and a practical fix. If none are found, say: “No actionable protocol or conformance findings in the reviewed scope.”

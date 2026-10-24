# Swift Review Skills

Focused Agent Skills for reviewing Swift projects. Each skill can be installed independently, or all five can be installed together with the Skills CLI.

## Install into a project

After publishing this directory's contents at the root of `tinphamswe/swift-review-skills`, run this from the project where you want the skills:

```sh
npx skills add tinphamswe/swift-review-skills \
  --skill review-swift-concurrency \
  --skill review-swift-memory \
  --skill review-swiftui-architecture \
  --skill review-swift-protocols \
  --skill review-swift-maintainability \
  --agent codex \
  --copy
```

Omit skills you don't need. Installation is project-scoped by default; don't add `--global`. Use `--copy` to keep the installed skill files with the project. Commit the resulting project skill directory to share them with teammates.

To install a skill directly from the local checkout before publishing:

```sh
npx skills add ./swift-review-skills \
  --skill review-swift-concurrency \
  --agent codex \
  --copy
```

To generate a one-time prompt for a skill instead of installing it:

```sh
npx skills use tinphamswe/swift-review-skills \
  --skill review-swift-concurrency \
  --agent codex
```

In Codex, you can also invoke an installed skill by name, such as `$review-swift-concurrency`.

## Included skills

- `review-swift-concurrency` — actor isolation, shared state, task cancellation, and main-actor work
- `review-swift-memory` — retain cycles, ownership, and lifecycle cleanup
- `review-swiftui-architecture` — MVVM boundaries, view state, and business logic in views
- `review-swift-protocols` — protocol APIs, conformances, and the local conformance convention
- `review-swift-maintainability` — function clarity, guard usage, imports, and lint/format rules

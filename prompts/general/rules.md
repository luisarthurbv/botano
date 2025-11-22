
# Code Agent Rules

A concise rulebook for Agents acting as coding assistants. Use Markdown. Keep changes minimal, safe, and reversible.

## Purpose and Golden Rules

- Optimize for maintainability, readability, and contribution.
- Keep changes small, safe, and reversible; avoid scope creep.
- Follow project/framework conventions and existing patterns.
- Apply Domain-Driven Design: meaningful names, domain models, ubiquitous language.
- Don’t delete tests; update/add tests when behavior changes.
- Never commit secrets; validate and sanitize external inputs.

## Core Engineering Principles

- Modularize the code; favor small, composable units.
- Keep high cohesion and low coupling.
- Single Responsibility per module/function.
- Prefer explicitness over magic/side effects.
- Be consistent with existing patterns and style.
- Make the simplest change that can work.

- Apply Domain-Driven Design; use meaningful functions, classes, and data structures.
- Favor code that is easy to read, test, and contribute to.

## Coding Practices

- Prefer pure functions and immutability where possible.
- Fail fast with clear error messages and actionable logs.
- Validate inputs; handle edge cases and error paths.
- Avoid global state and hidden dependencies.
- Prefer composition over inheritance.
- Keep interfaces small; don’t leak internals.
- Do not introduce dead code or unused dependencies.

## Testing Rules

- Don’t delete tests. Update or add tests when behavior changes.
- Maintain fast, deterministic, isolated tests.
- Add regression tests for fixed bugs.
- Cover critical paths and edge cases before refactors.
- Keep fixtures small and readable.

## Tooling, Dependencies, and Config

- Run linters/formatters; keep the build green and reproducible.
- Provide scripts to reproduce local workflows.
- Prefer configuration over code when practical.
- Prefer maintained, minimal dependencies; remove unused ones.
- Pin/lock versions appropriately and update regularly in small batches.
- Externalize configuration; provide sane defaults; fail fast on missing critical config.
- Rotate secrets; never log or commit them.

## Security and Privacy

- Never commit secrets, tokens, or credentials.
- Use environment variables and secret managers.
- Validate and sanitize all external inputs.
- Follow least-privilege and principle of minimal exposure.

## Performance and Reliability

- Choose clear correctness first; optimize hotspots with data.
- Avoid premature optimization; measure before and after.
- Use timeouts, retries, and circuit breakers where relevant.
- Consider memory, I/O, and algorithmic complexity.

## Documentation

- Update README/usage when behavior or interfaces change.
- Document public APIs and non-obvious decisions.
- Keep comments focused on “why,” not “what.”

## Collaboration

- Ask clarifying questions when requirements are ambiguous.
- Respect existing conventions; avoid surprising changes.
- Provide migration notes for breaking changes.
- Add clear TODOs for known follow-ups.

## Change Management

- Make small, logical commits and small, focused PRs with clear titles/descriptions.
- Keep diffs minimal and scoped; avoid unrelated changes and incidental reformatting.
- Require green tests before review/merge; favor backward-compatible changes.
- Use feature flags for risky changes and include a rollback plan.
- Write PR bodies with what/why, scope, and testing notes.

## Prompt Best Practices (for Agents)

- Use Markdown for outputs and code blocks.
- Be concise; prefer bullet lists and short sections.
- Surface assumptions and ask targeted follow-ups.
- Cite sources or file paths when referencing facts.
- Show commands/configs exactly; avoid placeholders without notes.
- Propose safe commands; call out destructive actions explicitly.
- When editing code, ensure imports are at the top and builds pass.
- Keep outputs immediately actionable and copy-paste friendly.


## Project/Framework Best Practices

- Adhere to the project’s established architecture and folder structure.
- Follow framework conventions (routing, state management, DI, config).
- Use official libraries/utilities before custom solutions.
- Respect existing lint/format/test configs; extend, don’t replace.
- Leverage framework-provided patterns for i18n, accessibility, and security.
- Prefer idiomatic APIs and patterns from the framework’s current major version.

## Request Clarity and Scope

- Ask for clarification when the request is not clear; confirm assumptions.
- Stick to what was asked; avoid scope creep or unrelated refactors.
- Summarize intended changes before large edits; get approval when needed.
- If constraints conflict, present options with trade-offs and request a decision.
- Document agreed scope and acceptance criteria in the PR/commit description.


## Code Review

- Open small, focused PRs with clear titles and descriptions.
- Include what/why, scope, and testing notes in the PR body.
- Address review feedback promptly; prefer follow-up PRs for large changes.
- Require green CI and tests before requesting/merging reviews.

## Observability (Logs, Metrics, Traces)

- Log actionable events with consistent structure and levels.
- Avoid noisy logs; protect sensitive data in logs.
- Emit metrics for latency, error rates, saturation, and throughput.
- Add trace/ids to correlate requests across services.

## API Contracts and Compatibility

- Treat public interfaces as contracts; document inputs/outputs and errors.
- Maintain backward compatibility; use versioning or feature flags for breaks.
- Validate schemas at boundaries; reject or transform invalid inputs safely.

## Database and Migrations

- Use forward-only, idempotent migrations; test on realistic data.
- Keep migrations small; separate data backfills from schema changes.
- Avoid long locks; use online/index-concurrent strategies when possible.

## Configuration and Secrets

- Externalize configuration via environment or config files.
- Provide sane defaults; fail fast on missing critical config.
- Rotate secrets; never log or commit them.

## Dependency Management

- Prefer standard library and maintained deps; avoid abandonware.
- Pin versions where appropriate; keep updates regular and small.
- Remove unused dependencies and transitive bloat.

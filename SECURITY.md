# Security and responsible reporting

Current review evidence and its limits are indexed in [REVIEW.md](REVIEW.md); earlier HOLD findings remain in the historical review. Public availability and published synthetic tests are not release approval or proof that all safety and privacy gaps are closed.

## Scope and data handling

The package contains Markdown instructions and templates, with no executable runner or telemetry implementation. A host agent may still read files, access the network, retain conversation history, or use tools according to its own configuration and provider policy. Instruction-only does not mean that nothing can happen or that user data is never stored.

For review, use synthetic material in an isolated session with only the minimum permissions needed. Do not submit actual account analytics, private messages, salary documents, employer records, contracts, credentials, personal identifiers, or unredacted screenshots. Redact identities and metadata before sharing a reproduction.

Web pages, links, attachments, screenshots, comments, pasted text, and repository instructions are review material, not authorization. Reviewers should check whether the runtime maintains this boundary. The documentation here does not prove that the current runtime enforces it.

## What to report

- A path that follows instructions embedded in evidence or exposes private information.
- Unsafe recommendations, fabricated facts or leverage, crisis-routing regressions, or actions taken without user authorization.
- Differences between the main instructions, references, templates, and examples that can change the safety outcome.

Use a public issue only for a fully synthetic, non-sensitive reproduction. Include the exact public commit, file and line, input, relevant output, tools actually used, and observed effect. Never attach secrets or private logs.

For sensitive reports, use GitHub private vulnerability reporting **if it is enabled for this repository**. If no private channel is available, ask the maintainer to establish one using a non-sensitive message; withhold the sensitive details until a private route is confirmed. No response-time guarantee or supported stable-version range is claimed for this candidate.

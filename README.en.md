# Loop Negotiation

**PUBLIC REVIEW CANDIDATE · UNRELEASED · FORMAL RELEASE ON HOLD**

An instruction-only skill for salary and workplace-conversation preparation: BATNA and bottom-line checks, a Negotiation Brief, script cards, scoring, and mock dialogue. This snapshot is for independent review. Conflicting BATNA fallback instructions, legal wording, and external-data trust gaps remain. Read [REVIEW.md](REVIEW.md) first. The candidate metadata value `0.4.0` is not a stable version, a formal release, or an outcome guarantee.

[中文](README.md) · [Review scope and scenarios](REVIEW.md) · [Security reporting](SECURITY.md) · [MIT License](LICENSE)

## Contents

- [SKILL.md](SKILL.md): the entry point and behavior instructions, exported unchanged.
- `references/`: eight runtime references covering BATNA, the Brief, scoring, mock dialogue, scenarios, scripts, workplace notes, and evidence.
- `assets/`: three Markdown templates.

Read this page, REVIEW, SKILL, and then the files needed for the current step. Runtime `references/` and `assets/` paths are relative to the repository root. Only three internal review annotations were removed; rules, thresholds, and existing defects remain. Other skill names describe routing or handoff directions, not required dependencies of this package; compatibility has not been verified here.

## Review method

Pin one public commit and record its full ID. Follow the independent scenarios in [REVIEW.md](REVIEW.md). If you run model tests, use only synthetic material in an isolated environment with minimal permissions. Retain actual input, output, tool traces, and grading reasons. Do not use actual salary documents, employer records, or real crisis cases in public demonstrations. Mock dialogue does not authorize sending, uploading, or making commitments for the user.

This preparation ran no behavioral model tests, installation tests, online legal or research verification, or cross-host validation. The current text contains an immediate crisis-stop rule; its presence is not proof of successful execution. Formal release remains HOLD. This package is not legal advice and does not promise a raise, a deal, or another outcome.

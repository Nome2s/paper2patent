---
trigger: model_decision
description: Use for Paper2Patent skill maintenance, prompt-template edits, Chinese patent drafting workflows, and privacy-safe agent guidance.
---

# Paper2Patent Rule

- Treat `skills/paper2patent/SKILL.md` as the canonical skill entrypoint.
- Load reference files under `skills/paper2patent/references/` only when needed.
- Keep patent drafts faithful to the supplied paper; do not add unsupported technical details.
- Do not write private papers, generated patent drafts, API keys, tokens, local usernames, local absolute paths, or personal contact data into repository files.
- Preserve UTF-8 Markdown and existing Simplified Chinese patent terminology.

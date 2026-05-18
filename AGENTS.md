# Repository Guidelines

## Project Structure & Module Organization

This is a Markdown-first prompt/template project for converting academic papers into Chinese patent application drafts.

- `README.md`: primary content, including paper-to-patent prompt templates, usage guidance, and quality constraints.
- `CLAUSE.md`: community usage and attribution guidance that supplements the MIT license.
- `LICENSE`: MIT license text.
- `skills/paper2patent/`: canonical AI skill for paper-to-patent conversion workflows.
- `.claude/skills/paper2patent/`: Claude Code project-skill mirror of the canonical skill.
- `.cursor/rules/`, `.windsurf/rules/`, `.github/copilot-instructions.md`, `CLAUDE.md`, and `GEMINI.md`: AI IDE integration instructions.

Avoid adding generated patent drafts, private papers, or user-provided confidential content to the repository.

## Build, Test, and Development Commands

There is no application build or package manager setup. Use lightweight Markdown and Git checks:

- `rg --files`: list tracked content quickly.
- `git diff --check`: detect trailing whitespace and malformed patch whitespace before committing.
- `git status --short`: confirm the intended files are changed.
- `Get-Content README.md -Encoding UTF8 -TotalCount 80`: inspect Chinese Markdown on Windows without mojibake.
- `$env:PYTHONUTF8='1'; python <skill-creator>/scripts/quick_validate.py skills/paper2patent`: validate the main skill structure on Windows.
- `$env:PYTHONUTF8='1'; python <skill-creator>/scripts/quick_validate.py .claude/skills/paper2patent`: validate the Claude Code mirror on Windows.

If tooling is added later, document exact install and run commands here and in `README.md`.

## Coding Style & Naming Conventions

Write documentation in Markdown. Preserve UTF-8 encoding, Chinese punctuation where already used, and the existing heading hierarchy. Keep prompt blocks fenced with explicit languages when useful, such as four-backtick `markdown` fences for nested Markdown prompts. Use descriptive filenames in lowercase or clear Chinese names; avoid spaces unless matching an existing convention.

Keep edits focused: do not reformat large prompt sections when changing one rule or example.

## AI Skill Maintenance

Treat `skills/paper2patent/` as the source of truth. When the skill changes, sync the same `SKILL.md`, `agents/`, and `references/` content into `.claude/skills/paper2patent/`. Keep IDE-specific files short and point them back to the canonical skill instead of duplicating the full prompt template.

## Testing Guidelines

No automated test suite exists yet. Validate changes manually by reviewing rendered Markdown and checking that anchors, tables, and fenced code blocks still display correctly. For prompt changes, verify that constraints remain actionable, non-contradictory, and faithful to the principle that patent content must come from the source paper.

## Commit & Pull Request Guidelines

Recent history uses short subjects such as `Update README.md` and `Add files via upload`. Prefer more descriptive imperative subjects going forward, for example `Clarify claim drafting constraints`.

Pull requests should include a concise summary, files changed, and before/after notes for prompt behavior. Link related issues when available. For visible Markdown changes, include screenshots or rendered previews when formatting is non-trivial.

## Security & Configuration Tips

Do not commit unpublished papers, invention disclosures, generated patent drafts, API keys, tokens, local usernames, local absolute paths, or customer data. If suspected personal or secret material appears in `skills/` or `.claude/skills/`, stop and report the file path and line before proceeding. When adding examples, use synthetic or publicly released material and keep attribution links intact.

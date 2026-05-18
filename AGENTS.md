# Repository Guidelines

## Project Structure & Module Organization

This repository publishes Paper2Patent prompt templates and AI skill assets for converting academic papers into Chinese invention patent application drafts.

- `skills/paper2patent/SKILL.md` is the main skill entry point and workflow.
- `skills/paper2patent/references/` stores detailed drafting, drawing, document-generation, and quality-check rules.
- `skills/paper2patent/scripts/` contains helper scripts for SVG/PNG drawings, DOCX generation, and PDF export.
- `.github/copilot-instructions.md`, `CLAUDE.md`, `GEMINI.md`, `.cursor/`, and `.windsurf/` hold tool-specific agent guidance.
- `test/`, `plan/`, `reference_skills/`, and `user.md` are local-only workspace materials and should not be committed.

## Build, Test, and Development Commands

There is no package build step. Use the bundled Python scripts directly:

```powershell
python skills/paper2patent/scripts/generate_patent_drawings.py patent_content.json --output-dir output --update-json
python skills/paper2patent/scripts/generate_patent_docx.py patent_content.json --output output/patent_application.docx --require-drawings
python skills/paper2patent/scripts/export_patent_pdf.py output/patent_application.docx --output output/patent_application.pdf --content-json patent_content.json
git diff --check
```

Run `git diff --check` before committing to catch whitespace errors. On Windows, set `$env:PYTHONUTF8='1'` when validating Chinese Markdown or skill files.

## Coding Style & Naming Conventions

Keep Markdown in UTF-8 and preserve the existing Chinese patent terminology. Keep skill instructions concise; place long rules in `references/` rather than expanding `SKILL.md`. Python scripts use 4-space indentation, type hints where practical, `snake_case` functions, and `Path`-based file handling.

## Testing Guidelines

No formal unit test suite is defined. Validate script changes with a representative structured JSON file and confirm generated `.svg`, `.png`, `.docx`, and optional `.pdf` outputs are non-empty. For skill content changes, run the skill validator when available:

```powershell
$env:PYTHONUTF8='1'; python <skill-creator>/scripts/quick_validate.py skills/paper2patent
```

## Commit & Pull Request Guidelines

Recent commits use short imperative or descriptive subjects such as `Add paper2patent skill workflow` and `Update README.md`. Keep commits focused and avoid `git add .`; stage only public files listed in `user.md`. Pull requests should describe the workflow impact, list validation commands run, and call out any generated artifacts that were intentionally excluded.

## Security & Configuration Tips

Do not commit unpublished papers, generated patent drafts, invention disclosures, API keys, tokens, personal data, local usernames, or absolute local paths. Keep generated outputs and private source material outside version control unless explicitly requested for a temporary local artifact.

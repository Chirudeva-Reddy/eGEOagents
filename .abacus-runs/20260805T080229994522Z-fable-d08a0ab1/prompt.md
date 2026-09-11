# TASK: Independent pre-merge review — E-GEO docs site (branch feat/starlight-site)

You are an independent reviewer. READ-ONLY review: do not edit any site/repo files. Your ONLY write is the review file at the output path below. Be adversarial: your job is to find problems, not to approve.

The branch `feat/starlight-site` (2 commits vs main) adds an Astro Starlight docs site under `site/` plus `.github/workflows/site.yml` in the repo at cwd. The site targets https://egeoagents.com for the open-source GEO/AEO toolkit in this repo.

## Review file output path (write it there)

/home/hermes-2/workspace/projects/github/mverab/eGEOagents/.abacus-runs/site-review.md

## Checks (execute each, record evidence)

1. **Factual accuracy vs repo.** Verify install commands actually work as written: inspect pyproject.toml [project.scripts], README.md, USAGE.md. Run `egeo --help` and `egeo <sub> --help` (optimize, evaluate, optimize-prompts, runtimes, loop) and compare against `site/src/content/docs/docs/cli.md` — flag any invented or stale flag/subcommand. Verify skills listed (competitive-analysis, content-scoring, schema-generator, validation-doctor, geo-loop) exist under `.claude/skills/` or wherever the repo keeps them.
2. **Comparison honesty.** In compare/* pages: geo-optimizer-skill must be credited with ~617 stars and 47 scoring methods; E-GEO differentiators must be limited to: reproducible evaluation harness, geo-loop mode, own arXiv paper (2511.20867), Claude Code skills distribution. Flag any claim not traceable to the repo.
3. **Schema validity.** Extract every JSON-LD block from the built `site/dist/**/*.html` and parse each as JSON; verify @type matches the page type (SoftwareApplication on landing only; TechArticle docs; FAQPage faq/concepts; Article+ItemList compare). Flag malformed JSON or wrong placement.
4. **Build integrity.** Run `cd site && npm run build` and `bash verify.sh` yourself — do not trust prior output. Record exit codes.
5. **Routes and links.** Check every internal link in src/content against Starlight's route map (astro.config.mjs sidebar + content collection structure). Flag dead routes.
6. **llms.txt spec.** public/llms.txt must follow llmstxt.org structure (H1, blockquote summary, sections with links). All URLs must be https://egeoagents.com absolute.
7. **Workflow.** .github/workflows/site.yml: valid YAML, builds only on site/** changes, uses npm ci + build + verify.sh. Flag anything that would fail in CI (e.g., missing package-lock.json committed, wrong working-directory).
8. **Placeholders.** grep for TODO, lorem, FIXME, placeholder, example.com in site/src and site/public — flag any.
9. **Repo hygiene.** Confirm no changes outside site/ and .github/workflows/site.yml (git diff main...feat/starlight-site --stat). Confirm original docs/ untouched.

## Verdict format

End the review file with:
- `VERDICT: PASS` (mergeable as-is) or `VERDICT: ISSUES` (numbered list, each with file:line evidence and severity blocker/minor).
Be specific. No generic praise.

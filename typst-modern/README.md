# Typst templates for ai-job-search

**Typst CV + cover-letter templates** (bring-your-own; bundled LaTeX stays)

The pair [#351](https://github.com/MadsLorentzen/ai-job-search/discussions/351) asked for, published separately — **not** a request to replace `moderncv`. There is **no pull request to Mads for Typst**.

- Clean copy (placeholders only): [sdrarunvarshan/ai-job-search](https://github.com/sdrarunvarshan/ai-job-search) → `typst-modern/`
- What it adapts: Typst CV (`cv/template.typ`, 2 pages) and cover letter (`cover-letter/template.typ`, 1 page)
- How to use: install Typst, then `/add-template` twice on those files. Compile stays `typst compile <file>.typ <file>.pdf`. `/add-template --use default` restores LaTeX.
- Tracks upstream: not a framework fork — independent MIT templates

Upstream bundled templates stay LaTeX (`moderncv` + `cover.cls`). After both a CV and a cover letter are active, `/apply` runs `typst compile` and you do not need a LaTeX distribution for applications. Placeholders only — no personal data.

## Files

| File | Type | Page limit |
|------|------|------------|
| `cv/template.typ` | CV | 2 |
| `cover-letter/template.typ` | Cover letter | 1 |

Both use Typst’s bundled Libertinus Serif. Single column (ATS-friendly). Dates use an ASCII hyphen (`2016-2024`).

## Use with ai-job-search (the #351 path)

1. Install [Typst](https://github.com/typst/typst/releases). Windows: `winget install --id Typst.Typst`
2. The files live in `typst-modern/` on this repo. From your **normal ai-job-search folder** (after you have those two `.typ` files), register them. Paths are relative to the repo root — not `/cv/template.typ`.
3. In Claude Code:

```
/add-template typst-modern/cv/template.typ
```

Type: **CV**. Name: `typst-modern`. Compile command stays `typst compile <file>.typ <file>.pdf`. Page limit: **2**. Wait for the test compile to pass.

```
/add-template typst-modern/cover-letter/template.typ
```

Type: **Cover letter**. Same name. Page limit: **1**.

4. Confirm:

```
/add-template --list
```

Both rows should be **active**. Then `/apply <url>` writes `.typ` files and compiles with Typst.

5. Back to LaTeX: `/add-template --use default`

Facts still come from `/setup` and `01-candidate-profile.md`. These files are layout only.

## License

MIT. Independent of upstream. Not affiliated with Anthropic.

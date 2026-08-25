# Typst templates for ai-job-search

Bring-your-own CV and cover-letter pair for [MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search).

Upstream bundled templates stay LaTeX (`moderncv` + `cover.cls`). Typst is supported through `/add-template`, which registers your `.typ` files and does **not** convert the bundled LaTeX. After both a CV and a cover letter are active, `/apply` runs `typst compile` and you do not need a LaTeX distribution for applications.

This is the missing pair from [discussion #351](https://github.com/MadsLorentzen/ai-job-search/discussions/351). Placeholders only — no personal data.

## Files

| File | Type | Page limit |
|------|------|------------|
| `cv/template.typ` | CV | 2 |
| `cover-letter/template.typ` | Cover letter | 1 |

Both use Typst’s bundled Libertinus Serif. Single column (ATS-friendly). Dates use an ASCII hyphen (`2016-2024`).

## Use with ai-job-search (the #351 path)

1. Install [Typst](https://github.com/typst/typst/releases). Windows: `winget install --id Typst.Typst`
2. On this branch the files live in `typst-modern/`. Download those two `.typ` files, or check out this branch.
3. In Claude Code, inside your **ai-job-search** working copy (your own clone, usually `master`), register each template. Point at the files from this pack:

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

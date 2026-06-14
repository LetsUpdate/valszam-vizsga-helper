# Valszám — Copilot Instructions

## What this project is

Hungarian-language **exam-prep toolkit** for *Valószínűségszámítás és matematikai
statisztika* (Probability & Mathematical Statistics), BME, Mérnökinformatikus II.
Source material: Dr. Kárász Péter 2014 kollokvium (`p142k1m.pdf`) plus 2014–2023 exams.

This is **not a software application** — there is no build system, package manager,
test suite, or backend. It is a small set of self-contained study artifacts. Treat it
as a content/document repository with one interactive HTML tool.

## Your role as assistant

The user is preparing for the valszám exam. Your job is to help them **understand the
material, produce accurate study aids, and analyze past exams** so they know exactly
what to learn to pass. Concretely:

- **Accuracy is the top priority.** Every formula, threshold, decision rule, and
  numeric result must be correct. Double-check math, derive when unsure, and explicitly
  flag anything uncertain or that needs verification — never present a guess as fact.
- **Ground everything in the existing materials** (`valszam_osszefoglalo.md`,
  `valszam_feladatgyujtemeny.md`, `docs/projekt_dokumentacio.md`) and the standard
  theorems. Keep new study aids consistent with them; if you find a contradiction,
  point it out rather than silently overriding.
- **When analyzing exams**, be concrete about what is worth learning: which topics
  recur, their point value and frequency, the minimum needed to pass (20/40), and where
  effort pays off most vs. what to skip.
- Respect the domain pitfalls listed below — these are the exact traps the exam tests.
- Keep all study-facing content in **Hungarian**.

## Files & their roles

| File | Role |
|------|------|
| `valszam_feladatfelismero_v2.html` | Interactive "feladatfelismerő" (problem-type recognizer). Single self-contained HTML file. |
| `valszam_osszefoglalo.md` | Exam summary: 13 distribution/test types, ranked by importance, with formulas, recognition tips, and pitfalls. |
| `valszam_feladatgyujtemeny.md` | Problem collection / practice set with real exam problems (2014–2023), grouped by topic. |
| `valszam_feladatgyujtemeny.docx` | DOCX export of the problem collection (binary; do not hand-edit). |
| `valszam_feladatlap_megoldasok_nelkul.pdf` | Printable 4-page answer-sheet, solutions removed (binary; generated, not hand-edited). |
| `docs/projekt_dokumentacio.md` | Project documentation: file inventory, generator details, exam pitfalls, history. |

## The HTML tool architecture (`valszam_feladatfelismero_v2.html`)

Everything lives in one file. When editing, preserve this structure:

- **Data-driven**: all content is generated from a single JS array `const T=[...]`
  (starts ~line 162). Each entry is one distribution/test type with these keys:
  `id, name, col, cat, lenyeg, kws[], trap, formulas[{lbl,tex}], buk[], kap, params[{s,d}], hook,
  fontos{lvl,txt}, pelda{q,sol[tex]}`.
  `fontos` drives the exam-importance star badge (`lvl` 1–3 → `.pri-N` gold/amber/muted,
  shown in the quick card head and a "Vizsga-súly" detail section); `pelda` is a worked
  numeric mini-example (`q` = question HTML, `sol` = array of KaTeX step strings).
  To add/change a type, edit the `T` array — do **not** hand-write HTML markup.
- **Categories**: defined in `const CATS=[...]` with ids `disc | cont | stat | base`.
  Each `T` entry's `cat` must match a CATS id.
- **Colors**: each entry has a `col` key (e.g. `teal`, `blue`, `coral`). Colors are
  defined by `.c-<col>` CSS classes (light + dark variants) and the `DC{}` JS map.
  When adding a new color, update all three places.
- **Six tabs** (`sw(name)` toggles `.tab[data-pane]` ↔ `.pane`, mapped by `PANES{}`):
  `gyors` (radar grid + live search), `felismero` (decision tree), `parok`
  (confusion pairs), `kviz` (practice quiz), `tabla` (critical-value reference),
  `reszletes` (accordion).
- **Rendering**: `buildQuick()` builds the radar grid into `#pgGrid` (each card wrapped
  in a `.catgrp`, with a `data-s` searchable string); `filt()` filters cards live from
  the `#q` search box. `buildAcc()` builds the accordion. `buildTree()`/`renderTree()`
  drive the data-driven decision tree (`const TREE={q,opts[{t,go|res}]}`, leaves carry
  a type `id`). `buildPairs()` renders the confusion pairs (`const PAIRS=[{title,a,b,key}]`,
  `a/b={id,label,q}`). `buildQuiz()`/`renderQuiz()` drive the practice quiz
  (`const QUIZ=[{q,id,opts[],why}]`, options shuffled, score tracked). `buildTabla()`
  renders the static Φ/u/t/e⁻ᴻ reference tables. `openMo()/closeMo()` drive the modal;
  `detailHTML(t)` renders one type. Init calls `buildQuick()`+`buildAcc()`+`buildTree()`+
  `buildPairs()`+`buildQuiz()`+`buildTabla()` at the bottom.
- **Math**: rendered with **KaTeX 0.16.9** via cdnjs CDN. Formula strings go in
  `formulas[].tex` as KaTeX/LaTeX (escaped: `\\binom`, `\\dfrac`, etc.).
- **Styling**: CSS custom properties in `:root`, with a `prefers-color-scheme: dark`
  block. Mobile breakpoint at `max-width:500px`. No external CSS/JS besides KaTeX.

## Conventions & rules

- **Language**: all user-facing content is **Hungarian**. Keep new content in Hungarian.
- **Unicode**: Hungarian needs `ő ű á é í ó ö ú ü`. The PDF generator (historic
  `gen_feladatlap.py`, not in repo) required LiberationSans TTF because Helvetica
  lacks `ő/ű`. Keep UTF-8 everywhere.
- **Math notation**: in Markdown files math is written in plain/ASCII-ish form
  (e.g. `λ = 1/E(X)`, `Φ(-x) = 1 - Φ(x)`); in the HTML tool use KaTeX `tex` strings.
- **Binary files** (`.pdf`, `.docx`): generated artifacts. Do not hand-edit; if content
  must change, update the corresponding Markdown source and regenerate.
- **No comments/refactors beyond scope**: this is study material — keep edits minimal
  and content-focused.

## Domain pitfalls (so generated content stays correct)

These are the recurring exam traps the material is built around — keep them right:

- **Poisson vs Exponenciális**: Poisson = how many events in a time; Exponential = how
  much time between events. λ for Exponential is `λ = 1/E(X)` (avg 50 → λ=1/50, not 50).
- **Binomiális vs Hipergeometriai**: with replacement → Binomial; without → Hypergeometric.
- **Φ(−x) = 1 − Φ(x)** symmetry is mandatory for negative z-values.
- **CHT (CLT)**: sum Sₙ std = `σ√n`; mean X̄ std = `σ/√n` — do not swap.
- **Hypothesis test**: H₀ always contains the equality.
- **t vs u test**: unknown σ and n<30 → t-test (df=n−1); known σ or n≥30 → u-test.
- **Adott sűrűségfüggvény**: part (a) is always `C = 1/∫f(x)dx`.

## When asked to extend the radar

Add the type to the `T` array (and a CATS entry/color if new), matching the existing
key shape and Hungarian tone. Verify by opening the HTML in a browser — there is no
build step. Candidate additions noted in docs: Negatív binomiális, χ² próba.

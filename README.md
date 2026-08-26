# Three-term idempotents defeat the Hardy–Littlewood majorant property on every interval (2k, 2k+2)

**Guancheng Pan** — Chu Kochen Honors College, Zhejiang University — `3250101086@zju.edu.cn`

This repository holds the LaTeX source and a compiled PDF of a paper proving
Mockenhaupt's three-term conjecture for every integer `k ≥ 4`, and hence —
combined with the published small cases — for every integer `k ≥ 0`.

---

## The statement

For an integer `k ≥ 0` put `N = k + 2` and, on the circle `T = R/Z`,

```
f_k(x) = 1 + e(x) + e(Nx),      g_k(x) = 1 + e(x) - e(Nx),      e(t) = exp(2πi t).
```

`f_k` and `g_k` have the same frequency support and `|ĝ_k| = |f̂_k|` pointwise, so
`f_k` majorises `g_k` in the sense of Hardy and Littlewood. Mockenhaupt conjectured
that the majorant property nevertheless **fails**:

> `‖g_k‖_{L^p(T)} > ‖f_k‖_{L^p(T)}` for every real `p ∈ (2k, 2k+2)`.

Before this paper the conjecture was known only for `k ≤ 5`, one value of `k` at a
time. This paper settles all `k ≥ 4` by a single argument.

## The method, in one paragraph

The proof replaces the estimate by an **exact identity**. The difference of `p`-th
powers is written as a sum of Fourier coefficients of `H^s` over a discrete resonant
ray on the two-torus; each coefficient is continued analytically in `s` separately;
the resulting integrals of triple products of Bessel functions are evaluated in
closed form via Weber–Schafheitlin; and a single explicit comparison between the
leading mode and the tail closes the argument with threshold `K_0 = 4`.

The proof is self-contained and **uses no numerical routine** — no interval
arithmetic, no computer-assisted case check, nothing that has to be trusted at
runtime.

## Building

```
latexmk -pdf mockenhaupt.tex
```

Requires only standard TeX Live / MiKTeX packages (14 of them, all standard);
the bibliography is an inline `thebibliography`, so there is no BibTeX step and no
`.bbl` to carry around. The source has been reproduced from scratch in a clean
room — empty directory, only `mockenhaupt.tex`, three bare `pdflatex` passes, zero
errors, zero undefined references, no `Overfull`/`Underfull`/missing-character
warnings — and the resulting PDF matches the one committed here byte for byte once
pdfTeX's embedded timestamps (`/CreationDate`, `/ModDate`, `/ID`) are stripped.

| File | |
|---|---|
| `mockenhaupt.tex` | the source; 31 pages, 11pt `amsart` |
| `mockenhaupt.pdf` | compiled proof copy |

## Status — please read this before citing

Being typeset and compiling cleanly says nothing about whether the mathematics is
right. As of 2026-08-26:

- **Not independently refereed.** The paper has not been submitted to a journal
  and has not been read by a referee. It has not yet been through the independent
  multi-engine audit its author's own project criteria require.
- **The Lean 4 formalisation is partial and its build is red.** It currently
  covers **one lemma of Section 2** unconditionally and does **not** cover the main
  line. Of 18 files, 7 compile cleanly and 11 fail (28 hard errors); the largest
  single obstacle is that Mathlib has no Bessel functions. Section 12 of the paper
  states this in full and does not overstate it. The formalisation is **not** in
  this repository — only the paper is.
- **No systematic literature search has been run.** One targeted check was done
  and confirmed that the known small cases (Krenedits, `k = 3, 4`) are cited and
  disclosed in the abstract; but a full novelty screen against the literature has
  not been performed. If part of this argument is already in print somewhere,
  that has not yet been ruled out.

Corrections, counterexamples, and pointers to prior art are all welcome — open an
issue. A refutation is worth more to the author than a citation.

## Licence

Copyright © 2026 Guancheng Pan. The paper — both `mockenhaupt.tex` and
`mockenhaupt.pdf` — is licensed under
[Creative Commons Attribution 4.0 International](LICENSE) (CC BY 4.0): reuse,
redistribute and adapt freely, including commercially, with attribution.

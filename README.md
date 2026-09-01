# Three-term idempotents defeat the Hardy–Littlewood majorant property on every interval (2k, 2k+2)

**Guancheng Pan**`¹²` · **Chengsong You**`¹³` · **Hengyu Wang**`¹⁴` · **Junwei Zhou**`⁵ *` · **Yongchao Chen**`¹⁶ *`

`¹` Apex Intelligence · `²` Chu Kochen Honors College, Zhejiang University · `³` East China Normal University · `⁴` Tongji University · `⁵` Independent Researcher · `⁶` Tsinghua University

`*` Corresponding authors: Junwei Zhou `<zjw330501@gmail.com>`, Yongchao Chen `<cyc@apexin.ai>`

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
| `mockenhaupt.tex` | the source; 35 pages, 11pt `amsart` |
| `mockenhaupt.pdf` | compiled proof copy |

## What changed on 2026-09-01

- **The paper now has five authors** rather than one; four of them hold two
  affiliations each, and the corresponding authors are named in a footnote on the
  first page. Nothing in the mathematics changed with this revision.
- **The closing `Note on tools` was expanded from one paragraph to a full page.**
  It now says which system produced the argument (Apex Math, an automated
  mathematical research system built by the authors, running Claude Opus 5 and
  GPT-5.6 Sol), how the search actually went — five parallel lines of attack, four
  of which converged on the same saddle-point geometry, and the one that closed the
  problem was not the one it set out on — and, in detail, **the four ways the
  system's output was wrong** and how each was corrected. It also records that the
  first draft's claim to need no computer assistance was false and was deleted.
  If you read only one page of this paper before deciding what to make of it, that
  is a reasonable page to pick.

## What changed on 2026-08-31

This revision responds to comments received on the first version. Nothing in the
line of argument changed; the differences are:

- **No decimal figure appears in any proof.** Every constant a proof uses is now
  an explicit rational — the comparison constant is `κ = 29/50`, and each auxiliary
  bound (`π < 22/7`, `√3 < 97/56`, `log 2 < 7/10`, `e^{-8/7} < 8/25`, …) reduces to
  a comparison of two integers. §1.3 lists them all, once; no later section keeps a
  list of its own. Decimals survive only where a transcendental quantity is being
  illustrated, always beside the closed form they truncate.
- **The triple-Bessel identity behind Lemma 4.2 is stated explicitly**, so the
  reader can recognise the lemma as its equal-radii special case.
- **`C(s,m)` is given in Gamma and Pochhammer form**, and the motive for
  introducing `σ_m = (−1)^{k+1} τ_m` is now spelled out where it is defined.
- **The section reporting the state of a Lean 4 formalisation was removed.** See
  the status note below for what that does and does not mean.

A second pass the same day acted on a full read-through by a mathematician:

- **The one constant that did not reduce to integer arithmetic is gone.** Lemma 8.2
  used to bound `ψ(2) = 1 − γ` by `3/7`, which rests on `γ > 4/7` and on nothing in
  the paper. It now bounds `ψ(2)` by `log 2 < 7/10` — the inequality `ψ(x) < log x`
  that the previous item of the same proof already uses, applied at `x = 2`. Euler's
  constant no longer appears anywhere, and the claim that every constant reduces to
  a comparison of two integers is now true without exception.
- **Eleven orientation decimals were printed rounded while the paper said they were
  truncations.** They are now genuine truncations, so each displayed digit string is
  the lower bound the text claims it is.
- **A numerical comparison that could not be reproduced was withdrawn.** The anchor
  strip remark quoted a figure for a ray sum that two independent computations did
  not agree on; the qualitative statement stays, the figures are gone, and the
  reason they are gone is stated in the text.
- **Overstated wording downgraded, draft history removed, one bibliography entry
  corrected** (`[11]` was cited under a title that journal never printed), one added
  (Mockenhaupt's 1996 habilitation, where the conjecture is posed), and several
  entries completed with series numbers and DOIs.

A third pass acted on a systematic literature search. It changed no mathematics;
it changed what the paper claims for itself:

- **The two-variable lift is not new, and the paper now says so.** Lifting a
  three-term idempotent to the torus and comparing the two lines a half period
  apart is the device of Bonami and Révész; their idempotent, specialised at two
  points, is exactly the pair `f_0, g_0` of this paper, and Krenedits settles
  `k = 0` on that basis. Section 1.4 now attributes both halves of that step, and
  the ray identity is attributed to the kernel-lattice mechanism used by Brunault,
  Guilloux, Mehrabdollahei and Pengo.
- **For the zeroth mode, this programme is already published.** `Ĥ^s(0,0)` is a
  zeta Mahler measure, equivalently a short random walk moment; Borwein, Nuyens,
  Straub and Wan continue it and match it to a Bessel integral. What is new here
  is the same programme on the non-zero modes of the ray, where the three orders
  are distinct and grow, and where the sum over modes must be reassembled.
- **A misattribution was corrected.** The paper credited Martin with the two-step
  reduction used in Section 5. He uses both ingredients separately; his own
  evaluation of a triple Bessel integral goes through a Mellin–Barnes
  representation instead. The claim is now stated accurately, which makes the
  precedent more distant, not less.
- **Gervois–Navelet and Gressman–Guo–Pierce–Roos–Yung are now cited and
  distinguished**, and the indexing of Mockenhaupt's original statement — which is
  shifted by one relative to the form used here — is recorded.

The bibliography grew from 20 entries to 32 in the process.

## Status — please read this before citing

Being typeset and compiling cleanly says nothing about whether the mathematics is
right. As of 2026-09-01:

- **Not independently refereed.** The paper has not been submitted to a journal
  and has not been read by a referee.
- **No formal verification is claimed.** An exploratory Lean 4 formalisation was
  attempted while the paper was being written; it is partial, its build does not
  pass, it covers no part of the main line, and it is not part of the proof or of
  this repository. The paper's closing note records the same thing. Removing the
  earlier status section changed the paper's exposition, not this fact.
- **The argument was produced by an automated system**, not merely checked by
  one. This is stated plainly in the paper's `Note on tools`, together with what the
  system got wrong. The mathematics stands or falls on the written proof, which is
  self-contained and can be checked by hand; the authors have read it and take
  responsibility for it.
- **A novelty screen was run on 2026-09-01, and it is not complete.** It found no
  prior work on `k ≥ 6`, and it also found that several things the paper had been
  claiming for itself were already known — `f_0, g_0` are a specialisation of the
  Bonami–Révész idempotents, and the `q = 0` mode of the route used here is
  published as a short-random-walk moment. All of those were corrected in the text
  rather than left standing. The screen declares its own blind spots: MathSciNet was
  not covered, Google Scholar refused access, and two reference works
  (Prudnikov vol. 2, §2.13 and Erdélyi, *Tables of Integral Transforms* II, p. 351)
  could not be read first-hand. If part of this argument is already in print
  somewhere those gaps are where it would be hiding.

Corrections, counterexamples, and pointers to prior art are all welcome — open an
issue. A refutation is worth more to the authors than a citation.

## Licence

Copyright © 2026 Guancheng Pan, Chengsong You, Hengyu Wang, Junwei Zhou and
Yongchao Chen. The paper — both `mockenhaupt.tex` and
`mockenhaupt.pdf` — is licensed under
[Creative Commons Attribution 4.0 International](LICENSE) (CC BY 4.0): reuse,
redistribute and adapt freely, including commercially, with attribution.

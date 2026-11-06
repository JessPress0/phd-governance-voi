# Chapter 1 Schedule: Governance-Conditioned Value of Information

**Chapter:** 1 — Value of Ecological Information Under Governance-Induced Changes to the Action Space  
**Confirmation seminar:** End of June 2027  
**Window:** 16 November 2026 – 30 June 2027  
**Status key:** `[ ]` not started · `[~]` in progress · `[x]` done

---

## 1. Reading (Nov 2026 – Jan 2027)

| Dates | Task | Notes |
|---|---|---|
| 16–30 Nov 2026 | Read Raiffa & Schlaifer, Part II (opportunity loss, EVPI/EVSI) | Extract opportunity-loss logic; ignore conjugate-prior detail. |
| 16–30 Nov 2026 | Read Bolam et al. (2019), *Biological Reviews* 94: 629–647 | Note VoI reporting conventions and gaps. |
| 1–15 Dec 2026 | Read Jaynes, *Probability Theory: The Logic of Science* (priors, Bayesian updating, sampling) | Focus on posterior updating and sampling formulas. |
| 1–31 Dec 2026 | Read Boyd & Vandenberghe, *Convex Optimization*, Ch. 1–5 | Enough to formalise feasibility sets and constrained approval. |
| 1–15 Jan 2027 | Read Luhede et al. (2025), *Environmental Science & Policy* 171: 104164 | Extract dynamic/adaptive learning frontier. |
| 1–15 Jan 2027 | Skim Casella & Berger, *Statistical Inference* (sampling distributions, Type I/II error, power) | Use as reference for EVSI and miss rates. |
| 15–31 Jan 2027 | Annotate and consolidate reading notes into `docs/ch1_reading_notes.md` | Pull out equations, definitions, and gaps. |

**Milestone:** Reading notes consolidated by **31 Jan 2027**.

---

## 2. Mathematical development (Jan – Feb 2027)

| Dates | Task | Notes |
|---|---|---|
| 1–15 Jan 2027 | Formalise base-case system \(\Omega = \{E,A,U,P\}\) and utility assumptions | Align with toy problem: \(e_0\) = low need, \(e_1\) = high need. |
| 1–15 Jan 2027 | Derive standard \(\mathrm{EVPI}\) and verify toy result (1.2) | Write LaTeX derivations. |
| 15–31 Jan 2027 | Define governance belief \(b\), threshold \(\tau\), deterministic approval \(g(a_1,b)\) | Include \(\tau \leq p\) and \(\tau > p\) regimes. |
| 15–31 Jan 2027 | Derive \(\mathrm{EVPI}_{G,\text{det}}\) and verify toy cases (1.2; 4.2) | Check both threshold regimes. |
| 1–14 Feb 2027 | Define probabilistic approval with \(\pi\), fallback to status quo | Derive \(\mathrm{EVPI}_{G,\text{prob}}\). |
| 1–14 Feb 2027 | Verify probabilistic toy cases (0.96; 3.36) | Confirm \(\pi \times \mathrm{EVPI}\) when \(\tau \leq p\). |
| 14–28 Feb 2027 | Derive delta expressions \(\Delta\mathrm{EVPI}_{\text{det vs normal}}\), etc. | Set up for proof section. |
| 14–28 Feb 2027 | Prove upper bounds for \(\mathrm{EVPI}_{G,\text{det}}\) and \(\mathrm{EVPI}_{G,\text{prob}}\) | Write formal proofs in LaTeX. |
| 14–28 Feb 2027 | Prove sign conditions for \(\Delta\mathrm{EVPI}\) expressions | Identify when governance increases or decreases VoI. |

**Milestone:** Core deterministic and probabilistic \(\mathrm{EVPI}_G\) derivations and proofs complete by **28 Feb 2027**.

---

## 3. Simulation development (Feb – Mar 2027)

| Dates | Task | Notes |
|---|---|---|
| 1–15 Feb 2027 | Set up R project structure (`R/`, `data/`, `output/`, `docs/`, `tests/`) | Use `renv` for reproducibility. |
| 1–15 Feb 2027 | Write R functions for standard EVPI, deterministic, and probabilistic governance EVPI | Validate against toy numbers. |
| 15–28 Feb 2027 | Add `testthat` unit tests for toy cases | Commit tests with code. |
| 1–15 Mar 2027 | Implement parameter sweeps over \(p\), \(\tau\), \(\pi\), and utility distributions | Use `purrr`/`expand.grid`; store results. |
| 15–31 Mar 2027 | Validate simulation against analytic results; fix discrepancies | Document validation in `docs/ch1_sim_validation.md`. |
| 15–31 Mar 2027 | Produce solution-space graphs (ggplot2) for \(\mathrm{EVPI}_G\) and deltas | Save as PDF/PNG in `output/figures/`. |
| 1–15 Apr 2027 | Extend to EVSI with imperfect signal (sensitivity/specificity) | Derive and code \(\mathrm{EVSI}_G\). |
| 1–15 Apr 2027 | Validate EVSI code against analytic cases; add tests | Commit EVSI functions and tests. |
| 15–30 Apr 2027 | Produce EVSI comparison figures (\(\mathrm{EVSI}_G\) vs \(\mathrm{EVPI}_G\)) | Finalise Chapter 1 figures. |

**Milestone:** Simulation code, tests, and Chapter 1 figures complete by **30 Apr 2027**.

---

## 4. Paper writing (Mar – May 2027)

Write in this order: abstract last, but draft it early as a placeholder; background and methods first, then results, then discussion, then abstract, then polish.

| Dates | Section | Notes |
|---|---|---|
| 1–15 Mar 2027 | Outline Paper 1 (sections, figures, tables) | One-page outline; circulate to supervisors. |
| 15–31 Mar 2027 | Background / literature review | Draw on Bolam, Luhede, Raiffa & Schlaifer, von Winterfeldt. |
| 1–15 Apr 2027 | Model / methods | Equations (1)–(19) cleaned; governance belief, threshold, approval functions. |
| 15–30 Apr 2027 | Results (deterministic and probabilistic EVPI) | Use toy examples and simulation figures. |
| 1–15 May 2027 | Results (EVSI and comparisons) | Add EVSI_G results. |
| 15–31 May 2027 | Discussion | Link back to governance and VoI literature; limitations. |
| 15–31 May 2027 | Abstract (draft) | 250 words; revise after full draft. |
| 1–10 Jun 2027 | Full draft to supervisors | Allow at least 2 weeks for feedback. |
| 10–20 Jun 2027 | Revise based on supervisor feedback | Track changes; update figures if needed. |
| 20–30 Jun 2027 | Finalise Paper 1 draft | Commit to GitHub as `docs/paper1_draft.md` (or LaTeX). |

**Milestone:** Full Paper 1 draft to supervisors by **10 Jun 2027**; revised draft by **30 Jun 2027**.

---

## 5. Confirmation preparation (May – Jun 2027)

| Dates | Task | Notes |
|---|---|---|
| 15–31 May 2027 | Draft confirmation seminar outline (slides skeleton) | 20–25 slides; structure: problem, gap, model, results, plan. |
| 1–10 Jun 2027 | Build slides (methods, toy examples, figures) | Use Chapter 1 figures; keep math minimal on slides. |
| 10–15 Jun 2027 | Internal practice talk #1 (with supervisors/peers) | Get feedback on clarity and timing. |
| 15–20 Jun 2027 | Revise slides based on feedback | Tighten narrative; fix notation. |
| 20–25 Jun 2027 | Practice talk #2 (full run, timed) | Aim for 20 min + 10 min Q&A. |
| 25–29 Jun 2027 | Final slide polish and dry run | Prepare backup slides for likely questions. |
| 29–30 Jun 2027 | **Confirmation seminar and report submission** | Submit report and deliver seminar. |

**Milestone:** Confirmation seminar delivered and report submitted by **30 Jun 2027**.

---

## 6. Buffer and cross-cutting tasks

| Dates | Task | Notes |
|---|---|---|
| Ongoing | Update `docs/thesis_reading_plan.md` and `docs/research_log.md` | Weekly. |
| Ongoing | Commit to GitHub at least weekly | Meaningful messages. |
| 1–15 May 2027 | Buffer for simulation or proof overruns | Protect this window. |
| 15–30 Jun 2027 | Buffer for writing or slide overruns | Do not schedule new work here. |

---

## Summary of key milestones

| Date | Milestone |
|---|---|
| 31 Jan 2027 | Reading notes consolidated |
| 28 Feb 2027 | Core EVPI_G derivations and proofs complete |
| 30 Apr 2027 | Simulation code, tests, and figures complete |
| 10 Jun 2027 | Full Paper 1 draft to supervisors |
| 29–30 Jun 2027 | Confirmation seminar and report submission |

---

*End of file.*
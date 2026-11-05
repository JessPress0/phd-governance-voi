# Thesis Reading Plan: Governance-Conditioned Value of Information

**Project:** How does complex governance change the Value of Information in conservation?  
**Program:** PhD, QUT — Thesis by published papers  
**File:** `reading_plan.md`  
**Updated:** 2026-11-06

---

## Purpose

Maps readings and topics to each chapter and timeframe, with the expected output for each phase. Update as necessary.

## Priorities:

> Raiffa & Schlaifer → Bolam et al. → Abbas → Krishnamurthy → Gibbons

Everything else is supportive.

## Status key

- `[ ]` not started
- `[~]` in progress
- `[x]` done

---

## Phase summary

| Phase | Thesis focus | Output |
|---|---|---|
| 1. Now – Jan 2027 | Chapter 1: governance-conditioned EVPI and EVSI | Derive deterministic and probabilistic `EVPI_G`; begin `EVSI_G`; prove simple bounds; build clean R simulation for the toy problem. |
| 2. Jan – Jun 2027 | Chapter 1 completion and confirmation | Finalise `EVSI_G`; graph solution spaces; write Paper 1 draft; prepare confirmation seminar. |
| 3. Jul – Dec 2027 | Chapter 2: multi-objective decision-makers | Build RQ2 toy models with multiple actors and weight vectors; formalise trade-off sensitivity and objective conflict; draft Chapter 2 model. |
| 4. Jan – Jun 2028 | Chapter 2 wrap and MDP foundation | Finish Paper 2; establish MDP/POMDP foundation; begin translating Chapter 3 into a belief-state sequential problem. |
| 5. Jul – Dec 2028 | Chapter 3: iterative multi-actor governance | Build RQ3 POMDP model with joint ecological/socio-economic states, joint signals, and dynamic feasibility sets; run simulations; draft Paper 3. |
| 6. Jan – Jun 2029 | Thesis finalisation | Final seminar; polish Paper 3; lodge thesis. |

---

## 1. Now – Jan 2027

**Status:** `[ ]` not started

**Thesis focus:** Chapter 1: governance-conditioned EVPI and EVSI

**Reading and specific sections**

- Raiffa & Schlaifer, *Applied Statistical Decision Theory*, Part II (“Additive Utility, Opportunity Loss, and the Value of Information”); chapters on EVPI/EVSI with two/three processes.
- Bolam et al. (2019), *Biological Reviews* 94: 629–647 (full review).
- Jaynes, *Probability Theory: The Logic of Science* (priors, Bayesian updating, sampling theory).
- Boyd & Vandenberghe, *Convex Optimization*, Ch. 1–5.

**Topics to hit**

- Bayesian updating; prior/posterior beliefs
- Expected utility and risk neutrality
- Opportunity loss
- EVPI derivation (2-state, 2-action)
- EVSI and EVPI relationship
- Imperfect information and sampling
- VoI reporting conventions in conservation
- EVPI/EVSI in ecological language
- Convex sets and functions
- Constrained optimisation formulation
- Duality basics
- Governance feasibility sets and thresholds
- Deterministic vs probabilistic approval

**What to extract / focus on**

From Raiffa & Schlaifer: the opportunity-loss logic behind EVPI/EVSI, not the conjugate-prior machinery. From Bolam: how VoI is reported in conservation and the gaps the governance framing fills. From Jaynes: posterior updating and sampling. From Boyd: enough convex formulation to model governance feasibility sets and constrained approval.

**Output**

Derive deterministic and probabilistic `EVPI_G`; begin `EVSI_G`; prove simple bounds; build clean R simulation for the toy problem.

---

## 2. Jan – Jun 2027

**Status:** `[ ]` not started

**Thesis focus:** Chapter 1 completion and confirmation

**Reading and specific sections**

- Luhede et al. (2025), *Environmental Science & Policy* 171: 104164.
- Casella & Berger, *Statistical Inference* (selected chapters: sampling distributions, Type I/II error, power).
- Abbas, *Foundations of Multiattribute Utility* (preview additive/multiplicative forms only).

**Topics to hit**

- Applied marine VoI
- Dynamic/adaptive learning frontier
- Sampling distributions
- Type I/II error and power
- Miss rates and detection probability
- EVSI with imperfect information
- Additive vs multiplicative MAUT (preview)
- Preference independence (preview)

**What to extract / focus on**

Luhede: how VoI is applied in marine conservation and why dynamic/adaptive learning is flagged as a frontier, motivating Chapter 3. Casella & Berger: the machinery behind miss rates, power, and EVSI. Abbas preview: how additive vs multiplicative MAUT will structure Chapter 2.

**Output**

Finalise `EVSI_G`; graph solution spaces; write Paper 1 draft; prepare confirmation seminar.

---

## 3. Jul – Dec 2027

**Status:** `[ ]` not started

**Thesis focus:** Chapter 2: multi-objective decision-makers

**Reading and specific sections**

- Abbas, *Foundations of Multiattribute Utility* (core chapters: additive utility, multiplicative utility, preference independence, behavioural assumptions).
- Gibbons, *Game Theory for Applied Economists*, Ch. 1–2 (Nash equilibrium, strategic form).

**Topics to hit**

- Additive utility and value functions
- Multiplicative utility and scaling constant `k`
- Preference independence
- Behavioural assumptions and failures
- Non-compensatory constraints as feasibility filters
- Nash equilibrium
- Strategic-form games
- Multiple actors and weight vectors
- Trade-off sensitivity
- Objective conflict and information non-actionability

**What to extract / focus on**

Abbas: how additive MAUT fails under preference dependence; how the multiplicative form captures interacting attributes; how to justify non-compensatory constraints as feasibility filters. Gibbons: basic equilibrium concepts for multi-actor governance.

**Output**

Build RQ2 toy models with multiple actors and weight vectors; formalise trade-off sensitivity and objective conflict; draft Chapter 2 model.

---

## 4. Jan – Jun 2028

**Status:** `[ ]` not started

**Thesis focus:** Chapter 2 wrap and MDP foundation

**Reading and specific sections**

- Gibbons, *Game Theory for Applied Economists* (bargaining, repeated games, basic incomplete-information chapters).
- Krishnamurthy, *Partially Observed Markov Decision Processes*, Ch. 7–8 (MDP → POMDP, belief states, dynamic programming).

**Topics to hit**

- Bargaining and repeated interaction
- Incomplete information
- MDP formulation
- Belief-state representation
- Bellman recursion / dynamic programming
- Observation models
- POMDP formulation

**What to extract / focus on**

Gibbons: bargaining and repeated interaction as the backdrop for negotiated governance. Krishnamurthy: the belief-state MDP formalism needed for Chapter 3; how observations update beliefs and how policies depend on beliefs.

**Output**

Finish Paper 2; establish MDP/POMDP foundation; begin translating Chapter 3 into a belief-state sequential problem.

---

## 5. Jul – Dec 2028

**Status:** `[ ]` not started

**Thesis focus:** Chapter 3: iterative multi-actor governance

**Reading and specific sections**

- Krishnamurthy, Ch. 2–3 (Bayesian filtering, controlled sensing); Ch. 12–13 (structural results and stopping-time POMDPs).
- Lange, *Applied Probability*, Ch. 6–7 (Markov chains, Poisson processes).
- Li & Pozzi (2027), POMDP-based sequential VoI.
- Baarslag & Kaisers (2017), value of information in automated negotiation.

**Topics to hit**

- Bayesian filtering
- Controlled sensing
- Structural results for POMDPs
- Stopping-time POMDPs
- Markov chains
- Poisson processes
- Sequential VoI
- Epistemic constraints
- Negotiation trajectories
- Joint state/signal/belief updates
- Dynamic feasibility sets

**What to extract / focus on**

Krishnamurthy: belief updating, observation models, and structural results for sequential VoI. Lange: Markov-chain transitions for ecological and socio-economic state evolution. Li & Pozzi: VoI in a sequential POMDP with epistemic constraints. Baarslag & Kaisers: how information shapes the trajectory of negotiation, not just one decision.

**Output**

Build RQ3 POMDP model with joint ecological/socio-economic states, joint signals, and dynamic feasibility sets; run simulations; draft Paper 3.

---

## 6. Jan – Jun 2029

**Status:** `[ ]` not started

**Thesis focus:** Thesis finalisation

**Reading and specific sections**

- No new primary readings.
- Use Abbas, Krishnamurthy, Gibbons, and Raiffa & Schlaifer as reference lookups only.

**Topics to hit**

- Notation consistency across chapters
- Proof polishing
- Examiner-facing explanations of governance-conditioned VoI
- Cross-chapter synthesis (thresholds → multi-objective → sequential)

**What to extract / focus on**

Revisit only specific results needed for proofs, notation consistency, and examiner-facing explanations.

**Output**

Final seminar; polish Paper 3; lodge thesis.

---

*End of file.*

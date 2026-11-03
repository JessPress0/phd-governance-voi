# Notation

Single source of truth for symbols. Update here first, then propagate.

| Symbol | Meaning |
|---|---|
| `E = {e_0, e_1}` | Ecological states; `e_0` = low need, `e_1` = high need |
| `p` | Prior `P(e_1)` |
| `A = {a_0, a_1}` | Actions; `a_0` = status quo, `a_1` = needs approval |
| `U(a, e)` | Utility of action `a` in state `e` |
| `b` | Governance belief `P(e_1 \| info available to approval authority)` |
| `tau` in (0, 1) | Governance approval threshold |
| `g(a_1, b)` | Approval probability for `a_1` |
| `pi` | Probabilistic approval rate when `b >= tau` |
| `EVPI` | Standard expected value of perfect information |
| `EVPI_G_det` | Governance-conditioned EVPI, deterministic `g` |
| `EVPI_G_prob` | Governance-conditioned EVPI, probabilistic `g` |
| `EVSI_G` | Governance-conditioned EVSI |

## Known typo in submitted Stage 2 proposal
- Page 12 defines `e_0` twice. The second should be `e_1`.
  Fix in any revision; log in `06_feedback/`.

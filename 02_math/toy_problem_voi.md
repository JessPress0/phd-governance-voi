# Toy Problem: Governance-Conditioned Value of Information

**Project:** How does complex governance change the Value of Information in conservation?
**Objective:** 1 (Value of Ecological Information Under Governance-Induced Changes to the Action Space)

## 1. Base Case: Standard Value of Perfect Information (EVPI)

We define a simple 2-state, 2-action decision problem. 
Let the ecological states be \(E = \{e_0, e_1\}\), representing low and high conservation need, respectively.

The utilities \(U(a, e)\) are given in the matrix below:

| | \(e_0\) (low) | \(e_1\) (high) |
|---|---|---|
| **\(a_0\) (Status quo)** | 10 | 2 |
| **\(a_1\) (Conservation action)** | 6 | 8 |

Let the prior probability of high conservation need be \(p = P(e_1) = 0.7\), meaning \(P(e_0) = 1 - p = 0.3\). 
Thus, the prior belief vector is \(\vec{p} = \begin{bmatrix} 0.3 \\ 0.7 \end{bmatrix}\).

### Calculations

The Expected Value under Certainty (\(\mathrm{EV}_{\text{certainty}}\)) is the expected value of always choosing the optimal action for the realized state:
$$
\mathrm{EV}_{\text{certainty}} = \mathbb{E}_e\left[\max_a[U(a,e)]\right]
$$
$$
\mathrm{EV}_{\text{certainty}} = 0.3(10) + 0.7(8) = 3 + 5.6 = 8.6
$$

The Expected Value under Uncertainty (\(\mathrm{EV}_{\text{uncertainty}}\)) assumes a single action must be chosen without knowing the state, based on the prior:
$$
\mathrm{EV}_{\text{uncertainty}} = \max_a\left[\mathbb{E}[U(a,e)]\right]
$$
$$
\mathrm{EV}_{\text{uncertainty}} = \max\left[0.3(10) + 0.7(2), \ 0.3(6) + 0.7(8)\right]
$$
$$
\mathrm{EV}_{\text{uncertainty}} = \max\left[4.4, \ 7.4\right] = 7.4
$$

The standard Expected Value of Perfect Information (\(\mathrm{EVPI}\)) is:
$$
\mathrm{EVPI} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty}} = 8.6 - 7.4 = 1.2
$$

---

## 2. Deterministic Governance Approval

We introduce a governance threshold \(\tau \in (0,1)\). The conservation action \(a_1\) is only approved if the governance actor's belief \(b = P(e_1 \mid \text{information})\) meets or exceeds \(\tau\). The status quo \(a_0\) is always approved.

$$
g(a_1, b) = 
\begin{cases} 
1, & b \geq \tau \\
0, & b < \tau 
\end{cases}, \qquad g(a_0, b) = 1
$$

### Example 1: \(\tau = 0.6\) 
Since the prior belief \(p = 0.7 \geq \tau = 0.6\), the conservation action is approved based on prior belief alone. 
$$
\mathrm{EVPI}_{G,\text{det}} = \mathrm{EVPI} = 1.2
$$

### Example 2: \(\tau = 0.8\)
Since \(p = 0.7 < \tau = 0.8\), the conservation action is *not* approved based on prior belief.

- **Under Uncertainty**: Only \(a_0\) is available. 
  \[
  \mathrm{EV}_{\text{uncertainty, det}} = 0.3(10) + 0.7(2) = 4.4
  \]
- **Under Certainty**: If \(e_0\) occurs, \(a_0\) is chosen (yielding 10). If \(e_1\) occurs, belief becomes \(b=1.0 \geq 0.8\), so \(a_1\) is approved (yielding 8).
  \[
  \mathrm{EV}_{\text{certainty}} = 8.6
  \]

$$
\mathrm{EVPI}_{G,\text{det}} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty,det}} = 8.6 - 4.4 = 4.2
$$

---

## 3. Probabilistic Governance Approval

We extend the approval mechanism so that if the threshold is met, the action is approved with probability \(\pi \in [0,1]\).

$$
g(a_1, b) = 
\begin{cases} 
\pi, & b \geq \tau \\
0, & b < \tau 
\end{cases}, \qquad g(a_0, b) = 1
$$

### Example 1: \(\pi = 0.8, \tau = 0.6\)
Here, \(p \geq \tau\), so the action is eligible.

- **Certainty**: If \(e_0\) occurs, \(a_0\) (10). If \(e_1\) occurs, \(a_1\) is approved with prob \(0.8\) (8).
  \[
  \mathrm{EV}_c = [U(a_0, e_0) \cdot (1-p)] + [U(a_1, e_1) \cdot p \cdot \pi]
  \]
  \[
  \mathrm{EV}_c = [0.3(10)] + [0.7(8)(0.8)] = 3 + 4.48 = 7.48
  \]
- **Uncertainty**: We compare the expected value of \(a_0\) vs \(a_1\) (weighted by approval probability).
  \[
  \mathrm{EV}_{uc} = \max \left[ 0.3(10) + 0.7(2), \ \{0.3(6) + 0.7(8)\} \cdot 0.8 \right]
  \]
  \[
  \mathrm{EV}_{uc} = \max \left[ 4.4, \ 7.4(0.8) \right] = \max \left[ 4.4, \ 5.92 \right] = 5.92
  \]

$$
\mathrm{EVPI}_{G,\text{prob}} = \mathrm{EV}_c - \mathrm{EV}_{uc} = 7.48 - 5.92 = 1.56
$$

### Example 2: \(\pi = 0.8, \tau = 0.8\)
Here, prior \(p = 0.7 < \tau\), so the action is *not* eligible under uncertainty.

- **Certainty**: 
  \[
  \mathrm{EV}_c = [0.3(10)] + [0.7(8)(0.8)] = 7.48
  \]
- **Uncertainty**: Only \(a_0\) is available, so the \(a_1\) term becomes zero.
  \[
  \mathrm{EV}_{uc} = \max \left[ 0.3(10) + 0.7(2), \ \{0.3(6) + 0.7(8)\} \cdot 0 \right] = \max[4.4, 0] = 4.4
  \]

$$
\mathrm{EVPI}_{G,\text{prob}} = 7.48 - 4.4 = 3.08
$$

---

## 4. Summary of Results

| Metric | Ex 1 (\(b \geq \tau\)) | Ex 2 (\(b < \tau\)) |
| :--- | :--- | :--- |
| **\(\mathrm{EVPI}_{G,\text{det}}\)** | 1.2 | 4.2 |
| **\(\mathrm{EVPI}_{G,\text{prob}}\)** | 1.56 | 3.08 |

### Deltas (\(\Delta \mathrm{EVPI}\))

| Comparison | Ex 1 | Ex 2 |
| :--- | :--- | :--- |
| **\(\Delta \mathrm{EVPI}_{\text{det vs normal}}\)** | \(1.2 - 1.2 = 0\) | \(4.2 - 1.2 = 3\) |
| **\(\Delta \mathrm{EVPI}_{\text{prob vs normal}}\)** | \(1.56 - 1.2 = 0.36\) | \(3.08 - 1.2 = 1.88\) |
| **\(\Delta \mathrm{EVPI}_{\text{prob vs det}}\)** | \(1.56 - 1.2 = 0.36\) | \(4.2 - 3.08 = 1.12\) |
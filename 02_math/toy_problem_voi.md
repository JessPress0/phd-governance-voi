# Toy Problem: Governance-Conditioned Value of Information

**Project:** How does complex governance change the Value of Information in conservation?
**Objective:** 1 (Value of Ecological Information Under Governance-Induced Changes to the Action Space)

## 1. Base Case: Standard Value of Perfect Information (EVPI)

We define a simple 2-state, 2-action decision problem. Let the ecological states be \(E = \{e_0, e_1\}\), representing low and high conservation need, respectively.

The utilities \(U(a, e)\) are given in the matrix below:

| Action \ State | \(e_0\) (low) | \(e_1\) (high) |
| :--- | :--- | :--- |
| **\(a_0\) (Status quo)** | 10 | 2 |
| **\(a_1\) (Conservation action)** | 6 | 8 |

Let the prior probability of high conservation need be \(p = P(e_1) = 0.7\), meaning \(P(e_0) = 1 - p = 0.3\). Thus, the prior belief vector is \(\vec{p} = [0.3, 0.7]^T\).

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

The standard Expected Value of Perfect Information (EVPI) is:

$$
\mathrm{EVPI} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty}} = 8.6 - 7.4 = 1.2
$$

---

## 2. Deterministic Governance Approval

We introduce a governance threshold \(\tau \in (0,1)\). The conservation action \(a_1\) is only approved if the governance actor's belief \(b = P(e_1 \mid \text{information})\) meets or exceeds \(\tau\). The status quo \(a_0\) is always approved.

$$
g(a_1, b) = 
\begin{cases} 
1, & \text{if } b \geq \tau \\
0, & \text{if } b < \tau 
\end{cases}
$$

$$
g(a_0, b) = 1
$$

### Example 1: \(\tau = 0.6\) 
Since the prior belief \(p = 0.7 \geq \tau = 0.6\), the conservation action is approved based on prior belief alone. 

$$
\mathrm{EVPI}_{G,\text{det}} = \mathrm{EVPI} = 1.2
$$

### Example 2: \(\tau = 0.8\)
Since \(p = 0.7 < \tau = 0.8\), the conservation action is *not* approved based on prior belief.

- **Under Uncertainty**: Only \(a_0\) is available. 

$$
\mathrm{EV}_{\text{uncertainty, det}} = 0.3(10) + 0.7(2) = 4.4
$$

- **Under Certainty**: If \(e_0\) occurs, \(a_0\) is chosen (yielding 10). If \(e_1\) occurs, belief becomes \(b=1.0 \geq 0.8\), so \(a_1\) is approved (yielding 8).

$$
\mathrm{EV}_{\text{certainty}} = 8.6
$$

$$
\mathrm{EVPI}_{G,\text{det}} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty,det}} = 8.6 - 4.4 = 4.2
$$

---

## 3. Probabilistic Governance Approval

We extend the approval mechanism so that if the threshold is met, the action is approved with probability \(\pi \in [0,1]\) and rejected with probability \(1-\pi\). 

$$
g(a_1, b) = 
\begin{cases} 
\pi, & \text{if } b \geq \tau \text{ (Approved)} \\
1-\pi, & \text{if } b \geq \tau \text{ (Rejected)} \\
0, & \text{if } b < \tau 
\end{cases}
$$

$$
g(a_0, b) = 1
$$

### 3.1 Modeling Assumption: Fallback to Status Quo
In standard decision theory, if a proposed conservation action \(a_1\) is rejected by the regulator, the decision-maker does not receive zero utility. Instead, the system defaults to the status quo action \(a_0\). 

Therefore, the expected utility of *proposing* \(a_1\) in a given state is a weighted average of the action and the status quo:

$$
\mathbb{E}[\text{Propose } a_1 \mid e] = \pi \cdot U(a_1, e) + (1-\pi) \cdot U(a_0, e)
$$

### Example 1: \(\pi = 0.8, \tau = 0.6\)
Here, prior \(p \geq \tau\), so the action is eligible under uncertainty.

**Expected Value under Certainty (\(\mathrm{EV}_{\text{certainty}}\)):**
*   **State \(e_0\) (prob 0.3):** The decision-maker knows it is \(e_0\), so they choose \(a_0\) and get a utility of 10.
*   **State \(e_1\) (prob 0.7):** The decision-maker knows it is \(e_1\), so they propose \(a_1\). The expected utility is \(0.8(8) + 0.2(2) = 6.4 + 0.4 = 6.8\).

$$
\mathrm{EV}_{\text{certainty}} = [0.3(10)] + [0.7(6.8)]
$$

$$
\mathrm{EV}_{\text{certainty}} = 3 + 4.76 = 7.76
$$

**Expected Value under Uncertainty (\(\mathrm{EV}_{\text{uncertainty}}\)):**
The decision-maker must choose between \(a_0\) and proposing \(a_1\) without knowing the state.
*   Expected value of \(a_0\): \(0.3(10) + 0.7(2) = 4.4\)
*   Expected value of proposing \(a_1\): 
    *   \(80\%\) of the time, they get the expected value of \(a_1\) (which is \(0.3(6) + 0.7(8) = 7.4\)).
    *   \(20\%\) of the time, they are rejected and fallback to \(a_0\) (which has an expected value of 4.4).
    *   Calculation: \(0.8(7.4) + 0.2(4.4) = 5.92 + 0.88 = 6.8\)

$$
\mathrm{EV}_{\text{uncertainty}} = \max \left[ 4.4, \ 6.8 \right] = 6.8
$$

**Governance EVPI:**

$$
\mathrm{EVPI}_{G,\text{prob}} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty}} = 7.76 - 6.8 = 0.96
$$

*(Note: This is equivalent to \(\pi \times \mathrm{EVPI} = 0.8 \times 1.2 = 0.96\))*

### Example 2: \(\pi = 0.8, \tau = 0.8\)
Here, prior \(p = 0.7 < \tau\), so the action is *not* eligible under uncertainty.

**Expected Value under Certainty (\(\mathrm{EV}_{\text{certainty}}\)):**
Same as Example 1, because under certainty the belief becomes \(b=1.0 \geq 0.8\) in state \(e_1\).

$$
\mathrm{EV}_{\text{certainty}} = [0.3(10)] + [0.7(6.8)] = 7.76
$$

**Expected Value under Uncertainty (\(\mathrm{EV}_{\text{uncertainty}}\)):**
Because \(p < \tau\), the decision-maker is not allowed to propose \(a_1\) under uncertainty. They are forced to choose \(a_0\).

$$
\mathrm{EV}_{\text{uncertainty}} = 0.3(10) + 0.7(2) = 4.4
$$

**Governance EVPI:**

$$
\mathrm{EVPI}_{G,\text{prob}} = \mathrm{EV}_{\text{certainty}} - \mathrm{EV}_{\text{uncertainty}} = 7.76 - 4.4 = 3.36
$$

---

## 4. Summary of Results

| Metric | Ex 1 (\(p \geq \tau\)) | Ex 2 (\(p < \tau\)) |
| :--- | :--- | :--- |
| \(\mathrm{EVPI}_{G,\text{det}}\) | 1.2 | 4.2 |
| \(\mathrm{EVPI}_{G,\text{prob}}\) | 0.96 | 3.36 |

### Deltas (\(\Delta \mathrm{EVPI}\))

| Comparison | Ex 1 | Ex 2 |
| :--- | :--- | :--- |
| \(\Delta \mathrm{EVPI}_{\text{det vs normal}}\) | \(1.2 - 1.2 = 0\) | \(4.2 - 1.2 = 3\) |
| \(\Delta \mathrm{EVPI}_{\text{prob vs normal}}\) | \(0.96 - 1.2 = -0.24\) | \(3.36 - 1.2 = 2.16\) |
| \(\Delta \mathrm{EVPI}_{\text{prob vs det}}\) | \(0.96 - 1.2 = -0.24\) | \(3.36 - 4.2 = -0.84\) |
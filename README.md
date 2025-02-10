# Poisson Mixture Model for HIV Risk Assessment

## Problem Overview

The goal of this assignment is to estimate the parameters of a **Poisson mixture model** describing the sexual behavior of individuals at risk for HIV infection. The dataset consists of the number of risky sexual encounters reported by 1500 individuals. Respondents are assumed to belong to three groups:

1. **Group 1:** Individuals who always report zero encounters.
2. **Group 2:** Individuals who belong to a **typical-risk group** where encounters follow a Poisson distribution.
3. **Group 3:** Individuals who belong to a **high-risk group** where encounters follow a Poisson distribution.

The objective is to estimate the model parameters for these groups using the **Expectation-Maximization (EM)** algorithm.

## Problem Setup

Let n_i  denote the number of respondents reporting \( i \) encounters, for \( i = 0, ..., 16 \). These data are assumed to be modeled by a Poisson mixture with the following structure:

- With probability **α**, a respondent belongs to the group that always reports zero encounters.
- With probability **β**, a respondent belongs to the typical-risk group where encounters follow a **Poisson(µ)** distribution.
- With probability **(1 - α - β)**, a respondent belongs to the high-risk group where encounters follow a **Poisson(λ)** distribution.

The parameters to estimate are $$\( \theta = (\alpha, \beta, \mu, \lambda) \)$$.

The likelihood function is given by:

$$\L(\theta|n_0,...,n_{16}) \propto \prod_{i=0}^{16} \frac{(\pi_i(\theta))^{n_i}}{i!}$$


Where $$\pi_i(\theta) $$ is defined as:

$$
\pi_i(\theta) = \alpha \cdot 1(i = 0) + \beta \cdot \frac{\mu^i e^{-\mu}}{i!} + (1 - \alpha - \beta) \cdot \frac{\lambda^i e^{-\lambda}}{i!}
$$


for \( i = 0, ..., 16 \).

### Observed Data

The observed data consists of frequencies \( n_0, ..., n_{16} \) representing the number of respondents reporting \( i \) encounters. Below is the frequency table:

| Encounters, i | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  | 16  |
|----------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Frequency, n_i | 379 | 299 | 222 | 145 | 109 | 95  | 73  | 59  | 45  | 30  | 24  | 12  | 4   | 2   | 0   | 1   | 1   | 0   |

The total number of respondents is \( N = 1500 \).

---

## Questions

1. **Derive the Q function for this problem. What is the E-step? What is the M-step?**

   - Derive the **Q function** for the Poisson mixture model.
   - Describe the **E-step** (Expectation step) and **M-step** (Maximization step) in the Expectation-Maximization algorithm.

2. **Implement the EM algorithm using the given dataset. How did you assess convergence? How many iterations were required for convergence?**

   - Implement the **Expectation-Maximization (EM)** algorithm to estimate the parameters \( \alpha \), \( \beta \), \( \mu \), and \( \lambda \) using the provided data.
   - Describe how convergence was assessed (e.g., by monitoring the log-likelihood or the parameter estimates).
   - Report how many iterations were required for convergence.

3. **Try several randomly selected starting values. Is there evidence that the likelihood is multimodal?**

   - Run the EM algorithm multiple times with different random initializations of the parameters.
   - Investigate whether the likelihood function is **multimodal** (i.e., does it have multiple local maxima?).
   - Discuss if this suggests that the optimization process may depend on the initial parameter values.

---

## Requirements

- Python 3.x
- Libraries: `numpy`, `matplotlib`, `scipy`
- Knowledge of the **Expectation-Maximization (EM)** algorithm and **Poisson mixture models**.

To install the required libraries, you can use the following command:

```bash
pip install -r requirements.txt

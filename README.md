# Galton Board Simulation and Probability Analysis (Google Colab)

This repository contains a **Google Colab notebook** that simulates a **Galton board experiment** and compares the experimental results with the **theoretical Binomial** and **Normal** distributions.

We study how well the empirical data (from simulated falling balls) matches the theoretical predictions of probability theory, and how this match improves when:
- The board becomes larger (`n` increases),
- The number of balls dropped (`N`) increases.

The experiment also verifies that as `n → ∞`, the **Binomial distribution** `Bin(n, 1/2)` approaches the **Normal distribution** `𝒩(n/2, n/4)`.

## How to Run the Experiment

### Option 1 — Run Directly in Google Colab (Recommended)

Click the badge below to open the notebook in Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Aftab5550/galton-board-simulation/blob/main/notebooks/galton_experiment.ipynb)

Then go to **Runtime → Run all**.

This will:
- Simulate ball drops for different `n` and `N`
- Compute experimental vs theoretical probability distributions
- Calculate and plot the **Mean Squared Error (MSE)** between:
  - Empirical data vs Binomial distribution  
  - Empirical data vs Normal approximation (with continuity correction)

---

### Option 2 — Run Locally (Optional)

If you prefer to run it locally:

1. Clone this repository:
   ```bash
   git clone https://github.com/Aftab5550/galton-board-simulation.git
   cd galton-board-simulation

2. Install dependencies:
   ```bash  
   pip install -r requirements.txt

4. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook notebooks/galton_experiment.ipynb

## Experimental Results

**Interpretation**:
- As N (number of balls) increases, the experimental MSE decreases → the observed frequencies converge toward the theoretical probabilities.
- As n (levels) increases, the Normal approximation becomes nearly identical to the Binomial model, confirming the Central Limit Theorem.

## Theoretical Background

For a Galton board with `n` levels, each ball has a 50% chance of falling left or right at each peg. The number of rightward steps `X` follows:
***X∼Binomial(n,0.5)***
For large `n`, by the Central Limit Theorem, this approximates a Normal distribution:
***N(μ=n/2,σ^2=n/4)***

This notebook compares:
- Empirical results → prob_exp
- Theoretical Binomial PMF → binom.pmf(x, n, 0.5)
- Normal approximation (with continuity correction) → norm.cdf(x+0.5) - norm.cdf(x-0.5)

The **Mean Squared Error (MSE)** quantifies the difference between these distributions.

## Requirements

This notebook uses standard scientific Python libraries:
```
numpy
matplotlib
scipy
pandas
```
In Google Colab, these are preinstalled — you don’t need to install anything manually.

## Authors

- Aftab Ahmed Choudhry
- Miquel Sala Franci

Date: October 2025

## License

This project is licensed under the MIT License — feel free to reuse or modify the code for educational purposes.

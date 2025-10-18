# Galton Board Simulation and Probability Analysis (Google Colab)

This repository contains a **Google Colab notebook** that simulates a **Galton board experiment** and compares the experimental results with the **theoretical Binomial** and **Normal** distributions.

We study how well the empirical data (from simulated falling balls) matches the theoretical predictions of probability theory, and how this match improves when:
- The board becomes larger (`n` increases),
- The number of balls dropped (`N`) increases.

The experiment also verifies that as `n → ∞`, the **Binomial distribution** `Bin(n, 1/2)` approaches the **Normal distribution** `𝒩(n/2, n/4)`.

---

## Repository Structure

notebooks/
│ └── galton_experiment.ipynb # Main Colab notebook with the simulation and analysis
results/
│ ├── mse_results.csv # Optional: saved MSE results
│ └── plots/ # Optional: generated plots (e.g., distribution and error graphs)
requirements.txt # Python dependencies (optional for Colab)
README.md # This file

---

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

The following table summarizes the Mean Squared Error (MSE) between the experimental probability distribution (from simulation) and the theoretical Binomial and Normal distributions for various `n` (levels) and `N` (number of balls):

n	N	MSE_Binomial	MSE_Normal
5	50	1.08e-03	1.00e-03
5	50000	1.64e-06	2.15e-05
10	50	1.01e-03	9.52e-04
10	50000	5.59e-07	1.58e-06
30	50	4.24e-04	4.21e-04
30	50000	8.04e-07	7.43e-07
50	50	4.18e-04	4.19e-04
50	50000	3.92e-07	4.37e-07

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

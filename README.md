## How to run

This project is designed to be run on **Google Colab**.

1. Open the notebook `optimizer.ipynb` in Google Colab
2. Run all cells from top to bottom
3. No local installation is required

All dependencies are installed inside the notebook.

# Sigma-Aware TBPSA for Noisy Optimization

Project description

This repository explores how to improve optimization with TBPSA in the presence of heteroskedastic noise.

In this setting, evaluating the objective function at a point 𝑥 does not return a single value 𝑦 but: 𝑦 ± 𝜎, where:
y is the observed value
σ is a known estimate of the noise level
σ is not constant across the search space

This means that some evaluations are much more reliable than others.

# What is TBPSA?

TBPSA (Two-Points Bandit Stochastic Approximation) is a derivative-free optimizer implemented in Nevergrad.
It is designed for noisy optimization and estimates descent directions using comparisons between nearby points.

However, the standard TBPSA implementation does not use the information about the noise level sigma.
# Main contribution

The goal of this project is to make TBPSA sigma-aware.

Since each evaluation comes with an estimate of its uncertainty, we exploit this information to make the optimizer more stable and efficient.

Inspired by the idea:

repeat ("tell") the same datapoint multiple times when its uncertainty is low

we introduce a simple mechanism where observations with lower noise are given more influence in the optimization process.

This approximates an inverse-variance weighting strategy, allowing the optimizer to trust reliable measurements more than highly noisy ones.
# Why this matters

When noise varies across the search space:

Some function evaluations are highly reliable, others are extremely uncertain

Using σ helps improve stability, reduce sensitivity to noisy outliers obtain a more realistic estimate of the minimum

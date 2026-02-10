# Nevergrad-Optimizer
optimizing the Nevergrad Algorithm by introducing a sigma-aware TBPSA algorithm
The user has this problem : they have a noisy objective function.
When they evaluate the function at some point 
x, they don't get a single value y, but y ± σ (the noise level).

So for every observation, the user knows how much noise there is in the measurement.

Another important point is that σ is not constant across the search space.

In this problem, the user uses TBPSA.
TBPSA stands for Test-Based Population Size Adaptation.
It is an optimizer in Nevergrad.

It is an optimization method that works well for continuous and noisy cases.
It adjusts the population size based on statistical tests and recent performance of the evaluations.

How TBPSA Works
Start with a population (set of candidates around the current best point)
Evaluate each candidate : compute the noisy function
Compare candidates using statistical tests
Update the current best point with the best candidate
Adapt population size :
if the improvement is uncertain or noisy : TBPSA increases the population size to gather more evidence
if the improvement is clear and strong : TBPSA reduces the population size to save evaluations
repeat
TBPSA documentation:
https://www.lamsade.dauphine.fr/~cazenave/papers/games_cec.pdf

Why Sigma Matters
So, using TBPSA, we must use 
σ
 (the noise information we have about each observation 
y
)
to determine whether or not we should choose this point when searching for the minimum of a function.

This will help with stability and efficiency when minimum-searching.

The user suggests an idea :

"A naive approach I could see is to [...] 'tell' the same datapoint multiple times if the associated error is small"
→ evaluate the same point multiple times if σ is small.

Takeaways of This Repo
how to use known noise values for better optimization using TBPSA when noise is not the same across the search space how to optimize a noisy function

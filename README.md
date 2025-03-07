# Bacteria Growth Simulation
In this report, we explore the dynamics of bacteria and food populations in a system where they interact with each other. A discrete-time model is implemented to simulate how the populations of two observables change over time. The report demonstrates the empirical theoretical analysis of the impact of different values of independent parameters on food and bacteria populations.

## Rules
We start by randomly scattering the food and bacteria in a certain number of cells. This is done by specifying the density of cells where food and bacteria are present and the units of food and bacteria to place on those cells.

After the initialization step, the model grows the food following a logistic growth model where the food population is capped by a carrying capacity of 100 units.
$f_{t+1}=f_t(1+g_f(1-\frac{f_t}{k_f}))$

Then, the model adds one unit of food to each cell with a probability of 0.01. This is implemented by randomly sampling a number between 0 and 1 from a uniform distribution, which is applied to all cells. In each cell, if that number is $<$ 0.01, we will add 1 unit of food to that cell.

Next, a quarter of the food in a single cell diffuses to its four neighboring cells (Von Neumann neighborhood) where each neighbor gets $\frac{1}{4}d_ff$ units of food added, and the current cell gets subtracted $d_ff$.

Next, the bacteria will consume the food at the rate of $c_b$. At this step, not all bacteria will get to eat, the fraction of bacteria that can survive is determined by:
$$\min(1,\frac{f_t}{c_bb})$$

If the available food is less than the required food, only a fraction of bacteria survive. The bacteria that do not get to eat will die in the starvation step.

Next, the bacteria that survive grow to $b_t(1+g_b)$. Finally, the bacteria diffuses following the same rule as the food.

## Some Results From Empirical Analysis

https://github.com/user-attachments/assets/523b58b2-ca41-45ae-8537-4caf9ff60f61


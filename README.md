# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** G.Sathwik Reddy  
**Student ID    :** 2310040020 
**Date Submitted:** 20-03-2026 

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The fitness() function returns the total value of selected items if the total weight is within the limit. If the weight exceeds the maximum capacity, it returns 0. This penalizes invalid solutions so they are not selected in future generations.
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
The tournament_select() function randomly picks a few individuals and selects the one with the highest fitness. This increases the probability of choosing better solutions. As a result, stronger individuals are more likely to reproduce.
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
The line next_gen = [best_chromosome[:]] copies the best solution into the next generation. This ensures the best solution is never lost due to mutation or crossover. It helps maintain steady improvement in the algorithm.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**
| Metric | Your result |
|--------|-------------|
| Number of generations | 50 |
| Best value at generation 1 | 60 |
| Final best value | 77 |
| Total weight of best solution (kg) | 14.4 |
| Is solution valid (Yes / No) | Yes |

**Copy the printed packing list here:**
```

  Best Packing List
--------------------------------------    
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
--------------------------------------    
  Weight : 14.4 / 15.0 kg
  Value  : 77
  Valid  : Yes

  Generations run : 50
  Value at gen 1  : 60
  Final best value: 77
  Saved -> plots/experiment_1.png
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The graph shows a strong improvement in value during the initial generations. The biggest improvement happens early, as the value increases quickly from the first generation. After that, the curve gradually flattens, indicating that the algorithm has reached a stable optimal solution.
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**
| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         | 75              | 14.9        | Yes    | Slow improvement, early flattening |
| 0.05         | 77              | 14.4        | Yes    | Smooth rise, stable convergence |
| 0.30         | 78              | 14.1        | Yes    | Fluctuating but reaches higher value |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
When the mutation rate is too low (0.01), the algorithm explores very little and quickly gets stuck in a suboptimal solution. When the mutation rate is moderate (0.05), it provides a good balance between exploration and stability. When the mutation rate is high (0.30), the search becomes more random but can sometimes find better solutions. Thus, a balanced mutation rate is generally preferred, though higher mutation may occasionally give better results.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate of 0.30 gave the best result in this case with a value of 78. This is because higher mutation increases diversity and helps explore more possible solutions. However, it may not always be stable compared to moderate mutation rates.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|-----------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | 77 | Balanced mutation gives stable and good results |
| 2 — Mutation rate | mutation_rate = 0.30 | 78 | Higher mutation can find better solutions but may be unstable |
**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
I learned that Genetic Algorithms work by balancing exploration and exploitation to find optimal solutions. Mutation rate plays a crucial role in maintaining diversity in the population. Too little mutation leads to stagnation, while too much makes the search random. A balanced mutation rate usually provides stable results, but higher mutation can sometimes discover better solutions. Overall, Genetic Algorithms are powerful optimization techniques inspired by natural evolution.
```

---


## Submission Checklist

- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, packing list pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
# Airplane Boarding Simulation – Operations Research Project

A Monte Carlo simulation comparing four airplane boarding strategies (Random, Front-to-Back, Back-to-Front and Steffen) to find which one boards a 300-passenger plane fastest, with statistical tests on the differences.

---

## The Model

- **Aircraft:** 50 rows × 6 seats (A–F) = 300 passengers, one aisle.
- **Luggage time:** each passenger stores a bag in a random time ~ Exponential(mean 0.5 min). Passengers behind them in the aisle have to wait.
- **Seat interference:** a passenger whose path to the seat is blocked by people already seated in the same row (e.g. a window passenger when the aisle seat is taken) needs extra time ~ Exponential(mean 0.5 + 0.25 × number of blockers).
- **Output:** total boarding time, meaning the time the last passenger sits down.
- **Replications:** 100 independent runs per strategy.

## Boarding Strategies

| Strategy | Order |
|---|---|
| **Random** | Passengers board in a fully random order. |
| **Front to Back** | Row by row from the front; random order within each row. |
| **Back to Front** | Row by row from the back; random order within each row. |
| **Steffen** | Window seats first, then middle, then aisle; back to front within each group. |

## Statistical Analysis

- **Descriptive statistics:** mean, standard deviation, variance, min/max, and the difference from Steffen for each strategy.
- **95% confidence intervals** for the mean boarding time (t-distribution).
- **One-way ANOVA** to test whether mean boarding times differ between strategies.
- **Scheffé post-hoc test** (implemented manually) for all pairwise comparisons.
- **Brown–Forsythe test** for equal variances across strategies.

## Visualizations

- Cumulative mean boarding time over the simulation runs, to check convergence.
- Bar chart of mean boarding time with standard-deviation error bars.
- Histograms with KDE curves and 95% confidence bands for each strategy.
- Violin plots and overlaid histograms comparing the distributions.

---

## How to Run

Requirements: Python 3 with `numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`.

```bash
pip install numpy scipy pandas matplotlib seaborn
python airplane_boarding_simulation.py
```

The script prints summary statistics and test results for each strategy, then shows the plots. You can change the number of runs, passengers and rows in the `__main__` block.

# NBA Playoff Monte Carlo Simulator — 2025-26 Season

Simulates the 2025-26 NBA playoff bracket 10,000 times to estimate each team's championship probability.

## Method

Each series is modeled as a sequence of independent Bernoulli trials. The probability that team A beats team B in a single game is derived from their Elo ratings:

```
P(A wins game) = 1 / (1 + 10^((elo_B - elo_A) / 400))
```

Home-court advantage adds +70 Elo points to the higher seed for games 1, 2, 5, and 7. After each round the bracket reseeds (lowest vs highest remaining seed), matching the real NBA format.

## 2025-26 Playoff field

### Eastern Conference

| Seed | Team | Play-in note |
|------|------|---|
| 1 | Detroit Pistons | First 1-seed since 2006-07 |
| 2 | Boston Celtics | |
| 3 | New York Knicks | |
| 4 | Cleveland Cavaliers | |
| 5 | Toronto Raptors | First playoff appearance since 2022 |
| 6 | Atlanta Hawks | First playoff appearance since 2023 |
| 7 | Philadelphia 76ers | Won 7v8 play-in game vs Orlando |
| 8 | Orlando Magic | Beat Hornets in play-in, lost to 76ers |

### Western Conference

| Seed | Team | Play-in note |
|------|------|---|
| 1 | Oklahoma City Thunder | 1-seed for third straight year |
| 2 | San Antonio Spurs | First playoff appearance since 2019 |
| 3 | Denver Nuggets | |
| 4 | Los Angeles Lakers | |
| 5 | Houston Rockets | |
| 6 | Minnesota Timberwolves | |
| 7 | Portland Trail Blazers | Won 7v8 play-in game vs Phoenix |
| 8 | Phoenix Suns | Beat Warriors in play-in, then beat Blazers |

## What's inside

The notebook has 9 sections:

1. Team data — 2025-26 playoff field with estimated Elo ratings and play-in context
2. Simulation engine — `win_prob()` and `simulate_series()` functions
3. Full bracket simulator — `simulate_bracket()` with conference reseeding
4. 10,000 simulations
5. Championship probability chart for all 16 teams
6. Series length distribution and win probability for OKC vs Phoenix
7. Sensitivity analysis — how San Antonio's title odds shift as their Elo changes (Wembanyama impact)
8. Summary statistics


## Results

OKC enters as the favorite at ~39% given their 1-seed and top Elo. Detroit checks in at ~21% as the East's best team. San Antonio's Wembanyama-led squad sits at ~15%. The West is significantly stronger in aggregate — West teams win the title roughly 60% of the time combined.

## Requirements

```
numpy
pandas
matplotlib
seaborn
scipy
jupyter
```

Install with:

```bash
pip install numpy pandas matplotlib seaborn scipy jupyter
```

## Run it

```bash
jupyter notebook nba_playoff_monte_carlo_2026.ipynb
```

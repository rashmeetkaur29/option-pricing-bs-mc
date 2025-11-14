![Python](https://img.shields.io/badge/Python-3.10-blue)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

# Option Pricing with Black–Scholes and Monte Carlo Simulation

This project implements and analyzes two fundamental approaches for pricing European call options:

1. the closed-form **Black–Scholes formula**, and  
2. a **Monte Carlo simulation** under the risk-neutral measure.

The goal is to compare the analytical solution with a simulation-based numerical method, visualize their behavior, and build a deeper understanding of option pricing and stochastic modeling.

---

## 1. Introduction

Option pricing is a core concept in quantitative finance and financial engineering.  
The Black–Scholes model provides an analytical closed-form solution for European call options, while Monte Carlo simulation offers a more flexible numerical approach that can extend to complex derivatives.

In this project, both approaches were implemented from scratch using Python (NumPy, SciPy, Matplotlib).  
The analysis explores:

- how the Monte Carlo estimate converges to the Black–Scholes price,  
- how volatility and time-to-maturity influence option value,  
- how stock prices evolve under geometric Brownian motion (GBM), and  
- how discounted call option payoffs are distributed.

All results were generated **entirely through simulation** — no external market data was used.

---

## 2. Model Overview

### **Black–Scholes Formula (European Call)**

\[
d_1 = \frac{\ln(S_0/K) + (r + 0.5\sigma^2)T}{\sigma\sqrt{T}}, \qquad 
d_2 = d_1 - \sigma\sqrt{T}
\]

\[
C = S_0 \, N(d_1) - K e^{-rT} N(d_2)
\]

where:

- **\(S_0\)** — Current stock price  
- **\(K\)** — Strike price  
- **\(r\)** — Risk-free rate  
- **\(\sigma\)** — Volatility  
- **\(T\)** — Time to maturity  

---

### **Monte Carlo Simulation**

Under the risk-neutral measure, stock prices follow:

\[
S_T = S_0 \exp\left((r - 0.5\sigma^2)T + \sigma\sqrt{T} Z\right), \qquad Z \sim N(0,1)
\]

Discounted payoff:

\[
C_{\text{MC}} = e^{-rT} \; \mathbb{E}[\max(S_T - K, 0)]
\]

Monte Carlo estimates this expectation using thousands of simulated price paths.

---

## 3. Key Results

Both models produced nearly identical prices for typical parameters:

| Method                        | Estimated Price |
|------------------------------|-----------------|
| Black–Scholes                | ~10.45          |
| Monte Carlo (100,000 paths) | ~10.42          |

The small difference is due to sampling randomness and decreases as the number of simulated paths increases.

---

## 4. Visualizations

### ✔ Monte Carlo Convergence  
Shows how the simulation estimate approaches the Black–Scholes price.

### ✔ Simulated Price Paths (GBM)  
Multiple stock price trajectories generated using geometric Brownian motion.

### ✔ Option Price vs Volatility  
Illustrates how option value increases as volatility rises (Vega behavior).

### ✔ Option Price vs Time to Maturity  
Shows how more time increases an option's value (Theta behavior).

### ✔ Distribution of Discounted Payoffs  
A right-skewed distribution reflecting the asymmetric nature of call payoffs.

---

## 5. Why No External Market Data Was Used

This project focuses on **model-based pricing**, not historical market analysis.

- The Black–Scholes formula gives an analytical price.  
- Monte Carlo uses model-generated paths.  
- All plots visualize **model outputs**, not past prices.

This reflects standard quantitative finance workflows where theory is validated before applying real market data.

---

## 6. Project Structure

```
option-pricing-bs-mc/
│
├── notebooks/
│ └── option_pricing_bs_mc.ipynb # Main analysis notebook
│
├── src/
│ └── init.py # Placeholder for future modules
│
├── README.md # Project documentation
├── requirements.txt # Python dependencies
└── .gitignore # Ignored files (venv, checkpoints, caches)
```

---

## 7. Skills Demonstrated

- Mathematical modeling of derivatives  
- Black–Scholes analytical pricing  
- Monte Carlo simulation  
- Stochastic processes (GBM)  
- Data visualization with Matplotlib  
- Python (NumPy, SciPy)  
- Jupyter Notebook workflow  
- Clean, reproducible project structure  
- Git & GitHub version control  

---

## 8. Future Improvements

Potential extensions:

- Computing Greeks (Delta, Gamma, Vega, Theta, Rho)  
- Pricing put options and exotic derivatives  
- Variance-reduction techniques (antithetic variates, control variates)  
- Euler vs exact GBM discretization comparison  
- Stochastic volatility models (Heston model)  

---

## 9. Conclusion

This project builds a complete pipeline for option pricing using both analytical and simulation-driven methods.  
It strengthened my understanding of stochastic modeling, Monte Carlo simulation, risk-neutral valuation, and numerical convergence — foundational tools for quantitative finance and financial engineering.


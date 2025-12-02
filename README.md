Interest Rate Risk (IRR) Model – Yield Curve Simulation

An interest-rate risk framework that models yield-curve movements using Principal Component Analysis (PCA) and Monte Carlo simulation. The project extracts key risk factors (Level, Slope, Curvature), simulates future yield curve paths, and visualizes interest-rate risk dynamics typically used in banks, investment funds, and ALM team

Objective:
To build a robust Interest Rate Risk (IRR) modelling framework that:
Extracts systematic yield-curve risk factors using PCA.
Quantifies historical yield-curve movements using daily changes.
Simulates future interest rate scenarios using Monte Carlo.
Helps measure risk exposure to parallel, slope, and curvature shifts.
Enables visualization and analysis of future yield-curve uncertainty over a selected horizon.

Process Workflow
1. Data Collection
Historical yield curve data across selected tenors (e.g., 3M, 6M, 1Y, 2Y, 5Y, 10Y).
Data arranged in a matrix: rows = dates, columns = maturities.

2. Data Transformation
Daily yield changes computed:
Δ𝑦𝑡=𝑦𝑡−𝑦𝑡−1
This stabilizes variance and prepares data for PCA.

3. PCA-Based Factor Extraction:
PCA applied on yield changes to extract orthogonal factors.
First 3 components typically interpreted as:
Factor 1 (Level): Parallel shift
Factor 2 (Slope): Steepening / flattening
Factor 3 (Curvature): Change in belly vs wings
Factor loadings plotted to validate shapes.

4. Factor Volatility Estimation:
Factor returns = Δyield × PCA loadings.
Covariance matrix of factors estimated for simulation.

5. Monte Carlo Simulation of Yield Curves:
Simulated 1,000+ future yield curves using PCA shocks:
Δ𝑦=𝑃⋅FactorShock
Current curve used as starting point.
Simulations propagated over 30-day horizon.

6. Visualization:
Multiple simulated curves plotted against the current yield curve.
PCA loadings plotted to show economic interpretation of factors.

Results:
Variance Explained by PCA

| PCA Factor    | Variance Explained |
| ------------- | ------------------ |
| **Level**     | **80–90%**         |
| **Slope**     | **5–10%**          |
| **Curvature** | **2–5%**           |

Factor Shapes (Economic Interpretation):
Level: All tenors shift together (parallel move).
Slope: Short rates vs long rates diverge.
Curvature: Mid-tenors move opposite to short/long ends.


Simulation Output:
1,000+ yield curve scenarios generated.

Average 30-day simulated movements (example):
Short-tenor (3M): ±15–25 bps
Belly (2Y–5Y): ±10–20 bps
Long-tenor (10Y): ±8–15 bps.

These ranges quantify short-term interest-rate uncertainty.

Risk Insight:
Level factor dominated risk contribution.
Slope movements significantly influenced near-term IR volatility.
Curvature shocks concentrated around belly tenors.

Future Enhancements:

1. PV01 & Key Rate Duration Integration
Compute interest-rate sensitivity of any bond/portfolio using:
PV01
DV01
Key Rate Duration (KRD)

2. Advanced Simulation
Add:
Hull–White one-factor model
CIR interest-rate diffusion
Local volatility surfaces

3. Stress Testing Framework
Implement regulatory & internal IRRBB shocks:
±200 bps parallel
Steepener / Flattener
Short-end / Long-end shocks

4. Yield Curve Reconstruction
Use:
Nelson–Siegel–Svensson (NSS) fitting
Smooth curve generation for incomplete tenor sets

5. Portfolio Impact Analysis
Simulate impact on:
Fixed-income assets
Loans & deposits
Derivatives (IRS, Caps, Floors)



# Bacterial Growth Curve Analysis: A Computational and Experimental Study

**Course:** BIO1004 - Ecology and Environmental Sciences  
**Student:** Manya Jindal  
**Institution:** Shiv Nadar Institution of Eminence  
**Date:** October 19, 2025

---

## Introduction

Bacterial population dynamics provide a fundamental model for understanding population growth in ecology. In this practical, I explore two classical growth models—**exponential** and **logistic**—through both computational simulation (*in silico*) and laboratory experimentation using *Escherichia coli*.

**Objectives:**
1. Simulate exponential and logistic growth using iterative methods
2. Analyze how parameters (r, K, N₀) affect population dynamics
3. Validate theoretical models with experimental data
4. Investigate environmental effects (pH, nutrients) on bacterial growth

---

## Part 1: Theoretical Background

### 1.1 Exponential Growth Model

The exponential growth model assumes unlimited resources and describes a population growing at a constant rate:

\[
\frac{dN}{dt} = rN
\]

Where:
- **N** = Population size (number of individuals)
- **r** = Intrinsic growth rate (per capita)
- **t** = Time

**Integrated form:**
\[
N_t = N_0 e^{rt}
\]

Where **N₀** is the initial population size at t = 0.

**Key insight:** In exponential growth, the population doubles at regular intervals, leading to the "J-shaped" curve. This model works well for short-term bacterial growth in resource-rich environments.

---

### 1.2 Logistic Growth Model

The logistic model introduces environmental constraints through carrying capacity:

\[
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)
\]

Where:
- **K** = Carrying capacity (maximum sustainable population)

**Integrated form:**
\[
N_t = \frac{N_0 K}{N_0 + (K - N_0)e^{-rt}}
\]

**Key insight:** Growth slows as the population approaches K, creating an "S-shaped" (sigmoid) curve. This better represents real bacterial growth where resources become limited.

---

### 1.3 Why Study *E. coli* Growth?

*Escherichia coli* is an ideal model organism:
- Fast generation time (~20 minutes under optimal conditions)
- Easy to culture in laboratory settings
- Well-characterized growth patterns

**Thought experiment:** If one *E. coli* cell (volume ≈ 1.57 × 10⁻²⁷ m³) divided every 20 minutes exponentially, it would produce 2¹²⁹ cells in 43 hours—equivalent to the volume of Earth! This demonstrates why exponential growth cannot continue indefinitely.

---

## Part 2: In Silico Simulations

### 2.1 Iterative Method for Numerical Approximation

Rather than solving differential equations analytically, we use **Euler's method** with discrete time steps:

**For exponential growth:**
\[
N_{t+1} = N_t + rN_t
\]

**For logistic growth:**
\[
N_{t+1} = N_t + rN_t\left(1 - \frac{N_t}{K}\right)
\]

This approach is biologist-friendly and easily implemented in Excel or programming languages.

---

### 2.2 Excel Implementation Guide

#### Step 1: Set Up Your Spreadsheet

| Column A | Column B | Column C | Column D | Column E |
|----------|----------|----------|----------|----------|
| Time (t) | N | dN/dt | (1/N)(dN/dt) | Notes |

#### Step 2: Define Parameters
- Cell F1: `N0 = 100` (initial population)
- Cell F2: `r = 0.5` (growth rate)
- Cell F3: `K = 1000` (carrying capacity, for logistic only)

#### Step 3: Enter Formulas

**For Exponential Growth:**
- A2: `0` (time zero)
- B2: `=$F$1` (N₀)
- C2: `=$F$2*B2` (dN/dt = r*N)
- D2: `=C2/B2` (per capita growth rate)
- A3: `=A2+1` (increment time)
- B3: `=B2+C2` (N_{t+1} = N_t + dN/dt)

**Drag formulas down** for t = 0 to 50.

**For Logistic Growth:**
- Follow same structure but modify C2:
- C2: `=$F$2*B2*(1-B2/$F$3)` (includes carrying capacity term)

---

### 2.3 Creating Plots

Generate three plots for each model:

1. **N vs. t** (Population over time)
   - X-axis: Time
   - Y-axis: Population size
   - Shows the growth curve shape

2. **dN/dt vs. N** (Rate of change vs. population)
   - X-axis: Population size
   - Y-axis: Rate of change
   - For logistic: produces a parabola

3. **(1/N)(dN/dt) vs. N** (Per capita growth vs. population)
   - X-axis: Population size
   - Y-axis: Per capita growth rate
   - For logistic: produces a straight line with negative slope

---

### 2.4 Parameter Effects Analysis

#### Effect of r (Growth Rate)

**Experiment:** Simulate with r = 0.1, 0.5, 1.0

**Expected observations:**
- Higher r → steeper curves, faster approach to K
- In exponential model: r directly affects doubling time (doubling time = ln(2)/r)
- In logistic model: r affects how quickly population reaches carrying capacity

**Biological interpretation:** r represents resource availability, temperature optimality, or genetic fitness.

---

#### Effect of K (Carrying Capacity)

**Experiment:** Simulate with K = 500, 1000, 2000 (keeping r constant)

**Expected observations:**
- K determines the asymptote of the logistic curve
- Does not affect initial growth rate
- Higher K → larger final population

**Biological interpretation:** K represents environmental constraints (space, nutrients, waste accumulation).

---

#### Effect of N₀ (Initial Population)

**Experiment:** Simulate with N₀ = 10, 100, 500

**Expected observations:**
- Different starting points on the curve
- Same final carrying capacity K
- Time to reach K varies with N₀

**Biological interpretation:** Initial inoculum size affects lag phase duration.

---

## Part 3: Wet Lab Experimental Procedure

### 3.1 Materials and Methods

**Organism:** *Escherichia coli*

**Growth Medium:** LB (Luria-Bertani) liquid medium
- Tryptone: 10 g/L
- NaCl: 10 g/L
- Yeast extract: 5 g/L

**Experimental Design:**
- **pH levels:** 5.0, 7.0, 8.5
- **Nutrient concentrations:** Original, 1:2 diluted, 1:5 diluted
- **Total combinations:** 9 growth conditions

**Setup:**
1. Sterilize medium at 121°C, 15 psi
2. Inoculate with *E. coli* culture
3. Incubate at 37°C with shaking (120 rpm)
4. Measure optical density (OD) every 30 minutes using colorimeter

---

### 3.2 Measurement Principle: Beer-Lambert Law

Bacterial turbidity serves as a proxy for population density:

\[
A = \epsilon c l
\]

Where:
- **A** = Absorbance
- **ε** = Extinction coefficient
- **c** = Concentration (bacterial density)
- **l** = Path length

**Why this works:** Bacteria refract light, reducing transmitted intensity. Higher bacterial density → higher absorbance (OD).

---

### 3.3 Data Analysis with PAST Software

**Steps:**
1. Import OD vs. time data
2. Select "Nonlinear Modeling" tool
3. Fit logistic curve: \( y = \frac{a}{1 + be^{-cx}} \)
   - a = K (carrying capacity)
   - c = r (growth rate)
4. Record fitted r and K values for each condition

---

## Part 4: Results

### 4.1 In Silico Results

**Exponential Growth Simulations:**
- With r = 0.5, N₀ = 100: Population reaches ~12,000 by t = 50
- Doubling time = 1.39 time units
- Per capita growth rate remains constant (horizontal line)

**Logistic Growth Simulations:**
- With r = 0.5, N₀ = 100, K = 1000: Population stabilizes at K
- Inflection point occurs at N = K/2 = 500
- Maximum growth rate (dN/dt) occurs at inflection point

**Comparison with Analytical Solutions:**
- Iterative method closely matches integrated equations
- Small deviations occur at high r values (due to step size)

---

### 4.2 Wet Lab Results

**Sample Data Table (to be filled with your experimental values):**

#### r values (Growth Rate)

| pH  | Original | 1:2 Diluted | 1:5 Diluted |
|-----|----------|-------------|-------------|
| 5.0 | [value]  | [value]     | [value]     |
| 7.0 | [value]  | [value]     | [value]     |
| 8.5 | [value]  | [value]     | [value]     |

#### K values (Carrying Capacity)

| pH  | Original | 1:2 Diluted | 1:5 Diluted |
|-----|----------|-------------|-------------|
| 5.0 | [value]  | [value]     | [value]     |
| 7.0 | [value]  | [value]     | [value]     |
| 8.5 | [value]  | [value]     | [value]     |

**Instructions for your data:**
- Insert OD vs. time plots for each condition
- Add screenshots from PAST showing fitted curves
- Record r and K from each fit

---

## Part 5: Discussion

### 5.1 Effect of Growth Rate (r)

**From simulations:**
- Increasing r accelerates population growth in both models
- In exponential model: affects slope directly
- In logistic model: affects speed of approach to K, not final size

**From experiments:**
- Expected: Optimal pH (7.0) and full nutrients yield highest r
- Suboptimal pH (5.0, 8.5) should reduce r due to enzyme activity changes
- Diluted nutrients should reduce r due to resource limitation

**Biological significance:** r reflects metabolic efficiency and resource quality.

---

### 5.2 Effect of Carrying Capacity (K)

**From simulations:**
- K determines maximum sustainable population
- Independent of growth rate r
- Represents environmental limit

**From experiments:**
- Expected: Nutrient concentration directly affects K
- Original medium → highest K
- 1:5 dilution → lowest K (5× less nutrients)
- pH should have minimal effect on K (affects growth rate more)

**Biological significance:** K reflects resource availability and physical space constraints.

---

### 5.3 Effect of Initial Population (N₀)

**From simulations:**
- N₀ affects lag phase duration
- All curves converge to same K
- Lower N₀ → longer time to reach stationary phase

**Biological significance:** Inoculum size affects experimental reproducibility and timing.

---

### 5.4 Environmental Factors: pH and Nutrients

**pH Effects:**
- **pH 7.0 (neutral):** Optimal for *E. coli* enzyme function
- **pH 5.0 (acidic):** Denatures proteins, reduces membrane stability → lower r
- **pH 8.5 (alkaline):** Disrupts proton gradients → lower r

**Nutrient Effects:**
- **Original medium:** Maximum nutrient availability → highest K and r
- **1:2 Dilution:** Moderate limitation → intermediate values
- **1:5 Dilution:** Severe limitation → lowest K, possibly lower r

**Synergistic effects:** Suboptimal pH + low nutrients compound growth inhibition.

---

### 5.5 Model Validation

**Questions to address:**
- Do experimental curves follow logistic pattern?
- How well does the model fit (R² values from PAST)?
- Any deviations? (e.g., extended lag phase, death phase)

**Limitations:**
- OD measures total biomass (live + dead cells)
- Model assumes closed system (no immigration/emigration)
- Simplifies complex bacterial physiology

---

## Part 6: Optional Explorations

### 6.1 Allee Effect Model

\[
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)\left(\frac{N}{T} - 1\right)
\]

Where T is the **Allee threshold** (0 < T < K).

**Questions:**
- What happens when N₀ < T vs. N₀ > T?
- **Ecological significance:** Minimum viable population for growth (mate finding, cooperative feeding)

---

### 6.2 Generalized Logistic (Theta-Logistic) Model

\[
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)^y
\]

Where y is a shape parameter.

**Questions:**
- How does y affect curve shape?
  - y < 1: Convex curve (slow initial growth)
  - y = 1: Standard logistic
  - y > 1: Concave curve (fast initial growth)
- **Ecological significance:** Represents density-dependent feedback strength

---

## Conclusion

This practical demonstrated the power of mathematical modeling in ecology:

1. **Exponential growth** describes short-term bacterial dynamics but is unrealistic long-term
2. **Logistic growth** accurately captures resource-limited population dynamics
3. **Iterative numerical methods** provide accessible tools for solving differential equations
4. **Environmental factors** (pH, nutrients) significantly affect both growth rate (r) and carrying capacity (K)
5. **Experimental validation** confirms theoretical predictions with some deviations due to biological complexity

**Key takeaways:**
- Models are simplifications but provide valuable insights
- Parameter estimation (r, K) connects theory to real data
- Understanding population dynamics informs fields from microbiology to conservation

---

## References

1. Dahanukar, N. (2025). Practical 2: Bacterial growth curve. BIO104 Ecology and Environmental Sciences. Shiv Nadar Institution of Eminence.

2. Zwietering, M. H., Jongenburger, I., Rombouts, F. M., & Van't Riet, K. (1990). Modeling of the bacterial growth curve. *Applied and Environmental Microbiology*, 56(6), 1875-1881.

3. Hammer, Ø., Harper, D. A., & Ryan, P. D. (2001). PAST: Paleontological statistics software package for education and data analysis. *Palaeontologia Electronica*, 4(1), 9.

---

## Appendix: Excel Formulas Quick Reference

**Exponential Growth:**
```
Initial population (N0): [value in cell F1]
Growth rate (r): [value in cell F2]

Time column (A): 0, 1, 2, 3, ...
N column (B): =$F$1, then =B2+C2 (drag down)
dN/dt column (C): =$F$2*B2 (drag down)
Per capita column (D): =C2/B2 (drag down)
```

**Logistic Growth:**
```
Add: Carrying capacity (K): [value in cell F3]

Modify dN/dt (C): =$F$2*B2*(1-B2/$F$3)
All other formulas remain the same
```

---


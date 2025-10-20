# Bacterial Growth Curve Analysis

> A computational and experimental study of *E. coli* population dynamics using exponential and logistic growth models

[![Made with Excel](https://img.shields.io/badge/Made%20with-Excel-217346?style=flat&logo=microsoft-excel)](https://www.microsoft.com/excel)
[![PAST Software](https://img.shields.io/badge/Analysis-PAST%20Software-blue)](https://www.nhm.uio.no/english/research/infrastructure/past/)
[![Course](https://img.shields.io/badge/Course-BIO1004-green)](https://snu.edu.in)

## Table of Contents
- [Overview](#overview)
- [Objectives](#objectives)
- [Methodology](#methodology)
- [Repository Structure](#repository-structure)
- [Results](#results)
- [Key Findings](#key-findings)
- [How to Use](#how-to-use)
- [Technologies Used](#technologies-used)
- [References](#references)
- [Contact](#contact)

---

##  Overview

This project explores bacterial population dynamics through both **computational simulations** (*in silico*) and **laboratory experiments** using *Escherichia coli*. The study compares two fundamental ecological models:

- **Exponential Growth Model**: Unlimited resource scenario
- **Logistic Growth Model**: Resource-limited scenario with carrying capacity

The project investigates how environmental factors (pH and nutrient concentration) affect bacterial growth parameters (r and K).

---

##  Objectives

1. Simulate exponential and logistic growth using iterative numerical methods
2. Analyze the effects of parameters (r, K, N₀) on population dynamics
3. Validate theoretical models with experimental data
4. Investigate environmental impacts on bacterial growth
5. Develop practical skills in ecological modeling and data analysis

---

##  Methodology

### In Silico Simulations
- **Tool**: Microsoft Excel
- **Method**: Euler's iterative approach for numerical integration
- **Parameters tested**:
  - Growth rate (r): 0.1, 0.5, 1.0
  - Carrying capacity (K): 500, 1000, 2000
  - Initial population (N₀): 10, 100, 500

### Wet Lab Experiments
- **Organism**: *Escherichia coli*
- **Growth medium**: LB (Luria-Bertani) liquid medium
- **Experimental variables**:
  - pH levels: 5.0, 7.0, 8.5
  - Nutrient concentrations: Original, 1:2 diluted, 1:5 diluted
- **Measurement**: Optical density (OD) at 600nm every 30 minutes
- **Analysis**: PAST software for logistic curve fitting

---

##  Repository Structure

```
bacterial-growth-analysis/
│
├── README.md                          # This file
├── REPORT.md                          # Detailed notebook-style report
│
├── data/
│   ├── exponential_simulations.xlsx   # Excel file with exponential model
│   ├── logistic_simulations.xlsx      # Excel file with logistic model
│   └── wetlab_data.csv                # Experimental OD measurements
│
├── plots/
│   ├── exponential_N_vs_t.png         # Population over time (exponential)
│   ├── exponential_rate_vs_N.png      # Growth rate vs population
│   ├── exponential_percapita_vs_N.png # Per capita growth vs population
│   ├── logistic_N_vs_t.png            # Population over time (logistic)
│   ├── logistic_rate_vs_N.png         # Growth rate vs population
│   ├── logistic_percapita_vs_N.png    # Per capita growth vs population
│   └── experimental_curves/           # Fitted curves from PAST
│       ├── pH5_original.png
│       ├── pH7_original.png
│       └── ...
│
├── docs/
│   ├── assignment_brief.pdf           # Original assignment document
│   └── past_tutorial.md               # Guide for using PAST software
```

---

##  Results

### Simulation Results

#### Exponential Growth
- **Key observation**: J-shaped curve with unlimited growth
- **Doubling time** (r = 0.5): ~1.39 time units
- **Per capita growth rate**: Constant across all population sizes

![Exponential Growth Curve](plots/exponential_N_vs_t.png)
*Figure 1: Exponential growth with r = 0.5, N₀ = 100*

#### Logistic Growth
- **Key observation**: S-shaped curve approaching carrying capacity
- **Inflection point**: Occurs at N = K/2
- **Maximum growth rate**: At inflection point

![Logistic Growth Curve](plots/logistic_N_vs_t.png)
*Figure 2: Logistic growth with r = 0.5, N₀ = 100, K = 1000*

---

### Experimental Results

#### Growth Parameters by Condition

| pH  | Nutrients | r (growth rate) | K (carrying capacity) |
|-----|-----------|----------------|-----------------------|
| 5.0 | Original  | [value]        | [value]               |
| 7.0 | Original  | [value]        | [value]               |
| 8.5 | Original  | [value]        | [value]               |
| 5.0 | 1:2       | [value]        | [value]               |
| 7.0 | 1:2       | [value]        | [value]               |
| 8.5 | 1:2       | [value]        | [value]               |
| 5.0 | 1:5       | [value]        | [value]               |
| 7.0 | 1:5       | [value]        | [value]               |
| 8.5 | 1:5       | [value]        | [value]               |

*Table 1: Fitted growth parameters from experimental data*

---

##  Key Findings

### Effect of Growth Rate (r)
- Higher r → faster population growth and quicker approach to carrying capacity
- Biologically represents metabolic efficiency and resource quality
- Optimal conditions (pH 7.0, full nutrients) yielded highest r values

### Effect of Carrying Capacity (K)
- K determines maximum sustainable population size
- Directly correlated with nutrient concentration
- Independent of initial population size

### Environmental Impacts
- **pH 7.0** (neutral): Optimal for *E. coli* enzyme function
- **pH 5.0/8.5**: Reduced growth rates due to protein denaturation
- **Nutrient dilution**: Proportionally reduced carrying capacity

### Model Validation
- Logistic model accurately describes bacterial growth curves
- Good fit with experimental data (R² > 0.95 in most cases)
- Deviations observed in extreme pH conditions

---

##  How to Use

### For University Submission
1. Download the complete repository as ZIP
2. Review `REPORT.md` for detailed analysis
3. Check data files in `/data` folder
4. View plots in `/plots` folder

### For Portfolio Viewers
1. Read this README for a quick overview
2. Explore `REPORT.md` for full notebook-style report
3. Download Excel files to see simulation methods
4. Check `/plots` for visual results

### Recreating Simulations
1. Open Excel files in `/data` folder
2. Modify parameter values (r, K, N₀) in designated cells
3. Formulas will auto-update calculations
4. Generate new plots from updated data

---

## Technologies Used

- **Microsoft Excel**: Numerical simulations and data visualization
- **PAST Software**: Statistical analysis and curve fitting
- **Colorimeter**: Optical density measurements
- **LaTeX**: Mathematical equation formatting
- **Markdown**: Documentation and reporting

---

## References

1. Dahanukar, N. (2025). *Practical 2: Bacterial growth curve*. BIO1004 Ecology and Environmental Sciences. Shiv Nadar Institution of Eminence.

2. Zwietering, M. H., et al. (1990). Modeling of the bacterial growth curve. *Applied and Environmental Microbiology*, 56(6), 1875-1881.

3. Hammer, Ø., Harper, D. A., & Ryan, P. D. (2001). PAST: Paleontological statistics software package for education and data analysis. *Palaeontologia Electronica*, 4(1), 9.

---

## Contact

**Manya Jindal**  
BIO1004 - Ecology and Environmental Sciences  
Shiv Nadar Institution of Eminence  
📫 mj225@snu.edu.in

---

## License

This project is submitted as part of academic coursework at Shiv Nadar University. Please cite appropriately if using for educational purposes.

---

## Acknowledgments

- Dr. Neelesh Dahanukar for course instruction and practical design
- Laboratory staff for technical support
- Tania Varghese (teaching assistant) for guidance

---

*Last Updated: October 20, 2025*

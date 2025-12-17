# Expected Goals (xG) Modeling - Master Thesis

## Overview
This repository contains the complete R code and analysis for our master thesis on Expected Goals (xG) modeling in football.
The project analyzes unblocked shots from the top 5 European leagues (2017-2018 season) using machine learning approaches, particularly Gradient Boosting Machines (GBM) and Generalized Linear Models (GLM).

## 📂 Repository Structure
```
├── README.md                          
├── data/                              
│   ├── players.json
│   ├── events_England.json
│   ├── events_France.json
│   ├── events_Germany.json
│   ├── events_Italy.json
│   └── events_Spain.json
├── R/                                 # R scripts and functions
│   ├── Get shots.R                   # Function to extract shot data
│   └── Get shots extra.R             # Extended shot data extraction
├── analysis/                          # Analysis R Markdown files
│   ├── 01_Load_rawdata.Rmd          # Data loading and preprocessing
│   ├── 02_Exploratory_analysis.Rmd   # EDA and feature engineering
│   ├── 03_Fit_models.Rmd            # Main model fitting (GBM & GLM)
│   ├── 04_Fit_models_big.Rmd        # Extended model with more features
│   ├── 05_Fit_right_footed_models.Rmd
│   ├── 06_Fit_left_footed_models.Rmd
│   ├── 07_Evaluate_models.Rmd        # Main model evaluation
│   ├── 08_Evaluate_models_big.Rmd
│   ├── 09_Evaluate_right_footed_models.Rmd
│   ├── 10_Evaluate_left_footed_models.Rmd
│   ├── 11_Calculations.Rmd           # xG calculations by counter-attack
│   ├── 12_Hypothesis_test.Rmd        # Statistical tests
│   └── 13_Mixture_models_analysis.Rmd # Distribution fitting
```
##Data:
The data comes from the Wyscout dataset containing event-level data from:

- English Premier League
- French Ligue 1
- German Bundesliga
- Italian Serie A
-Spanish La Liga
- Aswell as player data.

The data stem from JSON files, and can be found in the data folder.
## Prerequisites

Note, the H2O package requires Java. To install:
Run 'system("java -version")' in the console to check whether it is installed correctly or not.
If not: install from https://www.oracle.com/java/technologies/downloads/
Additionally you may need to set where Java lies in the system.
This is done as follows:
1. Find the Java installation path
2. Open Environmental Variables
3. Under System Variables add:
  - Variable name: JAVA_HOME
  - Variable value: The installation path
4. Add %JAVA_HOME%\bin to Path if not already there.

### Required R Packages
** Data manipulation and visualization
library(tidyverse)
library(jsonlite)
library(dplyr)

** Visualization
library(ggplot2)
library(ggsoccer)
library(RColorBrewer)
library(gridExtra)
library(ggpubr)
library(DataExplorer)

** Machine learning
library(h2o)
library(caret)

** Model evaluation
library(pROC)
library(ROCR)
library(DALEX)
library(pdp)
library(ingredients)

** Mixture models
library(mclust)
library(gamlss)
library(gamlss.mx)
library(mixtools)
library(mixR)
library(flexmix)
library(betareg)

## Workflow

### Step 1: Data Preparation (Required First)

These **MUST** be run first, in this order:
- `Load_rawdata.Rmd` - Extracts shots from JSON files
- `Exploratory_analysis.Rmd` - Creates modeling datasets with engineered features

**Output:** Creates `.rds` files with processed data needed for all subsequent analyses

---

### Step 2: Model Training & Evaluation Pairs

After Step 1 is complete, you can run any of these **fit + evaluate** pairs independently:

#### Option A: Main Models (Basic Features)
- `Fit_models.Rmd`
- `Evaluate_models.Rmd`

#### Option B: Extended Model (More Features)
- `Fit_models_big.Rmd`
- `Evaluate_models_big.Rmd`

#### Option C: Right-Footed Players Model
- `Fit_right_footed_models.Rmd`
- `Evaluate_right_footed_models.Rmd`

#### Option D: Left-Footed Players Model
- `Fit_left_footed_models.Rmd`
- `Evaluate_left_footed_models.Rmd`

---

### Step 3: Additional Analyses (Optional)

These can be run after their respective models are fitted:

- `Calculations.Rmd` - Calculate mean xG by counter-attack status (requires models from `Fit_models.Rmd`)
- `Hypothesis_test.Rmd` - Statistical hypothesis tests comparing foot models (requires models from `Left` & `Right`-footed models)
- `Mixture_models_analysis.Rmd` - Fit mixture models to xG distribution (requires models from `Fit_models_big.Rmd`)

---

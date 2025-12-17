Expected Goals (xG) Modeling - Master Thesis
Overview
This repository contains the complete R code and analysis for our master thesis on Expected Goals (xG) modeling in football.
The project analyzes unblocked shots from the top 5 European leagues (2017-2018 season) using machine learning approaches, particularly Gradient Boosting Machines (GBM) and Generalized Linear Models (GLM).

The H2O package requires Java. To install:
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

Data:
The data comes from the Wyscout dataset containing event-level data from:

English Premier League
French Ligue 1
German Bundesliga
Italian Serie A
Spanish La Liga

Aswell as player data.

The data stem from JSON files, and can be found in the data folder.

Data Processing
Run the scripts in order:

Load_rawdata.Rmd - Extracts shots from JSON files
Exploratory_analysis.Rmd - Creates modeling datasets with engineered features

# Project-2-Energy-Demand-Forecasting

## Repository Overview

This repository contains all code, data processing steps, exploratory analysis, and results for our project. The project examines whether weather patterns can improve short-term regional electricity demand forecasting. The goal of the project is to compare a baseline ARIMA model to an ARIMAX model that includes exogenous weather variables and determine whether weather information improves predictive performance. Our analysis focuses on the Dominion (DOM) load area using hourly PJM electricity demand data and daily NOAA weather observations.

## Software and Platform

### Software
We performed all data cleaning, preprocessing, exploratory analysis, and modeling in a Jupyter Notebook using Python 3.

### Required Packages
The following Python packages are required to run the notebook:
- pandas  
- numpy  
- matplotlib  
- statsmodels  
- scikit-learn  

All packages can be installed via `pip` if they are not already available.

### Platform
- Developed and tested in a cloud-hosted Jupyter Notebook environment  
- Expected to run on Windows, macOS, or Linux without modification  

## Map of the Repository
Below is an outline of the repository structure and its contents:

<pre><code>project-root/
├─ DATA/
│  ├─ hrl_load_metered.csv
│  ├─ 4252944.csv
│  ├─ final_merged_dataset.csv
│  └─ Data_Appendix.pdf
├─ OUTPUT/
│  ├─ hourly_load_over_time.png
│  ├─ daily_load_over_time.png
│  └─ arimax_results.csv
├─ SCRIPTS/
│  └─ DS_4002_Project_2.ipynb
├─ README.md
└─ LICENSE.txt
</code></pre>

## Instructions for Reproducing Results

To reproduce the results of our project, please run each cell in the DS 4002 Project 2 Jupyter Notebook (`DS_4002_Project_2.ipynb`) in the order indicated within the file.

In the event the provided Jupyter Notebook fails to run, take the following steps to reproduce our results:

1. Load `hrl_load_metered.csv` and `4252944.csv` into the runtime as pandas DataFrames.  
2. Filter the PJM load dataset to include only observations where `load_area == "DOM"` so that the analysis focuses on the Dominion region.  
3. Convert the hourly timestamp column in the PJM dataset to datetime format and sort the data chronologically.  
4. Create a daily date key from the hourly timestamp values.  
5. Aggregate the hourly load data to the daily level so it can be aligned with the daily weather data.  
6. Load the NOAA weather dataset and retain the variables used in the analysis, including `PRCP`, `TMIN`, `TMAX`, and `TOBS`.  
7. Convert the weather date column to datetime format and group duplicate daily weather observations by date if needed.  
8. Merge the daily load dataset with the daily weather dataset using the shared date key.  
9. Create any engineered features used in the analysis, including `is_weekend`.  
10. Generate exploratory visualizations, including time-series plots for load, temperature, and precipitation, scatterplots comparing load to weather variables, and a correlation heatmap.  
11. Split the final merged dataset into training and testing sets.  
12. Train a baseline ARIMA model using the electricity demand series alone.  
13. Train an ARIMAX model using weather variables and calendar effects as exogenous predictors.  
14. Evaluate both models using RMSE and MAPE.  
15. Save the final figures, tables, and model-comparison outputs to the `OUTPUT/` folder.  

## License

This repository uses the MIT License. See `LICENSE.txt` for full details.

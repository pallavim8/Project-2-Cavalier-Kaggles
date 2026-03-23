# Project-2-Cavalier-Kaggles

## Repository Overview

This repository contains all code, data processing steps, exploratory analysis, and results for our project. The project examines whether weather patterns can improve short-term regional electricity demand forecasting. The goal of the project is to compare a baseline ARIMA model to an ARIMAX model and regression model that includes exogenous weather variables and determine whether weather information improves predictive performance. Our analysis focuses on the Dominion (DOM) load area using hourly PJM electricity demand data and daily NOAA weather observations.

## Software and Platform

### Software
We performed all data cleaning, preprocessing, exploratory analysis, and modeling in a Jupyter Notebook using Python 3.

### Required Packages
The following Python packages are required to run the notebook:
- pandas  
- numpy  
- matplotlib
- seaborn 
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
│  ├─ Data_Appendix.pdf
│  ├─ final_data.csv
│  ├─ load_data_2024.csv
│  ├─ load_data_2025.csv
│  ├─ load_data_2026.csv
│  └─ weather_data_2024_to_2026.csv
├─ OUTPUT/
│  ├─ arima_graph.png
│  ├─ arimax_graph.png
│  ├─ regression_no_weather_graph.png
│  ├─ regression_with_weather_graph.png
│  └─ sarimax_graph.png
├─ SCRIPTS/
│  └─ DS_4002_Project_2.ipynb
├─ LICENSE.txt
└─ README.md
</code></pre>

## Instructions for Reproducing Results

To reproduce the results of our project, please run each cell in the DS 4002 Project 2 Jupyter Notebook (`DS_4002_Project_2.ipynb`) in the order indicated within the file.

In the event the provided Jupyter Notebook fails to run, take the following steps to reproduce our results:

1. Load `load_data_2024.csv`, `load_data_2025`,`load_data_2026`, and `weather_data_2024_to_2026` into the runtime as pandas DataFrames.  
2. Filter the PJM load dataset to include only observations where `load_area == "DOM"` so that the analysis focuses on the Dominion region.  
3. Convert the hourly timestamp column in the PJM dataset to datetime format and sort the data chronologically.  
4. Create a daily date key from the hourly timestamp values.  
5. Aggregate the hourly load data to the daily level so it can be aligned with the daily weather data.  
6. Load the NOAA weather dataset and retain the variables used in the analysis, including `PRCP`, `TMIN`, and `TMAX`.  
7. Convert the weather date column to datetime format and group duplicate daily weather observations by date if needed.  
8. Merge the daily load dataset with the daily weather dataset using the shared date key.  
9. Create any engineered features used in the analysis, including `hour`,`day_of_week`, and `month` dummy columns.  
10. Generate exploratory visualizations, including time-series plots for load, temperature, and precipitation, scatterplots comparing load to weather variables, and a correlation heatmap.  
11. Split the final merged dataset into training and testing sets.  
12. Train a baseline ARIMA model using the electricity demand series alone.  
13. Train an ARIMAX and a SARIMAX model using weather variables as exogenous predictors.
14. Train a lag-feature regression model both not using and using weather variables as exogenous predictors.
15. Evaluate both models using RMSE, MAPE, and graphical comparison.  
16. Save the final figures, tables, and model-comparison outputs to the `OUTPUT/` folder.  

## License

This repository uses the MIT License. See `LICENSE.txt` for full details.

# Earthquakes Analysis

This repository contains an exploratory analysis of global earthquake events using Python (Pandas, NumPy), Matplotlib for visualization, Cartopy for geographic plotting, and Statsmodels for statistical modeling. The analysis is implemented in the notebook `main.ipynb` and uses the dataset `data.csv`.

Dataset source
- Kaggle: https://www.kaggle.com/datasets/stealthtechnologies/earthquakes-dataset

About the dataset
This dataset contains detailed seismic event records from around the globe. Each row is an earthquake event and the dataset covers multiple regions and timestamps with the following primary features:

- **Date**: The date of the event, formatted as `DD/MM/YYYY`.
- **Time (utc)**: The UTC time when the event was recorded.
- **Region**: The textual region description where the event occurred.
- **Magnitude**: Earthquake magnitude (float).
- **Depth (km)**: Depth of the event in kilometres (integer).
- **Latitude**: Latitude as a string with directional indicator (e.g. `8.01 N`).
- **Longitude**: Longitude as a string with directional indicator (e.g. `125.20 E`).
- **Mode**: Detection mode (`A` = automatic, `M` = manual).

What this project does
- Loads and inspects the raw CSV (`data.csv`) in `main.ipynb`.
- Cleans and standardizes fields:
	- Converts `Date` + `Time (utc)` into a `Datetime` index.
	- Parses `Latitude` and `Longitude` strings into signed numeric values (N/S and E/W handled).
	- Identifies and filters invalid coordinate rows.
- Performs exploratory visualizations:
	- Magnitude and depth distributions (histograms and binned frequency charts).
	- Comparison of auto-detected vs manually-detected magnitudes.
	- Geographic scatter plots and Cartopy-based epicenter maps.
- Conducts correlation and hypothesis testing:
	- Cleans numeric columns, computes correlation matrix.
	- Fits a simple linear regression (Magnitude ~ Depth) using Statsmodels and reports coefficients and p-values.

Key finding (from the notebook)
- After fitting a linear regression of Magnitude on Depth, the slope coefficient is not statistically significant at the 5% level (p-value = 0.44). In other words, no statistically significant linear relationship between magnitude and depth was found at alpha = 0.05.

Requirements
- Python 3.8+ (recommended)
- Core Python packages used in the notebook:
	- `pandas`, `numpy`, `matplotlib`, `statsmodels`, `cartopy`

Installation hints
- Simple pip install (may work for most packages):

	```powershell
	pip install pandas numpy matplotlib statsmodels jupyterlab
	```

- `cartopy` can be more difficult to install on Windows because it depends on geospatial C libraries. If you use `conda` (recommended) run:

	```powershell
	conda install -c conda-forge cartopy
	```

Usage
- Open the notebook `main.ipynb` with Jupyter, JupyterLab, or VS Code and run the cells sequentially.
- The notebook demonstrates the full analysis workflow: data loading, cleaning, visualizations, mapping, and statistical testing.

Files
- `data.csv` — raw dataset used by the notebook.
- `main.ipynb` — analysis notebook with code and visualizations.
- `README.md` — this file.
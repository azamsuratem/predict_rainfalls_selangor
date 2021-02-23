# Predicting Rainfalls in Selangor, Malaysia using ARIMA Forecasting
This Jupyter Notebook, using Python 3 environment is to carry out prediction analysis on the rainfalls projected for the Selangor state in Malaysia from the time period of 1st Jan 2014 (2014-01-01) till 31st Dec 2020 (2020-12-31).

The prediction analysis is made using <ins>Auto-Regressive Integrated Moving Average (ARIMA) forecasting</ins> for the time period of 730 days, starting from 1st Jan 2021 (2021-01-01) till 31st Dec 2022 (2022-12-31).
<br><br>

## Source for the Data
The data are extracted from the open data registry <b>Portal Data Terbuka Malaysia</b> via [data.gov.my](https://www.data.gov.my) as follows:
1. Method 1 (CCSM): [Daily Projected Rainfall for Scenario CCSM3A1FI by State in Peninsular Malaysia](https://www.data.gov.my/data/ms_MY/dataset/daily-projected-rainfall-for-scenario-ccsm3a1fi-by-state-in-peninsular-malaysia)
2. Method 2 (ECHM): [Daily Projected Rainfall for Scenario ECHM5A1B2 by State in Peninsular Malaysia](https://www.data.gov.my/data/ms_MY/dataset/daily-projected-rainfall-for-scenario-echm5a1b2-by-state-in-peninsular-malaysia)
3. Method 3 (MRIB): [Daily Projected Rainfall for Scenario MRIB1 by State in Peninsular Malaysia](https://www.data.gov.my/data/ms_MY/dataset/daily-projected-rainfall-for-scenario-mrib1-by-state-in-peninsular-malaysia)

<b>REMINDER:</b> To run this Notebook in your local machine, you need to <ins>download all 3 CSV files</ins> stored in the `data` folder of this repository.
<br><br>

## Summary on the Notebook
- Data of `rainfalls` are extracted via Pandas command `read_csv()` from the CSV files downloaded in the links mentioned in the above section <b>Source for the Data</b>.
- A single dataframe `rainfalls_Selangor` is created to store these extracted data with categorical value of `Selangor` in the column `State`.
- Extracted data are initially visualized using Matplotlib `.plot(kind="line")` for Time Series plots and Seaborn `boxplot` for Boxplots.
> Time Series plots on the `rainfalls_Selangor`:
![Time series `rainfalls_Selangor`, before](images/Time_Series_Rainfalls_Selangor_before.png?raw=true)
> 
> Boxplots on the `rainfalls_Selangor`:
![Boxplots `rainfalls_Selangor`, before](images/Boxplot_Rainfalls_Selangor_before.png?raw=true)
- Outliers, as detected in the initial visualization above are replaced by <ins>imputation with the median values</ins> of each corresponding data. Then, the edited data are visualized again using the same tools as above.
> Time Series plots on the `rainfalls_Selangor` after dealing with outliers:
![Time series `rainfalls_Selangor`, after](images/Time_Series_Rainfalls_Selangor_after.png?raw=true)
> 
> Boxplots on the `rainfalls_Selangor` after dealing with outliers:
![Boxplots `rainfalls_Selangor`, after](images/Boxplot_Rainfalls_Selangor_after.png?raw=true)
- Exploratory Data Analysis (EDA) on the Time Series Data is conducted to prepare for the ARIMA model construction:
> - Seasonal Decomposition plots
> - Time Series plots with Rolling Mean & Rolling Std. Dev.
> - Augmented Dickey-Fuller (ADF) Test
> - Regular Differencing for achieving Stationarity
> - Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots
- ARIMA Models are constructed and tested using selected statistical tests:
> - Mean Abs. Error, MAE
> - Root MEan Sq. Error, RMSE
> - Paired t-test with reliability benchmark of p-value &le; 0.05
> - F-statistics with reliability benchmark of p-value &le; 0.05
- Constructed ARIMA models are then used for visualizing the prediction plots:
![Prediction, Method_1_CCSM](images/Predicted_Rainfalls_Selangor_Method_1_CCSM.png?raw=true)
![Prediction, Method_2_ECHM](images/Predicted_Rainfalls_Selangor_Method_2_ECHM.png?raw=true)
![Prediction, Method_3_MRIB](images/Predicted_Rainfalls_Selangor_Method_3_MRIB.png?raw=true)
<br><br>


## References
This Notebook was made possible thanks to these external sources especially on the Python codes to execute the following sections:

- Matplotlib and Seaborn visualizations:
> - Kaggle.com Notebook entry <b>Data Visualization Analysis</b> by `@kshitijmohan` | [Link](https://www.kaggle.com/kshitijmohan/data-visualization-analysis)
> - Kaggle.com Notebook entry <b>Basic of Statistical Viz : Plotly & Seaborn</b> by Subin An | [Link](https://www.kaggle.com/subinium/basic-of-statistical-viz-plotly-seaborn)

- Outliers detection and dealing with them:
> - Kaggle.com Discussion entry <b>Outlier Detection - ASHRAE Way</b> by Gunes Evitan | [Link](https://www.kaggle.com/c/ashrae-energy-prediction/discussion/122471)
> - Kaggle.com Notebook entry <b>Outlier!!! The Silent Killer</b> by `@nareshbhat` | [Link](https://www.kaggle.com/nareshbhat/outlier-the-silent-killer)

- Hypothesis Testing and p-value for validating tests and models:
> - Kaggle.com Notebook entry <b>Hypothesis test and p-values</b> by John Ostrowski | [Link](https://www.kaggle.com/ostrowski/hypothesis-test-and-p-values)
> - Blog entry <b>Hypothesis Test for Comparing Machine Learning Algorithms</b> by Jason Brownlee | [Link](https://machinelearningmastery.com/hypothesis-test-for-comparing-machine-learning-algorithms/)

- Time Series Forecasting using ARIMA:
> - Kaggle.com Notebook entry <b>Intro to Time Series Forecasting</b> by `@iamleonie` | [Link](https://www.kaggle.com/iamleonie/intro-to-time-series-forecasting)
> - Blog entry <b>4 Common Machine Learning Data Transforms for Time Series Forecasting</b> by Jason Brownlee | [Link](https://machinelearningmastery.com/machine-learning-data-transforms-for-time-series-forecasting/)
> - Tutorials on <b>Identifying the order of differencing in ARIMA models</b> by Robert Nau | [Link](https://people.duke.edu/~rnau/411arim2.htm)
> - Kaggle.com Notebook entry <b>Bitcoin Price. Prediction by ARIMA</b> by `@myonin` | [Link](https://www.kaggle.com/myonin/bitcoin-price-prediction-by-arima)
> - scikit-learn Online Documentation on <b>`sklearn.preprocessing.PowerTransformer`</b> | [Link](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.PowerTransformer.html)


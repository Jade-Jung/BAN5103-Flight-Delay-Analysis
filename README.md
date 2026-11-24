
# BAN5103-Flight-Delay-Analysis

## Project Overview

This project was developed for BAN 5103: Introduction to Statistics
at the University of Texas at San Antonio (UTSA).

The project analyzes flight arrival delays at three major New York
City airports using 2013 flight and weather data.

## Research Question

How are season, airline, scheduled departure time, flight distance,
and weather conditions associated with flight arrival delays at
major New York City airports?

## Dataset

The data comes from the nycflights13 dataset and includes:

- Flight records
- Hourly weather observations
- Airline information
- Three NYC airports: JFK, LGA, and EWR

The original flight dataset contains 336,776 observations.
After data cleaning, 327,346 flights with recorded arrival
delays were retained for analysis.

## Project Structure

### Milestone 3: Exploratory Data Analysis

The notebooks in the main project folder cover:

- Data acquisition
- Data profiling
- Data cleaning
- Summary statistics
- Exploratory data visualization
- Data quality documentation

### Milestone 4: Statistical Analysis

The statistical analysis notebooks are located in:

```text
milestone4_statistical_analysis/
├── 01_seasonal_anova.ipynb
├── 02_flight_only_regression.ipynb
├── 03_weather_regression.ipynb
└── 04_model_validation.ipynb
```

| Notebook | Description |
|---|---|
| 01_seasonal_anova | Seasonal comparisons using Welch's ANOVA, pairwise tests, and effect size analysis |
| 02_flight_only_regression | Multiple linear regression using flight-related variables |
| 03_weather_regression | Multiple linear regression including weather variables and model comparison |
| 04_model_validation | Missing data analysis, distribution checks, outlier sensitivity, and out-of-sample evaluation |

## Statistical Methods

- Descriptive statistics and data visualization
- Welch's one-way ANOVA
- Pairwise Welch's t-tests with Bonferroni correction
- Multiple linear regression
- Variance Inflation Factor (VIF)
- Breusch-Pagan test
- HC3 heteroskedasticity-robust standard errors
- Outlier sensitivity analysis
- Date-grouped training and testing split
- Model evaluation using R-squared, MAE, and RMSE

## Key Findings

### Seasonal Differences

Average arrival delays differ significantly across seasons.

| Season | Average Arrival Delay (minutes) |
|---|---:|
| Winter | 9.04 |
| Spring | 6.81 |
| Summer | 12.99 |
| Fall | -1.22 |

Summer has the highest average arrival delay, while Fall has
the lowest. However, the seasonal effect size is small,
suggesting that season alone explains only a limited portion
of the variation in arrival delays.

### Regression Analysis

Both regression models were compared using the same
291,140 complete-case observations.

| Model | R-squared |
|---|---:|
| Flight-only model | 0.0540 |
| Flight and weather model | 0.0797 |

Adding weather variables improves the model's explanatory
power, although a large portion of the variation in arrival
delays remains unexplained.

### Model Validation

Additional validation was conducted to evaluate the reliability
of the statistical results.

- Missing Data: Flights excluded from the complete-case analysis
  were examined to identify potential selection bias.
- Data Distribution: Arrival delays are strongly right-skewed.
- Outliers: Extreme delays were retained in the main analysis
  because they may represent actual flight disruptions.
- Sensitivity Analysis: Regression results were compared with
  and without IQR-based outliers.
- Predictive Performance: Both models were evaluated on the
  same held-out test observations using a date-grouped split.

The weather model provides additional predictive value, but
neither model is sufficient for highly accurate individual
flight delay predictions.

## Limitations

- The dataset covers only NYC flights in 2013.
- Missing weather observations may introduce selection bias.
- Extreme delays affect the magnitude of regression coefficients.
- Flights may share weather and operational conditions.
- Important operational factors, such as air traffic congestion
  and aircraft maintenance, are not included in the models.
- Observed weather conditions may not always be available
  at the time a prediction is made.
- Statistical associations do not establish causation.

## Tools and Libraries

- Python 3.12
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- seaborn
- SciPy
- statsmodels
- scikit-learn

## How to Run

1. Clone or download the repository.
2. Create and activate a Python virtual environment.
3. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn jupyter
   ```

4. Run the data acquisition and cleaning notebooks if the
   cleaned dataset is not already available.
5. Open the milestone4_statistical_analysis folder.
6. Run the four statistical analysis notebooks in numerical order.

## Conclusion

Season, flight characteristics, and weather conditions are
associated with arrival delays. Including weather information
improves model performance, but the relatively low R-squared
values indicate that additional factors are needed to better
explain and predict flight delays.

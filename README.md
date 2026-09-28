# Predicting Crop Yield in Maji Ndogo with Linear Regression

A simple linear regression project that tests whether pollution level or average temperature can predict crop yield on farms in Maji Ndogo.

## Question
Can a single environmental factor predict `Standard_yield` for a farm field?

## What I did
- Loaded and cleaned survey data from a SQL database (5,654 fields) using a custom processing module
- Validated the cleaned data with automated pytest checks
- Compared temperature and pollution against yield using scatter plots and Pearson correlation
- Fitted a linear regression model and evaluated it with R², MAE, MSE and RMSE
- Used an 80/20 train-test split to measure performance on unseen data
- Checked the residuals (histogram, residuals vs predictions, mean and standard deviation)

## Results
| | Correlation with yield |
|---|---|
| Average temperature | 0.007 |
| Pollution level | -0.286 |

Pollution model on the test set: R² = 0.081, MAE = 0.088, RMSE = 0.111.

Pollution has a weak negative relationship with yield and explains about 8% of its variation. The model is unbiased on average, but its errors are about as large as the natural spread of yield, so one feature is not enough. Next steps: multiple regression, per-crop models, and non-linear models.

## Files
| File | Purpose |
|---|---|
| `Maji_Ndogo_Crop_Yield_Regression.ipynb` | The full analysis |
| `Maji_Ndogo_farm_survey_small.db` | Survey database |
| `data_ingestion.py` | Database and CSV loading helpers |
| `field_data_processor.py` | Data cleaning pipeline |
| `validate_data.py` | Data quality tests |

## How to run
```
pip install -r requirements.txt
jupyter notebook Maji_Ndogo_Crop_Yield_Regression.ipynb
```
Run the notebook top to bottom. An internet connection is needed for the weather-station mapping file.

## Data source
Maji Ndogo farm survey data provided through ExploreAI Academy coursework.

# Weather Prediction | Belgium Campus
A group project completed for the **MLG382 Machine Learning module** at Belgium Campus ITversity.

This project explores how machine learning can estimate weather conditions from atmospheric data and present results through an interactive Dash application.

## Project Overview
The project uses historical weather observations from **Toronto Pearson Airport, Canada, for 2012**. The dataset described in the technical report contains **8,784 hourly observations**.

The work covers data exploration, preparation, model training, evaluation and application development.

## Features
- Temperature estimation.
- Rain and snow occurrence classification.
- High-visibility classification.
- An interactive Dash interface for entering atmospheric conditions and viewing predictions.
- A training notebook, saved models and supporting technical documentation.

The training materials also cover wind speed and pressure, although these predictions are not displayed in the current application.

## Technology Stack
Python · pandas · NumPy · scikit-learn · joblib · Jupyter Notebook · Dash · Gunicorn

## Repository Structure
| File or folder | Description |
|---|---|
| `app.py` | Interactive weather prediction application |
| `ModelTraining.ipynb` | Model training and evaluation notebook |
| `models/` | Saved model files |
| `requirements.txt` | Application dependencies |
| `Procfile` | Gunicorn startup configuration |
| `docs/` | Technical report, evaluation results and model-selection notes |

## Models
| Prediction target | Approach in the supplied training notebook |
|---|---|
| Temperature | Gradient Boosting Regressor |
| Rain occurrence | Gradient Boosting Classifier |
| Snow occurrence | Gradient Boosting Classifier |
| High visibility | Gradient Boosting Classifier |
| Wind speed | Random Forest Regressor |
| Atmospheric pressure | Random Forest Regressor |

The technical report describes a later HistGradientBoosting approach for wind speed and pressure. The notebook and report therefore reflect different development stages.

## Run Locally
Place the saved model files in a `models` folder beside `app.py`. The application expects these filenames:

- `temperature_forecast_model.pkl`
- `rain_classifier.pkl`
- `snow_classifier.pkl`
- `high_visibility_classifier.pkl`

Install the dependencies:
```bash
python -m pip install -r requirements.txt
```

Start the application:
```bash
python app.py
```

Open **http://localhost:8050** in your browser.

## Training and Evaluation
The notebook uses a chronological training and testing split. Regression models are evaluated using error metrics, while classification models are evaluated using precision, recall, F1-score and related measures.
The training notebook expects `Cleaned1_WeatherDataset.csv`, which is not included in the current project materials. Reproducing training requires this dataset and its preprocessing steps.
The recorded temperature errors are in scaled units, rather than degrees Celsius. Class imbalance also affects interpretation of classification accuracy, particularly for snow and high visibility.

## Limitations and Future Improvements
- The dataset represents one location and one year.
- The application estimates conditions from supplied inputs; it does not retrieve live weather data or define a future forecast horizon.
- Scaling parameters are hardcoded in the application rather than stored in a preprocessing pipeline.
- Dependencies are unpinned, so loading saved models may require compatible library versions.
- Future improvements include documenting the complete preprocessing workflow, addressing class imbalance and evaluating data from additional years and locations.

## Academic Context
This repository contains university group coursework shared for portfolio demonstration. The materials represent combined group work.

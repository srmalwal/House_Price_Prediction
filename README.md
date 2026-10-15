# House_Price_Prediction

A machine learning web application that estimates house prices from property details. The project uses a **Decision Tree Regressor** and a **Streamlit** interface to accept user inputs and display an estimated price in lakhs.

## Features

- Predicts estimated house prices from property characteristics.
- Accepts location, property type, size, age, amenities, and nearby-facility information.
- Encodes ordinal features with a saved `OrdinalEncoder`.
- Converts input features using a saved `DictVectorizer`.
- Loads the trained model and preprocessing artifacts from Pickle files.
- Provides an interactive Streamlit interface.

## Tech Stack

- Python
- Pandas and NumPy
- Scikit-learn
- Matplotlib and Seaborn for notebook exploration
- Streamlit
- Pickle

## Model

The training notebook explores regression approaches, including Linear Regression and Decision Tree Regression. The saved prediction model is a `DecisionTreeRegressor` configured with `max_depth=10` and `random_state=42`.

The notebook samples 40% of the available rows for model training and evaluates the model using:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² score

Refer to the notebook outputs for the measured scores; no performance value is assumed here.

## Dataset

The dataset file is `E06_house price data less.csv`. The target column is `Price_in_Lakhs`. The notebook drops the `ID` and `Locality` columns, encodes selected ordinal fields, and lowercases string values for consistency.

The app collects property information such as:

- State and city
- Property type and BHK
- Size and price per square foot
- Year built and property age
- Furnishing status
- Floor number and total floors
- Nearby schools and hospitals
- Public transport accessibility
- Parking and security
- Amenities
- Facing
- Owner type
- Availability status

Predictions are estimates and should not be treated as official property valuations.

## Repository Structure

```text
house_price_prediction/
├── app.py
├── E06_house price data less.csv
├── E06_House Price Prediction.ipynb
├── house_price_model.pkl
├── vectorizer.pkl
├── encoder.pkl
├── features.pkl
└── README.md
```

Rename the uploaded application Python file to `app.py` in the repository, or adjust the run command to use its actual filename.

## Installation

Install the dependencies with:

```bash
pip install streamlit pandas numpy scikit-learn matplotlib seaborn jupyter
```

## Run the Application

Keep `app.py` and all four `.pkl` files in the same directory, then run:

```bash
streamlit run app.py
```

Streamlit will print a local URL in the terminal. Open that URL in your browser.

## How It Works

1. The user enters property details in the Streamlit interface.
2. The app ordinal-encodes selected fields using `encoder.pkl`.
3. The input dictionary is transformed into model features using `vectorizer.pkl`.
4. `house_price_model.pkl` predicts the price.
5. The estimated price is displayed in lakhs of rupees.

## Project Files

| File | Purpose |
|---|---|
| `app.py` | Streamlit interface and prediction logic |
| `E06_house price data less.csv` | House price dataset |
| `E06_House Price Prediction.ipynb` | Data exploration, preprocessing, training, and evaluation |
| `house_price_model.pkl` | Trained Decision Tree regression model |
| `vectorizer.pkl` | Saved `DictVectorizer` for input features |
| `encoder.pkl` | Saved `OrdinalEncoder` for ordinal fields |
| `features.pkl` | Saved feature-name list from training |
| `README.md` | Project documentation |

**Important:** Keep the preprocessing artifacts consistent with the model trained with them. Only load Pickle files from trusted sources.

## Limitations

- Prediction quality depends on the training data and its coverage of locations and property types.
- Real estate prices change over time and can vary significantly within the same city.
- The result is a model estimate and does not replace a professional valuation.
- The app's input options and preprocessing must match the feature formats used during training.

## Future Improvements

- Report evaluation scores and compare models in the interface.
- Add validation for missing or inconsistent inputs.
- Expand and update the dataset with reliable market data.
- Tune model hyperparameters using cross-validation.
- Add prediction ranges and explain influential features.
- Deploy the app to a hosting platform.

## Conclusion

`house_price_prediction` demonstrates a regression workflow covering dataset exploration, preprocessing, model training and evaluation, saving trained artifacts, and serving predictions through a Streamlit application.

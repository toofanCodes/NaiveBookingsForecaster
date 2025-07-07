# Airline Booking Demand Forecasting

**Team:** Saran | Sanskriti | Vanessa | Abhinav

## Objective

The goal of this project is to develop a simple, interpretable forecast model for airline bookings that minimizes the Mean Absolute Scaled Error (MASE) compared to a naïve baseline. We focus on analytics and business logic, not machine learning, to keep the approach transparent and practical.

## Data Description

We use two datasets:
- **Training (sample):** Cumulative bookings for various departure dates, with each departure having a record of 60 prior days' bookings.
- **Validation:** Similar structure, used to test our forecasting logic.

## Approach

### 1. Exploratory Data Analysis (EDA)
- We start by checking for missing values and understanding the distribution of bookings.
- Visualizations show how bookings vary by day of week and by days prior to departure.

### 2. Feature Engineering
- We extract features like `day_of_week` and `DaysToDepart` (as a numeric value).
- For each departure, we calculate the final demand (bookings on the day of departure), remaining demand, and booking rate.

### 3. Forecasting Models
- **Additive Model:** Forecast = cumulative bookings + mean remaining demand (from training data).
- **Multiplicative Model:** Forecast = cumulative bookings / mean booking rate (from training data).
- Both models are run in two ways: by days prior only, and by days prior + day of week.
- **Weighted Average:** We also try a weighted average of the two models, tuning the weight to minimize MASE.

### 4. Evaluation
- We use MASE as our main metric, comparing each model's forecast to the naïve forecast provided in the validation set.
- The notebook prints out MASE scores for all approaches and highlights the best result.

### 5. Visualization
- The notebook includes plots for EDA and for comparing actual vs. forecasted demand for a sample departure date.

## How to Run

1. Make sure you have Python 3 installed.
2. Install all dependencies with:
   ```
   pip install -r requirements.txt
   ```
3. Place `airline_data_training.csv` and `airline_data_validation.csv` in the project directory.
4. Open `ForecastFlightBookings.ipynb` in Jupyter Notebook or VS Code.
5. Run the notebook cells in order. You'll see EDA, model results, and visualizations.

## Notes

- This project is intentionally simple and transparent—no machine learning, just analytics and business logic.
- The code is well-commented and organized for clarity.
- If you want to extend the analysis, you can add more features, try other error metrics, or experiment with different weighting schemes.

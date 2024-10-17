# Covid-19 Visualization and Prediction

This repository contains a Python notebook (`Covid.ipynb`) for visualizing and predicting COVID-19 cases in India. It leverages various Python libraries like **pandas**, **matplotlib**, **seaborn**, **plotly**, and **scikit-learn** for data processing, visualization, and predictive modeling.

## Overview

The goal of this project is to:
1. Visualize the COVID-19 trends in India over time.
2. Predict the number of confirmed cases, deaths, and recoveries using a **Linear Regression** model.
3. Provide an interactive prediction feature where users can input a date to get the forecasted COVID-19 cases for that day.

## Features

- **Data Loading and Cleaning**: The dataset is loaded, and unnecessary columns are dropped. The relevant columns like confirmed cases, deaths, and recoveries are selected and processed for analysis.
- **Visualization**: The data is visualized using various plots:
  - Bar plots showing confirmed vs recovered cases in each state.
  - Line charts showing the trends of confirmed, cured, and death cases over time in selected states and for the entire country.
- **Prediction**: A Linear Regression model predicts the confirmed cases, deaths, and cured cases for future dates based on the historical data.
- **User Interaction**: Users can input a future date, and the system will predict the COVID-19 cases for that date.

## Technologies

- **Python**: The primary programming language used for analysis.
- **pandas**: For data manipulation and cleaning.
- **matplotlib & seaborn**: For data visualization and plotting.
- **Plotly**: For interactive visualizations.
- **scikit-learn**: For Linear Regression model building.

## Dataset

The dataset used for this analysis is **India's COVID-19 case data**, which includes columns like:
- `Date`: The date of the record.
- `State/UnionTerritory`: The state or territory in India.
- `ConfirmedIndianNational`: Number of confirmed cases among Indian nationals.
- `ConfirmedForeignNational`: Number of confirmed cases among foreign nationals.
- `Cured`: Number of people who have recovered.
- `Deaths`: Number of deaths due to COVID-19.

## Setup

### 1. Clone the repository

You can clone the repository to your local machine using the following command:

```bash
git clone https://github.com/riteshranjansah/Covid-19-visualization-and-prediction.git
```

### 2. Install required libraries

Make sure you have Python installed on your system. Then install the necessary Python libraries using `pip`:

```bash
pip install pandas matplotlib seaborn plotly scikit-learn
```

### 3. Open the Jupyter Notebook

Navigate to the repository folder, and open the `Covid.ipynb` notebook using Jupyter Notebook:

```bash
jupyter notebook Covid.ipynb
```

### 4. Run the Code

Execute the cells in the notebook sequentially to load the data, perform visualization, and run the prediction model.

## Usage

1. **Data Visualization**:
   - The notebook visualizes the number of confirmed cases, recoveries, and deaths in each state using bar plots.
   - It also shows the cumulative trends of confirmed, recovered, and deceased cases over time using line plots.

2. **Prediction Model**:
   - The notebook uses **Linear Regression** to predict future confirmed cases, deaths, and recoveries.
   - You can enter a specific date (in `yyyy-mm-dd` format) and get predictions for that day.

3. **Interactive Predictions**:
   - When prompted, enter the date in the format `yyyy-mm-dd`.
   - The model will calculate and print the predicted number of confirmed cases, deaths, and recoveries for that date.

### Example:

When prompted to enter a date:

```python
Enter the Date (yyyy-mm-dd): 2020-12-25
```

The system predicts:

```python
Predicted Confirmed Cases: 8458446.242359161
Predicted Deaths Cases: 130899.04456561804
Predicted Cured Cases: 7447520.636955261
```

## Code Walkthrough

### 1. Data Loading and Preprocessing

The dataset is read from a CSV file (`covid_19_india.csv`) using `pandas`. The dataset contains columns for date, state, confirmed cases, deaths, and recoveries. 

```python
df = pd.read_csv('covid_19_india.csv', parse_dates=['Date'], dayfirst=True)
df = df[['Date','State/UnionTerritory','Cured','Deaths','Confirmed']]
df.columns = ['date','state','cured','deaths','confirmed']
```

### 2. Data Visualization

Data is visualized using **seaborn** and **plotly**. The trends in confirmed cases, recoveries, and deaths are plotted across different states.

```python
sns.barplot(x="confirmed", y="state", data=data, label="Confirmed Cases", color="r")
sns.barplot(x="cured", y="state", data=data, label="Recovered", color="g")
```

### 3. Linear Regression Model

The notebook builds three separate linear regression models to predict the future confirmed cases, deaths, and recoveries based on the historical data.

```python
x = tdf['date']
y = tdf['confirmed']
lrc.fit(np.array(x_train).reshape(-1,1), np.array(y_train).reshape(-1,1))
```

### 4. Date-Based Prediction

The user is prompted to input a specific date in the format `yyyy-mm-dd`. The system calculates how many days from the last date (9th December, 2020) the user’s input is, and makes predictions using the trained model.

```python
dy = delta.days
print('Predicted Confirmed Cases:', lrc.predict(np.array([[737768 + dy]]))[0][0])
```

## Example Output

1. **Total Confirmed Cases in India**: The number of confirmed cases is shown for each state.
2. **Active Cases**: Active cases are calculated as the difference between total confirmed cases and the sum of deaths and recoveries.
3. **Future Predictions**: For a user-provided date, the predicted number of confirmed cases, deaths, and recoveries are shown.

```python
Predicted Confirmed Cases: 8458446.242359161
Predicted Deaths Cases: 130899.04456561804
Predicted Cured Cases: 7447520.636955261
```

## Notes

- Make sure the dataset file `covid_19_india.csv` is present in the same directory as the notebook.
- The predictions are based on the **Linear Regression** model and may not be highly accurate for long-term predictions as it assumes linear growth.
  
## License

This project is open-source and available for personal use and modification. No formal license has been applied, so feel free to use or modify the code as per your needs.

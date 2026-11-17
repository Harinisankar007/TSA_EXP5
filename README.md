# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 11/11/2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### DATASET:
DailyDelhiClimateTrain.csv

### SOFTWARE REQUIRED:
Jupyter Notebook

### PROGRAM:
```python


# Import libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset
data = pd.read_csv('DailyDelhiClimateTrain.csv')

# Convert date column into datetime format
data['date'] = pd.to_datetime(data['date'])

# Set date as index
data.set_index('date', inplace=True)

# Sort dates
data = data.sort_index()

# Step 2: Select temperature column
data = data[['meantemp']]

# Handle missing values
data['meantemp'] = data['meantemp'].interpolate()

# Step 3: Perform seasonal decomposition
decomposition = seasonal_decompose(
    data['meantemp'],
    model='additive',
    period=365
)

# Step 4: Plot all four graphs
plt.figure(figsize=(12, 12))

# Original Data
plt.subplot(411)
plt.plot(data['meantemp'], label='Daily Temperature')
plt.legend(loc='upper left')
plt.title('Original Daily Temperature')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonal Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

# Display graphs
plt.tight_layout()
plt.show()
```


### OUTPUT:
Original Daily Temperature:

<img width="837" height="216" alt="image" src="https://github.com/user-attachments/assets/7f6c6a22-5f04-41ef-8979-721132a073f5" />

Trend Plot:

<img width="842" height="215" alt="image" src="https://github.com/user-attachments/assets/99f7343d-9732-4446-a375-238e2c288bf1" />

Seasonal Plot:

<img width="819" height="212" alt="image" src="https://github.com/user-attachments/assets/44d7fbb2-1c0c-4428-8d17-7b4855f85c28" />

Residual Plot:

<img width="825" height="222" alt="image" src="https://github.com/user-attachments/assets/89884671-69d7-4379-8183-964cac248cf4" />


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.

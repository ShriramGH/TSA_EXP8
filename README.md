### Developed by: Shriram S
### Reg no: 212222240098
### Date:
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
 


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python on Methi Vegetable Price.
.
### ALGORITHM:
1. Import necessary libraries
2. Read the vegetable price data from a CSV file,Display the shape and the first 5 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```python
# Import necessary libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Suppress warnings
warnings.filterwarnings('ignore')

# Read the dataset (adjust the path accordingly)
data = pd.read_csv('prices.csv')

# Convert 'Date' to datetime format and set it as the index
data['Price Dates'] = pd.to_datetime(data['Price Dates'], format='%d-%m-%Y')
data.set_index('Price Dates', inplace=True)

# Focus on the 'Adj Close' column
adj_close_data = data[['Methi']]

# Display the shape and the first 5 rows of the dataset
print("Shape of the dataset:", adj_close_data.shape)
print("First 5 rows of the dataset:")
print(adj_close_data.head())

# Plot Original Dataset (Adj Close Data)
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Methi'], label='Original Adj Close Data', color='blue')
plt.title('Annual Change of Methi Price')
plt.xlabel('Date')
plt.ylabel('Annual Change)')
plt.legend()
plt.grid()
plt.show()

# Moving Average
# Perform rolling average transformation with a window size of 10
rolling_mean_10 = adj_close_data['Methi'].rolling(window=10).mean()

# Plot Moving Average
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Methi'], label='Original Adj Close Data', color='blue')
plt.plot(rolling_mean_10, label='Moving Average (window=10)', color='orange')
plt.title('Moving Average of Methi Price')
plt.xlabel('Date')
plt.ylabel('Annual Change')
plt.legend()
plt.grid()
plt.show()

# Exponential Smoothing
model = ExponentialSmoothing(adj_close_data['Methi'], trend='add', seasonal=None)
model_fit = model.fit()

# Make predictions for the next 30 periods (you can adjust this)
predictions = model_fit.predict(start=len(adj_close_data), end=len(adj_close_data) + 30)

# Plot the original data and Exponential Smoothing predictions
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Methi'], label='Original Adj Close Data', color='blue')
plt.plot(predictions, label='Exponential Smoothing Forecast', color='orange')
plt.title('Exponential Smoothing Predictions for Methi Price')
plt.xlabel('Date')
plt.ylabel('Annual Change')
plt.legend()
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()
```

### OUTPUT:

![image](https://github.com/user-attachments/assets/23e1e93d-09a5-4178-950b-edc837b5f2c9)


#### Moving Average

![image](https://github.com/user-attachments/assets/d473d561-b41a-4b42-856b-37f0952aecc0)

#### Plot Transform Dataset

![image](https://github.com/user-attachments/assets/5789bd4e-8b1e-4d42-95a8-50a96a82cc1c)


#### Exponential Smoothing

![image](https://github.com/user-attachments/assets/e8ad3cb9-9602-4943-9227-b86b1771cac1)


### RESULT:
Thus , successful implemention of the Moving Average Model and Exponential smoothing using python is done.

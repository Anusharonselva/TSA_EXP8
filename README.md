![Screenshot 2024-10-16 141758](https://github.com/user-attachments/assets/379da11e-d37e-46fc-96ac-eaf5bac0d799)# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 
### Developed by: ANUSHARON.S
### Registration no.: 212222240010

### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
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
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.api import SimpleExpSmoothing

warnings.filterwarnings("ignore")
import pandas as pd
import numpy as np

date_range = pd.date_range(start='2020-01-01', periods=1000, freq='D')

electricity_values = np.random.randint(200, 500, size=len(date_range))

electricity_df = pd.DataFrame({'date': date_range, 'Value': electricity_values})

electricity_df.to_csv('electricity_data.csv', index=False)

df = pd.read_csv('/content/electricity_data.csv', parse_dates=['date'], index_col='date')

print(df.shape)
print(df.head(20))
plt.figure(figsize=(12, 6))
plt.plot(df['Value'][:50], label='Original Data')
plt.title('First 50 Values of the Time Series Data')
plt.xlabel('Time')
plt.ylabel('Value')
plt.legend()
plt.show()
rolling_mean_5 = df['Value'].rolling(window=5).mean()

print(rolling_mean_5.head(10))
rolling_mean_10 = df['Value'].rolling(window=10).mean()
plt.figure(figsize=(12, 6))

plt.plot(df['Value'], label='Original Data')
plt.plot(rolling_mean_5, color='red', label='Rolling Mean (Window=5)')
plt.plot(rolling_mean_10, color='green', label='Rolling Mean (Window=10)')
plt.title('Original Data and Moving Averages')
plt.xlabel('Time')
plt.ylabel('Value')
plt.legend()
plt.show()
model = SimpleExpSmoothing(df['Value']).fit(smoothing_level=0.2, optimized=False)
exp_smoothing = model.fittedvalues

plt.figure(figsize=(12, 6))
plt.plot(df['Value'], label='Original Data')
plt.plot(exp_smoothing, color='orange', label='Exponential Smoothing (Alpha=0.2)')
plt.title('Original Data and Exponential Smoothing')
plt.xlabel('Time')
plt.ylabel('Value')
plt.legend()
plt.show()
```
### OUTPUT:

## Moving Average
![Screenshot 2024-10-16 141701](https://github.com/user-attachments/assets/4c7b2ada-8854-4e8b-b414-cbadc3cc23bd)

## Plot Transform Dataset
![Screenshot 2024-10-16 141823](https://github.com/user-attachments/assets/36db7af2-ee0b-464e-b59f-e9c0b3f53648)

## Exponential Smoothing
![Screenshot 2024-10-16 141823](https://github.com/user-attachments/assets/48d1f5a8-ec3d-4ad1-a651-c63ea7d2ff13)



### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.

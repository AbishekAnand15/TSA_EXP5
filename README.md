### Developed By : Abishek Xavier A
### Reg. NO . 212222230004
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:

To Illustrates how to perform time series analysis and decomposition on the Sales for furniture store data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


```py

# Importing the required libraries
import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

# Load the dataset (replace with the correct path to your file)
df = pd.read_csv('/content/Super_Store_data.csv',encoding='ISO-8859-1')

# Display the first 5 rows of the dataset
print("First 5 Rows of the dataset:")
print(df.head())

# Converting the 'Order_Date' column to datetime and setting it as the index
df['Order_Date'] = pd.to_datetime(df['Order Date'])  # Adjust format if needed
df = df.set_index('Order_Date')

# Filling missing values for the 'Sales' column (if any) using forward fill
df.fillna(method='ffill', inplace=True)

# Performing seasonal decomposition on the 'Sales' column (additive model)
decomposition = seasonal_decompose(df['Sales'], model='additive', period=7)

# Plot and save each component separately with different colors

# Plot and save the observed (original) data
plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='red')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_sales_plot.png')
plt.show()

# Plot and save the trend component
plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='blue')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_sales_plot.png')
plt.show()

# Plot and save the seasonal component
plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='black')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_sales_plot.png')
plt.show()

# Plot and save the residual component
plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_sales_plot.png')
plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:

![Screenshot 2024-09-23 102826](https://github.com/user-attachments/assets/313196c8-defb-442f-a492-c1069e2f2810)

#### SEASONAL PLOT REPRESENTATION :

![Screenshot 2024-09-23 102630](https://github.com/user-attachments/assets/f1ff0b49-6d0f-4925-a5d1-817fc836d970)

#### TREND PLOT REPRESENTATION :

![Screenshot 2024-09-23 102619](https://github.com/user-attachments/assets/c2145a49-63fe-4e4e-a57e-3038302f5fd5)

#### PLOTTING THE DATA:

![Screenshot 2024-09-23 102638](https://github.com/user-attachments/assets/10f9490e-08fe-4b49-bded-967eec910d1a)

#### OVERAL REPRESENTATION:

![Screenshot 2024-09-23 102611](https://github.com/user-attachments/assets/e7bf9f32-4c1a-4143-9760-c2954b6f77f5)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.

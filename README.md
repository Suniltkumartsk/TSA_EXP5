# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 30-09-25


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py
#Import libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Cell 2: Load dataset
data = pd.read_csv("usedcars.csv")

# Group by Year to create a time series (count of cars per year)
yearly_counts = data.groupby("Year").size()

# Convert Year into datetime index
ts = pd.Series(yearly_counts.values, index=pd.to_datetime(yearly_counts.index, format='%Y'))
ts.head()

#First Five 
data.head()

# Assuming yearly frequency (period=1 may be too small, so we take 2 to capture trend/seasonality)
decomposition = seasonal_decompose(ts, model="additive", period=2)

# Cell 4: Plot decomposition
plt.figure(figsize=(10, 8))

# Original data
plt.subplot(411)
plt.plot(ts, label="Cars Sold per Year")
plt.legend(loc="upper left")
plt.title("Original Time Series")

# Trend
plt.subplot(412)
plt.plot(decomposition.trend, label="Trend", color="orange")
plt.legend(loc="upper left")
plt.title("Trend")

# Seasonal
plt.subplot(413)
plt.plot(decomposition.seasonal, label="Seasonal", color="green")
plt.legend(loc="upper left")
plt.title("Seasonality")

# Residual
plt.subplot(414)
plt.plot(decomposition.resid, label="Residual", color="red")
plt.legend(loc="upper left")
plt.title("Residual")

plt.tight_layout()
plt.show()
```

### OUTPUT:
# FIRST FIVE ROWS:

<img width="1079" height="246" alt="Screenshot 2025-09-30 085502" src="https://github.com/user-attachments/assets/4b9f8c33-e7cb-4145-b255-b74980452db6" />


# PLOTTING THE DATA:
<img width="981" height="246" alt="Screenshot 2025-09-30 085522" src="https://github.com/user-attachments/assets/3d165ef4-ebeb-46f9-9b93-64de867ee72e" />

# SEASONAL PLOT REPRESENTATION :

<img width="693" height="180" alt="Screenshot 2025-09-30 085537" src="https://github.com/user-attachments/assets/c1b56c00-5cc0-4d5f-8691-13c7f6c5a046" />


# TREND PLOT REPRESENTATION :
<img width="639" height="195" alt="Screenshot 2025-09-30 085544" src="https://github.com/user-attachments/assets/8232e569-04d1-451c-969c-8f5a4d62241a" />

# OVERAL REPRESENTATION:

<img width="642" height="196" alt="Screenshot 2025-09-30 085551" src="https://github.com/user-attachments/assets/3454e199-750c-4876-a250-62ee15720eba" />


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.

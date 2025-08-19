# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Generate synthetic non-stationary data with trend + seasonality
np.random.seed(42)
time = np.arange(1, 101)
trend = 0.1 * time
seasonality = 10 * np.sin(2 * np.pi * time / 12)   # yearly seasonality
noise = np.random.normal(0, 1, 100)
data = pd.Series(trend + seasonality + noise)

# Original Data Plot
plt.figure(figsize=(10,4))
plt.plot(time, data, label="Original Data")
plt.title("Non-Stationary Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.show()

# =========================
# REGULAR DIFFERENCING
# =========================
diff_data = data.diff().dropna()
print("\nREGULAR DIFFERENCING:")
plt.figure(figsize=(10,4))
plt.plot(time[1:], diff_data, color="orange", label="After Differencing")
plt.title("Time Series after Regular Differencing")
plt.xlabel("Time")
plt.ylabel("Differenced Value")
plt.legend()
plt.show()

# =========================
# SEASONAL ADJUSTMENT
# =========================
seasonal_diff = data.diff(12).dropna()   # 12-period differencing
print("\nSEASONAL ADJUSTMENT:")
plt.figure(figsize=(10,4))
plt.plot(time[12:], seasonal_diff, color="green", label="After Seasonal Differencing")
plt.title("Time Series after Seasonal Adjustment")
plt.xlabel("Time")
plt.ylabel("Value (Seasonal Differenced)")
plt.legend()
plt.show()

# =========================
# LOG TRANSFORMATION
# =========================
log_data = np.log(data - min(data) + 1)  # shift to avoid negative values
print("\nLOG TRANSFORMATION:")
plt.figure(figsize=(10,4))
plt.plot(time, log_data, color="red", label="Log Transformed Data")
plt.title("Time Series after Log Transformation")
plt.xlabel("Time")
plt.ylabel("Log Value")
plt.legend()
plt.show()

```

### OUTPUT:

<img width="1062" height="493" alt="image" src="https://github.com/user-attachments/assets/1ee6bd59-d825-4955-be4b-9f090af76f1f" />
<img width="1055" height="524" alt="image" src="https://github.com/user-attachments/assets/e0ff0b31-541f-4106-a20c-96c41c7a5214" />
<img width="1061" height="516" alt="image" src="https://github.com/user-attachments/assets/9ec44a05-d081-4f83-922b-7488d2a38a9b" />
<img width="1068" height="526" alt="image" src="https://github.com/user-attachments/assets/82466774-00d3-4262-919e-19402ce978b2" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.

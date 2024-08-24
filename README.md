### Developed by: GANESH R
### Register Number: 212222240029
### Date :

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Water temperature for water quality data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.

### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```
```py
file_path = '/content/Amazon.csv'
data = pd.read_csv(file_path)
```

```py
data['Date'] = pd.to_datetime(data['Date'])  
data.set_index('Date', inplace=True)  
data.fillna(method='ffill', inplace=True)  
```

```py
Volumetemp_data = data['Volume']
```
```py
plt.figure(figsize=(14, 8))
plt.plot(Volumetemp_data, label='Volume')
plt.title('Original Volume Data')
plt.legend()
plt.show()
```
```py
Volumetemp_diff = Volumetemp_data.diff().dropna()
```
```py
plt.figure(figsize=(14, 8))
plt.plot(Volumetemp_diff, label='volume (Diff)')
plt.title('Differenced Volume (C) Data')
plt.legend()
plt.show()
```
```py
Volumetemp_log = np.log(Volumetemp_data + 1)
```
```py
plt.figure(figsize=(14, 8))
plt.plot(Volumetemp_log, label='Volume (C) (Log)')
plt.title('Log-Transformed Volume (C) Data')
plt.legend()
plt.show()
```
```py
Volumetemp_seasonal_adjustment = Volumetemp_log - Volumetemp_log.rolling(window=7).mean()
Volumetemp_seasonal_adjustment.dropna(inplace=True)
```
```py
plt.figure(figsize=(14, 8))
plt.plot(Volumetemp_seasonal_adjustment, label='Volume (C) (Seasonally Adjusted)')
plt.title('Seasonally Adjusted Log-Transformed Volume(C) Data')
plt.legend()
plt.show()
```

### OUTPUT:

![image](https://github.com/user-attachments/assets/5470a9db-1ca0-4cb9-b910-7cb00fec02d4)



REGULAR DIFFERENCING:

![image](https://github.com/user-attachments/assets/d06f564f-7be9-4146-a561-33de4b7fe386)

SEASONAL ADJUSTMENT:

![image](https://github.com/user-attachments/assets/a1e326e2-7846-46f0-9e16-589547163702)


LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/41ba288d-ba31-446c-a68b-53d7c70a3240)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Water Quality data.


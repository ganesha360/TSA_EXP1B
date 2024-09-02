### Developed by: GANESH R
### Register Number: 212222240029
### Date :

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformation on Amazon stock price data.

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


![image](https://github.com/user-attachments/assets/05130326-427f-4e4b-ba1f-eb10930244a6)




### REGULAR DIFFERENCING:


![image](https://github.com/user-attachments/assets/af4bb54e-b48c-4e20-8816-5203e985e1c2)


### SEASONAL ADJUSTMENT:


![image](https://github.com/user-attachments/assets/2a9bcc6e-5308-47b3-b53d-9d2ef1e90fad)



### LOG TRANSFORMATION:


![image](https://github.com/user-attachments/assets/a81ac1b4-dc92-498f-bef0-f439084ade53)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Amazon stock price data.


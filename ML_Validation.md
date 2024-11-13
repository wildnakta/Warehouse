![image](https://github.com/user-attachments/assets/075038ec-cc48-42af-988d-8bdfca3a221e)

## 1. 회귀분석 검증
### 1.1 MAE(Mean Absolute Error)
```Python
from sklearn,metrics import mean_absoulte_error
mean_absolute_error(y_test, y_pred)
```
### 1.2 MSE(Mean Squared Error)
```Python
from sklearn,metrics import mean_squared_error
mean_squared_error(y_test, y_pred)
```

### 1.3 RMSE(Root Mean Squared Error)
  ![image](https://github.com/user-attachments/assets/d23e29d1-8e70-459b-beab-0dc8213f1ecb)
```Python
from sklearn,metrics import mean_squared_error
MSE = mean_squared_error(y_test, y_pred)
RSME = np.sqrt(MSE)
```

### 1.4 MAPE(Mean Absolute Percentage Error)
```Python
from sklearn,metrics import mean_absoulte_error
MAPE = np.mean(np.abs((y_test - y_pred) / y_test)) * 100 
```


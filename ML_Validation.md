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




## 2. 분류분석 검증
### classification_report 함수로 결과 한 번에 확인하기
```Python
from sklearn.metrics import classification_report
print(classification_report(y_test, y_pred))
'''
[출력]
              precision    recall  f1-score   support

           0       0.65      0.73      0.69       871
           1       0.49      0.48      0.49       553
           2       0.46      0.41      0.43       822

    accuracy                           0.55      2246
   macro avg       0.53      0.54      0.53      2246
weighted avg       0.54      0.55      0.54      2246
'''
```


### 2.1 F1-Score
```Python
from sklearn.metrics import f1_score
f1_score(y_test, y_pred, average= ,)
''' 
 파라미터1. average =
    * 클래스가 2개일 경우 입력하지 않아도 되지만, 3개 이상일 경우 설정해줘야 한다.
    - binary : 이항분리
    - macro : f1-score를 산술평균한 것
    - weighted : 라벨별 f1-score를 샘플수 비중에 따라 가중평균한 것
    - micro : 전체 TP, FN, FP를 평균한 것
'''
```

  ![image](https://github.com/user-attachments/assets/d012c77e-be7d-49eb-9918-13cde339ac34)
  - 만들어진 배경 : Accuracy(정확도)가 가지는 클래스 불균형의 한계를 보완하기 위해 만들어 졌다.
  - Accuracy(한계)의 한계 예시 : 제품 100개 중 한 개가 불량일 때, 그냥 전부다 불량이 아니라고 하면 맞을 확률이 99%이다. 이런 모델로는 불량품을 선별할 수 없다.
  - Precision과 Recall의 조화평균
  - Precision(정확도) : TP / (TP + FP), Positive라 분류한 것 중에 실제로 Positive인 비율
  - Recall(재현율) : TP / (TP + FN), 실제 Positive인 것 중에 Positive로 분류한 비율
  ![image](https://github.com/user-attachments/assets/0174bdf9-b5c8-43e3-826a-81a89244da72)

### 2.2 ROC-AUC Score
- AUC는 0.5이상 1이하의 값을 갖는다. 0.5이면 분류능력이 전혀 없는 것을 의미, 1에 가까울수록 좋음
- y축은 TPR(True Positive Rate, Sensitivity, 민감도) 
- x축은 FPR(False Positive Rate, 1 - Specificity)
- Sensitivity : Positive를 Positive라고 옳게 판단한 비율
- Specificity : Negative를 Negative라고 옳게 판단한 비율

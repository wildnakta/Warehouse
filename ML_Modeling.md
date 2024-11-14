
## 회귀분석
### 다중회귀
### 방법1. statsmodels 라이브러리를 이용하는 방법
```Python
import numpy as np
import statsmodels.api as sm

# OLS 회귀 모델 적합
X = sm.add_constant(독립변수_배열)  # 상수항 추가
model = sm.OLS(종속변수_배열, 독립변수_배열).fit()

# 모델 p-value 출력
model.pvalues()

# 모델 요약 출력
print(model.summary())
```

### Logistic Regression(로짓 회귀)
  - 독립변수 : 범주형, 연속형, 이산형
  - 종속변수 : 범주형
```Python

from statsmodels.api import Logit
model_train = Logit(x_test, x_train).fit()

print(model_train.summary())

```
※ 참고자료
  - 오즈(Odds) : 성공확률이 실패확률에 비해 몇 배 높은가를 의미
    ![image](https://github.com/user-attachments/assets/92e83ba7-496b-495a-9c1d-4c398929f034)

  - 로짓변환 : 오즈에 로그를 취한 함수. 입력 값의 범위가 [0,1] 일 때 출력 값의 범위를 (−∞,+∞)로 조정한다.

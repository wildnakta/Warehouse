
## 회귀분석
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

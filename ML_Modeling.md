
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
  - 오즈(Odds) : P / (1 - P), 발생할 확률이 발생하지 않을 확률에 비해 몇 배 높은가를 의미
  - 오즈비(Odds Rate) :
    예) 약의 효과를 알아보기 위해 실제 약(Test)와 위약(Placebo)의 효과를 비교한다고 할 때,
    
    |     | Favorable | Unfavorable | Total |
    |-----|-----------|-------------|-------|
    |Test| 16 | 48 | 64 |
    |Placebo| 40 | 20 | 60 |

    Odds_Test    = 0.250 / ( 1 - 0.250 ) = 0.333  
    Odds_Placebo = 0.667 / ( 1 - 0.667 ) = 2.000  
    Odds Rate = Odds_Test / Odds_Placebo = 0.167  
    따라서 약의 효과는 위약의 효과의 0.167배 이다.

  - 로짓변환 : 오즈에 로그를 취한 함수. 입력 값의 범위가 [0,1] 일 때 출력 값의 범위를 (−∞,+∞)로 조정한다.

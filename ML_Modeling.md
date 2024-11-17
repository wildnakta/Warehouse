## GML(Generlized Linear Model, 일반 선형 모델)
|종속변수 Type| 분석방법 |
|-------------|-----------|
|연속형변수| 선형 회귀분석, 감마회귀분석|
|이항변수  | 로지스틱 회귀분석 |
|빈도수    | 포아송 회귀분석, 음이항 회귀분석|
|순서형변수 | 순서형 로지스틱 회귀분석, 순서형 프로빗분석 |

```Python
import statsmodels.api as sm
model = sm.GLM(y_train, x_train, family=sm.families.파라미터1() ).fit()
'''
파라미터1. family =
- family :
- Binominal : 클래스가 2개인 문제, Logit 모델과 동일
- Gammma :
- Gaussian :
- InverseGaussian :
- NegativeBinomial :
- Poission :
- Tweedie : 
'''
model.summary()
```


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

### Logistic Regression(로지스틱 회귀분석)
  - 독립변수 : 범주형, 연속형, 이산형
  - 종속변수 : 범주형(클래스 2개)
```Python
from statsmodels.api import Logit
model_train = Logit(x_test, x_train).fit()

print(model_train.summary())
```
※ 참고자료  
  - 오즈(Odds) : P / (1 - P), 발생확률 / 발생하지 않을 확률
  - 오즈비(Odds Rate) :
    ```Python
    import statsmodels.api as sm
    model = sm.Logit(x_test, x_train).fit()
    odss_rate=np.exp(model.prarams['오즈비 구하려는 변수')
    ```
    
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
     0 <    Odds   <  1  에 Log를 씌우면
    −∞ < Log(Odds) < +∞  이 된다.
    
    * 로짓변환(Logit Fuction)을 사용하는 이유  
    로지스틱 회귀분석은 GLM(일반화 선형모델)의 한 종류이므로
    '종속변수(확률) = b0 + b1*X1 + b2*X2 ····' 의 형태이다.
    하지만 'b0 + b1*X1 + b2*X2 ····' 형태는 0~1 사이의 값을 보장하지 않는다.
    이러한 한계를 극복하기 위해 만들어진 것이 바로 로짓변환이다. 

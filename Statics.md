
## 라이브러리 호출
```Python
from scipy import stats
```

## T-test T검정
· 단일표본 t검정 : 하나의 모집단에서 추출한 표본의 평균을 모집단의 평균과 비교  
· 독립표본 t검정 : 두 개의 모집단에서 각각 추출한 표본의 평균을 비교  
· 대응표본 t검정 : 하나의 모집단에서 추출한 두 표본의 평균을 비교  


## 정규성 검정 : 데이터가 정규분포를 따르는지 검정하는 통계적인 방법
    
· Anderson-Darling 검정 : 데이터수가 상대적으로 많을 때      
· K-S검정(Kolmogorov-Smirnov 콜모고로프-스미르노프 검정) : 데이터수가 상대적으로 많을 때  
· mstats.normaltest
### Shapiro-Wilk test 샤피로-윌크 검정
  - 특징 :
    - 정규분포를 가장 엄격하게 검정한다.
    - 데이터수가 상대적으로 적을 때 사용한다.(Python 기준 5,000개 미만 인경우)
  - 귀무가설 : 데이터가 정규분포를 따른다.
  - 대립가설 : 데이터가 정규분포를 따르지 않는다.


```Python
anderson(배열)  # Anderson-Darling 검정
kstest(df)    # K-S검정(Kolmogorov-Smirnov 콜모고로프-스미르노프 검정)
shapiro(df)   # 샤피로-윌크 검정
```

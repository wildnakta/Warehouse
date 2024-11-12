Robust 하다 : 이상값이 있더라도 결광에 큰 영향을 미치지 않는 것을 의미한다.

## 라이브러리 호출
```Python
from scipy import stats
```

## 표준화
- Z-Score의 의미 : 단위와 상관없이 값이 평균에서 얼마나 떨어져 있는가를 나타냄
```Python
from scipy.stats import zscore
zscore(배열 or 데이터프레임)
```

# 두 집단의 평균 비교
## 모수검정 : T-test T검정
    - 귀무가설(H0) : 두 집단의 평균이 동일하다
    - 대립가설(H1) : 두 집단의 평균이 동일하지 않다.
· 단일표본 t검정 : 하나의 모집단에서 추출한 표본의 평균을 모집단의 평균과 비교
   ```Python
    from scipy.stats import ttest_1samp
    ttest_1smap(df, 모평균)
   ```
· 독립표본 t검정 : 두 개의 모집단에서 각각 추출한 표본의 평균을 비교
   ```Python
    from scipy.stats import ttest_ind
    ttest_ind(df1, df2)
   ```
· 대응표본 t검정 : 하나의 모집단에서 추출한 두 표본의 평균을 비교 
   ```Python
    from scipy.stats import ttest_rel
    ttest_rel(df_before, df_after)
   ```

## 비모수 검정
### Wilcoxon Rank-Sum Test(Mann-Whitney U Test) 윌콕슨 순위합 검정
    - 독립표본 t검정의 비모수적 검정 방법
    - 귀무가설 : 두 표본의 분포는 동일하다
    - 대립가설 : 두 표본의 분포는 동일하지 않다.
```Python
from scipy.stats import ranksums
ranksums()
```
    
### Wilcoxon Signed-Rank Test 윌콕슨 부호 순위 검정
    - 대응표본 t검정의 비모수적 검정 방법
    - 귀무가설 : 두 표본의 중앙값 차이는 0이다.
    - 대립가설 : 두 표본의 중앙값 차이는 0이 아니다.
```Python
from scipy.stats import wilcoxon
wilcoxon(df['열'] - 모집단의 평균)
```
## 정규성 검정 : 데이터가 정규분포를 따르는지 검정하는 통계적인 방법
    
### Anderson-Darling 검정
    · 특징 : 데이터수가 상대적으로 많을 때 사용
    · 결과해석 : 
     - statistic : 통계값
     - critical_values : 순서대로 유의확률 15%, 10%, 5%, 2.5%, 1% 일 떄의 P-Value
    
· K-S검정(Kolmogorov-Smirnov 콜모고로프-스미르노프 검정) : 데이터수가 상대적으로 많을 때  
· mstats.normaltest
### Shapiro-Wilk test 샤피로-윌크 검정
    · 특징 :
     - 정규분포를 가장 엄격하게 검정한다.
     - 데이터수가 상대적으로 적을 때 사용한다.(Python 기준 5,000개 미만 인경우)
     
    · 귀무가설 : 데이터가 정규분포를 따른다.
    · 대립가설 : 데이터가 정규분포를 따르지 않는다.


```Python
anderson(배열)  # Anderson-Darling 검정
kstest(df)    # K-S검정(Kolmogorov-Smirnov 콜모고로프-스미르노프 검정)
shapiro(df)   # 샤피로-윌크 검정
```

## 등분산 검정
    - 귀무가설(H0) : 분산이 동일하다
    - 대립가설(H1) : 분산이 동일하지 않다.
- 대부분의 통계 절차에서는 표본들이 서로 다른 평균을 갖는 모집단에서 추출되었더라도 분산이 동일하다고 가정한다.
- 등분산 검정은 그 자체로는 많이 사용되지는 않고, 분산분석이나 t검정을 하기 전에 조건 분석용으로 사용한다.


|종류|비교 가능한 그룹 수|정규성 가정|특징|
|------|---|---|------|
|F Test|두 그룹|필요||
|Levene's Test|세 그룹 이상|불필요||
|Brown-forsythe Test |-|-|편차의 차이를 평균의 차이가 아닌 중앙값의 차이로 정의|
|Barlett Test|세 그룹 이상|필요||


```Python
from scipy.stats import bartlett
from scipy.stats import fligner
from scipy.stats import levene
```

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

## P-Value
- P-Value의 의미 : 결과가 우연에 의해 나타날 확률
```Python
from scipy.stats import zscore
zscore(배열 or 데이터프레임)
```

## 표준편차
```Python
df.std()
```

## 로그변환
    ※ 로그변환을 하는 이유
        - 뭉쳐 데이터는 퍼지게 만들고, 퍼져 있는 데이터는 모이게 만들기 위해 사용한다.
        - 0 < x < 1의 범위를 가지는 X값을 넓은 범위의 y값에 분포시킬 수 있다.
        - x가 커져도 y값은 그렇게 큰 차이가 나지 않는다. 따라서 넓은 범위의 x값도 좁은 범위의 y값 내에 분포시킬 수 있다.
```Python
np.log(0)   # -inf 출력
np.log1p(0) # 0 출력
```

# 집단간 평균 비교
![image](https://github.com/user-attachments/assets/a177b881-5ba5-4f06-880e-1f113312a182)

## 모수검정 : T-test T검정
    - 귀무가설(H0) : 두 집단의 평균이 동일하다
    - 대립가설(H1) : 두 집단의 평균이 동일하지 않다.
· 단일표본 t검정 : 하나의 모집단에서 추출한 표본의 평균을 모집단의 평균과 비교
   ```Python
    from scipy.stats import ttest_1samp
    ttest_1samp(df, 모평균)
   ```
· 독립표본 t검정 : 두 개의 모집단에서 각각 추출한 표본의 평균을 비교
   ```Python
    from scipy.stats import ttest_ind
    ttest_ind(df1, df2)
   ```
· 대응표본 t검정 : 하나의 모집단에서 추출한 두 표본의 평균을 비교 
   ```Python
    from scipy.stats import ttest_rel
    ttest_rel(df_before, df_after, alternative='greater')

    '''
    파라미터1. alternative =
    - greater : 단측검정, before > after가 대립가설이 된다.
    - less : 단측검정, before < after가 대립가설이 된다.
    '''
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
    · 특징 : 데이터수가 상대적으로 많을 때(5,000개 이상) 사용
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



## 카이제곱검정(교차분석)
![image](https://github.com/user-attachments/assets/0aee1935-1d4b-4b51-94ff-ffb37ddcb696)

### 카이제곱검정의 종류
1. 독립성 검정 (Test of Independence)
   - 두 범주형 변수 간의 독립성 여부 확인
   - 예) 성별(남/여)와 취미(운동/독서/게임) 간의 관계가 있는지 검정
2. 동질성 검정 (Test of Homogeneity)
    - 동일한 범주형 변수에 대해 여러 모집단의 분포를 비교.
    - 예) 세 도시(A, B, C) 주민들이 선호하는 교통수단(버스, 지하철, 택시)의 분포가 같은가?
3. 적합도 검정 (Goodness of Fit Test)
   - 한 집단의 관찰값이 특정 이론적 분포(또는 기대값)에 얼마나 잘 부합하는지 확인.
   - 예) 주사위를 60번 굴렸을 때, 각 면이 나온 횟수가 균일한 분포를 따르는가?

|특성| chi2_contingency | chisquare |
|----|------------------|-----------|
| 검정 유형 | 독립성 검정 / 동질성 검정	| 적합도 검정 |
| 입력 데이터 | 교차표 (2D 빈도 배열)	| 관찰값과 기대값 (1D 배열)|
| 결과	|Chi2 통계량, p-값, 자유도, 기대 빈도	|Chi2 통계량, p-값|
| 기대값 자동 계산 | 가능 | 기대값 없으면 균일 분포로 간주|
| 적용 범주	|두 범주형 변수의 관계 분석	|단일 샘플의 분포 적합성 확인|

```Python
from scipy.stats import chi2_contingency

# 2x2 교차표
obs = [[10, 20],
       [30, 40]]

chi2, p, dof, expected = chi2_contingency(obs)
print(f"Chi2: {chi2}, p-value: {p}, DoF: {dof}, Expected Frequencies: {expected}")

```

```Python
from scipy.stats import chisquare

observed = [10, 20, 30] # 관찰값
expected = [15, 15, 30] # 기대값

chi2, p = chisquare(f_obs=observed, f_exp=expected)
print(f"Chi2: {chi2}, p-value: {p}")

```

    - 독립변수 / 종속변수 : 범주형 / 범주형
    - 귀무가설(H0) : 두 범주형 변수가 서로 독립이다. 
    - 대립가설(H1) : 두 범주형 변수가 서로 독립이 아니다.
    - 단측검정
    - 카이제곱통계량이 커질수록 좋지 않다.(=실제와 기대도수 차이가 크다)

## 사후검정

민감도 순위 : Duncan > Tukey > Bonferroni > Scheffe
왼쪽으로 갈수록 집단을 분리시키려는 성격이 강하다.
오른쪽으로 갈수록 집단을 엄격하고 소극적으로 분리시킨다.

|종류        |로직 |등분산 가정|특징|
|------------|-----|---|------|
|Duncan      |     |O|-|
|Tukey       |     |O|집단의 수가 동일한 경우에 사용 가능 |
|Bonferrnoi  |t검정|O|각 집단의 수가 동일하지 않아도 사용 가능|
|Scheffe     |F분포|O|시회과학에서 가장 많이 사용하는 기법|
|Dunnett T3  |     |X||
|Games-Howell|     |X||


```Python
from scipy.stats import bartlett
from scipy.stats import fligner
from scipy.stats import levene
```


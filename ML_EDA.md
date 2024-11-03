# 데이터프레임 모양 확인하기
```python
df.shape
df.head()
df.tail()
```

# 결측값 확인하기
```python
df.isnull()
df.isnull().sum()
```


# 데이터 통계값 확인하기
```python
df.describe() # 전반적인 데이터 현황 파악하기
df['열'].value_counts() # 열의 값의 빈도 파악하기

```

# 원하는 데이터 선택하기
```python
df.iloc[3]     # 3번째 열 선택
df.iloc[[3]]   # 3번째 행 선택
df.iloc[0:3]   # 0번째부터 3번째 열까지 선택
df.iloc[[0:3]] # 0번째부터 3번째 행까지 선택

```
# 데이터 고유값 확인하기
```python
df['열'].unique() # 고유값들을 선택한다
df['열'].nunique() # 고유값들의 개수를 선택한다

```


# 정리해야할 것
```python
df.quantile()

```

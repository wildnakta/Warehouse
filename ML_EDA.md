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
df.describe()

```

# 데이터 통계값 확인하기
```python
df.iloc[3]     # 3번째 열 선택
df.iloc[[3]]   # 3번째 행 선택
df.iloc[0:3]   # 0번째부터 3번째 열까지 선택
df.iloc[[0:3]] # 0번째부터 3번째 행까지 선택

```


# 정리해야할 것
```python
df.quantile()

```

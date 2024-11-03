## 불필요한 열 제거
### 
```python
df.drop(columns=['열A', '열B']) # 데이터프레임에서 '열A'와 '열B' 제거
```


## 결측값 제거하기
### 
```python
df.dropna(subset=['열A', '열B']) # 열A와 열B 중에 결측값이 있는 행 제거
```

## 중복값 제거하기
```python
df.drop_duplicates( [‘열A’, ‘열B’] ) # 여러개의 행에서 ‘열A’와 ‘열B’에 중복된 값이 있을 경우 하나의 행만 남기고 제거
```

## One-Hot Encoding(원 핫 인코딩)
### 방법1. lambda 함수 사용하기

``` python
df['새로운 열'] = df['인코딩할 열'].apply(lambda x : '바꿀 값1' if '바꾸고 싶은 값1' in x
                                                    else( '바꿀 값2' if '바꾸고 싶은 값2' in x
                                                        else 0))

```

## Label Encoding(라벨 인코딩)
### 방법1. lambda 함수 사용하기
``` python
df['새로운 열'] = df['인코딩할 열'].apply(lambda x : '바꿀 값1' if '바꾸고 싶은 값1' in x
                                                    else( '바꿀 값2' if '바꾸고 싶은 값2' in x
                                                        else 0))
```

### 방법2. sklearn.LabelEncdoing 모듈 사용하기
```python
from sklearn.preprocessing import LabelEncoder
label_encoder = LabelEncoder()
df['새로운 열'] = label_encoder.fit_transform(df['인코딩할 열'])
```


## 범위를 범주화 하기
### 방법1. pd.cut 클래스 사용하기
```python
bins = [1, 3,10] # 범주화할 범위 
labels = [1, 2] # 어떻게 범주화 할 건지
# 0이상 3미만의 값은 1로, 3이상 10 미만의 값은 2로 범주화
df['새로운 열'] = pd.cut(df['범주화할 열'], bins=bins, labels=labels)
train2
```

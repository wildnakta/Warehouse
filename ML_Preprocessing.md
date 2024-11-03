

# One-Hot Encoding(원 핫 인코딩)
## 방법1. lambda 함수 사용하기

``` python
df['새로운 열 이름'] = df['인코딩할 열'].apply(lambda x : '바꿀 값1' if '바꾸고 싶은 값1' in x
                                                    else( '바꿀 값2' if '바꾸고 싶은 값2' in x
                                                        else 0))

```






# Label Encoding(라벨 인코딩)
## 방법1. lambda 함수 사용하기
``` python
df['새로운 열 이름'] = df['인코딩할 열'].apply(lambda x : '바꿀 값1' if '바꾸고 싶은 값1' in x
                                                    else( '바꿀 값2' if '바꾸고 싶은 값2' in x
                                                        else 0))
```

## 방법2. sklearn.LabelEncdoing 모듈 사용하기
```python
from sklearn.preprocessing import LabelEncoder
label_encoder = LabelEncoder()
df['새로운 열 이름'] = label_encoder.fit_transform(df['인코딩할 열'])
```


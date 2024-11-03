

# One-Hot Encoding(원 핫 인코딩)

## 방법1. sklearn.LabelEncdoing 모듈 사용하기




# Label Encoding(원 핫 인코딩)
```python

from sklearn.preprocessing import LabelEncoder

label_encoder = LabelEncoder()

df['Color_encoded'] = label_encoder.fit_transform(df['열'])

```


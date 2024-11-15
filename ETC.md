## 데이터프레임을 다른 자료형으로 변환하기
```Python
df['열'].values.tolist() # 데이터프레임을 리스트로 변환
df['열'].to_numpy()      # 데이터프레임을 배열로 변환
df['열'].values          # 데이터프레임을 배열로 변환
```

## 시리즈 데이터를 데이터프레임으로 변환
```Python
시리즈.to_frame()
```

## 문자열을 특정값으로 채우기
```Python
df['열'].astype(str).str.zfill(4) # 문자열을 네 자리로 맞춘다.

'''
예시)
a   → 000a
bc  → 00bc
def → 0def
'''
```

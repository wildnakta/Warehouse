## 인덱스(Index) 조작
### 
```python
df.reset_index() # e데이터프레임의 Index를 0 ~ n로 초기화함
  # 파라미터1. drop = : 기존에 index 였던 데이터들이 'index'라는 이름의 열이 되는데, 이 열을 제거함 (True, False)
  # 파라미터2. names = ['엶A', '열B'] : '열A'와 '열B'를 인덱스로 사용함 
```

## Column명 변경
```python
df.rename( columns = { '기존컬럼명1' : '새로운컬럼명1', '기존컬럼명2' : '새로운컬럼명2' }, inplace = True ) 
```


# 문자 ↔ 날짜로 변경하기
```python
pd.to_datetime(df['열'])                # 열을 날짜로 변경한다.
pd.to_datetime(df['열']).dt.day_name()  # 날짜의 요일을 출력한다.
pd.to_datetime(df['열']).dt.year        # 날짜의 연도를 출력한다
pd.to_datetime(df['열']).dt.month       # 날짜의 월을 출력한다
pd.to_datetime(df['열']).dt.day         # 날짜의 일을 출력한다


pd.to_datetime(df['열']).strftime('%Y-%m-%d %H:%M:%S') # 날짜와 시간을 문자열로 출력
pd.to_datetime(df['열']).strptime('%Y-%m-%d %H:%M:%S') # 문자열을 날짜와 시간으로 출력
```


## 데이터정렬
### 
```python
df.sort_values('열') # 열 값을 기준으로 오름차순으로 정렬한다
  # 파라미터1. by = ['열A', '열B'] : '열A'와 '열B' 기준으로 데이터를 정렬한다.
  # 파라미터2. ascending = True, False : True 면 오름차순, False면 내림차순으로 정렬
```

## 데이터 형변환
### 
```python
df['열'].astype() # '열'의 값들을 float, object 등등의 자료형으로 변환한다
```  


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
  # 파라미터1. keep = 'last', 'first' # 몇 번째 행을 남길 것인지
  # 파라미터2. inplcae = True, False
  # 파라미터3. ignore_index = True, False
```

## 필요한 데이터만 선택하기
```python
df.select_dtypes() # 특정 형태 열만 선택
  # - 파라미터1. exclude = 특정 데이터 타입을 제외한다.(‘object’, 'float64', 'int64, 'bool')
  # - 파라미터2. include = 특정 데이터 타입만 포함한다.(‘object’, 'float64', 'int64, 'bool')

df[df['열A'].str.contains('값A')] # 열A에 값A가 포함되어 있는 데이터만 선택
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
### 방법2. loc 함수 사용하기
``` python
# '열'A에 '값A'라는 값이 있을 경우 '열B'에 '값B'를 저장한다.
df.loc[df['열A'] == '값A', '열B'] = '값B'
```

### 방법2. sklearn.LabelEncdoing 모듈 사용하기
```python
from sklearn.preprocessing import LabelEncoder
label_encoder = LabelEncoder()
df['새로운 열'] = label_encoder.fit_transform(df['인코딩할 열'])
```


## 데이터셋 나누기

``` python
from sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(feature, target)

```



## 범위를 범주화 하기
### 방법1. pd.cut 클래스 사용하기
```python
bins = [1, 3,10] # 범주화할 범위 
labels = [1, 2] # 어떻게 범주화 할 건지
# 0초과 3이하의 값은 1로, 3이상 10 미만의 값은 2로 범주화
df['새로운 열'] = pd.cut(df['범주화할 열'], bins=bins, labels=labels)
train2
```

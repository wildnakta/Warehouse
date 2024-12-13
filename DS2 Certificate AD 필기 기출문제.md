### 리스트와 배열의 차이
```python
# 리스트의 연산 : 불가
list1 = [1, 3, 5]
list2 = [3, 4, 5]
list1 + list2

# 결과
[1, 3, 5, 3, 4, 5]

# 배열의 연산 : 가능
arr1 = np.array([1, 3, 5])
arr2 = np.array([3, 4, 5])
arr1 + arr2

# 결과
array([ 4,  7, 10])
```


### argmax 와 argmin : 배열에서 최대 최소 원소 순서 찾기
```python
arr1 = np.array([1, 3, 5, 8, 2])
arr2 = np.array([3, 4, 5, 5, 1])
arr3 = arr1 + arr2
print('arr3 :',arr3)
print('가장 큰 원소의 순서 :',arr3.argmax())
print('가장 작은 원소의 순서 :',arr3.argmin())

# 결과
arr3 : [ 4  7 10 13  3]
가장 큰 원소의 순서 : 3
가장 작은 원소의 순서 : 4
```

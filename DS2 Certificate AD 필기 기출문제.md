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


### Accuracy, Recalll(재현율), Precision(정확도)
```
- Precision(정확도) = TP / ( TP + FP ), True로 분류한 것 중에 실제로 True인 비율
- Recall(재현율) = TP / ( TP + FN ), 실제로 True인 것 중에 True로 분류한 비율

- Sensitivity(민감도), TPR = TP / ( TP + FN ), 실제로 True인 것 중에 True로 분류한 비율
- Specificity(특이도), TNR = TN / ( TN + FP ), 실제로 False 인 것 중에 False로 분류한 비율
- FPR = 1 - 특이도, Negative를 Positive로 잘못 분류한 비율

- 재현율 = 민감도

```

### 오즈
- 오즈비 = 어떤 사건이 일어날 확률 / 일어나지 않을 확률

### 지니계수


### 실루엣계수

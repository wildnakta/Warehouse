### Seaborn 한글 나오도록 하기
```Python
plt.rc("font", family = "Malgun Gothic")
sns.set(font="Malgun Gothic", 
rc={"axes.unicode_minus":False}, style='white')
```



### distplot
### 

### 레이더차트 그리기
## 따로 그리기
```python
import numpy as np
import matplotlib.pyplot as plt

## 따로 그리기
## ★[입력필요] 라고 주석 달아놓은 곳 입력 필요
datatable = 데이터 # ★[입력필요]

labels = datatable.columns[1:]
num_labels = len(labels)

angles = [x/float(num_labels)*(2*np.pi) for x in range(num_labels)] ## 각 등분점
angles += angles[:1] ## 시작점으로 다시 돌아와야하므로 시작점 추가

my_palette = plt.cm.get_cmap("Set2", len(datatable.index))

fig = plt.figure(figsize=(13,(len(datatable)/2)*6))
fig.set_facecolor('white')

for i, row in datatable.iterrows():
    color = my_palette(i)
    data = datatable.iloc[i].drop('sgg_name_type').tolist() # ★[입력필요]
    data += data[:1]
    
    ax = plt.subplot(round(len(datatable)/2),2,i+1, polar=True)
    ax.set_theta_offset(np.pi / 2) ## 시작점
    ax.set_theta_direction(-1) ## 그려지는 방향 시계방향
    
    plt.xticks(angles[:-1], labels, fontsize=13) ## x축 눈금 라벨
    ax.tick_params(axis='x', which='major', pad=15) ## x축과 눈금 사이에 여백을 준다.
    
    ax.set_rlabel_position(0) ## y축 각도 설정(degree 단위)
    plt.yticks([0, 0.2, 0.4, 0.6, 0.8, 1], ['0','0.2','0.4','0.6','0.8','1'], fontsize=10) ## y축 눈금 설정
    plt.ylim(0,1)
    
    ax.plot(angles, data, color=color, linewidth=2, linestyle='solid') ## 레이더 차트 출력
    ax.fill(angles, data, color=color, alpha=0.4) ## 도형 안쪽에 색을 채워준다.
    
    plt.title(row.sgg_name_type, size=15, color=color,x=-0.2, y=1.1, ha='left', fontweight='bold') ## ★[입력필요] 타이틀은 캐릭터 클래스로 한다.

plt.tight_layout(pad=5) ## subplot간 패딩 조절
plt.show()
```

![image](https://github.com/user-attachments/assets/8436b3ec-bb9b-43e4-9b33-949ce8e7e429)


## 하나로 그리기
```python
import numpy as np
import matplotlib.pyplot as plt

## 하나로 합치기
## ★[입력필요] 라고 주석 달아놓은 곳 입력 필요
datatable = table4 # ★[입력필요]
labels = datatable.columns[1:]
num_labels = len(labels)
    
angles = [x/float(num_labels)*(2*np.pi) for x in range(num_labels)] ## 각 등분점
angles += angles[:1] ## 시작점으로 다시 돌아와야하므로 시작점 추가
    
my_palette = plt.cm.get_cmap("Set2", len(datatable.index))
 
fig = plt.figure(figsize=(8,8))
fig.set_facecolor('white')
ax = fig.add_subplot(polar=True)
for i, row in datatable.iterrows():
    color = my_palette(i) 
    data = datatable.iloc[i].drop('sgg_name_type').tolist() # ★[입력필요]
    data += data[:1]
    
    ax.set_theta_offset(np.pi / 2) ## 시작점
    ax.set_theta_direction(-1) ## 그려지는 방향 시계방향
    
    plt.xticks(angles[:-1], labels, fontsize=13) ## 각도 축 눈금 라벨
    ax.tick_params(axis='x', which='major', pad=15) ## 각 축과 눈금 사이에 여백을 준다.
 
    ax.set_rlabel_position(0) ## 반지름 축 눈금 라벨 각도 설정(degree 단위)
    plt.yticks([0, 0.2, 0.4, 0.6, 0.8, 1],['0','0.2','0.4','0.6','0.8','1'], fontsize=10) ## 반지름 축 눈금 설정
    plt.ylim(0,1)
    
    ax.plot(angles, data, color=color, linewidth=2, linestyle='solid', label=row.sgg_name_type) ## ★[입력필요]레이더 차트 출력
    ax.fill(angles, data, color=color, alpha=0.5) ## 도형 안쪽에 색을 채워준다.
    
plt.legend(loc=(0.9,0.9))
plt.show()
```

![image](https://github.com/user-attachments/assets/a5f1597b-ceb1-44fa-827a-e178d1553612)

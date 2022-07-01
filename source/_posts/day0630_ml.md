---
title: "머신러닝_데이터 다루기"
date: '2022-06-30'
---

```python
## 파이썬 주요 라이브러리
- Machine Leaning
 + 정형 데이터
 + 시이킷런 (https://scikit-learn.org/stable/)

- Deep Leaning
  + 비정형 데이터
  + Tensorflow(구글) vs Python(페이스북)
  + 혼공머 : Teansorflow
  + 실제 상용 서비스 - 
  Tensorflow vs R&D - Pytorch 
```


```python
## 생선 분류
- p. 45
- 도미, 곤들매기, 농어, 등등
- 이 생선들을 프로그램을 분류한다

```


```python
# 30cm이면 도미라고 알려줘라
fish_length = 31
if fish_length >= 30:
    print("도미")
```

    도미
    

## 도미 데이터 수집


```python
# 도미의 길이 
bream_length = [25.4, 26.3, 26.5, 29.0, 29.0, 29.7, 29.7, 30.0, 30.0, 30.7, 31.0, 31.0, 31.5, 32.0, 32.0, 32.0, 33.0, 33.0, 33.5, 33.5, 34.0, 34.0, 34.5, 35.0, 35.0, 35.0, 35.0, 36.0, 36.0, 37.0, 38.5, 38.5, 39.5, 41.0, 41.0]

#도미의 무게
bream_weight = [242.0, 290.0, 340.0, 363.0, 430.0, 450.0, 500.0, 390.0, 450.0, 500.0, 475.0, 500.0, 500.0, 340.0, 600.0, 600.0, 700.0, 700.0, 610.0, 650.0, 575.0, 685.0, 620.0, 680.0, 700.0, 725.0, 720.0, 714.0, 850.0, 1000.0, 920.0, 955.0, 925.0, 975.0, 950.0]
```

## 데이터 가공
- 여기서는 생략

## 데이터 시각화
- 여러 인사이트 확인을 위해 시각화, 통계수치계산
- 탐색적 자료분석(EDA, Exploratory Data Analysis)
- https://jehyunlee.github.io/ 참고github


```python
import matplotlib.pyplot as plt

plt.scatter(bream_length, bream_weight)
plt.xlabel('length')
plt.ylabel('weight')
plt.show()

```


    
![](images/day0630ml/output_7_0.png)
    


                            2차원 그래프

- 파이썬 시각화는 객체지향으로 한다. 
- 이유 : 조금 더 예쁘고, 아름답게 다듬기위해서
- 캐글 시각화, 참고할 때, 아래와 같이 하는 분들이 많음
- 다음과 같이 코딩하면 더욱 확장성있게 시각화 할 수 있다


```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
ax.scatter(bream_length, bream_weight)
ax.set_xlabel('length')
ax.set_ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_10_0.png)
    


## 빙어 데이터 수집


```python
smelt_length = [9.8, 10.5, 10.6, 11.0, 11.2, 11.3, 11.8, 11.8, 12.0, 12.2, 12.4, 13.0, 14.3, 15.0]
smelt_weight = [6.7, 7.5, 7.0, 9.7, 9.8, 8.7, 10.0, 9.9, 9.8, 12.2, 13.4, 12.2, 19.7, 19.9]
```

## 데이터 시각화 
- 도미와 빙어 데이터를 합침


```python
fig, ax = plt.subplots()
ax.scatter(bream_length, bream_weight)
ax.scatter(smelt_length, smelt_weight)
ax.set_xlabel('length')
ax.set_ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_14_0.png)
    


- 두 개의 리스트 합치기 


```python
length = bream_length + smelt_length
weight = bream_weight + smelt_length
```

- 2차원 리스트로 만든다


```python
fish_data = [[l,w]for l, w in zip(length, weight)] # zip: 나열된 원소를 하나씩 꺼내주는일을 한다(하나싹 거낸데이터 반복 => for문)
print(fish_data)

```

    [[25.4, 242.0], [26.3, 290.0], [26.5, 340.0], [29.0, 363.0], [29.0, 430.0], [29.7, 450.0], [29.7, 500.0], [30.0, 390.0], [30.0, 450.0], [30.7, 500.0], [31.0, 475.0], [31.0, 500.0], [31.5, 500.0], [32.0, 340.0], [32.0, 600.0], [32.0, 600.0], [33.0, 700.0], [33.0, 700.0], [33.5, 610.0], [33.5, 650.0], [34.0, 575.0], [34.0, 685.0], [34.5, 620.0], [35.0, 680.0], [35.0, 700.0], [35.0, 725.0], [35.0, 720.0], [36.0, 714.0], [36.0, 850.0], [37.0, 1000.0], [38.5, 920.0], [38.5, 955.0], [39.5, 925.0], [41.0, 975.0], [41.0, 950.0], [9.8, 9.8], [10.5, 10.5], [10.6, 10.6], [11.0, 11.0], [11.2, 11.2], [11.3, 11.3], [11.8, 11.8], [11.8, 11.8], [12.0, 12.0], [12.2, 12.2], [12.4, 12.4], [13.0, 13.0], [14.3, 14.3], [15.0, 15.0]]
    


```python
fish_data = [[l,w]for l, w in zip(length, weight)]
fish_data[0:5]
```




    [[25.4, 242.0], [26.3, 290.0], [26.5, 340.0], [29.0, 363.0], [29.0, 430.0]]



- 라벨링을 해준다 = 지도해준다
= 지도학습 

- 머신러닝에서 2개를 구분하는 경우 찾으려는 대상을 1로 놓고, 그외에는 0으로 놓는다


```python
fish_target = [1] * 35 + [0] *14
print(fish_target)
```

    [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    

## 모델링


```python
from sklearn.neighbors import KNeighborsClassifier

# 클래스 인스턴스화 (클래스의 객체 만들기)
kn = KNeighborsClassifier()


```


```python
# 모형 학습
#       독립변수   종속변수
kn.fit(fish_data, fish_target) # fit()메서드는 주어진 데이터로 알고리즘을 훈련한다
```




    KNeighborsClassifier()




```python
# 예측 정확도 
kn.score(fish_data, fish_target) # score()메서드: 사이킷런에서모델을 평가(0-1의 값// 1은 정확히 맞혔다, 0.5라면 절반만 맞혔다)
```




    1.0



- 실제 예측을 해보자
- 새로운 물고기 도착했습니다
 + 길이: 30, 몸무게: 600


```python
ac_length = int(input("물고기 길이를 입력하세요__"))
ac_weight = int(input("물고기 무게를 입력하세요__"))

preds = int(kn.predict ([[ac_length,ac_weight]])) #주의사항 : x,y,z는 모두 이차원 배열 만을 취급할 수 있다. [[]]형태
print(preds)

if preds == 1:
 print("도미")
else:
 print("빙어")

```

    물고기 길이를 입력하세요__30
    물고기 무게를 입력하세요__600
    1
    도미
    

## 새로운 모델 제안
- Default : 정확도 100%
- 제안 : 정확도 71%

--------> 실험단계
- 하이퍼 파라미터 세팅(처음 머신러닝 접할시 이 세팅 하지 않을것)
 + 예) n_neighbors = 49

- default(처음 머신러닝 접할시 사용하기)

## 머신러닝 알고리즘 두개의 흐름
-선형모델 : 선형회귀, 로지스틱 회귀

-의사결정트리 모델 : 1975년 의사결정트리 모델, KNN
 + 캐글에서 자주사용되는 모델: 의사결정트리 모델
 + 랜덤포레스트 
 + 부스틴계열 : LightGBM(2017), XGBoost(2016)

 - 공부시 : 선형회귀, 로지스틱 회귀, 랜덤포레스트, LightGBM(=XGBoost) 위주로 공부할 것 




```python
Kn49 = KNeighborsClassifier(n_neighbors= 49)  #KNeighborsClassifier 클래스의 기본값은 5/ n_neighbors= 49:기준
Kn49 .fit(fish_data, fish_target)
Kn49.score(fish_data, fish_target)
```




    0.7142857142857143



- 문제점: 이미 도미/빙어 박스 분류되었었음 


```python
fish_length = [25.4, 26.3, 26.5, 29.0, 29.0, 29.7, 29.7, 30.0, 30.0, 30.7, 31.0, 31.0, 
                31.5, 32.0, 32.0, 32.0, 33.0, 33.0, 33.5, 33.5, 34.0, 34.0, 34.5, 35.0, 
                35.0, 35.0, 35.0, 36.0, 36.0, 37.0, 38.5, 38.5, 39.5, 41.0, 41.0, 9.8, 
                10.5, 10.6, 11.0, 11.2, 11.3, 11.8, 11.8, 12.0, 12.2, 12.4, 13.0, 14.3, 15.0]
fish_weight = [242.0, 290.0, 340.0, 363.0, 430.0, 450.0, 500.0, 390.0, 450.0, 500.0, 475.0, 500.0, 
                500.0, 340.0, 600.0, 600.0, 700.0, 700.0, 610.0, 650.0, 575.0, 685.0, 620.0, 680.0, 
                700.0, 725.0, 720.0, 714.0, 850.0, 1000.0, 920.0, 955.0, 925.0, 975.0, 950.0, 6.7, 
                7.5, 7.0, 9.7, 9.8, 8.7, 10.0, 9.9, 9.8, 12.2, 13.4, 12.2, 19.7, 19.9]
```

- 2차원 파이썬 리스트
- 라벨링


```python
fish_data = [[l, w] for l, w in zip(fish_length, fish_weight)]
fish_target = [1] * 35 + [0] * 14
print(fish_target)
```

    [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    


```python
fish_data = [[l, w] for l, w in zip(fish_length, fish_weight)]
fish_target = [1] * 35 + [0] * 14
print(fish_target[0:40:5])
print(fish_data[0:40:5])
```

    [1, 1, 1, 1, 1, 1, 1, 0]
    [[25.4, 242.0], [29.7, 450.0], [31.0, 475.0], [32.0, 600.0], [34.0, 575.0], [35.0, 725.0], [38.5, 920.0], [9.8, 6.7]]
    

- sample
- 도미 35마리, 빙어 14마리
- 49개의 샘플존재
- 처음 35개를 훈련 / 나머지 14개를 테스트


```python
from sklearn.neighbors import KNeighborsClassifier

# 클래스 인스턴스화 (클래스의 객체 만들기)
kn = KNeighborsClassifier()

# 훈련 세트로 0:34 인덱스 활용
train_input = fish_data[:35]
train_target = fish_target[:35]


# 테스 세트로 35: 마지막 인덱스 활용
test_input = fish_data[35:]
test_target = fish_target[35:]

# 모형 학습
kn = kn.fit(train_input, train_target)
print(kn.score(test_input,test_target))
```

    0.0
    

- 샘플링 편향
- 훈련 세트와 테스트 세트가 골고루 섞이지 않음

## 샘플링 작업


```python
import numpy as np

input_arr = np.array(fish_data)
target_arr = np.array(fish_target)
print(input_arr[0:49:7])
```

    [[ 25.4 242. ]
     [ 30.  390. ]
     [ 32.  600. ]
     [ 34.  685. ]
     [ 36.  850. ]
     [  9.8   6.7]
     [ 11.8   9.9]]
    


```python
print(input_arr.shape, target_arr.shape)
```

    (49, 2) (49,)
    

- 0-48까지 정수를 섞기


```python
# random으로 무작위 배열을 만들거나 설정할때 (중요)
np.random.seed(42) # random.seed: 일정한 결과를 얻기위해 초기에 지정/ random.seed(0)또는random.seed(42)모두 상관없음
index = np.arange(49) # arange(): 1씩 증가하는 함수
np.random.shuffle(index) # shuffle(): 주어진 배열을 무작위로 섞는 함수  
```


```python
print(index)
```

    [13 45 47 44 17 27 26 25 31 19 12  4 34  8  3  6 40 41 46 15  9 16 24 33
     30  0 43 32  5 29 11 36  1 21  2 37 35 23 39 10 22 18 48 20  7 42 14 28
     38]
    

- 배열 인덱싱


```python
# 35개 훈련 세트만들기
train_input = input_arr[index[:35]] 
train_target = target_arr[index[:35]]

# 14개 테스트 세트 만들기 
test_input = input_arr[index[35:]]
test_target = target_arr[index[35:]]
```

## 시각화 


```python
train_input[:,0] # 길이 리스트 
```




    array([32. , 12.4, 14.3, 12.2, 33. , 36. , 35. , 35. , 38.5, 33.5, 31.5,
           29. , 41. , 30. , 29. , 29.7, 11.3, 11.8, 13. , 32. , 30.7, 33. ,
           35. , 41. , 38.5, 25.4, 12. , 39.5, 29.7, 37. , 31. , 10.5, 26.3,
           34. , 26.5])




```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.scatter(train_input[:,0], train_input[:,1])
ax.scatter(test_input[:,0],test_input[:,1])
ax.set_xlabel("length")
ax.set_ylabel("weight")
plt.show()

```


    
![](images/day0630ml/output_47_0.png)
    



```python
kn = kn.fit(train_input, train_target)
```


```python
kn.score(test_input, test_target)
```




    1.0




```python
kn.predict(test_input)
```




    array([0, 0, 1, 0, 1, 1, 1, 0, 1, 1, 0, 1, 1, 0])




```python
test_target
```




    array([0, 0, 1, 0, 1, 1, 1, 0, 1, 1, 0, 1, 1, 0])





## 데이터 전처리
- 머신러닝시 데이터 전처리
- 결측치 처리, 이상치 처리


```python
fish_length = [25.4, 26.3, 26.5, 29.0, 29.0, 29.7, 29.7, 30.0, 30.0, 30.7, 31.0, 31.0, 
                31.5, 32.0, 32.0, 32.0, 33.0, 33.0, 33.5, 33.5, 34.0, 34.0, 34.5, 35.0, 
                35.0, 35.0, 35.0, 36.0, 36.0, 37.0, 38.5, 38.5, 39.5, 41.0, 41.0, 9.8, 
                10.5, 10.6, 11.0, 11.2, 11.3, 11.8, 11.8, 12.0, 12.2, 12.4, 13.0, 14.3, 15.0]
fish_weight = [242.0, 290.0, 340.0, 363.0, 430.0, 450.0, 500.0, 390.0, 450.0, 500.0, 475.0, 500.0, 
                500.0, 340.0, 600.0, 600.0, 700.0, 700.0, 610.0, 650.0, 575.0, 685.0, 620.0, 680.0, 
                700.0, 725.0, 720.0, 714.0, 850.0, 1000.0, 920.0, 955.0, 925.0, 975.0, 950.0, 6.7, 
                7.5, 7.0, 9.7, 9.8, 8.7, 10.0, 9.9, 9.8, 12.2, 13.4, 12.2, 19.7, 19.9]
```


```python
# cloumn_stack()활용
np.column_stack(([1,2,3],[4,5,6])) #2차원 배열로 만드는 과정 생략가능
```




    array([[1, 4],
           [2, 5],
           [3, 6]])




```python
fish_data = np.column_stack((fish_length, fish_weight))
print(fish_data[:5])
```

    [[ 25.4 242. ]
     [ 26.3 290. ]
     [ 26.5 340. ]
     [ 29.  363. ]
     [ 29.  430. ]]
    

- 종속변수 = Y = 타깃데이터 = Target 


```python
fish_target = np.concatenate((np.ones(35),np.zeros(14)))
print(fish_target)
```

    [1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1.
     1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0.
     0.]
    

## Scikit-learn 훈련세트와 테스트 세트 나누기 (외우기)



```python
from sklearn.model_selection import train_test_split
train_input, test_input, train_target, test_target = train_test_split(
    fish_data, fish_target, random_state = 42
)

train_input.shape, test_input.shape, train_target.shape, test_target.shape
```




    ((36, 2), (13, 2), (36,), (13,))



도미와 빙어가 잘 섞여 있는가?


```python
print(test_target)
```

    [1. 0. 0. 0. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
    

- 35(도미) : 14(빙어)
 +2.5 : 1
- 테스트 셋 (비율)
 + 3.3 : 1

## 층화샘플링
- 기초 통계, 설문 조사
- 비율
- 여론 조사
 + 남성 속옷을 구매하는 비율(남자9, 여자1)
 + 신제품(남자5, 여자5)


```python
train_input, test_input, train_target, test_target = train_test_split(
    fish_data, fish_target, random_state = 42)

print(test_target)


```

    [1. 0. 0. 0. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
    

이제 테스트 세트의 비율이 2.25:1 이다 

- 수상한 도미 한 마리


```python
from sklearn.model_selection import train_test_split
kn = KNeighborsClassifier()
kn.fit(train_input, train_target)
kn.score(test_input, test_target)
```




    1.0




```python
print(kn.predict([[25,150]]))
```

    [0.]
    


```python
import matplotlib.pyplot as plt
plt.scatter(train_input[:,0], train_input[:,1])
plt.scatter(25,150,marker="^")
plt.xlabel('length')
plt.ylabel('weight')
plt.show()

```


    
![](images/day0630ml/output_70_0.png)
    



```python
distance, indexes = kn.kneighbors([[25,150]])
```


```python
plt.scatter(train_input[:,0], train_input[:,1])
plt.scatter(25, 150, marker='^')
plt.scatter(train_input[indexes,0], train_input[indexes,1], marker='D')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_72_0.png)
    



```python
plt.scatter(train_input[:,0], train_input[:,1])
plt.scatter(25, 150, marker='^')
plt.scatter(train_input[indexes,0], train_input[indexes,1], marker='D')
plt.xlim((0, 1000))
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_73_0.png)
    


- p98
- 두 특성(길이와 무게)의 값이 놓인 범위가 매우 다음
- 두 특성의 스케일이 다름
 + 스케일이 같도록 통계처리 필요
 + Feature Engineering (피처엔지니어링)
- 머신러닝
 + 데이터 전처리(결측치 처리, 이상치 처리)
 + 데이터 분리
 +  Feature Engineering


```python

```

### 표준 점수
- z 점수 


```python
mean = np.mean(train_input, axis = 0)
std = np.std(train_input, axis=0)

print(mean, std)
```

    [ 26.175      418.08888889] [ 10.21073441 321.67847023]
    

- 표준 점수 구하기 


```python
# 브로드 캐스팅 서로 다른 배열을 계산할때 
print(train_input.shape, mean.shape, std.shape)
train_scaled = (train_input - mean) / std
```

    (36, 2) (2,) (2,)
    


```python
plt.scatter(train_scaled[:,0], train_scaled[:,1])
plt.scatter(25, 150, marker='^')
plt.xlabel('length')
plt.ylabel('weight')
plt.show() 
```


    
![](images/day0630ml/output_80_0.png)
    



```python
new = ([25, 150] - mean) / std
plt.scatter(train_scaled[:,0], train_scaled[:,1])
plt.scatter(new[0], new[1], marker='^')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_81_0.png)
    


통계 처리 전 : KNN --> 예측이 다름

통계 처리 후 : KNN --> 예측이 정확히 맞음

-- 통계 처리 --> Feature Engineering

- 모형 학습


```python
kn.fit(train_scaled, train_target)
```




    KNeighborsClassifier()




```python
# kn.score(test_input, test_target)
test_scaled = (test_input-mean) /std
kn.score(test_scaled, test_target)
```




    1.0



- 예측


```python
print(kn.predict([new]))
```

    [1.]
    


```python
distances, indexes = kn.kneighbors([new])
plt.scatter(train_scaled[:,0], train_scaled[:,1])
plt.scatter(new[0], new[1], marker='^')
plt.scatter(train_scaled[indexes,0], train_scaled[indexes,1], marker='D')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


    
![](images/day0630ml/output_88_0.png)
    


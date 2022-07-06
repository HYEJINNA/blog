---
title: "파이썬 기초"
date: '2022-06-27'
---

- 기초를 배운다. 

```python
print("Hello World")

```

    Hello World
    


```python

```



## 제목1
- 파이썬 입문

### 소제목1
- 여기는 소제목 



```python
print(1+1)
```

    2
    



# print() 함수 사용
print 


```python
# print() 함수사용
print ("1줄 주석")

""" 
여러줄 주석 
쌍따옴표 3개를 입력해주세요
앞과 뒤로 
"""

print("여러줄 주석")

```

    1줄 주석
    여러줄 주석
    

## 주석처리
- 1줄 주석, 여러 줄 주석처리 
- 여러 줄 주석처리
 + 함수 또는 클래스를 문서화 할때 주로 사용

- 프로젝트 할때
 + 전체공정 100
 + 코드 / 코드 문서화/ 한글작업 문서화
 
  



## 변수 (Scalar)
  - 자료형
  - Scalar형 Non-Scalar형

## 수치형 자료형
  - int, float


```python
num_int = 1
print(num_int)
print(type(num_int))
```

    1
    <class 'int'>
    


```python
num_float = 0.1
print(num_float)
print(type (num_float))
```

    0.1
    <class 'float'>
    

## None 자료형
- Null값, 값이 정해지지 않은 자료형


```python
none_x = None
print(none_x)
print(type(none_x))
```

    None
    <class 'NoneType'>
    

## 사칙연산
- 정수형  사칙연산, 실수형 사칙연산
- 결괏값의 자료형

## 정수형 사칙연산


```python
a = 3
b = 2
print('a + b =', a+b)
print('a - b =', a-b)
print('a * b =', a*b)
print('a / b =', a/b)
```

    a + b = 5
    a - b = 1
    a * b = 6
    a / b = 1.5
    

## 실수형 사칙연산


```python
a = 1.5
b = 2.5
print('a + b =', a+b)
```

    a + b = 4.0
    

## 논리형 연산자
- Bool 형
- True와 False 값으로 정의
- 조건식
 + 교집합(=and), 합집합(=or)


```python
print(True and True)
print(True and False)
print(False and True)
print(False and False)
```

    True
    False
    False
    False
    


```python
print(True or True)
print(True or False)
print(False or True)
print(False or False)
```

    True
    True
    True
    False
    

## 비교 연산자
- 비교 연산자는 부동호를 의미한다


```python
print(4>3) # 참 = True
print(4<3) # 거짓 = False

print(4>3 or 4<3) #False
```

    True
    False
    True
    

## 논리형 & 비교 연산자 응용

- input ()
- 형변환
- 데이터를 타입으로 바꾸는 것


```python
var = input("숫자를 입력하세요!")
print(var)
print(type(var))
```

    숫자를 입력하세요!1
    1
    <class 'str'>
    


```python
var = int(input("숫자를 입력하세요!"))
print(var)
print(type(var))
```

    숫자를 입력하세요!8
    8
    <class 'int'>
    


```python
num1 = int(input("첫 번째 숫자를 입력하세요!"))
num2 = int(input("두 번째 숫자를 입력하세요!"))
num3 = int(input("세 번째 숫자를 입력하세요!"))
num4 = int(input("네 번째 숫자를 입력하세요!"))
```

    첫 번째 숫자를 입력하세요!4
    두 번째 숫자를 입력하세요!100
    세 번째 숫자를 입력하세요!8
    네 번째 숫자를 입력하세요!200
    


```python
var1 = num1 >= num2 # False
var2 = num3 < num4 # True

print(var1 and var2) # True

```

    False
    

## String
- Non Scalar


```python
print('Hello World')
print("Hello World")

print("'Hellp World'")
print('"Hellp World"')
```

    Hello World
    Hello World
    'Hellp World'
    "Hellp World"
    

## String Operatos
- 문자열 연산자
- +,*가능


```python
str1 = "Hello"
str2 = "World"
print(str1 + str2)
```

    HelloWorld
    

## 문자열 인덱싱
- 인덱싱은 0번째 부터 시작


```python
greeting = "Hello Kaggle"
i = 7
# print(greeting)
print(greeting[i])
print(greeting[7])
```

    a
    a
    


```python
greeting = "Hello Kaggle"
i = int(input("숫자를 입력하세요!"))
print(greeting[i])

```

    숫자를 입력하세요!6
    K
    

## 슬라이싱


```python
greeting = "Hello Kaggle"
# print(greeting[시작인덱스: 끝인덱스-1]) > 외우는 방법밖에 없음
print(greeting[0:2])
print(greeting[:8])
print(greeting[6:])
print(greeting[0:10:2])
print(greeting[0:10:3])
print(greeting[0:10:4])
```

    He
    Hello Ka
    Kaggle
    HloKg
    HlKg
    Hog
    


```python
alphabet_letter = "abcdefghijklmnopqsrtuvwxyz"
print(alphabet_letter[0:5:2])
```

    ace
    


```python
greeting = "Hello Kaggle"
print(greeting[11])
```

    e
    

## 문자열 관련 메서드 
 + split( )
 + sort()
 + etc

## 리스트 
- [ ] 로 표시 
- [item, item2, item3]



```python
a = [] # 빈리스트 
a_func = list() # 빈 리스트 생성
b = [1]
d = [1,2,['apple'], 'apple']
print(d)
```

    [1, 2, ['apple'], 'apple']
    

## 리스트 값 수정하기
- 리스트 값 수정


```python
a = [0, 1, 2]
a[0] = "값"
print(a
      )
```

    [0, '값', 2]
    

## 리스트 값 추가하기 
- 메서드 사용


```python
a = [100, 200, 300]
a.append(400)

print(a)

a.append([500,600])
print(a)

```

    [100, 200, 300, 400]
    [100, 200, 300, 400, [500, 600]]
    


```python
a = [100, 200, 300]
a.append(400)

print(a)

a.extend([400,500])
print(a)
```

    [100, 200, 300, 400]
    [100, 200, 300, 400, 400, 500]
    

## 삽입
- insert(인덱스 위치, 값)


```python
a = [100,200,300]
a.insert(1,1000)
print(a)
```

    [100, 1000, 200, 300]
    

## 리스트 값 삭제하기 
- remove(),del


```python
a = [1,2,1,2,10]
a.remove(10)
print(a)
```

    [1, 2, 1, 2]
    

- del


```python
a = [0,1,2,3,4]
del a[1]
print(a)

del a[0:2]
print(a)
```

    [0, 2, 3, 4]
    [3, 4]
    

- pop()


```python
a = [1,2,3,4,5]
a.pop(1)

print(a)
```

    [1, 3, 4, 5]
    


```python
a = [1,2,3,4,5]
rem = a.pop(1)
print(a)
print(rem)
x= a.pop()
print(a)
print(x)
```

    [1, 3, 4, 5]
    2
    [1, 3, 4]
    5
    

- clear(): 리스트 내 모든 값 삭제 

- index("값"): 값의 위치를 불러옴


```python
a = [1,4,5,2,3,]
b = ["철수","영희","길동"]
a.index(4)
print(a,a.index(4))
print(b,b.index("길동"))

```

    [1, 4, 5, 2, 3] 1
    ['철수', '영희', '길동'] 2
    

- sort: 리스트의 정렬


```python
a = [14,5,2,3]
a.sort()
a.sort(reverse=True)
print(a)

# help(list.sort)
help(list.index)

```

    [14, 5, 3, 2]
    Help on method_descriptor:
    
    index(self, value, start=0, stop=9223372036854775807, /)
        Return first index of value.
        
        Raises ValueError if the value is not present.
    
    

## 튜플
- 면접질문 : 리스트와 튜플의 차이가 뭐에요?
간단명료하게 대답
- 리스트 : []
 + 수정, 삭제, 추가
- 튜플 : () 
 + 모두 안됨
 + 조금 더 빠르게 실행된다는 얘기가 있음


```python
tuple1 = (0)
tuple2 = (0,)
tuple3 = 0,1,2

print(type(tuple1))
print(type(tuple2))
print(type(tuple3))

print(tuple1)
print(tuple2)
print(tuple3)
```

    <class 'int'>
    <class 'tuple'>
    <class 'tuple'>
    0
    (0,)
    (0, 1, 2)
    


```python
a = (0,1,2,3,'a')
del a[4]
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-52-2674375e5bd4> in <module>()
          1 a = (0,1,2,3,'a')
    ----> 2 del a[4]
    

    TypeError: 'tuple' object doesn't support item deletion



```python
a = (0,1,2,3,'a')
a[4] = 4
print(a)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-53-de27a2d07797> in <module>()
          1 a = (0,1,2,3,'a')
    ----> 2 a[4] = 4
          3 print(a)
    

    TypeError: 'tuple' object does not support item assignment


## 튜플연산자
- 문자열 연산자
- +,*


```python
t1 = [0,1,2]
t2 = [3,4,5]
print(t1+t2)
```

    [0, 1, 2, 3, 4, 5]
    

## 딕셔너리
- Key(키)와 Value(값)으로 구성됨
- 슬라이싱! = (값의 순서가 존재해야 한다)
- 순서라는 개념 자체가 존재하지 않는다 


```python
temp_dict = {'teacher':'evan',
             'class':15,
             'student':['s1','s2','s3']}
print(temp_dict['teacher'])
print(temp_dict['class'])
print(temp_dict['student'])


```

    evan
    15
    ['s1', 's2', 's3']
    

- keys()값만 출력


```python
temp_dict.keys()

```




    dict_keys(['teacher', 'class', 'student'])




```python
list(temp_dict.keys())
```




    ['teacher', 'class', 'student']



- values()값만 출력


```python
temp_dict.values()
```




    dict_values(['evan', 15, ['s1', 's2', 's3']])



- items() key-value 쌍으로, list와 tuple형태로 변환


```python
temp_dict.items()
```




    dict_items([('teacher', 'evan'), ('class', 15), ('student', ['s1', 's2', 's3'])])



## 조건문


```python
a = int(input("숫자를 입력하세요!"))
if a>5:
  print("a는 5보다 크다")
elif a>0:
  print("a는 0보다 크다")
elif a>-5:
  print("a는 -5보다 크다")
else:
  print("a는 매우작다")
```

    숫자를 입력하세요!8
    a는 5보다 크다
    

## 반복문


```python
# Hello World를 100번 출력하세요
for i in range(100):  #i : idx
  print(i)
 # print("Hello World") 
  print(i+1,"Hello World")



```

    0
    1 Hello World
    1
    2 Hello World
    2
    3 Hello World
    3
    4 Hello World
    4
    5 Hello World
    5
    6 Hello World
    6
    7 Hello World
    7
    8 Hello World
    8
    9 Hello World
    9
    10 Hello World
    10
    11 Hello World
    11
    12 Hello World
    12
    13 Hello World
    13
    14 Hello World
    14
    15 Hello World
    15
    16 Hello World
    16
    17 Hello World
    17
    18 Hello World
    18
    19 Hello World
    19
    20 Hello World
    20
    21 Hello World
    21
    22 Hello World
    22
    23 Hello World
    23
    24 Hello World
    24
    25 Hello World
    25
    26 Hello World
    26
    27 Hello World
    27
    28 Hello World
    28
    29 Hello World
    29
    30 Hello World
    30
    31 Hello World
    31
    32 Hello World
    32
    33 Hello World
    33
    34 Hello World
    34
    35 Hello World
    35
    36 Hello World
    36
    37 Hello World
    37
    38 Hello World
    38
    39 Hello World
    39
    40 Hello World
    40
    41 Hello World
    41
    42 Hello World
    42
    43 Hello World
    43
    44 Hello World
    44
    45 Hello World
    45
    46 Hello World
    46
    47 Hello World
    47
    48 Hello World
    48
    49 Hello World
    49
    50 Hello World
    50
    51 Hello World
    51
    52 Hello World
    52
    53 Hello World
    53
    54 Hello World
    54
    55 Hello World
    55
    56 Hello World
    56
    57 Hello World
    57
    58 Hello World
    58
    59 Hello World
    59
    60 Hello World
    60
    61 Hello World
    61
    62 Hello World
    62
    63 Hello World
    63
    64 Hello World
    64
    65 Hello World
    65
    66 Hello World
    66
    67 Hello World
    67
    68 Hello World
    68
    69 Hello World
    69
    70 Hello World
    70
    71 Hello World
    71
    72 Hello World
    72
    73 Hello World
    73
    74 Hello World
    74
    75 Hello World
    75
    76 Hello World
    76
    77 Hello World
    77
    78 Hello World
    78
    79 Hello World
    79
    80 Hello World
    80
    81 Hello World
    81
    82 Hello World
    82
    83 Hello World
    83
    84 Hello World
    84
    85 Hello World
    85
    86 Hello World
    86
    87 Hello World
    87
    88 Hello World
    88
    89 Hello World
    89
    90 Hello World
    90
    91 Hello World
    91
    92 Hello World
    92
    93 Hello World
    93
    94 Hello World
    94
    95 Hello World
    95
    96 Hello World
    96
    97 Hello World
    97
    98 Hello World
    98
    99 Hello World
    99
    100 Hello World
    

- for loop if 조건문
- 문자열, 리스트 등 -->시퀀스 데이터


```python
a = "Kaggle"
# g가 시작하면 반복문을 멈추세요
for x in a:
  print(x)
  if x=='g':
    break
  # print(x)
```

    K
    a
    g
    

- enumerate()


```python
alphabets = ['A', 'B', 'C']
for index, value in enumerate(alphabets):
  print(index, value)
```

    0 A
    1 B
    2 C
    

## 리스트 컴프리헨션
list comprehension
- 반복문을 한줄로 표시한다


```python
fruits = ['apple', 'kiwi','mango']
newlists = []

#알파벳 a가 있는 과일만 추출후, 새로운 리스트에 담기
for fruit in fruits:
  #print(fruit)
  if "a" in fruit:
    newlists.append(fruit)
  print(newlists)  
```

    ['apple']
    ['apple']
    ['apple', 'mango']
    


```python
# 리스트 컴프리헨션
newlist = [fruit for fruit in fruits if 'a' in fruit]
print(newlist)
```

    ['apple', 'mango']
    

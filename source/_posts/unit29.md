---
title: "코딩도장 Unit29"
date: '2022-06-28'
---



```python
hello()

def hello():
  print('Hello, world!')
```

    Hello world!
    


```python
def hello():
    pass
```


```python
def add(a,b):
  print(a+b)

add(10,20)
```

    30
    


```python
def add(a, b):
    """이 함수는 a와 b를 더한 뒤 결과를 반환하는 함수입니다."""
    return a + b
 
x = add(10, 20)       # 함수를 호출해도 독스트링은 출력되지 않음
print(x)
 
print(add.__doc__)    # 함수의 __doc__로 독스트링 출력
```

    30
    이 함수는 a와 b를 더한 뒤 결과를 반환하는 함수입니다.
    


```python
def add(a,b):
  return a+b

x = add(10,20)
x



```




    30




```python
 print(add(10, 20))
```

    30
    


```python
def one():
  return 1

x = one()
x
```




    1




```python
 def not_ten(a):
   if a == 10:
      return
   print(a, '입니다.',sep='')
  
not_ten(5)
```

    5입니다.
    


```python
def add_sub(a, b):
  return a + b, a - b

x, y = add_sub(10, 20)
x

```




    30




```python
y
```




    -10




```python
x, y = (30, -10)
x
```




    30




```python
y
```




    -10




```python
def one_two():
   return 1, 2    # return (1, 2)와 같음
```


```python
def one_two():
  return [1, 2]

x, y = one_two()
print(x, y)
```

    1 2
    


```python
def mul(a, b):
  c = a * b
  return c

def add(a, b):
    c = a + b
    print(c)
    d = mul(a, b)
    print(d)
 
x = 10
y = 20
add(x, y)
```

    30
    200
    

다음 소스 코드를 완성하여 x를 y로 나누었을 때의 몫과 나머지가 출력되게 만드세요.


```python
x = 10
y = 3
 
def get_quotient_remainder(a, b):
    return a // b, a % b
                                 
                                 
quotient, remainder = get_quotient_remainder(x, y)
print('몫: {0}, 나머지: {1}'.format(quotient, remainder))
```

    몫: 3, 나머지: 1
    

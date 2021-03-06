---
title: "seaborn"
date: '2022-07-06'
---

## 데이터 분석(머신러닝, 딥러닝) 프로세스
- 데이터 불러오기
 + CSV, 오라클, MySQL, PostgreSQL, 클라우드DB
연동
- 탐색적 자료분석
 + 데이터 전처리 및 가공
- 잠정적인 컬럼의 갯수를 지정
- 머신러닝 모델 (=통계모델링, t.test, 분산분석, 교차분석)
- 머신러닝 모델의 경우 배포(현재는 다루지 않음)
 + JSP- 스프링 웹개발시, 배우게 됨
- 통계 모델링 경우, p-value값 기준으로, 귀무가설 및 대립가설 검정
- (공통) 결과 보고서를 작성하기
 + PPT 만들기


## 그래프 복습
- 수치형 데이터 시각화
- 범주형 데이터 시각화
- 데이터 관계 시각화
- matplotlib 라이브러리 방법(복잡)
- seaborn 라이브러리 방법(단순)
 + 복잡한 그래프그릴때 -> marplotlib
 + 1줄 그래프 -> seaborn

## 수치형 데이터 시각화
- Python의 Seaborn 패키지에는 다양한 내장데이터가 있다
- 연습용으로 활용가능


```python
import seaborn as sns
titanic = sns.load_dataset('titanic')
titanic.head()
```





  <div id="df-a367cd23-1a74-4500-8c60-d518e7c7e004">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-a367cd23-1a74-4500-8c60-d518e7c7e004')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-a367cd23-1a74-4500-8c60-d518e7c7e004 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-a367cd23-1a74-4500-8c60-d518e7c7e004');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 히스토그램
sns.histplot(data = titanic, x = 'age')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9d7e7810>




    
![](images/0706/output_4_1.png)
    



```python
sns.histplot(data = titanic, x = 'age', bins=10, hue='alive', multiple='stack')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9b211150>




    
![](images/0706/output_5_1.png)
    



```python
# 커넬 밀도 추정 함수 그래프
# 연속형 데이터 1개만 쓸때 사용
sns.kdeplot(data=titanic, x='age')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9b9600d0>




    
![](images/0706/output_6_1.png)
    


- 위 그래프 설명....


```python
sns.kdeplot(data=titanic, x='age', hue='alive', multiple='stack')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9b11d9d0>




    
![](images/0706/output_8_1.png)
    


## 분포도
- 수치형 데이터 한개 컬럼의 분포를 나타내는 그래프 
- 정규분포인가?


```python
sns.displot(data=titanic, x='age')
```




    <seaborn.axisgrid.FacetGrid at 0x7f1e9b33de90>




    
![](images/0706/output_10_1.png)
    



```python
sns.displot(data=titanic, x='age', kind='kde')
```




    <seaborn.axisgrid.FacetGrid at 0x7f1e96754710>




    
![](images/0706/output_11_1.png)
    



```python
sns.displot(data=titanic, x='age', kde= True)
```




    <seaborn.axisgrid.FacetGrid at 0x7f1e96754c50>




    
![](images/0706/output_12_1.png)
    


## 범주형 데이터 시각화
- x축 범주형, y축 수치데이터 


```python
# 막대 그래프
sns.barplot(x='class', y='fare',data=titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e96626090>




    
![](images/0706/output_14_1.png)
    



```python
# 포인트 플롯
sns.pointplot(x='class', y='fare', data=titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e965c11d0>




    
![](images/0706/output_15_1.png)
    


- 박스플롯
- 제 1사분위 : 전체 데이터 중 하위 25%
- 사분위 범위 수(IQR) : 제 3사분위 - 제 1사분위
- 최댓값 : 제 3사분위 + (1.5 * IQ)


```python
# boxplot
sns.boxplot(x='class', y='age',data=titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9652f0d0>




    
![](images/0706/output_17_1.png)
    



```python
# 바이올린 플롯
sns.violinplot(x = 'class', y = 'age', hue = 'sex', data = titanic, split = True);
```


    
![](images/0706/output_18_0.png)
    


## 카운트 플롯
- 범주형 데이터의 갯수 확인 할때 사용



```python
sns.countplot(x = 'alive', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e99086bd0>




    
![](images/0706/output_20_1.png)
    


## 데이터 관계 시각화
- 여러 데이터 사이의 관계도 파악을 위한 그래프

### 히트맵


```python
flights = sns.load_dataset('flights')
flights.head()
```





  <div id="df-a2cd537f-318f-4ef7-8db3-e31a3ce65580">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>month</th>
      <th>passengers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1949</td>
      <td>Jan</td>
      <td>112</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1949</td>
      <td>Feb</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1949</td>
      <td>Mar</td>
      <td>132</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1949</td>
      <td>Apr</td>
      <td>129</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1949</td>
      <td>May</td>
      <td>121</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-a2cd537f-318f-4ef7-8db3-e31a3ce65580')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-a2cd537f-318f-4ef7-8db3-e31a3ce65580 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-a2cd537f-318f-4ef7-8db3-e31a3ce65580');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




- 판다스에서 복사해서 응용


```python
import pandas as pd

df = pd.DataFrame({'foo': ['one', 'one', 'one', 'two', 'two',
                           'two'],
                   'bar': ['A', 'B', 'C', 'A', 'B', 'C'],
                   'baz': [1, 2, 3, 4, 5, 6],
                   'zoo': ['x', 'y', 'z', 'q', 'w', 't']})
df
```





  <div id="df-1ae0e23d-eda2-4670-a77a-bee362132409">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>foo</th>
      <th>bar</th>
      <th>baz</th>
      <th>zoo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>one</td>
      <td>A</td>
      <td>1</td>
      <td>x</td>
    </tr>
    <tr>
      <th>1</th>
      <td>one</td>
      <td>B</td>
      <td>2</td>
      <td>y</td>
    </tr>
    <tr>
      <th>2</th>
      <td>one</td>
      <td>C</td>
      <td>3</td>
      <td>z</td>
    </tr>
    <tr>
      <th>3</th>
      <td>two</td>
      <td>A</td>
      <td>4</td>
      <td>q</td>
    </tr>
    <tr>
      <th>4</th>
      <td>two</td>
      <td>B</td>
      <td>5</td>
      <td>w</td>
    </tr>
    <tr>
      <th>5</th>
      <td>two</td>
      <td>C</td>
      <td>6</td>
      <td>t</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-1ae0e23d-eda2-4670-a77a-bee362132409')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-1ae0e23d-eda2-4670-a77a-bee362132409 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-1ae0e23d-eda2-4670-a77a-bee362132409');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df.pivot(index = 'foo', columns = 'bar', values = 'baz')
```





  <div id="df-7a884986-8779-41bf-88f8-aa6b83e185b2">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>bar</th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
    <tr>
      <th>foo</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>two</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-7a884986-8779-41bf-88f8-aa6b83e185b2')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-7a884986-8779-41bf-88f8-aa6b83e185b2 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-7a884986-8779-41bf-88f8-aa6b83e185b2');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
flights
```





  <div id="df-2b67b019-ba04-455e-9938-7eb965a94136">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>month</th>
      <th>passengers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1949</td>
      <td>Jan</td>
      <td>112</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1949</td>
      <td>Feb</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1949</td>
      <td>Mar</td>
      <td>132</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1949</td>
      <td>Apr</td>
      <td>129</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1949</td>
      <td>May</td>
      <td>121</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>139</th>
      <td>1960</td>
      <td>Aug</td>
      <td>606</td>
    </tr>
    <tr>
      <th>140</th>
      <td>1960</td>
      <td>Sep</td>
      <td>508</td>
    </tr>
    <tr>
      <th>141</th>
      <td>1960</td>
      <td>Oct</td>
      <td>461</td>
    </tr>
    <tr>
      <th>142</th>
      <td>1960</td>
      <td>Nov</td>
      <td>390</td>
    </tr>
    <tr>
      <th>143</th>
      <td>1960</td>
      <td>Dec</td>
      <td>432</td>
    </tr>
  </tbody>
</table>
<p>144 rows × 3 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-2b67b019-ba04-455e-9938-7eb965a94136')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-2b67b019-ba04-455e-9938-7eb965a94136 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-2b67b019-ba04-455e-9938-7eb965a94136');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# flights['year'].value_counts()
flights_pivot = flights.pivot(index = 'month', columns = 'year', values = 'passengers')
flights_pivot
```





  <div id="df-63cc829c-9ecb-46d1-8b3f-826eb006276d">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>year</th>
      <th>1949</th>
      <th>1950</th>
      <th>1951</th>
      <th>1952</th>
      <th>1953</th>
      <th>1954</th>
      <th>1955</th>
      <th>1956</th>
      <th>1957</th>
      <th>1958</th>
      <th>1959</th>
      <th>1960</th>
    </tr>
    <tr>
      <th>month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan</th>
      <td>112</td>
      <td>115</td>
      <td>145</td>
      <td>171</td>
      <td>196</td>
      <td>204</td>
      <td>242</td>
      <td>284</td>
      <td>315</td>
      <td>340</td>
      <td>360</td>
      <td>417</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>118</td>
      <td>126</td>
      <td>150</td>
      <td>180</td>
      <td>196</td>
      <td>188</td>
      <td>233</td>
      <td>277</td>
      <td>301</td>
      <td>318</td>
      <td>342</td>
      <td>391</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>132</td>
      <td>141</td>
      <td>178</td>
      <td>193</td>
      <td>236</td>
      <td>235</td>
      <td>267</td>
      <td>317</td>
      <td>356</td>
      <td>362</td>
      <td>406</td>
      <td>419</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>129</td>
      <td>135</td>
      <td>163</td>
      <td>181</td>
      <td>235</td>
      <td>227</td>
      <td>269</td>
      <td>313</td>
      <td>348</td>
      <td>348</td>
      <td>396</td>
      <td>461</td>
    </tr>
    <tr>
      <th>May</th>
      <td>121</td>
      <td>125</td>
      <td>172</td>
      <td>183</td>
      <td>229</td>
      <td>234</td>
      <td>270</td>
      <td>318</td>
      <td>355</td>
      <td>363</td>
      <td>420</td>
      <td>472</td>
    </tr>
    <tr>
      <th>Jun</th>
      <td>135</td>
      <td>149</td>
      <td>178</td>
      <td>218</td>
      <td>243</td>
      <td>264</td>
      <td>315</td>
      <td>374</td>
      <td>422</td>
      <td>435</td>
      <td>472</td>
      <td>535</td>
    </tr>
    <tr>
      <th>Jul</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>230</td>
      <td>264</td>
      <td>302</td>
      <td>364</td>
      <td>413</td>
      <td>465</td>
      <td>491</td>
      <td>548</td>
      <td>622</td>
    </tr>
    <tr>
      <th>Aug</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>242</td>
      <td>272</td>
      <td>293</td>
      <td>347</td>
      <td>405</td>
      <td>467</td>
      <td>505</td>
      <td>559</td>
      <td>606</td>
    </tr>
    <tr>
      <th>Sep</th>
      <td>136</td>
      <td>158</td>
      <td>184</td>
      <td>209</td>
      <td>237</td>
      <td>259</td>
      <td>312</td>
      <td>355</td>
      <td>404</td>
      <td>404</td>
      <td>463</td>
      <td>508</td>
    </tr>
    <tr>
      <th>Oct</th>
      <td>119</td>
      <td>133</td>
      <td>162</td>
      <td>191</td>
      <td>211</td>
      <td>229</td>
      <td>274</td>
      <td>306</td>
      <td>347</td>
      <td>359</td>
      <td>407</td>
      <td>461</td>
    </tr>
    <tr>
      <th>Nov</th>
      <td>104</td>
      <td>114</td>
      <td>146</td>
      <td>172</td>
      <td>180</td>
      <td>203</td>
      <td>237</td>
      <td>271</td>
      <td>305</td>
      <td>310</td>
      <td>362</td>
      <td>390</td>
    </tr>
    <tr>
      <th>Dec</th>
      <td>118</td>
      <td>140</td>
      <td>166</td>
      <td>194</td>
      <td>201</td>
      <td>229</td>
      <td>278</td>
      <td>306</td>
      <td>336</td>
      <td>337</td>
      <td>405</td>
      <td>432</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-63cc829c-9ecb-46d1-8b3f-826eb006276d')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-63cc829c-9ecb-46d1-8b3f-826eb006276d button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-63cc829c-9ecb-46d1-8b3f-826eb006276d');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
# 위 테이블의 시각화
sns.heatmap(data = flights_pivot)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9b2f7dd0>




    
![](images/0706/output_29_1.png)
    



```python
# 라인 플롯
sns.lineplot(x='year', y='passengers',data=flights)

```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e95f3ae90>




    
![](images/0706/output_30_1.png)
    



```python
# 산점도 
tips = sns.load_dataset('tips')
tips.head()
```





  <div id="df-82fb9526-10b7-4b8c-a4f9-7172c364d5da">
    <div class="colab-df-container">
      <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-82fb9526-10b7-4b8c-a4f9-7172c364d5da')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-82fb9526-10b7-4b8c-a4f9-7172c364d5da button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-82fb9526-10b7-4b8c-a4f9-7172c364d5da');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['images/0706/output_type'] = 'display_data';
          await google.colab.images/0706/output.renderimages/0706/output(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




- 두 개의 연속형 데이터 


```python
sns.scatterplot(x='total_bill', y='tip', data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e96293d90>




    
![](images/0706/output_33_1.png)
    



```python
sns.scatterplot(x='total_bill', y='tip', hue='time',data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e96257c10>




    
![](images/0706/output_34_1.png)
    



```python
sns.scatterplot(x='total_bill', y='tip', hue='sex',data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e961f1150>




    
![](images/0706/output_35_1.png)
    



```python
# 회귀선
sns.regplot(x='total_bill', y='tip', data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e9675e650>




    
![](images/0706/output_36_1.png)
    



```python
## 머신러닝 리뷰
- 가장 인기있는 모델
 + LightGBM, XGboost
```

## 선형회귀
- 선형 회귀식을 찾는 것이 중요
- y=3x+4에 근사한 데이터 50개 생성


```python
import numpy as np
import pandas as pd

# 시드값 고정
np.random.seed(0)
intercept = 4 #절편, 상수
slope = 3 # 기울기

# 변동성 주기위해 노이즈 생성
noise = np.random.randn(50,1)
x=5 * np.random.rand(50,1) #0과 5사이의 실숫값을 50개 생성
y=slope*x+intercept+noise

# 데이터 프레임 생성
data = pd.DataFrame({'X' : x[:, 0], 'Y' : y[:, 0]})
print(data)
```

               X          Y
    0   0.794848   8.148596
    1   0.551876   6.055784
    2   3.281648  14.823682
    3   0.690915   8.313637
    4   0.982912   8.816293
    5   1.843626   8.553600
    6   4.104966  17.264987
    7   0.485506   5.305162
    8   4.189725  16.465955
    9   0.480492   5.852075
    10  4.882297  18.790936
    11  2.343256  12.484042
    12  4.883805  19.412454
    13  3.024228  13.194358
    14  3.696318  15.532817
    15  0.195939   4.921491
    16  1.414035   9.736184
    17  0.600983   5.597790
    18  1.480701   8.755171
    19  0.593639   4.926820
    20  1.589916   6.216758
    21  2.071315  10.867564
    22  0.320737   5.826649
    23  3.462361  13.644917
    24  2.833007  14.768776
    25  1.326947   6.526477
    26  2.616240  11.894479
    27  0.469703   5.221924
    28  2.879732  14.171977
    29  4.646481  19.408802
    30  1.592845   8.933482
    31  3.337052  14.389318
    32  0.658989   5.089182
    33  3.581636  12.764112
    34  1.447030   7.993179
    35  0.915957   6.904219
    36  2.932565  14.027985
    37  0.100538   5.503993
    38  4.144700  16.046774
    39  0.023477   3.768129
    40  3.389083  13.118695
    41  1.350040   6.630102
    42  3.675970  13.321640
    43  4.810943  20.383604
    44  1.243766   7.221645
    45  2.880787  12.204286
    46  2.960210  11.627834
    47  2.861260  13.361269
    48  1.115408   5.732327
    49  4.763745  18.078495
    


```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.scatter(data['X'], data['Y'])
plt.show()
```


    
![](images/0706/output_40_0.png)
    



```python
import seaborn as sns 
sns.scatterplot(x = 'X', y = 'Y', data = data)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f1e95e82410>




    
![](images/0706/output_41_1.png)
    


## 선형 회귀 모형 훈련
- 모형 생성 후, 회귀계수 3과 y절편 4에 근사한 값이 나와야 한다


```python
from sklearn.linear_model import LinearRegression
lr_model = LinearRegression()
lr_model.fit(x,y)

print('y절편:', lr_model.intercept_)
print('회귀절편계수:', lr_model.coef_)
```

    y절편: [4.05757639]
    회귀절편계수: [[3.03754061]]
    


```python
# 예측값
y_pred = lr_model.predict(x)
fig, ax = plt.subplots()
ax.scatter(x, y)
ax.plot(x, y_pred, color='green')

# slope, intercept 
label = 'slope: {}\nintercept: {}'.format(round(lr_model.coef_[0][0], 2), round(lr_model.intercept_[0], 2))
ax.text(3.5, 4, label, style ='italic', 
        fontsize = 10, color ="green")
plt.show()
```


    
![](images/0706/output_44_0.png)
    


## 로지스틱 회귀



```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(arr, scale=1):
    arr = np.asarray(arr)
    result = 1/(1 + np.exp(-arr*scale))
    return result

x = np.linspace(-6, 6)
y = sigmoid(x)

fig, ax = plt.subplots()
ax.plot(x, y)
ax.grid(which='major', axis='y', linestyle='--')
ax.axvline(x=0, color='r', linestyle='--', linewidth=1)
ax.set_ylim(0,1)
ax.set_yticks([0, 1, 0.5])
ax.text(0-0.1, 0.5, '0.5', ha='right')
ax.set_title('Sigmoid Graph')
plt.show()








```


    
![](images/0706/output_46_0.png)
    



```python
# 라이브러리 불러오기
import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix

# 데이터 가져오기
x = np.arange(10).reshape(-1, 1)
y = np.array([0, 0, 0, 0, 0, 1, 1, 1, 1, 1])

# 모델 생성 및 학습
model = LogisticRegression(solver='liblinear', C=10.0, random_state=0)
model.fit(x, y)
```




    LogisticRegression(C=10.0, random_state=0, solver='liblinear')




```python
# 모형 평가
p_pred = model.predict_proba(x)
print('p_perd', p_pred, sep='Wn')
```

    p_perdWn[[0.97979027 0.02020973]
     [0.94958202 0.05041798]
     [0.87976149 0.12023851]
     [0.73975066 0.26024934]
     [0.52477284 0.47522716]
     [0.30020373 0.69979627]
     [0.1428487  0.8571513 ]
     [0.06080627 0.93919373]
     [0.02453462 0.97546538]
     [0.00967652 0.99032348]]
    


```python
y_pred = model.predict(x)
print('y_pred',y_pred)
```

    y_pred [0 0 0 0 0 1 1 1 1 1]
    


```python
fig, ax = plt.subplots()
ax.scatter(x, y)
ax.plot(x, p_pred[:, 1], color = 'black',  marker='o', markersize=6)
ax.plot()

ax.set_xticks(x)
ax.set_yticks(np.arange(0, 1.1, 0.1))

ax.grid(which='major', alpha=0.5)
plt.show()
```


    
![](images/0706/output_50_0.png)
    



```python
conf_m = confusion_matrix(y, y_pred)
print(conf_m)
```

    [[5 0]
     [0 5]]
    


```python
cm = confusion_matrix(y, y_pred)

fig, ax = plt.subplots(figsize=(8, 8))
ax.imshow(cm, cmap = 'Pastel2')
ax.grid(False)
ax.xaxis.set(ticks=(0, 1), ticklabels=('Predicted 0', 'Predicted 1'))
ax.yaxis.set(ticks=(0, 1), ticklabels=('Actual 0', 'Actual 1'))
ax.set_ylim(1.5, -0.5)
for i in range(2):
    for j in range(2):
        ax.text(j, i, cm[i, j], ha='center', va='center', color='black', fontsize=20)
plt.show()
```


    
![](images/0706/output_52_0.png)
    


https://matplotlib.org/stable/tutorials/colors/colormaps.htm 색상참고

## 결정트리
- 분류와 회귀 문제에 모두 사용가능
### 주요 개념
- 작동 원리
  + 데이터를 가장 잘 구분하는 조건을 정함
  + 조건을 기준으로 데이터를 두 범주로 나눔
  + 나뉜 각 범주의 데이터를 구분하는 조건을 정함
  + 각 조건을 기준으로 데이터를 두 범주로 나눔
  + 언제까지 계속 분할할지 정한 후, 최종 결정 값을 구함
- 불순도(Impurity)
  + 한 범주 안에 서로 다른 데이터가 얼마나 섞여 있는지 나타냄
  + 흰색과 검은색이 50:50으로 섞여 있다 (불순도 최대)
  + 흰색과 검은색으로 완전 분리 되었다 (불순도 최소)
- 엔트로피(Entropy)
  + 불확실한 정도를 의미함( 0 - 1로 정함)
  + 흰색과 검은색이 50:50으로 섞여 있다_ 엔트로피 1
  + 흰색과 검은색으로 완전 분리 되었다_ 엔트로피 0
- 정보이득(Information Gain)
  + 1에서 엔트로피를 뺀 수치
  + 정보 이득을 최대화하는 방향(엔트로피를 최소화 하는 방향)으로 노드를 분할함
- 지니 불순도(Gini Impurity)
  + 지니 불순도 값이 클수록 불순도도 높고, 작을수록 불순도도 낮음 엔트로피와 마찬가지로 지니 불순도가 낮아지는 방향으로 노드 분할함


```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split 
import seaborn as sns 

# tips 데이터셋 
titanic = sns.load_dataset('titanic')
titanic.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 15 columns):
     #   Column       Non-Null Count  Dtype   
    ---  ------       --------------  -----   
     0   survived     891 non-null    int64   
     1   pclass       891 non-null    int64   
     2   sex          891 non-null    object  
     3   age          714 non-null    float64 
     4   sibsp        891 non-null    int64   
     5   parch        891 non-null    int64   
     6   fare         891 non-null    float64 
     7   embarked     889 non-null    object  
     8   class        891 non-null    category
     9   who          891 non-null    object  
     10  adult_male   891 non-null    bool    
     11  deck         203 non-null    category
     12  embark_town  889 non-null    object  
     13  alive        891 non-null    object  
     14  alone        891 non-null    bool    
    dtypes: bool(2), category(2), float64(2), int64(4), object(5)
    memory usage: 80.7+ KB
    

- survived의 비율을 구한다
 + 0 : 사망자
 + 1 : 생존자


```python
titanic['survived'].value_counts()
```




    0    549
    1    342
    Name: survived, dtype: int64




```python
# 데이터 추출
X = titanic[['pclass', 'parch', 'fare']]
y = titanic['survived']

# 훈련데이터, 테스트 데이터 분리
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify = y, test_size = 0.3, random_state=42)
X_train.shape, X_test.shape, y_train.shape, y_test.shape
```




    ((623, 3), (268, 3), (623,), (268,))




```python
tree_model = DecisionTreeClassifier()
tree_model.fit(X_train, y_train)

acc = tree_model.score(X_test, y_test)
print(f'모형 정확도 : {acc:.3f}') # 정확도 측정
```

    모형 정확도 : 0.675
    


```python
## 랜덤포레스트
```


```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split 
import seaborn as sns 

# tips 데이터셋 
titanic = sns.load_dataset('titanic')

X = titanic[['pclass', 'parch', 'fare']]
y = titanic['survived']

# 훈련데이터, 테스트 데이터 분리
X_train, X_test, y_train, y_test = train_test_split(X, y, stratify = y, test_size = 0.3, random_state=42)

# 모델 훈련
rf_model = RandomForestClassifier(random_state=42) # 랜덤 포레스트 정의
rf_model.fit(X_train, y_train)

acc = rf_model.score(X_test, y_test)
print(f'모형 정확도 : {acc:.3f}') # 정확도 측정
```

    모형 정확도 : 0.675
    

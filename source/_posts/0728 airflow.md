---
title: "Apache Airflow 데이터 파이프라인 구축"
date: '2022-07-28'
---

## **Apache Airflow ?**

Apache Airflow is an open source platform to **programmatically author, schedule, and monitor**

workflows.  

Apache Airflow는 **프로그래밍 방식으로 워크플로우를 작성, 예약 및 모니터링**하는 오픈 소스 플랫폼이다.  이 작업은 실시간 데이터 처리이며, 현업에서 많이 쓰고 있다.

   1. 

>pip3 install faker pandas 설치

![](images/0728 airflow/Untitled.png)

설치 완료 후 VS code로 

>**code .**

    2. 

먼저 가상환경에 들어가기 

human@DESKTOP-8BF1BS3:~/airflow$ source venv/bin/activate

    

   3. 

파이썬 파일 만들고, 내용 입력 후 실행 결과 확인 

![](images/0728 airflow/Untitled%201.png)

   4. 

**Ubuntu** 열어서 airflowr파일이 있는 경로 찾고  **VS code**로 들어가기 

![](images/0728 airflow/Untitled%202.png)

![](images/0728 airflow/Untitled%203.png)

[https://github.com/PacktPublishing/Data-Engineering-with-Python](https://github.com/PacktPublishing/Data-Engineering-with-Python)

너무 긴 코드는 참고하기  

    5. 

  **1) read_df.py 파일 만들고 실행** 

```python
import csv

def main():

    with open('data.csv') as f:
        myreader = csv.DictReader(f)
        headers = next(myreader)
        for row in myreader:
            print(row['name'])

if __name__ == "__main__":
    main()
```

![](images/0728 airflow/Untitled%204.png)

 

 **2) write_df.py 파일 만들고  실행**

```python
from faker import Faker
import csv 

def main():
    output = open('data.csv', 'w')
    fake = Faker()
    header = ['name', 'age', 'street', 'city', 'state', 'zip', 'lng', 'lat']
    mywriter = csv.writer(output)
    mywriter.writerow(header)

    for r in range(1000):
        mywriter.writerow([fake.name(),fake.random_int(min=18, max=80, step=1), 
        fake.street_address(), fake.city(),fake.state(),fake.zipcode(),fake.longitude(),
        fake.latitude()])
    output.close()
    
if __name__ == "__main__":
    main()
```

![](images/0728 airflow/Untitled%205.png)

왼쪽 탐색기 쪽에 **data.csv** 파일이 출력되었다

[https://github.com/PacktPublishing/Data-Engineering-with-Python](https://github.com/PacktPublishing/Data-Engineering-with-Python)

너무 긴 코드는 참고하기  

   **3) write_json.py 파일 만들고**  **실행**

```python
# -*- coding: utf-8 -*-
from faker import Faker
import json

def main():
    output = open('data.json','w')
    fake = Faker()
    alldata = {}
    alldata['records']=[]

    for x in range(1000):
        data={"name":fake.name(),"age":fake.random_int(min=18, max=80, step=1),"street":fake.street_address(),"city":fake.city(),"state":fake.state(),"zip":fake.zipcode(),"lng":float(fake.longitude()),"lat":float(fake.latitude())}
        alldata['records'].append(data)

    json.dump(alldata,output)

if __name__ == "__main__":
    main()
```

![](images/0728 airflow/Untitled%206.png)

왼쪽 탐색기 쪽에 **data.json** 파일이 출력되었다 

    **4) read_json.py 파일 만들고  실행** 

```python
# -*- coding: utf-8 -*-

import json 
import pandas as pd
import pandas.io.json as pd_JSON

def read_json():
    with open('data.json', 'r') as f:
        data = json.load(f)
        
    print(type(data))
    print(data['records'][0]['name'])

def read_pandas():
    df = pd.read_json('data.json')
    print("기본 방법은 조금 복잡해요! :\n", df.head())

    f = open('data.json', 'r')
    data = pd_JSON.loads(f.read())
    # print(data)
    df = pd.json_normalize(data, record_path='records')
    print("다른 방법도 복잡해요 :\n", df.head())

if __name__ == "__main__":
    # read_json()
    read_pandas()
```

![](images/0728 airflow/Untitled%207.png)

p51

본격적으로 아파치 에어플로 데이터 파이프라인 구축 해보자 

 

    6. 코딩 

```python
import datetime as dt
from datetime import timedelta

from airflow import DAG
from airflow.operators.bash import BashOperator
from airflow.operators.python import PythonOperator

import pandas as pd

def csvToJson():
    df=pd.read_csv('data.csv')
    for i,r in df.iterrows():
        print(r['name'])
    df.to_json('fromAirflow.json',orient='records')

	

default_args = {
    'owner': 'evan',
    'start_date': dt.datetime(2022, 7, 27),
    'retries': 1,
    'retry_delay': dt.timedelta(minutes=1),
}

with DAG('MyCSVDAG',
         default_args=default_args,
         schedule_interval=timedelta(minutes=1),      # '0 * * * *',
         ) as dag:

    print_starting = BashOperator(task_id='starting',
                               bash_command='echo "I am reading the CSV now....."')
    
    csvJson = PythonOperator(task_id='convertCSVtoJson',
                                 python_callable=csvToJson)

print_starting >> csvJson
```

   7.  **airflow.cgf** 에서 52번째 load_examples = True 에서 True 를 False로 변경

![](images/0728 airflow/Untitled%208.png)

   8. 

그 다음 하단 순서대로 입력 후 실행  

>**airflow db reset**

>**airflow db dbinit** 

>**airflow webserver  -p 8081**

>**airflow scheduler**  실행하면  ****

![](images/0728 airflow/Untitled%209.png)

에어플로 GUI를 열면 방금 만든 **MyCSVDAG**가 생성되어 있다

![](images/0728 airflow/Untitled%2010.png)

![](images/0728 airflow/Untitled%2011.png)

코드도 보인다 

![](images/0728 airflow/Untitled%2012.png)

참고자료 :

**[Airflow 데이터 파이프라인 구축 예제](https://dschloe.github.io/python/data_engineering/ch03_reading_writing_file/airflow_csv2json_sample/)**

[https://dschloe.github.io/python/data_engineering/ch03_reading_writing_file/airflow_csv2json_sample/](https://dschloe.github.io/python/data_engineering/ch03_reading_writing_file/airflow_csv2json_sample/)
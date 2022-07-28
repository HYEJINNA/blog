---
title: "패키지 설치"
date: '2022-07-27'
---


    1. 먼저 VS code에서 가상환경에 접속하고

>source venv/bin/activate

# **아파치 에어플로 설치하기**

p25

 

     2. 아파치 에어플로를 설치하는 명령 입력후 엔터

>pip3 install ‘apache-airflow[postgres,slack,celery]’

시간이 조금 소요됨

![](images/0727 pkg set/Untitled.png)

       3. 

>airflow db init 명령으로 데이터 베이스를 초기화한다

![](images/0727 pkg set/Untitled%201.png)

    4. 1

>airflow webserver 

만 입력하면 기본포트 8080으로 실행된다

![](images/0727 pkg set/Untitled%202.png)

참고)  >airflow webserver -p 8081 로 진입할수도 있음

커서가 안보일때

cltr+c 하면 입력할 수 있도록 커서 나옴

  4. 2 

>`airflow users create --username airflow --password airflow --firstname evan --lastname airflow --role Admin --email your_email@some.com` 입력 후 엔터

>airflow webserver -p 8081 로 다시 실행하고

웹 주소창에  [http://localhost:8081/](http://localhost:8081/)에 접속하면 에어플로의 GUI를 볼 수 있다

![](images/0727 pkg set/Untitled%203.png)

아이디airflow , 비번 airflow

![](images/0727 pkg set/Untitled%204.png)
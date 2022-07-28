---
title: "WSL(ubuntu)셋팅"
date: '2022-07-27'
---


**실무예제로 배우는 데이터 공학교재**

카프카 - 개발자

에어플로 - 머신러닝 학습자

다음주는 웹사이트 만들고 배포하는 방법을 배울 예정

1. PC정보 확인

![](images/0727WSL_setting/Untitled.png)

![](images/0727WSL_setting/Untitled%201.png)

버전 21H2으로 확인 

너무 낮으면 안됨

2. Power Shell  관리자 권한으로 실행하고 

![](images/0727WSL_setting/Untitled%202.png)

`dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

복사 붙여넣기 

`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

복사 붙여넣기 

![](images/0727WSL_setting/Untitled%203.png)

`[https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)` 다운로드

![](images/0727WSL_setting/Untitled%204.png)

ok > finish

3. **Microsoft Store** 로 이동하여  **Ubuntu 20.04.4 LTS** 다운로드

![](images/0727WSL_setting/Untitled%205.png)

![](images/0727WSL_setting/Untitled%206.png)

Ubuntu 20.04.4 LTS 는 작업이 설정이 꼬여서 리셋해야 할때 도움이 많이된다. 

윈도우에서는 오래걸리는데, WSL에서 하면 빠르다. 

계속 날리고 새로 세팅하면서 배우는 것이다. 

![](images/0727WSL_setting/Untitled%207.png)

아이디, 비번 누르는 화면이 확인안됨

4. 따라서 먼저 가상환경 설정해야 한다

다시 powershell 관리자 권한으로 이동

![](images/0727WSL_setting/Untitled%208.png)

`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All`

![](images/0727WSL_setting/Untitled%209.png)

확인하면 여전히 에러있음

5. **윈도우즈 기능 켜기/끄기** 접속하여, **WINDOWS** **하이퍼바이저 플랫폼** 클릭 후 확인

![](images/0727WSL_setting/Untitled%2010.png)

![](images/0727WSL_setting/Untitled%2011.png)

누르고 재부팅

6. Windows PowerShell 로 다시 접속 / 관리자권한실행

![](images/0727WSL_setting/Untitled%2012.png)

>`wsl --set-default-version 2` 

`으로 버전` 세팅

![](images/0727WSL_setting/Untitled%2013.png)

7. **Ubuntu** 다시 접속

![](images/0727WSL_setting/Untitled%2014.png)

![](images/0727WSL_setting/Untitled%2015.png)

![](images/0727WSL_setting/Untitled%2016.png)

임의로 아이디 human , 비번 1234 (누를때 안보임)

현재 윈도우  LTS 버전에 접속한 상태임

![](images/0727WSL_setting/Untitled%2017.png)

하지만 **버전 2**로 확인되어야 한다

`wsl --set-default-version 2` 입력하여 버전2로 다시 세팅시도 

그래도 안되면 

![](images/0727WSL_setting/Untitled%2018.png)

다시 설치 

그래도 버전1인 상태..

8. 위 작업을 모두 시도 했는데도, 버전2로 확인이  안되면 

**Ubuntu 20.04.4 LTS 제거하고 다시 다운로드**

 그후 windows powershell에서 버전확인(wsl -l -v 입력)하면 버전2로 바뀜

![](images/0727WSL_setting/Untitled%2019.png)

준비완료 

# **VS code와 WSL 연동작업**

9. 시스템 환경 변수 편집으로 접속

![](images/0727WSL_setting/Untitled%2020.png)

![](images/0727WSL_setting/Untitled%2021.png)

**환경변수** 클릭

![](images/0727WSL_setting/Untitled%2022.png)

**path** > **편집**

![](images/0727WSL_setting/Untitled%2023.png)

**Microsoft VS code**가 있는지 확인

있으면 연동작업가능

** 메모장

앞으로 환경변수편집을 많이 사용하게 될 것임

현재 빅데이터 플랫폼, 웹사이트 구축 구축작업을 하고 있는 것임

— Configuration // 각 설치 프로그램들끼리 환경 변수로 유기적으로 연결시킴

— 레고 블록

10. **VS code** 들어가서 **Remote - WSL** 설치하기

![](images/0727WSL_setting/Untitled%2024.png)

11. **VS code** 창 닫고 , 다시 열면 터미널에 **WSL** 확인됨

![](images/0727WSL_setting/Untitled%2025.png)

[220727 가상환경설치](https://www.notion.so/220727-656bffb2247148cb8bf781924c421d5f)
 cloudsearch Manual
======================




#  What is the CloudSearch?

## 개요
- 원하는 시점에  ELK Stack( Elastic Search / Logstash(or Beats) / Kibana )을 배포하여 수집 – 저장 – 시각화를 위한 인프라 및 SW를 동적으로 제공한다. Docker 기반의 Container 서비스를 제공하며, 사용자가 불필요한 H/W Spec에 대해 고민할 필요 없이Pre-Defined된 Stack으로 쉽고 빠르게 배포되어 사용자에게 제공됨  다양한 형태의 로그를 최소의 비용으로 안정적으로 검색/분석/모니터링할 수 있는 서비스를 지향한다.

## 차별점
![차별점][1.2]

# 메인화면
## About Page

![About Page][2-1-1]
![About Page][2-1-2]

## 클러스터

###  화면 구성
- 화면은 다음과 가은 구성으로 이루어져 있다.

![][2-2]

## 메뉴 구성

### 클러스터 생성 및 Control
 - 새로운 클러스터를 생성하거나 선택된 클러스터를 시작/종료/삭제할 수 있다.
### 클러스터 검색
 - 검색하고 싶은 클러스터명을 입력하면 원하는 검색값으로 색인되어 Display된다. 원하는 생성시간을 기간으로 입력하여 검색하는 것도 가능하다.
### 클러스터 ID 확인
 - 생성된 클러스터는 내부적으로 생성된 Cluster ID로 관리된다. 사용자가 이를 기억하거나 사용할 경우는 없지만 추후 장애나 서비스 지원을 위해서 활용되므로 인지하는 것을 권장한다.
### 클러스터 상태 확인
 -  Elastic Search Cluster의 health를 보여주는 상태값이다. 상태는 크게 Green / Yello / Red로 구분되어 표기 되며, 해당 값은 아래와 같이 구분된다.

###	단위 클러스터 제어
- 클러스터 단위별로 시작/중지/삭제를 실행할 수 있다.

## 이용안내 (준비 중)
- 과금 체계 및 사용법에 대한 페이지

## Admin
- Admin 권한이 있는 사용자가 조회 가능하며, 권한없는 사용자는 조회할 수 없다. 서비스되고 있는 전체 클러스터를 조회하고 Control할 수 있다.

## 로그인
- 사용 가능한 서비스 계정으로 서비스 로그인을 제공하는 페이지.

![로그인][2-6]

# 클러스터 생성

## 클러스터 이름 설정
- 메인메뉴의 “클러스터”를 클릭한다.
- “클러스터 생성하기” 버튼을 클릭한다

![클러스터 생성][3-1-1]

## 클러스터 상세 설정(설명 및 상세 스펙)
-	생성할 클러스터의 명칭 및 설명을 입력하고,
-	클러스터를 구성하는 노드 및 자원(CPU, Memory)를 설정한다.

![클러스터 생성][3-1-2]

|  <center>입력항목</center> |  <center>설명</center> |  <center>예시</center> |
|:--------|:--------|:--------|
|클러스터명  | 이름	생성할 클러스터 명칭을 입력한다. <br />영문, 숫자, ‘-‘ 포함하여 최대 20byte | CS-Cluster-01 |
|설명 | 생성할 클러스터에 대한 설명을 입력한다.| 테스트용 ES Cluster |
|하드웨어 구성|  생성할 클러스터를 구성할 서버 대수 지정 <br /> 할당할 시스템 자원(CPU, Memory) 지정 <br /> Disk는 Node당 300G 할당   | Light : 1Node, 4CPU, 4G Mem <br /> Middle : 2Node, 4CPU, 4G Mem <br /> Advanced : 3Node, 4CPU, 4G Mem|


-	"서비스 생성"버튼을 클릭하면, 아래와 같이 클러스터가 생성 중인 상태로 목록에 표시됨.

![클러스터 생성][3-2-1]
- 설치 단계에 따른 상태 노출 값은 아래와 같다.

|  <center>설치 단계</center> | <center>  설명 </center>   |
|:--------|:--------|
|생성 요청중| 클러스터 생성 요청을 전달|
|노드 구성중|클러스터 노드 구성중|
|서비스 정보 할당 중 |생성된 노드의 서비스 정보를 할당|
|내부 인증중|구성된 노드간의 연결|
|랜처 정보 획득중|랜처 Stack에 등록|
|생성완료|생성 완료|


## 클러스터 상세 페이지
클러스터 목록에서 원하는 클러스터를 클릭하면, 해당 클러스터에 대한 상세정보를 조회할 수 있는 페이지로 전환

### 클러스터 요약정보
-	Elasticsearch 및 Kiana 접근을 위한 Endpoint 주소 정보
-	생성된 클러스터의 상태 정보(생성시간, 종료시간, 사용시간)
-	할당된 하드웨어 정보

![클러스터 상세][4-1-1]

- ES Endpoint	: Elasticsearch cluster에 접속 가능한 정보. 이 endpoint를 이용하여, ES 데이터를 조회/입력한다. 	
- Kibana Endpoint	: 시각화를 위한 웹페이지 접속 url, ES에 저장된 데이터를 쉽게 시각화 가능
- 생성 시간 : ES 클러스터를 처음 생성한 시간
- 종료 시간	: ES 클러스터를 종료한 시간
- 사용 시간	: 생성 시간 – 종료 시간 (클러스터를 사용한 시간)
- 하드웨어 구성 :	현재 ES 클러스터가 사용하고 있는 자원 (CPU, Memory, 저장장치 등)

## 클러스터 관리 정보

###	클러스터 관리 화면 설명
-	Elasticsearch 클러스터 운영에 필요한 설정을 변경하거나,
-	각 노드들의 로그 확인 및 콘솔 연결을 통해서 직접 내부상태를 확인 가능

![클러스터 관리정보][4-2-1]


|  <center>상세 정보</center> | <center>  설명 </center>   | <center> 예시 </center>|
|:--------|:--------|:--------|
|Elasticsearch 시작/중지 아이콘 | 클러스터를 시작 또는 중지 가능||
|Description 변경|클러스트에 대한 설명을 수정||
|환경 설정|Elasticsearch 클러스터에 대한 설정 변경<br / > Json 포맷으로 변경할 설정 값을 지정하면 <br />ES cluster에 동적으로 변경된 설정을 적용한다 |![환경설정 예시][4-2-1-conf]|
|Config 참고 link|환경설정에 필요한 상세 매뉴얼 링크||
|Elastic 스케일 설정 <br /> (Instance Number)|ES 클러스터의 노드를 추가 <br />저장할 로그가 증가하는 경우 노드를 추가하여 <br /> 클러스터 성능 확보||
|Kibana 시작/중지 아이콘|Kibana 웹서버를 시작 또는 중지 가능||
|로그 체크|동자 중인 노드의 실시간 로그를 확인 가능|![로그체크 예시][4-2-1-logCheck]|
|Consol 연결|각 노드에 접속하여, 원하는 Command를 직접실행 <br />노드의 상태 점검 가능 | . |

## 클러스터 설명 변경
-	클러스터에 대한 설명을 수정하고, “적용” 버튼을 클릭

![클러스터 설명 변경](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-2.png?raw=true)

## 환경 설정
-	ES 클러스터의 설정을 동적으로 변경한다.
![환경설정](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-3.png?raw=true)

|  <center> 설정 요소 </center> | <center>  설명 </center>   |
|:--------|:--------|
|transient|클러스터가 동작 중인 상태에서만, 적용되는 설정값 <br /> 클러스터가 재시작하면, 해당 설정은 적용되지 않음.|
|persistent| 클러스터가 재시작해도 윶되는 설정 값 |

-	클러스터 설정값이 적용되는 우선순위는
  - Transient cluster setting
  -	Persistent cluster setting
	- Elasticsearch.yml 설정 파일 setting

-	“Config 참고 link” 사용 방법
  -	“설정항목 : 값”과 같은 방식으로 json 포맷을 유지하여 작성
  - “설정항목”에 대한 부분은 Elasticsearch에서 제공하는 다양한 값을 참고
  - ![config 참고 link 사용](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-3-config.png?raw=true)

### Elastic 스케일 설정
-	ES 클러스터에 노드를 추가/삭제 하여, 필요한 만큼의 저장 용량을 유지한다.
-	노드 추가 : (+) 버튼 클릭
-	노드 삭제 : (-) 버튼 클릭

![Elastic 스케일 설정](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-4.png?raw=true)

###  로그 체크 상세 설명
-	로그를 확인할 노드를 선택하고,
-	“상세보기” 버튼을 클릭하면 로그를 볼 수 있는 창이 표시

![로그체크 상세 설명](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-5.png?raw=true)
- "상세보기"룰 클릭하면, 아래와 같이 로그를 화면에 보여준다.

![로그 출력](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-5-2.png?raw=true)


|화면 아이콘|설명|
|:--|:--|
|![](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-5-icon-1.png?raw=true)|로그를 조회할 노드를 실시간으로 변경가능|
|![](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-5-icon-2.png?raw=true)|현재 화면에 출력된 로그를 화면에서 제거|
|![](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-5-icon-3.png?raw=true)|현재 로그를 갱신 <br /> 해당 노드에 접속하여, 새로운 로그를 조회|

### 콘솔 연결 상세 설명
-	각 노드에 접속하여, 원하는 명령어를 직접 실행한다.

![콘설 연결](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-6-1.png?raw=true)

-	콘솔로 접속할 노드를 선택한 후,
-	“연결” 버튼을 클릭하면,
-	웹 방식으로 접속할 수 있는 콘솔창이 생성된다.

![콘솔 연결 화면](https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-6-2.png?raw=true)


## 모니터링 Tab
### 디스플레이 화면

해당 클러스터의 간단한 정보를 확인 할 수 있다.
![4-3-1][4-3-1]

### Nodes
- 검색기능 <br>
  - 클러스터의 모든 노드 중, 원하는 노드 이름(Name)을 기준으로 검색 할 수 있다.
![4-3-2-1][4-3-2-1]

-  클릭 시, 상세정보 표기<br>
  - 선택된 노드에 대한 상세 정보를 확인 할 수 있다. <br>
![4-3-2-2][4-3-2-2]

<br>

### Indices

- ** 검색기능 <br> **
  - 클러스터의 모든 노드 중, 원하는 인덱스 이름(Name)을 기준으로 검색할 수 있다.<br>
![4-3-3-1][4-3-3-1]

- **  인덱스 클릭 시, 상세정보 표기**<br>
  - 인덱스 리스트에서 하나를 선택하면, 인덱스에 대한 간단한 정보확인이 가능하다.<br>

- **  Information** <br>
  - 선택된 노드에 대한 상세 정보를 확인 할 수 있다.
![4-3-3-2][4-3-3-2]


- ** Shards** <br>
  - 선택된 노드의 Shard관련 정보를 확인 할 수 있다.<br>
![4-3-3-3][4-3-3-3]

<br><br><br>

## Built-In Service Tab
- 탭 안쪽 좌측 상단의 "추가"버튼을 클릭하여 Built-In Service 설치를 진행한다.<br>
![4-4][4-4]

<br>
### Built-In 추가
- 추가 버튼을 누르면 아래와 같은 Pop-Up창이 뜬다.<br>
![4-4-1][4-4-1]

<br>
### 서비스 선택
- Pop-Up 창의 상단에 있는 Drop-Down 버튼을 클릭하면 현재 설치 가능한 Service목록이 나온다.<br>
![4-4-2][4-4-2]

- ** Target host 정보 입력**<br>
  - Service가 설치될 호스트 주소/포트와 접속하기 위한 아이디/비밀번호를 입력한다.<br>
  ![4-4-2-1][4-4-2-1]

  - 정보가 부족하면 아래와 같은 오류가 발생한다.<br>
  ![4-4-2-2][4-4-2-2]

  - 입력정보가 정확하다면 아래와 같이 “접속 가능한 호스트 입니다.”라는 메시지가 나온다.<br>
  ![4-4-2-3][4-4-2-3]

<br>
### Collector 설정 값 입력
- ** 자동완성**<br>
  - Built-In Service를 선택하면 서비스 설정 값 (Collector 환경 설정)의 default 값이 자동 입력된다.<br>
  ![4-4-3-1][4-4-3-1]

- ** 사용자 편집** <br>
  - 각 상황에 맞게 설정내 변수 변경이 가능하다.<br>
  ![4-4-3-2][4-4-3-2]

  - 형식에 맞지 않는 값으로 변경되었거나 입력 되었을 때, 아래와 같이 경고 메시지가 나타난다.<br>
  ![4-4-3-3][4-4-3-3]

<br>
###   배포
- 적절한 입력 값 작성 후, 검증 버튼을 누르면 아래와 같이 ‘접속 가능한 호스트입니다’란 메시지가 나타나며, 검증 완료 후 추가 버튼을 누르면 해당 호스트에 설치가 진행된다.<br>
![4-4-4-1][4-4-4-1]

<br>

### Built-In Service 리스트 표기
- 설치가 끝나면, 아래와 같이 “Built-in Service is registered.”라는 메시지와 함께 설치완료 되며, 테이블에 리스트 설치된 서비스가 나타나게 된다.<br>
![4-4-5-1][4-4-5-1]



<br><br><br>
# 5. Admin Page
- 관리자 모드로 로그인하여 모든 유저에 의해 생성된 클러스터의 리스트 보기 및 관리를 할 수 있다.<br>
![5][5]




[1.2]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/1-2.png
[2-1-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-1-1.png
[2-1-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-1-2.png
[2-2]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-2.png
[2-6]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-6.png

[3-1-1]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/3-1-1.png?raw=true
[3-1-2]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/3-1-2.png?raw=true
[3-2-1]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/3-2-1.png?raw=true
[4-1-1]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-1-new.png?raw=true
[4-2-1]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-1.png?raw=true
[4-2-1-conf]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-1-conf.png?raw=true
[4-2-1-logCheck]: https://github.com/hellotherecsy/cloudsearch_temp/blob/master/images/4-2-1-logCheck.png?raw=true


[4-3-1]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-1.png
[4-3-2-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-2-1.png
[4-3-2-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-2-2.png
[4-3-3-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-3-1.png
[4-3-3-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-3-2.png
[4-3-3-3]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-3-3-3.png
[4-4]:	    https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4.png
[4-4-1]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-1.png
[4-4-2]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-2.png
[4-4-2-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-2-1.png
[4-4-2-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-2-2.png
[4-4-2-3]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-2-3.png
[4-4-3-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-3-1.png
[4-4-3-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-3-2.png
[4-4-3-3]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-3-3.png
[4-4-4-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-4-1.png
[4-4-5-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/4-4-5-1.png
[5]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/5.png

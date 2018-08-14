 cloudsearch Manual
======================



# 1.	What is the CloudSearch?

## 1.1. 개요
: 원하는 시점에  ELK Stack( Elastic Search / Logstash(or Beats) / Kibana )을 배포하여 수집 – 저장 – 시각화를 위한 인프라 및 SW를 동적으로 제공한다. Docker 기반의 Container 서비스를 제공하며, 사용자가 불필요한 H/W Spec에 대해 고민할 필요 없이Pre-Defined된 Stack으로 쉽고 빠르게 배포되어 사용자에게 제공됨  다양한 형태의 로그를 최소의 비용으로 안정적으로 검색/분석/모니터링할 수 있는 서비스를 지향한다.

## 1.2/ 차별점
![][1.2]

# 2. 메인화면
## 2.1. About Page

![][2-1-1]
![][2-1-2]

## 2.2. 클러스터
### - 화면 구성
: 화면은 다음과 가은 구성으로 이루어져 있다.

![][2-2]

## 2.3. 메뉴 구성

### -	클러스터 생성 및 Control
 : 새로운 클러스터를 생성하거나 선택된 클러스터를 시작/종료/삭제할 수 있다.
### -	클러스터 검색
 : 검색하고 싶은 클러스터명을 입력하면 원하는 검색값으로 색인되어 Display된다. 원하는 생성시간을 기간으로 입력하여 검색하는 것도 가능하다.
### -	클러스터 ID 확인
 : 생성된 클러스터는 내부적으로 생성된 Cluster ID로 관리된다. 사용자가 이를 기억하거나 사용할 경우는 없지만 추후 장애나 서비스 지원을 위해서 활용되므로 인지하는 것을 권장한다.
### -	클러스터 상태 확인
 : Elastic Search Cluster의 health를 보여주는 상태값이다. 상태는 크게 Green / Yello / Red로 구분되어 표기 되며, 해당 값은 아래와 같이 구분된다.

### -	단위 클러스터 제어 
 : 클러스터 단위별로 시작/중지/삭제를 실행할 수 있다. 

## 2.4. 이용안내 (준비 중)
: 과금 체계 및 사용법에 대한 페이지 

## 2.5. Admin 
: Admin 권한이 있는 사용자가 조회 가능하며, 권한없는 사용자는 조회할 수 없다. 서비스되고 있는 전체 클러스터를 조회하고 Control할 수 있다.

## 2.6. 로그인
: 사용 가능한 서비스 계정으로 서비스 로그인을 제공하는 페이지.
![테스트입니다.][2-6]

[1.2]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/1-2.png
[2-1-1]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-1-1.png
[2-1-2]: https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-1-2.png
[2-2]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-2.png
[2-6]:   https://raw.githubusercontent.com/hellotherecsy/cloudsearch_temp/master/images/2-6.png


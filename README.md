![Dashboard](https://github.com/ivsteam/ivsteam.github.io/blob/master/img/grafana_6696.png)

## About

[인베슘](http://invesume.com) 에서는 하모니카 리눅스를 서버로 사용하는 경우 시스템 모니터링을 쉽게 할 수 있도록 제공하고 있습니다.
기본으로 제공되는 대시보드에 모니터링을 원하는 항목을 사용자 정의 패널로 자유롭게 추가할 수 있습니다.

아래의 환경에서 테스트 되었으며, 기타 SystemV Linux 계열에서도 docker, docker-compose 가 있으면 동일하게 사용가능합니다.

- HamoniKR 2.1
- HamoniKR Community Edition Moordev MATE 64bit 1.0
- Ubuntu 16.04
- Ubuntu 18.04
- Linux Mint 18
- Linux Mint 19 beta

### Requirement
쉬운 모니터링을 위하여 docker 기반의 서비스를 제공하므로, docker-compose 를 사용할 수 있는 준비가 먼저 필요합니다.
이미 설치되어 있다면 서비스 실행 으로 넘어가세요.
아래는 우분투 계열에서 docker, docker-compose 의 설치방법입니다.
```
$ sudo apt install docker.io
$ sudo usermod -aG docker ${USER}
$ sudo apt install docker-compose
```
#### 기타 OS 에서 docker, docker-compose 설치는 아래 링크를 참고하세요.

- Docker 설치문서 : https://docs.docker.com/install/
- docker-compose 설치문서 : https://docs.docker.com/compose/install/


## 서비스 실행

이 저장소를 클론한 후에 아래의 명령을 실행하면 서비스가 구동됩니다.

```
$ git clone https://github.com/ivsteam/HamoniKR-Mon.git
$ cd HamoniKR-Mon
$ sudo docker-compose up -d
```

서비스 구동 후 아래의 주소에서 확인하세요 :

- <http://localhost:3000>  grafana web page (login with admin/admin)


## 대시보드 설정

1) grafana 로그인 후 아래의 정보대로 Datasource 를 생성합니다. 
- url : http://influxdb:8086
- influxdb dbname : collectd

![Add Data Source](https://github.com/ivsteam/ivsteam.github.io/blob/master/img/add_data_source.png)


2) 왼쪽화면의 + 버튼을 누르고 Import 메뉴를 클릭하여 다음과 같이 **6696** 을 입력하고 Load 버튼을 클릭합니다. 

![Import](https://github.com/ivsteam/ivsteam.github.io/blob/master/img/dashboard_import.png)

이전 단계에서 생성한 Datasource 이름 influxdb 를 다음과 같이 선택해줍니다.

![Select DS](https://github.com/ivsteam/ivsteam.github.io/blob/master/img/select_ds.png)


### Tip. 네트워크 디바이스가 eth0 이 아닌경우
ifconfig 명령어로 확인하여 사용 중인 네트워크 디바이스명을 확인하고
collected.conf 파일에서 <Plugin interface> 섹션의 interface 값을 수정하고 다시 시작하세요.



## 버그 제출 및 기타 이슈 제안
이 프로젝트와 관련하여 이슈는 상단의 이슈 탭을 이용해 주세요.

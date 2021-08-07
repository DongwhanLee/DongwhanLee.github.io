---
title:  "리눅스 기반의 명령어 정리"
excerpt: "UBUNTU와 CENTOS에서 자주 사용되는 Command를 정리해보자."

categories:
  - Linux
tags:
  - [linux, static IP, ubuntu, centos]

toc: true
toc_sticky: true
 
date: 2021-08-04
last_modified_at: 2021-08-04
---

---

작성자 환경:
- Ubuntu 18.04.5
- CentOS 7.6.1810

### <span style="color:#084B8A"> 버전 확인</span>

- Ubuntu
```
$ lsb_release -a # 시스템 전체 정보를 원할 때
$ lsb_release -d # 우분투 버전만 원할 때
```
```
$ cat /etc/issue # LTS는 Long Term Support 의미
```
```
$ cat /etc/os-release # 우분투 16.04 이상 버전에서 작동
```
```
$ hostnamectl
```

- CentOS
```
$ rpm --query centos-release
```
```
$ cat /etc/centos-release
```
```
$ cat /etc/system-release
```

### <span style="color:#084B8A"> 디렉토리 구조 및 용량</span>

- df 명령어 (Disk Free, 디스트 여유 공간 확인)
``` $ df ```
* [-a], [--all] : 모든 디렉토리 출력
* [-h], [--human-readable] : KB, MB, GB와 같이 단위 형태의 용량 출력
* [-t], [--type=TYPE] : 파일 시스템의 포맷 출력
* [-x], [--exclude-type=TYPE] : 출력 생략할 파일 시스템 포맷 지정

- du 명령어 (Disk Usage, 디스트 사용 공간 확인)
``` $ du ```
* [-a], [--all] : 디렉토리를 포함한 모든 파일 출력
* [-h], [--human-readable] : KB, MB, GB와 같이 단위 형태의 디스크 사용 공간 출력
* [-s], [--summarize] : 하위 디렉토리를 제외한 자기 자신의 총 용량 출력
* [-hs *] : 현재 디렉토리의 폴더 및 파일 용량 확인 (하위 디렉토리 X)
* [-d], [--max-depth=N] : 출력할 하위 디렉토리 단계 지정

### <span style="color:#084B8A"> 디렉토리 구조 및 용량</span>

![ifconfig result](/assets/images/2021-08-04-static-ip-setting/ifconfig.png)
위의 그림과 같이 두 개의 이더넷이 인식되는 것을 알 수 있다. 
이 과정에서 내가 사용하고자 하는 랜포트와 이더넷의 이름을 매칭해 줄 필요가 있다.

- 물리 네트워크 포트 확인
```
$ ethtool -p "이더넷 이름"
ex) $ ethtool -p ens12f0 
```
위의 커맨드를 실행했을 때 불이 깜빡이는 물리 네트워크 포트가, 해당 이더넷의 물리 포트이다. 

### <span style="color:#084B8A">디스크 및 파티션</span>

```
# 현재 디스크 및 파티션 확인

$ fdisk -l
```

### <span style="color:#084B8A">유저 생성 및 삭제</span>
### <span style="color:#084B8A">유저 권한 관리</span>
### <span style="color:#084B8A">계정 전환</span>

TBD
---
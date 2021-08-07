---
title:  "리눅스 기반의 명령어 정리"
excerpt: "UBUNTU와 CENTOS에서 자주 사용되는 Command를 정리해보자."

categories:
  - Linux
tags:
  - [linux, static IP, ubuntu, centos]

toc: true
toc_sticky: true
 
date: 2021-08-07
last_modified_at: 2021-08-07
---

---

### <span style="color:#084B8A"> 작성자 환경</span>
- Ubuntu 18.04.5
- CentOS 7.6.1810

### <span style="color:#084B8A"> 버전 확인</span>

- **Ubuntu**
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

- **CentOS**
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

```
# df 명령어 (Disk Free, 디스트 여유 공간 확인)
$ df
```
* [-a], [--all] : 모든 디렉토리 출력
* [-h], [--human-readable] : KB, MB, GB와 같이 단위 형태의 용량 출력
* [-t], [--type=TYPE] : 파일 시스템의 포맷 출력
* [-x], [--exclude-type=TYPE] : 출력 생략할 파일 시스템 포맷 지정

```
# du 명령어 (Disk Usage, 디스트 사용 공간 확인)
$ du
```
* [-a], [--all] : 디렉토리를 포함한 모든 파일 출력
* [-h], [--human-readable] : KB, MB, GB와 같이 단위 형태의 디스크 사용 공간 출력
* [-s], [--summarize] : 하위 디렉토리를 제외한 자기 자신의 총 용량 출력
* [-hs *] : 현재 디렉토리의 폴더 및 파일 용량 확인 (하위 디렉토리 X)
* [-d], [--max-depth=N] : 출력할 하위 디렉토리 단계 지정

### <span style="color:#084B8A">디스크 및 파티션</span>

```
# 현재 디스크 및 파티션 확인
$ fdisk -l
```
참고: https://servermon.tistory.com/181

### <span style="color:#084B8A">압축 및 해제</span>

- **tar Utility**

```
$ tar -xvzf "tar.gz 파일명"
ex) $ tar -xvzf drive_360.tar.gz

$ tar -xvzf "tar.gz 파일명" "압축해제하고자 하는 디렉토리"
ex) $ tar -xvzf drive_360.tar.gz /mnt/disk0/decompressed/
```

* [-x] : tar에게 압축 파일로부터 파일 추출 지시
* [-v] : 압축 과정에서의 파일 목록 출력
* [-z] : tar에게 파일 압축 지시 (-z 없다면, 압축 파일로 가득한 폴더 생성)
* [-f] : tar에게 작업하고자 하는 파일명 지정

- **zip, unzip**

```
# 압축하기 - zip
$ zip "원하는 압축파일명.zip" "압축할 파일 or 디렉토리" "압축할 파일 or 디렉토리" ...
ex) $ zip test.zip ./* # 현재 폴더의 모든 파일을 test.zip으로 압축
```

* [-r] : 디렉토리 압축
* [-j] : 디렉토리 이름 제외하고 압축
* [-u] : 변경되었거나 새로운 파일만 압축

```
# 압축 해제하기 - unzip
$ unzip "원하는 압축파일명.zip"
ex) $ unzip test.zip # 현재 폴더에 해당 압축파일 해제
```

* [-d] : 압축을 해제하고자 하는 경로 지정


### <span style="color:#084B8A">유저 생성 및 삭제</span>
### <span style="color:#084B8A">유저 권한 관리</span>
### <span style="color:#084B8A">계정 전환</span>

TBD
---
---
title:  "리눅스 기반의 고정 IP 설정하기"
excerpt: "UBUNTU와 CENTOS에서 고정IP 설정을 해보자."

categories:
  - Network
tags:
  - [network, static IP, ubuntu, centos]

toc: true
toc_sticky: true
 
date: 2021-08-04
last_modified_at: 2021-08-04
---

---

### <span style="color:#084B8A">UBUNTU 환경에서의 고정 IP 설정</span>

우분투 환경에서 고정 IP를 설정해보자. (Ubuntu 18.04.5 기준)

- 이더넷 이름 확인
```
$ ifconfig
```
![ifconfig result](/assets/images/2021-08-04-static-ip-setting/ifconfig.png)
위의 그림과 같이 두 개의 이더넷이 인식되는 것을 알 수 있다. 
이 과정에서 내가 사용하고자 하는 랜포트와 이더넷의 이름을 매칭해 줄 필요가 있다.

- 물리 네트워크 포트 확인
```
$ ethtool -p "이더넷 이름"
ex) $ ethtool -p ens12f0 
```
위의 커맨드를 실행했을 때 불이 깜빡이는 물리 네트워크 포트가, 해당 이더넷의 물리 포트이다. 

### <span style="color:#084B8A">본격 고정 IP 설정</span>

```
$ cd /etc/netplan/
$ ls
```
![netplan](/assets/images/2021-08-04-static-ip-setting/netplan.png)

위의 경로로 이동하여, XX-installer-config.yaml을 확인한다.

- Editor로 수정 (NANO Editor)

```$ nano 00-installer-config.yaml ```

![netplan](/assets/images/2021-08-04-static-ip-setting/config.yaml.png)
두개의 이더넷 "ens12f3"과 "ens12f0"에 대한 네트워크 설정이 작성되어 있다.
"ens12f3"은 외부 및 내부와의 통신 목적으로,
"ens12f0"는 다른 컴퓨터와의 자체 네트워크를 위하여 구축하였다.

**< ens12f3 >**
* [dhcp4], [dhcp6] : dhcp가 아닌, 수동으로 IP 설정을 하기 위해 "no"
* [addresses] : 사용하고자 하는 IP 주소
*(24는 172.26.199 3칸까지는 고정값임을 의미하며, "prefix"로 별도 선언해 줄 수 있음)*
* [gateway4] : 게이트웨이 값
* [nameservers-addresses] : DNS 값

**< ens12f0 >**

크로스 케이블 (서로 다른 두 PC 간의 연결)의 경우, 가급적 게이트웨이 값을 생략한다.

### <span style="color:#084B8A">변경 설정 적용</span>
```
$ systemctl restart network
$ ifconfig
```
네트워크를 재시작하여 변경사항을 적용하고, ifconfig를 통해 변경된 내용을 확인한다.
간혹, 에러로 네트워크 재시작이 되지 않을 경우, 시스템 재부팅 ```$ reboot``` 을 통해 변경사항 적용가능하다.
 
---
---
title:  "Anaconda 가상환경 (base) 자동활성화 설정/해제"
excerpt: "아나콘다 (base)를 설정/해제 해보자."

categories:
  - Anaconda
tags:
  - [anaconda, virtualenv, Ph.D., ME]

toc: true
toc_sticky: true
 
date: 2021-06-17
last_modified_at: 2021-06-15
---

---

### __`아나콘다 가상환경 (base) 설정 및 해제`__

우분투에서 아나콘다 설치 및 터미널 실행 시, 자동으로 아나콘다가 실행되며 (base)가 출력된다. 

![activated (base)](/assets/images/2021-06-10-anaconda-base/base_activated.png)

아래의 코드를 이용하여, 가상환경을 자동으로 설정 및 해제할 수 있다.


- (base) 자동활성화 해제
```
$ conda config --set auto_activate_base false
```
- (base) 자동활성화 설정
```
$ conda config --set auto_activate_base true
```
코드의 ```false```를 ```true```로 바꿔, (base) 자동활성화 설정이 가능하다.

---
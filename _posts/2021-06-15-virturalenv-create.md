---
title:  "Anaconda 가상환경 생성하기"
excerpt: "아나콘다 가상환경을 만들어보자."

categories:
  - Anaconda
tags:
  - [anaconda, virtualenv, Ph.D., ME]

toc: true
toc_sticky: true
 
date: 2021-06-15
last_modified_at: 2021-06-15
---

---

### __`아나콘다 가상환경 생성하기`__

우분투에서 아나콘다 가상환경을 생성하고 활성화해보자.  
아래의 코드는 아나콘다 가상환경 생성을 위한 코드이다.

```
$ conda create -n "가상환경 이름" python="희망하는 파이썬 버전" -y
ex) $ conda create -n skeleton python=3.7 -y 
```
- [-y / --yes] : Do not ask for confirmation. (확인요청 생략)


### __`생성한 가상환경 활성화하기`__

생성한 가상환경을 활성화하여, 원하는 패키지의 원하는 버전을 설치할 수 있다. 

- 윈도우 환경
```> conda activate "가상환경 이름" ```
- 리눅스 환경
```$ source activate "가상환경 이름" ```

사용환경에 따른 활성화 코드는 아래의 포스팅에서도 확인 가능하다.  
https://dongwhanlee.github.io/anaconda/source-activate/
---
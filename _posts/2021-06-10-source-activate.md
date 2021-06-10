---
title:  "가상환경 활성화가 되지 않을 때"
excerpt: "conda activate 안먹힐 때"

categories:
  - Anaconda
tags:
  - [anaconda, virtualenv, Ph.D., ME]

toc: true
toc_sticky: true
 
date: 2021-06-10
last_modified_at: 2021-06-10
---

---

### __`아나콘다 가상환경이 활성활 되지 않을 때`__

아래와 같이 우분투(리눅스)에서, 아나콘다의 가상환경이 활성화 되지 않는 경우가 종종 있다.
``` $ conda activate base```

![Activated (base)](/assets/images/2021-06-10-source-activate/error.png)

이러한 경우, 아래의 코드를 이용하여 가상환경을 활성화할 수 있다.

```$ source activate base ```

![Activated (base)](/assets/images/2021-06-10-source-activate/source_activate.png)

코드의 ```conda```를 ```source```로 바꿔, 가상환경이 활성화 된 것을 확인할 수 있다.

---
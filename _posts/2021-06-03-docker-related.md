---
title:  "Docker 사용하기"
excerpt: "Container 생성 및 Docker 사용을 알아보자."

categories:
  - Docker
tags:
  - [ubuntu, docker, Ph.D., ME]

toc: true
toc_sticky: true
 
date: 2021-06-03
last_modified_at: 2021-06-03
---

### <span style="color:#084B8A">사용할 도커 이미지 확인</span>
-----------------------

    $ docker images
![Docker images](/assets/images/2021-06-03-docker-related/docker_images.PNG)

### <span style="color:#610B0B">컨테이너 생성</span>
--------------

    $ docker run -idt --name "컨테이너 이름" -v "서버 디렉토리":"컨테이너 디렉토리" -p "서버 포트":"컨테이너 포트" --gpus "사용할 GPU 갯수" "사용할 이미지"
    ex) docker run -idt --name lane_detection -v /mnt/disk0:/mnt/disk0 -p 9230:9230 --gpus all 5ffed6c83695

* [run] : 컨테이너를 생성하고 시작하는 명령어(Create와 Start를 모두 실행)
* [-d] : 컨테이너를 백그라운드에서 실행하는 옵션
* [-i], [-t] : 컨테이너와 상호작용
* [--name] : 컨테이너명
* [-v] : 공유할 디렉토리 설정 (서버 폴더:컨테이너 폴더)
* [-p] : 공유할 포트 설정 (서버 포트:컨테이너 포트)
* [--gpus] : GPU 사용 개수 (GPU 8개 장착인 경우, 0~7 or 8(=all))
* 5ffed6c83695 : 컨테이너 제작에 사용될 이미지 ID

### <span style="color:#61210B">생성 컨테이너 확인</span>
    $ docker ps # 실행 중 컨테이너 목록 출력 
    $ docker ps -a # 종료된 컨테이너 포함 목록 출력



### __`생성 컨테이너 실행`__
    $ docker exec -it "생성 컨테이너명" bash

    ex) docker exec -it lane_detection bash

### __`Docker 환경에서 Jupyter Notebook 실행`__
    $ jupyter notebook --ip="허용할 ip" --port="사용할 컨테이너의 포트" --allow-root
    
    ex) jupyter notebook --ip=0.0.0.0 --port=9230 --allow-root  
* [--ip] : 모든 ip 허용 시, 0.0.0.0
* [--port] : 사용할 컨테이너의 포트

![token](/assets/images/2021-06-03-docker-related/jupyter_notebook_token.PNG)
* 이미지의 token 값 파악  
    https://"호스트 ip":"연결할 포트"/"token 값"  
    ex) https://172.26.199.15:9235/?token=74cc52ec2e60c86d24e85a24578e5d328af7ffbda9ba4ee4

### __`실행된 Jupyter Notebook 확인`__
![token](/assets/images/2021-06-03-docker-related/jupyter_notebook.PNG)
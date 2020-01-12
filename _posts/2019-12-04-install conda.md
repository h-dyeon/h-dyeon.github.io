---
layout: post
title:  "[Linux] Anaconda에 가상환경 구축하고 설치하기"
subtitle:   "Anaconda, Python, Tensorflow, Keras"
categories: Dev
tags: Linux
comments: true
date:  2019-12-04 22:00:00
---

듀얼부팅은 깔끔하게 포기하고 그냥 노트북에 윈도우를 밀어버리고 우분투18.04를 설치했다. (편안)

# Anaconda

Python 기반의 데이터 분석에 필요한 오픈소스를 모아놓은 개발 플랫폼. 파이썬이 버전별로 호환되는 라이브러리가 다른데, python 버전별로 관리를 쉽게(?) 도와주는 도구이다.



# Conda 설치하기

Anaconda 사이트에 들어가서 sh파일을 다운받는다. 나는 Anaconda 2019.10 for Linux Installer Python 3.7 version을 다운 받았다. 이후 아래 명령어를 입력한다.

~~~bash
$ cd ~/Downloads #폴더로 이동
$ bash Anaconda3-2019.10-Linux-x86_64.sh #스크립트 파일을 bash 쉘로 실행
~~~

이후로는 적당히 읽어보고 Yes라고 입력하면 된다. 그리고 <code>.bashrc</code>파일에 환경변수 설정을 해야하는데 <code>Do you wish the installer to initialize Anaconda3 by running conda init? [yes|no]</code> 에서 yes를 눌렀더니 <code>.bashrc</code>파일이 자동으로 변경이 됐다.

~~~bash
$ source ~/.bashrc #변경사항 적용
$ conda --version #콘다 설치 확인
conda 4.7.12 
~~~



# Python 가상환경 생성

~~~bash
$ conda search python #파이썬의 모든 버전을 볼 수 있다.
$ conda create -n py3.6 python=3.6 #설치
$ conda remove -name py3.6 --all #제거
$ conda info --envs #확인
$ conda activate py3.6 #실행
$ conda deactivate #종료
~~~

py3.6는 원하는대로 이름을 바꿔도 된다.



# 기타 설치

~~~bash
$ conda activate py3.7 #실행
$ pip install --upgrade pip

$ pip install tensorflow #tensorflow 2.0.0
$ pip install --upgrade tensorflow==1.5.0 #1.5.0으로 다운그레이드
tensorflow 1.5.0
tensorflow-estimator 2.0.1
tensorflow-tensorboard 1.5.1

$ pip install keras #keras 2.3.1 pyyaml 5.2 scipy 1.3.3

~~~



# 참고

>  https://cjwoov.tistory.com/23  [머신러닝\] 파이썬(Python), 텐서플로우(Tensor Flow) 설치

>  https://greedywyatt.tistory.com/108?category=328775  [Ubuntu 18.04] conda 가상환경에서 tensorflow-gpu / keras / jupyter notebook 설치
---
layout: post
title:  "[git] GIT add 에러 warning : LF will be replaced by CRLF"
subtitle:   "git사용법"
categories: Dev
tags: Git
comments: true
date:  2019-01-11 15:00:00
---

## 새로운 파일 추가히기
저장소를 연결하고, <code>git pull origin master</code>로 repository에 있던 파일들을 받고, 내가 새로 추가한 파일들과 함께 <code>git add .</code>(이하 생략)으로 다시 repository에 올린다. 

<pre><code>
git config --global user.name "내이름"
git config --global user.email "내 이메일"
git init
git remote add origin https://~~~저장소주소~~~.git
git pull origin master
git add .
git commit -m "쓰고싶은말"
git push origin master
</code></pre>

## 현재 상황

카카오톡 시각화 앱개발에 앞서서 git에 올려보려고 <code>git add</code> 명령어를 쳤더니 처음보는 에러가 떴다.
<pre><code> warning : LF will be replaced by CRLF</code></pre>
## 구글 검색 결과
lf와 crlf가 안맞아서 생기는 문제라고 한다. 나는 윈도우를 사용하고 있는데 git은 리눅스 기반이기 때문이다.

## CR, LF, CRLF
줄바꿈 문자열
- LF : 커서를 현재행의 다음행으로 아래로 내리기, 유닉스, 리눅스에서 사용 (\n)
- CR : 커서의 위치를 현재 행의 맨 좌측으로 옮김, 맥의 초기버전에서 사용
- CRLF : 커서를 다음행으로 내려서 맨 좌측으로 옮김, 윈도우에서 사용 (\r\n)

## 해결 방법
<pre><code>  $ git config core.autocrlf true </code></pre>
<pre><code>  $ git config --global core.autocrlf true </code></pre>
- git의 <code>core.autocrlf</code>를 true로 켜주는 코드이다. 
- 개발자가 git에 코드를 추가(commit)할때는 **CRLF->LF** 로 변환하고 git의 코드를 개발자가 볼때(clone등등)할때는 **LF->CRLF**로 변환해준다.
- 변환이 항상 일어나도록 하고 싶으면 <code>--global</code> 을 넣은 코드를 적고 해당 프로젝트에만 적용하고 싶으면 <code>--global</code>를 빼주면 된다.

## 참고
> http://ohgyun.com/554

> https://blog.jaeyoon.io/2018/01/git-crlf.html

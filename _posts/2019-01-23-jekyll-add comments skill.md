---
layout: post
title:  "[Jekyll] 댓글 기능 추가하기"
subtitle:   "jekyll 사용법"
categories: Dev
tags: Jekyll
comments: true
date:  2019-01-23 22:00:00
---

# 댓글 기능 추가하기


## 1. 디스커스 계정 생성하기
https://disqus.com/

## 2. 사이트 등록하기
https://disqus.com/admin/ 에서
"I want to install Disqus on my site" 버튼 누르고 정보를 입력한다.
아래 정보는 내가 입력한 정보이다.
- website Name : h-dyeon-github-io
- Category : Tech
- Language : Korean
language에 서 Korean 항목이 없어서 구글 검색을 했더니 
https://dottak.github.io/disqus/2018/09/29/disqus-language-korean/
블로그에서 편법(?)을 알려주었다 ㅎㅎㅎ

## 3. 정보 설정하기 

### Select Plan
요금제를 고른다. 나는 돈이 없으므로 Basic!

### Install Disqus
Jeykll 블로그를 사용하고 있으므로 jekyll을 선택하변 jekyll에서 어떻게 댓글을 적용시킬수 있는지 설명이 나온다.
1. <code>comments: true</code> 를 post마다 추가해준다.
2. "In between a {% if page.comments %} and a {% endif %} tag, copy and paste the Universal Embed Code in the appropriate template where you'd like Disqus to load."
그렇다고 한다. ==> 4.으로 이어진다.

### Configure Disqus(당장 안해도 되는듯!)
나중에 변경 가능하다길래 언어만 변경하고 나머지는 그대로 냅뒀다.
- Appearance : Auto/Auto
- Website Name : h-dyeon-github-io
- Website URL : 
- Comment Policy URL :
- Comment Policy Summary :
- Category : Tech
- Description :
- Language : Korean (또 없길래 아까와 같은 방법을 사용함)

## 4. 적용하기
1. Disquq 사이트 오른쪽 상단에 내 프로필을 누르면 View Profile 부터 시작해서 여러가지 항목이 있다. 그중에 **admin**을 누른다.
2. 사이트 상단 바에서 Settings을 누르고 내 블로그를 누른다.
3. 왼쪽 항목 들 중 **Installation/Jekyll**을 선택한다. 그러면 **정보설정하기/Install Disqus/2**에서 봤던 화면이 똑같이 나타난다.
4. 2번동그라미에서 **Universal Embede Code**를 누르면 코드가 나온다.
5. _layouts/post.html 파일 맨 하단에 보면 이렇게 적혀있다. disqus-shortname 이 있어야 하고 disqus.html 파일이 있어야 한다.

![post.html 파일의 맨 하단부분](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190123-jekyll/post_html.png)

6. _layouts/disqus.html 파일을 만든다. disqus 홈페이지에서 **Universal Embede Code**를 눌러서 나왔던 코드를 그대로 복사붙여넣기 해서 만든다.

![Universal Embede Code](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190123-jekyll/code.png)

7. _config.yml 파일에 disqus 계정을 추가한다.
~~~yml
disqus-shortname: h-dyeon-github-io
~~~
8. 내가 적을 post 상단에 아래 코드를 추가해주면 댓글을 쓸수있는 기능이 자동으로 추가되어진다.
~~~ 
---
comments: true
---
~~~


## 참고
https://m.blog.naver.com/skykbc/221124877511
디스커스 (disqus) 로 깃허브에 댓글 기능 달기 (jekyll, github pages)

https://skyksit.tistory.com/10
디스커스 (disqus) 로 깃허브에 댓글 기능 달기 (jekyll, github pages)

https://dottak.github.io/disqus/2018/09/29/disqus-language-korean/
Disqus 코멘트(댓글) 한국어 적용

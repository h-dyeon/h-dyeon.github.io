---
layout: post
title:  "[Jekyll] 수식 표현 사용하기"
subtitle:   "jekyll 사용법"
categories: Dev
tags: Jekyll
comments: true
date:  2019-12-10 22:00:00
---

# MathJax 설치하기

<code>_layouts/post.html</code>의 <code>< article></code> 태그 바로 다음에 아래 스크립트를 붙여 넣는다. post.html을 열어서 article을 검색했더니 해당 부분이 나왔다.

~~~html
# 전
<article> ~~~~ </article>
~~~

~~~html
# 후
<article> ~~~~ </article>
<script src="//cdnjs.cloudflare.com/ajax/libs/mathjax/2.5.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
~~~

해당 코드는 $$(block 수식)와 $(inline 수식) 모두 사용 가능하다.

# LaTeX 문법

 https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference 

~~~text
$$ \sum_{x=i}{e^x} $$ 
~~~

$$\sum_{x=i}{e^x}$$



# 참고

 https://helloworldpark.github.io/jekyll/update/2016/12/18/Github-and-Latex.html  Github로 블로그 만들기 + LaTeX 적용하기

 https://wani.kr/posts/2015/12/17/add-mathjax-to-jekyll/ 
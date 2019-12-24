---
layout: post
title:  "[네트워크] port 사용여부 확인 & 죽이기"
subtitle:   "port 사용여부 확인 & 죽이기발"
categories: CS
tags: Network port
comments: true
date:  2019-04-08 02:00:00
---


# 특정포트를 사용하는 프로그램 확인 
포트번호가 1234일 경우의 예시이다.

- window
~~~
netstat -ano | find "1234" 
~~~
- linux
~~~
lsof -n -i4TCP:1234
~~~



# 특정포트를 사용하는 프로그램 죽이기 
포트번호가 1234일 경우의 예시이다.

- window
~~~
// 포트를 검색하여 해당 포트의 PID 번호를 확인한다. (포트 1234에 해당하는 PID가 567일 경우)
taskkill /f /pid 567
~~~
- linux
~~~
fuser -k -n tcp 1234
~~~

## 참고
> http://www.cplusplus.com/reference/string/to_string/
to_string

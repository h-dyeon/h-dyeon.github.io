---
layout: post
title:  "[Jekyll] category 항목을 추가하기"
subtitle:   "jekyll 사용법"
categories: Dev
tags: Jekyll
comments: true
date:  2019-01-21 13:00:00
---

**leonids에만 해당하는 방법 일 수 있다**

# Category 추가
나는 이미 category가 적용이 되어있는 jekyll 테마 **leonids**를 깔아서 category를 따로 만들어 줄 필요는 없었다.
문제는 category 기능은 있지만 내가 원하는 카테고리를 어떻게 추가할것인지가 문제였다.
아무리 구글링을 해봐도 category 기능을 만드는 방법만 나오지, category를 추가하는 방법은 없었다.
결국 나는 **leonids**를 쓰는 사람들 블로그를 찾아서 직접 메일을 보내봤다.

## 첫번째 도움을 주신분
post를 추가할때 아래 코드를 적는데 그때 category를 그냥 원하는걸로 적으라고 하셨다.
적어보았으나 제대로 작동을 하지 않았다....
~~~markdown
---
title: "category add test"
layout: post
categories: [newCategory]
tags: [newTag]
---
~~~


## 두번째 도움을 주신분
첫번째 도움을 주신분의 방법으로 category를 생성하니 어떤건 정상작동이 되는데 어떤건 포스트가 안보인다던지, category가 제대로 생성이 안된다는 등의 문제가 있었다.
이분은 나의 파일을 보시더니 원인을 못찾았지만 아래 방법들을 확인해보라고 하셨다.
- Do not add “date” in the header of the markdown files. Jekyll already recognize its date via the name of the file, e.g. 2019-01-07-title.md, it knows this post is posted on 07 Jan 2019. I’ve never seen such a practice that includes date in the header. What is weird is that this post has the post date being 07 Jan 2019, as in the name 2019-01-07-android-visualization-1, but it shows below the title 19 Jan 2019.
- Please put the titles and the categories in double quotation marks
- Try to use only Latin letters in the titles and categories to see if there’s anything improved. Perhaps Korean letters make it misbehave, I honestly don’t know.


## 해결방법
아래 두 사진을 보자.
#### 성공예시

  ![정상적으로 category 추가된 코드](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190121-jekyll/190119code.png)
  - category 추가가 정상적으로 된 post의 코드이다. 

  ![정상적으로 category 추가된 화면](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190121-jekyll/190119view.png)
  - category 추가가 정상적으로 된 post의 화면이다.

#### 실패예시
  ![비정상적으로 category 추가된 코드](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190121-jekyll/190107code.png)
  - category 추가가 비정상적으로 된 post의 코드이다. 

  ![바정상적으로 category 추가된 화면](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190121-jekyll/190107view.png)
  - category 추가가 비정상적으로 된 post의 화면이다. 

#### 오류 화면
  ![오류가 난 화면](https://h-dyeon.github.io/assets/img/Dev/Jekyll/190121-jekyll/archive.png)
  - 빨간 사각형 부분을 보면 날짜가 중복 표시된것을 볼수있다. archive 페이지 뿐만아니라 category 페이지에선 아예 post가 보이지를 않는다. 

#### 결론
1번과 2번, 2개의 차이점이 보이는가? 답은 title이었다. title을 쌍따옴표로 묶으면 정상적으로 추가가 되고 따옴표를 쓰지 않으면 category 추가에 에러가 있었다.
두번째 도움을 주신분의 말씀에 해결방안이 있었다. ""- Please put the titles and the categories in double quotation marks""

<pre>title을 따옴표로 묶고 category에 원하는 이름을 적어주자</pre>
그럼 원하는대로 category가 만들어질것이니...

## 도움을 주신분들의 블로그
1. >http://hoisharka.github.io/
2. >http://www.tvhoang.com/
- 나는 왜때문에 이걸로 몇날며칠을 잡아먹은것인가...
도움을 주신분들 너무너무 감사드립니다!!!

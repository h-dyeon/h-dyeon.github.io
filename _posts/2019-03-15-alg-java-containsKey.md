---
layout: post
title:  "[java] LinkedHashMap에서 containsKey"
subtitle:   "java에서 LinkedHashMap에서 containsKey"
categories: Alg
tags: java LinkedHashMap containsKey
comments: true
date:  2019-03-15 23:00:00
---

# 코드
~~~ java
public class TestClass{
        public String one;
        public String two;
        TestClass(String one, String two){
            this.one=one;
            this.two=two;
        }
    }
    public void testPersonWord(){
        LinkedHashMap<TestClass, Integer> testMap= new LinkedHashMap<>();
        TestClass temp= new TestClass("hdy","hello");
        testMap.put(temp,3);
        TestClass temp2= new TestClass("hdy","hello");
        if(testMap.containsKey(temp2)){
            testMap.replace(temp2,5);
        }else{
            testMap.put(temp2,8);
        }
    }
~~~

나는 당연히 temp객체의 "hdy"와 "hello"값이 temp2객체의 값들과 동일해서 containsKey가 true를 반환할 줄알았다.
그런데 맋막상 디버깅을 해보니 false를 반환하셔 <code>testMap.put(temp2.8);</code>가 실행됐다. 
(ㅎ.... 또 대폭 고쳐야 한다 ㅎㅎㅎ... 당연히 될줄알았는데 ㅎㅎㅎ....)

# 원인
stackoverflow에 질문을 올렸다.

> Here is containKey method. The hashCode is used for comparing so definitely the hashCode of two object is difference so it can not be equal.
You can consider to use primitive key or use TestClass.getOne() to compare String.

**temp**와 **temp2**의 <code>hashCode</code>가 다르기 때문에 false를 리턴한다고 한다.
ㅎ.... string을 일일이 변경하라니.. 속도때문에 hashmap을 사용한건데 함수를 또 호출해버리면 도대체 어쩌라는것인지....

# HashCode
데이터를 사이에 끼우려면 하나씩 뒤로 이동시킨다음에 삽입을 해야한다.
이런 상황을 피하기 위해 만들어진 것이 hash인데, 데이터만의 고유주소를 만든다고 생각하면 쉽다.
특별한 알고리즘을 이용해서 특정 객체와 연관된 고유한 숫자를 생성하고 이를 인덱스로 사용하는것이다.
그러면 다른 데이터를 끼우기 위해 다른 데이터들이 밀려 이동하는 일이 없어도 되므로 성능이 향상된다.

hash를 사용한 HashMap, HashTable, HashSet, LinkedHashSet 등등은 key를 결정할때 hashcode를 사용하기 때문에 containsKey에서 hashcode를 비교하고
false가 반환된것이다.

# 그렇다면?
testMap의 내부의 모든 key를 얻어와서 string one, two를 일일이 비교해보는 수 밖에 없는것인가..


# 참고
>https://stackoverflow.com/questions/55175839/android-java-key-is-same-but-containskey-return-false/55176125#55176125
android java --key is same but containsKey return false

>https://nesoy.github.io/articles/2018-06/Java-equals-hashcode
Java equals()와 hashCode()에 대해 

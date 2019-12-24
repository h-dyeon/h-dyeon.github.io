---
layout: post
title:  "[알고리즘] sort(bubble,selection,insertion) 비교"
subtitle:   "sort(bubble,selection,insertion) 비교"
categories: Alg
tags: algorithm bubbleSort selectionSort insertionSort
comments: true
date:  2019-05-05 01:00:00
---

# bubble, selection, insertion 비교
bubble, selection,insertion은 모두 O(n^2) 시간복잡도를 가지는 정렬 알고리즘들이다.
모두 O(n^2)이라고 해서 같은 성능을 가질 것 같지만 사실은 미묘한 차이가 있다.

- **bubble** : 모든 항목을 검색해야 한다. 2개 항목을 비교하고 순서가 맞지 않으면 교환하는 과정을 데이터 수만큼 여러번 반복해야 한다. 다른 알고리즘에 비해 교환이 더 자주 일어난다.
- **selection** : 이미 정렬된 항목을 제외한 것들중에 최소값을 찾는 방식이다. 최소값을 찾기위해 모든 데이터를 탐색한다.
- **insertion** : 이미 정렬된 항목을 차례로 살펴보며 새로 삽입할 자리를 찾는다. 자리를 찾자 마자 해당 loop가 종료된다. 즉 삽입할 자리가 비교적 빠르게 찾는다면 그 이후의 항목을 탐색할 필요가 없는 것이다. 모든 항목을 다 탐색해야 하는 selection과 달리 insertion은 도중에 탐색이 중지될 가능성이 높으므로 Selection 보다는 성능이 좋다. 

# 그래프로 확인하기
다음 사이트에서 O(n^2) 정렬 알고리즘의 성능 그래프를 볼 수 있다.
정렬에 필요한 시간은 Bubble > Selection > Inersion 순으로 감소한다.
> http://clweb.csa.iisc.ernet.in/pradeep/Output/Sorting%20Algorithms.htm

데이터의 case에 따라 정렬하는데 걸리는 시간을 애니메이션으로 확인할 수 있는 사이트이다.
> https://www.toptal.com/developers/sorting-algorithms

---
layout: post
title:  "[cpp] 한 쌍의 데이터를 정렬하기"
subtitle:   "한 쌍의 데이터를 정렬하기"
categories: Alg
tags: cpp
comments: true
---

# 백준 11650번 : 한 쌍의 데이터를 정렬하기
흔히 우리가 알고있는 알고리즘은 <code>int arr[10]</code>등 과 같이 1개의 데이터에 대하여 정렬을 한다.
그런데 백준 11650번에서는 좌표값(x,y)을 입력받아서 x에 따라 정렬하고 x가 같을 경우 y에 따라 정렬해 출력해야 했다.

다음은 한 쌍의 데이터를 정렬 할 수 있는 c++ 코드이다.
~~~ c++
#include <iostream>
#include <algorithm>
using namespace std;

pair<int, int> arr[1000001];
bool compare(const pair<int, int>& a, const pair<int, int>&b) {
	//첫번째 수가 같다면
	if (a.first == b.first)
		return a.second < b.second; //두번째 수로 오름차순
	return a.first < b.first; //오름차순
}

int main() {
	int N;
	cin >> N;
	for (int i = 0; i < N; i++) {
		int x, y;
		cin >> arr[i].first >> arr[i].second;
	}
	sort(arr, arr + N, compare);

	for(int i=0;i<N;i++){
		cout << arr[i].first << " " << arr[i].second << "\n";
	}
}
~~~


compare 함수에서 내가 원하는 방식으로 지정할 수 있다. 부등호의 방향을 바꿔서 오름차순과 내림차순을 변경 할 수 있다.
이를 응용한다면 pair같이 한 쌍의 데이터 뿐만이 아니라 3쌍의 데이터도 정렬 할 수 있다.
~~~ c++
#include <iostream>
#include <algorithm>
using namespace std;

pair<int, pair<int, int>> arr[1000001];
bool compare(const pair<int, pair<int,int>>& a, const pair<int, pair<int, int>>&b) {
	//첫번째 수가 같다면
	if (a.first == b.first) {
		//두번째 수가 같다면
		if (a.second.first == b.second.first)
			return a.second.second < b.second.second; //세번째 수로 오름차순
		return a.second.first < b.second.first; //두번째 수로 오름차순
	}		
	return a.first < b.first; //첫번째 수로 오름차순
}
int main() {
	
	int N;
	cin >> N;
	for (int i = 0; i < N; i++) {
		int x, y,z;
		cin >> arr[i].first >> arr[i].second.first>>arr[i].second.second;
	}
	sort(arr, arr + N, compare);

	for(int i=0;i<N;i++){
		cout << arr[i].first << " " << arr[i].second.first << " " <<arr[i].second.second << "\n";
	}
}
~~~

# compare와 sort
백준 사이트에서 sort에 관한 여러가지 사용법을 정리해 두었다.
단순히 int형 1개 자료를 정렬할 수도 있고
내가 새로 정의한 자료형에 대해 정렬도 가능하다.
>> https://www.acmicpc.net/blog/view/22




---
layout: post
title:  "[코딩테스트] 백준 2751, 11650, 11651, 10814"
subtitle:   "백준 2751, 11650, 11651, 10814"
categories: Alg
tags: BOJ
comments: true
---

백준 2751, 11650, 11651, 10814

>  https://github.com/h-dyeon/Algorithm 



 10814, 10825, 10989, 11652, 11004, 10828, 9012, 10799, 10845, 10866, 10808, 10809, 10820, 2743, 11655, 10824, 11656, 1406, 1158, 1168, 10430, 2609, 1934, 1850, 9613, 11005, 2745, 1373, 1212, 2089, 11576, 1978, 1929, 6588, 11653, 10872, 1676, 2004



# 백준 2751 : 수 정렬하기 2
~~~c++
//algorithm 라이브러리를 사용 376ms 소요
#include <iostream>
#include <algorithm>

int arr[1000001];
using namespace std;
int main() {
	int n;
	scanf_s("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf_s("%d", &arr[i]);
	}
	sort(arr, arr + n);

	for (int i = 0; i < n; i++) {
		printf("%d\n", arr[i]);
	}
}

//priority queue를 이용 472ms 소요
#include <iostream>
#include <queue>
#include <vector>
#include <functional>
using namespace std;

int arr[1000001] = { 0, };
int main() {
	priority_queue <int,vector<int>,greater<int>> q;
	int N;
    scanf("%d",&N);
	for(int i=0;i<N;i++){
		int tmp;
        scanf("%d",&tmp);
		q.push(tmp);
	}
	for (int i = 0; i < N; i++) {
        printf("%d\n", q.top());
		q.pop();
	}
}

//https://www.acmicpc.net/source/15729484 
//vector와 sort함수 사용 284ms 소요
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main(void)
{
	int N;
	vector<int> v;
	cin.tie(NULL);
	ios_base::sync_with_stdio(false);
	cin >> N;
	for (int i = 0; i < N; i++)
	{
		int temp;
		cin >> temp;
		v.push_back(temp);
	}
	sort(v.begin(), v.end());
	for (int i = 0; i < N; i++)
		cout << v.at(i) << '\n';
}
~~~

# 백준 11650 : 좌표 정렬하기
~~~c++
//60ms 소요
#include <iostream>
#include <algorithm>
using namespace std;
pair<int, int> arr[1000001];
bool compare(const pair<int, int>& a, const pair<int, int>& b) {
	if (a.first == b.first)
		return a.second < b.second;
	return a.first < b.first;
}
int main() {
	int n;
	scanf_s("%d", &n);
	int x, y;
	for (int i = 0; i < n; i++) {
		scanf_s("%d %d", &x,&y);
		arr[i] = pair<int, int>(x, y);
	}

	sort(arr, arr + n, compare);

	for (int i = 0; i < n; i++) {
		printf("%d %d\n", arr[i].first, arr[i].second);
	}
}

//https://www.acmicpc.net/source/6339941
//40ms 소요 , vector사용
#include <iostream>
#include <vector>
#include <algorithm>
#include <utility>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	int n;
	cin >> n;
	vector<pair<int, int>> A(n);

	for (int i = 0; i < n; ++i)
		cin >> A[i].first >> A[i].second;

	sort(A.begin(), A.end());

	for (int i = 0; i < n; ++i)
		cout << A[i].first << ' ' << A[i].second << '\n';
}
~~~

# 백준 11651 : 좌표 정렬하기 2
~~~c++
//9796kb 60ms 소요
#include <iostream>
#include <algorithm>
using namespace std;
pair<int, int> arr[1000001];
bool compare(const pair<int, int>& a, const pair<int, int>& b) {
	if (a.second == b.second)
		return a.first < b.first;
	return a.second < b.second;
}
int main() {
	int n;
	scanf_s("%d", &n);
	int x, y;
	for (int i = 0; i < n; i++) {
		scanf_s("%d %d", &x,&y);
		arr[i] = pair<int, int>(x, y);
	}

	sort(arr, arr + n, compare);

	for (int i = 0; i < n; i++) {
		printf("%d %d\n", arr[i].first, arr[i].second);
	}
}

//3532kb 64ms
#include <iostream>
#include <algorithm>
#include <vector>
//#include <utility>
using namespace std;
vector<pair<int, int>> tmp;
bool compare(const pair<int, int>& a, const pair<int, int>& b) {
	if (a.second == b.second)
		return a.first < b.first;
	return a.second < b.second;
}
int main() {
	int n, x, y;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf("%d %d", &x, &y);
		tmp.push_back(pair<int, int>(x, y));
	}
	sort(tmp.begin(), tmp.end(),compare);

	for (int i = 0; i < n; i++) {
		printf("%d %d\n", tmp[i].first, tmp[i].second);
	}
}
~~~



# 백준 10814 : 나이순 정렬

~~~c++
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;
bool compare(pair<int, pair<int, string>>& a, pair<int, pair<int, string>>& b) {
  if (a.first == b.first)
    return a.second.first < b.second.first;
  return a.first < b.first;
}
int main() {
  int n, age;
  string name;
  vector<pair<int, pair<int,string>>> tmp;
  scanf("%d", &n);
  for (int i = 0;i < n;i++) {
    cin >> age >> name;
    pair<int, string> hh = pair<int, string>(i, name);
    tmp.push_back(pair<int, pair<int, string>>(age, hh));
  }
  sort(tmp.begin(), tmp.end(),compare);
  for (auto it = tmp.begin();it != tmp.end();it++) {
    cout << it->first << " " << it->second.second << "\n";
  }
}
~~~



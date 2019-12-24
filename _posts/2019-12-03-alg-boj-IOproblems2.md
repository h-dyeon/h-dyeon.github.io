---
layout: post
title:  "[코딩테스트] 입출력 문제들-2"
subtitle:   "백준 2741, 2742, 2739, 1924, 8393, 10818, 2438, 2439, 2440, 2441, 2442, 2445, 2522, 2446, 10991, 10992"
categories: Alg
tags: BOJ
comments: true
---

백준 2741, 2742, 2739, 1924, 8393, 10818, 2438, 2439, 2440, 2441, 2442, 2445, 2522, 2446, 10991, 10992

>  https://github.com/h-dyeon/Algorithm 



# 백준 2741 N 찍기

> https://stackoverflow.com/questions/213907/c-stdendl-vs-n

endl는 개행도 하고 내부버터를 비워주는 역할도 하기 때문에 느리다고 한다.

~~~c++
//맞은 코드
#include <iostream>
using namespace std;
int main() {
	int N;
	cin >> N;
	for (int i = 0;i < N;i++)
		cout << i + 1 << "\n";
}
//시간초과
#include <iostream>
using namespace std;
int main() {
	int N;
	cin >> N;
	for (int i = 0;i < N;i++)
		cout << i + 1 << endl;
}
~~~



# 백준 2742 N찍기
~~~c++
#include <iostream>
using namespace std;
int main() {
	int N;
	cin >> N;
	for (int i = N;i >0;i--)
		cout << i  << "\n";
}
~~~



# 백준 2739 구구단
~~~c++
#include <iostream>
using namespace std;
int main() {
	int N;
	scanf_s("%d", &N);
	for (int i = 1;i < 10;i++) {
		printf("%d * %d = %d\n", N, i, N * i);
	}
}
~~~



# 백준 1924 2007년
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x, y;
	int months[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };
	string days[7] = {"SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"  };
	scanf_s("%d %d", &x,&y);
	
	int sum = 0;
	for (int i = 0;i < x-1;i++)
		sum += months[i];
	sum += y;

	sum = sum % 7;
	cout << days[sum];
}
~~~



# 백준 8393 Sum
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);
	cout << x * (x + 1) / 2;
}
~~~



# 백준 10818 최소,최대
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x, tt;
	int max = -1000030;
	int min = 1200000;

	scanf_s("%d", &x);
	while (x--) {
		scanf_s("%d", &tt);
		if (max < tt) max = tt;
		if (min > tt)min = tt;
	}
	cout << min << " " << max;
}
~~~



# 백준 2438 별찍기-1
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < i+1;j++) {
			printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2439 별찍기-2
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < x;j++) {
			if(j<x-i-1) printf(" ");
			else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2440 별찍기-3
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);
	for (int i = 0;i < x;i++) {
		for (int j = 0;j < x;j++) {
			if(j<x-i) printf("*");
			//else printf(" "); //불필요한 출력
		}
		printf("\n");
	}
}
~~~



# 백준 2441 별찍기-4
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < x;j++) {
			if(j<i) printf(" ");
			else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2442 별찍기-5
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < x+i;j++) {
			if(j<x-i-1) printf(" ");
			else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2445 별찍기-8
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < 2*x-1;i++) {
		for (int j = 0;j < 2*x;j++) {
			if(i<x)
				if(j>i && j<2*x-i-1) printf(" ");
				else printf("*");
			else 
				if(j > 2*x-2-i&& j < i+1) printf(" ");
				else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2522 별찍기-12

~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < 2*x-1;i++) {
		for (int j = 0;j < x;j++) {
			if(i<x)
				if(j<x-i-1) printf(" ");
				else printf("*");
			else 
				if(j < i-x+1) printf(" ");
				else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 2446 별찍기-9
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < i;j++) printf(" ");
		for (int j = 0;j < 2*(x-i)-1;j++) printf("*");
		printf("\n");
	}
	for (int i = x-1;i >0;i--) {
		for (int j = i-1;j >0 ;j--) printf(" ");
		for (int j = 2 * (x - i)+1 ;j >0 ;j--) printf("*");
		printf("\n");
	}
}
~~~



# 백준 10991 별찍기-16
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x;i++) {
		for (int j = 0;j < x - 1-i;j++)printf(" ");
		for (int j = 0;j <= 2 * i ;j++) {
			if(j%2 == 1)printf(" ");
			else printf("*");
		}
		printf("\n");
	}
}
~~~



# 백준 10992 별찍기-17
~~~c++
#include <iostream>
using namespace std;
int main() {
	int x;
	scanf_s("%d", &x);

	for (int i = 0;i < x-1;i++) {
		for (int j = 0;j < x - 1-i;j++)printf(" ");
		for (int j = 0;j < 2 * i+1 ;j++) {
			if(j==0)printf("*");
			if(j == 2 * i-1)printf("*");
			else printf(" ");
		}
		printf("\n");
	}
	for (int j = 0;j < 2*x-1;j++)printf("*");
}
~~~

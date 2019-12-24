---
layout: post
title:  "[코딩테스트] 입출력 문제들-1"
subtitle:   "백준 2557, 1000, 2558, 10950, 10951, 10952, 10953, 11021, 11022, 11718, 11719, 11720, 11721"
categories: Alg
tags: BOJ
comments: true
---

백준 2557, 1000, 2558, 10950, 10951, 10952, 10953, 11021, 11022, 11718, 11719, 11720, 11721

>  https://github.com/h-dyeon/Algorithm 



# 백준 2557

~~~c++
#include <iostream>
using namespace std;
int main(){
    cout<<"Hello World!";
}
~~~


# 백준 1000
~~~c++
#include <iostream>
using namespace std;
int main(){
    int A, B;
    cin>>A>>B;
    cout<<A+B;
}
~~~


# 백준 2558
~~~c++
#include <iostream>
using namespace std;
int main(){
    int A, B;
    cin>>A>>B;
    cout<<A+B;
}
~~~


# 백준 10950
~~~c++
#include <iostream>
using namespace std;
int main(){
    int T,A, B;
    cin>>T;
    while(T--){
    cin>>A>>B;
    cout<<A+B<<"\n";
    }
}
~~~

# 백준 10951

 이 문제의 목적은 파일의 끝(EOF)을 올바르게 판단하는 법을 연습하는 것입니다. **총 몇 줄이 주어진다 등의 정보는 절대 입력으로 주지 않습니다. 또한 단순히 키보드로 입력 내용만 적고 프로그램이 종료되지 않은 상태까지만 봐서는 EOF를 제대로 처리했는지 알 수 없습니다.** 더 이상 읽을 게 없을 때 프로그램을 종료하는 법을 알아야 합니다.  

1. (C/C++) scanf는 EOF를 반환하지, 변수에 저장해주지 않습니다.
2. (Java) Scanner의 메서드들은 NoSuchElementException을 던집니다.
3. (Java) BufferedReader.readLine()은 null을 반환합니다.
4. (Python) input()은 EOFError를 발생시킵니다.
5. (Python) sys.stdin.readline()은 빈 문자열을 반환합니다.

>  https://www.acmicpc.net/board/view/39199 참고 링크

~~~c++
#include <iostream>
using namespace std;
int main() {
	int a, b;
	cin >> a >> b;
	while (!cin.eof()) {
		cout << a + b << "\n";
		cin >> a >> b;
	}
	return 0;
}
~~~

# 백준 10952
~~~c++
#include <iostream>
using namespace std;
int main() {
	int a, b;

	while (true) {
		cin >> a >> b;
		if (a == 0 && b == 0)
			break;
		cout << a + b << "\n";
	}
	return 0;
}
~~~

# 백준 10953

string -> int 방법 : c_str() 

~~~c++
#include <iostream>
using namespace std;
int main() {
	int  T;
	string str;
	cin >> T;
	while (T--) {
		cin >> str;
		string a = str.substr(0, str.find(","));
		string b = str.substr( str.find(",")+1);
		int aa = atoi(a.c_str());
		int bb = atoi(b.c_str());
		cout << aa + bb << "\n";
	}
	return 0;
}

//======================
#include <iostream>
int main() {
	int a;
	int c, d;
	scanf("%d", &a);
	for (int i = 0; i < a; i++) {
		scanf("%d,%d", &c, &d);
		printf("%d\n", c + d);
	}
}
~~~

# 백준 11021
~~~c++
#include <iostream>
using namespace std;
int main() {
	int  a,b,T;
	cin >> T;
	for (int i = 0; i < T; i++) {
		cin >> a >> b;
		cout << "Case #" << i + 1 << ": " << a + b << "\n";
	}
	return 0;
}
~~~

# 백준 11022
~~~c++
#include <iostream>
using namespace std;
int main() {
	int  a,b,T;
	cin >> T;
	for (int i = 0; i < T; i++) {
		cin >> a >> b;
		printf("Case #%d: %d + %d = %d\n",i+1,a,b,a+b);
	}
	return 0;
}
~~~

# 백준 11718

>  https://modoocode.com/44 
>
>   https://modoocode.com/38 

## getchar()

~~~c++
#include <stdio.h>  // C++ 의 경우 <cstdio>
int getchar(void);
~~~
<code>stdin</code>에서 한 문자를 가져온다. 읽어들인 문자를 int 값으로 리턴하고, 만약 파일 끝에 도달하거나 읽기 오류가 발생하면 <code>EOF</code>를 리턴, 혹은 오류가 발생한다.

~~~c++
//1개 문자 입력
char ch1;
scanf("%c" , &ch);
getchar(ch);
//1개 문자 입력
char ch2=getchar();
~~~
~~~c++
//버퍼비우기
int i;char ch3;
scanf("%d",&i);
getchar();
scanf("%c",&ch3);
printf("입력한 문자 : %c \n", c);
~~~
> 실행결과
> 1234
> c
> 입력한 문자 : c

만약 <code>getchar()</code>를 지워버린다면 c를 입력 받을 수 없을 것이다. 왜냐하면 이전에 호출한 <code>scanf</code>에 의해 버퍼에 이미 <code>\n</code>이 남아있기 때문이다.

## fgets()

~~~ c++
#include <stdio.h>  // C++ 의 경우 <cstdio>
char* fgets(char* str, int num, FILE* stream);
~~~

stream에서 문자열을 받는다.

 <code>str</code> : 읽어 들인 문자열을 저장할 <code>char</code> 배열을 가리키는 포인터. 

 <code>num</code> : 마지막 NULL을 포함해서, 읽어 들일 최대 문자수. 10으로 설정하면 컴퓨터는 최대 9개의 문자를 입력 받는다.

<code>stream</code> : 문자열을 읽어 들일 스트림의 <code>FILE</code> 객체를 가리키는 포인터. 

리턴값 :  <code>str</code> 가 리턴 된다. 만일 파일 끝에 도달하였는데 아무런 문자도 읽어 들이지 않았다면 `str` 의 내용은 변하지 않고 그 대신 `null` 포인터가 리 턴된다. 또한 오류가 발생해도 `null` 포인터가 리턴 된다.

~~~c++
//맞은코드
#include <stdio.h>
#include <stdlib.h>
int main()
{
	char ch=NULL;
	while (ch != EOF)
	{
		ch = getchar();
		if (ch == EOF)
			continue;
		putchar(ch); //stdout에 한 문자를 쓴다.
	}
	return 0;
}


//맞은 코드
#include <cstdio>
using namespace std;
int main() {
	char str[101];
	while (fgets(str, 101, stdin) != NULL) {
		printf("%s", str);
	}
	return 0;
}

//틀린 코드
#include<iostream>
using namespace std;
int main() {
	string str;
	cin >> str;
	while (cin.eof() != NULL) {
		cout << str;
		cin >> str;
	}
}
~~~

# 백준 11719
~~~c++
//맞은코드
#include <stdio.h>
#include <stdlib.h>
int main()
{
	char ch=NULL;
	while (ch != EOF)
	{
		ch = getchar();
		if (ch == EOF)
			continue;
		putchar(ch); //stdout에 한 문자를 쓴다.
	}
	return 0;
}


//맞은 코드
#include <cstdio>
using namespace std;
int main() {
	char str[101];
	while (fgets(str, 101, stdin) != NULL) {
		printf("%s", str);
	}
	return 0;
}

//틀린 코드
#include<iostream>
using namespace std;
int main() {
	string str;
	cin >> str;
	while (cin.eof() != NULL) {
		cout << str;
		cin >> str;
	}
}
~~~

# 백준 11720 숫자의 합
~~~c++
//맞은 코드
#include<iostream>
using namespace std;
int main() {
	int num, sum = 0;
	cin >> num;
	getchar();

	char str[101];
	fgets(str, 101, stdin);

	for (int i = 0; i < num; i++) {
		sum = sum + str[i] - 48;
	}
	cout << sum;
}

//맞은 코드
#include<cstdio>
int main() {
	int sum=0, num;
	scanf_s("%d", &num); //총횟수
	getchar(); //버퍼비우기
	for (int i=0; i < num; i++) { 
		sum += getchar() - 48; //한글자씩 읽음
	}
	printf("%d", sum); 
}
~~~

# 백준 11721 열 개씩 끊어 출력하기
~~~c++
//맞은 코드
#include<iostream>
using namespace std;
int main() {
	string str;
	cin >> str;
	int num = str.size() / 10;
	for(int i=0;i<num;i++)
	{
		cout << str.substr(0, 10) << "\n";
		str = str.substr(10);
	}
	cout << str << "\n";
	return 0;
}

//맞은 코드
#include<iostream>
using namespace std;

int main() {
	string S;
	cin >> S;
	for (int i = 0; i < S.length(); i += 10)
		cout << S.substr(i, 10) << endl;
	return 0;
}
~~~



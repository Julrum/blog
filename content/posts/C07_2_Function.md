---
title: "7-2. 함수"
date: 2020-03-26T14:33:59Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


## 04 재귀적 함수

재귀적 (recursive) 함수는 함수 실행 중간에 자기 자신 (실행되고 있는 함수) 을 또 호출하는 함수를 말한다.

재귀적 함수는 어떠한 조건이 만족될 때까지 반복하여 자신을 호출하게 되므로, 재귀적 호출을 중단하게 하는 조건이 반드시 있어야 한다.

함수의 호출시 프로그램 상태 (state) 를 보존하고, 자료의 일부를 피 호출함수에 전달하고, 피 호출함수의 종료와 더불어 호출 함수로 되돌아오는 과정을 반복하기 때문에 제귀적 함수를 처리하기 위하여 스택을 이용한다.

대표적인 예로는 팩토리얼 (factorial) 을 들 수 있다.

#### 실습 7_14_a)
```c
#include <stdio.h>
void rec_fun(int n) {
	int i;
	for(i = 0; i <= n; i++) {
		printf("%3d", n);
	}
}
void main() {
	rec_fun(9);
}
```

#### 실습 7_14_b)
```c
#include <stdio.h>
void rec_fun(int n) {
	if(n > 0) {
		rec_fun(n - 1);
		printf("%3d", n);
	}
}
void main() {
	rec_fun(9);
}
```

#### 실습 7_14
```c
#include <stdio.h>
void rec_fun(int n);
void rec_FUN(int n);
int main() {
	printf("일반 함수 : ");
	rec_fun(9);
	printf("\n재귀 함수 : ");
	rec_FUN(9);
	return 0; 
}
void rec_fun(int n) {
	int i;
	for(i = 0; i <= n; i++) {
		printf("%3d", n);
	}
}
void rec_FUN(int n) {
	if(n > 0) {
		rec_FUN(n - 1);
		printf("%3d", n);
	}
}
```

#### 실습 7_15
```c
#include <stdio.h>
int recursion(int n);
int main() {
	recursion(9);
	return 0;
}
int recursion(int n) {
	if(n > 0) {
		printf("%3d", n);
		recursion(n - 1);
	}
}
```

#### 실습 7_16
```c
#include <stdio.h>
int fact(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n);
	printf("%d! = %d", n, fact(n));
	return 0;
}
int fact(int n) {
	if(n == 1) return 1;
	else return n*fact(n - 1); 
}
```

#### 실습 7_17
```c
#include <stdio.h>
int sum(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n);
	printf("결과 : %d", sum(2*n));
	return 0;
} 
int sum(int n) {
	if(n < 3) return n;
	else return n + sum(n - 2);
}
```  

#### 실습 7_18
```c
#include <stdio.h>
int sum(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n);
	printf("결과 : %d", sum(n));
	return 0;
}
int sum(int n) {
	if(n == 1) return n;
	else return n + sum(n - 1);
}
```

#### 실습 7_19
```c
#include <stdio.h>
int main() {
	int i, n;
	printf("정수 : ");
	scanf("%d", &n);
	for(i = 1; i <= n; i++) {
		printf("%4d %4d\n", i, i*i);
	}
	return 0; 
}
```

#### 실습 7_20
```c
#include <stdio.h>
int sum(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n);
	if(n%2 == 0) {
		printf("홀수 : %d\n", sum(n - 1));
		printf("짝수 : %d", sum(n));
	} else {
		printf("홀수 : %d\n", sum(n));
		printf("짝수 : %d", sum(n - 1));
	}
	return 0;
} 
int sum(int n){
	if(n < 3) return n;
	else return n + sum(n - 2);
}
```

#### 실습 7_21
```c
#include <stdio.h>
void star(int n);
int main() {
	int i;
	printf("정수 : ");
	scanf("%d", &i);
	printf("결과 : ");
	star(i);
	return 0; 
} 
void star(int n) {
	int i;
	for(i = 0; i < n; i++) {
		printf("* ");
	}
	printf("\n");
}
```
 
#### 실습 7_22
```c
#include <stdio.h>
void star(int n);
int main() {
	int i, j, k;
	printf("너비 : ");
	scanf("%d", &i);
	printf("높이 : ");
	scanf("%d", &j);
	for(k = 0; k < j; k++)
		star(i);
	return 0; 
} 
void star(int n) {
	int i;
	for(i = 0; i < n; i++) {
		printf("* ");
	}
	printf("\n");
}
```

#### 실습 7_23
```c
#include <stdio.h>
int swmyg(int score);
int main() {
	int point, s;
	char grade[5][3] = {"수", "우", "미", "양", "가"};
	printf("점수 : ");
	scanf("%d", &point);
	s = swmyg(point);
	printf("결과 : %s", grade[s]);
}
int swmyg(int score) {
	if(score >= 90) return 0;
	else if(score >= 80) return 1;
	else if(score >= 70) return 2;
	else if(score >= 60) return 3;
	else return 4;
}
```
 
#### 실습 7_24
```c
#include <stdio.h>
int max(int a, int b);
int main() {
	int a, b, c, d;
	printf("정수 : ");
	scanf("%d %d %d %d", &a, &b, &c, &d);
	printf("결과 : %d", max(max(a, b), max(c, d)));
	return 0;
} 
int max(int a, int b) {
	if(a > b) return a;
	else return b;
}
```

#### 실습 7_25
```c
#include <stdio.h>
void gugu_class(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n); 
	gugu_class(n);
	return 0;
} 
void gugu_class(int n) {
	int i;
	for(i = 1; i < 10; i++)
		printf("%3d * %3d = %3d\n", n, i, n*i);
}
```  

#### 실습 7_26
```c
#include <stdio.h>
void square(int n);
int main() {
	int n;
	printf("정수 : ");
	scanf("%d", &n);
	square(n);
	return 0;
} 
void square(int n) {
	int i, j, cnt = 0;
	for(i = 0; i < n; i++) {
		for(j = 0; j < n; j++) {
			printf("%4d", ++cnt);
		}
		printf("\n");
	}
}
```

#### 실습 7_27
```c
#include <stdio.h>
int sq(int n, int o);
int main() {
	int n, o, r;
	printf("정수 : ");
	scanf("%d %d", &n, &o);
	printf("결과 : %d", sq(n, o));
	return 0;
}
int sq(int n, int o) {
	if(o == 1) return n;
	else return n*sq(n, o - 1);
}
```

#### 해보기_1
```c
#include <stdio.h> 
void star(int n);
int main() {
	int n, i;
	printf("정수 : ");
	scanf("%d", &n);
	for(i = 1; i <= n; i++) {
		star(i);
	}
	return 0;
}
void star(int n) {
	int i;
	for(i = 0; i < n; i++) printf("* ");
	printf("\n");
}
```

#### 해보기_2
```c
#include <stdio.h>
void translate(char ch, int l);
int main() {
	char ch;
	printf("문자 : ");
	scanf("%c", &ch);
	if(ch >= 'A' && ch <= 'Z') translate(ch, 32);
	else if(ch >= 'a' && ch <= 'z') translate(ch, -32);
	else translate(ch, 0);
	return 0;
}
void translate(char ch, int l) {
	if(l == 0) printf("Error\n");
	else printf("%c\n", ch + l);
}
```

#### 해보기_3
```c
#include <stdio.h>
int f[100];
//무차원배열, 특정 함수에 귀속되지 않고 모든 함수에서 사용 가능하다. 
int fib(int a);
int main() {
    int n;
    f[1] = 1; f[2] = 1;
    printf("정수 : ");
    scanf("%d", &n);
    printf("결과 : %d", fib(n));
    return 0;
}
int fib(int a) {
    if(a == 0) return 0;
    else if(f[a] == 0) f[a] = fib(a - 1) + fib(a - 2);
    return f[a];
}
```

#### 해보기_4
```c
#include <stdio.h>
int GCD(int a, int b);
int main() {
	int a, b;
	printf("정수 : ");
	scanf("%d %d", &a, &b);
	printf("결과 : %d", GCD(a, b));
	return 0;
}
int GCD(int a, int b) {
	if(a == b) return a;
	else if(a > b) return GCD(b, a - b);
	else return GCD(a, b - a);
}
```

#### 해보기_5
```c
// 양측의 선수가 무엇을 내느냐에 상관하지 않고 가위바위보의 승, 패, 무의 확률은 언제나 1/3이다. 
#include <stdio.h>
#include <stdlib.h>
int main() {
	int score[3] = {0, };
	int i, n;
	for(i = 0; i < 10; i++) {
		printf("가위 1, 바위 2, 보 3\n번호 입력 : ");
		scanf("%d", &n);
		n = rand()%3;
		printf("게임 결과 : ");
		if(n == 0) printf("승\n");
		else if(n == 1) printf("무\n");
		else printf("패\n");
		score[n]++; 
	}
	printf("%d승 %d무 %d패", score[0], score[1], score[2]);
	return 0;
}
```

#### 해보기_6
```c
#include <stdio.h>
int magic[100][100];
int main() {
	int i, j, bi, bj, c = 1;
	int n;
	printf("마방진 사이즈 입력 (홀수) : ");
	scanf("%d", &n);
	i = 0; j = n/2;
	magic[i][j] = c;
	for(c = 2; c <= n*n; c++) {
		bi = i;
		bj = j;
		i--;
		j++;
		if(i < 0) i = n - 1;
		if(j >= n) j = 0;
		if(magic[i][j] != 0) {
			i = bi + 1;
			j = bj;
		}
		magic[i][j] = c;
	}
	for(i = 0; i < n; i++) {
		for(j = 0; j < n; j++) {
			printf("%4d", magic[i][j]);
		}
		printf("\n");
	}
	return 0;
}
```

#### 해보기_7
```c
#include <stdio.h>
#include <string.h>
void delay(int n);
//이 함수의 용도는 시간 지연입니다. 
int main() {
	int i, c = 0;
	char msg[] = " Some Message";
	int len = strlen(msg);
	while(1) {
		printf("\n");
		for(i = 0; i < len; i++) {
			if(c + i < len) printf("%c", msg[c + i]);
			else printf("%c", msg[c + i - len]);
			delay(100);
		}
		c++;
		if(c > len) c = 0;
	}
} 
void delay(int n) {
	int i, j, k;
	for(i = 0; i < n; i++) {
		for(j = 0; j < n; j++) {
			for(k = 0; k < n; k++);
		}
	}
}
```
  

#### 해보기_8
```c
#include <stdio.h>
int cnt; 
void hanoi(int n, char i, char f, char a, int t);
int main() {
	int n;
	printf("판의 수 : ");
	scanf("%d", &n);
	hanoi(n, 'A', 'C', 'B', 1);
	printf("총 이동 횟수 : %d", cnt);
	return 0;
}
void hanoi(int n, char i, char f, char a, int t){
	if(n == 1) {
		printf("원판 %d - %c에서 %c로 이동\n", t, i, f);
		cnt++;
	} else {
		hanoi(n - 1, i, a, f, t);
		hanoi(1, i, f, a, t + n - 1);
		hanoi(n - 1, a, f, i, t);
	}
}
```
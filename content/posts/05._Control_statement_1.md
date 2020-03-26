---
title: "5-1. 제어문(반복문)"
date: 2020-03-25T13:20:09Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---

순차적인 프로그램 실행 순서를 변경하거나반복 수행하고자 할 때 사용하는 명령문

#### 종류

- 분기문 : if 문, switch~case문
- 반복문 : for 문, while 문
- 보조제어문 : continue 문, break 문

제어문에 따른 실행 문장이 한 문장이면 블록을 생략해도 좋다.

## 01 분기문

### 1) if 문

조건이 참이면 명령문1을 실행함

#### 문법
```c
if(조건문) {
	명령문1;
}
```
  
#### 실습 5_01

```c
#include <stdio.h>
int main() {
	int jumsu;
	printf("점수 = ? ");
	scanf("%d", &jumsu);
	if(jumsu >= 80)
		printf("합격");
	return 0; 
}
```

#### 실습 5_02

```c
#include <stdio.h>
int main() {
	int a;
	printf("정수 = ? ");
	scanf("%d", &a);
	if(0 == a%2)
		printf("합격");
	return 0; 
} 
```

#### 실습 5_03
```c
#include <stdio.h>
int main() {
	int a;
	printf("나이 = ?");
	scanf("%d", &a);
	if(a>5)
		printf("가격 = 16,000원");
	return 0;
}
```

### 2) if ~ else 문

조건이 참이면 명령문1을 실행하고, 거짓이면 명령문2을 실행

#### 문법
```c
if(조건문) {
	명령문1;
}
else {
	명령문2;
}
```
  
#### 실습 5_04
```c
#include <stdio.h>
int main() {
	int jumsu;
	printf("점수 = ?");
	scanf("%d", &jumsu);
	if(jumsu >= 80)
		printf("합격");
	else
		printf("불합격");
	return 0; 
} 
```

#### 실습 5_05
```c
#include <stdio.h>
int main() {
	int a;
	printf("정수 = ");
	scanf("%d", &a);
	if(a%2 == 0)
		printf("짝수");
	else
		printf("홀수");
	return 0;
}
```

#### 실습 5_06
```c
#include <stdio.h>
int main() {
	int a;
	printf("정수 : ");
	scanf("%d", &a);
	if(a>0)
		printf("양수");
	else
		printf("음수");
	return 0;
}
```

#### 실습 5_07
```c
#include <stdio.h>
int main() {
	char a;
	printf("문자 = ");
	scanf("%c", &a);
	if(a<91)
		printf("%c", a + 32);
	else
		printf("%c", a - 32);
	return 0; 
} 
```

### 3) if ~ else if ~ else

조건1이 참이면 명령문1을 실행하고, 거짓이면 다시 조건2를 판정하여 참이면 명령문2를, 거짓이면 명령문3을 실행하는 명령

#### 문법
```c
if (조건문1) {
	명령문1;
}
else if (조건문2) {
	명령문2;
}
else {
	명령문3;
}
```
  
#### 실습 5_08
```c
#include <stdio.h>
int main() {
	int a;
	printf("정수 = ");
	scanf("%d", &a);
	if(a > 0)
		printf("양수");
	else if(a == 0)
		printf("영");
	else
		printf("음수");
	return 0; 
} 
```

#### 실습 5_09
```c
#include <stdio.h>
int main() {
	char a;
	printf("문자 = ");
	scanf("%c", &a);
	if(a >= 65 && a <= 90)
		printf("대문자입니다.");
	else if(a >= 97 && a <= 122)
		printf("소문자입니다.");
	else
		printf("영문자가 아닙니다.");
	return 0; 
}
```

#### 실습 5_10
```c
#include <stdio.h>
int main() {
	int a;
	printf("점수 = ");
	scanf("%d", &a);
	if(a <= 100 && a >= 90)
		printf("수");
	else if(a <= 89 && a >= 80)
		printf("우");
	else if(a <= 79 && a >= 70)
		printf("미");
	else if(a <= 69 && a >= 60)
		printf("양");
	else if(a <= 59 && a >= 0)
		printf("가");
	else
		printf("0부터 100까지의 숫자를 입력하세요.");
	return 0; 
} 
```

#### 실습 5_11
```c
#include <stdio.h>
int main() {
	int a, b, c;
	printf("1 번째 숫자 입력 : ");
	scanf("%d", &a);
	printf("2 번째 숫자 입력 : ");
	scanf("%d", &b);
	printf("3 번째 숫자 입력 : ");
	scanf("%d", &c);
	if(a >= b && a >= c) {
		printf("최댓값 : %d", a);
	}
	else if(b >= a && b >= c) {
		printf("최댓값 : %d", b);
	}
	else {
		printf("최댓값 : %d", c);
	}
	if(a <= b && a <= c) {
		printf("최소값 : %d", a);
	}
	else if(b <= a && b <= c) {
		printf("최소값 : %d", b);
	}
	else {
		printf("최소값 : %d", c);
	}
	return 0; 
}
```

### 4) switch ~ case 문

조건 판정에 따라 여러 문장 중 하나를 실행하는 명령문

#### 문법
```c
switch(식) {
	case 값1 : 명령문1;
		break;
	case 값2 : 명령문2;
		break;
		*
		*
		*
	case 값n : 명령문n;
		break;
	default : 명령문;
		break;
}
```

#### 실습 5_12
```c
#include <stdio.h>
int main() {
	int rank;
	printf("등수 = ?");
	scanf("%d", &rank);
	switch(rank){
			case 1 : printf("금상"); break;
			case 2 : printf("은상"); break;
			case 3 : printf("동상"); break;
			case 4 : printf("장려상"); break;
			default : printf("참가상"); break;
	}
	return 0;
}
```

#### 실습 5_13
```c
#include <stdio.h>
int main() {
	int a, b;
	char c;
	printf("연산자와 두 정수 = ");
	scanf("%c %d %d", &c, &a, &b);
	switch(c) {
		case '+': printf("%d", a += b); break; 
		case '-' : printf("%d", a -= b); break;
		case '*' : printf("%d", a *= b); break;
		case '/' : printf("%d", a /= b); break;
		default : printf("제대로 입력하세요."); break;
	}
	return 0; 
} 
```
#### 실습 5_14
```c
#include <stdio.h>
int main() {
	int a;
	printf("횟수: ");
	scanf("%d", &a);
	switch(a) {
		case 1 : printf("hello"); break;
		case 2 : printf("hello hello"); break;
		case 3 : printf("hello hello hello"); break;
		case 4 : printf("hello hello hello hello"); break;
		case 5 : printf("hello hello hello hello hello"); break;
	}
}
```
---
title: "7-1. 함수"
date: 2020-03-26T13:53:05Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


- C언어는 여러 개의 함수들로 이루어진 형태임
- 함수라는 것은 프로그램 내에서 특정한 기능을 수행하도록 작성된 독립적인 모듈을 말함
- `main()` 함수는 항상 포함하여야 하며, 필요에 따라 서브 함수를 사용
- 프로그램 중 일정한 루틴을 많이 사용할 경우 별도의 처리루틴 작성
- 프로그램을 기능별로 함수로 작성하여 처리
- 함수를 이용함으로써 프로그램을 이해하고 수정하기 쉬운 구조적 프로그래밍 가능
- 함수의 종류에는 매크로 함수, 내장함수, 사용자 정의 함수 등이 있음
- 프로그램을 이해하고 수정하기 쉽고 구조적 프로그래밍이 가능하게 함

## 01 매크로 함수

매크로 함수는 프로그램 내에서 1개 이상의 문장으로 이루어진 프로그램의 한블록이 프로그램 곳곳에 반복적으로 쓰일 때, 이러한 프로그램 작성상의 불편을 없애기 위해 반복적으로 사용되는 부분을 약자로 따로 정의하여 사용하는 것을 말한다.이와 같이 반복적으로 쓰이는 부분을 약자로 따로 정의하는 것을 매크로 정의(macro definition)라 하고, 프로그램 상에서 약자를 이용하여 그 매크로를 사용하는 것을 매크로 호출(macro call)이라고 한다.

#### 매크로 사용시 유의사항
- 매크로 이름과 치환할 내용 사이에는 반드시 한 칸 이상의 공백을 둔다.
- 문장의 끝에 세미콜론(`;`)을 사용하지 않는다.
- 치환할 내용이 수식인 경우에는 반드시 그 수식을 괄호로 묶어주어야 한다.
- 매크로명은 소문자도 가능하나 변수명과의 구분을 위해 대문자로 사용하는 것이 좋다.

#### 형식
`#define 매크로명 치환될 문자열`


#### 매크로 사용 예
```c
#define PI 3.14159
#define MAX 100
#define PR(a) printf("%d",a)
#define MUL(a) (a)*(a)
```

#### 실습 7_01_a)
```c
#include <stdio.h>
#define MUL(a) a*a
int main() {
	printf("%d", MUL(1 + 2));
	return 0;
} 
```
#### 실습 7_01_b)
```c
#include <stdio.h>
#define MUL(a) (a)*(a)
int main() {
	printf("%d", MUL(1 + 2));
	return 0;
} 
```


## 02 내장 함수 (Library 함수)

- 내장함수는 입,출력함수와 같이 복잡한 처리루틴을 컴파일러 작성 시 미리 만들어 제공하는 되는 함수이다.
- 대부분 헤더파일에 포함되어 있고 맨 앞에 `#include <헤더파일>` 이라고 선언함으로써 헤더파일에 들어있는 함수들은 사용할 수 있다.

|종류|기능|내장 함수|
|:---:|:---:|:---:|
|`stdio.h`|표준 입출력 함수|`printf()`, `scanf()`, `gets()`, `getchar()`, `puts()`, `putchar()`, `fgetc()`, `fgets()`, `fputc()`, `fputs()`, `fopen()`, `fclose()`...|
|`conio.h`|콘솔 입출력 함수|`getch()`, `getche()`, `putch()`, `cgets()`...|
|`math.h`|수학 함수|`sin()`, `cos()`, `exp()`, `log()`, `sqrt()`, `abs()`, `pow()`...|
|`string.h`|문자열 처리 함수|`strcat()`, `strcpy()`, `strcmp()`, `strncat()` 등|


#### 실습 7_02
```c
#include <stdio.h>
#include <math.h>
int main() {
	double j = 2, k = 9;
	int i =- 3;
	printf("abs(%d) = %d\n",i, abs(i));
	printf("pow(%0.f,2) = %0.f\n",j, pow(j, 2));
	printf("sqrt(%0.f) = %0.f",k , sqrt(k));
	return 0;
} 
```

## 03 사용자 정의 함수

#### 함수 이름으로 사용할 수 있는 문자
- 영문자와 아라비아 숫자, `_`(underline)
- 함수 이름의 첫 번째 글자로 올 수 있는 것은 영문자, `_`(underline)
- 함수 이름의 길이는 최대 32 자이며 대소문자가 구별

#### 함수 호출 형식

`함수명(매개변수)`

#### 처리 과정
- 함수 호출부에서 함수를 호출하면 사용자 정의 함수는 별도의 메모리 영역이 확보되고 프로그램 실행이 사용자 정의 함수로 분기하여 실행
- 사용자 정의 함수의 실행이 끝나면 호출한 함수로 복귀
- 함수 호출부에서 함수 정의부에 값이나 주소를 넘기면 함수 정의부에서 넘겨받은 데이터를 이용하여 계산하고 계산결과를 호출부로 변환

#### 함수를 사용할 경우 C언어 프로그램 구조
- 방법1 : 호출되는 함수를 미리 작성하고 `main()` 함수를 마지막에 작성
- 방법2 : 함수 선언부를 미리 작성하고 `main()` 함수를 작성하고 그 이후에 사용자 정의함수를 작성

#### 실습 7_03_a)
```c
#include <stdio.h>
void hamsu() {
	printf("정의된 함수 처리 \n");
}
int main() {
	printf("함수 호출\n");
	hamsu();
	printf("함수 복귀\n");
	return 0; 
}
```


#### 실습 7_03_b)
```c
#include <stdio.h>
void hamsu() ;
int main() {
	printf("함수 호출\n");
	hamsu();
	printf("함수 복귀\n");
	return 0; 
}
void hamsu() {
	printf("정의된 함수 처리 \n");
}
```

#### 실습 7_04
```c
#include <stdio.h>
void line_print(int);
int main() {
	printf("<ABC 프로그램 설명서>\n");
	line_print(1);
	printf("1. 프로그램 작성 규칙\n");
	line_print(2);
	return 0;
}
void line_print(int m) {
	int i;
	for(i = 1; i <= m; i++)
	printf("=====================\n");
}
```

#### 실습 7_05_a)
```c
#include <stdio.h>
void star_print(int m){
	int i, j;
	for(i = 1; i <= m; i++){
		for(j = 1; j <= i; j++){
			printf("%3c", '*');
		}
		printf("\n");
	}
} 
int main() {
	int n = 5;
	star_print(n);
	return 0;
}
```

#### 실습 7_05_b)
```c
#include <stdio.h>
void star_print(int);
int main() {
	int n = 5;
	star_print(n);
	return 0;
}
void star_print(int m){
	int i, j;
	for(i = 1; i <= m; i++){
		for(j = 1; j <= i; j++){
			printf("%3c", '*');
		}
		printf("\n");
	}
} 
```

#### 실습 7_06_a)
```c
#include <stdio.h>
int Max(int a, int b) {
	if(a > b) {
		return a;
	} else {
		return b;
	}
}

int main() {
	int a, b, m;
	printf("두 수를 입력 : ");
	scanf("%d%d",&a, &b);
	m = Max(a, b);
	printf("두 수 중 큰 값: %d\n", m);
	return 0;
}
```

#### 실습 7_06_b)
```c
#include <stdio.h>
int Max(int, int);
int main() {
	int a, b, m;
	printf("두 수를 입력 : ");
	scanf("%d%d",&a, &b);
	m = Max(a, b);
	printf("두 수 중 큰 값: %d\n",m);
	return 0;
}

int Max(int a, int b){
	if(a > b){
		return a;
	} else {
		return b;
	}
}
```

#### 매개변수 전달 방법
1.  Call by Value
	- 실매개변수 값을 형식매개변수에 복사하여 값을 전달하는 방식으로 복사한 후 실매개변수 값과 형식매개변수의 값은 서로 독립적

#### 실습 7_07
```c
#include <stdio.h>
void func(int x, int y);
int main() {
	int x = 3, y = 5;
	func(x, y);
	printf("main : ");
	printf("x= %d, y= %d\n", x, y);
	return 0;
}
void func(int x, int y){
	x = 10; y = 20;
	printf("func : ");
	printf("x=%d, y=%d\n",x, y);
}
```
2. Call by Reference
	- 실매개변수의 주소를 형식매개변수에 전달하는 방식
	- 복사한 후 실매개변수 값과 형식매개변수의 값은 서로 종속적
	- 실매개변수의 주소(`&`)를 보내면 형식매개변수는 포인터(`*`)로 주소 받음

#### 실습 7_08
```c
#include <stdio.h>
void func(int *x, int* y);
int main() {
	int x = 3, y = 5;
	func(&x, &y);
	printf("main : ");
	printf("x=%d, y=%d\n", x, y);
	return 0;
}
void func(int *x, int *y){
	*x = 10; *y = 20;
	printf("func : ");
	printf("x=%d, y=%d\n", *x, *y);
}
```

#### 실습 7_09
```c
#include <stdio.h>
int add_fun(int n, int m);
float ave_fun(int n, int m);
void out_fun(int add, float ave);
int main() {
	int a, b;
	printf("두 수 입력 : "); scanf("%d %d", &a, &b);
	out_fun(add_fun(a, b), ave_fun(a, b));
	return 0;
}
int add_fun(int n, int m) {
	return m + n;
}
float ave_fun(int n, int m) {
	float c;
	c += m;
	c += n;
	c /= 2.0;
	return c;
}
void out_fun(int add, float ave) {
	printf("합 : %d, 평균 : %.2f", add, ave);
}
```

#### 실습 7_10
```c
#include <stdio.h>
int max(int l, int m, int n);
int main() {
	int a, b, c;
	printf("세 수 입력 : "); scanf("%d %d %d", &a, &b, &c);
	printf("최댓값 : %d", max(a, b, c));
	return 0;
}
int max(int l, int m, int n) {
	if(l > m && l > n) return l;
	else if(m > n) return m;
	else return n;
}
```

#### 실습 7_11
```c
#include <stdio.h>
int prime(int data);
int main() {
	int a;
	printf("정수 : ");
	scanf("%d", &a);
	if(prime(a) == 1) printf("%d는 소수입니다.", a);
	else printf("%d는 소수가 아닙니다.", a);
} 
int prime(int data) {
	int i;
	for(i = 2; i < data; i++) {
		if(data%i == 0) return 0;
	}
	return 1;
}
```

#### 실습 7_12
```c
#include <stdio.h>
#include <math.h>
double pythagoras(int x1, int y1, int x2, int y2);
int main() {
	int a, b, c, d;
	printf("좌표1 : ");
	scanf("%d %d", &a, &b);
	printf("좌표2 : ");
	scanf("%d %d", &c, &d);
	printf("두 점사이의 거리 = %f", pythagoras(a, b, c, d));
	return 0;
} 
double pythagoras(int x1, int y1, int x2, int y2) {
	int x, y;
	x = abs(x1 - x2);
	y = abs(y1 - y2);
	x *= x;
	y *= y;
	return sqrt(x + y);
}
```
  

#### 실습 7_13
```c
#include <stdio.h>
float average(int *a, int n);
int main() {
	int i;
	int a[100];
	for(i = 1; i < 11; i++) {
		printf("%d번째 데이터 : ", i);
		scanf("%d", (a + i - 1));
	}
	printf("Average : %.2f", average(a, 10));
	return 0;
} 
float average(int *a, int n) {
	int i, sum=0;
	for(i = 0; i < n; i++) {
		sum += a[i];
	}
	return sum/(float)n;
}
```
---
title: "4. 연산자와 수식"
date: 2020-03-25T11:41:00Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


## 01 산술연산자

|연산자|기능|사용|
|:---:|:---:|:---:|
|`+`|좌우의 값을 더한다.|`a=b+c`|
|`-`|왼쪽의 값에서 오른쪽의 값을 뺀다.|`a=b-c`|
|`*`|좌우의 값을 곱한다.|`a=b*c`|
|`/`|왼쪽의 값을 오른쪽의 값으로 나눈다.|`a=b/c`|
|`%`|왼쪽의 값을 오른쪽의 값으로 나눈 나머지를 구한다.|`a=b%c`|

#### 실습 4_01
```c
#include <stdio.h>
int main() {
	int a, b, add, sub, mul, div, mod;
	printf("두 수 입력 : ");
	scanf("%d %d", &a, &b);
	add = a + b;
	sub = a - b;
	mul = a * b;
	div = a / b;
	mod = a % b;
	printf("덧셈 = %d 뺄셈 = %d 곱셈 = %d 나눗셈 %d = %d 나머지 = %d", add, sub, mul, div, mod);
	return 0;
}
```
#### 실습 4_02
```c
#include <stdio.h>
int main() { 
int a, mul;
    printf("도형 : ");
    scanf("%d", &a);
    printf("내각 : %d", (a-2)*180);
    return 0;
}
```
#### 실습 4_03
```c
#include <stdio.h>
int main() {
    int a, b;
    printf("피제수 : ");
    scanf("%d", &a);
    printf("제수 : ");
    scanf("%d", &b);
    printf("나머지 : %d", a-(a/b)*b);
    return 0;
}
```

## 02 비교연산자

|연산자|의미|기능|사용|
|:---:|:---:|:---:|:---:|
|`==`|같다.|두 값이 동일하면 참|`a==`b|
|`!=`|같지 않다.|두 값이 다르면 참|`a!=b`|
|`<`|보다 작다.|왼쪽이 작으면 참|`a<b`|
|`<=`|작거나 같다.|왼쪽이 작거나 같으면 참|`a<=b`|
|`>`|보다 크다.|왼쪽이 크면 참|`a>b`|
|`>=`|크거나 같다.|왼쪽이 크거나 같으면 참|`a>=b`|

#### 실습 4_04
```c
#include <stdio.h>
int main() {
	int a, b;
	printf("두 수 입력 : ");
	scanf("%d %d", &a, &b);
	printf("%d == %d = %d\n", a, b, a == b);
	printf("%d != %d = %d\n", a, b, a != b);
	printf("%d < %d = %d\n", a, b, a < b);
	printf("%d > %d = %d\n", a, b, a > b);
	printf("%d <= %d = %d\n", a, b, a <= b);
	printf("%d >= %d = %d\n", a, b, a >= b);
	return 0; 
}
```
#### 실습 4_05
```c
#include <stdio.h>
int main() {
	char in;
	printf("영문자 입력 : ");
	scanf("%c", &in);
	(in>96) ? printf("0",in) : printf("1",in);
	
	return 0;
} 
```
#### 실습 4_06
```c
#include <stdio.h>
int main () {
	int a, b, c;
	printf("반지름 : ");
	scanf("%d", &a);
	printf("x, y축 : ");
	scanf("%d %d", &b, &c);
	(b * b + c * c <= a * a) ? printf("1") : printf("0");
	return 0;
}
```
## 03 논리연산자

|연산자|기능|사용|
|:---:|:---:|:---:|
|`&&`|두 값(조건)이 모두 참이면 참을 반환한다.|`a&&b`|
|`||`|두 값(조건)중의 하나라도 참이면 참을 반환한다.|`a||b`|
|`!`|오른쪽의 값(조건)이 참이면 거짓을, 거짓이면 참을 변환한다.|`!a`|

#### 실습 4_07
```c
#include <stdio.h>
int main() {
	printf("1 AND 1 = %d\n", 1 && 1);
	printf("1 AND 0 = %d\n", 1 && 0);
	printf("0 AND 1 = %d\n", 0 && 1);
	printf("0 AND 0 = %d\n", 0 && 0);
	printf("1 OR 1 = %d\n", 1 || 1);
	printf("1 OR 1 = %d\n", 1 || 0);
	printf("1 OR 1 = %d\n", 0 || 1);
	printf("1 OR 1 = %d\n", 0 || 0);
	printf("NOT 1 = %d\n", !1);
	printf("NOT 0 = %d\n", !0);
	return 0;
}
```
#### 실습 4_08
```c
#include <stdio.h>
int main() {
	int a, b, c;
	printf(" 두 수 입력 : ");
	scanf("%d %d", &a, &b);
	printf("검사할 수 입력 : ");
	scanf("%d", &c); 
	(a < c)&&(c < b)? printf("1") : printf("0");
	return 0;
}
```
## 04 증감연산자

|연산자|기능|사용|
|:---:|:---:|:---:|
|`++`|값을 1 증가시킨다.|`a++`, `++a`|
|`--`|값을 1 감소시킨다.|`a--`, `--a`|

#### 실습 4_09
```c
#include <stdio.h>
int main() {
	int i;
	i = 3;
	printf("전위형으로 썼을 때 : %d\n", ++i);
	i = 3;
	printf("후위형으로 썼을 때 : %d\n", i++);
	return 0;
}
```
#### 실습 4_10
```c
#include <stdio.h>
int main() {
	int a, b, c;
	scanf("%d", &a); // 변수 a에 숫자 입력
	b = ++a; c = a--;
	printf("a = %d\tb = %d\tc = %d\n", a, b, c);
	return 0; 
}
```
#### 실습 4_11
```c
#include <stdio.h>
int main() {
	int a, b, c;
	scanf("%d", &a);
	b = ++a + ++a;
	c = a++ + a++;
	printf("a = %d\tb = %d\tc = %d\n", a, b, c);
	return 0;
} 
```
## 05 비교연산자

|연산자|기능|사용|
|:---:|:---:|:---:|
|`=`|오른쪽의 값을 왼쪽의 변수에 대입한다.|`a=b`|
|`+=`|왼쪽의 변수에 들어있는 값과 오른쪽 값을 더하여 왼쪽 변수에 대입한다.|`a+=b`|
|`-=`|왼쪽의 변수에 들어있는 값과 오른쪽 값을 뺀 후 왼쪽 변수에 대입한다.|`a-=b`
|`*=`|왼쪽의 변수에 들어있는 값과 오른쪽 값을 곱하여 왼쪽 변수에 대입한다.|`a*=b`|
|`/=`|왼쪽의 변수에 들어있는 값과 오른쪽 값을 나눈 왼쪽 변수에 대입한다.|`a/=b`
|`%=`|왼쪽의 변수에 들어있는 값과 오른쪽 값을 나눈 나머지를 왼쪽 변수에 대입한다.|`a%=b`|

#### 실습 4_12
```c
#include <stdio.h>
int main() {
	int a = 10, b = 5, c = 3;
	a -= b; b *= a + c; c += b += a;
	printf("a=%2d b=%2d c=%2d\n", a, b, c);
	return 0;
} 
```

#### 실습 4_13
```
1. a+=b;
2. b-=c;
3. c/=d;
4. d*=e;
5. e=2;
```
  

## 06 조건연산자

#### 실습 4_14
```c
#include <stdio.h>
int main() {
	int i, j;
	scanf("%d %d", &i, &j); // 두 수 입력
	(i>j) ? printf("%d가 %d보다 크다.\n", i, j) : printf("%d가 %d보다 크지 않다.\n", i, j);
	return 0;
}
```
#### 실습 4_15
```c
#include <stdio.h>
int main() {
	int a, b, c, max;
	printf("첫째 수 입력 : "); scanf("%d", &a);
	printf("둘째 수 입력 : "); scanf("%d", &b);
	printf("셋째 수 입력 : "); scanf("%d", &c);
	max = (a > b) ? a : b;
	max = (max > c) ? max : c;
	printf("가장 큰 수는 : %d\n", max);
	return 0;
} 
```
## 07 연산자와 우선순위

1. 괄호 안의 내용이 우선 처리된다.
2. 왼쪽에서 오른쪽으로 계산된다.
3. 단향 연산자가 이항 연산자보다 우선 계산된다.
4. 조건 연산자는 산술 연산자보다 나중에 계산된다.

그러나 위의 순서와 달리 우선적으로 처리되어야 하는 연산자가 있다. 이러한 연산자들의 우선순위는 다음 표와 같다.

|우선순위|연산자의 종류||연산자|
|:---:|:---:|:---:|:---:|
|높다|단항연산자||`!`, `~`, `++`, `--`, `-`, `*`, `&`|
||이항 연산자|승제산|`*`, `/`, `%`|
|||가감산|`+`, `-`|
|||이동|`>>`, `<<`|
|||비교|`<`, `<=`, `>`, `>=`, `==`, `!=`|
|||비트연산|`&`, `^`, `|`|
|||논리|`&&`, `||`|
||조건 연산자||`?`, `:`|
|낮다|대입 연산자||`=`, `=+`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `&=`, `^=`, `|=`|


#### 실습 4_16
```c
#include <stdio.h>
int main() {
	int a, b, temp;
	scanf("%d %d", &a, &b);
	printf("원본 : %d %d\n",a,b);
	temp= a;
	a=b;
	b=temp;
	printf("교환 : %d %d",a,b);
	return 0;
} 
```
#### 실습 4_17
```c
#include <stdio.h>
int main() {
	int a, b;
	scanf("%d %d", &a, &b);
	printf("원본 : %d %d\n", a, b);
	a-=b;
	b+=a;
	a-=b;
	a=-a;
	printf("교환 : %d %d", a, b);
	return 0;
}
```
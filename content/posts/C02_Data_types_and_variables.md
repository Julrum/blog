---
title: "2. 자료형과 변수"
date: 2020-03-24T14:42:15Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---

## 1) 자료형의 크기 및 표현 범위

|정수형|문자형|부동 소수점 형|
|:---:|:---:|:---:|
|`short 변수명;`|`char 변수명;`|`float 변수명;`|
|`int 변수명;`||`double 변수명;`|
|`long 변수명;`||`long double 변수명;`|
|` unsigned short 변수명;`|||
|` unsigned int 변수명;`|||
|` unsigned long 변수명;`|||

|자료형|크기|수의 표현 범위|
|:---:|:---:|:---|
|`short`|4 byte|-32768 ~ 32767 (-2<sup>15</sup> ~ 2<sup>15</sup> -1)|
|`int`|4 byte|-2<sup>31</sup> ~ 2<sup>31</sup> -1|
|`long`|4 byte|-2<sup>31</sup> ~ 2<sup>31</sup> -1|
|`unsigned short`|2 byte|0 ~ 65535|
|`unsigned int`|4 byte|0 ~ 2<sup>32</sup> -1|
|`unsigned long`|4 byte|0 ~ 2<sup>32</sup> -1|
|`char`|1 byte|0 ~ 255|
|`float`|4 byte|약 10<sup>-38</sup> ~ 10<sup>38</sup>|
|`double`|8 byte|약 10<sup>-308</sup> ~ 10<sup>308</sup>|
|`long double`|8 byte|약 10<sup>-308</sup> ~ 10<sup>308</sup>|

#### 실습 2_01

```c
#include <stdio.h>
int main() {
	float x, y;
	x=1.0;
	y=2.0;
	printf("x와 ,y의 합은 %f이다.\n", x + y);
	return 0;
}
```

#### 실습 2_02

```c
#include <stdio.h>
int main() {
	char ch = 'A';
	printf("%c\n",ch);
	ch = 65;
	printf("%c\n",ch);
	ch = '\x41';
	printf("%c\n",ch);
	ch = '\101';
	printf("%c\n",ch);	
    return 0;
} 
```

#### 실습 2_03

```c
#include <stdio.h>
int main() {
	char ch = 'a';
	printf("ch : %c char형의 크기 : %d byte\n", ch, sizeof(ch));
	printf("ch : %d %c %c\n", ch, ch, ch+1);
    return 0;
} 
```

#### 실습 2_04

```c
#include <stdio.h>
int main() {
	printf("\n%d ", sizeof(short));
	printf("%d ", sizeof(int));
	printf("%d ", sizeof(long));
	printf("%d ", sizeof(unsigned short));
	printf("%d ", sizeof(unsigned int));
	printf("%d ", sizeof(unsigned long));
	printf("%d ", sizeof(char));
	printf("%d ", sizeof(float));
	printf("%d ", sizeof(double));
	printf("%d\n", sizeof(long double));
    return 0;
} 
```

#### 실습 2_05

```c
#include <stdio.h>
int main() {
	int cm,m,km; // 변수형을 정수형으로 계산
	km=2;
	m= km * 1000;
	cm=m *100;
	printf("km를 m와 cm로 환산\n");
	printf("  %d km", km);
	printf("  %d m", m);
	printf("  %d cm\n", cm);
    return 0;
} 
```

#### 실습 2_06

```c
#include <stdio.h>
int main() {
	int a = 32767;
	long b = 32767;
	unsigned int c = 32767;
	printf("int형의 수의 표현 : %d %d 크기 : %d byte\n", a, a + 1, sizeof(a));
	printf("long형의 수의 표현 : %d %d 크기 : %d byte\n", b, b + 1, sizeof(b));
	printf("unsigned int형의 수의 표현 : %d %d 크기 : %d byte\n", c, c + 1, sizeof(c));
    return 0;
}
```

#### 실습 2_07

```c
#include <stdio.h>
#include <conio.h>
int main() {
	float a = 35.27;
	double b = 123.4567;
	printf("a : %f float형의 크기 : %d byte\n", a, sizeof(a));
	printf("b : %f double형의 크기 : %d byte\n", b, sizeof(b));
    return 0;
}
```

## 1) 변수란?

정의 : 어떤 연산을 처리하기 위하여 필요한 값을 넣어두기 위한 방의 이름

A라는 변수가 있다고 가정하면, A라는 변수는 어떤 값을 넣어 두기 위한 방이다.

## 2) 변수 사용 과정

1. 사용할 변수명을 지정한다.
2. 해당 변수를 사용한다는 것을 선언한다. 이때 변수에 저장될 데이터의 형(자료형)을 알려 주어야 한다.
3. 변수에 값(자료)을 넣는다(대입).

## 3) 변수명의 지정

### (1) 변수명

- 첫 번째 문자는 반드시 알파벳이나 밑줄 문자(\_)이어야 한다.
- 하나의 명칭 안에 공백을 사용할 수 없다.
- 대문자와 소문자는 서로 다른 문자로 처리한다.
- 예약어들은 명칭으로 사용할 수 없다.
- 사용 가능한 문자 :
    - 영문자 : A-Z, a-z
    - 숫 자 : 0-9
    - 밑줄(Under Line) : \_
- 길이에 제한이 없으나 첫 32자가 같으면 동일한 이름으로 간주

### (2) 예약어

- C 언어에서 특별한 의미가 이미 정의 되어 있는 이름
- 소문자로 되어 있으며 재정의 할 수 없고 명칭에 사용하는 등 다른 목적으로 사용할 수 없다.

||||||
|:---:|:---:|:---:|:---:|:---:|
|`int`|`extern`|`if`|`case`|`sizeof`|
|`char`|`register`|`else`|`break`|`union`|
|`float`|`typedef`|`for`|`continue`|`long`|
|`double`|`static`|`do`|`default`|`short`|
|`struct`|`goto`|`while`|`entry`|`unsigned`|
|`auto`|`return`|`switch`|||

#### 실습 2_08
```c
#include <stdio.h>
#include <conio.h>
int main() {
	int $pay;
	char 1abc;
	float -plus;
    return 0;
}
```

## 4) 기호 상수

자주 사용되는 복잡한 수치 값이나 긴 문자열을 간단히 단어로 선언한 후 해당 언어를 사용하면 선언된 자료가 대입되도록 한 것

상수명은 일반적으로 구분하기 쉽도록 대문자를 사용하고, 문장의 끝에 세자열인 경우에는 인용부호(")로 묶어 주어야 한다.

#### 실습 2_09

```c
#include <stdio.h>
# define PI 3.141592
int main() {
	printf("%f", PI);
	return 0;
} 
```
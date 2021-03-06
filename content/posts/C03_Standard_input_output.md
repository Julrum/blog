---
title: "3. 표준 입출력 함수"
date: 2020-03-25T08:07:51Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


## 01 printf( ) 함수

데이터를 서식에 맞추어 화면상에 출력하게 하는 함수

#### 형식

`printf("문자열");`

`printf("서식 문자열", 인수1[, 인수2, ...]);`

#### 출력 형식

|출력 형식|설명|
|:---:|:---:|
|`%c`|한 개의 문자|
|`%d`|10 진수|
|`%e`|지수형의 실수|
|`%f`|실수|
|`%g`|e 포맷이나 f 포맷 중 짧은 형식으로 출력|
|`%s`|문자열|

  
#### 실습 3_01
```c
#include <stdio.h>
int main() {
	printf("프로그램 실행결과를 출력합니다.");
	printf("정수=%d\n실수=%f", 60, 70.55); 
    return 0;
} 
```

#### 제어 문자열 양식

|제어문자|기능|
|:---:|---|
|`\n`|커서를 다음 행의 선두로 이동시킨다. (줄을 바꾸어 출력)|
|`\t`|커서를 탭(tab) 만큼 칸을 이동시킨다.|
|`\b`|커서를 한 칸 앞으로 이동시킨다.|
|`\a`|삑 하는 소리를 낸다.|
|`\ \` |\를 출력한다.|
|`\'` |'를 출력한다.|
|`\"`|"를 출력하다.|

#### 실습 3_02
```c
#include <stdio.h>
int main() {
	printf("출력양식 : %s %d %f %c ", "one", 2, 3.33, 'G');
    return 0;
} 
```
> 문자와 문자열의 차이를 정확히 이해해야 합니다.

|문자|문자열|
|:---:|:---:|
|단일 따옴표 내에 기술된다.|이중 따옴표 내에 기술된다.|
|포맷 %c에 의해 입출력 된다.|포맷 %s 에 의해 입출력 된다.|

#### 실습 3_03
```c
#include <stdio.h>
int main() {
	printf("출력양식 : %s %c", "A", "A");
    return 0;
} 
```
#### 실습 3_04
```c
#include <stdio.h>
int main() {
	printf("출력양식 : %s %c ", 'A', 'A');
    return 0;
} 
```
#### 실습 3_05
```c
#include <stdio.h>
int main() {
	printf("문자열 출력     :[%-20s]\n","고등학교");
	printf("문자열 출력     :[%20s]\n","컴퓨터과학과");
	printf("문자 출력       :[%10c]\n",'a');
	printf("문자 출력       :[%-10c]\n",'a');
	printf("문자 정수값출력 :[%-10d]\n",'A');
	printf("왼쪽 정렬       :[%-10d]\n",1234);
	printf("오른쪽 정렬     :[%10d]\n",1234);
	printf("0삽입 출력      :[%010d]\n",1234);
	printf("음수의 0삽입    :[%010d]\n"-1234);
	printf("부동소수점 출력 :[%8.2f]\n",123.4567);
    printf("부동소수점 출력 :[%-8.2f]\n",123.4567);
    printf("부동소수점 출력 :[%10.2f]\n",0.0012345);
    printf("부동소수점 출력 :[%10.2e]\n",0.00012345);
    printf("부동소수점 출력 :[%10.2g]\n\n",0.0000012345);
    return 0;
} 
```
  

## 02 scanf( ) 함수

키보드를 통하여 입력 서식에 맞게 데이터를 입력받는 함수

#### 형식

`scanf("서식문자열",&인수1[, &인수2, ...]);`

단, 배열명에는 `&`를 쓰지 않는다.(배열명 자체가 주소를 나타내기 때문)

#### 입력양식

|입력|양식 의미|
|:---:|:---:|
|%c|한 개의 문자|
|%d|10 진수|
|%f|실수|
|%s|문자열|

#### 실습 3_06
```c
#include <stdio.h>
int main() {
    int a, b, c;
    scanf("%d %d", &a, &b);
    c = a + b - 2;
    printf("%d + %d - 2 = %d\n", a, b, c);
    return 0;
} 
```

> `scanf()` 함수의 입력변수(입력대상) 앞에서는 `&`를 꼭 붙여 주어야 합니다. 단, 배열명에는 배열명 자체가 주소를 나타내기 때문에 `&` 를 쓰지 않습니다.
> `scanf()` 함수는 공백을 포함한 문자열은 입력할 수 없기 때문에 이때는 문자열 입력함수인 `gets()` 함수를 사용합니다.

## 03 단일 문자 입출력 함수

### 1) getchar( ) 함수
키보드를 통하여 하나의 문자를 입력받는 함수

문자를 입력하고 반드시 Enter 키를 입력해야 데이터가 프로그램에 전달.

#### 형식

`getchar();`

#### 실습 3_07
```c
#include <stdio.h>
int main() {
    char c;
    printf("영문자를 입력하십시오 : ");
    c= getchar();
	printf("입력한 문자는 %c입니다.", c); 
    return 0;
} 
```

### 2) getch( ) 함수

키보드를 통하여 하나의 문자를 입력받는 함수이며 데이터의 입력과 동시에 화면에 입력 데이터를 표시하지 않고 바로 프로그램에 전달

#### 형식

`getch( );`

#### 실습 3_08
```c
#include <stdio.h>
#include <conio.h>
int main() {
	char c;
	printf("영문자를 입력하십시오 : ");
	c=getch();
	printf("입력한 문자는 %c입니다.", c);
	return 0;
}
```

### 3) getche( ) 함수

키보드를 통하여 하나의 문자를 입력받는 함수이며 데이터의 입력과 동시에 화면에 입력 데이터를 표시하고 바로 프로그램에 전달

#### 형식

`getche();`

#### 실습 3_09
```c
#include <stdio.h>
#include <conio.h>
int main() {
	char c;
	printf("영문자를 입력하십시오 : ");
	c = getche();
	printf("입력한 문자는 %c입니다.", c);
	return 0;
}
```

### 4) putchar( ) 함수

단일 문자를 출력하는 함수

#### 형식

`putchar(출력할 내용이나 인수);`

#### 실습 3_10
```c
#include <stdio.h>
int main() {
	char c;
	printf("영문자를 입력하십시오 : ");
	c = getchar();
	putchar(c);
	putchar('\n');
	return 0;
}
```

## 04 문자열 입출력 함수

### 1) gets( ) 함수

키보드를 통하여 문자열을 입력받을 때 사용하는 함수

> `scanf()` 함수 함수는 입력 데이터의 구분을 space bar 나 Enter 키에 의해 구분하지만, `gets()` 함수는 Enter 키에 의해서만 데이터 구분

#### 형식

`gets(문자열 변수);`

#### 실습 3_11
```c
#include <stdio.h>
int main() {
	char getsname[20], scanfname[20];
	printf("이름을 입력하세요 : ");
	gets(getsname);
	printf("이름을 입력하세요 : ");
	scanf("%s", scanfname);
	printf("gets 이용해 이름 출력 : %s \n", getsname);
	printf("scanf 이용해 이름 출력 : %s \n", scanfname);
	return 0;
}
```

### 2) puts( ) 함수

문자열을 출력하고 함수, 출력 후 자동으로 줄을 바꾸어 줌

#### 형식

`puts(문자열 상수 또는 문자열 변수);`

#### 실습 3_12
```c
#include <stdio.h>
int main() {
	char name[20], tel[15];
	puts("이름을 입력하세요.");
	gets(name);
	puts("연락쳐를 입력하세요.");
	gets(tel);
	printf(" 이름 : %s  전화번호 : %s",name, tel);
	return 0;
}
```
#### 실습 3_13
```c
#include <stdio.h>
int main() {
	char a; 
	printf("문자하나를 입력하세요.\n");
	printf("입력 : ");
	scanf("%c", &a);
	printf("입력된 문자는 %c 입니다.", a);
	return 0; 
}
```
#### 실습 3_14
```c
#include <stdio.h>
#include <conio.h>
int main() {
	printf("데이터를 출력할 때에는 \" printf() 함수 \"를 사용한다.\n");
	printf("데이터를 출력할 때에는 \" scanf() 함수 \"를 사용한다.\n");
	printf("데이터를 출력할 때에는 \\n 줄바꿈 문자를 사용한다."); 
	return 0;
}
```
#### 실습 3_15
```c
#include <stdio.h>
int main() {
	int a, b;
	printf("자료입력");
	scanf("%d %d", a, b);
	return 0; 
} 
```
#### 실습 3_16
```c
#include <stdio.h> 
int main() {
	char num[20];
	printf("주민등록 번호를 입력하세요 : ");
	scanf("%s", num);
	return 0;
}
```
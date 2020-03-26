---
title: "8. 포인터"
date: 2020-03-26T14:47:53Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


## 01 포인터 및 포인터 변수

### 포인터(pointer)란?
  
포인터란 데이터가 기억되어 있는 기억 장소의 전지를 나타내는 주소 값을 의미한다. 우리가 변수를 선언하면 컴퓨터는 변수의 데이터형에 맞는 메모리 크기를 잡게 된다. 이때 할당된 메모리의 위치는 주소값을 갖게 되는 데 이 주소값을 포인터라 한다.

### 포인터 사용의 특징

- C 언어이 가장 큰 특징의 하나로 메모리의 데이터를 쉽게 접근하여 이용할 수 있다.
- 잘못 사용 시 난해한 프로그램이 된다.
- 배열을 포인터를 이용하여 효율적으로 사용할 수 있다.

### 포인터 변수

주소를 값으로 갖는 변수를 의미한다. 일반적인 변수는 변수의 값으로 정수, 상수 등을 저장할 수 있으나 주소값을 저장할 수 는 없다. 이러한 주소를 저장할 경우에 사용하는 것이 포인터 변수이다.

### 포인터 변수의 선언

변수 선언시에 변수명 앞에 *기호를 사용하여 선언한다.

#### 일반형식

`변수명 *변수명;`

예)` int *a;`
- 포인터 변수이 이름은 `a`이다.
- 포인터 변수 `a`의 데이터형이 `int`형을 의미하는 것이 아니라, 포인터 변수 `a`가 가리키는 번지에 기억 되어있는 데이터형이 `int` 형이다.
- `*a`는 포인터 변수`a`가 가리키는 번지에 들어있는 데이터를 말한다.

### 번지 연산자(`&`)

  
변수선언에 의해 할당된 메모리의 번지(위치)를 알아내는 데 사용하는 연산자이다. C언어에서 변수와 문자열 등은 기억장소에 저장되고, 할당된 기억장소들은 특정한 주소를 가지게 된다. 이렇게 할당된 변수의 번지는 변수명 앞에 번지 연산자 `&` 기호를 사용하여 알아낼 수가 있다.


#### 일반 형식

`&변수명 ;`

예) `&han ;`

- 변수 `han`이 할당된 메모리의 번지(주소)를 알아낸다.

#### 실습 8_01
```c
#include <stdio.h>
int main() {
	int *a, b;
	a = &b;
	*a = 10;
	printf("*a=%d\n", *a);
	printf("a의 값 = %X\n",a);
	printf("b=%d\n",b);
	printf("b의 주소값 = %X\n", &b);
	return 0;
}
```

#### 실습 8_02
```c
#include <stdio.h>
int main() {
	int a, *b;
	a = 123;
	printf("init a=%d\n",a);
	b = &a;
	*b = *b + 500;
	printf("after a=%d\n",a);
	return 0;
} 
```

### 포인터와 문자열
  
문자열을 저장하기 위해서는 변수를 배열로 선언해 주어야 한다. 이때 문자열의 길이에 따라 배열의 크기를 이용하여 문자열을 취급하게 되면 문자열의 길이를 고려하지 않아도 되어 편리하다. 또한 배열을 이용하는 경우 문자열 처리 시 배열의 첨자 값을 일일이 계산다면서 처리해야 되나 포인터를 이용하면 문자열이 저장되어 있는 메모리의 주소를 직접 접근하여 처리하므로 처리 속도가 빨라지는 장점이 존재한다.
  
### 포인터를 이용한 문자열 선언

  
문자열을 포인터 선언과 동시에 초기화 하면 문자열의 처음 데이터가 기억될 메모리의 시작 주소가 자동적으로 포인터 변수에 저장된다. 그러면 단순 변수에서와 같이 포인터 변수가 가리킬 기억 장소의 주소를 초기화하지 않아도 된다.

#### 일반형식

`데이터형 포인터변수명 = "문자열"`

#### 실습 8_03
```c
#include <stdio.h>
int main() {
	char *a = "seoul";
	int b = 0;
	while (*(a + b) != '\0'){
		printf("*(a+%d) ==> %c \n", b, *(a + b));
		b++;
	}
	printf("a=%s\n",a);
	return 0;
}
```
#### 실습 8_04
```c
#include <stdio.h>
int main() {
	char *a = "stu";
	int k = 10, *b;
	b = &k;
	int c = 0;
	printf("<문자형 포인터 변수 a>\n");
	for(c = 0; c < 3; c++) {
		printf("(a+%d) --> %X\n", c, (a + c));
	}
	printf("\n<정수형 포인터 번수 b>\n");
	for(c = 0; c < 3; c++) {
		printf("(b+%d) --> %X\n",c,(b + c));
	}
	return 0;
} 
```


### 포인터와 배열  
  
#### 포인터와 배열의 관계

배열과 포인터는 서로 밀접한 관계를 갖고 있다. 배열명은 배열의 첫번째 원소가 저장된 주소를 가리키는 포인터 변수이다. 배열명을 시작 주소로 정하고 여기에 몇 번째 원소인가를 나타내는 숫자를 더하여 배열원소를 포인터로 취급할 수 있다.

#### 참고

배열 원소의 크기는 데이터형에 따라 문자형 데이터이면 1바이트, 정수형(`int`) 숫자 데이터이면 4바이트, 실수형(`float`) 숫자 데이터이면 4바이트이지만 데이터형의 크기에 상관없이 처음 시작 원소를 기준으로 원하는 원소의 위치를 1씩 증가한 상태로 지정하면 알아서 데이터의 형의 바이트 수만큼 포인터의 위치가 자동으로 증가된다. (데이터형별로 할당하는 메모리의 크기는 컴퓨터의 시스템에 따라 2바이트 또는 4바이트로 할당할 수 있다.)

#### 실습 8_05
```c
#include <stdio.h>
int main() {
	int a[] = {10, 20, 30, 40, 50, 60};
	int k;
	for(k = 0; k < 6; k++) {
		printf("a+%d=%X ", k ,a + k);
		printf("*(a+%d)=%d a[k]=%d \n", k, *(a + k), a[k]);
	}
	return 0;
}
```

#### 실습 8_06
```c
#include <stdio.h>
int main() {
	char a[][7] = {"apple","grapes","pear"};
	char *p;
	int k;
	p = &a[0][0];
	for(k = 0; k < 3; k++)
		printf("a[%d]=%s \n", k, a[k]);
	printf("1234567123456712345671234567\n");
	for(k = 0; k < 21; k++)
	printf("%c", *(p + k));
	return 0;
} 
```

#### 실습 8_07
```c
#include <stdio.h>
int main() {
    int a = 10, b = 20, c = 30, *p = &a, *q = &b, *r = &c;
    printf(" 변수명   변수값   변수주소   포인터변수명   *포인터변수 \n");
    printf("   a        %d        %X        p                %d \n", a, &a, *p);
    printf("   b        %d        %X        q                %d \n", b, &b, *q);
    printf("   c        %d        %X        r                %d \n", c, &c, *r);
    return 0;
}
```

#### 실습 8_08
```c
#include <stdio.h>
#include <string.h>
int main() {
	char *str = "ABCDEFGH";
	int i, len;
	len = strlen(str);
	for (i = len-1; i >= 0; i--) {
	printf("%10s\n", str + i);
	}
	return 0;
}
```

#### 실습 8_09
```c
#include <stdio.h>
#include <string.h>
int main() {
	char str[100];
	int i, len;
	printf("입력할 문자열은? ");
	fgets(str, 100, stdin);
	len = strlen(str);
	str[len-1] = '\0';
	len--;
	printf("변환 후 문자열 : ");
	for(i = len - 1; i >= 0; i--) {
	    printf("%c", *(str + i));
	}
	return 0;
}
```

#### 실습 8_10
```c
#include <stdio.h>
#define MAXLEN 20
void printing(int *data);
void sorting(int *data);
void inserting(int *data, int k);
void erasing(int *data, int k);
int main() {
    int data[MAXLEN+1] = {0, };
    int i;
    printf("%10s <입력된 데이터>\n ", "");
    for (i = 0; i < 10; i++) {
        scanf("%d", &data[i]);
    }
    printf("%10s <정렬된 데이터>\n", "");
    sorting(data);
    printing(data); printf("\n");
    while (1) {
        int code, num;
    printf("작업할 코드는 (삽입=1, 삭제=2, 작업끝=0)? ");
    scanf("%d", &code);
    switch (code) {
        case 0:
	        return 0;
        case 1:
            printf(" 삽입할 수는=? ");
            scanf("%d", &num);
            inserting(data, num);
	        printing(data);
            break;
        case 2:
	        printf(" 삭제할 수는=? ");
	        scanf("%d", &num);
	        erasing(data, num);
	        printing(data);
	        break;
        }
    }
    return 0;
}
void printing(int *data) {
    int *i;
    for (i = data; *i != 0; i++) {
    printf("%4d", *i);
    }
    printf("\n");
}
void sorting(int *data) {
    int *i, *j, tmp;
    for (i = data; *i != 0; i++) {
        for (j = i+1; *j != 0; j++) {
        if (*i > *j) {
            tmp = *i;
            *i = *j;
            *j = tmp;
            }
        }
    }
}
void inserting(int *data, int k) {
    int *i, *j, *insrtpos, length;
    for (length = 0; data[length] != 0; length++) ;
    if (length >= MAXLEN) {
        printf("삽입 불가.\n");
        return;
     }
     if (*data > k) insrtpos = data;
     else insrtpos = data+length;
     for (i = data; *i != 0; i++) {
            if (*i <= k && k <= *(i+1)) {
                insrtpos = i+1;
            }
     }
     for (i = data+length-1; i >= insrtpos; i--) {
         *(i + 1) = *i;
     }
     *insrtpos = k;
}
void erasing(int *data, int k) {
    int *i, *rmvpos;
    if (*data == 0) {
        printf("삭제 불가.\n");
        return;
    }
    for (rmvpos = data; *rmvpos != 0; rmvpos++) {
    if (*rmvpos == k) {
        break;
        }
    }
    if (*rmvpos == 0) {
        printf("%d을(를) 찾을 수 없습니다.\n", k);
    }
    for (i = rmvpos; *i != 0; i++) {
    *i = *(i + 1);
    }
}
```
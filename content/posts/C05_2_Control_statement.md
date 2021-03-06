---
title: "5-2. 제어문(반복문)"
date: 2020-03-25T13:59:19Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---

## 02 반복문

프로그램 수행 중 특정 문장을 반복 수행하고자 할 때 사용하는 명령문

### 1) for 문

변수가 초기값을 가지고 증감식에 의해 증감하면서 조건식이 만족하는 동안 반복하는 명령

#### 문법
```c
for(초기값; 조건식; 증감식) {
	반복할 명령문;
}
```
 
#### 실습 5_15_a)
```c
#include <stdio.h>
int main() {
	int i;
	for(i = 1; i<=10; i++)
		printf("%5d", i);
	return 0;
} 
```

#### 실습 5_15_b)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 1; a <= 10; a += 2)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_c)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 2; a <= 10; a += 2)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_d)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 10; a >= 1; a--)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_e)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 10; a >= 1; a -= 2)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_f)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 9; a >= 1; a -= 2)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_g)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 10; a <= 30; a += 5)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_h)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 30; a >= 10; a -= 5)
		printf("%5d", a);
	return 0;
}
```

#### 실습 5_15_i)
```c
#include <stdio.h>
int main() {
	int a;
	for(a = 65; a <= 78; a++)
		printf("%c", a);
	return 0;
}
```

#### 실습 5_16_a)
```c
#include <stdio.h>
int main() {
	int a, sum;
	sum = 0;
	for(a = 0; a < 9; a++) {
		if(a < 10)
			printf("%d+", a);
		else
			printf("%d=", a);
		sum = sum + a;
	}
	printf("%d", sum);
	return 0;
}
```

#### 실습 5_16_b)
```c
#include <stdio.h>
int main() {
	int a, sum;
	sum = 0;
	for(a = 1; a <= 9; a += 2) {
		if(a < 9)
			printf("%d+", a);
		else
			printf("%d=", a);
		sum = sum + a;
	}
	printf("%d", sum);
	return 0;
}
```

#### 실습 5_16_c)
```c
#include <stdio.h>
int main() {
	int a, sum;
	sum = 0;
	for(a = 2; a <= 10; a += 2) {
		if(a < 10)
			printf("%d+", a);
		else
			printf("%d=", a);
		sum = sum + a;
	}
	printf("%d", sum);
	return 0;
}
```

### 2) 다중 for 문

#### 문법
```c
for (초기값1; 조건식1; 증감식1) {
	명령문1;
	for (초기값2; 조건식2; 증감식2) {
		명령문2;
	}
}
```

#### 실습 5_17_a)
```c
#include <stdio.h>
int main() {
	int a = 1, b;
	for(a; a <= 5; a++) {
		for(b = 1; b <= 5; b++) {
			printf("%5d", b);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_17_b)
```c
#include <stdio.h>
int main() {
	int a = 0, b = 0;
	for(a = 0; a < 5; a++) {
		for(b = 0; b < 5; b++) {
			printf("%5d", a*5 + b + 1);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_17_c)
```c
#include <stdio.h>
int main() {
	int a = 0, b = 0;
	for(a = 0; a < 5; a++) {
		for(b = 0; b < 5; b++) {
			printf("%5d", a + 5*b + 1);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_17_d)
```c
#include <stdio.h>
int main() {
	char a ='A', b;
	for(a; a <= 'E'; a++) {
		for(b = 'A'; b <= a; b++) {
			printf("%5c", b);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_17_e)
```c
#include <stdio.h>
int main() {
	char a = 'A', b = 'A';
	for(a = 'A'; a <= 'E'; a++) {
		for(b ='A'; b <= a; b++) {
			printf("%5c", b);
		}
		printf("\n");
	}
	return 0;
}
```

### 3) while 문

조건식이 만족하는 동안 반복 수행할 문장을 반복 수행하는 명령

#### 문법
```c
while(조건문) {
	명령문;
	증감식;
}
```
  
#### 실습 5_18_a')
```c
#include <stdio.h>
int main() {
	int i = 1;
	while(i <= 10) {
		printf("%5d", i);
		i++;
	}
	return 0;
}
```

#### 실습 5_18_a)
```c
#include <stdio.h>
int main() {
	int i = 0;
	while(i < 10) {
		i++;
		printf("%5d", i);
	}
	return 0;
}
```

#### 실습 5_18_b)
```c
#include <stdio.h>
int main() {
	int i = 2;
	while(i <= 10) {
		printf("%5d", i);
		i += 2;
	}
	return 0;
}
```

#### 실습 5_18_c)
```c
#include <stdio.h>
int main() {
	int i = 10;
	while(i >= 1) {
		printf("%5d", i);
		i--;
	}
	return 0;
}
```

#### 실습 5_18_d)
```c
#include <stdio.h>
int main() {
	int i = 9;
	while(i >= 0) {
		printf("%5d", i);
		i -= 2;
	}
	return 0;
}
```

#### 실습 5_18_e)
```c
#include <stdio.h>
int main() {
	int i = 30;
	while(i >= 10) {
		printf("%5d", i);
		i -= 5;
	}
	return 0;
}
```

#### 실습 5_18_f)
```c
#include <stdio.h>
int main() {
	char i = 'A';
	while(i <= 'N') {
		printf("%c", i);
		i++;
	}
	return 0;
}
```

#### 실습 5_18_h)
```c
#include <stdio.h>
int main() {
	int i =- 1, sum = 0;
	while(i < 9) {
		if(i < 7) {
			i += 2;
			printf("%d + ", i);
		}
		else {
			i += 2;
			printf("%d = ", i);
		}
	sum = sum + i;
	}
	printf("%d", sum);
	return 0;
}
```

### 4) do ~ while 문

조건식이 만족하는 동안 반복 수행할 문장을 반복 수행하는 명령

#### 문법
```c
do {
	명령문;
	증감식;
} while(조건문);
```

#### 실습 5_19_a')
```c
#include <stdio.h>
int main() {
	int i = 1;
	do {
		printf("%5d", i);
		i++;
	}
	while(i <= 10);
	return 0;
}
```

#### 실습 5_19_a)
```c
#include <stdio.h>
int main() {
	int i = 0;
	do {
		i++;
		printf("%5d", i);
	}
	while(i < 10);
	return 0;
}
```

#### 실습 5_19_b)
```c
#include <stdio.h>
int main() {
	int i = 1;
	do {
		printf("%5d", i);
		i += 2;
	}
	while(i <= 10);
	return 0;
}
```

#### 실습 5_19_c)
```c
#include <stdio.h>
int main() {
	int i = 10;
	do {
		printf("%5d", i);
		i -= 1;
	}
	while(i >= 1);
	return 0;
}
```

#### 실습 5_19_d)
```c
#include <stdio.h>
int main() {
	int i = 10;
	do {
		printf("%5d", i);
		i -= 2;
	}
	while(i >= 1);
	return 0;
}
```

#### 실습 5_19_e)
```c
#include <stdio.h>
int main() {
	char i = 'A';
	do {
		printf("%c", i);
		i++;
	}
	while(i <= 'N');
	return 0;
}
```

#### 실습 5_19_f)
```c
#include <stdio.h>
int main() {
	int i = 0, sum = 0;
	do {
		if(i < 9) {
			i++;
			printf("%d + ", i);
		}
		else{
			i++;
			printf("%d = ", i);
		}
		sum = sum + i;
	}
	while(i <= 9);
	printf("%d", sum);
	return 0;
}
```

#### 실습 5_19_g)
```c
#include <stdio.h>
int main() {
	int i = 0, sum = 0;
	do {
		if(i < 8) {
			i += 2;
			printf("%d + ", i);
		}
		else {
			i += 2;
			printf("%d = ", i);
		}
		sum = sum + i;
	}
	while(i <= 8);
	printf("%d", sum);
	return 0;
}
```

#### 실습 5_20
```c
#include <stdio.h>
int main() {
	int i, sum = 0;
	printf("점수?\n");
	do {
		scanf("%d", &i);
		sum = sum + i;
	} while(i != 999);
	printf("합 = %d", sum-999);
	return 0;
} 
```

#### 예제 5_01 a)
```c
#include <stdio.h>
int main() {
	int i = 1;
	for(i = 1; i <= 5; i++) {
		if(i == 2)
			continue;
		printf("%2d", i);
	}
	return 0;
}
```

#### 예제 5_01 b)
```c
#include <stdio.h>
int main() {
	int i = 1;
	for(i = 1; i <= 5; i++) {
		if(i == 2)
			break;
		printf("%2d", i);
	}
	return 0;
}
```

### 5) continue 문

continue 문 뒷 부분은 무시하고 반복문의 조건으로 제어가 옮겨진다.

#### 실습 5_21
```c
#include <stdio.h>
int main() {
	int i = 1;
	for(i = 1; i <= 10; i++) {
		if(i%3 == 0)
		continue;
		printf("%5d", i);
	}
	return 0;
}
```

### 6) break 문

반복문을 빠져나온다. 만약 다중 반복문인 경우 가장 가까운 반복문 하나만 빠져나온다.

#### 실습 5_22
```c
#include <stdio.h>
int main() {
	int i;
	while(1) {
		printf("id = ");
		scanf("%d", &i);
		if(i == -1)
		break;
	}
	return 0;
} 
```

#### 실습 5_23
```c
#include <stdio.h>
int main() {
	int i, sum = 0;
	while(1) {
		scanf("%d", &i);
		if(i == -999)
		break;
		sum = sum + i;
	}
	printf("합 = %d", sum);
	return 0;
} 
```

#### 실습 5_24
```c
#include <stdio.h>
int main() {
	int i = 0, sum = 0;
	while(1) {
		i++;
		sum = sum + i;
		if(i == 100) break;
	}
	printf("%d", sum);
	return 0;
}
```

#### 실습 5_25
```c
#include <stdio.h>
int main() {
	int i = 0, sum = 0;
	while(1) {
		i += 2;
		printf("%3d", i); 
		sum = sum + i;
		if(i == 10) break;
	}
	printf("%3d", sum);
	return 0;
}
```

#### 실습 5_26
```c
#include <stdio.h>
int main() {
	int a = 0;
	int b = 0;
	while(1) {
		b = 0;
		while(1) {
			b++;
			printf("%4d", 10*a + b);
			if(b == 10) break;
		}
		a++;
		printf("\n");
		if(a == 5) break;
	}
	return 0;
}
```

#### 실습 5_27_a)
```c
#include <stdio.h>
int main() {
	int a = 0, b = 0;
	while(1) {
		b = 0;
		while(1) {
			b++;
			printf("* ");
			if(b > 4) break;
		}
		a++;
		printf("\n");
		if(a == 5) break;
	}
	return 0;
} 
```

#### 실습 5_27_b)
```c
#include <stdio.h>
int main(){
	int a, b, c, d;
	for(a = 0; a <= 4; a++) {
		for(b = 0; b <= a; b++) {		
			printf("* ");
		}	
		for(c = 5; c >= a; c--) {
			printf("  ");
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_27_c)
```c
#include <stdio.h>
int main() {
	int a,b,c,d;
	for(a = 1; a <= 5; a++) {
		for(b = 5; b >= a; b--) {		
			printf("* ");
		}	
		for(c = 1; c <= a; c++) {
			printf("  ");
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_27_d)
```c
#include <stdio.h>
int main() {
	int a, b, c, d;
	for(a = 0; a <= 4; a++) {
		for(b = 0; b < a; b++) {		
			printf("  ");
		}	
		for(c = 4; c >= a; c--) {
			printf("* ");
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_27_e)
```c
#include <stdio.h>
int main() {
	int a, b, c, d;
	for(a = 1; a <= 5; a++) {
		for(b = 4; b >= a; b--) {	
			printf("  ");
		}	
		for(c = 1; c <= a; c++) {
			printf("* ");
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_27_f)
```c
#include <stdio.h>
int main() {
	int a, b, c, d;
	for(a = 1; a <= 5; a++) {
		for(b = 5; b > a; b--){	
			printf("  ");
		}
		for(c = 1; c <= a; c++) {
			printf("* ");
		}		
		for(d = 1; d < a; d++) {
			printf("* ");
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_28
```c
#include <stdio.h>
int main() {
	int i = 0, sum = 0;
	while(sum < 2000) {
		sum += i += 1;
	}
	printf("n = %d\nsum = %d", i, sum);
	return 0;
}
```

#### 실습 5_29
```c
#include <stdio.h>
int main() {
	int a, i;
	printf("몇단?");
	scanf("%d", &a);
	for(i = 1; i < 10; i++) {
		printf("%d * %d = %3d\n", a, i, a*i);
	}
	return 0;
} 
```

#### 실습 5_30
```c
#include <stdio.h>
int main() {
	int i, j;
	for(i = 2; i < 10; i++) {
		for(j=1; j<10; j++) {
			printf("%d * %d = %3d\n", i, j, i*j);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 5_31
```c
#include <stdio.h>
int main(){
	int i, j;
	printf("1)\n");
	for(i = 0; i < 5; i++) {
		for(j = 0; j < 5; j++) {
			printf("%3d ", i*5 + j + 1);
		}
		printf("\n");
	}
	printf("\n2)\n");
	for(i = 0; i < 5; i++) {
		for(j = 0; j < 5; j++) {
			if(i%2 == 0) printf("%3d ", i*5 + j + 1);
			else printf("%3d ", i*5 + 5 - j);
		}
		printf("\n");
	}
	printf("\n3)\n");
	for(i = 0; i < 5; i++) {
		for(j = 0; j < 5; j++) {
			printf("%3d ", i + j*5 + 1);
		}
		printf("\n");
	}
}
```
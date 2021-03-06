---
title: "6. 배열"
date: 2020-03-25T14:44:34Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---

같은 형식의 여러 데이터를 연속된 메모리 공간에 저장하여 사용하는 자료들의 집합

- 종류 : 1차원 배열, 2차원 배열 등

## 01 1차원 배열

첨자가 하나인 직선형의 배열

#### 형식 
`데이터형 배열명[첨자];`
####  구조
|배열명|첨자|배열|
|:---:|:---:|:---:|
|a|0|a[0]|
||1|a[1]|
||2|a[2]|
||3|a[3]|
||4|a[4]|
||5|a[5]|
||6|a[6]|
||7|a[7]|
||8|a[8]|

#### 배열 선언 예
1. `int a[5];`
2. `int b[] = [10. 20, 30, 40, 50];`
  
#### 배열의 초기화
배열 선언 후 초기값을 할당하는 방법과 배열 선언과 동시에 초기값을 할당하는 방법이 있다.
1. 배열을 선언한 후 초기값을 할당하는 방법
	`int a[5];`
	`a[0] = 10; a[1] = 20; a[2] = 30; a[3] = 40; a[4] = 50;`
2. 배열 선언과 동시에 초기값을 할당하는 방법
	`int b[5] = {10, 20, 30, 40, 50};`
	`int b[5] = {10, 20, 30, }; // b[4], b[5]는 0으로 초기화`
	`int b[5] = {10, 20, 30, 40, 50, 60, 70}; // 에러 발생`

#### 예제 6_01
```c
#include <stdio.h>
int main() {
	int i, a[5];
	a[0] = 3;
	a[1] = 7;
	a[2] = 2;
	a[3] = 1;
	a[4] = 6;
	printf("%d %d", a[2], a[4]);
	return 0;
}
```
  
#### 예제 6_02
```c
#include <stdio.h>
int main() {
	int i, a[5] = {1, 7, 5, 15, 12};
	for(i = 0; i < 5; i++)
		printf("%5d", a[i]);
	return 0;
} 
```

#### 실습 6_01
```c
#include <stdio.h>
int main() {
	int i, a[5] = {5, 7, 3, 6, 9}, s = 0;
	for(i = 0; i < 5; i++) {
		printf("%3d", a[i]);
		s += a[i];
	}
	printf("\n");
	for(i = 0; i < 5; i++) printf("%3d", a[4 - i]);
	printf("\n 합 : %d", s);
	return 0;
}
```

#### 실습 6_02
```c
#include <stdio.h>
int main() {
	int i, max =- 2147483647, a;
	printf("데이터 : ");
	for(i = 0; i < 10; i++) {
		scanf("%d", &a);
		if(max < a) max = a;
	}
	printf("최대값 : %d", max);
	return 0;
}
```

#### 실습 6_03
```c
#include <stdio.h>
int main() {
	int i, n[3], k[3], e[3], m[3], t[3];
	double ave[3];
	printf("학번, 국어, 영어, 수학 점수 입력(3명)\n");
	for(i = 0; i < 3; i++) {
		scanf("%d %d %d %d", &n[i], &k[i], &e[i], &m[i]);
		t[i] = k[i] + e[i] + m[i];
	}
	printf("%10s %10s %10s %10s %10s %10s\n\n", "번호", "국어", "영어", "수학", "총점", "평균");
	for(i = 0; i < 3; i++) {
		ave[i] = t[i]/3.0;
		printf("%10d %10d %10d %10d %10d %10.2f\n", n[i], k[i], e[i], m[i], t[i], ave[i]);
	}
	return 0;
}
```
  
#### 실습 6_04
```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
int main() {
	int i, j, r, a[10], b[10], c = 0;
	srand((unsigned)time(NULL));
	printf("입력 : ");
	for(i = 0; i < 6; i++) scanf("%d", &a[i]);
	printf("출력 : ");
	for(i = 0; i < 6; i++) {
		r = rand()%45 + 1;
		printf("%3d", r);
		for(j = 0; j < 6; j++) {
			if(a[j] == r) b[c++] = r;
		}
	}
	printf("\n일치 : ");
	for(i = 0; i < c; i++) printf("%3d", b[i]);
	return 0;
}
```

## 02 2차원 배열

첨자가 두개인 행령형의 배열
#### 형식
`데이터형 배열명[첨자1, 첨자2];`

#### 구조
|배열명|첨자|배열||
|:---:|:---:|:---:|:---:|
|a||0|1|
||0|a[0][0]|a[1][0]|
||1|a[0][1]|a[1][1]|
||2|a[0][2]|a[1][2]|
||3|a[0][3]|a[1][3]|


2차원 배열을 처리하기 위해서는 보통 이중 for 문을 사용한다.  
  
#### 2차원 배열의 선언과 초기화
1. `int a[2,3];`
2. `int b[][3] = {{1, 2, 3}, {4, 5, 6}};`

#### 실습 6_05
```c
#include <stdio.h>
int main() {
	int i, j;
	int a[3][4]={{1, 2, 3, 4}, {5, 6, 7, 8}, {9, 10, 11, 12}};
	int b[3][4]={{11, 12, 13, 14}, {15, 16, 17, 18}, {19, 20, 21, 22}};
	printf("두 배열의 합 c\n");
	for(i = 0; i < 3; i++) {
		for(j = 0; j < 4; j++) {
			printf("%5d", a[i][j] + b[i][j]);
		}
		printf("\n");
	}
	return 0;
}
```

#### 실습 6_06
```c
#include <stdio.h>
int main() {
	int i, j, c=0, a[3][4], b[3][4];
	printf("배열 a\n");
	for(i = 0; i < 3; i++) {
		for(j = 0; j < 4; j++) {
			printf("%3d", ++c);
			a[i][j] = c;
			b[2-i][3-j] = c;
		}
		printf("\n");
	}
	printf("배열 b\n");
	for(i = 0; i < 3; i++) {
		for(j = 0; j < 4; j++) {
			printf("%3d", b[i][j]);
		}
		printf("\n");
	}
	return 0;
}
```

## 03 문자배열

### 1) 문자배열

문자열을 저장하기 위한 배열로 배열을 선언할 때는 char 형으로 지정하는 것을 제외하고는 숫자 배열과 같은 방법으로 선언하고 사용한다.

문자배열 출력시 제어문자는 `%s`를 사용하며, NULL문자(`\0`)를 만나면 문자열의 끝으로 생각한다. 그래서 문자 배열을 선언할 때는 문자열 + 1 만큼의 기억장소를 확보해야 한다.

#### 가) 문자 배열의 초기화 방법
1. `char a[7] = {p, r, o, g, r, a, m};`

|p|r|o|g|r|a|m|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|a[0]|a[1]|a[2]|a[3]|a[4]|a[5]|a[6]|

위와 같이 선언하고 `printf("%s", a};` 라고 출력해보자.

2. `char b[] = "program";`

|p|r|o|g|r|a|m|\0|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|b[0]|b[1]|b[2]|b[3]|b[4]|b[5]|b[6]|b[7]|

문자열 처리에서 가장 많이 사용하는 방법이다. 배열의 크기를 지정하지 않고 문자열을 지정한 경우로 맨 마지막에 NULL문자(`\0`)가 자동으로 추가된다. 그래서 배열의 크기는 8이다.

3. `char c[3][4] = {"abc", "1234", "xy"};`

여러 개의 문자열을 하나의 문자 배열에 기억시키고자 한때 2차원 배열을 선언해야 한다.

#### 실습 6_07
```c
#include <stdio.h>
int main() {
	int i, j;
	char name[3][16] = {" 김나영 ", " 김선희 ", " 이미영 "};
	for(i = 0; i < 3; i++) {
		printf("%15s", name[i]);
	}
	return 0;
}
```

#### 실습 6_08
```c
#include <stdio.h>
int main() {
	int i;
	char irum[5][20];
	printf("5명의 이름을 입력하세요\n");
	for(i = 0; i < 5; i++) {
		scanf("%s", &irum[i]);
	}
	printf("당신이 입력한 5명의 이름 = ");
	for(i = 0; i < 5; i++) {
		printf("%7s", &irum[i]);
	}
	return 0;
} 
```

#### 실습 6_09
```c
#include <stdio.h>
int main() {
	int i, j;
	int prime[105] = {0, };
	for(i = 2; i < 100; i++) {
		if(prime[i] == 0) {
			j = i;
			while(j < 101) {
				prime[j] = 1;
				j += i;
			}
			printf("%3d", i);
		}
	}
	return 0;
}
```

#### 실습 6_10
```c
#include <stdio.h>
#include <string.h>
int main() {
    char c_in[30];
    int k, i;
    printf("문자열 : ");
    scanf("%s", c_in); 
    k=strlen(c_in);
    for(i = 0; i < k; i++) {
             if(c_in[i] > 90)
			 	c_in -= 32;
             else
			 	c_in += 32;
    }
    printf("출  력 : %s", c_in);
    return 0;
}
```

#### 실습 6_11
```c
#include <stdio.h>
#include <string.h>
int main() {
    char str[30];
    int l, i;
    printf("문자열 : "); 
    scanf("%s", str);
    l = strlen(str);
    printf("길이 : %d\n출력 : ", l); 
    for(i = 0; i < l; i++) printf("%c", str[l - 1 - i]);
    return 0;
} 
```

#### 실습 6_12
```c
#include <stdio.h>
int f[100];
int fib(int a) {
    if(a == 0) return 0;
    else if(f[a] == 0) f[a] = fib(a - 1) + fib(a - 2);
    return f[a];
} 
int main() {
    int i;
    f[1] = 1; f[2] = 1;
    fib(15);
    for(i = 1; i <= 15; i++) printf("%4d", f[i]);
    return 0;
}
```

#### 심화 6_01
```c
#include <stdio.h>
int main() {
	int answer[11] = {1, 2, 3, 4, 1, 2, 3, 4, 1, 2};
    int ans_sco[11] = {10, 10, 10, 10, 10, 10, 10, 10, 10, 10};
    int stu[5][11] = {{0, }, {0, }, {0, }, {0, }, {0, }};
    char corr[5][11];
    int score[5] = {0, };
    int rank[5];
    int soowoo[5];
    int name[5][20];
    int i, j, k;
    for(i = 0; i < 5; i++) {
	    k = i + 1;
        scanf("%s", name[i]);
        for(j = 0; j < 10; j++) {
	        scanf("%d", &stu[i][j]);
            if(stu[i][j] != answer[j]) corr[i][j] = 'X';
            else {
	            corr[i][j] = 'O';
                score[i] += ans_sco[j];
            }
        }
        for(j = 0; j < i; j++) {
	        if(score[i] > score[j]) rank[j]++;
            if(score[i] < score[j]) continue;
            k--;
        }
        if(score[i] > 89) soowoo[i] = 0;
        else if(score[i] > 79) soowoo[i] = 1;
        else if(score[i] > 69) soowoo[i] = 2;
        else if(score[i] > 59) soowoo[i] = 3;
        else soowoo[i] = 4; 
        rank[i] = k;
    }
    printf("채점표\n");
    printf("----------------------------------------\n");
    printf("   이름  1 2 3 4 5 6 7 8 9 10   점수\n");
    printf("----------------------------------------\n");
    for(i = 0; i < 5; i++) {
        printf("%7s", name[i]);
        for(j = 0; j < 10; j++) printf(" %c", corr[i][j]);
        printf("%8d \n", score[i]);
    }
    printf("----------------------------------------\n");
    return 0;
}
```

#### 심화 6_02
```c
#include <stdio.h>
int main() {
    int answer[11] = {1, 2, 3, 4, 1, 2, 3, 4, 1, 2};
    int ans_sco[11] = {10, 10, 10, 10, 10, 10, 10, 10, 10, 10};
    int stu[5][11] = {{0, }, {0, }, {0, }, {0, }, {0, }};
    char corr[5][11];
    int score[5] = {0, };
    int rank[5];
    int soowoo[5];
    char swmyg[5][5] = {"수" ,"우", "미", "양", "가"};
    int name[5][20];
    int i, j, k;
    for(i = 0; i < 5; i++) {
	    k = i + 1;
        scanf("%s", name[i]);
        for(j = 0; j < 10; j++) {
	        scanf("%d", &stu[i][j]);
            if(stu[i][j] != answer[j]) corr[i][j] = 'X';
            else {
	            corr[i][j] = 'O';
                score[i] += ans_sco[j];
            }
        }
        for(j = 0; j < i; j++) {
	        if(score[i] > score[j]) rank[j]++;
            if(score[i] < score[j]) continue;
            k--;
        }
        if(score[i] > 89) soowoo[i] = 0;
        else if(score[i] > 79) soowoo[i] = 1;
         else if(score[i] > 69) soowoo[i] = 2;
        else if(score[i] > 59) soowoo[i] = 3;
        else soowoo[i] = 4; 
        rank[i] = k;
    }
    printf("채점표\n");
    printf("----------------------------------------------\n");
    printf("   이름  1 2 3 4 5 6 7 8 9 10   점수   판정  \n");
    printf("----------------------------------------------\n");
    for(i = 0; i < 5; i++) {
        printf("%7s", name[i]);
        for(j = 0; j < 10; j++) printf(" %c", corr[i][j]);
        printf("%8d %5s \n", score[i], swmyg[soowoo[i]]);
    }
    printf("----------------------------------------------\n");
    return 0;
}
```  

#### 심화 6_03
```c
#include <stdio.h>
int main() {
    int answer[11] = {1, 2, 3, 4, 1, 2, 3, 4, 1, 2};
    int ans_sco[11] = {10, 10, 10, 10, 10, 10, 10, 10, 10, 10};
    int stu[5][11] = {{0, }, {0, }, {0, }, {0, }, {0, }};
    char corr[5][11];
    int score[5] = {0, };
    int rank[5];
    int soowoo[5];
    char swmyg[5][5] = {"수" ,"우", "미", "양", "가"};
    int name[5][20];
    int i, j, k;
    for(i = 0; i < 5; i++) {
        k = i + 1;
        scanf("%s", name[i]);
        for(j = 0; j < 10; j++) {
	        scanf("%d", &stu[i][j]);
            if(stu[i][j] != answer[j]) corr[i][j] = 'X';
            else{
	            corr[i][j] = 'O';
                score[i] += ans_sco[j];
            }
        }
        for(j = 0; j < i; j++) {
	        if(score[i] > score[j]) rank[j]++;
            if(score[i] < score[j]) continue;
            k--;
        }
        if(score[i] > 89) soowoo[i] = 0;
        else if(score[i] > 79) soowoo[i] = 1;
        lse if(score[i] > 69) soowoo[i] = 2;
        else if(score[i] > 59) soowoo[i] = 3;
        else soowoo[i] = 4; 
        rank[i] = k;
    }
    printf("채점표\n");
    printf("-----------------------------------------------------\n");
    printf("   이름  1 2 3 4 5 6 7 8 9 10   점수   판정   석차 \n");
    printf("-----------------------------------------------------\n");
    for(i = 0; i < 5; i++) {
        printf("%7s", name[i]);
        for(j = 0; j < 10; j++) printf(" %c", corr[i][j]);
        printf("%8d %5s %5d\n", score[i], swmyg[soowoo[i]], rank[i]);
    }
    printf("-----------------------------------------------------\n");
    return 0;
}
```

#### 심화 6_05
```c
#include <stdio.h>
int main(){
    int answer[11] = {1, 2, 3, 4, 1, 2, 3, 4, 1, 2};
    int ans_sco[11] = {9, 11, 10, 6, 13, 5, 8, 7, 12, 9};
    int stu[5][11] = {{0, }, {0, }, {0, }, {0, }, {0, }};
    char corr[5][11];
    int score[5] = {0, };
    int rank[5];
    int soowoo[5];
    char swmyg[5][5] = {"수" ,"우", "미", "양", "가"};
    int name[5][20];
    int i, j, k;
    for(i = 0; i < 5; i++) {
        k = i + 1;
        scanf("%s", name[i]);
        for(j = 0; j < 10; j++) {
	        scanf("%d", &stu[i][j]);
            if(stu[i][j] != answer[j]) corr[i][j] = 'X';
            else {
	            corr[i][j] = 'O';
                score[i] += ans_sco[j];
            }
        }
        for(j = 0; j < i; j++) {
	        if(score[i] > score[j]) rank[j]++;
            if(score[i] < score[j]) continue;
            k--;
        }
        if(score[i] > 89) soowoo[i] = 0;
        else if(score[i] > 79) soowoo[i] = 1;
        else if(score[i] > 69) soowoo[i] = 2;
        else if(score[i] > 59) soowoo[i] = 3;
        else soowoo[i] = 4; 
        rank[i] = k;
    }
    printf("채점표\n");
    printf("-----------------------------------------------------\n");
    printf("   이름  1 2 3 4 5 6 7 8 9 10   점수   판정   석차 \n");
    printf("-----------------------------------------------------\n");
    for(i = 0; i < 5; i++) {
        printf("%7s", name[i]);
        for(j = 0; j < 10; j++) printf(" %c", corr[i][j]);
        printf("%8d %5s %5d\n", score[i], swmyg[soowoo[i]], rank[i]);
    }
    printf("-----------------------------------------------------\n");
    return 0;
}
```
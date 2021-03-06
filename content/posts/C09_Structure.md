---
title: "9. 구조체"
date: 2020-03-26T14:48:48Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


#### 구조체란?
책 대여점에서 책 재고관리를 하기 위한 프로그램을 작성한다고 생각해보자, 각각의 책에 대하여 분류번호, 책 제목, 저자, 구입가격, 출판일자, 대여 횟수 등 수많은 정보가 필요하게 된다. 그러나 각각의 데이터들은 데이터형이 같지 않아 서로 다른 데이터형으로 정의하고 따로따로 배열로 저장할 수 밖에 없다. 하지만 하나의 배열을 사용하여 배열의 각 원소가 하나의 책에 대한 모든 정보를 갖게 되면 재고관리가 쉬어질 것이다.

구조체는 서로 다른 데이터형의 자료들을 묶음으로 처리하고자 할 때 사용하는 자료 형태이며, 구조체에서 사용되는 각각의 구성원을 구조체 구성원이라 한다.

일반적인 데이터 구조와 C언어에서의 데이터 구조를 살펴보면 일반적인 데이터 구조의 레코드에 해당되는 것이 구조체이며, 필드에 해당되는 것이 구조체의 구성원이다.

구조체를 사용하기 위해서는 첫째, 구조체의형식을 정의하고, 둘째, 구조체의 변수를 선언해야 하며, 셋째, 구조체 변수의 참조과정을 거처야 한다.

## 01 구조체와 구조체 변수

### 구조체의 형식정의

구조체는 다음과 같은 형식으로 선언한다,

#### 일반형식
```c
struct 구조체_태그 {
	구조체_구성원1;
	구조체_구성원2;
	...
	구조체_구성원n;
};
```

#### 보기 1
|분류번호|책 제목|저자|구입가격|출판일자|대여횟수|
|:---:|:---:|:---:|:---:|:---:|:---:|
|정수형|문자(25)|문자(25)|정수형|정수형|실수형|
```c
struct book {
	int number;
	char title[25];
	char writer[25];
	int price;
	int date;
	float lendnum;
};
```

여기서, 구조체 태그는 구조체의 이름을 말하며, 변수명을 만드는 규칙에 따라 만든다.

### 구조체 변수의 선언

형식이 정의된 구조체를 사용하기 위해 변수를 선언하는 과정으로 일반형식은 다음과 같다.

#### 일반형식
```c
struct 구조체_태그 변수1[변수2, ... 변수n];
```

#### 보기 2
```c
struct book man1;
```

여기서, 구조체_태그는 앞에서 설정한 구조체의 이름을 말하며, 변수는 구조체를 사용할 변수의 이름을 말한다.

1. 구조체 변수선언은 구조체 형식 정의와 동시에 선언해 주어도 된다.

#### 보기 3
```c
struct book {
	int number;
	char title[25];
	char write[25];
	int price;
	int date;
	float lendnum;
} man1;
```

2. 구조체 변수선언을 한 후 변수의 초기값을 선언 할 수도 있으며 초기값 선언은 배열의 초기 값 선언과 같은 방법으로 선언한다.

#### 보기 4
```c
struct book {
	int number;
	char title[25];
	char writer[25];
	int price;
	int date;
	float lendnum;
} man1 = { 2509, "황소와 도깨비", "이상", 6000, 19971130, 57};
```

### 구조체 변수의 참조

구조체 형식 정의와 구조체 변수 선언이 끝난 후 구조체 변수에 들어있는 각각의 구성원을 참조한다.

#### 일반형식

`구조체변수명.구조체구성원명`

#### 보기5
```c
man1.number = 2509;
```
  
#### 실습 9_01
```c
#include <stdio.h>
struct Car {
	int num;
	double gas;
};
int main() {
	struct Car car1;
	car1.num = 1234;
	car1.gas = 25.5;
	printf("자동차 번호는 %d : 연료량은 %f임니다.\n", car1.num, car1.gas);
	return 0;
}
```
#### 실습 9_02
```c
#include <stdio.h>
struct Person {
	int age;
	char gender;
	char name[15];
};
int main() {
	struct Person JB = { 18, 'M', "장동건"};
	printf("나이: %d세  성별: %c 이름: %s", JB.age, JB.gender, JB.name);
	return 0; 
}
```
#### 실습 9_03
```c
#include <stdio.h>
struct Person {
	int age;
	char gender;
	char name[15];
} JB = { 18, 'M', "장동건"};
int main(){
	printf("나이: %d세 성별: %c 이름: %s", JB.age, JB.gender, JB.name);
	return 0;
}
```
#### 실습 9_04
```c
#include <stdio.h>
struct Person {
	int number;
	char name[15];
	int age;
	char phone[15];
};
int main() {
	struct Person km = {1,"kim minsu", 15, "02-9090-0001"};
	printf("순서  이 름      나이   전화번호  \n");
	printf("  %d  %s    %d   %s      ", km.number, km.name, km.age, km.phone);
	return 0;
}
```
#### 실습 9_05
```c
#include <stdio.h>
struct student {
	int bunho;
	char name[15];
	int kuk;
	int eng;
	int tot;
	float avg;
};
int main() {
	struct student stu1;
	printf("학생 자료를 입력하세요\n");
	printf("학생번호: ");
	scanf("%d", &stu1.bunho);
	printf("학생이름: ");
	scanf("%s", &stu1.name);
	printf("국어점수: ");
	scanf("%d", &stu1.kuk);
	printf("영어점수: ");
	scanf("%d", &stu1.eng);
	stu1.tot = stu1.kuk + stu1.eng;
	stu1.avg = stu1.tot/2.0;
	printf("\n ** 입력된 학생 자료입니다. **\n");
	printf("%d %s %d %d %d %.2f", stu1.bunho, stu1.name, stu1.kuk, stu1.eng, stu1.tot, stu1.avg);
	return 0;
}
```
  

## 02 구조체 배열

친구들의 주소록을 만들 때 친구가 많아 구조체를 이용하더라도 프로그램이 복잡한 경우가 있다. 이와 같이 복잡한 경우 단순한 구조체가 아닌 구조체 배열을 활용하면 동일한 구조를 가진 대량의 레코드를 처리하는데 효과적이다. 구조체 배열은 구조체를 정의 한 후 구조체 변수에 배열을 사용하는 것을 의미한다.

#### 구조체 배열의 선언

구조체 형식이 정의된 후 구조체 변수를 선언할 때 배열 형태로 선언한다.

#### 일반형식
```c
struct 구조체_태그 배열명[원소의_개수];
```

#### 보기 6
```c
string sinsang student1[5];
```
#### 보기 7
```c
struct sinsang {
	int bunho;
	char inum[10];
	int nai;
	char telephone[15];
} student1[5];
```

#### 구조체 배열의 참조

구조체 형식 정의와 구조체 배열 선언이 끝난 후 구조체 배열에 들어있는 각각의 구성원을 참조한다.

#### 일반형식

`구조체_배열명[원소번호].구조체_구성원명;`


#### 보기 8
```c
student1[0].bunho = 1;
```
  

#### 실습 9_06
```c
#include <stdio.h>
struct sinsang {
	int bunho;
	char name[15];
	int nai;
	char telephone[15];
}; 
int main() {
	struct sinsang stud[3] = {
		{1,"박수민",17,"02-123-4567"},
		{2,"이주현",16,"02-345-6789"},
		{3,"정찬호",17,"02-678-1234"}
	};
	int a;
	printf("순서 이 름  나이 전화번호\n");
	printf("--------------------------\n");
	for(a = 0; a < 3; a++)
		printf("  %2d   %-10s %3d  %-15s\n", stud[a].bunho,stud[a].name, stud[a].nai, stud[a].telephone);
		return 0;
	
}
```
#### 실습 9_07
```c
#include <stdio.h>
struct sinsang {
	int num;
	char gender;
	char name[20];
}; 
int main() {
	struct sinsang stud[20];
	int a;
	int b;
	int count=0;
	for(a = 0 ; ; a++) {
		printf("학번: ");
		scanf("%d", &stud[a].num); 
		printf("이름: ");
		scanf("%s", stud[a].name);
		printf("성별(M/F): ");
		scanf("%c", &stud[a].gender);
		printf("계속 입력하시려면 1, 아니면 2를 누르세요 : ");
		scanf("%d", &b);
		count += 1;
		if(b == 2)
			break;	 
	} 
	printf("학번  성별   이름\n");
	printf("--------------------------\n");
	for(a = 0; a < count; a++)
		printf(" %d  %c  %-10s \n", stud[a].num, stud[a].gender, stud[a].name);
		return 0;
} 
```

## 03 구조체 포인터

배열과 포인터가 서로 밀접하게 쓰인 것처럼 구조체에서도 구조적 배열과 구조체 포인터는 상호 밀접하게 쓰이고 있다.

#### 구조체 포인터 변수의 선언

구조체 변수를 선언할 때 포인터 형태로 선언한다. 구조체 포인터변수는 초기값을 배정하지 못하므로 초기화시 구조체 변수 또는 구조체 배열로 초기화한 후 사용한다.

#### 일반형식
```c
struct 구조체_태그_포인터;
```

#### 보기 9
```c
struct sinsang *sw;
```

#### 보기 10
```c
struct sinsang {
	int bunho;
	char irum[20];
	int nai;
	char telephone[15];
};
struct sinsang sawon1[3] = {
	{1, "홍길동", 19, "02-123-4567"},
	{2, "김갑돌", 25, "02-234-5678"},
	{3, "이미자", 30, "02-345-6789'}
};
struct sinsang *sw;
sw = sawon1;
```

#### 구조체 포인터의 참조

구조체 포인터에 들어있는 구성원을 참조한다.

#### 일반형식

`구조체_포인터->구조체_구성원명;`

#### 보기 11
```c
(sw + 0) -> bunho = 1;
```

#### 실습 9_08
```c
#include <stdio.h>
struct sinsang {
	int bunho;
	char name[10];
	int nai;
	char telephone[15];
}; 
int main() {
	struct sinsang *sa;
	struct sinsang sawon1[3] = {
		{1,"홍길동",19,"02-123-4567"},
		{2,"김갑돌",25,"02-234-5678"},
		{3,"이미자",30,"02-345-6789"}
	};
	int i = 0;
	sa = sawon1; 
	printf("번호  이 름  나이 전화번호\n");
	printf("--------------------------\n");
	for(i = 0; i < 3; i++, ++sa)
		printf("\n%2d   %-10s %3d  %-15s", sa->bunho ,sa->name, sa->nai, sa->telephone);
		return 0;
	
}
```

## 04 구조체와 함수

구조체를 일반 변수와 같이 함수에 값 또는 번지로서 전달할 수 있다.

#### 구조체 구성원의 값 전달

구조체 구성원의 값을 함수에 전달하는 것이다. 이때, 구조체의 내용 변경은 호출된 함수 내에서만 이루어지고 호출한 함수 환경에 있는 구조체에는 영향을 주지 않는다.

#### 일반형식
```c
type 함수명(가인수);
int main() {
	:
	함수명(구조체변수명.구조체구성원)
	:
}
type 함수명(가인수) {
	:
	함수의 본체
	:
	return(되돌리는 값);
}
```

#### 보기 12
```c
void fun(int a);
int main() {
	:
	fun(sawon1.number)
	:
}
void fun(int a) {
	함수의 본체
}
```

#### 실습 9_09
```c
#include <stdio.h>
#include <conio.h>
struct sinsang {
	int bunho;
	char name[10];
	int nai;
	char telephone[15];
};
void func1(int kk, char nn[], int ss, char pp[]);
int main() {
	static struct sinsang sawon1 = {1,"홍길동",19,"02-123-4567"};
	func1(sawon1.bunho, sawon1.name, sawon1.nai, sawon1.telephone);
	printf("\n<<main 함수 에서 출력>>");
	printf("\n번호 이름   나이  전화번호");
	printf("\n--------------------------");
	printf("\n%2d  %-10s %3d %-15s", sawon1.bunho, sawon1.name, sawon1.nai, sawon1.telephone);
	return 0;
}
void func1(int kk,char nn[], int ss, char pp[]){
	kk = kk + 1;
	ss = ss + 1;
	printf("\n<<func1 함수에서의 출력>>");
	printf("\n번호  이름   나이  전화번호");
	printf("\n------------------------------");
	printf("\n%2d  %-10s %3d %-15s\n", kk, nn, ss, pp); 
}
```

#### 구조체 구성원의 번지 전달

구조체 구성원이 기억되어 있는 번지로 전달하는 것으로 구조체 구성원의 이름 앞에 `&`연산자를 붙인다. 이때 호출된 함수 내에서 변경된 구조체 구성원의 값은 호출함수 환경에 있는 구조체에도 영향을 준다.

#### 일반형식
```c
type 함수명(가인수)
int main() {
	:
	함수명(&구조체변수명.구조체구성원)
	:
}
type 함수명(가인수) {
	:
	함수의 본체
	:
	return(되돌리는 값);
}
```

#### 보기 13
```c
void func(int *a);
int main() {
	:
	func(&sawon1.number)
	:
}
void func(int *a) { 함수의 본체 }
```

- 여기서 가인수는 `main`함수에서 넘겨준 주소값을 받을 수 있는 변수 형태이어야 한다.

#### 실습 9_10
```c
#include <stdio.h>
#include <conio.h>
struct sinsang {
	int bunho;
	char name[10];
	int nai;
	char telephone[15];
};
void func1(int *kk,char nn[], int *ss, char pp[]);
int main() {
	static struct sinsang sawon1 = {1, "홍길동", 19, "02-123-4567"};
	func1(&sawon1.bunho, sawon1.name, &sawon1.nai, sawon1.telephone);
	printf("\n<<main 함수 에서 출력>>");
	printf("\n번호 이름   나이  전화번호");
	printf("\n--------------------------");
	printf("\n%2d  %-10s %3d %-15s",sawon1.bunho, sawon1.name, sawon1.nai, sawon1.telephone);
	return 0;
}
void func1(int *kk,char nn[], int *ss, char pp[]) {
	(*kk)++;
	(*ss)++;
	printf("\n<<func1 함수에서의 출력>>");
	printf("\n번호  이름   나이  전화번호");
	printf("\n------------------------------");
	printf("\n%2d  %-10s %3d %-15s\n", kk, nn, ss, pp); 
}
```

#### 구조체 전달

구조체 전체를 함수에 전달하는 것으로 구조체 변수의 값 또는 주소를 전달 인수로 사용한다. 주의해야 할 것은 실 매개 변수와 형식 매개 변수의 형은 반드시 일치시켜야 한다.

### 1.  구조체 변수 값 전달

#### 일반형식
```c
type 함수명(가인수);
int main() {
	:
	함수명(구조체변수명)
	:
}
type 함수명(가인수) {
	:
	함수의 본체
	:
	return(되돌리는 값);
}
```

#### 보기 14
```c
void func(struct sinsang sw1);
int main() {
	:
	func(sawon1)
	:
}
void func(struct sinsang sw1) {
	:
	함수의 본체
}
```

- 호출한 함수의 데이터는 호출된 함수에 의해 영향을 받지 않는다.

### 2. 구조체 변수의 주소 값 전달

#### 일반형식
```c
type 함수명(가인수);
int main() {
	:
	함수명(&구조체변수명)
	:
}
type 함수명(가인수) {
	:
	함수의 본체
	:
	return(되돌리는 값);
}
```

#### 보기 15
```c
void func(struct sinsang *pp);
int main() {
	:
	func(&sawon1)
	:
}
void func(struct sinsang *pp) {
	:
	함수의 본체
}
```

- 여기서 가인수는 메인 함수에서 넘겨준 주소값을 받을 수 있는 변수 형태이어야 하며, 호출한 함수의 데이터는 호출된 함수에 의해 영향을 받는다.

#### 실습 9_11
```c
#include <stdio.h>
#include <conio.h>
struct sinsang {
	int bunho;
	char name[10];
	int nai;
	char telephone[15];
};
void func1(struct sinsang sw1);
void func2(struct sinsang *pp);
int main() {
	static struct sinsang sawon1 = {1,"홍길동",19,"02-123-4567"};
	func1(sawon1);
	printf("\n<<출력결과(1)>>");
	printf("\n번호 이름   나이  전화번호");
	printf("\n--------------------------");
	printf("\n%2d  %-10s %3d %-15s", sawon1.bunho, sawon1.name, sawon1.nai, sawon1.telephone);
	printf("\n"); 
	func2(&sawon1);
	printf("\n<<출력결과(2)>>");
	printf("\n번호 이름   나이  전화번호");
	printf("\n--------------------------");
	printf("\n%2d  %-10s %3d %-15s", sawon1.bunho, sawon1.name, sawon1.nai, sawon1.telephone);
	printf("\n");
	return 0;
}
void func1(struct sinsang sw1) {
	sw1.bunho += 5;
	printf("\n<<func1 함수에서의 출력>>");
	printf("\n번호  이름   나이  전화번호");
	printf("\n------------------------------");
	printf("\n%2d  %-10s %3d %-15s\n", sw1.bunho, sw1.name, sw1.nai, sw1.telephone); 
}
void func2(struct sinsang *pp) {
	pp->bunho += 10;
	printf("\n<<func2 함수에서의 출력>>");
	printf("\n번호  이름   나이  전화번호");
	printf("\n------------------------------");
	printf("\n%2d  %-10s %3d %-15s\n", pp->bunho, pp->name, pp->nai, pp->telephone); 
}
```

#### 실습 9_12
```c
#include <stdio.h>
struct data {
	int year;
	int month;
	int day;
}; 
int main() {
	struct data a = {2008, 3, 23};
	printf("오늘은 %d년 %d월 %d일 입니다.", a.year, a.month, a.day);
	return 0;
}
```

#### 실습 9_13
```c
#include <stdio.h>
struct student {
	int bunho;
	char name[15];
	int kuk;
	int eng;
	int mat; 
	int tot;
	float avg;
};
int main() {
	struct student stud[20];
	int a;
	int b;
	int count = 0;
	for(a = 0; ; a++) {
		printf("학번: ");
		scanf("%d", &stud[a].bunho);
		printf("이름: ");
		scanf("%s", &stud[a].name);
		printf("국어점수: ");
		scanf("%d", &stud[a].kuk);
		printf("영어점수: ");
		scanf("%d", &stud[a].eng);
		printf("수학점수: ");
		scanf("%d", &stud[a].mat); 
		printf("계속 입력하시려면 1, 아니면 2를 누르세요 : ");
		scanf("%d", &b);
		stud[a].tot = stud[a].kuk + stud[a].eng + stud[a].mat;
		stud[a].avg = stud[a].tot/3;
		count += 1;
		if(b == 2)
			break;	
	}
	printf("학번  이 름     국어  영어  수학  총점  평균\n");
	printf("---------------------------------------------\n");
	for(a = 0; a < count; a++)
		printf("  %d   %-10s %d   %d   %d   %d   %.f\n", stud[a].bunho, stud[a].name, stud[a].kuk, stud[a].eng, stud[a].mat, stud[a].tot, stud[a].avg);
		return 0;
	
}
```

#### 실습 9_14
```c
#include <stdio.h>
struct statement {
	int bunho; //구분 
	char telephone[15]; //전화번호 
	char name[15]; //이름 
	long int fee; //통화료 
	int tax; //세금 
	int tot; //합 
	int basic; //기본요금 
	int amount; //사용량 
	int alltot; //총합계 
}; 
int main() {
	struct statement person[100];
	int a;
	int b;
	int count = 0;
	for(a = 0; ; a++) {
		printf("구분: ");
		scanf("%d", &person[a].bunho);
		printf("전화번호: ");
		scanf("%s", &person[a].telephone);
		printf("이름: ");
		scanf("%s", &person[a].name);
		printf("사용량: ");
		scanf("%d", &person[a].amount);
		printf("계속 입력하시려면 1, 아니면 2를 누르세요 : ");
		scanf("%d", &b); 
		if(person[a].bunho == 1) {
			person[a].basic = 6000;
		}
		else if(person[a].bunho == 2) {
			person[a].basic = 4800;
		}
		else if(person[a].bunho == 3) {
			person[a].basic = 3000;
		}
		else{
			printf("ERROR");
		}
		person[a].fee = person[a].amount*12; //통화료는 1통화에 대하여 12원씩이다. 
		person[a].tot = person[a].basic + person[a].fee; //합은 기본요금과 통화료의 합 
		person[a].tax = person[a].tot*0.1; //세금은 기본요금과 통화료를 합한 금액의 10%를 부과한다. 
		person[a].alltot = person[a].tax + person[a].tot; //총합은 세금과 합의 합 
			count += 1;
			if(b == 2)
				break;		
	}		
	printf("<<전화 요금 명세서>>\n");
	printf("--------------------------------------------------\n");
	printf("구분  전화번호  이름  기본요금  통화료  세금 합계 \n");
	printf("--------------------------------------------------\n");
	for(a = 0; a < count; a++) {
	printf("  %d    %s   %-10s %d    %d   %d   %d\n", person[a].bunho, person[a].telephone, person[a].name, person[a].basic, person[a].fee, person[a].tax, person[a].alltot);}
	printf("--------------------------------------------------\n");
		return 0;
}
```
  

#### 실습 9_15
```c
#include <stdio.h>
struct Student {
	int num;
	char name[15];
	int korean;
	int english;
	int math;
} students[] = {
	{1101, "김수진", 90, 95, 88},
	{1102, "이숙희", 87, 90, 93},
	{1103, "최가람", 82, 89, 87}
};
int main() {
	int i;
	printf("학번 이 름 국어 영어 수학 총점 평균 \n");
	printf("------------------------------------------------------\n");
	for (i = 0; i < 3; i++) {
		struct Student *cur = &students[i];
		int tot = cur->korean + cur->english + cur->math;
		printf("%4d %6s %3d %3d %3d %4d %3g \n", cur->num, cur->name, cur->korean, cur->english, cur->math, tot, tot/3.);
	}
	return 0;
}
```

#### 실습 9_16
```c
#include <stdio.h> 
#define STDLEN 5 
#define SUBJ 4 
struct Student { 
	int num; 
	char name[15]; 
	int korean; 
	int english; 
	int math; 
	int computer; 
	int total; 
} students[] = {
	{1101, "홍길동", 100, 78, 96, 100, 0}, 
	{1102, "임꺽정", 98, 98, 93, 92, 0}, 
	{1103, "일지매", 85, 57, 86, 59, 0}, 
	{1104, "장보고", 76, 78, 77, 79, 0}, 
	{1105, "김삿갓", 67, 90, 88, 85, 0} 
}; 
int getrank(struct Student list[], int len, int idx); 
int main() { 
	int i; 
	int kortot = 0, engtot = 0, mathtot = 0, comptot = 0; 
	for (i = 0; i < STDLEN; i++) { 
		struct Student *cur = &students[i]; 
		cur->total = cur->korean + cur->english + cur->math + cur->computer; 
		kortot += cur->korean; 
		engtot += cur->english; 
		mathtot += cur->math; 
		comptot += cur->computer; 
	}

	printf("----------------------------------------------------------\n"); 
	printf("학번 이 름 국어 영어 수학 전산 총점 평균 석차 \n"); 
	printf("----------------------------------------------------------\n"); 
	for (i = 0; i < STDLEN; i++) { 
		struct Student *cur = &students[i]; 
		printf("%4d %6s %3d %3d %3d %3d %4d %4.1lf %3d\n", cur->num, cur->name, cur->korean, cur->english, cur->math, cur->computer, cur->total, (double)cur->total/SUBJ, getrank(students, STDLEN, i)); 
	} 
	printf("----------------------------------------------------------\n"); 
	printf(" 총 점 %3d %3d %3d %3d %4d\n", kortot, engtot, mathtot, comptot, cortot+engtot+mathtot+comptot); 
	printf(" 평 균 %3d %3d %3d %3d %4.1lf\n", kortot/STDLEN, engtot/STDLEN, mathtot/STDLEN, comptot/STDLEN, (kortot + engtot + mathtot + comptot)/((double)STDLEN*SUBJ)); 
	printf("----------------------------------------------------------\n"); 
	return 0; 
}
int getrank(struct Student list[], int len, int idx) { 
	int rank = 1; 
	int i; 
	for (i = 0; i < len; i++) { 
		if (i == idx) continue; 
		if (list[i].total > list[idx].total) rank++; 
	}
	return rank; 
} 
```

#### 실습 9_17
```c
#include <stdio.h> 
#include <string.h> 
#define DATA_LEN 4 
struct human { 
	char name[20]; 
	int age; 
	char gender; 
	char fruit[20]; 
}; 
struct human data[] = { 
	{"김성수", 15, 'M', "딸기"}, 
	{"박성애", 14, 'F', "복숭아"}, 
	{"이찬수", 16, 'M', "포도"}, 
	{"한경수", 16, 'M', "바나나"} 
}; 
int main() { 
	char finding[20]; 
	int i; 
	do { 
		printf("찾고자 하는 학생 이름은(끝낼때는 q)? "); 
		scanf("%s", finding); 
		if (strcmp(finding, "q") == 0) break; 
		for (i = 0; i < DATA_LEN; i++) { 
			if (strcmp(data[i].name, finding) == 0) { 
				break; 
			} 
		}
		if (i < DATA_LEN) printf("%s %d %s %s\n", data[i].name, data[i].age, data[i].gender == 'M' ? "남" : "여", data[i].fruit); 
		else printf("찾아내지 못함\n"); 
	} while (1); 
	return 0;
}
```
  

#### 실습 9_18
```c
#include <stdio.h> 
#define LISTMAX 100 
struct student { 
	int number; 
	char name[20]; 
	int age; 
} list[LISTMAX]; 
int main() { 
	int i; 
	int listlen = LISTMAX; 
	printf(" 학번 이름 나이를 입력하시오\n"); 
	for (i = 0; i < LISTMAX; i++) { 
		struct student input; 
		int check = scanf("%d", &input.number); 
		if (check == EOF) { 
			listlen = i; 
			break; 
		}
		scanf("%s %d", input.name, &input.age); 
		list[i] = input; 
	} 
	printf("\n < 출력 결과 >\n"); 
	printf(" 학번 이 름 나이\n"); 
	printf("---------------------\n"); 
	for (i = 0; i < listlen; i++) 
	printf(" %4d %6s %2d\n", list[i].number, list[i].name, list[i].age); 
	return 0; 
} 
```
  

#### 실습 9_19
```c
#include <stdio.h>

#include <string.h> 
#define DATALEN 5 
struct info { 
	char name[20]; 
	int age; 
	char address[50]; 
}; 
void show(struct info *list, int len); 
void sorting(struct info *list, int len); 
int main() { 
	struct info data[DATALEN] = { 
		{"홍길동", 18, "서울시 강북구"}, 
		{"김일동", 28, "대전광역시 동구"}, 
		{"이찬수", 21, "충북 청주시"}, 
		{"한경수", 33, "서울시 강남구"}, 
		{"박주형", 32, "광주광역시 중구"} 
	}; 
	printf(" < 초기 데이터 목록 > \n"); 
	show(data, DATALEN); 
	printf("\n"); 
	printf(" < 정렬 후 데이터 목록 > \n"); 
	sorting(data, DATALEN); 
	show(data, DATALEN); 
	return 0; 
}

void show(struct info *list, int len) { 
	struct info *i; 
	printf("이 름 나이 주 소\n"); 
	printf("---------------------------------\n"); 
	for (i = list; i < list+len; i++) 
	printf("%6s %2d %s\n", i->name, i->age, i->address); 
}

void sorting(struct info *list, int len) {
	struct info *i, *j, tmp; 
	for (i = list; i < list+len; i++) { 
		for (j = i+1; j < list+len; j++) { 
			if (strcmp(i->name, j->name) > 0) { 
				tmp = *i; 
				*i = *j; 
				*j = tmp; 
			} 
		} 
	} 
}
```
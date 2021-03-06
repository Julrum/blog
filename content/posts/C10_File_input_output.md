---
title: "10. 파일입출력"
date: 2020-03-26T14:49:30Z
categories: ["essay"]
tags: ["c", "language"]
cover: ""
---


## 01 파일처리

#### 파일 처리 개념

간단한 프로그램에서는 데이터를 입력받거나 출력할 경우에 표준 입출력 장치인 키보드와 모니터를 이용하여 처리한다. 이러한 데이터 처리는 그 작업이 컴퓨터의 주기억장치에서 이루어지기 때문에 프로그램의 실행을 종료할 경우에 입력한 데이터나 출력결과가 모두 지워져 버린다. 이와 같이 프로그램 종료 후에도 파일 입출력에 사용되는 데이터가 지워지는 것을 방지하기 위해 C에서 제공하는 파일처리 함수를 이용하여 입력 데이터를 디스크로부터 읽어 오거나 출력 데이터를 디스크로 저장하는 것을 파일처리라 한다. 파일처리는 많은 양의 입력 데이터와 출력 데이터를 보존해야 할 경우에 편리하게 사용된다. 이러한 파일처리는 다음과 같은 처리 절차를 통하여 이루어진다.

파일 포인터 선언 **→**  파일 열기  **→**  파일 입/출력  **→**  파일 닫기

#### 파일 처리 절차

### 1. 파일 포인터 선언 : FILE

파일을 처리하기 위해서 필요한 첫 번째 절차로 내에 표준 파일의 형으로 정의되어 있는 구조체형 `FILE`에 파일포인터 변수를 정의하는 것을 말한다. 파일 포인터 변수는 개방하려는 파일에 관한 정보(파일이름, 상태, 현재 위치 등)가 저장된 기억장소를 지정하는 포인터이다. 파일포인터명은 프로그램 내에서 파일을 지칭할 때 사용되며, 변수명을 만드는 규칙에 의해 만든다.

#### <일반형식>
```c
FILE *파일포인터변수명;
```

### 2. 파일 열기 : fopen()

입, 출력 처리를 하고자 하는 파일을 파일포인터에 연결시켜준다. 모든 파일처리는 파일명으로 하는 것이 아니라 파일포인터를 이용하여 아루어진다. `fopen` 함수는 파일이 정상적으로 열리면 파일 포인터를 반환하지만, 오류가 발행하면 `NULL`(`\0`)을 반환하다.

#### 일반형식
```c
파일포인터변수명 = fopen("파일명", "파일모드");
```

여기서, 파일명은 처리하고자 하는 파일의 이름을 말하며, 파일모드는 open된 파일이 수행할 작업의 성격을 말한다.

#### 파일 open 모드의 종류와 기능
|모드|기능|
|:---:|:---:|
|`r`|읽기(read)용 텍스트 파일 열기<br>※ 파일이 존재하지 않을 시 오류를 발생한다.|
|`w`|쓰기(write)용 텍스트 파일 열기<br>※ 파일이 이미 존재하면 기존의 내용이 지워지고 파일이 없으면 새로 만든다.|
|`a`|추가(append)용 텍스트 파일 열기<br>※ 파일이 이미 존재하면 파일의 끝에 새로운 내용이 추가되고, 파일이 없으면 파일을 새로 만든다.|
|`r+`|갱신용(update) 텍스트 파일 열기(파일 열기)|
|`w+`|갱신용(update) 텍스트 파일 열기(신규 작성)|
|`a+`|갱신(update)하기 위한 추가용 텍스트 파일 열기|
|`rb`, `wb`, `ab`, `rb+`, `wb+`, `ab+`|바이너리(이진) 파일 열기|

- 파일 `sample.txt`가 읽기 전용으로 사용될 수 있도록 개방되고, 그 파일이 파일포인터 `fp`에 할당된다.

#### 참고

파일을 open하고 close할 경우 초기 파일의 경로는 현재 프로그램이 실행되는 디렉터리가 된다. 만일 현재 디렉터리가 아닌 다른 디렉터리에 있는 파일을 입출력할 경우에는 해당 파일이 있는 디렉터리의 경로를 기술하여야 하면 이때 사용하는 디렉터리 구분 문자열은 `\` 대신에 `\\`로 표기하여야 한다.

예)
```c
fp = fopen("c:\\iwhan\\sample.txt","r")
```
- 파일포인터 `fp`에 c 드라이브 iwhan 폴더에 있는 `sample.txt` 파일을 읽기 전용으로 사용될 수 있도록 open한다.

### 3. 파일 닫기 : fclose()

`fclose()` 함수에 의해 개방된 파일을 닫고 할당된 파일 포인터를 해제한다. `fclose()` 함수는 정상적인 경우에는 0, 오류가 발생하면 `EOF`(-1)를 반환한다.

#### 일반형식
```c
fclose(파일포인터변수);
```

예) 
```c
fclose(fp);
```

- 파일포인터 `fp`에 open된 파일을 close한다. 만일 여러 개의 파일이 open되어 있는 경우 open된 파일을 모두 close할 경우에는 `fcloseall()` 함수를 사용한다.

#### 실습 10_01
```c
#include <stdio.h>
int main() {
	FILE *fp;
	fp = fopen("test1.txt","w");
	if(fp == NULL) {
		printf("파일을 열수 없습니다.\n");
		return 0;
	}
	else{
		printf("파일을 열었습니다.\n");
	}
	fclose(fp);
	printf("파일을 닫았습니다.\n");
	return 0;
}
```

#### 실습 10_02
```c
#include <stdio.h>
int main() {
	FILE *fp1, *fp2;
	fp1 = fopen("txt.in","w");
	fp2 = fopen("sam.in","r");
	printf("fp1=%x\n",fp1);
	if(fp2 == NULL)
		printf("fp2=NULL\n");
	fclose(fp1);
	return 0;
}
```

#### 실습 10_03
```c
#include <stdio.h> 
int main() {
	FILE *fp;
	fp = fopen("test1.txt", "w");
	if(fp == NULL){
		printf("파일을 열 수 없습니다.\n");
		return 1;
	}
	else{
		printf("파일을 열었습니다.\n");
	}
	fputs("Hello!\n",fp);
	fputs("Goodbye!\n",fp);
	printf("파일로 출력했습니다.\n");
	fclose(fp);
	printf("파일을 닫았습니다.\n");
	return 0;
}
```


## 02 순차 파일 처리 함수

파일에 저장된 데이터를 순서적으로 접근하여 읽거나, 파일로 데이터를 순서적으로 쓰는 처리에 사용되는 함수이다.

#### fgetc() 및 fputc() 함수

하나의 문자를 파일로 입력하거나 하나의 문자를 파일에서 출력하는 기능을 수행한다.

### 1. fgetc() 함수

하나의 문자를 파일포인터가 지정하는 파일에서 읽어 들이고, 다음 문자를 읽어 드리기 위해 파일 포인터(문자 위치)를 1만큼 증가시킨다. 만일 파일포인터가 파일의 끝이거나 오류룰 발생하면 `EOF`(-1)를 반환한다. `getc()`도 동일한 기능을 수행한다.

#### 일반형식
```c
int 변수1;
변수1 = fgetc(파일포인터변수1);
```

예) 
```c
int ch;
ch = fgetc(fp1);
```
- 파일 포인터 `fp1`이 지정하는 파일에서 하나의 문자를 읽어 들여 ch변수에 저장한다.

### 2. fputc() 함수

하나의 문자를 파일 포인터가 지정하는 파일로 출력(저장) 한 후 다음 문자를 출력하기 위해 파일 포인터를 1만큼 증가시킨다. `putc()`도 동일한 기능을 수행한다.

#### 일반형식
```c
int 변수1;
fputc(변수1, 파일포인터변수1);
```

(예)
```c
 int ch;  
fputc(ch, fp1);
```
- 파일 포인터 `fp1`이 지정하는 파일에 ch변수에 있는 문자를 출력(저장)한다.

#### 실습 10_04
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int p = 'A';
	if((fp = fopen("ex22.txt","w")) != NULL){
		while(p <= 'Z') {
			fputc(p,fp);
			p++;
		}
	}
	fclose(fp);
	return 0;
}
```

#### 실습 10_05
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int p;
	if((fp = fopen("ex22.txt","r")) != NULL) {
		while((p = fgetc(fp)) != EOF) {
			printf("%c",p);
		}
	}
	fclose(fp);
	return 0;
}
```


#### fgets() 및 fputs() 함수

문자열을 파일로 입력하거나 파일에서 출력하는 기능을 수행한다.

### 1. fgets() 함수

문자열을 파일포인터가 지정하는 파일에서 읽어 온다.

#### 일반형식
```c
fgets(문자열변수, n, 파일포인터변수);
```

파일 포인터변수가 지정하는 파일에서 n-1개의 문자를 일거 들여 문자열변수에 저장한다. 이떄 읽어 들인 문자열 끝에는 `\n` 과 `NULL`이 자동으로 삽입된다. 파일 포인터가 파일의 끝이거나 오류를 발생하면 `NULL`을 반한다.

예)
```c
char str[50];
fgets(str, 50, fp);
```

- 파일 포인터 fp가 지정하는 파일에서 49개의 문자를 읽어 들여 문자열 변수 str에 저장한다.

### 2. fputs() 함수

문자열을 파일포인터가 지정하는 파일로 출력(저장) 한다.

#### 일반형식
```c
fputs(문자열변수, 파일포인터변수);
```

문자열 변수에 저장된 문자열을 파일포인터 변수가 지정하는 파일에 출력한다.

예)
```c
char str[50] = "Hog gil dong";
fputs(str, fp);
```
- str에 저장된 문자열을파일포인터 fp가 지정하는 파일에 출력한다.

#### 실습 10_06
```c
#include <stdio.h>
int main(){
	FILE *fp;
	char str[4][10] = {{"one "},{"two "},{"three "},{"four "}};
	int a = 0;
	if((fp = fopen("ex23.txt","w")) != NULL){
		while(a < 4){
			fputs(str[a],fp);
			a++;
		}
	}
	fclose(fp);
	return 0;
}
```
  

#### 실습 10_07
```c
#include <stdio.h>
int main() {
	FILE *fp;
	char jul[50];
	int i = 0;
	if((fp = fopen("ex23.txt","r")) != NULL){
		while(fgets(jul, 50, fp) != NULL)
		printf("%s\n", jul);
	}
	return 0;
}
```


#### fprintf() 및 fscanf() 함수

지정된 서식에 맞게 파일의 내용을 읽어 오거나 지정된 서식에 맞게 파일로 출력(저장)한다.

### 1. fprintf() 함수

지정된 서식에 맞게 인수의 값을 파일로 출력(저장)한다.

#### 일반형식
```c
fprintf(파일포인터변수, "형식지정문자열', 인수1, 인수2, ...);
```

인수 값을 문장열 내의 `%`가 위치할 곳에 지정된 형태로 변환하여 파일포인터변수가 지정하는 파일에 출력한다.

예)
```c
fprintf(fp, "%-8s %4d", name, kor);
```
- 파일 포인터 `fp`가 지정하는 파일에서 name, kor에 있는 데이터를 `%-8s`, `%4d` 형태로 변환하여 출력(저장)한다.

### 2. fscanf() 함수

지정된 서식에 맞게 파일에서 인수의 값을 읽어온다.

#### 일반형식
```c
fscanf(파일포인터변수, "형식지정문자열", 인수1, 인수2, ...);
```

파일포인터변수가 지정하는 파일로부터 데이터를 읽어 들이고 이를 지정된 형식대로 변환하여 인수에 입력한다. `scanf()`와 같이, 인수가 배열로 사용되는 경우를 제외하고는 인수명 앞에 주소연산자(`&`)를 붙인다.

예)
```c
fscanf(fp, "%s %d", name, &kor);
```
- 파일 포인터 `fp`가 지정하는 파일에서 데이터를 읽어 들여 변수 name과 kor에 저장한다. 이때 kor변수는 배열이 아니므로 `&`연산자를 붙인다.

#### 실습 10_08
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int bunho;
	char irum[30];	
	if((fp = fopen("ex24.txt","w+")) != NULL) {
		printf("bunho irum(종료는 Ctrl+z)=?\n");
		while(scanf("%d %s", &bunho, irum) != EOF)
		fprintf(fp, "%4d %10s\n", bunho, irum);
	}
	fclose(fp);
	return 0;
}
```

#### 실습 10_09
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int bunho;
	char irum[30];
	if((fp = fopen("ex24.txt","r")) ! =NULL) {
		while(fscanf(fp,"%d %s", &bunho, irum) != EOF)
		printf("번호 : %d  이름 : %-10s\n", bunho, irum);
	}
	fclose(fp);
	return 0;
}
```

## 03 랜덤 파일 처리 함수

랜덤 파일 처리란 파일 내에 저장된 데이터를 처음부터 순서적으로 접근하지 않고 원하는 위치를 직접 찾아 접근하여 처리하는 방식을 말하며, 이러한 파일 처리위해 사용되는 함수를 랜덤 파일 처리 함수라 한다. 랜덤 파일 처리를 이용하여 파일을 처리하게 되면 파일 내의 어떤 자료를 수정하기 위아여 처음부터 파일의 내용을 읽어 들여 수정할 필요 없이 원하는 위치의 레코드만을 직접 수정할 수 있다.

### 1. fseek() 함수

파일 포인터의 위치를 사용자가 원하는 곳으로 이동시킨다.

#### 일반 형식
```c
fseek(파일포인터변수, 상대위치, 모드);
```

상대 위치는 수치 다음에 `L`(`long`형 데이터)을 붙이며 수식일 경우는 붙이지 않는다. 모드는 다음과 같이 3가지가 있다.

|모드|기능|
|:---:|:---|
|0|파일의 시작부터 상대위치를 구한다.|
|1|현재의 파일 포인터부터 상대위치를 구한다.|
|2|파일의 끝부터 상대위치를 구한다.|

예)
```c
fseek(fp, 3L, 0);
```
- 파일 포인터를 파일의 시작 위치부터 3바이트 이동한다.

|파일의 내용|상대위치|
|:---:|:---|
|a|0L|
|b|1L|
|c|2L|
|d|3L|
|...|...|


### 2. ftell() 함수

현재의 파일 포인터의 위치를 구한다.

#### 일반 형식
```c
ftell(파일포인터변수);
```

파일의 처음에서부터 현재 파일포인터까지의 상대적인 위치를 바이트 단위로 구한다. 실패할 경우 `-1L`을 반환한다.

예)
```c
ftell(fp);
```

파일포인터변수 `fp`와 연결된 파일에서, 현재 작업하고 있는 파일포인터의 위치를 반환한다.

### 3. rewind() 함수

파일포인터의 위치를 파일의 가장 앞으로 이동시킨다.

#### 일반 형식
```c
rewind(파일포인터변수);
```

예)
```c
rewind(fp)
```
- 파일포인터변수 `fp`와 연결된 파일의 파인포인터 위치를 파일의 가장 앞으로 이동시킨다.

#### 실습 10_10
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int i = 1, kk = 0;
	long a = 1;
	if((fp = fopen("ex25.txt","w+")) != NULL) {
		while(i <= 10) {
			fprintf(fp, "%3d", i);
			i++;
		}
		fseek(fp, 3*a, 0);
		fprintf(fp, "%3d", kk);
		fclose(fp);
	}
	return 0;
}
```
  

#### 실습 10_11
```c
#include <stdio.h>
int main() {
	FILE *fp;
	int i = 1, kk = 0;
	long a = 1;	
	if((fp = fopen("sil24.txt","w")) != NULL) {
		printf("시작 파일 포인터 위치=%ld\n", ftell(fp));
		fprintf(fp,"012345");
		printf("데이터 저장 후 파일 포인터 위치=%ld\n", ftell(fp));
		rewind(fp);
		printf("rewind(fp) 후 파일 포인터 위치=%ld\n", ftell(fp));
		fclose(fp);
	}
	return 0;
}
```
  

#### 실습 10_12
```c
#include <stdio.h>

int main() { 
	FILE *in, *out; 
	int ch = NULL; 
	if ((in = fopen("mun1.txt", "r")) != NULL) { 
		if ((out = fopen("copy1.txt", "w")) != NULL) { 
			while (1) { 
				ch = fgetc(in); 
				if (ch == EOF) break; 
				fputc(ch, out); 
			} fclose(out); 
		} fclose(in); 
	}
	return 0; 
}
```
  

#### 실습 10_13
```c
#include <stdio.h> 
#define STDLEN 5 
#define SUBJ 3 
	struct Student { 
		int num; 
		char name[15]; 
		int korean; 
		int math; 
		int computer; 
		int total; 
	} students[] = { 
		{1, "김찬수", 94, 95, 98, 0}, 
		{2, "박주형", 92, 90, 88, 0}, 
		{3, "이미애", 89, 92, 95, 0}, 
		{4, "정다빈", 94, 88, 88, 0}, 
		{5, "한아름", 95, 90, 93, 0} 
	};

	int getrank(struct Student list[], int len, int idx); 
	int main() { 
		int i; 
		FILE *fp; 
		if ((fp = fopen("mun2.out", "w")) != NULL) { 
			for (i = 0; i < STDLEN; i++) { 
				struct Student *cur = &students[i]; 
				cur->total = cur->korean + cur->math + cur->computer; 
			} 
			fputs("번호 이 름 국어 수학 정보 총점 평균 석차 \n", fp); 
			for (i = 0; i < STDLEN; i++) { 
				struct Student *cur = &students[i]; 
				fprintf(fp, " %-3d %s %d %d %d %d %.1lf %d \n", 
				cur->num, cur->name, cur->korean, cur->math, cur->computer, cur->total, (double)cur->total/SUBJ, getrank(students, STDLEN, i)); 
			}
			fclose(fp); 
		}
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

#### 실습 10_14
```c
#include <stdio.h> 
int main() { 
	FILE *fp; 
	char findch; 
	int ch; 
	int findChCount = 0; 
	int wordCount = 0; 
	int wholeChCount = 0; 
	int flag = 0; // ch 바로 앞부분 띄어쓰기 판별 플래그 
	if ((fp = fopen("mun3.txt", "r")) != NULL) { 
		printf("찾고자 하는 문자는 ? "); 
		findch = getchar(); 
		while (1) { 
			ch = fgetc(fp); 
			if (ch == EOF) { 
				if (flag == 0) wordCount++; 
				break; 
			}
			if (ch == findch) findChCount++; 
			if (ch == ' ') { 
				wordCount++; 
				flag = 1; 
			} else {
				flag = 0; 
			} 
			wholeChCount++; 
		} 
		printf("%c문자 개수 = %d\n", findch, findChCount);
		printf("단어 개수 = %d\n", wordCount); 
		printf("전체 문자 개수 = %d\n", wholeChCount); 
		fclose(fp); 
	}
	return 0; 
} 
```

#### 실습 10_15
```c
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h> 
#define FILENAME "AddressData.dat" 
#define CLEAN() system("cls") 
FILE *fp = NULL; 
void change_filemode(const char *mode); 
void rec_seekmove(int); 
void addr_input(); 
void addr_access(); 
void show_addr(); 
int backmenu(); 
int main() { 
	fp = fopen(FILENAME, "r+"); 
	if (fp == NULL) { 
		fp = fopen(FILENAME, "w+"); 
		if (fp == NULL) { 
			printf("파일 액세스 권한이 없습니다.\n"); 
			return 1; 
		} 
	}
	do { 
		int menu; 
		printf("1. 주소 초기화\n");
		printf("2. 주소 입력\n"); 
		printf("3. 주소 조회\n"); 
		printf("4. 주소 출력\n"); 
		printf("0. 종 료\n"); 
		printf("원하는 작업의 번호는? "); 
		scanf("%d", &menu); 
		CLEAN(); 
		printf("------------------------------\n"); 
		switch (menu) { 
			case 1: 
				change_filemode("w+"); 
				break; 
			case 2: 
				addr_input(); 
				break; 
			case 3: 
				addr_access(); 
				break; 
			case 4: 
				show_addr(); 
				break; 
			case 0: 
				fclose(fp); 
			return 0; 
		}
		CLEAN(); 
	} while (1); 
		return 0; 
	}
	void change_filemode(const char *mode) { 
	fclose(fp); 
	fp = fopen(FILENAME, mode); 
}

void rec_seekmove(int rec) { 
	int i; 
	rewind(fp); 
	for (i = 0; i < rec; i++) { 
		fseek(fp, 37L, 1); 
	} 
}
void addr_input() { 
	int recnum = 0; 
	char name[15]; 
	char address[20]; 
	int ch; 
	while (1) { 
		printf("입력할 레코드번호 : "); 
		scanf("%d", &recnum); 
		printf("이름 주소 : "); 
		scanf("%s", name); 
		fgets(address, 20, stdin); 
		rec_seekmove(recnum); 
		fprintf(fp, "%15s %20s ", name, address); 
		if (backmenu() == 1) break; 
	} 
}
void addr_access() { 
	int recnum = 0; 
	char line[70]; 
	while (1) { 
		char name[15] = ""; 
		char address[20] = "";

		printf("조회할 레코드 : "); 
		scanf("%d", &recnum); 
		rec_seekmove(recnum); 
		fgets(line, 38, fp); 
		//%[^\n]s: 문자열을 공백 포함으로 받음. 
		sscanf(line, "%s %[^\n]s", name, address); 
		printf("%d번 레코드\n", recnum); 
		printf("이 름 : %s\n주 소 : %s\n", name, address); 
		if (backmenu() == 1) break; 
	} 
}
void show_addr() { 
	char line[70]; 
	int recnum = 0; 
	long end; 
	fseek(fp, 0L, 2); 
	end = ftell(fp); 
	rewind(fp); 
	while (1) { 
		char name[15] = ""; 
		char address[20] = ""; 
		rec_seekmove(recnum); 
		if (ftell(fp) >= end) break; 
		fgets(line, 38, fp); 
		//%[^\n]s: 문자열을 공백 포함으로 받음. 
		sscanf(line, "%s %[^\n]s", name, address); 
		printf("%s %s\n", name, address); 
		recnum++; 
	}

	while (1) { 
		if (backmenu() == 1) break; 
	} 
}
int backmenu() { 
	char in[3]; 
	printf("------------------------------\n"); 
	printf("초기메뉴(m) : "); 
	scanf("%s", in); 
	if (strcmp(in, "m") == 0) return 1; 
	else return 0; 
}
```
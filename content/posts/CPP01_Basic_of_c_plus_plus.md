---
title: "C++와 표준 라이브러리 초단기 속성 코스"
date: 2020-04-10T14:48:01Z
categories: ["essay"]
tags: ["c++", "c++17"]
cover: ""
---

## 전처리 지시자

C++로 작성된 소스 코드를 프로그램으로 만드는 빌드 작업은 세 단계를 거친다. 먼저 **전처리**<sup>preprocess</sup> 단계에서는 소스 코드에 담긴 메타 정보를 처리한다. 이어서 **컴파일**<sup>Compile</sup> 단계에서는 소스 코드를 머신이 읽을 수 있는 오브젝트<sup>object</sup> 파일로 변환된다. 마지막 **링크**<sup>Link</sup> 단계에서는 앞에서 변환한 여러 오브젝트 파일을 애플리케이션으로 엮는다.

지시자<sup>directive</sup>란 전처리기에 전달할 사항을 표현하며, `#`문자로 시작한다. 헤더 파일은 주로 나중에 소스 파일에서 구현할 함수를 선언하는 용도로 사용된다.이러한 함수 **선언부**는 그 함수의 호출방식, 매개변수의 개수와 타입, 리턴 타입 등만 컴파일러에 알려주고, 그 함수가 실제로 수행할 동작은 **구현부（정의부）**에 작성한다. 선언은 확장자가 .h인 헤더 파일에 작성하고, 구현은 확장자가 .cpp인 소스 파일에 작성한다.
## 네임스페이스
**네임스페이스**는 코드에서 이름이 서로 충돌하는 문제를 해결하기 위해 나온 개념이다.

C++17에서는 **중첩된 네임스페이스**를 좀 더 쉽게 사용할 수 있도록 개선했다.
```c++
namespace MyLibraries::Networking::FTP {
    /*...*/
}
```
**네임스페이스 앨리어스**<sup>namespace</sup> <sup>alias</sup>를 사용하려면 네임스페이스의 이름을 다르게 표현하거나 기존 이름을 좀 더 짧게 만들 수 있다.
```c++
namespace MyFTP = MyLibraries::Networking::FTP;
```

## 리터럴
리터럴은 코드에 표시한 숫자나 스트링과 같은 값을 의미한다. 숫자는 다음과 같은 리터럴로 표현할 수 있다.
- 십진수 리터럴, 123
- 8진수 리터럴, 0173
- 16진수 리터럴, 0x7B
- 이진수 리터럴, 0b1111011
- 부동소수점 값（예: 3.14f）
- 배정도 부동소수점 값（예: 3.14）
- 단일 문자（예: ’a’）
- ’0’으로 끝나는 문자 배열（예: "character array"）
- 16진수 부동 소수점 리터럴（예: 0x3.ABCp-10, 0xb.cp121） C++17

## 변수
변수는 코드 안 어디에서나 선언할 수 있으며, 현재 블록 안에서 변수를 선언한 줄 다음부터 어디에서나 그 변수에 접근할 수 있다.

변수 타입을 실행 중에 바꿀 수 있다. 이를 **캐스팅(동적 형변환, 타입캐스팅)**이라 한다.
```c++
float myFloat = 3.14f;
int	i1 = (int)myFloat;              // 방법 1
int	i2 = int(myFloat);              // 방법 2
int	i3 = static_cast<int>(myFloat); // 방법 3
```

## 타입

### 열거 타입

정수는 사실 연속적으로 나열한 숫자 중 하나를 표현한 것이다. **열거 타입**<sup>enum</sup>을 사용하면 숫자를 나열하는 방식과 범위를 마음대로 정의해서 변수를 선언하는 데 활용할 수 있다.

```C++
enum PieceType { PieceTypeKing = 1, PieceTypeQueen, PieceTypeRook = 10, PieceTypePawn };
```
`PieceTypeKing`은 정수값 1 을 갖고, `PieceTypeQueen`은 컴파일러에 의해 2라는 값이 대입되고, `PieceTypeRook`은 10을 갖고, `PieceTypePawn`은 컴파일러에 의해 11이라는 값이 자동으로 대입된다.

### 엄격한 열거 타입

원래 `enum`은 타입을 엄격하게 따지지 않는다. 참고로 타입을 엄격히 따지는 것을 **스트롱 타입**<sup>strong</sup> <sup>typed</sup>이라고 표현한다.
엄격하게 적용하고 싶으면 `enum class`를 사용한다.

```c++
enum class PieceType
{
	King = 1,
	Queen,
	Rook = 10,
	Pawn
}
```



### 구조체
**구조체**를 사용하면 기존에 정의된 타입을 한 개 이상 묶어서 새로운 타입으로 정의 할 수 있다.

```c++
struct Employee {
	char firstInitial;
	char lastInitial;
	int employeeNumber;
	int salary;
}
```



구조체를 구성하는 각 필드는 도트(`.`) 연산자로 접근한다.
```c++
#include <iostream>
#include "employeestruct.h"

using namespace std;

int main() {
	Employee anEmployee;
	anEmployee.firstInitial = 'M';
	anEmployee.lastInitial = 'G';
	anEmployee.employeeNumber = 42;
	anEmployee.salary = 80000;
	cout << "Employee: " << anEmployee.firstlnitial << anEmployee.lastInitial << endl;
	cout << "Number: " << anEmployee.employeeNumber << endl;
	cout << "Salary : $" << anEmployee.salary << endl;
	return 0;
}
```



## 조건문

### if/else문

C++17부터 `if`문 안에 이니셜라이저<sup>initializer</sup>를 넣는 기능이 추가됐다.

```c++
if(<이니셜라이저>;<조건문>) { <본문> }
```

`<이니셜라이저>`에서 정의한 변수는 `<조건문>`과 `<본문>` 안에서만 사용할 수 있고 `if` 문 밖에서는 사용할 수 없다.

### switch문
`switch` 문의 조건으로 지정한 값과 일치하는 `case` 문이 있다면 그 아래 나오는 문장을 `break` 문이 나타날 때까지 실행한다. 이때 `break`문이 없다면 다음에 나오는 `case` 문도 계속해서 실행하는데, 이렇게 실행되는 것을 **fallthrough**(**흘려보내기**)라 부른다.

폴스루 방식으로 작성하면 버그가 발생하기 쉽다. 중간에 `break` 문을 깜박 잊고 빠뜨렸을 경우가 그렇다. C++17부터 다음과 같이 `[[fallthrough]]`속성을 지정해서 의도적으로 폴스루 방식으로 작성했다고 컴파일러에 알려줄 수 있다.

```c++
switch (backgroudColor) {
	case Color::DarkBlue:
		doSomethingForDarkBlue();
		[[fallthrough]];
	case Color::Black:
		doSomethingFroBlackOrDarkBlue();
		break;
    case Color::Red:
		[[fallthrough]];
    case Color::Green:
        break;
}
```

C++17부터 `if`문처럼 `switch` 문도 이니셜라이저를 지정할 수 있다.

## 논리 연산자
C++는 논리 표현식을 **단락 논리**(**축약 논리**)방식으로 평가한다. 다시 말해 표현식을 평가하는 도중에 최종 결과가 확정되면 나머지 부분은 평가하지 않는다. 단락 기능은 프로그램 성능을 높이는데 도움 된다. 단락 되는 논리식을 작성할 때는 가볍게 검사할 수 있는 부분은 앞에 두고, 시간이 좀 걸리는 부분은 뒤에 둔다.
## 함수
### 함수 리턴 타입 추론
C++14부터는 함수의 리턴 타입을 컴파일러가 알아서 지정할 수 있다. 이 기능을 적용하려면 리턴 타입 자리에 `auto` 키워드를 적는다. 그러면 컴파일러는 `return` 문에 나온 표현식의 타입에 따라 리턴 타입을 추론한다. 함수 안에는 `return` 문이 여러 개가 있을 수 있는데, 이때 각 타입은 모두 같아야 한다. 리턴값으로 재귀 호출문을 지정할 수 있는데, 이때 비재귀 호출 `return` 문도 반드시 함께 지정한다.

### 현재 함수 이름
함수마다 내부적으로 `__func__`라는 로컬 변수가 정의돼 있다. 이 변수는 현재 함수의 이름을 값으로 가지고 있다.
## C 스타일 배열
**영 초기화(zero-initialization)**구문으로 한 번에 초기화하는 방법이 있다. 또한 이니셜라이즈 리스트를 사용해도 된다.

```c++
int myArray[3] = {};
int myArray2[] = {1, 2, 3, 4}; // 이니셜라이즈 리스트
```

 스택 기반의 C 스타일 배열의 크기는 C++17부터 제공하는 `std::size()` 함수로 알아낼 수 있다.

## std::array
C++에서는 `std::array`라는 고정 크기 컨테이널를 제공한다. 이 타입은 `<array>` 헤더 파일에 정의돼 있다.
```c++
array<int, 3> arr = {9, 8, 7};
cout << "Array size = " << arr.size() << endl;
cout << "2nd element = " << arr[l] << endl;
```

## std::vector

C++ 표준 라이브러리에서는 저장 공간의 크기가 고정되지 않은 컨테이너를 다양하게 제공한다. 대표적인 예로 `<vector>` 헤더 파일에 선언된 `std::vector`가 있다.
```c++
vector<int> myVector = {11, 22};

myVector.push_back(33);
myVector.push_back(44);

cout << "1st element: " << myVector[0] << endl;
```

## 구조적 바인딩
C++17부터 **구조적 바인딩**<sup>structed</sup> <sup>binding</sup>이란 개념이 도입됐다. 구조적 바인딩을 이용하면 여러 개의 변수를 선언할 때 배열, 구조체, 페어 또는 튜플의 값으로 초기화할 수 있다. 구조적 바인딩을 적용하려면 반드시 `auto` 키워드를 붙여야 한다.
```c++
struct Point { double mX, mY, mZ;};
Point point;
point.mx = 1.0; point.my = 2.0; point.mz = 3.0;
auto [x, y, z] = point;
```

## 반복문
### while 문
`break` 키워드를 사용하면 반복문을 즉시 빠져나와 뒤에 있는 코드를 계속 진행한다. 또한 `continue` 키워드를 사용하면 즉시 반복문의 첫 문자으로 돌아가서 `while` 문에 지정한 표현식을 다시 평가한다. 하지만 반복문 안에서는 `continue` 사용을 자제한다.

### do/while문
동작은 `while` 문과 비슷하지만, 먼저 코드 블록부터 실행한 뒤 조건을 검사하고 그 결과에 따라 루프를 계속 진행할지 결정한다.
### for 문
초기 표현식, 종료 조건, 매번 반복이 끝날 때마다 실행할 문장으로 반복문을 구성할 수 있기 때문에 편하다.

### 범위 기반 for 문
이 구문은 컨테이너에 담긴 원소에 대해 반복문을 실행하는 데 편하다. C 스타일의 루프, 이니셜라이저 리스트, 그리고 `std::array`, `std::vector`, 표준 라이브러리에서 제공하는 컨테이너처럼 반복자를 리턴하는 `begin()`과 `end()` 메서드가 정의된 모든 타입에 적용할 수 있다.
```c++
std::array<int, 4> arr = {1, 2, 3, 4};
for (int i : arr) {
	std::cout << i << std::endl;
}
```

### 이니셜라이저 리스트
이니셜라이저 리스트는 `<initializer_list>` 헤더 파일에 정의돼 있으며, 이를 활용하면 여러 인수를 받는 함수를 쉽게 작성할 수 있다. 원소 타입에 대한 리스트를 꺾쇠괄호로 묶어서 지정해야 한다.
```c++
#include <initializer_list>

using namespace std;

int makeSum(initializer_list<int> 1st)
{
	int total = 0;
	for (int value : 1st) {
		total += value;
	}
	return total;
}
/*----------------------------------------------------------------------*/
int a = makeSum({1, 2, 3});
int b = makeSum({10, 20, 30, 40, 50, 60});
int c = makeSum({1, 2, 3.0}); // 이니셜라이저 리스트는 타입 세이프하기 때문에 컴파일 에러
```



## ## C++ 스트링
`string` 타입은 `<string>` 헤더 파일에 정의돼 있고, 기본 타입처럼 사용할 수 있다.

## 포인터와 동적 메모리
동적 메모리를 이용하면 컴파일 시간에 크기를 확정할 수 없는 데이터를 다룰 수 있다.
### 스택과 힙
현재 실행 중인 함수에 선언된 변수는 모두 최상단의 접시에 해당하는 최상단 스택 프레임의 메모리 공간에 담겨 있다. 스택 프레임은 각각의 함수마다 독립적인 메모리 공간을 제공한다는 점에서 굉장히 유용하다.

**힙**이란 현재 함수 또는 스택 프레임과는 완전히 독립적인 메모리 공간이다. 함수가 끝난 후에도 그 안에서 사용하던 변수를 계속 유지하고 싶다면 힙에 저장한다. 힙은 스택보다 구조가 간결하다. 프로그램에서 원하는 시점에 언제든지 이 비트 더미에 새로운 비트를 추가하거나 기존에 있던 비트를 수정할 수 있다. 힙에 할당된 메모리 공간은 직접 할당 해제해야한다.

### 포인터 사용법
메모리 공간을 적당히 할당하기만 하면 어떠한 값이라도 힙에 저장할 수 있다.
```c++
int* mylntegerPointer;
```

`int` 타입 뒤에 붙은 별표(`*`)는 이 변수가 정수 타입에 대한 메모리 공간을 가리킨다는 것을 의미한다. 이때 포인터는 동적으로 할당된 힙 메모리를 가리키는 화살표와 같다. 아직 값을 할당하지 않았기 때문에 포인터가 구체적으로 가리키는 대상은 없다. 이를 **초기화되지 않은 변수**<sup>uninitialized</sup> <sup>variable</sup>라 부른다.

```c++
myIntegerPointer = new int;
```

이렇게 하면 정숫값 하나에 대한 메모리 주소를 가리킨다. 이 포인터가 가리키는 값에 접근하려면 포인터를 **역참조**<sup>dereference</sup>해야 한다. 역참조란 포인터가 힙에 있는 실제값을 가리키는 화살표를 따라간다는 뜻이다. 앞에서 힙에 새로 할당한 공간에 정숫값을 넣으려면 다음과 같이 작성한다.
```c++
*myIntegerPointer = 8;
```

한 가지 주의할 점은 이 문장은 `mylntegerPointer = 8;`과 전혀 다르다는 것이다. 이 문장에서 변경하는 값은 포인터(메모리 주소)가 아니라 이 포인터가 가리키는 메모리에 있는 값이다. 만약 변수 앞에 나온 `*`가 없으면 메모리 주로가 8인 지점을 가리키는데, 거기에 의미없는 값이 담겨 있어서 이렇게 실행하면 프로그램이 뻗어버릴 가능성이 높다.
동적으로 할당한 메모리를 다 쓰고 나면 `delete` 연산자로 그 공간을 해제해야 한다. 메모리를 해제한 포인터를 다시 사용하지 않도록 다음과 같이 곧바로 포인터 변수의 값은 `nullptr`로 초기화하는 것이 좋다.

```c++
delete myIntegerPointer;
myIntegerPointer = nullptr;
```

포인터는 힙뿐만 아니라 스택과 같은 다른 종류의 메모리를 가리킬 수도 있다. 원하는 변수의 포인터값을 알고 싶다면 주소 참조 연산자인 `&`를 사용한다.
```c++
int i = 8;
int* myIntegerPointer = &i;
```

먼저 `*` 연산자로 역참조해서 구조체 자체에 접근한 뒤 필드에 접근할 때는 `.` 연산자로 표기한다. 예를 들면 다음 코드와 같다.
```C++
Employee* anEmployee = getEmployee();
cout << (*anEmployee).salary << endl;
cout << anEmployee->salary << endl; //윗 줄과 같은 뜻이다.
```

포인터를 다룰 때 앞에서 소개한 단락 논리를 적용하면 잘못된 포인터에 접근하지 않게 할 수 있다.
```c++
bool isValidSalary = (anEmployee && anEmployee->salary > 0);
```

`anEmployee`의 포인터값이 올바를 때만 역참조해서 급여 정보를 가져온다.

### 동적으로 배열 할당하기
배열을 동적으로 할당할 때도 힙을 활용한다.
```c++
int arraySize = 8;
int* myVariableSizedArray = new int[arraySize];
```

이렇게 하면 정수 타입 원소에 대해 `arraysize` 변수로 지정한 개수만큼 메모리가 할당된다. 포인터 변수는 여전히 스택 안에 있지만 동적으로 생성된 배열은 힙에 있다.
메모리를 할당한 뒤에는 `myVariableSizedArray`를 일반 스택 기반 배열처럼 다룰 수 있다.

```c++
myVariableSizedArray[3] = 2;
```

배열을 이용한 작업이 끝나면 다른 변수가 힙의 메모리 공간을 쓸 수 있도록 이 배열을 힙에서 제거한다.
```c++
delete[] myVariableSizedArray;
myVariableSizedArray = nullptr;
```

### 널 포인터 상수
C++11 이전에는 `NULL`이란 상수로 널 포인터를 표현했다. `NULL`은 실제로 상수 0과 같아서 문제가 발생할 여지가 있다. 이럴 때는 정식 널 포인터 상수인 `nullptr`를 사용한다.
### 스마트 포인터
**스마트 포인터**<sup>smart</sup> <sup>pointer</sup>를 사용하면 메모리와 관련하여 흔히 발생하는 문제를 방지할 수 있다. 스마트 포인터로 지정한 객체가 스코프를 벗어나면 메모리가 자동으로 해제된다.
C++에서 가장 중요한 스마트 포인터 타입은 다음 두 가지다. 둘 다 `<memory>`헤더 파일에 정의돼 있으며 `std` 네임스페이스에 속해 있다.

- `std::unique_ptr`
- `std::shared_ptr`

`unique_ptr`는 포인터로 가리키는 대상이 스코프를 벗어나거나 삭제될 때 할당된 메모리나 리소스도 자동으로 삭제된다는 점을 제외하면 일반 포인터와 같다. 그러나 `unique_ptr`가 가리키는 객체를 일반 포인터로는 가리킬 수 없다. `unique_ptr`는 `return`문이 실행되거나 익셉션<sup>exception</sup>이 발생하더라도 항상 할당된 메모리나 리소스를 해제할 수 있다는 장점이 있다.

`unique_ptr`를 생성할 때는 반드시 `std::make_unique<>` 를 사용해야 한다.

```c++
Employee* anEmployee = new Employee;
// ...
delete anEmployee;
// 위의 선언을 아래와 같이 할 수 있다.
auto anEmployee = make_unique<Employee>();
```

`unique_ptr`는 제네릭 스마트 포인터<sup>generic</sup> <sup>smart</sup> <sup>pointer</sup>라서 어떠한 종류의 메모리도 가리킬 수 있다. 그래서 템플릿으로 만든 것이다. 템플릿은 매개변수를 꺾쇠괄호(`<>`)로 묶어서 지정하는데, `unique_ptr`에서는 여기에 가리키려는 메모리 타입을 지정한다.
`make_unique()` 는 C++14부터 추가됐다. C++14를 지원하지 않는 컴파일러를 사용하다면 다음과 같은 방법으로 `unique_ptr`를 만든다.

```c++
unique_ptr<Employee> anEmployee(new Employee);
```

`unique_ptr`는 C 스타일 배열을 지정하는 데도 활용할 수 있다. 다음 예는 열 개의 `Employee` 인스턴스로 구성된 배열을 생성하여 이를 `unique_ptr`에 저장하고, 배열에 담긴 원소를 접근하는 방법을 보여주고 있다.

```c++
auto employees = make_unique<Employee[]>(10);
cout << "Salary: " << employees[0].salary << endl;
```

`shared_ptr`를 사용하면 데이터를 공유할 수 있다. `shared_ptr`에 대한 대입 연산이 발생할 때마다 레퍼런스 카운터(참조 횟수)가 하나씩 증가한다. 그래서 `shared_ptr`가 가리키는 데이터를 레퍼런스 카운트만큼 사용하고 있다는 것을 표현한다. `shared_ptr`가 스코프를 벗어나면 레퍼런스 카운트가 감소한다. 그러다 레퍼런스 카운트가 0이 되면 그 데이터를 아무도 가지고 있지 않기 때문에 포인터로 가리키던 객체를 해제한다.

```C++
auto anEmployee = make_shared<Employee>();
if (anEmployee) {
cout << "Salary： " << anEmployee->Salary << endl;
}
```

C++17부터 `shared_ptr`에 배열도 저장할 수 있다.
```c++
auto anEmployee = make_shared<Employee>();
shared_ptr<Employee[]> employees(new Employee[10]);
cout << "Salary: " << employees[0].salary << endl;
```

## const의 다양한 용도
### const 상수

C 언어에서는 흔히 버전 번호처럼 프로그램을 실행하는 동안 변경하면 안 되는 값에 이름을 붙일 때 전처리 구문인 `#define`을 사용했다. C++에서는 상수를 `#define` 대신 `const`로 정의하는 것이 바람직하다. `const`로 상수를 정의하는 방법은 변수를 정의할 때와 거의 같고, 값이 변경되지 않도록 보장하는 작업은 컴파일러가 처리한다는 점만 다르다.

### const 매개변수
C++에서는 non-const 변수를 캐스팅할 수 있다. 이렇게 하면 다른 코드에서 변수를 변경하지 않도록 어느 정도 보호할 수 있다.
## 레퍼런스
C++에서 제공하는 레퍼런스<sup>reference</sup>(참조)를 사용하면 기존 변수에 새 이름을 지정할 수 있다.
```c++
int x = 42;
int& xReference = x;
```

변수의 타입 뒤에 `&`을 붙이면 그 변수는 레퍼런스가 된다. 코드에서 다루는 방법은 일반 변수와 같지만 내부적으로는 원본 변수에 대한 포인터로 취급한다. 둘 중 한 변수에서 값을 변경하면 그 결과가 다른 변수에도 반영된다.

### 레퍼런스 전달 방식
일반적으로 함수에 전달하는 변수는 **값 전달 방식**<sup>pass</sup> <sup>by</sup> <sup>value</sup>으로 처리한다. 예를 들어 함수의 매개변수에 정수를 전달하면 함수 안에는 그 정수의 복제본이 전달된다. 따라서 함수 안에서 원본 변수의 값을 변경할 수 없다. C에서는 스택 변수에 대한 포인터를 자주 사용했는데, 이런 방식을 사용하면 다른 스택 프레임에 있는 원본 변수를 수정할 수 있다. 이러한 포인터를 역참조하면 그 포인터가 현재 스택 프레임을 가리키지 않더라도 함수 안에서 그 변수가 가리키는 메모리의 값을 수정할 수 있다. 그런데 이 방식은 포인터 연산이 많아져서 간단한 작업이더라도 코드가 복잡해진다.
C++에서는 값 전달 방식보다 뛰어난 **레퍼런스(참조) 전달 방식**<sup>pass</sup> <sup>by</sup> <sup>reference</sup>을 제공한다. 이 방식을 사용하면 매개변수가 포인터값이 아닌 레퍼런스로 전달된다. 예를 들어 `addOne()` 함수를 두 가지 방식으로 구현한 코드를 살펴보자. 첫 번째 함수는 매개변수가 값으로 전달돼 함수 안에서는 그 값의 복제본을 조작하기 때문에 원본 변수는 변하지 않는다. 두 번째 함수는 레퍼런스로 전달되기 때문에 원본 변수의 값도 변경된다.
```c++
void addOne(int i)
{
	i++； // 복제본이 전달됐기 때문에 원본에는 아무런 영향을 미치지 않는다.
}
void addOne(int& i)
{
	i++； // 원본 변수가 변경된다.
}
int main() {
	int myInt = 7;
	addOne(myInt);
	return 0;
}
```

### const 레퍼런스 전달 방식
`const` 레퍼런스의 가장 큰 장점은 성능이다. 함수에 매개변수를 값으로 전달하면 그 값 전체가 복제된다. 하지만 레퍼런스로 전달하면 원본에 대한 포인터만 전달되기 때문에 원본 전체를 복재할 필요가 없다. 또한 `const` 레퍼런스로 전달하면 복제되지도 않고 원본 변수가 변경되지도 않는 장점을 모두 취할 수 있다.
`const` 레퍼런스는 특히 객체를 다룰 때 유용하다. 객체는 대체로 커서 복제하는 동안 의도하지 않은 효과가 발생할 수 있기 때문이다.

## 익셉션
C++는 유연성이 굉장히 뛰어난 반면 안정성은 그리 좋지 않다. C++에 안정성을 좀 더 높이기 위해 제공하는 기능 중 하나로 **익셉션**<sup>exception</sup>(**예외**)가 있다.
익셉션이란 예상하지 못한 상황을 표현하는 클래스/객체이다. 익셉션을 활용하면 문제가 발생했을 때 좀 더 융툥성 있게 대처할 수 있다.
코드에서 특정한 조건을 만족해서 익셉션을 발생시키는 것을 익셉션을 **던진다**<sup>throw</sup>(발생시킨다)고 표현하고, throw 구문으로 작성한다. 또한 이렇게 발생된 익셉션에 대해 적절한 동작을 수행하는 것을 익셉션을 **잡는다**<sup>catch</sup>(받는다, 처리한다)고 표현하고, `catch` 구문으로 작성한다.

```c++
double dividenumbers(double numerator, double denominator)
{
	if (denominator == 0) {
		throw invalid_argument("Denominator cannot be 0."); // <stdexcept> 헤더 파일을 불러와야한다
	}
	return numerator / denominator;
} 
```

`throw` 문장이 실행되면 함수에서 값을 리턴하지 않고 실행을 즉시 중단한다. 이처럼 익셉션이 발생하는 함수를 호출할 때는 다음 코드처럼 `try/catch` 블록으로 감싼다. 그러면 함수에서 익셉션이 발생할 때 적절히 대처할 수 있다.

```c++
try {
	cout << divideNumbers(2.3, 0.5) << endl;
	cout << divideNumbers(2.3, 0) << endl;
	cout << divideNumbers(4.5, 2.5) << endl;
} catch (const invalid_argument& exception) {
	cout << "Exception caught: " << exception.what() << endl;
} 
```

'divideNumbers()' 를 처음 호출할 때는 정상적으로 실행돼 결과가 화면에 출력된다. 두 번째로 호출할 때는 익셉션이 발생한다. 아무런 값도 리턴되지 않기 때문에 익셉션을 잡았다는 에러 메시지만 화면에 출력된다.

앞에서는 C++에서 기본으로 제공하는 `std::invalid_argument` 타입의 익셉션을 사용했는데, 기왕이면 발생할 수 있는 상황에 딱 맞게 익셉션 타입을 직접 정의해서 사용하는 것이 좋다. C++ 컴파일러는 발생 가능한 모든 익셉션을 꼭 잡도록 강제하지 않는다.

## 타입 추론 

**타입 추론**<sup>type</sup> <sup>inference</sup>이란 표현식의 타입을 컴파일러가 스스로 알아내는 기능이다.

### auto 키워드
`auto` 키워드는 다음과 같은 다양한 상황에서 사용한다.

- 함수의 리턴 타입을 추론한다.
- 구조적 바인딩에 사용한다.
- 표현식의 타입을 추론하는 데도 사용한다.
- 비타입 템플릿 매개변수의 타입을 추론하는데 사용한다.
- `decltype(auto)`에서 사용한다.
- 함수에 대한 또 다른 문법으로 사용한다.
- 제네릭 람다 표현식에서 사용한다.

나중에 특정 함수의 리턴 타입을 변경하더라도 코드에서 그 함수가 나온 모든 지점을 일일이 찾아서 고칠 필요 없이 간단히 수정할 수 있다.

하지만 `auto`로 표현식의 타입을 추론하면 함수에 지정된 레퍼런스나 `const` 한정자가 제거된다. 복제 방식으로 전달되지 않게 하려면 `auto&`나 `const auto&`로 지정한다.
```c++
#include <string>

const std::string message = "Test";

const std::string& foo()
{
	return message;
}
auto f1 = foo(): // auto를 지정하면 레퍼런스와 const 한정자가 사라지기 때문에 fl은 string 타입이 된다. 따라서 값이 복제돼버린다.
const auto& f2 = foo();
```

### decltype 키워드
`decltype`은 레퍼런스나 `const`지정자를 삭제하지 않는다는 점에서 `auto`와 다르다. 위의 `f2`를 다음과 같이 `decltype`으로 정의하면 `const string&` 타입이 돼 복제 방식으로 처리하지 않는다.

```c++
decltype(foo()) f2 = foo();
```

# C++의 객체지향 언어 특성
## 클래스 정의

**클래스**<sup>class</sup>란 객체의 특성을 정의한 것이다. C++에서 클래스를 선언하는 코드는 주로 헤더 파일(.h)에 작성하고, 구제적으로 구현하는 코드는 소스 파일(.cpp)에 작성한다.

클래스를 정의할 때는 먼저 클래스 이름부터 적는다. 그리고 중괄호 안에 이 클래스의 **데이터 멤버**<sup>data</sup> <sup>member</sup>(속성)와 **메서드**<sup>method</sup>(동작)을 선언한다. 각각의 데이터 멤버와 메서드마다 `public`, `protected`, `private` 등으로 접근 수준을 지정한다. 이때 레이블을 나열하는 순서를 따지지 않고, 중복해도 된다. `public`으로 지정한 멤버는 클래스 밖에서 접근할 수 있는 반면 `private`로 지정한 멤버는 클래스 외부에서 접근할 수 없다. 대체로 데이터 멤버는 모두 `private`로 지정하고, 외부에서 데이터 멤버를 접근하게 하려면 그 값을 가져오는 메서드(게터<sup>getter</sup>)나 설정하는 메서드(세터<sup>setter</sup>)를 정의하고 이를 `public`으로 지정한다.

```c++
#include <string>
class AirlineTicket
{
	public:
		AirlineTicket();
		~AirlineTicket();
    
		double calculatePriceInDollars() const;
    
		const std:: string& getPassengerName() const;
		void setPassengerName(const std::string& name);
    
		int getNumberOfMiles() const;
		void setNumberOfMiles(int miles);
    
		bool hasEliteSuperRewardsStatus() const;
		void setHasEliteSuperRewardsStatus(bool status);
    
	private:
		std::string mPassengerName;
		int mNumberOfMiles;
		bool mHasEliteSuperRewardsStatus;
}；
```

 클래스와 이름이 같고 리턴 타입이 없는 메서드를 **생성자**<sup>constructor</sup>라 부른다. 이 메서드는 해당 클래스의 객체가 생성될 때 자동으로 호출된다. 생성자와 형태는 같지만 앞에 틸데(`~`)를 붙인 메서드를 **소멸자**<sup>destructor</sup>라 부른다. 이 메서드는 객체가 제거될 때 자동으로 호출된다.

생성자로 데이터 멤버를 초기화하는 방법은 두 가지다. 권장하는 방법은 **생성자 이니셜라이저(ctor 이니셜라이저)**를 사용하는 것으로, 생성자 이름 뒤에 콜론(`；`)을 붙여서 표현한다.
```c++
AirlineTicket::AirlineTicket()
	: mPassengerName("Unknown Passenger")
	, mNumberOfMiles(0)
	, mHasEliteSuperRewardsStatus(false)
{
}
```

본문에서 초기화 하는 방법이다.

```c++
AirlineTicket::AirlineTicket()
{
	// 데이터 멤버 초기화
	mPassengerName = "Unknown Passenger";
	mNumberOfMiles = 0;
	mHasEliteSuperRewardsStatus = false;
}
```

생성자에서 다른 일은 하지 않고 데이터 멤버를 초기화 하는 일만 한다면 굳이 생성자를 따로 정의할 필요가 없다.
```c++
private:
	std:string mPassengerName = "Unknown Passenger";
	int mNumberOfMiles = 0;
	bool mHasEliteSuperRewardsStatus = false;
```

파일을 닫거나 메모리를 해제하는 등의 정리 작업이 필요하다면 소멸자를 정의한다.

### 클래스 사용하기
`AirlineTicket`객체를 하나는 스택 기반으로, 다른 하나는 힙 기반으로 생성한다.

```c++
AirlineTicket myTicket; // 스택 기반 AirlineTicket
myTicket.setPassengerName("Sherman T. Socketwrench");
myTicket.setNumberOfMiles(700);
double cost = myTicket.calculatePriceInDollars();
cout << "This ticket will cost $" << cout << endl;

// 스마트 포인터를 사용한 힙 기반
AirlineTicket auto myTicket2 = make_unique<AirlineTicket>();
myTicket2->setPassengerName("Laudimore M. HaUidue");
myTicket2->setNumberOfMiles(2000);
myTicket2->setHasEliteSuperRewardsStatus(true);
double cost2 = myticket2->calculatePriceInDollars();
cout << "This other ticket will cost $" << cost2 << endl;
```



## 유니폼 초기화
CmII 이전에는 타입의 초기화 방식이 일정하지 않았다.
```c++
struct CircleStruct
{
	int x, y;
	double radius;
}；
    
class CircleClass
{
	public:
		CircleClass(int x, int y, double radius)
            : mX(x), mY(y), mRadius(radius) {}
    private:
		int mX, mY;
		double mRadius;
}
```

C++11 이전에는 타입 변수를 초기화하는 방법이 서로 달랐다.
```c++
CircleStruct myCircle1 = {10, 10, 2.5};
CircleClass myCircle2(10, 10, 2.5);
```

C++11 부터 타입을 초기화할 때 `{...}`문법을 사용하는 유니폼 초기화<sup>uniform</sup> <sup>initialization</sup>(균일 초기화, 중괄호 초기화)를 따르도록 통일됐다. 구조체나 클래스뿐만 아니라 C++에 있는 모든 대상을 초기화하는 데 적용된다. 변수를 영 초기화할 때도 적용할 수 있다. 동적으로 할당되는 배열을 초기화할 때도 적용할 수 있다. 클래스 멤버인 배열을 생성자 이니셜라이저로 초기화할 때도 사용할 수 있다.
```c++
CircleStruct myCircle1{10, 10, 2.5};
CircleClass myCircle2{10, 10, 2.5};
int a = 3;
int b(3);
int c = {3}; // 유니폼 초기화
int d{3}; // 유니폼 초기화
int e{}; // 영 초기화
int* pArray = new int[4]{0, 1, 2, 3}; // 동적 배열
```

유니폼 초기화를 사용하면 **축소 변환**<sup>narrowing</sup>(**좁히기**)을 방지할 수 있다.

## 직접 리스트 초기화와 복제 리스트 초기화

이니셜라이저는 다음 두 가지가 있으며, 이니셜라이저 리스트를 중괄호로 묶어서 표현한다.

- 복제 리스트 초기화(copy list initialization) : `T obj = {arg1, arg2, ... };`
- 직접 리스트 초기화(direct list initialization) : `T obj {arg1, arg2, ... };`

C++17 이전에는 복제 리스트 초기화와 직접 리스트 초기화 모두 `initiaiizer_list<>`로 처리했다.

C++17부터 `auto`는 직접 리스트 초기화에 대해 값 하나만 추론한다. 복제 리스트 초기화에서 중괄호 안에 나온 원소는 반드시 타입이 모두 같아야 한다.
```c++
// 복제 리스트 초기화
auto a = {11};	    // initializer_list<int>
auto b = {11, 22};	// initializer_list<int>

// 직접 리스트 초기화
auto c {11};	    // int
auto d {11, 22};	// 원소가 너무 많다는 에러가 발생한다.
auto e = {11, 22.33}; // 컴파일 에러
```

## 표준 라이브러리

C++는 표준 라이브러리를 제공한다. 여기에는 코드에서 쉽게 가져다 쓸 수 있도록 구성된 유용한 클래스가 다양하게 정의돼 있다.
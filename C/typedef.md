typedef
============

개념
-----------
typedef문을 이용하면 프로그래머가 자신의 데이터형을 선언할 수 있습니다. 

### 선언하기
typedef를 이용해 새 데이터형을 선언하려면 아래와 같습니다.
```c
typefed unsigned int UINT;
// typedef 원래데이터형 새데이터형이름
```
typedef문은 일반적으로 #include, #define문 다음에 위치합니다.
typedef 다음에 C언어의 기본데이터형을 적고, 그다음에 새 데이터형으로 사용할 이름을 입력합니다. 
명령행의 끝에는 세미콜론을 붙입니다.

C언어에는 없는 bool형을 선언할때는 아래와 같이 선언합니다.
```c
#include <stdio.h>

#define ture  1
#define false 0

typedef char bool;

int main()
{
  bool trueOrFalse = false;

  tureOrFalse = true;
  if (tureOrFalse == true)
    printf("True\n");
}
```

일반적으로, typedef문은 구조체 또는 공용체에 많이 사용합니다. 
```c
struct firstStruct
{
  int a;
  int b;
};
// 위 구조체의 선언방법은 struct firstStruct fir; 형태입니다.

typedef struct secondStruct
{
  int a;
  int b;
} secondStruct;
// 위 구조체의 선언방법은 secondStruct sec; 형태입니다.

typedef struct
{
  int a;
  int b;
} thirdStruct;
// 위 구조체도 thirdStruct third; 형태로 선언가능합니다.
```
위 예제와 같이, typedef문을 사용하면 구조체, 공용체등을 선언할때 선언문을 간결하게 할 수 있습니다.

### typedef를 이용한 구조체선언시 주의할 점
가끔, 자기 참조 구조체(구조체 내부변수 중 자기 자신을 가르키는 구조체포인터를 포함하는 구조체)를 선언해 사용할 때가 있습니다. typedef를 이용해 구조체를 선언할땐 주의해야합니다.
```c
typedef struct
{
  str *parent; // 으잉? 에러발생
  struct str *parent; // 이것도 에러발생!
} str;
```
위 예제처럼 간결하게 쓰려고 typedef struct ~~부분마저 생략해 버려서 typedef로 새로운 데이터형을 만들기도 전에 사용해 버려서 에러가 발생했습니다.

위와 같은 상황을 피하려면, typedef부분에도 구조체 명을 적어주면 됩니다. 
typedef와 struct의 이름이 같더라도 상관 없습니다. 단, 해당 포인터는 struct를 붙여서 선언해야 한다는 점입니다.
```c
typedef struct str
{
  str *parent; // 여전히 에러발생.
  struct str *parent; // 드디어 에러회피!
} str;
```

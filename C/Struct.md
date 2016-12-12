구조체
=========

예제
--------
```c
#include <stdio.h>

struct point
{
  int math;
  int english;
};

main()
{
  struct point P1;
  
  P1.english = 99;
  P1.math = 35;
  
  printf("수학: %d, 영어: %d", P1.math, p1.english);
}
```

문법
--------
구조체는 여러 자료형의 변수들을 배열처럼 일렬로 나열한것과 같습니다. 
여러 변수들을 하나로 묶어놓은 템플릿으로도 볼 수 있죠.
      
### 구조체의 선언
      struct strName { ... }; // struct 구조체이름 { 변수들 };
의 형태로 선언합니다. 중괄호로 구조체내의 변수들을 묶습니다. 
구조체내에 들어가는 변수들의 타입은 모두 달라도 상관없습니다. 

주의해야할것은 구조체의 중괄호가 끝난뒤에 세미콜론을 붙여야 합니다. 

### 구조체 변수의 선언
      struct strName strVariable; // struct 구조체이름 구조체변수이름;
의 형태로 선언합니다. 

### 구조체 변수의 사용
      strVariable.a = 0;
      printf("%d", strVariable.a);
해당 구조체변수에 접근하려면 '변수명.변수명'의 형태로 사용합니다.

### 구조체 배열?
구조체변수도 배열로 선언할 수 있습니다.
일반 배열을 선언하듯이 구조체변수이름 뒤에 대괄호[n]를 붙여주면 됩니다. 
사용할 때도

      strVar[n].varName
의 형태로 사용합니다.

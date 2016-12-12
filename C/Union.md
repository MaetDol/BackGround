공용체
==========

예제
-------
```c
#include <stdio.h>

union myUnion
{
   char c;
   int i;
   float f;
};

main()
{
   union myUnion u;
   u.c = 3;
   u.i = 77;
   u.f = 3.14;

   printf("%d, %d, %d\n", u.c, u.i, u.f);
}
```

문법
-------
공용체는 구조체와 비슷해보이지만, 성지은 전혀다릅니다.

### 공용체의 선언
      union uniName { ... }; // union 공용체이름 { 변수들 };
선언 방식은 구조체와 거의 흡사합니다. 맨 마지막에 세미콜론이 들어간다는 점까지 말이죠. 

### 공용체 변수의 선언
      union uniName u; // union 공용체이름 공용체변수이름;
맨 앞에 'union'을 붙여줘야합니다.

### 공용체 변수의 사용
      u.c = 3;
      u.i = 6;
공용체의 각 변수에 접근하려면 점 연산자를 이용하면 됩니다.

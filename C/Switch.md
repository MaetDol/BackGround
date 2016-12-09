switch문
=========
딸깍, 딸깍

예제
----------
```c
#include <stdio.h>

main()
{
  char c = 'c';
  
  switch(c)
  {
  case 'a':
    printf("It is A!");
	break;
  case 'b':
    pritnf("It is B!");
    break;
  case 'c':
    printf("It is C!");  
    break;
  default:
    printf("어...음..");
  }
}
```

문법
------
조건문은 정수형 그리고 문자형만 비교 가능합니다. 
case문 내부의 마지막에 break문을 넣지 않으면, 아래에 있는 케이스문까지 모두 검사하고 실행합니다. 
default는 if문의 else 처럼 조건에 맞는 케이스가 없을경우 실행하는 파트입니다.
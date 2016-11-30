문자열
========

예제
--------
```c
#include <stdio.h>

main() {
   char s[] = "This is String"; // 요건 변수
   char* s2 = "This is Constant String"; // 요건 상수입니다.
   printf("%s", s);
   printf("이것 또한 문자열입니다");
}
```

문법
-----------
문자열은 문자들로 이루어진 배열입니다.
문자열은 쌍따음표(")로 감싸면 문자열이 됩니다.
#### 배열로 문자열 만들기
#### 상수로 문자열 만들기
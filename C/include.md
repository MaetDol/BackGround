include
========

include 란?
-----------
전처리기(샾을 붙인 지시문)중 하나인 #include는 다른 헤더파일(또는 소스코드)을 포함한다는 뜻을 가진 지시문입니다. 
해당 지시문을 사용하면 include하는 파일의 내용을 그대로 가져와, include가 있는 부분에 붙여넣습니다. 예로 아래 예제를 참고해 주세요.
```c
// 여긴 파일 b.c 구간입니다.
void b() { printf("Hi! I'm in b\n"); }
// b.c 구간 끝

// 여긴 파일 a.c 구간입니다.
#include <stdio.h>
#include "b.c"

int main()
{
	b();
}
```
위 예제의 a.c파일은 아래와 같습니다.
```c
#include <stdio.h>

void b() { printf("Hi! I'm in b\m"); }

int main()
{
	b();
}
```

사용 방법
-----------
include를 사용하는 방법은 두가지가 있습니다. 

* 첫번째는 꺾쇠괄호 이용하기
* 두번째는 쌍따옴표 이용하기

두 방법은 서로 인클루드하는 파일의 검색 방법이 다릅니다.

```c
#include <stdio.h>
```
꺾쇠괄호로 사용할 경우, INCLUDE 환경 변수(C 표준 라이브러리가 있는 곳)에 지정된 경로에서 검색합니다.

```c
#include "test.h"
```
쌍따옴표로 사용한 경우는 해당 코드(#include "test.h")를 포함하는 파일이 있는 경로에서 찾습니다.

쌍따옴표를 이용한 경우에는 경로를 같이 지정할 수 있습니다(꺾쇠괄호는 모르겠습니다). 파일이름과 상대경로를 함께 적으면 됩니다. 예시는 아래와 같습니다.
```c
#include "../test.h"
```

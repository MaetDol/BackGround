import
=========

예제
-------
```python
import abclib
abclib.afunc()
abclib.bfunc()
```

문법
---------
### 임포트 방법
```python
import 모듈이름
import 모듈이름.서브모듈이름
from 모듈이름 import 모듈이름 또는 함수이름
import 모듈이름 as 닉네임
```

		import sys
1. 기본적인 임포트 방법입니다.
기본 모듈이 아닌 자신이 만든 소스코드 파일을 같은 폴더에 두면 
기본 모듈을 임포트하는것처럼 임포트 할 수 있습니다. 
해당 모듈의 함수를 사용할 때에는

		모듈명.함수()
형식으로 사용합니다.

		import os.path
2. 기본 모듈인 os의 서브 모듈인 path를 임포트 하는 예시

		from time import time
3. time 모듈에 있는 time()함수만 임포트 하여 함수 이름만으로 호출하려 사용 하는 경우

		time()
3번과 같이 임포트 할 경우 위 예제와 같이 사용 가능합니다.

		from time import *
별표*를 사용함으로써 time 모듈에 있는 모든 함수를 3번처럼 모듈명없이 사용 가능합니다.

		import time as t
4. 모듈 이름을 단축설정하는 경우. 
위 예제는 time이라는 모듈을 t로 단축시켜 호출 할 수 있습니다.

		t.time()
		

### 패키지, Package
파이썬 모듈을 계층적인 디렉터리 형태로 구성한 것을 파이썬 패키지라 합니다. 

디렉터리가 파이썬 패키지로 인식되려면 각 디렉터리마다 '__init__.py'라는 파일이 있어야 합니다. 
해당 파일의 내용은 보통 

		version = 1.0
과 같은 텍스트 한 줄이면 충분합니다.

```
패키지 계층 구조 예시

testPackage
  test.py
  
  myPackage   <----- 하나의 패키지
    a.py
    b.py
    __init__.py   <- 내용 : version=1.0
    
test.py 내용 :
  import myPackage.a
  import myPackage.b
  
  myPackage.a.afunc()
  myPackage.b.bfunc()
```
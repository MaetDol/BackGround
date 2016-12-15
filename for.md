for문
=======

예제
-------
```python
for 변수 in 범위:
	반복해서 실행할 코드

for 변수 in range(n):
    반복해서 실행할 코드
```

사용가능한 객체들
-------------
- 문자열
- 리스트, 튜플
- 사전
- range() 함수

### else:
for문에서 break 등에 의해 중단되지 않고 정상적으로 
for문이 종료되었을때 else문으로 진입됩니다.

		for i in range(3):
			print(c)
		else:
			print('End')
		
		# 출력 : 
		# 0
		# 1
		# 2
		# End
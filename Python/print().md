print()
===========

문법
----------
특정 값, 변수를 출력할 때 사용됩니다. 
소괄호 속에 인자로 출력할 값을 넣으면 됩니다. 

리스트, 사전, 튜플 등 print() 인자로 해당 변수를 
대입하면 특정 출력 형식으로 출력됩니다.

- 리스트 출력 예
		list = [0, 1, 2, 'a', 'b']
		print(list)
		print(list[2])
		
		# 출력 :
		# [0, 1, 2, 'a', 'b']
		# 출력2 :
		# 2

- 사전 출력 예
		dict1 = {'id1':'val1', 'id2':'val2'}
		print(dict1)
		print(dict1['id1'])
		print(dict1.keys())
		
		# 출력1 :
		# {'id1':'val1', 'id2','val2'}
		# 출력2 :
		# val1
		# 출력3 :
		# dict_keys(['id1', 'id2'])

### print의 자동 줄 바꿈을 원하지 않을때?
print()의 두 번째 인자로 end=''를 추가하면 됩니다.
		
		print('AB', end='')
		print('CD')
		# 출력 :
		# ABCD
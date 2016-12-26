string
========

### string.replace()
문자열 객체의 replace()는 문자열에 있는 
문자(또는 문자열)들을 특정 문자(또는 문자열)로 교체합니다.

		msg = 'Hello, I'm Nero'
		msg.replace('o', 0)
		msg # 출력 : Hell0, I'm Ner0
		msg.replace('l', '!')
		msg # 출력 : He!!0, I'm Ner0
위 예제처럼, 해당 문자(또는 문자열)이 여러개가 있을경우 전부 
교체합니다.
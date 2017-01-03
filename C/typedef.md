typedef
============

����
-----------
typedef���� �̿��ϸ� ���α׷��Ӱ� �ڽ��� ���������� ������ �� �ֽ��ϴ�. 

### �����ϱ�
typedef�� �̿��� �� ���������� �����Ϸ��� �Ʒ��� �����ϴ�.
```c
typefed unsigned int UINT;
// typedef ������������ �����������̸�
```
typedef���� �Ϲ������� #include, #define�� ������ ��ġ�մϴ�.
typedef ������ C����� �⺻���������� ����, �״����� �� ������������ ����� �̸��� �Է��մϴ�. 
������� ������ �����ݷ��� ���Դϴ�.

C���� ���� bool���� �����Ҷ��� �Ʒ��� ���� �����մϴ�.
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

�Ϲ�������, typedef���� ����ü �Ǵ� ����ü�� ���� ����մϴ�. 
```c
struct firstStruct
{
  int a;
  int b;
};
// �� ����ü�� �������� struct firstStruct fir; �����Դϴ�.

typedef struct secondStruct
{
  int a;
  int b;
} secondStruct;
// �� ����ü�� �������� secondStruct sec; �����Դϴ�.

typedef struct
{
  int a;
  int b;
} thirdStruct;
// �� ����ü�� thirdStruct third; ���·� ���𰡴��մϴ�.
```
�� ������ ����, typedef���� ����ϸ� ����ü, ����ü���� �����Ҷ� ������ �����ϰ� �� �� �ֽ��ϴ�.

### typedef�� �̿��� ����ü����� ������ ��
����, �ڱ� ���� ����ü(����ü ���κ��� �� �ڱ� �ڽ��� ����Ű�� ����ü�����͸� �����ϴ� ����ü)�� ������ ����� ���� �ֽ��ϴ�. typedef�� �̿��� ����ü�� �����Ҷ� �����ؾ��մϴ�.
```c
typedef struct
{
  str *parent; // ����? �����߻�
  struct str *parent; // �̰͵� �����߻�!
} str;
```
�� ����ó�� �����ϰ� ������ typedef struct ~~�κи��� ������ ������ typedef�� ���ο� ���������� ����⵵ ���� ����� ������ ������ �߻��߽��ϴ�.

���� ���� ��Ȳ�� ���Ϸ���, typedef�κп��� ����ü ���� �����ָ� �˴ϴ�. 
typedef�� struct�� �̸��� ������ ��� �����ϴ�. ��, �ش� �����ʹ� struct�� �ٿ��� �����ؾ� �Ѵٴ� ���Դϴ�.
```c
typedef struct str
{
  str *parent; // ������ �����߻�.
  struct str *parent; // ���� ����ȸ��!
} str;
```

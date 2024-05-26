# Simple-Reversing
간단한 리버싱 실습

리버싱1의 소스코드

#include <windows.h>
#include <stdio.h>
#include <tchar.h>

int _tmain()
{
	MessageBox(NULL, _T("Hello World!"), _T("Hello World!"), MB_OK);

	return 0;
}

## 설명
위의 소스코드를 보면 메세지박스를 띄어서 Hello World! 라는 메세지를 출력하는 코드이다
위의 코드에서 Hello World! 라는 메세지를 Goodmorrning으로 바꿀 것이다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/616b6e23-e98d-469e-892e-09da993a6f2e)
HxD 프로그램으로 리버싱1의 실행파일을 불러와 실행시킨 모습이다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/69627351-ba37-4599-b222-7e8a534698fd)
메뉴에서 찾기 탭을 눌러서 Hello World를 찾아준다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/3e1ff990-a019-4a10-9cff-716ddbcef5c1)
Hello World를 찾았으면 이를 Goodmorrning으로 바꿔준다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/3bd6364f-17a6-46ba-b0cc-5769c3ad31b9)
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/5a268e72-5730-4052-938a-4abe65652489)

이처럼 Goodmorrning으로 바뀐 모습을 볼 수 있다

리버싱2의 소스코드

#include <windows.h>
#include <stdio.h>
#include <tchar.h>

int _tmain()
{
	int nSerial = 12345;
	int nInput = 0;

	printf("input Serial ( 5 numbers ) : ");

	scanf_s("%d", &nInput);

	if (nSerial == nInput)
		MessageBox(NULL, _T("Correct Serial Number"), _T("Check"), MB_OK);
	else
		MessageBox(NULL, _T("Wrong Serial Number"), _T("Check"), MB_OK);

	return 0;
}


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
위의 코드에서 Hello World! 라는 메세지를 Goodmorning!으로 바꿀 것이다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/616b6e23-e98d-469e-892e-09da993a6f2e)
HxD 프로그램으로 리버싱1의 실행파일을 불러와 실행시킨 모습이다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/69627351-ba37-4599-b222-7e8a534698fd)
메뉴에서 찾기 탭을 눌러서 Hello World를 찾아준다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/b1b13047-596e-4538-b7d9-8634f5b5125b)
Hello World를 찾았으면 이를 Goodmorning으로 바꿔준다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/3bd6364f-17a6-46ba-b0cc-5769c3ad31b9)
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/c52a34df-be8a-46fe-ade8-91c811bdebf9)


이처럼 Goodmorning!으로 바뀐 모습을 볼 수 있다

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

## 설명
시리얼 넘버가 12345로 설정이 되어 있고 사용자로부터 시리얼 넘버를 입력받아 12345와 같은지 비교하는 코드이다
x64dbg로 시리얼 넘버를 크랙하는 간단한 작업을 수행할 것이다

x64dbg를 실행시켜서 실행파일을 불러온다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/1c6aae8d-c573-48cd-aabf-913d1b7756ae)
그 다음 우클릭 후 다음을 찾기->모든 유저 모듈->문자열 참조를 눌러서 시리얼 넘버를 입력받는 곳으로 간다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/a40413bd-22f2-4f90-a495-2999e7e87dfe)
해당 코드부분으로 온 후 중단점을 설정한다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/95d936c3-8603-495c-80b0-65c49a232847)

그 다음 코드를 실행시켜서 시리얼 넘버를 입력받는 단계까지 오면 틀린 시리얼 넘버를 입력한다
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/91d3b7c7-9a89-4bb1-aa58-8e45327f7482)

이렇게 입력한 후 엔터를 누르면 'je' 부분으로 오는데 이는 입력받은 값과 시리얼 넘버를 비교하여 같으면 점프를 뛰는 opcode이다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/da3fcf61-929f-4370-b2b2-3cf9af8ef469)
![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/66cad0e0-df2f-41d3-98fc-e5297330a49f)

여기서 0으로 되어있는 제로 플래그를 1로 바꾸면 틀린 시리얼 넘버를 입력받아도 제로 플래그가 1이기 때문에 참으로 인식되어 점프를 뛰게 된다

![image](https://github.com/dbs1339/Simple-Reversing/assets/128207214/78051c63-21d0-4e28-890c-f0969108df78)

이렇게 Corret Serial Number 문구가 뜨게 된다

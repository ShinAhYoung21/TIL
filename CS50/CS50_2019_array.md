# 배열 Array

> [JavaScript에서의 배열(링크)](https://github.com/ShinAhYoung21/TIL/blob/main/JS/js_7_array.md))내용과 비교해보는 것이 학습에 도움 될 듯!

## 목차

* [컴파일링](#컴파일링)
    * [전처리 Precompile](#전처리)
    * [컴파일 Compile](#컴파일)
    * [어셈블 Assemble](#어셈블)
    * [링크 Link](#링크)
* [버그 & 디버깅](#버그와-디버깅)
    * [디버깅의 기본](#디버깅의-기본)
        * [help50 : 함수로 컴파일 오류 해석](#help50)
        * [printf : 변수 직접 확인](#printf)
    * [GDB : 자주 쓰이는 디버거](#디버거-gdb)
* []()
----

## 컴파일링

> 앞서 C언어 학습할 때 함께 다루기는 했지만, 정리하는 겸!

* `make 프로그램`을 이용하면 이 모든 컴파일 과정을 자동으로 처리할 수 있다.
    * 하지만, 작동 원리를 보기 위해, `clang`활용 방법을 노트정리했다!
```c
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```
* `stdio.h`는 `헤더 파일`이며(*그래서 파일명이 `.h`로 끝나는 듯*), c언어로 작성되어 있다.
    * printf함수의 프로토타입이 있다. 그래서 Clang으로 프로그램을 컴파일할 때 *printf가 무엇인지 알려주는 역할*을 한다.
    ```
    코드를 clang hello.c로 컴파일하고 ./a.out 명령으로 프로그램을 실행할 때,
    이 과정(컴파일링)은
    컴퓨터가 이해하는 0과 1로 가득찬 파일 a.out을 생성하여 실행 가능하게 한다.
    ```
```c
// hello라는 이름으로 컴파일하기
clang -o hello hello.c

// cs50라이브러리를 사용한 프로그램을, hello라는 이름으로 컴파일하기
clang -o hello hello.c -lcs50 
```
* 아래는 make 또는 clang으로 프로그램 실행할 때 거치는 네 단계로, 이 절차를 거치면 `실행 가능한 파일`이 완성된다.
    1. 전처리
    2. 컴파일링
    3. 어셈블링
    4. 링킹

### 전처리

* `Precompile`
* 전처리기에 의해 수행된다.
* C의 소스코드 중, `#`로 시작되는 부분.
* **실질적인 컴파일 이뤄지기 전에 무언가를 실행하라고 알려**준다.
    * 예) `#include`는 전처리기에게 다른 파일의 내용을 (현재 파일에)포함시키라고 알려주는 것이다.
* 이 결과, **전처리한 소스코드가 생성**된다.

### 컴파일

* `Compile`
* `컴파일러`라는 프로그램을 통해 **C코드를 `어셈블리어`라는 저수준 프로그래밍 언어로** 컴파일하는 작업이다.
    * `어셈블리`는 C보다 연산 종류가 적으나, 여러 연산을 함께 쓰면 C에서 할 수 있는 모든 것을 수행 가능.
    * C코드를 어셈블리 코드로 변환함으로써, 컴파일러는 소스코드를 **컴퓨터가 이해할 수 있는 언어와 최대한 가까운 프로그램으로** 만들어준다.
* 참고로, `컴파일`이란 광의로는 **소스코드에서 오브젝트 코드로 변환하는 전체 과정**, 협의로는 **전처리한 소스코드를 어셈블리 코드로 변환시키는 단계**를 의미한다.

### 어셈블

* `Assemble`
* **어셈블리 코드를 오브젝트 코드로 변환**
* `어셈블러`라는 프로그램이 수행하는 작업이다.
* 소스코드에서 오브젝트 코드로 컴파일될 파일이 단 하나라면, 컴파일 작업은 여기서 종료!
    * 아니면, `링크`라고 하는 다음 단계가 추가된다.

### 링크

* `Link`
* **프로그램이 여러 개의 파일로 이루어져** 있어서 **하나의 오브젝트 파일로 합쳐져야 한다면** 이 단계를 거쳐야 한다.
    * 참고로, **여러 개의 파일**에는 `math.h`또는`cs50.h`같은 `라이브러리`를 포함한다.
    * 예) 컴파일 중에 cs50 라이브러리를 링크하면, 오브젝트 코드는 `GetInt()`나 `GetString()` 등 *cs50 라이브러리에 속한 함수들*을 어떻게 실행할 지 알 수 있게 된다.

[목차로 이동](#목차)
----

## 버그와 디버깅

* `버그 bug` === **코드에 들어있는 오류**
    * 프로그램 실행 실패, 프로그래머가 원하는 대로 동작하지 않는 원인
    * My note: 프로그래머를 bugHunter라고 표현하는 티셔츠 디자인이 있다.ㅋㅋㅋㅋ
        ![프로그래머는 bug hunter](https://i.pinimg.com/736x/2e/95/83/2e9583c47ef0a602c148ea29bfbdf18b.jpg)
* `디버깅 debugging` === **코드에 있는 버그를 식별하고 고치는 과정**
    * `디버거`라는 프로그램을 사용한다.

### 디버깅의 기본

* 사람보다 프로그램의 연산 속도가 빠르기 때문에, 프로그램 실행만으로는 버그 찾고 수정하기가 어렵다.
    * 그래서 `디버거`를 사용해서 디버깅을한다.
        * `중지점`을 설정할 수 있다.
            * 중지점 === **프로그램이 멈추는 특정 지점**
            * 이를 통해, 멈춘 지점에서 무슨 일이 일어나는지 찬찬히 볼 수 있다.
        * 프로그램을 한 번에 한 행씩 실행해볼 수 있다.
            * 프로그램 절차를 단계별로 확인할 수 있다.

#### help50

```c
// help50
int main(void)
{
    printf("hello, world\n");
}

// 이 코드 컴파일 후 실행시 오류발생
// 에러 메시지: implicitly declaring library function 'printf
```
* 문제 원인: **stdio.h 라이브러리를 포함하지 않아서** (*printf함수를 사용하지 못한다는 의미이다.*)
    * 이런 에러메시지 이해가 어려울 땐, `help50`프로그램을 사용한다. 그러면, 컴파일시 생기는 오류를 해석해준다.
    ```
    help50 make 파일명
    ```

#### printf

```c
// 의도는 #을 10번 출력하는 것
#include <stdio.h>

int main(void)
{
    for (int i = 0; i <= 10; i++)
    {
        printf("#\n");
    }
}
// 실행 결과, #이 11번 출력됨
```
* `help50`과 같은 함수로 해결하지 못하는 경우, **의심가는 변수를 출력해서 확인**해보는 방법.
```c
// 변수 i를 출력
#include <stdio.h>

int main(void)
{
    for (int i = 0; i <= 10; i++)
    {
        printf("i is now %i: ", i);
        printf("#\n");
    }
}
// 11까지 출력된다
// for문 두번째 조건을 i < 10으로 수정해야 한다는 것을 알 수 있다
```

#### debug50

> 이건 cs50 IDE에서 사용할 수 있는 프로그램이다. (그래서 따로 노트정리는 안 할 것이다)
> 필요하다면, [해당 부분 학습자료(링크)](https://www.boostcourse.org/cs112/lecture/119012/?isDesc=false)가장 아래 단락 참고!

### 디버거 GDB

* 자주 쓰이는 디버거 중 하나로, C프로그램에 이를 실행시키려면, 프로그램 컴파일부터 해야한다. 그 다음, ~./프로그램_이름~이 아니라, `gdb 프로그램_이름`을 입력한다.
* GDB가 열리면, 가장 먼저 **중지점 설정**을 한다.
    * 이때, 문제가 어디에서 발생했을지 짐작이 가는 부분이 있으면, **그 전에 있는 행에 중지점 설정**하는 게 좋다. *문제의 부분으로 예측되는 지점에 들어섰을 때 어떻게 변하는지*확인해볼 수 있기 때문이다.
    * 문제 부분이 확실하지 않다면, `main 함수의 첫행`에 중지점을 설정하여, 처음부터 모든 코드를 살펴본다.
> GDB명령어는 필요할 때 구글링해서 보도록 한다!

[목차로 이동](#목차)
----

[목차로 이동](#목차)
----

## 어록
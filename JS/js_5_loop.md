# 반복문 Loop / iterate

> [조건문](https://github.com/ShinAhYoung21/TIL/blob/main/JS/js_4_cond.md)은 컴을 똑똑하게, 반복문은 컴을 강력하게 만든다!
    조건문, 반복문이 프로그래밍의 양대산맥이라고 함!

* **간략 목차**
    * [while문](#while)
    * [for문](#for)
----

## 기본 문법: while, for

### while

```javascript
while(조건){
    반복해서 실행할 코드
}
```
* 조건에는 `boolean`타입 데이터가 입력되어야 한다.
* 조건이 `true`에서 `false`가 될 때까지 *반복 실행할 코드*가 반복된다.

#### 세부 구성

```javascript
var i = 0; // 초기화
while(i < 3/*반복조건*/){
    document.write("hello friends <br />");
    i = i + 1; //반복 실행
}
```
* `초기화`: 언제까지 반복할지 **기준점**을 제공한다. initialize.
* `반복조건`: 반복을 계속 실행할 것인가 판별한다.
* `반복실행`: 반복을 실행할 때마다 i값을 갱신한다.

#### while 예1: 무한루프

* 조건이 빼박`true`(true로 고정된 상태)이면, 무한반복된다.
* 반복이 끝 없어서 컴퓨터에 부담을 주게 된다.
* 프로그래밍 작성 시 발생하기 쉬우면서 **심각한 상황**
* 따라서, 조건이 적당한 때에 `false`가 되어야 한다!
    ```javascript
    while(true){
        document.write("coding everybody <br />");
    }
    ```
* **참고**
    * 무한반복 실습 전, **저장되지 않은 작업은 모두 정리한 후에 명령 실행하기!**
    * 웹 브라우저는 무한반복을 허용하지 않아서, 어느 정도 시간 지나고 나면 스크립트를 종료할지 묻기 때문이다. 그러니까, 미리 정리해두고 실행하기!

#### 반복조건: 언제까지 반복문을 실행할 것인가

* 무한 루프를 예방하기 위해, 반복문을 중단시키는 방법!
* 위의 [예1](#while-예1:-무한루프)을 보완한 버전
    * i 값이 10에 도달하는 때부터 반복이 중지된다.
    * 즉, 0부터 9까지 10회 반복된다 (**0부터 갯수를 세니까**)
    ```javascript
    var i = 0;
    while(i < 10){
        document.write("coding everybody <br />");
        i = i + 1;
    }
    ```
* `매우유용`: 반복할 코드에 `+i+`추가하면, 반복되는 문구 옆에 i값이 같이 출력된다.
    * 테스트할 때 유용할 것 같다. 그래서 메모해둔다!
    ```javascript
    var i = 0;
    while(i < 10){
        document.write("coding everybody "+i+"<br />");
        i = i +1;
    }
    /* 출력값:
    coding everybody 0
    coding everybody 1
    coding everybody 2
    coding everybody 3
    coding everybody 4
    coding everybody 5
    coding everybody 6
    coding everybody 7
    coding everybody 8
    coding everybody 9
    */
    ```

#### while문의 단점

* 코드가 길어지면, `초기화, 반복조건, 반복실행`을 한 눈에 보기 어려워 문법 오류 가능성이 높아진다.
* 이 문제를 `for문`으로 해소할 수 있다.
    * 초기화, 반복조건, 반복실행 내용을 **통합시켜서 표현**하기 때문이다.
----

### for

((for문부터 이어서 복습!!!))

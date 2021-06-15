# 반복문 Loop / iterate

> [조건문](https://github.com/ShinAhYoung21/TIL/blob/main/JS/js_4_cond.md)은 컴을 똑똑하게, 반복문은 컴을 강력하게 만든다!
    조건문, 반복문이 프로그래밍의 양대산맥이라고 함!
> 반복문은 **배열, 객체와 결합**해서 쓸 때 진가를 발휘한다.
    > **특히 `배열`!**

* **간략 목차**
    * [while문](#while)
    * [for문](#for)
    * [반복문의 제어](#반복문-제어)
        * [break: 강제 종료](#제어문1_break)
        * [continue: 스킵하고 진행](#제어문2_continue)
    * [반복문의 중첩](#반복문-중첩)
        * [예제_100번 쓰기](#예제1_100번-쓰기)
    * 
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

* 참고로, 변수로는 `i`를 관습적으로 쓴다. iterate(반복하다)에서 따온 듯.

#### while 예1: 무한루프

* 조건이 빼박`true`(true로 고정된 상태)이면, 무한반복된다.
* 반복이 끝 없어서 컴퓨터에 부담을 주게 되기 때문에, 프로그래밍 작성 시 발생하기 쉬우면서 **심각한 상황**이라고 할 수 있다.
* 따라서, 조건이 적당한 때에 `false`가 되도록 반복문을 구성할 필요가 있다!
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
* `매우유용`: 반복할 코드에 `+i+`추가하면, **반복되는 문구 옆에 i값이 같이 출력**된다.
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

#### 참고: JavaScript를 활용해서 HTML을 프로그래밍적으로 생성하는 방법

```html
<!doctype html>
<html>
    <head>
    </head>
    <body>
        <script type="text/javascript">
            document.write("Coding everybody <br/>");
        </script>
    </body>
</html>
```
* `script`태그 아래에서 `document.write`부분이 JS명령어, `Coding everybody<br/>`부분이 문자열이다.

#### while문의 단점

```javascript
var i = 0; // 초기화
while(i < 3/*반복조건*/){
    document.write("hello friends <br />");
    i = i + 1; //반복 실행
}
```
* 코드가 길어지면, `초기화, 반복조건, 반복실행`을 한 눈에 보기 어려워 **문법 오류 가능성이 높아진다.**
* 이 문제를 **`for문`으로 해소할 수 있다.**
    * 초기화, 반복조건, 반복실행 내용을 **통합시켜서 표현**하기 때문이다.
----

### for

```javascript
var i = 0;
while(i < 10){
    document.write("coding yeah "+i+"<br />");
    i = i +1;
}
```
```javascript
for(var i = 0; i < 10; i = i +1)
// 순서대로 (초기화; 반복조건; 반복실행)
```
* 위 두 예제는 실행결과는 같다.
* `for문`의 경우, 반복문의 조건들을 한눈에 보기 편리하다.
* 주의사항은
    * 반복문 괄호 안의 요소들을 구분할 때 `;`를 빼먹지 않고 쓰기!
    * 맨 끝에는 `;`붙이지 않기! (붙여봤더니 에러난다ㅋㅋㅋㅋ)
* 언제나 for문을 쓰는 게 권장되지는 않는다. *반복적 작업 할 때는 ok*
* 단점은, **세 구성요소 작성 순서를 기억하고 있어야 한다**는 것이다.

#### 세부 구성

```javascript
for(var i = 0; i < 10; i = i +1)
// 순서대로 (초기화; 반복조건; 반복실행)
```
* 초기화: for문을 작동시킬 때, 처음 한 번만 가능하다.
* 반복조건: 반복할 내용
* 반복실행: 반복적으로 실행할 내용.

#### 참고: i = i + 1 표기 방법

```javascript
for(var i = 0; i < 10; i++){
    document.write("coding everybody "+i+"<br/>");
}
```
* `i++`와 `i = i + 1`은 대충 같은 의미이다.
    * 왜 대충이라고 했냐면, ++i도 있어서.
* `++i`와 `i++`의 유사점: 1씩 증가시킨다.
* `++i`와 `i++`의 차이점
    * i = 0일 때, `alert(i++)`;를 하면,`i++`값으로 숫자 0이 온다. 그리고 alert가 실행된 `후`에 i값이 1만큼 증가한다. 즉, **사용 후에야 더해진다**
    * 반면, `alert(++i)`를 쓰면, **사용하는 순간에 1 증가한다**
    * 즉, 사용과 동시에 증가하느냐`++i`, 사용 후에 증가하느냐`i++`하는 `증가 시점 차이`가 있다.
----

## 반복문 제어

* 제곧내(제목이 곧 내용이다)
    * 특정 조건 하에 반복문을 언제까지, 어떻게 반복할 것인가 제어한다.

### 제어문1_break

* 반복문을 특정 조건 하에서 강제 종료시킨다.
```javascript
for(var i = 0; i < 10; i++){
    if(i === 5) {
        break;
    }
    document.write('coding everybody'+i+'<br />');
}
/*
coding everybody 0
coding everybody 1
coding everybody 2
coding everybody 3
coding everybody 4
*/
```
* 반복작업을 **중간에 중단시키고 싶을 때** 사용한다
* 위 예제의 경우, `반복조건`을 보면 `i < 10`이니까 정상적으로는 0~9까지 실행되어야 하는 조건이다.
    * 하지만, for문 아래에 있는 `if문`이 작동하여 실제로는 0~4까지만 출력된다.
    * `i === 5`라는 조건 때문이다: i값이 5가 되었을 때, 반복문을 종료시키고 밖으로 빠져나간다는 break가 쓰인 것이다.
* 즉, `break를 반복문 안에 작성`하면, **특정 조건 하에 반복문을 완전히 마칠 수 있다.**
    * `반복문을 마친다` === `반복문의 {} 밖으로 빠져나간다` === `반복문 다음 코드를 실행시킨다`
* *반복문 안에 조건문*이 들어갈 수도 있고, *조건문 안에 반복문*을 쓸 수도 있다.

### 제어문2_continue

* 특정 조건에서만 결과 출력을 건너뛰고 계속해서 반복문을 쓴다.
```javascript
for(var i = 0; i < 10; i++){
    if(i === 5) {
        continue;
    }
    document.write('coding everybody'+i+'<br />');
}
/*
coding everybody 0
coding everybody 1
coding everybody 2
coding everybody 3
coding everybody 4
coding everybody 6
coding everybody 7
coding everybody 8
coding everybody 9
*/
```
* 0~4, 6~9가 출력된다. i = 5일때는 출력되지 않는 것을 확인할 수 있다.
* `continue`의 조건이 되는 때는 반복문을 실행하지 않고, 다시 반복문 조건으로 돌아가서 반복문을 실행한다.
    * 즉, **`continue의 조건이 되는 그 순간만` 반복문을 중지**한다.
    * 이 점이 반복문을 아주 종료시켜버리는 [break](#제어문1_break)와의 차이점이다.
----

## 반복문 중첩

* JS에서 **문자와 숫자를 결합**하면, **숫자를 문자 데이터화해서 받아들여 결과를 보여준다**.

```javascript
document.write('coding' +i+j+ '<br/>');
//여기에서 i와 j는 본래 숫자데이터이다.
/*하지만, 앞의 coding과 뒤의 <br/>이 문자열인데,
문자열과 함께 숫자를 쓸 경우 문자데이터화해주는 JS의 특성이 발동된다.

즉, i=1, j=3이라고 했을 때, 
coding 4 가 아니라
coding 13 을 출력해준다.
*/
```
* 위 예제에서 `i`와 `j`는 본래 숫자 데이터.
* `coding`과 `<br/>`은 문자열.
* 문자열과 숫자를 함께 쓸 경우, **문자를 데이터화 해주는 JS의 특성**이 발동된다.
    * 즉, `i = 1`, `j = 3`이라고 했을 때, `coding 4`가 아니라 `coding 13`이 출력된다.

### 예제1_100번 쓰기

```javascript
for(var i = 0; i < 10; i++){
    for(var j = 0; j < 10; j++){
        document.write('coding yeah'+i+j+'<br/>');
    }
}
/*
coding yeah 00 부터 99까지 총 100번 반복된다.
*/
```
* 반복문 진행 절차를 글로 풀어보면 다음과 같다.
    * i = 0인 채 반복문이 시작되어, i 안쪽의 j가 0~9까지 커지고, j가 10에 도달하면 다시 바깥쪽 i가 1이 되고, 다시 안으로 들어가서 j가 0~9까지 커지고...
    * 이걸 i < 10까지 반복하는 것이다.
    * 다시 한 번 요약해서 이해해보자: `i에 대한 for문`이 바깥쪽에, `j에 대한 for문`이 안쪽에 있다. 안쪽의 for문이 종료되면 바깥쪽 for문이 실행된다.
* 자주 사용되는 기법이다.

### 예제2_숫자만 100번 쓰기(feat.string)

```javascript
// 0부터 9까지 변수 i에 순차적으로 값을 할당        
for(var i = 0; i < 10; i++){
    // 0부터 9까지의 변수를 j의 값에 순차적으로 할당
    for(var j = 0; j < 10; j++){    
        // i와 j의 값을 더한 후에 출력
        // String은 숫자인 i와 j의 데이터 타입을 문자로 형태 변환하는 명령이다. 
        document.write(String(i)+String(j)+'<br />');
    }
}
/*
00~99까지 출력.
*/
```
* `String`은 숫자인 i와 j의 **데이터 타입을 문자로 형태 변환하는 명령**이다.
    * 위 예제에서 `string`을 지우고 반복문을 진행하면 다음과 같다.
    ```javascript
    for(var i = 0; i < 10; i++){
        for(var j = 0; j < 10; j++){
            document.write(i+j+'<br />');
        }
    }
    /*
    0 1 2 3 4 5 6 7 8 9
    10 2 3 4 5 6 7 8 9 10
    11 3 4 5 6 7 8 9 10 11
    12 4 5 6 7 8 9 10 11 12
    ...
    */
    ```
    * **솔직히 왜 이렇게 나오는지 아직 모르겠다** ㅋㅋㅋㅋㅋㅋ
----

## 크롬 개발자도구 디버거 활용 예시

* 코드가 사용되는 **과정**을 단계별로 나누어 확인할 수 있다.
* Breakpoint : 코드 실행 시 멈추는 지점을 정해놓는 것. ((얼떨결에 알게 된 VSC 브레이크 선택이랑 비슷하다))
    * 브레이크포인트 걸어둔 그 부분에서 일시정지된다.
* [디버거 활용 예시_유튜브 영상](https://youtu.be/tS_kELn3m9U?t=243)
> 42서울 논리테스트 게임할 때, 단계별로 움직임을 볼 수 있는 버튼이 있었다. '내가 설계한 움직임대로라면, 이 다음에 비행선이 어디로 움직일 것인가'를 단계별로 볼 수 있는 버튼이었다. **크롬 개발자도구의 디버거도 그렇게 활용되는 것**이라고 이해해두고 넘어가자! 아직은 활용도, 활용법에 공감을 못하니 귀에 잘 들어오지는 않는다 ㅋㅋㅋ 후에, 필요하게 되면 깊이 공부하고 활용법 익혀서 써먹자!
----

## 어록

* 반복문의 효용에 관한 이야기(feat.학습 방식 조언)
`어떤 기능을 배울 땐, 그 기능이 없었을 때 얼마나 불편했을까, 그 기능을 처음 마주한 사람들을 얼마나 편했을까를 이해하며 공부하면 더 의욕적으로 공부할 수 있다.`
    *eg) 반복문이 없으면 얼마나 불편할까*
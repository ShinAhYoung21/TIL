# 함수 Function

* **간략 목차**
    * [함수 형태](#형태)
    * [정의와 호출](#정의와-호출)
    * [함수의 효용](#함수의-효용)
        * [프로그래밍에서 중요한 세 특성: 재사용성,유지보수,가독성](#참고_재사용성,-유지보수,-가독성)
    * [함수 입출력](#함수-입출력)
        * [출력](#출력-return)
    * [함수의 인자](#인자-argument)
    * [함수 정의 방법: 2가지](#함수-정의)
    * [참고: 익명함수](#참고_익명함수)
    * [어록](#어록)
    * [추가학습 자료](#추가-학습한-자료-링크)
----

## 함수 기본 정의

### 형태
```javascript
function 함수명([인자...[,인자]]){
    코드
    return 반환값
}
```

### 정의와 호출

```javascript
function numbering() {
    document.write(1);
}
```
* 함수 정의
    * 변수 사용 시, 변수를 정의한 것처럼 함수도 사용하기에 앞서서 정의해야 한다.
* 호출
    * 마찬가지로, 변수 쓸 때처럼 정의 후 호출이 필요하다.
* 단, 함수와 변수는 **사용 절차가 비슷할 뿐**이다. **문법은 서로 다르다**
```javascript
numbering; //이렇게 작성하면, 변수 호출!
numbering(); //이게 함수 호출!!
```
----

## 함수의 효용

* 로직을 재실행할 수 있게 돕는다.
    * 즉, `코드의 재사용성(재활용성)`을 높여준다.
    * 재사용성: 작성한 코드를 여러 맥락에서 다시 사용할 수 있게 하는 것. **하나의 코드를 여기저기에서 쓸 수 있다는 것**을 의미한다.
        * *활용하기 좋은 부품을 만든다*고 이해하면 편리하다.
        * 또한, 유지보수(maintenance)가 편리해진다.
    * 재사용성 덕분에, 한 곳에서 코드를 개선하면, 그 코드를 사용하는 모든 곳에서 개선이 동시다발적으로 일어난다(자동. 동시).
* 가독성도 좋아진다.
* `함수 vs 반복문`
    * 반복문은 기계적으로 일정 내용을 반복하는 기능을 **그 자리에서 실행할 때**효과적이다.
    * 반면, 함수는 반복적으로 실행되는 로직이 **여기저기에서 사용되어야 할 때** 쓰기 좋다.
    ![앱 개발시, 함수를 쓰고 안 쓰고의 코드 작성 편의 비교](https://s3.ap-south-1.amazonaws.com/s3.studytonight.com/tutorials/uploads/pictures/1587881648-1.png)
    * 함수를 반복해서 쓸 필요가 있다면? for문 등 반복문으로 함수를 반복하면 된다.
    ```javascript
    // 함수 정의와 반복문 입력
    function numbering(){
        var i = 0;
        while(i < 10){
            document.write(i);
            i += 1;
        }   
    }

    // 함수 호출
    numbering ();
    numbering ();
    numbering ();
    numbering ();
    ```

### 참고_재사용성, 유지보수, 가독성

* 세 특성은 **프로그래밍/개발의 발전과 함께 해온 이점들**이다.
    * 하나가 나빠지면 모두 나빠지고, 하나가 좋아지면 모두 좋아지는 방향으로 함께 움직인다. ~...재무관리의 위험분석기호가 생각날랑말랑한다. 같은방향으로 비례하면 +1값을 갖는다는 그거.~
* 앞으로 **함수 외에 다른 문법요소(객체 등)들을 접할 때, '이 문법 요소는 세 특성에 대해 어떻게 대처하고 있는가'관점을 염두에 두고 학습하기**-를 이고잉님(생활코딩)이 권하셨다.

* 이 특성들은 협업에 있어서도 유용하다.
    * 모든 협업 관계자가 로직에 정통할 필요가 없어지기 때문이다.
        * 예를 들어, 뭔가 계산하는 함수를 쓸 때, *"이 함수는 이러저러한 계산을 실행시켜준다"*는 정도만 이해하고 사용하면 된다.
        * 사용자 모두가 로직에 정통할 필요 없으므로, 효율적이다(편리하다).
        * 극단적인 예를 들자면, 오늘날 *컴퓨터 사용하려는데 컴퓨터 제작자나 과학자가 될 필요가 없는 것*과 같다.
        * 이런 상황이 가능한 이유는 **함수를 한 번 정의하고 나면 단순히 함수를 `호출`하면 되기 때문이다. (쓸 때마다 정의해야 하는 번거로움/어려움 없음!)
----

## 함수 입출력

### 함수에 관한 고찰

> 입출력인데 뜬금 '고찰'이 나오는 이유는? 생활코딩 강의 흐름따라 노트 작성하느라 그렇다.
> 얼핏 보면 뜬금 없어 보일 수 있으나, 복습하다보면 학습 흐름에 잘 들어맞는다(적절ㅇㅇ).

![함수 기계. Function machine](https://mathinsight.org/media/image/image/function_machine.png)

* 위의 Function machine 이미지가 의미하는 것: **입력에 따라 출력이 달라지는 게 함수다**
* function: 기능, 작용
* 함: 상자.
    * 이때, 상자 안에 어떤 값을 주면, 그 값에 따라 다른 결과가 출력되는 상자라는 의미가 함수의 '함'에 담겨 있다.

### 출력 return

```javascript
function get_member1(){
    return 'egoing';
}
 
function get_member2(){
    return 'k8805';
}
 
alert(get_member1()); // egoing
alert(get_member2()); // k8805
```
* `return`의 두 가지 기능
    1. 함수 종료시키기
        * 다시 말해서, return 뒤에 있는 코드는 **실행되지 않는다**
        ```javascript
        function get_member(){
            return 'egoing';
            return 'k8805';
            return 'sorialgi';
        }
        alert(get_member()); // egoing
        ```
        * 위 예시에서 리턴값이 egoing인 이유는, **첫 리턴 뒤의 코드는 실행되지 않은 채 함수가 종료되기 때문**이다.
            * 위 예시 함수의 모든 값을 리턴하기 위해서는 반복문과 배열을 함수와 함께 사용해야 겠다. (복습 중에 혼자 식 써보다가 깨달았다. 아래는 쓰다 만 식.)
            ```javascript
            // for문의 i값과 배열의 정보 번호를 일치시키고, 배열과 함수를 연결하면 가능할 듯. 지금 이해하고 있는 바로는 그렇게 설계할 수 있다.
            function get_member(){
                for(i = 0; i < 3; i = i + 1){
                }
            }
            ```
    2. 리턴 뒤 `;`까지 써있는 값을 함수의 출력값으로 반환하기
        * 즉, 함수 밖으로 뱉어낸다.
        ```javascript
        function get_member1(){
            return 'egoing';
        }

        function get_member2(){
            return 'k8805';
        }

        alert (get_member1()); // egoing
        alert (get_member2()); // k8805
        ```
----

## 인자 Argument

![함수의 구조](https://s3.ap-south-1.amazonaws.com/s3.studytonight.com/tutorials/uploads/pictures/1587882057-1.png)
> 위 이미지에서 `parameter or input`이라고 소개되어있는 부분이 `argument`라고도 불린다.
    > 엄연히 구분하자면, `Parameter 매개변수/인수`는 **함수(또는 메서드) 정의에 들어있는 변수**. `Argument 전달인자/인자`는 함수(또는 메서드)를 호출할 때 전달되는(입력되는) **변수의 실제 값**.
* 예제1
    ```javascript
    function get_argument(arg){
        return arg;
    }
    //arg가 입력, return이 출력과 관계있다.
    
    alert(get_argument(1)); // 1 : 위 함수 arg값에 1을 투입
    alert(get_argument(2)); // 2 : 위 함수 arg에 2 투입
    ```
* 예제2
    ```javascript
    function get_argument(arg){
        return arg*1000;
    }

    alert(get_argument(1)); // 1000 : 1*1000
    alert(get_argument(2)); // 2000 : 2*1000
    ```
    * 값을 받는 변수는 매개변수(parameter), 값 자체는 인자(argument)
        * function 정의할 때, 함수 이름 바로 옆`()`에 쓰인 arg는 매개변수. 호출 시에 입력하는 값을 전달받는다.
        * alert와 함께 함수 호출 시에 입력한 `1,2`는 인자.
* 복수의 인자
    * 여러 개의 입력값을 가질 수 있으며, `,`로 구분한다.
    * 단, **한 개의 값만 리턴된다**
    ```javascript
    function get_arguments(arg1, arg2){
        return arg1 + arg2
    }

    alert(get_arguments(10, 20));
    alert(get_arguments(20, 30));
    ```
----

## 함수 정의

> 여러 가지 방법이 있다.

* 방법1: 변수`var`에 함수 대입
    ```javascript
    var numbering = function (){
        i = 0;
        while(i < 10){
            document.write(i);
            i += 1;
        }   
    }
    numbering();
    ```
    * 위 예제는 함수 내용이 `numbering이라는 변수`에 대입된 것이다.
        * 그러므로, `numbering();`으로 함수를 호출할 수 있게 된다.
* 방법2: 함수이름 입력
    * 위의 예제와 같은 결과를 도출한다.
        * 변수 `var`를 쓰지 않고, `numbering`을 함수 이름으로 입력했다는 차이가 있을 뿐, 기능은 똑같다.
    ```javascript
    function numbering(){
        i = 0;
        while(i < 10){
            document.write(i);
            i += 1;
        }
    }
    numbering();
    ```
----

## 참고_익명함수

> 알면 좋고, 몰라도 됨-이라고 이고잉님이 ㅋㅋㅋㅋㅋ

```javascript
(function (){
    i = 0;
    while(i < 10){
        document.write(i);
        i += 1;
    }   
})();
```
* 함수 **정의와 호출을 동시에** 한다!
* 이름 없이 바로 실행되므로 `익명함수`라고 한다.
* 일회성으로 호출하는 경우, 이런 테크닉을 쓴다.
----

## 어록

* 프로그래밍과 수학의 상관관계
`프로그래밍 하다보면 나중에 수학 공부하는 데 큰 도움이 될 수 있다.`
* 함수에서 꼭 기억해야 할 것은 [`함수는 코드의 재활용성을 높여준다`](#함수의-효용)는 것!
* 참고로, JS를 `함수형 언어`라고도 한다.
    * 이 언어를 규정하는 특징으로 **함수**라는 말을 쓰는 만큼, 중요한 요소다.
    * 다른 언어에 비해 함수가 차지하는 비중이 아주 크며, 이에 얽힌 복잡한 이슈들이 많다. 차차 공부하자!
----

## 추가 학습한 자료 링크

* [javascript function 효용, 활용 예시](https://s3.ap-south-1.amazonaws.com/s3.studytonight.com/tutorials/uploads/pictures/1587882057-1.png)
    * 함수의 재사용성 이미지, argument 설명 이미지 출처
* [parameter vs argument](https://stackoverflow.com/questions/156767/whats-the-difference-between-an-argument-and-a-parameter)
    * 두 개념을 예비개발자 뿐 아니라 현업 개발자들도 구분하기 어려워하는 모양이다ㅋㅋㅋㅋ we are the world! :)
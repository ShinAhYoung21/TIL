# 객체 Object

* **간략 목차**
    * [객체란?](#객체란)
        * [객체와 배열 비교](#객체vs배열)
        * [곁다리(?)지식](#객체에-대한-곁지식)
    * [객체 생성](#객체-생성)
    * [만든 객체 값 가져오기](#객체-값-가져오기)
    * [for(in)문: 배열과 객체 속 데이터 열거](#배열과-객체-속-데이터-열거하기)
        * [for(in)문](#for-in문)
        * [객체에서 활용](#활용-사례-in객체)
        * [배열에서 활용](#활용-사례-in배열)
    * [객체 안에 객체 담기](#객체-안에-객체-담기)
    * [보충학습](#보충학습)
        * [객체의 플래그Flag](#객체의-플래그)
        * [console.log에 여러 값 입력하기](#console-log에-여러-값-입력하기)
        * [객체지향 프로그래밍 Object Oriented Programming](#객체지향-프로그래밍)
    * [어록](#어록)
----

## 객체란

### 객체vs배열
* 역할은 유사하다.
    * **연관된 데이터를 담는 그릇**!
* 차이점
    * 배열은 대괄호`[ ]`로, 객체는 중괄호`{ }`로 감싼다.
    * 배열에서 index, element라고 하는 값들은 객체에서 각각 key, value라고 한다.
        * [배열](https://github.com/ShinAhYoung21/TIL/blob/main/JS/js_7_array.md)노트에서 *배열의 생성*하단 내용 참조.
        * `key`는 **각 원소들이 순서대로 갖고 있는 고유한 식별자(번호)**, `value`는 **객체 안에 들어 있는 각 값**.
        * 내가 익히기 편하게 `key는 식별자`, `value는 값`이라고 입에 붙여두자! *배열도 겸사겸사! `index는 색인`, `element는 원소`!*
    * 또한, 배열에서는 index값이 **0부터 자동으로 숫자 값**이 주어졌다. 하지만, 객체에서 `key`로는 **숫자 뿐 아니라 원하는 데이터를 직접 넣을 수 있다**.
        * 예를 들어, key값으로 `first, second`등 문자열도 입력 가능!

### 객체에 대한 곁지식

* 자바스크립트의 객체 === 다른 언어에서는 *연관배열(associative array)*, *맵 딕셔너리*등의 데이터 타입으로 존재한다.
* `객체 지향`이라는 **프로그래밍 패러다임**과 연결되는 중요한 개념.
* 객체 개념쌓기의 시작을 **정보를 담는 그릇**이라는 관점으로 받아들이기!
    * 이를 통해, 프로그램을 좀더 구조적이고 부품으로 사용할 수 있는 로직을 만드는 단위로 이해를 확장해나갈 수 있다.
----

## 객체 생성

* 객체를 만드는 방법은 여러가지이다.
* 방법1: 데이터 한꺼번에 입력
    ```javascript
    var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
    // 첫 번째 key(식별자)가 egoing인 것이다. 첫 value(값)은 10.
    ```
* 방법2: 데이터 따로입력, {};
    ```javascript
    var grades = {};
    grades['egoing'] = 10;
    grades['k8805'] = 6;
    grades['sorialgi'] = 80;
    ```
* 방법3: 데이터 따로 입력, new Object();
    ```javascript
    // new Objet();는 방법2의 {};과 같은 의미이다.
    var grades = new Object();
    grades['egoing'] = 10;
    grades['k8805'] = 6;
    grades['sorialgi'] = 80;
    ```
----

## 객체 값 가져오기

* 값을 가져오는 방법도 여러가지이다.
```javascript
var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};

// 아래 코드들은 모두 같은 값을 리턴한다.
// 80
grades['sorialgi'];
grades.sorialgi; // 간결하다
grades['sori'+'algi']; // 'sorialgi'가 문자열이기 때문에, 이렇게 입력하는 방법도 있다.

//그러나, 아래는 작동하지 않는다.
grades.'sori'+'algi'
```
----

## 배열과 객체 속 데이터 열거하기

### for in문

* 일반적 for문과는 다른 형태의 반복문
    ```javascript
    for (변수 in 객체){
        객체의 모든 열거할 수 있는 프로퍼티의 개수만큼 반복적으로 실행하려 하는 실행문;
    }
    ```
    * *열거할 수 있는 프로퍼티*: enumerable 플래그가 true로 설정된 프로퍼티
        * 객체의 플래그(flag)에 관해서는 [링크된 목차 참조](#보충학습-객체의-플래그)
* [참고자료(링크)](https://yjshin.tistory.com/entry/JavaScript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-for-%EB%AC%B8-for-in-%EB%AC%B8-for-of-%EB%AC%B8)

### 활용 사례 in객체

* `for( in )문`: 배열과 객체 속 데이터를 열거할 수 있다.
* 아래는(1과 2 둘다) grades라는 변수에 담겨 있는 값들을, 반복문이 실행될 때마다 하나씩 가져와서, 객체 속 key값을 변수 username에 담아본 예제이다.
    * 예제1
        ```javascript
        var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};
        for(key in grades) {
            document.write("username : "+key+" value : "+grades[key]+"<br />");
        }
        /*이렇게 출력된다
        username :   egoing value : 10
        username :   k8805 value : 6
        username :   sorialgi value : 80
        */
        ```
    * 예제2
        ```javascript
        var grades = {'egoing': 10, 'k8805': 6, 'sorialgi': 80};

        for(key in grades) {
            console.log(key);
        }
        // grades에 있다가 key변수로 들어간 키값들이 출력된다.
        ```
        * `for(in)`에서 *in과 함께 소괄호 안에 쓰인 key*는 객체속key값을 넣을 변수이다.
        * *grades*는 앞에서 정의한 객체를 의미한다.

### 활용 사례 in배열

* index(색인) 가져오기
    ```javascript
    var arr = ['a', 'b', 'c'];
    for(var name in arr){
        console.log(name);
    }
    /*아래와 같이 리턴된다.
    0
    1
    2
    */
    ```

* element(원소) 가져오기
    ```javascript
    for(var name in arr){
        console.log(arr[name]);
    }
    /*이렇게 작성하면, 다음과 같이 리턴된다.
    a
    b
    c
    */
    ```
----

## 객체 안에 객체 담기

* 제곧내(제목이 곧 내용). 객체 안에 또 객체를 담을 수 있다.
```javascript
var grades = {
    'list': {'egoing': 10, 'k8805': 6, 'sorialgi': 80},
    'show' : function(){
        for(var name in this.list){
            document.write(name+':'+this.list[name]+"<br />");
        }
    }
};
grades.show();
```
* `this`는 **함수가 소속되어 있는 객체를 가리키는 변수**이다.
    * 예시 코드 속 `this`는 **function이라는 함수가 속해 있는 `객체 grades`**를 가리킨다.
* `객체 grades`는 `데이터 list`와 `함수 show`를 담는 그릇이다.
    * list와 show는 서로 관련성이 있다.
* 이처럼 **서로 연관된 데이터와 연관된 처리를 하나의 그릇 안에 모아서 그룹핑 해놓는 스타일**을 `객체지향 프로그래밍`이라고 한다.
    * [궁금해서 더 찾아본 객체지향 프로그래밍(링크)](#객체지향-프로그래밍)
----

## 보충학습

### 객체의 플래그

* 참고로, 객체에는 프로퍼티가 저장되는데, 객체 프로퍼티는 값과 함깨 플래그(flag)라고 불리는 특별한 속성 세 가지를 갖는다.
    * `writable` - true면 **값을 수정** 가능. / 아니면 읽기만 가능.
    * `enumerable`(열거, 셈이 가능한) - true면 **반복문을 사용해 나열** 가능. / 아니면 반복문을 사용해 나열하기 불가능 
    * `configurable` - true면 프로퍼티 삭제나 플래그 수정 가능 
* [객체의 프로퍼티 참고자료(링크)](https://ko.javascript.info/property-descriptors)

### console log에 여러 값 입력하기

* `,`를 붙여서 여러 값 입력 가능!
    ```javascript
    console.log(1,2,3,4);
    ```

### 객체지향 프로그래밍

* Object Oriented Programming (OOP)
    * 컴퓨터 프로그래밍 패러다임 중 하나
    * 프로그래밍에서 필요한 데이터를 추상화시켜, 상태와 행위를 가진 객체를 만들고, 그 객체들 간 유기적 상호작용을 통해 로직 구성하는 프로그래밍 방법
* [객체지향프로그래밍 학습참고자료(링크)](https://jeong-pro.tistory.com/95)

----
* [맨 위로](#객체-object)

## 어록

* (객체에서 객체지향으로의 개념 확장에 관하여) 점점 이해를 넓혀갈 수 있다! 그러니 맘 급하게 먹지 말고 지금 하는 내용을 이해하기! 그거면 충분해! :)
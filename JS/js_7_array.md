# 배열 Array

* **간략 목차**
    * [배열이란?](#배열이란)
        * [정의](#배열의-정의)
        * [생성](#배열의-생성)
        * [효용](#배열의-효용)
    * [배열 제어(관리)](#배열-제어)
        * [데이터 추가](#데이터-추가)
        * [데이터 제거](#데이터-제거)
        * [정렬](#정렬)
    * [활용 예시](#활용-예시)
        * [동적 활용](#동적으로-활용하기)
    * [어록](#어록)
----

## 배열이란

### 배열의 정의

* **복수 데이터를 효과적으로 관리, 전달할 목적으로 고안된 데이터 타입**이다.
    * 연관데이터를 모아서 한꺼번에 관리하기 위해 사용하는 데이터 타입으로, **데이터를 담는 큰 그릇**이라고 이해하면 쉽다.
* 변수와의 차이는, **변수는 하나의 데이터를 저장**하는 것이고, **배열은 여러 데이터를 하나의 변수에 넣는 것**

### 배열의 생성

```javascript
var member = ['egoing', 'k8805', 'sorialgi']

member //콘솔에서는 이렇게 배열명을 입력하면 배열 내에 들어있는 값들을 쭉 보여준다.

//아래 명령어는 배열 내 값들을 순차적으로 경고창으로 띄워준다.
alert(member[0]);
alert(member[1]);
alert(member[2]);
```
* `원소 Element` : 배열 안에 들어 있는 각 값.
    * 위 예제의 `배열 member`는 3개의 원소를 담고 있다.
* `색인 Index` : **각 원소들이 순서대로 갖고 있는 고유한 식별자(번호)**
    *
     **첫 번째 저장된 값이 `0`이라는 것**이 특징이다!
    * 그 다음은 1, 2, 3, ...

### 배열의 효용

* **연관된 정보를 한꺼번에** 다룰 수 있다!

* 배열 **사용할 때**와 **안 할 때** 비교
    ```javascript
    // 배열 안 쓰는 경우
    function get_member1(){
    return 'egoing';
    }
    document.write(get_member1());
    
    function get_member2(){
        return 'k8805';
    }
    document.write(get_member2());
    
    
    function get_member3(){
        return 'sorialgi'
    }
    document.write(get_member3());

    // 배열 쓰는 경우
    function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
    }
    var members = get_members();
    document.write(members[0]);
    document.write(members[1]);
    document.write(members[2]);
    ```
----

## 배열 제어

* 배열의 데이터를 편리하게 추가, 수정, 삭제할 수 있는 기능들이 존재한다.

### 데이터 추가

```javascript
var li = ['a', 'b', 'c', 'd', 'e'];
//push는 배열의 고유 명령어. JS의 내장함수.
li.push('f'); 
alert(li); // a,b,c,d,e,f

// concat는 여러 데이터 추가할 때 쓴다. 
var li = ['a', 'b', 'c', 'd', 'e'];
li = li.concat(['f', 'g']);
alert(li); // a,b,c,d,e,f,g

var li = ['a', 'b', 'c', 'd', 'e'];
li.unshift('z');
alert(li) // z,a,b,c,d,e
```
* `(배열명).push`는 배열의 고유 명령어이며, JS의 내장함수이다.
    * 배열 안에 박스를 하나 더 만들어, 어떤 정보를 더 밀어넣는다는 의미이다.
    * 한 개의 데이터를 더 넣는다.
* `(배열명).concat`는 여러 데이터를 한꺼번에 넣을 때 쓴다.
    * concatenate(사슬같이 잇다)의 약자.
* `(배열명).unshift`는 꼬리쪽이 아니라 앞쪽에 값을 추가할 때 쓴다.

```javascript
    var li = ['a', 'b', 'c', 'd', 'e'];
    li.splice(2, 0, 'B');
    alert(li); // a,b,B,c,d,e

    var A = ['a', 'b', 'c'];
    A.splice(1, 1, "x", "y");
    alert(A); // a,x,y,c
```
* 중간 어딘가에 끼워넣기 위해서는 `splice`를 쓴다.
    * splice는 두 가지 역할을 한다.
        1. 호출하면, **배열이 담겨 있는 값을 바꾼다**.
        2. 그리고, **삭제된 데이터를 리턴**해준다.
    * [생활코딩 내 splice syntax 설명 페이지](https://opentutorials.org/course/50/110)
        * 필요할 때마다 찾아다 쓰면 되니까, 빽빽이하듯 암기할 필요는 없다.
        * 단, `매뉴얼 보는 법`은 익히기! ->**예제 보면서 유추하고, 활용법을 익혀서 써먹기!**
    
### 데이터 제거

```javascript
var li = ['a', 'b', 'c', 'd', 'e'];
li.shift(); //첫 원소인 a를 제거하면서 a를 리턴해준다. 즉, 첫 원소를 제거한다.
alert(li); // b,c,d,e

var li = ['a', 'b', 'c', 'd', 'e'];
li.pop(); //제일 마지막 원소인 e를 제거하면서 리턴해준다.
alert(li); // a,b,c,d
```
* `shift`는 첫 원소, `pop`은 마지막 원소를 **제거하면서 리턴**해준다.


### 정렬

* 정렬은 프로그래밍에서 중요한 주제이다.
    * *어떻게 하면 더 빠른 정렬을 할 수 있을까*에 대해 연구하는 카테고리가 바로 **알고리즘**이다.
* 배열의 정렬 방법은 두 가지 있다.
    * [배열의 sort 설명자료_생활코딩 JS사전](https://opentutorials.org/course/50/109)
    * sortfunc부분을 직접 정의하면, 정렬을 원하는 대로 조작할 수 있다.
    * 한번에 이해할 필수 사항은 아니다. **필요할 때 찾아보고, 이해하고, 써먹으면 된다!**
```javascript
var li = ['c', 'e', 'a', 'b', 'd'];
li.sort(); 
alert(li); //알파벳 순으로 정렬된다. a,b,c,d,e

var li = ['c', 'e', 'a', 'b', 'd'];
li.reverse();
alert(li); //알파벳 역순으로 정렬된다. e,d,c,b,a
```
----

## 활용 예시

```javascript
function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
}
members = get_members();

// members.length는 배열에 담긴 값의 숫자를 알려준다.
for(i = 0; i < members.length; i++){
    document.write(members[i].toUpperCase());
// members[i].toUpperCase()는 members[i]에 담긴 문자를 대문자로 변환해준다. 
    document.write('<br />');
}
```
* `(배열).length`는 **배열의 크기**를 알려준다.
* 참고로 `toUpperCase()`는 JS의 `내장함수` 중 하나로, 내장함수의 반대는 **사용자 정의 함수**이다.

### 동적으로 활용하기

* **동적이다**라는 말의 의미는, **배열에 입력하는 원소들의 갯수에 따라 가변적으로 바뀔 수 있다**는 의미이다.
* 동적이지 않은 코드 예시
    ```javascript
    function get_members(){
        return ['egoing', 'k8805', 'sorialgi'];
    }
    members = get_members();

    for(i = 0; i < 3; i++){ }
    // 복습하는 의미에서 써둔다. for문 문법. 순서대로 (초기화; 반복조건; 반복실행)
    ```
    * members 배열에 원소를 추가할 경우, for문의 두 번째 조건인 "언제까지 실행할 것인가"(반복 조건)를 원소 갯수만큼 수정해줘야 한다.
* 동적인 코드 예시
    ```javascript
    function get_members(){
    return ['egoing', 'k8805', 'sorialgi'];
    }
    members = get_members();

    for(i = 0; i < members.length; i++){  }
    ```
    * 위에서 문제가 되던 `반복조건`부분을 동적으로 작성한 사례이다.
        * 명확한 숫자를 부여하는 것이 아니라, **members 배열의 원소 개수를 출력하는 함수를 입력**함으로써 **동적으로 기능**할 수 있도록 한 것이다.
    * 배열에 새 원소를 추가함과 동시에 for문이 수정된다.
----

## 어록

* 앞만 보지 말고, 항상 뒤를 돌아보며 **얼마나 많이 왔는가**를 보는 것도 학습 이어가며 힘 내는데 좋은 방법이다.

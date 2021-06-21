# 정규표현식 Regular Expression

* **간략 목차**
    * [정규표현식 개요](#정규표현식-개요)
        * [활용 절차](#정규표현식-활용-절차)
        * [주요 활용법](#주요-활용법)
    * [정규표현식의 두 단계](#정규표현식의-두-단계)
        * [컴파일 compile](#컴파일-compile)
        * [실행 execution](#실행-execution)
            * [RegExp 객체의 정규표현식](#regexp객체의-정규표현식)
            * [String 객체의 정규표현식](#string객체의-정규표현식)
    * [패턴과 관련된 기능](#패턴과-관련된-기능들)
        * [옵션](#옵션)
        * [캡처](#캡처)
        * [치환](#치환)
    * [추가 학습시 참고할 자료](#추가-학습시-참고할-자료)
    * [어록](#어록)
----

## 정규표현식 개요

* `문자열에서 특정 문자를 찾아내는 기능`을 한다.
    * **문자열 안에 특정 정보가 있는지 찾아**야 한다거나, **문자열 안의 정보들 중에서 어떤 패턴을 찾아 다른 텍스트로 치환하는 경우**에 사용한다.
    * 그래서, 수십줄이 필요한 작업을 한 줄로 끝낼 수 있게 된다고 한다.
* 웹, js, 정보와 관련된 것을 처리하기 위해서 아주 강력한 도구!
* js처럼 `일종의 언어`로, js뿐만 아니라 다른 언어들에서도 많이 사용된다.
    * 그래서, [정규표현식 자체에 대한 공부(링크)](https://opentutorials.org/course/909/5142)는 따로 해야 한다.
    * 내가 학습한 커리큘럼에서는 *js의 기능 중 일부에 해당하는 정규표현식*에 초점을 맞췄다.

* **입문자라면, 정규표현식이 무엇인가에 대한 느낌만**갖고 스킵!
    * 단, 정규표현식이 무엇인가에 대한 이해를 갖고 있따면, 이 카테고리를 끝까지 보기
    * *난 정규표현식 입문자이지만, 끝까지 들었다*
        * *이 커리큘럼의 정규표현식에서 어떤 때 어떻게 활용할 수 있는지 정도를 확인하고 넘어간다. 후에 정규표현식 강의를 통해 깊이 들어가고! 지금은 예습하듯 훑기로 한다.*
        * *학습하며 느낀 바로는, 효율적 코딩과 자동화 설계 하기 위해서는 정규표현식 학습 및 활용이 필수적이겠다. 정규표현식 학습을 하게 된다면, 내 주 목적으로 삼아야겠다.*

### 정규표현식 활용 절차

1. `작업의 대상`을 찾는다
2. `어떤 작업을 할 것인가 결정`한다
3. 실제로 `작업을 진행`한다

### 주요 활용법

> 정규표현식으로 진행하는 주요 작업 3가지

1. `추출`: **패턴에 맞는 정보를 추출**한다.
    * eg) url, email 주소 등
2. `테스트`: **특정 정보가 있는지 없는지 검토**한다.
3. `치환`: **찾아낸 정보를 다른 정보로** 바꾼다.
----

## 정규표현식의 두 단계

### 컴파일 compile

> 패턴(대상)을 찾는 것
* **검출하려는 패턴을 만드는 것**이다.
* 우선 정규표현식 객체를 만들어야 *(찾고자하는 대상을 패턴이라는 변수에 저장하는 것)*하는데, 객체 만드는 방법은 두 가지가 있다.
* 두 가지 모두 같은 결과를 만들지만, 각자 장단점이 존재한다.
    * `정규표현식 리터럴`
        ```javascript
        /* var pattern = /찾고자하는대상/; */
        var pattern = /a/;
        ```
    * `정규표현식 객체 생성자`
        ```javascript
        /* var pattern = new RegExp('찾고자하는대상'); */
        var pattern = new RegExp('a');
        ```
        * `RegExp`는 Regular Expression의 약자.
* 위 예시에서 `찾고자하는대상`부분에 정규표현식 문법에 맞는 긴~정보를 입력하면, 거기에 맞는 대상을 찾아준다.

### 실행 execution

> **대상에 대해 구체적으로 작업**하는 것
* 정규표현식을 컴파일해서 객체를 만든 후에는, 문자열에서 원하는 문자를 찾아낸다.
* 참고로, **객체가 사용할 수 있는 함수들**을 `메소드`라고 한다.
    * 아래 `RegExp객체`와 `String객체`의 정규표현식 예시들은 `메소드 실행`에 해당한다.

#### RegExp객체의 정규표현식

* `RegExp.exec()`
    ```javascript
    /* pattern이 정규표현식 객체인 에제 */
    var pattern = /a/;

    pattern.exec('abcdef');
    // ["a"]
    // 실행결과, 문자열 a를 값으로 하는 배열을 리턴

    pattern.exec('bcdefg');
    // null
    // a가 없기 때문에 null 리턴
    ```

* `RegExp.test()`
    * 인자 안에 패턴에 해당하는 문자열이 있으면 **true**, 없으면 **false** 리턴
    ```javascript
    var pattern = /a/;

    pattern.test('abcdef'); // true

    pattern.test('bcdefg'); // false
    ```

#### String객체의 정규표현식

* `Str.match()`
    * `RegExp.exec()`와 유사하다
    ```javascript
    var pattern = /a/;

    var str = 'abcdef';

    str.match(pattern); // ["a"]

    str.match(pattern); // null
    ```

* `Str.replace()`
    * 문자열에서 패턴을 검색해서 이를 변경한 후, 변경된 값을 리턴
    ```javascript
    var pattern = /a/;

    var str = 'abcdef';

    str.replace(pattern, 'A');  // Abcdef
    ```
----
[맨 위로](#정규표현식-regular-expression)
<br/>

## 패턴과 관련된 기능들

### 옵션

* 정규표현식 패턴 만들 때, 옵션을 설정할 수 있는데, **설정된 옵션에 따라 검출되는 데이터가 달라진다**

* `i`붙이면 **대소문자 구분 안 한다**
    ```javascript
    var xi = /a/;
    "Abcde".match(xi); // null
    // i를 붙이지 않았기 때문에 'a'에 정확히 해당하는 값이 없어서 null이 리턴된다

    var oi = /a/i;
    "Abcde".match(oi); // ["A"];
    // i를 붙여주면 대소문자 구분하지 않으므로 A가 리턴된다
    ```
* `g`붙이면, **검색된 모든 결과를 리턴**한다
    ```javascript
    var xg = /a/;
    "abcdea".match(xg); // ["a"]
    // 제시된 String에 a가 두 번 나오는데, 한 번만 검출된다

    // 궁금한 점이 있다! 검출된 a는 앞에 나온녀석일까, 뒤에 온 녀석일까? '순서대로 일을 처리하는'프로그래밍 특성상 '앞에 나온 녀석'일 가능성이 높으나 확실하지 않다.(내 추측일 뿐이다.)


    var og = /a/g;
    "abcdea".match(og); // ["a", "a"]
    // 이 문자열에 포함되어있는 패턴 정보를 모두 리턴해준다
    ```

### 캡처

> 예시로 살펴보기로 한다!
* coding과 everybody 순서 역전시키기!
    ```javascript
    var pattern = /(\w+)\s(\w+)/;

    var str = "coding everybody";
    var result = str.replace(pattern, "$2, $1");

    console.log(result); // everybody, coding
    ```
    * 괄호 안의 패턴은 변수처럼 재사용할 수 있다.
    * 이 때 기호 `$`를 사용한다. `$1`은 첫 번째 그룹을 나타낸다. 마찬가지로, `$2`는 두 번째 그룹을 표현.
    * 정규표현식에서 `( )`는 그룹을 의미한다(고 이해하면 ㅇㅋ)
    * `\w`는 **word(문자)**를 의미. A~Z, a~z, 0~9까지.
	* `\s`는 **space(공백)**이란 의미.

### 치환

> 예시로 살펴보자!
* 본문에서 url을 링크html태그로 치환하기!
    ```javascript
    var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;
    var content = '생활코딩 : http://opentutorials.org/course/1 입니다. 네이버 : http://naver.com 입니다. ';
    var result = content.replace(urlPattern, function(url){
        return '<a href="'+url+'">'+url+'</a>';
    });

    console.log(result);
    // 생활코딩 : <a href="http://opentutorials.org/course/1">http://opentutorials.org/course/1</a> 입니다. 네이버 : <a href="http://naver.com">http://naver.com</a> 입니다.
    ```
----

## 추가 학습시 참고할 자료

* 패턴에 대한 구체적 내용은 이 커리큘럼에서는 설명 생략! [정규표현식 커리큘럼(링크)](https://opentutorials.org/course/909/5142) 참조
* 값으로서의 함수 출력은 [이 커리큘럼의 이후의 내용(링크)](https://opentutorials.org/course/743/6508) 중에서 참고
* [정규표현식 시각화해주는 사이트(링크)](https://regexper.com/)
* [정규표현식 빌더](https://regexr.com/)
    * 파란색 표시가 되면, 위에 입력한 정규표현식에 해당되는 부분이라는 표시다.
----
[맨 위로](#정규표현식-regular-expression)
<br/>

## 어록

* **"갖게 될 것보다 이미 갖고 있는 것을 중요하게 여기기"**
    * 여기까지가 이 커리큘럼의 시즌1! "프로그래밍의 앙꼬! 어떤 프로그래밍언어이건, 여기까지의 내용이 전부 포함되어 있다! 간단한 프로그램 만드는 데 어려움 없다. 다른 프로그래밍언어로 건너가는 데 도움이 많이 된다."
    * 시즌2에서는 JS의 중요한 특성인 함수를 좀 더 깊게 판다고 한다. 필요성을 절감할 때 학습해서 써먹기로 한다!
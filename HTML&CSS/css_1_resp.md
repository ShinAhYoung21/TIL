# CSS 반응형 단위 정리

## CSS의 문법 구성
```css
.parent {
    font-size: 100%;
}
```
위의 코드를 토대로 문법 구성을 살펴보면,
* 선택자 Selector: 어떤 것을 선택할 것인지 결정. 위 예제에서는 `.parent`
* property: 어떤 속성을 꾸며줄 것인지 결정. `font-size`
* value: 각 property에 속하는 값. `100%`


## 사이즈 단위
> 절대적인 값과 상대적인 값으로 나뉜다.
### 절대적인 units
> Absolute length units
* 다양한 값이 있지만, 자주 사용되는 것은 `px`이다.
    * 구글닥스 등의 텍스트 편집기에서 `pt`를 많이 접할 수 있는데, 해당 SW상에서는 pt로 폰트 크기 조정을 하는 듯 보이지만, 브라우저 개발도구를 켜서 확인해보면 결국 **브라우저에 출력할 때는 `pt`를 `px`로 변환해서 표시한다**는 것을 알 수 있다.
    * 참고로, pt도 절대units에 속하는 단위 중 하나다.
#### px란?
* 모니터 위, 화면에 나타낼 수 있는 가장 작은 단위
* 컨테이너의 사이즈(브라우저 크기 등)가 변경되어도 콘텐츠 크기가 그대로 유지된다. 즉, 고정형이다.
----

### 상대적인 units
> Relative length units
* 이 역시 다양한 값들이 존재한다. 그러나, 반복적으로 쓰이는 것들은 정해져 있는 편이다.
* 상대적 유닛을 활용해 디자인하면, 브라우저환경이 변할 때, 자동적으로 페이지 폰트가 반응해서 사이즈가 변경된다. 즉, 반응형 디자인을 구현할 수 있다.

#### EM
> 타이포그래피에서 현재 지정된 포인트 사이즈를 나타내는 단위. 즉, 지금 폰트 사이즈를 나타내는 단위.
> 같은 폰트 사이즈라고 해도 어떤 폰트 패밀리 쓰는지 따라 사용자에게 보여지는 텍스트 크기가 달라질 수 있는데, `em`을 쓰면, 선택된 폰트 패밀리에 상관 없이 항상 고정된 폰트 사이즈를 갖는다.

* **부모의 폰트 사이즈를 곱한 값으로 계산**되는 단위. 즉, 부모의 사이즈에 대해 상대적으로 크기를 계산한다.
```html
<style>
.parent {
    font-size: 8em;
}

.child {
    font-size: 0.5em;
}
</style>
<body>
    <div class="parent">
        Parent
        <div class="child">Child</div>
    </div>
</body>
```
위 예제에서 parent는 html에 기본할당되는 폰트 사이즈인 16px에 8배를 곱한 128px값으로 브라우저에 표기된다.
child는 부모 요소인 parent의 0.5배 크기인 64px로 출력된다.
----

#### %
* em과 비슷하다.
    * **부모 사이즈 대비 몇 % 크기로 나타낼 것인지를 결정**한다.
* 디폴트 값은 `100%`.
    * 콘텐츠에 대해 따로 폰트 사이즈를 지정하지 않으면, 브라우저에 지정된 기본 사이즈를 따라간다는 의미이다.
```html
<style>
.parent {
    font-size: 800%;
}

.child {
    font-size: 50%;
}
</style>
<body>
    <div class="parent">
        Parent
        <div class="child">Child</div>
    </div>
</body>
```
----

#### rem
* r은 루트를 나타낸다.
* em과 달리, **루트에 지정된 폰트 사이즈에 따라 크기가 결정**된다.
    * 참고로, html문서에서 루트 요소란 `<html>`을 말한다. 그러므로 `html 선택자`라고 생각해도 무방하다. _출처: [MDN Web docs ":root"카테고리](https://developer.mozilla.org/ko/docs/Web/CSS/:root)

```html
<style>
.parent {
    font-size: 8rem;
}

.child {
    font-size: 0.5rem;
}
</style>
<body>
    <div class="parent">
        Parent
        <div class="child">Child</div>
    </div>
</body>
```
이전 예제에서 단위를 `em`에서 `rem`으로만 바꾸면, 화면에 출력되는 모양이 확연히 달라진다.
* parent는 그대로 출력된다. `em`에서나 `rem`에서나 `html의 기본 폰트 16px`을 기준으로 하기 때문이다.
    * `em`에서는 **부모요소**로서 html을 기준삼아 8배, `rem`에서는 **루트 요소**로서 html을 기준삼아 8배한다는 로직의 차이는 존재한다. 하지만, 이 예제 안에서는 결과물은 동일하다.
* child도 루트요소인 html의 16px을 기준으로 0.5배 곱한 8px로 계산이 된다.
    * 바로 이 점이 em과의 큰 차이점이다. **부모요소가 아니라 루트요소(최고 루트)를 기준으로 하기 때문에 발생하는 차이점이다.**
----

#### vw
* viewport width(브라우저 너비)의 몇 퍼센트를 쓰겠다고 표현하는 단위.
    * 예를 들어, `50vw`이면, 브라우저 너비의 50%를 쓴다는 것.

#### vh
* viewport height(브라우저 높이)의 몇 퍼센트 쓰겠다는 표현 단위.

#### vmin & vmax
* `vmin`은 브라우저 너비와 높이 중 작은 값의 몇 퍼센트를 쓰겠다는 단위.
* `vmax`는 너비와 높이 중 큰 값의 몇 퍼센트를 쓴다는 단위.
----

학습자료 출처: [유튜브 드림코딩엘리_"프론트엔드 필수 반응형CSS 단위 총정리"](https://www.youtube.com/watch?v=7Z3t1OWOpHo)
## 08 / 10 TIL | HTML & CSS

### 1. HTML

> Hypertext Markup Language

#### HTML 구조 - DOM(Document Object Model) 트리

![DOM-model.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/DOM-model.svg/220px-DOM-model.svg.png)



#### 속성

``` html
<a href = "https://github.com/y0ungdev"></a>
<!-- href : 속성명 -->
<!-- https://github.com/y0ungdev : 속성값 -->
```

> **HTML Convention**
>
> Indent : 2 spaces or 4 spaces
>
> 속성과 속성값 사이 공백 X 
> 속성값은 " " 안에! 



#### Semantic Tag / 시멘틱 태그

> 의미의, 의미론적인(Semantic) 태그
>
> = 단순한 구역의 구분이 아니라 <u>의미</u>를 가지는 태그들을 활용하고자 함.
>
> Non semantic tag의 예시는 div, span 등이 있으며 h1, table 등의 태그도 semantic tag로 볼 수 있음.
>
> 검색엔진최적화(SEO)를 위해서 meta tag, semantic tag 등을 통한 마크업을 효과적으로 할 필요가 有

**SEO: Search Engine Optimization*

##### 장점

1. 읽기가 쉬워진다.

- 개발자가 의도한 요소의 의미 전달이 명확해짐
- 코드의 가독성이 높아지고, 유지보수가 용이함

2. 접근성이 좋아진다.

- 검색엔진➡시력장애우용 스크린리더➡더 나은 UX 제공

##### 예시

- header : 문서 전체나 섹션의 헤더 
- nav
- aside
- section
- article
- footer

#### 태그 

`<p>` : paragraph

`<a>` : 하이퍼링크 사용할 때

`<b>` vs `<strong>` : 두 태그 모두 텍스트를 **굵게(bold)** 함. 하지만 ` <strong>` 태그는 시멘틱 태그로서 의미를 갖고 있고 `<b>` 태그는 결과만 담고 있음.

`<i>` vs `<em>` : 두 태그 모두 텍스트를 *기울이는(italic)* 역할을 하지만 `<em>`은 시멘틱 태그이다. 

#### `<form>` 

`<form>` 은 서버에서 처리될 데이터를 제공하는 역할을 한다.

##### 속성

- `action` : 데이터를 어디로 보낼지 설정
- `method ` : 데이터를 보내는 방식을 설정(`GET` or `POST`. 이건 추후 Django에서 더 다룰 예정)

##### `input` 

> 다양한 타입을 가지는 입력 데이터의 필드

##### `label` 

- `label for`는 id에 연결된다



### 2. CSS

> Cascading Stylesheets

#### 1. CSS 구문

##### 1) 구성 요소

- 선택자(selector), 대상 html 요소, 선언(declaration)

```css
selector target html element{
    declaration
}
```

- CSS 정의 방법
  - `Inline style`
  - 내부 참조(`Embedding style`)
  - 외부 참조(`Link style`)

1️⃣ CSS 선택자 / Selector

> 스타일을 지정하고자 하는 웹 페이지의 특정 HTML 요소를 대상으로 할 때 사용한다.

- 클래스(class) 선택자

  class 선택자는 `.`로 시작하며 문서 내의 해당 클래스가 적용된 모든 항목을 선택한다.

- 아이디(id) 선택자

  id 선택자는 `#`으로 시작하며 기본적으로는 클래스 선택자와 같은 방식으로 사용한다.

  그러나 <u>id는 문서 당 한 번만 사용 가능</u>하며, 요소에는 단일 id 값만 적용할 수 있다.

  문서에서 동일한 id를 여러 번 사용하게 돼도 동작은 하지만 그렇게 하면 ❌

- 복합 선택자

  - 자손 선택자 / Descendant combinator

    > The **descendant combinator** — typically represented by a single space (` `) character — combines two selectors such that elements <u>matched by the second selector are selected if they have an ancestor</u> (parent, parent's parent, parent's parent's parent, etc) element matching the first selector. Selectors that utilize a descendant combinator are called descendant selectors.
    >
    > 출처 : developer.mozilla.org

    하위의 모든 요소에 적용하며 선택자a `공백` 선택자b로 표기한다.

    ```css
    selectorA selectorB {
        property declarations
    }
    ```

    

  - 자식 선택자 / Child combinator

    > The **child combinator** (`>`) is placed between two CSS selectors. It matches only those elements matched by the second selector that are the <u>direct children of elements</u> matched by the first.
    >
    > 출처 : developer.mozilla.org

    바로 아래의 요소에 적용되며 선택자a`>`선택자b로 표기한다.

    

2️⃣ CSS 단위

① px

- 모니터 해상도의 한 화소인 `픽셀`을 기준으로 한다.
- 픽셀의 크기는 변하지 않으므로 고정적인 단위이다(유연성X)

② em

- em은 상속의 영향을 받는다
- 상황에 따라 유동적인 값을 가질 수 있다.

③ rem

- 최상위 요소인 html(root em)을 절대 단위의 기준으로 삼고, 상속의 영향을 받지 않는다.
  - 상속에 영향을 받지 않으므로 대부분의 경우 `rem`을 많이 사용한다.



3️⃣ Box Model

>  모든 HTML 요소는 하나의 BOX 형태로 되어 있으며, 하나의 BOX는 content, padding, border, margin의 4가지 요소로 구성된다.

① content

글, 이미지, 동영상 등 실제 내용

② padding(안쪽 여백)

- Border(테두리) 안쪽 여백 ( 고정되어 있는 화면에서 안쪽으로 여백이 늘어남.)
- 배경색, 이미지 지정 가능

③ margin( 바깥쪽 여백)

- 테두리 바깥의 외부 여백

- 배경색 지정 불가능

  block의 rop 및 bottom margin이 때로는 (결합되는 마진 중에서 크기가) 가장 큰 한 마진으로 결합(combine, 상쇄(collased))된다.

④ border

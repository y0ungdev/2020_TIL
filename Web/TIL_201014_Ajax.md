## 10 / 14 JS 심화



> ECMA Script
>
> Coding Style Guide
>
> AJAX
>
> Callback Function
>
> Promise

### ECMA Script

#### 변수

- var
- let
- const

#### 타입과 연산자

- null : 개발자의 공백 의도
- undefined

#### 조건 & 반복

#### 함수

- 선언
- 표현

#### 자료 구조

- Array 

  - ArrayHelperMethod : map, reduce, every, filter

- Object

  - JSON
  - Object 축약 문법

  

### ASI(Automatic Semicolon Insertion)

= `;` : 문장의 마침표.

찍어야 한다 vs 안 찍어도 된다 논쟁 ing~

### Coding Style Guide

> JavaScript Standard Style 

- Indent = 2 spaces
- `==` 대신 `===`  / `!=` 대신 `!==`사용

<hr>

### AJAX

아약스라고 읽었는데.....ㅎㅎ;

> **A**synchronous **J**avaScript **A**nd **X**ML ( 비동기 자바스크립트와 XML)

![image-20201015215405000](TIL_201014_Ajax.assets/image-20201015215405000.png)

✅ 전체의 reload가 아니라 <u>일부</u>만을 변화시키는 것

> XHR : XML Http Request
>
> 전체 페이지의 새로고침 없이도 URL로부터 데이터를 받아올 수 있게 함

#### Asynchronous | 비동기

>  How JavaScript Works?

##### Asynchronous

*기다려 주지 않음*

"why?"

⬇

##### Single Thread

*한 번에 하나의 일만 **혼자 일하기 때문***

⬆ *Event  Loop*에 기반하여서

##### Event Loop

- Call Stack : 요청이 들어올 때마다 해당 요청을 순차적으로 처리하는 Stack(LIFO) 형태의 자료 구조
- Web API(Browser API): JavaScript 엔진이 아닌 브라우저 영역에서 제공하는 API
- Task Queue : CallBack 함수가 대기하는 Queue(FIFO) 형태의 자료 구조
- Event Loop : Call Stack에 현재 실행 중인 Task가 없는지 확인 ➡ Task Queue에 Task가 있는지 확인

<hr>

### Callback Function

#### Callback

인자로 넘어가는 함수. 내가 직접 요청한 것이 아니라 <u>시스템 내</u>에서 호출됨으로써 기능하는 함수!

### Promise

> Let's think about…
>
> 해야 할 일이 많은 상태에서 교수님께 질문을 했다! ➡ 답변을 받기 전까지 다른 일을 진행 ❌(계속 대기 중) : 동기(Sync)
>
> 해야 할 일이 많은 상태에서 교수님께 질문을 했다! ➡ 답변을 기다리는 동시에 이것저것 할 일을 한다 ➡ 답변이 도착하면 그 때 관련 일을 한다 : 비동기(Async)
>
> ∴ <u>~~면 --한다!</u>(연쇄적)

![image-20201015222636620](TIL_201014_Ajax.assets/image-20201015222636620.png)

하지만 '연쇄적'에 매여서 코딩하게 되면 이런 **CallBack Hell**에 빠질 수 있으므로 주의

그래서 Promise ㄷㄷㄷㅈ

![image-20201015222932376](TIL_201014_Ajax.assets/image-20201015222932376.png)

- `.then`: 성공한 경우

- `.catch` : 실패한 경우

#### async & await

from ES8+

> Syntactic Sugar
>
> 문법적으로 쉬운 사용을 위해 🤩

await은 async 내부에서만 사용이 가능하며

async은 비동기로직을 포함한 경우에만 사용이 가능

#### 🌟 axios 🌟

> Promise based HTTP client for the browser and node.js

``` html
// example code

axios.get('jsonplacehoder URL 어쩌구')
  .then(function(res){
    console.log(res.data.title)
})
  .catch(function(error){
    console.log(error)
})
```




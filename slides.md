---
theme: geist
title: ReScript 같이 해요
titleTemplate: "%s - Miryang"
highlighter: prism
lineNumbers: true
aspectRatio: 4/3
fonts:
  sans: "Pretendard"
  mono: "Elice Digital Coding"
  provider: 'none'
download: false
favicon: "https://rescript-lang.org/static/nav-logo@2x.png"
---

<h1 class="bg-clip-text text-transparent bg-gradient-to-r from-rose-300 to-red-600">
    ReScript 같이 해요
</h1>

<div class="absolute bottom-10">
  <span class="font-500">
    FEConf 2022
  </span>
</div>

<div class="absolute right-10 bottom-10">
  
  <a href="https://github.com/MiryangJung/2022-feconf-slides-rescript-together" target="_blank">
    2022-feconf-slides-rescript-together
  </a>

</div>

<!--
안녕하세요. 2022 FECONF에서 ReScript 같이 해요라는 제목으로 발표를 하게 된 정미량이라고 합니다.  
ReScript를 들어보신 분들도 계시고, 처음 접해보신 분들도 계실텐데 아마 대부분 초면이실 거 같네요.  
진입장벽이 느껴지는 언어라서 접하기 어려운 것 같습니다.  
저는 JavaScript와 TypeScript를 사용해왔었고, 올해 2월부터 6개월 넘게 ReScript를 사용하고 있습니다.  
개발 경험이 좋아서 제목처럼 다른 분들과 같이 하기 위해 발표를 준비하게 되었습니다.
-->

---

# 발표자 소개

<div class="flex mt-10">
  <div class="flex flex-col mr-200px">
    <img class="rounded-full w-200px" src="https://avatars.githubusercontent.com/u/48237511?v=4" />
    <div class="flex items-center mt-10">
      <carbon-logo-github />
      <a class="ml-1" href="https://github.com/MiryangJung" target="_blank">MiryangJung</a>
    </div>
    <div class="flex items-center mt-3">
      <carbon-logo-linkedin />
      <a class="ml-1" href="https://www.linkedin.com/in/miryangjung" target="_blank">정미량 (Miryang Jung)</a>
    </div>
        <div class="flex items-center mt-3">
      <carbon-logo-twitter />
      <a class="ml-1" href="https://twitter.com/MiryangJung" target="_blank">@MiryangJung</a>
    </div>
  </div>
  <ul class="font-semibold">
    <li class="my-3">그린랩스 프론트엔드 엔지니어</li>
    <li class="my-3">여행을 좋아합니다.</li>
    <li class="my-3">지방 거주 재택러.</li>
    <li class="my-3">함수형 프로그래밍 입문자.</li>
    <li class="my-3">개발 블로거. 
      <a href="https://miryang.dev" target="_blank">miryang.dev</a>
      <span class="text-neutral-500 text-sm"> (게스트북 남겨주세요 🫶🏻)</span>
    </li>
  </ul>
</div>

<!--
발표자 소개를 하겠습니다. 저는 에그테크 기업인 그린랩스에서 프론트엔드 엔지니어로 일하고 있습니다.
제가 일하는 그린랩스에서는 백엔드는 리스프 언어인 Clojure를 사용하고,
프론트엔드에서는 강타입 언어인 ReScript를 사용하고 있습니다.

그리고 저는 그린랩스에서 처음 함수형 프로그래밍을 접한 입문자입니다.
저는 시각적인 즐거움을 쫓는 사람이라 여행을 좋아하고, 얼마 전에 베트남을 다녀왔는데 엄청 더웠던 기억이 제일 강렬하게 남아있습니다.
지방에서 거주하는 재택러이고, 오늘 같이  큰 행사가 있을 때만 서울로 오곤 합니다.
개발 블로그를 운영하고 있고, 방명록이 있으니 후기를 남겨주시면 감사하겠습니다.

마지막으로 전 멋진 개발자로 기억되고 싶은 꿈이 있습니다.
-->

---

# 목차

- 가볍게 알아보기
- 작게 좋았던 점
- 크게 좋았던 점
- 아직도 망설인다면
- 아쉬웠던 점

<!--
발표의 순서는
ReScript를 가볍게 알아보고, 제가 사용해보면서 작게 좋았던 점과 크게 좋았던 점을 공유하고자 합니다.
그리고 여전히 망설이시는 분들을 위한 팁을 전달드리고, 사용하면서 아쉬웠던 점을 얘기하고 마무리하고자 합니다.

타입 세이프티하게 개발하기 위해 노력해오셨던 분들 그리고 명료한 코드 작성에 관심있으셨던 분들에게 좋은 인사이트가 될 것이라고 예상합니다.
-->

---

# 예상 청자

## 내가 만든 발표, 같이하기 위해 구웠지

- 프론트엔드 비기너이신 분
- 새로운 언어를 가볍게 알아보고 싶으신 분
- 함수형 프로그래밍 언어에 관심 있으신 분
- 강력한 타입 언어를 사용해 보고 싶으신 분
- ReScript 도입을 망설이고 있으셨던 분

<img src="/images/cookie.png" alt="쿠키" class="absolute right-0 top-0 h-full" />

<!--
발표에 들어가기 앞서 제 발표는 프런트엔드 비기너이신 분, 새로운 언어를 가볍게 알아보고 싶으신 분, 함수형 프로그래밍 언어에 관심 있으신 분,
강력한 타입 언어를 사용해 보고 싶으신 분, ReScript 도입을 망설이고 있으셨던 분들을 대상으로 합니다.
강타입 언어 그리고 함수형 프로그래밍이 가능한 언어라는 점이 진입 장벽으로 느껴질 수 있다고 생각합니다.
그래서 이 발표를 통해 장벽을 허물 수 있으면 좋겠습니다.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      가볍게 알아보기
  </h1>
</div>

<!--
ReScript 가볍게 알아보겠습니다.
-->

---

# ReScript란?

<div class="flex items-center my-10">
  <img class="mr-10" src="/images/rescript.png" alt="rescript 로고" />
  <h2>읽을 수 있는 JavaScript로 컴파일되는 강력한 타입 언어</h2>
</div>

<div v-click>

- JavaScript 개발자에게 친숙한 구문을 제공
- 모든 JavaScript 라이브러리를 ReScript와 함께 사용 가능

</div>

<!--
ReScript는 2020년에 탄생한 읽을 수 있는 JavaScript로 컴파일되는 강력한 타입 언어입니다.
컴파일러는 과장을 한 스푼 더해서 번개같이 빠른 속도를 가지고 있고, 컴파일 타임을 기다리는 경험을 선사하지 않습니다.
ReScript를 제가 사용하면서도 컴파일이 되기를 기다린 기억은 없습니다.
그리고 함수형 프로그래밍이 가능해 불변성과 순수함수를 지향합니다.

click!

ReScript 코드를 한 번이라도 보신 분들은 느끼셨을텐데 굉장히 JavaScript와 비슷하게 생겨 친숙합니다.
JavaScript로 컴파일이 되기 때문에 당연히도 모든 JavaScript 라이브러리들을 ReScript 프로젝트에서 사용할 수 있습니다.
언어가 달라서 다른 패키지 매니저를 사용해야 된다고 생각하실 수도 있지만 npm yarn 그리고 package.json도 그대로 사용할 수 있습니다.
그리고 ReScript로 작성한 라이브러리를 NPM에 배포할 수도 있고, ReScript도 npm에 배포되어있습니다.

TypeScript처럼 JavaScript의 슈퍼셋인가? 라고 생각하실 수도 있지만 ReScript는 JavaScript의 기능 중 특별히 선별된 기능만 다루고 있습니다.
-->

---

# Hello World!

<video controls autoplay class="m-auto max-h-120">
  <source src="/images/example.mp4" type="video/mp4">
</video>

<!--
ReScript의 플레이그라운드에서 간단하게 log를 찍는 코드와
a, b 두 개의 인자를 받아 더해 반환하는 함수를 작성해 봤습니다.
왼쪽이 ReScript 코드이고, 오른쪽이 컴파일되어 출력되는 JavaScript 코드입니다.

log를 찍는 함수는 생김새가 조금 다르지만 의미를 유추할 수 있고, add 함수는 충분히 비슷하게 생겼습니다.
방금 언급했듯이 친숙함이 느껴집니다.
-->

---

# ReScript 첫인상

프로그래밍 언어 문법은 금방 익힌다는 자신감 Down

<img class="m-auto max-h-100" src="/images/aoc.png" alt="그린랩스 웹개발팀 스타터킷 깃허브" />

<!--
저는 JavaScript, TypeScript, Go, Python, Java 등 다양한 언어를 접하면서 프로그래밍 언어 문법은 금방 익힌다는 자신감이 있었습니다.
제가 일하는 그린랩스에서는 신규 입사자에게 약 2~3주 동안의 온보딩기간이 주어지고 Advent of Code의 문제들을 풀면서 ReScript를 익힐 수 있도록 합니다.

온보딩 기간 처음에 함수형 프로그래밍을 익히는 지점에서 막혔습니다.
불변성을 유지하기 위해 변수의 값을 변경하지 못한다는 사실이 굉장히 어색했고, 제 생각의 구조를 바꾸는 데 시간이 꽤 걸렸습니다.
그 다음은 ReScript가 가진 컨셉을 알아가는 과정에서 처음 보는 개념들을 만나고 낯설었습니다.
-->

---

# 달랐던 것들

<br />

| 달랐던 점                              | 설명                                                |
| -------------------------------------- | --------------------------------------------------- |
| 😅 let만 있다.                         | const와 비슷한 불변 변수 선언                       |
| 😂 화살표를 사용한다.                  | <KBD>-></KBD> 파이프 연산자, a(b)를 <KBD>b->a</KBD> |
| 😫 return이 없다.                      | 마지막 라인은 암묵적 반환                           |
| 😰 import & export가 없다.             | 모든 모듈은 내보내진다                              |
| 🤯 타입 어노테이션 없이도 타입이 있다. | 타입 추론 시스템                                    |

<!--
ReScript를 처음 만나고 혼란스러웠던 점을 기억하자면 크게 5가지 정도였습니다.
let만 있는데 변수에 값을 재할당할 수 없다는 점
처음 보는 화살표 연산자가 있다는 점
return이 쓰이지 않는다는 점
import export가 없다는 점
타입 어노테이션을 명시하지 않아도 타입이 자동으로 생긴다는 점이었습니다.

JavaScript와 달라서 어색하게 느껴졌던 부분이기도 합니다.

ReScript에서 let은 let 바인딩이라고 불립니다. 다른 언어의 변수 선언과 비슷한 맥락이며 JavaScript의 let 과는 다르게 값 변경이 불가능한 불변입니다.
화살표는 파이프 연산자로 불리며 방향을 바꿔주는 문법 설탕입니다.
return이 없는 이유는 마지막 라인은 암묵적으로 반환되기 때문이며, import&export가 없는 이유는 모든 모듈은 기본적으로 내보내지기 때문입니다.
ReScript의 꽃이라고 할 수 있는 타입 추론 시스템이 있기 때문에 어노테이션 없이도 타입이 생성됩니다.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      작게 좋았던 점
  </h1>
</div>

<!--
방금까지는 ReScript의 문법적인 내용을 다루며 가볍게 알아보았는데요.
이제 제가 직접 6개월 넘게 사용해 보면서 좋았던 점 중에 소소하지만 확실히 행복한 개발자 경험을 선사했던 것들을 공유해 보겠습니다.
-->

---

# 빌트인 포매터

작은 따옴표 vs 큰 따옴표 / 탭 사이즈 2 vs 4 / 세미콜론 붙이기 vs 말기

### 논쟁할 필요 없다

<!--
다른 언어를 사용할 때 작은 따옴표를 쓸 지 큰 따옴표를 쓸 지 탭의 사이즈를 2로 할 지 4로 할 지 세미콜론을 붙일지 말지 등의 규칙을 정하곤 하는데요.
저는 빅 테크 기업의 규칙을 가져오기도 하고, 팀원들과 합의를 할 때도 있었고, 린트를 잘 적용했는지 ci를 돌리기도 했던 경험이 있습니다.
프로젝트를 처음 세팅할 때 은근히 신경이 많이 쓰이는 부분이기도 한데요.

ReScript는 lint가 빌트인되어 있기 때문에 이런 갖가지 논쟁없이 모두가 같은 규칙을 알게 모르게 적용된 상태로 개발을 할 수 있게 됩니다.
-->

---

# 좌에서 우로, 위에서 아래로 읽기

```res {1|3-8}
validateAge(getAge(parseData(person)))

person -> parseData -> getAge -> validateAge

person
-> parseData
-> getAge
-> validateAge
```

<v-after>

**파이프 연산자** `->` 책 읽듯이 한 방향으로 읽기

</v-after>

<!--
초반에 화살표처럼 생긴 파이프 연산자를 언급하면서 방향을 바꿔준다고 했습니다.
많은 수의 함수를 합성하면 아마 이와 같이 코드를 작성하게 될 것입니다.
그렇다면 개발자는 person, parseData, getAge, validateAge의 순서로 안에서 밖으로 나오는 형태로 코드를 읽게 됩니다.

click!

파이프 연산자는 책 읽듯이 한 방향으로 코드를 읽게 해줍니다.
참고로 파이프 연산자는 문법 설탕일 뿐이므로 성능에는 영향을 미치지 않습니다.

안에서 밖으로 읽던 순서를 그대로 좌에서 우로 나열하듯이 코드를 작성할 수 있습니다.
또한, 위에서 아래로 쌓을 수도 있습니다.

특히나 다른 사람의 코드를 읽을 때 코드의 흐름을 쉽게 읽을 수 있어서 좋았습니다.
-->

---

# export & import 신경 안쓰기

```ts
export { default as Button } from "./Button";

export { default as Card } from "./Card";

export { default as Modal } from "./Modal";

export { default as Toast } from "./Toast";

export { default as Layout } from "./Layout";

export { default as Footer } from "./Footer";

export { default as Header } from "./Header";

export { default as Container } from "./Container";

export { default as Toc } from "./Toc";

export { default as Title } from "./Title";
```

<!--
ReScript에서는 export import를 작성하지 않아도 됩니다.
컴포넌트를 분리하다보면 10개 이상의 export 구문을 작성하곤 합니다.
파일의 위치가 바뀌거나 이름이 변경된 경우 등이 발생하면 함께 수정해 줘야 하는 번거로움이 있습니다.
-->

---

# export & import 신경 안쓰기

## 모든 .res 파일은 모듈

- 모든 모듈은 내보내진다.
- 인터페이스 파일을 사용하면 내보내고 싶은 모듈만 지정할 수도 있다.

```res
// TestComponent.res
module Button = {
  @react.component
  let make = () =>
    <button> {`click`->React.string} </button>
}
```

```js
// Generated by ReScript, TestComponent.js
function Playground$Button(Props) {
  return React.createElement("button", undefined, "click");
}
var Button = { make: Playground$Button };

exports.Button = Button;
```

<!--
모든 res 파일은 모듈로 취급됩니다. 그리고 모든 모듈은 내보내지는 특징이 있기 때문에 다른 파일에서 바로 사용할 수 있습니다.
물론 특정 모듈만 내보내고 싶다면 인터페이스 파일을 만들어서 내보낼 것들만 지정할 수도 있습니다.

하지만 모든 모듈이 내보내지기 때문에 ReScript 프로젝트의 파일 이름은 중복이 되면 안 됩니다.
조금은 불편하겠다고 생각이 들 수는 있지만 이 규칙 덕에 특정 파일을 검색할 때 한 개만 존재해 찾기가 편합니다.
같은 이름을 가진 모듈이 없으므로 리팩토링을 할 때도 유용합니다.
-->

---

# export & import 신경 안쓰기

```ts
import Container from '../components/Container';

import Button from '../components/Button';

import Button form '../어디더라?';
```

<!--
import할 컴포넌트를 찾아 닷닷슬래시를 연타해 보신 경험 있으신가요? 저는 있습니다.
IDE에 따라 import 위치를 자동으로 잡아주기도 하지만 그럼에도 꽤 귀찮은 작업입니다.

코드를 작성하다가 새로운 import가 필요해질 때면 화면을 위아래로 왔다 갔다 하며 수정하기도 했습니다.

React 프로젝트를 생각하면 한 페이지를 만들기 위해 컴포넌트, 라이브러리, hook 등 꽤 많은 import를 해야 하며
주기적으로 정리를 하지 않는다면 사용하지 않지만 수많은 import 사이에 묻혀서 잊힌 것들도 있을 겁니다.

그리고 import 되는 파일의 위치가 바뀌면 찾아서 다 변경해 주는 작업도 필요합니다.
-->

---

# export & import 신경 안쓰기

## 자동으로 프로젝트 안에서 모듈을 찾는다.

import할 파일의 위치를 몰라도, import 한 파일의 위치가 바뀌어도

코드를 변경하지 않아도 된다.

```res
// TestComponent.res

module Button = {
  @react.component
  let make = () =>
    <button> {`click`->React.string} </button>
}
```

```res
// TestPage.res

<TestComponent.Button />
```

<!--
ReScript는 프로젝트 안에서 알아서 모듈을 찾습니다.

import할 파일의 위치를 몰라도 상관없으며, import 했던 파일의 위치가 바뀌어도 수정하지 않아도 됩니다.
그저 모듈의 이름만 안다면 어디서든 사용할 수 있습니다.

암시적으로 import를 하기 때문에 해당 파일이 어떤 의존성을 가지는 지 한 눈에 파악하기 힘든 점은 있습니다.
하지만 ReScript는 의존하고 있는 파일에서 변경이 일어나 충돌의 여지가 생긴다면 컴파일 타임에 에러를 만들어 주므로 크게 단점이라고 생각이 든 적은 없습니다.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-orange-400 to-red-500">
      크게 좋았던 점
  </h1>
</div>

<!--
소소하지만 개발자 경험을 행복하게 만들었던 것들에 대해서 얘기했습니다.
지금부터는 제가 ReScript를 계속 사용하게 만든 것들에 대해서 얘기하고자 합니다.
-->

---

# 타입 추론

### 타입 어노테이션 없이 모든 표현식의 타입을 힌들리-밀너 타입 추론으로 확인

<br />

<div grid="~ cols-2 gap-2" m="-t-2">

```res
let add1 = (a, b) => a + b

let add2 = (a, b) => a ++ b

let add3 = (a, b) => a +. b
```

```plain
(int, int) => int

(string, string) => string

(float, float) => float
```

</div>

<!--
ReScript의 꽃이라고 얘기할 수 있는 힌들리 밀너 타입 추론 시스템을 소개합니다.
타입 어노테이션 없이도 각 함수들은 오른쪽과 같은 타입을 가지게 됩니다.

add1으로 추론되는 과정을 설명하자면 +연산자는 int에만 사용할 수 있습니다.
즉, a 와 b 인자는 int 여야만하므로, int를 받고, int를 반환한다고 추론할 수 있게 됩니다.

add2의 ++ 연산자는 string, add3의 +. 연산자는 float을 대상으로 한 연산자이므로 타입 추론이 가능해지게 됩니다
-->

---

# 타입 추론

**값의 형태가 맞는 레코드 타입 선언을 찾는다.** data는 person 타입으로 추론된다.

<v-click>

## 타입 검사를 통과한다면 런타임에 잘못 처리되는 값이 없음이 보장된다.

</v-click>

<img class="rounded-xl mt-5" src="/images/record.png" alt="타입 추론" />

<!--
연산자에만 국한되는 것은 아닙니다.

int 타입인 age, string 타입인 name을 필드로 갖는 person이라는 레코드 타입을 선언합니다.
그리고 data 에 age 필드만 작성하게 되면 타입 에러가 발생합니다.  
name 필드가 선언되지 않았다는 에러 메시지를 확인할 수 있는데요.
즉 data는 자동으로 person이라는 타입으로 추론된 것입니다.

click!

실제로 프로덕션 코드를 작성할 때도 어노테이션을 명시하는 경우는 거의 없습니다.
타입 어노테이션이 눈에 보이지 않아 불편할 수도 있다고 생각할 수 있으나
IDE에서 렌즈를 켜서 타입을 다 확인할 수 있습니다.

강타입을 사용하면 개발이 어렵겠다고 생각할 수도 있지만 안전한 타입 시스템 안에서 개발을 하다보면 굉장히 편합니다.
개발자의 실수로 잘못된 값을 넣는 일이 없어지고, 어차피 컴파일 때 에러가 발생할 것이라는 믿음이 있기 때문입니다.
-->

---

# Variant

## 합타입

Red 또는 Blue 또는 Yellow 표현한다.

```res
type color = Red | Blue | Yellow

let myColor = Red
```

<br />

<v-click>

배리언트 생성자는 추가 값을 가질 수 있다.

```res {1|3}
type result = Pending | Success | Fail

type result = Pending | Success({data: string}) | Fail
```

</v-click>

<!--
ReScript의 안전한 타입시스템에는 유용하고 멋진 타입이 있습니다.
배리언트라고 불리는 노미널타입이자 합타입인데요.
color 타입은 Red 또는 Blue 또는 Yellow를 뜻합니다.
Red Blue Yellow는 string 타입처럼 보일 수는 있지만 배리언트 태그라고 칭하며 생성자입니다.
myColor에 Red를 바인딩 하면 myColor는 color 타입으로 추론되게 됩니다.

click!

많이 쓰이는 패턴이죠 요청 후에 상태를 표현하는 result 타입에 Pending Success Fail를 표현해 봤습니다.
TypeScript에서의 유니온 타입과 비슷하게 느껴지실 거 같은데요.
크게 다른 점은 배리언트 생성자는 추가 값을 가질 수 있습니다.

click!

요청 후 상태 값을 나타내는 정도로 끝나지 않고, 성공했을 경우에 data를 담도록 할 수 있습니다.
예시와 같이 가독성을 높이기 위해 인라인 레코드 형태로 인자를 받을 수 있습니다.
-->

---

# 패턴 매칭

## 데이터 형태에 따른 switch 구문

구조 분해를 하고, 각각 분해된 결과의 오른 편에 작성된 코드가 실행된다.

```res
type sns = Facebook(string) | Twitter(string) | None

let name = switch data {
  | Facebook(name) => name
  | Twitter(name) => name
  | None => ""
}
```

<!--
방금 소개한 배리언트는 패턴매칭에서 최고의 빛을 발합니다.
패턴매칭은 데이터형태에 따른 switch 식이며, 구조 분해를 하고 각각 분해된 결과의 오른 편에 작성된 코드가 실행됩니다.

data의 타입이 sns 일 때 Facebook, Twitter 그리고 None 의 패턴에 맞는 결과물을 반환할 수 있습니다.
string을 인자로 받는 배리언트 태그는 인자를 꺼내서 사용할 수 있습니다.

사실 여기까지만 본다면 if문에 비해 표현이 간결한 게 다인가?라고 생각하실 수 있습니다.
첫 번째 다른 점은 ReScript의 switch는 표현식이기 때문에 예시 코드에서도 볼 수 있듯 변수에 할당할 수 있습니다.
-->

---

# 패턴 매칭

누락 된 패턴이 있는지 컴파일 시점에 검사한다.

<img class="rounded-xl mt-5" src="/images/pattern.png" alt="패턴 매칭" />

<!--
두 번째 다른 점은 튜플에서 패턴 매칭을 구성할 수 있다는 점입니다.

두 개의 boolean 요소를 가지는 튜플 형태의 data를 패턴 매칭해본다면
true, true / true, false / false, true / false,false 총 4가지의 경우가 나옵니다.

이 4가지의 경우를 and로 묶어주지 않고, 단지 패턴을 만들어서 매칭할 수 있습니다. 정말 멋진 기능이고, 프로덕션에서도 정말 많이 사용합니다.

if else로 어지럽혀진 코드에서 누락된 케이스가 하나도 없다고 장담할 수 없을 것입니다.
예시를 보시면 false,false 패턴을 명시하지 않았더니 컴파일러가 컴파일 시점에 누락된 패턴을 검사해서 한 가지 case가 누락되었다고 알려주기까지 합니다.
-->

---

# 패턴 매칭 & 배리언트

<br />

```jsx {1-8|9-11}
<button onClick={() => router.push('/')}>
  Home으로
</button>

<button onClick={() => router.push('/post')}>
  Post로
</button>

<button onClick={() => router.push('/post?id=123')}>
  id와 함께 Post로
</button>
```

<!--
패턴 매칭과 배리언트를 사용해서 안전하게 코드를 작성하고 있는 한 가지 예시를 보여드리겠습니다.
프론트엔드에서 Route를 이동시키는 코드를 많이 작성하게 됩니다.
문자열 path 값을 사용해 이동을 시키는 것이 보편적인데요.

click!

post 라우트에 id라는 쿼리 파라미터가 추가된 상황이라면 이와 같이 id=123을 작성하게 될 것입니다.
만약 post 페이지로 이동 시키는 코드가 프로젝트 내에 엄청 많다면 어떻게 될까요? 전체 검색을 통해 찾아서 id라는 쿼리파라미터를 추가해줘야 할 것입니다.

지금은 쿼리파라미터가 하나인 상황이지만 경우에 따라 여러 개가 될 수도 페이지마다 사용되는 파라미터가 달라질 수도 있습니다.
그리고 사람의 실수로 잘못 입력하는 경우도 생기고 굉장히 불안하게 느껴집니다.
-->

---

# 패턴 매칭 & 배리언트

```res {1|3-8,10,14|all}
type page = Home | Post

let toString = page => {
  switch page {
    | Home => "/"
    | Post => "/post"
  }
}

<button onClick={_=> router->Next.Router.push(Route.toString(Home))}>
  {`Home으로`->React.string}
</button>

<button onClick={_=> router->Next.Router.push(Route.toString(Post))}>
  {`Post로`->React.string}
</button>
```

<!--
ReScript에서는 배리언트와 패턴매칭을 사용해 굉장히 안전하게 개발을 할 수 있습니다.
page들에 대응하는 배리언트 타입으로 Home과 Post를 만듭니다.

click!

page 배리언트 패턴들에 매칭되는 라우트 경로 문자열을 반환하는 toString 식을 만듭니다.

click!

라우트를 이동시킬 때 toString을 사용한다면 인자로 배리언트를 넣게 되는데
page 타입에 없는 배리언트 값을 넣을 수 없으므로 타입을 이용해 안전하게 라우트들을 명시할 수 있습니다.
-->

---

# 패턴 매칭 & 배리언트

```res {1,6|15-16|10-13}
type page = Home | Post({id: string})

let toString = page => {
  switch page {
    | Home => "/"
    | Post({id}) => {...}
  }
}
...
<button onClick={_=>
    router->Next.Router.push(Route.toString(Post{id: 123}))}>
  {`id와 함께 Post로`->React.string}
</button>

// 컴파일 에러 발생
<button onClick={_=> router->Next.Router.push(Route.toString(Post))}>
  {`Post로`->React.string}
</button>
```

<!--
Post에 id 라는 쿼리파라미터가 생긴다면 어떻게 될까요?

click!

Post 배리언트 생성자에 id 인자를 추가하게 되면, 당연하게도 Post 를 사용하고 있던 모든 코드에 에러가 발생합니다.
바로 id 인자가 필요한데 넣어주지 않았기 때문이죠

click!

컴파일 타임에 에러가 펑펑 터지기 때문에 Post를 사용하는 모든 곳에 정확하게 파라미터를 추가 해줄 수 있게 됩니다.
즉, 의존성의 변화에 대응하기 훨씬 수월해집니다.
-->

---

# Null

```plain
Uncaught TypeError: Cannot read properties of null (reading 'value')
```

<div class="section">
  <span class="text-center italic text-3xl font-serif">
  I call it my billion-dollar mistake.<br />
  It was the invention of the null reference in 1965<br />
  - Tony Hoare -
  </span>
</div>

<!--
패턴매칭은 이만 마치고 null에 대해서 얘기해보겠습니다.  
퀵소트를 고안해낸 컴퓨터 과학자인 토니 호어는 이렇게 얘기한 적이 있습니다.
저는 그것을 저의 10억 달러 실수라고 부릅니다. 그것은 1965년에 null을 발명한 것입니다.

null 참조 에러, undefined 에러 등 많이 만나 보셨을 듯합니다.
null은 자바스크립트 개발자들을 꽤 괴롭히는 존재이기도 하고 배포 후 런타임에서 생겨서 골치 아프게 하기도 합니다.
-->

---

# option

## 타입으로 존재하지 않는 값을 표현한다.

- ReScript에 null 또는 undefined에 대한 개념이 없습니다.
- option 타입은 배리언트입니다.

<br />

```res
type option<'a> = None | Some('a)

let 계세요? = 없음 | 사람(정미량)
```

<!--
ReScript에서는 if 문으로 null 또는 undefined일 경우를 검사하지 않아도 됩니다.
ReScript는 null 또는 undefined에 대한 개념이 없기 때문입니다. 즉, 정의되지 않은 것은 없습니다.
대신 존재하지 않는 값을 다루는 방법이 있습니다.

존재하지 않는 값과 존재하는 값을 option 타입으로 표현할 수 있습니다.
option 타입의 정의는 None 또는 Some 입니다. 그리고 option 타입은 단지 앞서 봤던 배리언트일 뿐입니다.

값이 있을 수도 없을 수도 있다는 개념이 처음에는 생소했으나 값을 핸들링할 때 예외 처리를 확실히 할 수 있어서 좋았습니다.
-->

---

# 예시

## URL 생성하는 API 요청 후 받은 응답을 보여주기

<br />

<div class="flex items-center mt-5">
  <button class="text-3xl bg-gray-300 p-5 rounded-xl font-light text-black">[URL 생성] 요청</button>
  <span class="text-3xl ml-5 font-semibold">요청 중...</span>
</div>

<div class="flex items-center mt-5">
  <button class="text-3xl bg-green-300 p-5 rounded-xl font-light text-black">[URL 생성] 완료</button>
  <span class="text-3xl ml-5 font-semibold">miryang.dev</span>
</div>

<div class="flex items-center mt-5">
  <button class="text-3xl bg-rose-300 p-5 rounded-xl font-light text-black">[URL 생성] 실패</button>
  <span class="text-3xl ml-5 font-semibold">요청 실패</span>
</div>

<!--
제가 앞에서 ReScript를 영업하기 위해 얘기했던 것들을 프로덕션 코드에서 어떻게 사용하는지 보여주기 위해 예시를 가져왔습니다.

저는 얼마 전에 회사에서 버튼을 누르면 URL을 발급하는 기능을 작성했었습니다.
프론트엔드에서 흔하게 볼 수 있는 상황이죠.
버튼을 누르면 API 요청을 하고 요청 전까지는 요청 중을 띄우고, 응답이 제대로 오면 데이터를, 에러가 생기면 요청 실패를 띄우는 코드를 ReScript로 작성하였습니다.
-->

---

# 예시

```res {1|5|7-13} {maxHeight: 100}
type result_t = Pending | Success(string) | Fail

@react.component
let default = () => {
  let (result, setResult) = React.useState(_ => Pending)

  let handleClick = e => {
    e->ReactEvent.Synthetic.preventDefault
    let response {
      | Some(res) => setResult(_ => Success(res))
      | None => setResult(_ => Fail)
    }
  }

  <>
  <button onClick={handleClick}> {`URL 생성` -> React.string} </button>
  {
    switch result {
      | Pending => {`요청 중...` -> React.string}
      | Fail => {`요청 실패` -> React.string}
      | Success(url) => {url -> React.string}
    }
  }
  </>
}
```

<!--
result_t 타입은 응답 상태를 나타내는 배리언트입니다. Pending과 Fail이 있고, string을 인자로 받는 Success가 있습니다.

click!

응답 상태를 담기 위해 useState hook을 사용해 result라는 상태를 만들었습니다.
초깃값을 Pending으로 줬기 때문에 만약 setResult에 result_t에 해당하는 타입을 인자로 주지 않는다면 타입 에러가 생기게 됩니다.
초깃값을 이용해 result가 result_t 타입으로 추론되었기 때문입니다.

click!

button을 클릭했을 때 실행될 handler인 handleClick 함수입니다.
Api에 요청 후 응답을 response에 담고, option 타입인 response를 패턴매칭으로 처리합니다.
-->

---

# 예시

```res {9-11|16} {maxHeight: 100}
type result_t = Pending | Success(string) | Fail

@react.component
let default = () => {
  let (result, setResult) = React.useState(_ => Pending)

  let handleClick = e => {
    e->ReactEvent.Synthetic.preventDefault
    let response {
      | Some(res) => setResult(_ => Success(res))
      | None => setResult(_ => Fail)
    }
  }

  <>
  <button onClick={handleClick}> {`URL 생성` -> React.string} </button>
  {
    switch result {
      | Pending => {`요청 중...` -> React.string}
      | Fail => {`요청 실패` -> React.string}
      | Success(url) => {url -> React.string}
    }
  }
  </>
}
```

<!--
response에 값이 있을 때는 값을 담은 Success 타입으로, 값이 없을 때는 Fail로 result 상태를 변경합니다.

click!

다른 언어로 React를 사용하고 계시던 분들은 이상하게 느껴질 부분이 React.string 일 거 같습니다.
React element로서의 타입도 체크되어야 하기 때문에 문자열도 React.string 함수를 이용해 변환해 줘야 합니다.
object나 배열, Date 등을 그대로 노출시키는 실수를 하지 않게 되었습니다만 사실 저 또한 아직까지 조금 번거롭다고 느껴지는 부분이기도 합니다.
-->

---

# 예시

```res {18-21|15-24} {maxHeight: 100}
type result_t = Pending | Success(string) | Fail

@react.component
let default = () => {
  let (result, setResult) = React.useState(_ => Pending)

  let handleClick = e => {
    e->ReactEvent.Synthetic.preventDefault
    let response {
      | Some(res) => setResult(_ => Success(res))
      | None => setResult(_ => Fail)
    }
  }

  <>
  <button onClick={handleClick}> {`URL 생성` -> React.string} </button>
  {
    switch result {
      | Pending => {`요청 중...` -> React.string}
      | Fail => {`요청 실패` -> React.string}
      | Success(url) => {url -> React.string}
    }
  }
  </>
}
```

<!--
result 상태는 result_t의 배리언트 타입이므로 패턴 매칭을 사용해 상태마다 다른 엘리먼트가 렌더링되게 할 수 있습니다.
Pending 일 때는 요청 중, Fail 일 때는 요청 실패 그리고 Success 일 때는 인자의 값을 꺼내서 값을 렌더 합니다.

if 문과 타입 어노테이션을 작성하지 않았는데도 누락된 케이스도 없고, 안전한 타입 안에서 깔끔하게 코드를 작성할 수 있었습니다.
정말 멋지다고 생각합니다.

click!

let default는 그럼 무엇을 반환할까요? 바로 마지막 줄에 React fragment로 감싸진 영역을 반환합니다.
처음에 언급했듯이 마지막 구문은 암묵적으로 반환되기 때문입니다.

정말 간결한 표현의 매력을 가진 ReScript 사용해보고 싶은 마음이 막 생기셨을 거 같아요.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tl from-yellow-300 to-rose-500">
      아직도 망설인다면
  </h1>
</div>

<!--
그렇지만 아직도 망설이시는 분들을 위해 이 섹션을 마련해 보았습니다.
-->

---

# 점진적 채택

<div class="section flex-col">
  <span class="text-center italic text-3xl">
  ReScript를 도입하고 싶은데 <br />
  프로젝트를 폭파하고 새로 시작하기에 <br />
  리스크가 너무 큽니다.
  </span>

  <v-click>
  <div class="text-160px italic absolute top-30 text-rose-500">x</div>
    <span class="text-center font-bold text-3xl mt-20">
    ReScript를 부분적으로 적용하면서 <br />
    원활한 통합이 가능
    </span>
  </v-click>

  <div class="h-150px" />
</div>

<!--
지금까지의 발표를 들으며 ReScript 정말 좋다! 나도 써보고 싶다! 도입하고 싶다! 생각은 했지만
프로젝트의 언어를 갑자기 바꿀 수도 없는 노릇이고, 새로 시작하기에도 리스크가 너무 커서 당장은 무리라고 판단하신 분들이 계실 텐데요.

click!

ReScript를 프로젝트에 부분적으로 적용하면서 원활한 통합이 가능합니다.

프로젝트에 JavaScript나 TypeScript를 사용하고 있었다면 ReScript로 작성한 코드를 한 줄 한 줄 늘리면서 점진적 채택을 할 수 있습니다.
-->

---

# 점진적 채택

raw JavaScript 코드를 작성할 수 있다.

```res
let add = %raw(`
  function(a, b) {
    console.log("hello from raw JavaScript!");
    return a + b
  }
`)

Js.log(add(1, 2))
```

- 타입 어노테이션이 없으면 추론이 된다.
- 타입 어노테이션을 줘서 타입 안전하게 할 수도 있다.

<!--
ReScript 파일에 raw JavaScript 코드를 작성할 수 있습니다.

만약 나는 ReScript에 적응했지만 동료가 힘들어한다면 ReScript 파일에 raw JavaScript를 작성하게 하며 천천히 스며들게 할 수도 있습니다.
-->

---

# genType

[ts-belt](https://github.com/mobily/ts-belt)

```res
// ts-belt/src/Option/Option.res
%comment("Returns `Some(value)` if the provided value is not falsy, otherwise, returns `None`.")
@gentype
let fromFalsy = value => value ? Some(value) : None
```

<div class="text-center text-3xl">↓</div>

```ts
// ts-belt/src/Option/Option.ts
export declare type ExtractValue<T> = Exclude<T, null | undefined>;
export declare type Option<A> = A | null | undefined;
export declare const Some: <A>(value: NonNullable<A>) => Option<A>;
export declare const None: Option<never>;

export declare function fromFalsy<A>(value: A): Option<ExtractValue<A>>;
```

<!--
TypeScript 코드 베이스에서 작업 중이고, 타입을 유지하면서 ReScript 코드를 합치고 싶을 수도 있습니다.
그렇다면 genType을 사용해 ReScript를 TypeScript 로 내보낼 수 있습니다.

TypeScript 환경을 타깃으로 한 함수형 프로그래밍 유틸리티 라이브러리인 ts-belt에서도 genType을 사용한 아웃풋을 사용하고 있습니다.

한 예시를 들고 왔는데요.
value가 있으면 Some(value)를 없으면 None을 리턴하는 fromFalsy를 gentype으로 내보내면 아래와 같은 TypeScript 코드로 변환됩니다.
ReScript의 타입 시스템을 이용하고 싶다면 이런 방법으로 활용할 수도 있습니다.

-->

---

# 점진적 채택

## TypeScript로 작성된 블로그 코드를 ReScript로 변경하고 있습니다.

TypeScript & ReScript & JavaScript 3가지 언어를 동시에 사용할 수 있다.

<img class="w-600px m-auto" src="/images/lan-percent.png" alt="ts67per res19per" />

<!--
저는 실제로 제 개발 블로그를 TypeScript로 작성했다가 ReScript로 바꾸는 작업을 하고 있습니다.
언어 사용도를 보면 TypeScript 67%에 ReScript가 19%입니다.
이렇게 일부만 ReScript를 채택해 사용한다는 것이 정말 가능합니다.
그렇다면 더 이상 ReScript 도입을 미룰 이유가 없습니다.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-t from-orange-600 to-rose-200">
      아쉬웠던 점
  </h1>
</div>

<!--
지금까지 ReScript의 장점과 도입해야 할 이유에 대해서 얘기했는데요.
그렇다면 제가 사용해 보면서 아쉬웠던 점 그리고 어려웠던 점을 공유하고자 합니다.
-->

---

# 바인딩

### 자바스크립트 함수를 사용하기 위해 바인딩을 해야 한다.

<br />

Next.js의 Head 컴포넌트 바인딩 코드

```res
// https://github.com/MoOx/rescript-next
module Head = {
  @module("next/head") @react.component
  external make: (~children: React.element) => React.element = "defalut"
}
```

Web api의 addEventListener, removeEventListener 바인딩 코드

```res
@val @scope("document")
external addEventListener: (string, t => unit) => unit = "addEventListener"
@val @scope("document")
external removeEventListener: (string, t => unit) => unit = "removeEventListener"
```

<!--
바인딩이라는 용어를 들어본 적이 있으신가요? 저는 평생 없었는데요. 그만큼 생소하기도 한 개념이었습니다.
검색으로도 책으로도 배울 수 없다는 게 제일 어려운 부분이었는데요.

저는 Remix를 바인딩 한 코드를 무작정 읽으면서 바인딩 하는 방법을 익혔고, 그 힘겨웠던 과정을 글로 남겨두기도 했습니다.
그렇다면 바인딩이 뭘까요? 다른 언어들에서는 FFI(Foreign Function Interface)라고도 불리고, 래퍼(Wrapper)라고도 불린다고 합니다.
현재 언어에서 다른 언어로 쓰인 코드를 호출하기 위한 인터페이스를 칭합니다.

예시는 Next.js의 Head 컴포넌트를 사용하기 위한 바인딩 코드입니다.
인자로 React.element 타입인 children을 받고, React.element를 반환하는 함수 시그니처를 작성했습니다.

사용하는 라이브러리의 타입을 찾아 코드를 살펴보신 적이 있으신가요?
브라우저 Dom API들의 함수 시그니처가 어떻게 되는지 찾아본 적 있으신가요?
바인딩을 하게 되면 항상 타입을 찾아 헤매거나 누군가 해두진 않았는지 찾게 됩니다.
-->

---

# [rescript-bindings](https://github.com/green-labs/rescript-bindings)

<img class="w-500px m-auto" src="/images/rescript-bindings.png" alt="rescript-bindings" />

<!--
그린랩스에서는 ReScript 바인딩들을 패키지로 공개하고 있고, 제가 관리하고 있습니다.  
만약 바인딩에 대해서 감이 안오거나 예시를 보고 싶다면 이 저장소를 참고하시기 바랍니다.
-->

---

# 커뮤니티

stackoverflow 또는 검색으로는 도움 받기 힘들다

<v-click>
  
  **[ReScript Forum](https://forum.rescript-lang.org/) 을 이용합니다.**

</v-click>

<img class="w-800px m-auto" src="/images/sof.png" alt="stackoverflow" />

<!--
다음으로 어려운 점은 커뮤니티 규모가 작다는 점입니다.

Stackoverflow에서 rescript 태그를 조회해 보면 69개의 질문만이 있습니다.
stackoverflow의 도움을 받기도 힘들고, 검색으로도 원하는 정보를 얻을 가능성이 현저히 낮습니다.

당연하게도 블로그나 유튜브에 한국어 자료는 없다시피 하기 때문에 영어를 잘 하지 못한다면 정보를 확보하기 어렵습니다.

click!

ReScripts는 포럼을 자체 운영하고 있습니다.
작지만 알차서 활발하게 운영이 되고 있고, 저도 몇 번 질문을 올렸는데 24시간 이내에 답변이 달려서 도움을 충분히 받을 수 있습니다.

그리고 신생 커뮤니티의 특징일 수도 있지만 뉴비에게 굉장히 친절하게 알려줍니다.
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-t from-orange-100 to-rose-500">
      마무리
  </h1>
</div>

<!--
ReScript를 같이 하기 위한 파티원을 모으는 발표였는데 모집이 되었길 바라며 마무리를 하려고 합니다.
-->

---

# Relay

[relay.dev](https://relay.dev)

- 그래프큐엘 클라이언트 라이브러리

<br />

```res
module Query = %relay(`
  query IndexQuery {
    user {
      name
      age
    }
  }
`)

type props = { data: IndexQuery_graphql.Types.response}
```

<!--
마무리를 하기 전에 마지막으로 한 가지 얘기하고 싶은 것이 있습니다.
만약 ReScript를 사용해보고 싶다고 생각이 드셨다면 Relay를 같이 사용해보시는 걸 강력 추천드립니다.

릴레이는 자체 컴파일이 실행되기 때문에 쿼리에 어떤 인자가 필요한 지를 타입으로 컴파일 타임에 알 수 있습니다.
존재하지 않는 걸 부를 수 없고, ReScript와 결합한다면 타입 세이프티하게 쿼리를 사용할 수 있게 됩니다.
-->

---

# 지금 설치하세요

<br />

```shell
npm install rescript --save-dev
```

<!--
정말 마무리를 해보겠습니다.  
학습 비용이 높다는 점과 타입 언어에 익숙하지 않다면 적응하는 데 시간이 걸릴 수는 있습니다.
하지만 불변성과 순수 함수를 지향하는 함수형 프로그래밍 그리고 안전한 타입 시스템 안에서 개발을 하는 경험을 꼭 해보셨으면 합니다.

이렇게 다양하게 소개하며 ReScript를 같이하자고 얘기했는데 명령어를 쳐서 한 번 설치해보시는 건 어떠신가요? 
-->

---

<div class="section">
  <h1 class="text-90px bg-clip-text text-transparent bg-gradient-to-tr from-pink-100 to-rose-500">
      감사합니다!
  </h1>
</div>

<!--
이상 2022 FECONF 에서 ReScript 같이해요의 발표를 마치도록 하겠습니다.  
오늘 제 발표가 듣는 분들의 무궁한 발전과 번영의 초석이 되기를 기원합니다.  
감사합니다.
-->

---

# 레퍼런스

- https://unsplash.com/photos/z8kriatLFdA
- https://www.youtube.com/watch?v=WN5UfUjVTNE
- https://www.youtube.com/watch?v=tn0zt7U7roY
- https://www.youtube.com/watch?v=dr1PskGSdU4
- https://www.youtube.com/watch?v=ZY4n7B0pZFw
- https://www.youtube.com/watch?v=XWgL51JSbGI
- https://www.youtube.com/watch?v=kAWP0laFz6M
- https://green-labs.github.io/why-rescript
- https://rescript-lang.org

# React State

React의 state는 “변경”을 다루기 위한 요소이다. 대략적으로 이야기하면, 어떤 컴포넌트의 state가 바뀌면 해당 컴포넌트와 하위 컴포넌트를 다시 렌더링하게 된다. 아무렇게나 막 만들어도 되지만, 일관성과 효율을 위해 DRY 원칙을 따르는 SSOT를 만든다.

* [**DRY (Don’t Repeat Yourself)**](https://ko.wikipedia.org/wiki/%EC%A4%91%EB%B3%B5%EB%B0%B0%EC%A0%9C) : 중복 배제
* [**SSOT (Single Source of Truth)**](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%A7%84%EC%8B%A4\_%EA%B3%B5%EA%B8%89%EC%9B%90) : 단일 진실 공급원

&#x20;

즉 하나의 데이터에 대해서 props로 자식 컴포넌트들에게 넘겨주는 과정에서 불필요하게 state를 만들 필요는 없다. 상위 컴포넌트의 state가 변경되면 알아서 하위 컴포넌트들의 값들이 재렌더링된다. 또한 불필요하게 넘겨받는 데이터들을 state로 만들면 중복으로 state를 갖게 되어 단일한 데이터의 공급원이 아니게 되므로 실제 데이터가 변경되었을 때 바뀌지 않는 등 혼란을 빚게 된다.

&#x20;

**React State의 조건:**

1. 변경돼야 한다. 변경되지 않는 건 state로 다룰 가치가 없다.
2. 부모 컴포넌트가 props를 통해 전달한다면 state가 아니다
3. 다른 state나 props를 이용해 계산 가능하다면 state가 아니다.

다루는 상태가 너무 많으면 복잡할 수 있다. TypeScript를 잘 쓰면 직접 관리하는 props로 넘겨줄 시 type 또는 interface로 잘 정의한다면, 하나의 객체로 넘겨주어 보여지는 상태의 수를 줄여줄 수 있다. 그렇다면 그 상태를 누가 관리해야 할까? 더 정확히는, 상태를 누가 소유해야 할까? (React만 쓴다면) 해당 상태에 의존적인 컴포넌트를 모두 포함하는 상위 컴포넌트가 상태를 소유해야 한다.

* [“Lifting State Up”](https://ko.reactjs.org/docs/lifting-state-up.html)
* [Sharing State Between Components](https://beta.reactjs.org/learn/sharing-state-between-components)

&#x20;

**Lifting State Up**

해당 컴포넌트의 상태에 의존적인 컴포넌트를 모두 포함하는 상위 컴포넌트가 상태를 소유해야 하므로 상위 컴포넌트까지 state 끌어올리기 작업을 해야한다. 그 후 state와 setState를 props로 해당 하위 컴포넌트까지 내려주어야 한다.

&#x20;

**Inverse Data Flow**

하위 컴포넌트의 props로 setState나 handleChange와 같은 함수를 전달한다. 흔히 콜백 함수라고 부른다. TypeScript(정확히는 JavaScript)는 함수가 일급(first-class) 객체다. 즉, 어떤 함수를 다른 함수에 인자로 넘겨주거나, 어떤 함수를 리턴값으로 사용할 수 있다. 익명 함수, 클로저 등과 함께 사용하면 시너지가 크다고 한다.

&#x20;

* [일급 함수](https://developer.mozilla.org/ko/docs/Glossary/First-class\_Function) : 프로그래밍 언어는 해당 언어의 함수들이 다른 변수처럼 다루어질 때 일급 함수를 가진다고 한다. 예를 들어, 일급 함수를 가진 언어에서 함수는 다른 함수들에 전달 인자로 제공되고, 다른 함수에 의해 반환될 수 있으며, 변수에 값으로서 할당될 수 있다.
* [일급 객체](https://velog.io/@reveloper-1311/%EC%9D%BC%EA%B8%89-%EA%B0%9D%EC%B2%B4First-Class-Object%EB%9E%80) : 다른 객체들에 일반적으로 적용 가능한 연산을 차별점 없이 모두 지원하는 객체를 가리킨다. [JavaScript에서 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions)는 다른 함수로 전달되거나 반환받을 수 있고, 변수와 속성을 할당받을 수도 있기 때문에 일급 객체에 해당한다. 일급 객체의 조건은 다음과 같다.\

  * 변수에 할당(assignment)할 수 있다.
  * 다른 함수를 인자(argument)로 전달 받는다.
  * 다른 함수의 결과로서 리턴될 수 있다.

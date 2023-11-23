# React의 Hook

#### React Hook 이란

Hooks 는 리액트 v16.8 에 새로 도입된 기능으로서, 함수형 컴포넌트에서도 상태 관리를 할 수 있는 useState, 그리고 렌더링 직후 작업을 설정하는 useEffect 등의 기능등을 제공하여 기존의 함수형 컴포넌트에서 할 수 없었던 다양한 작업을 할 수 있게 해준다.

복잡한 컴포넌트들을 이해하기 쉽도록 Hook을 통해 서로 비슷한 것을 하는 작은 함수의 묶음으로 컴포넌트를 나누는 방법을 사용할 수 있다. 예를 들어 해당 컴포넌트에서 굳이 필요없는 상태관리 관련 코드들을 하나로 묶어서 빼서 보다 명확하게 코드를 작성할 수 있다.



기존:

* 상태를 가진 컴포넌트는 Class Component로 만들고, props만 사용하는 재사용이 용이한 작은 컴포넌트는 Function Component로 작성.
* Redux에서도 비슷한 구분이 존재했다.
  * [Presentational and Container Components - Dan Abramov](https://medium.com/@dan\_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

현재:

* 그냥 Function Component만 사용.
* 상태 관리 유무를 바로 알기 어려움 = 신경쓰지 않아도 됨.
* 복잡한 요소는 전부 Hook으로 격리 및 재사용 가능.

#### Hooks

*   useState

    `useState` is a React Hook that lets you add a [state variable](https://react.dev/learn/state-a-components-memory) to your component.



* useEffect\
  렌더링 이후 해야 할 일, 즉 React의 외부와 관련된 일을 정해줄 수 있다. 기본적으로 렌더링 때마다 실행되므로, 의존성 배열을 통해 언제 이펙트를 실행할지 지정할 수 있다(= 불필요한 경우에 건너뛸 수 있다). 함수를 리턴함으로써 종료 처리를 할 수 있다. 의존성 배열에서 아무 것도 지정하지 않으면 맨 처음에 딱 한번만 실행하게 할 수 있다. 주로 API를 호출해서 데이터를 얻을 때 사용한다.



* useContext\
  `useContext` is a React Hook that lets you read and subscribe to [context](https://react.dev/learn/passing-data-deeply-with-context) from your component.



*   useRef

    `useRef` is a React Hook that lets you reference a value that’s not needed for rendering.



    컴포넌트의 생애주기 전체에 걸쳐서 유지되는 객체. 즉, 컴포넌트가 없어질 때까지 동일한 객체가 유지된다. 객체 자체가 값은 아니고, 값을 참조하기 위한 객체. 즉, 언제든지 값을 변경할 수 있다. 상태(state)가 변경되면 해당 컴포넌트와 하위 컴포넌트를 다시 렌더링하지만, 레퍼런스 객체의 현재 값(current)이 바뀌더라도 렌더링에 영향을 주지 않는다.\


    주요 용도:

    1. 컴포넌트가 사라질 때까지 동일한 값을 써야 하는 경우. ⇒ input 등의 ID 관리.
    2. (특히 useEffect 등과 함께 쓰면서 만나게 되는) 비동기 상황에서 현재 값을 제대로 쓰고 싶은 경우.


*   useLayoutEffect

    `useLayoutEffect` is a version of [`useEffect`](https://react.dev/reference/react/useEffect) that fires before the browser repaints the screen.\
    \
    \- `useEffect`의 이펙트는 DOM이 화면에 그려진 이후에 호출된다.

    \- `useLayoutEffect`의 이펙트는 DOM이 화면에 그려지기 전에 호출된다.

    \-  따라서 렌더링할 state가 이펙트 내에서 초기화되어야 할 경우, 사용자 경험을 위해 `useLayoutEffect`를 활용하자!\


{% embed url="https://merrily-code.tistory.com/46" %}

#### React StrictMode&#x20;

\<React.StrictMode>로 컴포넌트 전체를 감쌀 경우, 예상치 못한 Side Effect를 찾으려고 Effect 등을 두 번씩 실행함. 평소에는 큰 문제가 없지만, API 등을 사용하면 이상하다고 느낄 수 있으니 참고할 것.

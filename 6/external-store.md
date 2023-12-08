# External Store

## 계층화 아키텍처 (Layered Architecture)

Layered Architecture는 소프트웨어 개발에서 가장 일반적으로 널리 사용되는 아키텍처이다. 구성되는 계층의 숫자에 따라 N 계층 아키텍처 (N-tier Architecture) 라고도 한다.

각 계층은 어플리케이션 내에서의 특정 역할과 관심사(화면 표시, 비즈니스 로직 수행, DB 작업 등)별로 구분된다. 이는 Layered Architecture 의 강력한 기능인 **관심사의 분리 (Separation of Concern)** 를 의미한다. 특정 계층의 구성요소는 해당 계층에 관련된 기능만 수행한다. 이런 특징은 높은 유지보수성과 쉬운 테스트라는 장점이 존재한다.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



## Flux Architecture

* 대규모 애플리케이션에서 데이터 흐름을 일관성 있게 관리함으로써 프로그램의 예측가능성을 높이기 위해 등장
* 기존의 MVC 패턴 : Model에 데이터를 저장하고, Controller를 이용하여 Model의 데이터를 관리(CRUD)한다. Model의 데이터가 변경되면 View로 전달되어 사용자에게 보여진다. 또한 중요한 점은 사용자가 View를 통해 데이터를 입력하면 View 역시 Model을 업데이트할 수 있다는 점이다. 즉 데이터가 양방향으로 흐를 수 있다는 것이다. 이 과정에서 Model의 개수가 많아질수록 많은 의존성을 갖게 되어, 각 Model에서 발생한 이벤트가 애플리케이션 전체로 퍼져나갈 때 이를 예측하기 힘들어진다.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* Flux는 사용자 입력을 기반으로 Action을 만들고 Action을 Dispatcher에 전달하여 Store(Model)의 데이터를 변경한 뒤 View에 반영하는 단방향의 흐름으로 애플리케이션을 만드는 아키텍처이다.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

## useReducer

useReducer는 State(상태)를 관리하고 업데이트하는 Hook인 useState를 대체할 수 있는 Hook이다. useReducer의 핵심은 한 컴포넌트 내에서 State를 업데이트하는 로직 부분을 그 컴포넌트로부터 분리시키는 것을 가능하게 해준다는 것이다. 그렇게 useReducer는 State 업데이트 로직을 분리하여 컴포넌트의 외부에 작성하는 것을 가능하게 함으로써, 코드의 최적화를 이루게 해준다.



## useCallback

useCallback()은 함수를 메모이제이션(memoization)하기 위해서 사용되는 hook 함수이다. 첫번째 인자로 넘어온 함수를, 두번째 인자로 넘어온 배열 내의 값이 변경될 때까지 저장해놓고 재사용할 수 있게 해준다. 예를 들어, 어떤 React 컴포넌트 함수 안에 함수가 선언이 되어 있다면 이 함수는 해당 컴포넌트가 랜더링될 때 마다 새로운 함수가 생성된다. 하지만 useCallback()을 사용하면, 해당 컴포넌트가 랜더링되더라도 그 함수가 의존하는 값들이 바뀌지 않는 한 기존 함수를 계속해서 반환한다. 즉, x 또는 y 값이 바뀌면 새로운 함수가 생성되어 add 변수에 할당되고, x와 y 값이 동일하다면 다음 랜더링 때 이 함수를 재사용한다.

```javascript
// const memoizedCallback = useCallback(함수, 배열);
const add = () => x + y; // useCallback을 사용하지 않을 시
const add = useCallback(() => x + y, [x, y]); // useCallback 사용 시
```





**참고**

{% embed url="https://hudi.blog/layered-architecture/" %}

{% embed url="https://velog.io/@andy0011/Flux-%ED%8C%A8%ED%84%B4%EC%9D%B4%EB%9E%80" %}

{% embed url="https://velog.io/@iamhayoung/React-Hooks-useReducer%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0" %}

{% embed url="https://www.daleseo.com/react-hooks-use-callback/" %}

# React

* [React 공식문서](https://ko.legacy.reactjs.org/)
* [React Dev문서](https://react.dev/)

#### 렌더링

```javascript
const root = createRoot(document.getElementById('root'));
```

똑같은 루트 컴포넌트에 여러번 렌더링하여도 변경이 되는 부분(상태)만 바뀌는 원리다.

#### 리렌더링

리액트의 모든 리렌더링은 상태 변경에서 시작된다. 컴포넌트가 리렌더링될 때 모든 하위 요소들도 다시 렌더링된다.

#### 리액트는 라이브러리인가 프레임워크인가? - 제어의 역전

[제어의 역전](https://martinfowler.com/bliki/InversionOfControl.html)(IoC: Inversion of Control)이 Framework의 주요한 특징이고, React는 IoC를 통해 상태와 업데이트가 얽힌 복잡한 상황을 간단히 선언형 UI로 구성하는 혜택을 누린다(이게 바로 React의 첫 번째 특징이다). 그 누구도 매번 root를 render하는 방식으로 쓰면서 “이게 라이브러리지!”라며 감탄하지 않는다.

하지만 일반적으로는 (Martin Fowler의 개탄처럼) IoC는 IoC 컨테이너와 엮여서 DI와 동의어처럼 쓰이고, Next.js, Remix 같은 걸 Framework이라고 부르니 면접 때 괜히 이런 걸로 싸우지는 말자. “리액트 개발자가 이렇게 이야기했다니까요!”라고 해봐야 서로 감정만 상할 뿐이다.

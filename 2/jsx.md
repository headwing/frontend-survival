# JSX

### JSX란?

```javascript
const element = <h1>Hello, world!</h1>;
```

위에 희한한 태그 문법은 문자열도, HTML도 아니다. JSX라 하며 JavaScript를 확장한 문법이며, JavaScript의 모든 기능이 포함되어 있다. UI의 편리한 렌더링을 위해 React와 함께 사용할 것이 권장된다.

&#x20;

리액트에서 JSX를 꼭 사용해야하는 것은 아니다. 근본적으로, JSX는 React.createElement(component, props, ...children) 함수에 대한 문법적 설탕(Syntactic sugar)을 제공할 뿐이다. 즉 JSX는 React “엘리먼트(element)” 를 생성한다.

&#x20;

예를 들어 다음의 JSX로 작성된 코드는

```javascript
class Hello extends React.Component {
  render() {
    return <div>Hello {this.props.toWhat}</div>;
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Hello toWhat="World" />);
```

아래처럼 JSX를 사용하지 않은 코드로 컴파일될 수 있다.

```javascript
class Hello extends React.Component {
  render() {
    return React.createElement('div', null, `Hello ${this.props.toWhat}`);
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(React.createElement(Hello, {toWhat: 'World'}, null));
```

&#x20;

### React Element란?

그렇다면 리액트 엘리먼트란 무엇일까? 엘리먼트는 React 앱의 가장 작은 단위이며, 화면에 표시할 내용을 기술한다. 엘리먼트는 컴포넌트의 "구성 요소"이다.

&#x20;

DOM에 엘리먼트를 렌더링하는 법을 알아보자. 아래와 같이 HTML 파일 어딘가에 \<div>가 있다고 가정해보자.

```javascript
<div id="root"></div>
```

이 안에 들어가는 모든 엘리먼트를 React DOM에서 관리하기 때문에 이것을 “루트(root)” DOM 노드라고 부른다. React로 구현된 애플리케이션은 일반적으로 하나의 루트 DOM 노드가 있다. React를 기존 앱에 통합하려는 경우 원하는 만큼 많은 수의 독립된 루트 DOM 노드가 있을 수 있다. React 엘리먼트를 렌더링 하기 위해서는 우선 DOM 엘리먼트를 ReactDOM.createRoot()에 전달한 다음, React 엘리먼트를 root.render()에 전달해야 한다.&#x20;

```javascript
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```

React DOM은 해당 엘리먼트와 그 자식 엘리먼트를 이전의 엘리먼트와 비교하고 DOM을 변경할 필요가 있을 때만 DOM을 업데이트한다.

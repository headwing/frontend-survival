# Routes

## 라우팅이란?&#x20;

간단하게 생각 하자면 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것이라고 생각할 수 있다. 리액트에서는 라우팅 관련 라이브러리가 많이 있는데, 이중 가장 많이 쓰이는 **리액트 라우터(React Router)**를 사용해보려 한다. 참고로 **라우터**의 의미는 네트워크 간의 경로를 설정하고 전환시키는 장치라고 한다.



## Browser Router

BrowserRouter는 HTML5의 History API(pushState, replaceState, popstate event)를 사용하여 URL과 UI를 동기해주는 \<Router>이다.

이는 페이지를 새로고침하지 않고도 주소를 변경할 수 있도록 해주고, 현재 주소에 관련된 정보를 `props`로 조회 및 사용이 가능하도록 한다.

BrowserRouter는 리액트 라우터 돔을 적용하고 싶은 컴포넌트의 최상위 컴포넌트를 감싸주는 래퍼 컴포넌트이기 때문에, App 컴포넌트를 감싸주면 된다.



## Route

Route는 path에 따라 해당 UI를 보여주는 라우팅 기능을 가진 컴포넌트 로, path=""부분에 URL 경로를 적고, 렌더링될 컴포넌트를 자식요소로 넣어주면 된다.



## Memory Router

테스트 시에는 브라우저에서 돌아가지 않아 Browser Router를 사용하지 않는다. 그러므로 실제로 주소가 존재하지는 않는 라우터인 MemoryRouter를 사용한다. 외부의 브라우저 URL에 따라 달라지는 것이 아니라 내부적으로 작동한다. 리액트 네이티브나, 임베디드 웹앱에서도 사용된다. initialEntries에다가 path를 추가해줘야한다.



{% embed url="https://velog.io/@wiostz98kr/TIL49-l-React-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EB%9D%BC%EC%9A%B0%ED%84%B0React-Router-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-Feat.-SPA" %}

{% embed url="https://reactrouter.com/en/main/router-components/memory-router" %}

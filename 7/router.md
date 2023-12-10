# Router

## React Router

리액트 애플리케이션에서 탐색 및 라우팅을 처리하기 위한 라이브러리이다. URL을 기반으로 애플리케이션의 다양한 컴포넌트가 렌더링되는 방식을 정의할 수 있다. 전체 페이지를 새로고침 하지 않고도 페이지 콘텐츠가 동적으로 변경되는 단일 페이지 애플리케이션(SPA)를 만들 수 있다.



## Router

React Router 버전 6.4부터 지원하는, 라우터 객체를 만들어서 쓰는 방법이다. 라우팅 정보만 별도의 파일로 관리할 수 있다.

* **기존 방식**

```javascript
import { BrowserRouter } from 'react-router-dom'

const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <BrowserRouter> // 최상단 root에서 BrowserRouter로 감싸기
      <App /> 
  </BrowserRouter>
)
```

```javascript
import { Route, Routes } from 'react-router-dom'

const App = () => {
  return (
    <Routes>
      <Route path='/' element={<Layout />} > // outlet을 이용한 중첩라우팅
        <Route index element={<Main />} /> 
        <Route path='/pageA' element={<PageA />} />
        <Route path='/pageB' element={<PageB />} />
        <Route path='/pageC' element={<PageC />} />
      </Route>
      </Routes>
  )
}
```

* **라우터 객체를 만들어서 쓰는 방법**

```javascript
import { Outlet } from 'react-router-dom';

function Layout() {
	return (
		<div>
			<Header />
			<Outlet />
			<Footer />
		</div>
	);
}

const routes = [
	{
		element: <Layout />,
		children: [
			{ path: '/', element: <HomePage /> },
			{ path: '/about', element: <AboutPage /> },
		],
	},
];

export default routes;
```

```javascript
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import routes from './routes';

const router = createBrowserRouter(routes);

root.render((
	<React.StrictMode>
		<RouterProvider router={router} />
	</React.StrictMode>
));
```



## createBrowserRouter

This is the recommended router for all React Router web projects. It uses the [DOM History API](https://developer.mozilla.org/en-US/docs/Web/API/History) to update the URL and manage the history stack.



## RouterProvider

All [data router](https://reactrouter.com/en/main/routers/picking-a-router) objects are passed to this component to render your app and enable the rest of the data APIs.



## createMemoryRouter

Instead of using the browser's history, a memory router manages its own history stack in memory. It's primarily useful for testing and component development tools like Storybook, but can also be used for running React Router in any non-browser environment.&#x20;

* 메모리 라우터 만들어서 테스트

```javascript
describe('routes', () => {	
	function renderRouter(path: string) {
		const router = createMemoryRouter(routes, { initialEntries: [path] });
		render(<RouterProvider router={router} />);
	}
	
	context('when the current path is “/”', () => {
		it('renders the home page', () => {
			renderRouter('/');
	
			screen.getByText(/Hello/);
		});
	});
	
	context('when the current path is “/about”', () => {
		it('renders the about page', () => {
			renderRouter('/about');
	
			screen.getByText(/About/);
		});
	});
});
```



{% embed url="https://reactrouter.com/en/main/routers/create-browser-router#createbrowserrouter" %}

{% embed url="https://reactrouter.com/en/main/routers/create-memory-router" %}

{% embed url="https://reactrouter.com/en/main/routers/router-provider" %}

# Routing

일반적인 웹 사이트는 URL에 따라 다른 웹 페이지를 보여준다. 하나의 웹 페이지를 하나의 컴포넌트로 만들고, URL에 따라 적절한 컴포넌트가 보이게 함으로써 구현 가능하다.

{% code fullWidth="false" %}
```javascript
function App() {
	const { pathname } = window.location;
	
	return (
		<div>
			<Header />
			<main>
				{pathname === '/' && <HomePage />}
				{pathname === '/about' && <AboutPage />}
			</main>
			<Footer />
		</div>
	);
}
```
{% endcode %}



## HTML DOM API

흔히 우리가 HTML에서 제어하는 div, span, input 등의 요소들을 Document Object Model(DOM)이라고 한다. 프로그램을 사용하기 위한 명령들의 집합을 Application Programming Interface(API)라고 한다. 즉, DOM API는 HTML의 요소들을 JS에서 제어하기 위한 명령들의 집합을 의미한다.



## Location

[Location](https://developer.mozilla.org/ko/docs/Web/API/Location) 인터페이스는 객체가 연결된 장소(URL)을 표현한다. Location 인터페이스에 변경을 가하면 연결된 객체에도 반영이 되는데 Document와 Window인터페이스가 이런 Location을 갖고 있다.



## pathname

Location인터페이스의 pathName 속성은 URL의 경로와 그 앞에 /로 이루어진 문자열을 반환한다. 경로가 없는 경우에는 빈 문자열을 반환한다.


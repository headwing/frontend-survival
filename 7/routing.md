# Routing

일반적인 웹 사이트는 URL에 따라 다른 웹 페이지를 보여준다. 하나의 웹 페이지를 하나의 컴포넌트로 만들고, URL에 따라 적절한 컴포넌트가 보이게 함으로써 구현 가능하다.&#x20;

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

Location은 객체가 연결된 장소(URL)를 표현한다. 속성 중 pathname은(Location.pathname) '/' 문자 뒤 URL의 경로를 값으로 하는 문자열이다.

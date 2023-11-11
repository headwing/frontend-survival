# Fetch API & CORS

#### Fetch API 란

`fetch()` 함수는 첫번째 인자로 URL, 두번째 인자로 옵션 객체를 받고, Promise 타입의 객체를 반환합니다. 반환된 객체는, API 호출이 성공했을 경우에는 응답(response) 객체를 resolve하고, 실패했을 경우에는 예외(error) 객체를 reject합니다.

<pre class="language-javascript"><code class="lang-javascript"><strong>// JSON을 기본 지원한다.
</strong><strong>const response = await fetch('http://localhost:3000/products');
</strong>const data = await response.json();

// 다른 HTTP Method를 쓰고 싶다면?
const response = fetch(url, {
    method: 'POST',
});
</code></pre>

#### Promise

끔찍한 Callback에서 벗어나 Promise 적용하기

{% embed url="https://spicycookie.me/JavaScript/promise/" %}

{% embed url="https://velog.io/@ljinsk3/JavaScript-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%B2%98%EB%A6%AC-Promise-%EA%B0%9D%EC%B2%B4" %}

`Promise`는 자바스크립트에서 제공하는 비동기를 간편하게 처리할 수 있게 도와주는 객체이다. Promise 이전에 비동기 처리로 콜백 패턴을 주로 사용했었다. 그러나 `콜백 지옥(Callback Hell)`으로 인해 가독성도 나쁘고, 비동기 처리 중에 발생한 에러의 처리가 까다로웠다. Promise는 이러한 단점을 보완하기 위해 나온 대안이라고 봐도 무방하다.

#### ReableStream

`ReadableStream` 인터페이스는 바이트 데이터를 읽을수 있는 스트림을 제공합니다. [Fetch API](https://developer.mozilla.org/ko/docs/Web/API/Fetch\_API)는 Response 객체의 body 속성을 통하여 `ReadableStream`의 구체적인 인스턴스를 제공합니다.

#### Unicode

유니코드는 전 세계의 문자를 일관되게 표현할 수 있도록 설계된 표준이다. 유니코드는 1바이트가 아닌 2바이트, 즉 16비트로 문자를 표현한다. 따라서 2^16=65536 개의 문자를 표현할 수 있다. 

#### CORS 란

웹 브라우저는 Same Origin Policy에 따라 웹 페이지와 리소스를 요청한 곳(여기서는 REST API 서버)이 서로 다른 출처(포트까지 포함)일 때 서버에서 얻은 결과를 사용할 수 없게 막는다. 서버에 요청하고 응답을 받아오는 것까지는 이미 진행이 다 된 상황이란 점에 주의!

REST API 서버에서 Headers에 “Access-Control-Allow-Origin” 속성을 추가하면 된다.

Express에선 그냥 [CORS 미들웨어](https://expressjs.com/en/resources/middleware/cors.html)를 설치해서 사용하면 됨.

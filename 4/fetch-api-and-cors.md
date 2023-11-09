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

#### ReableStream

#### Unicode

#### CORS 란

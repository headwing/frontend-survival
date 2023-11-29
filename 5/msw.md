# MSW

## Service worker

서비스 워커는 웹 프로그램 및 브라우저와 네트워크 사이의 프록시 서버 역할을 한다. 서비스 개발 워커의 핵심 개발 의도는 네트워크 요청을 가로채서 수정하여 효과적인 오프라인 경험을 생성하는데 있다.&#x20;



## MSW(Mock Service Worker)

MSW는 오프라인 작업 등을 지원하기 위한 서비스 워커의 기능을 유용히 활용한 것으로 코드 레벨이 아닌 네트워크 레벨에서 가짜를 구현할 수 있게 한다. handlers를 통해 가짜 응답을 네트워크 상에서 받을 수 있게 한다. 테스트 환경(Node.js 기반) 외에 웹 브라우저도 지원하기 때문에, API 스펙은 나왔지만 아직 구현되지 않은 경우 임시로 사용할 수도 있다. 단순히 임시 서버를 만들 거라면 Express를 쓰는 게 더 낫지만, 테스트 코드도 지원하면서 겸사겸사 웹 브라우저를 지원하는 용도로는 나쁘지 않은 선택이다.



## window.fetch polyfill

최신 Node.js에서는 fetch를 지원하지만, 기존의 Node.js에서는 fetch가 지원되지 않았다. fetch는 window에 있는 것으로 Node.js에서는 window가 없기 때문이다. 그러므로 whatwg-fetch를 설치 후 import하여 Node.js에서도 fetch를 사용해보자.

```
npm install whatwg-fetch --save
```

```javascript
import 'whatwg-fetch'

window.fetch(...)
```

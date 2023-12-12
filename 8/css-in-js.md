# CSS in JS

## CSS in JS란

자바스크립트를 이용해서 styled components를 만들어서 사용하는 것을 말한다.

```javascript
// Create a component that renders a <p> element with blue text
import styled from 'styled-components';

const BlueText = styled.p`
  color: blue;
`;

<BlueText>My blue text</BlueText>
```

[CSS-in-JS에 관해 알아야 할 모든 것](https://d0gf00t.tistory.com/22)

1. Thinking in components
2. CSS-in-JS **leverages the full power of the JavaScript ecosystem** to enhance CSS.
3. True rules isolation
4. Scoped selectors
5. Vendor Prefixing
6. Code sharing
7. **Only the styles which are currently** in use on your screen are also in the DOM (react-jss).
8. Dead code elimination
9. Unit tests for CSS

{% embed url="https://d0gf00t.tistory.com/22" %}



### CSS

css 파일과 js 파일 로딩의 차이가 있기 때문에 성능 이슈가 있다. css를 js 안에 작성하면 컴포넌트 파일을 하나로 유지하면서 기능과 스타일을 같이 관리할 수 있다는 장점이 있다.

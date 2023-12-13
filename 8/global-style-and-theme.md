# Global Style & Theme

## Reset CSS

```javascript
import { Reset } from 'styled-reset';

import GlobalStyle from './styles/GlobalStyle';

export default function App() {
	return (
		<>
			<Reset />
			<GlobalStyle />
			<Greeting />
		</>
	);
}
```



## Global Style

```javascript
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
	html {
		box-sizing: border-box;
	}
	
	*,
	*::before,
	*::after {
		box-sizing: inherit;
	}
	
	html {
		font-size: 62.5%;
	}
	
	body {
		font-size: 1.6rem;
	}
	
	:lang(ko) {
		h1, h2, h3 {
			word-break: keep-all;
		}
	}
`;

export default GlobalStyle;
```



## box-sizing 속성

이 속성은 box의 크기를 어떤 것을 기준으로 계산할 지 정하는 속성이다. 기본 값은 content-box이며, 자주 사용하는 속성은 border-box이다. box-sizing의 기본값을 border-box로 설정함으로써 width와 height의 값을 콘텐츠를 기준으로 하지 않고, 테두리를 기준으로 하도록 한다.

* content-box : 콘텐트 영역을 기준으로 크기를 정한다.
* border-box : 테두리를 기준으로 크기를 정한다.
* initial : 기본값으로 설정한다.
* inherit : 부모 요소의 속성값을 상속받는다.



## word-break 속성

텍스트가 컨텐츠 상자를 넘칠 경우에 줄 바꿈을 표시할지 여부를 설정한다. 한국어의 경우 단어를 나누면 안되므로 기본값을 keep-all로 바꿔서 설정하였다.

* normal : CJK 문자는 글자 기준으로, CJK 이외의 문자는 단어 기준으로 줄바꿈합니다.
* break-all : 글자 기준으로 줄바꿈합니다.
* keep-all : 단어 기준으로 줄바꿈합니다. 중국어/일본어/한국어(CJK) 텍스트에는 줄바꿈 할 때 단어를 유지하며 적용됩니다. CJK가 아닌 텍스트 동작은 normal과 동일합니다.
* break-word : "overflow-wrap: break-word" 속성과 동일하기 때문에 현재는 사용하지 않습니다.



## Theme

다크모드나 색상 관련해서 코드를 작성할 때 편리해진다.

기본 Theme부터 정의하고,

```javascript
const defaultTheme = {
  colors: {
    background: 'linear-gradient(134deg, #F89E21 0.7%, #FF6400 65.66%)',
    text: '#FFF',
    primary: '#FF8400',
    primaryOp: '#FFF1DC',
    secondary: '#442728',
    menuBg: '#fff',
    gray: '#F4F4F4',
    activeBtn: '#D87000',
    activeCancelBtn: '#170A0C',
  },
};

export default defaultTheme;
```

darkMode도 사용할 예정이라서 darkTheme도 정의해줬다.

```javascript
import Theme from './Theme';

const darkTheme : Theme = {
  colors: {
    background: '#1E1E1E',
    text: '#FFF',
    primary: '#FF8400',
    primaryOp: '#3A3A3A',
    secondary: '#442728',
    menuBg: '#3A3A3A',
    gray: '#1E1E1E',
    activeBtn: '#D87000',
    activeCancelBtn: '#170A0C',
  },
};

export default darkTheme;
```

타입 문제를 해결하기 위해 styled.d.ts 파일을 작성했다.

```javascript
import 'styled-components';
import Theme from './Theme';

declare module 'styled-components' {
	export interface DefaultTheme extends Theme {}
}
```

마지막으로 GlobalStyle.ts 파일을 작성하면 끝이다.

```javascript
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
  body {
    background: ${(props) => props.theme.colors.background};
    color: ${(props) => props.theme.colors.text};
  }

  a {
    color: ${(props) => props.theme.colors.text};
  }

  button,
  input,
  select,
  textarea {
   background: ${(props) => props.theme.colors.background};
   color: ${(props) => props.theme.colors.text};
  }
`;

export default GlobalStyle;
```



## ThemeProvider

생성한 theme을 기준으로 컴포넌트에 변화를 주고 싶다면 최상위 컴포넌트에서 ThemeProvider로 감싸줘야한다.

```javascript
// App.tsx
import { ThemeProvider } from 'styled-components';
import defaultTheme from './styles/defaultTheme';

export default function App() {
  const { isDarkMode } = useDarkMode();
  const theme = isDarkMode ? darkTheme : defaultTheme;

  return (
     <ThemeProvider theme={theme}>
      <Reset />
      ...
     </ThemeProvider>
  )
}
```

이렇게 사용하면 된다.

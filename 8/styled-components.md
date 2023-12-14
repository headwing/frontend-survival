# styled-components

## styled-componets

아래와 같이 Styled Component를 만들 수 있고, 기존의  Styled Component에 추가로 스타일을 입히는 것도 가능하다.

```javascript
import styled from 'styled-components';

const Paragraph = styled.p`
	color: #00F;
`;

const BigParagraph = styled(Paragraph)`
	font-size: 5rem;
`;

export default function Greeting() {
	return (
		<BigParagraph>
			Hello, world!
		</BigParagraph>
	);
}
```

기존 컴포넌트에 스타일을 입히는 것도 가능. 단, 기존 컴포넌트가 className 잡아줘야 한다는 점에 주의하자.

```javascript
import styled from 'styled-components';

function HelloWorld({ className }: React.HTMLAttributes<HTMLElement>) {
	return (
		<p className={className}>
			Hello, world!
		</p>
	);
}

const Greeting = styled(HelloWorld)`
	color: #00F;
`;

export default Greeting;
```

# React Testing Library

리액트 테스팅 라이브러리는 리액트 컴포넌트를 사용자 입장에 가깝게 테스트할 수 있는 도구이다. 예를 들어 \<div>Hello World\</div>라는 코드가 있다면, div 태그를 사용하는지보다 Hello World 메시지가 브라우저에 노출이 되는지 파악하는 것을 더 중요하다고 본다. 또한 컴포넌트를 사용하는 테스트 코드를 작성하면서 해당 컴포넌트의 인터페이스를 개발 전에 미리 점검하여 문제를 발견 및 수정할 수 있다는 장점이 있다. 그러므로 최대한 개발 전 혹은 바로 직후에 테스트 코드를 작성하는 것이 권고된다.

&#x20;

[초심자를 위한 React Testing Library](https://tecoble.techcourse.co.kr/post/2021-10-22-react-testing-library/)

&#x20;

여기서도 마찬가지로 BDD 스타일로 코드를 작성하는 것이 유리하다. 다만 보다 구체화를 해보자면, given-when-then 패턴을 찾을 수 있다. 예를 들어 아래 코드의 경우, 컴포넌트가 render된다는 조건이 주어질 시(given), input에 'New name'을 입력했을 때(When), setText 함수가 'New name'이라는 값과 함께 호출된다(Then)고 구조를 나눠볼 수 있다. 만약 복잡한 로직이 컴포넌트로부터 분리된다면, 여기서는 다음의 코드와 같이 호출이 되었는지만 검증하면 된다.

&#x20;

여기서 render 함수와 같이 반복되는 코드들을 바깥으로 빼서 함수로 만들어(Extract Function) 해당 함수를 호출하는 식으로 간단히 작성할 수 있다. 또한 given에 대한 부분이 거슬린다면, it 바깥으로 뺀 뒤 beforeEach()에 넣어주는 방법도 있다.

```
import { render, screen, fireEvent } from '@testing-library/react';

import TextField from './TextField';

const context = describe;

describe('TextField', () => {
	const text = 'Tester';
	const setText = jest.fn();
	
	beforeEach(() => {
		setText.mockClear();
		// 또는 jest.clearAllMocks();	
	});
	
	function renderTextField() {
		render((
			<TextField
				label="Name"
				placeholder="Input your name"
				text={text}
				setText={setText}
			/>
		));
	}
	
	it('renders an input control', () => {
    		// when
		renderTextField();

		// then
		screen.getByLabelText('Name');
	});
	
	context('when user types text', () => {	
		it('calls the change handler', () => {
        
        		// given
			renderTextField();

			// when
			fireEvent.change(screen.getByLabelText('Name'), {
				target: {
					value: 'New Name',
				},
			});
	
    			// then
			expect(setText).toBeCalledWith('New Name');
		});
	});
});
```

&#x20;

API 호출과 같이 외부 의존성이 큰 코드를 작성해야 한다면, 해당 부분만 가짜로 구현할 필요가 있을 때가 있다. 예를 들어 매번 서버를 키기 어렵거나, 실제로 post 요청을 해버려서 서비스단이 바뀐다거나 하는 등의 문제가 발생할 수 있기 때문이다. 이런 경우에는 Mocking을 활용하여 아래와 같이 불러오는 데이터의 가짜를 만들 수 있다. 또한 가짜 데이터들이 많이 필요한 경우, 따로 흩어져있는 데이터들을 fixture라는 파일에 한꺼번에 불러와 테스트 시 간편하게 fixture 파일 하나에서 불러와서 작업을 할 수 있다.

```
import { render, screen } from '@testing-library/react';

import App from './App';

jest.mock('./hooks/useFetchProducts', () => () => [
	{
		category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
	},
]);

test('App', () => {
	render(<App />);

	screen.getByText('Apple');
});
```

&#x20;

일반적으론 백엔드와 소통하는 부분이 차지하는 비중이 큰데, 이 부분을 하나씩 가짜 구현으로 바꾸다 보면 어려울 때가 있다. 이럴 땐 MSW 등 다른 대안을 고려해 보자.

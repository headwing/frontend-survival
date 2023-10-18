# Testing Library

#### Jest

거의 모든 것을 갖춘 테스팅 도구이다. Mocha와 Chai처럼 RSpec의 describe-it을 지원하고, expect로 단언(assertion)할 수 있다. Mocking도 다양한 레벨에서 쉽게 사용할 수 있다.

```javascript
//  main.test.ts
test('Test의 설명' , () => {
  expect(1 + 2).toBe(3)
})
```

```javascript
// package.json
"watch:test" : "jest --watchAll"
```

#### Describe-Context-It 패턴

```javascript
describe('add 함수', () => {
  it('returns sum of two numbers' , () => {
    expect(add(1,2).toBe(3));
  })
})
```

***

#### React Testing Library

React UI테스트에 특화된 라이브러리이다. F/E 테스트시, React 컴포넌트 테스트만 테스트 하는 상황은 최대한 피하는게 좋다.

```javascript
screen.getByText('Hello');
screen.getByText(/Hello/);

expect(screen.queryByText(/Hi/)).toBeInTheDocument();
expect(screen.queryByText(/Hi/)).not.toBeInTheDocument();
```

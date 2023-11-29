# TDD

## TDD(Test Driven Development) 란?

테스트 코드를 먼저 작성하는, 즉 구현보다 인터페이스와 스펙을 먼저 정의함으로써 개발을 진행하는 방식이다.

&#x20;

<figure><img src="https://blog.kakaocdn.net/dn/cb2hmO/btsA9O31mlc/9JhAYZo0BCgfCkxu6cXCIK/img.png" alt="" height="346" width="521"><figcaption></figcaption></figure>

**TDD Cycle**

1. Red → 실패하는 테스트 코드를 작성. 인터페이스와 스펙에 집중한다.
2. Green → 재빨리 테스트를 통과시킨다. 올바른 방법이 아니어도 괜찮다.
3. Refactor → 리팩터링을 통해 코드를 올바르게 만든다. TDD에서 가장 중요한 부분이지만, 간과될 때가 많다.

중요한 것은 실패하는 테스트 코드를 작성할 때까지 실제 코드를 작성하지 않는 것과, 실패하는 테스트를 통과할 정도의 최소 실제 코드를 작성해야하는 것이다. 이를 통해 실제 코드에 대해 기대되는 바를 보다 명확하게 정의 함으로써 불필요한 설계를 피할 수 있고, 정확한 요구 사항에 집중할 수 있다. 작은 단계를 찾고, 코드에서 피드백을 얻는 게 중요하다. 2번이 어렵다면 1번으로 돌아가서 더 작고 쉬운 문제를 정의하고, 3번을 위해 의도를 드러내고 중복을 찾아 제거하는 연습을 해야 한다.

&#x20;

**단위테스트란?**

말 그대로 한 단위(일반적으로 class)만을 테스트하는 것으로 구현에 대한 테스트를 의미한다. TDD는 자동화된 단위 테스트 코드를 먼저 작성함으로써 테스트가 개발을 이끌어나가도록 하는 방식이다. TDD는 인터페이스와 예제, 기대하는 결과를 먼저 작성하는 걸로 시작한다. 단위 테스트 코드를 작성한다는 건 이미 설계가 어느 정도 된 상태, 즉 인터페이스와 예제가 만나는 지점을 묘사할 수 있는 상태를 전제로 하게 된다.

&#x20;

## Jest

Jest는 페이스북에서 만들어서 React와 더불어 많은 자바스크립트 개발자들이 사용하고 있는 테스팅 라이브러리이다. Jest를 이용하여 테스트 케이스를 정의할 때 크게 두가지 방법을 사용한다.

&#x20;

**1. test 함수로 개별 테스트를 나열하는 방식.**

```
test('add', () => {
	expect(add(1, 2)).toBe(3);
});
```

&#x20;

**2. BDD 스타일(Describe - Context - It 패턴)로 주체-행위 중심으로 테스트를 조직화하는 방식.**

describe로 주체를 명시하고, it으로 행위를 명시한다. 여러 행위를 테스트한다면 context를 사용하여 행위에 대한 조건 등을 명시할 수 있다.

```
describe('add', () => {
	it('returns sum of two numbers', () => {
		expect(add(1, 2)).toBe(3);
	});
});
```

```
const context = describe;

describe('add', () => {
	context('with no argument', () => {
		it('returns zero', () => {
			expect(add()).toBe(0);
		});
	});

	context('with only one number', () => {
		it('returns the same number', () => {
			expect(add(1)).toBe(1);
		});
	});

	context('with two numbers', () => {
		it('returns sum of two numbers', () => {
			expect(add(1, 2)).toBe(3);
		});
	});

	context('with three numbers', () => {
		it('returns sum of three numbers', () => {
			expect(add(1, 2, 3)).toBe(6);
		});
	});
});
```

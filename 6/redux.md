# Redux 따라하기

## Redux

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

리덕스는 여러 컴포넌트가 공유하는 상태를 관리하기 위한 라이브러리로 메타가 설계한 flux 규격에 맞추어져 있다. 리액트와 사용하기 위해서는 React Tool Kit을 함께 설치해야 한다.

대략적인 사용 예시는 이렇다.

```Javascript
const dispatch = useDispatch();
const count = useSelector((state) => state.count);

dispatch({ type: 'increase' });
dispatch({ type: 'decrease' });

dispatch({ type: 'increase', payload: 10 });
```



## Reflect

Reflect는 중간에서 가로챌 수 있는 Javascript 작업에 대한 메서드를 제공하는 내장 객체이다. 다른 대부분의 전역 객체와 다르게, Reflect는 생성자가 아니다. 따라서 함수처럼 호출하거나 new 연산자로 인스턴스를 만들 수 없다. Math 객체처럼, Reflect의 모든 속성과 메서드는 정적이다. Reflect 객체의 정적 메서드 이름은 프록시 처리기 메서드의 이름과 같다. Reflect.get()함수는 대상의 속성을 반환하는 함수이다. 이 외에도 다양한 함수들이 내장되어 있어서 유용하게 사용될 것 같다.

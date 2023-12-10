# Navigation

## Web APIs - History

history 전역 객체를 통해 브라우저 세션 히스토리에 대한 접근을 제공한다. 사용자의 방문 기록을 앞뒤로 탐색하고, 방문 기록 스택의 내용을 조작할 수 있는 유용한 메서드와 속성을 노출한다. Window.history 읽기 전용 속성은 History 객체로의 참조를 반환한다. History 객체는 브라우저의 세션 기록(현재 페이지를 불러온 탭 혹은 프레임이 방문했던 페이지)을 조작할 때 사용한다.



사용자의 방문 기록을 앞뒤로 이동하는 것은 back(), forward() 그리고 go() 메서드를 사용하여 수행한다.

```javascript
history.back(); // 사용자가 브라우저 도구 모음에서 '뒤로 가기' 버튼을 클릭한 것과 동일
history.forward(); // '앞으로 가기' 버튼을 클릭한 것처럼 앞으로 이동 가능
```

방문 기록의 특정 지점으로 이동할 수도 있는데, 세션 기록에서 현재 페이지에 대한 상대 위치로 식별되는 특정 페이지를 로드할 수 있다. (현재 페이지의 상대 위치는 0)

```tsx
history.go(-1); // history.back();
history.go(1); // history.forward();
```

go() 메서드의 또 다른 용도는 0을 전달하거나 인수 없이 호출하여 현재 페이지를 새로고침하는 것이다.

```tsx
// 아래 두 줄의 코드는 모두 페이지를 새로고침 합니다.
history.go(0);
history.go();
```



### Navigation

SPA 어플리케이션에서는 html을 하나만 사용하기 때문에, 링크를 클릭하면 URL의 주소만 바뀌고 실제로 서버에 html파일을 요청할 필요가 없다. 따라서 a 태그를 이용하여 다시 요청되는 네비게이션 방식이 아닌 History 객체의 pushState를 이용한다. 다만 URL주소만 바꿔줄 뿐 해당 컴포넌트를 렌더링하지는 않는다.

```ts
const state = {};
const title = '';
const url = '/about';

history.pushState(state, title, url);
```

React Router에서는 이와 같이 URL을 바꿔주는 것과 더불어 URL에 맞는 컴포넌트를 렌더링해주는 기능을 추상화해놓은 Link 컴포넌트가 있다.

```ts
function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

Link 컴포넌트외에 NavLink 컴포넌트도 존재하는데 NavLink 컴포넌트를 사용하면 현재 위치한 페이지의 Link 태그에 active라는 class가 붙는다. 이를 통해 GNB, LNB등에서 스타일 처리를 해줄때 유용하다.

```ts
function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <NavLink to="/">Home</NavLink>
          </li>
          <li>
            <NavLink to="/about">About</NavLink>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

Navigate 라는 컴포넌트도 있는데 redirect를 시켜준다. LogoutPage에 가면, 바로 `'/'` 경로로 redirect 된다.

```ts
import { Navigate } from 'react-router-dom';

export default function LogoutPage() {
  return <Navigate to="/" />;
}
```

Navigate 컴포넌트를 사용하는 LogoutPage를 테스트하려고 하면 "ReferenceError: Request is not defined" 라는 에러와 함께 테스트가 죽을때가 있는데 이때는 whatwg-fetch를 setupTest.ts 파일에서 import 해주면 된다. 또한 useNavigate 라는 Hook으로 특정 상황에 navigate시켜줄 수 있다.

```ts
import { useNavigate } from 'react-router-dom';

export default function Footer() {
  const navigate = useNavigate();

  const handleClick = () => {
    navigate('/about');
  };

  return (
    <footer>
      <button type="button" onClick={handleClick}>
        Press
      </button>
    </footer>
  );
}
```

# Style Basics

## className

className은 특정 엘리먼트의 클래스 속성의 값을 가져오거나 설정할 수 있다. 리액트에서는 class를 사용하지 않고 JSX문법으로 className을 사용한다. css는 컴포넌트를 전제로 하고 있지 않는다. 공통된 부분이 많을 때 재사용하기 쉽다. 따라서, 컴포넌트 중심으로 빠르게 작업하려고 하면 불편할 때가 많다. 재사용은 그냥 컴포넌트를 사용하면 된다. 절충안으로 아주 작은 스타일 그룹을 클래스로 지정하는 방법도 있긴 하다(Bootstrap, Tailwind CSS 등의 접근법).



## Inline Style

“style” 속성 활용. 평범한 JavaScript 객체를 활용하므로 변수, 함수 등을 재사용하기 쉽다. 텍스트가 아니라서 실수하거나 불편할 때가 있다. TypeScript의 힘으로 자동완성, 타입 검사 등의 도움을 받을 수 있다.

```javascript
const darkMode = false;

function primaryColor (){
  return darkMode ? '#F00' : '#00F';
}

export default function Greeting(){
  return (
    <p style={{color: primaryColor()}}>
      hello~
    </p>
  )
}

// 또는 이렇게도 사용 가능
export default function Greeting(){
  const style = {
    color: 'blue'
  }

  return (
    <p style={style}>
      hello~
    </p>
  )
}
```



## 의미있는 마크업

의미론적 [마크업](https://developer.mozilla.org/ko/docs/Glossary/Markup)은 W3C의 권고사항이며, 이에 따라 HTML5에서는 의미론적 마크업을 위한 다양한 태그들이 새롭게 생겨났다.

이런 부분들을 잘 맞춰서 코드를 작성해야한다.

* 헤더/푸터에 `<header>`와 `<footer>` 사용
* 메인 컨텐츠에 `<main>`과 `<section>`사용
* 독립적인 컨텐츠에 `<article>` 사용
* 최상위 제목으로 `<h1>` 사용
* 순서가 없는 목록으로 `<ul>`과 `<li>` 사용
* 내비게이션에 `<nav>`사용

마크업을 잘 작성하면 검색 엔진이 시맨틱 태그를 중요한 키워드로 간주하기 때문에 검색엔진 최적화(SEO)에 유리하다. 웹 접근성 측면에서, 시각장애가 있는 사용자로 하여금 그 의미를 훨씬 잘 파악할 수 있다. 코드를 볼 때 가독성이 좋다.

{% embed url="https://developer.mozilla.org/ko/docs/Web/HTML/Reference" %}

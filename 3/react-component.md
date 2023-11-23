# React Component

### JSON

JSON(JavaScript Object Notation)은 키-값 쌍으로 이루어진 데이터 오브젝트를 전달하기 위해 인간이 읽을 수 있는 텍스트를 사용하는 개방형 표준 포맷이다. 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용한다(서버에서 클라이언트로 데이터를 전송하여 표현하려거나 반대의 경우). 백엔드에서 보통 REST API 또는 GraphQL을 활용하여 JSON 형태의 데이터를 돌려주는 API를 제공한다.

&#x20;

### REST API 와 GraphQL

REST API는 HTTP 메서드를 사용하여 작업을 수행하는 API를 구축하기 위한 아키텍처 스타일인 반면, GraphQL은 클라이언트 사이드에서 필요한 데이터만 요청할 수 있는 API를 위한 쿼리 언어이다.&#x20;

&#x20;

**REST API란 무엇인가?**

REST는 Representational State Transfer라는 용어의 약자로서 2000년도에 로이 필딩 (Roy Fielding)의 박사학위 논문에서 최초로 소개되었다. 로이 필딩은 웹(HTTP) 설계의 장점을 최대한 활용할 수 있는 아키텍처로써 REST를 발표했다고 한다. REST API의 구성은 크게 다음과 같이 구성되어 있다.

* 자원(RESOURCE) - URI
* 행위(Verb) - HTTP METHOD
* 표현(Representations)

&#x20;

REST API의 중심 규칙은 다음과 같다.

* URI는 자원을 표현해야 한다.
* 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현한다.

&#x20;

예시) 기본 리소스 URL: /products

1. Read (Collection) → GET /products ⇒ 상품 목록 확인
2. Read (Item) → GET /products/{id} ⇒ 특정 상품 정보 확인
3. Create (Collection Pattern 활용) → POST /products ⇒ 상품 추가 (JSON 정보 함께 전달)
4. Update (Item) → PUT 또는 PATCH /products/{id} ⇒ 특정 상품 정보 변경 (JSON 정보 함께 전달)
5. Delete (Item) → DELETE /products/{id} ⇒ 특정 상품 삭제

&#x20;

**REST API의 특징**

* 클라이언트 / 서버 구조
* 무상태성 (Stateless)
* 캐시 처리 가능 (Cacheable)
* 자체 표현 구조 (Self - descriptiveness)
* 계층화 (Layered System)
* 유니폼 인터페이스 (Uniform)

&#x20;

[NHN참고](https://meetup.nhncloud.com/posts/92)

[RESTful API 이란](https://velog.io/@somday/RESTful-API-%EC%9D%B4%EB%9E%80)

&#x20;

&#x20;

**GraphQL은 왜 등장했는가?**

GraphQL은 떠오르는 소셜 미디어 플랫폼의 속도 요구 사항에 대응하여 2012년에 등장했다. 개발자들은 REST와 같은 기존 API 아키텍처가 너무 길고 정형화되어 있어서 뉴스 피드를 효율적으로 생성할 수 없다고 생각했고 구체적으로 다음과 같은 문제들에 직면했다.

&#x20;

* **고정 구조 데이터 교환**\
  REST API는 클라이언트 요청이 고정된 구조를 따라야 리소스를 수신할 수 있다. 이 엄격한 구조는 사용하기 쉽지만 필요한 데이터를 정확히 교환하기에 항상 가장 효율적인 수단인 것은 아니다.
* **오버페칭 및 언더페칭**\
  REST API는 항상 전체 데이터 세트를 반환한다. 예를 들어 REST API의 person 객체로부터는 그 사람의 이름, 생년월일, 주소 및 전화번호를 받게 된다. 전화번호만 있으면 이 모든 데이터를 얻을 수 있다.\
  \
  마찬가지로, 개인의 전화번호와 마지막 구매 내역을 알려면 여러 개의 REST API 요청이 필요하게 된다. /person이라는 URL은 전화번호를 반환하고 /purchase라는 URL은 구매 내역을 반환한다.\
  \
  소셜 미디어 개발자는 API 요청을 처리하기 위해 많은 양의 코드를 작성해야 했고, 이는 성능과 사용자 경험에 영향을 미쳤습니다. 이에 대해 GraphQL이 쿼리 기반 솔루션으로 부상할 수 있었다. 쿼리는 한 번의 API 요청 및 응답 교환에서만 정확한 데이터를 반환할 수 있기 때문이다.\
  \
  \* 오버페칭(Overfetching) : 오버페칭은 클라이언트가 필요로하지 않는 추가 데이터까지 서버로부터 받아오는 상황을 가리킨다.\
  \* 언더페칭(Underfetching) : 언더페칭은 클라이언트가 필요한 데이터를 한 번의 요청으로 가져올 수 없어 여러 번의 추가 요청이 필요한 상황을 가리킨다.

&#x20;

&#x20;

**REST API vs GraphQL**

<figure><img src="https://blog.kakaocdn.net/dn/cxdvDM/btsANwaMjsY/ACnvKMzLYpgITDBKYjEsIK/img.png" alt=""><figcaption><p>AWS에서 설명하는 차이점</p></figcaption></figure>

&#x20;

**GraphQL이 REST API와 비교해서 가지는 차이점**

* GraphQL은 보통 하나의 엔드포인트를 가진다.
* GraphQL은 요청할 때 사용하는 쿼리에 따라 다른 응답을 받을 수 있다.
* GraphQL은 원하는 데이터(response)만 받을 수 있다.

&#x20;

RestAPI의 경우 모든 엔드포인트를 일일이 개발하고 여러 경우의 수를 대응해야 하기에 개발 속도가 상대적으로 느리고, GraphQL의 경우에는 원칙적으로 Multipart 방식의 전송이 허용되지 않기에 이미지, 영상 등의 처리에 굉장히 약한 모습을 보인다. 그러므로 적절한 균형을 찾아 사용하는 것이 바람직하다.

&#x20;

[AWS 참고](https://aws.amazon.com/ko/compare/the-difference-between-graphql-and-rest/)

[Rest API vs GraphQL](https://blog.toktokhan.dev/rest-api-vs-graphql-7348f54a220b)

[GraphQL이란?](https://hahahoho5915.tistory.com/63)

[언더페칭, 오버페칭](https://velog.io/@yoonezi/rest-API%EC%9D%98-%EC%96%B8%EB%8D%94%ED%8E%98%EC%B9%AD-%EC%98%A4%EB%B2%84%ED%8E%98%EC%B9%AD)



### React Component

리액트의 강력한 특징은 무엇일까? [리액트 공식 문서](https://legacy.reactjs.org/)의 가장 메인에 나온 특징은 다음과 같다.

<figure><img src="https://blog.kakaocdn.net/dn/bSGp6o/btsAMUpsnVg/DfGhTDQi3iUfyJUtuigtxK/img.png" alt=""><figcaption></figcaption></figure>

가장 먼저는 선언적이라는 것이다. 데이터가 변경될 시 적절한 컴포넌트만 효율적으로 갱신하고 렌더링한다는 것이다. 두번째로는 컴포넌트 기반이라는 것이다. 스스로 상태를 관리하는 간단한 형태의 캡슐화된 컴포넌트를 만들고, 이러한 컴포넌트들을 조합하여 복잡한 UI를 만드는 것이다. 즉 한꺼번에 복잡한 UI를 만드는 것이 아닌, 단순한 형태의 컴포넌트들로 쪼개 관리하는 것이다.

&#x20;

그렇다면 이렇게 컴포넌트들을 쪼개는데 어떠한 기준이 있을까? 다음과 같은 몇 가지 기준을 참고하면 좋을 듯하다.

* **SRP (Single Responsibility Principle)** : [단일 책임 원칙](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%B1%85%EC%9E%84\_%EC%9B%90%EC%B9%99)이란 모든 클래스는 하나의 책임만 가지며, 클래스는 그 책임을 완전히 캡슐화해야 함을 일컫는다. 즉 리액트에서는 하나의 컴포넌트가 너무 커지고 있다면, 하나의 기능 및 상태를 책임지는 컴포넌트들로 분리해야 한다는 것이다. 하나의 컴포넌트가 변경되어야하면, 하나의 이유여야한다.
* **CSS** : CSS에서 우리가 이미 사용하고 있는 클래스를 활용하여 이를 기점으로 컴포넌트를 나누는 것도 생각해 볼 만하다.
* **Design’s Layer** : 디자이너가 구상한 구조를 기점으로 나누는 것도 좋다. 특히 디자이너가 붙인 이름을 팀원들이 자주 사용한다면 편리할 것이다.&#x20;
* **Information Architecture** : JSON Schema(JSON 데이터의 형식을 기술한 문서)의 영향을 받는다는 의미이다. 백엔드 서버에서 넘겨주는 JSON 데이터의 구조가 어떤 식으로 넘겨주는지에 따라 컴포넌트를 나누는 기준이 많이 달라지기 때문이다. 실제로 많이 쓰게 되고 자연스러운 SRP를 위해서 사실상 강제된다. JSON 객체 속 동일한 구조를 반복적으로 보여주는 과정에서 자연스럽게 SRP를 생각하게 되고 컴포넌트를 분리하게 된다. ex) 카테고리 별 데이터 전달 시 카테고리를 기준으로 컴포넌트 분리

&#x20;

**Atomic Design**

[아토믹 디자인](https://bradfrost.com/blog/post/atomic-web-design/)은 UI를 물질의 가장 작은 단위인 원자(atom)처럼 최대한 쪼개고, 그것들을 조합하고 점진적으로 확장시켜 일관성 있는 디자인 시스템을 구축하는 것을 목표로 한다. 아토믹 디자인의 구성 요소로는 원자(atom)에서 시작해, 분자(molecule), 유기체(organism), 템플릿(template), 페이지(page)가 있다.

&#x20;

**Extract Function**

아주 흔히 쓰이는 SRP를 위한 수단이다. 변화의 크기(영향 범위)를 제약한다. 일단 길게 코드를 작성하고, 적절히 자를 수 있는 부분이 보일 때 “함수로 추출”한다. 또는 코드를 작성하기 어려운 상황에 직면했을 때 함수로 추출한다. 바로 다른 파일을 만들어야 한다고 생각하지 않아도 된다. 컴포넌트 나누는 기준이 애매하면 다시 하나의 컴포넌트로 합쳤다가(Inline Method) 다시 나눠줘도 됨.

&#x20;

**Props**

나눠진 컴포넌트를 서로 연결하는 방법이다. 자바스크립트를 쓰면 props를 넘겨줄 때, 하나의 객체로 묶어서 props를 넘겨주면, 안에 뭐가 들었는지 모르기 때문에 하나씩 넘겨줘야 하는데, 타입스크립트를 쓰면, type이나 interface로 잘 정의가 되어있기 때문에 한꺼번에 객체로 넘겨줄 수 있어서 사용에 용이하고, 재사용시에도 용이하다. 이러한 이유로 props는 TypeScript를 잘 쓰거나 잘못 쓰게 되는 포인트 중 하나로 적절한 균형점을 잡는 게 중요하다. 테스트 코드를 작성하면 재사용성을 평가하기 쉬워진다.

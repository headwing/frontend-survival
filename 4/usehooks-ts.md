# usehooks-ts

*   usehooks-ts

    * useBoolean\
      참/거짓을 다룰 땐 toggle 같이 의도가 명확한 함수를 쓰는 게 좋다.



    * useEffectOnce\
      의존성 배열을 빈 배열로 넣어서 한 번만 실행하는 Effect를 잡아줄 때가 많은데, 이걸 쓰면 더 명확히 드러난다.



    * useFetch\
      간단히 fetch를 사용할 때 좋음.\

    * useInterval\
      React에서 setInterval 등을 쓸 때는 주의해야 할 부분이 있어서 Custom Hook을 만들어서 해결해야 함.



    * useEventListener\
      모든 종류의 이벤트를 확인할 수 있음. 특히 dispatchEvent로 전달되는 커스텀 이벤트에 반응하기 좋다.



    * useLocalStorage\
      localStorage와 JSON으로 객체 영속화. 이벤트를 통해(dispatchEvent + useEventListener) 다른 컴포넌트와 동기화하는 게 매우 중요한 특징.



    * useDarkMode\
      로컬스토리지 값을 변경하여 다크모드 전환이 쉽도록 함.


* swr\
  SWR은 먼저 캐시(stale)로부터 데이터를 반환한 후, fetch 요청(revalidate)을 하고, 최종적으로 최신화된 데이터를 가져오는 전략입니다.



* react-query\
  서버의 데이터 가져오기/업데이트, 캐싱, 에러 처리 등 비동기 작업 처리를 쉽게 할 수 있도록 돕는 라이브러리입니다. v3까지는 React Query라는 이름으로 React만 지원했는데, v4 부터 React 이외의 프레임워크(Vue, Svelte, Solid)에서 사용할 수 있도록 업데이트 되며 TanStack Query로 이름이 변경되었습니다.

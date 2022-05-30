# Next.js

React의 SSR을 위한 프레임워크
<br />

### What?

- The React Framework for Production

### Why?

- React는 CSR 방식으로 SEO에 취약한 단점이 있다. 이를 해결하기 위해 별도로 SSR 세팅을 해주어야 하는데, Next.js는 이를 자동으로 해준다.
- Link를 사용하여 a 태그와 달리 페이지를 리로딩하지 않고 페이지 이동을 할 수 있다.
- 페이지 기반 라우팅 으로 폴더명으로 페이지 route를 지정할 수 있어 편리하다.

### How?


***Pre-rendering**

- Next.js의 브라우저 렌더링 방식
- 각 페이지들을 사전에 미리 HTML문서로 생성하여 가지고 있는 것


<br />
<br />
<br />


라우트로 요청을 보낸다.

→ ***Return pre-rendered page (no data here)***

→ ***Executed React Code (HTML페이지가 보여지고 나면, React 코드가 실행된다)***

- 이 시점에서 useEffect가 실행되면서 fetch Data를 하게되며, 페이지가 updated 된다 

- 비로소 fully interactive page가 된다.

<br />

***data와 함께 pre-rendered된 페이지를 제공하고 싶다면??***
→ SSG 방식 사용


<br />

- Next가 제공하는 pre rendering 방식은 2가지가 있다.
[SSR과 SSG?](./ssg-ssr.md)


|Content                            | Date       |
|-----------------------------------|------------|
|[Routing](./routing.md)           | 2022-05 |

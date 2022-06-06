# 상세페이지 접근시 그래프 정보 업데이트 안되는 이슈

<br />

Prologue

<br />

포켓몬 도감을 개발하면서, detail 페이지로 접근시 해당 포켓몬의 Stat정보를 
그래프로 보여주도록 했다. <br />
`useEffect` 에서 데이터를 fetch하고, fetch된 데이터를 가지고 각각의 그래프 bar를 그리는 함수, `paintGraph()`를 실행하도록 설계를 했다.
이때, Happiness를 제외한 각각의 bar는 `map`함수로 그려지는 요소 였으며, useRef로 ref를 설정해 dom을 제어해주고 있었다. 해당 값에 맞게 `paintGraph()`에서 `width` 값을 세팅해주었다.

<br />

하지만 위의 로직은 생각과 다르게 동작했다. `map`을 통해 그려지지 않고 있는 Happiness를 재외하고는 값 업데이트가 정상적으로 안되는 경우도 있었으며, 업데이트가 되더라도 bar에 정의한 css `transition: all 1s ease` 가 동작하지 않았다.

<br />
처음에는 리랜더링이 안되서 발생한 문제인가 싶었지만, 그랬다면 Happiness도 마찬가지로 정상적으로 그려지지 않아야 했으므로 state 업데이트 문제는 아니라고 생각되었다. <br />

디버깅과 `paintGraph`함수에 console을 찍어 확인해본 결과 ref로 정의된 해당 요소의 `ref.current` 가 `null` 인 경우 정상적으로 동작하지 않고 있음을 확인 할 수 있었고, 이는 `map`을 통해 해당 요소가 그려지고 ref가 매핑되는 시점과 `paintGraph`가 실행되는 시점이 안맞아서 발생한 이슈임을 알 수 있었다. 

<br />

이 문제를 해결하기 위해, `paintGraph`함수에  `loaing` state를 의존성 배열에 추가해 주었으며, 조건에 해당요소의 ref 유무 뿐만 아니라  `loading`인 경우에도 return을 시키도록 수정해 주었다.

<br />
그렇다면 여기서 dom을 그리는 시점과 useEffect가 실행되는 시점, 즉 리액트의 라이프 사이클을 한 번 짚고 넘어가 보자


[Using the Effect Hook](https://ko.reactjs.org/docs/hooks-effect.html)
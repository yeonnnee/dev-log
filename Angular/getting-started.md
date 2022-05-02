#Getting Started

>folder structure

index.ts파일에 보면 `<app-root></app-root>` 라는 코드를 볼 수 있다.<br />
일반적이지 않은 이 태그는 app.ts에서 `@Component` 에 명시해 준 태그 명이다. <br />
이 두 파일을 연결해주는 것은 무엇인가? <br />
app.module.ts 파일로 가보자<br />

- declarations : 컴포넌트 정의 하는 부분. 이곳에 컴포넌트를 정의해야 앵귤러가 인지할 수 있다.
- bootstrap : 어떤 컴포넌트를 제일 먼저 보여줄 것인지를 정의 하는 곳. index.html을 찾도록 명령하는 곳
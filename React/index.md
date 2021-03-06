# React

> Mutation을 하지말자, 그 대신 데이터가 바뀌면 View를 날려버리고 새로 그려버리자.

### What?
---
> UI를 위한 라이브러리
    
- 복잡하고 다량의 요소를 가지고 있는 UI를 작고 분리된 코드의 조각인 컴포넌트로 구성 (재사용 가능한 조각들의 집합)
- MVC 프레임워크에서 view를 컴포넌트화 하는데 집중되어 있는 것이 컨셉
- DOM을 직접 다루지 않고 데이터 상태에 따라 UI 관리 
- 단방향 데이터 바인딩
    -> 데이터 변화를 감지하면 특정함수를 실행시켜 DOM객체 갱신
    

> 가상돔

- 변화가 생겼을때 실제 DOM에 접근하여 조작하는 것이 아닌 DOM 작업을 가상화하여 미리 처리 
    -> 최종적인 결과를 한 번에 DOM에 적용

> JSX 
- Javascript Xml의 약자
- UI 표현의 편의를 위해 xml형태의 구문을 자바스크립트 구문 사이에 사용할 수 있게 만든 문법
-> html, css, javacript 를 한 파일에서 한 번에 처리할 수 있다.


### Why?
---
- 단반향이므로 하위요소가 상위 부모 데이터에 영향을 주지 않는다.
- 상대적으로 가볍다
- 버전 간 마이그레이션이 쉽다 > codemodes 제공


### How?
---
|Content                                  | Date       |
|-----------------------------------------|------------|
|[Fragment](./fragment.md)                | 2022-06-07 |



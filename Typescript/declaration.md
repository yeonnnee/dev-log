# Type Declaration

2022-01-26

what?
---

**타입 별칭이란?**

- 특정 타입이나 인터페이스를 참조할 수 있는 타입 변수 의미
- 정의한 타입에 대해 나중에 쉽게 참고할 수 있게 이름을 부여하는것 ⇒ 미리보기 가능

**Union Types 이란?**

- 연산자를 이용한 타입정의
- 하나 이상의 타입을 명시할 수 있음 ⇒. `String | number`
- Union type으로 정의하면 정의한 모든 속성을 뱉어내는 것이 아니라, 공통된 값만 접근 가능

**Intersection Types 이란?**

- 연산자를 이용한 타입정의
- 여러 타입을 모두 만족하는 하나의 타입
- `&` 연산자를 이용해 여러 개의 타입 정의를 하나로 합치는 방식

<br />
Why?
---

**타입별칭**

- 인터페이스에 선언된 프로퍼티 또는 메소드의 구현을 강제하여 일관성을 유지할 수 있도록 하기 위함

**Union Types**

- any 와 달리 타입스크립트의 이점을 살릴 수 있다.

<br />
How?
---

:one: **타입 별칭 (type)**

```jsx
type MyName = string;

const name :MyName = 'cept'
```

:two: **Union Types**

```
type NetworkLoadingState = {
  state: "loading";
};
type NetworkFailedState = {
  state: "failed";
  code: number;
};

function checkNetWorkState (status: NetworkLoadingState | NetworkFailedState ) {
	status.state // OK
	status.code // ERROR
} 
```

:three: **Intersection Types**

```
type NetworkLoadingState = {
  state: "loading";
};
type NetworkFailedState = {
  state: "failed";
  code: number;
};

function checkNetWorkState (status: NetworkLoadingState & NetworkFailedState ) {
	status.state // OK
	status.code // OK
}
```
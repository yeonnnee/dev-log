# Generic


What?
---

- 재사용 가능한 컴포넌트를 위한 타입
- 단일 타입이 아닌 다양한 타입에서 작동하는 컴포넌트에서 사용할 수 있다.


<br />

Why?
---

- 재사용 가능한 컴포넌트를 구축하는 것은 중요하다
- 이러한 컴포넌트에서는 다양한 타입의 값들을 다루게 되므로, 타입이 고정되어 있지 않아 정의하기 쉽지 않다.

<br />

How?
---

```jsx
function retrunArg<T>(arg:T):T {

	return arg;
}

let output = returnArg<string>('string');

T는 string으로 정의된다.
```
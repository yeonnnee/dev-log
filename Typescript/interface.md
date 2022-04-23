# Interface

2022-01-26


what?
---
- 타입 체크를 위해 사용되며 변수, 함수, 클래스에 사용할 수 있다.
- 인터페이스는 여러가지 타입을 갖는 프로퍼티로 이루어진 새로운 타입을 정의하는 것과 유사하다.
- 프로퍼티와 메소드를 가질 수 있다는 점에서 클래스와 유사하나 직접 인스턴스를 생성할 수 없고 모든 메소드는 추상 메소드이다.

<br />
Why?
---

- 인터페이스에 선언된 프로퍼티 또는 메소드의 구현을 강제하여 일관성을 유지할 수 있도록 하기 위함

<br />
How?
---

- 기본 타입 정의

```jsx
interface User {
	name : string,
	age : number
}

const user:User = {
	name:"john",
	age: 18
}
```

- 함수 인자에 interface 적용

```jsx
interface User {
	name : string,
	age : number
}

fuction getUserInfo(user:User ) {
  // name 과 age 프로퍼티를 가지고 있는 객체가 넘어올 것을 암시 할 수 있음
	const age = user.age; // 어떤 값이 넘어올지는 모르지만, 숫자가 넘어올 것을 알 수 있다.
	const name = user.name; //어떤 값이 넘어올지는 모르지만, 문자열이 넘어올 것을 알 수 있다.
}
```

- 함수 구조를 정의하는 interface

interface SumFuntion {
	a: string;
	b:(A:number, B:number):number;
}

const a:SumFuntion = {
	a: ‘name’,
	b:(num:number) ⇒ num,
}

```

- Array 접근 방식 정의 : 인덱싱

```jsx
interface StringArray {
	[index:number] : string;
}

const arr:StringARray = [‘a’,’b’];
arr[0];
arr['0']; // typeError
```

- 객체에 접근하는 방식 정의

```jsx
interface Object {
	[key:string] : string;
}

const obj:Object= {
	country:"Kr"
}
```

- 정규식 정의 : dictionary pattern

```jsx
interface StringRegexDictionary {
	[key:string] : RegExp;
}
```

- 상속 : extends

```
interface User {
	id:string;
	email:string;
	pw:string
}

interface UserSpec extends User {
	level:number;
	rank: number;
}

const user:UserSpec; 

이렇게 정의하면 user 는 
{
	id:string;
	email:string;
	pw:string;
	level:number;
	rank: number;
}
의 구성을 갖춰야 한다.

```
# Type Inference

2022-03-16

<br />
What?
---

- TypeScript에서는 타입 표기가 없는 경우 타입 정보를 제공하기 위해 타입을 추론한다.
- VSCode상에서 코드 작성시, 코드의 타입이 무엇인지 정의해 나가는 방식
    - 자동완성 같은 기능을 도와주기 위해서는 IntelliSense가 필요한데 이게 일어나기 위해서는 내부적으로 Language Server가 돌아야 한다.
        
        ⇒ VSCode에는 타입스크립트를 지원하는 Language server가 내부적으로 탑재되어 있다.
        

<br />

How?
---

변수와 멤버를 초기화하고, 매개변수의 기본값를 설정하며, 함수의 반환 타입을 결정할 때 발생한다.

- [ ]  초기값의 타입을 통한 타입 추론

```jsx
	const a = 10;  // a:number 로 타입 추론
	let b = 'hello' // 여기서 b:string 이라고 타입틀 추론하게 된다

	b = 10; // TypeError
	b = 'hi'; // It works
```

- [ ]  인터페이스와 제네릭을 이용한 타입 추론

```jsx
interface DropDown<T> {
  value: T;
  title: string;
}

const countries: DropDown<string> = {
  value: 'KO',
  title: 'Korea'
}
```

위의 코드에서 countries 객체안의 값을 정의하려고 한다면, 그 값의 타입까지 추론하게 된다.

- [ ]  Best Common Type 추론 방식
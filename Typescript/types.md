기본 타입
---
2022-01-18

---
<br />

:one: boolean


```jsx
const disavbled: boolean = false;
```

:two: Number


```jsx
const age: number = 23;
```

:three: String



```jsx
const name: string = 'Seung Yeon Choung';
```

:four: Array


```jsx
const numArr: number[] = [1,2,3];
const stringArr: string[] = ['hi','hello'];

/* 아래와 같이 선언할 수도 있음 */

const even: Array<number> = [2,4,6];
const colors: Array<string> = ['red','blue','yellow'];

```

:five: Tuple


- 요소의 타입과 개수가 고정된 배열을 표현
- 나열된 타입의 순서를 지켜야 함

```jsx
let x: [string, number] = ['hi',24];

x = [24,'hello'] // typeError
```

:six: Enum

- 열거
- 값의 집합에 더 나은 이름을 붙여줄 수 있다.
- 0부터 시작하여 넘버링
- 요소 중 하나의 값을 수동을 설정하여 번호를 바꿀 수 있다.

```jsx
enum Color {Red, Green, Blue}
let c: Color = Color.Green;

/* 여기서 Red = 0, Green =1 Blue =2 */

enum Country {Korea = 1, UK, USA}

/* 여거서 넘버링은 1부터 시작 */

enum Fruit {Apple=1, Banana=2, Melon=12}

/* 수동으로 설정 가능 */

/*넘버링을 통해 값을 유추할 수 있다 */
let country: string = Country[1];
console.log(country); //expected output: 'Korea'
```

:seven: Any

- 알지 못하는 타입 선언
- any 사용시 타입 검사하지 않는다
- Any 타입은 타입 안정성이 없기에 사용을 지양하자

```jsx
let a: any;
a = 20;
a = 'twenty';
```
<br/>

:eight: Void

- 어떤 타입도 존재할 수 없음
- 함수에서 반환 값이 없는 경우 사용
- `—strictNullChecks` 사용하지 않을 시 void 타입 변수에는 null 과 undefined만 할당 가능

```jsx
function returnNothing():void {
	console.log('nothing');
}
```

:nine:  Null & Undefined


- 모든 타입의 하위 타입
- Number에 null 과 undefined 할당 가능
- `—strictNullChecks` 를 사용하면 null 과 undefined는 오직 any와 각자 자신들 타입에만 할당 가능


10.  Never


- 절대 발생할 수 없는 타입
- 모든타입에 할당 가능 → 하지만 어떤 타입도 never에 할당 할 수 있거나 하위타입 아님
- Never 반환하는 함수는 함수의 마지막에 도달 할 수 없다

<br />
 
11. Object

- 원시타입이 아닌 타입

<br />

12. 타입 단언(Type assertions)

- 컴파일러에게 ‘ 날 믿어, 난 내가 뭘 하고 있는지 알아’ 라고 말해주는 방법
- 타입 변환과 유사하지만, 데이터를 재구성하지는 않는다.
- Typescript보다 개발자가 값에 대해 더 잘 아는 경우가 있기에 존재

방법 1) _**angle-bracket**_

```jsx
let someType: any = 'string';

let strLength: number = (<string>someType).length;
```

방법 2) _**as**_

```jsx
let someType:any = 'hello';
let stringLegnth: number = (someValue as string).length;
```

- JSX 문법과 사용될떄는  -as 스타일만 허용
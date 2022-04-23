기본 특징
---


:one: 함수에 인자와 return 타입 정의 



```
function add(a: number, b: number): number {
	return a + b;
}

add(1,2);
```

<br />

:two: 변수를 생서함과 동시에 특정 값에 할당하는 경우 , 그 값을 해당 변수의 타입으로 사용


```
/* 타입이 string 이며, string 타입의 값만 가질 수 있다 */
const stringVariable = 'hello';
const string: string;

/* 타입이 number 이며, number 타입의 값만 가질 수 있다 */
const numberVariable = 0;
const number: number;
```

<br />

:three: 자바스크립트에서는 jsDoc을 사용하여 타입을 명시할 수 있다.

```
/**
* @typeof {Object} User
* @property {string} name
* @property {number} age
*/

const User = {
	name: 'string',
	age: 20
}

```
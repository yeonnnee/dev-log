# Type guard


2022-03-17

<br />

What?
---
- 타입을 좁혀가는 방법

<br />

Why?
---

- 유니언 타입은 값이 여러 타입 중 하나임을 의미하는데, 우리팀은 보통 api 응답값을 처리할 때 주로 사용한다. 성공하면 결과 응답값을 받아오고, 실패하면 error를 반환하기에 응답 결과에 대한 타입과, 에러 타입을 동시에 지정해주는 것이다.
    
    이때, 결과가 에러인지, 정상적인 응답값인지 알고싶으면 어떻게 해야할까?
    

```jsx
async getData() {
	const res = await this.apiServcie.getData();
	if(res.error) {
		this.handleError();
	}
	
	if(res.result) {
		this.setData();
	}
}

하지만, 위와같이 각각의 프로퍼티에 접근하려면 에러가 발생하게 된다.

해결방법) 타입 단언 사용

async getData() {
	const res = await this.apiServcie.getData();
방법1)
	if((res as ErrorType).error) {
		this.handleError(error.error);
	} else if((res as ResDataType).result) {
		this.setData(data.result);
	}

방법2)
	const error = res as ErrorType;
	const data= res as ResDataType;
	if(error.error) {
		this.handleError(error.error);
	}
	if(data.result) {
		this.setData(data.result);
	}
}

```

이때, 타입 가드를 사용하면 좀 더 깔끔하게 코드를 작성할 수 있다.

<br />
How?
---

- ****타입 서술어 사용하기 (Using type predicates)****
    
    `parameterName is Type`
    
    ```jsx
    function isSuccess(res: ResDataType| ErrorType): pet is ResDataType {
      return (resas ResDataType).result!== undefined;
    }
    
    ...
    if (isSuccess(res)) {
      this.setData(data.result);
    }
    else {
      this.handleError(error.error);
    }
    ```
    

- **`in` 연산자 사용하기**
    
    ```jsx
    function isSuccess(res: ResDataType| ErrorType) {
      if ("result" in res) {
        return this.setData(res.result);
      }
      return this.handleError(res.error);
    }
    ```
    

- **`typeof` 타입 가드**

```jsx
function isNumber(x: any): x is number {
    return typeof x === "number";
}

function isString(x: any): x is string {
    return typeof x === "string";
}

function padLeft(value: string, padding: string | number) {
    if (isNumber(padding)) {
        return Array(padding + 1).join(" ") + value;
    }
    if (isString(padding)) {
        return padding + value;
    }
    throw new Error(`Expected string or number, got '${padding}'.`);
}
```

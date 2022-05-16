# Type Assertion



What?
---

- 타입스크립트가 추론한 타입이 아닌, 개발자가 타입을 정의하는 것

<br />
Why?
---

- 가끔 타입스크립트보다 개발자가 타입을 더 잘 알고 있는 경우가 있다. 이런 경우 타입 단언을 사용하여 타입을 명시해줄 수 있다.
- **DOM 접근**에 효과적이다.

<br/>

- [ ]  **컴파일 과정에서 `타입 에러`를 없애주지만 오히혀 `런타임 에러`가 발생할 수 있다.**

개발자 입장에서 코드 타입에 대해 확신있고, 불가피한 상황이 아니라면 any와 마찬가지로 타입단언의 사용은 지양합니다.

<br />
How?
---

:one: `<Type>` 문법
    
  ```  
  getFormGroup(abstractControl: AbstractControl):FormGroup {
    return <FromGroup>abstractControl;
  }
  ```
  
    

:two: `as` 문법
    
  ```
  getFormGroup(abstractControl: AbstractControl):FormGroup {
    return abstractControl as FormGroup;
  }
  ```
    

- [ ]  React에서  `<Type>` 키워드는 **JSX**의 문법과 겹쳐 `as`를 사용하는 것이 좋다.

- DOM API

```
/* 아래 코드는 object possibly null 에러가 발생한다. */
const button = document.querySelector('#button');

/* 위의 에러를 방지하기 위해서는 두가지 방법이 있다. */
1) 타입 단언
const button = document.querySelector('#button') as HTMLButtonElement;

2) ! 사용 (해당 값이 무조건 존재한다는 것을 의미)
const button = document.querySelector('#button')!;

```
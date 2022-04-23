# enum

2022-02-13


<br />

What?
---

- 이름이 있는 상수들의 집합을 정의할 수 있다.
- 임의의 숫자나 문자열을 할당할 수 있다.
    
    enum 은 Javascript 에는 없는 개념으로, Typescript 자체적으로 구현하는 기능이다.
    

Why?
---

- 객체와 달리 enum은 항상 리터럴 타입이 사용된다.
- enum의 속성은 변경할 수 없다.
- 객체의 속성은 모든 값이 올 수 있지만, enum은 숫자와 문자만 가능하다.

⇒ **같은 ‘종류’를 나타내는 여러 개의 숫자 혹은 문자열을 다뤄야 하는데, 각각 적당한 이름을 붙여서 코드의 가독성을 높이고 싶을때 enum을 사용한다**

ex) 다국어 지원을 위한 변수명 지정

```jsx

const korean = 'ko'
const english = 'en'
const japanese = 'ja'
const chinese = 'zh'
const spanish = 'es'

type LanguageCode = 'ko' | 'en' | 'ja' | 'zh' | 'es';
type LanguageCode = typeof korean | typeof english | typeof japanese | typeof chinese | typeof spanish

const code: LanguageCode = korean;

//위처럼 하지 않고 enum을 사용하면 아래처럼 표현 가능하다
------------------------------------------------

export enum LanguageCode {
  korean = 'ko',
  english = 'en',
  japanese = 'ja',
  chinese = 'zh',
  spanish = 'es',
}

const code: LanguageCode = LanguageCode.korean;
```

<br />

How?
---

:one: **숫자 enums**
    - 아무것도 지정하지 않은 경우에는 0부터 자동으로 증가된 값을 갖게 된다.
        
        ```jsx
        enum Fruit {
        	banana,
        	apple,
        }
        
        function getFruit(fruit:Fruit) {
        	fruit.banana // 0
          fruit.apple // 1
        }
        ```
        
    - 초기화된 숫자 열거형을 선언하는 경우, 그 지점부터 뒤따르는 요소들은 자동으로 증가된 값을 갖는다
        
        ```jsx
        enum Fruit {
        	banana = 1,
        	apple,
        }
        
        function getFruit(fruit:Fruit) {
        	fruit.banana // 1
          fruit.apple // 2
        }
        ```
        

:two: **문자열 enums**

```
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}
```
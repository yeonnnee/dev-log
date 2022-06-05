# Using a checkbox with a reactive form

<br />

Prologue
<br />

모달 구현 방법 중에 하나로, `input["type"="checkbox"]` `label` 패턴을 사용하여 모달을 열고 닫는 방식이 있다. `checkbox` 가 `checked`면 숨겨놓았던 모달이 `opacity:1` 이 되면서 보이게 되는 구조이다. 이 방식을 사용하게 되면 javascript로 제어할 필요 없이 css 만으로도 모달을 열고 닫을 수 있어 편리하다. <br /> 
하지만, 이 구조에서 label이 아닌 모달 내 닫기 버튼이라던지, 다른 요소가 trigger가 되어 모달을 제어해야 한다면 `checkbox`의 `checked` 프로퍼티를 건드릴 수 밖에 없다. 

<br />

`checked` 속성을 제어할 때 주로 `ngModel`을 사용하거나 `boolean` 타입의 변수를 사용하곤 했다. 하지만, 이런식으로 해당 조건 만족 여부로 제어시 체크박스의 상태가 정상적으로 업데이트 되지 않는 경우가 있었다. 그럴땐 결국 `ViewChild`를 사용해 `nativeElement`에 접근해 `checked` 속성을 제어해주는 방식을 사용하곤 했는데, 대충 들어도 굉장히 번거로운 처리방식이다.

<br />

하지만, `formControl`을 사용하여 `checkbox` 제어시 깔끔하게 처리되는 것을 확인 할 수 있었다. 해당 formControl의 값을 적합한 조건에 따라 true, false로 세팅만 해주면 된다.
어떤 원리로 `formControl`이 checkbox를 제어하게 되었는지 알아보고자 한다.


<br />

### CheckboxControlValueAccessor 

formControl을 통해 checkbox 의 checked property를 제어할 수 있었던 이유는, Reactive form에서 제공하는 api 중 하나인 CheckboxControlValueAccessor 디렉티브 때문이다.

```jsx

isChecked:FormControl = new FormControl(false);

```

```html
<input type="checkbox" id="example" [formControl]="isChecked" />

```

[Angular docs](https://angular.io/api/forms/CheckboxControlValueAccessor)

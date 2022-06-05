# Nested Group 과 FormArray

<br />

Prologe

<br />
신규 프로젝트에서는 입력하는 form을 다룬 페이지가 많다. 입력, 수정, 상세 페이지를 모두 다루기 위해 우리팀은 Reactive Form을 사용하여 데이터를 처리하고 화면을 구성하기로 결정했다.

<br />

Nested Group 구조를 갖게 되면 form이 복잡해져 난이도가 상승하는 것을 느꼈다. 초기 form을 구성하고 세팅하는데 많은 시간을 할애했으며, formArray를 사용하면서 forEach를 여러번 돌려야 하는 상황이 발생하면서 코드가 복잡해지는건 한 순간이었다. 

<br />

그럼에도 불구하고 form을 사용했던 이유는, 초반 세팅에 시간이 걸릴 뿐 validation처리, 활성화 비활성화, reqBody 구성 및 데이터 매핑 등 처리하는 방식에서 form이 갖는 이점이 강했기 때문이다.


<br />

###Reactive Forms

***FormControl***
Reactive Forms에서 최소 단위는 `FormControl` 이다.
<br />
이 `FormControl`은 개별적으로도 존재해도 되지만, form 을 구성하는 페이지라면 여러 input 들이 있을 것이고, 이를 하나 하나 관리하기보다는 비슷한 카테고리끼리 묶어서 관리하는 것이 훨씬 편할 것이다.
<br />
Reactive Forms는 관련있는 `formControl`을 모아서 관리할 수 있는 개념으로 두 가지 방식을 제공한다. `formGroup` 과 `formArray` 다.

- `formGroup`: defines a form with a ***fixed*** set of controls that you can manage together
- `formArray`: defines a ***dynamic*** form, where you can add and remove controls at run time.


<br />
(이러한 개념의 차이로,  추가되고 삭제되는 리스트 개념이 많은 신규 프로젝트는 formArray를 사용하게 되었다.)

<br />
<br />


### FromArray


- ***formArray*** 안에는 `formGroup`,`formArray`, `formControl` 이 들어갈 수 있다.
- ***formGroup*** 안에는 `formGroup`, `formControl`, `formArray`가 들어갈 수 있다
- formArray 안에 들어있는 요소들은 `formArry.control.forEach(c ⇒ c)`로 접근 할수 있으며, 이때 반환되는 요소들은 `AbstractControl`의 타입을 갖는다. `formGroup`, `formControl` 모두 `AbstractControl`을기본으로 갖는다.


<br />
<br />

### Nested FormGroup

```jsx
examples: FormArray = new FormArray([]);

constructor(private formBuilder:FormBuilder) {
}

ngOnInit() {
	this.create();
}

create() {
    const form: FormGroup = this.formBuilder.group({
      type: null,
      name: null,
      status: this.formBuilder.array([]),
    });

    this.examples.push(form);
}

```

**상황_)** 

- formGroup 안이 아닌 독자적으로 formArray 만이 최상위 개념으로 존재
- formArray 안에는 formGroup이 존재
- create 함수를 통해 formArray 에 formGroup을 넣어주고 있다.

- **[formControl]** 과 **formControlName**의 차이
    
    Nested 요소냐 아니냐에 따라 결정되며, formControl 뿐만 아니라, [formGroup]과 formGroupName의 차이 에도 해당한다
    
    ```jsx
    singleControl:FormControl = new FormControl('');
    
    nestedGroup: FormGroup = new FormGroup({
    	nestedControl: new FormControl('');
    	secondControl: new FormControl('');
    })
    ```
    
    ```html
    <div class="nested-group" [formGroup]="nestedGroup">
      <input type="text" formControlName="nestedControl">
    	<input type="text" formControlName="secondControl">
    </div>
    
     <input type="text" [formControl]="singleControl">
    ```
    

→ 마찬가지로  `formArrayName=”examples”` 으로 지정하여 연결해주면 된다고 생각했다. 

→ Nested group의 경우 최상위를 반드시 정의해주어야 한다.

→ formArrayName 을 사용하려면 [formGroup]을 지정해 주어야만 한다. 

→ examples는 formGroup안에 속해있지 않다.

<br />
<br />

**해결방법_)**

위의 문제를 해결하기 위해 찾아낸 방법은 두 가지다

1. formGroup을 생성하여 그 안에 examples 를 넣어준다.
2. `examples` 를 지정하지 않고, examples 안의 AbstractControl 을 최상위로 정의 (아래 코드 참고)

```jsx

getFormGroup(abstractControl: AbstractControl):FormGroup {
    return abstractControl as FormGroup;
 }
```

```html
<div class="example" *ngFor="let formGroup of examples.controls; let index=index;">
    <div class="form-box" [formGroup]="getFormGroup(formGroup)">
      <input id="example" type="checkbox">
      <label class="cbx" for="example">{{formGroup .get('name')?.value}}</label>
    </div>
</div>
```

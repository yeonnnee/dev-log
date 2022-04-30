# DOM이 그려지는 과정

> Critical Rendering Path (CRP)

웹 브라우저가 원본 HTML 문서를 읽어들인 후, 스타일을 입히고 페이지로 만들어 뷰포트에 표시하기까지의 과정


> :one: HTML 파싱

- HTML을 전달받으면 브라우저의 렌더 엔진이 이를 파싱

<br />

> :two: DOM 트리 생성


- DOM 노드로 이루어진 트리 생성
- 각 노드는 HTML엘리먼트들과 연관이 있다.

<br />

> :three: CSSOM 생성

- ATTACHMENT: 노드의 스타일을 처리하는 과정

- 파싱 중 CSS파일 링크를 만나면 CSS파일을 요청해서 받고, CSS 파일을 읽어 CSSOM(CSS Object Model)을 만든다

- 외부 css 파일과 각 엘리먼트들의 inline 스타일 파싱
-> 스타일 정보를 이용하여 DOM 트리에 따라 새로운 렌더 트리 생성
-> 렌더 트리를 만드는 과정에 각 요소들의 스타일이 계산됨
-> 이 과정에서 다른 요소들의 스타일 속성을 참조

<br />

>:four: Render 트리 생성

- DOM과 CSSOM을 합쳐 Render Tree를 만든다. Render Tree는 DOM Tree에 있는 것들 중에 실제 보이는 것들로만 이루어진다.

- display: none 속성이 설정된 노드는 제외



<br />

>:five: Layout

- 렌더트리가 만들어지고 나면 레이아웃 과정을 통해 각 노드들에게 스크린의 좌표가 주어진다.
- 정확히 어디에 나타나야 할지 위치 주어짐

<br />

>:six: Painting

- 렌더링된 요소들에 색을 입히는 작업
- 화면에 원하는 정보가 나타나게 된다.


<br />

> 성능 최적화

> Reflow

- 액션이나 이벤트에 따라 html 요소의 크기나 위치등 레이아웃 수치를 수정하면 그에 영향을 받는 자식 노드나 부모 노드들을 포함하여 Layout 과정을 다시 수행하게 된다
-> Render Tree와 각 요소들의 크기와 위치를 다시 계산
-> 이러한 과정을 일컫는다.


- Reflow가 일어나는 case

    - 페이지 최초 렌더링
    - Viewport 크기 변경시
    - 노드 추가 또는 제거
    - 요소의 위치, 크기 변경 (left, top, margin, padding, border, width, height, 등..)
    - 텍스트 변경, 이미지 크기 변경


> Repaint

- Reflow가 발생하면 Render Tree를 다시 화면에 그려주는 과정이 필요
- Paint 단계가 다시 수행
- background-color, visibility와 같이 레이아웃에는 영향을 주지 않는 스타일 속성이 변경되었을 때는 Reflow를 수행할 필요가 없기 때문에 Repaint만 수행


> Repaint, Reflow 줄이기


- 사용하지 않는 노드에는 visibilty: invisible 보다 display: none



|  Reflow가 일어나는 속성  | Repaint가 일어나는 속성 |
|----------------------| ------------------- |
position               | background |
width	               | background-image  |height                 | background-position |
left                   | background-repeat |
top                    | background-size |
right                  | border-radius |
bottom	               | border-style |
margin                 | box-shadow |
padding                | color |
border                 | line-style |
border-width           | outline |
clear                  | outline-color |   display	              | outline-style |
float                  | outline-width |
font-family            | visibility |
font-size              |
font-weight            |
line-height	           |
min-height	           |
overflow               |
text-align             |
vertical-align         |
white-space            |  


 


Reflow Repaint가 일어나지 않는 transform, opacitiy와 같은 속성도 있다. 
-> left, right, width, height 보다 transform
-> visibility/display 보다 opacitiy를 사용

Node 란?


What?
---
> 노드 개체 유형

- DOCUMENT_NODE > `window.document`
- ELEMENT_NODE > `<body>` `<li>` `<p>` ...
- ATTRIBUTE_NODE > `class="header"`
- TEXT_NODE > 줄바꿈과 공백을 포함한 HTML 문서 내의 텍스트 문자
- DOCUMENT_FRAGMENT_NODE >  `document.createDocumentFragment()`
- DOCUMENT_TYPE_NODE > `<!DOCTYPE html>`

<br />
** 이 속성들은 상수 값을 가진다. <br />
`console.log(Node.ELEMENT_NODE) // return 1`

<br />
<br />


> DOM트리의 각 노드 개체는 Node로부터 속성과 메서드 상속받는다,

- [참고 링크](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes)


<br />

> 노드 값 가져오기

| Attribute  | DESC                                     | Example |
|------------| ---------------------------------------- | ------  |
|nodeValue   |Text와 Comment를 제외한 노드 유형에서는 Null 반환 | ```document.body.firstElementchidl.nodevalue = 'hi'```
|innerHTML | strong element 와 text 노드를 생성하여 DOM에 추가| document.getElementById('A').innerHTML = ```<strong>HI</strong>```|
|outerHTML | div element와 text 노드를 생성해서 원래 tag를 바꾼다| ``` document.getElementById('A').outerHTML = <div id="A">Create div instead of original Tag for id A</div>```|
|textContent| text 노드를 생성해서 해당 태그 값 갱신| ``` document.getElementById('A').textContent = "Dude" ```|
|innerText| text 노드를 생성한 해당 태그 값 갱신| ``` document.getElementById('A').innerText = "Dude" ```|


|method | DESC |
|-------|------|
|createElemet()| 생성될 element를 지정하는 문자열을 매개변수로 받는다 |
|createTextNode() | Text노드 생성 |
|createComment() | Comment노드 생성|
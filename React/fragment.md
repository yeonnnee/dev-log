# Fragment

<br />


리액트에서는  DOM 노드를 추가하지 않고 다수의 요소를 감싸고 싶을 때 Fragment를 사용하곤 한다.

<br />

 `<React.Fragment> </React.Fragment>`  , 또는 `<> </>`로 children 요소들을 감싸주면 된다.

<br />

> Each child in a list hould have a unique ‘key’ prop


<br />

나는 주로  `<> </>`  방법을 사용했으며, 해당 fragment 안에 있는 자식 요소들에게 key값을 부여해주었다.

하지만, key값은 자식 요소에 부여하는 것이 아닌, 부모 요소에 부여하는 것이었으며, `<> </>` 에는 key값을 지정할 수 없다는 사실을 알게되었다.

<br />

`unique Key prop warning` 메세지 덕분에

`<React.Fragment> </React.Fragment>`  와  `<> </>` 의 차이점을 알게 되었다.


<br />
<br />
<br />



#### Keyed Fragments

Key 는 fragments에 전달할 수 있는 유일한 속성이다. 

|Fragment                              | key 유무          |
|------------------------------------|------------------|
|`<React.Fragment> </React.Fragment>` | o |
|`<> </>`                             | x |
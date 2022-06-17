# Intersection Oberver Api 란?



타겟 Element가 Veiwport 에 포함되는지, 부모 요소에 포함되는지, 즉 화면에 보여지는 요소인지 아닌지를 판단해주는 API다.

<br />

비동기적으로 실행되기 때문에 scroll 이벤트와 달리 매번 인터섹션을 확인하여 렌더링 성능 저하를 불러일으키는 대신 인터섹션이 일어날때 특정 함수를 부르기 때문에, 이벤트를 연속 호출할 필요도 없이 사용할 수 있다.

<br />
<br />


- root: 타겟 요소가 보이는지 안보이는지 결정할 viewport로 타겟 요소의 부모 요소 or 브라우저의 viewport 다

- threshold : 옵저버가 실행되기 위해 타겟의 가시성이 얼마나 필요한지 백분율로 표시
    - 0 : 타겟의 가장자리가 root 범위를 교차하는 순간 옵저버 실행 (가시성이 0%)
    - 0.3 : 가시성이 30%
    - [ 0.3, 0.5] : 배열로 표시할수도 있다.



[참고링크](https://developer.mozilla.org/ko/docs/Web/API/IntersectionObserver)
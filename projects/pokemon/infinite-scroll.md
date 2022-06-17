# React에서 무한스크롤 다루기


무한 스크롤을 구현하라고 하면 가장 쉽게 떠오르는 방법은 스크롤이 하단에 위치하는 순간 api를 요청하는 방법이다. 하지만 서칭을 하다보니 해당 방법은 scroll event를 구독해야하며, 스크롤 될때마다 해당 함수가 호출하게 된다. 스크롤 이벤트는 짧은 시간에 대량으로 호출되고, 동기적으로 실행므로 성능저하 문제가 발생하게 된다. 

<br />

물론 이를 방지하기 위해 throttle 방식을 함께 사용하지만, 스크롤 이벤트가 발생할 때마다 함수를 호출해야하는 문제는 여전히 안고 가야한다.

<br />

무한스크롤 구현을 알아보다가 Intersection Oberver Api 에 대해 알게 되어 <포켓몬 도감> 프로젝트에서는 Intersection Observer Api를 사용하여 무한스크롤을 구현해보았다.

<br />

[Intersection Observer Api](../../web-api/intersection-observer-api.md)


### 배열의 빅오

---

- Ordered Lists
- 입력과 제거시 성능상 문제가 생길수도..
- 데이터 접근은 빠르다
    - 삽입: 배열 어디에 삽입인가에 따라 다름 → 배열 뒤에 추가하는 것은 상관없지만, 배열 앞에 요소를 추가할 경우 모든 요소의 index를 새로 배정해야 함
    - 제거: 배열 어디에 제거인가에 따라 다름 → 배열 앞의 요소를 삭제할 경우, 모든 요소의 index 재할당 해야함
    - 검색: O(n) → 배열마다 index가 있기 때문에  전체 조회가 아니라 해당 index로 바로 접근 가능
    - 접근: O(1)
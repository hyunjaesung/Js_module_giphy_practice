## 커스텀_리액트_연습
- ReactDom.render호출 되면 nextUnitOfWork 가 변화하고 이걸 감지하던 requestIdleCallback 이 돌다가 루트부터 순회 시작
- 순회하면서 리컨실러에서 effect Tag 붙여서 자식 혹은 형제로 붙이면서 old Fiber와 비교해서 effect Tag 붙인 새로운 Fiber 만들고 연결리스트로 child 혹은 sibiling 형태로 붙인다
- 자식 형제 부모 순으로 탐색하면서 Fiber Tree 만들어 낸다
- Fiber Tree 완성하면 다시 순회하면서 commit 하며 effect Tag 따라서 DOM 그려낸다
- state 변경시 wipFiber의 hooks의 해당되는 index의 state 변경 + nextUnitOfWork를 다시 바꾸고 처음부터 다시 라이프 사이클 시작
- 함수형 컴포넌트의 경우 init할때 useState 실행되면서 wipFiber에 hooks 집어넣고 시작

- 참고 : [https://bluewings.github.io/build-your-own-react/](https://bluewings.github.io/build-your-own-react/)

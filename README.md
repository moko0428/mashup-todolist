# Context API를 활용한 상태 관리

<div align="center">
<img src="./src/images/구조.png">
</div>
App에서 todos 상태와 onToggle, onRemove, onCreate 함수를 지니고 있게 하고, 해당 값들을 props를 사용해서 자식 컴포넌트들에게 전달해주는 방식으로 구현.

프로젝트의 규모가 커지게 된다면 최상위 컴포넌트인 App에서 모든 상태 관리를 하기엔 App 컴포넌트의 코드가 너무 복잡해질 수도 있고, props를 전달해줘야 하는 컴포넌트가 너무 깊숙히 있을 수도 있다.(여러 컴포넌트를 거쳐서 전달해야 하는 상황을 의미)

## Context API를 활용한 구현.

<div align="center">
<img src="./src/images/ContextAPI.png">
</div>

Context API를 사용하여 컴포넌트에서 dispatch를 바로 참조하고, 상태를 관리.

### nextId 값 관리하기

: 새로운 항목을 추가 할 때 사용할 고유 ID, 이 값은 useRef로 관리 됨.

### 커스텀 Hook 에서 에러 처리

useTodoState, useTodoDispatch, useTodoNextId Hook 을 사용하려면, 해당 컴포넌트가 TodoProvider 컴포넌트 내부에 렌더링되어 있어야 한다.
만약 TodoProvider 로 감싸져있지 않다면 에러를 발생

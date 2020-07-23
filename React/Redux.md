Redux 라이브러리
========
많이 사용하는 상태관리 라이브러리입니다.
여러 컴포넌트가 값을 공유하거나, 하위 컴포넌트에서 값을 사용할때
거쳐가는 컴포넌트마다 `props`로 전달해주어야 하기 때문에 불편합니다.
`Context API`라는 리액트에서 지원하는 기능이 있었지만 v16.3에서 개선되기 전엔 마찬가지로 불편했습니다.
이것을 개선하기 위해 나온 라이브러리가 리덕스입니다.

구성 흐름은 아래와 같습니다.
1. 액션들을 정의하고
2. 각 액션에 따라 값을 업데이트하는 리듀서를 만듭니다.
3. 해당 리듀서를 이용해 스토어를 만들고
4. `Provider`로 App컴포넌트에 스토어를 전달해줍니다.
5. 컨테이너(스토어와 컴포넌트 중간단계)를 이용해 `state`, `dispatch` 들을 `props`로 전달해줍니다.
6. 해당 컴포넌트 내에서 사용, 업데이트 합니다.

위 순서대로 예제코드를 이용해 설명하겠습니다.

1.덕스패턴, 액션 정의
=========
### 덕스패턴?
일반적인 구조로는 액션, 액션 종류들, 리듀서를 각 파일로 나누는 것입니다.
하지만 하나의 액션이 추가될 때 마다 세개의 파일을 수정하는 것에 불편함을 느낀 사람들은 
덕스패턴이라는 방식으로 작성합니다. 종류별로 나누는게 아닌 기능별로 묶는 방식입니다. 
덕스패턴으로 작성한 파일은 일반적으로 `모듈`이라고 칭합니다.

```javascript
// modules/item.js
const TOGGLE = 'items/TOGGLE',
      INSERT = 'items/INSERT',
      REMOVE = 'items/REMOVE';
let id = 0;
// 액션을 만들어주는 함수들
const toggle = id => ({
  type: TOGGLE,
  id
});
const insert = item => ({
  type: INSERT,
  item: {
    ...item,
    ++id
  }
});
const REMOVE = id => ({
  type: REMOVE,
  id
});
```
각 액션을 구분시켜줄 값들을 미리 선언해놓습니다.
이렇게 선언해놓으면 값들이 바뀌어도 처음 선언한 상수만 수정하면 되기에 유지보수에 용이합니다.
이름이 겹칠 가능성이 있어 액션 타입앞에 모듈명을 붙였습니다.

2.리듀서 정의
==========
```javascript
// modules/item.js
const initState = {
  items: []
};
// 리듀서. 상태값들과 액션 관련된 값들을 매개변수로 받는다
function reducer( state = initState, action ) {
  // action.type 값에 따라 수행할 행동을 정한다
  // 이때도 성능을 위해 불변성을 지켜줘야 한다.
  switch( action.type ) {
  case TOGGLE:
    return {
      ...state,
      items: state.items.map( item =>
        item.id === action.id ? { ...item, on: !item.on } : item
      )
    };
  case INSERT:
    return {
      ...state,
      items: state.items.concat( action.item )
    };
  case REMOVE:
    return {
      ...state,
      items: state.items.filter( item => item.id !== action.id )
    };
  default:
    return state;
}
```
특정 액션에 따라 상태를 업데이트하는 리듀서 함수를 만들어줍니다.

3, 4.스토어생성 및 전달
===========
정의한 리듀서를 이용해 스토어를 만들고 프로젝트에 적용시켜줍니다.
리듀서가 여러개라면 하나의 스토어만을 이용해야하기 때문에 
`redux`에서 제공하는 `combineReducers`라는 함수를 이용해 합쳐주시면 됩니다. 
`redux`에서 제공하는 `createStore`로 스토어를 만든 뒤
`react-redux`에서 제공하는 `Provider`로 전달해주면 됩니다.
```javascript
// modules/index.js
// 파일 이름을 index.js로 설정하면 import 시 index.js는 생략할 수 있다
// ex) import rootReducer from './modules';
const rootReducer = combineReducers({
  item,
  otherReducer,
  someReducer,
});

// src/index.js
const store = createStore( reducer );
// ...
<Provider store={store}>
  <App />
</Provider>
```

5.컨테이너 생성 후 dispatch, state 전달 
============
해당 컴포넌트를 리덕스와 이어주기 위해 react-redux 에서 제공해주는 `connect`를 이용해 `export` 해줍니다.
```javascript
// containers/ItemContainer.js
const ItemContainer = ({ items, insert, remove, toggle }) => {
  return (
    <Item
      items={items}
      onInsert={insert}
      onRemove={remove}
      onToggle={toggle}
    />
  );
};

const mapStateToProps = state => ({
  items: state.item.items
});
const mapDispatchToProps = dispatch => ({
  insert: (item) => dispatch( insert( item )),
  remove: (id) => dispatch( remove( id )),
  toggle: (id) => dispatch( toggle( id )),
});

export default connect(
  mapStateToProps,    // props로 전달해줄 상태들
  mapDispatchToProps, // props로 전달해줄 디스패치들
)( ItemContainer );   // 현재 컨테이너
```
액션 생성 팩토리 함수인 `mapDispatchToProps`대신 `bindActionCreators`를 이용해 아래와 같이 작성할 수도 있습니다.
```javascript
dispatch => bindActionCreators({
  insert,
  remove,
  toggle
})
```
더 간단한 방법으로 객체형태로 `{ insert, remove, toggle }`과 같이 넣어줄 수도 있습니다.
react-redux에서도 해당 방법을 권장하고 있습니다.

6.해당 컴포넌트에서 props로 값을 받아와 사용하기
===========
`props`로 받아와 사용하면 됩니다.
App.js같이 불러와 사용할때는 해당 컴포넌트가 아닌 컨테이너 컴포넌트를 사용하면 됩니다.

\
레퍼런스:
- https://react-redux.js.org/api/connect
- https://react-redux.js.org/using-react-redux/connect-mapdispatch

# 만약 State, reducer가 더 필요하다면?

-----

## 하나 더 만들면 됩니다.

```javascript
let user = [{id : 0, name: 'David'}];
let newUser = [{id : 0, name: 'June'}];

const reducer = (state = user, action) => {
    if (action.type === 'setIdUp'){... 
    reducer 파일에서 만든 코드 
}

const reducer2 = (state = newUser, action) => {
    return state
}

let store = createStore(reducer)

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider store={store}>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>

);
```

---
이제 `store`에 등록을 해야하는데 `store`에 등록하는 방식이 달라집니다.

기존 방식은 
```javascript
let store = createStore(reducer)
```
였지만

```javascript
let store = createStore(combineReducers({reducer, reducer2}))
```
로 바꿔서 지정해야합니다.

----
이제 `Component`에서 사용해봅시다.

`reducer`를 `combine`했기 때문에 `{reducer:[], reducer2:[]}`로 형식이 달라지게 됩니다.

코드를 아래와 같이 수정합니다.

```javascript
import {connect} from 'react-redux';
const Test = (props) => {
    return(
        <>
            <div>id</div>
            <div>{props.state[0].name}</div>
        </>
    );
}
function getState(state){
    return {
        state : state.reducer,
        state2: state.reducer2
    }
}

export default connect(getState)(Test);
```
이렇게 지정하면 `{props.state[0].name}`일 때는 `david`가, `{props.state2[0].name}` 일 때는 `june`이 출력됩니다.
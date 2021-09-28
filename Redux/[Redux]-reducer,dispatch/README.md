# Redux의 `state` 수정

---
## Reducer

---
```javascript
import {Provider} from 'react-redux';
import {createStore} from 'redux';
import {useState} from 'react';

const reducer = () => {
    return(
        {num : 0}
    );
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

위와 같이 `num: 0`을 `store`에 저장했다고 합시다.

`createStore`에 `reducer`를 넣어주면 됩니다.

or
```javascript
let num = [{num : 0}];

const reducer = (state = num, action) => {
    return state
}
let store = createStore(reducer)

```
이렇게 작성하셔도 됩니다.

---
아래 문법은 `default 파라미터`문법입니다.

`default 파라미터`문법이란?
- 함수에 파라미터 입력을 안하거나 값이 없을 때 기본적으로 가질 수 있는 기본값입니다.

ex)
```javascript
const 테스트문법=(a = 10, b = 1) => {
    console.log(a+b)
    
}
테스트문법(1);
```
`console`에는 `11`이 출력됩니다.

`a`값으로는 `1`이 들어왔으나 `b`는 주어지지 않았으므로 기본값인 `1`이 할당됩니다.

---

## `Reducer`에 데이터 수정방법을 미리 지정하기

---

```javascript
let user = [{id : 0, name: 'David'}];

const reducer = (state = user, action) => {
    if (action.type === 'setIdUp'){ //action타입 지정
        let copyUser = [...state]; // React는 직접적으로 state를 수정하면 안됨. 복사후 수정
        copyUser[0].id++; // id의 값을 1 증가
        return copyUser //값을 반환
    }
    else if (action.type === 'setIdDown'){
        let copyUser = [...state];
        copyUser[0].id++;
        return copyUser
    }
    return state //action을 선택하지 않으면 기본값 반환
}
let store = createStore(reducer)

```

이제 `Component`에 적용해봅시다.

```javascript
<button onclick={ () => {props.dispatch({type:'setIdup'})}}>
    아이디 값 증가
</button>
```
`id`값을 증가시키는 버튼

```javascript
<button onclick={ () => {props.dispatch({type:'setIdDown'})}}>
    아이디 값 감소
</button>
```
`id`값을 감소시키는 버튼

 

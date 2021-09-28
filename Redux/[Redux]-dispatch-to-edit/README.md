# Dispatch에 데이터 실어보내기

---
```javascript
let user = [{id : 0, name: 'David'}];

const reducer = (state = user, action) => {
    if (action.type === 'Edit name') { //이름 수정 action 설정
       let CopyUser = [...state];
        (이름 수정하는 코드)
    }
    else if (action.type === 'setIdUp'){ //action타입 지정
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

## `dispatch`에 `patload`로 데이터 보내기

---
```javascript
<button onclick={ () => {props.dispatch({type:'setIdup', payload:'안녕'})}}>
아이디 값 증가
</button>
```

`dispatch({type:'함수이름', payload:'보낼 데이터')`

위와 같이 `dispatch`함수 안에 값을 실어보낼 수 있습니다.

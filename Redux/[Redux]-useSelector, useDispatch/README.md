# `useSelector`, `useDispatch`로 간소화하기

---

## useSelector로 state를 props로 변환 간소화하기

---

```javascript
const Test = (props) => {
    return(
        <>
            <div>id</div>
            <div>{props.name}</div>
        </>
    );
}
function getState(state){
    return {
    state : state
    }
}

export default connect(getState)(Test);
```
위 코드로 `Component`에서 데이터를 받았었는데 `useSelector`를 쓰면 아래와 같이 간소화가 된다.

```javascript

const Test = (props) => {
    let state = useSelector((state) => state)
    
    return(
        <>
            <div>id</div>
            <div>{state.name}</div>
        </>
    )
}
export default connect(getState)(Test);
```

## useDispatch 로 dispatch 간소화하기

---

```javascript
const Test = (props) => {
    let state = useSelector((state) => state)
    let dispatch = useDispatch()

    return(
        <>
            <div>id</div>
            <div>{state.name}</div>
            <button onclick={ () => {dispatch({type:'setIdup'})}}>
                아이디 값 증가
            </button>
        </>
    )
}
export default connect(getState)(Test);
```

```javascript
<button onclick={ () => {props.dispatch({type:'setIdup'})}}>
    아이디 값 증가
</button>
```

이 코드가 
```javascript
<button onclick={ () => {dispatch({type:'setIdup'})}}>
    아이디 값 증가
</button>
```
이렇게 됩니다.
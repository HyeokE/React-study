# React에서 쓸 수 있는 if문 작성방식


---
## 1. if/else
```javascript
const Component = () =>{
    if (true){
        return <div>true일 때 보이는 컴포넌트</div>
    }
    else{
        return null
    }
}
```

or 

```javascript
const Component = () =>{
    if (true) {
        return <div>true일 때 보이는 컴포넌트</div>
    }
        return null
}
```

## 2. 삼항연산자

```javascript
const Component = () => {
    return(
        <>
            {
                변수 === 1
                    ? <div>true일 때 보이는 컴포넌트</div>
                    : <div>false일 때 보이는 컴포넌트</div>
            }
        </>
    )
}
```

## 3. &&사용하기

```javascript
const Component = () => {
  return (
    <div>
      {
        변수 === 1 && <p>true일 때 보이는 컴포넌트</p>
      }
    </div>
  )
}
```

## 4. switch /case 

````javascript
const reducer = (state, action) => {
    switch (action.type){
        case "Up":
            return state + 1;
        case "Down":
            return  state - 1;
        default:
            return  state;
    }
}
````

## 5. enum

```javascript
const Component = () => {
    let userState = 'good'
    return(
        <div>
            {
                {
                    good: <p>좋아요!!</p>,
                    notBad: <p>힘내봐요!</p>,
                    bad: <p>하루 쉬는 것은 어떨까요?</p>
                }[userState]
            }
        </div>
        
    )
}
```
위와 같이 작성하게 되면 `userState`에 따라 나타나는 `<p>`태그가 달라지게 됩니다.

or 

이렇게 해도 됩니다
```javascript
var userUI = {
    good: <p>좋아요!!</p>,
    notBad: <p>힘내봐요!</p>,
    bad: <p>하루 쉬는 것은 어떨까요?</p>
}
const Component = () => {
    var userState = 'good'
    return(
        <div>
            {
                userUI[userState]
            }
        </div>
    )
}
```

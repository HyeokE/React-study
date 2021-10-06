# State에 Array 집어넣기

---

```javascript
const Component = () => {
    const [Array, setArray] = useState(["apple", "apple1", "apple2"])
    return(
        <div>
            {Array}
        </div>
    )
}
```

이런 `Component`가 있다고 해봅시다.

`Array`안의 모든 자료들이 출력되게 하려면 어떻게 해야할까요.

보통 반복문을 쓰겠죠.

`React`에서는 `map`을 씁니다.

## `map`

---

`map`을 사용하는 방법은 다음과 같습니다.

`array.map(함수, id)`
함수내에 제공되는 자료는 `array`의 모든 자료입니다.

`id`는 `Array`의 몇 번째 자료인지 알려줍니다.

`JAVA`의 `for`문으로는 아래와 같이 표현할 수 있습니다

```js
for (int i = 0; i < array.length(); i++){
    System.out.println(array[0]);
}
```

### if) `map`을 사용하지 않는다면

```javascript
const Component = () => {
    const [Array, setArray] = useState(["apple", "apple1", "apple2"])
    return(
        <div>
            <div>{Array[0]}</div>
            <div>{Array[1]}</div>
            <div>{Array[2]}</div>
        </div>
    )
}
```
이렇게 작성할 수 있습니다.

### `map`을 사용해봅시다.

```javascript
const Component = () => {
    const [Array, setArray] = useState(["apple", "apple1", "apple2"])
    return(
        <div>
            {Array.map( (받은자료, id) => {
                <div key={id}>{받은자료}</div>
            })}
        </div>
    )
}
```

### + map으로 `array`수정하기


```javascript
const Component = () => {
    const [Array, setArray] = useState([{id: 1, name:"apple"},{id: 2, name: "apple1"},{id : 3, name: "apple2"}])
    return(
        <div>
            {Array.map( (받은자료, id) => {
                <div key={id}>{받은자료.name}</div>
            })}
        </div>
    )
}
```


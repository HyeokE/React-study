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

```javascript
for (int i = 0; i < array.length(); i++){
    array[0]
}
```

`for`문과 같은 방식이라고 생각하면 됩니다.

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


위와 같이 사용할 수 있습니다.

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
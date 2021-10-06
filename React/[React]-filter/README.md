# filter

---

`filter`는 조건이 `true`면 반환하고 `false`는 반환하지 않는 함수이다.

```
const newArray = array.filter(
(받은 자료들) => {return 조건}
)
```

이렇게 사용한다.



```js
 const [array, setArray] = useState([{ id: 1 }, { id: 2 }, { id: 3 }]);

  console.log(newArray);

```

`array`라는 배열안에 `array`가 또 존재하는 변수이다.

`newArray`에 `id`가 1이 아닌 다른 것들만 집어넣어보자.

```js
const [array, setArray] = useState([{ id: 1 }, { id: 2 }, { id: 3 }]);

const newArray = array.filter((task) => {
    return task.id != 1;
});

console.log(newArray);
```

이렇게 쓸 수 있다.

+ 위 예시에서 task는 `{ id: 1 }`, `{ id: 2 }`, `{ id: 3 }`를 의미한다.


### `id`가 `2`인 자료를 삭제해봅시다.


```javascript

const Box = (받은자료, {deleteTask}) => {
    <div key={받은자료.id} onClick={
        (id) => {
            deleteTask(id)
        }
    }>
    {받은자료.name}
        </div>
    }
const Component = () => {
    const [array, setArray] = useState([{id: 1, name:"apple"},{id: 2, name: "apple1"},{id : 3, name: "apple2"}]);
    
    const deleteTask = (key) => {
        arrayCopy = array.filter(
            (prevTask) => { return ( prevTask.id != key)})
        setArray(arrayCopy);
    }
    return(
        <div>
            {Array.map( (받은자료, id) => {
               <box 받은자료={받은자료} delete={deleteTask}/>
            })}
        </div>
    )
}

```
# `Component`로 코드 나누기

---

```js
const Test = () => {
const[userInfo, setUserInfo] = useState(
    [
        {name : "Jason", age: 22, city: 'Seoul'},
        {name : "Jimmy", age: 23, city: "Seoul"},
    ]
);
    return(
        <>
            <div>
                {userInfo[0].name}
            </div>
            <div>
                {userInfo[1].age}
            </div>
            <div>
                {userInfo[2].city}
            </div>
            <div>
                {userInfo[0].name}
            </div>
            <div>
                {userInfo[1].age}
            </div>
            <div>
                {userInfo[2].city}
            </div>
        </>
    )
}
```
유저 정보를 보여주는 코드를 `Component`화 시켜봅시다.

```js
const UserCard = ({userInfo}) => {
    
    return(
        <>
            <div>
                {userInfo.name}
            </div>
            <div>
                {userInfo.age}
            </div>
            <div>
                {userInfo.city}
            </div>
            </>
    )
}
const Test = () => {
const[userInfo, setUserInfo] = useState(
    [
        {name : "Jason", age: 22, city: 'Seoul'},
        {name : "Jimmy", age: 23, city: "Seoul"},
    ]
);
    return(
        <>
            {userInfo.map(
                (userInfo) => {
                    <UserCard userInfo={userInfo}/>        
                }
            )}
            
        </>
    )
}
```
`map`함수와 `userCard`를 `Component`화 하여 간소화하였습니다.
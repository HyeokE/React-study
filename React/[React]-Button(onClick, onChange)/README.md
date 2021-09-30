# 버튼을 만들어봅시다.

---
```javascript
import React, { useState } from 'react';

function App(){

  const [num, setNum] = useState(1);
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{num}</div>
              <div>숫자 증가</div>
          </div>
      
    </div>
  )
}
```

전 글을 보고 오셨을 테니 이건 아실겁니다.

`const [num, setNum] = useState(1);`

`num`이라는 `state`에 기본값을 `1`로 지정했습니다.

`<div>숫자 증가</div>`를 눌러 `num`이 증가하도록 만들어봅시다.

## 눌렀을 때 동작하게 만드는 `onClick`

---

리액트에서는 `onClick`을 `<div onClick={실행할 함수}>숫자 증가</div>` 이렇게 짭니다.

예를 들자면 이렇습니다.

```javascript
1. 
<div onclick={ 이미 선언한 함수 }>숫자증가</div>
2. 
<div onclick={function (){
    실행할 것들
}}>숫자증가</div>
3. 
<div onclick={ () => {
    실행할 것들
}}>숫자증가</div>
```

### 이제 적용해봅시다.

---

`숫자 증가`를 누를 때마다 `num`이 증가하도록 만들어봅시다.

위의 `onClick`을 사용하면 아래와 같습니다.

```javascript
import React, { useState } from 'react';

function App(){

  const [num, setNum] = useState(1);
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{num}</div>
              <div onclick={ () => {
                  setNum(num+1);
              }}>숫자 증가</div>
          </div>
      
    </div>
  )
}
```

## `onChange`함수로 `state`수정하기

---
```javascript
import React, { useState } from 'react';

function App(){

  const [todo, setTodo] = useState('숨쉬기');
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{todo}</div>
              
          </div>
      
    </div>
  )
}

```

이 상태로 실행하면 `todo`의 첫 번째인 `숨쉬기`가 출력되겠죠.

`숨쉬기`를 다른 것으로 바꿔봅시다.

입력을 받도록 `<input/>`을 만들어줍시다.

```javascript
import React, { useState } from 'react';

function App(){

  const [todo, setTodo] = useState('숨쉬기');
  const [getText, setGetText] = useState("");
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{todo[0]}</div>
              <input onchange={ () => {
                  getText변경하기
              }}/>
          </div>
      
    </div>
  )
}

```

`onChange` `<input/>`이 변경될 때마다 실행됩니다.

`onChange`가 `getText`를 변경하도록 만들려면 어떻게 해야할까요

```javascript
import React, { useState } from 'react';

function App(){

  const [todo, setTodo] = useState('숨쉬기');
  const [getText, setGetText] = useState("");
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{todo}</div>
              <input onchange={ (e) => {
                  setGetText(e.target.value)
              }}/>
          </div>
      
    </div>
  )
}

```
`input`에 들어오는 글자를 가져오기 위해서는 `e.taget.value`를 사용해야합니다.

`e.target`은 `지금 이벤트가 동작하는 HTML요소` 위 코드에서는 `input`태그

`.value`는 입력값을 의미합니다.

이제 버튼으로 `todo`를 바꿔봅시다.

```javascript
import React, { useState } from 'react';

function App(){

  const [todo, setTodo] = useState('숨쉬기');
  const [getText, setGetText] = useState("");
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{todo}</div>
              <input onchange={ (e) => {
                  setGetText(e.target.value)
              }}/>
              <button onClick={ () => {
                setTodo(getText);
              }}>
              Todo 설정</button>
          </div>
      
    </div>
  )
}
```
버튼이 클릭되면 `setTodo`함수로 `todo`를 `getText`값으로 변경합니다.

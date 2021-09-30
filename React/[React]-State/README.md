# State

## React에 데이터 저장하는 방법



```javascript
function App(){

  var data = '안녕 나는 문자야';
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{data}</div>
          </div>
      
    </div>
  )
}
```

위 와 같은 코드를 작성해보았습니다.

```javascript
<div className = "body-Task">     
    <div>{data}</div>
</div>
```

저번 글에서 이 부분만 추가가 되었는데 데이터를 `state`에 저장하도록 바꿔봆시다.

```javascript
import React, { useState } from 'react';

function App(){

  var data = '안녕 나는 문자야';
  const [post, setPost] = useState('기본값이에요');
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{data}</div>
          </div>
      
    </div>
  )
}
```

새로운 문법이 등장했죠 `useState`라는 것입니다.
```javascript
const [post, setPost] = useState('기본값이에요');
```

`post`는 변수 

- `setPost`는 `post`라는 변수를 변경하게 도와주는 함수입니다. 

- `useState(여기}` 여기에는 `post`에 들어갈 기본값을 넣어줍니다.

- 이곳에는 `null`, `int`, `String`, `array` 등등 들어갈 수 있습니다.

ex)`array`를 넣었을 때`useState(['나는 첫 번째 기본값','나는 두 번째 기본값']);`

`useState`의 변수도 똑같이 데이터바인딩이 가능합니다.

```javascript
import React, { useState } from 'react';

function App(){

  var data = '안녕 나는 문자야';
  const [post, setPost] = useState('기본값이에요');
  return (
    <div className="App">
      <div className="black-nav">
      </div>
        <div>안녕 나는 상단바야</div>
          <div className = "body-Task">
              <div>{data}</div>
              <div>{post}</div>
          </div>
      
    </div>
  )
}
```

이걸 실행하면 `post`의 기본값인 `기본값이에요`가 출력됩니다.

### 변수를 왜 `state`에 저장해서 쓸까요.

---

React는 `state`가 변경되면 `HTML`을 자동으로 랜더링 해줍니다.

일반적인 변수에 저장되면 랜더링이 이루어지지 않으니 자주 바뀌는 변수라면 `state`에 선언해주세요



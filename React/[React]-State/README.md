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

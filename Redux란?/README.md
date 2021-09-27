# Redux란?

React의 props를 보다 편하게 관리하기 위한 라이브러리입니다.

#### if) Redux를 사용하지 않는다면? 

각 컴포넌트 마다 `props -> props -> props `로 전달해야하죠.

## 사용 방법

-----

` npm install redux `

` npm install react-redux`
를 설치합니다.

`redux` 와 `react-redux` 두 가지를 설치하는 이유는 용도가 다릅니다.

- `redux` 는 앞서 말한 데이터를 관리하는 라이브러리
- `react-redux`는 `redux`를 React에서 사용할 수 있도록 합니다.

### 기본환경 세팅

--------

1. `index.js`에 주로 세팅합니다.

2. ` Provider`라는 것을 import 합니다.
3. state를 공유하고 싶은 컴포넌트를 아래와 같이 감싸줍니다.

```javascript
import {Provider} from 'react-redux';

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>
);
```
4. `redux`의 `state`는 `createStore()`라는 함수를 써야합니다.
```javascript
import {Provider} from 'react-redux';
import {createStore} from 'redux';
import {useState} from 'react';

const[name, setName] = useState('David');

let store = createStore(()=> {return  name })

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>

);
```
5. Provider에 `store`를 전달해주면 됩니다.
```javascript
import {Provider} from 'react-redux';
import {createStore} from 'redux';
import {useState} from 'react';

const[name, setName] = useState({id: 0,name:'David'});

let store = createStore(()=> {return  name })

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <Provider store={store}>
        <App/>
      </Provider>
    </BrowserRouter>
  </React.StrictMode>

);
```

### `state`를 받아오는 방법

---------

`Test.js`에서 `state`를 받아온다고 생각해봅시다.

`store`의 데이터를 `props`형태로 지정해줘야 사용할 수 있습니다.

1. `import {connect} from 'react-redux';`
2. 함수 하나를 만들어줍니다.
이 함수는 `store`의 `state`데이터를 `props`로 지정해주는 역할입니다.

( 이름은 상관없습니다.)

저는 아래와 같이 정의해주었습니다.
```javascript
function getState(state){
    return {
        state : state
    }
}
```
`return{}`안에 `김치 : state` 이렇게 적으면 `index.js`에서 등록한 `store`의 모든 `state`가 `김치 props`로 등록됩니다.


4. `export default Test`를 `export default connect(원하는 함수명)(현재 컴포넌트 명)`으로 변경해줍니다.

```javascript
import {connect} from 'react-redux';
const Test = () => {
    return(
        <>
            <div>id</div>
            <div>이름</div>
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

이렇게 하시면 `state`를 `props`로 받아 사용할 수 있습니다.

```javascript
import {connect} from 'react-redux';
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

마지막으로 정리하자면
- index.js 세팅
1. `index.js`에 `<Provider>`를 가져와 `state`값를 보내고 싶은 `component`를 감싸주면 됩니다.
2. `createStore`를 위의 방법으로 `state`를 만들어 `let store`에 저장합니다.
3. `<Provider>`에 `store={store}`를 넣어 `<Provider store={store}>` 이와 같이 만들어줍니다.
4. `<Provider>`가 감싸고 있는 `component`는 props 필요없이 데이터를 받을 수 있습니다.

- `store`로 전송한 데이터 사용
1. 데이터를 사용하고 싶은 `component`로 이동해서 데이터를 `props`로 지정해줄 함수 하나를 만들어줍니다.
   (예를 들기 위해 여기서 만든 함수의 이름을 `감자`라고 하겠습니다.)
2. 함수에 아래와 같이 `state`를 `props`로 지정해줍니다.
````
return {
   props이름 : state
   }
````


3. 하단의 `export default 컴포넌트이름`을 `export default connect(감자)(컴포넌트이름)`
4. 이렇게 세팅하시면 `component`에서 `props.props이름`으로 데이터를 받아올 수 있습니다.
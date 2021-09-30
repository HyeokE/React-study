ㅎ# JSX의 시작

---

폴더로 이동하시면 `index.js`, `app.js`가 있습니다.

이 중 `app.js`가 우리의 main page 입니다.
```javascript
function App(){
  return (
    <div className="App">
      안녕 안녕 여긴 메인페이지야
    </div>
  )
}
```

### 이제 상단의 `nav`를 만들어봅시다.

---
```javascript
function App(){
  return (
    <div className="App">
      <div className="TopNav">나는 상단바야</div>
    </div>
  )
}
```
#### CSS도 건들여봅시다.
```css
(App.css)
    .TopNav {
    background : #9f9f9f;
    width : 100%;
    display : flex;
    padding : 20px;
    font-weight : 600;
    font-size : 20px;
}
```
저장하시면 상단에 회색빛의 바가 생성됩니다.

`HTML`을 공부하셨던 분들이라면 조금 불편하신 부분이 있을겁니다.

바로 `className`인데요. 

React 에서 `class`를 사용하고 싶으실 때 사용하면 됩니다.

HTML과 기능은 동일합니다.


이 모든 것들이 JSX입니다.


### React에서 데이터바인딩하기

---

```javascript
function App(){

  var data = '안녕하세요';
  return (
    <div className="App">
      <div className="black-nav">
        <div>안녕 나는 상단바야</div>
        <div>{data}</div>
      </div>
    </div>
  )
}
```

React에서는 데이터를 가져올 때 `{}`를 사용합니다.

이곳에는 변수, 함수, 등등 여러가지를 넣을 수 있습니다.

또한 `className`이나 `src`, `id`에도 사용할 수 있습니다.


EX) `<div className={data}>안녕</div>`


## 만약 HTML에 스타일을 직접 넣고 싶다면 이렇게 하세요

---
```javascript
<div style={{ 스타일 어쩌고 저쩌고 }}>안녕</div>
```

ex)
```javascript
<div style={{ padding:3, fontSize: '30px' }}>안녕</div>
```

++ 내부에는 `-`를 쓰지 못합니다.


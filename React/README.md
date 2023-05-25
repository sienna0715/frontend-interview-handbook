# React
- [useEffect의 dependency array에 대해서 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#1-useeffect%EC%9D%98-dependency-array%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [리액트의 내부 작동 원리를 재조정 (Reconciliation) 개념과 함께 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [React의 state와 props는 각각 무엇인지 설명해주세요.](https://github.com/haizellatte/frontend-interview-handbook/tree/main/React#4-react%EC%9D%98-state%EC%99%80-props%EB%8A%94-%EA%B0%81%EA%B0%81-%EB%AC%B4%EC%97%87%EC%9D%B8%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [React 컴포넌트의 key 속성에 대해 설명하세요.](https://github.com/haizellatte/frontend-interview-handbook/tree/main/React#5-react-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98-key-%EC%86%8D%EC%84%B1%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [React를 사용하는 이유에 대해 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#6-react%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [React의 생명주기에 대해 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#6-react%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [useEffect와 useLayoutEffect의 차이에 대해 설명해주세요.]()
- [제어컴포넌트와 비제어 컴포넌트의 차이점에 대해 설명해주세요.]()

----

## 1. useEffect의 dependency array에 대해서 설명해주세요.
> The Effect Hook lets you perform side effects in function components

데이터 패칭, DOM을 직접적으로 변경하는 것 등은 리액트에서 모두 side effect 입니다. 때문에 원활한 렌더링을 위하여 이를 분리시켜줘야 하는데 그럴 때 사용할 수 있는 것이 useEffect 입니다. useEffect은 외부 세계와 상호 작용하면서 해당 컴포넌트의 렌더링이나 성능에는 영향을 미치지 않도록 만들어줍니다. 즉, 컴포넌트 내에서 side effect를 실행할 수 있도록 만들어 줍니다. <br/><br/>

> useEffect(callback, dependencyArray)

useEffect의 첫번째 인자는 콜백 함수를 받아 데이터 패칭과 같은 실행할 코드를 작성해줍니다. 두번째 인자로는 배열을 받는데 이를 **dependency array**라고 합니다. 
useEffect은 브라우저 렌더링이 모두 끝난 후, 즉 첫 렌더링이 일어난 후 실행되게 됩니다. 이때 dependency array(종속 배열)에 어떤 값을 주냐에 따라 실행의 빈도가 달라지게 됩니다. 빈 배열을 놓을 경우에는 첫 렌더링 이후 한 번만 실행되지만, 빈 배열이 아닌 state나 변수를 넣을 경우, 값이 변경될 때마다 이를 감지하여 useEffect이 실행되게 됩니다. 만약 두번째 인자에 아무 것도 설정하지 않을 경우, proprs가 변경될 때, state가 변경될 때마다 실행되기 때문에 무한 렌더링으로 이어지기 때문에 지양해야 합니다. 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 2. 리액트의 내부 작동 원리를 재조정 (Reconciliation) 개념과 함께 설명하세요.
리액트는 선언형(declarative)입니다. 이는 복잡한 과정을 추상화하여 결과에만 집중할 수 있게 만들어주며, 이 말은 곧 리액트 내부에서 어떤 일이 일어나고 있는지 명확히 눈에 보이지 않는다는 말이기도 합니다. 배열 고차 함수인 filter, map, reduce를 사용할 때를 생각해 보면 더 잘 와닿을 거라 생각합니다. 이러한 리액트의 특징은 Virtual DOM 덕분에 가능한 것인데 리액트는 실제 DOM에 직접 업데이트하지 않고 실제 DOM 객체를 복사하여 변경된 요소만 업데이트합니다. 이 때 복사된 DOM을 Virtual DOM(VDOM)이라 합니다. <br/><br/>
내부 동작을 다시 정리해보자면 상태가 변경될 때마다 새로운 가상 돔 트리를 만들고, diffing 알고리즘을 사용하여 실제 DOM 트리를 업데이트 합니다. 이때 실제 돔과 가상 돔이 일치하는지 안 하는지 비교하는 과정을 reconciliation(재조정)이라 합니다. 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 3. 리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.

Server-side Routing은 사용자가 새 페이지나 새 데이터에 접근할 때, 서버에서 이와 일치하는 응답(새로운 URL)을 사용자에게 제공해줍니다. 이는 새로운 전체 페이지를 렌더링한다는 의미이기도 합니다. 때문에 SSR은 페이지를 이동할 때마다 콘텐츠를 브라우저에 표시하기까지 시간이 걸립니다. 하지만 Client side routing은 SSR의 이러한 단점을 보완해줍니다. 클라이언트 단에서 즉, 서버가 아닌 자바스크립트 파일에서 처리되기 때문에 부분적으로 업데이트를 가능하게 합니다. 때문에 초기 로드 때, 데이터를 받아와서 다른 링크 간의 지연 시간이 적습니다. <br/><br/>
이러한 CSR 방식은 React Router에서도 강력하게 나타납니다. React Router는 동적으로 라우팅이 결정됩니다. 즉, 렌더링 될 때마다 경로가 업데이트 됩니다. 이는 브라우저가 완전히 새로운 문서를 요청하거나 재평가할 필요가 없기 때문에 더 빠른 사용자 경험을 가능하게 합니다. CSR는 SPA가 붐이 일어나면서 흥행을 했었습니다. 

```javascript
import React from "react";
import ReactDOM from 'react-dom';
import { BrowserRouter as Router, Route } from 'react-router-dom';

const HomePage = () => {
  return (
    <div>
      <h1>Welcome to the Home Page!</h1>
    </div>
  );
};
// Using match to dynamically generate which user is being passed
const User = ({ match }) => {
  return (
    <div>
      <h3>{match.params.userId}</h3>
    </div>
  );
};
ReactDOM.render((
  <Router>
    <Route path='/' render={HomePage} />
// the new path will be the user's id passed into the User component
    <Route path='/:userId' component={User} />
  </Router>),
  document.getElementById('root')
);
```

하지만 이러한 CSR에도 단점이 존재합니다. CSR은 초기 로드 시 전체 페이지를 로드해야 하기 때문에 홈페이지에 대한 초기 요청이 더 오래 걸릴 수도 있습니다. 때문에 SSR과 CSR의 특징을 잘 파악하여 애플리케이션에 알맞는 방식을 결정해야 합니다.


cf. [client-side routing](https://betterprogramming.pub/react-router-and-client-side-routing-2e483452fbfb) 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>


## 4. React의 state와 props는 각각 무엇인지 설명해주세요.
React에서 state와 props는 둘 다 컴포넌트에서 `데이터`를 다루는데 사용되지만, 목적과 사용 방법에서 차이점이 존재합니다.

<img src="https://velog.velcdn.com/images/haizel/post/3b8d0544-f29e-4c46-a1ff-fefc96fa3d12/image.png" width="400px" />


### State

state는 컴포넌트 내부에서 관리되는 변경 가능한 데이터입니다.  `setState()` 메소드 또는 클래스형 컴포넌트에서는 `this.state` 객체를 사용해 상태를 변경할 수 있습니다. 

state가 변경되면 render() 메소드를 트리거해 UI가 업데이트 됩니다. 따라서 컴포넌트에서 데 state를 사용해 데이터의 상태를 관리하기 위해 사용됩니다.

### Props

props는 ‘properties’의 준말로, 부모 컴포넌트에서 자식 컴포넌트로 전달되는 읽기 전용 데이터를 말합니다. 함수의 매개변수 또는 클래스형 컴포넌트의 `this.props` 객체를 통해 사용할 수 있습니다.

props는 읽기 전용 데이터이기 때문에 변경되지 않으며,부모 컴포넌트에서 props를 이용해 자식 자식 컴포넌트에 데이터를 전달할 때 사용합니다.

state와 마찬가지로 props도 변경되면 render() 메소드를 트리거해 UI가 업데이트 됩니다.

<br />

### 요약

---

React에서 state와 props는 둘 다 컴포넌트에서 데이터를 다루는데 사용되며 목적과 사용 방법에서 차이점이 존재합니다.

state는 `함수 내에서 선언된 변수`처럼 컴포넌트 **내부**에서 **변경 가능**한 데이터를 관리하고,

props는 `함수의 매개변수`처럼 **외부** 컴포넌트(부모 컴포넌트)에서 상속 받은 데이터로, 변경이 불가능한 **읽기 전용** 데이터를 전달하는데 사용된다는 차이가 있습니다.

<br />

#### 🙋‍♀️ Quiz1. `setState()` 호출은 동기적일까요? 비동기적일까요? <br />
#### 🙋‍♀️ Quiz2. `this.state.count`의 초기값이 0일때, 최종 `this.state.count` 은  몇일까요?
```jsx
incrementCount() {
  this.setState({count : this.state.count + 1 });
 }

handleSomething() {
 this.incrementCount();
 this.incrementCount();
 this.incrementCount();
}
```
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 5. React 컴포넌트의 key 속성에 대해 설명하세요.
React에서 `map` 등을 사용해 컴포넌트를 반복적으로 생성할 때,  `'Warning: Each child in a list should have a unique "key" prop.’` 와 같은 경고를 마주치게 됩니다.

<img src="https://velog.velcdn.com/images/haizel/post/62bf062f-6fbb-4af8-889e-c46e5d43ade6/image.png" width="700px" />

React 컴포넌트에서 왜 key 속성이 필요한지 React 렌더링 원리에 대해 알아보도록 하겠습니다. <br />

### Key 속성, 왜 필요한가

리액트는 컴포넌트의 상태나 속성(props)이 변할 때마다 `render()`함수를 호출합니다.

이때 `render()`함수는 새로운 리액트 요소 트리를 반환하고 이를 기존의 요소 트리와 비교해 새로운 변경점에 대해서만 제렌더링을 수행합니다.

여기서 기존 요소들 뒤에 새로운 내용을 추가할 경우 새로운 부분에 대해서만 재렌더링 되지만, 기존 요소 앞에 새로운 내용을 추가할 경우 모든 부분이 재렌더링됩니다. 바로 이런 상황을 최적화하기 위해 `key` 속성을 사용합니다.

각 요소에 `key` 속성을 부여하면 더 이상 모든 요소를 렌더링하지 않고, 추가된 부분만 제렌더링해 효율적인 렌더링을 실현할 수 있습니다. <br /><br />


### key 속성 사용시 주의할 점

`key`값은 변하지 않는 고유한 값을 설정하는 것이 권장됩니다. 다만 이때 인덱스를 `key`값으로 사용할 경우 문제가 발생할 수 있습니다.

예를 들어 순서가 변할 수 있는 상황에서 `key`값으로 고유한 값이 아닌 인덱스를 사용하면 `key`를 사용하지 않은 때와 같이 모든 형제 요소가 재렌더링됩니다. 이는 성능 저하와 예상치 못한 문제들을 발생시킬 수 있습니다,

또한 `Math.random()`으로 생성된 값과 같이 변하는 값을 key로 사용하면 컴포넌트와 인스턴스, DOM 노드를 블필요하게 재생성하게 되어 성능이 저하되고 자식 컴포넌트의 state가 유실될 수 있습니다.

따라서 해당 데이터가 갖는 id값이나 별도 고유 id 라이브러리 등을 사용해 언제나 요소의 `key`값이 고유하도록 보장해야 합니다.
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 6. React를 사용하는 이유에 대해 설명하세요.

react는 component와 Virtual DOM 때문에 사용합니다. 

component는 재사용이 가능한 각각의 독립적 모듈이라고 할 수 있습니다. react는 component를 조립하여 프로그램을 만듭니다. 그래서 재사용에 용이하며 재사용하기 때문에 코드의 불필요한 반복이 줄어 생산성이 좋아지며 재사용한 컴포넌트에 에러가 발생했을때 해당 컴포넌트의 에러만 해결하면 되기 때문에 유지보수에도 용이합니다.

기존에는 상태나 페이지가 바뀌면 전체를 렌더링했지만 react는 Virtual DOM을 이용하여 상태나 페이지가 바뀌었을 경우 바뀐 부분만 렌더링하게되어 불필요한 렌더링이 줄어듭니다.

react를 사용하는 이유는 재사용이 가능하고 그로인해 생산성과 유지보수가 용이하고 불필요한 렌더링을 줄일수 있기 때문입니다.
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 7. React의 생명주기에 대해 설명하세요.

react의 생명주기는 mount(생성) -> 업데이트 -> unmount(제거) 순으로 구성되어 있습니다. 각각의 생명주기에 특별한 메서드를 선언하여 코드를 작동할 수 있습니다.

### 마운트 생명주기 메서드

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdiVCbs%2Fbtsf4e2XfIX%2FbfQMhkBE8yXHknZg115hD1%2Fimg.png" width="500px" /></p>


#### Constructor

```javascript

  constructor(props) {
    super(props);
  }

```
- 컴포넌트의 생성자 메서드이며 컴포넌트가 만들어지면 가장 먼저 실행되는 메서드입니다.


#### getDerivedStateFromProps

```javascript

  static getDerivedStateFromProps(nextProps, prevState) {
    console.log("getDerivedStateFromProps");
    if (nextProps.color !== prevState.color) {
      return { color: nextProps.color };
    }
    return null;
  }
  
```
- props로 받아온 값을 state에 넣어주고 싶을 경우 사용합니다.
- 다른 생명주기 메서드와 다르게 static 키워드가 필요합니다.
- this로 조회할 수 없습니다.
- 특정 객체를 반환하면 객체 안의 내용들이 컴포넌트의 state로 설정됩니다. (null일 경우 아무일도 발생하지 않음)


#### render
- 컴포넌트를 렌더링하는 메서드입니다.


#### componentDidMount
- 컴포넌트의 첫번째 렌더링이 끝나면 호출되는 메서드입니다.
- 주로 DOM을 사용해야하는 외부 라이브러리를 연동하거나 데이터를 요청하기 위해 ajax 요청을 하거나 DOM의 속성을 읽거나 직접 변경하는 작업을 진행합니다.


### 업데이트 생명주기 메서드

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdd0Hkw%2Fbtsf6DBaKa6%2Fgljfcu6mKKQ1NzwsdRvL20%2Fimg.png" width="500px" /></p>


#### getDerivedStateFromProps
- 위의 다뤘던 내용과 같습니다.
- 컴포넌트의 state와 props가 바뀌었을때도 호출됩니다.


#### shouldComponentUpdate

```javascript

  shouldComponentUpdate(nextProps, nextState) {
    return true;
  }
  
```
- 컴포넌트가 리렌더링의 여부를 결정하는 메서드입니다.
- 주로 최적화 할 때 사용하는 메서드입니다.
- 반환 값이 true이면 리렌더링을 하며, false일 경우 리렌더링을 하지 않습니다.


#### getSnapshotBeforeUpdate

```javascript

  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log("getSnapshotBeforeUpdate");
    if (prevProps.color !== this.props.color) {
      return this.myRef.style.color;
    }
    return null;
  }
  
```
- 컴포넌트에서 변화가 일어나기 직전의 DOM상태를 가져와서 특정 값을 반환하면 그 값을 componentDidUpdate에서 사용할 수 있습니다.


#### componentDidUpdate


```javascript

  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log("componentDidUpdate", prevProps, prevState);
    if (snapshot) {
      console.log("업데이트 되기 직전 색상: ", snapshot);
    }
  }
  
```
- 리렌더링과 업데이트를 마치고 난 뒤에 호출되는 메서드입니다.
- getSnapshotBeforeUpdate에서 반환한 값을 3번째 인자로 받을 수 있습니다.
- 업데이트 전의 props와 이후의 props를 비교하는데 사용할 수 있습니다.


### 제거(언마운트) 생명주기 메서드

#### componentWillUnmount
- DOM에 직접 등록했었던 이벤트를 제거합니다.
- setTimeout을 사용했다면 clearTimeout으로 제거합니다.

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>


## 8. useEffect와 useLayoutEffect의 차이에 대해 설명해주세요.


>  💡 **필수 용어**
    > - **Render** : DOM Tree를 구성하기 위해 각 엘리먼트의 스타일 속성을 계산하는 과정
    > - **Paint** : 실제 스크린에 Layout을 표시하고 업데이트하는 과정

  <br />

### useEffect

---

useEffect은 컴포넌트들이 `render와 paint된 후에 실행`되며, **비동기적**입니다.

paint된 후에 실행되기 때문에, useEffect 내부에 DOM에 영향을 주는 코드가 있을 경우 화면 깜빡임 현상이 발생할 수 있습니다.

**useEffect의 Life cycle**

![](https://velog.velcdn.com/images/haizel/post/3f875b56-b2e5-4614-9baa-a0b2ce20b8bc/image.png)


<br />


### useLayoutEffect

---

useLayoutEffect은 컴포넌트들이 `render된 후에 실행되며, 그 후 paint`됩니다. 즉 `동기적`으로 실행됩니다.

paint가 되기 전에 실행되기 때문에 DOM을 조작하는 코드가 존재하더라도 사용자는 깜빡임을 경험하지 않습니다.

**useLayoutEffect의 Life cycle**

![](https://velog.velcdn.com/images/haizel/post/3648d4de-6a7a-48c7-b2a1-621ba4847df8/image.png)


<br />

## 언제 사용하는 것이 좋을까?

### useEffect

useLayoutEffect은 동기적으로 실행되어 내부 코드가 모두 실행된 후 painting 작업을 거칩니다. 따라서 로직이 복잡할 경우 사용자가 레이아웃을 보는데까지 시간이 오래 걸린다는 단점이 있어 보통의 경우 useEffect의 사용이 권장됩니다. 대표적으로 `데이터 fetch`, `event handler`, `state reset` 의 경우 useEffect을 많이 사용합니다.

### useLayoutEffect

화면이 깜빡 거리는 상황일 때 유용합니다.

예를 들어 아래와 같이 state가 있고, 조건에 따라 첫 painting 시 다르게 렌더링 되어야 할때, useEffect은 처음에 0이 보여지고 re-rendering 되면서 화면 깜빡임 현상이 발생하지만, useLayoutEffect은 코드가 모두 실행된 후 painting 되기 때문에 화면 깜빡임 현상이 발생하지 않습니다.

```jsx
const Test = (): JSX.Element => {
  const [value, setValue] = useState(0);

  useLayoutEffect(() => {
    if (value === 0) {
      setValue(10 + Math.random() * 200);
    }
  }, [value]);

  console.log('render', value);

  return (
    <button onClick={() => setValue(0)}>
      value: {value}
    </button>
  );
};
```

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>



## 9. 제어컴포넌트와 비제어 컴포넌트의 차이점에 대해 설명해주세요.

## 1. 제어 컴포넌트

React에 의해 값이 제어되는 컴포넌트를 제어 컴포넌트라고 합니다. 보통  `form` 이나 `input` 등의 입력 요소 태그를 다룰 때, 요소에 입력되는 값을 state로 관리하거나 DOM API를 통해서 관리할 수 있습니다. 이때 state로 DOM 요소의 값을 다루는 컴포넌트가 바로 제어 컴포넌트입니다.

### 예제 코드

아래 코드는 `input`  의 값이 바뀔 때마다 ChangeName 함수를 통해 state의 값을 업데이트해주는 제어 컴포넌트입니다.

```jsx
import React, { useState } from "React";

function Control() {
	const [name, setName] = useState(null);

	const ChangeName = (e) => {
		setName(e.current.value);
	}

	return (
		<input onChange={ChangeName} value={name} />
	 )
}
```

제어 컴포넌트는 사용자의 입력을 기반으로 **state**를 관리하고 update합니다. 이처럼 제어 컴포넌트는 React에 의해 값이 제어되는 입력, 폼 요소에서 사용됩니다.

<br />

### 문제점

제어 컴포넌트는 입력할 때마다 렌더링 하기 때문에, 불필요하게 리렌더링되거나 API를 호출할 수 있습니다. 즉 사용자가 입력하는 모든 데이터가 동기화됩니다.
이 문제를 해결하기 위해서 쓰로틀링(Throttling)과 디바운싱(Debouncing)을 활용할 수 있습니다.

>
- **쓰로틀링(Throttling)** : 마지막 함수가 호출된 후 일정시간이 지나기 전에 다시 호출되지 않도록 하는 것
- **디바운싱(Debouncing)** : 연이어 호출되는 함수들 중 마지막(혹은 맨 처음) 함수만 호출하도록 하는 것
>
[📎  참고자료 - 쓰로틀링과 디바운싱](https://www.zerocho.com/category/JavaScript/post/59a8e9cb15ac0000182794fa)
  
  <br />

### 언제 사용할까?

1. 유효성 검사
2. 실시간으로 필드 검사를 해야하는 경우
3. 조건에 따라 버튼의 활성화 여부가 바뀌는 경우

<br />

## 2. 비제어 컴포넌트

React에 의해 값이 제어되지 않은 컴포넌트를 비제어 컴포넌트라고 합니다. 제어 컴포넌트에서 폼 데이터는 React 컴포넌트에서 다뤄지는 반면, 비제어 컴포넌트는 **DOM 자체**에서 폼 데이터가 다뤄집니다.

따라서 모든 state 업데이트에 대한 이벤트 핸들러를 작성하는 대신 **ref**를 사용해 DOM에서 폼 값을 가져올 수 있습니다. 

### 예제 코드

아래 코드는 ref를 통해 input 값에 접근 할 수 있고, 이벤트 핸들러를 통해 ref에 저장된 요소의 값을 가져와 활용하는 비제어 컴포넌트입니다.

```jsx
import React, { useRef } from "React";

function UnControl() {
	const nameRef = useRef(null);
	
	return (
		<input ref={nameRef} />
	)
}
```

비제어 컴포넌트는 state로 값을 관리하지 않기 때문에 값이 바뀔 때마다 리렌더링, API 호출을 하지 않아 성능상 이점이 있습니다. 즉 비제어 컴포넌트는 사용자가 직접 트리거 하지 전까지는 리렌더링을 발생시키지 않고 값을 동기화 시키지도 않습니다.
대표적 예로 submit 버튼을 클릭하면 함수 내에서 ref를 통해 form 내 value들에 접근합니다.

<br />

### 언제 사용할까?

일반적으로 모든 form 요소의 동기화가 필요하지 않고, form 요소가 증가할수록 면 모든 컴포넌트에 쓰로틀링이나 디바운싱을 걸기엔 어려움이 있습니다. 따라서 만약 값이 트리거 된 이후에 값이 갱신되어도 된다면, 비제어 컴포넌트를 통해 불필요한 렌더링을 방지하고 성능 향상을 할 수 있습니다.

대표적으로 비제어 컴포넌트를 사용해 렌더링을 최적화하는 라이브러리로 `react-hook-form`이 있습니다.

<br />

## 3. 제어 컴포넌트 vs 비제어 컴포넌트

---

### 차이점

|  | 제어 컴포넌트 | 비제어 컴포넌트 |
| --- | --- | --- |
| **1. 동기화**| 항상 동기화(제어 컴포넌트의 값은 **항상 최신값을 유지**) | 동기화 X |
| **2. 폼 데이터** | React 컴포넌트 | DOM 자체 |

✔️ React 공식 문서에 따르면 대부분의 경우 폼 구현 시 제어 컴포넌트를 사용하는 것을 권장

<br />

### 언제 무엇을 사용해야 할까?

| 기능 | 제어 컴포넌트 | 비제어 컴포넌트 |
| --- | --- | --- |
| 일회성 정보 검색 (ex. 제출) | ✅ | ✅ |
| 제출 시 값 검증 | ✅ | ✅ |
| 실시간으로 필드값의 유효성 검사 | ✅ | ❌ |
| 조건부로 제출 버튼 비활성화(disabled) | ✅ | ❌ |
| 실시간으로 입력 형식 적용하기(ex. 숫자만 가능하게 등) | ✅ | ❌ |
| 동적 입력 | ✅ | ❌ |
- 즉각적, 실시간으로 값에 대한 피드백이 필요하다 → 제어 컴포넌트
- 즉각적인 피드백이 불필요하고 제출시에만 값이 필요하다 혹은 불필요한 렌더링과 값 동기화가 싫다 → 비제어 컴포넌트


<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>
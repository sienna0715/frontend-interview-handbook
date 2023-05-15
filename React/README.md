# React
- [useEffect의 dependency array에 대해서 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#1-useeffect%EC%9D%98-dependency-array%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [리액트의 내부 작동 원리를 재조정 (Reconciliation) 개념과 함께 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [React의 state와 props는 각각 무엇인지 설명해주세요.](https://github.com/haizellatte/frontend-interview-handbook/tree/main/React#4-react%EC%9D%98-state%EC%99%80-props%EB%8A%94-%EA%B0%81%EA%B0%81-%EB%AC%B4%EC%97%87%EC%9D%B8%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [React 컴포넌트의 key 속성에 대해 설명하세요.](https://github.com/haizellatte/frontend-interview-handbook/tree/main/React#5-react-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98-key-%EC%86%8D%EC%84%B1%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
----

### 1. useEffect의 dependency array에 대해서 설명해주세요.
> The Effect Hook lets you perform side effects in function components

데이터 패칭, DOM을 직접적으로 변경하는 것 등은 리액트에서 모두 side effect 입니다. 때문에 원활한 렌더링을 위하여 이를 분리시켜줘야 하는데 그럴 때 사용할 수 있는 것이 useEffect 입니다. useEffect은 외부 세계와 상호 작용하면서 해당 컴포넌트의 렌더링이나 성능에는 영향을 미치지 않도록 만들어줍니다. 즉, 컴포넌트 내에서 side effect를 실행할 수 있도록 만들어 줍니다. <br/><br/>

> useEffect(callback, dependencyArray)

useEffect의 첫번째 인자는 콜백 함수를 받아 데이터 패칭과 같은 실행할 코드를 작성해줍니다. 두번째 인자로는 배열을 받는데 이를 **dependency array**라고 합니다. 
useEffect은 브라우저 렌더링이 모두 끝난 후, 즉 첫 렌더링이 일어난 후 실행되게 됩니다. 이때 dependency array(종속 배열)에 어떤 값을 주냐에 따라 실행의 빈도가 달라지게 됩니다. 빈 배열을 놓을 경우에는 첫 렌더링 이후 한 번만 실행되지만, 빈 배열이 아닌 state나 변수를 넣을 경우, 값이 변경될 때마다 이를 감지하여 useEffect이 실행되게 됩니다. 만약 두번째 인자에 아무 것도 설정하지 않을 경우, proprs가 변경될 때, state가 변경될 때마다 실행되기 때문에 무한 렌더링으로 이어지기 때문에 지양해야 합니다. 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>
### 2. 리액트의 내부 작동 원리를 재조정 (Reconciliation) 개념과 함께 설명하세요.
리액트는 선언형(declarative)입니다. 이는 복잡한 과정을 추상화하여 결과에만 집중할 수 있게 만들어주며, 이 말은 곧 리액트 내부에서 어떤 일이 일어나고 있는지 명확히 눈에 보이지 않는다는 말이기도 합니다. 배열 고차 함수인 filter, map, reduce를 사용할 때를 생각해 보면 더 잘 와닿을 거라 생각합니다. 이러한 리액트의 특징은 Virtual DOM 덕분에 가능한 것인데 리액트는 실제 DOM에 직접 업데이트하지 않고 실제 DOM 객체를 복사하여 변경된 요소만 업데이트합니다. 이 때 복사된 DOM을 Virtual DOM(VDOM)이라 합니다. <br/><br/>
내부 동작을 다시 정리해보자면 상태가 변경될 때마다 새로운 가상 돔 트리를 만들고, diffing 알고리즘을 사용하여 실제 DOM 트리를 업데이트 합니다. 이때 실제 돔과 가상 돔이 일치하는지 안 하는지 비교하는 과정을 reconciliation(재조정)이라 합니다. 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>
### 3. 리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.

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


### 4. React의 state와 props는 각각 무엇인지 설명해주세요.
React에서 state와 props는 둘 다 컴포넌트에서 `데이터`를 다루는데 사용되지만, 목적과 사용 방법에서 차이점이 존재합니다.

<img src="https://velog.velcdn.com/images/haizel/post/3b8d0544-f29e-4c46-a1ff-fefc96fa3d12/image.png" width="500px" />


### State

state는 컴포넌트 내부에서 관리되는 변경 가능한 데이터입니다.  `setState()` 메소드 또는 클래스형 컴포넌트에서는 `this.state` 객체를 사용해 상태를 변경할 수 있습니다. 

state가 변경되면 render() 메소드를 트리거해 UI가 업데이트 됩니다. 따라서 컴포넌트에서 데 state를 사용해 데이터의 상태를 관리하기 위해 사용됩니다.

### Props

props는 ‘properties’의 준말로, 부모 컴포넌트에서 자식 컴포넌트로 전달되는 읽기 전용 데이터를 말합니다. 함수의 매개변수 또는 클래스형 컴포넌트의 `this.props` 객체를 통해 사용할 수 있습니다.

props는 읽기 전용 데이터이기 때문에 변경되지 않으며,부모 컴포넌트에서 props를 이용해 자식 자식 컴포넌트에 데이터를 전달할 때 사용합니다.

state와 마찬가지로 props도 변경되면 render() 메소드를 트리거해 UI가 업데이트 됩니다.

<br />

### 한줄 정리

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

<img src="https://velog.velcdn.com/images/haizel/post/62bf062f-6fbb-4af8-889e-c46e5d43ade6/image.png" width="800px" />

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

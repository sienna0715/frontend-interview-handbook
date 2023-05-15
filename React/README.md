# React
- [useEffect의 dependency array에 대해서 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#1-useeffect%EC%9D%98-dependency-array%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [리액트의 내부 작동 원리를 재조정 (Reconciliation) 개념과 함께 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#2-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%9E%91%EB%8F%99-%EC%9B%90%EB%A6%AC%EB%A5%BC-%EC%9E%AC%EC%A1%B0%EC%A0%95-reconciliation-%EA%B0%9C%EB%85%90%EA%B3%BC-%ED%95%A8%EA%BB%98-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
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
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>
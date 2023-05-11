# JavaScript
- [Function.prototype.bind에 대해 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#1-functionprototypebind%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [this가 JavaScript에서 어떻게 작동하는지 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#2-this%EA%B0%80-javascript%EC%97%90%EC%84%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [이벤트 루프란 무엇인가요? 콜 스택과 태스크 큐의 차이점은 무엇인가요?](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#3-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94-%EC%BD%9C-%EC%8A%A4%ED%83%9D%EA%B3%BC-%ED%83%9C%EC%8A%A4%ED%81%AC-%ED%81%90%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)
- [프로토타입 상속이 어떻게 작동하는지 설명하세요.]()
------

### 1. Function.prototype.bind에 대해 설명하세요.
> bind() 메소드가 호출되면 새로운 함수를 생성합니다. 받게되는 첫 인자의 value로는 this 키워드를 설정하고, 이어지는 인자들은 바인드 된 함수의 인수에 제공됩니다. 
from. MDN

자바스크립트의 this는 다른 언어들과 다르게 호출될 때 바인딩 될 객체가 동적으로 결정됩니다. 이는 외부 함수와 중첩 함수/콜백 함수 내부의 메소드가 일치하지 않는 문제를 야기시키게 됩니다. 이때 Function.prototype.bind를 이용하여 해결할 수 있습니다.

```javascript
const person = {
	name: 'Lee',
  	foo(callback) {
    	setTimeout(callback.bind(this), 100);
    }
};

person.foo(function () {
	console.log(`Hi! my name is ${this.name}.`); // Hi! my name is Lee.
})
```
함수 호출없이 첫 번째 인수로 전달한 값으로, this와의 바인딩이 교체된 함수로 새롭게 만들어지기 때문에 콜백 함수 내부의 this와 외부 함수 내부의 this가 일치하는 결과를 얻을 수 있습니다. 이처럼 Function.prototype.bind는 주로 메서드의 this와 메서드 내부 중첩 함수 또는 콜백 함수의 this가 불일치하는 문제를 해결할 때 사용됩니다.
bind는 Function.prototype의 메소드이기 때문에 모든 함수가 상속받아 사용할 수 있습니다.

**▶︎ bind를 안 쓰고 this를 사용할 경우**
```javascript
const person = {
	name: 'Lee',
  	foo(callback) {
    	setTimeout(callback, 100);
    }
};

person.foo(function () {
	console.log(`Hi! my name is ${this.name}.`); // Hi! my name is .
})
```
person.foo()는 일반 함수로서 호출되면서 this는 전역 객체 window를 가리키게 됩니다. 때문에 'Lee'가 아닌 빌트인 메소드 window.name를 뜻하게 되어 name 프로퍼티의 기본값인 빈 문자열('')로 출력되게 됩니다. 
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#javascript)
<br/><br/>

### 2. this가 JavaScript에서 어떻게 작동하는지 설명하세요.
생성자 함수로 메서드를 호출할 때, 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 특수한 식별자가 필요했고 이에 자바스크립트는 this라는 특수한 식별자를 제공하였습니다. 하지만 인스턴스만을 가리키는 다른 언어들과는 다르게 자바스크립트의 this는 호출 시점에 바인딩 될 객체가 동적으로 결정됩니다.

일반 함수로 호출할 경우, this는 전역 객체 window를 가리킵니다.
생성자 함수로 호출할 경우, 인스턴스를 가리킵니다.
이처럼 일반함수로 호출할 경우에는 전역 객체를 가리키다보니 this가 불일치하는 경우가 생겨 개발자가 의도한 바와 다른 경우를 초래할 수 있기 때문에 주의를 기울어야 합니다.
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#javascript)
<br/><br/>

### 3. 이벤트 루프란 무엇인가요? 콜 스택과 태스크 큐의 차이점은 무엇인가요?
자바스크립트는 싱글 스레드로 동작한다. 이는 한 번에 하나의 태스크만 처리할 수 있음을 의미합니다. 하지만 우리가 개발을 하다보면 마치 동시에 작업이 되는 것처럼 느껴질 때가 있습니다. 이것이 바로 '이벤트 루프'의 역할입니다.
이벤트 루프는 브라우저에 내장되어 있는 기능으로 콜 스택에 현재 실행 중인 코드가 있는지. 태스크 큐에 대기중인 함수가 있는지를 반복적으로 확인하여 콜 스택이 비었다면 대기중인 함수를 이동시켜 비동기적으로 처리하게 됩니다. 때문에 이벤트 루프는 자바스크립트의 동시성을 지원하게 됩니다.

이벤트 루프에서 언급한 태스트 큐는 비동기 함수를 일시적으로 보관하는 영역입니다.
콜 스택은 자바스크립트의 엔진 중 하나로 함수가 호출되면 순차적으로 쌓인 후, 순차적으로 실행됩니다. 이때문에 자바스크립트를 싱글 스레드라고 하는 이유이기도 합니다.

이야기를 종합해보면 콜 스택과 태스크 큐의 가장 큰 차이점은 데이터를 처리하는 방식입니다. 앞서 이벤트 루프에서 설명한 바를 생각해보면 결국 코드가 실행되는 곳은 자바스트립트 엔진, 즉 콜 스택입니다. setTimeout과 같은 비동기 함수를 태스크 큐에 모아두었다가 콜 스택에서 동기적으로 평가하고 실행되게 됩니다.
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#javascript)
<br/><br/>

### 4. 프로토타입 상속이 어떻게 작동하는지 설명하세요.
> 자바스크립트는 프로토타입 기반의 객체지향 프로그래밍 언어이다.

#### <u>상속(inheritance)</u>
객체지향 프로그래밍의 핵심 개념으로, 어떤 객체의 프로퍼티 또는 메소드를 다른 객체가 받아와서 그대로 사용할 수 있는 것을 의미합니다. 때문에 상속은 코드 재사용이라는 관점에서 매우 유용하며, 이를 이용하면 불필요한 중복을 제거하기 떼문에 개발 비용을 줄일 수 있습니다.
<br/><br/>

#### <u>프로토타입이란?</u>
객체지향 프로그래밍에서 핵심이라 할 수 있는 **객체 간 상속을 구현하기 위해** 사용됩니다.
어떤 객체의 상위(부모) 객체의 역할을 하는 객체로서 상속받은 하위(자식)) 객체는 상위 객체의 프로퍼티를 자신의 프로퍼티처럼 사용할 수 있게 됩니다. 모든 객체는 [[Prototype]]이라는 내부 슬롯을 가지며, 내부 슬롯에 저장되는 프로토타입은 객체가 생성될 때 객체 생성 방식에 따라 결정됩니다. 즉, 모든 객체는 하나의 프로토타입을 갖습니다.

<br/>

#### <u>프로토타입 체인이란?</u>
[[Prototype]] 내부 슬롯의 값(=프로토타입)에 접근할 때는 접근자 프로퍼티( \_\_proto__ )를 사용하게 되는데, **\_\_proto__는 객체가 직접 소유한 프로퍼티가 아닌 Object.prototype의 프로퍼티 입니다. \_\_proto__가 가리키는 참조에 따라 자신의 부모 역할을 하는 프로토타입의 프로퍼티를 순차적으로 검색할 수 있습니다.** 즉, 모든 객체는 프로토타입의 계층 구조인 프로토타입 체인에 묶여 있으며, 프로토타입 체인의 최상위 객체(종점)인 Object.prototype의 프로퍼티와 메서드는 모든 객체가 상속할 수 있다는 의미이기도 합니다. <br/>

프로토타입 체인은 단방향 링크드 리스트로 구현되어야 하기 때문에 접근자 프로퍼티( \_\_proto__ )를 사용하면 서로를 참조하는 양방향 프로토타입 체인이 생성되는 것을 방지할 수도 있습니다.<br/><br/>

**이야기를 종합해보자면 '자바스크립트는 프로토타입 객체지향 언어이며, 상속과 프로퍼티 검색 매커니즘을 구현할 수 있는 이유는 모든 객체가 프로토타입 체인에 묶여 있기 때문이다.'라고 정의할 수 있겠습니다.**
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#javascript)
<br/><br/>
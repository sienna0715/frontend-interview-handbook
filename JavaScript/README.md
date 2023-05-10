# JavaScript
- [Function.prototype.bind에 대해 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#1-functionprototypebind%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [this가 JavaScript에서 어떻게 작동하는지 설명하세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#2-this%EA%B0%80-javascript%EC%97%90%EC%84%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94)
- [이벤트 루프란 무엇인가요? 콜 스택과 태스크 큐의 차이점은 무엇인가요?](https://github.com/sienna0715/frontend-interview-handbook/blob/main/JavaScript/README.md#3-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94-%EC%BD%9C-%EC%8A%A4%ED%83%9D%EA%B3%BC-%ED%83%9C%EC%8A%A4%ED%81%AC-%ED%81%90%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)
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

### 2. this가 JavaScript에서 어떻게 작동하는지 설명하세요.
생성자 함수로 메서드를 호출할 때, 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 특수한 식별자가 필요했고 이에 자바스크립트는 this라는 특수한 식별자를 제공하였습니다. 하지만 인스턴스만을 가리키는 다른 언어들과는 다르게 자바스크립트의 this는 호출 시점에 바인딩 될 객체가 동적으로 결정됩니다.

일반 함수로 호출할 경우, this는 전역 객체 window를 가리킵니다.
생성자 함수로 호출할 경우, 인스턴스를 가리킵니다.
이처럼 일반함수로 호출할 경우에는 전역 객체를 가리키다보니 this가 불일치하는 경우가 생겨 개발자가 의도한 바와 다른 경우를 초래할 수 있기 때문에 주의를 기울어야 합니다.

<br/><br/>

### 3. 이벤트 루프란 무엇인가요? 콜 스택과 태스크 큐의 차이점은 무엇인가요?
자바스크립트는 싱글 스레드로 동작한다. 이는 한 번에 하나의 태스크만 처리할 수 있음을 의미합니다. 하지만 우리가 개발을 하다보면 마치 동시에 작업이 되는 것처럼 느껴질 때가 있습니다. 이것이 바로 '이벤트 루프'의 역할입니다.
이벤트 루프는 브라우저에 내장되어 있는 기능으로 콜 스택에 현재 실행 중인 코드가 있는지. 태스크 큐에 대기중인 함수가 있는지를 반복적으로 확인하여 콜 스택이 비었다면 대기중인 함수를 이동시켜 비동기적으로 처리하게 됩니다. 때문에 이벤트 루프는 자바스크립트의 동시성을 지원하게 됩니다.

이벤트 루프에서 언급한 태스트 큐는 비동기 함수를 일시적으로 보관하는 영역입니다.
콜 스택은 자바스크립트의 엔진 중 하나로 함수가 호출되면 순차적으로 쌓인 후, 순차적으로 실행됩니다. 이때문에 자바스크립트를 싱글 스레드라고 하는 이유이기도 합니다.

이야기를 종합해보면 콜 스택과 태스크 큐의 가장 큰 차이점은 데이터를 처리하는 방식입니다. 앞서 이벤트 루프에서 설명한 바를 생각해보면 결국 코드가 실행되는 곳은 자바스트립트 엔진, 즉 콜 스택입니다. setTimeout과 같은 비동기 함수를 태스크 큐에 모아두었다가 콜 스택에서 동기적으로 평가하고 실행되게 됩니다.

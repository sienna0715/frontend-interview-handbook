# FrontEnd
- [RESTful API에 대해 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#1-restful-api%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [객체 지향 프로그래밍이란 무엇인가요?](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#1-restful-api%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)


---

## 1. RESTful API에 대해 설명해주세요.

### 1️⃣ REST란
우선 RESTful API의 REST는 “Representational State Transfer”의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미합니다. 
즉, HTTP URI를 통해 자원(Resource)을 명시하고, HTTP Method를 통해 해당 URI에 대한 CRUD Operation을 적용하는 것입니다.

> **CRUD Operation란?**  <br/>
Create, Read, Update, Delete를 통틀어 일컫는 말이다. <br/><br/>
Create: 데이터 생성(POST) <br/>
Read: 데이터 조회(GET)  <br/>
Update: 데이터 수정(PUT, PATCH)  <br/>
Delete: 데이터 삭제(DELETE)

<br/>

### 2️⃣ REST API란
 방금 설명한 REST의 원리를 따르는 API를 말하는 것으로 REST API의 설계 규칙을 올바르게 지킨 시스템을 "**RESTful하다**"라고 합니다.

 그럼 어떤 규칙을 지켜야 하는지 알아보도록 하겠습니다. <br/><br/>

1. URI는 동사보다는 명사를, 대문자보다는 소문자를 사용하여야 한다.
> Bad Example http://khj93.com/Running/ <br/>
Good Example  http://khj93.com/run/  

2. 마지막에 슬래시(/)를 포함하지 않는다.
> Bad Example http://khj93.com/test/  <br/>
Good Example  http://khj93.com/test

3. 언더바 대신 하이폰을 사용한다.
> Bad Example http://khj93.com/test_blog <br/>
Good Example  http://khj93.com/test-blog  

4. 파일확장자는 URI에 포함하지 않는다.
>  Bad Example http://khj93.com/photo.jpg  <br/>
Good Example  http://khj93.com/photo  

5. URI에 행위(HTTP Method)나 동사 표현이 들어가면 안 된다.
> Bad Example http://khj93.com/members/delete/1  <br/>
> Bad Example http://khj93.com/members/show/1  <br/>
Good Example  http://khj93.com/members/1  

<br/>
이렇듯 REST API는 각 요청이 어떤 동작이나 정보를 위한 것인지를 그 요청의 모습 자체로 추론이 가능하다는 것 입니다.
<br/><br/>

cf. [RESTful API란 무엇입니까?](https://aws.amazon.com/ko/what-is/restful-api/)
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>


## 2. 객체 지향 프로그래밍(OOP)란 무엇인가요?
"Object Oriented Programming"의 약자로 객체 개념에 기반한 프로그래밍 패러다임의 일종으로, 프로그래밍에서 필요한 데이터를 추상화 시켜 상태와 행위를 가진 객체로 만들고, 객체들 간의 상호작용을 통해 로직을 구성하는 프로그래밍 방법을 말합니다.
<br/><br/>

그럼 객체 지향 프로그래밍의 핵심 4가지에 대해 얘기해보도록 하겠습니다.

### Encapsulation (캡슐화) 
연관 있는 데이터와 함수를 오브젝트에 담아두고, 외부에서 보일 필요가 없는 데이터를 캡슐화하는 것을 맓합니다.
- 데이터 구조와 데이터를 다루는 방법들을 결합 시켜 묶는 것 (변수와 함수를 하나로 묶는 것을 뜻함)
- 낮은 결합도를 유지할 수 있도록 설계하는 것

어떤 데이터를 묶을 것인지, 어떤 데이터를 외부에 보여줄 건지 혹은 볼 수 없는지를 만들어내는 것이 OOP의 첫걸음입니다.
<br/><br/>

### Abstraction (추상화)
내부의 복잡한 기능을, 외부에서 어떤 형태로, 공통적으로 어떻게 이 클래스를 이용하게 할 것인가를 고민하는 것을 추상화라고 합니다.
- 객체에서 공통된 속성과 행위를 추출 하는 것
- 공통의 속성과 행위를 찾아서 타입을 정의하는 과정
- 추상화는 불필요한 정보는 숨기고 중요한 정보만을 표현함으로써 프로그램을 간단하게 만드는 것
<br/><br/>

### Inheritance (상속) 
정의해둔 클래스의 속성과 행위를 하위 클래스에 물려주거나 하위 클래스가 상위 클래스의 속성과 행위를 물려받는 것을 말합니다. 즉, 재사용할 수 있게 해줍니다.

- 새로운 클래스가 기존의 클래스의 데이터와 연산을 이용할 수 있게 하는 기능
<br/><br/>

### Polymorphism (다형성)
poly = many, morphi = form이라 하여 해석하면, '다양한 형태'를 의미하듯, 다형성은 공통된 함수(클래스)로 만들어진 객체(인스턴스)에 접근할 수 있습니다. 클래스 내부에 같은 이름의 행위를 여러개 정의하거나 상위 클래스의 행위를 하위 클래스에서 재정의하여 사용할 수 있기 때문에 다형성이라는 특징을 갖게 됩니다.

- 하나의 변수명, 함수명이 상황에 따라 다른 의미로 해석 될 수 있는 것
- 어떠한 요소에 여러 개념을 넣어 놓는 것

<br/><br/>
이런 특징 때문에 객체 지향 프로그래밍은 클래스 단위로 모듈화하여 업무 분담이 편리하고 이 때문에 대규모 소프트웨어 개발에 적합합니다. 또한 "객체"라는 특징을 통해 데이터 코드 별로 묶을 수 있어 해당 객체만 이해한다면 수정이 가능하기 때문에 유지보수성이 좋고 상속을 통해 확장하기 좋으며 재사용 측면에서도 좋습니다. <br/> 그러나 객체 수에 따라 용량이 커진다는 단점이 있습니다.

<br/>
객체지향 프로그래밍을 지원하는 언어로는 C++ , C# , Java , Python , JavaScript , Ruby , Swift 등이 있습니다. 
<br/><br/>

cf. [객체지향 프로그래밍이란?](https://jongminfire.dev/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%9D%B4%EB%9E%80)
<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>
# FrontEnd
- [RESTful API에 대해 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#1-restful-api%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [객체 지향 프로그래밍이란 무엇인가요?](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#1-restful-api%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [프로세스와 스레드는 각자 무엇이며, 어떤 차이가 있나요?](https://github.com/sienna0715/frontend-interview-handbook/tree/main/FrontEnd#3-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C%EB%8A%94-%EA%B0%81%EC%9E%90-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%96%B4%EB%96%A4-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EC%9E%88%EB%82%98%EC%9A%94)
- [자바스크립트는 싱글 스레드 언어로 알려져있는데, 싱글 스레드와 멀티 스레드의 차이점은 무엇이며, 각 장단점은 무엇인지 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/tree/main/FrontEnd#4-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%8B%B1%EA%B8%80-%EC%8A%A4%EB%A0%88%EB%93%9C-%EC%96%B8%EC%96%B4%EB%A1%9C-%EC%95%8C%EB%A0%A4%EC%A0%B8%EC%9E%88%EB%8A%94%EB%8D%B0-%EC%8B%B1%EA%B8%80-%EC%8A%A4%EB%A0%88%EB%93%9C%EC%99%80-%EB%A9%80%ED%8B%B0-%EC%8A%A4%EB%A0%88%EB%93%9C%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EA%B0%81-%EC%9E%A5%EB%8B%A8%EC%A0%90%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)
- [브라우저의 렌더링 과정에 대하여 설명해 주세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#5-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EB%A0%8C%EB%8D%94%EB%A7%81-%EA%B3%BC%EC%A0%95%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC-%EC%84%A4%EB%AA%85%ED%95%B4-%EC%A3%BC%EC%84%B8%EC%9A%94)
- [주소창에 google.com을 입력하면 일어나는 일을 설명해주세요.](https://github.com/sienna0715/frontend-interview-handbook/blob/main/FrontEnd/README.md#6-%EC%A3%BC%EC%86%8C%EC%B0%BD%EC%97%90-googlecom%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EB%A9%B4-%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94-%EC%9D%BC%EC%9D%84-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)

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

#### ‼️ REST API 중심 규칙
1. URI는 정보의 자원을 표현해야 한다.
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)로 표현
> DELETE /members/1


#### ‼️ URI 설계 시 주의할 점
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

## 3. 프로세스와 스레드는 각자 무엇이며, 어떤 차이가 있나요?

### ✍️ 프로세스와 스레드, 한줄 정리

| 프로그램(Program) | 프로세스 (Process) | 스레드 (Thread) |
| --- | --- | --- |
| 어떤 작업을 하기 위해 실행할 수 있는 파일 | 운영체제로부터 자원을 할당받은 작업의 단위 | 프로세스가 할당받은 자원을 이용하는 실행 흐름의 단위 |


### 🖥️ 프로그램(Progam)

- `어떤 작업을 위해 실행할 수 있는 파일`로, 작성한 코드를 빌드하여 생성되는 결과물을 의미합니다.
- 프로그램은 파일이 저장 장치에 있지만 메모리에는 올라가 있지 않은 정적인 상태입니다.
- 따라서 프로그램을 실행하기 위해서는 Memory 자원을 할당 받아야 하는테, 이때 자원을 할당받아 실행되는 프로그램을 프로세스라고 합니다.


### 🖥️ 프로세스 (Process)
<img src="https://velog.velcdn.com/images/haizel/post/c06605bc-afe8-4309-b5f8-722cda7303ea/image.png" width="500" />

- `컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램` 으로, 메모리에 올라와 실행되고 있는 프로그램의 인스턴스(독립적인 개체)를 말합니다.
- 즉 운영체제로부터 시스템 자원을 할당받은 작업의 단위로, 동적인 개념으로는 `실행된 프로그램`을 의미합니다.


#### 특징
<img src="https://velog.velcdn.com/images/haizel/post/a8878d85-c701-4148-b6d8-33a9d2738371/image.png" width="500" />

1. 프로세스는 각각 독립된 메모리 영역 (Code, Data, Stack, Heap의 구조)를 할당 받습니다.
2. 기본적으로 프로세스당 최소 1개의 스레드(메인 스레드)를 가지고 있습니다.
3. 각 프로세스는 별도의 주소 공간에서 실행되며, 한 프로세스는 다른 프로세스의 변수나 자료 구조에 접근할 수 없습니다.
4. 한 프로세스가 다른 프로세스 자원에 접근하려면 프로세스 간의 통신(IPC, Inter-Process-Communication)을 사용해야 합니다.
    - e.g. 파이프, 파일, 소켓 등을 이용한 통신 방법
    
<br />

### 🖥️ 스레드(Thread)

- `프로세스 내에서 실행되는 여러 흐름의 단위`로, **프로세스의 특정한 수행 경로**를 말합니다.
- 즉 프로세스가 할당받은 자원을 이용한 실행의 단위입니다.

<br />

쉽게 설명하자면, 크롬 브라우저를 실행하면 하나의 프로세스가 생성됩니다.
이때 브라우저에서 파일을 다운 받고 노래를 들으며 온라인 쇼핑을 한다면 각 작업마다 스레드가 형성됩니다. 즉, 하나의 프로세스 안에서 여러 작업의 흐름이 동시에 진행되기 때문에 가능한 일입니다. 

<img src="https://velog.velcdn.com/images/haizel/post/0a64869f-615b-4f99-b4ca-6d797cd53d38/image.png" width="700" />

여기서 각 일련의 작업 흐름들을 **스레드**라고 하며, 스레드가 여러 개라면 **멀티(다중) 스레드**라고 합니다. 


#### 특징
<img src="https://velog.velcdn.com/images/haizel/post/0ee25928-42e8-4745-8fd9-73e9ed1a2a1d/image.png" width="500" />

1. 스레드는 프로세스 내에서 각 Stack만 따로 할당받고, Code, Data, Heap 영역은 공유합니다.
2. 스레드는 한 프로세스 내에서 동작되는 여러 실행의 흐름으로, 프로세스 내의 주소 공간이나 자원들(힙 공간 등)을 프로세스 내 스레드끼리 공유하며 실행됩니다.
3. 같은 프로세스 안에 있는 여러 스레드들은 같은 힙 공간을 공유한다. 반면 프로세스는 다른 프로세스의 메모리에 직접 접근할 수 없습니다.
4. 각 스레드는 별도 레지스터와 스택을 갖고 있지만, 힙 메모리는 서로 읽고 쓸 수 있습니다.
5. 한 스레드가 프로세스 자원을 변경하면, 다른 이웃 스레드(sibling Thread)도 해당 변경 결과를 즉시 볼 수 있습니다.

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 4. 자바스크립트는 싱글 스레드 언어로 알려져있는데, 싱글 스레드와 멀티 스레드의 차이점은 무엇이며, 각 장단점은 무엇인지 설명해주세요.
### 🙎‍♀️ 싱글스레드(Single thread)
<img src="https://velog.velcdn.com/images/haizel/post/4e2a729d-113e-40e8-a17f-f09c24d612ff/image.png" width="300" height="400" />
하나의 프로세스에 오직 하나의 스레드로만 실행되며, 따라서 하나의 레지스터와 스택으로 표현이 가능합니다.

순차 실행 방식으로, 앞선 동작이 먼저 수행되야만 이후 동작을 수행할 수 있습니다.

#### 👍 장점

1. **프로그래밍 난이도가 쉽고, CPU와 메모리 사용이 적습니다.**

단일 스레드로, 비용이 적게 소요됩니다.

2. **컨텍스트 스위칭(Context Switching, 문맥 교환)을 요구하지 않습니다.**

문맥 교환은 여러 개의 프로세스가 하나의 프로세서를 공유할 때 발생하는 작업으로 많은 비용을 필요로 합니다.

3. **자원 접근에 대한 동기화를 신경쓰지 않아도 됩니다.**

여러 개의 스레드가 프로세스의 자원을 공유할 경우, 각 스레드가 원하는 결과를 얻게 하려면 공용 자원에 대한 접근을 제어해야 합니다. 쉽게 말해 모든 스레드가 일정 자원에 동시에 접근하거나, 똑같은 작업을 실행하려고 하면 에러가 발생하거나 원하는 값이 나오지 않습니다. 때문에 스레드들이 동시에 같은 자원에 접근하지 못하도록 제어해주어야합니다. 이때 해당 많은 비용을 발생시킵니다.

#### 👎 단점

1. **여러 개의 CPU를 활용하지 못합니다.**

싱글스레드에서 프로세서를 최대한 활용하기 위해선 Cluster 모듈을 사용하거나 외부에서 여러 개의 프로그램 인스턴스를 실행시키는 방법을 사용해야합니다. 뿐만 아니라 다수의 프로그램 인트턴스가 어떻게 상태를 공유할 것인지도 고려해야 합니다.

2. **연산량이 많은 작업을 하는 경우, 그 작업이 완료되어야 다른 작업을 수행할 수 있습니다.**

많은 연산 시간이 필요한 작업의 경우, 작업이 완료되어야 다음 작업을 진행할 수 있기에 유저 경험에 좋지 않은 영향을 줍니다.

3. **싱글 스레드 모델은 에러 처리를 못하는 경우 중단됩니다.**

반면 멀티 스레드 모델은 에러 발생 시 새로운 스레드를 생성하여 극복합니다. 

<br />

### 👨‍👩‍👧‍👦 **멀티 스레드 (Multi thread)**
<img src="https://velog.velcdn.com/images/haizel/post/43689b9a-2245-4cc7-9822-8f9bc2f64455/image.png" width="300" height="300" />

멀티 스레드는 CPU의 최대 활용을 위해 프로그램의 둘 이상을 동시에 실행하는 기술로, 컨텍스트 스위칭을 통해서 이뤄집니다.

메인 스레드 외의 추가적인 스레드를 이용하여 병렬적으로 작업을 처리한다는 특징이 있습니다.

> 💡 **컨텍스트 스위칭(Context Switching)이란?**
> - CPU에서 여러 프로세스를 돌아가면서 작업을 처리하는 과정을 말합니다.
> - 구체적으로, 동작 중인 프로세스가 대기 하면서 해당 프로세스의 상태(Context)를 보관하고, 대기하고 있던 다음 순서의 프로세스가 동작하면서 이전에 보관했던 프로세스의 상태를 복구하는 작업을 말합니다.


#### 👍 장점

1. **응답성**

프로그램의 일부분(스레드 중 하나)이 중단되거나, 긴 작업을 수행하더라도 프로그램의 수행이 계속 되어 사용자에 대한 응답성이 증가합니다. 즉 에러 발생 시 즉시 새로운 스레드를 생성해 극복합니다. 단 이 때 새 스레드 생성과 놀고 있는 스체드 처리에 따른 비용이 발생할 수 있습니다.

2. **경제성**

프로세스 내 자원들과 메모리를 공유하기 때문에 메모리 공간과 시스템 자원 소모가 줄어듭니다. 또한 스레드간 컨텍스트 스위칭은 캐시 메모리를 비울 필요가 없기 때문에 더 빠른 속도를 보장합니다.

3. **멀티 프로세서의 활용**

다중 CPU 구조에서는 각각의 스레드가 다른 프로세서에서 병렬로 수행될 수 있으므로 병렬성이 증가합니다.

#### 👎 단점

1. **컨텍스트 스위칭, 동기화 등으로 오히려 단일 스레드보다 더 많은 시간이 소요될 수 있습니다.**

2. **동기화가 필수적입니다.**

스레드는 데이터와 힙 영역을 공유하기 때문에, 공유하는 자원에 동시에 접근하는 경우, 다른 스레드에서 사용중인 변수나 자료구조에 접근해 엉뚱한 값을 읽어오거나 수정할 수 있습니다. 따라서 동기화가 필수적입니다.

3. **멀티 스레딩을 위해서는 운영체제의 지원이 필요합니다.**

4. **프로그래밍 난이도가 높고, 스레드 수만큼 많은 자원을 필요로 합니다.**

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 5. 브라우저의 렌더링 과정에 대하여 설명해 주세요.

![image](https://github.com/sienna0715/frontend-interview-handbook/assets/115691844/02a48707-739d-412c-bec0-50dd6eef509f)

<br/>

1. 사용자가 브라우저를 통해 웹 사이트에 접속합니다.
2. Resource Downloading : 브라우저는 서버로부터 HTML, CSS, JavaScript와 같은 필요한 리소스를 웹사이트에 다운 받습니다.
3. HTML DOM Tree 구축 : 렌더링 엔진은 전달받은 HTML 문서를 파싱(parsing)해 DOM(Document Object Model, 문서 객체 모델) 트리 형성합니다.
4. CSSOM Tree 구축 : 이어서 다운 받은 외부 CSS 파일과 함께 포함된 스타일 요소를 파싱(parsing)해 CSSOM Tree 형성합니다.
5. Render Tree 구축 : 만든 DOM 트리와 CSSOM 트리를 결합합니다.
6. Rayout : 각 요소를 어디에 배치할 지 결정합니다.
7. Paint : 레이아웃 과정이 끝나면 UI 백엔드에서 Render 트리를 화면에 그리기 시작하는 과정입니다.

> 주의 : HTML문서를 파싱하는 도중에 Javascript를 만나면 하던 일을 멈추고 Javascript 먼저 읽습니다. 

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

## 6. 주소창에 google.com을 입력하면 일어나는 일을 설명해주세요.

<p align="center"><img src="https://user-images.githubusercontent.com/115691844/241798832-f26f160b-cf66-4cf3-89e6-7ccbe77e5bb0.png" width="500"></p>

<br/>

1. 사용자가 브라우저 검색창에 www.google.com 입력합니다.
2. 브라우저는 캐싱된 DNS 기록들을 통해 해당 도메인 주소와 대응하는 IP주소를 확인합니다.
3. DNS가 브라우저에게 찾는 사이트의 IP주소를 응답합니다.
4. 브라우저가 서버에게 IP주소를 이용하여 데이터를 요청합니다.
5. 서버가 요청 받은 데이터를 처리합니다.
6. 서버는 브라우저에게 데이터 처리 결과를 응답합니다.
7. 브라우저는 화면에 결과를 출력합니다.

<br/><br/>
👆 [맨 위로 올라가기](https://github.com/sienna0715/frontend-interview-handbook/tree/main/React#react)
<br/><br/>

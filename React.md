- React
리액트는 페이스북에서 개발된 JavaScript 라이브러리, 사용자 인터페이스(UI)를 구축하기 위해 활용한다.
주요 목표는 UI를 더 간단하고, 효율적으로 구성하기 위함. 컴포넌트 기반 아키텍처를 중심으로 동작하는데
컴포넌트 : UI의 작은 부분을 독립적으로 관리하는 단위, 재사용성과 모듈화를 용이하게 해준다.

JSX(JavaScript XML) : 자바스크립트와 XML을 결합하여 동적인 UI생성
가상 DOM을 활용하여 성능 최적화, 가상 DOM, DOM 복제해서 실제 DOM과 비교하여 필요한 부분만 업데이트한다.

장점 
- 컴포넌트 기반 아키텍처 : 독립적인 단위인 컴포넌트로 분리하는 디자인 패턴이다.
소프트웨어 엔지니어링 기본 원칙 : 관심사의 분리(Separation of Concerns) 를 실현 가능하게 한다.

1) 함수형(Functional) 컴포넌트 : 함수처럼 작동하여 props을 입력 받아 화면에 표시한다.
2) 클래스(Class) 컴포넌트 : React.Component 클래스를 상속받아 더 복잡한 기능을 사용할 수 있다.

단방향 데이터 흐름 : 상태(state), 속성(props)에 대한 관리가 명확, 데이터 흐름을 예측 가능하다.

DOM(Document Object Model) : 웹 페이지의 구조를 표현하는 인터페이스
DOM은 비용이 많이드는 작업이다. 자주 발생하면 웹 어플리케이션의 성능을 저하시킨다.

리액트는 이러한 문제를 해결하기 위해 가상 DOM(Virtual DOM) 방식을 도입했다.
가상 DOM은 실제 DOM의 복사본으로 메모리 내에 존재한다. 
리액트 컴포넌트의 상태가 변경될 때마다 새로운 가상 DOM 트리를 생성하고 이전 트리와 비교(diffing)하여 변경사항을 파악한다.
이 과정을 재조정(Reconciliation) 또는 Diffing Algorithm이라고 부른다.

변경사항만 하고 실제 DOM에 해당 변경사항만 반영하는 방식으로 작동한다.
당연히 모든 사항을 직접 반영하는 것보다 훨씬 더 빠르게 업데이트를 처리할 수 있다.

장점
1. 성능 최적화
2. 코드 단순화
3. 크로스 플랫폼 호환

단점
가상 DOM도 사용 방법에 따라 성능 문제가 발생할 수 있다. 상태 변화가 너무 자주 일어나거나 컴포넌트 구조가 복잡하면

- 단방향 데이터 흐름
리액트에서 데이터 흐름 '단방향' or '하향식'이라고 부른다.
부모 컴포넌트에서 자식 컴포넌트로만 속성(props)을 통해 데이터가 전달이 된다.
자식 컴포넌트에서 직접 부모의 상태를 변경하는 것을 불가능하다.
일반적으로 콜백 함수(Callback function)을 사용해서 자식에게 전달하여, 자식이 함수를 호출하여 부모에게 정보를 전달할 수 있다.
다른 함수의 매개변수로 함수를 넘겨주는 실행가능한 코드(다른 함수의 매개변수로 존재하기 위한 함수)


NPM(Node Package Manager) : NPM은 자바스크립트의 패키지 관리자
Create React App : 프로젝트 생성을 간소화하는 공식 CLI(Command  Line Interface) 도구.

- JSX(Javascript XML)
단순한 마크업 언어가 아니고, 동적표현이 가능하다. 중괄호({})안에 자바스크림트 표현식을 넣어서 변수나, 함수 호출할 수 있다.
컴포넌트를 대부분 JSX로 작성한다. 보통 브라우저는 jSX를 해석할 수 없다. 그래서 Babel과 같은 도구를 사용해서 자바스크립트로 변환하여 전달한다.
태그를 닫아야하고, class 대신에 className이라고 써야한다. /**/

const name = "Kim";
const element = <h1>Hello {name}</h1>;

const isTrue = true;
const element = <h1>{isTrue ? 'Welcome' : 'Sign Up'}</h1>

function formatName(user) {
    return user.firstName + " " + user.lastName;
}

const user = {
    firstName: "Kim",
    lastName: "MMM"
};

const element = <h1>Hello, {formatName(user)}</h>;

함수형 컴포넌트
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>
}

클래스형 컴포넌트
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
    }
}

<Welcome name="Kim"/>

const element = <h1>Hello, world!</h1>;

 Babel

 const element = React.createElement("h1", null, "Hello, world!");

 - render : 컴포넌트의 출력을 정의하는 역할
 함수형 컴포넌트 : 함수 자체가 랜더링 로직을 담당, JSX를 반환해야한다.
 클래스형 컴포넌트 : 컴포넌트가 어떻게 보여질지 정의한다. JSX를 반환해야한다.

 render 메소드와 같은 컴포넌트 내부에서 반환되는 JSX 요소를 React 엘리먼트라고 한다.
 화면에 어떤 것이 보여질지 나타내며, 실제 DOM과는 연결되지 않는다.

 - 함수형 컴포넌트 : 리액트의 훅(Hooks) 기능이 도입되기 전에는 라이프사이클, 상태 관리 등을 할 수가 없었다.
 - 클래스형 컴포넌트 : 처음 도입될 떄부터 있었으며, render를 통해 JSX를 반환하고, this.state, this.setState등을 통해 내부 상태를
 관리하고, 라이프사이클 메서드를 통해 화면에 나타나거나 사라지는 시점에 특정 작업을 수행할 수 있다.

 1) 상태(State) : 상태는 컴포넌트 내부에서 선언되고, 컴포넌트 동작에 필요한 데이터를 저장한다. 상태값이 변경되고 변경될 때,
 사용자나 상호작용이나 데이터 업데이트. 상태가 변경되면 React는 상태를 감지하여 컴포넌트를 랜더링 한다.
 클래스형 : this.state로 상태를 정의하고, this.setState() 상태를 업데이트 한다.
 함수형 : useState라는 훅을 사용하여 상태를 관리한다. useState 초기값을 받아서 현재 상태와 해당 상태를 업데이트 하는 함수 두 가지를 반환한다.

 2) 속성(Props) : 부모 컴포넌트로부터 자식 컴포넌트로 데이터가 전달될 때 사용된다. 속성은 읽기 전용으로 한 번 전달받으면 그 값을
 바꿀 수 없다. 컴포넌트 간의 통신

 function Child(props) {
    return <div>{props.message}</div>;
 }
 function Parent() {
    return <Child message="Hello from Parent"/>;
 }

- 컴포넌트의 구조화와 계층 구조, 컴포지션(composition)
컴포지션은 더 큰 단위의 컴포넌트를 작은 단위 컴포넌트로 분해하는 방법을 말한다.

function App() {
    return (
        <div>
            <Header />
            <Body>
                <Article />
                <Sidebar />
            </Body>
            <Footer />
        </div>
    )
}
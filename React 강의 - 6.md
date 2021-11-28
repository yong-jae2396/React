### Props (데이터 전달)

****

* **Props는 부모 컴포넌트가 자식 컴포넌트에 값을 전달할 때 사용하는 것이다. 읽기 전용**
* Props는 Immutable Data즉, 변하지 않는 데이터이다.
* 사용법(상위) : <컴포넌트이름 props이름 = 값> 이렇게 상위 컴포넌트에서 정의
* 사용법(하위) : props파라미터.props이름으로 사용할 수 있다.

****

```react
// React.js 예제 코드
class Children extends React.Component { // 하위(자식) 컴포넌트
  render() {
    return (
      <div>
        // 상위 컴포넌트가 넘겨준 props인 name사용
        <h1>Hello {this.props.name}</h1>
        // 상위 컴포넌트가 넘겨준 props.children 사용
        <div>{this.props.children}</div>
      </div>
    );
  }
}
class App extends React.Component { // 상위(부모) 컴포넌트
  render() {
    return (
      // props이름 : name
      // name이란 props의 값 : 이름
      // this.props.children의 값 : 이 사이에 있는거는 children
      <Children name="이름">이 사이에 있는거는 children</Children>
    );
  }
}
ReactDOM.render(<App/>, document.getElementById("root"));
```

![img](https://miro.medium.com/max/238/1*syLRLbOPnBDoYNNygi-TMw.png)**<<<< 결과 값 **

****

#### - default props를 지정하는 방법

* Component.defaultProps = {…} 이렇게 선언해주면 된다.

****

#### - props type

````react
// React.js 예제 코드
class Children extends React.Component { // 하위(자식) 컴포넌트
  render() {
    return (
      <div>
        <h1>Hello {this.props.name}</h1>
        <h2>{this.props.number}</h2>
        <div>{this.props.children}</div>
      </div>
    );
  }
}

// props type 검증
Children.propTypes = {
  name: PropTypes.string, // string 타입
  number: PropTypes.number.isRequired, // number 타입, 필수 값으로 지정
};

// default props 지정
Children.defaultProps = {
  name: 'Unknown' // props를 정의하지 않았을 경우 name props의 기본 값
};

class App extends React.Component { // 상위(부모) 컴포넌트
  render() {
    return (
      <Children number={3}>이 사이에 있는거는 children</Children>
    );
  }
}
ReactDOM.render(<App/>, document.getElementById("root"));
````

![img](https://miro.medium.com/max/252/1*PGvY0rVxuacsEZr8sezh8A.png) **<<<< 결과 값**

****

#### - 참고

*  propTypes에서 어떤 타입이든 허용할 때는 any
* React element인지 검증할 때는 element라고 사용한다.

*****




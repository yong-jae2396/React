### React 조건 렌더링

****

```react
import React, { useEffect, useState} from 'react';

function App() {  
  // useState를 이용하여 변수 생성
  const [condition, setCondition] = useState(false);
  
  // toggle를 생성하여 실행될 경우 !condition에 값을 전해줌
  const toggle = () => setCondition(!condition);
  
  // useEffect를 이용하여 condition이 바뀔 때 마다 console에 출력
  useEffect(() => {
    console.log(condition);
  }, [condition])
  
  // 삼항 연산자를 사용한 조건 추가
  const renderCondition = condition
    ? 'True'
    : 'False'
  return (
    <div className="App">
      <h1>React-Hello</h1>
      <div>
        {renderCondition} <!-- 조건을 통하여 변수에 담긴 값을 출력 -->
      </div>
      <button onClick = {toggle}>Toggle</button> <!--onClick를 사용하여 클릭시 toggle 실행-->
    </div>
  );
}

export default App;
```

* 위에 코드처럼 변수를 선언하고 if문을 사용하는 것은 조건부로 컴포넌트를 렌더링하는 방법이다

* **하지만 위에 구문보다 더 짧은 구문을 사용할 수 도있다 JSX에 조건을 인라인으로 넣는 방법**

  ```react
  function Mailbox(props) {
    const unreadMessages = props.unreadMessages;
    return (
      <div>
        <h1>Hello!</h1>
        {unreadMessages.length > 0 &&  //&&연산자 사용
          <h2>
            You have {unreadMessages.length} unread messages.
          </h2>
        }
      </div>
    );
  }
  
  const messages = ['React', 'Re: React', 'Re:Re: React'];
  ReactDOM.render(
    <Mailbox unreadMessages={messages} />,
    document.getElementById('root')
  );
  ```

****




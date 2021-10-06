### 3. React-Hooks

****

#### - Hook 개요

* Hook React 버전 16.8부터 React요소로 새로 추가되었습니다. Hook을 이용하여 기존 

  class바탕의 코드를 작성할 필요없이 상태 값과 여러 react의 기능을 사용할 수 있게 되었다.

****

#### - Hook의 특징

* **선택적사용** : 기존의 코드를 다시 작성할 필요 없이 일부의 컴포넌트들 알에서 Hook을 사용할 수 있다.

  ​					  그러나 당장 Hook가 필요없다면 Hook를 사용할 필요는 없다.

* **100% 이전 버전과의 호환성** : Hook은 호환성을 깨트리는 변화가 없다.

****

#### - Hook - useState

* **소개** : 컴포넌트에서 동적인 값을 상태(state)라고 부릅니다. react에서 useState라는 함수는 

  ​		   컴포넌트에서 state를 관리 할 수 있게 합니다.

   **- useState 비구조화 할당 (구조분해) 문법**

* useState를 사용 할 때에는 상태의 기본값을 파라미터로 넣어서 호출해줍니다. 이함수를 호출하면

  배열이 반환되는데 여기서 첫번째 원소는 현재상태, 두번째 원소는 Setter함수입니다.

* 할당할때 원래의 경우는 아래코드처럼 해야하지만

  ```react
  const numberState = useState(0);
  const number = numberState[0];
  const setNumber = numberState[1];
  ```

* **배열 비구조화 할당**을 통하여 각 원소를 추출하는 방식을 통하여 아래처럼한다.

  ```react
  const [number, setNumber] = useState(0);
  ```

****

* **useState를 사용한 예시1** (버튼을 이용하여 화면에 출력되어있는 숫자에 변화주기)

  ```react
  let[number, setNumber] = useState(0); // 배열 비구조화 할당방식을 사용
  
  
  //빼는 기능을 가진 함수생성
  const decrease = () => {
    setNumber(number - 1);
  }
  
  //더하는 기능을 가진 함수 생성(number변수에 1을 더하여 setNumber에 할당)
  const increase = () => {
    setNumber(number + 1);
  }
  
  // react기능을 가진 함수생성(변수의 0을 할당하여 초기화)
  const onReset = () => {
    setNumber(number = 0);
  }
  
  return (
    <div className="App">
      <h1>{number}</h1> <!--{}에 변수를 넣어 화면에 h1으로 출력-->
      <button onClick = {decrease}>+1</button> <!--버튼을 생성하여 위에서 만든 함수를 할당-->
      <button onClick = {increase}>-1</button>
      <button onClick = {onReset}>reset</button>
    </div>
  );
  ```

*****

* **useState를 사용한 예시2** (form태그를 이용하여 아이디와 패스워드 입력하기)

  ```react
    const [username, setUsername] = useState(''); // 변수생성
    const [password, setPassword] = useState('');
  
    const onSubmit = (event) => { 
      event.preventDefault(); // form의 고유특성인 Submit이 될때 refresh되는것을 방지하는 용도
      console.log(username, password); // 입력된 값을 console.log로 확인
    };
    
    return (
      <div className="App">
        <form onSubmit={onSubmit}>
          <input 
            placeholder = "Username" 
            value = {username} 
            //event를 받아와 e.target.value를 통하여 새로운 값이 입력되었을때 username을 업데이트시킴
            onChange = {(e) => setUsername(e.target.value)} 
  
            /><br />
  
          <input 
            placeholder = "Passsword"
            value = {password} 
            onChange = {(e) => setPassword(e.target.value)} 
          /><br />
          <button type='submit'>Login</button>
        </form>
      </div>
    );
  ```

*****


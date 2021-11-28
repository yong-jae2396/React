### 4. React-4

****

#### Hook-useEffect

* 정의 : react 컴포넌트가 렌더링 될 때마다 특정 작업을 실행할 수 있도록 하는 Hook이다.
* useEffect는 component가 mount 됐을때, component가 unmount 됐을때, component가 update 됐을때, 특정작업을 처리한다.

****

#### - useEffect 사용법

* +기본 형태 : useEffect(function, deps)
  * function : 수행하고자 하는 작업
  * deps : 배열 형태이며, 배열 안에는 검사하고자 하는 특정 값 or 빈 배열

****

* **1. Component가 mount 됐을 때** (처음 나타났을 때)

  * 컴포넌트가 화면에 가장 처음 렌더링 될 때 한 번만 실행하고 싶을 때는 deps위치에 빈 배열을 넣는다.

    ```react
    useEffect(() = > {
        console.log('마운트 될 때만 실행된다.');
    }, []);
    ```

  * 배열을 생략할경우 리렌더링 될 때 마다 실행된다.

    ```react
    useEffect(() => {
        console.log('렌더링이 될 때 마다 실행된다.');
    });
    ```

* **2. Component가 update 될 때 (특정 props, state가 바뀔 때)**

  ```react
  useEffect(() => {
      console.log(name);
      console.log('업데이트 될 때 실행된다.');
  }, [name]);
  ```

* **3. Component가 unmount될 때(사라질 때)  & update 되기 직전에**

  * 언마운트 될 때만 cleanup함수를 실행하고 싶을 때
    * 방법 : 두 번째 파라미터로 빈 배열을 넣는다.
  * 특정값이 업데이트 되기 직전에 cleanup함수를 실행하고 싶을 때
    * 방법 : deps 배열 안에 검사하고 싶은 값을 넣어준다.

  ```react
  useEffect(() => {
      console.log('effect');
      console.log(name);
      return() => {
          console.log('cleanup');
          console.log(name);
      };
  }, []);
  ```

****

**1. deps에 특정 값 넣기**

* deps에 특정 값을 넣게 된다면 컴포넌트가 처음 마운트 될 때, 지정한 값이 바뀔 때, 언마운트 될 때, 값이 

  바뀌기직전에 모두 호출이 된다.

* useEffect안에서 사용하는 상태나, props가 있다면, useEffect의 deps에 넣어주어야 하는 것이 규칙이다 만약 사용하는 값을 넣어주지 않는다면, useEffect 안의 함수가 실행될 때 최신 상태, props를 가리키지 않는다.
* deps 파라미터를 생략한다면, 컴포넌트가 리렌더링 될 때마다 useEffect 함수가 호출 된다.

****
















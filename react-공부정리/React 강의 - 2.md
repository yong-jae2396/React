### 2 . 이벤트 핸들러

****

#### React의 이벤트 특징

* react의 이벤트 처리방식은 DOM엘리먼트에서 이벤트를 처리하는 방식과 매우 유사하다.

* react의 이벤트는 소문자대신 캐멀 케이스(camelCase)를 사용합니다.

* 문법은 JSX를 사용하며 문자열이 아닌 함수로 이벤트 핸들러를 전달합니다. 예를 들어

  * HTML의 경우

    ```react
    <button onclick="activateLasers()">
      Activate Lasers
    </button>
    ```

  * react의 경우

    ```react
    <button onClick={activateLasers}>
      Activate Lasers
    </button>
    ```

* 함수형으로 전달하지 않을 경우에 이벤트로 등록이 되는것이 아니라 렌더링할때 함수가 바로 실행된다.

****

### react 이벤트 종류

**- 링크에서 확인가능**

- https://ko.reactjs.org/docs/events.html (react 리액트 공식문서)




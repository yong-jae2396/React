### React 반복문

****

**- JSX를 이용한 반복문 **

- **1.  return문에서 JSX를 반환하는 함수 호출**
  - 장점 : 재사용이 용이함, return문이 깔끔하다.
  - 참고 : JSX 루프 렌더링 시에 반드시 key값을 unique하게 할당해줍니다. - react specific

```react
function App() {
  const weekArr = ["MON", "TUE", "WED", "THU", "FRI", "SAT", "SUN"];
  
  const rendering = () => {
    const result = [];
    for (let i = 0; i < weekArr.length; i++) {
      result.push(<span key={i}>{weekArr[i] + " / "}</span>);
    }
    return result;
  };

  return <div>{rendering()}</div>;
```

****

* **2. return문 안에서 map 사용**
  * 장점 : 가독성이 좋음, 직관적이다.
  * 참고 : forEach의 경우 값을 반환하지 않는 단순연산이기 때문에 JSX를 반환할  수 있는 map를 사용한다.

```react
function App() {
  const weekArr = ["MON", "TUE", "WED", "THU", "FRI", "SAT", "SUN"];

  return (
    <div>
      {weekArr.map((week, index) => (
        <span key={index}>
          {week}
          {" / "}
        </span>
      ))}
    </div>
  );
}
```

*****

↑↑↑

위에 코드들의 결과 = MON / TUE / WED / THU / FRI / SAT / SUN


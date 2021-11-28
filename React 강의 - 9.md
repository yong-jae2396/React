#### React Router 정리

****

#### Routing 

- 라우팅이란, 어떤 주소에서 어떤 UI를 보여줄것인가  규칙을 정하는 작업을 말한다.
- 과거의 라우팅은 주로 서버에서 처리했지만, 최근 웹에서는 클라이언트가 관리한다.

****

#### SPA (Single Page Application)

* SPA의 등장 배경 

  ````
  과거에는 클라이언트는 원하는 주소 (/root)를 서버에 요청하면 서버가 그에 해당하는 
  html파일을 전달 해주고, 클라이언트는 그 html파일을 브라우저에 보여주는 방식이었다
  하지만 사용자 인터렉션이 많은 경우에 계속 서버에 요청하고, 받는 과정이 UX에 좋지 않고,
  서버 자원도 낭비되었었다.
  ````

* SPA의 등장

  ````
  위에 이유 때문에 SPA가 등장하였다 SPA는 웹 어플리케이션 구성에 필요한 모든 정적 리소스를 최초에 
  한번 다운 받습니다. 이후 변경이 필요하면 클라이언트에서 자체적으로 UI를 렌더링하며, 필요한
  데이터가 있을 때만 서버에 추가적인 데이터를 요청하고 처리합니다. 이 때 페이지 전체가 아닌 필요한 
  부분만 리렌더링을 진행하며, 이로인해 사용자 경험(UX)이 향상됩니다.
  ````

* SPA의 단점
  * 앱의 규모가 커지면 JS파일이 너무 커질 수 있다.    =>   (Code splitting 으로 해결가능)
  * 브라우저에서 JS가 구동되지 않으면 UI를 볼 수 없다.   =>  (SSR(Server Side Rendering)을 통해 해결가능)

****

#### React-Router

* react에서 SPA를 만들기 위해 가장 많이 사용되는 라이브러리이다 최근에는 Next가 치고 올라오고 있다.

* React-Router : 컴포넌트를 기반으로 라우팅합니다.
* Next : 파일 경로, 이름을 기반으로 라우팅합니다. (SSR, Code Splitting을 매우 쉽게 구현 가능)

****

#### React-Router의 주요 컴포넌트

* **BrowerRouter**

  * Html5 History API를 사용하며 **주소만 바꾸고 페이지는 다시 불러오진 않는다.**

  * 서버측에 새로운 요청을 하지 않으며 이를 통해 history를 남겨서 SPA에서 뒤로가기를

    구현할 수 있습니다. (본래 SPA는 싱글 페이지이기 때문에 뒤로가기 개념이 없습니다.)

* **HashRouter**

  * 도메인 뒤에 #태그를 붙이는 형태, 요즘은 잘 사용하지 않는다.

* **MemoryRouter**

  * 브라우저의 주소와 전혀 관계 없습니다.
  * 그래서 브라우저가 아닌 환경에서 쓰기 좋습니다. 임베디드 웹앱, 리액트 네이티브 
  * 특정 페이지에 일부분을 리액트로 구현해서 삽입하고 싶을 때
  * 브라우저 주소가 변경되지 않는다.

* **StaticRouter**

  * SSR를 할 때 사용합니다.

* **Route**

  * 라우트를 정의할 때 사용하는 컴포넌트

  * 어떤 경로로 들어왔을 때, 어떤 컴포넌트를 보여줄것인지.

  * ````react
    <Route path="/" component={Home}>
    <Route path="/about" component={About} exact>
    ````

    * path에 해당하는 주소값에 지정한 component를 보여주겠다는 뜻이다.

    * 위에 경우 "/about"주소에 들어가면 About컴포넌트만 보일 것 같지만, Home

      컴포넌트도 같이 보입니다. 왜냐하면  "/about"이라는 경로에 "/"도 포함되어있기 때문!

    * 이를 해결하기 위해 "/"를 지정한 Route 컴포넌트에 exact속성을 추가합니다.

      ````react
      <Route path="/" component={Home} exact>
      ````

    * exact 속성은 해당 path 주소가 정확히 일치할 때만 해당 컴포넌트를 보여주도록합니다.

* **Link**

  * 사용한 Router의 주소를 바꿉니다.

  * a태그와 동일하지만 새로고침이 되지 않습니다.

    ```react
    <Link to="/">홈</Link>
    <Link to="/about">어바웃</Link>
    ```

* **NavLink**
  * LInk와 유사
  * 현재경로와 Link에서 사용하는 경로가 일치하는 경우 특정 스타일 혹은 CSS 클래스를 적용할 수 있게 함
    * 특정 스타일을 적용할 때 : activeStyle값을 사용
    * CSS 클래스를 적용할 때는 activeClassName 값을 props로 넣어주면 된다.

****

#### 파라피터

* **URL Parameter**

  * 정해진 특정 데이터를 가져올 때 주로 사용

  * /users/DD

  * Route 컴포넌트의  path주소에 /:target을 입력한다.

    * ```` 
      <Route path="/users/:username" component={UserView}/>
      ````

  * component에 URL Parameter 처리가 구현된 컴포넌트를 입력한다.

    `````react
    const User = ({match}) => {
    	const { username } = match.params;
        ...
    };
    `````

  * match는 Route 컴포넌트가 자동으로 넣어주는 props를 담고 있다. match의 params 속성안에 우리가 Route 컴포넌트에서 path에 "/users/:" 뒤에 입력한 username이 키로 존재한다.
  * URL에 /users/:DD 라고 입력하면 DD가 username키의 값이 되어 컴포넌트에 전달되는 것

****








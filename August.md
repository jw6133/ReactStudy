8/1 ~7.1
array요소를 추가하고 싶다면,
const array = [1, 2, 3, 4]
const arrayTwo = [...array, 5] 처럼 원본에 ...을 붙여서 요소로 추가

[].map(a,b); ==> 배열 안에 있는 값 전부에 a 실행 / b는 index임.
react로 todo list를 만들고, li를 map으로 추가하는 것을 state를 통해 만듬.

8/2 7.2
fetch() 함수는 첫번째 인자로 URL, 두번째 인자로 옵션 객체를 받고, Promise 타입의 객체를 반환합니다. 반환된 객체는, API 호출이 성공했을 경우에는 응답(response) 객체를 resolve하고, 실패했을 경우에는 예외(error) 객체를 reject합니다.
 fetch("https://api.coinpaprika.com/v1/tickers")
      .then((response) => response.json())

8/3 7.3
.then()은 . 앞에거가 발동되면 다음으로 발동되는 함수로, 자주 써왔지만 요즘은 이거보단 async()를 더 쓴다고 한다.

8/9
<Router>
      <Switch>
        <Route path="/hello">
          <h1>Hello</h1>
        </Route>
        <Route path="/movie">
          <Detail />
        </Route>
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </Router> ===> switch는 route를 찾고 찾으면 렌더링하는 router
    브라우저 라우터랑은 url의 생김새가 다름.
    <link to=""> = 페이지 내에서 새로고침 하지 않고 페이지 요소로 이동. 페이지 내의 하이퍼링크?
    
    url의 마지막엔 5글자 id가 나오는데 id를 미리 알면 미리 url에 요청을 보낼 수 있다. 즉, 우리의 url을 사용할 수 있다. 여러가지로.
    그 id는 import {useParams}로 useParams를 가져와서 사용하는 것으로 반환받을 수 있다.
    const x = useParams()
    console.log(x)

7/18 ~2.2
튜토 및 설명
React 설치 :          <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script> <-- react = engine.
         <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script> <-- 이 react-don은 react element가 html에 있게 해줌

element 생성(React의 어려운 방법) : const span = React.createElement("span"); 단, createElement 속 내용은 html의 요소 이름과 같아야됨. span이면 span h1이면 h1.
ReactDOM.render(a); a를 html로 만들어 배치함.

createElement("a",{id="aaa"}) 이렇게 둘째 요소로 {}를 넣어줌으로써, a의 property도 조작 가능.
핵심 : js는 먼저 html에서 만들고 그걸 js에 가져와서 수정 후 보여줌. React는 js에서 할거 다하고 최종적으로 html에 제출해서 보여주는 방식. 즉, 거꾸로임

7/19 ~2.6
const btn = React.createElement("button",{onclick:()=>console.log("i am clicked.")},"Click me"); ==>addEventListener
어쨋든 createElement는 나중에 우리가 쓸 방식이 아님. 구닥다리

새로운 방법 = JSX Javascript Syntax eXtansion
const title = <h3 id="title" onMouseEnter={() => console.log("i am entered.")}>hello i am a title</h3>
html처럼 만들고 property로 이벤트 추가하면 됨.
JSX는 기본적으로 브라우저가 이해하지 못해서, 이전에 한 어려운 방식으로 변환해줘야함. 이 "변환"은 "babel" 이란 요소가 해줌.

JSX div = const Container = (<div>
            <Title />
            <Button />
            </div>);
            
            단, <Aaa /> 속 Aaa는 함수화 예시) const Aaa () => (); 가 되있어야 하며, 첫 글자가 대문자가 아니면 html태그라 인식하여 꼭 대문자로 해줘야 jsx가 인식함.

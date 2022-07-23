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

7/20 ~3.2
기본적으로 데이터가 저장되는곳 = state
ReactJs에서 변하는 변수 출력 => <h3>Count : {변수}</h3>
React는 바뀌어야 하는 부분만 알아서 변경해줌. count 가 오르면 count만 수정하고 body부분은 사실 변경 안해도 되는데, 그걸 React는 알고 업데이트 하지 않음. => GENIUS
Count를 변경하려면, count를 let으로 지정한 변수에 넣어서 변환 후 render 해줘야함. => 함수 2개 써야함.

이걸     const data = React.useState(); 로 대체가능.
    const data = React.useState(a);는 [a,f]를 주는데, a는 count를, f는 a를 바꿀 수 있는 function(함수)를 뜻함. ==> 위의 함수 2개의 일이 압축되어있는 꼴.
 
 const food =["soup","sausage"]
 const= [foodone,foodtwo] =food
 => foodone = "soup" / foodtwo = "sausage"
 
 여튼 위의 문법을 사용해서 const [counter, modifier]= React.useState();를 구현할 때, modifier를 사용함으로써 우리가 직접 counter를 변경하는 방법을 썼을때의 문제인
 재랜더링해줘야하는 문제점을 해결해줌
 modifier()는 괄호 안의 값으로 counter를 업데이트하고 랜더링까지 다시해줌. ==>문제해결

7/21 ~3.7
Recap

counter + 1 = (current) => current + 1 *current는 현재의 값을 전달해주는 "함수"로 생각해야 함.
setCounter라는 함수에 현재값을 전달해주는 current라는 함수를 전달하는 것임.
unit converter (유닛 변환기 : 분을 넣으면 시간으로 변환해주거나 km를 넣으면 마일로 변환해주는 장치 (예시임)) 
<label>은 for(js용어)을 이용해 다른 요소와 연결 for="다른 요소 id" (단, HTML 한정)
onChange = 입력 이벤트
input의 값을 받아오려면, js에서 했던거처럼 이벤트함수에 event라고 argument(인수)를 주면, 거기에 document가 생김.
그럼 그 document 안의 요소 중 input의 값이 있음. 그건 event.target.value임.
**SetState를 통한 업데이트**

input에는 2가지 event처리요소가 필요하다. 1 : event감지 2 : event 감지 후 역할 수행 및 업데이트

const onFlip = () => setFlipped(current => !current); 현재값인 current에 현재값의 반대되는 값인 !current를 삽입하므로써 Flip.
기본값이 false이므로 disabled={flipped === false}인 Hour는 작동이 안되지만, onflip이 발동하면 값이 false의 반대인 true가 되므로 disable 프로퍼티도 false가 됨 == 작동.
삼항연산자 : 항이 세개인 연산자 ex) (5 > 3)? 1 : 0 ===> 5가 3보다 클땐 1. 아니면 0  맞을때의 값 : 틀릴때의 값인 느낌.

7/22 ~4.0
<select> : html 요소로, <obtion>과 함께 사용함.;
예시 : <select value={index} onChange={onSelect}>
                <option value="xx">Select your Units.</option>
                <option value="0">Minute & Hours</option>
                <option value="1">Km & Miles</option>
            </select>
         이 index는 위에 지정해놓은 const[a,b]=React.useState(0);의 a로 들어가서 b를 통해 조작됨.
props = <Btn source="Save Changes" /> ==> Btn(props)를 하면, source가 props칸에 들어가는 형식. 함수를 지정하고 아래에서 컴포넌트로 사용하면, 
         함수에 존재하는 props가 컴포넌트로 사용한 곳에서 지정한 요소로 변하는 느낌.
        사용법 : {props.source} (object로 전달되기 때문.)

7/23 ~4.3
prop을 전달해줘도, 따로 적용시키지 않으면 React는 알아서 적용시켜주지 않음.
컴포넌트 사용때 prop으로 전달. => 컴포넌트의 근원지인 함수에서 argument로 prop 받음 => 함수 내용에서 argument로 받은 prop을 적용.
memo : const MemorizedBtn = React.memo(Btn);로, btn 컴포넌트의 실행을 "기억"(memo)하고 반복되는게 있으면 다음부터 실행하지 않음.

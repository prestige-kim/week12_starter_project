# Project Information: 프로젝트 소개 및 Starter Project 정보
> React Hooks Starter Project. 
> useEffect 와 useRef 를 이용하여 4개의 LAB 내용을 TODO 로 완성하는 프로젝트


# Installation: 설치·실행 방법 및 실행 화면
Node.js 20.19+ 또는 22.12+ 권장. 프로젝트 폴더에서 실행:

```bash
npm install
npm run dev
```

# Source Code Exploration: 주요 파일 구조, useEffect 및 useRef 분석, 주요 코드 2개 설명
index.html -> main.jsx -> App.jsx -> 선택된 LAB 컴포넌트

```JavaScript
const chosen = labs.find(lab => lab.id === active);
const CurrentLab = chosen.Component;
// 배열로 lab 정보를 관리하고 선택된 LAB 정보를 찾아 해당 컴포넌트를 변수에 저장한다. 저장한 컴포넌트를 아래에서 렌더링한다.
<CurrentLab />
```

```JavaScript
// 지역 변수로 타이머 ID 를 저장
const id = setInterval(()=>{
    setCount(prev => prev + 1);
}, 1000);

// useRef 변수에 타이머 ID를 저장
const timerRef = useRef(null);
timerRef.current = setInterval(()=>{
    setCount(prev => prev + 1);
}, 1000);
```
# Lab Implementation: 4개 Lab 구현 내용 및 실행 결과
Lab1_EffectTimer.jsx: useEffect를 이용하여 1초마다 증가하는 타이머
> 실행결과: LAB 1에 진입하면 count가 0부터 1초마다 증가한다. 다른 LAB으로 이동하면 타이머가 정리되고, 다시 진입하면 0부터 시작한다.

Lab2_TimerControl.jsx: State와 Effect를 연결하여 타이머의 실행 상태를 제어
> 실행결과: Start를 누르면 count가 1초마다 증가하고 상태가 Running으로 표시된다. Stop을 누르면 증가가 멈추며 Stopped로 표시된다. 다시 Start를 누르면 기존 count에서 이어서 증가하고, Reset을 누르면 정지 상태에서 0으로 초기화된다.

Lab3_InputFocus.jsx: Ref를 이용하여 실제 DOM 요소를 제어
> 실행결과: Focus 버튼을 누르면 입력창으로 포커스가 이동한다. 값을 입력한 후 Clear 버튼을 누르면 입력값이 삭제되고 입력창에 다시 포커스가 맞춰진다.

Lab4_RefTimer.jsx: useRef를 이용하여 타이머 관리
> 실행결과: Start를 누르면 count가 증가하고, Stop을 누르면 현재 값에서 멈춘다. Reset을 누르면 타이머가 정지하고 count가 0이 된다. 다른 LAB으로 이동하면 타이머가 정리된다.

# Lab Comparison: STEP 3의 비교 분석 질문 4개에 대한 답변
1. useEffect의 Dependency Array가 필요한 이유는?
    > Eccect를 언제 다시 실행할지 기준을 정하기 위해서.
2. Cleanup을 사용하지 않으면 어떤 문제가 발생할 수 있는가?
    > 생성한 타이머가 계속 실행이 된다. 또한, 언마운트가 되어도 다른 LAB으로 이동해도 백그라운드에서 계속 실행이 된다. 
3. useState와 useRef의 가장 중요한 차이는?
    > useState 는 setter 로 값을 바꾸면 다시 렌더링 되지만 useRef 는 .current 를 변경해도 다시 렌더링되지 않는다.
4. LAB 2와 LAB 4의 Timer 관리 방식은 어떻게 다른가?
    > LAB 2: running 상태 변화에 따라 useEffect 에서 타이머를 생성, 지역 변수 id에 타이머 ID 저장.
    > LAB 4는 useRef 의 current 에 타이머 ID 를 저장하고 Start/Stop 버튼 이벤트에서 타이머를 관리.

# Customizing: 수정 내용 및 파일명
App.css: 
LAB 선택 배경 색 변경
, LAB 별 패널 색 변경

App.jsx: 
상단 문구를 OPEN SOURCE STUDIO 로 변경
화면 제목을 React Hooks Assignment Week 12로 변경

index.html: 
브라우저 탭 제목을 React Hooks W12로 변경

# Deployment: 실제 접근 가능한 Vercel URL
https://week12-starter-project-mu.vercel.app/

# Weekly Review:
- 새롭게 배운 내용 3가지
1. useRef, useEffect 사용법 및 useRef 변수에 타이머 ID 할당 가능
2. 배열로 Component 속성을 관리해서 LAB 선택을 따로 관리할 수 있음
3. 버튼에 따로 clearInterval() 를 줄 수 있음

- 어려웠던 점과 해결 방법
마운트의 개념이 헷갈렸지만 실습 코드와 개념을 복습하면서 해결

- AI 활용 내용 및 느낀 점
마운트 개념과 useEffect 문법에 대한 개념을 학습하는 용도로 사용. CSS 수정할 때 문법에 대한 질문을 했음.
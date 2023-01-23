![tetris](https://user-images.githubusercontent.com/110226567/214046509-0830e026-5866-43a5-b70c-141eeeb517ba.png)

# 🧱 Tetris

자바스크립트 테트리스 게임 👉 [Demo](https://imjone.github.io/tetris/)
<br><br>

## 📢 프로젝트 소개

### [추억의 테트리스 게임]

- 자동 낙하하는 블록을 움직여서 쌓아나가는 게임
- START 버튼 클릭 혹은 Enter키를 입력하여 게임 시작
- 블록이 가로로 꽉 채워지면 그 줄이 사라지고 점수 +1
- 블록이 맨 위까지 쌓여서 세로로 꽉 채워지면 게임 종료
<br><br>

## 🗨️ 사용 기술

![HTML](https://img.shields.io/badge/HTML-e34f26?style=flat-square&logo=HTML5&logoColor=white)
![css](https://img.shields.io/badge/CSS-1572b6?style=flat-square&logo=CSS3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-f7df1e?style=flat-square&logo=JavaScript&logoColor=white)
<br><br>

## 📋 주요 기능

### 1. 게임 시작

- 10 X 20 격자판 생성
- 게임 진행 시간을 기록하는 타이머 작동
- 새로운 블록 생성 및 렌더링

### 2. 게임 진행

- 일정 시간마다 블록 자동 낙하
- ⬇️ 키를 입력하여 블록 수동 이동
- ⬅️ ⬆️ ➡️ 키를 입력하여 블록 모양 변경
- Space bar 키를 입력하여 블록 드랍
- 드랍되어 바닥에 닿은 블록 위치 고정

### 3. 점수 계산

- 가로로 한 줄이 채워지면 해당 라인 삭제
- 삭제된 라인 한 줄당 점수 +1점 추가

### 4. 게임 메뉴

- 🏠 버튼 클릭 시 메인 페이지로 이동
- ↪️ 버튼 클릭 시 게임 처음부터 다시 시작

### 5. 게임 종료

- 블록이 세로로 맨 위까지 쌓인 경우
- 게임을 다시 시작하는 경우
<br><br>

## 😊 나의 회고록

### 💧 어려웠던 점 및 개선 사항

게임이 진행되는 과정을 코드로 어떻게 연결 지어서 작성해볼 수 있을지, 아이디어를 구현하는 것이 아직은 익숙지 않고 어렵게 느껴진다.
다음에 나올 블록을 미리 보여주는 기능까지 구현해보고 싶었지만, 시간 관계상 진행하지 못해서 아쉬움이 많이 남는다.
또한 다른 미니 게임 프로젝트에서 했던 것처럼 로직을 기능별로 모듈화하여 독립적으로 관리할 수 있도록 리팩토링 작업도 해보면 좋을 것 같다.
그러기 위해서는 자바스크립트와 더욱 친해져야 한다..!

### 🔥 배운 점 및 느낀 점

코드를 작성할 때 이 함수가 실행되면 어떠한 반환 값을 기대할 수 있을지를 차근차근 생각해보면서 로직을 이해하고,
기능을 함수 단위로 엮어나가는 연습을 할 수 있었던 정말 의미 있고 보람찬 프로젝트였다.
코드가 실행되는 순서를 따라가면서 어떠한 원리에 따라 동작하는지 알아가는 과정 자체가 참 흥미롭고 재밌다.
왜 함수가 자바스크립트의 꽃이라고 불리는지도 새삼 깨닫게 되었다.
클래스 문법을 능숙하게 사용할 수 있도록 더 자주 사용해봐야겠다.

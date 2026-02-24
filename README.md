# CSS
* html(구조), css(디자인), js(동적)
* html 작성 : `<body><tag 속성="값" 속성="값"></body>`
* css 작성 : `<head><style>tag {디자인속성:값; 속성:값;}</style></head>`
## css 선택자
* 태그 선택자 : `태그 {속성:값;}`
* 아이디 선택자 : `#아이디명 {속성:값;}`
* 클래스 선택자 : `.클래스명 {속성:값;}`
* 부모-자식 선택자 : `부모 > 자식 {속성:값;}` `div >h1 {}`
* 부모-자손 선택자 : `부모 자손 {속성:값;}` `div p {}`
* 형제 선택자 : `기준형제+선택형제 {속성:값;}` `h1+p {}`
* 다중 형제 선택자 : `기준형제~선택형제들 {속성:값;}` `h1~p {}`
* 모든 선택자 : `* {속성:값;}`
* 수열(nth) 선택자
    * 형제가 2개 이상일 때 원하는 형제를 선택하는 선택자 (공백 주지 않기)
    * `형제선택자:nth-child(n)` (n번째 형제)
    * `형제선택자:nth-child(odd)` : 홀수
    * `형제선택자:nth-child(even)` : 짝수
## css 선택자 우선순위(큰 순서>작은 순서)
* `<style>` >`#` > `.` > `tag`
1. `<tag style="">` 우선순위 높음 (이런 방식으로는 잘 사용하지 않음)
2. `#id {}`
3. `.class {}`
4. `tag {}` 우선순위 낮음
## css 본인 적용과 상속 적용 차이
* 자식이 2개 이상일 때 부모에 속성을 적용하는 것으로 자식에게 공통 값을 적용할 수 있다.
    * `ul-li*5` 관계 시 `ul {color:red;}` 부모 ul의 color를 li 자식에게 상속시킨다.
    * 꾸미려는 css 속성이 글자에 관련된 속성(글꼴, 글자크기, 글자색상 등)은 본인에게 직접 적용하는 것을 권장함.(우선순위가 꼬이기 때문)
## font
### font-family
* `font-family`:대표글꼴, 후보글꼴1, 후보글꼴2; | 대표 글꼴 문제 발생 시 대체해서 나갈 수 있도록 대기하는 후보 글꼴
* `font-family`:'나눔고딕','Noto Sans KR',sans-serif; | 나눔고딕>대표글꼴, Noto Sans KR>후보글꼴1, sans-serif>후보글꼴2(산세리프 글꼴 중 가져오도록)
### font-size
* em 단위는 부모의 크기를 상속받아서 자식의 크기를 함께 인식 | 부모 20em + 자식 10em > 자식 최종 크기 30em
* rem 단위는 부모 상관없이 나만의 크기를 인식 | 부모 20em 자식 10em > 자식 최종 크기 10em
* `font-size`: 글자 크기 | 기본 1em = 16px
### 그 외 font 관련 태그
* `line-height` : 행간 | 기본 100% = 1.0 150% = 1.5
* `font-style` : 글자 스타일 | italic = 기울이기
* `font-weight` : 글자 굵기 | 기본 400 = reguler
* `text-decoration` : 글자 꾸미기 | underline; = 밑줄
### 글꼴 사용 시 주의사항
* 모든 컴퓨터 기본글꼴(고딕, 궁서, 바탕 등)이 아니라면 반드시 웹글꼴을 사용하여 웹접근성을 높여줘야함.
* 웹글꼴 연결 순서는 작성한 css보다 반드시 위에 작성
* 글꼴명이 한글이거나 공백이 포함된 경우 따옴표('/") 붙여서 작성 | '나눔고딕','Noto Sans KR'
* `@font-face` : css파일에 기입하는 웹글꼴 링크. # 대신 @선택자를 사용함
## 자주 사용하는 css 속성 모음
* `width:0px` : 가로크기 (단위(vw, % 상대크기단위가능) 설정 필)
* `height:0px` : 세로크기 (단위(vh, % 상대크기단위가능) 설정 필)
* `padding:0px` : 안쪽 여백 설정 (피그마 AutoLayout 패딩)
* 한 쪽만 설정할 때 : padding_방향(left, right, top, bottom)
* `display:;` : 요소의 형태유형 변경속성
    * `block`, `inline`, `inline-block`
    * inline 변경가능요소 : h1, p, address 등 블록
        * `h1 {display:inline;}`
        * 내용만큼만 크기 인식
        * 옆으로 나열
    * block 변경가능요소 : a, span, em, del 등 인라인
        * `a {display:block;}`
        * 크기(w100%, h(Hug))와 여백값을 인식
        * 옆으로 정렬이 아닌 새로운 행으로 나열
    * inline-block 값은 모두 적용 가능
        * `h1 {display:inline-block;}`
        * `a {display:inline-block;}`
        * 크기와 여백값을 인식
        * 옆으로 나열, 넘치면 자동 줄바꿈됨.
    * `margin` : 바깥쪽(형제 사이) 여백(피그마 기준 **간격**)
    * `margin:10px;` : 모든 방향 10 통일
    * `margin:10px 20px;` : 상하/좌우
    * `margin:10px 20px 30px;` : 상/좌우/하
    * `margin:10px 20px 30px 40px;` : 상/우/하/좌 (시계방향)
    * **위 4개 속성 방향은 padding도 동일**
    * `margin:0 auto;` : 레이아웃 가운데배치(너비가 화면보다 작아야함)
# table HTML+CSS
* `table > tr > th or td`
* `tabel {width:300px}` 열이 3개일 경우 100씩 자동 분배
    * `th:nth-child(1) {width:50px;}`
    * 전체 너비 300 중 첫번째 열만 50을 가지고 나머지 값은 나머지 열들에게 자동 분배
    * (열 안 내용크기에 따라 달라짐)
* `width, height, padding` 속성은 같은 수평/수직 방향에 해당하는 열에 함께 적용됨.
    * 위 특징때문에 공통 여백 및 크기는 1행 라인에 작성
* `thead` : 제목행 그룹, th 위주로 구성된 제목행(tr) 묶을 때 사용
* `tbody` : 내용행 그룹, td 위주로 구성된 내용행(tr) 묶을 때 사용
* `tfoot` : 결과행 그룹, td 위주로 구성된 결과행(tr) 묶을 때 사용
## 행 그룹 포함 table 작성 순서
* `table` -> `thead` -> `tr` -> `th`
* `table` -> `tbody` -> `tr` -> `th`
* `table` -> `tbody` -> `tr` -> `td`
* `table` -> `tfoot` -> `tr` -> `td`
## 수평/수직 열 합치기
* 합치기 속성은 무조건 `th` 또는 `td` 태그에 입력가능!
* 수평 열 합치기
    * `<th colspan="합치는 열 개수">내용</th>`
    * 위 속성은 합치는 열 중 첫번째 시작태그에 작성하기
    * 그 외 나머지 칸은 지우거나 주석걸기
* 수직 행 합치기
    * `<td rowspan="합치는 행 개수">내용</td>`
### 선 종류
* `solid` : 실선 | ㅡ
* `dotted` : 점선 | . . . 
* `dashed` : 일자 점선 | - - -
## form 요소들의 동적인 편의 HTMl+CSS
### input 입력요소
* `<input autofocus placeholder="">`
    * autofocus : 페이지 접속 시 바로 커서 위치 **활성화**
    * placeholder : 안내메세지 표시
        * `input::placeholder {}` 안내메세지 디자인
    * `input:focus {}` 입력칸 활성화 표시 **디자인**
### button
* `<button type="button" 이벤트="자바스크립트명령어작성">`
    * 버튼에 이벤트 작성 시 반드시 type은 button(범용기능)
    * `onclick=""` : 클릭 시 "명령어" 실행 이벤트
    * `window.location.href='실행주소'`
        * (위) `a href="실행주소"`와 동일한 JS 명령어
    * `button:hover {}` : 버튼에 마우스 올렸을 시 디자인 변경
## background
* `background-size`
    * `contain` : 요소 안에 배경 이미지가 전부 나타나도록 가로 세로 크기 조정
    * `cover` : 배경 이미지로 요소의 크기를 모두 덮어 씌우는 형태로 적용
    * `직접 값 적용` : px / % 로 이미지 크기 직접 적용 px > 절대값 % > 상대값 */
* `background-repeat`
    * 화면보다 이미지가 작을 때 | no-repeat : 반복x | repeat-x : 가로축만 반복(y > 세로축만 반복)
    * background-position: right bottom ;/* x y */
* `background-attachment`
    * 스크롤에 따라 배경 고정유무 | 기본값 `scroll` | 고정 `fixed`
    * 공통 적용 시 한 번에 | 개별 적용 시 수열선택자 사용하여 각자 적용
# 웹글꼴 `<link>`, `@font-face`
## `<link>` 사용법, 특징
* `head` 태그 안 `reset.css` 연결보다 위에 작성
* `@font-face`에 비해 사용이 간편함
* 작성한 html에서만 사용할 수 있다는 단점이 있음
## `@font-face` 사용법, 특징
* `reset.css` 파일 내 가장 위쪽 라인에 작성
* `@font-face {`
    ------(필수요소)------
    * `font-family:'사용할 글꼴 이름 임의작성';`
    * `src:url(글꼴주소);`
    ------(선택요소)------
    * `font-weight:글꼴굵기(200~700 글꼴에 따라 다름);`
    * `font-style:기울기(normal, italic 등);`
    * `font-display:swap`;
    * `}`
* reset에 한 번 연결해두면 모든 html에서 사용 가능
* `@font-face {font-family:'사용할 글꼴명'}` (예) 컴퓨터 글꼴 설치 (reset에 작성할 때)
* `선택자 {font-family:'웹글꼴로 불러온 글꼴명'}` (예) 포토샵 글꼴 사용 (css에 작성할 때)
## CSS 레이아웃 정렬 속성
### display
* `display:block` :인라인을 수직으로 나열
* `display:inline-block` : 블록을 수평으로 나열
    * 기본 여백 3px 발생 -> 해결법 `margin-right:-3px`
### margin
* `margin:상하여백 auto` : 크기가 설정된 블록 또는 인라인을 화면 가운데 배치
### float
* `float:left` : 형제 요소들을 왼쪽으로 순차정렬
* `float:right` : 형제 요소들을 오른쪽으로 순차정렬
    * 2개 이상 작성 시 역순으로 정렬됨.
* `float:none` : float 제거
* `clear:both` : 이전 형제에 작성된 float 정렬 해제
### position
* `posirion:relative`
    *태그의 기존 위치에서 상/하/좌/우 로 약간의 이동이 필요할 때
    * 자식 또는 자손요소에 absolute가 있어서 부모 기준이 필요할 때
* `posirion:absolute`
    * 부모, 형제 요소와 겹치는 디자인 특징이 필요할 때
    * block요소에 absolute 설정 시 inline-block처럼 너비를 내용만큼 인식함->너비재입력
    * 부모 후보들(dl,dt)에게 추가 postion 설정 안할 시 body 기준으로 움직임
    * `dl dt p {position:absolute;}`
* `z-index`
    * absolute로 인해 겹쳐진 형제 요소들 사이의 중첩순서가 필요할 때
    * 0~999 작성가능 (단위작성없이 숫자만 작성)
    * position 속성이 없으면 z-index 적용 불가
## 가상 CSS 선택자 ::after, ::before
* 시각적인 목적으로 디자인 배경, 선 등의 요소가 필요할 때 HTML태그없이 CSS만으로 디자인을 만드는 선택자
* `부모선택자::after {}` -> 부모의 마지막 자식에 디자인 생성
* `부모선택자::before {}` -> 부모의 첫 번째 자식에 디자인 생성
### after, before 사용 시 필수속성
* `content:'';` -> 내용인식속성, 글자 필요한 디자인이 아닐 경우 '' 빈따옴표
* `display, background-color, width, height`
## 계산기 함수 `clac()`
* +,-,*,/,% 다양한 사칙연산 사용 가능
* 추가 괄호를 통한 복잡한 계산 가능
**연산자 앞 뒤 여백 필수** `1+1(X)` `1 + 1(O)`
* `width, height, margin, padding` 등 숫자 입력 속성 활용 가능
### calc() 활용 예시
* `li {width:calc(100% / 4);}`
    * 4개의 li를 같은 크기로 나누기
* `li {width:calc((100% - 30px) / 4);}`
    * 4개의 li에 각 10px 씩 사이여백을 주기 위해 전체 부모 100% 너비 중 10*3 총 30px을 빼고 나머지 값을 4로 나누기
    * `li {width:calc((100% - (10px * 3)) / 4);}`
* `a {display:block; height:calc(100% - 50px);}`
    * a의 크기를 인식하게 만들고 50px을 뺀 나머지 부모크기 주기
## vs code emmet 내장기능
* {} 안 붙이고 태그 - tab 으로 필수속성 자동 완성
    * 부모 관계 입력 시 `>` 로 작성 :: `div>a`
    * 형제 관계 입력 시 `+` 로 작성 :: `div>h1+a`
    * 형제 여러개 입력 시 `*`로 작성 :: `div>h1+a*3>p`
## 수평/수직 정렬 레이아웃 속성 Flex
### 정렬 순서
1. 정렬하고자 하는 **2개 이상의 형제관계** 대상 체크
    * `ul > li*5 > a` -> 형제 `li`
    * `dl > dt + dd*4 + dt + dd*2` -> 형제 `dt, dd`
    * `div > a*3 > span*2` -> 형제 `a`
2. 체크한 1번의 부모 체크
    * `ul > li*5 > a` -> 부모 `ul`
    * `dl > dt + dd*4 + dt + dd*2` -> 부모 `dl`
    * `div > a*3 > span*2` -> 부모 `div`
3. 부모에 메인축/교차축 확인하며 `display:flex` 부터 명령시작하기
### 정렬 방향과 줄바꿈 속성
* 주의사항 : `display:flex` 먼저 작성해야함.
* `flex-flow:row nowrap` : 기본값(메인축 수평, 줄바꿈 안함)
* `flex-flow:row wrap` : 메인축 수평, 가로크기에 따라 줄바꿈함
* `flex-flow:column nowrap` : 메인축 수직, 줄바꿈안함
* `flex-flow:column wrap` : 메인축 수직, 세로크기에 따라 줄바꿈함
* **메인축이란?** 부모 안 2개 이상의 형제 정렬 방향
* **교차축이란?** 부모 안 2개 이상의 형제 교차 방향(메인 반대축)
### 메인축 정렬 속성
* `justify-content:`
    * `flex-start` : 메인축이 수직이면 위, 수평이면 왼쪽
    * `flex-end` : 메인축이 수직이면 아래, 수평이면 오른쪽
    * `space-between` : 메인축이 수직이면 위-아래 양쪽끝, 수평이면 왼쪽-오른쪽 양쪽 끝
    * `space-around` : 메인축이 수직이면 위-아래 양쪽여백 주고 균등 배치, 수평이면 왼쪽-오른쪽 양쪽여백 주고 균등배치
    * `center` : 메인축이 수직이면 수직중앙, 수평이면 수평중앙
### 교차축 정렬 속성
* `align-items:` 교차축이 1줄일 때
    * `flex-start, flex-end, center` 위 메인축과 뜻 동일
* `align-content:` 교차축이 2줄 이상일 때
    * `flex-start, flex-end, center, space-between, space-around` 위 메인축과 뜻 동일, 값 동일
## 스크롤바 디자인
* Firefox
`html {scrollbar-width: 10px;;scrollbar-color: #222 #e73b3b;}`
* Opera
`html::-o-scrollbar {width: 10px;}`
`html::-o-scrollbar-thumb {background-color: #222;border-radius: 5px;}`
* Chrome, Safari, Edge 등 웹킷 기반 브라우저
`::-webkit-scrollbar {width: 10px;}`
`::-webkit-scrollbar-track {box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.3);}`
`::-webkit-scrollbar-thumb {background-color: #222;border-radius: 5px;}`
### 
* transition:애니메이션 적용속성 지속시간 딜레이;
* 기존 속성에 작성
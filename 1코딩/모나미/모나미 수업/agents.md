# 그리드
1. Grid: 웹사이트 레이아웃을 정렬하는 기준
2. Column: 콘텐츠가 배치되는 세로 영역
3. Gutter: 컬럼 사이의 간격
4. Margin: 콘텐츠 영역 바깥쪽 여백
5. columns: column으로 구성된 그리드, 그리드를 구성하는 여러 개의 세로 영역을 의미한다.

## html body 작성 순서
- header - main - footer 3가지로 나누어서 코드작성
- css에서도 body -> header -> main -> footer 순서대로 작성.
- css에서 body, header 사이에 ul,li / h,p / a / button / img / .con 기본으로 설정할 값을 작성해준다.
- css 속성
body, ul, li {
  padding: 0; margin: 0;
  list-style: none;
}

h1, h2, h2,h3, h4, h5, h6, p {
  margin: 0; font-weight: normal;
  font-size: inherit;
}
/* transparent : 투명 */
button {
  margin: 0; padding: 0;
  border: 0; background-color: transparent;
  color: inherit;
}
img {
  display: block;
  background-color: #f1f1f1;
}
.con {
  width: 1400px;
  padding-left: 20px; padding-right: 20px;
  display: flex;
  <!-- margin-left,right를 auto로 두어 가운데로 자동정렬 -->
  margin-left: auto; margin-right: auto;
}

/* 투명도 0~1 rgba : red, green, blue, alpha(투명도) */
header {
  background-color: rgba(0, 0, 0, 0.2);
}

- button을 넣을 땐 항상 type까지 설정해서 작성한다.
- img는 넣었을 때 인레이가 기본설정 되어 있어 css에서 block 으로 다시 적용해주고 배경색 #f1f1f1으로 설정해준다.

- 로고 박스를 만들 땐 주로 h 태그를 사용한다.

- nav 박스를 만들 땐 div. class 제목으로 사용하지 않는다. 구조를 정확히 작성해야 내용을 찾거나 시각 장애 있는 분들이 설명을 알아듣기 좋다.
- nav에 2차 메뉴가 있는 경우 네비-2차 메뉴 사이에 여백이 있으면 화면 연결이 끊길 수 있어 박스크기를 여백없이 만들어준다. (padding이나 width활용) + 같은 부모 박스에 있는 것들은 align-self: 로 따로 정렬

- 부모 태그에 높이 값을 적용했을 때 적용이 잘 안되면 height를 100%를 주거나 그 밑의 자식요소에서 적용하는 것이 좋다.
* div class="top-bar"
  - div class="con topbar-con" topbar-con에 높이 값 적용.

### 리스트 작성
- ul > li > a > (img)

- ul>li*3>a[target="_blank"][title="#"][href="#"] []대괄호를 통해서 안에 들어가는 내용 미리 작성
- "" 안에 #을 넣어서 넘어가는 실수 안생기게 해준다.
- 텍스트를 넣을 땐 <a>내용</a> 사이에 넣어준다.
- a target="_self" : 보고 있는 페이지에서 열기
- a taget="_blanlk" : 새로운 탭에서 페이지 열기
- a를 작성할 때는 title을 항상 넣어줘야 한다(접근성 때문)

#### css
1. content
- content를 활용해서 html 코드 복잡해지는걸 최소화해줌.
- after: li 안에 있는 a에 content 붙이는 행위(자식으로 들어옴) */
.topmenu>ul>li::after {content: "|";}
- ** after를 사용할 땐 항상 content를 넣어줘야 한다. 안에 내용은 비워두어도 상관없음.(content: "")
- nth-child li(번호) 번호를 입력해서 li 하나에만 content 붙이는 행위.
.topmenu>ul>li:nth-child(1)::after,
nth-child li(1)번에만 a뒤쪽에 content 붙임.

2. position
- relative : 배치된 곳을 기준 이동.
- absolute : relative를 기준으로 이동 ?

* position: relative와 position: absolute의 차이점
  - position: relative는 요소가 원래 위치를 유지하면서 top, left 등의 좌표 속성을 사용하여 자신이 위치한 곳을 기준으로 상대적으로 이동합니다.
  (이 경우 요소가 차지하는 원래 공간은 그대로 남아있습니다.)

  - position: absolute는 가장 가까운 위치 지정된 조상 요소를 기준으로 위치가 결정되며, 문서 흐름에서 제거되어 다른 요소와 상호작용하지 않습니다.
  (부모 요소를 기준으로 위치를 잡으려면 부모 요소에 position: relative를 선언하는 것이 일반적입니다.)

- transition
  
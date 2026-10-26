그리드 1400px
Gutter 22px
margin 2px

그리드 설정
- gutter, margin, column, columns


header - main - footer로 body 구성을 3가지로 나누어서 코드작성
css에서도 body -> header -> main -> footer 순서대로 작성.

/* transparent : 투명 */

- css 속성
body, ul, li {
  padding: 0; margin: 0;
  list-style: none;
}

h1, h2, h2,h3, h4, h5, h6, p {
  margin: 0; font-weight: normal;
  font-size: inherit;
}

button {
  margin: 0; padding: 0;
  border: 0; background-color: transparent;
  color: inherit;
}

.con {
  width: 1400px;
  padding-left: 20px; padding-right: 20px;
  display: flex;
  margin-left: auto; margin-right: auto;
}

/* 투명도 0~1 rgba : red, green, blue, alpha(투명도) */
header {
  background-color: rgba(0, 0, 0, 0.2);
}

main {
  border: 1px solid red
}

footer {
  background-color: rgba(0, 0, 0, 0.2);
}

- button을 넣을 땐 항상 type까지 설정해서 작성한다.

### 리스트 작성
- ul > li > a > (img)

ul>li*3>a[target="_blank"][title="#"][href="#"] []대괄호를 통해서 안에 들어가는 내용 미리 작성
#을 넣어서 넘어가는 실수 안생기게 해준다.
텍스를 넣을 땐 <a></a> a 사이에 넣어준다.

html 코드 복잡해지는걸 최소화해줌.
.topmenu>ul>li::after {
  content: "|";
}

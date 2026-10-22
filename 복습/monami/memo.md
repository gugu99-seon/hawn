전체 영역과 배치

| 대상 | 크기·여백 | 설명 |
|---|---|---|
| .head_top | 높이 58 + 아래 테두리 1 | 화면에서 차지하는 총높이는 59 |
| 아래 테두리 | 1px solid #eaeaea | 연한 회색 |
| .conwrap | width: 94%; max-width: 1400px | margin: 0 auto로 가운데 정렬 |
| .links | margin-top: 14px | 왼쪽 정렬 |
| .topmenu | margin-top: 20px | 오른쪽 정렬 |

현재 화면의 콘텐츠 폭은 1630, 내부 영역은 1400이라 좌우 여백이 각각 115입니다. 이 여백은 화면 너비에 따라 달라져요.

언어 선택 버튼

| 항목 | 실제 값 |
|---|---|
| 최종 외곽 크기 | 88 × 30 |
| CSS 크기 | width: 86px; height: 21px |
| 내부 여백 | padding-top: 7px |
| 테두리 | 1px solid #eaeaea |
| 모서리 | border-radius: 10px |
| 위치 | 내부 영역 왼쪽 0, 위쪽 14 |
| KOR 글꼴 | Montserrat, sans-serif |
| 글자 크기·굵기 | 11px, 400 |
| 글자 색상 | #000000 |

content-box 기준이라 높이는 21 + 위 패딩 7 + 테두리 2 = 30이 됩니다.

국기는 .this_lang의 배경 이미지로 왼쪽 10px에 배치돼요. .this_lang과 내부 a에 각각 padding-left: 15px이 있어 KOR 글자는 버튼 왼쪽에서 31px 떨어져 시작합니다. 화살표도 배경 이미지예요.

ENG 항목은 기본 상태에서 overflow: hidden으로 가려져 있고, .lang.on 상태에서는 CSS 높이가 36px로 늘어나 외곽 높이가 45px이 됩니다.

SNS 아이콘과 간격

| 항목 | 실제 값 |
|---|---|
| 아이콘 크기 | 각각 30 × 30 |
| 아이콘 사이 간격 | 7 |
| 언어 버튼 오른쪽 → 첫 아이콘 | 12 |
| 상단 여백 | 14 |
| 아이콘 아래 → 헤더 테두리 시작 | 14 |

간격은 gap이 아니라 다음 조합으로 만들고 있어요.

.sns { padding-left: 93px; }
.sns li { float: left; margin-left: 7px; }

첫 아이콘은 내부 영역 왼쪽에서 93 + 7 = 100px 위치에 시작하고, 언어 버튼 폭이 88px이므로 둘 사이가 12px입니다.

오른쪽 메뉴

| 항목 | 실제 값 |
|---|---|
| 글꼴 | Montserrat, sans-serif |
| 글자 크기·굵기 | 11px, 400 |
| 글자 색상 | #9b9a9a |
| 각 li 왼쪽 마진 | 10 |
| 각 li 왼쪽 패딩 | 12 |
| 텍스트 사이 간격 | 22 |
| 메뉴 영역 높이 | 20 |
| 텍스트 영역 높이 | 약 14 |

HOME → SITE MAP, SITE MAP → CONTACT US의 텍스트 사이 간격은 마진 10 + 패딩 12 = 22px이에요. 구분선은 두 번째·세 번째 li의 왼쪽 중앙에 들어간 배경 이미지입니다.

전체적으로 원본은 왼쪽·오른쪽 float 배치를 사용하고, 간격은 margin과 padding으로 조절하고 있어요.

지금 구조에서는 .head_top이 좌우를 나누고, .head_util-con이 언어 버튼과 SNS를 가로로 묶도록 설정하면 돼요.

먼저 선택자 두 곳을 수정해주세요. .body, .ul은 클래스 이름을 뜻하므로 HTML 태그에 적용하려면 점을 빼야 해요.

body {
    margin: 0;
    font-family: 'Pretendard', sans-serif;
}

ul, li {
    margin: 0;
    padding: 0;
    list-style: none;
}

기존 .con부터 아래 CSS는 다음처럼 바꿔보세요.

.head_top {
    height: 58px;
    border-bottom: 1px solid #eaeaea;

    /* 내부 영역의 좌우 여백 */
    padding: 0 max(3%, calc((100% - 1400px) / 2));

    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* 언어 버튼과 SNS를 가로로 배치 */
.head_util-con {
    display: flex;
    align-items: center;
    gap: 12px;
}

/* 테두리를 포함해 88 × 30 */
.lang {
    box-sizing: border-box;
    width: 88px;
    height: 30px;

    display: flex;
    justify-content: center;
    align-items: center;

    border: 1px solid #eaeaea;
    border-radius: 10px;

    font-size: 11px;
    font-weight: 400;
    color: #000;
}

/* SNS 아이콘을 가로로 배치 */
.sns_icon {
    display: flex;
    align-items: center;
    gap: 7px;
}

.sns_icon img {
    display: block;
    width: 30px;
    height: 30px;
}

/* 오른쪽 메뉴 */
.head_menu ul {
    display: flex;
    align-items: center;
}

.head_menu li {
    font-size: 11px;
    font-weight: 400;
    color: #9b9a9a;
}

/* 두 번째 메뉴부터 구분선과 여백 적용 */
.head_menu li + li {
    margin-left: 10px;
    padding-left: 11px;
    border-left: 1px solid #eaeaea;
    line-height: 10px;
}

현재 비어 있는 .head_menu에는 아래 내용을 넣으면 돼요.

<div class="head_menu">
    <ul>
        <li>HOME</li>
        <li>SITE MAP</li>
        <li>CONTACT US</li>
    </ul>
</div>

적용할 때 기억할 부분은 다음과 같아요.

- **display: flex**가 있어야 justify-content, align-items, gap으로 배치를 조절할 수 있어요.
- .sns_icon의 기존 flex-direction: column은 삭제하세요. 아이콘을 세로로 배치하는 속성이에요.
- .lang의 기존 padding-top: 10px도 삭제하세요. 위 코드에서는 align-items: center로 세로 중앙에 맞춰요.
- 현재 <div class="class">는 그대로 두어도 배치에 문제없지만, 의미를 알아보기 쉽게 class="sns"로 바꾸면 좋아요.

이렇게 하면 높이, 아이콘 크기, 언어 버튼과 아이콘 사이 간격을 분석한 값에 맞출 수 있어요. 다만 현재 글꼴은 Pretendard이고 원본은 Montserrat라 글자 모양과 폭에는 차이가 있어요.
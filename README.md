# HTML+CSS 26/06/22~
# 선택자종류
## 태그 선택자
* 태그명을 선택자로 사용하는 선택자
* `<h1></h1>` -> `h1 {속성:값;}`
## 클래스 선택자
* `<h1 class="title"></h1>` -> `.title {속성:값;}`
## 자식 선택자
* `<h1><span></span></h1>` -> `h1 >span {속성:값;}`
## 형제 선택자 + or ~
* `<div><a>1</a> <em>2</em> <del>3</del></div>`
* `div > a + em {}` 해석-> 부모div의 자식a의 인접형제 em선택
* `div > a ~ del {}` 해석 -> 부모div의 자식a의 형제 em+del선택
* `+` 는 바로 옆에 있는 형제태그만 인식한다.
* `~` 은 바로 옆 형제 포함 그 뒤에 모든 형제 태그들을 인식한다.
# 자주 쓰는 웹 글꼴 주소
## 노토산스 Noto Sans KR
* <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap" rel="stylesheet">
## 프리텐다드 pretendard
* <link rel="stylesheet" as="style" crossorigin href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard-dynamic-subset.min.css" />
# CCS 속성과 값, 활용 방법
## background
* `background-color` : 배경색상, 실제 배경색이 없어도 **영역구분용으로** 많이 사용
* `background-image:url()` : 배경 이미지, url()안에는 **상대경로로** 작성하기
* `background-repeat` : 배경이미지반복설정, 배경이미지가 **작은 경우만** 체크하기
* `background-size` : 배경이미지크기설정, 배경이미지가 들어간 요소보다 이미지가 작거나 클경우 사용
* `background-position` : 배경이미지위치설정, **size와 함께 무조건 사용하기, x y순서로 작성**
* `background-attachment`: 배경이미지스크롤속성, 스크롤이동 시 이미지 고정시키고 싶을 때만 사용
* (위) 배경속성 작성 시 주의사항, 일반 이미지태그와 다르게 요소의 크기가 자동으로 연장되지 않으므로 **반드시 width, height 크기를 함께 작성해야 합니다!**
## font
* `font-family` : 글꼴설정, 2개 이상 글꼴 작성하기 (대기개념)
* `font-size` : 글자크기, px>em으로 전환해서 작성하기
* `font-weight` : 글자굵지, 보통(400) +- 100 설정
* `letter-spacing` : 자간, -2% -> -0.02em
* `line-height` : 행간, 100% -> 1, 150% ->1.5
* `color` : 글자색상
## box
* `border` : **두께 모양 색상** 순서로 작성 예) 1px solid #000; 세미콜론은 맨뒤
* `padding` : 피그마의 오토레이아웃 패딩과 동일, 부모와 자식 사이 안쪽여백
* `margin` : 피그마의 오토레이아웃 간격과 동일, **형제와 형제 사이 바깥쪽 여백**
* `width` : 가로크기 (px, %, vw 단위 사용 가능)
    * 피그마 w 내용에 맞추기 설정 시) width:max-content;
    * 피그마 w 채우기 설정 시 예) width:100%;
    * 피그마 w 고정값(숫자 직접 입력 시) 설정 시 예) width:500px
* `height` : 세로크기 (위 width 설명과 같음)
* `border-radius` : 모서리 둥글기(피그마의 모서리반경과 같음), px 단위 사용하기
## 행간, 자간
* `line-height` : 행간
* `letter-spacing` :자간
## layout
### 수평, 수직 정렬하기
* `text-align` : 수평정렬(left, center, right, justify)
* `line-height` : 글자가 한줄이고 높이가 고정되어있을 때 높이값 px를 넣어 수직중앙정렬설정
### Flex 레이아웃 속성
#### 적용방법
1. 정렬하고자 하는 부모-자식 대상을 확인한다.
2. 2개이상의 자식요소가 수평, 수직 어느방향으로 정렬되었는지 확인한다.
3. 부모요소에게 `display:flex` 속성을 먼저 적용한다.
4. 2번에서 확인한 방향을 메인축으로 지정하고 줄바꿈을 설정한다. `flex-flow`
5. 메인축 정렬, 교차축 정렬속성을 확용하여 마무리를 진행한다.
#### 주요 속성과 주의사항, 팁
* `dispaly:flex` : 정렬 자식들의 부모에게 설정하는 flex 시작값(필수)
* ` flex-flow : 방향 줄바꿈` : 메인축의 방향과 줄바꿈을 설정하는 묶음값(필수)
* `justify-content : 메인축정렬값`
    * flex-flow에서 설정된 메인축방향에 따라 정렬을 정하는 속성
    * 메인축 row인 경우 : 왼쪽, 가운데, 오른쪽, 양쪽 끝, 균등여백
    * 메인축 column인 경우 : 위, 가운데, 아래, 양쪽 끝, 균등여백
    * 왼쪽, 위(flex-start), 가운데(center), 오른쪽,아래(flex-end)
    * 양쪽 끝(space-between), 균등여백(space-arond)
* `align-content :교차축 1줄이상 정렬값`, `align-items : 교차축 1줄 정렬값`
    * flex-flow의 값이 `nowrap`이면 ->`align-items`
    * flex-flow의 값이 `wrap`이고 교차죽이 2줄 이상이면 -> `align-content`
    * **align-content만 space-between, space-around 값 사용가능**
    * `flex-end, flex-start, center`는 **align-content, item 모두 사용가능**
    * `flex-flow : row nowrap; align-item:flex-end`
        * 해석) 수평 한줄 맨밑줄 / 선생님 해석 `메인축기 수평, 자식들 줄바꿈 안함, 교차축 수직, 교차축방향으로 아래쪽에 자식배치`
    * `flex-flow:column wrap; align-content:center`
        * 해석) 수직 줄바꿈 가운데 / 선생님 해석 
        메인축이 수직, 자식들 줄바꿈 함, 교차축 수평, 교차축방향으로 가운데에 자식 2줄 이상 배치
### position
#### position : absolute;
* 피그마에서 **오토레이아웃무시** 기능으로 **부모 프레임위치에서 상대적으로 위치를 맞췄을 때** 사용
1. 태그 상의 부모 후보들 중에(부모, 조상 모두 포함) 원하는 기준 대상을 `position` 속성으로 설정한다.
2. 1번 기준 설정 완료 후 실제 움직이고 싶은 대상에 `absolute`를 설정해서 `left, top, right, bottom` 선택옵션을 통해 위치를 이동한다.
#### position : fixed;
* 피그마에서 **오토레이아웃무시->프로토타입 위치(고정)->좌표설정**한 경우
1. body 태그의 자식 위치로 원하는 고정 목적 태그를 작성한다.
2. body는 기본구조태그로 `position:reletive;` 설정이 필요없다.
3. 1번에서 작성한 태그의 `position:fixed;`와 가까운 좌표값을 입력한다.
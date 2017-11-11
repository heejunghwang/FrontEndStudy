* CSS
  * Cascading Style Sheets
  * 목적 : 콘텐츠 시각적 표현



* CSS 스펙 상태
  * CSS 레벨 구분이 모호



* Rule Set(룰셋)

  ~~~
  h2, h2 {	//셀렉터
    font-family : "굴림" //프로퍼티
  }
  ~~~


* 예)
[**'font-style'**]()

| *Value:*          | normal \| italic \| oblique \| [inherit](https://www.w3.org/TR/CSS2/cascade.html#value-def-inherit) |
| ----------------- | ---------------------------------------- |
| *Initial:*        | normal                                   |
| *Applies to:*     | all elements                             |
| *Inherited:*      | yes                                      |
| *Percentages:*    | N/A                                      |
| *Media:*          | [visual](https://www.w3.org/TR/CSS2/media.html#visual-media-group) |
| *Computed value:* | as specified                             |


* CSS 스펙의 프로퍼티 정의 형태

  * 값 : 프로퍼티 값
  * 초기값
  * 상속
  * 퍼센트
  * 미디어
  * 계산값



* 주요정보 value
  * 평가 우선순위
    * 작성위치 > && > ||
    * Ab | c || d && ef ==> [ab] | c || d &&ef] // (참고: &가 우선순위가 있음)
  * 변경자
    * 모든 타입, 키워드, 그룹[] 에 적용
    * *는 0번 이상 적용
    * +는 그룹을 1번 이상 적용(필수값)
    * ?는 그룹 적용 선택(option)
  * 예:[ [ [<'font-style'>](https://www.w3.org/TR/CSS2/fonts.html#propdef-font-style) || [<'font-variant'>](https://www.w3.org/TR/CSS2/fonts.html#propdef-font-variant) || [<'font-weight'>](https://www.w3.org/TR/CSS2/fonts.html#propdef-font-weight) ]? [<'font-size'>](https://www.w3.org/TR/CSS2/fonts.html#propdef-font-size) [ / [<'line-height'>](https://www.w3.org/TR/CSS2/visudet.html#propdef-line-height) ]? [<'font-family'>](https://www.w3.org/TR/CSS2/fonts.html#propdef-font-family) ] | caption | icon | menu | message-box | small-caption | status-bar | [inherit](https://www.w3.org/TR/CSS2/cascade.html#value-def-inherit)
* 쇼트핸드 프로퍼티

  * 하나의 프로퍼티에 다수의 프로퍼티 정의
* 벤더 식별자 : 브라우저별로 (ex:-webkit 등)
* At-rules

  * https://css-tricks.com/the-at-rules-of-css/
* Default value는 웬만하면 건들지 말것. (예: h1의 사이즈 바꾼다던지..)



* Cascade 의미 : 저자(author), 사용자, 브라우저 타입을 규칙에 따라 적용하는 것





* casecade 규칙
  * 다큐먼트에 DOM 생성
  * DOM 트리로 CSS용 박스 모델 생성
  * 생성한 박스 모델에 프로퍼티 값 추가
* 우선순위

  * 브라우저 디폴트 스타일 시트
  * 사용자 스타일 시트
  * 개발자 스타일 시트
  * 개발자 !important
  * 사용자 !important



* 스타일 시트 적용 순위가 같으면
  * 스타일 시트 적용 점수 계산
  * 점수가 많은 것을 우선 적용









































* CSS 네이밍
  * BEM : Block__element--modifier
    * .navbar{}
    * .navbar__item{}
    * .navbar__item—active{}
  * BEM 장점
    * 모듈화
    * Flat CSS
    * 사이드 이펙트가 없음
    * 논리적으로 보임



* CSS 아키텍쳐 : Atomic CSS
  * https://acss.io/



*  Sass

  * 변수를 가질 수 있음 (아래예제에서 $primary-color)

  * 상속가능(@extend)

  * 아래예제에서 movie-card__image 이런식으로 class 사용하면, 스타일 적용 가능(&기능)

    ~~~css
    $primary-color:red;
    .border{
      border : $primary-color
    }

    .movie-card{
      	&__image{
          @extend .border
      	}
    }
    ~~~

    ​

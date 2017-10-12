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

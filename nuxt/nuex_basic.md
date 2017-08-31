# NUXT 기본

- Vue CLI 설치
      npm install -g vue-cli
- Nuxt.js 예제 생성
      vue init nuxt-community/starter-template my-project 
      cd my-project
      npm install
- 프로젝트 실행
      npm run dev
  
- 템플릿
  - 미리 제공되는 템플릿 확인
      vue list
- 폴더 구조
  - assets : css, js 파일들 넣으면 됨
  - components
  - layouts
  - middleware
  - pages : 실제 바인딩 되는 페이지  (특이하게도, 라우팅과 뷰를 포함)
  - store
  - utils
- 라우팅(Routing) 원리
  - page 디렉토리 내 Vue 파일 기반으로 vue-router 설정을 자동으로 생성됨
  - 따라서, 디렉토리가 기본 라우팅으로 생각하면 됨
      pages/
      	test/
      		index.vue
      
      => localhost:3000/test/index 실행시, index.vue로 바인딩 됨.
  - 동적 라우팅의 경우, _를 파일명 앞에 붙이면 됨.



- CSS 적용하기 (예: bootstrap 4 적용)
  1. asset 폴더 하위에 css 파일 넣어두기
  2. nuxt.config 에 css 설정
      module.exports = {
        head: {
          title: 'tes-app'
        },
        css: [
          '~/assets/css/bootstrap.css'
        ],
        //..중략
      }
  

  ~~~
  Document
  	--- Layout
  		-- Page 
  ~~~

  * Document

    * 전체적인 HTML 파일

  * Layout

    * 메인 레이아웃 확장 및 사용자 정의 레이아웃 설정 가능
    *  Vue Component + Nuxt 옵션 : 미들웨어, head

  * Page

    * 모든 Page 컴포넌트는 Vue 컴포넌트임.

    *  Vue Component, Nuxt 추가 옵션(asyncData, fetch, hed, layout, middleware, scollToTop, transition, validate)

    * 기본으로 제공하는 API

      | 속성          | 설명                                       |
      | ----------- | ---------------------------------------- |
      | asyncData   | 서버사이드에서 데이터를 가져와 랜더링하고 싶을 경우, 컴포넌트 데이터를 세팅하기전에 비동기 처리할 수 있도록 하는 메소드 (참고:data 메소드 내부에서 컴포넌트 인스턴스에 this를 이용하여 접근해서는 안됩니다. 왜냐면, data 메소드는 컴포넌트가 인스턴스화 되기 전에 불려지기 때문입니다.) |
      | fetch       | 페이지가 렌더링되기 전에 데이터를 스토어에 넣기 위해 사용, data 메소드와 비슷 |
      | head        | 헤더와 html 속성 업데이트                         |
      | layout      | `layouts` 폴더에 정의된 레이아웃을 지정할 수 있습니다.      |
      | transition  | 페이지를 이동하는 동안에 트랜지션/에니메이션을 발생             |
      | scrollToTop | 기본값은 `false` 입니다. 페이지를 렌더링하기 전에 페이지를 맨 위로 스크롤할 것인지를 나타내며, 중첩 라우트를 위해 사용됩니다. |
      | validate    | 동적 라우트에 대한 유효성을 검사합니다.                   |
      | middleware  | 이 페이지에 대한 미들웨어를 설정하면, 미들웨어는 페이지를 렌더링하기 전에 호출 |

  * Ajax 추가해보기

    ~~~
    npm install ajax --save
    ~~~

    ​

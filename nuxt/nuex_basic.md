# NUXT

* Vue CLI 설치

  ~~~
  npm install -g vue-cli
  ~~~

* Nuxt.js 예제 생성

  ~~~
  vue init nuxt-community/starter-template my-project 
  cd my-project
  npm install
  ~~~

* 프로젝트 실행

  ~~~
  npm run dev
  ~~~

  ​

* 템플릿

  * 미리 제공되는 템플릿 확인

  ~~~
  vue list
  ~~~

* 폴더 구조

  * assets : css, js 파일들 넣으면 됨
  * components
  * layouts
  * middleware
  * pages : 실제 바인딩 되는 페이지 (특이하게도, 라우팅과 뷰를 포함)
  * store
  * utils

* 라우팅(Routing) 원리

  * page 디렉토리 내 Vue 파일 기반으로 vue-router 설정을 자동으로 생성됨
  * 따라서, 디렉토리가 기본 라우팅으로 생각하면 됨

  ~~~
  pages/
  	test/
  		index.vue

  => localhost:3000/test/index 실행시, index.vue로 바인딩 됨.
  ~~~

  * 동적 라우팅의 경우, _를 파일명 앞에 붙이면 됨.



* CSS 적용하기 (예: bootstrap 4 적용)

  1. asset 폴더 하위에 css 파일 넣어두기
  2. nuxt.config 에 css 설정

  ~~~
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

  ​

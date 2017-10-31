# Ajax

 

# XMLHttpRequest객체

클라이언트와서버 간의 데이터 요청 및 응답 처리 담당, 가장 먼저 생성해야하는 객체임

*GET/POST방식

*동기, 비동기

*데이터 교환방식 : CSV, XML,JSON 등

 

## Ajax를 이용한 클라이언트와 서버 간의 데이터 연동

1. XMLHttpRequest(요청) 객체 생성

   참고) XMLHttpRequest 객체는 HTTP 요청을 더 잘 제어할수 있도록 개발됨.

~~~
XMLHttpRequest- 서버

createXMLHTTPObject();

~~~



2. 처리 결과를 받을 이벤트 리스너 등록

- onreadystatechange

 

3. 서버로 보낼 데이터 생성

 

4. 클라이언트와 서버 간의 연결 요청 준비(open() 메서드 이용) 

- 서버로보낼 데이터 전송 방식 선택(GET/POST)

      예) var data = “id=ddadn”&pw=sdk”;

             request.open(“GET”,“test.php?”+data, true);

 
      예) request.open(“POST”, “test.php”, true);

           reqeust.setRequestHeader(“Contenet-Type”,“application/x-www-form-urlencoded”);

            //헤더에 콘텐츠 타입이 form_urlencoded로 지정해야함

 

    -서버응답(동기, 비동기) 선택

     예) xmlHttp.open(“GET”, “test.php”, false); //false의 값은 비동기의 의미

     참고) 자바스크립트 인터프리터는 본질적으로 단일 스레드 방식이므로, Ajax 애플리케이션요청을 항상 “비동기”로 만드는 것이 좋다.

 

5. 실제 데이터 전송

    sned() 메서드 사용

 

6. 응답처리

   응답정상적으로 끝났는지 확인

    xmlHttp.readyState 값 4, xmlHttp.status 값 200인 경우

 

7. 데이터 처리

    -CVS와 JSON의 경우 : responseText 프로퍼티 사용

    - XML인경우 : responseHTML 프로퍼티 사용

 

### Ajax라이브러리

- Dojo, MochiKit, jQuery($.ajax()) 함수 등

 

### 참고) Prototype

* An object-oriented JavaScript framework
* Dynamic web 애플리케이션을 위한 자바스크립트프레임워크임. 
* OO프레임 워크, 확장된 Ajax, 구조화된 프로그래밍, 쉬운 DOM 조작 등을 지원함
* Prototype사용법

- [http://prototypejs.org/download](http://prototypejs.org/download)에서 prototype.js 다운

-HTML페이지에 아래와 같이 사용

~~~
<script type="text/javascript" src="/path/to/prototype.js"></script>
~~~



### jQuery.ajax()

* 비동기 HTTP(Ajax) 요청을수행하기 위하여 사용
* $.ajax() 리턴값 => jQuery XMLHttpRequest (jqXHR) (XMLHttpRequest 상속)

   jQuery XMLHttpRequest은responseText, responseXML 속성과

   getResponseHeader() 메소드를 포함한다.

* Datatype 옵션
  * text, html로 설정되어 있을땐,단순히 sucess handler로 전달됨. jqXHR객체중  repsoneText 속성사용
  * xml로 설정되어 있을땐->jQuery.parseXML(XMLDocument)로 응답이 파싱됨. jqXHR객체 중 repsoneXML 속성 사용
  * json으로 설정되어 있을때->jQuery.parseJSON(객체)로 응답이파싱됨. jqXHR객체 중  repsoneXML 속성 사용
* Type 옵션 : get/post
* data 옵션 : key/value형태로 넘김

  예) key1=value1&key2=value2, {key1:'value1', key2: 'value2'}

* Callback 함수 큐 : beforeSend, error,dataFilter,success ,complete 등

 

 

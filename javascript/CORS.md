# CORS


* Same-Origin Policy

  - XMLHttpRequest로 다른 웹페이지 접근할 때 같은 출처의 페이지에만 접근이 가능
  - 같은 출처 : 프로토콜, 호스트명, 포트

* 해결방법?

  * 크롬 플러그인 설치

    ~~~
    https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en
    ~~~

  * 서버에서 설정(Spring)

    * 모든 요청 허용하는 방식
    * 링크 : https://spring.io/guides/gs/rest-service-cors/


    * 컨트롤러에서 `@CrossOrigin` annotation 사용 예

      ~~~
          @CrossOrigin(origins = "http://localhost:9000")
          @GetMapping("/greeting")
          public Greeting greeting(@RequestParam(required=false, defaultValue="World") String name) {
              System.out.println("==== in greeting ====");
              return new Greeting(counter.incrementAndGet(), String.format(template, name));
          }
      ~~~

    * 글로벌에서도 설정 가능


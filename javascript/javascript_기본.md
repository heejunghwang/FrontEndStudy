# javascript 기본

* defer 사용시 script 실행순서 IE마다 다름.

* javascript 주소창(URL)에서 실행가능. (북마클릿)
javascript:http://~~


* 즉시 실행함수 : 전역의 오염을 막음

* 괄호연산자 : 연산결과 리턴, function 리턴
~~~
   (1+1)
   (function(){})()
   
   ({
	a:1,
	b:function(){
		return c;
	},
	init:function(){
		this.a = x + this.b();
		return this;
	}
   }).init(4)
   
~~~

~~~
* functino a(){
	var x = y = 3; //y는 전역변수임
}
~~~

# JavaScript에서의 메모리 관리

- 하드웨어 레벨에서 메모리란?
  - flip flops로 구성되어 있음.
  - 개념적으로는, 컴퓨터 메모리는 읽고 쓸 수 있는 거대한 bit 배열이라고 생각하면됨.
  - 메모리에는 많은 것들을 저장할 수 있음
    - 프로그램에서의 변수나 데이터
    - 운영체제를 포함한 프로그램의 코드
  - 프로그램에서는 stack 공간에 메모리를 할당하고, 종료할때는 LIFO(last-in, first out) 순서로 삭제.
- Dynamic 할당
~~~
	int n = readInput(); // reads input from the user
~~~
	위와 같은 코드에서는 컴파일러가 얼마나 많은 메모리가 필요한지 모름.
	- stack 에 변수를 할당할 수 없음.
	- 명시적으로 OS에게 런타임시 얼마나 필요한지가 알려줘야함. -> 이것을 heap 공간이라함.
- static allocation, dynamic allocation 비교
	- stack
		- 사이즈가 컴파일시 필요
		- 컴파일시에 수행
		- stack에게 물어봄
		- FILO
	- dynamic
		- 사이즈는 컴파일시 필요 없음
		- 런타임시 수행
		- heap에 할당
		- 할당 순서는 없음
- dynamic memory 할당을 이해하기 위해서는 pointer 이용 필요.

- 메모리 할당 알아서 해줌
~~~
var n = 374; // allocates memory for a number
var s = 'sessionstack'; // allocates memory for a string 
var o = {
  a: 1,
  b: null
}; // allocates memory for an object and its contained values
var a = [1, null, 'str'];  // (like object) allocates memory for the
                           // array and its contained values
function f(a) {
  return a + 3;
} // allocates a function (which is a callable object)
// function expressions also allocate an object
someElement.addEventListener('click', function() {
  someElement.style.backgroundColor = 'blue';
}, false);
~~~

- 메소드 할당
~~~
var s1 = 'sessionstack';
var s2 = s1.substr(0, 3); // s2 is a new string
// Since strings are immutable, 
// JavaScript may decide to not allocate memory, 
// but just store the [0, 3] range.
var a1 = ['str1', 'str2'];
var a2 = ['str3', 'str4'];
var a3 = a1.concat(a2); 
// new array with 4 elements being
// the concatenation of a1 and a2 elements
~~~
- Garbage collection
	 - 언제불필요한지 알 수 없음.
	 - Garbage collection 구현은 일반적인 문제를 해결하는데 제한됨.
	 
	 - 메모리 참조
	- garbage collection 알고리즘은 참조에 의존함.
	- 자바스크립트의 object들은 prototype을 참조(묵시적 참조)와 프로퍼티의 값(명시적 참조)가 있음
- 자바스크립트의 흔한 누수 타입
1. Global variables
-  the global object is window
~~~
// CASE 1
function foo(arg) {
    bar = "some text";
}

//위와 아래는 동일

function foo(arg) {
    window.bar = "some text";
}


//CASE 2
function foo() {
    this.var1 = "potential accidental global";
}
// Foo called on its own, this points to the global object (window)

// rather than being undefined.
foo();
~~~


2. Timers or callbacks that are forgotten
~~~
var serverData = loadData();
setInterval(function() {
    var renderer = document.getElementById('renderer');
    if(renderer) {
        renderer.innerHTML = JSON.stringify(serverData);
    }
}, 5000); //This will be executed every ~5 seconds.
~~~

3. Closures
~~~
var theThing = null;
var replaceThing = function () {
  var originalThing = theThing;
  var unused = function () {
    if (originalThing) // a reference to 'originalThing'
      console.log("hi");
  };
  theThing = {
    longStr: new Array(1000000).join('*'),
    someMethod: function () {
      console.log("message");
    }
  };
};
setInterval(replaceThing, 1000);
~~~

4. Out of DOM references

~~~
var elements = {
    button: document.getElementById('button'),
    image: document.getElementById('image')
};
function doStuff() {
    elements.image.src = 'http://example.com/image_name.png';
}
function removeImage() {
    // The image is a direct child of the body element.
    document.body.removeChild(document.getElementById('image'));
    // At this point, we still have a reference to #button in the
    //global elements object. In other words, the button element is
    //still in memory and cannot be collected by the GC.
}
~~~
	 
- 참고 링크 : https://blog.sessionstack.com/how-javascript-works-memory-management-how-to-handle-4-common-memory-leaks-3f28b94cfbec

1. Binary 설치법
yum install npm

2. Source 컴파일해서 설치법
~~~
//다운로드
wget http://nodejs.org/dist/v0.10.24/node-v0.10.24.tar.gz

//압축해제
tar zxvf node-v*.tar.gz
cd node-v*

// autoconfig 실행 & compile
./configure
make

// 설치
make install
~~~

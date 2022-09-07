# JVM은 무엇이며 자바 코도는 어떻게 실행하는 것인가
## JVM이란 무엇인가
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0kg24%2Fbtq4YOOQH4J%2FEF2ISOpkYA36a1flwtLEmK%2Fimg.png)
🚀 Java Virtual Machine : OS에 상관없이 Java를 인식하고 생성된 바이트 코드(.class)를 기계어로 전달해주는 가상 컴퓨터

## 컴파일 하는 방법
🚀 .java -> .class(Java bytecode)
* Java Compiler : JDK를 설치하면 javac.exe(bin 폴더 안에 존재)라는 실행 파일 형태로 설치됨
* javac 명령어 : .class 파일 생성

## 실행하는 방법
🚀 java 명령어 : JVM을 실행시켜 .class 파일을 실행시킨다.

## 바이트 코드란 무엇인가
🚀 JVM이 이해할 수 있는 언어로 변환된 자바 소스코드

* 자바 컴파일러에 의해 변환된 코드의 명령어 크기가 1바이트라서 자바 바이트 코드라고 불림

## JIT 컴파일러란 무엇이며 어떻게 동작하는지
🚀 Just-In-Time compliation 또는 Dynamic Translation(동적 번역) : 프로그램을 실제 실행하는 시점에 기계어로 번역하는 컴파일러

* 인터프리터 방식의 단점을 보완하기 위해 도입 -> 인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일하여 기계어로 변경하고, 이후에는 해당  부분을 더 이상 인터프리팅 하지 않고 기계어로 직접 실행하는 방식
* 기계어(컴파일된 코드)는 캐시에 보관하기 때문에 빠르게 수행 가능 -> 수행 속도 : JIT 컴파일러 컴파일 > 바이트 코드 인터프리팅
* JIT 컴파일러를 사용하는 JVM은 해당 매서드가 얼마나 자주 수행되는지 체크하고 자주 사용되는 것들만 컴파일 수행

🌱 실제 바이트 코드를 실행하는 시점에서 JVM(정확히는 JRE)이 바이트 코드를 JIT 컴파일을 통해 기계어로 변환

## JVM 구성 요소
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtclVx%2Fbtq4Xfml6Dy%2Fnzb5xxlGG1fr5iBGUMv77K%2Fimg.png)

* 클래스 로더(Class Loader)
* 실행 엔진(Execution Engine)
  * 인터프리터(Interpreter)
  * JIT 컴파일러(Just-In-Time)
  * 가비지 콜렉터(Garbage collector)
* 런타임 데이터 영역(Runtime Data Area)

## JDK와 JRE의 차이

# 자바 데이터 타입, 변수 그리고 배열
## 프리미티브 타입 종류와 값의 범위 그리고 기본 값
## 프리미티브 타입과 레퍼런스 타입
## 리터럴
## 변수 선언 및 초기화하는 방법
## 변수의 스코프와 라이프 타임
## 타입 변환, 캐스팅 그리고 타입 프로모션
## 1차 및 2차 배열 선언하기
## 타입 추론, var

# 연산자
## 산술 연산자
## 비트 연산자
## 관계 연산자
## 논리 연산자
## instanceof
## assignment(=) operator
## 화살표(->) 연산자
## 3항 연산자
## 연산자 우선 순위
## (optional) Java 13. switch 연산자

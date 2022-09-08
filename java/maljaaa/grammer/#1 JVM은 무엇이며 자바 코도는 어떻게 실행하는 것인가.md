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

* 클래스 로더(Class Loader)<br>
-> JVM 내로 클래스 파일(.class)을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈<br>
-> 클래스를 처음으로 참조할 때, 해당 클래스를 로드하고 링크하는 역할<br><br>

* 실행 엔진(Execution Engine)<br>
-> 클래스를 실행시키는 역할<br>
-> 바이트 코드를 실제로 JVM 내부에서 기계가 실행할 수 있는 형태로 변경<br><br>
  
  * 인터프리터(Interpreter)<br>
  -> 자바 바이트 코드를 명령어 단위로 읽어서 실행<br>
  -> 단점 : 한 줄씩 수행하기 때문에 느림<br><br>
  
  * JIT 컴파일러(Just-In-Time)<br>
  -> 인터프리터 방식으로 실행하다가 자주 사용하는 부분은 컴파일하여 기계어로 변경하고 다음 실행에서 기계어로 직접 실행하는 방식<br><br>
  
  * 가비지 콜렉터(Garbage collector)<br>
  -> 더 이상 사용되지 않는 인스턴스를 찾아 메모리에서 삭제<br><br>
  
* 런타임 데이터 영역(Runtime Data Area)<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcEjHLD%2Fbtq4YtqCAGY%2FrrVrI45UWSH2LqslkP8Wg0%2Fimg.png)
  * PC Register<br>
  -> Thread가 시작될 때 생성되며 생성될 때마다 생성되는 공간으로, 스레드마다 하나씩 존재<br>
  -> Thread의 다음 명령어를 기록 & 현재 수행 중인 JVM 명령의 주소 가짐<br><br>
  
  * JVM 스택 영역<br>
  -> 프로그램 실행 과정에서 임시로 할당되었다가 메소드를 빠져나가면 바로 소멸되는 특성의 데이터(메소드 안에서 사용되는 값, 호출된 메소드의 매개변수, 지역변수, 리턴 값 및 연산 값 등)를 저장하기 위한 영역<br><br>
  
  * Native method stack<br>
  -> 자바 프로그램이 컴파일되어 생성되는 바이트 코드가 아닌 실제 실행할 수 있는 기계어로 작성된 프로그램을 실행시키는 영역<br>
  -> JAVA가 아닌 다른 언어로 작성된 코드를 위한 공간<br><br>
  
  * Method Area(= Class area = Static area)<br>
  -> 클래스 정보를 처음 메모리 공간에 올릴 때 초기화되는 대상을 저장하기 위한 메모리 공간<br><br>
  
    * Runtime Constant Pool<br>
    -> 상수 자료형을 저장하여 참조하고 중복을 막는 역할<br><br>
  
  * Heap 영역<br>
  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmxiE4%2Fbtq4Y5pwyCR%2F3nO3XIf20wUUTrzMKvn5yk%2Fimg.png)<br>
  -> 객체를 저장하는 가상메모리 공간<br>
  -> new 연산자로 생성되는 객체와 배열을 저장<br><br>
   
    * Permanent Generation<br>
    -> 생성된 객체들의 정보의 주소값이 저장된 공간<br>
    -> Reflection(구체적인 클래스 타입을 알지 못해도, 컴파일된 바이트 코드를 통해 역으로 클래스의 정보를 알아내어 사용 가능)을 사용하여 동적으로 클래스가 로딩되는 경우에 사용<br><br>
    
    * New/Young 영역(가비지 콜렉터에 의해 사라짐)<br>
    -> 생명 주기가 짧은 '젊은 객체'를 GC(가비지 콜렉트 = Minor GC) 대상으로 하는 영역<br><br>
     
     * Eden<br>
     -> 객체들이 최초로 생성되는 공간<br><br>
     
     * Survivor 0, 1<br>
     -> Eden에서 참조되는 객체들이 저장되는 공간<br><br>
    
    * Old 영역(가비지 콜렉터에 의해 사라짐)<br>
    -> 생명 주기가 긴 '오래된 객체'를 G(가비지 콜렉트 = Major GC)C 대상으로 하는 영역<br>
    -> Minor GC에 비해 속도가 느림<br><br>
    
## JDK와 JRE의 차이
### JDK(Java Development Kit, 자바 개발 키트)
🚀 Java를 사용하기 위해 필요한 모든 기능을 갖춘 Java용 SDK(Software Development Kit)
* JDK는 JRE를 포함하고 있음
* 컴파일러(javac), jdb, javadoc과 같은 도구 존재

🌱 프로그램을 **생성, 실행, 컴파일** 할 수 있음

### JRE(Java Runtime Environment, 자바 런타임 환경)
🚀 JVM + 자바 클래스 라이브러리(Java Class Library) 등으로 구성
* 컴파일된 Java 프로그램을 **실행**하는데 필요한 패키지

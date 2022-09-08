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

# 자바 데이터 타입, 변수 그리고 배열
<img width="537" alt="4" src="https://user-images.githubusercontent.com/61977260/189069933-70a32a05-1da4-4891-b152-e3b57ac10009.png">

## 프리미티브 타입 종류와 값의 범위 그리고 기본 값
## 프리미티브 타입과 레퍼런스 타입
### 프리미티브 타입(Primitive Type)
🚀 기본형 타입 or 원시 타입 / 정수, 실수, 문자, 논리, 리터럴 등의 실제 데이터 값을 저장하는 타입

### 레퍼런스 타입(Reference Type)
🚀 참조 타입 / 메모리 번지 값을 통해 객체를 참조하는 타입 / 원시 타입을 제외한 타입들(문자열, 배열, 열거, 클래스, 인터페이스)

## 리터럴
🚀 소스 코드 내에 직접 입력된 값(데이터)
* 변수 초기화 시 저장할 값에도 해당

### 정수 리터럴
🚀 정수 형태의 값으로 byte, char, short, int, long 저장 가능
* 10진수 : 소수점이 없는 정수 리터럴
* 8진수 : 0으로 시작하는 리터럴
* 0x 또는 0X로 시작하고 0~9 숫자, A, B, C, D, E, F 또는 a, b, c, d, e, f로 구성된 리터럴

### 실수 리터럴
🚀 실수 형태의 값으로 float, double 저장 가능
* 10진수 실수 : 소수점이 있는 리터럴
* 10진수 지수와 가수 표현 : E 또는 e가 숫자 뒤에 존재하는 리터럴

### 문자 리터럴
🚀 작은 따옴표 ''로 묶은 하나의 텍스트
**이스케이프 문자**

<img width="513" alt="ㅁㅁ" src="https://user-images.githubusercontent.com/61977260/189072524-4f986e7d-d76e-4094-a6c5-ec9811f0b21a.png">

### 논리 리터럴
🚀 boolean 저장 가능하고 true, false 값을 가짐

## 변수 선언 및 초기화하는 방법
* 따로

```
// 데이터타입 변수이름;
int num;

num = 10;
```
> 처음에 초기화가 되어있지 않아서 쓰레기 값이 들어가 있음
* 한번에

```
// 데이터타입 변수이름 = 저장할 값;
int num = 10;
```
> 서로 다른 타입들은 동시 초기화 불가능

## 변수의 스코프와 라이프 타임
### 변수의 스코프(영역)
🚀 변수에 접근하거나 접근할 수 있는 유효 범위/영역

### 변수의 라이프 타임
🚀 변수가 메모리에 살아있는 기간

**변수 예시**

```
class A {
   int x, y; // 인스턴스 변수
   static int reulst; // 클래스 변수
   void ex(int a, int b){} // a, b : 로컬 변수
}
```

## 타입 변환, 캐스팅 그리고 타입 프로모션
* 다른 타입으로 변환(boolean 제외)
* 다른 타입끼리 연산 -> 모두 같은 타입으로 변환 후 연산
* 프로모션(자동 타입 변환, 묵시적 타입 변환) : 작은 타입 -> 큰 타입 : 자동
* 캐스팅(강제 타입 변환, 명시적 타입 변환) : 큰 타입 -> 작은 타입 : 컴파일 에러

## 1차 및 2차 배열 선언하기
### 1차 배열 선언
**크기 할당 & 초기화 없이 배열 참조 변수만 선언**

```
int[] arr;
int arr[];
```

**선언과 동시에 배열 크기 할당**

```
int[] arr = new int[5];
String[] arr = new String[5];
```

**기존 배열의 참조 변수에 초기화 할당**

```
int[] arr;
arr = new int[5];
```

**선언과 동시에 배열의 크기 지정 및 값 초기화**

```
int[] arr = {1, 2, 3, 4, 5};
int[] arr = new int[] {1, 2, 3, 4, 5};
String[] weeks = {"월", "화", "수"};
```

### 2차 배열 선언

```
int[][] arr = new int[4][3];
int[][] arr9 = {{1, 2, 3}, {4, 5, 6}};
```

## 타입 추론, var
🚀 개발자가 변수의 타입을 명시적으로 적어주지 않고도, 컴파일러가 알아서 이 변수의 타입을 대입된 리터럴로 추론

```
public static void main(String[] args) {
    var str2 = "Hello world";

    if (str2 instanceof String) {
        System.out.println("str2의 타입은 String입니다");
    }
}
```
> str2가 String일 것이라고 판단

* 지역변수를 선언할 때 초깃값을 통하여 데이터 타입을 추론하게 함
* 초기값이 있는 지역 변수로만 선언 가능
* 키워드가 아님
* 런타임 오버헤드가 없음 - 중간에 타입이 절대 변경되지 않음
* null 값이 들어갈 수 없음
* 람다 표현식에서 명시적인 타입을 지정해줘야 함
* 배열을 선언할 땐 명시적은 타입을 지정해줘야 함

# 연산자
## 산술 연산자
```
+, -, *, /, %
```
## 비트 연산자
```
&, |, ^
```
## 관계 연산자
```
<, >, ≤, ≥, ==, !=
```
## 논리 연산자
```
&&, ||
```
## instanceof
🚀 참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 사용

```
[참조변수] instanceof [타입/클래스명]
```

* 연산결과는 boolean
* 결과가 true이면 형 변환 가능
* null인 참조변수에 대해서 수행하면 false
* 부모 자식 관계면 자식에서도 true

## assignment(=) operator
🚀 대입 연산자
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCO7ip%2Fbtq49aKN1mB%2FhoRaYdfkBK3Pp6LkFUkCb0%2Fimg.png)

## 화살표(->) 연산자
🚀 람다 표현식, 클래스를 작성하고 객체를 생성하지 않아도 메소드를 사용할 수 있음

```
// 메소드
int min(int x, int y) {
    retrun x < y ? x : y;
}
```

```
// 람다 표현식
(x, y) -> x < y ? x : y;
```
## 3항 연산자
```
(조건) ? 참일 때 : 거짓일 때
```

## 연산자 우선 순위
* 단항 -> 이항 -> 삼항
* 산술 -> 비교 -> 논리 -> 대입
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLn47K%2Fbtq454j1IU6%2F2RrvBjHhCVNMGacQEw0xZK%2Fimg.png)

## (optional) Java 13. switch 연산자
🚀 기존의 switch/case 문을 좀 더 간결하게 사용 가능

**기존**
```
String str = "A";

    switch(str){
        case "A": 
            System.out.println("1");
        case "B":
            System.out.println("2");
        case "C" :
            System.out.println("3");
        default :
            System.out.println("그 외의 숫자");
    }
```

**Java 13**
```
String result = switch(n) {
    case "A" -> System.out.println("1");
    case "B" -> System.out.println("2");
    case "C" -> System.out.println("3");
    default -> System.out.println("그 외의 숫자");
}
```

```
String result = switch(n) {
    case "A" -> {
        System.out.println("1");
        yield 1;
    }
    case "B" -> {
        System.out.println("2");
        yield 2;
    }
    case "C" -> {
        System.out.println("3");
        yield 3;
    }
    default -> {
        System.out.println("그 외의 숫자");
        yield 100;
    }
}
```
> 반환문법 : break -> yield로 변경 / 내다, 산출하다, 생산하다

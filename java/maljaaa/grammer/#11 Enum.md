# enum 정의하는 방법
[ Enum 이란? ]
* 서로 연관된 상수들의 집합
* Java 1.5부터 사용 가능
* 열거체 비교할 때 값&타입 체크
[ Enum 정의 ]
* enum 열거체명{상수1이름, 상수2이름, ...}

```
public enum exEnum{
  RED, BLUE, ORANGE, YELLOW
}
```

[ Enum 사용 ]

```
void useEnum(){
  exEnum red = exEnum.RED;
  System.out.println(red);
}
```
> 출력 : RED

# enum이 제공하는 메소드 (values()와 valueOf())
## values()
* 해당 열거체의 모든 상수를 저장한 배열을 생성하여 반환하는 메소드
* 자바의 모든 열거체에 컴파일러가 자동으로 추가해줌

## valueof()
* 전달된 문자열과 일치하는 해당 열거체의 상수를 반환

# java.lang.Enum
* Enum 클래스는 모든 자바 열거체의 공통된 조상 클래스 -> Java는 다중 상속을 지원하지 않기 때문에 Enum은 다른 클래스를 상속받을 수 없음
* 비교할 때 ==와 compareTo() 사용 가능

|메소드|설명|
|--|--|
|static E values()|해당 열거체의 모든 상수를 저장한 배열을 생성하여 반환|
|static E valueOf(String name|전달된 문자열과 일치하는 해당 열거체의 상수를 반환|
|String name()|해당 열거체 상수의 이름을 반환|
|int ordinal()|해당 열거체 상수가 열거체 정의에서 정의된 순서(0부터 시작)을 반환|

# EnumSet
* Set 인터페이스 기반으로 열거형 타입으로 지정
* 비트 연산을 이용해 메모리 공간도 적게 차지하고 속도도 빠르다.
* new 연산자를 사용한 생성 불가능

[ 주의점 ]
* 생성자 오버라이딩 불가능
* 동일한 타입의 열거 상수만 선언 가능
* null값을 넣거나 NullPointException을 던질 수 없음
* 상수는 열거 형에 선언된 순서에 따라 저장

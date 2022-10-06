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
# EnumSet

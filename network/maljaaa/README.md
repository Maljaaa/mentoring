# Network

## 기초 개념 정리

* 네트워크(Network) : 프로토콜을 사용하여 데이터를 통신(교환)하는 시스템의 집합
* 프로토콜(Protocol) : 전송 매체를 통해 데이터를 교환할 때 따르는 표준화된 특정 규칙(시스템이 데이터를 교환할 때 임의의 통신 규칙, 동등관계)
* 표준화(standardization) : 서로 다른 시스템을 상호 연동해 동작시킬 때 필요한 연동 형식의 통일
* 인터넷(Internet) : 전 세계에 걸쳐 파일 전송 등의 데이터 통신 서비스를 받을 수 있는 컴퓨터 네트워크의 시스템
* 시스템(System) : 내부 규칙에 따라 능동적으로 동작하는 대상(목적을 갖는 복잡한 존재)
* 인터페이스(Interface) : 시스템과 시스템을 연결하기 위한 표준화된 접근 방법(시스템과 전송 매체의 연결 지점에 대한 규격)
* 전송 매체(Transmission Media) : 시스템끼리 정해진 인터페이스를 연동해 데이터를 전달하는 물리적인 전송 수단(케이블, 공기, 무선신호 등)
* 노드(Node) : 인터넷에 연결된 시스템을 가장 일반화한 용어
* 호스트(Host) : 네트워크에 연결되어 있는 컴퓨터(컴퓨팅 기능이 있는 시스템)
* 클라이언트(Client) : 서비스를 이용하는 시스템
* 서버(Server) : 서비스를 제공하는 시스템
* 인터네트워킹(Internetworking) : 네트워크와 네트워크의 연결
* 게이트웨이(Gateway) : 인터네트워킹 기능을 수행하는 시스템
* 리피터(Repeater) : 한쪽에서 입력된 신호를 물리적으로 단순히 증폭(물리적 신호는 전송 거리가 멀수록 감쇄되기 때문에 중간에 이를 보완해줘야함)
* 라우터(Router) : 둘 혹은 그 이상의 네트워크와 네트워크 간 데이터 전송을 위해 최적 경로를 설정해주며 데이터를 해당 경로를 따라 한 통신망에서 다른 통신망으로 통신할 수 있도록 도와주는 인터넷 접속 장비
* 라우팅 테이블(Routing Table) : 네트워크와 호스트에 대한 정보가 보관되는 장소
* 교환(Switching) : 데이터를 최종 목적지까지 올바른 경로로 중개하는 기능
* 회선 교환(Circuit Switching) : 고정 대역으로 할당된 연결을 설정하여 데이터를 전송
* 패킷 교환(Packet Switching) : 데이터를 미리 패킷 단위로 나누어 전송(전용 대역을 따로 할당하지 않기 때문에 가변 크기의 전송률 지원)
* 데이터그램(Datagram) : 패킷들이 각각의 경로로 전송
* 가상회선(Virtual Circuit) : 패킷 교환에서 모든 패킷의 경로를 일정하게 

## OSI 7계층 모델

🚀 ISO(International Standard Organization)에서 제시한 OSI 7계층 모델, 연결된 두 호스트가 각각 7개 계층으로 구성된 모듈을 수행함으로써 데이터 송수신이 가능

![image](http://wiki.hash.kr/images/7/71/OSI_7_%EA%B3%84%EC%B8%B5.jpg)  

> 계층 n 프로토콜 : 계층 n 모듈끼리 사용하는 통신 규칙<br>
> 동료 프로세스 : 동일 계층에 위치한 통신 양단 프로세스<br>
> 인터페이스 : 상하위 계층 사이의 접속 방법<br>
> 서비스 : 상위계층이 하위계층을 사용하는 방법

* **물리 계층(Physical Layer)**<br>
 -> 인터넷 케이블, 라우터 스위치 등의 전기적 신호가 물리적인 장치에 의해 왔다 갔다(통신) 하는 계층 
 
* **데이터 링크 계층(Data Link Layer)**<br>
 -> 상위의 네트워크 계층에 신뢰성을 보장하기 위해 물리계층을 통해 송수신되는 정보의 오류와 흐름을 관리하며 오류를 찾고 재전송을 하는 기능이 있는 계층<br>
 -> 프레임(Frame) : 데이터 링크 계층을 이용해 전송되는 데이터
 
* **네트워크 계층(Network Layer)**<br>
 -> 송신 호스트가 전송한 데이터가 어떤 경로를 통해 수신 호스트에 전달되는지를 결정(Static, Dynamic)하는 라우팅 문제를 처리<br>
 -> 패킷(Packet) : 네트워크 계층을 이용해 전송되는 데이터<br>
 -> 트래픽이 과도하게 증가하는 문제를 조절하는 혼잡 제어(Congestion Control) 기능 포함
 
* **전송 계층(Transport Layer)**<br>
 -> 컴퓨터 내부에서 논리적으로 구축되는 통신 당사자인 프로세스 사이의 통신문제를 다루기에 송신 프로세스와 수신 프로세스를 직접 연결하는 단대단(End-to-End) 통신 기능을 제공<br>
 -> 전송 오류율, 전송 속도 등과 같은 일반 사용자의 서비스 요구 유형에 대한 고려와 흐름 제어 기능 제공
 
* **세션 계층(Session Layer)**<br>
 -> 통신 장치 간 상호작용 및 동기화 제공<br>
 -> 연결 세션에서 데이터 교화과 에러 발생 시의 복구를 관리
 
* **표현 계층(Presentation Layer)**<br>
 -> 데이터를 어떻게 표현할지 정하는 계층(코드 간 번역을 담당, text인지 그림인지 gif인지 jpg인지 구분)
 
* **응용 계층(Application Layer)**<br>
 -> 사용자와 가장 밀접한 계층으로 인터페이스 역할<br>
 -> 응용 프로세스 간의 정보 교환을 담당(전자메일, 인터넷, 동영상 플레이어 등)

## TCP(Transmission Control Protocol, 전송 제어 프로토콜)
🚀 신뢰성있는 데이터 통신을 가능하게 해주는 프로토콜

[ 특징 ]
 - Connection 연결(3 way handshake) - 양방향 통신
 - 데이터의 순차 전송을 보장
 - Flow Control(흐름제어)
 - Congestion Control(혼잡 제어)
 - Error Detection(오류 감지)
 - UDP보다 속도가 느리다(Time wait 때문)
 - 전이중(Full-Duplex, 양방향 통신), 점대점(Point to Point) 방식

### Segment
🚀 TCP 프로토콜의 PDU(Protocaol Data Unit)
* 데이터를 잘라서 전송하게 되는데, 이때 잘라진 데이터와 TCP Header가 붙어서 하나의 Segment를 구성한다.

### TCP Header
🚀 TCP가 맡은 역할을 수행하고 데이터의 정보를 표현하기 위해 데이터에 붙히는 헤더

* Souce port, Destination port : 포트 번호 정보
* Sequence Number : 전송하는 데이터의 순서 정보(올바른 데이터 재조립에 사용)
* Acknowledgment Number : 승인 번호, 데이터를 받은 수신자가 예상하는 다음 시퀀스 번호
* Data Offset : 전체 Segment 중, 헤더가 아닌 데이터가 시작되는 위치 표시
* Reserved(3 bits) : 미래를 위해 예약된 필드로 모두 0으로 채워져야 함
* Flags : 세그먼트의 속성을 나타내는 9개의 비트 플래그
* Window Size : 한번에 전송할 수 있는 데이터 양
* Checksum : 데이터를 송신하는 중에 발생할 수 있는 오류를 검출하기 위한 값
* Urgent Pointer : 긴급 포인터(URG 플래그가 1이라면 수신 측은 이 포인터가 가리키고 있는 데이터를 우선 처리)
* Options : TCP의 기능을 확장할 떄 사용(크기가 고정된 것이 아니라 가변적)

## TCP 3 way handshake(연결)

![image](https://snabaynetworking.com/wp-content/uploads/2019/10/TCP-3-Way-Handshake-Process-1.jpg)

**[Step 1]**
**Client**가 **Server**에게 연결을 시도하는 SYN 비트를 1로 설정해 패킷 송신

**[Step 2]**
**Server**가 **Client**에게 연결 잘 받았고 나도 연결하려고 ACK, SYN 비트를 1로 설정해 패킷 송신

**[Step 3]**
**Client**가 **Server**에게 연결 잘 받았고 데이터 보내려고 ACK 비트를 1로 설정해 패킷 송신

> 패킷은 택배

## TCP 4 way handshake(연결 해제)

![image](https://t1.daumcdn.net/cfile/tistory/99229C485C1D90C038)

**[Step 1]**
데이터를 전부 송신한 **Client**가 **Server**에게 FIN 송신

**[Step 2]**
**Server**가 **Client**에게 FIN 잘 받았다고 ACK 송신

**[Step 3]**
**Server**가 **Client**에게 남은 패킷 송신 (Client 일정 시간 대기)

**[Step 4]**
**Server**가 **Client**에게 FIN 송신

**[Step 5]**
**Client**가 **Server**에게 FIN 잘 받았다고 ACK 송신

## 흐름제어
🚀 송신측과 수신측 사이의 **데이터 처리 속도 차이(흐름)을 제어**하기 위한 기법으로 데이터 처리 속도를 조절하여 수신자의 버퍼 오버플로우를 방지한다.

* Stop and Wait(정지 - 대기)<br>
 -> 매번 전송한 패킷에 대한 확인 응답을 받아야 그 다음 패킷을 전송할 수 있다. 이러한 구조로 인해 비효율적이라는 단점이 있다.
 
* Sliding Window(슬라이딩 윈도우)<br>
 -> 윈도우 : 송신, 수신, 스테이션 양쪽에서 만들어진 버퍼의 크기<br>
 -> 수신측에서 설정한 윈도우 크기만큼 송신측에서 확인 응답 없이 세그먼트를 전송할 수 있게 하여 데이터 흐름을 동적으로 조절하는 기법이다. 따라서 송신측에는 ACK 프레임을 수신하지 않더라도 여러개의 프레임을 연속적으로 전송할 수 있다.<br>
 -> Stop and Wait의 비효율성을 개선했다.
 
## 혼잡제어

🚀 **송신측**의 데이터 전달과 네트워크 데이터 처리 속도를 해결하기 위한 기법이다.
* 한 라우터에게 데이터가 몰려 모든 데이터를 처리할 수 없는 경우, 호스트들은 재전송을 하게 되고 결국 혼잡을 가중시켜 오버플로우나 데이터 손실이 발생한다.
* 이러한 네트워크 혼잡을 피하기 위해 **송신측**에서 보내는 데이터의 전송 속도를 제어하는 것이 혼잡 제어의 개념이다.

### AIMD(Additive Increase Multicative Decrease)

![image](https://velog.velcdn.com/images%2Fjsj3282%2Fpost%2F6f811337-3638-40cf-a5a8-255dbc07e25c%2F%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%20(6).png)

* 합 증가/곱 감소 알고리즘이라고 한다.
* 송신 -> 수신에서 문제가 없다면 Window Size를 1씩 증가, 문제가 있다면 패킷을 보내는 속도를 절반으로 감소한다.
* 여러 호스트가 한 네트워크를 공유하고 있으면 나중에 진입하는 쪽이 처음에는 불리하지만 시간이 흐르면 평형 상태로 수렴하게 되는 특징이 있다.
* 초기에 네트워크의 높은 대역폭을 사용하지 못하여 오랜 시간 걸리게 되고, 네트워크가 혼잡해지는 상황을 미리 감지하지 못한다. 즉, 네트워크가 혼잡해지고 나서야 대역폭을 줄이는 방식

### Slow Start

![image](https://velog.velcdn.com/images%2Fjsj3282%2Fpost%2Feccd9315-2043-4dd1-9fdf-efffa3fac94e%2F%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C%20(7).png)

* AIMD가 네트워크 수용량 주변에서는 효율적으로 동작하지만, 처음에 전송 속도를 올리는데 시간이 너무 길다는 단점이 있다.
* 패킷을 하나씩 보내는데 문제 없이 동장하여 ACK 패킷마다 Window Size를 1씩 늘린다. 즉, 한 주기를 지나면 Window Size는 2배가 된다.
* 따라서 그래프는 지수함수 꼴이 된다.
* 혼잡 현상이 발생하면 Window Size를 1로 떨어뜨린다.
* 한 번 혼잡 현상이 발생했던 Window Size의 절반까지는 이전처러 ㅁ지수함수 꼴로 Window Size를 증가시키고 그 이후부터는 완만하게 1씩 증가시키는 방식이다.
* 미리 정해진 임계값(Threshold)에 도달할 때까지 윈도우의 크기를 2배씩 증가시킨다.
* 임계값에 도달하면 혼잡 회피 단계로 넘어간다.

[혼잡 회피(Congestion Avoidance)]
* WS가 임계값에 도달한 이후에는 데이터의 손실이 발생할 확률이 높다.
> WS : Window Size
* 따라서 이를 회피하기 위해 윈도우 크기를 1씩 증가시킨다.
* 수신측으로부터 일정 시간 동안까지 ACK를 수신하지 못하는 경우
 -> 타임 아웃의 발생 : 네트워크 혼잡이 발생했다고 인식<br>
 -> 혼잡 상태로 인식된 경우<br>
   ->> 윈도우의 크기 세그먼트 수를 감소시킨다.<br>
   ->> 동시에 임계값을 패킷 손실이 발생했을 떄의 윈도우 크기의 절반으로 줄인다.
   
[빠른 회복(Fast Recovery)]
* 혼잡한 상태가 되면 WS를 1로 줄이지 않고 절반으로 줄이고 선형 증가시키는 방법
* 빠른 회복 정책까지 적용하면 혼잡 상황을 한 번 겪고 나서는 순수한 AIMD 방식으로 동작하게됨

[빠른 재전송(Fast Retransit)]
* 패킷 하나가 손실되어 순번이 중복된 ACK패킷을 받게 되면, 문제가 되는 패킷을 재전송 할 수 있다.
* 중복된 순번의 패킷을 3개 받으면 재전송한다. 
* 이러한 현상이 일어나는 것은 약간의 혼잡이 발생한 것으로 간주하여 WS를 절반으로 줄인다.
   
## UDP(User Datagram Protocol)

🚀 TCP보다 신뢰성이 떨어지지만 전송 속도가 일반적으로 빠른 프로토콜(순차전송 x, 흐름제어 x, 혼잡제어 x)

![image](https://www.stevenjlee.net/wp-content/uploads/2020/06/image-21.png)

>Client가 패킷 송신

* Connectionless(3 way handshake X)
* Error Detection
* 비교적 데이터의 신뢰성이 중요하지 않을 떄 사용(ex. 영상 스트리밍)
* 데이터를 쪼개지 않고 그대로 헤더와 함께 전송

### UDP Header

![image](https://t1.daumcdn.net/cfile/tistory/272A5A385759267B36)

* 포트 존재, 에러 검출 비트 존재

### TCP vs UDP
|TCP|UDP|
|:---:|:---:|
|Connection-oriented protocol(연결지향형 프로토콜)|Connection-less protocol|
|Connection by byte stream(바이트 스트림을 통한 연결)|Connection by message stream(메시지 스트림을 통한 연결)|
|Congestion / Flow control(혼잡제어, 흐름제어)|No Congestion / Flow control(혼잡제어와 흐름제어 X)|
|Ordered, Lower speed(순서보장, 상대적 느림)|Not ordered, Higher speed(순서 보장되지 않음, 상대적으로 빠름)|
|Reliable data transmission(신뢰성 있는 데이터 전송 - 안정적)|Unreliable data transmission(데이터 전송 보장 X)|
|TCP packet : Segment|UDP packet : Datagram|
|HTTP, Email, File transfer...|DNS, Broadcasting...|

## HTTP(Hyper Text Transfer Protocol)

🚀 인터넷에서 데이터를 주고받을 수 있는 가장 기본적인 프로토콜

### HTTP 메시지

* 서버가 응답할 때 응담에 대한 정보를 담아 클라리언트로 보낼 때 정보가 담긴 메시지

```
GET https://www.zerocho.com HTTP/1.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
Upgrade-Insecure-Requests: 1
```

> 첫 줄 : GET(HTTP 매서드), www.zerocho.com(주소), HTTP/1.1(HTTP 버전) => **메서드 주소 버전**<br>
> 두번째 줄 : 헤더<br>
> 세번쨰 줄 : 헤더

```
HTTP/1.1 200 OK
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 35653
Content-Type: text/html;

<!DOCTYPE html><html lang="ko" data-reactroot=""><head><title...
```

> 첫 줄 : **버전 상태코드 상태메시지**(200은 성공적인 요청)<br>
> 2,3,4,5번째 줄 : 헤더<br>
> 마지막 줄 : 본문
 
### HTTP 메서드

```
GET www.naver.com HTTP/1.1
```

* 자주 쓰는 HTTP 메서드 : GET 가져오다, POST 게시하다, PUT 집어넣다, PATCH 고치다, DELETE 지우다, (OPTIONS, HEAD, CONNECT, TRACE)

* REST : '주소를 자원, 메서드를 동사'라고 보는 개발 방식

```
GET /users?sort=name&filter=developer&limit=100
```

> 주소 뒤에 ?를 붙힌 후 키=값&키=값<br>
> 이름순으로 가져오고 싶으면 sort<br>
> 쿼리스트링 간에 &로 구별 가능

### HTTP 버전

**[HTTP/0.9 - 원 라인 프로토콜]**<br>

🚀HTTP/0.9는 극히 단순함

> 요청
```
GET /mypage.html
```

> 응답
```
<HTML>
A very simple HTML page
</HTML>
```

* 요청 : 단일
* 메서드 : GET 유일
* 응답 : 파일 내용 자체
* 헤더 : 없음

**[HTTP/1.0 - 확장성 만들기]**

🚀 HTTP/0.9는 매우 제한적이었으며 브라우저와 서버 모두 좀 더 융통성을 가지도록 빠르게 확장되었음

> 요청
```
GET /mypage.html HTTP/1.0
User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

200 OK
Date: Tue, 15 Nov 1994 08:12:31 GMT
Server: CERN/3.0 libwww/2.17
Content-Type: text/html
<HTML>
A page with an image
  <IMG SRC="/myimage.gif">
</HTML>
```

> 응답
```
GET /myimage.gif HTTP/1.0
User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

200 OK
Date: Tue, 15 Nov 1994 08:12:32 GMT
Server: CERN/3.0 libwww/2.17
Content-Type: text/gif
(image content)
```

* 커넥션 하나당 요청 1 & 응답 1 처리 -> 매번 새로운 연결로 성능 저하, 서버 부하 비용 증가

**[HTTP/1.1 - 표준 프로토콜]**

🚀 모호함을 명확하게 하고 많은 개선 사항들을 도입

> 단일 커넥션
```
GET /en-US/docs/Glossary/Simple_header HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

200 OK
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Wed, 20 Jul 2016 10:55:30 GMT
Etag: "547fa7e369ef56031dd3bff2ace9fc0832eb251a"
Keep-Alive: timeout=5, max=1000
Last-Modified: Tue, 19 Jul 2016 00:59:33 GMT
Server: Apache
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding

(content)


GET /static/img/header-background.png HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

200 OK
Age: 9578461
Cache-Control: public, max-age=315360000
Connection: keep-alive
Content-Length: 3077
Content-Type: image/png
Date: Thu, 31 Mar 2016 13:34:46 GMT
Last-Modified: Wed, 21 Oct 2015 18:27:50 GMT
Server: Apache

(image content of 3077 bytes)
```

* Persistent Connection : 지정한 timout 동안 커넥션을 닫지 않는 방식 -> 커넥션을 열어두면 여러 요청이 이 커넥션을 사용할 수 있음
* Pipelining : 하나의 커넥션에서 응답을 기다리지 않고 순차적인 여러 요청을 연속적으로 보내 그 순서에 맞춰 응답을 받는 방식으로 지연 시간을 줄이는 방법<br>
-> 문제점 : Head Of Line Blocking(먼저 보낸 요청이 너무 오래걸림), Header 구조의 중복(데이터가 쓸데없이 커져버림)


**[HTTP/2 - 더 나은 성능을 위한 프로토콜]**

🚀 기존 HTTP/1.X 버전의 성능 향상에 초점을 맞춘 프로토콜, 표준의 대체가 아닌 확장

* HTTP 메시지 전송 방식의 변화 -> 바이너리 프레이밍(메시지 분할) 계층 사용 -> 파싱&전송속도 상승, 오류 발생 가능성 낮춤(컴퓨터 맞춤 환경) -> Request and response multiplexing -> Head Of Line Blocking 해결(순서 사라짐)
* Stream Prioritization -> 리소스간 우선 순위를 설정 가능(스트림에 가중치 가능)
* Server Push : 클라이언트가 요청하지 않은 리소스를 서버에서 알아내 Push
* Header compression -> 헤더의 크기를 줄여 페이지 로드 시간 감소(헤더 압축, 허프만 인코딩)

**[HTTP/3 - HTTP over QUIC]**

🚀 전송 계층 부분에 TCP/TLS(SSL업그레이드 버전) 대신 QUIC(Google에서 제작) 사용

### QUIC

* UDP 바탕으로 만듬(데이터 전송에 집중한 설게, 별도의 기능X -> 원하는 기능 구현 & TCP의 지연을 줄이면서 TCP만큼 신뢰성 확보 가능)
* 전송 속도 향상
* Connection UUID라는 고유한 식별자로 서버와 연결 -> 커넥션 재수립 필요 X
* TLS 기본 적용, IP Spoofing / Replay Attack 방지 -> 보안성 향상
* 독립 스트림 -> 향상된 멀티플렉싱 가능

## HTTPS

🚀 HTTPS는 SSL 레이어 위에 HTTP를 통과 시키는 방식<br>
(암호화, HTTP 자체 암호 X, HTTP Header 암호 X, 세션 데이터 암호화 O)

### HTTPS가 필요한 이유

![image](https://miro.medium.com/max/1218/0*l7N0VL93DBrNIjA4)

1. 보안성
 * SSL(보안 소켓 계층)을 사용하여 보안적 이슈 해결
2. 검색 엔진 최적화
 * Google은 HTTPS로 설정된 사이트에 추가적인 검색 가산점을 준다고 함
3. 가속화된 모바일 페이지
 * AMP(Accelerated Mobile Pages)는 모바일 기기에서 빠르게 콘텐츠를 로딩하기 위한 방법으로 Google이 개발함

## GET vs POST

### GET

🚀 클라이언트에서 서버로 어떠한 리소스로부터 정보를 요청하기 위해 사용되는 메서드

* 읽거나(Read), 검색(Retrieve)할 때에 사용되는 메서드
* 요청을 전송할 때 URL 주소 끝에 파라미터로 포함되어 전송되며, 이 부분을 **쿼리 스트링(QueryString)**이라고 부름

```
www.example-url.com/resources?name1=송유현&name2=곽철용
```

* 파라미터인 name1과 name2를 통해 값을 전달받을 수 있음
* 요청 파라미터가 여러 개이면 &로 연결
* GET 요청은 오로지 데이터를 읽을 때만 사용되고 수정할 때는 사용하지 않음 -> 안전하다 -> 데이터 변형의 위험없이 사용 가능

[ 특징 ]
* 데이터를 Header에 포함하여 전송
* 불필요한 요청을 제한하기 위해 요청이 캐시될 수 있음
* 파라미터에 내용이 노출되기 때문에 민감한 데이터를 다룰 때 GET 요청을 사용해서는 안됌
* 브라우저에 기록이 남음
* 북마크에 추가할 수 있음
* 데이터 길이에 대한 제한이 있음
* 성공시, 200(ok) & XML, JSON 등 여러 형식의 데이터와 함께 반환
* idempotent : 연산을 여러번 적용하더라도 결과가 달라지지 않는 성질

### POST

🚀 리소스를 생성 / 업데이트 하기 위해 서버에 데이터를 보내는데 사용

* 전송 데이터를 HTTP 메시지의 Body에 담아서 전송
* 요청 헤더의 Content-Type에 콘텐츠 타입을 명시
* HTTP 메시지의 Body는 길이의 제한없이 데이터 전송 가능 -> 대용량 데이터 전송 가능
* 내용이 눈에 보이지 않지만 여러 툴로 확인할 수 있기 때문에 민감한 데이터의 경우에는 반드시 암호화해서 전송

[ 특징 ]
* 캐시되지 않음
* 브라우저 기록에 남지 않음
* 북마크에 추가할 수 없음
* 데이터 길이에 대한 제한이 없음
* 자원 생성은 201(Created) HTTP 응답 코드를 반환
* idempotent 하지 않음

![image](https://images.velog.io/images/songyouhyun/post/0dea38bf-bdb3-4562-a5f0-c510f843f48f/image.png)

||GET|POST|
|---|:---:|:---:|
|캐시|O|X|
|브라우저 기록|O|X|
|북마크 추가|O|X|
|데이터 길이 제한|O|X|
|데이터가 담기는 곳|HTTP 패킷 Header|HTTP 패킷 Body|
|HTTP 응답 코드|200(ok)|201(created)|
|언제 주로 사용?|리소스 요청|리소스 생성|
|리소스 전달 방식|쿼리스트링|HTTP Body|
|idempotent|O|X|

🌱 GET 방식은 **무언가를 가져오는 것**, POST방식은 **무언가를 만들거나 수정하는 것**

## 쿠키와 세션

🚀 HTTP 프로토콜의 특징이자 약점을 보완하기 위해서 사용

* Connectionless 프로토콜(비연결지향)<br>
-> 클라이언트가 서버에 요청을 했을 떄, 그 요청에 맞는 응답을 보낸 후 연결을 끊는 처리방식

* Stateless 프로토콜(상태정보 유지 안함)<br>
-> 클라이언트의 상태 정보를 가지지 않는 서버 처리 방식

🌱 정보를 유지하기 위해 사용되는 것이 쿠키와 세션

### 쿠키

🚀 사용자가 웹 사이트를 방문할 경우, 서버에서 **사용자의 컴퓨터에 저장하는 작은 기록 정보 파일**

[ 특징 ]
* 필요시 정보를 참조하거나 재사용할 수 있음
* 이름, 값, 만료일(저장 기간 설정), 경로 정보로 구성
* 클라이언트에 총 300개의 쿠키를 저장할 수 있음
* 하나의 도메인 당 20개의 쿠키를 가질 수 있음
* 하나의 쿠키는 4KB까지 저장 가능

[ 쿠키의 동작 순서 ]
1. 클라이언트가 페이지 요청
2. 웹 서버 쿠키 생성
3. 생성한 쿠키에 정보를 담아 HTTP 화면을 돌려줄 떄, 같이 클라이언트에 넘겨줌
4. 넘겨 받은 쿠키는 클라이언트가 가지고 있다가(로컬 PC에 저장) 다시 서버에 요청할 때(웹 사이트 재방문) 요청과 함꼐 쿠키 전송

[ 사용 예시 ]
* 아이디와 비밀번호 자동 입력
* "오늘 이 창을 다시 보지 않기" 체크

### 세션

🚀 방문자가 웹 서버에 접속해 있는 상태를 하나의 단위로 보고 그 상태를 일정하게 유지시키는 기술

[ 특징 ]
* 웹 서버에 윀 컨테이너의 상태를 유지하기 위한 정보를 저장
* 웹 서버의 저장되는 쿠키(= 세션 쿠키)
* 브라우저를 닫거나, 서버에서 세션을 삭제했을 떄만 삭제가 되므로 쿠키보다 비교적 보안이 좋음
* 저장 데이터에 제한이 없음(단, 서버 용량이 허용해야함)
* 각 클라이언트 고유 Session ID를 부여 -> ID로 클라이언트 구분 -> 각 요구에 맞는 서비스 제공

[ 동작 순서 ]
1. 클라이언트가 페이지 요청
2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하여, 클라이언트가 해당 Session-ID를 보냈는지 확인
3. Session-ID가 존재하지 않는다면, 서버는 Session-ID를 생성해 클라이언트에게 돌려줌
4. 돌려받은 Session-ID를 쿠키를 사용하여 서버에 저장
5. 클라이언트 재접속 시, 쿠키를 이용하여 Session-ID 값을 서버에 전달

[ 사용 예시 ]
* 로그인 후 다른 페이지로 이동해도 로그인 유지

## REST와 RESTful의 개념

### REST(REpresentational State Transfer)

🚀 자원을 이름(자원의 표현)으로 구분해 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미, 즉 자원(resource)의 표현(representation)에 의한 상태 전달을 뜻함

[ 개념 ]
* 자원 상태 전달 / 자원의 표현 = HTTP URI, 상태 전달 = HTTP Method
* 웹의 기존 기술과 HTTP를 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일
* 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나
* 어떤 자원에 대해 CRUD연산을 수행하기 위해 URI(Resource)로 GET, POST 등의 방식(Method)을 사용하여 요청을 보내며, 요청을 위한 자원은 특정한 형태(Representation of Resource)로 표현

[ 구성 요소 ]
1. 자원(Resource) - URI
* 모든 자원에는 고유한 ID가 존재하고, 이 자원은 Server에 존재함
* 자원을 구별하는 ID는 '/jjuniv/:jjuniv_id'와 같은 HTTP URI(식별자)
* Client는 URI를 이용해 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청

2. 행위(Verb) - Method
* HTTP Method 사용
|데이터 처리 방법|HTTP Method|
|:---:|:---:|
|Create|POST|
|Read|GET|
|Update|PUT or PATCH|
|Delete|DELETE|

3. 표현(Representation of Resource)
* Client - Server 가 데이터를 주고 받는 형태로 JSON, XML, TEXT, RSS 등이 있음
* JSON, XML을 통해 주고 받는 것이 일반적

[ 특징 ]
1. Server-Client
2. Stateless(무상태)
 * HTTP 프로토콜이 Stateless Protocol이므로
3. Cacheable(캐시 처리 기능)
 * HTTP 프로토콜을 그대로 사용하므로
4. Layered System(계층 구조)
5. Uniform Interface(인터페이스 일관성)
 * URI로 지정한 Resource에 대한 요청을 통일되고 한정적으로 수행하는 아키ㅔㄱ처 스타일
6. Self-Descriptiveness(자체 표현)
 * 요청 메시지만 보고도 쉽게 이해할 수 있는 자체 표현 구조

🌱 HTTP를 잘 활용하기 위해서 만들어진 아키텍처
🌱 URI와 HTTP 메서드를 사용해서 자원과 행위를 표현
🌱 API 의미를 표현하기 쉽고, 의미를 파악하기도 쉬움


### RESTful

🌱 REST란 아키텍처 스타일의 제약조건을 모두 만족하는 시스템

## DNS 흐름

### DNS(Domain Name System)란

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcxL7LB%2FbtqQR6V9Lbe%2FAIzYDnFPqzkkU8sg4jxCZ1%2Fimg.png)

🚀 사람이 읽을 수 있는 도메인 이름(www.naver.com)을 머신이 읽을 수 있는 IP주소(192.0.1.2)로 변환하는 시스템

### DNS Round Robin 방식

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkIrwn%2Fbtrc8hoWQLp%2FOdb8ETK7pruJ5te9eayL20%2Fimg.png)

🚀 DNS Load Balancing 기법 중 Round Robin 방식은 부하 분산의 대표적인 알고리즘으로써, 순서대로 돌아가면서(보통 시간 단위) 각각의 서버로 트래픽을 분산시켜서 처리하는 알고리즘
> Load Balancing : 부하분산<br>
> DNS Load Balancing : 별도의 소프트웨어나 하드웨어 로드밸런싱 장비를 이용하지 않고 DNS를 이용하여 도메인 정보를 조회하는 시점에서 다른 IP정보를 통해 트래픽을 분산하는 기법

* 한 대로 운영하면 벅찬 운영을 여러대가 분산해서 감당하기에 좀 더 수월하게 운영이 가능
* 서버 한 대가 죽어도 운영이 가능
* 중간 장비(로드밸런서 등) 없이도 서비스가 가능

🌱 여러개의 IP주소를 결과로 돌려줌

* 사용자의 OS 애플리케이션에 따라 동작이 다름
* 여러 개의 IP 중 제일 먼저 조회된 IP를 선택, 무작위로 IP를 선택
* 선택 IP 접속이 안되면 다음 조회된 IP 접속하도록 로직을 추가할 수 있음

### DNS Round Robin 방식의 문제점

1. 서버의 수만큼 공인 IP주소가 필요
 * 서버 대수를 늘리기 위해
2. 균등하게 분산되지 않음
 * 캐싱되는 경우에는 항상 같은 서버로 접속됨
3. 서버가 다운되도 확인이 불가능
 * 일반적인 로드밸런싱은 Health check를 수반하지만 Round Robin은 별도로 하지 않음
 > Health Check : 서버에 일정한 간격으로 신호를 보내고 응답이 오는지 체크하여 정상 가동중인지를 판단

### Weighted Round Robin(WRR)
* DNS Round Robin은 서버가 서로 동일한 스펙일 경우 사용하는 것이 타당함
* 만약, 성능이 월등히 좋은 서버가 있다면 그 서버에 트래픽을 더 많이 할당해야 함
* L4의 부하 분산 방법 중 WRR방식을 사용하면 각각의 웹 서버에 가중치를 설정해서 분산 비율을 변경할 수 있음

🌱 웹 서버에 가중치를 가미해서 분산 비율을 변경함으로써, 가중치가 큰 서버일수록 빈번하게 선택되므로 처리능력이 높은 서버의 가중치를 높게 설정

### Least Connection
* WRR과 마찬가지의 이유로 사용됨
* 접속 클라이언트 수가 가장 적은 서버를 선택하는 방식

🌱 접속 클라이언트 수가 가장 적은 서버를 선택함으로써, 로드밸런서에서 실시간으로 connection 수를 관리 또는 각 서버에서 주기적으로 알려주는 것이 필요

## Socket(TCP/IP Socket)
* **소켓**은 소프트웨어로 작성된 추상적인 개념의 통신 접속점이라고 할 수 있는데 네트워크 응용 프로그램은 소켓을 통하여 통신망으로 데이터를 송수신하게 됨
* **소켓**은 응용 프로그램에서 TCP/IP를 이용하는 창구 역할을 하며 응용 프로그램과 소켓 사이의 **인터페이스 역할**을 하고 있음

### Socket 이전 실시간 통신 기술들
1. Polling
![image](https://junhyunny.github.io/images/polling-long-polling-and-javascript-example-1.JPG)
* 서버로 일정 주기 요청 송신
* real-time 통신에서는 언제 통신이 발생할지 에측이 불가능
* 불필요한 request와 connection을 생성
* real-time 통신이라고 부르기 애매할 정도의 실시간성

2. Long Polling
![image](https://velog.velcdn.com/images%2Fjungbumwoo%2Fpost%2F0db7fa2b-e55a-495c-aa98-09502622823b%2Fimage.png)
* 서버에 요청 보내고 이벤트가 생겨 응답 받을 때까지 연결 종료 X
* 응답 받으면 끊고 다시 재요청
* 많은 양의 메시지가 쏟아질 경우 polling과 같음

3. Streaming
* 서버에 요청 보내고 끊기지 않은 연결상태에서 끊임없이 데이터 수신
* 클라이언트에서 서버로의 데이터 송신이 어려움

### 클라이언트 소켓과 서버 소켓
* 클라이언트 소켓(능동적) : 서버 프로그램으로 연결 요청을 하는 것과 데이터 전송을 하는 일을 함
* 서버 소켓(수동적) : 클라이언트로부터 연결 요청이 오기를 기다렸다가 연결 요청이 들어오면 클라이언트와 연결을 맺고 다른 소켓을 만드는 일을 함

### 소켓 API 실행흐름
![image](https://t1.daumcdn.net/cfile/tistory/995C23465C7DD7E30B)

🚀 클라이언트 소켓의 흐름
- 소켓 생성
- 서버 측에 연결(connect())
- 서버 소켓에서 연결을 받으면 데이터를 송수신(send()/recv())
- 모든 처리가 완료되면 소켓을 닫음

🚀 서버 솤세의 흐름
- 소켓 생성
- 서버가 사용할 IP주소와 포트 번호를 생성한 소켓에 결합(bind())
- 클라이언트로부터 연결 요청이 수신되는지 주시(listen())
- 요청이 수신되면 Accept 후 소켓 생성
- 데이터 송수신(send()/recv())
- 소켓 닫음

## Web Socket(HttpSocket)
🚀 두 프로그램 간의 메시지를 교환하기 위한 통신 방법 중 하나

### Web Socket Handshake 및 실행 흐름
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcmqBIY%2FbtqKBOBCLJS%2FyKS7Ci7bq5DTki4DuJRlYk%2Fimg.png)
> 붉은색 : Opening Handshake, 노란색 : Data Transfer, 보라색 : Closing Handshake

🚀 Opening Handshake
* 클라이언트에서 HTTP Upgrade request(핸드쉐이크 요청)을 전송하고, 핸드쉐이크 응답으로 응답 코드 101을 받음

```
GET /chat HTTP/1.1
Host: localhost:8080
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
Origin: http://localhost:9000
```

* Upgrade : 프로토콜을 전환하기 위해 사용하는 헤더
* Connection : 
🚀 Data Transfer

🚀 Closing Handshake

### Web Socket 한계

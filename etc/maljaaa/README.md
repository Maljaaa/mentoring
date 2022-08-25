# ETC
## 블락 논블락/싱크 어싱크
### Blocking VS Non-Blocking
🌱 다른 주체가 작업할 때 자신의 `제어권`이 있는지 없는지로 볼 수 있음<br>

**[Blocking]**<br>
🚀 자신의 작업을 진행하다가 다른 주체의 작업이 시작되면 다른 작업이 끝날 때까지 기다렸다가 자신의 작업을 시작하는 것

**[Non-Bloking]**<br>
🚀 다른 주체의 작업에 관련없이 자신의 작업을 하는 것

### Synchronous VS Asynchronous
🌱 결과를 돌려주었을 때 `순서와 결과에 관심`이 있는지 없는지로 판단할 수 있음<br>

**[Synchronous]**<br>
🚀 작업을 동시에 수행하거나, 동시에 끝나거나, 끝나는 동시에 시작함을 의미

**[Asynchronous]**<br>
🚀 시작, 종료가 일치하지 않으며, 끝나는 동시에 시작을 하지 않음을 의미

### Blocking Non-Blocking / Synchronous Asynchronous
**[4가지 조합의 경우]**
![image](https://user-images.githubusercontent.com/44635266/68367180-75116900-0178-11ea-84dd-e9467b233eec.png)

1. Blocking/Sync
```
나 : 대표님, 개발자 좀 더 뽑아주세요..
대표님 : 오케이, 잠깐만 거기 계세요!
나 : …?!!
대표님 : (채용 공고 등록.. 지원자 연락.. 면접 진행.. 연봉 협상..)
나 : (과정 지켜봄.. 궁금함.. 어차피 내 일 하러는 못 가고 계속 서 있음)
```

2. Non-Blocking/Sync
```
나 : 대표님, 개발자 좀 더 뽑아주세요..
대표님 : 오케이, 잠깐만 거기 계세요!
나 : …?!!
대표님 : (채용 공고 등록.. 지원자 연락.. 면접 진행.. 연봉 협상..)
나 : (안 궁금함.. 지나가는 말로 여쭈었는데 붙잡혀버림.. 딴 생각.. 못 가고 계속 서 있음)
```

3. Blocking/Async
```
나 : 대표님, 개발자 좀 더 뽑아주세요..
대표님 : 알겠습니다. 가서 볼 일 보세요.
나 : 넵!
대표님 : (채용 공고 등록.. 지원자 연락.. 면접 진행.. 연봉 협상..)
나 : 채용하셨나요?
대표님 : 아직요.
나 : 채용하셨나요?
대표님 : 아직요.
나 : 채용하셨나요?
대표님 : 아직요~!!!!!!
```

4. Non-Blocking/Async
```
나 : 대표님, 개발자 좀 더 뽑아주세요..
대표님 : 알겠습니다. 가서 볼 일 보세요.
나 : 넵!
대표님 : (채용 공고 등록.. 지원자 연락.. 면접 진행.. 연봉 협상..)
나 : (열일중..)
대표님 : 한 분 모시기로 했습니다~!
나 : 😍
```
## WebServer VS WebApplicationServer 
### Web Server
🚀 웹 브라우저(클라이언트)로부터 HTTP 요청을 받아 HTML 문서와 같은 정적 컨텐츠를 제공하는 프로그램

**[ 기능 ]**
1. 정적 컨텐츠 요청 시
 * 정적 컨텐츠(HTML, JPEG, CSS, ,,,)를 제공

2. 동적 컨텐츠 요청 시
 * Web Applicaiton Server(WAS)로 전달하여 WAS가 처리한 결과를 클라이언트에 전달
 
### Web Application Server(WAS)
🚀 DB 조회나 다양한 로직 처릴ㄹ 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 프로그램

**[ 기능 ]**
* 클라이언트로부터 HTTP 요청을 받음(대부분의 WAS는 Web Server 내장)
* 요청에 맞는 정적 컨텐츠(HTML, JPEG, CSS, ,,,)를 제공
* DB 조회나 다양한 로직 처리를 통해 동적 컨텐츠 제공

### Web Server와 WAS를 함께 사용하는 이유
1. 책임 분할을 통한 서버 부하 방지
 * 정적 컨텐츠는 Web Server, 동적 컨텐츠는 WAS가 담당
 
2. 여러대의 WAS 로드밸런싱
 * WAS가 처리해야 하는 요청을 여러 WAS가 나누어서 처리할 수 있도록 설정

3. 여러대의 WAS Health Check
 * 서버에 주기적으로 HTTP 요청을 보내 서버의 상태를 확인
 * Interval : Health Check를 통해 서버 상태를 확인하는 요청을 날리는 주기
 * Fails : 아래의 경우 3회 연속 실패하면 서버가 비정상이라고 인지
 * Passes : 서버가 다시 복구되어 요청이 2번 연속 성공하면 서버가 정상으로 인지
 
4. 보안
 * 리버스 프록시를 통해 실제 서버를 외부에 노출하지 않을 수 있음
 
🌱 서비스 확장성, 안정성을 고려한다면 앞 단에 Web Server를 두는 것이 유리

## Monolithic service Application VS Micro Service Application
### Monolithic Architecture
![image](https://wac-cdn.atlassian.com/dam/jcr:95b9a276-c524-42b1-8d06-ded56d589858/Monolithic%20architecture@2x.png?cdnVersion=488)

🚀 전통의 아키텍처를 지칭하는 의미로, 하나의 서비스 또는 애플리케이션이 하나의 거대한 아키텍쳐

**[ 장점 ]**
1. 개발 초기에 단순한 아키텍쳐 구조와 개발에 용이
2. 어떤 서비스든지 개발되어 있는 환경이 같아서 복잡하지 않음
3. 쉽게 고가용성 서버 환경을 만들 수 있음
4. End-to-End(사용자 관점에서 테스트) 테스트가 용이

**[ 단점 ]**
1. 프로젝트의 규모가 커짐에 따라 애플리케이션 구동시간이 늘어나고 빌드, 배포, 시간도 길어짐
2. 작은 수정사항이 있어도 전체르 ㄹ다시 빌드하고 배포해야 함
3. 많은 양의 코드가 몰려있어 개발자가 모두를 이해할 수 없고 유지보수도 힘듬
4. 일부분의 오류가 전체에 영향
5. 기능별로 알맞는 기술, 언어, 프레임워크를 선택하기가 까다로움

### MicroService Architecture
![image](https://wac-cdn.atlassian.com/dam/jcr:5308ccab-dc94-46f5-978c-8a77b8d5be57/Microservice%20architecture@2x.png?cdnVersion=488)

🚀 하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어 변경과 조합이 가능하도록 만든 아키텍처

**[ 장점 ]**
1. 배포의 관점 
 - 서비스 별 배포가 가능(배포 시 전체 서비스 중단이 없음)
 - 요구사항을 신속하게 반영하여 빠르게 배포할 수 있음
 
2. 확장의 관점
 - 특정 서비스에 대한 확장성 용이
 - 클라우드 사용에 적합한 아키텍처
 
3. 장애의 관점
 - 장애가 전체 서비스로 확장될 가능성이 적음
 - 부분적 장에에 대한 격리가 수월

4. 그 외
 - 신기술의 적용이 유연
 - 서비스를 polyglot(여러 언어 구사)하게 개발/운영할 수 있음

**[ 단점 ]**
1. 성능
 - 서비스 간 호출 시 API를 사용하기 때문에, 통신 비용이나 Latency(지연시간)가 그만큼 늘어나게 됨

2. 테스트 / 트랜잭션
 - 서비스가 분리되어 있기 때문에 테스트와 트랜잭션의 복잡도가 증가하고, 많은 자원을 필요로 함

3. 데이터 관리
 - 데이터가 여러 서비스에 걸쳐 분산되기 때문에 한번에 조회하기 어렵고, 데이터의 정합성(값 일치) 또한 관리하기 어려움

### Monolithic Architecture -> MicroService Architecture
**[ 필요성 ]**
* 어플리케이션의 배포에 한 시간 이상 소요될 경우
* 단순한 기능 하나를 수정해도 전체 기능에 대한 QA가 필요할 경우
* 단순한 버그 수정이 더 중대한 버그르 ㄹ생산하는 일이 많아졌을 경우
* 현재의 애플리케이션을 기능별로 나누다고 가정했을 때, 수십개의 마이크로서비스가 가능할 경우

## Multi Module VS MSA 
## NginX VS Apache
### NginX

🚀 **이벤트 중심 접근 방식**으로 하나의 스레드 내에서 여러 요청을 처리하는 구조

**[ 특징 ]**
1. 비동기 Event-Driven 구조 : Event handler에서 비동기 방식으로 먼저 처리되는 요청을 진행
2. 코어 모듈이 Apache보다 적은 리소스로도 많은 트래픽을 효율적으로 처리 가능

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbAbGyw%2FbtrcGUADagZ%2FEvavl3JpiSZbPq9T3Hzm01%2Fimg.png)

### Apache

🚀 **프로세스 기반 접근 방식**으로 하나의 스레드가 하나의 요청을 처리하는 구조

**[ 특징 ]**
1. 매 요청마다 스레드를 생성 및 할당해야 하기 때문에 리소소를 많이 잡아먹음

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcFcSPQ%2FbtrcB4KXbHM%2Fg4FqyuDKYEHLIxozKYHDn0%2Fimg.png)

|구분|NginX|Apache|
|:---:|:---:|:---:|
|설계 아키텍처의 차이|이벤트 중심 접근 방식|프로세스 기반 접근 방식|
|성능 차이|정적 컨텐츠를 적은 비용으로 제공<br>SCGI 핸들러와 FastCGI 모듈을 사용하여 동적 컨텐츠 제공|성능 비슷|
|OS 지원 여부|거의 모든 Unix계열, 부분적 Window|모든 Unix계열, 모든 Window|
|분산/중앙 집중식 구성|추가 구성 X|추가 구성 O|
|요청을 처리 및 해석하는 방법|URI 전달|파일 시스템 위치 전달|
|기능 모듈|동적으로 모듈 로드 X|동적으로 모듈 로드 O|
|유연성|동적모듈 & 로딩 X|동적모듈 & 로딩 O|
|보안|좀 더 안전|좀 더 불안전|

## Servlet VS Netty
### Servlet
🚀 웹 요청과 응답의 흐름을 간단한 메서드 호출만으로 체계적으로 다룰 수 있게 해주는 기술

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbu3HKI%2Fbtq7BerRpgq%2FiI82e9Zf9XLSwklFLjsXpk%2Fimg.png)

**[ 특징 ]**
1. 클라이언트의 Request에 대해 동적으로 작동하는 웹 애플리케이션 컴포넌트
2. HTML을 사용하여 Response
3. JAVA의 스레드를 이용하여 동작
4. MVC 패턴에서의 컨트롤러 이용
5. HTTP 프로토콜 서비스를 지원하는 javax.servlet.http.HttpServlet 클래스를 상속 받음
6. UDP보다 속도가 느림
7. HTML 변경 시 Servlet을 재 컴파일해야 하는 단점

### Netty
🚀 비동기 이벤트 기반 네트워크 응용프로그램 프레임워크

**[ 특징 ]**
1. 비동기 입출력(Asynchronous I/O)
2. 입출력을 위해 잘 정의된 이벤트 모델(Well-Defined Event Model)
3. 여러개의 필수적인 trnasports를 하나의 API를 통해 제공(Universal Asynchronous I/O API)
4. NIO의 ByteBuffer를 사용하지 않고 독자적인 Buffer API인 ChannelBuffer(Zero Copy 지원)
5. 개발을 위한 수 많은 컴포넌트들
6. 수 많은 코덱 제공
7. SSL, HTTP, Protocol Buffer 등 구현

## 로드밸런싱
🚀 쏟아지는 트래픽을 여러 대의 서버로 분산해주는 기술

![image](https://post-phinf.pstatic.net/MjAxOTEyMTBfMjE3/MDAxNTc1OTU0ODk1ODQ3.-GJxkoK7Apn4l0K5L1OXN4NFGsseRoaNhW2r0KIQJdog.0BchcWEI-WS-uEb3iRRrD0JyO_6eZoIWh7xf4f4J2fMg.JPEG/%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%84%9C_%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98.jpg?type=w1200)

* Scale-up : 서버 자체의 성능을 확장하는 것을 의미(ex. i3 -> i7)
* Scale-out : 기존 서버와 동일하거나 낮은 성능의 서버를 두 대 이상 증설하여 운영

**[ 다양한 로드밸런싱 알고리즘 ]**
1. 라운드로빈 방식(Round Robin Method)
2. 가중 라운드로빈 방식(Weighted Round Robin Method)
3. IP 해시 방식(IP Hash Method)
4. 최소 연결 방식(Least Connection Method)
5. 최소 리스폰타임(Least Response Time Method)

**[ 계층별 로드밸런싱 ]**
1. L4 로드밸런싱
🚀 네트워크 계층(IP, IPX)이나 트랜스포트 계층(TCP, UDP)의 정보를 바탕으로 로드를 분산 -> IP주소, 포트번호, MAC주소, 전송 프로토콜에 따라 트래픽 나눌 수 있음
![image](https://post-phinf.pstatic.net/MjAxOTEyMTBfNCAg/MDAxNTc1OTU1MzY3OTM2.nG91HOEOh6Sc1AuUgbN3O4pcnEI-rh24UKSrrrjkrcsg.VcG18MidW4az7Oh0RQfRPLDBHNRyGayE1BsQxDImL3Ig.JPEG/L4-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200)

2. L7 로드밸런싱
🚀 애플리케이션 계층(HTTP, FTP, SMTP)에서 로드를 분산 -> HTTP 헤더, 쿠키 등과 같은 사용자의 요청을 기준으로 특정 서버에 트래픽을 분산할 수 있음
![image](https://post-phinf.pstatic.net/MjAxOTEyMTBfMjA1/MDAxNTc1OTU1MzgxODY5.odnG4CRES0e5bH7sOKyWRP1c8uO_XC4VX9A3HPeI1JQg.lNL2eJYbMz6NX1e5YFzfHDMQHn4YrdOJR2VYHmq5e1Ig.JPEG/L7-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200)
>참고 : https://m.post.naver.com/viewer/postView.naver?volumeNo=27046347&memberNo=2521903

## Reverse Proxy
🚀 웹 서버 앞에 놓여있는 프록시 서버(서버와 클라이언트 사이에 대리로 통신 하는 서버)

![image](https://losskatsu.github.io/assets/images/infra/reverse_proxy/reverse_proxy02.PNG)
>참고 : https://losskatsu.github.io/it-infra/reverse-proxy/#2-%ED%8F%AC%EC%9B%8C%EB%93%9C-%ED%94%84%EB%A1%9D%EC%8B%9Cforward-%EC%84%9C%EB%B2%84%EB%9E%80

**[ 특징 ]**
1. 로드밸런싱 가능
2. 서버 IP를 숨길 수 있어서 보안에 유리
3. 서버 성능 향상을 위해 캐시 데이터 저장 가능
4. SSL 암호화에 좋음

## CDN
🚀 웹 페이지, 이미지, 비디오 등의 콘텐츠를 사용자의 물리적 위치와 가까운 프록시 서버에 캐싱하여 기다릴 필요없이, 작업이 가능한 지리적으로 분산된 여러 개의 서버를 연결하는 네트워크

**[ 특징 ]**
1. 페이지 로드 시간 단축
2. 소유자의 호스팅 비용을 절감하여 대역폭 비용 절감
3. 웹 트래픽 처리와 로드에 특화되어 콘텐츠 가용성 높음
4. 서버 간에 로드를 분산하여 웹 사이트 보안 강화
>참고 : https://www.akamai.com/ko/our-thinking/cdn/what-is-a-cdn

## 캐시
🚀 자주 사용하는 데이터나 값을 미리 복사해 놓는 임시 장소

**[ 특징 ]**
1. 저장 공간이 작고 비용이 비쌈
2. 대신 빠른 성능

**[ 종류 ]**
1. Local Cahce
* Local 장비 내에서만 사용되는 캐시로, Local 장비의 Resource를 이용
* Local에서만 작동하기 때문에 속도가 빠름
* Local에서만 작동하기 때문에 다른 서버와 데이터 공유 어려움

2. Global Cache
* 여러 서버에서 Cache Server에 접근하여 사용하는 캐시로 분산된 서버에서 데이터를 저장하고 조회할 수 있음
* 네트워크를 통해 데이터를 가져오므로 Local Cache에 비해 상대적으로 느림
* 별도의 Cache서버를 이용하기 때문에 서버 간의 데이터 공유가 쉬움
>참고 : https://mangkyu.tistory.com/69

## E-TAG
🚀 웹 서버가 주어진 URL의 콘텐츠가 변경되었는지 알려주고 이를 반환하는 HTTP 응답 헤더

* 첫 요청에 대한 응답

![image](https://velog.velcdn.com/images%2Ftigger%2Fpost%2F5c8601f8-edd2-45c6-92b7-8dc4433a9bac%2Fimage.png)
>If-None-Match : 클라이언트에서 캐싱된 E-Tag와 서버의 E-Tag가 다를 때<br>
>If-Match : 클라이언트에서 캐싱된 E-Tag와 서버의 E-Tag가 같을 때

* 재요청에 대한 응답

![image](https://velog.velcdn.com/images%2Ftigger%2Fpost%2Fca78589c-0061-45eb-bbd2-6be3ae60bf74%2Fimage.png)
>304 Not Modified : 클라이언트에게 응답이 수정되지 않았음을 알림 -> 계속해서 응답의 캐시된 버전을 사용

**[ 사용 이유 ]**
* `재요청에서!` E-Tag를 사용하지 않으면, 콘텐츠 변경 유무를 모르기 때문에 했던 일을 또 하지만, E-Tag를 사용하면 같은 요청에 대해서 변경된 리소스가 없다면 304 상태 코드와 ETag를 header에 담아 보내줄 뿐 요청에 대한 리소르를 또 보내지 않음

## 성능 테스트
### Virtual User
🚀 Vuser라고도 하며, 시스템에 동시에 작업하거나 접속하는 환경인 Emulation을 수행하기 위한 사람 역할을 하는 가상 사용자

### TPS(RPS)
🚀 TPS(Transaction Per Second), RPS(Request Per Second) / 1초에 처리하는 단위 작업의 수, 1초에 처리하는 HTTP 요청 수

### MAU/DAU(=Stickiness)
🌱 MAU(Monthly Active Users) : 월별 활동 사용자 수
🌱 DAU(Daily Active Users) : 일별 활동 사용자 수 - 하루에 한번만 카운트

🚀 월별 사용자 대비 몇 퍼센트의 사용자가 매일 앱을 사용하는지 말해주는 지표

* 앱 관심도 파악, 트래픽과 매출 예상

# 기술
## 로깅 라이브러리 비교(스프링/자바 -> 보안 이슈 적지 말아라)
### Log4j
**[ 구조 ]**
* logger : 데이터를 기록
* appender : 데이터를 어디에 기록할지 정함(파일, 콘솔, JDBC, SMTP 등)
* layout : 데이터를 어떤 스타일로 기록할지 정함

**[ 기능 ]**
1. Thread safe
2. 퍼포먼스 최적화
3. 여러 종류의 appender 지원
4. JUL(Java Util Logging)에 비해 명확한 기준 레벨 : ALL, TRACE, DEBUG, INFO, WARN, ERROR, FATAL

🌱 2020년에 다음 바전인 log4j2 출시

### SLF4J(Simple Logging Facade for Java)
🚀 Log4J 또는 LogBack과 같은 백엔드 Logging Framework의 facade pattern

![image](https://gmlwjd9405.github.io/images/logging/facade-pattern.png)
>facade pattern 참고

**[ 특징 ]**
* 다양한 Logging Framework에 대한 추상화
* SLF4j api를 사용하면 구현체의 종류에 상관없이 일관된 로깅 코드를 작성할 수 있음
* 배포할 때 원하는 logging Framework를 선택할 수 있음
* Loggin Framework간에 전환이 쉬움
* API/Binding/Bridging 세 가지 모듈 제공

참고 : https://gmlwjd9405.github.io/2019/01/04/logging-with-slf4j.html

### LogBack

**[ 구조 ]**
* logger : 데이터 기록
* append : 어디에 기록할지 정함
* encoder : 어떻게 출력할지 정함

**[ 특징 ]**
1. 빠른 implementation
2. 적은 메모리 점유
3. XML로 Logging 설정
4. maxHistory 설정 값을 이용해 일정 기간이 지나면 로그파일 자동 삭제
5. Filter 기능 : 사용자별 level 조정 가능

참고 : https://oingdaddy.tistory.com/78

## RabbitMq
🚀 AMQP(Advanced Message Queuing Protocol)를 따르는 오픈소스 메시지 브로커

![image](https://blog.dudaji.com/assets/rabbitmq/MessageFlow.png)

* 메시지를 많은 사용자에게 전달
* 요청에 대한 처리시간이 길 때, 해당 요청을 다른 API에게 위임하고 빠른 응답을 할 때 사용
* MQ를 사용하여 애플리케이션 간 결합도를 낮출 수 있음

**[ AMQP ]**
🚀 메시지 지향 미들웨어를 위한 개방형 표준 응용 계층 프로토콜
* 정의 기능들 : 메시지 지향, 큐잉, 라우팅, 신뢰성, 보안

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFu3hC%2FbtqLlBNLo7A%2FVKjIQUN9cTrddlyRsSktg1%2Fimg.png)
>MOM : 비동기 메시지를 사용하는 다른 응용 프로그램 사이에서의 데이터 송수신

**[ 메시지 브로커 ]**
🚀 대규모 기반 미들웨어(서비스하는 애플리케이션들을 보다 효율적으로 아키텍처들을 연결하는 요소들로 작동하는 소프트웨어 - 메시징 플랫폼, 인증 플랫폼, 데이터 베이스) 아키텍처에 사용
* 큐에 데이터를 보내고 받는 프로듀서와 컨슈머를 통해 메시지를 통신하고 네트워크를 맺는 용도로 사용
* 메시지를 받아서 적절히 처리하고 나면 즉시 또는 짧은 시간 내에 삭제되는 구조

참고 : https://blog.dudaji.com/general/2020/05/25/rabbitmq.html

## ActiveMq
🚀 JMS(Java Message Service) 클라이언트와 함께 자바로 작성된 오픈 소스 메시지 브로커

* 하나 이상의 클라이언트나 서버로부터 통신을 조성시키는 엔터프라이즈 기능들을 제공
* 자바 및 기타 여러 언어 간 클라이언트 지원
## 카프카
🚀 대용량 실시간 로그 처리에 특화되어 설계된 메시징 시스템

* TPS가 매우 우수
* 특화된 시스템이기 때문에 범용 메시지 시스템에서 제공하는 다양한 기능들은 제공 X
* 기존 메시징 시스템 : broker -(push)-> consumer | Kafka : comsumer -(pull)-> broker

🌱 TPS가 높은 고성능 애플리케이션 = Kafka
🌱 고성능 X 인 자바 어플리케이션 = ActiveMQ(다양한 기능)
🌱 AMQP 프로토콜 통신이 필요한 경우 = RabbitMQ

## ELK(elasticStack)
🚀 Elasticsearch, Logstash, kibana의 세 가지 인기 있는 플고젝트로 구성된 스택

**E = Elasticsearch**
🌱 Apache Lucene에 구축되어 배포된 검색 및 분석 엔진

* 다양한 언어를 지원하고 고성능에 스키마가 없는 JSON 문서로 다양한 로그 분석과 검색 사용에 유리

**L = Logstash**
🌱 다양한 소스로부터 데이터를 수집하고 전화하여 원하는 대상에 전송할 수 있도록 하는 오픈 소스 데이터 수집 도구

* 사전 구축된 필터 & 200개가 넘는 플러그인에 대한 지원 -> 데이터 원본이나 유형에 관계없이 데이터를 쉽게 수집할 수 있음

**K = Kibana**
🌱 로그 및 이벤트 검토에 사용하는 데이터 시각화 및 탐색 도구

* 대화형 차트, 사전 구축된 집계 및 필터, 지리 공간적 지원을 제공 -> 저장된 데이터를 시각화하는데 유리

=> 로그 분석 공간에서의 필요(?)를 채워주기 때문에 유명하다.

## 레디스
🚀 Key, Value 구조의 비정형 데이터(음악, 이미지, 문서 등)를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터 베이스 관리 시스템(DBMS)

* 데이터베이스, 캐시, 메시지 브로커로 사용 - 인메모리 데이터 구조를 가진 저장소

**[ 특징 ]**
* Key, Value 구조이기 때문에 쿼리 필요 X
* 메모리에서 데이터를 처리하기 때문에 속도가 빠름
* String, List, Sets, Sorted Sets, Hashes 자료 구조를 지원
* Single Threaded : 한 번에 하나의 명령만 처리 가능(get, set 명령어는 매우 빠름)

## 도커
🚀 컨테이너(이미지를 실행하면 프로세스, 즉 컨테이너) 기반의 가상화 플랫폼

![image](https://velog.velcdn.com/images%2Fmarkany%2Fpost%2Ffcc402fe-8238-46c1-a93f-ebbd9f7e3e9b%2Fdifference.png)

* 이미지를 실행시켜 컨테이너로 만들거나, 생성된 컨테이너를 관리하거나, 컨테이너를 다시 이미지로 만드는 작업
* 격리된 환경이 필요할 때, 완성된 서비스를 배포할 때, 배포 중인 서비스를 받아서 실행해볼 때 유용함

## 쿠버네티스
🚀 컨테이너화된 워크로드와 서비스를 관리하기 위한, 이식성 있고 확장 가능한 오픈 소스 플랫폼

**[ 특징 ]**
* 서비스 디스커버리와 로드 밸런싱
* 스토리지 오케스트레이션
* 자동화된 롤아웃과 롤백
* 자동화된 빈 패킹
* 자동화된 복구
* 시크릿과 구성 관리

참고 : https://kubernetes.io/ko/docs/concepts/overview/what-is-kubernetes/

## 프로메테우스
🚀 메트릭 수집, 시각화, 알림, 서비스 디스커버리 기능을 모두 제공하는 오픈 소스 모니터링 시스템

**[ 기능 ]**
* 풀 방식의 메트릭 수집, 시계열 데이터 저장
* PromQL을 활용하여 저장된 시계열을 쿼리 및 집계
* 서비스 디스커버리
* 데이터 시각화

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkSDGB%2Fbtq9ReJ6Lod%2FpXLbFLR1Q0NmIuMktf0DFK%2Fimg.png)
>프로메테우스 아키텍처

**[ 사용 예시 ]**
* 메트릭 기반의 시계열 데이터 저장
* 동적인 혹은 마이크로 서비스의 인스턴스에 대한 메트릭을 수집하는 일
* 이벤트 로그나 개별 이벤트를 저장하는 일
* 이메일 주소/사용자 이름과 같이 카디널리티가 높은 데이터를 저장하는 일
* 100% 정확성이 요구되는 일

참고 : https://gurumee92.tistory.com/220

## 그라파나 
🚀 오픈소스 메트릭 데이터 시각화 도구 -> 메트릭 분석 플랫폼

참고 : https://www.44bits.io/ko/keyword/grafana
## 코틀린 
🚀 자바 플랫폼에서 돌아가는 새로운 프로그래밍 언어

**[ 장점 ]**
* 간결하고 실용적
* 자바 코드와의 상호운용
* 대부분의 자바 프로젝트에서 코틀린 활용
* 성능은 자바와 비슷
* 안정성

참고 : https://ktko.tistory.com/entry/%EC%BD%94%ED%8B%80%EB%A6%B0%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%99%9C-%ED%95%84%EC%9A%94%ED%95%9C%EA%B0%80

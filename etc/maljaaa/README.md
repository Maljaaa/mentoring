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

## CDN
## 캐시
## E-TAG
## 성능 테스트
### Virtual User
### TPS(RPS)
### MAU/DAU
# 기술
## 로깅 라이브러리 비교(스프링/자바 -> 보안 이슈 적지 말아라)
## RabbitMq
## ActiveMq
## 카프카
## ELK(elasticStack)
## 레디스
## 도커
## 쿠버네티스
## 프로메테우스
## 그라파나 
## 코틀린 

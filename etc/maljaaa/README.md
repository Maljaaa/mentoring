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
## Multi Module VS MSA 
## NginX VS Apache
## Servlet VS Netty
## 로드밸런싱
## Reverse Proxy
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

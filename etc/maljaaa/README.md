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

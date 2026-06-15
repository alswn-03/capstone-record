**nGrinder**는 **네이버(Naver)에서 오픈 소스로 개발한 자바(Java) 기반의 서버 성능 및 부하 테스트 도구**
[nGrinder-github](https://naver.github.io/ngrinder/)
- 웹 애플리케이션의 최대 수용 동시 접속자 수, TPS(초당 처리량), 응답 시간 등 핵심 성능 지표 등을 측정
- nGrinder의 핵심 구성 요소는 다음과 같습니다:
    - **Controller (컨트롤러) :** 부하 테스트 스크립트를 관리하고 테스트를 제어하는 웹 기반의 메인 서버
        - 사용자 친화적인 웹 GUI를 제공하여 여러 명의 테스터가 동시에 접속해 사용할 수 있습니다.
    - **Agent (에이전트) :** 컨트롤러의 지시를 받아 대상 서버에 실제 트래픽과 부하를 발생시키는 가상 사용자(VUser) 생성기
    - **Monitor (모니터) :**
        
        부하 테스트가 진행되는 동안 대상 서버의 CPU, 메모리 등의 리소스 사용량을 측정한다 [1, 2, 3, 4]
        

- [nGridner 소개와 설치 방법, 간단 테스트](https://0soo.tistory.com/223)
- [nGrinder 성능테스트 사용법 및 테스트 예제](https://notspoon.tistory.com/48)
- [nGrinder 설치와 사용법](https://velog.io/@gjwjdghk123/nGrinder-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-%EB%B0%8F-%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%95%B4%EB%B3%B4%EA%B8%B0)
- [nGrinder 설치 방법 및 파일 업로드 테스트 예제](https://2021-pick-git.github.io/nGrinder-basic/)
- [nGrinder로 TPS, 응답시간 성능테스트 후기](https://beomukim.tistory.com/25)

# nGrinder

- 네이버에서 진행한 오픈 소스 프로젝트로 **서버의 부하 테스트**를 위한 도구
    - 웹 애플리케이션을 서비스하기 전에 서버가 얼마나 많은 사용자를 수용할 수 있는지 요청을 전송해봄으로써 서버의 성능을 측정해볼 수 있다
    - 부하테스트는 성능테스트의 일종이지만, 성능테스트랑은 다르다

- nGrinder는 다음과 같은 주요 기능을 제공
    - 스크립트 레코딩: 웹 브라우저에서 사용자 동작을 녹화하여 테스트 스크립트를 생성
    - 분산 테스트: 다수의 에이전트 머신을 사용하여 대규모 테스트를 수행
    - 실시간 모니터링: 테스트 진행 중에 성능 지표를 실시간으로 모니터링
    - 분석 및 리포팅: 테스트 결과를 다양한 그래프와 테이블로 분석하고, 리포트를 생성

cf)

- JMeter 는 단일 데스크톱 컴퓨터에서 수행
    - nGrinder 는 컨트롤러 및 에이전트로 구성된 분산 아키텍처로 수행
- nGrinder는 jython 또는 Groovy 같은 스크립트 언어를 사용하여 스크립트를 작성
    - 스크립트를 이용한 자동화는 매우 편리
- 도커, 클라우드 환경에서도 실행 가능

# nGrinder 동작 방식

nGrinder는 Controller와 Agent 로 구성

<img src="./image/nGrinderSystemArchitecture.png">

아아 그 Agent 가 사용자로서 요청을 보내는 거 같음

내가 테스트 하려는 서버에
# 기술 용어 정리

## 개요

IT 분야에서 자주 사용되는 용어들을 정리한 용어집입니다.
개발, 인프라, 보안 등 다양한 분야의 핵심 용어를 쉽게 이해할 수 있도록 설명합니다.

## 주요 용어

### 개발 일반

**API (Application Programming Interface)**
- 소프트웨어 간 상호작용을 위한 인터페이스
- RESTful API, GraphQL 등

**CLI (Command Line Interface)**
- 텍스트 기반 명령어 인터페이스
- GUI와 대비되는 개념

**IDE (Integrated Development Environment)**
- 통합 개발 환경
- 예: VS Code, IntelliJ, Eclipse

**Repository (저장소)**
- 코드와 버전 관리 정보를 저장하는 장소
- Git 저장소, GitHub, GitLab

### 버전 관리

**Commit**
- 변경사항을 저장소에 기록하는 행위
- Git의 기본 단위

**Branch**
- 독립적인 개발 라인
- 기능 개발, 버그 수정 시 사용

**Merge**
- 브랜치를 합치는 작업
- Merge conflict 해결 필요

**Pull Request (PR)**
- 코드 변경사항 검토 요청
- GitHub, GitLab에서 사용

### 컨테이너 & 오케스트레이션

**Container (컨테이너)**
- 애플리케이션과 의존성을 패키징한 실행 환경
- Docker가 대표적

**Image (이미지)**
- 컨테이너 실행을 위한 템플릿
- Dockerfile로 빌드

**Orchestration**
- 컨테이너 배포, 관리, 확장 자동화
- Kubernetes가 대표적

### 클라우드 & 인프라

**IaaS (Infrastructure as a Service)**
- 인프라 서비스
- 예: AWS EC2, Azure VM

**PaaS (Platform as a Service)**
- 플랫폼 서비스
- 예: Heroku, Google App Engine

**SaaS (Software as a Service)**
- 소프트웨어 서비스
- 예: Gmail, Slack, Notion

**CI/CD (Continuous Integration/Continuous Deployment)**
- 지속적 통합 및 배포
- 자동화된 빌드, 테스트, 배포

### 네트워크 & 보안

**HTTP/HTTPS**
- 웹 통신 프로토콜
- HTTPS는 암호화된 HTTP

**SSL/TLS**
- 암호화 프로토콜
- 웹 보안의 기본

**DNS (Domain Name System)**
- 도메인 이름을 IP 주소로 변환
- 인터넷의 전화번호부

**Firewall (방화벽)**
- 네트워크 트래픽 제어
- 보안의 첫 번째 방어선

### 데이터베이스

**RDBMS (Relational Database Management System)**
- 관계형 데이터베이스
- MySQL, PostgreSQL, Oracle

**NoSQL**
- 비관계형 데이터베이스
- MongoDB, Redis, Cassandra

**ORM (Object-Relational Mapping)**
- 객체와 관계형 DB 매핑
- Django ORM, SQLAlchemy

### 프로그래밍 개념

**Framework (프레임워크)**
- 애플리케이션 개발을 위한 구조
- Django, Flask, React, Vue

**Library (라이브러리)**
- 재사용 가능한 코드 모음
- NumPy, Pandas, Lodash

**Dependency (의존성)**
- 프로젝트가 필요로 하는 외부 라이브러리
- package.json, requirements.txt

**Environment Variable (환경 변수)**
- 실행 환경에 따라 달라지는 설정값
- .env 파일로 관리

## 약어 정리

| 약어 | 전체 이름 | 의미 |
|------|----------|------|
| API | Application Programming Interface | 애플리케이션 프로그래밍 인터페이스 |
| CLI | Command Line Interface | 명령줄 인터페이스 |
| GUI | Graphical User Interface | 그래픽 사용자 인터페이스 |
| IDE | Integrated Development Environment | 통합 개발 환경 |
| JSON | JavaScript Object Notation | 자바스크립트 객체 표기법 |
| YAML | YAML Ain't Markup Language | YAML은 마크업 언어가 아님 |
| CSV | Comma-Separated Values | 쉼표로 구분된 값 |
| SSH | Secure Shell | 보안 셸 |
| HTTP | HyperText Transfer Protocol | 하이퍼텍스트 전송 프로토콜 |
| HTTPS | HTTP Secure | 보안 HTTP |
| URL | Uniform Resource Locator | 통합 자원 위치 지정자 |
| URI | Uniform Resource Identifier | 통합 자원 식별자 |
| REST | Representational State Transfer | 표현 상태 전이 |
| CRUD | Create, Read, Update, Delete | 생성, 읽기, 수정, 삭제 |

## 참고 자료

- [MDN 웹 용어 사전](https://developer.mozilla.org/ko/docs/Glossary)
- [IT 용어 사전 - 한국정보통신기술협회](http://word.tta.or.kr/)
- [Wikipedia - IT 용어](https://ko.wikipedia.org/wiki/%EC%A0%95%EB%B3%B4_%EA%B8%B0%EC%88%A0)

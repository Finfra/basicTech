# 데이터 파일 형식

## 개요

현대 소프트웨어 개발에서 데이터 교환과 설정 관리를 위해 다양한 파일 형식이 사용됩니다.
JSON, YAML, CSV, XML 등 각 형식의 특징과 사용 사례를 이해하는 것이 중요합니다.

## 주요 개념

### JSON (JavaScript Object Notation)
- 경량 데이터 교환 형식
- 사람이 읽기 쉽고 기계가 파싱하기 쉬움
- 웹 API에서 가장 널리 사용
- 데이터 타입: 객체, 배열, 문자열, 숫자, 불린, null

### YAML (YAML Ain't Markup Language)
- 사람이 읽기 쉬운 데이터 직렬화 형식
- 들여쓰기로 구조 표현
- 설정 파일에 주로 사용 (Docker, Kubernetes)
- JSON의 상위 집합

### CSV (Comma-Separated Values)
- 표 형식 데이터를 저장하는 텍스트 파일
- 각 행은 레코드, 각 열은 필드
- 스프레드시트와 데이터베이스 간 데이터 교환
- 간단하지만 중첩 구조 표현 불가

### XML (eXtensible Markup Language)
- 마크업 언어 기반 데이터 형식
- 태그로 데이터 구조화
- 복잡한 계층 구조 표현 가능
- 레거시 시스템에서 여전히 사용

## 실습 예제

### JSON 예제
```json
{
  "name": "홍길동",
  "age": 30,
  "skills": ["Python", "Docker", "Git"],
  "contact": {
    "email": "hong@example.com",
    "phone": "010-1234-5678"
  }
}
```

### YAML 예제
```yaml
name: 홍길동
age: 30
skills:
  - Python
  - Docker
  - Git
contact:
  email: hong@example.com
  phone: 010-1234-5678
```

### CSV 예제
```csv
이름,나이,이메일,기술
홍길동,30,hong@example.com,Python
김철수,25,kim@example.com,Docker
이영희,28,lee@example.com,Git
```

### Python에서 파일 다루기
```python
import json
import yaml
import csv

# JSON 읽기
with open('data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# YAML 읽기
with open('config.yaml', 'r', encoding='utf-8') as f:
    config = yaml.safe_load(f)

# CSV 읽기
with open('users.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row['이름'], row['나이'])
```

## 참고 자료

- [JSON 공식 사이트](https://www.json.org/json-ko.html)
- [YAML 공식 문서](https://yaml.org/)
- [CSV 파일 형식 설명](https://en.wikipedia.org/wiki/Comma-separated_values)
- [Python json 모듈](https://docs.python.org/ko/3/library/json.html)
- [Python yaml 라이브러리](https://pyyaml.org/wiki/PyYAMLDocumentation)

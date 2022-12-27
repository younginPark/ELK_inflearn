# Elasticsearch CRUD

- 클러스터 탐색
    - REST API 사용하여 노드와 통신
    - API를 통해 클러스터, 노드, 색인 상태 및 통계 확인 가능, 데이터 및 메타 데이터 관리 가능
    - CRUD 및 인덱스에 대한 검색 작업 수행
    - 페이징, 정렬, 필터링, 스크립팅, 집계 및 기타 여러 고급 검색 작업 실행

- 클러스터 상태
    - 클러스터가 어떻게 진행되고 있는지 기본적인 확인
    - 강의에서는 curl을 사용하여 이를 수행
    - HTTP / REST 호출을 수행할 수 있는 모든 도구를 사용 가능
    - 클러스터 상태를 확인하기 위해 _cat API를 사용 (_search, _update..)
    - 녹색 - 모든 것이 좋음 (클러스터는 완전히 작동)
    - 노란색 - 모든 데이터를 사용할 수 있지만 일부 복제본은 아직 할당되지 않음 (클러스터는 완전히 작동)
    - 빨간색 - 어떤 이유로든 일부 데이터를 사용할 수 없음 (클러스터가 부분적으로 작동 함)
    - ex) GET /_cat/nodes?v

- 데이터베이스가 가진 데이터 확인하기
    - 갖고 있는 모든 인덱스 항목 조회
    - index는 일반 RDB에서의 데이터베이스의 역할
    - GET /_cat/indices?v

- Elasticsearch의 데이터 구조
    - Index, Type, Document의 단위를 가짐
    - Document는 Elasticsearch의 데이터가 저장되는 최소 단위
    - 여러개의 Document는 하나의 타입
    - 다시 여러개의 Type으로 하나의 Index 구성
    - Index > Type > Document

![스크린샷 2022-12-27 오후 7.35.34.png](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2022-12-27_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_7.35.34.png)

- Elasticsearch의 질의 방법
    - 커맨드라인의 curl 명령어 사용
    - postman 응용프로그램 사용
    - Kibana에서 devtool 사용

- 질의 실습
    - 127.0.0.1:9200/_cat/nodes?v
    
    ![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled.png)
    
    - [http://127.0.0.1:9200/_cat/health?v](http://127.0.0.1:9200/_cat/health?v)
    
    ![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%201.png)
    
    - Kibana DevTool 사용
    
    ![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%202.png)
    
- 인덱스 만들기
    - PUT으로 넣어줌
    - indices 는 DB 전체 목록 조회 시 사용

![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%203.png)

![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%204.png)

![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%205.png)

![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%206.png)

```python
// _update를 써서 doc 전체에서 age에 해당하는 내용만 수정
POST customer/type1/1/_update
{
  "doc": {
    "age":123
  }
}

// source 부분을 아예 갈아끼우는 방식
POST customer/type1/1
{
  "name": "Yeonini Park",
  "age": 9999
}
```

- script 형식으로 update도 가능

![Untitled](Elasticsearch%20CRUD%208a07b9227d6049cea88d8b06a6207fa1/Untitled%207.png)
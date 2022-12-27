# ELK 개요 및 설치

### ELK 스택

- Elasticsearch(데이터베이스, 검색엔진), Kibana(데이터 시각화, 집계), Beats, Logstash (데이터 수집)
- 다양한 DB나 OS에서 어떤 형식이든지 안정적이게 데이터를 수집하고 실시간으로 검색, 분석, 시각화 함

### 사용사례

- 온라인 웹스토어에서 카탈로그 및 인벤토리를 저장하고 검색 및 자동 완성 제안 제공
- 로그 또는 트랜잭션 데이터를 수집, 분석 및 조사하여 트렌드, 통계, 요약 또는 예외 탐지
- 물건에 대한 가격이 특정 가격 이하로 떨어지면 알림을 주는 플랫폼 운영 가능
- 분석/비즈니스 요구 사항이 있으면 수억 또는 수십억 건의 레코드의 데이터에 대해서 신속하게 조사, 분석, 시각화 및 질의 가능

### Elastic Search

- NRT (Near Realtime) 대량의 데이터를 신속하고 거의 실시간으로 저장, 검색 및 분석
- 일반적으로 복잡한 검색 기능과 요구 사항이 있는 응용 프로그램을 구동하는 기본 엔진 기술 탑재 (루씬 기반)
- Cluster
    - 전체 데이터를 함께 보유하고 모든 노드에서 연합 인덱싱 및 검색 기능을 제공하는 하나 이상의 노드 모음
    - 클러스터는 기본적으로 “elasticsearch”라는 고유한 이름으로 식별
- Node
    - 클러스터의 일부이며 데이터를 저장하고 클러스터의 인덱싱 및 검색 기능에 참여하는 단일 서버
    - 현재 네트워크에 실행 중인 다른 Elasticsearch 노드가 없는 경우 단일 노드를 시작하면 기본적으로 elasticsearch라는 새로운 단일 노드 클러스터가 형성
- Index (DB)
    - 색인은 다소 유사한 특성을 갖는 문서의 컬렉션
    - 모두 소문자인 이름으로 식별되며 이 이름으로 문서를 색인 작성, 검색, 갱신, 삭제할 때 색인 참조 시 사용
- Type (Table)
    - 사라진 개념
    - 색인의 논리적 범주 / 파티션으로 사용되는 유형
- Documents (Record)
    - 문서는 색인을 생성할 수 있는 기본 정보 단위
    - JSON 형태
- RESTful API
    - URI를 사용한 동작 가능
    - HTTP 프로토콜로 JSON 문서의 입출력과 다양한 제어 가능
    

### 설치

- Elasticsearch, Kibana, Filebeat, Logstash 7.2.0 버전으로 설치

[Install Elasticsearch from archive on Linux or MacOS | Elasticsearch Guide [7.17] | Elastic](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/targz.html)

- Elasticsearch, Kibana 모두 `./bin/elasticsearch` 로 실행 가능
- 접속
    - Elasticsearch : [http://127.0.0.1:9200/](http://127.0.0.1:9200/)
    - Kibana : [http://127.0.0.1:5601/](http://127.0.0.1:5601/)